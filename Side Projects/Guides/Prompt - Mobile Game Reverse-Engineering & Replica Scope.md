

I will provide you with only a Google Play Store or Apple App Store link for a mobile game.

Your job is to deeply research, analyze, and reverse-engineer the game into a comprehensive **Game Scope + Game Design Document (GDD)** that a professional mobile game development team can use to build a functionally comparable game from scratch.

Do not create a superficial review of the game. Approach this as a combination of:

- Senior Game Designer
- Systems Designer
- Economy Designer
- Product Manager
- Technical Game Designer
- LiveOps Designer
- UX Designer
- Monetization Designer
- Producer / Scope Planner
- Competitive Intelligence Analyst

Use publicly available information from the store page, official website, gameplay videos, trailers, screenshots, community discussions, wikis, reviews, social media, developer material, guides, gameplay recordings, and other reliable sources.

Do not copy copyrighted source code, proprietary assets, exact character designs, logos, dialogue, music, or other protected creative expression. Reverse-engineer the **systems, mechanics, structure, progression, economy, UX patterns, content model, and product architecture** so the resulting document can guide development of an original game with comparable functionality.

---

# **1. Executive Product Overview**

Start with a concise explanation of the game:

- Genre
- Subgenre
- Core fantasy
- Target audience
- Platform
- Camera perspective
- Session length
- Primary player motivation
- Core differentiator
- Competitive positioning
- Estimated complexity
- Expected content depth
- Primary monetization model
- Multiplayer/social dependency
- LiveOps dependency

Then explain the game in one paragraph as if briefing a development team that has never played it.

---

# **2. Core Gameplay Loop**

Identify the complete player loop.

Break it into:

### **Moment-to-Moment Loop**

What the player repeatedly does every few seconds.

### **Match / Level Loop**

What happens from entering a gameplay session until completion.

### **Session Loop**

What the player typically does during a 5–30 minute session.

### **Daily Loop**

What motivates the player to return each day.

### **Weekly Loop**

Events, challenges, rankings, refreshes, rewards, etc.

### **Long-Term Loop**

Progression over weeks/months.

Represent the loops visually using text diagrams such as:

Home  
↓  
Select Mode  
↓  
Prepare Loadout  
↓  
Play  
↓  
Earn Rewards  
↓  
Upgrade / Unlock  
↓  
Progress  
↓  
Next Challenge

Explain what keeps each loop engaging.

---

# **3. Gameplay Mechanics**

Document every identifiable gameplay mechanic.

For each mechanic describe:

- Purpose
- Player input
- Rules
- Success condition
- Failure condition
- Variables
- Difficulty scaling
- Feedback
- Rewards
- Edge cases
- Dependencies
- Likely implementation approach

Examples include:

- Movement
- Shooting
- Timing
- Aiming
- Match-3
- Combat
- Building
- Dressing
- Resource collection
- Crafting
- Racing
- Puzzle solving
- Energy consumption
- AI opponents
- PvP
- Simulation
- Idle production

Create formulas or pseudocode where useful.

---

# **4. Controls & Camera**

Document:

- Input model
- Touch interactions
- Tap
- Hold
- Drag
- Swipe
- Pinch
- Virtual joystick
- Contextual controls
- Camera movement
- Camera states
- Camera transitions
- Cinematic cameras
- Input locking
- Aim assist
- Auto-play systems

Explain how controls change according to gameplay state.

---

# **5. Game Modes**

Identify every visible or probable game mode.

For each mode document:

- Purpose
- Unlock requirements
- Entry cost
- Match structure
- Number of players
- AI/PvP
- Rules
- Difficulty
- Rewards
- Progression impact
- Failure penalties
- Matchmaking
- Reset cadence
- Monetization hooks
- Content requirements

Clearly distinguish:

- Core modes
- Secondary modes
- Events
- Limited-time modes
- Social modes
- Competitive modes
- Tutorial modes

---

# **6. Progression Architecture**

Reverse-engineer the full progression system.

Cover:

### **Player Progression**

- Account level
- XP
- Unlocks
- Level requirements

### **Content Progression**

- Worlds
- Chapters
- Areas
- Levels
- Missions
- Episodes

### **Power Progression**

- Character stats
- Equipment
- Cards
- Clothing
- Vehicles
- Buildings
- Skills
- Talents

### **Meta Progression**

- Collections
- Achievements
- Prestige
- Rank
- League
- Pass progression

Create a progression map.

Example:

Tutorial  
↓  
Level 2  
↓  
Feature A Unlocks  
↓  
Level 5  
↓  
PvP  
↓  
Level 8  
↓  
Events  
↓  
Level 12  
↓  
Guilds

