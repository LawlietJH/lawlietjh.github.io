---
title: "¿Qué es Minix?"
category: "Linux"
tags: ["Linux", Información]
date: 2022-07-20 21:03
published: true
---

**MINIX** es un *Clon del Sistema Operativo* <a href="Que-es-Unix">Unix</a> distribuido junto con su código fuente y desarrollado por el profesor **Andrew S. Tanenbaum** en 1987.

En 1975 los Laboratorios *Bell* de la *AT&T*, publicaron el sistema operativo *Unix V6*, para 1977 *John Lions* publicó unas notas con el código fuente que se usaba en los cursos de sistemas operativos. Cuando los Laboratorios Bell publicaron *Unix V7* en 1979, prohibieron su uso para la enseñanza. Por lo que en 1984 *Andrew S. Tanenbaum* comenzó a escribir un clon de *Unix* para las *IBM-PC* con *Intel 8086* de ese tiempo, con el fin de usarlo en su clase en lugar del entonces prohibido *Unix*. Terminado en 1987 pudo usarlo para enseñar a sus alumnos el diseño de sistemas operativos en la *Vrije Universiteit de Ámsterdam*.

Su libro fue ampliamente adoptado, porque además de que *Unix* estaba bajo restricciones de licencia de AT&T, era demasiado complicado y corría sobre máquinas complejas; algo completamente antipedagógico, mientras que *Minix* fue escrito con fines pedagógicos y para una máquina muy accesible. En 1997 publicó *Minix 2* y en el 2004, gracias al financiamiento de la Union Europea, *Minix 3* que es compatible con *NetBSD* y a prueba de fallas.

Gracias a su reducido tamaño, diseño basado en el paradigma del *micronúcleo*, y su amplia documentación, resulta bastante apropiado para personas que desean instalar un sistema operativo compatible con *Unix* en su máquina personal, así como aprender sobre su funcionamiento interno.

El primer *Minix* fue desarrollado para ser ejecutado en un *IBM PC* con *microprocesador Intel 8088* o superior, aunque se han creado conversiones para otros sistemas y *Minix 3*, también corre en procesadores *ARM*.

Debido al enfoque puramente educacional de *MINIX*, Tanenbaum no permitía que este fuera modificado demasiado ya que esto complicaría el sistema y no permitiría que sus estudiantes lo entendieran en un semestre. Por estos motivos, <a href="Quien-es-Linus-Torvalds">Linus Torvalds</a> decidió escribir su propio núcleo de sistema operativo (<a href="Que-es-GNU-Linux">Linux</a>) compatible con *Unix*. En simbiosis con las herramientas de <a href="Que-es-GNU">GNU</a> surgió GNU/Linux, que ha ganado protagonismo en el campo de los Unix para ordenadores compatibles con el *IBM PC*, principalmente debido a que su licencia (<a href="/software libre/Tipos-de-Licencias-de-Software-Libre#GNU LGPL">GPL</a>) permite la modificación del mismo. Actualmente *Minix* se distribuye con una licencia similar, la licencia <a href="/software libre/Tipos-de-Licencias-de-Software-Libre#BSD">BSD</a>, que es menos restrictiva que la de GNU, porque en palabras de Tenembaum, "está permitido todo excepto demandarlo".

Para una persona poco familiarizada con los elementos internos de un sistema operativo, *MINIX* es una buena opción que le permite entender casi todos los elementos del sistema, con solo algunos meses de uso y estudio.
