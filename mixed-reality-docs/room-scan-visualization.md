---
title: Room scan visualization
description: Applications that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.
author: mattzmsft
ms.author: alexpf
ms.date: 2/28/2018
ms.topic: article
keywords: Windows Mixed Reality, App patterns, design, HoloLens, room scan, spatial mapping, surface reconstruction, mesh
---



# Room scan visualization

Applications that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active. The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.

To ensure useful spatial mapping data, applications developers have several options:
* Rely on what may have already been collected. This data may be incomplete initially.
* Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience. They can use air-tap to confirm that all the necessary area is known to the device.
* Build a custom exploration experience in their own application.

Note that in all these cases the actual data gathered during the exploration is stored by the system and the application does not need to do this.

## Device support

<table>
<tr>
<th>Feature</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td> Room scan visualization</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>



## Building a custom scanning experience

Applications may decide to analyze the spatial mapping data at the start of the experience to judge whether they want the user to perform additional steps to improve its completeness and quality. If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:
* How much of the total volume in the users vicinity needs to be part of the experience
* Where the user should go to improve data

Users do not know what makes a "good" scan. They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, etc. The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.

In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.

## Cached versus continuous spatial mapping

The spatial mapping data is the most heavy weight data source applications can consume. To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.

Active scanning during an experience can be both beneficial or detrimental and the developer will need to decide which method to use based on the experience.

### Cached spatial mapping

In the case of cached spatial mapping, the application typically takes a snapshot of the spatial mapping data and uses this snapshot for the duration of the experience.

**Benefits**
* Reduced overhead on the system while the experience is running leading to dramatic power, thermal and cpu performance gains.
* A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.
* A single one time cost on any post processing of the spatial data for physics, graphics and other purposes.

**Drawbacks**
* The movement of real world objects or people is not reflected by the cached data. E.g. the application might consider a door open when it is actually closed now.
* Potentially more application memory to maintain the cached version of the data.

A good case for this method is a controlled environment or a table top game.

### Continuous spatial mapping

Certain applications may rely on continues scanning to refresh spatial mapping data.

**Benefits**
* You don't need to build in a separate scanning or exploration experience upfront in your application.
* The movement of real world objects can be reflected by the game, although with some delay.

**Drawbacks**
* Higher complexity in the implementation of the main experience.
* Potential overhead of the additional processing for graphic or physics as changes need to be incrementally ingested by these systems.
* Higher power, thermal and CPU impact.

A good case for this method is one where holograms are expected to interact with moving objects, e.g. a holographic car that drives on the floor may want to correctly bump into a door depending on whether it is open or closed.

## See also
* [Spatial mapping design](spatial-mapping-design.md)
* [Coordinate systems](coordinate-systems.md)
* [Spatial sound design](spatial-sound-design.md)
