# Lindmill Designs — Visual Revamp Brief

> **For:** Open Design / design agent
> **From:** Angus (developer) + Linda Miller (designer / site owner)
> **Date:** 2026-05-24

---

## TL;DR

Redesign the **visual layer** of Linda Miller's portfolio site (`lindmilldesigns.com` — Carrd replacement). The site is fully functional with all content in place; what it needs is a sharper, more distinctive design system. Linda is a motion designer + illustrator with 15+ years of brand experience — the site should *feel* like the work she makes (playful, motion-driven, brand-focused, animal-loving), not like a generic template.

**Scope:** Visual revamp only. Information architecture, content, and JavaScript behaviours stay as-is unless flagged.

---

## Project background

**Client:** Linda Miller, trading as **Lindmill Designs**
**Discipline:** Motion design · illustration · brand identity · textile design · food label design · layout & signage
**Career:** 15+ years — Triumph Lingerie, Hamiltons in Creative Co, Root 360, Rogz Pet Gear (in-house, 2011–2021), now freelance (Anglo Windows, Timothy Oulton Luxury Travel, The Really Great Teacher Co.)
**Personality:** Warm, playful, loves working with animals (her own work features them constantly). Brand-focused — she thinks in systems and stories.
**Site purpose:** Showcase the portfolio + funnel prospective clients to email.

---

## Current site

- **Live preview:** `http://192.168.1.106:5500` (local) — site folder: `C:\Users\User\Documents\CLAUDE MASTER\Lindmill Designs\lindmilldesigns-site`
- **Repo:** `angusm99/lindmill-designs-site` (branch `main`, latest commit `2c13e1c`)
- **Stack:** Single `index.html` file (~2,000 lines), inline `<style>`, inline `<script>`. Pure vanilla JS. No build step. No framework. Deploys to Netlify static hosting.

### What's already working (don't break)
- 4 pages controlled by `showPage(id)`: `#home`, `#work`, `#about` (contact), `#resume`
- Home: MP4 video hero (`videos/hero.mp4`) over an animated SVG fallback, hero PNG logo
- Work: 12 project tiles (about to split into 25 in next dev iteration — see *Project structure* below), filter pills (All / Animation / Illustration / Digital / Branding), modal with text section + horizontal snap-scroll gallery, fullscreen lightbox with prev/next/keyboard/swipe
- Contact: portrait grid, bio, email, footer with RESUME button
- Resume: pink/navy/white CV page with skill tags
- Floating scroll-to-top button
- Keyboard accessibility (focus rings, skip-link, tile Enter/Space)
- SEO meta + Open Graph + Schema.org Person

### What feels tired / under-loved
- **Typography hierarchy** is doing more than it should — Narnia + Barlow + Arial Rounded + Fredoka + Nunito are all fighting for attention. Needs editing down.
- **Motion & micro-interactions** are minimal. For a *motion designer's* site, this is the biggest miss. No page transitions, no scroll reveals, no playful hover states, no easter eggs.
- **Project tiles** are flat squares with a label. No personality. Hover does barely anything (image scales).
- **Modal experience** is functional but stark — text dropped at top, images scroll horizontally. Feels like a CMS demo, not a designer's portfolio.
- **Whitespace** is uneven. Some sections feel cramped (Work grid) while others are unscaffolded (Contact, Resume).
- **Filter pills** are pill-shaped tags. Generic.
- **Footer** is a single button + 3 icons on dark navy. Could carry more personality.
- **Mobile** works but isn't *thoughtful* — desktop layout shrunk down.

---

## The brief

### Revamp these things
1. **Establish a singular design language** — one font system (max 2 type families), one motion vocabulary, one set of UI primitives. Cut the dead weight.
2. **Make it feel like Linda made it** — leverage her actual portfolio aesthetic (illustrated, warm, animal-loving, character-driven) as the source of the design system. Don't reach for a generic creative-portfolio template.
3. **Hero moment on Home** — the video plays but the wordmark/logo doesn't have presence. Reimagine the first 5 seconds of arrival.
4. **Project tiles + grid** — these are the most-viewed surface. Hover, transition into modal, label treatment, ordering, and the grid rhythm all need work. Allow tiles to be different sizes/shapes if it serves the work.
5. **Project modal** — currently a stark block. Should feel like opening a case study. Text + gallery composition needs better hierarchy. Transitioning into and out of the modal should feel intentional (current: instant fade).
6. **Filter pills → something more interesting** — segmented control? Floating chips? Vertical sidebar? Surprise me.
7. **Contact page** — pink HELLO + bio + 2 photos + email is fine but flat. Better composition; more breathing room; possibly an illustrated/animated touch.
8. **Resume page** — currently a clean CV layout. Could lean further into Linda's branding (illustrated dividers, character marks, hand-drawn touches).
9. **Footer** — both work-footer (dark navy) and resume-footer. Currently identical. Add personality.
10. **Mobile design** — first-class, not an afterthought. The Work grid in particular needs mobile-native thinking.
11. **Motion & micro-interactions** — at least these:
    - Page transitions (showPage()) — current cut is jarring
    - Tile hover with delight (subtle, not noisy)
    - Filter pill click feedback
    - Modal open/close choreography
    - Scroll-into-view fades for project rows
    - Cursor accent on Home (if it adds, not distracts)
