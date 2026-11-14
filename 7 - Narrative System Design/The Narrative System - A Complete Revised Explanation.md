# The Narrative System: A Complete Revised Explanation

## Overview: Three Layers, One Persistent State

The dialogue architecture is not a single conversation tree. It comprises three distinct layers that share a persistent narrative state manager: **Logic Chains**, **standalone evidence interactions**, and **scripted narrative sequences**. Each layer serves a different function, and the player's investigative agency operates across all three.

**Logic Chains** are authored sequences representing lines of investigative reasoning. Each chain belongs to a character (unless deliberately configured otherwise) and contains an entry node and an ordered collection of dialogue nodes. These nodes hold the questions, responses, evidence requirements, and optional narrative events through which the line of inquiry becomes playable. A chain can require particular narrative flags or previously visited dialogue nodes before it becomes available. Consequently, possessing an item of evidence does not necessarily make every related question immediately accessible: the player may also need to establish an earlier premise or bring the investigation into the appropriate narrative state.

**Standalone evidence interactions** provide questions and responses without advancing a chain. They may be restricted by character, mode, evidence, or narrative flags; their questions can be hidden while a chain is active, require an additional flag, or disappear after their initial and optional variation responses have been used. Some also initiate delayed evidence processing, creating evidence that remains pending until the configured time has elapsed. These exchanges support practical investigative actions alongside argumentative progression, allowing dialogue to participate in evidence production as well as evidence interpretation.

**Scripted narrative sequences** present authored pages, potentially involving several speakers, and may include explicit choices with their own response pages. They hide the evidence slots and disable ordinary closing and mode switching while they play. Pages, choices, and sequence completion can set flags or fire events. Flag-based narrative rules can select these sequences according to narrative conditions and character strength, with priority determining which eligible sequence takes precedence. Not every spoken exchange is a Logic Chain, and not every dialogue choice is derived from equipped evidence.

The most important correction to any account of this system concerns **emergence**. The system combines persistent state across different lines of inquiry, but its responses, thresholds, and narrative interventions remain authored. It is therefore more accurate to describe a **cumulative, state-dependent character arc** than an arc that is "not authored." The player's route through the available evidence determines which authored contributions accumulate and when the relevant conditions are met; the system does not independently generate a psychological arc or infer one from the semantic content of the player's reasoning.

---

## Local Resolution: How a Question Becomes Available

The dialogue system determines which locally authored questions and responses become available within a given progression. In the implementation, this local resolution depends on more than the currently equipped evidence. It also considers the character being addressed, whether the player is conducting an Inquiry or a Confrontation, the character's recorded dialogue history, the active Logic Chain, and the narrative conditions that enable or suppress particular interactions. The relationship between global progression and local dialogue is therefore mediated by persistent state and events, rather than by a single, self-contained conversation tree.

When the player approaches a character, the evaluator requests nodes and interactions of the selected type. Inquiry presents questioning; Confrontation presents accusatory pressure. These modes do not merely change the presentation of an otherwise identical menu — the evaluator filters the available nodes by `nodeType`, so an Inquiry node and a Confrontation node with the same chain ID are distinct objects with distinct evidence requirements, distinct question text, and distinct response lines.

The evaluation pipeline considers, in order: the character being addressed; the mode; the equipped evidence (up to two slots); the character's recorded dialogue history (visited nodes, bookmarks, active chain); the active Logic Chain (if one is active, other chains for that character are normally suppressed); narrative flags (`requiredFlags` on nodes and chains, plus suppression rules); and standalone interaction overlap (chain questions take precedence over standalone interactions that overlap with evidence already covered by those questions).

The player can change equipped evidence or switch modes during an ordinary conversation, prompting the system to recalculate the available questions. Dialogue availability is therefore continuously reconstructed from the player's current evidential proposal and the investigation's accumulated state, rather than fixed when the conversation begins.

---

## Logic Chains: Structure and Progression

A Logic Chain is best understood as an authored sequence representing a line of investigative reasoning. Each chain belongs to a character, unless deliberately configured otherwise, and contains an entry node and an ordered collection of dialogue nodes. The chain is therefore not identical to a conversation session. Its progress can persist after the player stops speaking to the character and returns later.

