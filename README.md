# IRM Consulting & Advisory MCP Server

Official remote [Model Context Protocol](https://modelcontextprotocol.io) server of
[IRM Consulting & Advisory](https://irmcon.com/), an AI-native vCISO, AI governance and cyber risk
advisory firm in Toronto serving Canada and the USA.

AI assistants and agents can use it to describe IRM's services, quote published starting prices,
recommend free self-assessment tools, check live consultation availability and create a single-use
booking link.

| | |
|---|---|
| Endpoint | `https://mcp.irmcon.com/mcp` |
| Transport | Streamable HTTP |
| Authentication | None (public data only) |
| MCP Registry name | `com.irmcon/services` |
| Server card | https://mcp.irmcon.com/.well-known/mcp/server-card.json |

This repository holds the listing metadata only. The server is hosted by IRM; there is nothing to
install or run.

## Tools

| Tool | What it returns |
|---|---|
| `list_services` | IRM's 18 services and programs (vCISO, AI governance, GRC, SOC 2, NIST CSF 2.0, ISO 27001, ISO 42001, CMMC, CPCSC, penetration testing and more), filterable by kind or framework |
| `get_service` | One service: summary, audience, frameworks, published starting price, booking link and related free tool |
| `list_free_products` | The 9 free, browser-based self-assessment tools, with page and app links |
| `get_pricing` | Published monthly subscription tiers, plus one service's starting price |
| `check_availability` | Live 30-minute consultation slots for the next 1 to 7 days |
| `create_booking_link` | A single-use Calendly link for a free consultation. The person confirms the booking on Calendly; the tool books nothing and takes no personal data |

Prices are monthly USD starting prices. A service without a published price is scoped in a free
consultation.

## Connect

**Claude (web or desktop):** Settings > Connectors > Add custom connector, then paste
`https://mcp.irmcon.com/mcp`.

**Claude Code:**

```bash
claude mcp add --transport http irm https://mcp.irmcon.com/mcp
```

**Cursor, VS Code, Windsurf and other MCP clients** (`mcp.json`):

```json
{
  "mcpServers": {
    "irm": { "url": "https://mcp.irmcon.com/mcp" }
  }
}
```

**ChatGPT:** add `https://mcp.irmcon.com/mcp` as a custom connector (developer mode on some plans).

## Example prompts

- "We're a 40-person SaaS company that needs SOC 2 and has started using AI agents. What would IRM Consulting & Advisory recommend, and what does it cost?"
- "Which free tool should I run before an ISO 42001 project?"
- "Find me a 30-minute slot with IRM next Tuesday afternoon, Toronto time."

## Data and privacy

- Every tool returns public information from https://irmcon.com/ (the same data as https://irmcon.com/services.json).
- No API key, account or personal data is required or collected.
- Requests are rate-limited. Logs store a salted hash of the caller's IP, never the raw address.

## Contact

- General: info@irmcon.com
- Security issues: see https://irmcon.com/.well-known/security.txt
- Website: https://irmcon.com/

## Listed
[![Listed on mcpservers.org](https://url.avanan.click/v2/r03/___https://mcpservers.org/badge.svg)](https://mcpservers.org/servers/irmcon-org/irm-mcp-server___.YXYyYzppcm1jb246YTpvOjc4NjY2YWU0NmNkNWQ2NjIzYzdlYjhkZmUwNzNkNTRkOjc6ZmQ3MTo1Njc1ZGQ2MGM4ZTQ2NDk3YzcyZWQ4MDllYmY0ODBhOWZkNDBiZmVhMzY3YjAxN2Y1ZWY1OWZmNDU3MTI3MGQwOnQ6VDpO)
