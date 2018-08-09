---
title: Instalación de PowerShell Core en macOS
description: Información sobre cómo instalar PowerShell Core en macOS
ms.date: 08/06/2018
ms.openlocfilehash: ff1814d95b3ca3fa8497069dff249fd2ad5576ef
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587472"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="bcfee-103">Instalación de PowerShell Core en macOS</span><span class="sxs-lookup"><span data-stu-id="bcfee-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="bcfee-104">PowerShell Core admite macOS 10.12 y superior.</span><span class="sxs-lookup"><span data-stu-id="bcfee-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="bcfee-105">Todos los paquetes están disponibles en nuestra página de [versiones][] de GitHub.</span><span class="sxs-lookup"><span data-stu-id="bcfee-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="bcfee-106">Una vez que se haya instalado el paquete, ejecute `pwsh` desde un terminal.</span><span class="sxs-lookup"><span data-stu-id="bcfee-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-via-homebrew-on-macos-1012"></a><span data-ttu-id="bcfee-107">Instalación mediante Homebrew en macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="bcfee-107">Installation via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="bcfee-108">[Homebrew][brew] es el administrador de paquetes preferido de macOS.</span><span class="sxs-lookup"><span data-stu-id="bcfee-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="bcfee-109">En una ventana de terminal, escriba `brew` para ejecutar Homebrew.</span><span class="sxs-lookup"><span data-stu-id="bcfee-109">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="bcfee-110">Si no se encuentra el comando `brew`, debe instalar Homebrew según [sus instrucciones][brew].</span><span class="sxs-lookup"><span data-stu-id="bcfee-110">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="bcfee-111">Si instaló Homebrew anteriormente, se recomienda ejecutar "brew update-reset" y "brew update".</span><span class="sxs-lookup"><span data-stu-id="bcfee-111">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

> <span data-ttu-id="bcfee-112">Las versiones anteriores de Homebrew usaban la derivación "caskroom/cask", que está en desuso, y se migró a "homebrew/cask".</span><span class="sxs-lookup"><span data-stu-id="bcfee-112">Older versions of Homebrew used the tap 'caskroom/cask', which has been deprecated, and migrated into 'homebrew/cask'.</span></span>  <span data-ttu-id="bcfee-113">Puede encontrar más información en [Homebrew-cask][cask].</span><span class="sxs-lookup"><span data-stu-id="bcfee-113">More information can be found at [Homebrew-cask][cask].</span></span> <span data-ttu-id="bcfee-114">Use el comando "brew tap" para mostrar las derivaciones actuales.</span><span class="sxs-lookup"><span data-stu-id="bcfee-114">Use the 'brew tap' command to list your current taps.</span></span>  <span data-ttu-id="bcfee-115">Si ve "caskroom/cask", puede usar "brew update" para que Homebrew migre las derivaciones.</span><span class="sxs-lookup"><span data-stu-id="bcfee-115">If you see 'caskroom/cask' you can use 'brew update' to have Homebrew migrate the taps.</span></span>

```sh
brew tap
brew update
```

<span data-ttu-id="bcfee-116">Una vez que instale o actualice Homebrew, la instalación de PowerShell le resultará muy fácil.</span><span class="sxs-lookup"><span data-stu-id="bcfee-116">Once you've installed/updated Homebrew, installing PowerShell is easy.</span></span>

<span data-ttu-id="bcfee-117">Para instalar PowerShell:</span><span class="sxs-lookup"><span data-stu-id="bcfee-117">To install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="bcfee-118">Por último, compruebe que la instalación funciona correctamente:</span><span class="sxs-lookup"><span data-stu-id="bcfee-118">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="bcfee-119">Para salir de PowerShell y volver a Bash, use el comando "exit".</span><span class="sxs-lookup"><span data-stu-id="bcfee-119">To exit PowerShell, and return to bash, use the 'exit' command.</span></span>
```sh
exit
```

<span data-ttu-id="bcfee-120">Cuando se publiquen nuevas versiones de PowerShell, bastará con actualizar las fórmulas de Homebrew y PowerShell:</span><span class="sxs-lookup"><span data-stu-id="bcfee-120">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="bcfee-121">Los comandos anteriores pueden llamarse desde un host de PowerShell (pwsh), pero, acto seguido, el shell de PowerShell se debe cerrar y volver a iniciar para finalizar la actualización y actualizar los valores que aparecen en $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="bcfee-121">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installing-preview-via-homebrew-on-macos-1012"></a><span data-ttu-id="bcfee-122">Instalación de la versión preliminar mediante Homebrew en macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="bcfee-122">Installing Preview via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="bcfee-123">[Homebrew][brew] es el administrador de paquetes preferido de macOS.</span><span class="sxs-lookup"><span data-stu-id="bcfee-123">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="bcfee-124">En una ventana de terminal, escriba `brew` para ejecutar Homebrew.</span><span class="sxs-lookup"><span data-stu-id="bcfee-124">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="bcfee-125">Si no se encuentra el comando `brew`, debe instalar Homebrew según [sus instrucciones][brew].</span><span class="sxs-lookup"><span data-stu-id="bcfee-125">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="bcfee-126">Si instaló Homebrew anteriormente, se recomienda ejecutar "brew update-reset" y "brew update".</span><span class="sxs-lookup"><span data-stu-id="bcfee-126">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

