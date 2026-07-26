# bat submission

Status: PREPPED, DO NOT SUBMIT YET. Branch `add-toon-syntax` is pushed to the
fork https://github.com/mpgirro/bat and contains everything the PR needs.

## Blocker: inclusion criteria

bat's `doc/assets.md` requires **more than 10,000 downloads on
packagecontrol.io** before a syntax qualifies for inclusion. Submit only after
the Package Control package has crossed that bar (or upstream criteria change).
Before submitting: rebase the branch on bat master and bump the submodule pin
to the then-current release tag.

## What the branch contains

- `assets/syntaxes/02_Extra/sublime-toon-syntax` submodule pinned at `1.1.1`
- `tests/syntax-tests/source/TOON/sample.toon` (self-authored, MIT) + `LICENSE.md` note
- `tests/syntax-tests/highlighted/TOON/sample.toon` fixture, generated with the
  documented `update.sh` options (bat 0.26.1 + the same syntax content as the
  pin; regenerate via `tests/syntax-tests/update.sh` if upstream CI disagrees)
- CHANGELOG entry under `## Syntaxes` (replace `#XXXX` with the PR number after opening)
- Deliberately NOT included: `assets/syntaxes.bin` (regenerated before each bat
  release; PRs must not touch it, per `doc/assets.md`)

## Open the PR (when eligible)

https://github.com/sharkdp/bat/compare/master...mpgirro:bat:add-toon-syntax

Title: `Add syntax highlighting support for TOON`

Body draft:

> Adds TOON (https://toonformat.dev/, `.toon`), a compact JSON-equivalent data
> format aimed at LLM prompts.
>
> - Syntax source: https://github.com/mpgirro/sublime-toon-syntax (MIT),
>   pinned at its release tag; available on Package Control as "TOON" with
>   <N> downloads
> - `version: 1` sublime-syntax; the repo's CI runs its syntax tests under
>   syntect itself, so syntect compatibility is enforced, not assumed
> - Sample file is self-authored for this PR (MIT, see LICENSE.md next to it)
> - Highlighting sample: <attach `bat` screenshot of sample.toon>
