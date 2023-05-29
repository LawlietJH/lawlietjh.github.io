---
title: "Principios SOLID"
category: Informática
tags: Informática, Python
date: 2023-05-20 00:00
published: true
page_id: 29
---

En esta publicación veremos y entenderemos con ejemplos sencillos y prácticos lo que es SOLID.

## ¿Qué es SOLID?

SOLID es un acrónimo que representa cinco principios básicos de la programación orientada a objetos y el diseño. Es importante resaltar que **se trata de principios, no de reglas**.

## Los 5 Principios S.O.L.I.D.
<img class="general-img" src="/assets/images/029/SOLID.png" align="center">

<div id="single-responsibility"><br></div>

### Single Responsibility

"Una clase debe tener solo una responsabilidad, es decir, debe tener solo una razón para cambiar."

Cada clase deberá tener una **Responsabilidad Única** y no deberá tener más responsabilidades que esa, de esta manera las clases se vuelven más fáciles de mantener, modificar y probar, lo que mejora la calidad del software y su capacidad para adaptarse a los cambios. Además, este principio ayuda a evitar la duplicación de código y reduce la complejidad del sistema en general.

#### Ejemplo de código **sin utilizar SOLID**

Supongamos que tenemos una clase llamada `Order` la cual tiene 3 métodos que sirven para manejar una orden. Podemos notar que agregar un objeto o mirar el precio total de estos pueden ser su responsabilidad, pero si observamos con detenimiento el método `pay` se encarga de una responsabilidad distinta a la de la orden, se necesitaría quizás un procesador de pagos para ello.

```python
class Order:

    def __init__(self):
        self.items = []
        self.quantities = []
        self.prices = []
        self.status = 'open'

    def add_item(self, name: str, quantity: int, price: float) -> None:
        # Agrega un objeto con la cantidad y precio en la orden.
        self.items.append(name)
        self.quantities.append(quantity)
        self.prices.append(price)

    def total_price(self) -> float:
        # Devuelve el precio total a pagar.
        total = 0
        for i in range(len(self.prices)):
            total += self.quantities[i] * self.prices[i]
        return total

    def pay(self, payment_type: str, security_code: str) -> None:
        # Genera el pago según la forma de pago, débito o crédito.
        if payment_type == 'debit':
            print("Processing debit payment type")
            print(f"Verifying security code: {security_code}")
            self.status = 'paid'
        elif payment_type == 'credit':
            print("Processing credit payment type")
            print(f"Verifying security code: {security_code}")
            self.status = 'paid'
        else:
            print(f"Unknown payment type: {payment_type}")

# Se crea la instancia de la orden con los items, sus cantidades y precios.
order = Order()
order.add_item('Teclado', 1, 50.0)
order.add_item('Memoria', 1, 150.0)
order.add_item('Cable USB', 2, 5.0)

# Imprime el precio total de la orden
print(order.total_price())

# Se define la forma de pago.
order.pay('debit', '0372846')
```

Resultados:
```
210.0
Processing debit payment type   
Verifying security code: 0372846
```

#### Ejemplo de código con **Single Responsibility**:

Creando en este caso una nueva clase llamada `PaymentProcessor` que tendrá la responsabilidad de los métodos de pago, no solo hace que el código sea más organizado, sino que nos permite incluso poder expandir la funcionalidad de forma más simple.

Aunque el resultado es el mismo para ambos ejemplos, podemos darnos cuenta de que el código ahora es más mantenible y escalable.

```python
# Ahora se tiene una clase que sólo manejará métodos de la orden
# y se separa el método de pago en otra clase llamada PaymentProcessor
class Order:

    def __init__(self):
        self.items = []
        self.quantities = []
        self.prices = []
        self.status = 'open'

    def add_item(self, name: str, quantity: int, price: float) -> None:
        self.items.append(name)
        self.quantities.append(quantity)
        self.prices.append(price)

    def total_price(self) -> float:
        total = 0
        for i in range(len(self.prices)):
            total += self.quantities[i] * self.prices[i]
        return total

# Clase PaymentProcessor con los métodos: pago con débito y pago a crédito.
class PaymentProcessor:

    @staticmethod
    def pay_debit(order: Order, security_code: str) -> None:
        print("Processing debit payment type")
        print(f"Verifying security code: {security_code}")
        order.status = 'paid'

    @staticmethod
    def pay_credit(order: Order, security_code: str) -> None:
        print("Processing credit payment type")
        print(f"Verifying security code: {security_code}")
        order.status = 'paid'

# Ahora se instancia la clase Order, y se agrega los items a comprar en la orden.
order = Order()
order.add_item('Teclado', 1, 50.0)
order.add_item('Memoria', 1, 150.0)
order.add_item('Cable USB', 2, 5.0)

# Imprime el precio total de la orden
print(order.total_price())

# Instancia la clase de procesador de pago y se llama al método pagar con débito
# pasando como argumento la orden y el código de seguridad de la tarjeta.
processor = PaymentProcessor()
processor.pay_debit(order, '0372846')
```

