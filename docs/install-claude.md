# Install in Claude

## claude.ai (web)

1. Open **Settings → Connectors**.
2. Click **Add a custom connector** (you may need to enable it under Capabilities first).
3. Name: `Narracore Screenplay Formatter`
   URL: `https://mcp.narracore.app/mcp`
4. Click **Connect** / **Create connector**. No authentication needed for the free tier.
5. In any chat, the connector's tools become available:

   > 用剧本排版工具把下面这段排成剧本 PDF：……

## Claude Desktop

Settings → Connectors → Advanced → Add custom connector, same URL.

## Using a paid license key

Paste the key into chat (`我的授权码：NRC-…`) and the AI will pass it to the tool, or configure a custom header in your connector settings if your client supports it:

```
Authorization: Bearer NRC-XXXX-XXXX-XXXX-XXXX
```

## Verify it works

Ask: *"Check my screenplay formatter credits"* — the `check_credits` tool should answer (free tier: no key needed).
