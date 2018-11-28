---
title: Geräteportal-SSH-PINs– API-Referenz
description: Hier erfahren Sie, wie alle vertrauenswürdigen SSH-PINs programmgesteuert entfernt werden.
ms.localizationpriority: medium
ms.openlocfilehash: 1ddf15d3cdb4089a8ef010a4ae46d247a06a10d7
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "7848189"
---
# <a name="ssh-pins-api-reference"></a><span data-ttu-id="dd597-103">SSH-PINs– API-Referenz</span><span class="sxs-lookup"><span data-stu-id="dd597-103">SSH Pins API reference</span></span>
<span data-ttu-id="dd597-104">Sie können alle vertrauenswürdigen SSH-PINs in Ihrem Entwickler-Kit mit dieser REST-API entfernen.</span><span class="sxs-lookup"><span data-stu-id="dd597-104">You can remove all trusted SSH pins on your devkit using this REST API.</span></span>

## <a name="remove-trusted-ssh-pins"></a><span data-ttu-id="dd597-105">Entfernen von vertrauenswürdigen SSH-PINs</span><span class="sxs-lookup"><span data-stu-id="dd597-105">Remove trusted SSH pins</span></span>

**<span data-ttu-id="dd597-106">Anforderung</span><span class="sxs-lookup"><span data-stu-id="dd597-106">Request</span></span>**

<span data-ttu-id="dd597-107">Methode</span><span class="sxs-lookup"><span data-stu-id="dd597-107">Method</span></span>      | <span data-ttu-id="dd597-108">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="dd597-108">Request URI</span></span>
:------     | :-----
<span data-ttu-id="dd597-109">DELETE</span><span class="sxs-lookup"><span data-stu-id="dd597-109">DELETE</span></span> | <span data-ttu-id="dd597-110">/ext/App/sshpins</span><span class="sxs-lookup"><span data-stu-id="dd597-110">/ext/app/sshpins</span></span>
<br />
**<span data-ttu-id="dd597-111">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="dd597-111">URI parameters</span></span>**

- <span data-ttu-id="dd597-112">Keine</span><span class="sxs-lookup"><span data-stu-id="dd597-112">None</span></span>

**<span data-ttu-id="dd597-113">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="dd597-113">Request headers</span></span>**

- <span data-ttu-id="dd597-114">Keiner</span><span class="sxs-lookup"><span data-stu-id="dd597-114">None</span></span>

**<span data-ttu-id="dd597-115">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="dd597-115">Request body</span></span>**   

- <span data-ttu-id="dd597-116">Keine</span><span class="sxs-lookup"><span data-stu-id="dd597-116">None</span></span>

**<span data-ttu-id="dd597-117">Antwort</span><span class="sxs-lookup"><span data-stu-id="dd597-117">Response</span></span>**   

- <span data-ttu-id="dd597-118">Keine</span><span class="sxs-lookup"><span data-stu-id="dd597-118">None</span></span> 

**<span data-ttu-id="dd597-119">Statuscode</span><span class="sxs-lookup"><span data-stu-id="dd597-119">Status code</span></span>**

<span data-ttu-id="dd597-120">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="dd597-120">This API has the following expected status codes.</span></span>

<span data-ttu-id="dd597-121">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="dd597-121">HTTP status code</span></span>      | <span data-ttu-id="dd597-122">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="dd597-122">Description</span></span>
:------     | :-----
<span data-ttu-id="dd597-123">204</span><span class="sxs-lookup"><span data-stu-id="dd597-123">204</span></span> | <span data-ttu-id="dd597-124">Die Anforderung zum Löschen der PINs war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="dd597-124">The request to clear the pins was successful.</span></span>
<span data-ttu-id="dd597-125">4XX</span><span class="sxs-lookup"><span data-stu-id="dd597-125">4XX</span></span> | <span data-ttu-id="dd597-126">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="dd597-126">Error codes</span></span>
<span data-ttu-id="dd597-127">5XX</span><span class="sxs-lookup"><span data-stu-id="dd597-127">5XX</span></span> | <span data-ttu-id="dd597-128">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="dd597-128">Error codes</span></span>

<br />
**<span data-ttu-id="dd597-129">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="dd597-129">Available device families</span></span>**

* <span data-ttu-id="dd597-130">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="dd597-130">Windows Xbox</span></span>

