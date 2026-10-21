# Skill collection

| Skill | Purpose |
|---|---|
| [bottleneck](bottleneck/SKILL.md) | Interview to identify the most important constraint on progress. |
| [cli-first](cli-first/SKILL.md) | Prefer purpose-built command-line tools. |
| [core-principles](core-principles/SKILL.md) | Check decisions against project principles. |
| [git-sync](git-sync/SKILL.md) | Commit on the current branch, rebase, push, and verify remote parity. |
| [skill-finder](skill-finder/SKILL.md) | Find skills on skills.sh and install after operator consultation. |
| [chris-skills](chris-skills/SKILL.md) | Fetch selected skills and publish task-scoped improvements as ChrisMarxDev. |
| [jev](jev/SKILL.md) | Run typed judgments and batch workflows through Executor managed connections. |
| [taskfile](taskfile/SKILL.md) | Create and debug Taskfile automation. |

The initial four skills were imported unchanged from Christopher's local `~/.codex/skills/` installation on
2026-10-08, including each skill's `agents/openai.yaml` metadata.

`git-sync` was adapted from the local `github-rebase-sync` skill for automatic
checkpoint and task-completion synchronization on the current branch.

Selection is tracked in [SKILLS_REVIEW.md](../SKILLS_REVIEW.md). Further skills
remain under review. Runtime discovery and installation are not configured yet.

`skill-finder` and `chris-skills` are newly authored workflows. The canonical
source is [ChrisMarxDev/chris-skills](https://github.com/ChrisMarxDev/chris-skills).
