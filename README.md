# TableTopCaps (TTC)

A Total War: WARHAMMER III mod by **Drunk Flamingo** that brings tabletop-style
army composition to the campaign. Every unit is Core, Special, or Rare, and
each army has a points budget for its Special and Rare units.

## How it works

- **Core** units are unlimited.
- **Special** and **Rare** units each have a cost from 1 to 3. By default an
  army has 10 Special points and 5 Rare points. A unit can't be recruited if
  its cost would take the army over budget.
- Unit cards show each unit's category and cost. Caps apply to the player and,
  optionally, the AI. AI armies that would go over budget swap the extra units
  for Core units from their own roster.
- The campaign's unit-upgrade panel shows the TTC cost of an upgrade and blocks
  upgrades you can't afford.
- A few lords can recruit specific units as Core:
  - Lord Skrolk: Plague Monks
  - Drazhoath the Ashen: all three Infernal Guard units
- TTC only applies in campaigns. Custom Battle is never capped.

## Requirements

None. Mod Configuration Tool (MCT) is optional. If it's installed, it adds
settings for the Special/Rare budgets and whether the AI follows the caps.

## Building the pack

This repository is an [RPFM](https://github.com/Frodo45127/rpfm) MyMod project:
loose `db`/`script`/`text`/`ui` source instead of a compiled `.pack`. The `db`
and `text` folders are stored as `.tsv`, which the game can't read, so they
have to be converted to binary tables when the pack is built.

- **Don't** use RPFM's plain "Add Folder" on this repo. It copies the `.tsv`
  files in unconverted. The pack will load, but none of the DB tables or text
  will, and the mod does nothing.
- **Do** build it through RPFM's MyMod feature. Put this repo in your MyMods
  folder, open it as a MyMod, and use MyMod → Import. That converts the TSVs to
  binary. `settings.rpfm_reserved.json` sets which files the import skips.
- **Quick test when only Lua changed:** open the released `.pack` in RPFM,
  replace the changed `script/` file(s), and save it as a new pack.

To test, save the pack into the game's `data/` folder, disable the Workshop
version of TTC, and enable the local pack in the mod manager.

## Version history

### 1.1.0
- Added Lords of the End Times (`wh3_dlc29`) units and the new Host of Nagash
  subculture.
- Added Bhashiva's units (`wh3_cp1`).
- Added every other recruitable unit that was missing, mainly DLC27's
  Monstrous Arcanum variants. Prologue, quest-battle, and multiplayer-only
  units aren't included.

### 1.0.0
- Units through DLC27, plus errata for missed vanilla units.

## Unit table

Every unit TTC knows about, with its category and cost. Units not in this table
are treated as Core. The table is generated from
`script/ttc/ttc_vanilla_units.lua`, which is the source of truth.

| Faction | Unit key | Category | Cost |
|---|---|---|---|
| Beastmen | `wh2_dlc17_bst_cav_tuskgor_chariot_0` | Core | - |
| Beastmen | `wh_dlc03_bst_inf_chaos_warhounds_0` | Core | - |
| Beastmen | `wh_dlc03_bst_inf_chaos_warhounds_1` | Core | - |
| Beastmen | `wh_dlc03_bst_inf_gor_herd_0` | Core | - |
| Beastmen | `wh_dlc03_bst_inf_gor_herd_1` | Core | - |
| Beastmen | `wh_dlc03_bst_inf_ungor_herd_1` | Core | - |
| Beastmen | `wh_dlc03_bst_inf_ungor_raiders_0` | Core | - |
| Beastmen | `wh_dlc03_bst_inf_ungor_spearmen_0` | Core | - |
| Beastmen | `wh_dlc03_bst_inf_ungor_spearmen_1` | Core | - |
| Beastmen | `wh_pro04_bst_inf_gor_herd_ror_0` | Core | - |
| Beastmen | `wh_pro04_bst_inf_ungor_spearmen_ror_0` | Core | - |
| Beastmen | `wh2_dlc17_bst_inf_centigors_ror_1` | Special | 1 |
| Beastmen | `wh3_dlc24_bst_inf_tzaangors` | Special | 1 |
| Beastmen | `wh3_dlc25_bst_inf_pestigors` | Special | 1 |
| Beastmen | `wh3_dlc26_bst_inf_khorngors` | Special | 1 |
| Beastmen | `wh3_dlc27_bst_inf_slaangors` | Special | 1 |
| Beastmen | `wh_dlc03_bst_inf_bestigor_herd_0` | Special | 1 |
| Beastmen | `wh_dlc03_bst_inf_centigors_0` | Special | 1 |
| Beastmen | `wh_dlc03_bst_inf_centigors_1` | Special | 1 |
| Beastmen | `wh_dlc03_bst_inf_centigors_2` | Special | 1 |
| Beastmen | `wh_dlc03_bst_inf_razorgor_herd_0` | Special | 1 |
| Beastmen | `wh_dlc05_bst_mon_harpies_0` | Special | 1 |
| Beastmen | `wh_pro04_bst_inf_bestigor_herd_ror_0` | Special | 1 |
| Beastmen | `wh_pro04_bst_inf_centigors_ror_0` | Special | 1 |
| Beastmen | `wh_dlc03_bst_cav_razorgor_chariot_0` | Special | 2 |
| Beastmen | `wh_dlc03_bst_feral_manticore` | Special | 2 |
| Beastmen | `wh_dlc03_bst_inf_minotaurs_0` | Special | 2 |
| Beastmen | `wh_dlc03_bst_inf_minotaurs_1` | Special | 2 |
| Beastmen | `wh_dlc03_bst_inf_minotaurs_2` | Special | 2 |
| Beastmen | `wh_pro04_bst_inf_minotaurs_ror_0` | Special | 2 |
| Beastmen | `wh3_dlc24_bst_inf_centigors_great_weapons_mtze` | Rare | 1 |
| Beastmen | `wh_dlc03_bst_mon_chaos_spawn_0` | Rare | 1 |
| Beastmen | `wh3_dlc24_bst_mon_cockatrice` | Rare | 2 |
| Beastmen | `wh3_dlc27_bst_mon_chimera` | Rare | 2 |
| Beastmen | `wh3_dlc27_bst_mon_chimera_ror` | Rare | 2 |
| Beastmen | `wh3_dlc27_bst_mon_cockatrice` | Rare | 2 |
| Beastmen | `wh3_dlc27_bst_mon_preyton` | Rare | 2 |
| Beastmen | `wh3_dlc27_bst_mon_preyton_ror` | Rare | 2 |
| Beastmen | `wh3_dlc29_bst_mon_basilisk` | Rare | 2 |
| Beastmen | `wh3_dlc29_bst_mon_giant_spined_chaos_beast` | Rare | 2 |
| Beastmen | `wh3_dlc29_bst_mon_giant_spined_chaos_beast_ror` | Rare | 2 |
| Beastmen | `wh_dlc03_bst_mon_giant_0` | Rare | 2 |
| Beastmen | `wh2_dlc17_bst_mon_ghorgon_0` | Rare | 3 |
| Beastmen | `wh2_dlc17_bst_mon_ghorgon_ror_0` | Rare | 3 |
| Beastmen | `wh2_dlc17_bst_mon_jabberslythe_0` | Rare | 3 |
| Beastmen | `wh2_dlc17_bst_mon_jabberslythe_ror_0` | Rare | 3 |
| Beastmen | `wh3_dlc24_bst_mon_incarnate_elemental_of_beasts` | Rare | 3 |
| Beastmen | `wh3_dlc27_bst_inf_cygor_monst_arcanum_reward` | Rare | 3 |
| Beastmen | `wh3_dlc27_bst_mon_ghorgon_monst_arcanum` | Rare | 3 |
| Beastmen | `wh3_dlc27_bst_mon_ghorgon_monst_arcanum_reward` | Rare | 3 |
| Beastmen | `wh3_dlc27_bst_mon_jabberslythe_monst_arcanum` | Rare | 3 |
| Beastmen | `wh3_dlc27_bst_mon_jabberslythe_monst_arcanum_reward` | Rare | 3 |
| Beastmen | `wh_dlc03_bst_inf_cygor_0` | Rare | 3 |
| Beastmen | `wh_pro04_bst_inf_cygor_ror_0` | Rare | 3 |
| Bretonnia | `wh_dlc07_brt_cav_knights_errant_0` | Core | - |
| Bretonnia | `wh_dlc07_brt_inf_men_at_arms_1` | Core | - |
| Bretonnia | `wh_dlc07_brt_inf_men_at_arms_2` | Core | - |
| Bretonnia | `wh_dlc07_brt_inf_peasant_bowmen_1` | Core | - |
| Bretonnia | `wh_dlc07_brt_inf_peasant_bowmen_2` | Core | - |
| Bretonnia | `wh_dlc07_brt_inf_spearmen_at_arms_1` | Core | - |
| Bretonnia | `wh_dlc07_brt_peasant_mob_0` | Core | - |
| Bretonnia | `wh_main_brt_cav_knights_of_the_realm` | Core | - |
| Bretonnia | `wh_main_brt_cav_mounted_yeomen_0` | Core | - |
| Bretonnia | `wh_main_brt_cav_mounted_yeomen_1` | Core | - |
| Bretonnia | `wh_main_brt_inf_men_at_arms` | Core | - |
| Bretonnia | `wh_main_brt_inf_peasant_bowmen` | Core | - |
| Bretonnia | `wh_main_brt_inf_spearmen_at_arms` | Core | - |
| Bretonnia | `wh_pro04_brt_cav_knights_errant_ror_0` | Core | - |
| Bretonnia | `wh_pro04_brt_cav_knights_of_the_realm_ror_0` | Core | - |
| Bretonnia | `wh_pro04_brt_cav_mounted_yeomen_ror_0` | Core | - |
| Bretonnia | `wh_dlc07_brt_inf_battle_pilgrims_0` | Special | 1 |
| Bretonnia | `wh_dlc07_brt_inf_foot_squires_0` | Special | 1 |
| Bretonnia | `wh_pro04_brt_inf_battle_pilgrims_ror_0` | Special | 1 |
| Bretonnia | `wh_pro04_brt_inf_foot_squires_ror_0` | Special | 1 |
| Bretonnia | `wh_dlc07_brt_cav_questing_knights_0` | Special | 2 |
| Bretonnia | `wh_dlc07_brt_inf_grail_reliquae_0` | Special | 2 |
| Bretonnia | `wh_main_brt_cav_pegasus_knights` | Special | 2 |
| Bretonnia | `wh_pro04_brt_cav_questing_knights_ror_0` | Special | 2 |
| Bretonnia | `wh_main_brt_art_field_trebuchet` | Rare | 1 |
| Bretonnia | `wh_dlc07_brt_art_blessed_field_trebuchet_0` | Rare | 2 |
| Bretonnia | `wh_dlc07_brt_cav_grail_guardians_0` | Rare | 2 |
| Bretonnia | `wh_dlc07_brt_cav_royal_hippogryph_knights_0` | Rare | 2 |
| Bretonnia | `wh_dlc07_brt_cav_royal_pegasus_knights_0` | Rare | 2 |
| Bretonnia | `wh_main_brt_cav_grail_knights` | Rare | 2 |
| Cathay | `wh3_main_cth_cav_peasant_horsemen_0` | Core | - |
| Cathay | `wh3_main_cth_inf_grenadiers` | Core | - |
| Cathay | `wh3_main_cth_inf_iron_hail_gunners_0` | Core | - |
| Cathay | `wh3_main_cth_inf_jade_warrior_crossbowmen_0` | Core | - |
| Cathay | `wh3_main_cth_inf_jade_warrior_crossbowmen_1` | Core | - |
| Cathay | `wh3_main_cth_inf_jade_warriors_0` | Core | - |
| Cathay | `wh3_main_cth_inf_jade_warriors_1` | Core | - |
| Cathay | `wh3_main_cth_inf_peasant_archers_0` | Core | - |
| Cathay | `wh3_main_cth_inf_peasant_spearmen_1` | Core | - |
| Cathay | `wh3_twa10_cth_inf_peasant_archers_ror` | Core | - |
| Cathay | `wh3_cp1_cth_inf_tiger_warriors_dual_axe` | Special | 1 |
| Cathay | `wh3_dlc24_cth_inf_onyx_crowmen` | Special | 1 |
| Cathay | `wh3_dlc24_cth_inf_onyx_crowmen_ror` | Special | 1 |
| Cathay | `wh3_main_cth_cav_jade_lancers_0` | Special | 1 |
| Cathay | `wh3_main_cth_veh_sky_lantern_0` | Special | 1 |
| Cathay | `wh3_cp1_cth_inf_stalkers_throwing_disc` | Special | 2 |
| Cathay | `wh3_main_cth_art_grand_cannon_0` | Special | 2 |
| Cathay | `wh3_main_cth_inf_crane_gunners_0` | Special | 2 |
| Cathay | `wh3_cp1_cth_inf_iron_claw_guandao` | Special | 3 |
| Cathay | `wh3_dlc24_cth_mon_great_moon_bird` | Special | 3 |
| Cathay | `wh3_dlc24_cth_mon_jade_lion` | Special | 3 |
| Cathay | `wh3_dlc24_cth_mon_jet_lion` | Special | 3 |
| Cathay | `wh3_main_cth_veh_sky_junk_0` | Special | 3 |
| Cathay | `wh3_dlc24_cth_inf_dragon_guard_crossbowmen_ror` | Rare | 1 |
| Cathay | `wh3_main_cth_inf_dragon_guard_0` | Rare | 1 |
| Cathay | `wh3_main_cth_inf_dragon_guard_crossbowmen_0` | Rare | 1 |
| Cathay | `wh3_main_cth_veh_war_compass_0` | Rare | 1 |
| Cathay | `wh3_twa06_cth_inf_dragon_guard_ror_0` | Rare | 1 |
| Cathay | `wh3_dlc24_cth_mon_celestial_lion` | Rare | 2 |
| Cathay | `wh3_dlc24_cth_veh_zhangu_war_drum` | Rare | 2 |
| Cathay | `wh3_dlc24_cth_veh_zhangu_war_drum_ror` | Rare | 2 |
| Cathay | `wh3_dlc27_cth_mon_celestial_lion_monst_arcanum` | Rare | 2 |
| Cathay | `wh3_main_cth_art_fire_rain_rocket_battery_0` | Rare | 2 |
| Cathay | `wh3_main_cth_cav_jade_longma_riders_0` | Rare | 2 |
| Cathay | `wh3_twa07_cth_cav_jade_longma_riders_ror_0` | Rare | 2 |
| Cathay | `wh3_main_cth_mon_terracotta_sentinel_0` | Rare | 3 |
| Cathay | `wh3_twa08_cth_mon_terracotta_sentinel_0_ror` | Rare | 3 |
| Chaos Dwarfs | `wh3_dlc23_chd_inf_chaos_dwarf_blunderbusses` | Core | - |
| Chaos Dwarfs | `wh3_dlc23_chd_inf_chaos_dwarf_blunderbusses_ror` | Core | - |
| Chaos Dwarfs | `wh3_dlc23_chd_inf_chaos_dwarf_warriors` | Core | - |
| Chaos Dwarfs | `wh3_dlc23_chd_inf_chaos_dwarf_warriors_great_weapons` | Core | - |
| Chaos Dwarfs | `wh3_dlc23_chd_inf_chaos_dwarf_warriors_ror` | Core | - |
| Chaos Dwarfs | `wh3_dlc23_chd_inf_goblin_labourers` | Core | - |
| Chaos Dwarfs | `wh3_dlc23_chd_inf_hobgoblin_archers` | Core | - |
| Chaos Dwarfs | `wh3_dlc23_chd_inf_hobgoblin_cutthroats` | Core | - |
| Chaos Dwarfs | `wh3_dlc23_chd_inf_orc_labourers` | Core | - |
| Chaos Dwarfs | `wh3_dlc23_chd_inf_hobgoblin_sneaky_gits` | Special | 1 |
| Chaos Dwarfs | `wh3_dlc23_chd_inf_infernal_guard` | Special | 1 |
| Chaos Dwarfs | `wh3_dlc23_chd_inf_infernal_guard_fireglaives` | Special | 1 |
| Chaos Dwarfs | `wh3_dlc23_chd_inf_infernal_guard_great_weapons` | Special | 1 |
| Chaos Dwarfs | `wh3_dlc23_chd_cav_bull_centaurs_axe` | Special | 2 |
| Chaos Dwarfs | `wh3_dlc23_chd_cav_bull_centaurs_dual_axe` | Special | 2 |
| Chaos Dwarfs | `wh3_dlc23_chd_cav_bull_centaurs_dual_axe_ror` | Special | 2 |
| Chaos Dwarfs | `wh3_dlc23_chd_cav_bull_centaurs_greatweapons` | Special | 2 |
| Chaos Dwarfs | `wh3_dlc23_chd_inf_infernal_ironsworn` | Special | 2 |
| Chaos Dwarfs | `wh3_dlc23_chd_inf_infernal_ironsworn_ror` | Special | 2 |
| Chaos Dwarfs | `wh3_dlc23_chd_mon_kdaai_fireborn` | Special | 2 |
| Chaos Dwarfs | `wh3_dlc23_chd_veh_deathshrieker_rocket_launcher` | Special | 2 |
| Chaos Dwarfs | `wh3_dlc23_chd_veh_iron_daemon` | Special | 2 |
| Chaos Dwarfs | `wh3_dlc23_chd_veh_iron_daemon_ror` | Special | 2 |
| Chaos Dwarfs | `wh3_dlc23_chd_veh_magma_cannon` | Special | 2 |
| Chaos Dwarfs | `wh3_dlc23_chd_veh_skullcracker` | Special | 2 |
| Chaos Dwarfs | `wh3_main_chd_art_hobgob_bolt_thrower` | Special | 2 |
| Chaos Dwarfs | `wh3_dlc23_chd_cav_hobgoblin_wolf_raiders_bows` | Rare | 1 |
| Chaos Dwarfs | `wh3_dlc23_chd_cav_hobgoblin_wolf_raiders_ror` | Rare | 1 |
| Chaos Dwarfs | `wh3_dlc23_chd_cav_hobgoblin_wolf_raiders_spears` | Rare | 1 |
| Chaos Dwarfs | `wh3_dlc23_chd_mon_great_taurus` | Rare | 1 |
| Chaos Dwarfs | `wh3_dlc23_chd_mon_bale_taurus` | Rare | 2 |
| Chaos Dwarfs | `wh3_dlc23_chd_mon_lammasu` | Rare | 2 |
| Chaos Dwarfs | `wh3_dlc27_chd_mon_bale_taurus_monst_arcanum` | Rare | 2 |
| Chaos Dwarfs | `wh3_dlc27_chd_mon_lammasu_monst_arcanum` | Rare | 2 |
| Chaos Dwarfs | `wh3_dlc23_chd_mon_kdaai_destroyer` | Rare | 3 |
| Chaos Dwarfs | `wh3_dlc23_chd_veh_dreadquake_mortar` | Rare | 3 |
| Chaos Dwarfs | `wh3_dlc23_chd_veh_iron_daemon_1dreadquake` | Rare | 3 |
| Chaos Dwarfs | `wh3_dlc23_chd_veh_iron_daemon_ror_1dreadquake` | Rare | 3 |
| Chaos Dwarfs | `wh3_dlc23_chd_veh_skullcracker_1dreadquake` | Rare | 3 |
| Chaos Dwarfs | `wh3_dlc29_chd_mon_chaos_siege_giant` | Rare | 3 |
| Daemons of Chaos | `wh3_main_dae_inf_chaos_furies_0` | Special | 1 |
| Dark Elves | `wh2_dlc10_def_cav_raven_heralds_ror_0` | Core | - |
| Dark Elves | `wh2_dlc10_def_inf_sisters_of_the_singing_doom_ror_0` | Core | - |
| Dark Elves | `wh2_dlc10_def_inf_the_bolt_fiends_ror_0` | Core | - |
| Dark Elves | `wh2_dlc10_def_inf_the_hellebronai_ror_0` | Core | - |
| Dark Elves | `wh2_dlc14_def_inf_harpies_ror_0` | Core | - |
| Dark Elves | `wh2_main_def_cav_dark_riders_0` | Core | - |
| Dark Elves | `wh2_main_def_cav_dark_riders_1` | Core | - |
| Dark Elves | `wh2_main_def_cav_dark_riders_2` | Core | - |
| Dark Elves | `wh2_main_def_inf_black_ark_corsairs_0` | Core | - |
| Dark Elves | `wh2_main_def_inf_black_ark_corsairs_1` | Core | - |
| Dark Elves | `wh2_main_def_inf_bleakswords_0` | Core | - |
| Dark Elves | `wh2_main_def_inf_darkshards_0` | Core | - |
| Dark Elves | `wh2_main_def_inf_darkshards_1` | Core | - |
| Dark Elves | `wh2_main_def_inf_dreadspears_0` | Core | - |
| Dark Elves | `wh2_main_def_inf_witch_elves_0` | Core | - |
| Dark Elves | `wh_twa03_def_inf_squig_explosive_0` | Core | - |
| Dark Elves | `wh2_main_def_cav_cold_one_knights_0` | Special | 1 |
| Dark Elves | `wh2_main_def_inf_harpies` | Special | 1 |
| Dark Elves | `wh2_main_def_inf_shades_0` | Special | 1 |
| Dark Elves | `wh2_twa03_def_mon_wolves_0` | Special | 1 |
| Dark Elves | `wh2_dlc10_def_cav_doomfire_warlocks_0` | Special | 2 |
| Dark Elves | `wh2_dlc10_def_cav_knights_of_the_ebon_claw_ror_0` | Special | 2 |
| Dark Elves | `wh2_dlc10_def_cav_slaanesh_harvesters_ror_0` | Special | 2 |
| Dark Elves | `wh2_dlc10_def_inf_blades_of_the_blood_queen_ror_0` | Special | 2 |
| Dark Elves | `wh2_dlc10_def_mon_feral_manticore_0` | Special | 2 |
| Dark Elves | `wh2_dlc14_def_cav_scourgerunner_chariot_0` | Special | 2 |
| Dark Elves | `wh2_dlc14_def_cav_scourgerunner_chariot_ror_0` | Special | 2 |
| Dark Elves | `wh2_main_def_cav_cold_one_chariot` | Special | 2 |
| Dark Elves | `wh2_main_def_cav_cold_one_knights_1` | Special | 2 |
| Dark Elves | `wh2_main_def_inf_black_guard_0` | Special | 2 |
| Dark Elves | `wh2_main_def_inf_har_ganeth_executioners_0` | Special | 2 |
| Dark Elves | `wh2_main_def_inf_shades_1` | Special | 2 |
| Dark Elves | `wh2_main_def_inf_shades_2` | Special | 2 |
| Dark Elves | `wh2_dlc10_def_inf_sisters_of_slaughter` | Rare | 1 |
| Dark Elves | `wh2_dlc14_def_mon_bloodwrack_medusa_0` | Rare | 1 |
| Dark Elves | `wh2_main_def_art_reaper_bolt_thrower` | Rare | 1 |
| Dark Elves | `wh2_dlc10_def_mon_chill_of_sontar_ror_0` | Rare | 2 |
| Dark Elves | `wh2_dlc10_def_mon_kharibdyss_0` | Rare | 2 |
| Dark Elves | `wh2_dlc14_def_mon_bloodwrack_medusa_ror_0` | Rare | 2 |
| Dark Elves | `wh2_dlc14_def_veh_bloodwrack_shrine_0` | Rare | 2 |
| Dark Elves | `wh2_main_def_mon_war_hydra` | Rare | 2 |
| Dark Elves | `wh2_twa03_def_mon_war_mammoth_0` | Rare | 2 |
| Dark Elves | `wh2_main_def_mon_black_dragon` | Rare | 3 |
| Dark Elves | `wh3_dlc27_def_mon_black_dragon_monst_arcanum` | Rare | 3 |
| Dwarfs | `wh3_dlc25_dwf_inf_thunderers_ror` | Core | - |
| Dwarfs | `wh_dlc06_dwf_inf_ekrund_miners_0` | Core | - |
| Dwarfs | `wh_dlc06_dwf_inf_old_grumblers_0` | Core | - |
| Dwarfs | `wh_dlc06_dwf_inf_warriors_dragonfire_pass_0` | Core | - |
| Dwarfs | `wh_main_dwf_inf_dwarf_warrior_0` | Core | - |
| Dwarfs | `wh_main_dwf_inf_dwarf_warrior_1` | Core | - |
| Dwarfs | `wh_main_dwf_inf_longbeards` | Core | - |
| Dwarfs | `wh_main_dwf_inf_longbeards_1` | Core | - |
| Dwarfs | `wh_main_dwf_inf_longbeards_1_grudge_reward` | Core | - |
| Dwarfs | `wh_main_dwf_inf_miners_0` | Core | - |
| Dwarfs | `wh_main_dwf_inf_miners_1` | Core | - |
| Dwarfs | `wh_main_dwf_inf_quarrellers_0` | Core | - |
| Dwarfs | `wh_main_dwf_inf_quarrellers_1` | Core | - |
| Dwarfs | `wh_main_dwf_inf_quarrellers_1_grudge_reward` | Core | - |
| Dwarfs | `wh_main_dwf_inf_thunderers_0` | Core | - |
| Dwarfs | `wh3_dlc25_dwf_art_grudge_thrower_grudge_reward` | Special | 1 |
| Dwarfs | `wh3_dlc25_dwf_inf_thunderers_grudge_rakers` | Special | 1 |
| Dwarfs | `wh_dlc06_dwf_art_bolt_thrower_0` | Special | 1 |
| Dwarfs | `wh_dlc06_dwf_art_gob_lobber_0` | Special | 1 |
| Dwarfs | `wh_dlc06_dwf_inf_dragonback_slayers_0` | Special | 1 |
| Dwarfs | `wh_dlc06_dwf_inf_rangers_0` | Special | 1 |
| Dwarfs | `wh_dlc06_dwf_inf_rangers_1` | Special | 1 |
| Dwarfs | `wh_dlc06_dwf_inf_ulthars_raiders_0` | Special | 1 |
| Dwarfs | `wh_main_dwf_art_grudge_thrower` | Special | 1 |
| Dwarfs | `wh_main_dwf_inf_slayers` | Special | 1 |
| Dwarfs | `wh_main_dwf_inf_slayers_grudge_reward` | Special | 1 |
| Dwarfs | `wh2_dlc10_dwf_inf_giant_slayers` | Special | 2 |
| Dwarfs | `wh3_dlc25_dwf_inf_doomseekers` | Special | 2 |
| Dwarfs | `wh3_dlc25_dwf_inf_doomseekers_ror` | Special | 2 |
| Dwarfs | `wh_dlc06_dwf_inf_bugmans_rangers_0` | Special | 2 |
| Dwarfs | `wh_dlc06_dwf_inf_norgrimlings_ironbreakers_0` | Special | 2 |
| Dwarfs | `wh_dlc06_dwf_inf_peak_gate_guard_0` | Special | 2 |
| Dwarfs | `wh_dlc06_dwf_veh_skyhammer_0` | Special | 2 |
| Dwarfs | `wh_main_dwf_art_cannon` | Special | 2 |
| Dwarfs | `wh_main_dwf_art_cannon_malakai` | Special | 2 |
| Dwarfs | `wh_main_dwf_inf_hammerers` | Special | 2 |
| Dwarfs | `wh_main_dwf_inf_hammerers_grudge_reward` | Special | 2 |
| Dwarfs | `wh_main_dwf_inf_ironbreakers` | Special | 2 |
| Dwarfs | `wh_main_dwf_veh_gyrobomber` | Special | 2 |
| Dwarfs | `wh_main_dwf_veh_gyrobomber_malakai` | Special | 2 |
| Dwarfs | `wh_main_dwf_veh_gyrocopter_0` | Special | 2 |
| Dwarfs | `wh_main_dwf_veh_gyrocopter_0_malakai` | Special | 2 |
| Dwarfs | `wh_main_dwf_veh_gyrocopter_1` | Special | 2 |
| Dwarfs | `wh_main_dwf_veh_gyrocopter_1_grudge_reward` | Special | 2 |
| Dwarfs | `wh_main_dwf_veh_gyrocopter_1_malakai` | Special | 2 |
| Dwarfs | `wh3_dlc25_dwf_art_goblin_hewer` | Rare | 1 |
| Dwarfs | `wh3_dlc25_dwf_art_goblin_hewer_malakai` | Rare | 1 |
| Dwarfs | `wh3_dlc25_dwf_inf_slayer_pirates` | Rare | 1 |
| Dwarfs | `wh3_dlc25_dwf_inf_slayer_pirates_ror` | Rare | 1 |
| Dwarfs | `wh2_dlc17_dwf_mon_carnosaur_thorek_0` | Rare | 2 |
| Dwarfs | `wh_dlc06_dwf_inf_norgrimlings_irondrakes_0` | Rare | 2 |
| Dwarfs | `wh_main_dwf_art_flame_cannon` | Rare | 2 |
| Dwarfs | `wh_main_dwf_art_flame_cannon_grudge_reward` | Rare | 2 |
| Dwarfs | `wh_main_dwf_art_flame_cannon_malakai` | Rare | 2 |
| Dwarfs | `wh_main_dwf_art_organ_gun` | Rare | 2 |
| Dwarfs | `wh_main_dwf_art_organ_gun_malakai` | Rare | 2 |
| Dwarfs | `wh_main_dwf_inf_irondrakes_0` | Rare | 2 |
| Dwarfs | `wh_main_dwf_inf_irondrakes_0_grudge_reward` | Rare | 2 |
| Dwarfs | `wh_main_dwf_inf_irondrakes_2` | Rare | 2 |
| Dwarfs | `wh3_dlc25_dwf_veh_thunderbarge` | Rare | 3 |
| Dwarfs | `wh3_dlc25_dwf_veh_thunderbarge_grungni` | Rare | 3 |
| Dwarfs | `wh3_dlc25_dwf_veh_thunderbarge_malakai` | Rare | 3 |
| Empire | `wh2_dlc13_emp_inf_archers_0` | Core | - |
| Empire | `wh2_dlc13_emp_inf_archers_ror_0` | Core | - |
| Empire | `wh2_dlc13_emp_inf_crossbowmen_ror_0` | Core | - |
| Empire | `wh2_dlc13_emp_inf_halberdiers_imperial_supply` | Core | - |
| Empire | `wh2_dlc13_emp_inf_halberdiers_ror_0` | Core | - |
| Empire | `wh2_dlc13_emp_inf_handgunners_imperial_supply` | Core | - |
| Empire | `wh2_dlc13_emp_inf_handgunners_ror_0` | Core | - |
| Empire | `wh2_dlc13_emp_inf_spearmen_ror_0` | Core | - |
| Empire | `wh2_dlc13_emp_inf_swordsmen_ror_0` | Core | - |
| Empire | `wh2_dlc17_emp_inf_prisoners_0` | Core | - |
| Empire | `wh3_dlc25_emp_inf_spearmen_shields_ror` | Core | - |
| Empire | `wh3_dlc29_emp_inf_hunting_hounds` | Core | - |
| Empire | `wh3_dlc29_emp_inf_hunting_hounds_ror` | Core | - |
| Empire | `wh3_dlc29_emp_inf_warriors_of_ulric` | Core | - |
| Empire | `wh3_dlc29_emp_inf_wolf_kin` | Core | - |
| Empire | `wh_dlc04_emp_inf_free_company_militia_0` | Core | - |
| Empire | `wh_dlc04_emp_inf_sigmars_sons_0` | Core | - |
| Empire | `wh_dlc04_emp_inf_silver_bullets_0` | Core | - |
| Empire | `wh_dlc04_emp_inf_stirlands_revenge_0` | Core | - |
| Empire | `wh_main_emp_cav_empire_knights` | Core | - |
| Empire | `wh_main_emp_inf_crossbowmen` | Core | - |
| Empire | `wh_main_emp_inf_halberdiers` | Core | - |
| Empire | `wh_main_emp_inf_handgunners` | Core | - |
| Empire | `wh_main_emp_inf_spearmen_0` | Core | - |
| Empire | `wh_main_emp_inf_spearmen_1` | Core | - |
| Empire | `wh_main_emp_inf_swordsmen` | Core | - |
| Empire | `wh2_dlc13_emp_art_mortar_ror_0` | Special | 1 |
| Empire | `wh2_dlc13_emp_cav_empire_knights_imperial_supply` | Special | 1 |
| Empire | `wh2_dlc13_emp_cav_empire_knights_ror_0` | Special | 1 |
| Empire | `wh2_dlc13_emp_cav_empire_knights_ror_1` | Special | 1 |
| Empire | `wh2_dlc13_emp_cav_empire_knights_ror_2` | Special | 1 |
| Empire | `wh2_dlc13_emp_cav_outriders_1_imperial_supply` | Special | 1 |
| Empire | `wh2_dlc13_emp_cav_pistoliers_1_imperial_supply` | Special | 1 |
| Empire | `wh2_dlc13_emp_cav_pistoliers_ror_0` | Special | 1 |
| Empire | `wh2_dlc13_emp_inf_greatswords_imperial_supply` | Special | 1 |
| Empire | `wh2_dlc13_emp_inf_greatswords_ror_0` | Special | 1 |
| Empire | `wh2_dlc13_emp_inf_huntsmen_0` | Special | 1 |
| Empire | `wh2_dlc13_emp_inf_huntsmen_0_imperial_supply` | Special | 1 |
| Empire | `wh2_dlc13_emp_inf_huntsmen_ror_0` | Special | 1 |
| Empire | `wh3_dlc25_emp_inf_hochland_long_rifles` | Special | 1 |
| Empire | `wh3_dlc25_emp_inf_hochland_long_rifles_ror` | Special | 1 |
| Empire | `wh3_dlc25_emp_inf_nuln_ironsides` | Special | 1 |
| Empire | `wh_dlc04_emp_inf_flagellants_0` | Special | 1 |
| Empire | `wh_dlc04_emp_inf_tattersouls_0` | Special | 1 |
| Empire | `wh_main_emp_cav_outriders_0` | Special | 1 |
| Empire | `wh_main_emp_cav_pistoliers_1` | Special | 1 |
| Empire | `wh_main_emp_inf_greatswords` | Special | 1 |
| Empire | `wh2_dlc13_emp_art_great_cannon_imperial_supply` | Special | 2 |
| Empire | `wh2_dlc13_emp_cav_knights_blazing_sun_0_imperial_supply` | Special | 2 |
| Empire | `wh2_dlc13_emp_cav_outriders_ror_0` | Special | 2 |
| Empire | `wh2_dlc13_emp_cav_reiksguard_imperial_supply` | Special | 2 |
| Empire | `wh2_dlc13_huntmarshall_veh_obsinite_gyrocopter_0` | Special | 2 |
| Empire | `wh3_dlc25_emp_cav_knights_of_the_black_rose` | Special | 2 |
| Empire | `wh3_dlc25_emp_cav_outriders_morr` | Special | 2 |
| Empire | `wh3_dlc25_emp_inf_nuln_ironsides_morr` | Special | 2 |
| Empire | `wh3_dlc29_emp_cav_knights_of_the_white_wolf` | Special | 2 |
| Empire | `wh3_dlc29_emp_cav_knights_of_the_white_wolf_ror` | Special | 2 |
| Empire | `wh3_dlc29_emp_cav_knights_panther` | Special | 2 |
| Empire | `wh3_dlc29_emp_inf_teutogen_guard` | Special | 2 |
| Empire | `wh3_dlc29_emp_inf_teutogen_guard_ror` | Special | 2 |
| Empire | `wh_dlc04_emp_art_hammer_of_the_witches_0` | Special | 2 |
| Empire | `wh_dlc04_emp_cav_knights_blazing_sun_0` | Special | 2 |
| Empire | `wh_dlc04_emp_cav_zintlers_reiksguard_0` | Special | 2 |
| Empire | `wh_main_emp_art_great_cannon` | Special | 2 |
| Empire | `wh_main_emp_art_mortar` | Special | 2 |
| Empire | `wh_main_emp_cav_outriders_1` | Special | 2 |
| Empire | `wh_main_emp_cav_reiksguard` | Special | 2 |
| Empire | `wh2_dlc13_emp_cav_demigryph_knights_0_imperial_supply` | Special | 3 |
| Empire | `wh2_dlc13_emp_cav_demigryph_knights_1_imperial_supply` | Special | 3 |
| Empire | `wh_dlc04_emp_cav_royal_altdorf_gryphites_0` | Special | 3 |
| Empire | `wh_main_emp_cav_demigryph_knights_0` | Special | 3 |
| Empire | `wh_main_emp_cav_demigryph_knights_1` | Special | 3 |
| Empire | `wh2_dlc13_emp_veh_war_wagon_0` | Rare | 1 |
| Empire | `wh2_dlc13_emp_veh_war_wagon_0_imperial_supply` | Rare | 1 |
| Empire | `wh2_dlc13_emp_art_helblaster_volley_gun_imperial_supply` | Rare | 2 |
| Empire | `wh2_dlc13_emp_art_helstorm_rocket_battery_imperial_supply` | Rare | 2 |
| Empire | `wh2_dlc13_emp_veh_war_wagon_1` | Rare | 2 |
| Empire | `wh2_dlc13_emp_veh_war_wagon_1_imperial_supply` | Rare | 2 |
| Empire | `wh2_dlc13_emp_veh_war_wagon_ror_0` | Rare | 2 |
| Empire | `wh3_dlc25_emp_art_helstorm_rocket_battery_morr` | Rare | 2 |
| Empire | `wh3_dlc25_emp_veh_marienburg_land_ship` | Rare | 2 |
| Empire | `wh3_dlc25_emp_veh_marienburg_land_ship_morr` | Rare | 2 |
| Empire | `wh3_dlc25_emp_veh_marienburg_land_ship_ror` | Rare | 2 |
| Empire | `wh_dlc04_emp_art_sunmaker_0` | Rare | 2 |
| Empire | `wh_main_emp_art_helblaster_volley_gun` | Rare | 2 |
| Empire | `wh_main_emp_art_helstorm_rocket_battery` | Rare | 2 |
| Empire | `wh2_dlc13_emp_veh_luminark_of_hysh_0_imperial_supply` | Rare | 3 |
| Empire | `wh2_dlc13_emp_veh_steam_tank_imperial_supply` | Rare | 3 |
| Empire | `wh2_dlc13_emp_veh_steam_tank_ror_0` | Rare | 3 |
| Empire | `wh3_dlc25_emp_veh_steam_tank_volley_gun` | Rare | 3 |
| Empire | `wh3_dlc29_emp_veh_celestial_hurricanum_0` | Rare | 3 |
| Empire | `wh_dlc04_emp_veh_templehof_luminark_0` | Rare | 3 |
| Empire | `wh_main_emp_veh_luminark_of_hysh_0` | Rare | 3 |
| Empire | `wh_main_emp_veh_steam_tank` | Rare | 3 |
| Feral monsters | `wh3_main_monster_feral_bears` | Special | 2 |
| Feral monsters | `wh3_main_monster_feral_ice_bears` | Rare | 1 |
| Greenskins | `wh2_dlc15_grn_cav_forest_goblin_spider_riders_waaagh_0` | Core | - |
| Greenskins | `wh3_main_grn_inf_goblins_sword_shield` | Core | - |
| Greenskins | `wh3_main_grn_inf_orc_boyz_spear_shield` | Core | - |
| Greenskins | `wh_dlc06_grn_cav_deff_creepers_0` | Core | - |
| Greenskins | `wh_dlc06_grn_cav_mogrubbs_marauders_0` | Core | - |
| Greenskins | `wh_dlc06_grn_cav_moon_howlers_0` | Core | - |
| Greenskins | `wh_dlc06_grn_inf_da_eight_peaks_loonies_0` | Core | - |
| Greenskins | `wh_dlc06_grn_inf_da_warlords_boyz_0` | Core | - |
| Greenskins | `wh_dlc06_grn_inf_nasty_skulkers_0` | Core | - |
| Greenskins | `wh_dlc06_grn_inf_squig_explosive_0` | Core | - |
| Greenskins | `wh_dlc06_grn_mon_spider_hatchlings_0` | Core | - |
| Greenskins | `wh_main_grn_cav_forest_goblin_spider_riders_0` | Core | - |
| Greenskins | `wh_main_grn_cav_forest_goblin_spider_riders_1` | Core | - |
| Greenskins | `wh_main_grn_cav_goblin_wolf_riders_0` | Core | - |
| Greenskins | `wh_main_grn_cav_goblin_wolf_riders_1` | Core | - |
| Greenskins | `wh_main_grn_inf_goblin_archers` | Core | - |
| Greenskins | `wh_main_grn_inf_goblin_spearmen` | Core | - |
| Greenskins | `wh_main_grn_inf_night_goblin_archers` | Core | - |
| Greenskins | `wh_main_grn_inf_night_goblin_fanatics` | Core | - |
| Greenskins | `wh_main_grn_inf_night_goblin_fanatics_1` | Core | - |
| Greenskins | `wh_main_grn_inf_night_goblins` | Core | - |
| Greenskins | `wh_main_grn_inf_orc_arrer_boyz` | Core | - |
| Greenskins | `wh_main_grn_inf_orc_big_uns` | Core | - |
| Greenskins | `wh_main_grn_inf_orc_boyz` | Core | - |
| Greenskins | `wh_main_grn_inf_savage_orc_arrer_boyz` | Core | - |
| Greenskins | `wh_main_grn_inf_savage_orc_big_uns` | Core | - |
| Greenskins | `wh_main_grn_inf_savage_orcs` | Core | - |
| Greenskins | `wh_dlc06_grn_cav_teef_robbers_0` | Special | 1 |
| Greenskins | `wh_dlc06_grn_inf_da_rusty_arrers_0` | Special | 1 |
| Greenskins | `wh_dlc06_grn_inf_squig_herd_0` | Special | 1 |
| Greenskins | `wh_main_grn_cav_goblin_wolf_chariot` | Special | 1 |
| Greenskins | `wh_main_grn_cav_orc_boar_boyz` | Special | 1 |
| Greenskins | `wh_main_grn_cav_savage_orc_boar_boyz` | Special | 1 |
| Greenskins | `wh_main_grn_mon_trolls` | Special | 1 |
| Greenskins | `wh2_dlc15_grn_cav_squig_hoppers_waaagh_0` | Special | 2 |
| Greenskins | `wh2_dlc15_grn_mon_river_trolls_0` | Special | 2 |
| Greenskins | `wh2_dlc15_grn_mon_river_trolls_ror_0` | Special | 2 |
| Greenskins | `wh2_dlc15_grn_mon_stone_trolls_0` | Special | 2 |
| Greenskins | `wh3_dlc26_grn_art_bolt_throwa` | Special | 2 |
| Greenskins | `wh3_dlc26_grn_inf_black_orcs_shield` | Special | 2 |
| Greenskins | `wh3_dlc26_grn_inf_rugluds_armoured_orcs` | Special | 2 |
| Greenskins | `wh_dlc06_grn_cav_broken_tusks_mob_0` | Special | 2 |
| Greenskins | `wh_dlc06_grn_cav_durkits_squigs_0` | Special | 2 |
| Greenskins | `wh_dlc06_grn_cav_squig_hoppers_0` | Special | 2 |
| Greenskins | `wh_dlc06_grn_inf_krimson_killerz_0` | Special | 2 |
| Greenskins | `wh_main_grn_cav_orc_boar_boy_big_uns` | Special | 2 |
| Greenskins | `wh_main_grn_cav_orc_boar_chariot` | Special | 2 |
| Greenskins | `wh_main_grn_cav_savage_orc_boar_boy_big_uns` | Special | 2 |
| Greenskins | `wh_main_grn_inf_black_orcs` | Special | 2 |
| Greenskins | `wh2_dlc15_grn_mon_wyvern_waaagh_0` | Rare | 1 |
| Greenskins | `wh2_dlc15_grn_veh_snotling_pump_wagon_0` | Rare | 1 |
| Greenskins | `wh2_dlc15_grn_veh_snotling_pump_wagon_flappas_0` | Rare | 1 |
| Greenskins | `wh2_dlc15_grn_veh_snotling_pump_wagon_roller_0` | Rare | 1 |
| Greenskins | `wh2_dlc15_grn_veh_snotling_pump_wagon_ror_0` | Rare | 1 |
| Greenskins | `wh2_twa03_grn_mon_wyvern_0` | Rare | 1 |
| Greenskins | `wh3_dlc26_grn_art_bolt_throwa_ror` | Rare | 1 |
| Greenskins | `wh3_dlc26_grn_cav_mangler_squig` | Rare | 1 |
| Greenskins | `wh_dlc06_grn_art_hammer_of_gork_0` | Rare | 1 |
| Greenskins | `wh_main_grn_art_goblin_rock_lobber` | Rare | 1 |
| Greenskins | `wh2_dlc15_grn_mon_feral_hydra_waaagh_0` | Rare | 2 |
| Greenskins | `wh3_dlc26_grn_mon_colossal_squig` | Rare | 2 |
| Greenskins | `wh3_dlc26_grn_mon_colossal_squig_ror` | Rare | 2 |
| Greenskins | `wh_main_grn_art_doom_diver_catapult` | Rare | 2 |
| Greenskins | `wh_main_grn_mon_giant` | Rare | 2 |
| Greenskins | `wh2_dlc15_grn_mon_rogue_idol_0` | Rare | 3 |
| Greenskins | `wh2_dlc15_grn_mon_rogue_idol_ror_0` | Rare | 3 |
| Greenskins | `wh3_dlc26_grn_mon_arachnarok_spider_flinger` | Rare | 3 |
| Greenskins | `wh_dlc06_grn_mon_venom_queen_0` | Rare | 3 |
| Greenskins | `wh_dlc15_grn_mon_arachnarok_spider_waaagh_0` | Rare | 3 |
| Greenskins | `wh_main_grn_mon_arachnarok_spider_0` | Rare | 3 |
| High Elves | `wh2_dlc10_hef_cav_the_heralds_of_the_wind_ror_0` | Core | - |
| High Elves | `wh2_dlc10_hef_inf_dryads_0` | Core | - |
| High Elves | `wh2_dlc10_hef_inf_the_scions_of_mathlann_ror_0` | Core | - |
| High Elves | `wh2_dlc10_hef_inf_the_storm_riders_ror_0` | Core | - |
| High Elves | `wh2_dlc15_hef_inf_archers_ror_0` | Core | - |
| High Elves | `wh2_dlc15_hef_inf_rangers_0` | Core | - |
| High Elves | `wh2_main_hef_cav_ellyrian_reavers_0` | Core | - |
| High Elves | `wh2_main_hef_cav_ellyrian_reavers_1` | Core | - |
| High Elves | `wh2_main_hef_cav_silver_helms_0` | Core | - |
| High Elves | `wh2_main_hef_cav_silver_helms_1` | Core | - |
| High Elves | `wh2_main_hef_inf_archers_0` | Core | - |
| High Elves | `wh2_main_hef_inf_archers_1` | Core | - |
| High Elves | `wh2_main_hef_inf_gate_guard` | Core | - |
| High Elves | `wh2_main_hef_inf_lothern_sea_guard_0` | Core | - |
| High Elves | `wh2_main_hef_inf_lothern_sea_guard_1` | Core | - |
| High Elves | `wh2_main_hef_inf_spearmen_0` | Core | - |
| High Elves | `wh3_dlc27_hef_inf_ships_company` | Core | - |
| High Elves | `wh3_dlc27_hef_inf_ships_company_ror` | Core | - |
| High Elves | `wh2_dlc10_hef_inf_shadow_warriors_0` | Special | 1 |
| High Elves | `wh2_dlc10_hef_inf_the_grey_ror_0` | Special | 1 |
| High Elves | `wh2_dlc10_hef_inf_the_silverpelts_ror_0` | Special | 1 |
| High Elves | `wh2_dlc15_hef_inf_mistwalkers_faithbearers_0` | Special | 1 |
| High Elves | `wh2_dlc15_hef_inf_mistwalkers_sentinels_0` | Special | 1 |
| High Elves | `wh2_dlc15_hef_inf_mistwalkers_skyhawks_0` | Special | 1 |
| High Elves | `wh2_dlc15_hef_inf_mistwalkers_spireguard_0` | Special | 1 |
| High Elves | `wh2_dlc15_hef_inf_silverin_guard_0` | Special | 1 |
| High Elves | `wh2_dlc15_hef_mon_war_lions_of_chrace_0` | Special | 1 |
| High Elves | `wh2_dlc15_hef_mon_war_lions_of_chrace_ror_0` | Special | 1 |
| High Elves | `wh2_main_hef_cav_tiranoc_chariot` | Special | 1 |
| High Elves | `wh2_main_hef_inf_white_lions_of_chrace_0` | Special | 1 |
| High Elves | `wh2_dlc10_hef_cav_the_fireborn_ror_0` | Special | 2 |
| High Elves | `wh2_dlc10_hef_inf_keepers_of_the_flame_ror_0` | Special | 2 |
| High Elves | `wh2_dlc10_hef_inf_shadow_walkers_0` | Special | 2 |
| High Elves | `wh2_dlc10_hef_mon_treekin_0` | Special | 2 |
| High Elves | `wh2_dlc15_hef_veh_lion_chariot_of_chrace_0` | Special | 2 |
| High Elves | `wh2_main_hef_cav_dragon_princes` | Special | 2 |
| High Elves | `wh2_main_hef_cav_ithilmar_chariot` | Special | 2 |
| High Elves | `wh2_main_hef_inf_phoenix_guard` | Special | 2 |
| High Elves | `wh2_main_hef_inf_swordmasters_of_hoeth_0` | Special | 2 |
| High Elves | `wh2_main_hef_mon_great_eagle` | Special | 2 |
| High Elves | `wh3_dlc27_hef_inf_swordmasters_of_hoeth_ror` | Special | 2 |
| High Elves | `wh3_dlc27_hef_inf_oceanids` | Special | 3 |
| High Elves | `wh2_dlc10_hef_inf_everqueens_court_guards_ror_0` | Rare | 1 |
| High Elves | `wh2_dlc10_hef_inf_sisters_of_avelorn_0` | Rare | 1 |
| High Elves | `wh2_main_hef_art_eagle_claw_bolt_thrower` | Rare | 1 |
| High Elves | `wh2_main_hef_mon_phoenix_flamespyre` | Rare | 1 |
| High Elves | `wh2_main_hef_mon_phoenix_frostheart` | Rare | 1 |
| High Elves | `wh3_dlc27_hef_veh_skycutter_bows` | Rare | 1 |
| High Elves | `wh3_dlc27_hef_veh_skycutter_ror` | Rare | 1 |
| High Elves | `wh2_dlc15_hef_mon_arcane_phoenix_0` | Rare | 2 |
| High Elves | `wh2_dlc15_hef_mon_arcane_phoenix_ror_0` | Rare | 2 |
| High Elves | `wh2_dlc15_hef_mon_sun_dragon_imrik` | Rare | 2 |
| High Elves | `wh2_main_hef_mon_moon_dragon` | Rare | 2 |
| High Elves | `wh2_main_hef_mon_sun_dragon` | Rare | 2 |
| High Elves | `wh3_dlc27_hef_veh_skycutter_bolt_thrower` | Rare | 2 |
| High Elves | `wh2_dlc10_hef_mon_treeman_0` | Rare | 3 |
| High Elves | `wh2_dlc15_hef_inf_mistwalkers_griffon_knights_0` | Rare | 3 |
| High Elves | `wh2_dlc15_hef_mon_black_dragon_imrik` | Rare | 3 |
| High Elves | `wh2_dlc15_hef_mon_forest_dragon_0` | Rare | 3 |
| High Elves | `wh2_dlc15_hef_mon_forest_dragon_imrik` | Rare | 3 |
| High Elves | `wh2_dlc15_hef_mon_moon_dragon_imrik` | Rare | 3 |
| High Elves | `wh2_dlc15_hef_mon_star_dragon_imrik` | Rare | 3 |
| High Elves | `wh2_main_hef_mon_star_dragon` | Rare | 3 |
| High Elves | `wh3_dlc27_hef_mon_merwyrm` | Rare | 3 |
| High Elves | `wh3_dlc27_hef_mon_merwyrm_ror` | Rare | 3 |
| High Elves | `wh3_dlc27_hef_mon_sea_elemental` | Rare | 3 |
| Khorne | `wh3_dlc27_kho_inf_chaos_warriors_2` | Core | - |
| Khorne | `wh3_main_kho_inf_bloodletters_0` | Core | - |
| Khorne | `wh3_main_kho_inf_chaos_warhounds_0` | Core | - |
| Khorne | `wh3_main_kho_inf_chaos_warriors_0` | Core | - |
| Khorne | `wh3_main_kho_inf_chaos_warriors_1` | Core | - |
| Khorne | `wh3_main_kho_inf_chaos_warriors_2` | Core | - |
| Khorne | `wh3_dlc26_kho_inf_khorngors` | Special | 1 |
| Khorne | `wh3_main_kho_cav_gorebeast_chariot` | Special | 1 |
| Khorne | `wh3_main_kho_inf_chaos_furies_0` | Special | 1 |
| Khorne | `wh3_main_kho_inf_flesh_hounds_of_khorne_0` | Special | 1 |
| Khorne | `wh3_twa10_kho_inf_flesh_hounds_of_khorne_ror` | Special | 1 |
| Khorne | `wh3_dlc26_kho_inf_skullreapers` | Special | 2 |
| Khorne | `wh3_main_kho_cav_bloodcrushers_0` | Special | 2 |
| Khorne | `wh3_main_kho_inf_bloodletters_1` | Special | 2 |
| Khorne | `wh3_twa06_kho_inf_bloodletters_ror_0` | Special | 2 |
| Khorne | `wh3_twa07_kho_cav_bloodcrushers_ror_0` | Special | 2 |
| Khorne | `wh3_dlc26_kho_mon_bloodbeast_of_khorne` | Special | 3 |
| Khorne | `wh3_main_kho_mon_khornataurs_0` | Special | 3 |
| Khorne | `wh3_main_kho_mon_khornataurs_1` | Special | 3 |
| Khorne | `wh3_dlc26_kho_inf_wrathmongers` | Rare | 1 |
| Khorne | `wh3_dlc26_kho_inf_wrathmongers_ror` | Rare | 1 |
| Khorne | `wh3_dlc27_kho_mon_spawn_of_khorne_0` | Rare | 1 |
| Khorne | `wh3_main_kho_mon_spawn_of_khorne_0` | Rare | 1 |
| Khorne | `wh3_main_kho_veh_blood_shrine_0` | Rare | 1 |
| Khorne | `wh3_dlc20_kho_cav_skullcrushers_mkho_ror` | Rare | 2 |
| Khorne | `wh3_dlc26_kho_veh_skullcannon_ror` | Rare | 2 |
| Khorne | `wh3_main_kho_cav_skullcrushers_0` | Rare | 2 |
| Khorne | `wh3_main_kho_mon_soul_grinder_0` | Rare | 2 |
| Khorne | `wh3_main_kho_veh_skullcannon_0` | Rare | 2 |
| Khorne | `wh2_dlc17_kho_mon_ghorgon_ror_0` | Rare | 3 |
| Khorne | `wh3_dlc26_kho_mon_slaughterbrute` | Rare | 3 |
| Khorne | `wh3_main_kho_mon_bloodthirster_0` | Rare | 3 |
| Khorne | `wh3_twa08_kho_mon_bloodthirster_0_ror` | Rare | 3 |
| Kislev | `wh3_dlc24_ksl_inf_kislevite_warriors` | Core | - |
| Kislev | `wh3_dlc24_ksl_inf_streltsi_ror` | Core | - |
| Kislev | `wh3_main_ksl_cav_horse_archers_0` | Core | - |
| Kislev | `wh3_main_ksl_cav_horse_raiders_0` | Core | - |
| Kislev | `wh3_main_ksl_cav_winged_lancers_0` | Core | - |
| Kislev | `wh3_main_ksl_inf_armoured_kossars_0` | Core | - |
| Kislev | `wh3_main_ksl_inf_armoured_kossars_1` | Core | - |
| Kislev | `wh3_main_ksl_inf_kossars_0` | Core | - |
| Kislev | `wh3_main_ksl_inf_kossars_1` | Core | - |
| Kislev | `wh3_main_ksl_inf_streltsi_0` | Core | - |
| Kislev | `wh3_twa10_ksl_inf_armoured_kossars_ror` | Core | - |
| Kislev | `wh3_dlc24_ksl_mon_the_things_in_the_woods` | Special | 2 |
| Kislev | `wh3_dlc24_ksl_mon_the_things_in_the_woods_ror` | Special | 2 |
| Kislev | `wh3_main_ksl_cav_gryphon_legion_0` | Special | 2 |
| Kislev | `wh3_main_ksl_inf_tzar_guard_0` | Special | 2 |
| Kislev | `wh3_main_ksl_inf_tzar_guard_1` | Special | 2 |
| Kislev | `wh3_main_ksl_veh_light_war_sled_0` | Special | 2 |
| Kislev | `wh3_twa06_ksl_inf_tzar_guard_ror_0` | Special | 2 |
| Kislev | `wh3_main_ksl_cav_war_bear_riders_1` | Special | 3 |
| Kislev | `wh3_main_ksl_veh_heavy_war_sled_0` | Special | 3 |
| Kislev | `wh3_twa07_ksl_cav_war_bear_riders_ror_0` | Special | 3 |
| Kislev | `wh3_dlc24_ksl_inf_akshina_ambushers` | Rare | 1 |
| Kislev | `wh3_dlc24_ksl_inf_akshina_ambushers_ror` | Rare | 1 |
| Kislev | `wh3_main_ksl_inf_ice_guard_0` | Rare | 1 |
| Kislev | `wh3_main_ksl_inf_ice_guard_1` | Rare | 1 |
| Kislev | `wh3_main_ksl_mon_snow_leopard_0` | Rare | 1 |
| Kislev | `wh3_dlc24_ksl_mon_frost_wyrm` | Rare | 2 |
| Kislev | `wh3_main_ksl_veh_little_grom_0` | Rare | 2 |
| Kislev | `wh3_dlc24_ksl_mon_incarnate_elemental_of_beasts` | Rare | 3 |
| Kislev | `wh3_main_ksl_mon_elemental_bear_0` | Rare | 3 |
| Kislev | `wh3_twa08_ksl_mon_elemental_bear_0_ror` | Rare | 3 |
| Lizardmen | `wh2_dlc12_lzd_inf_skink_red_crested_0` | Core | - |
| Lizardmen | `wh2_main_lzd_cav_cold_ones_feral_0` | Core | - |
| Lizardmen | `wh2_main_lzd_inf_saurus_spearmen_0` | Core | - |
| Lizardmen | `wh2_main_lzd_inf_saurus_spearmen_1` | Core | - |
| Lizardmen | `wh2_main_lzd_inf_saurus_spearmen_blessed_1` | Core | - |
| Lizardmen | `wh2_main_lzd_inf_saurus_warriors_0` | Core | - |
| Lizardmen | `wh2_main_lzd_inf_saurus_warriors_1` | Core | - |
| Lizardmen | `wh2_main_lzd_inf_saurus_warriors_blessed_1` | Core | - |
| Lizardmen | `wh2_main_lzd_inf_skink_cohort_0` | Core | - |
| Lizardmen | `wh2_main_lzd_inf_skink_cohort_1` | Core | - |
| Lizardmen | `wh2_main_lzd_inf_skink_cohort_1_blessed` | Core | - |
| Lizardmen | `wh2_main_lzd_inf_skink_skirmishers_0` | Core | - |
| Lizardmen | `wh2_main_lzd_inf_skink_skirmishers_blessed_0` | Core | - |
| Lizardmen | `wh2_dlc12_lzd_cav_cold_one_spearriders_ror_0` | Special | 1 |
| Lizardmen | `wh2_dlc12_lzd_cav_ripperdactyl_riders_0` | Special | 1 |
| Lizardmen | `wh2_dlc12_lzd_cav_ripperdactyl_riders_0_blessed` | Special | 1 |
| Lizardmen | `wh2_dlc12_lzd_cav_ripperdactyl_riders_ror_0` | Special | 1 |
| Lizardmen | `wh2_dlc12_lzd_cav_terradon_riders_0_tlaqua` | Special | 1 |
| Lizardmen | `wh2_dlc12_lzd_cav_terradon_riders_1_tlaqua` | Special | 1 |
| Lizardmen | `wh2_dlc12_lzd_cav_terradon_riders_ror_0` | Special | 1 |
| Lizardmen | `wh2_dlc12_lzd_inf_saurus_warriors_ror_0` | Special | 1 |
| Lizardmen | `wh2_dlc12_lzd_inf_skink_red_crested_ror_0` | Special | 1 |
| Lizardmen | `wh2_dlc12_lzd_inf_temple_guards_ror_0` | Special | 1 |
| Lizardmen | `wh2_main_lzd_cav_cold_one_spearmen_1` | Special | 1 |
| Lizardmen | `wh2_main_lzd_cav_cold_one_spearriders_blessed_0` | Special | 1 |
| Lizardmen | `wh2_main_lzd_cav_cold_ones_1` | Special | 1 |
| Lizardmen | `wh2_main_lzd_cav_terradon_riders_0` | Special | 1 |
| Lizardmen | `wh2_main_lzd_cav_terradon_riders_0_blessed` | Special | 1 |
| Lizardmen | `wh2_main_lzd_cav_terradon_riders_1` | Special | 1 |
| Lizardmen | `wh2_main_lzd_cav_terradon_riders_blessed_1` | Special | 1 |
| Lizardmen | `wh2_main_lzd_inf_chameleon_skinks_0` | Special | 1 |
| Lizardmen | `wh2_main_lzd_inf_chameleon_skinks_blessed_0` | Special | 1 |
| Lizardmen | `wh2_main_lzd_inf_temple_guards` | Special | 1 |
| Lizardmen | `wh2_main_lzd_inf_temple_guards_blessed` | Special | 1 |
| Lizardmen | `wh2_main_lzd_inf_temple_guards_nakai` | Special | 1 |
| Lizardmen | `wh2_main_lzd_mon_bastiladon_0` | Special | 1 |
| Lizardmen | `wh2_main_lzd_mon_kroxigors_nakai` | Special | 1 |
| Lizardmen | `wh2_dlc12_lzd_mon_bastiladon_3` | Special | 2 |
| Lizardmen | `wh2_dlc12_lzd_mon_bastiladon_3_nakai` | Special | 2 |
| Lizardmen | `wh2_dlc12_lzd_mon_salamander_pack_0` | Special | 2 |
| Lizardmen | `wh2_dlc12_lzd_mon_salamander_pack_0_blessed` | Special | 2 |
| Lizardmen | `wh2_dlc12_lzd_mon_salamander_pack_ror_0` | Special | 2 |
| Lizardmen | `wh2_dlc13_lzd_mon_razordon_pack_0` | Special | 2 |
| Lizardmen | `wh2_dlc13_lzd_mon_razordon_pack_0_blessed` | Special | 2 |
| Lizardmen | `wh2_dlc13_lzd_mon_razordon_pack_ror_0` | Special | 2 |
| Lizardmen | `wh2_dlc13_lzd_mon_sacred_kroxigors_0` | Special | 2 |
| Lizardmen | `wh2_dlc13_lzd_mon_sacred_kroxigors_0_blessed` | Special | 2 |
| Lizardmen | `wh2_dlc13_lzd_mon_sacred_kroxigors_0_nakai` | Special | 2 |
| Lizardmen | `wh2_dlc13_lzd_mon_sacred_kroxigors_ror_0` | Special | 2 |
| Lizardmen | `wh2_main_lzd_cav_horned_ones_0` | Special | 2 |
| Lizardmen | `wh2_main_lzd_cav_horned_ones_0_nakai` | Special | 2 |
| Lizardmen | `wh2_main_lzd_cav_horned_ones_blessed_0` | Special | 2 |
| Lizardmen | `wh2_main_lzd_mon_bastiladon_1` | Special | 2 |
| Lizardmen | `wh2_main_lzd_mon_bastiladon_2` | Special | 2 |
| Lizardmen | `wh2_main_lzd_mon_bastiladon_blessed_2` | Special | 2 |
| Lizardmen | `wh2_main_lzd_mon_kroxigors` | Special | 2 |
| Lizardmen | `wh2_main_lzd_mon_kroxigors_blessed` | Special | 2 |
| Lizardmen | `wh2_main_lzd_mon_stegadon_0` | Special | 2 |
| Lizardmen | `wh2_main_lzd_mon_stegadon_1` | Special | 2 |
| Lizardmen | `wh2_main_lzd_mon_stegadon_blessed_1` | Special | 2 |
| Lizardmen | `wh2_dlc12_lzd_mon_ancient_salamander_0` | Rare | 1 |
| Lizardmen | `wh2_dlc12_lzd_mon_ancient_salamander_0_blessed` | Rare | 1 |
| Lizardmen | `wh2_dlc17_lzd_inf_chameleon_stalkers_0` | Rare | 1 |
| Lizardmen | `wh2_dlc17_lzd_inf_chameleon_stalkers_0_blessed` | Rare | 1 |
| Lizardmen | `wh2_dlc13_lzd_mon_dread_saurian_0` | Rare | 2 |
| Lizardmen | `wh2_dlc17_lzd_mon_carnosaur_ror_0` | Rare | 2 |
| Lizardmen | `wh2_dlc17_lzd_mon_coatl_0` | Rare | 2 |
| Lizardmen | `wh2_dlc17_lzd_mon_troglodon_0` | Rare | 2 |
| Lizardmen | `wh2_dlc17_lzd_mon_troglodon_ror_0` | Rare | 2 |
| Lizardmen | `wh2_main_lzd_mon_carnosaur_0` | Rare | 2 |
| Lizardmen | `wh2_main_lzd_mon_carnosaur_blessed_0` | Rare | 2 |
| Lizardmen | `wh3_dlc24_lzd_mon_carnosaur_0` | Rare | 2 |
| Lizardmen | `wh2_dlc12_lzd_mon_ancient_stegadon_1` | Rare | 3 |
| Lizardmen | `wh2_dlc12_lzd_mon_ancient_stegadon_1_nakai` | Rare | 3 |
| Lizardmen | `wh2_dlc12_lzd_mon_ancient_stegadon_ror_0` | Rare | 3 |
| Lizardmen | `wh2_dlc13_lzd_mon_dread_saurian_1` | Rare | 3 |
| Lizardmen | `wh2_dlc13_lzd_mon_dread_saurian_ror_0` | Rare | 3 |
| Lizardmen | `wh2_dlc17_lzd_mon_coatl_ror_0` | Rare | 3 |
| Lizardmen | `wh2_main_lzd_mon_ancient_stegadon` | Rare | 3 |
| Lizardmen | `wh2_main_lzd_mon_ancient_stegadon_blessed` | Rare | 3 |
| Lizardmen | `wh3_dlc27_lzd_mon_dread_saurian_monst_arcanum` | Rare | 3 |
| Norsca | `wh3_dlc27_nor_cav_chaos_chariot_ror` | Core | - |
| Norsca | `wh3_dlc27_nor_cav_marauder_horsemen_ror` | Core | - |
| Norsca | `wh3_dlc27_nor_inf_chaos_marauders_great_weapons_ror` | Core | - |
| Norsca | `wh_dlc08_nor_cav_marauder_horsemasters_0` | Core | - |
| Norsca | `wh_dlc08_nor_inf_marauder_hunters_0` | Core | - |
| Norsca | `wh_dlc08_nor_inf_marauder_hunters_1` | Core | - |
| Norsca | `wh_dlc08_nor_inf_marauder_spearman_0` | Core | - |
| Norsca | `wh_main_nor_cav_chaos_chariot` | Core | - |
| Norsca | `wh_main_nor_cav_marauder_horsemen_0` | Core | - |
| Norsca | `wh_main_nor_cav_marauder_horsemen_1` | Core | - |
| Norsca | `wh_main_nor_inf_chaos_marauders_0` | Core | - |
| Norsca | `wh_main_nor_inf_chaos_marauders_1` | Core | - |
| Norsca | `wh_main_nor_mon_chaos_warhounds_0` | Core | - |
| Norsca | `wh_main_nor_mon_chaos_warhounds_1` | Core | - |
| Norsca | `wh_pro04_nor_inf_chaos_marauders_ror_0` | Core | - |
| Norsca | `wh_pro04_nor_mon_marauder_warwolves_ror_0` | Core | - |
| Norsca | `wh3_dlc27_nor_cav_kurgan_horsemen_dualweapons` | Special | 1 |
| Norsca | `wh3_dlc27_nor_cav_kurgan_horsemen_greatweapons` | Special | 1 |
| Norsca | `wh3_dlc27_nor_inf_marauder_bearmen` | Special | 1 |
| Norsca | `wh3_dlc27_nor_inf_marauder_bearmen_greatweapons` | Special | 1 |
| Norsca | `wh3_dlc27_throgg_mon_chs_trolls_0` | Special | 1 |
| Norsca | `wh3_dlc27_throgg_mon_chs_trolls_1` | Special | 1 |
| Norsca | `wh_dlc08_nor_inf_marauder_berserkers_0` | Special | 1 |
| Norsca | `wh_dlc08_nor_mon_warwolves_0` | Special | 1 |
| Norsca | `wh_pro04_nor_inf_marauder_berserkers_ror_0` | Special | 1 |
| Norsca | `wh3_dlc27_throgg_mon_river_trolls_0` | Special | 2 |
| Norsca | `wh3_dlc27_throgg_mon_stone_trolls_0` | Special | 2 |
| Norsca | `wh_dlc08_nor_feral_manticore` | Special | 2 |
| Norsca | `wh_dlc08_nor_inf_marauder_champions_0` | Special | 2 |
| Norsca | `wh_dlc08_nor_inf_marauder_champions_1` | Special | 2 |
| Norsca | `wh_dlc08_nor_mon_norscan_ice_trolls_0` | Special | 2 |
| Norsca | `wh_dlc08_nor_mon_skinwolves_0` | Special | 2 |
| Norsca | `wh_dlc08_nor_mon_skinwolves_1` | Special | 2 |
| Norsca | `wh_dlc08_nor_veh_marauder_warwolves_chariot_0` | Special | 2 |
| Norsca | `wh_main_nor_mon_chaos_trolls` | Special | 2 |
| Norsca | `wh_pro04_nor_mon_skinwolves_ror_0` | Special | 2 |
| Norsca | `wh_dlc08_nor_mon_fimir_0` | Rare | 1 |
| Norsca | `wh_dlc08_nor_mon_fimir_1` | Rare | 1 |
| Norsca | `wh_pro04_nor_mon_fimir_ror_0` | Rare | 1 |
| Norsca | `wh3_dlc27_nor_mon_chimera` | Rare | 2 |
| Norsca | `wh3_dlc27_nor_mon_chimera_monst_arcanum` | Rare | 2 |
| Norsca | `wh3_dlc27_nor_mon_chimera_monst_arcanum_reward` | Rare | 2 |
| Norsca | `wh3_dlc27_nor_mon_chimera_ror` | Rare | 2 |
| Norsca | `wh3_dlc27_nor_mon_dread_maw` | Rare | 2 |
| Norsca | `wh3_dlc27_nor_mon_dread_maw_underground` | Rare | 2 |
| Norsca | `wh3_dlc27_throgg_mon_bile_trolls` | Rare | 2 |
| Norsca | `wh_dlc08_nor_mon_frost_wyrm_ror_0` | Rare | 2 |
| Norsca | `wh_dlc08_nor_mon_norscan_giant_0` | Rare | 2 |
| Norsca | `wh_dlc08_nor_mon_war_mammoth_0` | Rare | 2 |
| Norsca | `wh_dlc08_nor_mon_war_mammoth_ror_1` | Rare | 2 |
| Norsca | `wh3_dlc27_nor_mon_cursd_ettin` | Rare | 3 |
| Norsca | `wh3_dlc27_nor_mon_cursd_ettin_runecaller` | Rare | 3 |
| Norsca | `wh_dlc08_nor_art_hellcannon_battery` | Rare | 3 |
| Norsca | `wh_dlc08_nor_mon_frost_wyrm_0` | Rare | 3 |
| Norsca | `wh_dlc08_nor_mon_war_mammoth_1` | Rare | 3 |
| Norsca | `wh_dlc08_nor_mon_war_mammoth_2` | Rare | 3 |
| Norsca | `wh_pro04_nor_mon_war_mammoth_ror_0` | Rare | 3 |
| Nurgle | `wh3_dlc25_nur_chieftain_cav_chaos_chariot_mnur` | Core | - |
| Nurgle | `wh3_dlc25_nur_chieftain_inf_chaos_dwarf_blunderbusses` | Core | - |
| Nurgle | `wh3_main_nur_inf_forsaken_0` | Core | - |
| Nurgle | `wh3_main_nur_inf_forsaken_0_warriors` | Core | - |
| Nurgle | `wh3_main_nur_inf_nurglings_0` | Core | - |
| Nurgle | `wh3_main_nur_inf_plaguebearers_0` | Core | - |
| Nurgle | `wh3_main_nur_mon_plague_toads_0` | Core | - |
| Nurgle | `wh3_twa10_nur_inf_nurglings_ror` | Core | - |
| Nurgle | `wh3_dlc25_nur_chieftain_inf_centigors_1` | Special | 1 |
| Nurgle | `wh3_dlc25_nur_inf_pestigors` | Special | 1 |
| Nurgle | `wh3_main_nur_inf_chaos_furies_0` | Special | 1 |
| Nurgle | `wh3_main_nur_mon_beast_of_nurgle_0` | Special | 1 |
| Nurgle | `wh3_main_nur_mon_rot_flies_0` | Special | 1 |
| Nurgle | `wh3_dlc25_nur_chieftain_cav_rot_knights` | Special | 2 |
| Nurgle | `wh3_dlc25_nur_chieftain_inf_aspiring_champions_0` | Special | 2 |
| Nurgle | `wh3_dlc25_nur_chieftain_inf_infernal_guard_fireglaives` | Special | 2 |
| Nurgle | `wh3_dlc25_nur_chieftain_mon_skinwolves_0` | Special | 2 |
| Nurgle | `wh3_main_nur_cav_pox_riders_of_nurgle_0` | Special | 2 |
| Nurgle | `wh3_main_nur_inf_plaguebearers_1` | Special | 2 |
| Nurgle | `wh3_twa06_nur_inf_plaguebearers_ror_0` | Special | 2 |
| Nurgle | `wh3_twa07_nur_cav_pox_riders_of_nurgle_ror_0` | Special | 2 |
| Nurgle | `wh3_dlc25_nur_cav_rot_knights` | Special | 3 |
| Nurgle | `wh3_dlc25_nur_cav_rot_knights_ror` | Special | 3 |
| Nurgle | `wh3_dlc25_nur_cav_plague_drones_1_ror` | Rare | 1 |
| Nurgle | `wh3_dlc25_nur_chieftain_mon_fimir_0` | Rare | 1 |
| Nurgle | `wh3_dlc25_nur_chieftain_mon_fimir_1` | Rare | 1 |
| Nurgle | `wh3_dlc27_nur_mon_spawn_of_nurgle_0` | Rare | 1 |
| Nurgle | `wh3_main_nur_cav_plague_drones_0` | Rare | 1 |
| Nurgle | `wh3_main_nur_cav_plague_drones_1` | Rare | 1 |
| Nurgle | `wh3_main_nur_mon_spawn_of_nurgle_0` | Rare | 1 |
| Nurgle | `wh3_main_nur_mon_spawn_of_nurgle_0_warriors` | Rare | 1 |
| Nurgle | `wh3_dlc25_nur_chieftain_art_hellcannon` | Rare | 2 |
| Nurgle | `wh3_dlc25_nur_chieftain_inf_cygor_0` | Rare | 2 |
| Nurgle | `wh3_dlc25_nur_chieftain_mon_frost_wyrm_0` | Rare | 2 |
| Nurgle | `wh3_dlc25_nur_chieftain_mon_war_mammoth_0` | Rare | 2 |
| Nurgle | `wh3_dlc25_nur_inf_plague_ogres` | Rare | 2 |
| Nurgle | `wh3_dlc25_nur_inf_plague_ogres_great_weapons` | Rare | 2 |
| Nurgle | `wh3_dlc25_nur_mon_bile_trolls` | Rare | 2 |
| Nurgle | `wh3_dlc25_nur_mon_soul_grinder_0_ror` | Rare | 2 |
| Nurgle | `wh3_main_nur_mon_soul_grinder_0` | Rare | 2 |
| Nurgle | `wh3_dlc25_nur_chieftain_mon_dragon_ogre_shaggoth` | Rare | 3 |
| Nurgle | `wh3_dlc25_nur_chieftain_mon_ghorgon` | Rare | 3 |
| Nurgle | `wh3_dlc25_nur_chieftain_mon_toad_dragon` | Rare | 3 |
| Nurgle | `wh3_dlc25_nur_chieftain_mon_war_mammoth_1` | Rare | 3 |
| Nurgle | `wh3_dlc25_nur_chieftain_veh_dreadquake_mortar` | Rare | 3 |
| Nurgle | `wh3_dlc25_nur_mon_toad_dragon` | Rare | 3 |
| Nurgle | `wh3_dlc27_nur_mon_toad_dragon_monst_arcanum` | Rare | 3 |
| Nurgle | `wh3_dlc27_nur_mon_toad_dragon_monst_arcanum_reward` | Rare | 3 |
| Nurgle | `wh3_main_nur_mon_great_unclean_one_0` | Rare | 3 |
| Nurgle | `wh3_twa08_nur_mon_great_unclean_one_0_ror` | Rare | 3 |
| Ogre Kingdoms | `wh3_main_ogr_inf_gnoblars_0` | Core | - |
| Ogre Kingdoms | `wh3_main_ogr_inf_gnoblars_1` | Core | - |
| Ogre Kingdoms | `wh3_main_ogr_inf_gnoblars_flingers` | Core | - |
| Ogre Kingdoms | `wh3_main_ogr_inf_ogres_0` | Core | - |
| Ogre Kingdoms | `wh3_main_ogr_inf_ogres_1` | Core | - |
| Ogre Kingdoms | `wh3_main_ogr_inf_ogres_2` | Core | - |
| Ogre Kingdoms | `wh3_twa10_ogr_inf_gnoblars_ror` | Core | - |
| Ogre Kingdoms | `wh3_dlc26_ogr_inf_pigback_riders` | Special | 1 |
| Ogre Kingdoms | `wh3_dlc26_ogr_inf_pigback_riders_ror` | Special | 1 |
| Ogre Kingdoms | `wh3_dlc26_ogr_mon_blood_vultures` | Special | 1 |
| Ogre Kingdoms | `wh3_main_ogr_inf_ironguts_0` | Special | 1 |
| Ogre Kingdoms | `wh3_main_ogr_mon_sabretusk_pack_0` | Special | 1 |
| Ogre Kingdoms | `wh3_dlc26_ogr_mon_yhetees` | Special | 2 |
| Ogre Kingdoms | `wh3_dlc26_ogr_mon_yhetees_ror` | Special | 2 |
| Ogre Kingdoms | `wh3_main_ogr_cav_mournfang_cavalry_0` | Special | 2 |
| Ogre Kingdoms | `wh3_main_ogr_cav_mournfang_cavalry_1` | Special | 2 |
| Ogre Kingdoms | `wh3_main_ogr_cav_mournfang_cavalry_2` | Special | 2 |
| Ogre Kingdoms | `wh3_main_ogr_inf_leadbelchers_0` | Special | 2 |
| Ogre Kingdoms | `wh3_main_ogr_inf_maneaters_0` | Special | 2 |
| Ogre Kingdoms | `wh3_main_ogr_inf_maneaters_1` | Special | 2 |
| Ogre Kingdoms | `wh3_main_ogr_inf_maneaters_2` | Special | 2 |
| Ogre Kingdoms | `wh3_main_ogr_inf_maneaters_3` | Special | 2 |
| Ogre Kingdoms | `wh3_main_ogr_mon_gorgers_0` | Special | 2 |
| Ogre Kingdoms | `wh3_twa06_ogr_inf_maneaters_ror_0` | Special | 2 |
| Ogre Kingdoms | `wh3_dlc26_ogr_inf_golgfags_maneaters` | Special | 3 |
| Ogre Kingdoms | `wh3_dlc26_ogr_inf_eshin_maneater_ror` | Rare | 1 |
| Ogre Kingdoms | `wh3_main_ogr_veh_gnoblar_scraplauncher_0` | Rare | 1 |
| Ogre Kingdoms | `wh3_main_ogr_cav_crushers_0` | Rare | 2 |
| Ogre Kingdoms | `wh3_main_ogr_cav_crushers_1` | Rare | 2 |
| Ogre Kingdoms | `wh3_main_ogr_mon_giant_0` | Rare | 2 |
| Ogre Kingdoms | `wh3_main_ogr_mon_stonehorn_0` | Rare | 2 |
| Ogre Kingdoms | `wh3_main_ogr_veh_ironblaster_0` | Rare | 2 |
| Ogre Kingdoms | `wh3_twa07_ogr_cav_crushers_ror_0` | Rare | 2 |
| Ogre Kingdoms | `wh3_twa08_ogr_mon_stonehorn_0_ror` | Rare | 2 |
| Ogre Kingdoms | `wh3_dlc26_ogr_mon_thundertusk` | Rare | 3 |
| Ogre Kingdoms | `wh3_dlc27_ogr_mon_thundertusk_monst_arcanum` | Rare | 3 |
| Ogre Kingdoms | `wh3_main_ogr_mon_stonehorn_1` | Rare | 3 |
| Skaven | `wh2_dlc12_skv_inf_clanrats_ror_0` | Core | - |
| Skaven | `wh2_dlc16_skv_inf_skavenslave_spearmen_0_flesh_lab` | Core | - |
| Skaven | `wh2_dlc16_skv_inf_skavenslaves_0_flesh_lab` | Core | - |
| Skaven | `wh2_main_skv_inf_clanrat_spearmen_0` | Core | - |
| Skaven | `wh2_main_skv_inf_clanrat_spearmen_1` | Core | - |
| Skaven | `wh2_main_skv_inf_clanrats_0` | Core | - |
| Skaven | `wh2_main_skv_inf_clanrats_1` | Core | - |
| Skaven | `wh2_main_skv_inf_night_runners_0` | Core | - |
| Skaven | `wh2_main_skv_inf_night_runners_1` | Core | - |
| Skaven | `wh2_main_skv_inf_skavenslave_slingers_0` | Core | - |
| Skaven | `wh2_main_skv_inf_skavenslave_spearmen_0` | Core | - |
| Skaven | `wh2_main_skv_inf_skavenslaves_0` | Core | - |
| Skaven | `wh3_dlc29_skv_inf_clanrat_spearmen_vermintide` | Core | - |
| Skaven | `wh3_dlc29_skv_inf_clanrats_vermintide` | Core | - |
| Skaven | `wh3_dlc29_skv_inf_pusbags` | Core | - |
| Skaven | `wh3_dlc29_skv_inf_skavenslave_slingers_vermintide` | Core | - |
| Skaven | `wh3_dlc29_skv_inf_skavenslave_spearmen_vermintide` | Core | - |
| Skaven | `wh3_dlc29_skv_inf_skavenslaves_vermintide` | Core | - |
| Skaven | `wh2_dlc12_skv_inf_ratling_gun_0` | Special | 1 |
| Skaven | `wh2_dlc12_skv_inf_ratling_gun_ror_0` | Special | 1 |
| Skaven | `wh2_dlc12_skv_inf_ratling_gun_ror_tech_lab_0` | Special | 1 |
| Skaven | `wh2_dlc12_skv_inf_stormvermin_ror_0` | Special | 1 |
| Skaven | `wh2_dlc12_skv_inf_warpfire_thrower_ror_tech_lab_0` | Special | 1 |
| Skaven | `wh2_dlc14_skv_inf_eshin_triads_0` | Special | 1 |
| Skaven | `wh2_dlc14_skv_inf_eshin_triads_ror_0` | Special | 1 |
| Skaven | `wh2_dlc14_skv_inf_warp_grinder_0` | Special | 1 |
| Skaven | `wh2_dlc16_skv_mon_rat_ogres_flesh_lab` | Special | 1 |
| Skaven | `wh2_dlc16_skv_mon_wolf_rats_0` | Special | 1 |
| Skaven | `wh2_dlc16_skv_mon_wolf_rats_0_flesh_lab` | Special | 1 |
| Skaven | `wh2_dlc16_skv_mon_wolf_rats_1` | Special | 1 |
| Skaven | `wh2_dlc16_skv_mon_wolf_rats_1_flesh_lab` | Special | 1 |
| Skaven | `wh2_main_skv_inf_death_runners_0` | Special | 1 |
| Skaven | `wh2_main_skv_inf_gutter_runner_slingers_0` | Special | 1 |
| Skaven | `wh2_main_skv_inf_gutter_runner_slingers_1` | Special | 1 |
| Skaven | `wh2_main_skv_inf_gutter_runners_0` | Special | 1 |
| Skaven | `wh2_main_skv_inf_gutter_runners_1` | Special | 1 |
| Skaven | `wh2_main_skv_inf_plague_monks` | Special | 1 |
| Skaven | `wh2_main_skv_inf_stormvermin_0` | Special | 1 |
| Skaven | `wh2_main_skv_inf_stormvermin_1` | Special | 1 |
| Skaven | `wh2_main_skv_inf_warpfire_thrower` | Special | 1 |
| Skaven | `wh3_dlc29_skv_inf_deathvermin_ror` | Special | 1 |
| Skaven | `wh2_dlc12_skv_art_warplock_jezzails_ror_tech_lab_0` | Special | 2 |
| Skaven | `wh2_dlc12_skv_inf_plague_monk_censer_bearer_ror_0` | Special | 2 |
| Skaven | `wh2_dlc12_skv_inf_warplock_jezzails_0` | Special | 2 |
| Skaven | `wh2_dlc12_skv_inf_warplock_jezzails_ror_0` | Special | 2 |
| Skaven | `wh2_dlc12_skv_veh_doom_flayer_0` | Special | 2 |
| Skaven | `wh2_dlc12_skv_veh_doom_flayer_ror_0` | Special | 2 |
| Skaven | `wh2_dlc12_skv_veh_doom_flayer_ror_tech_lab_0` | Special | 2 |
| Skaven | `wh2_dlc14_skv_inf_death_runners_ror_0` | Special | 2 |
| Skaven | `wh2_dlc14_skv_inf_poison_wind_mortar_0` | Special | 2 |
| Skaven | `wh2_dlc14_skv_inf_poison_wind_mortar_ror_0` | Special | 2 |
| Skaven | `wh2_dlc16_skv_mon_rat_ogres_ror_0` | Special | 2 |
| Skaven | `wh2_main_skv_inf_plague_monk_censer_bearer` | Special | 2 |
| Skaven | `wh2_main_skv_inf_poison_wind_globadiers` | Special | 2 |
| Skaven | `wh2_main_skv_mon_rat_ogres` | Special | 2 |
| Skaven | `wh2_dlc16_skv_mon_rat_ogre_mutant` | Special | 3 |
| Skaven | `wh2_dlc16_skv_mon_rat_ogre_mutant_flesh_lab` | Special | 3 |
| Skaven | `wh2_dlc16_skv_mon_rat_ogre_mutant_ror_0` | Special | 3 |
| Skaven | `wh3_dlc29_skv_mon_stormfiend_doomflayer_gauntlets` | Special | 3 |
| Skaven | `wh3_dlc29_skv_mon_stormfiend_grinderfists` | Special | 3 |
| Skaven | `wh3_dlc29_skv_mon_stormfiend_ratling_cannons` | Special | 3 |
| Skaven | `wh3_dlc29_skv_mon_stormfiend_shock_gauntlets` | Special | 3 |
| Skaven | `wh3_dlc29_skv_mon_stormfiend_warpfire_projectors` | Special | 3 |
| Skaven | `wh3_dlc29_skv_mon_stormfiend_windlaunchers` | Special | 3 |
| Skaven | `wh3_dlc29_skv_mon_stormfiends_ratling_cannons_ror` | Special | 3 |
| Skaven | `wh2_main_skv_art_plagueclaw_catapult` | Rare | 1 |
| Skaven | `wh2_main_skv_inf_death_globe_bombardiers` | Rare | 1 |
| Skaven | `wh3_dlc29_skv_art_plagueclaw_catapult_ror` | Rare | 1 |
| Skaven | `wh2_dlc12_skv_art_warp_lightning_cannon_ror_0` | Rare | 2 |
| Skaven | `wh2_dlc12_skv_veh_doomwheel_ror_0` | Rare | 2 |
| Skaven | `wh2_dlc12_skv_veh_doomwheel_ror_tech_lab_0` | Rare | 2 |
| Skaven | `wh2_dlc16_skv_mon_brood_horror_0` | Rare | 2 |
| Skaven | `wh2_dlc16_skv_mon_brood_horror_0_flesh_lab` | Rare | 2 |
| Skaven | `wh2_main_skv_art_warp_lightning_cannon` | Rare | 2 |
| Skaven | `wh2_main_skv_veh_doomwheel` | Rare | 2 |
| Skaven | `wh3_dlc29_skv_art_warp_doom_magma_cannon` | Rare | 2 |
| Skaven | `wh3_dlc29_skv_veh_cauldron_of_a_thousand_poxes` | Rare | 2 |
| Skaven | `wh2_dlc16_skv_mon_hell_pit_abomination_flesh_lab` | Rare | 3 |
| Skaven | `wh2_dlc16_skv_mon_hell_pit_abomination_ror_0` | Rare | 3 |
| Skaven | `wh2_main_skv_mon_hell_pit_abomination` | Rare | 3 |
| Slaanesh | `wh3_main_sla_cav_hellstriders_0` | Core | - |
| Slaanesh | `wh3_main_sla_cav_hellstriders_1` | Core | - |
| Slaanesh | `wh3_main_sla_inf_daemonette_0` | Core | - |
| Slaanesh | `wh3_main_sla_inf_marauders_0` | Core | - |
| Slaanesh | `wh3_main_sla_inf_marauders_1` | Core | - |
| Slaanesh | `wh3_main_sla_inf_marauders_2` | Core | - |
| Slaanesh | `wh3_twa10_sla_inf_marauders_spears_ror` | Core | - |
| Slaanesh | `wh3_dlc27_sla_inf_chaos_furies_dechala` | Special | 1 |
| Slaanesh | `wh3_dlc27_sla_inf_devotees_of_slaanesh` | Special | 1 |
| Slaanesh | `wh3_dlc27_sla_inf_slaangors` | Special | 1 |
| Slaanesh | `wh3_dlc27_sla_veh_seeker_chariot_ror` | Special | 1 |
| Slaanesh | `wh3_main_sla_inf_chaos_furies_0` | Special | 1 |
| Slaanesh | `wh3_main_sla_veh_seeker_chariot_0` | Special | 1 |
| Slaanesh | `wh3_dlc27_sla_inf_daemonette_1_dechala` | Special | 2 |
| Slaanesh | `wh3_dlc27_sla_inf_devotees_of_slaanesh_crossbows` | Special | 2 |
| Slaanesh | `wh3_dlc27_sla_mon_fiends_of_slaanesh_dechala` | Special | 2 |
| Slaanesh | `wh3_main_sla_cav_seekers_of_slaanesh_0` | Special | 2 |
| Slaanesh | `wh3_main_sla_inf_daemonette_1` | Special | 2 |
| Slaanesh | `wh3_main_sla_mon_fiends_of_slaanesh_0` | Special | 2 |
| Slaanesh | `wh3_twa06_sla_inf_daemonette_ror_0` | Special | 2 |
| Slaanesh | `wh3_dlc27_sla_mon_champions_of_slaanesh` | Special | 3 |
| Slaanesh | `wh3_dlc27_sla_mon_champions_of_slaanesh_ror` | Special | 3 |
| Slaanesh | `wh3_dlc27_sla_mon_spawn_of_slaanesh_0` | Rare | 1 |
| Slaanesh | `wh3_main_sla_mon_spawn_of_slaanesh_0` | Rare | 1 |
| Slaanesh | `wh3_dlc27_sla_cav_heartseekers_of_slaanesh_dechala` | Rare | 2 |
| Slaanesh | `wh3_dlc27_sla_cav_pleasureseekers` | Rare | 2 |
| Slaanesh | `wh3_dlc27_sla_cav_pleasureseekers_dechala` | Rare | 2 |
| Slaanesh | `wh3_dlc27_sla_mon_preyton` | Rare | 2 |
| Slaanesh | `wh3_dlc27_sla_mon_preyton_monst_arcanum` | Rare | 2 |
| Slaanesh | `wh3_dlc27_sla_mon_preyton_monst_arcanum_reward` | Rare | 2 |
| Slaanesh | `wh3_dlc27_sla_mon_preyton_ror` | Rare | 2 |
| Slaanesh | `wh3_dlc27_sla_veh_exalted_seeker_chariot_dechala` | Rare | 2 |
| Slaanesh | `wh3_main_sla_cav_heartseekers_of_slaanesh_0` | Rare | 2 |
| Slaanesh | `wh3_main_sla_mon_soul_grinder_0` | Rare | 2 |
| Slaanesh | `wh3_main_sla_veh_exalted_seeker_chariot_0` | Rare | 2 |
| Slaanesh | `wh3_main_sla_veh_hellflayer_0` | Rare | 2 |
| Slaanesh | `wh3_twa07_sla_cav_heartseekers_of_slaanesh_ror_0` | Rare | 2 |
| Slaanesh | `wh3_dlc27_sla_mon_keeper_of_secrets_dechala` | Rare | 3 |
| Slaanesh | `wh3_main_sla_mon_keeper_of_secrets_0` | Rare | 3 |
| Slaanesh | `wh3_twa08_sla_mon_keeper_of_secrets_0_ror` | Rare | 3 |
| Tomb Kings | `wh2_dlc09_tmb_cav_skeleton_horsemen_0` | Core | - |
| Tomb Kings | `wh2_dlc09_tmb_cav_skeleton_horsemen_archers_0` | Core | - |
| Tomb Kings | `wh2_dlc09_tmb_inf_crypt_ghouls` | Core | - |
| Tomb Kings | `wh2_dlc09_tmb_inf_nehekhara_warriors_0` | Core | - |
| Tomb Kings | `wh2_dlc09_tmb_inf_skeleton_archers_0` | Core | - |
| Tomb Kings | `wh2_dlc09_tmb_inf_skeleton_archers_ror` | Core | - |
| Tomb Kings | `wh2_dlc09_tmb_inf_skeleton_spearmen_0` | Core | - |
| Tomb Kings | `wh2_dlc09_tmb_inf_skeleton_spearmen_ror` | Core | - |
| Tomb Kings | `wh2_dlc09_tmb_inf_skeleton_warriors_0` | Core | - |
| Tomb Kings | `wh2_dlc09_tmb_inf_spirit_host` | Core | - |
| Tomb Kings | `wh2_dlc09_tmb_mon_dire_wolves` | Core | - |
| Tomb Kings | `wh2_dlc09_tmb_mon_fell_bats` | Core | - |
| Tomb Kings | `wh2_dlc09_tmb_veh_skeleton_archer_chariot_0` | Core | - |
| Tomb Kings | `wh2_dlc09_tmb_veh_skeleton_chariot_0` | Core | - |
| Tomb Kings | `wh2_dlc09_tmb_cav_nehekhara_horsemen_0` | Special | 1 |
| Tomb Kings | `wh2_dlc09_tmb_cav_nehekhara_horsemen_ror` | Special | 1 |
| Tomb Kings | `wh2_dlc09_tmb_inf_nehekhara_warriors_ror` | Special | 1 |
| Tomb Kings | `wh2_dlc09_tmb_inf_tomb_guard_0` | Special | 1 |
| Tomb Kings | `wh2_dlc09_tmb_inf_tomb_guard_1` | Special | 1 |
| Tomb Kings | `wh2_dlc09_tmb_inf_tomb_guard_ror` | Special | 1 |
| Tomb Kings | `wh2_dlc09_tmb_mon_carrion_0` | Special | 1 |
| Tomb Kings | `wh2_dlc09_tmb_mon_carrion_ror` | Special | 1 |
| Tomb Kings | `wh3_dlc27_tmb_mon_carrion_monst_arcanum` | Special | 1 |
| Tomb Kings | `wh2_dlc09_tmb_cav_hexwraiths` | Special | 2 |
| Tomb Kings | `wh2_dlc09_tmb_cav_necropolis_knights_0` | Special | 2 |
| Tomb Kings | `wh2_dlc09_tmb_cav_necropolis_knights_1` | Special | 2 |
| Tomb Kings | `wh2_dlc09_tmb_cav_necropolis_knights_ror` | Special | 2 |
| Tomb Kings | `wh2_dlc09_tmb_mon_crypt_horrors` | Special | 2 |
| Tomb Kings | `wh2_dlc09_tmb_mon_sepulchral_stalkers_0` | Special | 2 |
| Tomb Kings | `wh2_dlc09_tmb_mon_sepulchral_stalkers_ror` | Special | 2 |
| Tomb Kings | `wh2_dlc09_tmb_mon_ushabti_0` | Special | 2 |
| Tomb Kings | `wh2_dlc09_tmb_mon_ushabti_1` | Special | 2 |
| Tomb Kings | `wh2_dlc09_tmb_mon_ushabti_ror` | Special | 2 |
| Tomb Kings | `wh3_dlc29_tmb_mon_ushabti_ror_sepulchrex` | Special | 2 |
| Tomb Kings | `wh2_dlc09_tmb_mon_morghast_archai` | Special | 3 |
| Tomb Kings | `wh2_dlc09_tmb_mon_morghast_harbingers` | Special | 3 |
| Tomb Kings | `wh2_dlc09_tmb_art_casket_of_souls_0` | Rare | 1 |
| Tomb Kings | `wh2_dlc09_tmb_art_screaming_skull_catapult_0` | Rare | 1 |
| Tomb Kings | `wh2_dlc09_tmb_inf_cairn_wraiths` | Rare | 1 |
| Tomb Kings | `wh2_dlc09_tmb_mon_tomb_scorpion_0` | Rare | 1 |
| Tomb Kings | `wh2_dlc09_tmb_veh_khemrian_warsphinx_0` | Rare | 2 |
| Tomb Kings | `wh2_pro06_tmb_mon_bone_giant_0` | Rare | 2 |
| Tomb Kings | `wh2_dlc09_tmb_mon_heirotitan_0` | Rare | 3 |
| Tomb Kings | `wh2_dlc09_tmb_mon_necrosphinx_0` | Rare | 3 |
| Tomb Kings | `wh2_dlc09_tmb_mon_necrosphinx_ror` | Rare | 3 |
| Tomb Kings | `wh3_dlc29_tmb_mon_khemric_titan` | Rare | 3 |
| Tomb Kings | `wh3_dlc29_tmb_mon_khemric_titan_ror` | Rare | 3 |
| Tzeentch | `wh3_dlc24_tze_inf_pink_horrors_ror` | Core | - |
| Tzeentch | `wh3_main_tze_inf_blue_horrors_0` | Core | - |
| Tzeentch | `wh3_main_tze_inf_forsaken_0` | Core | - |
| Tzeentch | `wh3_main_tze_inf_pink_horrors_0` | Core | - |
| Tzeentch | `wh3_twa10_tze_inf_blue_horrors_ror` | Core | - |
| Tzeentch | `wh3_dlc24_tze_inf_tzaangors` | Special | 1 |
| Tzeentch | `wh3_dlc24_tze_mon_screamers_ror` | Special | 1 |
| Tzeentch | `wh3_main_tze_inf_chaos_furies_0` | Special | 1 |
| Tzeentch | `wh3_main_tze_mon_screamers_0` | Special | 1 |
| Tzeentch | `wh3_main_tze_cav_chaos_knights_0` | Special | 2 |
| Tzeentch | `wh3_main_tze_inf_pink_horrors_1` | Special | 2 |
| Tzeentch | `wh3_main_tze_mon_flamers_0` | Special | 2 |
| Tzeentch | `wh3_twa06_tze_inf_pink_horrors_ror_0` | Special | 2 |
| Tzeentch | `wh3_dlc24_tze_inf_centigors_great_weapons` | Rare | 1 |
| Tzeentch | `wh3_dlc27_tze_mon_spawn_of_tzeentch_0` | Rare | 1 |
| Tzeentch | `wh3_main_tze_mon_spawn_of_tzeentch_0` | Rare | 1 |
| Tzeentch | `wh3_dlc24_tze_mon_cockatrice` | Rare | 2 |
| Tzeentch | `wh3_dlc24_tze_mon_flamers_changebringers` | Rare | 2 |
| Tzeentch | `wh3_dlc27_tze_mon_cockatrice_monst_arcanum` | Rare | 2 |
| Tzeentch | `wh3_dlc27_tze_mon_cockatrice_monst_arcanum_reward` | Rare | 2 |
| Tzeentch | `wh3_main_tze_cav_doom_knights_0` | Rare | 2 |
| Tzeentch | `wh3_main_tze_mon_exalted_flamers_0` | Rare | 2 |
| Tzeentch | `wh3_main_tze_mon_soul_grinder_0` | Rare | 2 |
| Tzeentch | `wh3_main_tze_veh_burning_chariot_0` | Rare | 2 |
| Tzeentch | `wh3_twa07_tze_cav_doom_knights_ror_0` | Rare | 2 |
| Tzeentch | `wh3_dlc24_tze_mon_mutalith_vortex_beast` | Rare | 3 |
| Tzeentch | `wh3_dlc24_tze_mon_mutalith_vortex_beast_ror` | Rare | 3 |
| Tzeentch | `wh3_main_tze_mon_lord_of_change_0` | Rare | 3 |
| Tzeentch | `wh3_twa08_tze_mon_lord_of_change_0_ror` | Rare | 3 |
| Vampire Coast | `wh2_dlc11_cst_cav_knights_errant_0` | Core | - |
| Vampire Coast | `wh2_dlc11_cst_cav_knights_errant_1` | Core | - |
| Vampire Coast | `wh2_dlc11_cst_cav_knights_errant_2` | Core | - |
| Vampire Coast | `wh2_dlc11_cst_cav_knights_of_the_realm` | Core | - |
| Vampire Coast | `wh2_dlc11_cst_inf_sartosa_free_company_0` | Core | - |
| Vampire Coast | `wh2_dlc11_cst_inf_sartosa_militia_0` | Core | - |
| Vampire Coast | `wh2_dlc11_cst_inf_zombie_deckhands_mob_0` | Core | - |
| Vampire Coast | `wh2_dlc11_cst_inf_zombie_deckhands_mob_1` | Core | - |
| Vampire Coast | `wh2_dlc11_cst_inf_zombie_deckhands_mob_ror_0` | Core | - |
| Vampire Coast | `wh2_dlc11_cst_inf_zombie_gunnery_mob_0` | Core | - |
| Vampire Coast | `wh2_dlc11_cst_inf_zombie_gunnery_mob_1` | Core | - |
| Vampire Coast | `wh2_dlc11_cst_inf_zombie_gunnery_mob_2` | Core | - |
| Vampire Coast | `wh2_dlc11_cst_inf_zombie_gunnery_mob_3` | Core | - |
| Vampire Coast | `wh2_dlc11_cst_mon_bloated_corpse_0` | Core | - |
| Vampire Coast | `wh2_dlc11_cst_mon_fell_bats` | Core | - |
| Vampire Coast | `wh2_dlc11_cst_mon_scurvy_dogs` | Core | - |
| Vampire Coast | `wh2_dlc11_cst_cav_deck_droppers_0` | Special | 1 |
| Vampire Coast | `wh2_dlc11_cst_cav_deck_droppers_1` | Special | 1 |
| Vampire Coast | `wh2_dlc11_cst_cav_deck_droppers_2` | Special | 1 |
| Vampire Coast | `wh2_dlc11_cst_cav_deck_droppers_ror_0` | Special | 1 |
| Vampire Coast | `wh2_dlc11_cst_inf_deck_gunners_0` | Special | 1 |
| Vampire Coast | `wh2_dlc11_cst_inf_deck_gunners_ror_0` | Special | 1 |
| Vampire Coast | `wh2_dlc11_cst_inf_zombie_gunnery_mob_ror_0` | Special | 1 |
| Vampire Coast | `wh2_dlc11_cst_mon_animated_hulks_0` | Special | 1 |
| Vampire Coast | `wh2_dlc11_cst_art_carronade` | Special | 2 |
| Vampire Coast | `wh2_dlc11_cst_art_mortar` | Special | 2 |
| Vampire Coast | `wh2_dlc11_cst_cav_questing_knights_0` | Special | 2 |
| Vampire Coast | `wh2_dlc11_cst_inf_depth_guard_0` | Special | 2 |
| Vampire Coast | `wh2_dlc11_cst_inf_depth_guard_1` | Special | 2 |
| Vampire Coast | `wh2_dlc11_cst_inf_depth_guard_ror_0` | Special | 2 |
| Vampire Coast | `wh2_dlc11_cst_inf_syreens` | Special | 2 |
| Vampire Coast | `wh2_dlc11_cst_mon_rotting_prometheans_0` | Special | 2 |
| Vampire Coast | `wh2_dlc11_cst_mon_rotting_prometheans_gunnery_mob_0` | Special | 2 |
| Vampire Coast | `wh2_dlc11_cst_mon_rotting_prometheans_gunnery_mob_ror` | Special | 2 |
| Vampire Coast | `wh2_dlc11_cst_mon_mournguls_0` | Rare | 1 |
| Vampire Coast | `wh2_dlc11_cst_mon_mournguls_ror_0` | Rare | 1 |
| Vampire Coast | `wh2_dlc11_cst_art_queen_bess` | Rare | 2 |
| Vampire Coast | `wh2_dlc11_cst_mon_necrofex_colossus_0` | Rare | 3 |
| Vampire Coast | `wh2_dlc11_cst_mon_necrofex_colossus_ror_0` | Rare | 3 |
| Vampire Coast | `wh2_dlc11_cst_mon_rotting_leviathan_0` | Rare | 3 |
| Vampire Coast | `wh2_dlc11_cst_mon_terrorgheist` | Rare | 3 |
| Vampire Counts | `wh3_dlc29_vmp_inf_skeleton_warriors_0_raise_legion` | Core | - |
| Vampire Counts | `wh3_dlc29_vmp_inf_skeleton_warriors_0_raise_legion_upgraded` | Core | - |
| Vampire Counts | `wh3_dlc29_vmp_inf_skeleton_warriors_0_the_awakening` | Core | - |
| Vampire Counts | `wh3_dlc29_vmp_inf_spirit_host` | Core | - |
| Vampire Counts | `wh3_dlc29_vmp_inf_zombies_raise_legion` | Core | - |
| Vampire Counts | `wh_dlc04_vmp_inf_feasters_in_the_dusk_0` | Core | - |
| Vampire Counts | `wh_dlc04_vmp_inf_konigstein_stalkers_0` | Core | - |
| Vampire Counts | `wh_dlc04_vmp_inf_tithe_0` | Core | - |
| Vampire Counts | `wh_dlc04_vmp_mon_direpack_0` | Core | - |
| Vampire Counts | `wh_main_vmp_inf_crypt_ghouls` | Core | - |
| Vampire Counts | `wh_main_vmp_inf_skeleton_warriors_0` | Core | - |
| Vampire Counts | `wh_main_vmp_inf_skeleton_warriors_1` | Core | - |
| Vampire Counts | `wh_main_vmp_inf_zombie` | Core | - |
| Vampire Counts | `wh_main_vmp_mon_dire_wolves` | Core | - |
| Vampire Counts | `wh_main_vmp_mon_fell_bats` | Core | - |
| Vampire Counts | `wh2_dlc11_vmp_inf_crossbowmen` | Special | 1 |
| Vampire Counts | `wh3_dlc29_vmp_inf_grave_guard_0_the_awakening` | Special | 1 |
| Vampire Counts | `wh3_dlc29_vmp_inf_grave_guard_1_the_awakening` | Special | 1 |
| Vampire Counts | `wh3_dlc29_vmp_inf_grave_guard_2_the_awakening` | Special | 1 |
| Vampire Counts | `wh3_main_vmp_inf_grave_guard_2` | Special | 1 |
| Vampire Counts | `wh_dlc04_vmp_inf_sternsmen_0` | Special | 1 |
| Vampire Counts | `wh_main_vmp_inf_grave_guard_0` | Special | 1 |
| Vampire Counts | `wh_main_vmp_inf_grave_guard_1` | Special | 1 |
| Vampire Counts | `wh3_dlc29_vmp_cav_drakenhof_templars` | Special | 2 |
| Vampire Counts | `wh3_dlc29_vmp_inf_lahmian_handmaidens_death` | Special | 2 |
| Vampire Counts | `wh3_dlc29_vmp_inf_lahmian_handmaidens_shadow` | Special | 2 |
| Vampire Counts | `wh_dlc04_vmp_cav_chillgheists_0` | Special | 2 |
| Vampire Counts | `wh_dlc04_vmp_cav_vereks_reavers_0` | Special | 2 |
| Vampire Counts | `wh_dlc04_vmp_mon_devils_swartzhafen_0` | Special | 2 |
| Vampire Counts | `wh_dlc04_vmp_veh_corpse_cart_0` | Special | 2 |
| Vampire Counts | `wh_main_vmp_cav_black_knights_0` | Special | 2 |
| Vampire Counts | `wh_main_vmp_cav_black_knights_3` | Special | 2 |
| Vampire Counts | `wh_main_vmp_cav_hexwraiths` | Special | 2 |
| Vampire Counts | `wh_main_vmp_mon_crypt_horrors` | Special | 2 |
| Vampire Counts | `wh_main_vmp_mon_vargheists` | Special | 2 |
| Vampire Counts | `wh3_dlc29_vmp_mon_morghast_archai` | Special | 3 |
| Vampire Counts | `wh3_dlc29_vmp_mon_morghast_archai_ror` | Special | 3 |
| Vampire Counts | `wh3_dlc29_vmp_mon_morghast_harbingers` | Special | 3 |
| Vampire Counts | `wh_dlc04_vmp_veh_corpse_cart_1` | Special | 3 |
| Vampire Counts | `wh_dlc04_vmp_veh_corpse_cart_2` | Special | 3 |
| Vampire Counts | `wh2_dlc11_vmp_inf_handgunners` | Rare | 1 |
| Vampire Counts | `wh_main_vmp_inf_cairn_wraiths` | Rare | 1 |
| Vampire Counts | `wh3_dlc29_vmp_veh_coven_throne` | Rare | 2 |
| Vampire Counts | `wh3_main_vmp_blood_knights_sword_shield` | Rare | 2 |
| Vampire Counts | `wh_dlc02_vmp_cav_blood_knights_0` | Rare | 2 |
| Vampire Counts | `wh_main_vmp_mon_varghulf` | Rare | 2 |
| Vampire Counts | `wh_main_vmp_veh_black_coach` | Rare | 2 |
| Vampire Counts | `wh3_dlc29_vmp_mon_zombie_dragon` | Rare | 3 |
| Vampire Counts | `wh_dlc04_vmp_veh_claw_of_nagash_0` | Rare | 3 |
| Vampire Counts | `wh_dlc04_vmp_veh_mortis_engine_0` | Rare | 3 |
| Vampire Counts | `wh_main_vmp_mon_terrorgheist` | Rare | 3 |
| Warriors of Chaos | `wh3_dlc20_chs_cav_chaos_chariot_mkho` | Core | - |
| Warriors of Chaos | `wh3_dlc20_chs_cav_chaos_chariot_mnur` | Core | - |
| Warriors of Chaos | `wh3_dlc20_chs_cav_chaos_chariot_msla` | Core | - |
| Warriors of Chaos | `wh3_dlc20_chs_cav_chaos_chariot_msla_ror` | Core | - |
| Warriors of Chaos | `wh3_dlc20_chs_cav_chaos_chariot_mtze` | Core | - |
| Warriors of Chaos | `wh3_dlc20_chs_cav_marauder_horsemen_mkho_throwing_axes` | Core | - |
| Warriors of Chaos | `wh3_dlc20_chs_cav_marauder_horsemen_mnur_throwing_axes` | Core | - |
| Warriors of Chaos | `wh3_dlc20_chs_cav_marauder_horsemen_msla_javelins` | Core | - |
| Warriors of Chaos | `wh3_dlc20_chs_cav_marauder_horsemen_mtze_javelins` | Core | - |
| Warriors of Chaos | `wh3_dlc20_chs_inf_chaos_marauders_mkho` | Core | - |
| Warriors of Chaos | `wh3_dlc20_chs_inf_chaos_marauders_mkho_dualweapons` | Core | - |
| Warriors of Chaos | `wh3_dlc20_chs_inf_chaos_marauders_mnur` | Core | - |
| Warriors of Chaos | `wh3_dlc20_chs_inf_chaos_marauders_mnur_greatweapons` | Core | - |
| Warriors of Chaos | `wh3_dlc20_chs_inf_chaos_marauders_msla` | Core | - |
| Warriors of Chaos | `wh3_dlc20_chs_inf_chaos_marauders_msla_hellscourges` | Core | - |
| Warriors of Chaos | `wh3_dlc20_chs_inf_chaos_marauders_mtze` | Core | - |
| Warriors of Chaos | `wh3_dlc20_chs_inf_chaos_marauders_mtze_spears` | Core | - |
| Warriors of Chaos | `wh3_dlc20_chs_inf_chaos_warriors_mnur` | Core | - |
| Warriors of Chaos | `wh3_dlc20_chs_inf_chaos_warriors_mnur_greatweapons` | Core | - |
| Warriors of Chaos | `wh3_dlc20_chs_inf_chaos_warriors_msla` | Core | - |
| Warriors of Chaos | `wh3_dlc20_chs_inf_chaos_warriors_msla_hellscourges` | Core | - |
| Warriors of Chaos | `wh3_dlc20_chs_inf_chaos_warriors_mtze` | Core | - |
| Warriors of Chaos | `wh3_dlc20_chs_inf_chaos_warriors_mtze_halberds` | Core | - |
| Warriors of Chaos | `wh3_dlc20_chs_inf_forsaken_mkho` | Core | - |
| Warriors of Chaos | `wh3_dlc20_chs_inf_forsaken_msla` | Core | - |
| Warriors of Chaos | `wh3_dlc27_chs_inf_chaos_warriors_0` | Core | - |
| Warriors of Chaos | `wh3_dlc27_chs_inf_chaos_warriors_1` | Core | - |
| Warriors of Chaos | `wh3_dlc27_chs_inf_chaos_warriors_2` | Core | - |
| Warriors of Chaos | `wh3_dlc27_chs_inf_chaos_warriors_mnur_greatweapons` | Core | - |
| Warriors of Chaos | `wh3_dlc27_chs_inf_chaos_warriors_msla_hellscourges` | Core | - |
| Warriors of Chaos | `wh3_dlc27_chs_inf_chaos_warriors_mtze_halberds` | Core | - |
| Warriors of Chaos | `wh3_dlc29_chs_inf_flayerkin` | Core | - |
| Warriors of Chaos | `wh_dlc01_chs_inf_chaos_warriors_2` | Core | - |
| Warriors of Chaos | `wh_dlc01_chs_inf_forsaken_0` | Core | - |
| Warriors of Chaos | `wh_dlc06_chs_cav_marauder_horsemasters_0` | Core | - |
| Warriors of Chaos | `wh_main_chs_cav_chaos_chariot` | Core | - |
| Warriors of Chaos | `wh_main_chs_cav_marauder_horsemen_0` | Core | - |
| Warriors of Chaos | `wh_main_chs_cav_marauder_horsemen_1` | Core | - |
| Warriors of Chaos | `wh_main_chs_inf_chaos_marauders_0` | Core | - |
| Warriors of Chaos | `wh_main_chs_inf_chaos_marauders_1` | Core | - |
| Warriors of Chaos | `wh_main_chs_inf_chaos_warriors_0` | Core | - |
| Warriors of Chaos | `wh_main_chs_inf_chaos_warriors_1` | Core | - |
| Warriors of Chaos | `wh_main_chs_mon_chaos_warhounds_0` | Core | - |
| Warriors of Chaos | `wh_main_chs_mon_chaos_warhounds_1` | Core | - |
| Warriors of Chaos | `wh_pro04_chs_inf_chaos_warriors_ror_0` | Core | - |
| Warriors of Chaos | `wh_pro04_chs_inf_forsaken_ror_0` | Core | - |
| Warriors of Chaos | `wh_dlc01_chs_cav_gorebeast_chariot` | Special | 1 |
| Warriors of Chaos | `wh_dlc01_chs_mon_trolls_1` | Special | 1 |
| Warriors of Chaos | `wh_main_chs_mon_trolls` | Special | 1 |
| Warriors of Chaos | `wh3_dlc20_chs_cav_chaos_knights_mkho` | Special | 2 |
| Warriors of Chaos | `wh3_dlc20_chs_cav_chaos_knights_mkho_lances` | Special | 2 |
| Warriors of Chaos | `wh3_dlc20_chs_cav_chaos_knights_mnur` | Special | 2 |
| Warriors of Chaos | `wh3_dlc20_chs_cav_chaos_knights_mnur_lances` | Special | 2 |
| Warriors of Chaos | `wh3_dlc20_chs_cav_chaos_knights_msla` | Special | 2 |
| Warriors of Chaos | `wh3_dlc20_chs_cav_chaos_knights_msla_lances` | Special | 2 |
| Warriors of Chaos | `wh3_dlc20_chs_cav_chaos_knights_mtze_lances` | Special | 2 |
| Warriors of Chaos | `wh3_dlc20_chs_inf_aspiring_champions_mtze_ror` | Special | 2 |
| Warriors of Chaos | `wh3_dlc20_chs_inf_chosen_mkho` | Special | 2 |
| Warriors of Chaos | `wh3_dlc20_chs_inf_chosen_mkho_dualweapons` | Special | 2 |
| Warriors of Chaos | `wh3_dlc20_chs_inf_chosen_mnur` | Special | 2 |
| Warriors of Chaos | `wh3_dlc20_chs_inf_chosen_mnur_greatweapons` | Special | 2 |
| Warriors of Chaos | `wh3_dlc20_chs_inf_chosen_msla` | Special | 2 |
| Warriors of Chaos | `wh3_dlc20_chs_inf_chosen_msla_hellscourges` | Special | 2 |
| Warriors of Chaos | `wh3_dlc20_chs_inf_chosen_mtze` | Special | 2 |
| Warriors of Chaos | `wh3_dlc20_chs_inf_chosen_mtze_halberds` | Special | 2 |
| Warriors of Chaos | `wh3_dlc20_chs_mon_warshrine` | Special | 2 |
| Warriors of Chaos | `wh3_dlc20_chs_mon_warshrine_mkho` | Special | 2 |
| Warriors of Chaos | `wh3_dlc20_chs_mon_warshrine_mnur` | Special | 2 |
| Warriors of Chaos | `wh3_dlc20_chs_mon_warshrine_msla` | Special | 2 |
| Warriors of Chaos | `wh3_dlc20_chs_mon_warshrine_mtze` | Special | 2 |
| Warriors of Chaos | `wh3_dlc26_chs_inf_chosen_mkho_ror` | Special | 2 |
| Warriors of Chaos | `wh3_dlc27_chs_feral_manticore_monst_arcanum` | Special | 2 |
| Warriors of Chaos | `wh3_dlc27_chs_feral_manticore_monst_arcanum_reward` | Special | 2 |
| Warriors of Chaos | `wh3_dlc29_chs_inf_chosen_mnur_ror` | Special | 2 |
| Warriors of Chaos | `wh3_dlc29_chs_inf_putrid_blightkings_axe_shield` | Special | 2 |
| Warriors of Chaos | `wh3_dlc29_chs_inf_putrid_blightkings_dual_axe` | Special | 2 |
| Warriors of Chaos | `wh3_dlc29_chs_inf_putrid_blightkings_dual_axe_ror` | Special | 2 |
| Warriors of Chaos | `wh3_dlc29_chs_inf_putrid_blightkings_great_weapons` | Special | 2 |
| Warriors of Chaos | `wh_dlc01_chs_inf_chosen_2` | Special | 2 |
| Warriors of Chaos | `wh_dlc01_chs_mon_dragon_ogre` | Special | 2 |
| Warriors of Chaos | `wh_dlc06_chs_feral_manticore` | Special | 2 |
| Warriors of Chaos | `wh_dlc06_chs_inf_aspiring_champions_0` | Special | 2 |
| Warriors of Chaos | `wh_main_chs_cav_chaos_knights_0` | Special | 2 |
| Warriors of Chaos | `wh_main_chs_cav_chaos_knights_1` | Special | 2 |
| Warriors of Chaos | `wh_main_chs_inf_chosen_0` | Special | 2 |
| Warriors of Chaos | `wh_main_chs_inf_chosen_1` | Special | 2 |
| Warriors of Chaos | `wh_pro04_chs_cav_chaos_knights_ror_0` | Special | 2 |
| Warriors of Chaos | `wh_pro04_chs_mon_dragon_ogre_ror_0` | Special | 2 |
| Warriors of Chaos | `wh3_dlc27_chs_mon_chaos_spawn` | Rare | 1 |
| Warriors of Chaos | `wh_main_chs_mon_chaos_spawn` | Rare | 1 |
| Warriors of Chaos | `wh_pro04_chs_mon_chaos_spawn_ror_0` | Rare | 1 |
| Warriors of Chaos | `wh3_dlc20_chs_mon_giant_mnur_ror` | Rare | 2 |
| Warriors of Chaos | `wh3_dlc27_woc_mon_chimera_ror` | Rare | 2 |
| Warriors of Chaos | `wh3_dlc29_chs_mon_basilisk` | Rare | 2 |
| Warriors of Chaos | `wh3_dlc29_chs_mon_giant_spined_chaos_beast` | Rare | 2 |
| Warriors of Chaos | `wh3_dlc29_chs_mon_giant_spined_chaos_beast_ror` | Rare | 2 |
| Warriors of Chaos | `wh_main_chs_art_hellcannon` | Rare | 2 |
| Warriors of Chaos | `wh_main_chs_mon_giant` | Rare | 2 |
| Warriors of Chaos | `wh_pro04_chs_art_hellcannon_ror_0` | Rare | 2 |
| Warriors of Chaos | `wh3_dlc27_chs_mon_dragon_ogre_shaggoth_monst_arcanum_reward` | Rare | 3 |
| Warriors of Chaos | `wh3_dlc29_chs_mon_chaos_siege_giant` | Rare | 3 |
| Warriors of Chaos | `wh_dlc01_chs_mon_dragon_ogre_shaggoth` | Rare | 3 |
| Wood Elves | `wh2_dlc16_wef_cav_glade_riders_2` | Core | - |
| Wood Elves | `wh2_dlc16_wef_inf_dryads_ror_0` | Core | - |
| Wood Elves | `wh2_dlc16_wef_inf_malicious_dryads_0` | Core | - |
| Wood Elves | `wh2_dlc16_wef_mon_cave_bats` | Core | - |
| Wood Elves | `wh2_dlc16_wef_mon_spider_hatchlings_0` | Core | - |
| Wood Elves | `wh_dlc05_wef_cav_glade_riders_0` | Core | - |
| Wood Elves | `wh_dlc05_wef_cav_glade_riders_1` | Core | - |
| Wood Elves | `wh_dlc05_wef_inf_dryads_0` | Core | - |
| Wood Elves | `wh_dlc05_wef_inf_eternal_guard_0` | Core | - |
| Wood Elves | `wh_dlc05_wef_inf_eternal_guard_1` | Core | - |
| Wood Elves | `wh_dlc05_wef_inf_glade_guard_0` | Core | - |
| Wood Elves | `wh_dlc05_wef_inf_glade_guard_1` | Core | - |
| Wood Elves | `wh_dlc05_wef_inf_glade_guard_2` | Core | - |
| Wood Elves | `wh_pro04_wef_inf_eternal_guard_ror_0` | Core | - |
| Wood Elves | `wh2_dlc16_wef_mon_giant_spiders_0` | Special | 1 |
| Wood Elves | `wh2_dlc16_wef_mon_harpies_0` | Special | 1 |
| Wood Elves | `wh2_dlc16_wef_mon_hawks_0` | Special | 1 |
| Wood Elves | `wh2_dlc16_wef_mon_wolves_0` | Special | 1 |
| Wood Elves | `wh_dlc05_wef_inf_deepwood_scouts_0` | Special | 1 |
| Wood Elves | `wh_dlc05_wef_inf_deepwood_scouts_1` | Special | 1 |
| Wood Elves | `wh_dlc05_wef_inf_wardancers_0` | Special | 1 |
| Wood Elves | `wh_dlc05_wef_inf_wardancers_1` | Special | 1 |
| Wood Elves | `wh_pro04_wef_inf_wardancers_ror_0` | Special | 1 |
| Wood Elves | `wh2_dlc16_wef_inf_bladesingers_0` | Special | 2 |
| Wood Elves | `wh2_dlc16_wef_mon_feral_manticore` | Special | 2 |
| Wood Elves | `wh2_dlc16_wef_mon_gwindalor_summoned` | Special | 2 |
| Wood Elves | `wh2_dlc16_wef_mon_malicious_treekin_0` | Special | 2 |
| Wood Elves | `wh_dlc05_wef_cav_hawk_riders_0` | Special | 2 |
| Wood Elves | `wh_dlc05_wef_cav_wild_riders_0` | Special | 2 |
| Wood Elves | `wh_dlc05_wef_cav_wild_riders_1` | Special | 2 |
| Wood Elves | `wh_dlc05_wef_inf_wildwood_rangers_0` | Special | 2 |
| Wood Elves | `wh_dlc05_wef_mon_great_eagle_0` | Special | 2 |
| Wood Elves | `wh_dlc05_wef_mon_treekin_0` | Special | 2 |
| Wood Elves | `wh_pro04_wef_cav_wild_riders_ror_0` | Special | 2 |
| Wood Elves | `wh_pro04_wef_inf_wildwood_rangers_ror_0` | Special | 2 |
| Wood Elves | `wh_pro04_wef_mon_treekin_ror_0` | Special | 2 |
| Wood Elves | `wh2_dlc16_wef_cav_great_stag_knights_0` | Rare | 1 |
| Wood Elves | `wh2_dlc16_wef_mon_zoats` | Rare | 1 |
| Wood Elves | `wh2_dlc16_wef_mon_zoats_ror_0` | Rare | 1 |
| Wood Elves | `wh_dlc05_wef_cav_sisters_thorn_0` | Rare | 1 |
| Wood Elves | `wh_dlc05_wef_inf_waywatchers_0` | Rare | 1 |
| Wood Elves | `wh_pro04_wef_inf_waywatchers_ror_0` | Rare | 1 |
| Wood Elves | `wh2_dlc16_wef_cav_great_stag_knights_ror_0` | Rare | 2 |
| Wood Elves | `wh2_dlc16_wef_mon_ceithin_har_summoned` | Rare | 3 |
| Wood Elves | `wh2_dlc16_wef_mon_malicious_treeman_0` | Rare | 3 |
| Wood Elves | `wh_dlc05_wef_forest_dragon_0` | Rare | 3 |
| Wood Elves | `wh_dlc05_wef_mon_treeman_0` | Rare | 3 |
