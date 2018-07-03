---
author: TerryWarwick
title: Auflisten von PointOfService-Geräten
description: Hier erfahren Sie, wie Sie PointOfService Geräte auflisten.
ms.author: jken
ms.date: 06/8/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Point of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: be1fdc42295fc03ff86a69e287a4089abe547689
ms.sourcegitcommit: ee77826642fe8fd9cfd9858d61bc05a96ff1bad7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "2018438"
---
# <a name="enumerating-point-of-service-devices"></a>Auflisten von Point of Service-Geräten
In diesem Abschnitt erfahren Sie, wie Sie [**eine Geräteauswahl definieren**](https://docs.microsoft.com/windows/uwp/devices-sensors/build-a-device-selector), die verwendet wird, um die im System verfügbaren Geräte abzufragen, und verwenden diese Auswahl, um Point of Service-Geräte mithilfe einer der folgenden Methoden aufzulisten:

**Methode 1:** [**Abrufen des ersten verfügbaren Geräts**](#Method-1:-get-first-available-device)<br />In diesem Abschnitt erfahren Sie, wie Sie mithilfe von **GetDefaultAsync** auf das erste verfügbare Gerät in einer bestimmten PointOfService Geräteklasse zugreifen.

**Methode 2:** [**Momentaufnahmen von Geräten**](#Method-2:-Snapshot-of-devices)<br />In diesem Abschnitterfahren Sie, wie Sie eine Momentaufnahme der PointOfService-Geräte auflisten, die zu einem bestimmten Zeitpunkt auf dem System vorhanden sind. Dies ist nützlich, wenn Sie eine eigene Benutzeroberfläche erstellen möchten oder Geräte auflisten müssen, ohne dem Benutzer eine Benutzeroberfläche anzuzeigen. FindAllAsync hält Ergebnisse zurück, bis die gesamte Auflistung abgeschlossen ist.

**Methode 3:** [**Auflisten und Überwachen**](#Method-3:-Enumerate-and-watch)<br />In diesem Abschnitterfahren Sie mehr über ein leistungsfähigeres und flexibleres Auflistungsmodell, mit dem Sie Geräte auflisten können, die derzeit vorhanden sind, und außerdem Benachrichtigungen empfangen, wenn Geräte hinzugefügt oder aus dem System entfernt werden.  Dies ist hilfreich, wenn Sie eine aktuelle Liste von Geräten im Hintergrund zur Anzeige auf Ihrer Benutzeroberfläche verwalten möchten, statt darauf zu warten, bis eine Momentaufnahme erstellt wird.
 

---
## <a name="define-a-device-selector"></a>Definieren einer Geräteauswahl
Mit einer Geräteauswahl können Sie die Geräte begrenzen, die Sie beim Auflisten von Geräten durchsuchen.  Dadurch können Sie nur relevante Ergebnisse abrufen und die Zeit verkürzen, die benötigt wird, um die gewünschten Geräte aufzulisten.  

Mithilfe von [**GetDeviceSelector**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.posprinter.getdeviceselector#Windows_Devices_PointOfService_PosPrinter_GetDeviceSelector) erhalten Sie eine Auswahl zum Auflisten aller mit dem System verbundener POSPrinters, einschließlich USB-, Netzwerk- und Bluetooth-POSPrinters.

```Csharp
using Windows.Devices.PointOfService;

string selector = POSPrinter.GetDeviceSelector();   

```

Mithilfe der Methode [**GetDeviceSelector**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.posprinter.getdeviceselector#Windows_Devices_PointOfService_PosPrinter_GetDeviceSelector_Windows_Devices_PointOfService_PosConnectionTypes_), die [**PosConnectionTypes**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.posconnectiontypes) als Parameter akzeptiert, können Sie Ihre Auswahl zum Auflisten von lokalen, Netzwerk- oder per Bluetooth verbundener POSPrinters einschränken und so die für das Abschließen der Abfrage erforderliche Zeit verkürzen.  Das folgende Beispiel zeigt die Verwendung dieser Methode zum Definieren einer Auswahl, die nur lokal verbundene POSPrinters unterstützt.

 ```Csharp
using Windows.Devices.PointOfService;

string selector = POSPrinter.GetDeviceSelector(PosConnectionTypes.Local);   

```
> [!TIP]
> Weitere Informationen zum Erstellen umfangreicherer Auswahlzeichenfolgen finden Sie unter [**Erstellen einer Geräteauswahl**](https://docs.microsoft.com/windows/uwp/devices-sensors/build-a-device-selector).

---

## <a name="method-1-get-first-available-device"></a>Methode 1: Abrufen des ersten verfügbaren Geräts

Die einfachste Möglichkeit zum Abrufen eines PointOfService-Geräts ist die Verwendung von **GetDefaultAsync** zum Abrufen des ersten verfügbaren Geräts in einer PointOfService-Geräteklasse. 

Das folgende Beispiel veranschaulicht die Verwendung von [**GetDefaultAsync**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.getdefaultasync#Windows_Devices_PointOfService_BarcodeScanner_GetDefaultAsync) für BarcodeScanner. Das Codierungsmuster ist für alle PointOfService-Geräteklassen ähnlich.

```Csharp

using Windows.Devices.PointOfService;

BarcodeScanner barcodeScanner = await BarcodeScanner.GetDefaultAsync();

```

> [!CAUTION]
> GetDefaultAsync muss mit Vorsicht verwendet werden, da möglicherweise von einer Sitzung zur nächsten ein anderes Gerät zurückgegeben wird. Viele Ereignisse können diese Auflistung beeinflussen und zu einem anderen ersten verfügbaren Gerät führen, darunter: 
> - Änderung bei den an Ihren Computer angeschlossenen Kameras 
> - Änderung bei den an Ihren Computer angeschlossenen PointOfService-Geräten
> - Änderung bei den über das Netzwerk angeschlossen PointOfService-Geräten, die in Ihrem Netzwerk verfügbar sind
> - Änderung bei den Bluetooth-PointOfService-Geräten in Reichweite Ihres Computers 
> - Änderungen an der PointOfService-Konfiguration 
> - Installation von Treibern oder OPOS-Serviceobjekten
> - Installation von PointOfService-Erweiterungen
> - Updates am Windows-Betriebssystem

---

## <a name="method-2-snapshot-of-devices"></a>Methode 2: Momentaufnahmen von Geräten

In einigen Szenarien möchten Sie vielleicht eine eigene Benutzeroberfläche erstellen oder müssen Geräte auflisten, ohne dem Benutzer eine Benutzeroberfläche anzuzeigen.  In diesen Situationen können Sie mithilfe von [**DeviceInformation.FindAllAsync**](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation.findallasync) eine Momentaufnahme von Geräten auflisten, die derzeit mit dem System verbunden oder gekoppelt sind.  Diese Methode hält alle Ergebnisse zurück, bis die gesamte Auflistung abgeschlossen ist.

> [!TIP]
> Es wird empfohlen, die GetDeviceSelector-Methode bei Verwendung von FindAllAsync mit dem Parameter PosConnectionTypes zu benutzen, um die Abfrage auf den gewünschten Verbindungstyp einzuschränken.  Netzwerk- und Bluetooth-Verbindungen können die Ergebnisse verzögern, da ihre Auflistungen abgeschlossen werden müssen, bevor FindAllAsync-Ergebnisse zurückgegeben werden.

>[!CAUTION] 
>FindAllAsync gibt ein Array von Geräten zurück.  Da sich die Reihenfolge dieses Arrays von Sitzung zu Sitzung ändern kann, wird nicht empfohlen, sich durch Verwendung eines hartcodierten Index für das Array auf eine bestimmte Reihenfolge zu verlassen.  Verwenden Sie DeviceInformation-Eigenschaften, um die Ergebnisse zu filtern oder dem Benutzer eine Benutzeroberfläche zur Auswahl bereitzustellen.

In diesem Beispiel wird die oben definierte Auswahl verwendet, um eine Momentaufnahme von Geräten mithilfe von FindAllAsync zu erstellen. Anschließend werden alle von der Sammlung zurückgegebenen Elemente aufgelistet, und der Gerätename und die ID werden in die Debugausgabe geschrieben. 

```Csharp
using Windows.Devices.Enumeration;

DeviceInformationCollection deviceCollection = await DeviceInformation.FindAllAsync(selector);

foreach (DeviceInformation devInfo in deviceCollection)
{
    Debug.WriteLine("{0} {1}", devInfo.Name, devInfo.Id);
}
```

> [!TIP] 
> Wenn Sie mit den [**Windows.Devices.Enumeration**](https://docs.microsoft.com/uwp/api/Windows.Devices.Enumeration)-APIs arbeiten, müssen Sie häufig [**DeviceInformation**](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation)-Objekte verwenden, um Informationen zu einem bestimmten Gerät zu erhalten. Beispielsweise kann die Eigenschaft [**DeviceInformation.ID**](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation.id) verwendet werden, um dasselbe Gerät wiederherzustellen und erneut zu verwenden, wenn es in einer zukünftigen Sitzung verfügbar ist, und die Eigenschaft [**DeviceInformation.Name**](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation.name) kann für Anzeigezwecke in Ihrer App verwendet werden.  Informationen zu weiteren verfügbaren Eigenschaften finden Sie auf der [**DeviceInformation**](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation) Referenzseite.

---

## <a name="method-3-enumerate-and-watch"></a>Methode 3: Auflisten und Überwachen

Eine leistungsfähigere und flexiblere Methode für die Auflistung von Geräten ist die Erstellung eines [**DeviceWatcher**](https://docs.microsoft.com/uwp/api/Windows.Devices.Enumeration.DeviceWatcher)-Elements.  Ein Geräteüberwachungselement listet Geräte dynamisch auf, sodass die Anwendung Benachrichtigungen erhält, wenn Geräte hinzugefügt, entfernt oder geändert werden, nachdem die ursprüngliche Aufzählung abgeschlossen ist.  Mit einem DeviceWatcher-Element können Sie erkennen, wann ein mit dem Netzwerk verbundenes Gerät online geschaltet wird, ein Bluetooth-Gerät in Reichweite ist und ob ein lokal angeschlossenes Gerät entfernt wird, sodass Sie die entsprechende Aktion innerhalb der Anwendung ausführen können.

In diesem Beispiel wird die oben definierte Auswahl verwendet, um ein DeviceWatcher-Element zu erstellen. Außerdem werden Ereignishandler für die Benachrichtigungen zu hinzugefügten, entfernten oder aktualisierten Geräten definiert. Sie müssen die Details zu den Aktionen ausfüllen, die bei jeder Benachrichtigung durchgeführt werden sollen.

```Csharp

using Windows.Devices.Enumeration;

DeviceWatcher deviceWatcher = DeviceInformation.CreateWatcher(selector);
deviceWatcher.Added += DeviceWatcher_Added;
deviceWatcher.Removed += DeviceWatcher_Removed;
deviceWatcher.Updated += DeviceWatcher_Updated;

void DeviceWatcher_Added(DeviceWatcher sender, DeviceInformation args)
{
    // TODO: Add the DeviceInformation object to your collection
}

void DeviceWatcher_Removed(DeviceWatcher sender, DeviceInformationUpdate args)
{
    // TODO: Remove the item in your collection associated with DeviceInformationUpdate
}

void DeviceWatcher_Updated(DeviceWatcher sender, DeviceInformationUpdate args)
{
    // TODO: Update your collection with information from DeviceInformationUpdate
}
```

> [!TIP]
> Weitere Details zur Verwendung eines DeviceWatcher-Elements finden Sie unter [**Auflisten und Überwachen von Geräten**]( https://docs.microsoft.com/windows/uwp/devices-sensors/enumerate-devices#enumerate-and-watch-devices).
