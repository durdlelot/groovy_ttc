# TableTopCaps (TTC)

A Total War: WARHAMMER III mod by **Drunk Flamingo** that brings tabletop-style
recruitment caps to campaign armies. Units are sorted into **Core**, **Special**,
and **Rare** categories, each with a points budget per army — mirroring how army
composition works in the Warhammer tabletop game, rather than the vanilla
unlimited-recruitment model.

## Features

- Every unit in the game (vanilla and DLC) is assigned a category (Core / Special
  / Rare) and, for Special/Rare units, a per-army cap.
- Caps are enforced for both the player and the AI (toggleable).
- Unit cards display their category and point cost.
- Points budgets (Special/Rare) are adjustable via MCT (Mod Configuration Tool).
- Integrates with the campaign's warband unit-upgrade panel, showing the TTC
  point cost of upgrading a unit and locking the option if it can't be afforded.
- Faction/subculture-specific special rules (e.g. Katarin can recruit Snow
  Leopards as Core, Lord Skrolk can recruit Plague Monks as Core).
- AI factions that would otherwise exceed their caps get their disallowed
  units swapped for suitable replacements, defined per subculture.

## Requirements

- [Mod Configuration Tool (MCT)](https://steamcommunity.com/sharedfiles/filedetails/?id=2857203103)

## Installation / Development

This repository is laid out as an [RPFM](https://github.com/Frodo45127/rpfm)
project (loose `db`/`script`/`text`/`ui` source rather than a compiled `.pack`).
To test changes in-game:

1. Open this folder in RPFM as a PackFile project.
2. Save/export a `.pack` file into your game's `data/` folder.
3. Enable it in the in-game mod manager alongside MCT.

## Version history

### 1.1.0 — Lord of the End Times support
- Added unit caps for the ~60 new recruitable units introduced by the *Lord of
  the End Times* DLC (`wh3_dlc29`) across Vampire Counts, Tomb Kings, Skaven,
  Warriors of Chaos, Beastmen, and Empire.
- Registered the new `Host of Nagash` (Undead Legions) subculture, with a
  default AI replacement-unit list drawn from the Vampire Counts/Tomb
  Kings/Skaven pools it recruits from.

### 1.0.0 — Baseline
- Existing caps coverage for WH1/WH2/WH3 vanilla units through DLC27, plus
  errata fixes for missing vanilla units.
