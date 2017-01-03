---
id: 1172
title: Respondiendo a críticas sobre agile
date: 2015-04-12T19:12:36+00:00
author: nhpatt
layout: post
guid: http://nhpatt.com/respondiendo-a-criticas-sobre-agile/
permalink: /respondiendo-a-criticas-sobre-agile/
categories:
  - agile
---
Por varias redes sociales me ha llegado esta [crítica](http://www.quora.com/Why-do-some-developers-at-strong-companies-like-Google-consider-Agile-development-to-be-nonsense/answer/Michael-O-Church?srid=TyrG&share=1) a _agile_. Leedla y volved.

Esa crítica ha resonado bastante y me parece muy desacertada. Colaboro con [@agilecyl](http://twitter.com/agilecyl) y [@agilespain](http://twitter.com/agilespain) habitualmente por lo que mi opinión al respecto os la podéis imaginar.

Pero soy muy pragmático y el primero en reconocer que las metodologías ágiles tienen muchas pegas pero no son las señaladas en esa respuesta en quora.



## Primeras críticas.

Veamos:

> let&#8217;s describe where Agile/Scrum can work

Empezamos bien. _Agile _no está en el mismo saco que _Scrum_. No puedes hacer una crítica general en contra de esos 2 términos, uno es un [manifiesto](http://agilemanifesto.org/) (al que sinceramente veo imposible sacar pegas, pero si las tenéis, comentad!) y otro es una metodología con muchas pegas, discutidas hasta la saciedad. La crítica no sabe distinguir uno de otro.

> It can work for a time-sensitive and critical project _of short duration_ (6 weeks max) that cross-cuts the business and has no clear manager

El primer ejemplo de aplicación de XP fue con un proyecto para Chrysler de larga duración. Hay decenas de contraejemplos.

> You can call it a &#8220;Code Red&#8221; or call it a Scrum or a &#8220;War Room&#8221; if you have a physical room for it.

No. No es lo mismo. Un &#8220;Code Red&#8221; es debido a un problema/urgencia a resolver asociado a largas noches sin dormir, las metodologías ágiles necesitan ser sostenibles en el tiempo.

> Note that &#8220;Agile&#8221; comes from the consulting world. It suits well the needs of a small consulting firm, not yet very well-established, that lands one big-ticket project and needs to deliver it quickly.

Ains.

> despite changing requirements and other potential bad behavior from the client

Que los requisitos cambien no es mal comportamiento del cliente. Es que sus necesidades cambian, o antes no las tenía claras. El cliente **tiene que poder** y **cambiará** sus requisitos, esto está discutido hasta la saciedad.

Agile da la bienvenida a requisitos cambiantes y se centra en desarrollar lo que realmente necesita al cliente. La forma _tradicional_ de desarrollar es no dejarle cambiar los requisitos (ese mal comportamiento del que habla el autor) y terminar desarrollando algo que no se ajusta a lo que el usuario necesita.

> I&#8217;m not opposed to the &#8220;Code Red&#8221;/&#8221;crunch time&#8221;/Scrum practice of ignoring peoples&#8217; career goals and their individual talents.

Insisto, no es lo mismo. Ni Scrum es crunch time, es necesario tiempo de _slack_.

El &#8220;crunch time&#8221; es habitual en proyectos tradicionales, a las 3 semanas de entregar el proyecto te das cuenta de que te faltan mil cosas y dedicas decenas de horas a &#8220;terminar&#8221;. Agile insiste en entregar y enseñar algo al cliente cada cierto tiempo para detectar antes si no le gusta, avanzas poco&#8230;

## &#8220;Pecados&#8221; de Scrum

Pasemos a los pecados que son más jugosos&#8230;

> It&#8217;s a culture of terminal juniority.

Esta crítica es absurda, directamente. Mucha gente le echa en cara a las metodologías ágiles justo lo contrario, que funcionan mejor en un equipo sólo de seniors/gente independiente/generalistas. Porque _agile_ insiste en que el equipo debe ser autoorganizado y un junior generalmente no se atreve a trabajar sin una dirección estilo command & control.

> Product development and architecture aren&#8217;t the programmer&#8217;s job, because they take longer than two weeks.

Las dos tareas se puede (y se deben) desarrollar en iteraciones. Por lo que más me toca cómo técnico, una arquitectura debe emerger, no sentarte un mes a escribir bloques en papel que luego no se puedan ajustar a las necesidades reales. Pero esto da para otra discusión acalorada.

> Rather, the programmer works on atomized feature-level &#8220;user stories&#8221;. (&#8230;) anyone with more than 5 years of experience is going to find it to be a dissatisfying way to work.

Por qué?

> There is no place for an actual senior engineer on a Scrum team.

?? sinceramente, no lo entiendo. Por qué no puedes ser un senior engineer en un equipo de Scrum?

> The only way to move up is to become a &#8220;Scrum Master&#8221;, a bullshit management role that involves responsibility without power.

Tengo muchas pegas a este comentario. Primero, Scrum Master no es un ascenso con respecto a programador, es otro rol dentro del proyecto. Las metodologías ágiles se entremezclan con un organigrama más plano (que una empresa tradicional) en el que perfectamente puedes ascender, dentro de un rol técnico y dentro de un equipo ágil (sea Scrum u otra cosa). Los &#8220;ascensos&#8221; no tienen que ser hacia gestión (porque hay gente que no le gusta!). Y me preocupa el concepto de &#8220;poder&#8221; que insinúa en el comentario.

> If you don&#8217;t believe in this stuff yourself (and I don&#8217;t) then you sure as hell don&#8217;t want to move up into a role where you&#8217;re responsible for enforcing it over people who technically answer to someone else.

El Scrum Master no es responsable de &#8220;enforcing&#8221; nada. Y perfectamente puedes ser líder técnico de un equipo (resolviendo dudas, teniendo la última palabra en debates de arquitectura) dentro de un equipo ágil.

> It&#8217;s aggressively short-term, by design.

No. Scrum no es ir más rápido o unir crunch time con crunch time. Y otras metodologías ágiles menos. Insisto, está en el manifiesto: _&#8220;Agile processes promote sustainable development. The sponsors, developers, and users should be able to maintain a constant pace indefinitely.&#8221;._

> These methodologies are designed for scrappy, unproven consulting firms that need to bear down and pass their first high-profile project. (&#8230;) but people who join large corporations do so _because they don&#8217;t want to be underdogs_. They&#8217;d rather be a small part of something stable than a bigger part of something that no one else yet believes in. If they wanted that other deal, they&#8217;d be in tiny startups.

Me encanta el desprecio latente a las pequeñas empresas (puede que sea cosa mía).

> Second, if you carry this way of working on for months or years, you get a lot of technical debt and you get low morale. Senior engineers are quicker to go, because they usually want something meatier than filling out some other guy&#8217;s &#8220;user stories&#8221;.

Hay muchas formas de crear un producto a base de sprints y mantener la deuda técnica baja. Es un punto de debate habitual, puedes hacer sprints limpiando deuda técnica o de innovación, pactar un número determinado de historias de usuario en cada sprint, formar al cliente sobre la importancia de la calidad en base a tu relación de colaboración&#8230;

Es gracioso porque los proyectos enterprise tradicionales suelen ser representados cómo proyectos con muchísima deuda técnica y moral bajísima.

> It has no regard for the programmers&#8217; career needs or desires.

Precisamente las metodologías ágiles insisten en que la gente importante en el proyecto es la que está realmente implicada desarrollándolo. Esas personas tienen que estar motivadas (_&#8220;Build projects around motivated individuals.&#8221;_) y trabajar sin impedimentos (el rol de SM en Scrum está básicamente para eliminar molestias del equipo).

> Now, people are willing to give up their career goals to pitch in on a short-term crisis, for two reasons. First, if it&#8217;s genuinely important to the firm, then it does help their career to do so. Second, a story of having solved a genuine crisis under time pressure can be a career booster.

De nuevo, agile no es &#8220;crunch time&#8221; o &#8220;short-term crisis&#8221;.

> Saying, &#8220;I was in the War Room and had 20 minutes each day with the CEO&#8221; means that you were important and valued. Saying &#8220;I was on a Scrum team&#8221; means &#8220;Kick me&#8221;.

Épico.

> It&#8217;s micromanagement.

Agile insiste en la confianza en el equipo. Una crítica habitual más fundada es que no soporta bien gente desmotivada o que no la interesa su trabajo. &#8220;Give _them the environment and support they need, and trust them to get the job done.&#8221;_

> User stories and backlog grooming are there to control what the engineer works on. The absurdly frequent meetings (and so many different kinds of status meetings!) are to intimidate him into not slacking. The story points are there to track productivity (in some superficial, inaccurate way).

No. Las historias de usuario y el backlog (esto es Scrum, no agile, cómo toda la crítica) están para ver qué quiere el cliente, ver si el proyecto tiene problemas y cambiar de dirección si es necesario.

> The talk of &#8220;removing impediments&#8221; is code for &#8220;spotting slackers&#8221;. Even for people who have nothing to hide&#8211; even for people who&#8217;d be strong performers in a more sane, relaxed, progress-over-rapidity organization&#8211; a surveillance state is an anxiety state.

Me preocupa el entorno tóxico en el que ha trabajado&#8230; eliminar impedimentos es eliminar problemas, interrupciones, dudas técnicas, no controlar las horas que está el programador trabajando.

>  It sucks, and if you&#8217;re good at what you do, it&#8217;s insulting to have to justify days and sometimes even hours of your time, and to be jerked around if these estimates are even slightly displeasing to the &#8220;product owner&#8221;.

En ningún momento (ni en Scrum!) se habla de &#8220;justificar días u horas&#8221;. Sin hablar de &#8220;negociar&#8221; estimaciones. Eso no es ni Scrum, ni agile.

> Let&#8217;s not kid ourselves. The reason &#8220;Agile&#8221; is so popular is that it carries this mythology of spotting low performers immediately&#8211; in two weeks instead of over months&#8211; and giving objective cause to fire them.

Primera vez que oigo hablar de que agile es popular para poder despedir a alguien.

> Agile and Scrum, however, single out and humiliate anyone who works for 2 weeks and doesn&#8217;t have something to show for it.

No. Agile ve que algo va mal e intenta arreglarlo. Por qué no se ha hecho nada en 2 semanas? a lo mejor hay que descartar esa tecnología, o afrontar cosas más sencillas o pedir ayuda a otros equipos.

> This means that there&#8217;s no room to fail, thus no room to experiment. For senior engineers who already know that they can fulfill user stories and trivial features, this also means that there&#8217;s no point in going to work.

El equipo se auto organiza, si el ingeniero experto no quiere hacer historias/funcionalidades sencillas sólo tiene que hablar con sus compañeros. Si quiere investigar en algo sólo tiene que hablar (!) con su equipo.

La forma tradicional en desarrollo es investigar a escondidas y mientras tanto decir que estás trabajando en otras cosas. Agile insiste en transparencia y colaboración, si quieres investigar una tecnología háblalo con el equipo en vez de engañarles por la espalda.

> I have _actually_ seen it kill companies.

Ok. Qué se puede responder a esto? mira que lo dudo.

> (since Scrum is all about engineers not thinking for themselves)

Justo es todo lo contrario.

> It&#8217;s sold dishonestly (&#8230;).

Básicamente un párrafo de 20 líneas en el que vuelve a insistir que agile es crunch time (no. Y de feedback, hablar con el cliente, software funcionando&#8230; no menciona nada). Y una comparación de lo que se gana en una enterprise vs una startup/agency.

## Conclusiones

No he respondido a todo&#8230; porque hay mucho texto y es cansado contestar cuando está claro que el autor ha vivido un sucedáneo de Scrum que destruye todo lo útil que hay detrás. Todos los comentarios del autor son críticas a una &#8220;implantación de Scrum&#8221; en una empresa enterprise sin cambiar nada la forma de trabajar.

Me quedo con los errores habituales, Scrum != Agile, Agile o Scrum != crunch time cada 2 semanas.

Es un tema polémico, comentad!

