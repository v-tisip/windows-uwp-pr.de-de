---
title: Erste Schritte mit Point Of Service-Geräten
description: Dieser Artikel enthält Informationen für erste Schritte mit Point Of Service-UWP-Apps.
ms.date: 05/1/2018
ms.topic: article
keywords: Windows 10, UWP, Point Of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: 0e537e40d5224f2522cb5ecebd92664d1794dd06
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8743730"
---
# <a name="getting-started-with-point-of-service"></a><span data-ttu-id="eb563-104">Erste Schritte mit Point Of Service-Geräten</span><span class="sxs-lookup"><span data-stu-id="eb563-104">Getting started with Point of Service</span></span>

<span data-ttu-id="eb563-105">Point Of Service-, Point Of Sale- oder POS-Geräte sind Peripheriegeräte des Computers für Einzelhandelstransaktionen.</span><span class="sxs-lookup"><span data-stu-id="eb563-105">Point of service, point of sale, or Point of Service devices are computer peripherals used to facilitate retail transactions.</span></span> <span data-ttu-id="eb563-106">Beispiele für POS-Geräte sind elektronische Registrierkassen, Strichcodescanner, Magnetstreifenleser und Belegdrucker.</span><span class="sxs-lookup"><span data-stu-id="eb563-106">Examples of Point of Service devices include electronic cash registers, barcode scanners, magnetic stripe readers, and receipt printers.</span></span>

<span data-ttu-id="eb563-107">In dieser Anleitung lernen Sie die Grundlagen der Anbindung an POS-Geräte mithilfe der POS-APIs für die Universelle Windows-Plattform (UWP) kennen.</span><span class="sxs-lookup"><span data-stu-id="eb563-107">Here you’ll learn the basics of interfacing with Point of Service devices by using the Universal Windows Platform (UWP) PointOfService APIs.</span></span> <span data-ttu-id="eb563-108">Behandelt werden Themen wie Geräteenumeration, Überprüfen von Gerätefunktionen, Anfordern von Geräten und die gemeinsame Nutzung von Geräten.</span><span class="sxs-lookup"><span data-stu-id="eb563-108">We’ll cover device enumeration, checking device capabilities, claiming devices, and device sharing.</span></span> <span data-ttu-id="eb563-109">Wir verwenden einen Strichcodescanner als Beispiel, aber fast alle Erläuterungen in dieser Anleitung gelten für alle UWP-kompatiblen POS-Geräte.</span><span class="sxs-lookup"><span data-stu-id="eb563-109">We use a barcode scanner device as an example, but almost all the guidance here applies to any UWP-compatible Point of Service device.</span></span> <span data-ttu-id="eb563-110">(Eine Liste der unterstützten Geräte finden Sie unter [POS-Geräteunterstützung](pos-device-support.md)).</span><span class="sxs-lookup"><span data-stu-id="eb563-110">(For a list of supported devices, see [Point of Service device support](pos-device-support.md)).</span></span>

## <a name="finding-and-connecting-to-point-of-service-peripherals"></a><span data-ttu-id="eb563-111">Koppeln von POS-Peripheriegeräten</span><span class="sxs-lookup"><span data-stu-id="eb563-111">Finding and connecting to Point of Service peripherals</span></span>

<span data-ttu-id="eb563-112">Bevor ein POS-Gerät von einer App verwendet werden kann, muss es mit dem PC gekoppelt werden, auf dem die App ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="eb563-112">Before a Point of Service device can be used by an app, it must be paired with the PC where the app is running.</span></span> <span data-ttu-id="eb563-113">Es gibt verschiedene Möglichkeiten, Verbindungen mit POS-Geräten herzustellen, entweder programmgesteuert oder über die App „Einstellungen”.</span><span class="sxs-lookup"><span data-stu-id="eb563-113">There are several ways to connect to Point of Service devices, either programmatically or through the Settings app.</span></span>

