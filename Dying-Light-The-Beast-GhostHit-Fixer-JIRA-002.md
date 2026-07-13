# [JIRA BOX #2 - CORRECTED - STARTER ARMOR VALUE INFLATION LEAK]

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
* **Title:** [Database/Inventory] [Armor Attribute Leak] NG+ initialization sequence duplicates un-tradeable starter gear and leaks elite Vanguard defense modifiers onto baseline asset IDs.
* **Severity:** Major
* **Reproducibility:** 100% / Continuous loop verified upon NG6+ stash tutorial execution.

## Preconditions
1. An active endgame save file transitioned into New Game Plus (NG6+ template).
2. "Vanguard Armor" set unlocked and available in the global profile data.

## Steps to Reproduce
1. Advance through the prologue until completing the first Chimera (Reaper) kill.
2. Enter the Monastery safe zone and interact with NPC Olivia to trigger her dialogue script.
3. Accept Olivia's objective prompt regarding the global Stash insertion.
4. Open the Stash interface array, then move both starter clothing items simultaneously into the active player Inventory.

## Actual Result
1. **Asset Multiplication:** Olivia's script bypasses existing player matrix data, forcing a repetitive, un-tradeable secondary batch of starter equipment (Hooded Top, Regular Jeans, Hiking Shoes) into individual inventory array slots. Both duplicated assets are fully functional: they can be equipped simultaneously, moved freely between the Inventory and Stash, and persist across storage updates without triggering an invalid asset clean-up routine.
2. **Attribute Leak:** The database incorrectly assigns defense coefficients. The lowest-tier baseline Starter Clothes are granted maximum-tier Vanguard Armor defense statistics, creating a 1:1 value equalization. Baseline asset values are inflated due to bad ID tracking.

## Expected Result
1. NG+ initialization scripts must parse existing storage indices to prevent item cloning loops.
2. Baseline starter clothes must retain their designated minimum defense values (1-2 points) independently, without absorbing elite Vanguard armor protection variables.

## Attachments
* Screenshots: `BUG_02_inventory_inflation_01.png` through `BUG_02_inventory_inflation_06.png` (6-part cumulative visual evidence)

---
[LinkedIn Profile](https://www.linkedin.com/in/balazs-manual-qa-specialist/)
[GitHub Profile](https://github.com/GhostHit-Fixer/)

 The fix is on the house. :)

- GhostHit_Fixer™

