# Truck Simulator: Ultimate — Reverse-Engineered Game Scope + GDD

**Reference:** Truck Simulator: Ultimate — Zuuks Games  
**Research snapshot:** September 3, 2026  
**Primary reference build:** current Google Play / iOS public product as of 2026  
**Document purpose:** functional product reconstruction for an original truck-simulation + logistics-management game.

Truck Simulator: Ultimate is commercially significant rather than a small niche reference: Google Play currently shows **100M+ downloads, 4.3 stars and roughly 2.56M reviews**. The current store description confirms **42+ trucks, 100+ cities, multiplayer seasons, freight auctions, employee/company management, office customization, truck modification, used trucks, DLC, rest stops, fuel pricing, toll roads and weather**.

Throughout this document:

- **[C] Confirmed** — directly documented or visibly evidenced.
- **[SI] Strongly Inferred** — multiple pieces of evidence support it.
- **[E] Estimated** — a production/economy estimate where exact values are unavailable.
- **[P] Proposed** — recommended implementation for an original comparable product.

---

# 1. Executive Product Overview

| Attribute | Assessment |
|---|---|
| Genre | **[C]** Vehicle simulation |
| Subgenre | Truck-driving simulator + logistics-company tycoon |
| Core fantasy | Start as an owner-driver and build an international trucking empire |
| Target audience | Mobile vehicle-sim fans; truck enthusiasts; light management/tycoon players |
| Platform | **[C]** Android, iOS/iPadOS; Windows availability also surfaced on Google Play |
| Camera | **[C]** Multi-camera: cockpit/first-person plus external driving views |
| Session length | **[SI]** 10–60+ minutes depending on delivery |
| Primary motivation | Drive realistically, acquire better trucks, expand company income |
| Differentiator | Truck simulation and idle/business-management progression in the same product |
| Competitive position | More meta-heavy than a pure mobile truck-driving sim |
| Complexity | **High** |
| Content depth | **High**, mostly route/truck/cargo combinatorics |
| Monetization | **[C]** Ads + currency IAP + bundles + VIP subscription |
| Multiplayer dependency | **Medium**; single-player is substantial |
| LiveOps dependency | **Medium**; multiplayer seasons and offers exist, but core game is evergreen |
| Production risk | World content, vehicle fidelity, long-session stability, economy tuning |

The product is essentially **two games sharing one economy**. One half is a mobile truck simulator in which the player accepts a cargo contract, couples to a trailer, follows GPS through highways and towns, obeys traffic rules, manages fuel/hunger/fatigue, and completes delivery. The second half is a logistics tycoon: earnings are reinvested into trucks, drivers, licenses, office equipment and additional offices, allowing AI employees to run jobs and create passive income. The business layer converts driving revenue into permanent expansion; the driving layer gives meaning and identity to the business.

---

# 2. Core Gameplay Loop

## 2.1 Macro loop

```text
HOME / COMPANY
      ↓
Browse Available Freight
      ↓
Select / Bid on Contract
      ↓
Choose:
 ┌────┴─────┐
 ↓          ↓
Drive       Assign Driver
Personally  to Job
 ↓          ↓
Prepare     Wait / Timer
Truck       ↓
 ↓          Collect Income
Pick Up Cargo
 ↓
Drive Route
 ↓
Fuel / Eat / Rest / Tolls
 ↓
Deliver & Park
 ↓
Contract Revenue
 ↓
Cash + Optional Ad/Premium Rewards
 ↓
Buy Truck / Hire Driver / License / Office / Upgrade
 ↓
Higher Capacity + New Freight
 ↓
Repeat
```

The key structural insight is:

> **Driving is active income. Fleet management is scalable passive income.**

That relationship is the primary progression engine.

## 2.2 Moment-to-moment loop

Every few seconds:

```text
Observe Road
→ Steer
→ Modulate throttle/brake
→ Read GPS
→ Manage traffic
→ Correct lane/position
→ Use mirrors/camera
→ Repeat
```

Intermittently:

```text
Turn signal
→ junction / lane change
→ avoid penalty/collision
```

Longer-interval interactions include cruise control, headlights, wipers, horn, fuel/rest stops and camera switching.

## 2.3 Match / delivery loop

```text
Contract Selection
↓
Truck + Driver Assignment
↓
Spawn at Depot
↓
Start Engine
↓
Locate Trailer
↓
Reverse + Couple
↓
Exit Yard
↓
Long-Haul Driving
↓
Optional Service Stops
↓
Destination Depot
↓
Position / Unload
↓
Job Results
↓
Income / Expenses / Bonus Options
```

Expenses can include fuel, food/rest, tolls, fines and accident/repair costs.

## 2.4 Session loop

A 20–30 minute player session is likely:

```text
Collect Driver Income
↓
Check New Contracts
↓
Assign 1–N AI Drivers
↓
Start Personal Contract
↓
Drive
↓
Complete Delivery
↓
Optional Rewarded Ad
↓
Upgrade / Buy / Hire
↓
Queue More AI Work
```

## 2.5 Daily loop

The documented systems suggest:

- **[C]** free daily bonus-wheel interaction.
- **[C]** additional wheel attempts through rewarded video.
- **[SI]** collect returning-driver income.
- refresh job selection.
- progress toward truck/office purchase.
- season/multiplayer participation.

## 2.6 Weekly / seasonal loop

**[C] Multiplayer seasons** include at least:

- joint cargo transport;
- races.

The public store does not expose season length or exact ranking mechanics.

## 2.7 Long-term loop

```text
Owner-Driver
↓
Second Truck
↓
First AI Driver
↓
Passive Revenue
↓
More Trucks + Drivers
↓
Cargo Licenses
↓
More Valuable Job Pool
↓
Office Upgrade
↓
New Offices
↓
International Expansion
↓
Premium / Specialized Fleet
↓
High-Efficiency Logistics Empire
```

---

# 3. Gameplay Mechanics

## 3.1 Truck locomotion

### Purpose
Create the primary simulation challenge.

### Input

- steering;
- accelerator;
- brake;
- P/D/R gear selector;
- handbrake;
- cruise control.

### Major variables

