---
name: character-bible
description: Use before generating any character image — runs a guided Q&A per character and writes production/character-bible/character-[N].md for each
---

# Character Bible

## Overview

One frontal character sheet is not enough. When the camera angle changes, the model drifts. By Shot 5, you have 5 slightly different people. Locking character identity requires 15-20 specific descriptors AND 8-10 reference images across angles AND environments. This skill builds that system through a structured Q&A for each character.

## The Iron Law

```
NO CHARACTER GENERATION BEFORE THE BIBLE IS WRITTEN AND THE CHARACTER SHEET IS APPROVED AT MULTIPLE ANGLES
```

## Active Process

Announce: "Usando `character-bible` para construir la identidad visual bloqueada de cada personaje."

**Step 1: Read context**

Read `production/art-direction.md` and `production/scene-geography.md` to understand the characters and the space they inhabit.

**Step 2: Ask how many characters**

> "¿Cuántos personajes necesitan biblia? (Solo los que aparecen en 2 o más planos necesitan una.)"

**Step 3: For each character — ask in sequence**

Run through these questions for one character before moving to the next.

**Pregunta 1 — Nombre de trabajo y rol:**
> "¿Cómo llamamos a este personaje durante la producción? ¿Qué rol tiene en la escena?"

**Pregunta 2 — Edad y estado emocional:**
> "¿Qué rango de edad tiene? ¿Y qué carga emocionalmente que nunca dice en voz alta en la escena?"

**Pregunta 3 — Descripción física (15-20 descriptores):**
> "Describí la cara con la mayor especificidad posible: color y textura de pelo, tono de piel, color de ojos, forma de mandíbula, pómulos, boca, nariz, qué marcas de edad tiene y dónde, qué es inconfundible de este rostro."

**Pregunta 4 — Cuerpo y postura:**
> "¿Qué impresión de altura da? ¿Cómo es su postura? ¿Qué revela su cuerpo sobre su interior?"

**Pregunta 5 — Vestuario completo:**
> "Describí cada prenda con especificidad: nombre, color exacto, material, corte, talla. Nada vago."

**Pregunta 6 — Manos:**
> "¿Cómo tiene las manos en reposo en esta escena? ¿Qué revelan?"

**Step 4: Generate the bible for this character**

Using all answers, generate the complete character bible and write to `production/character-bible/character-[N].md`:

```markdown
# Character Bible — [Character name/letter]
## [Project name]

> Output of `ai-filmmaking:character-bible`

## Working Reference
@character[N] = [Character name/letter] — LOCKED identity reference

## Core Identity
- Age range: [specific]
- Emotional state (never stated aloud): [specific]

## Face — 15-20 Specific Descriptors
[All descriptors from Q3 — each on its own line]

## Body
- Height impression: [specific]
- Posture: [specific]
- Build: [specific]

## Wardrobe — Complete
[Each item on its own line: garment / color / material / cut]

## Hands
[Position at rest + what they reveal]

## The Non-Negotiable List
What NEVER changes across any shot:
[Every element that is locked — derive from all of the above]

## Character Sheet Generation Protocol
Generate in this order before any scene:
1. Frontal portrait — white studio background, uniform studio lighting
2. 3/4 angle — same background, same lighting
3. Profile — same setup, full side view
4. In-scene neutral — actual set environment, neutral action
5. In-scene emotional — same environment, the scene's specific emotion
6. 3+ additional angles covering the range of camera positions planned

Approve best 8-10 as the locked reference set.
```

**Step 5: Ask about next character**

> "Biblia de [Character N] guardada. ¿Hay otro personaje o continuamos al siguiente paso?"

If more characters → repeat from Step 3.
If done → transition.

**Step 6: Transition**

> "Character Bible completa guardada en `production/character-bible/`. Invocando `shot-list-design`..."

Invoke `ai-filmmaking:shot-list-design`.

## Output

**Files:** `production/character-bible/character-[N].md` (one per character)
**Read by:** `shot-list-design`, `cinematographic-prompting`, `stills-audit-loop`, `continuity-checker`

## Red Flags

| Thought | Reality |
|---|---|
| "The AI will understand what I mean by 'middle-aged woman'" | It won't. 15-20 specific descriptors minimum. |
| "One frontal character sheet is enough" | Camera angle changes cause identity drift. 8-10 references required. |
| "I'll generate the character sheet later" | Generating scenes before character lock means regenerating everything. |
| "Close enough is fine for a secondary character" | Every character in 2+ shots needs a bible. |
| "I'll use text description instead of @ref" | Text description drifts. @ref is the only stable identity anchor. |
