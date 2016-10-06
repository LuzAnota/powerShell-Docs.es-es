---
title: "Recursos de configuración de estado deseado integrados para Linux"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 6b001c12885022006003ef3ffe91b7aede07bd17

---

# Recursos de configuración de estado deseado integrados para Linux

Los recursos son bloques de creación que puede usar para escribir un script de configuración de estado deseado (DSC) de PowerShell. DSC para Linux incorpora un conjunto de funcionalidades integradas para configurar recursos tales como archivos y carpetas, paquetes, variables de entorno, servicios y procesos.

## Recursos integrados 

En la tabla siguiente se ofrece una lista con estos recursos y vínculos a temas que los describen en detalle.

* [Recurso nxArchive](lnxArchiveResource.md): ofrece un mecanismo para desempaquetar archivos de almacenamiento (.tar, .zip) en una ruta específica.
* [Recurso nxEnvironment](lnxEnvironmentResource.md): administra las variables de entorno en los nodos de destino. 
* [Recurso nxFile](lnxFileResource.md): administra archivos y directorios de Linux. 
* [Recurso nxFileLine](lnxFileLineResource.md): administra líneas individuales de un archivo de Linux. 
* [Recurso nxGroup](lnxGroupResource.md): administra grupos locales de Linux. 
* [Recurso nxPackage](lnxPackageResource.md): administra paquetes en nodos de Linux.
* [Recurso nxScript](lnxScriptResource.md): ejecuta scripts en nodos de destino.
* [Recurso nxService](lnxServiceResource.md): administra servicios (demonios) de Linux.
* [Recurso nxSshAuthorizedKeys](lnxSshAuthorizedKeysResource.md): administra claves ssh públicas para un usuario de Linux. 
* [Recurso nxUser](lnxUserResource.md): administra usuarios locales de Linux. 
  



<!--HONumber=Aug16_HO3-->


