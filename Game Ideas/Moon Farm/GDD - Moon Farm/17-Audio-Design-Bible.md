
## 🔹 Audio Design Philosophy

- **Calm & Emotional Atmosphere:** Music reinforces the cozy, magical vibe of the game.
- **Dynamic Layers:** Music evolves with time of day, season, and player activity.
- **Player-Centric Feedback:** Every action (watering, swinging tools, gifting NPCs) has audio cues.
- **Memory-Driven Themes:** Seasonal motifs and NPC leitmotifs create emotional attachment.
- **Immersive Ambience:** Natural sounds react to weather, location, and time.

## 🔹 Audio Style Guide

| **Category**        | **Style Notes** |
| ------------------- | --------------- |
| **Music**           | Orchestral/folk hybrid with acoustic instruments (guitar, violin, flute) and soft synth pads for magic areas. |
| **Ambient Sound**   | Layered field recordings (wind, water, insects) with subtle reverb in magical biomes. |
| **SFX**             | Soft, tactile, and playful; emphasis on comfort (no harsh or metallic sounds unless intentional for dungeons). |
| **UI/Feedback**     | Bell tones, soft clicks, parchment rustles for menus. |
| **Combat/Action**   | Light but impactful sound design; stylized "magical" weapon sounds. |

## 🔹 Music Structure

| **Category**        | **Description & Purpose** |
| ------------------- | ------------------------- |
| **Seasonal Themes** | 4 main seasonal soundtracks (Spring, Summer, Fall, Winter) with day/night variations. |
| **Festival Themes** | Unique tracks for each festival; energetic and celebratory. |
| **Village Theme**   | Warm, welcoming motif with acoustic guitar and flute. |
| **Farm Theme (Day)** | Peaceful, slow-paced track encouraging relaxation. |
| **Farm Theme (Night)** | Soft piano, crickets, wind ambiance for calm nighttime. |
| **Dungeon Themes**  | Layered, mysterious melodies with soft percussion. |
| **Boss Themes**     | Epic but still melodic; no harsh tones to fit cozy vibe. |
| **Shrine Music**    | Ethereal vocals, soft synth pads, distant chimes. |
| **Endgame/Ruins**   | Mystical strings, low piano, slow percussion. |
| **Character Motifs** | Light leitmotifs for key NPCs (Elder, Rival, Chef, Merchant). |

## 🔹 Seasonal Music Variations

| **Season** | **Day Theme Notes**             | **Night Theme Notes** |
| ---------- | ------------------------------- | --------------------- |
| **Spring** | Bright acoustic guitar, flute melodies, bird songs. | Lullaby-style piano, frogs, crickets. |
| **Summer** | Light percussion, strings, cicadas. | Soft wind chimes, ocean waves if near beach. |
| **Fall**   | Fiddle, slow tempo, rustling leaves ambiance. | Hollow flute, owls, wind gusts. |
| **Winter** | Bells, soft pads, snow crunch ambience. | Minimalist piano, muffled wind, snowy reverb. |

## 🔹 Ambient Sound Zones

| **Zone**              | **Core Ambience Layers** |
| --------------------- | ------------------------ |
| **Village Center**    | Faint chatter, chickens, blacksmith hammer, fountain. |
| **Farmstead**         | Wind, rustling crops, animal noises (context-based). |
| **Meadowlands**       | Birds, bees, flowing stream. |
| **Whisper Cavern**    | Dripping water, distant echoes, bat screeches. |
| **Frostpeak Highlands** | Wind gusts, crunching snow, distant wolves. |
| **Sunset Shores**     | Waves, seagulls, soft wind. |
| **Moonlit Ruins**     | Low hum, faint magical whispers, reverb-heavy chimes. |
| **Shrine Areas**      | Gentle choir pad, bell tones, sparkling wind chimes. |

## 🔹 SFX Library Needs

| **Category**           | **Example Sounds** |
| ---------------------- | ------------------ |
| **Tools & Farming**    | Hoe tilling soil, watering can pour, seed drop, sickle swish. |
| **Harvesting**         | Soft "pop" for fruit pick, bag rustle for crops. |
| **Animal Sounds**      | Chickens clucking, cows mooing, goats bleating, soft variations per animal. |
| **Crafting/Artisan**   | Wood hammering, bubbling liquids, machine chimes. |
| **Fishing**            | Rod cast swoosh, water plop, reel tension sound. |
| **Combat**             | Weapon swishes, light hit impacts, enemy squeaks/snaps. |
| **Magic Abilities**    | Soft sparkle tones, rising chimes, wind gust effects. |
| **Dungeon Interaction** | Stone grinding, gate creaks, mystical rune activation. |
| **Pet Sounds**         | Purring, barks, whines, bird chirps, unique legendary pet calls. |
| **Weather SFX**        | Rain patter, distant thunder, wind through trees. |

## 🔹 UI Sound Design

| **Interaction**             | **Sound Type** |
| --------------------------- | -------------- |
| Button Click                | Soft "wood tap" with light bell tone. |
| Inventory Open/Close        | Leather creak, paper rustle. |
| Quest Complete              | Rising harp glissando. |
| New Recipe Learned          | Light bell "ding" + parchment flutter. |
| Level Up                    | Sparkle chime crescendo. |
| Achievement Popup           | Short piano arpeggio. |
| Shop Purchase               | Cash register bell or coin drop. |

## 🔹 Dynamic Audio Systems

| **System**        | **Implementation** |
| ----------------- | ------------------ |
| **Time of Day Music** | Crossfade between day/night tracks based on in-game clock. |
| **Weather Layers** | Overlay rain/wind/ambient SFX dynamically. |
| **Activity Layers** | Farming, fishing, and mining subtly alter soundtrack instrumentation. |
| **Combat Transitions** | Combat music fades in/out seamlessly when enemy engaged. |
| **Shrine Transitions** | Entering a shrine smoothly introduces mystical pads and reverb. |

## 🔹 Implementation Notes for Devs

- Audio middleware: **FMOD or Wwise** recommended for Switch/Mobile optimization.
- Dynamic mixing: Assign priorities (dialog > SFX > music > ambient).
- Memory optimization: Seasonal themes stream from disk; UI sounds cached in memory.
- Environmental reverb zones: Caverns and ruins need heavier reverb filters.
- Mobile optimization: Limit concurrent sounds, prioritize critical SFX.

---
**Back to:** [[Moon Farming GDD]]
