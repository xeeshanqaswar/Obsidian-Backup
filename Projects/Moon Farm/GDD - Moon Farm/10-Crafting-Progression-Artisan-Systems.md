
## 10.1. Core Design Goals

- **Player Agency:** Crafting should feel rewarding and player-driven, not just a grind.
- **Progression Through Tools:** Unlock higher tiers of recipes, stations, and artisan goods as the player advances.
- **Economy Integration:** Rare crafted goods should drive profits, encouraging farming, mining, and breeding loops.
- **Customization & Aesthetics:** Many recipes are decorative, rewarding creative players.

## 10.2. Crafting Pillars

| **Pillar**        | **Description** |
| ----------------- | --------------- |
| **Utility Crafting** | Tools, machines, furniture that improves gameplay efficiency. |
| **Consumables**   | Food, potions, fertilizers, animal treats. |
| **Artisan Goods** | High-value items (cheese, preserves, spirits) for economy scaling. |
| **Aesthetics**    | Furniture, paths, décor, clothing. |
| **Advanced Systems** | Magical crafting (late-game), rune-imbued tools, rare farm enhancements. |

## 10.3. Crafting Unlock Flow

| **Player Phase** | **Unlocks**                     | **Player Actions Driving Progression** |
| ---------------- | ------------------------------- | -------------------------------------- |
| **Early Game** (Days 1-15) | Basic recipes: fences, torches, scarecrows, simple food. | Gathering wood, stone, foraging. |
| **Mid Game** (Day 16+) | Tool upgrades, artisan machines, fertilizers. | Mining, farming upgrades. |
| **Late Game** (Year 2) | Magical crafts, rune tools, rare décor. | Shrine quests, breeding rares. |

## 10.4. Crafting System Flow

1. **Gather Materials** (farming, foraging, mining, fishing, breeding).
2. **Access Crafting Menu**:
    - Categories: Utility, Consumable, Artisan, Décor, Magical.
3. **Crafting Stations Required**:
    - Simple (handcrafting) or advanced (specialized workbenches).
4. **Time Cost:**
    - Most items instant; artisan goods take **in-game hours or days**.
5. **Quality Scaling:**
    - Quality bonuses based on ingredients used and player crafting skill.

## 10.5. Crafting Stations & Upgrades

| **Station Name** | **Unlock Method**       | **Use** |
| ---------------- | ----------------------- | ------- |
| Workbench        | Starter item            | Basic crafting (tools, fences, décor). |
| Cooking Stove    | Built after Carpenter upgrade | Cook dishes for buffs, gifts. |
| Loom             | Carpentry upgrade       | Converts wool into cloth. |
| Preserves Barrel | Crafted Year 1 Summer   | Turns fruit/veg into jams/pickles. |
| Cheese Press     | Rancher quest           | Makes cheese/butter from milk. |
| Fermentation Keg | Autumn Festival reward  | Ferments wine, ale, vinegar. |
| Potion Table     | Sage Luma's questline   | Crafts potions, fertilizers, elixirs. |
| Rune Forge       | Year 2 Shrine quest     | Imbues magical effects into gear/furniture. |

## 10.6. Example Recipe Categories

#### Utility Recipes

| **Item**            | **Inputs**             | **Function** |
| ------------------- | ---------------------- | ------------ |
| Scarecrow           | 20 Wood, 1 Cloth       | Protects crops from pests. |
| Automatic Feeder    | 50 Wood, 2 Iron Bars   | Automates animal feeding. |
| Water Sprinkler     | 2 Copper, 1 Iron       | Waters adjacent crops daily. |
| Storage Chest       | 30 Wood                | Expands inventory. |

#### Consumables

| **Item**         | **Inputs**                   | **Buff** |
| ---------------- | ---------------------------- | -------- |
| Stamina Stew     | Carrot, Onion, Egg           | +50 stamina. |
| Forest Tea       | Mint Leaf, Honey             | +Speed for 3 mins. |
| Moonlight Elixir | Moonberry, Starfish, Rune Dust | Increases rare forage chance. |

#### Artisan Goods

