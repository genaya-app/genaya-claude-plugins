# genaya-open-invoices: questions and output

Send each question to `ask_genaya` exactly as written, one per call, with a fresh `idempotency_key`. Open and overdue need no period (as of today in the organization's time zone); sent and paid take the member's period word, default this month.

## Questions

1. "Which invoices are overdue, with the client, due date and open balance, and what is the total?"
2. "How many invoices are overdue?"
3. "What is the total overdue balance?"
4. "How many open invoices do I have?"
5. "How much money is outstanding on open invoices?"
6. "Which invoices have no payment recorded against them?"
7. "Which invoice has the largest outstanding balance?"
8. "How many draft invoices are there?"
9. "What is the total value sitting in draft invoices?"
10. "How many invoices are partially paid?"
11. "How many invoices did we send out this month?"
12. "How many invoices were paid this month?"

Two-question asks: "who owes us and how much in total" is 1 then 5 (two credits).

## Definitions Genaya states (copy its line, never this one)

- Open: status sent, unpaid or partially paid with a balance above zero; canceled and deleted not counted.
- Overdue: an open invoice whose due date is before today in the organization's calendar.
- Draft: not sent; counted separately and never in open or overdue.

## Output template

```
**Owed as of today, <date>: <N> open invoices, <currency> <total>** - Overdue: <N>, <currency> <total>   (only the numbers Genaya returned; leave out a figure it did not give)

| <Client word> | Invoice | Due | Balance | Status |   (Genaya's columns and order; Status only when returned)

Counted as: <Genaya's definition line>
```

Single-record questions (largest balance): one line with the invoice number, the client and the balance as returned. Count questions: one line with the count and, when given, the total. Empty answer: one line, "No overdue invoices as of today." Same heading shape every run.
