# [JIRA BOX #10 - PROJECT_2_v1.6.0 - SPATIAL COORDINATE REGRESSION AUDIT]

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
* **Title:** [Physics/Scripting] [Spatial Coordinate Leak] Suicider reward interaction vectors dislocate from physical ragdoll models across v1.5 and v1.6.0 loops.
* **Severity:** Medium / Regression
* **Reproducibility:** High (Persistent across multi-version testing)

## Preconditions
1. Active progression during the "Power Gambit" main story mission inside the Waterworks facility.
2. Character must encounter a Suicider entity that is eliminated via partial upper-body damage scripts (leaving a persistent post-detonation torso ragdoll).

## Steps to Reproduce
1. Load the manual save and proceed to the upper metal catwalk/gantry levels inside the Waterworks sub-zone.
2. Locate the persistent Suicider torso entity resting on the flat metal floor grid.
3. Aim the crosshair directly at the physical body mesh and verify interaction availability. [Phase 1]
4. Move the camera reticle 1-2 meters away from the corpse, aiming into empty space at default standing head-height level. [Phase 2]
5. Complete a tight 360-degree walking circle around the physical corpse mesh and verify momentary layout updates.

## Actual Result
A severe spatial vector dislocation occurs where the loot interaction hitbox ('[F] Search' / '[G] Camouflage') unlinks from the physical entity model. When looking directly at the floor-bound torso mesh, zero interaction prompts appear. Looking 1-2 meters away into empty space at standing head-height reveals the fully functional interaction prompt floating in mid-air. The prompt maintains a fixed spatial coordinate anchor (independent of camera rotation). Circling the mesh triggers the UI prompt for a single frame at the actual feet of the corpse before it instantly snaps back to the dislocated air coordinate. This issue has persistently survived from version 1.5 into 1.6.0 without validation fixes.

## Expected Result
The interaction matrices and UI prompt anchors must remain strictly synchronized with the physical location of the target entity mesh at all times. Upon detonation, the interaction point should transition dynamically to the resting coordinates of the remaining ragdoll torso, rather than leaking and anchoring to the pre-detonation vertical standing coordinate.

## Attachments
* Video Proof: `BUG_10_suicider_vector_dislocation_1080p.mp4` (Control camera tracking on catwalk)

---

[LinkedIn Profile](https://www.linkedin.com/in/balazs-manual-qa-specialist/)



[GitHub Profile](https://github.com/GhostHit-Fixer/)



The fix is on the house. :)



- GhostHit_Fixer™


