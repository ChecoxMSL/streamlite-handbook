# QA Bonus Grading App — Employee Handbook (HTML)

Static HTML employee handbook for the **QA Bonus Grading App** (Streamlit v5.4.5).
Designed to be embedded in **Google Sites** — each HTML file maps to a page in the site.

### Project Status: 🔄 Content updated — assets pending

| Item | Status |
|---|---|
| HTML pages | 14/14 created |
| Google Drive assets — existing | 20/20 integrated |
| Google Drive assets — new (v5.4.5) | 0/1 pending (see below) |
| Google Sites URLs | 14/14 published |
| Navigation (Prev/Next) | ✅ All hrefs point to Google Sites URLs |
| `target="_parent"` (iframe) | ✅ Applied in all 3 chapters |
| Hub links (cards, breadcrumbs, back) | ✅ Complete |

#### Changes v5.4.5 (2026-04-28)
- `2-4_regrade_cleanup.html` — new section **3. Report Error 🐛**: when to use it, step-by-step flow, what the admin receives
- `3-1_architecture.html` — `Error_Reports/` added to Drive tree; new section **4.1 Agent Name Aliases** in BigQuery
- `README.md` — version bump to v5.4.5, pending assets updated, full English translation

> **Google Sites base URL:** `https://sites.google.com/marketingleads.com.mx/streamlite-handbook/`
> **Full URL index:** see `index.txt`

---

## Google Sites — Embed Configuration

### Site Details

| Field | Value |
|---|---|
| Site name | Streamlite Handbook |
| Owner account | `sergio@marketingleads.com.mx` |
| Public base URL | `https://sites.google.com/marketingleads.com.mx/streamlite-handbook/` |
| Edit URL | `https://sites.google.com/d/1M2Dm8d-r8fmu-veWjgFeYdQ1xJ0oCe1y/edit` |
| Drive Site ID | `1M2Dm8d-r8fmu-veWjgFeYdQ1xJ0oCe1y` |

### How It Works

Each Google Sites page embeds **one HTML file** from the GitHub repo using **GitHub Pages** as the iframe source. Content is served directly from GitHub Pages — no external hosting required.

```
GitHub repo (ChecoxMSL/streamlite-handbook)  →  GitHub Pages
    └── file.html                                  ↓
                     https://checoxmsl.github.io/streamlite-handbook/file.html
                                                   ↓
                     Google Sites → Insert → Embed → paste URL
```

> ⚠️ **Do NOT use `raw.githubusercontent.com`** — it serves HTML as `text/plain` and Google Sites will not render it. Always use the GitHub Pages URL (`checoxmsl.github.io/…`).

### Why Next/Previous Buttons Use `target="_parent"`

Navigation buttons **do not link to the neighboring HTML file** — they link to the **Google Sites URL** of the next page. They also use `target="_parent"` so that clicking the button navigates the full Sites page instead of loading the next page inside the iframe.

Without `target="_parent"`, clicking Next would open the next page **inside the iframe** (a Sites page nested inside another), breaking navigation entirely.

```html
<!-- ✅ How all nav buttons are configured -->
<a href="https://sites.google.com/marketingleads.com.mx/streamlite-handbook/2-admin-guide/2-3-send-functions"
   target="_parent" class="nav-btn nav-btn-next">
    Next →
</a>
```

### GitHub Pages URLs — Format

The repo has **GitHub Pages** enabled. Always use these URLs when adding embeds in Google Sites.

```
https://checoxmsl.github.io/streamlite-handbook/{file}.html
```

Examples:
```
https://checoxmsl.github.io/streamlite-handbook/index.html
https://checoxmsl.github.io/streamlite-handbook/2-4_regrade_cleanup.html
https://checoxmsl.github.io/streamlite-handbook/3-1_architecture.html
```

### How to Update a Page (Normal Flow)

1. Edit the `.html` file locally
2. `git push` to the `main` branch
3. GitHub Pages updates in ~1 minute
4. Google Sites **updates automatically** — no changes needed in Sites

### How to Re-add a Deleted Embed