12. **Accessibility** — current AA-ish. Keep keyboard nav, focus rings, skip link, ARIA. Don't regress.

### Don't touch
- ❌ Information architecture (Home → Work → Contact → Resume)
- ❌ Page-switch JS (`showPage()`) and routing model
- ❌ Modal JS logic (`openModal()`, image probing, lightbox prev/next)
- ❌ Filter logic (`data-category` / `data-filter` matching)
- ❌ PROJECTS object structure (will be 25 projects after the in-flight restructure — see below)
- ❌ Single-file constraint — keep everything in `index.html`. No build step. No npm. No CSS preprocessors.
- ❌ External hosted dependencies beyond Google Fonts (the site must run from Netlify static hosting with no other origins)
- ❌ Any image asset processing — Linda's images stay as-is, JPG/GIF/PNG, in their current folders

---

## Brand direction

### Current palette (treat as starting point, not gospel)
```
--navy   #06102e   primary dark
--navy2  #0d1f5c   panel variant
--lime   #d9ff76   accent (Narnia headings)
--pink   #fe2786   accent (Barlow sub-headings, CTAs)
--white  #ffffff   contact + resume background
--ink    #143465   dark text on white
```

The pink + lime combo is *very* Linda — keep both, but feel free to introduce a tertiary accent, soft pastels for backgrounds, or a warmer off-white instead of pure `#ffffff`.

### Current typography
- **Narnia** (custom, `fonts/Narnia.ttf`) — display, headings (LINDMILL, ALL WORK, HELLO!)
- **Barlow ExtraBold** (`fonts/Barlow-ExtraBold.ttf`) — sub-headings, pills, labels
- **Arial Rounded MT Bold** (system) — body
- **Fredoka 700** + **Nunito** (Google Fonts) — fallbacks

This is too many voices. Recommend: pick one display face, one workhorse. Free to swap Narnia/Barlow for better-curated faces (open-source ones from Google Fonts or Fontshare). Custom font files are fine if open-licensed.

### Mood references
Linda's own work is the primary reference. Specifically:
- **Blooming Flowers** project — lush, illustrated, joyful
- **Rogz characters** — playful, brand-driven character work
- **Dorothy GIFs** — animated, narrative
- **Pink Moon** — warm, dreamlike colour
- **Fancy Dress 2019 textile patterns** — bold, fun, pet-focused

Adjacent reference vibes (without copying):
- Mid-century children's book illustration
- Motion-design studio sites like Buck, Golden Wolf, but Linda's solo version of that
- Personal-portfolio sites that *feel* like the maker: Stefan Sagmeister-era warmth, not Awwwards parallax

Avoid:
- Generic dark-mode "developer portfolio" aesthetic
- Brutalist over-design
- Bento grid for the sake of bento grid
- Pure black-and-white minimalism (Linda is colour-forward)

---

## Project structure (note: changing soon)

The Work page currently has **12 tiles**. A pending dev iteration (will land before any design work) splits 4 of those into sub-projects, taking the count to **25**:

| Category | Current count | After split |
|---|---|---|
| Animation | 1 (Animated) | 6 (Blooming Flowers, Dorothy, New Year, Rogz, Star, Throwball) |
| Illustration | 3 (Drawn, Illustrated, Painted) | 7 (Pink Moon, Plugged In, Rogz Characters, Something Fishy, Space Inspectors, Angus, Lexi) |
| Digital | 4 (Video Editing, Website Layout, Social Media, Content Writing) | 4 (unchanged) |
| Branding | 4 (Food Labels, Logo Design, Textile Design, Layout & Signage) | 8 (Food Labels, Logo Design, Fancy Dress 2018, Fancy Dress 2019, Small Dog Range, Triumph Layout, Food Lover's Layout, Food Lover's Signage) |

