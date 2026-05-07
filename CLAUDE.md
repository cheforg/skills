Skills live directly under `skills/<skill-name>/`. There are no category sub-folders — every skill is a sibling.

Each skill directory contains a `SKILL.md` and any supporting files (rules, references, scripts) it needs.

Active skills must:
- Have a reference (with link to `SKILL.md`) in the top-level `README.md`.
- Have an entry in `.claude-plugin/plugin.json`.

Skills that are deprecated, in-progress, or personal-only must NOT appear in `.claude-plugin/plugin.json`. They may still appear in the `README.md` under a clearly-labelled section so readers know they exist but should not rely on them.
