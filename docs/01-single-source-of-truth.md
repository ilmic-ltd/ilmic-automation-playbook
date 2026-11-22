# 01 · Single source of truth

## The problem

A typical small consultancy receives enquiries from a website form, Meta Lead Ads, WhatsApp, email, phone and referrals. Each lands somewhere different. Nobody can answer "how many leads did we get this week, and how many paid?"

## The pattern

- **One lead table.** Every channel writes a row to the same table. Notion, HubSpot, Airtable or Postgres all work; the choice matters less than having only one.
- **Other tools are views or mirrors.** If HubSpot and Notion both exist, decide which one is the master. The other is read-only and synced one way.
- **A `source` field on every row.** `web_form`, `meta_lead_ad`, `whatsapp`, `email`, `referral`, `phone`. Without it you cannot see which channel pays.
- **De-duplicate on the way in.** Normalise phone numbers to E.164 (`+447…`, `+90…`) and lower-case emails before matching. Merge into the existing row and log the new touch, rather than creating a second lead.
- **Brand or service as a field, not a separate database.** Multi-brand firms keep one table and filter by `brand`.

## Rules of thumb

| Rule | Why |
|---|---|
| Forms never write directly to two places | Two writes drift apart within a month |
| Every row has an owner | Unowned leads are nobody's job |
| Status values are a fixed list | Free text cannot be reported on |
| Timestamps for every stage change | You cannot measure speed without them |

## Minimum fields

See [`templates/lead-schema.json`](../templates/lead-schema.json).
