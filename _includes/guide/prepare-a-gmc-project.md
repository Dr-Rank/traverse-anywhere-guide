**GMC is one of GASP & Traverse Anywhere's four movement routes**, alongside CMC, Network Prediction Mover and Chaos Mover, with full animation setup, traversal, the extras and first person.

<div class="notice dependency"><strong>Separate paid product required.</strong> General Movement Component (GMC) is a paid third-party product. You must purchase a compatible GMC version and install and enable it to use GASP & Traverse Anywhere with GMC. A GASP & Traverse Anywhere purchase does not include GMC or replace that purchase. Installing GMCMotion alone does not supply GMC.</div>

## Install the prerequisites

1. Back up your project. **Purchase and install a compatible licensed GMC version** for Unreal Engine 5.8. Keep one copy of each plugin.

2. Install a compatible [GMCMotion](https://github.com/Dr-Rank/GMCMotion) in your project's Plugins folder. Use the version matching your GASP & Traverse Anywhere release; older versions may lack movement features it needs.

3. Install [GMCAbilitySystem (GMAS), clear-fixes branch](https://github.com/Dr-Rank/DeepWorlds_GMCAbilitySystem/tree/clear-fixes). The integration requires GMAS; using its gameplay abilities in your own game is optional.

4. Copy `TraversalGMC`, and `TraversalGMCExtras` for the extras, into your Plugins folder.

5. Enable GMC, GMCMotion, GMAS and the GASP & Traverse Anywhere plugins, rebuild, then restart Unreal.

## Check the GMC panel

When you choose **GMC** in the wizard or in Full animation setup, the setup window lists each requirement in **green** (installed, enabled and loaded) or **red**, with what to do: install one copy, enable it and restart, or rebuild. A folder on disk is not enough; each plugin must be valid, enabled and loaded.

**Prepare GMC level services** adds what every GMC gameplay level needs: one **Aggregator** and one **World Time Replicator** in its persistent level. Existing actors are reused, never duplicated. Read the Output Log for the actor counts, then save the level.

## Set up the pawn

Choose [existing-character setup](#set-up-an-existing-character) to keep your own GMC locomotion, or [full animation setup](#create-a-character-with-full-animations) for a generated GMC pawn with the extras you tick. On GMC pawns using GMAS, the death ragdoll follows the GMAS death state automatically.

## Keep your custom pawn safe

Compare against [GMCLocomotion](https://github.com/Dr-Rank/GMCLocomotion) or a GMC demo pawn with GASP & Traverse Anywhere added, using matching tested versions. The original GMC demo does not contain it.

Do not replace or reparent a custom gameplay pawn just to clear a warning. Keep your movement subclasses, weapons, abilities, inventory and camera logic, and follow what blocked rows say. CMC and both Mover routes do not need GMC, GMCMotion or GMAS.
