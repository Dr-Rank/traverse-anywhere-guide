**Final-release feature plan · CMC / GMC / Network Prediction Mover / Chaos Mover**

Three slide behaviours are included in the plan. Choose the trigger model that fits your game; the movement system handles its own prediction and replay.

| Slide type | Intended behaviour |
| --- | --- |
| **Requested slope slide** | Crouch while sprinting on an eligible slope to start. Release crouch to end the requested slide. Entry checks use slope and speed. |
| **Automatic steep-slope slide** | Enter a slide when the configured steep-slope conditions are met, without a crouch request. This has its own automatic-entry rules. |
| **Flat crouch slide** | A GASP-style slide on suitable flat ground, followed by run-out and an exit appropriate to speed and stance. |

## Movement and animation

The slide system is designed to retain approach momentum, follow the floor and feed its slope to the animation. Entry, loop and exit clips must match the selected style and stance. Releasing a requested slide should lead to the correct standing exit; holding crouch can lead to a crouched exit.

Slide thresholds, steering, braking and exit conditions must be tuned with the chosen backend. Do not assume identical stopping distance between CMC, GMC, Network Prediction Mover and Chaos Mover.

## First-person view

The planned first-person setup follows the animated head during sliding and can restrict look angles. Limits should ease in and restore on exit, so a slide does not leave ordinary camera movement constrained.

## Check it in your project

Try each enabled trigger separately: a slope request, an automatic steep slope and a flat run-out. Repeat with early release, held crouch, a ledge exit and a blocked approach. Check the owner and another player's view for stance, speed and the transition back to locomotion.

See [release progress](#final-release-scope) for backend qualification and [optional setup](#optional-gasp-features) for the planned wizard.
