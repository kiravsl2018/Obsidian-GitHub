---
tags:
  - temario
Asignatura: Base de Datos
To-Do: Pendiente
Tema:
  - Introducción
Prioridad: Media 🟡
---
[[BADAT]] | [[Presentación - BADAT]] 
# **EL ALMACENAMIENTO DE LA INFORMACIÓN**
---

>[!INFO] EXAMEN
>- Tipo Test y de Razonamiento.

## *INTRO*
---
#### ***CONCEPTOS***

- **Sociedad de la información** --> Una sociedad con acceso inmediato a toda la información que se necesite.

- **Informática** --> Ciencia que estudia el tratamiento automático de la *Información*.

-  **Sistema de Información** --> Sistema encargado de gestionar y administrar la información de una empresa u organismo asegurando la *disponibilidad*, la *fiabilidad* y la *seguridad*.
---
## **LOS SITEMAS DE INFORMACIÓN**
---

Es un conjunto de componentes u objetos capaces de **procesar** unos **datos** para obtener una **INFORMACIÓN**. Debe ser **oportuna y relevante, exacta y fiable**. 

#### TIPOS DE SI
-  Con presencia de ordenadores.
-  Sin presencia de ordenadores.
Nos centraremos en los tipos de **SI** con presencia de ordenadores.
#### COMPONENTES DE UN SI

| FÍSICOS                                             | LÓGICOS                                                             | HUMANOS                                                | PROTOCOLOS                                                                                |
| --------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------ | ----------------------------------------------------------------------------------------- |
| Hardware implicado                                  | Software implicado                                                  | Personas implicadas                                    | Normas implicadas                                                                         |
| - Servidores<br>- Equipo cliente<br>- Equipo de red | - S.O. de servidor<br>- S.O de cliente<br>- Herramientas de gestión | - Equipo desarrollo<br>- Administradores<br>- Usuarios | - Protocolos de red<br>- Protocolos de Sist.<br>- Protocolos de Seg.<br>- Normas de datos |

#### OBJETIVOS DE UN S.I.
Se debe garantizar la mejora de gestión de la empresa, facilitar la organización y la planificación. La obtención de la información en tiempo real es muy importante.

Por último, debe ayudar en la toma de decisiones -> **BIGDATA** 


---
## **ALMACENAMIENTO DE DATOS**
---
**Es necesario tener en cuenta estos tres aspectos =**


| DÓNDE                                                                   | CÓMO                                                                 | INTERCAMBIO                                                               |
| ----------------------------------------------------------------------- | -------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| Dónde están físicamente                                                 | Cómo se organizan lógicamente                                        | Intercambio de datos entre S.I.                                           |
| Debe ser un Sist. de almacenamiento **Secundario, Permanente y Seguro** | Siguiendo un *modelo*<br>- Ficheros clásicos<br>- **Bases de datos** | - Ficheros clásicos.<br>- Ficheros XML.<br>- Ficheros JSON.<br>- Otros... |
|                                                                         |                                                                      |                                                                           |

---
## **SISTEMAS DE FICHEROS CLÁSICOS**
---

#### **Archivo/Fichero** -> 
- Estructura de datos, almacenada en memoria secundaria. Agrupada por un nombre
#### **Contenido de los ficheros de datos** ->
- Conjunto de datos, organizados en *registros*. Todos los registros de un fichero serán: del mismo tipo y número indeterminado
#### **Registro de un fichero** -> 
- Cada componente de un archivo. A cada registro de un fichero se podrá acceder por separado, por lo que son *unidades de acceso*. 
Los registros están formados por *campos*. 
#### **Campo clave** -> 
- Todos los ficheros contarán con *un campo o conjunto de campos* en todos los registros que identifiquen de forma única a un registro.

<br>
### ***Modos de organización de los Ficheros Clásicos***
---

> [!info] SECUENCIAL
> Los registros se leen uno a uno. Sencillo pero lento

> [!example] RELATIVA DIRECTA
> Los registros se acceden directamente a la posición en la que están almacenados. Más rápido, con un tamaño limitado y *dependiente de la plataforma*

> [!summary] SECUENCIAL INDEXADA
> Ficheros accesibles por un índice. Cada fichero se leerá secuencialmente, no es limitado y es más rápido que el primero. Aunque más complejo

### ***INCONVENIENTES***
---

- Lentitud en el acceso a datos
- Datos aislados
- Datos redundantes
	- Hay inconsistencia de la información
- Queda en manos de los programadores:
	- La integridad de los datos
	- El control de autorizaciones
	- El control de la concurrencia

