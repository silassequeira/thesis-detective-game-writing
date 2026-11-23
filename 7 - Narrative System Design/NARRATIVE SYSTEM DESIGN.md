# 7. System Design Architecture

The workshop did not produce a validated system. It produced a set of design problems, constraints, and interaction patterns that any digital implementation would need to address. This chapter describes the design process of translating the workshop role-playing detective experience to a digital prototype.

In order to adapt the workshop I had to reconstruct the evidence corpus, interaction logic, and narrative space so that the digital prototype could more reliably support epistemic agency. The revised narrative should therefore be understood as a direct response to the workshop findings. It is not presented as a final or fully validated version of the game. Instead, it represents the next Research-through-Design iteration: a more coherent and testable digital articulation of the systems rehearsed through the tabletop sessions.

The revision followed five connected design objectives:

1. Narrative Revisions such as correcting contradictions and inconsistencies in the evidence corpus, planning a revised spatial narrative that would be part of the system architecture.
2. Planning and solidifying how the evidence requests, investigative intentions, inquiries, confrontations, and final accusations, could be adapted to a digital playable prototype.
3. Translating the low-fidelity interaction model into a scalable narrative system that allows players to interrogate suspects.

## 7.1 Narrative Revisions

### Evidence Corpus Revision

A central outcome of the workshop was the identification of inconsistencies that could distort participant reasoning. These inconsistencies were especially important because the project depends on allowing players to construct theories from incomplete and ambiguous information. While most of the narrative inconsistencies were adjusted between sessions when those inconsistencies were identified, the evidence corpus was fully revised before beginning the development of the digital prototype. Since the reports contain unintended contradictions, players may develop theories that appear reasonable but are based on material errors rather than interpretive openness. The revision therefore distinguished between intended ambiguity, which should remain available for player interpretation, and unintended inconsistency, which needed correction (Appendix X).

The revised corpus further expands the available material through new reports, maps, environmental documents, and archival case material. These additions were made to address the multiple requests that participants made during the workshop sessions, that fit within the overall narrative, or serve to close off possible narrative inconsistencies. They connect the central homicide investigation to specific navigable locations in the precinct, the history of the previous detective, the wider anomaly surrounding Somnoryl-μ, and the player’s ability to decide which investigative routes are worth pursuing. 

### Revised Spatial Narrative

The low-fidelity workshop was spatially constrained by its tabletop format, but participant behavior showed continued interest in environmental exploration. While only some of the participants attempted to inspect the precinct, open doors, investigate unavailable rooms, since the provided layout of the precinct was very limited, adapting the layout to a 3D environment would only naturally reveal the explorations affordances that weren't previously clear.

The digital prototype therefore expands the precinct into a limited set of explorable locations (Image X). Its purpose is to give environmental interaction a narrative and epistemic function while maintaining a manageable prototype scope. The function of each room was first theorized in the base architecture and implemented for the digital prototype, so the explanation of each room's purpose will be later explained.

# 7.2 Base Architecture: A Petri net-inspired state machine for Video game Logic

In order to translate the workshop experience to a digital prototype, a lot of the mechanics, system and logic had to be well planned before even attempting to build anything in Unity. Since the design question still lingered on how could I build a video game architecture that could support a non-linear narrative and exploration while also being scalable enough for later revisions and future developments, considering that at this point, I wasn't sure how the dialogue would work, how to support different interpretations and integrating all this in ways that allowed the player to converge to the point where they were able to finish the case, and reset everything once the game was over to its original state.

## 7.2.1 The Architectural Problem

The prototype required an architectural layer capable of coordinating several systems whose behavior depends on one another. Evidence acquisition determines which dialogue options are available; dialogue outcomes set narrative flags; those flags gate spatial access; spatial access produces new evidence; and a global time limit constrains the entire process. A digital prototype cannot rely on improvised resolution to keep these systems consistent, so the architecture had to make the conditions of every interaction explicit and enforceable.

The approach taken was to adapt Petri net formalism into a custom state-machine notation focused on videogame logic. The result is a set of connected nodes, such as transitions, preconditions, output places, check nodes, and global room states, that together form the executable logic of the prototype.

The architecture was adopted because conventional scripting does not provide the legibility the prototype requires. When a system contains many interdependent conditions, imperative code obscures the relationships between them: a failure may originate in any of several systems, and the designer must reconstruct the causal chain by reading multiple scripts. A Petri net treats state as an explicit marking and transitions as explicitly gated events, so the conditions of progression are visible rather than implicit.

It is important to clarify the role this architecture actually played in the prototype's development. The Petri net diagram of the prototype was a suggestion of how I could define the major systems, their entry and exit conditions, the flag space through which they communicate, and the primary progression paths from the intro sequence through investigation to the ending. They were not, however, an exhaustive specification that the implementation followed to the letter.

The architecture should therefore be understood in two registers simultaneously: as the conceptual model that gave the prototype its coherent structure, and as a living reference that was continually reconciled with the implementation rather than enforced as a rigid specification. This distinction matters for the evaluation, because it means that the reference is best read as a map of the system's intended design rather than as a one-to-one description of its implementation.

## 7.2.2 Petri Nets and Their Adaptation

A Petri net is a modelling language for distributed systems. It consists of _places_ (conditions or states), _transitions_ (events or actions), and _arcs_ connecting them. A transition may fire only when all of its input places are marked. When it fires, it consumes tokens from its input places and produces tokens in its output places. This allows complex systems to be modelled without scripting every combination of conditions and outcomes, because the marking of places determines what can fire at any moment.

