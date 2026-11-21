GASP & Traverse Anywhere gives **Character Movement (CMC), GMC, Network Prediction Mover and Chaos Mover** equal standing. Choose the movement system your game uses: each has its own native integration, full animation setup, extras and first-person support.

<div class="notice dependency"><strong>GMC requires a separate purchase.</strong> General Movement Component (GMC) is a paid third-party product. You must purchase a compatible GMC version and install and enable it before GASP & Traverse Anywhere can work with GMC. GMC is not included with GASP & Traverse Anywhere. The other three movement routes do not require GMC.</div>

| Movement system | Choose it for | Plugins and requirements |
| --- | --- | --- |
| **Character Movement (CMC)** | Unreal's standard Character movement. **The simplest choice if you are unsure.** | `Traversal`, plus `TraversalGaspExtras` and `TraversalCMCExtras` for the extras. |
| **GMC** | A project built around General Movement Component | The separately purchased **GMC**, plus **GMCMotion** and **GMCAbilitySystem (GMAS)**; `TraversalGMC` and `TraversalGMCExtras`. See [GMC setup](#prepare-a-gmc-project). |
| **Network Prediction Mover** | A Mover pawn using Network Prediction | The engine's Mover and Network Prediction; `TraversalMover`, plus `TraversalMoverExtras` for the extras. |
| **Chaos Mover** | A Mover pawn using Chaos physics | The engine's Mover and Chaos Mover; `TraversalMoverChaos`, plus `TraversalMoverExtras`. Setup also applies the physics settings it needs. |

**Network Prediction Mover and Chaos Mover are separate choices.** Their movement, prediction and physics requirements differ, and choosing one does not install the other as a fallback. Mover is still marked experimental by Epic in Unreal Engine 5.8.

## Same features, native movement underneath

All four routes support traversal, full GASP animation setup, the optional extras and first person. The same feature does not mean identical physics or network timing: your movement system stays in charge of movement and prediction, so stopping distances, slide run-outs and correction behaviour differ between backends.

Use [existing-character setup](#set-up-an-existing-character) to keep your locomotion, or [full animation setup](#create-a-character-with-full-animations) for a generated character. An existing pawn always keeps its movement system; setup never swaps it.
