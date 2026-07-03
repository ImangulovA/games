# Daily Games

A tiny launcher hub for my daily puzzle games, in the spirit of the NYT Games
page. One place to jump into today's puzzle for each game, see your current
streak, and browse the archive.

**Live:** https://imangulova.github.io/games/

## Games

| Game | Live |
|------|------|
| 🚆 Train Tracks | https://imangulova.github.io/train-tracks/ |
| 🚢 Battleships  | https://imangulova.github.io/battleships/ |
| 🎣 ru-catfishing | https://imangulova.github.io/ru-catfishing/ |

## How it works

All three games are served as GitHub Pages **project sites under the same
origin** (`imangulova.github.io`). Because `localStorage` is scoped per origin
(not per path), the games all share this browser's `localStorage`, so this hub
reads each game's per-day progress records directly — no backend, no accounts,
nothing leaves the browser.

Each game writes one record per day under `` `${prefix}${dayIndex}` ``:

- **Train Tracks / Battleships** (`train-tracks_day*`, `battleships_day*`):
  `{ started, finished, elapsedMs, live, result }`
- **ru-catfishing** (`rucatfish_day*`):
  `{ i, results:['win'|'half'|'lose'|null], done, live }`

The registry (anchor date, key prefix, record shape) lives in `GAMES` at the top
of the `<script>` in `index.html`. To add a new game, add one entry there.

## Deploy

Plain static HTML — no build step. The repo is `ImangulovA/games`, served at
`imangulova.github.io/games/`.
**Settings → Pages → Source = Deploy from a branch → `main` / root.**
