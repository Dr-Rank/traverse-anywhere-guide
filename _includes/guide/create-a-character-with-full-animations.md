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

## Create the pawn in guided setup

1. Open **Tools > GASP & Traverse Anywhere**. Choose **Create a new pawn from a mesh**, select the skeletal mesh and choose a movement system.
2. On **Animation**, select the source Game Animation Sample project and the traversal style. Use **Copy mesh into my project** if setup asks for a writable copy.
3. On **View & Extras**, choose first or third person and the extras you want on the new pawn. First person also offers camera limits. To change the generated extras later, set up a new pawn.
4. On **Review your setup**, select **Set up my pawn**. Watch conversion, preparation and verification. Select **Install verified GASP library** when prompted. If Unreal asks you to restart, reopen the same project and choose **Continue setup**.

<div class="shots"><figure><a class="wizard-shot" href="assets/images/wizard-redesign-03-view-and-extras.webp"><img src="assets/images/wizard-redesign-03-view-and-extras.webp" alt="Current wizard View and Extras page showing a first-person pawn with all extras selected" width="1100" height="682" loading="lazy"></a><figcaption><strong>View &amp; Extras.</strong> Choose the view and extras before the wizard generates the pawn. Click or tap the screenshot for the full-size image.</figcaption></figure></div>

## Try the generated pawn

When **Guided setup is complete** appears, use **Open pawn** to inspect the Blueprint or **Open test level** to choose a map. For a quick playtest, select the generated **BP_GameMode** in the map’s **GameMode Override** in **World Settings**, then press Play.

## Run the steps manually

Open **Advanced tools** and expand **Full animation setup: create a new pawn**. Set the **GASP project**, select the movement system and saved target mesh, and choose the extras. Use **Preview changes**, **Prepare animation library** and **Install verified library** in that order. You can then select the generated pawn and run the remaining checks in Advanced tools. See [The setup window](#setup-window).

## What the library contains

Locomotion animations and the Animation Blueprint's supporting choosers, Pose Search data, mirroring and settings for the target, plus the animation states, input and physics assets for any extras you ticked.

Generated libraries are kept separate per target mesh, skeleton and backend under **Content/TraverseAnywhere/FullAnimation**. The preparation report gives the exact destination. An occupied destination is reported, not overwritten. Closing setup cancels an active preparation and keeps its logs.

A generated pawn is a starting point. Bring your own gameplay across deliberately and test it before replacing an existing character.