```text
enginePower
engineTorque
vehicleMass
cargoMass
gearState
wheelGrip
brakeForce
steeringAngle
speed
roadSlope
surfaceGrip
```

### Implementation [P]

Use a simplified wheel/axle simulation rather than arcade Rigidbody-only steering.

```text
DriveForce =
EngineTorque × GearRatio × DifferentialRatio × DrivetrainEfficiency

Acceleration =
(NetDriveForce - RollingResistance - Drag - GradeResistance)
÷ VehicleMass
```

For mobile, update full wheel physics only for player truck and nearby vehicles.

---

# 4. Controls & Camera

The known cockpit interaction set is unusually broad for mobile.

**Confirmed cockpit systems include:**

- ignition;
- GPS;
- indicators;
- hazards;
- headlights;
- wipers;
- sunshade;
- power windows;
- radio;
- air-conditioning;
- cockpit lighting;
- mirrors;
- horn;
- cruise control;
- handbrake.

## Suggested state model

```text
GARAGE
  Steering + pedals + camera
      ↓
TRAILER ALIGNMENT
  Prioritize external/reverse camera
      ↓
HIGHWAY
  Cockpit / chase
  Cruise control enabled
      ↓
SERVICE AREA
  Slow driving + contextual interaction
      ↓
DELIVERY PARK
  Top/reverse camera
  Precision steering
```

### Camera states [P]

1. cockpit driver;
2. dashboard;
3. hood;
4. third-person chase;
5. high rear;
6. trailer reverse;
7. orbit/photo;
8. cinematic arrival.

---

# 5. Game Modes

| Mode | Status | Structure |
|---|---|---|
| Career / Freight | **[C]** | Primary single-player contract gameplay |
| AI Driver Jobs | **[C]** | Delegate contract for timed passive revenue |
| Freight Auction | **[C]** | Bid for potentially higher-margin cargo |
| Multiplayer Cargo | **[C]** | Cooperative/shared cargo activity |
| Multiplayer Race | **[C]** | Competitive truck race |
| Used Truck Market | **[C]** | Vehicle acquisition meta system |
| Garage Practice | **[SI]** | Free manipulation/driving space |
| Seasonal Multiplayer | **[C]** | Recurring online competition |
| DLC Content | **[C]** | Modular extra content |

Online/used-truck access was historically reported to unlock after **four completed contracts**, although that should be treated as historical and potentially changed.

### Important monetization distinction

On iOS, the App Store currently states VIP Ultimate membership provides multiplayer access while subscribed.

That suggests multiplayer may currently be partly or fully subscription-gated on iOS. Do **not** assume Android behaves identically without hands-on verification.

---

# 6. Progression Architecture

The game does not appear to be level-map progression in the Candy Crush sense.

It uses **economic and capability progression**.

## 6.1 Player/company progression

```text
Company Creation
↓
Initial Truck + Office
↓
First Contracts
↓
Cash
↓
Office Equipment / Employees
↓
Second Vehicle
↓
Driver
↓
Automated Contract Revenue
↓
Cargo Licenses
↓
More Valuable Job Pool
↓
Office Capacity Upgrade
↓
Additional Offices
↓
International Fleet
```

## 6.2 VIP progression

**[C] VIP level acts as a meta gate.**

Historical evidence shows:

- better driver applicants can be VIP-gated;
- cargo licenses can be VIP-gated;
- trucks can require VIP thresholds;
- gold contributes to VIP progression.

This creates a second progression axis:

```text
Gold
↓
VIP Advancement
↓
Better Employees
+ Better Trucks
+ More Licenses
↓
Higher Revenue Potential
```

## 6.3 Content progression

**Confirmed content scale:**

- **42+ trucks**
- **100+ cities**
- multiple countries;
- American + European trucks;
- multiple cargo/job categories.

## Proposed unlock pacing

| Stage | Proposed Comparable Unlock |
|---|---|
| Tutorial | 1 truck, basic cargo |
| 1–3 contracts | office/equipment teaching |
| 4 contracts | used market / online teaser |
| 30–60 min | second truck |
| 1–2 hours | first driver |
| Day 1–2 | second cargo license |
| Day 2–4 | office upgrade |
| Week 1 | second office |
| Long-term | country network + specialized fleet |

---

# 7. Economy Reverse Engineering

## 7.1 Resource taxonomy

| Resource | Type | Earned From | Spent On | Scarcity | Monetized | Role |
|---|---|---|---|---|---|---|
| Cash / Money | Soft currency | Contracts, drivers, wheel, ads | Trucks, fuel, offices, employees, licenses, services | Medium | Yes | Main economy |
| Gold | Hard/premium | Ads/rewards/IAP | VIP progression, timers/gates | High | Yes | Premium progression |
| VIP Level | Meta resource | Gold / purchase-related progression | Not conventionally spent | High | Indirect | Unlock gate |
| Fuel | Runtime consumable | Purchased at station | Driving | Route-driven | Indirect | Operational cost |
| Hunger | Survival meter | Food | Depletes with travel | Low-medium | No direct evidence | Route interruption |
| Stamina/Fatigue | Survival meter | Motel/rest | Depletes with travel | Low-medium | No direct evidence | Route interruption |
| Employee Time | Time resource | Natural completion | AI jobs | Medium | Possibly gold | Idle economy gate |
| Cargo License | Permanent unlock | Purchased | — | Medium | Gold/VIP influences access | Expands jobs |
| Truck | Capital asset | Purchase/IAP/VIP | Assigned to player/driver | High | Yes | Revenue capacity |
| Office Slot | Capacity | Upgrade | Trucks/employees | High | Indirect | Fleet cap |
| Ad Opportunity | Attention resource | Time/cooldown | Wheel / multiplier | Limited | N/A | Monetization |

There is **no evidence of a classic mobile “energy/lives” system restricting contract starts.**

Instead, the game uses **in-world resource attrition**—fuel, hunger and fatigue.

---

# 8. Economy Flow

```text
                   ┌───────────────┐
                   │    IAP        │
                   └──────┬────────┘
                          ↓
                       Gold/Cash
                          ↓
Contracts → Cash → Trucks / Drivers / Offices
    ↑                     ↓
    │                 Fleet Capacity
    │                     ↓
    └──── AI Driver Jobs ←┘
              ↓
         Passive Cash
              ↓
       Cargo Licenses
              ↓
      Better Job Access
              ↓
        Higher Revenue
```

