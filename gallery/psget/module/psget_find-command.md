---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: psget_find command
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: 7d46f02106785b0f94f73e60231fb4623002cfb6

---

# Find-Command

Busca comandos de PowerShell en módulos.

## Descripción
El cmdlet Find-Command busca comandos de PowerShell, como cmdlets, alias, funciones y flujos de trabajo. Find-Command busca en los módulos de los repositorios registrados.
Para cada comando que este cmdlet encuentre, devuelve un objeto PSGetCommandInfo. Puede pasar un objeto PSGetCommandInfo al cmdlet Install-Module para instalar el módulo que contiene el comando.

- Find-Command puede filtrar con parámetros de versión: MinimumVersion, RequiredVersion y AllVersions.
  - Estos parámetros se excluyen mutuamente.
  - Estos parámetros de versión solo se permiten con el nombre de módulo único sin ningún carácter comodín.
  - Si no se especifica el parámetro RequiredVersion, Find-Command devuelve la versión más reciente del módulo que sea igual o mayor que la versión mínima especificada, o la versión más reciente del módulo si no se especifica ninguna versión mínima.
  - Si se especifica el parámetro RequiredVersion, Find-Command solo devuelve la versión del módulo que coincida exactamente con la versión especificada.
- Find-Command puede filtrar por los metadatos del módulo con el parámetro -Tag.
- Find-Command puede filtrar por el idioma de búsqueda específico del repositorio con el parámetro -Filter.
- Find-Command puede filtrar por los módulos de todos o algunos de los repositorios registrados.

## Sintaxis de cmdlet
```powershell
Get-Command -Name Find-Command -Module PowerShellGet -Syntax
```

## Referencia de la ayuda en línea de cmdlet

[Find-Command](http://go.microsoft.com/fwlink/?LinkId=733636)

## Comandos de ejemplo
```powershell

# Find a specific command
Find-Command -Name Get-ScriptAnalyzerRule

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Get-ScriptAnalyzerRule              1.5.0      PSScriptAnalyzer                    PSGallery

# Find multiple commands
Find-Command -Name Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

# Find all available commands from all registered repositories
Find-Command

# Find available commands from few registered repositories
Find-Command -Repository PSGallery,PrivatePSGallery

# Find all commands in a specified repository
Find-Command -Repository PSGallery

# Find a command defined in a specific module
Find-Command -Name Get-ScriptAnalyzerRule -Module PSScriptAnalyzer

# Find commands from all versions of a module
Find-Command -ModuleName PSReadline -AllVersions

# Find commands with module name and MinimumVersion.
Find-Command -ModuleName PSReadline -MinimumVersion 1.1

# Find commands with module name and exact version
Find-Command -ModuleName AzureRM -RequiredVersion 1.4.0

# Find commands defined modules with -Filter based search. -Filter searches in description and module names
Find-Command -Filter Cookbook
Find-Command -Filter RBAC

# Find all commands with tags Azure or DSC in module metadata
Find-Command -Tag Azure, DSC

```




<!--HONumber=Oct16_HO2-->

