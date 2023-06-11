---
title: "API: ¿Qué es y para qué sirve?"
category: Web
tags: Información API Web
date: 2022-07-27 00:00
published: true
page_id: 21
---

{% assign _020 = site.posts | where: "page_id", 20 | first %}
{% assign _020_json = _020.url %}

**API** son las siglas de *Application Programming Interface* o *Interfaz de Programación de Aplicaciones* es un conjunto de subrutinas, funciones o métodos para ser utilizada por otro software como una capa de abstracción. Es la manera más simple de comunicar 2 componentes de software completamente distintos entre sí.

La arquitectura de las *API* suele explicarse en términos de cliente y servidor. La aplicación que envía la solicitud se llama cliente, y la que envía la respuesta se llama servidor.

<div id="Endpoint"><br></div>
### ¿Qué es un Endpoint?

Los **Endpoints** son las *URLs* de un *API* o un *backend* que responden a una petición, ejemplo `/users`, `/users/{id}/gallery`, etc. Por otra parte, un *Entrypoint* es la *URL* que el visitante habrá ingresado en su navegador para ver su aplicación o sitio, ejemplo `home.html`, `gallery.html`, etc. Los mismos *Entrypoints* tienen que calzar con un *Endpoint* para existir.

<div id="Tipos de API"><br></div>
### ¿Cómo funcionan las API?

Las *API* pueden funcionar de cuatro maneras diferentes, según el momento y el motivo de su creación.

#### API de SOAP

Estas *API* utilizan el protocolo simple de acceso a objetos. El cliente y el servidor intercambian mensajes mediante *XML*. Se trata de una *API* menos flexible que era más popular en el pasado.

#### API de RPC

Estas *API* se denominan llamadas a procedimientos remotos. El cliente completa una función (o procedimiento) en el servidor, y el servidor devuelve el resultado al cliente.

#### API de WebSocket

La API de *WebSocket* es otro desarrollo moderno de la *API web* que utiliza *objetos* <a href="{{_020_json}}">JSON</a> para pasar datos. Esta admite la comunicación bidireccional entre las aplicaciones cliente y el servidor. El servidor puede enviar mensajes de devolución de llamada a los clientes conectados, por lo que es más eficiente que la API de *REST*.

#### API de REST

Estas son las *API* más populares y flexibles que se encuentran en la web actualmente. El cliente envía las solicitudes al servidor como datos. El servidor utiliza esta entrada del cliente para iniciar funciones internas y devuelve los datos de salida al cliente.

<div id="API REST"><br></div>
### ¿Qué son las API REST?

**REST** son las siglas de *Representational State Transfer* o *Transferencia de Estado Representacional*. *REST* define un conjunto de funciones como *GET*, *POST*, *PUT*, *DELETE*, etc. que los clientes pueden utilizar para acceder a los datos del servidor. Los clientes y los servidores intercambian datos mediante *HTTP*.

La principal característica de la API *REST* es la ausencia de estado. La ausencia de estado significa que los servidores no guardan los datos del cliente entre las solicitudes. Las solicitudes de los clientes al servidor son similares a las *URL* que se escriben en el navegador para visitar un sitio web. La respuesta del servidor son datos simples, sin la típica representación gráfica de una página web. La información se entrega por medio de *HTTP* en uno de estos formatos: <a href="{{_020_json}}">JSON</a>, HTML, XLT, Python, PHP o texto sin formato.

*REST* no es un protocolo ni un estándar, sino más bien un conjunto de límites de arquitectura. Los desarrolladores de las *API* pueden implementarlo de distintas maneras.

Cuando una *API* aplica *REST* se concidera que es una *API RESTful*.