Operational sinks:

```text
Revenue
  ↓
Fuel
Food
Rest
Tolls
Traffic Fines
Accident/Repair
Salary
Office Costs
```

## Design purpose

The crucial economy transformation is:

### Before employee automation
**Time → cash**

### After employee automation
**Capital → cash/time**

That creates an economic flywheel:

```text
More Capital
→ More Trucks
→ More Drivers
→ More Parallel Jobs
→ More Capital
```

The greatest balancing danger is runaway compounding.

---

# 9. Economy Balance Model

Public sources do not expose a reliable current price ladder, so the following is a **working [P] comparable economy**, not claimed reference values.

## Proposed launch economy

### Contract rewards

| Tier | Drive Time | Gross Reward |
|---|---:|---:|
| Local | 5–8 min | 2,000–4,000 |
| Regional | 8–15 min | 4,500–8,000 |
| Long Haul | 15–25 min | 9,000–18,000 |
| Specialized | 20–30 min | 15,000–30,000 |

Formula:

```text
BasePay =
DistanceKm × BaseRatePerKm

FinalPay =
BasePay
× CargoMultiplier
× DifficultyMultiplier
× LicenseMultiplier
+ CompletionBonus
- Expenses
```

Example:

```text
BaseRatePerKm       = 12
CargoMultiplier     = 1.15
DifficultyMultiplier= 1.10
Distance            = 500 km

Gross ≈ 500 × 12 × 1.15 × 1.10
      ≈ 7,590
```

## Proposed truck ladder

| Tier | Price |
|---|---:|
| Starter | 45K |
| Tier 2 | 80K |
| Tier 3 | 140K |
| Tier 4 | 250K |
| Premium | 400K |
| Heavy/Special | 600K+ |

## Driver model

```text
DriverNetProfit =
ContractRevenue
- DriverSalary
- FuelAllowance
- MaintenanceReserve
```

Suggested salary per completed job:

```text
Salary = Revenue × 8–18%
```

Higher-skilled drivers:

- complete faster;
- possibly unlock long haul;
- charge higher salary.

---

# 10. Early / Mid / Late Economy

## Early game

Player has:

- one truck;
- few licenses;
- little cash;
- no meaningful automation.

Primary pressure:

**“I need enough money for truck #2.”**

## Mid game

Player owns:

- 3–8 trucks;
- several drivers;
- 2+ offices;
- multiple cargo licenses.

Main decisions:

- truck vs office;
- driver quality vs salary;
- new market vs efficiency.

## Late game

Risk:

```text
Fleet → huge passive income → cash loses meaning
```

Control through:

- escalating truck prices;
- maintenance;
- employee costs;
- premium office tiers;
- license costs;
- used vehicle condition;
- fleet depreciation;
- high-end specialist contracts.

---

# 11. Energy / Lives System

### Classic energy
**[C] None identified.**

### Functional substitutes

The game has:

- fuel;
- hunger;
- stamina/exhaustion.

Product function:

- breaks up very long drives;
- adds route planning;
- creates soft-currency sinks;
- introduces roadside environments;
- reinforces simulation fantasy.

### Recommended model

```text
FuelConsumption =
Distance × TruckFuelRate × LoadFactor

HungerDrain =
RealDriveMinutes × HungerRate

FatigueDrain =
RealDriveMinutes × FatigueRate
```

---

# 12. Items, Equipment & Collections

## Truck entity

```yaml
Truck:
  truckId:
  manufacturer:
  model:
  regionType: EU|US
  tier:
  vipRequirement:
  cashPrice:
  premiumPrice:
  enginePower:
  engineTorque:
  engineCapacity:
  fuelCapacity:
  mass:
  maxSpeed:
  handling:
  axleLayout:
  compatibleTrailers: []
  owned:
  condition:
  mileage:
  customizationSlots: []
```

## Customization categories

The store explicitly confirms:

- lamps;
- bumpers;
- horns;
- cockpit lights;
- additional modification options.

Potential original taxonomy:

```text
Exterior
 ├ Wheels
 ├ Tires
 ├ Bumper
 ├ Lights
 ├ Paint
 └ Accessories

Cabin
 ├ Lighting
 ├ Dashboard accessories
 ├ Seat
 └ Decor

Mechanical
 ├ Engine
 ├ Gearbox
 ├ Fuel tank
 ├ Tires
 └ Brakes
```

---

# 13. Upgrade Systems

The publicly observable product emphasizes **vehicle acquisition/customization more clearly than conventional RPG-style truck leveling**.

For an original implementation:

```text
TruckPerformance =
BaseTruckStats
+ PartModifiers
+ ConditionModifier
```

Example:

```text
EnginePower =
BaseHP × (1 + EngineUpgradeLevel × 0.045)
```

Suggested upgrade costs:

```text
UpgradeCost =
BaseCost × 1.55^(Level-1)
```

---

# 14. Missions & Objective Systems

The game has cargo jobs rather than story “missions.”

The current store lists jobs such as:

- fashion shopping;
- gas/fuel;
- refrigerated cargo;
- money;
- food delivery;
- office supplies;
- cars;
- theme-park materials and others.

## Generic contract schema

```yaml
Contract:
  contractId:
  cargoType:
  originCity:
  destinationCity:
  distance:
  trailerType:
  requiredLicense:
  minTruckClass:
  expirationTime:
  aiCompletionTime:
  baseReward:
  bonusReward:
  penalties:
  auctionEligible:
  multiplayerEligible:
```

## Objective architecture

```yaml
Objective:
  type:
    - ReachDestination
    - CoupleTrailer
    - DeliverCargo
    - NoAccidents
    - UnderTime
    - FuelEfficiency
    - NoTrafficViolations
  target:
  progress:
  reward:
```

---

# 15. Events & LiveOps

The strongest confirmed LiveOps structure is **multiplayer seasons**.

```text
Season Opens
↓
Players Enter Online Mode
↓
Joint Cargo / Race
↓
Season Performance
↓
Rank / Leaderboard
↓
Season Reward
↓
Reset
```

