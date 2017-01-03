---
id: 938
title: Arreglando chapuzas en Android (un caso práctico)
date: 2014-03-13T12:00:09+00:00
author: nhpatt
layout: post
guid: http://nhpatt.com/arreglando-chapuzas-en-android/
permalink: /arreglando-chapuzas-en-android/
categories:
  - dev
  - java
---
Desviándome un poco de mi trabajo de estos últimos meses, me han pedido ayuda técnica en una aplicación Android.

Os pongo en situación: la aplicación llama a un WS pidiendo 300 objetos a actualizar, parsea el resultado, lo transforma a objetos, inserta/actualiza y vuelve a ver si hay más resultados (y repite el proceso si es así). Hay muchos resultados (+4000) por lo que tarda **105 segundos!** En un Nexus 5. Y hay más objetos a actualizar!

Es una barbaridad de tiempo pero tienen la suerte de que los usuarios **necesitan** la aplicación por lo que pacientemente esperan hasta que termina la actualización (que se repite cada 2-3 meses). También les sirve de consuelo la cantidad de aplicaciones que hacen esperar esos tiempos para actualizaciones de datos u otras cosas que podrían ser hechas en el backend (Skype, te miro a ti).

Veamos a ver lo que puedo hacer sin cambiar drásticamente el enfoque (rock-the-boat no permitidos):

  * Antes de empezar limpio código que no se usa, incluyendo pasar el contexto al servicio web** **para no usarlo nunca. Resultado **103 **segundos (bien puede ser cero la mejora, por desviación).

  * Veo que para insertar/actualizar primero hacen una consulta para ver si está en BD el dato y actuar en consecuencia. OrmLite incluye una forma de hacerlo automáticamente: **[insertWithOnConflict](http://developer.android.com/reference/android/database/sqlite/SQLiteDatabase.html#insertWithOnConflict(java.lang.String, java.lang.String, android.content.ContentValues, int)) **(con flag [replace](http://developer.android.com/reference/android/database/sqlite/SQLiteDatabase.html#CONFLICT_REPLACE)) mucho más eficiente en inserciones y algo en actualizaciones. Esto me permite quitar una select, un insert/update y no abrir la base de datos en modo lectura -> **93 **segundos.

  * Por defecto OrmLite abre una transacción por cada operación. Obviamente ( :( ) no han utilizado una para cada conjunto de datos (o global). Si abro **una única transacción**  -> **52 **segundos.

  * Tal como está el código, se parsea a lista de JSONObject y se transforma el resultado en objetos propios (además se aplican regex para quitar caracteres). Si **trabajamos directamente con la lista de JSONObject** -> **42 **segundos.

  * Al analizar dónde se va el tiempo, veo que hay muchas llamadas al garbage collector (porque hay muchos objetos creados), al analizar la clase que parsea veo que **está mal el parseo de los objetos** (se vuelven a parsear JSONObjects innecesariamente), cambio el código para trabajar con JSONArray directamente -> **22** segundos.

  * No entiendo bien porque se hace la operación en bucle (imagino que cómo gestión simple de memoria), cambio el código para que sólo se haga una vez -> **15** segundos.

  * Quito código que no me gusta, elimino creación de objetos varios en bucles -> **13** segundos.

Los 13 segundos actuales se desglosan en las siguientes operaciones:

  * 4 segundos recuperando del WS y parseando.
  * 6 segundos guardando (4000 objetos!).
  * 3 segundos actualizando la fecha de consulta del WS!!! -> Esta operación es **increíblemente ineficiente** (veo rápidamente que parece que es actualizar una fila y consultar) pero cómo es poco tiempo, lo ignoro de momento.

**Pero**, en el camino de la eficiencia me he cargado la aplicación de una regex para quitar caracteres erróneos, tengo que volver a incluirlo:

  * Hago unas mejoras previas, creando menos objetos -> **12** segundos.

  * Añado la regex tal como estaba, aplicada por cada objeto -> **30** segundos :(

  * La regex puede mejorarse **compilando el patrón** antes de aplicarla -> **22** segundos (son demasiados).

  * Soy idiota, debería aplicar las regex a toda la response (en vez de trozo a trozo) -> **13** segundos. Lo mejor es que no se si las regex son necesarias para estos datos, porque se buscan caracteres alfanuméricos y los resultados (que tengo) son sólo números!!!! pero aún así la dejo&#8230;

  * Por último, **lanzo la aplicación en modo ejecución (no debug)**, resultado -> **5 segundos**. El desglose es el siguiente:

  * 2 segundos recuperando del WS y parseando.
  * 1 segundo guardando.
  * 2 segundos actualizando la fecha!!! (sigue siendo demasiado, este código está mal).

**Resultado final: 5 segundos&#8230;** partiendo de 105.

Mi enfoque siempre ha sido ver lo que tarda más (con DDMS, trace y código) y atacar, teniendo en cuenta los mensajes del GC en el log. El resultado final también han sido 60 líneas de código menos (en 132 se ha quedado).

Hay más mejoras posibles (en [SO](http://stackoverflow.com/questions/1711631/improve-insert-per-second-performance-of-sqlite) hay un listado curioso) pero de momento así se queda, esperando feedback del resto del equipo.

Nada más, estoy abierto a cualquier sugerencia! (seguro que se me ha pasado algo) 😀

