

Yes. And I think I understand much better now what you're trying to achieve.

You're not asking me to review the thesis again and produce a conventional list of recommendations. You're asking me to help build a **structured question bank that functions as the actual writing and completion plan for Chapters 4–8.**

The questions are your preferred way of developing the thesis. You answer them in your own words, often with more detail than would eventually appear in the chapter. Later, you use those answers to expand, correct, reorganise, or replace the existing prose.

That means the question bank needs to serve a slightly different purpose from a normal academic outline.

I have the two documents:

- Your merged draft of Chapters 4, 5, 6, 7, 8.1, 8.2 and 8.3.
    
- The _Thesis Question Bank — Chapters 4–8_ containing the questions Claude suggested, their status, and their references to existing material.
    

I will use the following hierarchy when evaluating them:

1. **Your notes and answers take precedence over existing prose.** If the two disagree, the question bank must identify the contradiction and direct the later rewrite.
    
2. **Existing answers should not be requested again.** The question should reference the precise section or question ID where the answer already exists.
    
3. **Partially answered questions should identify the missing information**, rather than asking you to explain the entire subject again.
    
4. **Chapter 9 questions should remain in Chapter 9** when they genuinely require player observations or playtesting data.
    
5. **New questions should be added only when they address a meaningful gap.** I don't want to create an enormous questionnaire just for the sake of completeness.
    
6. Each question should have a clear destination in the thesis, even if its answer eventually becomes a sentence, a paragraph, a table, or an appendix.
    

There is also an important distinction I'll maintain: a question can be important to answer without its entire answer belonging in the chapter where it originated. Sometimes the correct solution is to answer it once in another chapter and reference that answer.

# **1. Evaluation of Claude's question bank**

Strong foundation

I think Claude did a good job identifying concrete gaps. In particular, the question bank is much more useful than a generic chapter outline because it already contains cross-references, contradictions, and indications of where answers belong.

However, I wouldn't use it exactly as it stands. I'd make some structural changes.

### **What Claude got right**

- It identified questions that are genuinely important to the research argument, not just missing descriptive information.
    
- It recognised that Chapter 8 already contains answers that should be reused in Chapters 4–7.
    
- It identified several conflicts between the intended design, the written narrative, and the actual implementation.
    
- It separated author-dependent questions `(R)` from implementation-verification questions `(V)` and playtesting questions `(D)`.
    
- It recognised that ethics, methodology, AI disclosure, and some evaluation questions belong in other chapters.
    
- It maintained your existing Chapter 8 question numbering, which is important for preserving your notes.
    

### **What I would change**

There are five improvements I'd make.

**1. Distinguish an unanswered question from an unresolved decision.**

For example, 4.18 asks whether time is a countdown or a currency.

You probably already know how the system works. The issue is that the terminology and conceptual explanation haven't been settled.

That's not quite the same as not knowing the answer.

I'd introduce a `DECISION` status for questions where you need to choose how to frame something.

**2. Distinguish an implementation discrepancy from a design discrepancy.**

This is particularly important for Chapter 5.

Claude identifies the build as the winner in question 5.20. I would be more careful here.

Your notes take precedence over existing prose, as you've specified. But the build shouldn't automatically take precedence over the intended narrative.

There are three possible situations:

- The prose is outdated, and the build correctly implements your intended design.
    
- The build has evolved beyond the original narrative design, and the narrative should be rewritten to reflect the new intended design.
    
- The build contains an implementation error, and the implementation should eventually be corrected.
    

These must not be treated as interchangeable.

**3. Avoid duplicating questions across chapters.**

For example:

- 4.11 and 8.1 Q7 ask essentially the same thing.
    
- 4.20, 6.16 Theme 4, and Q96 concern the same dream-to-waking relationship.
    
- 4.18 and Q78 concern the same temporal model.
    
- 7.24 and Q43 concern the same implementation trade-offs.
    
- 7.19 and Q75 concern AI assistance.
    

These should have one canonical answer location, with references elsewhere.

**4. Separate the question's answer from the question's academic destination.**

A question might be answered in Chapter 8 but need a reference in Chapter 4.

For example, why the system uses a two-slot interaction model could be answered in your existing Chapter 8 Q7, but its conceptual significance belongs in Chapter 4.

You shouldn't write the explanation twice. You should write it once and make the connection explicit.

**5. Make the question bank more selective.**

Some questions are useful for documentation but aren't necessarily important to the thesis argument.

For instance, listing every keyboard shortcut is worthwhile for an appendix, but it shouldn't have the same priority as explaining how the Two-Slot system supports investigative reasoning.

I would keep those questions, but distinguish between:

- Research-critical questions.
    
- Chapter-completion questions.
    
- Technical documentation questions.
    

# **2. The structure I recommend for the final question bank**

I'd preserve your existing question IDs and introduce a few additional classifications.

|Classification|Meaning|
|---|---|
|`(R)`|Requires your reasoning, design rationale, or recollection.|
|`(V)`|Requires verification against the actual Unity implementation or source files.|
|`(D)`|Requires Chapter 9 playtesting or PlaytestLogger data.|
|`(L)`|Literature or theoretical reference needs to be established.|
|`(A)`|Appendix or technical documentation material.|

