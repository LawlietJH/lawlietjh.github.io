---
title: "JWT: ¿Qué es y para qué sirve?"
category: Informática
tags: Informática Información JSON Tokens
date: 2023-10-28 21:00
show_words: 66
published: true
page_id: 31
---

{% assign _020 = site.posts | where: "page_id", 20 | first %}
{% assign _024 = site.posts | where: "page_id", 24 | first %}
{% assign _020_json             = _020.url %}
{% assign _024_codificacion_b64 = _024.url %}

## ¿Qué es JWT?

*JWT* o *JSON Web Token*, es un estándar abierto (***<a href="https://datatracker.ietf.org/doc/html/rfc7519" target="_blank">RFC 7519</a>***) que define una forma compacta y segura de transmitir información entre dos partes como un objeto **<a href="{{_020_json}}">JSON</a>**. Los *JWT* son comúnmente utilizados para la autenticación y la transmisión segura de información entre un cliente y un servidor. Consiste en tres partes: el encabezado, la carga útil y la firma, codificados en base64.

<div><br></div>
### Estructura de un JWT

Un *JWT* tiene la siguiente estructura: **header.payload.signature**

* **Header** (***Encabezado***): especifica el tipo del token (que es ***JWT***) y el algoritmo de firma utilizado, por ejemplo, ***HMAC SHA256*** o ***RSA***.

* **Payload** (***Carga útil***): contiene la información que deseas transmitir. Puede ser cualquier información en formato ***JSON***, como identificadores de usuario, roles, o cualquier otro dato relevante.

* **Signature** (***firma***): se crea a partir del encabezado, la carga útil y una clave secreta. La firma se utiliza para verificar la integridad del token y asegurarse de que no ha sido manipulado.

Una vez teniendo las 3 partes, cada una se codifica en **<a href="{{_024_codificacion_b64}}">base64</a>** y se concatenan con un *punto*.

<div><br></div>
### Creación de un JWT

