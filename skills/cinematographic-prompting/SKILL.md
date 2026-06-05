---
name: cinematographic-prompting
description: Use when writing any image or video generation prompt — enforces the 7-field structure that eliminates spatial ambiguity, character drift, and style inconsistency
---

# Cinematographic Prompting

## Overview

Natural language prompts produce natural language problems: the model fills in what you didn't specify with its own defaults. In a dramatic scene with two characters, a specific camera angle, a locked geography, and a defined lighting contract — "its own defaults" means everything breaks. The 7-field structure eliminates ambiguity by forcing you to specify every dimension of the image before the model generates it.

## The Iron Law

```
EVERY PROMPT MUST INCLUDE ALL 7 FIELDS AND THE REFERENCE SYNTAX — INCOMPLETE PROMPTS ARE REFUSED
```

## The 7 Fields

### SUBJECT
Who is in this shot and what is their locked identity reference.

```
SUBJECT: @character1 (Character A) | @character2 (Character B)
```

Use `@ref` syntax — do not describe the character in text when a locked reference exists. `@ref` overrides description. Text description drifts across generations; `@ref` does not.

### ACCIÓN
What the character intends or feels — not what they physically do.

```
ACCIÓN: She is waiting — exhausted, beyond impatience, simply enduring
```

- ✅ Emotional intention: "he moves as if being dragged forward by grief"
- ❌ Mechanical action: "he turns left and walks to the fridge"

The model interprets emotional intention as performance style, which is more stable than action description. "He is heartbroken" produces better results than "he looks sad and walks slowly."

### ENTORNO
The set — geography, objects, surfaces.

```
ENTORNO: <<<img1>>> — hospital waiting room, terracotta back wall, bench against wall,
         clock above bench, vending machine right wall warm amber, glass door left cold
```

- `<<<img1>>>` anchors the scene to the approved key visual
- Add specific object positions from the geography document
- This field re-states the geography to prevent model drift

### LENTE/CÁMARA
The focal length equivalent and camera position.

```
LENTE/CÁMARA: 50mm equivalent, CAM 1 MASTER position (frontal, wide, both characters visible)
```

Reference the floor plan camera by name. This anchors the camera position to the geography document rather than leaving it to model interpretation.

Common focal equivalents and their effects:
- 24-28mm: wide, environmental, slight distortion at edges
- 35mm: naturalistic, documentary feel
- 50mm: neutral, "what the eye sees"
- 85mm: slight compression, flattering, portraiture
- 135mm+: strong compression, subject isolated from background

### LUZ
Light direction, temperature, contrast, and reflection contract.

```
LUZ: cold blue-green institutional fluorescent from left corridor,
     warm tungsten amber from right vending machine,
     low ambient fill, deep shadows, compressed blacks.
     LEFT glass: cold reflection of corridor light.
     RIGHT vending glass: warm amber reflection of internal light.
```

State the reflection contract explicitly if reflective surfaces are in the frame. A reflection that shows the wrong temperature or the wrong content fails the continuity audit.

### ESTILO/REF
Style prefix tokens + moodboard tokens.

```
ESTILO/REF: [paste full style prefix here]
            analog night photography, cinematic psychological drama,
            textured matte surfaces, soft film grain, 24fps motion
```

The style prefix goes here verbatim — do not abbreviate it. Every generation needs the full prefix to produce consistent results.

### NEGATIVO
Exhaustive list of what must not appear.

Structure the NEGATIVO in categories:

```
NEGATIVO — Character violations:
  Do not move Character A. Do not move Character B. Do not swap left and right.
  Do not change wardrobe, age, hairstyle, posture, or emotional tone.

NEGATIVO — Spatial violations:
  Do not cross the 180-degree axis. Do not redesign the room.
  Do not move the bench, clock, vending machine, or plastic bag.

NEGATIVO — Style violations:
  No daylight. No bright modern lobby. No saturated colors.
  No decorative or artificial-looking reflections.

NEGATIVO — Technical violations:
  No motion blur. No noise artifacts. No fake depth of field.
  No visible AI artifacts. No deformed hands or faces.
```

A comprehensive NEGATIVO is not paranoia — it is the difference between getting the shot and regenerating 20 times.

## Critical Blocking Rule

Include verbatim in every multi-character prompt:

```
CRITICAL BLOCKING RULE:
Do not move the characters.
Do not re-stage the scene.
Do not re-block the scene.
Only move the camera.
```

## On Prompt Length

Comprehensive prompts (100-200 lines) are sometimes necessary for multi-character spatial scenes with complex geography and lighting contracts. This is correct and expected — do not shorten them for the sake of brevity.

However: **for single-character or simple shots, 2-3 prioritized cinematic cues often outperform over-specified prompts.**

When a detailed prompt fails repeatedly (3+ batches, same failure): strip to 3 core anchors and rebuild incrementally. Over-specification can confuse the model. The failure pattern tells you which field is causing the conflict.

## Red Flags

| Thought | Reality |
|---|---|
| "I'll describe the character instead of using @ref" | Text description drifts. @ref is the only stable identity anchor. |
| "The NEGATIVO field is optional" | Without negative constraints, the model fills in its own defaults. Those defaults break the scene. |
| "I'll just describe what I want naturally" | Natural description lacks the structure models need for spatial and identity consistency. |
| "Longer prompts are always better" | Over-specification can confuse models. When 3+ attempts fail, strip to 3 anchors and rebuild. |
| "I'll add the style prefix next time" | There is no "next time" without it. Every generation drifts without the prefix. |

**REQUIRED NEXT SKILL:** ai-filmmaking:stills-audit-loop
