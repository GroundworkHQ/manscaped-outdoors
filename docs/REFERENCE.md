# manscaped-outdoors — Reference

> Source-of-truth reference for manscaped-outdoors. Keep it current; `CLAUDE.md` points every new session here.

## 1. Overview
Landing/sales page for Manscaped Outdoors, a landscaping company serving Clarkesville, GA and surrounding Northeast Georgia. Current site (manscapedoutdoors.com) is dated and being fully redesigned. Client point of contact: Keith.

Long-term vision (future phases, NOT in current scope): basic CRM with sales pipeline tracking, AI chat bot, and an AI agent handling inbound calls and texts. This build is frontend only.

## 2. Stack & accounts
- Static HTML/CSS/JS, no framework for now (kept simple per client scope)
- Hosting: GitHub Pages
- Domain: manscapedoutdoors.com (currently live with the old site — this project replaces it)
- Reference assets/briefs: Google Drive folder "Manscaped Outdoors"

## 3. Architecture
Multi-page static site, no backend, no build step, no framework. Plain HTML/CSS/JS served from the repo root for GitHub Pages. Structure mirrors the old live site (Home / Services / About / Contact).
- `index.html` — Home: hero (boomerang video), services preview (→ services.html), portfolio grid + lightbox, service area, CTA band (→ contact.html)
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
- **Full multi-page site (Home / Services / About / Contact), verified in-browser** — hero video w/ seamless loop, alternating service rows, Jared's About story, contact form, lightbox, responsive, active nav, zero console errors. Content for Services/About/Contact was pulled from the old live site (manscapedoutdoors.com/services, /about-us..., /contact-us) and rewritten. Founder is **Jared** (grew up local, works alongside the crew). Extended service area: Clarkesville, **Lake Burton, Toccoa**, Habersham County.
- **Landing page** (earlier scaffold, now the Home page).
- Logo pulled from live site, saved at `assets/manscaped-outdoors-logo.png` (500x500 PNG — highest-res available on the current site; raster, not vector — ask Keith for the original AI/SVG if one exists). Used as brand mark + favicon.
- 9 portfolio photos at `assets/portfolio/` (IMG_5564–5573.JPG, 960x540–2048x1152) — wired into the portfolio grid + lightbox.
- **Hero video processed + wired in** (see item 5 for the full decision trail): `assets/hero/hero-eydmdd9.mp4` (1080p web, 5.2MB), `hero-eydmdd9-loop.mp4` (boomerang forward+reverse for a seamless loop, 9.8MB — this is the one the page uses), `hero-eydmdd9-poster.jpg` (poster still). Made with ffmpeg.

## 5. What's next
- **Contact form has no backend yet** — currently a `mailto:` fallback (opens the user's mail client). Future: wire to Resend (Miguel's stack) or Formspree by setting a real form action and removing the mailto handler in `js/main.js` (marked with a NOTE comment there and in index.html).
- Pull more/better portfolio photos as needed — the current 9 are cabin/deck/vista shots (great for "outdoor living" feel but light on pure hardscape/stonework close-ups). The Drive folder ("Manscaped Outdoors") has much more:
  - `Shirley_Project_Photos` → "*1.Best" (10 photos) and "*2.Best" (9 photos) — very large files (5–11MB each), compress before web use
  - `Premium-Portfolio` → Landscape, Stonework, Premium, Artificial+Turf, Boulder.Wall, Carpentry/Outdoor+Construction subfolders — only "Premium" surveyed so far (6 files, 3.8–7MB each)
  - `Container-Home_Carpentry+Total-Landscape` → "Before+After" subfolder not yet pulled (only "Best-After-Shots" done)
  - `B-Miller_Hardscape+Design` → only a "Videos" subfolder, not yet explored
