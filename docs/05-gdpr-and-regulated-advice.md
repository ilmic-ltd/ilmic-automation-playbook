# 05 · GDPR and regulated advice

This is a practical checklist, not legal advice. Take advice from a qualified professional for your own situation.

## UK GDPR basics for automation

- **Lawful basis for each use.** A lead asking for a quote is not consent to a newsletter.
- **Data minimisation.** Collect what the service needs. Passport numbers do not belong in a lead form.
- **Know where data goes.** Keep a simple list of every tool that stores personal data, where it is hosted and who has access.
- **Processor agreements** with every tool that holds client data.
- **Retention.** Set a period for unconverted leads and delete or anonymise after it.
- **Subject requests.** With one source of truth, finding and deleting a person's data takes minutes, not days.
- **No personal data in logs, alerts, test fixtures or git.**

## Regulated advice boundaries

In the UK, some advice may only be given by authorised or regulated people, for example immigration advice, mortgage and investment advice, legal advice and some tax work.

Automation in these sectors should:

- **Inform and organise**, never advise. "Here is the document checklist for this route" is information; "you qualify for this visa" is advice.
- **Route advice questions to an authorised person**, with the context already gathered.
- **Keep the human approval step** before any client-facing message that could be read as advice.
- **Use clear wording** in bots and auto-replies about what they can and cannot do.
- **Keep an audit trail** of what was sent, by whom and when.

## Marketing messages

- WhatsApp: opt-in and approved templates only outside the 24-hour window.
- Email and SMS: follow PECR. Soft opt-in only applies to similar services for existing customers.
- Every message has a clear way to opt out, and opt-outs sync back to the single source of truth.
