---
tags:
  - temario
Asignatura: Programación
Prioridad: Media 🟡
Tema:
  - Introducción
To-Do: Pendiente
Nota: Guía para iniciación en Java - Presentación
---
# Guía de Java para Principiantes

> **Nota para Obsidian:** Este documento está formateado en Markdown para que puedas importarlo directamente a tu bóveda. Utiliza etiquetas de código, llamadas y notas estructuradas para facilitar tu estudio.

---

## 1. ¿Qué es Java y por qué aprenderlo?

Java es un lenguaje de programación de propósito general, orientado a objetos y de alto nivel. Una de sus características principales es su filosofía **"Write Once, Run Anywhere"** (Escribe una vez, ejecuta en cualquier parte), lo que significa que el código compilado puede ejecutarse en cualquier dispositivo que tenga instalado la **JVM** (Java Virtual Machine).

### Conceptos Fundamentales del Ecosistema:
* **JDK (Java Development Kit):** El kit de herramientas para desarrolladores. Incluye el compilador y todo lo necesario para *crear* programas en Java.
* **JRE (Java Runtime Environment):** El entorno de ejecución. Permite *ejecutar* aplicaciones Java, pero no desarrollarlas.
* **JVM (Java Virtual Machine):** La máquina virtual que interpreta el código intermedio de Java ($bytecode$) y lo adapta al sistema operativo específico.

---

## 2. Instalación y Primeros Pasos

1. **Instalar el JDK:** Descarga e instala la versión más reciente del JDK (como OpenJDK o Oracle JDK) desde su sitio oficial.
2. **Configurar el entorno:** Asegúrate de agregar la ruta del JDK a las variables de entorno de tu sistema operativo (`PATH`).
3. **Elegir un IDE:** Para empezar de manera cómoda, puedes utilizar entornos de desarrollo como **IntelliJ IDEA**, **Eclipse** o **Visual Studio Code**.

---

## 3. Tu Primer Programa: Hola Mundo

En Java, todo código ejecutable debe estar dentro de una **clase**. Por convención, el nombre del archivo debe coincidir exactamente con el nombre de la clase pública.

```java
public class HolaMundo {
    public static void main(String[] args) {
        // Imprime un mensaje en la consola
        System.out.println("¡Hola, mundo desde Java!");
    }
}
```

### Desglose del Código:
* `public class HolaMundo`: Define una clase pública llamada `HolaMundo`.
* `public static void main(String[] args)`: Es el **método principal** (punto de entrada). Sin él, Java no sabe por dónde empezar a ejecutar el programa.
* `System.out.println(...)`: Instrucción para mostrar texto por pantalla seguido de un salto de línea.

---

## 4. Variables y Tipos de Datos Básicos

Java es un lenguaje de **tipado estático**, lo que significa que debes declarar el tipo de cada variable antes de usarla.

### Tipos Primitivos Principales:
* `int`: Números enteros (ej. `int edad = 25;`)
* `double`: Números con decimales (ej. `double precio = 19.99;`)
* `boolean`: Valores lógicos (`true` o `false`) (ej. `boolean activo = true;`)
* `char`: Un solo carácter (ej. `char letra = 'A';`)
* `byte`:
* `short`:
* `long`:

### Cadenas de Texto (No primitivo):
* `String`: Para almacenar textos más largos (ej. `String nombre = "Ana";`)

---

## 5. Estructuras de Control de Flujo

Permiten tomar decisiones y repetir bloques de código.

### Condicionales (`if`, `else`, `switch`):
```java
int edad = 18;

if (edad >= 18) {
    System.out.println("Eres mayor de edad.");
} else {
    System.out.println("Eres menor de edad.");
}
```

### Bucles (`for`, `while`):
El bucle `for` se utiliza cuando sabes cuántas veces quieres repetir una acción:
```java
for (int i = 1; i <= 5; i++) {
    System.out.println("Número: " + i);
}
```

---

## 6. Introducción a la Programación Orientada a Objetos (POO)

Java gira en torno a la POO. Los dos conceptos más importantes al empezar son las **Clases** (molde) y los **Objetos** (instancia creada a partir del molde).

```java
// Definición de la clase
class Coche {
    // Atributos (propiedades)
    String marca;
    int velocidad;

    // Método (comportamiento)
    void acelerar() {
        velocidad += 10;
        System.out.println("El coche aceleró. Velocidad actual: " + velocidad + " km/h");
    }
}

// Uso en el método main
public class Main {
    public static void main(String[] args) {
        // Creación del objeto
        Coche miCoche = new Coche();
        miCoche.marca = "Toyota";
        miCoche.velocidad = 50;
        
        miCoche.acelerar(); // Llama al método
    }
}
```

---
