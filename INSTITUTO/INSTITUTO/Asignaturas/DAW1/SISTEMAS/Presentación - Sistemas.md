---
tags:
  - temario-home
Asignatura: Sistemas
Tema:
  - Introducción
To-Do: Editable
---
[[SISTEMAS]]

# **TEORÍA**
---
- [[Teoría Presentación - Sistemas]]


# **PRÁCTICAS**
---
- [[Práctica Presentación - Sistemas]]
- 


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
