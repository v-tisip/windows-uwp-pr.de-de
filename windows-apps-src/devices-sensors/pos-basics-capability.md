---
author: TerryWarwick
title: PointOfService-Gerätefunktion
description: Die PointOfService-Gerätefunktion wird für die Verwendung des Windows.Devices.PointOfService-Namespace benötigt.
ms.author: jken
ms.date: 05/1/2018
ms.topic: article
keywords: Windows 10, UWP, Point Of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: dbed55af1a9fa3df14f0a7e3e7c6d1f599b40fd3
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7566630"
---
# <a name="pointofservice-device-capability"></a><span data-ttu-id="9b56d-104">PointOfService-Gerätefunktion</span><span class="sxs-lookup"><span data-stu-id="9b56d-104">PointOfService device capability</span></span>
<span data-ttu-id="9b56d-105">Sie fordern Zugriff auf die PointOfService-APIs an, indem Sie die Funktion in Ihrem Anwendungspaketmanifest deklarieren. Sie können die meisten Funktionen mithilfe des Manifest-Designers in Microsoft Visual Studio deklarieren, oder Sie können sie manuell hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="9b56d-105">You request access to the PointOfService APIs by declaring the capability in your application package manifest]  You can declare most capabilities by using the Manifest Designer, in Microsoft Visual Studio, or you can add them manually.</span></span>  

> [!Important]
> <span data-ttu-id="9b56d-106">Sie erhalten die Fehlermeldung **System.UnauthorizedAccessException**, wenn Sie versuchen, eine API im Namespace Windows.Devices.PointOfService zu verwenden, wenn Sie keine **pointOfService**-Funktion in Ihrem Anwendungsmanifest deklarieren.</span><span class="sxs-lookup"><span data-stu-id="9b56d-106">You will receive the error **System.UnauthorizedAccessException** when you attempt to use an API in the Winodws.Devices.PointOfService namespace if you do not declare the **pointOfService** capability in your application manifest.</span></span> 

## <a name="declare-capability-using-manifest-designer"></a><span data-ttu-id="9b56d-107">Deklarieren von Funktionen mithilfe des Manifest-Designers</span><span class="sxs-lookup"><span data-stu-id="9b56d-107">Declare capability using Manifest Designer</span></span>

1. <span data-ttu-id="9b56d-108">Erweitern Sie im **Projektmappen-Explorer** den Projektknoten Ihrer UWP-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="9b56d-108">In **Solution Explorer**, expand the project node of your UWP application.</span></span>
2. <span data-ttu-id="9b56d-109">Doppelklicken Sie auf die Datei **Package.appxmanifest**.</span><span class="sxs-lookup"><span data-stu-id="9b56d-109">Double-click the **Package.appxmanifest** file.</span></span>  
*<span data-ttu-id="9b56d-110">Wenn die Manifestdatei bereits in der XML-Codeansicht geöffnet ist, werden Sie von Visual Studio zum Schließen der Datei aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="9b56d-110">If the manifest file is already open in the XML code view, Visual Studio prompts you to close the file.</span></span>*
3. <span data-ttu-id="9b56d-111">Öffnen Sie die Registerkarte **Funktionen**.</span><span class="sxs-lookup"><span data-stu-id="9b56d-111">Click the **Capabilities** tab</span></span>
4. <span data-ttu-id="9b56d-112">Klicken Sie auf das Kontrollkästchen neben **Point of Service** in der Liste der Funktionen, um die Funktionalität des Point-of-Service-Geräts zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="9b56d-112">Click the checkbox next to **Point of Service** in the list of capabilities to enable the Point of Service device capability</span></span>


## <a name="declare-capability-manually"></a><span data-ttu-id="9b56d-113">Manuelles Deklarieren eines Funktion</span><span class="sxs-lookup"><span data-stu-id="9b56d-113">Declare capability manually</span></span>

1. <span data-ttu-id="9b56d-114">Erweitern Sie im **Projektmappen-Explorer** den Projektknoten Ihrer UWP-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="9b56d-114">In **Solution Explorer**, expand the project node of your UWP application.</span></span>
2. <span data-ttu-id="9b56d-115">Klicken Sie mit der rechten Maustaste auf die Datei **Package.appxmanifest**, und wählen Sie die Option **Code anzeigen** aus.</span><span class="sxs-lookup"><span data-stu-id="9b56d-115">Right-click the **Package.appxmanifest** file and choose **View Code**</span></span>
3. <span data-ttu-id="9b56d-116">Fügen Sie das PointOfService DeviceCapability-Element zum Abschnitt mit den Funktionen Ihres Anwendungsmanifests hinzu.</span><span class="sxs-lookup"><span data-stu-id="9b56d-116">Add the PointOfService DeviceCapability element to Capabilities section of your application manifest.</span></span>  

```xml
  <Capabilities>
    <DeviceCapability Name="pointOfService" />
  </Capabilities>
   ```
