---
title: ¿Qué es un Servidor Proxy?
category: Informática
tags: Informática
date: 2023-04-15 00:00
published: true
page_id: 25
---

Un **servidor proxy** es un ordenador que sirve de intermediario entre un navegador web e Internet. Los servidores proxy permiten proteger y mejorar el acceso a las páginas web, al conservarlas en la caché. De este modo, cuando un navegador envía una petición para acceder a una página web, que previamente ha sido almacenada en la caché, la respuesta y el tiempo de visualización es más rápido. Los servidores proxy aumentan también la seguridad, ya que pueden filtrar cierto contenido web y programas maliciosos.

Se puede aplicar un filtrado que se aplica en función de las políticas de seguridad implementadas en la red. Este filtrado permite bloquear sitios considerados maliciosos o sitios considerados inútiles en relación a la actividad de la empresa (redes sociales, pornografía, etc.).

A fin de limitar el acceso a la red exterior, y aumentar de este modo la seguridad de la red local, se puede implementar un sistema de autenticación para acceder a recursos externos. Esto es bastante disuasivo para los usuarios que desean visitar sitios que estén en contra de las reglas de uso de Internet en la empresa.

El **almacenamiento de logs** de los sitios visitados y páginas vistas, permite al administrador de la red redefinir la política de seguridad de la red y/o detectar a un usuario que visita frecuentemente sitios maliciosos o sin relación con la actividad de la empresa.

Generalmente el servidor proxy se utiliza para la web. Se trata entonces de un **proxy HTTP**. Sin embargo, puede haber servidores proxy para cada protocolo de aplicación (**FTP**, etc.).

<div id="Servidor-Proxy"></div>

## ¿Cómo Funciona Un Servidor Proxy?

Se trata de un servidor que actúa como representante de una aplicación efectuando solicitudes en Internet en su lugar. De esta manera, cuando un usuario se conecta a Internet con una aplicación del cliente configurada para utilizar un servidor proxy, la aplicación primero se conectará con el servidor proxy y le dará la solicitud. El servidor proxy se conecta entonces al servidor al que la aplicación del cliente desea conectarse y le envía la solicitud en su lugar. Después, el servidor le envía la respuesta al proxy, el cual a su vez la envía a la aplicación del cliente.

El cliente realiza una petición (por ejemplo, mediante un navegador web) de un recurso de Internet (una página web o cualquier otro archivo) especificado por una URL.

Cuando el proxy caché recibe la petición, busca la URL resultante en su caché local. Si la encuentra, contrasta la fecha y hora de la versión de la página demanda con el servidor remoto. Si la página no ha cambiado desde que se cargó en caché la devuelve inmediatamente, ahorrándose de esta manera mucho tráfico pues sólo intercambia un paquete para comprobar la versión. Si la versión es antigua o simplemente no se encuentra en la caché, lo captura del servidor remoto, lo devuelve al que lo pidió y guarda o actualiza una copia en su caché para futuras peticiones.

El caché utiliza normalmente un algoritmo para determinar cuándo un documento está obsoleto y debe ser eliminado de la caché, dependiendo de su antigüedad, tamaño e histórico de acceso.

Desde el punto de vista del usuario de la red local, el sistema funciona como si tuviera realmente un acceso directo a Internet. El usuario accede inmediatamente desde su ordenador a una página Web o recibe su correo electrónico, sin siquiera saber que el proxy existe.
 
<div id="Tipos-Proxies"></div>

## Diferentes tipos de proxies

Hay cuatro tipos de servidores proxy que difieren según el nivel de anonimato y para qué se utilizan. Estos tipos incluyen Servidores Proxy Anónimos, Servidores Proxy de Alto Nivel de Anonimato, Servidores Proxy Transparentes y Servidores Proxy Inversos.


<div id="Proxy-Anonimo"></div>

### Proxy Anónimo

El tipo de proxy más conocido es el Proxy Anónimo que se usa para enmascarar la dirección IP de la computadora original. No hay forma de que la computadora de punto final que está recibiendo tus solicitudes descubra cuál es la IP de tu hogar y, si existe una necesidad de mayor seguridad, la conexión entre tú y el servidor proxy puede ser encriptada. Esta es la forma en que la mayoría de los usuarios individuales se conectan a través del proxy. Un Proxy Anónimo, además de ocultar la dirección IP, puede eliminar cookies, pop-ups, banners, scripts e información confidencial en los campos de texto (nombre de usuario y contraseña).

<div id="Proxy-HAP"></div>

### Proxy de Alto Nivel de Anonimato (HAP)

Los Proxy de Alto Nivel de Anonimato proporcionan incluso más anonimato que la conexión normal, ya que no se presenta como un servidor proxy, sino como una computadora común que crea una solicitud de acceso unidireccional a internet. De esta forma, el sitio web o la aplicación de punto final se refiere al servidor proxy como un cliente y no como un punto de nodo, lo que evita las restricciones que algunos sitios web y aplicaciones presentan en los servidores proxy.

<div id="Proxy-Transparente"></div>

### Proxy Transparente

Si bien esto no es algo que la mayoría de los usuarios individuales considerarían como un servidor proxy, un proxy transparente solo se usa como servidor de paso y presenta la dirección IP doméstica como la computadora que realiza la solicitud. Como no hay anonimato, este tipo de servidor proxy no se usa para los mismos fines que los dos primeros, sino como una computadora para compartir recursos para algunos negocios. Este tipo de proxy es la base para muchos sistemas basados en la nube, que usan múltiples computadoras proxy, pero siempre muestran la dirección IP principal.

<div id="Proxy-Inverso"></div>

### Proxy inverso

El último tipo de servidor proxy es el proxy inverso donde el objetivo de la conexión no es protegerte al acceder a páginas web y aplicaciones, sino evitar que otros en internet accedan libremente a tu computadora. Si bien este tipo de proxy tiene una aplicación personal para las personas que almacenan datos confidenciales en su disco duro, la aplicación habitual es para las empresas más grandes que tienen recursos de la compañía en computadoras individuales y, al usar una conexión de proxy inverso, impiden conexiones de terceros a esas computadoras y en su lugar usan el servidor que puede protegerlos con una gran cantidad de encriptaciones, cortafuegos y otras medidas.

El servidor de proxy inverso es utilizado como un intermediario por los usuarios de Internet que desean acceder a un sitio web interno al enviar sus solicitudes indirectamente. Con un proxy inverso, el servidor web está protegido de ataques externos directos, lo cual fortalece la red interna. Además, la función caché de un proxy inverso puede disminuir la carga de trabajo del servidor asignado, razón por la cual se lo denomina en ocasiones acelerador de servidor. Finalmente, con algoritmos perfeccionados, el proxy inverso puede distribuir la carga de trabajo mediante la redirección de las solicitudes a otros servidores similares. Este proceso se denomina equilibrio de carga.