### <a name="connecting-to-devices-by-using-the-settings-app"></a><span data-ttu-id="eb563-114">Herstellen einer Verbindung mit Geräten mithilfe der App „Einstellungen”</span><span class="sxs-lookup"><span data-stu-id="eb563-114">Connecting to devices by using the Settings app</span></span>
<span data-ttu-id="eb563-115">Wenn Sie ein POS-Gerät, z.B. einen Strichcodescanner, an einen PC anschließen, wird es wie jedes anderes Gerät angezeigt.</span><span class="sxs-lookup"><span data-stu-id="eb563-115">When you plug a Point of Service device like a barcode scanner into a PC, it shows up just like any other device.</span></span> <span data-ttu-id="eb563-116">Sie finden es im Abschnitt **Geräte > Bluetooth- & andere Geräte** der App „Einstellungen”.</span><span class="sxs-lookup"><span data-stu-id="eb563-116">You can find it in the **Devices > Bluetooth & other devices** section of the Settings app.</span></span> <span data-ttu-id="eb563-117">Hier können Sie POS-Geräte koppeln, indem Sie **Bluetooth- oder anderes Gerät hinzufügen** wählen.</span><span class="sxs-lookup"><span data-stu-id="eb563-117">There you can pair with a Point of Service device by selecting **Add Bluetooth or other device**.</span></span>

<span data-ttu-id="eb563-118">Einige POS-Geräte werden möglicherweise erst dann in den Einstellungen angezeigt, nachdem sie mithilfe der POS-APIs programmgesteuert aufgelistet wurden.</span><span class="sxs-lookup"><span data-stu-id="eb563-118">Some Point of Service devices may not appear in the Settings app until they are programmatically enumerated by using the Point of Service APIs.</span></span>

### <a name="getting-a-single-point-of-service-device-with-getdefaultasync"></a><span data-ttu-id="eb563-119">Abrufen eines POS-Geräts mit GetDefaultAsync</span><span class="sxs-lookup"><span data-stu-id="eb563-119">Getting a single Point of Service device with GetDefaultAsync</span></span>
<span data-ttu-id="eb563-120">In einem einfachen Anwendungsfall haben Sie vielleicht nur ein POS-Peripheriegerät mit dem PC verbunden, auf dem die App ausgeführt wird, und möchten es so schnell wie möglich einrichten.</span><span class="sxs-lookup"><span data-stu-id="eb563-120">In a simple use case, you may have just one Point of Service peripheral connected to the PC where the app is running and want to set it up as quickly as possible.</span></span> <span data-ttu-id="eb563-121">Rufen Sie dazu das Standardgerät „Default” mit der **GetDefaultAsync**-Methode ab, wie hier gezeigt.</span><span class="sxs-lookup"><span data-stu-id="eb563-121">To do that, retrieve the “default” device with the **GetDefaultAsync** method as shown here.</span></span>

```Csharp
using Windows.Devices.PointOfService;

BarcodeScanner barcodeScanner = await BarcodeScanner.GetDefaultAsync();
```

<span data-ttu-id="eb563-122">Nachdem dieses Standardgerät gefunden wurde, kann das abgerufene Geräteobjekt beansprucht werden.</span><span class="sxs-lookup"><span data-stu-id="eb563-122">If the default device is found, the device object retrieved is ready to be claimed.</span></span> <span data-ttu-id="eb563-123">Eine Anwendung, die ein Gerät „beansprucht”, erhält exklusiven Zugriff darauf. Dadurch werden Konflikte vermieden, die entstehen würden, wenn mehrere Prozesse auf das Gerät zugreifen.</span><span class="sxs-lookup"><span data-stu-id="eb563-123">“Claiming” a device gives an application exclusive access to it, preventing conflicting commands from multiple processes.</span></span>

