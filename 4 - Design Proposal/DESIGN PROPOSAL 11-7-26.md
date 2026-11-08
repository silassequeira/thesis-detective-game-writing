# 4. Design Proposal

## 4.1 Concept Overview

#### Conceptual Origins

This design proposal emerged from an interest in detective narratives that combine familiar social environments with mystery, ambiguity, and psychological or supernatural elements. Works such as Twin Peaks, Gravity Falls, Sinister, IT, and Prisoners influenced the project's interest in situations where apparently ordinary events can support multiple competing interpretations. At the level of game design, Ace Attorney and Disco Elysium provided relevant references for their treatment of investigation, evidence, dialogue, and player interpretation.

These influences led to a specific design question: how might an interactive investigation treat interpretation itself as a playable activity? Detective games commonly ask players to search environments, collect evidence, question characters, and reconstruct events. Dream sequences, meanwhile, are frequently used to communicate psychological states, memories, or surreal narrative information. The project explores what happens when these two forms of interaction are brought into the same investigative structure: factual and indexical evidence in the waking world, alongside symbolic and affective material in a dream space.

  

#### Core Innovation

The central design proposition of this project is that player agency in detective games can be located in the construction, testing, and revision of interpretations rather than primarily in the selection of branching narrative outcomes.

The project therefore treats evidence not only as information to be collected or as keys to predetermined progression, but as material through which the player can express and test an interpretation of the case. A piece of evidence may be examined, compared with another item, presented to a character, used to request additional information, or incorporated into a developing theory. Its significance is consequently not determined only when it is acquired, but also through the relationships the player establishes between different pieces of information.

This proposition is operationalised through several interconnected systems. The Multi-Item Clue System allows evidence to fulfil different narrative and mechanical functions. The Two-Slot Epistemic Interaction System requires the player to select one or two pieces of evidence before certain investigative interactions, making the relationship between evidence an actionable part of the investigation. The Patience System introduces social consequences for unsupported or repetitive interrogation, while the Window of Opportunity, or kairos, mechanic makes timing and prioritisation part of investigative decision-making. The optional Dream–Awake sequence extends this structure by introducing symbolic and affective material that can prompt the player to reconsider the meaning of waking evidence.

The project does not attempt to simulate unrestricted human reasoning or to eliminate authorial control over the investigation. Instead, it proposes a bounded interaction model in which the player must make evidential relationships meaningful through their own decisions while remaining within an authored narrative and evidence corpus.

  

#### Addressing the "Static Detective" Problem

The design problem addressed by this project is what can be described as the static detective problem. In this model, the player may perform the actions associated with investigation, while much of the interpretive work required to transform that information into knowledge is performed by the game itself.

This can occur when clues have predetermined meanings, when the protagonist automatically explains their significance, when progression depends primarily on selecting an expected dialogue option, or when the game's structure implicitly identifies the correct interpretation before the player has constructed one. Under these conditions, the player can participate in investigation without necessarily being responsible for building and testing a theory of their own.

The proposed system therefore seeks to shift investigative agency towards interpretation. The player must decide which information is relevant, which pieces of evidence can be meaningfully related, what questions those relationships support, when additional information is worth pursuing, and when a theory is sufficiently supported to justify a final accusation. Agency is consequently distributed across a sequence of investigative decisions rather than concentrated in explicit narrative branches.

This does not mean that every interpretation is equally valid or that the player can produce any possible theory. The case remains deliberately authored, and the digital prototype relies on structured evidential relations and authored dialogue responses. The design objective is instead to create a bounded space in which the player is required to perform meaningful epistemic work within those constraints.

The project therefore investigates whether detective gameplay can shift from a model in which the player primarily discovers and follows an authored solution towards one in which the player actively constructs, tests, revises, and commits to an interpretation of incomplete evidence.

## 4.2 Core Design Systems

The following systems were designed as interconnected attempts to operationalize epistemic agency within a bounded interactive detective narrative. Rather than locating player agency only in branching dialogue choices or final outcomes, the proposal distributes it across the processes of discovering, selecting, combining, presenting, delaying, and reinterpreting information.