→ Design the grid system to gracefully handle **25 tiles** across 4 filter categories, not 12. Consider asymmetric/masonry layouts. Mobile likely needs vertical-rhythm thinking.

---

## Deliverables

Produce, in this order:

1. **Visual concept** — 2–3 distinct directions as reference mood boards or quick mocks (Home + Work + Project Modal screens). Show the design language, not pixel-perfect comps.
2. **Linda's feedback gate** — pause here. Linda picks one direction (or asks for a blend).
3. **Detailed mocks** for the chosen direction — every page at desktop + mobile breakpoint: Home, Work (grid + filters), Project Modal, Lightbox, Contact, Resume, Footer states, Empty/loading states.
4. **Design tokens spec** — colours, type scale, spacing scale, radii, shadows, easing curves, durations. Drop-in CSS variable values.
5. **Motion spec** — page transitions, tile hovers, modal open/close, scroll reveals. Reference easing names + durations. Storyboard or short video if helpful.
6. **Implementation handoff** — annotated mocks or a CSS patch ready to apply to `index.html`. Whoever implements (likely Claude Code) should be able to pick this up and ship without guessing.

Each deliverable should be small + reviewable; don't dump everything at once.

---

## Acceptance criteria

The revamp is done when:

- [ ] A first-time visitor on Home immediately knows Linda is a designer (not a developer, not a generic freelancer)
- [ ] The Work grid reads as a curated portfolio, not a CRUD list
- [ ] Hovering a project tile creates a small moment of delight that doesn't get annoying after the 10th hover
- [ ] Opening a project modal *feels* like opening a case study (transition + composition + scroll)
- [ ] At least one micro-interaction makes someone smile (cursor accent, hidden detail, sound, character mark — designer's call)
- [ ] Mobile experience is designed-for-mobile, not desktop-shrunk
- [ ] All 4 pages share one visual language — no page feels like it's from a different site
- [ ] Type system has max 2 families and a clean scale
- [ ] Colour palette is intentional — every colour earns its place
- [ ] All AA accessibility behaviours preserved (focus rings, skip-link, keyboard, contrast ≥ 4.5:1 for body text)
- [ ] The CSS still fits inside `index.html` (single file)
- [ ] No build step introduced
- [ ] Linda says: *"yes, that's the site I wanted."*

---

## File paths (for poking around)

```
Site folder:    C:\Users\User\Documents\CLAUDE MASTER\Lindmill Designs\lindmilldesigns-site\
Main HTML:      index.html  (everything is in here — CSS, HTML, JS)
Fonts:          fonts/Narnia.ttf, fonts/Narnia.otf, fonts/Barlow-ExtraBold.ttf
Hero video:     videos/hero.mp4
Hero logo:      images/lindmill-logo.png
Header logo:    images/updated-logo.gif
Project images: images/<project-slug>/01.jpg, 02.jpg, etc.
Thumbnails:     images/thumbnails/01.gif through 12.jpg
Contact photos: images/linda-1.jpg, images/linda-2.jpg
Carrd source:   https://lindmilldesign.carrd.co  (the site we're replacing)

Repo:           https://github.com/angusm99/lindmill-designs-site
Latest commit:  2c13e1c (run-up to Update 2 Part 2 — project restructure)

Linda's email:  thelindamiller@gmail.com
Instagram:      @thelindamiller
LinkedIn:       thelindamiller
```

---

## Open questions (please answer before starting)

1. **Direction count** — 2 directions or 3 in the initial concepts pass?
2. **Stretch budget** — are character marks / hand-illustrated UI elements in scope, or is that a separate engagement?
3. **Custom fonts vs Google Fonts** — Linda's current custom fonts (Narnia, Barlow) are licence-OK; willing to switch?
4. **Hero video** — keep as-is, or storyboard a new one? (New video is out of scope but could be flagged.)
5. **Motion library** — vanilla CSS/JS only (current stack), or are CDN-loaded libraries OK if light? (GSAP via CDN, ~30KB gzipped, is the obvious candidate — Linda's domain is motion.)

---

## Out of scope

- Logo / wordmark redesign (the `updated-logo.gif` is final)
- New copywriting (resume content + bio are signed off)
- New photography (Linda's portrait set + the 201 portfolio images stay)
- Custom illustrated assets beyond UI elements
- Backend / CMS work — site stays static
- E-commerce, blog, contact form, analytics dashboard
- Performance optimisation beyond keeping bundle reasonable

---

*Hand this brief to your design agent as-is. Everything they need to start is in this doc. Open questions in the section above should be answered first to scope the engagement.*