> [!NOTE] 
> <span data-ttu-id="eb563-124">Wenn mehrere POS-Geräte mit dem PC verbunden sind, liefert **GetDefaultAsync** das erste gefundene Gerät.</span><span class="sxs-lookup"><span data-stu-id="eb563-124">If more than one Point of Service device is connected to the PC, **GetDefaultAsync** returns the first device it finds.</span></span> <span data-ttu-id="eb563-125">Aus diesem Grund sollten Sie **FindAllAsync** verwenden, es sei denn, Sie sind sicher, dass die Anwendung nur ein POS-Gerät erkennt.</span><span class="sxs-lookup"><span data-stu-id="eb563-125">For this reason, use **FindAllAsync** unless you’re sure that only one Point of Service device is visible to the application.</span></span>

### <a name="enumerating-a-collection-of-devices-with-findallasync"></a><span data-ttu-id="eb563-126">Auflisten von Geräten mit FindAllAsync</span><span class="sxs-lookup"><span data-stu-id="eb563-126">Enumerating a collection of devices with FindAllAsync</span></span>

<span data-ttu-id="eb563-127">Sind mehrere Gerät angeschlossen, müssen Sie die Auflistung **PointOfService** durchsuchen, um das Geräteobjekt zu finden, das Sie beanspruchen möchten.</span><span class="sxs-lookup"><span data-stu-id="eb563-127">When connected to more than one device, you must enumerate the collection of **PointOfService** device objects to find the one you want to claim.</span></span> <span data-ttu-id="eb563-128">Der folgende Code erstellt z.B. eine Auflistung aller aktuell verbundenen Strichcodescanner und durchsucht die Auflistung dann nach einem Scanner mit einem bestimmten Namen.</span><span class="sxs-lookup"><span data-stu-id="eb563-128">For example, the following code creates a collection of all the barcode scanners currently connected, and then searches the collection for a scanner with a specific name.</span></span>

```Csharp
using Windows.Devices.Enumeration;
using Windows.Devices.PointOfService;

string selector = BarcodeScanner.GetDeviceSelector();       
DeviceInformationCollection deviceCollection = await DeviceInformation.FindAllAsync(selector);

foreach (DeviceInformation devInfo in deviceCollection)
{
    Debug.WriteLine("{0} {1}", devInfo.Name, devInfo.Id);
    if (devInfo.Name.Contains("1200G"))
    {
        Debug.WriteLine(" Found one");
    }
}
```

### <a name="scoping-the-device-selection"></a><span data-ttu-id="eb563-129">Begrenzen der Geräteauswahl</span><span class="sxs-lookup"><span data-stu-id="eb563-129">Scoping the device selection</span></span>
<span data-ttu-id="eb563-130">Beim Herstellen einer Verbindung mit einem Gerät können Sie die Suche auf eine Teilmenge der POS-Peripheriegeräte beschränken, auf die Ihre App zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="eb563-130">When connecting to a device, you may want to limit your search to a subset of Point of Service peripherals that your app has access to.</span></span> <span data-ttu-id="eb563-131">Mithilfe der Methode **GetDeviceSelector** beschränken Sie die Auflistung von Geräten auf solche, die nur über eine bestimmte Methode (Bluetooth, USB usw.) verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="eb563-131">Using the **GetDeviceSelector** method, you can scope the selection to retrieve devices connected only by a certain method (Bluetooth, USB, etc.).</span></span> <span data-ttu-id="eb563-132">Sie können einen Selektor erstellen, die über folgende Verbindungen nach Geräten sucht: **Bluetooth**, **IP**, **Local** oder **All connection types**.</span><span class="sxs-lookup"><span data-stu-id="eb563-132">You can create a selector that searches for devices over **Bluetooth**, **IP**, **Local**, or **All connection types**.</span></span> <span data-ttu-id="eb563-133">Das kann nützlich sein, da die Suche nach drahtlosen Geräte im Vergleich zur Suche nach lokalen (verkabelten) Geräten lange dauert.</span><span class="sxs-lookup"><span data-stu-id="eb563-133">This can be useful, as wireless device discovery takes a long time compared to local (wired) discovery.</span></span> <span data-ttu-id="eb563-134">Sie können eine bestimmte Wartezeit für die Verbindung mit lokalen Geräten sicherstellen, indem Sie **FindAllAsync** auf **Local**-Verbindungstypen beschränken.</span><span class="sxs-lookup"><span data-stu-id="eb563-134">You can ensure a deterministic wait time for local device connection by limiting **FindAllAsync** to **Local** connection types.</span></span> <span data-ttu-id="eb563-135">Dieser Code ermittelt beispielsweise alle Strichcodescanner, die über eine lokale Verbindung angeschlossen sind.</span><span class="sxs-lookup"><span data-stu-id="eb563-135">For example, this code retrieves all barcode scanners accessible via a local connection.</span></span> 

