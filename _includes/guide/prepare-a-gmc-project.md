**GMC is one of GASP & Traverse Anywhere's four movement routes**, alongside CMC, Network Prediction Mover and Chaos Mover, with full animation setup, traversal, the extras and first person.

<div class="notice dependency"><strong>Separate paid product required.</strong> General Movement Component (GMC) is a paid third-party product. You must purchase a compatible GMC version and install and enable it to use GASP & Traverse Anywhere with GMC. A GASP & Traverse Anywhere purchase does not include GMC or replace that purchase. Installing GMCMotion alone does not supply GMC.</div>

## Install the prerequisites

1. Back up your project. **Purchase and install a compatible licensed GMC version** for Unreal Engine 5.8. Keep one copy of each plugin.

2. Install a compatible [GMCMotion](https://github.com/Dr-Rank/GMCMotion) in your project's Plugins folder. Use the version matching your GASP & Traverse Anywhere release; older versions may lack movement features it needs.

3. Install [GMCAbilitySystem (GMAS), clear-fixes branch](https://github.com/Dr-Rank/DeepWorlds_GMCAbilitySystem/tree/clear-fixes). The integration requires GMAS; using its gameplay abilities in your own game is optional.

4. Copy `Traversal`, `TraversalGaspExtras` and `TraversalGMC` into your Plugins folder. `TraversalGMC` includes the GMC extras. In the tester download it is in `OptionalPlugins/GMC`, kept apart so that projects without GMC still compile: copy it into your project's **Plugins** folder (`YourProject/Plugins/TraversalGMC`). Unreal only finds plugins inside Plugins, so an `OptionalPlugins` folder in your project is ignored.

5. Enable GMC, GMCMotion, GMAS and the GASP & Traverse Anywhere plugins, rebuild, then restart Unreal.

## Check the GMC panel

When you choose **GMC** in the wizard or in Full animation setup, the setup window lists each requirement in **green** (installed, enabled and loaded) or **red**, with what to do: install one copy, enable it and restart, or rebuild. A folder on disk is not enough; each plugin must be valid, enabled and loaded.

**Prepare GMC level services** adds what every GMC gameplay level needs: one **Aggregator** and one **World Time Replicator** in its persistent level. Existing actors are reused, never duplicated. Read the Output Log for the actor counts, then save the level.

## Set up the pawn

Choose [existing-character setup](#set-up-an-existing-character) to keep your own GMC locomotion, or [full animation setup](#create-a-character-with-full-animations) for a generated GMC pawn with the extras you tick. On GMC pawns using GMAS, the death ragdoll follows the GMAS death state automatically.

## Set up GMC based movement on a moving platform

Based movement lets a pawn move with the surface it is standing on. Prepare the GMC level services first. On the pawn's **GMC Organic Movement** component, open **Movement → Operation → Based Movement → Source**, then choose a source that matches how your platform moves.

Add a **Traversable** component to the platform Blueprint. Attach the visible mesh, blocking collision and any traversal proxies to the part that moves so the ledge stays aligned during the climb. [Prepare traversal collision](#make-an-object-traversable).

### Relative for a replicated platform

1. Use a platform Actor with a **Movable** collision root. Enable **Replicates** and **Replicate Movement**, and drive the platform transform on the server.
2. Set the pawn's **Source** to **Relative**. The server validates attachment and GMC synchronizes the pawn relative to the base.
3. Start with a platform that translates slowly without rotating through the boarding point. A stationary boarding phase gives you a useful control if your route produces corrections. Test turns, tilts and faster routes separately. A deliberate walk-off can still cause a small correction when GMC releases the base.

### Velocity for a predictable platform

1. Start with **GMC Rollback Platform**, or duplicate **BP_MovingPlatform_BasedMovementDemo** from the GMCv2 Based Movement Demo. Use the same start transform, linear velocity and move duration on the host and clients.
2. Set the pawn's **Source** to **Velocity**. The rollback platform needs a route it can reproduce from GMC's synchronized clock during prediction and replay. For a server-driven route that changes with gameplay, start with Relative.

**Mixing modes in one level.** The source belongs to the pawn and applies before GMC finds a base. Use separate approach areas and switch the pawn's source early enough for the change to reach the client before it can climb. Use rollback platforms in Velocity areas. [GMCv2 Based Movement manual](https://grimtec.net/gmcv2-documentation-manual-based-movement/).

### Verify your boarding point

Run a listen server with two clients. Have each client climb while the other watches, then repeat with simulated lag and packet loss. Check the owner, host and observer views. During the climb, watch the hands against the moving ledge. At the top, check that the pawn stays grounded, rides with the platform and avoids a landing animation. Walk off deliberately to confirm that a real drop still lands normally.

The tested setup used a 2.5 m climb, a platform moving sideways at 25 cm/s, 100 ms simulated lag and 1% packet loss. Both sources finished grounded on all three views and preserved the landing on a real drop. The two Relative owners attached without a position correction, and neither mode logged a replay burst in that run. Use the same setup as a reference when testing your own platform, especially if it moves faster or rotates.

## Keep your custom pawn safe

Compare against [GMCLocomotion](https://github.com/Dr-Rank/GMCLocomotion) or a GMC demo pawn with GASP & Traverse Anywhere added, using matching tested versions. The original GMC demo does not contain it.

Do not replace or reparent a custom gameplay pawn just to clear a warning. Keep your movement subclasses, weapons, abilities, inventory and camera logic, and follow what blocked rows say. CMC and both Mover routes do not need GMC, GMCMotion or GMAS.
