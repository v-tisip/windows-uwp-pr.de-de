---
author: WilliamsJason
title: Device Portal - Referenz zu den APIs zum Registrieren loser Ordner
description: Erfahren Sie, wie Sie programmgesteuert auf die APIs zum Registrieren loser Ordner zugreifen.
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.assetid: efdf4214-9738-4df6-bf1f-ed7141696ef6
ms.localizationpriority: medium
ms.openlocfilehash: cb80e2dbd7ebdfbb05bd642b9875a9cd7cc356f3
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6980068"
---
# <a name="register-an-app-in-a-loose-folder"></a><span data-ttu-id="3606f-104">Registrieren einer App in einem losen Ordner</span><span class="sxs-lookup"><span data-stu-id="3606f-104">Register an app in a loose folder</span></span>  

**<span data-ttu-id="3606f-105">Anforderung</span><span class="sxs-lookup"><span data-stu-id="3606f-105">Request</span></span>**

<span data-ttu-id="3606f-106">Mithilfe des folgenden Anforderungsformats können Sie eine App in einem losen Ordner registrieren.</span><span class="sxs-lookup"><span data-stu-id="3606f-106">You can register an app in a loose folder by using the following request format.</span></span>

<span data-ttu-id="3606f-107">Methode</span><span class="sxs-lookup"><span data-stu-id="3606f-107">Method</span></span>      | <span data-ttu-id="3606f-108">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="3606f-108">Request URI</span></span>
:------     | :------
<span data-ttu-id="3606f-109">POST</span><span class="sxs-lookup"><span data-stu-id="3606f-109">POST</span></span> | <span data-ttu-id="3606f-110">/api/app/packagemanager/register</span><span class="sxs-lookup"><span data-stu-id="3606f-110">/api/app/packagemanager/register</span></span>
<br />
**<span data-ttu-id="3606f-111">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="3606f-111">URI parameters</span></span>**

<span data-ttu-id="3606f-112">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="3606f-112">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="3606f-113">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="3606f-113">URI Parameter</span></span>      | <span data-ttu-id="3606f-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3606f-114">Description</span></span>
:------     | :-----
<span data-ttu-id="3606f-115">folder (erforderlich)</span><span class="sxs-lookup"><span data-stu-id="3606f-115">folder (required)</span></span> | <span data-ttu-id="3606f-116">Der Name des Zielordners für das Paket, das registriert werden soll.</span><span class="sxs-lookup"><span data-stu-id="3606f-116">The destination folder name of the package to be registered.</span></span> <span data-ttu-id="3606f-117">Dieser Ordner muss unter „d:\developmentfiles\LooseApps“ auf der Konsole gespeichert sein.</span><span class="sxs-lookup"><span data-stu-id="3606f-117">This folder must exist under d:\developmentfiles\LooseApps on the console.</span></span> <span data-ttu-id="3606f-118">Der Ordnername muss base64-codiert sein, da er Pfadtrennzeichen enthalten kann, wenn der Ordner in einem Unterordner unter „LooseApps“ enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="3606f-118">This folder name should be base64 encoded as it may contain path separators if the folder is in a subfolder under LooseApps.</span></span>
<br />

**<span data-ttu-id="3606f-119">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="3606f-119">Request headers</span></span>**

- <span data-ttu-id="3606f-120">Keine</span><span class="sxs-lookup"><span data-stu-id="3606f-120">None</span></span>

**<span data-ttu-id="3606f-121">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="3606f-121">Request body</span></span>**

- <span data-ttu-id="3606f-122">Keine</span><span class="sxs-lookup"><span data-stu-id="3606f-122">None</span></span>

**<span data-ttu-id="3606f-123">Antwort</span><span class="sxs-lookup"><span data-stu-id="3606f-123">Response</span></span>**

**<span data-ttu-id="3606f-124">Statuscode</span><span class="sxs-lookup"><span data-stu-id="3606f-124">Status code</span></span>**

<span data-ttu-id="3606f-125">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="3606f-125">This API has the following expected status codes.</span></span>

