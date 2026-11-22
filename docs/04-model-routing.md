# 04 · Model routing

## The problem

Sending every task to the largest language model is slow and expensive. Sending everything to the smallest gives poor drafts and risky judgement calls.

## The pattern

Route by the **kind of thinking** the task needs:

| Tier | Use for | Examples |
|---|---|---|
| Small / fast | Classify, extract, route | Language detection, lead intent, tagging an email, pulling fields from a form |
| Medium | Build and draft | Reply drafts, summaries, document checklists, code changes |
| Large | Judgement | Strategy, compliance review, anything a mistake would be expensive on |

## Rules

- **Structured output for small-tier tasks.** Ask for JSON matching a schema and validate it. Retry once, then fall back to a human queue.
- **Escalate on low confidence.** If the small model is unsure, pass the item up a tier rather than guessing.
- **Large-tier output is still reviewed** where it touches clients, money or regulated advice.
- **Log cost per workflow** monthly. Re-check the routing when prices or models change.
- **Local models** are worth it for high-volume, low-risk classification and for data that should not leave your machines.

## Simple router

```
input ─► classify task type (small)
          ├─ classify/extract ─► small
          ├─ draft/build      ─► medium
          └─ judgement        ─► large ─► human review
```
