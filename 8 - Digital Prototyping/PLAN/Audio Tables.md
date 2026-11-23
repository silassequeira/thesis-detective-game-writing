
# Music tracks and their triggers

Source: `MusicCueDatabase` (27 cues; `CUE_MENUS` excluded). Track names are cleaned of file numbering.

**Gate for every cue:** the internal clock must be running (`requireClockRunning`). It starts at `FLAG_INTERNAL_CLOCK_STARTS`.

**Legend:** forced = interrupts the current cue if its priority wins; queued = waits in the queue (max 8) or plays when eligible. Priority: higher wins. Every cue plays once per run (until New Game resets it).

| Group            | Track                                              | Artist                               | Trigger                                                          |
| ---------------- | -------------------------------------------------- | ------------------------------------ | ---------------------------------------------------------------- |
| Clock            | Weaver Of Dreams                                   | Freddie Hubbard                      | `FLAG_INTERNAL_CLOCK_STARTS`                                     |
| Clock            | Round Midnight                                     | Joe Henderson, Al Foster, Rufus Reid | Under 15 h remaining on the clock                                |
| Clock            | Maiden Voyage                                      | Herbie Hancock                       | `FLAG_TIME_WARNING` (12 h remaining)                             |
| Evidence / world | Love Theme (From Chinatown)                        | Jerry Goldsmith et al.               | `FLAG_E4-TRACE_ACQUIRED`                                         |
| Evidence / world | Film Noir                                          | Paul Pritchard                       | `FLAG_N1_ACQUIRED`                                               |
| Evidence / world | Deep In A Dream                                    | Sonny Clark                          | `FLAG_BR_DOOR_OPEN`                                              |
| Evidence / world | `Heartbeat_SFX` (sound effect, not a track)        | n/a                                  | `FLAG_LOCKED_ROOM_SEQUENCE_STARTED`                              |
| Altered states   | Something I Dreamed Last Night                     | Miles Davis Quintet                  | `FLAG_AV_USED`                                                   |
| Altered states   | Quarto de Hotel (reverbed)                         | Hareton Salvanini                    | `FLAG_MOON_USED`                                                 |
| Altered states   | Dam That Dream                                     | Hank Mobley                          | `FLAG_DREAM_EXPERIENCED`                                         |
| Elara            | I Had The Craziest Dream                           | Dizzy Reece                          | `FLAG_ELARA_DREAM`                                               |
| Elara            | Here's That Rainy Day                              | João Gilberto, Stan Getz             | `FLAG_ELARA_GUN_REACTION`                                        |
| Elara            | A Flower Is A Lovesome Thing                       | n/a                                  | `FLAG_ELARA_SLEEPWALKING`                                        |
| Elara            | I'm A Fool To Want You                             | Donald Byrd                          | `FLAG_ELARA_AWARE_KAE_CONFESSED`                                 |
| Kae              | I Got It Bad And That Ain't Good                   | Oscar Peterson Trio                  | `FLAG_KAE_CONFESSION`                                            |
| Kae              | Solitude                                           | n/a                                  | `FLAG_KAE_CRIMINAL`                                              |
| Kae              | Indelible and Nocturnal                            | Wynton Marsalis                      | `FLAG_KAE_FALSE_ALIBI`                                           |
| Kae              | Here's That Rainy Day (second version, file "04.") | n/a                                  | `FLAG_KAE_RESPOSIBLE_AUGUST_INCIDENT` (spelling as in the asset) |
| Case theory      | When I Fall In Love                                | n/a                                  | `FLAG_FINANCIAL_ISSUES`                                          |
| Case theory      | Alone Together                                     | n/a                                  | `FLAG_TWO_SHAPES_THEORY`                                         |
| Miller           | Afterglow                                          | Bob Sneider, Joe Locke               | `FLAG_MILLER_ANGRY_SEQUENCE`                                     |
| Miller           | Summer Night                                       | Miles Davis                          | `FLAG_MILLER_PLAYER_FIRED`                                       |
| Endings          | Theme from Twin Peaks: Fire Walk with Me           | Angelo Badalamenti                   | `FLAG_ENDING_KAE_MURDER_ELARA_FREE`                              |
| Endings          | Night Flower                                       | Donald Byrd                          | `FLAG_ENDING_KAE_MURDER_ELARA_ACCOMPLICE`                        |
| Endings          | Moon Dreams                                        | n/a                                  | `FLAG_ENDING_ELARA_MURDER_KAE_ACCOMPLICE`                        |
| Endings          | Strange Fruit                                      | n/a                                  | `FLAG_ENDING_ELARA_MURDER_KAE_GUN_ONLY`                          |
| Endings          | Virgo                                              | n/a                                  | `FLAG_ENDING_GETS_KILLED`                                        |

