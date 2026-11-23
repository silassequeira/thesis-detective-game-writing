## Appendix X: Implementation Reference

*[Author note: assign the final appendix letter and update every "Appendix X.n" reference in Sections 8.1 and 8.2.]*

This appendix collects the class names, asset identifiers, tuning values, key bindings, and visual specifications referred to in Sections 8.1 and 8.2. All values describe the build evaluated in Chapter 9. Where a scene-configured value differs from the code default, the scene value is the one used in play.

---

### X.1 Scenes and Manager Layout

| Scene | Role |
| :--- | :--- |
| `MainMenu` | Introductory menu |
| `GeometryAttempt` | Six-room precinct; main investigation |
| `Dream_Sequence` | Surreal dream chamber |
| `Ending_Sequence` | Repurposed cell wing; closing sequence |

**Persistent managers** — grouped under `GameManagers_Persistent` (anchored by `PersistentRoot`) and carried across `SceneManager.LoadScene` transitions:
`NarrativeStateManager`, `EvidenceStateManager`, `EvidenceFolderManager`, `SlotManager`, `InternalClockManager`, `PendingEvidenceManager`, `GameStateManager`, `EndingManager`, `NarrativeSuppressionManager`, `SaveManager`, the audio managers (`MusicManager`, `SFXManager`), and the pause and settings UI.

**Scene-scoped infrastructure** — grouped under `GameManagers_Scene`:
`SceneLocalBootstrap`, `CombinationEvaluator`, `EvidenceIDRetriever`, `SlipEventHandler`, `IRSeatManager`, `FlagNarrativeManager`, and sequence controllers, alongside local UI and each character's `CharacterKnowledgeLog`.

---

### X.2 Script and Asset Index

#### Data asset types (`ScriptableObject`)

| Asset type | Role | Database / index |
| :--- | :--- | :--- |
| `EvidenceData` (×61) | Evidence items | — |
| `LogicChainData`, `DialogueNodeData`, `DetectiveQuestion` | Multi-step dialogue chains, their nodes, and individual questions | `LogicChainDatabase` |
| `EvidenceInteractionData` | Standalone single-item and paired interactions | `EvidenceInteractionDatabase` |
| `NarrativeDialogueData` (with `NarrativeChoice`) | Linear narrative sequences | — |
| `SlipEventData` | One-shot narrative events | `SlipEventDatabase` |
| `WorldObjectData`, `WorldObjectActionData` | World objects and their actions | — |
| `ComputerUnlockRule` | Terminal unlock rules | `ComputerUnlockDatabase` |
| `FlagNarrativeRule` | Flag-driven scripted beats | — |
| `NarrativeSuppressionRule` | Retirement of obsolete chains and interactions | `NarrativeSuppressionDatabase` |
| `ChainResetPackage` | Reopening of dialogue loops after cooldowns | — |
| `EndingPathData`, `EndingDialogueOverrideData` | Ending paths and their dialogue overrides | held by `EndingManager` |
| `EvidenceFlagMapping` | Evidence-to-flag mapping entries | held by `EvidenceFlagBridge` |
| `CharacterAnimationConfig` | Flag-to-posture bindings | — |
| `SFXDatabase`, `FlagSFXEntry`, `SFXDefinition` | Sound-effect rules and definitions | — |
| `MusicCueData`, `MusicCueDatabase` | Music cues | — |

#### Runtime components

