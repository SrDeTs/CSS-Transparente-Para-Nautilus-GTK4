# Transparent CSS for Nautilus (GTK4)

Makes Nautilus (GNOME Files) transparent/glass with a frosted glass effect.

## Installation

```bash
cp nautilus.css ~/.config/gtk-4.0/gtk.css
nautilus -q && nautilus
```

## What becomes transparent

- Main window (grid, list, sidebar, headerbar)
- Sidebar (`placessidebar`, `.navigation-sidebar`)
- Context popovers (right-click)
- Properties dialog (`Adw.Dialog`)
- About dialog (`AdwAboutDialog`)
- Shortcuts dialog (`AdwShortcutsDialog`)
- Grid view captions (`Adw.Dialog`)
- Tab bar (`AdwTabBar`)
- Floating bar (`.floating-bar`, `toast`)
- System dialogs (Trash, New Folder, rename)
- Preferences window
- Text entries (`entry`)
- Buttons

## Glass effect

Elements receive:
- Semi-transparent background (`alpha(@window_bg_color, 0.18)`)
- Subtle border (`alpha(@window_fg_color, 0.08)`)
- Drop shadow (`box-shadow`)
- Rounded corners (`border-radius`)
- Light gradient

> **Note:** GTK4 CSS **does not** support `backdrop-filter`. The blur effect comes from your compositor (GNOME/Mutter with opaque blur behind transparent windows).

## File structure

| Section | Content |
|---------|---------|
| 1 | Transparent base (main window) |
| 2 | Headerbar / top bar |
| 3 | Popover / context menu |
| 4 | System dialogs |
| 5 | Properties / info popover |
| 6 | Toast / floating bar |
| 7 | Adw.Dialog, About, Shortcuts, Sidebar, TabBar |

## Customization

Adjust opacity by changing the `0.18` value in:
- `alpha(@window_bg_color, 0.18)` — glass background
- `alpha(@window_fg_color, 0.08)` — border

Higher values = more opaque, lower = more transparent.

## Requirements

- Nautilus (GNOME Files) GTK4
- A compositor that supports transparency (GNOME/Mutter, KDE/KWin, etc.)
- Adwaita theme or derivative (uses CSS variables like `@window_bg_color`, `@accent_color`)

## Live inspector

```bash
GTK_DEBUG=interactive nautilus
```

Press `Ctrl+Shift+D` or menu → Inspector to inspect CSS nodes live.

## License

MIT
