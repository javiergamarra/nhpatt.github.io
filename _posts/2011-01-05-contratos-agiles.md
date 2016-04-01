---
id: 48
title: Contratos ágiles
date: 2011-01-05T21:15:17+00:00
author: nhpatt
layout: post
guid: http://nhpatt.wordpress.com/?p=48
permalink: /contratos-agiles/
jabber_published:
  - 1294258519
categories:
  - agile
  - scrum
---
Hace unas semanas tuvimos la suerte de recibir unas charlas sobre Scrum de manos de [@tolivern](https://twitter.com/tolivern) (muchas gracias!). Uno de los temas era la forma de &#8220;vender&#8221; Scrum al cliente y el modelo de **contrato más apropiado** para esa relación. Teresa nos comentó que a grandes rasgos existían dos modelos de contratos básicos, a precio fijo y contrato de servicios. Los detalles son los siguientes:

  * **Precio fijo**: en el contrato se establece previamente un **precio fijo a una funcionalidad definida**. Partimos de la premisa de que es imposible saber de antemano todas las características del sistema, por lo que el precio fijado nunca va a ser exacto. Todo el riesgo lo asume la empresa que desarrolla el software, ya que el **cliente no tiene ningún incentivo** para aceptar la entrega, siempre se podrá quejar de que el sistema no cubre toda la funcionalidad definida en el contrato (aunque sea inútil). La empresa desarrolladora suele aligerar las tareas del contrato (ya sea en calidad o en funcionalidad) e incluir algunas adicionales para cubrirse de posibles quejas.

  * **Servicios**: en este tipo de contratos, el cliente contrata los servicios de una empresa indefinidamente, hasta que acaben de desarrollar la funcionalidad deseada. Todo el **riesgo cae para el cliente**, que tiene que confiar al 100% en la empresa contratada. La empresa contratada puede abusar de la confianza del cliente y extender el desarrollo.

Frente a esos dos tipos de contratos (con sus variaciones), una de las opciones es que el cliente tenga tanta confianza con nosotros para que nos contrate Sprints de x puntos de historia. Pero propuestas no faltan, [Kent Beck](http://en.wikipedia.org/wiki/Kent_Beck) recomienda jugar con un [contrato sin scope definido](http://www.syntropy.co.uk/papers/optionalscope.pdf), en el que el precio y tiempo sean fijos y juguemos con la funcionalidad a desarrollar.

Por otra parte, [@tolivern](https://twitter.com/tolivern) nos comentó un contrato con bonuses (frente a bonus/penalty) para la empresa desarrolladora con la idea final de **motivar a las dos partes a aceptar el contrato antes**. En concreto la idea era establecer un precio medio con un buffer. Si el proyecto terminaba antes, el ahorro se reparte entre las dos partes y viceversa. El cliente tiene como incentivo acabar antes porque puede ahorrarse parte del coste y el proveedor obtiene más beneficios. En el caso de alargarse el desarrollo, el proveedor cubre parte de las pérdidas y el cliente no tiene que pagar todo el tiempo de desarrollo extra.

También nos introdujo una de las propuestas más populares, _Money for nothing, changes for free._ La idea subyacente es un contrato por sprints, mezcla de contrato de servicios con un coste objetivo. Uno de los propósitos del contrato es **no desarrollar toda la funcionalidad expuesta** (algo que nunca se hace en contratos &#8220;tradicionales&#8221; o se justifica), ya que la funcionalidad final probablemente tenga un muy bajo [ROI](http://es.wikipedia.org/wiki/Retorno_de_la_inversi%C3%B3n), es decir, costará mucho desarrollarla para el beneficio marginal obtenido por el cliente.

El nombre del contrato se deriva del hecho de que el cliente puede cancelar el contrato cuando considere que se **cubre la funcionalidad que más desea** (pagando una tasa de cancelación), por lo que recibe dinero &#8220;gratis&#8221; (aquel presupuestado en funcionalidades ahora poco importantes). De igual forma puede cambiar historias de usuario por otras de tamaño similar, obteniendo cambios &#8220;gratis&#8221;. Las dos partes tienen **incentivos por terminar cuanto antes**, el cliente porque reduce costes y el proveedor aumenta beneficios, si bien no tan marcados como en el caso anterior, con bonuses y pérdidas compartidas.

Otro tipo de contratos planteados fueron por los contratos por etapas o un contrato por cada sprints (como el [PS2000 noruego](http://www.dataforeningen.no/it-contract-standards.146223.no.html)). Me parece especialmente interesante el contrato por etapas, establecer un contrato inicial que cubra 3 iteraciones (por coste o por servicio) y después de analizar los resultados plantear otro contrato para el resto del desarrollo.

La idea de este tipo de contratos es establecer un marco colaborativo en la que las dos partes ganan (situación win-win) si el proyecto se desarrolla sin problemas.

Lo que parece claro es que **alternativas no faltan**! Y pone en tela de juicio las dudas de que el modelo Scrum no cuadra con la parte comercial de un proyecto.

En [10 agile contracts](https://www.scrumalliance.org/resource_download/1119) podéis ver más alternativas de contratos comparando estructura, alcance y riesgo y si queréis más información de contratos por etapas podéis consultar esta [presentación](http://coactivate.org/projects/agile-contracts/presentations/Agile-Contracts-at-Scrum-Gathering.pdf). Un ejemplo de textos en el contrato podéis encontrarlos en: <http://www.proyectosagiles.org/contrato-agil-scrum>. La mayor parte de ideas de este post provienen de la charla de [@tolivern](https://twitter.com/tolivern) y la excelente presentación de [Ángel Medinilla](http://www.presionblogosferica.com/): [contratos ágiles](http://www.slideshare.net/proyectalis/090603-contratos-giles).

