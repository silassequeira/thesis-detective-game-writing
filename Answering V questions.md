

I'll gather the remaining files in batches and check each question against them.

Now the scripts and settings files.

I went through every (V) question against the live repo and the scene dumps. Two are only partly settled: the dumps are older than some of the code (noted where it matters), and the interaction counts come from your mid-November extractor dumps rather than the live assets. I read files only and changed nothing.

The most important finding: two of your current claims are wrong. Section 8.1.4 says slip events wait until the last page, but only interaction slips wait; chain slips fire as soon as the question is chosen. And limitation 4 says the robbery-conviction route is unfinished, but it is wired up (see Q26 below).

## 8.1 System Architecture

**1. Build version.** `bundleVersion` is **0.1.0** (product name "Thesis Detective Game"). The build contains 4 scenes, in this order: MainMenu, GeometryAttempt, Ending_Sequence, Dream_Sequence. No build output is stored in the repo, so add the date yourself.

**10. Order in which questions appear.** This is set in `CombinationEvaluator.SortByHierarchy`, highest first:

1. resume
2. paired primary
3. paired ranged
4. single-item (primary before ranged)
5. narrative chains
6. interactions with no trigger
7. paired interactions
8. single-item interactions
9. the weak question, always last (newest chain first)

Two details: resume options only appear when both slots are empty and you're not inside a chain, and only in the mode of the bookmarked step. The draft 8.1.3 already matches this.

**11. Diminished responses and chain breaks.** Yes, both are in the build:

- The first weak question plays diminished response 1; the second in a row plays response 2 and breaks the chain.
- Any answered question resets the counter.
- One gap: the result object has a `chainBroken` field that `DialogueUI` never reads. After a break the panel just re-evaluates instead of showing only "End conversation".

**12. Strength.** Confirmed: by default +1 per Confrontation question and 0 for Inquiry, counted once per question, ever, and never reset. Only two narrative rules use it, both for Kae:

- **CONFESSION (KAE_PRESSURED_EVENT):** `FLAG_KAE_PRESSURED` plus Kae strength **≥ 27**, priority 20, fires once.
- **OBTANING_F1_EVENT_TIME:** `FLAG_POST_TIME_WARNING` set, F1, L1 and KAE_PRESSURED all _not_ set, plus Kae strength **≥ 13**, priority 5, fires once.
- E14R_ACQUIRED uses a flag only.

If every advancing question were asked, Kae's strength could reach 414, so both thresholds are reachable. Strength is never shown to the player.

**13. Leaving a chain mid-way.** Closing the panel breaks the chain, but the bookmark and the record of visited steps survive. When you return, the chain resumes at the first unvisited step. The resume option re-equips the original evidence and replays that exchange with its variation response.

**14. Corpus size.**

||Registered chains|Steps|Inquiry / Confrontation|Questions|With weak question|
|---|---|---|---|---|---|
|Elara|22|41|~20 / ~21|108|23|
|Kae|30|54|19 / 35|165|40|
|Miller|20 (15 confrontation + 5 warnings)|24|0 / 24|50|5|

Interaction files (excluding Unused): Elara 101, Kae 129, Miller 96 (14 of them special requests), plus 1 for the ending.

⚠️ **`CHAIN_ELARA_BLACKOUT_CONFRONTATION` is not in `LogicChainDatabase`**: 73 chain files, 72 registered. Players can never reach it.

**16. Authored pairs.** Roughly 215 distinct pairs are authored: 144 "all" pairs inside chains, plus the 147 interaction files named after a pair, minus overlap. Up to 38 terminal rules come on top, so about 250 of the 1,830 possible pairs (~14%). This is an estimate: interaction pairs were counted from file names. Also, every single-item trigger means _any_ pair containing that item surfaces something, so the share of pairs that produce _some_ response is much higher.

**23. How the Miller confrontation sets the verdict:**

1. **Gate:** "I'm ready to present the case" (`MILLER_CONFRONTATION_00`) only appears once the clock has started and E1R, E2R, E3R and E9R are all acquired. Before that, `MILLER_CONFRONTATION_FAIL` sets `FLAG_CASE_NOT_READY` (this is your "not enough evidence" path). A suppression rule removes the FAIL option once all four reports are acquired.
2. "I'm ready, I don't need to investigate further" moves on; "I'm not ready" sets `FLAG_MILLER_CHAIN_RESTORE`, and a reset package reopens the loop.
3. **Step 1 (the shooter):** sets `FLAG_ELARA_SHOOTER` or `FLAG_KAE_SHOOTER`.
4. **Step 2 (motive):** sets `FLAG_ELARA_MOTIVE` or `FLAG_KAE_MOTIVE`, either from evidence or from a no-evidence version gated by flags.
5. **Step 3 (involvement of the other suspect):** sets one of four ending flags, plus `FLAG_ENDING_SEQUENCE_STARTED` and `FLAG_MILLER_CONFRONTATION_DONE`.

**The fired path:** during the angry confrontation (armed by `FLAG_MILLER_AT_PLAYER`), `MillerPatienceWatcher` fires as soon as Miller's patience reaches 0. At 0.5 per confrontation misstep, that's two missteps. It plays MILLER_PLAYER_FIRED, which sets `FLAG_MILLER_PLAYER_FIRED`, and that triggers the `FiredSecondWarning` ending.

