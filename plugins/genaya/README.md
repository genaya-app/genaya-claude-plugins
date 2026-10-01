# Genaya for Claude Code

Ask Genaya AI about your own business without leaving the terminal. The plugin connects Claude Code to Genaya (`https://api.genaya.com/mcp`) and ships eight skills that know how to ask Genaya the right question and show the answer exactly as Genaya counted it.

Genaya runs the day-to-day of a service business: scheduling, clients and leads, estimates and invoices, payments, calls and texts. With this plugin you ask questions like "what is on tomorrow, in order", "who owes us", "what is my revenue this month", "how many calls did we miss last week" or "who is my best salesperson this quarter", and Claude answers from your Genaya records, as you, with your permissions.

## Install

Inside Claude Code:

```
/plugin marketplace add genaya-app/genaya-claude-plugins
/plugin install genaya@genaya
```

Then sign in: type `/mcp`, choose the Genaya entry, and your browser opens the Genaya consent screen. Sign in with your normal Genaya login, pick the organization you want to work in and tap Allow. Back in the terminal, ask your first question: "How many appointments do I have this week?"

If you added Genaya by hand earlier with `claude mcp add --transport http genaya https://api.genaya.com/mcp`, remove that copy with `claude mcp remove genaya` so the plugin's connection is the only one; otherwise Claude sees the same two tools twice.

Claude Code asks before it runs a Genaya tool the first time. Genaya's tools only read and answer, so approving one never changes a record, sends a message or spends money.

## What it costs

Every question is 10 Genaya AI credits on your plan, exactly like a question typed in the app; the `whoami` lookup is free. The plugin only sees what you can already see in Genaya, in the organization you connect. It never moves money and never changes billing, roles or bank settings.

## What it can and cannot do in this release

The plugin answers questions. Nothing is created, changed or sent in Genaya from Claude Code: when you ask for a change (a new task, a rescheduled appointment, a text to a client, a refund) the answer says it cannot do that here and hands back a link to finish it in Genaya, where you are signed in.

## Skills

Claude picks the matching skill on its own, or you can call one directly:

| Skill | What it answers |
|---|---|
| `/genaya:genaya-daily-briefing` | Today's appointments in order, overdue invoices, yesterday's calls, tasks due this week (four questions, 40 credits) |
| `/genaya:genaya-schedule-lookup` | One question about the schedule: how many, what is on tomorrow, the busiest day, one client's or one team member's appointments |
| `/genaya:genaya-money-check` | Revenue collected, invoiced, by method, failed or refunded payments, booked value, expenses, two periods side by side |
| `/genaya:genaya-open-invoices` | Open and overdue invoices with client, due date and balance, the total outstanding, drafts, partially paid |
| `/genaya:genaya-client-lookup` | One person's phone, email or appointments; counts of clients and leads, by lead source |
| `/genaya:genaya-call-check` | Calls for a period: total, inbound, outbound, missed, and which were missed |
| `/genaya:genaya-team-check` | Active members by role, one member's load this week, the best salesperson for a period |
| `/genaya:genaya-how-counted` | How Genaya defines a number: revenue, overdue, which days "this week" covers, what a status means |

## Tools the plugin brings

Two read-only tools from the Genaya MCP server, named `mcp__plugin_genaya_genaya__whoami` and `mcp__plugin_genaya_genaya__ask_genaya` inside Claude Code:

- `whoami`: who you are connected as, the organization's name, its words for client and appointment, its time zone and currency. Free.
- `ask_genaya`: one plain-language question to Genaya AI, answered from your records. 10 credits.

## Requirements

- A Genaya account on any plan, including the free trial (trial limits apply).
- Your role needs the "Use Genaya AI from ChatGPT, Claude and other assistants" permission. Owners, admins and managers have it by default.
- Claude Code with plugin support (`claude --version` 2.1 or later).

## Help

help@genaya.com or the Help Center at https://help.genaya.com.
