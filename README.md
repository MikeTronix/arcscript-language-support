# ArcScript Language Support

Syntax highlighting, code snippets, and language features for **ArcScript** (`.arc` files) — the visual novel scripting language for browser-based interactive stories.

---

## Features

### Syntax Highlighting

Full token-level highlighting for every ArcScript construct:

| Category | Highlighted Elements |
|---|---|
| **Structure** | `=== knots ===`, `= stitches`, `-> diverts`, `-> END`, `-> MENU` |
| **Declarations** | `VAR`, `CONST`, optional `:type` annotations |
| **Directives** | `~set`, `~if`/`~elif`/`~else`/`~unknown`, `~when`, `~unless`, `~end` |
| **Dialogue** | `Speaker: text` lines, `::speaker` blocks, closing `::` |
| **Choices** | `*` once-choices, `+` always-choices, `[label]` suppression, `{condition}` guards |
| **Media tags** | `%background%`, `%character%`, `%audio%`, `%effect%`, `%video%`, `%popup%` |
| **Minigames** | `%minigame%` tag form, `~minigame … ~end` block form |
| **Entities** | `~define char/place/object … ~end`, field names |
| **Sandbox** | `~triggers … ~end`, `~recipes … ~end`, `~func verb_X … ~end` |
| **Game time** | `~calendar … ~end`, `~time advance`/`wait_until`, time builtins (`hour()`, `weekday()`, `before()`, `on_or_after()`, …) |
| **Expressions** | Dot-paths, `any()`/`all()`/`count()`, `visits()`, operators |
| **BBCode** | `[b]`, `[i]`, `[color=…]`, `[shake]`, `[wave]` |
| **Interpolation** | `{expr}` in text and strings |
| **Debug** | `~log`, `~assert` |
| **Comments** | `//` and `##` line comments |

### Code Snippets

Type a prefix and press `Tab` to expand:

| Prefix | Expands to |
|---|---|
| `knot` | New knot with `-> END` |
| `stitch` | New stitch |
| `var` | `VAR name = value` |
| `vart` | Typed `VAR name: type = value` |
| `const` | `CONST NAME = value` |
| `set` | `~set var = expr` |
| `if` | `~if … ~end` block |
| `ifelse` | `~if … ~else … ~end` |
| `ifelif` | `~if … ~elif … ~else … ~end` |
| `ifunknown` | `~if … ~unknown … ~else … ~end` (ternary logic) |
| `when` | `~when … ~end` |
| `unless` | `~unless … ~end` |
| `choices` | Once-choice group with gather |
| `choicecond` | Conditional `* {cond} [text]` choice |
| `speak` | `Speaker: dialogue` line |
| `speakblock` | `::speaker … ::` block |
| `bg` | `%background%` with transition picker |
| `charshow` | `%character%` show with position/enter picker |
| `charexpr` | Change character expression |
| `charhide` | `%character% id %hide%` |
| `charexit` | `%character%` animated exit |
| `audio` | `%audio%` play with channel picker |
| `audiostop` | `%audio% %stop%` with fade |
| `effect` | `%effect%` with type picker |
| `video` | `%video%` with skip_after |
| `popup` | `%popup%` notification |
| `wait` | `~wait N` |
| `log` | `~log "…"` |
| `assert` | `~assert (cond) "message"` |
| `defchar` | Full `~define char … ~end` block |
| `defplace` | Full `~define place … ~end` block |
| `defobj` | Full `~define object … ~end` block |
| `triggers` | `~triggers … ~end` block |
| `trigger` | Single trigger rule line |
| `recipes` | `~recipes … ~end` block |
| `funcverb` | `~func verb_X … ~end` override |
| `minigame` | `%minigame%` tag form |
| `minigameblock` | `~minigame … ~end` block form |
| `mgresult` | `~if success / ~elif failure / ~else` branch |
| `menu` | `~set _current_place = … -> MENU` |
| `include` | `INCLUDE "path"` |
| `any` | `any(collection, predicate)` |
| `all` | `all(collection, predicate)` |
| `count` | `count(collection, predicate)` |
| `visits` | `visits(knot) == 0` guard |
| `calendar` | Full `~calendar … ~end` block |
| `timeadv` | `~time advance N` |
| `timewait` | `~time wait_until H M` |

### Language Features