**24. How Chapter 7's ending tables map to the build.** Chapter 7 had separate conviction flags (ELARA_FREE, ELARA_MURDER, ELARA_ACCOMPLICE, KAE_MURDER, KAE_GUN_POSSESSION) combined at the end. The build replaces them with **four combined ending flags**, each set by one step-3 slip, and gives each ending path its own reactions. Kae variants A–D became two overrides:

- **Pressured:** `FLAG_KAE_CONFESSION` + `FLAG_ELARA_SHOOTER` → replaces Kae's reaction.
- **Robbery conviction:** replaces Kae's reaction _and_ the outcome.

The confession-tape and E4-TRACE variants have no override in the build. Also, each ending path's first condition group checks `ENDING_SEQUENCE_STARTED` (no `FLAG_` prefix), so that group can never pass. Endings still resolve correctly through the second group, but fix the typo.

**26. The robbery conviction is not unfinished.** `MILLER_STEP2_KAE_MOTIVE` fires `SLIP_STEP2_VERDICT_KAE_MOTIVE_ROBBERY_CONVICTION` on its prior-convictions and robbery-pattern questions. That sets `FLAG_KAE_ROBBERY_CONVICTION`, and the override swaps in both Kae's reaction and the outcome. What's missing is only a separate fifth ending path. Rewrite limitation 4.

**27. Number of flags.** About **127 distinct `FLAG_…` names** across data and code (43 of them are constants in `GameFlags`). A few flags break the naming convention: `BATHROOM_DREAM_EXPERIENCED`, `MILLER_BRIEF_00_COMPLETE` / `_01_COMPLETE`, and slip IDs named `FLAG_ELARA_IN_IR` / `FLAG_KAE_IN_IR`.

**30. Taking the drug outside the bathroom.** Yes, it's in the build. With AI + E15 equipped, pressing E near the injection trigger (radius 14.92) starts the dream; separately, the bathroom door has a "Force Door Open" action. It can only happen once (`FLAG_MOON_USED`). On return, the game deducts 6h and checks the room you're in: bathroom sets `BATHROOM_DREAM_EXPERIENCED`, anywhere else sets `FLAG_MILLER_ANGRY_SEQUENCE`.

**31. Interrogation-room gate.** It's still in the build, simplified:

- The door says it's locked until you call in a suspect.
- Showing the portrait (PE or PK) to Miller fires `FLAG_ELARA_IN_IR` / `FLAG_KAE_IN_IR` plus `FLAG_SUSPECT_IN_IR`, which opens the door. This can be repeated.
- "How can I bring one of the suspects in?" is a hint interaction you can only use once.
- ⚠️ That hint interaction (`REQUEST_MILLER_SUSPECTS`) has the interaction ID **`REQUEST_MILLER_PK`**, the same as the real Kae request. Play counts are tracked by ID, so the two interfere with each other.

**40. Autosave.** Every newly set flag, and every consumed world action, schedules a save **3 s later in real time**. A new event restarts the timer, and saves only happen in GeometryAttempt. The stairs door forces a save and then locks saving. There's no save on quit (that code is commented out) and no manual save.

**42. Debug keys in the playtest build.** `DevModeGate` (dated 22 Nov, newer than your dumps) keeps every debug tool **off in release builds until a code is typed in MainMenu**. In the Editor and in Development Builds they're always on. Whether playtesters had them depends on whether you shipped a Development Build. Your MainMenu dump predates the gate, so re-export it to confirm it's placed there. Also: the GeometryAttempt `PlaytestLogger` is inactive, so logging only works when the game is started from MainMenu.

**Slip-event name (8.1.1 vs 8.1.7):** it's `OnEventFired`.

## 8.2 Interface Design

**55. Patience is not shown to the player.** There's no meter. The only signal is the text "Evidence out of range — patience reduced", which is hidden while the conversation stream is collapsed (always shown in the archive). No low-patience warning flag is set for any character. In practice, players first notice when the panel suddenly closes and the cooldown line plays.

**59. Clock during panels.** It keeps running during every panel, including dialogue, inventory and read mode. Only the pause menu stops it.

**60. Printer or station.** It's a printer (`printer_OR`). Fix 8.1.5.

**63. USS custom properties.** No stylesheet uses `var()`. `RootReference.uss` defines a `:root` palette with a note saying "copy this block into every USS", but the panel stylesheets just hard-code the values. The code can't confirm the stated reason ("compatibility limited custom properties"), and UI Toolkit does support `var()`. Describe it as hard-coding, and drop or soften the reason.

**[TAB] on the HUD** opens the inventory on the equipped folder.

## Small bugs found along the way

- Every chain's `chainName` is its ID, so all 72 resume options read "Let's get back to CHAIN_…".
- `KAE_LOW_PATIENCE` has the sequence ID `ELARA_LOW_PATIENCE`.
- Three ending slips are referenced by nothing: `MILLER_WARD_NOT_ACCOMPLICE`, `MILLER_CONFRONTATION_START` and `MILLER_CONFRONTATION_DONE`. This is from the data I staged.

I can turn these answers into edits to the 8.1, 8.1.3, 8.2 and appendix drafts if you want.