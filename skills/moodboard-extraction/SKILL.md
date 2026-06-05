---
name: moodboard-extraction
description: Use when you have collected reference images and need to extract reusable visual rules before generating any image — never use reference images directly in prompts
---

# Moodboard Extraction

## Overview

Reference images carry unwanted passengers: specific faces, intellectual property, compositional accidents, and contextual meaning that doesn't belong in your film. You cannot upload a moodboard image to a prompt and expect the AI to extract only what you want. You extract the DNA — the transferable rules — and those rules go into prompts, not the images.

## The Iron Law

```
NO IMAGE GENERATION BEFORE THE VISUAL TOKEN DOCUMENT IS WRITTEN — NEVER USE REFERENCE IMAGES DIRECTLY IN PROMPTS
```

## Moodboard Composition (Minimum 9 Images)

Collect references across these categories — weak coverage produces weak rules:

| Category | Minimum | What to look for |
|---|---|---|
| Lighting references | 2 | Direction, temperature, contrast, falloff |
| Color/palette references | 2 | Dominant tones, accent colors, relationships |
| Composition/framing references | 2 | Shot size, symmetry, negative space, geometry |
| Texture/material references | 2 | Surface quality, aging, finish (matte vs gloss) |
| Atmosphere/mood synthesis | 1 | The feeling of the whole — the image that synthesizes all others |

## Per-Image Analysis (All 6 Categories Required)

For each image in the moodboard, analyze and document:

**1. Stylistic register and visual language**
What is the cinematic grammar? (analog / documentary / editorial / thriller / etc.)
What is the camera's relationship to the subject? (observer / intruder / neutral / intimate)

**2. Light: direction, intensity, temperature, contrast**
- Where does the key light come from?
- What temperature is it? (tungsten warm / fluorescent cold / daylight neutral)
- How much contrast? (high / medium / low)
- What does it leave in shadow?

**3. Dominant color palette + accent colors**
- Name the 2-3 dominant colors
- Name the 1 accent color (what stands out)
- Describe the color relationship (complementary / tetradic / monochromatic / etc.)

**4. Materials, textures, surfaces**
- What surfaces are present? (stucco / ceramic / vinyl / glass / metal / fabric)
- What is their finish? (matte / semi-gloss / reflective)
- What do they communicate? (institutional / domestic / aged / pristine)

**5. Composition, framing, scale, visual hierarchy**
- Shot type (wide / medium / close-up / extreme close-up)
- Symmetry level (rigid / partial / asymmetric)
- Where is the subject in the frame?
- What is the negative space doing?

**6. Emotional atmosphere and repeatable visual resources**
- What emotion does this image evoke?
- What specific elements create that emotion and could be reused?

## Cross-Reference Analysis (After All Images)

Answer these three questions by comparing all images:

**What do all images share?** → These are your RULES. Apply them to every prompt.

**What tensions exist between images?** → These are CREATIVE CHOICES to make deliberately.

**What is excluded in all of them?** → These become your EXCLUSION LIST.

## The Visual Token Document (Output)

Write this document. It is the deliverable of this skill. Every section is required.

```
STYLE TOKENS:       [3-5 words: e.g., "analog night photography, cinematic psychological drama"]
LIGHTING TOKENS:    [3-5 words: e.g., "warm tungsten overhead, cold blue exterior, deep shadows"]
COLOR TOKENS:       [palette names: e.g., "deep navy, near-black brown, burnt amber, dusty pink"]
MATERIAL TOKENS:    [surfaces: e.g., "textured matte stucco, dark ceramic tile, brown vinyl chairs"]
COMPOSITION TOKENS: [framing rules: e.g., "frontal rigid portrait, empty chairs as negative space"]
ATMOSPHERE TOKENS:  [emotional words: e.g., "silent waiting, contained anxiety, nighttime stillness"]
EXCLUSION RULES:    [what to never generate: e.g., "no daylight, no saturated colors, no smiling"]
BASE FORMULA:       [one sentence: Space + Light + Figure + Color = Feeling]
```

## Red Flags

| Thought | Reality |
|---|---|
| "I'll upload the moodboard images directly to the prompt" | Direct references pull unwanted specifics: faces, IP, compositional accidents. Extract the rules. |
| "9 images is too many" | Fewer references = weaker cross-validation = weaker rules. 9 is the minimum. |
| "I'll do this mentally, I don't need to write it" | Unwritten rules drift. The token document must be written to be applied consistently. |
| "The colors speak for themselves" | Color names in prompts drift. Name them explicitly ("deep navy blue", not "dark blue"). |

**REQUIRED NEXT SKILL:** ai-filmmaking:style-prefix
