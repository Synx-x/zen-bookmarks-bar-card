# Bookmarks Bar Card

A mod for [Zen Browser](https://zen-browser.app) that rounds the compact-mode
bookmarks bar into a floating card, and removes the dark strips Zen leaves
above and below the page.

![Bookmarks Bar Card](image.png)

## What it does

Zen's compact mode hides the top bar until you pan to the window's top edge.
The bar slides down square-cornered, and the page sits inset behind it.

This mod changes two things:

- reshapes the bar into a rounded floating card, with a shadow and a hairline
  edge, matching the treatment compact mode gives the sidebar flyout
- closes the gaps above and below the page, so content runs edge to edge

The window close button stays pinned as the card's last item, vertically
centred, and keeps its place as the bookmarks bar fills up.

Everything is adjustable. Compact mode has to be on.

## The gaps

Two separate gaps produce the strips this mod removes.

Above the page, the collapsed card still holds about 9px of layout space, its
margin plus border, even at rest. That space pushes the page down and leaves a
strip where the window's backdrop shows through. This mod takes the bar out of
the layout flow, so it floats over the page instead of displacing it.

Below the page, `#zen-tabbox-wrapper` carries an 8px margin on every side.
Measured on a 508px window, the content area comes to 500px, leaving exactly
8px of backdrop at the bottom. This mod zeroes the top and bottom margins and
leaves the sides alone.

The "Keep Zen's default gaps" option restores both strips, for anyone who
prefers the inset look.

## Install

### From the Zen Mods store

Search for "Bookmarks Bar Card" in Settings, then Mods.

### Manual

Copy `chrome.css` into your profile:

```
~/.zen/<profile>/chrome/userChrome.css
```

Set `toolkit.legacyUserProfileCustomizations.stylesheets` to `true` in
`about:config`, then restart Zen. Chrome CSS loads once at startup, so a
restart is needed for any change.

## Options

| Option | Default | What it does |
| --- | --- | --- |
| Corner radius | 18 | Card corner rounding, in px |
| Gap | 8 | Space between the card and the window edge, in px |
| Inner side padding | 15 | Space inside the card, left and right, in px |
| Card background | `#202020` | Card fill colour |
| Remove the drop shadow | off | Drops the shadow under the card |
| Remove the hairline edge | off | Drops the 1px border |
| Keep Zen's default gaps | off | Restores the strips above and below the page |

## Tested against

Zen 1.22b on Linux, Wayland, compact mode enabled, verified on a clean
profile carrying this stylesheet and nothing else.

## Companion mod

[Minimalist Compact Mode](https://github.com/Synx-x/zen-minimalist-compact-mode)
gives the sidebar flyout the same card treatment. The two work together and
neither requires the other.

## License

MIT, see [LICENSE](LICENSE).
