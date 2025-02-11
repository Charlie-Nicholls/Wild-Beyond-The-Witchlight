<%*
// ###########################################################
//                        Main Code Section
// ###########################################################

// Call modal form & declare variables
const result = await MF.openForm('QUEST');
const name = result.Name.value;
const status = result.Status.value;
const location = result.Location.value;
const npc = result.Assignor.value;
const target = result.Assignee.value;

if (result.status === 'ok') {

    // Rename file & open in new tab; Fire toast notification
    await tp.file.rename(name);
    await app.workspace.getLeaf(true).openFile(tp.file.find_tfile(name));
    new Notice().noticeEl.innerHTML = `<span style="color: green; font-weight: bold;">Finished!</span><br>New quest <span style="text-decoration: underline;">${name}</span> added`;

} else {

    // Fire toast notification & exit templater
    new Notice().noticeEl.innerHTML = `<span style="color: red; font-weight: bold;">Cancelled:</span><br>Quest has not been added`;
    return;
}
_%>

---
type: quest
target: <% target === "[ Group Quest ]" ? '"[[The Party]]"' : target ? `"[[${target}]]"` : '' %>
locations:
 - <% location ? `"[[${location}]]"` : ''  %>
displayLink: "[[<% name %>]]"
status: <% status %>
---
###### <% name %>
<span class="sub2"> :FasCircleExclamation: Quest | :FasListCheck: `=this.status` | :FasUser: [[<% npc %>]] </span>
---

> [!column|flex 3]
>>[!note]- HISTORY
>>```dataview
>>LIST WITHOUT ID displayLink
>>FROM "Session Notes" AND [[#]]

---

### Description
Quest description here...

### Quest Giver
[[<% npc %>]]

### Objectives
 - [ ] Objective

### Stages
 - [ ] Stage 1

### Index
 - [[#]]

### Plan