Nodes are ordered, and each node declares its position within the chain (`chainNodeOrder`). The entry node is marked as such; subsequent nodes become available as the chain advances. A node can require particular narrative flags (`requiredFlags`) or previously visited dialogue nodes before it becomes available. Some nodes also declare `requiredEvidenceIDs` — the evidence that must be present in the player's slots for the node's primary question to become available. Others leave `requiredEvidenceIDs` empty and rely entirely on `logicRangeEvidenceIDs`, which defines the space of acceptable evidential proposals rather than a hard requirement.

**Progression is recorded at the node level**, rather than requiring the player to exhaust every question held by a node. An advancing answer establishes that the node has occurred; it is not necessary to ask all of its alternative formulations before moving forward. Questions can also be marked as **non-advancing**. These produce their authored responses and can trigger narrative events, but they do not enter the chain, mark its node as visited, create a bookmark, or contribute investigative strength. This distinguishes pursuing a line of reasoning from making a supplementary remark within its context.

Once the player answers an advancing chain question, the system enters that chain if necessary and records the node as visited. Subsequent evaluation uses the chain's ordered nodes and the character's history to determine the next relevant stage. During an active chain, other chains for that character do not normally surface as competing lines of inquiry.

---

## The Two-Slot Evidence System: Semantic Keys and Matching Rules

Evidence functions as a **semantic key** in a precise operational sense: an evidence identifier participates in rules that determine which authored questions can appear. A node's primary question uses the node's `requiredEvidenceIDs`, while additional questions within the same node use their own `triggerEvidenceIDs` and must satisfy the node's `logicRangeEvidenceIDs` conditions.

Some questions accept any one item from a list. Others require a combination. In the current two-slot implementation, a combination is expressed as an **anchor item together with any one permitted partner**. A list containing an anchor and several possible partners therefore defines several acceptable pairings, not a requirement to equip every listed item simultaneously. Selecting two pieces of evidence proposes a relation that the system can recognise, but the relation's wording and consequences remain authored.

Consider Elara's barefoot entry node (`ELARA_ADC4A6E2`, `CHAIN_ELARA_BAREFOOT`, node 1/2, Inquiry). Its `logicRangeEvidenceIDs` includes E4-C, E8R, E4R, E18R, E18, IR, ARE, and E4-TRACE. Within that node, distinct question variants are configured for distinct `triggerEvidenceIDs` subsets:

| Trigger evidence | Question formulation |
|---|---|
| E8R, E4R, E4-C, E4-TRACE | "Elara, when the officers found you, you were barefoot and your feet were cut up. Our witness describes the person standing over the body as barefoot. Can you explain that?" |
| E18R, E4R, E4-C, E4-TRACE | "…The night of the incident, the weather was cold and rainy. Do you remember going outside that night?" |
| E18, E4R, E4-C, ARE, E4-TRACE | "[Show {evidence}] … Do you remember going outside that night?" |
| IR, E4R, E4-C, E4-TRACE | "…Do you remember going outside that night?" |
| IR, ARE | "Elara, when the officers found you, were you barefoot?" (no slip event) |

The same node produces different question formulations depending on which evidence is equipped. Possessing E4R alone is not enough to access the node; the player needs at least one item from the range, and the specific item determines which formulation appears. The node's `requiredEvidenceIDs` is empty, but the node is not unconditionally available — its `logicRangeEvidenceIDs` defines the envelope of acceptable proposals.

**Combination requirements** are equally explicit. Kae's gun-bullet chain entry node (`61F3B69D`) requires **E1R + E1** — the forensic report and the physical gun together. Elara's financial chain entry (`ELARA_69B43226`) requires **ARK + E23R** — Kae's arrest report and Elara's employment verification. Kae's August incident node 2/3 (`9D1697C7`) requires **E9R + E11R** — Arthur's complaint and Kae's criminal record. Neither item alone opens the node; the pairing is the proposal.

**One-from-a-list requirements** appear frequently. Elara's barefoot node 2/2 (`8CF04777`, Confrontation) requires **E4R, E4-C, E4-TRACE** — the player needs at least one of these three, not all three. The list defines acceptable alternatives, not a simultaneous requirement.

