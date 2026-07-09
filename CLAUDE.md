# manscaped-outdoors — Claude Code context

## Read first
Before working, read **`docs/REFERENCE.md`** — the source of truth for this project. This file is just the quick orientation.

## What this is
Landing/sales page redesign for Manscaped Outdoors, a landscaping company in Clarkesville, GA. Current site (manscapedoutdoors.com) is outdated and being replaced. Frontend-only for now — CRM, AI chatbot, and AI inbound call/text agent are planned future phases, not in current scope.

## Stack
Simple static HTML/CSS/JS, no framework, no build step. Deployed via GitHub Pages. Files: `index.html`, `css/styles.css`, `js/main.js`. Preview locally with `python3 -m http.server 8765` from the repo root.

## Conventions & rules
- Secrets live in env vars / `.env.local` only, never in code. `.env.local` is gitignored. Rotate immediately if exposed.
- Commit + push at the end of each session to back up. Commit messages end with the Co-Authored-By line.
- Reference assets/briefs live in the client's Google Drive folder ("Manscaped Outdoors") — check there before asking the client for materials that may already exist.

## Current priority
Multi-page site built and verified in-browser: Home (index.html), Services, About, Contact — mirrors the old live site's structure, content rewritten from the old pages. Founder is Jared (note: "Keith" in old notes is the project point of contact, "Jared" is the public-facing founder/owner).

Immediate next steps: (1) wire the contact form to a real backend — currently a mailto fallback; Resend or Formspree (see NOTE in js/main.js + contact.html). (2) Deploy to GitHub Pages, point manscapedoutdoors.com DNS at it. (3) Swap in a unique service-area/About photo from the Drive "Premium-Portfolio/Landscape" folder to fully de-dup imagery (browser auto-download from Drive kept failing this session — Miguel can drag the file into assets/). See docs/REFERENCE.md for details.
