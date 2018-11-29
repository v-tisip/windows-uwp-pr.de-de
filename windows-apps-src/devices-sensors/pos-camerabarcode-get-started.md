---
title: Erste Schrittemit dem Kamera-Strichcodescanner
description: Umgang mit dem Kamera-Strichcodescanner
ms.date: 05/1/2018
ms.topic: article
keywords: Windows 10, UWP, Point Of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: b49ba463e39d09b915ce3925f94ae7d9f11a9a47
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "8195541"
---
# <a name="getting-started-with-a-camera-barcode-scanner"></a><span data-ttu-id="6dbd9-104">Erste Schrittemit dem Kamera-Strichcodescanner</span><span class="sxs-lookup"><span data-stu-id="6dbd9-104">Getting started with a camera barcode scanner</span></span>
## <a name="step-1-add-capability-declarations-to-your-app-manifest"></a><span data-ttu-id="6dbd9-105">Schritt 1: Hinzufügen von Funktionsdeklarationen zum App-Manifest</span><span class="sxs-lookup"><span data-stu-id="6dbd9-105">Step 1: Add capability declarations to your app manifest</span></span>
1. <span data-ttu-id="6dbd9-106">Öffnen Sie in MicrosoftVisual Studio im **Projektmappen-Explorer** den Designer für das Anwendungsmanifest, indem Sie auf das Element **package.appxmanifest** doppelklicken.</span><span class="sxs-lookup"><span data-stu-id="6dbd9-106">In Microsoft Visual Studio, in **Solution Explorer**, open the designer for the application manifest by double-clicking the **package.appxmanifest** item.</span></span>
2. <span data-ttu-id="6dbd9-107">Wählen Sie die Registerkarte **Funktionen** aus</span><span class="sxs-lookup"><span data-stu-id="6dbd9-107">Select the **Capabilities** tab</span></span>
3. <span data-ttu-id="6dbd9-108">Aktivieren Sie die Kontrollkästchen für **Webcam** und **PointOfService**</span><span class="sxs-lookup"><span data-stu-id="6dbd9-108">Check the boxes for **Webcam** and **PointOfService**</span></span> 

>[!NOTE] 
> <span data-ttu-id="6dbd9-109">Die **Webcam**-Funktion ist erforderlich, um für den Softwaredecoder von der Kamera Frames zum Decodieren zu empfangen, sowie eine Vorschau von Ihrer Anwendung bereitzustellen</span><span class="sxs-lookup"><span data-stu-id="6dbd9-109">The **Webcam** capability is required to for the software decoder to receive frames from the camera to decode as well as to provide a preview from your application</span></span>

## <a name="step-2-add-using-directives"></a><span data-ttu-id="6dbd9-110">Schritt2: Hinzufügen von using-Direktiven</span><span class="sxs-lookup"><span data-stu-id="6dbd9-110">Step 2: Add using directives</span></span>

```Csharp
using Windows.Devices.Enumeration;
using Windows.Devices.PointOfService;
```
## <a name="step-3-define-your-device-selector"></a><span data-ttu-id="6dbd9-111">Schritt3: Definieren der Geräteauswahl</span><span class="sxs-lookup"><span data-stu-id="6dbd9-111">Step 3: Define your device selector</span></span>

### **<a name="option-a-find-all-barcode-scanners"></a><span data-ttu-id="6dbd9-112">Option A: Anzeigen aller Strichcodescanner</span><span class="sxs-lookup"><span data-stu-id="6dbd9-112">Option A: Find all barcode scanners</span></span>**

```Csharp
string selector = BarcodeScanner.GetDeviceSelector();       
```

### **<a name="option-b-scoping-device-selector-to-connection-type"></a><span data-ttu-id="6dbd9-113">Option B: Begrenzen der Geräteauswahl für den Verbindungstyp</span><span class="sxs-lookup"><span data-stu-id="6dbd9-113">Option B: Scoping device selector to connection type</span></span>**

```Csharp
string selector = BarcodeScanner.GetDeviceSelector(PosConnectionTypes.Local);
DeviceInformationCollection deviceCollection = await DeviceInformation.FindAllAsync(selector);
```

## <a name="step-4-enumerate-barcode-scanners"></a><span data-ttu-id="6dbd9-114">Schritt4: Aufzählen der Strichcodescanner</span><span class="sxs-lookup"><span data-stu-id="6dbd9-114">Step 4: Enumerate barcode scanners</span></span>
<span data-ttu-id="6dbd9-115">Wenn Sie nicht erwarten, dass sich die Liste der Geräte über die Lebensdauer der Anwendung ändert, können Sie eine Momentaufnahme einmal mit *FindAllAsync* auflisten. Wenn Sie allerdings glauben, dass sich die Liste der Strichcodescanner während der Lebensdauer der Anwendung ändern wird, verwenden Sie stattdessen einen *DeviceWatcher*.</span><span class="sxs-lookup"><span data-stu-id="6dbd9-115">If you do not expect the list of devices to change over the lifespan of your application you can enumerate a snapshot just once with *FindAllAsync*, but if you believe that the list of barcode scanners could change over the lifespan of your application you should use a *DeviceWatcher* instead.</span></span>  

