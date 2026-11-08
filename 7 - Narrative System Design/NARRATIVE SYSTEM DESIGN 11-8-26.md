# 7. System Design Architecture

The workshop did not produce a validated system. It produced a set of design problems, constraints, and interaction patterns that any digital implementation would need to address. This chapter describes how those problems were translated into a technical architecture, and the narrative corrections that were done based on the feedback. The sessions revealed narrative inconsistencies, unclear interaction boundaries, incomplete information routes, unreliable facilitation-dependent responses, and insufficient support for evidence organization and theory revision.

The purpose of the revision was therefore not simply to add more content to the mystery. It was to reconstruct the evidence corpus, interaction logic, and narrative space so that the digital prototype could more reliably support epistemic agency. The revised prototype had to preserve ambiguity concerning responsibility for Arthur Penhaligon’s death while ensuring that ambiguity emerged from competing but intelligible interpretations of evidence rather than from contradictory dates, inaccurate reports, unclear interaction rules, missing information, or unintended dead ends.

The revision followed five connected design objectives:

1. Correcting contradictions and inconsistencies in the evidence corpus.
    
2. Clarifying the distinction between evidence requests, investigative intentions, inquiries, confrontations, and final accusations.
    
3. Translating the low-fidelity interaction model into a more structured digital Logic Chain and flag system.
    
4. Expanding the precinct into a limited but meaningful navigable environment that supported further investigation, reflection, and narrative context.
    
5. Providing tools that allowed the player to organize information and retain their own developing theories without automatically resolving the mystery for them.
    

The revised narrative should therefore be understood as a direct response to the workshop findings. It is not presented as a final or fully validated version of the game. Instead, it represents the next Research-through-Design iteration: a more coherent and testable digital articulation of the systems rehearsed through the tabletop sessions.


## 7.1 Narrative Revisions 

### Evidence Corpus Revision

A central outcome of the workshop was the identification of inconsistencies that could distort participant reasoning. These inconsistencies were especially important because the project depends on allowing players to construct theories from incomplete and ambiguous information. While most of the narrative inconsistencies were adjusted between sessions when those inconsistencies were identified, the evidence corpus was fully revised before beginning the development of the digital prototype. Since the reports contain unintended contradictions, players may develop theories that appear reasonable but are based on material errors rather than interpretive openness. The revision therefore distinguished between intended ambiguity, which should remain available for player interpretation, and unintended inconsistency, which needed correction (Appendix X).

The revised corpus further expands the available material through new reports, maps, environmental documents, and archival case material. These additions were made to address the multiple requests that participants made during the workshop sessions, that fit within the overall narrative, or serve to close off possible narrative inconsistencies. They connect the central homicide investigation to specific navigable locations in the precinct, the history of the previous detective, the wider anomaly surrounding Somnoryl-μ, and the player’s ability to decide which investigative routes are worth pursuing. 

### Revised Spatial Narrative

The low-fidelity workshop was spatially constrained by its tabletop format, but participant behavior showed continued interest in environmental exploration. Several participants attempted to inspect the precinct, open doors, investigate unavailable rooms, or ask questions about physical objects outside the central evidence system. These attempts sometimes revealed expectation gaps, but they also showed that participants understood the police station as a narrative space rather than merely as a neutral interface surrounding the evidence cards.

The digital prototype therefore expands the precinct into a limited set of explorable locations (Image X). Its purpose is to give environmental interaction a narrative and epistemic function while maintaining a manageable prototype scope.

#### Locked Evidence Room

The first new area is an inaccessible room located inside or adjacent to the evidence room. The player initially encounters a locked door and may inspect it to obtain the Locked Door Note (LDN). The note provides an institutional and narrative reason to ask Captain Miller for access. By presenting the note and communicating an appropriate investigative intention, the player can request the keys (KEYS) needed to enter the room.

The room contains an archived case file, CASE-R-456-19-872, together with associated images and physical evidence, CASE-456-19-872. This material expands the larger mystery surrounding the previous detective and the anomalous elements associated with Somnoryl-μ. The archive includes a missing-person report, travel-verification and welfare-check material, witness testimony, a supplemental anomaly memorandum, a closure notice, and associated visual material.

The room also creates a sequence focused on Julian’s vulnerability. Upon entering the dusty and neglected archive space, Julian experiences a severe allergic reaction. The player must use Julian’s auto-injector (AI) together with the adrenaline vial (AV) to stabilize him before continuing the search. This interaction provides a practical purpose for the adrenaline vial while also establishing that the detective is physically vulnerable and cannot treat the investigation as a purely abstract exercise in information management.