```Csharp
string selector = BarcodeScanner.GetDeviceSelector(PosConnectionTypes.Local);
DeviceInformationCollection deviceCollection = await DeviceInformation.FindAllAsync(selector);
```

### <a name="reacting-to-device-connection-changes-with-devicewatcher"></a><span data-ttu-id="eb563-136">Reagieren auf geänderte Geräteverbindungen mit DeviceWatcher</span><span class="sxs-lookup"><span data-stu-id="eb563-136">Reacting to device connection changes with DeviceWatcher</span></span>

<span data-ttu-id="eb563-137">Während Ihre App ausgeführt wird, ist nicht auszuschließen, dass Geräte getrennt, aktualisiert oder neu hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="eb563-137">As your app runs, sometimes devices will be disconnected or updated, or new devices will need to be added.</span></span> <span data-ttu-id="eb563-138">Sie können die Klasse **DeviceWatcher** verwenden, um auf gerätebezogene Ereignisse zuzugreifen, sodass Ihre App entsprechend reagieren kann.</span><span class="sxs-lookup"><span data-stu-id="eb563-138">You can use the **DeviceWatcher** class to access device-related events, so your app can respond accordingly.</span></span> <span data-ttu-id="eb563-139">Hier ein Beispiel zur Verwendung von **DeviceWatcher**. Der Code enthält Methodenstubs, die aufgerufen werden können, wenn ein Gerät hinzugefügt, entfernt oder aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="eb563-139">Here’s example of how to use **DeviceWatcher**, with method stubs to be called if a device is added, removed, or updated.</span></span>

