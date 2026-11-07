System Architecture

# Interaction System

## Interacting Character

### Considers Patience Level

### Has any evidence equipped ?

#### Two Slot System

### Option: Leave Conversation

## Interacting Computer System

### Has only one slot equipped ?

#### Is it a Tape ?

##### Return "Equip an Evidence to Begin Search"

#### Return "Equip a Tape to Begin Search"

### Has both slots equipped ?

#### Two Slot System

### Option: Leave Computer

# Two Slot System

## Slot Manager

### Equip Evidence to Slot A

### Equip Evidence to Slot B

### Clear Slots

### Send Input

## Inquiry

### Combination Evaluator

#### Is Slot A filled? (bool)

#### Is Slot B filled? (bool)

#### Check Previous Dialogue Inputs (Current Dialogue)

##### Display array of Inquiry dialogue options based on Evidence Slot Input

###### Determine Evaluation Mode

## Confrontation

### Combination Evaluator

#### Is Slot A filled? (bool)

#### Is Slot B filled? (bool)

#### Check Previous Dialogue Inquiries (Current Dialogue)

##### Display array of Confrontation dialogue options based on Evidence Slot Input

###### Determine Evaluation Mode

## Evaluation mode

### Single Evidence Mode (only one slot filled)

#### Determine Evidence Strenghth

#### Retrieve Evidence ID

### Paired Combination Mode (both slots filled)

#### Interacting With Computer ?

##### Retrieve Evidence ID (Computer)

#### Determine Evidence Strenghth

#### Retrieve Evidence ID

### No Evidence (No Slots Filled)

#### Return empty list

#### Return message "You need to equip Evidence in one of the slots in order to interact"

## Retrieve Evidence ID (Dialogue)

### Within Logic Range?

#### Check Character Knowledge Log

##### If first time

###### Return Evidence base response

##### If repeat

 (see:If repeat)

###### Return variation response

#### Currently in Logic Chain?

##### Confrontation?

###### Strenght ≥ threshold ?

* Check for Slip Trigger
  
  + If Slip
    
    - Fire Slip Event
    
    - Update Narrative State

##### Increase Argument Strength

### Outside Logic Range?

#### Return Diminished Response

#### Reduce Character Patience

#### Confrontation?

##### If yes

###### Break Logic Chain

##### Previous Response within a Logic Chain?

###### Second time failing ?

* Break Logic Chain

## Retrieve Evidence ID (Computer)

### Within Logic Range?

#### Check Computer Log

##### More Than One Evidence?

###### Return Evidence Item

##### If first time

###### Return Evidence Item

##### If repeat

###### Return "Already Requested"

### Outside Logic Range?

#### Contains one Tape?

##### Return "Not found in current tape database, try another" response

#### Return "Please provide a Tape and Evidence"

# Inventory System

## Evidence ScriptableObject

### ID (e.g. "E5", "X2")

### Display Name

### Unlock Condition (null if always available)

### Combination Tags (list of thematic keywords for logic range)

### Description Text

### Number Pages

## Evidence State Manager

### Acquired Evidence List

### Locked/Unlocked Evidence

### Available from start

# Evidence Inspection

## View Mode

### Zoom in / out

### Pan (move the view)

### Flip / Next Page

### Close

## Player Notes ?

# Narrative Manager

## New Inquiries & Confrontation Dialogue from Unlocked Evidence or Dialogue

## Endings

### Built a Case Endings

#### Kae Arrested

##### Committed the murder

##### Accomplice

#### Elara Arrested

##### Committed the murder

##### Accomplice

#### Elara Free

### Other Endings

#### Getting Fired

##### Uncomplete Case

###### Threatening with Gun

###### Running out of time

###### Injecting Moon Drug

##### Getting a Second Warning from the Captain

#### Dying

##### Injecting Adrenaline for no reason

##### Not Injecting Adrenaline when exploring the Old Evidence Locked Room

## Dream Sequence

## Final Confrontation with the Captain

---

Core Mechanics

# Two Slot System

## Dialogue System

### Inquiry

#### First Time Asking?

#### Map out Detective Questions

#### Base Responses

##### Elara

##### Kaelen

### Confrontation

#### Within Logic Range?

##### Calculate Argument Strength

#### Map out Slips

#### Base Responses

### Leave Conversation (Option)

#### Give Character Reaction Detail Responses

### Logic Range

#### Theories

##### Elara Guilty

##### Kae Guilty

##### Both

##### Another Person

#### Evidence Combination

##### Write Scripted questions for solid combinations?

##### System for aligning questions

### Character Exhaustion

### Read Input

## Computer Interaction

### Equip Tape (Only in Computer)

### Read Input

### Limit to Tape+Slot

## Inventory System

### Equip to Slot

### Organization?

### Mind Map?

## Track acquired Evidence

### Save Progress ?

### Already acquired?

# Evidence Interaction

## View Evidence

## Zoom Controls

## Move Controls

## Flip/Next

## Close

## Notes?

## Brief?

## Tabs?

## Shortcuts?

# Narrative Bits

## Endings

### Built Case

#### Kae Arrested

#### Elara Arrested

#### Kae Arrested (few years only)

#### Elara Free

### Other

#### Getting Fired

#### Shooting Someone?

#### Dying

## Dream Sequence

## Captain Final Confrontation

### Injected

### Threatened Suspects

### Ready to Convict

---

Visuals

# Models

## Elara

## Captain

## Kae

## Player Character

## Buckley

# Environment

## Interrogation Room

## Observation Room

## Evidence Room

### Moldy Old Records Room

## Corridor

## Dream

# UI

## Dialogue Interactions

## Computer Interaction

## Menu

## Inventory Interaction

## Two Slot HUD

## Time Display

# Animations

## Movement

### Follow Player

### Show/Hide Wall

### Camera

#### Zoom in for Interactions

## Character Animations

### Buckley Idle

### Elara

#### Idle

##### Crying

#### Looks at Player?

#### Reactions

### Captain

#### Idle

##### Angry

#### Looks at Player?

### Kae

#### Idle

##### Anxious

#### Looks at Player?

#### Reactions

### Player Character

#### Idle

#### Walk

#### Turn w Mouse

#### Stop

#### Lean over Table

#### Inject

#### Threaten With Gun

#### Reactions

---

Game Starts

# Intro Dialogue Scene

(Evidence Room)

## Captain Welcomes the Detective to the case

- Establishes that there are suspects
- Establishes that the previous detective quit on the case (out of nowhere)
- Establishes that the player needs to interact with the captain in order to bring the suspects in the room
- Establishes that the player can go to him if they need something
- Gives the player the Case folder to start investigating

### Interact with Captain Miller

(Observation Room)

#### V1-

- Obtain E14 using E21 / E8 / E10
- Obtain Note "Who is this Detective Thorne?" using "I'd rather be anywhere but here" Note
- Ask him about Evidence from Initial Case Folder
- Ask to bring Elara to Interrogation Room
- Ask to bring Kae to Interrogation Room

Read Files that come with the Case Folder

#### Memo

Arrest Report Kae
Arrest Report Elara
E21
E10
E18
E1
E2
E3
E15
E22
E13
E17
Incident Report
Portrait Elara
Portrait Kae
Portrait Arthur
"I'd rather be anywhere but here" Note

##### [Interact with E17]

###### Cards inside wallet

##### [Interact with E13]

###### Comment from the detective "It appear to be full, maybe I should gather more evidence on what this is]

##### [Interact with E13]

###### Comment from the detective "It's not loaded, but it's still a gun"

##### [Interact with E3]

###### Comment from the detective "It smell awful, did they bag this for evidence while still wet !?"

##### [Interact with E2]

###### Comment from the detective "Why is this used bullet here, along with the other evidence ?"

##### [Interact with E15]

###### Comment from the detective "Two vials, one appears to be emptier than the other, maybe I should gather more information about this"

##### [Interact with "I'd rather be anywhere but here" Note]

###### "Comment from the detective "Why was this note here ? Maybe the previous detective left it here"

Interact with Buckley

(Observation Room)

#### V1-

Response “Good Mourning Detective, and Welcome to the Precinct”

#### V2-

Response "Anything that you need you can address with the Captain"

Interact with Door

(Evidence Room)

#### V1-

Response (description of the door) “Very dusty window, you can see the dust particles making it hard to see anything inside clearly”

##### Options:

1. Open the Door
2. Leave

###### 1. Open the Door:

- Gives a response saying: “The door is locked shut, and needs a key for access”
- Gets the player a note saying “Ask for door access”

###### (Unlocks new possible dialogue)

* Interact with Captain Miller
  (Observation Room)
  
  + V2-
- Obtain Evidence Room Door Key  using "Who is this Detective Thorne?" Note + "Ask for door access" Note
  
  + Interact with Door (Evidence Room)
    
    - 1. Open the Door:

- Gives a response saying: “The door is locked shut, and needs a key for access”

