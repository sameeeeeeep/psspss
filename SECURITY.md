# psspss security

## What runs where

| Piece | Where | Holds |
|---|---|---|
| Runner (`~/.psspss/runner.mjs`) | Your Mac, as a login item | Your household's runner token (`~/.psspss/runner.json`, mode 600). Uses your local Claude Code sign-in; never sees or sends your Anthropic credentials. |
| Household + cats | psspss.dev (Cloudflare Durable Objects) | Chats, cat memory notes, gifts, tasks, routines, push subscriptions, hashed device tokens. |
| Connectors (Gmail, Drive, …) | Inside your own Claude Code | Your claude.ai connector logins stay in Claude. psspss.dev never receives connector credentials. |

The runner **dials out** to psspss.dev over a WebSocket. Nothing on your Mac listens for inbound connections.

## Households are isolated

- Each household has a random id and its own credentials. Every socket and API call is checked
  against that household: device tokens for phones and browsers, one runner token for your Mac.
- Tokens are 256-bit random values, stored only as SHA-256 hashes, and revocable per device in the app.
- Pairing codes are 6 characters from a 31-letter alphabet. They last 10 minutes, work at most 3 times,
  and redemption is rate-limited per IP. The iPhone home-screen handoff code is single-use and lasts 24 hours.
- Household creation is rate-limited.

## What a cat can do

- **Reads** (`search…`, `get…`, `list…` tools of connectors you enabled) run straight away.
- **Writes** (send, create, change, delete) stop and ask you with an Approve / Deny card plus a
  notification. No answer within 5 minutes means **deny**. Background runs (prowls, routines) never
  get approvals; they turn proposals into gifts or tasks.
- **Never**: shell, file reads or writes, web fetches, sub-agents, your Claude Code settings, hooks or
  plugins. The runner starts Claude with no built-in tools at all (`tools: []`), an empty working
  folder (`~/.psspss/workspace`), and `settingSources: []`. Connectors outside the allowlist are
  hidden from the model, not just blocked.
- Email and document content is treated as data, not instructions. The approval gate is the backstop
  if a malicious email tries to make a cat act.

## When your Mac sleeps

Cats switch to a small backup model on Cloudflare Workers AI, capped per household per day. It has
no access to your accounts and says so.

## Not yet

- Messages are encrypted in transit (TLS) and at rest by Cloudflare, but not end-to-end.
- A lost unlocked phone can use its device token until you remove that device under Settings → Devices.
- Device tokens travel in the WebSocket URL (over TLS), which is standard for browser WebSockets.

Report issues: open a GitHub issue, or email the maintainer listed on psspss.dev.
