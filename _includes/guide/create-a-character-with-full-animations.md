Choose this route for a prepared motion-matching animation library and a generated pawn for your selected mesh.

## Choose one of four movement systems

The **final setup plan** offers four dedicated choices: **Character Movement (CMC), GMC, Network Prediction Mover and Chaos Mover**. Choose the actual backend your game will use.

Older builds may show only **CMC** and **Mover**, where Mover creates a Chaos pawn, or lack the completed four-choice wizard. That is an older setup limitation, not the intended final feature split. Check [release progress](#final-release-scope) before following planned controls.

<div class="notice dependency"><strong>GMC prerequisite:</strong> GMC is a paid product that must be purchased, installed and enabled separately. Its TA route also requires compatible GMCMotion and GMAS. See <a href="#prepare-a-gmc-project">GMC setup</a>.</div>

## Prepare the library

1. Open **Full animation setup** and select your movement system.
2. Select the saved **target skeletal mesh** and supported **GASP source project folder**.
3. In the planned wizard, choose any [optional GASP features](#optional-gasp-features). They are off by default; resolve the requirements for the features you select.
4. Choose **Prepare animation assets** and wait for preparation and verification. The target and backend stay locked for that job.

## Install and try it

5. Choose **Install verified animation library** when the report allows it.
6. Select the generated pawn and complete its setup rows. Existing CMC/Chaos output uses **BP_CMC** / **BP_ChaosMover**; use the reported pawn and game mode for your chosen backend.
7. Set the generated **BP_GameMode** as your test map's **GameMode Override**, then press Play.

## What the library contains

The full setup prepares locomotion animations and the Animation Blueprint's supporting choosers, Pose Search data, mirroring and settings for the target. Selected extras also require their animation states, input and supporting physics/audio assets.

Generated libraries are separated by target mesh/skeleton and backend under **Content/TraverseAnywhere/FullAnimation**. Use the preparation report for the exact destination. An occupied destination is reported rather than overwritten; closing setup cancels an active preparation and retains its logs.

A generated pawn is a starting point. Bring across your own gameplay deliberately and test it before replacing an existing character.
