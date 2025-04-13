---
type: province
locations:
  - "[[Western Heartlands]]"
displayLink: "[[Western Heartlands]]"
---

![[imgSwordCoast.jpg|banner]]
###### The Sword Coast
<span class="sub2">:FasMap: Province</span>
___

>[!recite|clean no-t]
>	Introduction for players
>^IntroText

### Description
The Sword Coast, also nicknamed the Empty Lands, is the region in western [[Faerûn#Faerûn]] that lays along the coast of the Sea of Swords and extends inward into to the vale. It's an expansive tract of wilderness, dotted with independent cities and overrun by bands of monstrous creatures, that some see as merely a place through which you have to travel in order to reach an actual meaningful destination. It is much more than that of course. A rich and vibrant land with a long and storied history that encompassed some of the most important cities in all the Realms.

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
FROM "Compendium/Atlas/Material Plane/Toril/Faerûn/Western Heartlands/Sword Coast" AND [[#]]
WHERE file.name != this.file.name
SORT file.name ASC
>
>> [!note]- HISTORY
>>```dataview
LIST WITHOUT ID displayLink
FROM "Session Notes" AND [[#]]
SORT file.ctime DESC