# Theme Color Audit

Comparison of theme files against the [VSCode Theme Color Reference](https://code.visualstudio.com/api/references/theme-color).

**Audit Date:** 2026-01-20

## Summary

| Category                 | Status                      |
| ------------------------ | --------------------------- |
| Workbench Colors Defined | 207 per theme               |
| Invalid Keys             | 0                           |
| Token Colors Defined     | 11 rules (Markdown-focused) |
| Semantic Highlighting    | Disabled (intentional)      |

---

## Current Coverage

The themes define comprehensive colors for all major UI areas:

**Core UI:**

- Activity Bar (including active/inactive states)
- Badge, Breadcrumb, Button (primary and secondary)
- Command Center, Debug Toolbar
- Dropdown, Input (with validation states)

**Editor:**

- Selection, find, line highlight, cursor
- Bracket matching and colorization (muted)
- Gutter (added/modified/deleted indicators)
- Hover widget, suggest widget, sticky scroll
- Inlay hints, overview ruler, minimap

**Lists and Trees:**

- Selection, hover, focus states
- Error/warning foregrounds
- Filter match highlights
- Indent guides

**Panels and Widgets:**

- Notifications (with error/warning/info icons)
- Quick picker / command palette
- Peek view (with match highlights)
- Panel sections and headers

**Version Control:**

- Git decorations (added, modified, deleted, ignored, etc.)
- Diff editor (inserted/removed backgrounds)
- Merge conflict highlighting

**Other:**

- Terminal (all 16 ANSI colors, cursor, selection)
- Testing icons (passed, failed, errored, skipped)
- Settings editor, welcome page
- Menus, toolbars, scrollbars

---

## Token Colors and Semantic Highlighting

Comparison against the [Semantic Highlight Guide](https://code.visualstudio.com/api/language-extensions/semantic-highlight-guide).

### Current State

The themes have **no semantic token support** (`semanticHighlighting` and `semanticTokenColors` are absent). This appears intentional given the theme's purpose as "a minimal, monochromatic color scheme optimized for focused Markdown writing."

### Token Colors Defined (11 rules)

**Markdown formatting:**

| Scope                                | Style                   |
| ------------------------------------ | ----------------------- |
| `markup.heading`                     | Bold                    |
| `markup.italic`                      | Italic                  |
| `markup.bold`                        | Bold                    |
| `markup.bold markup.italic`          | Bold italic             |
| `markup.underline.link`              | Underline, accent color |
| `markup.inserted`                    | Green                   |
| `markup.deleted`                     | Red                     |
| `markup.changed`                     | Orange                  |
| `markup.ignored`, `markup.untracked` | Gray                    |

**General:**

| Scope                                                           | Style             |
| --------------------------------------------------------------- | ----------------- |
| `comment`, punctuation definitions                              | Muted foreground  |
| `meta.image.inline.description`, `meta.link.inline.description` | Normal foreground |
| `invalid`                                                       | Error foreground  |

### Limitation: Token Background Colors

VSCode does not support the `background` property in `tokenColors` (a TextMate feature that was never implemented). The following rules were removed as they only specified backgrounds:

- `markup.inline.raw`, `markup.fenced_code.block`, `markup.raw.block`, `meta.embedded.block`

The `invalid` scope was updated to use foreground-only styling.

### Missing Semantic Token Fallback Scopes

Per the [Semantic Token Scope Map](https://code.visualstudio.com/api/language-extensions/semantic-highlight-guide#semantic-token-scope-map), these TextMate scopes serve as fallbacks for semantic tokens. None are currently defined:

| Semantic Token                     | Fallback TextMate Scope             |
| ---------------------------------- | ----------------------------------- |
| `namespace`                        | `entity.name.namespace`             |
| `type`                             | `entity.name.type`                  |
| `type.defaultLibrary`              | `support.type`                      |
| `struct`                           | `storage.type.struct`               |
| `class`                            | `entity.name.type.class`            |
| `class.defaultLibrary`             | `support.class`                     |
| `interface`                        | `entity.name.type.interface`        |
| `enum`                             | `entity.name.type.enum`             |
| `function`                         | `entity.name.function`              |
| `function.defaultLibrary`          | `support.function`                  |
| `method`                           | `entity.name.function.member`       |
| `macro`                            | `entity.name.function.preprocessor` |
| `variable`                         | `variable.other.readwrite`          |
| `variable.readonly`                | `variable.other.constant`           |
| `variable.readonly.defaultLibrary` | `support.constant`                  |
| `parameter`                        | `variable.parameter`                |
| `property`                         | `variable.other.property`           |
| `property.readonly`                | `variable.other.constant.property`  |
| `enumMember`                       | `variable.other.enummember`         |
| `event`                            | `variable.other.event`              |

### Other Common Scopes Not Defined

These standard TextMate scopes have no rules:

- `keyword`, `keyword.control`, `keyword.operator`
- `string`, `string.quoted`
- `constant.numeric`, `constant.language`
- `storage`, `storage.type`, `storage.modifier`
- `entity.name.tag` (HTML/XML tags)
- `entity.other.attribute-name`

### Design Decision

The absence of code syntax highlighting is consistent with the theme's minimalist, writing-focused design. Options for future consideration:

1. **Keep as-is** - Maintain the monochromatic philosophy
2. **Subtle muting** - Apply the muted color to all code tokens
3. **Full semantic support** - Add `semanticHighlighting: true` and define colors

---

## Color Palette

| Role         | Light                                                          | Dark                                                           |
| ------------ | -------------------------------------------------------------- | -------------------------------------------------------------- |
| Background   | ![#F7F7F7](https://placehold.co/12x12/F7F7F7/F7F7F7) `#F7F7F7` | ![#1b1b1b](https://placehold.co/12x12/1b1b1b/1b1b1b) `#1b1b1b` |
| Secondary BG | ![#eeeeee](https://placehold.co/12x12/eeeeee/eeeeee) `#eeeeee` | ![#151515](https://placehold.co/12x12/151515/151515) `#151515` |
| Tertiary BG  | ![#f0f0f0](https://placehold.co/12x12/f0f0f0/f0f0f0) `#f0f0f0` | ![#222222](https://placehold.co/12x12/222222/222222) `#222222` |
| Foreground   | ![#1a1a1a](https://placehold.co/12x12/1a1a1a/1a1a1a) `#1a1a1a` | ![#cbcccc](https://placehold.co/12x12/cbcccc/cbcccc) `#cbcccc` |
| Muted        | ![#c6c5c2](https://placehold.co/12x12/c6c5c2/c6c5c2) `#c6c5c2` | ![#706f70](https://placehold.co/12x12/706f70/706f70) `#706f70` |
| Border       | ![#e0e0e0](https://placehold.co/12x12/e0e0e0/e0e0e0) `#e0e0e0` | ![#333333](https://placehold.co/12x12/333333/333333) `#333333` |
| Accent       | ![#58bae7](https://placehold.co/12x12/58bae7/58bae7) `#58bae7` | ![#55bbe7](https://placehold.co/12x12/55bbe7/55bbe7) `#55bbe7` |
| Selection    | ![#cee7f3](https://placehold.co/12x12/cee7f3/cee7f3) `#cee7f3` | ![#29434e](https://placehold.co/12x12/29434e/29434e) `#29434e` |
| Find Match   | ![#FFBC5D](https://placehold.co/12x12/FFBC5D/FFBC5D) `#FFBC5D` | ![#fffd54](https://placehold.co/12x12/fffd54/fffd54) `#fffd54` |
| Added        | ![#6abf40](https://placehold.co/12x12/6abf40/6abf40) `#6abf40` | ![#6abf40](https://placehold.co/12x12/6abf40/6abf40) `#6abf40` |
| Modified     | ![#ec9112](https://placehold.co/12x12/ec9112/ec9112) `#ec9112` | ![#ec9112](https://placehold.co/12x12/ec9112/ec9112) `#ec9112` |
| Deleted      | ![#d32d2a](https://placehold.co/12x12/d32d2a/d32d2a) `#d32d2a` | ![#d32d2a](https://placehold.co/12x12/d32d2a/d32d2a) `#d32d2a` |
| Error        | ![#ef786c](https://placehold.co/12x12/ef786c/ef786c) `#ef786c` | ![#ef786c](https://placehold.co/12x12/ef786c/ef786c) `#ef786c` |

---

## References

- [VSCode Theme Color Reference](https://code.visualstudio.com/api/references/theme-color)
- [Semantic Highlight Guide](https://code.visualstudio.com/api/language-extensions/semantic-highlight-guide)
- [Color Theme Documentation](https://code.visualstudio.com/api/extension-guides/color-theme)