## Proposed data-driven framework

```yaml
LiveEvent:
  eventId:
  eventType:
  startUtc:
  endUtc:
  eligibleRegions:
  requiredLevel:
  rulesetId:
  routePool:
  cargoPool:
  rewardTrack:
  leaderboardId:
  offerGroup:
  modifiers:
```

Event types:

1. delivery marathon;
2. cooperative freight target;
3. race season;
4. fuel-efficiency challenge;
5. manufacturer showcase;
6. specialist cargo week;
7. country expansion event.

---

# 16. Event Economy

Recommended model:

```text
Event Contract
↓
Event Points
↓
Personal Milestones
↓
Season Rank
↓
Cash / Gold / Cosmetics
```

For a collection event:

```text
Delivery
↓
Event Tokens
↓
Event Store
↓
Truck Paint / Accessory / Office Decor
```

---

# 17. Monetization Design

The game uses a hybrid model.

## Confirmed monetization

- ads;
- cash packs;
- gold packs;
- bundle offers;
- VIP Ultimate subscription;
- ad removal;
- VIP upgrade;
- branded welcome package.

## VIP proposition

Current App Store copy says VIP Ultimate includes:

- multiplayer while subscribed;
- monthly money;
- monthly gold;
- a truck;
- ads removed after trial.

This makes VIP simultaneously:

```text
Subscription
+ Content Access
+ Currency Stipend
+ Vehicle Reward
+ Ad Removal
```

---

# 18. Ad Design

Documented ad surfaces include:

### Rewarded wheel
Free spin plus additional ad-backed attempts.

### Post-contract gold
Rewarded ad → premium currency.

### Post-contract revenue multiplier
Rewarded ad → approximately doubled job cash in historical guide evidence.

Recommended safe pattern:

```text
Delivery complete
→ Optional ×2 cash

Daily wheel
→ Optional extra spin

No mid-drive forced ads
```

---

# 19. Store Architecture

Recommended tabs:

```text
STORE
├ Cash
├ Gold
├ Trucks
├ Bundles
├ VIP
└ Limited
```

Backend offer schema:

```yaml
StoreOffer:
  id:
  type:
  sku:
  displayPrice:
  contents:
    cash:
    gold:
    trucks:
    cosmetics:
  segment:
  minLevel:
  maxPurchases:
  startUtc:
  endUtc:
  priority:
  discountLabel:
  artKey:
```

---

# 20. Reward Architecture

```text
Contract Reward
├ Base Cash
├ Expenses Deducted
├ Possible Gold Ad
└ Possible Cash Multiplier Ad

Driver Contract
└ Passive Cash

Daily
└ Bonus Wheel

VIP
├ Monthly Cash
├ Gold
└ Truck

Season
└ Competitive Reward

IAP
└ Purchased Resource / Content
```

---

# 21. Retention Systems

## D0
- drive first truck;
- experience large vehicle physics;
- receive first payout;
- understand company fantasy.

## D1
- second truck progress;
- bonus wheel;
- unlock drivers;
- new cargo.

## D3
- first meaningful employee automation;
- better truck target.

## D7
- office expansion;
- larger fleet;
- specialized cargo;
- multiplayer season.

## D14
- second geography/office;
- fleet optimization.

## D30
- collection;
- premium trucks;
- company scale;
- season competition;
- social status.

---

# 22. Social Systems

Confirmed:

- multiplayer seasons;
- cooperative cargo;
- races;
- leaderboards.

No strong public evidence was found for:

- guilds;
- direct gifting;
- persistent team chat;
- friends economy.

---

# 23. PvP & Matchmaking

Recommended comparable design:

```text
Queue
↓
Check Region/Ping
↓
Determine Truck Performance Band
↓
Determine Player Rating Range
↓
Expand Search Over Time
↓
Create Room
↓
Load Same Route
↓
Countdown
↓
Race
↓
Server-validated Finish
↓
MMR / Season Points
```

Match on:

```text
PlayerMMR
+ TruckPerformanceBand
+ Latency
+ SeasonTier
```

---

# 24. AI Systems

## Traffic AI

### Traffic vehicle FSM

```text
Cruise
├ Follow
├ Brake
├ StopSignal
├ Yield
├ ChangeLane
├ Turn
└ Recover
```

### Utility modifiers

```text
laneScore =
RouteAlignment
+ SpeedAdvantage
- CollisionRisk
- LaneChangeCost
```

## Employee simulation

```text
ContractAssigned
→ TravelTimer
→ Completion
→ Revenue
→ Cooldown / Available
```

Use server timestamps.

---

# 25. UX / UI Architecture

Top-level navigation roughly structured around:

```text
JOBS
GARAGE
COMPANY
ONLINE
STORE
```

## Screen map

```text
Splash
↓
Authentication / Save
↓
Company Creation
├ Name
├ Avatar
├ Logo
└ Starting Region
↓
Main Hub
├ Jobs
│ ├ Job List
│ ├ Contract Detail
│ ├ Auction
│ └ Assign Driver / Drive
├ Garage
│ ├ My Trucks
│ ├ Dealer
│ ├ Used Market
│ ├ Customization
│ └ Wash/Service
├ Company
│ ├ Offices
│ ├ Employees
│ ├ Licenses
│ ├ Finance
│ └ Expansion Map
├ Online
│ ├ Season
│ ├ Cargo
│ ├ Race
│ └ Leaderboard
├ Store
│ ├ Cash
│ ├ Gold
│ ├ VIP
│ └ Bundles
└ Settings
```

---

# 26. Gameplay HUD

```text
TOP LEFT
Pause
Camera
Driver condition
Inventory

TOP CENTER
GPS / route

TOP RIGHT
Mirrors / status

BOTTOM LEFT
Steering control

BOTTOM RIGHT
Accelerator
Brake
Horn
Cruise
Handbrake

CABIN CONTROLS
Signals
Lights
Wipers
Radio
Windows
```

---

# 27. FTUE / Tutorial

## Recommended comparable FTUE

### 0–1 minute

```text
Logo
→ Company Name
→ Starting Region
→ Avatar
```

### 1–3 minutes

```text
Garage
→ Enter Truck
→ Start Engine
→ Basic Steering
```

