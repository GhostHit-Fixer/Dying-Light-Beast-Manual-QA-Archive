# [JIRA BOX #8 - PROJECT_2_v1.6.0 - VENDOR UI PERFORMANCE AUDIT]

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
* **Title:** [UI/X] [Inventory/Database] Input latency and optimization failure in vendor menu elongating radial progress bar on craftpart purchases.
* **Severity:** Low / Performance
* **Reproducibility:** 100% (Verified via A-B-A testing method)

## Preconditions
1. Access to any active open-world or safezone Vendor NPC unlocked.
2. Character inventory must have available storage slots and sufficient currency (Old World Money).

## Steps to Reproduce
1. Load the offline manual save and interact with the Vendor to open the trade screen.
2. Purchase single weapon assets sequentially (e.g., Hockey Stick, Kopis, Reinforced Stick, Simple Machete) by holding the interaction key/mouse button. [Phase A1]
3. Scroll down and purchase craftpart resources, both in bulk stacks and single units (e.g., Stack of 9 Alcohol, Stack of 3 Battery, 3x single Blades). [Phase B]
4. Scroll back up and purchase single weapons again (e.g., Fire Station Great Axe, Demolisher) to cross-verify performance consistency. [Phase A2]

## Actual Result
A severe 1-second input registration delay occurs exclusively when purchasing craftpart resources. While weapon assets require exactly ~2 seconds of holding down the key to fill the radial progress bar, craftpart assets require ~3 seconds. This input latency remains uniform regardless of the resource rarity (Common/Rare) or stack size, proving a hard script-loop calculation delay during inventory data array updates. Frametime telemetry shows identical minuscule spikes in both cases, ruling out hardware bottlenecks.

## Expected Result
The radial progress bar duration should remain completely uniform across all asset categories inside the vendor menu. Holding the interaction key for a single or stack purchase should take exactly ~2 seconds, regardless of whether the target item is a weapon or a craftpart resource matrix.

## Attachments
* Video Proof: `BUG_08_vendor_ui_optimization_1080p.mp4` (Bandicam 1080p control capture)

---

[LinkedIn Profile](https://www.linkedin.com/in/balazs-manual-qa-specialist/)



[GitHub Profile](https://github.com/GhostHit-Fixer/)



The fix is on the house. :)



- GhostHit_Fixer™
