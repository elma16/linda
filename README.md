# Linda

Linda is the renamed home for my Fairy-Stockfish fork. It keeps the Stockfish-based variant engine core while focusing on experiments around cylinder chess (wraparound files) and NNUE training. Everything is written in C++17 with optional Python and JavaScript bindings for library use.

## What this project does

- Multi-protocol engine (UCI, UCCI, USI, CECP/XBoard) with the Stockfish search stack.
- Native cylinder chess support alongside the upstream Fairy-Stockfish variant infrastructure for regression checks.
- NNUE-ready: load networks via the `EvalFile` option; training uses the standard Stockfish/Fairy-Stockfish NNUE tooling with cylinder-only data.
- Library bindings: Python (`src/pyffish.cpp`) and JavaScript (`src/ffishjs.cpp`) are exposed from the same C++ core.

## Build

Run engine builds from `src/`:

```bash
make -j2 ARCH=x86-64 build            # release build
make -j2 ARCH=x86-64 debug=yes build  # debug build
make -j2 ARCH=x86-64 largeboards=yes all=yes build  # full variant/large-board build
```

## Run

```bash
./stockfish
setoption name UCI_Variant value cylinder
go movetime 1000
```

Use `./stockfish bench` for a quick sanity check, or `./stockfish check variants.ini` to validate variant configs.

## License

Linda remains distributed under the GPL v3. See `Copying.txt` for details.
