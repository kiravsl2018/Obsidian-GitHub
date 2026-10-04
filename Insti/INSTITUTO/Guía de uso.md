---
tags:
  - guia
---
[[DAW HOME]]

# 📖 Guía de uso

## 0. Cómo está organizada la bóveda

```
INSTITUTO/
├── DAW HOME            ← panel de control (próximas 3 semanas, horario, progreso…)
├── Horario             ← tabla editable; el HOME la lee
├── Guía de uso         ← esta nota
├── Asignaturas/DAW1/
│   └── BADAT/          ← una carpeta por asignatura (igual para el resto)
│       ├── BADAT.md    ← la «home» de la asignatura: botones + tablas automáticas
│       ├── Temario/      teoría, bancos de preguntas, guías, índices de unidad, esquemas
│       ├── Actividades/  ejercicios hechos en clase e índices de actividades
│       ├── Evaluación/   exámenes y prácticas/proyectos evaluables
│       └── Adjuntos/     imágenes y capturas de esa asignatura
├── Plantillas/         ← plantillas de Templater (teoría, actividad, práctica, examen, día, asignatura)
├── Adjuntos/           ← donde caen las imágenes que pegues de ahora en adelante
├── Tasks/              ← notas de día creadas desde el Calendario
├── database/ · DATABASE NOTAS DAW · DAW EXCEL   ← tus bases de datos y hojas
```

> No hace falta enlazar nada a mano: cada asignatura **lista sola** su temario, actividades, prácticas, exámenes y tareas pendientes mirando su carpeta y las etiquetas de cada nota. Solo tienes que crear la nota dentro de la carpeta correcta (los botones ya lo hacen).

## 1. Cómo añadir prácticas, exámenes y actividades para que salgan en el HOME

El HOME (tarjeta **Próximas 3 semanas**, contadores y tarjetas de asignatura) lee **tareas** con una etiqueta y una fecha, y también las notas de examen/práctica con `Fecha` o `Entrega`. Hay tres formas; usa la que te venga mejor.

> **Qué sale en la tarjeta de próximos:** lo vencido sin marcar, hoy, los próximos 7 días, la semana siguiente y la tercera semana. **Todo lo que cae después** aparece debajo, en **«Más adelante»**, con su fecha: nada se queda fuera. Si prefieres otra ventana, cambia `DIAS_VENTANA` (7, 14, 21, 28…) al principio del bloque `CFG` del HOME; con `MAS_ADELANTE_ABIERTO: false` ese apartado sale plegado.

### A) Con los botones de la asignatura (la más cómoda)
1. Abre la nota de la asignatura (por ejemplo `BADAT`).
2. Pulsa el botón que toque:
   - **📖 Nueva Teoría** → se guarda en `Temario/`.
   - **📝 Nueva Actividad** → `Actividades/`.
   - **💻 Crear Nueva Práctica** y **🚨 Registrar Examen** → `Evaluación/`.
3. Te pregunta el tema (por ejemplo `01 - Introducción`). La asignatura la detecta sola por la carpeta.
4. **Cámbiale el nombre** (por ejemplo «Práctica Grafos»): ese nombre es el que se verá en el HOME.
5. En prácticas y exámenes rellena **`Entrega`** o **`Fecha`** con el formato `2026-10-15`.
6. Cuando la termines, marca la casilla de la tarea que trae la nota (o pon `To-Do: Realizado`). Desaparece de pendientes.

### B) Una tarea suelta en cualquier nota (la más rápida)
Escribe una línea así, con etiqueta y fecha:

- `- [ ] #practica Entregar práctica de grafos 📅 2026-10-15`
- `- [ ] #examen Examen Tema 2 📅 2026-10-20`
- `- [ ] #actividades Cuestionario del tema 1 📅 2026-10-08`

La asignatura se detecta sola por la carpeta (o por la propiedad `Asignatura` de la nota). Sin fecha, la tarea sale en «Sin fecha» dentro de la tarjeta.

### C) Desde el Calendario
Haz clic en un día del plugin Calendar: se crea la nota `AAAA-MM-DD` en `Tasks/` con una plantilla. Escribe dentro las tareas como en el punto B; **la fecha del nombre de la nota se usa si la tarea no lleva `📅`**. Pon en la propiedad `Asignatura` la que corresponda para que salga su color.

> Orden de prioridad de la fecha: `📅` de la tarea → propiedades `Fecha` / `Entrega` de la nota → fecha del nombre de la nota.

---

## 2. Etiquetas (qué significa cada una)

