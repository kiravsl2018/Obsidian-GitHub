---
tags:
  - actividades-home
Asignatura: Entorno
Prioridad: Baja 🟢
Tema:
  - Introducción
---

# ÍNDICE
---
- [[Actividad 1 - Entorno]]
- 


---
## 🔄 Índice automático

> [!INFO] Se rellena solo
> Lista todas las notas con la etiqueta `#actividad` o `#practica` de esta asignatura (propiedad `Asignatura`). Los enlaces manuales de arriba no hacen falta: puedes borrarlos cuando quieras.

```dataview
TABLE WITHOUT ID file.link AS "Actividad / práctica", Tema AS "Tema", Prioridad AS "Prioridad"
FROM #actividad OR #practica
WHERE lower(Asignatura) = lower(this.Asignatura)
SORT file.name ASC
```
