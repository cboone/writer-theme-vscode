# <img src="icon.png" alt="Writer Color Theme icon" height="24px" /> Writer Color Theme for VSCode

A color theme for focused long-form writing, based on [Tonsky's Sublime Text theme](https://github.com/tonsky/sublime-scheme-writer), which was in turn inspired by [iA Writer](https://ia.net/writer).

- Monochromatic color scheme for less distraction.
- Optimized for Markdown.
- Light and Dark versions.
- Pairs well with Tonsky's [Writer font](https://github.com/tonsky/font-writer) at 16 px.

## Background

This theme is a port of [the Writer color theme](https://github.com/tonsky/sublime-scheme-writer) created by [Nikita Prokopov (aka Tonsky)](https://github.com/tonsky), from Sublime Text to VSCode.

Tonsky created the original theme to replicate iA Writer's minimalist writing experience while gaining the broader capabilities of a full-featured text editor—multiple cursors. As he explains in his blog post ["Building an ultimate writing machine from Sublime Text"](https://tonsky.github.io/blog/sublime-writer/), iA Writer "found the perfect balance between features and simplicity, design and focus."

## Screenshot

![Writer Dark + Light themes combined screenshot](https://raw.githubusercontent.com/cboone/writer-theme-vscode/main/screenshots/writer-combined.png)

## Color Palette

| Role       | Light                                                          | Dark                                                           |
| ---------- | -------------------------------------------------------------- | -------------------------------------------------------------- |
| Background | ![#F7F7F7](https://placehold.co/16x16/F7F7F7/F7F7F7) `#F7F7F7` | ![#1b1b1b](https://placehold.co/16x16/1b1b1b/1b1b1b) `#1b1b1b` |
| Foreground | ![#1a1a1a](https://placehold.co/16x16/1a1a1a/1a1a1a) `#1a1a1a` | ![#cbcccc](https://placehold.co/16x16/cbcccc/cbcccc) `#cbcccc` |
| Accent     | ![#58bae7](https://placehold.co/16x16/58bae7/58bae7) `#58bae7` | ![#55bbe7](https://placehold.co/16x16/55bbe7/55bbe7) `#55bbe7` |
| Selection  | ![#cee7f3](https://placehold.co/16x16/cee7f3/cee7f3) `#cee7f3` | ![#29434e](https://placehold.co/16x16/29434e/29434e) `#29434e` |

## Installation

Install from the VS Code Marketplace:

1. Open Extensions (`Cmd+Shift+X`)
2. Search for "Writer Color Theme"
3. Click Install

Or install via Quick Open (`Cmd+P`):

```text
ext install cboone.writer-theme-vscode
```

Then enable the theme:

1. Open Command Palette (`Cmd+K Cmd+T`)
2. Select "Writer Light" or "Writer Dark"

## Recommended settings

To get Tonsky's full Writer experience, install [the Writer font](https://github.com/tonsky/font-writer), then add these to your `settings.json`:

```json
{
  "editor.cursorWidth": 2,
  "editor.fontFamily": "Writer",
  "editor.fontSize": 16,
  "editor.lineHeight": 1.6,
  "editor.lineNumbers": "off",
  "editor.minimap.enabled": false,
  "editor.guides.indentation": false,
  "editor.renderLineHighlight": "none",
  "editor.renderWhitespace": "selection",
  "editor.wordWrap": "wordWrapColumn",
  "editor.wordWrapColumn": 72,
  "workbench.activityBar.location": "hidden",
  "workbench.statusBar.visible": false,
  "zenMode.centerLayout": true,
  "zenMode.fullScreen": false,
  "zenMode.hideLineNumbers": true
}
```

## See also

### [iA Writer](https://ia.net/writer)

The app that inspired this theme's design philosophy. Hard to beat it.

### [iA Fonts](https://github.com/iaolo/iA-Fonts)

iA's modifications of IBM Plex Mono. These fonts are gorgeous. They're variable fonts, thus can be adjusted in every way possible. They're fully internationalized.

iA Writer Mono is a cleaned up variant of Plex Mono. iA Writer Duo is the same, but with several characters (such as `W` and `M`) expanded to 150% of the rest. iA Writer Quattro is the same as Duo, but with some characters (such as `f` and `t`) shrunk to 75%, and some (such as `i` and `j`) shrunk to 50%. Which, in the end, makes for a proportional monospaced typeface.

Read more about them in iA's blog post ["A Typographic Christmas"](https://ia.net/topics/a-typographic-christmas).

### [Writer font](https://github.com/tonsky/font-writer)

Tonsky's modified IBM Plex Mono, optimized for writing, "with increased letter-spacing and tuned weights."

### [Alabaster color theme](https://github.com/tonsky/sublime-scheme-alabaster)

Tonsky's minimal color scheme for coding, based on his philosophy of syntax highlighting, described in his blog post ["A case against syntax highlighting"](https://tonsky.me/blog/syntax-highlighting/).

Available for [a very wide range of tools](https://github.com/cboone/alabaster-themes-for-terminals#related-themes), including [my versions for terminal emulators](https://github.com/cboone/alabaster-themes-for-terminals).

### [Fira Code](https://github.com/tonsky/FiraCode/)

Tonsky's beautiful update of [Fira Mono](https://github.com/mozilla/Fira) for coding, with monospaced ligatures. Pairs very well with Alabaster.

## Credits

Original theme by [Nikita Prokopov (aka Tonsky)](https://github.com/tonsky/).

VSCode port by [Christopher Boone](https://cboone.github.io).

## License

[MIT License](LICENSE)
