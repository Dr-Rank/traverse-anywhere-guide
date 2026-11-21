Press **Help me choose: guided setup** at the top of the setup window to answer seven short questions. **Nothing is generated or changed while you answer.** Back is always available, and Cancel returns you to the setup window with your manual controls exactly as they were.

The wizard follows one of two paths depending on your first answer. The [screens](#setup-wizard-screens-1) below walk through both.

## The seven questions

| **Step** | **Question** | **What it decides** |
| --- | --- | --- |
| 1. Starting point | Where are you starting? | Keep an **existing pawn Blueprint**, or **create a new pawn** from a skeletal mesh. |
| 2. Animation system | Which animation setup do you want? | **Keep my locomotion and add traversal**, or **Use full GASP motion matching** in a separate generated pawn. |
| 3. Pawn and skeleton | Which pawn will you use? | The actual pawn (or mesh). Its skeleton is read for you. The page also says where to find pawns and meshes. |
| 4. Movement | How should your pawn move? | For a new pawn: CMC, NP Mover, Chaos Mover or GMC. An existing pawn keeps its movement. |
| 5. Perspective | What will the player see? | Third person, or first person with an owner-only body. |
| 6. Optional extras | Which extras would you like? | Slide, ragdoll and get-up, physical hit reactions, paired interactions, camera limits. New pawns only. |
| 7. Review | Your setup, at a glance | A summary. **Use this setup plan** returns it to the setup window. |

## Path A: you already have a pawn

1. **Step 1:** choose **I already have a pawn Blueprint**.
2. **Step 2:** choose **Keep my locomotion and add traversal** to keep your walking, running and idle. Traversal plays through a montage slot and hands back to your locomotion afterwards. Or choose **Use full GASP motion matching** to build a separate generated pawn for your mesh; your pawn is only read.
3. **Step 3:** pick your pawn. The wizard shows its mesh, skeleton and the movement adapter it detected. Under **Where to find them** it lists your own pawns, the Game Animation Sample's `SandboxCharacter_CMC` and `SandboxCharacter_Mover` in `/Game/Blueprints`, and the engine's Mover example pawns.
   - If the pawn is **engine or plugin content** (such as `/MoverExamples/Pawns/ChaosMannyPawn`) and you are keeping its locomotion, the wizard asks you to **Copy into my project** before Next unlocks. See [Copy an engine pawn into your project](#copy-into-project).
4. **Step 4:** an existing pawn **keeps its movement**. The wizard never swaps movement components on a pawn you already have. To try another movement system, go back and choose a new pawn.
5. **Step 5:** third or first person.
6. **Step 6:** extras are built into a **new** pawn when it is created, so this page explains that no extras are added when you keep your pawn. To get them, go back to step 1 and choose **I want to create a new pawn**, or choose full GASP motion matching in step 2.
7. **Step 7:** review, then **Use this setup plan**.

## Path B: you want a new pawn

1. **Step 1:** choose **I want to create a new pawn**.
2. **Step 2:** **Use full GASP motion matching** is selected for you. *Keep my locomotion* is unavailable here, because a mesh on its own has no locomotion to keep; the page says so.
3. **Step 3:** pick the **skeletal mesh** you want to see in game. Manny and Quinn can share a skeleton while using different meshes, so pick the mesh, not a skeleton preset. The Game Animation Sample's meshes live in `/Game/Characters/UE5_Mannequins/Meshes`; the Mover examples' mesh is `/MoverExamples/Characters/Mannequins/Meshes/SKM_Manny_Simple`. Engine and plugin meshes can be used as they are: the new pawn and its animations are created in your project and the mesh is not changed.
4. **Step 4:** choose the movement system.

   | **Choice** | **When to pick it** |
   | --- | --- |
   | Character Movement (CMC) | Unreal's standard character movement. **Recommended when you are unsure.** |
   | Network Prediction Mover | Mover using Network Prediction, for a project already built around that framework. |
   | Chaos Mover | Physics-driven Mover using Chaos, for a physics-based movement project. |
   | General Movement Component (GMC) | Your installed GMC framework. GMC is a separate paid purchase; see [GMC prerequisites](#prepare-a-gmc-project). |

5. **Step 5:** third or first person.
6. **Step 6:** tick only the extras your game needs. **Please choose carefully:** extras are built into the new pawn when it is created and **cannot be added or removed later**. To change them, set up a new pawn. The review page lists the support each extra needs, such as Physics Control and a physics asset fitted to your mesh.
7. **Step 7:** review, then **Use this setup plan**.

## First person and turn in place

First person works with the full GASP route **and** with a compatible locomotion setup of your own. Choosing it never overwrites your third-person pawn: you create a separate first-person variant later in the setup window.

**With your own locomotion, turn in place is your responsibility.** The full GASP route includes it. With your own locomotion you implement and manage turning in place yourself; GASP & Traverse Anywhere does not add turn-in-place animations to that system. The wizard repeats this whenever it applies.

## Extras

| Extra | What it adds |
| --- | --- |
| **Slide** | Slide movement and its animation transitions. See [Slides](#slides). |
| **Ragdoll and get-up** | The pawn falls physically and recovers into animation. Needs a physics asset fitted to the mesh and Physics Control. |
| **Physical hit reactions** | Reacts to impacts without a full knockdown. Same physics requirements. |
| **Paired interactions** | Shove, tackle and takedown between two pawns, with the recovery they need. |
| **Camera limits** | Limits first-person looking during supported actions. Your Blueprint can also set its own limits; see [first-person camera functions](#first-person-camera-blueprint). |

## After the wizard

**Use this setup plan** returns your answers to the setup window as a green plan line, for example: *Your plan: Character Movement (CMC) \| First person \| Full GASP motion matching \| Extras: Slide, Ragdoll and get-up, Camera limits. Nothing has been changed yet.* The window also fills in the matching controls, such as the movement system and extras under **Full animation setup**.

The plan does **not** generate assets, change your GameMode or enable plugins. Next:

- **Keeping your pawn:** work through the checks in section 02 and apply them. See [Set up an existing character](#set-up-an-existing-character).
- **Full GASP / new pawn:** choose the **GASP project** folder, then **Preview**, **Prepare** and **Install** under Full animation setup. See [Create a character with full animations](#create-a-character-with-full-animations).
- **First person:** after traversal setup, press **Create first-person variant**. See [Create a first-person character](#create-a-first-person-character).
