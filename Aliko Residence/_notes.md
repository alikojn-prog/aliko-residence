# Aliko Residence — Working Notes

## Workflow
- **Always plan changes first** and wait for Pavlos to say **"gl"** before implementing anything.
- Present the plan clearly: what will change, where, and why.
- Only proceed after Pavlos explicitly says **"gl"** — no other shorthand or approval counts.

---

## Site Overview
Single-file website: `index.html`
Stack: HTML + CSS + vanilla JS, no build tools.

Key files:
- `index.html` — entire site
- `Logo/white.svg` — nav logo (over hero)
- `Logo/navy_blue.svg` — nav logo (scrolled / white bg)
- `Logo/flower.svg` — favicon (primary)
- `Logo/flower.png` — favicon (fallback)
- `Fonts/Chopard Regular/Chopard Regular.ttf` — title font
- `Images/Rooms/*.avif` — 9 room photos
- `Images/Penthouse/*.avif` — 15 penthouse photos
- `Images/Map/mapMobile.jpg` — static map image (mobile only)

---

## Performance Notes
- Ken Burns (hero image scale) is desktop-only — disabled on mobile via `!important` overrides
- No `will-change` on `.hero-slide` or `.hero-slide img` — any forced compositor layers caused Chrome/Opera header and stacking issues
- Opacity transitions are GPU-accelerated by browsers natively without hints
- All reveal animations, hover zoom, and Ken Burns disabled on mobile (`max-width: 960px`)
- `scroll-behavior: smooth` scoped to desktop only (`min-width: 961px`)
- Viewport `user-scalable=no` prevents browser pinch-to-zoom interfering with the map iframe
- Mobile map: static `mapMobile.jpg` image replaces iframe; tapping opens Google Maps. Styled with `1px solid rgba(255,255,255,.2)` border to match `book-platform-btn`

## Design Decisions Log
- Montserrat for body, Chopard for all headings/titles
- Navy `#060F23` — only used in About section bg + scrolled nav
- White theme for all other sections
- Nav: 3-col grid — About (left, no border) | Logo center 70px | Book Now (right)
- Hero: 5-slide crossfade, Ken Burns on desktop only
- Rooms: 1/3 sticky text | 2/3 asymmetric 3-photo grid
- Penthouse: reversed (2/3 grid | 1/3 text); mobile mirrors Rooms (text first)
- Section breaks: 6rem white dividers between Hero→Rooms and Rooms→Penthouse
- About section (#060F23): combines location + links + footer into one block
- No contact form, no inline "Book a room" buttons — Book Now in nav is sufficient
- Map: OpenStreetMap iframe on desktop (dark-filtered), static image linking to Google Maps on mobile
- Mobile: all scroll animations disabled, Ken Burns off, hover zoom off