Estimate unlock pacing where exact information is unavailable.

Clearly label:

**Confirmed**

**Strongly Inferred**

**Estimated / Proposed**

---

# **7. Economy Reverse Engineering**

This section must be extremely detailed.

Identify every resource and currency.

Create a table containing:

|**Resource**|**Type**|**Earned From**|**Spent On**|**Scarcity**|**Monetized?**|**Role**|
|---|---|---|---|---|---|---|

Separate:

- Soft currency
- Hard currency
- Premium currency
- Energy
- Upgrade materials
- Event currency
- Crafting materials
- Tickets
- Keys
- Tokens
- XP
- Reputation
- Rank points

For each resource explain:

### **Sources**

Where it enters the economy.

### **Sinks**

Where it leaves the economy.

### **Faucets**

Repeatable generation sources.

### **Gates**

What restricts acquisition.

### **Conversion**

Whether resources convert into one another.

### **Scarcity**

How scarcity is created.

### **Monetization Relationship**

How the resource creates purchase pressure.

Create an economy flow diagram.

Example:

Gameplay  
↓  
Coins  
↓  
Upgrade Equipment  
↓  
Higher Difficulty  
↓  
Better Rewards

Premium Purchases  
↓  
Gems  
↓  
Energy / Premium Items / Speedups

---

# **8. Economy Balance Model**

Where possible, estimate numerical ranges.

Produce example balancing tables for:

- Currency earnings
- Upgrade costs
- XP requirements
- Energy costs
- Reward scaling
- Item prices
- Store bundles
- Event rewards

If exact values cannot be found, construct a **reasonable working economy model** inspired by the observed game.

Clearly label estimated numbers.

Explain:

- Early game economy
- Mid game economy
- Late game economy
- Inflation control
- Progression walls
- Currency pressure points
- Monetization pressure points

---

# **9. Energy / Lives System**

If applicable, explain:

- Energy cap
- Regeneration
- Session cost
- Refill mechanics
- Free refill sources
- Ad refills
- Premium refills
- Level-up refill
- Event energy
- Separate energy systems

Estimate how many sessions a player receives per day.

Explain why the system exists from a product perspective.

---

# **10. Items, Equipment & Collections**

Reverse-engineer the content taxonomy.

Examples:

- Characters
- Clothing
- Weapons
- Vehicles
- Cards
- Furniture
- Pets
- Buildings
- Equipment
- Decorations

For each category identify:

- Rarity
- Level
- Upgradeability
- Stats
- Cosmetic value
- Set bonuses
- Acquisition method
- Duplicate handling
- Inventory rules
- Equip slots

Create the likely item data structure.

Example:

ItemID  
Name  
Category  
Rarity  
Level  
MaxLevel  
BaseStats  
UpgradeCost  
UnlockRequirement  
AcquisitionSource  
VisualPrefab  
Icon  
Tags

---

# **11. Upgrade Systems**

Explain every upgrade system.

Document:

- Upgrade cost
- Required materials
- Level cap
- Stat growth
- Evolution
- Rarity increase
- Star system
- Merge system
- Duplicate conversion
- Failure chance
- Upgrade timers

Provide example formulas.

Example:

UpgradeCost = BaseCost × Level^1.5

Power = BasePower × RarityMultiplier × LevelMultiplier

---

# **12. Missions & Objective Systems**

Identify all objective structures:

- Main missions
- Side missions
- Daily missions
- Weekly missions
- Career missions
- Event missions
- Achievements
- Milestones
- Tutorial missions

Create a reusable mission architecture.

Example fields:

MissionID  
MissionType  
ObjectiveType  
TargetValue  
ProgressTracking  
Reward  
UnlockRequirement  
StartTime  
EndTime

---

# **13. Events & LiveOps**

Analyze the LiveOps framework deeply.

Document:

- Event types
- Frequency
- Duration
- Entry rules
- Event currencies
- Event shops
- Leaderboards
- Milestones
- Event passes
- Limited content
- Reward structures
- Return schedules

Explain whether events are:

- Content-driven
- Economy-driven
- Competitive
- Collection-driven
- Monetization-driven

Then design a reusable LiveOps framework capable of producing similar events without client updates.

---

# **14. Event Economy**

For each event type identify:

Event Entry  
↓  
Event Gameplay  
↓  
Event Currency  
↓  
Milestone Progress  
↓  
Event Store / Rewards  
↓  
Collection Completion

Explain:

- Currency earn rate
- Event sinks
- Event exclusivity
- Completion requirements
- Free-player feasibility
- Paying-player acceleration
- Event expiration behavior

---

