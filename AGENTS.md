# AGENTS.md

Welcome to **jeik-skills-hub**! This repository serves as the official open skills registry for JeikCode and other AI coding agents.

## Repository Conventions

1. **Pure Skill Packaging**:
   - Each skill lives inside `skills/<skill-name>/`.
   - Never commit heavy runtime binaries, node_modules, or compiled dependencies to this repository.
   - For heavy tools, point to independent source repositories and provide self-healing install commands in `SKILL.md`.

2. **Skill Anatomy**:
   - `skills/<skill-name>/SKILL.md` is strictly required and must contain valid YAML frontmatter (`name`, `description`).
   - Keep `SKILL.md` lightweight. Defer deep parameter tables and edge cases to `references/`.
   - Include a `metadata.json` complying with the Open Agent Skills specification.

3. **Commit & Co-Authorship**:
   - Adhere to Conventional Commits (e.g. `feat(...)`, `docs(...)`, `fix(...)`, `refactor(...)`).
   - Leave exactly one blank line between commit body and the trailer.
   - Strictly append the official JeikCode trailer to every commit:
     ```text
     Co-Authored-By: JeikCode <code@jeikcode.top>
     ```
