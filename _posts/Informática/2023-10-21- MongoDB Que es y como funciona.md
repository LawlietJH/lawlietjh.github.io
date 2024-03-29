---
title: "MongoDB: ¿Qué es y cómo funciona?"
category: Informática
tags: ["Informática", "Bases de Datos", "Información", "Tutorial"]
date: 2023-10-21 21:00
show_words: 85
published: true
page_id: 30
---

{% assign _016 = site.posts | where: "page_id", 16 | first %}
{% assign _020 = site.posts | where: "page_id", 20 | first %}
{% assign _016_gnu_linux = _016.url %}
{% assign _020_json      = _020.url %}

Si hablamos de Bases de Datos lo más común es pensar en SQL y su modelo relacional, pero existen alternativas como los modelos no relacionales donde MongoDB es el más destacado.

El nombre **MongoDB** proviene de "Humongous" (Gigantesco) y "Database" (Base de Datos), es un sistema de base de datos NoSQL orientado a documentos de código abierto y que está escrito en C++, que en lugar de guardar los datos en tablas lo hace en estructuras de datos BSON (Binary <a href="{{_020_json}}">JSON</a>) con un esquema dinámico. Este proyecto se encuentra disponible para los sistemas operativos Windows, <a href="{{_016_gnu_linux}}">GNU/Linux</a>, OS X y Solaris.

La razón de que MongoDB se encuentre en miles de proyectos en todo el mundo se debe a que, al estar escrito en C++, cuenta con una notoria capacidad para aprovechar los recursos de la máquina y, al estar licenciado bajo licencia GNU AGPL 3.0, se adapta perfectamente a nuestras necesidades.


## Cómo funciona MongoDB

MongoDB es una base de datos orientada a documentos, esto quiere decir que en lugar de guardar los datos en registros, guarda los datos en documentos. Estos documentos son almacenados en BSON, que es una representación binaria de JSON, y esto representa una de las diferencias más importantes con respecto a las bases de datos relacionales. Y resulta que no es que no es necesario seguir un esquema, los documentos de una misma colección (concepto similar a una tabla de una base de datos relacional), pueden tener esquemas diferentes.

A continuación, exploraremos algunas características clave de MongoDB:

* **Documentos**: Los datos se almacenan en documentos `BSON`, que son similares a objetos JSON. Cada documento puede tener una estructura diferente, lo que hace que MongoDB sea altamente flexible.

* **Colecciones**: Los documentos se organizan en colecciones, que son similares a tablas en bases de datos relacionales.

* **Escalabilidad**: MongoDB es altamente escalable y puede manejar grandes cantidades de datos y cargas de trabajo.

* **Consultas y búsquedas flexibles**: MongoDB permite realizar consultas complejas y búsquedas de texto completo, lo que lo hace ideal para aplicaciones que requieren flexibilidad en la recuperación de datos.

Imaginemos que tenemos una colección a la que llamamos *Libros*. Un documento podría almacenarse de la siguiente manera:

```json
{
    "title": "The Maze Runner",
    "author": "James Dashner",
    "book": 1,
    "country": "United States",
    "lenguages": "English",
    "series": "The Maze Runner Series",
    "genre": ["Young adult", "Science Fiction", "Post-Apocalyptic"],
    "published": "October 6, 2009",
    "pages": 375,
    "characters": [
        {
            "name": "Thomas",
            "books": [1, 2, 3]
        }
    ]
}
```

Como se puede observar, el documento es un JSON, la diferencia, es que internamente se le asignará un campo "_id" el cual será de tipo `ObjectID` como un identificador del documento. Este campo lo podemos modificar por cualquier valor enviandolo desde nuestro JSON.

Lo interesante viene cuando queremos almacenar en una misma colección un documento como este: `{ name: "Brenda", age: "17-19", gender: "Female", type: "Immune", ...  }`. Tal como podemos ver, este no sigue el mismo esquema del primero, añadiendo algún campo nuevo que no existe en el documento anterior o incluso de un tipo distinto, pero no importa. Algo que resulta impensable en una base de datos relacional como SQL es posible en MongoDB.


## Operaciones

La manera en la que podemos utilizar las operaciones básicas de mongo, es muy sencillo.


### Bases de datos

Crear y/o seleccionar una base de datos:
```bash
use my_database
```

Ver las bases de datos:
```bash
show databases
```

Eliminar la base de datos seleccionada:
```bash
db.dropDatabase()
```


### Colecciones

Ver las colecciones:
```bash
show collections
```

Crear una colección:
```bash
db.createCollection("my_collection", <options>)
```

Los 'options' son opcionales:

| Opción | Tipo | Descripción |
|--------|:----:|-------------|
| **capped**      | **Booleano** | Si es `true`, permite una colección limitada. Una colección limitada es una colección de tamaño fijo que sobrescribe automáticamente sus entradas más antiguas cuando alcanza su tamaño máximo. Si especifica `true`, también debe especificar el parámetro de `size`. |
| **autoIndexId** | **Booleano** | Si es `true` crea automáticamente un índice en el campo `_id`. Por defecto es `false` |
| **size**        | **Entero**   | Especifica el tamaño máximo en bytes para una colección limitada. Es obligatorio si el campo `capped` está a `true`. |
| **max**         | **Entero**   | Especifica el número máximo de documentos que están permitidos en la colección limitada. |

Ejemplo de uso:
```bash
db.createCollection("my_collection", {capped : true, autoIndexId: true, size: 6142800, max: 10000})
```


### Create, Read, Update & Delete (CRUD)

Insertar documentos en la colección: `insert` & `insert_one`
```bash
db.my_collection.insert({name: "Example", age: 30})
```

Realiza consultas para recuperar datos (Búsquedas): `find` & `find_one`
```bash
db.my_collection.find({name: "Example"})
```

Actualizar documentos: `update` & `update_one`
```bash
db.my_collection.update({name: "Example"}, {$set: {age: 30}})
```

Borrar documentos: `remove` & `remove_one`
```bash
db.my_collection.remove({name: "Example"})
```


##  Operadores Avanzados


### Operadores de comparación

Utilizados en filtros:

| Operador | Descripción |
|:--------:|-------------|
| **$eq**  | Coincide con valores que son iguales a un valor especificado.              |
| **$gt**  | Coincide con valores que son mayores que un valor especificado.            |
| **$gte** | Coincide con valores que son mayores o iguales que un valor especificado.  |
| **$in**  | Coincide con cualquiera de los valores especificados en una matriz.        |
| **$lt**  | Coincide con valores que son menores que un valor especificado.            |
| **$lte** | Coincide con valores que son menores o iguales que un valor especificado.  |
| **$ne**  | Coincide con todos los valores que no son iguales a un valor especificado. |
| **$nin** | No coincide con ninguno de los valores especificados en una matriz.        |


### Indexación

Los índices son fundamentales para optimizar el rendimiento de las consultas. Puedes crear índices en campos específicos para acelerar las búsquedas. Por ejemplo:
```bash
db.my_collection.createIndex({field: 1}) // Crea un índice ascendente
db.my_collection.createIndex({other_field: -1}) // Crea un índice descendente
```


### Agregación

MongoDB permite realizar operaciones de agregación para procesar datos en la base de datos y devolver resultados calculados. Aquí hay un ejemplo de agregación que calcula el promedio de una colección:
```bash
db.my_collection.aggregate([
    { $group: { _id: null, average: { $avg: "$field" } } }
])
```


### Consultas Avanzadas

MongoDB admite una variedad de operadores avanzados para realizar consultas más complejas. Por ejemplo, puedes usar el operador $or para buscar documentos que cumplan con una de varias condiciones:
```bash
db.my_collection.find({
    $or: [
        { field1: value1 },
        { field2: value2 }
    ]
})
```


### Transacciones

MongoDB 4.0 y versiones posteriores admiten transacciones para garantizar la integridad de los datos en operaciones complejas que involucran varias operaciones. Puedes iniciar una transacción de la siguiente manera:
```bash
session = db.getMongo().startSession()
session.startTransaction()

// Realiza operaciones dentro de la transacción
session.commitTransaction() // Para confirmar los cambios
session.abortTransaction()  // Para deshacer los cambios
session.endSession()
```


### Geolocalización

MongoDB es adecuado para datos geoespaciales. Puedes realizar consultas de geolocalización y encontrar documentos cercanos a una ubicación específica:
```bash
db.my_collection.find({
    location: {
        $near: {
            $geometry: {
                type: "Point",
                coordinates: [longitude, latitude]
            },
            $maxDistance: 1000 // Distancia máxima en metros
        }
    }
})
```


### Texto Completo

Puedes realizar búsquedas de texto completo en campos de texto utilizando el índice de texto completo de MongoDB:
```bash
db.my_collection.createIndex({text_field: "text"})
db.my_collection.find({ $text: { $search: "keyword" } })
```

<br><br>
Estos son solo algunos ejemplos de comandos y operaciones más avanzados en MongoDB. La base de datos ofrece una amplia gama de funcionalidades para adaptarse a diversas necesidades.

<br>
Debemos recordar que la documentación oficial de MongoDB es una fuente valiosa para explorar aún más estas capacidades.
