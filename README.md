# Stay Ready — Strategic Field Manual

A single-page review portal for the Stay Ready 365-day strategic plan and feedback collection.

Built as a static site so it runs free on GitHub Pages, no backend, no monthly cost. The plan, the math, the visuals, and the feedback form all live in one `index.html` file.

---

## What's in here

| File | Purpose |
|------|---------|
| `index.html` | The full site — strategy, roadmap, financials, risks, and feedback form |
| `README.md` | This file |

The site has six tabs:

1. **Mission** — the brand thesis and high-level pitch
2. **Model** — three product lines, revenue mix, subscription unit economics
3. **Roadmap** — four-phase 365-day plan with stage gates
4. **Financials** — capital deployment, P&L breakdowns, pricing scenarios
5. **Risks** — risk register with hedges
6. **Feedback** — 29 questions for Luie to answer, auto-saved as he types

---

## Deploying to GitHub Pages

### One-time setup

1. **Create the repo**
   - On GitHub: `New repository` → name it (e.g., `stay-ready-review`) → keep it private if you'd rather not have it indexable
   - Don't add a README or .gitignore yet — we already have those

2. **Upload the files**
   - Drag `index.html` and `README.md` into the repo via GitHub's web UI, or push from terminal:
     ```bash
     git init
     git add index.html README.md
     git commit -m "Initial commit"
     git branch -M main
     git remote add origin https://github.com/YOUR-USER/YOUR-REPO.git
     git push -u origin main
     ```

3. **Enable GitHub Pages**
   - In the repo: `Settings` → `Pages`
   - Under "Source," pick `Deploy from a branch`
   - Branch: `main`, Folder: `/ (root)` → `Save`
   - Wait ~1 minute. Your site is live at `https://YOUR-USER.github.io/YOUR-REPO/`

### Before you publish — edit one thing

Open `index.html` and find this line near the bottom (in the `<script>` block, around line ~1200):

```javascript
const SHANE_EMAIL = 'shane@example.com'; // ← replace with your email before deploying
```

Replace `shane@example.com` with the email you want feedback sent to. When Luie hits "Send to Shane" the form opens his mail client pre-filled with all his answers addressed to you.

Commit, push, done. The site updates within a minute.

---

## How feedback gets to you

The form gives Luie three ways to send his answers:

1. **Send to Shane** (primary) — opens his email client (Mail, Gmail, Outlook, whatever) with a pre-filled message addressed to you containing every answer formatted cleanly. He just hits send.
2. **Copy to clipboard** — copies all answers as formatted text. Useful if he prefers Slack, iMessage, etc.
3. **Download answers** — downloads a `.txt` file he can attach to anything.

Auto-save: every keystroke saves to his browser's local storage. He can fill it out across multiple sessions without losing progress. The "Last saved" timestamp shows in the bottom bar.

**Note:** This is a static site, so there's no shared database. Luie's answers stay on his device until he sends them via one of the three buttons above. That's the trade-off for free hosting and zero infrastructure.

---

## If you want shared real-time submissions later

Swap the form action to one of these (pick one when you're ready, all are free tier-friendly):

- **Formspree** — `https://formspree.io` — point the form to a Formspree endpoint, you get email + dashboard
- **Netlify Forms** — host on Netlify instead of GitHub Pages, forms come built-in
- **Google Forms** — embed a Google Form in an iframe; answers go to a Google Sheet

For now, the email/copy/download flow handles a single reviewer cleanly.

---

## Updating the content

All content lives in `index.html`. Major sections are clearly labeled with comment blocks:

```html
<!-- ============================================== -->
<!-- SECTION: MISSION -->
<!-- ============================================== -->
```

To update numbers, copy, or questions: edit the HTML, commit, push. GitHub Pages rebuilds in ~30 seconds.

To add a new feedback question:
1. Find the relevant `<div class="form-section">` block in the FEEDBACK section
2. Copy an existing `<div class="field">` block as a template
3. Update the label, name attribute, and any choice options
4. Add the new question to the `formatAnswers()` function in the script block at the bottom so it shows up in the export

---

## Brand & design notes

- **Color palette:** deep brown (`#1A120B`), warm card brown (`#2A1D12`), gold accent (`#D9A441` — matches the apparel script), cream text (`#F5EDE0`)
- **Typography:** Oswald (display, military-condensed), DM Sans (body), JetBrains Mono (technical labels), Allura (script wordmark)
- **Aesthetic intent:** field manual meets premium lifestyle — tactical without being LARP, refined without being precious
- All fonts loaded from Google Fonts, no local font files needed

---

## Tech notes

- Single HTML file, no build step, no dependencies to install
- Chart.js loaded from CDN for the three charts
- Google Fonts loaded from CDN
- No tracking, no analytics, no cookies (just localStorage for form persistence)
- Mobile-responsive
- Print stylesheet included (Luie can print the whole thing as a 6-page handout if he wants)
- Works offline once loaded

---

## Maintenance

This is meant to be a snapshot of the strategy at a point in time. After Luie sends feedback:

1. Capture his answers (the email)
2. Update the plan based on his input
3. Push a new version of `index.html` if you want the site to reflect the updated plan
4. Or archive this version and start a v2 site for the next review round

That's it. No infrastructure to maintain, no servers to babysit.

---

*"You don't have to get ready, if you stay ready."*
