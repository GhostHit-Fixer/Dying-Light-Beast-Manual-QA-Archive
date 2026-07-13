# [JIRA BOX #15 - PROJECT_2_v1.6.0 - DASH BASH INPUT RACE CONDITION]

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
* **Title:** [Animation/Input] [State-Machine] Input Race Condition during Dash-to-Bash transition allows weapon firing logic to execute while character model is unarmed.
* **Severity:** Medium
* **Reproducibility:** 100% / Verified 3 out of 3 times within a single controlled test sequence.

## Preconditions
1. Character equipped with a standard ballistic ranged weapon (e.g., Iconic Rifle).
2. Stamina pool must be fully charged (Required condition to trigger active Dash status).
3. Test conducted in an isolated environment free of hostile AI entities to prevent external collision variables.

## Steps to Reproduce
1. Load save game inside an isolated straight corridor zone (e.g., Mine Shaft).
2. Equip the Iconic Rifle and begin forward movement, activating the high-speed stamina-consuming Dash ability.
3. Observe that the weapon model is automatically hidden/sheathed during the Dash sequence, showing only empty hands.
4. While actively Dashing, immediately press the Primary Attack Key [Default: Left Mouse Button] to execute a physical "Bash" charge.
5. Observe the UI stamina tracking gauge and listen closely to the audio output layer during the transition.
6. Stop moving to let the character return to an idle state, then repeat the sequence multiple times consecutively.

## Actual Result
An Animation/Input Race Condition occurs during the transition between the Dash and Bash states. When the Primary Attack Key is triggered, the game successfully executes the physical Bash charge animation. However, the Weapon State Machine simultaneously registers a weapon firing input: an audible gunshot sound plays, and exactly 1 round is permanently deducted from the current magazine capacity, despite the 3D weapon model being completely sheathed and inactive. No visual muzzle flash or barrel smoke FX are rendered during this ghost firing cycle. Upon exiting the Bash state, the rifle instantly re-renders in the character's hands without frame-delays.

## Expected Result
Activating a physical Bash melee charge during a stamina-based Dash sequence must completely intercept and override all ranged weapon fire inputs. The weapon firing script must be locked until the character model exits the unarmed sprint/charge states and successfully re-equips the active firearm asset.

## Attachments
* Video Proof: `BUG_15_dash_bash_input_race_condition_1080p.mp4` (16-second controlled lab sequence verifying a consistent 3/3 reproduction rate)

---

[LinkedIn Profile](https://www.linkedin.com/in/balazs-manual-qa-specialist/)



[GitHub Profile](https://github.com/GhostHit-Fixer/)



The fix is on the house. :)



- GhostHit_Fixer™
