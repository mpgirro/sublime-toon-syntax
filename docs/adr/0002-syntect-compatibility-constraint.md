# Syntect compatibility is a hard constraint

This syntax ships in two consumers: Sublime Text 3 (via Package Control) and bat (https://github.com/sharkdp/bat), which renders through the syntect library. Every highlighting rule must therefore stay inside the feature subset that BOTH the ST3 `version: 1` engine and syntect support - no ST4-only keys, no branch points, no `embed`/`escape`.

Enforcement: the syntax tests run under syntect's `syntest` runner, so a rule that syntect cannot execute fails the build rather than silently breaking bat. Consequence: if a future feature (e.g. delimiter-aware tabular rows) cannot be expressed in this subset, it stays out - bat compatibility wins over highlighting fidelity.
