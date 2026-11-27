# 5. Narrative Design: The Authored Case Model

## 5.1 Chapter Purpose

This chapter establishes the complete designer-facing narrative model that structures the interactive investigation. In dramatic theory, this model functions as the formal cause of the experience, representing the underlying dramatic structure designed before the player begins. Following Brenda Laurel's six elements of interactive drama: action, character, thought, language, pattern, and spectacle (Laurel, 2014). The design operates through a downward causal movement. The crime and characters establish the central situation, their motivations govern what they disclose or conceal, clues and testimonies form recognizable patterns, and the prototype's rooms and interfaces present those patterns to the player. Crucially, this formal cause does not dictate a single sequence of mandatory discoveries. Instead, it establishes a field of competing possibilities within which different investigative interpretations can become plausible.

The player never receives this complete model at once. They encounter fragments through police reports, testimonies, physical traces, and character reactions. Presenting the complete structure here contextualizes the player behaviors and design decisions examined in later chapters.

**5.1 Chapter Purpose**

5.01 (R/L) Which of Laurel's six elements do you actually use later, and how does "formal cause" connect to Mateas & Stern's formal constraints in 7.3.1? (The Laurel sentence is also currently a fragment.) — Open

> _"In this proposal, Laurel's (2014) concept of_ **formal cause** _provides the static structural foundation for the authored case model, establishing how plot, character, and thought dictate the distribution of evidence and testimony_*. In Chapter 7 (Section 7.3.1), this static formal cause is operationalized as dynamic* **formal constraints from above** _(Mateas & Stern, 2004)_. By evaluating player slot proposals against flag-gated logic chains and suspect patience thresholds, the dialogue engine uses formal constraints to maintain dramatic probability and narrative coherence, ensuring that active player interpretation unfolds within a structurally bounded dramatic architecture_

> **Action (Plot):** Established in **Section 5.2**

> **Character:** Established in **Section 5.3**