## Notes

- 26 tracks plus 1 sound-effect cue (the locked-room heartbeat) make up the 27 cues.
- `Round Midnight` is the only cue with a non-flag trigger. It still requires the clock to be running.
- Most cues play at volume 0.1; the Elara, financial and two-shapes cues use 0.075.
- No cue uses `blockedByFlags`.
- Tracks in the music folder not assigned to any cue: Aphex Twin (#2), Blue And Sentimental, Park Avenue Petite, Quarto de Hotel (non-reverbed).
- Lane groupings are by narrative role. Where the Elara, Kae, case-theory and ending flags are set was not traced.




# SFX assets and their triggers

Source: `SFXDatabase` (`Assets/Sound/SFX_Data`). Clip names resolved from the `.meta` GUIDs.

**Shared by every entry:** volume 1, priority 0, no loop, played through the 8-source SFX pool. A flag entry fires only when its flag is newly set. Flag names are trimmed by `SFXManager`.

| Entry                   | Trigger                         | Clips                                                                            | Selection                            |
| ----------------------- | ------------------------------- | -------------------------------------------------------------------------------- | ------------------------------------ |
| Universal slip variants | Any slip event (`OnEventFired`) | `slipevent.ogg`, `slipevent_1.ogg`, `slipevent_2.ogg`                            | Random of 3, avoids immediate repeat |
| Opening Doors           | `FLAG_LOCKEDDOOR_OPEN`          | `openingdoor.ogg`, `openingdoor_1.ogg`, `openingdoor_2.ogg`, `openingdoor_3.ogg` | Random of 4, repeat allowed          |
| Opening Doors           | `FLAG_SUSPECT_IN_IR`            | same four clips                                                                  | Random of 4, repeat allowed          |
| Opening Doors           | `FLAG_BR_DOOR_OPEN`             | same four clips                                                                  | Random of 4, repeat allowed          |
| Pick Up Paper           | `FLAG_PICKUP_PAPER`             | `pickup_paper.ogg`                                                               | Single clip                          |
| Pick Up                 | `FLAG_PICKUP`                   | `pickup.ogg`                                                                     | Single clip                          |
| Toilet Flush            | `FLAG_TOILET_FLUSH`             | `toiletflush.ogg`                                                                | Single clip                          |
| Keys                    | `FLAG_KEYS_ACQUIRED`            | `key.ogg`                                                                        | Single clip                          |

## Notes

- Flag setters (from the scene dump): `FLAG_LOCKEDDOOR_OPEN` by the Open Door action with KEYS; `FLAG_BR_DOOR_OPEN` by the bathroom door actions; `FLAG_PICKUP_PAPER` by the locked-room case folder; `FLAG_PICKUP` by the tape container and evidence/case boxes; `FLAG_TOILET_FLUSH` by the Flush Toilet action. The setters of `FLAG_SUSPECT_IN_IR` and `FLAG_KEYS_ACQUIRED` were not traced.
- Flag sounds play only when the flag is newly set. I found no code that clears `FLAG_PICKUP`, `FLAG_PICKUP_PAPER`, `FLAG_TOILET_FLUSH` or `FLAG_KEYS_ACQUIRED`, so they likely play once per run. A `ChainResetListener` package could still clear one.
- Clips in the SFX folder not in the database: `Crying_SFX`, `computerstart`, `rattlinglockeddoor`, `rattlinglockeddoor_1`, `tapeeject`, `taperecording`.
- Footsteps are handled separately by `FootstepAudio`. `Heartbeat_SFX.ogg` plays through the music system (`CUE_LOCKED_ROOM_SEQUENCE_STARTED`).
