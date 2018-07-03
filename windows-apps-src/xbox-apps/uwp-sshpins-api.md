---
author: WilliamsJason
title: Geräteportal-SSH-PINs– API-Referenz
description: Hier erfahren Sie, wie alle vertrauenswürdigen SSH-PINs programmgesteuert entfernt werden.
ms.localizationpriority: medium
ms.openlocfilehash: 88ba9d3e35650c8c581b9ddb76911636fc18c72e
ms.sourcegitcommit: c104b653601d9b81cfc8bb6032ca434cff8fe9b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2018
ms.locfileid: "1921247"
---
# <a name="ssh-pins-api-reference"></a><span data-ttu-id="7cf07-103">SSH-PINs– API-Referenz</span><span class="sxs-lookup"><span data-stu-id="7cf07-103">SSH Pins API reference</span></span>
<span data-ttu-id="7cf07-104">Sie können alle vertrauenswürdigen SSH-PINs in Ihrem Entwickler-Kit mit dieser REST-API entfernen.</span><span class="sxs-lookup"><span data-stu-id="7cf07-104">You can remove all trusted SSH pins on your devkit using this REST API.</span></span>

## <a name="remove-trusted-ssh-pins"></a><span data-ttu-id="7cf07-105">Entfernen von vertrauenswürdigen SSH-PINs</span><span class="sxs-lookup"><span data-stu-id="7cf07-105">Remove trusted SSH pins</span></span>

**<span data-ttu-id="7cf07-106">Anforderung</span><span class="sxs-lookup"><span data-stu-id="7cf07-106">Request</span></span>**

<span data-ttu-id="7cf07-107">Methode</span><span class="sxs-lookup"><span data-stu-id="7cf07-107">Method</span></span>      | <span data-ttu-id="7cf07-108">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="7cf07-108">Request URI</span></span>
:------     | :-----
<span data-ttu-id="7cf07-109">DELETE</span><span class="sxs-lookup"><span data-stu-id="7cf07-109">DELETE</span></span> | <span data-ttu-id="7cf07-110">/ext/App/sshpins</span><span class="sxs-lookup"><span data-stu-id="7cf07-110">/ext/app/sshpins</span></span>
<br />
**<span data-ttu-id="7cf07-111">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="7cf07-111">URI parameters</span></span>**

- <span data-ttu-id="7cf07-112">Keine</span><span class="sxs-lookup"><span data-stu-id="7cf07-112">None</span></span>

**<span data-ttu-id="7cf07-113">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="7cf07-113">Request headers</span></span>**

- <span data-ttu-id="7cf07-114">Keiner</span><span class="sxs-lookup"><span data-stu-id="7cf07-114">None</span></span>

**<span data-ttu-id="7cf07-115">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="7cf07-115">Request body</span></span>**   

- <span data-ttu-id="7cf07-116">Keine</span><span class="sxs-lookup"><span data-stu-id="7cf07-116">None</span></span>

**<span data-ttu-id="7cf07-117">Antwort</span><span class="sxs-lookup"><span data-stu-id="7cf07-117">Response</span></span>**   

- <span data-ttu-id="7cf07-118">Keine</span><span class="sxs-lookup"><span data-stu-id="7cf07-118">None</span></span> 

**<span data-ttu-id="7cf07-119">Statuscode</span><span class="sxs-lookup"><span data-stu-id="7cf07-119">Status code</span></span>**

<span data-ttu-id="7cf07-120">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="7cf07-120">This API has the following expected status codes.</span></span>

<span data-ttu-id="7cf07-121">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="7cf07-121">HTTP status code</span></span>      | <span data-ttu-id="7cf07-122">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7cf07-122">Description</span></span>
:------     | :-----
<span data-ttu-id="7cf07-123">204</span><span class="sxs-lookup"><span data-stu-id="7cf07-123">204</span></span> | <span data-ttu-id="7cf07-124">Die Anforderung zum Löschen der PINs war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="7cf07-124">The request to clear the pins was successful.</span></span>
<span data-ttu-id="7cf07-125">4XX</span><span class="sxs-lookup"><span data-stu-id="7cf07-125">4XX</span></span> | <span data-ttu-id="7cf07-126">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="7cf07-126">Error codes</span></span>
<span data-ttu-id="7cf07-127">5XX</span><span class="sxs-lookup"><span data-stu-id="7cf07-127">5XX</span></span> | <span data-ttu-id="7cf07-128">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="7cf07-128">Error codes</span></span>

<br />
**<span data-ttu-id="7cf07-129">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="7cf07-129">Available device families</span></span>**

* <span data-ttu-id="7cf07-130">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="7cf07-130">Windows Xbox</span></span>

