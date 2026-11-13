# External skills

Skills maintained outside this collection, including Christopher’s vetted
recommendations and potential additions. Each entry states its status; the
skill content stays in its source repository.

## Grilling — Matt Pocock

[Source](https://github.com/mattpocock/skills/tree/main/skills/productivity/grilling)
· Skill name: `grilling`

Stress-test a plan, decision, or idea through structured rounds of questions.
It works through dependent decisions until the operator and agent reach a shared
understanding before taking action.

**Christopher’s verdict:** “I love it.” Vetted on 2026-10-09.

Install for Codex:

```sh
npx skills add mattpocock/skills --skill grilling --agent codex
```

Add `--global` for a user-wide installation. Agents should consult the operator
before installing, following the `skill-finder` workflow.

## Semantic Lint — Christopher Marx

[Source](https://github.com/ChrisMarxDev/semantic-lint)

**Status:** Potential external skill to add, suggested by Christopher on 2026-10-10.
The actual skill will live in the `semantic-lint` repository. Consult that
repository for the skill entrypoint and installation instructions when available,
and confirm installation with the operator.

## Knowledge Graph — Christopher Marx

[Source](https://github.com/ChrisMarxDev/knowledge-graph)

**Status:** General setup is in place and updated frequently, as noted by
Christopher on 2026-10-12.

The skill lives in its source repository. Read the latest repository documentation
for the current setup and installation instructions rather than relying on a
copied snapshot. Confirm installation with the operator.

## CMRX Video Toolkit — Christopher Marx

[Source](https://github.com/ChrisMarxDev/cmrx-video-toolkit)

Open tools and agent skills for programmable video: editing, components, shaders,
and local production pipelines.

**Status:** Added by Christopher on 2026-10-23; being developed further.

The skills stay in the source repository. Read its latest documentation for the
available skills, current setup, and installation instructions. Confirm the
selected skills and installation scope with the operator.

## Stageshow — Benji Taylor

[Introduction and examples](https://benji.org/stageshow) ·
[Upstream skill](https://github.com/benjitaylor/skills/tree/main/stageshow)
· Skill name: `stageshow`

**Status:** Requested by Christopher as a reusable resource on 2026-11-13.
Reviewed upstream SKILL.md version 1.1.1, including framing and craft guidance.

Builds believable product UI illustrations and short demos for marketing pages.
Useful for deliberate framing, focused stories, readable product shots and a
separate compact composition for mobile instead of shrinking desktop UI.
Apply the product’s own design system and keep real screenshots identified as
such; an authored mock demo is not evidence of a live product interaction.

Install from the original source after choosing agent and installation scope:

```sh
npx skills add benjitaylor/skills --skill stageshow --agent codex
```

The upstream kit uses React and CSS; review its dependencies and license before
copying a bundle. This entry saves the reference only and does not install or
redistribute the skill.
