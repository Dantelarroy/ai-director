---
name: asset-pipeline
description: Use when you need to generate a location, prop, or environmental element — creates each asset as a standalone approved reference before it appears in any scene
---

# Asset Pipeline

## Overview

Generating a character inside a location in one prompt causes spatial confusion: the model has two competing reference anchors and interprets them against each other. The character may appear inside the location image itself. The location may warp around the character. The geometry fails. Generate each asset — location, character, props — as a standalone element. Bring them together only at video generation.

## The Iron Law

```
EVERY LOCATION AND PROP IS A SEPARATE APPROVED ASSET BEFORE IT APPEARS IN ANY GENERATED SCENE
```

## Location Asset Protocol

**Step 1: Generate without characters**
Describe only the space. No character presence, no clothing, no action. The space must be complete and convincing before anyone enters it.

**Step 2: Generate minimum 2 views**
- Primary view (the MASTER shot angle)
- Reverse angle (looking back from the opposite side)

Both views together give the video model enough spatial context to understand the room from any camera position.

**Step 3: Combine into a reference sheet**
Place both views in a single 16:9 image (top panel + bottom panel, or side by side). Label which is which. This becomes the single location reference attached to every video prompt.

**Step 4: Iterate until all pass**
The location is not locked until all of these pass:
- [ ] Correct spatial layout (objects where the geography document says they are)
- [ ] Correct lighting (matches style prefix temperatures and directions)
- [ ] Correct materials (no plasticky textures, correct surfaces)
- [ ] No unwanted elements (no characters, no objects not in the geography document)

**Common location generation failures:**

| Problem | Fix |
|---|---|
| Plasticky textures | Add: "light atmospheric haze, soft film grain, photorealistic surface texture" |
| Wrong spatial layout | Regenerate from full prompt. Don't keep editing the same image — detail loss accumulates with each edit. |
| Model moves prop instead of camera | Write: "camera positioned at [anchor] — do NOT move [prop] closer to camera" |
| Hallway/door disappears after edits | Include it explicitly in every prompt iteration — it is not implied |
| Image looks "too new" or "too clean" | Add: "worn, lived-in surfaces, aged materials, revealed pipes, slight disrepair" |

**Step 5: Lock as named asset**
Give it a clear name (e.g., "location-waiting-room-primary", "location-waiting-room-reverse"). Reference this name consistently in all subsequent prompts.

## Prop Asset Protocol

**Simple props** (a single object, no characters): generate close-up on neutral background. One image is sufficient if it is clear and well-lit.

**Complex props** (a photo wall, a collage, multiple Polaroids, a setup with many items):
- Generate each element individually
- Assemble in Photoshop (or equivalent)
- Import the assembled composite as a single prop asset
- Never generate a 12-Polaroid photo wall in one prompt — 12 faces = 12 drifted faces

**Props that appear in video**:
- The prop must be visible and correctly positioned in the location reference sheet
- When generating video, reference the location sheet — the prop position is already visible in it
- Do not upload the prop separately for video unless it needs to be the primary subject of a shot

## Reference Image Upload Order

This order matters. Video and image models weight earlier references more heavily.

```
1. Character sheet(s)    ← uploaded first — gets most model weight
2. Location reference    ← uploaded second
3. Props                 ← uploaded third
```

If a character and a location both appear in a prompt, upload the character first. If the location goes first, the model may warp the character to fit the space rather than placing the character in the space.

## Red Flags

| Thought | Reality |
|---|---|
| "I'll generate the character in the room in one shot" | Spatial confusion causes both to drift. Generate separately. |
| "I'll fix location details after placing the character" | Character + location combined = harder to edit either. Lock location first. |
| "One view of the location is enough" | Different camera angles reveal different parts of the space. 2+ views required. |
| "I'll generate the photo wall in one prompt" | 12 faces in one prompt = 12 drifted faces. One image per Polaroid, assemble in post. |
| "The location looks fine on the first try" | Check against the geography document. "Fine looking" ≠ "spatially correct". |

**REQUIRED NEXT SKILL:** ai-filmmaking:cinematographic-prompting
