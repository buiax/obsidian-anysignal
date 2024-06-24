<%*
  let title = tp.file.title
  if (title.startsWith("Untitled")) {
    title = await tp.system.prompt("Title");
    await tp.file.rename(title);
  } 
  
  tR += "---"
%>
name:  <%* tR += title %>
aliases: 
cssclass:
tags: 

create-date: <% tp.date.now("YYYY-MM-DD HH:MM.SS") %>
update-date: <% tp.file.last_modified_date("YYYY-MM-DD HH:MM.SS") %>
---
# <%* tR += title %>

