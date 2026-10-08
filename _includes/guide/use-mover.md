## Select the actual pawn

The setup detects the pawn's backend and shows the relevant requirements. The supplied plugin contains the Mover integrations; enable **Traverse Anywhere** rather than installing extra older adapter plugins.

## Chaos setup rows

| **Row** | **What to do** |
| --- | --- |
| Async physics | Apply the required physics and prediction settings. Follow any restart advice before multiplayer testing. |
| Stable physics playback | Apply the row to support steady playback with uneven render frame times. It changes a project-wide setting, saves a backup and requires a restart. |
| Physics step rate | Optional. Read the trade-off before choosing a rate; Fix all leaves it alone. |
| Movement plugin | Enable Traverse Anywhere and restart if the integration is not loaded. |
| Chaos startup input | Apply the supported backend fix. A custom backend may need manual integration to preserve its own behaviour. |

Save before changing project-wide physics settings. If a row remains blocked after restart, read its reason: platform configuration or a higher-priority override can change the effective setting.

## Test in your game

Check approach, traversal and stopping with the frame rates you expect players to use. Test multiplayer views as well as the owning player. A custom Chaos pawn may need its normal braking settings tuned for a comfortable stop.

On remote Chaos pawns, the displayed mesh follows the traversal path and blends back to the corrected capsule. Gameplay collision still uses the capsule. Keep damage, overlaps and other gameplay checks tied to the intended collision representation.
