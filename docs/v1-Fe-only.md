# V1 — Front end only

V1 is a clickable prototype with dummy data. It exists so the team can judge the design and the look and feel of BEC before any back end is built.

## Running it

- Open `index.html`. It redirects to the Calendar page, which works as the home page.
- Every page loads its content from `data/dummy-data.json` (10 companies, 22 opportunities).
- "Today" is fixed at **Fri 30 Oct 2026**, so the deadline labels and calendar always look the same.
- Opportunities are left out everywhere if they are marked `hidden` or their deadline is before "today".

## Shared across all pages

**Breakpoints:** mobile below 600px, tablet 600–1023px, desktop 1024px and up.

**Header**
- BEC logo on the left. It links to the Calendar.
- Desktop and tablet: nav links for Calendar, Opportunities and About. The current page is underlined in the accent red.
- Mobile: a hamburger button opens a full-screen menu with the logo, a close (X) button and the same three links. Escape closes it, and keyboard focus stays inside the menu while it is open.

**Footer**
- Logo and two link groups:
  - **Find:** Calendar, Opportunities
  - **About:** About us, FAQ, Contact (a `mailto:` link to hello@bahrainearlycareers.com)
- © 2026 Bahrain Early Careers

**Opportunity detail panel** (`DetailPanel.dc.html`, used on Calendar and Opportunities)
- Opens when you click any opportunity row, anywhere on the row except the Apply button.
- Desktop and tablet: a 720px panel opens on the right side of the screen over a dimmed backdrop. A close (X) button sits at the top right.
- Mobile: the panel fills the screen and has a Back button at the top left.
- Contents, from top to bottom:
  - Type (Internship / Full-time / Graduate programme)
  - Position title
  - Company
  - **Apply on employer site** button (opens a new tab)
  - Fact list: Deadline, Location, Industry, Majors
  - **Requirements:** a bulleted list
  - **About the role:** the description paragraphs
- The Deadline shows "Today" or "Tomorrow" in red, otherwise a date in dd/mm/yyyy. Opportunities with no deadline show "Rolling applications".
- You can close the panel with the close or Back button, by clicking the backdrop, or with Escape. Focus then goes back to the row you opened it from.

**Apply buttons:** every Apply button links to the employer's own page and opens in a new tab. Nobody applies through BEC.

## Calendar page (`Calendar.dc.html`)

**What's visible**
- Page title: **Deadlines**
- **Month calendar card**
  - Header: the month and year, plus previous month, next month and **Today** buttons.
  - Weekday row (Sun–Sat). The weekday of the selected day is shown in red.
  - Day grid. Days from the neighbouring months appear greyed out and can't be clicked.
  - Today's date is shown in red. Past days are grey. The selected day has a light red tint.
  - A day with deadlines shows a dot. When more than one deadline falls on that day, a count appears next to the dot.
  - A legend under the grid reads "Dots mark application deadlines."
- **No-deadline note** under the card, e.g. "3 opportunities have no fixed deadline. View all opportunities". The link goes to the Opportunities page.
- **Selected-day list**
  - Heading with the selected date (e.g. "Fri 30 Oct").
  - One row per opportunity whose deadline is that day: position title, company and an **Apply** button.
  - When the day has no deadlines, it shows "No deadlines for this day".

**Layout**
- Desktop: the calendar is on the left and the selected-day list on the right. Their headers line up.
- Tablet and mobile: the selected-day list sits below the calendar.

**Flow**
1. The page opens on October 2026 with today (30 Oct) selected, so today's deadlines show straight away.
2. The arrows change the month. **Today** jumps back to October 2026 and selects 30 Oct.
3. Clicking a day selects it, and the list updates to that day's deadlines.
4. Clicking a row opens the detail panel. Apply goes straight to the employer.
5. To see opportunities that have no deadline, the user follows the "View all opportunities" link.

## Opportunities page (`Opportunities.dc.html`)

**What's visible**
- Page title **Opportunities**. A **Sort by** dropdown sits on the same line:
  - Soonest deadline (default)
  - Position A–Z
  - Company A–Z
- **Search bar:** "Search by role, employer, major or skill". It matches position title, company, majors and requirements. Every word you type has to match.
- **Filters** (desktop and tablet): three dropdown buttons with checkbox lists.
  - **Type:** Internship, Full-time, Graduate programme
  - **Industry:** the company's sector
  - **Major:** has its own search box inside the dropdown, e.g. "No majors match 'xyz'"
  - Each button label shows what is selected: "All types" when nothing is picked, the option name when one is picked, or "Types · 2" for several.
  - Options that would give zero results are greyed out and disabled.
  - Opportunities open to "Any major" always match the Major filter.
- **Filters** (mobile): one **Filters** button with a badge counting the active filters. It opens a full-screen sheet with all three filter groups, a **Clear filters** button, a close (X) button and a **Show N results** button at the bottom.
- **Clear filters** appears next to the filters once any filter or search text is active. It also clears the search.
- **Filter chips:** each active filter appears as a removable chip under the search bar.
- **Results**, in two sections:
  - **Rolling applications:** opportunities with no deadline. Each row shows title, company and Apply.
  - **With a closing date:** each row shows the deadline (dd/mm/yyyy, or "Today" or "Tomorrow" in red), title, company and Apply. On desktop and tablet the deadline is a column on the left. On mobile it sits above the title.
  - The sort order applies inside each section.
- **Empty state:** "No opportunities match your search", with a **Clear filters** button.

**Flow**
1. The page opens with every current opportunity, sorted by soonest deadline.
2. The user narrows the list with search, filters or both. The results, chips and option counts update as they go.
3. The user removes a single filter with its chip, or resets everything with Clear filters.
4. Clicking a row opens the detail panel. Apply goes straight to the employer.

## About page (`About.dc.html`)

- Title **About us**, followed by four paragraphs of lorem ipsum placeholder text. The real copy is still to be written.
- It has the shared header and footer. There is nothing interactive on the page.

## FAQ page (`FAQ.dc.html`)

- Reached from the footer only. It is not in the main nav.
- Title **Frequently asked questions**, with four questions and answers:
  - Do I apply through BEC? (No, Apply goes to the employer.)
  - Is it free? (Yes.)
  - What does "Rolling applications" mean?
  - I found a listing that's closed or wrong. (Email us.)

## Review helpers

- **`Responsive Review.dc.html`** shows each page side by side in iframes at desktop (1440), tablet (768) and mobile (375) widths, including the main open states. It is a review tool, not part of the site.
- **`?state=` URL parameters** open a page in a specific state:
  - `Calendar.dc.html?state=day`: selects Sun 8 Nov 2026
  - `Calendar.dc.html?state=panel`: opens the detail panel
  - `Opportunities.dc.html?state=panel`: opens the detail panel
  - `Opportunities.dc.html?state=filters`: opens the mobile filters sheet
  - `Opportunities.dc.html?state=empty`: shows the empty state
- **Known mismatches in the review page.** Some labels in Responsive Review are out of date:
  - "20 Oct selected": `state=day` actually selects 8 Nov.
  - "Mobile · Agenda": the Calendar no longer has an agenda view.
  - The mobile "Menu" frame uses `?state=menu`, which the Opportunities page doesn't handle, so it shows the plain list.
