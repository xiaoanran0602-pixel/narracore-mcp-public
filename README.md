# Narracore Screenplay Formatter

**Turn rough screenplay text into professionally structured screenplay format and a print-ready PDF — from any MCP-compatible AI.**

Remote MCP server (Streamable HTTP): `https://mcp.narracore.app/mcp`

Works with Claude, ChatGPT, Cursor, Gemini and any MCP-compatible client. Paste a rough script, get back structured blocks (scenes, characters, parentheticals, dialogue, transitions), layout diagnostics, and a typeset PDF identical to [narracore.cn](https://narracore.cn) — fixed typewriter grid, embedded Sarasa Mono / Courier Prime fonts, Chinese and English (or mixed) tracks.

- **Try it free**: one free formatting per day, no account, no key.
- **Need more?** $1.49 for 10 formats, $5.99 for 50 — [buy here](https://narracore.app/checkout). Failures are never charged; retries of the same request never double-charge.
- **Example**: [rough input](examples/input-en.txt) → [formatted PDF](examples/output-en.pdf) (also [Chinese](examples/input-zh.txt) → [中文 PDF](examples/output-zh.pdf)).

## Install

### Claude (claude.ai / Claude Desktop)

1. Settings → **Connectors** → **Add a custom connector** (Desktop: Settings → Connectors → Advanced).
2. URL: `https://mcp.narracore.app/mcp` → Connect.
3. In any chat, ask: *"Format this screenplay: …"*

Step-by-step: [docs/install-claude.md](docs/install-claude.md)

### ChatGPT

1. Settings → **Apps & Connectors** → Advanced → **Create** (Developer mode).
2. MCP Server URL: `https://mcp.narracore.app/mcp`.
3. Ask ChatGPT: *"用剧本排版工具排版这段剧本：…"*

Step-by-step: [docs/install-chatgpt.md](docs/install-chatgpt.md)

### Cursor

Settings → MCP → **Add new global MCP server**, type **url**:

```json
{ "url": "https://mcp.narracore.app/mcp" }
```

Step-by-step: [docs/install-cursor.md](docs/install-cursor.md)

### Gemini

Gemini CLI / Code Assist — add to `settings.json`:

```json
{
  "mcpServers": {
    "narracore-screenplay-formatter": { "httpUrl": "https://mcp.narracore.app/mcp" }
  }
}
```

Step-by-step: [docs/install-gemini.md](docs/install-gemini.md)

## Tools

| Tool | What it does |
| --- | --- |
| `format_screenplay` | Parse rough text → structured blocks → layout diagnostics → print-ready PDF (free `validate_only` mode included) |
| `check_credits` | Show remaining formatting credits for a license key |

Structured input (typed blocks), diagnostics codes, and header-based auth are documented in the tool descriptions themselves — your AI already knows how to use them.

## Paid credits (optional)

The daily free format works with no key. To format more:

1. Buy a pack at [narracore.app/checkout](https://narracore.app/checkout) ($1.49 / 10, $5.99 / 50).
2. You get a license key like `NRC-XXXX-XXXX-XXXX-XXXX`.
3. Give it to your AI (paste it in chat, or set header `Authorization: Bearer NRC-…` in your client). Top-ups land on the same key.

Details: [docs/pricing.md](docs/pricing.md) · Refund within 7 days if unused.

## Privacy

Your text is used only to produce your formatting result. PDFs are deleted after 24 hours. License keys are stored hashed. No training, no accounts, no newsletters. → [docs/privacy.md](docs/privacy.md)

## Links

- Product page: [narracore.app](https://narracore.app)
- Service endpoint: [mcp.narracore.app/mcp](https://mcp.narracore.app/mcp)
- Registry entry: `cn.narracore/screenplay-formatter`
- Security: [SECURITY.md](SECURITY.md)

---

This repository is the public anchor for the hosted service — it contains documentation, examples, and registry metadata only. Docs are licensed [CC-BY-4.0](LICENSE).