| **Item**         | **Station**     | **Inputs**         | **Notes** |
| ---------------- | --------------- | ------------------ | --------- |
| Sunflower Oil    | Preserves Barrel | Sunflower, Glass Bottle | Mid-game cooking ingredient. |
| Starfruit Wine   | Fermentation Keg | Starfruit, Sugar   | Late-game high-value product. |
| Moonstone Wool Scarf | Loom + Rune Forge | Glowing Wool, Moonstone | Magical décor, boosts warmth. |
| Honey Mead       | Fermentation Keg | Honey, Water Jar   | Village trade good. |

#### Décor

| **Item**        | **Inputs**              | **Notes** |
| --------------- | ----------------------- | --------- |
| Rustic Chair    | 10 Wood, 1 Iron Nail    | Aesthetic, placed in home or farm. |
| Garden Lantern  | 5 Iron Bars, Firefly Glass | Lights farm paths. |
| Winter Wreath   | Pine Branches, Ribbon   | Seasonal. |

#### Magical Crafts (Late-Game)

| **Item**       | **Station**   | **Inputs**            | **Effect** |
| -------------- | ------------- | --------------------- | ---------- |
| Rune-Infused Hoe | Rune Forge    | Mythril, Rune Dust    | Hoe 3x3 tiles at once. |
| Spirit Beacon  | Rune Forge    | Moonstone, Crystal Shard | Teleports player to chosen shrine. |
| Enchanted Planter | Rune Forge    | Gold Bar, Moonberry Seeds | Auto-grows crops out of season. |

## 10.7. Crafting Skill Progression

- **Skill Levels:**
  - **Novice → Adept → Master → Artisan → Rune Sage.**
- **XP Sources:**
  - Crafting items, using artisan stations, completing NPC crafting quests.
- **Perks:**
  - Reduced material costs, higher product quality, ability to customize furniture.

## 10.8. Artisan Economy Loop

1. **Farm & Gather**: Produce crops, rare fish, or exotic animal goods.
2. **Craft Artisan Goods**: Process into higher-value products (jam, cheese, wine).
3. **Sell or Gift**: Drive profits or unlock NPC story arcs with crafted gifts.
4. **Reinvest in Upgrades**: Expand farm automation, unlock rare breeding animals.
5. **Late Game Goal**: Create legendary rune artifacts for aesthetic mastery.

## 10.9. Inventory & Crafting UI (Implementation Notes)

| **Screen**         | **Features** |
| ------------------ | ------------ |
| **Crafting Menu**  | Filter tabs by category, recipe preview, "missing items" highlight. |
| **Inventory Menu** | Stack limits (99), rarity color-coding. |
| **Station Menu**   | Progress bar for artisan goods, queue system for late-game. |
| **Customization Mode** | Drag-and-place décor, rotate furniture. |

## 10.10. Art Direction

- **Station Design:**
  - Rustic wooden machines evolve visually with each upgrade (metal reinforcements, glowing runes late-game).
- **Icons:**
  - Hand-painted, vibrant colors, distinct silhouettes for readability on mobile/switch.
- **Animations:**
  - Small "working" animations for stations (spinning gears, bubbling liquids).
- **Rarity Colors:**
  - Common (White), Uncommon (Green), Rare (Blue), Epic (Purple), Legendary (Gold).

## 10.11. Full Recipe Tables

### 🔹 Utility Crafting Recipes

