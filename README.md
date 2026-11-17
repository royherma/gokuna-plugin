# GoKuna plugin

Hire a real, ID-checked person from your AI agent. They do something in the physical world (photograph a shelf price or a storefront, hold a sign, record a voice line or a short clip) and send a photo or video as proof. You pay only for results you accept.

This plugin connects your agent to the GoKuna MCP server and adds two skills that teach it how to write a good brief, spend only what you confirm, and review the results. One repo works in Claude Code, Claude, Cursor, Grok Build and Gemini CLI.

## What it does

| Piece | What it gives your agent |
| --- | --- |
| MCP server `https://gokuna.com/api/mcp` | 10 tools: `post_task`, `get_task`, `list_tasks`, `list_submissions`, `view_submission`, `review_submission`, `close_task`, `add_funds`, `redeem_code`, `get_balance` |
| Skill `hire-a-person` | Brief writing, picking reward and slots, and a rule that nothing is spent until you confirm the dollar amount |
| Skill `review-results` | Looking at each photo or video, accepting or rejecting with a reason, closing the task |

Amounts are US cents. Posting a task holds reward x slots from your GoKuna balance; slots nobody takes are returned when the task closes.

## Install

### Claude Code

```
/plugin marketplace add royherma/gokuna-plugin
/plugin install gokuna@gokuna
```

Or test from a local clone: `claude --plugin-dir ./gokuna-plugin`. Then run `/mcp` and sign in to `gokuna`.

### Claude (claude.ai, Cowork)

Customize > Plugins > Add > Upload plugin (zip this folder), then connect GoKuna from the plugin's Connectors tab and sign in.

### Cursor

Copy the repo to `~/.cursor/plugins/local/gokuna`, then run Developer: Reload Window. The plugin has a `.cursor-plugin/plugin.json` manifest.

### Grok Build

The plugin has a `.grok-plugin/plugin.json` manifest and `.mcp.json`. Install it from the xAI plugin marketplace once listed, or add this repo as a plugin source.

### Gemini CLI

```
gemini extensions install https://github.com/royherma/gokuna-plugin
```

### Any other MCP client

Add the remote server: `https://gokuna.com/api/mcp` (streamable HTTP).

## Sign in

- OAuth (default): the client opens a GoKuna sign-in the first time a tool is used. The server supports dynamic client registration, so no client id is needed.
- Clients without OAuth: see https://gokuna.com/for-agents for other ways to connect.

No key or secret is stored in this repo.

## Data and network

The plugin runs no code on your machine. It declares one network endpoint, `https://gokuna.com/api/mcp`, and your agent sends the task text you approve (title, description, instructions, reward, slots, countries), review decisions, and payment requests to it. Photos and videos that contributors submit are returned to your agent through `view_submission`. Docs: https://gokuna.com/for-agents.

## Privacy Policy

GoKuna's privacy policy applies to everything this plugin sends: https://gokuna.com/privacy. Terms: https://gokuna.com/terms.

## Support

Email support@gokuna.com or open an issue at https://github.com/royherma/gokuna-plugin/issues.

## License

MIT, Techguyver Labs. See LICENSE.