A question can have multiple tags, such as `(R/V)`.

For status, I'd use:

- `OPEN` — no answer established.
    
- `PARTIAL` — some information exists, but a specific gap remains.
    
- `ANSWERED → location` — already answered; link rather than repeat.
    
- `CONFLICT` — two sources disagree and need reconciliation.
    
- `DECISION` — the facts are known, but a design or writing decision remains.
    
- `PARKED → chapter` — belongs elsewhere.
    

I'd also add a priority classification:

- `P1` — must resolve before the chapter can be considered conceptually complete.
    
- `P2` — important for academic clarity or completeness.
    
- `P3` — supporting detail, appendix, or editorial refinement.
    

This gives you a much better way to work through the questions without feeling that every unresolved detail is equally urgent.

# **3. The consolidated chapter map**

Below is how I'd organise the existing questions, what I'd preserve, what I'd modify, and what I'd add.

The locations below refer to your existing question IDs and chapter sections. I use your current numbering rather than inventing replacements for existing questions.

## **Chapter 4 — Design Proposal**

P1 — conceptual foundation

This chapter should answer one fundamental question:

**What are you proposing, why are you proposing it, and how do the proposed mechanics operationalise that proposition?**

I would preserve almost all Claude's questions here.

|Question|Evaluation|Action|
|---|---|---|
|4.01 Research questions|Essential|Keep; link to Introduction and Chapter 9.|
|4.02 Static detective problem|Essential|Keep; clarify your contribution beyond Fernández-Vara.|
|4.03 Design influences|Useful|Keep, but only retain influences with identifiable contributions.|
|4.04 Game title|Editorial|Keep as P3.|
|4.05 Bounded interaction model|Essential|Keep; define exactly what is bounded.|
|4.06 Neo-Aristotelian frame|Important|Keep; coordinate with theoretical framework/SotA.|
|4.07 Five core systems|Essential|Keep; use canonical terminology.|
|4.08 Naming conventions|Important|Keep; settle once.|
|4.09 Multi-item evidence example|Useful|Keep.|
|4.10 Social levers|Already answered|Link to Chapter 8.1.2 and Q31.|
|4.11 Why two slots?|Essential|Merge with Chapter 8 Q7.|
|4.12 Difference from existing detective mechanics|Essential|Keep.|
|4.13 Aarseth reference|Important|Keep; verify the precise work and concept.|
|4.14 Patience conflict|Essential|Keep; use the Chapter 8 design description as the current authoritative account, subject to build verification.|
|4.15 Perception of conversational weakness|Important|Split design rationale from player perception in Chapter 9.|
|4.16 Disco Elysium comparison|Useful|Keep, but identify the specific mechanic.|
|4.17 Kairos reference|Essential|Keep.|
|4.18 Time as currency or countdown|Essential|Keep as one canonical question with Q78.|
|4.19 Conceptual/informational gating|Useful|Keep if the comparison supports your argument.|
|4.20 Dream-to-waking relationship|Essential|Keep; merge with 6.16 Theme 4 and Q96.|
|4.21 Dream influences|Useful|Keep.|
|4.22 Missing sections|Editorial|Keep as an editorial task, not a substantive question.|
|4.23 Expected contribution terminology|Important|Keep.|
|4.24 Authoring burden|Essential|Keep; revise the claim to match the actual implementation.|
|4.25 Atmosphere as epistemic infrastructure|Important|Keep, but consider narrowing the contribution.|
|4.26 Contribution evaluation|Essential|Move the actual evidence mapping to Chapter 9.|

### **New questions I'd add**

These are the ones I think are genuinely missing.

**4.27 (R) What is the precise relationship between epistemic agency, player freedom, and player choice in this project?**

You need to establish whether epistemic agency means having freedom to decide what happened, freedom to choose which evidence to use, or freedom to construct and test interpretations within an authored system.

These aren't identical.

Your system is bounded, so you need to explain how bounded interaction can still support meaningful agency.

**4.28 (R) What makes an evidence combination epistemically meaningful rather than merely mechanically valid?**

This is important.

The system can recognise that two items correspond to an authored question. But that doesn't automatically mean the combination represents a meaningful inference.

Explain the distinction between:

- A combination recognised by the system.
    
- A relationship that makes sense within the narrative.
    
- A conclusion that the player constructs from that relationship.
    

**4.29 (R) What happens when the player's interpretation is reasonable but not anticipated by the author?**

This is potentially one of the most important limitations of your design.

Does the system reject it? Does it provide a generic response? Can it still lead to an alternative interpretation?

You should explain the boundary between the player's interpretive freedom and the authored interaction corpus.

**4.30 (R) How do the five systems depend on one another?**

You explain the five systems individually, but I think you should also explain their interdependence.

For example, the Multi-Item Clue System provides the evidence, the Two-Slot system operationalises its use, the Patience System introduces social resistance, the Window of Opportunity introduces temporal constraints, and the Dream–Awake system introduces an alternative interpretive context.

This could be a short subsection or diagram rather than five additional pages of prose.

**4.31 (R/D) What would count as evidence that the central design proposition has not worked?**

I think this is an excellent question to answer before playtesting.

