# TradeFlags MCP

Authenticated market data for Hong Kong and US equities, delivered over the
Model Context Protocol — one streamable-HTTP endpoint, installable in Claude
Code, Hermes, and any MCP-capable agent.

**Operator:** AINFER Limited · Hong Kong · Business Registration No. 81518145

## What it serves

35 tools across 27 packages, all read-only and timestamped:

- **Breadth & signals** — TRIN/Arms Index, McClellan, RASI, Hi-Lo, power ratio, TD Sequential, Parabolic SAR, Hindenburg Omen, signal outcomes.
- **Volatility** — SVI-fitted volatility surfaces (HKEX/FUTU), index term structure, 25Δ skew, VHSI/VIX levels.
- **Macro & sentiment** — ADS Business Conditions Index, CRANE-X sentiment, VIX term structure, HKMA curve.
- **Forecasts** — Moirai HK index forecasts.
- **Company network** — nodes, edges, and scenario models.
- **On-demand OTC pricing** — accumulator / equity-derivative pricing with NPV + greeks.

See [docs/tools.md](docs/tools.md) for the full catalogue.

## Connect

One endpoint — streamable HTTP:

```
https://api.tradeflags.com/mcp
```

Authenticate with your API key:

```
Authorization: Bearer tf_live_<your-key>
```

### Claude Code

`claude mcp add tradeflags --transport http --url https://api.tradeflags.com/mcp --header "Authorization: Bearer tf_live_YOUR_KEY"`

or via `.mcp.json`:

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

### Hermes

In `~/.hermes/config.yaml`:

```yaml
mcp_servers:
  tradeflags:
    url: "https://api.tradeflags.com/mcp"
    headers:
      Authorization: "Bearer tf_live_YOUR_KEY"
```

Full install guide: [docs/install.md](docs/install.md)

## Get an API key

Sign in at [tradeflags.com](https://tradeflags.com), open your account dashboard,
and issue a key. Plans:

| Plan | Quota |
|------|-------|
| Free | 1,000 calls / month |
| Pro | 200,000 calls / month |
| Team | 2,000,000 calls / month |
| Enterprise | custom |

Pricing: [tradeflags.com/pricing.php](https://tradeflags.com/pricing.php)

## Registry manifests

- `server.json` — official MCP Registry manifest (namespace `com.tradeflags/mcp`).
- `smithery.yaml` — Smithery config schema.

## Documentation

Full documentation lives at [tradeflags.com/docs](https://tradeflags.com/docs).

## Disclaimer

Outputs are computational audit data only. Not investment advice. No dealing,
advising or asset-management activity is conducted.
