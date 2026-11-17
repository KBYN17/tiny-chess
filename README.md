[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/KBYN17/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/KBYN17/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

# TinyChess

A chess engine in 4 KB of Python, built for the
[make.fun bounty tiny-chess-01](https://make.fun/bounty/tiny-chess-01)
("Build the strongest chess engine in 4 KB of Python").

Sunfish-style 0x88 board, alpha-beta + PVS, null-move pruning, quiescence,
transposition table, killer + history ordering, piece-square tables. It searches a fixed 100,000 nodes a move — no
clock, no randomness — so a trial's replay matches move for move.

Practice trials play 6 games against the house ladder; the floor to enter
the final is a practice Elo of 1154.

`main.py` is the whole engine: a compressed payload of the readable source
`engine.py`, packed with `makefun compress`. Python 3.13 standard library
only; it reads no other file.

## Run it

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:8080 python3 main.py
```

The program plays the gauntlet through the env: it reads each position
(FEN + legal moves) and answers with a UCI move (e2e4, e7e8q).

## Check the move generator

```sh
python3 engine.py perft 3   # startpos: 8902
python3 engine.py perft 4   # startpos: 197281
```

License: MIT.
