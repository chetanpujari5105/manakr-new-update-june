# 🧠 CLAUDE.md — Manakar Clinic Website
> Claude Code reads this file FIRST on every session. Keep it up to date.

---

## 📌 Project Identity
- **Project:** Manakar Psychology Clinic Website
- **Client:** Dr. Sayli Manakar
- **Live URL:** https://manakar.in
- **Vercel Deployment:** https://manakar-psych.vercel.app
- **Built by:** Chetan Pujari (https://chetan-website-delta.vercel.app/)
- **Repo type:** Static single-file website hosted on Vercel

---

## 📁 Project File Structure

```
manakar-website/
├── CLAUDE.md               ← YOU ARE HERE — read this first always
├── index.html              ← THE ENTIRE WEBSITE (single file, ~1200+ lines)
├── Code.gs                 ← Google Apps Script backend (form + calendar + email)
├── docs/
│   ├── PROJECT_OVERVIEW.md ← What the site does, sections, features
│   ├── ARCHITECTURE.md     ← Tech stack, Tailwind config, custom colors
│   ├── BUGS_HISTORY.md     ← All bugs found and fixed (v1 to current)
│   ├── DEPLOYMENT.md       ← How to deploy to Vercel + update GAS
│   └── GOOGLE_APPS_SCRIPT.md ← Backend logic, sheet structure, config keys
└── scripts/
    └── validate.sh         ← Quick local validation script
```

---

## ⚡ Quick Reference — Most Common Tasks

### Change the Google Apps Script URL (contact form backend)
- File: `index.html`
- Search for: `const SCRIPT_URL =`
- It is on approximately **line 1117** inside `<!-- Google Sheets Form Submission -->` script block
- Replace the URL string value only — keep quotes and semicolon intact

### Update footer credit
- File: `index.html`
- Search for: `Built with` in the `<footer>` section
- Inside `<div class="border-t border-sage/30 pt-8 text-center">`

### Change clinic phone / WhatsApp number
- File: `index.html`
- Search for: `917620xxxxxx` (WhatsApp href uses country code format `91xxxxxxxxxx`)
- Also update the display text separately

### Change clinic email
- File: `index.html` — search for `mailto:`
- File: `Code.gs` — update `DOCTOR_EMAIL` in the `CONFIG` object

### Update appointment booking slots / hours
- File: `Code.gs` — update `APPOINTMENT_SLOTS` array in `CONFIG`
- File: `index.html` — update the visible slot grid in the booking section

---

## 🚫 ABSOLUTE RULES — Read Before Every Edit

1. **NEVER change any UI design, layout, colors, fonts, or spacing** unless explicitly asked
2. **NEVER restructure or reorganize code** unless a bug fix requires it
3. **NEVER remove any working features or animations**
4. **ALWAYS return the complete file** after any edit (not just a snippet)
5. **ALWAYS add comment `/* fix: description */`** next to every change made
6. **index.html is a single-file app** — all CSS and JS are inline, no external files
7. **Do NOT add `<link>` or `<script src="">` tags** — everything stays inline

---

## 🏗️ Architecture at a Glance

| Layer | Technology |
|-------|-----------|
| Frontend | Single HTML file with inline Tailwind CSS + custom styles |
| Styling | Tailwind CDN + custom Tailwind config (custom colors) |
| Icons | Lucide Icons (CDN) |
| Animations | AOS (Animate on Scroll, CDN) |
| Fonts | Google Fonts — Lora + Inter |
| Backend | Google Apps Script (deployed as Web App) |
| Database | Google Sheets (appointments + error log) |
| Calendar | Google Calendar API (via Apps Script) |
| Email | Gmail via Apps Script (MailApp) |
| Hosting | Vercel (auto-deploy from GitHub) |
| Domain | manakar.in (GoDaddy DNS → Vercel) |

---

## 🎨 Custom Tailwind Colors (defined in `tailwind.config`)

| Name | Use |
|------|-----|
| `soft-teal` | Primary brand color — links, buttons, accents |
| `teal-hover` | Hover state for teal elements |
| `charcoal` | Main text color |
| `sage` | Soft green — borders, subtle accents |
| `warm-cream` | Background color |
| `soft-rose` | Accent / highlight |

> Always use these names. Don't use raw hex or generic Tailwind colors for brand elements.

---

## 🔌 Backend: Google Apps Script

- **Web App URL location:** `index.html` line ~1117, `const SCRIPT_URL = '...'`
- **Script file:** `Code.gs`
- **Deployment rule:** Every code change requires a **New Deployment** in GAS — redeploying generates a new URL that must be updated in `index.html`
- **Access setting:** Execute as: Me | Who has access: Anyone
- See `docs/GOOGLE_APPS_SCRIPT.md` for full details

---

## ✅ Current Version Status
- Latest stable version: **v17** (index.html)
- Footer credit: "Built with ❤️ by Chetan Pujari" linking to portfolio
- Form backend: Google Apps Script (JSONP-based submission)
- Google Ads: Verified via Search Console, ads approved
- Known issues: None at last update (April 2026)

---

## 📋 When You Get a Bug Report

1. Check `docs/BUGS_HISTORY.md` first — it may already be documented
2. Open browser DevTools Console for JS errors
3. For form issues → check GAS deployment URL is correct and deployed as "Anyone"
4. For layout issues → check Tailwind class names (custom color names are case-sensitive)
5. For booking/calendar issues → check `Code.gs` CONFIG object

---

## 🚀 Deployment Checklist (before going live)

- [ ] Remove any `localStorage.removeItem('mnk_lastsubmit')` debug lines
- [ ] Verify `SCRIPT_URL` in index.html matches latest GAS deployment URL
- [ ] Test contact form end-to-end (check Google Sheet for new row)
- [ ] Test WhatsApp button (phone number format: `91xxxxxxxxxx`)
- [ ] Check mobile responsiveness at 375px width
- [ ] Verify all CDN links load (Tailwind, Lucide, AOS, Google Fonts)
