# Data models

Fields marked *(iteration 2)* or *(future)* aren't in V1 or `data/dummy-data.json` yet. Scope for each iteration is in [iteration-2.md](iteration-2.md).

## Relationships

- each opportunity belongs to a company
- each company has multiple opportunities
- a single opportunity belongs to a single company, so relationship between them is one-to-many 
    - where each opportunity can only belong to one company, but a company can have multiple opportunities
- so an opportunity cannot be company-less
- every `created-by`, `updated-by`, `requested_by` and `reviewed_by` field is a FK to an admin *(iteration 2)*
- each admin can create or review many changes, but a change can't be reviewed by the admin who requested it *(iteration 2)*
- each user can favourite many opportunities, and each opportunity can be favourited by many users, so the relationship is many-to-many through favourite *(future)*

## V1 models

- company data fields:
    - company_id
    - name
    - sector
    - company-url
    - created-at
    - created-by (FK)
    - updated-at
    - updated-by (FK)
    - blurb — short description shown on the company page *(iteration 2)*
    - logo_url — optional, for the company page *(iteration 2)*
    - linkedin_url — optional, for the company page *(iteration 2)*

- opportunity data fields:
    - opportunity_id
    - company_id (FK)
    - title/position
    - description
    - requirements (skillset)
    - major 
    - type (full-time, internship, GTP)
    - location
    - opportunity-link
    - deadline-date — empty for rolling applications; admins edit it when an extension is given
    - created-at
    - created-by (FK)
    - updated-at
    - updated-by (FK)
    - hidden — set by admins, or automatically once deadline-date has passed

## Iteration 2 models

- admin data fields:
    - admin_id
    - name
    - email
    - password_hash (or an external login ID, depending on how auth is done)
    - is_active — so an admin can be removed without breaking the created-by/updated-by history
    - created-at

- change request data fields (for two-admin approval):
    - change_id
    - entity_type (company, opportunity)
    - entity_id (FK) — empty when the change creates a new record
    - action (create, update, hide)
    - proposed_data — the new field values
    - status (pending, approved, rejected)
    - requested_by (FK)
    - requested_at
    - reviewed_by (FK)
    - reviewed_at
    - the live company/opportunity record only changes once the request is approved

- subscriber data fields (weekly Thursday reminders):
    - subscriber_id
    - email (unique)
    - confirmed — true once they click the confirmation email
    - subscribed_at
    - confirmed_at
    - unsubscribed_at — empty while subscribed
    - unsubscribe_token — used in the unsubscribe link in each email

- contact message data fields (only needed if the contact form stores messages rather than just emailing them):
    - message_id
    - name
    - email
    - message
    - created_at
    - handled — so admins can see what still needs a reply

- holiday data fields (only needed if holidays are stored rather than pulled from an external source):
    - holiday_id
    - name
    - date
    - created-by (FK)
    - updated-by (FK)

## Future models

- user data fields (public site accounts, needed for favourites):
    - user_id
    - email (unique)
    - name
    - password_hash (or an external login ID)
    - created_at

- favourite data fields:
    - user_id (FK)
    - opportunity_id (FK)
    - created_at
    - the pair user_id + opportunity_id is unique
    - updates to a favourite (deadline reminder, date extended) are sent based on these rows
