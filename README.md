# AI Filmmaking

A Claude Code plugin with 14 skills covering the full AI filmmaking pipeline — from dramatic brief to finished cinematic video with sound.

## The Problem

AI filmmaking defaults to "prompt and pray": random outputs, character identity drift across shots, spatial incoherence between camera angles, no systematic pipeline. A film with 8 shots has 6 continuity variables per shot. Without enforced discipline at each stage, every session resets from zero.

This plugin solves the three core failure modes:
- **Spatial incoherence** — shots filmed from different angles break the 180° axis and reverse character screen positions
- **Character identity drift** — the same character looks like 5 different people across 5 shots
- **"Prompt and pray"** — natural language prompts produce natural language problems

## Installation

```bash
# In Claude Code
/plugins install /path/to/ai-filmmaking

# Or add directly to your project's .claude/plugins directory
```

## The Pipeline

```
Brief → Art Direction → Moodboard → Style Prefix → Geography → Characters
                                                                    ↓
                                              Shot List + Asset Pipeline (parallel)
                                                                    ↓
                                               Cinematographic Prompting → Stills Audit Loop
                                                                    ↓
                                                         Continuity Checker
                                                                    ↓
                                                           Image to Video
                                                                    ↓
                                                          Audio Crafting
                                                                    ↓
                                                      Assembly + Compositing
```

## Skills

### Pre-Production
| Skill | What it protects against |
|---|---|
| `using-ai-filmmaking` | Starting production without pipeline discipline |
| `brief-to-art-direction` | Building visuals without a visual brief |
| `moodboard-extraction` | Using reference images directly (pulling unwanted elements) |
| `style-prefix` | Style drift across all generated content |
| `scene-geography` | 180° axis violations, reversed screen positions |

### Stills Production
| Skill | What it protects against |
|---|---|
| `character-bible` | Identity drift across angles and environments |
| `shot-list-design` | Improvised shots that can't be edited together |
| `asset-pipeline` | Generating characters and locations in the same prompt |
| `cinematographic-prompting` | Underspecified prompts that rely on model defaults |
| `stills-audit-loop` | Approving first generations without verification |
| `continuity-checker` | Cross-shot failures discovered after video generation |

### Video Production
| Skill | What it protects against |
|---|---|
| `image-to-video` | Random video iteration without spatial and directorial discipline |

### Post-Production
| Skill | What it protects against |
|---|---|
| `audio-crafting` | Decorative or reactive audio design |
| `assembly-compositing` | Assembling after all shots are generated (wrong order) |

## Key Concepts

**The 180° Axis Rule** — A spatial line that must never be crossed during editing. Crossing it reverses character screen positions and breaks all cut continuity. Locked in `scene-geography`.

**Style Prefix** — A locked dense block (8-12 lines) prefixed to every prompt. Contains grain, lighting, color, aspect ratio, and the critical audio constraint: `environmental sound effects only, no generated music, no subtitles`. Locked in `style-prefix`.

**Reference Syntax** — `@characterN` for locked character identity, `<<<img1>>>` for scene continuity. These override text description. Introduced in `character-bible`.

**Spatial Layout Block** — A camera position anchor section included in every video prompt. Describes camera position relative to visible landmarks in the reference sheet. Prevents the model from re-staging the scene. Introduced in `image-to-video`.

**Continuous Shot Rule** — Never define time-based beats in a continuous shot prompt. Every "first 3 seconds / then 3 seconds" description is interpreted as a cut. Introduced in `image-to-video`.

**4-6 Second Clip Units** — Optimal unit for video generation (not 15 seconds). Shorter clips have higher success rates and cut more cleanly. Enforced in `shot-list-design`.

**Batch Discipline** — 4 variants per prompt iteration. 3 batches (12 images) with the same failure = prompt problem, not model variance. Applied throughout stills and video production.

## Methodology

Built from research across:
- Higgsfield "Road to Cannes Ep.2" — real production workflow using Claude skills and video generation tools
- Gossip Goblin (Zack London) — character consistency methodology, "wet clay" mindset, modular coverage
- Jean Marie Bonthous — Image Clusters vs. Shot Lists; AI manages abundance not scarcity
- obra/superpowers — skill format, Iron Laws, Red Flags tables

## License

MIT