Resultados:
```
210.0
Processing debit payment type   
Verifying security code: 0372846
```

<div id="openclosed"><br></div>

### Open/Closed Principle

"Las entidades deberían estar abiertas para la extensión, pero cerradas para la modificación."

El principio de **Abierto/Cerrado** toma en cuenta que cuando se requiera agregar un nuevo comportamiento en un sistema existente, en lugar de modificar clases antiguas, se deben crear nuevas y utilizarlas mediante herencia y redefinición de los métodos de la clase padre o mediante inyectado de dependencias que implemente el mismo contrato. Esto evita que los objetos existentes cambien con frecuencia.

#### Ejemplo de código **sin utilizar SOLID**

Imaginemos que tuviéramos esta funcionalidad que se utiliza para comparar 2 números, pero se nos pide extenderla, agregando que también se pudieran comparar 3 números:

```python
class Numbers:
    @staticmethod
    def compare_two_numbers(a: int, b: int) -> int:
        bigger = b
        if a > bigger:
            return a
        return bigger
```

Lo más típico podría ser que se quiera hacer una refactorización de la siguiente manera:

```python
# "Refactorización"
# Agregando una extensión para validar ahora 3 números.
class Numbers:
    @staticmethod
    def compare_two_or_three_numbers(a: int, b: int, c: int = 0) -> int:
        bigger = b
        if a > bigger:
            bigger = a
        if c > bigger:
            bigger = c
        return bigger
```

Aunque no está mal, podría darse el caso en códigos muy grandes que, al modificar cosas ya existentes, afecte la funcionalidad completa y que altere las pruebas unitarias que ya se tenían.

Este principio nos recomienda intentar **extender la funcionalidad**, **sin modificar** lo ya existente. Aunque hay que recordar, que estos son **principios NO reglas**, por lo que no se exige que se haga en todo momento, habrá casos en los que sería imposible no modificar lo existente.

#### Ejemplo de código con **Open/Closed**

Tomando el primer ejemplo sin refactorizar, con solo agregarle una funcionalidad nueva, conseguimos extenderla sin necesitar modificar lo existente, en pocas palabras *mantuvimos la clase abierta para la extensión, pero cerrada para la modificación.*

```python
class Numbers:
    @staticmethod
    def compare_two_numbers(a: int, b: int) -> int:
        bigger = b
        if a > bigger:
            return a
        return bigger

    def compare_three_numbers(self, a: int, b: int, c: int) -> int:
        bigger = self.compare_two_numbers(a, b)
        bigger = self.compare_two_numbers(bigger, c)
        return bigger
```

<div id="liskov-substitution"><br></div>

### Liskov's Substitution

"Si parece un pato, hace cuac como un pato, pero necesita pilas...
probablemente tienes la abstracción incorrecta..."

La **Sustitución de Liskov** nos dice que si en alguna parte de nuestro código estamos utilizamos una clase y creamos clases hijas, esas clases hijas tienen que poder sustituir al padre y el código debe seguir funcionando exactamente de la misma forma.

La idea de este principio es que solo debemos crear clases padre que tengan todos los métodos que realmente sean necesarios a heredar y de esta manera hacer una abstracción correcta de lo que queremos, y para conseguirlo podemos también utilizar herencia múltiple para completar las necesidades de las clases hijas, siempre y cuando se utilicen todos los métodos de las clases padre.

#### Ejemplo de código **sin utilizar SOLID**

Un **niño** es una **persona**, pero un niño no tendrá *ine* o *tarjeta de crédito* y no podría *pagar con tarjeta*, por lo tanto, la clase `Child` que hereda de `Person` no utilizaría los atributos `ine` o `credit_card` y no debería poder utilizar el método `payment`. En estos casos lo típico que se haría, es pretender que esos atributos y métodos no existen o indicar que no se podrán utilizar, pero esto es una muy mala práctica.

Este caso nos muestra que tenemos una abstracción errónea de lo que realmente queremos conseguir, ya que hay cosas que realmente no se van a utilizar.

```python
class Person:
    def __init__(self, ine, name, last_name, credit_card):
        self.ine = ine
        self.name = name
        self.last_name = last_name
        self.credit_card = credit_card

    def payment(self):
        print(f"Payment with card {self.credit_card}")


class Child(Person):

    def init(self, name, last_name):
        super().__init__(None, name, last_name, None)

    def payment(self):
        raise RuntimeError("A child cannot pay")
```

#### Ejemplo de código con **Liskov's Substitution**

Ahora podemos ver que tenemos la abstracción correcta, cada clase hereda lo que realmente le corresponde.

