# Suggestions

Notes from reviewing `data-models.md`, `v1-Fe-only.md` and `bahrain-early-careers-theme-and-color-palette.md` together.

**Decided for v1** (built into `claude-design-prompts/` and the theme doc):
- Pages: Calendar (landing), Opportunities, Opportunity detail (side panel), About. No Home or Employers page.
- Clicking an opportunity row opens a detail side panel (full screen on mobile).
- Company logo added, with an initials fallback. No eligibility, duration, start date or pay.
- Past-deadline opportunities are hidden everywhere (no "Closed" status).
- Opportunity list: divider rows (no cards), role first, deadline at the end, a dark `ink` "Apply ↗" button on every row.
- Filters: dropdowns inside a search panel (a "Filters" sheet on mobile). White page background.
- "Today" / "Tomorrow" shown above the date, never instead of it.
- "Any major" is shown as text, isn't a filter option, and matches every major filter.

---

## 1. Where the docs disagree

| Topic | v1 plan says | Theme doc says | Suggestion |
| --- | --- | --- | --- |
| Pages | Calendar, Opportunities list, About | Home, Opportunities, Detail, Calendar, Employers, About | Decide on v1 scope before prompting (see questions). Don't put "Employers" in the nav if there's no page for it. |
| Card fields | employer name, position, type, deadline or N/A | logo, title, employer, location · type · duration, eligibility line, deadline block | Show only fields the data model has. Duration and eligibility aren't in the model yet. |
| Detail fact box | — | Deadline, eligibility, location, type, duration, start date, pay | Same: these fields aren't in the model. Either add them (see §2) or trim the fact box. |
| Below the calendar | 2 tabs: top 5 upcoming, no-date | Selected day's list | Use 3 tabs: **Selected day** (default when a day is clicked), **Next 5 deadlines**, **No deadline**. |
| Deadline | `deadline-date` (date only) | "Deadline shows date **and** time" | Show the date only for v1, or add `deadline-time`. |
| No-date opportunities | "N/A" | "Rolling" status | Choose one wording. "No fixed deadline" is clearer than "N/A". "Rolling" is accurate only if the employer really reviews applications continuously. |
| Save / Share buttons | no accounts in v1 | Secondary "Save" on cards and detail | Drop "Save" for v1. With no accounts there's nothing to save to. Keep "Share" (copy link) or remove it. |
| Header search icon | search bar on the list page | search icon in header | On v1, make the header icon go to the Opportunities page with search focused, or remove it. |
| Footer links | — | "List an opportunity", "Contact" | No pages exist for these. Use `mailto:` links or remove them for v1. |

Typos in `v1-Fe-only.md`: "employee name" should be "employer name", and "univeristy" should be "university".

---

## 2. Data model

**Company**
- Add `logo_url` (nullable). The design uses 48px logo circles; fall back to initials on `surface` when it's empty.
- Add `description` (short, 1–2 sentences) if an Employers page is added later.
- Make `sector` a fixed list (lookup table or enum) so the industry filter has clean values, for example Banking & finance, Energy, Telecoms, Consulting, Government, Aviation, Technology, Healthcare.

**Opportunity**
- `major` should be **many-to-many**: one opportunity usually accepts several majors. Use an `opportunity_major` join table and a `major` lookup table. The major filter needs this too.
- `requirements`: store as a list (or a join table to `skill`) rather than free text, so the UI can show a checklist.
- `type`: enum `full_time | internship | graduate_programme`. In the UI, spell GTP out as **"Graduate programme"**, because students may not know the acronym.
- `deadline_date`: nullable means "no fixed deadline". If you want to tell "rolling" apart from "unknown", add `deadline_type` (`fixed | rolling | unknown`).
- `location`: a fixed list (Manama, Seef, Muharraq, Riffa, Sitra, Isa Town…) plus `work_mode` (`on_site | hybrid | remote`).
- Optional, if the design keeps them: `eligibility` (e.g. nationality, graduation year), `duration`, `start_date`, `paid` (boolean) or `pay`.
- Add `published_at` so new listings can be marked "New".
- Status (Open / Closing soon / Urgent / Closed) should be **derived from `deadline_date`**, not stored.
- `hidden`: fine for admin later; the public UI never shows hidden rows.
- `created_by` / `updated_by` point to a `user` (admin) table that isn't defined yet. Add it to the ERD even if it's out of scope for v1.
- Remove the trailing empty `-` bullet at the end of the opportunity fields.

**ERD:** company 1 —< opportunity >—< major (through opportunity_major); user 1 —< company / opportunity (created_by, updated_by).

---

## 3. UX

**Opportunities list**
- Default sort: **soonest deadline**, with no-date items after dated ones and closed items last.
- Say what "sort alphabetically" sorts by: position title or company name (offer both, or pick one).
- Search should match title, company name, major and skills.
- Show the result count ("24 opportunities") and a list of active filters with ✕ to remove each one.
- Design an **empty state** ("No opportunities match these filters" plus a "Clear all filters" link).
- Decide whether closed opportunities are hidden or shown at the end. Showing them at the end tells students "this comes back every year."

