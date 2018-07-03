---
author: TerryWarwick
title: PointOfService-Gerätebeanspruchungsmodell
description: Weitere Informationen zum PointOfService-Beanspruchungsmodell
ms.author: jken
ms.date: 06/4/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Point Of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: 202234530945e55ef9c0d0fb68cf9ca83d2e15c3
ms.sourcegitcommit: ce45a2bc5ca6794e97d188166172f58590e2e434
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2018
ms.locfileid: "1983731"
---
# <a name="point-of-service-device-claim-model"></a>POS-Gerätebeanspruchungsmodell

## <a name="claiming-a-device-for-exclusive-use"></a>Beanspruchung der exklusiven Nutzung eines Geräts

Nachdem Sie erfolgreich ein PointOfService-Geräteobjekt erfolgreich erstellt haben, müssen Sie es mithilfe der entsprechenden Beanspruchungsmethode für den Gerätetyp beanspruchen, bevor Sie das Gerät für die Ein- und Ausgabe verwenden können.  Die Beanspruchung gewährt der Anwendung einen exklusiven Zugriff auf viele Funktionen des Geräts, um sicherzustellen, dass eine Anwendung die Verwendung des Geräts durch eine andere Anwendung nicht beeinträchtigt.  Es kann jeweils nur eine Anwendung die exklusive Verwendung eines PointOfService-Geräts beanspruchen. 

Im folgenden Beispiel ist gezeigt, wie Sie ein Strichcodescanner-Gerät beanspruchen, nachdem Sie erfolgreich ein Strichcodescanner-Objekt erstellt haben.

```Csharp
try
{
    claimedBarcodeScanner = await barcodeScanner.ClaimScannerAsync();
}
catch (Exception ex)
{
    Debug.WriteLine("EX: ClaimScannerAsync() - " + ex.Message);
}
```

> [!Warning]
> Ein Anspruch kann unter den folgenden Umständen verloren gehen:
> 1. Eine andere App hat einen Anspruch auf dasselbe Gerät angefordert, und Ihre App hat kein **RetainDevice** in Reaktion auf das Ereignis **ReleaseDeviceRequested** ausgestellt.  (Weitere Informationen finden Sie im Abschnitt [Anspruchsaushandlung](#Claim-negotiation) weiter unten).
> 2. Ihre App wurde unterbrochen, was dazu geführt hat, dass das Geräteobjekt geschlossen wurde und der Anspruch daher nicht mehr gültig ist. (Weitere Informationen finden Sie unter [Lebenszyklus von Geräteobjekten](pos-basics-deviceobject.md#device-object-lifecycle).)

### <a name="apis-used-for-claiming"></a>Für die Beanspruchung verwendete APIs

|Gerät|Anspruch |
|-|:-|
|BarcodeScanner | [ClaimScannerAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.claimscannerasync) | 
|CashDrawer | [ClaimDrawerAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.cashdrawer.claimdrawerasync) | 
|LineDisplay | [ClaimAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.linedisplay.claimasync) |
|MagneticStripeReader | [ClaimReaderAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereader.claimreaderasync) | 
|PosPrinter | [ClaimPrinterAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.posprinter.claimprinterasync) | 
|

## <a name="claim-negotiation"></a>Anspruchsaushandlung

Da Windows eine Multitaskingumgebung ist, fordern möglicherweise mehrere Anwendungen auf demselben Computer einen Zugriff auf Peripheriegeräte auf kooperative Weise an.  Die PointOfService-APIs bieten ein Aushandlungsmodell, das mehreren Anwendungen die gemeinsame Verwendung von an den Computer angeschlossenen Peripheriegeräten ermöglicht.

Wenn eine zweite Anwendung auf demselben Computer ein PointOfService-Peripheriegerät beansprucht, das bereits von einer anderen Anwendung in Anspruch genommen wird, wird eine **ReleaseDeviceRequested**-Ereignisbenachrichtigung veröffentlicht. Die Anwendung mit dem aktiven Anspruch muss auf die Ereignisbenachrichtigung reagieren, indem **RetainDevice** aufgerufen wird, wenn die Anwendung das Gerät derzeit verwendet, damit der Anspruch nicht verloren geht. 

Wenn die Anwendung mit dem aktiven Anspruch nicht sofort mit **RetainDevice** antwortet, wird davon ausgegangen, dass die Anwendung unterbrochen wurde oder das Gerät nicht benötigt, und der Anspruch wird widerrufen und an die neue Anwendung übergeben. 

In diesem Beispiel wird veranschaulicht, wie der Anspruch auf einen Strichcodescanner aufrechterhalten wird, wenn eine andere App fordert, das Gerät freizugegeben.  

```Csharp
claimedBarcodeScanner.ReleaseDeviceRequested += claimedBarcodeScanner_ReleaseDeviceRequested;

void claimedBarcodeScanner_ReleaseDeviceRequested(object sender, ClaimedBarcodeScanner myScanner)
{
    // Retain exclusive access to the device
    myScanner.RetainDevice();  
}
```
### <a name="apis-used-for-claim-negotiation"></a>Für die Anspruchsaushandlung verwendete APIs

|Beanspruchtes Gerät|Benachrichtigungsversion| Gerät beibehalten |
|-|:-|:-|
|ClaimedBarcodeScanner | [ReleaseDeviceRequested](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.releasedevicerequested) | [RetainDevice](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.retaindevice)
|ClaimedCashDrawer | [ReleaseDeviceRequested](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedcashdrawer.releasedevicerequested) | [RetainDevice](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedcashdrawer.retaindevice)
|ClaimedLineDisplay | [ReleaseDeviceRequested](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedlinedisplay.releasedevicerequested) | [RetainDevice](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedlinedisplay.retaindevice)
|ClaimedMagneticStripeReader | [ReleaseDeviceRequested](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedmagneticstripereader.releasedevicerequested) | [RetainDevice](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedlinedisplay.retaindevice)
|ClaimedPosPrinter | [ReleaseDeviceRequested](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedposprinter.releasedevicerequested) | [RetainDevice](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedposprinter.retaindevice)
|
