# Gemini CLI Tool Mapping — AI Filmmaking

Skills use Claude Code tool names. When you encounter these in a skill, use your platform equivalent:

| Skill references | Gemini CLI equivalent |
|---|---|
| `Skill` tool (invoke a skill) | Use `activate_skill` — Gemini loads skill metadata at session start |
| `Read` (read a file) | Use native file read tool |
| `Write` (create a file) | Use native file write tool |
| `Edit` (modify a file) | Use native file edit tool |
| `Bash` (run shell commands) | Use native shell tools |

No multi-agent support required. All ai-filmmaking skills run sequentially.

## Key behavior note

When a skill says "write `production/[filename].md`", create that file in the current working directory's `production/` folder.

When a skill says "invoke `ai-filmmaking:[skill-name]`", use `activate_skill` with the skill name.