| Component | Role (key members referred to in Chapter 8) |
| :--- | :--- |
| `NarrativeStateManager` | Shared flag vocabulary (`activeFlags`, `firedEvents`; `SetFlag`, `ClearFlag`, `IsFlagSet`, `FireSlipEvent`, `UnfireSlipEvent`, `LoadState`; events `OnFlagSet`, `OnFlagChanged(flag, isSet)`, and the slip-event notification). *[Author note: Section 8.1.1 previously named the slip-event notification `OnSlipEventFired`, while 8.1.7 named it `OnEventFired`; confirm against the code.]* |
| `EvidenceStateManager` | Acquired, unlocked, and seen evidence (`AcquireEvidence`) |
| `EvidenceFlagBridge` | Writes flags on evidence acquisition |
| `SlotManager` | Slot A / Slot B (`IsSameEvidence`, `GetFilledEvidenceIDs`, `OnSlotsChanged`) |
| `CombinationEvaluator` | Evaluates equipped slots against chains and interactions (`Evaluate`, `coveredByChain`, `SuppressSubsetInteractions`) |
| `LogicChainDatabase` | Chain lookup and suppression (`ApplyHierarchySuppression`, `ExtractFlagFromText`) |
| `DialogueNodeData` / `EvidenceInteractionData` / `ComputerUnlockRule` / `WorldObjectActionData` | Pair matching (`TryGetRequiredMatch`, `TryGetTriggerMatch`, `IsFlagConditionMet`, `Matches`, `IsUnlockedBy`, `GetDisplayLabel`) |
| `EvidenceIDRetriever` | Dialogue result retrieval; per-character slip-event history (`_firedSlipEvents`, `allowRepeatSlipEvent`, `RetrievalResult`) |
| `SlipEventHandler` | Executes slip-event rewards and toasts |
| `FlagNarrativeManager` | Fires `FlagNarrativeRule` beats on `OnFlagChanged` / `OnStrengthChanged` |
| `NarrativeSuppressionManager` | Applies suppression rules |
| `ChainResetListener` | Applies `ChainResetPackage` assets |
| `EndingManager` | Resolves endings (`EvaluateAndResolve`, `globalDialogueOverrides`, `ConditionsPass`) |
| `InternalClockManager` | Countdown (`HoursRemaining`, `IsRunning`, `SkipHours`) |
| `PendingEvidenceManager` | Delayed evidence (`RegisterPending`, `IsPending`, `unlockAtHoursRemaining`, `onReadySlipEvent`) |
| `CharacterKnowledgeLog` | Per-character patience and confrontation strength (`GetStrength`) |
| `PatienceCooldownHandler` | Patience lockouts, depletion counts, warnings |
| `CharacterRoomPresence`, `IRSeatManager` | Moving characters in and out of rooms; interrogation-room seating |
| `NPCApproachPlayer`, `NPCForcedConfrontation` | Miller's warnings and forced confrontations |
| `CharacterAnimationHandler` | Flag-driven posture changes |
| `FlagDrivenDoor`, `LockedRoomEntranceTrigger`, `DreamSequenceTrigger` | Flag- and slot-driven world triggers (`BothItemsEquipped`) |
| `PickupInteractable` | Pickups (`flagOnPickup`) |
| `GameStateManager` | Room state (`RoomState`) |
| `IntroSequenceController` | Opening briefing |
| `FallSequenceController`, `LockedRoomSequenceController` | Locked-room collapse and countdown (`CheckBothEquipped`) |
| `TimeAdvanceTrigger`, `TimeAdvanceController` | Rest stations and the wait panel |
| `SceneReturnHandler` | Dream return cost (`returnTimeSkipHours`) |
| `StairsDoorHandler` | Ending entry; locks saves |
| `EndingSequenceController`, `EndingOutcomeController` | Ending quotes, illustration, and credits |
| `SaveManager` | Save/load (`SaveData`, `IsSuspectPresenceFlag`, `LockSavesAfterEnding`) |
| `SFXManager` | Sound effects (`GetAvailableSource`) |
| `MusicManager` | Music (`EvaluateAndTransition`, `IsEligible`, `Pause`, `Resume`, `ResumeFresh`, `ResetSpent`) |
| `PlaytestLogger` | Playtest instrumentation (`.jsonl` event stream; `_final.json` dump with per-character `activeChainID` and `consecutiveOutOfRange`) |

#### UI components

