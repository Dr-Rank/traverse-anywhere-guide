**Final-release feature plan · CMC / GMC / Network Prediction Mover / Chaos Mover**

## Knockdown, ragdoll and get-up

The planned extras provide server-authoritative knockdown and active ragdoll, with physical recovery and pose-selected get-up animations. The body, movement capsule and animation must hand control back together so that getting up does not leave the pawn offset or unable to move.

Get-up selection uses the available face-up/face-down animations and pose history. The target mesh needs a suitable physics asset, PhysicsControl profile and the retargeted recovery library.

## Hit reactions and injuries

Physical hit reactions can be enabled **without a full knockdown**. Injury-state strength changes control how strongly the body follows its animation, allowing different physical responses rather than forcing every hit into ragdoll.

Connect reactions and injury changes to your game's damage/event logic. Traverse Anywhere's physical response does not define your game's health, damage balance or respawn rules.

## Death ragdolls

Death-ragdoll integration belongs to the extras scope. Trigger it from your game's authoritative death logic; a dead character must not take the ordinary get-up path. GMC's integration uses its GMAS-aware component, while CMC and Mover do not require GMAS.

## First-person recovery

The intended first-person view follows the actual animated or physics-driven head during physical reactions, ragdoll and getting up. Recovery aligns the view with the get-up direction and returns smoothly to ordinary camera behaviour. Camera limits apply to the local player's view.

## Check the mesh you ship

Test reactions both with and without knockdown, face-up and face-down recovery, death, interruptions and equipment attachments. Verify hands, knees and feet on each mesh and physics asset, then test owner/server/remote-player views under lag and packet loss. Skeleton compatibility alone does not prove physical contact on every body shape.

[Release progress](#final-release-scope) distinguishes completed backend work from the remaining CMC and wizard qualification.
