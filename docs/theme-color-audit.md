# Theme Color Audit

Comparison of theme files against the [VSCode Theme Color Reference](https://code.visualstudio.com/api/references/theme-color).

**Audit Date:** 2026-01-20

## Summary

| Category | Status |
|----------|--------|
| Workbench Colors Defined | 117 per theme |
| Invalid Keys | 0 |
| High-Impact Missing | ~25 |
| Medium-Impact Missing | ~30 |
| Token Colors Defined | 11 rules (Markdown-focused) |
| Semantic Highlighting | Disabled |

---

## Current Coverage

The themes define colors for these areas:

- Activity Bar, Badge, Breadcrumb
- Button, Dropdown, Input
- Editor (selection, find, line highlight, cursor, errors/warnings)
- Editor Gutter, Bracket Match, Indent Guides, Line Numbers
- List, Scrollbar, Panel, Peek View
- Sidebar, Status Bar, Tabs
- Terminal (all 16 ANSI colors)
- Title Bar, Tree, Text Links

---

## Token Colors and Semantic Highlighting

Comparison against the [Semantic Highlight Guide](https://code.visualstudio.com/api/language-extensions/semantic-highlight-guide).

### Current State

The themes have **no semantic token support** (`semanticHighlighting` and `semanticTokenColors` are absent). This appears intentional given the theme's purpose as "a minimal, monochromatic color scheme optimized for focused Markdown writing."

### Token Colors Defined (11 rules)

**Markdown formatting:**

| Scope | Style |
|-------|-------|
| `markup.heading` | Bold |
| `markup.italic` | Italic |
| `markup.bold` | Bold |
| `markup.bold markup.italic` | Bold italic |
| `markup.underline.link` | Underline, accent color |
| `markup.inserted` | Green |
| `markup.deleted` | Red |
| `markup.changed` | Orange |
| `markup.ignored`, `markup.untracked` | Gray |

**General:**

| Scope | Style |
|-------|-------|
| `comment`, punctuation definitions | Muted foreground |
| `meta.image.inline.description`, `meta.link.inline.description` | Normal foreground |
| `invalid` | Error foreground |

### Limitation: Token Background Colors

VSCode does not support the `background` property in `tokenColors` (a TextMate feature that was never implemented). The following rules were removed as they only specified backgrounds:

- `markup.inline.raw`, `markup.fenced_code.block`, `markup.raw.block`, `meta.embedded.block`

The `invalid` scope was updated to use foreground-only styling.

### Missing Semantic Token Fallback Scopes

Per the [Semantic Token Scope Map](https://code.visualstudio.com/api/language-extensions/semantic-highlight-guide#semantic-token-scope-map), these TextMate scopes serve as fallbacks for semantic tokens. None are currently defined:

| Semantic Token | Fallback TextMate Scope |
|----------------|-------------------------|
| `namespace` | `entity.name.namespace` |
| `type` | `entity.name.type` |
| `type.defaultLibrary` | `support.type` |
| `struct` | `storage.type.struct` |
| `class` | `entity.name.type.class` |
| `class.defaultLibrary` | `support.class` |
| `interface` | `entity.name.type.interface` |
| `enum` | `entity.name.type.enum` |
| `function` | `entity.name.function` |
| `function.defaultLibrary` | `support.function` |
| `method` | `entity.name.function.member` |
| `macro` | `entity.name.function.preprocessor` |
| `variable` | `variable.other.readwrite` |
| `variable.readonly` | `variable.other.constant` |
| `variable.readonly.defaultLibrary` | `support.constant` |
| `parameter` | `variable.parameter` |
| `property` | `variable.other.property` |
| `property.readonly` | `variable.other.constant.property` |
| `enumMember` | `variable.other.enummember` |
| `event` | `variable.other.event` |

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

## High-Impact Missing Colors

These affect commonly-used features and should be prioritized.

### Git Decorations

File tree coloring for version control status.

| Key | Purpose |
|-----|---------|
| `gitDecoration.addedResourceForeground` | New files |
| `gitDecoration.modifiedResourceForeground` | Changed files |
| `gitDecoration.deletedResourceForeground` | Deleted files |
| `gitDecoration.untrackedResourceForeground` | Untracked files |
| `gitDecoration.ignoredResourceForeground` | Ignored files |
| `gitDecoration.conflictingResourceForeground` | Merge conflicts |
| `gitDecoration.renamedResourceForeground` | Renamed files |
| `gitDecoration.stageModifiedResourceForeground` | Staged modifications |
| `gitDecoration.stageDeletedResourceForeground` | Staged deletions |
| `gitDecoration.submoduleResourceForeground` | Submodules |

### Diff Editor

Side-by-side and inline diff views.

| Key | Purpose |
|-----|---------|
| `diffEditor.insertedTextBackground` | Added text highlight |
| `diffEditor.insertedLineBackground` | Added line background |
| `diffEditor.removedTextBackground` | Removed text highlight |
| `diffEditor.removedLineBackground` | Removed line background |
| `diffEditor.border` | Diff editor border |
| `diffEditor.diagonalFill` | Diagonal fill pattern |
| `diffEditorGutter.insertedLineBackground` | Gutter for additions |
| `diffEditorGutter.removedLineBackground` | Gutter for deletions |

### Notifications

Toast notifications and notification center.

| Key | Purpose |
|-----|---------|
| `notifications.background` | Notification background |
| `notifications.foreground` | Notification text |
| `notifications.border` | Notification border |
| `notificationLink.foreground` | Links in notifications |
| `notificationCenterHeader.background` | Header background |
| `notificationCenterHeader.foreground` | Header text |
| `notificationsErrorIcon.foreground` | Error icon |
| `notificationsWarningIcon.foreground` | Warning icon |
| `notificationsInfoIcon.foreground` | Info icon |

### Quick Picker / Command Palette

Command palette and quick open dialogs.

| Key | Purpose |
|-----|---------|
| `quickInput.background` | Picker background |
| `quickInput.foreground` | Picker text |
| `quickInputList.focusBackground` | Focused item background |
| `quickInputList.focusForeground` | Focused item text |
| `quickInputTitle.background` | Title background |
| `pickerGroup.border` | Group separator |
| `pickerGroup.foreground` | Group label |

### Editor Suggest Widget

Autocomplete and IntelliSense dropdown.

| Key | Purpose |
|-----|---------|
| `editorSuggestWidget.background` | Widget background |
| `editorSuggestWidget.foreground` | Widget text |
| `editorSuggestWidget.border` | Widget border |
| `editorSuggestWidget.highlightForeground` | Matched text |
| `editorSuggestWidget.selectedBackground` | Selected item |
| `editorSuggestWidget.selectedForeground` | Selected item text |
| `editorSuggestWidget.focusHighlightForeground` | Focused match |

### Editor Hover Widget

Hover information popups.

| Key | Purpose |
|-----|---------|
| `editorHoverWidget.background` | Hover background |
| `editorHoverWidget.foreground` | Hover text |
| `editorHoverWidget.border` | Hover border |
| `editorHoverWidget.statusBarBackground` | Status bar in hover |

---

## Medium-Impact Missing Colors

These enhance the experience but have reasonable defaults.

### Base Colors

| Key | Purpose |
|-----|---------|
| `foreground` | Global default text |
| `descriptionForeground` | Secondary/muted text |
| `errorForeground` | Error text color |
| `disabledForeground` | Disabled elements |
| `widget.shadow` | Shadow for floating widgets |
| `selection.background` | Global selection |

### Terminal Extras

| Key | Purpose |
|-----|---------|
| `terminal.selectionBackground` | Selected text in terminal |
| `terminal.selectionForeground` | Selected text foreground |
| `terminalCursor.foreground` | Cursor color |
| `terminalCursor.background` | Cursor background |
| `terminal.findMatchBackground` | Find match highlight |
| `terminal.findMatchHighlightBackground` | Other matches |

### Minimap

| Key | Purpose |
|-----|---------|
| `minimap.background` | Minimap background |
| `minimap.findMatchHighlight` | Search matches |
| `minimap.errorHighlight` | Error indicators |
| `minimap.warningHighlight` | Warning indicators |
| `minimapSlider.background` | Viewport slider |
| `minimapSlider.hoverBackground` | Slider on hover |
| `minimapSlider.activeBackground` | Slider when dragging |
| `minimapGutter.addedBackground` | Added lines |
| `minimapGutter.modifiedBackground` | Modified lines |
| `minimapGutter.deletedBackground` | Deleted lines |

### Activity Bar Extras

| Key | Purpose |
|-----|---------|
| `activityBar.inactiveForeground` | Inactive icons |
| `activityBar.activeBorder` | Active indicator |
| `activityBar.activeBackground` | Active item background |

### Menu and Command Center

| Key | Purpose |
|-----|---------|
| `menu.background` | Menu background |
| `menu.foreground` | Menu text |
| `menu.selectionBackground` | Selected menu item |
| `menu.selectionForeground` | Selected item text |
| `menu.separatorBackground` | Menu dividers |
| `commandCenter.background` | Command center background |
| `commandCenter.foreground` | Command center text |
| `commandCenter.border` | Command center border |

### List Extras

| Key | Purpose |
|-----|---------|
| `list.focusForeground` | Focused item text |
| `list.hoverForeground` | Hovered item text |
| `list.errorForeground` | Items with errors |
| `list.warningForeground` | Items with warnings |
| `list.filterMatchBackground` | Filter match highlight |

### Tab Extras

| Key | Purpose |
|-----|---------|
| `tab.activeBorderTop` | Top border on active tab |
| `tab.hoverBackground` | Tab on hover |
| `tab.hoverForeground` | Tab text on hover |
| `tab.unfocusedActiveBackground` | Active tab, unfocused group |
| `tab.unfocusedActiveForeground` | Active tab text, unfocused |
| `tab.unfocusedInactiveForeground` | Inactive tab, unfocused |

---

## Lower Priority

These are specialized features with good defaults.

### Merge Conflicts

- `merge.currentHeaderBackground`
- `merge.currentContentBackground`
- `merge.incomingHeaderBackground`
- `merge.incomingContentBackground`
- `merge.border`
- `mergeEditor.change.background`

### Debug

- `debugToolBar.background`
- `debugToolBar.border`
- `editor.stackFrameHighlightBackground`
- `editor.focusedStackFrameHighlightBackground`
- `debugView.stateLabelBackground`
- `debugView.stateLabelForeground`

### Testing

- `testing.iconPassed`
- `testing.iconFailed`
- `testing.iconErrored`
- `testing.iconSkipped`
- `testing.peekBorder`
- `testing.peekHeaderBackground`

### Editor Inlay Hints

- `editorInlayHint.background`
- `editorInlayHint.foreground`
- `editorInlayHint.typeForeground`
- `editorInlayHint.parameterForeground`

### Sticky Scroll

- `editorStickyScroll.background`
- `editorStickyScroll.border`
- `editorStickyScrollHover.background`

### Bracket Pair Colorization

- `editorBracketHighlight.foreground1` through `foreground6`
- `editorBracketPairGuide.background1` through `background6`

### Welcome Page

- `welcomePage.background`
- `welcomePage.tileBackground`
- `welcomePage.tileHoverBackground`

### Settings Editor

- `settings.headerForeground`
- `settings.modifiedItemIndicator`
- `settings.focusedRowBackground`

---

## References

- [VSCode Theme Color Reference](https://code.visualstudio.com/api/references/theme-color)
- [Semantic Highlight Guide](https://code.visualstudio.com/api/language-extensions/semantic-highlight-guide)
- [Color Theme Documentation](https://code.visualstudio.com/api/extension-guides/color-theme)
