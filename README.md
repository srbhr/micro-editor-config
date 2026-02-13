# Micro Editor Themes & Configuration

Custom themes and personal settings for the [micro editor](https://micro-editor.github.io/) by [@srbhr](https://github.com/srbhr).

## What's Inside

This repository contains **color schemes / themes for micro editor.** Crafted with a personal touch along with my keybindings and editor settings.

### Themes

Located in `colorschemes/`:

| Theme | Description |
|-------|-------------|
| ayu-mirage | Ayu Mirage color palette |
| cyber-midnight | Cyberpunk-inspired dark theme |
| ember-glow | Warm ember tones |
| frost | Cool, frosty palette |
| one-dark-vivid-italic | One Dark with vivid colors and italic keywords |
| oxblood | Deep red-tinted dark theme |
| tokyo-night | Tokyo Night color palette |
| ultraviolet | Purple-heavy dark theme |
| verdant | Green-tinted nature theme |

27;5;27~Note: By adding `default` in the theme, you're inheriting your terminal's background. Using this, you can keep your terminal's opacity.

### Settings

- `settings.json` — Editor preferences
- `bindings.json` — Custom keybindings

## Installation

Copy the files into your micro config directory:

```bash
# Themes
cp colorschemes/*.micro ~/.config/micro/colorschemes/

# Settings & keybindings
cp settings.json ~/.config/micro/settings.json
cp bindings.json ~/.config/micro/bindings.json
```

Then set a theme in micro with `Ctrl+E` and typing:

```
set colorscheme theme-name
```

## macOS: Using Cmd Instead of Ctrl

Terminal apps like micro never receive `Cmd` keypresses — macOS and your terminal emulator intercept them first. The fix is to remap `Cmd` to send `Ctrl` escape codes at the terminal level.

### Ghostty

Add these to your Ghostty config (`~/.config/ghostty/config`):

```
keybind = cmd+s=text:\x13   # Save
keybind = cmd+q=text:\x11   # Quit
keybind = cmd+z=text:\x1a   # Undo
keybind = cmd+e=text:\x05   # Command bar
keybind = cmd+f=text:\x06   # Find
keybind = cmd+g=text:\x07   # Go to line
keybind = cmd+w=text:\x17   # Close
keybind = cmd+o=text:\x0f   # Open
```

Each line sends the corresponding Ctrl code when you press Cmd, so `Cmd+S` behaves like `Ctrl+S`.

> **Note:** This applies to all terminal apps running in Ghostty, not just micro. Usually fine, but worth knowing.

Add the ones you need, restart Ghostty, and test.

## Status Bar Customization

Micro supports left (`statusformatl`) and right (`statusformatr`) status bar formats.

### Available Placeholders

| Placeholder | Shows |
|-------------|-------|
| `$(status.filename)` | File name |
| `$(status.pathname)` | Full file path |
| `$(status.size)` | File size |
| `$(status.line)` | Current line number |
| `$(status.col)` | Current column |
| `$(status.lines)` | Total lines in file |
| `$(status.percent)` | Percentage through file |
| `$(status.branch)` | Git branch |
| `$(status.hash)` | Short commit hash |
| `$(status.modified)` | `[+]` if unsaved changes |
| `$(status.readonly)` | `[ro]` if read-only |

### Recommended Setup

```json
"statusformatl": "$(status.filename) $(status.modified)",
"statusformatr": "Ln $(status.line):$(status.col) | $(status.percent)% | $(status.branch)"
```

This gives you the file name with an unsaved indicator on the left, and cursor position, progress, and git branch on the right.
