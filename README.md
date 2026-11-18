# Tiny Chess — a 4 KB chess engine

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/Kamrul112M/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/Kamrul112M/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

An original chess engine written for the MakeFun **tiny-chess-01**
competition: the strongest engine that fits in **4,096 bytes of Python**.
`main.py` is a small `lzma` unpacker; the engine itself is packed inside
it and stays fully deterministic — fixed node budget, no clock, no
randomness — so every trial replays move for move.

## How it plays

- Negamax alpha-beta search with a transposition table and PVS
  (principal-variation search), iterative deepening to a fixed node cap.
- Quiescence search over captures and promotions, with every check
  evasion searched when the side to move is in check.
- Check extensions, game-history repetition detection, MVV-LVA move
  ordering with the transposition-table move first.
- Incremental evaluation: material + piece-square tables maintained
  move by move, with a tapered king table (middlegame → endgame).
- Copy-make board updates with Zobrist hashing.

## Run it

The engine talks to the competition environment server:

    MAKEFUN_ENV_URL=http://127.0.0.1:8080 python3 -P -s main.py

## Layout

- `main.py` — the whole entry (unpacker + packed engine), stdlib only.
- `LICENSE` — MIT.

Built and tested against the competition dev kit's practice gauntlet
(house alpha-beta anchors rated 855–1712).

## Links

- Competition: [make.fun bounty — tiny-chess-01](https://make.fun/bounty/tiny-chess-01)
- Author: https://github.com/Kamrul112M
