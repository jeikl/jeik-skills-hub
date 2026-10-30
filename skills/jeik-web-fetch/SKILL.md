---
name: jeik-web-fetch
description: "High-performance web extraction tool. Scrapes any URL (SPA, dynamic JS, anti-bot, intranet, or internet) and outputs clean structured Markdown with 3 categorized modes: --fast (default), --common, and --complex."
---

# Jeik Web Fetch

Industrial-grade web extraction engine. Scrapes any URL into clean structured Markdown using native Chromium/Chrome/Edge on the host (zero heavy dependencies, no Playwright/Docker required).

## 🛠️ Environment Check & Auto-Installation

Before running extraction, ensure the `jeik` CLI binary is available. If `jeik` is not installed or not in PATH, execute the one-command installer:

- **Linux (Ubuntu/Debian/CentOS/Arch, x64/ARM64) & macOS**:
  ```bash
  curl -fsSL https://raw.githubusercontent.com/jeikl/Jeik-Web-Fetch/main/scripts/install.sh | bash
  ```
- **Windows (PowerShell)**:
  ```powershell
  irm https://raw.githubusercontent.com/jeikl/Jeik-Web-Fetch/main/scripts/install.ps1 | iex
  ```

---

## 🎯 3 Categorized Fetch Modes

Run `jeik fetch "<URL>" [mode-flag]` based on the target website type:

| Mode Flag | Target Webpages & Scenarios | Underlying Mechanism | Example Command |
| :--- | :--- | :--- | :--- |
| **`--fast`**<br>*(Default)* | **Static Pages & Plain Text**<br>• GitHub repos, issues, code files<br>• Plain HTML blogs, Wikipedia<br>• Raw CSS, JS, Markdown, JSON files | **Sub-second HTTP Probe**<br>Direct fetch without launching a browser (<200ms). Automatically escalates to headless browser if an unhydrated client skeleton is detected. | `jeik fetch "https://github.com/torvalds/linux"`<br>`jeik fetch "https://raw.githubusercontent.com/..." --fast` |
| **`--common`** | **Dynamic Technical Docs & JS Pages**<br>• Modern JS documentation (DeepSeek, MiMo, Docusaurus, Mintlify)<br>• Client-side SPA (React, Vue, Next.js, Nuxt)<br>• Complex manuals with Monaco / CodeMirror editors, lazy loading, and expandable drawers | **Full Headless Browser Rendering**<br>Launches Chromium with JavaScript execution, waits for hydration, recursively expands folding sections, and extracts content along with sidebar navigation trees. | `jeik fetch "https://mimo.mi.com/docs/..." --common`<br>`jeik fetch "https://api-docs.deepseek.com/..." --common` |
| **`--complex`** | **High Anti-Bot Risk & Interactive Sites**<br>• Heavily restricted sites (Zhihu, Xiaohongshu, WeChat, Taobao)<br>• Cloudflare Turnstile/5s challenge, CAPTCHAs, login walls, or complex fingerprinting | **Deep Anti-Bot Stealth & Browser Takeover**<br>Enables advanced stealth spoofing, extended settling timeouts, and smooth micro-scrolling. Supports one-click browser debugging via `jeik open` for manual login and seamless tab takeover. | `jeik fetch "https://www.zhihu.com/..." --complex`<br>`jeik open "<URL>"` -> Login -> `jeik fetch --active-tab` |

---

## 🚀 Quick Recipes

### 1. Fast Mode (Default)
```bash
# Scrape GitHub repos or static blogs
jeik fetch "https://github.com/torvalds/linux"
```

### 2. Common Mode (Technical Docs & Dynamic Frameworks)
```bash
# Harvest complete docs with sidebar hierarchy & multi-language code snippets
jeik fetch "https://api-docs.deepseek.com/zh-cn/api/create-chat-completion" --common
```

### 3. Complex Mode & Seamless Tab Takeover
```bash
# For heavily restricted or anti-bot guarded sites
jeik fetch "https://www.zhihu.com/question/123456" --complex

# For login walls / slider CAPTCHAs:
jeik open "https://www.xiaohongshu.com"   # Opens browser window with remote debug port
jeik fetch --active-tab                  # Immediately extracts content from the active authenticated tab!
```

---

## ⚙️ Advanced Options & References

For high concurrency (`-j`), encrypted DNS (`--dns`), persistent cookies (`--cookie` / `jeik cookie set`), and suppressing sidebar navigation (`--no-sidebar`), refer to `./references/cli-options.md`.

Output begins with an absolute path header where the full Markdown has been persisted safely to `.jeik/fetches/`.
