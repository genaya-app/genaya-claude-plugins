# Genaya for Claude

Ask Genaya AI about your own business, and prepare changes you confirm, without leaving Claude. The plugin connects Claude to Genaya (`https://api.genaya.com/mcp`) and ships nine skills that know how to ask Genaya the right question, show the answer exactly as Genaya counted it, and walk a change from preview to confirmation.

Genaya runs the day-to-day of a service business: scheduling, clients and leads, estimates and invoices, payments, calls and texts. With this plugin you ask questions like "what is on tomorrow, in order", "who owes us", "what is my revenue this month", "how many calls did we miss last week" or "who is my best salesperson this quarter", and Claude answers from your Genaya records, as you, with your permissions.

## Install

Inside Claude Code:

```
/plugin marketplace add genaya-app/genaya-claude-plugins
/plugin install genaya@genaya
```

Then sign in: type `/mcp`, choose the Genaya entry, and your browser opens the Genaya consent screen. Sign in with your normal Genaya login, pick the organization you want to work in, keep "Prepare changes you confirm" ticked if you want to make changes from Claude, and tap Allow. Back in the terminal, ask your first question: "How many appointments do I have this week?"

If you added Genaya by hand earlier with `claude mcp add --transport http genaya https://api.genaya.com/mcp`, remove that copy with `claude mcp remove genaya` so the plugin's connection is the only one; otherwise Claude sees the same two tools twice.

Claude Code asks before it runs a Genaya tool the first time. Questions only read. A change is always prepared first and shown to you; nothing is created, edited or sent until you confirm it.

## What it costs

Every question is 10 Genaya AI credits on your plan, exactly like a question typed in the app, and 20 when Genaya prepares a change. Looking up who you are, confirming, canceling, undoing and listing changes are free. The plugin only sees what you can already see in Genaya, in the organization you connect. It never moves money and never changes billing, roles, phone numbers or bank settings.

## What it can and cannot do

The plugin answers questions and prepares changes. Ask for a new task, a new client or lead, an appointment, an estimate or invoice draft, an expense, a reschedule, a cancel or a complete: Genaya shows a preview and runs it only after you say yes, and you can undo a record change for 15 minutes. Texts, emails, invoice and estimate links, and anything of $2,500 or more are approved on a Genaya page where you are signed in, never inside the chat. Money, billing, roles, phone numbers and automations are not available from Claude. If you connected before changes existed, reconnect Genaya once to grant the permission.

## Skills

Claude picks the matching skill on its own, or you can call one directly:

| Skill | What it does |
|---|---|
| `/genaya:genaya-daily-briefing` | Today's appointments in order, overdue invoices, yesterday's calls, tasks due this week (four questions, 40 credits) |
| `/genaya:genaya-schedule-lookup` | One question about the schedule: how many, what is on tomorrow, the busiest day, one client's or one team member's appointments |
| `/genaya:genaya-money-check` | Revenue collected, invoiced, by method, failed or refunded payments, booked value, expenses, two periods side by side |
| `/genaya:genaya-open-invoices` | Open and overdue invoices with client, due date and balance, the total outstanding, drafts, partially paid |
| `/genaya:genaya-client-lookup` | One person's phone, email or appointments; counts of clients and leads, by lead source |
| `/genaya:genaya-call-check` | Calls for a period: total, inbound, outbound, missed, and which were missed |
| `/genaya:genaya-team-check` | Active members by role, one member's load this week, the best salesperson for a period |
| `/genaya:genaya-how-counted` | How Genaya defines a number: revenue, overdue, which days "this week" covers, what a status means |
| `/genaya:genaya-make-a-change` | One change you confirm: a task, a client, an appointment, a reschedule, a cancel, a draft, a text approved on a Genaya page |

## Tools the plugin brings

Seven tools from the Genaya MCP server, named `mcp__plugin_genaya_genaya__<tool>` inside Claude Code:

- `whoami`: who you are connected as, the organization's name, its words for client and appointment, its time zone and currency, and whether changes are available. Free.
- `ask_genaya`: one plain-language question to Genaya AI, answered from your records. 10 credits.
- `genaya_act`: prepares one change and returns its preview. 10 credits when it only answers, 20 when it prepares a change.
- `confirm_action`: runs a prepared change after you said yes. Free.
- `cancel_action`: drops a prepared change you declined. Free.
- `undo_action`: reverses a change that ran, within 15 minutes. Free.
- `list_actions`: your own prepared and completed changes. Free.

## Requirements

- A Genaya account on any plan, including the free trial (trial limits apply).
- Your role needs the "Use Genaya AI from ChatGPT, Claude and other assistants" permission. Owners, admins and managers have it by default.
- Claude Code with plugin support (`claude --version` 2.1 or later).

## Help

help@genaya.com or the Help Center at https://help.genaya.com.
