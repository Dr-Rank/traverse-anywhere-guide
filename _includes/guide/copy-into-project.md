Setup has to change the pawn you keep: it adds a component, edits the Animation Blueprint and may add a bone to the skeleton. **Engine and plugin content is read-only**, so a pawn such as the engine's Mover examples cannot be set up where it is. Setup copies it into your project instead and works on the copy. **The original is never changed.**

There are two cases:

- **Keeping an engine or plugin pawn's locomotion:** setup copies the **pawn** (with everything it uses from its plugin). The button is **Copy into my project**.
- **Building a new pawn from an engine or plugin mesh** (in the wizard or in Full animation setup, including full GASP from an existing pawn): setup copies the **mesh**, with its skeleton and the assets it uses. Traversal adds an 'attach' bone to that skeleton, and the generated animation library is built on it, so it has to be in your project before the new pawn is made. The button is **Copy mesh into my project**, and Preview, Prepare and the wizard's Next wait for it.

## Find the engine example pawns

1. Enable the **Mover Examples** plugin (**Edit > Plugins**) and restart.
2. In the Content Browser, open **Settings** and turn on **Show Engine Content** and **Show Plugin Content**. The pawns are in `/MoverExamples/Pawns`: `AnimatedMannyPawn` (Network Prediction Mover) and `ChaosMannyPawn` (Chaos Mover).
3. In setup's own pawn picker, open the picker's settings (the cog beside its search box) and tick **Engine Content** and **Plugin Content**. The Mover examples come from an engine plugin, so **Plugin Content alone is not enough**.

![The pawn picker's settings with Engine Content and Plugin Content ticked](assets/images/copy-00-picker-engine-content.webp)

## Copy the pawn or mesh

In the wizard (step 3) or in the setup window, an engine or plugin pawn or mesh shows an amber note and a copy button. The wizard keeps **Next** locked, and Full animation setup keeps **Preview** and **Prepare** greyed out, until the copy exists.

<div class="shots"><figure><img src="assets/images/copy-01-wizard-copy-button.webp" alt="Wizard step 3 asking to copy an engine pawn" width="1000" height="737" loading="lazy"><figcaption><strong>Before.</strong> The wizard explains why a copy is needed and what Unreal will show while it copies.</figcaption></figure><figure><img src="assets/images/copy-02-wizard-copied.webp" alt="Wizard step 3 after the copy" width="1000" height="636" loading="lazy"><figcaption><strong>After.</strong> ChaosMannyPawn and the 52 assets it uses were copied. Next is unlocked and setup continues with the copy.</figcaption></figure></div>

![The same option in step 1 of the setup window](assets/images/copy-03-main-window.webp)

<div class="shots"><figure><img src="assets/images/wizard-03b-new-pawn-mesh.webp" alt="Wizard step 3 asking to copy an engine mesh" width="1000" height="782" loading="lazy"><figcaption><strong>A new pawn from an engine mesh.</strong> The Mover examples' SKM_Manny_Simple must be copied before the new pawn is built.</figcaption></figure><figure><img src="assets/images/copy-05-wizard-mesh-copied.webp" alt="Wizard step 3 after copying the mesh" width="1000" height="666" loading="lazy"><figcaption><strong>After.</strong> The mesh and the 25 assets it uses were copied; the new pawn will be built on the copy.</figcaption></figure></div>

## What the copy contains

- The pawn and **every asset it uses from its own plugin**: its Animation Blueprint, mesh, skeleton, physics asset, materials, textures, input actions and so on.
- They go into `/Game/TraverseAnywhere/EngineCopies/<Plugin>/<Pawn or mesh>/`, for example `/Game/TraverseAnywhere/EngineCopies/MoverExamples/ChaosMannyPawn/`. Each copied asset gets its own folder, so copying a second pawn or mesh from the same plugin never touches the first copy.
- Picking an engine mesh that you already copied uses the copy automatically, and says so.
- References inside the copies are pointed at the copies, and everything is **saved**.
- Copying the same pawn or mesh again **reuses** the existing copy and says *Using the copy already in your project*.
- Engine-wide assets outside that plugin (engine materials, for example) are referenced, not copied.

After the copy, the checks that said *engine content* become ordinary **Action needed** rows with **Apply** buttons.

## What Unreal shows while it copies

Unreal checks the copies as it saves them. **This is normal and does not mean the copy failed.**

![The Message Log Unreal opens during a copy](assets/images/copy-04-message-log.webp)

- The **Message Log** opens on **Asset Check** and lists every copied asset (*Validating asset*). **Asset Tools** lists them too.
- You may see messages that a skeleton *does not match bound ControlRigObject*. They come from Unreal duplicating animation sequences and do not appear when the copies are loaded again.
- For the Chaos Mover example, one warning says an actor using a **ChaosPathedMovementMode** must have a primitive root component. Epic's original sample produces it too.

You can close the Message Log. The copied pawn loads and works normally.

## Use your copy

Set the copied pawn as your GameMode's **Default Pawn Class**, or place it in your test level, and play with it rather than the original.
