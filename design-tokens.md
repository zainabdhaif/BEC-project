# Design tokens — Bahrain Early Careers (v4)

Scope: `Calendar.dc.html`, `Opportunities.dc.html`, `About.dc.html`, `FAQ.dc.html`, `DetailPanel.dc.html` (current source of truth).
Base theme: `uploads/bahrain-early-careers-theme-and-color-palette-*.md`. Where this file differs, this file wins.

## Rules
- Only use colors listed below. No new hues.
- Accent (`#a93d35`) is reserved for: current-page nav underline, today's date (calendar number, "Today"/"Tomorrow" in rows), selected-day tint, selected weekday name, the "View all opportunities" link. Never for buttons, borders, hover or decoration.
- State is shown by color/background, never by weight. Weight stays constant across states so nothing shifts.
- Primary buttons: `ink` background, `white` text.
- No status color badges, no "Closes in N days" counters, no arrow icons on Apply.
- No intro/caption text under page titles or section labels.
- No filter-option counts, no results-count line.

## Colors

| Token         | Value                  | Usage |
|---------------|------------------------|-------|
| ink           | #101828                | Headings, listing titles, body emphasis, primary button bg, checkbox accent, 2px section rules |
| ink-hover     | #344054                | Primary button hover |
| text-strong   | #344054                | Control text (filters, sort, chips), dates in rows |
| text-muted    | #475467                | Company names, inactive nav, labels, captions, footer text, calendar-clock icon |
| icon          | #667085                | Icons, placeholders, deadline dots, out-of-month / past dates |
| text-faint    | #98a2b3                | Disabled options, inline separators |
| border-strong | #7d879b                | Input, select, filter button, chip, calendar nav button borders |
| border        | #eaecf0                | Row dividers, card/box borders, header bottom, footer top |
| surface-pill  | #f2f4f7                | Pills (where used) |
| surface-alt   | #f9fafb                | Header bg, footer bg, search/filter panel bg, row hover bg |
| white         | #ffffff                | Page bg, rows, inputs, calendar box |
| accent        | #a93d35                | See Rules |
| accent-tint   | rgba(169,61,53,0.10)   | Selected calendar day bg |
| accent-hover  | rgba(169,61,53,0.05)   | Calendar day hover bg |
| overlay       | rgba(16,24,40,0.4)     | Backdrop behind the detail panel |

## Typography

Families
- **Barlow** — headings and listing titles only. Weight 600.
- **Inter** — everything else.
- **IBM Plex Sans Arabic** — fallback for Arabic text.

Weights (one job each)
| Weight | Role | Examples |
|--------|------|----------|
| 400 | Reading text | Company names, "1 deadline" caption, no-fixed-deadline note, input text, empty-state text, copyright |
| 500 | Interactive + data | Nav links (incl. current), mobile menu items, all buttons (Apply, Today, filters, sort, Clear filters, Show results), chips, links (footer, "View all opportunities"), dates, calendar numbers, count badges |
| 600 | Structure | Barlow headings + listing titles, uppercase labels (DEADLINE, weekday names, section labels, footer group headings) |

Sizes
| Role | Font | Desktop | Mobile |
|------|------|---------|--------|
| Page title (h1) | Barlow 600, -0.01em | 36/44 | 28/36 |
| Sub heading (month, selected day, empty state) | Barlow 600 | 26/34 | 22/30 |
| Filter sheet headings | Barlow 600 | 20/28 | 20/28 |
| Listing title | Barlow 600 | 18/26, max 2 lines | same |
| Company | Inter 400 | 16/24 | same |
| Section label (ROLLING APPLICATIONS, WITH A CLOSING DATE) | Inter 600 uppercase, 0.05em | 15/20 | same |
| Small label (DEADLINE, weekdays, footer headings) | Inter 600 uppercase, 0.06em | 12/16 | same |
| Buttons, controls | Inter 500 | 15/20 | same |
| Filter chips | Inter 500 | 14/20 | same |
| Count badges (calendar day counts, filter count) | Inter 500 (calendar counts tabular) | 12/16 | same |
| Detail panel fact labels | Inter 600 uppercase, 0.06em | 12/24 | same |
| Detail panel fact values | Inter 400 (deadline 500) | 15/24 | same |
| Long-form body (detail panel description + requirements, About) | Inter 400 | 16/26 | same |
| Nav | Inter 500 | 15/24 | mobile menu 18/28 |
| Dates in rows | Inter 500, tabular | 15/20 | same |
| Calendar numbers | Inter 500, tabular | 14/20 | same |
| Captions | Inter 400 | 14/22 | same |

Minimum text size 12px for uppercase labels only; all other text ≥ 14px.

## Dates
- Format in rows: `DD/MM/YYYY` (e.g. 17/10/2026), no weekday.
- Today / tomorrow replace the date with "Today" / "Tomorrow" in accent, same weight (500).
- Calendar day heading: `Sun 11 Oct`. Month title: `October 2026`.

