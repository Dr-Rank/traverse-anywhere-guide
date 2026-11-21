Make copies of **your own** Animation Sequences and Montages for another skeleton, with the same retargeting GASP & Traverse Anywhere uses for its own imports. **True offline retargeting, no runtime retarget layer:** you get new animation assets on the target skeleton, and your originals are never changed.

## Retarget animations

1. In the Content Browser, select one or more **Animation Sequences** and **Montages**, all on the same skeleton.
2. Right-click and choose **GASP & Traverse Anywhere > Retarget with Traverse Anywhere...**. You can also press **Retarget your own animations...** in the setup window (step 1), which uses the Content Browser selection.
3. Choose the **Target skeletal mesh**: the character the copies should play on. The **Output folder** and **Name suffix** fill in for you (by default `/Game/TraverseAnywhere/Retargeted/<TargetSkeleton>` and `_<TargetSkeleton>`). Change them if you like.
4. Press **Retarget**. The result line lists what was made; the Content Browser shows the new assets.

<div class="shots"><figure><img src="assets/images/retarget-01-menu.webp" alt="The Retarget with Traverse Anywhere entry in the Content Browser menu" width="290" height="682" loading="lazy"><figcaption><strong>Right-click.</strong> The entry appears for any selection of Animation Sequences and Montages.</figcaption></figure><figure><img src="assets/images/retarget-02-dialog.webp" alt="The retarget dialog with a target chosen" width="1000" height="560" loading="lazy"><figcaption><strong>Choose the target.</strong> Here two of the engine's Mover Example animations (UE5 Manny) onto the UE4 mannequin.</figcaption></figure></div>

![The result: two sequences and a montage retargeted and saved](assets/images/retarget-03-done.webp)

## What it does

- Builds a Traverse Anywhere retargeter for this **pair of skeletons**, in its own folder under `/Game/TraverseAnywhere/Retargeters/<Source>_To_<Target>`, and reuses it next time. You can open and tune it like any IK Retargeter.
- Bakes each animation with the corrections the imports use: **finger retargeting** (each finger bends as in the source, and on a planted hand its tip keeps the source's contact), **IK-bone pinning**, **hand contact correction**, **absolute vertical pelvis motion** (a climb or jump keeps its authored height) and **knee contact correction** (kneeling knees keep their floor contact).
- A **montage** brings the sequences it plays. Additive animations keep their additive settings, with their base pose retargeted too.
- The copies, the retargeter and its rigs are **saved**. An existing copy is never overwritten; a run that fails keeps nothing.

## Check the result

![Source (dark, UE5 Manny) and retarget (white, UE4 mannequin) at the same moments](assets/images/retarget-04-compare.webp)

![Hands close up: source (left), UE4 retarget (middle), UEFN retarget (right). Rows: vault hand plant from the front, the same plant from the side, idle](assets/images/retarget-05-hands-v2.webp)

Hands close up, with the same Mover Example clips: UE5 Manny (left) and the retargets on the UE4 mannequin (middle) and UEFN mannequin (right). Top: the vault's hand plant. Middle: the same plant from the side, which shows each joint's bend. Bottom: idle.

Each finger bends the same way as in the source; none is bent back. While a hand is planted (still on a surface), the fingertips also keep the source's contact: on this vault every UE4 fingertip lands within 0.5 cm of Manny's, where copying the bends alone left the thumb about 2 cm into the surface. A moving hand keeps the copied bends unchanged. Traverse Anywhere's own traversal and full animation imports use the same finger step; animations you imported before this build keep the earlier fingers until you import them again.

Play the copies on your character before using them in gameplay, especially hands, fingers, knees and feet. Quality depends on the source motion and on how different the two characters' proportions are. Above, the engine's Mover Example vault, crouch and jog on UE5 Manny (dark) and their retargets on the UE4 mannequin (white), at the same moments.

## Limits

- **Both skeletons must be ones Traverse Anywhere supports:** UE5 Manny and Quinn, UE4 Mannequin, UEFN Mannequin, and male and female Animan. Any other pair is refused with the reason.
- The animations must all be on **one skeleton**, and the target must be on a **different** one.
- Animation Sequences and Montages only; Blend Spaces and other animation assets are not converted.
- The animations' skeleton needs a mesh in the project (its preview mesh, or any mesh on it): the retargeter reads its reference pose.
- Knee contact correction is qualified on Manny targets; on other targets, check kneeling poses.
