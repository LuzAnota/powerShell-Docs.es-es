---
title: Recurso nxFileLine de DSC para Linux
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 9196129e79272d8bee717ef8a5d42fb590760a0f
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="dsc-for-linux-nxfileline-resource"></a>Recurso nxFileLine de DSC para Linux

El recurso **nxFileLine** de la configuración de estado deseado (DSC) de PowerShell ofrece un mecanismo para administrar líneas dentro de un archivo de configuración en un nodo de Linux.

## <a name="syntax"></a>Sintaxis

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Propiedades

|  Propiedad |  Descripción | 
|---|---|
| FilePath| La ruta de acceso completa al archivo para administrar las líneas en el nodo de destino.| 
| ContainsLine| Una línea que debe asegurarse que exista en el archivo. Esta línea se anexará al archivo si no existe en él. **ContainsLine** es una propiedad obligatoria, pero se puede establecer en una cadena vacía (`ContainsLine = ‘’``) si no se necesita.| 
| DoesNotContainPattern| Un patrón de expresiones regulares para las líneas que no deben existir en el archivo. Para todas las líneas que existan en el archivo y coincidan con esta expresión regular, se quitará la línea del archivo.| 
| DependsOn | Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento **ID** del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.| 

## <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo utilizar el recurso **nxFileLine** para configurar el archivo `/etc/sudoers`, asegurándose de que el usuario monuser esté configurado como not requiretty.

```
Import-DSCResource -Module nx 

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
} 
```