The sequence should be implemented carefully. Its function is not simply to create an arbitrary obstacle or a conventional item-use puzzle. It should reinforce the relationship between physical exploration, bodily fragility, institutional neglect, and the traces left by the previous investigation. The room therefore expands the narrative context of the mystery while remaining connected to the project’s central concern with knowledge, uncertainty, and interpretation.

#### Bathroom and Dream Entry

The unused bathroom accessible through the precinct corridor provides a separate location for initiating the dream sequence. The player must communicate an investigative reason for entering the neglected space and use Julian’s auto-injector with a Somnoryl-μ vial to enter the dream state. This creates a more coherent spatial and material framing for the dream–awake loop than an unrestricted or unexplained transition.

The revised dream interaction allows Julian to wake from the dream and return to the precinct without Captain Miller automatically forcing a final confrontation. The dream is therefore not treated as an ending or a failure state. It becomes a voluntary but consequential investigative action. Entering the dream consumes seven hours of the limited investigation period, making it a Kairos-related decision. The player must assess whether the potential symbolic and narrative value of the dream justifies the time lost for questioning suspects, requesting reports, exploring the precinct, or preparing the final case.

This design is important because it preserves the dream’s interpretive openness. The dream does not reveal a direct solution to Arthur’s murder. It instead confronts Julian with his desire for truth, the fragility of perception, and the possibility that seeing something does not guarantee understanding or acceptance. The player may return to the waking investigation with new questions about testimony, memory, responsibility, consciousness, and the difference between institutional proof and subjective experience.

#### Jail Floor and Resolution

The jail floor becomes accessible after the player presents a case to Captain Miller. This area provides a final narrative sequence in which Julian can visit Elara and Kae in their cells before the game concludes. The purpose of this sequence is to make the final judgment legible as a consequence of the player’s interpretation rather than as a purely abstract results screen.

The reactions of Elara and Kae can vary according to the evidence revealed during the investigation and the flags established through dialogue. For example, Elara’s reaction may differ depending on whether she was made aware of Kae’s deception, criminal history, confession, or possible sacrifice. Kae’s reaction may differ depending on whether he confessed, whether the player challenged inconsistencies in that confession, and whether Elara was accused despite his attempt to redirect responsibility.

After these conversations, Captain Miller communicates the institutional outcome. A final image summarizes the consequences for both suspects, followed by the credits. This structure allows the ending to retain emotional and narrative weight while preserving the principle that the player’s accusation emerges from their own interpretation of the available evidence.

## 7.2 Dialogue Logic Chains

## 7.2.1 Positioning the Dialogue Architecture

The Petri net and the Logic Chain system operate at different levels of abstraction. The net governs global state: room states, evidence acquisition, time, ending resolution. The chain system governs local dialogue resolution: which questions surface given the current evidence combination and character state. The net does not model dialogue content; the chains do not model global progression. The two coordinate through the flag space.

A Logic Chain is best understood as a unit of investigative reasoning rather than a unit of conversation. Where a dialogue tree treats a conversation as a self-contained interaction with a beginning and an end, a Logic Chain treats a line of inquiry as a structure that spans multiple conversations, develops across the investigation, and can be entered, interrupted, resumed, or abandoned according to the player's evidential position. The chain is not the conversation; the chain is the reasoning that the conversation makes visible.

Within this model, evidence operates as what the State of the Art described as a semantic key. An item of evidence is not defined by its physical utility but by the questions it makes available. When the player equips evidence before speaking to a character, they are not selecting a tool; they are proposing a relation. The system evaluates the relation against the chains that belong to that character and surfaces the questions the relation supports. The player's investigative intention is expressed through the evidence combination, and the dialogue content is a consequence of that expression rather than a menu of independent options.

This has three conceptual consequences that matter for the thesis's argument about epistemic agency.

First, the meaning of a clue is not fixed at acquisition. The same evidence item can surface different questions depending on which chain it is brought into. The gun does not mean "Kae is the killer" or "Elara handled the weapon"; it means different things in different evidential contexts. The player constructs meaning by deciding where to bring the evidence, not by receiving meaning from the game.

Second, character state is distributed across chains rather than contained within a conversation. Kae's willingness to discuss the gun is not a property of his dialogue tree; it is a property of how many chains the player has pursued. The progressive breakdown visible across his chains is not authored as a single arc. It is an emergent property of the architecture, where the accumulation of evidential pressure produces something that no single chain could produce alone.

