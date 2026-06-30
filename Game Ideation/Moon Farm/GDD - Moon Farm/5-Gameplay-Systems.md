
## 5.1. Player Character System

**Overview:**
The player character is fully customizable and serves as the central avatar in the game world.

**Features:**

- Gender-neutral body base with customizable hair, facial features, outfits.
- Animations: Walking, running, farming, fishing, interacting, emoting.
- Player **stamina** and **energy** systems.

**Stats & Attributes:**

| **Stat**   | **Description**                | **Impact** |
| ---------- | ------------------------------ | ---------- |
| **Stamina** | Represents daily energy to farm, mine, fish. | Each action consumes stamina; rest recovers. |
| **Health**  | Used only in hazardous areas (e.g., mines). | Dropping to 0 teleports player home. |
| **Speed**   | Movement speed, affected by upgrades. | Equipment/boots can slightly boost speed. |

**Customization Options:**

- Hair (10 starter styles; unlockable via salon).
- Clothing sets (seasonal outfits, workwear, festival clothes).
- Accessories: Glasses, hats, backpacks.

## 5.2. Farming System

**Core Mechanics:**
Players transform and expand farmland over time. Farming includes soil prep, planting, watering, fertilizing, harvesting, and selling crops.

#### 5.2.1. Tools & Tiers

| **Tool**      | **Base Use**       | **Tier Upgrades**        | **Upgrade Materials** |
| ------------- | ------------------ | ------------------------ | --------------------- |
| Hoe           | Tills one soil tile | Bronze, Silver, Gold, Moonsteel | Ore bars, gems |
| Watering Can  | Waters crops       | Bronze+ (water more tiles) | Ore bars, gems |
| Axe           | Chops trees, stumps | Bronze+ (faster chop)    | Ore bars |
| Pickaxe       | Breaks rocks, ore nodes | Bronze+ (mine faster)    | Ore bars |
| Sickle        | Harvests grass     | Bronze+ (wider range)    | Ore bars |

#### 5.2.2. Crop Growth

- Each crop has **growth stages** (Seed → Sprout → Mature).
- **Growth Days**: 3–12 days depending on crop.
- **Seasons:** Crops are seasonal; planting out-of-season kills crops.
- **Watering:** Crops must be watered daily unless it rains or automated sprinklers are installed.
- **Fertilizers:** Boost growth speed or crop quality.

**Example Crop Table:**

| **Crop Name** | **Season** | **Growth Days** | **Regrowth** | **Sell Price (Base)** | **Notes** |
| ------------- | ---------- | --------------- | ------------ | --------------------- | --------- |
| Turnip        | Spring     | 4               | No           | 60                    | Fast starter crop |
| Strawberry    | Spring     | 8               | Yes (3d)     | 120                   | Popular repeat-harvest crop |
| Moon Blossom  | Summer     | 12              | No           | 500                   | Rare, glows at night |
| Pumpkin       | Fall       | 10              | No           | 300                   | Large, used in festivals |
| Winter Root   | Winter     | 6               | No           | 150                   | Found in snowy biomes |

#### 5.2.3. Soil Health System

- Crops deplete soil quality over time.
- Soil quality tiers: Poor → Normal → Fertile → Rich.
- Using fertilizers and rotating crops improves soil.
- Optional system toggle for casual players (default: ON).

#### 5.2.4. Farm Expansion

- Players unlock additional fields, orchards, greenhouses, and decorative landscaping through town investment and quest milestones.
- Player farm evolves visually (fences, paths, lighting) to show progress.

## 5.3. Animal System

**Animal Categories:**

| **Animal** | **Housing** | **Product** | **Breed Variants** | **Notes** |
| ---------- | ----------- | ----------- | ------------------ | --------- |
| Chicken    | Coop        | Eggs        | Brown/White        | Beginner animal |
| Cow        | Barn        | Milk        | Standard/Spotted   | Produces daily |
| Sheep      | Barn        | Wool        | White/Black        | Wool every 3 days |
| Goat       | Barn        | Goat Milk   | Standard           | Smaller barns, rare milk cheese |
| Rabbit     | Coop        | Wool/Fur    | Color variants     | Produces fur randomly |
| Moon Deer  | Large Barn  | Moon Antlers | Rare              | Magical late-game creature |

