Use this route to add traversal while keeping your current walking, running and idle animations.

In the [setup wizard](#use-the-setup-wizard), choose **I have a pawn** and then **Keep my locomotion and add traversal**. The steps below describe the manual route in **Advanced tools**.

## Choose your pawn

1. Open the [setup window](#setup-window) and pick the **Pawn Blueprint** your game uses in step 1. Check the mesh, skeleton and Animation Blueprint shown underneath.
2. If the pawn is engine or plugin content, press **Copy into my project** first. See [Copy an engine pawn into your project](#copy-into-project).
3. Set the **GASP project** folder. The traversal clips are imported from it.
4. Leave **Use Relaxed traversal animations** off for the default Neutral style, or tick it for Relaxed.

Setup detects the pawn's movement system (CMC, GMC, Network Prediction Mover or Chaos Mover) and only shows the checks relevant to it. **GMC needs its separately purchased plugin** plus GMCMotion and GMAS; see [GMC prerequisites](#prepare-a-gmc-project).

Keeping your locomotion does not add the extras (slides, ragdoll, reactions, interactions, camera limits). They are built into a **new** pawn by [full animation setup](#create-a-character-with-full-animations).

## Apply the checks

Work through section **02** from the top. Read each row, then press its **Apply**, or press **Apply required changes** to apply every required row at once (optional rows are skipped). Read any confirmation carefully, especially when a shared skeleton will change. Press **Check again** after changing something yourself.

Rows depend on one another: for example, *Jump input* and *Chooser* wait for the *Traversal Action component*. Applying the earlier rows unlocks the later ones. See [The setup window](#setup-window) for what each label means and [the setup rows](#understand-the-character-setup-rows) for what each row prepares.

When everything reads **Ready**, save (**File > Save All**) and press Play.

## Custom graphs

A custom jump graph or animation rig may need a small manual connection. The row says what to connect; follow it instead of replacing your whole graph. Start with a simple test level before integrating traversal into a larger gameplay system.
