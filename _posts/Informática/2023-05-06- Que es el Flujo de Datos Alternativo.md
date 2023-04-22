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