**Key Systems:**

- **Happiness Level:**
  - Scale: 0–100.
  - Affects product quality and breeding success.
  - Raised by feeding, petting, clean housing.
- **Breeding:**
  - Two animals of same type can breed after reaching happiness threshold.
  - Chance for rare coat colors or magical traits.
- **Feeding & Care:**
  - Hay or pasture grass; automatic feeders unlock later.
- **Weather Impact:**
  - Winter: Must keep animals inside with heaters.
  - Summer: Shade structures reduce stress.

## 5.4. Fishing System

**Overview:**
Fishing is a relaxing, skill-based mini-game with varied fish types per biome, weather, and time of day.

**Mechanics:**

- Player casts line, waits for bite, enters a timing-based reel mechanic.
- Higher-level rods allow fishing in new zones (deep sea, rare lakes).

**Fish Table Example:**

| **Fish Name** | **Season** | **Location**     | **Time** | **Sell Price** | **Notes** |
| ------------- | ---------- | ---------------- | -------- | -------------- | --------- |
| River Trout   | Spring     | Rivers           | Day      | 80             | Common starter fish |
| Golden Carp   | Summer     | Lakes            | Morning  | 200            | Mid-game fish |
| Moon Eel      | Fall       | Ocean (Full Moon) | Night    | 500            | Rare, lunar event fish |

## 5.5. Foraging & Gathering

**Core Mechanics:**

- Collect wild herbs, mushrooms, and seasonal flowers.
- Rare resources spawn in hard-to-reach areas or under specific weather conditions.
- Foraged goods can be eaten, sold, or used in crafting/quests.

**Seasonal Examples:**

| **Item**           | **Season** | **Location**    | **Use** |
| ------------------ | ---------- | --------------- | ------- |
| Spring Blossom     | Spring     | Forest          | Gift item, crafting decoration |
| Firecap Mushroom   | Summer     | Mountain Caves  | Cooking recipe ingredient |
| Frostberry         | Winter     | Snowy Plains    | Stamina recovery, festival dish |

## 5.6. Mining System

**Purpose:**
Mining provides ores, gems, and crafting materials. It also ties into exploration and narrative progression.

**Structure:**

- Mines are **multi-floor dungeons** with increasing difficulty.
- Some floors contain unique resources, hidden lore, or puzzles.
- Randomized floor layouts for replayability.

#### 5.6.1. Floors & Progression

| **Floor Range** | **Environment Theme** | **Primary Resources** | **Hazards/Enemies** |
| --------------- | --------------------- | --------------------- | ------------------- |
| 1–20            | Shallow Caverns       | Stone, Copper Ore     | Small rock crabs    |
| 21–40           | Crystal Caves         | Iron Ore, Quartz      | Bats                |
| 41–60           | Lava Depths           | Gold Ore, Fire Crystals | Lava slimes, falling rocks |
| 61–80           | Moonlit Abyss         | Moonsteel Ore, Rare Gems | Shadow creatures (late-game) |

#### 5.6.2. Mining Mechanics

- **Pickaxe Upgrades:** Unlock deeper floors.
- **Energy Cost:** Each rock hit consumes stamina.
- **Enemy Encounters:** Simple combat or avoidance (optional for casual players via difficulty toggle).
- **Elevator System:** Unlocks every 5 floors for quick travel.
- **Treasure Rooms:** Contain rare seeds, crafting blueprints, or artifacts.

## 5.7. Weather & Seasons

**Core Concept:**
Weather dynamically affects farming, fishing, and NPC behavior. Seasons change the game's look, soundtrack, and available resources.

#### 5.7.1. Weather Types

| **Weather** | **Effects** |
| ----------- | ----------- |
| Sunny       | Normal day. All outdoor activities available. |
| Rainy       | Crops auto-watered. Some fish only appear in rain. |
| Stormy      | Higher chance of rare materials washing ashore. |
| Snowy       | Winter-only. Slower movement outdoors without gear. |
| Foggy       | Rare. Hidden forest paths revealed. |
| Full Moon   | Unlocks special crops/creatures. Happens 3 times a year. |

