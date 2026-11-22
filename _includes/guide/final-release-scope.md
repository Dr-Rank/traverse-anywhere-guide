**Tester edition · November 2026 · Unreal Engine 5.8**

This guide describes the current tester build. Everything below is in that build unless it is marked **Not in this build**. Tell us when something does not match what you see.

## In this build

| Area | What you get |
| --- | --- |
| Traversal and objects | Hurdles, vaults, mantles and climbs up to 300 cm; automatic ledge queries; moving objects; one-click **Make Traversable**, fitted proxies and pawn collision, filters, level conversion tools and editor diagnostics. |
| Four movement systems | **CMC, GMC, Network Prediction Mover and Chaos Mover**, each with its own native integration. |
| Setup | The [setup window](#setup-window), the [guided setup wizard](#use-the-setup-wizard), per-row checks and fixes, and [copying engine example pawns](#copy-into-project) into your project. |
| Full animation setup | A generated pawn per backend with GASP locomotion, motion matching, pose history, choosers, Pose Search databases, mirroring and warping, prepared with **offline retargeting, no dynamic runtime retargeting**. |
| Supported skeletons | UE5 Manny and Quinn, UE4 Mannequin, UEFN Mannequin, and male and female Animan. |
| Slides | Requested slope slide, automatic steep-slope slide and flat crouch slide, with entry, loop and exit animation, on all four backends. |
| Ragdoll and recovery | Active ragdoll, knockdown, physical and motion-matched get-up, and death ragdolls. |
| Physical reactions | Physics Control hit reactions without a full knockdown, and injury-dependent strength. |
| Paired interactions | Shove, tackle and takedown with participant coordination and return of control. |
| Your own animations | [Retarget your own Animation Sequences and Montages](#retarget-your-own-animations) onto another supported skeleton with the same corrections the imports use, offline. |
| First person | An owner-only body, a steady camera that follows the head through traversal, slides, reactions, ragdoll and get-up, configurable look limits, and [Blueprint camera functions](#first-person-camera-blueprint). |
| Multiplayer | Traversal and the extras replicate for the server, the owning player and remote observers. |

## How it was tested

Each backend's extras pass our automated gameplay suites in the editor: slides, knockdown and get-up, every injury type, hit reactions, shove, tackle and takedown, first-person views, and networked server, owner and observer views, including runs with simulated lag and packet loss. The setup window and wizard have their own automated tests.

**That does not prove your project.** Your own pawn, input, animation, movement settings and gameplay code can behave differently. Back up first, test each feature in your own levels, and report what you find.

## Not in this build

| Item | Status |
| --- | --- |
| CMC slide body lean | CMC slides are animated, but do not yet lean the body into the slope the way the Mover slides do. |
| Mixed-backend paired interactions | Each backend's interactions are tested with two pawns of the same backend. CMC against GMC, or Mover against CMC, is not established. |

GASP assets come from your own, separately obtained Game Animation Sample project. All animation retargeting is offline.
