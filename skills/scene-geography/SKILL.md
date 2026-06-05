---
name: scene-geography
description: Use before generating any image of a scene — locks the spatial rules that every shot must respect, including character screen positions, object placements, camera axis, and reflection contracts
---

# Scene Geography

## Overview

AI image models have no persistent spatial memory. Each generation is stateless. If you do not enforce geography in every prompt, the model will place characters, objects, and light sources wherever it wants — and it will choose differently each time. Shot 3 will contradict Shot 1. Both will need to be regenerated.

## The Iron Law

```
LOCK THE FLOOR PLAN BEFORE GENERATING ANY IMAGE — MOVING A CHARACTER OR OBJECT AFTER APPROVAL BREAKS ALL PRIOR SHOTS
```

## The Geography Lock Document

Write this document before the first generation. Every section is required.

### Axis Definition

The 180° axis is the invisible line the camera never crosses.

- Define the line: e.g., "axis runs left-to-right along the bench, Character A on the left, Character B on the right"
- Once set: all cameras stay on one side of this line
- Crossing it reverses all screen positions and breaks all cut points

### Character Screen Positions

These positions are permanent. They do not change regardless of camera angle.

```
Character A: always screen-LEFT
Character B: always screen-RIGHT
```

Even when the camera moves to the opposite side for an OTS shot, Character A must still read as the "left" character in the narrative. The geometry shifts — the dramatic logic does not.

### Object Positions

Every significant object gets a fixed position anchored to a wall or side. Write them all:

```
[Object name]: [wall/side], [always describes: light quality, material, etc.]
Example: "Vending machine: right wall, always warm amber glow"
Example: "Clock: back wall, above bench, centered"
Example: "Plastic bag: center of bench, between the two characters, never moved"
```

### Reflection Contract

If reflective surfaces exist (glass doors, windows, vending machines, mirrors), define what each one shows:

```
LEFT surface must show:  [temperature] light, [specific elements reflected]
RIGHT surface must show: [temperature] light, [specific elements reflected]
```

Reflections must be physically coherent — what they show must correspond to what exists in that direction. "Decorative" reflections that don't match the scene geometry fail the audit.

### Camera Positions

Define one entry per planned shot, referencing the floor plan:

```
CAM 1 MASTER:   [position on floor plan] — [what it covers] — [facing direction]
CAM 2:          [position] — [coverage] — [facing]
CAM 3:          [position] — [coverage] — [facing]
```

## Critical Blocking Rule

Include this verbatim in every multi-character prompt:

```
CRITICAL BLOCKING RULE:
Do not move the characters.
Do not re-stage the scene.
Do not re-block the scene.
Only move the camera.
```

This is not descriptive text — it is a hard constraint that prevents the model from "helpfully" repositioning characters to match what it thinks the camera angle should show.

## Red Flags

| Thought | Reality |
|---|---|
| "I'll figure out the space as I generate" | Shot 3 will contradict Shot 1. Both need regeneration. |
| "The AI will understand the spatial relationship" | AI has no persistent spatial memory. You must re-state geography in every prompt. |
| "I'll fix wrong screen positions in post" | Wrong screen positions cannot be fixed in post without reshooting. |
| "The floor plan is just a rough guide" | It is law. Every violation requires regenerating all affected shots. |
| "I'll move this object in the next shot, it doesn't matter" | Every object position is a continuity commitment. Moving anything breaks prior shots. |

## Continuity Cascade

Understand what each element commits you to:

- **Character A screen position** → all 5 camera shots must respect it
- **Object position** → every shot where that object is visible must match
- **Reflection contract** → every shot where that surface is visible must show the correct reflection
- **180° axis** → ALL shots stay on one side

**REQUIRED NEXT SKILL:** ai-filmmaking:character-bible
