# Sketch Chess

A fully playable 3D chess game drawn in a hand-sketched pencil-and-ink style, in a single HTML file.

Open `index.html` in a modern browser (needs an internet connection for the CDN libraries and fonts).

## Features

- **Pencil-sketch rendering** — screen-space cross-hatching shaders, jittery double-stroke ink outlines (with a thin paper halo around the dark pieces, so they stay separate silhouettes when they overlap), scribbled dark squares, handwritten coordinates, hatched shadows, and an optional "wiggle" that redraws lines a few times a second. Turn the wiggle off (W) to hold every stroke still, in the game, in films and in exports; the setting is remembered between visits.
- **Full chess rules** via [chess.js](https://github.com/jhlywa/chess.js): castling, en passant, promotion, check, checkmate and draws.
- **Interaction** — drag-and-drop or click-to-move, legal-move markers, arcing move animations, captures burst into a three-frame puff of graphite and eraser dust as the taken piece slides into a tray beside the board, promotion picker with 3D-rendered thumbnails.
- **Camera** — orbit, pan and zoom (mouse or touch), flip to Black's side, reset view.
- **Colour** — switch between the pencil look and ink-and-wash colour: a green and cream board in a wooden frame, ivory and charcoal pieces, parchment page. Applies to the game, films and exports, and is remembered between visits. The toolbar's Colour button and the film studio's own pair of Colour and Wiggle buttons do the same thing, so you can set the look without leaving a story.
- **Diagram view** — look straight down at the board with the 3D pieces swapped for hand-inked diagram symbols (they crossfade). The symbols stay upright as you turn the board.
- **Move labels and evaluation bar** — the **Eval**, **Labels** and **All** buttons in the moves panel. While you play, Stockfish checks every position in the background (it loads from jsDelivr when first needed). **Eval** shows an evaluation bar beside the board (E). **Labels** (L) marks moves the way chess sites do, by how much of the player's winning chances a move gives away: by default only brilliant **!!** (a sacrifice that is still one of the best moves) and blunder **??** (more than 20% thrown away); with **All**, also great **!** (the only good move), best **★**, excellent and good **✓**, inaccuracy **?!**, mistake **?** and miss **✗** (the opponent's mistake not punished). Labels show in the moves list, the storyboard and as a pencil ring on the board, and a note pops up when one is played (or replayed after an undo). Undo a blunder, mistake or miss and a dashed blue arrow shows the engine's move instead. A quick engine scores positions slightly better for the side to move; that wobble is measured over the game and taken out before moves are judged.
- **UI** — turn indicator, check/mate/draw banners, undo/redo, synthesized pencil sound effects. The moves are kept in a small spiral notebook in the corner: its cover shows how many moves have been played (and a tab for the latest labelled move), and flips up over the spiral to open a ruled page with the moves, ten to a page, with a dog-eared corner to turn pages. The toolbar holds New game, Undo and Redo; the round ⋯ button grows it upwards into a drawer with everything else (flip, diagram, view, colour, wiggle, storyboard, film, sound), which stays open until you close it.

## Controls

| Action | Input |
| --- | --- |
| Move a piece | Drag it, or click it then click a square |
| Orbit / pan / zoom | Drag empty space / right-drag / scroll or pinch |
| Undo / redo | Ctrl+Z / Ctrl+Y |
| Flip board / reset camera | F / C |
| Diagram view on / off | D |
| Colour on / off | K |
| Line wiggle on / off | W |
| Evaluation bar on / off | E |
| Move labels on / off | L |
| Moves notebook open / closed | N |
| Toolbar drawer open / closed | M |
| Hide / show everything but the board (also the eye in the bottom-right corner) | H |
| Storyboard on / off | S |
| Storyboard: previous / next move | ← / → |
| Storyboard: delete the move just played (and any after it) | Delete / Backspace |
| Cancel selection or promotion | Esc |

## Storyboard

