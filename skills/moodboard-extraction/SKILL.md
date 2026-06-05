---
name: moodboard-extraction
description: Use when you have reference images to analyze — runs per-image analysis and writes production/visual-tokens.md with the extracted visual rules
---

# Moodboard Extraction

## Overview

Reference images carry unwanted elements: specific faces, intellectual property, compositional accidents from a different director's film. You never use reference images directly in prompts — you extract the DNA. The rules, not the images. This skill runs a structured analysis of each reference and produces the Visual Token Document that `style-prefix` will read.

## The Iron Law

```
NO IMAGE GENERATION BEFORE THE VISUAL TOKEN DOCUMENT IS WRITTEN — EXTRACT RULES, NEVER USE REFERENCES DIRECTLY
```

## Active Process

Announce: "Usando `moodboard-extraction` para extraer reglas visuales de las referencias."

**Step 1: Read context**

Read `production/art-direction.md`. Use it to frame what you're looking for in the references.

**Step 2: Request images**

> "Compartí las imágenes de referencia. Mínimo 9, idealmente en estas categorías: 2 de iluminación, 2 de paleta/color, 2 de composición/encuadre, 2 de texturas/materiales, 1 de atmósfera general. Podés compartirlas en un solo mensaje o de a una."

**Step 3: Analyze each image — 6 categories**

For each image, run this analysis out loud:

```
Imagen [N]:
1. Registro estilístico — ¿Qué tipo de imagen es? ¿Qué lenguaje visual usa?
2. Luz — dirección, intensidad, temperatura, contraste
3. Paleta dominante — colores principales + acento + lo que está ausente
4. Materiales y texturas — superficies, acabados, calidad
5. Composición — encuadre, escala, jerarquía visual
6. Atmósfera — qué emoción genera, qué recursos son repetibles
```

**Step 4: Cross-reference synthesis**

After all images:

> "Analizando patrones across todas las imágenes..."

Answer three questions:
- ¿Qué comparten todas? → estas son tus reglas
- ¿Qué tensiones existen? → estas son decisiones creativas a tomar
- ¿Qué está excluido en todas? → esta es tu lista de exclusiones

**Step 5: Generate and write Visual Token Document**

Write to `production/visual-tokens.md`:

```markdown
# Visual Token Document
## [Project name]

> Output of `ai-filmmaking:moodboard-extraction`

## Style tokens
[3-5 words]

## Lighting tokens
[3-5 words: direction, temperature, contrast]

## Color tokens
[Palette names — not hex codes]

## Material tokens
[Surfaces and textures]

## Composition tokens
[Framing rules]

## Atmosphere tokens
[Emotional words]

## Exclusion rules
[What to NEVER generate — consolidated]

## Base formula
[One sentence combining the above — used as prompt seed]
```

**Step 6: Transition**

> "Visual Token Document guardado en `production/visual-tokens.md`. Invocando `style-prefix`..."

Invoke `ai-filmmaking:style-prefix`.

## Output

**File:** `production/visual-tokens.md`
**Read by:** `style-prefix`

## Red Flags

| Thought | Reality |
|---|---|
| "I'll upload the moodboard images directly to the prompt" | Direct references pull unwanted specifics — specific faces, IP, accidental compositions. Extract the rules. |
| "9 images is too many" | Fewer references = weaker cross-validation = weaker rules. 9 is the minimum. |
| "I'll do this mentally, I don't need to write it" | Unwritten rules drift. Tokens must be documented to be applied consistently across all 14 shots. |
| "I'll analyze them all at once" | Per-image analysis catches what batch review misses. One image at a time. |