Third, flags and slip events convert prior investigative work into later dialogue content. A flag set during one chain can condition a question in another, suppress a chain that would otherwise be available, or unlock a chain that only becomes reachable once a prior condition has been met. A slip event is the moment where the accumulation of evidential pressure produces a narrative rupture, a character involuntarily revealing something that the player did not directly ask for. These mechanisms are what make the investigation feel cumulative rather than episodic.

The conceptual model is therefore not "dialogue with evidence requirements." It is evidence-bound reasoning across a stateful character, where the player's investigative work shapes both what can be asked and what the character is willing to reveal. The technical description that follows in Chapter 8 explains how this model was implemented; the evaluation chapter that follows the prototype examines whether players experience the model as reasoning rather than as navigation.

The Logic Chain system is not represented as a sub-net within the Petri net. A complete net model of every chain, node, question, and response would produce a combinatorial explosion that would obscure rather than clarify the architecture. The chains are instead treated as a bounded subsystem that the net invokes and whose outputs the net consumes. This is consistent with the Petri net's purpose: to make progression conditions legible, not to model every internal state of every subsystem.

### The Design Problem

The rehearsal revealed five conditions that any digital dialogue architecture would need to satisfy.

First, evidence must determine which questions become available. Participants who approached a character without relevant evidence in their slots could not articulate an investigative intention. The system needed to make question availability a consequence of what the player has discovered, not a menu of options available to all players at all times.

Second, reasoning must extend across multiple turns and multiple conversations. The workshop sessions showed that participants did not resolve a line of inquiry in a single exchange. They returned to characters after acquiring new evidence, revised their questions, and tested the same topic from different angles. A single-conversation dialogue tree would not accommodate this pattern.

Third, inquiry and confrontation must be mechanically distinct. Participants used calm inquiry to gather information and direct confrontation to apply pressure. These were not interchangeable, and the workshop showed that participants adjusted their approach based on their read of the character and the strength of their evidence.

Fourth, characters must break down progressively rather than change state abruptly. Kae's willingness to discuss the gun, his financial situation, or Elara's condition was not a fixed property. It shifted across the investigation as evidence accumulated. A dialogue system that treats each conversation as a self-contained state change would not reproduce this.

Fifth, the system must be authorable within prototype scope. The thesis is a solo project with a bounded development window. A solution that requires an AI reasoning engine, a real-time drama manager, or exponential authoring across narrative branches was not achievable.

### Alternative 1: Branching Dialogue Trees

The most commercially dominant dialogue architecture is the branching tree, in which the player selects from pre-authored options that lead to distinct paths. This structure is familiar to players, straightforward to author per conversation, and clearly communicates player expression of intent.

It was not adopted because it localizes agency in outcome selection rather than interpretation. The player chooses which branch to take, but the meaning of the evidence has already been decided by the branch structure. This contradicts the thesis's central claim that agency should be epistemic. Additionally, the rehearsal demonstrated that the same evidence combination should produce different questions depending on what else the player has established. A branching tree would require every conversation to duplicate itself for every possible flag state, producing combinatorial authoring burden that would make the prototype unbuildable within scope.

### Alternative 2: Contradiction-Locking (Ace Attorney)

The Ace Attorney series, discussed in Section 2.6.3, established the most influential investigative dialogue mechanic in the medium, where the player presents evidence to disprove a specific statement, and incorrect evidence produces a failure state. This structure is dramatic, legible, and produces strong ludonarrative harmony between the mechanic of objection and the narrative act of truth-seeking.

It was not adopted because the rehearsal demonstrated that participants who presented incriminating but imperfectly matched evidence experienced the resulting silence as arbitrary rather than as meaningful resistance. Contradiction-locking requires the player to find the single correct piece of evidence for each specific lie.

Logic Chains invert the direction of interaction. Instead of "here is a lie, disprove it," the system asks _"here is what you have, what can you ask?"_ The player's evidence selection surfaces questions; the questions produce responses; the responses can be followed up or abandoned. This produces more forgiving evidential reasoning while preserving the possibility of meaningful failure through the Weak Question path. When the player presents evidence that does not match any chain in range, the system does not fail the interaction — it produces a diminished response, reduces patience, and leaves the chain intact.

The trade-off accepted is that the prototype gives up the single dramatic "Objection!" beat in exchange for more graded and cumulative reasoning. The confrontation with Kae builds across many chains rather than resolving in one decisive moment.

### Alternative 3: Simulated Social AI (Prom Week / CiF)

Prom Week, discussed in Section 2.4.3, demonstrated that a rule-based social simulation can produce emergent dialogue and meaningful player agency without exponential branching. Its Comme il Faut engine models social interaction through thousands of sociocultural considerations and produces responses that the designer did not pre-script.

