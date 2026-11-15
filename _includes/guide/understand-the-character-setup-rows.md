You do not need to build these pieces by hand when the setup can fix them. This is what the main rows prepare.

| **Row** | **What it is for** |
| --- | --- |
| Traversable trace channel | Lets your pawn find traversable objects without interfering with other collision channels. |
| attach bone | Provides an animation reference point. The confirmation identifies the shared skeleton affected. |
| Traversal animations | Imports and bakes the traversal clips for the selected character. |
| Traversal Action component | Adds the character's traversal logic. |
| Jump input | Tries traversal when you press jump; otherwise uses the character's normal jump. Custom input graphs may need manual wiring. |
| Pose History | Helps select an animation that fits the character's current pose. |
| Chooser | Selects a suitable traversal animation for the obstacle and approach. |
| Montage slot | Connects traversal playback to the Animation Blueprint's output. |
| Foot IK while traversing | Stops ordinary floor IK from pulling the feet out of the traversal pose. |
| In-air pose while traversing | Prevents flying or airborne movement flags from selecting an unwanted animation pose during traversal. |
| Foot clearance against obstacles | Helps keep the legs clear of supported obstacle collision. |
| GASP level blocks | Adds the Traversable component to recognized sample level-block Blueprints already in your project. |

Movement-specific requirements are explained under [Choose your movement system](#choose-your-movement-system), [GMC setup](#prepare-a-gmc-project) and [Use Mover](#use-mover). A row can give manual guidance when your Blueprint differs from the supported automatic setup.

## Planned optional-feature checks

The final wizard is also planned to check the selected extras adapter, physics bodies/control profile, Ragdoll collision, Obstacle channel/preset, gameplay tags, feature animations, animation states and input bindings. Missing physics bodies are offered as an **optional** generation step.

GMC prerequisite checks require the separately purchased GMC product plus GMCMotion and GMAS; the other backends do not inherit those dependencies. See [Optional GASP features](#optional-gasp-features) for the planned flow.
