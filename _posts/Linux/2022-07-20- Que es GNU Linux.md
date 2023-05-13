---
title: "¿Qué es GNU/Linux?"
category: "Linux"
tags: ["Linux", Información]
date: 2022-07-20 21:02
published: true
page_id: 16
---

{% assign _010 = site.posts | where: "page_id", 10 | first %}
{% assign _015 = site.posts | where: "page_id", 15 | first %}
{% assign _018 = site.posts | where: "page_id", 18 | first %}

{% assign _010_richard_stallman = _010.url %}
{% assign _015_gnu              = _015.url %}
{% assign _018_linus_torvalds   = _018.url %}

**GNU/Linux** es un *Sistema Operativo* (o una familia de sistemas operativos) tipo *Unix* compuesto por *software libre* y de *código abierto*. Este sistema surge de las contribuciones de varios proyectos de software, entre los cuales destacan <a href="{{_015_gnu}}">GNU</a> (iniciado por <a href="{{_010_richard_stallman}}">Richard Stallman</a> en 1983) y el **kernel 'Linux'** (iniciado por <a href="{{_018_linus_torvalds}}">Linus Torvalds</a> en 1991).

A pesar de que en la jerga cotidiana la mayoría de las personas usan el vocablo **'Linux'** para referirse a este sistema operativo, en realidad ese es solo el nombre del *kernel* o *núcleo*, ya que el sistema completo está formado también por una gran cantidad de componentes del proyecto *GNU* junto a componentes de terceros, que van desde compiladores hasta entornos de escritorio. Cabe señalar que existen derivados que usan el *núcleo Linux* pero que no tienen componentes *GNU*, como por ejemplo el sistema operativo Android. También existen distribuciones de software *GNU* donde el *núcleo Linux* está ausente.
