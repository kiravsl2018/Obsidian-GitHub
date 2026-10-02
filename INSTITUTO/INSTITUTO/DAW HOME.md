---
tags:
  - dawhome
Asignatura: Home
cssclasses:
  - daw-home
estudiante: Miguel López Contreras
curso: 1º DAW · 2026/27
foco: ""
---

> [!⚡] **ACCESOS RÁPIDOS**
> ```meta-bind-button
> style: default
> label: 🕒 Horario
> actions:
>   - type: open
>     link: "[[Horario]]"
> ```
>
> ```meta-bind-button
> style: default
> label: 🔍 Buscar
> actions:
>   - type: command
>     command: "omnisearch:show-modal"
> ```
>
> ```meta-bind-button
> style: default
> label: 🗂️ Nuevo Kanban
> actions:
>   - type: command
>     command: "obsidian-kanban:create-new-kanban-board"
> ```
>
> ```meta-bind-button
> style: default
> label: ➕ Nota desde plantilla
> actions:
>   - type: command
>     command: "templater-obsidian:create-new-note-from-template"
> ```

🎯 **Foco actual:** `INPUT[text(placeholder(¿En qué te centras ahora?)):foco]`

```dataviewjs
/* ==========================================================================
   DAW HOME · panel de control
   - Todo lo que puedes querer cambiar está en CFG (aquí abajo).
   - El horario NO está aquí: vive en la nota "Horario" (una tabla editable).
   - Las fechas se leen de: la propia tarea (📅 2026-10-15), las propiedades
     Fecha / Entrega de la nota, o el nombre de la nota (2026-10-15 - ...).
   ========================================================================== */

const CFG = {
  DIAS_VENTANA: 14,        // días hacia delante en "Próximos"
  DIAS_ENTREGAS: 7,        // días del contador "Entregas"
  RECIENTES: 8,            // notas en "Recientes"
  COLORES: {               // color de cada asignatura (tildes y mayúsculas no importan)
    BADAT: '#00e5ff', 'PROGRAMACIÓN': '#7c4dff', SISTEMAS: '#f2994a', ENTORNO: '#a3e635',
    LENGUAJE: '#ff6fb5', 'DIGITALIZACIÓN': '#4f9dff', SOSTENIBILIDAD: '#34d399', IPE: '#fbbf24',
  },
  ALIAS: {                 // valor de la propiedad "Asignatura" -> nombre usado en el horario
    'base de datos': 'BADAT', 'bases de datos': 'BADAT',
    'entornos de desarrollo': 'ENTORNO', 'lenguajes de marcas': 'LENGUAJE',
  },
  TIPOS: {
    examen:    { etiqueta: 'Examen',    icono: '🚨', color: '#ff3366' },
    practica:  { etiqueta: 'Práctica',  icono: '💻', color: '#00e5ff' },
    actividad: { etiqueta: 'Actividad', icono: '📝', color: '#a3e635' },
    tarea:     { etiqueta: 'Tarea',     icono: '✅', color: '#a78bfa' },
  },
};

/* ---------- utilidades ---------- */
const APP = dv.app ?? app;
const ACTUAL = dv.current();
const BASE = ACTUAL.file.folder;                                  // p. ej. "INSTITUTO"
const ruta = (s) => (BASE ? BASE + '/' + s : s);
const norm = (s) => String(s ?? '').normalize('NFD').replace(/[\u0300-\u036f]/g, '').toLowerCase().trim();
const hexRgb = (h) => { const n = parseInt(h.replace('#', ''), 16); return [(n >> 16) & 255, (n >> 8) & 255, n & 255].join(','); };
const pad = (n) => String(n).padStart(2, '0');
const hhmm = (m) => Math.floor(m / 60) + ':' + pad(m % 60);
const dur = (m) => (m >= 60 ? Math.floor(m / 60) + ' h' + (m % 60 ? ' ' + (m % 60) + ' min' : '') : m + ' min');
const dia0 = (d) => new Date(d.getFullYear(), d.getMonth(), d.getDate());
const difDias = (a, b) => Math.round((Date.UTC(b.getFullYear(), b.getMonth(), b.getDate()) - Date.UTC(a.getFullYear(), a.getMonth(), a.getDate())) / 864e5);
const cap = (s) => s.charAt(0).toUpperCase() + s.slice(1);
const DIAS = ['Lunes', 'Martes', 'Miércoles', 'Jueves', 'Viernes'];

function el(padre, tag, cls, texto, attrs) {
  const e = document.createElement(tag);
  if (cls) e.className = cls;
  if (texto != null) e.textContent = texto;
  if (attrs) for (const k in attrs) e.setAttribute(k, attrs[k]);
  padre.appendChild(e);
  return e;
}

const COL = {};
for (const k in CFG.COLORES) COL[norm(k)] = CFG.COLORES[k];
const PALETA = ['#a78bfa', '#38bdf8', '#fb7185', '#facc15', '#4ade80', '#f472b6'];
function colorDe(materia) {
  const k = norm(materia);
  if (COL[k]) return COL[k];
  let h = 0; for (const c of k) h = (h * 31 + c.charCodeAt(0)) >>> 0;
  return PALETA[h % PALETA.length];
}

/* ---------- contenedor + estilos ---------- */
const root = el(dv.container, 'div', 'dh');
el(root, 'style', null, `
.markdown-source-view.daw-home, .markdown-preview-view.daw-home { --file-line-width: 1180px; }
.daw-home .callout[data-callout="⚡"] { max-width: none; }
.dh { container-type: inline-size; display: flex; flex-direction: column; gap: 16px; text-align: left; line-height: 1.35; }
.dh, .dh * { box-sizing: border-box; }
.dh a.dh-link { color: var(--text-normal); text-decoration: none; cursor: pointer; font-weight: 600; }
.dh a.dh-link:hover { color: var(--interactive-accent); text-decoration: underline; }
.dh-card { background: var(--background-secondary); border: 1px solid var(--background-modifier-border); border-radius: 14px; padding: 14px 16px; min-width: 0; }
.dh-titulo { display: flex; justify-content: space-between; align-items: baseline; gap: 8px; font-size: .74em; font-weight: 800; letter-spacing: .09em; text-transform: uppercase; color: var(--text-muted); margin-bottom: 10px; }
.dh-titulo small { font-weight: 500; letter-spacing: 0; text-transform: none; }
.dh-vacio { color: var(--text-muted); font-style: italic; padding: 6px 2px; }
.dh-chip { display: inline-flex; align-items: center; gap: 4px; padding: 1px 9px; border-radius: 999px; font-size: .74em; font-weight: 700; white-space: nowrap; background: rgba(var(--c), .16); color: rgb(var(--c)); }
.dh-chips { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 4px; }
.dh-hero { background: linear-gradient(135deg, rgba(124,77,255,.24), rgba(0,229,255,.07) 70%); border: 1px solid rgba(124,77,255,.4); border-radius: 16px; padding: 18px 20px; display: grid; grid-template-columns: minmax(0,1.1fr) minmax(0,1.5fr); gap: 18px; align-items: center; }
.dh-saludo { font-size: 1.75em; font-weight: 800; line-height: 1.1; }
.dh-fecha-hoy { color: var(--text-muted); margin-top: 6px; }
.dh-stats { display: grid; grid-template-columns: repeat(4, minmax(0,1fr)); gap: 10px; }
.dh-stat { background: rgba(0,0,0,.18); border: 1px solid var(--background-modifier-border); border-radius: 12px; padding: 10px 12px; }
.dh-stat b { display: block; font-size: 1.55em; line-height: 1.1; }
.dh-stat span { font-size: .72em; color: var(--text-muted); text-transform: uppercase; letter-spacing: .05em; }
.dh-stat small { display: block; font-size: .74em; color: var(--text-muted); margin-top: 2px; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
.dh-stat.rojo b { color: #ff5d7a; } .dh-stat.naranja b { color: #f2994a; } .dh-stat.verde b { color: #a3e635; }
.dh-dos { display: grid; grid-template-columns: repeat(2, minmax(0,1fr)); gap: 16px; }
.dh-cols { display: grid; grid-template-columns: minmax(0,1.5fr) minmax(0,1fr); gap: 16px; align-items: start; }
.dh-clase { border-left: 5px solid rgb(var(--c)); }
.dh-clase-nombre { font-size: 1.5em; font-weight: 800; line-height: 1.15; }
.dh-clase-nombre a { color: rgb(var(--c)) !important; }
.dh-clase-meta { color: var(--text-muted); margin-top: 4px; }
.dh-barra { height: 7px; border-radius: 99px; background: var(--background-modifier-border); overflow: hidden; margin-top: 10px; }
.dh-barra > i { display: block; height: 100%; border-radius: 99px; background: rgb(var(--c)); }
.dh-grupo { font-size: .76em; font-weight: 800; letter-spacing: .06em; text-transform: uppercase; margin: 12px 0 4px; display: flex; gap: 8px; align-items: center; }
.dh-grupo:first-of-type { margin-top: 0; }
.dh-grupo em { font-style: normal; font-weight: 600; color: var(--text-muted); letter-spacing: 0; text-transform: none; }
.dh-g-v { color: #ff5d7a; } .dh-g-h { color: #f2994a; } .dh-g-p { color: #fbbf24; } .dh-g-o { color: var(--text-muted); }
.dh-item { display: grid; grid-template-columns: 52px minmax(0,1fr) auto; gap: 12px; align-items: center; padding: 8px 4px; border-bottom: 1px solid var(--background-modifier-border); }
.dh-item:last-child { border-bottom: 0; }
.dh-fecha { text-align: center; border-radius: 10px; padding: 5px 0; background: rgba(var(--u), .14); color: rgb(var(--u)); line-height: 1.05; }
.dh-fecha b { display: block; font-size: 1.25em; } .dh-fecha span { font-size: .7em; text-transform: uppercase; font-weight: 700; }
.dh-u-v { --u: 255,93,122; } .dh-u-h { --u: 242,153,74; } .dh-u-p { --u: 251,191,36; } .dh-u-o { --u: 160,160,175; } .dh-u-n { --u: 160,160,175; }
.dh-rel { font-size: .8em; font-weight: 700; color: rgb(var(--u)); white-space: nowrap; }
.dh-item-titulo { overflow: hidden; text-overflow: ellipsis; }
.dh-mas { color: var(--text-muted); font-size: .85em; margin-top: 10px; }
.dh-materias { display: grid; grid-template-columns: repeat(auto-fill, minmax(215px, 1fr)); gap: 12px; }
.dh-materia { border-top: 4px solid rgb(var(--c)); padding: 12px 14px; background: var(--background-secondary); border-radius: 12px; border-left: 1px solid var(--background-modifier-border); border-right: 1px solid var(--background-modifier-border); border-bottom: 1px solid var(--background-modifier-border); }
.dh-materia-nombre { font-weight: 800; font-size: 1.05em; }
.dh-materia-nombre a { color: rgb(var(--c)) !important; }
.dh-materia-meta { display: flex; justify-content: space-between; font-size: .8em; color: var(--text-muted); margin-top: 6px; }
.dh-materia-prox { font-size: .8em; margin-top: 6px; min-height: 1.2em; }
.dh details { margin-top: 8px; font-size: .85em; }
.dh details > summary { cursor: pointer; color: var(--text-muted); }
.dh details ul { list-style: none; margin: 6px 0 0; padding: 0; } .dh details li { padding: 2px 0; }
.dh-reciente { display: flex; justify-content: space-between; align-items: center; gap: 10px; padding: 7px 2px; border-bottom: 1px solid var(--background-modifier-border); }
.dh-reciente:last-child { border-bottom: 0; }
.dh-reciente-t { min-width: 0; overflow: hidden; text-overflow: ellipsis; white-space: nowrap; }
.dh-hace { font-size: .78em; color: var(--text-muted); white-space: nowrap; }
.dh-scroll { overflow-x: auto; }
.dh-rejilla { display: grid; grid-template-columns: 92px repeat(5, minmax(0, 1fr)); gap: 5px; min-width: 720px; }
.dh-celda { display: flex; align-items: center; justify-content: center; min-width: 0; padding: 7px 6px; border-radius: 8px; text-align: center; font-size: .82em; overflow-wrap: anywhere; }
.dh-celda a.dh-link { color: inherit; font-weight: inherit; }
.dh-cab { color: var(--text-muted); font-weight: 700; }
.dh-cab.hoy { color: var(--interactive-accent); background: rgba(124,77,255,.15); }
.dh-hora { color: var(--text-muted); font-size: .75em; white-space: nowrap; }
.dh-descanso { background: var(--background-primary-alt); color: var(--text-faint); font-size: .72em; }
.dh-col-hoy { box-shadow: inset 0 0 0 1px rgba(124,77,255,.35); }
.dh-ahora { outline: 2px solid currentColor; outline-offset: -2px; }
.dh-accesos { display: flex; flex-wrap: wrap; gap: 8px; }
.dh-acceso { padding: 5px 12px; border-radius: 999px; border: 1px solid var(--background-modifier-border); background: var(--background-secondary); font-size: .85em; }
@container (max-width: 760px) {
  .dh-hero, .dh-dos, .dh-cols { grid-template-columns: minmax(0,1fr); }
  .dh-stats { grid-template-columns: repeat(2, minmax(0,1fr)); }
}
`);

function chip(padre, texto, color) {
  const c = el(padre, 'span', 'dh-chip', texto);
  c.style.setProperty('--c', hexRgb(color));
  return c;
}
function enlace(padre, destino, texto, cls) {
  const a = el(padre, 'a', cls || 'dh-link', texto, { 'data-dh-href': destino });
  a.addEventListener('click', (ev) => {
    ev.preventDefault();
    APP.workspace.openLinkText(destino, ACTUAL.file.path, ev.ctrlKey || ev.metaKey);
  });
  a.addEventListener('mouseover', (ev) => {
    try { APP.workspace.trigger('hover-link', { event: ev, source: 'preview', hoverParent: { hoverPopover: null }, targetEl: a, linktext: destino, sourcePath: ACTUAL.file.path }); } catch (e) { /* sin vista previa */ }
  });
  return a;
}

/* ---------- 1. HORARIO (se lee de la nota "Horario") ---------- */
const esDescanso = (s) => /^(☕|descanso|recreo)$/i.test(s);
async function cargarHorario() {
  let raw = '';
  try { raw = (await dv.io.load(ruta('Horario.md'))) ?? ''; } catch (e) { raw = ''; }
  const aMin = (h) => { const m = /(\d{1,2}):(\d{2})/.exec(h || ''); return m ? +m[1] * 60 + +m[2] : NaN; };
  const limpia = (c) => c.replace(/\[\[([^\]|]+)(?:\|([^\]]+))?\]\]/g, (_, a, b) => b || a).replace(/[*_`]/g, '').trim();
  const slots = [];
  for (const linea of raw.split('\n')) {
    const t = linea.trim();
    if (!t.startsWith('|')) continue;
    const c = t.replace(/^\||\|$/g, '').split('|').map(limpia);
    const ini = aMin(c[0]), fin = aMin(c[1]);
    if (isNaN(ini) || isNaN(fin)) continue;                 // cabecera y separador
    slots.push({ ini, fin, dias: [0, 1, 2, 3, 4].map((i) => c[2 + i] ?? '') });
  }
  return slots.sort((a, b) => a.ini - b.ini);
}
const slots = await cargarHorario();

