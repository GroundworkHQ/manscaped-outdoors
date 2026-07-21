# manscaped-outdoors — Reference

> Source-of-truth reference for manscaped-outdoors. Keep it current; `CLAUDE.md` points every new session here.

## 1. Overview
Premium sales site for Manscaped Outdoors, an outdoor design-build company serving mountain and lake properties across Northeast Georgia (Clarkesville base) plus select Western North Carolina by project fit. Current site (manscapedoutdoors.com) is dated and being fully redesigned. Client point of contact: Keith. Public-facing founder: Jared.

**Positioning locked to the client's "Website Build Direction + SEO Architecture" brief (July 2026, PDF in ~/Downloads/Manscaped_Outdoors_Website_Build_Direction.pdf).** The site is built around that brief and its whole build was applied on 2026-07-21. Core positioning: premium landscape design, hardscape, retaining wall, drainage, deck, and outdoor living company for North Georgia mountain/lake homes. Do NOT reintroduce lawn-care, maintenance, quarterly-install, "rock features," "outdoor construction," or "outdoor carpentry" as primary language (see brief §11 Do/Do-Not).

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
- **Repositioned to the client brief (2026-07-21).** All four pages rewritten to the "Website Build Direction" brief and verified in-browser:
  - **Home hero** — locked H1 "Premium Landscape Design, Hardscapes & Outdoor Living in Northeast Georgia" + locked subheadline; CTAs "Start Your Project" / "View Our Work"; supporting line "Built for Mountain Terrain · Designed for Outdoor Living" (eyebrow). New short intro section, then a **six-card services preview** linking to the services-page anchors, then portfolio, before/after, and the premium service-area section. Final CTA "Ready to Build Something That Lasts?"
  - **Six locked service categories** (replaced the old 4). Public architecture + slugs/anchors: `#landscape-design-installation`, `#patios-hardscapes-outdoor-living`, `#retaining-walls-boulder-walls`, `#drainage-grading-erosion-control`, `#decks-pergolas-outdoor-structures`, `#full-property-transformations`. These match the future `/services/<slug>` URLs so individual pages can be added later without rebuild. Deep keyword-rich copy per category; a **sticky quick-nav** sits under the banner and jumps to each (scroll-margin clears header + sub-nav).
  - **About** — headline "Rooted in Northeast Georgia. Built for Serious Outdoor Work.", growth-into-premium-design-build story, new "Beauty matters. Structure comes first." philosophy band, values retuned (Terrain First / Hands-On Craft / Relationships), 3 real reviews kept, premium service-area copy.
  - **Contact** — full lead-qualification form: First/Last, Phone, Email, Project Location/Nearest Community, Project Type (6 categories + Not Sure Yet), Approximate Budget dropdown ($ ranges), Desired Timeline, Project Description, Photo/Video upload. Hidden fields capture landing page + referrer + UTM for lead source; all fields + tracking go into the mailto body today and map cleanly to a real backend later.
  - **SEO titles** per brief §9 on all four pages; footer description + og copy updated site-wide to the premium blurb.
- Content originally pulled from the old live site (manscapedoutdoors.com/services, /about-us..., /contact-us) and rewritten. Founder is **Jared** (grew up local, works alongside the crew). Featured service area now the premium mountain/lake set: Clarkesville, Lake Burton, Lake Rabun, Lakemont, Tiger, Clayton, Rabun County, Blue Ridge, Lake Blue Ridge, Mineral Bluff, Aska/Toccoa River, Highlands NC, Cashiers NC (plus a "also serve by project fit" support line). Avoid "all of Habersham County" as the premium pitch.
- **Hero: STATIC wide aerial still** (`assets/hero/hero-still.jpg`). We tried a rotating drone video loop (dizzy) and a fire-only cinemagraph (loop artifacts) — both rejected; **static was the final call.** The video files (`hero-eydmdd9.mp4`, `-loop.mp4`, `-cinemagraph.mp4`, `-poster.jpg`) remain in `assets/hero/` but are **unused** by the page.
- **Before / After sliders** — two on the Home page (after portfolio, on a soft-sage separation band): (1) Shirley project, barren slope → boulder walls & fire-pit patio; (2) Container-Home, raw grade → stone steps & retaining wall. clip-path wipe driven by a keyboard-accessible range input; each slider's Before/After tag hides at the extreme so only the visible photo's label shows. Images in `assets/before-after/` (`ba-*` = slider 1, `ba2-*` = slider 2), 3:4 portrait.
- **Client reviews** — 3 testimonials on About (Carolyn Wilkes / Chuck Furstenau / Darren Hoeffner), from the old site.
- **Services page photos** — real per-service images in `assets/services/` (landscape-design, hardscape, rock-features, seasonal-installations), pulled from the old site (fixed an earlier mismatch where cabin/deck photos were used).
- **About founder photo** — `assets/jared.jpg` (pulled from the old site, optimized) in the Meet Jared section.
- Logo `assets/manscaped-outdoors-logo.png` (500x500 raster — ask Keith for a vector). 9 portfolio photos `assets/portfolio/` in the grid + lightbox.
- **Deployed (live preview):** https://miguelloza.com/manscaped-outdoors/ — served via the apex Vercel flow (see [[apex-site-flow]]). Source of truth: private repo `GroundworkHQ/manscaped-outdoors`. Deploy copy: `GroundworkHQ/miguelloza-forwards` (subfolder `manscaped-outdoors/`, git auto-deploys to Vercel).

