---
type: continent
locations:
 - "[[Toril]]"
displayLink: "[[Faerûn]]"
---

![[Faerûn.jpg|banner]]
###### Faerûn
<span class="sub2">:FasEarthAmericas: Continent</span>
___

>[!recite|clean no-t]
>	Introduction for players
>^IntroText

### Description
Faerûn is a major continent on the planet of [[Toril#Toril]]. The word "Faerûn" was a modified version of "Faerie", the name of the homeland of ancient elves. The continent includes terrain that is as varied as any other. Besides the exterior coastline to the west and south, the most dominant feature on the continent is the Sea of Fallen Stars. This is an irregular inland sea that keeps the interior lands fertile, connects the west and east regions of Faerûn, and serves as a major trade route for many of the bordering nations.
 
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
