---
type: realm
locations:
 - "[[Feywild]]"
displayLink: "[[Prismeer]]"
---

![[banner.jpg|banner]]

---

###### Prismeer
<span class="sub2">:RiGlobalLine: Realm (world)</span>

---

> [!recite|clean no-t]
>	Introduction for players
>^IntroText

### Description
Description of realm

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
FROM "Compendium/Atlas/Feywild/Prismeer" AND [[#]]
WHERE file.name != this.file.name
SORT file.name ASC
>
>> [!note]- HISTORY
>>```dataview
LIST WITHOUT ID displayLink
FROM "Session Notes" AND [[#]]
SORT file.ctime DESC