
## 🔹 Design Philosophy

- **Minimalist but Warm:** Soft palettes and stylized icons to match cozy aesthetic.
- **Low Cognitive Load:** Information is layered (basic info upfront, deeper stats tucked away).
- **Controller & Touch Friendly:** Both Switch and Mobile usability considered.
- **Diegetic Immersion:** Menus are styled like a journal/map owned by the player.
- **Quick Actions:** Hotbars, radial menus, and shortcuts for repetitive actions (watering, tools).

## 🔹 Core HUD Layout

| **Element**           | **Location**       | **Function** |
| --------------------- | ------------------ | ------------ |
| **Time & Date**       | Top-left corner    | Shows day, season, weather, and time (AM/PM). |
| **Stamina Bar**       | Bottom-left, horizontal | Green bar; flashes red when low. |
| **Health Bar**        | Above stamina bar  | Visible only in combat zones. |
| **Currency Display**  | Top-right          | Shows gold and seasonal currency. |
| **Tool & Item Hotbar** | Bottom-center      | Scrollable 8-slot bar with tool icons. |
| **Mini-Map (Optional Toggle)** | Top-right, under currency | Shows local map, shrine markers, quest pings. |
| **Notification Pop-ups** | Top-center fade-in | Quest updates, achievements, festival reminders. |

## 🔹 Main Menu Flow

| **Menu Tab**               | **Description** |
| -------------------------- | --------------- |
| **Inventory**              | Grid of items, stack counts, drag/drop. |
| **Crafting**               | Recipe book, craft queue, resource highlights. |
| **Farm Management**        | Lists all animals, crop growth stages, machine timers. |
| **Skill Tree**             | Separate XP bars, perk unlock nodes. |
| **Map**                    | Stylized hand-drawn map with fast travel points. |
| **Quest Journal**          | Quest tracker with story progress. |
| **Social/Relationships**   | Portrait grid of NPCs, heart meter, last gift given. |
| **Settings**               | Save, load, options (volume, controls, UI scaling). |

## 🔹 Inventory System Details

| **Feature**               | **Implementation Details** |
| ------------------------- | -------------------------- |
| **Item Grid**             | 6x8 grid by default, expandable via backpack upgrades. |
| **Stacking**              | Stack up to 99 common items; special items don't stack. |
| **Item Rarity Borders**   | Color-coded (Common, Rare, Legendary). |
| **Quick Actions**         | "Hold to Favorite," "Auto-Equip," "Drop." |
| **Drag & Drop Touch Controls** | Swipe to rearrange inventory on mobile. |

## 🔹 Crafting UI

- **Tabbed Recipes:** Farming Tools, Artisan Gear, Cooking, Furniture, Magic Items.
- **Material Highlighting:** Missing ingredients shown in red, owned ones in green.
- **Preview Window:** Shows 3D rotating model of crafted item.
- **Craft Queue:** Multiple items can be queued (late-game upgrade).

## 🔹 Skill Tree Screen

- Circular node-based skill progression:
  - **Farming Tree:** Crop yield, seed efficiency, magical planting.
  - **Combat Tree:** Weapon perks, dodge roll, elemental skills.
  - **Fishing Tree:** Better rod tension, rare catches.
  - **Crafting Tree:** Machine efficiency, recipe unlocks.
- Each tree is visually themed (farming tree has vines, combat has swords).
- Player gets **1 Skill Point per level** to invest.

## 🔹 Quest Journal

| **Section**          | **Function** |
| -------------------- | ------------ |
| **Active Quests**    | List of current tasks, step-by-step objectives. |
| **Story Arc Tab**    | Shows narrative progress by chapter (Act 1–4). |
| **NPC Story Tab**    | Lists side quests by NPC, shows friendship level. |
| **Festival/Event Tab** | Displays seasonal events, rewards, countdown timers. |

## 🔹 Social/Relationship Screen

- NPC portraits in a grid (color-coded by relationship stage).
- Heart meter per NPC (5 hearts base, 10 for romance options).
- Tooltip shows last gift given, favorite items, birthdays.
- Clicking NPC portrait opens **dialogue history and questlines**.

## 🔹 Map & Travel UI

- **Hand-Drawn Map:** Stylized parchment look.
- **Points of Interest:** Shrines, NPC homes, dungeon entrances.
- **Fast Travel:** Click shrine icons (if unlocked).
- **Farm View:** Zoomed farm plan, crop/animal timers shown as icons.

## 🔹 Shops & Merchant Menus

- Shop interface styled like a **market stall:**
  - **Shop Inventory Grid:** Tabs for seeds, animals, furniture.
  - **Preview Models:** 3D view for furniture, mounts, cosmetics.
  - **Discount System:** Shows current sale %, tied to Charisma stat.
  - **Barter Mode:** Trade rare items instead of gold (special NPCs).

## 🔹 Festival-Specific UI

- **Festival Timers:** Clock overlay showing event start/end time.
- **Competition Scoreboard:** Live tally for contests (fishing, cooking).
- **Festival-Exclusive Shop:** Seasonal tokens instead of gold.
- **Photo Mode Button:** Capture event screenshots with frame overlays.

## 🔹 Controls Overview

| **Platform**   | **Input Notes** |
| -------------- | --------------- |
| **Switch**     | Radial menus mapped to triggers, hotbar scroll with bumpers. |
| **Mobile**     | Tap-to-move (optional joystick), swipe inventory management. |
| **PC (Optional)** | WASD movement, Q/E tool cycling, number key item slots. |

## 🔹 UX Considerations

- **Contextual Buttons:** If standing near crops, "Water" replaces "Use Tool."
- **Onboarding:** Hover tooltips for every new UI element.
- **Accessibility:** Colorblind-friendly borders, font scaling slider, haptic feedback for mobile.
- **Saving:** Auto-save on sleeping, manual save via journal.

---
**Back to:** [[Moon Farming GDD]]