<span data-ttu-id="3606f-126">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="3606f-126">HTTP status code</span></span>      | <span data-ttu-id="3606f-127">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3606f-127">Description</span></span>
:------     | :-----
<span data-ttu-id="3606f-128">200</span><span class="sxs-lookup"><span data-stu-id="3606f-128">200</span></span> | <span data-ttu-id="3606f-129">Bereitstellungsanforderung akzeptiert und wird verarbeitet</span><span class="sxs-lookup"><span data-stu-id="3606f-129">Deploy request accepted and being processed</span></span>
<span data-ttu-id="3606f-130">4XX</span><span class="sxs-lookup"><span data-stu-id="3606f-130">4XX</span></span> | <span data-ttu-id="3606f-131">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="3606f-131">Error codes</span></span>
<span data-ttu-id="3606f-132">5XX</span><span class="sxs-lookup"><span data-stu-id="3606f-132">5XX</span></span> | <span data-ttu-id="3606f-133">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="3606f-133">Error codes</span></span>
<br />
**<span data-ttu-id="3606f-134">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="3606f-134">Available device families</span></span>**

* <span data-ttu-id="3606f-135">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="3606f-135">Windows Xbox</span></span>

**<span data-ttu-id="3606f-136">Hinweise</span><span class="sxs-lookup"><span data-stu-id="3606f-136">Notes</span></span>**

<span data-ttu-id="3606f-137">Es gibt mindestens drei verschiedene Möglichkeiten, die lose App in den gewünschten Ordner auf der Konsole einzufügen.</span><span class="sxs-lookup"><span data-stu-id="3606f-137">There are at least three different ways to get the loose app on the console in the desired folder.</span></span> <span data-ttu-id="3606f-138">Die einfachste Möglichkeit besteht darin, die Dateien einfach über SMB in „\\<IP_Address>\DevelopmentFiles\LooseApps“ zu kopieren.</span><span class="sxs-lookup"><span data-stu-id="3606f-138">The easiest is to simply copy the files via SMB to \\<IP_Address>\DevelopmentFiles\LooseApps.</span></span> <span data-ttu-id="3606f-139">Dazu sind ein Benutzername und Kennwort für UWA-Kits erforderlich, die über [/ext/smb/developerfolder](wdp-smb-api.md) abgerufen werden können.</span><span class="sxs-lookup"><span data-stu-id="3606f-139">This will require a username and password on UWA kits which can be obtained via [/ext/smb/developerfolder](wdp-smb-api.md).</span></span> 

<span data-ttu-id="3606f-140">Die zweite Möglichkeit besteht darin, einzelne Dateien mithilfe eines POST-Befehls für „/api/filesystem/apps/file“ in den richtigen Ordner zu kopieren. „knownfolderid“ entspricht dabei „DevelopmentFiles“, „packagefullname“ ist leer, und der Dateiname und Pfad sind ordnungsgemäß angegeben (der Pfad muss mit „LooseApps“ beginnen).</span><span class="sxs-lookup"><span data-stu-id="3606f-140">The second way is by copying over individual files to the correct location by doing a POST to /api/filesystem/apps/file where knownfolderid is DevelopmentFiles, packagefullname is empty, and filename and path are properly supplied (path should begin with LooseApps).</span></span>

<span data-ttu-id="3606f-141">Die dritte Möglichkeit besteht darin, einen vollständigen Ordner über [/api/app/packagemanager/upload](wdp-folder-upload.md) auf einmal zu kopieren. Dabei entspricht „destinationFolder“ dem Namen des Ordners, der unter „d:\developmentfiles\looseapps“ gespeichert werden soll, und die Nutzlast einem multipart-konformen HTTP-Text des Verzeichnisinhalts.</span><span class="sxs-lookup"><span data-stu-id="3606f-141">The third way is to copy an entire folder at a time via [/api/app/packagemanager/upload](wdp-folder-upload.md) where destinationFolder is the name of the folder to be placed under d:\developmentfiles\looseapps and the payload is a multi-part conforming http body of the directory contents.</span></span>

