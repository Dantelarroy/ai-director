---
name: style-prefix
description: Use after moodboard-extraction, before any prompt generation — creates the locked style document that must prefix every single prompt in the production
---

# Style Prefix

## Overview

Without a locked style prefix, every generation makes its own decisions about lighting temperature, grain, color grade, and aspect ratio. In a 5-shot film, this produces 5 visually incompatible clips. With 15 people on a team, it produces 15 different films. The style prefix is not a suggestion — it is infrastructure.

## The Iron Law

```
ALL PROMPTS MUST INCLUDE THE LOCKED STYLE PREFIX — NO EXCEPTIONS, EVEN FOR TEST GENERATIONS
```

## What the Style Prefix Contains (All 6 Elements Required)

**1. Film Stock / Grain**
The physical texture that unifies all shots.
- Example: `soft analog film grain, 24fps motion characteristics, subtle halation, slight vintage softness`
- 24fps is the default for filmic motion — other framerates read as video, not cinema

**2. Lighting Rules**
The governing constraint on all light in the film.
- Example: `natural light only, key light from sky and windows only` (no artificial key lights)
- Or: `practical light sources only — no studio fill, no beauty lighting`
- Be restrictive. Loose lighting rules produce wildly different results across generations.

**3. Color Grade**
The palette that all shots share.
- Use token names from the moodboard-extraction output, not hex codes
- Example: `muted tetradic palette — deep navy blue, near-black brown, burnt amber, dusty pink, olive gray green`
- State what is excluded: `no saturated primaries, no neon, no pure white`

**4. Aspect Ratio**
Lock this once. Never change mid-production.
- `21:9` for theatrical cinema (the frame most audiences associate with "film")
- `16:9` for streaming/broadcast
- Changing aspect ratio mid-production requires regenerating everything

**5. Audio Constraint for Video Generation**
This is the most commonly forgotten element and the most consequential.

```
CRITICAL: environmental sound effects only — no generated music, no subtitles
```

Video generation models (Seedance, Kling, Runway, etc.) will add music to emotional scenes if not explicitly prohibited. Generated music is baked into the audio track. It cannot be separated from dialogue or ambient sound in post-production. You will lose the scene.

**6. Exclusion Master List**
Consolidate all exclusions from Art Direction + Moodboard documents into one list.
- Example: `no daylight, no bright modern spaces, no saturated colors, no smiling, no dynamic handheld camera, no lens flare, no decorative lighting, no digital artifacts`

## Format

Write as a dense block, 8-12 lines maximum. Every word earns its place.

```
[Film stock/grain tokens]
[Lighting rule]
[Color palette tokens]
[Aspect ratio]
[Audio constraint]
[Exclusion list]
```

## When to Update

**Never**, mid-production. The style prefix is locked when production begins.

If you discover you need to change it after generating the first image: you must regenerate everything that used the old prefix. This is not optional — inconsistent prefixes produce inconsistent films.

## Rationalization Prevention

| Excuse | Reality |
|---|---|
| "I'll remember to add style rules to each prompt manually" | You won't. The prefix is infrastructure, not a reminder. |
| "The style prefix is too restrictive" | Constraints produce coherence. Looseness produces drift. |
| "I'll update it after a few test generations" | Test generations set visual expectations. Lock before the first generation. |
| "The video model will add tasteful music" | Generated music cannot be separated from dialogue in post. It destroys the scene. Always prohibit it. |
| "I'll add the audio constraint later" | "Later" means after a model has already baked music into 20 clips. |

**REQUIRED NEXT SKILL:** ai-filmmaking:scene-geography
