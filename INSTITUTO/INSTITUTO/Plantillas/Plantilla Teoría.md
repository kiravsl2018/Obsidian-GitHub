---
tags:
  - temario
  - plantilla
Asignatura: <% await tp.system.suggester(["Base de Datos","Programación","Sistemas","Entorno","Lenguaje","Digitalización","Sostenibilidad","IPE"], ["Base de Datos","Programación","Sistemas","Entorno","Lenguaje","Digitalización","Sostenibilidad","IPE"], false, "¿De qué asignatura es?") %>
Tema:
  - <% await tp.system.prompt("Tema (ej. 01 - Introducción)", "01 - ", false) %>
Prioridad: Media 🟡
To-Do: Pendiente
---
# <% tp.file.title %>

---