**Calendar**
- Add previous/next month arrows and a "Today" button.
- Plot each opportunity on its **deadline date** (the only date in the model).
- "Next 5 deadlines" should skip closed items and end with a "View all by deadline" link to the list page, already sorted.
- On mobile, use the agenda/list view by default, as the theme doc suggests.

**About page** (instead of generic filler)
- What BEC is and who it's for.
- How listings are collected and checked.
- A disclaimer: "We're not the employer. Applications happen on the employer's site."
- Contact email.

**Trust**
- A "Last checked 9 Oct 2026" line on each opportunity helps students trust that a listing is still live.

---

## 4. Getting the most out of Claude Design

- Attach the **theme doc** and the **logo PNG** with the prompt. The prompt sets page structure and data; the theme doc is the source of truth for visual style.
- Ask for one page at a time after the first pass, so you can review in small steps.
- Ask for **desktop (1440), tablet (768) and mobile (375)** of every page, because the plan calls for all three.
- Dummy data dated around **today (Oct 2026)** so the calendar has dots and every deadline status appears.
- Before sharing with Eman, check against the theme doc's "Avoid" list (too much coral, more than one primary button per view, colour-only status).

---

## 5. Doc changes for better Claude Design output

The main risk is **conflicting instructions**. Claude Design reads the theme doc and the prompt together. Wherever they disagree, it may follow either one, even with the "v1 overrides" section. Give each doc one job:

- **Theme doc = how things look:** tokens, type, components.
- **Prompt = what goes on each page.**

### 5.1 Theme doc: remove page-level content that clashes with v1 — ✅ done

| Where | Change |
| --- | --- |
| §1 "Main sections" (line 15) | Delete, or change to "Calendar · Opportunities · About" |
| §3 status table, "Open" row (line 79) | "Rolling" → "No fixed deadline"; mark the "Closed" row *(future, not in v1)* |
| §4 writing rules (line 120) | **Fix the date example:** 14 Nov 2026 is a **Saturday**, so "Fri 14 Nov" → "Sat 14 Nov". A wrong example teaches wrong weekdays. |
| §10 Buttons (line 265) | Remove "Save", "Share", "Add to calendar" from the secondary-button examples |
| §10 Site header (lines 260–261) | Remove "Employers" and the search icon |
| §10 Opportunity card (lines 280–284) | Remove "duration", the "eligibility summary" line, the "Closed" variant and the "Save button" note |
| §10 Calendar (line 291) | Match the v1 tabs: Next 5 deadlines / No fixed deadline, plus the selected day |
| §10 Detail panel (lines 295–298) | Remove "Save" and "date **and** time"; fact box rows → DEADLINE · TYPE · LOCATION · INDUSTRY · MAJORS; Eligibility checklist → **Requirements** checklist |
| §10 Footer (line 305) | Groups → Find (Calendar, Opportunities), About (About us, Contact) |
| §14 Suggested pages | Delete it. The page list lives in the prompt. |

Once these are done, the "v1 overrides" section in the prompt can shrink to almost nothing.

### 5.2 Add what Claude Design would otherwise guess

- **Icon set:** name one, for example "Lucide icons, 20px, 1.5px stroke, `ink-muted` by default". The status icons (alert-circle, clock, check-circle) are already Lucide names.
- **Serration mark as SVG:** add a ready-made SVG snippet to §9. Otherwise each page may draw the five triangles differently.
- **Logo as a vector:** if an SVG exists, attach it. Claude Design can't redraw the badge cleanly. Note: the logo PNG isn't in this project folder yet.
- **Rough wireframes:** an ASCII sketch of the opportunity card (desktop and mobile) and the calendar page layout gives Claude Design an exact structure to follow instead of interpreting prose.
- ✅ **Reference site:** Legal Cheek "The Firms Most List" was added to theme doc §1 and to the prompt.

### 5.3 Trim duplication — ✅ done (§6 is the single source; old §12 style sheet removed)

§6 (CSS variables), §12 (compact style sheet) and §3/§5 repeat the same values. Keep **§6 as the single source of values** and either delete §12 or label it "summary, values from §6". When you change a colour later, you only have to change it in one place.

### 5.4 Split the prompt into stages

Four views × three breakpoints is 12 screens in one go, and detail quality drops. Run it as:
1. Design-system check plus the **Opportunities page and detail panel** (desktop). Review.
2. The same at tablet and mobile.
3. **Calendar** at all three sizes.
4. **About**, then a consistency pass across everything.

### 5.5 Move dummy data into its own file

Put the companies and opportunities in `dummy-data.json`, shaped like the data model, and attach it. This keeps the prompt short, and the same file can seed the real front end later.

### 5.6 `data-models.md`

Don't attach it to Claude Design; the prompt already summarises it. Do update it with `logo_url` and many-to-many majors so it matches what the design shows.
