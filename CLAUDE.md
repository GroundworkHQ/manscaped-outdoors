# manscaped-outdoors — Claude Code context

## Read first
Before working, read **`docs/REFERENCE.md`** — the source of truth for this project. This file is just the quick orientation.

## What this is
Premium sales-site redesign for Manscaped Outdoors, an outdoor design-build company for mountain/lake homes in Northeast Georgia (Clarkesville base) + select Western NC. Current site (manscapedoutdoors.com) is outdated and being replaced. Frontend-only for now — CRM, AI chatbot, and AI inbound call/text agent are planned future phases, not in current scope.

**Positioning is locked to the client's "Website Build Direction + SEO Architecture" brief (PDF in ~/Downloads/Manscaped_Outdoors_Website_Build_Direction.pdf); the full build was applied 2026-07-21.** Premium landscape design / hardscapes / retaining walls / drainage / decks / outdoor living. Do NOT reintroduce lawn-care, maintenance, quarterly installs, "rock features," "outdoor construction," or "outdoor carpentry" as primary language.

## Stack
Simple static HTML/CSS/JS, no framework, no build step. Files: `index.html`, `css/styles.css`, `js/main.js`. Preview locally with `python3 -m http.server 8765` from the repo root. **Hosting (current, 2026-07-30): live preview at miguelloza.com/manscaped-outdoors/ via the apex Vercel flow — NOT GitHub Pages.** Final hosting for the real domain is no longer an open GitHub-Pages-vs-Vercel choice either: the plan is to deploy into the client's own existing SiteGround account (where manscapedoutdoors.com already resolves), not a fresh GitHub Pages/Vercel setup. See docs/REFERENCE.md §5 for the handoff plan.

## Conventions & rules
- Secrets live in env vars / `.env.local` only, never in code. `.env.local` is gitignored. Rotate immediately if exposed.
- Commit + push at the end of each session to back up. Commit messages end with the Co-Authored-By line.
- Reference assets/briefs live in the client's Google Drive folder ("Manscaped Outdoors") — check there before asking the client for materials that may already exist.

## Current priority
Multi-page site (Home / Services / About / Contact) fully repositioned to the client brief and verified in-browser on 2026-07-21: locked hero H1 + subheadline, six locked service categories with keyword-rich copy and future-proof anchors, premium mountain/lake service-area copy, and the full contact lead-qualification form (project type / budget / location / timeline / photo-video upload + UTM tracking). Jared = business owner/founder; Keith = the marketing consultant Jared hired (and Miguel's friend), the day-to-day point of contact. Business runs on GoHighLevel (GHL) as CRM **and native phone system**.

**Since 2026-07-21, also done (this section was stale until 2026-07-30 — see docs/REFERENCE.md §4 for full detail on each):** contact form wired into GHL (2026-07-24, verified end-to-end, replaced the mailto fallback entirely); privacy policy page added for Meta ad compliance (2026-07-28); GHL call-transfer pause bug found and fixed (2026-07-29); hosting handoff to the client's own SiteGround account started (2026-07-29/30) and the staging subdomain is now **live**: `new.manscapedoutdoors.com` has the full static build deployed and verified rendering correctly (see docs/REFERENCE.md §5 for the full deploy log).

**Home page reordered 2026-07-30** per Jared's feedback: the portfolio now sits directly below the hero (hero → portfolio → intro → services → before/after → area → CTA), cutting the scroll-to-first-project from ~3.4 desktop / ~3.9 mobile screens down to exactly one. The hero "View Our Work" button now points at `#before-after`. **🚀 LIVE ON THE REAL DOMAIN as of 2026-07-30.** `manscapedoutdoors.com` now serves this static site; WordPress has been removed from `public_html`. See docs/REFERENCE.md §4b for the full cutover log, including the two things that matter for any future deploy: **`.well-known/` must be preserved** (SSL cert validation + email autodiscovery) and **`.htaccess` had to be deleted** (its WordPress rewrite rule would have broken the static site). Backup `Pre-cutover WordPress 2026-07-30` is retained.

Also live on the miguelloza.com preview and the `new.manscapedoutdoors.com` staging site (both byte-identical to source). See docs/REFERENCE.md §4 — including the **SiteGround Dynamic Cache gotcha**: after any file change, the bare root `/` keeps serving a stale cached page until you flush Speed → Caching → Dynamic Cache for that host. Expect to hit this again on the production cutover.

Immediate next steps: (1) get Jared/Keith to review and sign off on https://new.manscapedoutdoors.com/, then back up WordPress and cut `public_html` over to the static build (Miguel wants to confirm that cutover step explicitly first — live production domain). (2) Build the parked AI chatbot — reuse the same GHL webhook the contact form already uses, and note assistant-starter's backend moved to Supabase Edge Functions 2026-07-30 (re-check docs/REFERENCE.md §5 before building, the old plan assumed Vercel). (3) Add Jared's Google reviews to the About page. (4) Curate remaining per-service/portfolio imagery from the Drive. See docs/REFERENCE.md for full detail.
