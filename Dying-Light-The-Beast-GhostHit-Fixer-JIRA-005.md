# [JIRA BOX #5 - PROJECT_2_v1.6.0 - GLOBAL MASTER TEMPLATE FORMAT]

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
* **Title:** [Physics/Collision] [Entity-Movement Anchor] Character transform hard-lock triggered by desynced Viral corpse ragdoll in Saint Paul Tunnel.
* **Severity:** Medium
* **Reproducibility:** 10% / 1 out of 10 attempts verified

## Preconditions
1. Active playthrough on Nightmare Mode with an active firearm (SMG) equipped.
2. Character must be inside the Saint Paul Tunnel sub-zone during or after the initial military support mission.

## Steps to Reproduce
1. Locate and eliminate an aggressive Viral entity inside the Saint Paul Tunnel zone using clean headshots.
2. Approach the falling corpse immediately while the ragdoll model undergoes its passive ground alignment script.
3. Observe that the loot prompt [F - Search] fails to initialize due to a state machine breakdown.
4. Move the character model directly into the un-lootable entity boundary to force a hitbox intersection.

## Actual Result
The character transform becomes completely anchored to a single 3D coordinate point. WASD inputs force the character model to perform rotational stepping animations, but the central position remains locked. Jump and Kick mechanics are completely unresponsive. 

## Expected Result
Entity bounding boxes should never merge or lock character transform positions. Loot interaction frames must remain active regardless of ragdoll state, and the player model should slide off the corpse asset smoothly.

## Attachments
* Video Proof: `BUG_05_tunnel_viral_lock_1080p.mp4` (Character transform hard-lock video proof)

---

[LinkedIn Profile](https://www.linkedin.com/in/balazs-manual-qa-specialist/)



[GitHub Profile](https://github.com/GhostHit-Fixer/)



The fix is on the house. :)



- GhostHit_Fixer™