| Component / file | Role (key members referred to in Chapter 8) |
| :--- | :--- |
| `DialogueUI` (`DialoguePanel.uxml`, `DialoguePanel.uss`) | Unified dialogue panel (`ReEvaluateQuestions`, `ApplyModeStyle`, `TryFireDeferredSlipEvent`, `ForceClose`) |
| `DragGhostHandler` | Drag-and-drop ghost card (`TryUnequipOnDragOut`) |
| `EvidenceCardFactory` | Evidence cards (`BuildCard`, `BuildSlotCard`, `OnCardDoubleClicked`) |
| `FreeRoamQuickMenuController` | Free-roam quick menu |
| `ComputerTerminalUI` (`ComputerTerminal.uxml`) | Computer terminal (`EjectTapesFromSlots`) |
| `InventoryPanelController` | Inventory and folders |
| `EvidenceFolderManager` | Folder state |
| `InspectModeController` | Inspect mode and notes |
| `ReadModeController`, `ReadModeQuickAccessInteractable` | Read mode; document folders placed in rooms |
| `ArchiveUI` | Conversation archive |
| `WorldObjectInteractor` | World-object interaction |
| `GlobalUIInputHandler`, `EvidenceHoverManager` | Hover shortcuts across panels |
| `BaseUIPanel`, `UIPanelTracker` | Modal count, escape stack, player locking (`PushModalPanel`, `openModalPanelCount`, `escapeStack`, `ClosableWithEscape`, `CheckAndResetIfStuck`; `PlayerController.SetLocked`) |
| `GlobalEscapeManager` | Escape routing (`RequestEscapeClose`, `OnEscapePressed`) |
| `PauseMenuController`, `SettingsPanelController` | Pause and settings (`ApplyTargetedUIScaling`) |
| `FreeRoamHUDController` | Clock HUD and free-roam slot strip |
| `ScreenFader` | Fade overlay |
| `RootReference.uss` | Reference palette |

#### Editor tooling

`LogicChainGraphWindow` (with `DialogueNodeView` and `EvidenceNodeView`), `LogicChainDataEditor`, `DetectiveQuestionDrawer`. Extractors: see X.10.

---

### X.3 Named Flags, Events, and Assets

#### Evidence IDs referred to in Chapter 8

| ID | Item |
| :--- | :--- |
| `E1R` | Kae's Firearm Evidence Record |
| `E2` | Fired projectile |
| `E2R` | Ballistics Examination Report |
| `E4-TRACE` | Foot Trace Analysis TR-189-04 (asset `Evidence_E4-TRACE`) |
| `E15` | Somnoryl-μ vials |
| `AI` | Auto Injector |
| `AV` | Adrenaline Vial |
| `KEYS` | Keys |
| `E3R`, `E4R`, `E9R`, `E14R`, `F1`, `L1`, `N1` | *[Author note: add item names]* |

Access tapes (tagged `"tape"`): `FL` (Forensics Laboratory), `EC`, `MU`, `CSU` *[Author note: add tape names]*.

#### Evidence-to-flag mappings (precinct scene)

| Evidence | Flag |
| :--- | :--- |
| `E1R` | `FLAG_E1R_ACQUIRED` |
| `E2R` | `FLAG_E2R_ACQUIRED` |
| `E3R` | `FLAG_E3R_ACQUIRED` |
| `E4-TRACE` | `FLAG_E4-TRACE_ACQUIRED` (mapping index `[3]`) |
| `E9R` | `FLAG_E9R_ACQUIRED` |
| `F1` | `FLAG_F1_ACQUIRED` |
| `L1` | `FLAG_L1_ACQUIRED` |
| `N1` | `FLAG_N1_ACQUIRED` |

#### Clock flags

- Start: `FLAG_INTERNAL_CLOCK_STARTS` (set after `MILLER_BRIEF_01`)
- Warning: `FLAG_TIME_WARNING` (triggers `MILLER_TIME_WARNING`)
- Expiry: `FLAG_MILLER_ANGRY_SEQUENCE`, `FLAG_CASE_NOT_READY`, `FLAG_MILLER_WARNING_DONE`, `FLAG_MILLER_WARNING_RESTORE`

#### World, presence, and animation flags

| Object / behaviour | Flag |
| :--- | :--- |
| `DoorHinge_LR` (locked room) | `FLAG_LOCKEDDOOR_OPEN` |
| `DoorHinge_IR` (interrogation room) | `FLAG_SUSPECT_IN_IR` |
| `DoorHinge_BR` (bathroom) | `FLAG_BR_DOOR_OPEN` |
| Elara / Kae in interrogation room | `FLAG_ELARA_IN_IR`, `FLAG_KAE_IN_IR` |
| Elara posture `Sitting Disbelief` | `FLAG_ELARA_GUN_REACTION` |
| Elara posture `Sitting Rubbing Arm` | `FLAG_ELARA_MOON_ADDICTION` |
| Pickup and other SFX flags | `FLAG_PICKUP_PAPER`, `FLAG_PICKUP`, `FLAG_TOILET_FLUSH`, `FLAG_KEYS_ACQUIRED` |

#### Patience warning flags

