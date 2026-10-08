---
name: cli-first
description: Prefer purpose-built command-line tools over Computer Use and GUI automation. Use whenever a task can be completed through shell commands, project CLIs, system utilities, or an application's official CLI, especially for opening files or folders, inspecting state, managing files, running builds and tests, Git operations, and developer workflows.
---

# CLI First

Choose the narrowest reliable CLI solution before invoking Computer Use.

## Tool selection

1. Check for an existing project command, official application CLI, or standard system utility.
2. Use the CLI when it can complete the task deterministically and expose useful output or exit status.
3. Use Computer Use only when the task depends on visual judgment, GUI-only state, an authenticated interaction unavailable through CLI or a dedicated connector, or when the CLI path has failed and no reliable command-line alternative remains.

Do not open Computer Use merely to launch Finder, reveal a file, open a URL, start an application, inspect logs, or perform another action available through commands such as `open`, `git`, `rg`, `find`, `ls`, or the project's own task runner.

## Execution

- Prefer non-interactive commands.
- Scope commands to explicit paths and targets.
- Preserve existing user data and changes.
- Follow sandbox, approval, and destructive-action requirements.
- Report the command-level outcome, including failures that affect completion.

If GUI interaction is necessary, briefly state why the CLI is insufficient before using Computer Use.
