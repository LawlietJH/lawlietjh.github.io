---
title: "¿Qué es una Memoria Caché?"
category: Informática
tags: Informática
date: 2023-04-22 00:00
published: true
page_id: 26
---

{% for post in site.posts %}
<!-- {{ post.page_id }} - {{ post.url }} -->
{% endfor %}

La **memoria caché** es un **búfer** especial de memoria que poseen las computadoras, que funciona de manera semejante a la memoria principal, pero es de menor tamaño y de acceso más rápido. Nace cuando las memorias ya no eran capaces de acompañar a la velocidad del procesador, por lo que se puede decir que es una memoria auxiliar, que posee una gran velocidad y eficiencia y es usada por el microprocesador para reducir el tiempo de acceso a datos ubicados en la memoria principal que se utilizan con más frecuencia.

La caché es una memoria que se sitúa entre la **unidad central de procesamiento** (**CPU**) y la **memoria de acceso aleatorio** (**RAM**) para acelerar el intercambio de datos.

Cuando se accede por primera vez a un dato, se hace una copia en la caché; los accesos siguientes se realizan a dicha copia, haciendo que sea menor el tiempo de acceso medio al dato. Cuando el microprocesador necesita leer o escribir en una ubicación en memoria principal, primero verifica si una copia de los datos está en la caché; si es así, el microprocesador de inmediato lee o escribe en la memoria caché, que es mucho más rápido que de la lectura o la escritura a la memoria principal.

De forma similar, cuando hablamos de **caché software** hablamos de un **espacio de memoria** que contiene los datos calculados o copiados desde un espacio más lento. Un ejemplo habitual es hablar de la caché del navegador web, este espacio en disco contiene la información temporal descargada desde Internet o red interna, que, por la naturaleza del sistema, siempre tendrá una velocidad más lenta que el disco físico de la máquina.

Es un componente de hardware o software que guarda datos para que las solicitudes futuras de esos datos se puedan atender con mayor rapidez; los datos almacenados en un caché pueden ser el resultado de un cálculo anterior o el duplicado de datos almacenados en otro lugar, generalmente, da velocidad de acceso más rápido. Se produce un acierto de caché cuando los datos solicitados se pueden encontrar en esta, mientras que un fallo de caché ocurre cuando no están dichos datos. La lectura de la caché es más rápida que volver a calcular un resultado o leer desde un almacén de datos más lento; por lo tanto, cuantas más solicitudes se puedan atender desde la memoria caché, más rápido funcionará el sistema.

Cuando hablamos de una caché de memoria nos referimos a la memoria de acceso rápido de una unidad central de procesamiento (CPU), que guarda temporalmente los datos recientes de los procesados (información).

Hay tres tipos de caché frecuentemente usados en computadoras personales: caché de disco, caché de pista y caché web.

* **Caché de disco**: Es una porción de memoria RAM asociada a un disco, con el fin de almacenar datos recientemente leídos y agilizar su carga en dado caso que sean solicitados otra vez. Puede mejorar notablemente el rendimiento de las aplicaciones, dado que acceder a un byte de datos en RAM puede ser miles de veces más rápido que acceder a un byte del disco duro.

* **Caché de pista**: Es una memoria de estado sólido tipo RAM cuyo uso de esta clase de discos generalmente se limita a las supercomputadoras por su costo tan elevado.

* **Caché web**: Es la encargada de almacenar documentos web para reducir el ancho de banda consumido, la carga de los servidores y el retraso de las descargas. Existen 3 tipos de caché web: Privados que solo funcionan para un usuario, Compartidos sirven páginas a varios usuarios y Pasarela que funcionan a cargo del propio servidor original, de forma que los clientes no distinguen unos de otros.
 
Existe una relación inherente entre el tamaño y la velocidad; dado que un recurso más grande implica mayores distancias físicas, pero también una compensación entre tecnologías costosas (como SRAM) versus productos más baratos, fácilmente producidos en masa (como DRAM o discos duros).

El almacenamiento en búfer proporcionado por un caché beneficia tanto el ancho de banda como la latencia:

* **Latencia**: Un recurso más grande incurre en una latencia significativa para el acceso, por ejemplo, puede tomar cientos de ciclos de reloj para que un procesador moderno de 4 GHz llegue a tener disponible los datos de una DRAM. Esto se mitiga leyendo en grandes fragmentos y almacenando los datos temporalmente en una memoria más rápida o cercana al procesador, con la esperanza de que las lecturas posteriores sean más rápidas. La predicción o la obtención previa explícita (en inglés prefetching) también pueden adivinar de dónde vendrán las lecturas futuras y realizar las solicitudes con anticipación; si se hace correctamente, la latencia se reduce a ser casi despreciable.

* **Ancho de Banda**: El uso de un caché también permite un mayor rendimiento (en inglés se usa el término throughput) del recurso subyacente, mediante el empaquetado de múltiples transferencias de pequeñas en solicitudes más grandes y más eficientes. En el caso de DRAM, esto podría servirse por un bus más ancho. Imagínese un programa escaneando bytes en un espacio de direcciones de 32 bits, pero atendido por un bus de datos de 128 bits fuera de chip; los accesos de byte individuales sin caché solo permitirían usar 1/16 del ancho de banda total, y el 80% del movimiento de datos serían direcciones. Leer trozos más grandes reduce la fracción de ancho de banda requerida para transmitir información de dirección.

Etimológicamente la palabra procede del inglés cache (escondite secreto para guardar mercancías, habitualmente de contrabando), y esta a su vez del francés cache, (escondido u oculto).