> [!Important] 
> <span data-ttu-id="6dbd9-116">Das Verwenden von GetDefaultAsync PointOfService-Geräten kann zu inkonsistentem Verhalten führen, da nur das erste Gerät in der Klasse zurückgegeben wird und sich dies von Sitzung zu Sitzung ändern kann.</span><span class="sxs-lookup"><span data-stu-id="6dbd9-116">Using GetDefaultAsync to enumerate PointOfService devices can result in inconsistent behavior as it simply returns the first device found in the class and this can change from session to session.</span></span>

### **<a name="option-a-enumerate-a-snapshot-of-barcode-scanners"></a><span data-ttu-id="6dbd9-117">Option A: Enumerieren einer Momentaufnahme von Strichcodescannern</span><span class="sxs-lookup"><span data-stu-id="6dbd9-117">Option A: Enumerate a snapshot of barcode scanners</span></span>**
```Csharp
DeviceInformationCollection deviceCollection = await DeviceInformation.FindAllAsync(selector);
```

> [!TIP]
> <span data-ttu-id="6dbd9-118">Unter [*Enumerieren einer Momentaufnahme von Geräten*](https://docs.microsoft.com/windows/uwp/devices-sensors/enumerate-devices#enumerate-a-snapshot-of-devices) finden Sie weitere Informationen zur Verwendung von *FindAllAsync*.</span><span class="sxs-lookup"><span data-stu-id="6dbd9-118">See [*Enumerate a snapshot of devices*](https://docs.microsoft.com/windows/uwp/devices-sensors/enumerate-devices#enumerate-a-snapshot-of-devices) for more information on using *FindAllAsync*.</span></span>

### **<a name="option-b-enumerate-and-watch-for-changes-in-available-barcode-scanners"></a><span data-ttu-id="6dbd9-119">Option B: Enumerieren und Überwachen von Änderungen in verfügbaren Strichcodescannern</span><span class="sxs-lookup"><span data-stu-id="6dbd9-119">Option B: Enumerate and watch for changes in available barcode scanners</span></span>**
```Csharp
DeviceWatcher deviceWatcher = DeviceInformation.CreateWatcher(selector);

// TODO: Add Event Listeners and Handlers
```
> [!TIP]
> <span data-ttu-id="6dbd9-120">Weitere Informationen finden Sie unter [*Enumerieren und Überwachen von Änderungen in Geräten*](https://docs.microsoft.com/windows/uwp/devices-sensors/enumerate-devices#enumerate-and-watch-devices) und [*DeviceWatcher*](https://docs.microsoft.com/uwp/api/Windows.Devices.Enumeration.DeviceWatcher).</span><span class="sxs-lookup"><span data-stu-id="6dbd9-120">See [*Enumerate and watch device changes*](https://docs.microsoft.com/windows/uwp/devices-sensors/enumerate-devices#enumerate-and-watch-devices) and [*DeviceWatcher*](https://docs.microsoft.com/uwp/api/Windows.Devices.Enumeration.DeviceWatcher) for more information.</span></span>

## <a name="step-5-identify-camera-barcode-scanners"></a><span data-ttu-id="6dbd9-121">Schritt5: Identifizieren von Kamera-Strichcodescannern</span><span class="sxs-lookup"><span data-stu-id="6dbd9-121">Step 5: Identify camera barcode scanners</span></span>
<span data-ttu-id="6dbd9-122">Ein Kamera-Strichcodescanner wird dynamisch erstellt, wenn Windows die Kamera(s) koppelt, die mit einen Software-Decoder an den Computer angeschlossen sind.</span><span class="sxs-lookup"><span data-stu-id="6dbd9-122">A camera barcode scanner is created dynamically as Windows pairs the camera(s) attached to your computer with a software decoder.</span></span>  <span data-ttu-id="6dbd9-123">Jede Kamera – gekoppelter Decoder ist ein voll funktionsfähiger Strichcodescanner.</span><span class="sxs-lookup"><span data-stu-id="6dbd9-123">Each camera - decoder pair is a fully functional barcode scanner.</span></span>

<span data-ttu-id="6dbd9-124">Für jeden Strichcodescanner in der resultieRendern Gerätesammlung, können Sie festlegen, welche Kamera-Strichcodescanner im Vergleich zu physischen Strichcodescannern sind, indem Sie die [*BarcodeScanner.VideoDeviceID*](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.videodeviceid#Windows_Devices_PointOfService_BarcodeScanner_VideoDeviceId)-Eigenschaft aktivieren.</span><span class="sxs-lookup"><span data-stu-id="6dbd9-124">For each barcode scanner in the resulting device collection, you can determine which are camera barcode scanners verses physical barcode scanners by checking the [*BarcodeScanner.VideoDeviceID*](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.videodeviceid#Windows_Devices_PointOfService_BarcodeScanner_VideoDeviceId) property.</span></span>  <span data-ttu-id="6dbd9-125">Eine Nicht-NULL-VideoDeviceID gibt an, dass das Strichcodescannerobjekt aus Ihrer Gerätesammlung ein Kamera-Strichcodescanner ist.</span><span class="sxs-lookup"><span data-stu-id="6dbd9-125">A non-NULL VideoDeviceID will indicate that the barcode scanner object from your device collection is a camera barcode scanner.</span></span>  <span data-ttu-id="6dbd9-126">Wenn Sie mehrere Kamera-Strichcodescanner haben, können Sie eine separate Sammlungen erstellen, die physische Strichcodescanner ausschließt..</span><span class="sxs-lookup"><span data-stu-id="6dbd9-126">If you have more than one camera barcode scanner you may want to build a separate collection which excludes physical barcode scanners.</span></span> 

<span data-ttu-id="6dbd9-127">Kamera-Strichcodescanner, die den Decoder verwenden, der mit Windows geliefert wird, sehen folgendes:</span><span class="sxs-lookup"><span data-stu-id="6dbd9-127">Camera barcode scanners using the decoder that ships with Windows will appear as:</span></span> 

> <span data-ttu-id="6dbd9-128">Microsoft-BarcodeScanner (*Name der Kamera hier*)</span><span class="sxs-lookup"><span data-stu-id="6dbd9-128">Microsoft BarcodeScanner (*name of your camera here*)</span></span>

<span data-ttu-id="6dbd9-129">Wenn Ihre Kamera im Gehäuse des Computers integriert ist, kann der Name sich zwischen *vorne* und *hinten* unterscheiden, wenn Sie über mehrere Kameras verfügen.</span><span class="sxs-lookup"><span data-stu-id="6dbd9-129">If your camera is built in to the chassis of your computer, the name may differentiate between *front* and *rear* if you have more than one camera.</span></span>  <span data-ttu-id="6dbd9-130">In Zukunft sind möglicherweise zusätzliche Softwaredecoder verfügbar, die ein anderes Benennungsschema haben.</span><span class="sxs-lookup"><span data-stu-id="6dbd9-130">In the future, additional software decoders may be available and carry a different naming scheme.</span></span>

## <a name="step-6-claim-the-camera-barcode-scanner"></a><span data-ttu-id="6dbd9-131">Schritt6: Anfordern des Kamera-Strichcodescanners</span><span class="sxs-lookup"><span data-stu-id="6dbd9-131">Step 6: Claim the camera barcode scanner</span></span> 
<span data-ttu-id="6dbd9-132">Verwenden Sie [BarcodeScanner.ClaimScannerAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.claimscannerasync#Windows_Devices_PointOfService_BarcodeScanner_ClaimScannerAsync), um eine exklusive Verwendung des Kamera-Strichcodescanners zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="6dbd9-132">Use [BarcodeScanner.ClaimScannerAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.claimscannerasync#Windows_Devices_PointOfService_BarcodeScanner_ClaimScannerAsync) to obtain exclusive use of the camera barcode scanner.</span></span>

## <a name="step-7-system-provided-preview"></a><span data-ttu-id="6dbd9-133">Schritt7: Vom System bereitgestellte Vorschau</span><span class="sxs-lookup"><span data-stu-id="6dbd9-133">Step 7: System provided preview</span></span>
<span data-ttu-id="6dbd9-134">Eine Kameravorschau ist für den Benutzer notwendig, um die Kamera auf Barcodes zu richten.</span><span class="sxs-lookup"><span data-stu-id="6dbd9-134">A camera preview is needed for the user to successfully aim the camera at barcodes.</span></span>  <span data-ttu-id="6dbd9-135">Windows bietet eine einfache Kameravorschau, die ein Dialogfeld startet, das die einfache Steuerung des Kamera-Strichcodescanners ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="6dbd9-135">Windows provides a simple camera preview that will launch a dialog that enables basic control of the camera barcode scanner.</span></span>  <span data-ttu-id="6dbd9-136">Rufen Sie einfach [ClaimedBarcodeScanner.ShowVideoPreview](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.showvideopreviewasync) auf, um das Dialogfeld zu öffnen und [ClaimedBarcodeScanner.HideVideoPreview](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.hidevideopreview) zu schließen, wenn Sie fertig sind.</span><span class="sxs-lookup"><span data-stu-id="6dbd9-136">Simply call [ClaimedBarcodeScanner.ShowVideoPreview](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.showvideopreviewasync) to open the dialog and [ClaimedBarcodeScanner.HideVideoPreview](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.hidevideopreview) to close it when finished.</span></span>

> [!TIP]
> <span data-ttu-id="6dbd9-137">Unter See [Hosting-Vorschau](pos-camerabarcode-hosting-preview.md) erfahren Sie, wie Sie die Vorschau für Kamera-Strichcodescanner in Ihrer Anwendung hosten.</span><span class="sxs-lookup"><span data-stu-id="6dbd9-137">See [Hosting Preview](pos-camerabarcode-hosting-preview.md) to host the preview for camera barcode scanner in your application.</span></span>

## <a name="step-8-initiate-scan"></a><span data-ttu-id="6dbd9-138">Schritt 8: Initialisieren scan</span><span class="sxs-lookup"><span data-stu-id="6dbd9-138">Step 8: Initiate scan</span></span> 
<span data-ttu-id="6dbd9-139">Sie können den Überprüfungsvorgang initiieren, indem Sie [**StartSoftwareTriggerAsync**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.startsoftwaretriggerasync#Windows_Devices_PointOfService_ClaimedBarcodeScanner_StartSoftwareTriggerAsync) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="6dbd9-139">You can initiate the scan process by calling [**StartSoftwareTriggerAsync**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.startsoftwaretriggerasync#Windows_Devices_PointOfService_ClaimedBarcodeScanner_StartSoftwareTriggerAsync).</span></span>  
<span data-ttu-id="6dbd9-140">Je nach Wert des [**IsDisabledOnDataReceived**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.isdisabledondatareceived#Windows_Devices_PointOfService_ClaimedBarcodeScanner_IsDisabledOnDataReceived) kann der Scanner nur einen Strichcode scannen und diesen beenden oder kontinuierlich bis zum Aufruf von [**StopSoftwareTriggerAsync**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.stopsoftwaretriggerasync#Windows_Devices_PointOfService_ClaimedBarcodeScanner_StopSoftwareTriggerAsync) scannen.</span><span class="sxs-lookup"><span data-stu-id="6dbd9-140">Depending on the value of [**IsDisabledOnDataReceived**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.isdisabledondatareceived#Windows_Devices_PointOfService_ClaimedBarcodeScanner_IsDisabledOnDataReceived) the scanner may scan only one barcode then stop or scan continuously until you call [**StopSoftwareTriggerAsync**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.stopsoftwaretriggerasync#Windows_Devices_PointOfService_ClaimedBarcodeScanner_StopSoftwareTriggerAsync).</span></span>

<span data-ttu-id="6dbd9-141">Legen Sie den gewünschten Wert der [**IsDisabledOnDataReceived**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.isdisabledondatareceived#Windows_Devices_PointOfService_ClaimedBarcodeScanner_IsDisabledOnDataReceived) fest, um das Verhalten des Scanners zu steuern, wenn ein Strichcode decodiert wird.</span><span class="sxs-lookup"><span data-stu-id="6dbd9-141">Set the desired value of [**IsDisabledOnDataReceived**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.isdisabledondatareceived#Windows_Devices_PointOfService_ClaimedBarcodeScanner_IsDisabledOnDataReceived) to control the scanner behavior when a barcode is decoded.</span></span>

| <span data-ttu-id="6dbd9-142">Wert</span><span class="sxs-lookup"><span data-stu-id="6dbd9-142">Value</span></span> | <span data-ttu-id="6dbd9-143">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6dbd9-143">Description</span></span> |
| ----- | ----------- |
| <span data-ttu-id="6dbd9-144">Wahr</span><span class="sxs-lookup"><span data-stu-id="6dbd9-144">True</span></span>   | <span data-ttu-id="6dbd9-145">Nur einen Barcode scannen und dann beenden</span><span class="sxs-lookup"><span data-stu-id="6dbd9-145">Scan only one barcode then stop</span></span> |
| <span data-ttu-id="6dbd9-146">False</span><span class="sxs-lookup"><span data-stu-id="6dbd9-146">False</span></span>  | <span data-ttu-id="6dbd9-147">Scannen Sie Barcodes ohne Unterbrechung</span><span class="sxs-lookup"><span data-stu-id="6dbd9-147">Continuously scan barcodes without stopping</span></span> |