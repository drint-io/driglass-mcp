# Driglass MCP — print straight on glass

**Driglass** is for packaging printed straight on the glass: ceramic screen print (applied ceramic label, ACL) on beer and wine bottles and on drinking glasses, not a paper label. This MCP server gives an AI assistant the real sizes of Driglass's containers and, for one container, its glass colour and its inks, the print spec a glass decorator works from: the art size of each print zone, the neck unrolled to its arc, how many screens are needed, and the rules for enamel on glass.

Containers (outside sizes from makers' sheets): 12 oz long-neck, 12 oz stubby and 500 ml Vichy beer bottles with a 26 mm crown cap; Bordeaux and Burgundy 750 ml wine bottles with a cork finish; 16 oz pint, 16 oz can glass and 9 oz rocks drinking glasses. Glass: flint (clear), amber, green, antique green, cobalt.

This repository holds the setup files for the **hosted** Driglass MCP server. There is nothing to install or run:

```
https://drint.io/driglass/mcp
```

- Transport: Streamable HTTP
- Sign-in: none, free. Both tools only read.
- Website: [drint.io/driglass](https://drint.io/driglass): place the art, see it in real 3D glass, download one film per screen at 1:1

## Tools

| Tool | What it does |
|---|---|
| `list_containers` | The bottles and drinking glasses Driglass makes: outside diameter and height, brim-full volume, finish (crown or cork), where the size comes from, and the zones that can take a print. Narrow it to `bottle` or `tumbler` |
| `print_spec` | For one container, its `glass` colour and its `inks`: the art size of each print zone (body; neck where there is one; crown-cap top), the neck unrolled to its arc (inner and outer radius, angle), the screens needed (one per ink, plus white under on coloured glass or for read-through art) and the rules for screen printing on glass. Returns a link that opens the same container in Driglass |

## Connect

### Claude (claude.ai, Claude Desktop)

Settings → Connectors → **Add custom connector** → URL `https://drint.io/driglass/mcp`.

### Claude Code

```bash
claude mcp add --transport http driglass https://drint.io/driglass/mcp
```

Or install it as a plugin from this repository:

```
/plugin marketplace add drint-io/driglass-mcp
/plugin install driglass@driglass
```

### ChatGPT

Settings → Apps & Connectors → Advanced → Developer mode → **Create** → MCP server URL `https://drint.io/driglass/mcp`, no authentication.

### Cursor

Add to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "driglass": { "url": "https://drint.io/driglass/mcp" }
  }
}
```

### VS Code (GitHub Copilot)

Command Palette → **MCP: Add Server** → HTTP → `https://drint.io/driglass/mcp`. Or add to `.vscode/mcp.json`:

```json
{
  "servers": {
    "driglass": { "type": "http", "url": "https://drint.io/driglass/mcp" }
  }
}
```

### Gemini CLI

```bash
gemini extensions install https://github.com/drint-io/driglass-mcp
```

### Codex CLI

Add to `~/.codex/config.toml`:

```toml
[mcp_servers.driglass]
url = "https://drint.io/driglass/mcp"
```

### Windsurf, Cline, Kiro, goose and other clients

Use any "remote / Streamable HTTP server" option with the URL `https://drint.io/driglass/mcp`. No headers and no key are needed.

## Try it

- "What size is the print on a 12 oz stubby in amber glass, white and gold?"
- "I'm printing our logo round the neck of a long-neck beer bottle: give me the unrolled arc."
- "How many screens for a three-colour print on a clear pint glass, and where must the decoration stop below the rim?"

## Links

- Driglass: https://drint.io/driglass
- Support: support@drint.io
- Privacy Policy: https://drint.io/privacy
- Drint (packaging mockups and dielines), Drict (label-law checks), Drisp (device mockups) and Dripod (print-on-demand mockups) have their own MCP servers: [drint-io/drint-mcp](https://github.com/drint-io/drint-mcp), [drint-io/drict-mcp](https://github.com/drint-io/drict-mcp), [drint-io/drisp-mcp](https://github.com/drint-io/drisp-mcp), [drint-io/dripod-mcp](https://github.com/drint-io/dripod-mcp)

Sizes are outside sizes from makers' sheets; check them against the glassworks' own drawing before making screens.

## License

The files in this repository are MIT-licensed. The drint.io service follows the [Drint Terms](https://drint.io/terms).
