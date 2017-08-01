---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Conceptos básicos de Windows PowerShell"
ms.assetid: 6b3cbbc8-060c-4877-b00b-7300dbbe4e28
ms.openlocfilehash: f8a520f1fbe97737c7d0c2acab0129f88b5ed425
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2017
---
# <a name="windows-powershell-basics"></a>Conceptos básicos de Windows PowerShell
Las interfaces gráficas de usuario usan algunos conceptos básicos con los que la mayoría de los usuarios de equipos están familiarizados. Los usuarios confían en la sencillez de estas interfaces para realizar tareas. Los sistemas operativos presentan a los usuarios una representación gráfica de los elementos que se pueden examinar, generalmente menús desplegables para acceder a funcionalidades específicas y menús contextuales para acceder a la funcionalidades específicas del contexto.

Una interfaz de la línea de comandos (CLI), como Windows PowerShell, debe usar un enfoque diferente para exponer información, porque no tiene menús ni sistemas de gráficos para ayudar al usuario. Debe conocer los nombres de los comandos antes de usarlos. Aunque puede escribir comandos complejos que sean equivalentes a las características en un entorno de interfaz gráfica de usuario, debe familiarizarse con los comandos usados frecuentemente y parámetros de comando.

La mayoría de las CLI no tienen patrones que puedan ayudar al usuario a obtener información sobre la interfaz. Dados que las CLI eran los primeros shells del sistema operativo, muchos de los nombres de comando y nombres de parámetro se seleccionaban de manera arbitraria. Se solían elegir los nombres de comando concisos antes que los claros. Aunque los estándares de diseño de comandos y sistemas de ayuda estaban integrados en la mayoría de las CLI, generalmente se diseñaban para ofrecer compatibilidad con los comandos más antiguos, por lo que el conjunto de comandos todavía está definido por decisiones tomadas hace décadas.

Windows PowerShell se diseñó para aprovechar el conocimiento histórico que un usuario tenía de las CLI. En este capítulo, hablaremos de algunas herramientas y conceptos básicos que puede usar para aprender a usar Windows PowerShell rápidamente. Incluyen:

-   Uso de Get-Command

-   Uso de los comandos de Cmd.exe y UNIX

-   Uso de comandos External

-   Uso de Tab-Completion

-   Uso de Get-Help

