> The following readme was AI generated.

# Crusade Manager

A fully offline, browser-based campaign tracker for **Warhammer 40,000 Crusade** events. No server, no account, no installation required — download a single HTML file, open it in any browser, and everything persists in local storage.

---

## Getting Started

Download `index.html` and open it in any modern browser. On first load you'll see the **New Crusade** setup screen. Fill in your campaign details and click **Begin the Crusade**. From that point the app works fully offline — even without an internet connection.

Your data is saved automatically to your browser's local storage after every change. To move data between devices or back it up, use **Settings → Export Crusade Data** to download a JSON file, then **Import Crusade Data** on the other device.

---

## Initial Configuration

When starting a new crusade you configure the following:

**Crusade Name** — displayed throughout the app and on all printed output.

**Number of Alliances** — set to 0 for an individual tournament (no alliance groupings), or 2–20 for a crusade with alliance-level SP tracking. Each alliance gets a name and a colour.

**Pairing Method** — choose between Round Robin and Win Path (see [Pairing Methods](#pairing-methods) below).

**Number of Players** *(Round Robin only)* — used to auto-calculate the default number of rounds. The app computes the minimum rounds needed for every player to face every other player once and divides them evenly across phases.

**Rounds Per Phase** — leave blank to use the auto-calculated default, or enter a number to override it.

**Number of Phases** — defaults to 3. Supports 1 and above.

**Allow Rematches** — if unchecked, the pairing system will avoid matching players who have already played each other.

**Phase Victory Method** — choose between Raw SP Total (the alliance with the most Strategic Points wins the phase) or SP per Match Played (total SP divided by number of cross-alliance matches played, which balances alliances with unequal player counts).

**Play Format** — Individual (players are paired directly) or Team Play (players belong to teams which are paired each round; captains assign individual match-ups offline). See [Team Play](#team-play) below.

---

## Navigation

The top navigation bar has six sections. On small screens it collapses into a hamburger menu (☰).

- **Overview** — at-a-glance dashboard
- **Alliances & Rosters** — manage alliances, teams, and players
- **Matches** — record and browse match results
- **Standings** — phase SP standings, team standings (if applicable), and individual player standings
- **Pairings** — generate and print round pairings
- **Print / Export** — full print centre
- **Settings** — edit crusade configuration and manage data

---

## Overview

The Overview tab shows:

- **Phase bar** — all phases with their round ranges. The current phase is highlighted. Completed phases show their winner, or "Tied" if no alliance won outright. If the crusade is complete (all phases finished), a banner announces the overall winner or a draw.
- **Quick stats** — current round, current phase, total matches played, total players enlisted.
- **Alliance standings** — SP (or SP/Match) for the current phase, with phases won listed per alliance.
- **Recent matches** — the five most recently recorded matches.

---

## Alliances & Rosters

### Individual Mode (0 Alliances)

All players appear in a single roster table. Use **+ Add Player** to enlist players.

### Alliance Mode

Each alliance is shown as a card with its current-phase SP total and a list of its players with W/L records. Use **+ Add Player** to add players and assign them to an alliance.

### Team Play Mode

The view becomes two-level: alliance cards contain team cards. Each team card shows the captain (⚑), team VP total, aggregate W/L, and the full member list with individual records.

**+ Add Team** creates a new team. Team names are ad-hoc — you can add them at any time. Each team has an optional captain designation used on printed pairing sheets.

When adding or editing a player in team play mode, you can assign them to a team. The app enforces that a player's alliance must match their team's alliance.

### Player Actions

- **✎** — edit name, faction, alliance, or team assignment
- **✕** — remove the player (their match records are kept)

---

## Matches

### Recording a Match

Click **+ Record Match** to open the recording modal.

- **Team Pairing** *(team play mode only)* — select the team pairing this match belongs to. The player dropdowns will automatically filter to members of the two teams. This field is optional.
- **Round** — defaults to the current round. Can be changed to record a match from a different round.
- **Phase** — auto-calculated from the round number.
- **Player 1 / Player 2** — select the two players.
- **Result** — Win, Loss, or Draw for each side.
- **Victory Points** — VP scored by each player.
- **Strategic Points Contributed** — SP each player contributes to their alliance's phase total.

### Filtering Matches

Use the dropdowns above the match table to filter by round, phase, or player.

### Deleting a Match

Click **✕** on any row to delete that match record.

---

## Standings

### Phase Alliance Standings

One card per phase showing each alliance's SP total, matches played, and SP/Match (if that victory method is selected). Completed phases show their winner or "Tied". The current phase is marked "In Progress".

### Team Standings *(team play mode)*

A table of all teams sorted by Team VP, showing alliance, captain, player count, VP, W, L, and Win%.

### Individual Player Standings

All players ranked by wins then OGW%. Columns: Player, Alliance, Team *(if applicable)*, W, L, Win%, VP For, VP Against, OGW%, Win Path.

**Win Path** is a string of W/L/D results in round order (e.g. `WWLW`) used for pairing in Win Path mode.

**OGW%** (Opponent Game Win %) is the average win percentage of all opponents a player has faced, used as a tiebreaker.

---

## Pairing Methods

### Round Robin

Players (or teams) are seeded by Win Path — record → path sequence → OGW%. Priority is given to opponents not yet faced. If all opponents have been played and rematches are disabled, the system falls back to Win Path order.

### Win Path

Players are grouped by W/L record, then sub-grouped by their exact sequence of results (e.g. all players who are 2–1 with a loss in round 2 are grouped together). Within each group, players are sorted and paired by OGW% (closest OGW% face each other). If a group has an odd number of players, the one with the lowest OGW% drops down to the next group.

---

## Pairings

### Generating Pairings

Go to the **Pairings** tab and click **Generate Next Round**. The app produces pairings for the current round using the configured method.

**Allow intra-alliance pairings** — uncheck this to prevent players from the same alliance being paired against each other. Hidden in individual tournaments and team play mode.

Bye players (odd groups) appear in an amber alert below the pairings. In individual mode you can optionally record SP for a bye player using the **Record SP** button.

### Locking Pairings

Once you're happy with the pairings, click **Lock & Advance Round**. This commits the pairings to history (for rematch avoidance) and increments the round counter. You can then record the matches for that round.

### Quick Print

The **⎙ Print Slip** button opens your browser's print dialog with a clean, minimal pairings slip — no app chrome, just the match-ups. In team play mode this prints a full captain's reference sheet (see [Team Play](#team-play)).

---

## Team Play

When **Play Format** is set to Team Play:

- Players are assigned to teams.
- Teams (not individual players) are paired each round.
- The pairing system sorts teams by **Team VP** descending. Higher VP earns the harder matchup. Tiebreaker is aggregate W/L ratio.
- In Round Robin mode, priority is given to teams that haven't faced each other yet.
- Captains receive a printed pairing sheet and assign individual match-ups offline. The app does not record who plays whom within a team pairing — only the individual 1v1 match results.

### Recording Matches in Team Play

Open **+ Record Match** and select the Team Pairing from the dropdown. This filters the player selects to the two teams' rosters, making batch entry after a round straightforward.

### Captain's Pairing Sheet

Click **⎙ Print Slip** on the Pairings tab after generating pairings. Each team pairing prints as a block showing:

- Both team names, alliance, captain, VP total, and W/L
- Side-by-side roster table with each player's W/L and OGW%
- A blank write-in assignment table for captains to fill in match-ups (one row per player on the larger roster, plus one overflow row)

---

## Phase & Crusade Victory

### Phase Victory

At the end of each phase, the alliance with the highest SP total (or SP/Match, if that method is selected) wins the phase. If two or more alliances tie, no alliance wins that phase — it is marked "Tied".

**SP per Match Played** — only cross-alliance matches count toward a team's match count. Intra-alliance matches contribute SP but do not increase the denominator, preventing teams from inflating their ratio through easy internal games.

### Overall Crusade Victory

When all phases are complete, the overall winner is determined by:

1. **Total SP** (or SP/Match) across all phases — highest wins.
2. **Phases won** — tiebreaker if SP totals are equal.
3. **Draw** — if both are tied, the crusade ends in a draw.

---

## Print & Export

Go to **Print / Export** to configure a full campaign document. Check or uncheck sections and click **Print Now** to open the browser print dialog. Choose "Save as PDF" from there to create a PDF file — no extra software needed.

### Available Sections

| Section | Description |
|---|---|
| Cover Page | Crusade name, date, current round and phase |
| Phase Summary | SP standings for every phase with winners |
| Alliance Rosters | Player lists grouped by alliance and team |
| Individual Standings | Full player table with all stats |
| Current Pairings | The currently generated round's pairings |
| Match History | All recorded matches grouped by round |
| Round Scoresheet | Write-in table for every round (see below) |

### Round Scoresheet

A physical tracking sheet covering every round of the crusade. Each round block shows a table with columns for Player 1, Win ☐, VP, SP, SP, VP, Win ☐, Player 2.

- **Completed rounds** — pre-filled with player names, scores, and a checked ☑ for the winner.
- **Current round with pairings set** — player names filled in, result columns blank.
- **Future rounds** — all blank with row numbers.
- **Bye** — occupies the extra row with "Bye: [player name]". If there is no bye, the extra row is a blank overflow row.

In team play mode the scoresheet shows team pairings with the write-in assignment table instead of individual player rows.

---

## Settings

| Setting | Description |
|---|---|
| Crusade Name | Editable at any time |
| Pairing Method | Round Robin or Win Path |
| Allow Rematches | Toggle rematch avoidance |
| Rounds Per Phase | Override the auto-calculated default |
| Number of Phases | Adjustable mid-crusade |
| Phase Victory Method | Raw SP or SP per Match Played |
| Play Format | Individual or Team Play (warns if changed mid-crusade with existing matches) |

### Data Management

- **Export Crusade Data** — downloads a `.json` file of your entire crusade state.
- **Import Crusade Data** — loads a previously exported `.json` file, replacing the current crusade.
- **Reset** — clears all data and returns to the setup screen.

---

## Browser Compatibility

The app uses standard HTML, CSS, and JavaScript with no external dependencies loaded at runtime (fonts are loaded from Google Fonts on first open). It works in any modern browser — Chrome, Firefox, Safari, Edge. Internet Explorer is not supported.

Local storage is used for persistence. Private/incognito browsing sessions will not retain data between browser restarts. For permanent storage, export your data regularly.

---

## Contributing

Issues and pull requests welcome. The entire app lives in a single HTML file — no build step, no dependencies, no framework. Just open it and edit.

---

*Not affiliated with Games Workshop. Warhammer 40,000 is a trademark of Games Workshop Ltd. This tool is a fan-made utility for personal use.*
