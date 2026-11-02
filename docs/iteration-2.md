# Iteration 2 — Remaining scope

This doc compares the full feature list for BEC against what V1 delivered. V1 is described in [v1-Fe-only.md](v1-Fe-only.md). Everything not yet built is grouped here into Iteration 2 work and future enhancements.

V1 is front end only. It runs on dummy data and "today" is fixed at a set date. Most of Iteration 2 needs a back end first.

## Status of the original feature list

| Feature | Status | Notes |
|---|---|---|
| Calendar showing all upcoming deadlines | Done | Month view with deadline dots |
| Calendar matches Bahrain weekends and public holidays | Not done | Fri and Sat aren't marked as weekend, and no holidays are shown |
| Entries for each application | Done | |
| Each entry links to the external application | Done | Apply buttons open the employer's page |
| Each entry links to an individual company page | Not done | Company names are plain text and company pages don't exist |
| General opportunities page with major and type filters | Done | Industry filter, search and sort were also added |
| Legal pages | Not done | |
| About page | Partly done | The page exists but holds placeholder (lorem ipsum) text |
| Subscribe for weekly reminders of applications closing within 7 days, sent every Thursday | Not done | |
| Links to LinkedIn and Instagram | Not done | |
| Responsive on tablet and mobile | Done | |
| Admin page | Not done | See [Admin](#3-admin) |
| Contact page or form | Partly done | There's only a `mailto:` link in the footer |
| Opportunities hidden after their closing date | Partly done | V1 hides past deadlines in the browser, on dummy data only |
| Admins can extend a closing date | Not done | Part of admin editing |
| Opportunities with no closing date | Done | Shown as "Rolling applications" |
| Favourites with updates | Future | |

## Iteration 2 work

The groups are in a suggested build order. Groups 1–3 depend on each other. Group 4 can run in parallel once group 1 exists.

### 1. Back end and data

Most of what follows depends on this group.

- A database and API to replace `data/dummy-data.json`. Start from the existing model in [data-models.md](data-models.md).
- Use the real current date instead of the date fixed in V1.
- Hide opportunities automatically once their closing date has passed. Do this on the server, not only in the browser.
- Extend the data model with:
  - **Company:** a blurb or description, plus logo, LinkedIn and other fields as needed for the company page.
  - **Admin users:** the `created_by` and `updated_by` fields already point to admin users, but that table hasn't been defined.
  - **Approval state:** so a change can wait for a second admin to approve it (see Admin).
  - **Subscribers:** an email address and subscription date, plus unsubscribe handling.
  - **Contact messages**, if the contact form stores what people send rather than only emailing it.

### 2. Public site additions

- **Bahrain weekends and holidays on the calendar**
  - Mark Fri and Sat as the weekend.
  - Show Bahrain public holidays.
  - Islamic holidays move every year, so the team needs a way to keep the holiday list up to date.
- **Company pages**
  - One page per company, showing its name, blurb, industry and website.
  - Include the company's current opportunities.
  - Link to the page from the company name in opportunity rows and in the detail panel.
- **Legal pages**
  - Privacy policy and terms of use, at a minimum.
  - Link them from the footer.
  - The privacy policy needs to cover subscriber emails.
- **About page copy**
  - Replace the placeholder text with real content.
- **Contact page or form**
  - Replace the footer `mailto:` link with a page that has a form.
  - The FAQ promises a reply "within one working day", so messages have to reach someone who will answer them.
- **Social links**
  - Add LinkedIn and Instagram links to the footer, and possibly to the header or mobile menu.
- **Subscribe form**
  - Add an email sign-up, for example in the footer, on the calendar, or both.
  - Include a confirmation step and an unsubscribe link.

### 3. Admin

An area for admins only, behind a login.

- **Opportunities**
  - Add, edit and hide opportunities.
  - Extend a closing date when an employer allows it.
  - Mark an opportunity as having no closing date.
- **Companies**
  - Add and edit companies, including their blurbs.
- **Two-admin approval**
  - A new opportunity or a change only goes live once a second admin has approved it.
  - Admins need to see the changes waiting for approval and be able to approve or reject them.
- **Subscribers**
  - View the newsletter subscribers, and ideally export the list.
- **Admin accounts**
  - Support more than one admin.

### 4. Weekly reminder emails

- Every Thursday, email each subscriber the opportunities that close within the next 7 days.
- This needs a scheduled job and an email provider.
- Every email needs an unsubscribe link.
- Decide what to send when nothing closes that week: skip the email, or send a "nothing this week" note.

## Future enhancements (after Iteration 2)

- **Favourites:** users save opportunities and get updates about them, such as a reminder before the deadline or a notice when the date is extended. This needs user accounts for the public site, which Iteration 2 doesn't include.
