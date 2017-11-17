---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Get-InstalledModule
ms.openlocfilehash: 6f485d04503ea6d9a51a68ae7ec3d0dc2e6facab
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="get-installedmodule"></a><span data-ttu-id="b6f11-103">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="b6f11-103">Get-InstalledModule</span></span>

<span data-ttu-id="b6f11-104">Obtiene los módulos instalados en un equipo.</span><span class="sxs-lookup"><span data-stu-id="b6f11-104">Gets installed modules on a computer.</span></span>

## <a name="description"></a><span data-ttu-id="b6f11-105">Descripción</span><span class="sxs-lookup"><span data-stu-id="b6f11-105">Description</span></span>

<span data-ttu-id="b6f11-106">El cmdlet Get-InstalledModule obtiene los módulos de PowerShell que se instalaron en un equipo mediante el cmdlet Install-Module.</span><span class="sxs-lookup"><span data-stu-id="b6f11-106">The Get-InstalledModule cmdlet gets installed PowerShell modules on a computer which were installed using Install-Module cmdlet.</span></span>

<span data-ttu-id="b6f11-107">Para cada módulo instalado, Get-InstalledModule devuelve un objeto PSRepositoryItemInfo que opcionalmente se puede canalizar a Uninstall-Module para desinstalar los módulos instalados.</span><span class="sxs-lookup"><span data-stu-id="b6f11-107">For each installed module, Get-InstalledModule returns a PSRepositoryItemInfo object which can optionally be piped to Uninstall-Module for uninstalling the installed modules.</span></span>

- <span data-ttu-id="b6f11-108">Get-InstalledModule puede filtrar los módulos instalados en función de parámetros de nombre y versión.</span><span class="sxs-lookup"><span data-stu-id="b6f11-108">Get-InstalledModule can filter installed modules based on name, version parameters.</span></span>
- <span data-ttu-id="b6f11-109">Get-InstalledModule puede filtrar con parámetros de versión: MinimumVersion, MaximumVersion, RequiredVersion y AllVersions.</span><span class="sxs-lookup"><span data-stu-id="b6f11-109">Get-InstalledModule can filter with version parameters: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="b6f11-110">Estos parámetros se excluyen mutuamente, excepto MinmimumVersion y MaximumVersion.</span><span class="sxs-lookup"><span data-stu-id="b6f11-110">These parameters are mutually exclusive, except MinmimumVersion and MaximumVersion.</span></span>
  - <span data-ttu-id="b6f11-111">Estos parámetros de versión solo se permiten con el nombre de módulo único sin ningún carácter comodín.</span><span class="sxs-lookup"><span data-stu-id="b6f11-111">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="b6f11-112">Si no se especifica el parámetro RequiredVersion, Get-InstalledModule devuelve la versión más reciente del módulo instalado que sea igual o mayor que la versión mínima especificada, o la versión más reciente del módulo si no se especifica ninguna versión mínima.</span><span class="sxs-lookup"><span data-stu-id="b6f11-112">If the RequiredVersion parameter is not specified, Get-InstalledModule returns the latest version of the installed module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span> 
  - <span data-ttu-id="b6f11-113">Si se especifica el parámetro RequiredVersion, Get-InstalledModule solo devuelve la versión del módulo instalado que coincida exactamente con la versión especificada.</span><span class="sxs-lookup"><span data-stu-id="b6f11-113">If the RequiredVersion parameter is specified, Get-InstalledModule only returns the version of installed module that exactly matches the specified version.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="b6f11-114">Sintaxis de cmdlet</span><span class="sxs-lookup"><span data-stu-id="b6f11-114">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Get-InstalledModule -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="b6f11-115">Referencia de la ayuda en línea de cmdlet</span><span class="sxs-lookup"><span data-stu-id="b6f11-115">Cmdlet online help reference</span></span>

[<span data-ttu-id="b6f11-116">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="b6f11-116">Get-InstalledModule</span></span>](http://go.microsoft.com/fwlink/?LinkId=526863)

## <a name="example-commands"></a><span data-ttu-id="b6f11-117">Comandos de ejemplo</span><span class="sxs-lookup"><span data-stu-id="b6f11-117">Example commands</span></span>

```powershell

# Get all modules installed using PowerShellGet cmdlets
Get-InstalledModule

# Get a specific installed module
Get-InstalledModule DJoin

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        DJoin                               PSGallery            This is a PowerShell frontend to the DJOIN.exe c...

# Get installed module with wildcards
Get-InstalledModule -Name AzureRM*

# Get all versions of an installed module
Get-InstalledModule -Name AzureRM.Automation -AllVersions

# Get installed module with MinimumVersion
Get-InstalledModule -Name AzureRM.Automation -MinimumVersion 1.0.0

# Get installed module with MaximumVersion
Get-InstalledModule -Name AzureRM.Automation -MaximumVersion 1.0.8

# Get installed module with version range
Get-InstalledModule -Name AzureRM.Automation -MinimumVersion 1.0.0 -MaximumVersion 1.0.8

# Get installed module with RequiredVersion
Get-InstalledScript -Name AzureRM.Automation -RequiredVersion 1.0.3

# Properties of Get-InstalledModule returned object
Get-InstalledModule DJoin | Format-List * -Force

Name                       : DJoin
Version                    : 1.0
Type                       : Module
Description                : This is a PowerShell frontend to the DJOIN.exe command which provides better
                             discoverability and usability.
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 7:12:37 PM
InstalledDate              : 4/5/2016 4:13:39 PM
UpdatedDate                :
LicenseUri                 :
ProjectUri                 :
IconUri                    :
Tags                       : {Nano, PSModule}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               :
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {description, installeddate, tags, PackageManagementProvider...}
InstalledLocation          : C:\Program Files\WindowsPowerShell\Modules\DJoin\1.0

```



## <a name="installeddate-and-updateddate-properties-in-psgetrepositoryiteminfo-object"></a><span data-ttu-id="b6f11-118">Propiedades InstalledDate y UpdatedDate en el objeto PSGetRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="b6f11-118">InstalledDate and UpdatedDate properties in PSGetRepositoryItemInfo object</span></span>

    During the install operation:
        InstalledDate: current DateTime (Get-Date) value
        UpdatedDate: null

    During the Update operation:
        InstalledDate: InstalledDate from the previous installation otherwise current DateTime (Get-Date) value
        UpdatedDate: current DateTime (Get-Date) value

```powershell
Install-Module -Name ContosoServer -RequiredVersion 1.0 -Repository INT
Get-InstalledModule -Name ContosoServer | Format-Table Name, InstalledDate, UpdatedDate

Name          InstalledDate         UpdatedDate
----          -------------         -----------
ContosoServer 2/29/2016 11:59:14 AM


\Update-Module -Name ContosoServer
Get-InstalledModule -Name ContosoServer | Format-Table Name, InstalledDate, UpdatedDate

Name          InstalledDate         UpdatedDate
----          -------------         -----------
ContosoServer 2/29/2016 11:59:14 AM 2/29/2016 12:00:15 PM
```

