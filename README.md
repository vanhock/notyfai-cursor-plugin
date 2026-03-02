# Notyfai — Quick Hooks for Cursor Agent Status

**Notyfai** is an open-source solution for quick hooks setup for instant status notifications from your Cursor agent. 

Whenever your agent is **blocked** (waiting for shell, MCP, or file approval) or **stops** (run finished), Notyfai forwards the event status to your private endpoint. 

Stay updated on your agent's progress without keeping Cursor in the foreground. Get notified on your phone, Telegram, Slack, or any service of your choice—as soon as the agent needs you or has finished its work.

## Features

- **Quick Hook Setup**: Maps Cursor agent events to a single forwarding script.
- **Open Source & Extensible**: A lightweight, transparent wrapper around Cursor hooks.
- **Secure by Default**: Your hook URL stays on your machine; only event payloads are sent.
- **Compatible**: Works with the [Notyfai mobile app](https://notyfai.com) or any custom webhook backend.

## How It Works

Notyfai uses Cursor's native `hooks.json` to monitor agent activity. Each event triggers a simple shell script (`scripts/notyfai-send.sh`) that forwards the event JSON to your configured `HOOK_URL`.

## Install

1. **Clone this repo** into your Cursor workspace or install from the Cursor Marketplace (coming soon!).
2. **Get a hook URL**:
   - Use the [Notyfai app](https://notyfai.com) for easy push notifications.
   - Or setup your own backend endpoint (e.g., via [notyfai main repo](https://github.com/vanhock/notyfai)).
3. **Configure the URL**:
   Add your endpoint URL to your local environment:
   ```bash
   echo 'https://your-webhook-url.com/...' > .cursor/notyfai-url
   ```
4. **Restart Cursor** to activate the hooks.

## Triggers

You will receive notifications for key agent status changes:
- **Agent Blocked**: When the agent is waiting for permission (shell, MCP, file read/write).
- **Agent Stopped**: When the agent run is complete.
- **Subagent Status**: Track when subagents start or stop.

## License

MIT. See [LICENSE](LICENSE).
