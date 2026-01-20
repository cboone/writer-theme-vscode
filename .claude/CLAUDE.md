# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

VSCode color theme extension converted from Sublime Text. A minimal, monochromatic color scheme optimized for focused Markdown writing, inspired by iA Writer. Includes light and dark variants.

## Development

This is a pure JSON theme extension with no build process or npm dependencies.

### Testing the Theme

Press `F5` in VSCode to launch Extension Development Host, then:

1. Open Command Palette (`Cmd+K Cmd+T`)
2. Select «Writer» or «Writer Dark»
3. Open `specimen.md` to verify Markdown rendering

### Key Files

- `themes/writer-light-color-theme.json` - Light theme definition
- `themes/writer-dark-color-theme.json` - Dark theme definition
- `package.json` - Extension manifest
- `specimen.md` - Markdown test file for theme verification

## Architecture

VSCode theme files have two main sections:

- `colors` - Workbench colors (editor, sidebar, tabs, statusbar, terminal)
- `tokenColors` - Syntax highlighting rules with TextMate scopes

### Color Palette

Light theme base colors:

- Background: `#F7F7F7`
- Foreground: `#1a1a1a`
- Accent: `#58bae7`
- Selection: `#cee7f3`

Dark theme base colors:

- Background: `#1b1b1b`
- Foreground: `#cbcccc`
- Accent: `#55bbe7`
- Selection: `#29434e`