**Header (Algorithm & Token Type)**
```json
{
  "alg": "HS256",
  "typ": "JWT"
}
```
Base64: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9`

<div><br></div>
**Payload (Data)**
```json
{
  "name": "John Doe",
  "iat": 1516239022
}
```
Base64: `eyJuYW1lIjoiSm9obiBEb2UiLCJpYXQiOjE1MTYyMzkwMjJ9`

<div><br></div>
**Verify Signature**
```python
HMACSHA256(
  base64UrlEncode(header) + "." + base64UrlEncode(payload),
  "your-256-bit-secret"
)
```
Base64: `hqWGSaFpvbrXkOWc6lrnffhNWR19W_S1YKFBx2arWBk`

<div><br></div>
**JWT** (***Encoded***):
```python
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJuYW1lIjoiSm9obiBEb2UiLCJpYXQiOjE1MTYyMzkwMjJ9.hqWGSaFpvbrXkOWc6lrnffhNWR19W_S1YKFBx2arWBk
```

<br>
Podemos ver más claramente el como funciona JWT en esta web: **<a href="https://jwt.io/" target="_blank">JWT.io</a>**

<div><br></div>
### Algoritmos de firma

El JWT puede utilizar varios algoritmos de firma para garantizar la integridad y autenticidad de los datos en el token. Los algoritmos de firma disponibles en JWT son especificados en el campo "alg" del encabezado del token (header). Algunos de los algoritmos comunes son:

1. **HMAC** (Hash-based Message Authentication Code):

    * **HS256**: Utiliza HMAC con SHA-256 como función hash.
    * **HS384**: Utiliza HMAC con SHA-384 como función hash.
    * **HS512**: Utiliza HMAC con SHA-512 como función hash.

2. **RSA** (Rivest-Shamir-Adleman):

    * **RS256**: Utiliza RSA con SHA-256 para la firma.
    * **RS384**: Utiliza RSA con SHA-384 para la firma.
    * **RS512**: Utiliza RSA con SHA-512 para la firma.

3. **ECDSA** (Elliptic Curve Digital Signature Algorithm):

    * **ES256**: Utiliza ECDSA con SHA-256 como función hash.
    * **ES384**: Utiliza ECDSA con SHA-384 como función hash.
    * **ES512**: Utiliza ECDSA con SHA-512 como función hash.

4. **Ninguno** (None): Este algoritmo permite que el token no esté firmado. No se recomienda a menos que tengas razones específicas para no firmar el token, ya que el token podría ser modificado por cualquiera en tránsito.

La elección del algoritmo depende de las necesidades de seguridad y de la infraestructura de la aplicación. En general, se recomienda utilizar algoritmos seguros como **RS256** o **ES256** en lugar de **HMAC** si la seguridad es una preocupación importante. Además, es importante proteger adecuadamente la clave secreta (en el caso de *HMAC*) o las claves privadas (en el caso de *RSA* o *ECDSA*) para evitar posibles vulnerabilidades.

La seguridad de **JWT** también depende de cómo se implementa y se almacenan las claves, y de cómo se manejan las fechas de vencimiento y revocación de los tokens. Por lo tanto, es importante seguir buenas prácticas de seguridad al trabajar con JWT.

En el **RFC 7518** que habla sobre **JSON Web Algorithms (JWA)**, podremos encontrar una lista completa de los tipos de algoritmos que podemos utilizar: <a href="https://datatracker.ietf.org/doc/html/rfc7518#section-3" target="_blank">3. Cryptographic Algorithms for Digital Signatures and MACs</a>

<div><br></div>
### ¿Qué son los Claims?

Los "claims" son declaraciones o afirmaciones que se incluyen en la carga útil (payload).

Son una parte fundamental de un JWT y se utilizan para transportar información sobre el usuario o la entidad a la que se refiere el token.

Son representados como pares clave-valor en formato *JSON* y proporcionan información adicional sobre el token. Hay tres tipos de claims en un JWT: claims registrados, claims públicos y claims privados.

1. **Claims Registrados** (*Registered Claims*): Estos son un conjunto de claims predefinidos cuyos nombres y significados están registrados en la especificación de JWT. Algunos de los claims registrados más comunes son:

    * `iss` (**Issuer**): Identifica al emisor del token.
    * `sub` (**Subject**): Identifica al sujeto del token, generalmente el ID del usuario.
    * `aud` (**Audience**): Especifica a quién va dirigido el token.
    * `exp` (**Expiration Time**): Indica la fecha y hora de vencimiento del token.
    * `nbf` (**Not Before**): Indica la fecha y hora a partir de la cual el token es válido.
    * `iat` (**Issued At**): Indica la fecha y hora en que se emitió el token.
    * `jti` (**JWT ID**): Proporciona un identificador único para el token.

2. **Claims Públicos** (*Public Claims*): Estos son claims personalizados que pueden ser definidos por el emisor y el receptor del token. Aunque no están registrados en la especificación JWT, se deben elegir nombres de manera que no entren en conflicto con los claims registrados.

    Por ejemplo, puedes incluir claims públicos como: name, user_id, role, email, u otros que sean relevantes para la aplicación.

3. **Claims Privados** (*Private Claims*): Son claims personalizados que son específicos de una aplicación o entidad en particular. Estos claims no deben entrar en conflicto con los *claims registrados* ni con los *claims públicos*. Para evitar colisiones, es común que los claims privados se nombren usando un *espacio de nombres* específico, como un *dominio inverso*, por ejemplo, **com.myweb.claims**.

Ejemplo de un JWT con claims:
```json
{
  "sub": "1234567890",
  "name": "John Doe",
  "exp": 1609459200,
  "email": "johndoe@example.com",
  "custom_claim": "some value"
}
```

Los claims se utilizan para transportar información sobre el usuario, roles, permisos y otros datos relevantes en un formato estructurado. Al validar un JWT, el servidor puede verificar la información contenida en los claims para tomar decisiones de autorización y autenticación. Es importante asegurarse de que la información contenida en los claims sea precisa y segura, y de proteger adecuadamente el JWT para evitar la manipulación, así mismo, evitar que los claims contengan datos sensibles como contraseñas, ya que al ir codificados en base64, es información fácilmente obtenible.

<div><br></div>
### Cómo funciona JWT

1. **Autenticación**: Un usuario inicia sesión proporcionando su nombre de usuario y contraseña. El servidor autentica las credenciales del usuario.

2. **Generación del JWT**: Una vez autenticado, el servidor crea un *JWT* que contiene información sobre el usuario, como su ID y rol. Se codifica en formato *JSON* y se firma con una clave secreta que solo el servidor conoce. Luego, el servidor envía el JWT al cliente.

3. **Almacenamiento del JWT**: El cliente puede almacenar el JWT en una *cookie*, en el almacenamiento local o en cualquier otro lugar seguro. El JWT es autónomo y lleva consigo la información necesaria para validar la autenticación.

4. **Uso del JWT**: Cuando el cliente realiza solicitudes al servidor, envía el JWT en el encabezado de autorización de la solicitud. El servidor verifica la firma del JWT y la integridad de la información. Si el JWT es válido, el servidor puede confiar en la información contenida en él.

5. **Autorización**: El servidor utiliza la información en el JWT para determinar qué acciones o recursos tiene permitido el usuario. Por ejemplo, puede verificar si el usuario tiene los permisos para darle acceso o restringirlo.

6. **Renovación**: JWT generalmente tienen una fecha de vencimiento (expiración) para mayor seguridad. Cuando un JWT está por vencer, el servidor puede emitir un nuevo JWT con una nueva fecha de vencimiento. Esto permite que el usuario permanezca autenticado sin tener que volver a iniciar sesión.

<div><br></div>
### Consideraciones de seguridad

* Se debe mantener la clave secreta segura y no se debe compartir con nadie. Si se compromete, los JWT pueden ser falsificados.

* No se debe almacenar información confidencial en la carga útil (payload) del JWT, ya que los usuarios pueden descifrarla al ser un base64.

* Configura adecuadamente las fechas de vencimiento y revocación para garantizar la seguridad.

* Utiliza HTTPS para proteger la transmisión de JWT entre el cliente y el servidor.

<br>
*JWT* es una forma eficaz y versátil de autenticación y autorización en aplicaciones web. Sin embargo, es importante implementarlo de manera segura y seguir las mejores prácticas para evitar vulnerabilidades.
