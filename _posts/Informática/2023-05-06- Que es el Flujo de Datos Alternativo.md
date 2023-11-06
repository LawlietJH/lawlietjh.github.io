---
title: ¿Qué es el Flujo de Datos Alternativo (ADS)?
category: Informática
tags: Información Windows CMD PowerShell
date: 2023-05-06 21:00
show_words: 44
published: true
page_id: 28
---

Los **Flujos Alternativos de Datos**, *Alternate Data Streams* o ***ADS*** son una característica del sistema de archivos *NTFS* que permite almacenar metainformación con un fichero, sin necesidad de usar un fichero separado para almacenarla.

Es posible ver los *ADS* en Windows con los comandos:

CMD: `dir /r`

PowerShell: `Get-Item .\file.etc -Stream *`

También es posible crear uno (con notepad) o abrirlo y mirar su contenido con los siguientes comandos:

CMD: `notepad "file.etc:stream_name"`

Ejemplo: `notepad "master.zip:Zone.Identifier"`

PowerShell: `Get-Content .\file.etc -Stream Zone.Identifier`

También deben saber que los *ADS* solo existirán en un Disco con formato *NTFS*.

El *ADS* creado no aumentará el peso ni alterara el archivo original, estos **flujos de datos alternativos** coexisten con ellos pero siguen siendo externos, esto nos permite almacenar el contenido que sea en los *ADS* vinculados, pero no podremos pasarlos a otro dispositivo que no sea *NTFS*.

<div id="Archivos-ADS"></div>

## Archivos con flujos alternativos de datos

Esto solo funciona en una unidad con formato **NTFS**. Tiene sus limitaciones, es importante resaltar que estas capas ocultas de texto no son posibles de compartir al sacar el archivo del disco duro. Estas capas no son más que flujos de datos que apuntan al mismo archivo.

<img class="general-img" src="/assets/images/028/alternate_data_streams_ADS.png" width="300" align="right">
Desde Windows 2000, el sistema de archivos **NTFS** en Windows ha admitido **flujos de datos alternativos**, que le permiten almacenar datos *"detrás"* de un nombre de archivo con el uso de un nombre de flujo. No es detectable mientras se navega por el sistema de archivos, o en cualquier lugar dentro de Windows, solo se puede acceder a él con la **"clave secreta"**, que en realidad es solo el nombre de la transmisión.

Puedes pensar en estas secuencias adicionales como compartimientos secretos o capas dentro del archivo al que solo se puede acceder si se conoce el **"código secreto"**, que en este caso es solo el nombre de la secuencia. Esta no es una forma completamente segura de ocultar datos, como ilustraremos más adelante, pero es un truco divertido para conocer.

<div id="Archivos-y-Clusters"></div>

### Archivos y Clusters

Un archivo es una unidad de datos en el sistema de archivos a la que un usuario puede acceder y administrar. Un archivo debe tener un nombre único en su directorio.
Consiste en una o más **secuencias de bytes** que contienen un conjunto de datos relacionados, más un conjunto de atributos (también llamados propiedades) que describen el archivo o los datos dentro del archivo. El tiempo de creación de un archivo es un ejemplo de un atributo de archivo.

Cuando se crea un archivo, se crea una secuencia predeterminada sin nombre para almacenar todos los datos escritos en el archivo mientras está abierto.
También puede crear secuencias adicionales dentro del archivo. Estas secuencias adicionales se denominan **secuencias alternativas**.

Los atributos de archivo no se almacenan en las secuencias de datos con los datos del archivo, sino que se almacenan en otro lugar y son administrados por el sistema operativo.

Todos los datos del sistema de archivos, incluidos el código de arranque del sistema y los directorios, son almacenados por el sistema de archivos **NTFS** en archivos. Otros sistemas de archivos almacenan esta información en regiones de disco externas al sistema de archivos.
Una ventaja de almacenar esta información en archivos es que Windows puede localizar, acceder y mantener la información fácilmente. Otras ventajas son que cada uno de estos archivos puede estar protegido por un descriptor de seguridad y, en el caso de daños parciales en el disco, pueden reubicarse rápidamente en una parte más segura del disco.

La unidad de almacenamiento fundamental de todos los sistemas de archivos compatibles es un clúster, que es un **grupo de sectores**.
Esto permite que el sistema de archivos optimice la administración de los datos del disco independientemente del tamaño del sector del disco establecido por el controlador de disco de hardware. Si el disco a administrar es grande y grandes cantidades de datos se mueven y organizan en una sola operación, el administrador puede ajustar el tamaño del clúster para acomodar esto.

<div id="Crear-Archivo-con-ADS"></div>

## ¿Cómo Crear Un Archivo de texto Con Flujos Alternativos?

Probemos con un archivo de texto.

Podemos crear o acceder a un flujo de datos alternativo utilizando el notepado de la siguient emanera: `notepad file.txt:ads_name`.
Podemos crear tantos como queramos y acceder a ellos utilizando el nombre asignado al *ADS*.

<img class="general-img" src="/assets/images/028/hidden_section.png" width="240" align="right">
Si abrimos de forma normal, no aparecerá nada de lo anterior escrito. Entonces podremos escribir de forma normal en el archivo y tener algún texto oculto en distintos flujos.
Pueden hacerse tantas capas como queramos, lo importante es que se llamen diferente.

<img class="general-img" src="/assets/images/028/command_dir-r.png" width="270" align="right">
Si el archivo tiene un espacio en el nombre es importante colocarlo entre comillas para que funcione.
Utilizando el comando `dir` podemos ver los archivos y carpetas que se encuentran en la ruta actual,
pero si utilizamos el comando `dir /r` es posible ver los flujos alternativos del archivo, estos serám todos los archivos con terminación **:$DATA**.

Todos los archivos existentes en Windows están conformados por binarios que pueden verse en texto plano, y es posible crearles capas ocultas. Para hacer esto solo basta con hacer lo mismo que ya hemos visto, pero en lugar de abrir un archivo `.txt` puede ser cualquier archivo con otra extensión.
