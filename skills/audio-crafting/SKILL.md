---
name: audio-crafting
description: Use after all video clips are approved — reads the art direction document, designs the complete 3-layer audio world with specificity, writes production/audio-design.md, then hands off to assembly-compositing
---

# Audio Crafting

## Overview

AI video models produce non-separable generated audio. Any audio the model generates is baked into the clip and cannot be removed in post — it becomes part of the image. The constraint is therefore absolute: all AI generation must use the no-generated-music, no-subtitles constraint in the style prefix. The audio layer is designed separately and composited manually. This skill designs the complete audio world for the piece.

## The Iron Law

```
NO GENERATED MUSIC — ALL AUDIO IS DESIGNED HERE AND COMPOSITED MANUALLY IN POST
```

## Active Process

Announce: "Usando `audio-crafting` para diseñar el mundo sonoro de la producción."

**Step 1: Read context**

Read `production/art-direction.md` — specifically the emotional register, spatial description, time/era, and visual concept sentence. These drive all audio decisions.

**Step 2: Ask one clarifying question**

> "¿Hay alguna fuente de sonido específica del espacio que sea dramáticamente importante? (por ejemplo: el ruido de un aparato médico, lluvia contra una ventana, una conversación lejana)"

Wait for the answer. This single answer is enough — all other audio design decisions come from the art-direction document.

**Step 3: Design Layer 1 — Voice**

Define the voice layer with specificity:

```
VOICE LAYER:
- Dialogue present: [yes/no]
- If yes: acoustic treatment (close-mic intimacy, room reverb, distance)
- Voice-off / narration: [yes/no, and if yes: describe tone and placement]
- Silence as voice: [where silence carries more than speech]
- Generation tool: HeyGen / ElevenLabs / on-set recording
```

**Step 4: Design Layer 2 — Ambient / Environmental**

This is the primary audio layer. Environmental sound effects only. No generated music.

```
AMBIENT LAYER:
- Primary room tone: [the acoustic character of the space]
- Continuous sounds: [what runs under everything]
- Intermittent sounds: [what arrives and departs]
- Off-screen acoustic world: [what do we hear from outside the frame]
- Silence regions: [scenes or moments that are intentionally silent]
```

**Step 5: Design Layer 3 — Score (manual only)**

```
SCORE LAYER:
- Score present: [yes/no]
- If yes: instrumentation, tempo, emotional direction
- Source: MANUAL ONLY — library or external composer. No AI-generated music.
- Entry points: [exact moments where score enters]
- Exit points: [exact moments where score exits or fades]
```

**Step 6: Write the complete audio design**

Write to `production/audio-design.md`:

```markdown
# Audio Design
## [Project name]

> Output of `ai-filmmaking:audio-crafting`

## Audio Philosophy
[One paragraph: how sound reinforces the emotional register]

## LAYER 1 — Voice
[Complete design with acoustic notes]

## LAYER 2 — Ambient / Environmental
[Complete design with specific sounds per scene or shot]

## LAYER 3 — Score
[Design with source, timing, and sync points]

## Absolute Constraints
- Generated audio from video models: PROHIBITED
- No generated music
- No subtitles
- Style prefix constraint: "environmental sound effects only, no generated music, no subtitles"

## Mix Order for Post
1. Ambient first
2. Voice second
3. Music third
```

**Step 7: Transition**

> "Diseño de audio guardado en `production/audio-design.md`. Invocando `assembly-compositing` para el montaje final..."

Invoke `ai-filmmaking:assembly-compositing`.

## Output

**File:** `production/audio-design.md`
**Read by:** `assembly-compositing`

## The Three-Layer Model

| Layer | Content | Source |
|---|---|---|
| Voice | Dialogue, narration, silence | Recorded on set or generated via voice cloning |
| Ambient | Room tone, signature sounds, off-screen world | SFX library or field recording |
| Score | Music, leitmotif, silence regions | Manual library or external composer |

**Critical constraint:** Mix in order — ambient → voice → music. Reversing buries layers.

## Red Flags

| Thought | Reality |
|---|---|
| "I'll let the video model add ambient sound" | Generated audio is baked into the clip. Cannot be removed. |
| "A little generated music as placeholder" | There is no placeholder — it becomes the final audio. |
| "The sound design can wait until post" | Post has no layer to work with if it isn't designed here. |
| "Ambient sound isn't dramatic" | Room tone defines whether a scene breathes or suffocates. Always dramatic. |
