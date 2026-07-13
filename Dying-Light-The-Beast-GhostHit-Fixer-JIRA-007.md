# [JIRA BOX #7 - PROJECT_2_v1.6.0 - THE BRESLAU BLADE PROGRESSION BLOCKER]

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
* **Title:** [Progression/Easter-Egg] [Hit-Registration] High-frequency SMG damage overflow causes total invulnerability on Town Hall Crest assets, blocking "The Breslau Blade" unlock.
* **Severity:** Major
* **Reproducibility:** 100% / Verified across multiple Cold Starts on all 9 assets.

## Preconditions
1. Access to Old Town / Town Hall plaza area unlocked.
2. Character equipped with the highest-damage Iconic NG+ Legend Level SMG blueprint variant.
3. No previous triggers on the hidden "Breslau Blade" (Statue Sword) Easter Egg tracking array.

## Steps to Reproduce
1. Locate any of the 9 hidden crest assets surrounding the Town Hall statue in Old Town (including close-range ground crests and long-range tower clock pillars).
2. Aim the crosshair directly at the crest asset bounding box.
3. Fire a continuous stream of ammunition (full 40-round magazine) using the high-ROF Iconic SMG.
4. Observe the visual decal registration (bullet holes, dust particles, debris impact FX) and associated audio cues on the crest mesh.

## Actual Result
Despite registering 40 consecutive hits (proven by visual decals and impact audio), the crest asset fails to trigger its destruction script. The damage calculation routine encounters an overflow/race-condition due to the high frequency of the projectile impacts. The asset remains 100% intact, permanently locking the hidden Easter Egg progression array across multiple Cold Starts.

## Expected Result
Crest assets must have an active structural health threshold that registers damage correctly regardless of weapon fire rate or projectile frequency. Accumulating threshold damage must trigger the mesh destruction sequence to advance the Breslau Blade tracking array.

## Weapon Matrix Details [Lab Testing Completed]
* **Automatic Rifles:** [ STATUS: 100% BUGGED / 0% DAMAGE REGISTRATION ]
* **Iconic SMGs (High RoF):** [ STATUS: 100% BUGGED / 0% DAMAGE REGISTRATION ]
* **Handguns / Pistols:** [ STATUS: 100% BUGGED / 0% DAMAGE REGISTRATION ]
* **Shotguns (Low RoF):** [ STATUS: 100% FUNCTIONAL / DESTRUCTION TRIGGERED ]
* **Revolvers:** [ STATUS: 100% FUNCTIONAL / DESTRUCTION TRIGGERED ]
* **Bows / Crossbows:** [ STATUS: 100% FUNCTIONAL / DESTRUCTION TRIGGERED ]

## Attachments
* Video Proof: `BUG_07_crest_damage_overflow_720p.mp4` (Frame-by-frame verified via MPC-HC)

---

[LinkedIn Profile](https://www.linkedin.com/in/balazs-manual-qa-specialist/)



[GitHub Profile](https://github.com/GhostHit-Fixer/)



The fix is on the house. :)



- GhostHit_Fixer™