- Consider a secondary "our craft" section using a work-in-action clip (reserve candidates: 9BRD3DA paver build, UKG8EMP retaining wall — see item on hero decision).
- Deploy to GitHub Pages, point manscapedoutdoors.com DNS at it.
- All large source photos (5-11MB) will need resizing/compression before use — raw camera-resolution files are too heavy for web.
- **Hero video decision (FINAL):** `EYDMDD9` — "Aerial top-down drone over fire pit in stone-path garden" by BlackBoxGuild (elements.envato.com/aerial-top-down-drone-rotate-above-fire-pit-table--EYDMDD9), 4K UHD horizontal. Chosen after pivoting the hero concept from terrain-matching (rejected the Zenistock "riding lawn mower" European-estate series — didn't match NE Georgia / NC Appalachian-foothills terrain) to a "work in action / finished outdoor-living" beauty shot that sells the craft directly.
  - **Downloaded + processed + wired in.** 4K master (68MB, 3840x2160, 11.3s, no audio) downloaded via Miguel's Envato account. ffmpeg outputs in `assets/hero/`: `hero-eydmdd9.mp4` (1080p, CRF 24, muted, +faststart, 5.2MB), `hero-eydmdd9-loop.mp4` (boomerang, seamless, 9.8MB — **used by the page**), `hero-eydmdd9-poster.jpg` (frame @ 5s, 324KB). 4K master left in Miguel's ~/Downloads, not committed (too heavy for the Pages repo). To regenerate the loop: `ffmpeg -i hero-eydmdd9.mp4 -filter_complex "[0]split[a][b];[b]reverse[r];[a][r]concat=n=2:v=1[out]" -map "[out]" -c:v libx264 -pix_fmt yuv420p -crf 24 -movflags +faststart -an hero-eydmdd9-loop.mp4`.

## 5. What's next
- Pull more portfolio photos as needed — the Drive folder ("Manscaped Outdoors") has much more available beyond the initial batch grabbed:
  - `Shirley_Project_Photos` → "*1.Best" (10 photos) and "*2.Best" (9 photos) — NOTE: these are very large files (5–11MB each), will need compression before web use
  - `Premium-Portfolio` → Landscape, Stonework, Premium, Artificial+Turf, Boulder.Wall, Carpentry/Outdoor+Construction subfolders — only "Premium" subfolder has been surveyed so far (6 files, also large 3.8–7MB each)
  - `Container-Home_Carpentry+Total-Landscape` → "Before+After" subfolder not yet pulled (only "Best-After-Shots" done)
  - `B-Miller_Hardscape+Design` → only has a "Videos" subfolder, not yet explored
- Build landing page sections (services, service area, contact/estimate request, portfolio/photos)
- Deploy to GitHub Pages, point manscapedoutdoors.com DNS at it
- All large source photos (5-11MB) will need resizing/compression before use on the actual site regardless of source — raw camera-resolution files are too heavy for web
- **Hero video decision (FINAL):** `EYDMDD9` — "Aerial top-down drone over fire pit in stone-path garden" by BlackBoxGuild (elements.envato.com/aerial-top-down-drone-rotate-above-fire-pit-table--EYDMDD9), 4K UHD horizontal. Chosen after pivoting the hero concept from terrain-matching (rejected the Zenistock "riding lawn mower" European-estate series — didn't match NE Georgia / NC Appalachian-foothills terrain) to a "work in action / finished outdoor-living" beauty shot that sells the craft directly. Reserve/secondary "our craft" candidates if needed: 9BRD3DA (paver pathway build), UKG8EMP (block retaining wall build), S8CQXAE (backyard patio).
  - **Downloaded + processed.** 4K master (68MB, 3840x2160, 11.3s, no audio) downloaded via Miguel's Envato account. Web version created with ffmpeg: `assets/hero/hero-eydmdd9.mp4` (1080p, CRF 24, muted, +faststart, 5.2MB) plus poster still `assets/hero/hero-eydmdd9-poster.jpg` (frame @ 5s, 324KB). 4K master left in Miguel's ~/Downloads, not committed (too heavy for the Pages repo).
  - Still needs: wire into the hero `<video>` (autoplay + muted + loop + playsinline, poster=hero-eydmdd9-poster.jpg, brand-tinted overlay for text legibility) when the landing page is scaffolded.

## 6. Conventions
- Plain static site, no build step — edit `index.html` / `css/styles.css` / `js/main.js` directly. To preview: `python3 -m http.server 8765` from the repo root, open `http://127.0.0.1:8765`.
- Brand colors and type live as CSS custom properties in `:root` at the top of `styles.css` — change them there, not scattered through the file. Ember orange (`--ember`) is the CTA/accent, pulled from the hero fire; everything else is the earthy logo palette (bark/olive/sage/cream/trunk).
- Video assets: ship a compressed web version, never the raw 4K master. Hero background uses the boomerang `-loop.mp4` so it repeats seamlessly.
- Section reveals use `data-reveal` added by JS + an IntersectionObserver; if you add a section and want it to animate in, no attribute needed in HTML — just add its selector to the `revealTargets` query in `main.js`.

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
