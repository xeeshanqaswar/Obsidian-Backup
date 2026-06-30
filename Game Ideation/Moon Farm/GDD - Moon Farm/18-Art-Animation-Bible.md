
## 🔹 Art Direction Overview

- **Tone:** Cozy, stylized, whimsical, magical realism.
- **Perspective:** 3D stylized assets with a **slightly tilted top-down camera** (~30° tilt).
- **Style Inspiration:** Soft colors, round shapes, painterly textures, low visual noise for readability.
- **Target Platforms:** Switch and Mobile (performance-optimized) → low poly but rich in color & lighting.
- **Primary Goals:**
  - Avoid realism; focus on charm and warmth.
  - Consistent, easily expandable pipeline for new content.
  - Visual storytelling: Seasons, festivals, and NPC personalities are distinct through design.

## 🔹 Core Art Pillars

| **Pillar**        | **Execution Notes** |
| ----------------- | ------------------- |
| **Simplicity**    | Low-poly models, minimal edge loops, hand-painted textures. |
| **Color Theory**  | Seasonal palettes with complementary accent colors. |
| **Readability**   | Characters and objects "pop" against environments; heavy outlines avoided. |
| **Softness**      | Rounded edges, minimal harsh lines or photoreal shading. |
| **Cohesive World** | Props, UI, and NPCs share design language (same proportions, materials). |

## 🔹 Art Style Specs

| **Element**      | **Specification** |
| ---------------- | ----------------- |
| **Character Scale** | ~2.5–3 heads tall, stylized proportions. |
| **World Scale**  | ~2m per tile equivalent (character slightly chibi for cuteness). |
| **Poly Count Targets** | Characters: 3k–5k; Buildings: 2k–5k; Small props: <1k. |
| **Texture Style** | Hand-painted, stylized PBR (base color + subtle roughness). |
| **Shader Style** | Simple toon shader with soft shadow gradients; baked AO. |
| **Lighting**     | Warm directional sunlight, soft global illumination, bloom on magical items. |
| **VFX Style**    | Minimalistic particles; soft glows, sparkles, and dust motes. |

## 🔹 Character Design Bible

| **Aspect**        | **Rules** |
| ----------------- | --------- |
| **Silhouette Design** | Each character easily recognizable from silhouette. |
| **Color Coding**  | NPC roles indicated subtly (e.g., fisherman wears blues, blacksmith wears browns/grays). |
| **Face Design**   | Minimal facial detail: dot eyes, small mouths, simple noses; expressive animations instead. |
| **Clothing Style** | Medieval-cottagecore meets fantasy; functional farm outfits with whimsical accents. |
| **Seasonal Outfits** | NPCs swap accessories (scarves, hats, jackets) based on weather. |
| **Accessory Variety** | Distinct hats, satchels, jewelry to make NPCs memorable. |
| **Legendary Characters** | Ancient symbols, glowing runes, flowing capes for magical NPCs. |

#### NPC Archetype Examples

- **Village Elder:** Long robes, curved staff, soft warm palette (sage, cream).
- **Merchant:** Bright reds and gold accents; carries large pack.
- **Fisherman:** Worn overalls, wide-brimmed hat, rope accessories.
- **Children:** Chubbier proportions, pastel clothing.
- **Adventurer NPCs:** Leather armor with stylized buckles, belts, glowing relics.

## 🔹 Creature & Animal Design

- **Pets:** Simplified and round, with oversized eyes for cuteness.
- **Farm Animals:** Exaggerated proportions (small legs, round bodies).
- **Legendary Creatures:** Soft glowing textures, semi-transparent VFX.
- **Wildlife:** Silhouettes for each biome (foxes in forests, snow owls in winter, glowing bugs at night).

