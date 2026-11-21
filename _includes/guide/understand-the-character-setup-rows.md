You do not need to build these pieces by hand when setup can apply them. This is what the main rows prepare.

| **Row** | **What it is for** |
| --- | --- |
| Traversable trace channel | Lets your pawn find traversable objects without interfering with other collision channels. |
| 'attach' bone | An animation reference bone the traversal clips need on the target mesh. The confirmation names the shared skeleton affected. |
| Traversal animations | Imports and bakes the traversal clips for the selected character. |
| Traversal Action component | Adds the character's traversal logic. Its movement adapter is picked automatically at runtime. |
| Jump input | Tries traversal when you press jump; otherwise uses the character's normal jump. Custom input graphs may need manual wiring. |
| Pose History | Links the pose history the chooser uses to pick an animation that fits the current pose. |
| Chooser | Selects a suitable traversal animation for the obstacle and approach. |
| Montage slot | Connects traversal playback to the Animation Blueprint's output. |
| Foot IK while traversing | Stops ordinary floor IK from pulling the feet out of the traversal pose. |
| In-air pose while traversing | Prevents flying or airborne movement flags from selecting an unwanted pose during traversal. |
| Foot clearance against obstacles | Helps keep the legs clear of supported obstacle collision. |
| GASP level blocks | Adds the Traversable component to recognised Game Animation Sample level-block Blueprints already in your project. |

Movement-specific rows appear only for the backend that needs them: physics and startup rows for Chaos Mover, a fixed-tick-rate row for Network Prediction Mover, and prerequisite rows for GMC. See [Use Mover](#use-mover) and [GMC setup](#prepare-a-gmc-project).

A row gives manual guidance (**Info**) when your Blueprint differs from what setup can change automatically, and **Needs attention** when something else must happen first. Its text always says what.
