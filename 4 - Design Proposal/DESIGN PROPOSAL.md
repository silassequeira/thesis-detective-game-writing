# 4. Design Proposal

## 4.1 Concept Overview

#### Conceptual Origins

This design proposal emerged from an interest in detective narratives that combine familiar social environments with mystery, ambiguity, and psychological or supernatural elements. Works such as Twin Peaks, Gravity Falls, Sinister, IT, and Prisoners influenced the project's interest in situations where apparently ordinary events can support multiple competing interpretations. At the level of game design, Ace Attorney and Disco Elysium provided relevant references for their treatment of investigation, evidence, dialogue, and player interpretation.

These influences led to a specific design question: how might an interactive investigation treat interpretation itself as a playable activity? Detective games commonly ask players to search environments, collect evidence, question characters, and reconstruct events. Dream sequences, meanwhile, are frequently used to communicate psychological states, memories, or surreal narrative information. The project explores what happens when these two forms of interaction are brought into the same investigative structure: factual and indexical evidence in the waking world, alongside symbolic and affective material in a dream space.

#### Core Innovation

The central design proposition of this project is that player agency in detective games can be located in the construction, testing, and revision of interpretations rather than primarily in the selection of branching narrative outcomes.

The project therefore treats evidence not only as information to be collected or as keys to predetermined progression, but as material through which the player can express and test an interpretation of the case. A piece of evidence may be examined, compared with another item, presented to a character, used to request additional information, or incorporated into a developing theory. Its significance is consequently not determined only when it is acquired, but also through the relationships the player establishes between different pieces of information.

This proposition is operationalized through several interconnected systems. The Multi-Item Clue System allows evidence to fulfil different narrative and mechanical functions. The Two-Slot Epistemic Interaction System requires the player to select one or two pieces of evidence before certain investigative interactions, making the relationship between evidence an actionable part of the investigation. The Patience System introduces social consequences for unsupported or repetitive interrogation, while the Window of Opportunity, or kairos, mechanic makes timing and prioritization part of investigative decision-making. The optional Dream-Awake sequence extends this structure by introducing symbolic and affective material that can prompt the player to reconsider the meaning of waking evidence.

The project does not attempt to simulate unrestricted human reasoning or to eliminate authorial control over the investigation. Instead, it proposes a bounded interaction model in which the player must make evidential relationships meaningful through their own decisions while remaining within an authored narrative and evidence corpus.

#### Addressing the "Static Detective" Problem

The design problem addressed by this project is what can be described as the static detective problem. In this model, the player may perform the actions associated with investigation, while much of the interpretive work required to transform that information into knowledge is performed by the game itself.

This can occur when clues have predetermined meanings, when the protagonist automatically explains their significance, when progression depends primarily on selecting an expected dialogue option, or when the game's structure implicitly identifies the correct interpretation before the player has constructed one. Under these conditions, the player can participate in investigation without necessarily being responsible for building and testing a theory of their own.

The proposed system therefore seeks to shift investigative agency towards interpretation. The player must decide which information is relevant, which pieces of evidence can be meaningfully related, what questions those relationships support, when additional information is worth pursuing, and when a theory is sufficiently supported to justify a final accusation. Agency is consequently distributed across a sequence of investigative decisions rather than concentrated in explicit narrative branches.

This does not mean that every interpretation is equally valid or that the player can produce any possible theory. The case remains deliberately authored, and the digital prototype relies on structured evidential relations and authored dialogue responses. The design objective is instead to create a bounded space in which the player is required to perform meaningful epistemic work within those constraints.

The project therefore investigates whether detective gameplay can shift from a model in which the player primarily discovers and follows an authored solution towards one in which the player actively constructs, tests, revises, and commits to an interpretation of incomplete evidence.

**Chapter 4 — Design Proposal**

4.1 Concept Overview
4.01 ★ ® What are the research questions this proposal answers? Chapter 9 needs them to be named so each finding can be tied to one. — Open; canonical in the Introduction (parked)

> **RQ1: Epistemic Agency & The "Static Detective" Problem**

> _How can an interactive detective game shift player agency from discovering pre-authored deductions toward actively constructing, testing, and committing to an interpretation of incomplete evidence?_

> **RQ2: Dual-World Epistemic Inquiry (Symbolic vs. Indexical Evidence)**

> _How can a symbolic/affective dream space be mechanically integrated with factual/indexical waking investigation to function as an active tool for theory-building rather than an atmospheric or non-interactive interlude?_

>  **RQ3: Social Resistance &amp; Temporal Commitment (Kairos)**

> *How do systemic social friction (NPC Patience) and temporal constraints (the Window of Opportunity mechanic) influence investigative strategy and force epistemic commitment under conditions of uncertainty?*


