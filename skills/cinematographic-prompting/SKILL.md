---
name: cinematographic-prompting
description: Use when generating any image — reads all locked production documents and writes a complete 7-field prompt for the requested shot to production/prompts/[shot-id].md
---

# Cinematographic Prompting

## Overview

Natural language prompts produce natural language problems: the model fills in what you didn't specify with its own defaults. In a dramatic scene with two characters, a specific camera angle, and a locked geography — "its own defaults" means everything breaks. The 7-field structure eliminates ambiguity by specifying every dimension before the model generates.

## The Iron Law

```
EVERY PROMPT MUST INCLUDE ALL 7 FIELDS AND THE REFERENCE SYNTAX — INCOMPLETE PROMPTS ARE REFUSED
```

## Active Process

Announce: "Usando `cinematographic-prompting` para escribir el prompt completo del plano."

**Step 1: Read all locked documents**

Read:
- `production/style-prefix.md` — the locked prefix (full, verbatim)
- `production/scene-geography.md` — axis, screen positions, objects, cameras, blocking rule
- `production/shot-list.md` — all planned shots
- `production/character-bible/character-*.md` — all character descriptors

**Step 2: Ask which shot**

> "¿Para qué Shot ID escribimos el prompt? (Ver `production/shot-list.md` para la lista completa)"

**Step 3: Generate the complete 7-field prompt**

Using ALL information from the locked documents, write the complete prompt. Do not ask questions — all information is in the documents. Generate directly.

**The 7 Fields:**

```
SUBJECT:
@characterN — [Character name], [screen position per geography].
[Additional characters if multi-character shot]
@ref overrides all text description.

CRITICAL BLOCKING RULE:
[Copy verbatim from production/scene-geography.md]

ACCIÓN:
[Emotional intention — not mechanical action]
[Example: "She is enduring — not performing patience, simply waiting"]
[Never: "She turns left and walks to the window"]

ENTORNO:
<<<img1>>> — [location name]
[All objects with their locked positions from scene-geography.md]
[Camera name and position from scene-geography.md]

LENTE/CÁMARA:
[Focal equivalent — derive from camera name in geography]
[Static or moving — describe the motion as continuous arc if moving]

LUZ:
[Temperature and direction per geography document]
[Reflection contract per geography document — stated explicitly]

ESTILO/REF:
[Style prefix — paste full, verbatim from production/style-prefix.md]
[Additional atmosphere tokens from art-direction.md]

NEGATIVO — Character violations:
[Do not move, swap, change wardrobe, age, hair of any character]
[Do not add characters]

NEGATIVO — Spatial violations:
[Do not cross the 180° axis]
[Do not move any locked objects]
[Do not redesign the space]

NEGATIVO — Lighting violations:
[Do not show wrong temperature on wrong side]
[Do not show wrong reflection temperature]

NEGATIVO — Style violations:
[All exclusions from style-prefix.md exclusion list]

NEGATIVO — Technical violations:
[No AI artifacts, no deformed faces/hands, no plasticky textures]
```

**Step 4: Show and request approval**

Show the complete prompt. Ask:
> "¿Aprobás este prompt para Shot [ID] o ajustamos algo?"

If adjustments needed → update and show again. Repeat until approved.

**Step 5: Write the prompt**

Write to `production/prompts/[shot-id].md` with the full prompt plus the audit checklist.

**Step 6: Ask about next shot**

> "Prompt de Shot [ID] guardado. ¿Generamos el siguiente plano o ya tenés todos?"

- If more shots → ask which shot ID and repeat from Step 2
- If all shots done → transition

**Step 7: Transition**

> "Todos los prompts generados. Invocando `stills-audit-loop` para auditar las imágenes generadas..."

Invoke `ai-filmmaking:stills-audit-loop`.

## Output

**File:** `production/prompts/[shot-id].md` (one per shot)
**Read by:** `stills-audit-loop`, `image-to-video`

## On Prompt Length

Comprehensive prompts (80-150 lines) are correct and expected for multi-character spatial scenes. Do not shorten for brevity.

For single-character or simple shots: 2-3 prioritized cinematic cues often outperform over-specified prompts.

When 3+ batches fail with the same prompt structure: strip to 3 core anchors (identity reference, scene continuity reference, camera position) and rebuild one field at a time.

## Red Flags

| Thought | Reality |
|---|---|
| "I'll describe the character instead of using @ref" | Text description drifts. @ref is the only stable identity anchor. |
| "The NEGATIVO field is optional" | Without negative constraints, the model fills in its own defaults. Those defaults break the scene. |
| "I'll just describe what I want naturally" | Natural description lacks the structure models need. |
| "Longer prompts are always better" | When 3+ attempts fail, strip to 3 anchors and rebuild. Over-specification can confuse models. |
| "I'll add the style prefix later" | Every generation without the prefix produces a different film. There is no later. |
