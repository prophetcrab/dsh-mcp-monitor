# dsh-mcp-monitor

Read-only inventory of the MCP servers configured in a [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness)
profile: transport, command or endpoint, whether the server is connected, and the tools it registers.

## What it adds

- **Settings → MCP servers**: one row per configured server, with a live status dot, tool count, call timeout,
  auto-reconnect state, and an expandable list of tool names.
- **`mcp_servers` tool**: the same snapshot for the agent, optionally narrowed with `server`.
- **`GET /mcp-monitor/servers`**: the JSON the panel reads.

The join is the live signal: a server whose `mcp__<name>__*` tools are registered is connected. Credentials in
stdio `env` and HTTP `headers` never leave the Host.

## Install

Add the market index `https://prophetcrab.github.io/dsh-plugins/index.json` in Settings → Plugins → Discover,
or add it manually:

```json
{
  "dependencies": {
    "dsh-mcp-monitor": "github:prophetcrab/dsh-mcp-monitor"
  }
}
```

Then include the bundle in `dsh.profile.bundles` (or add its `cordis.patch.yml` row to your profile patch).

## License

MIT
