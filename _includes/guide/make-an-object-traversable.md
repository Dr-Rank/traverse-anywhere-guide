## The quickest route

1. Stop Play In Editor and find the **static mesh asset** in the Content Browser.

2. Right-click it and choose **Make Traversable**.

3. Traverse Anywhere creates a Blueprint with the mesh as its root, adds the **Traversable** component and **generates proxies automatically**. Fitted pawn collision is enabled for this new Blueprint.

4. The Content Browser goes to and highlights the new Blueprint in **Content/TraverseAnywhere/TraversableObjects**. Drag that Blueprint into your level.

5. Save and play. Approach the object and press jump. Try every side you intend players to use.

## What proxies do

Proxies are simple invisible collision shapes fitted to the object. They give traversal a usable surface and, with fitted pawn collision enabled, give the character a surface to climb and land on. You do not need to create them separately after Make Traversable.

The detailed mesh keeps its appearance. The generated physical proxies handle the pawn's collision, helping details such as door latches avoid obstructing the climb. Other collision uses, such as projectiles, still need to suit your game's setup.

## Use an existing Blueprint

Open the object's Blueprint and add a **Traversable** component. Its **Traversable Proxy** section provides **Generate proxies** when no set exists, or **Rebuild proxies** for an existing set. Use these controls for manually assembled Blueprints and when revising an object.

Check that the object has a reachable ledge, enough room on top and clear space above it. A generated proxy does not make an unsuitable ledge climbable.