```Csharp
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

## <a name="checking-the-capabilities-of-a-point-of-service-device"></a><span data-ttu-id="eb563-140">Überprüfen der Funktionalität eines POS-Geräts</span><span class="sxs-lookup"><span data-stu-id="eb563-140">Checking the capabilities of a Point of Service device</span></span>
<span data-ttu-id="eb563-141">Sogar innerhalb einer Geräteklasse (z.B. der Strichcodescanner) können die Attribute der einzelnen Geräte modellbedingt erheblich variieren.</span><span class="sxs-lookup"><span data-stu-id="eb563-141">Even within a device class, such as barcode scanners, the attributes of each device may vary considerably between models.</span></span> <span data-ttu-id="eb563-142">Wenn für Ihre App ein bestimmtes Geräteattribut erforderlich ist, sollten Sie jedes verbundene Gerätobjekt überprüfen, um festzustellen, ob das Attribut unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="eb563-142">If your app requires a specific device attribute, you may need to inspect each connected device object to determine whether the attribute is supported.</span></span> <span data-ttu-id="eb563-143">Beispielsweise könnte es für Ihr Unternehmen erforderlich sein, dass Bezeichnungen mit einem bestimmten Strichcodemuster versehen sind.</span><span class="sxs-lookup"><span data-stu-id="eb563-143">For example, perhaps your business requires that labels be created using a specific barcode printing pattern.</span></span> <span data-ttu-id="eb563-144">Im Folgenden wird gezeigt, wie Sie überprüfen können, ob ein verbundener Strichcodescanner eine Symbologie unterstützt.</span><span class="sxs-lookup"><span data-stu-id="eb563-144">Here’s how you could check to see whether a connected barcode scanner supports a symbology.</span></span> 

> [!NOTE]
> <span data-ttu-id="eb563-145">Eine Symbologie ist die Sprache, die zum Codieren von Nachrichten in einem Strichcode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="eb563-145">A symbology is the language mapping that a barcode uses to encode messages.</span></span>

```Csharp
try
{
    BarcodeScanner barcodeScanner = await BarcodeScanner.FromIdAsync(deviceId);
    if (await barcodeScanner.IsSymbologySupportedAsync(BarcodeSymbologies.Code32))
    {
        Debug.WriteLine("Has symbology");
    }
}
catch (Exception ex)
{
    Debug.WriteLine("FromIdAsync() - " + ex.Message);
}
```

### <a name="using-the-devicecapabilities-class"></a><span data-ttu-id="eb563-146">Verwenden der Device.Capabilities-Klasse</span><span class="sxs-lookup"><span data-stu-id="eb563-146">Using the Device.Capabilities class</span></span>
<span data-ttu-id="eb563-147">Die **Device.Capabilities**-Klasse ist ein Attribut aller POS-Geräteklassen und kann verwendet werden, um allgemeine Informationen zu einzelnen Geräten abzurufen.</span><span class="sxs-lookup"><span data-stu-id="eb563-147">The **Device.Capabilities** class is an attribute of all Point of Service device classes and can be used to get general information about each device.</span></span> <span data-ttu-id="eb563-148">In diesem Beispiel wird beispielsweise geprüft, ob ein Gerät Statistiken liefert. Wenn das der Fall ist, werden Statistiken für alle unterstützt Typen abgerufen.</span><span class="sxs-lookup"><span data-stu-id="eb563-148">For example, this example determines whether a device supports statistics reporting and, if it does, retrieves statistics for any types supported.</span></span>

```Csharp
try
{
    if (barcodeScanner.Capabilities.IsStatisticsReportingSupported)
    {
        Debug.WriteLine("Statistics reporting is supported");

        string[] statTypes = new string[] {""};
        IBuffer ibuffer = await barcodeScanner.RetrieveStatisticsAsync(statTypes);
    }
}
catch (Exception ex)
{
    Debug.WriteLine("EX: RetrieveStatisticsAsync() - " + ex.Message);
}
```

## <a name="claiming-a-point-of-service-device"></a><span data-ttu-id="eb563-149">Beanspruchen eines POS-Geräts</span><span class="sxs-lookup"><span data-stu-id="eb563-149">Claiming a Point of Service device</span></span>
<span data-ttu-id="eb563-150">Bevor Sie ein POS-Gerät für Ein- oder Ausgaben verwenden können, müssen Sie es „beanspruchen”. Dadurch erhält die Anwendung exklusiven Zugriff auf viele Gerätefunktionen.</span><span class="sxs-lookup"><span data-stu-id="eb563-150">Before you can use a Point of Service device for active input or output, you must claim it, granting the application exclusive access to many of its functions.</span></span> <span data-ttu-id="eb563-151">Dieser Code zeigt, wie Sie einen Strichcodescanner beanspruchen, nachdem Sie das Gerät mithilfe einer der zuvor beschriebenen Methoden gefunden haben.</span><span class="sxs-lookup"><span data-stu-id="eb563-151">This code shows how to claim a barcode scanner device, after you’ve found the device by using one of the methods described earlier.</span></span>

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

### <a name="retaining-the-device"></a><span data-ttu-id="eb563-152">Aufrechthalten des Geräteanspruchs</span><span class="sxs-lookup"><span data-stu-id="eb563-152">Retaining the device</span></span>
<span data-ttu-id="eb563-153">Wenn Sie ein POS-Gerät über eine Netzwerk- oder Bluetooth-Verbindung verwenden, möchten Sie das Gerät möglicherweise mit anderen Apps im Netzwerk teilen.</span><span class="sxs-lookup"><span data-stu-id="eb563-153">When using a Point of Service device over a network or Bluetooth connection, you may wish to share the device with other apps on the network.</span></span> <span data-ttu-id="eb563-154">(Weitere Informationen hierzu finden Sie unter [Teilen von Geräten](#sharing-a-device-between-apps).) In anderen Fällen möchten Sie vielleicht die Gerätenutzung verlängern.</span><span class="sxs-lookup"><span data-stu-id="eb563-154">(For more info about this, see [Sharing Devices](#sharing-a-device-between-apps).) In other cases, you may want to hold on to the device for prolonged use.</span></span> <span data-ttu-id="eb563-155">In diesem Beispiel wird veranschaulicht, wie der Anspruch auf einen Strichcodescanner aufrechterhalten wird, wenn eine andere App fordert, das Gerät freizugegeben.</span><span class="sxs-lookup"><span data-stu-id="eb563-155">This example shows how to retain a claimed barcode scanner after another app has requested that the device be released.</span></span>

```Csharp
claimedBarcodeScanner.ReleaseDeviceRequested += claimedBarcodeScanner_ReleaseDeviceRequested;

