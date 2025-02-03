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

// Return icon based on type
function getIcon(type) {
    const iconMappings = {
	'Lore': ':LiScrollText:', 
	'Plan': ':LiNotebookPen:',
        'Prophecy': ':FasScroll:',
    }; 

    return iconMappings[type] || ':FasCircleQuestion:';
}

// ###########################################################
//                        Main Code Section
// ###########################################################

// Call modal form & declare variables
const result = await MF.openForm('LORE');
const name = result.Name.value;
const type = result.Type.value;
const icon = getIcon(type);

if (result.status === 'ok') {

    // Rename file & open in new tab; Fire toast notification
    await tp.file.rename(name);
    await app.workspace.getLeaf(true).openFile(tp.file.find_tfile(name));
    new Notice().noticeEl.innerHTML = `<span style="color: green; font-weight: bold;">Finished!</span><br>New lore <span style="text-decoration: underline;">${name}</span> added`;

} else {

    // Fire toast notification & exit templater
    new Notice().noticeEl.innerHTML = `<span style="color: red; font-weight: bold;">Cancelled:</span><br>Lore has not been added`;
    return;
}
_%>

---
type: lore
displayLink: "[[<% name %>]]"
---

###### <% name %>
<span class="sub2"><% type ? `${icon} ${type}` : '' %></span>
___

> [!recite|clean no-t]
>	Introduction for players
>^IntroText

### Description
Description of the <% type ? type.toLowerCase() : 'lore' %>, <% name %>.

---

>[!column|flex 2]
>>[!hint]- PEOPLE
>>```dataview
LIST WITHOUT ID displayLink
FROM "Compendium/NPCs" AND [[#]] OR "Compendium/Party/Player Characters" AND [[#]]
>
>>[!note]- HISTORY
>>```dataview
>LIST WITHOUT ID displayLink
>FROM "Session Notes" AND [[#]]
