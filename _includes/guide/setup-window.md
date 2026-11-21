The setup window is where every pawn change is made. It checks the chosen pawn, explains what is missing and applies the fixes you choose. **Nothing changes until you press a button that says so.**

![The setup window with a plan from the guided setup and Full animation setup expanded](assets/images/setup-window-plan.webp)

## What is on the screen

| Area | What it does |
| --- | --- |
| **Help me choose: guided setup** | Opens the [seven-question wizard](#use-the-setup-wizard). It only records a plan; you can skip it entirely. |
| **Your plan** (green) | Appears after the wizard: your movement system, view, animation route and extras. It also says *Nothing has been changed yet*. |
| **NEXT** bar | A one-line summary: how many checks need attention, need an action or are ready. |
| **01 Setup Wizard - Step 1: Choose your Pawn** | Pick the **Pawn Blueprint**, the **GASP project** folder and where imported clips go (**Import to**). The mesh, skeleton and Animation Blueprint read from the pawn are shown underneath. **Use Relaxed traversal animations** switches the traversal style. |
| **Full animation setup: create a new pawn** | Open when the window opens (a keep-your-locomotion plan folds it away). Use it to generate a new pawn with a complete GASP animation library: pick the movement system, the **Target skeletal mesh** and the extras, then **1. Preview changes**, **2. Prepare animation library** and **3. Install verified library**. See [full animation setup](#create-a-character-with-full-animations). |
| **02 Review and make changes to your current setup** | One row per check for the chosen pawn, each with its own **Apply** button. **If you are starting with a new pawn, don't follow these steps yet:** use the guided setup or Full animation setup in step 1 first. |
| **Apply required changes** / **Check again** | Apply every *required* change in one go, or re-run the checks after you have changed something yourself. |
| **First-person variant** | Further down: **Create first-person variant** once traversal setup is complete. See [first-person setup](#create-a-first-person-character). |

If your plan builds full GASP from an existing pawn, Full animation setup keeps that pawn's movement system: choosing another one shows an amber warning, and Preview and Prepare stay greyed out until the two match.

If you pick an engine or plugin pawn (for example one of the Mover examples), step 1 also shows **Copy into my project**. See [Copy an engine pawn into your project](#copy-into-project).

## Read the checks

![Setup checks for a CMC pawn](assets/images/setup-window-checks.webp)

| **Label** | **What it means** | **What to do** |
| --- | --- | --- |
| **Ready** | This part is set up. | Nothing. |
| **Action needed** | Setup can make this change for you. | Read the row, then press its **Apply**, or use **Apply required changes**. |
| **Needs attention** | Setup cannot continue this row yet. The row says why: usually another row must be applied first, or the asset is read-only. | Follow the row's text, then **Check again**. |
| **Optional** | A change that is your choice. | Apply it only if you want it. **Apply required changes skips it.** |
| **Info** | Guidance for something you have to do yourself, such as a manual connection in a custom graph. | Follow the row's guidance. |
| **Restart needed** | A project setting changed that only takes effect after a restart. | Save your work, restart Unreal, then **Check again**. |

Rows depend on each other. In the picture above, *Jump input* and *Chooser* need the *Traversal Action component* first, so applying that row turns them into **Action needed**.

## Save when you are done

**Apply** edits assets in memory. When the pawn, its Animation Blueprint, chooser or contact data are still unsaved, the result message names them, for example: *Not saved yet: BP_CMC, ABP_CMC. Save them (File > Save All, or Ctrl+S in its editor) so the changes survive reopening the project and are included in cooks.* Undo and autosave work as they normally do in Unreal.
