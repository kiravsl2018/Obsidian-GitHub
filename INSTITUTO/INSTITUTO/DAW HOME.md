---
tags:
  - dawhome
Asignatura: Home
---

```dataviewjs
// 1. CÁLCULO GLOBAL (#actividades)
let pages = dv.pages('#actividades');
let totalTasks = pages.file.tasks;

let pct = 0;
let pendientesCount = 0;
let completadasCount = 0;

if (totalTasks.length > 0) {
    pendientesCount = totalTasks.filter(t => !t.completed).length;
    completadasCount = totalTasks.filter(t => t.completed).length;
    pct = Math.round((completadasCount / totalTasks.length) * 100);
}

// 2. CONSTRUCCIÓN DEL CONTENEDOR PRINCIPAL (ESTADO DEL ARTE)
let html = '<div style="background: linear-gradient(135deg, #1e1e2e 0%, #2b2b3a 100%); border-left: 5px solid #7c4dff; padding: 20px; border-radius: 8px; margin-bottom: 25px; box-shadow: 0 4px 6px rgba(0,0,0,0.1);">';

// Título e Información del Estudiante
html += '<h2 style="margin: 0 0 10px 0; color: #7c4dff; font-size: 1.5em; font-weight: bold;">📊 ESTADO DEL ARTE</h2>';
html += '<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 15px; color: #b3b3b3; font-size: 0.95em;">';
html += '<div>👤 <b>Estudiante:</b> Miguel López Contreras</div>';
html += '<div>🚀 <b>Foco Actual:</b> Superar Programación y BD</div>';
html += '<div>📅 <b>Temporada:</b> Verano 2026</div>';
html += '</div>';

// Separador e Inicio de la sección de progreso unificada
html += '<div style="margin-top: 20px; border-top: 1px solid #313244; padding-top: 15px;">';
html += '<p style="margin: 0 0 8px 0; font-size: 0.9em; color: #bbb; font-weight: bold; letter-spacing: 0.5px;">📈 PROGRESO GLOBAL DE ACTIVIDADES:</p>';

// Envoltura de la barra flex para alinear barra + porcentaje en una sola fila limpia
html += '<div style="display: flex; align-items: center; justify-content: space-between; gap: 15px;">';

// La Barra de Progreso Dinámica (con degradado de Morado/Cian a Verde)
html += '<div style="flex-grow: 1; background: #11111b; border-radius: 20px; height: 12px; overflow: hidden; position: relative;">';
html += '<div style="background: linear-gradient(90deg, #7c4dff 0%, #00e5ff 50%, #a3e635 100%); height: 100%; width: ' + pct + '%; border-radius: 20px; transition: width 0.5s ease;"></div>';
html += '</div>';

// Contador de tareas hechas/totales y Badge del Porcentaje
html += '<div style="flex-shrink: 0; display: flex; align-items: center; gap: 10px;">';
html += '<span style="font-size: 0.8em; color: #a6adc8; font-weight: 500;">(' + completadasCount + '/' + totalTasks.length + ')</span>';
html += '<span style="background: #a3e63522; color: #a3e635; font-family: monospace; font-size: 1em; font-weight: bold; padding: 2px 8px; border-radius: 5px; border: 1px solid #a3e63533;">' + pct + '%</span>';
html += '</div>';

// Cierre de todas las etiquetas contenedoras
html += '</div></div></div>';

// Pintar el panel unificado en la nota
dv.paragraph(html);
```
---
```dataviewjs
// CONSTRUCCIÓN DEL HORARIO EN BLANCO
let html = '<div style="background: #1e1e2e; border: 1px solid #2b2b3a; padding: 20px; border-radius: 8px; margin-top: 20px; box-shadow: 0 4px 6px rgba(0,0,0,0.1); overflow-x: auto;">';

html += '<h3 style="margin: 0 0 15px 0; color: #00e5ff; font-size: 1.3em; font-weight: bold; display: flex; align-items: center; gap: 8px;">📅 HORARIO DE CLASE</h3>';

// Inicio de la tabla estilizada
html += '<table style="width: 100%; border-collapse: separate; border-spacing: 6px; text-align: center; font-size: 0.9em; color: #cdd6f4;">';

// Cabecera con los días de la semana (Colores de acento modernos)
html += '<thead><tr>';
html += '<th style="background: #313244; color: #a6adc8; padding: 10px; border-radius: 4px; font-weight: bold; width: 12%;">Hora</th>';
html += '<th style="background: #7c4dff22; color: #7c4dff; padding: 10px; border-radius: 4px; font-weight: bold; width: 17.6%;">Lunes</th>';
html += '<th style="background: #00e5ff22; color: #00e5ff; padding: 10px; border-radius: 4px; font-weight: bold; width: 17.6%;">Martes</th>';
html += '<th style="background: #a3e63522; color: #a3e635; padding: 10px; border-radius: 4px; font-weight: bold; width: 17.6%;">Miércoles</th>';
html += '<th style="background: #ffb86c22; color: #ffb86c; padding: 10px; border-radius: 4px; font-weight: bold; width: 17.6%;">Jueves</th>';
html += '<th style="background: #ff555522; color: #ff5555; padding: 10px; border-radius: 4px; font-weight: bold; width: 17.6%;">Viernes</th>';
html += '</tr></thead>';

// Cuerpo de la tabla (Filas de ejemplo con horas preparadas)
html += '<tbody>';

// --- FILA 1 ---
html += '<tr>';
html += '<td style="background: #11111b; padding: 12px; border-radius: 4px; font-weight: 500; color: #888;">8:15 - 9:15</td>';
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">BADAT</td>'; // Lunes
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">LENGUAJE</td>'; // Martes
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">IPE</td>'; // Miércoles
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">ENTORNO</td>'; // Jueves
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">BADAT</td>'; // Viernes
html += '</tr>';

// --- FILA 2 ---
html += '<tr>';
html += '<td style="background: #11111b; padding: 12px; border-radius: 4px; font-weight: 500; color: #888;">9:15 - 10:15</td>'; 
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">BADAT</td>';
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">DIGITALIZACIÓN</td>';
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">IPE</td>';
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">PROGRAMACIÓN</td>';
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">BADAT</td>';
html += '</tr>';

// --- FILA 3 ---
html += '<tr>';
html += '<td style="background: #11111b; padding: 12px; border-radius: 4px; font-weight: 500; color: #888;">10:15 - 11:15</td>';
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">SISTEMAS</td>';
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">SOSTENIBILIDAD</td>';
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">ENTORNO</td>';
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">PROGRAMACIÓN</td>';
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">PROGRAMACIÓN</td>';
html += '</tr>';

// --- RECREO O DESCANSO ---
html += '<tr><td colspan="6" style="background: #11111b; padding: 6px; border-radius: 4px; font-size: 0.8em; color: #555; letter-spacing: 2px;">☕ DESCANSO</td></tr>';

// --- FILA 4 ---
html += '<tr>';
html += '<td style="background: #11111b; padding: 12px; border-radius: 4px; font-weight: 500; color: #888;">11:45 - 12:45</td>';
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">SISTEMAS</td>';
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">PROGRAMACIÓN</td>';
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">ENTORNO</td>';
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">LENGUAJE</td>';
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">PROGRAMACIÓN</td>';
html += '</tr>';

// --- FILA 5 ---
html += '<tr>';
html += '<td style="background: #11111b; padding: 12px; border-radius: 4px; font-weight: 500; color: #888;">12:45 - 13:45</td>';
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">PROGRAMACIÓN</td>';
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">PROGRAMACIÓN</td>';
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">BADAT</td>';
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">LENGUAJE</td>';
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">SISTEMAS</td>';
html += '</tr>';

// --- FILA 6 ---
html += '<tr>';
html += '<td style="background: #11111b; padding: 12px; border-radius: 4px; font-weight: 500; color: #888;">13:45 - 14:45</td>';
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">PROGRAMACIÓN</td>';
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">SISTEMAS</td>';
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">BADAT</td>';
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">IPE</td>';
html += '<td style="background: #2b2b3a; padding: 12px; border-radius: 4px; color: #888; font-style: italic;">SISTEMAS</td>';
html += '</tr>';

html += '</tbody></table></div>';

dv.paragraph(html);
```

