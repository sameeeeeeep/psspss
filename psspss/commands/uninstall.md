---
description: Stop the psspss runner on this Mac (add "forget" to also delete this Mac's household login)
allowed-tools: Bash(node:*)
---

If the user said "forget" (or wants everything removed), run `node "${CLAUDE_PLUGIN_ROOT}/bin/psspss.mjs" uninstall --forget`; otherwise run `node "${CLAUDE_PLUGIN_ROOT}/bin/psspss.mjs" uninstall`. Confirm in one line. Their cats and chats stay on psspss.dev; they can run /psspss:setup again any time.
