---
description: Set up psspss — your cats on your phone, powered by this Claude
allowed-tools: Bash(node:*)
---

Run this and wait for it to finish (it can take up to a minute while the runner connects):

```
node "${CLAUDE_PLUGIN_ROOT}/bin/psspss.mjs" setup
```

Then tell the user, briefly:
- Whether the runner is up (the ✓ / ! lines).
- That their browser just opened psspss.dev/welcome, which pairs this Mac and shows a QR for their phone.
- The 6-character pairing code from the output (format ABC-DEF), in case they'd rather type it at psspss.dev/pair. It works for 10 minutes.
- On iPhone: open in Safari → Share → Add to Home Screen → open from there → turn on notifications.
- Their cats can use the connectors they've set up in Claude (claude.ai/settings/connectors); adding Gmail or Calendar there makes cats more useful.

Don't paste the QR block itself; the browser shows a cleaner one. If the command failed, show the ✗ line and suggest a fix.
