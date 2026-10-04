---
db_view: true
database:
  id: mui8is5g_3uz8jhd
  name: Database Daw
  icon: 🍷
  coverImage: INSTITUTO/yepers.jpeg
  coverImagePositionY: 50
  description: Base de Datos de DAW- General
  sourceFolder: ""
  sourceRules: []
  sourceLogic: and
  newRecordFolder: ""
  recordIconField: ""
  computedSyncMode: display-only
  summaryFormulas: {}
  columns:
    - key: file.name
      label: Name
      type: text
    - key: tags
      label: tags
      type: multi-select
      statusOptions:
        - value: Calendario
          color: gray
        - value: Tasks
          color: brown
        - value: actividad
          color: orange
        - value: asignatura
          color: yellow
        - value: dawhome
          color: green
        - value: examen
          color: blue
        - value: practica
          color: pink
        - value: actividades-home
          color: red
        - value: temario
          color: lime
        - value: temario-home
          color: teal
        - value: plantilla
          color: purple
    - key: Asignatura
      label: Asignatura
      type: text
    - key: Prioridad
      label: Prioridad
      type: text
    - key: Tema
      label: Tema
      type: multi-select
      statusOptions:
        - value: Introducción
          color: blue
    - key: To-Do
      label: To-Do
      type: text
    - key: Nota
      label: Nota
      type: text
  computedFields: []
  statusPresets: []
  defaultStatusPresetId: ""
  views:
    - id: mu9qvcmj_esc6euq
      name: Table view
      viewType: table
      sourceFolder: ""
      sourceRules: []
      sourceLogic: and
      showRecordIcon: false
      recordIconFieldOverrideEnabled: true
      recordIconField: ""
      newRecordFolder: ""
      displayWidth: wide
      sortColumn: ""
      sortDirection: asc
      sortRules: []
      columnOrder:
        - file.name
        - Asignatura
        - tags
        - Tema
        - Prioridad
        - To-Do
        - Nota
      columnWidths:
        file.name: 242
      hiddenColumns: []
      sortColumnOrder: ""
      statusFilter: ""
      groupByField: tags
      groupOrders:
        tags:
          - Tasks
          - examen
          - practica
          - actividad
          - temario
          - temario-home
          - actividades-home
          - asignatura
          - dawhome
          - Calendario
          - csv
          - DB
          - guia
          - horario
          - plantilla
      showEmptyGroups: {}
      collapsedGroups:
        tags:
          - DB
          - Calendario
          - guia
          - horario
          - csv
          - dawhome
      boardGroupField: ""
      boardSubgroupEnabled: false
      boardSubgroupField: ""
      boardColumnWidth: 280
      defaultColumnWidth: 150
      titleField: ""
      boardCardOrders: {}
      manualOrder:
        ranks:
          Tasks/2026-10-02.md: 2aAK
          Tasks/2026-09-30 - BADAT.md: 5AKe
          Sin título.md: 7kUy
          Plantilla DAW.md: AKfI
          DAW HOME.md: Cupc
          Asignaturas/DAW1/SISTEMAS/SISTEMAS.md: FUzw
          Asignaturas/DAW1/LENGUAJE/Presentación - Lenguaje.md: I5AG
          Asignaturas/DAW1/LENGUAJE/Teoría Presentación - Lenguaje.md: KfKa
          Asignaturas/DAW1/LENGUAJE/LENGUAJE.md: NFUu
          Asignaturas/DAW1/SOSTENIBILIDAD/SOSTENIBILIDAD.md: PpfE
          Asignaturas/DAW1/DIGITALIZACIÓN/DIGITALIZACIÓN.md: SPpY
          Asignaturas/DAW1/ENTORNO/ENTORNO.md: Uzzs
          Asignaturas/DAW1/ENTORNO/Guía de Estilos de Presentación.md: XaAC
          Asignaturas/DAW1/PROGRAMACIÓN/Presentación Docs-Programación/Teoría Presentación - Programación.md: aAKW
          Asignaturas/DAW1/PROGRAMACIÓN/Presentación Docs-Programación/Práctica Presentación - Programación.md: ckUq
          Asignaturas/DAW1/PROGRAMACIÓN/PROGRAMACIÓN.md: fKfA
          Asignaturas/DAW1/PROGRAMACIÓN/Presentación - Programación.md: hupU
          Asignaturas/DAW1/PROGRAMACIÓN/Presentación Actividades - Programación/Actividad 1.3 - Programación.md: kUzo
          Asignaturas/DAW1/PROGRAMACIÓN/Presentación Actividades - Programación/Actividad 1.2 - PROGRAMACIÓN.md: n5A8
          Asignaturas/DAW1/BADAT/Presentación Docs -BADAT/Teoría Presentación - BADAT.md: pfKS
          Asignaturas/DAW1/BADAT/Presentación Docs -BADAT/Práctica Presentación - BADAT.md: sFUm
          Asignaturas/DAW1/BADAT/Presentación - BADAT.md: upf6
          Asignaturas/DAW1/BADAT/BADAT.md: xPpQ
          database/Untitled.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          DATABASE NOTAS DAW.md: xPpQV
          DB-CSV/DATABASE NOTAS DAW.md: xPpQVV
          database/DATABASE NOTAS DAW.md: xPpQVVV
          INSTITUTO/Tasks/2026-10-02.md: xPpQVVVV
          INSTITUTO/Tasks/2026-09-30 - BADAT.md: xPpQVVVVV
          INSTITUTO/Plantilla DAW.md: xPpQVVVVVV
          INSTITUTO/DAW HOME.md: xPpQVVVVVVV
          INSTITUTO/DATABASE NOTAS DAW.md: xPpQVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/SOSTENIBILIDAD/SOSTENIBILIDAD.md: xPpQVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/SISTEMAS/SISTEMAS.md: xPpQVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/PROGRAMACIÓN/Presentación Docs-Programación/Teoría Presentación - Programación.md: xPpQVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/PROGRAMACIÓN/Presentación Docs-Programación/Práctica Presentación - Programación.md: xPpQVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/PROGRAMACIÓN/Presentación Actividades - Programación/Actividad 1.3 - Programación.md: xPpQVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/PROGRAMACIÓN/Presentación Actividades - Programación/Actividad 1.2 - PROGRAMACIÓN.md: xPpQVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/PROGRAMACIÓN/Presentación - Programación.md: xPpQVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/PROGRAMACIÓN/PROGRAMACIÓN.md: xPpQVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/LENGUAJE/Teoría Presentación - Lenguaje.md: xPpQVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/LENGUAJE/Presentación - Lenguaje.md: xPpQVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/LENGUAJE/LENGUAJE.md: xPpQVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/ENTORNO/Guía de Estilos de Presentación.md: xPpQVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/ENTORNO/ENTORNO.md: xPpQVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/DIGITALIZACIÓN/DIGITALIZACIÓN.md: xPpQVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/BADAT/Presentación Docs -BADAT/Teoría Presentación - BADAT.md: xPpQVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/BADAT/Presentación Docs -BADAT/Práctica Presentación - BADAT.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/BADAT/Presentación - BADAT.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/BADAT/BADAT.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/BADAT/Presentación Docs -BADAT/Banco de preguntas - BADAT.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/SISTEMAS/Presentación - Sistemas.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/SISTEMAS/Presentación Docs - Sistemas/Práctica Presentación - Sistemas.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/SISTEMAS/Presentación Docs - Sistemas/Teoría Presentación - Sistemas.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/PROGRAMACIÓN/Presentación Actividades - Programación/Actividad 1.2 - Programación.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/LENGUAJE/Presentación Docs - Lenguaje/Teoría Presentación - Lenguaje.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/LENGUAJE/Presentación Docs - Lenguaje/Práctica Presentación - Lenguaje.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/LENGUAJE/Presentación Actividades - Lenguaje/Ejercicio1.1 - Lenguaje.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/LENGUAJE/Presentación Actividades - Lenguaje/Ejercicio 1.1 - Lenguaje.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          IPE EJERCICIO.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          test.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/IPE/IPE EJERCICIO.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/ENTORNO/Presentación Docs - Entorno/Práctica Presentación - Entorno.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/ENTORNO/Presentación Docs - Entorno/Teoría Presentación - Entorno.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/ENTORNO/Presentación Actividades - Entorno/Actividad 1 - Entorno.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/ENTORNO/Presentación  - Entorno.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/ENTORNO/Presentación Docs - Entorno/Guía de Estilos de Presentación.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          Plantillas/Plantilla DAW.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          Plantillas/Act-1.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/guía java .md: xPpQVVVVVVVVVVVF
          INSTITUTO/Asignaturas/DAW1/LENGUAJE/Presentación Actividades - Lenguaje/MIGUEL_LÓPEZ_TEMA1_EJERCICIO2.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/LENGUAJE/Presentación Actividades - Lenguaje/MIGUEL_LÓPEZ_TEMA1_EJERCICIO1.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          Plantillas/Plantilla.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          VM/INSTALACION Y PASO A PASO - VIRTUALBOX.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Plantillas/Plantilla DAW 1.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Plantillas/Plantilla.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Plantillas/Plantilla DAW.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/ENTORNO/Presentación Actividades - Entorno/Tema0_Act1_MLC.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/BADAT/Presentación Actividades - BADAT/Actividad 1.2 BADAT.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Plantillas/Plantilla Práctica.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Plantillas/Plantilla Examen.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Plantillas/Plantilla Teoría.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Plantillas/Plantilla Dia.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Plantillas/Plantilla Actividad.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Horario.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Guía de uso.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/PROGRAMACIÓN/Presentación Actividades - Programación/guía java .md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/BADAT/EXAMENES-BADAT/EXAMEN GRAFOS.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/PROGRAMACIÓN/EXAMENES PROGRAMACIÓN/EXAMEN PROGRAMACIÓN.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/BADAT/EXAMENES-BADAT/PROYECTO GOOGLE-AWS.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/DIGITALIZACIÓN/EXAMEN DE DIGITALIZACION.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/PROGRAMACIÓN/Evaluación/EXAMEN PROGRAMACIÓN.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/PROGRAMACIÓN/Temario/Teoría Presentación - Programación.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/PROGRAMACIÓN/Temario/Presentación - Programación.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/PROGRAMACIÓN/Temario/guía java .md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/PROGRAMACIÓN/Actividades/Práctica Presentación - Programación.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/PROGRAMACIÓN/Actividades/Actividad 1.3 - Programación.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/PROGRAMACIÓN/Actividades/Actividad 1.2 - Programación.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/IPE/Actividades/IPE EJERCICIO.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/IPE/IPE.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/SISTEMAS/Temario/Teoría Presentación - Sistemas.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/SISTEMAS/Temario/Presentación - Sistemas.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/SISTEMAS/Temario/INSTALACION Y PASO A PASO - VIRTUALBOX.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/SISTEMAS/Actividades/Práctica Presentación - Sistemas.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/DIGITALIZACIÓN/Evaluación/EXAMEN DE DIGITALIZACION.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/LENGUAJE/Temario/Teoría Presentación - Lenguaje.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/LENGUAJE/Temario/Presentación - Lenguaje.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/LENGUAJE/Actividades/Práctica Presentación - Lenguaje.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/LENGUAJE/Actividades/MIGUEL_LÓPEZ_TEMA1_EJERCICIO1.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/LENGUAJE/Actividades/MIGUEL_LÓPEZ_TEMA1_EJERCICIO2.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/LENGUAJE/Actividades/Ejercicio 1.1 - Lenguaje.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/BADAT/Temario/Banco de preguntas - BADAT.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/BADAT/Temario/Teoría Presentación - BADAT.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/BADAT/Temario/Presentación - BADAT.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/BADAT/Evaluación/EXAMEN GRAFOS.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/BADAT/Evaluación/PROYECTO GOOGLE-AWS.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/BADAT/Actividades/Práctica Presentación - BADAT.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/BADAT/Actividades/Actividad 1.2 BADAT.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/ENTORNO/Temario/Teoría Presentación - Entorno.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/ENTORNO/Temario/Presentación  - Entorno.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/ENTORNO/Temario/Guía de Estilos de Presentación.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/ENTORNO/Actividades/Tema0_Act1_MLC.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/ENTORNO/Actividades/Práctica Presentación - Entorno.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/ENTORNO/Actividades/Actividad 1 - Entorno.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/BADAT/Temario/T1-PRESENTACIÓN TEORÍA- BADAT.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/SISTEMAS/Temario/T1-PRESENTACIÓN-SISTEMAS.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/PROGRAMACIÓN/Temario/T1-TEORÍA-PROGRAMACIÓN.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/LENGUAJE/Temario/T1-TEORÍA-LENGUAJE.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/ENTORNO/Temario/T1-TEORÍA-ENTORNO.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/BADAT/Temario/T1-PRESENTACIÓN-BADAT.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/SISTEMAS/Temario/T1-TEORÍA-SISTEMAS.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
          INSTITUTO/Asignaturas/DAW1/BADAT/Temario/T1-TEORÍA-BADAT.md: xPpQVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
      galleryImageField: ""
      galleryImageAspectRatio: 0.75
      galleryCardSize: 250
      galleryImageFit: cover
      boardImageField: ""
      boardImageAspectRatio: 0.75
      boardImageFit: cover
      showEmptyFields: false
      listCompactFields: false
      statusPresets: []
      defaultStatusPresetId: ""
      filterLogic: and
      filters: []
      summaryRules: []
      conditionalFormats: []
      chartType: bar
      chartGroupField: ""
      chartDateBucket: ""
      chartNumberBucket: ""
      chartStackField: ""
      chartSeriesField: ""
      chartAggregation: count
      chartValueField: ""
      chartSecondaryAggregation: count
      chartSecondaryValueField: ""
      chartSortBy: ""
      chartHiddenGroups: {}
      chartOmitZeroValues: false
      chartCumulative: false
      chartHeight: ""
      chartGridLines: ""
      chartAxisNames: ""
      chartShowTitle: true
      chartTitle: ""
      chartShowDataLabels: false
      chartDataLabelMode: ""
      chartDataLabelColor: ""
      chartSmoothLine: false
      chartGradientArea: false
      chartColorPalette: ""
      chartColorByValue: false
      chartShowDonutCenter: false
      chartDonutCenterMode: ""
      chartValueAxisRange: ""
      chartReferenceLines: []
      calendarMonth: ""
      calendarStartDateField: ""
      calendarEndDateField: ""
      calendarTitleField: ""
      calendarColorField: ""
      calendarKeepCellAspectRatio: false
      calendarScale: ""
      calendarDay: ""
      calendarWeekStart: ""
      timelineStartDateField: ""
      timelineEndDateField: ""
      timelineGroupField: ""
      timelineTitleField: ""
      timelineColorField: ""
      timelineScale: ""
      timelineAnchor: ""
      timelineColumnSizeMode: ""
      viewStates:
        table:
          groupByField: tags
tags:
  - DB
---

