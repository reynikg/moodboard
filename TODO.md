# TODO

Planned features and changes for Moodboard. This is a personal working list — nothing here is promised or scheduled, it's just where ideas live until they get built.

Checkboxes are for tracking. Notes under each item are implementation hints for whoever picks it up (likely me + Claude).


---

## Ideas parking lot (unprioritized)

Anything that comes up but isn't committed to yet:

- [ ] Grouping + nested groups
- [ ] Snapping to alignment guides during distribution
- [ ] Keyboard shortcut to send to front/back
- [ ] Version name display within the canvas (bottom left corner)
- [ ] Font selection
- [ ] Italics, bold support
- [ ] Auto-align with equal spacing (3+ objects)
- [ ] Alignment / distribution controls for multi-select. Align left / right / top / bottom / centre across selected objects.
- [ ] Copy & paste objects within the canvas
- [ ] Group objects
- [ ] Place images in pre-defined templates


---

## Done

> Move items here as they ship (and add them to `CHANGELOG.md`).

- [x] **Paste image URLs.** Copied an image link, paste it (`Cmd/Ctrl+V`), and it loads onto the canvas. Image files on the clipboard still take priority.
- [x] **Drag images directly from a browser into the canvas.** Dragging an image off a web page reads the dropped URL (`text/uri-list` / `text/html`) and adds it.
- [x] **Color palette extraction from images.** Select an image and the inspector shows a five-swatch dominant-color palette (median cut). Click a swatch to copy its hex. Falls back to a note when the image is cross-origin and can't be read.
