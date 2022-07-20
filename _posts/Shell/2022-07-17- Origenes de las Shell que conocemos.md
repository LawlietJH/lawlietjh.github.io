---
title: "Orígenes de las Shell que conocemos"
category: Shell
tags: Información Shell
date: 2022-07-17 21:00
published: true
---

<div id="Thompson"><br></div>
### La Primera Shell

El **Thompson shell** es el primer *shell de* <a href="/linux/Que-es-Unix">Unix</a> (*sh*), introducido en la primera versión de *Unix* en 1971, y fue escrito por **Ken Thompson**. Era un simple intérprete de comandos, no diseñado para secuencias de comandos, pero, sin embargo, introdujo varias funciones innovadoras. Presenta las características de la interfaz de línea de comandos y condujo al desarrollo de las *Shell* de *Unix* posteriores.

<div id="Bourne"><br></div>
### El Remplazo de la Thompson Shell: Bourne Shell

La **Bourne Shell** (el actual *sh*) incorporó características tales como control de procesos, redirección de entrada/salida, listado y lectura de ficheros, protección, comunicaciones y un lenguaje de órdenes para escribir programas por *lotes* o *Scripts*. Fue el intérprete usado en las primeras versiones de *Unix* y se convirtió en un estándar de facto.

Fue desarrollada por *Stephen Bourne*, de los Laboratorios Bell de AT&T. Vio la luz en *UNIX* Versión 7, distribuido a colegios y universidades y en el cual era el intérprete de comandos predeterminado. Sustituyó al *Thompson shell*, cuyo archivo ejecutable tenía el mismo nombre: `sh`. Todavía es un intérprete de comandos muy popular para entornos *Unix*.

Todos los sistemas de tipo *Unix* tienen al menos un intérprete compatible con el *Bourne shell*. Se encuentra dentro de la jerarquía de archivos de *Unix* en */bin/sh*. En algunos sistemas, tal como *BSD*, */bin/sh* es un *Bourne shell* o un equivalente, pero en otros sistemas, como muchas distribuciones de <a href="/linux/Que-es-GNU-Linux">Linux</a>, */bin/sh* es un enlace simbólico a un *Shell* compatible con más características (como *Bash*). *POSIX* especifica su *Shell* estándar como un subconjunto estricto del *Korn shell*.

<div id="Ksh"><br></div>
### KornShell: La Shell Basada en Bourne Shell

**KornShell** (*ksh*) fue desarrollado por *David Korn* en *AT&T* en los Laboratorios Bell en *1980* y divulgado en *USENIX* el 14 de julio de 1983. Su desarrollo inicial se basó en el código de *Bourne Shell*. Otros contribuidores fueron los desarrolladores de los Laboratorios Bell *Mike Veach* y *Pat Sullivan* quienes escribieron el modo de edición *Emacs* y *Vi* para la línea de comandos. Es compatible con versiones anteriores de *Bourne Shell* e incluye muchas características del intérprete *C Shell* inspiradas a petición de los usuarios de los Laboratorios Bell.

La principal ventaja de *ksh* sobre otros intérpretes de comandos tradicionales de *Unix*, es el uso como *lenguaje de programación*. Desde su concepción, se le agregaron gradualmente muchas capacidades.

<div id="Bash"><br></div>
### Bash: La Shell del Software Libre

**GNU Bash** o simplemente **Bash** (*Bourne-again shell*) es una popular interfaz de usuario de línea de comandos, específicamente un *Shell* de *Unix*; así como un *lenguaje de Scripting*. Fue originalmente escrito por *Brian Fox* para el sistema operativo <a href="/linux/Que-es-GNU">GNU</a>, y pretendía ser el reemplazo de *software libre* del *Bourne Shell*. Lanzado por primera vez en *1989*, se ha utilizado ampliamente como el intérprete de inicio de sesión (login) predeterminado para la mayoría de las distribuciones de <a href="/linux/Que-es-GNU-Linux">GNU/Linux</a>, y también de *Mac OS X* de Apple hasta la versión 10.15. Una versión también está disponible para Windows 10 y Android. También es el intérprete de órdenes de usuario predeterminado en Solaris 11.

Bash es un intérprete de órdenes que generalmente se ejecuta en una ventana de texto donde el usuario escribe órdenes en modo texto. Bash también puede leer y ejecutar órdenes desde un archivo, llamado guion o "script". Al igual que todos los intérpretes de Unix, es compatible con el agrupamiento de nombres de archivo (coincidencia de comodines), tuberías, sustitución de comandos, variables y estructuras de control para pruebas de condición e iteración. Las palabras reservadas, la sintaxis, las variables de ámbito dinámico y otras características básicas del lenguaje se copian de *sh*. Otras características, por ejemplo, el historial, se copian de *csh* y *ksh*. Es un intérprete de órdenes compatible con *POSIX*, pero con varias extensiones.

El nombre del intérprete es un acrónimo de 'Bourne-again shell' (intérprete de órdenes Bourne, de nuevo), un juego de palabras con el nombre del intérprete Bourne que reemplaza y la noción de "nacer de nuevo" (born-again).

Un agujero de seguridad en Bash que data de la *versión 1.03* (agosto de 1989), denominado *Shellshock*, fue descubierto a principios de septiembre de 2014 y recibió amplia atención de los medios. Rápidamente, provocó una serie de *ciberataques en Internet*. Los parches para corregir los errores se pusieron a disposición poco después de que se identificaron los errores.

<div id="Zsh"><br></div>
### Z Shell: Una Bash Mejorada

**Z shell** (o simplemente *zsh*) es un potente intérprete de comandos para sistemas operativos de tipo *Unix*, como por ejemplo los *BSD* o <a href="/linux/Que-es-GNU-Linux">GNU/Linux</a>. La primera versión fue escrita por *Paul Falstad* en *1990*, cuando era estudiante en la *Universidad de Princeton*.

Esta se diseñó para poder usarse interactivamente. Se le han incorporado muchas de las características principales de otras *Shells* de *Unix* como *Bash*, *ksh*, o *tcsh* y además posee características propias originales.
*macOS Catalina*, lanzada en *octubre de 2019*, adoptó a *Zsh* como la *Shell* predeterminada, remplazando a *Bash*.

El nombre zsh procede del profesor de Yale Zhong Shao, por entonces profesor asistente en la Universidad de Princeton. Falstad pensó que su nombre de inicio de sesión, "zsh", era un buen nombre para una shell.