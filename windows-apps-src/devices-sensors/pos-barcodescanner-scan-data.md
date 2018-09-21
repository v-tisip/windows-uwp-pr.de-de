---
author: eliotcowley
title: Beziehen und Barcodedaten verstehen
description: Informationen Sie zum Sammeln und Interpretieren von Barcode-Daten, die Sie scannen.
ms.author: elcowle
ms.date: 08/29/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Point of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: 0992ea54092063ba53f23871599905e58f1b456e
ms.sourcegitcommit: 5dda01da4702cbc49c799c750efe0e430b699502
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/21/2018
ms.locfileid: "4114518"
---
# <a name="obtain-and-understand-barcode-data"></a><span data-ttu-id="02d3c-104">Beziehen und Barcodedaten verstehen</span><span class="sxs-lookup"><span data-stu-id="02d3c-104">Obtain and understand barcode data</span></span>

<span data-ttu-id="02d3c-105">Wenn der Barcodescanner eingerichtet haben, benötigen Sie natürlich eine Möglichkeit zum Verständnis der Daten, die Sie scannen.</span><span class="sxs-lookup"><span data-stu-id="02d3c-105">Once you've set up your barcode scanner, you of course need a way of understanding the data that you scan.</span></span> <span data-ttu-id="02d3c-106">Beim Scannen von Barcodes wird das [DataReceived](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.datareceived) -Ereignis ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="02d3c-106">When you scan a barcode, the [DataReceived](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.datareceived) event is raised.</span></span> <span data-ttu-id="02d3c-107">Die [ClaimedBarcodeScanner](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner) sollte dieses Ereignis abonnieren.</span><span class="sxs-lookup"><span data-stu-id="02d3c-107">The [ClaimedBarcodeScanner](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner) should subscribe to this event.</span></span> <span data-ttu-id="02d3c-108">Das **DataReceived** -Ereignis übergibt ein [BarcodeScannerDataReceivedEventArgs](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerdatareceivedeventargs) -Objekt, das mit die Barcode-Daten zugreifen.</span><span class="sxs-lookup"><span data-stu-id="02d3c-108">The **DataReceived** event passes a [BarcodeScannerDataReceivedEventArgs](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerdatareceivedeventargs) object, which you can use to access the barcode data.</span></span>

## <a name="subscribe-to-the-datareceived-event"></a><span data-ttu-id="02d3c-109">Das DataReceived-Ereignis abonnieren</span><span class="sxs-lookup"><span data-stu-id="02d3c-109">Subscribe to the DataReceived event</span></span>

<span data-ttu-id="02d3c-110">Haben Sie eine **ClaimedBarcodeScanner**haben Sie das **DataReceived** -Ereignis abonnieren:</span><span class="sxs-lookup"><span data-stu-id="02d3c-110">Once you have a **ClaimedBarcodeScanner**, have it subscribe to the **DataReceived** event:</span></span>

```cs
claimedBarcodeScanner.DataReceived += ClaimedBarcodeScanner_DataReceived;
```

