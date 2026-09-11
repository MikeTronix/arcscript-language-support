# Changelog

All notable changes to the ArcScript Language Support extension will be documented
in this file. Format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).
Versioning follows [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [1.0.5] — 2026-09-11

### Added

Catch-up release. The grammar had fallen behind the compiler by eight directives,
one entity type and two media tags — all of them shipped language features that
simply rendered as plain text.

- Block directives: `~achievement`, `~input`, `~grants`, `~display`, `~sparkle`,
  and the `~minigame … ~end` form
- Line directives: `~pov`, `~location`, and `~sparkle off`
- `~define objective` (the alternation accepted only `char|place|object`)
- `%base%` and `%object%` media tags

### Changed

- The drift that caused all of the above is now caught automatically:
  `compiler/tests/test_syntax_coverage.py` in the ArcTree repo reads the
  directives, `~define` types and media tags straight out of the compiler and
  fails if this grammar is missing any. It skips cleanly when this repo is not
  checked out alongside it.

---

## [1.0.4] — 2026-09-01

### Added

- `%flip%` media sub-field (mirrors a character sprite about its vertical axis),
  highlighting and the `charflip` snippet

---

## [1.0.3] — 2026-06-11

### Added

**Game Time support**
- `~calendar … ~end` block highlighting, with `key: value` configuration lines
- `~time advance` and `~time wait_until` directives
- Time builtin functions in expressions: `hour`, `minute`, `day`, `day_of_week`,
  `weekday`, `part_of_day`, `time_str`, `month`, `year`, `clock`, `before`, `after`,
  `between`, `is_weekday`, `on_or_after`, `minutes_until`
- Snippets: `calendar` (full calendar block), `timeadv` (`~time advance`),
  `timewait` (`~time wait_until`)

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
