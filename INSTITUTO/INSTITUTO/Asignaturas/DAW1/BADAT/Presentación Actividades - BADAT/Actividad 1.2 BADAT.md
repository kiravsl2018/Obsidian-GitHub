---
title: Desarrollo de Aplicaciones Web
subtitle: "Tema 1:  El almacenamiento de la información"
author: Miguel López
date: 2026-09-25
subject: Grado Superior DAW
tags:
  - actividad
Asignatura: Base de Datos
Tema:
  - Introducción
---

<br><br><br>

# **Tipos de BBDD**

## Unidad 1. El almacenamiento de la información

<br><br><br><br><br><br><br><br><br><br>

**Autor:** Miguel López Contreras 
**Módulo:** Desarrollo de Aplicaciones Web (DAW)  
**Fecha:** 24 de septiembre de 2026  

\
*IES / Mar de Alborán*

<div style="page-break-after: always;"></div>


```table-of-contents
```


<div style="page-break-after: always;"></div>




# Situación A

Una pequeña empresa de gestión de alquileres de turismo rural que contaba con un servidor de datos, ha desarrollado una app, por lo que ha crecido exponencialmente y en este momento se encuentra con que el sistema se está colapsando, por ello ha decidido incorporar otros servidor de datos pasando así del modelo **centralizado** al modelo **distribuido**.

En este momento, contando con dos servidores, indica cual crees que sería la mejor opción para garantizar las 3 características que debe cumplir un sistema de este tipo explicando como se cumple cada una de dichas características:

> En esta situación elegiría hacer servidores mediante **Distribución** puesto que puedo separar por secciones los diferentes alquileres. El diseño sería el siguiente:
> 
> En el primer servidor tendría las secciones del recorrido del turismo rural con sus respectivos alquileres y en el segundo servidor tendría los datos de los usuarios que acceden al servidor y el alquiler que han elegido.

> Cumple la *alta disponibilidad* y el *balanceo de carga* puesto que el usuario no va a tener que esperar tanto a la respuesta del servidor ya que toda la información está repartida y se evita el cuello de botella. En referencia a la *escalabilidad*, nos damos cuenta que, teniendo dos servidores, podríamos en un futuro añadir más secciones de turismo y más usuarios.


# Situación B

Un año más tarde de la situación A, la empresa ha crecido tanto que la solución anterior no resulta suficiente, por lo que se necesita diseñar una estrategia que permita mantenerse y no morir de **exito** e, incluso, seguir creciendo. Las necesidades actuales son las siguientes:

1. Existen casas en 10 zonas claramente diferenciadas y los usuarios suelen acceder a una de ellas desde el inicio de las búsquedas.
    
2. De las 10 zonas exiten dos zonas en las que la proporción de búsquedas es bastante más baja que la media (aproximadamente un poco menos de la mitad).
    
3. De las 8 zonas restantes, existen otras dos zonas que tienen un porcentaje de búsquedas del doble que la media.
    
4. Es necesario garantizar las 3 características fundamentales de un buen sistema de BBDD de este tipo.
    
5. Por último se sabe que dentro de  una zona, las búsquedas se diferencian claramente por los dos tipos de casa en alquiler (dentro de la población, fuera de casco urbano).
    
6. No hay límite, pero hay que elegir la opción más económica que garantice todos los puntos anteriores.
    

