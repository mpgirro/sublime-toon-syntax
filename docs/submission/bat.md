# bat submission

Do this after the Package Control PR (the submodule should pin the `1.0.0` tag commit).

## 1. Fork and branch

Fork https://github.com/sharkdp/bat, create branch `add-toon-syntax`.

## 2. Add the syntax as a submodule

```bash
git submodule add https://github.com/mpgirro/sublime-toon-syntax.git assets/syntaxes/02_Extra/sublime-toon-syntax
cd assets/syntaxes/02_Extra/sublime-toon-syntax
git checkout 1.1.1   # pin the release tag commit
cd -
```

## 3. Regression test sample

Copy `docs/submission/bat/sample.toon` (from this repo) to
`tests/syntax-tests/source/TOON/sample.toon` in the bat repo. The sample is
self-authored for this purpose and MIT licensed - state that in the PR.

## 4. Regenerate assets and fixtures

Follow bat's current instructions in `doc/assets.md` (script names change; as of
writing: `assets/create.sh` to rebuild the syntax set, then the syntax-test
update script to generate `tests/syntax-tests/highlighted/TOON/`). Run the
regression test suite and make sure TOON passes.

## 5. PR body draft

> **Add syntax highlighting for TOON**
>
> Adds TOON (https://toonformat.dev/, `.toon`), a compact JSON-equivalent data
> format aimed at LLM prompts.
>
> - Syntax source: https://github.com/mpgirro/sublime-toon-syntax (MIT), pinned at `1.0.0`
> - `version: 1` sublime-syntax; the repo's CI runs its 129 syntax-test
>   assertions under syntect itself, so syntect compatibility is enforced, not assumed
> - Sample file is self-authored for this PR, MIT
> - `Highlighting sample`: attach `bat` screenshot of `sample.toon` after building assets