It was not adopted because the thesis requires authored evidential precision. The false-confession path for Kae depends on specific evidence conditions being met and specific flags being active. The content of the confession is not generated, it is authored to produce a specific narrative rupture that the design depends on. A simulated social AI would struggle to produce this precise effect.

The more practical consideration is scope. Comme il Faut is a research-grade system that required years of development by a team. Reimplementing it for a solo prototype was not feasible.

The trade-off accepted is that dialogue content is authored rather than simulated. The player cannot ask questions the designer did not anticipate. This is a significant limitation, and the evaluation chapter should examine whether players experience it as a constraint on their investigative agency.

### Alternative 4: Façade's Drama Manager

Façade, discussed in Section 2.4.3, is the most theoretically ambitious resolution of the tension between authored narrative and player freedom. Its drama manager selects beats in real time based on tension state, producing a coherent Aristotelian arc even with free player input.

It was not adopted because Façade's beats are selected by dramatic tension, whereas the investigative content of _Oakhaven_ is structured around evidential relations. A beat system would need to be re-authored around an evidential graph, which would then require the same authored content that Logic Chains encode directly. The drama manager would not eliminate authoring; it would relocate it.

More fundamentally, Façade's arc is emotional escalation between two characters. The _Oakhaven_ arc is epistemic, the player's transformation from ignorance to knowledge. The selection criteria for beats would be different in kind, and adapting the drama manager to those criteria would constitute a new research project.

The trade-off accepted is that the prototype does not attempt global dramatic arc control. The Kairos mechanic converts incomplete investigation into a designed consequence rather than a failure state.

### Alternative 5: Disco Elysium's Skill-Check Gating

Disco Elysium, discussed in Section 2.5.4, gates narrative access through skill checks. Failing a check produces a different content branch rather than blocking progress, and the game treats failure as a source of narrative interest rather than a penalty.

It was not adopted because skill checks are **player-state-gated** rather than **evidence-gated**. The player's ability to progress depends on how they built their character, not on what they have discovered. The thesis requires that investigative work, finding, combining, and interpreting evidence, be the primary driver of progression. A player who has not discovered the relevant evidence should not be able to bypass a confrontation through a lucky roll.

The trade-off accepted is that the prototype does not model detective skills or character progression. This narrows replayability compared to Disco Elysium but keeps the focus on evidential reasoning.

### Synthesis: What Logic Chains Are

After positioning against these alternatives, the Logic Chain architecture can be described positively. It is an authoring structure that combines:

- **Evidence-bound questioning** from Ace Attorney, but without binary success/failure states.
    
- **Multi-turn progression across conversations** from Façade, but authored rather than beat-selected.
    
- **Stateful character memory** from Prom Week, but authored rather than simulated.
    
- **Progressive character breakdown** through cumulative evidential pressure, which is specific to this prototype.
    
- **Flag-conditioned question surfacing**, which allows the same chain to produce different content depending on the player's prior investigative work, without duplicating the chain.
    
- **Authorability within solo prototype scope**, which none of the alternatives achieve on their own.
    

The architecture is not a solution that supersedes any of these precedents. It is a design response to the specific combination of problems identified by the rehearsal, and it accepts the trade-offs named above.

### The Evidence the Content Provides

The Logic Chain content itself demonstrates capabilities that the alternatives could not produce within the same scope. Three examples illustrate this.

**Progressive character breakdown across chains.** Kae's response in `CHAIN_KAE_GUN` is defiant and composed:

> _"Yeah, it's my gun. But look, that model ain't exactly rare. Taurus 905s are all over this city…"_

By `CHAIN_KAE_TWO_SHAPES_FALSE_ALIBI`, the same character is visibly disintegrating:

> _"Don't. Don't make me answer that. Please. Every question gets me closer to saying something I can't take back, about either one of us, and I don't know which answer hurts less anymore."_

This progression is not authored as a single emotional arc. It emerges from the cumulative effect of multiple chains hitting the same character from different evidential angles. No single chain produces the progression. It is a property of the architecture.

Flag-conditioned question surfacing. The question _"Your manager at Greenway Market said you called out the weekend of the murder…"_ surfaces only when `FLAG_ELARA_WORKS_AT_MARKET` has been established elsewhere. This is not a branch. It is a conditional question inside a chain that would otherwise look identical. The player experiences different dialogue content based on prior investigative work, without the designer needing to author parallel versions of the same chain.

