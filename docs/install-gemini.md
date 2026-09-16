# Install in Gemini

## Gemini CLI / Gemini Code Assist

Add to `~/.gemini/settings.json`:

```json
{
  "mcpServers": {
    "narracore-screenplay-formatter": {
      "httpUrl": "https://mcp.narracore.app/mcp"
    }
  }
}
```

Restart the CLI, then:

> 用 format_screenplay 排版这段剧本，给我 PDF 链接。

## Gemini web app

Settings → Apps (Connected apps) → look for custom connector / MCP support and add the same URL. Availability varies by account type; the CLI route above always works.

## Paid license key (optional)

Paste it in chat (`授权码：NRC-…`), or if your client supports custom headers:

```
Authorization: Bearer NRC-XXXX-XXXX-XXXX-XXXX
```
