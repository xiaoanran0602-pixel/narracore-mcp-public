# Narracore Screenplay Formatter

**Turn rough screenplay text into professionally structured screenplay format and a print-ready PDF — from any MCP-compatible AI.**

Remote MCP server (Streamable HTTP): `https://mcp.narracore.app/mcp`

Works with Claude, ChatGPT, Cursor, Gemini and any MCP-compatible client. Paste a rough script, get back structured blocks (scenes, characters, parentheticals, dialogue, transitions), layout diagnostics, and a typeset PDF identical to [narracore.cn](https://narracore.cn) — fixed typewriter grid, embedded Sarasa Mono / Courier Prime fonts, Chinese and English (or mixed) tracks.

Beyond formatting, the same endpoint carries a film-breakdown protocol and a story-continuity protocol for AI agents (14 tools in total — [see below](#tools)).

- **Try it free**: one free credit per day, no account, no key.
- **Need more?** $1.49 for 10 credits, $5.99 for 50 — [buy here](https://narracore.app/checkout). One credit covers one screenplay for 24 hours across the screenplay tools, or one film analysis, or one story project. Failures are never charged; retries of the same request never double-charge.
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

Fourteen tools over one endpoint, in three billing units (see [Paid credits](#paid-credits-optional)).

### Screenplay

| Tool | What it does |
| --- | --- |
| `format_screenplay` | Parse rough text (or typed blocks) → structured blocks → layout diagnostics → print-ready PDF (free `validate_only` mode included) |
| `analyze_screenplay` | Deterministic stats: scene list with parsed headings, character table, dialogue ratio, action density |
| `diagnose_scenes` | Scene shootability diagnosis — the calling AI cites evidence, the server validates and scores 0-100 (`material` mode free) |
| `convert_fountain` | Blocks ↔ Fountain (plain-text screenplay interchange format), both directions |
| `build_video_prompts` | Screenplay → structured video-prompt scaffolds: ~15s segments, ≤4 shots each, character registry, dialogue pre-filled verbatim, style guidance (checklist / editable presets / your own note) |
| `check_video_prompts` | **Free** deterministic checks of finished video prompts against the screenplay: dialogue-verbatim lock, cut-point handoff, shared-content rules (violations) + eyeline/rhetoric/conflict advisories |

One credit covers one screenplay for 24 hours across all of the above (they share a content fingerprint — send the same script, or the blocks you got back, to several tools and it charges once).

### Film breakdown (the video never leaves your machine)

Your agent watches the footage locally with its own vision model; this server supplies the protocol, the deterministic validation and the compilation.

| Tool | What it does |
| --- | --- |
| `get_film_contract` | **Free** — the Film Contract by section: pipeline and entities, the long-take window protocol, observability levels, closed vocabularies + alias table, observation and reasoning prompt templates, reference ffmpeg recipes |
| `plan_film_analysis` | **Free** — cut timestamps → the analysis topology every Film Protocol agent shares: numbered base shots, long-take windows, ≤20s / ≤8-shot analysis units |
| `validate_film_breakdown` | **Free** preflight — schema, closed vocabularies, cross-references, window topology, provenance shape; returns a lossless `normalized_patch` and retry feedback for your model |
| `compile_film_breakdown` | **Billed: 1 credit per film analysis** — authoritative validation → long-take merge (a 96s take is ONE shot in every statistic) → exact aggregates → labelled deterministic heuristics → PDF report with a 24h signed link |

### Story continuity

For AI agents carrying a long-running story (novel, interactive fiction, tabletop campaign, worldbuilding) across context windows. The full text and the returned `StoryState` stay with you; the server stores nothing.

| Tool | What it does |
| --- | --- |
| `prepare_story_window` | **Free** — split a conversation (verbatim user/assistant turns) into stable, hash-anchored units bound to your current state |
| `absorb_story_window` | **Billed: 1 credit per story project / 24h** — validate and apply YOUR extraction: selectors must quote exact unit text, and the returned `canon_patch` is tail-hash-verified before you apply it |
| `render_story_handoff` | **Free** — render the state you supply into a model-independent zh/en handoff document for a successor writer/AI |

### Account

| Tool | What it does |
| --- | --- |
| `check_credits` | Show remaining credits for a license key, plus recent usage and the purchase link |

Structured input (typed blocks), diagnostics codes, and header-based auth are documented in the tool descriptions themselves — your AI already knows how to use them.

## Paid credits (optional)

The free daily credit works with no key. To buy more:

1. Buy a pack at [narracore.app/checkout](https://narracore.app/checkout) ($1.49 / 10 credits, $5.99 / 50 credits).
2. You get a license key like `NRC-XXXX-XXXX-XXXX-XXXX`.
3. Give it to your AI (paste it in chat, or set header `Authorization: Bearer NRC-…` in your client). Top-ups land on the same key.

**What one credit covers** (three independent units — a credit spent on one is not a credit in another):

| Unit | Charged once per | Tools |
| --- | --- | --- |
| Screenplay | one screenplay, for 24 hours | `format_screenplay`, `analyze_screenplay`, `diagnose_scenes`, `convert_fountain`, `build_video_prompts` |
| Film analysis | one `analysis_id`, for 24 hours | `compile_film_breakdown` |
| Story project | one story project, for 24 hours | `absorb_story_window` |

Free tier: one credit per day per visitor, any of the three. Failures are never charged; retrying the same `request_id` never double-charges.

Details: [docs/pricing.md](docs/pricing.md) · Refund within 7 days if unused.

## Privacy

Your text is used only to produce your result. PDFs are deleted after 24 hours. License keys are stored hashed. Videos are never uploaded for film breakdowns. No training, no accounts, no newsletters. → [docs/privacy.md](docs/privacy.md)

## Links

- Product page: [narracore.app](https://narracore.app)
- Service endpoint: [mcp.narracore.app/mcp](https://mcp.narracore.app/mcp)
- Registry entry: `cn.narracore/screenplay-formatter`
- Security: [SECURITY.md](SECURITY.md)

---

This repository is the public anchor for the hosted service — it contains documentation, examples, and registry metadata only. Docs are licensed [CC-BY-4.0](LICENSE).
