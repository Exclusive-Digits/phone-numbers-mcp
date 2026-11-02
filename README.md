<p align="center"><img src="assets/logo.png" alt="Exclusive Digits" width="96" height="96"></p>

# Exclusive Digits MCP server

Search US local phone numbers for sale by city, area code, word, pattern or price, and check any number's price and availability, from Claude, ChatGPT or any MCP client.

- Server URL: `https://exclusivedigits.com/mcp`
- Transport: Streamable HTTP
- Authentication: none
- Read-only: it cannot buy, reserve or hold a number, create an account, or send messages. You buy on the number's own page on [exclusivedigits.com](https://exclusivedigits.com), where price and availability are checked again at checkout.

This repository holds the server's listing files. The server itself is a hosted service run by Exclusive Digits.

## Connect

**Claude:** add [Exclusive Digits from the Claude directory](https://claude.ai/directory/exclusive-digits). Or open Settings, then Connectors, choose Add custom connector, and paste the server URL.

**ChatGPT:** with developer mode on, add a connector with the server URL and no authentication.

**Claude Code:**

```bash
claude mcp add --transport http exclusive-digits https://exclusivedigits.com/mcp
```

**Cursor** (`.cursor/mcp.json`), and other clients that use the `mcpServers` format:

```json
{
  "mcpServers": {
    "exclusive-digits": {
      "url": "https://exclusivedigits.com/mcp"
    }
  }
}
```

**VS Code** (`.vscode/mcp.json`):

```json
{
  "servers": {
    "exclusive-digits": {
      "type": "http",
      "url": "https://exclusivedigits.com/mcp"
    }
  }
}
```

## Tools

| Tool | What it does |
|---|---|
| `find_numbers` | Searches the numbers for sale by place, area code, a word to spell, digits, pattern, industry, price or sale, and returns up to 20, ranked best first, with price, location, patterns and page link. When nothing matches, the store widens the search and says how. Up to 5 pages per search. |
| `get_number` | Returns the current price, availability, location, patterns and page link for one ten-digit US number. |
| `catalog_vocabulary` | Lists the pattern and industry codes `find_numbers` accepts. |
| `how_buying_works` | Explains payment, when the card is charged, what the buyer receives, transfer time and refunds. |

Every tool is marked read-only (`readOnlyHint`).

## Things to ask

- "Find me a 212 number with a repeating pattern."
- "I need a phone number for my plumbing business in Austin, Texas, under $300."
- "Are there numbers in Miami that spell PIZZA?"
- "Is 212-994-0888 still for sale, and what does it cost?"
- "How does buying a number work, and how long does the transfer take?"
- "What number patterns can I search by?"

## Limits

Each search returns up to 20 numbers, with up to 5 pages. Calls are rate limited per network address; when the limit is reached, the tools say so and the assistant can try again shortly. Search results from the past few minutes may be reused. Toll-free numbers are not sold.

## Listed in

- [Claude directory](https://claude.ai/directory/exclusive-digits)
- [Official MCP Registry](https://registry.modelcontextprotocol.io/v0/servers?search=com.exclusivedigits) as `com.exclusivedigits/phone-numbers` ([server.json](server.json))

## Documentation, privacy and support

- Documentation: [exclusivedigits.com/ai-assistants](https://exclusivedigits.com/ai-assistants)
- Privacy: [AI assistant connections](https://exclusivedigits.com/privacy#ai-assistants) in the Privacy Policy
- Questions, problems or security reports: [support@exclusivedigits.com](mailto:support@exclusivedigits.com)
