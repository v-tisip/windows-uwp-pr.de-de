---
title: Abrufen und Verstehen von Strichcode-Daten
description: Informationen Sie zum Erhalt und der Interpretation der Barcodedaten, die Sie scannen.
ms.date: 08/29/2018
ms.topic: article
keywords: Windows 10, UWP, Point of Service, POS
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: ece246ffd369ee21c089598f07b2566424757f55
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "8878810"
---
# <a name="obtain-and-understand-barcode-data"></a>Abrufen und Verstehen von Strichcode-Daten

Nachdem Sie Ihr Strichcodescanner eingerichtet haben, benötigen Sie natürlich eine Möglichkeit zum Verständnis der Daten, die Sie scannen. Wenn Sie einen Strichcode scannen, wird das [DataReceived](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.datareceived) -Ereignis ausgelöst. Die [ClaimedBarcodeScanner](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner) sollte dieses Ereignis abonnieren. Das **DataReceived** -Ereignis übergibt ein [BarcodeScannerDataReceivedEventArgs](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerdatareceivedeventargs) -Objekt, das Sie verwenden können, auf die Strichcode-Daten zugreifen.

## <a name="subscribe-to-the-datareceived-event"></a>Abonnieren Sie das DataReceived-Ereignis

Wenn Sie eine **ClaimedBarcodeScanner**haben, haben sie die **DataReceived** Ereignis abonnieren:

```cs
claimedBarcodeScanner.DataReceived += ClaimedBarcodeScanner_DataReceived;
```