# **15. Monetization Design**

Reverse-engineer all monetization layers.

Document:

### **IAP**

- Currency packs
- Starter packs
- Upgrade packs
- Event packs
- Limited offers
- Bundles
- Subscription
- Pass

### **Ads**

- Rewarded video
- Interstitial
- Offerwall
- Ad-based energy
- Ad-based currency
- Ad-based retry
- Ad-based bonus rewards

### **Monetization Triggers**

Identify when offers appear:

- After failure
- At resource shortage
- After unlocking content
- During events
- On login
- On progression wall

Explain the psychology and product purpose without recommending deceptive or exploitative practices.

---

# **16. Store Architecture**

Reverse-engineer the store.

Document:

- Store tabs
- Product categories
- Rotation
- Timers
- Discounts
- Personalized offers
- Recommended items
- Limited offers
- Bundles
- Free daily items

Create a backend-friendly product configuration.

Example:

ProductID  
ProductType  
Price  
Currency  
Contents  
Discount  
UnlockCondition  
StartTime  
EndTime  
PurchaseLimit  
Segment

---

# **17. Reward Architecture**

Map all reward channels.

Examples:

- Login rewards
- Match rewards
- Level rewards
- Event rewards
- Daily mission rewards
- Pass rewards
- Achievements
- Ads
- Social rewards
- Inbox rewards
- Compensation

Explain how reward pacing supports retention.

---

# **18. Retention Systems**

Identify likely retention hooks.

Cover:

- Daily rewards
- Streaks
- Energy
- Missions
- Events
- Collections
- Pass
- Leaderboards
- Social pressure
- Limited-time offers
- Notifications
- Content unlocks

Break down expected:

D0  
D1  
D3  
D7  
D14  
D30

player motivations.

---

# **19. Social Systems**

Document all social mechanics.

Possible systems:

- Friends
- Follow
- Guilds
- Clubs
- Teams
- PvP
- Leaderboards
- Gifting
- Chat
- Likes
- Visiting
- Sharing
- Spectating

Explain whether social mechanics affect:

- Gameplay
- Economy
- Retention
- Monetization

---

# **20. PvP & Matchmaking**

If applicable, document:

- Real-time vs asynchronous
- Matchmaking inputs
- MMR
- League
- Rank
- Bots
- Player pools
- Match duration
- Entry fees
- Rewards
- Anti-abuse systems

Create a probable matchmaking flow.

---

# **21. AI Systems**

Analyze AI requirements.

Include:

- NPC behavior
- Enemy behavior
- Bot players
- Difficulty adaptation
- Decision-making
- Scripted behavior
- Navigation
- Combat AI
- Simulation

Specify which AI systems can be:

- FSM
- Behavior tree
- Utility AI
- Rule-based

---

# **22. UX / UI Architecture**

Reverse-engineer the complete screen hierarchy.

Create a screen map.

Example:

Splash  
↓  
Login  
↓  
Tutorial  
↓  
Home  
├── Play  
├── Store  
├── Events  
├── Collection  
├── Profile  
└── Settings

For every screen document:

- Purpose
- Information hierarchy
- Main CTA
- Secondary CTA
- Navigation
- Currency display
- Popups
- State changes

---

# **23. FTUE / Tutorial**

Reconstruct the probable first-time user experience.

Document minute-by-minute:

0–1 minute  
1–3 minutes  
3–5 minutes  
5–10 minutes  
10–20 minutes

Identify:

- First interaction
- First reward
- First upgrade
- First unlock
- First monetization exposure
- First event exposure
- First social exposure

Design a comparable FTUE flow.

---

# **24. Content Inventory**

Estimate the amount of content required.

Create a table like:

|**Content Type**|**Launch Minimum**|**Comparable Scope**|**Long-Term Target**|
|---|---|---|---|
|Characters||||
|Outfits||||
|Levels||||
|Environments||||
|Missions||||
|Events||||
|Items||||

Explain which content is manually authored versus systemically generated.

---

# **25. Content Production Pipeline**

Explain how the development team should produce scalable content.

Examples:

Character  
Concept  
↓  
Model  
↓  
Rig  
↓  
Animation  
↓  
Materials  
↓  
Prefab  
↓  
Config  
↓  
Game

Level  
Blockout  
↓  
Gameplay Pass  
↓  
Art Pass  
↓  
Lighting  
↓  
Optimization  
↓  
QA  
↓  
Release

Identify reusable components that reduce production cost.

---

# **26. Art Scope**

Analyze:

- 2D/3D
- Rendering style
- Character complexity
- Environment complexity
- Animation complexity
- VFX complexity
- UI art complexity
- Asset reuse
- Camera presentation