## Shape and elevation
- Radius: inputs/buttons 8px, calendar box 12px, search/filter panel 12px, chips 6px, calendar day cells 8px, pills 999px. Rows have no radius.
- Shadow (inputs/buttons): `0 1px 2px rgba(16,24,40,0.05)`.
- Shadow (dropdown menus): `0 12px 16px -4px rgba(16,24,40,0.08), 0 4px 6px -2px rgba(16,24,40,0.03)`.
- Shadow (overlays — detail panel, mobile menu): `0 20px 24px -4px rgba(16,24,40,0.08), 0 8px 8px -4px rgba(16,24,40,0.03)`.
- Focus ring: `2px solid #101828`, offset 2px.

## Components

Header
- Bg `surface-alt`, 1px `border` bottom. Height 64 (mobile 56).
- Logo `assets/BEC-logo-trimmed.svg` (case-sensitive on the live site), 48px (mobile 40px), no wordmark text. Favicon `assets/favicon.svg`.
- Nav: Calendar, Opportunities, About. Current page = `ink` + 2px accent underline, offset 8px. Mobile: hamburger → full-screen menu.

Footer
- Bg `surface-alt`, 1px `border` top. Logo 96px. Groups: Find (Calendar, Opportunities), About (About us, FAQ, Contact → mailto). Copyright line below.

Section label
- Uppercase label + 2px `ink` rule below (padding-bottom 12px). Used for list groups and the calendar day header.

Opportunity row (shared by both pages)
- Content: title + company only. Apply button (ink, 44px, text only).
- Opportunities page, dated rows: deadline column first (DEADLINE label + date), then title/company, then Apply. Mobile: deadline above title.
- Calendar page rows: no date info (the day heading already shows it).
- Dividers: 1px `border` bottom. Row padding 14px vertical (mobile 12px), 16px horizontal (mobile 12px) with matching negative margin so text aligns with the page edge.
- Hover: background `surface-alt` only. No accent, no shadow, no text color change.
- Whole row opens the detail panel; Apply opens employer site in a new tab.

Opportunities page
- h1 "Opportunities" + sort select on the right.
- Search + filters (Type, Industry, Major) in one `surface-alt` panel; "Clear filters" appears when anything is active. Active filter chips below.
- Two sections, both filtered by search/filters, hidden when empty:
  1. ROLLING APPLICATIONS (no deadline) — pinned first, no deadline column.
  2. WITH A CLOSING DATE — sorted by selected sort.

Calendar page
- h1 "Deadlines". Desktop: 7fr calendar / 5fr day list. Tablet/mobile: stacked.
- Calendar box: month title, prev/next + Today buttons, weekday row with 2px `ink` rule, Sunday-first grid.
- Day cell: number + grey dot (count shown if > 1). Today = accent number. Selected = `accent-tint` bg, no outline. Hover = `accent-hover` bg. Past/out-of-month = `icon` color.
- Legend: "Dots mark application deadlines." Note below box: "N opportunities have no fixed deadline." + accent "View all opportunities" link (no underline).
- Day list header: calendar-clock icon (28px, `text-muted`) + day heading, no caption, sitting on a 2px `ink` rule aligned (desktop) with the weekday rule. Empty day → "No deadlines for this day" (Inter 400 14/22, `text-muted`) under the rule.

Detail panel (`DetailPanel.dc.html`)
- Right-side sheet: 720px desktop, `min(720px, 100vw − 96px)` tablet, full-screen mobile. `overlay` backdrop. Overlay shadow. 12px left radius (none on mobile).
- Sticky 64px top bar with 1px `border` bottom; close = 44px outline button with X icon (mobile: back arrow).
- Type label (small uppercase), title (Barlow 600 26/34), company (Inter 400 16/24 `text-muted`), Apply on employer site (ink button, no arrow).
- Facts list on a 2px `ink` rule: Deadline (DD/MM/YYYY, Today/Tomorrow in accent, "Rolling applications" if none), Location, Industry, Majors. 1px dividers, 120px label column (mobile: label stacks above value).
- Requirements and About the role use section labels. Requirements: grey 6px dot bullets, no dividers, 4px vertical padding per item (12px above the first).
- One Apply button only (top).

About page (`About.dc.html`)
- Single column, max 720px: h1 "About us" on a 2px `ink` rule, body paragraphs below (Inter 400 16/26, `ink`), 24px gap. Copy is lorem ipsum placeholder.

FAQ page (`FAQ.dc.html`)
- Same single column. h1 "Frequently asked questions" on the rule, then Q (Barlow 600 18/26) + A (Inter 400 16/24, `text-muted`), 1px `border` dividers.
- Not in header nav. Linked from footer About group: About us, FAQ, Contact (mailto).

## Layout
- Density: compact (single mode). Page top padding 40px desktop / 32px tablet / 24px mobile. Section gap 40px (mobile 28px). Footer top margin 64px (tablet/mobile 48px).
- Search/filter panel padding 16px (mobile 12px). Calendar box padding 16px (mobile 12px). Calendar cells 52px desktop / 48px tablet / 44px mobile. Calendar–list gap 48px desktop / 32px stacked.
- Desktop day-header height 115px so its rule aligns with the weekday rule (1 border + 16 pad + 44 month row + 24 gap + 16 weekdays + 12 pad + 2 rule).
- Max content width 1280px. Gutters: desktop 32px, tablet 24px, mobile 16px.
- Breakpoints: mobile < 600px, tablet 600–1023px, desktop ≥ 1024px.
- Minimum hit target 44px.
