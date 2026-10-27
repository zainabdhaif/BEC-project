# Bahrain Early Careers — Design System v3

> Single design brief for the Bahrain Early Careers website. It replaces both the original theme brief (Doc A) and the v2 token sheet (Doc B) and applies to **every page**: Calendar, Opportunities, About, detail panel, header and footer.
>
> v3 takes the **look** of Doc B (cool neutrals, ink buttons, restraint) and the **substance** of Doc A (logo rules, type scale, components, accessibility, writing rules).
>
> **All values are defined once, in §6 (CSS variables).** Every other section refers to them by token name.

Last updated: 23 Oct 2026

---

## 1. Brand direction

**Quietly official:** a calm, precise, white website that reads like a bank or a university careers office. Dark ink does the work. The logo's coral appears in only a few places, so the brand feels owned without looking playful.

Bahrain Early Careers helps students and recent graduates find **internships, graduate programmes and entry-level jobs in Bahrain**.

- **Navigation:** Calendar · Opportunities · About.
- **Detail:** an opportunity opens in a panel over the list.

**Proportion:** about **85% white and cool greys, 14% ink, 1% coral.** If coral catches the eye anywhere except the logo, a selected day or an urgent deadline, there is too much.

**What makes it look legit**
- Real dates everywhere, never only "3 days left".
- Real employer names and logos, linking to official application pages.
- A clear About page: who runs the site, how listings are checked, a contact address.
- A "Last verified" date on each listing.
- No ads, no pop-ups, consistent spacing, no typos.