1. Go to Google Sites → edit the corresponding page
2. **Insert → Embed**
3. Paste the GitHub Pages URL for that file (format above)
4. Save and publish

### Full Embed Table

| Google Sites Page | HTML File | GitHub Pages URL |
|---|---|---|
| Home | `index.html` | `…/index.html` |
| Chapter 1 — QA Agent Guide | `main_chapter1.html` | `…/main_chapter1.html` |
| 1-1 Access & Setup | `1-1_access.html` | `…/1-1_access.html` |
| 1-2 Grading Workflow | `1-2_grading.html` | `…/1-2_grading.html` |
| 1-3 Grading Outputs | `1-3_outputs.html` | `…/1-3_outputs.html` |
| 1-4 Drive & Handoff | `1-4_handoff.html` | `…/1-4_handoff.html` |
| Chapter 2 — Admin Guide | `main_chapter2.html` | `…/main_chapter2.html` |
| 2-1 Admin Access | `2-1_admin_access.html` | `…/2-1_admin_access.html` |
| 2-2 Config & Whitelist | `2-2_config_whitelist.html` | `…/2-2_config_whitelist.html` |
| 2-3 Send Functions | `2-3_send_functions.html` | `…/2-3_send_functions.html` |
| 2-4 Re-grade & Cleanup | `2-4_regrade_cleanup.html` | `…/2-4_regrade_cleanup.html` |
| Chapter 3 — Extra Info | `main_chapter3.html` | `…/main_chapter3.html` |
| 3-1 Architecture | `3-1_architecture.html` | `…/3-1_architecture.html` |
| 3-2 History & Reference | `3-2_history_reference.html` | `…/3-2_history_reference.html` |

> `…` = `https://checoxmsl.github.io/streamlite-handbook`

---

## Site Structure

```
Google Sites Page          HTML File                  Description
─────────────────────────  ─────────────────────────  ────────────────────────────────────────
Home                       index.html                 Landing page — 3 chapter cards
│
├── QA Agent Guide         main_chapter1.html         Chapter 1 landing — scope + 4 subpage cards
│   ├── Access & Setup     1-1_access.html            Login, authentication, semaphore legend
│   ├── Grading Workflow   1-2_grading.html           Step-by-step grading, penalty reference
│   ├── Grading Outputs    1-3_outputs.html           Report Card / Certificate / Banner logic
│   └── Drive & Handoff    1-4_handoff.html           Drive folder routing, handoff checklist
│
├── Admin Guide            main_chapter2.html         Chapter 2 landing — admin scope + workflow strip
│   ├── Admin Access       2-1_admin_access.html      PIN unlock, PROD/SANDBOX environment toggle
│   ├── Config & Whitelist 2-2_config_whitelist.html  Penalty rules, Whitelist, SP Comercial Tier
│   ├── Send Functions     2-3_send_functions.html    HR Sync (🟣→🔵), Chat Dispatch (🔵→🟢)
│   └── Re-grade & Cleanup 2-4_regrade_cleanup.html   Re-grade, ledger edit/remove, week reset
│
└── Extra Information      main_chapter3.html         Chapter 3 landing — service highlights
    ├── Architecture       3-1_architecture.html      System diagram, Sheets backend, Drive structure
    └── History & Ref      3-2_history_reference.html Week slots, auto-archival, semaphore legend
```

### Legacy Files (not linked)

| File | Note |
|---|---|
| `V1pag1.html` | Early draft of page 1. Not referenced anywhere. |
| `Qa Agent Guide Pag1 .html` | Early draft of page 1. Not referenced anywhere. |
| `styles.css` | Empty file — all CSS is inline per page. |

---

## Tech Stack

- **Pure HTML + CSS** — no build tools, no JavaScript frameworks, no dependencies.
- **Google Fonts** — DM Serif Display + DM Sans (hub/main pages), Segoe UI (content pages).
- **Images** — hosted on Google Drive via `drive.google.com/thumbnail?id=<FILE_ID>&sz=w1000`.
- **No shared stylesheet** — each file contains its own complete `<style>` block.

