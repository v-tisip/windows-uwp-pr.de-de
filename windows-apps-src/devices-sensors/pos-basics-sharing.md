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
ms.sourcegitcommit: cbe7cf620622a5e4df7414f9e38dfecec1cfca99
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "7445676"
---
# <a name="pointofservice-device-sharing"></a><span data-ttu-id="46a90-104">PointOfService gemeinsame Nutzung von Geräten</span><span class="sxs-lookup"><span data-stu-id="46a90-104">PointOfService device sharing</span></span>

<span data-ttu-id="46a90-105">Erfahren Sie mehr über das Netzwerk oder verbundenen Bluetooth-Peripheriegeräte mit anderen Computern in einer Umgebung Teilen, in denen mehrere PCs auf Peripheriegeräte anstatt dedizierten auf jeden Computer angeschlossenen Peripheriegeräte angewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="46a90-105">Learn how to share network or Bluetooth connected peripherals with other computers in an environment where multiple PCs rely on shared peripherals rather than dedicated peripherals attached to each computer.</span></span>

## <a name="device-sharing"></a><span data-ttu-id="46a90-106">Gemeinsame Nutzung von Geräten</span><span class="sxs-lookup"><span data-stu-id="46a90-106">Device sharing</span></span>

<span data-ttu-id="46a90-107">Netzwerk- und Bluetooth verbundenen PointOfService-Peripheriegeräte normalerweise verwendet werden, in einer Umgebung Wheere teilen sich mehrere Clientgeräte dieselben Peripheriegeräte ganzen Tag.</span><span class="sxs-lookup"><span data-stu-id="46a90-107">Network and Bluetooth connected PointOfService peripherals are typically used in an environment wheere multiple client devices are sharing the same peripherals throughout the day.</span></span>  <span data-ttu-id="46a90-108">In einer ausgelastete Einzelhandel oder Essen Services-Umgebung wirkt sich jegliche Verzögerung in die Möglichkeit für einen Client-Gerät an ein Peripheriegerät Anfügen auf die Effizienz, in der ein zuordnen kann eine Transaktion mit dem Kunden zu schließen und auf die weiter.</span><span class="sxs-lookup"><span data-stu-id="46a90-108">In a busy retail or food services environment any delay in the ability for a client device to attach to a peripheral has an impact on the efficiency in which an associate can close a transaction with the customer and move on to the next.</span></span> <span data-ttu-id="46a90-109">In einem schnellen Service Restaurant-Szenario, in denen eine Belegdrucker als Küche Drucker verwendet wird, um die Details der Bestellung des Kunden in die Küche zur Vorbereitung übertragen, werden mehrere Client-Geräte, die Kunden Aufträge verliert.</span><span class="sxs-lookup"><span data-stu-id="46a90-109">In a quick service restaurant scenario where a receipt printer is used as a kitchen printer to transfer the details of a customer's order to the kitchen for preparation there will be multiple client devices taking orders from customers.</span></span>  <span data-ttu-id="46a90-110">Nach Abschluss die Reihenfolge sollte jedes Client-Gerät in der Lage beansprucht den freigegebenen Drucker und die Reihenfolge für die Küche ist immer sofort zu drucken.</span><span class="sxs-lookup"><span data-stu-id="46a90-110">Once the order is complete each client device should be able to claim the shared printer and immediately print the order for the kitchen.</span></span>

<span data-ttu-id="46a90-111">In diesen Umgebungen ist es wichtig für die Anwendung von vollständig **dispose** das Geräteobjekt, damit eine andere dasselbe Gerät geltend machen kann.</span><span class="sxs-lookup"><span data-stu-id="46a90-111">In these environments, it is important for the application to fully **dispose** the device object so that another can claim the same device.</span></span>

<span data-ttu-id="46a90-112">Freigeben von einen PosPrinter am Ende eines "using"-Blocks</span><span class="sxs-lookup"><span data-stu-id="46a90-112">Disposing of a PosPrinter at the end of a ‘using’ block</span></span>

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


<span data-ttu-id="46a90-113">Freigeben von einen PosPrinter durch Aufrufen von Dispose() explizit</span><span class="sxs-lookup"><span data-stu-id="46a90-113">Disposing of a PosPrinter by calling Dispose() explicitly</span></span>

```Csharp 
using Windows.Devices.PointOfService;

PosPrinter printer = await PosPrinter.FromIdAsync("Device ID");
if (printer != null)
{
    // Exercise the printer, then dispose of the printer explicitly.
    printer.Dispose();
}
```

## <a name="api-methods-used"></a><span data-ttu-id="46a90-114">API-Methoden verwendet</span><span class="sxs-lookup"><span data-stu-id="46a90-114">API methods used</span></span> 

+ [<span data-ttu-id="46a90-115">BarcodeScanner.Dispose</span><span class="sxs-lookup"><span data-stu-id="46a90-115">BarcodeScanner.Dispose</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.dispose) 
+ [<span data-ttu-id="46a90-116">CashDrawer.Dispose</span><span class="sxs-lookup"><span data-stu-id="46a90-116">CashDrawer.Dispose</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.cashdrawer.dispose) 
+ [<span data-ttu-id="46a90-117">LineDisplay.Dispose</span><span class="sxs-lookup"><span data-stu-id="46a90-117">LineDisplay.Dispose</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.linedisplay.dispose) 
+ [<span data-ttu-id="46a90-118">MagneticStripeReader.Dispose</span><span class="sxs-lookup"><span data-stu-id="46a90-118">MagneticStripeReader.Dispose</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereader.dispose)  
+ [<span data-ttu-id="46a90-119">PosPrinter.Dispose</span><span class="sxs-lookup"><span data-stu-id="46a90-119">PosPrinter.Dispose</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.posprinter.dispose) 


[!INCLUDE [feedback](./includes/pos-feedback.md)]
