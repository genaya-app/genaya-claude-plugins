# genaya-money-check: questions and output

Send each question to `ask_genaya` exactly as written, one per call, with a fresh `idempotency_key`. Swap only the period word. Every amount comes back in the organization's currency from `whoami`; copy it as returned.

## Questions

1. "What is my revenue this month?"
2. "How much did we collect last month?"
3. "How much revenue have we collected this quarter?"
4. "How much have we invoiced this month?"
5. "Break down this month's collected payments by payment method."
6. "How many payments failed in the last 30 days?"
7. "How many payments have been refunded?"
8. "What is the total value of this month's appointments?"
9. "How much have we spent on expenses this month?"
10. "What were our total expenses last month?"
11. "How many expenses were logged this month?"

Comparison: 1 then 2 as two standalone calls without `conversation_id` (20 credits); or the two periods the member named in the same wording.

## Definitions Genaya states (copy its line, never this one)

- Revenue and collected: succeeded payments by payment date; pending, failed, canceled and refunded not counted. Invoice totals are not revenue.
- Invoiced: invoice totals created in the window, drafts and canceled not counted; billed, not collected.
- Sales or booked value: the appointments' totals by scheduled date across every status; not revenue.

## Output template

```
**<Metric> <window exactly as Genaya named it>: <currency> <amount>**
Counted as: <Genaya's definition line>

Breakdown questions only:
| Method (or Status) | Amount |   (as returned, Genaya's order)

Comparison only:
| Period | Collected |
| <this month, to date, as Genaya named it> | <amount> |
| <last month, as Genaya named it> | <amount> |
Difference: <amount>, computed from the two totals above. Higher: <period>.
```

Empty answer: one line in Genaya's words. Same heading shape every run.
