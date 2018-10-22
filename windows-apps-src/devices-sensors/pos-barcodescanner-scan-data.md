---
author: eliotcowley
title: Abrufen und Verstehen von Strichcode-Daten
description: Erfahren Sie, wie zum Erhalt und der Interpretation der Strichcode-Daten, die Sie scannen.
ms.author: elcowle
ms.date: 08/29/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Point of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: 0992ea54092063ba53f23871599905e58f1b456e
ms.sourcegitcommit: c4d3115348c8b54fcc92aae8e18fdabc3deb301d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2018
ms.locfileid: "5395635"
---
# <a name="obtain-and-understand-barcode-data"></a><span data-ttu-id="0dd50-104">Abrufen und Verstehen von Strichcode-Daten</span><span class="sxs-lookup"><span data-stu-id="0dd50-104">Obtain and understand barcode data</span></span>

<span data-ttu-id="0dd50-105">Nachdem Sie Ihr Strichcodescanner eingerichtet haben, benötigen Sie natürlich eine Möglichkeit, Verständnis der Daten, die Sie scannen.</span><span class="sxs-lookup"><span data-stu-id="0dd50-105">Once you've set up your barcode scanner, you of course need a way of understanding the data that you scan.</span></span> <span data-ttu-id="0dd50-106">Wenn Sie einen Strichcode scannen, wird das [DataReceived](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.datareceived) -Ereignis ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="0dd50-106">When you scan a barcode, the [DataReceived](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.datareceived) event is raised.</span></span> <span data-ttu-id="0dd50-107">Die [ClaimedBarcodeScanner](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner) sollte dieses Ereignis abonnieren.</span><span class="sxs-lookup"><span data-stu-id="0dd50-107">The [ClaimedBarcodeScanner](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner) should subscribe to this event.</span></span> <span data-ttu-id="0dd50-108">Das **DataReceived** Ereignis übergibt ein [BarcodeScannerDataReceivedEventArgs](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerdatareceivedeventargs) -Objekt, das Sie verwenden können, um die Strichcode-Daten zugreifen.</span><span class="sxs-lookup"><span data-stu-id="0dd50-108">The **DataReceived** event passes a [BarcodeScannerDataReceivedEventArgs](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerdatareceivedeventargs) object, which you can use to access the barcode data.</span></span>

## <a name="subscribe-to-the-datareceived-event"></a><span data-ttu-id="0dd50-109">Abonnieren Sie das DataReceived-Ereignis</span><span class="sxs-lookup"><span data-stu-id="0dd50-109">Subscribe to the DataReceived event</span></span>

<span data-ttu-id="0dd50-110">Wenn Sie eine **ClaimedBarcodeScanner**haben, haben sie die **DataReceived** Ereignis abonnieren:</span><span class="sxs-lookup"><span data-stu-id="0dd50-110">Once you have a **ClaimedBarcodeScanner**, have it subscribe to the **DataReceived** event:</span></span>

```cs
claimedBarcodeScanner.DataReceived += ClaimedBarcodeScanner_DataReceived;
```

