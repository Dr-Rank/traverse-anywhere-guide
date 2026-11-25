A first-person variant created by setup gets a **Traversal First Person Steady Camera** component. It keeps the view steady during ordinary locomotion and blends onto the animated head during traversal, landing, crouch, slides and physical actions. Six Blueprint functions let **your own gameplay** use the same head follow and look limits, for example a ledge peek, a cutscene-style moment, a ladder or a vehicle seat.

![The six camera functions called from two custom events](assets/images/camera-blueprint-functions.webp)

## Get the camera

The camera is created **at runtime, for the locally controlled player only**: it is not in the Blueprint's component list, and other players' copies of the pawn do not have one. Get it with **Get Component by Class**:

1. In your first-person pawn (or anything that can reach it), add **Get Component by Class** and set **Component Class** to **Traversal First Person Steady Camera Component**.
2. Use **Is Valid** on the result before calling it. It is empty on the server for remote players, on other clients, and before the pawn is possessed.
3. Drag from **Return Value** and search the **Traversal Camera** category.

The view is local presentation, so call these functions **on the owning player's machine**, for example from an input event or a client-side event. They do not replicate and do not change gameplay.

The example above compiles as shown: **Start Ledge Peek** follows the head and limits the view, **End Ledge Peek** releases everything with the default return blend.

## The functions

| Function | Inputs | What it does |
| --- | --- | --- |
| **Start Head Camera Follow** | Blend Seconds | Blends the eye onto the animated head with the same eased entry traversal uses, and stays there until you stop it. |
| **Stop Head Camera Follow** | Blend Seconds | Blends the eye back to its normal position with the same bounded return traversal uses. |
| **Is Head Camera Follow Requested** | | True while your Start Head Camera Follow is active. |
| **Start Camera Yaw Restrictions** | Left Degrees, Right Degrees, Blend Seconds | Limits turning left and right, in degrees either side of **the body's forward direction**. Calling it again blends from the current limits to the new ones. |
| **Stop Camera Yaw Restrictions** | Blend Seconds | Releases **only your** yaw limits. |
| **Start Camera Pitch Restrictions** | Down Degrees, Up Degrees, Blend Seconds | Limits looking down and up. Both are positive numbers: *Down 20, Up 30* allows 20° down and 30° up. |
| **Stop Camera Pitch Restrictions** | Blend Seconds | Releases **only your** pitch limits. |

**Blend Seconds:** each call has its own blend time. **Zero or a negative value uses the default**: 0.25 s for a Start, 0.65 s for a Stop.

Head follow, yaw limits and pitch limits are **independent**. Start or stop any of them without affecting the others.

## How it combines with the automatic camera

- **Traversal, airborne motion and physical follow take priority.** If you stop head follow while the pawn is mid-vault, the camera keeps following the head until the vault ends, then returns.
- **Automatic safety limits stay on.** Stopping your restrictions never removes the limits the plugin applies itself. For example, while a first-person body is knocked down the view stays within a window around the physical head, so you cannot look into the open neck of a headless body.
- Your limits are blended in and out, never snapped, so starting a restriction while the player is looking outside it eases the view into range.

## Tune the first-person view

Select the **Traversal First Person Presentation** component on your first-person variant to change these defaults:

| Setting | Default | Meaning |
| --- | --- | --- |
| First Person Max Look Down Degrees | 65 | How far below level the player may look while the body is shown. 0 removes the cap. |
| Physical Camera Yaw Range | 90 | While knocked down or getting up, how far either side of the body the view may turn. 0 = off. |
| Limit View To Physical Head | On | While the head is physically followed, keep the view in a cone around the head. |
| Physical Head Yaw Range / Pitch Range / Pitch Down Range | 45 / 40 / 10 | The size of that cone (degrees). |
| Get Up View Align Time | 0.35 s | How quickly the view turns to the direction the body gets up facing. 0 = no turn. |
| Landing Head Follow Seconds | 1.0 s | How long the camera stays on the head after landing. |
| Crouch Head Follow Seconds | 0.6 s | How long the camera follows the head into a crouch. |
| Eye Offset | (0, 0, 64) | The standing eye position, tuned for the UE5 mannequin. |
| Match Eye To Head Height | On | Adjusts the camera to the mesh's head height across supported body proportions, including compatible MetaHumans. |
| Turn Body With Camera | Off | Turns the owner body with the camera. |
| Use Reachable Arm IK | Off | Keeps the shoulder and solves planted arms without stretching. |
| Add Crouch Input If Missing | On | Adds a crouch binding only if your pawn has none. |

## Advanced: physical head follow

The ragdoll, get-up, hit-reaction and interaction extras switch physical head follow on and off for you. If you build your own physical action, the presentation component offers **Set Physical Head Follow Enabled**, **Set Physical Head Follow Reason** (Ragdoll, Get Up, Reaction or Interaction) and **Is Physical Head Following**. A reason only takes effect on the locally controlled pawn of a variant with physical head follow enabled; the function returns false otherwise.
