# tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/Hellboys87/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/Hellboys87/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

**KECIL** — a complete chess engine in 4,062 bytes of Python. The committed
`main.py` is a tiny unpacker stub plus an lzma payload (latin-1 literal);
it decompresses to ~9.2 KB of dense engine source at startup.

Design: 0x88 board with incremental make/unmake (Zobrist hash, tapered
material + piece-square score, pawn bitboards). Negamax with PVS,
iterative deepening to a fixed 60,000-node budget per move (fully
deterministic — no wall clock anywhere), transposition table, null-move
pruning, late-move reductions, check extensions, and a capture/promotion
quiescence search with check evasions. Evaluation: tapered piece-square
tables and passed-pawn bonuses; faster mates score higher, and
repetition and fifty-move draws are scored 0 inside the search.

## Run it

```sh
MAKEFUN_ENV_URL=http://localhost:<port> python3 main.py
```

The engine speaks the make.fun env protocol: it polls `POST /game` and
answers `your_move` states with `POST /move` until the env says `done`.

---
<sub>Entered on [make.fun](https://make.fun/?ref=9xcq3bkm&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
