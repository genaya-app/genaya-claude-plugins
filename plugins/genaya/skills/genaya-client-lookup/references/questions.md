# genaya-client-lookup: questions and output

Send each question to `ask_genaya` exactly as written, one per call, with a fresh `idempotency_key`. Put a name exactly as the member typed it; swap only the period word for counts.

## Questions

1. "What is the phone number for <Client Name>?"
2. "Show me all appointments for <Client Name>."
3. "How many clients do I have?"
4. "How many new clients did we add this month?"
5. "List my last 5 clients."
6. "Where do my clients come from? Break them down by lead source."
7. "How many leads came in this month?"
8. "Which lead sources bring in the most leads?"
9. "How many leads are in my pipeline?"
10. "How many new leads did we get in the last 7 days?"

Two-question asks: "pull up <name>" is 1 then 2 with `conversation_id` and `entity` from the first answer (two credits); "leads this month and by source" is 7 then 8 (two credits).

## Output template

```
Person questions:
**<Name> - <client word>**
- Phone: <as returned>
- Email: <as returned>
- Lead source: <as returned>   (only the fields Genaya returned)
<Appointment word>s on file: <N, as returned>
| Date | Type | Status | Amount |   (as returned, Genaya's order)

Count questions:
**<N> <client word>s (or leads) <window exactly as Genaya named it>**
| Lead source | Count |   (breakdowns only, as returned)

Counted as: <Genaya's definition line when given>
```

Empty answer: one line in Genaya's words ("No <client word> named <name> on file.", "No leads this month (to date)."). Same heading shape every run.
