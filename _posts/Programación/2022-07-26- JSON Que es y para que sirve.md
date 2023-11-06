---
title: "JSON: ¿Qué es y para qué sirve?"
category: Programación
tags: Información JSON
date: 2022-07-26 00:00
published: true
page_id: 20
---

**JSON** son las siglas de *JavaScript Object Notation* o *Notación de Objetos de JavaScript*, es un formato ligero de intercambio de datos muy simple de leer y escribir para los programadores y fácil de generar e interpretar por las máquinas. Este es un formato de texto completamente independiente de un lenguaje de programación, pero utiliza convenciones que son ampliamente conocidos por programadores.

A pesar de su nombre, no es necesariamente parte de JavaScript, de hecho, es un estándar basado en texto plano para el intercambio de datos, por lo que se usa en muchos sistemas que requieren mostrar o enviar información para ser interpretada por otros sistemas.

Una de las características de JSON, al ser un formato que es independiente de cualquier lenguaje de programación, es que los servicios que comparten información por este método no necesitan hablar el mismo idioma, es decir, el emisor puede ser Java y el receptor Python, pues cada uno tiene su propia librería para codificar y decodificar cadenas en este formato.

Podemos concluir entonces en que JSON es un formato común para **'serializar'** y **'deserializar'** objetos en la mayoría de los idiomas.

Un archivo *JSON* tiene como extensión **.json**, además los datos que contiene son representados en pares: *key:value*.

Aprender a interpretar JSON es fundamental para cualquier desarrollador, ya que es el formato de texto más ampliamente usado en el mundo para la comunicación entre software.

<div id="Sintaxis JSON"></div>
### Sintaxis básica de JSON

```json
{
    "key": "value",
    "key2": true,
    "key3": 7,
    "key4": false,
    "key5": null,
    "words": ["word1", "word2", "word3", "word4"],
    "otherWords": {
        "one": "Name1",
        "two": "Name2",
        "three": "Name3"
    }
}
```

JSON define 6 tipos de valores: *nulos*, *enteros*, *cadenas*, *booleanos*, *arreglos* y *objetos*.

<div id="Reglas Sintaxis JSON"></div>
### Reglas para sintaxis JSON

*JSON* es muy estricto en cuanto a los tipos de datos soportados.

Las reglas de sintaxis *JSON* que hay que conocer:

* Todos los datos del archivo deben estar rodeados de *llaves* {} si quieres representar un *objeto* y entre corchetes cuadrados si es un *arreglo* [].
* Las comillas simples no están permitidas, solamente dentro de las cadenas de texto.
* La *key* en cada JSON debe ser única por *objeto* y debe estar entre comillas dobles.
* Los números no deben ir entre comillas dobles, de lo contrario se tratarán como cadenas de texto.
* El tipo de dato *null* no debe ir entre comillas dobles.
* Los valores booleanos solo pueden ser *true* o *false*.
* Cada par *key:value* debe terminar con una coma, excepto el último elemento.
* Un solo objeto dentro de un *arreglo* debe terminar también con una coma.
* Para escapar un carácter se debe utilizar un '\\' por delante.


### Conclusión

Como programador, es indispensable entender el formato JSON, la mayoría de las API actuales trabajan con él en lugar de XML (antes ampliamente empleado).

JSON fue inicialmente concebido por JavaScript, pero ahora muchos otros lenguajes lo soportan gracias a su simplicidad y su naturaleza independiente del lenguaje.

En Python podemos encontrar un ejemplo práctico del uso de JSON a través de los *Diccionarios*, una adaptación muy similar para el manejo de objetos por *key:value*.