Multi-chain convergence. Four separate chains — `CHAIN_ELARA_BAREFOOT`, `CHAIN_ELARA_BLACKOUT`, `CHAIN_ELARA_SLEEPWALKING`, and `CHAIN_ELARA_TWO_SHAPES` — approach the same theme of Elara's altered state through different evidential angles. The player can enter through any of them. This is what makes the interrogation feel like construction rather than navigation. The same convergence appears across Kae's chains on Elara's condition and the false-alibi question.

### Trade-Offs Accepted

The architecture accepts four trade-offs that should be named explicitly.

**Authored content over emergent content.** The player cannot ask questions the designer did not anticipate. This constrains the range of investigative expression available.

**Legibility over mystery.** The system communicates which evidence unlocks which questions, though it does not tell the player what the evidence means. This distinction — legibility of operational rules versus opacity of interpretation — was central to the workshop findings and is preserved in the digital architecture.

**Evidence-bound reasoning over free-form reasoning.** The player's expression of investigative intent is constrained to combinations of evidence they have acquired. This is the price of evidence-gated progression.

**No binary success/failure states.** Failing to unlock a chain does not produce a game over. It produces a weaker investigative position, reduced patience, and the possibility that a later chain will not become available. The final accusation is the only place where the player can definitively fail.

These trade-offs are not weaknesses to be hidden. They are the conditions under which the prototype operates, and the evaluation chapter should examine whether players experience them as acceptable constraints on investigative agency or as limitations that undermine the intended experience.

### What the Architecture Does Not Claim

The Logic Chain system is not presented as a validated solution. It is a design response to problems identified during the rehearsal, translated into a technical architecture that could be implemented and evaluated within the constraints of a solo digital prototype. Whether it produces the intended experience of epistemic agency and whether players experience the dialogue as evidence-bound reasoning rather than as navigation through authored content.

Three specific risks should be named before the technical description proceeds.

Over-authoring risk. Logic Chains may produce a system that feels more like a dialogue tree than an interpretive act. If the player experiences the chains as a set of authored conversations to be unlocked rather than as a system that responds to their evidential reasoning, the architecture has failed at its central claim.

Legibility risk. The interaction between chains, flags, suppression rules, and reset packages may be invisible to players and therefore feel arbitrary. The workshop identified this as the central failure mode of the low-fidelity prototype, and the digital system must make operational feedback sufficiently clear without revealing interpretive content.

Scale risk. The authoring burden of chains may make the system impractical beyond a prototype. The content already developed for Elara, Kae, and Miller represents a substantial portion of the total dialogue corpus for a small case.

These risks are the subject of the evaluation chapter, and the technical description that follows should be read as the substrate for that evaluation rather than as a validated system.


# 7.3 Base Architecture: A Petri net-inspired state machine for Videogame Logic

## 7.3.1 The Architectural Problem

The prototype required an architectural layer capable of coordinating several systems whose behavior depends on one another. Evidence acquisition determines which dialogue options are available; dialogue outcomes set narrative flags; those flags gate spatial access; spatial access produces new evidence; and a global time limit constrains the entire process. A digital prototype cannot rely on improvised resolution to keep these systems consistent, so the architecture had to make the conditions of every interaction explicit and enforceable.

The approach taken was to adapt Petri net formalism into a custom state-machine notation focused on videogame logic. The result is a set of connected nodes, such as transitions, preconditions, output places, check nodes, and global room states, that together form the executable logic of the prototype. This architecture was converted into a human-readable reference document, the _state_machine_reference_ (Appendix X), which serves as design documentation, authoring aid, and debugging tool. The reference allows the designer to trace which conditions must be satisfied for any event to fire, which flags it produces, and which state it transitions into.

The architecture was adopted because conventional scripting does not provide the legibility the prototype requires. When a system contains many interdependent conditions, imperative code obscures the relationships between them: a failure may originate in any of several systems, and the designer must reconstruct the causal chain by reading multiple scripts. A Petri net treats state as an explicit marking and transitions as explicitly gated events, so the conditions of progression are visible rather than implicit.

It is important to clarify the role this architecture actually played in the prototype's development. The Petri net diagram and its derived reference document functioned as the _base architectural structure_ of the prototype: they defined the major systems, their entry and exit conditions, the flag space through which they communicate, and the primary progression paths from the intro sequence through investigation to the ending. They were not, however, an exhaustive specification that the implementation followed to the letter. As development proceeded, individual flags, transitions, and states were added, renamed, merged, split, or bypassed when the needs of the running prototype diverged from the initial diagram. Some interactions were implemented directly in script without a corresponding node in the net; some nodes in the net were authored as design scaffolding before their implementation was consolidated into a smaller number of runtime systems; and some transitions that appeared as distinct steps in the diagram were collapsed into a single scripted sequence once the surrounding systems were stable.

