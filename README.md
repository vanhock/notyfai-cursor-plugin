# Notyfai

Get push notifications on your phone, telegram, whatever when a Cursor agent needs you or has finished—so you can step away and still respond when it’s waiting for approval or done.

Notyfai is a Cursor plugin that forwards agent events to your service. You get a push when the agent is **blocked** (e.g. waiting for shell, MCP, or file approval) and when the agent **stops**. No need to keep Cursor in the foreground; your phone tells you when to come back. **Secure and simple:** your hook URL stays on your machine or in env; no code or secrets are sent—just event payloads to your private endpoint.

## Install

1. **Install from the Cursor Marketplace**  
   Open the marketplace in Cursor, search for **Notyfai**, and install the plugin.

2. **Get the Notyfai app**  
   Install the Notyfai mobile app for iOS or Android (coming soon!) and sign in. From the app you get a unique hook URL for your account.

3. **Configure the hook URL**  
   The plugin script needs your hook URL. Choose one:

   - Open Cursor terminal from the project root and run:
     ```bash
     echo 'YOUR_HOOK_URL' > .cursor/notyfai-url
     ```
   - Add `.cursor/notyfai-url` to `.gitignore` so the URL is not committed.

4. **Restart Cursor** so it loads the plugin and hooks.

## What triggers notifications

- **Agent blocked** — The agent is waiting for permission (e.g. shell command, MCP call, file read with "ask" or "deny"). A push is sent after a short debounce (about 15 seconds).
- **Agent stopped** — The agent run finished (`stop` event). You get an immediate notification.

All other hook events (session start/end, tool use, file edits, etc.) are sent to the backend for execution tracking and history; they do not trigger push notifications by themselves.

## Setup your own server

You can self-host your own server, setup hook manualy using a script from this repo [main Notyfai repo](https://github.com/vanhock/notyfai) (e.g. `docs/configure-hook.md`).

## License

MIT. See [LICENSE](LICENSE).
