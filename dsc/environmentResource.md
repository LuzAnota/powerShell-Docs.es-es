---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recursos de DSC Environment
ms.openlocfilehash: 9c166d719ba3f168c936278acd6fb5fb7658613e
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-environment-resource"></a>Recursos de DSC Environment

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

El recurso __Environment__ de la configuración de estado deseado (DSC) de PowerShell ofrece un mecanismo para administrar variables de entorno del sistema.

## <a name="syntax"></a>Sintaxis
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## <a name="properties"></a>Propiedades

|  Propiedad  |  Descripción   | 
|---|---| 
| Nombre| Indica el nombre de la variable de entorno para la que quiere garantizar un estado específico.| 
| Ensure| Indica si existe una variable. Establezca esta propiedad en __Present__ para crear la variable de entorno si no existe o para garantizar que su valor coincida con el que se proporciona mediante la propiedad __Value__ si la variable ya existe. Establézcala en __Absent__ para eliminar la variable si existe.| 
| Ruta| Define la variable de entorno que se está configurando. Establezca esta propiedad en __$true__ si la variable es la variable __Path__; de lo contrario, establézcala en __$false__. El valor predeterminado es __$false__. Si la variable que se está configurando es la variable __Path__, el valor facilitado mediante la propiedad __Value__ se anexará al valor existente.| 
| DependsOn | Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.| 
| Value| Valor que se asigna a la variable de entorno.| 

## <a name="example"></a>Ejemplo

El ejemplo siguiente se asegura de que __TestEnvironmentVariable__ exista y tenga el valor __TestValue__. Si no existe, se crea.

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```

