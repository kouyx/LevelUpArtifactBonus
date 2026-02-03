# Hero LevelUp Artifact Bonus (Full Remake)

Inspired by: bismarck2 (level-up with artifact bonus idea)
Author: MoonHeart

## changelog

### v1.3(2026/01/02)

1. The basis for dividing the level-up reward artifact pools has been adjusted from experience points to hero levels, optimizing the pool selection logic for consecutive level-ups: the original mechanism only drew from the pool corresponding to the final level, while now it draws from the pool matching the new level of each individual level-up;
2. Initial high-level heroes (including scenarios with initial high experience such as map presets and tavern recruitment) will no longer trigger the level-up artifact reward mechanism. Only heroes who level up by normally gaining experience points after the game starts can activate this mechanism.

### v1.2(2025/12/31)

1. Optimization of duplicate prevention for level-up reward artifacts: If the hero has already equipped with the artifact or owns it in the backpack, a new random artifact will be reallocated; if no brand-new artifact can be obtained, the guaranteed artifact "Hourglass of the Evil Hour" will be granted.

### v1.1(2025/12/15)

1. **Semantic function name refactoring**: Changed numeric function names (FU9999-FU9995) to descriptive names, improving code readability
2. **Artifact pool adjustments**: Removed Fire Magic Book (ID:86) from all pools

## Core Function
Heroes automatically receive random artifact rewards when leveling up. Different quality artifact pools are matched based on level gradients, and only artifacts in the whitelist take effect, ensuring controllable rewards and adaptation to the mod ecosystem.

## Core Remake Changes (Over 90% of Content Reconstructed)
1. Rule Reconstruction: Abandon the original "blacklist exclusion" logic and switch to "whitelist access" — only artifacts with specified IDs can be drawn, avoiding invalid/conflicting artifact distribution;
2. Pool Expansion: Add the FU(grand_master_lv_up_bonus) pool to complete 5 gradient pools (FU(basic_lv_up_bonus)~FU(grand_master_lv_up_bonus)), covering the full growth cycle from novice to endgame;
3. Format Optimization: Fully merge all continuous artifact ID intervals (single point + single point/single point + interval/interval + interval) without split intervals, with complete annotations for artifact names and affiliated mods;
4. Experience Gradient Adjustment: New level-experience matching rules (Lv1-9/FU(basic_lv_up_bonus), Lv10-19/FU(advanced_lv_up_bonus), Lv20-28/FU(expert_lv_up_bonus), Lv29-39/FU(master_lv_up_bonus), Lv40+/FU(grand_master_lv_up_bonus)) to adapt to the hero growth curve;
5. Compatibility Enhancement: Perfectly compatible with ERA 3.0+, WoG 3.58f+, Advanced Classes Mod v1.094a, and Third Upgrade Mod Reborn v1.7.3.

## Trigger Conditions
WoG Map Rule 15 (Custom script triggers on hero level up) must be enabled. The script triggers automatically after hero leveling up — only human players receive pop-up prompts, while AI players get artifacts normally without prompts.

## Artifact Pool Design Principles (Core Restrictions & Exceptions)
### Prohibited Categories (Not Included in Pools)
- Artifacts adding adventure map magic: Earth Book, Water Book, Air Book, Magic Hat (avoid triggering unbalanced magic like Teleport/Fly/Return);
- Artifacts enhancing battlefield magic: Armageddon's Blade, Seer's Boots, Warlock's Ring, Mage's Robe, Mage's Staff, Elemental Ring (prevent battlefield magic imbalance);
- Artifacts modifying adventure map movement mode: Water Walking Boots, Wings, Sea Cap (alter map exploration rhythm and strategy);
- Components/items for combining artifacts: Most shields, highest-tier components of combined artifacts, Balloon, Earth Orb, Fire Orb, Titan Components (avoid rapid formation of powerful artifacts via rewards);
- Direct rewards of complete combined artifacts: Prevent one-step acquisition of top-tier combined sets to maintain progression rhythm;
- Artifacts adding/removing battlefield restrictions: War Shackles, Anti-Magic Orb, Cloak of Silence, Orb of Annihilation, Elemental Immunity Artifacts (distort core battlefield rules);
- Overpowered single artifacts: Class Sets, Ogre's Fist, Rare Artifacts (drastically change combat balance with one piece).

### Exception Categories (Included in Pools)
- Battlefield magic exceptions: Fire Book, some artifacts with opening spells (basic functions or weak effects that don't break balance);
- Combination exceptions: Golden Goose, Binoculars, Diplomat's Cloak, Horn of Plenty, Forest Lord's Robe.

## Artifact Pool Rules
- FU(basic_lv_up_bonus) (Lv1-9): Novice basic artifacts (mainly normal artifacts);
- FU(advanced_lv_up_bonus) (Lv10-19): Transitional low-to-medium artifacts (normal + a small number of Third Upgrade Mod artifacts);
- FU(expert_lv_up_bonus) (Lv20-28): Developmental mid-tier artifacts (normal + WoG + Third Upgrade Mod artifacts);
- FU(master_lv_up_bonus) (Lv29-39): Mature high-to-medium artifacts (high-tier normal + Commander + Third Upgrade Mod artifacts);
- FU(grand_master_lv_up_bonus) (Lv40+): Endgame high-tier artifacts (top-tier normal + rare artifacts from all mods).

## Notes
1. All artifacts are automatically equipped to the hero after distribution — ensure the hero has empty slots in the corresponding equipment bar;
2. The random range of artifacts is 7-289; IDs not in the whitelist will be re-randomized to ensure 100% valid artifact distribution;
3. The maximum number of re-randomization attempts for non-whitelist IDs is 100. If the limit is reached without hitting the whitelist, the Doom Sandglass will be awarded (also an easter egg).