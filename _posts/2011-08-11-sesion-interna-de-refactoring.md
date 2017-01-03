---
id: 431
title: Sesión interna de refactoring
date: 2011-08-11T12:00:21+00:00
author: nhpatt
layout: post
guid: http://nhpatt.com/sesion-interna-de-refactoring/
permalink: /sesion-interna-de-refactoring/
categories:
  - dev
---
El pasado miércoles impartí una sesión sobre calidad en [Luce I.T.](http://luceit.com), concretamente sobre Refactoring. Las slides están [aquí](http://nhpatt.com/slides/a%20REFACTORING%20day/) (lamentablemente dependen mucho de la explicación).

Intenté explicar los conceptos fundamentales basándome en el ejemplo de [Refactoring](http://books.google.fr/books/about/Refactoring.html?id=1MsETFPD3I0C&redir_esc=y) de Martin Fowler. Para los que no hayáis leído el libro, en el primer capítulo se describe un pequeño proyecto de alquiler de películas. El código del mismo está [aquí](https://github.com/nhpatt/refactoring/commit/9615a58844695de93426f3682b4e714d8d58fd23).

La mayor parte de la sesión fue la ejecución en público de las refactorizaciones del ejemplo, que originaron interesantes discusiones con todos los presentes (unas 15 personas) sobre los pasos más controvertidos. Los pasos más &#8216;_polémicos_&#8216; fueron los siguientes:



  * Sustitución de los comentarios por código descriptivo que les hacía redundantes (ya tuvimos una sesión al hilo de [Clean Code](http://books.google.fr/books/about/Clean_code.html?id=dwSfGQAACAAJ&redir_esc=y) sobre este asunto por lo que este tema concreto no originó preguntas).
  * **Usar más de un return statement**&#8230; en el ejemplo Martin Fowler contradice las &#8216;buenas prácticas&#8217; que se suelen enseñar en la carrera de Informática para poder eliminar flags de control o simplemente hacer el código más claro. En este caso concreto si que hubo una discusión interesante, sobre todo teniendo en cuenta que la siguiente refactorización que sugiere es&#8230;
  * Usar un operador ternario, en un caso concreto en el que el código queda poco legible (sin haber extraído constantes tampoco). Esta refactorización no despertó la simpatía de los presentes y creo que es bastante discutible. A mi los operadores ternarios no me molestan para situaciones muy puntuales, pero entiendo que son poco claros.
  * **Hacer un inline de un temporal **sustituyendo varias llamadas al temporal por la ejecución de un método (replace temp with query). Este refactoring despertó críticas por la supuesta pérdida de eficiencia, pero enseguida se llegó a un consenso, ya que en el ejemplo la sustitución era inofensiva en términos de rendimiento (y aprovechamos para explicar el concepto de optimizacion temprana). Ejemplo:

    ```java
    - double thisAmount = rental.getCharge();
    - String.valueOf(thisAmount) + "\n";
    - totalAmount += thisAmount;
    + String.valueOf(rental.getCharge()) + "\n";
    + totalAmount += rental.getCharge();
    ```

  * **Reemplazar switch con polimorfismo** y la máxima de que si tienes que tener un switch, que sea en el código de la clase propietaria para que sólo esté en una única clase. Esta refactorización despertó muchas simpatías, aunque sea compleja de seguir. Aprovechamos para explicar las maldades de los switch, el [código polimórfico](https://github.com/nhpatt/refactoring/commit/4ae830c66b24098dfc45542f674220e2ce17197b) era sustancialmente más simple.
  * Explicamos los problemas en Java con los temporales al extraer métodos (con 0 o 1 la refactorización es trivial) y la raíz del problema, que **Java utiliza paso por valor de la referencia**, por lo que las modificaciones de más de un temporal (si es sólo uno puedes devolverlo en el return) dentro de un método hacen que extraer métodos de ese código sea sustancialmente más complejo.
  * Otro refactoring polémico fue este:

    ```java
    for (final Rental rental : rentals) {
    -        frequentRenterPoints += rental.getRenterPoints();
    (...)
    }
    + public Double getTotalAmount() {
    +    Double totalAmount = 0D;
    +    for (final Rental rental : rentals) {
    +      totalAmount += rental.getCharge();
    +    }
    +    return totalAmount;
    +  }
    ```
    
    Sustituyendo un cálculo que se realizaba dentro de un bucle, junto con otras cosas, a un método aparte y dejando el bucle (más código y dos bucles). La principal pega era rendimiento, ya que la refactorización separaba cálculos y dejaba el código más claro, pero teniendo en cuenta de nuevo la [optimización temprana](http://en.wikipedia.org/wiki/Program_optimization#When_to_optimize) no es un problema.
    
    Por último, resumí brevemente las [slides](http://nhpatt.com/slides/a%20REFACTORING%20day/) y tuvimos una ronda de dudas y preguntas. Se quedaron en el tintero ejercicios prácticos por parejas, estilo los videos de [Jason Gorman](https://www.youtube.com/user/parlezuml).

    Realizaremos más sesiones sobre refactoring en un futuro. Si estás por Valladolid y te apetece pasarte a una sesión (miércoles cada 2 semanas), dame un toque. Estáis todos invitados
    
    :)

    PD: [@jmbeas](https://twitter.com/jmbeas) tiene una serie de posts más extensos sobre los refactors empleados en el libro, recomiendo echarles un ojo: <http://blog.jmbeas.es/tag/refactor/>

