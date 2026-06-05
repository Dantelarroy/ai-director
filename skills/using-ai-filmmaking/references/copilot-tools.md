# Copilot CLI Tool Mapping — AI Filmmaking

Skills use Claude Code tool names. When you encounter these in a skill, use your platform equivalent:

| Skill references | Copilot CLI equivalent |
|---|---|
| `Skill` tool (invoke a skill) | Use the `skill` tool — skills are auto-discovered |
| `Read` (read a file) | Use native file tools |
| `Write` (create a file) | Use native file tools |
| `Edit` (modify a file) | Use native file tools |
| `Bash` (run shell commands) | Use native shell tools |

No multi-agent support required. All ai-filmmaking skills run sequentially.

## Key behavior note

When a skill says "write `production/[filename].md`", create that file in the current working directory's `production/` folder.

When a skill says "invoke `ai-filmmaking:[skill-name]`", use the `skill` tool with the skill name.