| **Item Name**   | **Station**   | **Ingredients**   | **Unlock Condition** | **Use** |
| --------------- | ------------- | ----------------- | -------------------- | ------- |
| **Storage Chest** | Workbench      | 30 Wood           | Starter recipe       | Expands inventory by +24 slots. |
| **Wooden Fence** | Workbench      | 4 Wood            | Starter recipe       | Protects crops/animals, decorative. |
| **Stone Fence** | Workbench      | 4 Stone           | Lv. 2 Crafting Skill | More durable fence. |
| **Torch**       | Workbench      | 1 Wood, 1 Coal    | Starter recipe       | Basic lighting for farm. |
| **Lantern Post** | Workbench      | 5 Iron Bar, 1 Glass Pane | Lv. 3 Crafting Skill | Permanent outdoor lighting. |
| **Scarecrow**   | Workbench      | 20 Wood, 5 Fiber, 1 Cloth | Starter recipe       | Keeps pests away from 5x5 tile radius. |
| **Advanced Sprinkler** | Workbench      | 2 Copper, 1 Iron, 1 Gold Bar | Farming Lv. 4 | Waters 3x3 tile area daily. |
| **Bee Box**     | Workbench      | 40 Wood, 3 Iron Bars, 5 Honeycomb | Year 1 Spring Festival reward | Produces honey over time near flowers. |
| **Animal Feeder** | Carpenter Shop | 50 Wood, 2 Iron Bars | Ranching Lv. 3 | Automates barn/coop feeding. |
| **Automatic Gate** | Carpenter Shop | 40 Wood, 3 Copper Bars, 1 Gear | Year 1 Summer | Opens/closes for animals automatically. |
| **Fishing Net** | Workbench      | 15 Fiber, 2 Iron Nails | Fishing Lv. 2 | Placeable trap for passive fish gathering. |
| **Mini Greenhouse** | Carpenter Shop | 60 Wood, 10 Glass Pane, 5 Gold Bars | Year 2 Spring Festival reward | Grows one crop out of season. |

### 🔹 Building Materials Recipes

| **Item Name** | **Station**   | **Ingredients** | **Unlock Condition** | **Use** |
| ------------- | ------------- | --------------- | -------------------- | ------- |
| **Wood Plank** | Sawmill        | 3 Wood          | Starter              | Core building material. |
| **Stone Brick** | Mason Bench    | 3 Stone         | Starter              | Core construction material. |
| **Glass Pane** | Mason Bench    | 2 Sand, 1 Coal  | Year 1 Summer        | Used for décor, lanterns, greenhouses. |
| **Iron Nail Pack** | Workbench      | 1 Iron Bar      | Starter              | Required for furniture and structures. |
| **Gear**      | Workbench      | 2 Iron Bars     | Mining Lv. 3         | For automation upgrades. |
| **Rope Bundle** | Loom           | 5 Fiber         | Starter              | Used for animal gear, fishing, décor. |

### 🔹 Consumable Recipes (Food & Buffs)

| **Item Name** | **Station**   | **Ingredients Required** | **Unlock Condition** | **Buff/Effect** |
| ------------- | ------------- | ------------------------ | -------------------- | --------------- |
| **Vegetable Stew** | Cooking Stove | Carrot x2, Potato x1, Onion x1 | Starter cooking book | +50 stamina |
| **Forest Tea** | Cooking Stove | Mint Leaf x2, Honey x1   | Foraging Lv. 3       | +Speed for 3 min |
| **Farmer's Omelette** | Cooking Stove | Egg x2, Milk x1, Spinach x1 | Ranching Lv. 2       | +Farming efficiency for 1 in-game day |
| **Star Salad** | Cooking Stove | Starfruit x1, Lettuce x1, Olive Oil x1 | Summer Festival reward | +Luck for rare drops |
| **Moonlight Elixir** | Potion Table  | Moonberry x2, Starfish x1, Rune Dust x1 | Year 2 Shrine Quest | +25% chance of rare forage for 3 days |
| **Fisher's Chowder** | Cooking Stove | Fish x1, Corn x1, Milk x1 | Fishing Lv. 3        | +Fishing success rate |
| **Rancher's Treats** | Cooking Stove | Wheat x2, Berry x1       | Ranching Lv. 3       | Makes animals happier for 2 days |

### 🔹 Artisan Goods (Profitable & Processing Recipes)

| **Item Name** | **Station**    | **Ingredients**     | **Unlock Condition** | **Sale Value (Base)** |
| ------------- | -------------- | ------------------- | -------------------- | --------------------- |
| **Fruit Jam** | Preserves Barrel | Any Fruit x2, Sugar x1 | Year 1 Spring        | 150g |
| **Pickled Veggies** | Preserves Barrel | Any Veggie x2, Vinegar x1 | Year 1 Summer        | 140g |
| **Sunflower Oil** | Preserves Barrel | Sunflower x1, Glass Bottle x1 | Summer Festival      | 200g |
| **Cheese (Cow)** | Cheese Press   | Cow Milk x1         | Ranching Lv. 2       | 220g |
| **Goat Cheese** | Cheese Press   | Goat Milk x1        | Ranching Lv. 3       | 300g |
| **Honey Mead** | Fermentation Keg | Honey x1, Water Jar x1 | Autumn Festival      | 250g |
| **Starfruit Wine** | Fermentation Keg | Starfruit x1, Sugar x1 | Year 2              | 600g |
| **Truffle Oil** | Preserves Barrel | Truffle x1, Glass Bottle x1 | Pig Breeding Lv. 2   | 500g |

