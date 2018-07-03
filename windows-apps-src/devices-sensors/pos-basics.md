---
author: TerryWarwick
title: Erste Schritte mit Point Of Service-Geräten
description: Dieser Artikel enthält Informationen für die ersten Schritte mit PointOfService-UWP-Apps.
ms.author: jken
ms.date: 05/1/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Point Of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: a0583adbcef9e45dfe0b2e56e03ce7e0451ac5bb
ms.sourcegitcommit: ce45a2bc5ca6794e97d188166172f58590e2e434
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2018
ms.locfileid: "1983543"
---
# <a name="getting-started-with-point-of-service"></a><span data-ttu-id="f3205-104">Erste Schritte mit Point Of Service-Geräten</span><span class="sxs-lookup"><span data-stu-id="f3205-104">Getting started with Point of Service</span></span>

<span data-ttu-id="f3205-105">Dieser Abschnitt enthält Themen, die für alle Point of Service-Gerätekategorien gleich sind.</span><span class="sxs-lookup"><span data-stu-id="f3205-105">This section contains topics that are common across all Point of Service device categories.</span></span>

|<span data-ttu-id="f3205-106">Thema</span><span class="sxs-lookup"><span data-stu-id="f3205-106">Topic</span></span> |<span data-ttu-id="f3205-107">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f3205-107">Description</span></span> |
|------|------------|
| [<span data-ttu-id="f3205-108">Funktionsdeklaration</span><span class="sxs-lookup"><span data-stu-id="f3205-108">Capability declaration</span></span>](pos-basics-capability.md)      | <span data-ttu-id="f3205-109">Erfahren Sie, wie Sie die Funktion **pointOfService** zu Ihrem Anwendungsmanifest hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f3205-109">Learn how to add the **pointOfService** capability to your application manifest.</span></span>  <span data-ttu-id="f3205-110">Diese Funktion wird für die Verwendung des Windows.Devices.PointOfService-Namespace benötigt.</span><span class="sxs-lookup"><span data-stu-id="f3205-110">This capability is required for use of Windows.Devices.PointOfService namespace.</span></span>  |
| [<span data-ttu-id="f3205-111">Enumerieren von Geräten</span><span class="sxs-lookup"><span data-stu-id="f3205-111">Enumerating devices</span></span>](pos-basics-enumerating.md)        | <span data-ttu-id="f3205-112">Erfahren Sie, wie Sie eine Geräteauswahl definieren, die verwendet wird, um die im System verfügbaren Geräte abzufragen, und verwenden diese Auswahl, um Point of Service-Geräte aufzulisten.</span><span class="sxs-lookup"><span data-stu-id="f3205-112">Learn how to define a device selector that is used to query devices available to the system and use this selector to enumerate Point of Service devices.</span></span>  |
| [<span data-ttu-id="f3205-113">Erstellen eines Geräteobjekts</span><span class="sxs-lookup"><span data-stu-id="f3205-113">Creating a device object</span></span>](pos-basics-deviceobject.md)  | <span data-ttu-id="f3205-114">Erfahren Sie, wie Sie ein PointOfService-Geräteobjekt erstellen, das Ihnen den Zugriff auf schreibgeschützte Eigenschaften des Peripheriegeräts und die Beanspruchung der exklusiven Nutzung des Peripheriegeräts ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="f3205-114">Learn how to create a PointOfService device object that will give you access to read-only properties of the peripheral and claim the peripheral for exclusive use.</span></span> |
| [<span data-ttu-id="f3205-115">Beanspruchung der exklusiven Nutzung eines Geräts</span><span class="sxs-lookup"><span data-stu-id="f3205-115">Claiming a device for exclusive use</span></span> ](pos-basics-claim.md)  | <span data-ttu-id="f3205-116">Erfahren Sie, wie Sie mit dem PointOfService-Anspruchsmodell die exklusive Nutzung eines PointOfService-Peripheriegeräts reservieren, während gleichzeitig andere Anwendungen auf demselben Computer auf das PointOfService-Peripheriegerät zugreifen können, wenn sie eine exklusive Nutzung benötigen.</span><span class="sxs-lookup"><span data-stu-id="f3205-116">Learn how to reserve a PointOfService peripheral for exclusive use with the PointOfService claim model while allowing other applications on the same computer access to the PointOfService peripheral when they need exclusive use.</span></span>  |
|

## <a name="see-also"></a><span data-ttu-id="f3205-117">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f3205-117">See also</span></span>
[<span data-ttu-id="f3205-118">Erste Schritte mit Windows.Devices.PointOfService</span><span class="sxs-lookup"><span data-stu-id="f3205-118">Getting started with Windows.Devices.PointOfService</span></span>](pos-get-started.md)


## <a name="sample-code"></a><span data-ttu-id="f3205-119">Beispielcode</span><span class="sxs-lookup"><span data-stu-id="f3205-119">Sample code</span></span>
+ [<span data-ttu-id="f3205-120">Beispiel für Strichcodescanner</span><span class="sxs-lookup"><span data-stu-id="f3205-120">Barcode scanner sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BarcodeScanner)
+ [<span data-ttu-id="f3205-121">Beispiel für Kassenschubladen</span><span class="sxs-lookup"><span data-stu-id="f3205-121">Cash drawer sample</span></span>]( https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CashDrawer)
+ [<span data-ttu-id="f3205-122">Beispiel für Zeilenanzeigen</span><span class="sxs-lookup"><span data-stu-id="f3205-122">Line display sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/LineDisplay)
+ [<span data-ttu-id="f3205-123">Beispiel für Magnetstreifenleser</span><span class="sxs-lookup"><span data-stu-id="f3205-123">Magnetic stripe reader sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MagneticStripeReader)
+ [<span data-ttu-id="f3205-124">Beispiel für POS-Drucker</span><span class="sxs-lookup"><span data-stu-id="f3205-124">POSPrinter sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/PosPrinter)

