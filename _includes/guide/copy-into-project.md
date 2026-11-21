Setup has to change the pawn you keep: it adds a component, edits the Animation Blueprint and may add a bone to the skeleton. **Engine and plugin content is read-only**, so a pawn such as the engine's Mover examples cannot be set up where it is. Setup copies it into your project instead and works on the copy. **The original is never changed.**

You only need this when you **keep** an engine or plugin pawn's locomotion. Full GASP motion matching and new pawns only read the source, so they need no copy.

## Find the engine example pawns

1. Enable the **Mover Examples** plugin (**Edit > Plugins**) and restart.
2. In the Content Browser, open **Settings** and turn on **Show Engine Content** and **Show Plugin Content**. The pawns are in `/MoverExamples/Pawns`: `AnimatedMannyPawn` (Network Prediction Mover) and `ChaosMannyPawn` (Chaos Mover).
3. In setup's own pawn picker, open the picker's settings (the cog beside its search box) and tick **Engine Content** and **Plugin Content**. The Mover examples come from an engine plugin, so **Plugin Content alone is not enough**.

![The pawn picker's settings with Engine Content and Plugin Content ticked](assets/images/copy-00-picker-engine-content.webp)

## Copy the pawn

In the wizard (step 3, keeping your locomotion) or in step 1 of the setup window, an engine or plugin pawn shows an amber note and a **Copy into my project** button. The wizard keeps **Next** locked until the copy exists.

<div class="shots"><figure><img src="assets/images/copy-01-wizard-copy-button.webp" alt="Wizard step 3 asking to copy an engine pawn" width="1000" height="737" loading="lazy"><figcaption><strong>Before.</strong> The wizard explains why a copy is needed and what Unreal will show while it copies.</figcaption></figure><figure><img src="assets/images/copy-02-wizard-copied.webp" alt="Wizard step 3 after the copy" width="1000" height="636" loading="lazy"><figcaption><strong>After.</strong> ChaosMannyPawn and the 52 assets it uses were copied. Next is unlocked and setup continues with the copy.</figcaption></figure></div>

![The same option in step 1 of the setup window](assets/images/copy-03-main-window.webp)

## What the copy contains

- The pawn and **every asset it uses from its own plugin**: its Animation Blueprint, mesh, skeleton, physics asset, materials, textures, input actions and so on.
- They go into `/Game/TraverseAnywhere/EngineCopies/<Plugin>/<Pawn>/`, for example `/Game/TraverseAnywhere/EngineCopies/MoverExamples/ChaosMannyPawn/`. Each pawn gets its own folder, so copying a second pawn from the same plugin never touches the first copy.
- References inside the copies are pointed at the copies, and everything is **saved**.
- Copying the same pawn again **reuses** the existing copy and says *Using the copy already in your project*.
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
