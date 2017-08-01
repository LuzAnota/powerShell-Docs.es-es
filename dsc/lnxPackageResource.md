---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recurso nxPackage de DSC para Linux
ms.openlocfilehash: 11019b1cd12f23b0b498b7cb9a06e02c46c3c279
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-for-linux-nxpackage-resource"></a>Recurso nxPackage de DSC para Linux

El recurso **nxPackage** de la configuración de estado deseado (DSC) de PowerShell ofrece un mecanismo para administrar paquetes en un nodo de Linux.

## <a name="syntax"></a>Sintaxis

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]
    
}
```

## <a name="properties"></a>Propiedades

|  Propiedad |  Descripción | 
|---|---|
| Nombre| El nombre del paquete para el que quiere garantizar un estado específico.| 
| Ensure| Determina si se debe comprobar si existe el paquete. Establezca esta propiedad en "Present" para asegurarse de que el paquete exista. Establézcala en "Absent" para asegurarse de que el paquete no exista. El valor predeterminado es "Present".|  
| PackageManager| Los valores admitidos son "yum", "apt" y "zypper". Especifica el administrador de paquetes que se utilizará al instalar paquetes. Si se especifica la propiedad **FilePath**, la ruta de acceso facilitada se usará para instalar el paquete. De lo contrario, se utilizará un administrador de paquetes para instalar el paquete desde un repositorio configurado previamente. Si no se facilitan ni **PackageManager** ni **FilePath**, se usará el administrador de paquetes predeterminado del sistema.| 
| FilePath| La ruta de acceso donde reside el paquete.| 
| PackageGroup| Si su valor es **$true**, se espera que el valor **Name** sea el nombre de un grupo de paquetes que se usará con un elemento **PackageManager**. La propiedad **PackageGroup** no es válida cuando se proporciona un elemento **FilePath**.| 
| Argumentos| Una cadena de argumentos que se pasarán al paquete tal y como se faciliten.| 
| ReturnCode| El código de retorno esperado. Si el código de retorno real no a coincide con el valor esperado facilitado aquí, la configuración devolverá un error.| 
| DependsOn | Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento **ID** del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.| 

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se garantiza que el paquete denominado "httpd" está instalado en un equipo Linux, mediante el administrador de paquetes "Yum".

```
Import-DSCResource -Module nx 

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```

