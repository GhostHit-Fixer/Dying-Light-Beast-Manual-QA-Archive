# [JIRA BUG REPORT] SYSTEM: DYING LIGHT: THE BEAST v1.6.0 (OFFLINE MIN-SPEC SETUP)

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
* **Title:** [Physics/Collision] [Invisible Wall] Severe invisible hitbox blocking bullet registration at the Church basement archway entrance.
* **Severity:** Major / High (Combat Core Disruption)
* **Reproducibility:** 100% (3/3 consecutive test cycles verified)

## Preconditions
* **Location:** Castor Woods - Church Zone (Jacob's initial basement quest area).
* **Setup:** Low-end video settings active (TAA enabled, 1080p profile).

## Steps to Reproduce
1. Reach the Church area and go to the basement entrance stairwell.
2. Stand directly inside the archway on the top step (1 step before dropping down to the basement level).
3. Locate an infected enemy standing directly below/inside the basement passage (Close range, approx. 3-5 meters away).
4. Aim directly at the enemy through the open space of the archway (Ensure the crosshair is clear of the visible stone pillar).
5. Fire multiple consecutive magazines using a ranged weapon (SMG tested).

## Actual Result
An invisible collision box extending from the side pillar completely blocks all projectiles. Bullets disappear into thin air without hitting the target, leaving no bullet decals on the visible stone but causing 0 damage to the enemy. The control group test verified that weapon hit registration functions normally when shooting at non-blocked targets immediately after.

## Expected Result
Projectiles should pass freely through the open space of the archway and register damage on the enemy. The invisible collision geometry should strictly match the visible boundaries of the stone asset.

## Weapon Matrix Details [Lab Testing Completed]
* **SMG (40-round mag):** [ STATUS: 100% BLOCKED / 0% DAMAGE REGISTRATION ]
* **Rifle (25-round mag):** [ STATUS: 100% BLOCKED / 0% DAMAGE REGISTRATION ]
* **Handgun/Pistol:** [ STATUS: 100% BLOCKED / 0% DAMAGE REGISTRATION ]
* **Revolver:** [ STATUS: 100% BLOCKED / 0% DAMAGE REGISTRATION ]
* **Shotgun:** [ STATUS: 100% BLOCKED / 0% DAMAGE REGISTRATION ]
* **Bow / Crossbow:** [ STATUS: 100% BLOCKED / 0% DAMAGE REGISTRATION ]

## Attachments
* `BUG_03_invisible_wall_archway_1080p.mp4` (Control group stress-test video proof)

---
[LinkedIn Profile](https://linkedin.com)

[GitHub Profile](https://github.com)

 The fix is on the house. :)

- GhostHit_Fixer™

