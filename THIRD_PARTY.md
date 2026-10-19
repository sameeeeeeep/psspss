# Third-party code

`psspss/bin/*.mjs` bundle these MIT-licensed packages: `agents` (Cloudflare), `partysocket`,
`zod`, `ws`, `uqr`.

The Claude Agent SDK (`@anthropic-ai/claude-agent-sdk`) is **not** included. `/psspss:setup`
installs it from npm into `~/.psspss` on your Mac; its use is subject to Anthropic's terms.

`refs-server.mjs` is the MIT-licensed references-mcp server (sameeeeeeep/references-mcp), bundled so cats can bring /refs reference directions.
