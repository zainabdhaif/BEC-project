# Stage 2 — Opportunities page and detail panel (tablet and mobile)

> **Attach:** nothing new. Use the same Claude Design project as Stage 1.
>
> **Check before Stage 3:**
> - At 375px, a row is readable at a glance: role, company, date, badge and Apply, with nothing cramped.
> - The filter sheet opens and its "Show N results" button stays visible.
> - Nothing scrolls sideways.

---

Now design the **tablet (768px)** and **mobile (375px)** versions of the Opportunities page and the detail panel. Keep everything from the desktop version and change only what's listed here.

## Header

- **Tablet:** the same as desktop (80px bar, 64px logo, three nav links).
- **Mobile:** a 64px bar with the 48px logo on the left and a menu icon on the right. The menu opens a full-screen sheet with the links at 18px.

## Search panel

- **Tablet:** the search field stays full width. The three filter dropdowns and "Clear filters" stay in one row under it, wrapping to a second line only if they don't fit.
- **Mobile:** the search field stays. The dropdowns are replaced by a secondary **"Filters"** button. It opens a full-screen sheet with:
  - Type, Industry and Major as checkbox lists with counts (the Major list has a search field)
  - a "Clear filters" link
  - ✕ to close
  - a sticky **"Show N results"** primary button at the bottom
- **Results header:** the count and Sort stay on one line. On mobile, Sort can shrink to "Sort ▾".

## Opportunity rows

- **Tablet:** the same layout as desktop, with the deadline block and Apply button at the end of the row.
- **Mobile:**
  - Logo circle 32px.
  - Role (max 2 lines), then company, then location · type.
  - Under those, one line with the deadline block (label, date, badge) and the Apply button at the end of that line.
  - `space-4` padding above and below each row.

## Detail panel

- **Tablet:** a side panel over the list, covering most of the screen width, with the dimmed list visible beside it.
- **Mobile:** a full-screen view with a back arrow at the top. In the fact box, labels stack above their values.

## Footer

- **Mobile:** the link groups stack in one column under the logo.

## Spacing and type

- Gutters are `space-5` on tablet and `space-4` on mobile.
- On mobile, `h1` is 28/36 and `h2` is 22/30.
- Body text never goes below 16px, and metadata never below 14px.

## Before you finish

- Every tappable element, including each row's Apply button and the menu icon, is at least 44px, with at least 8px between neighbouring targets.
- No horizontal scrolling at 375px.
- The filter sheet and detail panel close with Esc and keep focus inside while open.