### 3–5 minutes

```text
Reverse to Trailer
→ Couple
→ Exit Depot
```

### 5–10 minutes

```text
Short Guided Route
→ GPS
→ Traffic Signal
→ Arrival
```

### 10–12 minutes

```text
Delivery
→ First Cash Reward
→ Reward Multiplier Teaser
```

### 12–20 minutes

```text
Company Screen
→ Explain next truck
→ Introduce driver
→ Show long-term empire
```

---

# 28. Content Inventory

## Reference confirmed

| Content Type | Public Scope |
|---|---:|
| Trucks | 42+ |
| Cities | 100+ |
| Countries | Numerous / global |
| Radio stations | 250+ |
| Languages | 25+ |
| Truck archetypes | American + European |
| Cargo types | Many / license-driven |
| Multiplayer formats | At least 2 |

## Original launch recommendation

| Content | MVP | Soft Launch | Commercial |
|---|---:|---:|---:|
| Trucks | 4 | 10 | 24 |
| Truck brands | fictional 2 | 3 | 5 |
| Maps/regions | 1 | 2 | 4 |
| Cities | 8 | 20 | 50 |
| Cargo types | 8 | 18 | 35 |
| Trailers | 4 | 8 | 14 |
| Offices | 1 visual kit | 3 | 6 |
| Driver portraits | 12 | 30 | 60 |
| Service-stop layouts | 2 | 5 | 10 |
| Multiplayer modes | 0 | 1 | 2 |
| Events | 0 | 2 templates | 5+ |

---

# 29. Content Production Pipeline

## Truck

```text
Reference Research
↓
Concept / Brand Language
↓
High Poly
↓
Low Poly
↓
UV
↓
Textures
↓
Cabin Interior
↓
Rig / Wheels
↓
Lights
↓
Physics Setup
↓
Audio
↓
LOD
↓
Prefab
↓
Vehicle Config
↓
QA
```

## Road environment

```text
Region Style Guide
↓
Road Kit
↓
Terrain Tiles
↓
Intersection Library
↓
Town Modules
↓
Service Area Modules
↓
Vegetation
↓
Traffic Setup
↓
NavGraph
↓
Lighting
↓
Optimization
↓
QA
```

---

# 30. Art Scope

| Domain | Complexity |
|---|---|
| Truck exterior | Very High |
| Truck cockpit | Very High |
| Trailer | Medium |
| Road kit | Medium |
| Generic city architecture | Medium |
| Terrain | Medium |
| Traffic vehicles | Medium |
| Characters | Low/Medium |
| Office interior | Medium |
| VFX/weather | Medium |
| UI | Medium/High |

The biggest visual selling point is **vehicle fidelity**, not character fidelity.

---

# 31. Animation Requirements

Truck animation set:

- steering wheel;
- front wheels;
- suspension;
- gear selector;
- wipers;
- indicators;
- doors/windows;
- seat adjustment if visible;
- mirror controls;
- trailer coupling;
- fifth-wheel connection;
- cabin camera shake.

World:

- traffic cars;
- trucks;
- pedestrians where required;
- pumps;
- toll barriers;
- depot gates.

UI:

- currency flyouts;
- unlocks;
- truck acquisition;
- wheel spinner;
- season rank;
- store offers.

---

# 32. Audio Requirements

## Truck

Each major truck family needs:

- idle;
- low RPM;
- mid RPM;
- high RPM;
- acceleration;
- deceleration;
- turbo;
- air brake;
- horn;
- reverse beep where applicable;
- indicator;
- door/window;
- suspension noise.

## Environment

- highway bed;
- city;
- rain;
- thunder;
- wind;
- gas station;
- depot;
- motel/rest stop;
- traffic.

## UI

Around 30–50 shared sounds.

---

# 33. Technical Architecture

```text
                     ┌──────────────────┐
                     │ Mobile Client    │
                     │ Unity / Unreal   │
                     └────────┬─────────┘
                              │ HTTPS/WSS
                              ↓
                    ┌────────────────────┐
                    │ API Gateway/Auth   │
                    └─────────┬──────────┘
                              │
        ┌─────────────────────┼────────────────────────┐
        ↓                     ↓                        ↓
 Player Service        Economy Service          Multiplayer
        │                     │                        │
        ├ Inventory           ├ Wallet                 ├ Matchmaking
        ├ Progression         ├ Rewards                ├ Rooms
        ├ Fleet               ├ Purchases              └ Results
        └ Offices             └ Offers

        ┌─────────────────────┼────────────────────────┐
        ↓                     ↓                        ↓
 Mission Service       LiveOps Service          Leaderboards
        │                     │
        └ Job Generator       ├ Events
                              └ Remote Config

                              ↓
                        Analytics/CDP
```

---

# 34. Client Feature Architecture

```text
Core
├ Bootstrap
├ Save
├ Config
└ Services

Gameplay
├ VehiclePhysics
├ Trailer
├ Traffic
├ Roads
├ GPS
├ Weather
├ ServiceStops
└ Delivery

Company
├ Offices
├ Employees
├ Fleet
├ Licenses
└ Finance

Economy
├ Wallet
├ Rewards
├ Pricing
└ Costs

Garage
├ TruckInventory
├ Dealer
├ UsedMarket
├ Customization
└ Maintenance

Online
├ Matchmaking
├ Season
├ Race
└ CoopCargo

UI
Audio
Analytics
Ads
IAP
RemoteConfig
Localization
```

---

# 35. Backend Data Models

## Player

```json
{
  "playerId": "uuid",
  "companyName": "string",
  "level": 8,
  "vipLevel": 3,
  "homeOfficeId": "office_01",
  "createdAt": "utc"
}
```

## Wallet

```json
{
  "cash": 128500,
  "gold": 120
}
```

## Truck ownership

```json
{
  "instanceId": "uuid",
  "truckId": "truck_04",
  "officeId": "office_02",
  "assignedDriverId": null,
  "mileage": 15230,
  "fuel": 340,
  "condition": 0.92,
  "customization": {}
}
```

## Employee

```json
{
  "employeeId": "uuid",
  "type": "driver",
  "skill": 3,
  "salaryRate": 0.12,
  "officeId": "office_02",
  "state": "busy",
  "jobCompleteAt": "utc"
}
```

