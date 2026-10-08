## A useful first test

Use a simple block in a clear level. Try walking, running and sprinting approaches, then both sides of an irregular object. Look at hand placement during contact, leg clearance, landing and the blend back to walking or idle. Repeat while holding movement and while releasing it. Test packaged gameplay and multiplayer if your game uses them.

| **What you see** | **What to check** |
| --- | --- |
| Normal jump instead of traversal | Recheck the pawn's setup rows, jump input, chooser and Traversable trace channel. Use the generated object Blueprint, not the original static mesh actor. |
| Object detected but no climb | Check height, usable depth, ledge width, headroom, landing room and available animations. Update an older chooser if the setup reports it. |
| Hands sit too high | Update the baked traversal animations if the import row requests it. Check the selected mesh and any custom rig that changes the pose. |
| Feet pull away or enter the object | Check Foot IK and Foot clearance rows, the target rig's compatibility, and the object's actual collision. |
| Latches or raised corners spoil a climb | Rebuild proxies with the side-shelf and top/ledge height controls. Check the visible result from each approach. |
| Proxy buttons unavailable | Stop Play. Use a writable Blueprint and read the button tooltip for inherited-proxy or selection conflicts. |
| Full import will not install | Read its preparation report. Check the source folder, saved target mesh, write access and whether the destination already belongs to a library. |
| Pose snaps at the end | Keep the montage slot connected to locomotion. Check custom code that stops montages twice, replaces the Animation Blueprint or resets its state. |

## Need more detail?

Use this guide for setup and troubleshooting. For detailed animation-selection adjustments, see the [Chooser reference](assets/downloads/chooser-reference.pdf).

When asking for help, include your Unreal version, movement backend, pawn and mesh names, the row's message, and the smallest steps that reproduce the problem. Keep your project backup until your own gameplay checks are complete.
