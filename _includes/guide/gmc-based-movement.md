## Set up GMC based movement on a moving platform

Based movement lets a pawn move with the surface it is standing on. Prepare the GMC level services first. On the pawn's **GMC Organic Movement** component, open **Movement → Operation → Based Movement → Source**, then choose a source that matches how your platform moves.

Add a **Traversable** component to the platform Blueprint. Attach the visible mesh, blocking collision and any traversal proxies to the part that moves so the ledge stays aligned during the climb. [Prepare traversal collision]({{ '/#make-an-object-traversable' | relative_url }}).

### Relative for a replicated platform

1. Use a platform Actor with a **Movable** collision root. Enable **Replicates** and **Replicate Movement**, and drive the platform transform on the server.
2. Set the pawn's **Source** to **Relative**. The server validates attachment and GMC synchronizes the pawn relative to the base.
3. Start with a platform that translates slowly without rotating through the boarding point. A stationary boarding phase gives you a useful control if your route produces corrections. Test turns, tilts and faster routes separately. A deliberate walk-off can still cause a small correction when GMC releases the base.

### Velocity for a predictable platform

1. Start with **GMC Rollback Platform**, or duplicate **BP_MovingPlatform_BasedMovementDemo** from the GMCv2 Based Movement Demo. Use the same start transform, linear velocity and move duration on the host and clients.
2. Set the pawn's **Source** to **Velocity**. The rollback platform needs a route it can reproduce from GMC's synchronized clock during prediction and replay. For a server-driven route that changes with gameplay, start with Relative.

**Mixing modes in one level.** The source belongs to the pawn and applies before GMC finds a base. Use separate approach areas and switch the pawn's source early enough for the change to reach the client before it can climb. Use rollback platforms in Velocity areas. [GMCv2 Based Movement manual](https://grimtec.net/gmcv2-documentation-manual-based-movement/).

### Verify your boarding point

Run a listen server with two clients. Have each client climb while the other watches, then repeat with simulated lag and packet loss. Check the owner, host and observer views. During the climb, watch the hands against the moving ledge. At the top, check that the pawn stays grounded, rides with the platform and avoids a landing animation. Walk off deliberately to confirm that a real drop still lands normally.

The tested setup used a 2.5 m climb, a platform moving sideways at 25 cm/s, 100 ms simulated lag and 1% packet loss. Both sources finished grounded on all three views and preserved the landing on a real drop. The two Relative owners attached without a position correction, and neither mode logged a replay burst in that run. Use the same setup as a reference when testing your own platform, especially if it moves faster or rotates.
