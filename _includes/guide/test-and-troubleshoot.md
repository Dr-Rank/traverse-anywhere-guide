## A useful first test

Use a simple block in a clear level. Try walking, running and sprinting approaches, then both sides of an irregular object. Watch hand placement during contact, leg clearance, landing and the blend back to walking or idle. Repeat while holding movement and while releasing it. Test packaged gameplay and multiplayer if your game uses them.

## Setup

| **What you see** | **What to check** |
| --- | --- |
| A row says **Needs attention** | Read its text: usually another row must be applied first, or the asset is read-only. Apply the earlier row, then **Check again**. |
| A row says a pawn or mesh is **engine content** | Engine and plugin content is read-only. For the pawn, use **Copy into my project** ([how](#copy-into-project)). For a project pawn whose *mesh* is engine content, the copy button does not appear yet; use a mesh in your project. |
| The Mover example pawns are missing from the pawn picker | Enable the Mover Examples plugin, then in the picker's settings tick **Engine Content** as well as **Plugin Content**. |
| The Message Log opens during a copy | Normal. Unreal checks the copies as they are saved. See [What Unreal shows while it copies](#copy-into-project). |
| The wizard shows the previous pawn | The wizard starts from your last plan. Pick the pawn again in step 3. |
| Extras are not offered | Extras are built into **new** pawns only. Choose a new pawn in the wizard, or tick them in Full animation setup. An amber line under the checkboxes gives any reason one cannot be generated. |
| Preview and Prepare are greyed out | Choose the **GASP project** folder and a saved **Target skeletal mesh** first. |
| Full import will not install | Read its preparation report. Check the source folder, the saved target mesh, write access and whether the destination already holds a library. |
| GMC unavailable or red in the GMC panel | Purchase and install the paid GMC plugin separately; enable compatible GMC, GMCMotion and GMAS, then rebuild and restart. GMCMotion alone does not provide GMC. |
| Changes are lost after restarting Unreal | Applied changes are in memory until you save. **File > Save All**. |

## Traversal and objects

| **What you see** | **What to check** |
| --- | --- |
| Normal jump instead of traversal | Recheck the pawn's rows, jump input, chooser and the Traversable trace channel. Use the generated object Blueprint, not the original static mesh actor. |
| Object detected but no climb | Check height, usable depth, ledge width, headroom, landing room and available animations. Update an older chooser if setup reports it. |
| Hands sit too high | Update the baked traversal animations if the import row asks. Check the selected mesh and any custom rig that changes the pose. |
| Feet pull away or enter the object | Check the Foot IK and Foot clearance rows, the rig's compatibility and the object's actual collision. |
| Latches or raised corners spoil a climb | Rebuild proxies with the side-shelf and top/ledge height controls. Check the result from each approach. |
| Overlapping objects offer a ledge inside another object | Select them and use **Cull Covered Traversal Proxies**. |
| Proxy buttons unavailable | Stop Play. Use a writable Blueprint and read the button tooltip for inherited-proxy or selection conflicts. |
| Pose snaps at the end | Keep the montage slot connected to locomotion. Check custom code that stops montages twice, replaces the Animation Blueprint or resets its state. |
| Chaos Mover: a press far from the obstacle just jumps | A networked Chaos press is refused when the pawn could not brake in time. Press closer. |

## Extras and first person

| **What you see** | **What to check** |
| --- | --- |
| Slide does not start or ends in the wrong stance | Check the slide type you expect (requested, automatic or flat), slope and speed, crouch input and the slide animation states. Compare owner and remote views. |
| Ragdoll or get-up fails | Check the physics asset, Physics Control, recovery animations, pose history and animation-state wiring. Players get up with the get-up input once still. |
| Hits do nothing | **Add Hit Impulse** and **Trigger Ragdoll** only work on the server. Call them from server-side damage code. |
| A paired action is refused | Check both participants: on the ground, in front, within 2 m, not busy, and on a supported movement system. |
| First-person view stays limited | Your own **Start Camera ... Restrictions** need matching **Stop** calls. The built-in limits release when the action ends. |
| Camera functions do nothing | The camera exists only for the locally controlled player. Check **Is Valid** on Get Component by Class, and call from the owning client. |
| Retargeting my own animations | Not in this build. See [the planned step](#retarget-your-own-animations). |

Test each extra on its own and in the combinations you intend to ship, including with all extras off. Cover third and first person, the meshes and physics assets you ship, server, owner and remote views, spectators, lag and packet loss, and packaged gameplay.

## Reporting a problem

Include your Unreal version, movement system, pawn and mesh names, the row's message or the Output Log, and the smallest steps that reproduce it. Screenshots help for camera and animation issues. For detailed animation-selection rules, see the [Chooser reference](assets/downloads/chooser-reference.pdf). Keep your project backup until your own gameplay checks are complete.
