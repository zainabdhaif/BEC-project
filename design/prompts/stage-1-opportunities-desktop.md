# Stage 1 — Opportunities page and detail panel (desktop)

> **Attach:** `bahrain-early-careers-theme-and-color-palette.md`, `dummy-data.json`, `BEC-logo-trimmed.svg`, `ref-legal-cheek-list.png`, `ref-deadline-list.png`, `ref-opportunity-search.png`
>
> **Check before Stage 2:**
> - It looks white and calm, not pink.
> - Rows are divider rows (no boxes), role first, with the deadline and a dark Apply button at the end.
> - The 3 visible "urgent" items and "No fixed deadline" items look right.
> - The detail panel opens and closes.
>
> Ask for fixes here. Later stages copy whatever this stage sets.

---

Design a clickable, front-end-only prototype for **Bahrain Early Careers (BEC)**. BEC is a website that helps students and recent graduates in Bahrain find internships, graduate programmes and entry-level full-time jobs. The team will judge the look and feel from it. Use the realistic dummy data in the attached `dummy-data.json`. No back end, accounts or admin screens.

We'll build this in four stages. **This stage covers the Opportunities page and the opportunity detail panel, desktop only (1440px).** Later stages add tablet and mobile, a Calendar page and an About page. Build the header, footer, rows and panel as reusable components.

The attached **theme doc is the source of truth for visual style**: colour tokens, typography, spacing, radius, components, logo rules, accessibility and the "Avoid" list. Follow it exactly. All colour and spacing values are in its §6 CSS variables.

Assume **today is Sunday 11 Oct 2026** for all deadline calculations.

## User stories

These cover the whole site. Use them to decide what gets the most visual weight on each screen.

1. As a final-year student, I want to see which deadlines are coming up this week, so I don't miss an application.
2. As a computer science student, I want to filter by my major and by internships, so I only see roles I can apply for.
3. As a student browsing on my phone between classes, I want to scan opportunities quickly, so each listing has to be readable at a glance.
4. As a student comparing options, I want to see a role's requirements and majors before I leave the site.
5. As a student ready to apply, I want a quick way to get to the employer's application.
6. As a student who isn't sure where to start, I want to see roles with no fixed deadline, so I know I can apply any time.

## Global layout

- **Header:** the BEC logo (`BEC-logo-trimmed.svg`, 64px) on the left. Nav: **Calendar · Opportunities · About**, with the current page underlined 2px in `primary`. Only Opportunities works in this stage.
- **Footer:** `surface` ground, the serration mark once along its top edge, the logo at 96px. Link groups: **Find** (Calendar, Opportunities) and **About** (About us, Contact, which is a `mailto:` link). A small line: "© 2026 Bahrain Early Careers".

## Opportunities page

- `h1`: "Opportunities", with a one-line intro under it.
- **Search panel**, full width above the list (theme doc: "Search panel and filter dropdowns"):
  - A search field that searches position, company, major and skills.
  - Under it, one row of multi-select filter dropdowns with result counts, then a "Clear filters" link at the end:
    - **Type:** Internship, Full-time, Graduate programme
    - **Industry:** the company sectors in the data
    - **Major:** the majors in the data, with a search field inside the menu
- **Results header:** the result count ("20 opportunities") at the start, and a **Sort** dropdown at the end with **Soonest deadline** (default; no-date items go last), **Position A–Z** and **Company A–Z**. Active filters show underneath as removable chips.
- **Empty state:** "No opportunities match your search", with a "Clear filters" link.
- **Opportunity rows**, not cards (theme doc: "Opportunity row"). One column, separated by hairline dividers, with no box around each row. Each row shows **only these fields**, in this order:
  1. Company logo circle with **initials**. No company logo files exist, but design the slot so a real logo can drop in later.
  2. Position (`row-title`, bold), with the company name under it (`ink-muted`)
  3. Meta row: location · type
  4. Deadline block: a `DEADLINE` label (or "TODAY" / "TOMORROW" when it applies), the date ("Tue 20 Oct 2026") and a status badge. For no-date items, show "No fixed deadline" in place of the date, with no badge.
  5. A dark **"Apply ↗"** button at the very end (theme doc: "Row Apply"), which opens the employer's link in a new tab.
- Clicking anywhere on a row except the Apply button opens the detail panel.

## Opportunity detail panel

A side panel over the dimmed list, with `shadow-overlay`. It closes with ✕ or Esc and returns focus to the row. Order of content:

1. `label` eyebrow with the type ("GRADUATE PROGRAMME")
2. `h2` position
3. Company name · location
4. The coral primary button **"Apply on employer site ↗"**
5. **Fact box** (`surface`): DEADLINE (date and badge) · TYPE · LOCATION · INDUSTRY · MAJORS
6. **Requirements:** a ✓ checklist, one item per line
7. **About the role:** the description paragraphs (max 720px wide)
8. The "Apply on employer site" button repeated at the end

## Data

Use `dummy-data.json` for all content. Don't invent other opportunities or companies.

- Each opportunity belongs to exactly one company (`company_id`), and a company can have many opportunities.
- Show `type` as: `gtp` → "Graduate programme", `full_time` → "Full-time", `internship` → "Internship".
- `deadline_date: null` means "No fixed deadline".
- `major: ["Any major"]` means the role is open to all majors:
  - Show "Any major" in the detail panel.
  - Don't list "Any major" as an option in the Major filter.
  - Include these roles in the results for every major selected.
- **Never show** opportunities with `hidden: true` or a deadline before today. In the file, these are #21 and #22, so 20 opportunities are visible.
- The Industry filter uses the company's `sector`. The Major filter uses the values in each opportunity's `major` list.

## References (attached screenshots)

These are inspiration only. Where a screenshot and the theme doc disagree, **the theme doc wins**.

- **`ref-legal-cheek-list.png` is the main reference for the overall feel.** Borrow:
  - one main column of rows separated by thin dividers, with no boxes
  - each row leading with a name, with one key fact at the end
  - quiet, plain controls
  - lots of white space

  Don't copy its underlined headings, grey sidebar or the promo line above the list.
- **`ref-deadline-list.png`.** Borrow:
  - the row rhythm: a bold heading, a lighter line under it, a thin divider between rows
  - the compact dark Apply button at the end of each row
  - "Today" / "Tomorrow" as a word near the date

  Don't copy:
  - the date column at the start (our deadline goes at the end)
  - the company-first headings (ours are role first)
  - the cyan date colour
  - relative dates shown without the actual date
- **`ref-opportunity-search.png`.** Borrow:
  - the search panel, with a full-width search field above a row of filter dropdowns and "Clear filters" at the end
  - initials in place of company logos

  Don't copy its cream background, the 3-column card grid, or the duration and eligibility lines (those fields don't exist).

## Scope

- Desktop (1440px) only in this stage.
- Don't add Home or Employers pages, or Save, Share or "Add to calendar" buttons.
- Deadlines are date only (no time). English only, with start/end alignment so Arabic RTL can be added later.

## Before you finish

- Coral stays around 5% of the screen: the logo, the serration mark, the coral primary button, links and urgent badges. Row Apply buttons are dark `ink`, not coral.
- Only one coral primary button is visible at a time.
- Every deadline status has a word, an icon and the actual date, never colour alone.
- Every tappable element is at least 44px and has a visible focus ring.