| **Animal Type**      | **Design Notes** |
| -------------------- | ---------------- |
| **Chickens**         | Plump, round feathers, tiny wings. |
| **Cows**             | Bell collars, soft spots, pastel tones. |
| **Goats**            | Curved horns, mischievous eyes. |
| **Rabbits**          | Floppy ears, seasonal color variations. |
| **Foxes**            | Sleek, glowing eyes in moonlight. |
| **Legendary Pet**    | Dragon or Phoenix variant; stylized runes. |

## 🔹 Environment Design

| **Zone**            | **Palette & Design** |
| ------------------- | -------------------- |
| **Village Center**  | Warm pastels, cobblestone, timber-frame houses. |
| **Farmstead**       | Lush greens, soft dirt paths, warm wood barns. |
| **Meadows**         | Long grass, wildflowers, butterflies, glowing mushrooms at night. |
| **Forests**         | Stylized trees with broad leaves, soft ambient fog. |
| **Mountains**       | Snow-tipped peaks, jagged rocks, faint auroras. |
| **Ocean/Beaches**   | Soft gradient ocean shader, stylized foam, seashell scatter. |
| **Ruins & Shrines** | Mossy stone, glowing runes, floating particles. |

## 🔹 Seasonal Color Palette

| **Season** | **Palette Style** |
| ---------- | ----------------- |
| **Spring** | Pastels: mint green, baby blue, pink blossoms. |
| **Summer** | Saturated: bright yellows, vibrant greens, deep ocean blues. |
| **Fall**   | Warm: amber, orange, burgundy, muted teal. |
| **Winter** | Cool: icy blues, lavender shadows, snow whites. |

## 🔹 UI & HUD Design

- **UI Theme:** Wooden panels with hand-drawn borders and soft parchment textures.
- **Font:** Serif for titles, rounded sans-serif for text readability.
- **Color Code:** Soft gold for highlights, cream for panels, muted blue for inactive states.
- **Inventory Grid:** Stylized slots with soft shadows.
- **Dialogue Boxes:** Scroll-inspired box with soft portrait cutouts for NPCs.
- **HUD:** Minimal; hearts for stamina/health, coin bag icon, and time/weather indicators.

## 🔹 Animation Guidelines

| **Category**      | **Notes** |
| ----------------- | --------- |
| **Character Idle** | Subtle breathing, eye blinks, slight sways. |
| **Movement**      | Exaggerated head bobbing for chibi charm. |
| **Tool Use**      | Each tool has a unique silhouette motion (scythe overhead, hoe side swing). |
| **Farming Actions** | Short loops (~0.8s), snappy transitions. |
| **Animal Animations** | Grazing, tail flicking, lying down; playful idle loops. |
| **NPC Interactions** | Unique gestures per archetype (fisherman adjusts hat, elder strokes beard). |
| **Festival Animations** | Firework sequences, dancing loops, lantern releases. |
| **Cinematic Moments** | Hand-keyed gestures, smooth camera pans; use particle VFX. |

## 🔹 VFX Style Guide

- **Farming:** Small dirt puffs, soft water splash.
- **Magic:** Glowing orbs, sparkles with fading trails.
- **Weather:** Layered particles for snow/rain; gentle motion.
- **Dungeon Hazards:** Smoke puffs, glowing trap runes, dust particles.
- **Festival Effects:** Fireworks, floating lanterns, glowing confetti.

## 🔹 Asset Production Pipeline

1. **Concept Art Stage:**
    - Sketch → Colored illustration → Orthographic views for modeling.
2. **Modeling:**
    - Blockout (low-poly, silhouette check) → High-poly (if needed for bake) → Final low-poly model.
3. **Texturing:**
    - Hand-paint base color → Bake AO → Subtle stylized roughness map.
4. **Rigging:**
    - Simple skeleton rigs for animals, humans; IK for tools/weapons.
5. **Animation:**
    - Core movement cycles first, then NPC-specific gestures.
6. **Integration:**
    - Exported FBX + prefab setup in Unity (Animator controllers, LOD setup).
7. **Optimization:**
    - Combine props per scene, bake lighting for mobile, texture atlases for similar items.

---
**Back to:** [[Moon Farming GDD]]
