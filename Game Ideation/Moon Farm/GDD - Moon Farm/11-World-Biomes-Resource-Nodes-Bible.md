
## 🔹 Biome Design Goals

- **Exploration Depth:** Each biome feels unique, visually and mechanically.
- **Resource Loop:** Players are incentivized to travel for rare crafting materials.
- **Hazard & Wildlife Integration:** Each biome has passive wildlife and occasional enemy hazards.
- **Seasonal Layering:** Tileset palette swaps (snow in winter, vibrant in spring, etc.).
- **Player Guidance:** Progression-based unlock (tools, stamina, mounts).

## 🌍 Biome Overview Table

| **Biome Name**  | **Theme & Visuals**    | **Player Progression Level** | **Key Features** |
| --------------- | ---------------------- | ---------------------------- | --------------- |
| **1. Farmstead** | Player's central hub; green fields, fences. | Starter Area | Home, barn, coop, first tools. |
| **2. Meadowlands** | Rolling grass hills, flowers, rivers. | Early Game | Basic forage, starter mining node. |
| **3. Whispering Woods** | Dense forest, mist FX, magical lighting. | Early-Mid | Rare forage, intro wildlife hazard. |
| **4. Crystal Lake** | Lake biome with crystalline water. | Mid-Game | Fishing hub, water-based crafting. |
| **5. Ember Caverns** | Underground magma caves, glowing crystals. | Mid-High | Rare ores, lava hazards. |
| **6. Frostpeaks** | Snowy tundra, ice cliffs, Aurora skies. | High Game | Endgame wildlife & shrine unlocks. |
| **7. Moonlit Ruins** | Ancient ruins, glowing plants, magical FX. | High-End | Legendary crafting mats, boss tier. |

## 🔹 Biome Detailed Specs

#### 1. Farmstead (Starter Zone)

| **Category**        | **Details** |
| ------------------- | ----------- |
| **Visual Notes**    | Rolling hills, wooden fences, dirt paths, starter crops. Day-night cycle visible from the house window. |
| **Resources**       | Weeds, stones, tree stumps, starter wildflowers (Daisy, Sun Petal), firewood. |
| **Wildlife**        | Chickens, sparrows, butterflies (decorative). |
| **Hazards**         | None. |
| **Player Purpose**  | Introduces farming mechanics, animal care, basic crafting. |
| **Unique Asset Requirements** | Custom farmhouse tileset (3 seasonal variants), small decorative props (buckets, tools). |

#### 2. Meadowlands

| **Category**    | **Details** |
| --------------- | ----------- |
| **Visual Notes** | Open fields, long grass sway animations, wildflower patches. |
| **Resources**   | Fiber, herbs, Tier 1 ore nodes, common fish. |
| **Wildlife**    | Rabbits, fox (rare). |
| **Hazards**     | Slime puddles (slow debuff). |
| **Unique Nodes** | Beehives (Honey resource), Wild Berry Bushes. |
| **Player Purpose** | Early exploration, first forage items, introduction to basic enemies. |
| **Asset Notes** | Soft pastel grass colors, seasonal flower palette swap. |

#### 3. Whispering Woods

| **Category**    | **Details** |
| --------------- | ----------- |
| **Visual Notes** | Darker palette, shafts of sunlight, magical mushrooms glow at night. |
| **Resources**   | Mushrooms, rare wood, magic herbs. |
| **Wildlife**    | Owls, deer, rare spirit fox. |
| **Hazards**     | Thorn brambles (HP damage), forest wisps (stun attack). |
| **Nodes**       | Enchanted Tree Stump (rare wood), Glowcap Mushrooms (night only). |
| **Purpose**     | First magical resources, higher stamina requirement. |
| **Asset Notes** | Parallax forest layers, glowing particle FX. |

#### 4. Crystal Lake

| **Category**    | **Details** |
| --------------- | ----------- |
| **Visual Notes** | Sparkling water, glowing crystals along shore, lilypads, water reflections. |
| **Resources**   | Fish (tier 2), lotus flower, water crystals. |
| **Wildlife**    | Frogs, koi fish, dragonflies. |
| **Hazards**     | Water slimes, whirlpools (pull effect). |
| **Nodes**       | Water Crystal Shards, Rare Fish Spots. |
| **Purpose**     | Fishing and potion-based crafting expansion. |
| **Asset Notes** | Water shader with ripples, reflection map, glowing edge crystals. |

#### 5. Ember Caverns

