Setup has to change the pawn you keep: it adds a component, edits the Animation Blueprint and may add a bone to the skeleton. **Engine and plugin content is read-only**, so a pawn such as the engine's Mover examples cannot be set up where it is. Setup copies it into your project instead and works on the copy. **The original is never changed.**

There are two cases:

- **Keeping an engine or plugin pawn's locomotion:** setup copies the **pawn** (with everything it uses from its plugin). The button is **Copy into my project**.
- **Building a new pawn from an engine or plugin mesh** (in the wizard or in Full animation setup, including full GASP from an existing pawn): setup copies the **mesh**, with its skeleton and the assets it uses. Traversal adds an 'attach' bone to that skeleton, and the generated animation library is built on it, so it has to be in your project before the new pawn is made. The button is **Copy mesh into my project**, and Preview, Prepare and the wizard's **Continue** action wait for it.

## Find the engine example pawns

1. Enable your Traverse Anywhere Mover plugin (**Edit > Plugins**) and restart. Unreal enables **Mover Examples** automatically.
2. In the Content Browser, open **Settings** and turn on **Show Engine Content** and **Show Plugin Content**. The pawns are in `/MoverExamples/Pawns`: `AnimatedMannyPawn` (Network Prediction Mover) and `ChaosMannyPawn` (Chaos Mover).
3. In setup's own pawn picker, open the picker's settings (the cog beside its search box) and tick **Engine Content** and **Plugin Content**. The Mover examples come from an engine plugin, so **Plugin Content alone is not enough**.

![The pawn picker's settings with Engine Content and Plugin Content ticked](assets/images/copy-00-picker-engine-content.webp)

## Copy the pawn or mesh

The wizard offers **Copy into my project** on **Your pawn** for an engine or plugin selection. When you use full GASP from an existing pawn, **Animation** can also offer **Copy mesh into my project**. Select the copy to continue setup. The [Pawn screenshot](#setup-wizard-screens-1) shows the asset picker with a project-owned mesh selected.

## What the copy contains

- The pawn and **every asset it uses from its own plugin**: its Animation Blueprint, mesh, skeleton, physics asset, materials, textures, input actions and so on.
- They go into `/Game/TraverseAnywhere/EngineCopies/<Plugin>/<Pawn or mesh>/`, for example `/Game/TraverseAnywhere/EngineCopies/MoverExamples/ChaosMannyPawn/`. Each copied asset gets its own folder, so copying a second pawn or mesh from the same plugin never touches the first copy.
- Picking an engine mesh that you already copied uses the copy automatically, and says so.
- References inside the copies are pointed at the copies, and everything is **saved**.
- Copying the same pawn or mesh again **reuses** the existing copy and says *Using the copy already in your project*.
- Engine-wide assets outside that plugin (engine materials, for example) are referenced, not copied.

After the copy, continue in the wizard. If you use Advanced tools, the individual checks are available there.

## What Unreal shows while it copies

Unreal checks the copies as it saves them. **This is normal and does not mean the copy failed.**

![The Message Log Unreal opens during a copy](assets/images/copy-04-message-log.webp)

- The **Message Log** opens on **Asset Check** and lists every copied asset (*Validating asset*). **Asset Tools** lists them too.
- You may see messages that a skeleton *does not match bound ControlRigObject*. They come from Unreal duplicating animation sequences and do not appear when the copies are loaded again.
- For the Chaos Mover example, one warning says an actor using a **ChaosPathedMovementMode** must have a primitive root component. Epic's original sample produces it too.

You can close the Message Log. The copied pawn loads and works normally.

## Use your copy

Set the copied pawn as your GameMode's **Default Pawn Class**, or place it in your test level, and play with it rather than the original.
