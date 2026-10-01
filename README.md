# Genaya plugins for Claude

This repository is a Claude plugin marketplace published by Genaya, at `https://github.com/genaya-app/genaya-claude-plugins`.

It holds one plugin today:

| Plugin | What it does |
|---|---|
| `genaya` | Connects Claude to Genaya AI and adds nine skills: eight for asking about your own schedule, money, invoices, clients, calls and team, and one for changes you confirm. See [plugins/genaya/README.md](plugins/genaya/README.md). |

## Install

Inside Claude Code:

```
/plugin marketplace add genaya-app/genaya-claude-plugins
/plugin install genaya@genaya
```

Then type `/mcp`, choose the Genaya entry and sign in to Genaya in the browser that opens. Every question is 10 Genaya AI credits on your plan, exactly like a question in the app, and 20 when Genaya prepares a change. The plugin only sees what you can already see in Genaya, in the organization you connect. Nothing changes until you confirm it. It never moves money and never changes billing, roles, phone numbers or bank settings.

## Layout

```
.claude-plugin/marketplace.json     the marketplace catalog
plugins/genaya/.claude-plugin/plugin.json
plugins/genaya/.mcp.json            the Genaya MCP server (https://api.genaya.com/mcp)
plugins/genaya/skills/<name>/SKILL.md
```

## Updates

Run `/plugin marketplace update genaya` and then `/plugin update genaya@genaya`. New versions are tagged `genaya--v<version>` in this repository.

## License

MIT. See [LICENSE](LICENSE).
