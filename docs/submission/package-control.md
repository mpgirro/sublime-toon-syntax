# Package Control submission

Order matters: tag first, then this PR, then the bat PR (see bat.md).

## 1. Prerequisites (this repo)

- [ ] CI green on master
- [ ] Push master to GitHub
- [ ] Tag the release: `git tag 1.0.0 && git push origin 1.0.0` (plain semver, no `v` prefix)
- [ ] Optional but recommended: add a screenshot to the README (listings without one look bare)

## 2. Channel PR

Fork https://github.com/wbond/package_control_channel and add this entry to
`repository/t.json` (alphabetical position within the file):

```json
{
    "name": "TOON",
    "details": "https://github.com/mpgirro/sublime-toon-syntax",
    "labels": ["syntax", "language syntax", "toon"],
    "releases": [
        {
            "sublime_text": "*",
            "tags": true
        }
    ]
}
```

Run their validation locally before opening the PR (from the channel repo root):

```bash
python -m pytest tests  # or follow the channel repo's current CONTRIBUTING instructions
```

## 3. PR body draft

> **Add TOON syntax package**
>
> Adds syntax highlighting for TOON (https://toonformat.dev/), a compact
> JSON-equivalent data format aimed at LLM prompts.
>
> - Repo: https://github.com/mpgirro/sublime-toon-syntax
> - `.sublime-syntax`, `version: 1` feature set, works on ST3 and ST4
> - Standard scope names throughout, tested with 129 syntax-test assertions
> - CI runs the official headless `syntax_tests` binary plus syntect
> - MIT licensed
>
> No existing package claims the `.toon` extension (checked packagecontrol.io search).

Note: verify that last claim right before submitting - search https://packagecontrol.io/search/toon.
