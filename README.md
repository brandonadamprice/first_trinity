# First Trinity Oktoberfest — A Very Silly Pixel Fest 🥨

A tiny 2D pixel-art exploration game of the **First Trinity Oktoberfest**
(First Trinity Evangelical-Lutheran Church, 533 N Neville St, Pittsburgh — est. 1837).

The grounds are modeled on the official FOCUS Oktoberfest map: the Sanctuary
(open for visits, with the Women's Sanctuary Restroom off the narthex and the
organ loft above it), one walkway leading up into the fellowship hallway — the
Kid's Center + booths (Caitlyn at crafts, Debra at the PLDM table) are entered
from the side through it — the PALM and LSF ministry tents (with Brandon and
Pastor Andrae), the axe throw with Alex, cornhole with Kristi, Mirka's food
line beside the rectory, David grilling out back, Terry at the info tent, the
back parking lot connecting both driveways, and the Biergarten — where Mike
and Norm hold down the tables and the Pittsburgh PolkaMeisters play facing
the crowd. Requesting a song really changes the music.

## Play

Open `index.html`. That's it — the whole game is one file with **zero
dependencies, no build step, and no external assets** (all pixel art and music
are generated in code), so it works from a plain file, any static host, or
embedded in a website.

### Controls

| Action        | Keyboard              | Touch          |
|---------------|-----------------------|----------------|
| Move          | WASD / Arrow keys     | D-pad          |
| Interact      | E / Space / Enter     | A button       |
| Quest list    | Tab / C               | ☰ QUESTS       |
| Music on/off  | M                     | ♪ button       |

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