The intention is not to simulate unrestricted human reasoning or to create an infinite number of possible narrative paths. Instead, the prototype explores whether a player can be encouraged to experience investigation as an active process of interpretation. The player is asked to consider what a clue means, how it relates to other information, when it should be used, who it should be presented to, and whether a current interpretation is sufficiently supported. In this way, the systems attempt to shift the player from the role of someone who merely retrieves information into the role of someone who constructs provisional knowledge.

### 4.2.1 Multi-Item Clue System

The Multi-Item Clue System proposes that evidence should not function only as an inventory object or as a single-use key that unlocks the next predetermined event. Instead, a clue is treated as an epistemic object: something that can be collected, read, inspected, organised, compared, presented in dialogue, or used to access further information depending on the context of the investigation.

A clue can therefore occupy multiple roles at the same time. It may be a physical trace found in the environment, a document containing factual information, a possible contradiction of a character’s testimony, a component of a theory, or a social lever that changes the direction of an interrogation. Its meaning is not fixed when it is acquired. It becomes meaningful through the relations the player constructs around it.

Evidence in this system is designed to serve multiple simultaneous functions, collapsing the traditional separation between inventory mechanics and narrative mechanics:

- Physical inventory item (carried, manipulated, used as a tool)
    
- Dialogue evidence (presented to NPCs to elicit responses)
    
- Conceptual clue (contributes to case-building and theory construction)
    
- Social lever (influences NPC behavior, unlocks doors, creates opportunities) Objects can also function in conversations.
    

This approach is informed by indexical storytelling, where evidence functions as a trace that points towards an absent event rather than revealing its meaning automatically (Fernández-Vara, 2011). A clue such as a report, object, image, or testimony does not simply tell the player what happened. It invites the player to ask what it implies, what other traces it relates to, and which interpretation it supports. The system therefore attempts to make the process of moving from trace to hypothesis part of the gameplay itself.

### 4.2.2 Two-Slot Epistemic Interaction System

The Two-Slot Epistemic Interaction System provides the main interaction structure through which the player can express an investigative interpretation. Before questioning a character, confronting them, or interacting with particular investigative systems, the player can equip one or two pieces of evidence. This act of selection communicates what the player considers relevant at that moment.

The two slots are not intended only as an inventory-management feature. They form a small and accessible language of evidential relation. One item can communicate a direct inquiry about a clue, while two items can communicate a comparison, contradiction, association, suspicion, or possible causal relationship. For example, the player may present a testimony alongside a forensic report in order to question whether the two accounts can coexist.

This system is influenced by the Logic mechanic discussed in Ace Attorney Investigations: Miles Edgeworth, where the player is asked to connect pieces of information rather than allowing the protagonist to make every deduction automatically. However, the two-slot system does not attempt to formalise all possible forms of deduction. It provides a constrained interface through which players can make a current interpretation actionable. The player still operates within authored evidence relations and narrative possibilities, but must participate in selecting the grounds from which an interaction can occur.

The system is also connected to Aarseth’s concept of ergodic effort. The player does not only read or receive the investigation; they must perform work by retrieving evidence, reviewing it, selecting it, and testing its relevance in a particular situation. This is intended to make investigation feel less like progressing through a checklist and more like constructing and revising a working theory.

### 4.2.3 Patience System

The Patience System introduces social consequence into the investigative process. In many detective games, characters can be treated as information dispensers: the player can repeatedly ask every available question, test every dialogue option, and eventually exhaust the conversation without meaningful cost. This proposal instead treats access to information as dependent not only on the investigative effort, and theory building, but also on the character’s willingness to engage, based on their narrative constraints. 

Each major character has a limited patience value that can be reduced when the player repeatedly presents irrelevant evidence, pressures the character without sufficient support, or continues an unproductive line of questioning. As patience decreases, the player’s conversational position becomes weaker. The character may stop cooperating temporarily, or the player may need to wait before returning to the interaction.

