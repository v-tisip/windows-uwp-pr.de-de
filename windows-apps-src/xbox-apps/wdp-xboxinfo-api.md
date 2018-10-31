---
author: M-Stahl
title: Portal Xbox Geräteinformationen-API-Referenz
description: Enthält Informationen zum Zugriff auf Xbox-Geräteinformationen.
ms.author: mstahl
ms.date: 11/7/2017
ms.topic: article
keywords: Windows 10, Uwp, Xbox, Device portal
ms.localizationpriority: medium
ms.openlocfilehash: 4b0e2bab0ce7d5525e8032809954ff656a74a61c
ms.sourcegitcommit: ca96031debe1e76d4501621a7680079244ef1c60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "5812364"
---
# <a name="xbox-info-api-reference"></a><span data-ttu-id="e804a-104">Xbox-Info-API-Referenz</span><span class="sxs-lookup"><span data-stu-id="e804a-104">Xbox Info API reference</span></span>   
<span data-ttu-id="e804a-105">Sie können die Xbox One Geräteinformationen mithilfe dieser API zugreifen.</span><span class="sxs-lookup"><span data-stu-id="e804a-105">You can access Xbox One device information using this API.</span></span>

## <a name="get-xbox-one-device-information"></a><span data-ttu-id="e804a-106">Abrufen von Xbox One Geräteinformationen</span><span class="sxs-lookup"><span data-stu-id="e804a-106">Get Xbox One device information</span></span>

**<span data-ttu-id="e804a-107">Anforderung</span><span class="sxs-lookup"><span data-stu-id="e804a-107">Request</span></span>**

<span data-ttu-id="e804a-108">Informationen erhalten zu Ihrer Xbox One.</span><span class="sxs-lookup"><span data-stu-id="e804a-108">You can get device information about your Xbox One.</span></span>

<span data-ttu-id="e804a-109">Methode</span><span class="sxs-lookup"><span data-stu-id="e804a-109">Method</span></span>      | <span data-ttu-id="e804a-110">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="e804a-110">Request URI</span></span>
:------     | :-----
<span data-ttu-id="e804a-111">GET</span><span class="sxs-lookup"><span data-stu-id="e804a-111">GET</span></span> | <span data-ttu-id="e804a-112">/ext/xbox/info</span><span class="sxs-lookup"><span data-stu-id="e804a-112">/ext/xbox/info</span></span>
<br />
**<span data-ttu-id="e804a-113">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="e804a-113">URI parameters</span></span>**

- <span data-ttu-id="e804a-114">Keine</span><span class="sxs-lookup"><span data-stu-id="e804a-114">None</span></span>

**<span data-ttu-id="e804a-115">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="e804a-115">Request headers</span></span>**

- <span data-ttu-id="e804a-116">Keine</span><span class="sxs-lookup"><span data-stu-id="e804a-116">None</span></span>

**<span data-ttu-id="e804a-117">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="e804a-117">Request body</span></span>**

- <span data-ttu-id="e804a-118">Keine</span><span class="sxs-lookup"><span data-stu-id="e804a-118">None</span></span>

**<span data-ttu-id="e804a-119">Antwort</span><span class="sxs-lookup"><span data-stu-id="e804a-119">Response</span></span>**   
<span data-ttu-id="e804a-120">Ein JSON-Objekt mit den folgenden Feldern:</span><span class="sxs-lookup"><span data-stu-id="e804a-120">A JSON object with the following fields:</span></span>

* <span data-ttu-id="e804a-121">OsVersion - (Zeichenfolge) die Version des Betriebssystems.</span><span class="sxs-lookup"><span data-stu-id="e804a-121">OsVersion - (String) The version of the OS.</span></span>
* <span data-ttu-id="e804a-122">OsEdition - (Zeichenfolge) die Edition des Betriebssystems, z. B. "März 2017" oder "März 2017 QFE 1".</span><span class="sxs-lookup"><span data-stu-id="e804a-122">OsEdition - (String) The edition of the OS, such as "March 2017" or "March 2017 QFE 1".</span></span>
* <span data-ttu-id="e804a-123">ConsoleId - (Zeichenfolge) die Konsole des-ID.</span><span class="sxs-lookup"><span data-stu-id="e804a-123">ConsoleId - (String) The console's ID.</span></span>
* <span data-ttu-id="e804a-124">DeviceId - (Zeichenfolge) die Konsole des Xbox Live Gerät Id.</span><span class="sxs-lookup"><span data-stu-id="e804a-124">DeviceId - (String) The console's Xbox Live Device Id.</span></span>
* <span data-ttu-id="e804a-125">Seriennummer - (Zeichenfolge) die Konsole des Seriennummer.</span><span class="sxs-lookup"><span data-stu-id="e804a-125">SerialNumber - (String) The console's serial number.</span></span>
* <span data-ttu-id="e804a-126">DevMode - (Zeichenfolge) die Konsole des aktuellen Entwicklermodus, z. B. "None" oder "Retail".</span><span class="sxs-lookup"><span data-stu-id="e804a-126">DevMode - (String) The console's current developer mode, such as "None" or "Retail".</span></span>
* <span data-ttu-id="e804a-127">ConsoleType - (Zeichenfolge) die Konsole des Typ, z. B. "Xbox One" oder "Xbox One S".</span><span class="sxs-lookup"><span data-stu-id="e804a-127">ConsoleType - (String) The console's type, such as "Xbox One" or "Xbox One S".</span></span>
* <span data-ttu-id="e804a-128">DevkitCertificateExpirationTime – (Number) der UTC-Zeit in Sekunden, wenn die Konsole Developer Kit Zertifikat abläuft.</span><span class="sxs-lookup"><span data-stu-id="e804a-128">DevkitCertificateExpirationTime - (Number) The UTC Time in seconds when the console's developer kit certificate will expire.</span></span>

**<span data-ttu-id="e804a-129">Statuscode</span><span class="sxs-lookup"><span data-stu-id="e804a-129">Status code</span></span>**

<span data-ttu-id="e804a-130">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="e804a-130">This API has the following expected status codes.</span></span>

<span data-ttu-id="e804a-131">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="e804a-131">HTTP status code</span></span>      | <span data-ttu-id="e804a-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e804a-132">Description</span></span>
:------     | :-----
<span data-ttu-id="e804a-133">200</span><span class="sxs-lookup"><span data-stu-id="e804a-133">200</span></span> | <span data-ttu-id="e804a-134">Die Anforderung war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="e804a-134">Request was successful</span></span>
<span data-ttu-id="e804a-135">4XX</span><span class="sxs-lookup"><span data-stu-id="e804a-135">4XX</span></span> | <span data-ttu-id="e804a-136">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="e804a-136">Error codes</span></span>
<span data-ttu-id="e804a-137">5XX</span><span class="sxs-lookup"><span data-stu-id="e804a-137">5XX</span></span> | <span data-ttu-id="e804a-138">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="e804a-138">Error codes</span></span>

<br />
**<span data-ttu-id="e804a-139">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="e804a-139">Available device families</span></span>**

* <span data-ttu-id="e804a-140">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="e804a-140">Windows Xbox</span></span>