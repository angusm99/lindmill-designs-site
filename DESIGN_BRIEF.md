# Lindmill Designs — Design Brief (v2, built)

This is the **current, built** spec for Linda Miller's portfolio site. It supersedes the original `PROJECT_DOCUMENTATION.md` artifact spec. Paste into Claude Design (or any AI design tool) to iterate further.

Repo: https://github.com/angusm99/lindmill-designs-site
Stack: single-file `index.html` + CSS + vanilla JS. No build step.

---

## TL;DR — what changed from the original spec

| Original spec said | What we built | Why |
|---|---|---|
| Hero is full-page MP4 video only | MP4 video **with animated SVG scenic scene as fallback** | Best of both — distinctive backup if video blocked/loading; SVG matches Linda's whimsical brand |
| 6 filter categories (Motion / Branding / Product / Digital / Textile + All) | **4 filters: All / Motion + Illustration / Digital / Branding** | Matches Linda's actual folder organisation (her 3 disciplines) |
| 16 project tiles | **12 project tiles** | Matches Linda's "ALL WORK THUMBNAILS/" of exactly 12 categories |
| Fish-scale decorative borders on Work + Contact panels | Dropped — clean white panel, navy header strip | Fish-scale was too busy with the modal-heavy work grid; cleaner = better hierarchy |
| Tweaks panel (React, runtime CSS variable editor) | Dropped | Single-author site, no need for end-user theming |
| Hard-coded image counts per category | **Smart probe** — modal probes 01..50 across `.jpg/.png/.gif/.jpeg`, shows whatever exists | Lets Linda add/remove images without touching code |
| Modal: empty galleries show grid of placeholders | **Single-image hero** of the category thumbnail when folder is empty | Looks intentional rather than "broken" |

---

## Visual Design System (LOCKED — do not change without asking)

### Colour tokens
```css
--navy:   #06102e   /* dark background, hero, header */
--navy2:  #0d1f5c   /* panel variant, badge bg */
--lime:   #c7ff3e   /* wordmark, headings, button outlines, accents */
--pink:   #ff3d96   /* primary CTA, hover overlays, dividers */
--ink:    #0e1729   /* text on light backgrounds */
--white:  #ffffff   /* work panel bg */
```

### Typography
- **Fredoka 700** — wordmark, headings, button labels, filter pills, modal titles. Google Fonts.
- **Nunito 400/600/800/900** — body copy, bio, descriptions. Google Fonts.

### Buttons (two variants only)
- `.btn-lime` — outline, lime border + lime text → fills lime on hover, text goes navy
- `.btn-pink` — solid pink fill + white text → darkens on hover

Both: Fredoka 700, uppercase, letter-spacing 0.08em, border-radius 6px.

---

## Page Structure (3 pages, page-switch model, no scroll-spy)

JS function `showPage(id)` swaps `.page.active`. Pages: `home`, `work`, `about`.

### 1. Home (`#home`)
- Full-viewport (`100svh`), navy background
- Layer stack (z-index ascending):
  1. **SVG scenic scene** — sky gradient, twinkling stars, sparkles, hills, rainbow, windmill (animated blades), river waves
  2. **MP4 video** (`videos/hero.mp4`) — autoplays muted, covers SVG; SVG shows through if video fails
  3. **Vignette** — radial gradient navy 0.55→0.72 for text contrast
  4. **Twinkling sparkle stars** — 10 procedural HTML stars with CSS opacity animations
  5. **Overlay content** (centred): LINDMILL wordmark, DESIGNS subline, pink divider (120px wide), tagline "Motion Design + Visual Storytelling"
- **Contact button**: top-centre, lime outline
- **See My Work button**: bottom-centre, lime outline (no arrow)

### 2. Work (`#work`)
- Navy header strip: logo badge (52px, navy2 rounded square, animated GIF) on left, nav (Home + pink Contact button) on right
- White panel below:
  - "ALL WORK" heading, Fredoka 700, navy, `clamp(2.8rem, 9vw, 5.5rem)`
  - Intro paragraph (1 line, max-width 640px)
  - Hint: italic pink "Select a project to view the full gallery."
  - 4 **filter pills**: All / Motion + Illustration / Digital / Branding — navy outline, pink fill on active/hover
  - **4-column project grid** (2-col on <700px), 8px gap, 1:1 tiles
- Navy footer with Contact + Home buttons

### 3. About (`#about`)
- Same navy header
- Centred body (max-width 680px), navy background
- 88px rounded badge with animated logo GIF
- "HELLO!" heading, Fredoka 700, lime, `clamp(3.5rem, 13vw, 6.5rem)`
- Bio: 2 paragraphs of body copy
- Email line + email link (Fredoka, pink, 1.35rem)
- 2-col photo grid (4:3 aspect, 10px gap): `linda-1.jpg`, `linda-2.jpg`
- Social bar: Instagram / LinkedIn / Email / Behance SVG icons
- Footer with See My Work + Home buttons

---

## Project Tile (the workhorse component)

