<img src="assets/icon.svg" width="64" height="64" alt="">

# chris-skills

Christopher's agent skills, portable between machines and cloud environments.
The collection is public so others can use the workflows too.

Skills live in [`.skills/`](.skills/). See [the publishing review](SKILLS_REVIEW.md)
for the global inventory, suggested first batch, and portability work.
[External skills](external-skills.md) lists skills by others that Christopher has
vetted and recommends. [AGENTS.md](AGENTS.md) provides Codex project instructions.

The first four skills are imported: `bottleneck`, `cli-first`, `core-principles`,
and `taskfile`. A reworked `git-sync` adds current-branch commit, rebase,
and push as the default task-completion workflow. `skill-finder` discovers skills
on skills.sh with operator consultation; `chris-skills` installs selected skills
from this collection. Further skills are under discussion. The public source is
[ChrisMarxDev/chris-skills](https://github.com/ChrisMarxDev/chris-skills).
The `.skills/` directory is our source layout;
installation into the chosen cloud agent runtime will be handled separately.

Created in [T3 Code](https://t3.codes).