**Storyboard** (S) turns the game you're playing into a film without writing any PGN. The moves list becomes a column of beat cards, one per caption, and the board shows the film's 9:16 frame as a dashed guide.

- **Play and direct**: play moves as usual. Click any move in a card (or use ← / →) to go back to that position; play a different move there and the line (with its notes) changes from that point. The × next to a move (shown on hover, and always on the current and last moves) deletes it and every move after it, as does Delete / Backspace for the move just played; it asks first if captions or marks would go with them.
- **Captions**: each card has a caption and an optional chapter title. **＋ New beat here** starts a new card at the current move. A card's moves play while its caption is on screen.
- **Marks**: pick Circle, Arrow, Zone, Cross, Tick or Label and a pencil colour, then click squares. Marks belong to the position on the board and stay up until the beat ends, as in the film, unless you stop them sooner: go to a later move and use **Erase** on the square (or **Clear marks** for all of them), and they show until that move, then disappear. Erase at the move where a mark was drawn, or the × on its chip, deletes it altogether.
- **Camera**: the board shows what the film's camera will see at each move (turn off *The board shows the film's camera* to look around freely). The Camera panel names the shot and where it comes from. Pick **Auto** (the director frames the moves), **Overview**, **Close-up** or **Low** (both aim at the last move and the marks), and switch **3D / 2D** (the top-down diagram; the toolbar's Diagram button and D do the same). Or drag the board to frame your own shot inside the dashed film frame and **Save view here** (or **Discard**). A shot lasts from its move until the camera changes or the beat ends.
- **Open in film** opens the storyboard in the film studio, at the beat you're on, to preview, fine-tune in the story editor and export. **Save .pgn** downloads it as a story file. Opening the storyboard again replaces its film, so make final tweaks either in the storyboard or in the studio.

## Film studio

The **Film** button turns an annotated game into a narrated, auto-directed vertical video (1080×1920, 60 fps MP4). It ships with four stories: **The Opera Game** (Morphy, Paris 1858), **The Game of the Century** (Byrne – Fischer, New York 1956), the endgame of **Flohr vs Vidmar, Nottingham 1936**, and **How chess notation works**, a 90-second explainer of squares, piece letters, captures, castling, check and mate, told through Légal's mate.

- **＋ New** starts a story and opens it in the editor: the game you've played on the board, with an intro and a closing caption to fill in, or a short starter that explains the format if you haven't played one. It starts unsaved, so use **Save .pgn** to keep it.
- **Pick a story** from the dropdown, or **Load PGN…** (or drop a `.pgn` on the panel) to film any game. Plain games from Lichess or chessgames.com work as they are; add `{comments}` and tags to narrate and direct them. A file with several games films the first one, and loading the same file again replaces it, so you can edit a story in a text editor and reload. Loaded files last for the session; the app doesn't store them.
- **Preview**: Play/Pause (Space), scrub, or click a beat (← / → jump between beats). What you preview is exactly what gets recorded.
- **Look**: **Colour** (K) and **Wiggle** (W) under the beat list, since the toolbar is out of the way while you film. Colour swaps the pencil look for ink and wash; with the wiggle off the pencil strokes hold still instead of being redrawn a few times a second. Both change the preview and the exported MP4, and both are the same settings as the toolbar's, so they carry back to the game.
- **Move labels in films**: the same labels (and the same Labels / All setting) apply to films. A brilliant move bursts out in a comic **BRILLIANT!!** and a blunder gets a red **BLUNDER??** rubber stamp with a jolt of the camera; every shown label gets a pencil ring on the board and its symbol in the move name, and the notable ones a dot on the evaluation wave. They come from the story's engine evaluations: the built-in films have them, **Analyse** adds them (with the engine's second choice, as `[Evals2]`, which "great" moves need), and storyboards carry over what Stockfish worked out while you played. The editor's status line lists them.
- **Export MP4** renders frame by frame on a virtual clock, so playback speed doesn't matter, and encodes H.264 + AAC in the browser with WebCodecs ([Mediabunny](https://mediabunny.dev)). Use a recent Chrome or Edge.
- **Voiceover**: "Narration script" copies and downloads one line per beat (`vo-01`, `vo-02`, …). Record or generate a clip per line, name it to match (`vo-03.mp3`), and drop the clips on the panel. Each beat stretches to fit its clip, and the clips are mixed into the export.
- **Subtitles .srt** downloads captions timed to the film.
- **Evaluation wave**: the timeline at the bottom of the film is a sideways evaluation bar that rises when White is better and dips when Black is; Black's share is shaded and cross-hatched. What has been played is inked, the rest is a faint preview. The built-in films include engine evaluations. **Analyse** works them out for any other story with Stockfish in the browser (about a minute for a long game) and writes them into the story as an `[Evals]` header; Lichess PGNs that already contain `[%eval]` comments work as they are.

