
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