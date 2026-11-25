### X.11 Visual Environments Reference (Section 8.3)

*[Author note: add this section to the Implementation Reference appendix.]*

#### Scenes and room roots

| Room / scene | Object or scene name |
| :--- | :--- |
| Main menu | `MainMenu` (`MainMenuController`, `VideoPlayer`; inactive `MainMenuTheme`, `RainLoop`) |
| Precinct | `GeometryAttempt` |
| Evidence Room | `RoomGroup_ER` |
| Corridor | `RoomGroup_CR` |
| Observation Room | `RoomGroup_OR` |
| Interrogation Room | `RoomGroup_IR` |
| Bathroom | `RoomGroup_BR` |
| Locked Room | `RoomGroup_LR` |
| Dream | `Dream_Sequence` |
| Ending / jail cells | `Ending_Sequence` |

Doors: `Door_ER`, `Door_OR`, `Door_02_OR`, `Door_IR`, `Door_BR`, `Door_LR`, `Door_STAIRS` (`WorldObject_Stairs_Door`, `StairsDoorHandler`).

#### Room contents and gates

| Room | Objects | Gate |
| :--- | :--- | :--- |
| Evidence Room | Terminal `Desk_Computer_ER` (`ComputerTerminalUI`); tape container (`FL`, `MU`, `EC`, `CSU`); evidence box `storage_box_TOP` (`E1`, `E2`, `E3`, `E15`, `E13`, `E17`); wait chair `chair_ER_00` (`TimeAdvanceTrigger`); read-mode folder `THIS`; rain audio `Sounds_ER` | Open |
| Corridor | `Door_STAIRS` | Stairs: `FLAG_ENDING_SEQUENCE_STARTED` |
| Observation Room | `MillerRoot`, `BuckleyRoot` (`WorldObject_Buckley`); wait printer `printer_OR` (`TimeAdvanceTrigger`); folder `documentsfolder_OR (1)` | Open |
| Interrogation Room | `DoorHinge_IR` (`FlagDrivenDoor`); `IRSeatManager`, `CharacterRoomPresence`, `NPCSeatedBehaviour`; folder `documentsfolder_IR (1)` | `FLAG_SUSPECT_IN_IR` (via `FLAG_ELARA_IN_IR` / `FLAG_KAE_IN_IR`) |
| Bathroom | `DoorHinge_BR`; `WorldObject_Toilet`; actions `Action_Bathrooom_KEYS`, `Action_Bathrooom_Dream` *(spelling as in project)* | `FLAG_BR_DOOR_OPEN` (`KEYS`, or `E15` + `AI`) |
| Locked Room | `DoorHinge_LR`; `storage_box_BOT_02` (25 records); `CASE-19` (`storage_box_TOP_3`), `CASE-47` (`documentsfolder_LR`); `AmbientDust`; entry trigger `Door_Trigger_LR_SEQUENCE` → `LockedRoomEntranceTrigger`, `FallSequenceController`, `LockedRoomSequenceController`; optional action `Action_Locked_Room_LDN` | `FLAG_LOCKEDDOOR_OPEN` (`KEYS`) |

Dream return (`SceneReturnHandler`, `DreamSessionData.ReturnRoom`): Bathroom sets `BATHROOM_DREAM_EXPERIENCED`; any other room sets `FLAG_MILLER_ANGRY_SEQUENCE`.

#### Doors, outlines and visibility

| Item | Value |
| :--- | :--- |
| Door components | `WorldObjectInteractor`, `WorldObjectActionData`, `FlagDrivenDoor` (listens to `NarrativeStateManager.OnFlagSet`) |
| Door open angle / time | −90° (LR, IR); 0.5 s |
| Outline | `InteractableProximityOutline` (switches to outline layer); disabled after the door opens or `disableWhenExhausted` + `disableFlag` |
| Room visibility | `GameStateManager`, `RoomRootRegistrar`, `RoomTrigger` (`TransitionToRoom`, `coVisibleRooms`, `objectsToHide`), `HandleRoomChanged` |
| Co-visible rooms | IR → OR; BR → CR; LR → ER |
| Dark covers | `FOW` group in each room |

#### Lighting and atmosphere

| Item | Value |
| :--- | :--- |
| Local light groups | `Lights_ER` 3, `Lights_CR` 4, `Lights_OR` 3, `Lights_IR` 2, `Lights_BR` 2, `Lights_LR` 3 |
| Directional light | None in `GeometryAttempt` |
| Lightmapping profile | `CreateOmenLightingAsset`: GPU lightmapper, 64 / 128 / 64 direct / indirect / environment samples, 1024 max lightmap resolution, OpenImage denoiser |
| Blob shadows | `CharacterShadowController` → `BlobShadow_*`, ray onto `groundMask` |
| Dust | `AtmosphericDustController`: 220.9 normal, 710.5 disturbed density |
| Darkened walls | `WallsDark` (9 objects, precinct); `DarkenedWalls` (5 objects, ending) |
| Ending scene | `JailWall` ×2, `Door_Elara`, `Door_Kae`, `DarkRoof_OR`, `Light_CR` ×5, `Audio_Source_Ambience`, `Audio_Source_Crying_SFX`, inactive `Elara_Crying` / `Kaelen_Seated`, `NavySuitChar_Mixamo (1)` |
| Dream scene | `Floor_02_DS`, `Wall_00_DS`–`Wall_03_DS`, one `Point Light`, one `Light Probe Group`, `Audio_Source_Ambience`; mannequins `Alpha_Joints` / `Alpha_Surface`, `Beta_Joints` / `Beta_Surface` |
| Footstep volume | 0.2 (dream) vs 0.05 (precinct) |

#### Camera

| Item | Value |
| :--- | :--- |
| Component | `IsometricCamera`; movement remap `PlayerController.RemapToCameraSpace` |
| Position offset | (−20, 20, 0), with `lookAtOffset` |
| Dead zone / smoothing | 2 × 1.5 units; 0.25 s |
| Zoom range | 2.5 (`zoomedInSize`) to 5 (`zoomedOutSize`; scene override of the code default 9) |
| Zoom suppressed when | `UIPanelTracker.IsAnyUIPanelOpen` or player locked |
| Interaction framing | `ZoomInForInteraction`: 15 % shift toward `_interactionFocus`; 65 % of default size (≈ 3.25); never zooms out (`Mathf.Min(_preInteractionSize, wanted)`) |
