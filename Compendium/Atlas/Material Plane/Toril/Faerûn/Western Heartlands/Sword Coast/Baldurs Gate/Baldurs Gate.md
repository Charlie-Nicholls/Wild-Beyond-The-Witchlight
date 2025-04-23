---
type: locale
locations:
  - "[[Sword Coast]]"
displayLink: "[[Baldurs Gate]]"
---

![[imgBaldursGate.webp|banner]]
###### Baldurs Gate
<span class="sub2">:FasCity: City</span>

___

>[!recite|clean no-t]
>	Introduction for players
>^IntroText

### Description
Baldur's Gate, also called simply the Gate, is the largest metropolis and city-state on the Sword Coast, within the greater Western Heartlands. It is a crowded city of commerce and opportunity, perhaps the most prosperous and influential merchant city on the western coast of [[Faerûn#Faerûn]]. Despite its long-standing presence as a neutral power, the leaders of Baldur's Gate are members of the Lords' Alliance of powers in the west.

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
FROM "Compendium/Atlas/Material Plane/Toril/Faerûn/Western Heartlands/The Sword Coast/Baldurs Gate"  AND [[#]]
WHERE file.name != this.file.name
SORT file.name ASC
>
>> [!note]- HISTORY
>>```dataview
LIST WITHOUT ID displayLink
FROM "Session Notes" AND [[#]]
SORT file.ctime DESC