# Moodboard

A fast, single-file moodboard tool for collecting images, arranging them on an infinite canvas, and exporting the result. Built with plain HTML, CSS and JavaScript — no build step, no dependencies, no account, nothing uploaded anywhere.

## Getting started

Open `moodboard.html` in a modern browser (Chrome, Safari, Edge or Firefox). That's it.

```bash
open moodboard.html
```

Everything runs locally in the page. Boards are saved as `.json` files on your own computer.

## Features

**Getting images in**
- Drag image files from your computer onto the canvas.
- Drag images straight off a web page — including images inside links, like Google Images or Pinterest results.
- Paste an image (`⌘V`) or a copied image link.
- Use the image tool (`I`) to pick files.

Images from the web are embedded in the board when the site allows it, so they keep working offline and in exports. If a site won't share the file, the image is linked instead.

**Arranging**
- Move, resize and rotate anything; hold `Shift` to keep proportions or snap the angle.
- Magnetic snapping to neighbouring items, with a spacing gap proportional to their size (adjustable in Settings).
- Auto-arrange (`L`) packs images into a justified mosaic — the whole board, or just the selection.
- Text, rectangles, ellipses, and lines/arrows (straight or curved).

**Layers & inspector**
- The **Layers** drawer (bottom-left, or `⌥1`) lists every item front to back. Drag rows to change stacking order; double-click a name to rename it.
- The inspector shows options for the selected item: colour, border, corner radius, opacity, text styling and more. Click the name at the top to rename it.
- Selecting an image shows its five dominant colours — click a swatch to copy the hex code.

**Saving & exporting**
- **Save** (`⌘S`) downloads the board as `moodboard.json`; **Open** (`⌘O`) loads it back.
- **Export** (`⇧⌘E`) creates a transparent PNG at 1×, 2× or 3× with adjustable padding.
- Turn on **Include images** to also download `moodboard-images.zip` — a folder with every image on the board, named after its layer.

**Comfort**
- Light and dark mode (follows your system until you choose).
- Respects Reduce Motion, Reduce Transparency and Increase Contrast.
- Layout adapts from wide desktop windows down to phone width.

## Keyboard shortcuts

Press `?` in the app for the full list.

| Action | Shortcut |
| --- | --- |
| Select / Hand / Text / Rectangle / Ellipse / Line | `V` / `H` / `T` / `R` / `O` / `A` |
| Add image | `I` |
| Auto-arrange | `L` |
| Show / hide layers | `⌥1` |
| Undo / Redo | `⌘Z` / `⇧⌘Z` |
| Duplicate / Select all / Delete | `⌘D` / `⌘A` / `⌫` |
| Nudge (×10 with `Shift`) | Arrow keys |
| Pan | `Space` + drag, or scroll |
| Zoom | `⌘` + scroll, `+` / `−` |
| Zoom to fit | `⇧1` |
| Save / Open / Export | `⌘S` / `⌘O` / `⇧⌘E` |

On Windows and Linux, use `Ctrl` in place of `⌘`.

## Known limitations

- Some websites block their images from being loaded elsewhere. Those can't be dragged in — copy and paste the image instead.
- Images that are linked rather than embedded (because their site refuses to share the file) are left out of PNG exports and listed as links in the images zip.
- Boards with many embedded images produce large `.json` files.
- With **Include images** on, your browser may ask once to allow multiple downloads.

## Project files

| File | Purpose |
| --- | --- |
| `moodboard.html` | The entire app |
| `CHANGELOG.md` | What changed in each version |
| `TODO.md` | Ideas and planned features |

## License

[MIT](LICENSE) © 2026 reynikg
