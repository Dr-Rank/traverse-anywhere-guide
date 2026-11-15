## Choose your character

In the setup window, select the **pawn Blueprint** your game uses. Check that it has the intended skeletal mesh and Animation Blueprint. Traverse Anywhere checks the pawn's movement system and shows the rows relevant to it.

Use this route to add traversal while keeping your current walking, running and idle animations. The four movement routes are **Character Movement (CMC)**, **GMC**, **Network Prediction Mover** and **Chaos Mover**. Mover is an experimental Unreal Engine system.

**GMC requires a separately purchased and installed paid GMC plugin**, plus compatible GMCMotion and GMAS. Complete [GMC prerequisites](#prepare-a-gmc-project) before using that route. See [release progress](#final-release-scope) for final wizard and qualification work.

Keeping your locomotion does not automatically add the full GASP extras. Their planned generated-pawn setup is covered under [Optional GASP features](#optional-gasp-features); a custom pawn also needs the matching adapter, animation, physics and input integration.

## Read the setup results

| **Result** | **What to do** |
| --- | --- |
| Ok | This item is ready. |
| Fixable | Use Fix for this row, or Fix all to apply the available fixes. |
| Optional | Read the explanation and choose its Fix only if you want that change. Fix all leaves optional settings alone. |
| Info | Follow the row's guidance. This part needs your attention rather than an automatic edit. |
| Blocked | Resolve the reason shown, then check the pawn again. |
| Restart needed | Save your work and restart before continuing the affected checks. |

## Apply the fixes

Set the GASP folder, choose your traversal style, then use **Fix all** or work through individual **Fix** buttons. Read any confirmation carefully, especially when a shared skeleton will change. Check the rows again after setup finishes.

A custom jump graph or animation rig may need a small manual connection. Follow the row's explanation instead of replacing your whole graph. Start with a simple test level before integrating traversal into a larger gameplay system.
