---
name: shot-list-design
description: Use after character-bible — reads the geography and character documents, asks about dramatic beats, proposes the complete shot list, and writes production/shot-list.md
---

# Shot List Design

## Overview

Improvised shots produce uneditable material. A shot generated without a planned relationship to adjacent shots cannot be cut cleanly — the axis may be wrong, the screen positions may be reversed, the coverage redundant. The shot list is the editorial structure of your film, built before the first generation.

## The Iron Law

```
LOCK THE SHOT LIST BEFORE GENERATING ANY IMAGE — NO SPONTANEOUS OR EXPLORATORY SHOTS DURING PRODUCTION
```

## Active Process

Announce: "Usando `shot-list-design` para diseñar el shot list antes de cualquier generación."

**Step 1: Read context**

Read `production/art-direction.md`, `production/scene-geography.md`, and all files in `production/character-bible/`.

**Step 2: Ask about dramatic beats**

> "¿Cuántos momentos o beats dramáticos tiene la escena? Describílos brevemente — no te preocupés por los planos, solo qué pasa emocionalmente y cuándo."

Wait for the answer.

**Step 3: Ask methodology**

> "¿Esta escena requiere continuidad espacial precisa (personajes interactuando, planos que deben cortar entre sí) o es más exploratoria (world-building, ambiente, selección en montaje)?"

- Si requiere continuidad → Shot List (este skill)
- Si es exploratoria → Image Clusters (nombrarlos por función: Arrival / Observation / Realization / Presence)

**Step 4: Propose the shot list**

Based on the beats and the geography, generate the complete shot list. Include for each shot:

```
Shot ID:         [e.g., S1A]
Type:            [MASTER / OTS A→B / OTS B→A / COVERAGE A / COVERAGE B / INSERT]
Camera:          [from production/scene-geography.md — use exact camera name]
Primary subject: [Character A / B / both / object]
Action:          [what happens in this 4-6 second clip — emotion-based]
Duration:        [4-6 seconds]
References:      [@character1, @character2, <<<img1>>>]
Continuity:      [what must match adjacent shots]
```

Show the full proposed list and ask:
> "¿Este shot list cubre los beats de la escena? ¿Ajustamos algo?"

Iterate until approved.

**Step 5: Write the document**

Write to `production/shot-list.md`:

```markdown
# Shot List
## [Project name / scene name]

> Output of `ai-filmmaking:shot-list-design`
> Unit: 4-6 second clips. All shots respect the locked geography.

## Shots

[Shot table — all entries]

## Coverage Summary
MASTER: [which shot]
CHARACTER A coverage: [which shots]
CHARACTER B coverage: [which shots]
OTS shots: [which shots]
INSERTS: [which shots]
```

**Step 6: Transition**

> "Shot List guardado en `production/shot-list.md`. Invocando `asset-pipeline` para generar los assets de locación y props antes de los prompts de planos..."

Invoke `ai-filmmaking:asset-pipeline`.

## Output

**File:** `production/shot-list.md`
**Read by:** `asset-pipeline`, `cinematographic-prompting`, `stills-audit-loop`, `continuity-checker`, `image-to-video`, `assembly-compositing`

## Coverage Types

| Type | Camera Position | Primary Subject | When |
|---|---|---|---|
| MASTER | Wide — all characters visible | Both + full space | Establish geography, open/close scene |
| OTS A→B | Behind Character A, toward B | Character B | Dialogue addressed to B, reaction |
| OTS B→A | Behind Character B, toward A | Character A | Dialogue addressed to A, reaction |
| COVERAGE A | Character A primary | Character A | Character A's internal moment |
| COVERAGE B | Character B primary | Character B | Character B's internal moment |
| INSERT | Close on object or detail | Object / hand / face | Narrative emphasis |

## Red Flags

| Thought | Reality |
|---|---|
| "I'll generate the best angles organically" | Organic generation violates the 180° axis and produces uneditable material. |
| "15 seconds per clip gives me more to work with" | 4-6 seconds = more control, higher success rate, cleaner edits. |
| "I'll improvise shots during generation" | Improvised shots have no continuity anchor. They can't be cut with planned shots. |
| "I only need the master shot" | Without coverage, you have no editorial options. |