The architecture should therefore be understood in two registers simultaneously: as the conceptual model that gave the prototype its coherent structure, and as a living reference that was continually reconciled with the implementation rather than enforced as a rigid specification. The state_machine_reference documents the intended logic and the majority of the implemented logic, but it does not claim to account for every runtime condition, every edge case, or every flag that exists in the codebase. This distinction matters for the evaluation, because it means that the reference is best read as a map of the system's intended design rather than as a one-to-one description of its implementation.

## 7.3.2 Petri Nets and Their Adaptation

A Petri net is a modelling language for distributed systems. It consists of _places_ (conditions or states), _transitions_ (events or actions), and _arcs_ connecting them. A transition may fire only when all of its input places are marked. When it fires, it consumes tokens from its input places and produces tokens in its output places. This allows complex systems to be modelled without scripting every combination of conditions and outcomes, because the marking of places determines what can fire at any moment.

The adaptation used here departs from classical Petri nets in four ways.

First, the places are differentiated. The architecture distinguishes between _output places_ (persistent flags or state variables), _preconditions_ (conditions that must be satisfied before a transition can fire), _check nodes_ (branching evaluations that route to different transitions), and _global room states_ (the current explorable space, which exposes the interactions available within it). This differentiation allows the notation to express both persistent narrative state and spatial or modal state within a single formalism.

Second, transitions are named according to the action that triggers them and each produces a named output. This naming discipline allows the reference document to function as a catalogue: the designer can look up an interaction and immediately see its preconditions, its outputs, and its downstream consequences.

Third, the architecture uses flags as persistent marking. Rather than moving tokens between places, the system sets and clears flags. A flag that is set corresponds to a marked place; a flag that is absent corresponds to an unmarked place. This allows narrative state to persist across scenes, dialogues, and time transitions without requiring the entire net to be held in memory.

Fourth, the architecture introduces _subroutine pointers_ for sequences that recur or span multiple systems. A transition such as `MILLER_ANGRY_SEQUENCE` does not fire a single dialogue; it points to a sequence that may involve multiple dialogue pages, flag changes, and ending triggers. This keeps the net readable while allowing complex sequences to be authored as nested units.

## 7.3.3 The State Machine Reference

Once the architecture was authored, it was converted into a reference document that translates the graph into tables of states, transitions, and acquisition logic. The reference is structured into six sections, each answering a different design question.

**Game Flow States** lists every `GLOBAL_ROOM_STATE` and `OUTPUT_PLACE` node that represents a persistent room or game state. This section answers: _where can the player be, and what does each location expose?_ For example, `STATE_EXPLORING_EVIDENCE_ROOM` exposes the case folder, the computer, the locked room door, the corridor door, and the window. `STATE_EXPLORING_CORRIDOR_ROOM` exposes the bathroom, the observation room, the interrogation room, the evidence room, and the stairs.

**System-Level State Flags** lists every flag that represents a persistent systemic condition, the initial sequence, the case folder, the clock, the dream sequence, the ending sequence. Flags such as `INITIAL_SEQUENCE_COMPLETE`, `SLOTS_INVENTORY_ENABLED`, `INTERNAL_CLOCK_STARTS`, and `DREAM_EXPERIENCED` describe not only narrative conditions but the operational state of the prototype.

**Linear Sequence Events** describes the step-by-step progression from `GameStarts` to `EnableFreeRoam`. It traces the intro chain from the first Miller briefing through case folder acquisition, the second briefing, the fade into gameplay, and the activation of free-roam controls.

**Interaction Logic Table** lists every clickable object, dialogue trigger, computer submission, and countdown completion, together with its preconditions and its resulting state or flag. This is the primary reference for debugging, because it allows any failed interaction to be traced to a specific unmet precondition.

**Inventory & Evidence Acquisition** lists every transition that produces an acquired item, organized by acquisition method: starter files, computer-acquired reports, Miller-mediated acquisitions, event-acquired items, and consumable rules. It makes the evidence economy explicit, including the distinction between evidence acquired automatically, evidence requiring a tape combination, evidence delayed by a countdown, and evidence consumed on use.

**Ending & Outcome Logic** describes the ending entry gate, the reaction phase, the outcome phase, and the final ending flow. It lists the conviction flags that can be set during the confrontation, the branches that open depending on those flags, and the terminal states that can conclude the game.

## 7.3.4 How the Systems Connect

The value of the architecture is not that it models any single system particularly well, but that it models the connections between systems. Each system writes to and reads from the same flag space, and each transition can depend on flags set by any other system.

