# QA Bonus Grading App — Employee Handbook (HTML)

Static HTML employee handbook for the **QA Bonus Grading App** (Streamlit v5.4.5).
Designed to be embedded in **Google Sites** — each HTML file maps to a page in the site.

### Estado del Proyecto: 🔄 Contenido actualizado — assets pendientes

| Item | Estado |
|---|---|
| Paginas HTML | 14/14 creadas |
| Google Drive assets — existentes | 20/20 integrados |
| Google Drive assets — nuevos (v5.4.5) | 0/1 pendientes (ver abajo) |
| Google Sites URLs | 14/14 publicadas |
| Navegacion (Prev/Next) | ✅ Todos los hrefs apuntan a Google Sites |
| `target="_parent"` (iframe) | ✅ Aplicado en los 3 capitulos |
| Hub links (cards, breadcrumbs, back) | ✅ Completo |

#### Cambios v5.4.5 (2026-04-28)
- `2-4_regrade_cleanup.html` — nueva sección **3. Report Error 🐛**: cuando usar el botón, flujo paso a paso, qué recibe el administrador
- `3-1_architecture.html` — `Error_Reports/` agregado al árbol de Drive; nueva sección **4.1 Agent Name Aliases** en BigQuery
- `README.md` — version bump a v5.4.5, assets pendientes actualizados

> **Google Sites URL base:** `https://sites.google.com/marketingleads.com.mx/streamlite-handbook/`
> **Indice completo de URLs:** ver `index.txt`

---

## Google Sites — Configuración del Embed

### Cómo está montado

Cada página de Google Sites embebe **un archivo HTML** del repo de GitHub usando la URL raw como `src` de un iframe. El contenido se sirve directamente desde GitHub — no hay hosting externo.

```
GitHub repo (ChecoxMSL/streamlite-handbook)
    └── archivo.html
            ↓  raw URL
Google Sites → Insert → Embed
    └── <iframe src="https://raw.githubusercontent.com/ChecoxMSL/streamlite-handbook/main/archivo.html">
```

### Por qué los botones Next/Previous usan `target="_parent"`

Los botones de navegación **no apuntan al archivo HTML vecino** — apuntan a la **URL de Google Sites** de la página siguiente. Además tienen `target="_parent"` para que el clic salga del iframe y navegue la página completa de Sites.

Sin `target="_parent"`, el clic abriría la siguiente página **dentro del iframe** (una página de Sites dentro de otra), rompiendo la navegación.

```html
<!-- ✅ Así están configurados todos los botones -->
<a href="https://sites.google.com/marketingleads.com.mx/streamlite-handbook/2-admin-guide/2-3-send-functions"
   target="_parent" class="nav-btn nav-btn-next">
    Next →
</a>
```

### GitHub Pages URLs — formato

El repo tiene **GitHub Pages** habilitado. Usar siempre estas URLs (no `raw.githubusercontent.com` — ese sirve el HTML como texto plano y Google Sites no lo renderiza).

```
https://checoxmsl.github.io/streamlite-handbook/{archivo}.html
```

Ejemplos:
```
https://checoxmsl.github.io/streamlite-handbook/index.html
https://checoxmsl.github.io/streamlite-handbook/2-4_regrade_cleanup.html
https://checoxmsl.github.io/streamlite-handbook/3-1_architecture.html
```

### Cómo actualizar una página (flujo normal)

1. Editar el archivo `.html` localmente
2. `git push` al branch `main`
3. GitHub Pages se actualiza en ~1 minuto
4. Google Sites **actualiza automáticamente** — no hay que tocar Sites

### Cómo re-agregar un embed borrado

1. Ir a Google Sites → editar la página correspondiente
2. **Insert → Embed**
3. Pegar la GitHub Pages URL del archivo (formato arriba)
4. Guardar y publicar

### Tabla completa de embeds

| Google Sites Page | Archivo HTML | GitHub Pages URL |
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

### Legacy files (not linked)

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

> Todos los assets están completos. Drive IDs registrados abajo.
> Formato del src: `https://drive.google.com/thumbnail?id=TU_ID_AQUI&sz=w1000`
>
> ⚠️ **Nota sobre orientación:** Varios screenshots del Chapter 2 fueron capturados en **formato vertical** (portrait). Los archivos HTML correspondientes ya contemplan esto — no es necesario rotar ni reescalar antes de subir a Drive.

### Logo

- [x] **Company Logo** — `index.html` linea 291
  - Placeholder: `REPLACE_WITH_LOGO_ID`
  - Tomar de: `assets/logo.png` del proyecto Streamlit, subir a Drive, copiar el ID

### Chapter 1 — QA Agent Guide ✅ completas

