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
Single static site, no backend. To be scaffolded.

## 4. What's built
- Logo pulled from live site, saved at `assets/manscaped-outdoors-logo.png` (500x500 PNG — this is the highest-res version available on the current site; it's raster, not vector — ask Keith for the original AI/SVG file if one exists)
- 9 portfolio photos pulled from Drive, saved at `assets/portfolio/` (IMG_5564–5573.JPG, from Container-Home project's "Best-After-Shots" folder, 960x540–2048x1152)

## 5. What's next
- Pull more portfolio photos as needed — the Drive folder ("Manscaped Outdoors") has much more available beyond the initial batch grabbed:
  - `Shirley_Project_Photos` → "*1.Best" (10 photos) and "*2.Best" (9 photos) — NOTE: these are very large files (5–11MB each), will need compression before web use
  - `Premium-Portfolio` → Landscape, Stonework, Premium, Artificial+Turf, Boulder.Wall, Carpentry/Outdoor+Construction subfolders — only "Premium" subfolder has been surveyed so far (6 files, also large 3.8–7MB each)
  - `Container-Home_Carpentry+Total-Landscape` → "Before+After" subfolder not yet pulled (only "Best-After-Shots" done)
  - `B-Miller_Hardscape+Design` → only has a "Videos" subfolder, not yet explored
- Build landing page sections (services, service area, contact/estimate request, portfolio/photos)
- Deploy to GitHub Pages, point manscapedoutdoors.com DNS at it
- All large source photos (5-11MB) will need resizing/compression before use on the actual site regardless of source — raw camera-resolution files are too heavy for web
- **Blocked/deferred:** find a hero-section background video (drone/landscaping footage) on Envato Elements. No Envato MCP was connected this session — check for one in a fresh session before falling back to manual browsing via the Chrome extension at elements.envato.com

## 6. Conventions
<!-- Naming, patterns, security rules, gotchas. -->

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
