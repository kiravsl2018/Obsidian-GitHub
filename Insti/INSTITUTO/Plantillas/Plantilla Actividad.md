---
tags:
  - actividad
Asignatura: <% ({'BADAT':'Base de Datos','PROGRAMACIÓN':'Programación','SISTEMAS':'Sistemas','ENTORNO':'Entorno','LENGUAJE':'Lenguaje','DIGITALIZACIÓN':'Digitalización','SOSTENIBILIDAD':'Sostenibilidad','IPE':'IPE'})[tp.file.folder(true).split('/')[3]] ?? tp.file.folder(true).split('/')[3] ?? await tp.system.suggester(['Base de Datos','Programación','Sistemas','Entorno','Lenguaje','Digitalización','Sostenibilidad','IPE'], ['Base de Datos','Programación','Sistemas','Entorno','Lenguaje','Digitalización','Sostenibilidad','IPE'], false, '¿De qué asignatura es?') %>
Tema:
  - <% await tp.system.prompt('Tema (ej. 01 - Introducción)', '01 - ', false) %>
Prioridad: Media 🟡
To-Do: Pendiente
---
[[<% tp.file.folder(true).split('/')[3] ?? 'DAW HOME' %>]] · [[DAW HOME]]

# <% tp.file.title %>

---

