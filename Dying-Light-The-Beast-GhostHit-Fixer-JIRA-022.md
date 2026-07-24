# [BUG_22_JIRA_REPORT - INTERACTION_UIX_OCCLUSION_GEOMETRY_INTERSECT]

## Environment
* **Platform:** PC / Standalone (Offline Mode - Air-Gapped Workstation)
* **OS:** Windows 10 Enterprise 64-bit, Build 19044.1566 (21H2)
* **CPU:** AMD FX(tm)-6300 Six-Core Processor (6 CPUs), ~3.5GHz
* **GPU:** NVIDIA GTX 1050 2GB
* **RAM:** 8GB DDR3 RAM 
* **GPU Driver Version:** 31.0.15.3118
* **Game Version:** v1.6.0 
* **Graphics Profile:** Min-Spec Custom (TAA Enabled, Texture Quality: Low)

## Details
* **Title:** [UI/X] [Physics] Endgame interactive weapon asset looting failure caused by asset layer geometry intersection inside the Castle zone.
* **Severity:** Major
* **Reproducibility:** 100% [Verified across multiple independent high-cycle New Game Plus profiles]

## Preconditions
1. Progress the main storyline to the final mission ("The Last Supper").
2. Active endgame save file loaded (verified on high-cycle NG7+/NG8+ progression matrices).
3. Secure the Castle interior staircase area by eliminating all hostile Baron Soldier entities.

## Steps to Reproduce
1. Advance up the central staircase to the upper horizontal platform area during the active pursuit of the Baron.
2. Activate the Survival Sense mechanism to scan the structural floor layout and the carpet asset layer.
3. Observe the 5 white spatial interaction indicators highlighting dropped weapon nodes.
4. Position the crosshair directly over the visible dropped weapon models lying on the floor surface.
5. Move closely over all 5 weapon coordinates, then retreat and re-approach the points from the opposite direction.
6. Execute a manual physical kick interaction directly into the highlighted weapon matrices to verify object state stability.

## Actual Result
The interaction layer completely fails to initialize loot prompt triggers for weapon assets dropped on specific Castle platform nodes. 
The underlying geometry layer or the decorative carpet asset mesh intersects and occludes the weapon loot boundaries. Faint indicator pings confirm 5 active items, but multiple weapon models are visually clipped underneath the solid floor structure, while the remaining visible weapons fail to generate any looting UI prompts. The physical kick interaction applies zero velocity force, proving that the weapon arrays are locked in a persistent, non-interactive asset loop.

## Expected Result
Dropped weapon assets must maintain fully operational interaction volumes regardless of the underlying structural layout layers. 
Decorative asset meshes (like carpets) must not clip or occlude loot UI trigger boxes. Fired survival scans and direct crosshair targeting must consistently render loot prompts, and object arrays must retain basic physics reactivity until collected.

## Attachments
* Video Proof 1: `castle_staircase_weapon_loot_occlusion_004_1080p.mp4` (High-cycle profile verification)
* Video Proof 2: `last_supper_weapon_asset_lock_kick_test_557_1080p.mp4` (Physics lock and scan verification)

---

[LinkedIn Profile](https://www.linkedin.com/in/balazs-manual-qa-specialist/)



[GitHub Profile](https://github.com/GhostHit-Fixer/)



The fix is on the house. :)



- GhostHit_Fixer™
