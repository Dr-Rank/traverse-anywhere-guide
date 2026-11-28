Open **Tools > GASP & Traverse Anywhere** in the Unreal Editor. The wizard opens on **Your pawn**. Use **Continue** and **Back** to move between pages. **Set up my pawn** starts work after you review your choices. If you choose **Copy into my project** earlier, the copy is created at that point.

## Choose your setup

| Page | What to do |
| --- | --- |
| **Your pawn** | Choose **I have a pawn** to select a Blueprint you already use. The wizard reads its mesh, skeleton and movement system. Or choose **Create a new pawn from a mesh**, pick the skeletal mesh, and select CMC, Network Prediction Mover, Chaos Mover or GMC. GMC requires its own plugin. |
| **Animation** | For an existing pawn, choose **Keep my locomotion and add traversal**, or **Full GASP motion matching** to build a separate pawn. A new pawn uses full GASP. Pick Neutral or Relaxed traversal montages separately from the locomotion style. Point the wizard to your Game Animation Sample project folder. |
| **View and extras** | Choose third or first person. Full GASP can include slide, ragdoll and get-up, physical hit reactions, and paired interactions. **First-person camera limits** appear when you choose First person. |
| **Review your setup** | Check the movement system, animation choices, view, extras and proposed asset changes. Leave **Make GASP sample level blocks traversable** off unless you want to update the sample's obstacle Blueprints. When you're ready, choose **Set up my pawn**. |

If you pick engine or plugin content, use the [copy action](#copy-into-project) when the wizard asks. The generated pawn or the traversal setup works with project-owned assets.

**Keeping your locomotion** preserves the pawn's movement system and existing animation setup. If you're using ALS, disable its built-in mantling and keep its normal jump. If the wizard can't recognise your custom jump graph, it shows where to call **TryTraversal** and how to use your existing jump when that call returns false. First person works with a compatible custom locomotion system. You manage turn in place in that system.

**Full GASP** creates a separate pawn, including the extras you select. If required physics bodies are missing, setup generates a compatible physics asset for the new pawn and keeps the original. To change the generated extras later, set up a new pawn.

## Full GASP dependencies

If the wizard or scripted preview names **MovieSceneAnimMixer** or **Mover** as missing, enable the named engine plugins in **Edit > Plugins**, restart the editor, and continue setup. Full GASP requires them even if you already installed the animation library.

## Follow setup progress

1. For full GASP, the progress panel shows **conversion**, **preparation** and **verification**. It shows the current clip or check, a percentage once the total is known, and how long the current stage has been running.
2. If Unreal separately asks whether to import detected changes to source content files, choose **Don't Import**. Continue in the wizard.
3. When verification finishes, choose **Install verified GASP library**. The wizard continues with the applicable pawn checks, including physics playback, pose history, hand contact and obstacle foot clearance.
4. If the wizard asks you to restart, save your work and reopen the same project. Open **GASP & Traverse Anywhere** and choose **Continue setup**. It resumes with your saved selections and installed pawn.
5. When **Guided setup is complete** appears, use **Open pawn** to see the generated Blueprint or pick a level and choose **Open test level**. Set the resulting pawn as your GameMode's **Default Pawn Class** before testing. Selecting **First person** creates the first-person variant during guided setup.

Open **Advanced tools** from the first page when you want the individual checks or need to repair an existing setup. The guided flow runs its own required checks.

[See the redesigned wizard screens](#setup-wizard-screens-1).

## Run guided setup from a script

You can use the same guided setup from the editor console, Python or an editor Blueprint. Both routes use the same setup choices and saved progress.

1. Preview the choices before making changes. In the editor console, run:

   ```text
   TraverseAnywhere.Setup.Wizard.Preview Mesh=/Game/Characters/Hero/SKM_Hero.SKM_Hero Backend=CMC GASP="C:/Projects/GameAnimationSample"
   ```

   Use your mesh asset path and Game Animation Sample project folder. For an existing pawn, use `Pawn=/Game/.../BP_MyPawn.BP_MyPawn` instead of `Mesh=…`. A new pawn uses full GASP. Adding `FullGasp` to an existing pawn's options creates a separate pawn with GASP locomotion.

2. When the preview says setup can start and you have reviewed the asset changes, run the same command with `Start` in place of `Preview`.
3. Use `TraverseAnywhere.Setup.Wizard.Status` to check progress and `TraverseAnywhere.Setup.Wizard.Install` when the verified library is ready. Add `AutoInstall` to the start command when you want installation to occur automatically after verification.
4. Use `TraverseAnywhere.Setup.Wizard.Pause` to pause a scripted run, or `TraverseAnywhere.Setup.Wizard.Resume` after pausing or restarting. You can also reopen the guided wizard and choose **Continue setup**. Run one guided setup at a time.

For Python or editor Blueprints, use **Traversal Setup Scripting**. Its `PreviewGuidedSetup`, `StartGuidedSetup`, `GetGuidedSetupStatus`, `InstallVerifiedLibrary`, `PauseGuidedSetup` and `ResumeGuidedSetup` functions follow the same steps. An active scripted run also writes its status to `Saved/TraverseAnywhere/ScriptedSetup.json` inside your project.
