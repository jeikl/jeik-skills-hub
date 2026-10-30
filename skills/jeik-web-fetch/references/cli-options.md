# Jeik CLI Advanced Options Reference

This document provides detailed explanations and examples for advanced `jeik` commands and flags.

---

## 1. Concurrency & Performance (`-j` / `--threads`)
Batch scrape multiple URLs in parallel using concurrent worker threads:

```bash
# Scrape 3 pages with 4 parallel threads in common mode
jeik fetch "https://example.com/page1" "https://example.com/page2" "https://example.com/page3" -j 4 --common
```

---

## 2. Custom & Encrypted DNS (`--dns`)
Supports standard numeric IP resolvers and DNS-over-HTTPS (DoH) encrypted queries:

```bash
# Custom DoH resolver
jeik fetch "<URL>" --dns "https://1.1.1.1/dns-query"

# Preset alias (google / cloudflare)
jeik fetch "<URL>" --dns google
jeik fetch "<URL>" --dns cloudflare
```

---

## 3. Persistent Cookie Management (`--cookie` / `jeik cookie`)
Maintain authenticated sessions across scrapes:

```bash
# Direct inline cookie string
jeik fetch "<URL>" --cookie "session_id=abc; token=123" --complex

# Read from a Netscape/JSON cookie file
jeik fetch "<URL>" --cookie-file "/path/to/cookies.txt" --complex

# Domain-scoped persistent storage
jeik cookie set zhihu.com "z_c0=2|1:0|10:..."   # Persists across all future zhihu fetches
jeik cookie list                              # View stored domain cookies
jeik cookie clear                             # Clear stored cookies
```

---

## 4. Sidebar Suppression (`--no-sidebar`)
By default, `--common` extracts full-text markdown along with an appendix catalog tree of all sidebar navigation links. To strip the catalog and keep only body content:

```bash
jeik fetch "<URL>" --common --no-sidebar
```

---

## 5. Local Daemon / API Server (`jeik serve`)
Launch a high-performance FastAPI daemon on the host:

```bash
jeik serve --port 8000
```
API endpoints:
- `POST /scrape`: `{"url": "...", "mode": "fast|common|complex"}`
- `POST /scrape/batch`: `{"urls": ["..."], "mode": "..."}`
- `GET /health`

---

## 6. Self-Upgrade & Maintenance
```bash
jeik upgrade      # Checks GitHub Releases and updates the binary in-place
jeik --version    # Check current installed version
```
