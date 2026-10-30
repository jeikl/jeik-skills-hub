# Jeik Web Fetch (Agent Skill)

Official skill package for **Jeik-Web-Fetch** — an industrial-grade web extraction engine that converts any web page (SPAs, modern documentation, anti-bot guarded sites) into clean structured Markdown.

## 📦 What is This?

This directory contains the **pure skill package (manifest & instructions)** for AI coding agents (JeikCode, Claude Code, Cursor, Codex, etc.). 

- Source code & binary releases: [jeikl/Jeik-Web-Fetch](https://github.com/jeikl/Jeik-Web-Fetch)
- Skill specification: [Open Agent Skills format](https://skills.sh)

## ⚡ Installation

### Via Skills CLI (Universal)
```bash
# Install to global agent skills directory
npx skills add jeikl/jeik-skills-hub@jeik-web-fetch -g -y
```

### For JeikCode
Place this directory under either:
- Global: `~/.jeikcode/skills/jeik-web-fetch/`
- Workspace: `<workspace>/.jeikcode/skills/jeik-web-fetch/`

Reload inside session via `/reload` or `jeikcode_config(action="reload")`.

## 🛠️ CLI Binary Installation
This skill utilizes the lightweight host binary `jeik`. If not yet installed on your machine:

- **Linux / macOS**:
  ```bash
  curl -fsSL https://raw.githubusercontent.com/jeikl/Jeik-Web-Fetch/main/scripts/install.sh | bash
  ```
- **Windows (PowerShell)**:
  ```powershell
  irm https://raw.githubusercontent.com/jeikl/Jeik-Web-Fetch/main/scripts/install.ps1 | iex
  ```

## 📖 Skill Structure
- `SKILL.md`: Main execution decision tree and agent prompts.
- `metadata.json`: Machine-readable package metadata.
- `references/cli-options.md`: Advanced flags and parameter reference.
