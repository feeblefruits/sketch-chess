# Sketch Chess

A fully playable 3D chess game drawn in a hand-sketched pencil-and-ink style, in a single HTML file.

Open `index.html` in a modern browser (needs an internet connection for the CDN libraries and fonts).

## Features

- **Pencil-sketch rendering** — screen-space cross-hatching shaders, jittery double-stroke ink outlines, scribbled dark squares, handwritten coordinates, hatched shadows, and an optional "wiggle" that redraws lines a few times a second.
- **Full chess rules** via [chess.js](https://github.com/jhlywa/chess.js): castling, en passant, promotion, check, checkmate and draws.
- **Interaction** — drag-and-drop or click-to-move, legal-move markers, arcing move animations, captured pieces slide into a tray beside the board, promotion picker with 3D-rendered thumbnails.
- **Camera** — orbit, pan and zoom (mouse or touch), flip to Black's side, reset view.
- **UI** — turn indicator, check/mate/draw banners, move log, undo/redo, synthesized pencil sound effects.

## Controls

| Action | Input |
| --- | --- |
| Move a piece | Drag it, or click it then click a square |
| Orbit / pan / zoom | Drag empty space / right-drag / scroll or pinch |
| Undo / redo | Ctrl+Z / Ctrl+Y |
| Flip board / reset camera | F / C |
| Cancel selection or promotion | Esc |

Built with [Three.js](https://threejs.org) r160 and chess.js 1.0.0, loaded from jsDelivr.
