# [BUG_20_JIRA_REPORT - STRUCTURAL_MESH_COLLISION_LAYER_BYPASS]

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
* **Title:** [Physics/Geometry] [Collision Map] Structural sector corner mesh leakage and asymmetric hit-registration bypass across interior walls.
* **Severity:** Major
* **Reproducibility:** 100% [Verified in Basement and First Floor sub-sectors]

## Preconditions
1. Access to the Asylum facility sub-zone unlocked.
2. Iconic Rifle and Iconic SMG equipped in active weapon loadout slots for hitscan verification.

## Steps to Reproduce
1. Load the active save game and position the character inside the Asylum basement structural chamber.
2. Agitate a Volatile entity located out in the main corridor. Remain stationary away from the closed door mesh.
3. Observe the entity's pathfinding vector shifting to compute the absolute shortest linear path (Z-axis/X-axis projection) through the solid corner wall geometry instead of routing via the door frame.
4. Maintain a 2-3 meter safety threshold from the wall layer, aim at the protruding 3D mesh head of the entity, and fire the Iconic Rifle.
5. Move to the Asylum First Floor corridor, position the character outside a closed room, and agitate an interior Viral entity.
6. Maintain a 0.5-meter distance from the corner node, wait for the Viral's upper torso mesh to penetrate the structure, and fire the Iconic SMG.

## Actual Result
The structural layout mesh fails to maintain absolute boundary integrity against active AI chase paths. 
In both the basement and the first floor, the entities' navigation routines force their 3D models to partially clip straight through solid interior walls to close the distance to the player. The hitscan verification is fully functional from the player's side: firing at the protruding asset nodes registers valid headshots. Upon elimination, the blood splash decals incorrectly render on the interior wall (player-side wall surface), proving that the geometry lacks a solid physical blocking volume during active pursuit phases.

## Expected Result
All structural interior and exterior wall layers must possess permanent, absolute collision boundaries. 
Dynamic AI entities must be structurally prohibited from penetrating solid geometry layers regardless of the computed shortest-path navigation vectors. Damage registration and texture decal matrices must not execute inside the safe boundary zone due to external asset leakage.

## Attachments
* Video Proof 1: `volatile_basement_wall_bypass_hitscan_1080p.mp4` (Basement isolation test)
* Video Proof 2: `viral_first_floor_corner_clipping_smg_1080p.mp4` (First-floor corner replication test)

---

[LinkedIn Profile](https://www.linkedin.com/in/balazs-manual-qa-specialist/)



[GitHub Profile](https://github.com/GhostHit-Fixer/)



The fix is on the house. :)



- GhostHit_Fixer™
