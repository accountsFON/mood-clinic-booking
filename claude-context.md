# Mood Clinic Landing Page - Project Context

> Last updated: 2026-03-24

## What This Project Is

A custom HTML/CSS/JS landing page for Mood Clinic (moodclinic.org), a psychiatric care practice. The page is deployed inside a WordPress Elementor HTML widget and serves as the main booking/marketing landing page with a Calendly integration for scheduling consultations.

## Tech Stack

- **Language:** HTML, CSS, JavaScript (vanilla)
- **Styling:** Tailwind CSS (CDN), inline styles, Google Fonts (Plus Jakarta Sans, Inter, Material Symbols)
- **CMS:** WordPress via Elementor HTML widget (post ID: 5967)
- **Site Management:** ManageWP (orion.managewp.com)
- **Booking:** Calendly inline widget (`calendly.com/moodclinic/20minutes`)
- **Deployment:** Pushed live via Elementor "Publish" button on moodclinic.org

## Project Structure

```
mood-clinic-landing/
└── index.html    # Full page — styles, modal, all sections, scripts
```

## How to Run

No build step. Open `index.html` in a browser to preview locally (Tailwind loads from CDN). To deploy, paste the full contents into the Elementor HTML widget on post ID 5967 and publish.

## Environment Variables

None. All external dependencies are loaded via CDN links inside `index.html`.

## Key Implementation Details

- **Full-width breakout trick:** `width:100vw; position:relative; left:50%; transform:translateX(-50%)` overrides Elementor's column width constraints so the page spans the full viewport.
- **Calendly modal:** A fixed overlay (`#mc-cal-overlay`) is toggled via `openCal()`. All booking buttons call this function. The Calendly widget loads lazily inside the modal.
- **Nav button hiding:** The theme's "Get Started" nav button is hidden on this page only using CSS selectors targeting `.elementor-button-wrapper` inside `header`, plus a JS fallback with 3 timeouts (300ms, 1s, 2.5s) for late-rendering buttons.
- **Hero top padding:** Uses `clamp(5.5rem, 12vh, 8rem)` to always clear the sticky theme nav regardless of screen size.
- **FAQ accordion:** Pure JS — `mcToggleFaq()` closes all items then opens the clicked one. Active state: white background + purple left border.
- **Image animation:** Hero image card has `rotate(2deg)` that transitions to `rotate(0deg)` on hover using inline `onmouseover/onmouseout`.
- **Font sizes are all explicit px** (not rem) to avoid dependency on the WordPress theme's root font size.

## Typography Scale

| Element | Size |
|---|---|
| Hero H1 | `clamp(3rem, 6vw, 5rem)` (48–80px) |
| Section H2 | `clamp(28px, 3vw, 36px)` |
| Card / Condition titles (H3/H4) | `22px` |
| FAQ questions | `18px` |
| Body / paragraph copy | `16px` |
| CTA Buttons | `18px` |
| Badge / label | `13px` |
| Section subtitle | `14px` |
| Insurance carrier names | `clamp(24px, 3vw, 32px)` |

## Known TODOs / Issues

- Nav button hiding relies on JS timeouts — if the theme loads its nav after 2.5s it may reappear (unlikely but possible)
- FAQ answers are static copy — may need updating to match live site FAQ content
- No analytics/tracking events on Calendly modal open

---

## Session Continuity

> This section tracks active work so a new chat can pick up where the last left off.

### Last Session (2026-03-24)

- **What was done:** Built full landing page from scratch — hero, benefits grid, insurance partners, conditions, FAQ, Calendly modal. Fixed typography to explicit px values. Hid nav "Get Started" button for this page only. Increased H1 to `clamp(3rem, 6vw, 5rem)`. Published live via Elementor.
- **Current state:** Page is live at moodclinic.org (post ID 5967). All sections working. Calendly modal opens on all booking buttons. Nav button hidden. FAQ accordion functional.
- **Active work:** None — page is published and stable.
- **Next steps:** Potentially add analytics events on Calendly open, review on mobile, add more FAQ answers
- **Blockers:** None

### Change Log

| Date | Summary |
|------|---------|
| 2026-03-24 | Created claude-context.md with full project context |
| 2026-03-24 | Increased H1 to clamp(3rem, 6vw, 5rem) |
| 2026-03-24 | Fixed all font sizes to explicit px, hid nav button, fixed hero padding |
| 2026-03-24 | Initial page built and published — hero, benefits, conditions, FAQ, Calendly modal |
