---
layout: default
guide: true
title: "Features"
permalink: /features.html
---

Explore the tools for preparing characters, importing animations and making objects traversable.

Feature pictures illustrate the tools rather than showing exact gameplay frames. The supported-character picture uses renders of the original meshes, including the blue Animan male. Proxy overlays are hidden in gameplay.

## Character setup

### Guided character setup

See what is ready, fix supported setup rows individually or use Fix all. Backup reminders and confirmations identify shared changes; optional rows stay yours to choose.

![Illustration: Guided character setup](assets/images/11-guided-character-setup.webp)

### Traversal with your locomotion

Add traversal through a montage slot while keeping your character's normal locomotion. Supported jump setup tries traversal first and falls back to ordinary jump when no action can start.

![Illustration: Traversal with your locomotion](assets/images/12-keep-your-locomotion.webp)

## Animation libraries

### Full animation preparation

Prepare and verify a motion-matching library for your selected mesh, then install a generated CMC or Chaos Mover pawn, game mode and settings. Existing gameplay pawns are kept separate.

![Illustration: Full animation preparation](assets/images/13-full-animation-setup.webp)

### Supported skeleton libraries

Import baked traversal clips for Manny, Quinn, UE4, UEFN and male or female Animan. Multiple skeletons and differing mesh poses retain their own libraries without overwriting other targets.

![Illustration: Supported skeleton libraries](assets/images/14-skeleton-specific-libraries.webp)

## Styles and action selection

### Neutral and Relaxed styles

Choose Neutral or Relaxed traversal, then apply the chooser setup. Your selection is retained; some Relaxed actions intentionally reuse Neutral clips.

![Illustration: Neutral and Relaxed styles](assets/images/15-traversal-styles.webp)

### Pose selection and motion warping

A chooser uses approach, obstacle data and pose history to select hurdles, vaults, mantles and climbs. Motion warping adjusts supported clips to ledge and landing targets; grounded climb rows extend to 300 cm.

![Illustration: Pose selection and motion warping](assets/images/16-animation-selection-and-warping.webp)

## Contact and locomotion recovery

### Hand contact and leg clearance

Baked retargeting preserves authored hand-goal heights on supported rigs. Foot-clearance controls help keep legs clear of box collision, while setup gates ordinary foot IK and unwanted airborne poses during traversal.

![Illustration: Hand contact and leg clearance](assets/images/17-hands-and-foot-clearance.webp)

### Return to locomotion

Traversal uses the montage's blend-out to recover into walking or idle, including hybrid setups. Keep the slot connected to locomotion; custom code must preserve the animation graph through the handoff.

![Illustration: Return to locomotion](assets/images/18-blend-back-to-locomotion.webp)

## Objects and proxies

### One click object setup

Right-click a static mesh and choose Make Traversable. The new Blueprint includes its mesh, Traversable component, generated proxies and fitted Pawn collision, ready to drag into your level.

![Illustration: One click object setup](assets/images/01-one-click-setup.webp)

### Cleaner traversal surfaces

Fit simple boxes to detailed static meshes and supported assemblies, including instanced, spline and child-actor meshes. Traversal reads the fitted surfaces rather than relying on poor source collision.

![Illustration: Cleaner traversal surfaces](assets/images/02-clean-traversal-surfaces.webp)

### Local ledge heights

Raised corners stay local instead of lifting the entire top. Tighter edge fitting gives the traversal chooser and motion warping more representative ledge targets.

![Illustration: Local ledge heights](assets/images/03-local-ledge-heights.webp)

### Narrow spike filtering

Filter small isolated raised details without flattening long walls or rails. The filter radius is adjustable, so you can retain decoration when it matters to your design.

![Illustration: Narrow spike filtering](assets/images/04-filter-small-spikes.webp)

### Usable surface filtering

Omit shallow shelves beside taller geometry while retaining usable steps and standalone thin walls. Configure the required footprint; runtime room checks still decide whether the action is safe.

![Illustration: Usable surface filtering](assets/images/05-filter-unusable-shelves.webp)

### Fitted Pawn support

Optional physical proxies align Pawn support with the traversal shape. Make Traversable enables them automatically, replacing the source mesh's Pawn response while leaving its other responses available.

![Illustration: Fitted Pawn support](assets/images/06-fitted-pawn-collision.webp)

### Preserved source geometry

Keep the original static mesh asset, visual detail and non-Pawn collision responses. Traversal probes and the forward sweep use eligible generated proxies, avoiding competing source colliders.

![Illustration: Preserved source geometry](assets/images/07-preserve-other-collision.webp)

### Reusable runtime proxies

Calculate in the editor and reuse the saved components across Blueprint instances and packaged games. The game queries boxes without running the editor fitter; cost depends on the proxy count.

![Illustration: Reusable runtime proxies](assets/images/08-reusable-runtime-proxies.webp)

### Control over fitting

Adjust sampling, filters, top and ledge tolerances, and the preferred box budget. Accuracy limits take priority over the budget, so complexity reductions do not justify an arbitrarily inflated surface.

![Illustration: Control over fitting](assets/images/09-tune-the-fit.webp)

### Rebuild remove and undo

Rebuild the Blueprint's proxies after geometry or setting changes to update its instances. Generation is undoable; removing proxies restores source tracing and ends the fitted Pawn collision takeover.

![Illustration: Rebuild remove and undo](assets/images/10-rebuild-and-undo.webp)

## Movement and multiplayer

### Movement backend support

Use traversal with Character Movement, Network Prediction Mover or Chaos Mover. Relevant setup rows guide the backend requirements. Full animation setup offers CMC or Chaos Mover; Mover remains experimental in Unreal.

![Illustration: Movement backend support](assets/images/19-movement-backend-choice.webp)

### Multiplayer traversal playback

Supported backends coordinate traversal across owner, server and other players. Chaos remote-mesh replay improves displayed traversal recovery while gameplay collision remains on the capsule. Test your own network conditions.

![Illustration: Multiplayer traversal playback](assets/images/20-multiplayer-traversal.webp)

## Inspection and integration

### Ledge inspection and controls

Inspect estimated height labels and debug probes, then tune ledge width, search height, depth, surface inset and slope acceptance. Queries follow current object transforms and usable room still matters.

![Illustration: Ledge inspection and controls](assets/images/21-ledge-debugging.webp)

### Custom integration and events

Read front and back ledge data through Blueprint or C++ for your own traversal logic. Start and end events support cosmetics; animation helper nodes expose traversal state without replacing your usual values.

![Illustration: Custom integration and events](assets/images/22-custom-traversal-integration.webp)