---
```dataviewjs
let recientes = dv.pages().sort(p => p.file.mday, "desc").slice(0, 5);

let html = '<div style="background: #1e1e2e; border: 1px solid #2b2b3a; padding: 18px; border-radius: 8px; margin-top: 20px; box-shadow: 0 4px 6px rgba(0,0,0,0.1);">';
html += '<h4 style="margin: 0 0 12px 0; color: #a3e635; font-size: 1.1em; font-weight: bold;">⏳ ARCHIVOS RECIENTES</h4>';
html += '<ul style="list-style: none; padding: 0; margin: 0;">';

for (let p of recientes) {
    let fecha = p.file.mday.day + '/' + p.file.mday.month + '/' + p.file.mday.year;
    let rutaLimpia = p.file.name;
    
    html += '<li style="padding: 8px 0; border-bottom: 1px solid #2b2b3a; display: flex; justify-content: space-between; align-items: center; font-size: 0.9em; color: #cdd6f4;">';
    html += '<span>📝 <a class="internal-link" href="' + rutaLimpia + '" style="color: #cdd6f4; text-decoration: none; font-weight: 500;">' + rutaLimpia + '</a></span>';
    html += '<span style="font-size: 0.8em; color: #6c7086; background: #11111b; padding: 2px 6px; border-radius: 4px;">' + fecha + '</span>';
    html += '</li>';
}

html += '</ul></div>';

dv.paragraph(html);
```
---
## 📁ÁRBOL DE CARPETAS
```dataviewjs
let homeName = dv.current().file.name;
let children = dv.pages().where(p => p.file.outlinks.includes(dv.current().file.link));

if (children.length === 0) {
    dv.paragraph('*Aún no hay notas vinculadas directamente a este HOME.*');
} else {
    for (let child of children) {
        dv.el("h3", '📁 ' + child.file.link, { attr: { style: "text-align: left; margin-bottom: 8px;" } });
        
        // Buscamos los nietos (notas que apuntan al hijo, pero que no sean el propio HOME)
        let grandchildren = dv.pages().where(p => p.file.outlinks.includes(child.file.link) && p.file.name !== homeName);
        
        if (grandchildren.length > 0) {
            let listItems = [];
            for (let grandchild of grandchildren) {
                listItems.push('└── 📄 ' + grandchild.file.link);
            }
            dv.list(listItems);
        } else {
            dv.paragraph('<small style="color: #666; margin-left: 20px;">*Sin notas anidadas todavía*</small>');
        }
    }
}
```
---
## 🗂️ RADAR DE ENTREGAS Y EXÁMENES
```dataviewjs
let pages = dv.pages('#examen or #practica').sort(p => p.file.mday, 'desc');

if (pages.length === 0) {
    dv.paragraph('<div style="background: #1e1e2e; padding: 15px; border-radius: 8px; border: 1px solid #2b2b3a; color: #888; font-style: italic; text-align: center;">🎯 ¡Al día! No hay exámenes ni prácticas etiquetadas en tus notas.</div>');
} else {
    let content = '<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 12px; margin-top: 10px;">';
    
    for (let p of pages) {
        let isExamen = p.file.tags.includes('#examen');
        let badgeColor = isExamen ? '#ff3366' : '#00e5ff';
        let badgeText = isExamen ? '🚨 EXAMEN' : '💻 PRÁCTICA';
        
        // Limpiamos el nombre de la nota actual para el título
        let notaLimpia = p.file.name;
        
        // Limpiamos el nombre de la Asignatura
        let linksTo = p.file.outlinks.filter(l => l.path !== dv.current().file.path);
        let asignaturaName = '';
        
        if (linksTo.length > 0) {
            // Extraemos solo el nombre del archivo sin rutas ni .md
            asignaturaName = linksTo[0].path.split('/').pop().replace('.md', '');
        } else {
            asignaturaName = p.file.folder.split('/').pop();
        }
        
        let fechaText = p.file.mday.day + '/' + p.file.mday.month + '/' + p.file.mday.year;
        
        // Construimos la tarjeta con enlaces internos limpios de Obsidian
        content += '<div style="background: #1e1e2e; border: 1px solid #2b2b3a; border-left: 4px solid ' + badgeColor + '; padding: 15px; border-radius: 6px; box-shadow: 0 4px 6px rgba(0,0,0,0.05);">';
        content += '<span style="background: ' + badgeColor + '22; color: ' + badgeColor + '; font-size: 0.75em; font-weight: bold; padding: 3px 8px; border-radius: 4px; display: inline-block; margin-bottom: 8px;">' + badgeText + '</span>';
        
        // Título limpio y clicable
        content += '<h4 style="margin: 0 0 5px 0; font-size: 1.1em;"><a class="internal-link" href="' + notaLimpia + '" style="text-decoration: none; color: inherit;">' + notaLimpia + '</a></h4>';
        
        content += '<div style="font-size: 0.85em; color: #b3b3b3; margin-top: 8px;">';
        
        // Asignatura limpia y clicable
        content += '📚 <b>Asignatura:</b> <a class="internal-link" href="' + asignaturaName + '" style="color: ' + badgeColor + '; font-weight: 500;">' + asignaturaName + '</a><br>';
        
        content += '📅 <b>Modificado:</b> ' + fechaText;
        content += '</div></div>';
    }
    
    content += '</div>';
    dv.paragraph(content);
}
```
---
## ✅ RADAR DE ACTIVIDADES
```dataviewjs
let pages = dv.pages('#actividades or #practica');

// Filtramos las tareas asegurando que el texto de la propia tarea contenga la etiqueta
let totalTasks = pages.file.tasks.filter(t => {
    let texto = t.text.toLowerCase();
    return texto.includes('#actividades') || texto.includes('#practicas');
});

if (totalTasks.length === 0) {
    dv.paragraph('<div style="background: #1e1e2e; padding: 15px; border-radius: 8px; border: 1px solid #2b2b3a; color: #888; text-align: center; font-style: italic;">🎯 ¡Al día! No se han encontrado tareas con #actividades o #practicas.</div>');
} else {
    let pendientes = totalTasks.filter(t => !t.completed);
    let completadas = totalTasks.filter(t => t.completed);
    let pct = totalTasks.length > 0 ? Math.round((completadas.length / totalTasks.length) * 100) : 0;

    let statusHtml = '<div style="background: #1e1e2e; border: 1px solid #2b2b3a; padding: 15px; border-radius: 8px; margin-bottom: 20px; display: flex; justify-content: space-around; text-align: center;">';
    statusHtml += '<div><span style="font-size: 1.5em; font-weight: bold; color: #ff3366;">' + pendientes.length + '</span><br><span style="font-size: 0.8em; color: #888;">PENDIENTES</span></div>';
    statusHtml += '<div><span style="font-size: 1.5em; font-weight: bold; color: #00e5ff;">' + completadas.length + '</span><br><span style="font-size: 0.8em; color: #888;">HECHAS</span></div>';
    statusHtml += '<div><span style="font-size: 1.5em; font-weight: bold; color: #a3e635;">' + pct + '%</span><br><span style="font-size: 0.8em; color: #888;">PROGRESO</span></div>';
    statusHtml += '</div>';
    
    dv.paragraph(statusHtml);

    dv.header(3, '⏳ Actividades / Prácticas Pendientes');
    if (pendientes.length > 0) {
        dv.taskList(pendientes, false);
    } else {
        dv.paragraph('<p style="color: #a3e635; font-style: italic; font-size: 0.9em; margin-left: 10px;">¡Buen trabajo! No quedan tareas pendientes 🎉</p>');
    }

    dv.header(3, '✅ Actividades / Prácticas Completadas');
    if (completadas.length > 0) {
        dv.taskList(completadas, false);
    } else {
        dv.paragraph('<p style="color: #666; font-style: italic; font-size: 0.9em; margin-left: 10px;">Aún no has completado ninguna tarea.</p>');
    }
}
```
---


>[!IMPORTANT] DB AND EXCEL
>[[DATABASE NOTAS DAW]] and [[Database Daw]]

