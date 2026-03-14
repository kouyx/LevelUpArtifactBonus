# Hero LevelUp Artifact Bonus (Full Remake)

Inspired by bismarck2 (level-up artifact bonus idea)
Author: MoonHeart

## Changelog

### v1.4 (2026-03-14)
- Replaced the artifact RNG implementation with a time-based generator; reloading a save may produce different outcomes.
- Switched to built-in i18n text and removed hardcoded popup strings; script files are now saved in UTF-8.

### v1.3 (2026-01-02)
- Pools are now divided by hero level instead of experience, improving selection during consecutive level-ups: previously only the final level's pool was used; now each level-up draws from the pool matching the level gained.
- Heroes that start the game at a high level (map presets, tavern recruits, etc.) no longer trigger the level-up artifact reward. Only heroes who gain levels through normal in-game experience after the game start can trigger the mechanism.

### v1.2 (2025-12-31)
- Duplicate prevention improved: if a hero already has the artifact equipped or in their backpack, a new artifact will be re-randomized; if no new artifact can be found, the fallback artifact "Hourglass of the Evil Hour" is granted.

### v1.1 (2025-12-15)
- Refactored numeric function names (FU9999–FU9995) to descriptive names to improve readability.
- Removed Fire Magic Book (ID: 86) from all pools.

## Core Function
When a hero levels up, they automatically receive a random artifact. Artifact quality is chosen from level-based pools, and only whitelisted artifact IDs are eligible to ensure predictable, mod-friendly rewards.

## Major Changes (Rework >90%)
1. Replaced "blacklist exclusion" with a whitelist approach: only specified artifact IDs can be drawn, avoiding invalid or conflicting rewards.
2. Added `FU(grand_master_lv_up_bonus)` to complete five tiered pools (`FU(basic_lv_up_bonus)` → `FU(grand_master_lv_up_bonus)`), covering early to endgame.
3. Consolidated continuous ID ranges (single points and intervals) and added full annotations for artifact names and source mods.
4. Revised level-to-pool mapping: Lv1–9 → `FU(basic_lv_up_bonus)`, Lv10–19 → `FU(advanced_lv_up_bonus)`, Lv20–28 → `FU(expert_lv_up_bonus)`, Lv29–39 → `FU(master_lv_up_bonus)`, Lv40+ → `FU(grand_master_lv_up_bonus)`.
5. Improved compatibility with ERA 3.0+, WoG 3.58f+, Advanced Classes Mod v1.094a, and Third Upgrade Mod Reborn v1.7.3.

## Trigger Conditions
Requires WoG Map Rule 15 (custom script on hero level-up). The script runs automatically on level-up; human players receive a popup, while AI players receive artifacts silently.

## Artifact Pool Design (Restrictions & Exceptions)
### Excluded categories
- Adventure-map magic artifacts (Earth/Water/Air Books, Magic Hat) — avoid teleport/fly/return effects.
- Battlefield magic artifacts (Armageddon's Blade, Seer's Boots, Warlock's Ring, Mage's Robe, Mage's Staff, Elemental Ring) — prevent battlefield magic imbalance.
- Movement-altering artifacts (Water Walking Boots, Wings, Sea Cap) — avoid changing exploration pacing.
- Components for artifact combinations (most shields, top-tier combination components, Balloon, Earth/Fire Orbs, Titan components) — avoid enabling rapid formation of powerful combination artifacts.
- Directly awarding completed combined artifacts — prevent one-step acquisition of top-tier sets.
- Artifacts that add/remove battlefield restrictions (War Shackles, Anti-Magic Orb, Cloak of Silence, Orb of Annihilation, immunity artifacts) — preserve core battlefield rules.
- Single overpowered artifacts (Class Sets, Ogre's Fist, rare one-piece artifacts) — avoid major balance shifts.

### Exceptions
- Some battlefield magic artifacts such as a few opening-spell artifacts (weak or basic effects) are allowed.
- Allowed combination exceptions: Golden Goose, Binoculars, Diplomat's Cloak, Horn of Plenty, Forest Lord's Robe.

## Pool Mapping
- `FU(basic_lv_up_bonus)` (Lv1–9): Novice basic artifacts (mainly common artifacts).
- `FU(advanced_lv_up_bonus)` (Lv10–19): Low-to-mid tier (common + some Third Upgrade Mod items).
- `FU(expert_lv_up_bonus)` (Lv20–28): Mid-tier (common + WoG + Third Upgrade Mod items).
- `FU(master_lv_up_bonus)` (Lv29–39): High-mid tier (high-tier common + commander + Third Upgrade items).
- `FU(grand_master_lv_up_bonus)` (Lv40+): Endgame top-tier (top-tier common + rare artifacts from various mods).

## Notes
1. Artifacts are automatically equipped to the hero—ensure they have empty slots available.
2. Artifact ID range is 7–289; IDs outside the whitelist are re-randomized until a whitelist hit is found.
3. Re-randomization attempts cap at 100; if none succeed, the Doom Sandglass (Hourglass of the Evil Hour) is granted as a fallback.