`FLAG_MILLER_ELARA_WARNING_SEQUENCE`, `FLAG_MILLER_KAE_WARNING_SEQUENCE`, `FLAG_MILLER_WARNING_SEQUENCE`; depletion cap fires `FLAG_MILLER_ANGRY_SEQUENCE`.

#### Dialogue identifiers used as examples

- `KAE_E1R` (single-item gun-ownership question); `KAE_E1R_E2R` (paired question)
- Worked trace (Section 8.1.4): `REQUEST_MILLER_E4-TRACE` → slip event `E4-TRACE_ACQUIRED` → `FLAG_E4-TRACE_ACQUIRED` → `KAE_E4-TRACE` or paired `KAE_E4-TRACE_E4R` → slip event `SHOWN_E4-TRACE_KAE` → `FLAG_ELARA_BAREFOOT_1`

#### World actions and terminal rules

| Asset | Object | Requires |
| :--- | :--- | :--- |
| `Action_IntDoor_Open` | — | Nothing |
| `Action_Greeting_Buckley` | Buckley | Nothing |
| `Action_LockedRoom_Open` | `Door_LR` | `KEYS` |
| `Action_Bathrooom_Dream` *(spelling as in project)* | `Door_BR` | `E15` + `AI` |
| `Rule_FL_E2R` | Computer terminal | `FL` + `E2` → unlocks `E2R` |

#### Narrative rules, suppression rules, and reset packages

- `FlagNarrativeRule` assets (precinct scene): `FlagNarrativeRule_E14R_ACQUIRED`, `FlagNarrativeRule_CONFESSION`, `FlagNarrativeRule_OBTANING_F1_EVENT_TIME` *(spelling as in project)*
- `NarrativeSuppressionRule` examples: `ELARA_GUN_REACTION_CONFRONTATION`, `KAE_GUN_OWNER`, `MILLER_KEYS_AVAILABLE`, `ENDING_SEQUENCE_STARTED`
- `ChainResetPackage` examples: `ChainResetPackageMillerConfrontation`, `ChainResetPackageWarningDone` (fields `triggerFlag`, `chainsToReactivate`, `flagsToClear`, `slipEventsToRestore`)

#### Ending paths and overrides

| Priority | `EndingPathData` |
| :---: | :--- |
| 100 | `01_ENDING_KAE_MURDER_ELARA_FREE` |
| 95 | `02_ENDING_KAE_MURDER_ELARA_ACCOMPLICE` |
| 90 | `03_ENDING_ELARA_MURDER_KAE_ACCOMPLICE` |
| 85 | `04_ENDING_ELARA_MURDER_KAE_GUN_ONLY` |

Each path holds a `FlagGroup` of `FlagCondition` predicates and three `NarrativeDialogueData` references: `elaraReactionDialogue`, `kaeReactionDialogue`, `outcomeNarrative`.

Global overrides (`EndingDialogueOverrideData`, fields `elaraReactionOverride`, `kaeReactionOverride`, `outcomeOverride`): `KAE_REACTION_ELARA_SHOOTER_KAE_PRESSURED`, `KAE_REACTION_KAE_SHOOTER_ROBBERY_CONVICTION`.

Drafted but unwired robbery-conviction assets: `KAE_REACTION_ENDING_KAE_MURDER_ROBBERY_CONVICTION`, `OUTCOME_ENDING_KAE_MURDER_ROBBERY_CONVICTION`, `SLIP_STEP2_VERDICT_KAE_MOTIVE_ROBBERY_CONVICTION`.

---

### X.4 Two-Slot Examples with Identifiers

| Slot A | Slot B | Active System Context | What Surfaces |
| :--- | :--- | :--- | :--- |
| `—` | `—` | Dialogue (`DialogueUI`) | No evidence-triggered options; only bookmarked chain resume options (if any) or the empty-slot prompt. |
| `—` | `—` | World Objects (`WorldObjectInteractor`) | Only zero-requirement actions unlock (e.g., `Action_IntDoor_Open`, `Action_Greeting_Buckley`). |
| `E1R` | `—` | Dialogue with Kae | Single-item prompt (`KAE_E1R`) or single-trigger chain node. |
| `E1R` | `E2R` | Dialogue with Kae | Pairwise synthesis (`KAE_E1R_E2R`); hierarchy suppression hides the standalone `E1R` and `E2R` options. |
| `FL` | `E2` | Computer Terminal (`ComputerTerminalUI`) | Matches `Rule_FL_E2R` (evaluated by `ComputerUnlockDatabase.Evaluate`), unlocking `E2R` via `EvidenceStateManager`. |
| `E15` | `AI` | Bathroom Door / Dream Trigger | Unlocks `Action_Bathrooom_Dream` on `Door_BR` and enables `DreamSequenceTrigger`. |
| `AI` | `AV` | Locked-Room Countdown | Satisfies `LockedRoomSequenceController.CheckBothEquipped()`, enabling injection with `[E]`. |