For example, if players simply brute-force evidence combinations, follow the most obvious dialogue prompts, and never revise their interpretations, would that undermine the proposition?

Establishing potential failure conditions will make your evaluation more credible.

## **Chapter 5 — Narrative Design: The Authored Case Model**

P1 — narrative consistency

The central question here should be:

**How does the authored narrative provide the conditions for investigation, interpretation, uncertainty, and institutional judgment?**

Claude's existing questions are generally very good.

I'd retain almost all of them, but reorganise them slightly.

|Question|Evaluation|Action|
|---|---|---|
|5.01 Laurel's six elements|Useful|Keep, but only explain elements used later.|
|5.02 Original disappearance concept|Useful|Keep.|
|5.03 Place-name consistency|Technical/editorial|Keep as verification.|
|5.04 Exact timeline|Essential|Keep as P1.|
|5.05 Meredith's observations|Essential|Keep as P1 conflict.|
|5.06 Gun discovery explanation|Important|Keep; distinguish first and second narrative layers.|
|5.07 August robbery|Important|Keep; establish the chronology and causality.|
|5.08 Rico's implementation|Technical|Keep as verification.|
|5.09 Second-layer evidence|Important|Keep; list actual in-build materials.|
|5.10 Communication of second layer|Essential|Keep; resolve with Q96 and 4.20.|
|5.11 Entity's motivation|Important|Keep.|
|5.12 Canonical character names|Essential|Keep; global terminology decision.|
|5.13 Buckley's role|Useful|Keep, with Chapter 8 reference.|
|5.14 Allergy and injector|Useful|Keep, with Q35 reference.|
|5.15 Red herrings|Essential|Keep; explain the actual misleading interpretations.|
|5.16 Kae's confession|Already answered|Link to Q12.|
|5.17 Elara's devastation|Verification|Keep.|
|5.18 Independence of narrative arcs|Essential|Keep; clarify the Pressured override.|
|5.19 Temporal pressure|Already answered|Link to 8.1.6.|
|5.20 Ending conditions|Essential|Keep, but separate intended narrative from implemented outcome.|
|5.21 Failure states|Important|Keep.|
|5.22 Emotional variants|Verification|Keep.|
|5.23 Ending catharsis|Important|Keep.|
|5.24 Chapter cross-references|Editorial|Keep as P3.|

### **New questions I'd add**

**5.25 (R) What does the player need to know to construct each of the possible interpretations, and what information remains inaccessible?**

This is important because you have multiple possible reconstructions, but not every player will necessarily encounter the same information.

You need to understand which information is:

- Mandatory.
    
- Optional.
    
- Discoverable only through certain interactions.
    
- Exclusive to the dream sequence.
    
- Available only through character disclosures.
    

This also helps distinguish narrative incompleteness from accidental information gaps.

**5.26 (R) What is the difference between the player's possible conclusions and the game's accepted conclusions?**

This is related to 4.05, but Chapter 5 needs the narrative application.

A player might believe something that is plausible but cannot be submitted through Miller's accusation structure.

Explain what happens to that interpretation.

**5.27 (R/V) Does each character possess a consistent knowledge boundary throughout the narrative and the actual implementation?**

For each character, establish:

- What they know.
    
- What they believe.
    
- What they conceal.
    
- What they misunderstand.
    
- What they can discover.
    
- What they can reveal.
    

This could be a knowledge matrix, which I think would be particularly valuable for Kae, Elara, Miller, Meredith, and the supernatural entity.

**5.28 (R) What makes the red herrings fair rather than arbitrary?**

You have deliberately misleading reports and competing explanations.

Explain whether the player can reasonably recognise contradictions or whether the red herrings are simply discarded once the correct evidence is found.

**5.29 (R) What does the game consider a successful investigation when the player doesn't uncover the complete authorial truth?**

This is important to your entire proposition.

A player who reaches a defensible institutional verdict without discovering the supernatural layer may still have completed the primary investigation.

Explain why that is an intentional narrative outcome.

**5.30 (V) Are all narrative branches described in Chapter 5 reachable in the current build, and which are theoretical, incomplete, or inaccessible?**

This is a useful addition because the current question bank already identifies inconsistencies between the authored case and implementation.

I'd make this a systematic verification task.

## **Chapter 6 — Early Design Rehearsals**

P1 — research credibility

The central question:

**What did the physical rehearsals reveal about the design, and how did those observations influence subsequent development?**

I think this chapter has a particularly important responsibility: it must demonstrate that the later digital systems were informed by actual design exploration, rather than simply being implemented according to an earlier plan.

I'd retain the original questions with the following adjustments.