Its theoretical foundation is the approach proposed by Araújo and Roque (2009), who describe Petri nets as a means of representing game systems and game flow through places, transitions, and tokens. Their approach is particularly relevant to interactions whose outcomes depend on several conditions and to systems in which multiple processes may develop concurrently.

The resulting model was created first in a paper format (Figure X), and the final diagram (Figure X) was developed in draw.io using the Petri-net modelling approach discussed by Araújo and Roque (2009) as its conceptual foundation. Following this approach, game behavior was organised through places representing conditions, transitions representing actions or events, and directed connections representing their dependencies. This provided a way to describe the adaptation in terms of what the player could do, under which conditions, and with which consequences.

Places were used to represent progression conditions, interaction prerequisites, and exploration states. A condition is interpreted as marked when it holds and unmarked when it does not. Transitions become enabled when their required conditions are satisfied and fire when the corresponding player action or system event occurs. Their consequences establish, preserve, or remove conditions that influence subsequent interactions.

The diagram distinguishes preconditions, output places, and global room states to make their roles easier to identify. These are project-specific categories within the condition-based representation. 

## 7.2.3 The State Machine Reference

Once the architecture was authored, it was converted into a reference document that translates the graph into tables of states, transitions, and acquisition logic. The reference is structured into six sections.

**Game Flow States** lists every `GLOBAL_ROOM_STATE` and `OUTPUT_PLACE` node that represents a persistent room or game state. This section answers: _where can the player be, and what does each location expose?_ For example, `STATE_EXPLORING_EVIDENCE_ROOM` exposes the case folder, the computer, the locked room door, the corridor door, and the window. `STATE_EXPLORING_CORRIDOR_ROOM` exposes the bathroom, the observation room, the interrogation room, the evidence room, and the stairs.

**System-Level State Flags** lists every flag that represents a persistent systemic condition, the initial sequence, the case folder, the clock, the dream sequence, the ending sequence. Flags such as `INITIAL_SEQUENCE_COMPLETE`, `SLOTS_INVENTORY_ENABLED`, `INTERNAL_CLOCK_STARTS`, and `DREAM_EXPERIENCED` describe not only narrative conditions but the operational state of the prototype.

**Linear Sequence Events** describes the step-by-step progression from `GameStarts` to `EnableFreeRoam`. It traces the intro chain from the first Miller briefing through case folder acquisition, the second briefing, the fade into gameplay, and the activation of free-roam controls.

**Interaction Logic Table** lists every clickable object, dialogue trigger, computer submission, and countdown completion, together with its preconditions and its resulting state or flag. This is the primary reference for debugging, because it allows any failed interaction to be traced to a specific unmet precondition.

**Inventory & Evidence Acquisition** lists every transition that produces an acquired item, organized by acquisition method: starter files, computer-acquired reports, Miller-mediated acquisitions, event-acquired items, and consumable rules. It makes the evidence economy explicit, including the distinction between evidence acquired automatically, evidence requiring a tape combination, evidence delayed by a countdown, and evidence consumed on use.

**Ending & Outcome Logic** describes the ending entry gate, the reaction phase, the outcome phase, and the final ending flow. It lists the conviction flags that can be set during the confrontation, the branches that open depending on those flags, and the terminal states that can conclude the game.

## 7.2.4 A Concrete Trace

To make the architecture concrete, consider the sequence that leads from the initial briefing to the first suspect interrogation. 

The game begins with `GameStarts`, which sets `INITIAL_SEQUENCE_STARTED` and fires `MILLER_BRIEF_00`. On completion, `POST_BRIEF_00` is set. `Acquire.CaseFolder` fires, setting `CASE_FOLDER_ACQUIRED`. `MILLER_BRIEF_01` plays, setting `POST_BRIEF_01`. `INITIAL_SEQUENCE_COMPLETE` is set, and `FadeInGameplay` transitions to `EnableFreeRoam`. `SLOTS_INVENTORY_ENABLED` is set, and the player enters `STATE_EXPLORING_EVIDENCE_ROOM`. `INTERNAL_CLOCK_STARTS` begins the 36-hour countdown (Figure X).

The player clicks the computer, setting `DISPLAY_COMPUTER_WINDOW`. They equip the Forensics Laboratory tape and `E2`. The `CHECKING_REQUIREMENTS` node evaluates the combination, and `Aquire.E2R` fires, setting `E2R_ACQUIRED`. The tape is ejected (Figure X).

The player returns to the corridor and clicks the observation room door, entering `STATE_EXPLORING_OBSERVATION_ROOM`. They approach Miller and equip `E4R`. Miller's inquiry dialogue fires, and `INITIATE_4H_COUNTDOWN_E4-TRACE` is set. The countdown begins (Figure X).

The player continues to the interrogation room door. `CHECKING_INTERROGATION_ROOM_STATUS` evaluates `SUSPECT_READY_FOR_INTERROGATION`. Because the player has not yet inquired with Miller using `PE` or `PK`, the flag is not set, so `InterrogationRoom.DenyEntry` fires and the player receives `JULIAN_IR_DENIED_00` (Figure X).

The player returns to Miller and equips `PE`. `ELARA_IN_IR` is set, and the player can now enter the interrogation room. `STATE_EXPLORING_INTERROGATION_ROOM` is entered, and the player can interact with Elara using the two-slot system (Figure X).

