**Planned setup · added to the release plan on 15 November 2026**

Use GASP & Traverse Anywhere's retargeting work for animations you bring into your project, as well as the GASP library. The planned wizard step accepts **animation sequences or montages** and reuses the TA retargeter already prepared for a supported source/target skeleton pair.

## Planned workflow

1. Set up the relevant skeleton pair through GASP & Traverse Anywhere's import process.
2. Select the source animations, including assets outside the GASP folders.
3. Choose the source and target skeletons from the sets TA has already prepared.
4. Choose a destination folder and run the offline batch.
5. Inspect the output on your actual target mesh before using it in gameplay.

If no TA retargeter exists for the selected pair, the step should refuse with an explanation. This is not a promise of automatic support for every arbitrary skeleton.

## Corrections reused from the import

| Retargeting work | Purpose |
| --- | --- |
| Finger retargeting | Preserve useful finger posing on supported rigs. |
| IK-bone pinning | Keep the IK reference bones aligned with their intended targets. |
| Hand-contact correction | Retain authored hand contact more accurately. |
| Knee-contact correction | Improve knee contact in poses such as physical recovery. |
| Absolute vertical pelvis motion | Preserve authored climb height instead of scaling it away. |

The step uses the same retargeter and batch path as the existing import, rather than creating a different set of rules for your own clips.

## Source assets and verification

Retargeting is **offline only** and produces assets for the target skeleton. It must never overwrite your source animations. The planned operation is repeatable and undoable, with a chosen output folder.

This wizard step and its non-GASP animation checks are still pending. Final qualification calls for a non-GASP animation on each supported skeleton, including finger, hand and knee checks. Animation quality still depends on the source motion, target proportions and rig.
