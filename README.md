# derebrand-claude-code

A [Claude Code](https://claude.com/claude-code) plugin that neutralizes the visual branding of the **Claude Code VS Code extension** — renames it to a neutral name and swaps the terracotta/orange accents for gray — and re-applies the change after a manual extension update overwrites it.

It only touches the extension **chrome**: `package.json` display strings, the sidebar logo SVGs, and the webview `index.js`/`index.css` (strings + colors). It never edits the minified logic or the CLI binary, and it leaves semantic colors (error red, warning amber) alone.

## Install (Claude Code plugin)

```
/plugin marketplace add Abhyuday98/derebrand-claude-code
/plugin install derebrand-claude-code@abhyuday-skills
```

Then invoke it anytime with **"reapply the rebrand"** or `/derebrand-claude-code`.

### Or clone as a plain skill

```bash
git clone https://github.com/Abhyuday98/derebrand-claude-code /tmp/dcc \
  && cp -r /tmp/dcc/derebrand-claude-code ~/.claude/skills/derebrand-claude-code
```

## What it changes

- Activity-bar title, view names, command-palette entries: `Claude Code` → `Assistant`
- Sidebar icon → a neutral chat-bubble glyph
- Brand oranges (send button, accents, icons) → neutral gray (`#808080`)
- The red input focus ring (`--vscode-errorForeground`) → gray, scoped to the webview
- A curated set of visible prose phrases ("focus or unfocus Claude", etc.)

Runs across every installed version folder in `~/.vscode` and `~/.vscode-server`. Idempotent — safe to run repeatedly. Keeps a `.bak` of every changed file.

## Custom name

```bash
bash derebrand-claude-code/rebrand.sh Copilot   # instead of "Assistant"
```

## After it runs

Reload VS Code: **Developer: Reload Webviews** (or fully restart) — a plain "Reload Window" often keeps the cached webview CSS.

## Revert

Every changed file has a `.bak` next to it. Restore those, or just let the next
extension update install a clean copy.

## Notes

- Extension auto-update installs a fresh copy under a new version folder; disable
  auto-update and run this after each manual update.
- Unofficial and cosmetic. Not affiliated with Anthropic.

## License

MIT © Abhyuday Samadder
