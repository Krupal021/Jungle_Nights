# 🌴 Jungle Night — a Game Boy style survival adventure

A single-file, retro Game Boy–inspired browser game. No build tools, no
dependencies, no external images — everything (pixel-art sprites, chiptune
sound effects, and music loops) is generated in plain HTML/CSS/JavaScript
using `<canvas>` and the Web Audio API.

## The story
You play a girl exploring a jungle by day, looking for your friend who
got lost. Find him, gather **sticks** and **stones** to craft a **sword**,
and grab **apples** for healing — because once night falls, monsters come
hunting, and you'll both need to fight to survive.

## Controls
| Action | Keys |
|---|---|
| Move | Arrow keys or `W A S D` |
| Attack | `Z` |
| Eat apple (heal +30 HP) | `X` |
| Start / Restart | `Enter` |
| Mute / Unmute | `M` |

## Gameplay rules (as requested)
- Player and friend each have **120 HP**.
- The monster has **200 HP**.
- Sword hits deal **15 damage** per hit (fists only deal 5 — craft the
  sword!).
- Crafting requires **2 sticks + 1 stone**, picked up while exploring.
- Apples heal **30 HP** each.
- A day timer counts down while you explore — when it hits zero, night
  falls and the monster attacks.

## How to play it right now
Just open `index.html` in any modern browser (Chrome, Firefox, Edge,
Safari). No server or install required.

## How to publish it on GitHub so anyone can play in a browser
1. Create a new repository on GitHub (e.g. `jungle-night-gameboy`).
2. Upload `index.html` (and this `README.md`) to the repo root.
3. Go to **Settings → Pages**.
4. Under **Build and deployment**, set **Source** to `Deploy from a
   branch`, branch `main`, folder `/ (root)`. Save.
5. Wait a minute, then GitHub will give you a live link like:
   `https://<your-username>.github.io/jungle-night-gameboy/`

That's it — the game runs entirely client-side, so GitHub Pages is all
you need (no backend, no database).

## Notes on the art style
This uses a small curated retro palette (in the spirit of a Game Boy
Color era title) rather than the original 4-shade monochrome Game Boy
green palette, specifically so skin tones, hair, and clothing could be
represented — the true 1989 monochrome DMG palette can't render color
at all, so it wouldn't be able to depict the characters as described.
Sprites are hand-composed from rectangles at 3x pixel scale with
`image-rendering: pixelated` to keep the blocky, crisp retro look.

## File structure
```
index.html   ← the entire game (HTML + CSS + JS, self-contained)
README.md    ← this file
```

Feel free to tweak balance values at the top of the `<script>` block in
`index.html` — search for `Game.dayTimer`, `p.hp`, `m.hp`, and the
damage numbers in `tryAttack()` / `updateCombat()`.
