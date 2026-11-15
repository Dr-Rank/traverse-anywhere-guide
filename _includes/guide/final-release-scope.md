**Final-release scope · updated from the latest 15 November 2026 handover**

This guide covers the intended final version as well as established traversal setup. Sections marked **Planned setup** describe work still to be completed. They are not a claim that those controls are already present in your installed build.

## What the final version is planned to include

| Area | Included in the release plan |
| --- | --- |
| Traversal and objects | Hurdles, vaults, mantles/climbs; automatic ledge queries; moving-object transforms; fitted proxies, collision, filters and editor diagnostics; planned camera-facing height markers and closer surface fitting. |
| Four movement systems | CMC, GMC, Network Prediction Mover and Chaos Mover, including dedicated full-animation setup choices. |
| Full animation setup | Locomotion, motion matching, pose history, choosers, Pose Search databases, mirroring, warping and supported skeleton libraries prepared with **offline retargeting, without dynamic runtime retargeting**. |
| Slides | Requested slope slide, automatic steep-slope slide and flat crouch slide, with entry, loop and exit animation. |
| Ragdoll and recovery | Active ragdoll, knockdown, physical/motion-matched get-up and death-ragdoll integration. |
| Physical reactions | PhysicsControl hit reactions without a full knockdown, plus injury-state strength changes. |
| Paired interactions | Shove, tackle and takedown with participant coordination and return of control. |
| Cameras and views | Third-person presentation and first-person head following through traversal, slides, physical reactions, ragdoll and get-up, with configurable look limits. |
| Setup and imports | Optional-feature selection, physics-asset checks, collision/tag configuration and the required animation, audio and input dependencies. |
| Your own animations | Offline retargeting of selected sequences or montages using an existing TA retargeter for the chosen skeleton pair. |

## Development progress, not a shipping declaration

| Movement system / work | Position in the 15 November handover |
| --- | --- |
| **CMC extras** | **Complete 22-case extras suite passed**, including all three animated slides, ragdoll/recovery, injuries, paired interactions and camera/network cases. Additional skeleton checks, owner review and product carry remain. [CMC feature update](#cmc-extras). |
| **GMC extras** | Completed extras work; the shared-change regression passed **14/14**. Final wizard integration and release packaging remain. |
| **Network Prediction Mover extras** | Earlier 22-case and additional skeleton checks passed and were carried. Regression of the latest shared CMC-related changes is **under investigation** following a first-person camera failure in the running takedown; the latest handover records a diagnostic run, not a pass. |
| **Chaos Mover extras** | Completed and carried, with additional skeleton checks. Regression of the latest shared changes passed **22/22**. Final wizard integration and release packaging remain. |

CMC's complete extras gameplay suite is now qualified in the lab. The open NP regression, additional CMC skeleton coverage, review/product carry, shared wizard, optional-feature generation/imports, user-animation retargeting, remaining Mover test failures and final packaging/documentation still need completion. Passing backend tests does not mean the complete buyer installation is release-qualified.

## Broader GASP coverage still being reconciled

The release plan also requires checking the full source inventory: locomotion and movement modes, animation/pose/chooser systems, foot IK and warping, cameras, Foley audio, input/configuration, and AI/SmartObject behaviour. Bench interactions, avoidance/look-at examples, flying and sample/debug functionality must be explicitly assessed rather than silently omitted. Their complete four-backend integration is **not yet confirmed** by the handover.

GASP assets are imported from the user's separately obtained project. All animation retargeting is offline. Independent ALS-style overlay exploration is a later investigation, outside the current release commitment.
