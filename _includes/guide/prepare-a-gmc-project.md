**GMC is one of GASP & Traverse Anywhere's four primary movement routes**, alongside CMC, Network Prediction Mover and Chaos Mover. The final plan includes full-animation setup, traversal, optional extras and first-person presentation for GMC.

<div class="notice dependency"><strong>Separate paid product required.</strong> General Movement Component (GMC) is a paid third-party product. You must purchase a compatible GMC version and install and enable it to use GASP & Traverse Anywhere with GMC. A GASP & Traverse Anywhere purchase does not include GMC or replace that purchase. Installing GMCMotion alone does not supply GMC.</div>

## Install the prerequisites

1. Back up your project. **Purchase and install a compatible licensed GMC version** for your Unreal Engine version. Keep one copy of each plugin.

2. Install a compatible [GMCMotion](https://github.com/Dr-Rank/GMCMotion) version in your project's Plugins folder. Use the version required by your TA release; older builds may lack the movement features it needs.

3. Install [GMCAbilitySystem (GMAS), clear-fixes branch](https://github.com/Dr-Rank/DeepWorlds_GMCAbilitySystem/tree/clear-fixes). GMAS is required by this integration; using its gameplay abilities in your game is optional.

4. Enable GMC, GMCMotion, GMAS and GASP & Traverse Anywhere. Rebuild for the matching engine where required, then restart Unreal. Choose **GMC** in setup and resolve the prerequisite results. A folder alone is not enough: the required plugins must be valid, enabled and loaded.

## Planned feature setup

Choose [existing-character setup](#set-up-an-existing-character) to retain your own locomotion, or [full animation setup](#create-a-character-with-full-animations) for a generated GMC pawn. The final wizard is planned to install selected slides, ragdoll/get-ups, physical reactions and interactions through the GMC-specific extras integration.

GMC extras work and its regression checks are completed and carried forward in the 15 November handover. The shared wizard and final package qualification remain; see [release progress](#final-release-scope).

## Keep your custom pawn safe

Compare against **GMCv2_Demo with TA added** or [GMCLocomotion](https://github.com/Dr-Rank/GMCLocomotion), using matching tested versions. The original GMC demo does not already contain TA.

Do not replace or reparent a custom gameplay pawn merely to clear a warning. Preserve movement subclasses, weapons, abilities, inventory and camera logic, and follow blocked-row guidance. CMC and both Mover routes do not need GMC, GMCMotion or GMAS.