- [x] Login Screen — `1-1_access.html` linea 120 — `id=1kLIGmLMf0fvyi76eUGcm6dqmt7y_qpSc`
- [x] Sidebar Progress Tracker — `1-1_access.html` linea 194 — `id=19ugQsB3SduBObsTbMr9VSQN2LUsMwVYA`
- [x] Sidebar Progress Tracker — `1-2_grading.html` linea 133 — `id=19ugQsB3SduBObsTbMr9VSQN2LUsMwVYA`
- [x] Agent Selection — `1-2_grading.html` linea 143 — `id=1jfQd_jJZh8_nNSJm1QCGFJNrihp1oUCu`
- [x] Call Logs Dashboard — `1-2_grading.html` linea 154 — `id=1PfTEHi6TDdqcLiI4VB2NutIlrI1zF1ht`
- [x] Report Card PDF — `1-3_outputs.html` linea 191 — `id=1ZMMMLM5RCqlPImymxkz62_exPIMhNJ4v`
- [x] Full Bonus Certificate PDF — `1-3_outputs.html` linea 195 — `id=1bUFEYFNhPCO7GV2bCekqLWVEhe9IpPKi`
- [x] Suspension Banner PNG — `1-3_outputs.html` linea 199 — `id=1ToYvraf6a5AGqxFZfZ-8yPehBz4xaQJ7`

### Chapter 2 — Admin Guide ✅ completas

> ⚠️ Los siguientes items marcados con `[vertical]` fueron capturados en orientación portrait.
> Verificar que el contenedor `<img>` en el HTML tenga `width: 100%` y sin `height` fijo para que escalen correctamente.

- [x] **Admin PIN Entry** — `2-1_admin_access.html` linea 99 `[vertical]`
  - Screenshot del campo de PIN en el expander ⚙️ Admin Settings
- [x] **Environment Toggle** — `2-1_admin_access.html` linea 162 `[vertical]`
  - Screenshot del toggle PROD/SANDBOX con el badge de ambiente visible
- [x] **Edit Penalty Rules Panel** — `2-2_config_whitelist.html` linea 97
  - Screenshot de los sliders de deduccion y threshold por categoria
- [x] **Full Bonus Whitelist Panel** — `2-2_config_whitelist.html` linea 135
  - Screenshot del multiselect de agentes con boton Save Whitelist
- [x] **SP Comercial Tier Panel** — `2-2_config_whitelist.html` linea 161
  - Screenshot del multiselect SP Tier con el lead threshold visible
- [x] **HR Sync Button** — `2-3_send_functions.html` linea 130
  - Screenshot del panel Send Functions mostrando el boton 📊 Send QA Bonus to HR
- [x] **Chat Dispatch Section** — `2-3_send_functions.html` linea 170 `[vertical]`
  - Screenshot del panel 📤 Send PDF Preview con la lista de agentes y boton Send
- [x] **Re-grade Agent Panel** — `2-4_regrade_cleanup.html` linea 101
  - Screenshot del panel Re-grade con el search, dropdown y boton Reset to pending
- [x] **Ledger & Cleanup Section** — `2-4_regrade_cleanup.html` linea 126
  - Screenshot del panel Ledger mostrando agent search, checkboxes y botones

### Chapter 3 — Extra Information ✅ completas

- [x] **System Integration Flow Diagram** — `3-1_architecture.html` linea 157
  - Exportado de `System_Integration_Flow_v5.4.1.drawio` como PNG
- [x] **Audit History Panel** — `3-2_history_reference.html` linea 166
  - Screenshot del tab 📚 History con la tabla de un week slot archivado

### Nuevos assets — v5.4.5 ⏳ pendientes

- [ ] **Report Error Expander** — `2-4_regrade_cleanup.html` sección 3
  - Screenshot del expander 🐛 abierto mostrando: error capturado, text area de notas, file uploader, y botón 📨 Send
  - Placeholder a agregar: `REPLACE_WITH_REPORT_ERROR_SCREENSHOT_ID`

### Resumen de assets

| Estado | Cantidad | Detalle |
|---|---|---|
| Completas | 20 | Todos los assets tienen Drive ID |
| Pendientes (v5.4.5) | 1 | Report Error expander screenshot |
| Orientación vertical | 3 | `2-1` PIN Entry, `2-1` Env Toggle, `2-3` Chat Dispatch |
| **Total** | **21** | **🔄 1 asset pendiente** |

---

## Navigation URLs — ✅ Completo

> Todas las URLs de Google Sites han sido aplicadas en los botones Previous/Next y en los links de navegacion (breadcrumbs, cards, back links).
> Todos los subpages tienen `target="_parent"` para compatibilidad con iframe en Google Sites.

### Hub & Main Pages

| Archivo | Links actualizados |
|---|---|
| `index.html` | 3 chapter card hrefs → Google Sites URLs |
| `main_chapter1.html` | 4 card hrefs + breadcrumb Home + back link |
| `main_chapter2.html` | 4 card hrefs + breadcrumb Home + back link |
| `main_chapter3.html` | 2 card hrefs + breadcrumb Home + back link |

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

1. Copy an existing content page (e.g., `2-2_config_whitelist.html`) as template.
2. Name it `{chapter}-{page}_{slug}.html` (e.g., `3-3_faq.html`).
3. Update the page indicator badge (`Page X of Y`) and chapter label.
4. Wire Previous/Next nav buttons to the neighboring pages.
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