---

## Design Tokens

| Token | Hub / Main pages | Content pages |
|---|---|---|
| Navy (primary) | `--navy: #0F1E35` | `--primary-brand-color: #1A365D` |
| Gold (accent) | `--gold: #D4AF37` | `--accent-color: #D4AF37` |
| Background | Dark navy | White `#FFFFFF` |
| Body text | `--white: #F7F9FC` | `--text-main: #333333` |

---

## Assets Checklist

> All assets are complete. Drive IDs registered below.
> Image src format: `https://drive.google.com/thumbnail?id=FILE_ID_HERE&sz=w1000`
>
> ⚠️ **Note on orientation:** Several Chapter 2 screenshots were captured in **portrait (vertical)** format. The corresponding HTML files already account for this — no rotation or rescaling needed before uploading to Drive.

### Logo

- [x] **Company Logo** — `index.html` line 291
  - Placeholder: `REPLACE_WITH_LOGO_ID`
  - Source: `assets/logo.png` from the Streamlit project — upload to Drive and copy the file ID

### Chapter 1 — QA Agent Guide ✅ complete

- [x] Login Screen — `1-1_access.html` line 120 — `id=1kLIGmLMf0fvyi76eUGcm6dqmt7y_qpSc`
- [x] Sidebar Progress Tracker — `1-1_access.html` line 194 — `id=19ugQsB3SduBObsTbMr9VSQN2LUsMwVYA`
- [x] Sidebar Progress Tracker — `1-2_grading.html` line 133 — `id=19ugQsB3SduBObsTbMr9VSQN2LUsMwVYA`
- [x] Agent Selection — `1-2_grading.html` line 143 — `id=1jfQd_jJZh8_nNSJm1QCGFJNrihp1oUCu`
- [x] Call Logs Dashboard — `1-2_grading.html` line 154 — `id=1PfTEHi6TDdqcLiI4VB2NutIlrI1zF1ht`
- [x] Report Card PDF — `1-3_outputs.html` line 191 — `id=1ZMMMLM5RCqlPImymxkz62_exPIMhNJ4v`
- [x] Full Bonus Certificate PDF — `1-3_outputs.html` line 195 — `id=1bUFEYFNhPCO7GV2bCekqLWVEhe9IpPKi`
- [x] Suspension Banner PNG — `1-3_outputs.html` line 199 — `id=1ToYvraf6a5AGqxFZfZ-8yPehBz4xaQJ7`

### Chapter 2 — Admin Guide ✅ complete

> ⚠️ Items marked `[vertical]` were captured in portrait orientation.
> Make sure the `<img>` container in the HTML has `width: 100%` and no fixed `height` so they scale correctly.

- [x] **Admin PIN Entry** — `2-1_admin_access.html` line 99 `[vertical]`
  - Screenshot of the PIN field inside the ⚙️ Admin Settings expander
- [x] **Environment Toggle** — `2-1_admin_access.html` line 162 `[vertical]`
  - Screenshot of the PROD/SANDBOX toggle with the environment badge visible
- [x] **Edit Penalty Rules Panel** — `2-2_config_whitelist.html` line 97
  - Screenshot of the deduction sliders and threshold inputs per category
- [x] **Full Bonus Whitelist Panel** — `2-2_config_whitelist.html` line 135
  - Screenshot of the agent multiselect with the Save Whitelist button
- [x] **SP Comercial Tier Panel** — `2-2_config_whitelist.html` line 161
  - Screenshot of the SP Tier multiselect with the lead threshold visible
- [x] **HR Sync Button** — `2-3_send_functions.html` line 130
  - Screenshot of the Send Functions panel showing the 📊 Send QA Bonus to HR button
- [x] **Chat Dispatch Section** — `2-3_send_functions.html` line 170 `[vertical]`
  - Screenshot of the 📤 Send PDF Preview panel with agent list and Send button
- [x] **Re-grade Agent Panel** — `2-4_regrade_cleanup.html` line 101
  - Screenshot of the Re-grade panel with search, dropdown, and Reset to pending button
