---
name: derebrand-claude-code
description: Re-apply the "Assistant" rebrand (neutral name, icon, and colors) to the installed Claude Code VSCode extension after a manual update overwrites it. Use when the user says "rebrand the extension", "de-claude", "reapply the rebrand", "I updated the extension", or "/derebrand-claude-code".
---

Run the bundled script and report its output. When installed as a plugin, use
`${CLAUDE_PLUGIN_ROOT}`; if cloned into `~/.claude/skills`, use that path instead:

```bash
bash "${CLAUDE_PLUGIN_ROOT:-$HOME/.claude/skills/derebrand-claude-code}/rebrand.sh"
```

- Renames the activity-bar title, view names, and command-palette entries from "Claude Code" to "Assistant"; swaps the sidebar icon for a neutral chat-bubble glyph; neutralizes the brand oranges and the red input focus ring; and rewrites a curated set of visible prose phrases — across every installed version folder (`.vscode` and `.vscode-server`).
- Idempotent — safe to run repeatedly; already-patched folders are skipped.
- To use a different name: append it as an argument, e.g. `rebrand.sh Copilot`.
- Only touches the extension chrome (package.json, logo SVGs, webview css/js strings + colors) — never the minified logic or the CLI binary. Semantic colors (error red, warning amber) are left alone.

After it runs, tell the user to reload: Command Palette → **Developer: Reload Webviews** (or fully restart VSCode) — a plain "Reload Window" often keeps the cached webview CSS.