<span data-ttu-id="0dd50-111">Der Ereignishandler wird die **ClaimedBarcodeScanner** und ein Objekt **BarcodeScannerDataReceivedEventArgs** übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="0dd50-111">The event handler will be passed the **ClaimedBarcodeScanner** and a **BarcodeScannerDataReceivedEventArgs** object.</span></span> <span data-ttu-id="0dd50-112">Sie können die Strichcode-Daten über dieses Objekt [Bericht](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerdatareceivedeventargs.report#Windows_Devices_PointOfService_BarcodeScannerDataReceivedEventArgs_Report) Eigenschaft Typ [BarcodeScannerReport vom](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport)zugreifen.</span><span class="sxs-lookup"><span data-stu-id="0dd50-112">You can access the barcode data through this object's [Report](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerdatareceivedeventargs.report#Windows_Devices_PointOfService_BarcodeScannerDataReceivedEventArgs_Report) property, which is of type [BarcodeScannerReport](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport).</span></span>

```cs
private async void ClaimedBarcodeScanner_DataReceived(ClaimedBarcodeScanner sender, BarcodeScannerDataReceivedEventArgs args)
{
    // Parse the data
}
```

## <a name="get-the-data"></a><span data-ttu-id="0dd50-113">Abrufen der Daten</span><span class="sxs-lookup"><span data-stu-id="0dd50-113">Get the data</span></span>

<span data-ttu-id="0dd50-114">Wenn Sie die **BarcodeScannerReport**haben, können Sie Zugriff auf und Analysieren der Strichcode-Daten.</span><span class="sxs-lookup"><span data-stu-id="0dd50-114">Once you have the **BarcodeScannerReport**, you can access and parse the barcode data.</span></span> <span data-ttu-id="0dd50-115">**BarcodeScannerReport** verfügt über drei Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="0dd50-115">**BarcodeScannerReport** has three properties:</span></span>

* <span data-ttu-id="0dd50-116">[ScanData](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport.scandata): die vollständige, unformatierte Strichcode-Daten.</span><span class="sxs-lookup"><span data-stu-id="0dd50-116">[ScanData](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport.scandata): The full, raw barcode data.</span></span>
* <span data-ttu-id="0dd50-117">[ScanDataLabel](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport.scandatalabel): die decodierten Barcode-Bezeichnung, die nicht in der Kopfzeile, Prüfsumme und andere Informationen enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="0dd50-117">[ScanDataLabel](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport.scandatalabel): The decoded barcode label, which does not include the header, checksum, and other miscellaneous information.</span></span>
* <span data-ttu-id="0dd50-118">[ScanDataType](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport.scandatatype): der decodierten Barcode Label-Typ.</span><span class="sxs-lookup"><span data-stu-id="0dd50-118">[ScanDataType](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport.scandatatype): The decoded barcode label type.</span></span> <span data-ttu-id="0dd50-119">Mögliche Werte sind in der [BarcodeSymbologies](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies) -Klasse definiert.</span><span class="sxs-lookup"><span data-stu-id="0dd50-119">Possible values are defined in the [BarcodeSymbologies](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies) class.</span></span>

<span data-ttu-id="0dd50-120">Wenn Sie **ScanDataLabel** oder **ScanDataType**zugreifen möchten, müssen Sie zuerst [IsDecodeDataEnabled](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.isdecodedataenabled#Windows_Devices_PointOfService_ClaimedBarcodeScanner_IsDecodeDataEnabled) auf **"true"** festlegen.</span><span class="sxs-lookup"><span data-stu-id="0dd50-120">If you want to access either **ScanDataLabel** or **ScanDataType**, you must first set [IsDecodeDataEnabled](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.isdecodedataenabled#Windows_Devices_PointOfService_ClaimedBarcodeScanner_IsDecodeDataEnabled) to **true**.</span></span>

```cs
claimedBarcodeScanner.IsDecodeDataEnabled = true;
```

### <a name="get-the-scan-data-type"></a><span data-ttu-id="0dd50-121">Rufen Sie den Scan-Datentyp ab</span><span class="sxs-lookup"><span data-stu-id="0dd50-121">Get the scan data type</span></span>

<span data-ttu-id="0dd50-122">Abrufen des decodierten Barcode Beschriftung Typs ist ganz einfach&mdash;rufen wir einfach [GetName](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies.getname) auf **ScanDataType**.</span><span class="sxs-lookup"><span data-stu-id="0dd50-122">Getting the decoded barcode label type is fairly trivial&mdash;we simply call [GetName](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies.getname) on **ScanDataType**.</span></span>

```cs
private string GetSymbology(BarcodeScannerDataReceivedEventArgs args)
{
    return BarcodeSymbologies.GetName(args.Report.ScanDataType);
}
```

### <a name="get-the-scan-data-label"></a><span data-ttu-id="0dd50-123">Rufen Sie die Beschriftung scan</span><span class="sxs-lookup"><span data-stu-id="0dd50-123">Get the scan data label</span></span>

<span data-ttu-id="0dd50-124">Um die decodierten Barcode-Bezeichnung zu erhalten, gibt es einige Dinge zu beachten.</span><span class="sxs-lookup"><span data-stu-id="0dd50-124">To get the decoded barcode label, there are a few things you have to be aware of.</span></span> <span data-ttu-id="0dd50-125">Nur bestimmte Datentypen enthalten codierten Text, damit Sie zuerst suchen soll, wenn die Symbologie in eine Zeichenfolge konvertiert werden kann, und konvertieren Sie anschließend den Puffer, die wir aus **ScanDataLabel** auf eine codierten UTF-8-Zeichenfolge erhalten.</span><span class="sxs-lookup"><span data-stu-id="0dd50-125">Only certain data types contain encoded text, so you should first check if the symbology can be converted to a string, and then convert the buffer we get from **ScanDataLabel** to an encoded UTF-8 string.</span></span>

```cs
private string GetDataLabel(BarcodeScannerDataReceivedEventArgs args)
{
    uint scanDataType = args.Report.ScanDataType;

    // Only certain data types contain encoded text.
    // To keep this simple, we'll just decode a few of them.
    if (args.Report.ScanDataLabel == null)
    {
        return "No data";
    }

    // This is not an exhaustive list of symbologies that can be converted to a string.
    else if (scanDataType == BarcodeSymbologies.Upca ||
        scanDataType == BarcodeSymbologies.UpcaAdd2 ||
        scanDataType == BarcodeSymbologies.UpcaAdd5 ||
        scanDataType == BarcodeSymbologies.Upce ||
        scanDataType == BarcodeSymbologies.UpceAdd2 ||
        scanDataType == BarcodeSymbologies.UpceAdd5 ||
        scanDataType == BarcodeSymbologies.Ean8 ||
        scanDataType == BarcodeSymbologies.TfStd)
    {
        // The UPC, EAN8, and 2 of 5 families encode the digits 0..9
        // which are then sent to the app in a UTF8 string (like "01234").
        return CryptographicBuffer.ConvertBinaryToString(BinaryStringEncoding.Utf8, args.Report.ScanDataLabel);
    }

    // Some other symbologies (typically 2-D symbologies) contain binary data that
    // should not be converted to text.
    else
    {
        return "Decoded data unavailable.";
    }
}
```

### <a name="get-the-raw-scan-data"></a><span data-ttu-id="0dd50-126">Abrufen der unformatierten Scan-Daten</span><span class="sxs-lookup"><span data-stu-id="0dd50-126">Get the raw scan data</span></span>

<span data-ttu-id="0dd50-127">Um die vollständige zu erhalten, konvertieren Sie unformatierte Daten aus der Strichcode wir einfach den Puffer, die, den wir in einer Zeichenfolge aus **ScanData** erhalten.</span><span class="sxs-lookup"><span data-stu-id="0dd50-127">To get the full, raw data from the barcode, we simply convert the buffer we get from **ScanData** into a string.</span></span>

```cs
private string GetRawData(BarcodeScannerDataReceivedEventArgs args)
{
    // Get the full, raw barcode data.
    if (args.Report.ScanData == null)
    {
        return "No data";
    }

    // Just to show that we have the raw data, we'll print the value of the bytes.
    else
    {
        return CryptographicBuffer.ConvertBinaryToString(BinaryStringEncoding.Utf8, args.Report.ScanData);
    }
}
```

<span data-ttu-id="0dd50-128">Diese Daten werden in der Regel im Format wie aus dem Scanner übermittelt.</span><span class="sxs-lookup"><span data-stu-id="0dd50-128">These data are, in general, in the format as delivered from the scanner.</span></span> <span data-ttu-id="0dd50-129">Header und Trailer Informationen werden entfernt, jedoch, da diese enthalten keine nützliche Informationen für eine Anwendung und Stichwörtern Scanner für die jeweilige.</span><span class="sxs-lookup"><span data-stu-id="0dd50-129">Message header and trailer information are removed, however, since they do not contain useful information for an application and are likely to be scanner-specific.</span></span>

<span data-ttu-id="0dd50-130">Allgemeine Headerinformationen ist ein Präfix (z. B. ein STX Zeichen).</span><span class="sxs-lookup"><span data-stu-id="0dd50-130">Common header information is a prefix character (such as an STX character).</span></span> <span data-ttu-id="0dd50-131">Allgemeine Trailer-Informationen sind ein Abschluss-Zeichen (z. B. ein ETX oder CR Zeichen) und ein Block Kontrollkästchen, wenn eine von der Scanner generiert wird.</span><span class="sxs-lookup"><span data-stu-id="0dd50-131">Common trailer information is a terminator character (such as an ETX or CR character) and a block check character if one is generated by the scanner.</span></span>

<span data-ttu-id="0dd50-132">Diese Eigenschaft sollte eine Symbologie Zeichen enthalten, wenn eine der Scanner zurückgegeben wird (z. B. ein **A** für UPC A).</span><span class="sxs-lookup"><span data-stu-id="0dd50-132">This property should include a symbology character if one is returned by the scanner (for example, an **A** for UPC-A).</span></span> <span data-ttu-id="0dd50-133">Es sollte auch Kontrollkästchen Ziffern enthalten, wenn sie in der Beschriftung vorhanden sind und von der Scanner zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="0dd50-133">It should also include check digits if they are present in the label and returned by the scanner.</span></span> <span data-ttu-id="0dd50-134">(Beachten Sie, dass sowohl Symbologie Zeichen Kontrollkästchen Ziffern und können möglicherweise nicht vorhanden, je nach der Konfiguration des Scanner.</span><span class="sxs-lookup"><span data-stu-id="0dd50-134">(Note that both symbology characters and check digits may or may not be present, depending upon the scanner configuration.</span></span> <span data-ttu-id="0dd50-135">Der Scanner wird zurücksenden, wenn vorhanden, wird jedoch nicht zu generieren oder berechnen lassen, wenn er nicht vorhanden sind.)</span><span class="sxs-lookup"><span data-stu-id="0dd50-135">The scanner will return them if present, but will not generate or calculate them if they are absent.)</span></span>

<span data-ttu-id="0dd50-136">Einige Waren kann mit einem ergänzende Strichcode gekennzeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="0dd50-136">Some merchandise may be marked with a supplemental barcode.</span></span> <span data-ttu-id="0dd50-137">Diese Barcode wird in der Regel rechts neben den wichtigsten Strichcode platziert und besteht aus einer zusätzlichen 2 oder 5 Zeichen von Informationen.</span><span class="sxs-lookup"><span data-stu-id="0dd50-137">This barcode is typically placed to the right of the main barcode, and consists of an additional two or five characters of information.</span></span> <span data-ttu-id="0dd50-138">Lautet der Scanner waren, die Haupt- und ergänzende Barcodes enthält, die zusätzlichen Zeichen werden an den hauptpersonen angehängt und das Ergebnis wird an die Anwendung als eine Beschriftung übermittelt.</span><span class="sxs-lookup"><span data-stu-id="0dd50-138">If the scanner reads merchandise that contains both main and supplemental barcodes, the supplemental characters are appended to the main characters, and the result is delivered to the application as one label.</span></span> <span data-ttu-id="0dd50-139">(Beachten Sie, dass ein Scanner eine Konfiguration unterstützen kann, die aktiviert oder deaktiviert das Lesen von ergänzende Codes.)</span><span class="sxs-lookup"><span data-stu-id="0dd50-139">(Note that a scanner may support a configuration that enables or disables the reading of supplemental codes.)</span></span>

<span data-ttu-id="0dd50-140">Einige waren möglicherweise mit mehreren Beschriftungen, auch *mit mehreren Symbolen Beschriftungen* oder *mehrstufigen Beschriftungen*genannt gekennzeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="0dd50-140">Some merchandise may be marked with multiple labels, sometimes called *multisymbol labels* or *tiered labels*.</span></span> <span data-ttu-id="0dd50-141">Diese Barcodes werden in der Regel vertikal angeordnet, und von den gleichen oder unterschiedliche Symbologie sein.</span><span class="sxs-lookup"><span data-stu-id="0dd50-141">These barcodes are typically arranged vertically, and may be of the same or different symbology.</span></span> <span data-ttu-id="0dd50-142">Wenn der Scanner waren, die mehrere Beschriftungen enthält liest, wird jede Barcode an die Anwendung als separate Bezeichnung übermittelt.</span><span class="sxs-lookup"><span data-stu-id="0dd50-142">If the scanner reads merchandise that contains multiple labels, each barcode is delivered to the application as a separate label.</span></span> <span data-ttu-id="0dd50-143">Dies ist aufgrund der aktuellen Mangel an Standardisierung dieser Typen für Barcode erforderlich.</span><span class="sxs-lookup"><span data-stu-id="0dd50-143">This is necessary due to the current lack of standardization of these barcode types.</span></span> <span data-ttu-id="0dd50-144">Eine kann nicht für alle Varianten basierend auf den einzelnen Barcode-Daten zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="0dd50-144">One is not able to determine all variations based upon the individual barcode data.</span></span> <span data-ttu-id="0dd50-145">Aus diesem Grund wird die Anwendung muss, um zu bestimmen, wann ein mehrere Beschriftung Strichcode basierend auf der zurückgegebenen Daten gelesen wurde.</span><span class="sxs-lookup"><span data-stu-id="0dd50-145">Therefore, the application will need to determine when a multiple label barcode has been read based upon the data returned.</span></span> <span data-ttu-id="0dd50-146">(Beachten Sie, dass ein Scanner kann oder möglicherweise nicht lesen von mehreren Beschriftungen unterstützen.)</span><span class="sxs-lookup"><span data-stu-id="0dd50-146">(Note that a scanner may or may not support reading of multiple labels.)</span></span>

<span data-ttu-id="0dd50-147">Dieser Wert wird vor einem **DataReceived** -Ereignis ausgelöst werden, um die Anwendung festgelegt.</span><span class="sxs-lookup"><span data-stu-id="0dd50-147">This value is set prior to a **DataReceived** event being raised to the application.</span></span>

[!INCLUDE [feedback](./includes/pos-feedback.md)]

## <a name="see-also"></a><span data-ttu-id="0dd50-148">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="0dd50-148">See also</span></span>
* [<span data-ttu-id="0dd50-149">Strichcodescanner</span><span class="sxs-lookup"><span data-stu-id="0dd50-149">Barcode scanner</span></span>](pos-barcodescanner.md)
* [<span data-ttu-id="0dd50-150">ClaimedBarcodeScanner-Klasse</span><span class="sxs-lookup"><span data-stu-id="0dd50-150">ClaimedBarcodeScanner Class</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies.getname)
* [<span data-ttu-id="0dd50-151">BarcodeScannerDataReceivedEventArgs-Klasse</span><span class="sxs-lookup"><span data-stu-id="0dd50-151">BarcodeScannerDataReceivedEventArgs Class</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerdatareceivedeventargs)
* [<span data-ttu-id="0dd50-152">BarcodeScannerReport-Klasse</span><span class="sxs-lookup"><span data-stu-id="0dd50-152">BarcodeScannerReport Class</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport)
* [<span data-ttu-id="0dd50-153">BarcodeSymbologies-Klasse</span><span class="sxs-lookup"><span data-stu-id="0dd50-153">BarcodeSymbologies Class</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies)