Prepare your character, then right-click a static mesh and choose **Make Traversable**. Traverse Anywhere creates the Blueprint, adds traversal and generates its proxies for you. Drag the new Blueprint into your level and try it.

This guide takes you through installation, character setup, animations, objects, proxy settings and everyday troubleshooting. You can use your existing character's locomotion or prepare a full animation library for a new character.

**Four movement choices:** CMC, GMC, Network Prediction Mover and Chaos Mover. Start with [Choose your movement system](#choose-your-movement-system). **GMC is a paid third-party product: purchase, install and enable it separately to use the GMC route. It is not included with Traverse Anywhere.**

This edition also covers the planned final-release extras and user-animation retargeting. [Release scope and progress](#final-release-scope) identifies the remaining setup and qualification work.

## Before making changes

**Back up your project.** Make a source-control commit or a complete project copy before running setup or importing animations. Some changes affect shared skeletons, Animation Blueprints and project settings. Your own input, animation, movement and gameplay setup may behave differently: some features may break or not work as expected. Test on a copy first. Unreal's Undo is not a replacement for a backup.

## Install and open the plugin

1. Install the Traverse Anywhere version that matches your Unreal Engine version. For a supplied project package, place its **Traversal** folder inside your project's **Plugins** folder.

2. Open **Edit > Plugins**, enable **Traverse Anywhere** and restart Unreal when requested. Use one copy of the plugin.

3. Open **Tools > Traverse Anywhere Setup**. The setup window stays closed until you open it. You can also use **Traversal Setup** in a pawn Blueprint's toolbar.

4. Have a separately obtained, extracted **Unreal Engine 5.8 Game Animation Sample** project available when importing animations. Select its folder in **GASP project**. You can save that folder in **Editor Preferences > Plugins > Traverse Anywhere Import**.

## Find your way around

| **I want to...** | **Read...** |
| --- | --- |
| Choose my movement system | [CMC, GMC, NP Mover and Chaos Mover](#choose-your-movement-system) |
| Explore the final feature set | [Features](#features) and [release progress](#final-release-scope) |
| Keep my character's locomotion | Set up an existing character |
| Prepare a full animation library | Create a character with full animations |
| Climb objects in my level | Make an object traversable |
| Adjust a generated object | Adjust proxies and ledges |
| Add slides, physical reactions or interactions | [Optional GASP features](#optional-gasp-features) |
| Retarget my own animation clips | [Planned user-animation retargeting](#retarget-your-own-animations) |
| Solve a problem | [Troubleshooting](#test-and-troubleshoot) |
