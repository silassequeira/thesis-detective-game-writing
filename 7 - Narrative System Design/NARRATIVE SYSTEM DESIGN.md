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

While modelling the game's systems using petri nets was extremely useful to map out practically all the interactions and states for the digital prototype, a different but connected conceptualization for how the dialogue system would work. This distinction was made since it wouldn't be valuable in this stage to fully mapping out each possible line of logic that would be possible to explore within the digital prototype. 

## 7.3 Dialogue Narrative System

The dialogue narrative system unlike the modelling the architecture using petri-net diagram, was created as a separate scalable system that would work on any narrative that followed the *Two-Slot Epistemic Interaction System*. 
