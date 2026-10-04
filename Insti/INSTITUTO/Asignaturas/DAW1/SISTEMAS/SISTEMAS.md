---
tags:
  - asignatura
cssclasses:
  - dashboard
Asignatura: Sistemas
To-Do:
Profesor: FRANCIS
---
# 📚 SISTEMAS
[[DAW HOME]] · 🎓 Profesor/a: `INPUT[text(placeholder(Nombre)):Profesor]`

> [!⚡] **ACCIONES RÁPIDAS DE LA MATERIA**
> ```meta-bind-button
> style: default
> label: 📖 Nueva Teoría
> actions:
>   - type: templaterCreateNote
>     templateFile: "INSTITUTO/Plantillas/Plantilla Teoría.md"
>     folderPath: "INSTITUTO/Asignaturas/DAW1/SISTEMAS/Temario"
>     fileName: "Nueva Teoría"
>     openNote: true
> ```
> 
> ```meta-bind-button
> style: default
> label: 📝 Nueva Actividad
> actions:
>   - type: templaterCreateNote
>     templateFile: "INSTITUTO/Plantillas/Plantilla Actividad.md"
>     folderPath: "INSTITUTO/Asignaturas/DAW1/SISTEMAS/Actividades"
>     fileName: "Nueva Actividad"
>     openNote: true
> ```
> 
> ```meta-bind-button
> style: default
> label: 💻 Crear Nueva Práctica
> actions:
>   - type: templaterCreateNote
>     templateFile: "INSTITUTO/Plantillas/Plantilla Práctica.md"
>     folderPath: "INSTITUTO/Asignaturas/DAW1/SISTEMAS/Evaluación"
>     fileName: "Nueva Práctica"
>     openNote: true
> ```
> 
> ```meta-bind-button
> style: default
> label: 🚨 Registrar Examen
> actions:
>   - type: templaterCreateNote
>     templateFile: "INSTITUTO/Plantillas/Plantilla Examen.md"
>     folderPath: "INSTITUTO/Asignaturas/DAW1/SISTEMAS/Evaluación"
>     fileName: "Nuevo Examen"
>     openNote: true
> ```

---

## 📖 Temario

```dataview
TABLE WITHOUT ID file.link AS "Nota", Tema AS "Unidad", Prioridad AS "Prioridad", file.frontmatter["To-Do"] AS "Estado"
FROM #temario
WHERE startswith(file.folder, this.file.folder)
SORT Tema ASC, file.name ASC
```

## 📝 Actividades

```dataview
TABLE WITHOUT ID file.link AS "Nota", Tema AS "Unidad", Prioridad AS "Prioridad", file.frontmatter["To-Do"] AS "Estado"
FROM #actividad
WHERE startswith(file.folder, this.file.folder)
SORT Tema ASC, file.name ASC
```

## 🎯 Prácticas y exámenes

```dataview
TABLE WITHOUT ID file.link AS "Nota", choice(contains(file.tags, "#examen"), "🚨 Examen", "💻 Práctica") AS "Tipo", Tema AS "Unidad", default(Fecha, Entrega) AS "Fecha", Prioridad AS "Prioridad", file.frontmatter["To-Do"] AS "Estado"
FROM #practica OR #examen
WHERE startswith(file.folder, this.file.folder)
SORT default(Fecha, Entrega) ASC, file.name ASC
```

## ✅ Tareas pendientes de la asignatura

```dataview
TASK
WHERE !completed AND text != "" AND startswith(file.folder, this.file.folder)
GROUP BY file.link
```

```dataviewjs
// Mantenimiento silencioso: crea las carpetas de la asignatura si faltan, para que los botones de arriba siempre funcionen.
const base = dv.current().file.folder;
if (base.includes('/Asignaturas/')) {
  for (const n of ['Temario', 'Actividades', 'Evaluación', 'Adjuntos']) {
    if (!dv.app.vault.getAbstractFileByPath(base + '/' + n)) { try { await dv.app.vault.createFolder(base + '/' + n); } catch (e) { /* ya existe */ } }
  }
}
```

---

## 🗺️ MAPA DE CONTENIDOS (TEMARIO)

* 📂 **Bloque 1: Introducción y Fundamentos**
	* -
	* -
* 📂 **Bloque 2: Desarrollo Avanzado**
	* -

---

## 💻 RADAR DE ENTREGAS 

> [!TIP] **¿Cómo crear una actividad rápido?**
> Solo tienes que añadir un elemento a la lista de abajo con la etiqueta `#actividades`. Si además es una práctica o un examen, añádele su tag correspondiente (`#practica` o `#examen`) y **se teletransportará sola a las tarjetas visuales de tu DAW HOME**.

---

## 🔍 NOTAS CONECTADAS A ESTA MATERIA

```dataview
LIST
WHERE contains(file.outlinks, this.file.link) AND file.path != this.file.path
SORT file.mday DESC
```
