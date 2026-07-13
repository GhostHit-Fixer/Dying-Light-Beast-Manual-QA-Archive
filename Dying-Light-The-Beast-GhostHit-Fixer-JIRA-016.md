# [JIRA BOX #16 - PROJECT_2_v1.6.0 - SCHOOLS OUT VERSION CROSS-CONTAMINATION]

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
* **Title:** [Quest-Logic] [State-Machine] Pre-emptive AI door provocation triggers legacy v1.5 script overlap during v1.6 "School's Out" Main Quest, causing a hybrid objective state.
* **Severity:** Critical
* **Reproducibility:** 100% / Persistent legacy code bleed-through verified via structural sequence bypass.

## Preconditions
1. Progression reached Main Quest: "School's Out".
2. Character located in the school courtyard prior to initiating the mandatory conversation with the Scout NPC.
3. Access to environmental explosive assets (Gas Tank) available in the immediate vicinity.

## Steps to Reproduce
1. Load save game at the school exterior phase. Before speaking to the Scout NPC, pick up a Gas Tank and throw it at the gymnasium window structure.
2. Detonate the tank to generate high-volume environmental explosion noise, forcing the hostile Bandit AI inside the locked gymnasium to transition into a search/attack state and manually open the exterior-locked double doors to exit.
3. Initiate and complete the mandatory conversation script with the Scout NPC to advance the main quest.
4. Enter the gymnasium via the pre-opened doors and observe the HUD quest tracker objective instructions.
5. Use Survival Sense to scan the gymnasium interior and locate the highlighted quest object markers.
6. Advance through the basement network to lockpick the Scientist's door, trigger the rescue cutscene, obtain the Key, and open the primary document cabinet.

## Actual Result
By forcing the Bandit AI to manually open the locked gymnasium doors prior to the Scout trigger, the game engine encounters a severe state-machine override. Instead of executing the streamlined v1.6 single-document script ("Retrieve the Document"), the logic layer references the legacy v1.5 code block, forcing the "Retrieve Research Documents 0/5" tracking array onto the HUD. Survival Sense highlights the 4 deleted legacy documents in the main room alongside the 5th object (Scientist Key/Document) inside the locked backroom. Collecting the legacy assets advances the counter (1/5, 2/5). Despite this hybrid code contamination, rescuing the scientist and opening the v1.6 cabinet successfully overrides the array and executes the final cinematic transition, preventing a hard progression lock.

## Expected Result
Environmental audio/combat triggers must not bypass current quest phase condition gates. The state machine must actively restrict the rendering and interaction scripts of legacy v1.5 assets ("0/5 Documents") regardless of the physical status of the gymnasium access doors during v1.6 execution.

## Attachments (MPC-HC Frame-by-Frame Verified Archive)
* Video Proof A: `BUG_16_A_school_trigger_bypass_01.mp4` (AI door bypass and 0/5 HUD trigger - 5s)
* Video Proof B: `BUG_16_B_legacy_item_pickup_02.mp4` (Interaction and collection of deprecated v1.5 assets - 21s)
* Video Proof C: `BUG_16_C_survival_sense_wall_bypass_03.mp4` (Survival Sense wall-scan verifying 5th object coordinate - 21s)
* Video Proof D: `BUG_16_D_hybrid_quest_resolution_04.mp4` (Successful phase progression via final cabinet interaction - 19s)

---

[LinkedIn Profile](https://www.linkedin.com/in/balazs-manual-qa-specialist/)



[GitHub Profile](https://github.com/GhostHit-Fixer/)



The fix is on the house. :)



- GhostHit_Fixer™