The examples in this section are drawn from the architecture as designed. The specific flag names and gate conditions changed as the prototype evolved; what remains constant is the pattern of cross-system coordination they illustrate.

Evidence acquisition is connected to dialogue through flags. When the player acquires `E2R` through the computer, the flag `E2R_ACQUIRED` is set. This flag is a precondition for the confrontation gate: the player cannot begin the final confrontation with Miller until `E2R_ACQUIRED` and `SUSPECT_INTERACTED` are both set. The confrontation itself is resolved by the Logic Chain system described in 7.2: `MILLER_CONFRONTATION_00` through `_04` are chain nodes whose entry conditions include these flags. The evidence system gates the chain system, and the chain system in turn produces the conviction flags that the ending system consumes.

Dialogue is connected to time through countdowns. When the player inquires with Miller using `E4R_EQUIPPED`, the transition `INITIATE_4H_COUNTDOWN_E4-TRACE` fires. This sets a countdown that produces `4H_COUNTDOWN_E4-TRACE_COMPLETE` after four in-game hours. The player can continue investigating while the countdown is pending. When it completes, the player can return to Miller to receive `E4-TRACE_ACQUIRED`. Time is therefore not an external constraint but an active participant in the investigation: requesting a report has an opportunity cost, and waiting for a report is a decision.

Dialogue is connected to space through flags. When the player inquires with Miller using `PK_EQUIPPED`, the flag `KAELEN_IN_IR` is set. This flag is a precondition for entering the interrogation room and interacting with Kae. Without it, the interrogation room denies entry and produces `JULIAN_IR_DENIED_00` since none of the suspects are inside the room. The player cannot access a space until the narrative has produced the condition for accessing it.

Ending resolution is connected to confrontation through conviction flags. During the confrontation chain (`MILLER_CONFRONTATION_00` through `_04`), the player equips evidence and triggers options. Depending on which evidence is equipped and which options are selected, conviction flags such as `ELARA_MURDER`, `ELARA_ACCOMPLICE`, `KAE_MURDER`, `KAE_GUN_POSSESSION`, and `KAE_ACCOMPLICE` are set. These flags are then read by `EndingManager` to resolve which ending path applies. The ending system does not re-evaluate the evidence; it reads the flags that the confrontation system produced.

## 7.3.5 A Concrete Trace

To make the architecture concrete, consider the sequence that leads from the initial briefing to the first suspect interrogation. 

The game begins with `GameStarts`, which sets `INITIAL_SEQUENCE_STARTED` and fires `MILLER_BRIEF_00`. On completion, `POST_BRIEF_00` is set. `Acquire.CaseFolder` fires, setting `CASE_FOLDER_ACQUIRED`. `MILLER_BRIEF_01` plays, setting `POST_BRIEF_01`. `INITIAL_SEQUENCE_COMPLETE` is set, and `FadeInGameplay` transitions to `EnableFreeRoam`. `SLOTS_INVENTORY_ENABLED` is set, and the player enters `STATE_EXPLORING_EVIDENCE_ROOM`. `INTERNAL_CLOCK_STARTS` begins the 36-hour countdown.

The player clicks the computer, setting `DISPLAY_COMPUTER_WINDOW`. They equip the Forensics Laboratory tape and `E2`. The `CHECKING_REQUIREMENTS` node evaluates the combination, and `Aquire.E2R` fires, setting `E2R_ACQUIRED`. The tape is ejected.

The player returns to the corridor and clicks the observation room door, entering `STATE_EXPLORING_OBSERVATION_ROOM`. They approach Miller and equip `E4R`. Miller's inquiry dialogue fires, and `INITIATE_4H_COUNTDOWN_E4-TRACE` is set. The countdown begins.

The player continues to the interrogation room door. `CHECKING_INTERROGATION_ROOM_STATUS` evaluates `SUSPECT_READY_FOR_INTERROGATION`. Because the player has not yet inquired with Miller using `PE` or `PK`, the flag is not set, so `InterrogationRoom.DenyEntry` fires and the player receives `JULIAN_IR_DENIED_00`.

The player returns to Miller and equips `PE`. `ELARA_IN_IR` is set, and the player can now enter the interrogation room. `STATE_EXPLORING_INTERROGATION_ROOM` is entered, and the player can interact with Elara using the two-slot system.

Four in-game hours later, `4H_COUNTDOWN_E4-TRACE_COMPLETE` fires. The player returns to Miller, and `MILLER_TRACE_00` plays, producing `E4-TRACE_ACQUIRED`.

