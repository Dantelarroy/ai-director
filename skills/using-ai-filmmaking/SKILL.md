---
name: using-ai-filmmaking
description: Use when starting any AI film project — bootstraps the session, detects existing project state, and guides to the correct next step without requiring the user to know the pipeline
---

# Using AI Filmmaking

## Overview

You are the session orchestrator. Every AI filmmaking session starts here. You detect where the project is, tell the user what happens next, and invoke the first relevant skill. The user never needs to know which skill to call — you carry them through.

## The Iron Law

```
CHECK PROJECT STATE BEFORE ANYTHING ELSE — NEVER ASSUME A CLEAN START
```

## Active Process

When this skill is invoked, run this process in order:

**Step 1: Detect project state**

Check if `production/` exists in the current working directory:
- If `production/` does not exist → this is a new project. Go to Step 2.
- If `production/` exists → read which files are present and report status. Go to Step 3.

**Step 2: New project — ask one question**

Say exactly:

> "¿De qué trata tu proyecto? Describime la escena en una oración."

Wait for the answer. Then:
- Create the `production/` directory
- Announce: "Empezamos por el principio. Invocando `brief-to-art-direction`..."
- Invoke `ai-filmmaking:brief-to-art-direction`

**Step 3: Existing project — show state and ask where to continue**

Read which files exist in `production/` and show a status table:

```
Estado del proyecto:

✅  art-direction.md        — Art Direction Document
✅  visual-tokens.md        — Visual Token Document
✅  style-prefix.md         — Style Prefix [LOCKED]
⬜  scene-geography.md      — Scene Geography (pendiente)
⬜  character-bible/        — Character Bible (pendiente)
...
```

Then ask:
> "¿Continuamos desde `scene-geography` o necesitás volver a algún paso anterior?"

Based on the answer, invoke the appropriate skill.

## Platform Adaptation

**Claude Code:** Use the `Skill` tool to invoke skills.

**Codex:** See `references/codex-tools.md` for tool mapping.

**Copilot CLI:** See `references/copilot-tools.md` for tool mapping.

**Gemini CLI:** Tool mapping loaded from `references/gemini-tools.md` via GEMINI.md.

## The Full Pipeline

| Step | Skill | Output file |
|---|---|---|
| 1 | `brief-to-art-direction` | `production/art-direction.md` |
| 2 | `moodboard-extraction` | `production/visual-tokens.md` |
| 3 | `style-prefix` | `production/style-prefix.md` [LOCKED] |
| 4 | `scene-geography` | `production/scene-geography.md` [LOCKED] |
| 5 | `character-bible` | `production/character-bible/character-[N].md` |
| 6 | `shot-list-design` | `production/shot-list.md` |
| 7 | `asset-pipeline` | `production/assets/` |
| 8→loop | `cinematographic-prompting` | `production/prompts/[shot-id].md` |
| 8→loop | `stills-audit-loop` | appends to `production/audit-log.md` |
| 9 | `continuity-checker` | `production/continuity-report.md` |
| 10→loop | `image-to-video` | video prompts per shot |
| 11 | `audio-crafting` | `production/audio-design.md` |
| 12 | `assembly-compositing` | final assembly |

## What Each Skill Protects

| Skill | Without it |
|---|---|
| `brief-to-art-direction` | Visual drift from the first generation |
| `moodboard-extraction` | Borrowing specific faces, IP, accidental compositions from references |
| `style-prefix` | Every shot looks like a different film |
| `scene-geography` | 180° axis violations, reversed character positions, uneditable material |
| `character-bible` | Identity drift — 5 shots = 5 different people |
| `shot-list-design` | Improvised shots that can't be cut together |
| `asset-pipeline` | Spatial confusion from generating character + location in one prompt |
| `cinematographic-prompting` | Underspecified prompts that rely on model defaults |
| `stills-audit-loop` | Approving drifted images that become corrupted references |
| `continuity-checker` | Cross-shot failures discovered after video generation |
| `image-to-video` | Spatial incoherence, accidental cuts, mechanical motion |
| `audio-crafting` | Non-separable generated music embedded in video |
| `assembly-compositing` | Assembling after generation instead of during |

## Red Flags

| Thought | Reality |
|---|---|
| "I'll just generate one test image first" | Test images set visual expectations. Run the pipeline. |
| "I know what the scene looks like" | You know the narrative. The visual DNA needs extraction. |
| "Skills are overhead for a 1-minute short" | 1 minute = 5-8 shots = 6 continuity variables per shot. The pipeline prevents chaos, it doesn't create it. |
| "I'll fix consistency in post" | Post cannot fix wrong character identity or crossed 180° axis. |
| "I can skip straight to cinematographic-prompting" | Without locked geography and style prefix, every prompt is guessing. |
