# Shogi Dojo for Claude

Shogi Dojo is an online shogi (Japanese chess) dojo: play, review your games with an engine, and train with next-move quizzes. Connect it, and you can ask the AI to find your recent games, go through one move by move, see how other players continued from a position, and save the positions you got wrong as a review list to practise.

What it can do:
• List your own games, newest first, filtered by result or opponent
• Read one game in full: players, result, time control, every move in USI and in Japanese notation, and the KIF record
• Explore a position: the moves players chose from it in Shogi Dojo's game database, with how often each was played and its share, by rank band
• List your review (quiz) lists
• Create a new review list from positions, each with the right move and a comment

Creating a review list is the only thing it writes. It never edits or deletes an existing list, a game or anything else in your account, and that is enforced by Shogi Dojo's server, not left to the AI.

You sign in to Shogi Dojo and approve the connection on a Shogi Dojo page that names the app and whether it may only read or also create review lists. The AI acts as your account and reaches only your own games and lists, plus the statistics anyone can see in the position explorer. Disconnect at any time in your Shogi Dojo account settings, under Connected apps.

Limitations: it cannot play or move in a game, run the engine, read other players' private games, or change or delete anything already in your account.

## What this plugin contains

- `.mcp.json` — connects Claude to Shogi Dojo's remote MCP server at `https://shogidojo.online/api/mcp` over Streamable HTTP. It runs nothing on your computer.
- `skills/shogidojo/SKILL.md` — how to use the Shogi Dojo tools well: find the game first, quote moves from the record, pass positions as SFEN, and only create the review lists you were asked for.

## Tools

- `list_games` (List my games) — read-only
- `read_game` (Read a game) — read-only
- `explore_position` (Explore a position) — read-only
- `list_review_lists` (List my review lists) — read-only
- `create_review_list` (Create a review list) — writes: creates a new review list, never edits or deletes

## Sign-in and data

The first time a tool is used, Claude opens Shogi Dojo's sign-in page. You sign in to Shogi Dojo and approve the connection on a page that names the app and what it may do (OAuth 2.1 with PKCE). Claude then acts as your account and reaches only your own games and review lists, plus the aggregated statistics anyone can see in the position explorer.

What the tools return — your games (opponents' display names, results, dates, moves and KIF records), your review lists, and move statistics for a position — is sent to Claude when a tool is called. Shogi Dojo never receives your conversation with Claude. The plugin sends data to no destination other than Shogi Dojo's MCP server.

Disconnect at any time in your Shogi Dojo account settings, under Connected apps. A connection unused for 90 days ends on its own.

- Documentation: https://shogidojo.online/docs/public/ai.php
- Privacy policy: https://shogidojo.online/docs/public/privacy.php
- Terms: https://shogidojo.online/docs/public/terms.php
- Support: https://shogidojo.online/docs/public/contact.php (rustify@shogidojo.online)

## License

Apache-2.0. See LICENSE.
