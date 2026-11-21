## The quickest route

1. Stop Play In Editor and find the **static mesh asset** in the Content Browser.

2. Right-click it and choose **Make Traversable**.

3. GASP & Traverse Anywhere creates a Blueprint with the mesh as its root, adds the **Traversable** component and **generates proxies automatically**. Fitted pawn collision is turned on for the new Blueprint.

4. The Content Browser goes to the new Blueprint in **Content/TraverseAnywhere/TraversableObjects**. Drag it into your level.

5. Save and play. Approach the object and press jump. Try every side you intend players to use.

## Convert meshes already placed in your level

Right-click a placed static mesh actor in the viewport or the Outliner. The **GASP & Traverse Anywhere** section offers:

![The GASP & Traverse Anywhere section of the level actor menu](assets/images/level-actor-menu.webp)

| Menu entry | What it does |
| --- | --- |
| **Make Traversable (this instance)** or **(N selected instances)** | Replaces the selected actors with the mesh's traversable Blueprint (made, or reused, in TraverseAnywhere/TraversableObjects), keeping their exact transforms. |
| **Make Traversable (all N instances of *Mesh*)** | Does the same for every loaded plain static mesh actor showing that mesh. Blueprint actors, other meshes and unloaded World Partition cells are never touched. |
| **Make Traversable (all N instances in *Component*)** | On an instanced static mesh component: each instance becomes a placed traversable actor at its exact transform, and is removed from the component. Foliage, PCG output and construction-script instancers are not offered. |
| **Cull Covered Traversal Proxies (N selected)** | For traversable objects that overlap: proxies whose whole top is buried inside another object's proxies stop offering ledges. Pawn collision is unchanged and assets are never edited. |

Each of these is one **Edit > Undo** step. Back up your project before converting a large level.

## What proxies do

Proxies are simple invisible collision shapes fitted to the object. They give traversal a usable surface and, with fitted pawn collision, give the character a surface to climb and land on. You do not need to create them separately after Make Traversable.

The detailed mesh keeps its appearance. The generated proxies handle the pawn's collision, which stops small details such as door latches spoiling a climb. Other collision uses, such as projectiles, still follow your game's own setup: proxies never block bullets or the camera.

## Use an existing Blueprint

Open the object's Blueprint and add a **Traversable** component. Its **Traversable Proxy** section offers **Generate proxies** when there is no set yet, or **Rebuild proxies** for an existing set. Use these for hand-assembled Blueprints and when revising an object.

Check that the object has a reachable ledge, enough room on top and clear space above it. A proxy does not make an unsuitable ledge climbable.
