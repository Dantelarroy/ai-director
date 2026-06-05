---
name: audio-crafting
description: Use when designing the audio layer of a film — enforces three-layer discipline before any mixing begins
---

# Audio Crafting

## Overview

Audio is not decoration added after the picture is locked. Audio shapes the editing rhythm, carries the emotional weight that image cannot, and defines the physical reality of the space. An AI-generated film without designed audio is a demo reel. A film with designed audio is a film. The three-layer discipline is not overhead — it is the minimum structure that produces a coherent sound world.

## The Iron Law

```
AUDIO MUST BE DESIGNED IN THREE LAYERS BEFORE MIXING — NEVER ADD SOUND REACTIVELY OR DECORATIVELY
```

## The Three Layers

### Layer 1: Voice

If characters speak, voice is the foundation everything else is built around.

**Voice cloning (recommended approach):**
- Provide a voice sample (minimum 30 seconds of clean audio, one speaker, no background noise)
- Write the script with full punctuation — pauses, breath marks, ellipses affect timing
- Generate with HeyGen, ElevenLabs, or equivalent voice cloning tool
- Sync to video in post: the cloned voice goes over the generated video, not into it

**Why not use the video model's audio:**
Video models that generate audio embed it non-separably into the clip. If the character speaks and the model generates their voice, that voice cannot be extracted, equalized, or replaced in post. Always generate video with `environmental sound effects only, no generated music, no subtitles` in the style prefix, then add voice in post.

**Silent characters:**
Silence is a design choice. If characters do not speak, design the silence — identify what ambient sound fills the moment and what the absence of voice is meant to convey.

### Layer 2: Ambient (Space Sound)

Every physical space has a specific sonic signature. Generic ambient fails because it sounds like "atmosphere" rather than a place. Specific ambient sounds real.

**How to approach:**
1. Name the space: hospital waiting room / parking garage at night / kitchen at 3am
2. List the specific sounds that space actually makes
3. Select and layer: which sounds run continuous, which are intermittent

**Example — hospital waiting room at night:**
- Continuous: fluorescent hum (low, variable pitch), HVAC draft (white noise background)
- Intermittent: distant PA announcement (no words audible), vinyl chair squeak (from 3 seats away), single set of shoes on linoleum (corridor, approaching then receding)
- Absent: traffic, voices, music

**Ambient as emotional instrument:**
Ambient can support or contradict the visual emotion. A cold institutional hum under a moment of human connection deepens the isolation. Silence under the same moment says something else. Design this intentionally.

### Layer 3: Music

Music should enter when the character's emotion cannot be expressed any other way. It is not a default filler for pauses.

**Map the arc before selecting any track:**
1. Mark the dramatic beats on the timeline
2. Identify where tension builds, where it peaks, where it releases
3. Map when music should enter, when it should withdraw
4. Let the structure determine the music — not the other way around

**Silence is valid and often superior** for contained dramatic scenes. A quiet scene in a hospital waiting room does not need music. The ambient layer carries the weight. Music entering late — as a last resort — hits harder than music throughout.

**When selecting a track:**
- Look for tracks that can be cut, looped, or faded without seams
- Avoid tracks with strong melodic hooks in the first 10 seconds — they dominate everything
- Favor tone over melody for short-form dramatic content

## Critical Constraint

Include this in every video generation prompt's style prefix:

```
environmental sound effects only, no generated music, no subtitles
```

Generated music embedded in video cannot be separated from dialogue or ambient in post. This constraint must appear in the style prefix and must never be removed.

## Production Timeline

Audio design does not happen after picture lock — it happens during production:

1. **Pre-production**: design the voice approach and ambient world per location
2. **During stills**: confirm the space matches the designed sonic world
3. **During video**: generate with the correct audio constraint in style prefix
4. **Post-production**: layer voice, then ambient, then music. Mix in that order.

## Red Flags

| Thought | Reality |
|---|---|
| "I'll add ambient sound to make it feel alive" | "Ambient sound" without specificity sounds like a plugin preset. Name the space and list its actual sounds. |
| "The video model generated audio sounds fine" | It is non-separable from the picture. Fine for demos. Not for cinema. |
| "I'll add music to fill the silence" | Silence IS a design choice. In a contained space under emotional tension, silence is often more powerful than any track. |
| "I'll design audio after the edit is done" | Audio shapes the edit. Add music from day one of assembly. |
| "The voice-over can be fixed later" | Voice timing is locked to the edit. Lock voice timing before locking the edit. |

**REQUIRED NEXT SKILL:** ai-filmmaking:assembly-compositing
