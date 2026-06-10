# Changelog

All notable changes to the ArcScript Language Support extension will be documented
in this file. Format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).
Versioning follows [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [1.0.0] — 2026-06-09

### Added

**Syntax Highlighting** (`syntaxes/arcscript.tmLanguage.json`)
- Knot headers `=== name ===` and stitch headers `= name`
- `VAR` and `CONST` declarations, including optional `: type` annotations
  (`int`, `float`, `str`, `bool`, `Ternary`, `list`, `dict`)
- `~set` assignment directive with dot-path variable support
- Conditional blocks: `~if`, `~elif`, `~else`, `~unknown`, `~when`, `~unless`, `~end`
- `~wait` timed pause with numeric argument
- `~log` and `~assert` debug directives
- Diverts `->` to knots, stitches, `END`, and `MENU`
- Once-choices `*` and always-choices `+`, including `[label]` suppression
  and `{condition}` guards
- Gather markers `-`
- Single-line speaker dialogue `Speaker: text`
- Speaker blocks `::speaker_id … ::`
- BBCode inline markup: `[b]`, `[i]`, `[color=#rrggbb]`, `[shake]`, `[wave]`
- `{expr}` interpolation in narrative text, dialogue, and strings
- Media tags: `%background%`, `%character%`, `%audio%`, `%effect%`,
  `%video%`, `%popup%`, `%minigame%`
- Media sub-fields: `%transition%`, `%duration%`, `%channel%`, `%loop%`,
  `%volume%`, `%stop%`, `%fade_out%`, `%sprite%`, `%pos%`, `%enter%`,
  `%exit%`, `%hide%`, `%scale%`, `%z%`, `%color%`, `%intensity%`,
  `%skip_after%`, `%result_var%`, `%difficulty%`, `%icon%`
- `~define char / place / object … ~end` entity blocks with field name highlighting
- `~triggers … ~end` and `~recipes … ~end` blocks with rule syntax
- `~func verb_X(target) -> _result … ~end` verb function declarations
- `~minigame … ~end` block form (JSON body)
- `INCLUDE "path"` file inclusion directive
- Built-in functions: `any()`, `all()`, `count()`, `visits()`
- Logical operators `and`, `or`, `not`; comparison and arithmetic operators
- Boolean literals `True`/`False`, ternary literals `Unknown`/`T`/`F`/`U`
- Numeric and string literals (including interpolation inside strings)
- Line comments `//` and `##`

**Language Configuration** (`language-configuration.json`)
- Auto-closing pairs for `{`, `[`, `(`, `"`
- Indent-increase after `~if`, `~elif`, `~else`, `~unknown`, `~when`,
  `~unless`, `~define`, `~func`, `~triggers`, `~recipes`, `~minigame`
- Indent-decrease at `~end`, `~elif`, `~else`, `~unknown`
- Code folding for knots, `~define` blocks, `~func` blocks, and `~triggers` blocks
- Word pattern including dot-path separators

**Snippets** (`snippets/arcscript.code-snippets`) — ~45 snippets:
- `knot`, `stitch` — structure
- `var`, `vart`, `const`, `set` — variables
- `if`, `ifelse`, `ifelif`, `ifunknown`, `when`, `unless` — conditionals
- `choices`, `choicecond` — player choices
- `speak`, `speakblock` — dialogue
- `bg`, `charshow`, `charexpr`, `charhide`, `charexit` — visuals
- `audio`, `audiostop`, `effect`, `video`, `popup` — media
- `wait`, `log`, `assert` — timing and debug
- `defchar`, `defplace`, `defobj` — entity definitions
- `triggers`, `trigger`, `recipes`, `funcverb` — sandbox
- `minigame`, `minigameblock`, `mgresult` — minigames
- `menu` — sandbox entry
- `include` — file inclusion
- `any`, `all`, `count`, `visits` — collection predicates
