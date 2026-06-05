---
name: stills-audit-loop
description: Use after generating any image — mandatory review loop before any image is approved or used as a continuity reference for subsequent shots
---

# Stills Audit Loop

## Overview

The first generation is almost never the final image. Approving the first generation that "looks good enough" and using it as the reference for subsequent shots compounds errors — every subsequent shot inherits the failures of the reference. The audit loop exists to catch failures before they become the foundation of the entire production.

## The Iron Law

```
NEVER APPROVE THE FIRST GENERATION — MINIMUM ONE FULL AUDIT CYCLE REQUIRED BEFORE ANY IMAGE BECOMES A REFERENCE
```

## Batch Discipline

- Generate **4 variants** per prompt iteration (not 1, not 8)
- 4 variants reveal whether a failure is consistent (prompt problem) or random (model variance)
- If all 4 fail on the same point → the prompt is wrong → fix the prompt, generate 4 more
- If failures are inconsistent → it is model variance → batch 4 more with the same prompt
- **If 3 batches (12 images) fail with the same prompt structure: scrap the prompt, rebuild from 3 core anchors**

Never accept a "close enough" image as a reference. Drift compounds — small errors in the reference become large errors in every subsequent shot.

## Audit Checklist

Run this checklist on every image before approval. All items must pass.

**Geography**
- [ ] Character A is on the correct screen side (per geography document)
- [ ] Character B is on the correct screen side (per geography document)
- [ ] All significant objects are in their locked positions
- [ ] The 180° axis has not been crossed

**Character Identity**
- [ ] Character A's face matches @character1 reference (age, features, hair)
- [ ] Character A's wardrobe matches the bible exactly
- [ ] Character A's posture matches the emotional state
- [ ] Character B's face matches @character2 reference
- [ ] Character B's wardrobe matches the bible exactly

**Lighting**
- [ ] Lighting temperature matches the style prefix and geography document
- [ ] Left surface shows the correct reflection (cold side = cold reflection)
- [ ] Right surface shows the correct reflection (warm side = warm reflection)
- [ ] Shadow depth matches the style prefix (deep shadows, not filled)

**Style**
- [ ] Film grain present and correct (not plasticky, not over-processed)
- [ ] Color palette matches the moodboard tokens
- [ ] No elements from the exclusion list are present

**Stop condition for approval:** Geography ✓ AND Character Identity ✓ AND Lighting ✓ must all pass simultaneously. Passing 2 of 3 is not approval.

## Failure Diagnosis Table

When images fail, diagnose before fixing:

| Failure | Likely Cause | Fix |
|---|---|---|
| Characters swapped left/right | 180° axis crossed or screen position not stated | Add explicit screen position to NEGATIVO; re-state Critical Blocking Rule |
| Character identity drift | @ref not dominant enough | Reduce text descriptors; let @ref carry more weight; add angle-specific reference |
| Wrong reflection temperature | Reflection contract not in LUZ field | Add reflection contract explicitly to LUZ field |
| Plasticky textures | Missing grain/haze tokens | Add "light atmospheric haze, soft film grain, photorealistic surface texture" to ESTILO |
| Object in wrong position | Geography not re-stated in ENTORNO | Re-state object positions explicitly in ENTORNO field |
| Wrong camera angle | Camera position not anchored to floor plan | Name the floor plan camera explicitly; anchor to visible landmark |
| Style inconsistency | Style prefix missing or abbreviated | Include full style prefix verbatim in ESTILO field |

## When to Scrap vs. Amend

**Amend the prompt** when: the failure is specific and isolated (one object in the wrong position, one lighting element missing).

**Scrap and rebuild** when:
- 3 batches (12 images) have failed with the same structural problem
- The prompt has accumulated many amendments that may be contradicting each other
- You cannot identify which field is causing the failure

When scrapping: start from 3 core anchors (the identity reference, the scene continuity reference, and the camera position). Add fields back one at a time until the failure recurs. That field is the problem.

## Red Flags

| Thought | Reality |
|---|---|
| "This one is close enough" | Drift compounds. "Close enough" in Shot 1 becomes "clearly wrong" by Shot 5. |
| "I'll fix the continuity issue in the next shot" | The next shot will inherit the error and compound it. |
| "The character looks approximately right" | Character identity is binary — it either matches the @ref or it doesn't. |
| "4 failures is unusual, I'll keep batching" | 4 failures with the same prompt = prompt problem. Fix the prompt. |

**REQUIRED NEXT SKILL:** ai-filmmaking:continuity-checker (after all shots in the scene are approved)