---
## **SISTEMAS DE DATOS EN BASE DE DATOS**
---
#### **Base de datos (BD)** ->
- Almacen de datos. 
- *DEFINICIÓN* -> [[#DEFINICIÓN DE BASE DE DATOS]].
#### **Sistema Gestor de BBDD** ->
- Herramientas/interfaces/procesos que gestionan las *Bases de Datos (BBDD)*.
- Surgen en los ***años 60***
- **Objetivo** -> Solucionar los problemas con los Sistemas de Ficheros Clásicos.
- **Proponen** -> La integración de los ficheros de datos, de su estructura y de las aplicaciones que los manejen. 
- *DEFINICIÓN* -> [[#Los Sistemas Gestores de BBDD]]

> [!summary] Características
> - Independencia física y lógica de los datos
> - Disminuición de costes de almacenamiento y mantenimiento
> - Mínima ***redundacia***
> - Máxima ***integridad***
> - Los *Sistemas Gestor de Base de Datos (SGDB)* dispondrán de herramientas que:
> 	- Garanticen que se cumplan las características propias de las BD
> 	- Facilitan el control de la **Seguridad** de las BD
> 	- Facilitan la **Administración** con las aplicaciones, interfaces... necesarias.

>[!WARNING] Recuerda
>Una BD tiene una ***estructura***, siguiendo un modelo de datos

---
## **Modelos de Datos**
---

> [!INFO] Modelo de referencia
> **Modelo ANSI/SPARC**

De éste, se basan los siguientes:

- *Jerárquico y Red* -> Obsoleto || Organización en árbol
- *Orientado a Objetos y Objetos Relacionales.*
- *Relacional*. -> Cada objeto lo tenemos en una tabla, organizada en columnas y filas. || Se relacionan entre sí, debido a sus datos semejantes.
- *NoSQL*.

---
## **MODELO ANSI/SPARC**
---
>[!example] *"DIVIDE Y VENCERAS"*
>Se deben tener en cuenta muchísimas cosas para que los datos estén bien almacenados.
>Al tratarse de un proceso tan complejo:
>- ***Dividimos el trabajo y el control en diferentes niveles***

#### Para que una **DB** sea robusta, se debe contar con estos **3 niveles**:

1. **Almacenamiento físico.** || *Nivel interno*
	1. Almacenamiento de los datos con sus normas y protocolos para ello.
2. **Estructura.** || *Nivel Intermedio*
	1. Estructura de los datos de la empresa vistas de forma global
3. **Visión.** || *Nivel externo*
	1. Visión que tienen cada usuario o grupo de usuario de la base de datos, ya que solo verá la parte para la que está autorizado.

### ***NIVEL INTERNO / ESQUEMA INTERNO***

>[!TEST] Esquema Interno
>- Controla los datos físicamente almacenados en el **Servidor/Servidores**.
>- Gestiona la estructura física con la que se almacenan los datos.
>- Se encarga de garantizar la *Independencia Física* de los datos.

### ***NIVEL INTERMEDIO / ESQUEMA CONCEPTUAL***

>[!tip] Esquema Conceptual
> Representa la *estructura* de la base de datos de toda la empresa.

### ***NIVEL EXTERNO / ESQUEMA EXTERNO***

>[!question] Esquema Externo
>- Habrá uno por cada tipo de usuario.
>- Representa a la visión de la **BD** que tiene cada tipo de usuario.


---
## **DEFINICIÓN DE BASE DE DATOS**
---

>[!important] DEFINICIÓN
> Es una colección de datos almacenados en soporte informático *secundario/permanente* y de *acceso directo*.
> Los datos de una base de datos están lógicamente relacionados entre sí y están estructurados según un modelo de datos.
> > Es decir, los datos no están aislados y pueden seguir un *modelo relacional, orientado a objetos, no-relacionales*...
> 
>Una base de datos tiene que describir un ente (empresa, organismo...) del mundo real, es decir, describen los datos y la estructura de los mismos de la empresa para la que se diseña. **Podríamos decir que una Base de Datos es "EL PLANO DE LOS DATOS" de la empresa**.
>Por último, los datos de una *Base de datos* son independientes de los programas que acceden a ellos y de los equipos en el que se encuentran, además no tendrán redundancias innnecesarias.

---
## **LOS SISTEMAS GESTORES DE BBDD**
---
>[!IMPORTANT] DEFINICIÓN
>Conjunto de programas, procedimientos, lenguajes... que suministra, los medios necesarios para *describir, recuperar y manipular* los datos integrados en la BD, asegurando la *integridad, la confidencialidad y la seguridad de los mismos.*

#### Deben garantizar que se den las siguientes características de las BBDD:

- **Garantizar la Independencia lógica y física de los datos**
- **Garantizan la mínima Redundancia de los datos.**
- **Facilitar la administración mediante:**
	- Interfaz de *definición y manipulación* de los datos para programadores
	- *Herramientas visuales* para la generación de los objetos de la BD o bien lenguajes que permitan esta tarea.
	- Asistentes que facilitan las tareas de *instalación, configuración, creación de BD, etc*.
- **Garantizar la Integridad de los datos** ➔ Herramientas preventivas y de recuperación (curativas).
- **Facilitar el control de la seguridad de las bases de datos**➔ Gestionar el control de *accesos* y de la *concurrencia*.
- **Facilitar la atomicidad en las operaciones** ➔ Los *SGBD* deben suministrar las herramientas necesarias que permitan hacer operaciones consecutivas sobre los datos como si fuera una sola operación, de forma que un error durante el proceso no deje a los datos en un estado inestable.

>[!WARNING] DEFINICIÓN IMPORTANTE || *ATOMICIDAD*
>Varias operaciones como una sola.

### **FUNCIONES DE UN SGDB/DBMS**


| definición                                                                | manipulación                                                  | uso/control                                                     |
| ------------------------------------------------------------------------- | ------------------------------------------------------------- | --------------------------------------------------------------- |
| LDD                                                                       | LMD                                                           | LCD                                                             |
| Leng. de Definición de Datos                                              | Leng. de Manipulación de Datos                                | Leng. de Control de Datos                                       |
| - Elementos de la BD<br>- Estructura de la BD<br>- Restricciones de la BD | Permite:<br>- Añadir<br>- Suprimir<br>- Modificar<br>- Buscar | Interfaces para:<br>- Acceso de usuarios<br>- Tareas de control |
|                                                                           |                                                               |                                                                 |

### **COMPONENTES DE UN SGDB/DBMS**


| DICCIONARIO DE DATOS            | COMP. DE PROCESAMIENTO                      | MOTOR DE EJECUCIÓN                      | GESTIÓN DE ALMACEN.                                                                                                                       |
| ------------------------------- | ------------------------------------------- | --------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Datos sobre datos *(Metadatos)* | Permiten tratar sentencias *DDL, DML y DCL* | Permiten ejecutar sentencias procesadas | - Gestor autorizaciones<br>- Gestor de integridad<br>- Gestor de ficheros<br>- Interfaz de comunicaciones<br>- *Gestor de transacciones.* |

---
## **BBDD CENTRALIZADAS Y DISTRIBUIDAS**
---

### *DÓNDE ESTÁN LOCALIZADOS LOS DATOS*

Solo en un servidor -> BBDD Centralizadas
Pueden estar en varios servidores -> BBDD Distribuidas

>[!WARNING] IMPORTANTE
>Todas las BBDD *SIEMPRE* contienen garantías de seguridad, integridad, disponibilidad...

### *CÓMO ESTÁN DISTRIBUIDOS LOS DATOS*

**Repetidos** o **replicados** y/o **Distribuidos** entre los servidores.

#### TIPOS DE DISTRIBUCIÓN
- **Vertical** -> Columnas/tablas
- **Horizontal** -> Por registros
- **Mixta** -> Combinación de ambas

---
#### ESQUEMA DE TIPOS
[[ESQUEMA DE TIPOS DE BBDD.canvas]]

---

### *QUÉ DEBE GARANTIZAR UN SISTEMA DISTRIBUIDO*

>[!example] **ALTA DISPONIBILIDAD**
>Se debe garantizar que si un servidor se cae, los usuarios pueden seguir accediendo sin problema.
>> Es decir, debemos asegurar que los datos seguirán estando disponibles en otro servidor y los usuarios no deben notar dicha caída
>
>La **REPLICACIÓN** garantiza esta característica, ya que todos los datos se encuentras copiados en otro/s servidores. 


>[!tip] **BALANCEO DE CARGA**
> Se debe garantizar que no se produzcan **cuellos de botella**, es decir, que la política de distribución/replicación/mixta garantice que las peticiones de acceso a los diferentes servidores estén **balanceadas** y no hay un servidor sobrecargado mientras que otro se encuentre muy descargado.

>[!quest] **ESCALABILIDAD**
>Se debe garantizar que aumentar el número de servidores pueda crecer de manera fácil y rápida. 
>La *REPLICACIÓN* es la mejor opción que garantiza esta característica ya que solo hay que clonar los datos, no hay que reestructurar la distribución de los mismos. 
>
>Si combinamos una política de *distribución/replicación* garantizaría esta característica si replicamos los servidores por grupos.


## **NORMATIVA VIGENTE SOBRE PROTECCIÓN DE DATOS**
---
### *POR QUÉ ES NECESARIO*

Todos nuestros datos están al alcance de cualquiera en tiempo real y debemos tener derecho a la intimidad. 

> Es de vital importancia garantizar un uso y custodia responsable de los mismos por parte de las empresas para asegurar el derecho a la intimidad de las personas que pueden ser muy vulnerables si no se hace un buen uso de sus datos.

### *LEY DE PROTECCIÓN DE DATOS*

>[!WARNING] LEY ORGÁNICA
>Una ley orgánica significa que su objetivo es proteger un derecho *fundamental* de los ciudadanos. Los *derechos fundamentales* son los que se recogen en la **Constitución Española**.
>
>Todas las leyes que protegen los derechos establecidos en la *Constitución* son *Leyes Orgánicas* y deben ser aprobadas por mayoría absoluta.

#### *OBJETIVO*

---
>Garantizar el derecho que tenemos todas las personas a la protección de sus datos personales, el derecho a la intimidad. Y para ello se establecen las bases y principios sobre la protección de datos y los procedimientos a seguir para que se garantice este derecho.
---

### *NOMBRE*

---
 Ley Orgánica(1) 3/2018, de 5 de diciembre, de Protección de Datos Personales y garantía de los derechos digitales (LOPDGDD).
---






