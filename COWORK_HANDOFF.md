# Lindmill Designs — Cowork Handoff (2026-05-24 evening)

> **Use this doc to brief Claude in Cowork on what just shipped and what's left.**
> Copy/paste the *Status snapshot* + *What's left* sections into the next Cowork session.

---

## Status snapshot

**Repo:** `angusm99/lindmill-designs-site` (branch `main`)
**Latest commit:** `1eb170f` — *"Update 2 (visuals only): hero size, pink headings, white contact, resume page"*
**Local preview:** `http://192.168.1.106:5500` (run `python -m http.server 5500 --bind 0.0.0.0` from the site folder)
**Deployed:** not yet — Netlify drag-and-drop still pending

**One-file site:** everything lives in `index.html` (~2,000 lines). Pure HTML + CSS + vanilla JS, no build step.

---

## What shipped in this session (Update 2 — Part 1 of 2)

Linda sent a second batch of changes in `LINDMILL_UPDATE_2.md`. We split the work into two commits — the **visual changes shipped tonight**, the **project restructure saved for tomorrow** (see *What's left* below).

### ✅ Home page
- Hero logo doubled (`max-width: 1200px`, was 600px)
- Decorative twinkling stars hidden (video already has stars baked in) — done via CSS only so the JS that creates them still runs harmlessly

### ✅ Work page
- Header logo swapped to `images/updated-logo.gif` (Linda's new GIF)
- **ALL WORK** heading → pink (`#fe2786`)
- Pink overlay on thumbnails removed — thumbnails show natural colour
- Scroll-to-top button → pink (was lime)
- Footer: **Behance link removed** · 28px more breathing room between GET IN TOUCH button and social icons

### ✅ Contact page
- White background (was navy)
- Body text retinted to dark navy (`#143465`) for contrast on white
- **HELLO!** heading → pink (`#fe2786`)
- Header logo + about-badge swapped to `updated-logo.gif`
- Old footer (See My Work + Portfolio buttons) replaced with **work-style dark footer**: RESUME button + social icons (Instagram, LinkedIn, Email — no Behance)

### ✅ Resume page (brand new)
- New `<section id="resume">` page — opens when RESUME button is clicked
- White background, pink section headings, navy text
- Real CV content fetched from Linda's existing Carrd page (`https://lindmilldesign.carrd.co`):
  - **Profile** — 15+ years across fashion, interiors, food/jewellery, pet brands
  - **Freelance** (April 2021–present) — Anglo Windows · Timothy Oulton · The Really Great Teacher Co.
  - **In-house** (Jan 2011–April 2021) — Rogz Pet Gear · Root 360 · Hamiltons · Triumph Lingerie
  - **Skills** grouped: Design / Writing / Software (Illustrator, Photoshop, AE, InDesign, Animate, Figma, Office)
  - **Contact** — email, Instagram, LinkedIn
- Resume page footer has its own GET IN TOUCH button → links back to Contact

---

## How we got here (failed attempt + recovery)

A first attempt at Update 2 (`47a1573`) tried to do everything at once — visual changes **and** the big project restructure. It broke the site: console errors, broken tiles, missing fonts, layout issues. We reverted it (`7c2e33f`) and reshipped only the safe visual half (`1eb170f`).

**Key safety patterns used this time** — apply these to any further edits:

1. **Hide, don't delete.** When removing the stars and pink overlay, we left the JS / HTML in place and added `display: none !important` overrides at the end of the stylesheet. Nothing for the JS to crash on.
2. **Scope new CSS.** White-background changes are written as `#about .xxx { ... !important }` so they can't leak onto Work or Home.
3. **Append overrides last.** All Update-2 CSS lives in one block at the very end of the `<style>` tag → wins specificity by source order, no need to hunt down every old rule.
4. **Don't touch the typography selectors.** The previous attempt edited `.work-heading, .about-hello, .modal-title { color: #d9ff76; }` and broke fonts. This time we just overrode `.about-hello` separately.
5. **Don't touch the PROJECTS object** unless you're doing the project split. The 12 existing project tiles + their `openModal()` keys are working — leave them alone.

---

## What's left (Update 2 — Part 2, to ship tomorrow)

**Linda's brief calls for splitting 4 multi-project tiles into 17 sub-projects and renaming 2 more. Plan: do this as a single dedicated commit AFTER confirming visuals look right.**

### Project splits
| Current tile | Split into |
|---|---|
| Animated | Blooming Flowers, Dorothy, New Year, Rogz, Star, Throwball |
| Illustrated | Pink Moon, Plugged In, Rogz Characters, Something Fishy, Space Inspectors |
| Textile Design | Fancy Dress 2018, Fancy Dress 2019, Small Dog Range |
| Layout & Signage | Triumph Layout, Food Lover's Layout, Food Lover's Signage |

### Renames
- Drawn → **Angus**
- Painted → **Lexi**

**Source assets** are all in:
`C:\Users\User\CLAUDE\LINDA MILLER WEBSITE\LINDMILL ASSET FOLDER-20260522T162626Z-3-001\LINDMILL ASSET FOLDER\`

Each sub-project already has its own subfolder there (e.g. `MOTION & ILLUSTRATION\ANIMATED\Blooming Flowers\`). The previous failed attempt successfully copied them into `images/blooming-flowers/`, `images/dorothy/`, etc. and the file counts checked out — the assets work, only the HTML/JS restructure broke things. The PowerShell copy commands are in the chat history if anyone wants to re-run them quickly.

### Implementation notes for next session
- After copying assets, update the `PROJECTS` object in `<script>` with 25 entries (12 originals minus 4 split-out + 17 new sub-projects + 2 renames). Keep `folder`, `thumb`, `maxCount`, `title`, `role`, `desc` fields.
- Update the 12 `.project-tile` divs in the project grid → 25 tiles, each pointing to its new `openModal('xxx')` key.
- The 4 categories (Animation / Illustration / Digital / Branding) stay the same — `data-category` values on each tile decide which filter pill shows it.
- Test each tile click in the browser before committing.

---

## Open follow-ups (lower priority, parked from earlier sessions)

- **Real social URLs** — Instagram / LinkedIn placeholders still link to `https://www.instagram.com/`. Get Linda's actual handles. (Resume page already uses her real `@thelindamiller` — apply that to footer socials too.)
- **Netlify deploy** — still not done. Easiest path: drag the `lindmilldesigns-site` folder onto `https://app.netlify.com/drop`.
- **Custom domain** — Linda hasn't decided. `lindmilldesigns.com` ~R200/yr at Namecheap.
- **Logo GIF transparency** — `updated-logo.gif` may still have a white background. Visible mainly on the about-badge. If Linda wants a clean blend, she'll need to export a transparent-bg GIF or PNG sequence.
- **Image compression audit** — `01.gif` is 7 MB, `linda-1.jpg` is 2.19 MB. Worth shrinking before deploy.
- **Performance optimisation** — open task #16 from earlier session.
- **Gallery sub-grouping** — task #18: sort larger galleries by sub-project (matters less now that the splits will happen anyway).

---

## Quick reference

```
Site folder:    C:\Users\User\Documents\CLAUDE MASTER\Lindmill Designs\lindmilldesigns-site
Run server:     python -m http.server 5500 --bind 0.0.0.0
Mobile preview: http://192.168.1.106:5500
Desktop:        http://localhost:5500
GitHub:         angusm99/lindmill-designs-site
Last good SHA:  1eb170f
Linda's email:  thelindamiller@gmail.com
```

---

*Generated 2026-05-24 evening at end of Update 2 — Part 1 session.*
