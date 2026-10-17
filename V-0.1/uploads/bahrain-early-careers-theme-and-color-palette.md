# Bahrain Early Careers — Theme and Color Palette

> Design brief for prototyping the Bahrain Early Careers website. Everything a designer (or Claude Design) needs: brand direction, color tokens, typography, layout, logo rules, components and accessibility rules.
>
> **All colour, spacing, radius and shadow values are defined once, in §6 (CSS variables).** Every other section refers to them by token name.

---

## 1. About the site

Bahrain Early Careers helps students and recent graduates find **internships, graduate programmes and entry-level jobs in Bahrain**.

**Feel:** minimal, clear and approachable. White space and dark text do the work, the logo's coral appears in a few purposeful places, and every deadline can be read at a glance.

**Direction in one line:** a white, calm website where the coral badge is the only big splash of colour, one deepened coral marks every action and urgent deadline, and two small shapes from the logo — the circle and the serrated edge — appear as quiet accents.

**Reference for the feel:** [Legal Cheek — The Firms Most List](https://www.legalcheek.com/the-firms-most-list/). Borrow its calm, clean, minimal character:
- one main reading column
- list rows that lead with a name and one key fact, with little decoration per row
- quiet, text-based controls
- plenty of white space between items

Take the feel only, not its hero photo or advertising.

**Main sections (navigation):** Calendar · Opportunities · About. Opportunity detail opens as a panel over the list.

---

## 2. What the logo gives us

The logo is a round coral badge with a cream serrated edge on the left (a nod to the Bahraini flag), the word "BAHRAIN" in spaced light-grey capitals and "Early Careers" in bold.

| Element | Observation | How the website uses it |
| --- | --- | --- |
| Coral (`brand-coral`) | Warm, friendly red-coral; the badge's field | Kept for the logo and small graphics. For buttons and text it is deepened to `primary`, because the original coral is only 3.7:1 on white |
| Cream (`brand-cream`) | Warm off-white in the serrated edge and wordmark | Becomes the highlight ground (today in the calendar) |
| Light grey (`brand-grey`) | The spaced "BAHRAIN" line | Stays inside the logo only; its spaced capitals inspire the `label` style |
| Typeface | Poppins — Regular, wide-tracked caps for "BAHRAIN"; Bold for "Early Careers" | Poppins for headings, so the site and the logo share a voice |
| Circle | A round badge — soft, approachable | Round deadline dots, employer-logo circles and pill-shaped active-filter chips |
| Serrated edge | Five cream points on the left | A small "serration mark", used once per page at most |

Logo file: `BEC-logo-trimmed.svg`, trimmed to the circle on a transparent background. Attach it separately when prototyping. (`BEC-logo.svg` is the untrimmed original, with a white square around the badge; don't use it on the site.)

---

## 3. Colour palette

**Proportion:** roughly **80% white and warm neutrals, 15% ink text, 5% coral.** If a screen looks pink, there is too much coral.

Values for every token are in §6.

### Brand colours (from the logo)

| Token | Usage |
| --- | --- |
| `brand-coral` | Logo itself and small graphic accents only: calendar deadline dots, the serration mark, an icon. **Never for text or button fills** (3.7:1 on white). |
| `brand-cream` | Warm highlight ground: today in the calendar. Not behind the logo. `ink` (12.9:1) and `primary` (5.3:1) read on it. |
| `brand-grey` | Lives inside the logo only. Do not use on the website. |

### Action colours

| Token | Usage |
| --- | --- |
| `primary` | The one action colour (deepened logo coral). Primary button fill, text links, focus ring, urgent-deadline text. 6.2:1 on white. |
| `primary-hover` | Hover / pressed state of primary buttons and links. |
| `primary-tint` | Soft coral ground: urgent deadline badge, hover row in calendar list. |
| `on-primary` | Text and icons on `primary` / `primary-hover`. |

### Neutrals

| Token | Usage |
| --- | --- |
| `bg` | Page background, inputs, dropdowns, calendar container |
| `surface` | Search panel, detail-panel fact box, row hover, footer |
| `surface-muted` | Disabled control fill |
| `ink` | Headings, body, dates, selected calendar day, row Apply buttons (15.1:1 on white) |
| `ink-muted` | Secondary text: employer names, metadata, helper text, "No fixed deadline" (7.2:1 on white) |
| `ink-disabled` | Disabled labels only — never for information users need |
| `border` | Hairline dividers between opportunity rows, panel outlines (1px) |
| `border-strong` | Inputs, dropdowns, checkboxes (3.7:1) |
| `focus-ring` | 2px solid ring with 2px gap (same colour as `primary`) |

### Deadline status colours

Always paired with a **word and an icon** — never colour alone. Opportunities past their deadline are hidden, so there is no "Closed" status.

| Status | Rule | Text token | Ground token | Icon + wording |
| --- | --- | --- | --- | --- |
| Urgent | 0–7 days left | `status-urgent` | `status-urgent-bg` | alert-circle · "Closes in 3 days" / "Closes today" |
| Closing soon | 8–14 days | `status-soon` | `status-soon-bg` | clock · "Closes in 10 days" |
| Open | 15+ days | `status-open` | `status-open-bg` | check-circle · "Open" |
| No fixed deadline | No deadline date | `ink-muted` | none | No badge — "No fixed deadline" is shown in place of the date |

Every text pair meets WCAG AA (lowest is 5.3:1). Control borders and the focus ring meet 3:1.

---

## 4. Typography

All free on Google Fonts. Font stacks are in §6 (`--font-display`, `--font-sans`, `--font-arabic`).

- **Poppins 600** (`display`) — headings only. The logo's typeface; SemiBold rather than Bold so headings stay calm.
- **IBM Plex Sans 400 / 500 / 600** (`sans`) — body, navigation, labels, dates. Has tabular figures so dates line up.
- **IBM Plex Sans Arabic** (`arabic`) — companion for a future Arabic version. Set one step larger with more line height.

| Style | Font | Size / line height | Weight | Sample | Use |
| --- | --- | --- | --- | --- | --- |
| `h1` | Poppins | 36/44 (mobile 28/36), −0.01em | 600 | "Graduate programmes in Bahrain" | Page title, once per page |
| `h2` | Poppins | 26/34 (mobile 22/30) | 600 | "Deadlines this month" | Section titles |
| `h3` | Poppins | 20/28 | 600 | "Requirements" | Detail-panel sub-sections, calendar month name, filter-sheet group titles |
| `row-title` | Poppins | 18/26 | 600 | "Graduate Analyst Programme" | Opportunity titles (max 2 lines) |
| `body` | IBM Plex Sans | 16/26 | 400 | "Open to graduates in accounting, finance or economics." | All paragraphs |
| `body-sm` | IBM Plex Sans | 14/22 | 400 | "Manama · Full-time" | Row metadata, helper text |
| `nav` | IBM Plex Sans | 15/24 | 500 | "Calendar  Opportunities  About" | Header and footer links |
| `button` | IBM Plex Sans | 15/20 | 600 | "Apply on employer site" | Buttons, dropdown labels |
| `label` | IBM Plex Sans | 12/16, UPPERCASE, +0.08em | 600 | "REQUIREMENTS" | Eyebrows, fact labels (echoes logo's spaced "BAHRAIN") |
| `date` | IBM Plex Sans | 15/20, tabular-nums | 600 | "Closes 14 Nov 2026" | Every deadline |
| `date-day` | IBM Plex Sans | 14/20, tabular-nums | 500 | "1 2 3 14 28" | Calendar day numbers |
| `ar-heading` | IBM Plex Sans Arabic | 30/44 | 600 | "فرص التدريب في البحرين" | Arabic headings (future) |
| `ar-body` | IBM Plex Sans Arabic | 17/30 | 400 | "آخر موعد للتقديم ١٤ نوفمبر ٢٠٢٦" | Arabic body (future) |

**Writing rules**
- Sentence case for headings and buttons ("Apply on employer site", not "APPLY NOW").
- Dates always written the same way: **14 Nov 2026**, plus the weekday where space allows ("Sat 14 Nov"). Month as a word, never 14/11.
- For deadlines today or tomorrow, add "Today" / "Tomorrow" **above** the date, never instead of it.
- Write the type "GTP" as **"Graduate programme"**.
- Left-align text; never justify.

---

## 5. Spacing, radius, shadow

Values are in §6.

**Spacing (8px base — use only these steps)**

| Token | Usage |
| --- | --- |
| `space-1` | Icon-to-text gap, badge vertical padding |
| `space-2` | Gap between dropdowns, chips and meta items |
| `space-3` | Row title to meta row |
| `space-4` | Mobile gutter; row vertical padding (mobile) |
| `space-5` | Row vertical padding (desktop); search panel padding; tablet gutter |
| `space-6` | Desktop gutter; heading to content block |
| `space-7` | Between page sections (mobile) |
| `space-8` | Between page sections (desktop) |
| `width-content` | Max page container width |
| `width-reading` | Max paragraph width (~70 characters) |
| `touch-target` | Minimum size of anything tappable |

**Radius** — no other values.

| Token | Usage |
| --- | --- |
| `radius-sm` | Status badges, small tags |
| `radius-md` | Buttons, inputs, dropdowns, calendar day cells |
| `radius-lg` | Search panel, detail panel, fact box, calendar container |
| `radius-full` | Active-filter chips, deadline dots, employer-logo circles |

**Shadow** — borders and dividers do the work; shadows only lift things that float.

| Token | Usage |
| --- | --- |
| `shadow-overlay` | Detail panel overlay, mobile filter sheet, open dropdown menus |

---

## 6. CSS variables (single source of values)

```css
:root {
  /* brand */
  --brand-coral: #d95d51;
  --brand-cream: #f8ecdc;
  --brand-grey: #d6d7d9;  /* logo only — not used on the website */
  /* action */
  --primary: #a93d35;
  --primary-hover: #8e322c;
  --primary-tint: #fbeae6;
  --on-primary: #ffffff;
  /* neutrals */
  --bg: #ffffff;
  --surface: #faf7f4;
  --surface-muted: #f1edea;
  --ink: #2b2523;
  --ink-muted: #5e5653;
  --ink-disabled: #a39b97;
  --border: #e7dfd9;
  --border-strong: #8c8380;
  --focus-ring: var(--primary);
  /* status */
  --status-open: #2f6b4f;      --status-open-bg: #e8f3ec;
  --status-soon: #8a5300;      --status-soon-bg: #fdf1dc;
  --status-urgent: var(--primary); --status-urgent-bg: var(--primary-tint);
  /* type */
  --font-display: Poppins, "IBM Plex Sans Arabic", system-ui, sans-serif;
  --font-sans: "IBM Plex Sans", "IBM Plex Sans Arabic", system-ui, -apple-system, "Segoe UI", sans-serif;
  --font-arabic: "IBM Plex Sans Arabic", "IBM Plex Sans", system-ui, sans-serif;
  /* spacing */
  --space-1: 4px; --space-2: 8px; --space-3: 12px; --space-4: 16px;
  --space-5: 24px; --space-6: 32px; --space-7: 48px; --space-8: 64px;
  --width-content: 1200px; --width-reading: 720px; --touch-target: 44px;
  /* radius */
  --radius-sm: 6px; --radius-md: 8px; --radius-lg: 12px; --radius-full: 999px;
  /* shadow */
  --shadow-overlay: 0 8px 24px rgba(43, 37, 35, 0.12);
}
```

Google Fonts: Poppins (600), IBM Plex Sans (400, 500, 600), IBM Plex Sans Arabic (400, 600).

---

## 7. Logo usage

| Placement | Size (circle diameter) | Notes |
| --- | --- | --- |
| Desktop header | **64px** in an 80px-tall bar | Left-aligned with content edge; links to the Calendar page (landing page) |
| Mobile header | **48px** in a 64px-tall bar | Left; menu icon right |
| Footer | **96px** | On `surface`; wordmark fully legible |
| About hero (optional) | 140–200px | Only if the page has no large heading image |
| Favicon | 32px | Badge as-is |
| Minimum | **40px** | Below this the words can't be read |

- **Clear space:** at least ¼ of the diameter on all sides (16px at 64px, 24px at 96px).
- **Backgrounds:** `bg` or `surface` (also holds on `ink`). **Not** on `brand-cream`, coral, photographs or patterns.
- Scale proportionally only. No recolouring, outlining, rotating, stretching, cropping or rebuilding the text.
- Don't add a second text logo next to it — the full name appears in page title, footer and browser tab.
- Alt text: "Bahrain Early Careers — home".

---

## 8. Layout

- **Container:** max `width-content`, centred. Gutters: `space-4` mobile, `space-5` tablet, `space-6` desktop.
- **Reading width:** detail-panel paragraphs max `width-reading`.
- **Opportunities page:** a full-width search panel (search field + filter dropdowns) above **one column of divider rows** — no card boxes, like a clean ranked list. On mobile, the filter dropdowns move into a full-screen sheet.
- **Spacing:** row padding `space-5` top and bottom (`space-4` mobile), `space-8` between page sections (`space-7` mobile).
- **Alignment:** everything left-aligned to one edge. Dates and status sit at the right end of a row on desktop and tablet, under the title on mobile.

---

## 9. Accents from the logo (use sparingly)

1. **The circle** — 6px `brand-coral` deadline dots in the calendar, employer logos in 40px circles, active-filter chips as full pills. The everyday accent.
2. **The serration mark** — five small triangles from the logo's edge, 8px tall, in `brand-coral`. Runs once along the top edge of the footer, and nowhere else on the page. Never as a background pattern, behind text or in list rows.

---

## 10. Components

### Shared states

| State | Treatment |
| --- | --- |
| Hover | One step darker (`primary` → `primary-hover`; `border` → `border-strong`). Cursor: pointer |
| Focus (keyboard) | 2px solid `focus-ring` with a 2px white gap, on every interactive element. Never removed |
| Selected | Calendar day: `ink` fill with white number. Dropdown option: ticked checkbox. Never colour alone |
| Disabled | `surface-muted` fill, `ink-disabled` text, no hover; explain why nearby ("No results for this filter") |

### Site header
- Desktop: 80px tall, `bg`, 1px `border` below. Logo 64px left, linking to the Calendar page. Links (Calendar, Opportunities, About) in `nav` style, `ink-muted`; current page `ink` with 2px `primary` underline.
- Mobile: 64px tall, logo 48px left, menu icon right (`touch-target`). Menu opens a full-screen sheet with links at 18px.

### Buttons
- **Primary:** `primary` fill, `on-primary` text, `button` style, `touch-target` tall, `radius-md`, 20px side padding. Main action only — "Apply on employer site", "Show 24 results". One per view.
- **Secondary:** `bg` fill, 1px `border-strong`, `ink` text. "Today" (calendar), "Filters" (mobile). Hover: `surface` fill, `ink` border.
- **Row Apply:** `ink` fill, white text, `button` style, `touch-target` tall, `radius-md`, 16px side padding, label "Apply ↗". One at the end of every opportunity row; opens the employer's site in a new tab. Hover: label underlined. Dark, not coral, so the list doesn't turn pink and the coral primary button stays the single main action.
- **Text link:** `primary`, underlined (3px offset). "View all by deadline", "Clear all" and in-text links.
- Don't use all caps, icon-only primary buttons, or `brand-coral` fills.

### Search panel and filter dropdowns
- One panel above the results: `surface` fill, `radius-lg`, `space-5` padding.
- **Top line:** a full-width search field (`bg`, 1px `border-strong`, `radius-md`, `touch-target` tall, search icon at the start, placeholder "Search by role, employer, major or skill").
- **Second line:** filter dropdowns side by side, `space-2` apart — "All types", "All industries", "All majors". On the far end, a "Clear filters" text link.
- **Dropdown button:** `bg`, 1px `border-strong`, `radius-md`, `touch-target` tall, chevron at the end. The label shows the selection ("Internship", or "Majors · 2" when several are picked).
- **Dropdown menu:** `bg`, `shadow-overlay`, `radius-md`; options are checkboxes (multi-select) with the result count in `ink-muted` ("Internship 7"). A 0-result option is disabled, not hidden. The major menu gets a small search field at the top because the list is long.
- **Active-filter chips:** under the panel, each selected value appears as a pill (`radius-full`, `bg`, 1px `border`) with an ✕ to remove it.
- **Mobile:** the panel keeps the search field; the dropdowns are replaced by a secondary "Filters" button that opens a full-screen sheet with the same three groups as checkbox lists and a sticky "Show 7 results" primary button.

### Deadline badge
- `radius-sm`, 13px semibold text, 4px × 10px padding, icon + words + day count (see status table).
- The full date always sits beside or above it in `date` style ("Fri 9 Oct 2026").
- Deadline today or tomorrow: the label above the date reads "TODAY" / "TOMORROW" in `primary` (instead of "DEADLINE"); the date and badge still show.
- No fixed deadline: no badge; "No fixed deadline" in `ink-muted` where the date would be.

### Opportunity row
- Rows sit in one column with **no box around them**: a 1px `border` hairline above the first row and below every row, like a clean ranked list.
- Layout: 40px employer-logo circle (initials on `surface` when there is no logo) · title (`row-title`, max 2 lines) · employer (`ink-muted`) · meta row (location · type, `body-sm`) · deadline block (DEADLINE label — or TODAY / TOMORROW — `date`, badge) · row Apply button at the very end.
- `space-5` padding top and bottom (`space-4` mobile), no side padding so text lines up with the page edge.
- Hover: `surface` fill across the row and the title underlined. No shadow.
- Mobile: the deadline block moves under the meta row, with the Apply button at the end of that line; logo circle 32px.
- The row opens the detail panel; the Apply button is a separate control (not nested inside the row link) and goes straight to the employer's site. Its accessible name includes the role: "Apply for Graduate Analyst Programme at Gulf Pearl Bank (opens employer site)".
- The calendar's tab lists use the same row.

### Deadline calendar
- The month sits in a container (`bg`, 1px `border`, `radius-lg`, `space-5` padding): month name in `h3` at the start, previous/next arrows and a "Today" button at the end.
- Week starts **Sunday** (Bahrain working week). Day names in `label` style.
- Under the grid, a one-line legend in `body-sm`, `ink-muted`: "● Dots mark application deadlines."
- Day cells: `radius-md`, at least `touch-target` tall, tabular numbers.
- **Today:** `brand-cream` fill + 1px `ink` ring. **Has deadlines:** 6px `brand-coral` dot, plus a count when more than one ("●3"). **Selected:** `ink` fill, white number (dot turns cream). **Hover:** `surface` fill.
- Accessible name per day: "20 October, 3 deadlines".
- **Below the grid, a tab group:** "Next 5 deadlines" (ends with a "View all by deadline" link) and "No fixed deadline". Clicking a day adds a first tab for that day ("Tue 20 Oct · 3") and makes it active. Each list shows opportunities with their date and badge.
- Mobile: open in **List / Agenda view** (upcoming deadlines grouped by week) with a toggle to the month grid.

### Detail panel
- Order: `label` type eyebrow · `h2` title · employer and location · primary "Apply on employer site ↗" · fact box · requirements · description.
- **Fact box:** `surface`, `radius-lg`, `space-5` padding, labelled rows — DEADLINE · TYPE · LOCATION · INDUSTRY · MAJORS. Label in `label` caps (140px column), value in body. Labels stack above values on mobile.
- **Requirements** as a ✓ checklist (green `status-open` check), one skill per line.
- Deadline shows the date plus the badge.
- Paragraphs max `width-reading`. Repeat the primary button at the end of long descriptions.
- Desktop and tablet: side panel over the list with `shadow-overlay`, closes with ✕ or Esc, returns focus to the row. Mobile: full screen with a back arrow.

### Site footer
- `surface` ground; serration mark (coral triangles, 8px tall) runs once along its top edge.
- Logo at 96px. Link groups headed in `label` caps; links in `ink`, underlined on hover.
- Groups: **Find** (Calendar, Opportunities), **About** (About us, Contact).

---

## 11. Mobile and accessibility

- **Font sizes:** body 16px minimum; metadata 14px minimum; 12px `label` caps for one- or two-word labels only.
- **Touch targets:** `touch-target` × `touch-target` minimum; `space-2` between adjacent targets.
- **Contrast:** use the token pairs as documented; never `brand-coral` or `brand-grey` text on white.
- **Keyboard:** every link, dropdown, calendar day and button reachable with Tab, in reading order; focus ring always visible; dropdown menus, the mobile filter sheet and the detail panel close with Esc (the sheet and panel also trap focus).
- **Not colour alone:** each deadline status has a word, an icon and a day count; selected filter options have a ticked checkbox; calendar dots also have a number and an accessible name.
- **Motion:** none required; if used, under 200ms and respect "reduce motion".
- **Arabic later:** build layouts with start/end alignment so they mirror for right-to-left.

---

## 12. Avoid

- Coral backgrounds for whole sections, or coral text in paragraphs.
- Using `brand-coral` for buttons or text (too light) — use `primary`.
- Recolouring, outlining, stretching or cropping the logo; placing it on cream, coral or photos.
- More than one coral primary button per view (row Apply buttons are `ink`, not `primary`); all-caps buttons.
- Showing deadline urgency by colour alone, or relative dates without the actual date.
- Card boxes around opportunity rows, heavy drop shadows, gradients, and coloured stripes down the side of rows.
- Using the serration mark more than once per page, or as a pattern.
- Extra fonts, or Poppins for long paragraphs.
- Text smaller than 14px (except one-word `label` caps), and grey text lighter than `ink-muted`.
