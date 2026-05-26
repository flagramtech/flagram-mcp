# Flagram MCP

> Advertising marketplace for Telegram channels, VK communities and Max messenger — as an MCP server.

Search channels and bloggers by topic, audience, geo, language and price. Get ad placement pricing, post reach, engagement rate (ER), CPV and subscriber analytics. Use for influencer marketing, media planning, ad campaign targeting and competitor research.

🌐 Website: [flagram.com](https://flagram.com)
📦 Registry: [`io.github.flagramtech/flagram-mcp`](https://registry.modelcontextprotocol.io/v0/servers?search=flagram-mcp)
🌍 Language: **English** · [Русский](README.ru.md)

---

## What you get

A remote Streamable-HTTP MCP server exposing the Flagram catalog and ad-buying flow as tools:

| Group | Tools |
|---|---|
| **Discovery** | `searchChannels`, `searchPosts`, `searchAdvPosts`, `analyzeChannel` |
| **Campaigns** | `listCampaigns`, `analyzeCampaign`, `getProjects` |
| **Cart & checkout** | `getCartSummary`, `listCartItems`, `addCartItem`, `removeCartItem`, `cleanCart`, `checkoutCart` |
| **Dictionaries** | `getCategories`, `getLanguages`, `getCountries`, `getCities`, `getPlatforms`, `getSalesChannels` |

All read-only tools are idempotent; cart operations mutate state on your Flagram account.

## Endpoint

```
https://mcp.flagram.com/mcp
```

Transport: `streamable-http` (JSON-RPC 2.0).
Auth: `Authorization: Bearer <api_token>` — required for every request.

## Get an API token

1. Sign in at [flagram.com](https://flagram.com).
2. Open **Settings → API tokens** and create a new token.
3. Copy the token — you will not see it again.

## Connect

### Claude Desktop / Code

```json
{
  "mcpServers": {
    "flagram": {
      "url": "https://mcp.flagram.com/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_TOKEN"
      }
    }
  }
}
```

### Cursor / any MCP-compatible client

Add a remote server with:
- URL: `https://mcp.flagram.com/mcp`
- Header: `Authorization: Bearer YOUR_TOKEN`

## Recommended flow

1. Call `getCategories`, `getLanguages`, `getCountries` / `getCities`, `getPlatforms` to resolve ids.
2. Call `searchChannels` with those ids to find inventory.
3. Use `analyzeChannel` for deep stats on a specific channel.
4. Add picks via `addCartItem`, review with `getCartSummary`, then `checkoutCart`.

## Support

- Issues: [github.com/flagramtech/flagram-mcp/issues](https://github.com/flagramtech/flagram-mcp/issues)
- Email: support@flagram.com

## License

MIT
