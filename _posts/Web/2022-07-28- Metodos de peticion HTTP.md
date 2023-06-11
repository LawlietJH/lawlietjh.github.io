---
title: Métodos de petición HTTP
category: Web
tags: Información HTTP Web
date: 2022-07-28 00:00
published: true
page_id: 22
---

### ¿Qué es el HTTP?

*HTTP* es un protocolo. De hecho, el acrónimo significa **Protocolo de Transferencia de Hipertexto**. Este protocolo rige la estructura y el lenguaje de las peticiones y respuestas que tienen lugar entre clientes y servidores. Los clientes suelen ser los navegadores web, pero pueden presentarse de muchas formas, como los robots de los motores de búsqueda.

Cuando visitas sitios web a través de un navegador, toda la conexión tiene lugar a través de *HTTP*. El protocolo te permite recibir datos, incluyendo *texto, imágenes, vídeos, hojas de estilo, scripts, etc.*

*HTTP* ha sido una de las columnas vertebrales de la web desde principios de los 90. En las últimas décadas, ha evolucionado para ser más eficiente. En la segunda mitad de la década de 2010 se desarrolló *HTTP/2*, que permite a los clientes cargar los recursos de forma simultánea en lugar de asíncrona. Esto da lugar a un aumento masivo del rendimiento.

### Métodos HTTP

**HTTP** define un conjunto de métodos de petición para indicar la acción que se desea realizar para un recurso determinado. Aunque estos también pueden ser sustantivos, estos métodos de solicitud a veces son llamados *HTTP verbs*.

### GET

El método **GET** solicita una representación de un recurso específico. Las peticiones que usan el método *GET* sólo deben recuperar datos.

### HEAD

El método **HEAD** pide una respuesta idéntica a la de una petición *GET*, pero sin el cuerpo de la respuesta.

### POST

El método **POST** se utiliza para enviar una entidad a un recurso en específico, causando a menudo un cambio en el estado o efectos secundarios en el servidor.

### PUT

El modo **PUT** reemplaza todas las representaciones actuales del recurso de destino con la carga útil de la petición.

### DELETE

El método **DELETE** borra un recurso en específico.

### CONNECT

El método **CONNECT** establece un túnel hacia el servidor identificado por el recurso.

### OPTIONS

El método **OPTIONS** es utilizado para describir las opciones de comunicación para el recurso de destino.

### TRACE

El método **TRACE** realiza una prueba de bucle de retorno de mensaje a lo largo de la ruta al recurso de destino.

### PATCH

El método **PATCH** es utilizado para aplicar modificaciones parciales a un recurso.