|Question|Evaluation|Action|
|---|---|---|
|6.01 Terminology: rehearsal/workshop|Editorial|Keep; global terminology decision.|
|6.02 Consent and data handling|Essential|Park in Methodology, link here.|
|6.03 Character profiles/facilitator rules|Useful|Keep; decide appendix placement.|
|6.04 Language and translation|Important|Keep.|
|6.05 Patience threshold|Important|Keep; explain the facilitator's operational judgement.|
|6.06 Starter materials|Verification|Keep.|
|6.07 Evidence codes|Verification|Keep.|
|6.08 Buckley's participation|Useful|Keep.|
|6.09 Session dates and rule changes|Essential|Keep; resolve chronological conflict.|
|6.10 Session length|Useful|Keep.|
|6.11 Changes between sessions|Essential|Keep.|
|6.12 Thematic coding|Essential|Move methodology details to Chapter 3; retain analytical explanation here.|
|6.13 Kae's confession frequency|Important|Keep.|
|6.14 Success rate terminology|Important|Keep; use precise counts.|
|6.15 Revolver-intimidation removal|Useful|Link to Q29.|
|6.16 Workshop-to-build mapping|Essential|Keep; this is one of the most important questions in Chapter 6.|
|6.17 Four versus five objectives|Important|Merge with 7.01.|

### **New questions I'd add**

**6.18 (R) What was the original intention behind each physical rehearsal mechanic, and what did participants actually do instead?**

This would help distinguish between the intended activity and the emergent behaviour.

For example, participants might have used evidence cards in ways you hadn't anticipated, created their own organisational structures, or pursued interactions outside the intended scope.

These are valuable observations.

**6.19 (R) Which observations led to actual design changes, and which were deliberately not acted upon?**

This is important because not every participant request should become a feature.

You should explain how you decided which feedback represented a meaningful design problem and which requests were outside the project's intended scope.

This connects directly with 7.05 and 7.06.

**6.20 (R) Were there observations that contradicted your original design assumptions?**

I'd particularly like to see whether there were moments where participants behaved differently from what you expected.

Negative or contradictory findings are often more interesting than observations that merely confirm your initial ideas.

**6.21 (R) How did the physical facilitator's improvisation affect the apparent success of the systems?**

This deserves its own question, even though aspects of it are already discussed.

The facilitator could:

- Clarify ambiguous evidence.
    
- Rephrase questions.
    
- Provide contextual information.
    
- Interpret character reactions.
    
- Correct misunderstandings.
    

The digital system doesn't necessarily have those capabilities.

You should explain what this means when comparing the physical and digital prototypes.

**6.22 (R) What were the limitations of the participant sample and the research conditions?**

You already discuss some limitations, but I'd ensure that the chapter explicitly distinguishes:

- Number of participants.
    
- Number of sessions.
    
- Repeated participation.
    
- Group sizes.
    
- Session duration.
    
- Familiarity with detective games, if collected.
    
- Variations in the materials and protocol.
    

Don't invent demographic information if it wasn't collected.

**6.23 (R) How were the six thematic findings derived from the observations and questionnaires?**

This complements 6.12.

The important thing is to make the reasoning from raw observation to theme understandable, without turning Chapter 6 into a full qualitative-methodology chapter.

### **One particularly important recommendation**

I'd strengthen the relationship between 6.5 and 7.1.

The final section of Chapter 6 should ideally produce a set of design requirements.

For example:

|Rehearsal finding|Derived design requirement|
|---|---|
|Players lost track of available evidence.|Evidence must remain retrievable and organised.|
|Players struggled to understand failed combinations.|Interaction feedback must communicate evidentiary relevance.|
|Participants developed alternative interpretations.|The system should support multiple authored investigative possibilities.|
|Dialogue became difficult to manage.|Conversations need persistent state and progression logic.|
|Dream information felt detached.|Symbolic discoveries need an identifiable relationship with the waking investigation.|
|Players struggled with time and opportunities.|Temporal consequences need to be communicated clearly.|

These requirements can then become the starting point of Chapter 7.

That would give you a much more convincing transition.

## **Chapter 7 — System Design Architecture**

P1 — design formalisation

The central question:

**How were the narrative and interaction requirements formalised into an architecture capable of supporting the intended investigative experience?**

This chapter needs to explain the reasoning behind your architecture, not simply describe its structure.

|Question|Evaluation|Action|
|---|---|---|
|7.01 Five design objectives|Essential|Merge with 6.17; establish one canonical list.|
|7.02 First-person writing|Editorial|Keep as global style decision.|
|7.03 Development chronology|Important|Keep; link to Methodology.|
|7.04 Narrative inconsistencies|Useful|Keep; link to 6.11.|
|7.05 New documents answering requests|Essential|Keep.|
|7.06 Requests deliberately not satisfied|Important|Keep.|
|7.07 Bathroom and Locked Room|Already answered|Link to 8.3.1 and Q35.|
|7.08 Why Petri nets?|Essential|Expand; compare alternatives.|
|7.09 Architecture iterations|Important|Keep.|
|7.10 Formal analysis or notation|Essential|Keep.|
|7.11 Reference document|Documentation|Link to Q6.|
|7.12 36-hour clock|Already answered|Link to 8.1.6 and Q31.|
|7.13 Large flag tables|Editorial|Keep; decide appendix placement.|
|7.14 Miller's three questions|Essential|Keep; explain the design rationale.|
|7.15 Slideshow replaced by cell scene|Important|Keep.|
|7.16 Light Person dialogue|Important|Merge with Q96.|
|7.17 Drug consumption outside Bathroom|Already answered|Link to Q30.|
|7.18 Why not Ink/Yarn Spinner/etc.?|Essential|Keep; add actual tool comparison.|
|7.19 AI assistance|Essential|Park in Methodology, with technical details here where relevant.|
|7.20 Fernández-Vara reference|Important|Keep; verify the exact publication.|
|7.21 Logic Chain origins|Important|Keep.|
|7.22 Planning blockquotes|Editorial|Remove or integrate; link to 8.1.3.|
|7.23 Related evidence departure|Already answered|Link to 8.1.3.|
|7.24 Implemented trade-offs|Essential|Merge with Q43.|
|7.25 Isometric versus visual novel|Important|Keep, but avoid duplicated argumentation with Chapter 8.|
|7.26 Evidence-card design|Already answered|Link to Q50.|
|7.27 Dragging versus hotkeys|Already answered|Link to Q45.|
|7.28 Clock visibility|Already answered|Link to Q58.|
|7.29 Disco Elysium layout|Already answered|Link to Q46.|
|7.30 Web prototype tool|Useful|Keep.|
|7.31 Chapter summary|Editorial|Keep.|

