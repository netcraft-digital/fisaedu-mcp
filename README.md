<p align="center"><img src="assets/logo.png" alt="FișaEdu" width="96" height="96"></p>

# FișaEdu MCP server

[FișaEdu](https://www.fisaedu.ro) is a free library of printable worksheets (*fișe de lucru*) for Romanian schools:
kindergarten (grupa mică, mijlocie, mare), clasa pregătitoare and grades I–XII, organised by the national curriculum
(*programa școlară*). Its remote MCP server lets Claude, ChatGPT, Cursor, VS Code and other MCP clients find worksheets
for a grade, subject and topic, and link to them.

[![FișaEdu MCP connector](https://glama.ai/mcp/connectors/ro.fisaedu/fise-de-lucru/badges/score.svg)](https://glama.ai/mcp/connectors/ro.fisaedu/fise-de-lucru)

| | |
| --- | --- |
| Endpoint | `https://www.fisaedu.ro/mcp` |
| Transport | Streamable HTTP |
| Authentication | None. All tools are public and read-only. |
| Language | Romanian content; questions can be asked in any language |
| Registry name | `ro.fisaedu/fise-de-lucru` ([official MCP Registry](https://registry.modelcontextprotocol.io/v0/servers?search=ro.fisaedu)) |

The server is hosted by FișaEdu. This repository holds its public listing files only; there is nothing to install or
run.

## Tools

| Tool | What it does |
| --- | --- |
| `cauta_fise` | Searches the worksheets by grade, subject and topic. Each result has the fisaedu.ro link where it opens, prints and downloads. |
| `detalii_fisa` | Describes one worksheet: grade, subject, topic, instructions, how many exercises and what they ask (without the answers), image and link. |
| `programa` | Lists the curriculum topics for a grade and subject, as FișaEdu organises them, each with the link to its worksheets. |

Example prompts: *„Am nevoie de o fișă de lucru la matematică pentru clasa a II-a, adunarea până la 100”*, or
*"Find a printable Romanian grammar worksheet for 5th grade."*

## Connect

**Claude** (claude.ai or the desktop app): Settings → Connectors → Add custom connector, then paste
`https://www.fisaedu.ro/mcp`.

**ChatGPT**: add a custom MCP server with the URL above and no authentication. See <https://www.fisaedu.ro/chatgpt>.

**Claude Code**:

```sh
claude mcp add --transport http fisaedu https://www.fisaedu.ro/mcp
```

**Cursor**: add this to `~/.cursor/mcp.json` (or `.cursor/mcp.json` in a project):

```json
{
  "mcpServers": {
    "fisaedu": { "url": "https://www.fisaedu.ro/mcp" }
  }
}
```

**VS Code**: add this to `.vscode/mcp.json`:

```json
{
  "servers": {
    "fisaedu": { "type": "http", "url": "https://www.fisaedu.ro/mcp" }
  }
}
```

## Files

- [`server.json`](server.json): the entry in the official MCP Registry.
- [`.mcp.json`](.mcp.json): a ready configuration for clients that read it.
- [`assets/`](assets): the logo.

## Contact

FișaEdu, by Netcraft Digital SRL, Cluj-Napoca, Romania · contact@fisaedu.ro · <https://www.fisaedu.ro>
