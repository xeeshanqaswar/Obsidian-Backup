
## 🔹 Farming System Goals

- **Clear Crop Lifecycle:** Each crop has exact growth days, seasonal availability, and visuals per stage.
- **Economic Balance:** Common crops for early-game money, rare crops for mid/late-game profitability.
- **Visual Clarity:** Each growth stage has dedicated sprites/3D models with seasonal palette adjustments.
- **Player Progression Hook:** New crops unlock with new tools, quests, and seasonal events.
- **Automation Path:** Late-game sprinklers, scarecrows, and magical fertilizers reduce micromanagement.

## 🔹 Core Farming Mechanics

| **Mechanic**    | **Details** |
| --------------- | ----------- |
| **Plot Tilling** | Player tills soil with a hoe; upgraded tools increase area (1x1 → 3x3). |
| **Planting**    | Plant seeds; seeds indicate correct season in UI. |
| **Watering**    | Daily watering required; upgraded watering cans water multiple tiles; sprinklers automate. |
| **Fertilizers** | Improve growth speed, crop quality, or yield. |
| **Growth Stages** | Each crop has **4–6 visual stages**; seasonal plants wilt when season changes. |
| **Harvest Types** | - **Single-Harvest Crops:** Replant each time.<br>- **Multi-Harvest Crops:** Regrow after cutting. |
| **Seasonal Rules** | Crops only grow in listed seasons unless grown in **Greenhouses or Magic Fields**. |
| **Quality Tiers** | Bronze, Silver, Gold, Star-tier crops increase value. |
| **Special Crops** | Legendary crops tied to events, shrines, or festivals. |

## 🔹 Seed Shop & Unlock Flow

| **Crop Tier**      | **Unlock Condition** |
| ------------------ | -------------------- |
| **Basic**          | Available at start. |
| **Intermediate**   | Buy from general store after Year 1 or complete NPC quests. |
| **Advanced**       | Only found in traveling merchant stock, shrine quests, or festival rewards. |

## 🌱 Core Crop Table (Per Season)

| **Crop Name**    | **Season(s)**   | **Days to Grow** | **Regrow?** | **Harvest Yield** | **Base Value** | **Growth Stages** | **Notes for Artists** |
| ---------------- | --------------- | ---------------- | ----------- | ----------------- | -------------- | ----------------- | --------------------- |
| **Turnip**       | Spring          | 4 days           | No          | 1                 | 40g            | 4                 | Simple leafy sprout → bulb. |
| **Carrot**       | Spring/Fall     | 5 days           | No          | 1-2               | 50g            | 4                 | Orange tops visible at final stage. |
| **Strawberry**   | Spring          | 8 days           | Yes         | 2-4 berries       | 80g each       | 5                 | Flowering vine, bright red fruits. |
| **Blueberry**    | Summer          | 9 days           | Yes         | 3 berries         | 90g each       | 5                 | Blue fruit clusters, bushy plant. |
| **Corn**         | Summer/Fall     | 14 days          | Yes         | 2 ears            | 120g each      | 6                 | Tall stalk, yellow kernels. |
| **Tomato**       | Summer          | 8 days           | Yes         | 2-3 tomatoes      | 85g each       | 5                 | Tomato cage asset, hanging fruits. |
| **Pumpkin**      | Fall            | 13 days          | No          | 1 pumpkin         | 250g           | 6                 | Large round fruit, vine-based. |
| **Cabbage**      | Fall            | 10 days          | No          | 1 cabbage         | 100g           | 5                 | Dense leafy design, vibrant green. |
| **Potato**       | Spring/Fall     | 6 days           | No          | 1-3 potatoes      | 60g each       | 4                 | Small leaves, dug-up animation. |
| **Grapes**       | Fall            | 10 days          | Yes         | 3 grapes          | 75g each       | 5                 | Trellis art needed, purple fruit clusters. |

## 🌺 Advanced & Magical Crops

| **Crop Name**    | **Season(s)**   | **Days to Grow** | **Regrow?** | **Harvest Yield** | **Base Value** | **Growth Stages** | **Notes for Artists** |
| ---------------- | --------------- | ---------------- | ----------- | ----------------- | -------------- | ----------------- | --------------------- |
| **Moonflower**   | Any (Night)     | 12 days          | No          | 1 flower          | 500g           | 6                 | Glowing petals, emits light at night. |
| **Starfruit**    | Summer          | 14 days          | No          | 1 fruit           | 700g           | 6                 | Sparkly sheen effect, rare treasure crop. |
| **Sunberry**     | Summer/Fall     | 10 days          | Yes         | 2 berries         | 150g each      | 5                 | Golden particles, sunray shine FX. |
| **Frostmelon**   | Winter (Greenhouse) | 15 days       | No          | 1 melon           | 800g           | 6                 | Semi-transparent blue melon, frosted leaves. |
| **Lunar Lotus**  | Any (Lake)      | 18 days          | No          | 1 lotus           | 1000g          | 6                 | Grows only on water tiles, glowing reflection. |
| **Shadow Pepper** | Fall/Winter    | 12 days          | Yes         | 3 peppers         | 180g each      | 5                 | Dark purple flame particle effect. |

## 🔹 Fertilizer & Soil Enhancements

| **Fertilizer Name** | **Effect**                       | **Recipe/Unlock** |
| ------------------- | -------------------------------- | ----------------- |
| Basic Fertilizer    | +10% quality chance              | Starter crafting |
| Growth Tonic        | -2 days growth                   | Mid-game quest reward |
| Miracle Compost     | +30% quality, +1 harvest yield   | Shrine ritual or merchant |
| Water Gem Soil      | No watering needed               | Crystal Lake rare reward |
| Lunar Essence Mix   | Unlocks "Any Season" growth in plots | Endgame shrine crafting |

## 🔹 Crop Growth Stages (Universal Asset Specs)

| **Stage**         | **Description**            | **Asset Notes** |
| ----------------- | -------------------------- | --------------- |
| **Seed Stage**    | Small brown seedling tile. | Minimal animation, single-frame. |
| **Sprout Stage**  | Tiny green sprout, 2 leaves. | Add idle sway. |
| **Early Growth**  | Slightly larger plant.     | 2–3 animation frames, seasonal tinting. |
| **Mid Growth**    | Taller, bushier, crop buds visible. | Optional flower bloom for crops. |
| **Pre-Harvest**   | Fully grown, ripe.         | Bright highlights, heavier shading. |
| **Harvested Soil** | Empty soil patch with roots left. | Optional moisture effect. |

## 🔹 Greenhouse & Late-Game Farming

- **Greenhouse Unlock:** Year 1 winter quest. Allows year-round growth.
- **Magic Fields:** Late-game shrine unlock; allows **Moonflower, Lunar Lotus, Shadow Pepper** growth anywhere.
- **Auto-Systems:** Sprinklers, drones, auto-collect systems to reduce grind and encourage large farms.

## 🔹 Seasonal Farm Visuals

| **Season** | **Palette Changes**             | **FX Layer** |
| ---------- | ------------------------------- | ------------ |
| Spring     | Bright greens, flower patches.  | Light flower petal particle effect. |
| Summer     | Vibrant colors, lush leaves.    | Occasional heat haze. |
| Fall       | Warm orange/brown tones.        | Falling leaves. |
| Winter     | Snow overlay, frozen soil visuals. | Snow particle system. |

---
**Back to:** [[Moon Farming GDD]]
