---
type: territory
locations:
 - "[[Faerûn]]"
displayLink: "[[Western Heartlands]]"
---

![[imgWesternHeartlands.jpg|banner]]
###### Western Heartlands
<span class="sub2">:FasMap: General Region</span>

___

>[!recite|clean no-t]
>	Introduction for players
>^IntroText

### Description
The Western Heartlands (originally "Hartlands" for the abundance of deer) is a region located in the western portion of [[Faerûn]]. It stretches from the [[Sword Coast]] region at water's edge of the Sea of Swords in the west, to the Storm Horn Mountains in the east. The region extends north until the Lizard Marsh of the Delimbiyr Vale, including the High Moor to the northeast, and went as far south to the Lands of Intrigue of Amn, Tethyr and Calimshan. 

---

> [!column|flex 3]
>> [!hint]-  NPCs
>>```dataview
LIST WITHOUT ID displayLink
FROM "Compendium/NPCs" AND [[#]]
SORT file.name ASC
>
>> [!example]- LOCATIONS
>>```dataview
LIST WITHOUT ID displayLink
FROM "Compendium/Atlas/Material Plane/Toril/Faerûn" AND [[#]]
WHERE file.name != this.file.name
SORT file.name ASC
>
>> [!note]- HISTORY
>>```dataview
LIST WITHOUT ID displayLink
FROM "Session Notes" AND [[#]]
SORT file.ctime DESC