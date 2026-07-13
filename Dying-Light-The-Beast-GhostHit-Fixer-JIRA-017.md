# [JIRA BOX #17 - PROJECT_2_v1.6.0 - MILITARY FACTION STATE MACHINE COLLAPSE]

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
* **Title:** [AI/Behavior] [Combat-Collision] Total State Machine paralysis and damage invulnerability on Military Encounter Entities during "Secrets in the Air" Main Quest phase.
* **Severity:** Critical
* **Reproducibility:** 80% / Persistent high-rate regression verified across multiple cold starts on NG8+/NG9+ profiles.

## Preconditions
1. Progression reached Main Quest: "Secrets in the Air" (Radio Relay area active).
2. Character profile operating on highly accumulated endgame save files (NG8+ / NG9+).
3. Game difficulty set to Nightmare Mode (Disables baseline floating HUD vital indicators).

## Steps to Reproduce
1. Load save game and navigate to the highway off-ramp intersection adjacent to the Radio Relay in the Cement Gardens district.
2. Locate the dynamically spawned Military Loot Encounter (consisting of 5 Military AI entities, sandbags, wooden roadblocks, and a locked loot crate).
3. Walk directly in front of the standing Military AI assets to trigger their perception sweeps.
4. Attempt to sprint directly through the physical model of any Military AI asset.
5. Execute consecutive melee attacks using a one-handed Axe and standard kicks into the center of the AI meshes.
6. Equip the Iconic Rifle and fire several rounds directly into the torso of the AI assets, then fire into the environmental fuel spill at their feet.
7. Interact with the central locked crate, complete the lockpicking minigame, and empty the loot array.

## Actual Result
The dynamically spawned Military Encounter entities encounter a total structural State Machine paralysis. The AI completely fails to transition into an aggressive combat posture upon direct line-of-sight exposure on Nightmare. Physically, the assets act as solid obstacles (preventing the character from clipping through them), but all weapon interactions trigger a complete GhostHit anomaly: melee strikes and firearms pass through the models with zero impact audio or damage registration, and the crosshair turns yellow (Friendly NPC status). An environmental fuel fire explosion at their feet is completely ignored. The look-at script remains active, as the AI heads track the player's movement, but no combat triggers execute. Upon looting the crate, the HUD correctly registers "Encounter Successful", but the 5 entities remain permanently frozen, invincible, and unresponsive. 

## Spatial Deviation Analysis
* Out of the 5 spawned entities, exactly 3 exhibit a spatial clipping failure where their feet assets are permanently submerged underneath the asphalt terrain geometry. The remaining 2 render at standard baseline height.

## Internal Lab Observation (Unsupported by Active Proof - For Review)
* Hostile interaction failure extends across factions: during secondary sweeps, wandering Viral assets targeted the player exclusively, completely ignoring the physical volume of the unresponsive Military entities despite direct pathfinding obstruction.

## Attachments (MPC-HC Frame-by-Frame Verified Archive)
* Video Proof A: `BUG_17_A_military_perception_clipping_893.mp4` (Asphalt clipping, perception bypass, and fuel fire sub-test - 13s)
* Video Proof B: `BUG_17_B_weapon_matrix_immunity_504.mp4` (Solid boundary block vs. melee/ballistic damage immunity checks - 21s)
* Video Proof C: `BUG_17_C_lookat_logic_freeze_966.mp4` (Post-loot analysis showing active head-tracking alongside total combat paralysis - 42s)

---

[LinkedIn Profile](https://www.linkedin.com/in/balazs-manual-qa-specialist/)



[GitHub Profile](https://github.com/GhostHit-Fixer/)



The fix is on the house. :)



- GhostHit_Fixer™

