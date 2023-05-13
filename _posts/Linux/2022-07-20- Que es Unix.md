---
title: "¿Qué es Unix?"
category: "Linux"
tags: ["Linux", Información]
date: 2022-07-20 21:00
published: true
page_id: 14
---

{% assign _016 = site.posts | where: "page_id", 16 | first %}
{% assign _019 = site.posts | where: "page_id", 19 | first %}

{% assign _016_gnu_linux       = _016.url %}
{% assign _019_so_familia_unix = _019.url %}

Unix es un **Sistema Operativo** que nace a principios de los años 70, creado principalmente por **Dennis Ritchie** y **Ken Thompson**. Sus características técnicas principales son: su portabilidad, su capacidad multiusuario y multitarea, su eficiencia; su alta seguridad y su buen desempeño en tareas de red. Pero *Unix*, más que una marca, también es una filosofía que tiene por principios el minimalismo y la modularidad: hacer programas que hagan una sola cosa bien hecha y que, al comunicarse entre sí, ejecuten tareas más complejas.

Un sistema **Unix** puede dividirse en tres áreas básicas:
* El núcleo del sistema operativo.
* El intérprete de comandos y algunos programas utilitarios.
* Lo demás que necesitas, como las aplicaciones de usuario o la interfaz gráfica, son paquetes adicionales.

Por sus características técnicas y su filosofía abierta, existen diversos sistemas operativos que se conocen como derivados de Unix o sistemas de la familia *Unix*. Entre estos están <a href="{{_019_so_familia_unix}}#BSD">FreeBSD</a> y <a href="{{_016_gnu_linux}}">GNU/Linux</a>; macOS también es un sistema *Unix*, al igual que *Android* (derivado de *Linux*) e *iOS* (derivado de *Mac OS X*).
