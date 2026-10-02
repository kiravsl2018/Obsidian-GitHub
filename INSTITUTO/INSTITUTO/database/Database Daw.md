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
        - value: plantilla
          color: purple
        - value: practica
          color: pink
        - value: practica-home
          color: red
        - value: temario
          color: lime
        - value: tema-home
          color: teal
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
      recordIconFieldOverrideEnabled: false
      recordIconField: ""
      newRecordFolder: ""
      displayWidth: wide
      sortColumn: ""
      sortDirection: asc
      sortRules: []
      columnOrder:
        - file.name
        - tags
        - Asignatura
        - Prioridad
        - Tema
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
          - Calendario
          - Tasks
          - actividad
          - asignatura
          - dawhome
          - plantilla
          - practica-home
          - temario
          - tema-home
          - csv
          - DB
      showEmptyGroups: {}
      collapsedGroups:
        tags:
          - Calendario
          - csv
          - DB
          - dawhome
          - asignatura
          - plantilla
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

