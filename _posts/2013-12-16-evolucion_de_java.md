---
id: 834
title: Evolución de Java (desde JDK5 a 8)
date: 2013-12-16T12:00:20+00:00
author: nhpatt
layout: post
guid: http://nhpatt.com/?p=834
permalink: /evolucion_de_java/
categories:
  - dev
  - java
---
El pasado miércoles di, junto con [Pilar Fraile](https://twitter.com/pilyemaya), una charla sobre la evolución de Java, desde la JDK5 hasta la 8. La charla estaba inspirada por [esta charla](http://www.slideshare.net/mariofusco/fp-in-java-project-lambda-and-beyond) de Mario Fusco sobre Java 8 Lambdas en la Codemotion 2013.

La idea sobre todo era centrarse en cambios de sintaxis con dos propósitos, **explicar y convencer de las mejoras** hasta Java 7 a los desarrolladores que todavía no están usando el [diamond operator](http://www.javaworld.com/article/2074080/core-java/jdk-7--the-diamond-operator.html), [auto-cierre de recursos en el try](http://www.oracle.com/technetwork/articles/java/trywithresources-401775.html), enumeraciones&#8230; y, por otra parte, **introducir los grandes cambios en Java 8**. Sobre los cambios en Java 8 nos centramos principalmente en métodos por defecto y estáticos en interfaces, **la nueva API de fechas y lambdas**.

Planteamos la charla mostrando código en Java 5/6/7 y el equivalente en versiones más modernas, mostrando, por ejemplo, cómo calcular el siguiente miércoles de la semana en Java 7 con el API de Calendar o con Java 8.

Todo el código usado (a base de tests) **[está disponible](https://github.com/nhpatt/evolution_of_java) junto [con las slides](http://www.slideshare.net/nhpatt/evolution-of-java-29207560)**, echadles un vistazo y enviad preguntas/sugerencias/correcciones :)

También grabamos la sesión con **[un hangout](https://www.youtube.com/watch?v=By_3U1buyxY&feature=youtu.be)**. Debido a mi incapacidad técnica no he grabado toda la parte de Pili, JDK5 a JDK7 ( sorry :( ), sobre todo está grabado cuando hablamos de Java 8.

Al público le encantó el nuevo API de fechas (basado en Joda time) pero las expresiones lambdas no fueron tan bien recibidas (sobre todo por cuestiones de legibilidad). Probablemente no me centré lo suficiente en las ventajas de reutilización, composición, lazyness. También está la resistencia al cambio, sobre todo cuando parece complicado.

Por mi parte, todos estos cambios son más que bienvenidos (no habrían estado mal 4-5 años antes). De momento me tocará conformarme con que ya podemos usar casi [todos los cambios de Java 7 en Android](http://tools.android.com/tech-docs/new-build-system/user-guide#TOC-Using-sourceCompatibility-1.7).

Incluyo las slides:

<iframe style="border: 1px solid #CCC; border-width: 1px 1px 0; margin-bottom: 5px;" src="http://www.slideshare.net/slideshow/embed_code/29207560" width="425" height="355" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" allowfullscreen="allowfullscreen"></iframe>

**Cualquier feedback es bienvenido** 😀

