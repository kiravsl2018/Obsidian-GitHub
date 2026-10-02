---
tags:
  - guia
---
[[DAW HOME]]

# 📖 Guía de uso

## 1. Cómo añadir prácticas, exámenes y actividades para que salgan en el HOME

El HOME (tarjeta **Próximos 14 días**, contadores y tarjetas de asignatura) lee **tareas** con una etiqueta y una fecha. Hay tres formas; usa la que te venga mejor.

### A) Con los botones de la asignatura (la más cómoda)
1. Abre la nota de la asignatura (por ejemplo `BADAT`).
2. Pulsa **💻 Crear Nueva Práctica** o **🚨 Registrar Examen**. Se crea una nota con plantilla en la carpeta de la asignatura.
3. **Cámbiale el nombre** (por ejemplo «Práctica Grafos»): ese nombre es el que se verá en el HOME.
4. Rellena la propiedad **`Entrega`** (práctica) o **`Fecha`** (examen) con el formato `2026-10-15`.
5. Cuando la termines, marca la casilla de la tarea que trae la nota. Desaparece de pendientes.

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

| Etiqueta | Qué es | Ejemplo |
|---|---|---|
| `asignatura` | La «home» de cada asignatura | `BADAT` |
| `temario-home` | Índice de una unidad (enlaza a teoría y a actividades). Antes `tema-home` | `Presentación - BADAT` |
| `temario` | Nota de teoría | `Teoría Presentación - BADAT` |
| `actividades-home` | Índice de actividades de una unidad. Antes `practica-home` | `Práctica Presentación - BADAT` |
| `actividad` | Ejercicio o actividad hecha en clase | `Actividad 1.2 BADAT` |
| `practica` | Práctica evaluable (se crea con el botón) | `Práctica Grafos` |
| `examen` | Examen (se crea con el botón) | `Examen Tema 1` |
| `plantilla` | Solo dentro de `Plantillas/` | |
| `Tasks`, `Calendario` | Notas de día creadas por el Calendario | `2026-10-02` |

> `practica` (una práctica que se entrega) y `actividades-home` (un índice) son cosas distintas: por eso el índice ya no se llama `practica-home`.

## 3. Propiedades (lo que cada nota debe llevar)

| Propiedad | Para qué | Valor |
|---|---|---|
| `Asignatura` | A qué asignatura pertenece | `Base de Datos`, `Programación`, `Sistemas`… |
| `Tema` | A qué unidad pertenece | `01 - Introducción`, `02 - Redes`… |
| `Entrega` / `Fecha` | Día de entrega o de examen | `2026-10-15` |
| `Prioridad` | Urgencia | `Alta 🔴`, `Media 🟡`, `Baja 🟢` |
| `To-Do` | Estado | `Pendiente`, `Realizado`… |

### ¿Cómo indico el tema (1, 2, 3…)?
**No con etiquetas**: tendrías que inventar `tema1`, `tema2`… y no se pueden ordenar ni filtrar bien. Usa la propiedad **`Tema`** con **número de dos cifras + nombre**: `01 - Introducción`, `02 - Redes`, …`10 - …`. Con dos cifras se ordenan bien en tablas y en Base de datos, y puedes agrupar por tema con una sola columna.

## 4. Índices automáticos
Las notas `temario-home` y `actividades-home` tienen al final un **Índice automático**: una tabla con todas las notas de esa asignatura que lleven la etiqueta correspondiente. Si creas una teoría o actividad con la propiedad `Asignatura` bien puesta, **aparece sola**, sin tener que enlazarla a mano.

## 5. Crear notas nuevas con plantilla
En el HOME, botón **➕ Nota desde plantilla**. Plantillas disponibles:
- **Plantilla Teoría** → etiqueta `temario`, te pregunta asignatura y tema.
- **Plantilla Actividad** → etiqueta `actividad`, te pregunta asignatura y tema.
- **Plantilla Práctica** y **Plantilla Examen** → las de los botones.