### **New questions I'd add**

**7.32 (R) What were the functional requirements that the architecture needed to satisfy?**

This is something I think is missing.

You have design objectives, but what did the architecture actually need to support?

For example:

- Independent investigative progression.
    
- Shared narrative state.
    
- Conditional dialogue availability.
    
- Persistent suspect memory.
    
- Evidence acquisition.
    
- Temporal events.
    
- Narrative interruptions.
    
- Multiple endings.
    
- Optional exploration.
    

A concise requirements table would make the architecture much easier to understand.

**7.33 (R) How did you determine which systems needed to communicate with one another, and which needed to remain independent?**

This is important for explaining why you adopted shared flags, separate managers, and independent dialogue chains.

It would also help establish whether the architecture was designed to avoid excessive dependencies.

**7.34 (V) What happens when two or more narrative conditions become valid simultaneously?**

You describe priority-based rules, but I think you should explicitly explain conflict resolution.

For example:

- Can two scripted sequences trigger simultaneously?
    
- What determines which plays first?
    
- Can an event interrupt another?
    
- Are lower-priority events delayed, discarded, or evaluated again?
    

This is important to the architecture's reliability.

**7.35 (V) How are impossible or unreachable narrative states prevented or handled?**

This complements 7.10.

You don't need to conduct a formal mathematical analysis if you didn't do one.

But you should establish whether you inspected the architecture for unreachable transitions, contradictory flags, deadlocks, or progression states that could leave the player unable to continue.

**7.36 (R) What is the relationship between the architecture's formal representation and the actual authoring workflow?**

You explain the Petri-net representation and the Logic Chain model separately.

I'd like to know whether the Petri net was actually used to author the narrative or primarily to reason about its structure.

This is important because those are different contributions.

**7.37 (R/V) What limitations emerged when translating the architectural model into Unity?**

This is different from asking which mechanics were removed.

It concerns limitations of the architecture itself:

- Did the implementation become more complicated than expected?
    
- Were some dependencies difficult to maintain?
    
- Did certain states become difficult to debug?
    
- Were some systems more tightly coupled than originally intended?
    

This could be answered partly in Chapter 8.1.8.

## **Chapter 8 — Digital Prototyping**

P1 — implementation and evidence

This chapter has the largest question bank already, and I would preserve its existing structure.

However, I think it needs a little more organisation because the questions currently cover three different levels:

1. How the systems were implemented.
    
2. Why certain implementation decisions were made.
    
3. What remains unvalidated and needs to be investigated in Chapter 9.
    

I'd maintain Q1–Q66 and the new Q67–Q98. I wouldn't renumber them.

### **8.1 Architecture and implementation**

The existing questions are mostly well-targeted.

|Question|Evaluation|Action|
|---|---|---|
|Q1–Q6|Largely answered|Retain cross-references and fix any incomplete prose.|
|Q7–Q8|Essential|Resolve two-slot rationale and anchor/partner limitations.|
|Q9|Playtesting|Move to Chapter 9.|
|Q10–Q15|Existing implementation documentation|Retain; verify against the code.|
|Q16|Important|Keep authoring scale and brute-force question, separating them.|
|Q17|Important|Keep; establish iteration history.|
|Q18|Essential|Keep; link to 4.05 and the accusation system.|
|Q19–Q22|Mostly answered|Fix incomplete prose and link AI disclosure to Methodology.|
|Q23–Q26|Essential|Reconcile ending logic and correct prose.|
|Q27–Q31|Mostly answered|Verify implementation and document departures.|
|Q32–Q35|Evaluation/implementation|Separate factual system description from player experience.|
|Q36–Q42|Mostly answered|Retain and verify.|
|Q43|Essential|Merge with 7.24.|

I'd give particular attention to Q43 because it can serve as a synthesis of the architectural departures and technical limitations.

### **8.1.3 Logic Chains and social friction**

Q69–Q73 are useful and should remain.

I'd also add:

**Q99 (R/V) What is the difference between a Logic Chain being unavailable, being unavailable because of missing evidence, being suppressed, and being broken?**

This is important because the system has multiple reasons why a player might not receive a question.

Those conditions should be clearly distinguished.