#### 5.7.2. Seasonal Themes

| **Season** | **Visual Tone**        | **Gameplay Highlights** |
| ---------- | ---------------------- | ----------------------- |
| Spring     | Pastel greens, blossoms | Starter crops, new animals, introductory festivals |
| Summer     | Bright, lush colors    | Rare ocean fish, heat events, high-value crops |
| Fall       | Warm tones, falling leaves | Abundant foraging, harvest festivals |
| Winter     | White landscapes       | Mining focus, winter animals, slower farm activity |

## 5.8. Day/Night Cycle

**Purpose:**
The in-game day-night cycle sets pace and adds strategy to time management.

| **In-Game Time**      | **Real-Time Duration** | **Effects** |
| --------------------- | ---------------------- | ----------- |
| Morning (6AM–12PM)    | ~7.5 mins              | NPCs wake up, shops open at 9AM |
| Afternoon (12PM–6PM)  | ~7.5 mins              | Peak outdoor activity |
| Evening (6PM–12AM)    | ~7.5 mins              | Shops close, nightlife NPC schedules |
| Late Night (12AM–2AM) | ~3 mins                | Player faints at 2AM if awake |

- **1 In-Game Day ≈ 25 minutes real-time.**
- Shops operate from **9AM–6PM**; festivals override shop schedules.
- Night lighting and ambiance are dynamic.

## 5.9. Calendar & Festivals

**Calendar Structure:**

- **12 months** in a year, 4 seasons, 28 days per season.
- **Festivals:** 2–3 per season, encouraging community engagement.
- **Birthdays:** NPC birthdays listed on calendar (affects friendship gain).

#### Example Festival List

| **Season** | **Festival Name**    | **Date** | **Theme** |
| ---------- | -------------------- | -------- | --------- |
| Spring     | Flower Dance         | Day 14   | Dance competition, rare flower shop |
| Summer     | Ocean Lights Festival | Day 21   | Lantern release, ocean fishing contest |
| Fall       | Harvest Celebration  | Day 28   | Crop competition, cooking mini-game |
| Winter     | Moonlight Eve        | Day 24   | Rare moon seeds, gifting tradition |

## 5.10. Housing & Farm Upgrades

**Player Housing Progression:**

| **Upgrade Level** | **Features**                   | **Cost** |
| ----------------- | ------------------------------ | -------- |
| Cabin (Default)   | Single room, basic bed, chest. | Free (starting house). |
| Cottage           | Kitchen unlocks cooking.       | 10,000g, 200 wood, 100 stone |
| Farmhouse         | Large storage, customizable rooms. | 25,000g, 400 wood, 150 stone |
| Estate            | Max size, guest rooms, trophy hall | 50,000g, luxury materials |

**Farm Buildings:**

| **Building** | **Purpose**                 | **Upgrade Path** |
| ------------ | --------------------------- | ---------------- |
| Coop         | Houses chickens, rabbits.   | Coop → Big Coop → Deluxe Coop |
| Barn         | Houses cows, goats, sheep.  | Barn → Big Barn → Deluxe Barn |
| Greenhouse   | Year-round farming.         | Unlocked mid-game via quest. |
| Shed         | Storage and workshop.       | Basic Shed → Deluxe Shed |
| Mill         | Process wheat and other crops. | One-time construction. |
| Silo         | Stores hay.                 | Expandable with cost. |

## 5.11. Crafting System

**Purpose:**
Crafting is the backbone of player progression, providing tools, furniture, farm structures, and consumables. It motivates exploration (for materials) and farming (to produce raw goods).

#### 5.11.1. Crafting Mechanics

