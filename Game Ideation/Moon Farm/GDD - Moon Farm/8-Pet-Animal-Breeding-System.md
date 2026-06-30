
## 8.1. Overview

- **Purpose:**
  - Provide a mid- and late-game economy driver.
  - Give players deeper progression through genetics and customization.
  - Add emotional attachment via pets that assist in farming/fishing.
- **Core Philosophy:** Animals should feel **alive and unique**. Breeding is rewarding but not overly grindy. Pets are companions, while livestock drives economy.

## 8.2. Animal Categories

| **Category**   | **Examples**                   | **Primary Use** |
| -------------- | ------------------------------ | --------------- |
| **Farm Animals** | Chickens, cows, sheep, goats, pigs, ducks, rabbits | Milk, eggs, wool, truffles, breeding for profit |
| **Exotic Animals** | Alpacas, peacocks, bees, reindeer, koi fish | Rare goods (festival unlocks) |
| **Pets**       | Dog, cat, fox, owl, turtle     | Utility (herding, pest control, carrying items) |
| **Mounts**     | Horses, llamas                 | Travel, racing mini-games |

## 8.3. Animal Acquisition

| **Method**           | **Description** |
| -------------------- | --------------- |
| Purchase from Vendor | Basic animals at the ranch shop (chickens, cows, sheep). |
| Breeding             | Combine traits to produce unique offspring. |
| Exploration/Quests   | Exotic animals as quest rewards. |
| Festivals            | Seasonal livestock competitions unlock rare breeds. |
| Taming               | Some pets/mounts can be tamed in the wild. |

## 8.4. Housing & Ranch Design

| **Building**    | **Capacity**        | **Upgrade Benefits** |
| --------------- | ------------------- | -------------------- |
| Coop            | 4 → 8 animals       | Automatic feeders, incubator. |
| Barn            | 4 → 12 animals      | Auto-cleaners, larger storage. |
| Stable          | 1 → 2 mounts        | Saddle storage, racing training. |
| Aviary          | 2 → 6 birds         | Bird nesting boxes. |
| Exotic Habitat  | Varies (per animal) | Unlockable via Sage Luma's quests. |
| Pet House       | 1 → 3 pets          | Grooming station, pet toys. |

**Art Notes:** Barn/coop exteriors evolve visually with upgrades. Interiors show animals' personalities (toys, bedding, name tags).

## 8.5. Animal Lifecycle

| **Stage**   | **Duration (In-Game Days)** | **Notes** |
| ----------- | --------------------------- | --------- |
| Baby        | 3 days                      | Needs bottle feeding or warmth. |
| Juvenile    | 4 days                      | Cannot breed; limited produce. |
| Adult       | Infinite                    | Produces resources, can breed. |
| Elder       | Cosmetic only               | Stops breeding; still produces. |

## 8.6. Care Mechanics

- **Daily Needs:** Food, petting, cleaning stalls.
- **Mood Meter:** Impacts production rate.
  - **Happy:** Extra items, higher breeding chance.
  - **Neutral:** Normal production.
  - **Sad:** Refuses to produce.
- **Food System:**
  - Seasonal crops → Animal-specific treats.
  - Special festival foods boost breeding traits.

## 8.7. Breeding System (Core)

| **Mechanic**    | **Specification** |
| --------------- | ----------------- |
| Breeding Pen    | Building upgrade required for pairing animals. |
| Gestation Period | 3–5 in-game days. |
| Trait Inheritance | Dominant/recessive gene system for traits. |
| Breeding Cooldown | 5 in-game days post-birth per parent. |
| Crossbreeding   | Certain animals unlock hybrid variants (e.g., Peacock × Duck → Exotic Plumage Duck). |

#### Trait System

Each animal has **5 trait slots**:

1. **Size** (Small, Medium, Large)
2. **Coat/Color** (Multiple palettes per breed)
3. **Temperament** (Friendly, Shy, Aggressive)
4. **Production Quality** (Normal, Silver, Gold, Moonstone)
5. **Special Trait** (Rare: Glowing Wool, Extra-Large Eggs, etc.)

| **Trait Type**    | **Effect** |
| ----------------- | ---------- |
| Size              | Determines feeding needs, product size. |
| Coat/Color        | Cosmetic, drives collection system. |
| Temperament       | Impacts ease of training pets/mounts. |
| Production Quality | Higher sale price, better crafting inputs. |
| Special Trait     | Unique gameplay bonuses (e.g., Moonlight Wool glows at night). |

## 8.8. Genetic Algorithm (For Devs)

**Algorithm Flow:**

1. Select two parent animals.
2. Each trait has **70% chance** to inherit one parent's trait, **20% mutation chance**, **10% random new trait**.
3. If both parents share a trait, offspring inherits it guaranteed.
4. Mutation table defines rare coat patterns or traits (Festival exclusive).

## 8.9. Pet Utility System

| **Pet**   | **Unique Abilities** |
| --------- | -------------------- |
| Dog       | Herd livestock, fetch dropped tools. |
| Cat       | Controls barn pests, occasionally gifts items. |
| Owl       | Delivers player mail, acts as quest notifier. |
| Turtle    | Protects crops from pests; slow but tanky companion. |
| Fox       | Can locate hidden forageables in forest. |

Pets can **gain XP** via activities:

- **Level 1–3:** Basic utility.
- **Level 4–5:** Special abilities (fetch rare loot, assist fishing).
- XP earned by interaction, feeding, minigames.

## 8.10. Festivals & Competitions

- **Livestock Show:** Judge animals based on mood, coat rarity, production stats.
- **Racing Tournaments:** Mount racing with skill-based minigame.
- **Pet Trick Festival:** Pets compete in skill events (fetch, agility).
- Rewards: Unique cosmetics, rare foods, exclusive breeding tokens.

## 8.11. Art & Animation Specs

| **Asset Type**        | **Notes** |
| --------------------- | --------- |
| Baby/Adult Models     | Each animal has **3 LOD models** (baby, adult, elder). |
| Coat Variants         | Use **shader-based recolors** for performance efficiency. |
| Idle Animations       | Each animal has **3 idle loops** (eat, sleep, wander). |
| Interaction Animations | Unique animation for petting, grooming, feeding. |
| Pet Gear              | Simple attachable meshes (collars, saddles, toys). |

## 8.12. Player Progression Integration

- Early Game: Basic animals only (chickens, cows).
- Mid Game: Unlock breeding pens, genetics system, exotic animals.
- Late Game: Pets/mounts provide **utility boosts**, exotic animals unlock rare crafting recipes.
- Economy Loop:
  1. Breed → Sell rare variants.
  2. Use rare produce for **artisan goods**.
  3. Drive high-value crafting economy.

---
**Back to:** [[Moon Farming GDD]]
