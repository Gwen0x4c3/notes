# MCP

## 检索类

### Context7

### DeepWiki

[DeepWiki](https://deepwiki.org/) | [MCP](https://mcp.deepwiki.com/)

```bash
claude mcp add -s user -t http deepwiki https://mcp.deepwiki.com/mcp
```

### Exa Code

[Exa Code](https://exa.ai/) | [MCP](https://smithery.ai/server/exa)

```bash
claude mcp add --transport http exa "https://server.smithery.ai/exa/mcp"
```

### fetch-mcp

[Github]() | [MCP]()

```json
{
  "mcpServers": {
    "fetch": {
      "command": "npx",
      "args": ["mcp-fetch-server"],
      "env": {
        "DEFAULT_LIMIT": "50000" // optionally change default limit
      }
    }
  }
}
```
