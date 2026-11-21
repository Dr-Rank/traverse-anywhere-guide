## Two separate Mover choices

**Network Prediction Mover** and **Chaos Mover** are separate first-class routes alongside **CMC** and **GMC**. Both are offered in the wizard and in Full animation setup, with the same extras. Neither needs the paid GMC product.

For **Network Prediction Mover**, copy `Traversal`, `TraversalGaspExtras` and `TraversalMover`. For **Chaos Mover**, add `TraversalMoverChaos` as well. Each Mover plugin includes its own extras. Do not install older separate adapter plugins alongside them.

## Try the engine's example pawns

The engine's **Mover Examples** plugin includes `AnimatedMannyPawn` (Network Prediction) and `ChaosMannyPawn` (Chaos) in `/MoverExamples/Pawns`. They are engine content, so setup copies one into your project before changing it. See [Copy an engine pawn into your project](#copy-into-project).

## Select the actual pawn

Setup detects the pawn's backend and shows the rows that backend needs.

## Chaos Mover rows

| **Row** | **What to do** |
| --- | --- |
| Async physics | Apply the required physics and prediction settings. Follow any restart advice before multiplayer testing. |
| Stable physics playback | Supports steady playback with uneven frame times. It changes a project-wide setting, saves a backup and needs a restart. |
| Physics step rate | **Optional.** Read the trade-off before choosing a rate. Apply required changes leaves it alone. |
| Mesh tick group | **Optional.** Ticking the mesh after physics makes Chaos Mover's animation order match Network Prediction's. The row explains the cost. |
| Movement plugin | Enable the Chaos Mover integration and restart if it is not loaded. |
| Chaos startup input | Apply the supported backend fix. A custom backend may need a manual connection to keep its own behaviour. |

Save before changing project-wide physics settings. If a row stays blocked after a restart, read its reason: a platform configuration or a higher-priority override can change the effective setting.

## Network Prediction Mover rows

**NP fixed tick rate:** Network Prediction's fixed tick rate should divide 1000 exactly (for example 50, 100 or 125 Hz). Other rates run every Network Prediction simulation slightly slow; 60 Hz runs 4% slow. The row reports the actual slowdown and offers the change.

## Test in your game

Check approach, traversal and stopping at the frame rates you expect players to use. Test other players' views as well as the owning player. A custom Chaos pawn may need its braking tuned for a comfortable stop.

On remote Chaos pawns, the displayed mesh follows the traversal path and blends back to the corrected capsule. Gameplay collision still uses the capsule, so keep damage, overlaps and other gameplay checks on the intended collision.

**Chaos press distance:** on a networked Chaos pawn, a traversal press from too far away for the pawn to brake in time is refused before braking, and the press stays a normal jump. Press closer to the obstacle.

## Spectators on Network Prediction Mover

For NP multiplayer spectators, use **ATraversalGaspNPSpectatorPawn**. Network Prediction needs a suitable locally controlled NP pawn to correct remote players, so test spectator views as well as active players.