Der Ereignishandler wird die **ClaimedBarcodeScanner** und ein Objekt **BarcodeScannerDataReceivedEventArgs** übergeben werden. Sie können über dieses Objekt [Bericht](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerdatareceivedeventargs.report#Windows_Devices_PointOfService_BarcodeScannerDataReceivedEventArgs_Report) -Eigenschaft, die vom Typ [BarcodeScannerReport](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport), Strichcode-Daten zugreifen.

```cs
private async void ClaimedBarcodeScanner_DataReceived(ClaimedBarcodeScanner sender, BarcodeScannerDataReceivedEventArgs args)
{
    // Parse the data
}
```

## <a name="get-the-data"></a>Abrufen der Daten

Wenn Sie die **BarcodeScannerReport**haben, können Sie den Zugriff und Analysieren von Strichcode-Daten. **BarcodeScannerReport** verfügt über drei Eigenschaften:

* [ScanData](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport.scandata): die vollständige, unformatierte Strichcode-Daten.
* [ScanDataLabel](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport.scandatalabel): die decodierten Barcode-Bezeichnung, die nicht in den Header, Prüfsumme und andere Informationen enthalten ist.
* [ScanDataType](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport.scandatatype): der Typ der decodierten Barcode-Bezeichnung. Mögliche Werte sind in der Klasse [BarcodeSymbologies](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies) definiert.

Wenn Sie **ScanDataLabel** oder **ScanDataType**zugreifen möchten, müssen Sie zuerst [IsDecodeDataEnabled](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.isdecodedataenabled#Windows_Devices_PointOfService_ClaimedBarcodeScanner_IsDecodeDataEnabled) auf **true**festlegen.

```cs
claimedBarcodeScanner.IsDecodeDataEnabled = true;
```

### <a name="get-the-scan-data-type"></a>Rufen Sie den Scan-Datentyp ab

Den Typ der decodierten Barcode-Bezeichnung ist ganz einfach&mdash;rufen wir einfach [GetName](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies.getname) auf **ScanDataType**.

```cs
private string GetSymbology(BarcodeScannerDataReceivedEventArgs args)
{
    return BarcodeSymbologies.GetName(args.Report.ScanDataType);
}
```

### <a name="get-the-scan-data-label"></a>Rufen Sie die Beschriftung Überprüfung

Um die decodierten Barcode-Bezeichnung zu erhalten, gibt es einige Dinge zu beachten. Nur bestimmte Datentypen enthalten codierten Text, damit Sie zunächst suchen soll, wenn die Symbologie in eine Zeichenfolge konvertiert werden kann, und konvertieren Sie anschließend den Puffer, die wir aus **ScanDataLabel** auf eine codierten UTF-8-Zeichenfolge zu erhalten.

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

### <a name="get-the-raw-scan-data"></a>Abrufen der unformatierten Scan-Daten

Um die vollständige zu erhalten, konvertieren Sie unformatierte Daten aus der Strichcode wir einfach den Puffer, die, den wir aus **ScanData** in eine Zeichenfolge zu erhalten.

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

Diese Daten werden in der Regel im Format wie aus der Scanner übermittelt. Nachricht Header und Trailer-Informationen werden entfernt, jedoch, da diese enthalten keine nützliche Informationen für eine Anwendung und sind wahrscheinlich Strichcodescanner-spezifische.

Allgemeine Headerinformationen ist ein Präfix (z. B. ein STX Zeichen). Allgemeine Trailer-Informationen ist ein Abschluss-Zeichen (z. B. ein ETX oder CR Zeichen) und ein Block Kontrollkästchen, wenn eine der Scanner generiert wird.

Diese Eigenschaft sollte eine Symbologie Zeichen enthalten, wenn eine der Scanner zurückgegeben wird (z. B. ein **A** für UPC A). Es sollte auch Kontrollkästchen Ziffern enthalten, wenn sie in der Beschriftung vorhanden sind und von der Scanner zurückgegeben. (Beachten Sie, dass Symbologie Zeichen und Kontrollkästchen Ziffern möglicherweise nicht vorhanden, je nach Konfiguration Scanner. Der Scanner wird zurücksenden, wenn vorhanden, wird aber nicht erstellen oder berechnen lassen, wenn sie nicht vorhanden sind.)

Einige Waren kann mit einem ergänzende Strichcode gekennzeichnet werden. Diese Strichcodescanner wird in der Regel auf der rechten Seite des wichtigsten Barcodes platziert und besteht aus einer zusätzlichen 2 oder 5 Zeichen Informationen. Lautet der Scanner waren, die wichtigsten und ergänzende Barcodes enthält, die zusätzlichen Zeichen werden an den hauptpersonen angehängt und das Ergebnis für die Anwendung als eine Beschriftung bereitgestellt wird. (Beachten Sie, dass ein Scanner eine Konfiguration unterstützen kann, die aktiviert oder deaktiviert das Lesen von ergänzende Codes.)

Einige waren möglicherweise mit mehreren Beschriftungen, auch *mit mehreren Symbolen Beschriftungen* oder *Mehrstufige Beschriftungen*genannt gekennzeichnet werden. Diese Barcodes werden in der Regel vertikal angeordnet, und die gleichen oder unterschiedliche Symbologie sein kann. Der Scanner ggf. lesen kann, die mehrere Beschriftungen enthält, wird jede Strichcodescanner an die Anwendung als separate Bezeichnung übermittelt. Dies ist notwendig, aufgrund der aktuellen Mangel an Standardisierung dieser Typen für Strichcodescanner. Eine kann nicht alle Varianten basierend auf den einzelnen Barcode-Daten zu ermitteln. Aus diesem Grund müssen die Anwendung zu bestimmen, wenn mehrere Bezeichnung Barcodes basierend auf der zurückgegebenen Daten gelesen wurde. (Beachten Sie, dass ein Scanner unterstützt möglicherweise nicht lesen von mehreren Beschriftungen.)

Dieser Wert wird vor dem ein **DataReceived** -Ereignis ausgelöst wird, um die Anwendung festgelegt.

[!INCLUDE [feedback](./includes/pos-feedback.md)]

## <a name="see-also"></a>Weitere Informationen:
* [Strichcodescanner](pos-barcodescanner.md)
* [ClaimedBarcodeScanner-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies.getname)
* [BarcodeScannerDataReceivedEventArgs-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerdatareceivedeventargs)
* [BarcodeScannerReport-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport)
* [BarcodeSymbologies-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies)