## Job

```json
{
  "jobId": "job_982",
  "origin": "city_10",
  "destination": "city_13",
  "cargo": "cargo_food",
  "distance": 420,
  "grossReward": 7200,
  "license": "refrigerated",
  "expiresAt": "utc"
}
```

---

# 36. Remote Configuration

Remote configure:

- job payout;
- cargo multipliers;
- job spawn weighting;
- fuel prices;
- fine values;
- AI driver times;
- salaries;
- truck prices;
- license prices;
- office prices;
- VIP requirements;
- gold rewards;
- ad reward multipliers;
- wheel probabilities;
- event schedules;
- leaderboard rules;
- store offers;
- IAP mappings;
- used-market rotation;
- multiplayer rules;
- traffic density;
- weather probabilities.

---

# 37. Analytics Tracking Plan

| Event | Key Parameters |
|---|---|
| `session_start` | player_level, cash, gold, fleet_size |
| `tutorial_step` | step_id, completed |
| `job_impression` | cargo, distance, reward |
| `job_accept` | job_id, cargo, expected_profit |
| `job_start` | truck_id, origin, destination |
| `trailer_attached` | time_to_attach |
| `fuel_purchase` | liters, price |
| `rest_stop` | type, cost |
| `traffic_violation` | type, cost |
| `collision` | speed, damage |
| `job_complete` | time, reward, expenses, profit |
| `job_fail` | reason |
| `driver_job_assign` | driver_id, reward, duration |
| `driver_job_collect` | revenue |
| `truck_purchase` | truck_id, currency, price |
| `employee_hire` | role, salary |
| `office_purchase` | country, cost |
| `license_purchase` | license_id |
| `currency_earned` | currency, amount, source |
| `currency_spent` | currency, amount, sink |
| `ad_offer` | placement |
| `ad_complete` | placement, reward |
| `iap_complete` | product_id, price |
| `season_enter` | season_id |
| `multiplayer_match` | result, mode |

---

# 38. KPIs

- D1 / D7 / D30 retention;
- sessions/user;
- session duration;
- contracts/player/day;
- completion rate;
- average drive duration;
- truck purchase interval;
- driver hire interval;
- fleet size by day;
- office expansion rate;
- cash earned/day;
- cash spent/day;
- sink/source ratio;
- passive vs active earnings;
- gold earn/spend;
- time to second truck;
- time to first driver.

### Particularly important

```text
Passive Income ÷ Total Income
```

Recommended target [P]:

```text
Early: 0–15%
Mid:   25–50%
Late:  50–70%
```

---

# 39. Notification Strategy

| Trigger | Purpose |
|---|---|
| Driver completed job | Return to collect / reassign |
| New freight market | New jobs available |
| Daily reward | Return habit |
| Season ending | Competitive urgency |
| Used truck available | Collection target |
| Limited offer | Commercial reminder |
| New truck/content | Re-engagement |

---

# 40. Edge Cases & Failure States

## Disconnect during single-player drive

Store locally:

```text
jobId
truckTransform
trailerTransform
fuel
damage
routeProgress
expenses
```

Checkpoint every 20–60 seconds.

## Duplicate contract completion

```text
RewardTransactionId =
Hash(playerId + contractId + attemptId)
```

## Purchase interruption

```text
Platform Receipt
→ Backend Verification
→ Entitlement Transaction
→ Wallet
```

## Driver timer cheating

Never use device clock.

---

# 41. Anti-Cheat / Abuse Prevention

Server authoritative:

- wallet;
- gold;
- IAP;
- inventory;
- truck ownership;
- license ownership;
- AI job timestamps;
- multiplayer outcomes;
- season rank.

Driving can be client simulated, but validate results heuristically.

```text
distance / elapsedTime > impossibleSpeed
→ reject or flag

fuelUsed << physical minimum
→ flag

contract completed before MinimumExpectedDuration
→ flag
```

---

# 42. Performance Requirements

Recommended targets:

### FPS
- low-end: stable 30 FPS;
- mid/high: 60 FPS.

### Memory

```text
Low-end runtime < 1.2 GB
Mid-range < 1.8 GB
```

### Traffic LOD

```text
0–80m    full physics
80–200m  simplified physics
200m+    spline simulation
```

### Environment streaming

```text
Active Cell
+ Next 2 Cells
+ Previous Cell
```

---

# 43. Development Scope

## MVP

Goal: prove **“truck driving + company growth”**.

Include:

- 1 region;
- 4 trucks;
- 8 cargo types;
- 8 locations;
- trailer coupling;
- driving;
- traffic;
- GPS;
- fuel;
- basic jobs;
- cash;
- truck shop;
- 1 office;
- drivers;
- AI job timers;
- basic analytics.

Exclude:

- multiplayer;
- seasons;
- auction;
- used market;
- premium subscription;
- elaborate office customization;
- weather variety;
- DLC.

## Soft Launch

Add:

- 10 trucks;
- 20 cities;
- 2 regions;
- license system;
- office upgrades;
- used market;
- auctions;
- food/rest;
- ads;
- IAP;
- VIP;
- remote economy;
- events;
- one multiplayer mode.

## Global Launch

Add:

- 20–30 trucks;
- 40–60 cities;
- multiple regions;
- races;
- coop freight;
- seasons;
- deep customization;
- polished weather;
- strong event rotation;
- localized content.

## Post-launch

- manufacturers;
- trailers;
- convoy/clubs;
- more map regions;
- custom offices;
- DLC;
- special cargo;
- limited vehicles.

---

# 44. Development Roadmap

```text
1. Vehicle Prototype
        ↓
2. Trailer Physics
        ↓
3. Road + Traffic Prototype
        ↓
4. Delivery Vertical Slice
        ↓
5. Economy / Contract System
        ↓
6. Garage + Fleet
        ↓
7. Drivers / Passive Jobs
        ↓
8. Office Progression
        ↓
9. World Streaming
        ↓
10. Content Pipeline
        ↓
11. Monetization
        ↓
12. Backend / Remote Config
        ↓
13. LiveOps
        ↓
14. Multiplayer
        ↓
15. Soft Launch
        ↓
16. Economy / Retention Tuning
        ↓
17. Global Content Expansion
```