**Q100 (V) What happens when the player returns to a chain after a cooldown or after advancing another narrative flag?**

You already describe suspect memory and bookmarks. This would establish exactly how the implementation preserves or resets conversational progression.

### **8.1.4 Data-driven content**

Q74 and Q75 are good.

I would add:

**Q101 (V) What is the exact fallback behaviour when an evidence combination has no authored response?**

This is essential for understanding the bounded interaction model.

What happens when the player attempts an unexpected combination?

Does the game:

- Return no question?
    
- Provide a weak question?
    
- Exit the conversation?
    
- Display a generic response?
    
- Reduce patience?
    

You already discuss parts of this in the Logic Chain explanation. The additional question is to ensure the actual implementation is accurately described.

### **8.1.5 Flags**

Q76 and Q77 are sufficient.

I wouldn't add more questions unless the code inspection reveals a specific inconsistency.

### **8.1.6 Time**

Q78–Q80 are important.

I'd add:

**Q102 (R/V) What are the exact rules governing time advancement, including passive progression, waiting, delayed evidence, cooldowns, and the dream sequence?**

This would establish one coherent temporal model.

**Q103 (V) Can any sequence of actions cause time to exceed the intended deadline, or trigger events after the investigation should have ended?**

This is a technical reliability question.

### **8.1.7 Sound**

Q81 is appropriate.

I'd add only one thing:

**Q104 (R) Which sounds communicate information about the game state, and which are purely atmospheric?**

This supports your Chapter 4 contribution about atmosphere, without assuming that all sound is epistemic.

### **8.1.8 Making it hold together**

Q82 and Q83 are both important.

Q83 is especially critical.

I would actually elevate it to a blocking question before you finalize the Chapter 9 evaluation methodology.

If the logger does not record attempted slot combinations, you cannot later claim to know how often players experimented with or brute-forced combinations based on that logger alone.

You might still recover some information from recordings, observations, or interviews, but you need to establish the evidence source explicitly.

### **New subsection: Final accusation**

I strongly agree with Claude that this deserves its own subsection.

Q84–Q89 are some of the most important questions in the entire bank.

I'd add one more:

**Q105 (R/V) Can the player submit an accusation that is narratively plausible but not supported by the required institutional evidence, and what happens in that situation?**

This would clarify whether the final accusation is an expression of player interpretation, a constrained institutional procedure, or both.

### **8.2 Interface**

Q90–Q92 are good.

I'd add:

**Q106 (R) What is the hierarchy of information presented to the player during investigation, and how does the interface distinguish important information from optional information?**

This connects interface design to epistemic agency.

**Q107 (R/V) Which interface elements provide affordances, which provide feedback, and which provide information about persistent game state?**

This would help structure your interface chapter academically.

**Q108 (V) What accessibility and usability limitations are present in the current prototype?**

For example, text readability, input flexibility, visual contrast, interaction discoverability, and reliance on particular keyboard inputs.

You don't need to claim the prototype is accessible. You should accurately describe its limitations.

### **8.3 Visual environments**

Q93–Q98 are appropriate.

I'd add:

**Q109 (R) How does the spatial arrangement of the precinct support the investigative structure?**

This is more specific than simply asking what the player can do in each room.

Consider whether spatial organisation:

- Groups related investigative activities.
    
- Establishes institutional hierarchies.
    
- Makes certain interactions discoverable.
    
- Creates meaningful movement between evidence sources.
    
- Communicates changes in narrative state.
    

**Q110 (R/V) Which environmental interactions are functional, which are decorative, and which provide narrative information?**

This would help prevent overclaiming the epistemic role of the environment.

**Q111 (R) What does the visual language of the dream environment communicate that the waking environment does not?**

This is particularly relevant to the distinction between documentary evidence and symbolic interpretation.

# **4. Questions that should be answered outside Chapters 4–8**

I agree with Claude's decision to park certain questions.

I would preserve that structure, but make the connections more explicit.

## **Introduction — Chapter 1**

|Question|Origin|Purpose|
|---|---|---|
|What is the central research problem?|4.01, 4.02|Establish the problem the thesis investigates.|
|What are the research questions?|4.01|Establish what the research will investigate.|
|What is the central thesis proposition?|4.05, 8.1 Q18|Explain bounded epistemic agency.|
|What are the principal contributions?|4.23–4.26|State what the research intends to contribute.|
|What is the scope of the project?|4.05|Clarify what the project does and does not attempt to demonstrate.|

**New question I'd add:**

**1.01 (R) What is the specific knowledge gap that this research attempts to address, and why is a game prototype an appropriate way to investigate it?**

This is worth answering because the project is not simply about making a detective game. You need to establish why the design problem merits research.

## **Methodology — Chapter 3**

|Question|Origin|Purpose|
|---|---|---|
|Why Research-through-Design?|7.03, Q17|Justify the methodology.|
|How are the design iterations structured?|6.01, 7.03, Q17|Explain the development process.|
|How were rehearsal participants recruited?|6.02|Establish research procedures.|
|How was consent obtained?|6.02|Establish ethical compliance.|
|How were recordings and participant data stored?|6.02, Q41|Explain data management.|
|How were qualitative observations coded?|6.12|Explain analysis.|
|How was AI assistance used?|7.19, Q75|Disclose the role of AI in development and writing.|
|Which assets were AI-generated or externally sourced?|Q97|Disclose asset provenance.|
|How were music and sound assets licensed?|Q81|Establish copyright and licensing compliance.|

