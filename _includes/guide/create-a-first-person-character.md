## Create the variant

Complete normal traversal setup first. Select the prepared character and choose **Create first-person variant**. The current verified generation route uses a CMC character. GMC fake first person support is included in the integration work, but its generated-pawn gameplay is still being qualified.

**Use Full GASP motion matching** is recommended and selected by default for responsive turn in place. Prepare the full animation library first and select its generated pawn. Otherwise, keep your existing traversal animation setup. Generation is unavailable during Play.

## Your view and other players' view

The generated child pawn has an owner-only fake first person body and a third person world mesh visible to other players. The owner body copies the world mesh's evaluated animation before its own view adjustments. This uses Copy Pose rather than shared Leader Pose buffers so its owner rig can adjust independently. The source pawn and source meshes are preserved.

## Camera and crouch

The camera stays steady during ordinary locomotion. During traversal, airborne motion, landing recovery and crouch it follows the animated head position and returns smoothly. Existing crouch input is retained; a missing binding is added. Check crouch, landing, looking down and equipped weapons in your game.

## First person action selection

The first person variant has its own chooser. The selected spinning and twisting hurdle/vault rows are excluded to keep the first person view comfortable. Its climb rows retain the **300 cm** ceiling. This does not remove those actions from an ordinary third person chooser. Check that your pawn actually uses the generated first person chooser if you still see a twisting action.

## Update old imports and variants

Finger retarget corrections are shared by traversal and Full GASP imports. Regenerate existing baked animation imports to receive them. Recreate older first person variants to receive their mesh-specific fingertip skin probes and owned rig changes. Test visible hands, fingers and feet on the selected mesh; a shared skeleton alone does not prove contact on every mesh.
