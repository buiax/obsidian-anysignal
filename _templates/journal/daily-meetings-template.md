---
name: <% tp.file.title %>
aliases: 
cssclass: 
tags: meeting log
created-date: <% tp.date.now("YYYY-MM-DD HH:MM.SS") %>
---
# [[<% tp.date.now("[Daily]-YYYYMMDD-ddd", 0, tp.file.title, "[meeting]-YYYYMMDD") %> | Meetings for  <% tp.date.now("dddd - MMMM DD", 0, tp.file.title, "[meeting]-YYYYMMDD") %> ]]

---

<% tp.file.include("[[_templates/journal/meeting-outline]]") %>