```
.project-tile (1:1, rounded, coloured fallback bg by nth-child)
  ├── .tile-img         (cover-fit thumbnail, scales 1.06 on hover)
  ├── .tile-pink-overlay (pink mix-blend-multiply, opacity 0.5 → 0.22 on hover)
  └── .tile-label       (bottom-left, lime Fredoka uppercase, navy gradient backdrop)
```

Click → `openModal('<category-key>')`.

---

## Modal & Lightbox

### Modal
- Full-screen navy 0.93 overlay, scrollable
- White card max-width 760px, padding 2.2rem 2rem 2rem, radius 14px
- Floating pink close button (top-right, -15px offset, 42px circle)
- Title (Fredoka 2rem, navy) + description (#666 0.9rem)
- **Modal grid**: `repeat(auto-fill, minmax(150px, 1fr))`, 8px gap, 1:1 items

### Smart gallery loader
- On open, probes `images/<folder>/01.jpg`, `02.jpg`, … up to `maxCount: 50`, also tries `.png`, `.gif`, `.jpeg` at each index
- All found images render in the grid
- **If none found** → renders single full-width hero image of the category thumbnail (no "coming soon" text — looks intentional)

### Lightbox
- Click any image → fullscreen black overlay with the image, click anywhere to close
- ESC key closes both modal and lightbox

---

## The 12 Categories (Linda's actual organisation)

Each tile uses thumbnail `images/thumbnails/0N.{jpg|gif}` (numbered 01–12 matching her source folder).

| # | Tile label | Filter group | Image folder | Current count |
|---|---|---|---|---|
| 1 | Animated | Motion + Illustration | `images/animated/` | 38 |
| 2 | Drawn | Motion + Illustration | `images/drawn/` | 4 |
| 3 | Illustrated | Motion + Illustration | `images/illustrated/` | 22 |
| 4 | Painted | Motion + Illustration | `images/painted/` | 4 |
| 5 | Video Editing | Digital | `images/video-editing/` | 7 |
| 6 | Website Layout | Digital | `images/website-layout/` | 4 |
| 7 | Social Media | Digital | `images/social-media/` | 36 |
| 8 | Content Writing | Digital | `images/content-writing/` | 16 |
| 9 | Food Label Design | Branding | `images/food-labels/` | 19 |
| 10 | Logo Design | Branding | `images/logo-design/` | 17 |
| 11 | Textile Design | Branding | `images/textile-design/` | 18 |
| 12 | Layout + Signage | Branding | `images/layout/` | 16 |

**Total: 201 gallery images** (excluding hero video, logo, contact photos).

---

## Asset Conventions

```
images/
  logo.gif              ← animated logo badge (header, about)
  linda-1.jpg           ← bio photo 1 (Linda Miller portrait)
  linda-2.jpg           ← bio photo 2 (Me & Zula)
  thumbnails/
    01.gif → 12.jpg     ← one per work tile, exact mapping above
  <category-folder>/
    01.jpg, 02.jpg, …   ← natural-sorted from Linda's source folders
                          MP4s and >2000px duplicates excluded
videos/
  hero.mp4              ← home page hero video
```

---

## Responsive Behaviour

- **>700px**: 4-col project grid, filter pills full size, modals 760px wide
- **≤700px**: 2-col project grid, smaller header nav, padded content, modal full-width
- All `clamp()` typography scales from mobile to desktop natively
- 100svh used for hero (mobile-safe viewport)

---

## What I'd ask Claude Design to iterate on next

Now that the structure works and content is in, design-iteration candidates:

1. **Modal hero treatment** — currently the empty-state shows the thumbnail full-width with `max-height: 420px`. Could be more interesting — e.g. a styled "showcase" treatment with the title overlaid.
2. **Loading state** — modals fade in but the grid pops. Could add a subtle stagger animation as probed images resolve.
3. **Filter pill UX** — pills don't show counts. Could add `(38)` style counts.
4. **Lightbox** — currently just shows the image. Could add prev/next arrows + keyboard nav.
5. **About page polish** — the photo grid is functional; could be more editorial with mixed aspect ratios.
6. **Header on scroll** — Work page has long galleries; header could shrink/stick on scroll.
7. **MP4 reel handling** — Linda has MP4s (Ballustrade reel, Star colour variations) currently excluded as too heavy. A `<video>` item type in the modal grid could bring them back with `preload="none"`.
8. **OG meta tags** — site has no `og:image` / Twitter card for nice link previews. Add when domain is decided.

---

## Outstanding placeholders (replace before launch)

- Social URLs in About + footer: `https://www.instagram.com/`, `https://www.linkedin.com/`, `https://www.behance.net/`
- No custom domain yet (default would be Netlify subdomain)

---

## Files

```
lindmilldesigns-site/
├── index.html              ← all markup, CSS, JS
├── HOW-TO-PUBLISH.txt      ← Linda-friendly publishing guide
├── README.md               ← developer notes
├── DESIGN_BRIEF.md         ← this file
├── .gitignore
├── videos/hero.mp4
└── images/                 ← logo, photos, thumbnails, 12 category folders
```
