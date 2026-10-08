---
layout: default
guide: true
title: "Set up an existing character"
permalink: /set-up-an-existing-character.html
---

## Choose your character

In the setup window, select the **pawn Blueprint** your game uses. Check that it has the intended skeletal mesh and Animation Blueprint. Traverse Anywhere checks the pawn's movement system and shows the rows relevant to it.

Use this route to add traversal while keeping your current walking, running and idle animations. Supported movement routes include **Character Movement (CMC)**, **Network Prediction Mover** and **Chaos Mover**. Mover is an experimental Unreal Engine system.

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
