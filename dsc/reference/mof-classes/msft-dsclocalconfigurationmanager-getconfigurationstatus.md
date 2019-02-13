---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método GetConfigurationStatus de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: c66ccc4eefaef2d0c3a68fa8a96c5abb9bda6e4c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "55681425"
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9e7a9-103">Método GetConfigurationStatus de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="9e7a9-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9e7a9-104">Obtiene el historial de estado de la configuración.</span><span class="sxs-lookup"><span data-stu-id="9e7a9-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="9e7a9-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9e7a9-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="9e7a9-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9e7a9-106">Parameters</span></span>

<span data-ttu-id="9e7a9-107">*All* \[in\] **true** si este método debe devolver información sobre toda la configuración que se ejecuta en la máquina, incluidas la aplicación de configuración y la comprobación de coherencia.</span><span class="sxs-lookup"><span data-stu-id="9e7a9-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="9e7a9-108">*configurationStatus* \[out\] En la devolución, contiene una instancia insertada de la clase **MSFT_DSCConfigurationStatus** que define la configuración.</span><span class="sxs-lookup"><span data-stu-id="9e7a9-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="9e7a9-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="9e7a9-109">Return value</span></span>

<span data-ttu-id="9e7a9-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="9e7a9-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9e7a9-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="9e7a9-111">Remarks</span></span>

<span data-ttu-id="9e7a9-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="9e7a9-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9e7a9-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9e7a9-113">Requirements</span></span>

<span data-ttu-id="9e7a9-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9e7a9-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="9e7a9-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9e7a9-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="9e7a9-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="9e7a9-116">See also</span></span>

[<span data-ttu-id="9e7a9-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9e7a9-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)