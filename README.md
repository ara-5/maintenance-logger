# PropTrack — Maintenance Issue Logger

A clean, internal single-file maintenance tracker with submit form + live dashboard.

---

## Project Structure

```
maintenance-logger/
├── index.html      ← The entire app (HTML + CSS + JS, no build required)
└── README.md       ← This file
```

## Features

### Core
- **Submit Form** — Property, Category, Urgency, Description (with char counter), optional Photo upload
- **Unique Ticket Numbers** — Format `MNT-0001`, auto-incrementing, collision-safe
- **Dashboard Table** — All submissions with sortable columns
- **Status Tracking** — Inline dropdown (Open / In Progress / Resolved), persists to localStorage
- **Urgency Color-Coding** — Green (Low) / Yellow (Medium) / Red (High)
- **Filters** — Search text, filter by Property, Category, Urgency, Status; active filter chips
- **Data Persistence** — `localStorage` survives page refresh

### Bonus
- **CSV Export** — Download all tickets as a dated `.csv` file
- **Dark / Light Mode** — Toggle in topbar, saved to localStorage
- **Sortable Columns** — Click any column header to sort asc/desc
- **Issue Detail Modal** — Full description popup without leaving the page
- **Delete Ticket** — Per-row delete with confirmation dialog
- **Clear All** — Bulk delete with confirmation
- **Active Filter Chips** — Visual pills showing active filters, click × to remove each
- **Stats Cards** — Total / Open / In Progress / Resolved counts at a glance
- **Toast Notifications** — Non-blocking corner toasts on status changes, exports, deletions
- **Sample Data** — Pre-loaded with 5 realistic tickets on first load

## Security Improvements (vs. original)

| Issue in original | Fix applied |
|---|---|
| `event` global used in `showView()` | Replaced with explicit `addEventListener` |
| Inline `onchange`/`onclick` in HTML | All handlers attached via JS (separation of concerns) |
| `innerHTML` used with user data | All user data inserted via `textContent` or `sanitize()` helper |
| No localStorage data validation | `isValidIssue()` validator — rejects malformed/injected entries |
| No file type/size validation | Validates MIME type + size before accepting upload |
| `nextTicket()` could return `MNT-NaN` | Filtered with `Number.isFinite` guard |
| No `min-length` on description | Enforced at 10 characters minimum |

## How to Run

Open `index.html` in any modern browser — no server, no dependencies, no build step.
