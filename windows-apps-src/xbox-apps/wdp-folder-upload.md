---
author: WilliamsJason
title: Device Portal - Referenz zu den APIs zum Hochladen von Ordnern
description: Erfahren Sie, wie Sie programmgesteuert auf die APIs zum Hochladen von Ordnern zugreifen.
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.assetid: e1a2c7f0-0040-4ce7-94de-17224736e20b
ms.localizationpriority: medium
ms.openlocfilehash: 481ec666c327b15088d8e60577c51fa1697918fe
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "5934081"
---
# <a name="upload-a-folder-to-the-development-directory"></a><span data-ttu-id="3569b-104">Hochladen eines Ordners in das Entwicklungsverzeichnis</span><span class="sxs-lookup"><span data-stu-id="3569b-104">Upload a folder to the development directory</span></span>

**<span data-ttu-id="3569b-105">Anforderung</span><span class="sxs-lookup"><span data-stu-id="3569b-105">Request</span></span>**

<span data-ttu-id="3569b-106">Sie können einen vollständigen Ordner unter der ID für bekannte Ordner in den Ordner „DevelopmentFiles“ (oder in einen Unterordner innerhalb dieses Ordners) auf einmal hochladen.</span><span class="sxs-lookup"><span data-stu-id="3569b-106">You can upload an entire folder at once to the Known Folder Id for the DevelopmentFiles (or to a subfolder within that folder).</span></span>

<span data-ttu-id="3569b-107">Methode</span><span class="sxs-lookup"><span data-stu-id="3569b-107">Method</span></span>      | <span data-ttu-id="3569b-108">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="3569b-108">Request URI</span></span>
:------     | :------
<span data-ttu-id="3569b-109">POST</span><span class="sxs-lookup"><span data-stu-id="3569b-109">POST</span></span> | <span data-ttu-id="3569b-110">/api/app/packagemanager/upload</span><span class="sxs-lookup"><span data-stu-id="3569b-110">/api/app/packagemanager/upload</span></span> 
<br />
**<span data-ttu-id="3569b-111">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="3569b-111">URI parameters</span></span>**

<span data-ttu-id="3569b-112">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="3569b-112">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="3569b-113">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="3569b-113">URI Parameter</span></span>      | <span data-ttu-id="3569b-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3569b-114">Description</span></span>
:------     | :-----
<span data-ttu-id="3569b-115">destinationFolder (erforderlich)</span><span class="sxs-lookup"><span data-stu-id="3569b-115">destinationFolder  (required)</span></span> | <span data-ttu-id="3569b-116">Der Name des Zielordners für den Ordner, der hochgeladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="3569b-116">The destination folder name of the folder to be uploaded.</span></span> <span data-ttu-id="3569b-117">Dieser Ordner wird unter „d:\developmentfiles\LooseApps“ auf der Konsole gespeichert.</span><span class="sxs-lookup"><span data-stu-id="3569b-117">This folder will be placed under d:\developmentfiles\LooseApps on the console.</span></span> <span data-ttu-id="3569b-118">Der Ordnername muss base64-codiert sein, da er Pfadtrennzeichen enthalten kann, wenn der Ordner ein Unterordner unter „LooseApps“ ist.</span><span class="sxs-lookup"><span data-stu-id="3569b-118">This folder name should be base64 encoded as it may contain path separators if the folder is a subfolder under LooseApps.</span></span>
<br />

**<span data-ttu-id="3569b-119">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="3569b-119">Request headers</span></span>**

- <span data-ttu-id="3569b-120">Keine</span><span class="sxs-lookup"><span data-stu-id="3569b-120">None</span></span>

**<span data-ttu-id="3569b-121">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="3569b-121">Request body</span></span>**

- <span data-ttu-id="3569b-122">Multipart-konformer HTTP-Text des Verzeichnisinhalts.</span><span class="sxs-lookup"><span data-stu-id="3569b-122">multi-part conforming http body of the directory contents.</span></span>

**<span data-ttu-id="3569b-123">Antwort</span><span class="sxs-lookup"><span data-stu-id="3569b-123">Response</span></span>**

**<span data-ttu-id="3569b-124">Statuscode</span><span class="sxs-lookup"><span data-stu-id="3569b-124">Status code</span></span>**

<span data-ttu-id="3569b-125">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="3569b-125">This API has the following expected status codes.</span></span>

<span data-ttu-id="3569b-126">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="3569b-126">HTTP status code</span></span>      | <span data-ttu-id="3569b-127">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3569b-127">Description</span></span>
:------     | :-----
<span data-ttu-id="3569b-128">200</span><span class="sxs-lookup"><span data-stu-id="3569b-128">200</span></span> | <span data-ttu-id="3569b-129">Erfolg</span><span class="sxs-lookup"><span data-stu-id="3569b-129">Success</span></span>
<span data-ttu-id="3569b-130">4XX</span><span class="sxs-lookup"><span data-stu-id="3569b-130">4XX</span></span> | <span data-ttu-id="3569b-131">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="3569b-131">Error codes</span></span>
<span data-ttu-id="3569b-132">5XX</span><span class="sxs-lookup"><span data-stu-id="3569b-132">5XX</span></span> | <span data-ttu-id="3569b-133">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="3569b-133">Error codes</span></span>
<br />
**<span data-ttu-id="3569b-134">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="3569b-134">Available device families</span></span>**

* <span data-ttu-id="3569b-135">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="3569b-135">Windows Xbox</span></span>