## 5. What's next
- **Contact form still has no backend** — the qualification structure + lead-source tracking are built, but it's still a `mailto:` fallback (opens the user's mail client) and **file uploads can't attach via mailto** (the handler only lists filenames). Wire to Resend (Miguel's stack) or Formspree: set a real form action, POST the fields + files, and remove the mailto handler in `js/main.js` (NOTE comments mark the spot in `js/main.js` + `contact.html`). Backend must persist landing page / referral / UTM / project type / budget / location / timeline / uploads (brief §8 "Backend tracking request").
- **Hero is now a real project photo (2026-07-21).** Replaced the overhead drone still with `assets/hero/hero-flagstone.jpg` — a client flagstone-patio + curved seat-wall shot (from the Drive's Premium-Portfolio/Stonework set, orig `IMG_2149.png`, the "option D" Miguel picked). Eye-level and premium, per his feedback that the overhead angle looked flat. The unused `hero-still.jpg` + video variants remain in `assets/hero/`. Client also liked "option C" (`IMG_2148.png`, flagstone STEPS + stacked walls) but its harsh midday cast shadow can't be cleanly lifted — earmarked for the Services retaining-walls/steps section (smaller, shadow reads as depth), not yet placed.
- **Service-page imagery is now curated from the client Drive (2026-07-21).** Each of the six sections uses a real, category-matched project photo (all in `assets/services/` unless noted): landscape=`landscape-design-planting.jpg` (planting beds + stone edging, from Drive Landscape UUID set), patios=`patios-outdoor-living.jpg` (circular flagstone patio w/ star inlay, `IMG_2147`), retaining=`retaining-walls-steps.jpg` (stone steps + stacked walls, `IMG_2148` = "option C", **un-lightened original** per Miguel), drainage=`drainage-grading.jpg` (excavator + graded soil + drainage pipe, `IMG_2052` — authentic earthwork), decks=`assets/portfolio/IMG_5566.JPG` (real deck, kept), transformations=`full-transformation.jpg` (paver + putting green + boulder wall + home, `IMG_2154`). Old best-fit images (`hardscape.jpg`, `rock-features.jpg`, `landscape-design.jpg`, `seasonal-installations.jpg`, `before-after/ba*.jpg`) are now unused by services but remain in the repo.
  - **Home portfolio grid also refreshed (2026-07-21):** curated 9-image mix of daytime craft (`portfolio-flagstone-patio.jpg`, `portfolio-putting-green.jpg`, `portfolio-stone-column.jpg`, `portfolio-boulder-wall.jpg`) + the professional dusk Container-Home lifestyle shots (`IMG_5565` illuminated steps, `IMG_5569`/`IMG_5572` deck fire pits, `IMG_5571` hot tub, `IMG_5564` aerial). Dropped weaker `IMG_5566/5567/5568/5573` from the grid.
  - NOTE: hero + all 6 service photos + the portfolio grid now come from the Drive's Premium-Portfolio + Container-Home sets. Extracted candidate library + contact sheets are in the session scratchpad (not committed). The hero-picker comparison artifact: https://claude.ai/code/artifact/2ba7fa7f-9471-4984-94a7-ab9a78c584d9
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
