---
title: "Sistemas Operativos: La Familia Unix"
category: "Linux"
tags: ["Linux", Información]
date: 2022-07-20 21:05
published: true
page_id: 19
---

{% assign _010 = site.posts | where: "page_id", 10 | first %}
{% assign _013 = site.posts | where: "page_id", 13 | first %}
{% assign _014 = site.posts | where: "page_id", 14 | first %}
{% assign _015 = site.posts | where: "page_id", 15 | first %}
{% assign _016 = site.posts | where: "page_id", 16 | first %}
{% assign _018 = site.posts | where: "page_id", 18 | first %}

{% assign _010_richard_stallman               = _010.url %}
{% assign _013_tipos_licencias_software_libre = _013.url %}
{% assign _014_unix                           = _014.url %}
{% assign _015_gnu                            = _015.url %}
{% assign _016_gnu_linux                      = _016.url %}
{% assign _018_linus_torvalds                 = _018.url %}

*Windows de Microsoft* y *macOS de Apple*, son quizás los sistemas operativos más conocidos. Pero no son los únicos.

<div id="Unix"><br></div>

### UNIX

El sistema operativo <a href="{{_014_unix}}">UNIX</a> fue creado por los laboratorios Bell de *AT&T* en 1969 y es un *SO* multiusuario y multitarea, que corre en diferentes computadoras, desde *supercomputadoras*, *Mainframes*, *Minicomputadoras*, computadoras personales y estaciones de trabajo.

<div id="GNU"><br></div>

### GNU

<a href="{{_015_gnu}}">GNU</a> se inició en 1983 por <a href="_010_richard_stallman">Richard Stallman</a>. Tiene como objetivo el desarrollo de un sistema operativo Unix completo y compuesto enteramente de Software libre.

<div id="GNU Hurd"><br></div>

### GNU Hurd

*GNU* tenía su propio proyecto de nucleo, llamado **Hurd**. Sin embargo, su desarrollo no continuó como se esperaba al aparecer el Nuleo de Linux.

<div id="GNU Linux"><br></div>

### GNU/Linux

A principios de los años 90, <a href="{{_018_linus_torvalds}}">Linus Torvalds</a> comenzó a escribir un sistema operativo que pudiera ejecutarse en un computador personal de la época. Al mismo tiempo, ya se desarrollaba otro proyecto con la intención de crear un sistema operativo tipo *Unix* gratuito: el proyecto *GNU*. Este proyecto tenía muchas herramientas listas, pero faltaba el núcleo del sistema. Fue cuestión de tiempo para que el núcleo Linux se distribuyera junto con las herramientas GNU, dando lugar a lo que hoy conocemos como <a href="{{_016_gnu_linux}}">GNU/Linux</a> o simplemente *Linux*, un sistema operativo libre de la familia *Unix*.

*GNU/Linux* es uno de los términos empleados para referirse a la combinación del núcleo libre similar a Unix denominado *Linux* con el sistema operativo *GNU*.

Lo que realmente marcó la diferencia y el éxito de este proyecto fue la licencia de uso: el proyecto GNU creó la licencia de software <a href="{{_013_tipos_licencias_software_libre}}#GNU LGPL">GPL</a>, una licencia que garantiza libertades en el uso, modificación y colaboración respecto al software. Así que Linux y las herramientas de *GNU* son desarrolladas, revisadas, mejoradas y adaptadas por miles de usuarios y cientos de empresas alrededor del mundo. Además, este conjunto está disponible sin costo y su código fuente es abierto.

<div id="BSD"><br></div>

### BSD

A finales de los años 70, en la *Universidad de California* se desarrollaba un sistema *Unix* llamado **BSD** (por *Berkeley Software Distribution*). Por conflictos en licencias, al principio, el sistema no tuvo mucha adopción pero, una vez superados estos inconvenientes, se pudo lanzar la primera versión de *FreeBSD* en 1993.

Actualmente, el equipo de *FreeBSD* desarrolla tanto el núcleo del sistema como las herramientas y la documentación, así que es un sistema muy ordenado y bien integrado. Su licencia de distribución también es de software libre, pero mucho más permisiva que la propia *GPL*, así que se puede encontrar código *BSD* en sistemas comerciales como *macOS* de *Apple* y en las consolas *PlayStation 3* y *PlayStation 4* de *Sony*.

*"A diferencia de otros, con Unix tienes libertad para elegir cómo quieres que se vea tu sistema."*

<div id="AIX"><br></div>

### AIX

Esta familia surge por el licenciamiento de *UNIX System III* a *IBM*.

<div id="HP-UX"><br></div>

### HP-UX

Es la versión de *Unix* desarrollada y mantenida por *Hewlett-Packard* desde 1983, ejecutable típicamente sobre procesadores *HP PA RISCY* y en sus últimas versiones sobre *Intel Italium* (arquitectura Intel de 64 bits).

<div id="Irix"><br></div>

### Irix

Es un sistema operativo compatible con *Unix*, creado por Silicon Graphics para su plataforma *MIPS* de 64 bits.

<div id="Minix"><br></div>

### Minix

Este sistema es para *PC* y *VAX*. Se distribuye con los fuentes. Compatible con la versión 7.

<div id="System V"><br></div>

### System V

**System V** es la versión más ampliamente usada de *UNIX*. Es el descendiente directo del *UNIX* desarrollado por *AT&T* en 1969.

<div id="Solaris"><br></div>

### Solaris

Basado en el sistema operativo *UNIX BSD*.

<div id="UnixWare"><br></div>

### UnixWare

Basado en el sistema operativo *Unix System V* y vendido a *SCO*.

<div id="Xenix"><br></div>

### Xenix

Familia derivada de la adquisición de los derechos originales de *AT&T* primero por parte de *Microsoft* y de esta los vendió a *SCO*.

<div id="Otros"><br></div>

### Otros Sistemas Operativos UNIX

*macOS* también es un sistema *Unix* al igual que *Android* (derivado de *Linux*) e *iOS* (derivado de *Mac OS X*).

<div id="GUI"><br></div>

### La Parte Gráfica

Un sistema *Unix* sólo incorpora el *núcleo*, las herramientas básicas y un intérprete de comandos. Este último es el programa que recibe instrucciones del usuario en forma de texto y las procesa, así que un sistema *Unix* estándar solo presenta una terminal de letricas, al mejor estilo del *DOS* de *Microsoft* en los años 80. Pero esto no quiere decir que un sistema Unix no pueda tener una interfaz gráfica. De hecho, ha tenido muchas.

El componente principal del sistema gráfico en *Unix* es el servidor *X*, desarrollado en el *MIT* en los años 80, que permite a las aplicaciones en *Unix* acceder a la pantalla, el teclado y el ratón. Pero siguiendo su filosofía, es otro componente adicional el que presenta las ventanas y menús que conocemos: el gestor de ventanas. Funciones como: mover, minimizar o cambiar el tamaño de una ventana son responsabilidad de este componente.

Por otra parte, un ambiente de escritorio es otro componente que incluye un gestor de ventanas, explorador de archivos, reproductores multimedia, fondos de escritorio, protectores de pantalla y menús de aplicaciones, entre otras.
Existen varios entornos de escritorio, entre los primeros que existieron están *TWM* y *CDE*. Luego, aparecieron unos más modernos como *Gnome* y *KDE* y, actualmente, contamos con *MATE* y *Unity*.