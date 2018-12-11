---
title: Referenz zur Medienerfassungs-API
description: Erfahren Sie, wie Sie programmgesteuert auf die Medienerfassungs-API zugreifen.
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.assetid: 3f92c8fd-4096-4972-97da-01ae5db6423c
ms.localizationpriority: medium
ms.openlocfilehash: 7a27d13f7ceedd14a84d5b4b4aa1233445037a1f
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8887627"
---
# <a name="media-capture-api-reference"></a><span data-ttu-id="0575d-104">Referenz zur Medienerfassungs-API</span><span class="sxs-lookup"><span data-stu-id="0575d-104">Media Capture API reference</span></span> #

**<span data-ttu-id="0575d-105">Anforderung</span><span class="sxs-lookup"><span data-stu-id="0575d-105">Request</span></span>**

<span data-ttu-id="0575d-106">Mithilfe des folgenden Anforderungsformats können Sie eine PNG-Darstellung des aktuellen Bildschirms erfassen.</span><span class="sxs-lookup"><span data-stu-id="0575d-106">You can capture a PNG representation of the current screen by using the following request format.</span></span>

| <span data-ttu-id="0575d-107">Methode</span><span class="sxs-lookup"><span data-stu-id="0575d-107">Method</span></span>        | <span data-ttu-id="0575d-108">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="0575d-108">Request URI</span></span>     | 
| ------------- |-----------------|
| <span data-ttu-id="0575d-109">GET</span><span class="sxs-lookup"><span data-stu-id="0575d-109">GET</span></span>           | <span data-ttu-id="0575d-110">/ext/screenshot</span><span class="sxs-lookup"><span data-stu-id="0575d-110">/ext/screenshot</span></span> |
<br>

**<span data-ttu-id="0575d-111">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="0575d-111">URI parameters</span></span>**

<span data-ttu-id="0575d-112">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="0575d-112">You can specify the following additional parameters on the request URI:</span></span>


| <span data-ttu-id="0575d-113">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="0575d-113">URI parameter</span></span>      | <span data-ttu-id="0575d-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0575d-114">Description</span></span>     | 
| ------------------ |-----------------|
| <span data-ttu-id="0575d-115">download (optional)</span><span class="sxs-lookup"><span data-stu-id="0575d-115">download (optional)</span></span>| <span data-ttu-id="0575d-116">Ein boolescher Wert, der angibt, ob HTTP-Antwortheader festgelegt werden sollen, die angeben, dass der Hostbrowser den Screenshot als Anhang herunterladen soll, anstatt ihn im Browser zu rendern.</span><span class="sxs-lookup"><span data-stu-id="0575d-116">A boolean value indicating if HTTP response headers should be set indicating that the host browser should download the screenshot as an attachment rather than rendering it in the browser.</span></span>  |
<br>

**<span data-ttu-id="0575d-117">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="0575d-117">Request headers</span></span>**

* <span data-ttu-id="0575d-118">Keine</span><span class="sxs-lookup"><span data-stu-id="0575d-118">None</span></span>

**<span data-ttu-id="0575d-119">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="0575d-119">Request body</span></span>**

* <span data-ttu-id="0575d-120">Keine</span><span class="sxs-lookup"><span data-stu-id="0575d-120">None</span></span>

###<a name="response"></a><span data-ttu-id="0575d-121">Antwort ###</span><span class="sxs-lookup"><span data-stu-id="0575d-121">Response###</span></span>

**<span data-ttu-id="0575d-122">Statuscode</span><span class="sxs-lookup"><span data-stu-id="0575d-122">Status code</span></span>**

<span data-ttu-id="0575d-123">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="0575d-123">This API has the following expected status codes.</span></span>

| <span data-ttu-id="0575d-124">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="0575d-124">HTTP status code</span></span>   | <span data-ttu-id="0575d-125">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0575d-125">Description</span></span>     | 
| ------------------ |-----------------|
| <span data-ttu-id="0575d-126">200</span><span class="sxs-lookup"><span data-stu-id="0575d-126">200</span></span>                | <span data-ttu-id="0575d-127">Die Screenshotanforderung war erfolgreich, und der erfasste Inhalt wurde zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="0575d-127">Screenshot request successful and capture returned</span></span> |
| <span data-ttu-id="0575d-128">5XX</span><span class="sxs-lookup"><span data-stu-id="0575d-128">5XX</span></span>                | <span data-ttu-id="0575d-129">Fehlercodes für unerwartete Fehler</span><span class="sxs-lookup"><span data-stu-id="0575d-129">Error codes for unexpected failures</span></span> |
<br>

**<span data-ttu-id="0575d-130">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="0575d-130">Available device families</span></span>**

* <span data-ttu-id="0575d-131">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="0575d-131">Windows Xbox</span></span>

