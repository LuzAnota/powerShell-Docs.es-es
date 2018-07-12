---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Otros objetos de scripting útiles
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 2ae9bc1864daedbcb0070c5f3862a6c98f8db2d4
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893287"
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="72df4-103">Otros objetos de scripting útiles</span><span class="sxs-lookup"><span data-stu-id="72df4-103">Other Useful Scripting Objects</span></span>

<span data-ttu-id="72df4-104">Los objetos siguientes proporcionan funcionalidad adicional de scripting de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="72df4-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="72df4-105">No forman parte de la jerarquía de **$psISE**.</span><span class="sxs-lookup"><span data-stu-id="72df4-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="72df4-106">Objetos de scripting útiles</span><span class="sxs-lookup"><span data-stu-id="72df4-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="72df4-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="72df4-107">$psUnsupportedConsoleApplications</span></span>

<span data-ttu-id="72df4-108">Existen algunas limitaciones sobre cómo Windows PowerShell ISE interactúa con las aplicaciones de consola.</span><span class="sxs-lookup"><span data-stu-id="72df4-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="72df4-109">Un comando o un script de automatización que requiere la intervención de usuario podrían no funcionar de la misma forma que desde la consola de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="72df4-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="72df4-110">Puede bloquear la ejecución de estos comandos o scripts en el panel de comandos de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="72df4-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="72df4-111">El objeto **$psUnsupportedConsoleApplications** mantiene una lista de estos comandos.</span><span class="sxs-lookup"><span data-stu-id="72df4-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="72df4-112">Si intenta ejecutar los comandos de esta lista, recibirá un mensaje donde se indica que no son compatibles.</span><span class="sxs-lookup"><span data-stu-id="72df4-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="72df4-113">El siguiente script agrega una entrada a la lista.</span><span class="sxs-lookup"><span data-stu-id="72df4-113">The following script adds an entry to the list.</span></span>

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a><span data-ttu-id="72df4-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="72df4-114">$psLocalHelp</span></span>

<span data-ttu-id="72df4-115">Se trata de un objeto de diccionario que mantiene una asignación contextual entre los temas de Ayuda y sus vínculos asociados en el archivo de Ayuda HTML compilado local.</span><span class="sxs-lookup"><span data-stu-id="72df4-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="72df4-116">Se utiliza para buscar la Ayuda local para un tema determinado.</span><span class="sxs-lookup"><span data-stu-id="72df4-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="72df4-117">Puede agregar o eliminar los temas de esta lista.</span><span class="sxs-lookup"><span data-stu-id="72df4-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="72df4-118">En el ejemplo de código siguiente se muestran algunos pares clave-valor de ejemplo que se encuentran en `$psLocalHelp`.</span><span class="sxs-lookup"><span data-stu-id="72df4-118">The following code example shows some example key-value pairs that are contained in `$psLocalHelp`.</span></span>

```powershell
# See the local help map
$psLocalHelp | Format-List
```

### <a name="pslocalhelp-sample-output"></a><span data-ttu-id="72df4-119">Salida de ejemplo $psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="72df4-119">$psLocalHelp Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="72df4-120">Clave: Add-Computer</span><span class="sxs-lookup"><span data-stu-id="72df4-120">Key : Add-Computer</span></span>|<span data-ttu-id="72df4-121">Valor: WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span><span class="sxs-lookup"><span data-stu-id="72df4-121">Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span></span>|
|<span data-ttu-id="72df4-122">Clave: Add-Content</span><span class="sxs-lookup"><span data-stu-id="72df4-122">Key : Add-Content</span></span>|<span data-ttu-id="72df4-123">Valor: WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span><span class="sxs-lookup"><span data-stu-id="72df4-123">Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span></span>|

<span data-ttu-id="72df4-124">El siguiente script agrega una entrada a la lista.</span><span class="sxs-lookup"><span data-stu-id="72df4-124">The following script adds an entry to the list.</span></span>

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="72df4-125">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="72df4-125">$psOnlineHelp</span></span>

<span data-ttu-id="72df4-126">Se trata de un objeto de diccionario que mantiene una asignación contextual entre los títulos de los temas de Ayuda y sus direcciones URL externas asociadas.</span><span class="sxs-lookup"><span data-stu-id="72df4-126">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="72df4-127">Se utiliza para buscar la Ayuda para un tema determinado en la Web.</span><span class="sxs-lookup"><span data-stu-id="72df4-127">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="72df4-128">Puede agregar o eliminar los temas de esta lista.</span><span class="sxs-lookup"><span data-stu-id="72df4-128">You can add or delete topics from this list.</span></span>

```powershell
$psOnlineHelp | Format-List
```

## <a name="psonilnehelp-sample-output"></a><span data-ttu-id="72df4-129">Salida de ejemplo $psOnilneHelp</span><span class="sxs-lookup"><span data-stu-id="72df4-129">$psOnilneHelp Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="72df4-130">Clave: Add-Computer</span><span class="sxs-lookup"><span data-stu-id="72df4-130">Key : Add-Computer</span></span>|<span data-ttu-id="72df4-131">Valor: http://go.microsoft.com/fwlink/p/?LinkID=135194</span><span class="sxs-lookup"><span data-stu-id="72df4-131">Value : http://go.microsoft.com/fwlink/p/?LinkID=135194</span></span>|
|<span data-ttu-id="72df4-132">Clave: Add-Content</span><span class="sxs-lookup"><span data-stu-id="72df4-132">Key : Add-Content</span></span>|<span data-ttu-id="72df4-133">Valor: http://go.microsoft.com/fwlink/p/?LinkID=113278</span><span class="sxs-lookup"><span data-stu-id="72df4-133">Value : http://go.microsoft.com/fwlink/p/?LinkID=113278</span></span>|

<span data-ttu-id="72df4-134">El siguiente script agrega una entrada a la lista.</span><span class="sxs-lookup"><span data-stu-id="72df4-134">The following script adds an entry to the list.</span></span>

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="72df4-135">Véase también</span><span class="sxs-lookup"><span data-stu-id="72df4-135">See Also</span></span>

[<span data-ttu-id="72df4-136">Finalidad del modelo de objetos de scripting de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="72df4-136">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)