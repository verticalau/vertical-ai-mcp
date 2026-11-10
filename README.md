# Vertical AI MCP server

Build, test and run voice and text agents for Australian contact centres from your AI assistant.

The Vertical AI MCP server gives an AI assistant the controls of the [Vertical AI](https://verticalai.com.au) app. Create and edit voice and text agents, their prompts, tools and knowledge, check what blocks publishing, run tests, review calls and publish. Sign in through the browser; access is scoped to your workspace.

This repository holds the server's listing details only. The server is hosted by Vertical AI, so there is nothing to install or run.

## Connect

| | |
|---|---|
| URL | `https://app.verticalai.com.au/api/mcp` |
| Transport | Streamable HTTP |
| Authentication | OAuth sign-in in the browser, with dynamic client registration and PKCE. No API key to copy |
| Scopes | `agent:read`, `agent:write`, `agent:delete`, `workspace:admin` |
| Registry name | `au.com.verticalai/mcp` in the [Official MCP Registry](https://registry.modelcontextprotocol.io/v0.1/servers?search=au.com.verticalai/mcp) |

Add it to any client that takes a remote MCP server by URL. For clients that read an `mcpServers` config:

```json
{
  "mcpServers": {
    "vertical-ai": {
      "url": "https://app.verticalai.com.au/api/mcp"
    }
  }
}
```

The first call opens a browser to sign in to your Vertical AI workspace.

## Account

You need a Vertical AI workspace. The 7-day trial needs no card. See [pricing](https://verticalai.com.au/pricing).

## Docs

- [Connect your assistant](https://docs.verticalai.com.au/docs/platform/connect-your-assistant)
- [Programmatic access](https://docs.verticalai.com.au/docs/platform/programmatic-access)

## Data

By default every call stays in Australia: call audio, speech recognition, the voice, the AI model, recordings and transcripts.

## Contact

hello@verticalai.com.au. Vertical AI Pty Ltd, Perth, ABN 73 695 607 946.
