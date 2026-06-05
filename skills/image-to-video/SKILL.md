---
name: image-to-video
description: Use when converting approved stills to video clips — enforces the five disciplines that eliminate the most common video generation failures
---

# Image to Video

## Overview

Video generation is not image generation with more steps. The failure modes are different, the prompt structure is different, and the iteration volume is different. "Prompt and pray" is the industry default — 1 usable clip in 64 attempts is a real published benchmark. This skill replaces random iteration with structured discipline. Five sub-disciplines govern everything.

## The Iron Law

```
LOCK THE KEY VISUAL STILL BEFORE ANY VIDEO GENERATION — THE APPROVED STILL DEFINES ALL LIGHTING, STYLE, AND GEOGRAPHY FOR THE VIDEO
```

## Sub-Discipline 1: Spatial Layout Block

Every video prompt must begin with a spatial anchor section that describes camera position relative to visible landmarks in the reference sheet — not in abstract coordinates, but in terms of what is actually visible.

```
SPATIAL ANCHOR:
Reference: [name of approved still] — attached as reference image.
Camera is positioned at [landmark visible in reference, e.g., "the doorway on the right"].
[Specific object] is visible on the [left/right] of frame.
The camera does NOT move closer to [object]. The camera moves laterally only.
```

This anchors the video model to the spatial reality of the reference, not to a reinterpreted or hallucinated space. Without this block, the model re-stages the scene in every generation.

## Sub-Discipline 2: Continuous Shot Rule

```
NEVER DEFINE BEATS OR SECONDS IN A CONTINUOUS SHOT PROMPT — EVERY TIME-SEGMENT DESCRIPTION IS A CUT
```

This is the most common video prompting error. If your prompt says:

> "First 3 seconds: she sits still. Next 3 seconds: she turns her head. Final 3 seconds: she stands."

The video model reads this as three separate shots with cuts between them. Even with no intended cut, the model generates three segments that are visually discontinuous.

**Write one continuous motion arc instead:**
- ❌ "First 3 seconds she is still, then she slowly turns to look at the door"
- ✅ "She is still — the stillness of someone who has been waiting for a very long time — and the weight of that stillness slowly resolves into a turn toward the door, as if she finally heard something she had been dreading"

One continuous description = one continuous clip.

## Sub-Discipline 3: Emotion-Based Direction

Describing what a character feels produces better performance than describing what they physically do.

| Mechanical description | Emotion-based description |
|---|---|
| "He turns left and walks to the window" | "He moves as if being dragged forward by grief — each step slower than tired, slower than exhausted" |
| "She looks up" | "She lifts her gaze the way someone does when they've decided something they didn't want to decide" |
| "He opens the door" | "He opens the door with the precise care of someone trying not to wake the last thing that is still sleeping" |

The model interprets emotional intention as performance style. Mechanical description produces mechanical animation. Emotional intention produces acting.

## Sub-Discipline 4: Reference Upload Order

Order matters. Video models weight earlier references more heavily.

```
Upload order:
1. Character sheet(s)      ← first — identity gets priority
2. Location reference      ← second — spatial context
3. Props                   ← third — object context
```

If a character and a location compete, the character must win. Upload order determines which reference the model trusts more when they conflict.

## Sub-Discipline 5: Batch and Iteration Discipline

- Standard batch: 4-8 videos per prompt iteration
- If 4-8 videos fail with the same structural problem → fix the prompt, do not batch more of the same
- If 3 prompt iterations fail with the same core problem (12-24 videos) → scrap the prompt, rebuild from 3 anchors
- When a prompt has accumulated many amendments and is still failing → start completely fresh

**The industry baseline: 1 usable clip in 64 attempts.** This is not failure. This is process. Every failed generation tells you what the prompt needs. Read the failures diagnostically.

## Common Failure Patterns

| Failure | Cause | Fix |
|---|---|---|
| Wrong camera angle | Camera not anchored to named landmark | Add spatial anchor block: "in the reference image, the [landmark] is on the [left/right] — camera is at [position]" |
| Character enters from wrong side | Entry direction not stated relative to room element | Add: "enters from the [left/right], coming from the direction of the [door/corridor/window visible in reference]" |
| Unwanted cuts in continuous shot | Time-based beat definitions in prompt | Remove all "first X seconds / then X seconds" language. Describe as one continuous motion arc. |
| Character moves too fast | Pace described mechanically, not emotionally | Replace speed description with emotional state. "He is heartbroken" produces slower movement than "he walks slowly." |
| Props appear in wrong location | Prop referenced by name, not by position in reference sheet | Reference by position: "the plastic bag visible on the bench in the reference image, left of center" |
| Room geometry breaks mid-clip | Model re-stages the space | Upload reference sheet again; add spatial anchor block; name each landmark relative to its position in the reference sheet |
| Character identity drift in motion | Reference not dominant enough | Simplify text description; let the character reference carry more weight; add a close angle character reference |
| Camera drifts toward object | Spatial constraint not explicit | Add: "the camera does NOT move closer to [object]. [Object] stays at its position in the reference image." |

## On Volume

Expect to generate significant batches for complex shots — 48, 72, or more attempts for a single critical shot is within the normal range for professional AI filmmaking. The goal is to develop a diagnostic relationship with the failures, not to avoid them. Each failure teaches the next prompt revision.

Track what you learn. If generation 12 fails the same way as generation 4, the prompt structure is not working and needs to be rebuilt, not adjusted.

## Red Flags

| Thought | Reality |
|---|---|
| "I'll describe the shot in natural language and see what happens" | Natural language produces the model's interpretation of your intent. Use the 5 sub-disciplines. |
| "I'll add more detail to fix the spatial problem" | After 3 failed iterations, more detail is not the fix. Scrap and rebuild from 3 anchors. |
| "72 generations for one shot means something is wrong with my concept" | It means you're doing the work correctly. Process, not failure. |
| "The video model will add good ambient music" | Generated audio is non-separable from dialogue. Never allow generated music in the video model. Include: "environmental sound effects only, no generated music." |
| "I'll fix the spatial problem by moving the character" | The character and all objects are fixed. Only the camera moves. |

**REQUIRED NEXT SKILL:** ai-filmmaking:audio-crafting
