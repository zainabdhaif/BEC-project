# Stage 3 — Calendar page (all three sizes)

> **Attach:** `ref-calendar.png`
>
> **Check before Stage 4:**
> - Today (11 Oct) stands out.
> - 20 Oct shows "●3".
> - Clicking a day adds its tab.
> - The rows under the grid match the Opportunities page.
> - The mobile agenda view reads well.

---

Now design the **Calendar page** at desktop (1440px), tablet (768px) and mobile (375px). It is the site's **landing page**: the logo links here, and the Calendar nav link is now active. Reuse the header, footer, opportunity row and detail panel from the earlier stages.

## Page content

- `h1`: "Deadlines calendar", with a one-line intro under it.
- **Month container** (theme doc: "Deadline calendar"):
  - Showing **October 2026**, with the month name at the start and previous/next arrows and a "Today" button at the end.
  - The week starts on **Sunday**. Day names use the `label` style.
- **Deadline dots:** each opportunity appears on its **deadline date** as a coral dot, with a count when a day has more than one ("●3").
  - Days before today show no dots, because past-deadline opportunities are hidden.
- **Today (11 Oct)** has a `brand-cream` fill and an `ink` ring.
- **Selected day:** `ink` fill with a white number. Every day has an accessible name, such as "20 October, 3 deadlines".
- **Legend:** one line under the grid, "● Dots mark application deadlines."
- **Tabs below the month:**
  - **Next 5 deadlines:** the 5 soonest upcoming opportunities as opportunity rows, ending with a "View all by deadline" link to the Opportunities page sorted by deadline.
  - **No fixed deadline:** every opportunity without a deadline date, as opportunity rows.
  - When the user clicks a day, a new tab appears first and becomes active. It's labelled with the day, such as "Tue 20 Oct · 3", and lists that day's opportunities.
- The rows are the same as on the Opportunities page, with the Apply button at the end. Clicking a row opens the same detail panel.

## Sizes

- **Desktop and tablet:** the month grid, with the tabs underneath.
- **Mobile:**
  - Open in an **agenda view**: upcoming deadlines grouped by week ("This week", "Next week", then week by week), using the mobile opportunity row.
  - A toggle at the top switches between "Agenda" and "Month". The month grid must fit 375px with day cells at least 44px tall.
  - The "No fixed deadline" list stays available as a tab below.

## Reference

**`ref-calendar.png`** is inspiration only. Borrow:
- the calendar in its own rounded container
- the month name at the start, with arrow buttons at the end
- rounded day cells
- the one-line legend under the grid

Don't copy its cream background, the week starting on Monday, or the tinted deadline cells. Use the theme doc's white page, Sunday start and coral dots.
