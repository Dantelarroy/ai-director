---
name: continuity-checker
description: Use after completing all stills for a scene, before beginning video generation — verifies that character identity and geography are consistent across every shot
---

# Continuity Checker

## Overview

Every shot in a scene was generated independently. The model had no memory of the previous shot when it generated the next. Continuity failures are therefore not random accidents — they are the structural default. Without a dedicated verification pass, continuity failures become embedded in video generation and cannot be fixed without reshooting. This skill is the mandatory quality gate between stills and video.

## The Iron Law

```
VERIFY CHARACTER IDENTITY AND GEOGRAPHY ACROSS ALL SHOTS BEFORE MOVING TO VIDEO — POST CANNOT FIX CONTINUITY
```

## Cross-Shot Checklist

Place all approved stills side by side (in a grid or comparison view) and run this checklist:

**Screen Positions**
- [ ] Character A appears on the correct screen side in every shot
- [ ] Character B appears on the correct screen side in every shot
- [ ] No shot has reversed character positions relative to the geography document
- [ ] The 180° axis has not been crossed in any shot

**Object Positions**
- [ ] Every significant object is in its locked position in every shot
- [ ] No object has drifted, moved closer to camera, or disappeared

**Lighting Consistency**
- [ ] Lighting temperature is consistent: same wall = same temperature across all shots
- [ ] Left surface shows cold reflection in every shot it appears
- [ ] Right surface shows warm reflection in every shot it appears
- [ ] Shadow direction and depth are consistent across all shots

**Material and Environmental Consistency**
- [ ] Same floor surface, same walls, same furniture in all shots
- [ ] No element of the set has been redesigned between shots
- [ ] Environmental details (age, wear, color) are consistent

**Character Identity**
- [ ] Compare `@character1` face in all shots simultaneously — identity is consistent
- [ ] Compare `@character2` face in all shots simultaneously — identity is consistent
- [ ] Character A wears identical wardrobe in all shots (every item, every detail)
- [ ] Character B wears identical wardrobe in all shots (every item, every detail)
- [ ] Character posture and emotional state are consistent within each scene beat

**Style**
- [ ] Film grain and texture are consistent across all shots
- [ ] Color palette is consistent — no shot has drifted toward a different grade
- [ ] No shot has elements from the exclusion list

## Failure Recovery Protocol

When a continuity failure is found, repair in this order:

**Step 1: Identify the failing shot**
Do not regenerate anything until you know exactly which shot contains the error and exactly what is wrong.

**Step 2: Diagnose root cause**
- Screen position reversal → 180° axis was crossed or screen position was not explicitly stated in that shot's prompt
- Object drift → ENTORNO field did not re-state object position for that shot
- Character identity drift → @ref was not dominant enough for that shot's angle
- Lighting inconsistency → LUZ field was not restated consistently for that shot
- Wardrobe inconsistency → Non-Negotiable List was not included in that shot's NEGATIVO

**Step 3: Fix the prompt**
Go to the cinematographic-prompting skill. Fix the specific field that caused the failure.

**Step 4: Re-run stills-audit-loop for that shot only**
Do not regenerate the entire scene. Fix only the failing shot.

**Step 5: Re-run the full continuity checklist**
After any fix, recheck all items. A fix in one shot may reveal a related failure in another.

## Do Not Proceed If

Any of these failures are present — they cannot be fixed in video:
- Crossed 180° axis in any shot
- Character on wrong screen side in any shot
- Character identity drift that is visible at normal resolution
- Objects in wrong positions that appear in multiple shots

## Red Flags

| Thought | Reality |
|---|---|
| "It's close enough — I'll fix it in the edit" | Post cannot fix reversed screen positions, wrong character faces, or wrong object positions. |
| "The lighting difference is subtle" | Subtle differences become obvious when shots are cut together. Fix now. |
| "I'll check continuity while generating video" | Video generation is the wrong time to discover continuity failures. |
| "The audience won't notice" | The audience notices everything that breaks the geography — even if they can't name it. |

**REQUIRED NEXT SKILL:** ai-filmmaking:image-to-video
