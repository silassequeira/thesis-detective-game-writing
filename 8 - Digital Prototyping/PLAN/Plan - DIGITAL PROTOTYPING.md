### Full version: about 15 pages (roughly 5,500–6,000 words plus 5–6 figures or tables)


### Proposed structure

**Chapter opening (about one page, no number):** purpose, scope (solo project, bounded window), tools (Unity 6000.3 LTS, UI Toolkit, NavMesh, ScriptableObjects), and the build version that was playtested. This build is the one Chapter 9 tests.

**8.1 Software Architecture**

- 8.1.1 Technical overview: scenes, assemblies, managers, the data-driven ScriptableObject pipeline.
- 8.1.2 Shared state: flags, evidence, slots, folders, pending evidence, and the clock. Include how the workshop afternoon became in-game hours.
- 8.1.3 From Petri net to code: a table mapping each net construct to its implementation. Mark what was kept, what diverged, and what was added.
- 8.1.4 Dialogue system implementation: Logic Chains, nodes, evidence ranking, patience and strength, slip events, narrative rules, suppression and reset. Then the authoring workflow, with your 7.3.2 notes moved here.
- 8.1.5 Accusation and endings: the final iteration, Miller’s patience, forced confrontation, the fired ending, and how “the system never confirms correctness” is enforced.
- 8.1.6 Dream sequence logic: triggers, consequences by location, and the return path to waking evidence.
- 8.1.7 Persistence, reset and instrumentation: save and reset behaviour, plus the playtest logger, since Chapter 9’s data depends on it.

**8.2 Visual Environments**

- 8.2.1 From four tabletop rooms to the precinct: a room table (room, what it exposes, epistemic function), compared with Figure 38.
- 8.2.2 Environmental clues and how the space answers the workshop’s out-of-scope requests.
- 8.2.3 Isometric camera, navigation, and interaction cues, i.e. how players know what is interactive.
- 8.2.4 Lighting and mood: noir, rain, atmosphere.
- 8.2.5 The dream environment, from concept art (Figure 32) to the built scene.

**8.3 Interface Design** (don’t repeat 7.4’s iterations, only final versus planned)

- 8.3.1 UI Toolkit pipeline: web prototype to UXML/USS, shared panel framework, palette.
- 8.3.2 HUD and persistent clock.
- 8.3.3 Evidence cards, inventory, folders, and drag rules.
- 8.3.4 Two-slot dialogue panel: Inquiry/Confrontation, question ordering, history, archive, failure feedback, character availability, patience cues.
- 8.3.5 Inspect and Read modes, plus the computer terminal, delayed reports, and time-advance panel.
- 8.3.6 Accusation interface.
- 8.3.7 Input scheme, on-screen hints, and what changed from the planned layouts.

**8.4 2D and 3D Art**

- 8.4.1 Art direction and scope decisions.
- 8.4.2 3D environment and props.
- 8.4.3 Characters and animation.
- 8.4.4 2D art: concept art, portraits, photos, report design, ending panels.
- 8.4.5 Asset provenance table (source, licence, modified or placeholder), with the full version in an annex.

**8.5 Sound Design**

- 8.5.1 Role of sound, starting from the workshop’s noir-jazz and rain.
- 8.5.2 Music and tension cues tied to the clock.
- 8.5.3 SFX, ambience, footsteps, UI sounds.
- 8.5.4 Mix, settings, and sound as epistemic infrastructure.
- 8.5.5 Provenance.

**8.6 Chapter Synthesis** (like your 5.6 and 6.5): the traceability table below, plus known limitations and cut features for Chapters 9 and 11.
