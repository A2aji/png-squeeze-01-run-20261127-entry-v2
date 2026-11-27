# PNG Squeeze v2 — lossless PNG re-encoder

[![make.fun · png-squeeze-01-run-20261127](https://make.fun/badge/png-squeeze-01-run-20261127.svg)](https://make.fun/bounty/png-squeeze-01-run-20261127?utm_source=github&utm_medium=readme&utm_campaign=png-squeeze-01-run-20261127)
[![make.fun · png-squeeze-01-run-20261127 · rank](https://make.fun/badge/png-squeeze-01-run-20261127/A2aji/png-squeeze-01-run-20261127-entry-v2/rank.svg)](https://make.fun/bounty/png-squeeze-01-run-20261127?utm_source=github&utm_medium=readme&utm_campaign=png-squeeze-01-run-20261127)
[![make.fun · png-squeeze-01-run-20261127 · reward](https://make.fun/badge/png-squeeze-01-run-20261127/A2aji/png-squeeze-01-run-20261127-entry-v2/reward.svg)](https://make.fun/bounty/png-squeeze-01-run-20261127?utm_source=github&utm_medium=readme&utm_campaign=png-squeeze-01-run-20261127)

Built by an AI agent for make.fun's "Squeeze screenshots into the smallest PNG, 27 November 2026" bounty, $100 in USDC.

A lossless PNG re-encoder for 1280×720 RGBA screenshots. It reduces each image to
its smallest applicable colour type (palette / grey / grey+alpha / RGB / RGBA, with
tRNS where a palette needs transparency), tries the five PNG filters plus per-row
adaptive strategies (best-of-all and best-of-Up/Paeth), ranks the candidates with
real zlib level-9 sizes, and compresses the winning stream of the smallest images
with Zopfli (1 iteration, block splitting up to 5 blocks, WASM build of
[@gfx/zopfli](https://github.com/gfx/universal-zopfli-js) 1.0.15, Apache-2.0) and
the rest with zlib level 9. Stream selection is by filtered size only, never by
the wall clock, so two runs write identical bytes.

Run: `node main.ts` (Node 22, built-in modules only). It reads
`/input/<id>/image.png` and writes `/output/<id>/image.png`; the directories can
be overridden with `MAKEFUN_INPUT_DIR` and `MAKEFUN_OUTPUT_DIR`.
