# Writer Color Theme for VS Code

A color scheme for focused long-form writing, mimicking fantastic [iA Writer](https://ia.net/writer).

- Monochromatic color scheme for less distraction.
- Optimized for Markdown.
- Light and Dark versions.
- Pairs well with [Writer font](https://github.com/tonsky/font-writer) at 16 px.

## Screenshots

<img src="screenshot.png" width="780px" alt="Writer theme screenshot">
<img src="screenshot_light.png" width="780px" alt="Writer light theme screenshot">
<img src="screenshot_dark.png" width="780px" alt="Writer dark theme screenshot">

## Installation

Install from the VS Code Marketplace:

1. Open Extensions (`Cmd+Shift+X`)
2. Search for "Writer Color Theme"
3. Click Install

Or install via Quick Open (`Cmd+P`):

```text
ext install tonsky.writer-theme
```

Then enable the theme:

1. Open Command Palette (`Cmd+K Cmd+T`)
2. Select "Writer" for light variant or "Writer Dark" for dark variant

## Recommended settings

Add these to your `settings.json` for the best writing experience:

```json
{
  "editor.cursorWidth": 2,
  "editor.fontFamily": "Writer",
  "editor.fontSize": 16,
  "editor.lineHeight": 1.6,
  "editor.lineNumbers": "off",
  "editor.minimap.enabled": false,
  "editor.renderIndentGuides": false,
  "editor.renderLineHighlight": "none",
  "editor.renderWhitespace": "selection",
  "editor.wordWrap": "wordWrapColumn",
  "editor.wordWrapColumn": 72,
  "workbench.activityBar.visible": false,
  "workbench.statusBar.visible": false,
  "zenMode.centerLayout": true,
  "zenMode.fullScreen": false,
  "zenMode.hideLineNumbers": true
}
```

## See also

[Alabaster Color Scheme](https://github.com/tonsky/sublime-scheme-alabaster): minimal color scheme for coding.

[Fira Code](https://github.com/tonsky/FiraCode/): Best coding font in the world.

## Credits

Made by [Niki Tonsky](https://twitter.com/nikitonsky).

## License

[MIT License](./LICENSE)

## To do

- Take screenshots
- Create icon
- Finalize README
- Publish to VSCode
- Publish to VSCodium
