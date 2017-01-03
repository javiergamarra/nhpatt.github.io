---
id: 684
title: hackforgood
date: 2013-03-10T13:00:40+00:00
author: nhpatt
layout: post
guid: http://nhpatt.com/hackforgood/
permalink: /hackforgood/
categories:
  - agile
  - dev
---
El pasado fin de semana estuve de [hackathon](http://en.wikipedia.org/wiki/Hackathon) social, en una iniciativa nacional llamada [HackForGood](http://hackforgood.net/que-es-hackforgood/) y, en concreto, en la sede de [Valladolid -León](http://hackforgood.net/category/valladolid/).

Nos juntamos un grupo con los habituales de [cylicon valley](http://www.cyliconvalley.es/) y [agilecyl](http://agilecyl.org/) y presentamos una iniciativa conjunta, una parte web desarrollada por [Amalia](https://twitter.com/amaliahern), [Semurat](https://twitter.com/semurat), [Álvaro](https://twitter.com/aloaisa), [Jorge Maroto](https://twitter.com/patoroco) y [Mario de Frutos](https://twitter.com/ethervoid) con la colaboración en el diseño de [Mario del Valle](https://twitter.com/maduil) y una parte móvil en Android desarrollada por [Soraya](https://twitter.com/sorayavay), [José Da Rocha](https://twitter.com/josedarocha), [Andrés Sedano](https://plus.google.com/102930499045104366868/about), [Mario del Valle](https://twitter.com/maduil) y un [servidor](https://twitter.com/nhpatt).

El proyecto estaba basado en uno de los retos propuesto por la organización y consistía en crear una plataforma móvil para poner en contacto ONGs y donantes, de tal forma que la participación de los donantes en los proyectos de colaboración no se limitase a poner dinero, si no que pudieran participar con sugerencias y recibir notificaciones y actualizaciones del progreso del proyecto.

La parte web se encargó de encontrar y procesar los datos de las ONGs de todo el mundo y los países en los que operan y mostrarlos en un mapa, superponiendo un índice de pobreza (personas que viven con menos de 3 dólares al día), con el propósito de incentivar a la gente a elegir proyectos de cooperación en zonas más necesitadas.

Esta parte está accesible en http://yourcommitment.org/ y usa [CartoDB](http://cartodb.com/) para mostrar de forma espectacular mapas y [parse](https://parse.com/ "parse") de backend. **Echadle un ojo!**

La parte móvil muestra los proyectos de cooperación, permite fijarte una cantidad de dinero y repartirla entre los proyectos más interesantes. Los proyectos también pueden enviar actualizaciones del estado del proyecto y los donantes pueden recibir notificaciones push con información adicional.

La parte móvil está descrita en este video:

<object width="480" height="360" classid="clsid:d27cdb6e-ae6d-11cf-96b8-444553540000" codebase="http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=6,0,40,0"><param name="allowFullScreen" value="true" /><param name="allowscriptaccess" value="always" /><param name="src" value="http://www.youtube.com/v/NpZDXq_beVI?hl=en_US&amp;version=3" /><param name="allowfullscreen" value="true" /><embed width="480" height="360" type="application/x-shockwave-flash" src="http://www.youtube.com/v/NpZDXq_beVI?hl=en_US&amp;version=3" allowFullScreen="true" allowscriptaccess="always" allowfullscreen="true" /></object>

Está disponible en [github](https://github.com/nhpatt/yourcommitment) y usa [roboguice](https://github.com/roboguice/roboguice) y [parse](https://parse.com/) para el backend (recuperar información de proyectos, ONGs, guardar usuarios, donaciones&#8230;), login de facebook (necesita el facebook SDK) y notificaciones Push.

La experiencia en sí fue **magnífica**, disfruté mucho, tanto de la compañía, que era inmejorable, cómo de la oportunidad de juntarnos 2 días para intentar realizar un proyecto un poco más social&#8230; definitivamente se lo recomiendo a cualquier desarrollador que se atreva y yo mismo repetiré en la próxima oportunidad que surja.

Mucho tuvo que ver en el éxito del fin de semana la impecable organización de [Valentín Cardeñoso](https://twitter.com/vcp1984), que construyó un espacio único para que pudieramos desarrollar sin problemas. Un kudos gigante por una **organización espectacular** :)

Por último, tuvimos la suerte de conseguir el segundo premio local con la aplicación móvil y el tercero con la aplicación web, junto con el accésit de diseño por el excelente trabajo de [Mario](https://twitter.com/maduil). El primer premio fue a [BlueCom](http://vimeo.com/61355599), más que bien merecido, ya que el proyecto era espectacular  :)(Arduino, Bluetooth, pulsadores, aplicación móvil con barrido&#8230;)

Nos vemos en la próxima!

