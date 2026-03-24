# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

A static HTML employee handbook documenting the internal **QA Bonus Grading App** (Streamlit + BigQuery + Google Sheets + Drive + Chat). This repo contains only the handbook site — not the app itself. The handbook is designed for embedding in Google Sites.

## Page Structure

```
index.html                    ← Main hub (dark navy+gold theme, company logo)
│
├── Chapter 1: QA Agent Guide (regular QA agents)
│   ├── 1-1_access.html       ← Access & Initial Setup
│   ├── 1-2_grading.html      ← Grading Workflow
│   ├── 1-3_outputs.html      ← Grading Outputs
│   └── 1-4_handoff.html      ← Drive & Handoff
│
├── Chapter 2: Admin Guide (QA agents with admin access)
│   ├── 2-1_admin_access.html      ← Admin Access & Environment (PROD/SANDBOX)
│   ├── 2-2_config_whitelist.html  ← Penalties, Whitelist & SP Tier
│   ├── 2-3_send_functions.html    ← Send Functions (HR Sync + Chat Dispatch)
│   └── 2-4_regrade_cleanup.html   ← Re-grade, Ledger & Cleanup
│
├── Chapter 3: Extra Information
│   ├── 3-1_architecture.html      ← System Architecture & Backend
│   └── 3-2_history_reference.html ← Audit History & Reference
│
├── V1pag1.html                ← Legacy draft (not linked)
├── Qa Agent Guide Pag1 .html ← Legacy draft (not linked)
└── styles.css                 ← Empty/unused
```

## Key Design Patterns

- **No build system or dependencies** — plain HTML/CSS, opened directly in a browser or embedded via iframe.
- **No shared stylesheet** — each page carries its own complete `<style>` block. When changing shared design tokens (colors, fonts, spacing), every page must be updated individually.
- **Design tokens** — Hub page uses CSS custom properties: `--navy: #0F1E35`, `--gold: #D4AF37`, `--navy-mid: #1A365D`, etc. Content pages use: `--primary-brand-color: #1A365D`, `--accent-color: #D4AF37`.
- **Images hosted on Google Drive** — Screenshots use `drive.google.com/thumbnail?id=...&sz=w1000` URLs. New pages use `REPLACE_WITH_IMAGE_ID` as placeholder for the Drive file ID.
- **Logo placeholder** — `index.html` has `REPLACE_WITH_LOGO_ID` placeholder in the logo `<img>` src.
- **Navigation** — Each subpage has prev/next nav buttons linking to siblings within the same chapter.

## When Adding New Pages

1. Copy an existing content page (e.g., `2-2_config_whitelist.html`) as the template — it has the full inline style block and nav button structure.
2. Use the naming convention `{chapter}-{page}_{slug}.html` (e.g., `2-5_new_feature.html`).
3. Update `index.html` to add/update the corresponding card in the chapter grid.
4. Update the chapter progress bar `width` percentage and label in `index.html`.
5. Wire up prev/next nav links in both the new page and its neighbors.

## Source Context

The handbook documents the Streamlit app at `C:\Users\MARKETING\Desktop\GRADING TOOL STREAMLITE 2026\`. The README.md and `System_Integration_Flow_v5.4.1.drawio` in that project are the primary sources for handbook content.
