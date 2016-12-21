---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Usar nombres de comando conocidos
ms.technology: powershell
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: c71df3c8e973f58bab76a5b99142f6c61ca652b2
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="using-familiar-command-names"></a>Usar nombres de comando conocidos
Mediante un mecanismo denominado *alias*, Windows PowerShell permite a los usuarios hacer referencia a los comandos con nombres alternativos. El aliasing permite a los usuarios con experiencia en otros shells reutilizar los nombres de comandos comunes que ya conocen para realizar operaciones similares en Windows PowerShell. Aunque no trataremos en detalle los alias de Windows PowerShell, puede usarlos para empezar a trabajar con Windows PowerShell.

El aliasing asocia un nombre de comando que escribe a otro comando. Por ejemplo, Windows PowerShell tiene una función interna denominada **Clear-Host** que borra la ventana de salida. Si escribe el comando **cls** o **clear** en un símbolo del sistema, Windows PowerShell interpreta que se trata de un alias de la función **Clear-Host** y ejecuta la función **Clear-Host**.

Esta característica ayuda a los usuarios a aprender a usar Windows PowerShell. En primer lugar, la mayoría de los usuarios de Cmd.exe y UNIX tienen una gran repertorio de comandos que los usuarios que ya conocen por su nombre y, aunque los equivalentes de Windows PowerShell podrían no producir resultados idénticos, son lo suficientemente parecidos para que los usuarios pueden usarlos en su trabajo sin tener que memorizar primero los nombres de Windows PowerShell. En segundo lugar, la principal fuente de frustración a la hora de aprender un nuevo shell cuando el usuario ya está familiarizado con otro, son los errores provocados por la "memoria digital". Si hace años que usa Cmd.exe y tiene una pantalla repleta de salida que quiere limpiar, escribiría de manera reflexiva el comando **cls** y presionaría la tecla ENTRAR. Sin el alias de la función **Clear-Host** de Windows PowerShell, obtendría un mensaje de error similar a "**'cls' no se reconoce como cmdlet, función, programa ejecutable o archivo de script**" y se quedaría sin saber qué debe hacer para borrar la salida.

La siguiente es una lista breve de comandos de Cmd.exe y UNIX comunes que puede usar en Windows PowerShell:

|||||
|-|-|-|-|
|cat|dir|montar|rm|
|cd|echo|move|rmdir|
|chdir|erase|popd|sleep|
|clear|h|ps|sort|
|cls|history|pushd|tee|
|copy|kill|pwd|tipo|
|del|lp|r|write|
|diff|ls|ren||

Si usa uno de estos comandos de forma reflexiva y desea obtener el nombre real del comando nativo de Windows PowerShell, puede usar el comando **Get-Alias**:

```
PS> Get-Alias cls

CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

Para que los ejemplos sean más legibles, la Guía de usuario de Windows PowerShell suele evitar el uso de alias. Sin embargo, saber más sobre los alias con antelación puede resultarle útil si trabaja con fragmentos de código arbitrarios de código de Windows PowerShell de otro origen o desea definir sus propios alias. En el resto de esta sección se tratarán los alias estándar y cómo definir sus propios alias.

### <a name="interpreting-standard-aliases"></a>Interpretar los alias estándar
A diferencia de los alias descritos anteriormente, que se diseñaron para ofrecer compatibilidad con los nombres de otras interfaces, los alias integrados en Windows PowerShell están diseñados generalmente para ofrecer brevedad. Estos nombres más cortos pueden escribirse rápidamente, pero son imposibles de leer si no sabe a qué hacen referencia.

Windows PowerShell intenta compensar la claridad y la brevedad proporcionando un conjunto de alias estándar que se basan en nombres abreviados para nombres y verbos comunes. Esto permite un conjunto principal de alias para cmdlets comunes que son legibles si se conocen los nombres abreviados. Por ejemplo, en los alias estándar, el verbo **Get** se abrevia a **g**, el verbo **et** se abrevia a **s**, el nombre **Item** se abrevia a **i**, el nombre **Location** se abrevia a **l** y el nombre Command se abrevia a **cm**.

Este es un breve ejemplo para ilustrar cómo funciona. El alias estándar de Get-Item procede de la combinación de **g** de Get e **i** de Item: **gi**. El alias estándar de Set-Item procede de la combinación de **s** de Set e **i** de Item: **si**. El alias estándar de Get-Location procede de la combinación de **g** de Get y **l** de Location: **gl**. El alias estándar de Set-Location procede de la combinación de **s** de Set y **l** de Location: **sl**. El alias estándar de Get-Command procede de la combinación de **g** de Get y **cm** de Command: **gcm**. No existe un cmdlet Set-Command, pero si lo hubiera, podríamos adivinar que el alias estándar proviene de **s** de Set y **cm** de Command: **scm**. Además, las personas que conozcan los alias de Windows PowerShell que se encuentren **scm** podrán adivinar que el alias hace referencia a Set-Command.

### <a name="creating-new-aliases"></a>Crear nuevos alias
Puede crear sus propios alias mediante el cmdlet Set-Alias. Por ejemplo, las siguientes instrucciones crean los alias de cmdlet estándar que se describen en Interpretar los alias estándar:

```
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

Internamente, Windows PowerShell usa estos comandos durante el inicio, pero estos alias no se pueden cambiar. Si intenta ejecutar realmente uno de estos comandos, obtendrá un error que indicará que no se puede modificar el alias. Por ejemplo:

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```

