# ⚽ soccerTeamMgr

A web page that splits players into evenly balanced soccer teams based on their skill ratings. Everything runs in a single `index.html` with no server.

**Live:** https://chococula.github.io/soccerTeamMgr/

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

The roster is saved in the browser (localStorage). "Share link" creates a URL with the roster encoded in it.

## Running
- Locally: open `index.html` in a browser.
- Hosted: GitHub Pages serves the `main` branch root.
