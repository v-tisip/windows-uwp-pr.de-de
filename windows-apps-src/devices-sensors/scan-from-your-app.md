---
author: PatrickFarley
ms.assetid: 374D1983-60E0-4E18-ABBB-04775BAA0F0D
title: Scannen aus Ihrer App
description: Erfahren Sie, wie Sie Inhalte über Ihre App mithilfe eines Flachbett-, Einzugs- oder automatisch konfigurierten Scanners scannen können.
ms.author: pafarley
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: f9128056cbb3b9218d164b243948d9dd16af0786
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2018
ms.locfileid: "7151804"
---
# <a name="scan-from-your-app"></a><span data-ttu-id="e282b-104">Scannen aus Ihrer App</span><span class="sxs-lookup"><span data-stu-id="e282b-104">Scan from your app</span></span>


**<span data-ttu-id="e282b-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="e282b-105">Important APIs</span></span>**

-   [**<span data-ttu-id="e282b-106">Windows.Devices.Scanners</span><span class="sxs-lookup"><span data-stu-id="e282b-106">Windows.Devices.Scanners</span></span>**](https://msdn.microsoft.com/library/windows/apps/Dn264250)
-   [**<span data-ttu-id="e282b-107">DeviceInformation</span><span class="sxs-lookup"><span data-stu-id="e282b-107">DeviceInformation</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR225393)
-   [**<span data-ttu-id="e282b-108">DeviceClass</span><span class="sxs-lookup"><span data-stu-id="e282b-108">DeviceClass</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR225381)

<span data-ttu-id="e282b-109">Erfahren Sie, wie Sie Inhalte über Ihre App mithilfe eines Flachbett-, Einzugs- oder automatisch konfigurierten Scanners scannen können.</span><span class="sxs-lookup"><span data-stu-id="e282b-109">Learn here how to scan content from your app by using a flatbed, feeder, or auto-configured scan source.</span></span>

<span data-ttu-id="e282b-110">**Wichtige**die [**Windows.Devices.Scanners**](https://msdn.microsoft.com/library/windows/apps/Dn264250) -APIs sind Teil der desktop [-Gerätefamilie](https://msdn.microsoft.com/library/windows/apps/Dn894631).</span><span class="sxs-lookup"><span data-stu-id="e282b-110">**Important**The [**Windows.Devices.Scanners**](https://msdn.microsoft.com/library/windows/apps/Dn264250) APIs are part of the desktop [device family](https://msdn.microsoft.com/library/windows/apps/Dn894631).</span></span> <span data-ttu-id="e282b-111">Apps können diese APIs nur in der Desktopversion von Windows 10 verwenden.</span><span class="sxs-lookup"><span data-stu-id="e282b-111">Apps can use these APIs only on the desktop version of Windows10.</span></span>

<span data-ttu-id="e282b-112">Damit Sie über Ihre App scannen können, müssen Sie zunächst die verfügbaren Scanner auflisten, indem Sie ein neues [**DeviceInformation**](https://msdn.microsoft.com/library/windows/apps/BR225393)-Objekt deklarieren und den [**DeviceClass**](https://msdn.microsoft.com/library/windows/apps/BR225381)-Typ abrufen.</span><span class="sxs-lookup"><span data-stu-id="e282b-112">To scan from your app, you must first list the available scanners by declaring a new [**DeviceInformation**](https://msdn.microsoft.com/library/windows/apps/BR225393) object and getting the [**DeviceClass**](https://msdn.microsoft.com/library/windows/apps/BR225381) type.</span></span> <span data-ttu-id="e282b-113">Nur Scanner, die lokal mit WIA-Treibern installiert sind, werden in Ihrer App aufgeführt und stehen darin zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="e282b-113">Only scanners that are installed locally with WIA drivers are listed and available to your app.</span></span>

<span data-ttu-id="e282b-114">Nachdem Ihre App verfügbare Scanner aufgelistet hat, kann sie die auf dem Scannertyp basierenden automatisch konfigurierten Scaneinstellungen verwenden oder einfach unter Verwendung der verfügbaren Flachbett- oder Einzugsscanquelle scannen.</span><span class="sxs-lookup"><span data-stu-id="e282b-114">After your app has listed available scanners, it can use the auto-configured scan settings based on the scanner type, or just scan using the available flatbed or feeder scan source.</span></span> <span data-ttu-id="e282b-115">Damit die automatisch konfigurierten Einstellungen verwendet werden können, muss der Scanner mit der automatischen Konfiguration kompatibel sein und darf nicht sowohl über einen Flachbett- als auch über einen Einzugsscanner verfügen.</span><span class="sxs-lookup"><span data-stu-id="e282b-115">To use auto-configured settings, the scanner must be enabled for auto-configuration must not be equipped with both a flatbed and a feeder scanner.</span></span> <span data-ttu-id="e282b-116">Weitere Informationen finden Sie unter [Automatisch konfigurierter Scan](https://msdn.microsoft.com/library/windows/hardware/Ff539393).</span><span class="sxs-lookup"><span data-stu-id="e282b-116">For more info, see [Auto-Configured Scanning](https://msdn.microsoft.com/library/windows/hardware/Ff539393).</span></span>

## <a name="enumerate-available-scanners"></a><span data-ttu-id="e282b-117">Aufzählen verfügbarer Scanner</span><span class="sxs-lookup"><span data-stu-id="e282b-117">Enumerate available scanners</span></span>

<span data-ttu-id="e282b-118">Windows erkennt Scanner nicht automatisch.</span><span class="sxs-lookup"><span data-stu-id="e282b-118">Windows does not detect scanners automatically.</span></span> <span data-ttu-id="e282b-119">Sie müssen diesen Schritt ausführen, damit Ihre App mit dem Scanner kommunizieren kann.</span><span class="sxs-lookup"><span data-stu-id="e282b-119">You must perform this step in order for your app to communicate with the scanner.</span></span> <span data-ttu-id="e282b-120">In diesem Beispiel erfolgt die Scannergeräteaufzählung mit dem [**Windows.Devices.Enumeration**](https://msdn.microsoft.com/library/windows/apps/BR225459)-Namespace.</span><span class="sxs-lookup"><span data-stu-id="e282b-120">In this example, the scanner device enumeration is done using the [**Windows.Devices.Enumeration**](https://msdn.microsoft.com/library/windows/apps/BR225459) namespace.</span></span>

1.  <span data-ttu-id="e282b-121">Fügen Sie zunächst diese using-Anweisungen zu Ihrer Klassendefinitionsdatei hinzu.</span><span class="sxs-lookup"><span data-stu-id="e282b-121">First, add these using statements to your class definition file.</span></span>

``` csharp
    using Windows.Devices.Enumeration;
    using Windows.Devices.Scanners;
```

2.  <span data-ttu-id="e282b-122">Implementieren Sie dann die Geräteüberwachung, um mit der Scanneraufzählung zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="e282b-122">Next, implement a device watcher to start enumerating scanners.</span></span> <span data-ttu-id="e282b-123">Weitere Informationen finden Sie unter [Aufzählen von Geräten](enumerate-devices.md).</span><span class="sxs-lookup"><span data-stu-id="e282b-123">For more info, see [Enumerate devices](enumerate-devices.md).</span></span>

```csharp
    void InitDeviceWatcher()
    {
       // Create a Device Watcher class for type Image Scanner for enumerating scanners
       scannerWatcher = DeviceInformation.CreateWatcher(DeviceClass.ImageScanner);

       scannerWatcher.Added += OnScannerAdded;
       scannerWatcher.Removed += OnScannerRemoved;
       scannerWatcher.EnumerationCompleted += OnScannerEnumerationComplete;
    }
```

3.  <span data-ttu-id="e282b-124">Erstellen Sie einen Ereignishandler für den Fall, dass ein Scanner hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="e282b-124">Create an event handler for when a scanner is added.</span></span>

```csharp
    private async void OnScannerAdded(DeviceWatcher sender,  DeviceInformation deviceInfo)
    {
       await
       MainPage.Current.Dispatcher.RunAsync(
             Windows.UI.Core.CoreDispatcherPriority.Normal,
             () =>
             {
                MainPage.Current.NotifyUser(String.Format("Scanner with device id {0} has been added", deviceInfo.Id), NotifyType.StatusMessage);

                // search the device list for a device with a matching device id
                ScannerDataItem match = FindInList(deviceInfo.Id);

                // If we found a match then mark it as verified and return
                if (match != null)
                {
                   match.Matched = true;
                   return;
                }

                // Add the new element to the end of the list of devices
                AppendToList(deviceInfo);
             }
       );
    }
```

## <a name="scan"></a><span data-ttu-id="e282b-125">Überprüfen</span><span class="sxs-lookup"><span data-stu-id="e282b-125">Scan</span></span>

1.  **<span data-ttu-id="e282b-126">Abrufen eines ImageScanner-Objekts</span><span class="sxs-lookup"><span data-stu-id="e282b-126">Get an ImageScanner object</span></span>**

<span data-ttu-id="e282b-127">Für jeden [**ImageScannerScanSource**](https://msdn.microsoft.com/library/windows/apps/Dn264238)-Aufzählungstyp (ob **Default**, **AutoConfigured**, **Flatbed** oder **Feeder**) müssen Sie zunächst ein [**ImageScanner**](https://msdn.microsoft.com/library/windows/apps/Dn263806)-Objekt erstellen, indem Sie wie folgt die [**ImageScanner.FromIdAsync**](https://msdn.microsoft.com/library/windows/apps/windows.devices.scanners.imagescanner.fromidasync)-Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="e282b-127">For each [**ImageScannerScanSource**](https://msdn.microsoft.com/library/windows/apps/Dn264238) enumeration type, whether it's **Default**, **AutoConfigured**, **Flatbed**, or **Feeder**, you must first create an [**ImageScanner**](https://msdn.microsoft.com/library/windows/apps/Dn263806) object by calling the [**ImageScanner.FromIdAsync**](https://msdn.microsoft.com/library/windows/apps/windows.devices.scanners.imagescanner.fromidasync) method, like this.</span></span>

 ```csharp
    ImageScanner myScanner = await ImageScanner.FromIdAsync(deviceId);
 ```

2.  **<span data-ttu-id="e282b-128">Einfach scannen</span><span class="sxs-lookup"><span data-stu-id="e282b-128">Just scan</span></span>**

<span data-ttu-id="e282b-129">Zum Scan mit den Standardeinstellungen ist Ihre App bei der Auswahl eines Scanners vom [**Windows.Devices.Scanners**](https://msdn.microsoft.com/library/windows/apps/Dn264250)-Namespace abhängig und scannt aus dieser Quelle.</span><span class="sxs-lookup"><span data-stu-id="e282b-129">To scan with the default settings, your app relies on the [**Windows.Devices.Scanners**](https://msdn.microsoft.com/library/windows/apps/Dn264250) namespace to select a scanner and scans from that source.</span></span> <span data-ttu-id="e282b-130">Es werden keine Scaneinstellungen geändert.</span><span class="sxs-lookup"><span data-stu-id="e282b-130">No scan settings are changed.</span></span> <span data-ttu-id="e282b-131">Die möglichen Scanner sind „Automatisch konfiguriert“, „Flachbett“ und „Einzug“.</span><span class="sxs-lookup"><span data-stu-id="e282b-131">The possible scanners are auto-configure, flatbed, or feeder.</span></span> <span data-ttu-id="e282b-132">Bei dieser Scanart kommt es wahrscheinlich zu einem erfolgreichen Scanvorgang, selbst wenn der Scan von der falschen Quelle aus stattfindet (wie Flachbett anstelle von Einzug).</span><span class="sxs-lookup"><span data-stu-id="e282b-132">This type of scan will most likely produce a successful scan operation, even if it scans from the wrong source, like flatbed instead of feeder.</span></span>

<span data-ttu-id="e282b-133">**Hinweis:** Wenn der Benutzer das Dokument zum Scannen in den Einzug legt, erfolgt der Scanvorgang aus dem Flachbett stattdessen.</span><span class="sxs-lookup"><span data-stu-id="e282b-133">**Note**If the user places the document to scan in the feeder, the scanner will scan from the flatbed instead.</span></span> <span data-ttu-id="e282b-134">Wenn der Benutzer versucht, aus einem leeren Einzug zu scannen, generiert der Scanauftrag keine gescannten Dateien.</span><span class="sxs-lookup"><span data-stu-id="e282b-134">If the user tries to scan from an empty feeder, the scan job won't produce any scanned files.</span></span>
 
```csharp
    var result = await myScanner.ScanFilesToFolderAsync(ImageScannerScanSource.Default,
        folder).AsTask(cancellationToken.Token, progress);
```

3.  **<span data-ttu-id="e282b-135">Scannen aus der Quelle „Automatisch konfiguriert“, „Flachbett“ oder „Einzug“</span><span class="sxs-lookup"><span data-stu-id="e282b-135">Scan from Auto-configured, Flatbed, or Feeder source</span></span>**

<span data-ttu-id="e282b-136">Ihre App kann den [automatisch konfigurierten Scan](https://msdn.microsoft.com/library/windows/hardware/Ff539393) des Geräts mit den optimalen Scaneinstellungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="e282b-136">Your app can use the device's [Auto-Configured Scanning](https://msdn.microsoft.com/library/windows/hardware/Ff539393) to scan with the most optimal scan settings.</span></span> <span data-ttu-id="e282b-137">Bei dieser Option kann das Gerät selbst die besten Scaneinstellungen, wie Farbmodus und Scanauflösung, basierend auf dem zu scannenden Inhalt bestimmen.</span><span class="sxs-lookup"><span data-stu-id="e282b-137">With this option, the device itself can determine the best scan settings, like color mode and scan resolution, based on the content being scanned.</span></span> <span data-ttu-id="e282b-138">Das Gerät wählt die Scaneinstellungen zur Laufzeit für jeden neuen Scanauftrag.</span><span class="sxs-lookup"><span data-stu-id="e282b-138">The device selects the scan settings at run time for each new scan job.</span></span>

<span data-ttu-id="e282b-139">**Hinweis:** dieses Feature wird von nicht von allen Scannern unterstützt, daher die app prüfen muss, ob der Scanner dieses Feature unterstützt, bevor Sie diese Einstellung verwenden.</span><span class="sxs-lookup"><span data-stu-id="e282b-139">**Note**Not all scanners support this feature, so the app must check if the scanner supports this feature before using this setting.</span></span>

<span data-ttu-id="e282b-140">In diesem Beispiel prüft die App zunächst, ob der Scanner die automatische Konfiguration unterstützt, und startet dann den Scanvorgang.</span><span class="sxs-lookup"><span data-stu-id="e282b-140">In this example, the app first checks if the scanner is capable of auto-configuration and then scans.</span></span> <span data-ttu-id="e282b-141">Um einen Flachbett- oder Einzugsscanner anzugeben, ersetzen Sie einfach **AutoConfigured** durch **Flatbed** oder **Feeder**.</span><span class="sxs-lookup"><span data-stu-id="e282b-141">To specify either flatbed or feeder scanner, simply replace **AutoConfigured** with **Flatbed** or **Feeder**.</span></span>

```csharp
    if (myScanner.IsScanSourceSupported(ImageScannerScanSource.AutoConfigured))
    {
        ...
        // Scan API call to start scanning with Auto-Configured settings.
        var result = await myScanner.ScanFilesToFolderAsync(
            ImageScannerScanSource.AutoConfigured, folder).AsTask(cancellationToken.Token, progress);
        ...
    }
```

## <a name="preview-the-scan"></a><span data-ttu-id="e282b-142">Scanvorschau</span><span class="sxs-lookup"><span data-stu-id="e282b-142">Preview the scan</span></span>

<span data-ttu-id="e282b-143">Sie können Code hinzufügen, um eine Scanvorschau vor dem Scan in einen Ordner anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="e282b-143">You can add code to preview the scan before scanning to a folder.</span></span> <span data-ttu-id="e282b-144">Im folgenden Beispiel prüft die App, ob der **Flatbed**-Scanner die Vorschau unterstützt, und zeigt dann die Scanvorschau an.</span><span class="sxs-lookup"><span data-stu-id="e282b-144">In the example below, the app checks if the **Flatbed** scanner supports preview, then previews the scan.</span></span>

```csharp
if (myScanner.IsPreviewSupported(ImageScannerScanSource.Flatbed))
{
    rootPage.NotifyUser("Scanning", NotifyType.StatusMessage);
                // Scan API call to get preview from the flatbed.
                var result = await myScanner.ScanPreviewToStreamAsync(
                    ImageScannerScanSource.Flatbed, stream);
```

## <a name="cancel-the-scan"></a><span data-ttu-id="e282b-145">Abbrechen des Scans</span><span class="sxs-lookup"><span data-stu-id="e282b-145">Cancel the scan</span></span>

<span data-ttu-id="e282b-146">Sie können wie folgt zulassen, dass Benutzer den Scanauftrag während der Ausführung abbrechen.</span><span class="sxs-lookup"><span data-stu-id="e282b-146">You can let users cancel the scan job midway through a scan, like this.</span></span>

```csharp
void CancelScanning()
{
    if (ModelDataContext.ScenarioRunning)
    {
        if (cancellationToken != null)
        {
            cancellationToken.Cancel();
        }                
        DisplayImage.Source = null;
        ModelDataContext.ScenarioRunning = false;
        ModelDataContext.ClearFileList();
    }
}
```

## <a name="scan-with-progress"></a><span data-ttu-id="e282b-147">Scannen mit Fortschritt</span><span class="sxs-lookup"><span data-stu-id="e282b-147">Scan with progress</span></span>

1.  <span data-ttu-id="e282b-148">Erstellen eines **System.Threading.CancellationTokenSource**-Objekts.</span><span class="sxs-lookup"><span data-stu-id="e282b-148">Create a **System.Threading.CancellationTokenSource** object.</span></span>

```csharp
cancellationToken = new CancellationTokenSource();
```

2.  <span data-ttu-id="e282b-149">Richten Sie den Fortschritts-Ereignishandler ein, und rufen Sie den Scanfortschritt ab.</span><span class="sxs-lookup"><span data-stu-id="e282b-149">Set up the progress event handler and get the progress of the scan.</span></span>

```csharp
    rootPage.NotifyUser("Scanning", NotifyType.StatusMessage);
    var progress = new Progress<UInt32>(ScanProgress);
```

## <a name="scanning-to-the-pictures-library"></a><span data-ttu-id="e282b-150">Scannen in die Bildbibliothek</span><span class="sxs-lookup"><span data-stu-id="e282b-150">Scanning to the pictures library</span></span>

<span data-ttu-id="e282b-151">Benutzer können dynamisch mit der [**FolderPicker**](https://msdn.microsoft.com/library/windows/apps/BR207881)-Klasse in beliebige Ordner scannen. Sie müssen aber die Funktion *Bildbibliothek* im Manifest deklarieren, damit Benutzer in diesen Ordner scannen können.</span><span class="sxs-lookup"><span data-stu-id="e282b-151">Users can scan to any folder dynamically using the [**FolderPicker**](https://msdn.microsoft.com/library/windows/apps/BR207881) class, but you must declare the *Pictures Library* capability in the manifest to allow users to scan to that folder.</span></span> <span data-ttu-id="e282b-152">Weitere Informationen zu App-Funktionen finden Sie unter [Deklarationen der App-Funktionen](https://msdn.microsoft.com/library/windows/apps/Mt270968).</span><span class="sxs-lookup"><span data-stu-id="e282b-152">For more info on app capabilities, see [App capability declarations](https://msdn.microsoft.com/library/windows/apps/Mt270968).</span></span>
