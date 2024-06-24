---
name: <% tp.file.title %>
aliases: 
cssclass: 
tags: daily worklog
create-date: <% tp.date.now("YYYY-MM-DD HH:MM.SS") %>
update-date: <% tp.date.now("YYYY-MM-DD HH:MM.SS") %>
week-number: <% tp.date.now("w", -1, tp.file.title, "[Daily]-YYYYMMDD-ddd") %>
---

# <% tp.date.now("dddd - MMMM DD", 0, tp.file.title, "[daily]_YYYYMMDD") %>

##### [[journal/<% tp.date.now("YYYY", -1, tp.file.title, "[daily]_YYYYMMDD-ddd") %>/daily/<% tp.date.now("MM-MMM", -1, tp.file.title, "[daily]_YYYYMMDD-ddd") %>/<% tp.date.now("[daily]-YYYYMMDD-ddd", -1, tp.file.title, "[daily]_YYYYMMDD-ddd") %> | <% tp.date.now("dddd - MMMM DD", -1, tp.file.title, "[daily]-YYYYMMDD-ddd") %> ]]       |       [[journal/<% tp.date.now("YYYY", 1, tp.file.title, "[daily]-YYYYMMDD-ddd") %>/daily/<% tp.date.now("MM-MMM", 1, tp.file.title, "[daily]-YYYYMMDD-ddd") %>/<% tp.date.now("[daily]-YYYYMMDD-ddd", 1, tp.file.title, "[daily]-YYYYMMDD-ddd") %> | <% tp.date.now("dddd - MMMM DD", 1, tp.file.title, "[daily]-YYYYMMDD-ddd") %> ]]
#### Worklog
- 9:30 am - 9:30 am
	- 

#### Issues
- [[ <% tp.date.now("[journal/]YYYY[/daily/]MM-MMM[/issues/][issues]-YYYYMMDD", 0, tp.file.title, "[Daily]-YYYYMMDD-ddd") %> | Issues]]

```dataview
list without id
L.text
from "<% tp.date.now("[journal/]YYYY[/daily/]MM-MMM[/issues/][issues]-YYYYMMDD", 0, tp.file.title, "[Daily]-YYYYMMDD-ddd") %>"
flatten file.lists as L
where contains(L.tags, "#issue")
```

#### Meetings
- [[ <% tp.date.now("[journal/]YYYY[/daily/]MM-MMM[/meetings/][meetings]-YYYYMMDD", 0, tp.file.title, "[Daily]-YYYYMMDD-ddd") %> | Logs]]

```dataview
list without id
L.text
from "<% tp.date.now("[journal/]YYYY[/daily/]MM-MMM[/meetings/][meeting]-YYYYMMDD", 0, tp.file.title, "[Daily]-YYYYMMDD-ddd") %>"
flatten file.lists as L
where contains(L.tags, "#issue")
```

#### Events
- None 

#### Todo

---
