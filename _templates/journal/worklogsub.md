---
name: 
aliases: 
cssclass: 
tags: 

date: 
starttime: 
endtime: 

status: 
topic: 
---
# <% tp.date.now("dddd - MMMM DD", 0, tp.file.title, "[daily]_YYYYMMDD") %>

##### [[daily/<% tp.date.now("YYYY") %>/<% tp.date.now("MM MMM") %>/<% tp.date.now("[daily]_YYYYMMDD", -1, tp.file.title, "[daily]_YYYYMMDD") %> | <% tp.date.now("dddd - MMMM DD", -1, tp.file.title, "[daily]_YYYYMMDD") %> ]]       |       [[daily/<% tp.date.now("YYYY") %>/<% tp.date.now("MM MMM") %>/<% tp.date.now("[daily]_YYYYMMDD", 1, tp.file.title, "[daily]_YYYYMMDD") %> | <% tp.date.now("dddd - MMMM DD", 1, tp.file.title, "[daily]_YYYYMMDD") %> ]]
---
#### Worklog

#### Issues

#### Events
- None 

#### Todo
<% tp.user.rolloverTodo(tp) %>
---
<% await tp.file.move("daily/" + tp.date.now("YYYY") + "/" + tp.file.title) %>