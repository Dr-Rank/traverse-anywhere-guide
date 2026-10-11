## GMC integration status

GMC integration is being verified in GMCv2_Demo on Unreal Engine 5.8. The prerequisite checks and native traversal tests are available in the development build; the one-click existing-pawn and Full GASP installation paths, first person gameplay, multiplayer and packaged GMC checks are not yet release-qualified. Do not treat the GMC option as a completed installation path until those checks are finished.

## Install the prerequisites

1. Back up your project. Install a compatible licensed **GMC** version for your engine. Keep only one copy of each plugin.

2. Install **GMCMotion** from [github.com/Dr-Rank/GMCMotion](https://github.com/Dr-Rank/GMCMotion) in your project's Plugins folder.

3. Install **GMCAbilitySystem (GMAS)** from [Dr-Rank/DeepWorlds_GMCAbilitySystem, clear-fixes branch](https://github.com/Dr-Rank/DeepWorlds_GMCAbilitySystem/tree/clear-fixes) in the same Plugins folder. GMAS installation is required by GMCMotion; using gameplay abilities in your game is optional.

4. Enable the prerequisites and Traverse Anywhere, rebuild for the matching engine when required, then restart Unreal. Select **GMC** in Traverse Anywhere Setup and read the prerequisite results. A plugin folder alone is not enough: its descriptor must be valid, and the required plugins must be enabled and loaded.

## Use the reference projects

Compare your pawn, movement component, input, Animation Blueprint, chooser and mesh tick settings against **GMCv2_Demo with Traverse Anywhere added** and **GMCLocomotion** if your own setup behaves differently. Use the matching tested versions. These are integration references, not a guarantee that a custom project will work unchanged. The original GMC demo does not already contain Traverse Anywhere.

## Keep your custom pawn safe

Do not replace or reparent your gameplay pawn just to clear a setup warning. Custom GMC movement subclasses and input graphs need compatibility checks. Preserve weapons, abilities, inventory and camera logic, and read any blocked-row explanation before proceeding.
