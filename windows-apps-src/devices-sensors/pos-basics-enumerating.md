---
author: TerryWarwick
title: Auflisten von PointOfService-Geräten
description: Hier erfahren Sie, wie Sie PointOfService Geräte auflisten.
ms.author: jken
ms.date: 10/08/2018
ms.topic: article
keywords: Windows 10, UWP, Point of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: 10804b006cb7ab542c74e363af5134634b7651e3
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5867857"
---
# <a name="enumerating-point-of-service-devices"></a>Auflisten von Point of Service-Geräten
In diesem Abschnitt erfahren Sie, wie Sie [eine Geräteauswahl definieren](https://docs.microsoft.com/windows/uwp/devices-sensors/build-a-device-selector), die verwendet wird, um die im System verfügbaren Geräte abzufragen, und verwenden diese Auswahl, um Point of Service-Geräte mithilfe einer der folgenden Methoden aufzulisten:

**Methode 1:** [Verwenden einer Geräteauswahl](#method-1:-use-a-device-picker)
<br/>
Zeigen Sie eine Geräteauswahl-UI an und den Benutzer ein verbundenen Gerät auswählen. Diese Methode behandelt die Liste aktualisieren, wenn Geräte angeschlossen und entfernt werden, und es ist einfacher und sicherer als andere Methoden.

**Methode 2:** [Abrufen des ersten verfügbaren Geräts](#Method-1:-get-first-available-device)<br />Verwenden Sie [GetDefaultAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.getdefaultasync) , um das erste verfügbare Gerät in einer bestimmten Point of Service-Geräteklasse zugreifen.

**Methode 3:** [Momentaufnahmen von Geräten](#Method-2:-Snapshot-of-devices)<br />Enumerieren einer Momentaufnahme von POS-Geräte, die auf dem System zu einem bestimmten Zeitpunkt vorhanden sind. Dies ist nützlich, wenn Sie eine eigene Benutzeroberfläche erstellen möchten oder Geräte auflisten müssen, ohne dem Benutzer eine Benutzeroberfläche anzuzeigen. [FindAllAsync](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation.findallasync) hält Ergebnisse zurück, bis die gesamte Auflistung abgeschlossen ist.

**Methode 4:** [Auflisten und überwachen](#Method-3:-Enumerate-and-watch)<br />[DeviceWatcher](https://docs.microsoft.com/uwp/api/Windows.Devices.Enumeration.DeviceWatcher) ist eine leistungsfähigere und flexiblere Enumeration-Modell, das ermöglicht Ihnen das Aufzählen von Geräten, die derzeit vorhanden sind, und außerdem Benachrichtigungen empfangen, wenn Geräte hinzugefügt oder aus dem System entfernt werden.  Dies ist hilfreich, wenn Sie eine aktuelle Liste von Geräten im Hintergrund zur Anzeige auf Ihrer Benutzeroberfläche verwalten möchten, statt darauf zu warten, bis eine Momentaufnahme erstellt wird.

## <a name="define-a-device-selector"></a>Definieren einer Geräteauswahl
Mit einer Geräteauswahl können Sie die Geräte begrenzen, die Sie beim Auflisten von Geräten durchsuchen.  Dadurch können Sie nur relevante Ergebnisse abrufen und die Zeit verkürzen benötigt wird, um die gewünschten Geräte aufzulisten.

Sie können die **GetDeviceSelector** -Methode für den Typ des Geräts verwenden, die Sie für erfahren möchten, können Sie die Geräteauswahl für dieses Typs abrufen. Mit [PosPrinter.GetDeviceSelector](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.posprinter.getdeviceselector#Windows_Devices_PointOfService_PosPrinter_GetDeviceSelector) wird z. B. bereitstellen, dass Sie eine Auswahl zum Auflisten aller [PosPrinters](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.posprinter) an das System, einschließlich USB-, Netzwerk- und Bluetooth-POS-Drucker angefügt.

```Csharp
using Windows.Devices.PointOfService;

string selector = POSPrinter.GetDeviceSelector();
```

Die **GetDeviceSelector** -Methoden für die verschiedenen Gerätetypen sind:

* [BarcodeScanner.GetDeviceSelector](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.getdeviceselector)
* [CashDrawer.GetDeviceSelector](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.cashdrawer.getdeviceselector)
* [LineDisplay.GetDeviceSelector](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.linedisplay.getdeviceselector)
* [MagneticStripeReader.GetDeviceSelector](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereader.getdeviceselector)
* [PosPrinter.GetDeviceSelector](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.posprinter.getdeviceselector)

Verwenden eine **GetDeviceSelector** -Methode, die einen [PosConnectionTypes](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.posconnectiontypes) Wert als Parameter akzeptiert, können Sie einschränken, Ihre Auswahl zum Auflisten von lokalen, Netzwerk- oder Bluetooth-attached POS-Geräte, reduziert den Zeitaufwand für die Abfrage abgeschlossen.  Das folgende Beispiel zeigt, dass eine Verwendung dieser Methode einen Selektor definieren, der nur lokal unterstützt POS-Drucker verbunden.

 ```Csharp
using Windows.Devices.PointOfService;

string selector = POSPrinter.GetDeviceSelector(PosConnectionTypes.Local);
```

> [!TIP]
> Weitere Informationen zum Erstellen umfangreicherer Auswahlzeichenfolgen finden Sie unter [Erstellen einer Geräteauswahl](https://docs.microsoft.com/windows/uwp/devices-sensors/build-a-device-selector).

## <a name="method-1-use-a-device-picker"></a>Methode 1: Verwenden einer Geräteauswahl

Die [DevicePicker](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.devicepicker) -Klasse können Sie eine Auswahl-Flyout angezeigt wird, eine Liste der Geräte für den Benutzer zur Auswahl enthält. Die Eigenschaft [Filter](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.devicepicker.filter) können Sie auswählen, welche Arten von Geräten in der Auswahl angezeigt. Diese Eigenschaft ist vom Typ [DevicePickerFilter](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.devicepickerfilter). Sie können den Filter unter Verwendung der [SupportedDeviceClasses](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.devicepickerfilter.supporteddeviceclasses) oder [SupportedDeviceSelectors](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.devicepickerfilter.supporteddeviceselectors) Gerätetypen hinzufügen.

Wenn Sie bereit sind, die Geräteauswahl anzuzeigen sind, können Sie die Methode [PickSingleDeviceAsync](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.devicepicker.picksingledeviceasync) Aufrufen der die Auswahl-UI anzeigen, und das ausgewählte Gerät zurückzugeben. Sie müssen eine [Rect](https://docs.microsoft.com/uwp/api/windows.foundation.rect) angeben, die bestimmt, wo das Flyout angezeigt wird. Diese Methode gibt ein [DeviceInformation](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation) -Objekt, damit es mit der POS-APIs verwenden, müssen Sie die **FromIdAsync** -Methode für die bestimmte Geräteklasse verwenden, die Sie möchten. Sie übergeben Sie die [DeviceInformation.Id](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation.id) Eigenschaft als den Methodenparameter *DeviceId* , und rufen Sie eine Instanz der Geräteklasse als Rückgabewert.

Der folgende Codeausschnitt erstellt ein **DevicePicker**, fügt ein Barcode-Scanner Filter, hat den Benutzer ein Gerät auswählen und erstellt dann ein **BarcodeScanner** -Objekt basierend auf der Geräte-ID:

```cs
private async Task<BarcodeScanner> GetBarcodeScanner()
{
    DevicePicker devicePicker = new DevicePicker();
    devicePicker.Filter.SupportedDeviceSelectors.Add(BarcodeScanner.GetDeviceSelector());
    Rect rect = new Rect();
    DeviceInformation deviceInformation = await devicePicker.PickSingleDeviceAsync(rect);
    BarcodeScanner barcodeScanner = await BarcodeScanner.FromIdAsync(deviceInformation.Id);
    return barcodeScanner;
}
```

## <a name="method-2-get-first-available-device"></a>Methode 2: Abrufen des ersten verfügbaren Geräts

Die einfachste Möglichkeit zum Abrufen eines POS-Geräts ist mit **GetDefaultAsync** das erste verfügbare Gerät innerhalb einer Geräteklasse Point of Service abrufen. 

Das folgende Beispiel veranschaulicht die Verwendung von [GetDefaultAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.getdefaultasync#Windows_Devices_PointOfService_BarcodeScanner_GetDefaultAsync) für [BarcodeScanner](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner). Das Codierungsmuster ist für alle Point of Service-Geräteklassen ähnlich.

```Csharp
using Windows.Devices.PointOfService;

BarcodeScanner barcodeScanner = await BarcodeScanner.GetDefaultAsync();
```

> [!CAUTION]
> **GetDefaultAsync** muss mit Vorsicht verwendet werden, da ein anderes Gerät von einer Sitzung zur nächsten möglicherweise zurückgegeben wird. Viele Ereignisse können diese Auflistung beeinflussen und zu einem anderen ersten verfügbaren Gerät führen, darunter: 
> - Änderung bei den an Ihren Computer angeschlossenen Kameras 
> - Point Service-Geräte an Ihren Computer angeschlossenen ändern
> - Änderung bei den Network attached POS-Geräte in Ihrem Netzwerk verfügbar
> - Änderung bei den Bluetooth-Point of Service-Geräte in Reichweite Ihres Computers 
> - Änderungen an der Point of Service-Konfiguration 
> - Installation von Treibern oder OPOS-Serviceobjekten
> - Installation von Point of Service-Erweiterungen
> - Updates am Windows-Betriebssystem

## <a name="method-3-snapshot-of-devices"></a>Methode 3: Momentaufnahmen von Geräten

In einigen Szenarien möchten Sie vielleicht eine eigene Benutzeroberfläche erstellen oder müssen Geräte auflisten, ohne dem Benutzer eine Benutzeroberfläche anzuzeigen.  In diesen Situationen können Sie mithilfe von [DeviceInformation.FindAllAsync](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation.findallasync) eine Momentaufnahme von Geräten auflisten, die derzeit mit dem System verbunden oder gekoppelt sind.  Diese Methode hält alle Ergebnisse zurück, bis die gesamte Auflistung abgeschlossen ist.

> [!TIP]
> Es wird empfohlen, die **GetDeviceSelector** -Methode mit dem Parameter **PosConnectionTypes** zu verwenden, wenn Sie **FindAllAsync** verwenden, um die Abfrage auf den gewünschten Verbindungstyp einzuschränken.  Netzwerk- und Bluetooth-Verbindungen können die Ergebnisse verzögern, da ihre Auflistungen abgeschlossen werden müssen, bevor **FindAllAsync** -Ergebnisse zurückgegeben werden.

> [!CAUTION] 
> **FindAllAsync** gibt ein Array von Geräten.  Da sich die Reihenfolge dieses Arrays von Sitzung zu Sitzung ändern kann, wird nicht empfohlen, sich durch Verwendung eines hartcodierten Index für das Array auf eine bestimmte Reihenfolge zu verlassen.  Verwenden Sie [DeviceInformation](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation) -Eigenschaften, um die Ergebnisse zu filtern oder eine Benutzeroberfläche für den Benutzer zur Auswahl bereitzustellen.

In diesem Beispiel wird die Auswahl einer Momentaufnahme von Geräten mit **FindAllAsync** den oben definierten verwendet und dann jedes Element der Sammlung zurückgegebenen durchläuft und schreibt Device Name und ID in die Debugausgabe geschrieben. 

```Csharp
using Windows.Devices.Enumeration;

DeviceInformationCollection deviceCollection = await DeviceInformation.FindAllAsync(selector);

foreach (DeviceInformation devInfo in deviceCollection)
{
    Debug.WriteLine("{0} {1}", devInfo.Name, devInfo.Id);
}
```

> [!TIP] 
> Wenn Sie mit den [Windows.Devices.Enumeration](https://docs.microsoft.com/uwp/api/Windows.Devices.Enumeration)-APIs arbeiten, müssen Sie häufig [DeviceInformation](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation)-Objekte verwenden, um Informationen zu einem bestimmten Gerät zu erhalten. Die Eigenschaft [DeviceInformation.ID](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation.id) kann z. B. verwendet werden, zum Wiederherstellen und wiederverwenden dasselbe Gerät in einer zukünftigen Sitzung verfügbar ist und die [DeviceInformation.Name](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation.name) -Eigenschaft kann für Anzeigezwecke in Ihrer app verwendet werden.  Informationen zu weiteren verfügbaren Eigenschaften finden Sie auf der [DeviceInformation](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation) Referenzseite.

## <a name="method-4-enumerate-and-watch"></a>Methode 4: Auflisten und überwachen

Eine leistungsfähigere und flexiblere Methode für die Auflistung von Geräten ist die Erstellung eines [DeviceWatcher](https://docs.microsoft.com/uwp/api/Windows.Devices.Enumeration.DeviceWatcher)-Elements.  Ein Geräteüberwachungselement listet Geräte dynamisch auf, sodass die Anwendung Benachrichtigungen erhält, wenn Geräte hinzugefügt, entfernt oder geändert werden, nachdem die ursprüngliche Aufzählung abgeschlossen ist.  Ein **DeviceWatcher** können Sie erkennen, wann ein Netzwerk verbundenen Gerät online geschaltet wird, ein Bluetooth-Gerät in Reichweite, auch als ob ein lokal angeschlossenes Gerät entfernt wird, damit Sie die entsprechende Aktion innerhalb der Anwendung nutzen können.

In diesem Beispiel wird die zum Erstellen einer **DeviceWatcher** oben definierte Auswahl verwendet sowie Ereignishandler für die [hinzugefügten](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.devicewatcher.added), [entfernten](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.devicewatcher.removed)oder [aktualisierten](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.devicewatcher.updated) Benachrichtigungen definiert. Sie müssen die Details zu den Aktionen ausfüllen, die bei jeder Benachrichtigung durchgeführt werden sollen.

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
> Weitere Informationen zur Verwendung von einem **DeviceWatcher**finden Sie unter [enumerieren und Überwachen von Geräten]( https://docs.microsoft.com/windows/uwp/devices-sensors/enumerate-devices#enumerate-and-watch-devices) .

## <a name="see-also"></a>Weitere Informationen:
* [Erste Schritte mit Point Of Service-Geräten](pos-basics.md)
* [DeviceInformation-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation)
* [PosPrinter-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.posprinter)
* [PosConnectionTypes-Enumeration](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.posconnectiontypes)
* [BarcodeScanner-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner)
* [DeviceWatcher-Klasse](https://docs.microsoft.com/uwp/api/Windows.Devices.Enumeration.DeviceWatcher)

[!INCLUDE [feedback](./includes/pos-feedback.md)]