Four in-game hours later, `4H_COUNTDOWN_E4-TRACE_COMPLETE` fires. The player returns to Miller, and `MILLER_TRACE_00` plays, producing `E4-TRACE_ACQUIRED`(Figure X).

The trace demonstrates how the architecture connects evidence, dialogue, space, time, and narrative consequence of a shared flag space, allowing each system to operate independently while remaining coordinated with the others. 

## 7.2.5 The Accusation Sequence

This sequence was conceptualized during in the Petri-net diagram, and expanded with the possible narrative configuration that the logic chains allowed in this specific sequence (Figure X), this is just one of the iterations of the RTD process, chapter 8 explores the final iteration. 

The workshop ended with a final accusation, and the design question is how to let the player commit to one without the interface confirming it in advance. This is the point where the static detective risk is greatest: an interface that checks the accusation before it is delivered would perform the interpretation the whole system is built to leave to the player.

The accusation must be a commitment, not a submission for marking. The player selects the suspect and the evidence that supports the accusation, and the story answers. 

In order for the game to be validated within a achievable scope, the planning that was done in order to implement the accusation sequence revolved around Miller asking the questions and the detective answering them. The hardest part was establishing the questions that would need to be made so that a player that made his case could answer Miller with their interpretation, and punish an unprepared player that could attempt to cheese their way into finishing the game, or one that didn't even investigate enough to have a case in the first place.

Ending Entry Gate (Figure X)

The ending sequence is gated by the `CHECKING_REQUIREMENTS` (CHECK_NODE) during the Miller Confrontation. Only when sufficient evidence is assembled does `MILLER_CONFRONTATION_00` fire. Insufficient evidence routes to the `MILLER_CONFRONTATION_NOT_ENOUGH_EVIDENCE_01` path.

**Conviction flags** are set during the Confrontation chain (steps `MILLER_CONFRONTATION_00` through `_04`). The specific conviction depends on which evidence items are equipped (`$_EQUIPPED`) during each confrontation round.

If a player exhausts the patience of Miller during the accusation sequence as planned in the petri-net, will lead to two different outcomes depending on the state that they're in. 

In the first scenario (Figure X), the player the dialogue panel closes and the player returns to the observation room. 

In the second scenario (Figure X), happens if the player is in a forced confrontation after the "MILLER_ANGRY_SEQUENCE_INITIALIZED" is set. This outcome will then result in the detective getting fired. 

If the player was able to present the evidence without depleating Miller's patience it then triggers the following sequence (Figure X).

### (Reaction Phase)

In the petri-net iteration phase for the ending phase, consisted of showing a slide show of the character's reactions, where some of the narrative decisions were different. 

**Rule:** `TRIGGERENDING_1` always strictly precedes `TRIGGERENDING_2`.

Entry point: `TRIGGER_ENDING_SEQUENCE_00` fires upon confrontation completion.

Simultaneous effects:

- `POST_TRIGGER_ENDING_SEQUENCE_00` is set.
- `ENABLE_CUTSCENE_CONTROLS` is set.
- `DESABLE_PLAYER_CONTROLS` is set.

From `POST_TRIGGER_ENDING_SEQUENCE_00`, the system fans out to the Elara Reaction branches and then the Kae Reaction branches in sequence.

#### Elara Reaction Branches (`TRIGGER_ENDING_1_ELARA_$`)

|Variant|Precondition(s)|Behaviour|
|---|---|---|
|`TRIGGER_ENDING_1_ELARA_$` (Free)|`ELARA_FREE`|If `SHOWN_CONFESSION_TAPE` = true → Elara defends Kae's innocence emotionally. If `SHOWN_CONFESSION_TAPE` = false → Elara is confused, asks about Kae.|
|`TRIGGER_ENDING_1_ELARA_$` (Arrested)|`ELARA_MURDER` [OR] `ELARA_ACCOMPLICE`|Elara is being charged. Reaction varies by conviction.|

All Elara reaction branches converge at `POST_TRIGGER_ENDING_1_ELARA_$` → `POST_TRIGGER_ENDING_SEQUENCE_01`.

#### Kae Reaction Branches (`TRIGGER_ENDING_1_KAE_$`)

|Variant|Precondition(s)|Behaviour|
|---|---|---|
|`TRIGGER_ENDING_1_KAE_02`|`KAE_ACCOMPLICE [OR] ELARA_ACCMPLICE [OR] ELARA_MURDER`|Kae reaction for accomplice/shared-guilt conviction.|
|`TRIGGER_ENDING_1_KAE_03` (variant A)|`NO_CONFESSION_TAPE` AND `KAE_MURDER`|Standard guilty reaction, no confession exists.|
|`TRIGGER_ENDING_1_KAE_03` (variant B)|`CONFESSION_TAPE` AND `KAE_MURDER`|Kae being arrested with confession; begs for Elara's release.|
|`TRIGGER_ENDING_1_KAE_03` (variant C)|`SHOWN_E4-TRACE` AND `KAE_MURDER`|Trace evidence variant; Kae confronted with barefoot mud trace.|
|`TRIGGER_ENDING_1_KAE_03` (variant D)|`ELARA_FREE` AND `KAE_MURDER`|Kae accepts fate while Elara goes free.|

All Kae reaction branches converge at `POST_TRIGGER_ENDING_1_KAE_$`.