---

### X.5 Tuning Values

| System | Parameter | Value |
| :--- | :--- | :--- |
| Internal clock | `totalHours` | 24 (code default 36) |
| | `warningAtHoursRemaining` | 12 (code default 18) |
| | Rate | `Time.deltaTime / 3600` (1 in-game hour = 1 real hour) |
| | HUD wall-clock start | 3:30 PM |
| Wait panel | Range | 1–24h, whole hours |
| | Screen fade | 1.6 s out / 1.6 s in |
| Dream | `returnTimeSkipHours` | 6h |
| Locked room | `countdownDuration` | 25 s (bar pulses below 10 s) |
| Patience drain — Elara, Kae | Inquiry misstep / confrontation misstep | 0.125 / 0.25 |
| Patience drain — Miller | Misstep | 0.5 |
| Patience cooldown | Elara, Kae / Miller | 2h / 3h (in-game) |
| Escalation | `depletionsBeforeWarning` | 2 |
| | Depletion cap | 3 (Miller, Elara); 4 (Kae) |
| Inspect mode | Note length | 288 characters |
| Read mode | Zoom | 0.5×–4× (`Ctrl+Scroll`); double-click toggles 2× |
| Folders | Maximum | 6 |
| UI tracker | Stuck-modal reset | 3 s of active, unpaused play |
| SFX | `poolSize` | 8 |
| | `priorityStealThreshold` | 0 |
| Music | Evaluation interval | 0.5 s (unscaled time) |
| | Cross-fade | 2 s out / 2 s in |
| | Queue limit | 8 |
| | `CUE_ROUND_MIDNIGHT` window | below 15h remaining |

---

### X.6 Audio Content

#### Sound-effect rules (`SFXDatabase`)

| Entry | Trigger flags | Variants |
| --- | --- | --- |
| Opening Doors | `FLAG_LOCKEDDOOR_OPEN`, `FLAG_SUSPECT_IN_IR`, `FLAG_BR_DOOR_OPEN` | 4 |
| Pick Up Paper | `FLAG_PICKUP_PAPER` | 1 |
| Pick Up | `FLAG_PICKUP` | 1 |
| Toilet Flush | `FLAG_TOILET_FLUSH` | 1 |
| Keys | `FLAG_KEYS_ACQUIRED` | 1 |

Universal slip-event variants (`universalSlipEventVariants`): 3. Rule fields: label, trigger flags, variants, `avoidImmediateRepeat`. `SFXDefinition` fields: clip, volume, base pitch, pitch variance, loop, priority.

#### Music cues (`MusicCueDatabase`)

`MusicCueData` fields: ID, clip, priority, `activeWhenHoursRemainingBelow`, `requireClockRunning`, `requiredFlags`, `blockedByFlags`, `loop`, `volume`, `forcePlay`.

27 cues: 14 `forcePlay`, 13 not; all `loop` off; all `requireClockRunning`; all keyed on one required flag except `CUE_ROUND_MIDNIGHT` (time-based, priority 30, not forced); no cue uses `blockedByFlags`.

| Priority | Role (examples) |
| --- | --- |
| 0–6 | Evidence and deduction stings (`CUE_E4-TRACE_ACQUIRED`, `CUE_KAE_FALSE_ALIBI`, `CUE_N1_ACQUIRED`, `CUE_INTERNAL_CLOCK_STARTS`) |
| 15–16 | Character beats (`CUE_KAE_CONFESSION`, `CUE_ELARA_SLEEPWALKING`, `CUE_MILLER_ANGRY_SEQUENCE`) |
| 20–27 | Altered-state and sequence cues (`CUE_LOCKED_ROOM_SEQUENCE_STARTED`, `CUE_AV_USED`, `CUE_MOON_USED`, `CUE_DREAM_EXPERIENCED`) |
| 30–40 | Time pressure (`CUE_ROUND_MIDNIGHT`, `CUE_TIME_WARNING` — priority 40, forced) |
| 50 | Outcomes (the five `CUE_ENDING_*` cues, `CUE_MILLER_PLAYER_FIRED`) |