**Reference for the feel:** [Legal Cheek — The Firms Most List](https://www.legalcheek.com/the-firms-most-list/). Borrow its character, not its photos or ads:
- one reading column
- rows that lead with a name and one key fact
- quiet text controls
- generous white space

---

## 2. Colour palette

Use only these colours; do not introduce new hues. Contrast is measured on white.

| Token | Hex | Contrast | Usage |
| --- | --- | --- | --- |
| `ink` | `#101828` | 17.8:1 | Headings, body text, active nav, primary buttons, row Apply buttons, text links, focus ring, checkbox accent, calendar 2px rule |
| `ink-hover` | `#344054` | 10.5:1 | Hover / pressed state of ink buttons |
| `text-strong` | `#344054` | 10.5:1 | Filter and secondary button text, pill text, field labels ("Related majors:") |
| `text-muted` | `#475467` | 7.7:1 | Secondary text: employer names, metadata, inactive nav, weekday names, footer text, empty states, "No fixed deadline" |
| `icon` | `#667085` | 5.0:1 | Icons, placeholders, calendar deadline dots, past and out-of-month dates |
| `text-faint` | `#98a2b3` | 2.6:1 | **Disabled options and inline separators ( · ) only.** Never for information people need |
| `border-input` | `#7d879b` | 3.6:1 | Inputs, selects, filter buttons, checkboxes, secondary button borders |
| `border` | `#eaecf0` | 1.2:1 | Row dividers, panel outlines, header and footer rules (decorative only) |
| `surface-pill` | `#f2f4f7` | — | Company and industry pills, "Deadlines" tag, employer-initial circles, disabled control fill |
| `surface-hover` | `#f9fafb` | — | Hover grounds (rows, buttons, dropdown options), search panel, fact box, footer |
| `white` | `#ffffff` | — | Page background, inputs, dropdown menus, calendar container |
| `accent` | `#a93d35` | 6.2:1 | Selected calendar day (fill) + its weekday, urgent deadline text (≤ 7 days), hovered row title, active nav underline |
| `brand-coral` | `#d95d51` | 3.7:1 | **Inside the logo only** |
| `brand-cream` | `#f8ecdc` | — | **Inside the logo only** |

### Accent rules
- Accent is a signal, never decoration: no accent buttons, backgrounds, icons or section fills.
- Keep to a few accent marks per screen. A list where several rows are urgent still shows accent only on their deadline text.
- White on `accent` is 6.2:1, so a selected calendar day can use an accent fill with a white number.

### Deadline status

Text and icon, no coloured badges. Listings past their deadline are hidden, so there is no "Closed" status.

| Status | Rule | Text | Icon + wording |
| --- | --- | --- | --- |
| Urgent | 0–7 days | `accent`, semibold | alert-circle · "Closes today" / "Closes in 3 days" |
| Closing soon | 8–14 days | `text-muted` | clock · "Closes in 10 days" |
| Open | 15+ days | — | No status line; the date alone |
| No fixed deadline | No date | `text-muted` | "No fixed deadline" where the date would be |

---

## 3. Typography

All free on Google Fonts. Load only: **Barlow 600; Inter 400, 500, 600.**

- **Barlow 600** (`display`): headings and opportunity titles, on every page. Compact and slightly rounded, it echoes the logo's round badge without looking playful.
- **Inter 400 / 500 / 600** (`sans`): body, navigation, buttons, filters, labels, metadata and **all dates and numbers** (tabular figures).

| Style | Font | Size / line height | Weight | Sample | Use |
| --- | --- | --- | --- | --- | --- |
| `h1` | Barlow | 36/44 (mobile 28/36), −0.01em | 600 | "Graduate programmes in Bahrain" | Page title, once per page |
| `h2` | Barlow | 26/34 (mobile 22/30) | 600 | "Deadlines this month" | Section titles, detail-panel title |
| `h3` | Barlow | 20/28 | 600 | "Requirements" | Sub-sections, calendar month name, filter group titles |
| `row-title` | Barlow | 18/26 | 600 | "Graduate Analyst Programme" | Opportunity titles (max 2 lines) |
| `body` | Inter | 16/26 | 400 | "Open to graduates in accounting, finance or economics." | All paragraphs |
| `body-sm` | Inter | 14/22 | 400 | "Manama · Full-time" | Row metadata, helper text |
| `nav` | Inter | 15/24 | 500 | "Calendar  Opportunities  About" | Header and footer links |
| `button` | Inter | 15/20 | 600 | "Apply on employer site" | Buttons, dropdown labels |
| `label` | Inter | 12/16, UPPERCASE, +0.06em | 600 | "REQUIREMENTS" | Eyebrows, fact labels (one or two words only) |
| `date` | Inter | 15/20, tabular-nums | 600 | "Closes 14 Nov 2026" | Every deadline |
| `date-day` | Inter | 14/20, tabular-nums | 500 | "1 2 3 14 28" | Calendar day numbers |

### Writing rules
- Sentence case for headings and buttons ("Apply on employer site", not "APPLY NOW").
- Dates always as **14 Nov 2026**, with the weekday where space allows ("Sat 14 Nov"). Month as a word, never 14/11.
- For deadlines today or tomorrow, add "Today" / "Tomorrow" **above** the date, never instead of it.
- Write the type "GTP" as **"Graduate programme"**.
- Left-align text; never justify.

---

## 4. Spacing, radius, shadow

### Spacing (8px base; use only these steps)

| Token | Value | Usage |
| --- | --- | --- |
| `space-1` | 4px | Icon-to-text gap, tag vertical padding |
| `space-2` | 8px | Gap between dropdowns, chips and meta items; between adjacent touch targets |
| `space-3` | 12px | Row title to meta row |
| `space-4` | 16px | Mobile gutter; row vertical padding (mobile) |
| `space-5` | 24px | Row vertical padding (desktop); search panel padding; tablet gutter |
| `space-6` | 32px | Desktop gutter; heading to content block |
| `space-7` | 48px | Between page sections (mobile) |
| `space-8` | 64px | Between page sections (desktop) |

### Radius (no other values)

| Token | Value | Usage |
| --- | --- | --- |
| `radius-none` | 0 | "Deadlines" tag |
| `radius-sm` | 6px | Filter chips, small tags |
| `radius-md` | 8px | Buttons, inputs, dropdowns, calendar day cells |
| `radius-lg` | 12px | Search panel, detail panel, fact box, calendar container |
| `radius-full` | 999px | Company / industry pills, deadline dots, employer-logo circles |

### Shadow (borders and dividers do most of the work)

| Token | Usage |
| --- | --- |
| `shadow-xs` | Inputs, dropdown buttons, secondary buttons |
| `shadow-menu` | Open dropdown menus |
| `shadow-overlay` | Detail panel, mobile filter sheet, mobile menu |

No shadows on rows, the search panel or the calendar.

---

## 5. Layout

- **Container:** max `width-content` (1280px), centred.
- **Gutters:** 16px mobile, 24px tablet, 32px desktop.
- **Breakpoints:** mobile < 600px, tablet 600–1023px, desktop ≥ 1024px.
- **Reading width:** paragraphs max `width-reading` (720px).
- **Opportunities page:** full-width search panel above **one column of divider rows**, with no cards. On mobile the filters move into a full-screen sheet.
- **Spacing:** row padding `space-5` top and bottom (`space-4` mobile); `space-8` between page sections (`space-7` mobile).
- **Alignment:** everything left-aligned to one edge. Dates and status sit at the end of a row on desktop and tablet, under the title on mobile.
- **Touch targets:** 44 × 44px minimum.

---

## 6. CSS variables (single source of values)

```css
:root {
  /* text and ink */
  --ink: #101828;
  --ink-hover: #344054;
  --text-strong: #344054;
  --text-muted: #475467;
  --icon: #667085;
  --text-faint: #98a2b3;   /* disabled + separators only */
  --on-ink: #ffffff;
  /* borders */
  --border-input: #7d879b; /* 3.6:1 — controls */
  --border: #eaecf0;       /* decorative dividers */
  /* surfaces */
  --white: #ffffff;
  --surface-hover: #f9fafb;
  --surface-pill: #f2f4f7;
  /* accent */
  --accent: #a93d35;
  --on-accent: #ffffff;
  /* logo only — never used in UI */
  --brand-coral: #d95d51;
  --brand-cream: #f8ecdc;
  /* focus */
  --focus-ring: 2px solid var(--ink);
  --focus-offset: 2px;
  /* type */
  --font-display: Barlow, system-ui, sans-serif;
  --font-sans: Inter, system-ui, -apple-system, "Segoe UI", sans-serif;
  /* spacing */
  --space-1: 4px; --space-2: 8px; --space-3: 12px; --space-4: 16px;
  --space-5: 24px; --space-6: 32px; --space-7: 48px; --space-8: 64px;
  --width-content: 1280px; --width-reading: 720px; --touch-target: 44px;
  /* radius */
  --radius-none: 0; --radius-sm: 6px; --radius-md: 8px; --radius-lg: 12px; --radius-full: 999px;
  /* shadow */
  --shadow-xs: 0 1px 2px rgba(16, 24, 40, 0.05);
  --shadow-menu: 0 12px 16px -4px rgba(16, 24, 40, 0.08), 0 4px 6px -2px rgba(16, 24, 40, 0.03);
  --shadow-overlay: 0 20px 24px -4px rgba(16, 24, 40, 0.08), 0 8px 8px -4px rgba(16, 24, 40, 0.03);
}

/* breakpoints: mobile < 600px · tablet 600–1023px · desktop ≥ 1024px */
.date, .date-day { font-family: var(--font-sans); font-variant-numeric: tabular-nums; }
```

```html
<link href="https://fonts.googleapis.com/css2?family=Barlow:wght@600&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
```

---

## 7. Logo usage

The logo is a round coral badge with a cream serrated edge on the left (a nod to the Bahraini flag), "BAHRAIN" in spaced light-grey capitals and "Early Careers" in bold. On this cool, quiet site it is the **main splash of brand colour**, so give it room.

File: `BEC-logo-trimmed.svg` (circle on a transparent background). Don't use the untrimmed `BEC-logo.svg`, which has a white square around the badge.

| Placement | Size (circle diameter) | Notes |
| --- | --- | --- |
| Desktop header | **64px** in an 80px bar | Left, aligned with the content edge; links to Calendar (landing page) |
| Mobile header | **48px** in a 64px bar | Left; menu icon right |
| Footer | **96px** | On `surface-hover`; wordmark fully legible |
| About hero (optional) | 140–200px | Only if the page has no large heading image |
| Favicon | 32px | Badge as-is |
| Minimum | **40px** | Below this the words can't be read |

- **Clear space:** at least ¼ of the diameter on all sides (16px at 64px, 24px at 96px).
- **Backgrounds:** `white`, `surface-hover` or `ink`. Not on coral, cream, photos or patterns.
- Scale proportionally only. No recolouring, outlining, rotating, stretching, cropping or rebuilding the text.
- No second text logo beside it; the full name appears in the page title, footer and browser tab.
- Alt text: "Bahrain Early Careers — home".

---

## 8. Components

### Shared states

| State | Treatment |
| --- | --- |
| Hover | Ink buttons → `ink-hover`; secondary buttons, rows, options → `surface-hover` fill; `border` → `border-input`. Cursor: pointer |
| Focus (keyboard) | `focus-ring` (2px ink) with 2px offset on every interactive element. Never removed |
| Selected | Calendar day: `accent` fill, white number. Dropdown option: ticked checkbox (`ink`). Never colour alone |
| Disabled | `surface-pill` fill, `text-faint` text, no hover; explain why nearby ("No results for this filter") |

### Site header
- **Desktop:** 80px tall, `white`, 1px `border` below. Logo 64px left. Links in `nav` style, `text-muted`; current page in `ink` with a 2px `accent` underline.
- **Mobile:** 64px tall, logo 48px left, menu icon right (44px). The menu opens a full-screen sheet with 18px links.

### Buttons
- **Primary:** `ink` fill, white text, `button` style, 44px tall, `radius-md`, 20px side padding, `shadow-xs`. Hover `ink-hover`. Main action only: "Apply on employer site", "Show 24 results". One per view.
- **Secondary:** `white` fill, 1px `border-input`, `text-strong` text, `shadow-xs`. "Today" (calendar), "Filters" (mobile). Hover: `surface-hover` fill.
- **Row Apply:** `ink` fill, white text, 44px tall, `radius-md`, 16px side padding, label "Apply ↗". One per opportunity row; opens the employer's site in a new tab. Hover: `ink-hover`.
- **Text link:** `ink`, underlined (3px offset). "View all by deadline", "Clear filters" and in-text links. Hover: underline thickens to 2px.
- Never: accent or coral fills, all caps, icon-only primary buttons.

### Search panel and filter dropdowns
- One panel above the results: `surface-hover` fill, `radius-lg`, `space-5` padding, no shadow.
- **Top line:** full-width search field (`white`, 1px `border-input`, `radius-md`, 44px tall, `shadow-xs`, search icon in `icon` at the start, placeholder "Search by role, employer, major or skill").
- **Second line:** dropdowns side by side, `space-2` apart: "All types", "All industries", "All majors". "Clear filters" text link at the far end.
- **Dropdown button:** `white`, 1px `border-input`, `radius-md`, 44px tall, `text-strong` label, chevron at the end. The label shows the selection ("Internship", or "Majors · 2").
- **Dropdown menu:** `white`, `shadow-menu`, `radius-md`. Checkbox options with the result count in `text-muted` ("Internship 7"). A 0-result option is disabled, not hidden. The majors menu has a small search field at the top.
- **Active-filter chips:** under the panel, each selected value as a chip (`radius-sm`, `white`, 1px `border-input`, `text-strong`) with an ✕ to remove it.
- **Mobile:** keeps the search field; the dropdowns become a secondary "Filters" button that opens a full-screen sheet with the three groups as checkbox lists and a sticky "Show 7 results" primary button.

### Deadline line
- `date` style, always with the full date: "Fri 9 Oct 2026".
- Below or beside it, the status line from §2 (icon + words). Urgent in `accent` semibold; closing soon in `text-muted`; open shows no status line.
- The label above the date reads **DEADLINE**, or **TODAY** / **TOMORROW** (in `accent`) when it closes today or tomorrow.
- No fixed deadline: "No fixed deadline" in `text-muted` in place of the date.

### Opportunity row
- One column, **no box**: a 1px `border` hairline above the first row and below every row.
- **Layout:** 40px employer-logo circle (initials in `text-strong` on `surface-pill` when there is no logo) · title (`row-title`, max 2 lines) · employer (`text-muted`) · meta row (location · type, `body-sm`, separators in `text-faint`) · optional pills (company, industry: `surface-pill`, `radius-full`, `text-strong`) · deadline block · row Apply button at the very end.
- `space-5` padding top and bottom (`space-4` mobile); no side padding, so text lines up with the page edge.
- **Hover:** `surface-hover` fill across the row, title in `accent`, plus a 2px `accent` line along the row's top edge. No shadow.
- **Mobile:** the deadline block moves under the meta row, with Apply at the end of that line; logo circle 32px.
- The row opens the detail panel; Apply is a separate control (not nested inside the row link). Its accessible name includes the role: "Apply for Graduate Analyst Programme at Gulf Pearl Bank (opens employer site)".
- The calendar's tab lists use the same row.

### Deadline calendar
- Month in a container: `white`, 1px `border`, `radius-lg`, `space-5` padding. Month name in `h3` at the start; previous / next arrows and a secondary "Today" button at the end. A 2px `ink` rule sits under the weekday row.
- Week starts **Sunday** (Bahrain working week). Weekday names in `label` style, `text-muted`.
- Day cells: `radius-md`, at least 44px tall, `date-day` style.
- **Has deadlines:** 6px `icon` dot under the number, plus a count when more than one ("●3").
- **Today:** 1px `ink` ring, number in semibold.
- **Selected:** `accent` fill, white number and dot; its weekday name turns `accent`.
- **Past / out-of-month days:** number in `icon`.
- **Hover:** `surface-hover` fill.
- Under the grid, a legend in `body-sm`, `text-muted`: "● Dots mark application deadlines."
- Accessible name per day: "20 October, 3 deadlines".
- **Below the grid, a tab group:** "Next 5 deadlines" (ends with a "View all by deadline" link) and "No fixed deadline". Clicking a day adds a first tab for that day ("Tue 20 Oct · 3") and makes it active.
- **Mobile:** opens in **List / Agenda view** (upcoming deadlines grouped by week) with a toggle to the month grid.

### Detail panel
- **Order:** `label` type eyebrow · `h2` title · employer and location · primary "Apply on employer site ↗" · fact box · requirements · description · "Last verified 20 Oct 2026" in `body-sm`, `text-muted`.
- **Fact box:** `surface-hover`, `radius-lg`, `space-5` padding, labelled rows DEADLINE · TYPE · LOCATION · INDUSTRY · MAJORS. Labels in `label` caps, `text-muted` (140px column); values in `body`, `ink`. Labels stack above values on mobile.
- **Requirements:** ✓ checklist with the check in `ink`, one skill per line.
- Paragraphs max `width-reading`. Repeat the primary button at the end of long descriptions.
- **Desktop and tablet:** side panel over the list with `shadow-overlay`; closes with ✕ or Esc and returns focus to the row. **Mobile:** full screen with a back arrow.

### Site footer
- `surface-hover` ground, 1px `border` top rule.
- Logo at 96px. Link groups headed in `label` caps, `text-muted`; links in `ink`, underlined on hover.
- Groups: **Find** (Calendar, Opportunities), **About** (About us, How we verify listings, Contact).

---

## 9. Accessibility

- **Text sizes:** body 16px minimum; metadata 14px minimum; 12px `label` caps for one- or two-word labels only.
- **Contrast:** all text pairs in §2 meet WCAG AA (lowest readable pair: `icon` at 5.0:1). Control borders (`border-input`, 3.6:1) and the focus ring meet 3:1. `text-faint` is for disabled items and separators only.
- **Touch targets:** 44 × 44px minimum, with `space-2` between adjacent targets.
- **Keyboard:** every link, dropdown, calendar day and button reachable with Tab in reading order; focus ring always visible. Dropdown menus, the mobile filter sheet and the detail panel close with Esc (the sheet and panel also trap focus).
- **Not colour alone:** urgent deadlines carry an icon, words and the real date; selected filter options have a ticked checkbox; the selected calendar day has an accessible "selected" state; calendar dots have a count and an accessible name.
- **Motion:** none required; if used, under 200ms and respect "reduce motion".

---

## 10. Avoid

- Accent or coral on buttons, backgrounds, section fills, icons or decoration.
- `brand-coral` or `brand-cream` anywhere outside the logo.
- Warm beige / brown neutrals from the old theme, or any hue not in §2.
- Coloured status badges (green / amber / coral tags).
- Showing urgency by colour alone, or relative dates without the real date.
- Card boxes around opportunity rows, heavy shadows, gradients, coloured side stripes.
- Different font families on different pages; Barlow for long paragraphs; fonts beyond Barlow and Inter.
- `text-faint` for anything people need to read; `border` (`#eaecf0`) as the only edge of an input.
- Recolouring, outlining, stretching or cropping the logo; placing it on coral, cream or photos.
- More than one primary button per view (row Apply buttons excepted); all-caps buttons.
- The serration mark or other logo shapes used as decoration.
