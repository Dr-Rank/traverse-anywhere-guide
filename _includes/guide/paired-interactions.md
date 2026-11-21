**Extra · CMC / GMC / Network Prediction Mover / Chaos Mover**

Shove, tackle and takedown are coordinated two-character actions, with matching animations for both participants and server-authoritative state.

| Interaction | What happens |
| --- | --- |
| **Shove** | The target is pushed and reacts physically. |
| **Tackle** | A coordinated approach and contact, displacement and the resulting physical response. |
| **Takedown** | Matching attacker and target animations, a transition into the downed state, then recovery and return of control. |

The initiator stays in control. The target is out of control until it has recovered; **Is Out Of Player Control** tells your code when.

## Both participants matter

The plugin picks an eligible partner in front of the initiator (within 2 m, 50 cm up or down, 60° either side, unobstructed), assigns roles and plays both sides from the best-matching paired animation for the initiator's speed. A participant whose movement integration does not support interactions is skipped.

Interactions are tested between two pawns **of the same movement system**. Mixed pairings, such as CMC against GMC, are not established.

## Connect your game's rules

Trigger an interaction from input with **Request Interaction**, or from server code with **Try Interaction**. Your game decides when it is allowed (targeting, teams, cooldowns) and what it means for health and death. Check refusal when no partner is available or the partner is busy, interruption, completion and return of control. See the [Blueprint reference](#blueprint-reference).

## Multiplayer checks

Watch both characters from the server, both owning clients and a remote observer. They should agree on the pairing and animation, then settle back into normal gameplay.
