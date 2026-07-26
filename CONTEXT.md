# sublime-toon

Syntax highlighting for the TOON data format in Sublime Text 3. These terms name TOON grammar constructs the way the highlighting rules and tests refer to them.

## Language

**Key-value line**:
A line of the form `key: value` defining one object field.
_Avoid_: property, entry, mapping

**Array header**:
A line introducing an array: `key[N]:` or `key[N]{fields}:`. Carries the length marker and optionally a field list and delimiter marker.
_Avoid_: table header, column header

**Length marker**:
The `[N]` bracket segment in an array header declaring the element count.
_Avoid_: size, count annotation

**Field list**:
The `{a,b,c}` brace segment in an array header declaring the field names each tabular row must supply, once for the whole array.
_Avoid_: columns, schema, header fields

**Tabular row**:
An indented line under an array header holding delimiter-separated values, one element of the array.
_Avoid_: record, table line, data line

**List item**:
A `- value` line, one element of a non-uniform or mixed-type array.
_Avoid_: sequence entry, bullet

**Delimiter**:
The character separating field names in a field list and values in a tabular row: comma, tab, or pipe.
_Avoid_: separator (reserved for the `:` after a key)

**Rule class**:
One group of highlighting rules covering a single construct above; the unit of syntax-test coverage.
