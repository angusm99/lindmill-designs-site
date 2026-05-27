# Lindmill Designs — Complete Project Handoff

> **Purpose:** Self-contained reference for an AI agent (Codex, Claude, etc.) or human dev picking up this project cold. Everything you need to be productive on day one lives in this document.
> **Last updated:** 2026-05-24 (post Update 2 Part 1)
> **Repo:** `https://github.com/angusm99/lindmill-designs-site`
> **Latest commit:** `2c13e1c`

---

## 1. Three-bullet orientation

- **What:** Single-file HTML portfolio site for South African motion designer Linda Miller. Replaces a paid Carrd subscription.
- **Stack:** Pure HTML / CSS / vanilla JS in one ~1,925-line `index.html`. No build step. No framework. Deploys to Netlify static hosting.
- **Status:** Fully functional, 201 portfolio images live, awaiting Netlify deploy and a pending project restructure (12 tiles → 25). A separate visual revamp brief exists (`OPEN_DESIGN_BRIEF.md`) for when Linda wants a polish pass.

---

## 2. Quick start

```bash
# Clone
git clone https://github.com/angusm99/lindmill-designs-site.git
cd lindmill-designs-site

# Local preview (Python 3)
python -m http.server 5500 --bind 0.0.0.0
# Desktop: http://localhost:5500
# Mobile (same WiFi): http://192.168.1.106:5500   (LAN IP varies by network)

# That's it. No npm install. No build. Just edit index.html and refresh.
```

**Local filesystem path on dev's machine:**
```
C:\Users\User\Documents\CLAUDE MASTER\Lindmill Designs\lindmilldesigns-site\
```

---

## 3. Project context

### The client — Linda Miller

| | |
|---|---|
| Name | Linda Miller |
| Brand | Lindmill Designs |
| Email | thelindamiller@gmail.com |
| Instagram | @thelindamiller |
| LinkedIn | thelindamiller |
| Location | South Africa (Cape Town area) |
| Discipline | Motion design · illustration · brand identity · textile design · food label design · layout & signage |
| Career | 15+ years. In-house 2011–2021 (Triumph Lingerie → Hamiltons Creative → Root 360 → Rogz Pet Gear). Freelance from April 2021 (Anglo Windows, Timothy Oulton Luxury Travel, The Really Great Teacher Co.) |
| Vibe | Warm, playful, loves animals, brand-focused, thinks in systems and stories |

### Why this site exists

Linda had a Carrd site (`https://lindmilldesign.carrd.co`) — paid subscription, limited customisation. Angus (developer) is building her a free self-hosted replacement with full visual control. Same content + more flexibility + zero ongoing cost.

### Success criteria

- Portfolio is browseable on mobile and desktop
- Prospective clients can email Linda from the site
- Site looks like Linda's work (not a generic template)
- Zero maintenance cost (Netlify free tier)
- Linda can publish updates herself with minimal hand-holding (`HOW-TO-PUBLISH.txt` is her guide)

---

## 4. Tech stack & decisions

### What we chose

| Layer | Choice | Why |
|---|---|---|
| Markup | HTML5, single file | One file is easier for Linda to understand and self-edit |
| Styles | Vanilla CSS in `<style>` | No preprocessor → no build step |
| Scripts | Vanilla JS in `<script>` | No framework → no toolchain |
| Fonts | Custom `@font-face` + Google Fonts | Narnia (custom display), Barlow ExtraBold (custom sub), Fredoka + Nunito (Google) |
| Hosting | Netlify free tier (planned) | Free, fast, HTTPS, drag-and-drop deploy |
| Domain | TBD — likely `lindmilldesigns.com` (Namecheap, ~R200/yr) | |
| Source control | Git → GitHub `angusm99/lindmill-designs-site` | |
| Image format | JPG / GIF / PNG as-supplied | No on-the-fly processing |

### What we explicitly avoided

- ❌ WordPress (would fight every customisation Linda wants, paid PHP host)
- ❌ React / Vue / Svelte (overkill for 4 static pages)
- ❌ Astro / Next.js / any SSG (build step Linda would have to maintain)
- ❌ Tailwind / Bootstrap (custom design system; want full control)
- ❌ Sass / Less / PostCSS (build step)
- ❌ Bundlers, package managers, lockfiles
- ❌ Backend / CMS / DB (site is brochureware)
- ❌ Contact form (uses `mailto:` link instead — no backend needed)
- ❌ Analytics (could add Plausible script tag later if Linda wants)

**Bottom line:** Edit `index.html`, save, refresh browser, push to GitHub. That's the entire dev loop.

---

## 5. Repository structure

