---
title: "Sistemas Operativos: La Familia Unix"
category: "Linux"
tags: ["Linux", Información]
date: 2022-07-20 21:05
published: true
---

*Windows de Microsoft* y *macOS de Apple*, son quizás los sistemas operativos más conocidos. Pero no son los únicos.

### GNU/Linux

A principios de los años 90, <a href="Quien-es-Linus-Torvalds">Linus Torvalds</a> comenzó a escribir un sistema operativo que pudiera ejecutarse en un computador personal de la época. Al mismo tiempo, ya se desarrollaba otro proyecto con la intención de crear un sistema operativo tipo <a href="Quien-es-Unix">Unix</a> gratuito: el proyecto <a href="Quien-es-GNU">GNU</a>. Este proyecto tenía muchas herramientas listas, pero faltaba el núcleo del sistema. Fue cuestión de tiempo para que el núcleo Linux se distribuyera junto con las herramientas GNU, dando lugar a lo que hoy conocemos como <a href="Quien-es-GNU-Linux">GNU/Linux</a> o simplemente *Linux*, un sistema operativo libre de la familia *Unix*.

Lo que realmente marcó la diferencia y el éxito de este proyecto fue la licencia de uso: el proyecto GNU creó la licencia de software <a href="Tipos-de-Licencias-de-Software-Libre#GNU LGPL">GPL</a>, una licencia que garantiza libertades en el uso, modificación y colaboración respecto al software. Así que Linux y las herramientas de *GNU* son desarrolladas, revisadas, mejoradas y adaptadas por miles de usuarios y cientos de empresas alrededor del mundo. Además, este conjunto está disponible sin costo y su código fuente es abierto.

### BSD

Al mismo tiempo, a finales de los años 70, en la *Universidad de California* se desarrollaba un sistema *Unix* llamado **BSD** (por *Berkeley Software Distribution*). Por conflictos en licencias, al principio, el sistema no tuvo mucha adopción pero, una vez superados estos inconvenientes, se pudo lanzar la primera versión de *FreeBSD* en 1993.

Actualmente, el equipo de *FreeBSD* desarrolla tanto el núcleo del sistema como las herramientas y la documentación, así que es un sistema muy ordenado y bien integrado. Su licencia de distribución también es de software libre, pero mucho más permisiva que la propia *GPL*, así que se puede encontrar código *BSD* en sistemas comerciales como *macOS* de *Apple* y en las consolas *PlayStation 3* y *PlayStation 4* de *Sony*.

*"A diferencia de otros, con Unix tienes libertad para elegir cómo quieres que se vea tu sistema."*

### Otros Sistemas Operativos UNIX

*macOS* también es un sistema *Unix* al igual que *Android* (derivado de *Linux*) e *iOS* (derivado de *Mac OS X*).

### La Parte Gráfica

Un sistema *Unix* sólo incorpora el *núcleo*, las herramientas básicas y un intérprete de comandos. Este último es el programa que recibe instrucciones del usuario en forma de texto y las procesa, así que un sistema *Unix* estándar solo presenta una terminal de letricas, al mejor estilo del *DOS* de *Microsoft* en los años 80. Pero esto no quiere decir que un sistema Unix no pueda tener una interfaz gráfica. De hecho, ha tenido muchas.

El componente principal del sistema gráfico en *Unix* es el servidor *X*, desarrollado en el *MIT* en los años 80, que permite a las aplicaciones en *Unix* acceder a la pantalla, el teclado y el ratón. Pero siguiendo su filosofía, es otro componente adicional el que presenta las ventanas y menús que conocemos: el gestor de ventanas. Funciones como: mover, minimizar o cambiar el tamaño de una ventana son responsabilidad de este componente.

Por otra parte, un ambiente de escritorio es otro componente que incluye un gestor de ventanas, explorador de archivos, reproductores multimedia, fondos de escritorio, protectores de pantalla y menús de aplicaciones, entre otras.
Existen varios entornos de escritorio, entre los primeros que existieron están *TWM* y *CDE*. Luego, aparecieron unos más modernos como *Gnome* y *KDE* y, actualmente, contamos con *MATE* y *Unity*.