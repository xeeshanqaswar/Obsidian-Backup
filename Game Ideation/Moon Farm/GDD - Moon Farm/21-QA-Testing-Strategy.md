
## 🔹 QA Philosophy

- **Quality = Core Value:** The game should feel polished, cozy, and stable at launch.
- **Playability First:** Prioritize smooth gameplay experience over raw feature count.
- **Platform-Specific Testing:** Mobile, Switch, and PC optimizations verified separately.
- **Continuous Testing:** Testing starts in **early development** and continues post-launch.

## 🔹 QA Goals

| **Goal**           | **Notes** |
| ------------------ | --------- |
| **Bug-Free Core Systems** | Farming, crafting, NPC interactions must be rock-solid. |
| **Performance Stability** | Maintain **60 FPS on Switch and high-end mobile**; adaptive frame cap for low-end devices. |
| **Save System Reliability** | Test every save/load edge case extensively. |
| **Cross-Platform UX** | Controls, UI scaling, and accessibility verified for each platform. |
| **Content Consistency** | Ensure all items, recipes, and NPC dialogue function as designed. |

## 🔹 QA Milestones

| **Stage**         | **Testing Focus** |
| ----------------- | ---------------- |
| **Prototype Stage** | Core mechanics sanity check, crash detection. |
| **Vertical Slice** | Test farming, mining, and NPC systems end-to-end. |
| **Alpha**         | Full map navigation, item economy checks, performance profiling. |
| **Closed Beta**   | External testers focus on UX, difficulty, and balance. |
| **Pre-Launch (Gold)** | Certification testing for Switch, App Store, and Steam. |
| **Post-Launch**   | Bug patch cadence every 2 weeks initially. |

## 🔹 QA Roles

| **Role**              | **Responsibilities** |
| --------------------- | -------------------- |
| **Lead QA**           | Coordinates testing schedule, verifies bug triage. |
| **Platform QA**       | Switch certification, mobile store compliance. |
| **Gameplay QA**       | System integration, balancing, soft lock prevention. |
| **UX QA**             | Accessibility, controls, UI responsiveness. |
| **Localization QA**   | Text proofing, cultural checks. |
| **Community Testers** | Invite fans to early beta for real-world feedback. |

## 🔹 Bug Tracking Workflow

- **Tool:** Jira, Trello, or GitHub Issues for bug triage.
- **Priority Levels:**
  1. P0: Crash/blocker
  2. P1: Gameplay-breaking
  3. P2: UI/UX issues
  4. P3: Minor cosmetic bugs
- **Workflow:**
  1. Bug logged with screenshots, repro steps.
  2. Assigned to dev.
  3. Fixed, verified by QA, marked resolved.

## 🔹 Performance Testing

| **Platform**         | **Key Focus Areas** |
| -------------------- | ------------------- |
| **Nintendo Switch**  | Handheld vs docked resolution, memory limits. |
| **Mobile**           | Device range testing, adaptive graphics. |
| **PC**               | Low-spec support, controller mapping. |

## 🔹 Automated Testing

- Basic **unit testing** for farming logic, inventory, save/load.
- **Scene load testing** to ensure memory safety.
- Optional: Automated **input scripts** for stress-testing UI.

---
**Back to:** [[Moon Farming GDD]]