### 🔹 Fertilizers & Soil Enhancements

| **Item Name**      | **Station**   | **Ingredients**   | **Unlock Condition** | **Effect** |
| ------------------ | ------------- | ----------------- | -------------------- | ---------- |
| **Basic Fertilizer** | Workbench     | Sap x2, Compost x1 | Starter              | +10% crop quality |
| **Speed-Grow Fertilizer** | Potion Table  | Fishbone x1, Ash x1 | Farming Lv. 2        | Crops mature 25% faster |
| **Super Fertilizer** | Potion Table  | Moon Dust x1, Rare Herb x1 | Year 2 Shrine Quest | +25% crop quality |
| **Pest-Repellent Mix** | Potion Table  | Mint Leaf x1, Bug Shell x1 | Foraging Lv. 4       | Crops immune to pests for 7 days |

### 🔹 Clothing & Fashion Crafting

| **Item Name**    | **Station**   | **Ingredients**    | **Unlock Condition** | **Notes** |
| ---------------- | ------------- | ------------------ | -------------------- | --------- |
| **Farmer's Hat** | Loom          | Cloth x1, Leather Strap x1 | Starter              | Basic starter hat. |
| **Adventurer's Boots** | Loom          | Leather x2, Wool x1 | Mining Lv. 3         | +Speed on rugged terrain. |
| **Sun Dress**    | Loom          | Cloth x3, Dye x1   | Year 1 Summer Festival | Cosmetic only. |
| **Moonstone Cloak** | Rune Forge    | Moonstone x1, Glowing Wool x3 | Year 2 Winter Shrine | +Magic resistance. |

### 🔹 Magical Crafts (Late-Game Power Items)

| **Item Name**    | **Station**   | **Ingredients**         | **Effect** |
| ---------------- | ------------- | ----------------------- | ---------- |
| **Rune-Infused Hoe** | Rune Forge    | Mythril x2, Rune Dust x3 | Hoe 3x3 tiles at once. |
| **Spirit Beacon** | Rune Forge    | Moonstone x2, Crystal Shard x1 | Teleports player to chosen shrine. |
| **Enchanted Planter** | Rune Forge    | Gold Bar x2, Moonberry Seeds x3 | Auto-grows crops out of season. |
| **Phoenix Charm** | Rune Forge    | Phoenix Feather x1, Gold Bar x1 | Auto-revive once per in-game week. |

### 🔹 Décor & Farm Customization

| **Item Name** | **Station**   | **Ingredients**      | **Notes** |
| ------------- | ------------- | -------------------- | --------- |
| **Rustic Chair** | Workbench     | Wood x10, Iron Nail x1 | Decorative. |
| **Garden Lantern** | Workbench     | Iron Bar x2, Firefly Glass x1 | Emits soft light. |
| **Winter Wreath** | Workbench     | Pine Branch x5, Ribbon x1 | Seasonal décor. |
| **Stone Fountain** | Mason Bench   | Stone x30, Copper Bar x1 | Animated décor, boosts farm appeal. |

### 🔹 Key Design Notes for Devs & Artists

- **Each Recipe Icon**: Hand-painted, bold silhouettes, vibrant seasonal palettes.
- **Stations Visually Upgrade**: Rustic → Refined → Magical aesthetics.
- **Ingredient Icons**: Categorize by **color-coded borders** (Green: Foraged, Blue: Farmed, Purple: Magical).
- **Balance Notes**: Rare items require festival rewards or shrine quests to encourage exploration and event participation.

## 10.12. Full Crop Table (Farming System)

### 🔹 Farming Design Goals

