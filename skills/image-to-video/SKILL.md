---
name: image-to-video
description: Use when converting approved stills to video — reads all locked documents, generates complete video prompts per shot using the 5 sub-disciplines, then hands off to audio-crafting
---

# Image to Video

## Overview

Video generation is not image generation with more steps. The failure modes are different, the prompt structure is different, and the iteration volume is different. "Prompt and pray" is the industry default — 1 usable clip in 64 attempts is a real published benchmark. The five sub-disciplines replace random iteration with structured discipline.

## The Iron Law

```
LOCK THE KEY VISUAL STILL BEFORE ANY VIDEO GENERATION — THE APPROVED STILL DEFINES ALL LIGHTING, STYLE, AND GEOGRAPHY FOR THE VIDEO
```

## Active Process

Announce: "Usando `image-to-video` para generar los prompts de video para cada plano."

**Step 1: Read context**

Read `production/style-prefix.md`, `production/scene-geography.md`, `production/shot-list.md`, `production/continuity-report.md`.

**Step 2: Ask which shot**

> "¿Para qué Shot ID generamos el prompt de video? Compartí el still aprobado de ese plano."

**Step 3: Generate the video prompt using all 5 sub-disciplines**

**Sub-discipline 1 — Spatial Layout Block (required in every video prompt):**

```
SPATIAL ANCHOR:
Reference: [shot ID still] — attached as reference image.
Camera is positioned at [landmark visible in reference].
[Specific object] is visible on the [left/right] of frame.
The camera does NOT move closer to [object]. Move the camera instead.
```

**Sub-discipline 2 — Continuous Shot Rule:**

Never define time-based beats. Write one continuous motion arc.

❌ Never: "First 3 seconds: she sits. Then 3 seconds: she turns."
✅ Always: "She sits in the stillness of someone who has been waiting for a very long time, and that stillness slowly resolves into a turn toward the door — as if she finally heard something she had been dreading."

**Sub-discipline 3 — Emotion-Based Direction:**

Describe the character's feeling, not their physical action.

| Mechanical | Emotion-based |
|---|---|
| "He turns left and walks to the window" | "He moves as if being dragged forward by grief — slower than tired, slower than exhausted" |
| "She looks up" | "She lifts her gaze the way someone does when they've decided something they didn't want to decide" |

**Sub-discipline 4 — Reference Upload Order:**

State in the prompt:
```
REFERENCE UPLOAD ORDER:
1. Character sheet(s) — uploaded first
2. Location reference — uploaded second
3. Props — uploaded third
```

**Sub-discipline 5 — Batch discipline:**

Tell the user:
> "Batches recomendados: 4-8 videos por iteración. Si los 4-8 fallan con el mismo problema estructural → corregir el prompt. Si 3 iteraciones fallan (12-24 videos, mismo problema) → descartá el prompt, empezá desde 3 anchors."

**Step 4: Generate the full video prompt**

Combine all 5 sub-disciplines with the style prefix and geography into one complete prompt. Write it directly.

**Step 5: Write the video prompt**

Append to `production/prompts/[shot-id].md` under a `## Video Prompt` section.

**Step 6: Common failure patterns**

| Failure | Fix |
|---|---|
| Wrong camera angle | Anchor camera to named landmark: "in the reference image, [landmark] is on the [left/right]" |
| Unwanted cuts in continuous shot | Remove all "first X seconds / then X seconds" language |
| Character moves too fast | Replace speed with emotion: "she is heartbroken" produces slower movement than "she walks slowly" |
| Room geometry breaks | Re-anchor each element to its position in reference sheet |
| Only 1 in 64 usable | This is normal. Batch is process. Read failures diagnostically. |

**Step 7: Next shot or transition**

> "Prompt de video para Shot [ID] guardado. ¿Generamos el siguiente o ya están todos?"

When all video prompts are done:
> "Todos los prompts de video generados. Invocando `audio-crafting`..."

Invoke `ai-filmmaking:audio-crafting`.

## Output

**File:** Appended to `production/prompts/[shot-id].md` (video section)
**Read by:** `assembly-compositing`

## Red Flags

| Thought | Reality |
|---|---|
| "I'll describe the shot in natural language" | Natural language produces the model's interpretation. Use the 5 sub-disciplines. |
| "More detail will fix the spatial problem" | After 3 failed iterations, more detail is not the fix. Scrap and rebuild from 3 anchors. |
| "72 generations for one shot means something is wrong with my concept" | It means you're doing the work correctly. Process, not failure. |
| "The video model will add good music" | Generated audio is non-separable. Never allow generated music. Always include audio constraint. |