The purpose of this system is not simply to punish failure. It is to make unsuccessful or premature investigative actions meaningful. A weak confrontation can reveal that the player’s theory is not yet sufficiently grounded, that the evidence has been misread, or that another route must be pursued before the character can be approached again.

This system relates to the discussion of Disco Elysium, particularly its use of constraints, failure, and social reactivity to create meaningful agency. The player is not given unlimited freedom, but their actions alter the dramatic conditions of the interaction. In this prototype, patience makes dialogue a social negotiation rather than a neutral menu of information, where failure is intended to motivate the player to investigate further and solidify their theory.

  

### 4.2.4 Window of Opportunity: A Kairos Mechanic

The Window of Opportunity mechanic introduces time as an investigative and interpretive condition. The prototype contains a finite investigation period, but the function of time is not only to create a countdown or pressure the player to think of the consequences of their actions. Time is also connected to the idea of kairos: the appropriate, consequential, or strategically meaningful moment for action.

The player may possess a clue without yet being ready to use it effectively. A character may not be available, a line of reasoning may still lack support, an evidence request may still be processing, or a previous interaction may have exhausted a character’s patience. The relevant question is therefore not only “What evidence do I have?” but also “Is this the right moment to act on it?”

The player must decide whether to continue exploring, wait for information to become available, recover a damaged conversational interaction, or proceed with an incomplete but potentially urgent theory. This transforms time from a purely external limitation into part of the player’s reasoning process.

The mechanic connects to the State of the Art discussion of conceptual and informational gating. As in games where progression depends on knowledge rather than only on physical access, the player’s obstacle is not always a locked door or missing object. It may be a lack of readiness, sufficient context, social opportunity, or confidence in an interpretation. The prototype therefore combines chronological time with epistemic timing: not just how much time remains, but what can meaningfully be done with the time that remains.

  

### 4.2.5 Dream Sequence Mechanic

The Dream Sequence Mechanic introduces an alternative mode of investigation based on symbolic and affective interpretation. While the waking investigation is primarily concerned with physical traces, testimonies, documents, access, and contradiction, the dream sequence creates a different kind of epistemic space. It allows the player to engage with images, atmosphere, memory and symbolic relations that cannot be approached in the same way through factual evidence alone.

The dream should not be understood as a passive cutscene or simply as an atmospheric interruption. It is proposed as a navigable and interpretable environment. The player is still required to explore, notice, associate, and form a possible understanding of what is being represented. However, the object of investigation shifts from the direct reconstruction of external events towards the interpretation of symbolic mysterious messages.

This approach develops the discussion of dreamscapes in the State of the Art, particularly the idea that surreal environments can function as symbolic texts. As in Yume Nikki, Alan Wake, or the dream sequences of Max Payne, the player is not necessarily presented with literal answers. Instead, they are invited to recognise patterns, motifs, spatial distortions, and emotional associations that complicate the meaning of the waking narrative.

  

## 4.5 Expected Contributions

This design proposal (consisting of ideas that require testing) aims to contribute to the field of interactive narrative design by :

1. Operationalizing Epistemic Agency: Demonstrating how detective mechanics can distribute agency through interpretation.

2. Integrating Symbolic and Indexical Storytelling: Testing whether dream-based symbolic investigation can function as a mechanical system rather than atmospheric flavor.

3. Social Systems as Investigative Tools: Exploring whether NPC patience can create emergent narrative complexity without exponential authorial burden.

4. Challenging the Static Detective Problem: Offering an alternative to automated deduction and quest-marker-driven investigation by requiring active cognitive synthesis from the player.

5. Atmosphere as Epistemic Infrastructure: Demonstrating that audiovisual design functions not as decoration but as a core investigative system that shapes player understanding and enables meaningful exploration.

By treating mystery not as narrative content but as the structural foundation of agency, and by recognizing that atmosphere is epistemic infrastructure, this project seeks to advance understanding of how sensory immersion, cognitive labor, and emotional resonance can combine to produce meaningful, intellectually engaging interactive experiences.

