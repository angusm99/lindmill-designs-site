# Lindmill Designs — Portfolio Site

Static portfolio site for Linda Miller (Lindmill Designs) — motion designer and illustrator.

## Stack
Pure HTML / CSS / vanilla JavaScript. No build step, no dependencies. Hosted free on Netlify.

## Local preview
Open `index.html` directly in any browser (double-click), or serve with:
```
python -m http.server 5500
```
Then visit http://localhost:5500

## Deploying
Drag the project folder onto https://app.netlify.com/drop — done. See `HOW-TO-PUBLISH.txt` for the full walkthrough.

## Project structure
```
index.html            ← all markup, CSS and JS in one file
HOW-TO-PUBLISH.txt    ← non-technical publishing instructions
videos/hero.mp4       ← home page background video
images/
  ├── logo.gif        ← animated logo badge
  ├── linda-1.jpg     ← bio photo 1
  ├── linda-2.jpg     ← bio photo 2
  ├── animation/      ← 01.jpg … 08.jpg
  ├── illustration/   ← 01.jpg … 08.jpg
  ├── food-labels/    ← 01.jpg … 12.jpg
  ├── logo-design/    ← 01.jpg … 17.jpg
  ├── textile/        ← 01.jpg … 05.jpg
  ├── fancy-dress/    ← 01.jpg … 07.jpg
  ├── seafood/        ← 01.jpg … 12.jpg
  └── branding/       ← 01.jpg … 08.jpg
```

## Pages
- **Home** — animated MP4 hero with the wordmark and Contact / Work buttons. SVG scene fallback if video is blocked.
- **Work** — 12-tile project grid with category filters and modal galleries.
- **About** — bio, email, photos, social links.

## Design tokens (CSS variables)
```
--navy  #06102e   --lime  #c7ff3e   --pink  #ff3d96
```
