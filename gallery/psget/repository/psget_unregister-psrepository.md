---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: psget_unregister psrepository
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: 7d9c24ebb20756a2f7852692532ac6ec7e558ca9

---

# Unregister-PSRepository

Anula el registro de un repositorio.

## Descripción

El cmdlet Unregister-PSRepository anula el registro de un repositorio del usuario actual.
- Se permite la anulación del registro y el nuevo registro del repositorio PSGallery para una empresa y escenarios desconectados.
- Para que los usuarios puedan volver a registrar PSGallery, simplemente deben ejecutar `Register-PSRepository -Default`
- Puesto que PSGallery es el repositorio de publicación predeterminado de los cmdlets Publish-Module y Publish-Script, se producirá un error si PSGallery no está disponible en la lista de repositorios registrados.

## Sintaxis de cmdlet

```powershell
Get-Command -Name Unregister-PSRepository -Module PowerShellGet -Syntax
```
## Referencia de la ayuda en línea de cmdlet

[Unregister-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517130)

## Comandos de ejemplo

```powershell
Unregister-PSRepository -Name "MyPrivateGallery"

Get-PSRepository exp | Unregister-PSRepository
```

### Se permite la anulación del registro y el nuevo registro del repositorio PSGallery para una empresa y escenarios desconectados.
```powershell

# Unregister PSGallery repository
Unregister-PSRepository PSGallery

# Publish-Module throws an error when PSGallery is not a registered repository
Publish-Module -Name MyModule
publish-module : Unable to find repository 'PSGallery'. Use Get-PSRepository to see all available repositories. Try again after specifying a valid repository name. You can use 'Register-PSRepository -Default' to register the PSGallery repository.
At line:1 char:1
+ publish-module -name mymodule
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (PSGallery:String) [Publish-Module], ArgumentException
    + FullyQualifiedErrorId : PSGalleryNotFound,Publish-Module

# Re-register PSGallery repository
Register-PSRepository -Default
```




<!--HONumber=Oct16_HO2-->

