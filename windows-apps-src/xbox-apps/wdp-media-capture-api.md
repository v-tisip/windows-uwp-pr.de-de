---
author: WilliamsJason
title: Referenz zur Medienerfassungs-API
description: Erfahren Sie, wie Sie programmgesteuert auf die Medienerfassungs-API zugreifen.
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.assetid: 3f92c8fd-4096-4972-97da-01ae5db6423c
ms.localizationpriority: medium
ms.openlocfilehash: f58fa4c3a9a1abd407f635f27de3a545c3aafc6c
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7556553"
---
# <a name="media-capture-api-reference"></a><span data-ttu-id="29e79-104">Referenz zur Medienerfassungs-API</span><span class="sxs-lookup"><span data-stu-id="29e79-104">Media Capture API reference</span></span> #

**<span data-ttu-id="29e79-105">Anforderung</span><span class="sxs-lookup"><span data-stu-id="29e79-105">Request</span></span>**

<span data-ttu-id="29e79-106">Mithilfe des folgenden Anforderungsformats können Sie eine PNG-Darstellung des aktuellen Bildschirms erfassen.</span><span class="sxs-lookup"><span data-stu-id="29e79-106">You can capture a PNG representation of the current screen by using the following request format.</span></span>

| <span data-ttu-id="29e79-107">Methode</span><span class="sxs-lookup"><span data-stu-id="29e79-107">Method</span></span>        | <span data-ttu-id="29e79-108">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="29e79-108">Request URI</span></span>     | 
| ------------- |-----------------|
| <span data-ttu-id="29e79-109">GET</span><span class="sxs-lookup"><span data-stu-id="29e79-109">GET</span></span>           | <span data-ttu-id="29e79-110">/ext/screenshot</span><span class="sxs-lookup"><span data-stu-id="29e79-110">/ext/screenshot</span></span> |
<br>

**<span data-ttu-id="29e79-111">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="29e79-111">URI parameters</span></span>**

<span data-ttu-id="29e79-112">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="29e79-112">You can specify the following additional parameters on the request URI:</span></span>


| <span data-ttu-id="29e79-113">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="29e79-113">URI parameter</span></span>      | <span data-ttu-id="29e79-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="29e79-114">Description</span></span>     | 
| ------------------ |-----------------|
| <span data-ttu-id="29e79-115">download (optional)</span><span class="sxs-lookup"><span data-stu-id="29e79-115">download (optional)</span></span>| <span data-ttu-id="29e79-116">Ein boolescher Wert, der angibt, ob HTTP-Antwortheader festgelegt werden sollen, die angeben, dass der Hostbrowser den Screenshot als Anhang herunterladen soll, anstatt ihn im Browser zu rendern.</span><span class="sxs-lookup"><span data-stu-id="29e79-116">A boolean value indicating if HTTP response headers should be set indicating that the host browser should download the screenshot as an attachment rather than rendering it in the browser.</span></span>  |
<br>

**<span data-ttu-id="29e79-117">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="29e79-117">Request headers</span></span>**

* <span data-ttu-id="29e79-118">Keine</span><span class="sxs-lookup"><span data-stu-id="29e79-118">None</span></span>

**<span data-ttu-id="29e79-119">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="29e79-119">Request body</span></span>**

* <span data-ttu-id="29e79-120">Keine</span><span class="sxs-lookup"><span data-stu-id="29e79-120">None</span></span>

###<a name="response"></a><span data-ttu-id="29e79-121">Antwort ###</span><span class="sxs-lookup"><span data-stu-id="29e79-121">Response###</span></span>

**<span data-ttu-id="29e79-122">Statuscode</span><span class="sxs-lookup"><span data-stu-id="29e79-122">Status code</span></span>**

<span data-ttu-id="29e79-123">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="29e79-123">This API has the following expected status codes.</span></span>

| <span data-ttu-id="29e79-124">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="29e79-124">HTTP status code</span></span>   | <span data-ttu-id="29e79-125">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="29e79-125">Description</span></span>     | 
| ------------------ |-----------------|
| <span data-ttu-id="29e79-126">200</span><span class="sxs-lookup"><span data-stu-id="29e79-126">200</span></span>                | <span data-ttu-id="29e79-127">Die Screenshotanforderung war erfolgreich, und der erfasste Inhalt wurde zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="29e79-127">Screenshot request successful and capture returned</span></span> |
| <span data-ttu-id="29e79-128">5XX</span><span class="sxs-lookup"><span data-stu-id="29e79-128">5XX</span></span>                | <span data-ttu-id="29e79-129">Fehlercodes für unerwartete Fehler</span><span class="sxs-lookup"><span data-stu-id="29e79-129">Error codes for unexpected failures</span></span> |
<br>

**<span data-ttu-id="29e79-130">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="29e79-130">Available device families</span></span>**

* <span data-ttu-id="29e79-131">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="29e79-131">Windows Xbox</span></span>

