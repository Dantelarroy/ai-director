---
name: assembly-compositing
description: Use when assembling individual shots into a finished film — enforces editorial discipline and the edit-as-you-go workflow that produces coherent short-form cinema
---

# Assembly and Compositing

## Overview

Generating all shots first, then assembling, is the wrong order. Shots generated without an editorial reference accumulate in the wrong direction — the shot that works for the 60-second version is different from the shot that works for the 90-second version, and you discover this too late. Edit as you go. The timeline is the truth; the pile of generated clips is not.

## The Iron Law

```
CUT TO THE RHYTHM OF PERFORMANCE, NOT TO VISUAL VARIETY — EVERY SHOT MUST EARN ITS PLACE IN THE EDIT
```

## Edit-As-You-Go Protocol

**Do not wait until all shots are generated to begin editing.** Add each approved clip to the timeline immediately after it passes the stills audit loop and continuity check.

Order of operations per shot:
1. Shot passes stills-audit-loop
2. Shot passes continuity-checker cross-shot validation
3. Shot is converted to video via image-to-video
4. Clip is added to the timeline immediately
5. The edit is re-evaluated after each addition

**Edit with music from day one.** Do not assemble all clips then add music. The music reveals what duration each shot actually needs — a beat that requires 4 seconds in your head may need 3 in context, or 6. This cannot be discovered from a clip pile.

## Editorial Principles

**Cut on performance, not on action.** The cut point is the emotional peak of the shot, not the completion of the physical action.

**L-cuts:** The previous shot's audio continues under the new visual. A character hears something and turns — the sound of what she hears leads into the next shot, before she has finished turning.

**J-cuts:** The next shot's audio begins before the visual cut. The hum of the waiting room begins while we are still in the corridor.

**Hold on stillness.** The most emotionally loaded moments are often the most visually static. Resist the urge to cut away from a still face. The audience reads everything that happens in that stillness.

**The discipline of duration:** A shot lasts as long as the performance requires. 4 seconds is not better or worse than 8 seconds — the performance tells you which.

## The Discarding Rule

A technically perfect shot that does not serve the rhythm of the edit is discarded.

"I generated 64 takes to get this" is not a reason to use it. If the shot breaks the rhythm, slows the momentum, or adds visual information the edit does not need — discard it.

The edit is a curation, not a showcase of what was generated.

**What gets discarded:**
- Shots that break the pacing of adjacent shots
- Shots with continuity failures that were not caught before video generation
- Shots that are technically correct but emotionally redundant with adjacent shots
- Alternative takes that are good but not better than what's already in the cut

**Never apologize for discarding generated material.** The goal is the finished film.

## VFX and Compositing Order

Apply in this sequence to avoid compounding corrections:

**1. Composite separately-generated elements**
Props generated independently (photo walls, Polaroid collections, handmade objects) must be composited into the scene in Photoshop or equivalent before being imported as final clips. Never composite in the timeline — the temporal interface is not designed for spatial compositing.

**2. Color grade**
90% of the color grade should already be baked in through reference work and the style prefix. The post grade is correction, not creation. If shots look wildly different from each other at this stage, the reference work was insufficient — post cannot fix this.

Film grain: add as a unified post layer across the entire film (not per-shot), so grain is consistent regardless of minor style differences between shots.

**3. Audio mix**
Layer in order: ambient first, then voice, then music. This order ensures each layer is audible when the next is added. Reversing the order buries ambient under music and voice under music.

**4. Final export**
- Target format: 24fps (already locked in style prefix)
- Aspect ratio: as defined in style prefix
- Export at highest quality from the timeline before compressing for delivery

## Red Flags

| Thought | Reality |
|---|---|
| "I'll generate all shots first, then assemble" | Shots generated without editorial reference accumulate in the wrong direction. Edit as you go. |
| "I'll use every shot I generated" | The edit is a curation. Every shot that earns its place is in. Every shot that doesn't is discarded. |
| "I'll add music at the end after the edit is locked" | Music shapes the edit. Add it from the first clip. |
| "This shot has a continuity error but it's the best take" | Continuity errors break immersion permanently. Regenerate. There is no "best take" with a visible error. |
| "I'll fix the color grade in post" | Post color grading on footage with wildly different base looks produces visual incoherence. Fix the reference. |
| "The composited elements can be done in the timeline" | Timeline compositing lacks the precision needed for spatial element integration. Use a dedicated compositing tool. |

**Pipeline complete.** If you need to iterate on the film, return to the skill that governs the failing element:
- Wrong geography in video → ai-filmmaking:scene-geography
- Character identity drift → ai-filmmaking:character-bible
- Stills failing audit → ai-filmmaking:stills-audit-loop
- Continuity failures → ai-filmmaking:continuity-checker
- Video generation failures → ai-filmmaking:image-to-video
- Audio not working → ai-filmmaking:audio-crafting
