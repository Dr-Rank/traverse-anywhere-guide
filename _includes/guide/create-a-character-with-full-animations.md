Choose this route when you want a prepared motion-matching animation library and a generated pawn for your selected mesh.

## Prepare the library

1. Open **Full animation setup** in the setup window.

2. Choose **Character Movement (CMC)** or **Mover**. The Mover option creates a **Chaos Mover** pawn. Network Prediction Mover uses the existing-pawn traversal setup.

3. Select your saved **target skeletal mesh** and the supported **GASP source project folder**.

4. Choose **Prepare animation assets**. Wait for preparation and verification to finish. You can continue using the editor, but the selected target and backend stay locked for that job.

## Install and try it

5. When ready, choose **Install verified animation library**.

6. The setup selects the generated **BP_CMC** or **BP_ChaosMover** pawn, and the Content Browser highlights its **BP_GameMode**. Complete the pawn's setup rows.

7. In your test map's **World Settings**, set **GameMode Override** to that generated game mode, then press Play.

## Where your assets go

Each target and backend has its own folder under **Content/TraverseAnywhere/FullAnimation/<Skeleton>__<Mesh>/<CMC or Mover>**. The imported animation graph, pawn, input and animation settings belong to that library. Its motion-matching default is local to that Animation Blueprint.

An occupied destination is reported rather than overwritten. Read the preparation report if installation is unavailable. Closing the setup window cancels an active preparation and retains its logs.

The generated pawn is a starting point for your game. Bring your own camera, abilities, equipment and other gameplay across deliberately, keeping a backup of your existing character.
