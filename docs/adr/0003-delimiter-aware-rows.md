# Delimiter-aware tabular rows via indent-anchored contexts

Supersedes the row treatment of ADR-0001; its stateless design remains for every other construct and as the fallback when indentation is malformed.

Array headers with a field list push a row context selected by the declared delimiter (comma default, tab, or pipe). The header match captures its leading indent, and the row context pops on the first non-blank, non-comment line not indented deeper than the header (`^(?!\1 |\s*$| *#)` with a backreference to the captured indent) - the heredoc pattern. Comment lines must not pop: the spec strips them in a lexical pre-pass, so they may appear inside a tabular block at any indentation (this also keeps syntax-test assertion lines from killing the context). Backreferences from the pushing match are a `version: 1` feature and syntect implements them - verified by a spike against syntect's runner, and CI re-proves it on every push.

Inside a row, only the declared delimiter is a separator and primitives match as complete cells. Consequences: mismatched delimiters and partial-cell lookalikes (`v1.2`) correctly get no highlighting; malformed indentation mis-scopes at most the offending line because any dedent pops; arity checking (cell count vs `[N]`) remains out of scope - not expressible in this engine.
