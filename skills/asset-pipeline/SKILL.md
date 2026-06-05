---
name: asset-pipeline
description: Use after shot-list-design — generates complete prompts for all location and prop assets, writes production/assets/, then hands off to cinematographic-prompting
---

# Asset Pipeline

## Overview

Generating a character inside a location in one prompt causes spatial confusion: the model has two competing reference anchors and interprets them against each other. Location and character must be generated separately. This skill generates the prompts for all location assets (minimum 2 views each) and props, so they exist as locked, approved references before any character enters a scene.

## The Iron Law

```
EVERY LOCATION AND PROP IS A SEPARATE APPROVED ASSET BEFORE IT APPEARS IN ANY GENERATED SCENE
```

## Active Process

Announce: "Usando `asset-pipeline` para generar los prompts de todos los assets de locación y props."

**Step 1: Read context**

Read `production/scene-geography.md` and `production/style-prefix.md`. Identify all locations and significant props from the geography document.

**Step 2: Generate location prompts**

For each location, generate two prompts — primary view and reverse angle:

**Location prompt structure:**
```
[Style prefix — full, verbatim]

LOCATION: [name]
View: [primary / reverse angle]
Space: [complete spatial description from scene-geography.md]
Objects: [all significant objects with their locked positions]
Light: [temperature and direction per the geography document]
Materials: [surfaces, textures, worn/aged as needed]
No characters. No people. Space only.

NEGATIVO:
[No characters, no people, no silhouettes]
[No objects not listed in the geography document]
[No modern redesign of the space]
[No daylight if night scene]
```

Show each prompt and ask: "¿Ajustamos algo antes de generar?"

**Step 3: Write location prompts**

Write to `production/assets/locations.md` — all location prompts ready to copy-paste into the generation tool.

**Step 4: Generate prop prompts (if needed)**

For each significant prop that appears in character scenes:

```
PROP: [name]
[Style prefix — full, verbatim]
Close-up, neutral background. Object as subject.
[Specific description of the prop]
```

Complex props (photo walls, collages, multiple items): one prompt per element. Never generate multiple distinct objects in one prompt.

Write to `production/assets/props.md`.

**Step 5: Communicate the reference upload order**

Tell the user:

> "Una vez que generes los assets, el orden de upload para cada prompt de personaje-en-locación es:
> 1. Character sheet(s) — primero
> 2. Location reference — segundo
> 3. Props — tercero
> El modelo da más peso a los primeros uploads."

**Step 6: Common failures reference**

| Problem | Fix |
|---|---|
| Plasticky textures | Add: "light atmospheric haze, soft film grain, photorealistic surface texture" |
| Wrong spatial layout | Regenerate from full prompt. Don't keep editing the same image — detail loss accumulates. |
| Model moves prop instead of camera | Write: "camera positioned at [anchor] — do NOT move [prop] closer to camera" |
| Location looks too new/clean | Add: "worn, lived-in surfaces, aged materials, slight disrepair" |

**Step 7: Transition**

> "Prompts de assets guardados en `production/assets/`. Invocando `cinematographic-prompting` para el primer plano..."

Invoke `ai-filmmaking:cinematographic-prompting`.

## Output

**Files:** `production/assets/locations.md`, `production/assets/props.md`
**Read by:** `cinematographic-prompting`, `image-to-video`

## Red Flags

| Thought | Reality |
|---|---|
| "I'll generate the character in the room in one shot" | Spatial confusion causes both to drift. Generate separately. |
| "One view of the location is enough" | Different camera angles reveal different parts. 2+ views required. |
| "I'll generate the photo wall in one prompt" | 12 faces in one prompt = 12 drifted faces. One image per element. |
| "The location looks fine on the first try" | Check against the geography document. "Fine looking" ≠ "spatially correct". |