---

# 45. Team Requirements

## Lean prototype team

**8–10 people**

- producer/game designer;
- technical designer/economy;
- 2 gameplay engineers;
- 1 generalist/backend engineer;
- environment artist;
- vehicle artist;
- UI/UX;
- QA;
- shared audio/VFX.

## Recommended commercial team

**18–25**

- producer;
- product manager;
- systems/economy designer;
- gameplay designer;
- 4–5 client engineers;
- 2 backend engineers;
- technical artist;
- 2 vehicle artists;
- 2 environment artists;
- UI artist;
- UX designer;
- animator;
- VFX;
- audio;
- 2–3 QA;
- data analyst.

## Large-content production

**35–50+**

---

# 46. Effort Estimation

| Feature | Scope | Technical Risk | Content Risk | Backend |
|---|---|---|---|---|
| Truck physics | Large | High | Low | No |
| Trailer physics | Large | High | Low | No |
| Traffic | Very Large | High | Medium | No |
| Road/world streaming | Very Large | High | High | No |
| Contract generator | Medium | Low | Medium | Yes |
| Garage | Medium | Medium | Medium | Yes |
| Drivers | Medium | Low | Low | Yes |
| Office system | Medium | Low | Medium | Yes |
| Economy | Large | Medium | Low | Yes |
| Truck customization | Large | Medium | High | Yes |
| Used market | Medium | Low | Medium | Yes |
| Auctions | Medium | Medium | Low | Yes |
| Fuel/rest | Medium | Low | Medium | Partial |
| Weather | Large | Medium | High | No |
| Multiplayer race | Very Large | Very High | Medium | Critical |
| Coop freight | Very Large | High | Medium | Critical |
| Seasons | Large | Medium | Medium | Critical |
| Store/IAP | Medium | Medium | Low | Critical |
| Remote LiveOps | Large | Medium | Low | Critical |
| DLC | Large | High | High | Yes |

---

# 47. Feature Dependency Matrix

```text
Vehicle Physics
    ↓
Trailer
    ↓
Delivery
    ↓
Contracts
    ↓
Economy
 ┌──┼────────┐
 ↓  ↓        ↓
Garage Drivers Licenses
 ↓     ↓
Fleet  Passive Income
 └─────┬──────┘
       ↓
Office Expansion
       ↓
Long-Term Progression
```

Critical path:

1. vehicle feel;
2. trailer handling;
3. world route;
4. delivery completion;
5. economy;
6. fleet automation.

---

# 48. Replica Difficulty Analysis

## Easy to reproduce

- wallet;
- store;
- jobs UI;
- employee timers;
- licenses;
- office slots;
- daily reward;
- truck dealer;
- ad multipliers.

## Moderately difficult

- scalable economy;
- truck customization;
- GPS;
- contract generation;
- rest/fuel interactions;
- used market;
- auction UX.

## Difficult

- satisfying truck physics;
- articulated trailer behavior;
- competent traffic;
- mobile world streaming;
- low-end optimization;
- high-quality cockpits.

## Very difficult

- 40+ high-fidelity trucks;
- 100+ city-scale content;
- multiplayer races with vehicle physics;
- global QA matrix;
- licensing major real manufacturers;
- maintaining long drive sessions without crashes.

---

# 49. Minimum Content Needed to Feel Complete

A believable original launch could use:

- **16 trucks**
- **30 locations**
- **3 visually distinct regions**
- **12 trailer types**
- **24 cargo categories**
- **10 cargo licenses**
- **40 employee portraits**
- **4 office tiers**
- **8 service-area variants**
- **4 weather presets**
- **3 depot families**
- **2 multiplayer formats**
- **3 LiveOps templates**
- **60+ customization items**

Use combinatorics:

```text
30 Cities
× 24 Cargo Types
× 12 Trailers
× Variable Distance
× Weather
× Daytime
× Reward Tier
```

---

# 50. Proposed Original Version

## Haul Empire

Preserve:

- active driving + passive logistics;
- long-haul contracts;
- trucking company;
- vehicle acquisition;
- employees;
- offices;
- route economy;
- licenses;
- seasonal online play.

Differentiate:

Make the world fictional rather than nominally recreating real cities.

Three launch regions:

```text
REDWOOD COAST
Forests / mountain highways

SUNBELT
Desert / interstate / industrial cities

NORTHLAND
Snow / steep grades / ports
```

Create fictional manufacturers:

- Atlas;
- Sterling Haul;
- Nordwerk;
- Bellgrave;
- Kestrel Motors.

Contract types:

```text
Standard Freight
Fragile
Refrigerated
Hazmat
Oversized
Express
Night Cargo
Convoy
```

Driver specializations:

```text
Long Haul
Fuel Efficient
Fast
Fragile Cargo
Hazmat
Heavy Haul
```

---

# 51. Improved Original Economy Philosophy

Rather than:

```text
More Truck
= More Money
```

use:

```text
Truck
+ Driver
+ License
+ Region Demand
+ Cargo Compatibility
= Profitability
```

Example:

```text
ExpectedProfit =
ContractBase
× MarketDemand
× DriverSkill
× TruckEfficiency
- Fuel
- Salary
- Maintenance
```

---

# 52. Improved Freight Market

Suggested job-generation model:

```text
Origin City produces:
Food
Machinery
Timber

Destination City demands:
Food 1.4×
Machinery 0.9×
Timber 1.2×
```

Then:

```text
Reward =
DistanceRate
× CargoValue
× DemandMultiplier
× Difficulty
```

---

# 53. Biggest UX/Product Lesson

The game succeeds structurally because every system reinforces the same fantasy.

```text
Drive better
↓
Earn more
↓
Buy trucks
↓
Hire people
↓
Expand company
↓
Unlock freight
↓
Have more reasons to drive
```

---

# 54. Unknowns Requiring Hands-On Gameplay

