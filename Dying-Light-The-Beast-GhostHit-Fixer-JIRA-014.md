# [JIRA BOX #14 - PROJECT_2_v1.6.0 - THE LAST SUPPER BARRICADE HITBOX LOCK]

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
* **Title:** [Physics/Collision] [Hit-Registration] Structural Barricade asset hitbox alignment failure blocks standard melee kick interactions during "The Last Supper" Castle ascent.
* **Severity:** Major
* **Reproducibility:** 100% / Edge-case vertex breakdown verified across multiple playthroughs.

## Preconditions
1. Progression reached Final Main Quest: "The Last Supper" (Castle multi-level basement ascent phase).
2. Character equipped with standard cosmetic layers (e.g., Beaver Costume - verified passive visual variable only).
3. Character operating in standard human form (No active Beast Mode modifiers).

## Steps to Reproduce
1. Load save game and navigate through the underground basement network leading up to the Castle entrance.
2. Advance to the top of the stairwell corridor and position the character directly flush against the center of the wooden structural barricade asset.
3. Perform 6 consecutive standard melee kicks [Default Kick Input] directly into the central face of the barricade mesh.
4. Observe the lack of structural damage audio or particle debris registration.
5. Shift the character angle or crosshair alignment slightly to the absolute left edge of the barricade asset.
6. Execute the 7th melee kick input directly at the left perimeter vertex.

## Actual Result
The first 6 consecutive central melee kicks completely fail to register on the barricade's structural destruction tracking routine. The game plays the standard "whiff" audio (as if kicking empty air), and the mesh remains completely static without emitting wood debris FX. However, the 7th kick directed at the absolute left edge instantly triggers the collision logic, executing the fracture script, wood-shattering audio, and physical debris dispersion. 

## Internal Lab Testing Notes
* **Ballistic Weaponry:** Fully Functional. (Firing a standard rifle round directly into the center instantly triggers the destruction sequence).
* **Physical Raycast Collision:** 100% Bugged. (The melee kick raycast fails central alignment checks on flat terrain due to displaced interaction boundaries).

## Attachments
* Video Proof: `BUG_14_barricade_hitbox_edge_trigger_1080p.mp4` (7-second frame-by-frame verified mesh interaction and edge-bypass capture)

---

[LinkedIn Profile](https://www.linkedin.com/in/balazs-manual-qa-specialist/)



[GitHub Profile](https://github.com/GhostHit-Fixer/)



The fix is on the house. :)



- GhostHit_Fixer™
