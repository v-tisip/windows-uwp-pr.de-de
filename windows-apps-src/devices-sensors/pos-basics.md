---
author: TerryWarwick
title: Erste Schritte mit Point Of Service-Geräten
description: Dieser Artikel enthält Informationen für die ersten Schritte mit PointOfService-UWP-Apps.
ms.author: jken
ms.date: 06/13/2018
ms.topic: article
keywords: Windows 10, UWP, Point Of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: 46dd1f615e42f6e89ee9a92cb980299e9a0e5205
ms.sourcegitcommit: 71e8eae5c077a7740e5606298951bb78fc42b22c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6664659"
---
# <a name="getting-started-with-point-of-service"></a><span data-ttu-id="76c23-104">Erste Schritte mit Point Of Service-Geräten</span><span class="sxs-lookup"><span data-stu-id="76c23-104">Getting started with Point of Service</span></span>

## <a name="pointofservice-basics"></a><span data-ttu-id="76c23-105">PointOfService-Grundlagen</span><span class="sxs-lookup"><span data-stu-id="76c23-105">PointOfService basics</span></span>

<span data-ttu-id="76c23-106">Dieser Abschnitt enthält Themen, die für alle Point of Service-Gerätekategorien gleich sind.</span><span class="sxs-lookup"><span data-stu-id="76c23-106">This section contains topics that are common across all Point of Service device categories.</span></span>

|<span data-ttu-id="76c23-107">Thema</span><span class="sxs-lookup"><span data-stu-id="76c23-107">Topic</span></span> |<span data-ttu-id="76c23-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="76c23-108">Description</span></span> |
|------|------------|
| [<span data-ttu-id="76c23-109">Funktionsdeklaration</span><span class="sxs-lookup"><span data-stu-id="76c23-109">Capability declaration</span></span>](pos-basics-capability.md)      | <span data-ttu-id="76c23-110">Erfahren Sie, wie Sie die Funktion **pointOfService** zu Ihrem Anwendungsmanifest hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="76c23-110">Learn how to add the **pointOfService** capability to your application manifest.</span></span>  <span data-ttu-id="76c23-111">Diese Funktion wird für die Verwendung des Windows.Devices.PointOfService-Namespace benötigt.</span><span class="sxs-lookup"><span data-stu-id="76c23-111">This capability is required for use of Windows.Devices.PointOfService namespace.</span></span>  |
| [<span data-ttu-id="76c23-112">Enumerieren von Geräten</span><span class="sxs-lookup"><span data-stu-id="76c23-112">Enumerating devices</span></span>](pos-basics-enumerating.md)        | <span data-ttu-id="76c23-113">Erfahren Sie, wie Sie eine Geräteauswahl definieren, die verwendet wird, um die im System verfügbaren Geräte abzufragen, und verwenden diese Auswahl, um Point of Service-Geräte aufzulisten.</span><span class="sxs-lookup"><span data-stu-id="76c23-113">Learn how to define a device selector that is used to query devices available to the system and use this selector to enumerate Point of Service devices.</span></span>  |
| [<span data-ttu-id="76c23-114">Erstellen eines Geräteobjekts</span><span class="sxs-lookup"><span data-stu-id="76c23-114">Creating a device object</span></span>](pos-basics-deviceobject.md)  | <span data-ttu-id="76c23-115">Erfahren Sie, wie Sie ein PointOfService-Geräteobjekt erstellen, das Ihnen den Zugriff auf schreibgeschützte Eigenschaften des Peripheriegeräts und die Beanspruchung der exklusiven Nutzung des Peripheriegeräts ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="76c23-115">Learn how to create a PointOfService device object that will give you access to read-only properties of the peripheral and claim the peripheral for exclusive use.</span></span> |
| [<span data-ttu-id="76c23-116">Anspruch und aktivieren</span><span class="sxs-lookup"><span data-stu-id="76c23-116">Claim and enable</span></span> ](pos-basics-claim.md)  | <span data-ttu-id="76c23-117">Informationen Sie zum Reservieren eines PointOfService-Peripheriegeräts für die exklusive Nutzung und für e/a-Vorgänge zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="76c23-117">Learn how to reserve a PointOfService peripheral for exclusive use and enable for I/O operations.</span></span>  |
| [<span data-ttu-id="76c23-118">Freigeben von Peripheriegeräten für andere Personen</span><span class="sxs-lookup"><span data-stu-id="76c23-118">Sharing peripherals with others</span></span>](pos-basics-sharing.md) | <span data-ttu-id="76c23-119">Erfahren Sie mehr über das Netzwerk oder verbundenen Bluetooth-Peripheriegeräte mit anderen Computern in einer Umgebung Teilen, in denen mehrere PCs auf Peripheriegeräte anstatt dedizierten auf jeden Computer angeschlossenen Peripheriegeräte angewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="76c23-119">Learn how to share network or Bluetooth connected peripherals with other computers in an environment where multiple PCs rely on shared peripherals rather than dedicated peripherals attached to each computer.</span></span>
| [<span data-ttu-id="76c23-120">PointOfService-End-to-end</span><span class="sxs-lookup"><span data-stu-id="76c23-120">PointOfService end-to-end</span></span>](pos-get-started.md)  | <span data-ttu-id="76c23-121">Dies ist ein End-to-End-Beispiel zum PointOfService-Peripheriegeräte unter Verwendung der obigen Beispielen interagieren.</span><span class="sxs-lookup"><span data-stu-id="76c23-121">This is an end to end example of how to interact with PointOfService peripherals utilizing the examples above.</span></span> |
|

