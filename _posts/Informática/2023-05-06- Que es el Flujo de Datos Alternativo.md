---
title: "¿Qué es el Flujo de Datos Alternativo (ADS)?"
category: Informática
tags: Información Windows CMD PowerShell
date: 2023-05-06 00:00
published: false
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

El *ADS* creado no aumentará el peso ni alterara el archivo original, estos flujos de datos alternativos coexisten con ellos pero siguen siendo externos, esto nos permite almacenar el contenido que sea en los *ADS* vinculados, pero no podremos pasarlos a otro dispositivo que no sea *NTFS*.

<div id="Archivos-ADS"><br></div>

## Archivos con flujos alternativos de datos

Esto solo funciona en una unidad con formato NTFS. Tiene sus limitaciones, es importante resaltar que estas capas ocultas de texto no son posibles de compartir al sacar el archivo del disco duro.
Estas capas no son más que flujos de datos que apuntan al mismo archivo.

<img class="general-img" src="/assets/Alternate%20Data%20Strams%20-%20ADS.png" width="360" align="right">

Desde Windows 2000, el sistema de archivos NTFS en Windows ha admitido flujos de datos alternativos, que le permiten almacenar datos "detrás" de un nombre de archivo con el uso de un nombre de flujo. No es detectable mientras se navega por el sistema de archivos, o en cualquier lugar dentro de Windows, solo se puede acceder a él con la "clave secreta", que en realidad es solo el nombre de la transmisión.

Puedes pensar en estas secuencias adicionales como compartimientos secretos o capas dentro del archivo al que solo se puede acceder si se conoce el "código secreto", que en este caso es solo el nombre de la secuencia. Esta no es una forma completamente segura de ocultar datos, como ilustraremos más adelante, pero es un truco divertido para conocer.

<div id="Archivos-y-Clusters"><br></div>

## Archivos y Clusters

Un archivo es una unidad de datos en el sistema de archivos a la que un usuario puede acceder y administrar. Un archivo debe tener un nombre único en su directorio. Consiste en una o más secuencias de bytes que contienen un conjunto de datos relacionados, más un conjunto de atributos (también llamados propiedades) que describen el archivo o los datos dentro del archivo. El tiempo de creación de un archivo es un ejemplo de un atributo de archivo.

Cuando se crea un archivo, se crea una secuencia predeterminada sin nombre para almacenar todos los datos escritos en el archivo mientras está abierto. También puede crear secuencias adicionales dentro del archivo. Estas secuencias adicionales se denominan secuencias alternativas. La figura anterior muestra un archivo con la secuencia predeterminada y dos secuencias alternativas.

Los atributos de archivo no se almacenan en las secuencias de datos con los datos del archivo, sino que se almacenan en otro lugar y son administrados por el sistema operativo.

Todos los datos del sistema de archivos, incluidos el código de arranque del sistema y los directorios, son almacenados por el sistema de archivos NTFS en archivos. Otros sistemas de archivos almacenan esta información en regiones de disco externas al sistema de archivos. Una ventaja de almacenar esta información en archivos es que Windows puede localizar, acceder y mantener la información fácilmente. Otras ventajas son que cada uno de estos archivos puede estar protegido por un descriptor de seguridad y, en el caso de daños parciales en el disco, pueden reubicarse rápidamente en una parte más segura del disco.

La unidad de almacenamiento fundamental de todos los sistemas de archivos compatibles es un clúster, que es un grupo de sectores. Esto permite que el sistema de archivos optimice la administración de los datos del disco independientemente del tamaño del sector del disco establecido por el controlador de disco de hardware. Si el disco a administrar es grande y grandes cantidades de datos se mueven y organizan en una sola operación, el administrador puede ajustar el tamaño del clúster para acomodar esto.

<div id="Crear-Archivo-con-ADS"><br></div>

## ¿Cómo Crear Un Archivo de texto Con Flujos Alternativos?

Primero creamos un Archivo.txt ya sea directamente o desde el CMD.

Para crear el archivo desde consola (CMD) vamos a la ventana de Ejecutar presionando las teclas Win+R, escribimos CMD y presionamos Enter para abrir la consola de comandos.

Una vez estando en la consola, vamos a la ruta donde queramos crear el Archivo.txt, por ejemplo, para ir al escritorio podríamos utilizar CD Desktop o si te encuentras en otra ruta puedes utilizar CD %UserProfile%\Desktop

Ahora, para crear un Archivo.txt utilizaremos el comando NotePad Nombre.txt puedes utilizar el nombre que sea.
También podemos crear directamente el Archivo.txt y su flujo alternativo con NotePad Nombre.txt:OtroNombre.

Al agregar ":" después del nombre del archivo y su extensión, dirá que no existe y que si deseamos crearlo, indicamos que sí y ya podremos escribir ahí.

Si abrimos de forma normal, no aparecerá nada de lo anterior escrito. Entonces podremos escribir de forma normal en el archivo y tener texto oculto del otro lado.

Pueden hacerse todas las capas que queramos, lo importante es que se llamen diferente, si el archivo tiene en el nombre un espacio, es importante colocarlo entre comillas para que funcione.
Utilizando el comando DIR podemos ver los archivos y carpetas que se encuentran en la ruta actual, en este caso en el escritorio, pero si utilizamos el comando DIR /R es posible ver las capas ocultas (flujos alternativos) del archivo, son todos los archivos con terminación :$DATA. Esta es una buena forma de esconder texto.

Todos los archivos existentes en Windows están conformados por texto plano, es posible crear capas ocultas de texto no solo en los archivos de Texto (.txt) sino, también con cualquier otro tipo de extensión. Para hacer esto solo basta con hacer lo mismo que ya hemos visto, pero en lugar de abrir un archivo .txt puede tener cualquier otra extensión y que sea existente el archivo. En el ejemplo se utiliza un archivo .zip ya existente, y se utiliza NotePad para acceder al Texto plano del archivo.
