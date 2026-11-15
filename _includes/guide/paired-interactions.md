**Final-release feature plan · CMC / GMC / Network Prediction Mover / Chaos Mover**

Shove, tackle and takedown are part of the planned release. These are coordinated two-character actions, with matching participant animations and authoritative gameplay state.

| Interaction | What setup must provide |
| --- | --- |
| **Shove** | Suitable participant selection, paired animation and the target's reaction. |
| **Tackle** | Coordinated approach/contact, displacement and the resulting physical response. |
| **Takedown** | Matching attacker/target animation, transition into the intended downed state and appropriate recovery or control return. |

## Both participants matter

The system must select an eligible partner, assign roles and coordinate the action. A participant whose movement integration does not support interactions is excluded. Treat support for each backend as separate from **mixed-backend pairings**: arbitrary CMC/GMC/Mover combinations are not established by the handover.

The import needs the paired montages, interaction Pose Search assets, choosers and any required recovery animations. Retargeting only the attacker's clip is insufficient.

## Connect your game's rules

Use your own targeting, input and eligibility rules to decide when to request an interaction. Check refusal when a partner is unavailable or busy, interruption, completion and the return of movement/control. Decide how these actions affect health and death in your game.

## Multiplayer checks

Verify both characters from the server, owning clients and a remote observer. They should agree on the pairing and selected animation, then settle back into the intended gameplay state.

CMC has now passed the complete 22-case suite, including paired and network interaction cases. GMC and Chaos passed the latest shared-change regressions. NP's earlier suite passed, but its latest shared-change regression is under investigation. The final setup wizard and packaged feature combinations remain part of the release work. See [release progress](#final-release-scope).
