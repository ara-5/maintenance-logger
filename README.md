# PropTrack — Maintenance Issue Logger

> A production-quality internal tool for logging, tracking, and managing property maintenance requests — built as a self-contained single-file web application with zero dependencies.

**Live Demo → [Add your GitHub Pages link here after deploying]**

---

## Overview

PropTrack is a full-featured maintenance issue tracker designed for property management teams. It lets staff report issues on-site and lets coordinators monitor, prioritize, and update requests in real time — all from a clean, fast interface that works straight from a browser with no login, no server, and no installation required.

This project demonstrates:
- Real-world UI/UX thinking beyond basic CRUD
- Frontend security best practices (XSS prevention, input validation, storage integrity)
- Polished, accessible design with dark/light mode support
- Bonus features a real product team would ship

---

## Features

### View 1 — Submit an Issue
- **Property Name** dropdown with 5 sample properties
- **Issue Category** dropdown: Plumbing, Electrical, AC/HVAC, Furniture, Cleaning, Other
- **Urgency** radio group: Low / Medium / High (color-coded green/yellow/red)
- **Description** textarea with live character counter (min 10, max 500 chars)
- **Photo Upload** — optional, with drag-and-drop, MIME type validation (JPEG/PNG/WEBP) and 5 MB size limit
- On submit: generates a unique ticket number (`MNT-0001` format) and shows it in a success banner
- Full client-side validation with inline field-level error messages

### View 2 — Issue Dashboard

| Column | Details |
|---|---|
| Ticket # | Monospaced `MNT-XXXX` identifier |
| Property | Bold property name |
| Category | Subdued category label |
| Urgency | Color-coded badge — Green (Low) / Yellow (Medium) / Red (High) |
| Date Submitted | Human-readable date |
| Status | Inline dropdown: Open / In Progress / Resolved — persists on refresh |
| Actions | View detail modal + delete with confirmation |

- Filter by Property, Category, Urgency, Status, or free-text search
- Active filters shown as removable chip pills
- Sortable columns (click any header)
- Stats bar: Open / In Progress / Resolved ticket counts

### Bonus Features

| Feature | Details |
|---|---|
| 🌙 Dark / Light Mode | Toggle in topbar, saved to `localStorage` |
| ⬇ CSV Export | Downloads all tickets as a dated `.csv` |
| 🔍 Full-text Search | Searches ticket #, property, category, description |
| 🗑 Delete & Clear All | Per-row delete + bulk clear, both with confirm dialogs |
| 👁 Detail Modal | Full issue view with all metadata in a popup |
| 🔔 Toast Notifications | Corner toasts on status changes, export, and deletes |
| 📋 Sample Data | 5 realistic pre-loaded tickets on first open |
| ♿ Accessibility | ARIA roles, `aria-label`, `aria-live`, keyboard navigation |

---

## Security Highlights

| Concern | Implementation |
|---|---|
| **XSS Prevention** | All user data inserted via `textContent` or a `sanitize()` helper — never raw `innerHTML` |
| **Storage Integrity** | `isValidIssue()` validates every object loaded from `localStorage` — rejects malformed or injected entries |
| **File Upload Safety** | MIME type whitelist + 5 MB max enforced client-side before any processing |
| **Input Validation** | Required fields, min/max description length, focus-on-first-error UX |
| **Ticket Collision Safety** | `nextTicket()` uses `Number.isFinite` guard to prevent `MNT-NaN` from corrupted data |
| **No Inline Handlers** | Zero `onclick`/`onchange` in HTML — all events attached via `addEventListener` |
| **No Data Leakage** | Fully client-side; no data leaves the browser |

---

## Tech Stack

| Layer | Choice |
|---|---|
| Language | Vanilla HTML5, CSS3, JavaScript (ES6+) |
| Fonts | Google Fonts — Outfit + DM Mono |
| Storage | `localStorage` |
| Dependencies | **None** |
| Build Step | **None** |

Deliberate choice to use no frameworks — demonstrates mastery of fundamentals and makes the project instantly portable.

---

## Getting Started

### Run Locally

```bash
git clone https://github.com/YOUR_USERNAME/proptrack-maintenance-logger.git
cd proptrack-maintenance-logger
open index.html
```

No `npm install`. No build step. No config. Just open the file.

---

## Deployment Guide

### Option 1 — GitHub Pages (Recommended, Free)

1. Push this repo to GitHub
2. Go to **Settings → Pages**
3. Under **Source**, select **Deploy from a branch**
4. Choose `main` branch, `/ (root)` folder → click **Save**
5. Your app is live at:
   ```
   https://YOUR_USERNAME.github.io/proptrack-maintenance-logger/
   ```

> GitHub Pages is the best option here — free, instant, HTTPS by default, and gives you a clean shareable link for your resume or portfolio.

---

### Option 2 — Netlify Drop (30 seconds, no account needed)

1. Go to **[app.netlify.com/drop](https://app.netlify.com/drop)**
2. Drag the project folder onto the page
3. Done — you get a live `https://random-name.netlify.app` URL instantly
4. Optional: sign in to rename the URL or connect it to your GitHub repo for auto-deploys

---

### Option 3 — Vercel (CLI)

```bash
npm install -g vercel
cd proptrack-maintenance-logger
vercel --yes
```

Vercel will give you a live URL in under 30 seconds.

---

## Project Structure

```
proptrack-maintenance-logger/
├── index.html      ← Entire application (HTML + CSS + JS, ~1500 lines)
└── README.md       ← This file
```

Inside `index.html`, the code is organized into clearly commented sections:

```
<style>     — CSS variables, layout, all component styles, responsive rules
<body>      — Semantic HTML: topbar, submit view, dashboard view, modals, dialogs
<script>    — Constants → Storage helpers → Theme → Tab navigation →
              Form logic → Table render → Filters → Sort → Modal →
              Confirm/Delete → CSV Export → Notifications → Init
```

---

## What I'd Add Next (Production Roadmap)

- **Backend + Database** — Node/Express + PostgreSQL or Firebase to sync across devices
- **Email notifications** — Alert on High urgency ticket submission
- **Role-based access** — Tenant / Maintenance Staff / Manager views
- **Photo preview** — `FileReader` API thumbnail before upload
- **Audit log** — Track who changed status and when
- **PWA support** — Offline-capable service worker

---

## Author

Built by **[Your Name]**

[LinkedIn](https://linkedin.com/in/yourprofile) · [Portfolio](https://yourportfolio.com) · [GitHub](https://github.com/YOUR_USERNAME)
