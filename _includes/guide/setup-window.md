Open **Tools > GASP & Traverse Anywhere** to start [guided setup](#use-the-setup-wizard). Choose **Advanced tools** on the first page if you want to inspect or repair a pawn manually.

## Advanced tools

| Area | What it does |
| --- | --- |
| **Guided setup** | Returns to the main wizard. |
| **Choose a pawn** | Select a **Pawn Blueprint**, the source **GASP project** folder, and the **Import to** folder. The pane shows the resolved mesh, skeleton and Animation Blueprint. |
| **Full animation setup: create a new pawn** | The manual route for previewing, preparing and installing a GASP library. The wizard handles these stages when you choose full GASP. |
| **Retarget your own animations...** | Opens the [retarget dialog](#retarget-your-own-animations) for animations selected in the Content Browser. |
| **Check or repair this pawn** | Shows one row per relevant check. Read the row and choose **Apply** for a specific change. **Apply required changes** handles the required rows. **Check again** refreshes the results. |
| **Create a first-person variant manually** | Creates a separate first-person pawn from an already configured pawn. |

## Read the checks

| Label | What to do |
| --- | --- |
| **Ready** | The check passed. |
| **Action needed** | Read the proposed change and choose **Apply** if you want to make it. |
| **Needs attention** | Follow the row's instructions, then choose **Check again**. |
| **Optional** | Choose **Enable** only if you want the change. For example, you can opt in to traversal on GASP sample level blocks. |
| **Info** | Read the guidance. Some custom graphs need a manual connection. |
| **Restart needed** | Save your work, reopen the project, then return to the check. For guided setup, choose **Continue setup**. |

Advanced actions that leave unsaved assets list them in the result. Save those assets before closing the editor so the changes survive reopening and are available to packaged builds.