A node could be configured so that a weapon alone makes a general question available, while the weapon combined with a witness statement makes a more specific challenge available. The important distinction is between acquiring evidence and deciding how to mobilise it. Acquisition adds an item to the player's investigative resources; equipping it for a particular character, in a particular mode, tests one of its possible conversational applications. The same item can therefore support different questions across different contexts without the system assigning it one universal conversational meaning. E15 (Moon vials) appears in `CHAIN_ELARA_DREAM`, `CHAIN_ELARA_MOON_DRUG`, and `CHAIN_KAE_MOON` — each time in a different conversational role. E1R (gun report) appears in `CHAIN_ELARA_GUN`, `CHAIN_ELARA_GUN_CONFRONTATION`, `CHAIN_KAE_GUN`, and `CHAIN_KAE_GUN_BULLET` — different chains, different characters, different modes.

---

## Menu Selectivity: Precedence and Suppression

The available menu is selective rather than a simple list of every matching question. The evaluator gives **chain questions precedence over standalone interactions** that overlap with evidence already covered by those questions. Within a node, a **more specific combination question can suppress a question supported by a smaller subset** of the same evidence. A comparable rule applies between standalone interactions. The remaining options are ordered so that resumption and combination-based chain questions appear ahead of less specific options, while weak questions appear last. These rules make the menu sensitive to the specificity of the player's proposal and reduce competing formulations of the same evidential material. They do not guarantee that every question supported by either equipped item will remain visible.

---

## Progression, Interruption, and Resumption

Interruption does not ordinarily erase investigative work. Closing a normal conversation clears the character's active-chain status, but preserves the dialogue records and chain bookmarks. A **bookmark** stores the last advancing question, its node, its displayed text, and its relevant evidence.

When the player returns with **no evidence equipped** and no chain active, an eligible unfinished chain can offer a resumption option. Selecting it restores the bookmarked evidence to the slots where possible and replays the bookmarked question, allowing the player to re-enter the line of inquiry through an explicit conversational reminder. Resumption remains conditional: suspended or narratively suppressed chains do not offer these options, and the system checks whether the chain has already reached its recorded final node. A chain is therefore persistent, but not unconditionally available.

This is why late-chain confrontations that fire the same slip event can be bookmarked and resumed independently. Kae's `CHAIN_KAE_ELARA_BAREFOOT_FALSE_ALIBI` node `0124D534` and `CHAIN_KAE_ELARA_BAREFOOT_HOODIE` node `7512B53D` both fire `ELARA_BAREFOOT_2`, but they belong to different chains and are bookmarked separately. The player can pause one line, pursue another, and return to the first through the explicit resumption option.

---

## Patience: The Cost of Unsupported Proposals

The system also represents unsuccessful evidential proposals. If an active node has no valid question for the equipped evidence and has an authored weak-question fallback, the system can surface that fallback instead. Some chains explicitly permit this behaviour at their entry point as well. Selecting a weak question does not advance the investigation. It reduces the character's patience and produces a diminished response, with a second response available for repeated failure. Two consecutive out-of-range attempts break an active chain, while a recorded in-chain answer resets the consecutive-failure count.

Patience is maintained **separately from chain progress**, so breaking a line of questioning does not restore the character's willingness to engage. Crossing configured low-patience or depleted-patience thresholds can also set narrative flags and notify other systems. The consequence of an unsupported proposal is therefore not simply the absence of progress; it can alter the conditions of subsequent interaction.

The weak-question structure is visible in the data. Elara's barefoot node 2/2 (`8CF04777`) has a weak question template and two diminished response sets, with `[EXIT]` on the second. Kae's `CHAIN_KAE_ELARA_BAREFOOT_HOODIE` node `7512B53D`'s weak question has a second response that explicitly says the chain's purpose is "fully realized" — the player has cornered Kae toward confession even though the chain's momentum is lost for this pass. The weak question is not a dead end; it is a state transition with narrative consequences.

**Note on data gaps:** Several nodes in the current data have empty `weakQuestionTemplate` and empty `diminishedResponseLines` fields (e.g., `ELARA_ADC4A6E2`, `ELARA_F556FDDA`, `KAE_B95A6508`, `KAE_1947E6A7`, `KAE_2C0E2D78`, `KAE_B0F02CAE`, `KAE_022CDFE1`, `KAE_2586377A`, `KAE_86EF110A`, `KAE_3463A08F`). In those nodes, an unsupported proposal has no authored fallback — the system may have nothing to show, which can break the patience/weak-question loop. These are content gaps, not architectural problems, but they affect playability.

---

## Strength: Cumulative Argumentative Pressure

