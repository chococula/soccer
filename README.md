# ⚽ soccer

A web page that splits players into evenly balanced soccer teams based on their skill ratings. Everything runs in a single `index.html` with no server.

**Live:** https://chococula.github.io/soccer/

## Input
- **Player cards**: one card per player with five skills rated 1–5 stars (Speed, Passing, Shooting, Defense, Stamina), each labeled with its full name. The card shows an OVR (20–100), and its color changes with the rating: bronze, silver, gold, or elite. On phones the cards stack one per row with large stars that are easy to tap.
- **Position** (optional): tap GK / DF / MF / FW on the card (tap again to clear). Positions are spread across teams, so the goalkeepers don't all end up on one team.
- **Playing** switch on each card: turn it off for anyone sitting out today.
- **Number of teams** and **players per team**: set with the − / + buttons.
- The bar at the bottom always shows whether you have enough players. **Make teams** becomes active once you do.

## How it works
1. Snake draft by average rating (1→2→2→1 …)
2. Swap players between teams to minimize the spread of team averages, per-skill averages, and position counts
3. Repeat 40 times and keep the most balanced result. "Shuffle again" gives a different, similarly balanced split.

If more players are checked in than `teams × players per team`, the extras are spread across the teams as subs.

## Privacy
The roster is saved only in the browser on your device (localStorage). There is no share link, the page ignores roster data in URLs, and nothing is sent to any server. Other people opening the same URL see an empty roster.

## Saving and importing players (JSON)
**Save JSON** downloads the roster as `soccer-players-YYYY-MM-DD.json` to the device (on iPhone it goes to Files → Downloads). Keep this file as a backup.

Tap **Import JSON** next to the player count. If a player's name is already on the list, that player is updated. New names are added. The result is saved on the device.

```json
[
  { "name": "John", "pos": "FW", "skills": [4, 3, 5, 2, 4] },
  { "name": "Mike", "pos": "DF", "Speed": 3, "Passing": 4, "Shooting": 3, "Defense": 5, "Stamina": 3 }
]
```
`skills` follows the order Speed, Passing, Shooting, Defense, Stamina, each 1–5. `{ "players": [...] }` also works.

## Running
- Locally: open `index.html` in a browser.
- Hosted: GitHub Pages serves the `main` branch root.
