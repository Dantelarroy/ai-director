---
name: continuity-checker
description: Use after all stills are approved — compares all shots simultaneously against the locked geography and character bibles, writes production/continuity-report.md, then hands off to image-to-video
---

# Continuity Checker

## Overview

Every shot was generated independently. The model had no memory of the previous shot. Continuity failures are the structural default — not random accidents. Without a dedicated cross-shot verification pass, failures become embedded in video generation and cannot be fixed without reshooting. This is the mandatory gate between stills and video.

## The Iron Law

```
VERIFY CHARACTER IDENTITY AND GEOGRAPHY ACROSS ALL SHOTS BEFORE MOVING TO VIDEO — POST CANNOT FIX CONTINUITY
```

## Active Process

Announce: "Usando `continuity-checker` para verificar consistencia cross-shot antes del video."

**Step 1: Read context**

Read `production/audit-log.md` (to know which shots passed individual audit), `production/scene-geography.md`, `production/character-bible/character-*.md`.

**Step 2: Request all approved images together**

> "Compartí todas las imágenes aprobadas juntas — idealmente en un grid o en un solo mensaje. Las voy a comparar entre sí."

**Step 3: Run the 12-item cross-shot checklist**

For each item, evaluate ALL shots simultaneously:

```
SCREEN POSITIONS
☐ Character A appears on the correct screen side in EVERY shot
☐ Character B appears on the correct screen side in EVERY shot
☐ No shot has reversed character positions
☐ The 180° axis has not been crossed in any shot

OBJECT POSITIONS
☐ Every significant object is in its locked position in every shot
☐ No object has drifted, moved, or disappeared between shots

LIGHTING CONSISTENCY
☐ Lighting temperature is consistent: same wall = same temperature in all shots
☐ Left surface shows cold reflection consistently
☐ Right surface shows warm reflection consistently

CHARACTER IDENTITY
☐ @character1 face is consistent across all shots (compare simultaneously)
☐ @character2 face is consistent across all shots
☐ Character wardrobe is identical in every shot
```

**Step 4: If continuity failure found — diagnose and repair**

Tell the user:
> "Falla de continuidad en Shot [ID]: [item]. La causa probable es [diagnosis]. Pasos:
> 1. Volvé al prompt de `production/prompts/[shot-id].md`
> 2. Corregí el campo [field] específico
> 3. Ejecutá `stills-audit-loop` solo para ese shot
> 4. Volvé aquí cuando esté aprobado"

**Do not proceed to image-to-video until all continuity failures are resolved.**

**Step 5: Do not proceed if any of these are unresolved**

- Crossed 180° axis in any shot
- Character on wrong screen side in any shot
- Character identity drift visible at normal resolution
- Objects in wrong positions in shots that appear in the same scene

**Step 6: Write the continuity report**

Write to `production/continuity-report.md`:

```markdown
# Continuity Report
## [Project name]

> Output of `ai-filmmaking:continuity-checker`

## Result: [APROBADO / REQUIERE CORRECCIÓN]

## Shots verified
[List of Shot IDs]

## Issues found
[List of failures with shot ID and field, or "Ninguno"]

## Status per shot
[Table: Shot ID | Status | Notes]
```

**Step 7: Transition**

When all items pass:
> "Continuidad verificada. Todos los shots pasan el check cross-shot. Informe guardado en `production/continuity-report.md`. Invocando `image-to-video`..."

Invoke `ai-filmmaking:image-to-video`.

## Output

**File:** `production/continuity-report.md`
**Read by:** `image-to-video`

## Failure Recovery Protocol

When a continuity failure is found:
1. Identify the exact shot containing the error
2. Diagnose which prompt field caused it
3. Fix the prompt in `production/prompts/[shot-id].md`
4. Re-run `stills-audit-loop` for that shot only
5. Re-run full continuity-checker after fix

## Red Flags

| Thought | Reality |
|---|---|
| "It's close enough — I'll fix it in the edit" | Post cannot fix reversed screen positions, wrong character faces, or wrong object positions. |
| "The lighting difference is subtle" | Subtle differences become obvious when shots are cut together. Fix now. |
| "I'll check continuity while generating video" | Video generation is the wrong time to discover continuity failures. |
| "The audience won't notice" | The audience notices everything that breaks the geography — even if they can't name it. |
