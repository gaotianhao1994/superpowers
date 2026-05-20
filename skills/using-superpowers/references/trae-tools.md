# Trae Solo CN Tool Mapping

Skills use Claude Code tool names. When you encounter these in a skill, use your platform equivalent:

| Skill references | Trae Solo CN equivalent |
|-----------------|-------------------------|
| `Read` (file reading) | Use your native file reading tool |
| `Write` (file creation) | Use your native file writing tool |
| `Edit` (file editing) | Use your native file editing tool |
| `Bash` (run commands) | Use your native shell tool |
| `Grep` (search file content) | Use your native search tool |
| `Glob` (search files by name) | Use your native file search tool |
| `Skill` tool (invoke a skill) | Use your native skill invocation tool |
| `TodoWrite` (task tracking) | Use your native task tracking tool |
| `Task` tool (dispatch subagent) | Use your native subagent tool |
| `WebFetch` | Use your native web fetch tool |
| `WebSearch` | Use your native web search tool |

**Note:** If Trae Solo CN does not have a direct equivalent for a tool, use the closest available tool or adapt the workflow accordingly.

## Environment Detection

Skills that create worktrees or finish branches should detect their environment with read-only git commands before proceeding:

```bash
GIT_DIR=$(cd "$(git rev-parse --git-dir)" 2>/dev/null && pwd -P)
GIT_COMMON=$(cd "$(git rev-parse --git-common-dir)" 2>/dev/null && pwd -P)
BRANCH=$(git branch --show-current)
```

- `GIT_DIR != GIT_COMMON` → already in a linked worktree (skip creation)
- `BRANCH` empty → detached HEAD (cannot branch/push/PR from sandbox)

See `using-git-worktrees` Step 0 and `finishing-a-development-branch` Step 1 for how each skill uses these signals.

## Customization

You can modify this file to match the exact tool names available in your Trae Solo CN environment.
