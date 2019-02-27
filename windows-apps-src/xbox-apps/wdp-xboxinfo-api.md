---
title: Xbox-Portal Geräteinformationen-API-Referenz
description: Erfahren Sie, wie auf Xbox-Informationen zugreifen.
ms.date: 11/072017
ms.topic: article
keywords: Windows 10, Uwp, Xbox, geräteportal
ms.localizationpriority: medium
ms.openlocfilehash: 85c2c139aa8064e1f0769064b95eeb531086b8c1
ms.sourcegitcommit: 079801609165bc7eb69670d771a05bffe236d483
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/27/2019
ms.locfileid: "9115980"
---
# <a name="xbox-info-api-reference"></a><span data-ttu-id="005a8-104">Xbox-Info-API-Referenz</span><span class="sxs-lookup"><span data-stu-id="005a8-104">Xbox Info API reference</span></span>   
<span data-ttu-id="005a8-105">Sie können die Xbox One Geräteinformationen mithilfe dieser API zugreifen.</span><span class="sxs-lookup"><span data-stu-id="005a8-105">You can access Xbox One device information using this API.</span></span>

## <a name="get-xbox-one-device-information"></a><span data-ttu-id="005a8-106">Abrufen von Xbox One Geräteinformationen</span><span class="sxs-lookup"><span data-stu-id="005a8-106">Get Xbox One device information</span></span>

**<span data-ttu-id="005a8-107">Anforderung</span><span class="sxs-lookup"><span data-stu-id="005a8-107">Request</span></span>**

<span data-ttu-id="005a8-108">Sie erhalten Informationen über Ihre Xbox One.</span><span class="sxs-lookup"><span data-stu-id="005a8-108">You can get device information about your Xbox One.</span></span>

<span data-ttu-id="005a8-109">Methode</span><span class="sxs-lookup"><span data-stu-id="005a8-109">Method</span></span>      | <span data-ttu-id="005a8-110">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="005a8-110">Request URI</span></span>
:------     | :-----
<span data-ttu-id="005a8-111">GET</span><span class="sxs-lookup"><span data-stu-id="005a8-111">GET</span></span> | <span data-ttu-id="005a8-112">/ext/xbox/info</span><span class="sxs-lookup"><span data-stu-id="005a8-112">/ext/xbox/info</span></span>
<br />
**<span data-ttu-id="005a8-113">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="005a8-113">URI parameters</span></span>**

- <span data-ttu-id="005a8-114">Keine</span><span class="sxs-lookup"><span data-stu-id="005a8-114">None</span></span>

**<span data-ttu-id="005a8-115">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="005a8-115">Request headers</span></span>**

- <span data-ttu-id="005a8-116">Keiner</span><span class="sxs-lookup"><span data-stu-id="005a8-116">None</span></span>

**<span data-ttu-id="005a8-117">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="005a8-117">Request body</span></span>**

- <span data-ttu-id="005a8-118">Keine</span><span class="sxs-lookup"><span data-stu-id="005a8-118">None</span></span>

**<span data-ttu-id="005a8-119">Antwort</span><span class="sxs-lookup"><span data-stu-id="005a8-119">Response</span></span>**   
<span data-ttu-id="005a8-120">Ein JSON-Objekt mit den folgenden Feldern:</span><span class="sxs-lookup"><span data-stu-id="005a8-120">A JSON object with the following fields:</span></span>

* <span data-ttu-id="005a8-121">OsVersion - (Zeichenfolge) die Version des Betriebssystems.</span><span class="sxs-lookup"><span data-stu-id="005a8-121">OsVersion - (String) The version of the OS.</span></span>
* <span data-ttu-id="005a8-122">OsEdition - (Zeichenfolge) die Edition des Betriebssystems, z. B. "März 2017" oder "März 2017 QFE 1".</span><span class="sxs-lookup"><span data-stu-id="005a8-122">OsEdition - (String) The edition of the OS, such as "March 2017" or "March 2017 QFE 1".</span></span>
* <span data-ttu-id="005a8-123">ConsoleId - (Zeichenfolge) die Konsole des-ID.</span><span class="sxs-lookup"><span data-stu-id="005a8-123">ConsoleId - (String) The console's ID.</span></span>
* <span data-ttu-id="005a8-124">Geräte-ID - (Zeichenfolge) die Konsole des Xbox Live Gerät ID</span><span class="sxs-lookup"><span data-stu-id="005a8-124">DeviceId - (String) The console's Xbox Live Device Id.</span></span>
* <span data-ttu-id="005a8-125">Seriennummer - (Zeichenfolge) die Konsole des Seriennummer.</span><span class="sxs-lookup"><span data-stu-id="005a8-125">SerialNumber - (String) The console's serial number.</span></span>
* <span data-ttu-id="005a8-126">DevMode - (Zeichenfolge) die Konsole des aktuellen Entwicklermodus, z. B. "None" oder "Retail".</span><span class="sxs-lookup"><span data-stu-id="005a8-126">DevMode - (String) The console's current developer mode, such as "None" or "Retail".</span></span>
* <span data-ttu-id="005a8-127">ConsoleType - (Zeichenfolge) die Konsole des Typ, z. B. "Xbox One" oder "Xbox One S".</span><span class="sxs-lookup"><span data-stu-id="005a8-127">ConsoleType - (String) The console's type, such as "Xbox One" or "Xbox One S".</span></span>
* <span data-ttu-id="005a8-128">DevkitCertificateExpirationTime – (Number) der UTC-Zeit in Sekunden, wenn die Konsole Developer Kit Zertifikat abläuft.</span><span class="sxs-lookup"><span data-stu-id="005a8-128">DevkitCertificateExpirationTime - (Number) The UTC Time in seconds when the console's developer kit certificate will expire.</span></span>

**<span data-ttu-id="005a8-129">Statuscode</span><span class="sxs-lookup"><span data-stu-id="005a8-129">Status code</span></span>**

<span data-ttu-id="005a8-130">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="005a8-130">This API has the following expected status codes.</span></span>

<span data-ttu-id="005a8-131">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="005a8-131">HTTP status code</span></span>      | <span data-ttu-id="005a8-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="005a8-132">Description</span></span>
:------     | :-----
<span data-ttu-id="005a8-133">200</span><span class="sxs-lookup"><span data-stu-id="005a8-133">200</span></span> | <span data-ttu-id="005a8-134">Die Anforderung war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="005a8-134">Request was successful</span></span>
<span data-ttu-id="005a8-135">4XX</span><span class="sxs-lookup"><span data-stu-id="005a8-135">4XX</span></span> | <span data-ttu-id="005a8-136">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="005a8-136">Error codes</span></span>
<span data-ttu-id="005a8-137">5XX</span><span class="sxs-lookup"><span data-stu-id="005a8-137">5XX</span></span> | <span data-ttu-id="005a8-138">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="005a8-138">Error codes</span></span>

<br />
**<span data-ttu-id="005a8-139">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="005a8-139">Available device families</span></span>**

* <span data-ttu-id="005a8-140">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="005a8-140">Windows Xbox</span></span>