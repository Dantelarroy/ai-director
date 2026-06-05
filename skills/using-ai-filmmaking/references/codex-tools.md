# Codex Tool Mapping — AI Filmmaking

Skills use Claude Code tool names. When you encounter these in a skill, use your platform equivalent:

| Skill references | Codex equivalent |
|---|---|
| `Skill` tool (invoke a skill) | Skills load natively — follow instructions directly |
| `Read` (read a file) | Use native file read tool |
| `Write` (create a file) | Use native file write tool |
| `Edit` (modify a file) | Use native file edit tool |
| `Bash` (run shell commands) | Use native shell tool |

No multi-agent support required. All ai-filmmaking skills run sequentially — one skill invokes the next in the same session.

## Key behavior note

When a skill says "write `production/[filename].md`", create that file in the current working directory's `production/` folder. This is where all pipeline artifacts are stored.

When a skill says "invoke `ai-filmmaking:[skill-name]`", follow the instructions of that skill directly in the same session.