```
lindmilldesigns-site/
├── index.html                  # The entire site (1,925 lines)
├── .gitignore                  # OS, editor, temp, _originals/ backup folders
├── README.md                   # Repo readme
├── CHECKPOINT.md               # Recovery guide for the 2026-05-24 stable state
├── COWORK_HANDOFF.md           # Session brief for Cowork (post Update 2 Part 1)
├── OPEN_DESIGN_BRIEF.md        # Visual revamp brief for design agent
├── DESIGN_BRIEF.md             # Earlier design brief from Claude Design handoff
├── CODEX_PROJECT_HANDOFF.md    # This document
├── HOW-TO-PUBLISH.txt          # Linda-facing publishing guide
├── robots.txt                  # SEO — allow all crawlers
├── sitemap.xml                 # SEO — single-page site sitemap
├── fonts/
│   ├── Narnia.ttf              # Custom display font (headings)
│   ├── Narnia.otf              # OpenType variant
│   └── Barlow-ExtraBold.ttf    # Custom sub-heading font
├── videos/
│   └── hero.mp4                # Home page hero video (~12 MB)
└── images/
    ├── lindmill-logo.png       # Hero PNG logo (Home page)
    ├── logo.gif                # Original animated logo (now unused, kept for fallback)
    ├── updated-logo.gif        # Current animated logo (Work + Contact headers, About badge)
    ├── linda-1.jpg             # Contact page portrait 1
    ├── linda-2.jpg             # Contact page portrait 2
    ├── thumbnails/             # 12 project tile thumbnails (01.gif – 12.jpg)
    ├── _originals/             # Local image backups (gitignored)
    │
    ├── animated/               # 38 images — to be split into 6 sub-projects in Update 2 Part 2
    ├── illustrated/            # 22 images — to be split into 5 sub-projects
    ├── drawn/                  # 4 images — to be renamed to "angus" project
    ├── painted/                # 4 images — to be renamed to "lexi" project
    ├── textile-design/         # 18 images — to be split into 3 sub-projects
    ├── layout/                 # 16 images — to be split into 3 sub-projects
    ├── food-labels/            # 19 images
    ├── logo-design/            # 17 images
    ├── social-media/           # 36 images
    ├── content-writing/        # 16 images
    ├── video-editing/          # 7 images
    ├── website-layout/         # 4 images
    │
    └── # Empty folders ready for Update 2 Part 2 (created but un-populated since the revert):
        # blooming-flowers/, dorothy/, new-year/, rogz-animated/, star/, throwball/,
        # pink-moon/, plugged-in/, rogz-characters/, something-fishy/, space-inspectors/,
        # fancy-dress-2018/, fancy-dress-2019/, small-dog-range/,
        # triumph-layout/, food-lovers-layout/, food-lovers-signage/
```

