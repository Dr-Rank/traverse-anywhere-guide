**Extra · CMC / GMC / Network Prediction Mover / Chaos Mover**

Three slide behaviours are included. The movement system handles its own prediction and replay.

| Slide type | Behaviour |
| --- | --- |
| **Requested slope slide** | Crouch while sprinting on an eligible slope to start. Release crouch to end the slide. Entry checks the slope and your speed. |
| **Automatic steep-slope slide** | Starts by itself on a slope steep enough, without a crouch request, and recovers into animation when the slope eases. |
| **Flat crouch slide** | A GASP-style slide on flat ground when you crouch while running fast, followed by a run-out and an exit that suits your speed and stance. |

## Movement and animation

The slide keeps your approach momentum, follows the floor and feeds its slope to the animation. Entry, loop and exit clips match the style and stance: releasing crouch leads to a standing exit, holding crouch to a crouched exit.

**CMC:** the Game Animation Sample's own CMC character has no working slide. GASP & Traverse Anywhere adds native CMC slide movement and the selection rules for the slide animations, so all three slides work on CMC. CMC slides do not yet lean the body into the slope the way the Mover slides do.

Slide thresholds, steering, braking and exit conditions are tuned per backend. Stopping distances differ between CMC, GMC, Network Prediction Mover and Chaos Mover.

## First-person view

In first person the camera follows the animated head through the slide. With the **Camera limits** extra, look angles are limited during the slide, eased in and restored on exit, so normal camera movement is never left constrained.

## Check it in your project

Try each slide separately: a slope request, an automatic steep slope and a flat run-out. Repeat with early release, held crouch, a ledge exit and a blocked approach. Check the owner's and another player's view for stance, speed and the transition back to locomotion.
