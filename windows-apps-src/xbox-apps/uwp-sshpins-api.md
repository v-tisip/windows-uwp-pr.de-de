---
title: Geräteportal-SSH-PINs– API-Referenz
description: Hier erfahren Sie, wie alle vertrauenswürdigen SSH-PINs programmgesteuert entfernt werden.
ms.localizationpriority: medium
ms.topic: article
ms.date: 02/08/2017
ms.openlocfilehash: 2c7dc6fab021c11c98276ee53af161bea25601a9
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8779120"
---
# <a name="ssh-pins-api-reference"></a><span data-ttu-id="c78b7-103">SSH-PINs– API-Referenz</span><span class="sxs-lookup"><span data-stu-id="c78b7-103">SSH Pins API reference</span></span>
<span data-ttu-id="c78b7-104">Sie können alle vertrauenswürdigen SSH-PINs in Ihrem Entwickler-Kit mit dieser REST-API entfernen.</span><span class="sxs-lookup"><span data-stu-id="c78b7-104">You can remove all trusted SSH pins on your devkit using this REST API.</span></span>

## <a name="remove-trusted-ssh-pins"></a><span data-ttu-id="c78b7-105">Entfernen von vertrauenswürdigen SSH-PINs</span><span class="sxs-lookup"><span data-stu-id="c78b7-105">Remove trusted SSH pins</span></span>

**<span data-ttu-id="c78b7-106">Anforderung</span><span class="sxs-lookup"><span data-stu-id="c78b7-106">Request</span></span>**

<span data-ttu-id="c78b7-107">Methode</span><span class="sxs-lookup"><span data-stu-id="c78b7-107">Method</span></span>      | <span data-ttu-id="c78b7-108">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="c78b7-108">Request URI</span></span>
:------     | :-----
<span data-ttu-id="c78b7-109">DELETE</span><span class="sxs-lookup"><span data-stu-id="c78b7-109">DELETE</span></span> | <span data-ttu-id="c78b7-110">/ext/App/sshpins</span><span class="sxs-lookup"><span data-stu-id="c78b7-110">/ext/app/sshpins</span></span>
<br />
**<span data-ttu-id="c78b7-111">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="c78b7-111">URI parameters</span></span>**

- <span data-ttu-id="c78b7-112">Keine</span><span class="sxs-lookup"><span data-stu-id="c78b7-112">None</span></span>

**<span data-ttu-id="c78b7-113">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="c78b7-113">Request headers</span></span>**

- <span data-ttu-id="c78b7-114">Keiner</span><span class="sxs-lookup"><span data-stu-id="c78b7-114">None</span></span>

**<span data-ttu-id="c78b7-115">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="c78b7-115">Request body</span></span>**   

- <span data-ttu-id="c78b7-116">Keine</span><span class="sxs-lookup"><span data-stu-id="c78b7-116">None</span></span>

**<span data-ttu-id="c78b7-117">Antwort</span><span class="sxs-lookup"><span data-stu-id="c78b7-117">Response</span></span>**   

- <span data-ttu-id="c78b7-118">Keine</span><span class="sxs-lookup"><span data-stu-id="c78b7-118">None</span></span> 

**<span data-ttu-id="c78b7-119">Statuscode</span><span class="sxs-lookup"><span data-stu-id="c78b7-119">Status code</span></span>**

<span data-ttu-id="c78b7-120">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="c78b7-120">This API has the following expected status codes.</span></span>

<span data-ttu-id="c78b7-121">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="c78b7-121">HTTP status code</span></span>      | <span data-ttu-id="c78b7-122">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c78b7-122">Description</span></span>
:------     | :-----
<span data-ttu-id="c78b7-123">204</span><span class="sxs-lookup"><span data-stu-id="c78b7-123">204</span></span> | <span data-ttu-id="c78b7-124">Die Anforderung zum Löschen der PINs war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="c78b7-124">The request to clear the pins was successful.</span></span>
<span data-ttu-id="c78b7-125">4XX</span><span class="sxs-lookup"><span data-stu-id="c78b7-125">4XX</span></span> | <span data-ttu-id="c78b7-126">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="c78b7-126">Error codes</span></span>
<span data-ttu-id="c78b7-127">5XX</span><span class="sxs-lookup"><span data-stu-id="c78b7-127">5XX</span></span> | <span data-ttu-id="c78b7-128">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="c78b7-128">Error codes</span></span>

<br />
**<span data-ttu-id="c78b7-129">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="c78b7-129">Available device families</span></span>**

* <span data-ttu-id="c78b7-130">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="c78b7-130">Windows Xbox</span></span>

