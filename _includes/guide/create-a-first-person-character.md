## Create the variant

Complete normal traversal setup first. Select the prepared character and choose **Create first-person variant**. The final-release plan covers **CMC, GMC, Network Prediction Mover and Chaos Mover**. CMC was the earlier verified generation route; do not treat an older build's menu as the final backend scope. The shared wizard and final generated-pawn checks remain in progress. **GMC needs a separately purchased and installed paid GMC plugin**, plus its [prerequisites](#prepare-a-gmc-project).

**Use Full GASP motion matching** is recommended and selected by default for responsive turn in place. Prepare the full animation library first and select its generated pawn. Otherwise, keep your existing traversal animation setup. Generation is unavailable during Play.

## Your view and other players' view

The generated child pawn has an owner-only fake first person body and a third person world mesh visible to other players. The owner body copies the world mesh's evaluated animation before its own view adjustments. This uses Copy Pose rather than shared Leader Pose buffers so its owner rig can adjust independently. The source pawn and source meshes are preserved.

## Camera and crouch

The camera stays steady during ordinary locomotion. During traversal, airborne motion, landing recovery and crouch it follows the animated head position and returns smoothly. Existing crouch input is retained; a missing binding is added. Check crouch, landing, looking down and equipped weapons in your game.

## Slides and physical motion

The planned extras extend head following to **slides, physical hit reactions without knockdown, ragdoll and getting up**. The camera follows the actual animated or physics-driven head, then returns smoothly to normal locomotion. Get-up alignment turns the view toward the recovery direction.

Configurable slide/knockdown look limits must restore on exit and affect only the local player. Test looking down, head/body visibility, camera collision and equipment through each enabled state. These additions are part of the [final-release plan](#final-release-scope), not a claim that every generated variant is already qualified.

## First person action selection

The first person variant has its own chooser. The selected spinning and twisting hurdle/vault rows are excluded to keep the first person view comfortable. Its climb rows retain the **300 cm** ceiling. This does not remove those actions from an ordinary third person chooser. Check that your pawn actually uses the generated first person chooser if you still see a twisting action.

## Update old imports and variants

Finger retarget corrections are shared by traversal and Full GASP imports. Regenerate existing baked animation imports to receive them. Recreate older first person variants to receive their mesh-specific fingertip skin probes and owned rig changes. Test visible hands, fingers and feet on the selected mesh; a shared skeleton alone does not prove contact on every mesh.
