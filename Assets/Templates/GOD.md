<%*
// ###########################################################
//                        Helper Functions
// ###########################################################

// Convert string to camelCase
function toCamelCase(str) {
  return str
    .replace(/(?:^\w|[A-Z]|\b\w|\s+|[-_])/g, (match, index) =>
      index === 0 ? match.toLowerCase() : match.toUpperCase()
    )
    .replace(/[\s-_]+/g, '');
}

// ###########################################################
//                        Main Code Section
// ###########################################################

// Call modal form & declare variables
const result = await MF.openForm('GOD');
const type = result.Type.value;
const name = result.Name.value;
const gender = result.Gender.value;
const domains = result.Domains.value;
const pantheon = result.Pantheon.value;

if (result.status === 'ok') {

    // Rename file & open in new tab; Fire toast notification
    await tp.file.rename(name);
    await app.workspace.getLeaf(true).openFile(tp.file.find_tfile(name));
    new Notice().noticeEl.innerHTML = `<span style="color: green; font-weight: bold;">Finished!</span><br>New deity <span style="text-decoration: underline;">${name}</span> added`;

} else {

    // Fire toast notification & exit templater
    new Notice().noticeEl.innerHTML = `<span style="color: red; font-weight: bold;">Cancelled:</span><br>Deity has not been added`;
    return;
}
_%>

---
type: deity
displayLink: "[[<% name %>]]"
domains: <% domains ? domains.join(', ') : '' %>
pantheon: <% pantheon ? pantheon : '' %>
---

###### <% name %>
<span class="sub2">:FasPersonRays: <% type %> | :FasBoltLightning: `=this.domains` </span>
___

> [!infobox|no-t right]
> ![[portrait.jpg|350]]
>
> | Type | Stat |
> | ---- | ---- |
> | :FasBoltLightning: Domains | `=this.domains` |
> | :FasVenusMars: Gender | <% gender ? gender : '' %> |
> | :FasBuildingColumns: Pantheon | `=this.pantheon` |
>
>> [!info]- STORYLINES
>>```dataview
>>LIST WITHOUT ID displayLink
>>FROM "Compendium/Party/Quests" AND [[#]]
>
>> [!hint]-  PEOPLE
>>```dataview
>>LIST WITHOUT ID displayLink
>>FROM "Compendium/NPCs" AND [[#]] OR "Compendium/Party" AND [[#]] 
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
Description of <% name %>, the <% type %> of `=this.domains`.