<span data-ttu-id="02d3c-111">Der Ereignishandler wird **ClaimedBarcodeScanner** und ein **BarcodeScannerDataReceivedEventArgs** -Objekt übergeben.</span><span class="sxs-lookup"><span data-stu-id="02d3c-111">The event handler will be passed the **ClaimedBarcodeScanner** and a **BarcodeScannerDataReceivedEventArgs** object.</span></span> <span data-ttu-id="02d3c-112">Sie können dieses Objekt [Bericht](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerdatareceivedeventargs.report#Windows_Devices_PointOfService_BarcodeScannerDataReceivedEventArgs_Report) vom Typ [BarcodeScannerReport](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport), Barcode-Daten zugreifen.</span><span class="sxs-lookup"><span data-stu-id="02d3c-112">You can access the barcode data through this object's [Report](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerdatareceivedeventargs.report#Windows_Devices_PointOfService_BarcodeScannerDataReceivedEventArgs_Report) property, which is of type [BarcodeScannerReport](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport).</span></span>

```cs
private async void ClaimedBarcodeScanner_DataReceived(ClaimedBarcodeScanner sender, BarcodeScannerDataReceivedEventArgs args)
{
    // Parse the data
}
```

## <a name="get-the-data"></a><span data-ttu-id="02d3c-113">Daten abrufen</span><span class="sxs-lookup"><span data-stu-id="02d3c-113">Get the data</span></span>

<span data-ttu-id="02d3c-114">Haben Sie **BarcodeScannerReport**, können Zugriff auf und die Barcodedaten analysieren.</span><span class="sxs-lookup"><span data-stu-id="02d3c-114">Once you have the **BarcodeScannerReport**, you can access and parse the barcode data.</span></span> <span data-ttu-id="02d3c-115">**BarcodeScannerReport** hat drei Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="02d3c-115">**BarcodeScannerReport** has three properties:</span></span>

* <span data-ttu-id="02d3c-116">[ScanData](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport.scandata): der vollständige raw Barcodedaten.</span><span class="sxs-lookup"><span data-stu-id="02d3c-116">[ScanData](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport.scandata): The full, raw barcode data.</span></span>
* <span data-ttu-id="02d3c-117">[ScanDataLabel](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport.scandatalabel): die decodierten Strichcode-Etikett, das keinen Header-Prüfsumme und sonstige Informationen enthält.</span><span class="sxs-lookup"><span data-stu-id="02d3c-117">[ScanDataLabel](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport.scandatalabel): The decoded barcode label, which does not include the header, checksum, and other miscellaneous information.</span></span>
* <span data-ttu-id="02d3c-118">[ScanDataType](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport.scandatatype): die decodierten Barcodetyp Bezeichnung.</span><span class="sxs-lookup"><span data-stu-id="02d3c-118">[ScanDataType](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport.scandatatype): The decoded barcode label type.</span></span> <span data-ttu-id="02d3c-119">Mögliche Werte sind in der [BarcodeSymbologies](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies) -Klasse definiert.</span><span class="sxs-lookup"><span data-stu-id="02d3c-119">Possible values are defined in the [BarcodeSymbologies](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies) class.</span></span>

<span data-ttu-id="02d3c-120">Sie **ScanDataLabel** oder **ScanDataType**zugreifen möchten, müssen Sie [IsDecodeDataEnabled](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.isdecodedataenabled#Windows_Devices_PointOfService_ClaimedBarcodeScanner_IsDecodeDataEnabled) zuerst auf **true**festlegen.</span><span class="sxs-lookup"><span data-stu-id="02d3c-120">If you want to access either **ScanDataLabel** or **ScanDataType**, you must first set [IsDecodeDataEnabled](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.isdecodedataenabled#Windows_Devices_PointOfService_ClaimedBarcodeScanner_IsDecodeDataEnabled) to **true**.</span></span>

```cs
claimedBarcodeScanner.IsDecodeDataEnabled = true;
```

### <a name="get-the-scan-data-type"></a><span data-ttu-id="02d3c-121">Rufen Sie den Scan-Datentyp ab</span><span class="sxs-lookup"><span data-stu-id="02d3c-121">Get the scan data type</span></span>

<span data-ttu-id="02d3c-122">Etikettentyp decodierten Barcode ist ganz einfach&mdash;rufen wir einfach [GetName](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies.getname) auf **ScanDataType**.</span><span class="sxs-lookup"><span data-stu-id="02d3c-122">Getting the decoded barcode label type is fairly trivial&mdash;we simply call [GetName](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies.getname) on **ScanDataType**.</span></span>

```cs
private string GetSymbology(BarcodeScannerDataReceivedEventArgs args)
{
    return BarcodeSymbologies.GetName(args.Report.ScanDataType);
}
```

### <a name="get-the-scan-data-label"></a><span data-ttu-id="02d3c-123">Die Beschriftung Scan erhalten</span><span class="sxs-lookup"><span data-stu-id="02d3c-123">Get the scan data label</span></span>

<span data-ttu-id="02d3c-124">Zu decodierten Strichcode-Etikett gibt es einiges zu beachten haben.</span><span class="sxs-lookup"><span data-stu-id="02d3c-124">To get the decoded barcode label, there are a few things you have to be aware of.</span></span> <span data-ttu-id="02d3c-125">Nur bestimmte Datentypen enthalten codierten Text, sodass Sie zuerst die Symbologie in eine Zeichenfolge konvertiert werden kann und den Puffer bekommen wir aus **ScanDataLabel** eine codierte UTF-8-Zeichenfolge zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="02d3c-125">Only certain data types contain encoded text, so you should first check if the symbology can be converted to a string, and then convert the buffer we get from **ScanDataLabel** to an encoded UTF-8 string.</span></span>

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

### <a name="get-the-raw-scan-data"></a><span data-ttu-id="02d3c-126">Raw Scan Daten</span><span class="sxs-lookup"><span data-stu-id="02d3c-126">Get the raw scan data</span></span>

<span data-ttu-id="02d3c-127">Zu vollständigen konvertieren Rohdaten aus den Barcode wir einfach den Puffer erhalten wir von **ScanData** in eine Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="02d3c-127">To get the full, raw data from the barcode, we simply convert the buffer we get from **ScanData** into a string.</span></span>

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

<span data-ttu-id="02d3c-128">Diese Daten sind im Allgemeinen das Format vom Scanner geliefert.</span><span class="sxs-lookup"><span data-stu-id="02d3c-128">These data are, in general, in the format as delivered from the scanner.</span></span> <span data-ttu-id="02d3c-129">Header und Trailer Informationen werden entfernt, jedoch enthalten nützliche Informationen für eine Anwendung und Scanner spezifisch sein.</span><span class="sxs-lookup"><span data-stu-id="02d3c-129">Message header and trailer information are removed, however, since they do not contain useful information for an application and are likely to be scanner-specific.</span></span>

<span data-ttu-id="02d3c-130">Allgemeine Headerinformationen ist ein Präfix (z. B. ein STX-Zeichen).</span><span class="sxs-lookup"><span data-stu-id="02d3c-130">Common header information is a prefix character (such as an STX character).</span></span> <span data-ttu-id="02d3c-131">Anhänger Informationen ist ein Abschlusszeichen (z. B. ein Zeichen ETX oder CR) und ein Blockzeichen Kontrollkästchen einen der Scanner generiert wird.</span><span class="sxs-lookup"><span data-stu-id="02d3c-131">Common trailer information is a terminator character (such as an ETX or CR character) and a block check character if one is generated by the scanner.</span></span>

<span data-ttu-id="02d3c-132">Diese Eigenschaft sollte Symbologie Zeichen, wenn der Scanner zurückgegeben (z. B. **ein** für UPC-A).</span><span class="sxs-lookup"><span data-stu-id="02d3c-132">This property should include a symbology character if one is returned by the scanner (for example, an **A** for UPC-A).</span></span> <span data-ttu-id="02d3c-133">Es sollte auch Prüfziffern in der Bezeichnung vorhanden sind und der Scanner zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="02d3c-133">It should also include check digits if they are present in the label and returned by the scanner.</span></span> <span data-ttu-id="02d3c-134">(Beachten Sie, dass Symbologie Zeichen und Prüfziffern können oder nicht vorhanden sein darf, die Scanner-Konfiguration abhängig.</span><span class="sxs-lookup"><span data-stu-id="02d3c-134">(Note that both symbology characters and check digits may or may not be present, depending upon the scanner configuration.</span></span> <span data-ttu-id="02d3c-135">Der Scanner wird zurücksenden, wenn vorhanden, aber nicht erstellen oder berechnen lassen, wenn sie fehlen.)</span><span class="sxs-lookup"><span data-stu-id="02d3c-135">The scanner will return them if present, but will not generate or calculate them if they are absent.)</span></span>

<span data-ttu-id="02d3c-136">Einige waren möglicherweise zusätzliche Barcode markiert.</span><span class="sxs-lookup"><span data-stu-id="02d3c-136">Some merchandise may be marked with a supplemental barcode.</span></span> <span data-ttu-id="02d3c-137">Barcode befindet sich normalerweise rechts neben den wichtigsten Barcode und eine weitere zwei oder fünf Zeichen von Informationen aus.</span><span class="sxs-lookup"><span data-stu-id="02d3c-137">This barcode is typically placed to the right of the main barcode, and consists of an additional two or five characters of information.</span></span> <span data-ttu-id="02d3c-138">Liest der Scanner waren Haupt- und zusätzliche Barcodes enthält zusätzlichen Zeichen sind die wichtigsten Zeichen angehängt und das Ergebnis als eine Bezeichnung an die Anwendung übermittelt.</span><span class="sxs-lookup"><span data-stu-id="02d3c-138">If the scanner reads merchandise that contains both main and supplemental barcodes, the supplemental characters are appended to the main characters, and the result is delivered to the application as one label.</span></span> <span data-ttu-id="02d3c-139">(Beachten Sie, dass ein Scanner eine Konfiguration unterstützt, die aktiviert oder deaktiviert das Lesen des Codes zusätzliche.)</span><span class="sxs-lookup"><span data-stu-id="02d3c-139">(Note that a scanner may support a configuration that enables or disables the reading of supplemental codes.)</span></span>

<span data-ttu-id="02d3c-140">Einige waren möglicherweise mehrere Bezeichnungsfelder bezeichnet *mit mehreren Symbolen* oder *gestuften Etiketten*markiert.</span><span class="sxs-lookup"><span data-stu-id="02d3c-140">Some merchandise may be marked with multiple labels, sometimes called *multisymbol labels* or *tiered labels*.</span></span> <span data-ttu-id="02d3c-141">Diese Barcodes werden in der Regel vertikal angeordnet und von demselben oder einem anderen Symbologie möglicherweise.</span><span class="sxs-lookup"><span data-stu-id="02d3c-141">These barcodes are typically arranged vertically, and may be of the same or different symbology.</span></span> <span data-ttu-id="02d3c-142">Der Scanner waren liest, die mehrere Etiketten enthält, wird jeder Barcode Anwendung als separate Bezeichnung übermittelt.</span><span class="sxs-lookup"><span data-stu-id="02d3c-142">If the scanner reads merchandise that contains multiple labels, each barcode is delivered to the application as a separate label.</span></span> <span data-ttu-id="02d3c-143">Dies ist aufgrund des aktuellen Mangels von Standardisierung dieser Barcode-Typen.</span><span class="sxs-lookup"><span data-stu-id="02d3c-143">This is necessary due to the current lack of standardization of these barcode types.</span></span> <span data-ttu-id="02d3c-144">Eine kann nicht alle Varianten basierend auf den einzelnen Barcode-Daten bestimmt.</span><span class="sxs-lookup"><span data-stu-id="02d3c-144">One is not able to determine all variations based upon the individual barcode data.</span></span> <span data-ttu-id="02d3c-145">Daher muss die Anwendung bestimmen, wenn mehrere Label Barcode bei den zurückgegebenen Daten gelesen wurden.</span><span class="sxs-lookup"><span data-stu-id="02d3c-145">Therefore, the application will need to determine when a multiple label barcode has been read based upon the data returned.</span></span> <span data-ttu-id="02d3c-146">(Beachten Sie, dass ein Scanner unterstützen mehrere Etiketten lesen.)</span><span class="sxs-lookup"><span data-stu-id="02d3c-146">(Note that a scanner may or may not support reading of multiple labels.)</span></span>

<span data-ttu-id="02d3c-147">Dieser Wert wird vor einem **DataReceived** zu der Anwendung festgelegt.</span><span class="sxs-lookup"><span data-stu-id="02d3c-147">This value is set prior to a **DataReceived** event being raised to the application.</span></span>

[!INCLUDE [feedback](./includes/pos-feedback.md)]

## <a name="see-also"></a><span data-ttu-id="02d3c-148">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="02d3c-148">See also</span></span>
* [<span data-ttu-id="02d3c-149">Strichcodescanner</span><span class="sxs-lookup"><span data-stu-id="02d3c-149">Barcode scanner</span></span>](pos-barcodescanner.md)
* [<span data-ttu-id="02d3c-150">ClaimedBarcodeScanner-Klasse</span><span class="sxs-lookup"><span data-stu-id="02d3c-150">ClaimedBarcodeScanner Class</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies.getname)
* [<span data-ttu-id="02d3c-151">BarcodeScannerDataReceivedEventArgs-Klasse</span><span class="sxs-lookup"><span data-stu-id="02d3c-151">BarcodeScannerDataReceivedEventArgs Class</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerdatareceivedeventargs)
* [<span data-ttu-id="02d3c-152">BarcodeScannerReport-Klasse</span><span class="sxs-lookup"><span data-stu-id="02d3c-152">BarcodeScannerReport Class</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport)
* [<span data-ttu-id="02d3c-153">BarcodeSymbologies-Klasse</span><span class="sxs-lookup"><span data-stu-id="02d3c-153">BarcodeSymbologies Class</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies)