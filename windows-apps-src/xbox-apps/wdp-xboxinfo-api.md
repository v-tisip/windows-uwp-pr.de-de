---
author: M-Stahl
title: Portal Xbox Geräteinformationen-API-Referenz
description: Erfahren Sie, wie Xbox Geräteinformationen zugreifen.
ms.author: mstahl
ms.date: 11/7/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Xbox Gerät portal
ms.localizationpriority: medium
ms.openlocfilehash: db1df2418a2bb60de4a72f51ad01a0bfd547ec20
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "406259"
---
# <a name="xbox-info-api-reference"></a><span data-ttu-id="fbcce-104">Xbox Info-API-Referenz</span><span class="sxs-lookup"><span data-stu-id="fbcce-104">Xbox Info API reference</span></span>   
<span data-ttu-id="fbcce-105">Sie können eine Xbox Geräteinformationen mit dieser API zugreifen.</span><span class="sxs-lookup"><span data-stu-id="fbcce-105">You can access Xbox One device information using this API.</span></span>

## <a name="get-xbox-one-device-information"></a><span data-ttu-id="fbcce-106">Abrufen von Informationen für eine Xbox Gerät</span><span class="sxs-lookup"><span data-stu-id="fbcce-106">Get Xbox One device information</span></span>

**<span data-ttu-id="fbcce-107">Anforderung</span><span class="sxs-lookup"><span data-stu-id="fbcce-107">Request</span></span>**

<span data-ttu-id="fbcce-108">Sie können die Geräteinformationen zu Ihrer Xbox eine abrufen.</span><span class="sxs-lookup"><span data-stu-id="fbcce-108">You can get device information about your Xbox One.</span></span>

<span data-ttu-id="fbcce-109">Methode</span><span class="sxs-lookup"><span data-stu-id="fbcce-109">Method</span></span>      | <span data-ttu-id="fbcce-110">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="fbcce-110">Request URI</span></span>
:------     | :-----
<span data-ttu-id="fbcce-111">GET</span><span class="sxs-lookup"><span data-stu-id="fbcce-111">GET</span></span> | <span data-ttu-id="fbcce-112">/ext/xbox/info</span><span class="sxs-lookup"><span data-stu-id="fbcce-112">/ext/xbox/info</span></span>
<br />
**<span data-ttu-id="fbcce-113">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="fbcce-113">URI parameters</span></span>**

- <span data-ttu-id="fbcce-114">Keine</span><span class="sxs-lookup"><span data-stu-id="fbcce-114">None</span></span>

**<span data-ttu-id="fbcce-115">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="fbcce-115">Request headers</span></span>**

- <span data-ttu-id="fbcce-116">Keine</span><span class="sxs-lookup"><span data-stu-id="fbcce-116">None</span></span>

**<span data-ttu-id="fbcce-117">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="fbcce-117">Request body</span></span>**

- <span data-ttu-id="fbcce-118">Keine</span><span class="sxs-lookup"><span data-stu-id="fbcce-118">None</span></span>

**<span data-ttu-id="fbcce-119">Antwort</span><span class="sxs-lookup"><span data-stu-id="fbcce-119">Response</span></span>**   
<span data-ttu-id="fbcce-120">Ein JSON-Objekt mit den folgenden Feldern:</span><span class="sxs-lookup"><span data-stu-id="fbcce-120">A JSON object with the following fields:</span></span>

* <span data-ttu-id="fbcce-121">OsVersion - (Zeichenfolge) die Version des Betriebssystems.</span><span class="sxs-lookup"><span data-stu-id="fbcce-121">OsVersion - (String) The version of the OS.</span></span>
* <span data-ttu-id="fbcce-122">OsEdition - (Zeichenfolge) die Version des Betriebssystems, beispielsweise "März 2017" oder "März 2017 QFE 1".</span><span class="sxs-lookup"><span data-stu-id="fbcce-122">OsEdition - (String) The edition of the OS, such as "March 2017" or "March 2017 QFE 1".</span></span>
* <span data-ttu-id="fbcce-123">ConsoleId - ID (Zeichenfolge) der Konsole des</span><span class="sxs-lookup"><span data-stu-id="fbcce-123">ConsoleId - (String) The console's ID.</span></span>
* <span data-ttu-id="fbcce-124">Geräte-ID - (String) der Konsole des Xbox Live Gerät Id.</span><span class="sxs-lookup"><span data-stu-id="fbcce-124">DeviceId - (String) The console's Xbox Live Device Id.</span></span>
* <span data-ttu-id="fbcce-125">SerialNumber - Seriennummer (String) der Konsole des.</span><span class="sxs-lookup"><span data-stu-id="fbcce-125">SerialNumber - (String) The console's serial number.</span></span>
* <span data-ttu-id="fbcce-126">DevMode - (String) der Konsole des aktuellen Entwicklermodus, beispielsweise "None" oder "Retail".</span><span class="sxs-lookup"><span data-stu-id="fbcce-126">DevMode - (String) The console's current developer mode, such as "None" or "Retail".</span></span>
* <span data-ttu-id="fbcce-127">ConsoleType - (String) der Konsole des Typs, beispielsweise "Xbox ein" oder "Xbox ein S".</span><span class="sxs-lookup"><span data-stu-id="fbcce-127">ConsoleType - (String) The console's type, such as "Xbox One" or "Xbox One S".</span></span>
* <span data-ttu-id="fbcce-128">DevkitCertificateExpirationTime - (Anzahl) der UTC-Zeit in Sekunden, wenn die Konsole Developer Kit Zertifikat abläuft.</span><span class="sxs-lookup"><span data-stu-id="fbcce-128">DevkitCertificateExpirationTime - (Number) The UTC Time in seconds when the console's developer kit certificate will expire.</span></span>

**<span data-ttu-id="fbcce-129">Statuscode</span><span class="sxs-lookup"><span data-stu-id="fbcce-129">Status code</span></span>**

<span data-ttu-id="fbcce-130">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="fbcce-130">This API has the following expected status codes.</span></span>

<span data-ttu-id="fbcce-131">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="fbcce-131">HTTP status code</span></span>      | <span data-ttu-id="fbcce-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="fbcce-132">Description</span></span>
:------     | :-----
<span data-ttu-id="fbcce-133">200</span><span class="sxs-lookup"><span data-stu-id="fbcce-133">200</span></span> | <span data-ttu-id="fbcce-134">Die Anforderung war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="fbcce-134">Request was successful</span></span>
<span data-ttu-id="fbcce-135">4XX</span><span class="sxs-lookup"><span data-stu-id="fbcce-135">4XX</span></span> | <span data-ttu-id="fbcce-136">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="fbcce-136">Error codes</span></span>
<span data-ttu-id="fbcce-137">5XX</span><span class="sxs-lookup"><span data-stu-id="fbcce-137">5XX</span></span> | <span data-ttu-id="fbcce-138">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="fbcce-138">Error codes</span></span>

<br />
**<span data-ttu-id="fbcce-139">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="fbcce-139">Available device families</span></span>**

* <span data-ttu-id="fbcce-140">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="fbcce-140">Windows Xbox</span></span>