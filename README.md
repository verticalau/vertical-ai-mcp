# Vertical AI MCP server

Build, test and run voice and text agents for Australian contact centres from your AI assistant.

The Vertical AI MCP server gives an AI assistant the controls of the [Vertical AI](https://verticalai.com.au) app. Sign in through the browser, and the assistant works in your workspace with your role.

This repository holds the server's listing details only. The server is hosted by Vertical AI, so there's nothing to install or run.

## What it does

- **Build agents.** Create a voice or text agent, write its prompt and greeting, add tools that call your systems, and give it a knowledge base.
- **Check before you ship.** See what blocks publishing, write test scenarios, run them, and read the transcripts and results.
- **Talk to it.** Hold a text conversation with the draft, or have it ring your phone so you can hear it.
- **Publish and undo.** Publish a tested draft so the next call uses it, or roll the draft back up to ten changes.
- **Review real calls.** List calls with each caller's summary, topic and urgency, and read any call in full.
- **Read the guides.** The building guides and the docs are served by the server itself, so your assistant follows the same rules as the app.

Anything that publishes, deletes, changes what live callers get or spends money on calls or test runs asks you first.

## Connect

| | |
|---|---|
| URL | `https://app.verticalai.com.au/api/mcp` |
| Transport | Streamable HTTP |
| Authentication | OAuth sign-in in the browser, with dynamic client registration and PKCE. No API key to copy |
| Scopes | `agent:read`, `agent:write`, `agent:delete`, `workspace:admin` |
| Registry name | `au.com.verticalai/mcp` in the [Official MCP Registry](https://registry.modelcontextprotocol.io/v0.1/servers?search=au.com.verticalai/mcp) |

The first call opens a browser to sign in. The consent screen asks which workspace the connection reaches, one or all of yours, and whether it's read-only. Add `?read_only=1` to the URL to keep a connection to reads.

### VS Code and GitHub Copilot

[Install in VS Code](https://vscode.dev/redirect?url=vscode%3Amcp%2Finstall%3F%257B%2522name%2522%253A%2522vertical-ai%2522%252C%2522type%2522%253A%2522http%2522%252C%2522url%2522%253A%2522https%253A%252F%252Fapp.verticalai.com.au%252Fapi%252Fmcp%2522%257D), or add it to `.vscode/mcp.json`:

```json
{
  "servers": {
    "vertical-ai": {
      "type": "http",
      "url": "https://app.verticalai.com.au/api/mcp"
    }
  }
}
```

Start the server from the file or the MCP view, sign in when VS Code asks, then use it from Copilot Chat in agent mode.

### Other clients

Any client that takes a remote MCP server by URL works. For clients that read an `mcpServers` config:

```json
{
  "mcpServers": {
    "vertical-ai": {
      "type": "http",
      "url": "https://app.verticalai.com.au/api/mcp"
    }
  }
}
```

Steps for Claude, Cursor, Windsurf and ChatGPT are in [Connect your assistant](https://docs.verticalai.com.au/docs/platform/connect-your-assistant).

## Use it

Ask in plain language:

```text
List my agents.
```

```text
Open my support agent. Tighten the greeting, add a tool that looks up an
order by its number, and tell me what's blocking publish.
```

```text
Run my support agent's tests and tell me which ones failed and why.
```

```text
Who rang yesterday, and what did they want?
```

A client sees the build, test and ship tools as soon as it connects. The rest, from caller routing to answering hours, it finds with `search_tools`. Every tool is in the [tool reference](https://docs.verticalai.com.au/docs/platform/mcp-tool-reference).

### The owner connection

A personal assistant that runs your day doesn't need the building tools. Point it at `https://app.verticalai.com.au/api/mcp/owner` instead: who rang and what they wanted, close early or reopen, and the closed message. It can't build or edit an agent.

## Account

You need a Vertical AI workspace. The 7-day trial needs no card. See [pricing](https://verticalai.com.au/pricing).

## Docs

- [Connect your assistant](https://docs.verticalai.com.au/docs/platform/connect-your-assistant)
- [MCP tool reference](https://docs.verticalai.com.au/docs/platform/mcp-tool-reference)
- [Programmatic access](https://docs.verticalai.com.au/docs/platform/programmatic-access)

## Data

By default every call stays in Australia: call audio, speech recognition, the voice, the AI model, recordings and transcripts.

## Contact

hello@verticalai.com.au. Vertical AI Pty Ltd, Perth, ABN 73 695 607 946.
