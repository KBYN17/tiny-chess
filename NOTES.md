# TinyChess — notes

Engine: 0x88 board, alpha-beta + PVS, null-move pruning, quiescence
(captures + promotions), transposition table, killer + history moves,
piece-square tables. Fixed budget 100,000 nodes/move, no clock, no
randomness, stdlib only. Env driver: reads MAKEFUN_ENV_URL, loops
POST /game, /move, /resign. Source: engine.py (readable); main.py is
the kit-packed entry (node cli/makefun.mjs compress engine.py).

Perft (packed main.py): startpos d3=8902, d4=197281; kiwipete
d3=97862. All correct.

Practice gauntlet (kit server.mjs, anchors 855/1073/1199/1392/1497/1596):
- trial-0 @75k nodes: 1W 4D 1L = 3.0 pts, Elo 1279
- trial-1 @100k nodes: 2W 2D 2L = 3.0 pts, Elo 1279
- trial-2 @100k nodes: 3W 2D 1L = 4.0 pts, Elo 1451
Mean practice Elo 1336 (floor 1154, margin +182).

Fix vs round 1: engine rewritten fresh (never read old source); root
now searches the previous iteration's best move first (iterative
deepening), which fixed shallow-depth blunders (was 0-0-6 in trial-0).
