---
name: using-ai-filmmaking
description: Use when starting any AI film project — establishes the mandatory pipeline order and skill invocation discipline before any generation begins
---

# Using AI Filmmaking

## Overview

AI filmmaking without a pipeline produces visual chaos: character identity drifts between shots, spatial geography contradicts itself, lighting temperature shifts randomly, and hours of generation produce unusable footage. The skills in this plugin enforce the discipline that separates cinema from slop.

## The Iron Law

```
CHECK FOR SKILLS BEFORE ANY PRODUCTION STEP — EVEN "JUST ONE QUICK PROMPT"
```

Every step in AI filmmaking has a skill. The skill exists because that step has a failure mode that kills the entire production. Skipping the skill means skipping the protection.

## The Pipeline (in order)

```
1.  brief-to-art-direction     ← translate narrative into visual DNA
2.  moodboard-extraction       ← extract reusable rules from references
3.  style-prefix               ← lock the style document for all prompts
4.  scene-geography            ← lock the spatial rules before any image
5.  character-bible            ← lock character identity at multiple angles
6.  shot-list-design           ← plan all shots before generating any
    asset-pipeline             ← generate location and props as separate assets
7.  cinematographic-prompting  ← write every prompt with 7-field structure
    stills-audit-loop          ← audit every generated image before approval
8.  continuity-checker         ← verify cross-shot consistency before video
9.  image-to-video             ← convert approved stills to video clips
10. audio-crafting             ← design voice + ambient + music in three layers
11. assembly-compositing       ← edit to performance rhythm, not visual variety
```

Steps 6 and 7 run in parallel pairs. Every other step is sequential.

## How to Invoke Skills

In Claude Code, use the `Skill` tool:
- `ai-filmmaking:brief-to-art-direction`
- `ai-filmmaking:moodboard-extraction`
- etc.

Invoke the skill BEFORE taking any action in that pipeline stage — not after.

## Red Flags

| Thought | Reality |
|---|---|
| "I'll just generate one test image first" | Test images set visual expectations that become hard to abandon. Run the pipeline. |
| "I know what the scene looks like" | You know the narrative. The visual DNA still needs extraction. |
| "Skills are overhead for a 1-minute short" | A 1-minute short has 5–8 shots. Each shot has 6 continuity variables. The pipeline prevents chaos. |
| "I'll fix consistency in post" | Post cannot fix wrong character identity or a crossed 180° axis. |
| "I'll invoke the skill after I try this once" | Once you generate, you've set expectations. Invoke before. |

## What Each Skill Protects

| Skill | What it prevents |
|---|---|
| brief-to-art-direction | Visual drift from unanchored narrative decisions |
| moodboard-extraction | Importing unwanted specifics (faces, IP) from reference images |
| style-prefix | Style fragmentation across shots or team members |
| scene-geography | Characters swapping sides, objects moving between shots |
| character-bible | Character identity drift across camera angles |
| shot-list-design | Improvised shots that cannot be cut with planned shots |
| asset-pipeline | Spatial confusion from generating character + location together |
| cinematographic-prompting | Prompts that produce inconsistent or ambiguous results |
| stills-audit-loop | Approving images that will break continuity downstream |
| continuity-checker | Continuity errors that cannot be fixed in post |
| image-to-video | Camera positioning failures, unwanted cuts, wrong pacing |
| audio-crafting | Non-separable generated music, reactive sound design |
| assembly-compositing | Cuts that don't serve rhythm, color grade failures |

**REQUIRED NEXT SKILL:** ai-filmmaking:brief-to-art-direction
