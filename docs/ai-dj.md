# AI DJ

spotatui can pick music for you. It reads the listening history it already
collects locally, and holds a conversation with a model that can search the
catalogue, look at your queue, and queue tracks. It can also just talk: ask it what
you have been listening to, or answer a question it asks you before it plays
anything.

There are **two ways to use it**, and they share everything below the model —
including the tool list, so both can do exactly the same things:

| | [MCP server](mcp-setup.md) | In-TUI DJ (this page) |
|---|---|---|
| Where you talk | Your coding agent (Claude Code, Codex, …) | A DJ screen inside spotatui |
| Needs an API key | No | Only for the API backends |
| Build with | `--features mcp-server` | `--features ai-dj` |
| Tools | The full set, driven by your agent | The same set, driven by spotatui |

Use the MCP server if you would rather DJ from a window you already have open;
**one command sets it up**, see [`docs/mcp-setup.md`](mcp-setup.md).

## How a turn works

A turn is up to **four steps**. Each step the model either says something, asks for
tools to be run, or both; spotatui runs what it asked for and hands back the
results, so it can look something up before committing. A step with words and no
tool calls ends the turn — which is what an ordinary conversational reply is.