4.02 ★ (R/L) Is the "static detective problem" your own term, or does it come from Fernández-Vara? If it builds on her critique, what does your version add? — ◐ Partly: 7.3.1 attributes the critique of automated deduction to Fernández-Vara; Ch4 needs to say so too, with the citation

> **Addressing the "Static Detective" Problem**

> The core design problem addressed by this project is what can be characterized as the **static detective problem**. This concept builds directly upon Clara Fernández-Vara’s critique of traditional detective game design. As Fernández-Vara observes, conventional mystery games frequently reduce the player's role to retrieving information while the software automatically performs the critical reasoning and deduction By treating clues merely as inventory keys that unlock single predetermined dialogue branches or automated deduction trees, the medium often minimizes the player's interpretive agency, reducing investigation to a sequence of mechanical unlocks rather than active sensemaking.

> While Fernández-Vara identifies this gap in existing detective fiction adaptations, this proposal extends her critique by operationalizing a mechanical solution. Rather than automating deduction or offering unconstrained narrative branching, the prototype introduces a bounded interaction framework. Through the **Two-Slot Epistemic Interface**, evidence items are reconfigured as active tools for hypothesis construction. The player must select, pair, and test evidential relationships against a suspect's epistemic resistance, shifting player agency from passively discovering pre-authored solutions toward actively constructing, testing, and committing to an interpretation under temporal (_kairos_) and social (patience) constraints.

4.03 ® What exactly did each influence give the project (Twin Peaks, Gravity Falls, Sinister, IT, Prisoners, Ace Attorney, Disco Elysium)? Keep only those you can name a specific contribution for. — Open 

> Some of these references are more related to my original design proposal that took place in a small town, these references need to be adjusted to new ones. Twin Peaks is still a reference, not fully explicit, but it's still a reference, having a whole mysterious surreal layer to the surface layer was inspired by this show's surreal dreams and dark lodge ideas. Gravity Falls the first season follows the same logic, having hidden notes, small details that hint at the full mystery that is only revealed in season 2. Ace Attorney and L.A noire, they're a reference because they operationalize in their own way, the deduction and presenting evidence during dialogue to put into action a similar concept to the Two-slot epistemic system used through out the thesis. Disco Elysium, I took more inspiration to the Dialogue Text focused style of gameplay they adopted, where they essentially managed make a reading game fun, besides that, the isometric style, and another feature, not really the main mechanic, but a feature present in the game where depending on the items that the player has equipped on the detective, different dialogue options appear in specific situations.  

4.04 ® Where should the game's title ("Moonlight") first appear? — ◐ Partly: 8.3.2 (Main Menu note) is currently the only place 

> This is a good question I don't currently have an answer to, is it important to state the name of the game ? 

4.05 ★ ® What is "bounded" in your bounded interaction model, concretely: the corpus, the number of pairs, the verdicts Miller accepts? — ◐ Partly: Ch8 Q16 (about 250 of 1,830 pairs authored) and Ch8 Q18 ("only the one the player is able to live with"); bring Q18's wording into 4.1

