---
title: "Cómo crear una API REST con Python y Flask"
category: Programación
tags: Tutorial Python Flask API Web
date: 2022-07-28 00:03
published: true
---

Sabemos que, en el mundo de la programación, existe una fuerte necesidad por la comunicación entre componentes de software, una excelente solución a esto fueron las [API](/web/API-Que-es-y-para-que-sirve) y [JSON](JSON-Que-es-y-para-que-sirve).

En esta publicación les mostraré como crear una [API REST](/web/API-Que-es-y-para-que-sirve#API REST) básica utilizando *Flask* de manera muy simple.

Usaré el software [Insomnia](https://insomnia.rest/download){:target="_blank"} para hacer las peticiones a la *API* y poder ver los resultados fácilmente.

<div><br></div>
### Código base

Al manejar una *API REST* nos centraremos en un **CRUD** (*Create*, *Read*, *Update*, *Delete*) a un [Endpoint](/web/API-Que-es-y-para-que-sirve#Endpoint) utilizando los [Métodos de petición HTTP](/web/Metodos-de-peticion-HTTP): *GET*, *POST*, *PUT/PATCH*, *DELETE*.

Como base tomaremos este fragmento de código:

```python
# Name: app.py
from flask import Flask, jsonify, request

app = Flask(__name__)

if __name__ == '__main__':
    app.run(debug=True)
```

Con este pequeño fragmento de código podemos generar una aplicación básica en flask.

Podemos cambiar el puerto con el parámetro `port`.

```python
# Ejemplo:
app.run(debug=True, port=8000)
```

Si ahora corremos la aplicación con el comando `python app.py` se nos iniciará un pequeño servidor alojado en el puerto 5000 (por defecto). Podemos verlo en nuestro navegador si vamos a `http://localhost:5000` o desde **Insomnia** haciendo una petición `GET` a la misma *URL*.

Podemos observar lo siguiente:

![Error 404](/assets/images/2022-07-28/Python API REST 01 - 404.png)

Esto que estamos viendo es nuestro servidor, pero al no tener nada que mostrar, por defecto se nos mostrará el código de estado *404*.

Para la creación de la *API REST* necesitaremos una base de datos, pero por fines prácticos emplearé solamente un diccionario. Haré una base de datos que almacenará solamente frutas, su nombre, precio y cantidad. Agregaré 3 registros para tener algo que mostrar.

```python
fruits_db = [
    {'name': 'Apple',  'price': 10, 'quantity': 7},
    {'name': 'Banana', 'price': 5,  'quantity': 12},
    {'name': 'Pear',   'price': 7,  'quantity': 6}
]
```

<div><br></div>
### Creación de un Endpoint

Para la creación de un *endpoint*, debemos tener una función que devolverá la página solicitada y deberá tener un *decorador* (llamado *route*) que vendrá desde nuestra aplicación y recibirá como parámetro el nombre de nuestro *endpoint* y los métodos de petición *HTTP* (por defecto tendrá solamente *GET*).

Una *API REST* responderá las peticiones en un formato simple y en este caso utilizaré *jsonify* para las respuestas en formato *JSON*.

```python
# Ejemplo:
@app.route('/endpoint/', methods=['GET'])
def getData():
    return jsonify({'data': data})
```

Cada cosa que vayamos a manipular de la base de datos, es recomendable que sea a través de distintos *endpoints* y que cumplan unica y exclusivamente la tarea asignada. Como ejemplo, si deseas manipular empleados y clientes, puedes hacer un *CRUD* para `/employees`, y para `/customers`.

No importa cuantos *endpoints* tengas al final, lo importante es que seas organizado y así la API cumpla tus necesidades, respetando que cada endpoint cumpla una tarea especifica, ya sea manipular los registros de empleados o los de clintes, pero no ambos al mismo tiempo.

En este caso yo solo usaré `/fruits`, pues solo manipularé *frutas*.

<div id="Método GET"><br></div>
### Método GET

Para este ejemplo, este *endpoint* se llamará `/fruits`. Por defecto, este toma el método *GET*, y la función en este caso la llamaré `getFruits`. Este método servirá para pedir información a la base de datos.

```python
@app.route('/fruits/')
def getFruits():
    return jsonify({
        'message': "Fruit's List",
        'fruits': fruits_db
    })
```

Con este fragmento de código tenemos el método *GET* implementado, si vamos a `http://localhost:5000/fruits` podremos obtener toda la información, ya que en el campo `fruits` le estamos pasando nuestro diccionario de frutas.

```json
{
    "fruits": [
        {
            "name": "Apple",
            "price": 10,
            "quantity": 7
        },
        {
            "name": "Banana",
            "price": 5,
            "quantity": 12
        },
        {
            "name": "Pear",
            "price": 7,
            "quantity": 6
        }
    ],
    "message": "Fruit's List"
}
```

Los datos serán mostrados en orden alfabético.

<div id="Método GET con Filtro"><br></div>
### Método GET: Filtro por nombre

Podemos buscar un dato en específico, para ello crearemos una nueva función.

Para este ejemplo buscaremos las frutas por `name`.

En este caso la función se llamará `getFruit`, igual que la anterior pero en singular, ya que expresa que solo se desea obtener la información de una sola fruta. Así mismo, es método *GET*.

En el *endpoint* agregaré `<string:fruit_name>` que será un indicador de que le pasaremos el nombre de una de las frutas. La función también recibirá el mismo parámetro y con ello podremos saber qué hacer internamente.

Primero buscaremos la fruta que coincida con el nombre. Implementé una lista por comprensión, la cual almacenará todas las coincidencias con el nombre de la fruta solicitada y para una mayor precisión, agregué que se compararan en letras minúsculas:

```python
@app.route('/fruits/<string:fruit_name>')
def getFruit(fruit_name):
    fruit = [
        fruit for fruit in fruits_db
        if fruit['name'].lower() == fruit_name.lower()
    ]
    ...
```

Ahora tendremos que verificar si se encontró al menos una coincidencia, si fue así, tomaremos solo la primera y si no, se devolverá el mensaje *'Fruit not found'*:

```python
    ...
    if fruit:
        fruit = fruit[0]
        return jsonify({
            'fruit': fruit
        })
    else:
        return jsonify({
            'message': "Fruit not found"
        })
```

Si miramos el *endpoint* en busca de `apple` por ejemplo, `http://localhost:5000/fruits/apple` veremos:

```json
{
    "fruit": {
        "name": "Apple",
        "price": 10,
        "quantity": 7
    }
}
```

Y si no se encontrara la fruta, por ejemplo `http://localhost:5000/fruits/peach` entonces nos mostrará:

```json
{
    "message": "Fruit not found"
}
```

La función completa quedaría finalmente así:

```python
@app.route('/fruits/<string:fruit_name>')
def getFruit(fruit_name):
    fruit = [
        fruit for fruit in fruits_db
        if fruit['name'].lower() == fruit_name.lower()
    ]
    if fruit:
        fruit = fruit[0]
        return jsonify({
            'fruit': fruit
        })
    else:
        return jsonify({
            'message': "Fruit not found"
        })
```

<div id="Método POST"><br></div>
### Método POST

Con este método podremos añadir una fruta a la base de datos.

Nombraré a la función como `setFruit` y en el `route`, como parámetros, tendrá el nombre del *endpoint* y el método `POST`.

Los datos enviados deberán ser de tipo *JSON* (*Content-Type: application/json*) y los recibiremos en el código mediante `request.json`.

Crearemos el nuevo registro con sus valores necesarios y buscaremos si este nuevo registro (por nombre) ya existe.

```python
@app.route('/fruits/', methods=['POST'])
def setFruit():
    new_fruit = {
        'name': request.json.get('name'),
        'price': request.json.get('price'),
        'quantity': request.json.get('quantity')
    }
    fruit = [
        fruit for fruit in fruits_db
        if fruit['name'].lower() == new_fruit['name'].lower()
    ]
    ...
```

Si se encontró al menos una coincidencia, se devolverá el mensaje 'Fruit Already Exists', si no, lo añadiremos a nuestra base de datos y lo mostraremos con el mensaje 'Added Successfully':

```python
    ...
    if not fruit:
        fruits_db.append(new_fruit)
        return jsonify({
            'message': 'Added Successfully'
        })
    return jsonify({
        'message': 'Fruit Already Exists'
    })
```

Si enviamos el siguiente **JSON** por `POST` a `http://localhost:5000/fruits/`:

```json
{
    "name": "Peach",
    "price": 6,
    "quantity": 3
}
```

La **API** nos responderá:

```json
{
    "message": "Added Successfully"
}
```

Ahora, si vamos por `GET` a `http://localhost:5000/fruits/peach` nos responderá correctamente, mostrándonos que ya existe la fruta en la base de datos:

```json
{
    "fruit": {
        "name": "Peach",
        "price": 6,
        "quantity": 3
    }
}
```

La función completa quedaría finalmente así:

```python
@app.route('/fruits/', methods=['POST'])
def setFruit():
    new_fruit = {
        'name': request.json.get('name'),
        'price': request.json.get('price'),
        'quantity': request.json.get('quantity')
    }
    fruit = [
        fruit for fruit in fruits_db
        if fruit['name'].lower() == new_fruit['name'].lower()
    ]
    if not fruit:
        fruits_db.append(new_fruit)
        return jsonify({
            'message': 'Added Successfully'
        })
    return jsonify({
        'message': 'Fruit Already Exists'
    })
```

<div id="Método PUT"><br></div>
### Método PUT

Este método nos permitirá indicar que queremos modificar un registro de la base de datos.

Nombraré a la función como `editFruit` y en el `route`, como parámetro, tendrá el nombre del *endpoint* y el método `PUT`.

Para este método indicaremos en el *endpoint* que registro queremos modificar, en este caso buscaremos una fruta por nombre con `fruit_name`.

```python
@app.route('/fruits/<string:fruit_name>', methods=['PUT'])
def editFruit(fruit_name):
    fruit = [
        fruit for fruit in fruits_db
        if fruit['name'].lower() == fruit_name.lower()
    ]
    ...
```

Si existe una o más coincidencias de frutas con el mismo nombre, solo tomaremos la primera y remplazaremos sus campos con los nuevos datos, si no hubo coincidencias, entonces diremos *'Fruit not found'*.

```python
    ...
    if fruit:
        fruit = fruit[0]
        fruit['name'] = request.json.get('name')
        fruit['price'] = request.json.get('price')
        fruit['quantity'] = request.json.get('quantity')
        return jsonify({
            'message': 'Fruit Modified'
        })
    return jsonify({
        'message': "Fruit not found"
    })
```

Si enviamos el siguiente **JSON** por `PUT` a `http://localhost:5000/fruits/peach`:

```json
{
    "name": "Peach",
    "price": 8,
    "quantity": 7
}
```

La **API** nos responderá:

```json
{
    "message": "Fruit Modified"
}
```

Ahora, si vamos por `GET` a `http://localhost:5000/fruits/peach` nos responderá con la fruta modificada:

```json
{
    "fruit": {
        "name": "Peach",
        "price": 8,
        "quantity": 7
    }
}
```

Finalmente, la función quedaría así:

```python
@app.route('/fruits/<string:fruit_name>', methods=['PUT'])
def editFruit(fruit_name):
    fruit = [
        fruit for fruit in fruits_db
        if fruit['name'].lower() == fruit_name.lower()
    ]
    if fruit:
        fruit = fruit[0]
        fruit['name'] = request.json.get('name')
        fruit['price'] = request.json.get('price')
        fruit['quantity'] = request.json.get('quantity')
        return jsonify({
            'message': 'Fruit Modified'
        })
    return jsonify({
        'message': "Fruit not found"
    })
```

<div><br></div>
### Método PATCH

Este método es muy similar al método PUT, la diferencia entre ellos es que PUT se utiliza para actualizar un registro completo, mientras que PATCH solo modificarán algunos campos en el registro.

Nombraré a la función como `updateFruit` y en el `route`, como parámetro, tendrá el nombre del *endpoint* y el método `PATCH`.

Este método será similar al anterior, la única diferencia es que modificará solo los campos indicados.

```python
@app.route('/fruits/<string:fruit_name>', methods=['PATCH'])
def updateFruit(fruit_name):
    fruit = [
        fruit for fruit in fruits_db
        if fruit['name'].lower() == fruit_name.lower()
    ]
    if fruit:
        fruit = fruit[0]
        if request.json.get('name'):
            fruit['name'] = request.json.get('name')
        if request.json.get('price'):
            fruit['price'] = request.json.get('price')
        if request.json.get('quantity'):
            fruit['quantity'] = request.json.get('quantity')
        return jsonify({
            'message': 'Fruit Modified'
        })
    return jsonify({
        'message': "Fruit not found"
    })
```

Si enviamos el siguiente **JSON** por `PATCH` a `http://localhost:5000/fruits/peach`:

```json
{
    "price": 12,
}
```

La **API** nos responderá:

```json
{
    "message": "Fruit Modified"
}
```

Ahora, si vamos por `GET` a `http://localhost:5000/fruits/peach` nos responderá con la fruta y su precio modificado:

```json
{
    "fruit": {
        "name": "Peach",
        "price": 12,
        "quantity": 7
    }
}
```

<div><br></div>
### Método DELETE

Este método indicará que queremos eliminar un registro.

Este método será similar al método `GET` con filtro por nombre, pero con la única diferencia de que si el registro fue encontrado sea removido de la base de datos.

```python
@app.route('/fruits/<string:fruit_name>', methods=['DELETE'])
def deleteFruit(fruit_name):
    fruit = [
        fruit for fruit in fruits_db
        if fruit['name'].lower() == fruit_name.lower()
    ]
    if fruit:
        fruit = fruit[0]
        fruits_db.remove(fruit)
        return jsonify({
            'message': "Fruit Deleted"
        })
    else:
        return jsonify({
            'message': "Fruit not found"
        })
```

Si enviamos una petición por el método `DELETE` a `http://localhost:5000/fruits/peach` la **API** nos responderá:

```json
{
    "message": "Fruit Deleted"
}
```

Ahora, si vamos por `GET` a `http://localhost:5000/fruits/peach` nos responderá con que la fruta no fue encontrada:

```json
{
    "message": "Fruit not found"
}
```

<div><br></div>
### Código completo

Finalmente, el código completo quedaría de la siguiente manera:

```python
from flask import Flask, jsonify, request

app = Flask(__name__)

fruits_db = [
    {'name': 'Apple',  'price': 10, 'quantity': 7},
    {'name': 'Banana', 'price': 5,  'quantity': 12},
    {'name': 'Pear',   'price': 7,  'quantity': 6}
]

@app.route('/fruits/')
def getFruits():
    return jsonify({
        'message': "Fruit's List",
        'fruits': fruits_db
    })

@app.route('/fruits/<string:fruit_name>')
def getFruit(fruit_name):
    fruit = [
        fruit for fruit in fruits_db
        if fruit['name'].lower() == fruit_name.lower()
    ]
    if fruit:
        fruit = fruit[0]
        return jsonify({
            'fruit': fruit
        })
    else:
        return jsonify({
            'message': "Fruit not found"
        })

@app.route('/fruits/', methods=['POST'])
def setFruit():
    new_fruit = {
        'name': request.json.get('name'),
        'price': request.json.get('price'),
        'quantity': request.json.get('quantity')
    }
    fruit = [
        fruit for fruit in fruits_db
        if fruit['name'].lower() == new_fruit['name'].lower()
    ]
    if not fruit:
        fruits_db.append(new_fruit)
        return jsonify({
            'message': 'Added Successfully'
        })
    return jsonify({
        'message': 'Fruit Already Exists'
    })

@app.route('/fruits/<string:fruit_name>', methods=['PUT'])
def editFruit(fruit_name):
    fruit = [
        fruit for fruit in fruits_db
        if fruit['name'].lower() == fruit_name.lower()
    ]
    if fruit:
        fruit = fruit[0]
        fruit['name'] = request.json.get('name')
        fruit['price'] = request.json.get('price')
        fruit['quantity'] = request.json.get('quantity')
        return jsonify({
            'message': 'Fruit Modified'
        })
    return jsonify({
        'message': "Fruit not found"
    })

@app.route('/fruits/<string:fruit_name>', methods=['PATCH'])
def updateFruit(fruit_name):
    fruit = [
        fruit for fruit in fruits_db
        if fruit['name'].lower() == fruit_name.lower()
    ]
    if fruit:
        fruit = fruit[0]
        if request.json.get('name'):
            fruit['name'] = request.json.get('name')
        if request.json.get('price'):
            fruit['price'] = request.json.get('price')
        if request.json.get('quantity'):
            fruit['quantity'] = request.json.get('quantity')
        return jsonify({
            'message': 'Fruit Modified'
        })
    return jsonify({
        'message': "Fruit not found"
    })

@app.route('/fruits/<string:fruit_name>', methods=['DELETE'])
def deleteFruit(fruit_name):
    fruit = [
        fruit for fruit in fruits_db
        if fruit['name'].lower() == fruit_name.lower()
    ]
    if fruit:
        fruit = fruit[0]
        fruits_db.remove(fruit)
        return jsonify({
            'message': "Fruit Deleted"
        })
    else:
        return jsonify({
            'message': "Fruit not found"
        })

if __name__ == '__main__':
    app.run(debug=True)
```

Este es un CRUD funcional en una API REST con Python y Flask.

Hoy en día es indispensable conocer como funcionan y se implementan las API REST para la consulta de datos, es tan común utilizarlas, que entender como funcionan siempre será necesario.

Espero que les haya gustado esta publicación. !Hasta la próxima!
