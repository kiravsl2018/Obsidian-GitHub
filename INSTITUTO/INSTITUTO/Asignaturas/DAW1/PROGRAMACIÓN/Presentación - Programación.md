---
tags:
  - temario-home
Asignatura: Programación
To-Do: Editable
Tema:
  - Introducción
Prioridad:
---
[[PROGRAMACIÓN]]

---
# Teoría
- [[Teoría Presentación - Programación]]

---
# Práctica
---

- [[Práctica Presentación - Programación]]


---
## 🔄 Índice automático

> [!INFO] Se rellena solo
> Lista todas las notas con la etiqueta `#temario` de esta asignatura (propiedad `Asignatura`). Los enlaces manuales de arriba no hacen falta: puedes borrarlos cuando quieras.

```dataview
TABLE WITHOUT ID file.link AS "Teoría", Tema AS "Tema", Prioridad AS "Prioridad"
FROM #temario
WHERE lower(Asignatura) = lower(this.Asignatura)
SORT file.name ASC
```
