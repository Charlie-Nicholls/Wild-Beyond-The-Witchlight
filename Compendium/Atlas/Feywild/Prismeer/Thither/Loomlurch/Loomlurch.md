---
type: locale
locations:
 - "[[Thither]]"
displayLink: "[[Loomlurch]]"
---

![[imgLoomlurch.png|banner]]
###### Loomlurch
<span class="sub2">:RiBuilding4Fill: Town</span>

---

> [!recite|clean no-t]
>	Introduction for players
>^IntroText

### Description
A fallen tree in the forest that has been hollowed and and is now the home of [[Skabatha Nightshade]].

### Market
Here various goblin stall sell magical chocolates with interesting effects. Can be bought with trinkets.

### Parlor
Where [[Skabatha Nightshade]] held a meeting with [[Thalia Evergreen|Thalia]] and [[David Dennis]].

### Workshop
Children toil away making toys under the watchful gaze of monsters in the shadows.

### Tower One
Contains two patrolling soldiers and dormitories.

### Corridor
Connects Tower One with Tower Two. One side room has the [[Pig Mask Girl]] imprisoned. Another contains a treasure trove of trinkets including an empty hourglass.

### Tower Two
Bottom floor contains 5 portraits, of the three members of the [[Hourglass Coven]], [[]] and [[]]. Upper floor has two more guards.

### Kitchen
[[Skabatha Nightshade|Scabatha]]'s pet dragon hangs out here, [[Mishka]] is cleaning and a cell in the floor contains an unknown person.

### Tower Three
Bottom floor is [[Skabatha Nightshade|Scabatha]]'s Study and the upper floor contains her bed, dollshouse, crib and moth jar.

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
FROM "Compendium/Atlas//Loomlurch" AND [[#]]
WHERE file.name != this.file.name
SORT file.name ASC
>
>> [!note]- HISTORY
>>```dataview
LIST WITHOUT ID displayLink
FROM "Session Notes" AND [[#]]
SORT file.ctime DESC