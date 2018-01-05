---
author: payzer
title: Device Portal - Referenz zu SMB-APIs
description: Erfahren Sie, wie Sie programmgesteuert auf die SMB-APIs zugreifen.
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.assetid: 1f0eb76e-fe3e-4674-a27e-229beec7e63d
ms.openlocfilehash: 1bc02780808d5b9fca09576165f428eca1cce715
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: HT
ms.contentlocale: de-DE
---
# <a name="developer-folder-api-reference"></a><span data-ttu-id="eadf3-104">Referenz zur API für den Entwicklerordner</span><span class="sxs-lookup"><span data-stu-id="eadf3-104">Developer folder API reference</span></span>   
<span data-ttu-id="eadf3-105">Für den Zugriff auf Dateien auf Ihrer Xbox One, die sich auf die Entwicklung beziehen, können Sie einen standardmäßigen Datei-Explorer verwenden.</span><span class="sxs-lookup"><span data-stu-id="eadf3-105">You can access development-related files on your Xbox One using a standard file explorer.</span></span> <span data-ttu-id="eadf3-106">Dadurch können Sie problemlos Dateien von Ihrem PC anzeigen und auf der Konsole ersetzen.</span><span class="sxs-lookup"><span data-stu-id="eadf3-106">This allows you to easily view and replace files from your PC to the console.</span></span>

**<span data-ttu-id="eadf3-107">Anforderung</span><span class="sxs-lookup"><span data-stu-id="eadf3-107">Request</span></span>**

<span data-ttu-id="eadf3-108">Sie können mithilfe der folgenden Anforderung auf den Entwicklerordner zugreifen.</span><span class="sxs-lookup"><span data-stu-id="eadf3-108">You can access the developer folder using the following request.</span></span> <span data-ttu-id="eadf3-109">Die Anforderung gibt Folgendes zurück:</span><span class="sxs-lookup"><span data-stu-id="eadf3-109">The request will return:</span></span>    
* <span data-ttu-id="eadf3-110">Den Speicherort der Dateifreigabe.</span><span class="sxs-lookup"><span data-stu-id="eadf3-110">The location of the file share.</span></span> <span data-ttu-id="eadf3-111">Dieser Speicherort kann in die Adressleiste eines Datei-Explorers eingegeben werden.</span><span class="sxs-lookup"><span data-stu-id="eadf3-111">This location can be entered into the address bar in a file explorer.</span></span>
* <span data-ttu-id="eadf3-112">Den Benutzernamen für den Zugriff auf die Dateifreigabe.</span><span class="sxs-lookup"><span data-stu-id="eadf3-112">The username to access the file share.</span></span>
* <span data-ttu-id="eadf3-113">Das Kennwort für den Zugriff auf die Dateifreigabe.</span><span class="sxs-lookup"><span data-stu-id="eadf3-113">The password to access the file share.</span></span>

<span data-ttu-id="eadf3-114">Methode</span><span class="sxs-lookup"><span data-stu-id="eadf3-114">Method</span></span>      | <span data-ttu-id="eadf3-115">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="eadf3-115">Request URI</span></span>
:------     | :-----
<span data-ttu-id="eadf3-116">GET</span><span class="sxs-lookup"><span data-stu-id="eadf3-116">GET</span></span> | <span data-ttu-id="eadf3-117">/ext/smb/developerfolder</span><span class="sxs-lookup"><span data-stu-id="eadf3-117">/ext/smb/developerfolder</span></span>
<br />
**<span data-ttu-id="eadf3-118">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="eadf3-118">URI parameters</span></span>**

- <span data-ttu-id="eadf3-119">Keine</span><span class="sxs-lookup"><span data-stu-id="eadf3-119">None</span></span>

**<span data-ttu-id="eadf3-120">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="eadf3-120">Request headers</span></span>**

- <span data-ttu-id="eadf3-121">Keine</span><span class="sxs-lookup"><span data-stu-id="eadf3-121">None</span></span>

**<span data-ttu-id="eadf3-122">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="eadf3-122">Request body</span></span>**

- <span data-ttu-id="eadf3-123">Keine</span><span class="sxs-lookup"><span data-stu-id="eadf3-123">None</span></span>

**<span data-ttu-id="eadf3-124">Antwort</span><span class="sxs-lookup"><span data-stu-id="eadf3-124">Response</span></span>**   
<span data-ttu-id="eadf3-125">Path: Der Pfad zur Dateifreigabe mit den Entwicklerdateien.</span><span class="sxs-lookup"><span data-stu-id="eadf3-125">Path - the path to the file developer files share.</span></span>   
<span data-ttu-id="eadf3-126">Username: Der Benutzername für den Zugriff auf die Freigabe mit den Entwicklerdateien.</span><span class="sxs-lookup"><span data-stu-id="eadf3-126">Username - the username needed to access the developer files share.</span></span>   
<span data-ttu-id="eadf3-127">Password: Das Kennwort für den Zugriff auf die Freigabe mit den Entwicklerdateien.</span><span class="sxs-lookup"><span data-stu-id="eadf3-127">Password - the password needed to access the developer files share.</span></span>   

**<span data-ttu-id="eadf3-128">Statuscode</span><span class="sxs-lookup"><span data-stu-id="eadf3-128">Status code</span></span>**

<span data-ttu-id="eadf3-129">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="eadf3-129">This API has the following expected status codes.</span></span>

<span data-ttu-id="eadf3-130">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="eadf3-130">HTTP status code</span></span>      | <span data-ttu-id="eadf3-131">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="eadf3-131">Description</span></span>
:------     | :-----
<span data-ttu-id="eadf3-132">200</span><span class="sxs-lookup"><span data-stu-id="eadf3-132">200</span></span> | <span data-ttu-id="eadf3-133">Die Anforderung für den Zugriff auf die Anmeldeinformationen für die Dateifreigabe wurde gewährt.</span><span class="sxs-lookup"><span data-stu-id="eadf3-133">The request to access the credentials for the file share was granted.</span></span>
<span data-ttu-id="eadf3-134">4XX</span><span class="sxs-lookup"><span data-stu-id="eadf3-134">4XX</span></span> | <span data-ttu-id="eadf3-135">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="eadf3-135">Error codes</span></span>
<span data-ttu-id="eadf3-136">5XX</span><span class="sxs-lookup"><span data-stu-id="eadf3-136">5XX</span></span> | <span data-ttu-id="eadf3-137">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="eadf3-137">Error codes</span></span>
<br />
**<span data-ttu-id="eadf3-138">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="eadf3-138">Available device families</span></span>**

* <span data-ttu-id="eadf3-139">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="eadf3-139">Windows Xbox</span></span>