- **Clear Seasonal Cycles:** Each crop tied to a season (or multiple).
- **Visual Growth Stages:** Every crop has 3–5 growth stages, with distinct art assets.
- **Progression Integration:** Early crops for stability, late crops for high-profit artisan goods.
- **Crafting Links:** Nearly every crop ties into cooking, artisan, or magical crafting.
- **Economic Diversity:** Cheap staple crops + rare, festival-exclusive plants.

### 🔹 Farming System Rules

| **Feature**            | **Detail** |
| ---------------------- | ---------- |
| Growth Stages          | Sprout → Seedling → Bud → Mature → Harvest. |
| Daily Growth           | Each day advances a stage based on crop's growth timer. |
| Water Requirement      | Must be watered daily or growth halts. |
| Fertilizer Impact      | Improves quality (Bronze/Silver/Gold/Star) & yield. |
| Regrow vs. Single Harvest | Some crops regrow after harvest (e.g., berries). |
| Seasonal Decay         | Crops wilt if season changes (except greenhouse-grown). |
| Quality Scaling        | Based on farming skill, fertilizer, and random luck factor. |
| Tools Needed           | Hoe (till), Watering Can (water), Scythe or Hands (harvest). |

### 🔹 Crop Rarity Tiers

| **Rarity** | **Color Code** | **Example Crops** | **Notes** |
| ---------- | -------------- | ----------------- | --------- |
| Common     | White          | Carrot, Potato    | Fast growth, low profit. |
| Uncommon   | Green          | Strawberry, Corn  | Moderate growth/profit. |
| Rare       | Blue           | Starfruit, Pumpkin | Festival unlocks, high value. |
| Epic       | Purple         | Moonberry, Lotus  | Late-game, shrine quests required. |

## 🌱 CROP TABLE (BY SEASON)

### 🌸 Spring Crops

| **Crop Name** | **Days to Grow** | **Regrow?** | **Sell Value (Base)** | **Crafting/Use** | **Notes for Artists (Visuals)** |
| ------------- | ---------------- | ----------- | --------------------- | ---------------- | ------------------------------- |
| Carrot        | 4 days           | No          | 40g                   | Cooking (Stew), Ranch Treats | Bright orange, leafy greens. |
| Potato        | 6 days           | No          | 60g                   | Stew, Chips      | Brown earthy tuber, rustic texture. |
| Strawberry    | 8 days           | Yes         | 90g                   | Jams, Wine       | Red, heart-shaped, leafy crown. |
| Lettuce       | 5 days           | No          | 50g                   | Salads, Wraps    | Light green, rounded leaves. |
| Bluebell Flower | 6 days         | No          | 55g                   | Potion Ingredient | Blue bloom, vibrant color pop. |
| Mint Herb     | 5 days           | Yes         | 45g                   | Forest Tea, Potions | Small green leaves, animated shimmer. |
| Spring Onion  | 5 days           | No          | 35g                   | Stir Fry, Elixirs | White bulb, thin stalk. |
| Clover        | 7 days           | No          | 70g                   | Lucky charms, Festival item | Small tri-leaf design, stylized animation. |

### ☀️ Summer Crops

| **Crop Name** | **Days to Grow** | **Regrow?** | **Sell Value (Base)** | **Crafting/Use** | **Notes for Artists (Visuals)** |
| ------------- | ---------------- | ----------- | --------------------- | ---------------- | ------------------------------- |
| Tomato        | 7 days           | Yes         | 80g                   | Sauces, Salads   | Vivid red, vine cluster. |
| Corn          | 10 days          | Yes         | 100g                  | Cornbread, Chowder | Tall stalk, yellow cobs. |
| Sunflower     | 12 days          | No          | 120g                  | Oil, Décor       | Tall flower, animated turning head. |
| Watermelon    | 12 days          | No          | 180g                  | Juice, Summer recipes | Large, striped fruit, ground vines. |
| Chili Pepper  | 6 days           | Yes         | 85g                   | Spicy dishes, Potions | Bright red, curved pepper shape. |
| Olive         | 11 days          | Yes         | 110g                  | Olive oil, Antipasto | Small olive tree sapling asset. |
| Tropical Orchid | 13 days        | No          | 200g                  | Rare décor, Magical elixirs | Bright pink, delicate petals, sparkle VFX. |

