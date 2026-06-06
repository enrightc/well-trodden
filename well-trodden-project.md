# Well Trodden — Project Reference

## Brand

**Name:** Well Trodden
**Tagline:** No fluff. No package tours. Just the full story of trips we actually did.
**Tone:** Honest, warm, capable. Rugged but not try-hard. No waffle, no stock-photo vibes, no "discover the magic of..." copy.
**Focus:** Worldwide self-directed trips, done properly, with honest practical detail.

### What the site is

Personal itinerary site documenting real trips — not guides, not listicles, not inspiration boards. Day-by-day accounts of self-directed trips with practical detail: costs, timings, transport, honest verdicts. The kind of site you'd trust because it doesn't oversell anything.

Not package holidays. Just two people figuring it out, moving around, packing a lot in.

---

## Design

### Overall feel
- Light, clean, open — white and warm off-white backgrounds
- Photography and typography carry equal weight
- No stats, no gimmicks, no repeated taglines
- Feels like a site built by someone who actually went and did it

### Typography
- **Display / headings:** Cormorant Garamond (serif) — elegant, editorial weight
- **Body / UI:** Outfit (sans-serif) — clean, legible, modern without being sterile

### Colours
- `--paper: #F4F1EC` — warm off-white background
- `--ink: #1A1916` — near-black for headings and strong text
- `--stone: #6B6860` — mid tone for body copy and secondary text
- `--dust: #A8A49C` — muted tone for labels, regions, meta
- `--border: rgba(26,25,22,0.12)` — subtle borders throughout
- White `#ffffff` for card backgrounds

### Navigation
Fixed, transparent over hero — fades to paper background with border on scroll. Four items: Home · Trips · Map · About.

### Homepage
- Full-screen hero photo with site name and tagline centred over it
- Nav transitions from transparent (over hero) to solid on scroll
- Three equal trip cards below with photo, region, title, one-line summary, pills for duration and trip type
- Clean footer — logo left, strapline right

### Trip cards
Each card shows:
- Hero photo
- Region (small caps, muted)
- Trip title (serif)
- One-line summary (sans, light weight)
- Pills: duration, trip type

### Trip page — long/complex trips
Four sections with sticky in-page navigation:
1. Overview — where, when, how long, who it suits, honest verdict
2. The Route — map showing how it connects
3. Day by Day — chronological detail
4. Practical Info — costs, transport, booking tips

### Trip page — short/simple trips
Single flowing page — overview, what we did, practical tips in one scroll.

---

## Site structure

```
/                   Home
/trips              Trips index (filterable by region)
/trips/[slug]       Individual trip page
/map                Interactive world map
/about              About page
```

---

## Navigation

Four items, nothing more:
- Home
- Trips
- Map
- About

Trips index is filterable by region only. No activity tags — kept clean and simple.

---

## Content — trips to build

| Trip | Duration | Type | Status |
|------|----------|------|--------|
| Guatemala & Belize | 16 days | Shuttle & hire car | Notes drafted |
| Iceland | 10 days | Campervan | To write |
| Jordan | 10 days | Hire car | To write |
| Malaysia | 14 days | Train & bus | To write |
| Japan | 14 days | Rail | To write |
| European city breaks | Various | Various | To write |

---

## Tech stack

### Framework
**Astro** — content-heavy, fast, ideal for structured trip documents. Trips authored as Markdown/MDX with frontmatter for metadata.

### Content model
Each trip is a Markdown file in `src/content/trips/` with frontmatter:

```yaml
---
title: "Guatemala & Belize"
slug: "guatemala-belize"
region: "Central America"
duration: "16 days"
tripType: "Shuttle & hire car"
date: "2026-05"
summary: "Two weeks, two countries. Volcanoes to Mayan ruins to snorkelling the barrier reef."
heroImage: "/images/trips/guatemala-belize/hero.jpg"
featured: true
type: "long"   # long | short
---
```

### Suggested structure

```
well-trodden/
├── public/
│   └── images/
│       └── trips/
├── src/
│   ├── components/
│   │   ├── Nav.astro
│   │   ├── TripCard.astro
│   │   ├── TripNav.astro        ← sticky in-page nav for long trips
│   │   └── Map.astro
│   ├── content/
│   │   └── trips/
│   │       └── guatemala-belize.md
│   ├── layouts/
│   │   ├── Base.astro
│   │   ├── TripLong.astro
│   │   └── TripShort.astro
│   └── pages/
│       ├── index.astro           ← homepage
│       ├── trips/
│       │   ├── index.astro       ← trips index
│       │   └── [slug].astro      ← individual trip
│       ├── map.astro
│       └── about.astro
├── astro.config.mjs
└── package.json
```

### Map page
Interactive world map with every destination pinned. Each pin links to the relevant trip. Built with Leaflet.js or Mapbox GL — to be decided. Doubles as a portfolio piece.

### Hosting
Not yet decided. Likely Netlify or Vercel — both have excellent Astro support and free tiers.

---

## Build order

1. Set up Astro project and base layout
2. Build homepage — hero, nav, trip cards
3. Build trips index page with region filter
4. Build long trip template — Overview, Route, Day by Day, Practical Info
5. Write up Guatemala & Belize as the first full trip
6. Build short trip template
7. Build map page
8. Build about page
9. Write up remaining trips
10. Choose hosting and deploy
