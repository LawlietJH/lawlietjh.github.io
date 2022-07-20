---
title: "¿Qué es una Shell?"
category: Shell
tags: Información Shell
date: 2022-07-16 21:00
published: true
---

<div id="Shell"></div>
En informática, el **shell** (*intérprete de órdenes*​ o *intérprete de comandos*) es el programa informático que provee una interfaz de usuario para acceder a los servicios del sistema operativo.

Dependiendo del tipo de interfaz que empleen, los shells pueden ser:
* De líneas texto (<a href="#CLI">CLI</a>, Command-Line Interface).
* Gráficos (GUI, Graphical User Interface).
* De lenguaje natural (NUI, Natural User Interface).

Estos son necesarios para invocar o ejecutar los distintos programas disponibles en la computadora. Un ejemplo de ello en Windows es `PowerShell`, en <a href="/linux/Que-es-GNU-Linux">GNU/Linux</a> es <a href="Origenes-de-las-Shell-que-conocemos#Bash">Bash</a> y en MacOS es <a href="Origenes-de-las-Shell-que-conocemos#Zsh">Zsh</a> (también se puede utilizar en sistemas de GNU/Linux).

Ejemplo: Ejecución del comando `ls` en Bash para listar el contenido de un directorio.
```bash
root@deleon:~/category/shell# ls -l
```

Resultados:
```bash
❯ ls -l
-rw-r--r-- 1 deleon 197121    460 Jul 16 21:06 index.html
```

<div id="CLI"><br></div>
### ¿Qué es una Interfaz de línea de Comandos (CLI)?

La **interfaz de línea de comandos** (*command-line interface*) es un tipo de interfaz de usuario de computadora que permite a los usuarios dar instrucciones a algún programa informático o al sistema operativo por medio de una línea de texto simple. Debe notarse que los conceptos de *CLI*, *Shell* y *emulador de terminal* no son lo mismo, ya que *CLI* se refiere al paradigma, mientras que los otros son programas informáticos específicos, que usualmente en conjunto implementan la *CLI*. Sin embargo, los tres suelen usarse como sinónimos.

Las *CLI* pueden emplearse interactivamente, escribiendo instrucciones en alguna especie de entrada de texto, o pueden utilizarse de una forma mucho más automatizada (archivo *batch*), leyendo órdenes desde un archivo de scripts.

Este tipo de interfaz existe casi desde los comienzos de la computación, superada en antigüedad solo por las tarjetas perforadas y mecanismos similares. Existen para diversos programas y sistemas operativos, para diverso hardware, y con distinta funcionalidad.

Por ejemplo, las *CLI* son parte fundamental de los *shells* o *emuladores de terminal*. Aparecen en todas las interfaces de escritorio (**GNOME**, **KDE**, **Microsoft Windows**) como un método para ejecutar aplicaciones rápidamente. Aparecen como interfaz de lenguajes interpretados tales como **Java**, **Python**, **Ruby** o **Perl**. También se emplean en aplicaciones *cliente-servidor*, en gestores de bases de datos, en clientes **FTP**, etc. Las *CLI* son un elemento valioso en aplicaciones de ingeniería, tan importantes como **MATLAB** y **AutoCAD**.

La contraparte de *CLI* es la interfaz gráfica de usuario (*GUI*) que ofrece una estética mejorada y una mayor simplificación, a costa de un mayor consumo de recursos computacionales, y, en general, de una reducción de la funcionalidad alcanzable. Asimismo aparece el problema de poder existir una mayor vulnerabilidad dada su complejidad.

Estas son empleadas por muchos programadores y administradores de sistemas como herramienta primaria de trabajo, especialmente en sistemas operativos basados en Unix; en entornos científicos y de ingeniería, y un subconjunto más pequeño de usuarios domésticos avanzados.
