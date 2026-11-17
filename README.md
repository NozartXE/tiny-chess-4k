# tiny-chess-4k

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/NozartXE/tiny-chess-4k/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/NozartXE/tiny-chess-4k/reward.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in 4 KB of Python: 0x88 board, negamax alpha-beta with PVS, null-move pruning, late-move reductions, a transposition table and quiescence search, and a tapered piece-square evaluation. Pawns and kings use packed tables; knights, bishops, rooks and queens use a compact positional formula. It searches to a 30,000-node cap, never a clock, so every move is deterministic.

## Engine design

The engine searches a 0x88 board with Python negamax and principal variation search (PVS).
Its transposition table supplies move-ordering hints; search also uses null-move pruning and simplified late-move reductions (LMR).
Quiescence is folded into the search.
Evaluation is tapered: pawns and kings use piece-square tables, while other pieces use a centrality formula.
Each move has a fixed 30,000-node cap, with no clock; results are fully deterministic.
The shipped `main.py` is the readable source minified and LZMA-packed in a two-line `exec` wrapper.
This is the same build technique used by the competition's house baseline.

## Run it

```sh
MAKEFUN_ENV_URL=<env url> python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=hr2ehgtj&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>

## Verification

Standard-start perft at depths 1–3: 20 / 400 / 8,902; Kiwipete at depths 1–2: 48 / 2,039.
Move choice is deterministic with a fixed node cap and no wall-clock use; repeated runs of the same game produce identical moves.
`main.py` is 4,083 bytes, under the competition's 4,096-byte cap.
The repository contains 4 files.