> **Thought:** Operationalized through the internal motivations, cognitive/psychoactive states, and secret goals of the characters (e.g., Elara's impaired memory and addiction, Kae's protective deception, Captain Turner's institutional pragmatism), as well as the internal cognitive labor (abductive reasoning) required of the player.

> **Language (Diction):** Represented by the text of the evidence reports, items, images, and the explicit text dialogue from interrogating the suspects using the two slot system

> **Pattern:** Represented by the logic-chain steps, evidence pairings, and relational links across documents that form recognizable, testable hypotheses aiming to provide Hermeneutic pleasure.

> **Spectacle (Enactment):** Operationalized in Chapter 8 through the physical and audio visual presentation.


> **Formal Cause in Chapter 5 (Designer-Facing Model):** Following Laurel (2014), **formal cause** is the static, overarching authorial blueprint of the whole action
> It flows downward: the crime (_action_) defines the suspects (_character_), whose motivations shape their secrecy (_thought_), which determines their statements (_language_) that influence the interrogation logic (_pattern_), that is ultimately rendered through the game interface (_spectacle_)

> **Formal Constraints in Section 7.3.1 (Runtime System Architecture):** Following Mateas & Stern (2004/2005), interactive drama translates formal cause into **formal constraints from above** that operate dynamically during play. While the Two-Slot interface provides **material constraints/affordances from below** (what the player can express), the system enforces **formal constraints from above** via global narrative flags, logic-chain step preconditions, suspect patience thresholds, and strength gates. In the workshop the formal constraints are not tracked through variables, but are instead a part of the role playing experience and being able to express these constraints.  

> **The Connection:** The authored case in Chapter 5 provides the structural _content_ of the formal cause. Section 7.3.1 provides the _mechanism_ that enforces that formal cause during play—using logic chains and state flags as **formal constraints** to narrow the space of dramatic probability as the player builds argumentative pressure, ensuring that player agency yields dramatic coherence rather than unconstrained, chaotic branching

---
## 5.2 The Authored Case

The narrative originated as a wider mystery set across a small town, centering on an addictive dream-inducing substance and the disappearance of a young woman (Figure 32). Because that scope exceeded what could be implemented and evaluated within an early playable prototype, the project was reconstructed as a bounded homicide investigation.

|   |
|---|
||
|##### Figure 32 - Concept Art of the Dream Environment (Left) and Small Town (Right)|

The victim, Arthur Penhaligon, was killed one evening by a single 9mm bullet to the forehead in the fictional city of Oakhaven. Two suspects are being held in custody, and the initial investigation conducted by Detective Thorne was left unresolved after his abrupt resignation. The player assumes responsibility for concluding the investigation using the files and physical traces left behind.

**5.2 The Authored Case**
5.02 ® What was cut when the small-town disappearance became a homicide, and what survived (the missing-person file, Somnoryl-μ)? — ◐ Partly: 5.2 gives scope as the reason; 5.2.7 shows what survived

> To answer this I would have to link it to an annexed file section that explain everything that the previous design proposition had going for. Basically it took place in a small section within a small town, had multiple locations, a revolved around a missing person case instead with a private detective. It had full character arcs being explored through dreams, that explored different character traumas and provided a symbolic interpretation for both the detective arc on his repressed memory, as well as the arc of figuring out a possible reason why the person went missing. The investigation in the small town revolved around, using people's statements in dialogue to influence the questions when interacting with other npcs, also had the reports and the evidences, but that wasn't the full main focus, and also had a layer of exploration of the locations to find the evidences, since it's not given by the terminal or the captain like in this version. The solution to this answer should be to link to the annexed file that contained the full design proposal written, that was abandoned. 
> 
> It survived the two slot epistemic system, the inventory organization, the inquiry and confrontation options, the focus on epistemic agency and multiple interpretations for a narrative as other small things. The narrative change to smaller scope homicide case, with less interactable characters, and a simple investigation was to reduce the scope into a doable solo developer project that could be delivered, tested and analyzed within the limited time that I had to do my thesis.   


5.03 (V) Are place names consistent everywhere (Oakhaven, Gallows Creek, Wharf Street, Fourth District)? — Open 

> Yes, since those names are introduced in the reports, all of those locations and details needed to be and stay consistent through out, to make the the fabula and the whole investigation credible, a minor narrative inconsistency could lead a player to change his interpretation to one that the narrative doesn't have investigative path option to pursue. For the future of the prototype, a 3D recreation of the crime scene and suspect's apartment intends to be made, to not only make sure that all of the distance and details are consistent in a materialized location, but also be able to provide further videos and images that are missing from the current evidence corpus.  

---
### 5.2.1 Elara, Kaelen, and Somnoryl-μ

Elara Vance and Kaelen "Kae" Ward (Figure 33) began their relationship two years before the murder, each carrying significant personal difficulties. Elara had a fragile relationship with her family and a pattern of emotional dependency on troubled partners. Kae had grown up in instability, learning to approach the world as hostile and unsafe.

|   |
|---|
||
|##### Figure 33 - Concept Art of Kaelen (Left) and Elara (Right)|

Shortly after they began dating, Kae introduced Elara to Somnoryl-μ, a fictional street drug also known as the Moon Drug (Figure 34). The substance produces vivid dreams that feel indistinguishable from waking experience, responding to the user's desires, memories, and emotional needs. For Elara, it became an escape from a waking world she experienced as painful and difficult to control. Her attachment to the drug was tied not only to physical addiction, but also to the emotional relief it provided.

Over time, Kae's relationship with the substance changed. He gradually lost the ability to experience the dreams as pleasurable and began taking smaller doses simply to avoid withdrawal. Even so, he continued purchasing the drug because he believed Elara still needed it. He obtained his supply on credit from a dealer named Rico, causing his debt to accumulate.

### 5.2.2 The Firearm and the Failed Robbery

With his drug debt growing and criminal activity increasing around his building, Kae acquired a Taurus 905 revolver with a filed-off serial number from an associate of Rico (Figure 34). He hid the weapon beneath the floorboards of their apartment for protection and never informed Elara that he owned it.

|   |
|---|
||
|##### Figure 34 - Taurus 905 (Left) Somnoryl-μ (Right)|

Prior to Arthur Penhaligon's death, Kae attempted to rob him. Concealing his face, Kae demanded Arthur's wallet, but Arthur resisted. The confrontation became aggressive before Kae fled empty-handed without firing the weapon. Arthur reported the attempted robbery to the police, and bystanders witnessed the altercation, establishing a documented prior link between Kae and the victim.

### 5.2.3 The Night of the Murder

On the night of the murder, Elara and Kae both consumed Somnoryl-μ before falling asleep. Because Elara consumed a higher dosage, the drug affected her more strongly. Kae woke later that night as his dose began wearing off and realized Elara was no longer in the apartment.

He waited until she returned. Her clothing was soaked from the rain, and she was barefoot. She appeared detached from her surroundings, failed to respond normally when Kae spoke to her, and was carrying his Taurus 905 revolver.

Elara did not explain where she had been. Moving as if she were sleepwalking and still partially inside the dream state produced by Somnoryl-μ, she calmly returned to bed and fell asleep without offering a coherent account of what had occurred. Frightened by her condition and the presence of the firearm, Kae heard police sirens outside and understood that a serious incident had taken place.

Rather than contacting the police or waking Elara to question her about the weapon, Kae returned the revolver to its hiding place beneath the floorboards. He placed her wet hoodie inside the laundry basket and remained alert for when officers would eventually canvass the building. His decision was driven by fear, transforming his awareness into active concealment. Even without knowing precisely what had happened outside, he recognized that the firearm could link one or both of them to a major crime.

Earlier that evening, Arthur Penhaligon had been walking toward his car after finishing a work shift when he was shot. Nothing was stolen from him, and there was no clear evidence that he had been pursued. The attack appeared sudden and disproportionate, killing him immediately with a single shot to the forehead.

The only direct witness was Meredith Gable, an elderly resident living in the same deteriorating apartment building as Elara and Kae. Looking out into the rain around the time of the shooting, she observed a figure moving through the street barefoot and wearing a dark, wet hooded garment. Because of the darkness, rain, and distance, she could not identify the person's face.

### 5.2.4 Kae's First Deception

When police arrived at the building that night, Kae stepped into the corridor to prevent officers from looking inside the apartment and claimed Elara was still getting dressed. Asked whether he had seen anyone moving through the area, Kae stated falsely that he had been watching television all evening and had not heard anything unusual. He also claimed Elara had gone to sleep early because she had work the following morning.

Kae recognized that the officers were suspicious, but his account prevented them from immediately inspecting the interior of the apartment. Although his statement was false in several respects, he still did not know whether Elara had committed the shooting or whether someone else had used the weapon.

The following morning, Kae warned Elara that the police would likely return with a search warrant and asked whether she remembered anything from the previous night. Elara misunderstood the intent of his question. She described the night as a pleasant dream and had no memory of leaving the apartment, walking barefoot in the rain, or carrying the firearm.

Interpreting her lack of memory as evidence that she had been involved in the shooting while impaired, Kae remained convinced that she had not acted with conscious awareness or intent. Blaming himself for bringing the weapon and the drug into their lives, his fear developed into a protective resolve to prevent Elara from being charged as the shooter and sentenced to prison.

### 5.2.5 The Arrest

Police soon returned with a search warrant. During the search, they uncovered the Taurus 905 revolver beneath the floorboards along with Somnoryl-μ, rain-dampened clothing, and trace materials linking the couple to the night of the murder.

Both Elara and Kae were arrested, and their apartment became part of the crime scene. Both suspects were clearly connected to the crime, though through conflicting sets of evidence that support competing interpretations of responsibility.

### 5.2.6 The Complete Account

The authored model contains two distinct, separable layers of explanation. The first layer establishes the grounded murder case, which contains the moral tension that governs all legal verdicts.

Within this primary account, Elara was the person who shot Arthur Penhaligon. She acted while severely impaired by Somnoryl-μ, experiencing an altered state that compromised her perception and erased her memory. While Kae slept, Elara rose in a somnambulistic state, moving with calculated, mechanical precision. She retrieved the hidden revolver from beneath the floorboards, left the apartment barefoot in the rain, and walked toward Arthur's route. Noticing someone following him, Arthur turned to see Elara aiming a revolver at him without any emotional reaction. Terrified, he lowered his posture, and before he could speak, she shot him directly in the forehead. She then walked slowly back to the apartment and returned to bed as if nothing had occurred.

Kae did not commit the murder, yet his actions contributed indirectly to the circumstances that made it possible. He purchased the illegal weapon, concealed its existence from Elara, returned to street crime, accumulated drug debt, and sustained their shared dependency on Somnoryl-μ. After discovering Elara in a disturbed state, he hid the firearm and lied to the police. His subsequent protective behavior makes him legally and morally implicated even though he did not fire the shot.

This distinction between direct physical action and indirect responsibility forms the central moral tension of the case. Elara is responsible for the physical act of killing Arthur, yet her capacity to understand and control that act was severely compromised. Kae did not kill Arthur, yet his reckless choices and concealment enabled the crime. Consequently, the case cannot be reduced to a simple opposition between an innocent suspect and a guilty villain.

Players can fully resolve this primary layer by questioning the suspects and examining police reports and photographs. A player who never engages with the second layer below can still reach any of the game's outcomes using standard investigative evidence.

### 5.2.7 The Second Layer

The second layer addresses the deeper mystery of how Elara accessed a hidden weapon she did not know existed, why she was targeted, and why Detective Thorne resigned. This layer is intentionally under-determined, designed to sustain player interpretation and post-game discussion rather than to be definitively resolved.

During an optional dream sequence, the player encounters a nihilistic dream entity that preys on mentally vulnerable individuals. Within the designer's complete model, the entity selected Elara specifically because her natural predisposition to sleepwalking, combined with the unusually heavy dose of Somnoryl-μ she consumed that night, made her susceptible to motor control during sleep. During the dream, the entity remarks that human existence is so paradoxical that people try their hardest to be anywhere else. This statement mirrors the cryptic note Detective Thorne left behind stating that he would rather be anywhere else. Recognizing that connection aims to encourage players to link Somnoryl-μ to an older, closed missing-person file stored inside a locked precinct room, suggesting that Elara's case belongs to a recurring pattern.

Within this underlying account, the entity learned how to control human bodies without leaving physical traces, orchestrated Arthur's murder, and located the hidden revolver by accessing Kae's dreams. Once an individual consumes Somnoryl-μ, the entity retains access to their consciousness during sleep, preventing them from ever feeling rested even after discontinuing the need for the drug. Detective Thorne resigned because he uncovered fragments of this phenomenon and realized it could never be prosecuted or explained within institutional police procedures.

Pursuing this second layer is entirely optional. It unlocks no additional physical clues, cannot be discussed with the suspects or Captain Miller Turner, and does not alter the available verdicts. Instead, it aims to offer observant players an interpretive framework that connects the murder to a broader conspiracy.


**5.2.1–5.2.5 Fabula**
5.04 ★ ® Give the exact timeline of the night: when Elara leaves, the time of death, her return, the sirens, the police knock. The 5.2.3 order ("Earlier that evening…" after Kae waking) is hard to follow. — ◐ Partly: the 7.3.2 note gives peak Moon effect 21:00–01:00 covering the time of death.

> I'll provide the diagram image that I created with the full complete timeline of the events. 

5.05 ★ ® What did Meredith actually see? 5.2.3 says a barefoot figure moving through the street; the intro video says she heard the shot and saw someone standing over the body. — ⚠ Conflict: 5.2.3 vs the 8.3.2 intro script (G02)

> The full reports will be available in the annexed file section to clear all of these evidence related questions. 

5.06 ® For a player who never enters the dream, is there any first-layer explanation for how Elara found a gun she didn't know about? — ◐ Partly: 5.2.7 gives the second-layer answer (the entity read Kae's dreams)