**Asset master folder** (outside repo, on Angus's machine):
```
C:\Users\User\CLAUDE\LINDA MILLER WEBSITE\LINDMILL ASSET FOLDER-20260522T162626Z-3-001\LINDMILL ASSET FOLDER\
├── ALL WORK THUMBNAILS\
├── HOME PAGE\
├── CONTACT\
├── MOTION & ILLUSTRATION\
│   ├── ANIMATED\        ← {Blooming Flowers, Dorothy, New Year, Rogz Pet Gear, Star, Throwball}
│   ├── ILLUSTRATED\     ← {Pink Moon, Plugged In, Rogz Characters, Something Fishy, Space Inspectors}
│   ├── DRAWN\           ← becomes "Angus" project
│   └── PAINTED\         ← becomes "Lexi" project
├── BRANDING\
│   ├── FOOD LABELS\
│   ├── LOGO DESIGN\
│   ├── TEXTILE DESIGN\  ← {Fancy Dress 2018, Fancy Dress 2019, Small Dog}
│   └── LAYOUT + SIGNAGE\ ← {Triumph, Food Lover's Market, Food Lover's Market Signage}
├── DIGITAL\
│   ├── CONTENT WRITING\
│   ├── SOCIAL MEDIA\
│   ├── VIDEO EDITING\
│   └── WEBSITE LAYOUT\
├── Site Fonts & Colours\
├── Updated Logo Gif.gif
└── Website Update.txt   ← Linda's original Update 2 brief
```

---

## 6. `index.html` anatomy

**Total: 1,925 lines.** Three top-level sections inside the `<html>`:

### `<head>` (lines 1–73)
- Standard meta + viewport
- **SEO block** (lines 9–37): description, keywords, theme-color, canonical, OG, Twitter card, favicon (uses `logo.gif`)
- **Schema.org Person JSON-LD** (lines 39–53)
- **Google Fonts preconnect + import** (lines 55–57): Fredoka 700 + Nunito 400-900
- **Custom @font-face block** (lines 60–73): Narnia (TTF+OTF), Barlow ExtraBold

### `<style>` (lines 75–1184)
Organised by section, each delimited with a `/* ============ */` banner. Approximate line ranges:

| Line | Section | Notes |
|---|---|---|
| 77 | Reset & CSS variables | `:root` defines `--navy`, `--navy2`, `--lime`, `--pink`, `--ink`, `--white`, `--fish` |
| 128 | Page switch system | `.page { display:none }`, `.page.active { display:flex }` |
| 139 | Shared buttons | `.btn-lime`, `.btn-pink` |
| 184 | Page header | `.site-header`, `.header-logo`, `.header-nav` |
| 243 | Home page | `#home`, `.home-svg`, `.home-video`, `.home-vignette`, `.home-stars`, `.wordmark`, `.home-tagline`, `.home-btn-*` |
| 379 | Work page | `#work`, `.work-body`, `.work-heading`, `.filter-pill`, `.project-grid`, `.project-tile`, `.tile-img`, `.tile-pink-overlay`, `.tile-label`, `.work-footer` |
| 554 | About/Contact page | `#about`, `.about-body`, `.about-badge`, `.about-hello`, `.about-bio`, `.about-email`, `.photo-grid`, `.social-bar`, `.about-footer` |
| 689 | Modal | `.modal-overlay`, `.modal-card`, `.modal-close`, `.modal-title`, `.modal-desc`, `.modal-grid` (old), `.modal-text-section`, `.modal-gallery-section`, `.gallery-scroll`, `.gallery-counter`, lightbox |
| 924 | Responsive | `@media (max-width:700px)` + `(max-width:440px)` |
| 942 | Typography | Narnia / Barlow EB / Arial Rounded assignments |
| 973 | Hero logo | `.hero-logo { max-width: 1200px; }` (Update 2) |
| 986 | Header logo | Transparent override |
| 1001 | Filter pills | No-border override |
| 1015 | Work footer redesign | Dark navy, column flex, socials gap |
| 1042 | Scroll-to-top | Floating bottom-right pink (Update 2) |
| 1066 | Project modal redesign | Full-dark layout, text + horizontal gallery |
| 1184 | **Update 2 overrides** | All Update 2 visual changes appended last → win source-order specificity. Includes hidden stars, hidden tile overlay, pink HELLO, white contact bg, resume page styling |

### `<body>` (lines 1186–1822)

```
1188   skip-link
1193   <section class="page active" id="home">     ─ Home page
1413   </section>
1418   <section class="page" id="work">             ─ Work page (12 project tiles)
1561   </section>
1566   <section class="page" id="about">            ─ Contact page
1678   </section>
1684   <section class="page" id="resume">           ─ Resume page (NEW in Update 2)
1786   </section>
1796   <button id="scrollToTopBtn">                  ─ Floating scroll-to-top
1798   <div class="modal-overlay" id="modalOverlay"> ─ Project modal
1818   <div class="lightbox" id="lightbox">          ─ Fullscreen image viewer
```

### `<script>` (lines 1824–1922)

| Line | Function / Block | Purpose |
|---|---|---|
| 1830 | `showPage(id)` | Hide all `.page` sections, show the one with this id, scroll to top |
| 1837 | IIFE `addStars()` | Generates twinkling stars in `#starsContainer`. **Currently hidden via CSS** (Update 2) — IIFE still runs harmlessly |
| 1857 | Filter pill `click` handler | Sets `.active` on clicked pill, hides/shows tiles based on `data-category` |
| 1869 | `const PROJECTS = { ... }` | Project metadata object — **12 entries currently**, 25 after Update 2 Part 2. See section 9 |
| 1895 | `openModal(key)` | Looks up `PROJECTS[key]`, populates text section, probes images sequentially, builds horizontal gallery |
| 1959 | `probeImage(folder, num, exts)` | Tries `01.jpg`, `01.png`, `01.gif`, `01.jpeg` in turn until one loads. Returns URL or null |
| 1976 | `closeModal()` | Hides modal, restores body scroll, returns focus |
| 1985 | Backdrop click handler | Close modal when user clicks the overlay (not the card) |
| 1992 | `openPortfolioModal()` | **Currently unused** (Portfolio button removed in Update 2) but kept for safety |
| 2008 | Scroll-to-top IIFE | Shows/hides button when `window.scrollY > 300`, smooth-scrolls on click |
| 2020 | `openLightbox(images, idx)` | Opens fullscreen image viewer |
| 2031 | `_renderLightboxFrame()` | Updates lightbox image src + counter |
| 2038 | `stepLightbox(dir)` | Prev/next navigation |
| 2044 | `closeLightbox()` | |
| 2050 | `lightboxBgClick(e)` | Close only when clicking backdrop, not buttons or image |
| 2056 | Touch swipe IIFE | Touch-start/end → swipe left/right = stepLightbox |
| 2066 | Keyboard `keydown` handler | Escape closes modal/lightbox, arrow keys step lightbox |
| 2078 | Modal trigger tracking | Captures which tile opened the modal so focus returns on close |
| 2084 | `DOMContentLoaded` | Adds `role=button`, `tabindex=0`, aria-label to tiles; toggles `.using-keyboard` body class for focus rings |

---

## 7. Design system (current)

### Colours

```css
:root {
  --navy:  #06102e;   /* primary dark background (Home, Work footer, Modal) */
  --navy2: #0d1f5c;   /* panel variant (header borders) */
  --lime:  #c7ff3e;   /* original lime (still in :root for buttons) */
  --pink:  #ff3d96;   /* original pink (still in :root for buttons) */
  --ink:   #0e1729;   /* dark text */
  --white: #ffffff;
  --fish:  #0a1540;   /* legacy, unused */
}
```

**Update 2 introduced two refined hex values used in overrides only:**
- `#d9ff76` — refined lime (Narnia heading accent)
- `#fe2786` — refined pink (Barlow accents, CTAs, ALL WORK heading, HELLO heading, scroll button)
- `#143465` — dark navy for body text on white backgrounds

### Typography

| Family | Usage | Where |
|---|---|---|
| **Narnia** (custom TTF/OTF) | Display headings | `.wordmark`, `.wordmark-sub`, `.work-heading`, `.about-hello`, `.modal-title`, `.resume-heading` |
| **Barlow ExtraBold** (custom TTF) | Sub-headings, labels, pills | `.filter-pill`, `.tile-label`, `.work-hint`, `.work-intro`, `.modal-role`, `.resume-sub`, `.resume-section-title`, `.resume-skill-tag` |
| **Arial Rounded MT Bold** (system) | Body | `body`, `p`, `.about-bio`, `.home-tagline`, `.modal-desc` |
| **Fredoka 700** (Google Fonts) | Fallback for Narnia | All Narnia selectors as `'Narnia', 'Fredoka', sans-serif` |
| **Nunito** (Google Fonts) | Fallback for Arial Rounded | All body selectors as `'Arial Rounded MT Bold', ..., 'Nunito', Arial, sans-serif` |

⚠️ **Design feedback flagged:** Too many type voices. Visual revamp brief (`OPEN_DESIGN_BRIEF.md`) recommends collapsing to max 2 families.

### Component primitives

| CSS class | Purpose |
|---|---|
| `.btn-lime` | Lime-outline button (Home CTAs) |
| `.btn-pink` | Solid pink button (Contact, RESUME, GET IN TOUCH) |
| `.site-header` | Top bar on Work + Contact + Resume pages |
| `.header-logo` | 48px logo container (transparent, no border) |
| `.header-nav-link` | Text nav button in header |
| `.filter-pill` | Pill-shaped filter chip (Work page) |
| `.project-tile` | Square tile in Work grid |
| `.tile-img` | Image inside tile (`object-fit: cover`) |
| `.tile-label` | Bottom-aligned label with gradient background |
| `.work-footer` | Dark-navy footer (Work, Contact, Resume) with button + socials |
| `.modal-overlay` / `.modal-card` | Fullscreen modal with text + scrollable gallery |
| `.gallery-scroll` | Horizontal snap-scroll image strip |
| `.lightbox` | Fullscreen image viewer with prev/next |

---

## 8. Page-by-page walkthrough

### Home (`#home`, lines 1193–1413)

**Layers (z-index ascending):**
1. SVG scenic fallback (sky gradient, hills, windmill, rainbow, river) — z-index 1
2. MP4 hero video (`videos/hero.mp4`) overlaid — z-index 1
3. Vignette gradient — z-index 2
4. ~~Twinkling stars~~ — hidden via Update 2 CSS, JS still runs
5. Centred logo PNG (`.hero-logo`, max-width 1200px) — z-index 5
6. Contact button (top-centre) and "See My Work" button (bottom-centre) — z-index 10

**Critical:** the hero PNG (`images/lindmill-logo.png`) has an `onerror` fallback to a wordmark div with "LINDMILL DESIGNS" Narnia text — so if the PNG fails, the page still shows branding.

### Work (`#work`, lines 1418–1561)

```
[header.site-header]   logo + Contact button
[work-body]
  [h1.work-heading]    "ALL WORK" (pink, Narnia)
  [p.work-intro]       Linda's tagline
  [p.work-hint]        "*Select a project..."
  [div.filter-bar]     5 .filter-pill buttons: All / Animation / Illustration / Digital / Branding
  [div.project-grid]   12 .project-tile divs (becomes 25 after Update 2 Part 2)
[div.work-footer]      GET IN TOUCH button + Instagram/LinkedIn/Email icons (Behance removed)
```

Each `.project-tile` carries `data-category="<filter>"` and `onclick="openModal('<key>')"`. The filter pill JS just toggles `display` on tiles whose `data-category` doesn't match.

### Contact / About (`#about`, lines 1566–1678)

White background (Update 2). Centred column up to 680px wide.

```
[header.site-header]    logo + Work nav link
[about-body]
  [div.about-badge]     88px logo gif (transparent)
  [h2.about-hello]      "HELLO!" (pink)
  [p.about-bio] × 2     Linda's bio paragraphs (dark navy text on white)
  [p.about-contact-line]
  [a.about-email]       thelindamiller@gmail.com (pink, large)
  [div.photo-grid]      2 × portrait JPGs (Linda + dog, Linda outdoors)
  [div.social-bar]      Instagram / LinkedIn / Email / Behance icons
[div.work-footer]       RESUME button → showPage('resume') + 3 social icons (no Behance)
```

### Resume (`#resume`, lines 1684–1786)

New in Update 2. White bg, navy text, pink section headings. Content sourced from Linda's existing Carrd page.

```
[header.site-header]      logo + Contact + Work nav
[div.resume-body]
  [h1.resume-heading]     "Resume" (pink, Narnia)
  [p.resume-sub]          "Linda Miller — Designer, Illustrator & Motion Artist"
  Sections (each with .resume-section-title + .resume-item blocks):
    - Profile
    - Experience (Freelance + In-House)
    - Skills (Design / Writing / Software tags)
    - Contact (email, IG, LinkedIn)
[div.work-footer]         GET IN TOUCH button → showPage('about')
```

---

## 9. The `PROJECTS` object

The single source of truth for what Work tiles open. Lives at line ~1869 in `index.html`.

### Schema

```js
'<slug>': {
  title:    'Project Title',           // shown in modal h2
  role:     'Linda's role',            // shown under desc as "My Role: ..."
  desc:     'One-paragraph description', // shown in modal
  folder:   'images/<slug>',           // where probeImage() looks
  thumb:    'images/thumbnails/0X.jpg', // fallback if no gallery images
  maxCount: 50,                        // probeImage tries 01..maxCount
},
```

### Current 12 entries (before Update 2 Part 2)

| Key | Folder | Image count | Category |
|---|---|---|---|
| `animated` | `images/animated` | 38 | animation |
| `drawn` | `images/drawn` | 4 | illustration |
| `illustrated` | `images/illustrated` | 22 | illustration |
| `painted` | `images/painted` | 4 | illustration |
| `video-editing` | `images/video-editing` | 7 | digital |
| `website-layout` | `images/website-layout` | 4 | digital |
| `social-media` | `images/social-media` | 36 | digital |
| `content-writing` | `images/content-writing` | 16 | digital |
| `food-labels` | `images/food-labels` | 19 | branding |
| `logo-design` | `images/logo-design` | 17 | branding |
| `textile-design` | `images/textile-design` | 18 | branding |
| `layout` | `images/layout` | 16 | branding |

**Total: 201 portfolio images.** All numbered sequentially (`01.jpg`, `02.jpg`, etc.) within each folder. Extension mixed — `probeImage()` tries `.jpg` → `.png` → `.gif` → `.jpeg` per slot.

### How probing works

```js
// pseudo-code
for (let i = 1; i <= maxCount; i++) {
  for (let ext of ['jpg', 'png', 'gif', 'jpeg']) {
    if (image_loads(`${folder}/${pad(i,2)}.${ext}`)) {
      collect this src;
      break;
    }
  }
}
```

So for `maxCount: 50` and a folder with 38 images, the function probes 50 slots × ~4 extensions = up to 200 HEAD requests. **This is wasteful and a known perf issue** (task #16). For Update 2 Part 2 the new sub-project folders have 2-12 images each, so set `maxCount` tighter (e.g. 10 or 15).

---

## 10. Project history (chronological)

| Date | SHA | Title | What |
|---|---|---|---|
| 2026-05-22 | `7d0a048` | Initial commit | Bare scaffold |
| 2026-05-22 | `43a5c9b` | Linda's assets + restructure | Imported assets, set up 12 categories |
| 2026-05-22 | `3f66a47` | First 5 real galleries + home tweaks | |
| 2026-05-22 | `0c35125` | Drop "coming soon" message | |
| 2026-05-22 | `929ad46` | Populate all 12 galleries (201 images) | |
| 2026-05-23 | `80cea10` | DESIGN_BRIEF.md handoff doc | |
| 2026-05-24 | `080117d` | Lightbox prev/next + lazy loading + SEO files + HOW-TO-PUBLISH refresh | Tasks 15, 17, 20 |
| 2026-05-24 | `a2457b2` | CHECKPOINT.md | Recovery guide for stable state |
| 2026-05-24 | `bd16f84` | **Tasks 1–9 redesign** | Hero logo PNG, typography (Narnia/Barlow), nav, filters, modal, footer |
| 2026-05-24 | `ddfa242` | Polish | About-badge transparent, new contact photos, GIF fix |
| 2026-05-24 | `47a1573` | ❌ **Failed full Update 2** | Tried hero+stars+logo+pink+overlay+25 tiles+contact+resume all at once. Broke site (fonts wrong, tiles wouldn't open, console errors) |
| 2026-05-24 | `7c2e33f` | Revert | Roll-back of `47a1573` |
| 2026-05-24 | `1eb170f` | **Update 2 Part 1 (visuals only)** | Safe re-ship of just the visual changes, no project restructure |
| 2026-05-24 | `2c13e1c` | Add Cowork handoff + gitignore tidy | |

**Key lesson from `47a1573` failure:** when shipping many changes at once, prefer **CSS overrides at end of stylesheet** over editing existing rules. The full Update 2 attempt rewrote the PROJECTS object, replaced all 12 tiles, removed JS, and touched typography selectors simultaneously — multiple failure modes compounded. The successful re-ship (`1eb170f`) used hide-don't-delete + scoped overrides + appended-last CSS and worked first try.

---

## 11. Update 2 status

### Part 1 — SHIPPED (`1eb170f`)

✅ Hero logo doubled (600px → 1200px max-width)
✅ Decorative stars hidden via CSS (`.home-stars { display:none !important }`) — JS IIFE still runs harmlessly
✅ Header logo gif swapped: `logo.gif` → `updated-logo.gif` (3 locations: Work header, Contact header, About badge)
✅ ALL WORK heading → pink `#fe2786`
✅ Pink thumbnail overlay hidden via CSS
✅ Scroll-to-top button → pink
✅ Work footer: Behance removed, 28px gap added above socials
✅ Contact page → white bg, dark navy text (scoped to `#about`)
✅ HELLO! heading → pink
✅ Contact footer replaced with work-style footer + RESUME button
✅ **New Resume page** with real CV content from Linda's Carrd (Anglo Windows, Timothy Oulton, RTGT, Rogz, Root 360, Hamiltons, Triumph, skills grouped by Design/Writing/Software)

### Part 2 — PENDING (this is the next priority)

🟡 **Split 4 multi-projects into 17 sub-projects** + rename 2:

| Old project (1 tile) | New (multiple tiles) |
|---|---|
| Animated | Blooming Flowers, Dorothy, New Year, Rogz, Star, Throwball |
| Illustrated | Pink Moon, Plugged In, Rogz Characters, Something Fishy, Space Inspectors |
| Drawn (rename) | **Angus** |
| Painted (rename) | **Lexi** |
| Textile Design | Fancy Dress 2018, Fancy Dress 2019, Small Dog Range |
| Layout & Signage | Triumph Layout, Food Lover's Layout, Food Lover's Signage |

→ Grid goes from **12 tiles to 25**.

**Source assets** for the splits are all in the master asset folder (see section 5). Each sub-project already has its own subfolder there — just needs copying + numeric renaming into `images/<sub-project-slug>/`.

**Sub-project image counts (planned):**

| Sub-project | Source | Files |
|---|---|---|
| blooming-flowers | ANIMATED/Blooming Flowers | 3 |
| dorothy | ANIMATED/Dorothy | 5 |
| new-year | ANIMATED/New Year | 3 |
| rogz-animated | ANIMATED/Rogz Pet Gear | 10 |
| star | ANIMATED/Star | 7 (jpgs only, mp4s skipped) |
| throwball | ANIMATED/Throwball | 10 |
| pink-moon | ILLUSTRATED/Pink Moon | 4 |
| plugged-in | ILLUSTRATED/Plugged In | 2 |
| rogz-characters | ILLUSTRATED/Rogz Characters | 10 |
| something-fishy | ILLUSTRATED/Something Fishy | 5 |
| space-inspectors | ILLUSTRATED/Space Inspectors | 4 |
| angus | DRAWN (existing) | 4 |
| lexi | PAINTED (existing) | 4 |
| fancy-dress-2018 | TEXTILE DESIGN/Fancy Dress 2018 | 6 |
| fancy-dress-2019 | TEXTILE DESIGN/Fancy Dress 2019 | 7 |
| small-dog-range | TEXTILE DESIGN/Small Dog | 5 |
| triumph-layout | LAYOUT + SIGNAGE/Triumph | 12 |
| food-lovers-layout | LAYOUT + SIGNAGE/Food Lover's Market | 4 |
| food-lovers-signage | LAYOUT + SIGNAGE/Food Lover's Market Signage | 6 |

**Implementation outline:**
1. Copy assets via PowerShell into `images/<sub-project-slug>/01.jpg`, `02.jpg`, etc. (PowerShell script for this is in chat history from the failed `47a1573` attempt — it worked, it was only the HTML/JS that broke.)
2. Replace the 12 `.project-tile` divs in the project grid with 25 new tiles (preserving the 4 filter `data-category` values)
3. Replace `PROJECTS` object with 25 entries matching the new keys
4. Test each tile click in the browser **before committing**
5. Commit as single atomic change

---

## 12. Outstanding work (priority ranked)

| # | Task | Priority | Notes |
|---|---|---|---|
| 1 | Update 2 Part 2 — project restructure | 🔴 HIGH | Linda asked for it, blocks design revamp |
| 2 | Real social URLs | 🟡 MED | Resume page already uses `@thelindamiller` for IG and `thelindamiller` for LinkedIn — apply same to footer socials throughout. Behance: no profile yet |
| 3 | Netlify deploy | 🟡 MED | Drag site folder onto `app.netlify.com/drop`. Auto-deploy from GitHub is a bonus |
| 4 | Custom domain | 🟢 LOW | Linda's call — `lindmilldesigns.com` ~R200/yr at Namecheap |
| 5 | Image compression audit | 🟢 LOW | `01.gif` is 7 MB, `linda-1.jpg` 2.19 MB. Shrink before deploy for mobile load times |
| 6 | Logo GIF transparency | 🟢 LOW | `updated-logo.gif` likely has white bg — visible on About badge. Linda needs to re-export with transparent bg |
| 7 | Visual revamp (per `OPEN_DESIGN_BRIEF.md`) | 🟢 LOW (future) | Design agent engagement to follow Update 2 Part 2 |
| 8 | Performance optimisation | 🟢 LOW | `probeImage()` brute-force probing is wasteful. Consider a `gallery: [...]` array in PROJECTS so we know up-front which files exist |
| 9 | Sort larger galleries by sub-group | ⚪ deprioritised | Becomes moot after Update 2 Part 2 splits |

---

## 13. Known issues / gotchas

| Issue | Where | Impact | Fix |
|---|---|---|---|
| `addStars` IIFE runs but appends to a hidden div | `<script>` line 1837 | None functional, slight CPU on load | Could remove the IIFE — but the CSS hide is safer (no JS edit risk) |
| `openPortfolioModal()` is defined but never called | `<script>` line 1992 | None | Dead code, harmless. Remove if cleaning up |
| Image probing makes ~200 requests for a large `maxCount` | `probeImage()` | Slow first-modal-open | Replace `maxCount` with explicit `gallery: ['01.jpg', '02.jpg', ...]` list per project |
| Carrd-site DNS / domain | external | Linda's old Carrd is still live at `lindmilldesign.carrd.co` — keep it until Netlify deploy is verified | |
| Resume CV content drift | `#resume` | If Linda updates her Carrd CV, the resume page goes stale | Worth a periodic re-fetch from `https://lindmilldesign.carrd.co/#scrollpoint06` |
| Some thumbnails are PNG-flat against pink overlay | `images/thumbnails/` | After Update 2 the pink overlay is hidden so this doesn't matter, but original thumbnails were colour-graded for pink overlay | No fix needed |
| LF/CRLF warning when committing on Windows | git | Cosmetic | git auto-converts; ignore |

---

## 14. Deployment plan

### Netlify (free tier)

**Drag-and-drop method** (simplest, works today):
1. Open `https://app.netlify.com/drop`
2. Drag the entire `lindmilldesigns-site` folder onto the page
3. Netlify returns a `*.netlify.app` URL (e.g. `lindmill-designs.netlify.app`)
4. Done. HTTPS, CDN, global edge — all included.

**GitHub auto-deploy method** (better long-term):
1. In Netlify dashboard → "Add new site" → "Import from Git"
2. Authorise GitHub → pick `angusm99/lindmill-designs-site`
3. Build command: *(leave empty)* — there's no build step
4. Publish directory: `/` (repo root)
5. Deploy. Every `git push origin main` now triggers a fresh deploy.

### Custom domain (later)

1. Buy `lindmilldesigns.com` at Namecheap (~R200/yr)
2. In Netlify: site settings → "Domain management" → "Add custom domain"
3. Netlify gives DNS records. Either:
   - Point Namecheap nameservers to Netlify's DNS (easiest, full delegation)
   - Or add a `CNAME` from `www.lindmilldesigns.com` → `*.netlify.app` at Namecheap
4. Netlify auto-provisions Let's Encrypt cert. Done.

---

## 15. Related docs in repo

| File | Purpose | Audience |
|---|---|---|
| `README.md` | Repo overview | Anyone on GitHub |
| `CHECKPOINT.md` | Recovery instructions for the 2026-05-24 stable state (Tasks 15-17-20) | Future maintainer |
| `COWORK_HANDOFF.md` | Session brief for Cowork after Update 2 Part 1 | Next Cowork agent |
| `OPEN_DESIGN_BRIEF.md` | Visual revamp brief for design agent | Design agent / human designer |
| `DESIGN_BRIEF.md` | Earlier brief from Claude Design handoff | Historical reference |
| `CODEX_PROJECT_HANDOFF.md` | **This document** — complete project overview | Codex, future Claude sessions, new contributors |
| `HOW-TO-PUBLISH.txt` | Linda-friendly publishing instructions | Linda |

---

## 16. Conventions & naming

- **Project slugs** — lowercase, hyphenated: `blooming-flowers`, not `BloomingFlowers` or `blooming_flowers`
- **Image filenames within a project folder** — zero-padded sequential: `01.jpg`, `02.gif`, `03.png`. Extension determined by source; `probeImage()` figures it out
- **CSS section banners** — `/* ============== */` lines delimit logical sections inside `<style>`
- **HTML section banners** — `<!-- ============== -->` for page sections
- **Update 2 CSS overrides** are all in one block at the END of `<style>` (line ~1184) so they win source-order specificity over earlier rules without needing more `!important`s than necessary
- **Git commit messages** — start with a verb, mention which area changed. Co-Authored-By trailer for AI-assisted commits
- **Page IDs** — `#home`, `#work`, `#about`, `#resume`. `showPage('id')` switches between them
- **Data attributes** — `data-category` on tiles, `data-filter` on pills. Matching string → tile visible

---

## 17. Setup checklist for a new agent / contributor

- [ ] Clone the repo: `git clone https://github.com/angusm99/lindmill-designs-site.git`
- [ ] Read this doc (`CODEX_PROJECT_HANDOFF.md`) end-to-end
- [ ] Skim `index.html` — it's all in one file, use the line-range table in section 6
- [ ] Run `python -m http.server 5500` from the repo root and open `http://localhost:5500`
- [ ] Click around: Home → See My Work → click a tile → modal opens → click image → lightbox → close → back to Work → filter pills work → Contact → RESUME → back
- [ ] Read `COWORK_HANDOFF.md` for current session state and immediate next steps
- [ ] Read `OPEN_DESIGN_BRIEF.md` if doing any visual work (separate engagement, not Codex's job)
- [ ] Check git log (`git log --oneline -20`) to understand recent history
- [ ] Top priority is Update 2 Part 2 — see section 11 above

---

## 18. Contacts & access

| | |
|---|---|
| **Linda Miller (client)** | thelindamiller@gmail.com · @thelindamiller (IG) · linkedin.com/in/thelindamiller |
| **Angus (dev)** | angusm99@gmail.com · github.com/angusm99 |
| **GitHub repo** | `angusm99/lindmill-designs-site` (public, branch `main`) |
| **Carrd source site** | `https://lindmilldesign.carrd.co` (the one we're replacing) |
| **Asset master folder** | `C:\Users\User\CLAUDE\LINDA MILLER WEBSITE\LINDMILL ASSET FOLDER-...` (local, not in repo) |
| **Local dev server** | `http://localhost:5500` (Angus's machine) · `http://192.168.1.106:5500` (LAN) |
| **Planned production URL** | `https://lindmilldesigns.com` (domain not yet purchased) |
| **Planned Netlify URL** | `https://lindmill-designs.netlify.app` (site not yet deployed) |

---

*End of handoff. If anything is unclear, the next-best source of truth is `index.html` itself — the whole site is in that one file and is heavily commented.*
