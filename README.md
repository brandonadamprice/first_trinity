# First Trinity Oktoberfest — A Very Silly Pixel Fest 🥨

A tiny 2D pixel-art exploration game of the **First Trinity Oktoberfest**
(First Trinity Evangelical-Lutheran Church, 533 N Neville St, Pittsburgh — est. 1837).

The grounds are modeled on the official FOCUS Oktoberfest map: the Sanctuary
(open for visits!), the fellowship hall with all **three legendary restrooms**,
the Kid's Center + booths, the gazebos, the axe throw, the food tent, the back
parking lot up the driveway, and the Biergarten — where the Pittsburgh
PolkaMeisters are playing.

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

Nine very important festival achievements:

1. 🥨 Grab a giant pretzel
2. 🌭 Get a brat from the grill
3. 🍺 Win the stein hold (mash to keep it up!)
4. 🪓 Hit a bullseye at the axe throw
5. 🎈 Get a balloon dachshund
6. 🎵 Request a song from the Pittsburgh PolkaMeisters
7. ⛪ Visit the sanctuary altar
8. 🐶 Pet Strudel the dachshund
9. 🚻 Discover all three legendary restrooms

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
  (off by default; toggle with M or the ♪ button).
- Text is rendered with a built-in 5×7 pixel bitmap font.
