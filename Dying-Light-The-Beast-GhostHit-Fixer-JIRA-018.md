# [JIRA BOX #18 - PROJECT_2_v1.6.0 - CHIMNEY HEIGHT PHYSICS STALLING COMBO]

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
* **Title:** [Physics/Collision] [State-Machine] Displaced collision mesh boundaries and velocity vector stalling on Factory Chimney edges cause floating and animation loops.
* **Severity:** Medium
* **Reproducibility:** 100% / Verified across 2 independent test casings on separate quest branches.

## Preconditions
1. Access to the high-rise industrial zone unlocked (Factory Chimneys accessible).
2. Character advanced to the absolute highest perimeter lip of the designated chimney structures.
3. Test captures conducted across separate playthroughs/active quest branches.

## Steps to Reproduce
### [CASE 1: INACTIVE POSITION FLOATING - VIDEO 534]
1. Position the character model roughly 0.5 meters outward over the open edge of the chimney perimeter.
2. Look directly down at the feet assets to confirm total separation from the visual mesh.
3. Perform 360-degree mouse look turns while observing the idle standing animation layer.
4. Execute a minor movement input (WASD) outward, away from the chimney structure.

### [CASE 2: ACTIVE FALLING STATE FREEZE - VIDEO 378]
1. Step off the chimney ledge into the vertical drop vector adjacent to the structure face.
2. Observe the sudden activation of the character's active falling animation layer (legs positioned for drop).
3. Perform consecutive horizontal and vertical camera look sweeps (left, right, up, down).
4. Execute a minor movement input (WASD) away from the chimney boundary line.

## Actual Result
* **CASE 1:** The physics layer fails to calculate gravity updates due to an invisible, displaced extension of the chimney's collision grid. The character remains completely suspended in mid-air in a standard idle standing pose, performing smooth ground-turn foot animations. HUD waypoints stay completely static. A minor movement input terminates the lock, causing a normal drop onto the lower metal catwalk geometry.
* **CASE 2:** The engine registers the vertical drop path and locks the animation state machine into the active "Falling State" (ambient wind audio layer is fully active). However, the downward velocity vector is incorrectly locked at 0. Camera tracking loops do not update the positional data. A minor directional movement input is mandatory to re-engage gravity tracking and complete the landing sequence onto the lower catwalk.

## Expected Result
Physical collision bounds must conform precisely to the visual constraints of the chimney meshes. Stepping beyond the 3D model boundary must instantly initiate gravity tracking, apply downward velocity vectors, and execute an uninterrupted drop transition without requiring secondary movement input updates.

## Attachments
* Video Proof 1: `BUG_18_A_chimney_invisible_ledge_floating_534.mp4` (15-second ambient rain/standing asset capture)
* Video Proof 2: `BUG_18_B_chimney_falling_animation_stall_378.mp4` (15-second wind audio/velocity lock loop capture)

---

[LinkedIn Profile](https://www.linkedin.com/in/balazs-manual-qa-specialist/)



[GitHub Profile](https://github.com/GhostHit-Fixer/)



The fix is on the house. :)



- GhostHit_Fixer™
