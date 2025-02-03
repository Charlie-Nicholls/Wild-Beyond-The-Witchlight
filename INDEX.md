---
cssClasses: index
displayLink: "[[INDEX]]"
---

###### <span class="head"> The Wild Beyond The Witchlight </span> 
![[compendium.jpg|banner p+tcc]]
 
```dataviewjs
// Set path and class
const vault = this.app.vault.adapter.getResourcePath("").split("?")[0];
dv.container.className += ' hideSort cards cards-cover cards-1-1';

// Display PC card table
dv.table(["cover", "name", "details"],
  dv.pages(`"Compendium/Party/Player Characters"`)
  .sort(page => page.file.name, "asc")
    .map(p => [
      `![](${vault}/${p.cover})`, // For image link use: [![](${vault}/${p.cover})](<${p.file.name}#${p.file.name}>)
      p.displayLink,
      obsidian.Platform.isMobile ? `:FasPerson: ${p.player}<br>:FasUserGroup: ${p.race}<br>:RiSwordFill: ${p.class}` : `:FasPerson: ${p.player} / :FasUserGroup: ${p.race} / :RiSwordFill: ${p.class}`
    ])
);
```

> [!session]-  Session Notes<br><span class="sub">Summaries, Transcripts, & Notes</span>
> ```dataviewjs
> dv.container.className += ' listMe';
> let pages = dv.pages('"Session Notes"').sort(p => p.file.date, "desc");  
>dv.table(["Date"], pages.map(page => [`- ${page.displayLink}`]));
>```
> `BUTTON[note]`

> [!npc]-   NPCs<br><span class="sub">Non-Player Characters</span>
> ```dataviewjs
> dv.container.className += ' listMe';
> let pages = dv.pages('"Compendium/NPCs"').sort(p => p.file.name, "asc");  
> dv.table(["Name"], pages.map(page => [`- ${page.displayLink}`]));
>```
> `BUTTON[npc]`

> [!agenda]-  The Party<br><span class="sub">Objectives, Players, & Quests</span>
>```dataviewjs
>dv.container.className += ' listMe';
>let pages = dv.pages('"Compendium/Party/Quests"').sort(p => p.file.name, "asc");
>dv.table(["Name", "Status"], pages.map(page => {
>const questStatusTerms = ["completed", "abandoned", "failed", "ongoing", "pending"];
>let status = questStatusTerms.find(term => page.status && page.status.includes(term));
>status = status ? `(${status.replace("quest/", "")})` : "";
>return [`- ${page.displayLink} ${status}`, status];
>}));
>```
> `BUTTON[pc]` `BUTTON[quest]`

> [!genloc]-  Locations<br><span class="sub">Countries, Settlements, & Topography</span>
> ```dataviewjs
> dv.container.className += ' listMe';
> let pages = dv.pages('"Compendium/Atlas"').sort(p => p.file.name, "asc");  
> dv.table(["Name", "Type"], pages.map(page => [`- ${page.displayLink} (${page.type})`, page.type]));
>```
>`BUTTON[plane, realm, continent, territory, province, locale, landmark]`

> [!lore]-  Lore & Mythos<br><span class="sub">Factions, Gods, Relics, & More</span> 
> ```dataviewjs
> dv.container.className += ' listMe';
> let pages = dv.pages('"Compendium/Lore"').sort(p => p.file.name, "asc");  
>dv.table(["Name", "Type"], pages.map(page => [`- ${page.displayLink} (${page.type})`, page.type]));
>```
> `BUTTON[deity, event, object, org]`
