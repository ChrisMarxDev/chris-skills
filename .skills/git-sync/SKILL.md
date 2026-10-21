---
name: git-sync
description: Inactive placeholder for installing an opt-in Git Sync workflow into a specific repository. Do not use this global entry to commit, rebase, or push.
---

# Git Sync — inactive placeholder

This is empty. Do not use it to perform Git operations or establish a default
workflow. If tasked to install Git Sync into a repository, read the
[real skill template](references/repository-skill.md).

Only for an explicitly requested repository installation, copy that template to
`<repository>/.agents/skills/git-sync/SKILL.md` and copy
[its metadata](references/repository-openai.yaml) to
`<repository>/.agents/skills/git-sync/agents/openai.yaml`.
The template's persistent AGENTS.md rule applies only to that target repository
when requested. Never replace this global placeholder with the active template.
