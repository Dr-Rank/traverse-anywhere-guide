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

Enable **MovieSceneAnimMixer** and **Mover** in **Edit > Plugins** before starting full GASP setup. If the wizard flags a missing plugin, enable it and restart the editor. This also applies when the animation library is already installed. See [Full GASP dependencies](#full-gasp-dependencies).

1. Open **Tools > GASP & Traverse Anywhere**. Choose **Create a new pawn from a mesh**, select the skeletal mesh and choose a movement system.
2. On **Animation**, select the source Game Animation Sample project and the traversal style. Use **Copy mesh into my project** if setup asks for a writable copy.
3. On **View & Extras**, choose first or third person and the extras you want on the new pawn. First person also offers camera limits. To change the generated extras later, set up a new pawn.
4. On **Review your setup**, select **Set up my pawn**. Watch conversion, preparation and verification. Select **Install verified GASP library** when prompted. If Unreal asks you to restart, reopen the same project and choose **Continue setup**.

<div class="shots"><figure><a class="wizard-shot" href="assets/images/wizard-redesign-03-view-and-extras.webp"><img src="assets/images/wizard-redesign-03-view-and-extras.webp" alt="Current wizard View and Extras page showing a first-person pawn with all extras selected" width="1100" height="682" loading="lazy"></a><figcaption><strong>View &amp; Extras.</strong> Choose the view and extras before the wizard generates the pawn. Click or tap the screenshot for the full-size image.</figcaption></figure></div>

## Use a MetaHuman from the Game Animation Sample

Start with **Kellan**, the sample MetaHuman. In the Content Browser, find the **Skeletal Mesh** named `m_med_nrw_body` under `MetaHumans/Kellan/Male/Medium/NormalWeight/Body`. Use this body mesh as the wizard's target. Epic's sample pawn Blueprint uses its own animation setup. [Epic's GASP MetaHuman guide](https://dev.epicgames.com/documentation/unreal-engine/adding-a-metahuman-to-the-game-animation-sample-project-in-unreal-engine?application_version=5.8)

1. If you are working in another project, right-click the body mesh in the sample's Content Browser and choose **Asset Actions > Migrate**. Keep its dependencies selected and choose the destination project's **Content** folder. If you are setting up within the sample project, select the mesh there. [Epic's asset migration guide](https://dev.epicgames.com/documentation/en-us/unreal-engine/migrating-assets-in-unreal-engine)
2. In the TA wizard, choose **Create a new pawn from a mesh**, select that body mesh, and choose **Full GASP motion matching** on the Animation page. The wizard identifies the MetaHuman body and bakes the animations in the editor. It creates owned compatibility assets when the body needs IK foot helpers or a compatible physics asset.
3. Choose your movement system and **First person** or **Third person**. Choose the extras you want, install the verified library, and play using the generated pawn.

Packaged first-person gameplay checks covered Kellan on CMC and General Movement Component (GMC), and a second imported MetaHuman body on CMC. The CMC body-motion and camera review also passed.

### Create and assemble your own MetaHuman

You can also start with a custom body, face, outfit and hair from MetaHuman Creator.

1. Enable **MetaHuman Creator** under **Edit > Plugins**, restart if prompted, and check that your Unreal installation includes the Creator Core Data. In the Content Browser, right-click an empty area and choose **MetaHuman > MetaHuman Character**. Open the character asset, choose a preset and customize it. [Epic's MetaHuman project requirements](https://dev.epicgames.com/documentation/metahuman/requirements-and-configuration-settings-for-metahumans-in-unreal-engine)
2. In **MetaHuman Creator**, select **Download Texture Sources** and **Create Full Rig**. Open **Assembly**, choose **UE Optimized** for a gameplay pawn, use the **AnimBP** output if the choice is shown, and click **Assemble**. Save the generated assets. [Epic's character creation guide](https://dev.epicgames.com/documentation/metahuman/creating-a-metahuman-character-in-unreal-engine?application_version=5.8) · [Epic's assembly options](https://dev.epicgames.com/documentation/metahuman/assembly?application_version=5.8)
3. Open the resulting MetaHuman Blueprint and find its **Body** Skeletal Mesh. Select that mesh in the TA wizard with **Full GASP motion matching**. Once the wizard creates your playable pawn, use the assembled Blueprint as the donor for the outfit, face and hair in the steps below.

### Assemble the complete MetaHuman pawn

Use the assembled MetaHuman Blueprint as the template for the render components, materials and attachments. For GASP's example, open `BP_Kellan` and inspect its **Face**, **Torso**, **Legs**, **Feet**, groom components and **LODSync**. If you are moving Kellan to another project and want the complete appearance, migrate `BP_Kellan` with its dependencies so the face, clothing, groom bindings and materials arrive together. Enable the engine plugins that the imported assets require before opening the Blueprint. [Epic's GASP MetaHuman assembly example](https://dev.epicgames.com/documentation/unreal-engine/adding-a-metahuman-to-the-game-animation-sample-project-in-unreal-engine?application_version=5.8) · [MetaHuman project requirements](https://dev.epicgames.com/documentation/metahuman/requirements-and-configuration-settings-for-metahumans-in-unreal-engine)

1. **Start from the TA pawn.** Create a child Blueprint of the pawn the wizard finished installing. If you chose first person, use the generated first-person pawn as the parent. Keep the inherited movement component, capsule, body mesh, Animation Blueprint and camera. The inherited body mesh drives the baked animations and physics.
2. **Add the outfit.** Add the matching Torso, Legs and Feet Skeletal Mesh Components under the inherited body mesh. Assign their assets and material overrides from `BP_Kellan`. Check the relative transforms against the donor in the Blueprint viewport. Disable collision and overlap generation on the outfit pieces. In the Construction Script, keep the parent construction call and use **Set Leader Pose Component** on each outfit piece, with the inherited body mesh as the leader. The garments then follow the same pose during traversal, ragdoll and recovery. [Epic's modular character guide](https://dev.epicgames.com/documentation/unreal-engine/working-with-modular-characters-in-unreal-engine)
3. **Add the face and grooms.** Parent the Face Skeletal Mesh Component to the inherited body mesh and disable its collision. Use the donor's face mesh, face Animation Blueprint and face post-process settings so the face can follow the body and evaluate its own facial rig. In the face Animation Blueprint, check that its body pose source resolves to the inherited mesh, for example through **Use Attached Parent** on **Copy Pose From Mesh**. Attach the groom components to the face using the donor's groom assets, bindings and relative transforms. If your donor has a **MetaHuman Component**, carry across its face and body settings and check that its component references point at the new pawn. [Epic's MetaHuman assembly example](https://dev.epicgames.com/documentation/unreal-engine/adding-a-metahuman-to-the-game-animation-sample-project-in-unreal-engine?application_version=5.8) · [MetaHuman Component](https://dev.epicgames.com/documentation/metahuman/the-metahuman-component-for-unreal-engine)
4. **Sync the appearance.** Copy the donor's **LODSync** settings and update its component list to use the names on the new pawn. Check the face, grooms and clothing at several camera distances. For first person, set **Owner No See** on the world face and grooms if they obstruct the local view. Keep the generated first-person body. For visible first-person clothing, use separate **Only Owner See** garment components and set their leader to **Owner Body** on the TA first-person presentation component once that reference is valid. Set **Owner No See** on the corresponding world garments so the local camera sees one outfit. [Epic's LODSync guide](https://dev.epicgames.com/documentation/metahuman/lodsync-component-for-unreal-engine?application_version=5.8)
5. **Play as the assembled pawn.** Compile and save the child Blueprint. Create a child of the generated **BP_GameMode** and set its **Default Pawn Class** to the assembled pawn. Select that GameMode in the test map's **World Settings > GameMode Override**, add a **Player Start**, and press Play. Check the camera, limbs, outfit and neck while jumping, traversing and using the enabled extras. Test a packaged build and check the assembled pawn from another player's view if your project is multiplayer.

## Try the generated pawn

When **Guided setup is complete** appears, use **Open pawn** to inspect the Blueprint or **Open test level** to choose a map. For a quick playtest, select the generated **BP_GameMode** in the map’s **GameMode Override** in **World Settings**, then press Play.

## Run the steps manually

Open **Advanced tools** and expand **Full animation setup: create a new pawn**. Set the **GASP project**, select the movement system and saved target mesh, and choose the extras. Use **Preview changes**, **Prepare animation library** and **Install verified library** in that order. You can then select the generated pawn and run the remaining checks in Advanced tools. See [The setup window](#setup-window).

## What the library contains

Locomotion animations and the Animation Blueprint's supporting choosers, Pose Search data, mirroring and settings for the target, plus the animation states, input and physics assets for any extras you ticked.

Generated libraries are kept separate per target mesh, skeleton and backend under **Content/TraverseAnywhere/FullAnimation**. The preparation report gives the exact destination. An occupied destination is reported, not overwritten. Closing setup cancels an active preparation and keeps its logs.

A generated pawn is a starting point. Bring your own gameplay across deliberately and test it before replacing an existing character.
