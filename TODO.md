# TODO

Planned features and changes for Moodboard. This is a personal working list — nothing here is promised or scheduled, it's just where ideas live until they get built.

Checkboxes are for tracking. Notes under each item are implementation hints for whoever picks it up (likely me + Claude).

---

## Objects & selection

- [ ] **Group objects.** Let multiple objects be grouped into a single selectable/movable unit, and ungrouped again.
  - Likely a `group` object type holding child ids, or a `groupId` field on members. Needs hit-testing, move, and layers-panel handling to treat the group as one.

- [ ] **Copy & paste objects within the canvas.** Copy selected lines, shapes, text, images and paste them back.
  - Currently `Cmd/Ctrl+V` only handles pasted *images* from the system clipboard. Add an internal clipboard (deep-cloned scene objects) for canvas elements, with a small offset on paste. Be careful not to clash with image paste — internal clipboard should take priority when it holds objects.

- [ ] **Duplicate shortcut: `Cmd/Ctrl+J`.** Add as an alternative to the existing `Cmd/Ctrl+D`.
  - Wire into the keydown handler alongside `D`; add to the shortcuts window.

## Layers

- [ ] **"To top" / "to bottom" buttons in the Layers panel.** Send the selected item to the very front or very back of the stack.
  - Splice the object to the start (back) or end (front) of the `scene` array. Pairs naturally with the existing Back/Forward inspector controls.

- [ ] **Insert new objects directly above the selected layer.** When something is selected and a new object is added, place it right above the selection in the stacking order instead of always on top of everything.
  - In `addObject`, if there's a single selection, splice the new object in at `selectedIndex + 1` rather than pushing to the end. Falls back to "on top" when nothing is selected.

## Alignment & layout

- [ ] **Alignment / distribution controls for multi-select.** Align left / right / top / bottom / centre across selected objects.
  - Show these in the inspector when 2+ objects are selected. Operate on each object's axis-aligned bounding box.

- [ ] **Auto-align with equal spacing (3+ objects).** When three or more objects are selected, a button distributes them evenly — either vertically or horizontally — with equal gaps.
  - Detect dominant axis (or offer both buttons). Sort by position along the axis, then space centres (or edges) evenly between the first and last. Closely related to the alignment controls above — probably the same inspector section.

## Images

All current image items shipped — see Done below.

## Text

- [ ] **Multiple fonts + font selection.** Let text objects use different font families, chosen from a dropdown in the inspector.
  - Store `fontFamily` per text object; default to the current system stack. Decide whether to offer a curated set of safe web fonts or load a few via `@font-face` (bundling keeps the single-file, offline nature intact).

- [ ] **Italic, underline, strikethrough.** Add these text styles.
  - Italic = `font-style` in the canvas `font` string. Underline and strikethrough aren't native to canvas text — draw them manually as lines under/through measured text runs. Store as boolean flags on the text object; add toggle buttons to the inspector.

## Boards

- [ ] **Per-board notes.** A place to jot notes/context attached to the whole board (not a canvas object).
  - Store a `notes` string in the saved JSON. Could surface as a collapsible panel or a notes button. Decide whether notes should also appear on PNG export (probably not — keep export clean).

---

## Ideas parking lot (unprioritized)

Anything that comes up but isn't committed to yet:

- [ ] Grouping + nested groups
- [ ] Snapping to alignment guides during distribution
- [ ] Keyboard shortcut to send to front/back
- [ ] Export selected objects only
- [ ] Version name display within the canvas (bottom left corner)

---

## Done

> Move items here as they ship (and add them to `CHANGELOG.md`).

- [x] **Paste image URLs.** Copied an image link, paste it (`Cmd/Ctrl+V`), and it loads onto the canvas. Image files on the clipboard still take priority.
- [x] **Drag images directly from a browser into the canvas.** Dragging an image off a web page reads the dropped URL (`text/uri-list` / `text/html`) and adds it.
- [x] **Color palette extraction from images.** Select an image and the inspector shows a five-swatch dominant-color palette (median cut). Click a swatch to copy its hex. Falls back to a note when the image is cross-origin and can't be read.
