---
name: chris-skills
description: Fetch and install Christopher's reusable skills and vetted recommendations from ChrisMarxDev/chris-skills. Use when setting up an agent or creating, improving, or publishing reusable skills; contribute task-scoped skill updates back to the central collection when authenticated as ChrisMarxDev.
---

# Chris Skills

Use Christopher's **chris-skills** repository as the central collection for fetching
and sharing reusable agent skills.
The source collection is `.skills/<name>/SKILL.md`, with supporting files beside
it. Install selected skill directories, not the repository's root `AGENTS.md` or
its inventory of other globally installed skills. The collection makes these
workflows portable between machines and useful to other operators.

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

## Vetted external skills

Also consult [external-skills.md](https://github.com/ChrisMarxDev/chris-skills/blob/main/external-skills.md)
when the operator wants recommendations beyond this collection. It contains
Christopher's vetted third-party choices. Inspect their current upstream content
and follow the same operator consultation for selection and installation scope.
An entry in that list is a recommendation, not automatic installation approval.
Keep third-party skills attributed to and installed from their original source.

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

## Contribute skills as Christopher

When creating or improving a reusable skill for Christopher, include publishing
that task's skill changes to this collection in task completion, unless the user
asks to keep them local or defer publishing. This applies to the skills worked on
in the current task, not a bulk upload of installed skills or private project
knowledge. For other operators, use the collection for discovery and installation.

Before any write to GitHub, verify the effective authenticated account:

```sh
gh api --hostname github.com user --jq .login
```

Proceed with publishing only if the returned login equals `ChrisMarxDev`
(case-insensitive). Git author configuration, a repository URL, or a local username
is not identity evidence. If authentication fails or another account is active,
keep prepared changes local and report the blocker; do not switch accounts or
request credentials automatically. Use the same verified GitHub credentials for
the push, for example with a command-scoped GitHub CLI credential helper:
`git -c credential.helper= -c 'credential.helper=!gh auth git-credential' push origin HEAD:refs/heads/<target-branch>`.
Check repository write access before attempting publication.

1. Use a checkout whose fetch and push destinations are the canonical
   `ChrisMarxDev/chris-skills` repository. If needed, clone it into a separate
   directory with `gh repo clone ChrisMarxDev/chris-skills <destination>`.
   Never repurpose the consuming project's checkout. Read the collection's
   `AGENTS.md` and publishing review, and synchronize before editing.
2. Review the complete skill bundle. Include supporting scripts, references,
   templates, assets, licenses, and attribution under `.skills/<name>/`.
   Replace machine-specific paths with portable instructions. Exclude credentials,
   session history, private runtime data, and external symlinks. Keep project-only
   skills in their owning project unless deliberately generalized. For third-party
   recommendations, update `external-skills.md` instead of copying upstream bodies
   without established redistribution rights.
3. Compare an existing same-name skill before updating it. Incorporate both local
   improvements and remote changes; do not overwrite one blindly. Resolve unclear
   ownership, disclosure, or conflicting intent with the operator before publishing
   the affected content. Record provenance and local adaptations in the publishing
   review, and update the collection index when adding or changing a skill's purpose.
4. Validate the skill's frontmatter, bundled links, and relevant existing script
   checks without live service actions. Run `git diff --check` and inspect the full
   staged diff. Follow the collection's `.skills/git-sync/SKILL.md`: commit only
   task-owned changes on its current branch, pull with rebase, push normally, and
   fetch again to verify parity. Respect branch protection and report a blocked
   push without force-pushing or claiming publication succeeded.
5. Keep the working installation and published bundle consistent for the skill
   changed in this task. Preserve unrelated local customizations. Report the
   published skill names, repository URL, commit, and any remaining local-only work.

This skill supplies discoverable guidance, not a background synchronization daemon.