| **Category**    | **Details** |
| --------------- | ----------- |
| **Visual Notes** | Red/orange hue, lava rivers, glowing crystals, ash particle FX. |
| **Resources**   | Tier 3 ores (Mythril, Sunstone), Lava Pearls. |
| **Wildlife**    | Fire bats, magma slimes. |
| **Hazards**     | Lava pools, collapsing rock paths, heat damage over time. |
| **Nodes**       | Magma Crystal Cluster, Molten Ore Vein. |
| **Purpose**     | High-tier mining, crafting fire-element gear. |
| **Asset Notes** | Animated lava tiles, glowing cracks in floor, smoke layers. |

#### 6. Frostpeaks

| **Category**    | **Details** |
| --------------- | ----------- |
| **Visual Notes** | Blue-white palette, auroras in the sky, snow FX, icy cliff terrain. |
| **Resources**   | Frost Lotus, Ice Crystals, Blizzard Fish. |
| **Wildlife**    | Polar owls, snow hares, frost wolves. |
| **Hazards**     | Ice tiles (slip mechanic), blizzard storms (visibility reduction). |
| **Nodes**       | Ice Shards, Frozen Shrines. |
| **Purpose**     | Unlock late-game shrines, cold survival gear progression. |
| **Asset Notes** | Aurora shader pass, snow footprints, particle blizzards. |

#### 7. Moonlit Ruins

| **Category**    | **Details** |
| --------------- | ----------- |
| **Visual Notes** | Bioluminescent plants, glowing ruins, moonlight filters. |
| **Resources**   | Moonstone, Starflower, Ancient Runes. |
| **Wildlife**    | Spirit stag, magical creatures, endgame boss. |
| **Hazards**     | Cursed fog (HP drain), ruin guardians (melee AI). |
| **Nodes**       | Ancient Rune Pillars, Moonstone Cluster. |
| **Purpose**     | Endgame magical gear, rare pets, story climax area. |
| **Asset Notes** | Neon glow palette, animated runes, particle FX trails. |

## 🔹 Resource Node Master Table

| **Node Name**  | **Biome**     | **Tool Required** | **Respawn Rate** | **Drops** |
| -------------- | ------------- | ---------------- | --------------- | --------- |
| Stone Pile     | Farmstead, Meadow | Pickaxe Lv1      | 1 day           | Stone x3, Pebble x1 |
| Ore Vein (Iron) | Meadow, Caverns | Pickaxe Lv1      | 2 days          | Iron Ore x3-5 |
| Ore Vein (Mythril) | Caverns       | Pickaxe Lv2      | 3 days          | Mythril Ore x2-4 |
| Magma Crystal Cluster | Caverns    | Pickaxe Lv3      | 4 days          | Magma Crystal x1, Lava Pearl (rare) |
| Ice Shard Cluster | Frostpeaks  | Pickaxe Lv2      | 3 days          | Ice Shard x3, Frozen Essence (rare) |
| Moonstone Cluster | Moonlit Ruins | Pickaxe Lv3      | 5 days          | Moonstone x1-2, Ancient Dust |
| Herb Patch     | Meadow, Woods | Sickle Lv1       | 1 day           | Herbs (Common, Rare), Flower Seeds |
| Mushroom Ring  | Woods         | Hands            | 2 days          | Glowcap Mushroom, Fairy Cap (rare) |
| Lotus Pond     | Crystal Lake  | Fishing Rod      | 2 days          | Lotus Flower, Water Crystal |
| Beehive        | Meadow        | Hands/Smoke      | 3 days          | Honeycomb, Royal Jelly (rare) |
| Ancient Rune Pillar | Moonlit Ruins | Rune Key        | Static          | Rune Fragment x1 |

## 🔹 Hazards System Table

| **Hazard Type** | **Biome**     | **Mechanic**                 | **Damage/Effect** |
| --------------- | ------------- | ---------------------------- | ----------------- |
| Slime Puddle    | Meadowlands   | Slows movement by 40%.       | No direct damage. |
| Thorn Brambles  | Woods         | Deals chip damage, knocks back. | 5 HP per hit. |
| Lava Pool       | Caverns       | Contact burns, HP drain over time. | 20 HP/sec. |
| Blizzard Storm  | Frostpeaks    | Reduces visibility, drains stamina. | 10 stamina/sec. |
| Cursed Fog      | Ruins         | HP drain aura, lowers accuracy. | 10 HP/sec. |

---
**Back to:** [[Moon Farming GDD]]