---

### X.7 UI Sorting Order and Escape Handling (`GeometryAttempt`)

| Sorting Order | UI Document(s) | Escape Behaviour |
| :---: | :--- | :--- |
| **3** | `FreeRoamUI` (`FreeRoamHUD`) | Non-modal HUD; hidden when modals open |
| **5** | `DialogueUI`, `ComputerTerminalUI` | `ComputerTerminalUI` closes on `Tab`/`Esc`; `DialogueUI` opts out of `Esc` so interrogations cannot be accidentally aborted |
| **7** | `ArchiveUI`, `TimeAdvanceUI` | `TimeAdvanceUI` closes via `BaseUIPanel`; `ArchiveUI` toggles with `[L]` (and closes via `Esc`) |
| **10** | `InvetoryUI` *(spelling as in project)*, `PauseMenu` | `InventoryPanelController` cancels open rename/delete prompts before closing; `PauseMenu` opens only when the stack is empty |
| **20** | `InspectModeUI`, `SettingsPanel` | `InspectModeController` discards an active note edit on `Esc` before closing; `SettingsPanel` returns to caller |
| **30** | `ReadModeUI` | Closes cleanly via `BaseUIPanel` |
| **98** | `ScreenFader` | Non-blocking fade overlay (`picking-mode: ignore`) |
| **99** | `SaveIndicatorUI` | Always-on-top saving/loading status pill |

---

### X.8 Key Bindings

*[Author note: bindings are scene-configured; confirm against the final scene values before submission.]*

| Context | Key | Action |
| :--- | :--- | :--- |
| Dialogue | `[Q]` | Switch Inquiry / Confrontation |
| Free roam | `[H]` | Cycle free-roam quick menu |
| | `[I]` | Open inventory |
| | `[L]` | Open / close archive |
| | `[TAB]` | Shown on HUD badge *[Author note: confirm action]* |
| | `[E]` | Interact (proximity prompts; locked-room injection) |
| Inventory | `[N]` / `[T]` / `[L]` | New / rename / delete folder |
| | `[Q]` / `[E]` | Cycle folders |
| | `[W]` | Toggle Slots View / Folder Contents View |
| | `[F]` / `[R]` | Inspect / Read hovered card |
| | `[A]` / `[S]` | Equip to Slot A / Slot B |
| | `[X]` | Remove |
| Inspect mode | `[F]` or double-click | Open |
| | `[W]`, `[A]`, `[S]` | Quick-equip buttons |
| | `[N]` / `[Enter]` | Edit / save note |
| | `[R]` | Open read mode |
| Read mode | `Ctrl+Scroll` | Zoom |
| | Double-click | Toggle 2× |
| | `[V]` | Reset view |
| Terminal | `Tab` / `Esc` | Close |
| Global | `Esc` | Close topmost panel, or open pause menu |
| Debug | `[F1]` | `PrototypeDiagnostic`, `DebugEvidenceGranter` |
| | `[F2]` | `DevToolsPanel` |
| | `[F3]` | `RuntimeDebugConsole` |
| | `[F5]`–`[F8]` | `DebugTimeSkip` |
| | `[F10]` | `PlaytestLogger` final dump |
| | `[F11]` | Second `DebugEvidenceGranter` |

---

### X.9 Visual Specification

#### Dialogue panel layout

| Element | Value |
| :--- | :--- |
| `slots-sidebar` | 160px wide |
| `main-content` | 726px wide, anchored bottom-centre |
| Collapsed `main-content` | 353px high; `conversation-stream` capped at 183px, no scrollbar |
| Expanded `main-content` | 573px high |
| Clock HUD | 217px wide, `rgba(14, 12, 9, 0.88)` |

#### Mode and button colours

| Element | Inquiry | Confrontation |
| :--- | :--- | :--- |
| Mode badge | `#36689b` | `#904c77` |
| Occupied slot border | `#37699e` | `#904c77` |
| Detective speech accent | `#101820` | `#191020` |
| Character speech | `#af8041` | `#af8041` |

