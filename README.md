# LiteScribe MCP server

Search, read and act on your [LiteScribe](https://litescribe.ai) recordings from Claude, ChatGPT, Cursor, VS Code and any other MCP client: meetings, calls, lectures, voice notes and videos, with transcripts, summaries, action items, chapters, screenshots and timestamped quotes.

- **Server URL:** `https://mcp.litescribe.ai/mcp` (remote, Streamable HTTP)
- **Sign-in:** OAuth with your LiteScribe account. You choose read-only or "make changes" on the consent page.
- **Plans:** every LiteScribe plan can connect, including Free.
- **Listed in:** [Claude connectors directory](https://claude.com/connectors/litescribe), [MCP Registry](https://registry.modelcontextprotocol.io/) (`ai.litescribe/litescribe`)
- **Docs:** [litescribe.ai/integrations/mcp](https://litescribe.ai/integrations/mcp/)

LiteScribe records and transcribes in 99 languages on the web, desktop (Windows, macOS, Linux), Chrome extension, iPhone and Android. This server is hosted by LiteScribe; there is nothing to install or run.

## What you can ask

- "What did we decide about pricing in last week's calls?"
- "List my action items from October."
- "Find where Sarah talked about the launch date, with a link to that moment."
- "Show me the slides from the onboarding call." (screenshots taken while recording)
- "Put the Acme calls in my Acme collection."

Answers cite the exact moment with a link that opens the LiteScribe player at that second.

## Connect

### Claude (web, desktop, mobile)

Open [LiteScribe in the Claude connectors directory](https://claude.com/connectors/litescribe) and click Connect. Or: Settings, Connectors, Add custom connector, and paste `https://mcp.litescribe.ai/mcp`.

### Claude Code

```
claude mcp add --transport http litescribe https://mcp.litescribe.ai/mcp
```

Then run `/mcp` in Claude Code and sign in.

### ChatGPT

On chatgpt.com, switch on Developer mode (Settings, Apps, Advanced settings), then Settings, Apps, Create: name it LiteScribe, enter `https://mcp.litescribe.ai/mcp` and choose OAuth. Full steps: [litescribe.ai/integrations/chatgpt](https://litescribe.ai/integrations/chatgpt/).

### Cursor

`~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "litescribe": { "url": "https://mcp.litescribe.ai/mcp" }
  }
}
```

### VS Code

`.vscode/mcp.json`:

```json
{
  "servers": {
    "litescribe": { "type": "http", "url": "https://mcp.litescribe.ai/mcp" }
  }
}
```

## Tools

| Tool | What it does |
|---|---|
| `get_account` | Your plan, minutes left, recording and collection counts |
| `search_recordings` | Find recordings by words, date, collection, speaker, source, device and language |
| `get_recording` | Summary, action items, chapters, speakers, topics, notes, screenshot count |
| `get_transcript` | Speaker turns with timestamps, by time range or page; stored translations |
| `find_moments` | The passages where something was said, with links to that second |
| `list_action_items` | Action items across recordings, with owners and due dates |
| `list_screenshots` | Screenshots taken while recording, with time and what was said then |
| `get_screenshot` | Up to 10 screenshots as images, or short-lived download links to the originals |
| `list_collections` | Your collections (deals, clients, courses, shows) and their other names |
| `get_collection` | One collection's recordings and action items |
| `suggest_collection_members` | Recordings that probably belong in a collection, with the evidence |
| `rename_recording` | Rename a recording (needs "make changes") |
| `add_to_collection` | Add recordings to a collection (needs "make changes") |
| `remove_from_collection` | Take a recording out of a collection (needs "make changes") |
| `create_share_link` | Turn on a recording's share link (needs "make changes") |

Nothing can be deleted through the connector.

## Privacy and security

- Only your own recordings are visible. Recordings in Trash, recordings marked private, and Local Mode recordings that never leave your computer are never returned.
- OAuth 2.1 with PKCE (S256), audience-bound tokens, and an explicit consent page that names the app asking for access.
- Reads call no AI model and use no transcription minutes.
- Recording content is labelled as data, not instructions, in every result.
- Disconnect any app at any time from Integrations in LiteScribe.
- Privacy policy: [litescribe.ai/privacy](https://litescribe.ai/privacy). Support: support@litescribe.ai

## About LiteScribe

[LiteScribe](https://litescribe.ai) is an AI meeting recorder and transcription app: live captions and transcripts, speaker names, summaries and action items, AI chat with your recordings, and on-device transcription in Local Mode. [Get started free](https://litescribe.ai).
