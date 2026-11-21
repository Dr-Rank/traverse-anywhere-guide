Choose this route for a prepared motion-matching animation library and a **new generated pawn** for your selected mesh. Your existing pawns are only read, never changed.

## True offline retargeting — no dynamic runtime retargeting

GASP & Traverse Anywhere prepares **retargeted animation assets for your chosen supported skeleton** during import. The generated character uses that target-skeleton library directly in game. It does not depend on **Retarget Pose From Mesh** to convert another skeleton's live animation pose every frame.

GASP's runtime character-retargeting workflow uses a source character to drive a different mesh dynamically; Epic's [GASP MetaHuman example](https://dev.epicgames.com/documentation/en-us/metahuman/runtime-retargeting#runtimeparentskeletalmeshretargetinginthegameanimationsampleproject) documents this approach. GASP & Traverse Anywhere instead prepares the assets for the target skeleton ahead of gameplay.

| | GASP runtime character-retargeting workflow | GASP & Traverse Anywhere generated setup |
| --- | --- | --- |
| When retargeting happens | During gameplay, from the source mesh's current pose. | During offline asset preparation. |
| What the target plays | A pose dynamically retargeted from another skeleton. | Animation assets prepared for its own skeleton. |
| Runtime cross-skeleton retarget layer | Used to drive the target mesh. | Not required by the generated setup. |

Motion matching, IK and motion warping still run during gameplay; they are separate from cross-skeleton retargeting.

## Prepare the library

In the setup window, set the **GASP project** folder in step 1, then expand **Full animation setup: create a new pawn**. The [guided setup](#use-the-setup-wizard) fills these in for you when you choose a new pawn.

1. Choose the movement system: **Character Movement (CMC)**, **Chaos Mover**, **NP Mover** or **GMC**. GMC needs its [separately purchased plugin](#prepare-a-gmc-project).
2. Choose the **Target skeletal mesh**: the mesh you want to see in game. If it is engine or plugin content (for example the Mover examples' `SKM_Manny_Simple`), press **Copy mesh into my project** first; the new pawn is built on the copy. See [the copy step](#copy-into-project).
3. Under **Extras for the new pawn (optional)**, tick only what your game needs: Slide, Ragdoll and get-up, Physical hit reactions, Paired interactions, Camera limits (first person). **Please choose carefully:** extras are built into the new pawn when it is created and cannot be added or removed later. If an extra cannot be generated for your choice, the reason appears in amber underneath.
4. **1. Preview changes** lists the source and destination without changing anything.
5. **2. Prepare animation library** retargets and verifies the library. It can take several minutes; the target and backend stay locked while it runs, and **Cancel preparation** stops it.
6. **3. Install verified library** becomes available once preparation is verified. It installs the library, the generated pawn and its GameMode.

![Full animation setup with extras ticked](assets/images/setup-window-plan.webp)

## Try it

1. Select the generated pawn in step 1 and apply its remaining checks.
2. Open your test map, set the generated **BP_GameMode** as the map's **GameMode Override** in **World Settings**, then press Play.

## What the library contains

Locomotion animations and the Animation Blueprint's supporting choosers, Pose Search data, mirroring and settings for the target, plus the animation states, input and physics assets for any extras you ticked.

Generated libraries are kept separate per target mesh, skeleton and backend under **Content/TraverseAnywhere/FullAnimation**. The preparation report gives the exact destination. An occupied destination is reported, not overwritten. Closing setup cancels an active preparation and keeps its logs.

A generated pawn is a starting point. Bring your own gameplay across deliberately and test it before replacing an existing character.
