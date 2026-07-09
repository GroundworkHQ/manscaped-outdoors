# manscaped-outdoors — Reference

> Source-of-truth reference for manscaped-outdoors. Keep it current; `CLAUDE.md` points every new session here.

## 1. Overview
Landing/sales page for Manscaped Outdoors, a landscaping company serving Clarkesville, GA and surrounding Northeast Georgia. Current site (manscapedoutdoors.com) is dated and being fully redesigned. Client point of contact: Keith.

Long-term vision (future phases, NOT in current scope): basic CRM with sales pipeline tracking, AI chat bot, and an AI agent handling inbound calls and texts. This build is frontend only.

## 2. Stack & accounts
- Static HTML/CSS/JS, no framework, no build step (kept simple per client scope)
- Repos (GitHub org GroundworkHQ): **`manscaped-outdoors`** (private, source of truth) and **`miguelloza-forwards`** (the apex Vercel deploy — serves the preview)
- Hosting (current): **live preview at https://miguelloza.com/manscaped-outdoors/** via the apex Vercel flow ([[apex-site-flow]]). Final hosting for `manscapedoutdoors.com` TBD at deploy time (static → GitHub Pages or Vercel).
- Domain: manscapedoutdoors.com (currently the old site — this project replaces it)
- Reference assets/briefs: Google Drive folder "Manscaped Outdoors" (fully downloaded to ~/Downloads this session)

## 3. Architecture
Multi-page static site, no backend, no build step, no framework. Plain HTML/CSS/JS served from the repo root for GitHub Pages. Structure mirrors the old live site (Home / Services / About / Contact).
- `index.html` — Home: hero (static image), services preview (→ services.html), portfolio grid + lightbox, two before/after sliders (on a sage band), service area, CTA band (→ contact.html)
- `services.html` — 4 services as alternating image/text detail rows (Landscape Design, Hardscape, Seasonal Installations, Rock Features) + CTA
- `about.html` — Jared's story, pull quote, values, service area + CTA
- `contact.html` — "Let's bring your vision to life" + estimate form (First/Last/Email/Phone/Project type/Message) + details + FB + same-day-response note
- `css/styles.css` — all styles; brand palette + type as CSS custom properties in `:root`. Fonts: Fraunces (display) + Inter (body) via Google Fonts. Shared component classes reused across pages.
- `js/main.js` — vanilla IIFE, no deps: header scroll state, mobile nav toggle, IntersectionObserver scroll-reveals, portfolio lightbox, contact-form mailto fallback (reads split firstName/lastName defensively), footer year. Respects `prefers-reduced-motion`.

**Multi-page conventions:**
- Header/footer markup is duplicated across the 4 pages (no build/includes) — keep them in sync when editing nav or footer.
- Subpages set `class="site-header is-scrolled"` + `data-solid` on the header so it stays solid (cream) with no video hero behind it; `main.js` keeps `is-scrolled` on when `data-solid` is present.
- Active nav link: add `aria-current="page"` to the current page's nav `<a>` (styled ember + underline).
- `.page-banner` (with inline `background-image` per page) is the top section on every subpage; its padding clears the fixed header.

## 4. What's built
- **Full multi-page site (Home / Services / About / Contact), built + verified + deployed.** Content for Services/About/Contact pulled from the old live site (manscapedoutdoors.com/services, /about-us..., /contact-us) and rewritten. Founder is **Jared** (grew up local, works alongside the crew). Extended service area: Clarkesville, **Lake Burton, Toccoa**, Habersham County.
- **Hero: STATIC wide aerial still** (`assets/hero/hero-still.jpg`). We tried a rotating drone video loop (dizzy) and a fire-only cinemagraph (loop artifacts) — both rejected; **static was the final call.** The video files (`hero-eydmdd9.mp4`, `-loop.mp4`, `-cinemagraph.mp4`, `-poster.jpg`) remain in `assets/hero/` but are **unused** by the page.
- **Before / After sliders** — two on the Home page (after portfolio, on a soft-sage separation band): (1) Shirley project, barren slope → boulder walls & fire-pit patio; (2) Container-Home, raw grade → stone steps & retaining wall. clip-path wipe driven by a keyboard-accessible range input; each slider's Before/After tag hides at the extreme so only the visible photo's label shows. Images in `assets/before-after/` (`ba-*` = slider 1, `ba2-*` = slider 2), 3:4 portrait.
- **Client reviews** — 3 testimonials on About (Carolyn Wilkes / Chuck Furstenau / Darren Hoeffner), from the old site.
- **Services page photos** — real per-service images in `assets/services/` (landscape-design, hardscape, rock-features, seasonal-installations), pulled from the old site (fixed an earlier mismatch where cabin/deck photos were used).
- **About founder photo** — `assets/jared.jpg` (pulled from the old site, optimized) in the Meet Jared section.
- Logo `assets/manscaped-outdoors-logo.png` (500x500 raster — ask Keith for a vector). 9 portfolio photos `assets/portfolio/` in the grid + lightbox.
- **Deployed (live preview):** https://miguelloza.com/manscaped-outdoors/ — served via the apex Vercel flow (see [[apex-site-flow]]). Source of truth: private repo `GroundworkHQ/manscaped-outdoors`. Deploy copy: `GroundworkHQ/miguelloza-forwards` (subfolder `manscaped-outdoors/`, git auto-deploys to Vercel).

