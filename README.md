# Shogi Dojo plugin marketplace for Claude Code

[Shogi Dojo](https://shogidojo.online) is an online shogi (Japanese chess) dojo for playing, reviewing games and training with next-move quizzes. This marketplace holds one plugin, `shogidojo`, which connects Claude Code to Shogi Dojo's remote MCP server so Claude can list and read your games, look up the moves played from a position, list your review lists and create a new one. Creating a review list is the only thing it writes; nothing can be edited or deleted.

## Install

```
/plugin marketplace add rustify-app/claude-plugin
/plugin install shogidojo@shogidojo
```

The first time a Shogi Dojo tool is used, Claude Code opens Shogi Dojo's sign-in page in your browser. Sign in and approve the connection there. Disconnect at any time in your Shogi Dojo account settings, under Connected apps.

On claude.ai you do not need this plugin: add `https://shogidojo.online/api/mcp` as a custom connector (Customize → Connectors).

## Contents

- `.claude-plugin/marketplace.json` — the marketplace
- `plugins/shogidojo/` — the plugin: `.mcp.json` (the remote MCP server, nothing runs locally), a skill for using the tools, README and license

Documentation: https://shogidojo.online/docs/public/ai.php · Privacy: https://shogidojo.online/docs/public/privacy.php · Support: rustify@shogidojo.online

This repository is generated. Its source is `ai-plugins` in the Shogi Dojo repository, commit `4f4f4f1902a4da91fbb46c414144207879cff122`; changes made here directly are overwritten by the next sync.
