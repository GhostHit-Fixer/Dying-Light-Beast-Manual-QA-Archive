# [JIRA BUG REPORT] unique item duplication constraint violation

## Environment
* **Platform:** PC / Steam (Offline Mode - Air-Gapped Workstation)
* **OS:** Windows 10 Enterprise 64-bit ,Build 19044.1566 (21H2)
* **CPU:** AMD FX(tm)-6300 Six-Core Processor  (6 CPUs), ~3.5GHz
* **GPU:** NVIDIA GTX 1050  2GB
* **RAM:** 8GB DDR3 RAM 
* **GPU Driver Version:** 31.0.15.3118
* **Game Version:** v1.6.0 
* **Graphics Profile:** Min-Spec Custom (TAA Enabled, Texture Quality: Low)

## Details
* **Title:** [Inventory/Database] Unique item constraint violation allows multiple "Mulder's sunflower seed" collection during consecutive NG+ cycles.
* **Severity:** Medium (Database / Inventory Logic Error)
* **Reproducibility:** 100% (Verified up to 4 duplicate items in inventory during NG6+ cycle)

## Preconditions
* Player must be on a New Game Plus (NG+) cycle (NG6+  verified).
* Player must already possess at least 1 or more "Mulder's sunflower seed" items in their inventory from previous playthroughs.

## Steps to Reproduce
1. Load the active NG+ save game and open the Inventory menu.
2. Verify that existing "Mulder's sunflower seed" items occupy separate individual slots (No stacking logic applied).
3. Travel to the Industrial Sector in Castor Woods.
4. Locate the specific factory building containing the Volatile Hive interior.
5. Climb up to the top of the highest factory chimney directly adjacent to this Volatile Hive building.
6. Observe the Easter Egg spawn point on the chimney rim.
7. Execute the `[F - pick up]` interaction on the spawned item.

## Actual Result
The game displays a fresh `[F - pick up]` interaction prompt for the "Mulder's sunflower seed" item, completely ignoring the unique item database constraint ("You can carry only one"). The character successfully triggers the pickup animation and audio. The item is added to the inventory as a 4th individual slot item.

## Expected Result
The item spawn point should check the player's persistent inventory flag. If the player already owns "Mulder's sunflower seed", the interaction prompt should be disabled, or the item should be un-interactable to prevent duplication.

## Attachments
* `BUG_01_item_stacking_NG6+.mp4` (1080p / 30 FPS video proof)

---
[LinkedIn Profile](https://www.linkedin.com/in/balazs-manual-qa-specialist/)
[GitHub Profile](https://github.com/GhostHit-Fixer/)

 The fix is on the house. :)

- GhostHit_Fixer™

