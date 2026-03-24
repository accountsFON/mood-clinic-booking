# Mood Clinic Landing Page - Project Context

> Last updated: 2026-03-24

## What This Project Is

A custom HTML/CSS/JS landing page for Mood Clinic (moodclinic.org), a psychiatric care practice in NH/ME/MA. The page lives inside a WordPress Elementor HTML widget and serves as the primary booking/marketing landing page. It features a Calendly modal for scheduling free 15-minute consultations and links out to the site's existing service pages.

## Tech Stack

- **Language:** HTML, CSS, JavaScript (vanilla)
- **Styling:** Tailwind CSS (CDN), inline styles
- **Fonts:** Google Fonts — Plus Jakarta Sans (headlines), Inter (body), Material Symbols Outlined (icons)
- **CMS:** WordPress via Elementor HTML widget — **post ID: 5967**
- **Site Management:** ManageWP → orion.managewp.com (site ID: 24138402)
- **WP Admin URL:** `https://moodclinic.org/wp-admin/post.php?post=5967&action=elementor`
- **Booking:** Calendly — `https://calendly.com/moodclinic/20minutes`
- **Repo:** `git@github.com:accountsFON/mood-clinic-booking.git`
- **Deployment:** Elementor "Publish" button on moodclinic.org

## Project Structure

```
mood-clinic-landing/
├── index.html          # Full page — styles, modal, all sections, scripts
└── claude-context.md   # This file
```

## How to Run / Deploy

No build step. Open `index.html` in a browser to preview locally (Tailwind loads from CDN).

**To deploy changes:**
1. Open ManageWP → Mood Clinic → WP icon → logs into moodclinic.org/wp-admin
2. Navigate to post 5967 in Elementor
3. Click the HTML widget → Edit HTML panel opens (ACE editor)
4. Paste / inject new HTML via JS: `ace.edit(document.querySelector('.ace_editor')).setValue(html, -1)`
5. Save: `elementor.saver.saveDraft()`
6. Publish: click the purple "Publish" button top-right

**Chrome MCP note:** `tabId` is a number type. Must call `ToolSearch` for `navigate`, `javascript_tool`, `computer` schemas before first use each session or they'll fail with "Expected number, received string".

## Page Sections (top to bottom)

1. **Hero** — H1, subtext, "Book Your Free 15-Minute Consult" CTA button, doctor image with rotate animation
2. **Benefits Grid** — 4 cards (Fast Access, Flexible Hours, Integrated Care, Full Coverage) + booking button
3. **Insurance Partners** — Cigna, UnitedHealthcare, Aetna, BlueCross, Oscar (grayscale hover effect). No booking button.
4. **Conditions / Expertise** — 4 cards linking to service pages (Anxiety, Depression, ADHD, Mood Disorders) + booking button
5. **FAQ Accordion** — 7 questions, accordion toggle, + booking button

## Key Implementation Details

- **Full-width breakout:** `width:100vw; position:relative; left:50%; transform:translateX(-50%)` overrides Elementor's column width so the page spans full viewport.
- **Calendly modal:** Fixed overlay `#mc-cal-overlay` toggled by `openCal()`. All CTA buttons call this. Widget loads inside the modal.
- **Nav button hiding:** Theme's "Get Started" button hidden on this page only via CSS (`header .elementor-button-wrapper {display:none!important}`) + JS fallback with 3 timeouts (300ms, 1s, 2.5s).
- **Hero top padding:** `clamp(5.5rem, 12vh, 8rem)` clears the sticky theme nav on all screen sizes.
- **FAQ accordion:** `mcToggleFaq()` — closes all, opens clicked. Active: white bg + purple left border.
- **Image animation:** Hero image rotates 2deg, transitions to 0deg on hover via inline `onmouseover/onmouseout`.
- **All font sizes are explicit px** — not rem — to avoid WordPress theme root font-size interference.

## Typography Scale (approved)

| Element | Size |
|---|---|
| Hero H1 | `clamp(3rem, 6vw, 5rem)` — 48px → 80px |
| Section H2 | `clamp(28px, 3vw, 36px)` |
| Card / Condition titles (H3/H4) | `22px` |
| FAQ questions | `18px` |
| Body / paragraph copy | `16px` |
| CTA Buttons | `18px` |
| Badge ("Now Accepting New Patients") | `13px` |
| Section subtitle ("In-Network With...") | `14px` |
| Insurance carrier names | `clamp(24px, 3vw, 32px)` |

## Internal Links

| Button / Card | Destination |
|---|---|
| Anxiety card | `https://moodclinic.org/services/anxiety/` |
| Depression card | `https://moodclinic.org/services/depression/` |
| ADHD card | `https://moodclinic.org/services/adhd/` |
| Mood Disorders card | `https://moodclinic.org/services/bipolar-disorder/` |
| All booking buttons | Opens Calendly modal |

## Known TODOs / Issues

- Nav button hiding uses JS timeouts — if the theme loads nav after 2.5s the button could reappear (unlikely)
- FAQ answers are custom copy — may need syncing with the live site's FAQ content
- No analytics/tracking events on Calendly modal open or button clicks
- Hero image is hotlinked from WP uploads — should be monitored if image changes

---

## Session Continuity

> Updated after every change. Start a new chat by reading this file first.

### Last Session (2026-03-24)

- **What was done:**
  - Built full landing page from HTML design provided by user
  - Wired all nav links to existing moodclinic.org pages
  - Wired all booking buttons to Calendly modal (calendly.com/moodclinic/20minutes)
  - Removed "Learn More" and "View All Services" buttons
  - Added booking CTA at bottom of every section except Insurance Partners
  - Hid "Get Started" nav button for this page only (CSS + JS)
  - Fixed full-width viewport layout (breakout trick)
  - Set hero background to white
  - Applied approved typography scale with all explicit px values
  - Fixed hero top padding to clear sticky nav
  - Preserved hero image rotate animation
  - Removed "Yes" from FAQ therapy answer
  - Increased H1 to `clamp(3rem, 6vw, 5rem)`
  - Created GitHub repo: `accountsFON/mood-clinic-booking`
  - Resolved Chrome MCP tabId type issue via ToolSearch schema loading
  - Used ManageWP SSO to access WP admin without manual login

- **Current state:** Page is live and published at moodclinic.org (post ID 5967). All sections rendering correctly in Elementor preview. Nav button hidden. FAQ accordion working. Calendly modal wired to all CTAs.

- **Active work:** None — stable and published.

- **Next steps:**
  - Test on mobile viewport
  - Consider adding Calendly event tracking (GA4 or Pixel)
  - Sync FAQ answers with live site copy if needed

- **Blockers:** None

### Change Log

| Date | Change |
|------|--------|
| 2026-03-24 | Increase H1 to `clamp(3rem, 6vw, 5rem)` |
| 2026-03-24 | Fix all font sizes to explicit px, hero padding, nav button hiding |
| 2026-03-24 | Apply approved typography scale |
| 2026-03-24 | Set hero background to white |
| 2026-03-24 | Add booking buttons under every section (except insurance) |
| 2026-03-24 | Wire all CTAs to Calendly modal |
| 2026-03-24 | Remove "Learn More" and "View All Services" buttons |
| 2026-03-24 | Wire nav links to existing site pages |
| 2026-03-24 | Initial page built from provided HTML design |
| 2026-03-24 | Created repo `accountsFON/mood-clinic-booking` |
| 2026-03-24 | Created claude-context.md |
