# manscaped-outdoors — Claude Code context

## Read first
Before working, read **`docs/REFERENCE.md`** — the source of truth for this project. This file is just the quick orientation.

## What this is
Premium sales-site redesign for Manscaped Outdoors, an outdoor design-build company for mountain/lake homes in Northeast Georgia (Clarkesville base) + select Western NC. Current site (manscapedoutdoors.com) is outdated and being replaced. Frontend-only for now — CRM, AI chatbot, and AI inbound call/text agent are planned future phases, not in current scope.

**Positioning is locked to the client's "Website Build Direction + SEO Architecture" brief (PDF in ~/Downloads/Manscaped_Outdoors_Website_Build_Direction.pdf); the full build was applied 2026-07-21.** Premium landscape design / hardscapes / retaining walls / drainage / decks / outdoor living. Do NOT reintroduce lawn-care, maintenance, quarterly installs, "rock features," "outdoor construction," or "outdoor carpentry" as primary language.

## Stack
Simple static HTML/CSS/JS, no framework, no build step. Deployed via GitHub Pages. Files: `index.html`, `css/styles.css`, `js/main.js`. Preview locally with `python3 -m http.server 8765` from the repo root.

## Conventions & rules
- Secrets live in env vars / `.env.local` only, never in code. `.env.local` is gitignored. Rotate immediately if exposed.
- Commit + push at the end of each session to back up. Commit messages end with the Co-Authored-By line.
- Reference assets/briefs live in the client's Google Drive folder ("Manscaped Outdoors") — check there before asking the client for materials that may already exist.

## Current priority
Multi-page site (Home / Services / About / Contact) fully repositioned to the client brief and verified in-browser on 2026-07-21: locked hero H1 + subheadline, six locked service categories with keyword-rich copy and future-proof anchors, premium mountain/lake service-area copy, and the full contact lead-qualification form (project type / budget / location / timeline / photo-video upload + UTM tracking). Keith = project point of contact, Jared = public-facing founder/owner.

Immediate next steps: (1) wire the contact form to a real backend — still a mailto fallback and files can't attach via mailto; Resend or Formspree (see NOTE in js/main.js + contact.html), persisting the lead-tracking fields per brief §8. (2) Deploy to GitHub Pages / apex Vercel flow, point manscapedoutdoors.com DNS at it. (3) Curate per-service and portfolio imagery from the Drive (current service images are best-fit, not category-specific). See docs/REFERENCE.md for full detail.