> "bounded interaction model" is still incomplete, there are combinations missing that are not implemented in the game, the logic chains and the options inside can only be validated through playtesting. What I meant with "only the one the player is able to live with", depends on the player's interpretation of the case and whether it was satisfying enough based on the evidence or not, it's not something measurable since it's related to the person's internal resolution, and assuming that they would want to play again to find a missing answer they weren't hoping for. That's why I don't understand the question. 
> 
> the three concrete boundaries I designed into the system are: 
> 
> **The Corpus Boundary:** Investigation is restricted to a finite, authored pool of evidence items (rather than an open-ended database or free internet search), and what each evidence is able to produce in terms of knowledge depends on the player reading it and its interpretation, but it's limited in the sence that there's no more evidence that the game can provide, so the player needs to stick with the evidence he's able to gather. 
> 
> **The Interaction Boundary (Two-Slot Interface):** Instead of letting players type anything into a chat box (unconstrained) or clicking a generic "Ask About Crime" button (passive), interaction is bounded by having one or two evidences in the slot interface and bounded to the context of the logic chain, or logic of the argument the player is trying to go with.
> 
>**The Institutional Boundary (Miller's Evaluation):** The final accusation sequence is bounded by what the evidence flags can logically support. Captain Miller will not accept an accusation if the player has no evidence flags to back it up.
>
> Crucially, within these boundaries, the system never declares a player's hypothesis 'correct' or 'incorrect' By restricting Miller's acceptance to evidence-backed arguments while leaving room for competing interpretations, the bounded model transfers the moral and epistemic weight of the verdict entirely to the player—requiring them to commit to **only the interpretation they are able to live with**

4.06 (R/L) Where do you introduce the neo-Aristotelian frame (Mateas & Stern, formal vs material constraints) as one of the thesis's five concepts? — ◐ Partly: it first appears in 7.3.1; decide whether Ch4 or the SotA introduces it 

> **The Neo-Aristotelian Framework of Epistemic Agency**

> To balance player agency with structured mystery resolution, the design proposal adopts the **neo-Aristotelian theory of interactive drama** formulated by Mateas and Stern (2004), building upon Brenda Laurel's (2014) dramatic model. In this framework, genuine dramatic agency is produced not through unconstrained freedom, but through a structural balance between **formal constraints** from above (authorial plot necessity, dramatic probability, and system rules) and **material constraints** from below (interface affordances, available clues, and character state)

> In this project, this dual causality is reconfigured for an epistemic narrative:

>**Material Affordances (Bottom-Up):** The **Two-Slot Epistemic Interface** and evidence corpus provide the material means through which the player constructs conversational hypotheses, selecting and presenting clue pairings to interrogate suspects

> **Formal Constraints (Top-Down):** **NPC Patience**, **diegetic time costs (** **kairos** **)**, and logic-chain rules govern how suspects yield or resist, narrowing the dramatic probability space toward a resolution without the engine ever revealing an objective 'truth' flag

4.27 ★ ® What does epistemic agency mean here, as distinct from narrative choice and from freedom to conclude anything? Which freedoms does the player have (which evidence, which question, when to accuse, which theory to commit to), and which not? — ◐ Partly: 4.1 ("bounded space") and Ch8 Q18

>  **Defining Epistemic Agency in a Bounded Architecture**

> Within this proposal, **epistemic agency** is defined as the player's capacity to perform nontrivial cognitive labor—discovering, selecting, pairing, and interpreting evidence to construct and test provisional hypotheses. Epistemic agency operates distinctively from both traditional narrative branching and unconstrained sandbox play:
> **Distinct from Narrative Choice:** Rather than selecting explicit plot branches that alter external story trajectories, the player exercises agency internally over the _process of investigation itself_—deciding which clues are relevant, what questions those clues support, and how to resolve conflicting testimonies
> **Distinct from Unconstrained Freedom:** Epistemic agency does not grant the player freedom to invent any arbitrary conclusion. The interaction space remains strictly bounded within an authored corpus of 61 evidence items and the logic of the argument or in the digital prototype with the logic chains. 

> Under this model, player freedom is specifically allocated across four investigative dimensions:

> 1. _Evidential Freedom:_ Selecting which physical stations, documents, and forensic reports to examine
> 2.  _Interrogative Freedom:_ Deciding which evidence items to use in the Two-Slot Epistemic Interface to test conversational hypotheses against suspect resistance
> 3. *Temporal Freedom (* *Kairos* *):* Deciding when an investigation is sufficient and when to trigger the final accusation under conditions of temporal scarcity
> 4. _Interpretive Freedom:_ Choosing which defensible narrative theory to present to Captain Miller. Conversely, the system deliberately restricts player freedom by fixing the underlying past events of the crime, limiting valid dialogue prompts to authored logic chains, and rejecting accusations unsupported by evidence. Crucially, because the game engine evaluates evidential relevance rather than declaring an objective 'truth,' the system leaves the final burden of conviction on the investigator—requiring the player to commit to his theory and interpretation of the case and present evidence that supports it.

---
## 4.2 Core Design Systems

The following systems were designed as interconnected attempts to operationalize epistemic agency within a bounded interactive detective narrative. Rather than locating player agency only in branching dialogue choices or final outcomes, the proposal distributes it across the processes of discovering, selecting, combining, presenting, delaying, and reinterpreting information.

The intention is not to simulate unrestricted human reasoning or to create an infinite number of possible narrative paths. Instead, the prototype explores whether a player can be encouraged to experience investigation as an active process of interpretation. The player is asked to consider what a clue means, how it relates to other information, when it should be used, who it should be presented to, and whether a current interpretation is sufficiently supported. In this way, the systems attempt to shift the player from the role of someone who merely retrieves information into the role of someone who constructs provisional knowledge.

**4.2 Core Design Systems**
4.07 ® Do the five systems named here match exactly the "five core epistemic mechanics" Chapter 8 refers to? — ↪ Answered: Ch8 Q2 ("provide context of the design proposal chapter"); check the names match word for word

4.08 ® Pick one name each for the dream system and the two-slot system. The drafts use "Dream-Awake sequence", "Dream Sequence Mechanic" and "Dream–Awake Epistemic Loop", and both "Interaction System" and "Interface". — ◆ Decision; canonical for system names (G01) 

> The canonical name for both systems will be the "Dream Sequence" and the "Two-Slot Epistemic Interaction System" what do you think ? 

4.30 ® How do the five systems depend on each other? A diagram may be enough here. — ◐ Partly: 7.2.1 (evidence → dialogue → flags → space → time) and 8.1.2 (one gesture across five systems) 

> I'll build the diagram then. 

---

### 4.2.1 Multi-Item Clue System

The Multi-Item Clue System proposes that evidence should not function only as an inventory object or as a single-use key that unlocks the next predetermined event. Instead, a clue is treated as an epistemic object: something that can be collected, read, inspected, organised, compared, presented in dialogue, or used to access further information depending on the context of the investigation.

A clue can therefore occupy multiple roles at the same time. It may be a physical trace found in the environment, a document containing factual information, a possible contradiction of a character's testimony, a component of a theory, or a social lever that changes the direction of an interrogation. Its meaning is not fixed when it is acquired. It becomes meaningful through the relations the player constructs around it.

Evidence in this system is designed to serve multiple simultaneous functions, collapsing the traditional separation between inventory mechanics and narrative mechanics:

- Physical inventory item (carried, manipulated, used as a tool)
- Dialogue evidence (presented to NPCs to elicit responses)
- Conceptual clue (contributes to case-building and theory construction)
- Social lever (influences NPC behavior, unlocks doors, creates opportunities) Objects can also function in conversations.

This approach is informed by indexical storytelling, where evidence functions as a trace that points towards an absent event rather than revealing its meaning automatically (Fernández-Vara, 2011). A clue such as a report, object, image, or testimony does not simply tell the player what happened. It invites the player to ask what it implies, what other traces it relates to, and which interpretation it supports. The system therefore attempts to make the process of moving from trace to hypothesis part of the gameplay itself.

**4.2.1 Multi-Item Clue System**
4.09 ® Which single item in the case shows all four roles at once (inventory item, dialogue evidence, conceptual clue, social lever)? — Open 

> I think the best answer here is the E15, the moon drug vials, since the player is able to use it in dialogue to confront or inquiry both suspect with it, in certain contexts, since it's a physical clue, the player would be able to manipulate it such as rotate it, or use it as a valid intention to force the bathroom door open, it's also a conceptual clue, since the player can analyze it, and notice that one contains more of the substance than the other, and as a social lever, it creates the opportunity to enter the dream sequence.

4.10 (V) Which items act as "social levers" in the build? — ↪ Answered: 8.1.2 table (keys, Somnoryl-μ vials + Auto Injector, Locked Door Note) and Ch8 Q31 (PE/PK portraits shown to Miller)

---
### 4.2.2 Two-Slot Epistemic Interaction System

The Two-Slot Epistemic Interaction System provides the main interaction structure through which the player can express an investigative interpretation. Before questioning a character, confronting them, or interacting with particular investigative systems, the player can equip one or two pieces of evidence. This act of selection communicates what the player considers relevant at that moment.

The two slots are not intended only as an inventory-management feature. They form a small and accessible language of evidential relation. One item can communicate a direct inquiry about a clue, while two items can communicate a comparison, contradiction, association, suspicion, or possible causal relationship. For example, the player may present a testimony alongside a forensic report in order to question whether the two accounts can coexist.

This system is influenced by the Logic mechanic discussed in Ace Attorney Investigations: Miles Edgeworth, where the player is asked to connect pieces of information rather than allowing the protagonist to make every deduction automatically. However, the two-slot system does not attempt to formalize all possible forms of deduction. It provides a constrained interface through which players can make a current interpretation actionable. The player still operates within authored evidence relations and narrative possibilities, but must participate in selecting the grounds from which an interaction can occur.

The system is also connected to Aarseth's concept of ergodic effort. The player does not only read or receive the investigation; they must perform work by retrieving evidence, reviewing it, selecting it, and testing its relevance in a particular situation. This is intended to make investigation feel less like progressing through a checklist and more like constructing and revising a working theory.

**4.2.2 Two-Slot Epistemic Interaction System**

4.11 ★ ® Why two slots, not one or three? — Open; canonical here (Ch8 Q7 links here, and 8.1.3 only adds the implementation consequences)

> I chose two slots, because it's easier to explain, as it's explained in the Memo Tutorial report: "You always have up to two slots available when interacting. Slot A – left hand; Slot B – right hand; You can: Equip one piece of evidence.; Equip two pieces of evidence that make sense together. If Slot A and Slot B support the same idea , they become a stronger argument." The way I explain is that kinda like in detective television shows, where they are interrogating a suspect, in an argument they would present the report/image to inquiry or confront during an interrogation, and they physically have the actual evidence up to two, since one hand is holding an evidence and the other hand holds another. The two slot system attemps to recreate this logic, where you physically hold in one hand or the other the evidence you want to use in a interrogation, or action in general since usually there's not a third, or just one hand in these situations. 

4.12 ® How does the two-slot system differ from Edgeworth's Logic and from Ace Attorney's "present evidence"? What can it express that they can't? — Open

> **Divergence from Capcom’s Mystery Mechanics**

>The **Two-Slot Epistemic Interaction System** diverges fundamentally from _Ace Attorney_’s "Present Evidence" and _Miles Edgeworth_’s "Logic" across three core dimensions:

>- **Vs.** **Ace Attorney** **("Present Evidence"):** Standard _Ace Attorney_ uses a **reactive, 1-to-1 binary lock-and-key** structure (presenting one item to contradict one statement line during cross-examination). By contrast, the Two-Slot system is **proactive and relational**: the player equips up to two items (_Slot A_ and _Slot B_) from their evidence corpus to frame a conversational proposal _before_ engaging a suspect.
>- **Vs.** **Edgeworth’s** **"Logic":** Edgeworth’s system pairs two thoughts inside an **internal, abstract mind menu**, executing an automated deduction that advances a linear plot. In contrast, the Two-Slot system **externalizes clue pairing into a world-facing interaction primitive**. It surfaces questions that must be actively tested against a suspect’s **epistemic resistance** rather than automatically solving the mystery in the detective's head.

> **Expressive Capacity: What the Two-Slot System Expresses**

>By expanding clue presentation from a single item to a two-slot relational pairing, the system introduces a richer grammar for investigative intent:

>1. **Relational Semantics:** Expresses comparison, contradiction, or association between two distinct traces (_"How does Suspect Account A relate to Forensic Report B?"_) rather than a simple single-item check (_"Tell me about Item X"_).
>2. **Dual Operational Register:** The same clue pairing can be deployed as an **Inquiry** (soft probing without social penalty) or a **Confrontation** (accusatory pressure that risks NPC Patience to build Case Strength).
>3. **A Unified Interaction Verb:** Acts as a single interaction primitive across the entire game world—used for dialogue interrogations, physical door unlocks, database terminal queries, survival choices, and entering the **Dream Sequence**.
>4. **Non-Confirmation of "Objective Truth":** Evaluates local evidential fit rather than binary correctness. Out-of-range pairings trigger suspect deflections, while valid pairings surface ranged logic-chain questions—leaving the final burden of conviction on the player to commit to _only the interpretation they are able to live with_.

4.13 (L) Which Aarseth work and concept are you using (ergodic literature, nontrivial effort)? Add the citation. — Open

> In conventional detective games, deduction is often "trivialized" or automated by software prompts. In the prototype, the **Two-Slot Epistemic Interface** and evidence corpus require **nontrivial ergodic effort**—the player must physically and cognitively retrieve, pair, and present evidence to frame inquiries and confrontations, making hypothesis construction a player-driven ergodic act. (Aarseth, 1997, pp. 1–2) Aarseth, E. J. (1997). _Cybertext: Perspectives on Ergodic Literature_. Baltimore: Johns Hopkins University Press

4.28 ® What separates a combination the system recognises from an inference the player has actually made? — ◐ Partly: 8.1.3 "Where the evaluation stops" (the evaluator judges relevance, not truth)

> * The game evaluator **only judges local evidential relevance, not global truth or internal player thoughts**.
>* The game engine does **not** evaluate whether the player's overarching theory is "true." It only verifies whether the two equipped clues form an authored, relevant argument in that conversation.
>* The system provides the **expressive vocabulary** (surfacing a specific question), but the cognitive burden of synthesizing the clues into an actual inference remains 100% inside the player's mind.

> What this means in practice, is that the game doesn't attempt to cover every single player inference, but provides a question and response that attempt to satisfy the player epistemic search of gathering more information, the idea with the system is to provide valid combinations based on the possible grammar or intention the player is trying to communicate to get the system to have for them, of course there's always the limitation of the system not covering every single inference, and that's why it requires a lot of playtesting and reviewing, but the idea is to satisfy the player's intentions within a certain context, and limiting or punishing inferences that don't match the context they are trying to present it in. 

4.29 ★ ® What happens when a player's reasonable interpretation was not anticipated by the author? — ◐ Partly: 7.3.2 trade-offs ("Authored content over emergent content") and the note after them, 8.1.3 weak questions, Ch8 Q15 (ranges grow with playtesting) 

> If it's a reasonable interpretation, the author should be able to cover since it will be backed up by evidence, if it's not there and it's valid, then the author needs to add it, if not the game and it's systems have way of riderecting the player to review the evidence and create a more defensable interpretation.

---
### 4.2.3 Patience System

The Patience System introduces social consequence on the investigative process. In many detective games, characters can be treated as information dispensers: the player can repeatedly ask every available question, test every dialogue option, and eventually exhaust the conversation without meaningful cost. This proposal instead treats access to information as dependent not only on the investigative effort, and theory building, but also on the character's willingness to engage, based on their narrative constraints.

Each major character has a limited patience value that is reduced when the player commits to an active line of questioning and selects an unsupported or weak argument. While freely examining or equipping evidence outside a logic chain carries no social penalty, making missteps within an active interrogation drains character patience, weakening the player's conversational position and temporarily shutting down dialogue until a cooldown period passes. The character may stop cooperating temporarily, or the player may need to wait before returning to the interaction.

The purpose of this system is not simply to punish failure. It is to make unsuccessful or premature investigative actions meaningful. A weak confrontation can reveal that the player's theory is not yet sufficiently grounded, that the evidence has been misread, or that another route must be pursued before the character can be approached again.

This system relates to the discussion of Disco Elysium, particularly its use of constraints, failure, and social reactivity to create meaningful agency. The player is not given unlimited freedom, but their actions alter the dramatic conditions of the interaction. In this prototype, patience makes dialogue a social negotiation rather than a neutral menu of information, where failure is intended to motivate the player to investigate further and solidify their theory.

**4.2.3 Patience System**
4.14 ★ ® Patience in the build drops only when the player picks a weak question inside an active chain; looking at evidence outside a chain is free. Ch4 says it drops for "irrelevant evidence" in general. Is 8.1.3 the design you intend? — ⚠ Conflict (most likely outdated prose): 8.1.3 "Social friction" ("the social cost attaches to arguing badly, not to looking")

> Yes, Section 8.1.3 represents the intended final design. During digital prototyping, the patience mechanic was refined so that patience is only consumed when a player selects a weak question inside an active logic chain. Exploring or equipping evidence combinations outside an active chain costs no patience, ensuring the social cost attaches to *arguing badly within a committed argument* rather than *freely experimenting with evidence*. Chapter 4.2.3 will be updated to reflect this distinction.

4.15 ® Ch4 says the player's "conversational position becomes weaker". By design, how should the player perceive that, given there is no meter? — ◐ Partly: Ch8 Q55 (patience not shown; only the hidden out-of-range text). Whether players actually perceive it → Ch9

> The conversation position becomes weaker, because the player could fail to present relevant evidence within that context, and deplete the character's patience. Depending on the situation, two consequences happen with this, the player looses time, having to wait in order to talk with the character again, or triggers an action from Miller, with Miller either warning the player of the consequence of his actions, or forcing him to present the case or be fired, how this situation is handled depends on the player and his previous investigative progress and time. Basically the player knows by the character's reaction, and his conversational position gets weaker the more he presses down a character. 

4.16 ® Which Disco Elysium mechanic exactly are you comparing to (skill checks, NPC reactivity, failure as content)? — Open

> The Patience System draws directly upon the design principles of _Disco Elysium_ (ZA/UM, 2019), specifically its use of **social reactivity** and **failure as narrative content**, while deliberately departing from its RPG skill-check mechanics. In _Disco Elysium_, NPCs react dynamically to player posture rather than acting as neutral dialogue menus, and failed interactions branch the narrative into new dramatic directions rather than terminating play. The prototype operationalizes these two principles within an epistemic framework:
> _Social Reactivity:_ Suspects actively resist interrogation, altering their emotional state and cooperation level based on the quality of the player's evidential proposals
> _Failure as an Investigative Signal:_ Exhausting a suspect's patience or failing a confrontation is treated as a meaningful dramatic beat rather than a binary game-over. A patience breakdown provides in-fiction feedback that the player's current hypothesis is insufficiently supported, compelling them to re-examine case files and reconstruct their theory. 
> Crucially, the prototype diverges from _Disco Elysium_ by omitting dice rolls, skill stats, and automated skill-check deductions. Rather than relying on character stats to solve clues, the system requires the player to perform all cognitive synthesis.

---
### 4.2.4 Window of Opportunity: A Kairos Mechanic

The Window of Opportunity mechanic introduces time as an investigative and interpretive condition. The prototype contains a finite investigation period, but the function of time is not only to create a countdown or pressure the player to think of the consequences of their actions. Time is also connected to the idea of kairos: the appropriate, consequential, or strategically meaningful moment for action.

The player may possess a clue without yet being ready to use it effectively. A character may not be available, a line of reasoning may still lack support, an evidence request may still be processing, or a previous interaction may have exhausted a character's patience. The relevant question is therefore not only "What evidence do I have?" but also "Is this the right moment to act on it?"

The player must decide whether to continue exploring, wait for information to become available, recover a damaged conversational interaction, or proceed with an incomplete but potentially urgent theory. This transforms time from a purely external limitation into part of the player's reasoning process.

The mechanic connects to the State-of-the-Art discussion of conceptual and informational gating. As in games where progression depends on knowledge rather than only on physical access, the player's obstacle is not always a locked door or missing object. It may be a lack of readiness, sufficient context, social opportunity, or confidence in an interpretation. The prototype therefore combines chronological time with epistemic timing: not just how much time remains, but what can meaningfully be done with the time that remains.

**4.2.4 Window of Opportunity (Kairos)**
4.17 ★ (L) Which source do you cite for kairos? — ◐ Partly: Ch8 Q34 says it is cited earlier; confirm it is in the SotA and add the reference here too

> The **Window of Opportunity** mechanic introduces time as an investigative and interpretive condition. While traditional game timers operate as quantitative countdowns (_chronos_), this mechanic operationalizes the classical concept of **kairos**: the opportune, qualitative, and strategically meaningful moment for action (Aristotle, 1954; Sipiora & Baumlin, 2002)
> This system directly builds upon the State of the Art discussion in Chapter 2 regarding **temporal agency** and the **chronotope** (Bakhtin, 1981; Aarseth, 1997).
> As demonstrated in early time-sensitive detective games like _Deadline_ (Blank, 1982), progression depends not merely on physical presence or possessing an item, but on **epistemic timing**—whether the player possesses the necessary context, social readiness, or supporting evidence to act before a fleeting window closes.
> In the prototype, time is thus transformed from an external pressure into an internal component of the player's cognitive reasoning process.

4.18 ★ ® One in-game hour equals one real hour, so pressure comes almost entirely from spending time (waits, lab delays, cooldowns, the dream's 6 h). Should time be described as a countdown or as a currency? — ◆ Decision; canonical for time (G03). Facts: 8.1.6 ("time being more of a currency") and Ch8 Q33. Then update 4.2.4, 6.2.5 and the 8.3 "Space and Time" paragraph

> Ok in this specific example, it depends, since on average people who play tested the prototype, took on average 3h to 5h, when the player engages this long with the digital prototype, these 3 to 5 hours could be the difference between being able to gather another report or press a suspect further. So in practice it's both a countdown and a currency. 

> **As a Countdown (** **Chronos** **):** The global 24-hour clock acts as an overarching structural container. By running continuously in real time (1 in-game hour = 1 real hour) and displaying a 12-hour warning threshold, it provides ambient narrative urgency and enforces an absolute institutional deadline for Captain Miller's final accusation sequence.

> **As a Currency (** **Kairos** **):** Within a typical 3-to-5-hour playtest session, spatial exploration consumes only a fraction of the clock. Instead, investigative pressure is driven by deliberate temporal expenditures—where the player trades hours as a currency to purchase delayed forensic reports (e.g., 8 hours for `E4-TRACE`), pay social penalties for poor interrogations (2-to-3-hour NPC patience cooldowns), or finance surreal exploration (a 6-hour deduction upon returning from the dream).

> **Thesis Application:** Across Chapters 4.2.4, 6.2.5, and 8.1.6, time should be defined as **"epistemic time currency bounded by an institutional countdown,"** emphasizing that the primary player choice is not *beating the ticking clock*, but *deciding which investigative leads and actions are worth the temporal investment*.

4.19 (R/L) Which games from the SotA do you mean by "conceptual and informational gating"? Name them. — Open

> Grounding in Knowledge-Based Gating

> The *Window of Opportunity* mechanic directly operationalizes the models of **conceptual and informational gating** analyzed in the Chapter 2 State of the Art (Section 2.6.2):

> * **Conceptual Gating (** **Outer Wilds** **):** Where physical obstacles are replaced by player ignorance, and progression is unlocked through mental breakthroughs rather than inventory keys.
> * **Informational &; Linguistic Gating (** **Her Story** **,** **Telling Lies** **):** Where access to narrative fragments is gated by the player's vocabulary, search queries, and hypothesis framing.
> * **Deductive &; Spatial Gating (** **Return of the Obra Dinn** **,** **Shadows of Doubt** **):** Where progress requires cross-referencing indexical traces and committing to deductions within an informational workspace.

> In conventional games, an obstacle is an ontic barrier—a locked door or a missing key. In these knowledge-based exemplars—and in this prototype—the obstacle is an **epistemic threshold**: a lack of contextual readiness, an unrecognised social opening, or an unconfirmed interpretation. The prototype synthesizes these models by coupling chronological time with **epistemic timing**: requiring the player to possess not just the physical clue, but the necessary social context and interpretive confidence before a fleeting temporal window closes.

---
### 4.2.5 Dream Sequence Mechanic

The Dream Sequence Mechanic introduces an alternative mode of investigation based on symbolic and affective interpretation. While the waking investigation is primarily concerned with physical traces, testimonies, documents, access, and contradiction, the dream sequence creates a different kind of epistemic space. It allows the player to engage with images, atmosphere, memory and symbolic relations that cannot be approached in the same way through factual evidence alone.

The dream should not be understood as a passive cutscene or simply as an atmospheric interruption. It is proposed as a navigable and interpretable environment. The player is still required to explore, notice, associate, and form a possible understanding of what is being represented. However, the object of investigation shifts from the direct reconstruction of external events towards the interpretation of symbolic mysterious messages.

This approach develops the discussion of dreamscapes in the State of the Art, particularly the idea that surreal environments can function as symbolic texts. As in Yume Nikki, Alan Wake, or the dream sequences of Max Payne, the player is not necessarily presented with literal answers. Instead, they are invited to recognize patterns, motifs, spatial distortions, and emotional associations that complicate the meaning of the waking narrative.

**4.2.5 Dream Sequence Mechanic**

4.20 ★ ® What does the dream do for the waking investigation in the build: does it set a flag, unlock a question, change any dialogue? — ⚠ Conflict; canonical for the dream (G05). 5.2.7 says it "unlocks no additional physical clues"; 6.4.5 says it should open new waking lines of inquiry; Chapter 8 doesn't say

> Currently it sets a flag, and set E15 evidence to used, with the player not being able to engage with the dream sequence again, it also costs time 6h, and can trigger the Miller Angry Sequence, so in a certain way, it does have consequences in the waking investigation, but currently due to the time limitation, scope and being a solo developer I still haven't been able to focus on integrating that action into new questions, or new dialogue options, but it's something to implement in the future, and it's core to the narrative. Being a possible and actionable decision in the workshop where participants actually made questions to the captain after the dream sequence. Plus the idea is to complicate or help with the investigation and interpretation that the player builds while awake, aiming to give a symbolic suggestion with the power to influence the investigation on a interpretation level.


4.21 ® What does each reference give you (Yume Nikki, Alan Wake, Max Payne)? — Open

> Yume Nikki - Navigation as Decoding -- Stripping away dialogue/UI to turn spatial exploration into the act of reading symbolic motifs

> Alan Wake - Psychological Projection & Dream Logic -- Using environmental symbolism and recurring motifs to open non-conclusive lines of waking inquiry

> Max Payne - Substance & Affective Reenactment -- Framing Somnoryl-μ consumption as a distorted, drug-induced state that communicates parasomnia and hints at a unconscious level of symbolic revelation. 

## 4.3 Expected Contributions

This design proposal (consisting of ideas that require testing) aims to contribute to the field of interactive narrative design by :

1. Operationalizing Epistemic Agency: Proposes a theoretical framework for distributing agency through interpretation;.

2. Integrating Symbolic and Indexical Storytelling: Testing the epistemic impact of a dream-based symbolic investigation in a indexical type investigation.

3. Social Systems as Investigative Tools: Exploring whether NPC patience constraints, and constrained time window can create emergent narrative complexity within a bounded narrative scope.

4. Challenging the Static Detective Problem: Offering an alternative to automated deduction and quest-marker-driven investigation by requiring active cognitive synthesis where the player is instead actively constructing, testing, and committing to an interpretation of incomplete evidence.

5. How a fragmented indexical tracess of evidence can be created to suggest different interpretations and investigation playstyles, and whether it results in more perceived agency. 

By treating mystery not as narrative content but as the structural foundation of agency, and by recognizing that atmosphere is epistemic infrastructure, this project seeks to advance understanding of how cognitive labor, and emotional resonance can combine to produce meaningful, intellectually engaging interactive experiences.

**4.5 Expected Contributions**
4.22 ® Sections 4.3 and 4.4 are missing. Were they cut, or does this become 4.3? — Open 

> I've changed to 4.3, the other sections were abandoned systems from the previous prototype. 

4.23 ® For each contribution: is it a design proposal, something implemented, or something tested in Ch9? The verb follows from that ("proposes", "implements", "examines"), not a blanket change to "exploring". — Open

4.31 ★ ® What player behavior would show the core proposition did not work: brute-forcing pairs, always taking the first question offered, never revising a theory? Write it down before reading the Ch9 data. — Open → used in Ch9

> For the evaluation to show that the core proposition did not work, the playtest analysis would have to show that:  1. players didn't feel like they were doing themselves the deductions and that their investigation decisions were done by the game and not based on their actual cognitive behavior.  2. They never explored or showed curiosity in exploring the dream sequence, or the affordances in the digital prototype aren't enough for the player to engage with the symbolic dream in the first place, so It never returns any observations related to it, of course to fully validate the success it would require a lot more tests to see if a pattern appears from the player's engaging with the game. 3. If player always made the same interpretation and the final branching resolution feels rigged to a single outcome. 4. If the social and time constraints are not felt and don't lead the player to explore better and more meaningful investigation paths.  

4.26 (D) For each contribution, which Ch9 data will support or weaken it? — Open → Ch9