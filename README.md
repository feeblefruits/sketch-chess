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

## Film studio

The **Film** button turns an annotated game into a narrated, auto-directed vertical video (1080×1920, 60 fps MP4). It ships with one story: the endgame of **Flohr vs Vidmar, Nottingham 1936**.

- **Preview**: Play/Pause (Space), scrub, or click a beat (← / → jump between beats). What you preview is exactly what gets recorded.
- **Export MP4** renders frame by frame on a virtual clock, so playback speed doesn't matter, and encodes H.264 + AAC in the browser with WebCodecs ([Mediabunny](https://mediabunny.dev)). Use a recent Chrome or Edge.
- **Voiceover**: "Narration script" copies and downloads one line per beat (`vo-01`, `vo-02`, …). Record or generate a clip per line, name it to match (`vo-03.mp3`), and drop the clips on the panel. Each beat stretches to fit its clip, and the clips are mixed into the export.
- **Subtitles .srt** downloads captions timed to the film.

### Writing a story

Stories are PGN embedded in `index.html` as `<script type="text/x-chess-story">`. A comment with text opens a *beat*: it becomes a caption card and one narration line, and the moves after it play while it is on screen. Tags inside comments direct the film:

| Tag | Effect |
| --- | --- |
| `[%cam preset squares…]` | Camera shot: `overview`, `top`, `frame`, `closeup`, `low`, `orbit`, `follow` (tracks the pieces on those squares), `profile` (looks along a line of squares). Add `b` to shoot from Black's side. Without one, the director frames the beat's moves and drops to a low angle for checks. |
| `[%cal Gd2d4,Rb6d4]` / `[%csl Rd5]` | Pencil arrows / circles that draw themselves on (G graphite, R red, B blue, Y highlighter) |
| `[%zone Bd4]`, `[%trail Ga7a8]`, `[%cross c5]`, `[%tick e4]` | Hatched square, back-and-forth trail, scribbled-out square, tick |
| `[%label d5 "isolated"]` | Handwritten label pinned to a square |
| `[%think c1]` | The piece hesitates (lifts and wobbles) before the next move |
| `( variation )` | Played as a see-through "ghost" line, then crossed out (or ticked with `!`) and rewound |
| `!` after a move | Slow motion |
| `[%title "…"]`, `[%hold 2]`, `[%speed 1.7]`, `[%timelapse 0.3]`, `[%recap "a\|b\|c"]`, `[%vo id]` | Chapter title, pause, pacing, flip-book run, closing checklist, voiceover clip name |

Built with [Three.js](https://threejs.org) r160, chess.js 1.0.0 and Mediabunny 1.61, loaded from jsDelivr.
