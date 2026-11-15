**CMC extras now supported · verified development build**

The native CMC integration now passes the **complete 22-case extras gameplay suite**, including **all three slide behaviours with animation**. This is a substantial addition to the audited GASP 5.8 CMC character, which did not have a working slide setup.

| Feature | What CMC now supports in the qualified test build |
| --- | --- |
| **Requested slope slide** | Crouch-requested entry, animated sliding and release-to-stop. |
| **Automatic steep-slope slide** | Automatic entry on eligible slopes and animated recovery. |
| **Flat crouch slide** | Flat-ground slide, run-out, crouched speed exit and standing release exit. |
| **Ragdoll and recovery** | Knockdown, active ragdoll, physical get-up and return of control. |
| **Physical reactions and injuries** | The shared hit-reaction/injury system, including the tested injury cases. |
| **Paired interactions** | Shove, tackle and takedown, including standing, walking and running takedown cases. |
| **First-person presentation** | Head-camera behaviour through the tested physical actions and recovery. |
| **Multiplayer behaviour** | Server/owner/remote views, network ragdoll and paired cases, including the suite's lag/loss tests. |

## What GASP & Traverse Anywhere adds for CMC

The source audit found that GASP's CMC motion-matching setup did not select the slide databases, and its character had no slide movement. Existing slide-named animation states did not make it a working slide implementation.

The CMC integration now combines native slide movement with the Relaxed slide animation databases and the selection rules needed for entry, loop and exits. It adds those rules to the **Dense, Sparse and Extreme Sparse** CMC choosers and supplies the hand pose-history data needed by slide exits. The generated CMC animation set was checked to contain one Animation Blueprint, without importing the Mover character Blueprint.

**Remaining visual distinction:** the CMC slide plan identifies Mover-style body lean/alignment to the slope as separate work. The latest handover confirms animated slide support, but does not establish that slope-lean parity is complete.

This keeps CMC as the movement system. **Neither GMC nor a switch to a Mover pawn is required.**

## Verified support and remaining release work

The latest 15 November handover records **run 7351: 22/22 passed**, with the strict runner, no long-frame allowance and no long-frame warnings. Shared-change regression checks subsequently passed on GMC (**14/14**) and Chaos Mover (**22/22**).

The NP Mover regression was still under investigation in that handover. Additional CMC skeleton coverage, owner review, carrying the changes into the product, shared wizard integration and final packaging remain separate release steps. This result establishes the tested CMC extras support; it is not a declaration that every buyer installation or arbitrary custom CMC character is already qualified.

See [release progress](#final-release-scope) and [optional-feature setup](#optional-gasp-features).