### 🍂 Autumn Crops

| **Crop Name** | **Days to Grow** | **Regrow?** | **Sell Value (Base)** | **Crafting/Use** | **Notes for Artists (Visuals)** |
| ------------- | ---------------- | ----------- | --------------------- | ---------------- | ------------------------------- |
| Pumpkin       | 13 days          | No          | 220g                  | Pie, Soup, Décor | Orange round gourd, Halloween tie-in. |
| Grape         | 9 days           | Yes         | 90g                   | Wine, Jelly      | Purple grape vines on trellis. |
| Apple         | 14 days          | Yes         | 130g                  | Cider, Baking    | Red apple tree, falling leaf animations. |
| Cranberry     | 8 days           | Yes         | 75g                   | Sauces, Jams     | Red clusters, bog-style field asset. |
| Beetroot      | 6 days           | No          | 60g                   | Soup, Salads     | Bright magenta, leafy top. |
| Chestnut      | 11 days          | No          | 100g                  | Roasting, Snacks | Tree crop, husked fruit asset. |
| Autumn Lotus  | 15 days          | No          | 250g                  | Magical Crafts   | Glowing purple-pink lotus blossom. |

### ❄️ Winter Crops (Special Greenhouse / Snow Farming)

| **Crop Name** | **Days to Grow** | **Regrow?** | **Sell Value (Base)** | **Crafting/Use** | **Notes for Artists (Visuals)** |
| ------------- | ---------------- | ----------- | --------------------- | ---------------- | ------------------------------- |
| Snow Pea      | 7 days           | Yes         | 80g                   | Soups, Stir Fry  | Frosted pods, cool tone leaves. |
| Winterberry   | 9 days           | Yes         | 95g                   | Jams, Holiday décor | Red berries, frosted vine assets. |
| Moonberry     | 14 days          | No          | 300g                  | Moonlight Elixir, Late-game crafts | Glowing blue-purple fruit with light pulse. |
| Ice Ginseng   | 12 days          | No          | 280g                  | Rare potions, Stamina boosters | Frosted root with icy tips. |
| Frost Orchid  | 15 days          | No          | 350g                  | Legendary potion ingredient | Shimmering petals with frost particle effect. |

### 🌟 Special Festival Crops (Event-Exclusive Seeds)

| **Crop Name** | **Days to Grow** | **Regrow?** | **Sell Value (Base)** | **Crafting/Use** | **Notes for Artists** |
| ------------- | ---------------- | ----------- | --------------------- | ---------------- | --------------------- |
| Starfruit     | 15 days          | No          | 500g                  | Starfruit Wine, Star Salad | Glowing yellow star-shaped fruit. |
| Phoenix Pepper | 12 days        | No          | 400g                  | Phoenix Charm, Potions | Fiery glow animation. |
| Spirit Bloom  | 16 days          | No          | 600g                  | Rune Forge Recipes | Pulsing glow, particle aura. |

### 🔹 Farming Progression Summary

| **Player Stage** | **Crops Available**        | **Notes** |
| ---------------- | -------------------------- | --------- |
| **Early Game**   | Carrots, Potatoes, Lettuce | Quick growth, stabilizes income. |
| **Mid Game**     | Corn, Grapes, Pumpkins     | Ties into artisan products. |
| **Late Game**    | Moonberries, Frost Orchids | Drives magical crafting & economy. |
| **Festival Tier** | Starfruit, Spirit Bloom, Phoenix | Late-game goals, rare seeds from events. |

### 🔹 Art & Animation Direction

- **Growth Stage Assets per Crop:**
  - Stage 1: Sprout (small leaf, soil bump).
  - Stage 2: Seedling (tiny leaves).
  - Stage 3: Bud (medium plant).
  - Stage 4: Mature (ready-to-harvest visuals).
  - Stage 5: Harvested (soil patch).
- **VFX Layers:**
  - Rare crops glow slightly.
  - Seasonal color palettes for soil and crop shading.
- **Tile Size & Scale:**
  - Crops scale proportionally to character height (1.5 tiles max).
- **UI Icons:**
  - Clear, bold icons matching hand-painted stylization.

---
**Back to:** [[Moon Farming GDD]]
