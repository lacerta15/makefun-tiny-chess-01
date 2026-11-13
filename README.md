# tiny-chess-01 entry

A from-scratch chess engine in 4,096 bytes of Python 3.13 standard library,
entered for make.fun's "Build the strongest chess engine in 4 KB of Python"
bounty.

`main.py` is a tiny unpacker (`lzma` + `base64`, both stdlib) around an
lzma-compressed, base85-encoded copy of the actual engine source. The engine
itself is an original mailbox-board move generator (full legality: castling,
en passant, promotion, check detection) plus a negamax alpha-beta search with
quiescence search, MVV move ordering, and a fixed node-budget iterative
deepening loop. The node budget (not wall-clock time) bounds search per move,
so the same position always produces the same move regardless of the
machine's speed, as the rules require for the replayed final.

No network access beyond the competition's env, no model calls, no files
read besides `main.py`'s own bytes.
