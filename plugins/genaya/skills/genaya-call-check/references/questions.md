# genaya-call-check: questions and output

Send each question to `ask_genaya` exactly as written, one per call, with a fresh `idempotency_key`. Swap only the period word (today, yesterday, this week, last week, last 7 days, last 30 days, this month).

## Questions

1. "How many calls did we have today?"
2. "How many calls did we have yesterday, and how many were missed?"
3. "How many calls did we have in the last 7 days?"
4. "How many inbound calls came in over the last 7 days?"
5. "How many outbound calls did the team make in the last 7 days?"
6. "How many calls did we have last week?"
7. "How many calls did we miss in the last 30 days?"
8. "Which calls were missed in the last 7 days, with the caller, the number and the time?"

Two-question asks: "inbound versus outbound" is 4 then 5 for the same period (two credits).

## Definition Genaya states (copy its line, never this one)

Calls by call time in the window, split by direction (inbound, outbound) and outcome (answered, missed, voicemail); deleted calls not counted.

## Output template

```
**Calls <window exactly as Genaya named it>: <total>** - inbound <N>, outbound <N>, missed <N>   (only the numbers Genaya returned; leave out a split it did not give)

Missed-call list only:
| When | Caller | Number |   (as returned, Genaya's order, times in the organization's time zone)

| Day | Calls |   (only when Genaya returned a per-day table, in its order)

Counted as: <Genaya's definition line>
```

Empty answer: one line, "No calls <window>." or "No missed calls <window>." Same heading shape every run.