## 5. What's next
- **Contact form has no backend** — `mailto:` fallback (opens the user's mail client). Wire to Resend (Miguel's stack) or Formspree: set a real form action and remove the mailto handler in `js/main.js` (NOTE comments mark the spot in `js/main.js` + `contact.html`).
- **Broader photo curation (now unblocked).** The **entire Drive is downloaded**: `~/Downloads/Manscaped Outdoors-...-2-001.zip` (~1.3GB, includes 13 videos + 179 images). Browser downloads from Drive don't work in-session — this was a manual bulk-download. Re-extract images from that zip (skip videos) to curate. To do: swap the remaining portfolio/service/About imagery for best-of-library, and fix the last home-page duplicate (the service-area image `IMG_5567` is reused from the portfolio grid). Notable folders: `Shirley_Project_Photos` (before/after + `_1.Best`/`_2.Best` curated), `Container-Home.../Before+After` (curated + `PHOTO_SELECTION_NOTES.txt`), `Premium-Portfolio` (Landscape/Stonework/Boulder.Wall/etc.).
- **Deploy to the real domain** `manscapedoutdoors.com` when the client approves (currently only on the miguelloza.com preview). NOTE: the site is fully static and could go on GitHub Pages OR the Vercel apex flow — decide at deploy time.
- Optional: more before/after sliders (Drive has more matched pairs).

## 6. Conventions
- Plain static site, no build step — edit `index.html` / `css/styles.css` / `js/main.js` directly. Preview: `python3 -m http.server 8765` from the repo root → `http://127.0.0.1:8765`.
- Brand colors + type are CSS custom properties in `:root` at the top of `styles.css`. Ember orange (`--ember`) is the CTA/accent; the rest is the earthy logo palette (bark/olive/sage/cream/trunk).
- **Hero is a static `<img>`** (`hero-still.jpg`), not a video. Don't re-introduce the drone video loop — it was rejected as dizzy (rotating + zooming footage loops badly). The unused video files can be deleted if you want to slim the repo.
- Section reveals: `data-reveal` is added by JS + an IntersectionObserver — to animate a new section, just add its selector to the `revealTargets` query in `main.js` (no HTML attribute needed).
- Before/after slider: markup is a `.ba` figure with `data-ba`; JS loops all `[data-ba]`, so adding another slider needs no JS changes. The wipe is `clip-path` on `.ba__before` driven by `--pos` (a range input). Two-up via `.ba-grid`.
- **Deployment (two-repo sync).** Edit the **source** repo (`manscaped-outdoors`), commit + push. Then sync the web files (`index.html`, `css/`, `js/`, changed `assets/`) into `miguelloza-forwards/manscaped-outdoors/`, **re-add `<base href="/manscaped-outdoors/" />` after `<head>` in the copied `index.html`** (source has no base tag), commit + push → Vercel auto-deploys. Full flow in [[apex-site-flow]].

## 7. Open decisions
- Final branding direction — current site's logo ("tree of life in a circle") and photography may carry over, but overall design needs a full refresh since current site is considered outdated
- CRM / AI chatbot / AI call-and-text agent are explicitly deferred to a future phase — do not scope them into this build

## Brand palette (derived from logo)
- Olive/sage green (background)
- Dark brown / near-black (ring, text background)
- Cream / tan (lettering, tree linework highlights)
- Warm mid-brown (tree trunk, roots)
Logo: illustrated tree-of-life emblem in a circular badge, earthy/rustic aesthetic — matches the outdoor/landscaping trade well. Current design needs modernizing but the color story and tree motif are worth carrying forward.

## Business reference (pulled from current live site)
- Services: Landscape Design, Hardscapes (patios, walkways, retaining walls, fire pits), Quarterly Installations, Rock Features (stone ponds, waterfalls, dry creek beds)
- Phone: (469) 841-6524
- Email: info@manscapedoutdoors.com
- Facebook: facebook.com/manscapedlawncare
- Service area: Clarkesville, GA and surrounding Northeast Georgia
- Tagline: "we craft outdoor experiences"
