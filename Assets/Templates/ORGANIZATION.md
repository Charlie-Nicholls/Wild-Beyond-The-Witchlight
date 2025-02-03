<%*
// ###########################################################
//                        Main Code Section
// ###########################################################

// Call modal form & declare variables
const result = await MF.openForm('ORGANIZATION');
const alignment = result.Alignment.value;
const name = result.Name.value;
const location = result.Location.value;

if (result.status === 'ok') {

    // Rename file & open in new tab; Fire toast notification
    await tp.file.rename(name);
    await app.workspace.getLeaf(true).openFile(tp.file.find_tfile(name));
    new Notice().noticeEl.innerHTML = `<span style="color: green; font-weight: bold;">Finished!</span><br>New organization <span style="text-decoration: underline;">${name}</span> added`;

} else {

    // Fire toast notification & exit templater
    new Notice().noticeEl.innerHTML = `<span style="color: red; font-weight: bold;">Cancelled:</span><br>Organization has not been added`;
    return;
}
_%>

---
type: organization
locations:
 - <% location ? `"[[${location}]]"` : '' %>
displayLink: "[[<% name %>]]"
---

###### <% name %>
<span class="sub2">:FasSitemap: Organization</span>
___

> [!infobox|no-t right]
> ![[embed.jpg|350]]
>>[!hint]- PEOPLE
>>```dataview
>>LIST WITHOUT ID displayLink
>>FROM "Compendium/NPCs" AND [[#]] OR "Compendium/Party/Player Characters" AND [[#]]
>
>>[!note]- HISTORY
>>```dataview
>>LIST WITHOUT ID displayLink
>>FROM "Session Notes" AND [[#]]
---

> [!recite|clean no-t]
>	Introduction for players
>^IntroText

### Description
Description of <% name %>, the <% alignment ? alignment.toLowerCase() : 'unknown' %> aligned organization.
