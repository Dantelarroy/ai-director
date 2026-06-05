---
name: style-prefix
description: Use after moodboard-extraction — reads the art direction and visual tokens documents, generates the locked style prefix, and writes production/style-prefix.md
---

# Style Prefix

## Overview

Without a locked prefix, each generation makes independent style decisions. Shot 3 will have different grain than Shot 1. Shot 7 will have a different color grade. By Shot 10, you have 10 different films. The style prefix is the only mechanism that keeps all generations in the same visual universe. It is locked on approval and never changed mid-production.

## The Iron Law

```
ALL PROMPTS MUST INCLUDE THE LOCKED STYLE PREFIX — NO EXCEPTIONS, EVEN FOR TEST GENERATIONS
```

## Active Process

Announce: "Usando `style-prefix` para generar el prefix de estilo bloqueado."

**Step 1: Read source documents**

Read `production/art-direction.md` and `production/visual-tokens.md`. Both documents are required. If either is missing, stop and invoke the missing skill first.

**Step 2: Generate the prefix**

Using the art direction and visual tokens, generate the complete style prefix. Do not ask questions — all information is in the documents.

The prefix must contain all 6 elements:

```
1. Film stock / grain (e.g., "soft analog film grain, 24fps motion characteristics")
2. Lighting rules (dominant temperature, contrast, key light source)
3. Color grade (palette family using token names from visual-tokens.md)
4. Aspect ratio (21:9 for cinema, 16:9 for streaming — derive from art direction)
5. Audio constraint: "environmental sound effects only, no generated music, no subtitles"
6. Exclusion master list (consolidated from both documents)
```

**Format:** Dense block, 8-12 lines. Every word must earn its place. Write it as a code block ready to copy-paste.

**Step 3: Show and request approval**

Show the prefix and ask:
> "Este es el Style Prefix propuesto. Una vez aprobado queda bloqueado — no se puede modificar mid-producción sin regenerar todo lo que lo usó. ¿Aprobás?"

If the user requests changes → update and show again. Repeat until approved.

**Step 4: Write the locked document**

Write to `production/style-prefix.md` with the [LOCKED] marker:

```markdown
# Style Prefix — [LOCKED]
## [Project name]

> Output of `ai-filmmaking:style-prefix`
> NEVER MODIFY MID-PRODUCTION. Any change requires regenerating all assets that used this prefix.

## THE PREFIX — copy verbatim into every prompt

\```
STYLE PREFIX [LOCKED — DO NOT MODIFY]:
[8-12 line prefix here]
\```

## Element Breakdown

| Element | Value | Why |
|---|---|---|
[one row per element]
```

**Step 5: Transition**

> "Style Prefix guardado y bloqueado en `production/style-prefix.md`. Invocando `scene-geography`..."

Invoke `ai-filmmaking:scene-geography`.

## Output

**File:** `production/style-prefix.md` [LOCKED]
**Used by:** Every single prompt in the production — image and video

## Red Flags

| Thought | Reality |
|---|---|
| "I'll remember to add style rules to each prompt manually" | You won't. The prefix is infrastructure. It cannot be optional. |
| "The style prefix is too restrictive" | Constraints produce coherence. Looseness produces drift. |
| "I'll update it after a few test generations" | Test generations set visual expectations. Lock before first generation. |
| "The video model will add good music" | Generated music cannot be separated from dialogue in post. Always exclude it. |
| "I can derive this from memory during generation" | You cannot. Lock it now. |
