---
cssClasses: index
displayLink: "[[Session Notes]]"
---

###### <span class="head">Session Notes</span> 
![[compendium.jpg|banner]]


 ### Title TBD
 
```dataviewjs
let pages = dv.pages('"Session Notes"').sort(p => p.number, "desc"); 
let chapters = [];
for (let i=0; i < pages.length; i++) {
	if (pages[i].number > 0) {
		chapters.push(`[[${pages[i].file.name}|${pages[i].alias}]]`);
		}
	}
dv.list(chapters)
dv.list(pages[1])
```