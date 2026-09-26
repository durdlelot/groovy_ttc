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

None. Mod Configuration Tool (MCT) is optional. If it's installed, it adds
settings for the Special/Rare point budgets and the AI toggle.

## Building the pack

This repository is an [RPFM](https://github.com/Frodo45127/rpfm) MyMod project:
loose `db`/`script`/`text`/`ui` source instead of a compiled `.pack`. The
`db` and `text` folders are stored as `.tsv`, and the game can't read TSV.
They have to be converted to binary tables when the pack is built.

- **Don't** use RPFM's plain "Add Folder" on this repo. It copies the `.tsv`
  files in unconverted. The pack will load, but none of the DB tables or text
  will, and the mod does nothing.
- **Do** build it through RPFM's MyMod feature. Put this repo in your MyMods
  folder, open it as a MyMod, and use MyMod → Import. That converts the TSVs to
  binary. `settings.rpfm_reserved.json` sets which files the import skips.
- **Quick test when only Lua changed:** open the released `.pack` in RPFM,
  replace the changed `script/` file(s), and save it as a new pack.

To test, save the pack into the game's `data/` folder, disable the Workshop
version of TTC, and enable the local pack in the mod manager. TTC runs in
campaigns only. Custom Battle is never capped.

## Version history

### 1.1.0 — Lords of the End Times support, missing units sweep
- Added unit caps for the ~60 new recruitable units introduced by the *Lord of
  the End Times* DLC (`wh3_dlc29`) across Vampire Counts, Tomb Kings, Skaven,
  Warriors of Chaos, Chaos Dwarfs, Beastmen, and Empire.
- Registered the new `Host of Nagash` (Undead Legions) subculture, with a
  default AI replacement-unit list drawn from the Vampire Counts/Tomb
  Kings/Skaven pools it recruits from.
- Added Bhashiva's Cathay units (`wh3_cp1`).
- Added DLC27 units that were missing, mainly the Monstrous Arcanum variants,
  using the same caps as their base units.
- Added older units that were missing (legacy Tomb Kings undead, Tlaqua
  Terradons, Forest Dragon, and others). Every recruitable unit in the game now
  has a cap entry, except prologue, quest-battle, and multiplayer-only units.

### 1.0.0 — Baseline
- Existing caps coverage for WH1/WH2/WH3 vanilla units through DLC27, plus
  errata fixes for missing vanilla units.
