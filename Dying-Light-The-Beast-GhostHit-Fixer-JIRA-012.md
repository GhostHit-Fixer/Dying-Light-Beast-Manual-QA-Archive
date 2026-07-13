# [JIRA BOX #12 - PROJECT_2_v1.6.0 - AI STATE MACHINE & RAYCAST COLLAPSE]

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
* **Title:** [AI/Combat] [Raycast Collapse] Sniper AI enters infinite firing loop bypassing reload scripts while damage registration completely fails.
* **Severity:** Critical / Blocker
* **Reproducibility:** 100% (14-shot sequence verified via frame-by-frame analysis)

## Preconditions
1. Game mode set to Restored Land.
2. Character must engage a hostile armed Sniper entity (Baron Soldier) in an open-world hillside terrain sector (Upper-Left quadrant of the map).
3. Character equipped with a high-precision firearm (e.g., Iconic Rifle).

## Steps to Reproduce
1. Load the manual save and approach the designated hillside combat zone.
2. Locate the active Sniper entity and step into its direct line of sight at a close-range distance of approximately 3 meters.
3. Stand completely motionless while the Sniper anchors its red laser sight indicator directly onto the player's character model.
4. Allow the Sniper to initiate its offensive sequence and maintain a static position for a minimum of 14 consecutive shots.
5. Aim down sights (ADS) with the Iconic Rifle, execute a clean headshot to eliminate the entity, and immediately pulse the Survival Sense radar while tracking the ragdoll body rolling down the hill slopes.

## Actual Result
A catastrophic breakdown occurs across the AI state machine and combat raycast sub-systems simultaneously. The Sniper entity completely bypasses its hard-coded 5-shot magazine capacity limits, entering an infinite firing loop executing 14 consecutive shots with full muzzle flash and audio cues but zero reload animations. Concurrently, projectile damage calculation completely crashes: despite the laser indicator being anchored to the player, the raycast registers 0 damage. The player's health bar remains pixel-identical, with zero visual flinching, grunting, or blood decals. Upon headshot elimination, the weapon asset instantly clips and despawns through the hillside terrain mesh, leaving zero pickup prompt, while the standard human corpse loot matrix ('[F] Search') remains accessible.

## Expected Result
Sniper AI entities must strictly adhere to ammunition constraints and trigger mandatory reload animations after every 5-shot magazine cycle. Projectile raycasts matching an anchored laser sight indicator must register valid hits on the player hitbox, applying high-tier Restored Land damage modifiers, visual flinch indicators, and audio grunts. Eliminated entities must drop weapon assets onto the surface terrain with functional physics and interaction layers instead of clipping into the geometry.

## Attachments
* Video Proof: `BUG_12_sniper_ai_infinite_loop_720p.mp4` (14-shot frame-verified sequence via MPC-HC)

---

[LinkedIn Profile](https://www.linkedin.com/in/balazs-manual-qa-specialist/)



[GitHub Profile](https://github.com/GhostHit-Fixer/)



The fix is on the house. :)



- GhostHit_Fixer™
