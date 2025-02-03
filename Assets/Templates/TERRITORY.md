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
    Country: ':FasFlag:',
    'General Region': ':FasMap:',
    Kingdom: ':FasChessRook:',
    Nation: ':FasFlag:'
  };

  return iconMappings[type] || ':FasCircleQuestion:';
}


// Return modified path based on location
const dv = app.plugins.plugins.dataview.api;
function getPath(location) {
    const match = dv.pages('"Compendium/Atlas"')
        .where(p => (p.type === "continent" || p.type === "ocean") && p.file.name === location)
        .map(obj => obj.file.path.split('/').slice(2, -1).join('/'))
        .find(Boolean);

    return match || '';
}

// ###########################################################
//                        Main Code Section
// ###########################################################

// Call modal form & declare variables
const result = await MF.openForm('TERRITORY');
const location = result.Location.value;
const name = result.Name.value;
const type = result.Type.value;
const icon = getIcon(type);
const path = getPath(location);

if (result.status === 'ok') {

    // Rename file & open in new tab; Fire toast notification
    await tp.file.move(`Compendium/Atlas/${location ? `${path}/` : ''}${name}/${name}`);
    await app.workspace.getLeaf(true).openFile(tp.file.find_tfile(name));
    new Notice().noticeEl.innerHTML = `<span style="color: green; font-weight: bold;">Finished!</span><br>New territory <span style="text-decoration: underline;">${name}</span> added`;

} else {

    // Fire toast notification & exit templater
    new Notice().noticeEl.innerHTML = `<span style="color: red; font-weight: bold;">Cancelled:</span><br>Territory has not been added`;
    return;
}
_%>

---
type: territory
locations:
 - <% location ? `"[[${location}]]"` : '' %>
displayLink: "[[<% name %>]]"
---

![[banner.jpg|banner]]

---

###### <% name %>
<span class="sub2"><% type ? `${icon} ${type}` : '' %></span>

---

> [!recite|clean no-t]
>	Introduction for players
>^IntroText

### Description
Description of Territory

---

> [!column|flex 3]
>> [!hint]-  NPCs
>>```dataview
LIST WITHOUT ID displayLink
FROM "Compendium/NPCs" AND [[#]] OR "Compendium/Party" AND [[#]] 
> 
>> [!example]- LOCATIONS
>>```dataview
LIST WITHOUT ID displayLink + " (" + type + ")"
FROM "Compendium/Atlas/<% location ? `${path}/` : '' %><% name %>" AND [[#]]
WHERE file.name != this.file.name
SORT file.name ASC
>
>> [!note]- HISTORY
>>```dataview
LIST WITHOUT ID displayLink
FROM "Session Notes" AND [[#]]
SORT file.ctime DESC