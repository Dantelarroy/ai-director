---
name: assembly-compositing
description: Use when all clips and audio are ready — reads all production documents, generates the complete edit order and VFX list, and closes the pipeline
---

# Assembly & Compositing

## Overview

Assembly is where every upstream decision is tested simultaneously. The shot list defined the dramatic structure. The geography defined the spatial contract. The continuity checker verified it. Now all three are enforced by the cut. A wrong cut here surfaces a failure from five skills ago. This skill generates the edit order, compositing notes, and closes the production pipeline.

## The Iron Law

```
THE EDIT ORDER FOLLOWS THE DRAMATIC LOGIC, NOT THE SHOT LIST ORDER — RESTRUCTURE IF THE STORY DEMANDS IT
```

## Active Process

Announce: "Usando `assembly-compositing` para generar el montaje final."

**Step 1: Read all production documents**

Read:
- `production/art-direction.md` — the dramatic intent
- `production/shot-list.md` — the planned structure
- `production/scene-geography.md` — the spatial contract
- `production/continuity-report.md` — verified shot statuses
- `production/audio-design.md` — the three-layer audio world

**Step 2: Ask one question**

> "¿Tenés todos los clips aprobados listos para montar? ¿Hay algún plano que haya quedado fuera o que quieras reemplazar antes de cerrar?"

**Step 3: Generate the edit order**

The edit order follows dramatic logic, not shot list order. Propose the cut sequence:

```
EDIT ORDER:
[N]. Shot [ID] — [TYPE] — [Duration] — [Transition] — [Dramatic function]
[N]. Shot [ID] — [TYPE] — [Duration] — [Transition] — [Dramatic function]
...
```

For each transition:
- **Hard cut** — tension or contrast
- **Dissolve** — time passage or emotional softening
- **L-cut** — previous shot audio continues under new visual (incoming sound leads)
- **J-cut** — next shot audio begins before visual cut
- **Match cut** — spatial continuity across scenes

**Step 4: Generate the compositing notes**

```
COMPOSITING NOTES:
1. Composite elements: [props generated separately → composite in Photoshop before timeline import]
2. Color grade: [correction only — base look already baked via style prefix]
3. Grain: [unified post layer across full film — not per-shot]
4. Export: 24fps / [aspect ratio from style prefix] / highest quality before delivery compression

AUDIO COMPOSITE ORDER:
1. Ambient first (room tone, signature sounds)
2. Voice second (dialogue, narration)
3. Music third (score, sync points)
[Sync points from production/audio-design.md]
```

**Step 5: Surface any unresolved issues**

Check `production/continuity-report.md` for any unresolved failures:

> "Antes de cerrar el pipeline, el continuity report registra: [issue / 'ningún problema']. ¿Lo resolvés o lo dejamos para iteración futura?"

**Step 6: Show plan for approval**

Show full edit order and compositing notes. Ask:
> "¿Aprobás este plan de montaje o ajustamos algo?"

**Step 7: Write the assembly document**

Write to `production/assembly.md`:

```markdown
# Assembly Plan
## [Project name]

> Output of `ai-filmmaking:assembly-compositing`

## Edit Order
[Full sequence table]

## Compositing Notes
[Grade / grain / export / element compositing]

## Audio Composite
[Layer order and sync points from audio-design.md]

## Pipeline Status
[COMPLETO / Pendiente: list]

## Iteration notes
[If any shot needs to be regenerated: which skill to return to]
```

**Step 8: Close the pipeline**

> "Pipeline completo. Todos los documentos de producción están en `production/`. El plan de montaje está en `production/assembly.md`."

Show the production file tree:

```
production/
  art-direction.md          ✅
  visual-tokens.md          ✅
  style-prefix.md           ✅ [LOCKED]
  scene-geography.md        ✅ [LOCKED]
  character-bible/          ✅
  shot-list.md              ✅
  assets/                   ✅
  prompts/                  ✅
  audit-log.md              ✅
  continuity-report.md      ✅
  audio-design.md           ✅
  assembly.md               ✅
```

If iteration is needed: return to the governing skill — `scene-geography` for spatial failures, `character-bible` for identity drift, `stills-audit-loop` for image failures, `audio-crafting` for audio issues.

## Output

**File:** `production/assembly.md`
**This is the final skill in the pipeline.**

## Cut Principles

| Principle | Application |
|---|---|
| Cut on performance | Cut at the emotional peak of the shot, not completion of action |
| L-cut | Previous audio continues under new visual — incoming sound leads |
| J-cut | Next audio begins before visual cut — space breathes before cut |
| Hold on stillness | The most loaded moments are often visually static — resist cutting away |
| Discard earned shots | A technically perfect shot that breaks rhythm is discarded. Generation count is not a reason to keep it. |

## Red Flags

| Thought | Reality |
|---|---|
| "I'll generate all shots first, then assemble" | Shots without editorial reference accumulate in the wrong direction. |
| "I'll use every shot I generated" | The edit is a curation. Shots that don't earn their place are discarded. |
| "I'll add music after the edit is locked" | Music shapes the edit. Add from the first clip. |
| "This shot has a continuity error but it's the best take" | Continuity errors break immersion permanently. Regenerate. |
| "I'll fix the color grade in post" | Wildly different base looks cannot be corrected by grading. Fix the reference. |
