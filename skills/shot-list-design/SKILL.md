---
name: shot-list-design
description: Use after character-bible, before generating any scene image — creates the shot list that governs all image and video generation for the scene
---

# Shot List Design

## Overview

Improvised shots produce uneditable material. A shot generated without a planned relationship to adjacent shots cannot be cut cleanly — the axis may be wrong, the screen positions may be reversed, the coverage may be redundant. The shot list is not bureaucracy: it is the editorial structure of your film built before the first generation.

## The Iron Law

```
LOCK THE SHOT LIST BEFORE GENERATING ANY IMAGE — NO SPONTANEOUS OR EXPLORATORY SHOTS DURING PRODUCTION
```

## Shot List vs. Image Clusters

Two valid methodologies — choose based on what you're producing:

**Shot List (this skill)**
For: dramatic scenes requiring spatial continuity, character interaction, 180° axis discipline, scenes that will be edited in a specific sequence.
Structure: precise camera coverage, mandatory sequence, continuity rules.

**Image Clusters**
For: exploratory world-building, location aesthetic passes, abstract or poetic sequences where you generate broadly and select during editing.
Structure: narrative function buckets (Arrival / Observation / Realization / Presence), not specific shots.

If you are making a dramatic scene with dialogue, character blocking, and continuous geography: use Shot List.

## Shot List Format

Generate using Claude as an assistant. Output format: two-column HTML.
- Left column: scene description (what happens, who, where, emotional intention)
- Right column: the prompt for that shot

Target unit: **4-6 second clips** for video generation.
- 4-6 seconds = one clear action or moment
- Shorter clips have higher generation success rates
- Multiple 4-6s clips cut together more cleanly than one long clip
- Do NOT target 15-second clips — they compound failures

## Coverage Types

| Type | Camera Position | Primary Subject | When to Use |
|---|---|---|---|
| MASTER | Wide — all characters visible | Both characters + full space | Establish geography, open/close scene |
| OTS A→B | Behind Character A, toward B | Character B | Reaction shots, dialogue addressed to B |
| OTS B→A | Behind Character B, toward A | Character A | Reaction shots, dialogue addressed to A |
| COVERAGE A | Character A as primary | Character A | Character A's internal moment |
| COVERAGE B | Character B as primary | Character B | Character B's internal moment |
| INSERT | Close on object or detail | Object / hand / face detail | Narrative emphasis |

## Per-Shot Entry (All Fields Required)

```
Shot ID:           [e.g., S1A, S1B, S2A]
Type:              [from coverage types above]
Camera:            [floor plan camera reference — e.g., "CAM 1 MASTER"]
Primary subject:   [Character A / Character B / both / object]
Action:            [what happens in this 4-6 second clip]
Duration target:   [4-6 seconds]
References:        [@character1, @character2, <<<img1>>>]
Continuity notes:  [what must match adjacent shots]
```

## Coverage Logic for a 5-Shot Short Film

A coherent 1-minute short with continuous geography typically needs:

1. **MASTER** — establish the space, both characters, all objects
2. **COVERAGE A** — Character A's isolated moment
3. **COVERAGE B** — Character B's isolated moment
4. **OTS A→B** — the interaction from A's perspective
5. **OTS B→A** — the interaction from B's perspective

This gives the editor options at every moment. Missing coverage = missing editorial flexibility.

## Red Flags

| Thought | Reality |
|---|---|
| "I'll generate the best angles organically" | Organic generation violates the 180° axis and produces uneditable material. |
| "15 seconds per clip gives me more to work with" | 4-6 seconds = more control, higher success rate, cleaner edits. |
| "I'll improvise shots during generation" | Improvised shots have no continuity anchor. They cannot be cut with planned shots. |
| "I only need the master shot" | Without coverage shots, you have no editorial options. One long master = one long take. |
| "The shot list takes too long to write" | Writing a 5-shot list takes 15 minutes. Regenerating 20 failed shots takes 4 hours. |

**REQUIRED NEXT SKILL:** ai-filmmaking:asset-pipeline
