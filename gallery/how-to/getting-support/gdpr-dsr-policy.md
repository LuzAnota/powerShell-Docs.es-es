---
ms.date: 03/27/2018
contributor: JKeithB
keywords: gallery,powershell,psgallery,GDPR
title: Cumplimiento del RGPD en la Galería de PowerShell
ms.openlocfilehash: dca1a82952c284980a84caafa13b2807e47e25a0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
---
# <a name="powershell-gallery-gdpr-compliance"></a><span data-ttu-id="75586-103">Cumplimiento del RGPD en la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="75586-103">PowerShell Gallery GDPR compliance</span></span>

## <a name="overview"></a><span data-ttu-id="75586-104">Introducción</span><span class="sxs-lookup"><span data-stu-id="75586-104">Overview</span></span>

<span data-ttu-id="75586-105">En mayo de 2018 entra en vigor una ley europea de privacidad, el Reglamento general de protección de datos (RGPD).</span><span class="sxs-lookup"><span data-stu-id="75586-105">In May 2018, a European privacy law, the General Data Protection Regulation (GDPR), takes effect.</span></span>
<span data-ttu-id="75586-106">El RGPD establece nuevas normas para empresas, organismos gubernamentales, organizaciones sin ánimo de lucro y otras organizaciones que ofrecen bienes y servicios a los ciudadanos de la Unión Europea (UE) o bien que recopilan y analizan datos vinculados a residentes de la UE.</span><span class="sxs-lookup"><span data-stu-id="75586-106">The GDPR imposes new rules on companies, government agencies, non-profits, and other organizations that offer goods and services to people in the European Union (EU), or that collect and analyze data tied to EU residents.</span></span>
<span data-ttu-id="75586-107">El RGPD se aplica con independencia de la ubicación.</span><span class="sxs-lookup"><span data-stu-id="75586-107">The GDPR applies no matter where you are located.</span></span>

