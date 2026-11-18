# Tiny Chess — a 4 KB chess engine

![Python](https://img.shields.io/badge/Python-3.13-blue)
![Size](https://img.shields.io/badge/main.py-4058%20bytes-brightgreen)
![License](https://img.shields.io/badge/license-MIT-green)

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

## Layout

- `main.py` — the whole entry (unpacker + packed engine), stdlib only.
- `LICENSE` — MIT.

Built and tested against the competition dev kit's practice gauntlet
(house alpha-beta anchors rated 855–1712).

## Links

- Competition: https://make.fun (tiny-chess-01)
- Author: https://github.com/Kamrul112M