### Editing in the studio

**✎ Edit story** opens the story editor next to the preview. Everything you do there is written into the story's PGN text, so it all ends up in the file you save.

- **Text**: edit captions, moves and tags; the preview recompiles as you type. As the film plays, the current beat is softly highlighted in the text and the move just played more strongly, and the text scrolls to follow (unless you're typing in it). If something doesn't parse, the editor names the line and the preview keeps the last working version.
- **Mark the board**: pick Circle, Arrow, Zone, Cross, Tick or Label and a pencil colour, then click squares on the preview (an arrow takes two clicks). The mark is added at the current moment of the film, after the last move shown, and appears as that piece lands. **Erase** removes the marks on a square that are showing at that moment.
- **Camera**: the Camera panel names the shot at this moment and the story line that sets it. **Auto**, **Overview**, **Close-up**, **Low** and **3D / 2D** write the shot into the story from this moment on. Drag the preview to orbit, right-drag to pan and scroll to zoom, whichever tool is selected (a plain click uses the tool); then **Save view here** keeps that exact view (`[%cam view …]`) and **Discard** hands the camera back.
- **Save .pgn** downloads the story, **Revert** returns to the version you loaded, and **Undo** (or Ctrl+Z in the text) steps back through every change, including marks and camera views. Esc steps out of a tool or the free camera.

### Writing a story

A story is a PGN file (optionally with `[Evals "0.20,0.35,#-3,…"]`, one engine evaluation per position from White's point of view, starting with the initial position): load it with **Load PGN…**, or embed it in `index.html` as a `<script type="text/x-chess-story" id="…">` block to make it a built-in choice in the dropdown. `[FilmHeader "…"]` and `[FilmFile "…"]` set the on-screen header and the export filename; otherwise they come from the White, Black, Event and Date tags. A comment with text opens a *beat*: it becomes a caption card and one narration line, and the moves after it play while it is on screen. Moves don't have to be legal. A move chess.js won't accept is played as written (a *free move*), so you can skip ahead or stage an illustrative position: the named piece of the side to move goes to the square (the nearest one, unless the move says which, like `Nge2` or `R1d1`), capturing whatever is there, and a piece already on its square just passes the turn. The editor lists the free moves under the preview, so a typo doesn't go unnoticed. A move that names a piece the side doesn't have, or that can't be read at all, is still an error. Tags inside comments direct the film:

| Tag | Effect |
| --- | --- |
| `[%cam preset squares…]` | Camera shot: `overview`, `top`, `frame`, `closeup`, `low`, `orbit`, `follow` (tracks the pieces on those squares), `profile` (looks along a line of squares). `auto` hands the camera back to the director mid-beat. Add `b` to shoot from Black's side. `top` shots switch to the diagram view (inked symbols); add `3d` to keep the 3D pieces, or `diagram` to use symbols in any shot. `[%cam view x y z distance phi theta]` holds an exact view (what **Use this view** writes). Without a camera tag, the director frames the beat's moves and drops to a low angle for checks. |
| `[%cal Gd2d4,Rb6d4]` / `[%csl Rd5]` | Pencil arrows / circles that draw themselves on (G graphite, R red, B blue, Y highlighter) |
| `[%zone Bd4]`, `[%trail Ga7a8]`, `[%cross c5]`, `[%tick e4]` | Hatched square, back-and-forth trail, scribbled-out square, tick |
| `[%label d5 "isolated"]` | Handwritten label pinned to a square (add `above` to write it straight over the piece, e.g. `[%label e1 "K" above]`) |
| `[%clear]` / `[%clear c4,f7]` | Take down all the marks (or the ones on those squares) as the move before it lands |
| `[%think c1]` | The piece hesitates (lifts and wobbles) before the next move |
| `( variation )` | Played as a see-through "ghost" line, then crossed out (or ticked with `!`) and rewound |
| `!` after a move | Slow motion |
| `!!` `!` `?!` `?` `??` after a move | Sets the move's label (brilliant, great, inaccuracy, mistake, blunder) whatever the engine says |
| `[%preview end]` / `[%preview 34]` | Open the beat on a later position of the game (the final position, or the position after that many half-moves), e.g. a title shot of the decisive moment; the next beat sweeps the pieces back |
| `[%steady]` | Keep this beat's camera: no automatic cut to a low angle on checks |
| `[%title "…"]`, `[%hold 2]`, `[%speed 1.7]`, `[%timelapse 0.3]`, `[%recap "a\|b\|c"]`, `[%vo id]` | Chapter title, pause, pacing, flip-book run, closing checklist, voiceover clip name |

### Story format reference (for people and LLMs)

Everything a film needs is in one plain-text story file, so a story can be written by hand or generated by an LLM. To turn one into a video, open **Film**, press **Load PGN…** (or **＋ New**, then **✎ Edit story** and paste the text), check the preview, and press **Export MP4**. The editor's status line confirms it worked (`✓ 8 moves · 6 beats · 0:59`) or names the line with the problem.

#### Layout

```text
[Event "…"]                                        ← headers: one per line
[White "…"]
[Black "…"]
[Result "1-0"]
[FilmHeader "…"]                                   ← optional: the on-screen header
[FilmFile "…"]                                     ← optional: the export file name
[FEN "…"]                                          ← optional: start from this position
                                                   ← blank line
{ [%title "…"] [%cam …] marks…  Caption text. }    ← beat 1 (a comment with caption text opens a beat)
1. e4 e5 2. Nf3                                    ← moves played during beat 1
{ [%cam …]  Caption text. }                        ← beat 2
2... Nc6 3. Bb5 { [%csl Rc6] }                     ← a tag-only comment: marks drawn as 3. Bb5 lands
…
1-0                                                ← result
```

#### Rules

1. **Headers.** `[Event]`, `[White]`, `[Black]`, `[Result]` and `[Date]` are standard PGN. Optional film headers:
   - `[FilmHeader "…"]` is the small header at the top of the video.
   - `[FilmFile "…"]` is the export file name, a lowercase slug.
   - `[FEN "…"]` sets the starting position. Positions that aren't legal are accepted, for illustration.
   - `[Evals "…"]` and `[Evals2 "…"]` hold engine evaluations, one per position, written by **Analyse**.
2. **Moves.**
   - Write moves in standard algebraic notation with English piece letters (K Q R B N; pawns get none). Castling is `O-O` or `O-O-O`, promotion is `e8=Q`, and `+` or `#` marks check or mate.
   - Move numbers are optional but help readers. Write a Black move that follows a comment as `12... Nf6`.
   - Annotation symbols go straight after the move with no space: `!`, `?`, `!!`, `??`, `!?`, `?!`.
3. **Comments and beats.**
   - Comments are `{ … }`. Inside one, anything in the form `[%name args]` is a tag, and everything else is the caption.
   - A comment with caption text (or a `[%title]`) starts a new *beat*: a caption card plus the moves that follow it.
   - A comment with only tags adds those tags at that point of the current beat.
4. **When things happen.**
   - Tags in a beat's opening comment act as the beat starts.
   - Tags in a comment straight after a move act as that move's piece lands.
5. **How long things last.**
   - Marks stay until the beat ends, or until `[%clear]` takes them down.
   - A camera tag holds until the next camera tag or the end of the beat.
   - A beat with no camera tag gets the director's shot of its moves, with a low angle on checks.
6. **Square and colour syntax.**
   - Squares are lowercase (`e4`).
   - Arrows, circles, zones and trails need a colour letter in front: `G` graphite, `R` red, `B` blue, `Y` highlighter. For example `[%csl Rd5]` or `[%cal Gd2d4,Rb6d4]`. Separate several items with commas and no spaces.
   - Crosses, ticks and labels take bare squares (`[%cross c5]`, `[%label d5 "weak"]`).
7. **Text.**
   - Keep `{ } [ ]` out of captions.
   - Inside a quoted value (titles, labels, recap), write a double quote as ”.
   - Separate recap items with `|`.
   - Keep labels short (one to three words).
8. **Variations.**
   - `( … )` straight after a move is an alternative to *that* move, for example `3... Kh8 (3... Kf8 4. Qf7#)`.
   - It plays as a see-through "what if" line before the real move, then rewinds. It's crossed out, or ticked if its last move ends with `!`.
9. **Free moves.** A move that isn't legal is played as written (see above). The editor lists free moves, so make sure any you see are intended.

#### Timing

- **Beat length.** A beat lasts as long as the longer of two things, plus any `[%hold n]`:
  - its moves;
  - the time to read its caption, about *words ÷ 2.6 + 1.6* seconds.
- **Moves.** About 1.5 s each, divided by `[%speed]`. Moves marked `!` play slower, captures take a little longer, and a brilliant move or blunder adds about 1 s for its stamp.
- **Marks.** Each mark adds about 0.35 s.
- **Rule of thumb.** 6–9 beats of 15–25 words make a 60–90 s film. The status line shows the exact length.

#### Camera cheat sheet

| `[%cam …]` | Shot |
| --- | --- |
| `overview` | The whole board from a raised angle (squares are ignored) |
| `top` | Straight down on the whole board, in the 2D diagram style |
| `frame a1 h8 …` | Fits the given squares, at a normal angle |
| `closeup e4 f5 …` | Tighter and lower on the given squares |
| `low e1 h4 …` | A low, dramatic angle on the given squares |
| `orbit d4 e5 …` | Slowly circles the given squares |
| `follow g1 …` | Tracks the pieces standing on those squares as they move |
| `profile a7 a1` | Looks along the line from the first square to the last |
| `auto` | Hands the camera back to the director mid-beat |
| `view tx ty tz dist phi theta` | An exact view: the target point (board centre 0 0 0; one unit per square, `a1` at x −3.5, z 3.5), the distance, the tilt `phi` (0 is straight down, about 0.75 is normal, 1.2 is low) and the direction `theta` (0 from White's side, 3.14 from Black's) |

Add `b` to any preset to shoot from Black's side, `3d` to keep 3D pieces in a `top` shot, or `diagram` to use the inked 2D symbols in any shot.

#### Checklist for writing a story (useful in an LLM prompt)

- Start from a real game's PGN, or from a `[FEN]` position. Make sure every move is legal from there, unless a free move is intended.
- Open with a hook: `[%title "…"]`, `[%preview end]` (open on the final position) and a short caption saying what's coming.
- Give each beat one idea, 15–25 words of caption and 1–6 moves.
- Point at what the caption talks about: circle the weak square, draw an arrow for the threat, label the key piece. Put marks right after the move they belong to.
- Show the "what if" lines as variations instead of describing them.
- Close with a `[%recap "…|…|…"]` beat and `[%hold 2]`.
- Set `[FilmHeader]` and `[FilmFile]`.
- Load the story and check the status line: no errors, no unintended free moves, and the length you wanted.

#### Example 1: Fool's mate (31 seconds, standard start)

```pgn
[Event "Fool's mate"]
[White "White"]
[Black "Black"]
[Result "0-1"]
[FilmHeader "The fastest checkmate"]
[FilmFile "fools-mate"]

{ [%title "Fool's mate"] [%preview end] [%cam closeup e1 h4 f2 g3] [%csl Re1] [%cal Rh4e1]
  The fastest checkmate in chess takes just four moves. Here is how White walks into it. [%hold 1] }

{ [%cam overview]
  White weakens the king with two pawn moves on the same side. }
1. f3 e5 2. g4? { [%cal Rd8h4] [%label g4 "too loose"] }

{ [%title "Checkmate"] [%cam low e1 f2 g3 h4] [%steady]
  The queen slides to h4. Nothing can block it, and the king has nowhere to go. }
2... Qh4# { [%csl Re1] }

{ [%cam orbit e1 h4] [%recap "Keep pawns in front of the king|Watch the diagonal to e1"]
  Lesson: don't open the king's diagonal early. [%hold 2] }
0-1
```

#### Example 2: the smothered mate (59 seconds, from a position)

A `[FEN]` start, a "what if" variation, a hesitating piece (`[%think]`), zones, labels and a `!!` sacrifice, which gets the BRILLIANT stamp:

```pgn
[Event "Philidor's legacy"]
[White "White"]
[Black "Black"]
[Result "1-0"]
[FEN "4r1k1/6pp/8/6N1/2Q5/8/5PPP/6K1 b - - 0 1"]
[FilmHeader "The smothered mate"]
[FilmFile "smothered-mate"]

{ [%title "The smothered mate"] [%preview end] [%cam closeup h8 g8 f7 g7 h7] [%label h8 "trapped"]
  A king boxed in by its own pieces can be mated by a lone knight. This is how it happens. [%hold 1] }

{ [%cam frame c4 g8 g5 e8] [%cal Rc4g8] [%zone Rg8]
  The queen on c4 pins Black to the back rank. Black tucks the king into the corner, a fatal mistake. }
1... Kh8?

{ [%cam closeup f7 g8 h8 h6] [%think g5]
  White checks with the knight, and keeps on checking. }
2. Nf7+ Kg8 3. Nh6+ { [%cal Rc4g8,Rh6g8] [%label h6 "double check"] } Kh8 (3... Kf8 4. Qf7#)

{ [%title "The sacrifice"] [%cam low g8 h8 e8 c4] [%think c4]
  Now the queen offers itself on g8. Black has to take it with the rook. }
4. Qg8+!! Rxg8

{ [%cam closeup f7 g8 h8 g7 h7] [%steady]
  The knight returns, and the king is smothered by its own rook and pawns. }
5. Nf7# { [%csl Rh8] [%zone Rg8,Rg7,Rh7] }

{ [%cam orbit h8 f7] [%recap "Pin the king to the back rank|Check with the knight|Sacrifice the queen on g8|Mate with the knight"]
  Checkmate with a single knight. [%hold 2] }
1-0
```

The built-in **How chess notation works** film is a third example. Its story is the `<script type="text/x-chess-story" id="chess-notation">` block in `index.html`, and it uses exact `view` cameras, the 2D diagram style and labels written above pieces.

Built with [Three.js](https://threejs.org) r160, chess.js 1.0.0 and Mediabunny 1.61, loaded from jsDelivr.

Sound effects: wooden impact recordings from Kenney's [Impact Sounds](https://kenney.nl/assets/impact-sounds) pack (CC0, public domain), trimmed and embedded in the page. Thanks, Kenney!
