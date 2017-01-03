---
id: 429
title: 'Review de Refactoring: improving the design of existing code'
date: 2011-08-08T11:00:35+00:00
author: nhpatt
layout: post
guid: http://nhpatt.com/review-de-refactoring-improving-the-design-of-existing-code/
permalink: /review-de-refactoring-improving-the-design-of-existing-code/
categories:
  - dev
  - review
tags:
  - Review
---
La semana pasada, para preparar decentemente la charla que impartí en [Luce I.T.](http://luceit.com), leí _[Refactoring: improving the design of existing code](http://books.google.fr/books/about/Refactoring.html?id=1MsETFPD3I0C&redir_esc=y)_ de [Martin Fowler](https://www.google.fr/search?hl=es&tbo=p&tbm=bks&q=inauthor:%22Martin+Fowler%22&gws_rd=cr&ei=_yp_VKHtOMWracL9gqgJ) y [Kent Beck](https://www.google.fr/search?hl=es&tbo=p&tbm=bks&q=inauthor:%22Kent+Beck%22&gws_rd=cr&ei=tkB_VJLMNYKBabKpgdgJ). _Refactoring_ es un libro que tenía pendiente desde hace tiempo y no me ha defraudado.

### Estructura

El libro comienza explicando el concepto básico de [Refactoring](http://en.wikipedia.org/wiki/Code_refactoring) mediante un [ejemplo práctico](https://github.com/nhpatt/refactoring). De esta forma introduce rápidamente las ventajas de aplicar refactorización. Posteriormente, en capítulos posteriores, introduce las definiciones, ventajas e incovenientes y consejos de cuando aplicar refactoring.

El gran núcleo del libro se dedica a los [code smells](http://en.wikipedia.org/wiki/Code_smell) y a la lista de posibles [refactorings](http://www.refactoring.com/catalog/index.html) con guías de aplicación paso a paso. El libro se completa con tres capítulos escritos por invitados, uno sobre general sobre refactoring, otro de la herramienta específica de Smalltalk y un capítulo final escrito por [Kent Beck](http://en.wikipedia.org/wiki/Kent_Beck).

Un pequeño resumen destilado está en estas [slides](http://nhpatt.com/slides/a%20REFACTORING%20day/) (pulsa &#8216;c&#8217; para ver los comentarios).



### Citas destacadas y comentarios

Comento algunas citas que han gustado o provocado especialmente (el resto las he dejado en quotista.com):

> &#8220;Any fool can write code that a computer can understand. Good programmers write code that humans can understand&#8221;

Sobre la importancia de refactoring y del naming concretamente. Esta cita ya la había visto con otras formas.

> &#8220;With refactoring you find the balance of work changes. You find that design, rather than occuring all up front, occurs continuously during development&#8221;

Sobre refactoring y diseño. Ante el [BDUF](http://en.wikipedia.org/wiki/Big_Design_Up_Front), Martin Fowler defiende una mejora del diseño continua, la refactorización soluciona el deterioro del diseño a lo largo del tiempo de vida del proyecto.

> &#8220;Here&#8217;s a guideline Don Roberts gave me: The first time you do something, you just do it. The second time you do something similar, you wince at the duplication, but you do the duplicate thing anyway. The third time you do something similar, you refactor.&#8221;

La polémica regla de la tercera vez&#8230; discuss!

> &#8220;The other time you should avoid refactoring is when you are close to a deadline. At that point the productivity gain from refactoring would appear after the deadline and thus be too late.&#8221;

El problema de este tipo de sentencias es que sirven para justificar nuestros pecados.

> &#8220;It is better to write and run incomplete tests than not to run complete tests. You should concentrate on where the risk is. Look at the code and see where it becomes complex.&#8221;

Mejor algo que nada&#8230;

### Conclusiones

Me ha gustado especialmente el capítulo de Kent Beck, sobre la importancia de establecer objetivos claros y saber parar. Martin Fowler menciona el problema de &#8216;cavar demasiado&#8217; y refactorizar sin un rumbo claro y recomienda **la suma de pequeñas refactorizaciones** para lograr el mismo objetivo.

A lo largo del libro se menciona la importancia de saber con certeza **la actividad que estás realizando en todo momento**, con una metáfora de sombreros (llevar puesto el sombrero de refactoring o de desarrollador) y no mezclar en el mismo instante las dos activades.

Me gusta especialmente [la lista exhaustiva de refactorings](http://nhpatt.com/slides/a%20REFACTORING%20day/#slide9), [de code smells](http://nhpatt.com/slides/a%20REFACTORING%20day/#slide8) y las razones por las que [refactorizar](http://nhpatt.com/slides/a%20REFACTORING%20day/#slide4), [cuando](http://nhpatt.com/slides/a%20REFACTORING%20day/#slide5), [los problemas](http://nhpatt.com/slides/a%20REFACTORING%20day/#slide7) y qué contar al jefe (si no le importa la calidad, no se lo cuentes y hazlo!).

Por poner pegas al libro, las guías de refactorización pierden un poco el sentido ante el avance de los entornos con refactorizaciones automatizadas (aunque no para todos los lenguajes) y echo de menos alguna refactorización más larga (estilo Clean Code).

Son pequeños comentarios a un libro editado en 1999 que sigue totalmente vigente. **Lectura recomendada**.

