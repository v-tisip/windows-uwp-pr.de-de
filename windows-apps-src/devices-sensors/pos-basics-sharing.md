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
# <a name="pointofservice-device-sharing"></a>PointOfService gemeinsame Nutzung von Geräten

Erfahren Sie mehr über das Netzwerk oder verbundenen Bluetooth-Peripheriegeräte mit anderen Computern in einer Umgebung freigeben, in denen mehrere PCs auf Peripheriegeräte anstatt dedizierten auf jeden Computer angeschlossenen Peripheriegeräte angewiesen sind.

## <a name="device-sharing"></a>Gemeinsame Nutzung von Geräten

Netzwerk- und Bluetooth verbundenen PointOfService-Peripheriegeräte normalerweise verwendet werden, in einer Umgebung Wheere teilen sich mehrere Clientgeräte dieselben Peripheriegeräte ganzen Tag.  In einer ausgelastet Einzelhandel oder Essen Services-Umgebung hat jegliche Verzögerung beim die Möglichkeit für einen Client-Gerät an ein Peripheriegerät anfügen eine Auswirkung auf die Effizienz, in der ein zuordnen schließen eine Transaktion mit dem Kunden und fahren Sie mit der nächsten kann. In einem schnellen Service Restaurant Szenario, in denen eine Belegdrucker als Küche Drucker verwendet wird, um die Details der Bestellung des Kunden in die Küche ist immer zur Vorbereitung übertragen, werden mehrere Clientgeräte Kunden Aufträge verliert.  Nach Abschluss die Reihenfolge sollte jedes Client-Gerät in der Lage beansprucht den freigegebenen Drucker und die Reihenfolge für die Küche ist immer sofort zu drucken.

In diesen Umgebungen ist es wichtig für die Anwendung von vollständig **dispose** das Geräteobjekt, sodass ein anderes dasselbe Gerät geltend machen kann.

Freigeben von einen PosPrinter am Ende eines "using"-Blocks befinden

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


Freigeben von einen PosPrinter durch Aufrufen von Dispose() explizit

```Csharp 
using Windows.Devices.PointOfService;

PosPrinter printer = await PosPrinter.FromIdAsync("Device ID");
if (printer != null)
{
    // Exercise the printer, then dispose of the printer explicitly.
    printer.Dispose();
}
```

## <a name="api-methods-used"></a>API-Methoden verwendet 

+ [BarcodeScanner.Dispose](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.dispose) 
+ [CashDrawer.Dispose](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.cashdrawer.dispose) 
+ [LineDisplay.Dispose](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.linedisplay.dispose) 
+ [MagneticStripeReader.Dispose](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereader.dispose)  
+ [PosPrinter.Dispose](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.posprinter.dispose) 


[!INCLUDE [feedback](./includes/pos-feedback.md)]
