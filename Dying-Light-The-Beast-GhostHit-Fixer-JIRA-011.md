# [JIRA BOX #11 - PROJECT_2_v1.6.0 - ASSET RUNTIME INTERACTION LOCK]

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
* **Title:** [Scripting/Inventory] [Asset Runtime Lock] Enemy weapon drops generate visual mesh but completely omit interaction hitbox layers across v1.5 and v1.6.0.
* **Severity:** Major / Economy Blocker
* **Reproducibility:** High (Persistent regression across multiple sub-zones)

## Preconditions
1. Game mode set to Restored Land (No resource or enemy respawn active).
2. Physical access to main story areas containing armed entities (e.g., E&F Factory rooftop or Mine entrance exterior).

## Steps to Reproduce
1. Load the offline manual save and proceed through the active main mission sector.
2. Eliminate any weapon-wielding hostile entity (e.g., Baron Soldiers or Renegade archers) and trigger their death-drop script.
3. Locate the physical weapon asset dropped onto the terrain surface (Test Case 1: Bow on flat factory concrete roof | Test Case 2: Sniper Rifle on uneven grass/dirt ground).
4. Activate the Survival Sense radar pulse to check object visibility.
5. Approach the asset closely from a standing position and execute a standard physical kick [E].

## Actual Result
The drop script successfully instantiates the visual 3D asset mesh and applies physics gravity (allowing models to fall from roofs to the ground normally). However, the runtime engine completely omits the interaction hitbox layer and physical collision registry. The UI prompt for '[F] Pick Up' or '[G] Swap' is completely missing. Survival Sense radar pulses successfully detect the root object (flashing the standard white indicator ring above the asset), but a physical kick applies zero impulse force, passing straight through the mesh. This layout omission leaves the weapon entirely uncollectable before despawning at a 50-meter distance, causing permanent resource depletion in Restored Land mode. This regression has persistently survived from version 1.5 into 1.6.0.

## Expected Result
All hostile weapon drops must dynamically instantiate with their full complement of behavioral layers. Visual meshes must be accompanied by active collision boundaries (allowing physics manipulation via kicks) and a standardized interaction hitbox that triggers the pickup/swap UI array instantly within a 1-2 meter proximity vector.

## Attachments
* Video Proof: `BUG_11_weapon_drops_interaction_lock_720p.mp4` (Combined Bow and Rifle runtime lock footage verified via MPC-HC)

---

[LinkedIn Profile](https://www.linkedin.com/in/balazs-manual-qa-specialist/)



[GitHub Profile](https://github.com/GhostHit-Fixer/)



The fix is on the house. :)



- GhostHit_Fixer™
