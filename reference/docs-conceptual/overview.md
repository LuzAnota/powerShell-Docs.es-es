---
ms.date: 08/27/2018
keywords: powershell, cmdlet
title: Scripting de PowerShell
ms.openlocfilehash: 07925ce8dcafd33970a703c9b241bf6f76f88d10
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402897"
---
# <a name="powershell"></a>PowerShell

PowerShell es un shell (interfaz de usuario) de línea de comandos y un lenguaje de scripting basado en tareas integrado en .NET.
PowerShell ayuda a los administradores de sistemas y a los usuarios avanzados a automatizar rápidamente las tareas que administran sistemas operativos (Linux, macOS y Windows) y procesos.

Los comandos de PowerShell permiten administrar los equipos desde la línea de comandos. Los proveedores de PowerShell permiten obtener acceso a almacenes de datos, como el Registro y el almacén de certificados, con la misma simplicidad con que se obtiene acceso al sistema de archivos. PowerShell incluye un analizador de expresiones muy completo y un lenguaje de scripting totalmente desarrollado.

## <a name="powershell-is-open-source"></a>PowerShell es de código abierto

El código fuente base de PowerShell ahora está disponible en GitHub y admite las contribuciones de la comunidad.
Vea el [código de PowerShell en GitHub](https://github.com/powershell/powershell).

Puede empezar con los fragmentos que necesita en [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell) (Obtener PowerShell).
O, si lo prefiere, con el paseo introductorio incluido en esta [introducción](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).

## <a name="powershell-design-goals"></a>Objetivos de diseño de PowerShell

PowerShell está diseñado para mejorar el entorno de scripting y línea de comandos mediante la eliminación de antiguos problemas y la adición de nuevas características.

### <a name="discoverability"></a>Detectabilidad

PowerShell facilita la detección de sus características. Por ejemplo, para buscar una lista de cmdlets con la finalidad de ver y cambiar los servicios de Windows, escriba:

```powershell
Get-Command *-Service
```

Tras detectar qué cmdlet lleva a cabo una tarea, si desea obtener más información sobre él, utilice el cmdlet `Get-Help`. Por ejemplo, para mostrar ayuda acerca del cmdlet `Get-Service`, escriba:

```powershell
Get-Help Get-Service
```

La mayoría de los cmdlets devuelven objetos que se pueden manipular y después representarse como texto para mostrar. Para conocer a la perfección la salida de un cmdlet, canalice la salida al cmdlet `Get-Member`. Por ejemplo, el siguiente comando muestra información acerca de los miembros de la salida del objeto mediante el cmdlet `Get-Service`.

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>Consistency

La administración de sistemas puede ser una tarea compleja. Las herramientas que tienen una interfaz coherente ayudan a controlar esa complejidad inherente. Lamentablemente, ni las herramientas de línea de comandos ni los objetos COM que permiten ejecutar scripts son famosos por su coherencia.

La coherencia de PowerShell es uno de sus activos principales. Por ejemplo, si aprende a usar el cmdlet `Sort-Object`, podrá usar dicho conocimiento para ordenar la salida de cualquier cmdlet. No es necesario obtener información sobre las distintas rutinas de ordenación de cada cmdlet.

Además, los desarrolladores de cmdlets no tienen que diseñar características de ordenación para sus cmdlets. PowerShell proporciona una plataforma con las características básicas que aplican la coherencia. La plataforma elimina algunas opciones que quedan para el desarrollador. Pero, a cambio, hace que el desarrollo de los cmdlets sea mucho más sencillo.

### <a name="interactive-and-scripting-environments"></a>Entornos interactivo y de scripting

El símbolo del sistema de Windows proporciona un shell interactivo con acceso a herramientas de línea de comandos y scripting básico. Windows Script Host (WSH) tiene herramientas de línea de comandos que permiten ejecutar scripts y objetos de automatización COM, pero no proporciona un shell interactivo.

PowerShell combina un shell interactivo y un entorno de scripting. PowerShell puede acceder a las herramientas de línea de comandos, objetos COM y bibliotecas de clases .NET. Esta combinación de características amplía las funcionalidades del usuario interactivo, el escritor de scripts y el administrador del sistema.

### <a name="object-orientation"></a>Orientación a objetos

PowerShell se basa en el objeto, no en el texto. La salida de un comando es un objeto. Puede enviar el objeto de salida a otro comando como entrada, a través de una canalización.

Esta canalización proporciona una interfaz familiar para las personas que tienen experiencia con otros shells. PowerShell extiende este concepto mediante el envío de objetos en lugar de texto.

### <a name="easy-transition-to-scripting"></a>Transición sencilla al scripting

La detectabilidad de comandos de PowerShell facilita la transición de la escritura interactiva de comandos a la creación y ejecución de scripts. Las transcripciones y el historial de PowerShell facilitan la copia de comandos a un archivo para su uso como script.