- [x] **Ledger & Cleanup Section** — `2-4_regrade_cleanup.html` line 126
  - Screenshot of the Ledger panel showing agent search, checkboxes, and action buttons

### Chapter 3 — Extra Information ✅ complete

- [x] **System Integration Flow Diagram** — `3-1_architecture.html` line 157
  - Exported from `System_Integration_Flow_v5.4.1.drawio` as PNG
- [x] **Audit History Panel** — `3-2_history_reference.html` line 166
  - Screenshot of the 📚 History tab with an archived week slot table visible

### New Assets — v5.4.5 ⏳ pending

- [ ] **Report Error Expander** — `2-4_regrade_cleanup.html` section 3
  - Screenshot of the 🐛 expander open showing: captured error, notes text area, file uploader, and 📨 Send button
  - Placeholder to add: `REPLACE_WITH_REPORT_ERROR_SCREENSHOT_ID`

### Assets Summary

| Status | Count | Detail |
|---|---|---|
| Complete | 20 | All assets have a Drive ID |
| Pending (v5.4.5) | 1 | Report Error expander screenshot |
| Portrait orientation | 3 | `2-1` PIN Entry, `2-1` Env Toggle, `2-3` Chat Dispatch |
| **Total** | **21** | **🔄 1 asset pending** |

---

## Navigation URLs — ✅ Complete

> All Google Sites URLs have been applied to the Previous/Next buttons and navigation links (breadcrumbs, cards, back links).
> All subpages use `target="_parent"` for iframe compatibility in Google Sites.

### Hub & Main Pages

| File | Links updated |
|---|---|
| `index.html` | 3 chapter card hrefs → Google Sites URLs |
| `main_chapter1.html` | 4 card hrefs + Home breadcrumb + back link |
| `main_chapter2.html` | 4 card hrefs + Home breadcrumb + back link |
| `main_chapter3.html` | 2 card hrefs + Home breadcrumb + back link |

### Chapter 1 — Subpage Nav Buttons (`target="_parent"`)

- [x] `1-1_access.html` — Next → `1-2-the-grading-process`
- [x] `1-2_grading.html` — Prev → `1-1-access-progress` · Next → `1-3-understanding-outputs`
- [x] `1-3_outputs.html` — Prev → `1-2-the-grading-process` · Next → `1-4-file-management`
- [x] `1-4_handoff.html` — Prev → `1-3-understanding-outputs`

### Chapter 2 — Subpage Nav Buttons (`target="_parent"`)

- [x] `2-1_admin_access.html` — Next → `2-2-config-whitelist`
- [x] `2-2_config_whitelist.html` — Prev → `2-1-admin-access` · Next → `2-3-send-functions`
- [x] `2-3_send_functions.html` — Prev → `2-2-config-whitelist` · Next → `2-4-re-grade-function`
- [x] `2-4_regrade_cleanup.html` — Prev → `2-3-send-functions`

### Chapter 3 — Subpage Nav Buttons (`target="_parent"`)

- [x] `3-1_architecture.html` — Next → `3-2-history-reference`
- [x] `3-2_history_reference.html` — Prev → `3-1-architecture`

---

## How to Add a New Page

1. Copy an existing content page (e.g., `2-2_config_whitelist.html`) as a template.
2. Name it `{chapter}-{page}_{slug}.html` (e.g., `3-3_faq.html`).
3. Update the page indicator badge (`Page X of Y`) and chapter label.
4. Wire the Previous/Next nav buttons to the neighboring Google Sites URLs.
5. Add a card for the new page in the corresponding `main_chapter*.html`.
6. Update the progress bar count in `main_chapter*.html`.

---

## Source Material

This handbook documents the Streamlit app located at:

```
C:\Users\MARKETING\Desktop\GRADING TOOL STREAMLITE 2026\
```

Key reference files:
- `README.md` — Full project documentation (architecture, sheets backend, output types, etc.)
- `System_Integration_Flow_v5.4.1.drawio` — Architecture diagram (3 pages)