Regla: **la etiqueta dice qué TIPO de nota es**. A qué asignatura y tema pertenece lo dicen las **propiedades**, no las etiquetas.

| Etiqueta | Qué es | Dónde vive | Ejemplo |
|---|---|---|---|
| `asignatura` | La «home» de cada asignatura | raíz de la asignatura | `BADAT` |
| `temario-home` | Índice de una unidad (enlaza a teoría y a actividades) | `Temario/` | `Presentación - BADAT` |
| `temario` | Nota de teoría, guías, bancos de preguntas | `Temario/` | `Teoría Presentación - BADAT` |
| `actividades-home` | Índice de actividades de una unidad | `Actividades/` | `Práctica Presentación - BADAT` |
| `actividad` | Ejercicio o actividad hecha en clase | `Actividades/` | `Actividad 1.2 BADAT` |
| `practica` | Práctica o proyecto evaluable (se crea con el botón) | `Evaluación/` | `PROYECTO GOOGLE-AWS` |
| `examen` | Examen (se crea con el botón) | `Evaluación/` | `EXAMEN GRAFOS` |
| `Tasks`, `Calendario` | Notas de día creadas por el Calendario | `Tasks/` | `2026-10-02` |

> `practica` (una práctica que se entrega) y `actividades-home` (un índice) son cosas distintas: por eso el índice no se llama `practica-home`.
> La etiqueta `plantilla` ya **no** se copia a las notas nuevas: las plantillas no la llevan.

## 3. Propiedades (lo que cada nota debe llevar)

| Propiedad | Para qué | Valor |
|---|---|---|
| `Asignatura` | A qué asignatura pertenece | `Base de Datos`, `Programación`, `Sistemas`… |
| `Tema` | A qué unidad pertenece | `01 - Introducción`, `02 - Redes`… |
| `Entrega` / `Fecha` | Día de entrega o de examen | `2026-10-15` |
| `Prioridad` | Urgencia | `Alta 🔴`, `Media 🟡`, `Baja 🟢` |
| `To-Do` | Estado | `Pendiente`, `Realizado`… |
| `Profesor` | (solo en la nota de la asignatura) | se escribe en la propia nota |

### ¿Cómo indico el tema (1, 2, 3…)?
**No con etiquetas**: tendrías que inventar `tema1`, `tema2`… y no se pueden ordenar ni filtrar bien. Usa la propiedad **`Tema`** con **número de dos cifras + nombre**: `01 - Introducción`, `02 - Redes`, …`10 - …`. Con dos cifras se ordenan bien en las tablas de cada asignatura.

## 4. Índices automáticos
- Cada **nota de asignatura** tiene 3 tablas (Temario, Actividades, Prácticas y exámenes) y una lista de tareas pendientes. Se rellenan solas con lo que haya dentro de la carpeta de esa asignatura.
- Las notas `temario-home` y `actividades-home` siguen teniendo su **Índice automático** por la propiedad `Asignatura`.

## 5. Crear notas nuevas con plantilla
En el HOME, botón **➕ Nota desde plantilla**. Plantillas disponibles:
- **Plantilla Teoría** → etiqueta `temario`.
- **Plantilla Actividad** → etiqueta `actividad`.
- **Plantilla Práctica** y **Plantilla Examen** → las de los botones.
- **Plantilla DAW 1** → una asignatura nueva entera (ver abajo).
- **Plantilla Dia** → la usa el Calendario.

Si creas la nota **dentro de la carpeta de una asignatura**, la asignatura se rellena sola; si no, te la pregunta.

## 6. Asignatura nueva
1. En el HOME pulsa **➕ Nota desde plantilla**, elige **Plantilla DAW 1** y ponle de nombre el de la asignatura, en mayúsculas (por ejemplo `INGLÉS`).
2. La plantilla crea sola la carpeta `Asignaturas/DAW1/INGLÉS/` y se coloca dentro, con sus botones y tablas. Las subcarpetas `Temario`, `Actividades`, `Evaluación` y `Adjuntos` se crean al abrir la nota.
3. Añade la asignatura al `Horario` con el mismo nombre y el HOME le pondrá color y enlace. (Para elegir el color, añádela en `COLORES` del bloque `CFG` del HOME.)
4. Para que aparezca en la lista que ofrecen las plantillas cuando creas una nota fuera de su carpeta, añade su nombre en las plantillas (busca `'IPE'`).
5. El curso `DAW1` va escrito al final de la plantilla `Plantilla DAW 1`; el año que viene cámbialo por `DAW2`.
