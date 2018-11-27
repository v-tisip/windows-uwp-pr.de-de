---
title: PointOfService gemeinsame Nutzung von Geräten
description: PointOfService-Peripheriegeräte freigeben für andere Personen
ms.date: 06/14/2018
ms.topic: article
keywords: Windows 10, UWP, Point of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: 53dc22b2aa35b5e69854f6fb489ff6a454c73bf6
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7699087"
---
# <a name="pointofservice-device-sharing"></a>PointOfService gemeinsame Nutzung von Geräten

Erfahren Sie mehr über das Netzwerk oder verbundenen Bluetooth-Peripheriegeräte mit anderen Computern in einer Umgebung Teilen, in denen mehrere PCs auf Peripheriegeräte anstatt dedizierten auf jeden Computer angeschlossenen Peripheriegeräte angewiesen sind.

## <a name="device-sharing"></a>Gemeinsame Nutzung von Geräten

Netzwerk- und Bluetooth verbundenen PointOfService-Peripheriegeräte normalerweise verwendet werden, in einer Umgebung Wheere teilen sich mehrere Clientgeräte dieselben Peripheriegeräte ganzen Tag.  In einer ausgelastete Einzelhandel oder Essen Services-Umgebung wirkt sich jegliche Verzögerung in die Möglichkeit für einen Client-Gerät an ein Peripheriegerät Anfügen auf die Effizienz, in der ein zuordnen kann eine Transaktion mit dem Kunden zu schließen und auf die weiter. In einem schnellen Service Restaurant-Szenario, in denen eine Belegdrucker als Küche Drucker verwendet wird, um die Details der Bestellung des Kunden in die Küche zur Vorbereitung übertragen, werden mehrere Client-Geräte, die Kunden Aufträge verliert.  Nach Abschluss die Reihenfolge sollte jedes Client-Gerät in der Lage beansprucht den freigegebenen Drucker und die Reihenfolge für die Küche ist immer sofort zu drucken.

In diesen Umgebungen ist es wichtig für die Anwendung von vollständig **dispose** das Geräteobjekt, damit eine andere dasselbe Gerät geltend machen kann.

Freigeben von einen PosPrinter am Ende eines "using"-Blocks

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