<span data-ttu-id="bcfee-127">Luego, debe derivar el repositorio `versions` de Cask para obtener el paquete de versión preliminar:</span><span class="sxs-lookup"><span data-stu-id="bcfee-127">Then, you must tap the `versions` casks repository to get the preview package:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="bcfee-128">Para instalar la versión preliminar de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="bcfee-128">To install PowerShell Preview:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="bcfee-129">Por último, compruebe que la instalación funciona correctamente:</span><span class="sxs-lookup"><span data-stu-id="bcfee-129">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="bcfee-130">Cuando se publiquen nuevas versiones de PowerShell, bastará con actualizar las fórmulas de Homebrew y actualizar la versión preliminar de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="bcfee-130">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell Preview:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="bcfee-131">Los comandos anteriores pueden llamarse desde un host de PowerShell (pwsh), pero, acto seguido, el shell de PowerShell se debe cerrar y volver a iniciar para finalizar la actualización y actualizar los valores que aparecen en $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="bcfee-131">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installation-via-direct-download"></a><span data-ttu-id="bcfee-132">Instalación mediante descarga directa</span><span class="sxs-lookup"><span data-stu-id="bcfee-132">Installation via Direct Download</span></span>

<span data-ttu-id="bcfee-133">Descargue el paquete PKG `powershell-6.0.2-osx.10.12-x64.pkg` de la página de [versiones][] en la máquina macOS.</span><span class="sxs-lookup"><span data-stu-id="bcfee-133">Download the PKG package `powershell-6.0.2-osx.10.12-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="bcfee-134">Puede hacer doble clic en el archivo y seguir las indicaciones, o bien instalarlo desde el terminal:</span><span class="sxs-lookup"><span data-stu-id="bcfee-134">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="bcfee-135">Archivos binarios</span><span class="sxs-lookup"><span data-stu-id="bcfee-135">Binary Archives</span></span>

<span data-ttu-id="bcfee-136">Se proporcionan archivos binarios `tar.gz` de PowerShell para que las plataformas macOS y Linux permitan escenarios de implementación avanzada.</span><span class="sxs-lookup"><span data-stu-id="bcfee-136">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="bcfee-137">Instalación de archivos binarios en macOS</span><span class="sxs-lookup"><span data-stu-id="bcfee-137">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.2/pwsh /usr/local/bin/pwsh
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="bcfee-138">Desinstalación de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="bcfee-138">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="bcfee-139">Si ha instalado PowerShell con Homebrew, la desinstalación es fácil:</span><span class="sxs-lookup"><span data-stu-id="bcfee-139">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="bcfee-140">Si ha instalado PowerShell mediante descarga directa, deberá quitar PowerShell manualmente:</span><span class="sxs-lookup"><span data-stu-id="bcfee-140">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="bcfee-141">Para quitar las rutas de acceso de PowerShell adicionales, consulte la sección [Rutas de acceso][] de este documento y elimine las rutas de acceso deseadas mediante `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="bcfee-141">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="bcfee-142">Este paso no es necesario si ha realizado la instalación con Homebrew.</span><span class="sxs-lookup"><span data-stu-id="bcfee-142">This is not necessary if you installed with Homebrew.</span></span>

[Rutas de acceso]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="bcfee-144">Rutas de acceso</span><span class="sxs-lookup"><span data-stu-id="bcfee-144">Paths</span></span>

* <span data-ttu-id="bcfee-145">`$PSHOME` es `/usr/local/microsoft/powershell/6.0.2/`.</span><span class="sxs-lookup"><span data-stu-id="bcfee-145">`$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="bcfee-146">Los perfiles de usuario se leerán de `~/.config/powershell/profile.ps1`.</span><span class="sxs-lookup"><span data-stu-id="bcfee-146">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="bcfee-147">Los perfiles predeterminados se leerán de `$PSHOME/profile.ps1`.</span><span class="sxs-lookup"><span data-stu-id="bcfee-147">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="bcfee-148">Los módulos de usuario se leerán de `~/.local/share/powershell/Modules`.</span><span class="sxs-lookup"><span data-stu-id="bcfee-148">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="bcfee-149">Los módulos compartidos se leerán de `/usr/local/share/powershell/Modules`.</span><span class="sxs-lookup"><span data-stu-id="bcfee-149">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="bcfee-150">Los módulos predeterminados se leerán de `$PSHOME/Modules`.</span><span class="sxs-lookup"><span data-stu-id="bcfee-150">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="bcfee-151">El historial de PSReadline se grabará en `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`.</span><span class="sxs-lookup"><span data-stu-id="bcfee-151">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="bcfee-152">Los perfiles respetan la configuración por host de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bcfee-152">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="bcfee-153">Así que los perfiles predeterminados específicos del host están en `Microsoft.PowerShell_profile.ps1` en las mismas ubicaciones.</span><span class="sxs-lookup"><span data-stu-id="bcfee-153">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="bcfee-154">PowerShell respeta la [especificación de directorio base de XDG][xdg-bds] en macOS.</span><span class="sxs-lookup"><span data-stu-id="bcfee-154">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="bcfee-155">Dado que macOS es una derivación de BSD, se usa el prefijo `/usr/local` en lugar de `/opt`.</span><span class="sxs-lookup"><span data-stu-id="bcfee-155">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="bcfee-156">Por lo tanto, `$PSHOME` es `/usr/local/microsoft/powershell/6.0.2/`, y el vínculo simbólico se coloca en `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="bcfee-156">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="bcfee-157">Recursos adicionales</span><span class="sxs-lookup"><span data-stu-id="bcfee-157">Additional Resources</span></span>

* <span data-ttu-id="bcfee-158">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="bcfee-158">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="bcfee-159">[Repositorio GitHub de Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="bcfee-159">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="bcfee-160">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="bcfee-160">[Homebrew-Cask][cask]</span></span>


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[Versiones]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
