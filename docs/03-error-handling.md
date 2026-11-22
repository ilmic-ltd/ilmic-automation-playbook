# 03 · Error handling

## The problem

Automations fail silently. A token expires on Friday night and nobody notices that leads stopped arriving until Tuesday.

## The pattern

Every workflow uses the same error path:

```
Any node fails
   └─► Error Trigger
         ├─► write a row to a "Workflow Errors" table
         │      (workflow, node, message, time, execution link, severity)
         └─► send one internal alert (Telegram / Slack)
```

In n8n, build this once as an **error workflow** and set it as the error workflow of every production workflow.

**Ready-made template:** [ilmic-ltd/n8n-error-handler](https://github.com/ilmic-ltd/n8n-error-handler) implements this pattern (Notion log, Telegram alert, personal-data clean-up, repeat grouping).

## Rules

- **No client personal data in error messages or alerts.** Log record IDs, not names, phone numbers or emails.
- **De-duplicate alerts.** Same workflow + same error within an hour = one alert with a counter.
- **One daily brief.** Low-severity errors roll up into a morning summary instead of fifty pings.
- **A heartbeat for critical flows.** If lead intake has not run for N hours during business time, alert, even with no error.
- **Every workflow has an owner** who acknowledges and closes errors.

## Severity

| Level | Example | Response |
|---|---|---|
| Critical | Lead intake stopped, payments failing | Within the hour |
| High | Follow-up messages not sending | Same day |
| Low | Report formatting, retries that recovered | Daily brief |

## Secrets

Credentials live in the automation tool's credential store or a secrets manager. Never in workflow JSON, code, exports or git history. If one leaks, rotate first and clean up second.
