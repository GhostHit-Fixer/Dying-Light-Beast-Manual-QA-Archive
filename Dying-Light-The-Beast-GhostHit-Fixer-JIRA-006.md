# [JIRA BOX #6 - PROJECT_2_v1.6.0 - GLOBAL MASTER TEMPLATE FORMAT]

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
* **Title:** [UI/Animation] [Mesh Clipping] Campaign Menu stand-up animation regression and "Beaver Costume" hand mesh clipping integration failure.
* **Severity:** Low
* **Reproducibility:** 100% / Continuous loop verification on active save state

## Preconditions
1. "Beaver Costume" cosmetic skin must be unlocked and currently equipped on the active character profile.
2. At least one compatible end-game/NG+ save slot must be present in the main menu pool.

## Steps to Reproduce
1. Launch the game client to the main title screen and navigate directly into the Campaign Selection sub-menu.
2. Observe the idle character animation loop (sitting on the stairs, consuming seeds).
3. Monitor the hand mesh boundary whenever the character lifts a seed to the face area.
4. Select the compatible save slot and press the [Enter / Left Click] confirmation key to initiate the load sequence.

## Actual Result
1. **Mesh Clipping:** Due to the extended spatial boundaries of the Beaver mask asset, the character's hand mesh entirely clips through and vanishes inside the head model during all 3 idle animation variations.
2. **Animation Regression:** Upon confirming the load command, a single frame-skip occurs. The mandatory transitional stand-up animation and its associated audio assets (cloth rustling/door close cues) are entirely bypassed. The character remains seated during the global fade-out sequence.

## Expected Result
1. Hand meshes should have automated collision tracking or adjusted keyframes to prevent model intersection with oversized cosmetic headwear.
2. The UI confirmation routine must smoothly trigger the transitional stand-up sequence and play the designated environment audio cues prior to completing the screen fade-out.

## Attachments
* Video Proof: `BUG_06_beaver_menu_regression_1080p.mp4` (Frame-by-frame verified via MPC-HC)

---

[LinkedIn Profile](https://www.linkedin.com/in/balazs-manual-qa-specialist/)



[GitHub Profile](https://github.com/GhostHit-Fixer/)



The fix is on the house. :)



- GhostHit_Fixer™