## <a name="see-also"></a><span data-ttu-id="76c23-122">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="76c23-122">See also</span></span>

| <span data-ttu-id="76c23-123">Thema</span><span class="sxs-lookup"><span data-stu-id="76c23-123">Topic</span></span>   | <span data-ttu-id="76c23-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="76c23-124">Description</span></span> |
|:--------|:------------|
| [<span data-ttu-id="76c23-125">Anwendung Verteilung</span><span class="sxs-lookup"><span data-stu-id="76c23-125">Application distribution</span></span>](../publish/distribute-lob-apps-to-enterprises.md) | <span data-ttu-id="76c23-126">Informationen Sie zu den Optionen für Ihre app an Unternehmenskunden verteilen.</span><span class="sxs-lookup"><span data-stu-id="76c23-126">Learn about the options for distributing your app to enterprise customers.</span></span> |
| [<span data-ttu-id="76c23-127">App-Lebenszyklus</span><span class="sxs-lookup"><span data-stu-id="76c23-127">Application lifecycle</span></span>](../launch-resume/app-lifecycle.md) | <span data-ttu-id="76c23-128">Erfahren Sie mehr über den Lebenszyklus einer UWP-Anwendung und was geschieht, wenn Windows startet, anhält und Ihrer app fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="76c23-128">Learn about the life cycle of a UWP application and what happens when Windows launches, suspends, and resumes your app.</span></span> |
| [<span data-ttu-id="76c23-129">Anwendungsressourcen</span><span class="sxs-lookup"><span data-stu-id="76c23-129">Application resources</span></span>](../app-resources/index.md) | <span data-ttu-id="76c23-130">Enthält Informationen zum Erstellen, Paket, und nutzen, String, Bild- und Dateiressourcen Ihrer app.</span><span class="sxs-lookup"><span data-stu-id="76c23-130">Learn how to author, package, and consume your app's string, image, and file resources.</span></span> |
| [<span data-ttu-id="76c23-131">Datenbindung</span><span class="sxs-lookup"><span data-stu-id="76c23-131">Data binding</span></span>](../data-binding/index.md) | <span data-ttu-id="76c23-132">Erfahren Sie, wie Sie die Datenbindung verwenden, um Daten in der Benutzeroberfläche Ihrer app anzeigen.</span><span class="sxs-lookup"><span data-stu-id="76c23-132">Learn how to use data binding to display data in your app's UI.</span></span> |
| [<span data-ttu-id="76c23-133">Geräteenumeration</span><span class="sxs-lookup"><span data-stu-id="76c23-133">Device enumeration</span></span>](enumerate-devices.md) | <span data-ttu-id="76c23-134">Hier erfahren Sie verwenden erweiterter Enumeration Techniken, um Peripheriegeräte zu suchen.</span><span class="sxs-lookup"><span data-stu-id="76c23-134">Learn use advanced enumeration techniques to find your peripherals.</span></span>|
| [<span data-ttu-id="76c23-135">Adaptive Applications Version</span><span class="sxs-lookup"><span data-stu-id="76c23-135">Version adaptive applications</span></span>](../debug-test-perf/version-adaptive-apps.md) | <span data-ttu-id="76c23-136">Erläutert, wie Ihre app so entwerfen, dass sie auf mehrere Versionen von Windows 10 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="76c23-136">Lean how to design your app so that it runs on multiple versions of Windows 10.</span></span>|
|


## <a name="sample-code"></a><span data-ttu-id="76c23-137">Beispielcode</span><span class="sxs-lookup"><span data-stu-id="76c23-137">Sample code</span></span>
+ [<span data-ttu-id="76c23-138">Beispiel für Strichcodescanner</span><span class="sxs-lookup"><span data-stu-id="76c23-138">Barcode scanner sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BarcodeScanner)
+ [<span data-ttu-id="76c23-139">Beispiel für Kassenschubladen</span><span class="sxs-lookup"><span data-stu-id="76c23-139">Cash drawer sample</span></span>]( https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CashDrawer)
+ [<span data-ttu-id="76c23-140">Beispiel für Zeilenanzeigen</span><span class="sxs-lookup"><span data-stu-id="76c23-140">Line display sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/LineDisplay)
+ [<span data-ttu-id="76c23-141">Beispiel für Magnetstreifenleser</span><span class="sxs-lookup"><span data-stu-id="76c23-141">Magnetic stripe reader sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MagneticStripeReader)
+ [<span data-ttu-id="76c23-142">Beispiel für POS-Drucker</span><span class="sxs-lookup"><span data-stu-id="76c23-142">POSPrinter sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/PosPrinter)

