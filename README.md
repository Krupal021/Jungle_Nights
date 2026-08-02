# 🌴 Jungle Night — a Game Boy style survival adventure (now on Android)

A retro Game Boy–inspired browser game, playable on desktop **and Android**.
No build tools, no app store, no APK compiling required — it's a
installable **PWA (Progressive Web App)**: open it in Chrome on your
phone, tap "Add to Home Screen," and it launches full-screen like a
native app, works offline, and has on-screen touch controls styled to
match the Game Boy shell.

## The story
You play a girl exploring a jungle by day, looking for her friend who
got lost. Find him, gather **sticks** and **stones** to craft a **sword**,
and grab **apples** for healing — because once night falls, monsters come
hunting, and you'll both need to fight to survive.

## What's new in this version
- **Fixed the left-facing glitch** — turning left used to make both the
  girl and her friend vanish. The sprite-mirroring math was placing them
  hundreds of pixels off the right edge of the canvas any time either
  character faced left. Now movement and following work correctly in
  every direction.
- **Pokémon Fire Red style wild encounters** — step into a patch of tall
  grass while exploring and you may be ambushed by a wild jungle
  critter (Forest Boar, Hornet Swarm, or Cave Bat), complete with a
  flashing screen-wipe battle transition just like the classic games.
  Win and it drops a stick, stone, or apple; lose HP if you're careless.
- **Fire Red style battle menu** — a FIGHT / ITEM / ALLY / RUN box now
  appears in every battle, mirroring the iconic four-option layout.
  Direct hotkeys (Z/X) still work instantly; RUN is new.
- **RUN option** — you can flee a wild critter (usually succeeds, but
  not always — "Couldn't get away!" can happen, just like in Fire Red).
  You cannot run from the main night monster — the story's climax has
  to be fought.
- **More overworld texture** — tall grass patches, wildflowers, loose
  rocks (a new light obstacle), a dirt path, and a small pond now
  dress up the jungle, closer to a Fire Red route.
- **Enter your name** — a "Who's exploring today?" screen appears before
  the title screen. Whatever name you type is used throughout the game
  (health bar label, win/lose messages).
- **Girl is the sole playable character** — you always control her; the
  friend is a loyal AI ally who fights alongside you once found.
- **"Happy Friendship Day" pop-up** — appears with a pulsing gold banner
  and confetti when you win, alongside "SURVIVED THE NIGHT!"
- **Android-ready** — responsive full-screen layout, on-screen D-pad and
  A/B touch buttons (⚔ attack / 🍎 heal / 🏃 run), installable as a
  home-screen app, works offline after first load.
- Desktop/keyboard play is unchanged and still fully supported.

## Controls
| Action | Keyboard | Touch (Android) |
|---|---|---|
| Move | Arrow keys or `W A S D` | On-screen D-pad |
| Attack | `Z` | ⚔ button |
| Eat apple (heal +30 HP) | `X` | 🍎 button |
| Run (wild critter fights only) | `R` | RUN button |
| Start / Restart | `Enter` | START button |
| Mute / Unmute | `M` | MUTE button |

## Gameplay rules
- Player and friend each have **120 HP**.
- The monster has **200 HP**; wild critters have 24–36 HP and hit for
  4–6 damage.
- Sword hits deal **15 damage** per hit (fists only deal 5 — craft the
  sword!).
- Crafting requires **2 sticks + 1 stone**, picked up while exploring.
- Apples heal **30 HP** each.
- A day timer counts down while you explore (it pauses during wild
  battles) — when it hits zero, night falls and the monster attacks.
- Wild critter fights are optional risk/reward: win for a bonus item,
  or press RUN to try to escape back to exploring.

## How to play it right now
Just open `index.html` in any modern browser (Chrome, Firefox, Edge,
Safari, or Chrome/Samsung Internet on Android). No server or install
required.

## How to publish it on GitHub so anyone can play (including on Android)
1. Create a new repository on GitHub (e.g. `jungle-night-gameboy`).
2. Upload the **entire contents of this folder**, keeping the structure:
   ```
   index.html
   manifest.json
   service-worker.js
   icons/icon-192.png
   icons/icon-512.png
   README.md
   ```
   (The `icons/` folder must stay a folder — don't flatten it.)
3. Go to **Settings → Pages**.
4. Under **Build and deployment**, set **Source** to `Deploy from a
   branch`, branch `main`, folder `/ (root)`. Save.
5. Wait a minute, then GitHub will give you a live link like:
   `https://<your-username>.github.io/jungle-night-gameboy/`

That's it — everything runs client-side, so GitHub Pages is all you
need (no backend, no database, no Android Studio).

## Installing it on an Android phone
1. Open the GitHub Pages link in **Chrome** on your Android phone.
2. Tap the **⋮** menu → **"Add to Home screen"** (Chrome may also
   prompt this automatically as "Install app").
3. It now launches full-screen from your home screen icon, with touch
   controls, just like a native app — and works even with no signal
   after the first load, thanks to the built-in offline cache.

### A quick note on "a real Android app"
This is deployed as an installable web app (PWA) rather than a `.apk`,
because building and signing an actual Android package requires the
Android SDK/Studio toolchain (and a device or emulator to test on),
which isn't something that can be produced or verified here. The PWA
route gives you the same result a player cares about — an icon on the
home screen, full-screen play, offline support, touch controls — without
needing a Play Store listing or a build pipeline. If you'd ever like to
go further and wrap this into a real `.apk` (e.g. with a tool like
Bubblewrap or Capacitor), this file structure is already set up to be
compatible with that step.

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
index.html            ← the entire game (HTML + CSS + JS, self-contained)
manifest.json          ← PWA metadata (name, icons, colors) for installability
service-worker.js      ← offline caching for installed/home-screen play
icons/icon-192.png     ← home screen icon (small)
icons/icon-512.png     ← home screen icon (large / splash)
README.md              ← this file
```

Feel free to tweak balance values at the top of the `<script>` block in
`index.html` — search for `Game.dayTimer`, `p.hp`, `m.hp`, and the
damage numbers in `tryAttack()` / `updateCombat()`. Wild critter stats
live in the `WILD_CRITTERS` array, and encounter frequency is the
`0.35` chance multiplier inside `updateExplore()`.