Estimate production cost categories:

Low  
Medium  
High  
Very High

Do not copy exact art assets. Define an original visual production scope with comparable fidelity.

---

# **27. Animation Requirements**

Create an animation inventory.

Examples:

Idle  
Walk  
Run  
Win  
Lose  
Interact  
Attack  
Hit  
Equip  
Celebrate

Estimate:

- Number of animations
- Character-specific vs shared
- Procedural animations
- UI animation
- Camera animation

---

# **28. Audio Requirements**

Document:

- Music states
- Gameplay SFX
- UI SFX
- Character audio
- Ambient audio
- Reward sounds
- Event music
- Voiceover

Create an estimated audio asset list.

---

# **29. Technical Architecture**

Suggest a high-level architecture suitable for implementing the game.

Cover:

Client  
Backend  
Database  
Analytics  
Remote Config  
LiveOps  
Authentication  
Inventory  
Economy  
Leaderboard  
Matchmaking  
Cloud Save  
Payments  
Ads  
Push Notifications

Create a system diagram.

Example:

Mobile Client  
↓  
API Layer  
↓  
Game Backend  
├── Player Service  
├── Economy Service  
├── Inventory  
├── Matchmaking  
├── Events  
├── Leaderboards  
└── LiveOps Config

---

# **30. Client Feature Architecture**

Suggest major client modules.

Example:

Core  
Gameplay  
Player  
Inventory  
Economy  
Store  
Events  
Missions  
Social  
UI  
Audio  
Analytics  
Networking  
RemoteConfig

Describe responsibilities of each module.

---

# **31. Backend Data Models**

Define likely backend entities.

Include example schemas for:

Player  
Inventory  
CurrencyWallet  
Item  
Mission  
Event  
StoreOffer  
LeaderboardEntry  
Match  
Progression  
Reward

Keep schemas engine/backend agnostic.

---

# **32. Remote Configuration**

Identify everything that should be remotely configurable:

- Economy values
- Rewards
- Store products
- Events
- Mission definitions
- Drop rates
- Unlock levels
- Difficulty
- Ads
- Energy
- Offers
- Content schedules

Explain which features should not require a client update.

---

# **33. Analytics**

Create a tracking plan.

Include events such as:

session_start  
tutorial_step  
level_start  
level_complete  
level_fail  
currency_earned  
currency_spent  
item_unlocked  
item_upgraded  
iap_started  
iap_complete  
ad_watched  
event_entered  
mission_complete  
store_opened

For each important event include useful parameters.

---

# **34. KPIs**

List relevant product KPIs.

Examples:

Retention  
D1  
D7  
D30  
Sessions/User  
Session Length  
ARPDAU  
ARPPU  
Conversion Rate  
LTV  
Ad ARPDAU  
Progression Rate  
Economy Balance  
Event Participation

Explain what healthy behavior would look like for this type of game without inventing exact industry benchmarks unless reliable data is available.

---

# **35. Notifications**

Reverse-engineer probable notification strategy.

Examples:

Energy full  
Event ending  
Reward ready  
Daily reset  
Friend challenge  
New content  
Pass ending

Create a notification matrix.

---

# **36. Edge Cases & Failure States**

Document likely edge cases:

- Disconnect
- App backgrounding
- Purchase interruption
- Duplicate rewards
- Failed transactions
- Inventory full
- Event expiry
- Match abandonment
- Save conflicts
- Time manipulation
- Cheat attempts

Explain required handling.

---

# **37. Anti-Cheat / Abuse Prevention**

If relevant, include:

- Server-authoritative values
- Economy validation
- Match validation
- Purchase validation
- Replay validation
- Speed hacking prevention
- Clock manipulation
- Save tampering
- Reward duplication
- Bot abuse

---

# **38. Performance Requirements**

Estimate:

- Target FPS
- Device range
- Memory budget
- Loading expectations
- Draw-call considerations
- Texture strategy
- Asset bundles
- Streaming
- Download size
- Battery concerns

---

# **39. Development Scope**

Split development into:

### **MVP**

The smallest version that proves the core game.

### **Soft Launch**

Enough systems for retention/economy testing.

### **Global Launch**

Comparable commercial product.

### **Post-Launch**

LiveOps and expansion.

For each phase clearly state included and excluded features.

---

# **40. Development Roadmap**

Provide a recommended sequence such as:

Prototype  
↓  
Vertical Slice  
↓  
Core Gameplay  
↓  
Meta  
↓  
Economy  
↓  
Content Production  
↓  
Backend  
↓  
LiveOps  
↓  
Soft Launch  
↓  
Optimization  
↓  
Global Launch