/* ---------- 2. DATOS: tareas, fechas y asignaturas ---------- */
const EXCLUIDAS = [ruta('Plantillas/'), ruta('database/')];
const incluir = (p) => p.file.path !== ACTUAL.file.path && p.file.name !== 'DATABASE NOTAS DAW' && !EXCLUIDAS.some((x) => p.file.path.startsWith(x));
const paginas = Array.from(dv.pages(BASE ? '"' + BASE + '"' : '')).filter(incluir);
const tagsDe = (p) => Array.from(p.file.tags ?? []).map((t) => String(t).toLowerCase());

const notaMateria = {};                                      // NOMBRE -> ruta de su nota
for (const p of paginas) if (tagsDe(p).includes('#asignatura')) notaMateria[norm(p.file.name)] = p.file.path;

const MATERIAS = [];
const nuevaMateria = (m) => { if (m && !esDescanso(m) && !MATERIAS.some((x) => norm(x) === norm(m))) MATERIAS.push(m); };
for (const s of slots) s.dias.forEach(nuevaMateria);
for (const p of paginas) if (tagsDe(p).includes('#asignatura')) nuevaMateria(p.file.name);
Object.keys(CFG.COLORES).forEach(nuevaMateria);
MATERIAS.sort((a, b) => a.localeCompare(b, 'es'));

