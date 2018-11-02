---
author: TerryWarwick
title: PointOfService gemeinsame Nutzung von Geräten
description: PointOfService-Peripheriegeräte freigeben für andere Personen
ms.author: jken
ms.date: 06/14/2018
ms.topic: article
keywords: Windows 10, UWP, Point of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: 591ba592d1c17b03ae29c6fb98ef546bc18b8bdc
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5937163"
---
# <a name="pointofservice-device-sharing"></a><span data-ttu-id="4c3bc-104">PointOfService gemeinsame Nutzung von Geräten</span><span class="sxs-lookup"><span data-stu-id="4c3bc-104">PointOfService device sharing</span></span>

<span data-ttu-id="4c3bc-105">Erfahren Sie mehr über das Netzwerk oder verbundenen Bluetooth-Peripheriegeräte mit anderen Computern in einer Umgebung freigeben, in denen mehrere PCs auf Peripheriegeräte anstatt dedizierten auf jeden Computer angeschlossenen Peripheriegeräte angewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="4c3bc-105">Learn how to share network or Bluetooth connected peripherals with other computers in an environment where multiple PCs rely on shared peripherals rather than dedicated peripherals attached to each computer.</span></span>

## <a name="device-sharing"></a><span data-ttu-id="4c3bc-106">Gemeinsame Nutzung von Geräten</span><span class="sxs-lookup"><span data-stu-id="4c3bc-106">Device sharing</span></span>

<span data-ttu-id="4c3bc-107">Netzwerk- und Bluetooth verbundenen PointOfService-Peripheriegeräte normalerweise verwendet werden, in einer Umgebung Wheere teilen sich mehrere Clientgeräte dieselben Peripheriegeräte ganzen Tag.</span><span class="sxs-lookup"><span data-stu-id="4c3bc-107">Network and Bluetooth connected PointOfService peripherals are typically used in an environment wheere multiple client devices are sharing the same peripherals throughout the day.</span></span>  <span data-ttu-id="4c3bc-108">In einer ausgelastet Einzelhandel oder Essen Services-Umgebung hat jegliche Verzögerung beim die Möglichkeit für einen Client-Gerät an ein Peripheriegerät anfügen eine Auswirkung auf die Effizienz, in der ein zuordnen schließen eine Transaktion mit dem Kunden und fahren Sie mit der nächsten kann.</span><span class="sxs-lookup"><span data-stu-id="4c3bc-108">In a busy retail or food services environment any delay in the ability for a client device to attach to a peripheral has an impact on the efficiency in which an associate can close a transaction with the customer and move on to the next.</span></span> <span data-ttu-id="4c3bc-109">In einem schnellen Service Restaurant Szenario, in denen eine Belegdrucker als Küche Drucker verwendet wird, um die Details der Bestellung des Kunden in die Küche ist immer zur Vorbereitung übertragen, werden mehrere Clientgeräte Kunden Aufträge verliert.</span><span class="sxs-lookup"><span data-stu-id="4c3bc-109">In a quick service restaurant scenario where a receipt printer is used as a kitchen printer to transfer the details of a customer's order to the kitchen for preparation there will be multiple client devices taking orders from customers.</span></span>  <span data-ttu-id="4c3bc-110">Nach Abschluss die Reihenfolge sollte jedes Client-Gerät in der Lage beansprucht den freigegebenen Drucker und die Reihenfolge für die Küche ist immer sofort zu drucken.</span><span class="sxs-lookup"><span data-stu-id="4c3bc-110">Once the order is complete each client device should be able to claim the shared printer and immediately print the order for the kitchen.</span></span>

<span data-ttu-id="4c3bc-111">In diesen Umgebungen ist es wichtig für die Anwendung von vollständig **dispose** das Geräteobjekt, sodass ein anderes dasselbe Gerät geltend machen kann.</span><span class="sxs-lookup"><span data-stu-id="4c3bc-111">In these environments, it is important for the application to fully **dispose** the device object so that another can claim the same device.</span></span>

<span data-ttu-id="4c3bc-112">Freigeben von einen PosPrinter am Ende eines "using"-Blocks befinden</span><span class="sxs-lookup"><span data-stu-id="4c3bc-112">Disposing of a PosPrinter at the end of a ‘using’ block</span></span>

```Csharp 
using Windows.Devices.PointOfService;
using(PosPrinter printer = await PosPrinter.FromIdAsync("Device ID"))
{
    if (printer != null)
    {
        // Exercise the printer.
    }

    // When leaving this scope, printer.Dispose() is automatically invoked, 
    // releasing the session we have with the printer.
}
```


<span data-ttu-id="4c3bc-113">Freigeben von einen PosPrinter durch Aufrufen von Dispose() explizit</span><span class="sxs-lookup"><span data-stu-id="4c3bc-113">Disposing of a PosPrinter by calling Dispose() explicitly</span></span>

```Csharp 
using Windows.Devices.PointOfService;

PosPrinter printer = await PosPrinter.FromIdAsync("Device ID");
if (printer != null)
{
    // Exercise the printer, then dispose of the printer explicitly.
    printer.Dispose();
}
```

## <a name="api-methods-used"></a><span data-ttu-id="4c3bc-114">API-Methoden verwendet</span><span class="sxs-lookup"><span data-stu-id="4c3bc-114">API methods used</span></span> 

+ [<span data-ttu-id="4c3bc-115">BarcodeScanner.Dispose</span><span class="sxs-lookup"><span data-stu-id="4c3bc-115">BarcodeScanner.Dispose</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.dispose) 
+ [<span data-ttu-id="4c3bc-116">CashDrawer.Dispose</span><span class="sxs-lookup"><span data-stu-id="4c3bc-116">CashDrawer.Dispose</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.cashdrawer.dispose) 
+ [<span data-ttu-id="4c3bc-117">LineDisplay.Dispose</span><span class="sxs-lookup"><span data-stu-id="4c3bc-117">LineDisplay.Dispose</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.linedisplay.dispose) 
+ [<span data-ttu-id="4c3bc-118">MagneticStripeReader.Dispose</span><span class="sxs-lookup"><span data-stu-id="4c3bc-118">MagneticStripeReader.Dispose</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereader.dispose)  
+ [<span data-ttu-id="4c3bc-119">PosPrinter.Dispose</span><span class="sxs-lookup"><span data-stu-id="4c3bc-119">PosPrinter.Dispose</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.posprinter.dispose) 


[!INCLUDE [feedback](./includes/pos-feedback.md)]