- Player equips Evidence Room Key
  2- Leave
  
  - [The mold starts attacking his throat, the player hears detective's Heartbeat]
    
    * 1- Leave back to Evidence Room
    
    * 2- [Interacts with the detective] Auto Injector + Adrenaline
      
      + [Interact with box saying "Case-19-76-23"
      
      + [Interact with box saying "Case-47-85-04"
    
    * 3- [Investigate]
      
      + [Interact with box saying "Case-19-76-23"
        
        - Ending Gets Killed - [Falls to the ground, sound of heart beat, then it stop, screen becomes blurry and transitions to darkness] detective then comments "Now I just have to wait in peace"
      
      + [Interact with box saying "Case-47-85-04"
        
        - Ending Gets Killed - [Falls to the ground, sound of heart beat, then it stop, screen becomes blurry and transitions to darkness] detective then comments "Now I just have to wait in peace"

### Interact with Police Computer

(Evidence Room)

#### Forensics Laboratory Tape:

E2R = E2+FL
E3R = E3+FL
E21R = E21+FL

#### Medical Unit Tape:

E4 = PE+MU || ARE+MU
E4-C = E4+MU
E12 = PK+MU || ARK+MU
E16 = PA+MU
E7 = E16+ MU

#### Controlled Substances Unit Tape

E15R = E15+CSU
X2 = E15R+CSU
N1 = X2+CSU
E13R = E13+CSU
X4 = E13R+CSU
E5 = PE+CSU || ARE+CSU
E6 = PK+CSU || ARK+CSU

#### Evidence & Custody Tape

E9 = E22+EC
E1R = E1+EC
E18R = E18+EC
E19 = PK+EC
E17R = E17+EC
E10R = E10+EC
GC-AL-01 = E10R+EC
E11 = ARK+EC
E23 = PE+EC || ARE+EC
E22 = PA+EC
E3R = E3+EC

### [Player gathers more information about the case]

#### Interact with Captain Miller

(Observation Room)

##### V2-

- E14 using E21 / E8 / E10
- E7 using E16 / E10 + E5 / E6
- N1 using E5/E6 + E15/X2
- E4-Trace (Request Only) using E21+E4 || E4+E7 || E4+E4C
- Ask to bring Suspects
- Make Conviction

###### Make Conviction against Elara

* Convicting Elara (Requires Solid Case)
  
  + Captain Requests E4-Trace
    
    - [Wait for E4-Trace]
      
      * Ending: Convicting Elara (Requires Solid Case)

* Response from Captain: "Gather more evidence and stop wasting my time"

* [Player makes a solid case against Elara]
  
  + Response from Captain: "I'll look into this theory of yours maybe there's a file still waiting to be processed, you can wait for it, or continue on with your investigation

###### Make Conviction against Kae

* Response from Captain: "Gather more evidence and stop wasting my time"

* Ending: Convicting Kae (Requires Solid Case)
  
  + L1 Marco's Statement (Request Only)
    
    - [Wait for Evidence]
      
      * L1
        
        + Confront Kae
        
        + Confront/Inquiry Captain with L1
          
          - F1
  
  Ending: Convicting Kae
  
      * F1
      
        + Ending: Convicting Kae

###### [Wait for E4-Trace]

* Ending: Convicting Elara (Requires Solid Case)

#### Interact with Interrogation Room Door

(Corridor)

##### V1- Response from Detective "I need to Ask the Captain to Bring a Suspect In, it would be weird if they saw me exploring an empty room"

##### Interrogation with Kae

###### Ask Kae about Evidence

###### Confront Kae with Evidence

###### Leave Interrogation Room

##### [Outcomes]

###### Pressure Kae with Elara

* Confession Tape

* L1 Marco's Statement (Request Only)

###### Pressure Kae with a Good Case

* F1 Crime Report in Area (Request Only)

* Confession Tape

###### Confront with Gun a bullet shot

###### Confront how he gets the money

###### Interact using Gun

* Confronts using evidence against Elara
  
  + Slip where he only saw her sleepwalk with the gun, but that she is incapable of killing that man and that he feels so guilty and begs the player to convict him instead and leave her alone, since he's the one guilty for having the gun in the first place

* V1- Response from Captain "What hell are you thinking, you better have a good reason for doing this!"
  
  + Make Conviction
    
    - Ending Gets Fired - [The detective walks away] and comments "Maybe getting fired isn't the worst thing, maybe becoming a private detective might be the best for me, since I don't have to follow these unforgiving state institutions"
    
    - Presents a good case..

##### [Wait for Evidence]

###### L1

* Confront Kae

* Confront/Inquiry Captain with L1
  
  + F1
    
    - Ending: Convicting Kae

###### F1

* Ending: Convicting Kae

##### Interrogation with Elara

###### Ask Elara about Evidence

###### Confront Elara with Evidence

Leave Interrogation Room

##### [Outcomes]

###### Elara's Drug Experience

* Challenges the detective to try the moon drug

###### Elara's Reaction to Kae

###### Elara's Reaction to Kae's Confession

###### Confirming work schedule

###### Interact using E1 (Gun)

* Confront Elara
  
  + Response: "Why are you doing this !?"
    
    - V1- Response from Captain "What hell are you thinking, get the fuck out of my sigh and never come here ever again"
      
      * Ending Gets Fired - [The detective walks away] and comments "Maybe getting fired isn't the worst thing, maybe becoming a private detective might be the best for me, since I don't have to follow these unforgiving state institutions"

#### [Interacts with the detective] Auto Injector + Moon Drug

##### V1- "I better be sure I want to try this, because it might get me fired"

##### V2- [Interacts with the detective] Auto Injector + Moon Drug = Dream Narrative Bit

###### [Skips to Ending Confrontation with Captain]

* Ending Gets Fired - [The detective walks away] and comments "Maybe getting fired isn't the worst thing, maybe becoming a private detective might be the best for me, since I don't have to follow these unforgiving state institutions"

#### Interact using E1 (Gun)

##### Confront Kae

###### Response: "Why are you doing this !?"

* V1- Response from Captain "What hell are you thinking, you better have a good reason for doing this!"
  
  + Make Conviction
    
    - Ending Gets Fired - [The detective walks away] and comments "Maybe getting fired isn't the worst thing, maybe becoming a private detective might be the best for me, since I don't have to follow these unforgiving state institutions"
    
    - Presents a good case..

##### Confront Elara

###### Response: "Why are you doing this !?"

* V1- Response from Captain "What hell are you thinking, you better have a good reason for doing this!"
  
  + Make Conviction
    
    - Ending Gets Fired - [The detective walks away] and comments "Maybe getting fired isn't the worst thing, maybe becoming a private detective might be the best for me, since I don't have to follow these unforgiving state institutions"
    
    - Presents a good case..

### Interact with Interrogation Room Door

(Corridor)

#### V1- Response from Detective "I need to Ask the Captain to Bring a Suspect In, it would be weird if they saw me exploring an empty room"

#### Interrogation with Kae

##### Ask Kae about Evidence from Initial Case Folder

##### Confront Kae with Evidence from Initial Case Folder

##### Leave Interrogation Room

#### Interrogation with Elara

##### Ask Elara about Evidence from Initial Case Folder

##### Confront Elara with Evidence from Initial Case Folder

Leave Interrogation Room

#### Interact using E1 (Gun)

##### Confront Kae

###### Response: "Why are you doing this !?"

* V1- Response from Captain "What hell are you thinking, get the fuck out of my sigh and never come here ever again"
  
  + Ending Gets Fired - [The detective walks away] and comments "Maybe getting fired isn't the worst thing, maybe becoming a private detective might be the best for me, since I don't have to follow these unforgiving state institutions"

##### Confront Elara

###### Response: "Why are you doing this !?"

* V1- Response from Captain "What hell are you thinking, get the fuck out of my sigh and never come here ever again"
  
  + Ending Gets Fired - [The detective walks away] and comments "Maybe getting fired isn't the worst thing, maybe becoming a private detective might be the best for me, since I don't have to follow these unforgiving state institutions"

### [Interacts with the detective] Auto Injector + Moon Drug

#### V1- "I better be sure I want to try this, because it might get me fired"

#### V2- [Interacts with the detective] Auto Injector + Moon Drug = Dream Narrative Bit

##### V1- Response from Captain "What hell are you thinking, get the fuck out of my sigh and never come here ever again"

###### Ending Gets Fired - [The detective walks away] and comments "Maybe getting fired isn't the worst thing, maybe becoming a private detective might be the best for me, since I don't have to follow these unforgiving state institutions"

### Interact with Window

(Evidence Room)

#### V1- [You see a crowd demanding that a judge quits for letting a man get out] Gets a comment from the Detective "It seems that this city is only made for those that create the questions, not the ones that demand for answers"

### Interact with Bathroom Door

(Corridor)

#### V1- "It smells so bad, I better have a good reason to get myself to this torture"

#### Auto Injector + Moon Drug = Dream Narrative Bit

##### [Skips 4h of in game hours]

###### Gets automatic comment from Buckley "We all have our wars in that room, I hope that the toilet survived this time"

### Interact with Stairs

(Corridor)

#### Gets comment from detective "The only way I'm leaving this place is if get fired"

### Interact using E1 (Gun)

#### Confront Captain

##### V1: Response "You're funny guy, but stop joking around"

##### V2: Response "I'm not kidding, get back and do your job, stop wasting your time"

##### V3: Response "That's it ! Get the fuck out of my sigh and never come here ever again"

###### Ending Gets Fired - [The detective walks away] and comments "Maybe getting fired isn't the worst thing, maybe becoming a private detective might be the best for me, since I don't have to follow these unforgiving state institutions"

#### Interact with Buckley

##### Response: "Nice gun! Don't go swing that around"

### [Interacts with the detective] Auto Injector + Adrenaline

#### V1: "I better only use this if I have to, using this for no reason could get me killed"

#### V2- [Interacts with the detective] Auto Injector + Moon Adrenaline =

##### Ending Gets Killed - [Falls to the ground, sound of heart beat, then it stop, screen becomes blurry and transitions to darkness] detective then comments "Now I just have to wait in peace"

---

# Game Architecture — State-Machine Logic Reference

> Parsed from `Diagram.xml` + Logic Override Rules. All variable names treated as literal, case-sensitive strings. Labels are space-stripped per parsing rules (e.g., `TRIGGER_DREAM _SEQUENCE` → `TRIGGER_DREAM_SEQUENCE`).

---

## 1. Game Flow States

All `GLOBAL_ROOM_STATE` and `OUTPUT_PLACE` nodes that represent persistent room or game states.

| State Variable                       | Description                                                                                                                                                                                                                                          |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `STATE_EXPLORING_EVIDENCE_ROOM`      | Player is free-roaming the Evidence Room. Starting state post-intro. Exposes clickable: `CaseFolder.Object`, `CorridorRoom.Door`, `Window`, `LockedRoom.Door`, `Computer`.                                                                           |
| `STATE_EXPLORING_CORRIDOR_ROOM`      | Player is in the Corridor hub. Exposes navigation doors: Bathroom, Observation Room, Interrogation Room, Evidence Room, Stairs. This is also the **failure return state** — `POST_MILLER_CONFRONTATION_NOT_ENOUGH_EVIDENCE` always routes back here. |
| `STATE_EXPLORING_LOCKED_ROOM`        | Player has unlocked and entered the Locked Room. Becomes accessible only after `OPENED_DOOR_USING_KEYS` is set.                                                                                                                                      |
| `STATE_EXPLORING_INTERROGATION_ROOM` | Player is in the Interrogation Room with a suspect present. Entry requires `SUSPECT_READY_FOR_INTERROGATION`. Exposes the suspect interaction object.                                                                                                |
| `STATE_EXPLORING_OBSERVATION_ROOM`   | Player is in the Observation Room. Entered from the Corridor via `ClickOn.ObservationRoom.Door`.                                                                                                                                                     |
| `KAELEN_IN_IR`                       | Flag/state set when Kae enters the Interrogation Room (triggered by inquiring Miller with `PK_EQUIPPED`). Triggers a `FADE_TO_BLACK`.                                                                                                                |
| `ELARA_IN_IR`                        | Flag/state set when Elara enters the Interrogation Room (triggered by inquiring Miller with `PE_EQUIPPED`). Triggers a `FADE_TO_BLACK`.                                                                                                              |

### System-Level State Flags

| Flag                                | Description                                                                                                                                         |
| ----------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| `INITIAL_SEQUENCE_STARTED`          | Set when `GameStarts` fires via `MILLER_BRIEF_00`.                                                                                                  |
| `POST_BRIEF_00`                     | Set after the first Miller briefing segment completes.                                                                                              |
| `CASE_FOLDER_ACQUIRED`              | Set after the `Acquire.CaseFolder` transition fires.                                                                                                |
| `POST_BRIEF_01`                     | Set after the second Miller briefing segment completes.                                                                                             |
| `INITIAL_SEQUENCE_COMPLETE`         | Set when the full intro chain resolves. Prerequisite for `FadeInGameplay`.                                                                          |
| `SLOTS_INVENTORY_ENABLED`           | Set by `EnableFreeRoam`. Activates the SlotManager/inventory HUD.                                                                                   |
| `OPENED_DOOR_USING_KEYS`            | Persistent flag set when `KEYS_EQUIPPED` + `OpenLockedRoomDoor` fires. Unlocks `STATE_EXPLORING_LOCKED_ROOM` permanently.                           |
| `LR_NOTE_ACQUIRED`                  | Set when `Acquire.LockedRoomNote` fires. Enables Key acquisition dialogue.                                                                          |
| `DISPLAY_COMPUTER_WINDOW`           | Set when `ClickOn.Computer` fires. Opens the tape-based computer UI.                                                                                |
| `TAPE_EQUIPPED_SLOT_A`              | Set when any tape is loaded. Routes to applicable Computer Rules per tape type.                                                                     |
| `INTERNAL_CLOCK_STARTS`             | Initiates the in-game 36-hour time limit countdown.                                                                                                 |
| `RAN_OUT_OF_TIME`                   | Set when `REACHED_36_HOURS_LIMIT` fires via `TRIGGER_TIME_LIMIT_REACHED` → `MILLER_TIMEOUT_SEQUENCE` (subroutine pointer).                          |
| `SUSPECT_INTERACTED`                | Set after first contact with a suspect in the Interrogation Room. Required to unlock `MILLER_CONFRONTATION_00`.                                     |
| `DREAM_EXPERIENCED`                 | Side-effect flag. Set after any dream sequence completes. Persists for `MILLER_ANGRY_SEQUENCE` eligibility. Does **not** change current room state. |
| `MILLER_ANGRY_SEQUENCE_INITIALIZED` | Set when `MILLER_ANGRY_SEQUENCE` (subroutine) fires.                                                                                                |
| `ENABLE_CUTSCENE_CONTROLS`          | Set at start of ending sequence. Replaces player input mode.                                                                                        |
| `DESABLE_PLAYER_CONTROLS`           | Set simultaneously with `ENABLE_CUTSCENE_CONTROLS`. Disables free-roam input.                                                                       |
| `ENDING_SEQUENCE_COMPLETE`          | Set after `MILLER_ENDING_DIALOGUE` fires. Leads to `TRIGGER_CREDITS_ROLL`.                                                                          |

---

## 2. Linear Sequence Events

Step-by-step from `GameStarts` to `EnableFreeRoam`.

```
Step 01 │ [EVENT]       GameStarts
         │               Fires unconditionally at launch.
         │
Step 02 │ [FLAG SET]    INITIAL_SEQUENCE_STARTED
         │               OUTPUT_PLACE set immediately by the GameStarts transition.
         │
Step 03 │ [DIALOGUE]    MILLER_BRIEF_00
         │               First briefing sequence. Miller introduces the case.
         │
Step 04 │ [FLAG SET]    POST_BRIEF_00
         │               Set on completion of MILLER_BRIEF_00.
         │
Step 05 │ [EVENT]       Acquire.CaseFolder
         │               Case folder physically handed to player (auto-triggered).
         │               Items received: CASE-47 or CASE-19 (per context).
         │
Step 06 │ [FLAG SET]    CASE_FOLDER_ACQUIRED
         │               OUTPUT_PLACE set by Acquire.CaseFolder.
         │
Step 07 │ [DIALOGUE]    MILLER_BRIEF_01
         │               Second briefing segment. Miller outlines the time limit.
         │
Step 08 │ [FLAG SET]    POST_BRIEF_01
         │               Set on completion of MILLER_BRIEF_01.
         │
Step 09 │ [FLAG SET]    INITIAL_SEQUENCE_COMPLETE
         │               Final flag of the intro chain. Set after POST_BRIEF_01.
         │
Step 10 │ [EVENT]       FadeInGameplay
         │               Visual fade from black into the Evidence Room.
         │
Step 11 │ [EVENT]       EnableFreeRoam
         │               Activates player controls and inventory HUD.
         │
Step 12 │ [FLAG SET]    SLOTS_INVENTORY_ENABLED
         │               Set as a simultaneous OUTPUT_PLACE of EnableFreeRoam.
         │               All STARTER_FILES are now in inventory:
         │               ARE, ARK, IR, MEMO, E8R, E1, E2, E3, E15, E13, E17,
         │               E21, E10, E18, PK, PE, PA, AV, AI, TN
         │
Step 13 │ [STATE]       STATE_EXPLORING_EVIDENCE_ROOM
         │               First active GLOBAL_ROOM_STATE. Player is now in Evidence Room.
         │               INTERNAL_CLOCK_STARTS also fires here (36-hour countdown begins).
```

---

## 3. Interaction Logic Table

> **Key:**
> 
> - `$_EQUIPPED` = any single evidence item in SlotManager.
> - `_ACQUIRED` = obtained automatically after an event.
> - `[OR]` logic explicitly denoted where present in XML.
> - **AND** logic: multiple PRECONDITION sources listed mean all must be true.

| Trigger Action                                  | Required Conditions (Preconditions)                                       | Resulting State / Event / Flag                                                                                                                                                                                                                                                                                                                          |
| ----------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `ClickOn.CorridorRoom.Door`                     | None (available in `STATE_EXPLORING_EVIDENCE_ROOM`)                       | → `STATE_EXPLORING_CORRIDOR_ROOM`                                                                                                                                                                                                                                                                                                                       |
| `ClickOn.EvidenceRoom.Door`                     | Available in `STATE_EXPLORING_CORRIDOR_ROOM`                              | → `STATE_EXPLORING_EVIDENCE_ROOM`                                                                                                                                                                                                                                                                                                                       |
| `ClickOn.Bathroom.Door`                         | Available in `STATE_EXPLORING_CORRIDOR_ROOM`                              | → Dialogue cluster: `JULIAN_BATHROOM_00`, then `JULIAN_BATHROOM_01`                                                                                                                                                                                                                                                                                     |
| `ClickOn.ObservationRoom.Door`                  | Available in `STATE_EXPLORING_CORRIDOR_ROOM`                              | → `STATE_EXPLORING_OBSERVATION_ROOM`                                                                                                                                                                                                                                                                                                                    |
| `ClickOn.Stairs`                                | Available in `STATE_EXPLORING_CORRIDOR_ROOM`                              | → `DISPLAY_DIALOGUE_WINDOW` → `JULIAN_STAIRS_00` → `POST_STAIRS_00` → `TRIGGER_OPTION_00` → `STATE_EXPLORING_CORRIDOR_ROOM`                                                                                                                                                                                                                             |
| `ClickOn.Window`                                | Available in `STATE_EXPLORING_EVIDENCE_ROOM`                              | → `DISPLAY_DIALOGUE_WINDOW` → `JULIAN_WINDOW_00` → `POST_JULIAN_WINDOW_00` → `TRIGGER_OPTION_00` → `STATE_EXPLORING_EVIDENCE_ROOM`                                                                                                                                                                                                                      |
| `ClickOn.InterrogationRoom.Door`                | Available in `STATE_EXPLORING_CORRIDOR_ROOM`                              | → `CHECKING_INTERROGATION_ROOM_STATUS` (CHECK_NODE)                                                                                                                                                                                                                                                                                                     |
| — `InterrogationRoom.AllowEntry` branch         | `SUSPECT_READY_FOR_INTERROGATION` = true                                  | → `STATE_EXPLORING_INTERROGATION_ROOM` + `DISPLAY_DIALOGUE_WINDOW`                                                                                                                                                                                                                                                                                      |
| — `InterrogationRoom.DenyEntry` branch          | `SUSPECT_READY_FOR_INTERROGATION` = false                                 | → `DISPLAY_DIALOGUE_WINDOW` → `JULIAN_IR_DENIED_00` → `POST_IR_DENIED_00` → `TRIGGER_OPTION_00` → `STATE_EXPLORING_CORRIDOR_ROOM`                                                                                                                                                                                                                       |
| `ClickOn.LockedRoom.Door`                       | Available in `STATE_EXPLORING_EVIDENCE_ROOM`                              | → `CHECKING_LOCKED_ROOM_STATUS` (CHECK_NODE)                                                                                                                                                                                                                                                                                                            |
| — `LockedRoom.AllowEntry` branch                | `OPENED_DOOR_USING_KEYS` = true                                           | → `STATE_EXPLORING_LOCKED_ROOM`                                                                                                                                                                                                                                                                                                                         |
| — `LockedRoom.DenyEntry` branch (Option 00)     | `LR_NOTE_ACQUIRED` = false                                                | → `DISPLAY_INTERACTION_WINDOW` → `TRIGGER_OPTION_00` → `JULIAN_LR_DENIED_00` → sets `LR_NOTE_ACQUIRED && POST_LR_DENIED_00`                                                                                                                                                                                                                             |
| — `LockedRoom.DenyEntry` branch (Option 01)     | `LR_NOTE_ACQUIRED` = true (already acquired)                              | → `TRIGGER_OPTION_01` → `JULIAN_LR_DENIED_01` → `POST_LR_DENIED_01` → re-routes to `CHECKING_LOCKED_ROOM_STATUS`                                                                                                                                                                                                                                        |
| `Acquire.LockedRoomNote`                        | Triggered from the Locked Room Deny branch                                | → `LR_NOTE_ACQUIRED && POST_LR_DENIED_00` flag set                                                                                                                                                                                                                                                                                                      |
| `KEYS_EQUIPPED` (precondition active)           | `KEYS_ACQUIRED` = true AND key item in slot                               | → Enables `OpenLockedRoomDoor` transition                                                                                                                                                                                                                                                                                                               |
| `OpenLockedRoomDoor`                            | `KEYS_EQUIPPED`                                                           | → `OPENED_DOOR_USING_KEYS` (OUTPUT_PLACE) → `LockedRoom.AllowEntry` → `STATE_EXPLORING_LOCKED_ROOM`                                                                                                                                                                                                                                                     |
| `ClickOn.Computer`                              | Available in `STATE_EXPLORING_EVIDENCE_ROOM`                              | → `DISPLAY_COMPUTER_WINDOW`                                                                                                                                                                                                                                                                                                                             |
| `ClickOn.Tape.FL`                               | `DISPLAY_COMPUTER_WINDOW` active                                          | → `TAPE_EQUIPPED_SLOT_A` (type FL)                                                                                                                                                                                                                                                                                                                      |
| `ClickOn.Tape.MU`                               | `DISPLAY_COMPUTER_WINDOW` active                                          | → `TAPE_EQUIPPED_SLOT_A` (type MU)                                                                                                                                                                                                                                                                                                                      |
| `ClickOn.Tape.CSU`                              | `DISPLAY_COMPUTER_WINDOW` active                                          | → `TAPE_EQUIPPED_SLOT_A` (type CSU)                                                                                                                                                                                                                                                                                                                     |
| `ClickOn.Tape.EC`                               | `DISPLAY_COMPUTER_WINDOW` active                                          | → `TAPE_EQUIPPED_SLOT_A` (type EC)                                                                                                                                                                                                                                                                                                                      |
| `CHECKING_REQUIREMENTS` (Computer submit)       | Tape + Evidence item equipped                                             | → Routes to matching `Aquire.*` transition; after acquisition, **used tape is removed from slot** → return to Tape Selection Phase                                                                                                                                                                                                                      |
| **Computer: `MAP-R` acquisition**               | `TAPE_EC_EQUIPPED` AND `E11R_EQUIPPED`                                    | → `MAP-R_EQUIPPED` (manual acquisition via submit)                                                                                                                                                                                                                                                                                                      |
| `JULIAN_BATHROOM_01` (Bathroom interaction)     | `AUTOINJECTOR_EQUIPPED` AND`E15_EQUIPPED`                                 | → Offers `TRIGGER_OPTION_00` (use substance) or `TRIGGER_OPTION_01` (dismiss)                                                                                                                                                                                                                                                                           |
| — Bathroom `TRIGGER_OPTION_00` (Use `E15`)      | `E15` not previously `SET_E15_USED`                                       | → `SET_E15_USED` + `TIME_SUBTRACT_4h` + `TRIGGER_DREAM_SEQUENCE` (subroutine pointer) → `SET_DREAM_SEQUENCE_TO_EXPERIENCED` + `BATHROOM_DREAM_EXPERIENCED` → `JULIAN_BATHROOM_02` → `POST_BATHROOM_00`                                                                                                                                                  |
| — Bathroom `TRIGGER_OPTION_01` (Dismiss)        | None                                                                      | → `POST_BATHROOM_00` → returns to corridor context                                                                                                                                                                                                                                                                                                      |
| — Moon `TRIGGER_OPTION_00` (Use Moon/AV)        | Not `SET_E15_TO_USED` / Not `SET_AV_TO_USED`                              | → `FALL_DOWN_ANIMATION` (transient, no room change) + `SET_E15_TO_USED` + `TRIGGER_DREAM_SEQUENCE` (subroutine) → `SET_DREAM_SEQUENCE_TO_EXPERIENCED` + `DREAM_EXPERIENCED` → then `MILLER_ANGRY_SEQUENCE` if `DREAM_EXPERIENCED` already set                                                                                                           |
| — Moon `TRIGGER_OPTION_01` (Refuse)             | None                                                                      | → `CLOSE_DIALOGUE_WINDOW` → `TRIGGER_OPTION_01` → leads to Dream dialogue branch (`JULIAN_DREAM_00` → `POST_JULIAN_DREAM_00`) then `ClickOn.LightPerson.Object` sequence                                                                                                                                                                                |
| `ClickOn.LightPerson.Object`                    | Fires after `CLOSE_DIALOGUE_WINDOW` from dream path                       | → `DISPLAY_DIALOGUE_WINDOW` → `LIGHT_PERSON_DREAM_00` → options `TRIGGER_OPTION_00` / `TRIGGER_OPTION_01` → `LIGHT_PERSON_DREAM_01` → `POST_DETECTIVE_DREAM_01` → connects forward to `TRIGGER_OPTION_00` or `TRIGGER_OPTION_01` *(per Missing Links rule: `POST_LIGHT_PERSON_DREAM_00` connects to either `TRIGGER_OPTION_00` or `TRIGGER_OPTION_01`)* |
| `ClickOn.Miller.Object` (Corridor)              | `STATE_EXPLORING_CORRIDOR_ROOM` active                                    | → `DISPLAY_DIALOGUE_WINDOW` → Miller inquiry / confrontation routing                                                                                                                                                                                                                                                                                    |
| Miller Inquiry: `LR_NOTE_EQUIPPED`              | `LR_NOTE_ACQUIRED` AND LR Note in slot                                    | → `KEYS_ACQUIRED` (per Missing Links rule) + `POST_MILLER_INQUIRY_$` + `DISPLAY_DIALOGUE_WINDOW`                                                                                                                                                                                                                                                        |
| Miller Inquiry: `CT_EQUIPPED`                   | Confession Tape in slot                                                   | → `INITIATE_4H_COUNTDOWN_L1` + `POST_MILLER_INQUIRY_$` + `DISPLAY_DIALOGUE_WINDOW`                                                                                                                                                                                                                                                                      |
| Miller Inquiry: `PK_EQUIPPED`                   | Portrait of Kaelen in slot                                                | → `KAELEN_IN_IR` + `FADE_TO_BLACK` + `POST_MILLER_INQUIRY_$` + `DISPLAY_DIALOGUE_WINDOW`                                                                                                                                                                                                                                                                |
| Miller Inquiry: `PE_EQUIPPED`                   | Portrait of Elara in slot                                                 | → `ELARA_IN_IR` + `FADE_TO_BLACK` + `POST_MILLER_INQUIRY_$` + `DISPLAY_DIALOGUE_WINDOW`                                                                                                                                                                                                                                                                 |
| Miller Inquiry: `E4R_EQUIPPED`                  | E4R (Barefoot Condition Report) in slot                                   | → `INITIATE_4H_COUNTDOWN_E4-TRACE` + `POST_MILLER_INQUIRY_$` + `DISPLAY_DIALOGUE_WINDOW`                                                                                                                                                                                                                                                                |
| Miller Inquiry: `E9R_EQUIPPED`                  | Arthur Penhaligon's Police Complaint in slot                              | → `DISPLAY_INQUIRY_OPTIONS` → `TRIGGER_OPTION_$` → `POST_MILLER_INQUIRY_$` + `DISPLAY_DIALOGUE_WINDOW`                                                                                                                                                                                                                                                  |
| Miller Inquiry: `MAP-R_EQUIPPED`                | MAP-R in slot                                                             | → `DISPLAY_INQUIRY_OPTIONS` → `TRIGGER_OPTION_$` → `POST_MILLER_INQUIRY_$` + `DISPLAY_DIALOGUE_WINDOW`                                                                                                                                                                                                                                                  |
| `4H_COUNTDOWN_E4-TRACE_COMPLETE`                | Fires after 4-hour real-time delay                                        | → `ClickOn.Miller.Object` enabled → `MILLER_TRACE_00` → `POST_MILLER_TRACE_00` + `E4-TRACE_ACQUIRED` + `DISPLAY_DIALOGUE_WINDOW`                                                                                                                                                                                                                        |
| `4H_COUNTDOWN_F1_COMPLETE`                      | Fires after 4-hour delay (Crime Report)                                   | → `ClickOn.Miller.Object` → `MILLER_TRACE_00` → `POST_MILLER_TRACE_00` + `F1_ACQUIRED` + `DISPLAY_DIALOGUE_WINDOW`                                                                                                                                                                                                                                      |
| `4H_COUNTDOWN_L1_COMPLETE`                      | Fires after 4-hour delay (Marco Rico Statement)                           | → `ClickOn.Miller.Object` → dialogue → `L1_ACQUIRED` (Ambiguous from XML — implied by countdown pattern)                                                                                                                                                                                                                                                |
| **Confrontation Gate: `CHECKING_REQUIREMENTS`** | `E2R_ACQUIRED` AND `SUSPECT_INTERACTED`                                   | → `MILLER_CONFRONTATION_00`                                                                                                                                                                                                                                                                                                                             |
| — Confrontation denied                          | Requirements not met                                                      | → `MILLER_CONFRONTATION_DENIED` → `DISPLAY_DIALOGUE_WINDOW` + `POST_MILLER_CONFRONTATION_DENIED`                                                                                                                                                                                                                                                        |
| `MILLER_CONFRONTATION_00`                       | Requirements met                                                          | → `POST_MILLER_CONFRONTATION_00` → `TRIGGER_OPTION_00` / `TRIGGER_OPTION_01`                                                                                                                                                                                                                                                                            |
| `MILLER_CONFRONTATION_01`                       | `POST_TRIGGER_OPTION_00` from confrontation 00                            | → `$_EQUIPPED` precondition → `TRIGGER_OPTION_$` → `POST_MILLER_CONFRONTATION_01`                                                                                                                                                                                                                                                                       |
| `MILLER_CONFRONTATION_02`                       | `POST_TRIGGER_OPTION_$` from confrontation 01                             | → `$_EQUIPPED` precondition → `TRIGGER_OPTION_$` → `POST_MILLER_CONFRONTATION_02`                                                                                                                                                                                                                                                                       |
| `MILLER_CONFRONTATION_03`                       | `POST_TRIGGER_OPTION_$` from confrontation 02                             | → `$_EQUIPPED` precondition → `TRIGGER_OPTION_$` → `POST_MILLER_CONFRONTATION_03`                                                                                                                                                                                                                                                                       |
| `MILLER_CONFRONTATION_04`                       | `POST_TRIGGER_OPTION_$` from confrontation 03                             | → `$_EQUIPPED` precondition → `TRIGGER_OPTION_$` → continues confrontation chain                                                                                                                                                                                                                                                                        |
| `MILLER_CONFRONTATION_NOT_ENOUGH_EVIDENCE_01`   | `NOT_ENOUGH_EVIDENCE` [OR] `DREAM_EXPERIENCED [OR] RAN_OUT_OF_TIME`       | → `POST_MILLER_CONFRONTATION_NOT_ENOUGH_EVIDENCE_01` → `TRIGGER_ENDING_GETS_FIRED`                                                                                                                                                                                                                                                                      |
| **Failure Path**                                | `POST_MILLER_CONFRONTATION_NOT_ENOUGH_EVIDENCE`                           | → Always routes back to `STATE_EXPLORING_CORRIDOR_ROOM`                                                                                                                                                                                                                                                                                                 |
| `TRIGGER_ENDING_GETS_FIRED`                     | `NOT_ENOUGH_EVIDENCE` + (`DREAM_EXPERIENCED [OR] RAN_OUT_OF_TIME`)        | → Detective walks away. Dialogue: *"Maybe becoming a private detective might be the best for me…"*                                                                                                                                                                                                                                                      |
| `TRIGGER_ENDING_GETS_KILLED`                    | Ambiguous from XML — condition not fully resolved in source               | → Detective collapses, heartbeat stops, screen blurs to black. Dialogue: *"Now I just have to wait in peace."*                                                                                                                                                                                                                                          |
| `REACHED_36_HOURS_LIMIT`                        | Internal clock expires                                                    | → `TRIGGER_TIME_LIMIT_REACHED` → `MILLER_TIMEOUT_SEQUENCE` (subroutine pointer) → `RAN_OUT_OF_TIME`                                                                                                                                                                                                                                                     |
| Interrogation Room — Suspect Inquiry            | `$_EQUIPPED` (any item) in slot; suspect present                          | → `DISPLAY_AVAILABLE_INQUIRY_OPTIONS` → `TRIGGER_OPTION_$` → `POST_TRIGGER_OPTION_$` → `ELARA_INQUIRY_$ [OR] KAELEN_INQUIRY_$`                                                                                                                                                                                                                          |
| Interrogation Room — Suspect Confrontation      | `$_EQUIPPED` (any item) in slot; suspect present                          | → `DISPLAY_AVAILABLE_CONFRONTATION_OPTIONS` → `TRIGGER_OPTION_$` → `POST_TRIGGER_OPTION_$` → `ELARA_CONFRONTATION_$ [OR] KAELEN_CONFRONTATION_$`                                                                                                                                                                                                        |
| `OpenLockedRoomDoor`                            | `KEYS_EQUIPPED`                                                           | → `STATE_LOCKED_ROOM_ENTRY_TIMER` (Starts 30s)                                                                                                                                                                                                                                                                                                          |
| Survival Interaction** (`[E]` Key)              | AV_EQUIPPED` AND `AI_EQUIPPED` AND `STATE_LOCKED_ROOM_ENTRY_TIMER` active | → `TRIGGER_FALL_ANIMATION` (Calls `FallSequenceController.TriggerFall()`) → `SET_LOCKED_ROOM_SAVED` → `STATE_EXPLORING_LOCKED_ROOM`                                                                                                                                                                                                                     |
| **Failure Condition**                           | `REACHED_30_SECONDS_LIMIT`                                                | → `TRIGGER_ENDING_GETS_KILLED` (via `EndingSequenceController`)                                                                                                                                                                                                                                                                                         |

---

## 4. Inventory & Evidence Acquisition

All transitions that produce an `_ACQUIRED` OUTPUT_PLACE flag. Items marked **[STARTER]** are in inventory at game start.

### 4A — Starter Files (Automatic at `EnableFreeRoam`)

These are issued without conditions:

`ARE_ACQUIRED`, `ARK_ACQUIRED`, `IR_ACQUIRED`, `MEMO_ACQUIRED`, `E8R_ACQUIRED` *(note: E8R is a starter file)*, `E1_ACQUIRED`, `E2_ACQUIRED`, `E3_ACQUIRED`, `E15_ACQUIRED`, `E13_ACQUIRED`, `E17_ACQUIRED`, `E21_ACQUIRED`, `E10_ACQUIRED`, `E18_ACQUIRED`, `PK_ACQUIRED`, `PE_ACQUIRED`, `PA_ACQUIRED`, `AV_ACQUIRED`, `AI_ACQUIRED`, `TN_ACQUIRED`

### 4B — Computer-Acquired Reports (via Tape + Evidence Combination)

After acquisition, the used tape is ejected from Slot A and the system returns to the Tape Selection Phase.

| Transition                   | Tape Required                                  | Evidence Required (OR logic where noted)                     | Flag Set                                               |
| ---------------------------- | ---------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------ |
| `Aquire.E2R`                 | `TAPE_FL_EQUIPPED` [OR] `TAPE_EQUIPPED_SLOT_A` | `E2_EQUIPPED` [OR] `TAPE_FL_EQUIPPED`                        | `E2R_ACQUIRED`                                         |
| `Aquire.E3R`                 | `TAPE_FL_EQUIPPED`                             | `E3_EQUIPPED` [OR] `TAPE_FL_EQUIPPED`                        | `E3R_ACQUIRED`                                         |
| `Aquire.E21R`                | `TAPE_FL_EQUIPPED`                             | `E21_EQUIPPED` [OR] `TAPE_FL_EQUIPPED`                       | `E21R_ACQUIRED`                                        |
| `Aquire.E4R`                 | `TAPE_MU_EQUIPPED`                             | `PE_EQUIPPED [OR] ARE_EQUIPPED` [OR] `TAPE_MU_EQUIPPED`      | `E4R_ACQUIRED`                                         |
| `Aquire.E4-C`                | `TAPE_MU_EQUIPPED`                             | `E4R_EQUIPPED` [OR] `TAPE_MU_EQUIPPED`                       | `E4-C_ACQUIRED`                                        |
| `Aquire.E12R`                | `TAPE_MU_EQUIPPED`                             | `PK_EQUIPPED [OR] ARK_EQUIPPED` [OR] `TAPE_MU_EQUIPPED`      | `E12R_ACQUIRED` *(Computer loop — tape ejected after)* |
| `Aquire.E16R`                | `TAPE_MU_EQUIPPED`                             | *(Ambiguous from XML — secondary precondition not resolved)* | `E16R_ACQUIRED`                                        |
| `Aquire.E19R`                | `TAPE_EC_EQUIPPED`                             | `PK_EQUIPPED` [OR] `TAPE_EC_EQUIPPED`                        | `E19R_ACQUIRED`                                        |
| `Aquire.17R` *(label as-is)* | `TAPE_EC_EQUIPPED`                             | `E17_EQUIPPED` [OR] `TAPE_EC_EQUIPPED`                       | `E17R_ACQUIRED`                                        |
| `Aquire.E10R`                | `TAPE_EC_EQUIPPED`                             | `E10_EQUIPPED` [OR] `TAPE_EC_EQUIPPED`                       | `E10R_ACQUIRED`                                        |
| `Aquire.E10-B`               | `TAPE_EC_EQUIPPED`                             | `E10R_EQUIPPED` [OR] `TAPE_EC_EQUIPPED`                      | `E10-B_ACQUIRED`                                       |
| `Aquire.E11R`                | `TAPE_EC_EQUIPPED`                             | `ARK_EQUIPPED` [OR] `TAPE_EC_EQUIPPED`                       | `E11R_ACQUIRED`                                        |
| `Aquire.E23R`                | `TAPE_EC_EQUIPPED`                             | `PE_EQUIPPED [OR] ARE_EQUIPPED` [OR] `TAPE_EC_EQUIPPED`      | `E23R_ACQUIRED`                                        |
| `Aquire.E22R`                | `TAPE_EC_EQUIPPED`                             | `PA_EQUIPPED` [OR] `TAPE_EC_EQUIPPED`                        | `E22R_ACQUIRED`                                        |
| `Aquire.E3R` *(EC variant)*  | `TAPE_EC_EQUIPPED`                             | `E3_EQUIPPED` [OR] `TAPE_EC_EQUIPPED`                        | `E3R_ACQUIRED`                                         |
| `MAP-R acquisition`          | `TAPE_EC_EQUIPPED` (AND) `E11R_EQUIPPED`       | Manual equip + submit                                        | `MAP-R_EQUIPPED`                                       |

> **Computer Loop Rule:** After `E14R_ACQUIRED`, `E8-A_ACQUIRED`, or `E12R_ACQUIRED`, the tape is removed from Slot A. Player must re-equip a tape to continue.

### 4C — Miller-Mediated Acquisitions (Timed, via Countdown)

| Trigger                                             | Countdown                                                                | Precondition                          | Flag Set                                       |
| --------------------------------------------------- | ------------------------------------------------------------------------ | ------------------------------------- | ---------------------------------------------- |
| Miller inquiry with `E4R_EQUIPPED`                  | `INITIATE_4H_COUNTDOWN_E4-TRACE` → 4h → `4H_COUNTDOWN_E4-TRACE_COMPLETE` | `E4R_EQUIPPED`                        | `E4-TRACE_ACQUIRED`                            |
| Miller inquiry with `F1`-related item               | `INITIATE_4H_COUNTDOWN_F1` → 4h → `4H_COUNTDOWN_F1_COMPLETE`             | *(Evidence item; Ambiguous from XML)* | `F1_ACQUIRED`                                  |
| Miller inquiry with `CT_EQUIPPED` (Confession Tape) | `INITIATE_4H_COUNTDOWN_L1` → 4h                                          | `CT_EQUIPPED`                         | `L1_ACQUIRED` *(Ambiguous from XML — implied)* |

### 4D — Event-Acquired Items (Automatic After Events)

| Event That Fires                                        | Flag Set                                                                  | Item                                                                                            |
| ------------------------------------------------------- | ------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| `MILLER__INQUIRY_$` with `LR_NOTE_EQUIPPED`             | `KEYS_ACQUIRED`                                                           | Keys to the Locked Door                                                                         |
| Entered the Locked Room                                 | `STATE_LOCKED_ROOM_ENTRY_TIMER`                                           | Active during the 30-second survival countdown. Disables normal movement.                       |
| Player saved himself using AI + AV                      | `SET_LOCKED_ROOM_SAVED`                                                   | Set upon successful interaction with [E]. Permanently unlocks the Locked Room for future entry. |
| Player didn't save himself                              | `TRIGGER_ENDING_GETS_KILLED`                                              | Terminal state triggered if the player fails to use the AV and AI before the timer expires.     |
| Dream sequence completes (either path)                  | `DREAM_EXPERIENCED`                                                       | Side-effect flag (not an inventory item)                                                        |
| `TRIGGER_DREAM_SEQUENCE` (both bathroom and moon paths) | `SET_DREAM_SEQUENCE_TO_EXPERIENCED`                                       | Side-effect flag                                                                                |
| Bathroom `E15` path                                     | `SET_E15_USED` + `BATHROOM_DREAM_EXPERIENCED`                             | Consumable block flag                                                                           |
| Moon/Detective object `TRIGGER_OPTION_00`               | `SET_E15_TO_USED` [or `SET_AV_TO_USED` per AV path] + `DREAM_EXPERIENCED` | Consumable block flag                                                                           |

### 4E — Consumable Rules

| Item                            | Consumable Flag                    | Block Condition                                                                 | Notes                                                                                                      |
| ------------------------------- | ---------------------------------- | ------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| `AV` (Julian's Adrenaline Vial) | `SET_AV_TO_USED`                   | Once set, the gated action (injection) cannot repeat. `AV` remains equippable.  | Triggers `FALL_DOWN_ANIMATION` (transient visual only; no room change).                                    |
| `E15` (Somnoryl-μ Vials)        | `SET_E15_USED` / `SET_E15_TO_USED` | Once set, the gated action (injection) cannot repeat. `E15` remains equippable. | Used in both Bathroom and Locked Room paths. Also set by `MILLER_ANGRY_SEQUENCE`.                          |
| AV + AI                         | Used as "Survival Kit"             | Once set, the gated action (injection) cannot repeat. `AI` remains equippable.  | Must be equipped during the 30s STATE_LOCKED_ROOM_ENTRY_TIMER to trigger the FallSequence and save Julian. |

---

## 5. Ending & Outcome Logic

### 5A — Ending Entry Gate

The ending sequence is gated by the `CHECKING_REQUIREMENTS` (CHECK_NODE) during the Miller Confrontation. Only when sufficient evidence is assembled does `MILLER_CONFRONTATION_00` fire. Insufficient evidence routes to the `MILLER_CONFRONTATION_NOT_ENOUGH_EVIDENCE_01` path.

**Conviction flags** are set during the Confrontation chain (steps `MILLER_CONFRONTATION_00` through `_04`). The specific conviction depends on which evidence items are equipped (`$_EQUIPPED`) during each confrontation round.

---

### 5B — TRIGGERENDING_1 (Reaction Phase)

**Rule:** `TRIGGERENDING_1` always strictly precedes `TRIGGERENDING_2`.

Entry point: `TRIGGER_ENDING_SEQUENCE_00` fires upon confrontation completion.

Simultaneous effects:

- `POST_TRIGGER_ENDING_SEQUENCE_00` is set.
- `ENABLE_CUTSCENE_CONTROLS` is set.
- `DESABLE_PLAYER_CONTROLS` is set.

From `POST_TRIGGER_ENDING_SEQUENCE_00`, the system fans out to the Elara Reaction branches and then the Kae Reaction branches in sequence:

#### Elara Reaction Branches (`TRIGGER_ENDING_1_ELARA_$`)

| Variant                               | Precondition(s)                        | Behaviour                                                                                                                                              |
| ------------------------------------- | -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `TRIGGER_ENDING_1_ELARA_$` (Free)     | `ELARA_FREE`                           | If `SHOWN_CONFESSION_TAPE` = true → Elara defends Kae's innocence emotionally. If `SHOWN_CONFESSION_TAPE` = false → Elara is confused, asks about Kae. |
| `TRIGGER_ENDING_1_ELARA_$` (Arrested) | `ELARA_MURDER` [OR] `ELARA_ACCOMPLICE` | Elara is being charged. Reaction varies by conviction.                                                                                                 |

All Elara reaction branches converge at `POST_TRIGGER_ENDING_1_ELARA_$` → `POST_TRIGGER_ENDING_SEQUENCE_01`.

#### Kae Reaction Branches (`TRIGGER_ENDING_1_KAE_$`)

| Variant                               | Precondition(s)                                         | Behaviour                                                       |
| ------------------------------------- | ------------------------------------------------------- | --------------------------------------------------------------- |
| `TRIGGER_ENDING_1_KAE_02`             | `KAE_ACCOMPLICE [OR] ELARA_ACCMPLICE [OR] ELARA_MURDER` | Kae reaction for accomplice/shared-guilt conviction.            |
| `TRIGGER_ENDING_1_KAE_03` (variant A) | `NO_CONFESSION_TAPE` AND `KAE_MURDER`                   | Standard guilty reaction, no confession exists.                 |
| `TRIGGER_ENDING_1_KAE_03` (variant B) | `CONFESSION_TAPE` AND `KAE_MURDER`                      | Kae being arrested with confession; begs for Elara's release.   |
| `TRIGGER_ENDING_1_KAE_03` (variant C) | `SHOWN_E4-TRACE` AND `KAE_MURDER`                       | Trace evidence variant; Kae confronted with barefoot mud trace. |
| `TRIGGER_ENDING_1_KAE_03` (variant D) | `ELARA_FREE` AND `KAE_MURDER`                           | Kae accepts fate while Elara goes free.                         |

All Kae reaction branches converge at `POST_TRIGGER_ENDING_1_KAE_$`.

Flow after Kae reactions → `TRIGGER_ENDING_SEQUENCE_02` → `POST_TRIGGER_ENDING_SEQUENCE_02` → fans out to the Outcome Phase.

---

### 5C — TRIGGERENDING_2 (Outcome Phase)

Entry: `POST_TRIGGER_ENDING_SEQUENCE_02` → fans to multiple `TRIGGER_ENDING_2_$` branches based on conviction flags.

#### Elara Outcomes (`TRIGGER_ENDING_2_ELARA_$`)

| Conviction Flag    | Outcome Scene                              |
| ------------------ | ------------------------------------------ |
| `ELARA_FREE`       | Scene of Elara reuniting with her parents. |
| `ELARA_MURDER`     | Scene of Elara crying in a jail cell bed.  |
| `ELARA_ACCOMPLICE` | Scene of Elara crying in a jail cell bed.  |

All Elara outcome branches converge at `POST_TRIGGER_ENDING_2_ELARA_$`.

#### Kae Outcomes (`TRIGGER_ENDING_2_KAE_$`)

| Precondition(s)                                                                  | Variant                   | Outcome Scene                                       |
| -------------------------------------------------------------------------------- | ------------------------- | --------------------------------------------------- |
| `KAE_GUN_POSSESSION [OR] KAE_ACCOMPLICE [OR] ELARA_ACCOMPLICE [OR] ELARA_MURDER` | `TRIGGER_ENDING_2_KAE_00` | Kae emotionally devastated, screaming through bars. |
| `KAE_MURDER`                                                                     | `TRIGGER_ENDING_2_KAE_01` | Kae calm, accepting look.                           |

All Kae outcome branches converge at `POST_TRIGGER_ENDING_2_KAE_$`.

---

### 5D — Final Ending Flow

```
POST_TRIGGER_ENDING_2_KAE_$
    └─► TRIGGER_ENDING_SEQUENCE_03
        └─► POST_TRIGGER_ENDING_SEQUENCE_03
            ├─► TRIGGER_ENDING_2_KAE_00 (if KAE_GUN_POSSESSION / KAE_ACCOMPLICE / ELARA_ACCOMPLICE / ELARA_MURDER)
            └─► TRIGGER_ENDING_2_KAE_01 (if KAE_MURDER)
                └─► POST_TRIGGER_ENDING_2_KAE_$
                    └─► MILLER_ENDING_DIALOGUE
                        ├─► POST_MILLER_ENDING_DIALOGUE
                        └─► ENDING_SEQUENCE_COMPLETE
                            └─► TRIGGER_CREDITS_ROLL
```

---

### 5E — Special / Side Endings

These are terminal branches that bypass the main conviction flow entirely.

| Trigger                      | Condition(s)                                                            | Result                                                                                                                  |
| ---------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| `TRIGGER_ENDING_GETS_FIRED`  | `NOT_ENOUGH_EVIDENCE` + (`DREAM_EXPERIENCED [OR] RAN_OUT_OF_TIME`)      | Detective walks away. Dialogue: *"Maybe becoming a private detective might be the best for me…"*                        |
| `TRIGGER_ENDING_GETS_KILLED` | *(Ambiguous from XML — full precondition chain not resolved in source)* | Detective collapses, heartbeat stops, screen blurs to black. Dialogue: *"Now I just have to wait in peace."*            |
| `MILLER_TIMEOUT_SEQUENCE`    | `REACHED_36_HOURS_LIMIT` fires                                          | Subroutine pointer. Sets `RAN_OUT_OF_TIME`. Feeds into `TRIGGER_ENDING_GETS_FIRED` if `NOT_ENOUGH_EVIDENCE` also holds. |

---

### 5F — Conviction Flags Reference Summary

| Flag                    | Description                                                           |
| ----------------------- | --------------------------------------------------------------------- |
| `ELARA_FREE`            | Elara is cleared of all charges.                                      |
| `ELARA_MURDER`          | Elara convicted of murder.                                            |
| `ELARA_ACCOMPLICE`      | Elara convicted as accomplice.                                        |
| `KAE_MURDER`            | Kae convicted of murder.                                              |
| `KAE_GUN_POSSESSION`    | Kae convicted of illegal gun possession.                              |
| `KAE_ACCOMPLICE`        | Kae convicted as accomplice.                                          |
| `CONFESSION_TAPE`       | Confession tape was presented during confrontation.                   |
| `NO_CONFESSION_TAPE`    | Confrontation proceeded without confession tape.                      |
| `SHOWN_CONFESSION_TAPE` | Tape was shown during Elara's reaction in Ending Phase 1.             |
| `SHOWN_E4-TRACE`        | Mud trace analysis was shown during Kae's reaction in Ending Phase 1. |

---

*Document generated from `Diagram.xml` and `Codebase.txt`. Ambiguous nodes are explicitly marked. No connections have been inferred where source/target IDs were unresolved or null.*

---

This document outlines the core architecture, interaction loops, user interface logic, and audiovisual standards for a minimalist, logic-driven isometric detective game.

---

## 1. Core Architecture & Navigation

- **Perspective:** Fixed Isometric (Orthographic) at a 45-degree angle.

- **Movement (Hybrid System):** Navigation is performed via free-form **WASD movement**, while interaction requires both **physical proximity** and **deliberate mouse selection**.

- **Decoupling Rule:** The "Brain" (Logic IDs) is strictly separated from the "Body" (3D Visuals). Clicking a 3D object sends a `UniqueIdentifier` to the logic scripts, ensuring 3D visual assets can be swapped without breaking the underlying game state.

### 1.1 Isometric WASD Movement Rules

To resolve the "Diagonal Disconnect" common in isometric views, movement mapping is skewed by a 45-degree rotation matrix:

- **Vertical (W/S):** Moves the character along the screen's vertical axis (World Z-diagonal).

- **Horizontal (A/D):** Moves the character along the screen's horizontal axis (World X-diagonal).

- **Rotation:** The character model performs a soft `Slerp` rotation to face the direction of travel. When interacting, the character automatically rotates to face the target object.

### 1.2 Minimalist Camera Logic

The camera acts as a "Lazy Follower," never snapping hard to the detective’s position.

- **Dead-Zone:** The detective can move within a small central rectangle before the camera begins to pan.

- **Smooth Damp:** Camera movement uses `Vector3.SmoothDamp` to prevent motion sickness.

- **Interactive Offset:** During an active interaction, the camera shifts its focal point to a position between the Detective and the target object, creating a "shared space."

---

## 2. Interaction Archetypes & Sequences

Every interactable object falls into one of three primary archetypes.

| **Archetype**      | **Description**                                                                                                                                              | **Manifest Examples**                 |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------- |
| **The Transition** | Clicking a door box teleports the player, updates the `GLOBAL_ROOM_STATE`, and handles "Fog of War" (hiding/showing room geometry upon first entry).         | `Door_ER`, `Door_LR`, `Door_OR`       |
| **The Inquiry**    | Clicking a character zooms the camera slightly on them, opens the Dialogue UI, and loads all related logic.                                                  | `Miller`, `Julian`, `Kaelen`, `Elara` |
| **The Inspection** | Clicking specific objects switches the camera to a fixed 1st-person perspective and displays the appropriate UI window (e.g., Computer UI or Document Mode). | `SlavicTVMonitor_ER`, `Door_LR`       |

### 2.1 Layered Interaction Sequence

When a player intends to examine a world object, the following sequence must trigger:

1. **Physical Proximity:** The Detective must be within the Interaction Threshold (Default: 3.0 Units). If out of range, the object is inert to mouse input.

2. **Visual "Vibe" Pulse:** Hovering over a valid, in-range object activates a Rim-Light Pulse (Fresnel Effect), providing feedback that it is reachable.

3. **Camera Focus:** On click, the camera performs a 15% smooth zoom toward the target (or changes to a 1st-person view).

4. **Observation Pop-Up (Pre-Dialogue):** The Interaction Window slides in. Instead of showing buttons immediately, it displays a single block of text representing the Detective’s immediate observation (e.g., _"The detective smells like stale coffee..."_).

5. **Dialogue Initiation:** The player must click "Continue" or press Space/Enter to acknowledge the observation. Only then does the UI populate with the interaction choices.

### 2.2 Sensory Feedback Hierarchy

| **Interaction Stage**     | **Visual Feedback**              | **Audio Feedback**                          |
| ------------------------- | -------------------------------- | ------------------------------------------- |
| **Hover (In-Range)**      | Object Rim-Glow (White/Gold)     | Subtle High-Frequency "Hiss"                |
| **Click (First Contact)** | Camera Focus Shift + Zoom        | Mechanical "Click" or Paper Rustle          |
| **Observation Phase**     | Text fades in/out in World-Space | Low-priority ambient "Logic" cue            |
| **State Rejection**       | Object pulses Red                | Muted "Thud" (Indicates locked/unavailable) |

---

## 3. Audiovisual Standards & Implementation

### 3.1 3D & Animation Standards

- **3D Geometry:** Room architecture is built as simple shells in Blender, traced over the environment plan.

- **Visual Style:** "Solid Color" method. No textures/complex UV unwrapping. Materials use simple Albedo colors to denote roles (e.g., Blue = Examine, Green = Transition).

- **Physics:** Interaction relies purely on Box Colliders (Unity Primitives) for bug-free clicking. Mesh colliders are strictly avoided.

- **Animation (State-Based):** Characters use a "snap-to-pose" system. Logic triggers call `animator.Play()` directly. Required poses: `Idle_Standing`, `Idle_Sitting`, `Falling`, `Down_Idle`.

### 3.2 Workflow Rules

- **Object Naming:** Every interactive 3D object MUST share the exact ID name found in the `state_machine_reference.md`.

- **Blender Export:** Always "Apply All Transforms" and check "Apply Transform" in the FBX export settings to prevent Unity rotation issues.

- **Manager Context:** The Scene Manifest Generator script must always include "Manager" and "System" objects (e.g., `GameManager`, `NarrativeStateManager`).

### 3.3 Scene-to-Logic Mapping

- **Evidence Room (Room 7):**
  
  - `PoliceFolder_ER` -> Triggers `CASE_FOLDER_ACQUIRED` logic.
  
  - `SlavicTVMonitor_ER` -> Initiates 1st-person Computer UI.
  
  - `CassetteTape` objects -> Disappear on click and add `Tape_ID` to `SlotManager`.

- **Corridor (Room 2):** Standard navigation door boxes linking all other rooms.

- **Interrogation Room (Room 4):** Characters (`Julian`, `Kaelen`, `Elara`) -> Loads `STATE_EXPLORING_INTERROGATION_ROOM`.

---

## 4. UI, Inventory, & Case Management

### 4.1 Document View Mode (The "Dossier" Interface)

When interacting with a significant report, the game enters a High-Fidelity View Mode.

- **Analog Movement:** Click and drag the mouse to move the document (mimicking paper on a desk).

- **Zooming:** Scroll-wheel zooms into specific paragraphs. Zooming dynamically decreases drag sensitivity for precision.

- **Paging:** Hotzones on the left/right edges (or A/D keys) trigger page flips.

- **Audiovisual Cues:** The background blurs or shifts to a dark desk texture. Audio includes sliding sounds for zoom and crisp paper rustles for paging.

### 4.2 Inventory Organization & Representation

Evidence is represented in two primary ways:

1. **The "Card" (Grid View):** A clean, squared icon with a small representative image and title (e.g., `E13 - Psychiatric Medication`) for easy identification and equipping.

2. **The "Detailed/Highlighted Form":** Expanding a card shows equipping options (Slot A or B), the sticky note, a full view of the report (with pagination if applicable), and an `Inspect` button to launch Document View Mode.

### 4.3 The Case Management System (Folder Architecture)

The UI features a full-screen, tab-based navigation bar (`INVENTORY | STARTER FOLDER | CASE FOLDER #1 | CASE FOLDER #2 | NEW FOLDER +`).

- **Manual Sorting:** Players drag and drop evidence cards from the master inventory grid (right) into the Folder Container (left).

- **Customization:** Players can rename folders (e.g., "Julian's Lies") and maintain up to 10 active folders.

- **Sticky Notes:** Every evidence item has an editable text field (Sticky Note) for the player to write deductions. This is a visual aid only and does not affect backend logic.

- **Dialogue Integration:** During conversations, the equipped evidence is persistently displayed on the left.

- **Quick Evidence Menu (Tactical Overlay):** Clicking an active slot mid-dialogue opens a condensed overlay of the current folder, allowing the player to quickly pivot equipped evidence (via drag or click) or use numeric keys (1-0) to swap folders without breaking the interrogation flow.

---

## 5. UI Architecture & Unity Implementation Mapping

Based on the Figma mockups, the UI is modular and component-driven, structured as follows:

- **Dialogue & Slot UI (`UI_DialogueManager` & `UI_SlotPanel`):** Screen is split. Persistent Slots (A & B) remain on the left. The Narrative Feed (Inquiry, Questions) scrolls on the right. Utilizes keyboard QoL navigation (`[Q] SWITCH MODE`, `[X] END CONVERSATION`).

- **Folder Desk View (`UI_DropZone` & `UI_DraggableItem`):** Uses Unity's drag-and-drop interfaces (`IBeginDragHandler`, `IDragHandler`). Moving an item from the grid to the left container updates the underlying `SlotManager` list.

- **Evidence Grid Layout:** The right-side inventory relies heavily on Unity's `GridLayoutGroup` to automatically organize instantiated Evidence Card prefabs into neat rows/columns.

- **Document Viewer (`UI_DocumentViewer`):** Implemented using Unity's `ScrollRect` component (movement set to Unrestricted) to allow fluid click-and-drag panning over large UI textures.

- **UI State Machine:** Panels are managed via `CanvasGroup` components. Instead of destroying/instantiating UI elements constantly, the system alters the `Alpha`, `Interactable`, and `BlocksRaycasts` properties to switch between states (e.g., `UI_STATE_DIALOGUE`, `UI_STATE_DESK_MANAGER`, `UI_STATE_DOCUMENT_INSPECT`).

---

The prototype can be understood as a **time-bounded investigative experience** in which the player explores a space, collects and interprets evidence, chooses how to use that evidence in conversations, and gradually changes the narrative world through their decisions. Rather than treating dialogue, evidence, time, world interaction, and UI as separate features, the prototype makes them interdependent parts of one investigative loop. 

## Overall prototype loop

At the highest level, the player repeatedly moves through this cycle:

\[
\text{Explore} \rightarrow \text{Find evidence} \rightarrow \text{Organise evidence} \rightarrow \text{Question characters} \rightarrow \text{Create consequences} \rightarrow \text{Unlock new possibilities}
\]

The player is not simply selecting prewritten dialogue options. They are asked to make interpretive decisions: what evidence matters, which pieces belong together, when to present them, whom to confront, and whether to spend limited time pursuing one lead rather than another.

The prototype therefore frames investigation as a process of **reading, connecting, and testing meanings**. Evidence is not automatically meaningful; it becomes meaningful through the player’s decision to bring it into a particular conversation or situation.

The systems also preserve the consequences of those decisions. Characters remember conversations, dialogue paths can progress or break, evidence can unlock new material, narrative flags alter world access and character availability, and the passing clock puts pressure on the entire process.

## Dialogue and narrative

The Dialogue & Narrative System is the core system through which the player turns investigative interpretation into story progression.

Instead of dialogue functioning only as exposition, conversations are designed as investigative encounters. The player approaches a character, chooses whether to make an inquiry or confrontation, and then uses selected evidence to determine what questions become available. The conversation is therefore shaped by what the player knows, what they have equipped, what they have already asked, and the current state of the narrative.

### Evidence-led questioning

The system treats evidence as a conversational instrument. A piece of evidence can open a question, support a line of inquiry, challenge a character’s account, or become one part of a larger logical argument.

This creates a meaningful difference between:

- **Inquiry**, where the player investigates, probes, or seeks clarification.
- **Confrontation**, where the player uses evidence more directly to pressure, expose, or challenge a character.
- **Logic chains**, where several pieces of evidence and several exchanges form a structured argumentative progression.
- **Standalone interactions**, where a particular evidence item produces a specific, more self-contained conversational response.

The prototype evaluates the evidence currently selected by the player and uses that selection to determine which authored questions can be surfaced. This supports the central fantasy of detective work: the player is not given the conclusion, but is asked to decide what to present and why it matters.

### Character memory and trust

Each relevant character has their own evolving conversational memory. The prototype records which dialogue material has been used, which questions have already been asked, whether a conversation took place within a logic chain, and what evidence was involved. It also keeps a conversation history that can later be revisited in the archive.

This means interactions can feel cumulative rather than disposable. The player’s previous choices matter because the game can avoid treating every conversation as if it were happening for the first time.

The system also introduces **patience** as a social and pacing mechanism. If the player repeatedly presents unsuitable or poorly matched evidence, the character’s patience can decrease. Low patience can trigger narrative consequences, and repeated mistakes can interrupt an ongoing reasoning chain.

This makes incorrect evidence use more interesting than a simple “wrong answer” state. It becomes a social cost: the player risks damaging the conversation, losing momentum, or making a character less willing to cooperate.

### Narrative consequences

Dialogue outcomes do not stay inside the conversation interface. They can set narrative flags that affect the wider prototype:

- A character may become available, move into a room, or leave it.
- A world object or door may become accessible.
- A new interaction may become possible.
- A character reaction or animation may play.
- A logic chain may be suspended, resumed, reset, or revived.
- A slip event may reveal a contradiction, involuntary reaction, or important narrative rupture.

The narrative state system acts as the prototype’s shared memory of these developments. It allows the player’s investigative actions to produce persistent changes across dialogue, evidence access, world conditions, character behaviour, and final outcomes.

### Why it matters

Conceptually, the dialogue system makes the narrative **participatory**. The player does not just receive a plot; they build their route through it by selecting evidence, testing hypotheses, and managing interpersonal pressure.

A useful way to describe it is:

> The dialogue system transforms evidence from collectible information into an argumentative resource. Players advance the narrative by deciding how and when to use what they have discovered.

***

## Evidence and inventory

The Evidence & Inventory System gives the player the material basis for investigation. It governs how evidence is discovered, acquired, stored, inspected, read, organised, selected, and ultimately used in dialogue or evidence-processing situations.

This system is not merely an inventory in the conventional game-design sense. Its main purpose is to support **interpretation and reasoning**.

### Evidence as an investigative resource

Each evidence item has an identity, a name, and presentation material that lets it be shown as a distinct object or document. The player can collect different forms of evidence, including ordinary evidence and access tapes associated with the computer-terminal subsystem. The prototype distinguishes between the definition of an item and the player’s changing relationship to it: whether it has been acquired, seen, placed in a folder, equipped, or made relevant through a narrative development.

This distinction is important because it supports a sense of investigative accumulation. The player’s collection becomes an evolving representation of what they have discovered.

### Organisation, selection, and interpretation

The player can organise evidence into folders and temporarily equip up to two pieces of evidence in dedicated slots. These slots create a deliberate moment of selection: before questioning a character or processing evidence, the player must decide which items to bring forward.

That design supports several ideas at once:

- The player has to review their findings rather than merely collect them.
- Evidence can be considered in relation to other evidence.
- The player’s selected combination communicates an investigative hypothesis.
- Dialogue becomes dependent on preparation, not just immediate choice.
- The player can change focus between different possible leads.

The two-slot structure is especially important because it allows the prototype to represent a relationship between pieces of evidence. It suggests comparison, contradiction, corroboration, cause and effect, or a more complex argument—rather than treating each item as an isolated key. 

### Modes of engaging with evidence

The prototype offers several ways for evidence to be encountered and understood:

| Evidence activity   | Player purpose                                                      |
| ------------------- | ------------------------------------------------------------------- |
| Collecting          | Bringing a clue into the investigation                              |
| Inventory browsing  | Reviewing everything currently acquired                             |
| Folder organisation | Grouping material around a lead, subject, or interpretation         |
| Equipping           | Choosing evidence for immediate use                                 |
| Inspection          | Looking more closely at an item                                     |
| Reading             | Engaging with textual or document-based material                    |
| Terminal processing | Using a diegetic interface to combine access materials and evidence |
| Dialogue use        | Presenting selected evidence to a character                         |
| Archive review      | Revisiting how evidence was used in past conversations              |

The computer terminal extends this system into the world. It acts as a diegetic evidence-processing space where the player can use access tapes, load selected evidence, submit a request, and potentially unlock new material or narrative possibilities. It reinforces the idea that investigation involves procedures and interpretation, rather than simply clicking an item to reveal its answer.

### Evidence and player agency

The evidence system provides a form of agency that is not based on reflexes or combat skill. The player’s agency comes from interpretation:

- What should I examine?
- What belongs together?
- What am I trying to prove?
- Which person should I question?
- Is this evidence relevant now, or should I save it for later?
- Do I have enough information to confront someone?

This is one of the clearest ways the prototype supports a detective-game identity. The player’s progress is tied to making connections between discovered information and narrative opportunities.

***

## Time and pacing

The Time System & Pacing System gives the investigation urgency, structure, and consequence. It turns time into a resource that the player must consider while exploring, gathering evidence, managing relationships, and deciding which narrative paths to pursue.

The prototype’s clock is not only a visual timer. It functions as a framework for pacing the investigation and communicating that the player cannot pursue every possibility indefinitely.

### The finite investigation window

The player is given a remaining amount of in-game time, presented through the Free Roam HUD as:

- A diegetic wall-clock time.
- A countdown showing the remaining investigation period.
- A visual progress bar.
- Explicit states such as running, paused, warning, and expired.

The clock interface makes time visible during exploration rather than hiding it in a menu. As time runs low, the visual feedback changes to communicate increasing pressure; when time expires, the system can lead into narrative consequences.

This makes the player aware that every action has an opportunity cost. Spending time on one room, one evidence item, one conversation, or one line of questioning can mean losing the chance to pursue another.

### Time as narrative pressure

The system becomes more meaningful because it is connected to the rest of the prototype:

- Time can be advanced through dedicated interactions or locations.
- Narrative events can be triggered by temporal progress.
- The availability of characters, rooms, sequences, and endings can depend on the current state of the investigation.
- Some evidence may be pending or tied to a waiting period.
- Character patience can recover through a cooldown process, linking social tension to the passage of time.
- The final outcome can depend on what the player achieved before the available time expired.

This transforms time from an external punishment into a design tool that shapes the player’s reasoning. The player must choose between acting immediately, gathering more support, repairing a strained conversation, investigating a different lead, or advancing time to create new conditions.

### Social pacing

A particularly valuable aspect of the prototype is that pacing is not only temporal; it is also interpersonal.

The player must manage character patience and their own use of evidence. Presenting inappropriate evidence can weaken a conversation, while waiting or allowing time to pass can create space for recovery. In this sense, time is connected to the emotional rhythm of the investigation: urgency pushes the player forward, while patience encourages careful judgement.

### Why it matters

The system supports a central tension in investigative storytelling:

> A good investigator needs time to understand the evidence, but the case does not wait for complete certainty.

This makes the player’s route through the prototype meaningful. They are not expected to exhaustively consume all available content. Instead, they make prioritisation decisions under uncertainty.

***

## World interaction

The World Interaction System turns the investigation into something spatial and embodied. It allows the player to move through the environment, approach people and objects, collect evidence, operate devices, access rooms, encounter blocked paths, and see the physical consequences of narrative progress.

Without this system, the prototype could function as a menu-based dialogue and evidence game. With it, investigation becomes situated in a world.

### Exploration as discovery

The player navigates an isometric environment and interacts with nearby elements through proximity-based prompts. Characters, pickups, terminals, doors, documents, suspect cells, and other world objects can each invite different forms of interaction.

This is important because it makes evidence feel discovered rather than simply awarded. A clue exists in a place, becomes available under certain narrative conditions, and has to be approached or accessed by the player.

The world therefore communicates information through placement, access, timing, and environmental change—not only through text.

### The environment responds to narrative progress

World interactions are often connected to the narrative-state system. This means that player actions can alter the space in understandable ways:

- A door can become unlocked once a condition has been met.
- A terminal can remain inaccessible until a relevant narrative flag is active.
- A tape or evidence item can be gated until the player reaches a particular point in the story.
- Characters can enter, leave, or become available in a specific room.
- A suspect may be seated in an interrogation setting only after the relevant narrative event.
- A scene transition can move the player into a new phase of the investigation.

For example, character presence is not treated as static decoration. Narrative developments can bring a character into the interrogation room, seat them there, or remove them from that context. The physical world thus reflects the changing state of the case.

### World objects as narrative interfaces

Objects in the environment are not simply obstacles or decorative props. They act as interfaces between player intent and narrative consequence.

A computer terminal, a locked door, a cell, a readable object, or a piece of evidence can all be understood as a different kind of narrative interface:

| World element         | Narrative role                                  |
| --------------------- | ----------------------------------------------- |
| Evidence pickup       | Introduces a new clue or line of reasoning      |
| Character             | Enables investigation through dialogue          |
| Door or room entrance | Controls spatial progression and access         |
| Computer terminal     | Supports diegetic evidence processing           |
| Readable object       | Provides contextual or interpretive information |
| Suspect cell          | Supports consequential end-stage interactions   |
| Time-advance point    | Lets the player choose to move the case forward |

This makes the environment part of the story logic. The player learns not only from what characters say, but from what the world permits, withholds, reveals, and changes.

### Why it matters

The World Interaction System grounds abstract narrative systems in physical action. It makes the player feel that they are inhabiting an investigative space rather than navigating an abstract decision tree.

A concise description would be:

> The world acts as a spatial expression of the investigation’s state: as the player discovers evidence and changes the narrative, new people, objects, spaces, and actions become available.

***

## UI and user experience

The UI System & User Experience layer makes the prototype’s complex investigative state understandable and usable. It is the player-facing structure that helps them move between exploration, evidence organisation, dialogue, reading, inspection, time awareness, conversation review, and settings.

Its role is especially important because the prototype asks the player to manage multiple kinds of information at once: evidence, selected evidence, character relationships, available dialogue opportunities, past conversations, time remaining, and world access.

### Making investigation legible

The UI provides different interfaces for different cognitive tasks:

| Interface                | Main player need                                            |
| ------------------------ | ----------------------------------------------------------- |
| Free Roam HUD            | Staying oriented during exploration                         |
| Inventory                | Reviewing acquired evidence                                 |
| Evidence folders         | Organising material by lead or interpretation               |
| Quick menu               | Rapidly equipping evidence while remaining in the game flow |
| Dialogue panel           | Choosing questions and following conversations              |
| Dialogue quick menu      | Managing evidence within conversation                       |
| Inspect mode             | Examining evidence more closely                             |
| Read mode                | Reading documents and written material                      |
| Archive                  | Reviewing previous conversations and consequences           |
| Computer terminal        | Processing evidence through a diegetic interface            |
| Time-advance panel       | Deliberately moving time forward                            |
| Pause and settings menus | Managing the broader play session                           |

This is not redundant interface design. Each screen supports a different kind of player activity: active decision-making, reflection, preparation, recall, or orientation.

### Continuity between interfaces

The UI is visually and interactively connected through recurring elements:

- Evidence appears as recognisable cards across inventory, folders, dialogue menus, terminal interfaces, and free-roam quick access.
- The same drag-and-drop interaction model is used to move evidence into slots.
- Equipped evidence remains visible in the exploration HUD.
- The inventory can indicate when newly acquired evidence has not yet been reviewed.
- Modal panels temporarily shift the player out of free-roam interaction, preventing accidental world actions while the player is reading, organising, or choosing.
- The archive lets the player revisit dialogue history and see which evidence was equipped during a past session.

This continuity is important for usability. The player does not have to relearn how evidence works every time it appears in a new context.

### UI as a reflective tool

Several interfaces do more than enable actions; they support reflection.

The archive allows the player to reconstruct prior conversations, including questions, responses, evidence used, out-of-range attempts, and slip events. The inventory, folders, inspect mode, and read mode allow the player to pause, revisit, and reinterpret material before taking further action. 

These reflective interfaces are especially aligned with the prototype’s investigative intent. They encourage the player to think back over prior information rather than rely solely on memory or linear progression.

### Diegetic and non-diegetic balance

The UI also balances practical game feedback with narrative atmosphere.

The Free Roam HUD gives the player essential information about time, equipped evidence, inventory access, folders, and archives. At the same time, the computer terminal turns a functional evidence-management process into a world object with its own visual identity and interaction context.

This combination supports the prototype’s atmosphere: some information is made immediately accessible for usability, while other actions are embedded into the fiction to make investigation feel procedural and situated.

### Why it matters

The UI is not only a technical presentation layer. It is the system that makes the player’s thinking visible:

> It externalises the investigation by showing what the player knows, what they are currently considering, what has happened before, and what pressures are shaping the next decision.

***

Taken together, the five systems create a prototype where investigative play is based on **interpretation under pressure**. The player explores to gather information, organises that information into possible meanings, uses it to shape conversations, experiences consequences in the world, and does all of this within a limited temporal and social frame.

---

Data Asset Structure - Fri Sep  4 11:39:01 GMTDT 2026
------------------------------------------

Structure for: Data
==============================

|-- Data / ChainFolder.asset
|-- Data / ChainResetPackageMillerConfrontation.asset
|-- Data / Chains / ELARA / Chain_CHAIN_ELARA_BAREFOOT.asset
|-- Data / Chains / ELARA / Chain_CHAIN_ELARA_BLACKOUT.asset
|-- Data / Chains / ELARA / Chain_CHAIN_ELARA_DREAM.asset
|-- Data / Chains / ELARA / Chain_CHAIN_ELARA_FINANCIAL.asset
|-- Data / Chains / ELARA / Chain_CHAIN_ELARA_FORENSIC_TRACE.asset
|-- Data / Chains / ELARA / Chain_CHAIN_ELARA_GREENMARKET_CONFRONTATION.asset
|-- Data / Chains / ELARA / Chain_CHAIN_ELARA_GREENWAY_MARKET.asset
|-- Data / Chains / ELARA / Chain_CHAIN_ELARA_GUN.asset
|-- Data / Chains / ELARA / Chain_CHAIN_ELARA_GUN_CONFRONTATION.asset
|-- Data / Chains / ELARA / Chain_CHAIN_ELARA_HEIGHT_SHOOTER.asset
|-- Data / Chains / ELARA / Chain_CHAIN_ELARA_HOODIE.asset
|-- Data / Chains / ELARA / Chain_CHAIN_ELARA_KAE_CRIMES_AREA.asset
|-- Data / Chains / ELARA / Chain_CHAIN_ELARA_KAE_PRIOR_CRIMINAL.asset
|-- Data / Chains / ELARA / Chain_CHAIN_ELARA_MEDICATION_WITHDRAWAL.asset
|-- Data / Chains / ELARA / Chain_CHAIN_ELARA_MOON_DRUG.asset
|-- Data / Chains / ELARA / Chain_CHAIN_ELARA_PRESENCE.asset
|-- Data / Chains / ELARA / Chain_CHAIN_ELARA_PRIOR_TARGET.asset
|-- Data / Chains / ELARA / Chain_CHAIN_ELARA_SLEEPWALKING.asset
|-- Data / Chains / ELARA / Chain_CHAIN_ELARA_TWO_SHAPES.asset
|-- Data / Chains / ELARA / Chain_CHAIN_ELARA_TWO_SHAPES_FALSE_ALIBI.asset
|-- Data / Chains / ELARA / Chain_CHAIN_ELARA_TWO_SHAPES_HOODIE.asset
|-- Data / Chains / ENDINGS / MILLER_ANGRY_CONFRONTATION_EXIT.asset
|-- Data / Chains / ENDINGS / MILLER_CONFRONTATION_00.asset
|-- Data / Chains / ENDINGS / MILLER_CONFRONTATION_01.asset
|-- Data / Chains / ENDINGS / MILLER_CONFRONTATION_01_EXIT.asset
|-- Data / Chains / ENDINGS / MILLER_STEP1_SHOOTER.asset
|-- Data / Chains / ENDINGS / MILLER_STEP2_ELARA_MOTIVE.asset
|-- Data / Chains / ENDINGS / MILLER_STEP2_KAE_MOTIVE.asset
|-- Data / Chains / ENDINGS / MILLER_STEP3_ELARA_INVOLVEMENT.asset
|-- Data / Chains / ENDINGS / MILLER_STEP3_KAE_INVOLVEMENT.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_AUGUST_INCIDENT.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_CONFESSION.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_CONFESSION_2.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_E4_TRACE.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_ELARA_BAREFOOT.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_ELARA_BAREFOOT_FALSE_ALIBI.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_ELARA_BAREFOOT_HOODIE.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_ELARA_BLACKOUT.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_ELARA_MEDICATION.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_ELARA_SLEEPWALKING.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_FALSE_ALIBI.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_FINANCIAL.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_FOOTPRINTS.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_GUN.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_GUN_BULLET.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_HEIGHT_SHOOTER.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_HOODIE.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_KILLER.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_KILLER_ARTHUR_PRIOR_TARGET.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_KILLER_CRIMINAL.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_KILLER_HOODIE.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_LIED.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_MOON.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_MOON_HISTORY.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_PRESENCE.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_PRIOR_INCIDENTS.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_TWO_SHAPES.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_TWO_SHAPES_ARTHUR_PRIOR_TARGET.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_TWO_SHAPES_FALSE_ALIBI.asset
|-- Data / Chains / KAE / Chain_CHAIN_KAE_TWO_SHAPES_HOODIE.asset
|-- Data / Chains / LogicChainDatabase.asset
|-- Data / Chains / SuppressionRules / ELARA_GUN_REACTION_CONFRONTATION.asset
|-- Data / Chains / SuppressionRules / ELARA_GUN_REACTION_INQUIRY.asset
|-- Data / Computer / ComputerUnlockDatabase.asset
|-- Data / Computer / Rules / Rule_CSU_ARE_E5.asset
|-- Data / Computer / Rules / Rule_CSU_ARK_E6.asset
|-- Data / Computer / Rules / Rule_CSU_E13R.asset
|-- Data / Computer / Rules / Rule_CSU_E15R.asset
|-- Data / Computer / Rules / Rule_CSU_N1.asset
|-- Data / Computer / Rules / Rule_CSU_PE_E5.asset
|-- Data / Computer / Rules / Rule_CSU_PK_E6.asset
|-- Data / Computer / Rules / Rule_CSU_X2.asset
|-- Data / Computer / Rules / Rule_CSU_X4.asset
|-- Data / Computer / Rules / Rule_EC_ARE_E23.asset
|-- Data / Computer / Rules / Rule_EC_E10R.asset
|-- Data / Computer / Rules / Rule_EC_E11.asset
|-- Data / Computer / Rules / Rule_EC_E17R.asset
|-- Data / Computer / Rules / Rule_EC_E18R.asset
|-- Data / Computer / Rules / Rule_EC_E1R.asset
|-- Data / Computer / Rules / Rule_EC_E3R.asset
|-- Data / Computer / Rules / Rule_EC_E8R_E8-A.asset
|-- Data / Computer / Rules / Rule_EC_E9.asset
|-- Data / Computer / Rules / Rule_EC_GCAL01.asset
|-- Data / Computer / Rules / Rule_EC_PA_E22.asset
|-- Data / Computer / Rules / Rule_EC_PE_E23.asset
|-- Data / Computer / Rules / Rule_EC_PK_E19.asset
|-- Data / Computer / Rules / Rule_FL_ARE_E5.asset
|-- Data / Computer / Rules / Rule_FL_ARK_E6.asset
|-- Data / Computer / Rules / Rule_FL_E21R.asset
|-- Data / Computer / Rules / Rule_FL_E2R.asset
|-- Data / Computer / Rules / Rule_FL_E3R.asset
|-- Data / Computer / Rules / Rule_FL_PE_E5.asset
|-- Data / Computer / Rules / Rule_FL_PK_E6.asset
|-- Data / Computer / Rules / Rule_MU_ARE_E4.asset
|-- Data / Computer / Rules / Rule_MU_ARK_E12.asset
|-- Data / Computer / Rules / Rule_MU_E4C.asset
|-- Data / Computer / Rules / Rule_MU_PA_E16.asset
|-- Data / Computer / Rules / Rule_MU_PE_E4.asset
|-- Data / Computer / Rules / Rule_MU_PK_E12.asset
|-- Data / Computer / Rules / UnlockRule_.asset
|-- Data / Ending Paths / 01_ENDING_KAE_MURDER_ELARA_FREE.asset
|-- Data / Ending Paths / 02_ENDING_KAE_MURDER_ELARA_ACCOMPLICE.asset
|-- Data / Ending Paths / 03_ENDING_ELARA_MURDER_KAE_ACCOMPLICE.asset
|-- Data / Ending Paths / 04_ENDING_ELARA_MURDER_KAE_GUN_ONLY.asset
|-- Data / Ending Paths / DialogueOverrideData / KAE_REACTION_ELARA_SHOOTER_KAE_PRESSURED.asset
|-- Data / EndingFolder.asset
|-- Data / Evidence / Evidence_AI.asset
|-- Data / Evidence / Evidence_ARE.asset
|-- Data / Evidence / Evidence_ARK.asset
|-- Data / Evidence / Evidence_AV.asset
|-- Data / Evidence / Evidence_CASE-19.asset
|-- Data / Evidence / Evidence_CASE-47.asset
|-- Data / Evidence / Evidence_CONF_TAPE.asset
|-- Data / Evidence / Evidence_CSU.asset
|-- Data / Evidence / Evidence_E1.asset
|-- Data / Evidence / Evidence_E10-B.asset
|-- Data / Evidence / Evidence_E10.asset
|-- Data / Evidence / Evidence_E10R.asset
|-- Data / Evidence / Evidence_E11R.asset
|-- Data / Evidence / Evidence_E12R.asset
|-- Data / Evidence / Evidence_E13.asset
|-- Data / Evidence / Evidence_E13R.asset
|-- Data / Evidence / Evidence_E14R.asset
|-- Data / Evidence / Evidence_E15.asset
|-- Data / Evidence / Evidence_E15R.asset
|-- Data / Evidence / Evidence_E16R.asset
|-- Data / Evidence / Evidence_E17.asset
|-- Data / Evidence / Evidence_E17R.asset
|-- Data / Evidence / Evidence_E18.asset
|-- Data / Evidence / Evidence_E18R.asset
|-- Data / Evidence / Evidence_E19R.asset
|-- Data / Evidence / Evidence_E1R.asset
|-- Data / Evidence / Evidence_E2.asset
|-- Data / Evidence / Evidence_E21.asset
|-- Data / Evidence / Evidence_E21R.asset
|-- Data / Evidence / Evidence_E22R.asset
|-- Data / Evidence / Evidence_E23R.asset
|-- Data / Evidence / Evidence_E2R.asset
|-- Data / Evidence / Evidence_E3.asset
|-- Data / Evidence / Evidence_E3R.asset
|-- Data / Evidence / Evidence_E4-C.asset
|-- Data / Evidence / Evidence_E4-TRACE.asset
|-- Data / Evidence / Evidence_E4R.asset
|-- Data / Evidence / Evidence_E5R.asset
|-- Data / Evidence / Evidence_E6R.asset
|-- Data / Evidence / Evidence_E7R.asset
|-- Data / Evidence / Evidence_E8-A.asset
|-- Data / Evidence / Evidence_E8R.asset
|-- Data / Evidence / Evidence_E9R.asset
|-- Data / Evidence / Evidence_EC.asset
|-- Data / Evidence / Evidence_F1.asset
|-- Data / Evidence / Evidence_FL.asset
|-- Data / Evidence / Evidence_IR.asset
|-- Data / Evidence / Evidence_KEYS.asset
|-- Data / Evidence / Evidence_L1.asset
|-- Data / Evidence / Evidence_LDN.asset
|-- Data / Evidence / Evidence_MAP.asset
|-- Data / Evidence / Evidence_MEMO.asset
|-- Data / Evidence / Evidence_MU.asset
|-- Data / Evidence / Evidence_N1.asset
|-- Data / Evidence / Evidence_PA.asset
|-- Data / Evidence / Evidence_PE.asset
|-- Data / Evidence / Evidence_PK.asset
|-- Data / Evidence / Evidence_TN.asset
|-- Data / Evidence / Evidence_X2.asset
|-- Data / Evidence / Evidence_X4.asset
|-- Data / Interactions / Elara / ELARA_AI.asset
|-- Data / Interactions / Elara / ELARA_ARE.asset
|-- Data / Interactions / Elara / ELARA_ARK.asset
|-- Data / Interactions / Elara / ELARA_AV.asset
|-- Data / Interactions / Elara / ELARA_CONF_TAPE.asset
|-- Data / Interactions / Elara / ELARA_E1.asset
|-- Data / Interactions / Elara / ELARA_E10-B.asset
|-- Data / Interactions / Elara / ELARA_E10.asset
|-- Data / Interactions / Elara / ELARA_E10R.asset
|-- Data / Interactions / Elara / ELARA_E11R.asset
|-- Data / Interactions / Elara / ELARA_E12R.asset
|-- Data / Interactions / Elara / ELARA_E13.asset
|-- Data / Interactions / Elara / ELARA_E13R.asset
|-- Data / Interactions / Elara / ELARA_E14R.asset
|-- Data / Interactions / Elara / ELARA_E15.asset
|-- Data / Interactions / Elara / ELARA_E15R.asset
|-- Data / Interactions / Elara / ELARA_E16R.asset
|-- Data / Interactions / Elara / ELARA_E17.asset
|-- Data / Interactions / Elara / ELARA_E17R.asset
|-- Data / Interactions / Elara / ELARA_E18.asset
|-- Data / Interactions / Elara / ELARA_E18R.asset
|-- Data / Interactions / Elara / ELARA_E19R.asset
|-- Data / Interactions / Elara / ELARA_E1R.asset
|-- Data / Interactions / Elara / ELARA_E2.asset
|-- Data / Interactions / Elara / ELARA_E21.asset
|-- Data / Interactions / Elara / ELARA_E21R.asset
|-- Data / Interactions / Elara / ELARA_E22R.asset
|-- Data / Interactions / Elara / ELARA_E23R.asset
|-- Data / Interactions / Elara / ELARA_E2R.asset
|-- Data / Interactions / Elara / ELARA_E3.asset
|-- Data / Interactions / Elara / ELARA_E3R.asset
|-- Data / Interactions / Elara / ELARA_E4-C.asset
|-- Data / Interactions / Elara / ELARA_E4-TRACE.asset
|-- Data / Interactions / Elara / ELARA_E4R.asset
|-- Data / Interactions / Elara / ELARA_E5R.asset
|-- Data / Interactions / Elara / ELARA_E6R.asset
|-- Data / Interactions / Elara / ELARA_E7R.asset
|-- Data / Interactions / Elara / ELARA_E8-A.asset
|-- Data / Interactions / Elara / ELARA_E8R.asset
|-- Data / Interactions / Elara / ELARA_E9R.asset
|-- Data / Interactions / Elara / ELARA_F1.asset
|-- Data / Interactions / Elara / ELARA_IR.asset
|-- Data / Interactions / Elara / ELARA_KEYS.asset
|-- Data / Interactions / Elara / ELARA_L1.asset
|-- Data / Interactions / Elara / ELARA_LDN.asset
|-- Data / Interactions / Elara / ELARA_MEMO.asset
|-- Data / Interactions / Elara / ELARA_N1.asset
|-- Data / Interactions / Elara / ELARA_PA.asset
|-- Data / Interactions / Elara / ELARA_PE.asset
|-- Data / Interactions / Elara / ELARA_PK.asset
|-- Data / Interactions / Elara / ELARA_TN.asset
|-- Data / Interactions / Elara / ELARA_X2.asset
|-- Data / Interactions / Elara / ELARA_X4.asset
|-- Data / Interactions / ENDING / MILLER_CONFRONTATION_01.asset
|-- Data / Interactions / EvidenceInteractionDatabase.asset
|-- Data / Interactions / Interaction_ PE.asset
|-- Data / Interactions / Interaction_ PK.asset
|-- Data / Interactions / Interaction_M_E14.asset
|-- Data / Interactions / Interaction_M_E4-TRACE.asset
|-- Data / Interactions / Interaction_M_E7.asset
|-- Data / Interactions / Interaction_M_F1.asset
|-- Data / Interactions / Interaction_M_L1.asset
|-- Data / Interactions / Interaction_M_LDN.asset
|-- Data / Interactions / Interaction_M_MAP.asset
|-- Data / Interactions / Interaction_M_N1.asset
|-- Data / Interactions / Kae / KAE_AI.asset
|-- Data / Interactions / Kae / KAE_ARE.asset
|-- Data / Interactions / Kae / KAE_ARK.asset
|-- Data / Interactions / Kae / KAE_AV.asset
|-- Data / Interactions / Kae / KAE_CONF_TAPE.asset
|-- Data / Interactions / Kae / KAE_E1.asset
|-- Data / Interactions / Kae / KAE_E10-B.asset
|-- Data / Interactions / Kae / KAE_E10.asset
|-- Data / Interactions / Kae / KAE_E10R.asset
|-- Data / Interactions / Kae / KAE_E11R.asset
|-- Data / Interactions / Kae / KAE_E12R.asset
|-- Data / Interactions / Kae / KAE_E13.asset
|-- Data / Interactions / Kae / KAE_E13R.asset
|-- Data / Interactions / Kae / KAE_E14R.asset
|-- Data / Interactions / Kae / KAE_E15.asset
|-- Data / Interactions / Kae / KAE_E15R.asset
|-- Data / Interactions / Kae / KAE_E16R.asset
|-- Data / Interactions / Kae / KAE_E17.asset
|-- Data / Interactions / Kae / KAE_E17R.asset
|-- Data / Interactions / Kae / KAE_E18.asset
|-- Data / Interactions / Kae / KAE_E18R.asset
|-- Data / Interactions / Kae / KAE_E19R.asset
|-- Data / Interactions / Kae / KAE_E1R.asset
|-- Data / Interactions / Kae / KAE_E2.asset
|-- Data / Interactions / Kae / KAE_E21.asset
|-- Data / Interactions / Kae / KAE_E21R.asset
|-- Data / Interactions / Kae / KAE_E22R.asset
|-- Data / Interactions / Kae / KAE_E23R.asset
|-- Data / Interactions / Kae / KAE_E2R.asset
|-- Data / Interactions / Kae / KAE_E3.asset
|-- Data / Interactions / Kae / KAE_E3R.asset
|-- Data / Interactions / Kae / KAE_E4-C.asset
|-- Data / Interactions / Kae / KAE_E4-TRACE.asset
|-- Data / Interactions / Kae / KAE_E4R.asset
|-- Data / Interactions / Kae / KAE_E5R.asset
|-- Data / Interactions / Kae / KAE_E6R.asset
|-- Data / Interactions / Kae / KAE_E7R.asset
|-- Data / Interactions / Kae / KAE_E8-A.asset
|-- Data / Interactions / Kae / KAE_E8R.asset
|-- Data / Interactions / Kae / KAE_E9R.asset
|-- Data / Interactions / Kae / KAE_F1.asset
|-- Data / Interactions / Kae / KAE_IR.asset
|-- Data / Interactions / Kae / KAE_KEYS.asset
|-- Data / Interactions / Kae / KAE_L1.asset
|-- Data / Interactions / Kae / KAE_LDN.asset
|-- Data / Interactions / Kae / KAE_MEMO.asset
|-- Data / Interactions / Kae / KAE_N1.asset
|-- Data / Interactions / Kae / KAE_PA.asset
|-- Data / Interactions / Kae / KAE_PE.asset
|-- Data / Interactions / Kae / KAE_PK.asset
|-- Data / Interactions / Kae / KAE_TN.asset
|-- Data / Interactions / Kae / KAE_X2.asset
|-- Data / Interactions / Kae / KAE_X4.asset
|-- Data / Interactions / Miller / MILLER_AI.asset
|-- Data / Interactions / Miller / MILLER_ARE.asset
|-- Data / Interactions / Miller / MILLER_ARK.asset
|-- Data / Interactions / Miller / MILLER_AV.asset
|-- Data / Interactions / Miller / MILLER_CONF_TAPE.asset
|-- Data / Interactions / Miller / MILLER_E1.asset
|-- Data / Interactions / Miller / MILLER_E10-B.asset
|-- Data / Interactions / Miller / MILLER_E10.asset
|-- Data / Interactions / Miller / MILLER_E10R.asset
|-- Data / Interactions / Miller / MILLER_E11R.asset
|-- Data / Interactions / Miller / MILLER_E12R.asset
|-- Data / Interactions / Miller / MILLER_E13.asset
|-- Data / Interactions / Miller / MILLER_E13R.asset
|-- Data / Interactions / Miller / MILLER_E14R.asset
|-- Data / Interactions / Miller / MILLER_E15.asset
|-- Data / Interactions / Miller / MILLER_E15R.asset
|-- Data / Interactions / Miller / MILLER_E16R.asset
|-- Data / Interactions / Miller / MILLER_E17.asset
|-- Data / Interactions / Miller / MILLER_E17R.asset
|-- Data / Interactions / Miller / MILLER_E18.asset
|-- Data / Interactions / Miller / MILLER_E18R.asset
|-- Data / Interactions / Miller / MILLER_E19R.asset
|-- Data / Interactions / Miller / MILLER_E1R.asset
|-- Data / Interactions / Miller / MILLER_E2.asset
|-- Data / Interactions / Miller / MILLER_E21.asset
|-- Data / Interactions / Miller / MILLER_E21R.asset
|-- Data / Interactions / Miller / MILLER_E22R.asset
|-- Data / Interactions / Miller / MILLER_E23R.asset
|-- Data / Interactions / Miller / MILLER_E2R.asset
|-- Data / Interactions / Miller / MILLER_E3.asset
|-- Data / Interactions / Miller / MILLER_E3R.asset
|-- Data / Interactions / Miller / MILLER_E4-C.asset
|-- Data / Interactions / Miller / MILLER_E4-TRACE.asset
|-- Data / Interactions / Miller / MILLER_E4R.asset
|-- Data / Interactions / Miller / MILLER_E5R.asset
|-- Data / Interactions / Miller / MILLER_E6R.asset
|-- Data / Interactions / Miller / MILLER_E7R.asset
|-- Data / Interactions / Miller / MILLER_E8-A.asset
|-- Data / Interactions / Miller / MILLER_E8R.asset
|-- Data / Interactions / Miller / MILLER_E9R.asset
|-- Data / Interactions / Miller / MILLER_F1.asset
|-- Data / Interactions / Miller / MILLER_IR.asset
|-- Data / Interactions / Miller / MILLER_KEYS.asset
|-- Data / Interactions / Miller / MILLER_L1.asset
|-- Data / Interactions / Miller / MILLER_LDN.asset
|-- Data / Interactions / Miller / MILLER_MEMO.asset
|-- Data / Interactions / Miller / MILLER_N1.asset
|-- Data / Interactions / Miller / MILLER_PA.asset
|-- Data / Interactions / Miller / MILLER_PE.asset
|-- Data / Interactions / Miller / MILLER_PK.asset
|-- Data / Interactions / Miller / MILLER_TN.asset
|-- Data / Interactions / Miller / MILLER_X2.asset
|-- Data / Interactions / Miller / MILLER_X4.asset
|-- Data / Narrative Dialogue / ELARA_LOW_PATIENCE.asset
|-- Data / Narrative Dialogue / ENDINGS / ELARA_REACTION / ELARA_REACTION_ENDING_ELARA_MURDER_KAE_ACCOMPLICE.asset
|-- Data / Narrative Dialogue / ENDINGS / ELARA_REACTION / ELARA_REACTION_ENDING_ELARA_MURDER_KAE_GUN_ONLY.asset
|-- Data / Narrative Dialogue / ENDINGS / ELARA_REACTION / ELARA_REACTION_ENDING_KAE_MURDER_ELARA_ACCOMPLICE.asset
|-- Data / Narrative Dialogue / ENDINGS / ELARA_REACTION / ELARA_REACTION_ENDING_KAE_MURDER_ELARA_FREE.asset
|-- Data / Narrative Dialogue / ENDINGS / KAE_REACTION / KAE_REACTION_ELARA_SHOOTER_KAE_PRESSURED.asset
|-- Data / Narrative Dialogue / ENDINGS / KAE_REACTION / KAE_REACTION_ENDING_ELARA_MURDER_KAE_ACCOMPLICE.asset
|-- Data / Narrative Dialogue / ENDINGS / KAE_REACTION / KAE_REACTION_ENDING_ELARA_MURDER_KAE_GUN_ONLY.asset
|-- Data / Narrative Dialogue / ENDINGS / KAE_REACTION / KAE_REACTION_ENDING_KAE_MURDER_ELARA_ACCOMPLICE.asset
|-- Data / Narrative Dialogue / ENDINGS / KAE_REACTION / KAE_REACTION_ENDING_KAE_MURDER_ELARA_FREE.asset
|-- Data / Narrative Dialogue / ENDINGS / OUTCOME / OUTCOME_ENDING_ELARA_MURDER_KAE_ACCOMPLICE.asset
|-- Data / Narrative Dialogue / ENDINGS / OUTCOME / OUTCOME_ENDING_ELARA_MURDER_KAE_GUN_ONLY.asset
|-- Data / Narrative Dialogue / ENDINGS / OUTCOME / OUTCOME_ENDING_KAE_MURDER_ELARA_ACCOMPLICE.asset
|-- Data / Narrative Dialogue / ENDINGS / OUTCOME / OUTCOME_ENDING_KAE_MURDER_ELARA_FREE.asset
|-- Data / Narrative Dialogue / ENTITY_DIALOGUE.asset
|-- Data / Narrative Dialogue / MILLER_BRIEF_00.asset
|-- Data / Narrative Dialogue / MILLER_BRIEF_01.asset
|-- Data / Narrative Dialogue / MILLER_LOW_PATIENCE.asset
|-- Data / Narrative Dialogue / MILLER_PLAYER_FIRED.asset
|-- Data / Nodes / Node_ELARA_BLACK_01.asset
|-- Data / Nodes / Node_ELARA_BLACK_02.asset
|-- Data / Nodes / Node_ELARA_BLACK_03.asset
|-- Data / Nodes / Node_ELARA_BLACK_SLIP.asset
|-- Data / Nodes / Node_ELARA_CONF_01.asset
|-- Data / Nodes / Node_ELARA_CONF_02.asset
|-- Data / Nodes / Node_ELARA_CONF_03.asset
|-- Data / Nodes / Node_ELARA_CONF_SLIP.asset
|-- Data / Nodes / Node_ELARA_PRES_01.asset
|-- Data / Nodes / Node_ELARA_PRES_02.asset
|-- Data / Nodes / Node_ELARA_PRES_03.asset
|-- Data / Nodes / Node_FA_ELARA_01.asset
|-- Data / Nodes / Node_FA_ELARA_02.asset
|-- Data / Nodes / Node_FA_ELARA_CONF.asset
|-- Data / Nodes / Node_FA_KAE_01.asset
|-- Data / Nodes / Node_FA_KAE_02.asset
|-- Data / Nodes / Node_FA_KAE_03.asset
|-- Data / Nodes / Node_FA_KAE_CONF.asset
|-- Data / Nodes / Node_FB_ELARA_01.asset
|-- Data / Nodes / Node_FB_ELARA_02.asset
|-- Data / Nodes / Node_FB_ELARA_03.asset
|-- Data / Nodes / Node_FB_ELARA_CONF.asset
|-- Data / Nodes / Node_FB_KAE_01.asset
|-- Data / Nodes / Node_FB_KAE_02.asset
|-- Data / Nodes / Node_FB_KAE_CONF.asset
|-- Data / Nodes / Node_FC_ELARA_01.asset
|-- Data / Nodes / Node_FC_ELARA_02.asset
|-- Data / Nodes / Node_FC_ELARA_03.asset
|-- Data / Nodes / Node_FC_ELARA_04.asset
|-- Data / Nodes / Node_FC_ELARA_CONF.asset
|-- Data / Nodes / Node_FC_KAE_GUN.asset
|-- Data / Nodes / Node_FD_KAE_01.asset
|-- Data / Nodes / Node_FD_KAE_02.asset
|-- Data / Nodes / Node_FD_KAE_03.asset
|-- Data / Nodes / Node_FD_KAE_04.asset
|-- Data / Nodes / Node_FD_KAE_05.asset
|-- Data / Nodes / Node_FD_KAE_CONF.asset
|-- Data / Nodes / Node_KAE_BF_01.asset
|-- Data / Nodes / Node_KAE_BF_02.asset
|-- Data / Nodes / Node_KAE_BF_03.asset
|-- Data / Nodes / Node_KAE_BF_SLIP.asset
|-- Data / Nodes / Node_KAE_GUN_01.asset
|-- Data / Nodes / Node_KAE_GUN_02.asset
|-- Data / Nodes / Node_KAE_GUN_03.asset
|-- Data / Nodes / Node_KAE_GUN_SLIP.asset
|-- Data / Nodes / Node_KAE_LIE_01.asset
|-- Data / Nodes / Node_KAE_LIE_02.asset
|-- Data / Nodes / Node_KAE_LIE_SLIP.asset
|-- Data / Nodes / Node_MILLER_EV_E14.asset
|-- Data / Nodes / Node_MILLER_EV_E7.asset
|-- Data / Nodes / Node_MILLER_EV_N1.asset
|-- Data / Nodes / Node_MILLER_EV_TRACE.asset
|-- Data / Slips / DIALOGUE / ARTHUR_PRIOR_TARGET.asset
|-- Data / Slips / DIALOGUE / BULLET_SHOT_FROM_GUN.asset
|-- Data / Slips / DIALOGUE / ELARA_AWARE_KAE_CONFESSED.asset
|-- Data / Slips / DIALOGUE / ELARA_AWARE_KAE_CRIMINAL_AREA.asset
|-- Data / Slips / DIALOGUE / ELARA_AWARE_KAE_CRIMINAL_HISTORY.asset
|-- Data / Slips / DIALOGUE / ELARA_BAREFOOT_1.asset
|-- Data / Slips / DIALOGUE / ELARA_BAREFOOT_2.asset
|-- Data / Slips / DIALOGUE / ELARA_BLACKOUT.asset
|-- Data / Slips / DIALOGUE / ELARA_DREAM.asset
|-- Data / Slips / DIALOGUE / ELARA_GUN_REACTION.asset
|-- Data / Slips / DIALOGUE / ELARA_GUN_REACTION_CONFRONTATION.asset
|-- Data / Slips / DIALOGUE / ELARA_HEIGHT_MATCH.asset
|-- Data / Slips / DIALOGUE / ELARA_KNEW_ARTHUR.asset
|-- Data / Slips / DIALOGUE / ELARA_MOON_ADDICTION.asset
|-- Data / Slips / DIALOGUE / ELARA_NOT_REMEMBERING_ARTHUR.asset
|-- Data / Slips / DIALOGUE / ELARA_NOT_USING_MEDICATION.asset
|-- Data / Slips / DIALOGUE / ELARA_PRESENCE.asset
|-- Data / Slips / DIALOGUE / ELARA_RESENTFUL.asset
|-- Data / Slips / DIALOGUE / ELARA_SHOT_BULLET.asset
|-- Data / Slips / DIALOGUE / ELARA_SLEEPWALKING.asset
|-- Data / Slips / DIALOGUE / ELARA_WORKS_AT_MARKET.asset
|-- Data / Slips / DIALOGUE / FINANCIAL_ISSUES.asset
|-- Data / Slips / DIALOGUE / HOODIE_OWNERSHIP.asset
|-- Data / Slips / DIALOGUE / KAE_CONFESSION.asset
|-- Data / Slips / DIALOGUE / KAE_CONFESSION_2.asset
|-- Data / Slips / DIALOGUE / KAE_CRIMINAL.asset
|-- Data / Slips / DIALOGUE / KAE_FALSE_ALIBI.asset
|-- Data / Slips / DIALOGUE / KAE_FOOTPRINTS.asset
|-- Data / Slips / DIALOGUE / KAE_GUN_OWNER.asset
|-- Data / Slips / DIALOGUE / KAE_HEIGHT_MATCH.asset
|-- Data / Slips / DIALOGUE / KAE_KILLER_THEORY.asset
|-- Data / Slips / DIALOGUE / KAE_MOON_ADDICTION.asset
|-- Data / Slips / DIALOGUE / KAE_MOON_HISTORY.asset
|-- Data / Slips / DIALOGUE / KAE_PRESENCE.asset
|-- Data / Slips / DIALOGUE / KAE_PRESSURED.asset
|-- Data / Slips / DIALOGUE / KAE_RESPOSIBLE_AUGUST_INCIDENT.asset
|-- Data / Slips / DIALOGUE / KAE_SHOT_BULLET.asset
|-- Data / Slips / DIALOGUE / KAE_WIPED_GUN.asset
|-- Data / Slips / DIALOGUE / TWO_SHAPES_THEORY.asset
|-- Data / Slips / E14_ACQUIRED.asset
|-- Data / Slips / E4-TRACE_ACQUIRED.asset
|-- Data / Slips / E7R_ACQUIRED.asset
|-- Data / Slips / ELARA_IN_IR.asset
|-- Data / Slips / ENDING / MILLER_CONFRONTATION_00.asset
|-- Data / Slips / ENDING / MILLER_CONFRONTATION_01.asset
|-- Data / Slips / ENDING / MILLER_CONFRONTATION_01_EXIT.asset
|-- Data / Slips / ENDING / MILLER_CONFRONTATION_DONE.asset
|-- Data / Slips / ENDING / MILLER_CONFRONTATION_START.asset
|-- Data / Slips / ENDING / MILLER_WARD_NOT_ACCOMPLICE.asset
|-- Data / Slips / ENDING / SLIP_STEP1_VERDICT_ELARA_SHOOTER.asset
|-- Data / Slips / ENDING / SLIP_STEP1_VERDICT_KAE_SHOOTER.asset
|-- Data / Slips / ENDING / SLIP_STEP2_VERDICT_ELARA_MOTIVE.asset
|-- Data / Slips / ENDING / SLIP_STEP2_VERDICT_KAE_MOTIVE.asset
|-- Data / Slips / ENDING / SLIP_STEP3_VERDICT_ELARA_ALONE.asset
|-- Data / Slips / ENDING / SLIP_STEP3_VERDICT_ELARA_AT_SCENE.asset
|-- Data / Slips / ENDING / SLIP_STEP3_VERDICT_KAE_ALONE.asset
|-- Data / Slips / ENDING / SLIP_STEP3_VERDICT_KAE_AT_SCENE.asset
|-- Data / Slips / F1_ACQUIRED.asset
|-- Data / Slips / KAE_IN_IR.asset
|-- Data / Slips / KEYS_ACQUIRED.asset
|-- Data / Slips / L1_ACQUIRED.asset
|-- Data / Slips / LDN_ACQUIRED.asset
|-- Data / Slips / MAP_ACQUIRED.asset
|-- Data / Slips / N1_ACQUIRED.asset
|-- Data / Slips / SlipEventDatabase.asset
|-- Data / StarterFolder.asset
|-- Data / StarterInventory.asset
|-- Data / TestInventory.asset
|-- Data / WorldActionData / Action_Bathrooom_Dream.asset
|-- Data / WorldActionData / Action_IntDoor_Open.asset
|-- Data / WorldActionData / Action_LockedRoom_Open.asset
|-- Data / WorldActionData / Action_Locked_Room_LDN.asset
|-- Data / WorldActionData / Action_StairsDoor_Open.asset
|-- Data / WorldObjectData / WorldObject_Bathroom_Door.asset
|-- Data / WorldObjectData / WorldObject_Elara_Ending.asset
|-- Data / WorldObjectData / WorldObject_Interrogation_Door.asset
|-- Data / WorldObjectData / WorldObject_Kae_Ending.asset
|-- Data / WorldObjectData / WorldObject_LockedDoor.asset
|-- Data / WorldObjectData / WorldObject_Stairs_Door.asset

---

Here’s the honest truth upfront: **the first codebase is a narrower, more focused prototype**. It does **not** have:

- A real-time clock or time pacing system (no `InternalClockManager`)

- World interaction (no room transitions, NPC locomotion, seating, or isometric player movement)

- The full suite of UI panels (no Free Roam HUD, full Inventory panel, Read/Inspect modes)

Instead, it is a **tightly coupled evidence-and-dialogue engine** with a minimal on-screen interface, designed to prove out the investigative conversation mechanics.

Here’s how it maps to your five topics.

---

## 1. Dialogue & Narrative System

In the first codebase, dialogue is the **core mechanical engine**. The entire prototype revolves around proving that evidence can shape conversation.

- **Two conversational modes**: The player can choose **Inquiry** (casual questioning) or **Confrontation** (accusatory pressure). This changes which dialogue nodes are available and how characters react.

- **Logic Chains as case-building**: Dialogue isn't just a tree of options—it's structured into **Logic Chains** (`LogicChainData`). Each chain represents a specific investigative theory (e.g., "Kae is the murderer," "Elara was an accomplice"). You progress through a chain by presenting the correct evidence at each node.

- **Character memory and patience**: Each character has a `CharacterKnowledgeLog`. It tracks which dialogue nodes have been used, whether the player is currently inside a chain, and their **patience level** (`CharacterKnowledgeLog.cs`). If the player asks about irrelevant evidence too many times, patience drops, and the chain breaks—forcing the player to leave and re-approach.

- **Evaluation engine**: The `CombinationEvaluator` is the brain. It looks at what evidence is currently equipped, checks the character’s logic chains, and asks: _"What questions can I offer the player right now?"_ It also handles standalone interactions (`EvidenceInteractionData`) that aren’t part of a larger chain.

- **Slip Events** (`SlipEventData`, `SlipEventHandler`): When you push a character hard enough (with enough correct evidence in Confrontation mode), they "slip up"—revealing a secret, unlocking new evidence, or setting narrative flags that change the world state. These are the "aha!" moments of the investigation.

- **Narrative state**: `NarrativeStateManager` is a simple flag system. It tracks which slip events have fired, which dialogue nodes are unlocked, and can trigger game endings. It acts as the shared memory of what the player has achieved.

---

## 2. Evidence & Inventory System

Evidence is treated as a **physical and logical resource**. The first codebase has a minimal but functional inventory system.

- **EvidenceData assets**: Each piece of evidence is a ScriptableObject with an ID, display name, description, and combination tags. These tags are used for logic matching (e.g., does this evidence belong to the "Kae" or "Elara" story thread?).

- **State management**: `EvidenceStateManager` is a singleton that tracks:
  
  - What evidence is **acquired** (picked up and in your inventory)
  
  - What evidence is **unlocked** (available to find or receive)
  
  - It fires events when evidence is acquired or unlocked, so the UI can update.

- **The two-slot system**: You can only equip **two pieces of evidence at a time** (`SlotManager`). This forces a moment of intentionality: _"What am I trying to prove right now?"_ Slot A and Slot B can be combined, and the system evaluates them together.

- **Basic inventory UI**: `InventorySlotUI` is a simple OnGUI panel (not UXML) that lists all acquired evidence and lets you click buttons to equip them to Slot A or Slot B. It's functional but minimal.

- **Evidence interactions**: `EvidenceInteractionData` defines one-off responses. If you equip a specific piece of evidence and talk to a character, it might trigger a standalone line of dialogue—separate from the deeper logic chains.

- **Computer unlock system**: Evidence isn't just found—it can be **processed**. `ComputerUnlockRule` defines combinations: if you equip Tape X + Evidence Y, you unlock Evidence Z. This creates a puzzle layer where the player must figure out which pieces to combine.

---

## 3. Time System & Pacing

**This system is completely absent in the first codebase.**

- There is no internal clock, no countdown, no time-advance mechanism, and no urgency mechanic built into the core loop.

- The `GameFlags` file contains a constant for `INTERNALCLOCKSTARTS`, but it's just a placeholder string—there's no clock logic that uses it.

- Pacing is instead driven by **patience** (social pacing) and **chain progression** (narrative pacing). You can't exhaust a character indefinitely, and you have to find the right evidence to advance the story. But you are not under a time limit.

**Implication**: Without a clock, the prototype is a _logic puzzle_ rather than a _race against time_. The player can experiment freely, which is great for proving the dialogue/evidence mechanics, but it lacks the pressure that the reference text describes.

---

## 4. World Interaction

**This is extremely limited** in the first codebase. There is no exploration environment in the code provided—just the interaction scripts.

- **CharacterInteractor**: This script uses a simple `Physics.Raycast` from the camera to detect if the mouse is over a character. It doesn't use proximity (like walking up to them). Instead, it's a point-and-click style interaction (though it could easily be adapted).

- **Mode selection**: When you click on a character, you choose Inquiry or Confrontation via on-screen buttons (1 or 2).

- **No room system**: There are no rooms, no doors, no NPC locomotion, no world objects like pickups or terminals. The `source_structure.txt` shows there's no `GameStateManager`, `RoomTrigger`, or `PlayerController` in this file list.

**Implication**: This codebase is designed for a **static scene** where characters stand in place, and the player interacts with them via point-and-click. The "world" is just a backdrop for dialogue.

---

## 5. UI System & User Experience

The UI is **purely functional and built with a mix of Unity UI Toolkit (UXML) and classic OnGUI**.

- **Dialogue UI** (`DialoguePanel.uxml` + `DialogueUI.cs`): This is the most polished part. It uses a **bottom-centred panel** with:
  
  - A character name and mode label (Inquiry/Confrontation).
  
  - A conversation stream (scrollable speech bubbles).
  
  - A question area that lists available questions based on equipped evidence.
  
  - A "Continue" button for paging through multi-line character responses.

- **Archive UI** (`ArchivePanel.uxml` + `ArchiveUI.cs`): A separate modal panel that lets the player review past conversations. It lists conversations grouped by character, shows the evidence used, and replays the dialogue with badges for out-of-range attempts or slip events.

- **Inventory UI** (`InventorySlotUI.cs`): This uses **OnGUI** (immediate mode) rather than UXML. It's a simple window that lists evidence and lets you click "→ A" or "→ B" to equip it. It's functional but visually rough compared to the UXML panels.

- **HUD and shortcuts**: There's no persistent HUD in the first codebase. You toggle the inventory with `I`, the archive with `C`, and the interaction prompts appear as OnGUI labels.

- **Debug tools**: `PrototypeDiagnostic` (press F1) prints a detailed diagnostic log to the console, showing which chains and interactions are currently matchable with the equipped evidence. `DebugEvidenceGranter` lets you press `G` to instantly acquire all evidence—useful for testing.

**Implication**: The UI is _adequate for prototyping_ but not polished. The visual style (noir detective, amber/gold accents) is present in the USS stylesheets, but there are missing pieces (no clock HUD, no read/inspect modes, no pause menu).

---

## Summary Table: First Codebase vs. Reference Text

| System                   | Reference Text (Conceptual)                           | First Codebase (Actual)                                                                                                           |
| ------------------------ | ----------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| **Dialogue & Narrative** | Full system with chains, patience, slip events        | ✅ **Present.** Chains, patience, slips, and `CombinationEvaluator` all exist and work together.                                   |
| **Evidence & Inventory** | Collect, organise, equip, process                     | ✅ **Present.** Two-slot equipping, state tracking, computer unlock rules. Inventory UI is basic but functional.                   |
| **Time & Pacing**        | Finite clock, urgency, cooldowns                      | ❌ **Absent.** No clock, no time-advance. Pacing is purely social (patience) and logical (chain progression).                      |
| **World Interaction**    | Isometric exploration, room transitions, NPC movement | ❌ **Absent.** Point-and-click raycasting only. No rooms, no player controller, no world objects.                                  |
| **UI & UX**              | Complete suite of panels                              | ⚠️ **Partial.** Dialogue and Archive are polished (UXML). Inventory is rough (OnGUI). No HUD, no read/inspect, no pause/settings. |

---

## In Plain Terms

The first codebase is **an evidence-led dialogue engine first, and a game second**.

It is laser-focused on answering one question: _"Does equipping different evidence and choosing Inquiry vs. Confrontation create interesting, branching conversations?"_

- **It does this well**: The Logic Chains, patience system, Slip Events, and Combination Evaluator form a tight, functional loop.

- **It ignores everything else**: There's no world to explore, no clock to manage, and no fancy UI—just the bare minimum to test the dialogue logic.

If you were to build a full game from this, you would need to graft on the **Time System** and **World Interaction** from the second, larger codebase (which has all those features). The first codebase is the "engine room" of the investigation; the second codebase adds the "game shell" around it.