- **Workbench Required:** All crafting occurs at a workbench (available at player's house).
- **Categories:** Tools, Farm Equipment, Furniture, Decor, Materials, and Consumables.
- **Blueprint System:**
  - Players unlock recipes via quests, festivals, shop purchases, or NPC friendship milestones.
- **Crafting UI:**
  - Grid-based recipe book with categories & search bar.
  - Shows ingredient preview, owned count, and craftable quantity.
- **Crafting Time:** Instant for small items; large structures require NPC builder and time.

#### 5.11.2. Crafting Tiers

| **Tier**       | **Unlock Requirement**            | **Examples** |
| -------------- | --------------------------------- | ------------ |
| Basic          | Default recipes                   | Wood fence, torch, storage box. |
| Intermediate   | Level 2 tools, 1st Mine unlock    | Sprinkler, scarecrow, keg. |
| Advanced       | Mid-game (Mine Level 40+, 2nd house upgrade) | Beehive, lightning rod, large furniture. |
| Master         | Post-main quest, rare events      | Magical artifacts, rare equipment. |

#### 5.11.3. Example Crafting Recipes

| **Item Name** | **Category**   | **Ingredients**       | **Function** |
| ------------- | -------------- | --------------------- | ------------ |
| Scarecrow     | Farm Equipment | 50 Wood, 1 Cloth, 20 Fiber | Prevents crows from eating crops. |
| Sprinkler     | Farm Equipment | 1 Copper Bar, 1 Iron Bar | Waters 4 tiles daily. |
| Keg           | Processing     | 30 Wood, 10 Iron Bar  | Ferments crops into alcohol/juices. |
| Beehive       | Processing     | 40 Wood, 10 Fiber, 1 Queen Bee | Produces honey every 3 days. |
| Crystal Lamp  | Decor          | 5 Glass, 1 Rare Gem   | Emits glow at night. |
| Moonstone Fence | Decor        | 2 Moonsteel Bars per 5 units | Decorative, never breaks. |

## 5.12. Cooking System

**Purpose:**
Cooking creates consumables that provide stamina, health, and buffs. It also adds depth to NPC relationships through gift preferences.

#### 5.12.1. Cooking Mechanics

- **Kitchen Required:** Available after first house upgrade.
- **Recipe Book:** Unlocked by befriending NPCs, reading books, or buying cookbooks.
- **Cooking UI:**
  - Shows all learned recipes and highlights available ones.
  - Displays buffs clearly (icon-based).
- **Meal Buffs:** Increase stamina regen, mining speed, fishing success, etc. Buffs last **in-game hours**.

#### 5.12.2. Cooking Tiers

| **Tier**       | **Unlock Condition**           | **Examples** |
| -------------- | ------------------------------ | ------------ |
| Basic          | Kitchen unlock                 | Simple salads, bread, boiled egg |
| Intermediate   | 2nd house upgrade, mid-game crops | Stews, sushi, pies |
| Gourmet        | Festival-exclusive recipes     | Rare feasts, magical moon dishes |

#### 5.12.3. Example Cooking Recipes

| **Dish Name** | **Ingredients**              | **Effect** |
| ------------- | ---------------------------- | ---------- |
| Herb Salad    | 2 Spring Blossoms, 1 Olive Oil | +20 Stamina, +10 Energy Regen |
| Fisher's Stew | 1 Trout, 1 Herb, 1 Milk     | +50 Stamina, +5 Fishing Skill |
| Moonlight Pie | 1 Moon Blossom, 1 Sugar, 1 Flour | +80 Stamina, +5 Luck, Glow effect |
| Spicy Ramen   | 1 Chili, 1 Egg, 1 Wheat Flour | +30 Speed, +30 Mining Efficiency |

## 5.13. NPC Interaction & Relationship System

This is **critical** to narrative and replayability. Every NPC has a **personality, schedule, backstory, and growth arc**.

#### 5.13.1. Friendship & Romance

| **Relationship Level** | **Heart Count** | **Unlocks** |
| ---------------------- | --------------- | ----------- |
| Acquaintance           | 0–1             | Basic dialogue |
| Friendly               | 2–3             | Gift reactions, minor quests |
| Close Friend           | 4–5             | Deeper dialogue, special cutscenes |
| Confidant              | 6–7             | Backstory quests, unique gifts |
| Romantic               | 8–9             | Date events, special items |
| Partner/Spouse         | 10              | Marriage, moving in, family content |

- **Gift Preferences:** Each NPC has favorite, liked, neutral, and disliked gifts.
- **Schedule System:** NPCs follow daily routines based on weather, season, and relationships.
- **Event Triggers:**
  - Festivals, birthdays, and relationship milestones trigger custom scenes.

#### 5.13.2. NPC Roles

NPCs are categorized by function:

| **Category**    | **Role**                    | **Example NPC Types** |
| --------------- | --------------------------- | --------------------- |
| Shopkeepers     | Sell seeds, tools, and unique goods | Seed seller, blacksmith, general store owner |
| Town Officials  | Advance plot, give licenses, unlock features | Mayor, ranger, librarian |
| Specialists     | Provide quests, recipes, or rare items | Herbalist, fisherman, miner |
| Neighbors & Friends | Social depth, romance candidates | Farmers, artists, musicians, scholars |
| Mystery Characters | Late-game secrets           | Hermit, spirits, ancient guardians |

#### 5.13.3. NPC Sample Table (25 Core NPCs)

| **Name** | **Role**          | **Personality Keywords** | **Home/Shop** | **Notable Traits** |
| -------- | ----------------- | ------------------------ | ------------- | ------------------ |
| Elara    | Mayor             | Caring, organized, stern | Town Hall     | Central quest giver |
| Theo     | Blacksmith        | Stoic, honest, strong    | Smithy        | Upgrades tools, loves ore |
| Mira     | Florist           | Cheerful, artistic       | Flower Shop   | Breeds rare seeds |
| Finn     | Fisherman         | Laid-back, mysterious    | Beach Hut     | Unlocks fishing zones |
| Kiera    | Librarian         | Bookish, shy, kind       | Library       | Unlocks lore and hidden recipes |
| Aric     | Rancher           | Tough, hardworking       | Ranch         | Animal breeding quests |
| Rina     | Traveling Merchant | Energetic, secretive     | Wandering Caravan | Rare rotating stock |
| Sage     | Herbalist         | Wise, mystical           | Forest Cottage | Potion recipes, foraging tips |
| Lyle     | Musician          | Dreamy, adventurous      | Town Center   | Unlocks instruments |
| Soren    | Guard Captain     | Protective, loyal        | Guard Barracks | Guides in dangerous areas |
| + 15 others... | (Details fully in Character Bible) | ... | ... | ... |

## 5.14. Dialogue System

To ensure **no ambiguity for writing**:

- **Dialogue Trees:**
  - Branching responses based on friendship, weather, season, and events.
- **Dynamic Variables:** Player name, farm name, seasonal greetings.
- **Cutscene Integration:** Triggered by reaching heart milestones or completing quests.
- **Tone System:** NPC mood changes dialogue tone depending on weather, gifts, or town events.

## 5.15. Relationship Economy

- Gifting favorite items gives **+100 points**; disliked items **-50**.
- Talking daily gives **+5 points**.
- Festivals attended with an NPC give **+50 points**.
- **Marriage Requirements:** 8+ hearts, purchase of engagement item, and certain story events.
- Post-marriage, spouses help around the farm and have unique dialogue.

## 5.16. Economy & Currency Overview

**Currency Name:** **Luna** (ℒ)

- Single currency used for all player transactions.
- Coins displayed as "ℒ1234" in UI.

**Core Economy Pillars:**

1. **Primary Income Streams:** Farming, Fishing, Mining, Animal Products, Foraging, Crafting.
2. **Secondary Income Streams:** Festivals (competition prizes), Quests, Rare Event Items.
3. **Player Money Flow:** Earn → Invest (seeds, tools, upgrades) → Unlock New Systems.
4. **Economic Goal:** Ensure steady early progression, strong mid-game investment loop, and high-value late-game goals.

#### 5.16.1. Income Balancing Philosophy

| **Stage**        | **Duration**   | **Player Goals**             | **Daily Earnings Target** |
| ---------------- | -------------- | ---------------------------- | ------------------------- |
| **Early Game** (Days 1–28) | First month    | Learn farming, fishing; basic tools. | ℒ300–ℒ800/day |
| **Mid Game** (Day 29–90) | Month 2–3      | Greenhouse, barns, mining deeper. | ℒ1,500–ℒ3,000/day |
| **Late Game** (90+) | Post-story     | Max farm expansion, magical crops & rare fish. | ℒ5,000–ℒ10,000/day |

#### 5.16.2. Currency Sinks (Money Outflow)

| **Category**        | **Cost Range (ℒ)** | **Notes** |
| ------------------- | ------------------ | --------- |
| Seeds & Saplings    | ℒ20–ℒ500 per seed/tree | Primary early-game sink |
| Tool Upgrades       | ℒ2,000–ℒ15,000 per tier | Requires ores and blacksmith services |
| Farm Buildings      | ℒ3,000–ℒ50,000    | Barns, coops, silos, sheds, greenhouses |
| House Upgrades      | ℒ10,000–ℒ50,000   | Kitchen, large rooms, trophy halls |
| Animals             | ℒ500–ℒ3,000       | Livestock and magical creatures |
| Crafting Blueprints | ℒ1,000–ℒ20,000    | Mid/late-game unlocks |
| Clothing & Cosmetics | ℒ100–ℒ5,000       | Optional vanity system |
| Festival Items & Tickets | ℒ500–ℒ3,000 per event | Keeps economy balanced |
| Furniture & Decor   | ℒ200–ℒ10,000      | Customization endgame loop |

#### 5.16.3. Pricing Logic Formula

We'll use a **baseline formula** to price every item for consistency:

`Base Price = (Growth Time × Rarity Multiplier × Processing Multiplier) + 10`

- **Growth Time (GT):** Days required to obtain the item (seed growth, fish availability).
- **Rarity Multiplier (RM):**
  - Common: 1.0
  - Uncommon: 1.5
  - Rare: 2.0
  - Legendary: 3.0+
- **Processing Multiplier (PM):**
  - Raw item: 1.0
  - Processed (wine, cheese, artisan goods): 1.5–2.5x.

#### 5.16.4. Crop Price Table

| **Crop Name** | **Season** | **Growth Days** | **Base Sell Price (ℒ)** | **Notes** |
| ------------- | ---------- | --------------- | ----------------------- | --------- |
| Turnip        | Spring     | 4               | ℒ60                     | Beginner-friendly |
| Cabbage       | Spring     | 6               | ℒ90                     | Balanced starter crop |
| Strawberry    | Spring     | 8 + regrow      | ℒ120                    | Profitable over time |
| Corn          | Summer     | 7 + regrow      | ℒ140                    | Steady mid-tier crop |
| Blueberry     | Summer     | 9 + regrow      | ℒ160                    | High-yield |
| Pumpkin       | Fall       | 10              | ℒ300                    | Festival centerpiece crop |
| Moon Blossom  | Summer     | 12              | ℒ500                    | Rare, magical crop (glows at night) |
| Winter Root   | Winter     | 6               | ℒ150                    | Foraged in snowfields |

#### 5.16.5. Animal Product Table

| **Animal** | **Product** | **Frequency** | **Base Sell Price (ℒ)** | **Notes** |
| ---------- | ----------- | ------------- | ----------------------- | --------- |
| Chicken    | Egg         | Daily         | ℒ60                     | Standard staple product |
| Cow        | Milk        | Daily         | ℒ100                    | Can process into cheese |
| Sheep      | Wool        | Every 3d      | ℒ150                    | Spinning wheel upgrade |
| Goat       | Goat Milk   | Every 2d      | ℒ180                    | Higher-value cheese |
| Rabbit     | Fur         | Random        | ℒ200                    | Luxury tailoring resource |
| Moon Deer  | Moon Antlers | Seasonal      | ℒ800                    | Rare magical material |

#### 5.16.6. Fish Price Table

| **Fish Name** | **Rarity** | **Base Price (ℒ)** | **Location**     | **Notes** |
| ------------- | ---------- | ------------------ | ---------------- | --------- |
| River Trout   | Common     | ℒ80                | Rivers           | Easy beginner catch |
| Golden Carp   | Uncommon   | ℒ200               | Lakes            | Mid-game fishing goal |
| Star Tuna     | Rare       | ℒ350               | Ocean            | Festival competition fish |
| Moon Eel      | Legendary  | ℒ500               | Ocean (Full Moon) | Seasonal, magical fish |

#### 5.16.7. Mining Resource Price Table

| **Resource**    | **Rarity** | **Base Price (ℒ)** | **Use** |
| --------------- | ---------- | ------------------ | ------- |
| Copper Ore      | Common     | ℒ30                | Basic tool upgrades |
| Iron Ore        | Common     | ℒ60                | Mid-tier upgrades |
| Gold Ore        | Uncommon   | ℒ120               | Advanced upgrades |
| Fire Crystal    | Rare       | ℒ250               | Magical crafting material |
| Moonsteel Ore   | Legendary  | ℒ500               | Endgame tools and weapons |

#### 5.16.8. Processed Goods Pricing

Processing doubles or triples profit, encouraging farm infrastructure investment.

| **Processed Good** | **Base Ingredients** | **Sell Price (ℒ)** | **Notes** |
| ------------------ | -------------------- | ------------------ | --------- |
| Cheese             | Milk                 | ℒ200               | Dairy processing tier 1 |
| Goat Cheese        | Goat Milk            | ℒ300               | Higher-tier product |
| Wine               | Fruit (x3)           | ℒ400               | Luxury artisan product |
| Honey              | Beehive output       | ℒ150               | Seasonal flavors |
| Moon Blossom Tea   | Moon Blossom + Herbs | ℒ600               | Buffs, late-game |

#### 5.16.9. Quests, Festivals & Rare Event Rewards

- **Daily Quests:** +ℒ200–ℒ500 (deliveries, gathering).
- **Festival Competitions:** +ℒ2,000+ for winning contests.
- **Late-Game Rares:** Up to ℒ10,000 per item (Moon Antlers, Legendary Fish).

## 5.17. Inventory & Storage Progression

| **Stage**     | **Starting Capacity** | **Max Capacity** | **Unlocks** |
| ------------- | --------------------- | ---------------- | ----------- |
| Backpack Tier 1 | 16 slots              | -                | Default |
| Backpack Tier 2 | 24 slots              | ℒ5,000, Shop Upgrade | |
| Backpack Tier 3 | 36 slots              | ℒ15,000, Shop Upgrade | |
| Chest (Storage) | 20 slots              | 999 placed       | Crafted from 50 Wood |
| Shed Storage  | -                     | Infinite         | Houses furniture & artisan goods |

- **Sorting Filters:** Crop, animal, fish, materials, quest items.
- **Quick Stack:** Auto-sorts inventory to matching chests.
- **Hotbar:** 10 slots, customizable.

## 5.18. World Overview

**World Concept:**

- A **self-contained island** with **distinct biomes**.
- Core town hub surrounded by natural exploration zones (farming land, beaches, forests, caves, mountains, snowy regions).
- Exploration starts small (farm + town), then expands as the player upgrades gear and completes quests.
- Designed for **Switch and mobile optimization**: modular zones loaded per area, but visually seamless.

#### Exploration Pillars

1. **Vertical Progression:** Gear upgrades (pickaxe, axe) unlock deeper mine floors, new foraging areas.
2. **Seasonal Transformation:** Biomes visually and mechanically change per season.
3. **Discovery Rewards:** Hidden paths, rare forage items, treasure caches, and lore notes.
4. **Fast Travel:** Initially minimal; later unlocked via **Moon Shrines** (magical teleport points).

## 5.19. Biome Breakdown

Here's a **zone-by-zone spec** for environment artists and level designers.

#### 1. Player Farm

- **Starting Area:** 60x60 tile grid; overgrown at start.
- **Features:**
  - House (expandable), small shed, mailbox, basic farmland patches.
  - Later expansions: animal barns, coop, greenhouses, decorative landscaping.
- **Assets:** Broken fences, tall grass, rocks, trees.
- **Gameplay Hooks:** Tutorial, farming core loop.

#### 2. Town Center

- **Purpose:** Social hub, NPC shops, events.
- **Key Buildings:**
  - Town Hall (Mayor's office, bulletin board, festival coordination).
  - General Store (seeds, daily goods).
  - Blacksmith (tool upgrades, ore processing).
  - Flower Shop, Tavern, Library, Tailor.
- **Map Size:** Medium (40x40 tiles).
- **NPC Density:** High; most NPCs have daily routines here.

#### 3. Forest Region

- **Layout:** Dense trees, rivers, hidden paths.
- **Points of Interest:**
  - Herbalist's Cottage (Sage NPC).
  - Mushroom Grove (seasonal rare spawns).
  - Abandoned Treehouse (quest unlock).
- **Gameplay:** Foraging focus; certain fish in forest ponds.
- **Seasonal Changes:**
  - Spring flowers, Summer greenery, Fall mushrooms, Winter barren trees.

#### 4. Beach & Oceanfront

- **Access:** From Town, available Day 1.
- **POIs:**
  - Fisherman's Hut (Finn NPC).
  - Dock (fishing quests, boat rentals later).
  - Tide Pools (rare shells, moonstone).
- **Gameplay:** Fishing hub, summer festivals held here.
- **Art Direction:** Warm sand tones, seashell clutter, dynamic tide animation.

#### 5. Mountain Range

- **Unlock:** Day 7 via quest.
- **POIs:**
  - Mine Entrance.
  - Mountain Lake (rare fish).
  - Observatory (late-game quest hub).
- **Gameplay:**
  - Mining progression starts here.
  - Seasonal wildlife appearances.
- **Size:** Large vertical maps with switchbacks and bridges.

#### 6. Cave Systems (Mines)

- Procedural interiors (5-floor sets with theme tilesets).
- Four main tiers (Caverns → Crystal Caves → Lava Depths → Moonlit Abyss).
- Secret treasure rooms every 10th floor.

#### 7. Snowy Plains (Endgame)

- **Unlock:** Late-game questline.
- **Biome:** Permanent snow, aurora skies.
- **Gameplay:** Winter-exclusive forageables, rare creatures, high-value ores.
- **POIs:** Frozen Lake (legendary fish), Ice Ruins (dungeon).

#### 8. Festival Grounds

- A central area north of Town, dynamically decorated for events.
- Hosted festivals include Flower Dance, Ocean Lights Festival, Harvest Celebration, Moonlight Eve.

## 5.20. Exploration Progression & Unlock Flow

| **Stage**      | **Player Level/Quest Requirement** | **New Zone/Feature Unlocked** |
| -------------- | ---------------------------------- | ----------------------------- |
| Start          | Day 1                              | Farm + Town + Beach |
| Early Game     | Day 7, First Axe Upgrade           | Forest & Mountain Base |
| Mid Game       | Mine Floor 20+, Questline          | Mountain Lake + Crystal Caves |
| Mid-Late Game  | Greenhouse Built, Festival Arc     | Observatory + Lava Depth Mines |
| Late Game      | Main Story Completion              | Snowy Plains + Ice Ruins |

### 5.21. Map Layout (Textual Diagram)

[Snowy Plains / Ice Ruins]
|
[Mountain Peak & Observatory]
|
[Mountain Mines & Lake]
|
[Forest Region] --[Town Center]-- [Beach & Oceanfront]
| |
[Farm] [Festival Grounds]

**Design Notes:**

- Central **Town** acts as the hub; all other regions radiate from it.
- **Farm** is slightly isolated south of Town for performance and immersion.
- **Mountain** zones tier vertically; Snowy Plains are a narrative climax zone.
- Map designed with **clear sightlines** and **landmarks** for navigation (windmill near farm, lighthouse near beach, tall peak for mountains).

## 5.22. Fast Travel & Movement

- **Walking/Running:** Default traversal; stamina not consumed.
- **Mounts:** Unlockable mid-game (rideable deer/horse).
- **Moon Shrines:** Teleport between zones; unlocked after shrine quests.
- **Boats:** Allow ocean exploration (late-game fishing islands).

## 5.23. Exploration Rewards

| **Reward Type**    | **Example**                   | **Purpose** |
| ------------------ | ----------------------------- | ----------- |
| Rare Forageables   | Frostberry, Firecap Mushroom  | Unique cooking & alchemy |
| Treasure Caches    | Ancient Coins, Tools          | Money/upgrade rewards |
| Lore Notes & Relics | Journals, Murals             | Builds world narrative |
| Hidden Shortcuts   | Rope ladders, tunnels         | Travel optimization |
| Shrine Unlocks     | Moon Shrines grant teleport nodes | World traversal speed |

---
**Back to:** [[Moon Farming GDD]]
