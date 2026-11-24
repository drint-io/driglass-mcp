# Installing the Driglass MCP server

Driglass is a hosted MCP server. There is nothing to clone, build or install, it needs no API key, and there is no sign-in.

1. Add this entry to the MCP settings file (for Cline: `cline_mcp_settings.json`):

```json
{
  "mcpServers": {
    "driglass": {
      "type": "streamableHttp",
      "url": "https://drint.io/driglass/mcp"
    }
  }
}
```

2. Check that it works: call `list_containers`. It lists every bottle and drinking glass with its size and print zones.

3. For a print spec, call `print_spec` with `container` (an id from `list_containers`), optionally `glass` (flint, amber, green, antique, cobalt), `inks` (e.g. ["white", "gold"]), `white_under` and `cap`. It returns the art size of each zone, the screens and the rules.

Docs: https://drint.io/driglass
