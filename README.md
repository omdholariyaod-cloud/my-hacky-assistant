# my-hacky-assistant

A simple Slack bot that responds to slash commands. Get cat facts, jokes, and check latency right from Slack.

## What it does

| Command | What happens |
|---|---|
| `/my-hacky-assistant` | Shows bot latency (ping) |
| `/my-hacky-assistant-help` | Lists all commands |
| `/my-hacky-assistant-catfact` | Returns a random cat fact |
| `/my-hacky-assistant-joke` | Returns a random joke |

## Prerequisites

- [Node.js](https://nodejs.org) version 20 or higher
- A [Slack workspace](https://slack.com/create) where you can install apps

## Set up a Slack App

1. Go to [api.slack.com/apps](https://api.slack.com/apps) and click **Create New App**.
2. Choose **From scratch**. Pick a name and your workspace.
3. Under **Socket Mode**, turn it on. Create an app-level token with the `connections:write` scope. Copy the token (starts with `xapp-`).
4. Under **OAuth & Permissions**, add the `commands` scope. Install the app to your workspace. Copy the bot token (starts with `xoxb-`).
5. Under **Event Subscriptions**, turn it on.
6. Under **Slash Commands**, create these four commands:
   - `/my-hacky-assistant` — Description: Check bot latency
   - `/my-hacky-assistant-help` — Description: Show help
   - `/my-hacky-assistant-catfact` — Description: Get a cat fact
   - `/my-hacky-assistant-joke` — Description: Get a joke
7. Click **Install to Workspace** and approve.

## Install and run

```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/my-hacky-assistant.git
cd my-hacky-assistant

# Install dependencies
npm install

# Create a .env file and add your tokens
echo "SLACK_BOT_TOKEN=xoxb-your-token-here" > .env
echo "SLACK_APP_TOKEN=xapp-your-token-here" >> .env

# Start the bot
node index.js
```

You should see `bot is running!` in the terminal. Go to Slack and type `/my-hacky-assistant` in any channel where the bot is present.

## How it works

The bot uses [Socket Mode](https://api.slack.com/apis/socket-mode) to connect to Slack over WebSocket. No public URL or server needed.

- `@slack/bolt` handles the Slack connection and command routing.
- `axios` fetches data from external APIs (cat facts and jokes).
- `dotenv` loads your tokens from the `.env` file.

## Project structure

```
my-hacky-assistant/
├── index.js          # All bot logic (61 lines)
├── package.json      # Dependencies and metadata
├── .env              # Your Slack tokens (not tracked by git)
└── .gitignore        # Ignores node_modules and .env
```

## License

ISC
