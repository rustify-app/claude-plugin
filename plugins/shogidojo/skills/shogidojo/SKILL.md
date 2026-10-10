---
name: shogidojo
description: Review the user's shogi games on Shogi Dojo, look up how players continue from a position, and save positions as a review (quiz) list. Use when the user asks about their own shogi games, a game's moves or KIF record, what is usually played from a shogi position, or wants to practise positions they got wrong.
---

# Shogi Dojo

Shogi Dojo (shogidojo.online) is an online shogi dojo: people play, review their games with an engine, and train with next-move quizzes collected in review lists.

The Shogi Dojo tools act as the connected account. They reach that account's own games and review lists, plus the aggregated statistics anyone can see in the position explorer.

## Finding a game

1. Call `list_games` first. It returns the account's own games, newest first, each with its `id`, opponent, result and date. Narrow it with `limit`, `before` (for the next page), `result` or `opponent` rather than reading many games.
2. If the user names an opponent or a day, match it from the list. If more than one game could be meant, ask which one before going further.

## Reading a game

- `read_game` returns one game: its players, result and time control, every move both in USI (`7g7f`, `8h2b+`, `P*5e`) and in Japanese notation (`▲7六歩`), the SFEN of each position, and the KIF record.
- Refer to moves by their number and in the notation the user uses. Quote moves from the record; never invent a move that was not played.
- Moves in USI are the ones to pass to other tools. Show the user the notation they will recognise.
- If the user wants the record itself, give them the KIF as returned; do not reformat it.

## Exploring a position

- `explore_position` takes a position as SFEN (`lnsgkgsnl/1r5b1/ppppppppp/9/9/9/PPPPPPPPP/1B5R1/LNSGKGSNL b - 1`), not as KIF or a move list. Take the SFEN from `read_game`, or build it carefully from what the user gives you.
- It returns the moves players chose from that position in Shogi Dojo's game database, with how often each was played and its share, optionally for one rank band. These are statistics from human games, not an engine evaluation; say so when it matters.
- A position with few or no games has little or no data. Say that, rather than drawing conclusions from one or two games.

## Review lists

- `list_review_lists` shows the account's review (quiz) lists and how many positions each holds.
- `create_review_list` creates a **new** list from positions, each `{ sfen, answerUsi, comment }`: the position, the right move in USI, and a short explanation. It never edits, adds to or deletes an existing list, and no tool can.
- Before creating a list, tell the user which positions and answers you are about to save, and use the name they asked for. Choose answers you can justify from the game and the explorer; if you are unsure of the right move, say so in the comment rather than guessing.
- If the user asks to change, extend or delete an existing list, explain that this connection can only create new lists, and that existing ones are edited in the Shogi Dojo app.
- Read-only connections cannot create lists. If `create_review_list` reports that, tell the user they can reconnect Shogi Dojo with write access.

## What it cannot do

It cannot play or move in a game, run the engine, read another player's private games, or change anything already in the account. Say so plainly when asked.