- **Auto-closing pairs** — `{`, `[`, `(`, `"` auto-close
- **Auto-indentation** — indent increases after `~if`, `~define`, `~func`, etc.; decreases at `~end`, `~elif`, `~else`
- **Code folding** — knots, `~define` blocks, `~func` blocks, and `~triggers` blocks fold cleanly
- **Comment toggling** — `Ctrl+/` toggles `//` line comments

---

## Installation

### Option A — Install the `.vsix` Directly (Recommended)

1. Build the package: `npm run package` (requires Node.js)
2. In VS Code: `Extensions → … → Install from VSIX…` → select `arcscript-1.0.0.vsix`
3. In Visual Studio 2022+: `Extensions → Manage Extensions → … → Install from VSIX`

### Option B — Development / Sideload (VS Code)

1. Copy this folder into `%USERPROFILE%\.vscode\extensions\arcscript-1.0.0\`
2. Restart VS Code — `.arc` files will immediately use ArcScript syntax

### Option C — Visual Studio 2022 (TextMate Grammar Only)

Visual Studio 2022 16.6+ natively supports TextMate grammars. To use without packaging:

1. Install the [TextMate Bundles](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.TextmateBundleInstaller) extension for Visual Studio
2. Copy `syntaxes/arcscript.tmLanguage.json` into your Visual Studio TextMate bundle directory
3. Associate `.arc` files with the `source.arc` scope in VS options

---

## Color Theme Compatibility

The grammar uses standard TextMate scopes, so it works well with most popular themes:

| Scope used | Typical theme color |
|---|---|
| `keyword.control.*` | Blue / purple (keywords) |
| `entity.name.section.knot` | Yellow / gold (function names) |
| `entity.name.function.speaker` | Cyan / teal (function names) |
| `storage.type.*` | Blue (type keywords) |
| `variable.other` | White / light (variables) |
| `variable.other.constant` | Teal / light blue (constants) |
| `constant.numeric` | Orange / yellow (numbers) |
| `constant.language.*` | Magenta / purple (true/false/Unknown) |
| `string.quoted.double` | Green / orange (strings) |
| `comment.line.*` | Gray / green-gray (comments) |
| `support.function.builtin` | Cyan (built-in functions) |
| `markup.bold` | Bold white |
| `markup.italic` | Italic |
| `support.type.property-name` | Light blue (entity field names) |

---

## File Structure

```
arcscript-vsx/
├── package.json                  ← Extension manifest
├── language-configuration.json   ← Bracket matching, folding, indentation
├── .vscodeignore
├── README.md
├── syntaxes/
│   └── arcscript.tmLanguage.json ← TextMate grammar (core syntax rules)
└── snippets/
    └── arcscript.code-snippets   ← ~50 code snippets
```

---

## Quick ArcScript Reference

```arc
// Comments — ignored by compiler
## Also a comment (preferred for section headers)

=== knot_name ===        // Scene (knot) definition — compiler starts at the first knot
= stitch_name            // Sub-section within a knot

CONST MAX = 100          // Compile-time constant
VAR score: int = 0       // Runtime variable (optional type annotation)
~set score = score + 10  // Update a variable

-> other_knot            // Jump to a knot
-> knot.stitch           // Jump to a specific stitch
-> END                   // End the story
-> MENU                  // Enter sandbox exploration mode

* [Choice text] Story text   // Once-choice (disappears after selection)
+ [Always choice]            // Always-choice
* {condition} [Guarded]      // Conditional choice
-                            // Gather — convergence after choices

~if (expr)               // Conditional block
~elif (expr)
~unknown                 // Ternary Unknown branch
~else
~end

~when (expr) … ~end      // Single-branch if
~unless (expr) … ~end    // Runs when false

Speaker: Dialogue text   // Single speaker line
::speaker_id             // Open speaker block
All lines attributed.
::                       // Close speaker block

%background% path %transition% fade %duration% 1.5
%character% id %sprite% name %pos% left %enter% slide_in
%audio% path %channel% bgm %loop% %volume% 0.4
%effect% screen_shake %intensity% 0.5 %duration% 0.4
%video% path.mp4 %skip_after% 3
%popup% "Message" %duration% 3.0
%minigame% lockpick %difficulty% 2 %result_var% result_var

~define char "id" … ~end
~define place "id" … ~end
~define object "id" … ~end
~triggers … ~end
~recipes … ~end
~func verb_examine(target) -> _result … ~end

any(coll, it.field > 0)
all(coll, it.sealed == True)
count(coll, it.health > 0)
visits(knot_name)

~wait 1.5
~log "debug: {var}"
~assert (cond) "message"
INCLUDE "path/to/file.arc"
```
