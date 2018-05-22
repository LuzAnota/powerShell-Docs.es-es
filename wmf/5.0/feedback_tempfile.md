---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 08f431c27cd0ee769518b5246af2fa95aa499d54
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="new-temporaryfile"></a><span data-ttu-id="050bb-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="050bb-102">New-TemporaryFile</span></span>
<span data-ttu-id="050bb-103">A veces es necesario crear un archivo temporal en los scripts.</span><span class="sxs-lookup"><span data-stu-id="050bb-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="050bb-104">Puede hacerlo fácilmente con el cmdlet **New-TemporaryFile**:</span><span class="sxs-lookup"><span data-stu-id="050bb-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="050bb-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="050bb-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="050bb-106">PS C:\\&gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="050bb-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="050bb-107">C:\\Usuarios\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="050bb-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>
