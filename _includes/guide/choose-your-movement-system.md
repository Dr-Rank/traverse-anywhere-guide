GASP & Traverse Anywhere's final-release plan gives **Character Movement (CMC), GMC, Network Prediction Mover and Chaos Mover** equal standing. Choose the movement system your game uses; each has its own integration and planned full-animation setup.

<div class="notice dependency"><strong>GMC requires a separate purchase.</strong> General Movement Component (GMC) is a paid third-party product. You must purchase a compatible GMC version and install and enable it before GASP & Traverse Anywhere can work with GMC. GMC is not included with GASP & Traverse Anywhere. The other three movement routes do not require GMC.</div>

| Movement system | Choose it for | Requirements and setup |
| --- | --- | --- |
| **Character Movement (CMC)** | Unreal's Character-based movement | Native CMC character with its own extras adapter; the complete extras suite, including animated slides, now passes. [CMC update](#cmc-extras). |
| **GMC** | A project built around General Movement Component | Separately purchased and installed **GMC**, plus compatible **GMCMotion** and **GMCAbilitySystem (GMAS)**. See [GMC setup](#prepare-a-gmc-project). |
| **Network Prediction Mover** | A Mover pawn using Network Prediction | Mover and Network Prediction, with TA's native NP integration. A dedicated full-animation choice is part of the final setup plan. |
| **Chaos Mover** | A Mover pawn using Chaos physics | Mover and Chaos Mover, with TA's native Chaos integration and its required physics settings. |

**Network Prediction Mover and Chaos Mover are distinct choices.** Their movement, prediction and physics requirements differ; choosing one does not install the other as a fallback. Mover remains experimental in the engine version covered by this guide.

## The same feature goals, native movement underneath

All four routes are in scope for traversal, full GASP animation setup, the optional extras and first-person presentation. A shared feature set does not mean identical physics or network timing. Your chosen backend retains responsibility for movement and prediction.

Use [existing-character setup](#set-up-an-existing-character) to keep your locomotion, or [full animation setup](#create-a-character-with-full-animations) for a generated character. Check [release progress](#final-release-scope) for what is implemented and what still needs final integration.
