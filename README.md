# psspss

A household of AI cats on your phone, powered by your own Claude.

Cats prowl your Gmail, calendar and docs through the connectors you already have in Claude,
drop what matters at your door as push notifications, and ask before they do anything that
sends, books or deletes. Each cat has a job. They think with your Claude subscription (or
Codex, or a local model) on your own Mac. No new AI bill.

## Install (Claude Code on a Mac)

```
/plugin marketplace add sameeeeeeep/psspss
/plugin install psspss@psspss
/psspss:setup
```

Setup creates your household, starts a small runner on your Mac (a login item), and opens
psspss.dev with a QR code. Scan it with your phone, add it to your home screen, done.

| Command | |
|---|---|
| `/psspss:setup` | Set up (or re-pair) this Mac |
| `/psspss:pair` | Fresh QR for another phone or laptop |
| `/psspss:status` | Is the runner up? |
| `/psspss:uninstall` | Stop the runner (`forget` to delete this Mac's login) |

## How it works

- **Your Mac** runs `runner.mjs` (Claude Agent SDK). It dials out to your household on psspss.dev,
  so nothing on your Mac is exposed. It uses your Claude Code login and your claude.ai connectors.
- **Reads** (search, get, list) run straight away. **Writes** (send, create, delete) wait for an
  Approve tap on your phone. Shell and file tools are off entirely.
- **When your Mac sleeps**, cats fall back to a small free model and say they're away.
- **psspss.dev** stores your cats' chats, memory and gifts, and sends notifications.

The source for this plugin is the bundled `bin/` files; they're built from the psspss app repo.