> No, this is meant to be the unanswered question of the case that aims to lead someone to explore the second layer of the narrative. Through the right evidence combinations and actions, the player could be able to extract what Kae actually knows of what happened that night, which would be enough for the player to have the full complete case to convict Elara, tricking Kae into providing the account of what really happened from his perspective, but the "How she found the gun", is the question that requires the player to interpret the symbolic knowledge present in the second layer.  

5.07 ® When was Kae's failed robbery of Arthur, and in the first layer is it coincidence that Arthur became the victim? — ◐ Partly: the 7.3.2 note mentions an "August incident" flag

> Yes, it was in fact a coincidence that complicates the investigation, Arthur wasn't the only one that Kae robbed prior to the night event. But this coincidence was designed to make Kae look guilty for the crime, but a player that paid attention would see that in E11R, in crime history report, and later in F1 report, the killing or violent thefts don't match his crime pattern. 

5.08 (V) Is Rico present in the build (evidence, dialogue, the ending)? — ◐ Partly: the 8.3 Ending note says his object exists but isn't configured

> This was I typo, I meant to say officer Ruiz that is mentioned in the reports along with Buckley, but narratively speaking, since Rico gets arrested if the player request the L1 report, it makes sense to have him present in the Ending Sequence Scene if the player made that request.   


