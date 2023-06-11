---
title: ¿Qué es GNU/Linux?
category: Linux
tags: Linux Información
date: 2022-07-22 21:00
published: true
page_id: 16
---

{% assign _008 = site.posts | where: "page_id",  8 | first %}
{% assign _010 = site.posts | where: "page_id", 10 | first %}
{% assign _012 = site.posts | where: "page_id", 12 | first %}
{% assign _013 = site.posts | where: "page_id", 13 | first %}
{% assign _014 = site.posts | where: "page_id", 14 | first %}
{% assign _015 = site.posts | where: "page_id", 15 | first %}
{% assign _018 = site.posts | where: "page_id", 18 | first %}
{% assign _008_origenes_shell                 = _008.url %}
{% assign _010_richard_stallman               = _010.url %}
{% assign _012_licencias_software             = _012.url %}
{% assign _013_tipos_licencias_software_libre = _013.url %}
{% assign _014_unix                           = _014.url %}
{% assign _015_gnu                            = _015.url %}
{% assign _018_linus_torvalds     = _018.url %}

**GNU/Linux** es un *Sistema Operativo* (o una familia de sistemas operativos) tipo <a href="{{_014_unix}}">Unix</a> compuesto por <a href="{{_012_licencias_software}}">software libre</a> y de *código abierto*. Este sistema surge de las contribuciones de varios proyectos de software, entre los cuales destacan <a href="{{_015_gnu}}">GNU</a> (iniciado por <a href="{{_010_richard_stallman}}">Richard Stallman</a> en 1983) y el **kernel 'Linux'** (iniciado por <a href="{{_018_linus_torvalds}}">Linus Torvalds</a> en 1991).

A pesar de que en la jerga cotidiana la mayoría de las personas usan el vocablo **'Linux'** para referirse a este sistema operativo, en realidad ese es solo el nombre del *kernel* o *núcleo*, ya que el sistema completo está formado también por una gran cantidad de componentes del proyecto *GNU* junto a componentes de terceros, que van desde compiladores hasta entornos de escritorio. Cabe señalar que existen derivados que usan el *núcleo Linux* pero que no tienen componentes *GNU*, como por ejemplo el sistema operativo Android. También existen distribuciones de software *GNU* donde el *núcleo Linux* está ausente.

### Kernel Linux

El **kernel** o **núcleo**, es la parte central de cualquier *sistema operativo*. En palabras simples y simplificando mucho, digamos que es la parte que comunica los componentes de software del sistema con los recursos de hardware de la máquina.  En este sentido, cada distribución *GNU/Linux* opta por una versión específica del kernel, que no siempre tiene porque coincidir con la más reciente.

### GNU

Aquí me refiero al conjunto de herramientas propias del proyecto *GNU*, que conforman los componentes mas core del sistema y que, general, son independientes del entorno de escritorio utilizado. Algunas de las más conocidas son el interprete de comandos <a href="{{_008_origenes_shell}}#Bash">Bash</a>, el compilador *GCC*, o el propio entorno de escritorio *GNOME*, que forma parte también del proyecto *GNU*.

### El kernel Linux

**Linux** es el **kernel** desarrollado por *Linus Torvalds* en 1991 y ofrecido actualmente bajo una licencia <a href="{{_013_tipos_licencias_software_libre}}#GNU LGPL">GPL v2</a>. Si bien empezó como un proyecto a cargo de *Linus*, con la colaboración voluntaria de otros programadores, actualmente es un proyecto de titánicas proporciones. En él contribuyen todo tipo de empresas, algunas de la talla de *Red Hat, Intel, Samsung, Dell u Oracle*. Eso sin contar a *Microsoft* y *Google*, las cuáles ya son miembros Platino de la *Linux Foundation*.
