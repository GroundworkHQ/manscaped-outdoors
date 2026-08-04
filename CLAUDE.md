# manscaped-outdoors — Claude Code context

## Read first
**`docs/REFERENCE.md`** is the source of truth. Read it before working. This file is orientation only and deliberately holds no project state — if a fact about status, history, or deploys is worth writing down, it goes in REFERENCE.md, not here.

## What this is
Premium sales site for Manscaped Outdoors, an outdoor design-build company for mountain/lake homes in Northeast Georgia (Clarkesville base) plus select Western NC. **Live on `manscapedoutdoors.com` since 2026-07-30.**

Jared = business owner. Keith = the marketing consultant Jared hired, Miguel's friend, and the day-to-day contact.

## Stack
Static HTML/CSS/JS. No framework, no build step. `index.html` + `about.html` + `contact.html` + `privacy-policy.html` + `services.html`, plus `css/styles.css`, `js/main.js`, `assets/`.

Preview locally: `python3 -m http.server 8765` from the repo root.

## Before you ship
Four things bite on this project. Each is explained in REFERENCE.md, listed here only so you check them:

1. **Bump `?v=YYYYMMDD` on `styles.css` and `main.js` in all five HTML pages** after any CSS or JS change. Assets cache for a year on purpose; the version query is the only thing that reaches returning visitors. (§4d)
2. **Production deploys are manual** through SiteGround's File Manager, and images can only be uploaded by Miguel. Flush Dynamic Cache afterwards or `/` keeps serving a stale page. (§6)
3. **Positioning is locked to the client's Build Direction brief.** Do not reintroduce lawn care, maintenance, quarterly installs, "rock features," "outdoor construction," or "outdoor carpentry" as primary language. (§1)
4. **Never reword client-approved copy** without asking, and no em dashes anywhere in site copy.

## Conventions & rules
- Secrets live in env vars / `.env.local` only, never in code. `.env.local` is gitignored. Rotate immediately if exposed.
- Do not commit or push unless Miguel says to. Commit messages end with the Co-Authored-By line.
- Reference assets and briefs live in the client's Google Drive folder ("Manscaped Outdoors"). Check there before asking the client for materials that may already exist.

## Current priority
See **REFERENCE.md §5**. It is the only list, kept current there.
