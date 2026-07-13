# [JIRA BOX #13 - PROJECT_2_v1.6.0 - THE BAIT AND THE BEAST ENTITY REGRESSION]

## Environment
* **Platform:** PC / Standalone (Offline Mode - Air-Gapped Workstation)
* **OS:** Windows 10 Enterprise 64-bit ,Build 19044.1566 (21H2)
* **CPU:** AMD FX(tm)-6300 Six-Core Processor  (6 CPUs), ~3.5GHz
* **GPU:** NVIDIA GTX 1050  2GB
* **RAM:** 8GB DDR3 RAM 
* **GPU Driver Version:** 31.0.15.3118
* **Game Version:** v1.6.0 
* **Graphics Profile:** Min-Spec Custom (TAA Enabled, Texture Quality: Low)

## Details
* **Title:** [Quest-Regression] [Entity-Shedding] Main Quest "The Bait and the Beast" script phase fails to spawn designated Scientist Corpse asset in E&F Factory Basement, leaving an invisible interactive Trigger Box.
* **Severity:** Medium
* **Reproducibility:** 100% / Persistent across multiple cold starts after entering specific quest phase.

## Preconditions
1. Progression reached Main Quest: "The Bait and the Beast".
2. Access to E&F Factory Basement area unlocked and cleared of active hostile entities.
3. Character active on Nightmare Difficulty profile (influences loot table feedback).

## Steps to Reproduce
1. Load save game and navigate into the E&F Factory Basement sub-zone.
2. Turn the corner approaching the blood decal coordinates on the floor where the static Scientist Corpse asset is designated to spawn.
3. Approach the blood decal directly and observe the lack of any 3D character mesh/texture.
4. Position the crosshair directly over the center of the blood decal on the floor to trigger the interaction HUD.
5. Press and hold the interaction key `[F]` to execute the "Search" routine until the progress ring fills completely.

## Actual Result
The 3D character mesh and texture for the dead scientist asset fail to load entirely, leaving only the static blood splatter decal visible on the ground. However, the logic layer remains fully active: approaching the coordinates triggers the `[F - Search]` UI prompt on the floor (Z-axis is correct). Executing the interaction completes the looting circle sequence and correctly returns a "Nothing" database output (standard behavior for Nightmare difficulty empty loot tables), after which the interaction trigger cleanly terminates and disappears from the HUD.

## Expected Result
The script phase for "The Bait and the Beast" must correctly call and render the designated 3D Scientist Corpse asset on top of the blood decal coordinates. The visual asset layer must match the active underlying interactive Trigger Box to maintain visual-to-logic synchronization.

## Regression Notes
* **Prior Quest Phase:** Fully Functional. (The 3D asset renders correctly during earlier sub-zone exploration before this specific quest line updates).
* **Current Quest Phase:** 100% Bugged. (The asset is completely deleted/shedded from the render queue once "The Bait and the Beast" phase becomes active).

## Attachments
* Video Proof: `BUG_13_invisible_corpse_interaction_1080p.mp4` (13-second MPC-HC frame-by-frame verified approach and loot cycle capture)

---

[LinkedIn Profile](https://www.linkedin.com/in/balazs-manual-qa-specialist/)



[GitHub Profile](https://github.com/GhostHit-Fixer/)



The fix is on the house. :)



- GhostHit_Fixer™