A further character-level variable makes investigative pressure **cumulative across chains**. The implementation calls this value `strength`, but it represents accumulated argumentative pressure against the character rather than the character's personal resilience. Each advancing question can contribute an authored amount, counted only once for that node-and-question pair. By default, Confrontation nodes contribute one point and Inquiry nodes contribute none, although individual nodes can override these defaults. Weak questions and non-advancing questions contribute nothing. Repeating the same advancing question therefore cannot repeatedly increase pressure.

Because the value belongs to the character's knowledge log rather than to an individual chain, **different lines of inquiry can contribute to a shared threshold**. Narrative rules can then use that threshold, together with flag conditions, to make a later sequence eligible. This is the mechanism behind the CONFESSION rule:

```
ruleLabel: "KAE_PRESSURED_EVENT"
priority: 0
fireOnce: true
strengthCharacterID: "KAE"
strengthThreshold: 27
usesStrength: true
conditions: [FLAG_KAE_PRESSURED mustBeSet=true]
sequence: NarrativeDialogue_CONFESSION
```

The rule requires **two keys simultaneously**: Kae's strength must reach 27, and `FLAG_KAE_PRESSURED` must be set. The flag is presumably set by one of the `KAE_PRESSURED` slip events that fire from specific late-chain confrontations (`CHAIN_KAE_ELARA_SLEEPWALKING` node `F5C18ACE`, `CHAIN_KAE_KILLER_ARTHUR_PRIOR_TARGET` node `4A6B024B`, `CHAIN_KAE_KILLER_CRIMINAL` node `5D5BE304`, `CHAIN_KAE_KILLER_HOODIE` node `32898282`, and the two-shapes variants). Reaching strength 27 requires the player to pursue a substantial portion of Kae's confrontational chains — across multiple lines of inquiry, not just one. The threshold is a **global gate**, not a local one.

This provides a more concrete account of character development than describing it as an unauthored breakdown. The character's responses and threshold-triggered sequences are authored, but the player's route through the available evidence determines which contributions accumulate and when the relevant conditions are met. A later reaction can acknowledge pressure established across several earlier exchanges without requiring all of those exchanges to belong to one conversation or one chain. The architecture supports a cumulative character arc whose timing depends on investigative activity; it does not independently generate a psychological arc or infer one from the semantic content of the player's reasoning.

---

## Flags and Slip Events: Connecting Local Exchanges to the Wider Investigation

**Flags** represent conditions that can remain active, be queried, and, where appropriate, be cleared. They can enable a chain, condition a question, or activate a suppression rule that removes chains and standalone interactions from consideration.

Flag-enabled chains are visible throughout the data. `CHAIN_ELARA_DREAM` requires `FLAG_ELARA_MOON_ADDICTION`; `CHAIN_ELARA_FORENSIC_TRACE` requires `FLAG_ELARA_BAREFOOT_1` and `FLAG_E4-TRACE_ACQUIRED`; `CHAIN_KAE_CONFESSION_2` requires `FLAG_KAE_CONFESSION`; `CHAIN_KAE_ELARA_MEDICATION` requires `FLAG_ELARA_NOT_USING_MEDICATION`; `CHAIN_ELARA_TWO_SHAPES_FALSE_ALIBI` and `CHAIN_ELARA_TWO_SHAPES_HOODIE` both require `FLAG_TWO_SHAPES_THEORY` plus a second flag. The flag system is the connective tissue between chains: a slip event fires in one chain, a listener sets a flag, and a different chain (possibly for a different character) becomes available.

Flag-conditioned questions are embedded directly in question text. `CHAIN_ELARA_FINANCIAL` node `254BFEB8` has variants prefixed with `{FLAG_ELARA_MOON_ADDICTION}` and `{FLAG_KAE_MOON_ADDICTION}`. `CHAIN_ELARA_GUN` node `B74A0512` has variants prefixed with `{FLAG_FINANCIAL_ISSUES}`, `{FLAG_ARTHUR_PRIOR_TARGET}`, and `{FLAG_HOODIE_OWNERSHIP}`. The flag is evaluated at menu-construction time; if the flag is not set, the variant does not appear.

**Slip events** are registered event identifiers that notify the narrative system when a configured occurrence takes place. Although a slip event can represent an involuntary revelation in the fiction, its technical role is broader: the same event mechanism is also called from narrative pages, choices, object interactions, and evidence-processing completion. It is therefore more accurate to treat a slip as an authored narrative occurrence with possible systemic consequences, rather than assume that every event is automatically produced by accumulated pressure.