function canon(nombre) {
  const n = norm(nombre);
  return MATERIAS.find((m) => norm(m) === n) ?? CFG.ALIAS[n] ?? null;
}
function materiaCarpeta(p) {
  const rel = BASE ? p.file.path.slice(BASE.length + 1) : p.file.path;
  const m = /^Asignaturas\/[^/]+\/([^/]+)\//.exec(rel);
  return m ? canon(m[1]) : null;
}
function materiaDe(p) {
  const c = materiaCarpeta(p);
  if (c) return c;
  const a = p.Asignatura ?? p.asignatura;
  if (a) { const x = canon(Array.isArray(a) ? a[0] : a); if (x) return x; }
  const nom = norm(p.file.name);
  return MATERIAS.find((m) => nom.includes(norm(m))) ?? null;
}

function aFecha(v) {
  if (v == null || v === '') return null;
  if (typeof v.toJSDate === 'function') return dia0(v.toJSDate());
  if (v instanceof Date) return dia0(v);
  const s = String(v);
  let m = /(\d{4})-(\d{2})-(\d{2})/.exec(s);
  if (m) return new Date(+m[1], +m[2] - 1, +m[3]);
  m = /(\d{1,2})\/(\d{1,2})\/(\d{4})/.exec(s);
  return m ? new Date(+m[3], +m[2] - 1, +m[1]) : null;
}
function fechaPagina(p) {
  for (const k of ['Fecha', 'fecha', 'Entrega', 'entrega']) { const d = aFecha(p[k]); if (d) return d; }
  const m = /^(\d{4})-(\d{2})-(\d{2})/.exec(p.file.name);    // notas del Calendario: 2026-10-02 ...
  return m ? new Date(+m[1], +m[2] - 1, +m[3]) : null;
}
const RE_TIPO = /#(examen(?:es)?|pr[aá]cticas?|actividad(?:es)?)(?![\w-])/i;
const RE_FECHA_TAREA = [/(?:📅|🗓️?)\s*(\d{4}-\d{2}-\d{2})/, /(?:due|fecha|entrega|vence)\s*::\s*(\d{4}-\d{2}-\d{2})/i];
function tipoDe(texto) {
  const m = RE_TIPO.exec(texto);
  if (!m) return null;
  const t = norm(m[1]);
  return t.startsWith('ex') ? 'examen' : t.startsWith('pra') ? 'practica' : 'actividad';
}
function fechaTarea(texto) {
  for (const re of RE_FECHA_TAREA) { const m = re.exec(texto); if (m) return aFecha(m[1]); }
  return null;
}
const limpiarTitulo = (t) => t.replace(/\[?\(?(?:due|fecha|entrega|vence)\s*::[^\])]*[\])]?/gi, '').replace(/(?:📅|🗓️?|⏳|🛫|✅|➕)\s*\d{4}-\d{2}-\d{2}/g, '').replace(/#[\p{L}\p{N}_\/-]+/gu, '').replace(/\s+/g, ' ').trim();

const GENERICO = /^(entregar pr[aá]ctica|estudiar para el examen)$/i;   // texto que ponen las plantillas
const items = [];
for (const p of paginas) {
  const dPag = fechaPagina(p), mat = materiaDe(p);
  const tareas = Array.from(p.file.tasks ?? []);
  const relevantes = tareas.filter((t) => tipoDe(t.text) || fechaTarea(t.text));
  for (const t of relevantes) {
    items.push({ tipo: tipoDe(t.text) ?? 'tarea', titulo: ((x) => (!x || GENERICO.test(x) ? p.file.name : x))(limpiarTitulo(t.text)), fecha: fechaTarea(t.text) ?? dPag,
      hecha: !!t.completed, materia: mat, pagina: p.file.path, esTarea: true });
  }
  // nota de examen/práctica sin tareas etiquetadas: cuenta como un elemento por sí misma
  if (!relevantes.some((t) => tipoDe(t.text)) && dPag) {
    const tg = tagsDe(p);
    const tp = tg.includes('#examen') ? 'examen' : tg.includes('#practica') ? 'practica' : null;
    if (tp) items.push({ tipo: tp, titulo: p.file.name, fecha: dPag, hecha: false, materia: mat, pagina: p.file.path, esTarea: false });
  }
}
const pend = items.filter((i) => !i.hecha);
const porFecha = (a, b) => a.fecha - b.fecha;

/* ---------- 3. AHORA / SIGUIENTE ---------- */
function bloque(i, dd) {                                     // une franjas contiguas de la misma asignatura
  const mat = slots[i].dias[dd];
  let a = i, b = i;
  while (a > 0 && slots[a - 1].fin === slots[a].ini && slots[a - 1].dias[dd] === mat) a--;
  while (b < slots.length - 1 && slots[b + 1].ini === slots[b].fin && slots[b + 1].dias[dd] === mat) b++;
  return { materia: mat, ini: slots[a].ini, fin: slots[b].fin };
}
function calcular(ahora) {
  const dia = (ahora.getDay() + 6) % 7, min = ahora.getHours() * 60 + ahora.getMinutes();
  let actual = null;
  if (dia <= 4) { const i = slots.findIndex((s) => s.ini <= min && min < s.fin); if (i >= 0) actual = bloque(i, dia); }
  let siguiente = null;
  for (let d = 0; d <= 7 && !siguiente; d++) {
    const f = new Date(ahora.getFullYear(), ahora.getMonth(), ahora.getDate() + d), dd = (f.getDay() + 6) % 7;
    if (dd > 4) continue;
    for (let i = 0; i < slots.length; i++) {
      const mat = slots[i].dias[dd];
      if (!mat || esDescanso(mat)) continue;
      if (d === 0 && (actual ? slots[i].ini < actual.fin : slots[i].ini <= min)) continue;
      siguiente = { ...bloque(i, dd), d, dd, fecha: f };
      break;
    }
  }
  return { dia, min, actual, siguiente };
}

function pintarAhora(cardA, cardS) {
  const ahora = new Date();
  cardA.replaceChildren(); cardS.replaceChildren();
  el(cardA, 'div', 'dh-titulo', 'Ahora');
  el(cardS, 'div', 'dh-titulo', 'Siguiente');
  if (!slots.length) {
    el(cardA, 'div', 'dh-vacio', 'No encuentro la tabla de la nota «Horario».');
    el(cardS, 'div', 'dh-vacio', '—');
    return;
  }
  const { dia, min, actual, siguiente } = calcular(ahora);
  if (actual && actual.materia && !esDescanso(actual.materia)) {
    cardA.style.setProperty('--c', hexRgb(colorDe(actual.materia)));
    cardA.classList.add('dh-clase');
    const n = el(cardA, 'div', 'dh-clase-nombre');
    if (notaMateria[norm(actual.materia)]) enlace(n, notaMateria[norm(actual.materia)], actual.materia); else n.textContent = actual.materia;
    el(cardA, 'div', 'dh-clase-meta', hhmm(actual.ini) + ' – ' + hhmm(actual.fin) + ' · quedan ' + dur(actual.fin - min));
    const b = el(cardA, 'div', 'dh-barra'); const i = el(b, 'i');
    i.style.width = Math.max(2, Math.min(100, Math.round(((min - actual.ini) / (actual.fin - actual.ini)) * 100))) + '%';
  } else if (actual) {
    cardA.classList.remove('dh-clase');
    el(cardA, 'div', 'dh-clase-nombre', esDescanso(actual.materia) ? '☕ Descanso' : 'Hora libre');
    el(cardA, 'div', 'dh-clase-meta', 'hasta las ' + hhmm(actual.fin) + ' · quedan ' + dur(actual.fin - min));
  } else {
    cardA.classList.remove('dh-clase');
    el(cardA, 'div', 'dh-clase-nombre', dia > 4 ? 'Fin de semana' : min < slots[0].ini ? 'Aún sin clase' : 'Clases terminadas');
    el(cardA, 'div', 'dh-clase-meta', dia > 4 ? 'Descansa o adelanta tareas' : min < slots[0].ini ? 'La primera clase empieza a las ' + hhmm(slots[0].ini) : 'Hasta aquí por hoy');
  }
  if (siguiente) {
    cardS.style.setProperty('--c', hexRgb(colorDe(siguiente.materia)));
    cardS.classList.add('dh-clase');
    const n = el(cardS, 'div', 'dh-clase-nombre');
    if (notaMateria[norm(siguiente.materia)]) enlace(n, notaMateria[norm(siguiente.materia)], siguiente.materia); else n.textContent = siguiente.materia;
    const cuando = siguiente.d === 0 ? 'a las ' + hhmm(siguiente.ini) + ' · en ' + dur(siguiente.ini - min)
      : siguiente.d === 1 ? 'mañana a las ' + hhmm(siguiente.ini)
      : DIAS[siguiente.dd].toLowerCase() + ' a las ' + hhmm(siguiente.ini);
    el(cardS, 'div', 'dh-clase-meta', cuando + ' (hasta las ' + hhmm(siguiente.fin) + ')');
  } else {
    cardS.classList.remove('dh-clase');
    el(cardS, 'div', 'dh-vacio', 'No hay más clases en el horario.');
  }
}

/* ---------- 4. PINTAR EL PANEL ---------- */
const hoy = dia0(new Date());
const nombre = String(ACTUAL.estudiante ?? '').split(' ')[0];

// 4.1 cabecera + contadores
const proximoExamen = pend.filter((i) => i.tipo === 'examen' && i.fecha && difDias(hoy, i.fecha) >= 0).sort(porFecha)[0];
const vencidas = pend.filter((i) => i.fecha && difDias(hoy, i.fecha) < 0);
const entregas = pend.filter((i) => i.tipo !== 'examen' && i.fecha && difDias(hoy, i.fecha) >= 0 && difDias(hoy, i.fecha) <= CFG.DIAS_ENTREGAS);
const hero = el(root, 'div', 'dh-hero');
const hl = el(hero, 'div');
const h = new Date().getHours();
el(hl, 'div', 'dh-saludo', (h < 6 ? 'Buenas noches' : h < 13 ? 'Buenos días' : h < 21 ? 'Buenas tardes' : 'Buenas noches') + (nombre ? ', ' + nombre : ''));
el(hl, 'div', 'dh-fecha-hoy', cap(new Date().toLocaleDateString('es-ES', { weekday: 'long', day: 'numeric', month: 'long', year: 'numeric' })) + (ACTUAL.curso ? ' · ' + ACTUAL.curso : ''));
if (ACTUAL.foco) el(hl, 'div', 'dh-fecha-hoy', '🎯 ' + ACTUAL.foco);
const st = el(hero, 'div', 'dh-stats');
function stat(valor, etiqueta, sub, clase) {
  const s = el(st, 'div', 'dh-stat' + (clase ? ' ' + clase : ''));
  el(s, 'b', null, valor); el(s, 'span', null, etiqueta); if (sub) el(s, 'small', null, sub);
}
const relTxt = (d) => (d == null ? 'sin fecha' : d < -1 ? 'hace ' + -d + ' días' : d === -1 ? 'ayer' : d === 0 ? 'hoy' : d === 1 ? 'mañana' : 'en ' + d + ' días');
stat(proximoExamen ? String(difDias(hoy, proximoExamen.fecha)) : '—', 'días al examen', proximoExamen ? (proximoExamen.materia ?? proximoExamen.titulo) : 'ninguno con fecha', proximoExamen ? 'rojo' : '');
stat(String(entregas.length), 'entregas ' + CFG.DIAS_ENTREGAS + ' días', entregas[0] ? 'la primera: ' + relTxt(difDias(hoy, entregas.sort(porFecha)[0].fecha)) : 'nada a la vista', entregas.length ? 'naranja' : 'verde');
stat(String(pend.filter((i) => i.esTarea).length), 'tareas pendientes', null);
stat(String(vencidas.length), 'vencidas', vencidas.length ? 'marca las que ya hiciste' : 'estás al día', vencidas.length ? 'rojo' : 'verde');

// 4.2 ahora / siguiente (se refresca cada 30 s)
const dos = el(root, 'div', 'dh-dos');
const cardA = el(dos, 'div', 'dh-card'), cardS = el(dos, 'div', 'dh-card');
pintarAhora(cardA, cardS);
const reloj = setInterval(() => { if (!root.isConnected) { clearInterval(reloj); return; } pintarAhora(cardA, cardS); }, 30000);

// 4.3 próximos + recientes
const cols = el(root, 'div', 'dh-cols');
const cardP = el(cols, 'div', 'dh-card');
el(cardP, 'div', 'dh-titulo').innerHTML = '';
{ const t = cardP.lastChild; el(t, 'span', null, 'Próximos ' + CFG.DIAS_VENTANA + ' días'); el(t, 'small', null, 'fecha de la tarea, de la nota o del nombre'); }

function fila(padre, it) {
  const d = it.fecha ? difDias(hoy, it.fecha) : null;
  const u = d == null ? 'n' : d < 0 ? 'v' : d === 0 ? 'h' : d <= 3 ? 'p' : 'o';
  const f = el(padre, 'div', 'dh-item dh-u-' + u);
  const b = el(f, 'div', 'dh-fecha');
  if (it.fecha) { el(b, 'b', null, String(it.fecha.getDate())); el(b, 'span', null, it.fecha.toLocaleDateString('es-ES', { month: 'short' }).replace('.', '')); } else el(b, 'b', null, '—');
  const m = el(f, 'div');
  enlace(el(m, 'div', 'dh-item-titulo'), it.pagina, it.titulo);
  const cs = el(m, 'div', 'dh-chips');
  chip(cs, CFG.TIPOS[it.tipo].icono + ' ' + CFG.TIPOS[it.tipo].etiqueta, CFG.TIPOS[it.tipo].color);
  if (it.materia) chip(cs, it.materia, colorDe(it.materia));
  el(f, 'div', 'dh-rel', relTxt(d));
}
function grupo(titulo, clase, lista, nota) {
  if (!lista.length) return;
  const g = el(cardP, 'div', 'dh-grupo ' + clase, titulo); if (nota) el(g, 'em', null, nota);
  lista.forEach((it) => fila(cardP, it));
}
const conFecha = pend.filter((i) => i.fecha).sort(porFecha);
const dd = (i) => difDias(hoy, i.fecha);
const gVenc = conFecha.filter((i) => dd(i) < 0), gHoy = conFecha.filter((i) => dd(i) === 0);
const gSem = conFecha.filter((i) => dd(i) >= 1 && dd(i) <= 7), gSig = conFecha.filter((i) => dd(i) >= 8 && dd(i) <= CFG.DIAS_VENTANA);
const gMas = conFecha.filter((i) => dd(i) > CFG.DIAS_VENTANA), gSin = pend.filter((i) => !i.fecha && i.esTarea);
grupo('Vencido', 'dh-g-v', gVenc, 'sigue sin marcar');
grupo('Hoy', 'dh-g-h', gHoy);
grupo('Próximos 7 días', 'dh-g-p', gSem);
grupo('Semana siguiente', 'dh-g-o', gSig);
if (!gVenc.length && !gHoy.length && !gSem.length && !gSig.length) {
  el(cardP, 'div', 'dh-vacio', 'Nada urgente en los próximos ' + CFG.DIAS_VENTANA + ' días. Para que algo aparezca aquí, ponle fecha: «📅 2026-10-15» en la tarea, o rellena Fecha / Entrega en la nota.');
}
if (gMas.length) el(cardP, 'div', 'dh-mas', '+ ' + gMas.length + ' más adelante (el siguiente: ' + relTxt(dd(gMas[0])) + ')');
if (gSin.length) {
  const dt = el(cardP, 'details'); el(dt, 'summary', null, 'Sin fecha (' + gSin.length + ')');
  const ul = el(dt, 'div'); gSin.forEach((it) => fila(ul, it));
}

const cardR = el(cols, 'div', 'dh-card');
{ const t = el(cardR, 'div', 'dh-titulo'); el(t, 'span', null, 'Recientes'); }
const recientes = paginas
  .slice().sort((a, b) => b.file.mtime.toMillis() - a.file.mtime.toMillis()).slice(0, CFG.RECIENTES);
const hace = (ms) => {
  const s = Math.round((Date.now() - ms) / 1000), rtf = new Intl.RelativeTimeFormat('es', { numeric: 'auto' });
  return s < 60 ? 'ahora mismo' : s < 3600 ? rtf.format(-Math.round(s / 60), 'minute') : s < 86400 ? rtf.format(-Math.round(s / 3600), 'hour') : rtf.format(-Math.round(s / 86400), 'day');
};
if (!recientes.length) el(cardR, 'div', 'dh-vacio', 'Sin notas todavía.');
for (const p of recientes) {
  const r = el(cardR, 'div', 'dh-reciente');
  const l = el(r, 'div', 'dh-reciente-t'); enlace(l, p.file.path, p.file.name);
  const m = materiaDe(p); if (m && norm(m) !== norm(p.file.name)) { l.appendChild(document.createTextNode(' ')); chip(l, m, colorDe(m)); }
  el(r, 'div', 'dh-hace', hace(p.file.mtime.toMillis()));
}

// 4.4 progreso por asignatura
const cardM = el(root, 'div', 'dh-card');
{ const t = el(cardM, 'div', 'dh-titulo'); el(t, 'span', null, 'Asignaturas'); el(t, 'small', null, 'progreso = tareas marcadas / tareas con etiqueta o fecha'); }
const rejilla = el(cardM, 'div', 'dh-materias');
for (const m of MATERIAS) {
  const tareasM = items.filter((i) => i.esTarea && i.materia === m);
  const hechas = tareasM.filter((i) => i.hecha).length, total = tareasM.length;
  const prox = pend.filter((i) => i.materia === m && i.fecha && difDias(hoy, i.fecha) >= 0).sort(porFecha)[0];
  const venc = pend.filter((i) => i.materia === m && i.fecha && difDias(hoy, i.fecha) < 0).length;
  const notas = paginas.filter((p) => materiaCarpeta(p) === m && p.file.path !== notaMateria[norm(m)]).sort((a, b) => a.file.name.localeCompare(b.file.name, 'es'));
  const c = el(rejilla, 'div', 'dh-materia'); c.style.setProperty('--c', hexRgb(colorDe(m)));
  const n = el(c, 'div', 'dh-materia-nombre');
  if (notaMateria[norm(m)]) enlace(n, notaMateria[norm(m)], m); else n.textContent = m;
  const b = el(c, 'div', 'dh-barra'); el(b, 'i').style.width = (total ? Math.round((hechas / total) * 100) : 0) + '%';
  const meta = el(c, 'div', 'dh-materia-meta'); el(meta, 'span', null, total ? hechas + '/' + total + ' tareas' : 'sin tareas'); el(meta, 'span', null, '📄 ' + notas.length);
  const px = el(c, 'div', 'dh-materia-prox');
  if (venc) { px.textContent = '⚠️ ' + venc + ' vencida' + (venc > 1 ? 's' : ''); px.style.color = '#ff5d7a'; }
  else if (prox) { px.textContent = CFG.TIPOS[prox.tipo].icono + ' ' + relTxt(difDias(hoy, prox.fecha)); px.style.color = 'var(--text-muted)'; }
  if (notas.length) {
    const dt = el(c, 'details'); el(dt, 'summary', null, 'Notas (' + notas.length + ')');
    const ul = el(dt, 'ul'); notas.slice(0, 30).forEach((p) => enlace(el(ul, 'li'), p.file.path, p.file.name));
  }
}

// 4.5 horario semanal
const cardH = el(root, 'div', 'dh-card');
{ const t = el(cardH, 'div', 'dh-titulo'); el(t, 'span', null, 'Horario semanal'); const s = el(t, 'small'); enlace(s, ruta('Horario.md'), 'editar horario'); }
if (!slots.length) el(cardH, 'div', 'dh-vacio', 'Crea la nota «Horario» con una tabla (Inicio | Fin | Lunes ... Viernes).');
else {
  const ahora = new Date(), diaHoy = (ahora.getDay() + 6) % 7, minHoy = ahora.getHours() * 60 + ahora.getMinutes();
  const rej = el(el(cardH, 'div', 'dh-scroll'), 'div', 'dh-rejilla');
  el(rej, 'div', 'dh-celda dh-cab');
  DIAS.forEach((d, i) => el(rej, 'div', 'dh-celda dh-cab' + (i === diaHoy ? ' hoy' : ''), d));
  for (const s of slots) {
    el(rej, 'div', 'dh-celda dh-hora', hhmm(s.ini) + ' – ' + hhmm(s.fin));
    s.dias.forEach((mat, i) => {
      const c = el(rej, 'div', 'dh-celda' + (i === diaHoy ? ' dh-col-hoy' : ''));
      if (esDescanso(mat)) { c.classList.add('dh-descanso'); c.textContent = '☕'; return; }
      if (!mat) return;
      const rgb = hexRgb(colorDe(mat)), ahoraMismo = i === diaHoy && s.ini <= minHoy && minHoy < s.fin;
      // colores en línea: ninguna regla de tema o snippet puede pisarlos
      c.style.background = 'rgba(' + rgb + ', ' + (ahoraMismo ? .32 : .16) + ')';
      c.style.color = 'rgb(' + rgb + ')';
      c.style.fontWeight = '700';
      if (ahoraMismo) c.classList.add('dh-ahora');
      if (notaMateria[norm(mat)]) enlace(c, notaMateria[norm(mat)], mat); else c.textContent = mat;
    });
  }
}

// 4.6 accesos
function abrirCalendario() {
  // el comando del plugin no hace nada si la vista ya existe: en ese caso la mostramos
  const hojas = APP.workspace.getLeavesOfType('calendar');
  if (hojas.length) APP.workspace.revealLeaf(hojas[0]);
  else APP.commands.executeCommandById('calendar:show-calendar-view');
}
const ac = el(root, 'div', 'dh-accesos');
{
  const a = el(el(ac, 'span', 'dh-acceso'), 'a', 'dh-link', '📅 Calendario');
  a.addEventListener('click', (ev) => { ev.preventDefault(); abrirCalendario(); });
}
const accesos = [['Guía de uso', '📖 Guía de uso'], ['DATABASE NOTAS DAW', '📊 Notas (hoja de cálculo)'], ['Database Daw', '🗄️ Base de datos DAW'], ['Horario', '🕒 Horario']];
accesos.filter(([n]) => APP.metadataCache.getFirstLinkpathDest(n, ACTUAL.file.path))
  .forEach(([n, etiqueta]) => enlace(el(ac, 'span', 'dh-acceso'), n, etiqueta));
```
