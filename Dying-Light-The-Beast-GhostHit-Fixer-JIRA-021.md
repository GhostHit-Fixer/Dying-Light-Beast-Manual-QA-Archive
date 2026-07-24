# [BUG_21_JIRA_REPORT - Z-AXIS_SPAWN_GLITCH_ASYMMETRIC_DECAL_RENDERING]

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
* **Title:** [Art/Environment] [Spawning] Severe Z-axis coordinate spawn displacement on static environmental assets combined with asymmetric 2D decal occlusion rendering.
* **Severity:** Medium
* **Reproducibility:** 100% [Persistent across clean scene reloads]

## Preconditions
1. Access to the Industrial Sector outer boundaries unlocked.
2. Locate the flooded railway tracks ("Junkyard Flooded Tracks") situated in close proximity to the Bus Refuge safe zone.
3. Iconic Rifle equipped for long-range impact particle verification.

## Steps to Reproduce
1. Load the active save game and travel to the flooded railway tracks near the edge of the Industrial Sector.
2. Advance to the end of the railway tracks where the water depth reaches ankle level and look upward at a 45-degree angle.
3. Observe the caked/dismembered static environmental zombie asset (torso, upper limbs, head) floating roughly 4-5 meters high in mid-air.
4. Execute a jump-collision test utilizing a wandering entity to verify the floating entity physical collision volume.
5. Move 180 degrees around the asset coordinate, and cycle between approaching and retreating from the vertex to verify texture layer rendering.
6. Park a vehicle directly underneath the asset, climb onto the roof surface to achieve a 1-meter proximity threshold, and fire the Iconic Rifle directly into the floating geometry.

## Actual Result
A pre-placed static environmental asset fails to snap to the terrain layout due to a severe Z-axis spawn vector displacement. 
The asset hovers 4-5 meters in mid-air but retains its full solid collision volume, completely halting player momentum during vertical jumping tests. Furthermore, the attached vertical 2D blood drip decal strip suffers from a broken asymmetric shader rendering routine: the texture completely disappears from the top-down or bottom-up perspective depending on proximity distance, and completely un-renders when viewed from a 180-degree lateral angle. Firing into the asset from the vehicle roof registers clear projectile spark impact particles, proving the physical mesh presence is active despite the spatial displacement.

## Expected Result
Pre-placed static environmental decoration assets must snap flawlessly to the surface terrain mesh parameters. 
Z-axis spawn coordinates must be hard-locked to prevent gravity-defying asset hovering. All attached 2D texture decals and shader strips must utilize uniform omnidirectional rendering passes to maintain absolute visibility regardless of player proximity or lateral viewing angles.

## Attachments
* Video Proof 1: `floating_torso_flooded_tracks_collision_042_1080p.mp4` (Jump collision verification)
* Video Proof 2: `environmental_asset_occlusion_angle_test_096_1080p.mp4` (Distance and 180-degree tracking test)
* Video Proof 3: `car_roof_hit_registration_vertical_shader_520_1080p.mp4` (Proximity hit-registration check)

---

[LinkedIn Profile](https://www.linkedin.com/in/balazs-manual-qa-specialist/)



[GitHub Profile](https://github.com/GhostHit-Fixer/)



The fix is on the house. :)



- GhostHit_Fixer™
