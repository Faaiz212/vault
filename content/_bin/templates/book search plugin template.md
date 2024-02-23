---
created: <% moment(tp.file.creation_date("YYYY-MM-DDTHH:mm:ss.SSSZ")).toISOString() %>
id: '<% tp.file.creation_date("YYYYMMDDHHmmss") %>'
tags:
  - books
  - type/litnote
title: "{{title}}"
---

Title:: "{{title}}"  
Author(s):: [[{{author}}]]  
Date:: {{publishDate}}  
Status:: <% await tp.system.suggester(["#read", "#unread", "#unfinished"], ["#read", "#unread", "#unfinished"]) %>  
ISBN:: {{isbn10}} {{isbn13}}  

---

![cover|150]({{coverUrl}})

# {{title}}

## Highlights

## Literature Notes

## Quotes

---

## Thesis
- **Definition**: 
- **Key Points**:
    - 
- **Arguments/Support**:
    - 

## Antithesis
- **Definition**: 
- **Key Points**:
    - 
- **Arguments/Support**:
    - 

## Synthesis
- **Definition**: 
- **Key Points**:
    - 
- **Arguments/Support**:
    - 

## Personal Reflections/Notes

-  

## References

-  
