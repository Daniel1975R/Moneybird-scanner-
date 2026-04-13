# Moneybird-scanner-
This tool adds descriptions for tickets in moneybird
# 📋 Moneybird Scanner

> A lightweight, mobile-first tool that helps volunteer organizations and small businesses scan receipts and automatically route them to Moneybird with the right descriptions — no app installation required.

---

## The Problem

Volunteer organizations often struggle with expense administration. Volunteers buy groceries, materials, or supplies out of pocket — and tracking who paid what, for which project, becomes a manual and error-prone process.

Common pain points:
- Receipts get lost or submitted without context
- Bookkeepers receive scans without knowing who paid or which project it belongs to
- No clear audit trail for reimbursements

---

## The Solution

Moneybird Scanner is a single HTML file that runs directly in Safari on iPhone — no app store, no installation. It guides the user through a simple 3-step flow:

1. **Photograph the receipt** using the iPhone camera
2. **Select** who submitted the receipt and who paid for it upfront
3. **Send** — the tool generates a framed image with all metadata and opens the native share sheet, ready to email directly to the Moneybird inbox

Moneybird's AI then reads the receipt image and automatically extracts the amount, VAT, and date. The description in the subject line tells the bookkeeper exactly who submitted it and which project it belongs to.

---

## Features

- First-time setup screen — configure your organisation name, Moneybird inbox email, and admin password
- Password-protected admin panel to manage:
  - Submitters (e.g. staff members)
  - Payees (e.g. volunteers who paid upfront)
  - Projects
  - Organisation settings
- Receipt is framed with metadata (payee, project) before sending
- Confirmation step — user must confirm the email was actually sent
- Works fully offline after first load
- Saves to iPhone home screen as a PWA-style shortcut

---

## How to Deploy

### Option 1 — Netlify Drop (recommended, free)
1. Download `index.html`
2. Go to [netlify.com/drop](https://netlify.com/drop)
3. Drag and drop the file
4. Share the generated URL with your team

### Option 2 — Any static hosting
Upload `index.html` to any static hosting provider (GitHub Pages, Vercel, etc.)

> **Note:** The tool must be served over HTTPS for the Web Share API (camera + file sharing) to work on iPhone.

---

## First-Time Setup

When a user opens the tool for the first time, a setup screen appears:

- **Organisation name** — shown in the app header and on receipt images
- **Bookkeeping email** — the Moneybird inbox address (format: `name@inkomend.moneybird.nl`)
- **Admin password** — used to access the admin panel (⚙️ button, top right)

All data is stored locally in the browser (`localStorage`) — nothing is sent to any server.

---

## Email Subject Format

Each receipt generates an email with the following subject line:

```
Bon | Indiener: [CODE] - [NAME] | Voorgeschoten: [CODE] - [NAME] | Project: [PROJECT]
```

This allows Moneybird and your bookkeeper to instantly identify the receipt without opening the attachment.

---

## Tech Stack

- Pure HTML, CSS, JavaScript — zero dependencies
- Canvas API for receipt framing
- Web Share API for native iOS sharing
- localStorage for persistent configuration

---

## License

MIT — free to use, modify, and distribute.
