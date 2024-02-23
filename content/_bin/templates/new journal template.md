---
id: '<% tp.file.creation_date("YYYYMMDDHHmmss") %>'
title: '<% tp.file.title %>'
tags:
  - journal
created: <% moment(tp.file.creation_date("YYYY-MM-DDTHH:mm:ss.SSSZ")).toISOString() %>
---