```python
class Person:
    def __init__(self, name: str, last_name: str):
        self.name = name
        self.last_name = last_name


class Adult(Person):
    def __init__(self, name: str, last_name: str, ine: str, credit_card: str):
        super().__init__(name, last_name)
        self.ine = ine
        self.credit_card = credit_card

    def payment(self):
        print(f"Payment with card {self.credit_card}")


class Child(Person):

    def __init__(self, name: str, last_name: str, tutor: Adult):
        super().__init__(name, last_name)
        self.tutor = tutor

    def payment(self):
        self.tutor.payment()
```

<div id="interface-segregation"><br></div>

### Interface Segregation

"Un cliente no debería ser obligado a depender de métodos que no utiliza."

En la **Segregación de Interfaz** se nos indica que ninguna clase deberá depender de métodos que no serán utilizados, es decir, cuando creamos una nueva interfaz que definirá los comportamientos de una clase, debemos estar seguros de que se usen todos sus métodos; para que esto se cumpla, se recomienda tener varias interfaces pequeñas que cumplan con las funcionalidades necesarias.

Esto es muy similar al principio anterior, la diferencia es que se enfoca en la herencia de interfaces.

#### Ejemplo de código **sin utilizar SOLID**

Imaginemos que tenemos una interfaz, la cual indica la estructura que deberán tener las clases en donde se herede. Esta interfaz exigirá que se utilicen los métodos que contiene: `get_values`, `set_quantity` y `rewind`. Si uno de estos métodos falta, se nos indicará que habrá que crearlo.

Podemos ver el problema de este ejemplo muy claramente: un `Cassette` que hereda de `Products` puede utilizar la funcionalidad `rewind` pero, en el caso de un `CD` que hereda de `Products` no podrá utilizar la función `rewind`, ya que los CD no se pueden rebobinar, a diferencia de los casetes. Por lo tanto, esta es una abstracción incorrecta y nos arrojará un error.

```python
from abc import ABCMeta, abstractmethod

# Interfaces (Clases Abstractas):
class Products(metaclass=ABCMeta):

    @abstractmethod
    def get_values(self) -> dict:
        raise NotImplementedError

    @abstractmethod
    def set_quantity(self, quantity: int) -> None:
        raise NotImplementedError

    @abstractmethod
    def rewind(self) -> bool:
        raise NotImplementedError

# Clases:
class Cassette(Products):

    def __init__(self, name: str, quantity: int) -> None:
        self.name = name
        self.quantity = quantity

    def get_values(self) -> dict:
        return {'name': self.name, 'quantity': self.quantity}

    def set_quantity(self, quantity: int) -> None:
        self.quantity = quantity

    def rewind(self) -> bool:
        return True

class CD(Products):

    def __init__(self, name: str, quantity: int) -> None:
        self.name = name
        self.quantity = quantity

    def get_values(self) -> dict:
        return {'name': self.name, 'quantity': self.quantity}

    def set_quantity(self, quantity: int) -> None:
        self.quantity = quantity

# Instancias:
cassette = Cassette('Heavy Metal', 2)
print(cassette.get_values())

cd = CD('Trash Metal', 4)
print(cd.get_values())
```

Resultados:
```
{'name': 'Heavy Metal', 'quantity': 2}
Traceback (most recent call last):
  File ".\Products.py", line 50, in <module>
    cd = CD('Trash Metal', 4)
TypeError: Can't instantiate abstract class CD with abstract methods rewind
```

#### Ejemplo de código con **Interface Segregation**

Ahora, como podremos observar, a la interfaz `Actions` se le pasa el método `rewind`, de esta manera podemos heredar en `Cassette` a `Products` y `Actions`, y en `CD` podemos heredar solamente `Products` y cumplir con este principio.

```python
from abc import ABCMeta, abstractmethod

# Interfaces (Clases Abstractas):
class Products(metaclass=ABCMeta):

    @abstractmethod
    def get_values(self) -> dict:
        raise NotImplementedError

    @abstractmethod
    def set_quantity(self, quantity) -> None:
        raise NotImplementedError

class Actions(metaclass=ABCMeta):

    @abstractmethod
    def rewind(self) -> bool:
        raise NotImplementedError

# Clases:
class Cassette(Products, Actions):

    def __init__(self, name: str, quantity: int) -> None:
        self.name = name
        self.quantity = quantity

    def get_values(self) -> dict:
        return {'name': self.name, 'quantity': self.quantity}

    def set_quantity(self, quantity: int) -> None:
        self.quantity = quantity

    def rewind(self) -> bool:
        return True

class CD(Products):

    def __init__(self, name: str, quantity: int) -> None:
        self.name = name
        self.quantity = quantity

    def get_values(self) -> dict:
        return {'name': self.name, 'quantity': self.quantity}

    def set_quantity(self, quantity: int) -> None:
        self.quantity = quantity

# Instancias:
cassette = Cassette('Heavy Metal', 2)
print(cassette.get_values())

cd = CD('Trash Metal', 4)
print(cd.get_values())
```

