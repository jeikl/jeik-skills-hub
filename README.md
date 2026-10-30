# Jeik Skills Hub 🚀

Official collection of battle-tested, high-performance skills for **JeikCode** and modern AI coding agents (Claude Code, Cursor, Codex, OpenCode, etc.).

All skills in this hub adhere to the **Open Agent Skills Specification** and **JeikCode Progressive Disclosure Guidelines**, ensuring minimal token overhead, deterministic execution, and seamless cross-agent compatibility.

---

## ⚡ Quick Start & Installation

### 1. Via Skills CLI (Universal Agent Ecosystem)
Browse and install skills interactively or globally:

```bash
# Browse all available skills in this hub (without installing)
npx skills add jeikl/jeik-skills-hub -l

# Install a specific skill
npx skills add jeikl/jeik-skills-hub@<skill-name> -g -y

# Install all skills in this hub
npx skills add jeikl/jeik-skills-hub -g -y
```

### 2. For JeikCode Users
JeikCode automatically discovers skills in standard paths:

- **Project-Level**: Clone or symlink into `<workspace>/.jeikcode/skills/<skill-name>/`
- **Global User-Level**: Clone or copy into `~/.jeikcode/skills/<skill-name>/`

Run `/reload` in the console or call `jeikcode_config(action="reload")` to activate immediately.

---

## 🛠️ Contributing a New Skill

We welcome high-quality skills from the community!

1. Fork this repository.
2. Create a folder under `skills/<your-skill-name>/`.
3. Provide a valid `SKILL.md` with standard YAML frontmatter:
   ```markdown
   ---
   name: your-skill-name
   description: "One or two concise sentences describing the trigger condition and capability."
   ---

   # Your Skill Guide
   ...
   ```
4. Keep `SKILL.md` token-efficient (150–350 tokens); place long reference docs in a `references/` subdirectory.
5. Submit a pull request. Our CI workflow will validate frontmatter syntax and directory structure automatically.

---

## 📄 License

Apache-2.0 License. See [LICENSE](./LICENSE) for details.
