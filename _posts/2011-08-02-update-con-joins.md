---
id: 371
title: Update con joins
date: 2011-08-02T11:00:29+00:00
author: nhpatt
layout: post
guid: http://nhpatt.com/update-con-joins/
permalink: /update-con-joins/
categories:
  - dev
---
Estos últimos días he estado integrando una base de datos SQL Server en otra existente en Oracle (not fun). Llevaba mucho tiempo sin trabajar directamente con sentencias SQL, así que no me ha costado nada de tiempo descubrir algo que no sabía.

Así que, [exponiendo mi ignorancia](http://www.oreilly.com/ofps/): no sabía que se podían hacer cruces en sentencias update de SQL. Y al parecer es algo bastante [común](https://www.google.com/search?sourceid=chrome&ie=UTF-8&q=join+update&gws_rd=ssl). Para el que no lo supiera, como yo, aquí va un pequeño resumen.

La sintaxis habitual de una sentencia UPDATE es:

```sql
  UPDATE _tabla t_ SET _t.columna_ = _valor_;
```

Si quieres hacer un cruce con otra tabla, siempre he hecho algo así:

```sql
  UPDATE _tabla t_ SET _t.columna_ =
    (SELECT _e.valor_ FROM _tabla2 e_
     WHERE _t.columna = e.columna_);
```

Esa sentencia es **muy ineficiente**, por lo que tarda mucho. Puedes hacer apaños y poner un índice en el cruce o bien, utilizar joins directamente! . Esto es válido en MySQL:

```sql
  UPDATE _t_ SET _t.columna = e.valor_ FROM_ tabla t_
  INNER JOIN_ tabla2 e_ ON _t.columna = e.columna;_
```

Puedes completar la consulta con los cruces que necesites. Es sustancialmente más rápida, por lo que ahora pienso en los minutos que he gastado optimizando updates con subconsultas.

En Oracle la sintaxis es diferente:

```sql
  UPDATE /*+BYPASS_UJVC*/
   (SELECT t.columna antiguoValor,e.columna nuevoValor
    FROM tabla t, tabla2 e
    WHERE t.columna = e.columna) 
  SET antiguo = nuevo
```

El hint (/\*+BYPASS_UJVC\*/) es necesario ya que por defecto sólo actualiza si los valores están indexados. La sintaxis de este UPDATE no se parece a nada de lo que haya visto antes pero funciona. Escribes tu consulta de selección y luego aplicas unos alias para actualizar.

Ya me diréis si os es útil o si ya lo sabíais desde hace mucho tiempo.

PD: Comentaba @[germanDZ](https://twitter.com/germanDZ) que el hint es feo feo. Adjunto la respuesta, porque da más claridad al post:

> A mi me parece feísimo. En AskTom comentan que nunca debería usarse para una query repetible (en PL o aplicación) pero para una manipulación manual con resultado acotado (como era el caso) te sirve para salir del paso.

  Muchísimo más bonita la sintaxis estándar que Oracle no soporta :S.

Otra posibilidad es hacer un [Merge](http://en.wikipedia.org/wiki/Merge_(SQL)) :)

