# Tiny Chess — 4 KB Python engine

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/BidyutRoy2/tinychess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/BidyutRoy2/tinychess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A hand-written chess engine in a single 4 KB Python file, built for make.fun
`tiny-chess-01`. 0x88 board, legal move generation (castling, en passant,
promotion), PVS + quiescence search with a transposition table, killer moves
and MVV-LVA ordering, tapered piece-square evaluation — all under a fixed
75,000-node budget per move, never a clock, so every trial replays
byte-for-byte.

## Practice results (honest numbers)

6-game practice trials against the house gauntlet, local harness:

| Trial | W–D–L | Elo |
|---|---|---|
| 0 | 2–2–2 | 1,279 |
| 1 | 3–1–2 | 1,364 |
| 2 | 2–1–3 | 1,191 |

Mean Elo **1,278** — passes the 1,154 entry floor on every trial, below the
sunfish baseline's 1,365 practice mean. No move over 10 s (max 5.6 s),
mean think ~2.8 s, no timeouts. Replay verified byte-identical.

## The size rule

- `main.py` is the whole engine: 3,968 bytes as committed (cap 4,096),
  Python 3.13, standard library only. It reads, imports or execs no other
  file in the repository.
- The source is packed with the kit's `makefun compress` (lzma payload +
  unpacker); the readable source lives beside the transcript bundle.
- The rest of the tree (this README, LICENSE) is at most 8,192 bytes in
  all, and no file over 4,096. MIT licence.

## Run it

Grade it with the competition's dev kit:

```sh
makefun grade-local --kit . --bot <this repository> --driver docker
```

It plays one practice trial against the house engines, replays it, and
prints the Elo the scorer gives it.

## License

MIT — see LICENSE.

---

<sub>Entered on [make.fun](https://make.fun/?ref=v36tdgxj&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
