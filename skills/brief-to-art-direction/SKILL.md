---
name: brief-to-art-direction
description: Use when you have a dramatic idea, scene, or script — runs a guided Q&A and writes production/art-direction.md before any image is generated
---

# Brief to Art Direction

## Overview

A narrative brief is not a visual brief. "A woman waits for news in a hospital" tells you the story. It tells you nothing about the color temperature of the light, the emotional register of the space, or what the film must never look like. This skill runs a structured Q&A to extract the visual DNA from the narrative, then writes the Art Direction Document that every subsequent skill will read.

## The Iron Law

```
NO PRODUCTION STEP BEGINS BEFORE THE DRAMATIC BRIEF IS FULLY TRANSLATED INTO VISUAL DNA
```

## Active Process

Announce: "Usando `brief-to-art-direction` para construir el documento de dirección de arte."

**Step 1: Check for existing document**

If `production/art-direction.md` exists → read it, show a summary, and ask:
> "Ya existe un Art Direction Document. ¿Lo retomamos o empezamos de cero?"

If it doesn't exist → proceed to Step 2.

**Step 2: Ask 5 questions — one at a time. Wait for each answer before asking the next.**

**Pregunta 1 — Registro emocional:**
> "¿Cuál es el registro emocional de esta historia? (drama psicológico, comedia oscura, documental, thriller, poético, otro)"

**Pregunta 2 — El espacio:**
> "¿Cómo se siente el espacio donde transcurre? No qué contiene — cómo se siente. (institucional, doméstico, liminal, opresivo, íntimo, etc.)"

**Pregunta 3 — Tensión visual central:**
> "¿Cuál es la tensión visual central? Ejemplos: frío exterior vs. calor interior / espacio vacío vs. figuras ocupadas / luz controlada vs. caos"

**Pregunta 4 — Personajes:**
> "¿Cuántos personajes hay y qué cargan emocionalmente que nunca dicen en voz alta?"

**Pregunta 5 — Tiempo y época:**
> "¿Qué hora del día, estación, época? ¿Hay algún elemento temporal que sea dramáticamente importante?"

**Step 3: Propose the Visual Concept**

Synthesize one sentence from the answers. Show it and ask:
> "Concepto visual propuesto: '[una oración]'. ¿Aprobás o ajustamos?"

Iterate until approved.

**Step 4: Generate and write the full document**

Write all 8 sections, then save to `production/art-direction.md`:

```markdown
# Art Direction Document
## [Project name or scene description]

> Output of `ai-filmmaking:brief-to-art-direction`

### 1. Visual Concept
[One sentence]

### 2. Emotional Register and Tone
[2-3 sentences]

### 3. Space Description
[How the space feels — not what it contains]

### 4. Character Visual Archetypes
[Per character: what they carry physically, what their body shows]

### 5. Lighting Philosophy
[One dominant contrast]

### 6. Color Philosophy
[Palette family, accent color, exclusions]

### 7. Atmosphere Tokens
[7-10 words or short phrases for prompt use]

### 8. Exclusion List — What This Film Is NOT
[5-7 specific exclusions]
```

**Step 5: Transition**

> "Art Direction Document guardado en `production/art-direction.md`. Invocando `moodboard-extraction`..."

Invoke `ai-filmmaking:moodboard-extraction`.

## Output

**File:** `production/art-direction.md`
**Read by:** `moodboard-extraction`, `style-prefix`, `scene-geography`, `character-bible`, `audio-crafting`

## Red Flags

| Thought | Reality |
|---|---|
| "The brief is clear enough to start generating" | A clear narrative brief is not a visual brief. They are different documents. |
| "I'll figure out the look as I generate" | Visual drift is the #1 cause of incoherent AI films. Fix the look first. |
| "The moodboard will define the look" | Moodboard extracts existing looks. Art Direction defines YOUR look. Both required. |
| "5 questions is too many" | These 5 answers determine every visual decision that follows. They take 2 minutes. |
