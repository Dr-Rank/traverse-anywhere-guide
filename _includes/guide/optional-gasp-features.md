**Planned setup · all four movement systems**

The final **Full animation setup** workflow is planned to offer an **Optional GASP features** group for **CMC, GMC, Network Prediction Mover and Chaos Mover**. Extras are **opt-in and off by default**. Leaving them unticked is intended to preserve the existing generated output.

| Option | What it adds |
| --- | --- |
| Slide | Selectable slide triggers, native movement integration and slide animation states. |
| Ragdoll & get-ups | Knockdown, active ragdoll, pose-based recovery and the components needed to return control. |
| Physical hit reactions | PhysicsControl reactions and injury strength, usable without a full knockdown. |
| Interactions | Paired shove, tackle and takedown animations and participant coordination. |
| First-person camera limits | Limits during slides/knockdown, with restoration when normal control returns. Physical head following is covered in [first-person setup](#create-a-first-person-character). |

## Planned setup flow

1. Choose your movement system, target mesh and GASP source project.
2. Select only the extras your game needs and choose the slide trigger behaviour.
3. Resolve the prerequisite and physics-asset checks for that exact mesh.
4. Prepare and verify the animations and their supporting assets, then install the generated library and pawn.
5. Review input, animation and collision setup; test each selected feature in your map and network configuration.

Unavailable options should explain the missing dependency or unsupported setup. They must not silently switch your pawn to another movement system.

## Physics and animation preparation

The wizard is planned to check the physics bodies required by the selected control profile and map that profile to the target skeleton. Generating missing bodies is an **explicit optional choice**, not an automatic replacement of your physics asset.

Planned checks also cover the Ragdoll collision profile, Obstacle channel/preset and gameplay tags. Feature imports include get-up montages/choosers, injury and strength data, slide clips/curves, paired-interaction databases and required Foley assets.

The Animation Blueprint must have the corresponding ragdoll/get-up and slide states, montage playback and pose history. Copying animation files alone does not complete setup. Existing gameplay input, equipment and camera logic still need integration.
