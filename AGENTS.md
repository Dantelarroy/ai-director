# AI Director — AI Filmmaking Plugin

End-to-end AI filmmaking skills: from dramatic brief to finished cinematic video with sound.

## How to Use

To start any new AI film project, invoke:

```
ai-filmmaking:using-ai-filmmaking
```

This skill bootstraps the session, detects existing project state, and guides you through the full pipeline without needing to invoke any other skill manually.

## The 14 Skills

| Skill | Stage | What it does |
|---|---|---|
| `using-ai-filmmaking` | Meta | Session bootstrap — detects state, guides to next step |
| `brief-to-art-direction` | Pre-production | Translates narrative into visual DNA |
| `moodboard-extraction` | Pre-production | Extracts visual rules from reference images |
| `style-prefix` | Pre-production | Generates the locked style block for all prompts |
| `scene-geography` | Pre-production | Locks the 180° axis, screen positions, cameras |
| `character-bible` | Pre-production | Builds locked character identity references |
| `shot-list-design` | Pre-production | Designs the shot list before any generation |
| `asset-pipeline` | Pre-production | Generates location and prop assets separately |
| `cinematographic-prompting` | Stills | Writes complete 7-field prompts per shot |
| `stills-audit-loop` | Stills | Audits every generated image before approval |
| `continuity-checker` | Stills | Verifies cross-shot consistency before video |
| `image-to-video` | Video | Converts approved stills to video with discipline |
| `audio-crafting` | Post | Designs the 3-layer audio world |
| `assembly-compositing` | Post | Assembles and edits the final film |

## Platform — Codex

Skills load natively in Codex. Tool mapping:

| Skill references | Codex equivalent |
|---|---|
| `Skill` tool | Skills load natively — follow the instructions directly |
| `Read`, `Write`, `Edit` | Use native file tools |
| `Bash` | Use native shell tools |

No multi-agent support required — all skills run sequentially.

See `skills/using-ai-filmmaking/references/codex-tools.md` for full mapping.

## Output Structure

Each skill writes to a `production/` directory in your working folder.

```
production/
  art-direction.md
  visual-tokens.md
  style-prefix.md        [LOCKED]
  scene-geography.md     [LOCKED]
  character-bible/
  shot-list.md
  assets/
  prompts/
  audit-log.md
  continuity-report.md
  audio-design.md
```
