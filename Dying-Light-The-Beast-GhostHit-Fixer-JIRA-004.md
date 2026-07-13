# [BOX 1: JIRA RECONSTRUCTED BUG REPORT - ANGOL & MAGYAR]

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
* **Title:** [Gameplay/Interaction] Ragdoll collision state locks out Loot/Camouflage prompts on dead Hazmat Infected until forced physical physics reset.
* **Severity:** Medium (Interaction Conflict / Core Reward Blocker)
* **Reproducibility:** 100% (Verified via multiple consecutive kills)

## Preconditions
* **Game mode:** Nightmare Difficulty active.
* **Player must locate and eliminate a Hazmat Infected enemy via clean headshots,** leaving the oxygen tank asset on its back completely intact.

## Steps to Reproduce
1. Eliminate a Hazmat Infected enemy using a ranged weapon (SMG verified).
2. Approach the fallen corpse lying on the ground.
3. Perform a full 360-degree orbit walk around the body to test camera collision angles for interaction prompts.
4. Verify that both the `[F - Search]` and `[G - Camouflage]` UI prompts are completely missing from all angles.
5. Perform a basic physical melee strike or kick `[Default E]` directly onto the dead ragdoll mesh to force a physics engine status reset.
6. Observe the immediate reaction of the UI prompts and the oxygen tank asset.

## Actual Result
Upon death, the Hazmat ragdoll settles into a glitched state that entirely locks out the `[F - Search]` and `[G - Camouflage]` prompts. Performing a basic kick `[E]` successfully resets the physics state and flashes the loot prompts, but it simultaneously registers as a melee impact on the oxygen tank hitbox. The tank begins sparking and igniting, forcing the player to dodge away before the resulting explosion permanently destroys the corpse and eliminates all possible loot rewards.

## Expected Result
Fallen Hazmat Infected ragdolls should immediately trigger accessible `[F]` and `[G]` interaction UI prompts from any valid angle upon entering a stationary ground state. Basic kicks on dead companion assets should not auto-ignite intact structural hitboxes if used strictly as a tactical interaction workaround.

## Attachments
* `BUG_04_hazmat_ragdoll_trap_01.mp4` (Primary ignition anomaly video proof)
* `BUG_04_hazmat_ragdoll_control_02.mp4` (Secondary physics reset control video)

---
[LinkedIn Profile](https://www.linkedin.com/in/balazs-manual-qa-specialist/)

[GitHub Profile](https://github.com/GhostHit-Fixer/)
 The fix is on the house. :)

- GhostHit_Fixer™

