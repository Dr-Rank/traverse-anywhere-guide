These are the Blueprint functions and events you are most likely to connect to your own gameplay. **Server** means the function only works on the server (it is marked *Authority Only* and does nothing on a client). Camera functions are on the previous page: [First-person camera functions](#first-person-camera-blueprint).

## Traversal: Traversal Action component

| Function or event | Where to call it | What it does |
| --- | --- | --- |
| **Try Traversal Or Jump** | Locally controlled pawn | Detects, chooses and starts a traversal. On a Character with nothing to traverse, it jumps instead. Returns whether a traversal started. This is the node setup wires into your jump input; keep **Stop Jumping** on release. |
| **Try Traversal** | Locally controlled pawn | The traversal attempt only. Returns false when there is nothing to traverse, so your own jump can run. Use it on non-Character pawns, whose movement system owns jumping. |
| **Is Traversing** | Anywhere | True while a traversal plays. |
| **On Traversal Started** / **On Traversal Ended** | Bind on any machine | Events for cosmetics such as camera shake, sound or particles. They fire on every machine that plays the traversal, so do not run gameplay rules from them. |

The traversal calls return false on machines that do not control the pawn; the other machines hear about it through the plugin's replication.

**In an Animation Blueprint:** **Is Owner Traversing**, **False While Traversing** and **Zero While Traversing** gate foot IK, in-air poses and similar values during traversal. The setup rows insert them for you.

**On a traversable object:** the Traversable component's **Get Measured Height** returns the object's estimated climb height. **Get Trace Type By Name** finds the *Traversable* trace channel for your own traces.

## Ragdoll, hits and death: Traversal Gasp Ragdoll component

Added to pawns created with the ragdoll, hit-reaction or interaction extras.

| Function | Where | What it does |
| --- | --- | --- |
| **Add Hit Impulse** (Impact Velocity, Impact Location, Imparted Energy) | Server | Report an impact, such as a bullet, projectile or blow. A standing pawn plays a hit reaction on the hit limb, or is knocked down once enough hits add up. A knocked-down pawn's nearest body is kicked. **This is the usual entry point from your damage code.** |
| **Trigger Ragdoll** (Injury, Impulse, Impulse Location) | Server | Knock the pawn down directly. Injury chooses how it recovers: None, Limp, Stunned, Head Face, Head Back, Body Front or Groin. Ignored when the pawn is dead or already ragdolling. |
| **Exit Ragdoll** (Force) | Server | Get up now. Force skips the "on the floor" check. By default, players get up by pressing the component's **Get Up Action** input once they are still on the floor, and AI pawns get up by themselves after **Bot Get Up Delay** (3 s). Tick **Players Get Up Automatically** to treat players like AI. |
| **Trigger Death Ragdoll** | Server | The pawn dies: a limp ragdoll that never gets up. **Call it from your own death logic.** On GMC pawns with GMAS the GMC extras do it for you. |
| **Request Toggle Ragdoll** | Owning client or server | Input helper: fall when standing, get up when down. |
| **Is Dead**, **Is Ragdolling**, **Is Getting Up**, **Get Ragdoll Phase** | Anywhere | Current state. The phase is None, Ragdoll, Getting Up, Dead or Interacting. |
| **Is Out Of Player Control** | Anywhere | True while knocked down, getting up, or on the receiving end of a shove, tackle or takedown. Disable your own input or abilities while it is true. |
| **Is Actor Ragdolling** (Actor) | Anywhere | Static helper. Use it rather than *Is Simulating Physics*, which the physical hit-reaction layer also turns on. |
| **Is Death Ragdoll Active** (Actor) | Anywhere | Static helper to run death logic **once**, not every tick on a corpse. |

## Paired interactions

| Function | Where | What it does |
| --- | --- | --- |
| **Request Interaction** (Type) | Owning client or server | Input helper: try a Shove, Tackle or Takedown against the characters in front. |
| **Try Interaction** (Type, Target) | Server | Start an interaction now, optionally against one Target. Returns false when nothing could start. |
| **Can Do Character Interaction** | Anywhere | This pawn can start one: on the ground, no montage playing, not aiming. |
| **Can Be Interacted With** | Anywhere | This pawn can be a target (on the ground). |
| **Find Interactable Characters** | Anywhere | Characters within 2 m, 50 cm up or down, 60° in front and unobstructed. |

Your game decides **when** an interaction is allowed (input, targeting, teams, cooldowns). Health, damage and death rules stay yours.

## Networking rules of thumb

- Call **Server** functions from server-side code, such as your damage handling, a server RPC or the GameMode.
- The owning-client helpers (**Request ...**) send their own server request.
- The camera functions are local to the owning player.
- Movement and traversal replication are handled by your movement backend and the plugin. Test with the server, the owning client and a remote observer.