void claimedBarcodeScanner_ReleaseDeviceRequested(object sender, ClaimedBarcodeScanner e)
{
    e.RetainDevice();  // Retain exclusive access to the device
}
```

## <a name="input-and-output"></a><span data-ttu-id="eb563-156">Eingabe und Ausgabe</span><span class="sxs-lookup"><span data-stu-id="eb563-156">Input and output</span></span>

<span data-ttu-id="eb563-157">Nachdem Sie ein Gerät beansprucht haben, steht der Verwendung kaum noch etwas im Wege.</span><span class="sxs-lookup"><span data-stu-id="eb563-157">After you’ve claimed a device, you’re almost ready to use it.</span></span> <span data-ttu-id="eb563-158">Um Eingaben vom Gerät zu empfangen, müssen Sie es einrichten und einen Delegaten aktivieren, der die Daten übernimmt.</span><span class="sxs-lookup"><span data-stu-id="eb563-158">To receive input from the device, you must set up and enable a delegate to receive data.</span></span> <span data-ttu-id="eb563-159">Im folgenden Beispiel wird ein Strichcodescanner beansprucht, und es wird die Decodierungseigenschaft festgelegt. Dann erfolgt der Aufruf von **EnableAsync**, um decodierte Eingaben vom Gerät zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="eb563-159">In the example below, we claim a barcode scanner device, set its decode property, and then call **EnableAsync** to enable decoded input from the device.</span></span> <span data-ttu-id="eb563-160">Dieser Vorgang variiert je nach Geräteklasse. Informationen zum Einrichten eines Delegaten für andere als Strichcodegeräte finden Sie im entsprechenden [UWP-App-Beispiel](https://github.com/Microsoft/Windows-universal-samples#devices-and-sensors).</span><span class="sxs-lookup"><span data-stu-id="eb563-160">This process varies between device classes, so for guidance about how to set up a delegate for non-barcode devices, refer to the relevant [UWP app sample](https://github.com/Microsoft/Windows-universal-samples#devices-and-sensors).</span></span>

```Csharp
try
{
    claimedBarcodeScanner = await barcodeScanner.ClaimScannerAsync();
    if (claimedBarcodeScanner != null)
    {
        claimedBarcodeScanner.DataReceived += claimedBarcodeScanner_DataReceived;
        claimedBarcodeScanner.IsDecodeDataEnabled = true;
        await claimedBarcodeScanner.EnableAsync();
    }
}
catch (Exception ex)
{
    Debug.WriteLine("EX: ClaimScannerAsync() - " + ex.Message);
}


