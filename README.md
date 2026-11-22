# ILMIC Automation Playbook

How [ILMIC](https://ilmic.co.uk) builds automation, CRM and AI systems for small UK service businesses.

These are the patterns we use on our own group of consultancies every day. They are written for owners and small teams with limited budget, not for enterprises. No client data, credentials or private infrastructure details are included.

## The one-line version

> Capture every lead in one place, reply within a minute, score and route it, book a paid consultation, chase until a clear yes or no, and make every failure visible.

## Contents

| # | Pattern | Problem it solves |
|---|---|---|
| 01 | [Single source of truth](docs/01-single-source-of-truth.md) | Leads scattered across forms, inboxes and spreadsheets |
| 02 | [Lead pipeline](docs/02-lead-pipeline.md) | Slow replies, no scoring, no follow-up |
| 03 | [Error handling](docs/03-error-handling.md) | Workflows that fail silently |
| 04 | [Model routing](docs/04-model-routing.md) | Paying top-model prices for simple jobs |
| 05 | [GDPR and regulated advice](docs/05-gdpr-and-regulated-advice.md) | Automation that crosses legal lines |
| — | [Lead record schema](templates/lead-schema.json) | A starting schema for the central lead table |

## Principles

1. **Fix the biggest leak first.** Measure where enquiries die, then automate that step only.
2. **Many forms, one database.** Every channel writes to the same table with a `source` field.
3. **Humans approve, machines prepare.** Drafts, summaries and scores are automatic; client-facing advice is not.
4. **Fail loudly.** Every workflow has an error path that a person sees the same day.
5. **Boring beats clever.** Prefer a tool the team already knows over a better one nobody maintains.
6. **Write it down.** Every workflow has an owner, a purpose line and a runbook link.

## Typical stack

n8n (self-hosted) · Notion or HubSpot · Jotform / Meta Lead Ads · Twilio WhatsApp · Brevo · Google Calendar · Stripe · Telegram for internal alerts.

The patterns are tool-agnostic: swap n8n for Make or Zapier, Notion for Airtable or Postgres.

## Licence

[MIT](LICENSE). Use the patterns freely. If you would like help applying them, start with the SME Automation Audit at [ilmic.co.uk](https://ilmic.co.uk).
