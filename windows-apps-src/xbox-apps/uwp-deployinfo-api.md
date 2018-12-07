---
title: 'Referenz zur API für Bereitstellungsinformationen des Geräteportals '
description: Erfahren Sie, wie Sie programmgesteuert auf die API für die Bereitstellung von Informationen zugreifen.
ms.localizationpriority: medium
ms.topic: article
ms.date: 02/08/2017
ms.openlocfilehash: 7543b41c6ee1d9c07f4540012f84dccc10bb4d76
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8784509"
---
# <a name="requests-deployment-information-for-one-or-more-installed-packages"></a><span data-ttu-id="e8446-103">Fordert Bereitstellungsinformationen für ein oder mehrere installierte Pakete an.</span><span class="sxs-lookup"><span data-stu-id="e8446-103">Requests deployment information for one or more installed packages.</span></span>

**<span data-ttu-id="e8446-104">Anforderung</span><span class="sxs-lookup"><span data-stu-id="e8446-104">Request</span></span>**

<span data-ttu-id="e8446-105">Methode</span><span class="sxs-lookup"><span data-stu-id="e8446-105">Method</span></span>      | <span data-ttu-id="e8446-106">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="e8446-106">Request URI</span></span>
:------     | :------
<span data-ttu-id="e8446-107">POST</span><span class="sxs-lookup"><span data-stu-id="e8446-107">POST</span></span> | <span data-ttu-id="e8446-108">/ext/app/deployinfo</span><span class="sxs-lookup"><span data-stu-id="e8446-108">/ext/app/deployinfo</span></span>
<br />
**<span data-ttu-id="e8446-109">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="e8446-109">URI parameters</span></span>**

 - <span data-ttu-id="e8446-110">Keine</span><span class="sxs-lookup"><span data-stu-id="e8446-110">None</span></span>

**<span data-ttu-id="e8446-111">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="e8446-111">Request headers</span></span>**

- <span data-ttu-id="e8446-112">Keiner</span><span class="sxs-lookup"><span data-stu-id="e8446-112">None</span></span>

**<span data-ttu-id="e8446-113">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="e8446-113">Request body</span></span>**

<span data-ttu-id="e8446-114">Ein JSON-Array im folgenden Format:</span><span class="sxs-lookup"><span data-stu-id="e8446-114">A JSON array in the following format:</span></span>

* <span data-ttu-id="e8446-115">DeployInfo</span><span class="sxs-lookup"><span data-stu-id="e8446-115">DeployInfo</span></span>
  * <span data-ttu-id="e8446-116">PackageFullName: Name des Pakets, zu dem wir Informationen anfordern</span><span class="sxs-lookup"><span data-stu-id="e8446-116">PackageFullName - Name of the package that we are requesting information about.</span></span>
  * <span data-ttu-id="e8446-117">OverlayFolder: Optionaler Pfad zu einem Overlay-Ordnerpfad, wenn dieses Feature verwendet wird</span><span class="sxs-lookup"><span data-stu-id="e8446-117">OverlayFolder - Optional path to an overlay folder path if using this feature.</span></span>

###<a name="response"></a><span data-ttu-id="e8446-118">Response</span><span class="sxs-lookup"><span data-stu-id="e8446-118">Response</span></span>

**<span data-ttu-id="e8446-119">Antworttext</span><span class="sxs-lookup"><span data-stu-id="e8446-119">Response body</span></span>**

<span data-ttu-id="e8446-120">Ein JSON-Array in folgendem Format (einige Felder sind optional):</span><span class="sxs-lookup"><span data-stu-id="e8446-120">A JSON array in the following format (some fields are optional):</span></span>

* <span data-ttu-id="e8446-121">DeployInfo</span><span class="sxs-lookup"><span data-stu-id="e8446-121">DeployInfo</span></span>
  * <span data-ttu-id="e8446-122">PackageFullName: Name des Pakets, zu dem wir Informationen erhalten.</span><span class="sxs-lookup"><span data-stu-id="e8446-122">PackageFullName - Name of the package that we are receiving information about.</span></span>
  * <span data-ttu-id="e8446-123">DeployType: Der Bereitstellungstyp.</span><span class="sxs-lookup"><span data-stu-id="e8446-123">DeployType - The type of deployment.</span></span>
  * <span data-ttu-id="e8446-124">DeployPathOrSpecifiers: Ein Bereitstellungspfad für lose Bereitstellungen oder installierte Bezeichner für Bereitstellungen in Paketen.</span><span class="sxs-lookup"><span data-stu-id="e8446-124">DeployPathOrSpecifiers - A deploy path for loose deployments or installed specifiers for packaged deployments.</span></span>
  * <span data-ttu-id="e8446-125">DeployDrive: Das Laufwerk, für das das Paket für die entsprechenden Bereitstellungstypen bereitgestellt wird</span><span class="sxs-lookup"><span data-stu-id="e8446-125">DeployDrive - The drive the package is deployed to for applicable deployment types.</span></span>
  * <span data-ttu-id="e8446-126">DeploySizeInBytes: Die Größe des Pakets in Byte für die entsprechenden Bereitstellungstypen</span><span class="sxs-lookup"><span data-stu-id="e8446-126">DeploySizeInBytes - The size in bytes of the package for applicable deployment types.</span></span>
  * <span data-ttu-id="e8446-127">OverlayFolder: Der Overlay-Ordner für Bereitstellungen, die dieses Feature unterstützen</span><span class="sxs-lookup"><span data-stu-id="e8446-127">OverlayFolder - The overlay folder for deployments which support this feature.</span></span>

**<span data-ttu-id="e8446-128">Statuscode</span><span class="sxs-lookup"><span data-stu-id="e8446-128">Status code</span></span>**

<span data-ttu-id="e8446-129">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="e8446-129">This API has the following expected status codes.</span></span>

<span data-ttu-id="e8446-130">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="e8446-130">HTTP status code</span></span>      | <span data-ttu-id="e8446-131">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e8446-131">Description</span></span>
:------     | :-----
<span data-ttu-id="e8446-132">200</span><span class="sxs-lookup"><span data-stu-id="e8446-132">200</span></span> | <span data-ttu-id="e8446-133">Erfolg</span><span class="sxs-lookup"><span data-stu-id="e8446-133">Success</span></span>
<span data-ttu-id="e8446-134">4XX</span><span class="sxs-lookup"><span data-stu-id="e8446-134">4XX</span></span> | <span data-ttu-id="e8446-135">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="e8446-135">Error codes</span></span>
<span data-ttu-id="e8446-136">5XX</span><span class="sxs-lookup"><span data-stu-id="e8446-136">5XX</span></span> | <span data-ttu-id="e8446-137">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="e8446-137">Error codes</span></span>
<br />

**<span data-ttu-id="e8446-138">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="e8446-138">Available device families</span></span>**

* <span data-ttu-id="e8446-139">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="e8446-139">Windows Xbox</span></span>