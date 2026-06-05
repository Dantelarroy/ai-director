---
name: stills-audit-loop
description: Use after generating any image — runs the 14-item audit checklist, diagnoses failures, logs results to production/audit-log.md, and loops until all shots are approved
---

# Stills Audit Loop

## Overview

The first generation is almost never the final image. Approving the first generation that "looks good enough" and using it as the continuity reference for subsequent shots compounds errors — every subsequent shot inherits the failures of the reference. The audit loop exists to catch failures before they become the foundation of the entire production.

## The Iron Law

```
NEVER APPROVE THE FIRST GENERATION — MINIMUM ONE FULL AUDIT CYCLE REQUIRED BEFORE ANY IMAGE BECOMES A REFERENCE
```

## Active Process

Announce: "Usando `stills-audit-loop` para auditar las imágenes generadas."

**Step 1: Read locked documents**

Read `production/scene-geography.md`, `production/character-bible/character-*.md`, `production/style-prefix.md`.

**Step 2: Ask which shot to audit**

> "¿Qué Shot ID estás auditando? Compartí la imagen generada."

**Step 3: Run the 14-item checklist out loud**

For each item, state the result explicitly (✅ pasa / ❌ falla):

```
GEOGRAPHY
☐ Character A is on the correct screen side (per scene-geography.md)
☐ Character B is on the correct screen side (per scene-geography.md)
☐ All significant objects are in their locked positions
☐ The 180° axis has not been crossed

CHARACTER IDENTITY
☐ Character A's face matches @character1 (age, features, hair)
☐ Character A's wardrobe matches the bible exactly
☐ Character A's posture matches the emotional state
☐ Character B's face matches @character2
☐ Character B's wardrobe matches the bible exactly

LIGHTING
☐ Lighting temperature matches the style prefix and geography
☐ Left surface shows the correct reflection temperature
☐ Right surface shows the correct reflection temperature

STYLE
☐ Film grain present and correct — not plasticky
☐ No elements from the exclusion list are present
```

**Stop condition:** Geography ✅ AND Character Identity ✅ AND Lighting ✅ must all pass simultaneously.

**Step 4: If any item fails — diagnose**

| Failure | Likely Cause | Fix |
|---|---|---|
| Characters swapped left/right | 180° axis crossed or screen position not stated | Add explicit screen position to NEGATIVO; re-state Critical Blocking Rule |
| Character identity drift | @ref not dominant enough | Reduce text descriptors; add angle-specific reference |
| Wrong reflection temperature | Reflection contract not in LUZ field | Add reflection contract explicitly |
| Plasticky textures | Missing grain/haze tokens | Add "light atmospheric haze, soft film grain, photorealistic surface texture" |
| Object in wrong position | ENTORNO didn't re-state object position | Re-state object positions explicitly |
| Style inconsistency | Style prefix missing or abbreviated | Include full style prefix verbatim |

Tell the user:
> "Falla en: [item]. Causa probable: [diagnosis]. Fix recomendado: [fix]. Regenerá con el prompt corregido y compartí la nueva imagen."

**Step 5: Log the result**

Append to `production/audit-log.md`:

```markdown
## Shot [ID] — [APROBADO / EN REVISIÓN]
- Date: [timestamp]
- Attempts: [N]
- Failures found: [list or "ninguna"]
- Status: APROBADO / REQUIERE REGENERACIÓN
```

**Step 6: Batch discipline reminder**

After each failed attempt:
- Generate **4 variants** per prompt iteration
- If all 4 fail on the same point → fix the prompt, generate 4 more
- If 3 batches (12 images) fail with the same structure → scrap the prompt, rebuild from 3 core anchors
- Never accept "close enough" — drift compounds

**Step 7: Next shot or transition**

When a shot is approved:
> "Shot [ID] aprobado y registrado en `production/audit-log.md`. ¿Auditamos el siguiente shot o ya están todos aprobados?"

When all shots are approved:
> "Todos los shots aprobados. Invocando `continuity-checker` para verificar la consistencia entre planos..."

Invoke `ai-filmmaking:continuity-checker`.

## Output

**File:** `production/audit-log.md` (appended per shot)
**Read by:** `continuity-checker`

## Red Flags

| Thought | Reality |
|---|---|
| "This one is close enough" | Drift compounds. "Close enough" in Shot 1 becomes "clearly wrong" by Shot 5. |
| "I'll fix the continuity issue in the next shot" | The next shot inherits the error and compounds it. |
| "The character looks approximately right" | Character identity is binary — it matches the @ref or it doesn't. |
| "4 failures is unusual, I'll keep batching" | 4 failures with the same prompt = prompt problem. Fix the prompt. |