Flow after Kae reactions → `TRIGGER_ENDING_SEQUENCE_02` → `POST_TRIGGER_ENDING_SEQUENCE_02` → fans out to the Outcome Phase.

---

### (Outcome Phase)

Entry: `POST_TRIGGER_ENDING_SEQUENCE_02` → fans to multiple `TRIGGER_ENDING_2_$` branches based on conviction flags.

#### Elara Outcomes (`TRIGGER_ENDING_2_ELARA_$`)

|Conviction Flag|Outcome Scene|
|---|---|
|`ELARA_FREE`|Scene of Elara reuniting with her parents.|
|`ELARA_MURDER`|Scene of Elara crying in a jail cell bed.|
|`ELARA_ACCOMPLICE`|Scene of Elara crying in a jail cell bed.|

All Elara outcome branches converge at `POST_TRIGGER_ENDING_2_ELARA_$`.

#### Kae Outcomes (`TRIGGER_ENDING_2_KAE_$`)

|Precondition(s)|Variant|Outcome Scene|
|---|---|---|
|`KAE_GUN_POSSESSION [OR] KAE_ACCOMPLICE [OR] ELARA_ACCOMPLICE [OR] ELARA_MURDER`|`TRIGGER_ENDING_2_KAE_00`|Kae emotionally devastated, screaming through bars.|
|`KAE_MURDER`|`TRIGGER_ENDING_2_KAE_01`|Kae calm, accepting look.|

All Kae outcome branches converge at `POST_TRIGGER_ENDING_2_KAE_$`.


It does not tell the player whether the accusation is correct before or during submission, it only provides the Captain's reaction to the evidence and option that is being presented, this is all done so that the ending outcome with the character's reactions and ending panels reflect the player's decisions for the case that Miller accepts.

## 7.2.6 The Dream Sequence

This sequence can be seen here (Figure X). The way that the player can trigger this sequence, can be either in the bathroom, or anywhere else, with different outcomes depending on where the player decided to consume the Moon Drug, by equipping the AI + E15 in the slots and clicking on the detective player model. 

ClickOn.LightPerson.Object

→ `DISPLAY_DIALOGUE_WINDOW` → `LIGHT_PERSON_DREAM_00` → options `TRIGGER_OPTION_00` / `TRIGGER_OPTION_01` → `LIGHT_PERSON_DREAM_01` → `POST_DETECTIVE_DREAM_01` → connects forward to `TRIGGER_OPTION_00` or `TRIGGER_OPTION_01` _(per Missing Links rule: `POST_LIGHT_PERSON_DREAM_00` connects to either `TRIGGER_OPTION_00` or `TRIGGER_OPTION_01`)

If the player decided to trigger the sequence during inside the bathroom, he then returns back and can continue the investigation, if he triggerend anywhere else it will set "MILLER_ANGRY_SEQUENCE_INITIALIZED" and force the ending confrontation that can lead to the player getting fired. 


While modelling the game's systems using petri nets was extremely useful to map out practically all the interactions and states for the digital prototype, a different but connected conceptualization for how the dialogue system would work. This distinction was made since it wouldn't be valuable in this stage to fully mapping out each possible line of logic that would be possible to explore within the digital prototype. 

## 7.3 Dialogue Narrative System

The dialogue narrative system unlike the modelling the architecture using petri-net diagram, was created as a separate scalable system that would work on any narrative that followed the *Two-Slot Epistemic Interaction System*. 

## 7.3.1 Design Objectives

Before implementing the full interconnected game architecture in Unity, I needed to establish how the dialogue system would operate in practice. The tabletop workshop had already confirmed that players could naturally connect investigative questions to case evidence. The central design challenge was building a scalable, non-linear dialogue system capable of recognizing a player's investigative intent based on the evidence equipped in the two slots within a given narrative context. Reviewing how workshop participants paired items and phrased their inquiries also revealed recurring question patterns and lines of reasoning that I would not have anticipated by myself.

The fist design objective was to build a dialogue engine that explored a different solution to the  problem with the automated deduction trees, building directly upon Clara Fernández-Vara’s critique of the traditional detective game. In conventional detective games, the player's interpretive role is minimized because the software performs the critical reasoning, reducing gameplay to collecting clues that trigger predetermined deductions.

To create this system for a playable digital prototype, I evaluated two established approaches before designing a custom solution.

- **Generative language models.** Using an LLM to generate questions and suspect responses dynamically would accommodate open-ended player phrasing, but it introduced major risks regarding narrative and character consistency. In an epistemic investigation where every detail shapes the player's interpretation, hallucinations or unscripted concessions could undermine the case. Even during the live workshop sessions, where I improvised responses as a facilitator, I strictly bounded every character's answers to respect their narrative constraints and guide players toward the authored evidence traces. Giving up that authorial control in a digital build would create unpredictable logic failures.
    
- **Branching dialogue trees and automated deduction.** The commercially dominant approach in detective games relies on branching dialogue trees or inference engines that pre-compute a fixed solution path. In those models, the player selects from pre-authored branches whose evidential meaning is already decided in advance. As Fernández-Vara observes in her critique of static detective puzzles, treating each clue as a key to a single predetermined lock reduces investigation to a sequence of mechanical unlocks rather than active reasoning. Furthermore, scaling a branching tree across multiple narrative flags creates a combinatorial authoring burden, requiring entire conversations to be duplicated for every state change.

