<%*
// ###########################################################
//                       Helper Functions
// ###########################################################

// Convert string to camelCase
function toCamelCase(str) {
  return str
    .replace(/(?:^\w|[A-Z]|\b\w|\s+|[-_])/g, (match, index) =>
      index === 0 ? match.toLowerCase() : match.toUpperCase()
    )
    .replace(/[\s-_]+/g, '');
}

// Return icon based on class
function getIcon(pClass) {
  const iconMappings = {
    Artificer: ':RiToolsFill: Specialist',
    Barbarian: ':LiAxe: Primal Path',
    Bard: ':FasGuitar: College',
    Cleric: ':FasPersonPraying: Divine Domain',
    Druid: ':FasMoon: Circle',
    Fighter: ':FasUserShield: Archetype',
    Monk: ':FasHandFist: Tradition',
    Paladin: ':FasFireFlameCurved: Oath',
    Ranger: ':FasBullseye: Conclave',
    Rogue: ':RiSwordFill: Archetype',
    Sorcerer: ':FasHandSparkles: Origin',
    Warlock: ':FasBurst: Patron',
    Wizard: ':FasWandMagicSparkles: Tradition'
  };

  return iconMappings[pClass] || ':FasCircleQuestion: Sub Class';
}

// ###########################################################
//                         Main Code
// ###########################################################

// Call modal form & declare variables
const result = await MF.openForm('PC');
const player = result.Player.value;
const pClass = result.pClass.value;
const subClass = result.subClass.value;
const subType = getIcon(pClass);
const name = result.Name.value;
const race = result.Race.value;
const lostThing = result.LostThing.value;

if (result.status === 'ok') {

    // Rename file & open in new tab; Fire toast notification
    await tp.file.rename(name);
    await app.workspace.getLeaf(true).openFile(tp.file.find_tfile(name));
    new Notice().noticeEl.innerHTML = `<span style="color: green; font-weight: bold;">Finished!</span><br>New player character <span style="text-decoration: underline;">${name}</span> added`;

} else {

    // Fire toast notification & exit templater
    new Notice().noticeEl.innerHTML = `<span style="color: red; font-weight: bold;">Cancelled:</span><br>Player character has not been added`;
    return;
}
-%>
---
type: pc
displayLink: "[[<% name %>]]"
level: 1
ac: 10
hp: 10
modifier: 0
race: "<% race ? race : '' %>"
class: "<% pClass ? pClass : '' %>"
subClass: "<% subClass ? subClass : '' %>"
player: "<% player ? player : '' %>"
cover: "/Assets/Images/Portrait.jpg"
---

###### <% name %>
<span class="sub2"> :FasPerson: Player Character | `=this.player` </span>
___
> [!infobox|no-t right]
> ![[portrait.jpg|350]]
>
> | Type | Stat |
> | ---- | ---- |
> | :FasCrown: Level   | `=this.level` |
> | :RiSwordFill: Class |  `=this.class`|
> | <% subType %> |  `=this.subClass`|
> |  :FasUserGroup: Race |  `=this.race`|
> 
>> [!tip]- STATS
>> | Stat | Score |
>> | ---- | :----: |
>> | :LiEye: Passive Perception | 11 |
>> | :FasMagnifyingGlass: Passive Investigation | 10 |
>> | :RiSpeakFill: Passive Insight | 11 |
>> | :FasShield: Armour Class | `=this.ac` |
>> | :FasHeart: Max Hit Points | `=this.hp` |
>
>> [!info]- STORYLINES
>>```dataview
>>LIST WITHOUT ID displayLink
>>FROM "Compendium/Party/Quests" AND ([[<% name %>]]  OR [[The Party]])
>>SORT file.ctime DESC
>
>>[!note]- HISTORY
>>```dataview
>>LIST WITHOUT ID displayLink
>>FROM "Session Notes" AND [[#]]
>>SORT file.ctime DESC
>
>^InfoBox

# Profile

> [!recite|clean no-t]
>	Introduction for players
>^IntroText
	
### Description
General Description

### Motivations
- List of Motivations

### Magic Items / Abilities
- None

### Allies
- [[Characters]] or [[Organisations]]

### Enemies
- [[Characters]] or [[Organisations]]

### Lost Thing
- <% lostThing ? lostThing : '' %>