The trace demonstrates how the architecture coordinates evidence, dialogue, space, and time without requiring any one system to know the internal details of another. The computer system does not know about the interrogation room. The interrogation room does not know about the countdown. Each system reads and writes flags, and the flags determine what is possible.

## 7.3.6 Design Consequences

The architecture produced several consequences for the prototype's development.

**Legibility.** Every system can be traced through the reference document. If an interaction fails, the designer can look up the relevant transition, identify which precondition is unmet, and determine whether the failure is intended or a bug.

**Debuggability.** Because all state is stored in flags rather than in hidden script variables, the current marking of the system can be inspected at any moment. The designer can see which flags are set, which transitions are available, and which sequences are pending. This made it possible to identify and correct inconsistencies as they emerged during development.

**Authorability.** Adding a new evidence item, dialogue chain, or spatial interaction does not require modifying existing systems. It requires defining a new transition with its preconditions and outputs, and connecting it to the existing flag space. This made it feasible for a solo developer to expand the prototype's content without creating cascading dependencies.

**Consistency.** Because every system uses the same notation, the prototype avoids the common problem of systems that work in isolation but fail when combined. The confrontation system depends on flags set by the dialogue system, the evidence system, and the time system, but because all three write to the same flag space, the confrontation system does not need to know how those flags were produced.

**Separation of concerns.** The architecture separates operational logic (what can fire and when) from narrative content (what the dialogue says, what the evidence contains, what the endings show). This separation allowed the narrative and dialogue systems to be developed independently of the underlying state machine.

**A design scaffold rather than a specification.** The architecture's most important contribution may be that it provided a shared conceptual language for the systems before they were implemented. Because the diagram and reference were authored before the corresponding scripts, they forced the designer to resolve questions about prerequisites, outputs, and cross-system dependencies _before_ those questions became entangled with implementation detail. This does not mean that the implementation matched the diagram exactly, but it means that the implementation was shaped by the questions the diagram made the designer ask. In practice, this produced a hybrid development process: the net served as the initial plan, and the implementation evolved from it through iterative reconciliation, with the reference updated when the divergence was significant enough to affect future authoring.

## 7.3.7 Trade-offs and Limitations

The architecture is not without limitations. The most significant is that the Petri net does not express the semantic meaning of flags. The system knows that `E2R_ACQUIRED` is set, but it does not know what `E2R` is or why it matters. The architecture can enforce operational consistency, but it cannot validate narrative consistency; the designer must still ensure that the flags correspond to meaningful narrative states.

A second limitation is readability at scale. The reference document is currently manageable because the prototype is small, but scaling to a larger investigation would require additional tooling. 

A third limitation is that the architecture does not model the player's cognitive state. It can track whether the player has acquired `E4-TRACE`, but it cannot track whether the player understands what `E4-TRACE` means, whether they have connected it to `E4R`, or whether they have formed a theory that explains it. This is not a flaw of the Petri net; it is a boundary of what any state-machine architecture can express. The dialogue architecture described in 7.2 is designed to bridge this gap by allowing the player's evidence selections to surface questions and interpretations, but the underlying state machine still only knows which flags are set.

A fourth limitation, already noted, is that the architecture was not implemented as a strict specification. Some runtime conditions, edge cases, and flags exist in the codebase without a corresponding node in the reference, and some nodes in the reference were superseded by a smaller number of runtime systems. This is a normal characteristic of architecture that is authored before implementation rather than extracted from it, but it means that the reference should not be treated as a complete description of the prototype's behavior. Where the reference and the implementation diverge, the implementation is the authoritative record of what the prototype actually does; the reference is the authoritative record of what the prototype was designed to do.

These limitations are the subject of the evaluation chapter, which examines whether players experience the architecture as a legible system or as an opaque set of conditions. The architecture was designed to make the prototype's logic traceable, but traceability is not the same as transparency. A system can be fully traceable and still feel arbitrary to a player who does not understand its rules. The evaluation must therefore examine not only whether the architecture works, but whether it produces the intended experience of epistemic agency.

## 7.3.8 Summary

This subchapter has described the base architecture of the digital prototype: a Petri net-inspired state machine adaptation focused on videogame logic, converted into a state-machine reference for authoring, debugging, and documentation. The architecture connects evidence, dialogue, space, time, and narrative consequence of a shared flag space, allowing each system to operate independently while remaining coordinated with the others. It functioned as the base architectural structure of the prototype rather than as an exhaustive specification, and was continually reconciled with the implementation as the prototype evolved. It provides the operational foundation for the narrative and dialogue systems described in 7.1 and 7.2. The following subchapter describes how this architecture was implemented in the digital prototype, including the evidence system, dialogue UI, countdown management, and ending resolution.