**New question I'd add:**

**3.01 (R) What is the relationship between the formative research phase, the design formalisation phase, implementation, and summative playtesting?**

I think this deserves an explicit methodological diagram.

**Formative exploration**

Physical design rehearsals — Chapter 6

**Design formalisation**

Narrative and system architecture — Chapter 7

**Digital prototyping**

Unity implementation — Chapter 8

**Summative evaluation**

Digital playtesting — Chapter 9

**Synthesis**

Findings and research implications — Chapters 10–12

The important thing is to establish that these phases have different purposes and that the evaluation isn't simply another development iteration.

## **Chapter 9 — Playtesting**

I'd preserve Claude's existing parked questions.

However, I'd group them by research proposition rather than simply listing them in the order they were discovered.

|Evaluation dimension|Existing questions|
|---|---|
|Evidence interaction|Q9, Q16, Q50, Q51|
|Dialogue and social resistance|Q47, Q55|
|Narrative progression|Q17, Q28, Q54|
|Temporal behaviour|Q32, 4.18|
|Dream interpretation|4.20, 6.16 Theme 4|
|Interface comprehension|Q48, Q64, Q65|
|Environmental exploration|Q35|
|Player interpretation|5.5.3, 5.20|
|Research contributions|4.26|

I'd add three questions:

**9.01 (D) What investigative strategies do players develop spontaneously, and do these strategies correspond to the intended design?**

This is particularly relevant to epistemic agency.

**9.02 (D) When players arrive at an incorrect or incomplete interpretation, what caused it?**

Was it insufficient information, misleading information, interface confusion, failure to understand character behaviour, or an interpretation that the author didn't anticipate?

**9.03 (D) Which mechanics did players actively use, which did they ignore, and which did they misunderstand?**

This could be very useful for determining whether the five systems actually contribute to the experience.

One important qualification: Chapter 9 should distinguish between what the logger records, what direct observation reveals, and what participants report retrospectively. These are different kinds of evidence.

## **Discussion — Chapter 11**

I would retain Claude's question about the relationship between authored systems and epistemic agency.

I'd expand it with:

**11.01 (R) To what extent does bounded authorial control enable, constrain, or undermine epistemic agency?**

**11.02 (R) What are the limitations of using authored evidence combinations to represent investigative reasoning?**

**11.03 (R) What can the research say about the relationship between symbolic and factual knowledge?**

**11.04 (R) Which aspects of the design proposition were supported, contradicted, or left inconclusive by the evaluation?**

These should be answered after Chapter 9, not prematurely in the design chapters.

# **5. Cross-chapter questions that deserve special treatment**

There are several issues that shouldn't be treated as isolated questions because their answers affect the consistency of the entire thesis.

I'd create a separate section in the question bank called **Global consistency and design decisions**.

**G01 — Terminology**

Settle the canonical names of:

- Two-Slot Epistemic Interaction System / Interface.
    
- Dream Sequence / Dream–Awake Epistemic Loop.
    
- Workshop / Rehearsal.
    
- Captain Miller / Captain Turner / Captain Miller Turner.
    
- Julian Stoker / Julian Hammond Stoker.
    

Sources: 4.08, 5.12, 6.01.

**G02 — Narrative truth versus implementation**

Establish which discrepancies are outdated prose, intentional design changes, or implementation errors.

Sources: 4.20, 5.05, 5.10, 5.20, 5.22, Q69–Q70, Q73–Q77, Q96.

**G03 — Temporal model**

Establish the authoritative explanation of:

- The 24-hour investigation.
    
- One in-game hour equalling one real-world hour.
    
- Time-consuming actions.
    
- Delayed evidence.
    
- Cooldowns.
    
- The dream's six-hour cost.
    
- The 12-hour warning.
    

Sources: 4.18, 5.19, 7.12, Q33, Q78–Q80, 8.1.6.

**G04 — Evidence and accusation**

Establish:

- What evidence exists.
    
- What evidence is mandatory.
    
- What combinations are supported.
    
- What interpretations are accepted.
    
- What conclusions the player can submit.
    
- How institutional judgment differs from authorial truth.
    

Sources: 4.05, 4.09–4.12, 5.15, 5.20, Q16, Q18, Q23–Q26, Q84–Q89.

**G05 — Research methodology**

Establish the research chronology, ethics, participant data, AI disclosure, and evaluation methodology.

Sources: 6.02, 6.09, 6.12, 7.03, 7.19, Q17, Q41, Q75, Q97.

These are not additional questions that you necessarily need to answer separately. They are consistency checkpoints that help you avoid answering the same subject differently in several chapters.

# **6. The questions I consider most important overall**

If I had to reduce everything to the questions that will have the greatest impact on the quality of the thesis, I'd choose these.

Highest priority

