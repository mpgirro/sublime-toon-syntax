# Package Control submission

Status: PREPPED. Branch `add-toon-syntax` is pushed to the fork
https://github.com/mpgirro/package_control_channel with the `repository/t.json`
entry (formatter-clean). Release `1.1.1` is tagged; `.gitattributes`
export-ignores non-package files; packagecontrol.io has no existing TOON
package (verified 2026-07-26).

## Open the PR

https://github.com/wbond/package_control_channel/compare/master...mpgirro:package_control_channel:add-toon-syntax

Title: `Add TOON`

Body (their PULL_REQUEST_TEMPLATE, boxes reflect actual state):

```markdown
- [x] I'm the package's author and/or maintainer.
- [x] I have read [the docs][1].
- [x] I have tagged a release with a [semver][2] version number.
- [x] My package repo has a description and a README describing what it's for and how to use it.
- [x] My package doesn't add context menu entries. *
- [x] My package doesn't add key bindings. **
- [x] Any commands are available via the command palette.
- [x] Preferences and keybindings (if any) are listed in the menu and the command palette, and open in split view.
- [x] If my package is a syntax it doesn't also add a color scheme. ***
- [x] I use [.gitattributes][3] to exclude files from the package: images, test files, sublime-project/workspace.

[1]: https://docs.sublimetext.io/guide/package-control/submitting.html
[2]: https://semver.org
[3]: https://www.git-scm.com/docs/gitattributes#_export_ignore

My package is a syntax highlighting package for TOON (Token-Oriented Object
Notation, https://toonformat.dev/), a compact JSON-equivalent data format
aimed at LLM prompts. It uses standard scope names, targets ST3 and ST4
(`version: 1` sublime-syntax), and CI runs the official headless
`syntax_tests` binary plus syntect on every change.

There are no packages like it in Package Control.
```

Note (their AGENTS.md): the review is a human-to-human conversation - respond
to reviewer feedback yourself.