Resultados:
```
{'name': 'Heavy Metal', 'quantity': 2}
{'name': 'Trash Metal', 'quantity': 4}
```

<div id="dependency-inversion"><br></div>

### Dependency Inversion

"Este principio recomienda el uso de inyección de dependencias."

El objetivo de la **Inversión de Dependencias** es desacoplar nuestro código de sus dependencias directas. Este principio dice que las capas de las clases superiores no deben de depender de las capas inferiores, sino que ambas dependen de abstracciones.

#### Ejemplo de código **sin utilizar SOLID**

Podremos ver que tenemos una *canasta de compras*, y al querer pagar las compras, se busca guardar la información en una base de datos y luego pagar.

Esta implementación dará problemas al hacer **Pruebas Unitarias**, ya que tenemos dependencias en la función para comprar.

```python
class Shopping:
    ...

# Persistencia
class MongoDatabase:
    def save(self, shopping: Shopping): ...

# Método de Pago
class CreditCard:
    def pay(self, shopping: Shopping): ...

# Canasta de Compras:
class ShoppingBasket:
    def buy(self, shopping: Shopping):
        db = MongoDatabase()
        credit_card = CreditCard()
        db.save(shopping)
        credit_card.pay(shopping)

# Instancias:
shopping = Shopping()

# Ejecución:
shopping_basket = ShoppingBasket()
shopping_basket.buy(shopping)
```

#### Ejemplo de código con **Dependency Inversion**

De esta manera podremos incluso tener distintas clases para *Persistencia* y distintas clases de *Métodos de Pago*, ya que al tener interfaces, obligamos a que se mantengan siempre los mismos métodos, de esta forma no importará la instancia que se mande, se utilizará de la misma manera.

En la implementación de las compras, al crear la instancia de `ShoppingBasket` se le enviarán todas las dependencias necesarias, y al mantener la misma estructura, los tipos de dependencias `Persistence` o `PaymentMethod`, internamente, se nos permite usarlo por igual, sin importar si por ejemplo `Persistance` es de tipo `MongoDatabase` o `MySQLDatabase` se podrá utilizar el método `save()` desde la instancia `self._persistance`.

Con esto, al aplicar la **inyección de dependencias**, ahora tendremos una implementación fácilmente testeable.

```python
from abc import ABCMeta, abstractmethod

class Shopping:
    ...

# Interfaces:
class Persistence(metaclass=ABCMeta):
    @abstractmethod
    def save(self, shopping: Shopping) -> None:
        raise NotImplementedError

class PaymentMethod(metaclass=ABCMeta):
    @abstractmethod
    def pay(self, shopping: Shopping) -> None:
        raise NotImplementedError

# Clases para Persistencia:
class MongoDatabase(Persistence):
    def save(self, shopping: Shopping): ...

class MySQLDatabase(Persistence):
    def save(self, shopping: Shopping): ...

# Clases para Métodos de Pago:
class CreditCard(PaymentMethod):
    def pay(self, shopping: Shopping): ...

class Paypal(PaymentMethod):
    def pay(self, shopping: Shopping): ...

# Canasta de Compras:
class ShoppingBasket:

    def __init__(self, persistance: Persistence,
                 payment_method: PaymentMethod) -> None:
        self._persistance = persistance
        self._payment_method = payment_method

    def buy(self, shopping: Shopping) -> None:
        self._persistance.save(shopping)
        self._payment_method.pay(shopping)

# Instancias:
shopping = Shopping()

# Persistencia
mongo_db = MongoDatabase()
mysql_db = MySQLDatabase()

# Métodos de Pago
credit_card = CreditCard()
paypal = Paypal()

# Ejecución:
shopping_basket_1 = ShoppingBasket(mongo_db, paypal)
shopping_basket_1.buy(shopping)

shopping_basket_2 = ShoppingBasket(mysql_db, credit_card)
shopping_basket_2.buy(shopping)
```

## Conclusión:

Los principios SOLID nos ayudan a tener un código muy limpio y escalable. En ellos, **Single Responsibility** se enfoca en las responsabilidades separadas, **Open/Closed** se basa en la extensión en lugar de la modificación, **Liskov's Sustitution** en tener herencias donde todos los métodos sean utilizados, **Interface Segregation** en tener interfaces donde se utilicen todos los métodos necesarios y no más que eso, y finalmente, **Dependency Inversion** en el cúal se contempla la *inyección de dependencias*.

Como ven, todos los principios son muy buenos, siempre van de la mano, complementándose y reforzándose. Combinando todos ellos podremos obtener un **código de calidad**.