Tracing a flag through the system: `CHAIN_ELARA_MOON_DRUG` node `DA4611C9` fires `ELARA_MOON_ADDICTION`. A listener presumably sets `FLAG_ELARA_MOON_ADDICTION`. `CHAIN_ELARA_DREAM` entry node `ELARA_14C55225` then becomes available, requiring that flag plus E15. `CHAIN_ELARA_FINANCIAL` node `254BFEB8` gains a drug-specific question variant. `CHAIN_KAE_ELARA_MEDICATION` entry `F3F47563` requires a different flag (`FLAG_ELARA_NOT_USING_MEDICATION`), set by `CHAIN_ELARA_MEDICATION_WITHDRAWAL` slip events. The flags persist across conversations, across characters, and across the three dialogue layers.

---

## Scripted Narrative Sequences: The CONFESSION Example

Scripted narrative sequences form a distinct layer from Logic Chains. They present authored pages, potentially involving several speakers, and may include explicit choices with their own response pages. They hide the evidence slots and disable ordinary closing and mode switching while they play. Pages, choices, and sequence completion can set flags or fire events.

The CONFESSION sequence (`NarrativeDialogue_CONFESSION`, `sequenceID: "KAE_PRESSURED_EVENT"`) is the clearest example in the data:

- `isRepeatable: false`
- `pageCount: 8`
- Single speaker (KAE) across all 8 pages
- No choices
- `[OnComplete]` fires `KAE_CONFESSION` slip event

The pages are fixed authored content: Kae taking a deep breath, confessing to the shooting, constructing a narrative that explains the forensics while claiming total responsibility, and asking the detective to leave Elara out of it. The sequence is triggered by the `FlagNarrativeRule_CONFESSION` rule, which requires strength 27 plus `FLAG_KAE_PRESSURED`. The player's investigative activity determines *whether and when* the sequence fires; the sequence's content is entirely authored.

The sequence's completion fires `KAE_CONFESSION`, which presumably sets `FLAG_KAE_CONFESSION`. `CHAIN_KAE_CONFESSION_2` entry node `41DB04B8` then becomes available, requiring that flag plus E8R, ARK, and E21R. This is a **post-confession confrontation** — Kae defending his confession against further evidence. The scripted sequence opens a new Logic Chain; the layers are not isolated.

---

## A Worked Walkthrough

To show how the layers interact in practice:

**Step 1 — Early investigation (Elara).** The player has E1R (gun report), E4R (barefoot medical record), and E8R (witness statement). They approach Elara in **Inquiry** with E4R + E8R equipped. `CHAIN_ELARA_BAREFOOT` entry node `ELARA_ADC4A6E2` evaluates: both items are in `logicRangeEvidenceIDs`, and the variant with `triggerEvidenceIDs: E8R, E4R, E4-C, E4-TRACE` matches. The question appears: *"Elara, when the officers found you, you were barefoot and your feet were cut up. Our witness describes the person standing over the body as barefoot. Can you explain that?"* Elara responds with the base response lines. The node is marked visited. The chain advances to node 2/2. `ELARA_BAREFOOT_1` slip event fires.

**Step 2 — Following up (Elara, Confrontation).** The player switches to **Confrontation** with E4R + E4-C + E4-TRACE (or any subset satisfying the required list). Node `8CF04777` evaluates: `requiredEvidenceIDs: E4R, E4-C, E4-TRACE` — at least one is present. The question appears: *"[Shows {evidence}] 'Really look at the evidence this time. You need to stop telling me you don't remember and start telling me the truth.'"* The response advances the chain. If the player has the wrong evidence, the weak question fires, patience drops, and a second failure exits the conversation.

**Step 3 — Cross-character pressure (Kae).** The player has accumulated `FLAG_ELARA_BAREFOOT_1` and `FLAG_E4-TRACE_ACQUIRED` from Elara's chains. They approach Kae in **Confrontation** with E4-TRACE equipped. `CHAIN_KAE_E4_TRACE` entry `EF57C79B` requires `FLAG_E4-TRACE_ACQUIRED` + `FLAG_ELARA_BAREFOOT_1` + E4-TRACE. All conditions met. The question appears: *"{FLAG_ELARA_BAREFOOT_1} 'Read the damn report! You blamed the apartment floor. Then how can you explain what was found in her injuries.'"* Kae's response shows visible strain. The node advances. Kae's strength increases by 1.

