## Open the setup window

Open **Tools > GASP & Traverse Anywhere** from the level editor, or press **GASP & Traverse Anywhere** on the toolbar of a pawn Blueprint. The setup window lists every check and fix for the chosen pawn. Experienced users can work from it directly; the guided setup is optional.

Press **Help me choose: guided setup** to answer seven short questions. **Nothing is generated or changed while you answer.** You can go back at any time, and Cancel returns you to the setup window with your manual controls intact.

## The seven questions

| **Step** | **Question** | **What it decides** |
| --- | --- | --- |
| 1. Starting point | Where are you starting? | Keep an existing pawn Blueprint, or create a new pawn from a skeletal mesh. |
| 2. Animation system | Which animation setup do you want? | Keep your locomotion and add traversal, or use full GASP motion matching in a separate generated pawn. |
| 3. Pawn and skeleton | Which pawn will you use? | The actual pawn or mesh. Its skeleton is detected for you. |
| 4. Movement | How should your pawn move? | Character Movement (CMC), Network Prediction Mover, Chaos Mover or General Movement Component (GMC) for a new pawn. An existing pawn keeps its movement. |
| 5. Perspective | What will the player see? | Third person, or first person with an owner-only body. |
| 6. Optional extras | Which extras would you like? | Slide, ragdoll and get-up, physical hit reactions, paired interactions, camera limits. |
| 7. Review | Your setup, at a glance | A summary. **Use this setup plan** returns it to the setup window. |

## Keep your locomotion, or use full GASP

These are two different routes, and the wizard asks about them separately from movement:

- **Keep my locomotion and add traversal** uses your current Animation Blueprint and locomotion. Traversal animations play through a montage slot and hand back to your locomotion afterwards. Nothing about your walking, running or idle is replaced.
- **Use full GASP motion matching** prepares a complete GASP animation library for your mesh and installs it in a **separate generated pawn**. You preview and verify it before installation, and your existing gameplay pawns are kept.

Both routes can use the GASP traversal animations. Only the second adopts GASP locomotion and motion matching.

## Choose a pawn, not a skeleton preset

Pick the pawn Blueprint (or, for a new pawn, the skeletal mesh) you want in game. To keep your locomotion you must start from an existing pawn Blueprint: a mesh alone has no locomotion to preserve, and the wizard says so and holds you on that step. The wizard reads the mesh and skeleton from it and shows them, so you never have to guess a skeleton preset. Meshes such as Manny and Quinn can share one skeleton; choose the mesh you actually want to see.

## Movement

For a **new** pawn, choose a movement system. If you have no particular framework in mind, **Character Movement (CMC)** is the simplest starting choice.

| **Choice** | **When to pick it** |
| --- | --- |
| Character Movement (CMC) | Unreal's standard character movement. Recommended when you are unsure. |
| Network Prediction Mover | Mover using Network Prediction, for a project already designed around that framework. |
| Chaos Mover | Physics-driven Mover using Chaos, for a physics-based movement project. |
| General Movement Component (GMC) | Use your installed GMC movement framework. GMC plugin is required. GMC is a separate paid purchase; see [GMC prerequisites](#prepare-a-gmc-project). |

An **existing** pawn keeps its movement. The wizard never swaps movement components on a pawn you already have; to try another system, go back and choose a new pawn.

## First person

First person works with the full GASP route **and** with a compatible locomotion setup of your own. Choosing it never overwrites your third-person pawn; the setup window checks support before creating a separate first-person variant.

**With your own locomotion, turn-in-place is your responsibility.** The full GASP route includes it. With your own locomotion you must implement and manage turning in place yourself; Traverse Anywhere does not add turn-in-place animations to that system. The wizard repeats this warning on the review page whenever it applies.

## Optional extras

Start with only what your game needs. Every extra is optional, and its required support appears in your plan:

- **Slide** adds slide movement and its animation transitions.
- **Ragdoll and get-up** lets the pawn fall physically and recover into animation.
- **Physical hit reactions** react to impacts without opting into standalone knockdown.
- **Paired interactions** coordinate actions between two pawns, including the recovery they need.
- **Camera limits** constrain first-person looking during supported actions. They apply to first person only, so the wizard asks you to choose first person or turn them off.

Ragdoll, hit reactions and paired interactions need **Physics Control** and a physics asset fitted to your mesh. Interactions also need recovery animations.

## After the wizard

**Use this setup plan** returns your answers to the setup window as a plan. It does **not** generate assets, change your GameMode or enable plugins, and a selected extra is not an installed feature until you apply it. The window shows your plan in one line, for example: *Keep existing movement, Third person, Extras: Slide*.

Then review the setup rows, choose the GASP source folder if one is needed, and preview before preparing or installing. Every manual control stays available.

## Save when you are done

Fix and Fix all edit assets in memory. When any of the pawn, its Animation Blueprint, chooser or contact data is still unsaved, the result message ends with a reminder that names them, for example: *Not saved yet: BP_CMC, ABP_CMC. Save them (File > Save All, or Ctrl+S in its editor) so the changes survive reopening the project and are included in cooks.* Undo and autosave behave exactly as they normally do in Unreal.
