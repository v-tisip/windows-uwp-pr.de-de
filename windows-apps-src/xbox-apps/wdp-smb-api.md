---
author: payzer
title: Device Portal - Referenz zu SMB-APIs
description: Erfahren Sie, wie Sie programmgesteuert auf die SMB-APIs zugreifen.
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.assetid: 1f0eb76e-fe3e-4674-a27e-229beec7e63d
ms.localizationpriority: medium
ms.openlocfilehash: 2a337fe722d73a08c1c75a84478fc31e5bdf6b03
ms.sourcegitcommit: 38f06f1714334273d865935d9afb80efffe97a17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6191412"
---
# <a name="developer-folder-api-reference"></a><span data-ttu-id="12b68-104">Referenz zur API für den Entwicklerordner</span><span class="sxs-lookup"><span data-stu-id="12b68-104">Developer folder API reference</span></span>   
<span data-ttu-id="12b68-105">Für den Zugriff auf Dateien auf Ihrer Xbox One, die sich auf die Entwicklung beziehen, können Sie einen standardmäßigen Datei-Explorer verwenden.</span><span class="sxs-lookup"><span data-stu-id="12b68-105">You can access development-related files on your Xbox One using a standard file explorer.</span></span> <span data-ttu-id="12b68-106">Dadurch können Sie problemlos Dateien von Ihrem PC anzeigen und auf der Konsole ersetzen.</span><span class="sxs-lookup"><span data-stu-id="12b68-106">This allows you to easily view and replace files from your PC to the console.</span></span>

**<span data-ttu-id="12b68-107">Anforderung</span><span class="sxs-lookup"><span data-stu-id="12b68-107">Request</span></span>**

<span data-ttu-id="12b68-108">Sie können mithilfe der folgenden Anforderung auf den Entwicklerordner zugreifen.</span><span class="sxs-lookup"><span data-stu-id="12b68-108">You can access the developer folder using the following request.</span></span> <span data-ttu-id="12b68-109">Die Anforderung gibt Folgendes zurück:</span><span class="sxs-lookup"><span data-stu-id="12b68-109">The request will return:</span></span>    
* <span data-ttu-id="12b68-110">Den Speicherort der Dateifreigabe.</span><span class="sxs-lookup"><span data-stu-id="12b68-110">The location of the file share.</span></span> <span data-ttu-id="12b68-111">Dieser Speicherort kann in die Adressleiste eines Datei-Explorers eingegeben werden.</span><span class="sxs-lookup"><span data-stu-id="12b68-111">This location can be entered into the address bar in a file explorer.</span></span>
* <span data-ttu-id="12b68-112">Den Benutzernamen für den Zugriff auf die Dateifreigabe.</span><span class="sxs-lookup"><span data-stu-id="12b68-112">The username to access the file share.</span></span>
* <span data-ttu-id="12b68-113">Das Kennwort für den Zugriff auf die Dateifreigabe.</span><span class="sxs-lookup"><span data-stu-id="12b68-113">The password to access the file share.</span></span>

<span data-ttu-id="12b68-114">Methode</span><span class="sxs-lookup"><span data-stu-id="12b68-114">Method</span></span>      | <span data-ttu-id="12b68-115">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="12b68-115">Request URI</span></span>
:------     | :-----
<span data-ttu-id="12b68-116">GET</span><span class="sxs-lookup"><span data-stu-id="12b68-116">GET</span></span> | <span data-ttu-id="12b68-117">/ext/smb/developerfolder</span><span class="sxs-lookup"><span data-stu-id="12b68-117">/ext/smb/developerfolder</span></span>
<br />
**<span data-ttu-id="12b68-118">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="12b68-118">URI parameters</span></span>**

- <span data-ttu-id="12b68-119">Keine</span><span class="sxs-lookup"><span data-stu-id="12b68-119">None</span></span>

**<span data-ttu-id="12b68-120">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="12b68-120">Request headers</span></span>**

- <span data-ttu-id="12b68-121">Keine</span><span class="sxs-lookup"><span data-stu-id="12b68-121">None</span></span>

**<span data-ttu-id="12b68-122">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="12b68-122">Request body</span></span>**

- <span data-ttu-id="12b68-123">Keine</span><span class="sxs-lookup"><span data-stu-id="12b68-123">None</span></span>

**<span data-ttu-id="12b68-124">Antwort</span><span class="sxs-lookup"><span data-stu-id="12b68-124">Response</span></span>**   
<span data-ttu-id="12b68-125">Path: Der Pfad zur Dateifreigabe mit den Entwicklerdateien.</span><span class="sxs-lookup"><span data-stu-id="12b68-125">Path - the path to the file developer files share.</span></span>   
<span data-ttu-id="12b68-126">Username: Der Benutzername für den Zugriff auf die Freigabe mit den Entwicklerdateien.</span><span class="sxs-lookup"><span data-stu-id="12b68-126">Username - the username needed to access the developer files share.</span></span>   
<span data-ttu-id="12b68-127">Password: Das Kennwort für den Zugriff auf die Freigabe mit den Entwicklerdateien.</span><span class="sxs-lookup"><span data-stu-id="12b68-127">Password - the password needed to access the developer files share.</span></span>   

**<span data-ttu-id="12b68-128">Statuscode</span><span class="sxs-lookup"><span data-stu-id="12b68-128">Status code</span></span>**

<span data-ttu-id="12b68-129">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="12b68-129">This API has the following expected status codes.</span></span>

<span data-ttu-id="12b68-130">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="12b68-130">HTTP status code</span></span>      | <span data-ttu-id="12b68-131">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="12b68-131">Description</span></span>
:------     | :-----
<span data-ttu-id="12b68-132">200</span><span class="sxs-lookup"><span data-stu-id="12b68-132">200</span></span> | <span data-ttu-id="12b68-133">Die Anforderung für den Zugriff auf die Anmeldeinformationen für die Dateifreigabe wurde gewährt.</span><span class="sxs-lookup"><span data-stu-id="12b68-133">The request to access the credentials for the file share was granted.</span></span>
<span data-ttu-id="12b68-134">4XX</span><span class="sxs-lookup"><span data-stu-id="12b68-134">4XX</span></span> | <span data-ttu-id="12b68-135">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="12b68-135">Error codes</span></span>
<span data-ttu-id="12b68-136">5XX</span><span class="sxs-lookup"><span data-stu-id="12b68-136">5XX</span></span> | <span data-ttu-id="12b68-137">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="12b68-137">Error codes</span></span>
<br />
**<span data-ttu-id="12b68-138">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="12b68-138">Available device families</span></span>**

* <span data-ttu-id="12b68-139">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="12b68-139">Windows Xbox</span></span>
