# Changelog

All notable changes to this project are documented here.

The format is loosely based on [Keep a Changelog](https://keepachangelog.com/),
and this project uses date-based, incremental versioning. Dates are in YYYY-MM-DD.

---

## [1.4.0] — 2026-10-03

### Fixed
- **Dragging images from web pages.** Dropping an image that sits inside a link (Google Images, Pinterest, most galleries) used to fail with "Couldn't load that image link", because the link's page URL was tried instead of the picture. The `<img>` (including the largest `srcset` entry and `data:` thumbnails) is now tried first, then each other candidate in turn.
- **Layers list now updates by itself** when images are dropped, pasted or imported. Previously it only refreshed after another action such as Back/Forward.
- **Double-click to rename a layer** works again. The list grabbed the pointer on every press, which redirected the double-click away from the name.
- **No overlapping UI when the window shrinks.** The brand, tools and actions share one bar: the wordmark hides first, then the tools move to their own row, then they scroll sideways. Panels are positioned below the bar, and the board stays centred on resize.

### Added
- **Rename from the inspector.** The inspector header shows the object's name; click it to edit. The Layers list follows as you type.
- **Export images as a .zip.** Turn on *Include images* in the Export popover to also download `moodboard-images.zip`: a folder with every image on the board, named after its layer. Images whose site won't release the file are listed as links in `image-links.txt`.
- Images dropped or pasted from the web are embedded in the board when their site allows it, so they save, export and show a colour palette like local files.
- `⌥1` shortcut to show or hide Layers.
- **Errors appear in the middle of the screen** as an alert with **Learn more**, instead of a toast that disappears. Success messages stay as toasts.
- **Error messages explained** (Settings, under Keyboard shortcuts): a guide to every error message — what it means and what to do.
- **Save Your Board sheet.** When some images come from a site that won't share the file (e.g. Pinterest), Export shows the full board on a transparent background so you can save it with the browser's own **Save Image As…** / **Copy Image**, or download the PNG without those images.
- Dropping non-image files, or images the browser can't open (e.g. HEIC in Chrome), now says so instead of failing silently.

### Changed
- **Layers is a drawer.** It starts closed behind a *Layers* button at the bottom left and slides in from the left edge when clicked.
- PNG export no longer fails outright when the board has an image from a site that blocks it (see Save Your Board). Very large boards are scaled down to fit the browser's size limit instead of failing.
- Apple-style polish: critically damped spring motion for panels, instant press feedback, delayed tooltips, keyboard focus rings, labels for icon buttons, dark mode that follows the system until you choose, and support for Reduce Motion, Reduce Transparency and Increase Contrast.

---

## [1.3.0] — 2026

More ways to get images onto the board, and a way to read color back out of them.

### Added
- **Paste image URLs.** Copy an image link from the web and paste it (`Cmd/Ctrl+V`) to drop it on the canvas. Actual image files on the clipboard still win when both are present.
- **Drag images straight from a browser.** Dragging an image off a web page now works — the dropped URL is read from `text/uri-list` / `text/html` and loaded, no need to save the file first.
- **Color palette extraction.** Selecting an image shows a five-color palette in the inspector, pulled with a median-cut pass over a downscaled copy. Click a swatch to copy its hex.

### Notes
- Images loaded from a URL are cross-origin. They display fine, but the browser won't let us read their pixels — so palette extraction shows a short note instead of swatches for those, and PNG export of a board containing them can be blocked. Pasted/imported image files (local) work fully.

---

## [1.2.0] — 2026

Connectors and a layers workflow.

### Added
- **Lines and arrows.** New connector tool (`A`) with a style flyout: straight line, arrow, curved line, and curved arrow. Arrowheads can be toggled independently on each end.
- **Connector editing.** Draggable endpoint handles, a control-point handle for curves, and a midpoint "bend" handle that converts a straight connector into a curved one. Hold `Shift` while drawing to constrain the angle.
- **Layers panel.** A docked panel listing every object front-to-back, with type icons and live selection highlighting. Click a row to select it on the canvas.
  - Drag rows to reorder stacking (z-order), with a visual insertion indicator.
  - Double-click a layer name to rename it; names are saved with the board.
  - Double-click the panel title to collapse it; the collapsed state is remembered.
- Inspector controls for connectors (shape, arrowheads, thickness, color, opacity).

### Changed
- The inspector and Layers panel now share a right-side dock; when the inspector is open it stacks above the Layers panel, and the pair stays vertically centered.
- Keyboard shortcuts window updated to include the Line / Arrow tool.

### Fixed
- Typing in the layer-rename field no longer triggers tool keyboard shortcuts.

---

## [1.1.0] — 2026

Snapping and settings.

### Added
- **Magnetic snapping.** While dragging, objects snap to neighbours' edges and centres (flush alignment) and to a margin gap that scales with the neighbour's width (side-by-side) or height (stacked). Pink guide lines and a measured gap indicator show the active snaps.
- **Settings menu** with toggles for snapping and dark mode, plus a slider to tune snap spacing.
- **Dark mode** — darkens the full canvas, grid, and UI.
- **Keyboard shortcuts window**, opened from Settings or with `?`.
- Settings persist between sessions via `localStorage`.
- Hold `Cmd/Ctrl` while dragging to temporarily disable snapping.

### Fixed
- Inspector controls (Back/Forward layer order, Delete, text fields, hex inputs, sliders) no longer broke on click — a global pointer handler was rebuilding the inspector DOM mid-interaction and destroying the control being used.
- Dark mode now correctly darkens the canvas background and grid, not just the floating panels (CSS variables were being read from the wrong element).

---

## [1.0.0] — 2026

Initial working version. The first build that did what the abandoned Python attempt never managed to.

### Added
- **Infinite canvas** with smooth pan and zoom, rendered on a raw `<canvas>` with a custom transform matrix.
- **Image import** by drag-and-drop, paste, or file picker.
- **Auto-arrange** into a justified "loose mosaic" row-packing layout (`L`).
- **Shapes and text:** rectangles, ellipses, and editable text blocks.
- **Object transforms:** move, 8-handle resize (with proportional `Shift`), and rotation (with `Shift` angle snapping), all correct under rotation.
- **Inspector** with per-object controls: fill, stroke, corner radius, opacity, font, alignment, and layer order.
- **Selection:** single, shift-multi-select, marquee select, duplicate, and arrow-key nudge.
- **Undo / redo** via scene snapshots.
- **Save / load** boards as JSON.
- **Export** to transparent PNG at 1×/2×/3×, cropped to content with adjustable padding.
- Apple-inspired UI: glass panels, clean typography, smooth transitions.
- Full keyboard shortcut set.

---

## Background

Before `1.0.0`, this project existed only as an unfinished Python experiment from a few years earlier that never reached a usable state. The current implementation is a fresh, single-file web rewrite, "vibe coded" with **Claude Opus 4.8** plus manual adjustments.
