## Neutral or Relaxed

**Neutral** is the default style. Choose **Relaxed traversal** for the alternative authored set. Apply the **Chooser** row after changing style so the pawn uses that selection. Some Relaxed actions intentionally share Neutral clips.

## Import for your character

The importer reads the supported GASP project and creates traversal animations on your character's skeleton. The animations are baked during import, so traversal does not need runtime retargeting. Keep the source project available if you need to import again.

Generated clips normally appear under **Content/TraverseAnywhere/Traversal**, in a folder for the target skeleton. Meshes that need different reference poses receive separate libraries. Same-named skeletons are kept separate, and importing for another target preserves existing libraries.

You can set up more than one skeleton in the same project. Select and complete each pawn separately, then test each mesh. Reusing a skeleton does not automatically mean every mesh has the same proportions or reference pose.

Supported character families include UE5 Manny and Quinn, UE4 Mannequin, UEFN Mannequin and male/female Animan. Choose the actual mesh you intend to use; custom proportions and rigs still need a gameplay check.

## Update an existing setup

If the **Traversal animations** row reports that imported clips need updating, run its Fix again. This updates the baked animation assets; changing retarget settings alone does not update clips already imported.

Use the **Chooser** row to update an older generated chooser. The setup asks before changing an edited or different chooser and keeps numbered backups when rebuilding. Read the prompt before replacing your own selection rules.

## Adjust the chooser

The generated chooser selects among the imported traversal montages. To change its rules, open the chooser asset beside that target's clips and use the [Chooser reference](assets/downloads/chooser-reference.pdf) to understand the action, movement and obstacle conditions. Keep a copy before editing, and repeat your gameplay checks after changing a rule.

## Check the result

Try both walking and running approaches. Watch hands during their contact with the ledge, feet during landing, and the return to locomotion. The grounded climb chooser supports heights up to **300 cm**; usable depth, headroom and available animations also matter.
