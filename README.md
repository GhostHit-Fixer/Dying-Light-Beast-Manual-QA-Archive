# Dying Light: The Beast — Manual QA Case Study Archive

Official repository for standalone laboratory testing, engine-level regression, and systematic JIRA-compliant bug documentation for *Dying Light: The Beast* (v1.6.0).
---

### 🎬 Video Proofs & Attachments
> ⚠️ **File Size Note:** Due to GitHub's file size limits for individual markdown attachments, all un-cut, frame-verified video proofs are hosted centrally. You can download and review the raw footage for each specific bug report here:
> 👉 **[Direct Link to Video Proofs / Release Assets](https://github.com/GhostHit-Fixer/Dying-Light-Beast-Manual-QA-Archive/releases/tag/Proofs)**

---

## 🛠️ Testing Environment & Methodology
All test cycles were executed on a standardized, min-spec hardware configuration to monitor resource constraints and low-spec engine boundaries:
* **OS:** Windows 10 Enterprise 64-bit (Build 19044.1566)
* **CPU:** AMD FX(tm)-6300 Six-Core Processor (~3.5GHz)
* **GPU:** NVIDIA GeForce GTX 1050 2GB DDR5 RAM (Driver: 31.0.15.3118)
* **Environment:** Standalone, Offline Mode (Air-Gapped Workstation)
* **Graphics Profile:** Min-Spec Custom (TAA Enabled, Texture Quality: Low)

> 💡 **Review Note for Developers:** Due to active pipeline schedules, **it is highly recommended to inspect the Critical and Major functional regressions listed below** first.

---

## 🚨 High Impact Reports (Critical / Blocker & Major)

### [JIRA-012] [AI/Combat] Sniper AI Infinite Firing Loop & Raycast Collapse
* **Severity:** Major / High | **Reproducibility:** 100%
* Catastrophic state machine breakdown where Sniper AI enters an infinite firing loop (14-shot sequence verified) bypassing magazine capacity constraints, while projectile raycasts fail to register damage on the player hitbox.
* 👉 [Open Bug Report](./Dying-Light-The-Beast-GhostHit-Fixer-JIRA-012.md)

### [JIRA-017] [AI/Behavior] Total State Machine Paralysis and Invulnerability
* **Severity:** High / Major | **Reproducibility:** 80% (Regression from v1.5)
* Complete script freeze on Military Encounter entities during the "Secrets in the Air" Main Quest. Assets track player position via look-at scripts but remain completely non-hostile, unresponsive to weapon matrices, and physically clipped into the terrain geometry.
* 👉 [Open Bug Report](./Dying-Light-The-Beast-GhostHit-Fixer-JIRA-017.md)

### [JIRA-002] [Database/Inventory] NG+ Starter Armor Value Inflation Leak
* **Severity:** Major | **Reproducibility:** 100%
* NG+ initialization script sequence duplicates un-tradeable starter gear and incorrectly leaks elite Vanguard defense modifiers onto baseline asset IDs, resulting in a game-breaking economy and stat balancing exploit.
* 👉 [Open Bug Report](./Dying-Light-The-Beast-GhostHit-Fixer-JIRA-002.md)

### [JIRA-003] [Physics/Collision] Invisible Hitbox Wall Blocker at Church Archway
* **Severity:** Major | **Reproducibility:** 100%
* Displaced collision geometry extends from the stone pillars at the Church basement entrance, creating a severe invisible wall that completely blocks all ranged projectiles while rendering no decals.
* 👉 [Open Bug Report](./Dying-Light-The-Beast-GhostHit-Fixer-JIRA-003.md)

### [JIRA-011] [Scripting/Inventory] Enemy Weapon Drops Runtime Interaction Lock
* **Severity:** Major / Economy Blocker | **Reproducibility:** High (Regression from v1.5)
* Drop scripts successfully instantiate 3D weapon meshes from dead hostiles, but the runtime engine entirely omits the interaction hitbox layer, leaving vital resources uncollectable in "Restored Land" mode.
* 👉 [Open Bug Report](./Dying-Light-The-Beast-GhostHit-Fixer-JIRA-011.md)

### [JIRA-014] [Physics/Collision] Barricade Hitbox Alignment Failure during Castle Ascent
* **Severity:** Major | **Reproducibility:** 100%
* Structural barricade asset vertex breakdown during "The Last Supper" quest. Central melee physical raycasts fail to register destruction damage ("whiffing" air), while edge-vertex alignment hits instantly trigger the fracture sequence.
* 👉 [Open Bug Report](./Dying-Light-The-Beast-GhostHit-Fixer-JIRA-014.md)

### [JIRA-016] [Quest-Logic] Quest State Machine Asynchronous UI Desync via Sequence Break
* **Severity:** Major | **Reproducibility:** 100%
* Bypassing intended interior corridor trigger gates via environmental explosive AI doors manipulation causes the objective state machine to fail coordinate tracking, regressing the HUD into an un-synchronized generic Area Tracker state.
* 👉 [Open Bug Report](./Dying-Light-The-Beast-GhostHit-Fixer-JIRA-016.md)

### [JIRA-019] [AI/Physics] Dynamic Entity Navigation Mesh Trapping & Door Clipping
* **Severity:** Major | **Reproducibility:** 100%
* Enemy pathfinding matrices completely fail to calculate manual door asset states, forcing dynamic Viral and Volatile models to clip directly through solid door geometry layers during active pursuit states.
* 👉 [Open Bug Report](./Dying-Light-The-Beast-GhostHit-Fixer-JIRA-019.md)

### [JIRA-020] [Physics/Geometry] Interior Wall Structural Corner Mesh Leakage
* **Severity:** Major | **Reproducibility:** 100%
* Asylum facility interior corner nodes lack solid physical blocking volume. Chase path routines force dynamic entity meshes to penetrate solid walls, allowing asymmetric hitscan registration and graphical decal leaks on the safe side.
* 👉 [Open Bug Report](./Dying-Light-The-Beast-GhostHit-Fixer-JIRA-020.md)

### [JIRA-022] [UI/X] [Physics] Endgame Interactive Weapon Asset Looting Geometry Intersection
* **Severity:** Major | **Reproducibility:** 100%
* Decorative carpet asset layers inside the Castle zone intersect and occlude the interaction boundaries of 5 dropped weapon nodes, permanently locking the endgame asset arrays in a non-interactive loop.
* 👉 [Open Bug Report](./Dying-Light-The-Beast-GhostHit-Fixer-JIRA-022.md)

---

## 📊 Medium Impact Reports (Functional & Logic Anomalies)

* **[JIRA-001] [Inventory/Database] Unique Item Constraint Violation & Duplication**  
  *NG+ persistence bypass allows consecutive collection and separate slot storage of restricted single-instance items.*  
  👉 [Open Report](./Dying-Light-The-Beast-GhostHit-Fixer-JIRA-001.md)

* **[JIRA-004] [Gameplay/Interaction] Ragdoll Collision Interaction Lock on Hazmat Infected**  
  *Dead Hazmat entity physics states lock out search/camouflage prompts until forced reset via physical kicks, risking accidental tank auto-ignition.*  
  👉 [Open Report](./Dying-Light-The-Beast-GhostHit-Fixer-JIRA-004.md)

* **[JIRA-005] [Physics/Collision] Character Transform Hard-Lock in Saint Paul Tunnel**  
  *Desynced Viral corpse ground-alignment script catches player bounding box, hard-anchoring the character transform to a single 3D coordinate.*  
  👉 [Open Report](./Dying-Light-The-Beast-GhostHit-Fixer-JIRA-005.md)

* **[JIRA-007] [Progression/Easter-Egg] High-Frequency Damage Overflow Invulnerability**  
  *High rate-of-fire weapons (SMG/Rifles) cause a calculation overflow/race-condition on hidden crest assets, blocking destruction triggers and Easter Egg progression.*  
  👉 [Open Report](./Dying-Light-The-Beast-GhostHit-Fixer-JIRA-007.md)

* **[JIRA-009] [Physics/Engine] Havok Physics Sleep State Failure inside Mine Sub-Zone**  
  *Complex organic ragdolls and weapon drops fail to trigger kinetic deceleration sleep states under high-density conditions, causing permanent high-frequency jittering.*  
  👉 [Open Report](./Dying-Light-The-Beast-GhostHit-Fixer-JIRA-009.md)

* **[JIRA-010] [Physics/Scripting] Suicider Interaction Vector Dislocation**  
  *Loot interaction vectors un-sync from physical post-detonation torso ragdolls, permanently anchoring the floating UI prompts 1-2 meters away into empty air.*  
  👉 [Open Report](./Dying-Light-The-Beast-GhostHit-Fixer-JIRA-010.md)

* **[JIRA-013] [Quest-Regression] Scientist Corpse Asset Shedding in Factory Basement**  
  *Main story script phase deletes the 3D visual character mesh from the render queue, leaving an invisible but operational interactive logical trigger box on the floor.*  
  👉 [Open Report](./Dying-Light-The-Beast-GhostHit-Fixer-JIRA-013.md)

* **[JIRA-015] [Animation/Input] Dash-to-Bash Transition Input Race Condition**  
  *Flawed animation/input state handling allows ranged weapon firing logic to execute and deduct ammunition while the 3D weapon model is fully sheathed.*  
  👉 [Open Report](./Dying-Light-The-Beast-GhostHit-Fixer-JIRA-015.md)

* **[JIRA-018] [Physics/Collision] Velocity Vector Stalling on Factory Chimney Edges**  
  *Displaced boundary extensions cause character assets to float suspended in mid-air or freeze downward velocity calculations in active falling states.*  
  👉 [Open Report](./Dying-Light-The-Beast-GhostHit-Fixer-JIRA-018.md)

* **[JIRA-021] [Art/Environment] Z-Axis Coordinate Spawn Displacement & Decal Occlusion**  
  *Static environment zombie assets float 4-5 meters high while retaining solid jumping collision, combined with a broken asymmetric 2D blood shader pass.*  
  👉 [Open Report](./Dying-Light-The-Beast-GhostHit-Fixer-JIRA-021.md)

---

## 🛠️ Low Severity & Performance Reports

The remaining reports cover edge-case cosmetics clipping, input latency on specific vendor sub-menus, and minor UI polish anomalies:
* **[JIRA-006]** — *Campaign Menu stand-up animation regression & "Beaver Costume" mesh clipping.*
* **[JIRA-008]** — *Vendor UI input latency and calculation loops during craftpart resource bulk purchases.*

---

**GhostHit_Fixer™**
