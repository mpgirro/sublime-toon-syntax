# TOON for Sublime Text

[![CI](https://github.com/mpgirro/sublime-toon-syntax/actions/workflows/ci.yml/badge.svg)](https://github.com/mpgirro/sublime-toon-syntax/actions/workflows/ci.yml)

Syntax highlighting for [TOON](https://toonformat.dev/) (Token-Oriented Object Notation) in Sublime Text - and in [bat](https://github.com/sharkdp/bat), which reads the same `.sublime-syntax` format.

<!-- TODO: add a screenshot of a highlighted .toon file (open sample from docs/submission/bat/sample.toon in ST) -->

## Installation

### Package Control

Once the package is accepted: Command Palette > `Package Control: Install Package` > `TOON`.

### Manual (Sublime Text)

Clone into your `Packages/` directory as `TOON` (macOS path shown):

```bash
git clone https://github.com/mpgirro/sublime-toon-syntax.git \
  "$HOME/Library/Application Support/Sublime Text 3/Packages/TOON"
```

### bat

Until bundled with bat itself, install as a local syntax:

```bash
mkdir -p "$(bat --config-dir)/syntaxes"
git clone https://github.com/mpgirro/sublime-toon-syntax.git "$(bat --config-dir)/syntaxes/sublime-toon-syntax"
bat cache --build
bat sample.toon   # highlighted
```

## What gets highlighted

Comments, keys (quoted and unquoted), array headers with length markers `[N]`, delimiter markers (`,` / tab / `|`) and `{field,lists}`, list items, double-quoted strings with escape validation, numbers, `true`/`false`/`null`. Tabular rows get value-token highlighting; they are deliberately not delimiter-aware (see `docs/adr/0001-stateless-line-oriented-highlighting.md`).

## Development

```bash
# Symlink for live development (macOS); the name TOON matters
ln -s "$PWD" "$HOME/Library/Application Support/Sublime Text 3/Packages/TOON"
```

Tests live in `syntax_test_toon.toon`. Run them inside Sublime via Tools > Build, or headlessly with [syntect](https://github.com/trishume/syntect)'s test runner (this also proves bat compatibility):

```bash
git clone --depth 1 https://github.com/trishume/syntect.git
cargo build --example syntest --manifest-path syntect/Cargo.toml
mkdir -p /tmp/pkg && ln -sfn "$PWD" /tmp/pkg/TOON
syntect/target/debug/examples/syntest syntax_test_toon.toon /tmp/pkg
```

## License

MIT - see [LICENSE](LICENSE).
