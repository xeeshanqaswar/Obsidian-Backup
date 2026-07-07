
---

## 1️⃣ Executive Overview

**Genre:** Casual Simulation / Time-Management / Cozy Builder  
**Platform:** iOS (Primary), Android (Secondary)  
**Target Audience:** Casual players (13–40), Cozy simulation fans

### Core Fantasy
> Run your own colorful ice cream shop, craft beautiful frozen creations, satisfy customers, and grow from a small street cart into a premium dessert destination.

---

## 2️⃣ Core Gameplay Pillars

1. **Creative Assembly** — Build visually satisfying ice cream orders.
2. **Customer Satisfaction** — Speed + accuracy + presentation.
3. **Progression & Expansion** — Unlock flavors, toppings, equipment.
4. **Customization** — Personalize shop appearance and serving styles.
5. **Seasonal Variety** — Limited-time flavors and themed events.

---

## 3️⃣ Core Gameplay Loop

1. Customer enters shop  
2. Customer places order  
3. Player prepares ice cream  
4. Serve order  
5. Earn coins + tips  
6. Upgrade or unlock new ingredients  
7. Repeat with increased complexity  

---

## 4️⃣ Core Systems

### 4.1 Ice Cream Assembly System

An order may include:

- **Container** (cone or cup)
- **Number of scoops** (1–3)
- **Flavor selection**
- **Toppings**
- **Sauce drizzle**
- Optional: **whipped cream** or **cherry**

#### Assembly Interaction

| Step | Interaction Type |
| --- | --- |
| Select container | Tap |
| Scoop ice cream | Drag & release |
| Add toppings | Tap |
| Add sauce | Swipe drizzle gesture |
| Finalize | Swipe to serve |

**Failure conditions**
- Wrong flavor
- Missing topping
- Incorrect container
- Patience timer expires

---

### 4.2 Containers

**Starter containers**
- Cup
- Sugar Cone
- Waffle Cone

**Advanced containers**
- Chocolate-dipped cone
- Sprinkle-coated cone
- Glass sundae bowl
- Premium layered parfait cup

**Container affects**
- Base order value
- Visual appeal bonus
- Tip multiplier

---

### 4.3 Flavors

**Starter flavors (MVP)**
- Vanilla
- Chocolate
- Strawberry
- Mint Chip
- Mango
- Cookies & Cream

**Mid-tier unlocks**
- Pistachio
- Matcha
- Blueberry
- Peanut Butter
- Salted Caramel

**Seasonal examples**
- Pumpkin Spice (Autumn)
- Candy Cane (Winter)
- Tropical Coconut (Summer)

---

### 4.4 Toppings

**Basic**
- Sprinkles
- Chocolate chips
- Crushed nuts
- Marshmallows

**Advanced**
- Cookie crumble
- Brownie bits
- Fresh fruit slices
- Candy pieces

Each topping:
- Adds preparation time
- Increases order value
- Impacts satisfaction score

---

### 4.5 Sauce System

**Available sauces**
- Chocolate syrup
- Caramel
- Strawberry
- Hot fudge

**Precision bonus**
Players earn higher tips if:
- Sauce is evenly distributed
- Coverage matches request
- No over-pouring

---

## 5️⃣ Customer System

### Customer State Flow
Enter → Queue → Order → Waiting → Served → Exit

### Customer Variables
- PatienceTimer
- MoodLevel
- TipChance
- OrderComplexity

### Customer Types

| Type | Behavior |
| --- | --- |
| Casual | Simple orders |
| Family | Multi-scoop orders |
| Trendy | Exotic flavors |
| VIP | High tips, low patience |

---

## 6️⃣ Economy System

### Currency Types

| Currency | Source | Usage |
| --- | --- | --- |
| Coins | Orders | Upgrades |
| Tips | Fast service | Cosmetic unlocks |
| Premium Currency | IAP | Boosters & skins |

### Order Value Formula

Final Reward =  
(Base Container Value  
+ Scoop Value × Scoop Count  
+ Topping Value  
+ Sauce Bonus)  
× Speed Multiplier

---

## 7️⃣ Upgrade System

### Equipment Upgrades
1. **Freezer Unit** — Reduces scoop delay; unlocks more flavor slots (as upgrades).  
2. **Counter Space** — Increases queue capacity.  
3. **Topping Station** — Unlocks additional topping types.  
4. **Sauce Dispenser** — Improves drizzle precision window.

### Upgrade Scaling Example

| Level | Cost | Effect |
| --- | ---: | --- |
| 1 → 2 | 200 | +5% speed |
| 2 → 3 | 500 | +10% speed |
| 3 → 4 | 1200 | +15% speed |

---

## 8️⃣ Shop Customization

Unlockable elements:
- Wall colors
- Floor tiles
- Neon signs
- Counter skins
- Staff uniforms

Customization benefits:
- Increased tip percentage
- Increased customer flow

---

## 9️⃣ Game Modes

- **Story Mode** — Progress through shop expansion chapters.
- **Daily Challenge** — Serve X perfect orders within a time limit.
- **Endless Mode** — Continuous customer flow.
- **Event Mode** — Seasonal ingredients and decorations.

---

## 🔟 Art Direction

**Visual style**
- Bright pastel palette
- Glossy, satisfying textures
- Stylized realism
- Clean, rounded UI

**Visual asset requirements**
- 15–20 flavor texture variants
- 10+ topping visuals
- Drizzle animation system
- Optional melt simulation (late-game difficulty mechanic)

---

## 1️⃣1️⃣ Audio Design

- Freezer hum ambience
- Scoop scraping sound
- Topping sprinkle sound
- Sauce drizzle sound
- Coin reward sound
- Customer reaction cues

---

## 1️⃣2️⃣ Monetization Plan

### IAP Packs

| Pack | Price |
| --- | ---: |
| Starter Scoop | $2.99 |
| Sweet Bundle | $9.99 |
| Ice Cream Empire Pack | $19.99 |

### Rewarded Ads
- Double tips
- Instant upgrade finish
- Free rare ingredient

---

## 1️⃣3️⃣ Technical Architecture (Unity)

**Core systems**
- ScriptableObjects: Flavors, Toppings, Containers
- Customer AI state machine
- Queue manager
- Economy manager
- Save/Load system

### Sample Save Data

```json
{
  "coins": 1500,
  "freezerLevel": 2,
  "counterLevel": 3,
  "unlockedFlavors": ["vanilla", "chocolate", "mango"],
  "decorItems": ["pink_walls"]
}
```

---

## 1️⃣4️⃣ Production Timeline

| Phase | Duration |
| --- | --- |
| Preproduction | 3 weeks |
| Vertical Slice | 4 weeks |
| MVP Build | 8 weeks |
| Soft Launch | Month 4 |
| Global Launch | Month 6 |

---

## 1️⃣5️⃣ Risk Assessment

| Risk | Mitigation |
| --- | --- |
| Repetitive gameplay | Add ingredient layers + new customer types |
| Economy inflation | Controlled unlock pacing + price scaling |
| Visual clutter | Clear UI layering + ingredient grouping |
| Too easy | Introduce impatient VIP customers + harder recipes |

---

## 🎯 Final Success Criteria

The game succeeds if:
- Assembly feels satisfying
- Visuals are vibrant and appealing
- Progression feels rewarding
- Customization feels meaningful
