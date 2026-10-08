---
layout: default
guide: true
title: Property reference
permalink: /property-reference.html
---

These are the Traversable component settings. For the everyday workflow, start with [Adjust proxies and ledges](adjust-proxies-and-ledges.html).



## Setup

| Property | Default | Meaning |
|---|---|---|
| `bAutoConfigureCollision` | `true` | Set the owner's primitives to block the channel on register |
| `ExcludedComponentTags` | *(empty)* | Primitives with any of these tags are never configured, traced, read as a proxy source, or counted as generated proxies |

## Ledge

| Property | Default | Meaning |
|---|---|---|
| `MinLedgeWidth` | `60 cm` | Narrower ledges are rejected; found points are kept at least half this from a side edge, so a character does not float when traversing near a corner |
| `MaxLedgeSearchHeight` | `250 cm` | How far above the hit to search for a top surface |
| `MaxObstacleDepth` | `300 cm` | Past this depth the back ledge is reported invalid |

## Probe

| Property | Default | Meaning |
|---|---|---|
| `SurfaceInset` | `10 cm` | How far into the object the downward probe is offset, so it lands on the top face |
| `EdgeProbeDepth` | `5 cm` | How far below the top face the horizontal edge probes run |
| `MinTopSurfaceNormalZ` | `0.7` | Reject top surfaces steeper than this — too steep to stand on |
| `TraceChannelName` | `Traversable` | Trace channel the owner is made to block, by name. An object channel is warned about at runtime and refused by Generate Proxies |

## Height

| Property | Default | Meaning |
|---|---|---|
| `GroundTraceChannel` | `TraceTypeQuery1` (Visibility) | Used to find the ground beneath the obstacle. Safe as an index where `TraceChannelName` was not: the two built-in trace types are fixed ahead of any a project declares, so this is Visibility everywhere |
| `MaxGroundSearchDistance` | `1000 cm` | How far below the top surface to look for ground before giving up |

## Debug — editor only

| Property | Default | Meaning |
|---|---|---|
| `bShowHeightLabel` | `true` | The in-viewport climb-height label |
| `HeightLabelOffset` | `(0,0,20)` | Label offset above the owner's bounds |
| `bDrawDebugTraces` | `false` | Draw the ledge probes. **Transient** — never serialises into an asset |

## Traversable Proxy — editor only, used by Generate Proxies

| Property | Default | Meaning |
|---|---|---|
| `ProxyCellSize` | `2.5 cm` | Height-map cell size. Smaller follows the shape more closely and produces more boxes; very large objects may have the cell enlarged automatically to cap the map's size |
| `ProxySpikeFilterRadius` | `15 cm` | Features narrower than about twice this in every direction are flattened. `0` disables the filter; clamped to `200 cm` |
| `ProxyMinSideShelfDepth` | `60 cm` | Omit lower shelves beside a taller wall when their connected top cannot hold this square footprint. A rise over half this depth distinguishes the wall from a ramp. Standalone thin walls remain. `0` disables the filter |
| `ProxyHeightTolerance` | `5 cm` | Height spread allowed within one merged box — its top is always the highest cell in it, never an average |
| `ProxyMaxTopHeightError` | `5 cm` | Caps fitting tolerance against the filtered map. Raised corners remain separate. `0` restores legacy budget fitting |
| `ProxyMaxLedgeHeightError` | `2.5 cm` | Tighter top inflation limit near exposed footprint edges, including holes, through the top-probe inset plus two cells. Larger interior boxes can use the ordinary top tolerance. `0` disables the extra constraint; legacy top fitting also disables it. Rebuild existing proxies to apply |
| `ProxyMaxBoxes` | `16` | Preferred budget; retries cannot exceed Max Top Height Error. Accuracy takes priority and an over-budget fit is reported. More than 256 boxes is refused without replacing existing proxies |

Edited in the Blueprint only (`EditDefaultsOnly`; they do not appear on a placed instance), and read
from the **class defaults** when you press **Generate proxies**. Saved with the Blueprint like
any other property; editor-only data, so they are compiled out of packaged builds.

---

