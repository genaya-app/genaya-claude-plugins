# Genaya plugins for Claude Code

This repository is a Claude Code plugin marketplace published by Genaya. It is planned to live at `https://github.com/genaya-app/genaya-claude-plugins`; until that repository exists, the address in the install lines below is the planned one.

It holds one plugin today:

| Plugin | What it does |
|---|---|
| `genaya` | Connects Claude Code to Genaya AI and adds eight skills for asking about your own schedule, money, invoices, clients, calls and team. See [plugins/genaya/README.md](plugins/genaya/README.md). |

## Install

Inside Claude Code:

```
/plugin marketplace add genaya-app/genaya-claude-plugins
/plugin install genaya@genaya
```

Then type `/mcp`, choose the Genaya entry and sign in to Genaya in the browser that opens. Every question is one Genaya AI credit on your plan, exactly like a question in the app. The plugin only sees what you can already see in Genaya, in the organization you connect. It never moves money and never changes billing, roles or bank settings.

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
