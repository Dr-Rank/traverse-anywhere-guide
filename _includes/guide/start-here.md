**GASP & Traverse Anywhere** brings together character animation, traversal and physical interaction for Unreal Engine 5.8.

**First or Third Person. Your Choice of Supported Skeleton.**

**True offline retargeting. No dynamic runtime retargeting.** The prepared animation library targets your chosen supported skeleton directly, so the character plays its own retargeted assets in game. [How the full animation setup works](#create-a-character-with-full-animations).

Choose **CMC, GMC, Network Prediction Mover or Chaos Mover**. The editor also uses the shorter name **Traverse Anywhere**, for example on its window tab.

Prepare your character, then right-click a static mesh and choose **Make Traversable**. GASP & Traverse Anywhere creates the Blueprint, adds traversal and generates its proxies for you. Drag the new Blueprint into your level and try it.

<div class="notice dependency"><strong>GMC is a paid third-party product.</strong> Purchase, install and enable it separately to use the GMC route. It is not included with GASP & Traverse Anywhere. The other three movement routes do not need it. See <a href="#prepare-a-gmc-project">GMC setup</a>.</div>

## Before making changes

**Back up your project.** Make a source-control commit or a complete project copy before running setup or importing animations. Setup can change shared skeletons, Animation Blueprints and project settings, and your own input, animation, movement and gameplay code may react differently. Test on a copy first. Unreal's Undo is not a replacement for a backup.

## Install

1. Use Unreal Engine **5.8** (tested on 5.8.4) with its C++ toolchain (Visual Studio 2022). The plugins are source plugins and compile into your project.

2. Copy the plugins into your project's **Plugins** folder. There are five, all listed under one **Traverse Anywhere** category in **Edit > Plugins**. **Always copy `Traversal` and `TraversalGaspExtras`**, then add the plugin for your movement system:

   | Plugin folder | Name in Edit > Plugins | What it adds | When you need it |
   | --- | --- | --- | --- |
   | `Traversal` | GASP & Traverse Anywhere | Traversable objects, ledge detection, traversal for Character Movement (CMC), the setup window and wizard, GASP import, first-person presentation | Always |
   | `TraversalGaspExtras` | Traverse Anywhere - GASP Extras | Ragdoll and get-up, hit reactions, injuries, paired interactions and slides, shared by every movement system, with Character Movement support built in | Always (Mover and GMC need it even without extras) |
   | `TraversalMover` | Traverse Anywhere - Mover | Network Prediction Mover, including its extras | NP Mover, and Chaos Mover |
   | `TraversalMoverChaos` | Traverse Anywhere - Chaos Mover | Chaos Mover, including its extras | Chaos Mover (with `TraversalMover`) |
   | `TraversalGMC` | Traverse Anywhere - GMC | General Movement Component, including its extras | GMC only: see below |

   **CMC** needs only the first two. **NP Mover** adds `TraversalMover`; **Chaos Mover** adds `TraversalMover` and `TraversalMoverChaos`. Copying all of the tester download's `Plugins` folder is fine. Keep **one copy** of each plugin. Never leave a second copy elsewhere in the project or in the engine.

   <div class="notice dependency"><strong>Copy the GMC plugin only if your project has GMC.</strong> <code>TraversalGMC</code> (kept in <code>OptionalPlugins/GMC</code> in the tester download) cannot compile without GMC, GMCMotion and GMAS. A Blueprint-only project compiles <strong>every</strong> plugin in its Plugins folder, enabled or not, so the GMC plugin without GMC stops the whole project building with <em>Could not find definition for module 'GMCMotion'</em>. If your project does have GMC, copy <code>TraversalGMC</code> into the project's <strong>Plugins</strong> folder (<code>YourProject/Plugins/TraversalGMC</code>): Unreal only finds plugins inside Plugins, so an <code>OptionalPlugins</code> folder in your project is ignored.</div>

   **Updating from an earlier tester build?** The old `TraversalCMCExtras`, `TraversalMoverExtras` and `TraversalGMCExtras` folders are now part of the plugins above. Delete those three folders from your project's Plugins folder before copying the new ones. If Unreal then says one of them cannot be found, choose to disable it: its contents are now in `TraversalGaspExtras`, `TraversalMover` or `TraversalGMC`.

3. Open the project and let it compile. Under **Edit > Plugins**, check that **GASP & Traverse Anywhere** and the backend plugins you copied are enabled, then restart if Unreal asks.

   <div class="notice"><strong>Using NP Mover or Chaos Mover?</strong> While you are in <strong>Edit &gt; Plugins</strong>, also enable Epic's <strong>Mover Examples</strong> plugin. It adds Epic's example base pawns, <code>AnimatedMannyPawn</code> (Network Prediction Mover) and <code>ChaosMannyPawn</code> (Chaos Mover), in <code>/MoverExamples/Pawns</code>. You can add Traverse Anywhere to either one: setup copies it into your project first. See <a href="#use-mover">Use NP Mover or Chaos Mover</a>.</div>

4. For animation imports, have a separately obtained, extracted **Unreal Engine 5.8 Game Animation Sample (GASP)** project on disk. You select its folder as the **GASP project** in setup. You can save it in **Editor Preferences > Plugins > Traverse Anywhere Import**.

## Open the setup window

Open **Tools > GASP & Traverse Anywhere** in the level editor, or press **GASP & Traverse Anywhere** on the toolbar of any pawn Blueprint. The window opens as a **Traverse Anywhere** tab. See [The setup window](#setup-window) for a tour.

![The GASP & Traverse Anywhere button on a Blueprint editor toolbar](assets/images/blueprint-toolbar-button.webp)

## Find your way around

| **I want to...** | **Read...** |
| --- | --- |
| Choose my movement system | [CMC, GMC, NP Mover and Chaos Mover](#choose-your-movement-system) |
| Be guided through setup | [Use the setup wizard](#use-the-setup-wizard) |
| Set up an engine example pawn | [Copy an engine pawn into your project](#copy-into-project) |
| Keep my character's locomotion | [Set up an existing character](#set-up-an-existing-character) |
| Prepare a full animation library | [Create a character with full animations](#create-a-character-with-full-animations) |
| Climb objects in my level | [Make an object traversable](#make-an-object-traversable) |
| Adjust a generated object | [Adjust proxies and ledges](#adjust-proxies-and-ledges) |
| Add slides, physical reactions or interactions | [Optional GASP features](#optional-gasp-features) |
| Retarget my own animations | [Retarget your own animations](#retarget-your-own-animations) |
| Play in first person | [Create a first-person character](#create-a-first-person-character) |
| Drive the camera, ragdoll or interactions from Blueprint | [First-person camera functions](#first-person-camera-blueprint) and [Blueprint reference](#blueprint-reference) |
| Solve a problem | [Test and troubleshoot](#test-and-troubleshoot) |
