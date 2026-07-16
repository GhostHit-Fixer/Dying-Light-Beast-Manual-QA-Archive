# [JIRA BOX #16 - PROJECT_2_v1.6.0 - QUEST STATE MACHINE ASYNCHRONOUS UI DESYNC]

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
* **Title:** [Quest-Logic] [UI-Regression] AI-driven courtyard(gym) door manipulation triggers asynchronous Quest State Machine desynchronization, forcing HUD into a generic Area Tracker state during "School's Out" Main Quest.
* **Severity:** Medium
* **Reproducibility:** 100% / Persistent UI logic regression verified via structural sequence bypass.

## Preconditions
1. Campaign progression reached Main Quest: "School's Out".
2. Character located in the school exterior courtyard after completing the mandatory conversation script with the Scout NPC.
3. Access to environmental explosive assets (Gas Tank) available in the immediate vicinity.

## Steps to Reproduce
1. Load the active save game at the school exterior phase. Do not enter through the main school entrance.
2. Pick up a Gas Tank, transport it to the closed gym exterior courtyard doors, and detonate it near the windows.
3. Observe the hostile Bandit AI inside transitioning into a search state due to the high-volume audio trigger, causing them to internally unlock and manually open the exterior double doors to exit.
4. Perform a sequence break by sliding past the alerted AI and entering the gym directly, bypassing the intended interior corridor progression path.
5. Execute Survival Sense near the entrance and monitor the compass/HUD tracking behavior.
6. Interact with the 4 separate desks inside the gym to collect the paper lore document assets, then proceed to the basement to free the Scientist and unlock the primary cabinet.

## Actual Result
By bypassing the internal corridor trigger gates via AI door manipulation, the quest state machine fails to dynamically update the active player coordinates. Instead of correctly locking the objective marker straight onto the Scientist's backroom door (standard v1.6 behavior), the HUD telemetry regresses into a broad search state. The compass displays the generic "Inside Objective Arena" zone tracker, while the side Quest Log displays the "0/5 Retrieve the research from the gym outpost" progression criteria. The engine successfully registers physical item interactions out of order (updating the sidebar log to 1/5, 2/5 upon collecting desk documents), but fails to synchronize the primary spatial objective pin. Rescuing the Scientist later successfully forces a recovery script execution, realigning the UI with the active quest lane without causing a hard lock.

## Expected Result
Spatial HUD markers and quest tracking state machines must validate active player coordinates independently of specific corridor trigger sequences. Entering the destination zone early via environmental exploit must seamlessly update the primary objective pin to the active sub-objective (Scientist Room Boundary) rather than reverting the HUD telemetry back to a generic area search box.

## Attachments
* Video Proof A: `BUG_16_A_school_trigger_bypass_01.mp4` (AI door bypass and initial main entrance objective pointer validation - 5s)
* Video Proof B: `BUG_16_B_arena_tracker_hud_02.mp4` (HUD displaying "Inside Objective Arena" and "0/5" log upon direct entry - 21s)
* Video Proof C: `BUG_16_C_document_desk_interaction_03.mp4` (Collection of lore assets on desks advancing the desynced counter - 21s)
* Video Proof D: `BUG_16_D_quest_alignment_recovery_04.mp4` (Successful state realignment via backroom Scientist rescue interaction - 19s)

---

[LinkedIn Profile](https://www.linkedin.com/in/balazs-manual-qa-specialist/)



[GitHub Profile](https://github.com/GhostHit-Fixer/)



The fix is on the house. :)



- GhostHit_Fixer™
