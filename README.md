# Konbini

An [Omarchy](https://omarchy.org) theme for late nights, empty streets, and the
glow of a convenience store sign — inspired by quiet anime slice-of-life
backdrops. Deep navy night sky, warm amber window and streetlamp light, soft
starfields.

![Desktop](screenshots/desktop.jpg)

## Gallery

| | |
| --- | --- |
| ![Theme picker](screenshots/theme-switcher.jpg)<br>Theme picker | ![Terminal](screenshots/terminal.jpg)<br>Terminal + gradient border |
| ![Lock screen](screenshots/lockscreen.jpg)<br>Lock screen | ![Second wallpaper](screenshots/desktop-corner-store.jpg)<br>Second wallpaper |
| ![Third wallpaper](screenshots/desktop-quiet-street.jpg)<br>Third wallpaper | ![Boot unlock screen](preview-unlock.png)<br>Boot / disk-unlock screen |

## Install

**Option A — `omarchy theme install` (recommended):**

```bash
omarchy theme install https://github.com/Lohan-Pieterse/omarchy-konbini-theme.git
```

This clones the repo into `~/.config/omarchy/themes/konbini` and applies the
theme right away. As a security measure, Omarchy won't apply any `*.lua`,
terminal configs, or `vscode.json` from a theme cloned from git — this theme
doesn't ship any of those, so nothing is lost.

**Option B — manual clone**, if you want to inspect or tweak it first:

```bash
git clone https://github.com/Lohan-Pieterse/omarchy-konbini-theme.git \
  ~/.config/omarchy/themes/konbini
omarchy theme set konbini
```

A manual clone still has its `.git` directory, so Omarchy treats it exactly
like an installed theme: the same file filtering, and `omarchy theme update`
keeps it up to date.

**After installing**, cycle between the three wallpapers with:

```bash
omarchy theme bg next
```

## Palette

| Role       | Color                                                    | Hex       |
| ---------- | -------------------------------------------------------- | --------- |
| accent     | ![#F0B87E](https://placehold.co/16x16/F0B87E/F0B87E.png) | `#F0B87E` |
| background | ![#121B26](https://placehold.co/16x16/121B26/121B26.png) | `#121B26` |
| foreground | ![#D6DEE8](https://placehold.co/16x16/D6DEE8/D6DEE8.png) | `#D6DEE8` |
| red        | ![#DC6A62](https://placehold.co/16x16/DC6A62/DC6A62.png) | `#DC6A62` |
| yellow     | ![#F2C879](https://placehold.co/16x16/F2C879/F2C879.png) | `#F2C879` |
| orange     | ![#EE9858](https://placehold.co/16x16/EE9858/EE9858.png) | `#EE9858` |
| green      | ![#A4D497](https://placehold.co/16x16/A4D497/A4D497.png) | `#A4D497` |
| cyan       | ![#6FB4C7](https://placehold.co/16x16/6FB4C7/6FB4C7.png) | `#6FB4C7` |
| blue       | ![#5C89C2](https://placehold.co/16x16/5C89C2/5C89C2.png) | `#5C89C2` |
| magenta    | ![#A587A8](https://placehold.co/16x16/A587A8/A587A8.png) | `#A587A8` |
| brown      | ![#A27E61](https://placehold.co/16x16/A27E61/A27E61.png) | `#A27E61` |

Full values in [`colors.toml`](colors.toml).

## Backgrounds

Three wallpapers included under `backgrounds/` at a true 3840×2160 (4K). All
were generated with Google's image generation AI at 1376×768, then upscaled
with Real-ESRGAN (`realesr-animevideov3`), which keeps the painted texture of
the wet streets, foliage and skies instead of smoothing it away.

- `01-station-crossing.jpg` — a girl waiting at a rail crossing by a corner
  store. Shown first (Omarchy picks backgrounds alphabetically the first time
  a theme is applied).
  This is also the wallpaper behind the windows in `preview.png`.
- `02-corner-store.jpg` — the same fictional Sunset Mart, on a street corner
  under a starry sky.
- `03-quiet-street.jpg` — a sleeping residential lane after rain, one warm
  window still lit.

The signage was repainted by hand after generation: real-world brand logos
were replaced with the fictional Sunset Mart, and garbled AI text on the
store signs, banners, street signs and crossing plates was replaced with
real Japanese (24時間営業, おにぎり・お弁当, 踏切注意, 年中無休, 止まれ,
自転車通行可, 自動ドア, たばこ). Every sign says something you would actually
see on a Japanese street.

## Lock screen

Nothing to configure — Omarchy's lock screen automatically blurs whichever
background is currently active, and `shell.lock.toml` gives the password box
the same amber-to-blue gradient outline as your windows. You can safely
preview it without actually locking your session:

```bash
omarchy shell lock preview      # show it
omarchy shell lock hidePreview  # dismiss it
```

## Away screen (optional)

Konbini ships an idle screensaver, `screensaver.txt`: the quiet lane from
`03-quiet-street.jpg` in solid blocks (houses, a power line, a crescent moon
and stars), drawn in by Omarchy's text effects in place of the stock logo.
It is 66×17, so it fits the screensaver terminal even on small HiDPI
screens. Omarchy picks the effect and its colors at random each cycle;
themes can't change those. Omarchy keeps the screensaver
in your personal branding rather than in the theme, so it takes one step:

```bash
# Just use it:
cp ~/.config/omarchy/themes/konbini/screensaver.txt ~/.config/omarchy/branding/screensaver.txt

# Or swap it in automatically whenever Konbini is the active theme
# (your own screensaver comes back when you switch themes):
omarchy hook install theme-set ~/.config/omarchy/themes/konbini/extras/screensaver-hook
```

Preview it with `omarchy launch screensaver force`; any key ends it.

## What's themed

- `colors.toml` — the full Omarchy color palette, including
  `hyprland_active_border`/`hyprland_inactive_border` for an amber-to-blue
  gradient window border
- `icons.theme` — Yaru-yellow, amber folders that match the shop-window
  glow
- `shell.controls.toml` — amber focus and selected states for buttons, tabs
  and dropdowns in the Omarchy shell (the rest of the shell is generated)
- `shell.lock.toml` — the amber-to-blue gradient on the lock screen's
  password box
- `unlock.png` / `preview-unlock.png` — an amber Omarchy logo for the boot /
  disk-unlock screen; pick it under **Menu → Style → Unlock**
- `preview.png` — a real desktop screenshot (btop, neovim + neo-tree, and
  Files tiled together, matching the layout Omarchy's own stock themes use
  for their previews), shown in the Omarchy theme picker and on
  [omarchy.org/themes](https://omarchy.org/themes/)
- Everything else (terminal apps, bar, lock screen, etc.) is generated
  automatically by Omarchy from `colors.toml`. The palette is tuned for
  legibility: every text color clears WCAG AA (4.5:1) on the background
  except `muted` (≈4:1, used for comments and autosuggestions), and red/green
  stay distinguishable with red-green color blindness

## License

The theme files (`colors.toml`, `icons.theme`, the `shell.*.toml` files,
`screensaver.txt` and `extras/`) are MIT licensed — see
[LICENSE](LICENSE). The background images are AI-generated (see
[Backgrounds](#backgrounds)); feel free to use them as personal desktop
backgrounds, but please don't resell them. The store names in the artwork are
fictional.

Made by Lohan Pieterse ([@Lohan-Pieterse](https://github.com/Lohan-Pieterse)).