Explain dependencies.

---

# **41. Team Requirements**

Estimate team roles needed.

Examples:

Producer  
Game Designer  
Economy Designer  
Unity/Unreal Developers  
Backend Developer  
UI/UX Designer  
2D Artist  
3D Artist  
Animator  
VFX Artist  
QA  
Data Analyst

Provide:

- Lean team
- Recommended team
- Large production team

Do not invent salary costs unless specifically requested.

---

# **42. Effort Estimation**

For every major feature assign:

Small  
Medium  
Large  
Very Large

Also classify:

Technical Risk  
Content Risk  
Design Risk  
Backend Dependency

Produce a feature scope matrix.

---

# **43. Feature Dependency Matrix**

Show dependencies such as:

Inventory → Store  
Inventory → Equipment  
Economy → Upgrades  
Remote Config → Events  
Backend → Leaderboards  
Analytics → Soft Launch

Identify critical-path systems.

---

# **44. Replica Difficulty Analysis**

Identify the hardest parts to reproduce.

Separate:

### **Easy to Reproduce**

Commodity systems.

### **Moderately Difficult**

Systems requiring substantial tuning.

### **Difficult**

High-content/high-tech systems.

### **Very Difficult**

Network effects, huge content libraries, sophisticated multiplayer, etc.

Explain where development risk actually resides.

---

# **45. Minimum Content Needed to Feel Complete**

Define the smallest believable launch inventory.

Example:

5 environments  
50 levels  
20 characters  
100 cosmetic items  
3 event formats  
1 pass  
20 daily missions

Use game-specific estimates based on the researched title.

---

# **46. Proposed Original Version**

After analyzing the reference game, propose how to build an **original game inspired by its product structure without directly cloning its copyrighted expression**.

Preserve valuable patterns such as:

- Core loop
- Progression architecture
- Economy philosophy
- LiveOps architecture
- Content cadence

But identify areas that should be differentiated:

- Theme
- Characters
- Art
- Story
- UI identity
- Level layouts
- Content naming
- Narrative
- Audio
- Branding

---

# **47. Unknowns & Research Confidence**

Every major conclusion must be tagged where appropriate as:

**Confirmed** — directly visible or documented.

**Strongly Inferred** — multiple pieces of evidence support it.

**Estimated** — reasonable professional estimate.

**Proposed** — design suggested to fill missing information.

Never pretend that hidden backend values or proprietary systems are known.

Create a final section called:

## **Unknowns Requiring Hands-On Gameplay**

List everything that cannot reliably be determined from public research.

---

# **48. Final Developer Blueprint**

Finish with a concise build blueprint containing:

### **Game Pillars**

### **Core Loop**

### **Major Systems**

### **Economy**

### **Progression**

### **Content**

### **LiveOps**

### **Monetization**

### **Backend**

### **MVP Scope**

### **Launch Scope**

### **Biggest Risks**

### **Development Priority**

Then produce a final table:

|**Priority**|**System**|**Why It Matters**|**Dependency**|**Scope**|
|---|---|---|---|---|

Rank systems from P0 to P3.

P0 = mandatory for prototype/core experience  
P1 = mandatory for MVP  
P2 = required for commercial launch  
P3 = post-launch enhancement

---

# **Research Requirements**

Do not rely solely on the store description.

Search broadly for:

- Official gameplay videos
- YouTube gameplay
- App Store / Play Store screenshots
- Game trailers
- Reviews
- Community discussions
- Reddit
- Wikis
- Strategy guides
- Social media
- Update notes
- Patch notes
- Developer website
- Event screenshots
- Shop screenshots
- Progression screenshots

Prioritize actual gameplay evidence over marketing descriptions.

When different sources conflict, state the conflict.

Use screenshots and videos to infer systems where possible.

Do not fabricate exact values.

---

# **Required Output Style**

The final result should read like an internal professional production document, not a game review.

It should be sufficiently detailed that:

- A Game Designer can recreate the gameplay rules.
- An Economy Designer can build a first-pass economy.
- A UX Designer can construct the screen flow.
- A Client Developer can identify required modules.
- A Backend Developer can identify services and data models.
- A Producer can estimate scope.
- An Artist can estimate required content.
- QA can understand major game states.
- A Product Manager can understand retention and monetization.
- A LiveOps Designer can build recurring events.

Use:

- Tables
- Flow diagrams
- Formulas
- Example configs
- State diagrams
- Data models
- Feature matrices

Avoid vague descriptions such as “the game has many upgrades.”

Instead explain exactly how the observed or inferred system works and what would need to be implemented.

My game link is:

[PASTE STORE LINK HERE]