**5.2.6–5.2.7 Two Layers**

5.09 ® Which in-build items carry the second layer (Thorne's note, Case 47, Case 19, Locked Room files)? List them. — ◐ Partly: Ch8 Q29 names Case 47 and Case 19; 8.3.2 mentions 25 Locked Room files

> This depends on the player's interpretation of course, but it's first introduced through these evidences related to the Moon Drug: 
> 
> X2- Moon Drug Police Medical Brief
> N1- Drug Official Medical Document
> E15- Somnoryl-μ Vials (Since it allows the player to trigger the dream sequence)
> E10- Video Surveillance Image GC-AL-02 (Photo Print) -- Ideally, for future improvements, there would be a way for the player to see the 5FPS video mentioned in E10R, which would show Elara walking really slow almost mechanized. 
> TN- Thorne's Note
> CASE-19 - Case file number 456-19-872 of the missing person case.

> 8.3.2 mentions 25 Locked Room files, maybe this to be more clear, but essentially the player in the locked room, is able to gather the two parts of the CASE-19, as well as all of the evidence reports that were gathered by Detective Thorne before dropping the case.  


5.10 ★ ® Is it still true that the second layer "cannot be discussed with the suspects or Captain Miller Turner"? — ⚠ Conflict: Ch8 Q20 lists a "Chain Elara Dream"; 6.4.5 has Elara daring the detective to take the drug. Answer together with 4.20 (G05)

> In the workshop, the players were able to question about the second layer, the statement "cannot be discussed with the suspects or Captain Miller Turner" relates to the fact that I wasn't able to implement those interactions in the digital prototype, since narratively speaking it makes complete sense for the player to make those questions. 
> 
> Elara daring the player to take the drug is instead a dialogue signifier that the player is able to perform that action. 

5.11 ® Why does the entity want Elara isolated in prison, and does the game convey that anywhere? — Open 

> I've removed that section, since an explanation of the entities motives just leads to further questions, I'll explore this layer further in the future, but for now, the second layer explanations is that the entity is able to enter people's consciousness through their dreams, this was an isolated event, where someone could theorize the entity wants to cause chaos, or is experimenting by controlling people's minds, either way, these types of conclusions should be the furthest the game could provide, with the intentions and bigger conspiracy, just not being revealed. 

## 5.3 The Knowledge Structure

### 5.3.1 Character Positions

Each character enters the investigation with distinct identities, motivations, relationships, and limitations that govern what actions and disclosures are dramatically plausible.

|   |
|---|
||
|##### Figure 35 - Concept Art for Captain Miller Turner (Left) and Detective Julian Stoker (Right)|

Detective Julian Stoker is the player character (Figure 35). A relatively junior homicide detective transferred to Oakhaven Central after solving a series of rural murders, he is positioned between two models of investigative work: strict institutional procedure and independent interpretation. Captain Miller Turner is evaluating whether Stoker is capable of handling a major homicide case, placing Stoker's professional standing directly at stake.

Captain Miller Turner is the chief of Oakhaven Central's fourth district station and oversees the investigation (Figure 35). Serving as Stoker's superior and evaluator, he represents institutional procedure. To Turner, a successful investigation produces an identifiable suspect, defensible evidence, and a closed file. He disregards emotional complexity, psychological trauma, or broader social causes unless they can be translated into a prosecutable charge, serving as the institutional standard against which the player's theory is tested.

Elara Vance is emotionally fragile, traumatized, and heavily dependent on Somnoryl-μ. During questioning, she attempts to speak truthfully about the fragments she remembers, though shame and her genuine memory gap restrict what she can provide. Her loyalty to Kae shapes every response. Even knowing his criminal history, she believes he is fundamentally gentle and incapable of murder, remaining unaware that he lost his employment and returned to robbery to finance their drug supply.

Kaelen "Kae" Ward is governed by a single primary objective during interrogation, which is to protect Elara. Motivated by guilt over bringing the firearm and the drug into their home, he lies, deflects questions, and is prepared to confess to a murder he did not commit if he believes doing so will prevent Elara from going to prison.

### 5.3.2 Knowledge Distribution

|                         |                                                                                     |                                                                             |                                                                        |
| ----------------------- | ----------------------------------------------------------------------------------- | --------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| Character               | Knows                                                                               | Does Not Know or Cannot Establish                                           | Attempts to Protect or Preserve                                        |
| Detective Julian Stoker | The physical evidence collected and the statements provided during questioning      | The complete relationship between the clues and the true sequence of events | Professional credibility and an independent investigative theory       |
| Captain Miller Turner   | Institutional procedures and the evidentiary standards required for prosecution     | The full emotional and subjective context of the suspects                   | Procedural efficiency and institutional closure                        |
| Elara Vance             | Her relationship with Kae and scattered fragments of her dreams from that night     | How she reached the crime scene or what she did while impaired              | Her relationship, dignity, and emotional stability                     |
| Kaelen "Kae" Ward       | The firearm's origin, his criminal activities, and Elara's condition upon returning | The exact sequence of Elara's altered actions or her intention              | Elara's freedom and her idealized perception of him                    |
| Meredith Gable          | The silhouette, bare feet, and wet hooded garment of the figure outside             | The identity or face of the person she observed in the rain                 | Her distance from neighborhood criminal activity                       |
| Detective Thorne        | Hints of the wider Somnoryl-μ pattern and the closed missing-person file            | How to establish the entity's involvement within institutional rules        | His distance from a case he cannot resolve within institutional rules. |

Table 1 - Knowledge Distribution

Distributing knowledge across these characters prevents the investigation from being resolved through a single authoritative testimony. Elara cannot explain the crime because she cannot remember it, Kae deliberately distorts his testimony to shield Elara, Meredith observed only a silhouette, and Turner evaluates legal adequacy without possessing the full truth. Stoker and the player must construct a coherent theory by cross-checking these incomplete perspectives against physical evidence.

### 5.3.3 Character as Constraint

Each character's established identity and circumstances impose intrinsic constraints on what they can say or do. Elara cannot suddenly provide a precise chronological account of the shooting under pressure because her psychoactive state genuinely prevented memory formation. Kae cannot calmly disclose every relevant fact as long as doing so threatens Elara's freedom. Captain Turner cannot accept intuitive certainty as a substitute for documented evidence because his institutional role requires prosecutable proof.

These limitations are not merely technical restrictions on dialogue. They give the fictional world internal coherence. Player agency is created by allowing the player to act meaningfully within a system whose responses remain consistent with the characters' motivations and constraints.

**5.3 Knowledge Structure**
5.12 ★ ® Which form of each name is canonical: "Captain Miller Turner", "Captain Turner" or "Captain Miller"; "Julian Stoker" or "Julian Hammond Stoker"? — ◆ Decision; canonical for character names (G01) 

> I've made these changes, because the full name of each character is "Miller Turner" and "Julian Hammond Stoker" all of those variations are canonical, I made those variations to not repeat the same name over and over. 

5.13 ® Should Buckley get a character position in 5.3.1, given his role in guidance and onboarding? — ◐ Partly: 8.3.2 ("offers guidance") and Ch8 Q64

> I'm still thinking about this, since his role is specific to the digital prototype, his role in the narrative is to provide assistance, seeing that a lot of reports have his name. But he's not actually a big and important character as a part of the narrative, so I don't know what is the solution here. 

5.14 ® Do Stoker's mould and dust allergy and the auto-injector belong in 5.3.1 as part of the authored case? — ◐ Partly: Ch8 Q35 has the full rationale

> Maybe, its a part of his character, and shows his vulnerability, but it's also an aspect specific to the digital prototype, not being fully realized during the workshop, I don't know if a reader could ask why this wasn't explored in the workshop, and the reason is that the Locked Room was only fully realized for the digital prototype, some people during the workshop showed some interest in exploring it, but none of them did, so it's not really a fundamental part of the narrative itself, but it's structural to the digital prototype.  

5.27 (V) Does Table 1 (Knowledge Distribution) still match what each character can reveal in the build? — Open

> Yes, it matches what each character can reveal in the build, the narrative structure is the same. 

---
## 5.4 The Dramatic Structure

### 5.4.1 Three Levels of Conflict

The investigation operates as a negotiation among characters attempting to preserve their freedom, their relationship, their professional standing, or their understanding of themselves. The central dramatic conflict unfolds across three interconnected levels.

First is the indexical conflict concerning who killed Arthur Penhaligon. Physical evidence points in competing directions: Kae owned the firearm, possessed a criminal record, and had previously attempted to rob Arthur, whereas Elara was physically present at the scene while impaired by Somnoryl-μ. Several reports in the case file function as deliberate red herrings designed to misdirect players who fail to cross-check timelines and physical details. Even when the physical clues align, they do not independently establish intention or awareness.

Second is the relational conflict concerning what Elara and Kae will sacrifice to protect each other. Their relationship rests on mutual dependency entangled with concealment and protective deception. Investigative questioning forces these concealed truths into the open, supplying essential personal context that complements the cold facts in the forensic reports.

Third is the institutional conflict concerning what constitutes sufficient proof. Captain Turner represents the bureaucratic demand for a clear, defensible accusation rather than an exhaustive psychological truth. Stoker must translate an ambiguous human situation into a legally viable charge, even though satisfying Turner's institutional standard does not guarantee moral justice.

### 5.4.2 Dramatic Pressures

Before the player begins, the dramatic situation is already unstable. The murder has occurred, the suspects have been arrested, and Detective Thorne has resigned, leaving an incomplete file. Captain Turner assigns Stoker to conclude the case, establishing five dramatic pressures.

- **Narrative pressure.** The crime has already occurred, meaning the player can only reconstruct the event rather than prevent it.
- **Temporal pressure.** The investigation window is bounded, requiring Stoker to conclude inquiries before institutional deadlines close.
- **Professional pressure.** Stoker's career depends on the outcome, and failing to construct a well-supported accusation results in dismissal.
- **Epistemic pressure.** Because the evidence is incomplete and contradictory, the player must commit to a theory under conditions of uncertainty.
- **Moral pressure.** Neither suspect is a conventional villain, forcing the player to weigh intention, mental capacity, and consequence.

### 5.4.3 Dramatic Action

The player advances the investigation by examining physical evidence, requesting forensic reports, questioning suspects, consulting Captain Turner, and optionally entering the dream sequence. The specific mechanics and interfaces supporting these investigative actions are detailed in the Digital Prototype chapter.

### 5.4.4 Suspect Arcs: Accumulated Pressure and Attitude Shifts

A suspect's reaction under questioning often reveals critical information even when their words evade the question. Every confrontation or piece of evidence presented during interrogation advances both suspects along independent emotional arcs.

**Kae's Protective Collapse**

Kae enters the investigation committed to denial and deflection, sustaining that posture through counter-accusations and appeals to systemic unfairness. Each confrontation that exposes the facts he is concealing, such as his lost employment, the illegal revolver, his drug debts, or his false alibi, erodes that defensive posture. Realizing that maintaining his denials will leave Elara vulnerable to prosecution, Kae eventually offers a calm, fabricated confession designed to absorb all charges.

The design never labels Kae's confession as false. Instead, aims to test careful players that can identify direct contradictions between his account and the forensic record, most notably his assertion that Elara never left the apartment. Determining whether to accept his confession as truth or recognize it as a protective fabrication is one of the investigation's central interpretive acts. Once Kae confesses, his posture is permanent and he never returns to denial.

**Elara's Gradual Devastation**

Because Elara genuinely cannot remember the shooting, no amount of pressure can produce a confession. Instead, she undergoes a gradual emotional degradation driven by the player's interrogation choices. Initially, she defends Kae with earnest certainty. However, confronting her with evidence of Kae's deceptions fractures her understanding of their relationship, while relentlessly pressing her with physical evidence of actions she cannot recall toward emotional collapse. At the endpoint of her arc, she ceases engaging with the detective altogether, dissolving into tears and withdrawing from the interrogation. Reaching this state is not a failure state, but an intended dramatic outcome produced through persistent questioning.

The two arcs operate independently. A player can drive Kae to confess without devastating Elara, devastate Elara without eliciting a confession from Kae, trigger both outcomes, or trigger neither.

### 5.4.5 Revelations

As the investigation progresses, key revelations reshape the player's developing theory of the case.

| Revelation                     | Investigative Source                                       | Effect on the Player's Theory                                                                                                                                             |
| ------------------------------ | ---------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Kae's secret crimes**        | Financial and employment records, suspect interrogation    | Undermines Kae's alibi, establishes financial motive and criminal means, and exposes his ongoing deception.                                                               |
| **The Wharf Street pattern**   | Crime analysis report                                      | Connects Kae's failed mugging of Arthur to local robberies, but indicates that a fatal shooting breaks his established non-lethal modus operandi.                         |
| **Elara's peak impairment**    | Toxicology report                                          | Establishes that Elara was severely intoxicated during the murder window, supporting an interpretation of diminished capacity.                                            |
| **Elara's memory gap**         | Suspect interrogation                                      | Suggests her inability to recall the night stems from Somnoryl-μ impairment rather than calculated evasion.                                                               |
| **Alleyway particulate trace** | Forensic particulate report                                | Matches abrasions and particulate residue on Elara's bare feet to the crime scene alley, placing her physically at the site of the shooting.                              |
| **Kae's false confession**     | High-pressure suspect interrogation                        | Offers a coherent, prosecutable narrative that collapses if cross-checked against forensic evidence placing Elara at the scene.                                           |
| **Red herring reports**        | Auxiliary precinct files and witness logs (ex. E14R, E21R) | Introduces misleading or irrelevant leads that test whether the player cross-examines evidence before committing to a theory or influences their interpretation directly. |

Table 2 - Key Investigative Revelations

**5.4 Dramatic Structure**

5.15 ★ ® Which reports are red herrings, and what does each mislead toward? — ◐ Partly: Table 2 (E14R, E21R) and Ch8 Q18 and Q20 (the two-shape theory)

> Well it depends, some evidences, are meant to mislead towards making Kae seem more guilty, they reveal important information that allows the player to uncover Kae's criminal life, but mislead the player from going after Elara (ex. F1, L1, E12R, E21R). Then there are filler reports, meant to waste the player's time, or help me player catch the details that were present in the initial reports that are now made obvious (ex. E8-A, E13R, X4, E13, E20R, E21R, E14R, E17R), then there are ones that straight up lead players to look into another path entirely if they decide to actively go with E14R and E21R that are weak evidence as the basis of their theory and placing both suspects in crime scene, ignoring other stronger information such as E8R. Red Herring in this case is completely relative since it depends on the player's interpretation, one might hear Kae's false confession, and convict him because he believed it made sense, while other might hear his confession, and immediately know that he's providing a fake confession and trying to save Elara from getting convicted.

5.26 ® What makes each red herring fair: which contradiction lets a careful player see through it? — Open

> It depends as well, E14R, the contradiction that a careful player would see through, is that it's ambiguous, it contradicts the E8R witness, wasn't filled in to the system by Thorne, then the images E10, E10-B and the report only mention or show one figure, not two. E21R evidence complements this by showing possible footprints match, but saying that it's not enough to make establish a connection, plus the pattern of the footprint of the boot, doesn't match Kae's boots. Basically weak evidence. Then for Kae's confession to be true, the player would have to simply ignore the witness statement and other reports that directly contradict his confession.  

5.16 (V) What triggers Kae's confession in the build? — ↪ Answered: Ch8 Q12 (FLAG_KAE_PRESSURED + Kae strength ≥ 27). 5.4.4 should say that it is threshold-based

5.17 (V) Is Elara's "devastation" endpoint implemented? Is it her patience depletion cap, a flag, or a narrative rule? — Open

> It's not implemented right now, but I think I can still make this addition until the end of the delivery, but now I should just assume that it's not implemented since the playtest results don't have this character arc fully implemented, due to not having time, and being a solo-developer 

5.18 (V) Do the two arcs really stay independent in the build, and do they change the endings? — ◐ Partly: 8.1.4 and Ch8 Q24 (the "Pressured" override)

> Yes, there's the ending where if the player manages to get Kae's confession and decides to convict Elara for the murder of Arthur he will have a different reaction. They are independent in the build and serve different purposes. 

5.19 ® What does the temporal pressure ("institutional deadlines") correspond to in the build? — ↪ Answered: 8.1.6 (24 h, warning at 12 h); framing follows 4.18 (G03)

---

## 5.5 The Resolution Structure

### 5.5.1 Convergence Architecture

Rather than relying on a single linear sequence or an unmanageable tree of independent branches, the narrative employs a convergent structure. Players investigate the case through varied combinations of evidence, interviews, and interpretations before their paths converge into a bounded set of outcomes.

This architecture operates across three layers:

- **Investigative variation.** At the outset, players choose which reports to request, which objects to examine, and which lines of questioning to pursue. They may focus on Kae's criminal history and firearm possession, or examine Elara's physical condition and psychoactive impairment.
- **Interpretive convergence.** During the middle phase of the investigation, players weigh conflicting clues, evaluate the credibility of Kae's confession, and synthesize a coherent theory of responsibility. Player agency is concentrated in this process of forming a theory, as the player decides which evidence is reliable and when to conclude the investigation and commit to an accusation.
- **Resolution variation.** When the player presents their final theory to Captain Turner, private interpretation is transformed into an official institutional judgment. This confrontation produces one of a limited number of legal verdicts alongside distinct emotional outcomes for the suspects.

### 5.5.2 Principal Endings and Emotional Variants

Depending on the evidence gathered and the theory presented to Captain Turner, the investigation concludes in one of three legal verdicts or a single institutional failure state. Two players can reach the same legal outcome while producing markedly different emotional consequences depending on which truths were exposed during questioning.

| Outcome                                                                        | Required Case Theory                                                                                                                                                                                                                                                                                                                                                                                                        | Emotional Resolution Variants                                                                                                                                                                                                                                           |
| ------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Verdict 1** Kae convicted of murder, Elara released                          | Attributes the shooting to Kae based on weapon ownership, the prior confrontation, concealment and, optionally, his confession. Three interpretations lead here: (a) Kae acted alone and Elara is not placed at the scene; (b) the player concludes both suspects were present and Kae fired while Elara was too impaired to be held responsible; (c) the player additionally links Kae to the Wharf Street robbery series. | If Elara has been confronted with Kae's deceptions, she views him coldly and accepts his conviction. If she remains unaware, she leaves loyal and distressed by his arrest. Kae reacts with acceptance understanding that ultimately he got Elara out of going to jail. |
| **Verdict 2** Elara convicted of manslaughter, Kae convicted of obstruction    | Establishes that Elara fired the weapon while impaired by Somnoryl-μ, reducing her charge to manslaughter, while (a) convicting Kae for concealing the firearm and/or lying to the police; (b) convicting Kae for present at the scene and/or concealing the firearm and/or lying to police;                                                                                                                                | If Kae confessed to protect Elara yet the player convicts her anyway, Kae is left deeply shaken by the failure of his self-sacrifice.                                                                                                                                   |
| **Verdict 3** Elara convicted of manslaughter, Kae convicted of gun possession | Establishes that Elara fired the weapon while impaired, but (a) fails to prove Kae concealed the murder weapon; (b) Chooses to not include him in the murder accusation; limiting his conviction to illegal firearm possession.                                                                                                                                                                                             | Because Kae's protective cover-up is not fully exposed, emotional variation is narrowed, leaving both suspects estranged as Elara absorbs primary blame.                                                                                                                |
| **Failure State** Case dismissed, Detective Stoker fired                       | Triggered when the player concludes the investigation without sufficient supporting evidence to satisfy Turner's procedural standards.                                                                                                                                                                                                                                                                                      | The suspects remain in legal limbo while Stoker loses his position at Oakhaven Central.                                                                                                                                                                                 |

Table 3 - Resolution Outcomes and Emotional Variants

### 5.5.3 Catharsis

Because characters remain bound by their established limitations, no dialogue choice can undo the consequences of the past. Catharsis in this narrative is not defined as achieving a morally clean victory. Instead, it emerges from recognizing that every resolution leaves vital questions unresolved.

Outcomes are determined by the accusation with reasoning to support it, misleading evidence can produce a valid verdict through an incorrect reconstruction. This is consistent with the institutional conflict, as Turner evaluates defensibility, not truth.

Convicting Elara requires the player to weigh the justice of punishing someone whose conscious agency was compromised by Somnoryl-μ. Convicting Kae means imprisoning a man who did not fire the weapon and lied out of protective loyalty. Even securing Captain Turner's approval leaves the player questioning whether institutional closure is equivalent to moral justice. Ultimately, the resolution is designed to encourage players to reflect on the assumptions that guided their investigation, questioning whether possession implies guilt, whether memory loss implies innocence, and whether a confession guarantees truth.

**5.5 Resolution Structure**

5.20 ★ ® Table 3 doesn't match the build. Ch5 has Elara manslaughter + Kae obstruction or gun possession. The build has "Elara murderer" and a "Kae murderer / Elara accomplice" path that Ch5 doesn't have. For each difference, which case is it: Ch5 is outdated, the design changed during the build, or the build is wrong? Then write the definitive ending matrix once, here. — ⚠ Conflict; canonical for narrative vs build (G02). Sources: 8.1.4, Ch8 Q23, Q24, Q26. Ch8 Q25 and Q74 point back here

> This is a ID naming issue, "Elara murderer" is the ending "**Verdict 3** Elara convicted of manslaughter, Kae convicted of gun possession", "Kae murderer / Elara accomplice" relates to the "**Verdict 1** Kae convicted of murder, Elara released", the accomplice naming can be misleading, since the player can only prove that she could have been present in the scene, not that she was aware to be considered an accomplice. The verdicts in this chapter 5 are the canon ones, but there are other missing that are part of the build, such as the variation where on top of Kae being convicted for Arthur's murder he's also being convicted of the crimes in area if the player is able to present that it was him. And there might be other variantions that aren't fully realized right now that require further playtesting to see if they are worth adding or not, but this is for future improvements. 

5.25 ★ ® For each accepted ending, which information is mandatory, which is optional, which comes only from dialogue slips, and which only from the dream or the Locked Room? — ◐ Partly: Ch8 Q23 (gate: E1R, E2R, E3R, E9R) and 5.2.6 (the first layer is enough for every verdict)

> The ending sequence in the prototype isn't fully figured out, and requires playtesting to cover all possible accepted evidence in each step. But one of the possible mandatory for being able to convict Elara is to link the witness E8R to her feet condition related evidence such as E4R, while as for the motive, establish that she did it while being impaired and presenting E5R. For convicting Kae, the player needs can establish that he had the means since he owned the gun and the bullet, and for the motive, establish that he was the culprit of the E9R prior incident with Arthur, other stronger ones are ones like Kae's confession tape or Elara's E4-Trace, but are not mandatory. 
> 
> This  (gate: E1R, E2R, E3R, E9R) was established, but it needs further playtesting to know if it's working as intended or not, with the biggest question being related to the inclusion of E9R, since it's not an accessible evidence, but motivates the player to look and investigate further evidence and question characters, so this can only be measured only after having enough playtests to know.  

5.21 ® Are the locked-room death and "fired during the angry confrontation" part of the resolution structure? Ch5 lists only one failure state. — ◐ Partly: 8.1.6 (death), Ch8 Q23 (fired path)

> Maybe, they serve more of as a plausible consequence for the player's actions, his decisions could converge to the fired path, but I left out because they don't necessarily bring a cathartic resolution, but maybe I should add since they happen and are still one of the possible endings of the game. 

5.22 (V) Which emotional variants in Table 3 exist in the build? — ◐ Partly: Ch8 Q24 (the confession-tape and E4-TRACE variants have no override)

> The confession tape flag overrides Kae's dialogue if Elara is convicted, but the E4-Trace variant isn't implemented, but could make sense, since the player could show it to Kae, and choosing to spare Elara should bring a different dialogue override, but it's currently not implemented. 

5.28 (V) Which outcomes and variants described in this chapter can actually be reached in the build, and which are incomplete? — ◐ Partly: Ch8 Q24 and Q26; extends 5.22 to the whole chapter

> Almost all of them, only this one that reflects Elara's Arc isn't "If Elara has been confronted with Kae's deceptions, she views him coldly and accepts his conviction. If she remains unaware, she leaves loyal and distressed by his arrest. Kae reacts with acceptance understanding that ultimately he got Elara out of going to jail."

5.23 ® How does the ending scene (cells, Miller's approach, yellow light) deliver the catharsis described in 5.5.3? — ◐ Partly: 8.3 Ending Sequence note ("both trapped")

> First and more importantly, the player gets both character's reactions to their outcomes, that reflect the player's decisions, then Kae warns dialogue reaction implies that the prisons in oakhaven are not entirely good, indicating that she her fragile state could lead to her death. If Elara is free, she gets to meet her Parents again and start over without being influenced by Kae, and having another chance to fight her addiction. Lastly Miller outcome dialogue, also provides the last resolution point, where if Kae gets convicted for Arthur's Death he suggests that he could get the death penalty. I'll provide the outcome dialogue as an annexed file. 

5.24 ® 5.6 refers to "the Workshop chapter" and "the Digital Prototype chapter". Update to the final chapter titles. — Open

> The follow up is the Workshop chapter, so a better transition paragraph is required here. 

### 5.6 Chapter Synthesis

This chapter established the complete designer-facing narrative model governing the interactive investigation, detailing the fabula of Arthur Penhaligon's death, the distribution of knowledge across characters, and the dramatic structures that guide players toward a resolution.

Rather than relying on unrestricted narrative branching, the design supports player agency through the selection, combination, and interpretation of incomplete evidence. These interpretive paths converge into three legal verdicts or an institutional dismissal state, each paired with emotional consequences shaped by how the player confronted the suspects.

This narrative architecture provides the foundation for the subsequent phases of the research. The Workshop chapter examines how this formal structure was enacted through low-fidelity materials and facilitator-led role-play, while the Digital Prototype chapter describes how these investigative relationships were implemented within an interactive system.