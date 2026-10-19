# Third-party code

`psspss/bin/*.mjs` bundle these MIT-licensed packages: `agents` (Cloudflare), `partysocket`,
`zod`, `ws`, `uqr`.

The Claude Agent SDK (`@anthropic-ai/claude-agent-sdk`) is **not** included. `/psspss:setup`
installs it from npm into `~/.psspss` on your Mac; its use is subject to Anthropic's terms.
