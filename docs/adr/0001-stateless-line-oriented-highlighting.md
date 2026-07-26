# Stateless line-oriented highlighting

TOON marks structure by indentation, and tabular rows are only recognizable via the array header above them. Sublime Text 3's `version: 1` syntax engine has no reliable way to pop a context on dedent (no branch points), so tracking tabular blocks statefully would be fragile YAML-grade hackery. We classify every line independently instead: comment, array header, key-value, list item - and anything else gets generic value-token highlighting only.

Consequence: tabular rows are not delimiter-aware in v1 (a comma inside an unquoted cell can mis-scope a following number). This is deliberate, not an oversight. A delimiter-aware v2 requires a stateful redesign but can keep all existing scope names, so color schemes and tests survive.
