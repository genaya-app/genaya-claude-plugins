# genaya-schedule-lookup: questions and output

Send each question to `ask_genaya` exactly as written, one per call, with a fresh `idempotency_key`. Swap only the period word or the name in angle brackets. Every question here answers today from the organization's own schedule.

## Questions

1. "How many appointments do I have today?"
2. "What appointments do I have today, in order, with the client and the time?"
3. "What appointments do I have tomorrow, in order, with the client and the time?"
4. "How many appointments are scheduled this week?"
5. "How many appointments have we had so far this week?"
6. "How many appointments are scheduled next week?"
7. "Which day next week is the busiest?"
8. "How many appointments are booked for the next 7 days?"
9. "What types of appointments do we have in the next 7 days?"
10. "Break down this month's appointments by status."
11. "How many appointments were canceled this week?"
12. "Show me all appointments for <Client Name>."
13. "How many appointments does <Team Member Name> have this week?"
14. "Where in Genaya do I see the calendar for tomorrow?" (only when a free-slot request needs a link and none is on hand)

Two-question asks: "how many next week and which day is busiest" is 6 then 7 (20 credits). A period word swap keeps the sentence otherwise identical.

## Output template

```
**<N> <appointment word>s <window exactly as Genaya named it>** - <not-counted note as returned>

List questions only:
| Time | <Client word> | Type | Status | Team member |   (Genaya's columns and order; times in the organization's time zone)

Breakdown and busiest-day questions only:
| Day (or Status, or Type) | <Appointment word>s |   (as returned; every tied day named)

Counted as: <Genaya's definition line when it gave one, for example scheduled start in the window, canceled and deleted not counted>
```

Empty answer: one line, "No <appointment word>s <window>." A request for free slots reads: "Genaya confirms availability on its calendar: <link>. Here is <day> in order:" followed by the table. Never a second page; never a total computed from the rows.
