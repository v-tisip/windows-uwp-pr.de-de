---
author: M-Stahl
title: Xbox-Portal Geräteinformationen-API-Referenz
description: Erfahren Sie mehr über das Xbox-Geräteinformationen zugreifen.
ms.author: mstahl
ms.date: 11/7/2017
ms.topic: article
keywords: Windows 10, Uwp, Xbox, Device portal
ms.localizationpriority: medium
ms.openlocfilehash: 4b0e2bab0ce7d5525e8032809954ff656a74a61c
ms.sourcegitcommit: cbe7cf620622a5e4df7414f9e38dfecec1cfca99
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "7419044"
---
# <a name="xbox-info-api-reference"></a><span data-ttu-id="0f9b6-104">Xbox-Info-API-Referenz</span><span class="sxs-lookup"><span data-stu-id="0f9b6-104">Xbox Info API reference</span></span>   
<span data-ttu-id="0f9b6-105">Sie können die Xbox One Geräteinformationen mithilfe dieser API zugreifen.</span><span class="sxs-lookup"><span data-stu-id="0f9b6-105">You can access Xbox One device information using this API.</span></span>

## <a name="get-xbox-one-device-information"></a><span data-ttu-id="0f9b6-106">Abrufen von Xbox One Geräteinformationen</span><span class="sxs-lookup"><span data-stu-id="0f9b6-106">Get Xbox One device information</span></span>

**<span data-ttu-id="0f9b6-107">Anforderung</span><span class="sxs-lookup"><span data-stu-id="0f9b6-107">Request</span></span>**

<span data-ttu-id="0f9b6-108">Sie erhalten Informationen über Ihre Xbox One.</span><span class="sxs-lookup"><span data-stu-id="0f9b6-108">You can get device information about your Xbox One.</span></span>

<span data-ttu-id="0f9b6-109">Methode</span><span class="sxs-lookup"><span data-stu-id="0f9b6-109">Method</span></span>      | <span data-ttu-id="0f9b6-110">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="0f9b6-110">Request URI</span></span>
:------     | :-----
<span data-ttu-id="0f9b6-111">GET</span><span class="sxs-lookup"><span data-stu-id="0f9b6-111">GET</span></span> | <span data-ttu-id="0f9b6-112">/ext/xbox/info</span><span class="sxs-lookup"><span data-stu-id="0f9b6-112">/ext/xbox/info</span></span>
<br />
**<span data-ttu-id="0f9b6-113">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="0f9b6-113">URI parameters</span></span>**

- <span data-ttu-id="0f9b6-114">Keine</span><span class="sxs-lookup"><span data-stu-id="0f9b6-114">None</span></span>

**<span data-ttu-id="0f9b6-115">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="0f9b6-115">Request headers</span></span>**

- <span data-ttu-id="0f9b6-116">Keine</span><span class="sxs-lookup"><span data-stu-id="0f9b6-116">None</span></span>

**<span data-ttu-id="0f9b6-117">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="0f9b6-117">Request body</span></span>**

- <span data-ttu-id="0f9b6-118">Keine</span><span class="sxs-lookup"><span data-stu-id="0f9b6-118">None</span></span>

**<span data-ttu-id="0f9b6-119">Antwort</span><span class="sxs-lookup"><span data-stu-id="0f9b6-119">Response</span></span>**   
<span data-ttu-id="0f9b6-120">Ein JSON-Objekt mit den folgenden Feldern:</span><span class="sxs-lookup"><span data-stu-id="0f9b6-120">A JSON object with the following fields:</span></span>

* <span data-ttu-id="0f9b6-121">OsVersion - (Zeichenfolge) die Version des Betriebssystems.</span><span class="sxs-lookup"><span data-stu-id="0f9b6-121">OsVersion - (String) The version of the OS.</span></span>
* <span data-ttu-id="0f9b6-122">OsEdition - (Zeichenfolge) die Edition des Betriebssystems, z. B. "März 2017" oder "März 2017 QFE 1".</span><span class="sxs-lookup"><span data-stu-id="0f9b6-122">OsEdition - (String) The edition of the OS, such as "March 2017" or "March 2017 QFE 1".</span></span>
* <span data-ttu-id="0f9b6-123">ConsoleId - (Zeichenfolge) die Konsole des-ID.</span><span class="sxs-lookup"><span data-stu-id="0f9b6-123">ConsoleId - (String) The console's ID.</span></span>
* <span data-ttu-id="0f9b6-124">Geräte-ID - (Zeichenfolge) die Konsole des Xbox Live-Gerät Id.</span><span class="sxs-lookup"><span data-stu-id="0f9b6-124">DeviceId - (String) The console's Xbox Live Device Id.</span></span>
* <span data-ttu-id="0f9b6-125">Seriennummer - (Zeichenfolge) der Konsole der Seriennummer.</span><span class="sxs-lookup"><span data-stu-id="0f9b6-125">SerialNumber - (String) The console's serial number.</span></span>
* <span data-ttu-id="0f9b6-126">DevMode - (Zeichenfolge) die Konsole des aktuellen Entwicklermodus, z. B. "None" oder "Retail".</span><span class="sxs-lookup"><span data-stu-id="0f9b6-126">DevMode - (String) The console's current developer mode, such as "None" or "Retail".</span></span>
* <span data-ttu-id="0f9b6-127">ConsoleType - (Zeichenfolge) der Konsole Typ, z. B. "Xbox One" oder "Xbox One S".</span><span class="sxs-lookup"><span data-stu-id="0f9b6-127">ConsoleType - (String) The console's type, such as "Xbox One" or "Xbox One S".</span></span>
* <span data-ttu-id="0f9b6-128">DevkitCertificateExpirationTime – (Number) der UTC-Zeit in Sekunden, wenn die Konsole Developer Kit Zertifikat abläuft.</span><span class="sxs-lookup"><span data-stu-id="0f9b6-128">DevkitCertificateExpirationTime - (Number) The UTC Time in seconds when the console's developer kit certificate will expire.</span></span>

**<span data-ttu-id="0f9b6-129">Statuscode</span><span class="sxs-lookup"><span data-stu-id="0f9b6-129">Status code</span></span>**

<span data-ttu-id="0f9b6-130">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="0f9b6-130">This API has the following expected status codes.</span></span>

<span data-ttu-id="0f9b6-131">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="0f9b6-131">HTTP status code</span></span>      | <span data-ttu-id="0f9b6-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0f9b6-132">Description</span></span>
:------     | :-----
<span data-ttu-id="0f9b6-133">200</span><span class="sxs-lookup"><span data-stu-id="0f9b6-133">200</span></span> | <span data-ttu-id="0f9b6-134">Die Anforderung war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="0f9b6-134">Request was successful</span></span>
<span data-ttu-id="0f9b6-135">4XX</span><span class="sxs-lookup"><span data-stu-id="0f9b6-135">4XX</span></span> | <span data-ttu-id="0f9b6-136">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="0f9b6-136">Error codes</span></span>
<span data-ttu-id="0f9b6-137">5XX</span><span class="sxs-lookup"><span data-stu-id="0f9b6-137">5XX</span></span> | <span data-ttu-id="0f9b6-138">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="0f9b6-138">Error codes</span></span>

<br />
**<span data-ttu-id="0f9b6-139">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="0f9b6-139">Available device families</span></span>**

* <span data-ttu-id="0f9b6-140">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="0f9b6-140">Windows Xbox</span></span>