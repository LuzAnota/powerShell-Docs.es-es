---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: e503f9a4462e94fce42ffcdcc0976d261c051f87
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="6804d-102">Declarar la interfaz implementada</span><span class="sxs-lookup"><span data-stu-id="6804d-102">Declare Implemented Interface</span></span>

<span data-ttu-id="6804d-103">Puede declarar interfaces implementadas después de los tipos base o inmediatamente después de dos puntos (:) si no existe ningún tipo base especificado.</span><span class="sxs-lookup"><span data-stu-id="6804d-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="6804d-104">Separe todos los nombres de tipo con comas.</span><span class="sxs-lookup"><span data-stu-id="6804d-104">Separate all type names by using commas.</span></span> <span data-ttu-id="6804d-105">Es muy similar a la sintaxis de C#.</span><span class="sxs-lookup"><span data-stu-id="6804d-105">It’s very similar to C# syntax.</span></span>

```PowerShell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

