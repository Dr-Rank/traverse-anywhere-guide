**Extras · CMC / GMC / Network Prediction Mover / Chaos Mover**

## Knockdown, ragdoll and get-up

The server knocks the pawn down into an active ragdoll, and the pawn recovers with a physical get-up into a pose-selected animation. Body, movement capsule and animation hand control back together, so getting up never leaves the pawn offset or unable to move.

Get-up animations are chosen from face-up and face-down clips using pose history. The target mesh needs a fitted physics asset, the Physics Control profile and the retargeted recovery library, all of which full animation setup prepares.

**Players** get up by pressing the get-up input once they are still on the floor; **AI pawns** get up by themselves after a short delay. Both are settings on the ragdoll component.

## Hit reactions and injuries

Physical hit reactions work **without a full knockdown**: the hit limb reacts and the pawn keeps control. Hits add up, so enough of them in a short time knock the pawn down. The injury type (Limp, Stunned, Head Face, Head Back, Body Front, Groin) changes how strongly the body follows its animation and how it recovers.

Connect reactions to your damage code with **Add Hit Impulse**, or knock a pawn down directly with **Trigger Ragdoll**. Both run on the server. See the [Blueprint reference](#blueprint-reference). GASP & Traverse Anywhere does not define your game's health, damage balance or respawn rules.

## Death ragdolls

Call **Trigger Death Ragdoll** from your game's authoritative death logic. A dead pawn becomes a limp ragdoll that never takes the get-up path. GMC pawns using GMAS do this from their death state automatically; CMC and Mover pawns do not need GMAS.

## First-person recovery

In first person the camera follows the real, physics-driven head through reactions, ragdoll and getting up. The view stays within a window around the head, so a headless first-person body never shows its own neck, then turns toward the get-up direction and returns smoothly to normal control.

## Check the mesh you ship

Test reactions with and without knockdown, face-up and face-down recovery, death, interruptions and equipment attachments. Check hands, knees and feet on each mesh and physics asset, then test owner, server and remote-player views, with lag and packet loss if your game is networked. A compatible skeleton alone does not prove physical contact on every body shape.