To avoid both unscripted generation and rigid branching trees, I designed a state-dependent dialogue engine organized around **Logic Chains** that can be best described as units of investigative reasoning . This system means to treat the interrogation room as an open epistemic space. Equipping evidence in the Two-Slot Epistemic Interface does not automatically solve the case. Instead, it allows the player to construct a conversational hypothesis and test it against a suspect's epistemic resistance. The burden of interpretation remains on the player, making critical exegesis the core gameplay activity.

This architecture intends to align with Mateas and Stern's neo-Aristotelian model of interactive drama, which builds on Laurel's adaptation of Aristotle's poetics. Mateas and Stern argue that genuine **dramatic agency** emerges when there is a structural balance between top-down **formal constraints** (authorial plot necessity and dramatic probability) and bottom-up **material constraints** (the affordances provided by the interface and character state).

- **Material constraints from below.** Provided through the **Two-Slot Epistemic Interface**, inventory reports, interview modes (_Inquiry_ and _Confrontation_), and the suspect's inferable motivations. The interface offers clear material affordances that allow the player to assemble logical arguments.
    
- **Formal constraints from above.** Governed by dramatic probability, global narrative flags, threshold rules, and suspect resistance. As the player builds argumentative pressure, formal rules narrow the space of dramatic probability, guiding the interrogation toward a necessary dramatic crisis, with the suspects internal arcs or in the final verdicts.

By balancing material affordances with formal narrative constraints, the system intends to explore a different approach in solving the tension between interactive agency and authorial design, in order to evaluate if the player choices lead to coherent, emotionally resonant narrative resolutions with actions that intend to feel consequential.

The last design objective is that the system must be authorable within prototype scope. The thesis is a solo project with a bounded development window. A solution that requires an AI reasoning engine, a real-time drama manager, or exponential authoring across narrative branches would not be achievable.

In order to understand how this dialogue narrative system attempts to reach that goal, it would be better understood with a system overview explaining how those concepts were put into practice. 

### 7.3.2 System Overview

The system can be understood through four groups of concepts: what the player brings to a conversation, what the author prepares in advance, what the system remembers about each suspect, and which rules decide when the story reacts. The definitions stay at the conceptual level. The implementation is covered in the next chapter.

#### What the player brings

- **Evidence.** The documents, reports, recordings and other material the player collects during the case. Evidence is the player’s main vocabulary in an interrogation. The player never names a topic. They decide which items belong together.
    
- **The Two-Slot Epistemic Interface.** The primary material interface through which the player formulates investigative hypotheses. The player equips up to two items (Slot A and Slot B), and the same item cannot occupy both. The questions available to the player depend on this choice. One item on its own opens one set of questions, and the same item paired with a second can open different ones. The player decides what to place on the table, and the system surfaces the questions that choice makes possible.
    
- **Interview Modes: Inquiry and Confrontation.** Two ways of approaching the same evidence. _Inquiry_ is soft probing: asking what an item means and gathering the suspect’s account. _Confrontation_ is accusatory pressure: pointing at a contradiction. Every dialogue node belongs to one mode, so the mode determines which step of a line of reasoning the suspect can answer. Moving a line of reasoning forward may therefore require switching between modes mid-conversation.
    
- **Conversational Proposal.** The unit the system evaluates each time the player acts. It combines the equipped evidence, the chosen mode and the suspect being addressed, read against that suspect’s history and the current story state.

#### What the author prepares

> The idea to how the trigger evidence IDs were configured is that it allows different trigger evidence configurations such as (ex. E8R, E4R, E4-C, E4-TRACE), in this case the Require All triggers (AND) is set meaning that the possible combinations for this question to appear are (E8R, E4R);  (E8R, E4-C); (E8R, E4-TRACE); But if the "Require All triggers (AND)" is not set (ex. E8R, E4R, E4-C, E4-TRACE), this means that any of this evidence equipped will allow the question to be displayed. 

> There is specific way the dialogue was designed. A primary question is meant to be main one, or the most relevant option basically displays over a ranged question with a combination in the slots.  

> Writing this "[Show {evidence}]" on the detective question field, basically displays the evidence names on the question, meaning [Show {evidence}] for the (ex. E8R, E4R, E4-C, E4-TRACE), will display all of the name combinations depending on how it's configured.

> A Variation response field if configured allows the author to contextualize the player more quickly if he decides to return to a chain later, or just provide a variation response to a question that does not advance the chain.

