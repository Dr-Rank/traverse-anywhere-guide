## Create the variant

First person works on **CMC, GMC, Network Prediction Mover and Chaos Mover**. Select **First person** on **View and extras** in [guided setup](#use-the-setup-wizard) to create the variant automatically. Use the steps below to create one later from **Advanced tools**.

1. Complete the pawn's traversal setup first. **Full GASP motion matching is recommended**, because it includes responsive turn in place: prepare it, install it, and select its generated pawn.
2. In the setup window's **First-person variant** section, press **Create first-person variant**. Generation is unavailable during Play.
3. Set the new variant as your GameMode's **Default Pawn Class**, then test your level.

Your selected pawn is kept as it is; the variant is a separate child Blueprint.

**With your own locomotion, turn in place is your responsibility.** The full GASP route includes it. With your own locomotion you implement and manage turning in place yourself.

## Your view and other players' view

The variant has an **owner-only first-person body** and a **third-person world mesh** that other players see. The owner body copies the world mesh's evaluated animation before its own view adjustments (Copy Pose rather than shared Leader Pose buffers, so the owner rig can adjust independently) and hides its head. The source pawn and its meshes are preserved.

## Camera

A steady camera is created for the local player. It stays steady during ordinary locomotion, and during traversal, airborne motion, landing and crouch it follows the animated head, then returns smoothly. With the extras it also follows the head through **slides, hit reactions, ragdoll and getting up**, and turns the view toward the get-up direction.

Built-in limits keep a headless body from showing itself: the player cannot look further down than **65°** below level, and while the head is physically followed the view stays in a window around the head. Your own gameplay can use the same head follow and add its own limits with the [first-person camera functions](#first-person-camera-blueprint), which also lists the settings you can tune.

Existing crouch input is kept; a crouch binding is added only if your pawn has none.

## First-person action selection

The variant uses its own chooser. Spinning and twisting hurdle and vault rows are left out to keep the first-person view comfortable; climbs keep the **300 cm** ceiling. The third-person chooser is unchanged. If you still see a twisting action in first person, check that the pawn really uses the generated first-person chooser.

## Update old imports and variants

Finger retarget corrections are shared by the traversal and full GASP imports: re-import existing baked animations to receive them. Recreate older first-person variants to receive their mesh-specific fingertip probes and rig changes. Check visible hands, fingers and feet on the mesh you ship; a shared skeleton alone does not prove contact on every mesh.