**Step 4 — Accumulating strength across chains.** The player pursues `CHAIN_KAE_GUN_BULLET`, `CHAIN_KAE_AUGUST_INCIDENT`, `CHAIN_KAE_FALSE_ALIBI`, `CHAIN_KAE_TWO_SHAPES_*`, and other lines. Each advancing Confrontation question adds 1 to Kae's strength. The player does not need to exhaust every question in a node — one advancing answer per node is enough. The player also triggers `KAE_PRESSURED` slip events through specific nodes (`F5C18ACE`, `4A6B024B`, etc.), which presumably set `FLAG_KAE_PRESSURED`.

**Step 5 — The confession.** Kae's strength reaches 27. `FLAG_KAE_PRESSURED` is set. `FlagNarrativeRule_CONFESSION` evaluates: strength threshold met, flag condition met, priority 0, fire once. `NarrativeDialogue_CONFESSION` plays: 8 authored pages. Evidence slots hidden. Mode switching disabled. On complete, `KAE_CONFESSION` slip event fires. `CHAIN_KAE_CONFESSION_2` entry `41DB04B8` becomes available if the player has E8R, ARK, and E21R equipped — the post-confession confrontation.

**What the player controlled:** which evidence to equip, which mode to use, which chains to pursue, when to switch characters, when to leave and return. **What the system authored:** every question, every response, the threshold (27), the flag condition, the confession pages. The player's agency operates within an authored space of recognisable relations.

---

## Implications for Epistemic Agency

The implications for epistemic agency follow from the distinction between authored content and state-dependent access.

**First**, the conversational significance of a clue is not exhausted by its acquisition. The player decides where to present it, whether to combine it with another item, and whether to use it in Inquiry or Confrontation. E4R means something different in Elara's barefoot inquiry than it does in Kae's trace-evidence confrontation; the same item, in different contexts, opens different authored questions.

**Second**, the system retains consequences across exchanges through visited nodes, bookmarks, patience, strength, and narrative state. Earlier questioning can therefore change the conditions under which later questioning occurs. A flag set in one chain enables a different chain for a different character. A strength threshold reached across multiple chains unlocks a scripted sequence. A bookmark preserves an unfinished line for resumption.

**Third**, the player's agency operates within an authored space of recognisable relations. The system does not evaluate arbitrary deductions or generate new interpretations; it recognises configured evidential proposals and makes their associated dialogue and consequences available. Its contribution is to make investigative activity consequential across a persistent structure, rather than to remove authorial control over what those consequences mean.

The character's responses and threshold-triggered sequences are authored, but the player's route through the available evidence determines which contributions accumulate and when the relevant conditions are met. A later reaction can acknowledge pressure established across several earlier exchanges without requiring all of those exchanges to belong to one conversation or one chain. The architecture supports a cumulative character arc whose timing depends on investigative activity; it does not independently generate a psychological arc or infer one from the semantic content of the player's reasoning.

---

## Implementation Notes: Known Gaps

The architecture supports the intended behaviour, but the current data has content gaps that affect playability:

- **Empty `baseResponseLines`:** Several question variants produce no response (`ELARA_ADC4A6E2` variant with E18/E4R/E4-C/ARE/E4-TRACE; `B74A0512` first two questions; `4824B6AA` second question; `E858D918` second question). These are likely data-entry gaps.
- **Empty weak-question templates:** Many nodes have no `weakQuestionTemplate` and no `diminishedResponseLines` (listed above). In those nodes, an unsupported proposal has no authored fallback.
- **Flag-dependent nodes with no valid questions:** `CHAIN_ELARA_GUN` node `B74A0512` relies entirely on flag-conditioned question variants; if none of the flags are set, the node has no valid questions. `CHAIN_KAE_TWO_SHAPES_HOODIE` node `E50E572C` similarly depends on `FLAG_BULLET_SHOT_FROM_GUN` and has empty `requiredEvidenceIDs`. The weak questions are present, so these are not hard blocks, but the nodes' intended purpose (cornering the character on the trigger-puller) depends on flags that may not be set by the time the player reaches them.

These are fixable content issues, not architectural problems. The system's behaviour is determined by the authored data; filling in the gaps will make the intended behaviour fully playable.