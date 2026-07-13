# [JIRA BOX #9 - PROJECT_2_v1.6.0 - HAVOK PHYSICS SLEEP FAILURE AUDIT]

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
* **Title:** [Physics/Engine] [Bound-Box Vibration] Ragdoll entities and dropped weapon assets failing to trigger physics sleep state inside the Mine sub-zone.
* **Severity:** Medium
* **Reproducibility:** 100% (Verified via entity cross-testing)

## Preconditions
1. Active main story quest progression tracking that grants physical access to the locked Mine sub-zone (Aiden container area).
2. Character equipped with melee capabilities or standard kick input enabled.

## Steps to Reproduce
1. Load the manual save file and proceed into the main mine shaft area during the designated story mission.
2. Force entry through the destructible wooden barricade obstruction and eliminate the 6-8 standard zombie entities grouped behind it. [Test Case 1]
3. Observe the structural interaction of the dead ragdoll entities as they clip into the debris meshes on the floor terrain.
4. Proceed to the deep section of the mine, eliminate a Baron Soldier entity, and observe the dropped weapon asset (e.g., Common Military Axe) resting on the ground surface. [Test Case 2]
5. Approach both target boundaries closely and execute a standard physical kick [E] to attempt a hard state reset on the jittering meshes.

## Actual Result
The Havok/internal physics engine completely fails to register a 'Sleep State' for complex meshes under high density conditions or post-mortem drop scripts. In Test Case 1, a zombie ragdoll traps itself in an infinite kinetic calculation loop against the broken wooden debris, causing high-frequency vertical shaking (~21-22 FPS). A physical kick successfully recalculates the vectors, causing the entity to slowly decelerate into a static state. In Test Case 2, the dropped Military Axe exhibits continuous rhythmic jittering on flat terrain without external force. Executing a physical kick against the weapon asset applies zero force, and the object fails to stabilize, remaining in a perpetual calculation state despite maintaining a straight frametime line.

## Expected Result
All dynamic physical assets, including organic ragdoll models and dropped weapon entities, must quickly calculate contact points with the terrain matrix and enter a low-overhead physics sleep state within 1-2 seconds of coming to rest. Environmental debris or death script drops should not generate infinite kinetic feedback loops or continuous visual jittering. Kicks should apply uniform force to weapon assets.

## Attachments
* Video Proof: `BUG_09_physics_sleep_failure_720p.mp4` (Combined ragdoll and weapon jittering footage verified via MPC-HC)

---

[LinkedIn Profile](https://www.linkedin.com/in/balazs-manual-qa-specialist/)



[GitHub Profile](https://github.com/GhostHit-Fixer/)



The fix is on the house. :)



- GhostHit_Fixer™
