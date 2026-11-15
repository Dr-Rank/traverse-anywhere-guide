## Two distinct Mover choices

**Network Prediction Mover** and **Chaos Mover** are separate first-class routes alongside **CMC** and **GMC**. The final wizard is planned to expose both as dedicated full-animation choices, with the same optional-feature goals. Neither requires the paid GMC product.

## Select the actual pawn

The setup detects the pawn's backend and shows the relevant requirements. The supplied plugin contains the Mover integrations; enable **Traverse Anywhere** rather than installing extra older adapter plugins.

## Chaos setup rows

| **Row** | **What to do** |
| --- | --- |
| Async physics | Apply the required physics and prediction settings. Follow any restart advice before multiplayer testing. |
| Stable physics playback | Apply the row to support steady playback with uneven render frame times. It changes a project-wide setting, saves a backup and requires a restart. |
| Physics step rate | Optional. Read the trade-off before choosing a rate; Fix all leaves it alone. |
| Movement plugin | Enable GASP & Traverse Anywhere and restart if the integration is not loaded. |
| Chaos startup input | Apply the supported backend fix. A custom backend may need manual integration to preserve its own behaviour. |

Save before changing project-wide physics settings. If a row remains blocked after restart, read its reason: platform configuration or a higher-priority override can change the effective setting.

## Test in your game

Check approach, traversal and stopping with the frame rates you expect players to use. Test multiplayer views as well as the owning player. A custom Chaos pawn may need its normal braking settings tuned for a comfortable stop.

On remote Chaos pawns, the displayed mesh follows the traversal path and blends back to the corrected capsule. Gameplay collision still uses the capsule. Keep damage, overlaps and other gameplay checks tied to the intended collision representation.

## Extras and network spectators

Both Mover backends completed their earlier extras suites: slides, ragdoll/recovery, physical reactions and paired interactions. Chaos has also passed regression of the latest shared changes; the updated handover records an open NP first-person camera regression investigation. See [release progress](#final-release-scope). The shared setup wizard and final packaging remain. Use each backend's own integration; NP modes cannot substitute for Chaos modes.

For NP multiplayer spectators, the integration provides **ATraversalGaspNPSpectatorPawn**. Use the supported NP spectator path: Network Prediction needs an appropriate locally controlled NP pawn to correct remote players. Test spectator views as well as active players.
