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
# <a name="enumerating-point-of-service-devices"></a><span data-ttu-id="f5e28-104">Auflisten von Point of Service-Geräten</span><span class="sxs-lookup"><span data-stu-id="f5e28-104">Enumerating Point of Service devices</span></span>
<span data-ttu-id="f5e28-105">In diesem Abschnitt erfahren Sie, wie Sie [**eine Geräteauswahl definieren**](https://docs.microsoft.com/windows/uwp/devices-sensors/build-a-device-selector), die verwendet wird, um die im System verfügbaren Geräte abzufragen, und verwenden diese Auswahl, um Point of Service-Geräte mithilfe einer der folgenden Methoden aufzulisten:</span><span class="sxs-lookup"><span data-stu-id="f5e28-105">In this section you will learn how to [**define a device selector**](https://docs.microsoft.com/windows/uwp/devices-sensors/build-a-device-selector) that is used to query devices available to the system and use this selector to enumerate Point of Service devices using one of the following methods:</span></span>

<span data-ttu-id="f5e28-106">**Methode 1:** [**Abrufen des ersten verfügbaren Geräts**](#Method-1:-get-first-available-device)</span><span class="sxs-lookup"><span data-stu-id="f5e28-106">**Method 1:** [**Get first available device**](#Method-1:-get-first-available-device)</span></span><br /><span data-ttu-id="f5e28-107">In diesem Abschnitt erfahren Sie, wie Sie mithilfe von **GetDefaultAsync** auf das erste verfügbare Gerät in einer bestimmten PointOfService Geräteklasse zugreifen.</span><span class="sxs-lookup"><span data-stu-id="f5e28-107">In this section you will learn how to use **GetDefaultAsync** to access the first available device in a specific PointOfService device class.</span></span>

<span data-ttu-id="f5e28-108">**Methode 2:** [**Momentaufnahmen von Geräten**](#Method-2:-Snapshot-of-devices)</span><span class="sxs-lookup"><span data-stu-id="f5e28-108">**Method 2:** [**Snapshot of devices**](#Method-2:-Snapshot-of-devices)</span></span><br /><span data-ttu-id="f5e28-109">In diesem Abschnitterfahren Sie, wie Sie eine Momentaufnahme der PointOfService-Geräte auflisten, die zu einem bestimmten Zeitpunkt auf dem System vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="f5e28-109">In this section you will learn how to enumerate a snapshot of PointOfService devices that are present on the system at a given point in time.</span></span> <span data-ttu-id="f5e28-110">Dies ist nützlich, wenn Sie eine eigene Benutzeroberfläche erstellen möchten oder Geräte auflisten müssen, ohne dem Benutzer eine Benutzeroberfläche anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="f5e28-110">This is useful when you want to build your own UI or need to enumerate devices without displaying a UI to the user.</span></span> <span data-ttu-id="f5e28-111">FindAllAsync hält Ergebnisse zurück, bis die gesamte Auflistung abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="f5e28-111">FindAllAsync will hold back results until the entire enumeration is completed.</span></span>

<span data-ttu-id="f5e28-112">**Methode 3:** [**Auflisten und Überwachen**](#Method-3:-Enumerate-and-watch)</span><span class="sxs-lookup"><span data-stu-id="f5e28-112">**Method 3:** [**Enumerate and watch**](#Method-3:-Enumerate-and-watch)</span></span><br /><span data-ttu-id="f5e28-113">In diesem Abschnitterfahren Sie mehr über ein leistungsfähigeres und flexibleres Auflistungsmodell, mit dem Sie Geräte auflisten können, die derzeit vorhanden sind, und außerdem Benachrichtigungen empfangen, wenn Geräte hinzugefügt oder aus dem System entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="f5e28-113">In this section you will learn about a more powerful and flexible enumeration model that allows you to enumerate devices that are currently present, and also receive notifications when devices are added or removed from the system.</span></span>  <span data-ttu-id="f5e28-114">Dies ist hilfreich, wenn Sie eine aktuelle Liste von Geräten im Hintergrund zur Anzeige auf Ihrer Benutzeroberfläche verwalten möchten, statt darauf zu warten, bis eine Momentaufnahme erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="f5e28-114">This is useful when you want to maintain a current list of devices in the background for displaying in your UI rather than waiting for a snapshot to occur.</span></span>
 

---
## <a name="define-a-device-selector"></a><span data-ttu-id="f5e28-115">Definieren einer Geräteauswahl</span><span class="sxs-lookup"><span data-stu-id="f5e28-115">Define a device selector</span></span>
<span data-ttu-id="f5e28-116">Mit einer Geräteauswahl können Sie die Geräte begrenzen, die Sie beim Auflisten von Geräten durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="f5e28-116">A device selector will enable you to limit the devices you are searching through when enumerating devices.</span></span>  <span data-ttu-id="f5e28-117">Dadurch können Sie nur relevante Ergebnisse abrufen und die Zeit verkürzen, die benötigt wird, um die gewünschten Geräte aufzulisten.</span><span class="sxs-lookup"><span data-stu-id="f5e28-117">This will enable you to only get relevant results and reduce the time it takes to enumerate the desired devices.</span></span>  

<span data-ttu-id="f5e28-118">Mithilfe von [**GetDeviceSelector**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.posprinter.getdeviceselector#Windows_Devices_PointOfService_PosPrinter_GetDeviceSelector) erhalten Sie eine Auswahl zum Auflisten aller mit dem System verbundener POSPrinters, einschließlich USB-, Netzwerk- und Bluetooth-POSPrinters.</span><span class="sxs-lookup"><span data-stu-id="f5e28-118">Using [**GetDeviceSelector**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.posprinter.getdeviceselector#Windows_Devices_PointOfService_PosPrinter_GetDeviceSelector) will provide you with a selector to enumerate all POSPrinters attached to the system, including USB, network and Bluetooth POSPrinters.</span></span>

```Csharp
using Windows.Devices.PointOfService;

string selector = POSPrinter.GetDeviceSelector();   

```

<span data-ttu-id="f5e28-119">Mithilfe der Methode [**GetDeviceSelector**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.posprinter.getdeviceselector#Windows_Devices_PointOfService_PosPrinter_GetDeviceSelector_Windows_Devices_PointOfService_PosConnectionTypes_), die [**PosConnectionTypes**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.posconnectiontypes) als Parameter akzeptiert, können Sie Ihre Auswahl zum Auflisten von lokalen, Netzwerk- oder per Bluetooth verbundener POSPrinters einschränken und so die für das Abschließen der Abfrage erforderliche Zeit verkürzen.</span><span class="sxs-lookup"><span data-stu-id="f5e28-119">Using the [**GetDeviceSelector**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.posprinter.getdeviceselector#Windows_Devices_PointOfService_PosPrinter_GetDeviceSelector_Windows_Devices_PointOfService_PosConnectionTypes_) method that takes [**PosConnectionTypes**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.posconnectiontypes) as a parameter, you can restrict your selector to enumerate local, network or Bluetooth attached POSPrinters reducing the time it takes for the query to complete.</span></span>  <span data-ttu-id="f5e28-120">Das folgende Beispiel zeigt die Verwendung dieser Methode zum Definieren einer Auswahl, die nur lokal verbundene POSPrinters unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f5e28-120">The sample below shows the use of this method to define a selctor that support only locally attached POSPrinters.</span></span>

 ```Csharp
using Windows.Devices.PointOfService;

string selector = POSPrinter.GetDeviceSelector(PosConnectionTypes.Local);   

```
> [!TIP]
> <span data-ttu-id="f5e28-121">Weitere Informationen zum Erstellen umfangreicherer Auswahlzeichenfolgen finden Sie unter [**Erstellen einer Geräteauswahl**](https://docs.microsoft.com/windows/uwp/devices-sensors/build-a-device-selector).</span><span class="sxs-lookup"><span data-stu-id="f5e28-121">See [**Build a device selector**](https://docs.microsoft.com/windows/uwp/devices-sensors/build-a-device-selector) for building more advanced selector strings.</span></span>

---

## <a name="method-1-get-first-available-device"></a><span data-ttu-id="f5e28-122">Methode 1: Abrufen des ersten verfügbaren Geräts</span><span class="sxs-lookup"><span data-stu-id="f5e28-122">Method 1: Get first available device</span></span>

<span data-ttu-id="f5e28-123">Die einfachste Möglichkeit zum Abrufen eines PointOfService-Geräts ist die Verwendung von **GetDefaultAsync** zum Abrufen des ersten verfügbaren Geräts in einer PointOfService-Geräteklasse.</span><span class="sxs-lookup"><span data-stu-id="f5e28-123">The simplest way to get a PointOfService device is to use **GetDefaultAsync** to get the first available device within a PointOfService device class.</span></span> 

<span data-ttu-id="f5e28-124">Das folgende Beispiel veranschaulicht die Verwendung von [**GetDefaultAsync**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.getdefaultasync#Windows_Devices_PointOfService_BarcodeScanner_GetDefaultAsync) für BarcodeScanner.</span><span class="sxs-lookup"><span data-stu-id="f5e28-124">The sample below illustrates the use of [**GetDefaultAsync**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.getdefaultasync#Windows_Devices_PointOfService_BarcodeScanner_GetDefaultAsync) for BarcodeScanner.</span></span> <span data-ttu-id="f5e28-125">Das Codierungsmuster ist für alle PointOfService-Geräteklassen ähnlich.</span><span class="sxs-lookup"><span data-stu-id="f5e28-125">The coding pattern is similar for all PointOfService device classes.</span></span>

```Csharp

using Windows.Devices.PointOfService;

BarcodeScanner barcodeScanner = await BarcodeScanner.GetDefaultAsync();

```

> [!CAUTION]
> <span data-ttu-id="f5e28-126">GetDefaultAsync muss mit Vorsicht verwendet werden, da möglicherweise von einer Sitzung zur nächsten ein anderes Gerät zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="f5e28-126">GetDefaultAsync must be used with care as it may return a different device from one session to the next.</span></span> <span data-ttu-id="f5e28-127">Viele Ereignisse können diese Auflistung beeinflussen und zu einem anderen ersten verfügbaren Gerät führen, darunter:</span><span class="sxs-lookup"><span data-stu-id="f5e28-127">Many events can influence this enumeration resulting in a different first available device, including:</span></span> 
> - <span data-ttu-id="f5e28-128">Änderung bei den an Ihren Computer angeschlossenen Kameras</span><span class="sxs-lookup"><span data-stu-id="f5e28-128">Change in cameras attached to your computer</span></span> 
> - <span data-ttu-id="f5e28-129">Änderung bei den an Ihren Computer angeschlossenen PointOfService-Geräten</span><span class="sxs-lookup"><span data-stu-id="f5e28-129">Change in PointOfService devices attached to your computer</span></span>
> - <span data-ttu-id="f5e28-130">Änderung bei den über das Netzwerk angeschlossen PointOfService-Geräten, die in Ihrem Netzwerk verfügbar sind</span><span class="sxs-lookup"><span data-stu-id="f5e28-130">Change in network attached PointOfService devices available on your network</span></span>
> - <span data-ttu-id="f5e28-131">Änderung bei den Bluetooth-PointOfService-Geräten in Reichweite Ihres Computers</span><span class="sxs-lookup"><span data-stu-id="f5e28-131">Change in Bluetooth PointOfService devices within range of your computer</span></span> 
> - <span data-ttu-id="f5e28-132">Änderungen an der PointOfService-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="f5e28-132">Changes to the PointOfService configuration</span></span> 
> - <span data-ttu-id="f5e28-133">Installation von Treibern oder OPOS-Serviceobjekten</span><span class="sxs-lookup"><span data-stu-id="f5e28-133">Installation of drivers or OPOS service objects</span></span>
> - <span data-ttu-id="f5e28-134">Installation von PointOfService-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="f5e28-134">Installation of PointOfService extensions</span></span>
> - <span data-ttu-id="f5e28-135">Updates am Windows-Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="f5e28-135">Update to Windows operating system</span></span>

---

## <a name="method-2-snapshot-of-devices"></a><span data-ttu-id="f5e28-136">Methode 2: Momentaufnahmen von Geräten</span><span class="sxs-lookup"><span data-stu-id="f5e28-136">Method 2: Snapshot of devices</span></span>

<span data-ttu-id="f5e28-137">In einigen Szenarien möchten Sie vielleicht eine eigene Benutzeroberfläche erstellen oder müssen Geräte auflisten, ohne dem Benutzer eine Benutzeroberfläche anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="f5e28-137">In some scenarios you may want to build your own UI or need to enumerate devices without displaying a UI to the user.</span></span>  <span data-ttu-id="f5e28-138">In diesen Situationen können Sie mithilfe von [**DeviceInformation.FindAllAsync**](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation.findallasync) eine Momentaufnahme von Geräten auflisten, die derzeit mit dem System verbunden oder gekoppelt sind.</span><span class="sxs-lookup"><span data-stu-id="f5e28-138">In these situations, you could enumerate a snapshot of devices that are currently connected or paired with the system using [**DeviceInformation.FindAllAsync**](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation.findallasync).</span></span>  <span data-ttu-id="f5e28-139">Diese Methode hält alle Ergebnisse zurück, bis die gesamte Auflistung abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="f5e28-139">This method will hold back any results until the entire enumeration is completed.</span></span>

> [!TIP]
> <span data-ttu-id="f5e28-140">Es wird empfohlen, die GetDeviceSelector-Methode bei Verwendung von FindAllAsync mit dem Parameter PosConnectionTypes zu benutzen, um die Abfrage auf den gewünschten Verbindungstyp einzuschränken.</span><span class="sxs-lookup"><span data-stu-id="f5e28-140">It is recommended to use GetDeviceSelector method with the PosConnectionTypes parameter when using FindAllAsync to limit your query to the connection type desired.</span></span>  <span data-ttu-id="f5e28-141">Netzwerk- und Bluetooth-Verbindungen können die Ergebnisse verzögern, da ihre Auflistungen abgeschlossen werden müssen, bevor FindAllAsync-Ergebnisse zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="f5e28-141">Network and Bluetooth connections can delay the results as their enumerations must complete before FindAllAsync results are returned.</span></span>

>[!CAUTION] 
><span data-ttu-id="f5e28-142">FindAllAsync gibt ein Array von Geräten zurück.</span><span class="sxs-lookup"><span data-stu-id="f5e28-142">FindAllAsync returns an array of devices.</span></span>  <span data-ttu-id="f5e28-143">Da sich die Reihenfolge dieses Arrays von Sitzung zu Sitzung ändern kann, wird nicht empfohlen, sich durch Verwendung eines hartcodierten Index für das Array auf eine bestimmte Reihenfolge zu verlassen.</span><span class="sxs-lookup"><span data-stu-id="f5e28-143">The order of this array can change from session to session, therefore it is not recommended to rely on a specific order by using a hardcoded index into the array.</span></span>  <span data-ttu-id="f5e28-144">Verwenden Sie DeviceInformation-Eigenschaften, um die Ergebnisse zu filtern oder dem Benutzer eine Benutzeroberfläche zur Auswahl bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="f5e28-144">Use DeviceInformation properties to filter your results or provide an UI for the user to choose from.</span></span>

<span data-ttu-id="f5e28-145">In diesem Beispiel wird die oben definierte Auswahl verwendet, um eine Momentaufnahme von Geräten mithilfe von FindAllAsync zu erstellen. Anschließend werden alle von der Sammlung zurückgegebenen Elemente aufgelistet, und der Gerätename und die ID werden in die Debugausgabe geschrieben.</span><span class="sxs-lookup"><span data-stu-id="f5e28-145">This sample uses the selector defined above to take a snapshot of devices using FindAllAsync then enumerates through each of the items returned by the collection and writes the device name and ID to the debug output.</span></span> 

```Csharp
using Windows.Devices.Enumeration;

DeviceInformationCollection deviceCollection = await DeviceInformation.FindAllAsync(selector);

foreach (DeviceInformation devInfo in deviceCollection)
{
    Debug.WriteLine("{0} {1}", devInfo.Name, devInfo.Id);
}
```

> [!TIP] 
> <span data-ttu-id="f5e28-146">Wenn Sie mit den [**Windows.Devices.Enumeration**](https://docs.microsoft.com/uwp/api/Windows.Devices.Enumeration)-APIs arbeiten, müssen Sie häufig [**DeviceInformation**](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation)-Objekte verwenden, um Informationen zu einem bestimmten Gerät zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="f5e28-146">When working with the [**Windows.Devices.Enumeration**](https://docs.microsoft.com/uwp/api/Windows.Devices.Enumeration) APIs, you will frequently need to use [**DeviceInformation**](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation) objects to obtain information about a specific device.</span></span> <span data-ttu-id="f5e28-147">Beispielsweise kann die Eigenschaft [**DeviceInformation.ID**](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation.id) verwendet werden, um dasselbe Gerät wiederherzustellen und erneut zu verwenden, wenn es in einer zukünftigen Sitzung verfügbar ist, und die Eigenschaft [**DeviceInformation.Name**](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation.name) kann für Anzeigezwecke in Ihrer App verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f5e28-147">For example, [**DeviceInformation.ID**](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation.id) property can be used to recover and reuse the same device if it is available in a future session and [**DeviceInformation.Name**](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation.name) property can be used for display purposes in your app.</span></span>  <span data-ttu-id="f5e28-148">Informationen zu weiteren verfügbaren Eigenschaften finden Sie auf der [**DeviceInformation**](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation) Referenzseite.</span><span class="sxs-lookup"><span data-stu-id="f5e28-148">See the [**DeviceInformation**](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation) reference page for information about additional properties available.</span></span>

---

## <a name="method-3-enumerate-and-watch"></a><span data-ttu-id="f5e28-149">Methode 3: Auflisten und Überwachen</span><span class="sxs-lookup"><span data-stu-id="f5e28-149">Method 3: Enumerate and watch</span></span>

<span data-ttu-id="f5e28-150">Eine leistungsfähigere und flexiblere Methode für die Auflistung von Geräten ist die Erstellung eines [**DeviceWatcher**](https://docs.microsoft.com/uwp/api/Windows.Devices.Enumeration.DeviceWatcher)-Elements.</span><span class="sxs-lookup"><span data-stu-id="f5e28-150">A more powerful and flexible method of enumerating devices is creating a [**DeviceWatcher**](https://docs.microsoft.com/uwp/api/Windows.Devices.Enumeration.DeviceWatcher).</span></span>  <span data-ttu-id="f5e28-151">Ein Geräteüberwachungselement listet Geräte dynamisch auf, sodass die Anwendung Benachrichtigungen erhält, wenn Geräte hinzugefügt, entfernt oder geändert werden, nachdem die ursprüngliche Aufzählung abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="f5e28-151">A device watcher enumerates devices dynamically, so that the application receives notifications if devices are added, removed, or changed  after the initial enumeration is complete.</span></span>  <span data-ttu-id="f5e28-152">Mit einem DeviceWatcher-Element können Sie erkennen, wann ein mit dem Netzwerk verbundenes Gerät online geschaltet wird, ein Bluetooth-Gerät in Reichweite ist und ob ein lokal angeschlossenes Gerät entfernt wird, sodass Sie die entsprechende Aktion innerhalb der Anwendung ausführen können.</span><span class="sxs-lookup"><span data-stu-id="f5e28-152">A DeviceWatcher will allow you to detect when a network connected device comes online, a Bluetooth device is in range, as well as if a locally connected device is unplugged so that you can take the appropriate action within your application.</span></span>

<span data-ttu-id="f5e28-153">In diesem Beispiel wird die oben definierte Auswahl verwendet, um ein DeviceWatcher-Element zu erstellen. Außerdem werden Ereignishandler für die Benachrichtigungen zu hinzugefügten, entfernten oder aktualisierten Geräten definiert.</span><span class="sxs-lookup"><span data-stu-id="f5e28-153">This sample uses the selector defined above to create a DeviceWatcher as well as defines event handlers for the Added, Removed and Updated notifications.</span></span> <span data-ttu-id="f5e28-154">Sie müssen die Details zu den Aktionen ausfüllen, die bei jeder Benachrichtigung durchgeführt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="f5e28-154">You will need to fill in the details of the actions that you wish to take upon each notification.</span></span>

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
> <span data-ttu-id="f5e28-155">Weitere Details zur Verwendung eines DeviceWatcher-Elements finden Sie unter [**Auflisten und Überwachen von Geräten**]( https://docs.microsoft.com/windows/uwp/devices-sensors/enumerate-devices#enumerate-and-watch-devices).</span><span class="sxs-lookup"><span data-stu-id="f5e28-155">See [**Enumerate and watch devices**]( https://docs.microsoft.com/windows/uwp/devices-sensors/enumerate-devices#enumerate-and-watch-devices) for more details on the use of a DeviceWatcher</span></span>
