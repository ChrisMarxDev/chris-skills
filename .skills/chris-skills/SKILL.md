---
name: chris-skills
description: Discover and install selected skills from Christopher's chris-skills repository when setting up an agent, restoring his workflow, or looking for his reusable skills. Resolve the collection source, review available skills, and install the operator's chosen subset.
---

# Chris Skills

Use Christopher's **chris-skills** repository as a source of installable skills.
The source collection is `.skills/<name>/SKILL.md`, with supporting files beside
it. Install selected skill directories, not the repository's root `AGENTS.md` or
its inventory of other globally installed skills.

## Resolve the source

Canonical source: [ChrisMarxDev/chris-skills](https://github.com/ChrisMarxDev/chris-skills).
Skills live under `.skills/` on `main`. Use this source unless the operator
explicitly supplies a different checkout or revision. Do not use the consuming
project's remote as the source when this skill has been installed elsewhere.

List the remote collection without installing it:

```sh
npx skills add https://github.com/ChrisMarxDev/chris-skills/tree/main/.skills --list
```

## Choose the skills

Read the resolved source's `.skills/README.md` and inspect its actual skill
entrypoints. Use that live inventory; `SKILLS_REVIEW.md` includes unselected global
skills and is not an install list. From a local checkout, the CLI can list the
collection without installing it:

```sh
npx skills add /path/to/chris-skills/.skills --list
```

Explain which available skills fit the operator's workflow. Confirm the chosen
names, target agent, project/global scope, and any existing installations that
would be replaced. Wait for approval unless those specifics are already authorized.
Explain that selecting an installation scope is part of this skill's workflow.
Do not install every skill by default or recursively invoke this installer merely
because it appears in the collection.

## Install and verify

Use the [Skills CLI](https://github.com/vercel-labs/skills) with explicit selection.
For a verified local source checkout, use:

```sh
npx skills add /path/to/chris-skills/.skills --skill <selected-name> --agent <agent-name>
```

For a remote source, resolve its actual branch/ref and list skills first. If the
repository root does not expose the collection, use a direct URL to its `.skills`
subdirectory or obtain a separate source checkout and use the local command above.
Do not switch or repurpose the consuming project's checkout to obtain the source.
Add `--global` only for agreed global installation, and `--yes` only after approval.

Preserve complete bundles, licenses, and local customizations. If replacing a
same-name customized skill, review the differences with the operator first.
Verify the selected files reached the target agent's installation directory and
report source URL/path, source revision when available, names, and scope. Explain
any runtime reload requirement without assuming installation implies activation.

If `git-sync` is selected to establish an always-on workflow, also apply its
persistent `AGENTS.md` rule in the intended project when that policy setup is
part of the operator's request. Installing files alone does not enforce the policy.
