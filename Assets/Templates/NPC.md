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

// Format sub heading
function formatSub(location, affinity) {
  return [
    location && `:FasMapLocationDot: [[${location}]]`,
    affinity && `:FasHeartPulse: ${affinity}`
  ]
  .filter(sub => sub)
  .join(' | ');
}


// ###########################################################
//                         Main Code
// ###########################################################

// Call modal form & declare variables
const result = await MF.openForm('NPC');
const affinity = result.Affinity.value;
const gender = result.Gender.value;
const location = result.Location.value;
const name = result.Name.value;
const race = result.Race.value;
const sub = formatSub(location, affinity);

if (result.status === 'ok') {

    // Rename file & open in new tab; Fire toast notification
    await tp.file.rename(name);
    await app.workspace.getLeaf(true).openFile(tp.file.find_tfile(name));
    new Notice().noticeEl.innerHTML = `<span style="color: green; font-weight: bold;">Finished!</span><br>New NPC <span style="text-decoration: underline;">${name}</span> added`;

} else {

    // Fire toast notification & exit templater
    new Notice().noticeEl.innerHTML = `<span style="color: red; font-weight: bold;">Cancelled:</span><br>NPC has not been added`;
    return;
}
_%>

---
type: npc
locations:
 - <% location ? `"[[${location}]]"` : '' %>
displayLink: "[[<% name %>]]"
---
###### <% name %>
<span class="sub2"><% sub ? sub : '' %> </span>
___

> [!infobox|no-t right]
> ![[portrait.jpg|350]]
>
> | Type | Stat |
> | ---- | ---- |
> | :FasVenusMars: Gender | <% gender ? gender : '' %> |
> | :FasUser: Race | <% race ? race : '' %> |
>
>> [!info]- STORYLINES
>>```dataview
>>LIST WITHOUT ID displayLink
>>FROM "Compendium/Party/Quests" AND [[#]]
>
>>[!note]- HISTORY
>>```dataview
>>LIST WITHOUT ID displayLink
>>FROM "Session Notes" AND [[#]]
>
>^InfoBox

# Profile

> [!recite|clean no-t]
>	Introduction for players
>^IntroText

### Description
Description

### Motivations
- List of Motivations

### Magic Items / Abilities
- None

### Allies
- [[Characters]] or [[Organisations]]

### Enemies
- [[Characters]] or [[Organisations]]

### Secrets
- None