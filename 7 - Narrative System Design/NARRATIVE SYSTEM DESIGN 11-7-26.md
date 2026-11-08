# 6. Narrative System Design

The low-fidelity rehearsal revealed that the central design proposition of the project was viable but required substantial revision before digital implementation.The sessions revealed narrative inconsistencies, unclear interaction boundaries, incomplete information routes, unreliable facilitation-dependent responses, and insufficient support for evidence organisation and theory revision.

The purpose of the revision was therefore not simply to add more content to the mystery. It was to reconstruct the evidence corpus, interaction logic, and narrative space so that the digital prototype could more reliably support epistemic agency. The revised prototype had to preserve ambiguity concerning responsibility for Arthur Penhaligon’s death while ensuring that ambiguity emerged from competing but intelligible interpretations of evidence rather than from contradictory dates, inaccurate reports, unclear interaction rules, missing information, or unintended dead ends.

The revision followed five connected design objectives:

1. Correcting contradictions and inconsistencies in the evidence corpus.
    
2. Clarifying the distinction between evidence requests, investigative intentions, inquiries, confrontations, and final accusations.
    
3. Translating the low-fidelity interaction model into a more structured digital Logic Chain and flag system.
    
4. Expanding the precinct into a limited but meaningful navigable environment that supported further investigation, reflection, and narrative context.
    
5. Providing tools that allowed the player to organise information and retain their own developing theories without automatically resolving the mystery for them.
    

The revised narrative should therefore be understood as a direct response to the workshop findings. It is not presented as a final or fully validated version of the game. Instead, it represents the next Research-through-Design iteration: a more coherent and testable digital articulation of the systems rehearsed through the tabletop sessions.

### Evidence Corpus Revision

A central outcome of the workshop was the identification of inconsistencies that could distort participant reasoning. These inconsistencies were especially important because the project depends on allowing players to construct theories from incomplete and ambiguous information. While most of the narrative inconsistencies were adjusted between sessions when those inconsistencies were identified, the evidence corpus was fully revised before beginning the development of the digital prototype. Since the reports contain unintended contradictions, players may develop theories that appear reasonable but are based on material errors rather than interpretive openness. The revision therefore distinguished between intended ambiguity, which should remain available for player interpretation, and unintended inconsistency, which needed correction (X).

The revised corpus further expands the available material through new reports, maps, environmental documents, and archival case material. These additions were made to address the multiple requests that participants made during the workshop sessions, that fit within the overall narrative, or serve to close off possible narrative inconsistencies. They connect the central homicide investigation to specific navigable locations in the precinct, the history of the previous detective, the wider anomaly surrounding Somnoryl-μ, and the player’s ability to decide which investigative routes are worth pursuing. 

### Revised Spatial Narrative

The low-fidelity workshop was spatially constrained by its tabletop format, but participant behaviour showed continued interest in environmental exploration. Several participants attempted to inspect the precinct, open doors, investigate unavailable rooms, or ask questions about physical objects outside the central evidence system. These attempts sometimes revealed expectation gaps, but they also showed that participants understood the police station as a narrative space rather than merely as a neutral interface surrounding the evidence cards.

The digital prototype therefore expands the precinct into a limited set of explorable locations. Its purpose is to give environmental interaction a narrative and epistemic function while maintaining a manageable prototype scope.

#### Locked Evidence Room

The first new area is an inaccessible room located inside or adjacent to the evidence room. The player initially encounters a locked door and may inspect it to obtain the Locked Door Note (LDN). The note provides an institutional and narrative reason to ask Captain Miller for access. By presenting the note and communicating an appropriate investigative intention, the player can request the keys (KEYS) needed to enter the room.

The room contains an archived case file, CASE-R-456-19-872, together with associated images and physical evidence, CASE-456-19-872. This material expands the larger mystery surrounding the previous detective and the anomalous elements associated with Somnoryl-μ. The archive includes a missing-person report, travel-verification and welfare-check material, witness testimony, a supplemental anomaly memorandum, a closure notice, and associated visual material.

The room also creates a sequence focused on Julian’s vulnerability. Upon entering the dusty and neglected archive space, Julian experiences a severe allergic reaction. The player must use Julian’s auto-injector (AI) together with the adrenaline vial (AV) to stabilise him before continuing the search. This interaction provides a practical purpose for the adrenaline vial while also establishing that the detective is physically vulnerable and cannot treat the investigation as a purely abstract exercise in information management.

The sequence should be implemented carefully. Its function is not simply to create an arbitrary obstacle or a conventional item-use puzzle. It should reinforce the relationship between physical exploration, bodily fragility, institutional neglect, and the traces left by the previous investigation. The room therefore expands the narrative context of the mystery while remaining connected to the project’s central concern with knowledge, uncertainty, and interpretation.

#### Bathroom and Dream Entry

The unused bathroom accessible through the precinct corridor provides a separate location for initiating the dream sequence. The player must communicate an investigative reason for entering the neglected space and use Julian’s auto-injector with a Somnoryl-μ vial to enter the dream state. This creates a more coherent spatial and material framing for the dream–awake loop than an unrestricted or unexplained transition.

The revised dream interaction allows Julian to wake from the dream and return to the precinct without Captain Miller automatically forcing a final confrontation. The dream is therefore not treated as an ending or a failure state. It becomes a voluntary but consequential investigative action. Entering the dream consumes seven hours of the limited investigation period, making it a Kairos-related decision. The player must assess whether the potential symbolic and narrative value of the dream justifies the time lost for questioning suspects, requesting reports, exploring the precinct, or preparing the final case.

This design is important because it preserves the dream’s interpretive openness. The dream does not reveal a direct solution to Arthur’s murder. It instead confronts Julian with his desire for truth, the fragility of perception, and the possibility that seeing something does not guarantee understanding or acceptance. The player may return to the waking investigation with new questions about testimony, memory, responsibility, consciousness, and the difference between institutional proof and subjective experience.

#### Jail Floor and Resolution

The jail floor becomes accessible after the player presents a case to Captain Miller. This area provides a final narrative sequence in which Julian can visit Elara and Kae in their cells before the game concludes. The purpose of this sequence is to make the final judgment legible as a consequence of the player’s interpretation rather than as a purely abstract results screen.

The reactions of Elara and Kae can vary according to the evidence revealed during the investigation and the flags established through dialogue. For example, Elara’s reaction may differ depending on whether she was made aware of Kae’s deception, criminal history, confession, or possible sacrifice. Kae’s reaction may differ depending on whether he confessed, whether the player challenged inconsistencies in that confession, and whether Elara was accused despite his attempt to redirect responsibility.

After these conversations, Captain Miller communicates the institutional outcome. A final image summarises the consequences for both suspects, followed by the credits. This structure allows the ending to retain emotional and narrative weight while preserving the principle that the player’s accusation emerges from their own interpretation of the available evidence.