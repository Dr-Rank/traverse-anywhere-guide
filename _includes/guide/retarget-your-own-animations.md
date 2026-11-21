<div class="notice dependency"><strong>Not in this build.</strong> This page describes a planned addition. The tester build does not include a step for retargeting your own animations yet. The retargeting described in <a href="#create-a-character-with-full-animations">full animation setup</a> and the traversal import is in this build.</div>

**True offline retargeting — no dynamic runtime retargeting.** The import already prepares GASP assets for your target skeleton to play directly. The planned step extends that to your own clips; it does not add a runtime retarget layer.

## Planned workflow

1. Set up the skeleton pair through GASP & Traverse Anywhere's import.
2. Select your source animation sequences or montages, including assets outside the GASP folders.
3. Choose the source and target skeletons from the pairs already prepared.
4. Choose a destination folder and run the offline batch.
5. Inspect the result on your actual target mesh before using it in gameplay.

If no retargeter exists for the selected pair, the step will refuse and explain why. It is not a promise of automatic support for every skeleton.

## Corrections it will reuse from the import

| Retargeting work | Purpose |
| --- | --- |
| Finger retargeting | Keep useful finger posing on supported rigs. |
| IK-bone pinning | Keep the IK reference bones aligned with their targets. |
| Hand-contact correction | Keep authored hand contact accurate. |
| Knee-contact correction | Improve knee contact in poses such as physical recovery. |
| Absolute vertical pelvis motion | Keep the authored climb height instead of scaling it away. |

Retargeting will be **offline only**, write to a folder you choose, and never overwrite your source animations.
