# sublime-toon

TOON syntax highlighting package for Sublime Text 3.

## Stack

- Sublime Text 3 package. No build tooling; Sublime loads files straight from its `Packages/` directory.
- Syntax definition: `.sublime-syntax` (YAML). Use it, not the legacy `.tmLanguage` XML format.

## Conventions

- Target ST3: stick to `version: 1` sublime-syntax features; avoid ST4-only additions.
- Use standard scope names from https://www.sublimetext.com/docs/scope_naming.html so all color schemes work.

## Commands

```bash
# Install for local development (macOS): symlink repo into Sublime's Packages dir
# Symlink name must be TOON: Package Control installs to Packages/TOON/ and the
# syntax test header points there.
ln -s "$PWD" "$HOME/Library/Application Support/Sublime Text 3/Packages/TOON"
```

## Testing

- Write Sublime syntax tests: `syntax_test_*.toon` files whose first line is the syntax-test header comment pointing at the `.sublime-syntax` file.
- Run them inside Sublime via Tools > Build on the test file. Highlighting changes ship only with passing syntax tests covering the changed rules.
- No Sublime install on this machine: run tests headlessly via syntect's `syntest` instead (recipe in README > Development). syntect must stay green regardless - bat compatibility is a hard constraint (docs/adr/0002).

## External Docs

- **TOON format spec** - https://toonformat.dev/
  - READ when adding or changing highlighting rules. Derive token grammar from the spec, never from guesswork.
- **Sublime syntax definition reference** - https://www.sublimetext.com/docs/syntax.html
  - READ when writing or modifying `.sublime-syntax` files.