- exact current FTUE steps;
- exact starting cash;
- exact starting truck;
- current truck-price ladder;
- exact VIP level formula;
- exact gold cost per VIP level;
- exact maximum VIP level;
- all employee categories;
- office employee effects;
- exact employee salary mechanics;
- exact office tiers;
- office equipment bonuses;
- exact maximum trucks per office;
- exact job refresh cadence;
- exact freight-auction algorithm;
- exact current used-market refresh;
- vehicle depreciation rules;
- current truck maintenance formula;
- current fuel-price ranges;
- hunger/fatigue drain rate;
- exact failure state at zero hunger;
- exact failure state at zero stamina;
- whether toll/fine values scale;
- current cargo-license list;
- cargo-license costs;
- current online unlock condition;
- multiplayer server model;
- matchmaking variables;
- multiplayer race player count;
- co-op cargo synchronization rules;
- season duration;
- season reward ladder;
- bots in multiplayer;
- current notification strategy;
- exact current ad frequency;
- whether ad frequency is segmented;
- Android-specific VIP terms;
- all DLC functionality;
- current event cadence;
- whether VIP subscription is the only route to multiplayer on every platform.

---

# 55. Research Conflicts / Caveats

### Ads
Some players report very limited ads outside trip boundaries; others complain of substantial ad pressure. Therefore ad frequency is likely version-, segment-, territory-, or purchase-dependent.

### World geography
The game markets a global city network, but recent reviews indicate routes often reuse environments and distances are not literal geographic simulation.

### Multiplayer
Google Play markets multiplayer as a feature, while iOS currently states VIP Ultimate grants multiplayer while subscribed. Treat exact access rules as platform/version dependent until tested.

### Content count
Older videos describe fewer trucks; current official listings say 42+. This is normal content expansion.

---

# 56. Final Developer Blueprint

## Game pillars

### 1. Feel Like a Truck Driver
Heavy, deliberate vehicles; cockpit interaction; trailer handling; road rules.

### 2. Build a Logistics Empire
Every successful delivery contributes to fleet/company growth.

### 3. Own the Fleet
Vehicles must be desirable both mechanically and aesthetically.

### 4. The Road Is the Challenge
Traffic, fuel, fatigue, cargo, weather and distance create variation.

### 5. Grow Beyond Yourself
Drivers and offices turn active success into scalable business.

## Core loop

```text
Select Freight
↓
Drive Cargo
↓
Manage Route Costs
↓
Deliver
↓
Earn Profit
↓
Invest in Fleet
↓
Hire Drivers
↓
Expand Offices
↓
Unlock Better Contracts
↓
Repeat
```

## Economy

```text
SOFT
Cash

HARD
Gold

META
VIP
Licenses
Company Capacity

OPERATING
Fuel
Food
Rest
Maintenance

CAPITAL
Trucks
Offices
Drivers
```

## MVP Test

The MVP should prove exactly this:

> **Is manually driving cargo fun enough that players care about using the resulting money to expand a company?**

If that answer is no, do not build multiplayer or LiveOps.

---

# 57. Final Priority Matrix

| Priority | System | Why It Matters | Dependency | Scope |
|---|---|---|---|---|
| **P0** | Truck physics | Core fantasy | None | Large |
| **P0** | Steering/controls | Core playability | Truck physics | Medium |
| **P0** | Trailer system | Defines trucking gameplay | Physics | Large |
| **P0** | Road environment | Required gameplay space | None | Large |
| **P0** | Traffic AI | Driving challenge | Road | Very Large |
| **P0** | GPS/routes | Makes deliveries possible | World | Medium |
| **P0** | Contract lifecycle | Core session | Gameplay | Medium |
| **P0** | Delivery/parking | Success condition | Trailer | Medium |
| **P0** | Cash economy | Connects gameplay/meta | Contract | Medium |
| **P1** | Truck ownership | Core progression | Economy | Medium |
| **P1** | Truck dealer | Main sink | Inventory | Medium |
| **P1** | Company | Core differentiator | Economy | Large |
| **P1** | Drivers | Passive-income loop | Company | Medium |
| **P1** | AI job timers | Makes fleet meaningful | Backend | Medium |
| **P1** | Offices | Capacity progression | Company | Medium |
| **P1** | Licenses | Content progression | Economy | Medium |
| **P1** | Fuel | Simulation + sink | Gameplay | Small |
| **P1** | Save/backend | Commercial reliability | Core | Large |
| **P1** | Analytics | Needed for soft launch | All | Medium |
| **P2** | Used truck market | Economy variety | Inventory | Medium |
| **P2** | Freight auction | Economic depth | Jobs | Medium |
| **P2** | Food/rest | Route depth | World | Medium |
| **P2** | Customization | Collection/monetization | Truck | Large |
| **P2** | Weather | Simulation depth | World | Large |
| **P2** | Ads | Revenue | Economy | Medium |
| **P2** | IAP | Revenue | Backend | Medium |
| **P2** | VIP | Retention/revenue | IAP/config | Medium |
| **P2** | Remote Config | Live tuning | Backend | Large |
| **P2** | Multiplayer race | Commercial breadth | Networking | Very Large |
| **P2** | Seasons | Long-term retention | Multiplayer | Large |
| **P3** | Cooperative freight | Social depth | Multiplayer | Very Large |
| **P3** | Clubs/companies | Social retention | Social backend | Large |
| **P3** | DLC framework | Content expansion | Content pipeline | Large |
| **P3** | Advanced offices | Meta depth | Company | Medium |
| **P3** | Dynamic freight market | Strategic depth | Jobs/economy | Large |

---

# Production Takeaway

The reference game should **not** be scoped internally as “a truck driving game with menus.”

Its true product structure is:

```text
          ACTIVE SIMULATION
 Truck → Cargo → Route → Delivery
              │
              ↓
             CASH
              │
              ↓
       BUSINESS TYCOON
 Truck → Driver → Office → License
              │
              ↓
       PARALLEL REVENUE
              │
              ↓
      BIGGER COMPANY
              │
              └────────→ More Reasons to Drive
```

The **MVP does not need 42 trucks, 100 cities, multiplayer, real vehicle licenses or 250 radio stations**. The correct first milestone is a polished truck, believable trailer physics, one modular road region, a functioning freight economy, truck #2, and a hired driver who visibly changes the player's earning capacity.

If that 60–90 minute progression is compelling, the remaining product can scale outward into the much larger structure represented by Truck Simulator: Ultimate.
