# Theme Color Audit

Comparison of theme files against the [VSCode Theme Color Reference](https://code.visualstudio.com/api/references/theme-color).

**Audit Date:** 2026-01-20

## Summary

| Category | Status |
|----------|--------|
| Colors Defined | 117 per theme |
| Invalid Keys | 0 |
| High-Impact Missing | ~25 |
| Medium-Impact Missing | ~30 |

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
- [Color Theme Documentation](https://code.visualstudio.com/api/extension-guides/color-theme)
