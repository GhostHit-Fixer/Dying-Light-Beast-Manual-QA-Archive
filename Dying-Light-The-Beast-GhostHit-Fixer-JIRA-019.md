# [JIRA BUG REPORT - BUG_19] - ENGLISH VERSION

## Environment
* **Platform:** PC / Standalone (Offline Mode - Air-Gapped Workstation)
* **OS:** Windows 10 Enterprise 64-bit, Build 19044.1566 (21H2)
* **CPU:** AMD FX(tm)-6300 Six-Core Processor (6 CPUs), ~3.5GHz
* **GPU:** NVIDIA GTX 1050 2GB
* **RAM:** 8GB DDR3 RAM 
* **GPU Driver Version:** 31.0.15.3118
* **Game Version:** v1.6.0 
* **Graphics Profile:** Min-Spec Custom (TAA Enabled, Texture Quality: Low)

## Details
* **Title:** [AI/Physics] [Pathfinding] Dynamic entity navigation mesh trapping and structural collision clipping across manual door meshes.
* **Severity:** Major
* **Reproducibility:** 100% [Verified across multiple independent sub-zones and AI tiers]

## Preconditions
1. Access to the Asylum sub-zone unlocked (requires keycard panel interaction for specific double-door nodes).
2. Access to the Factory sub-zone unlocked with active night cycle capability (Level 1 Chase state required for volatile tracking).

## Steps to Reproduce
1. Load the active checkpoint save and approach the targeted double-door asset in the Asylum corridor.
2. Swipe the keycard to transition the door into an interactive state, then manually execute the opening animation.
3. Agitate a Viral/Zombie entity to trigger an active pursuit state towards the player's coordinate matrix.
4. Reposition the character immediately outside/behind the arc of the opened door blade to force the AI into the narrow boundary gap between the door and the wall texture.
5. Manually close and reopen the door multiple times while observing the entity's collision mesh.
6. **[Alternative Test - Factory]:** Trigger a Level 1 Chase at night, retreat behind a standard closed single-wing door, and observe the Volatile pathfinding routines.

## Actual Result
The dynamic AI pathfinding matrix completely chokes on door mesh states. 
In the Asylum, the Viral asset becomes trapped in a "Trapped State" between the wall and the door blade, while its body parts continuously clip straight through the solid door model. The asset actively tracks the player's minor movements through the solid geometry. It only breaks the loop if the player moves deeper past the door axis, resetting the NavMesh calculation.
In the Factory, during a Level 1 Chase, the Volatile's collision box fails to register the closed door asset completely; half of its 3D model clips straight through the solid door during its running loop before it steps back to repeat the broken cycle.

## Expected Result
Dynamic entities should accurately recalculate paths around physical door geometry based on active NavMesh updates. 
Collision boundaries of doors must remain absolute solid blocks across all open/closed animation states. AI assets should never penetrate solid layout matrices or enter loop stalling phases due to basic door positioning.

## Attachments
* Video Proof 1: `viral_trapped_asylum_door_loop_1080p.mp4` (Control-group loop test)
* Video Proof 2: `zombie_horde_asylum_door_clipping_1080p.mp4` (Multiple entity verification)
* Video Proof 3: `volatile_chase_factory_door_clipping_1080p.mp4` (Apex predator chase tracking)

---

[LinkedIn Profile](https://www.linkedin.com/in/balazs-manual-qa-specialist/)



[GitHub Profile](https://github.com/GhostHit-Fixer/)



The fix is on the house. :)



- GhostHit_Fixer™