| Button class | Styling |
| :--- | :--- |
| `.question-btn--chain`, `.question-btn--standalone` | Active mode accent |
| `.question-btn--resume` | `#d4a94e` border on `#2a2416` |
| `.question-btn--action` | `#8a8880` border |
| `.question-btn--locked` | 52% opacity, `rgba(255, 80, 80, 0.35)` edge |

#### Evidence status styling

| Class | Styling |
| :--- | :--- |
| `.evidence-card--new` | Border `rgba(200, 175, 100, 0.90)`; HUD icon `InventoryNewSprite` |
| `.evidence-card--pending` | 45% opacity, dark overlay, `⏳` and `Xh Xm` timer |
| `.badge-warning` / `.out-of-range-badge` | Out-of-range marker |
| `.badge-success` / `.slip-badge` | Slip-event marker |

#### Palette (`RootReference.uss`)

| Role | Values |
| :--- | :--- |
| Menu / HUD surfaces | `#0E0C0A` to `#302C20` |
| Investigative panel surfaces | `#202020`, `#1B1B19`, `#111110` |
| Headings | `#DCC89B` |
| Body text | `#B9AA87`, `#E8E6DF` |
| Detective / Inquiry | `#4778af`, `#37699e` |
| Characters (witnesses, suspects, Miller) | `#af8041`, `#946a34` |
| Confrontation | `#904c77` |
| Warnings, pending, unseen | `#c88c3c`, `rgba(200, 175, 100, 0.90)` |
| Computer access tapes | `rgba(80, 190, 230, 0.55)` |

Palette values are inlined across twelve panel `.uss` files.

#### Typography and cursors

| Use | Value |
| :--- | :--- |
| Terminal | `AnonymousPro-Regular.ttf`, 10–12px |
| Header letter-spacing | 1–4px |
| Micro-badges | 8–11px |
| Body text | 12–16px |
| Display titles | 26–52px |
| Key badges | `.key-badge`, 2px bottom border |
| Cursors | `Click.png`, `Grab.png` |

#### UI scaling

`ScalePanelSettings` is shared by `ArchiveUI`, `DialogueUI`, `FreeRoamUI`, and `ComputerTerminalUI`, rescaled by `SettingsPanelController.ApplyTargetedUIScaling()`. `InventoryPanel`, `InspectMode`, and `ReadMode` use fixed `PanelSettings`; the `Scalable UI Documents` list in `MainMenu` is empty.

#### UXML element names referred to in Section 8.2

`quick-menu`, `qm-grid`, `qm-tab-starter`, `qm-tab-inventory`, `slot-drop-A`, `slot-drop-B`, `drag-ghost`, `.slot-drag-over`, `.mode-confrontation`, `tapes-grid`, `.tape-card`, `evidence-grid`, `variant-slots`, `variant-folder`, `.shortcut-item--dimmed`, `note-container` (`NoteTexture`), `.equip-btn--active`, `read-edge-left`, `read-edge-right`, `slot-badges-bar`, `entry-evidence-chip`, `.hidden`, `clock-bar-fill`, `fr-slot-A`, `fr-slot-B`, `.time-error`.

---

### X.10 Debug and Verification Tooling

| Tool | Purpose |
| :--- | :--- |
| `GameFlags` | Centralized constants for core runtime flags |
| `GameBootstrapValidator` | Verifies required managers on scene load |
| `PrototypeDiagnostic` (`[F1]`) | Tests equipped slots against `LogicChainDatabase` and `EvidenceInteractionDatabase` |
| `RuntimeDebugConsole` (`[F3]`) | Runtime console |
| `DevToolsPanel` (`[F2]`) | Developer panel |
| `DebugTimeSkip` (`[F5]`–`[F8]`) | Clock skips |
| `DebugEvidenceGranter` (`[F1]`/`[F11]`) | Grants evidence |
| `ControlStateDebugger` | Control-state inspection |
| `PlaytestLogger` (`[F10]`) | Playtest event log and final dump |

Editor extractors (`Assets/Editor/Extractors/`): `SceneContextExporter`, `DialogueExtractor`, `EvidenceInteractionExtractor`, `SlipEventExtractor`, `SuppressionRuleExtractor`, `NarrativeFlagRuleExtractor`, `WorldObjectExtractor`.
