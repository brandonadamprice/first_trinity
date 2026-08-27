# First Trinity Oktoberfest — A Very Silly Pixel Fest 🥨

A tiny 2D pixel-art exploration game of the **First Trinity Oktoberfest**
(First Trinity Evangelical-Lutheran Church, 533 N Neville St, Pittsburgh — est. 1837).

The grounds are modeled on the official FOCUS Oktoberfest map: the Sanctuary
(open for visits, with the Women's Sanctuary Restroom off the narthex and the
organ loft above it), one walkway leading up into the fellowship hallway — the
Kid's Center + booths (Caitlyn at crafts, Debra at the PLDM table, and Lily,
Danielle and Hallie running the place) are entered from the side through it —
the PALM and LSF ministry tents (with Brandon and Pastor Andrae), the axe
throw with Alex, cornhole with Kristi, Mirka's serving row up against the
rectory wall (you join at the south end and walk the line),
David grilling out back, Terry at the info tent, the back parking lot
connecting both driveways, and the Biergarten — where Mike, Cindy and Norm
hold down the tables and the Pittsburgh PolkaMeisters play facing the crowd.
Requesting a song really changes the music.

## Play

Open `index.html`. That's it — the whole game is one file with **zero
dependencies, no build step, and no external assets** (all pixel art and music
are generated in code), so it works from a plain file, any static host, or
embedded in a website.

### Controls

| Action        | Keyboard              | Touch          |
|---------------|-----------------------|----------------|
| Move          | WASD / Arrow keys     | D-pad          |
| Sprint        | Hold Shift            | —              |
| Interact      | E / Space / Enter     | A button       |
| Quest list    | Tab / C               | ☰ QUESTS       |
| Music on/off  | M                     | ♪ button       |

On touch screens the game fills the display, the controls scale up for
thumbs, and the D-pad is slideable — drag toward a corner to walk
diagonally. Portrait phones get a Game Boy-style layout: a taller,
zoomed-in view up top with the controls in their own space below.

### The Festkarte (quest list)

Ten very important festival achievements:

1. 🥨 Grab a giant pretzel
2. 🌭 Get a brat from the grill
3. 🍺 Win the stein hold (mash to keep it up — losing is allowed, retrying is optional)
4. 🪓 Hit a bullseye at the axe throw
5. 🌽 Sink a cornhole bag (set power, then aim — beat Kristi)
6. 🎈 Get a balloon dachshund
7. 🎵 Request a song from the Pittsburgh PolkaMeisters
8. ⛪ Visit the sanctuary altar
9. 🐶 Pet Strudel the dachshund
10. 🚻 Discover all three legendary restrooms

Finish them all to become an **OKTOBERFEST LEGEND**.

## Embedding in a website

Either copy `index.html` (rename it however you like) onto your site and link
to it, or drop it in an iframe:

```html
<iframe src="/oktoberfest-game.html"
        style="width:100%;max-width:960px;aspect-ratio:3/2;border:0"
        allow="autoplay"
        title="First Trinity Oktoberfest game"></iframe>
```

The game scales itself to whatever space it's given and automatically shows
touch controls on phones/tablets.

## Tech notes

- Single-file HTML5 `<canvas>` game, 480×320 internal resolution, integer-scaled.
- All sprites, tiles, and the church facade title screen are drawn procedurally.
- Music is a little 2/4 chiptune oompah generated with the Web Audio API
  (on by default after your first input; toggle with M or the ♪ button —
  four tunes total, three of them requestable from the band).
- Text is rendered with a built-in 5×7 pixel bitmap font.
- Dialogue is authored as **phrases** — one phrase is one complete thought,
  written out in full rather than hand-broken into display lines. At talk time
  each phrase is word-wrapped to the box's current width and packed into pages
  of `DLG_ROWS` lines, and the box resizes to fit the page, so a long thought
  fills the box and a short one doesn't leave it half empty. The wrap measures
  the box rather than assuming 480, so it follows portrait mode down to 360 and
  an open box re-wraps if the phone is rotated. A new phrase always starts a new
  box — that's how a punchline keeps its own beat. Put `\n` inside a phrase to
  force a break (signs and the noticeboard use this).
- Characters don't recite. Each one has a **repertoire** of about three things
  to say, and `chatter()` plays *one* per interaction, cycling from the top, so
  talking again gets you something new. An entry is one phrase, or an array of
  phrases when a joke needs more than one box in a row (Alex's three rules).
  Booths give their full spiel once — gated on a `met` flag, not on the quest,
  so backing out of a minigame doesn't restart the whole pitch — then fall back
  to chatter. Scripted moments (quest beats, minigame results, scenery you
  examine) still play as written with `say()`.
- **Every utterance has to stand on its own**, because any of them can be the
  first thing you hear. A line that answers or continues another one belongs in
  the same entry, not in a separate one — Chuck's "DON'T TELL ANYONE I SAID
  DAT" is stapled to the Stillers line it answers, and Mike says "I PACE MYSELF
  ON THE BRATS" rather than leaving "THE PACE IS FOUR" to dangle.
- People are drawn by `drawPerson()` at 12px with a two-frame walk: feet apart
  on one frame, together with the body lifted a pixel on the other. The stride
  has to live in the two rows below the body block, which paints over
  everything above `y+12`. Kids (`kid:true`) use `drawKid()` — the same build
  four rows shorter with a full-size head, which is what reads as "child" at
  this scale; `small:true` takes another row off for the three-year-olds.
- The bitmap font is ASCII plus `Ë`, whose E is squashed to six rows to fit the
  diaeresis. `drawText` silently skips glyphs it doesn't have, so a new
  character's name needs a glyph before it will render.
