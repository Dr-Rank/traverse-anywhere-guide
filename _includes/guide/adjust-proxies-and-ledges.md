## Start with the generated result

Open the object Blueprint, select **Traversable**, and inspect its proxy settings. After changing the mesh, root scale or proxy settings, stop Play and choose **Rebuild proxies**. The rebuilt set applies to all placed instances of that Blueprint.

| **Proxy setting** | **When it helps** |
| --- | --- |
| Cell size | Controls sampling detail. Smaller cells follow finer shapes but take more work. |
| Spike filter radius | Smooths small raised details on the sampled top surface. |
| Min side shelf depth | Filters shallow shelves beside a taller surface, such as small latch ledges. Default 60 cm; 0 disables this filter. |
| Height tolerance | Controls how closely boxes follow changes in height. |
| Max top height error | Keeps raised corners from lifting a much larger top surface. Default 5 cm. |
| Max ledge height error | Fits exposed ledge edges more closely. Default 2.5 cm. |
| Maximum boxes | Preferred number of boxes. The generator can use more to retain accuracy; it reports an excessive result instead of replacing a usable set. |
| Generate Fitted Pawn Collision | Adds physical support for the pawn alongside the traversal query proxies. Make Traversable enables this automatically. |

## Remove or revise a set

**Remove proxies** removes the generated shapes and restores the source mesh's original Pawn collision response. You can generate a new set later. Removing proxies from a placed Blueprint affects its shared Blueprint, so review the other instances too.

For unusual shapes, use the component's ledge controls: **Min Ledge Width**, **Max Ledge Search Height**, **Max Obstacle Depth**, **Surface Inset**, **Edge Probe Depth** and **Min Top Surface Normal Z**. The [Property reference](property-reference.html) explains their defaults.

For inspection, enable **Show Height Label** on the Traversable component to display its estimated climb height. **Draw Debug Traces** shows the ledge probes in the editor. These tools help explain a rejected surface; the pawn still makes the final traversal decision.

Prefer uniform scale on placed instances. For a changed shape or non-uniform scale, set the desired root scale in the Blueprint and rebuild there. Parent and child Blueprints with conflicting inherited proxy sets cannot be rebuilt independently.
