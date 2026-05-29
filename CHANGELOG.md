# Changelog

All notable changes to this project are documented here.

The format is loosely based on [Keep a Changelog](https://keepachangelog.com/),
and this project uses date-based, incremental versioning. Dates are in YYYY-MM-DD.

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
