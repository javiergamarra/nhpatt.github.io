---
id: 191
title: Retrospectiva All Together Now
date: 2011-04-12T00:15:19+00:00
author: nhpatt
layout: post
guid: http://nhpatt.com/retrospectiva-all-together-now/
permalink: /retrospectiva-all-together-now/
categories:
  - agile
  - all together now
---
Hace 8 días ya (que rápido pasa el tiempo!) comenzábamos el [All Together Now](http://alltogether.es/2011/04/05/teaser-de-la-vida-en-la-casa/).

La sensación final ha sido maravillosa, he aprendido mucho de otros proyectos, descubierto ideas extraordinarias y discutido con visitas sorpresa :). **Una experiencia que quiero repetir** muchas más veces.

El [proyecto](http://nhpatt.com/2011/03/31/alltogethernow/) que planteábamos [@edulan](https://twitter.com/edulan) y yo al final llegó a buen puerto, pese a encontrar bastantes obstáculos. He recopilado a grandes rasgos las tareas que hicimos cada día (las historias de usuario están en pivotal tracker) y os las comento brevemente. Breve recopilación: grabadora de clases para sordos, que convierte el audio grabado en texto.

[<img class="alignright size-medium wp-image-215" alt="HomeScreen" src="http://nhpatt.com/nhpatt/wp-content/uploads/2011/04/HomeScreen-200x300.png" width="200" height="300" srcset="http://nhpatt.com/nhpatt/wp-content/uploads/2011/04/HomeScreen-200x300.png 200w, http://nhpatt.com/nhpatt/wp-content/uploads/2011/04/HomeScreen.png 320w" sizes="(max-width: 200px) 100vw, 200px" />](http://nhpatt.com/nhpatt/wp-content/uploads/2011/04/HomeScreen.png)

Partimos los dos con **poca experiencia en Android**, por lo que una constante del fin de semana fue la autoformación. El libro [Hello Android](https://pragprog.com/book/eband/hello-android) y el API estaban siempre presentes. El primer día (viernes por la tarde) nos dedicamos a familiarizarnos con la estructura básica de Android, montamos el entorno (en [Github](https://github.com/edulan/Grabadora-para-sordos)), identificamos y priorizamos las historias de usuario, investigamos el API de testing y empezamos a hacer las primeras pruebas. El día terminó a las 2 de la mañana con una pequeña demo de grabación de sesiones de audio. Teníamos claro el look de la aplicación gracias a unos prototipos rápidos, [1](http://nhpatt.com/nhpatt/wp-content/uploads/2011/04/ClassesScreen.png) y [2](http://nhpatt.com/nhpatt/wp-content/uploads/2011/04/SubjectsScreen.png).

El sábado empezó a las 10 de la mañana, permitiendo la reproducción de audio, refactorizando el código de grabación del día anterior y afrontando el API de grabación de base de datos de Android, en SQLite. **Esta última tarea nos llevó mucho más tiempo** del que esperábamos. Nos encontramos con limitaciones por todas partes, empezamos un mini ORM que al final desechamos&#8230; el tiempo invertido en aprender el API nos retrasó sustancialmente en las fases posteriores. Terminamos el día a las 4 a.m. con el flujo de ventanas terminado, la creación de asignaturas, clases, sesiones de audio y los diálogos de grabación y reproducción. Investigamos brevemente el API de Speech To Text de Android para descubrir que parecía **no servir a nuestros propósitos**.

El domingo comenzamos a las 10, confirmando que el API no nos servía (al necesitar conectarse a los servidores, no permitir grabación y tener una duración límite). [@edulan](https://twitter.com/edulan) descubrió el día anterior que el [API de Google Chrome](http://www.engadget.com/2011/03/23/chrome-11-goes-beta-with-speech-to-text-capabilities/) podría valernos (tenía 4 días de vida) y encontró una gema que se comunicaba con los servidores de Google. **Así que pusimos la fábrica en marcha**, mientras @edulan montaba un servidor en local instalando la gema, yo cambié la aplicación para grabar wav con AudioRecorder en sustitución de 3GP (ya que la gema convertía de wav a flac, el único formato aceptado por el API de Speech to Text) y perdía un tiempo valioso en intentar hacer un post a los servidores directamente.

Y&#8230; **al final todo salió bien**, en el último momento la gema que daba problemas se instaló correctamente, conseguimos hacer un post multipart (con librerías de Apache) desde Android adjuntando el fichero .wav y recibir la conversión correctamente. En los últimos minutos ajustamos algunas cosillas de estilos e incluimos el menú de conversión y el formateo del JSON recibido.[<img class="alignright size-medium wp-image-216" title="RecordingsScreen" alt="" src="http://nhpatt.com/nhpatt/wp-content/uploads/2011/04/RecordingsScreen-200x300.png" width="200" height="300" srcset="http://nhpatt.com/nhpatt/wp-content/uploads/2011/04/RecordingsScreen-200x300.png 200w, http://nhpatt.com/nhpatt/wp-content/uploads/2011/04/RecordingsScreen.png 320w" sizes="(max-width: 200px) 100vw, 200px" />](http://nhpatt.com/nhpatt/wp-content/uploads/2011/04/RecordingsScreen.png)

Al final el proceso quedó de la siguiente forma:



  1. El usuario graba una sesión (dentro de una asignatura y una clase) en wma.
  2. Cuando decide, selecciona la opción de conversión.
  3. Y el sistema hace un post, adjuntando el fichero, al servidor de [@edulan](https://twitter.com/edulan) que se la remite a los servidores de Google Chrome&#8230;
  4. Que devuelven la respuesta con un % de confianza al servidor, que se la devuelve a la aplicación&#8230;
  5. Y el sistema la muestra por pantalla.

La aplicación funcionando (sorprendentemente, bastante bien y en perfecto castellano) os la enseñaré en un próximo post.

Decir ahora que tenemos pensadas **muchas** mejoras, que afrontaremos estos días y **un gracias gigante** a [@edulan](https://twitter.com/edulan) por todo lo que me ha enseñado, por la experiencia vivida y porque sin él todo esto no habría sido posible :)
