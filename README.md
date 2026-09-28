# Modern Tetris

A modern, mobile-first Tetris in a single self-contained HTML file. No build step, no frameworks, no dependencies, no network calls — open it and play.

Play: **https://jlaiii.github.io/modern-tetris/**

## Features

- **Main menu** — Play, High Scores, Settings, Cheats, How to Play.
- **Modern mechanics** — seven-bag randomiser, SRS rotation with full wall-kick tables, hold, ghost piece, configurable next queue, lock delay with move reset, T-spin detection (mini and full), back-to-back and combo scoring.
- **Nine toggleable cheats** — see below. Every cheat applies instantly, including mid-game from the pause screen.
- **Mobile-first controls** — a 7-button touch pad sized for thumbs, plus swipe gestures on the board (drag to move, drag down to soft drop, flick down to hard drop, tap to rotate, swipe up to hold).
- **Keyboard controls** — arrows to move and rotate, `Space` to hard drop, `C` to hold, `P` to pause, `R` to restart.
- **Themes** — Neon, Synthwave, Mono and Daylight, each a full colour re-skin.
- **Local high scores** — top 10 runs, plus best score / games played / total lines, all stored in `localStorage`.
- **Generated audio** — short WebAudio blips, no asset files.
- **Responsive** — verified from 320 px phones up to desktop, including landscape.

## Cheats

| Cheat | What it does |
| --- | --- |
| No top-out | Blocks that would overflow are discarded — the game never ends. |
| Infinite hold | Swap with hold as many times as you like. |
| Zero gravity | Pieces only move when you move them. |
| Slow motion | Gravity runs at a quarter speed. |
| Score multiplier | 1x / 2x / 5x / 10x on every point you earn. |
| Auto-play | The machine plays with an El-Tetris-style stacking heuristic — it clears lines reliably. |
| Clear bottom row | Deletes the lowest occupied row on demand. |
| Choose a piece | Spawn any of the seven pieces immediately. |
| Undo last drop | Steps the board back up to 5 drops. |

Cheats are honest about themselves: any run played with a cheat enabled is saved to the high-score list tagged **assisted**.

## Controls

Keyboard:

| Action | Keys |
| --- | --- |
| Move | `←` `→` |
| Soft drop | `↓` |
| Hard drop | `Space` |
| Rotate clockwise / counter-clockwise | `↑` / `X` · `Z` |
| Hold | `C` |
| Pause | `P` / `Esc` |
| Restart | `R` |

Touch: the pad under the board mirrors all of those actions. Swipe gestures on the board itself are on by default and can be switched off in Settings. A left-handed layout is available.

## Scoring

- Single / Double / Triple / Tetris — 100 / 300 / 500 / 800
- T-spin single / double / triple — 800 / 1200 / 1600 (mini 200 / 400)
- Back-to-back bonus — x1.5
- Combo — +50 per chained clear
- Soft drop 1 point per row, hard drop 2 points per row
- All line points scale with the level (a new level every 10 lines)

## Running it

Open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server 8000
```

There is no build step. The single file contains the markup, styles and game logic.

## Development notes

The file exposes a small debug API on `window.__tetris` (`start`, `pause`, `advance(ms)`, `state()`, `setCheat`, `setSetting`, `hardDrop`, ...) plus `window.__GAME_OK`, which is set once the game boots. They exist so the game can be driven headlessly by automated tests; they are not needed for normal play.

## Licence

MIT
