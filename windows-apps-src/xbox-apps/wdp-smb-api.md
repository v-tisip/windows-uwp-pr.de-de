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
ms.sourcegitcommit: 086001cffaf436e6e4324761d59bcc5e598c15ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2018
ms.locfileid: "5691088"
---
# <a name="developer-folder-api-reference"></a><span data-ttu-id="bfd5a-104">Referenz zur API für den Entwicklerordner</span><span class="sxs-lookup"><span data-stu-id="bfd5a-104">Developer folder API reference</span></span>   
<span data-ttu-id="bfd5a-105">Für den Zugriff auf Dateien auf Ihrer Xbox One, die sich auf die Entwicklung beziehen, können Sie einen standardmäßigen Datei-Explorer verwenden.</span><span class="sxs-lookup"><span data-stu-id="bfd5a-105">You can access development-related files on your Xbox One using a standard file explorer.</span></span> <span data-ttu-id="bfd5a-106">Dadurch können Sie problemlos Dateien von Ihrem PC anzeigen und auf der Konsole ersetzen.</span><span class="sxs-lookup"><span data-stu-id="bfd5a-106">This allows you to easily view and replace files from your PC to the console.</span></span>

**<span data-ttu-id="bfd5a-107">Anforderung</span><span class="sxs-lookup"><span data-stu-id="bfd5a-107">Request</span></span>**

<span data-ttu-id="bfd5a-108">Sie können mithilfe der folgenden Anforderung auf den Entwicklerordner zugreifen.</span><span class="sxs-lookup"><span data-stu-id="bfd5a-108">You can access the developer folder using the following request.</span></span> <span data-ttu-id="bfd5a-109">Die Anforderung gibt Folgendes zurück:</span><span class="sxs-lookup"><span data-stu-id="bfd5a-109">The request will return:</span></span>    
* <span data-ttu-id="bfd5a-110">Den Speicherort der Dateifreigabe.</span><span class="sxs-lookup"><span data-stu-id="bfd5a-110">The location of the file share.</span></span> <span data-ttu-id="bfd5a-111">Dieser Speicherort kann in die Adressleiste eines Datei-Explorers eingegeben werden.</span><span class="sxs-lookup"><span data-stu-id="bfd5a-111">This location can be entered into the address bar in a file explorer.</span></span>
* <span data-ttu-id="bfd5a-112">Den Benutzernamen für den Zugriff auf die Dateifreigabe.</span><span class="sxs-lookup"><span data-stu-id="bfd5a-112">The username to access the file share.</span></span>
* <span data-ttu-id="bfd5a-113">Das Kennwort für den Zugriff auf die Dateifreigabe.</span><span class="sxs-lookup"><span data-stu-id="bfd5a-113">The password to access the file share.</span></span>

<span data-ttu-id="bfd5a-114">Methode</span><span class="sxs-lookup"><span data-stu-id="bfd5a-114">Method</span></span>      | <span data-ttu-id="bfd5a-115">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="bfd5a-115">Request URI</span></span>
:------     | :-----
<span data-ttu-id="bfd5a-116">GET</span><span class="sxs-lookup"><span data-stu-id="bfd5a-116">GET</span></span> | <span data-ttu-id="bfd5a-117">/ext/smb/developerfolder</span><span class="sxs-lookup"><span data-stu-id="bfd5a-117">/ext/smb/developerfolder</span></span>
<br />
**<span data-ttu-id="bfd5a-118">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="bfd5a-118">URI parameters</span></span>**

- <span data-ttu-id="bfd5a-119">Keine</span><span class="sxs-lookup"><span data-stu-id="bfd5a-119">None</span></span>

**<span data-ttu-id="bfd5a-120">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="bfd5a-120">Request headers</span></span>**

- <span data-ttu-id="bfd5a-121">Keine</span><span class="sxs-lookup"><span data-stu-id="bfd5a-121">None</span></span>

**<span data-ttu-id="bfd5a-122">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="bfd5a-122">Request body</span></span>**

- <span data-ttu-id="bfd5a-123">Keine</span><span class="sxs-lookup"><span data-stu-id="bfd5a-123">None</span></span>

**<span data-ttu-id="bfd5a-124">Antwort</span><span class="sxs-lookup"><span data-stu-id="bfd5a-124">Response</span></span>**   
<span data-ttu-id="bfd5a-125">Path: Der Pfad zur Dateifreigabe mit den Entwicklerdateien.</span><span class="sxs-lookup"><span data-stu-id="bfd5a-125">Path - the path to the file developer files share.</span></span>   
<span data-ttu-id="bfd5a-126">Username: Der Benutzername für den Zugriff auf die Freigabe mit den Entwicklerdateien.</span><span class="sxs-lookup"><span data-stu-id="bfd5a-126">Username - the username needed to access the developer files share.</span></span>   
<span data-ttu-id="bfd5a-127">Password: Das Kennwort für den Zugriff auf die Freigabe mit den Entwicklerdateien.</span><span class="sxs-lookup"><span data-stu-id="bfd5a-127">Password - the password needed to access the developer files share.</span></span>   

**<span data-ttu-id="bfd5a-128">Statuscode</span><span class="sxs-lookup"><span data-stu-id="bfd5a-128">Status code</span></span>**

<span data-ttu-id="bfd5a-129">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="bfd5a-129">This API has the following expected status codes.</span></span>

<span data-ttu-id="bfd5a-130">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="bfd5a-130">HTTP status code</span></span>      | <span data-ttu-id="bfd5a-131">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bfd5a-131">Description</span></span>
:------     | :-----
<span data-ttu-id="bfd5a-132">200</span><span class="sxs-lookup"><span data-stu-id="bfd5a-132">200</span></span> | <span data-ttu-id="bfd5a-133">Die Anforderung für den Zugriff auf die Anmeldeinformationen für die Dateifreigabe wurde gewährt.</span><span class="sxs-lookup"><span data-stu-id="bfd5a-133">The request to access the credentials for the file share was granted.</span></span>
<span data-ttu-id="bfd5a-134">4XX</span><span class="sxs-lookup"><span data-stu-id="bfd5a-134">4XX</span></span> | <span data-ttu-id="bfd5a-135">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="bfd5a-135">Error codes</span></span>
<span data-ttu-id="bfd5a-136">5XX</span><span class="sxs-lookup"><span data-stu-id="bfd5a-136">5XX</span></span> | <span data-ttu-id="bfd5a-137">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="bfd5a-137">Error codes</span></span>
<br />
**<span data-ttu-id="bfd5a-138">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="bfd5a-138">Available device families</span></span>**

* <span data-ttu-id="bfd5a-139">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="bfd5a-139">Windows Xbox</span></span>
