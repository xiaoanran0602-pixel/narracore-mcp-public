# Install in Cursor

## UI

Settings → MCP → **Add new global MCP server** → type **url**:

- Name: `narracore-screenplay-formatter`
- URL: `https://mcp.narracore.app/mcp`

## Or edit `~/.cursor/mcp.json` directly

```json
{
  "mcpServers": {
    "narracore-screenplay-formatter": {
      "url": "https://mcp.narracore.app/mcp"
    }
  }
}
```

## Paid license key (optional)

```json
{
  "mcpServers": {
    "narracore-screenplay-formatter": {
      "url": "https://mcp.narracore.app/mcp",
      "headers": { "Authorization": "Bearer NRC-XXXX-XXXX-XXXX-XXXX" }
    }
  }
}
```

Then ask the agent: *"Format this screenplay with format_screenplay and give me the PDF link."*
