# Modern Tetris

A modern, mobile-first Tetris in a single self-contained HTML file. No build step, no frameworks, no dependencies, no network calls — open it and play.

Play: **https://jlaiii.github.io/modern-tetris/**

## Features

- **Main menu** — Play, High Scores, Settings, Cheats, How to Play.
- **Modern mechanics** — seven-bag randomiser, SRS rotation with full wall-kick tables, hold, ghost piece, configurable next queue, lock delay with move reset, T-spin detection (mini and full), back-to-back and combo scoring.
- **Thirty toggleable cheats** in five tabs (Auto-play, Board, Control, Pieces & Score, Visuals) — see below. Every cheat applies instantly, including mid-game from the pause screen.
- **Six auto-play personalities** — Balanced, Tetris Hunter, Perfect Clear, Survivor, Speed Demon and Saboteur — plus deep-think lookahead, bot-uses-hold, a visible bot plan and auto-restart.
- **Mobile-first controls** — a 7-button touch pad sized for thumbs, plus swipe gestures on the board (drag to move, drag down to soft drop, flick down to hard drop, tap to rotate, swipe up to hold).
- **Keyboard controls** — arrows to move and rotate, `Space` to hard drop, `C` to hold, `P` to pause, `R` to restart.
- **Themes** — Neon, Synthwave, Mono and Daylight, each a full colour re-skin.
- **Local high scores** — top 10 runs, plus best score / games played / total lines, all stored in `localStorage`.
- **Generated audio** — short WebAudio blips, no asset files.
- **Responsive** — verified from 320 px phones up to desktop, including landscape.

## Cheats

Thirty cheats, grouped into five tabs on the Cheats screen. Everything applies instantly, mid-run included.

**Auto-play**

| Cheat | What it does |
| --- | --- |
| Auto-play | Off, or a bot personality: Balanced, Tetris Hunter, Perfect Clear, Survivor, Speed Demon, Saboteur. |
| Bot speed | Chill / Normal / Fast / Turbo (300 / 90 / 35 / 14 ms per move). |
| Deep think | Looks one piece ahead before committing — slower decisions, tidier stacking. |
| Bot uses hold | Lets the bot park a piece in hold when the next one fits better. |
| Show bot plan | Outlines the placement the bot has picked before it commits. |
| Auto-restart | Starts a fresh run automatically when the stack tops out — useful with a bot mode on for an endless demo. |

**Board**

| Cheat | What it does |
| --- | --- |
| No top-out | Blocks that would overflow are discarded — the game never ends. |
| Clear bottom row | Deletes the lowest occupied row right now. |
| Wipe the board | Empties the whole playfield, keeping score and level. |
| Bomb tallest column | Rubs out every block in the column built highest. |
| Load bottom row | Fills the bottom row and leaves a single gap to close. |
| Garbage rain | Pushes five rows of garbage up from the floor. |
| Undo last drop | Steps back up to 5 drops. |
| Rewind run | Restarts the run in place — board, score, lines and level reset. |

**Control**

| Cheat | What it does |
| --- | --- |
| Zero gravity | Pieces only move when you move them. |
| Slow motion | Gravity runs at a quarter speed. |
| Hyper speed | Gravity runs eight times faster. |
| Smart slow-mo | Drops into slow motion on its own once the stack gets dangerous. |
| Anti-gravity | Pieces float upwards and lock against the ceiling. |

**Pieces & Score**

| Cheat | What it does |
| --- | --- |
| Infinite hold | Swap with hold as many times as you like. |
| Choose a piece | Spawn any of the seven pieces on demand. |
| Random piece | Swap the falling piece for a random one. |
| Combo keeper | A miss no longer breaks your combo chain. |
| Back-to-back keeper | The x1.5 back-to-back bonus never drops. |
| Tetris forever | Any line clear scores as a Tetris. |
| Score multiplier | 1x / 2x / 5x / 10x on every point you earn. |
| Freeze level | Gravity stays put — the level never rises. |

**Visuals**

| Cheat | What it does |
| --- | --- |
| Column guide | Vertical light under the falling piece down to the floor. |
| Hole highlighter | Tints covered gaps in the stack. |
| Live stats | Pieces, pieces per second, stack height, holes and the bot's score, drawn on the board. |

Cheats are honest about themselves: any run played with a cheat enabled is saved to the high-score list tagged **assisted**.

### Auto-play modes

| Mode | Behaviour |
| --- | --- |
| Balanced | El-Tetris-style heuristic: steady line clears, low stack. |
| Tetris Hunter | Keeps column 1 open as a well and refuses to spend rows on small clears — it plays for tetrises. |
| Perfect Clear | Weights clearing rows and empty boards far more heavily than anything else. |
| Survivor | Heavy hole and height penalties — plays it safe and rarely tops out. |
| Speed Demon | Balanced play at the Turbo interval (14 ms per move). |
| Saboteur | Picks the *worst* placement on purpose. Not useful. Very funny. |

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

The file exposes a small debug API on `window.__tetris` (`start`, `pause`, `resume`, `quit`, `move`, `rotate`, `hardDrop`, `hold`, `advance(ms)`, `state()`, `setCheat`, `setSetting`, `setBoard`, `pickPiece`, `wipeBoard`, `bombColumn`, `garbageRain`, `fillBottom`, `rewind`, `botPlan()`, `botModes()`, `setCheatTab()`, ...) plus `window.__GAME_OK`, which is set once the game boots. They exist so the game can be driven headlessly by automated tests; they are not needed for normal play.

## Licence

MIT
