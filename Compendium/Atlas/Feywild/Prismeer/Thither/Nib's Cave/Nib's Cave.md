---
type: locale
locations:
 - "[[Thither]]"
displayLink: "[[Nib's Cave]]"
---

![[banner.jpg|banner]]
###### Nib's Cave
<span class="sub2">:FasMound: Cave</span>

---

> [!recite|clean no-t]
>	Introduction for players
>^IntroText

### Description
Description of location

---

> [!column|flex 3]
>> [!hint]-  NPCs
>>```dataview
LIST WITHOUT ID displayLink
FROM "Compendium/NPCs" AND [[#]] OR "Compendium/Party" AND [[#]] 
> 
>> [!example]- LOCATIONS
>>```dataview
LIST WITHOUT ID displayLink
FROM "Compendium/Atlas//Nib's Cave" AND [[#]]
WHERE file.name != this.file.name
SORT file.name ASC
>
>> [!note]- HISTORY
>>```dataview
LIST WITHOUT ID displayLink
FROM "Session Notes" AND [[#]]
SORT file.ctime DESC