> The weak questions configuration can have varied functions depending on the context. First it serves to guide the player through the chain by providing a vague context question that can hint to the logic it expects the player to continue showing in order to progress:  (NOTE: this is specific node that is conditioned by the player first needing to establish the connection of the witness and Elara's feet condition)  (ex. [Show {evidence}] "This report here proves that you were at the scene. Explain how it got there."), in this example for the weak question, it allows the player to equip the evidence that actually proves she was present at the scene, (E4-TRACE), punishing the player by reducing the character's patience. Second function if the author notices that players are equipping evidence without thinking about them first within that context, is to write a vague follow up within the context using primary question or ranged (ex. "[Shows {evidence}]" This was why you stopped taking you medication ?") with the necessary required evidence to cover the intended combination the player wants to use in that specific scenario, and then write for the weak question the same detective question. The third function is to provide diegetic feedback that a certain combination does not fit that node or wasn't covered, while also forcing the player out of the interrogation (without breaking the character's patience if not exhausted), aiming to make the player rethink the evidence that they are equipping within that context, or to look for more that are a better fit. 

> The author can also condition the dialogue in different ways that would allow for a even more complex dialogue intention, by writing {FLAG_ELARA_MOON_ADDICTION} for the detective question. First it can have the function to condition a certain question until a certain flag is established first (Ex."{FLAG_KAE_RESPOSIBLE_AUGUST_INCIDENT} Arthur was already targeted in August. The pattern shows Kae escalating. He came back to finish what he started.”). Another function would be condition a certain question based on what what previously established to create a more complex detective question/confrontation for a certain trigger combination : Trigger evidence: E7R, E4R, E4-TRACE (ex. {FLAG_ELARA_BLACKOUT} “The temporal report puts Elara at peak Moon effect from 21:00 to 01:00—covering the entire TOD. Her soles are cut with fresh alley asphalt. She wasn’t asleep at home; she was in that alley, impaired.”), since each node is registered, the authors can create conditions that can cover any valuable intention with the act of playing essentially being a way of the player showing what they know and having the possibility to reward that knowledge by providing a dialogue specific to that established narrative flag. 

> This narrative system was created to allow inquiries and confrontations to be configurable in a way that can cover and reward the player's investigative questions and provide enough narrative tension and consequence to reward the player deductions.  

- **Logic Chains**. Authored lines of investigative reasoning, such as “prove the suspect was at the scene”. A chain is an ordered set of steps that the player builds up across one or more conversations, and it is not a rigid conversation tree. Each suspect has several chains, and the evidence the player brings decides which one opens. Once the player is inside a chain, the other chains are set aside until it ends or breaks. A chain can also stay unavailable until a story flag is set or earlier steps have been visited.
    
- **Dialogue Nodes** (`nodeID`). One step in a chain’s argument. A node defines its mode and the evidence that advances it (`requiredEvidenceIDs`). It also defines the evidence related to it (`logicRangeEvidenceIDs`) and the questions and responses attached to it. The first time a question is asked, the suspect gives a base response. If the player repeats it, the suspect gives a variation.
    
- **Evidential Fit.** For any node, the equipped evidence falls into one of three categories:
    - _Advancing evidence_ matches what the step requires and surfaces its main question. Two items authored to work together rank above either item alone. The more specific the proposal, the higher its priority.
    - _Related evidence_ is relevant to the same line of reasoning. It surfaces additional questions on the step and keeps the argument alive.
    - _Out-of-range evidence_ matches nothing. Outside a chain it simply produces no question. Inside a chain the suspect deflects, which costs patience (see below).
    
- **Evidence Interactions.** Baseline reactions to an item or pair that exist outside any chain. They are always available and never cost patience. They are hidden when a chain question already covers the same evidence. Allow to configure delayed outcomes, such as an item that comes back from processing hours later. 
    
- **Slip Events**. Moments when a suspect’s cover story cracks, or establishes a meaningful flag within the narrative. They are attached to specific questions and normally fire once per suspect. A slip can hand the player new evidence and can set narrative flags, so it is the main way a conversation changes the rest of the game.

#### What the system remembers

- **Suspect Memory.** Each suspect individually remembers which steps and questions have been used, which chain they are inside, and a bookmark of where each chain stopped. The bookmark lets the player later resume a line of questioning. This memory is what lets a cover story persist across several interrogations.
    
- **State Counters (Patience and Strength).**
    - _Patience_ is a suspect’s social willingness to endure questioning. It drops when the player, in the middle of an argument, presents evidence that doesn’t fit. The first misstep gets a diminished response. A second consecutive misstep breaks the chain. At zero the suspect stops engaging and enters a cooldown measured in in-game time, after which patience is restored. Repeated depletions escalate: first a warning beat, then, at the limit, the story intervenes.
        
    - _Strength_ (`strengthCharacterID`) is a suspect’s accumulated argumentative pressure. It grows when the player’s questions advance a chain. By default each Confrontation question adds one point and Inquiry questions add none, unless the author says otherwise. Each question counts once and strength is never reset.
    
- **Narrative Flags.** Global yes/no facts about the story state. Slips, evidence acquisition and patience events set them. Chains, questions, suppression rules, narrative rules and endings read them.

#### What the system decides

- **Threshold-Based Narrative Rules**. High-priority background evaluators. They run whenever a flag or a strength value changes. A rule’s conditions can require flags to be set or unset, and can require a named suspect’s strength to reach a threshold. When conditions pass, the highest-priority rule plays its Scripted Narrative Sequence, once if so authored. Timing is deliberately cautious. A rule driven by strength waits for the current answer to finish, and any rule waits while another panel is open.
    
- **Scripted Narrative Sequences.** Authored, linear pages of dialogue that the system plays rather than the player prompting them. They are used for rule triggers, patience warnings, cooldown lines and briefings.
    
- **Narrative Suppression and Chain Reset.** Two safeguards that keep authoring manageable. Suppression retires chains and interactions once a flag shows they are obsolete, for example after a suspect has already reacted to an item. After a patience cooldown, a reset package can reactivate chains and clear flags so the player can revisit them. These rules switch existing content on and off by state, so conversations don’t have to be duplicated for every state change.

#### The Player Interaction Loop

The loop has five moments, repeated for as long as the investigation continues.

1. **Frame a proposal.** The player approaches a suspect, chooses Inquiry or Confrontation, and equips zero, one or two items. If the suspect has run out of patience, the conversation does not open. Only a short fallback line plays.
2. **The system reads the proposal.** It compares the evidence and mode against the suspect’s chains, memory and the current flags. It builds the list of questions the proposal supports, ordered from most specific to most generic. A resumable line of questioning and combined items come first. Single items and baseline reactions follow, and the deflecting weak question comes last. Anything the proposal does not support does not appear.
3. **Commit to a hypothesis.** The player chooses one of the surfaced questions. The player’s interpretive work is here: deciding which evidence to pair and which question to press.
4. **The suspect responds.** There are three possible outcomes:
    - If the question advances a chain, the suspect answers, the chain moves on, memory is updated and strength may rise.
    - If the question triggers a slip, new evidence or flags enter the game.
    - If the evidence was out of range, patience drops and the suspect deflects.
5. **The world reacts.** Flags gate or suppress other chains. Counters cross thresholds, so patience warnings fire and narrative rules interrupt with scripted sequences. The player then returns to step 1 with a changed suspect, possibly with new evidence in the inventory.

In terms of Mateas and Stern’s model, steps 1 to 3 are where the **material constraints** operate, because they are what the interface lets the player express. Steps 4 and 5 are where the **formal constraints** operate, because they decide how the story answers. The system never declares a hypothesis “correct”. It only lets the suspect yield or resist.

> The player interaction loop would only make sense if during the accusation screen they are able to communicate their theory and make the final decisions that influence the cathartic and resolution moments of the game.
#### Trade-Offs Accepted

The dialogue system architecture accepts trade-offs that should be named explicitly.

**Authored content over emergent content.** The player cannot ask questions the designer did not anticipate. This constrains the range of investigative expression available.

**Legibility over mystery.** The system communicates which evidence unlocks which questions, though it does not tell the player what the evidence means. This distinction between legibility of operational rules versus opacity of interpretation was central to the workshop findings and it aims to be preserved in the digital prototype.

**Evidence-bound reasoning over free-form reasoning.** The player's expression of investigative intent is constrained to by the evidence they have acquired. This is the price of evidence-gated progression.

**Intent inferred from evidence over intent expressed in words.** The system recognises what the player means from the evidence and mode, not from how they would phrase it. This makes recognition reliable and keeps the suspect’s answers under authorial control, which was the reason for rejecting generative models. It also means two players with different intentions who equip the same items and mode get the same questions, and the system cannot distinguish them.

> But the system does not mean to cover every possible question possible, it means to reward the player with knowledge based on the evidence and flags that they've established prior, it means to guide the player towards better paths that can or cannot cover their desired question, with the purpose of the character's response to answer even if lightly some of the questions that they weren't able to ask.  

**Graded outcomes over binary success**. The system never declares a hypothesis correct or incorrect. Responses vary in degree: a suspect answers, resists with a diminished response, or slips and concedes something. Strength accumulates, flags combine, and the investigation ends in one of several endings rather than a single solved state. Failure is also rarely terminal inside a conversation, because patience recovers and chains can be revived. It only becomes consequential when the cost accumulates, for example when depletions escalate towards Miller’s intervention.

> The success of the narrative dialogue system depends on good writing. The system not being generative requires the writer to elaborate questions and responses meaningful enough to guide and reward the player towards paths that reward their investigative efforts towards a more solid theory than the one they started with. Also requiring continuous playtesting to map out and design questions and paths for the players to express themselves in a meaningful way. 

These trade-offs are not weaknesses to be hidden. They are the conditions under which the prototype operates, and the evaluation chapter should examine whether players experience them as acceptable constraints on investigative agency or as limitations that undermine the intended experience.

The Narrative system and how it works, its one component of the experience, being more of the brains of the narrative system while the action component that is explored through the UI, and the system architecture would also need to fall into the decision of how is the game going to feel and look like. 


## 7.4 Interface and Presentation Planning

The final part of the prototype’s conceptualisation concerned how the investigation should feel and how the player should interact with it. These decisions had to be made before development began because they constrained the scope of the project, the asset pipeline, and the usability of the dialogue system. The audio-visual production and the concrete behaviour of each interface panel are covered in Chapter 8. This section documents the design intent, the interaction problems identified during the workshop, and the iteration history that led to the implemented interface.

Two framing notes apply. First, this section describes planning, not build. The concrete behaviour of each panel—drag rules, hover states, character limits, timings, and final layouts—is specified in Chapter 8. Second, the design was iterative. The figures cited below pair early sketches with later layouts, and these pairs are part of the Research-through-Design evidence for this chapter.

### 7.4.1 The Feel of the Game

The first presentation decision concerned perspective and dimensionality. An earlier design proposal had imagined navigation in a 3D isometric perspective. During the conceptualisation of this narrative, I considered instead making the game in a visual-novel style, since the player would only be able to explore a limited set of rooms (Figure X). That option was abandoned for three reasons. It would not be scalable: if the project were extended, the navigation-specific assets could not easily be reused. It would require either generating sprites with AI or spending a large part of the limited development window drawing minimal room sprites and character animations, which would still risk looking stiff during interrogations. And it would have moved the project away from the spatial exploration that workshop participants had already shown interest in.

The decision to use an isometric 3D perspective therefore preserved the original vision for the project while remaining achievable. It allowed me to learn and develop in 3D, to scale the environment more easily, and to use free 3D assets, animations, and character models as placeholders that could be replaced if the project were developed further. The audio-visual side of this decision, including final asset use and production, is discussed in Chapter 8.

### 7.4.2 Interaction Design Problems

The two-slot mechanic had already become, during the workshop, the essential middle ground between the system recognising the player’s intention and the player being able to present the evidence they wanted to show within a given context. The interface therefore had to support three things at once: the player’s expression of an investigative intention through Inquiry or Confrontation, the player’s ability to organise their case, and the persistent pressure of the in-game clock. The clock had to remain visible at all times to build time pressure.

Within that brief, the UI planning centred on three problems.

First, evidence cards had to be visually distinct but still recognisable. There were many pieces of evidence, most of them reports with similar formats, and during the workshop the facilitator often had to help participants find the report card or document they wanted to present. Each evidence card therefore had to communicate its relation to the underlying report quickly, without requiring the player to read the full title every time (Figure X).

Second, equipping evidence had to be fast enough to communicate intention during a conversation, but not so frictionless that the player could endlessly test combinations to see whether something new appeared. The decision was to implement a dragging interaction to one of the slots, mirroring how players had physically dragged cards during the workshop sessions.

Third, participants had organised their evidence in different ways during the workshop. The interface therefore needed tools that would let players sort evidence by suspect, theory, or timeline without the system performing any deduction or investigative reasoning for them.

### 7.4.3 First Iteration: Side-by-Side Dialogue and Case Folder

The first design iteration organised the screen in two parts (Figure X). The left side was focused on dialogue and the two slots; the right side held the inventory and the clock. The layout resembled a Disco Elysium-style arrangement, so that dialogue would not interfere with the player’s ability to see the action on screen while still allowing them to read dialogue and drag evidence into the slots (Figure X).

In this iteration, dialogue was shown in a column style, with questions and character responses registered alongside one another. The narrative system had not yet been conceptualised, so the options were rendered from the evidence the player chose and the intention they were pursuing: Inquiry, Confrontation, or End Conversation. This first concept was abandoned because it was too limited and obscured the player’s dialogue decision.

The inventory was designed to resemble an actual police folder on the right side of the screen. It allowed the player to see the information they needed from the case folder while retaining the dialogue context on the left, and to drag evidence from the folder into the slots in a way that mimicked the physical interaction of the workshop. The inspection panel aimed to resemble the folder itself: the player could zoom in and out and pan around a document, and could create and organise evidence in different folders in a way that resembled the workshop sessions (Figure X).

### 7.4.4 Second Iteration: Centring the Investigative Act

The second iteration repositioned the player’s action at the centre of the screen. This iteration is closer to the interface explored in Chapter 8.

Dialogue affordances became part of the main panel itself. The player could switch between Inquiry and Confrontation while in the panel, and the questions displayed depended on the equipped evidence, following the logic described in §7.3. The player could also scroll through the dialogue history. A quick menu allowed evidence to be dragged from either the inventory or the equipped folder directly into the slots, and a conversation archive allowed the player to revisit previous dialogue and see which evidence had triggered it (Figure X). The archive was intended to support reflection: it lets the player reconstruct their own line of reasoning without the system interpreting it for them.

The inventory was reconceived as the detective’s case file. It could open either to the full evidence list or to the player’s equipped folder, and it covered the whole screen when opened (Figure X). The important design shift was that the player could organise folders and equip evidence without closing the inventory, so that sorting and arguing were part of the same workflow. Inside a folder, the player could switch between viewing its contents and moving evidence into it. The HUD sat in the top-left corner with inventory and folder icons that opened the appropriate panel.

Inspection and reading were planned as a close-up evidence mode with note-taking, page navigation, and equip controls. The concrete layout and interaction rules for that mode belong to Chapter 8. What matters for the design architecture is the principle: inspecting evidence should feel like handling a document, not like opening a database entry.


> Note: I should explain here the process behind building the evidence cards for the UI. 

### 7.4.5 Design Principles Carried into Implementation

The interface planning produced a small set of principles that constrain the implementation described in Chapter 8.

Evidence must remain legible at a glance, because the player’s main expressive act is choosing which evidence to put forward. Equipping should involve deliberate friction—dragging rather than instant selection—so that the player commits to a proposal rather than testing combinations passively. Organisation tools should help the player sort and retrieve evidence without performing deduction for them. Dialogue context and the clock should remain available while the player works with evidence. And the interface should never confirm an interpretation in advance; it should let the player commit to a hypothesis and let the story answer.

Because Unity’s UI Toolkit follows a web-like logic similar to HTML and CSS, the visual and functional aspects of the interface were first prototyped in a web environment before being adapted into Unity (Figure X). The concrete build, final panel behavior, and audio-visual implementation are specified in Chapter 8.

## 7.5 Summary

This subchapter has described the base architecture of the digital prototype: a Petri net-inspired state machine adaptation focused on videogame logic, converted into a state-machine reference for authoring, debugging, and documentation. The architecture connects evidence, dialogue, space, time, and narrative consequence through a shared flag space, allowing each system to operate independently while remaining coordinated with the others. It functioned as the base architectural structure of the prototype rather than as an exhaustive specification, and was continually reconciled with the implementation as the prototype evolved. It provides the operational foundation for the narrative and dialogue systems described in 7.1 and 7.2. The following subchapter describes how this architecture was implemented in the digital prototype, including the evidence system, dialogue UI, countdown management, and ending resolution.