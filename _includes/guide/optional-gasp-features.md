**All four movement systems · new pawns only**

The extras are opt-in and **off by default**. You choose them for a **new** pawn, either in [wizard step 6](#use-the-setup-wizard) or under **Extras for the new pawn (optional)** in [Full animation setup](#create-a-character-with-full-animations). Leaving them all unticked gives you base traversal and locomotion only.

| Extra | What it adds | Read more |
| --- | --- | --- |
| Slide | Slide movement for your backend and its animation states and transitions. | [Slides](#slides) |
| Ragdoll and get-up | Knockdown, active ragdoll, pose-based recovery, death ragdolls and the components that return control. | [Ragdoll and physical reactions](#ragdoll-and-physical-reactions) |
| Physical hit reactions | Physics Control reactions and injury strength, without a full knockdown. | [Ragdoll and physical reactions](#ragdoll-and-physical-reactions) |
| Paired interactions | Shove, tackle and takedown animations, participant coordination and the recovery they need. | [Paired interactions](#paired-interactions) |
| Camera limits (first person) | Limits first-person looking during slides and knockdowns, restored when normal control returns. | [First-person camera functions](#first-person-camera-blueprint) |

## Choose carefully

**Extras are built into the new pawn when it is created and cannot be added or removed later.** To change them, set up a new pawn. An existing pawn that keeps its own locomotion gets no extras; the setup window and the wizard both say so.

If an extra cannot be generated for your choice of movement system and mesh, Full animation setup shows the reason in amber under the checkboxes. Setup never silently switches your pawn to another movement system to make an extra work.

## What the extras need

- **Ragdoll, hit reactions and interactions** need the **Physics Control** plugin and a physics asset fitted to your mesh. Interactions also need recovery animations, which they bring with them.
- The generated Animation Blueprint carries the ragdoll and get-up, slide and interaction states, montage playback and pose history. Copying animation files alone does not complete the setup.
- **Your game** still decides when things happen: damage and death, which input triggers an interaction, and what a knockdown means for scoring. Connect them with the [Blueprint reference](#blueprint-reference).

## Test each extra

Test each extra on its own and in the combinations you intend to ship, including with all extras off. Cover third and first person, the meshes and physics assets you ship, and server, owner and remote-player views, with lag and packet loss if your game is networked.
