---
name: character-bible
description: Use before generating any character image — creates the identity anchor that ensures the same person appears across all shots at any camera angle
---

# Character Bible

## Overview

One frontal character sheet is not enough. When the camera angle changes, the model drifts. It reinterprets hairstyle, skin tone, age, wardrobe, and posture independently at each angle. By the time you have 5 camera angles, you have 5 slightly different people. Locking character identity requires 8-10 references across angles AND environments, not one studio portrait.

## The Iron Law

```
NO CHARACTER GENERATION BEFORE THE BIBLE IS WRITTEN AND THE CHARACTER SHEET IS APPROVED AT MULTIPLE ANGLES
```

## The Character Bible (Per Character, All Fields Required)

**Age**
Specific range, not a vague category.
- ✅ "30-45, the weight of a decade of quiet professional disappointment"
- ❌ "middle-aged"

**Emotional State**
What they carry that is never stated aloud. This controls posture, micro-expression, eye quality.
- ✅ "contained exhaustion, restrained vulnerability — she is holding herself together and has been for hours"
- ❌ "tired and sad"

**Face: 15-20 Specific Descriptors**
Do not rely on @ref alone for description — the descriptors reinforce identity when the angle shifts.

Required descriptor categories:
- Hair color (specific: "ash blonde", not "blonde")
- Hair texture and style (specific: "straight, pulled back tightly, not a strand loose")
- Skin tone (specific: "pale northern European skin, slight blue undertone under eyes")
- Eye color
- Eye shape (specific: "slightly hooded, heavy upper lid")
- Nose shape
- Jaw and chin shape
- Cheekbone prominence
- Mouth (size, set — relaxed or held?)
- Age markers (where do they show their age?)
- What is distinctive and unchangeable about this face?

**Body**
- Height impression (tall and imposing / compact and contained / average and unremarkable)
- Posture (rigid / collapsed / held / open / closed)
- Build (specific: "the body of someone who was once athletic and has become still")

**Wardrobe: Specific Items with Specific Colors**
Every item named and described.
- ✅ "dusty pale pink short-sleeved collared dress, matte cotton, slightly fitted, below the knee"
- ❌ "pink dress"

Include: upper garment, lower garment or dress, shoes, any accessories. Nothing vague.

**Hands**
Position at rest. What they reveal.
- "Hands clasped together on her lap — fingers interlaced, the grip of someone waiting without knowing how long"

**The Non-Negotiable List**
What NEVER changes about this character across any shot:
- [list every element that is locked]

## Character Sheet Generation Protocol

Follow these steps in order:

1. **Frontal portrait** — white studio background, soft uniform studio lighting, character sheet purpose (legibility, not drama). Face fully visible.
2. **3/4 angle** — same background, same lighting, head turned approximately 45°
3. **Profile** — same background, same lighting, full side view
4. **In-scene neutral** — the actual set environment, neutral action (seated, standing, looking forward)
5. **In-scene emotional** — same environment, the specific emotion of the scene
6. **Additional angles** — generate until you have 8-10 usable references covering the range of angles the camera will use

Select the best 8-10 images as the locked reference set. Discard the rest.

## Reference Syntax

Lock these before any scene generation:

```
@character1  =  Character A — locked identity reference
@character2  =  Character B — locked identity reference
<<<img1>>>   =  Scene continuity reference (approved key visual / master shot)
```

When generating any image or video:
- Use `@characterN` — do not describe the character in text if @ref is available
- `@ref` overrides description. If both conflict, @ref wins.
- If the model ignores @ref (rare): reduce description tokens and let @ref do more work

## Red Flags

| Thought | Reality |
|---|---|
| "The AI will understand what I mean by 'middle-aged woman'" | It won't. 15-20 specific descriptors minimum. |
| "One frontal character sheet is enough" | Camera angle changes cause identity drift. 8-10 references required. |
| "I'll generate the character sheet later" | Generating scenes before character lock means regenerating everything. |
| "Close enough is fine for a secondary character" | Every character who appears in 2+ shots needs a bible. |
| "I'll use text description instead of @ref" | Text description drifts. @ref is the only stable identity anchor. |

**REQUIRED NEXT SKILL:** ai-filmmaking:shot-list-design