void claimedBarcodeScanner_DataReceived(ClaimedBarcodeScanner sender, BarcodeScannerDataReceivedEventArgs args)
{
    string symbologyName = BarcodeSymbologies.GetName(args.Report.ScanDataType);
    var scanDataLabelReader = DataReader.FromBuffer(args.Report.ScanDataLabel);
    string barcode = scanDataLabelReader.ReadString(args.Report.ScanDataLabel.Length);
}
```

## <a name="sharing-a-device-between-apps"></a><span data-ttu-id="eb563-161">Teilen eines Geräts zwischen Apps</span><span class="sxs-lookup"><span data-stu-id="eb563-161">Sharing a device between apps</span></span>

<span data-ttu-id="eb563-162">POS-Geräte werden häufig in Fällen verwendet, in denen mehrere Apps innerhalb eines kurzen Zeitraums darauf zugreifen müssen.</span><span class="sxs-lookup"><span data-stu-id="eb563-162">Point of Service devices are often used in cases where more than one app will need to access them in a brief period.</span></span>  <span data-ttu-id="eb563-163">Ein Gerät kann geteilt werden, wenn es mit mehreren Apps entweder lokal verbunden ist (über USB- oder eine andere Kabelverbindung) oder über ein Bluetooth- oder IP-Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="eb563-163">A device can be shared when connected to multiple apps locally (USB or other wired connection), or through a Bluetooth or IP network.</span></span> <span data-ttu-id="eb563-164">Je nach den Anforderungen der einzelnen Apps muss ein Prozess möglicherweise seinen Anspruch auf das Gerät aufgeben.</span><span class="sxs-lookup"><span data-stu-id="eb563-164">Depending on the needs of each app, one process may need to dispose of its claim on the device.</span></span> <span data-ttu-id="eb563-165">Dieser Code gibt den Anspruch auf den Strichcodescanner auf, damit er von einer anderen App beansprucht und verwendet werden kann</span><span class="sxs-lookup"><span data-stu-id="eb563-165">This code disposes of our claimed barcode scanner device, allowing other apps to claim and use it.</span></span>

```Csharp
if (claimedBarcodeScanner != null)
{
    claimedBarcodeScanner.Dispose();
    claimedBarcodeScanner = null;
}
```

> [!NOTE]
> <span data-ttu-id="eb563-166">Sowohl die beanspruchten als auch die nicht beanspruchten POS-Geräteklassen implementieren die [IClosable-Schnittstelle](https://docs.microsoft.com/uwp/api/windows.foundation.iclosable).</span><span class="sxs-lookup"><span data-stu-id="eb563-166">Both the claimed and unclaimed Point of Service device classes implement the [IClosable interface](https://docs.microsoft.com/uwp/api/windows.foundation.iclosable).</span></span> <span data-ttu-id="eb563-167">Wenn ein Gerät über ein Netzwerk oder Bluetooth mit einer App verbunden ist, müssen sowohl die beanspruchten als auch die nicht beanspruchten Objekte freigegeben werden, bevor eine andere App eine Verbindung herstellen kann.</span><span class="sxs-lookup"><span data-stu-id="eb563-167">If a device is connected to an app via network or Bluetooth, both the claimed and unclaimed objects must be disposed of before another app can connect.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb563-168">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="eb563-168">See also</span></span>
+ [<span data-ttu-id="eb563-169">Beispiel für Strichcodescanner</span><span class="sxs-lookup"><span data-stu-id="eb563-169">Barcode scanner sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BarcodeScanner)
+ [<span data-ttu-id="eb563-170">Beispiel für Kassenschubladen</span><span class="sxs-lookup"><span data-stu-id="eb563-170">Cash drawer sample</span></span>]( https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CashDrawer)
+ [<span data-ttu-id="eb563-171">Beispiel für Zeilenanzeigen</span><span class="sxs-lookup"><span data-stu-id="eb563-171">Line display sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/LineDisplay)
+ [<span data-ttu-id="eb563-172">Beispiel für Magnetstreifenleser</span><span class="sxs-lookup"><span data-stu-id="eb563-172">Magnetic stripe reader sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MagneticStripeReader)
+ [<span data-ttu-id="eb563-173">Beispiel für POS-Drucker</span><span class="sxs-lookup"><span data-stu-id="eb563-173">POSPrinter sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/PosPrinter)