> [!NOTE]
> <span data-ttu-id="75586-108">Este artículo contiene los pasos necesarios para eliminar datos personales de la Galería de PowerShell y se puede usar para cumplir las obligaciones legales relativas al RGPD.</span><span class="sxs-lookup"><span data-stu-id="75586-108">This article provides steps for how to delete personal data from the PowerShell Gallery and can be used to support your obligations under the GDPR.</span></span> <span data-ttu-id="75586-109">Si quiere obtener información general sobre este reglamento, vea la [sección del RGPD del Portal de confianza de servicios](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span><span class="sxs-lookup"><span data-stu-id="75586-109">If you’re looking for general info about GDPR, see the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span></span>

## <a name="personally-identifiable-data"></a><span data-ttu-id="75586-110">Datos de identificación personal</span><span class="sxs-lookup"><span data-stu-id="75586-110">Personally identifiable data</span></span>

<span data-ttu-id="75586-111">La Galería de PowerShell almacena la información siguiente que pueden proporcionar los usuarios y que podría contener información personal:</span><span class="sxs-lookup"><span data-stu-id="75586-111">The PowerShell Gallery stores the following information that may be provided by users, which may contain personal information:</span></span>

* <span data-ttu-id="75586-112">Cuenta de la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="75586-112">PowerShell Gallery account</span></span>
* <span data-ttu-id="75586-113">Elementos publicados en la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="75586-113">Items published to the PowerShell Gallery</span></span>
* <span data-ttu-id="75586-114">Comunicaciones por correo electrónico con el equipo de la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="75586-114">Email correspondence with the PowerShell Gallery team</span></span>

<span data-ttu-id="75586-115">La mayoría de los usuarios no crea una cuenta de la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="75586-115">Most users do not create a PowerShell Gallery account.</span></span>
<span data-ttu-id="75586-116">Dicha cuenta no es necesaria a menos que tenga intención de publicar un elemento o usar la característica "Ponerse en contacto con el propietario" de la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="75586-116">An account is not required unless you are going to publish an item or use the "Contact Owner" feature in the PowerShell Gallery.</span></span>
<span data-ttu-id="75586-117">Aparte de las comunicaciones por correo electrónico iniciadas por un usuario, la Galería de PowerShell no almacena datos de identificación personal de los usuarios que no han creado ninguna cuenta.</span><span class="sxs-lookup"><span data-stu-id="75586-117">Other than email correspondence initiated by the user, the PowerShell Gallery does not store personally identifiable data for users who have not created an account.</span></span>

<span data-ttu-id="75586-118">Los usuarios que creen una Galería de PowerShell podrán publicar elementos en la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="75586-118">Users who create a PowerShell Gallery account can publish items to the PowerShell Gallery.</span></span>
<span data-ttu-id="75586-119">Se espera que dichos elementos sean código de PowerShell, pero pueden contener otros datos que contengan información personal.</span><span class="sxs-lookup"><span data-stu-id="75586-119">Those items are expected to be PowerShell code, but may contain other information including personal information.</span></span>
<span data-ttu-id="75586-120">En la información que se indica a continuación se indica cómo obtener todos los elementos publicados en la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="75586-120">The information below will show how you can get all the items you have published to the PowerShell Gallery.</span></span>

## <a name="dsr-export-of-powershell-gallery-data"></a><span data-ttu-id="75586-121">Exportación de DSR de los datos de la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="75586-121">DSR Export of PowerShell Gallery Data</span></span>

<span data-ttu-id="75586-122">En las secciones siguientes se describe de qué forma la Galería de PowerShell admite las solicitudes de interesados (DSR) y se explica cómo exportar la información almacenada en la Galería de PowerShell y solicitar su eliminación.</span><span class="sxs-lookup"><span data-stu-id="75586-122">The following sections describe how the PowerShell Gallery supports data subject requests (DSR), by explaining how to export information stored in the PowerShell Gallery, and how to request deletion of this information.</span></span>

### <a name="email"></a><span data-ttu-id="75586-123">Correo electrónico</span><span class="sxs-lookup"><span data-stu-id="75586-123">Email</span></span>

<span data-ttu-id="75586-124">Entre las comunicaciones por correo electrónico se incluye todo lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="75586-124">Email correspondence may include any of the following:</span></span>

* <span data-ttu-id="75586-125">Correos electrónicos enviados a los propietarios de elementos de la Galería de PowerShell, si en los exámenes de análisis de código se ha detectado un problema con algún elemento que estos han publicado en la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="75586-125">Email sent to the owners of PowerShell Gallery items if the code analysis scans detected an issue with any item they have published to the PowerShell Gallery</span></span>
* <span data-ttu-id="75586-126">Correos electrónicos enviados por cualquier persona al equipo de la Galería de PowerShell mediante la dirección de correo electrónico de la página "Póngase en contacto con nosotros" (cgadmin@microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="75586-126">Email sent by anyone to the PowerShell Gallery team using the email address in the "Contact Us" page (cgadmin@microsoft.com)</span></span>
* <span data-ttu-id="75586-127">Los usuarios registrados que usen la característica "Ponerse en contacto con el propietario" de la Galería de PowerShell para enviar correos electrónicos al propietario de un elemento de la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="75586-127">Registered users who use the "Contact Owner" feature in the PowerShell Gallery to send email to the owner of an item in the PowerShell Gallery</span></span>

<span data-ttu-id="75586-128">Para los correos electrónicos enviados a la Galería de PowerShell o mediante esta se establece una directiva de retención de 90 días para llevar a cabo las posibles investigaciones de seguridad en caso de que se detecte código malicioso en la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="75586-128">Emails sent by or to the PowerShell Gallery have a retention policy of 90 days to support possible security investigations should malicious code be discovered on the PowerShell Gallery.</span></span>
<span data-ttu-id="75586-129">Los correos electrónicos se eliminan de acuerdo con la directiva mencionada al cabo de 90 días.</span><span class="sxs-lookup"><span data-stu-id="75586-129">Emails are deleted by policy after 90 days.</span></span>

<span data-ttu-id="75586-130">Dispone de un término de 90 días para solicitar copias de los correos electrónicos enviados a su dirección de correo electrónico o desde esta y a la Galería de PowerShell o desde esta.</span><span class="sxs-lookup"><span data-stu-id="75586-130">You may request copies of all emails sent to or from your email address and the PowerShell Gallery within the previous 90 days.</span></span>
<span data-ttu-id="75586-131">Para solicitar estas comunicaciones, envíe un correo electrónico a cgadmin@microsoft.com con el asunto "DSR Request for emails relating to this account" (Solicitud de DSR para los correos electrónicos relativos a esta cuenta).</span><span class="sxs-lookup"><span data-stu-id="75586-131">To request this correspondence, send an email to cgadmin@microsoft.com, with the title: "DSR Request for emails relating to this account".</span></span>
<span data-ttu-id="75586-132">En el cuerpo del mensaje, indique qué información solicita (por ejemplo, recibir todos los correos electrónicos enviados o recibidos en esta dirección de correo electrónico). Todos los correos electrónicos relacionados con su dirección de correo electrónico en los 90 días posteriores a la solicitud se enviarán en un término de 7 días laborables.</span><span class="sxs-lookup"><span data-stu-id="75586-132">In the body of the message, state what information you are requesting (for example: Please send all emails sent to or received from this email address.) All emails involving your email address within 90 days of the request will be sent within 7 business days.</span></span>

### <a name="powershell-gallery-account-information"></a><span data-ttu-id="75586-133">Información sobre la cuenta de la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="75586-133">PowerShell Gallery Account Information</span></span>

<span data-ttu-id="75586-134">Si ha creado una cuenta de la Galería de PowerShell, siga los pasos que se indican a continuación para encontrar toda la información personal almacenada en ella:</span><span class="sxs-lookup"><span data-stu-id="75586-134">If you have created a PowerShell Gallery account, you can find all personal information that has been stored in PowerShell Gallery by taking the following steps:</span></span>

1. <span data-ttu-id="75586-135">Inicie sesión en la Galería de PowerShell y haga clic en su nombre de usuario.</span><span class="sxs-lookup"><span data-stu-id="75586-135">Sign in to the PowerShell Gallery, then click on your username</span></span>
2. <span data-ttu-id="75586-136">La siguiente página que se mostrará será la página Cuenta, en la que constará la dirección de correo electrónico usada para la cuenta de la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="75586-136">The next page displayed is the Account page, which shows the email address used for the PowerShell Gallery account</span></span>

<span data-ttu-id="75586-137">Si ha creado más de una cuenta en la Galería de PowerShell, tendrá que repetir estos pasos para cada cuenta.</span><span class="sxs-lookup"><span data-stu-id="75586-137">If you have created more than one account in the PowerShell Gallery, you will need to repeat these steps for each account.</span></span>

### <a name="items-in-the-powershell-gallery"></a><span data-ttu-id="75586-138">Elementos de la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="75586-138">Items in the PowerShell Gallery</span></span>

<span data-ttu-id="75586-139">Para facilitar la exportación de elementos publicados en la Galería de PowerShell, hemos publicado el script "GetPSGalleryItemsForAuthor" en la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="75586-139">To facilitate exporting items published to the PowerShell Gallery, we have published the script "GetPSGalleryItemsForAuthor" to the PowerShell Gallery.</span></span>
<span data-ttu-id="75586-140">Este script exporta una copia de la versión de cada elemento colocado en la Galería de PowerShell a partir de la información sobre el autor almacenada en el elemento.</span><span class="sxs-lookup"><span data-stu-id="75586-140">This script exports a copy of every version of every item put into the PowerShell Gallery based on the author information stored in the item.</span></span>

> [!NOTE]
> <span data-ttu-id="75586-141">El autor se almacena en el manifiesto de un elemento al publicarlo.</span><span class="sxs-lookup"><span data-stu-id="75586-141">The Author is stored in the item manifest when you publish your item.</span></span>
> <span data-ttu-id="75586-142">No hay ninguna garantía de que el autor tenga la misma identidad que la de la cuenta que se usa en la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="75586-142">There is no guarantee that the Author is the same identity as the account you use in the PowerShell Gallery.</span></span>
> <span data-ttu-id="75586-143">Si usa otro valor en el campo Autor, debe proporcionar dicho valor al utilizar este script.</span><span class="sxs-lookup"><span data-stu-id="75586-143">If you use some other value in the Author field, you will need to supply that value when using this script.</span></span>

<span data-ttu-id="75586-144">Puede descargar el script usando este comando de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="75586-144">You may download the script by using the following PowerShell command:</span></span>

```powershell
Save-Script GetPSGalleryItemsForAuthor -path <local folder location> -repository psgallery
```

<span data-ttu-id="75586-145">A continuación podrá ejecutar el script directamente mediante los siguientes comandos de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="75586-145">You can then run the script directly, by running the following PowerShell commands:</span></span>

```powershell
cd <local folder location >
.\GetPSGalleryItemsForAuthor.ps1
```

<span data-ttu-id="75586-146">Se le pedirá que proporcione el autor y una carpeta en su sistema donde se deben guardar los elementos.</span><span class="sxs-lookup"><span data-stu-id="75586-146">You will be prompted to supply the Author and a folder on your system where you want the items to be saved.</span></span>

## <a name="deleting-personal-data-from-the-powershell-gallery"></a><span data-ttu-id="75586-147">Eliminación de los datos personales de la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="75586-147">Deleting Personal Data From The PowerShell Gallery</span></span>

<span data-ttu-id="75586-148">Para eliminar la cuenta de la Galería de PowerShell o cualquier elemento suyo de la Galería de PowerShell, envíe un correo electrónico a cgadmin@microsoft.com con el asunto "GDPR Request for items relating to this account" (Solicitud relativa al RGPD para elementos relacionados con esta cuenta).</span><span class="sxs-lookup"><span data-stu-id="75586-148">To delete your PowerShell Gallery account or any item you own in the PowerShell Gallery, send email to cgadmin@microsoft.com with the title: "GDPR Request for items relating to this account".</span></span>
<span data-ttu-id="75586-149">En el cuerpo del mensaje, indique qué información quiere que se elimine.</span><span class="sxs-lookup"><span data-stu-id="75586-149">In the body of the message state what information you want deleted.</span></span> <span data-ttu-id="75586-150">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="75586-150">For example:</span></span>

* <span data-ttu-id="75586-151">Eliminar la versión x.y.z del elemento "X".</span><span class="sxs-lookup"><span data-stu-id="75586-151">Please delete version x.y.z of my item "item name"</span></span>
* <span data-ttu-id="75586-152">Eliminar todas las versiones del elemento "X".</span><span class="sxs-lookup"><span data-stu-id="75586-152">Please delete all versions of my item "item name"</span></span>
* <span data-ttu-id="75586-153">Eliminar mi cuenta de la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="75586-153">Please delete my PowerShell Gallery account</span></span>

<span data-ttu-id="75586-154">Los administradores de la Galería de PowerShell responderán en un término de 7 días laborables.</span><span class="sxs-lookup"><span data-stu-id="75586-154">The PowerShell Gallery administrators will reply within 7 business days.</span></span>
<span data-ttu-id="75586-155">Los elementos especificados se eliminarán durante los 30 días posteriores al envío de la solicitud.</span><span class="sxs-lookup"><span data-stu-id="75586-155">The items specified will be deleted within 30 days after the request is sent.</span></span>