|ID|Question|Why it matters|
|---|---|---|
|4.01|What are the research questions?|Everything else needs to connect to them.|
|4.05|What exactly is bounded in the interaction model?|Defines the central proposition.|
|4.11 / Q7|Why two slots?|Explains the central mechanic.|
|4.20 / Q96|What does the dream change in the waking investigation?|Resolves a significant design inconsistency.|
|4.24|How does the system manage authoring complexity?|Prevents overclaiming the technical contribution.|
|4.25|What does atmosphere contribute epistemically?|Determines whether this contribution is defensible.|
|5.04–5.05|What exactly happened on the night of the murder?|Establishes narrative coherence.|
|5.10|Can the secondary mystery influence waking interactions?|Clarifies the relationship between narrative layers.|
|5.20|What are the actual ending conditions?|Establishes the relationship between narrative and implementation.|
|6.16|How did workshop findings change the digital design?|Connects the research phases.|
|7.08|Why Petri nets?|Justifies the architecture.|
|7.18|Why a custom dialogue system?|Justifies a major technical contribution.|
|7.32|What were the architectural requirements?|Establishes what the architecture was designed to accomplish.|
|Q43|What trade-offs were realised?|Establishes the difference between intention and implementation.|
|Q83|What does the logger actually record?|Determines what can be evaluated in Chapter 9.|
|Q84–Q89|How does the accusation work?|Addresses a potential tension between agency and authored outcomes.|

I would work through these before worrying about the smaller questions.

# **7. A few questions I'd actually remove or merge**

I wouldn't necessarily delete them from your notes, but I'd avoid treating them as independent writing tasks.

|Questions|Recommendation|
|---|---|
|4.11 and Q7|One canonical answer about why two slots.|
|4.18 and Q78|One canonical answer about the temporal model.|
|4.20, 6.16 Theme 4 and Q96|One canonical answer about the dream's consequences.|
|4.24 and Q16|One answer about authoring complexity and its actual scale.|
|4.25, Q37–Q38, Q61 and Q104|One coordinated argument about atmosphere, sound and epistemic information.|
|5.20, Q23–Q26 and Q74|One canonical ending and accusation model.|
|6.16 and 7.01|The former derives design requirements; the latter establishes the architecture's objectives. They should reference one another, not duplicate one another.|
|7.19 and Q75|One AI-assistance disclosure in Methodology, with technical specifics referenced in Chapters 7–8.|
|7.24 and Q43|One answer about architectural trade-offs.|
|Q84 and Q23|Q23 explains the ending structure; Q84 should explain the complete player-facing sequence.|

I would also reconsider 4.23. Rather than simply changing _demonstrating_ to _exploring_, consider whether the contributions are:

- Proposed design contributions.
    
- Implemented technical contributions.
    
- Empirically investigated contributions.
    

Those can have different levels of evidentiary support.

# **8. How I'd use this question bank while writing**

This is perhaps the most important practical recommendation.

I wouldn't turn the question bank into another document that needs to be constantly maintained manually.

I'd make it your primary writing companion, with a consistent structure for each question.

For example:

**Example: 4.11 — Why two slots rather than one or three?**

P1

R

OPEN

**Question**

Why does the system use two evidence slots rather than one or three?

**What the answer needs to establish**

- What one slot would prevent the player from expressing.
    
- Why two slots provide the intended degree of combinatorial interaction.
    
- Why three slots were unnecessary or undesirable.
    
- How the number of slots relates to investigative reasoning rather than interface convenience.
    

**Existing information**

Chapter 8 Q7, currently unanswered.

**Destination**

Primary explanation: Chapter 4.2.2.

Implementation implications: Chapter 8.1.3.

**Expected output**

One substantive answer, potentially a few paragraphs, with a reference from Chapter 8 rather than a duplicated explanation.

I would also allow an answer to generate more than one output.

For example, when answering 5.20, you might produce:

- A definitive narrative outcome matrix.
    
- A corrected Chapter 5 table.
    
- A correction to Chapter 8.1.4.
    
- A verification task for the implementation.
    
- A Chapter 9 evaluation question.
    

That's entirely appropriate. The purpose of answering the question is to resolve the underlying subject, not merely fill a paragraph.

# **9. My final recommendation**

I think your existing Claude question bank is already approximately the right foundation. I'd preserve its original questions and numbering, add the new questions above, and introduce the cross-chapter consistency section.

The biggest improvement isn't adding more questions. It's making sure each question has a single, clear responsibility.

I would organise the actual working document into four layers:

1. **Chapter questions:** The questions you answer while developing the content.
    
2. **Cross-references:** Questions already answered elsewhere, which should not be answered twice.
    
3. **Consistency decisions:** Contradictions between your notes, prose, intended design, and implementation.
    
4. **Parked questions:** Questions that belong in the Introduction, Methodology, Chapter 9, Discussion, or appendices.
    

And one last thing: I would not force yourself to write the answers academically at this stage.

Answer them as you naturally would when explaining your design decisions. Use informal language, technical details, examples, even incomplete thoughts. Those answers are your source material.

The academic prose should come later, when the information is sufficiently complete.

**The objective of this question bank is to make sure that when you eventually consolidate the chapters, you aren't discovering missing design decisions, unresolved contradictions, or unexplained research choices while trying to polish the writing.**

That's the workflow I'd recommend for this thesis.