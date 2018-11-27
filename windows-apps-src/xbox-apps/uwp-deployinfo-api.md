---
title: 'Referenz zur API für Bereitstellungsinformationen des Geräteportals '
description: Erfahren Sie, wie Sie programmgesteuert auf die API für die Bereitstellung von Informationen zugreifen.
ms.localizationpriority: medium
ms.openlocfilehash: c44089313b100880b419e9b55a26101e877496f3
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7709852"
---
# <a name="requests-deployment-information-for-one-or-more-installed-packages"></a><span data-ttu-id="a9d09-103">Fordert Bereitstellungsinformationen für ein oder mehrere installierte Pakete an.</span><span class="sxs-lookup"><span data-stu-id="a9d09-103">Requests deployment information for one or more installed packages.</span></span>

**<span data-ttu-id="a9d09-104">Anforderung</span><span class="sxs-lookup"><span data-stu-id="a9d09-104">Request</span></span>**

<span data-ttu-id="a9d09-105">Methode</span><span class="sxs-lookup"><span data-stu-id="a9d09-105">Method</span></span>      | <span data-ttu-id="a9d09-106">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="a9d09-106">Request URI</span></span>
:------     | :------
<span data-ttu-id="a9d09-107">POST</span><span class="sxs-lookup"><span data-stu-id="a9d09-107">POST</span></span> | <span data-ttu-id="a9d09-108">/ext/app/deployinfo</span><span class="sxs-lookup"><span data-stu-id="a9d09-108">/ext/app/deployinfo</span></span>
<br />
**<span data-ttu-id="a9d09-109">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="a9d09-109">URI parameters</span></span>**

 - <span data-ttu-id="a9d09-110">Keine</span><span class="sxs-lookup"><span data-stu-id="a9d09-110">None</span></span>

**<span data-ttu-id="a9d09-111">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="a9d09-111">Request headers</span></span>**

- <span data-ttu-id="a9d09-112">Keiner</span><span class="sxs-lookup"><span data-stu-id="a9d09-112">None</span></span>

**<span data-ttu-id="a9d09-113">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="a9d09-113">Request body</span></span>**

<span data-ttu-id="a9d09-114">Ein JSON-Array im folgenden Format:</span><span class="sxs-lookup"><span data-stu-id="a9d09-114">A JSON array in the following format:</span></span>

* <span data-ttu-id="a9d09-115">DeployInfo</span><span class="sxs-lookup"><span data-stu-id="a9d09-115">DeployInfo</span></span>
  * <span data-ttu-id="a9d09-116">PackageFullName: Name des Pakets, zu dem wir Informationen anfordern</span><span class="sxs-lookup"><span data-stu-id="a9d09-116">PackageFullName - Name of the package that we are requesting information about.</span></span>
  * <span data-ttu-id="a9d09-117">OverlayFolder: Optionaler Pfad zu einem Overlay-Ordnerpfad, wenn dieses Feature verwendet wird</span><span class="sxs-lookup"><span data-stu-id="a9d09-117">OverlayFolder - Optional path to an overlay folder path if using this feature.</span></span>

###<a name="response"></a><span data-ttu-id="a9d09-118">Response</span><span class="sxs-lookup"><span data-stu-id="a9d09-118">Response</span></span>

**<span data-ttu-id="a9d09-119">Antworttext</span><span class="sxs-lookup"><span data-stu-id="a9d09-119">Response body</span></span>**

<span data-ttu-id="a9d09-120">Ein JSON-Array in folgendem Format (einige Felder sind optional):</span><span class="sxs-lookup"><span data-stu-id="a9d09-120">A JSON array in the following format (some fields are optional):</span></span>

* <span data-ttu-id="a9d09-121">DeployInfo</span><span class="sxs-lookup"><span data-stu-id="a9d09-121">DeployInfo</span></span>
  * <span data-ttu-id="a9d09-122">PackageFullName: Name des Pakets, zu dem wir Informationen erhalten.</span><span class="sxs-lookup"><span data-stu-id="a9d09-122">PackageFullName - Name of the package that we are receiving information about.</span></span>
  * <span data-ttu-id="a9d09-123">DeployType: Der Bereitstellungstyp.</span><span class="sxs-lookup"><span data-stu-id="a9d09-123">DeployType - The type of deployment.</span></span>
  * <span data-ttu-id="a9d09-124">DeployPathOrSpecifiers: Ein Bereitstellungspfad für lose Bereitstellungen oder installierte Bezeichner für Bereitstellungen in Paketen.</span><span class="sxs-lookup"><span data-stu-id="a9d09-124">DeployPathOrSpecifiers - A deploy path for loose deployments or installed specifiers for packaged deployments.</span></span>
  * <span data-ttu-id="a9d09-125">DeployDrive: Das Laufwerk, für das das Paket für die entsprechenden Bereitstellungstypen bereitgestellt wird</span><span class="sxs-lookup"><span data-stu-id="a9d09-125">DeployDrive - The drive the package is deployed to for applicable deployment types.</span></span>
  * <span data-ttu-id="a9d09-126">DeploySizeInBytes: Die Größe des Pakets in Byte für die entsprechenden Bereitstellungstypen</span><span class="sxs-lookup"><span data-stu-id="a9d09-126">DeploySizeInBytes - The size in bytes of the package for applicable deployment types.</span></span>
  * <span data-ttu-id="a9d09-127">OverlayFolder: Der Overlay-Ordner für Bereitstellungen, die dieses Feature unterstützen</span><span class="sxs-lookup"><span data-stu-id="a9d09-127">OverlayFolder - The overlay folder for deployments which support this feature.</span></span>

**<span data-ttu-id="a9d09-128">Statuscode</span><span class="sxs-lookup"><span data-stu-id="a9d09-128">Status code</span></span>**

<span data-ttu-id="a9d09-129">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="a9d09-129">This API has the following expected status codes.</span></span>

<span data-ttu-id="a9d09-130">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="a9d09-130">HTTP status code</span></span>      | <span data-ttu-id="a9d09-131">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a9d09-131">Description</span></span>
:------     | :-----
<span data-ttu-id="a9d09-132">200</span><span class="sxs-lookup"><span data-stu-id="a9d09-132">200</span></span> | <span data-ttu-id="a9d09-133">Erfolg</span><span class="sxs-lookup"><span data-stu-id="a9d09-133">Success</span></span>
<span data-ttu-id="a9d09-134">4XX</span><span class="sxs-lookup"><span data-stu-id="a9d09-134">4XX</span></span> | <span data-ttu-id="a9d09-135">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="a9d09-135">Error codes</span></span>
<span data-ttu-id="a9d09-136">5XX</span><span class="sxs-lookup"><span data-stu-id="a9d09-136">5XX</span></span> | <span data-ttu-id="a9d09-137">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="a9d09-137">Error codes</span></span>
<br />

**<span data-ttu-id="a9d09-138">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="a9d09-138">Available device families</span></span>**

* <span data-ttu-id="a9d09-139">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="a9d09-139">Windows Xbox</span></span>