# Installing TradeFlags MCP

One streamable-HTTP endpoint: `https://api.tradeflags.com/mcp`, authenticated
with `Authorization: Bearer tf_live_<your-key>`.

Get a key: sign in at https://tradeflags.com, open your dashboard, issue a key.
The Free tier is 1,000 calls/month.

OAuth sign-in is also supported for MCP directories (Claude Desktop, ChatGPT):
their "Connect" flow uses `https://api.tradeflags.com/.well-known/oauth-authorization-server`
and signs you in with Google/Apple/email — no API key needed for those clients.

## Claude Code

Option A — CLI:

```
claude mcp add tradeflags --transport http --url https://api.tradeflags.com/mcp --header "Authorization: Bearer tf_live_YOUR_KEY"
```

Option B — `.mcp.json` in your project root:

```json
{
  "mcpServers": {
    "tradeflags": {
      "type": "http",
      "url": "https://api.tradeflags.com/mcp",
      "headers": { "Authorization": "Bearer tf_live_YOUR_KEY" }
    }
  }
}
```

Restart Claude Code. The tools appear as `tradeflags__<tool>`.

## Hermes Agent

Add to `~/.hermes/config.yaml`:

```yaml
mcp_servers:
  tradeflags:
    url: "https://api.tradeflags.com/mcp"
    headers:
      Authorization: "Bearer tf_live_YOUR_KEY"
```

Restart Hermes. The tools appear prefixed `mcp_tradeflags_*`.

## Example prompts

- "Price a 12-month accumulator on 0700 (Tencent) at 97% strike, 105% KO, 2× leverage."
- "Give me the latest breadth panel for the Hang Seng — TRIN, McClellan, Hi-Lo, RASI."
- "Evaluate whether to add HSBC (0005) here using the signal and breadth packages."
- "Fetch the current VHSI level and the HSI 25Δ skew term structure."

## Notes

- HK stock codes are 4-digit zero-padded: `0001`, `0700`.
- Every tool returns an `as_of` timestamp; data is refreshed intraday for
  volatility surfaces and nightly for the rest.
- Read-only API: no orders, no portfolio mutation.
