---
name: scene-geography
description: Use before generating any image — runs a Q&A to construct the floor plan, locks the 180° axis and all spatial rules, and writes production/scene-geography.md
---

# Scene Geography

## Overview

AI has no persistent spatial memory. Without an explicit floor plan locked before generation, Shot 3 will contradict Shot 1 and both will need regeneration. The 180° axis violation — crossing the line that reverses all screen positions — is the most common and most expensive error in AI filmmaking. It cannot be fixed in post. This skill locks the spatial contract before any generation begins.

## The Iron Law

```
LOCK THE FLOOR PLAN BEFORE GENERATING ANY IMAGE — MOVING A CHARACTER OR OBJECT AFTER APPROVAL REQUIRES REGENERATING ALL PRIOR SHOTS
```

## Active Process

Announce: "Usando `scene-geography` para construir y bloquear el plano de espacio."

**Step 1: Read context**

Read `production/art-direction.md`. Use the space description as the starting point.

**Step 2: Ask 4 questions — one at a time**

**Pregunta 1 — El espacio:**
> "Describí la habitación o espacio donde transcurre la escena. ¿Qué hay en las paredes, qué objetos son importantes, qué tan grande es?"

**Pregunta 2 — Los personajes:**
> "¿Cuántos personajes hay en la escena y dónde están ubicados? ¿Están sentados, de pie, en movimiento?"

**Pregunta 3 — Fuentes de luz:**
> "¿De dónde viene la luz? ¿Hay superficies reflectantes importantes (vidrio, espejo, ventana)?"

**Pregunta 4 — El movimiento de cámara:**
> "¿Hay movimiento de cámara o son planos fijos? ¿Hay un plano máster que establezca todo el espacio?"

**Step 3: Construct the floor plan**

Based on the answers, build the geography document section by section in real time:

1. Define the 180° axis from the character positions
2. Assign screen positions (Character A = screen LEFT, Character B = screen RIGHT — never changes)
3. Lock each significant object to a wall/side with temperature
4. Define the reflection contract (which surface = which temperature)
5. Propose 3-5 named camera positions based on the space

**Step 4: Show the geography summary and request approval**

Show a text-based summary:

```
AXIS: [description of the line]

LEFT SIDE:  [what's here — light temperature, objects, characters]
CENTER:     [what's here]
RIGHT SIDE: [what's here — light temperature, objects, characters]

Character A: ALWAYS SCREEN LEFT — [where specifically]
Character B: ALWAYS SCREEN RIGHT — [where specifically]

Cameras:
CAM 1 MASTER: [position and coverage]
CAM 2: [position and coverage]
...
```

Ask:
> "¿Esta geografía refleja el espacio que tenés en mente? Una vez aprobada queda bloqueada."

**Step 5: Write the locked document**

Write to `production/scene-geography.md`:

```markdown
# Scene Geography — [LOCKED]
## [Project name]

> Output of `ai-filmmaking:scene-geography`
> NEVER MODIFY after first image is approved. Every violation requires regenerating all affected shots.

## The 180° Axis
[Definition + DO NOT CROSS statement]

## Character Screen Positions
[Table: Character | Screen Position | Location | Notes]

## Object Positions — All Locked
[Table: Object | Wall/Side | Position | Temperature]

## Reflection Contract
[Table: Surface | Temperature | What It Reflects]

## Camera Positions
[CAM 1 through CAM N — position, angle, coverage]

## Critical Blocking Rule
[Verbatim — copy into every multi-character prompt]

## Quick Reference
[LEFT / CENTER / RIGHT summary]
```

**The Critical Blocking Rule** — always include this block verbatim at the end of the document:

```
CRITICAL BLOCKING RULE:
Do not move the characters.
Do not re-stage the scene.
Do not re-block the scene.
Only move the camera.
Character A remains SCREEN LEFT at all times.
Character B remains SCREEN RIGHT at all times.
```

**Step 6: Transition**

> "Scene Geography guardada y bloqueada en `production/scene-geography.md`. Invocando `character-bible`..."

Invoke `ai-filmmaking:character-bible`.

## Output

**File:** `production/scene-geography.md` [LOCKED]
**Read by:** `character-bible`, `shot-list-design`, `cinematographic-prompting`, `stills-audit-loop`, `continuity-checker`, `image-to-video`

## Red Flags

| Thought | Reality |
|---|---|
| "I'll figure out the space as I generate" | Shot 3 will contradict Shot 1. Both need regeneration. |
| "The AI will understand the spatial relationship" | AI has no persistent spatial memory. You must enforce geography in every prompt. |
| "I'll fix wrong positions in post" | Wrong screen positions cannot be fixed in post without reshooting. |
| "The floor plan is just a rough guide" | It is law. Every violation requires regenerating all affected shots. |
