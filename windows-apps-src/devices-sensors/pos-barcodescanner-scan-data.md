---
author: eliotcowley
title: Abzurufen Sie und zu verstehen Sie Barcode-Daten
description: Erfahren Sie, wie zum Erhalt und der Interpretation der Barcodedaten, die Sie scannen.
ms.author: elcowle
ms.date: 08/29/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Point of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: 0992ea54092063ba53f23871599905e58f1b456e
ms.sourcegitcommit: e4f3e1b2d08a02b9920e78e802234e5b674e7223
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2018
ms.locfileid: "4211004"
---
# <a name="obtain-and-understand-barcode-data"></a>Abzurufen Sie und zu verstehen Sie Barcode-Daten

Nachdem Sie Ihr Strichcodescanner eingerichtet haben, benötigen Sie natürlich eine Möglichkeit, Verständnis der Daten, die Sie scannen. Wenn Sie einen Strichcode scannen, wird das [DataReceived](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.datareceived) -Ereignis ausgelöst. Die [ClaimedBarcodeScanner](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner) sollte dieses Ereignis abonnieren. Das **DataReceived** Ereignis übergibt ein [BarcodeScannerDataReceivedEventArgs](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerdatareceivedeventargs) -Objekt, das Sie verwenden können, auf die Barcodedaten zugreifen.

## <a name="subscribe-to-the-datareceived-event"></a>Abonnieren Sie das DataReceived-Ereignis

Wenn Sie eine **ClaimedBarcodeScanner**haben, haben sie die **DataReceived** Ereignis abonnieren:

```cs
claimedBarcodeScanner.DataReceived += ClaimedBarcodeScanner_DataReceived;
```

Der Ereignishandler wird die **ClaimedBarcodeScanner** und ein Objekt **BarcodeScannerDataReceivedEventArgs** übergeben werden. Sie können die Barcode-Daten über dieses Objekts [Bericht](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerdatareceivedeventargs.report#Windows_Devices_PointOfService_BarcodeScannerDataReceivedEventArgs_Report) Eigenschaft Typ [BarcodeScannerReport vom](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport)zugreifen.

```cs
private async void ClaimedBarcodeScanner_DataReceived(ClaimedBarcodeScanner sender, BarcodeScannerDataReceivedEventArgs args)
{
    // Parse the data
}
```

## <a name="get-the-data"></a>Abrufen der Daten

Wenn Sie die **BarcodeScannerReport**haben, können Sie Zugriff auf und analysieren die Barcode-Daten. **BarcodeScannerReport** verfügt über drei Eigenschaften:

* [ScanData](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport.scandata): die vollständige, unformatierte Barcodedaten.
* [ScanDataLabel](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport.scandatalabel): die decodierten Barcode-Bezeichnung, die nicht in der Kopfzeile, Prüfsumme und sonstige Informationen enthalten ist.
* [ScanDataType](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport.scandatatype): der decodierten Barcode Label-Typ. Mögliche Werte sind in der Klasse [BarcodeSymbologies](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies) definiert.

Wenn Sie **ScanDataLabel** oder **ScanDataType**zugreifen möchten, müssen Sie zuerst [IsDecodeDataEnabled](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.isdecodedataenabled#Windows_Devices_PointOfService_ClaimedBarcodeScanner_IsDecodeDataEnabled) auf **"true"** festlegen.

```cs
claimedBarcodeScanner.IsDecodeDataEnabled = true;
```

### <a name="get-the-scan-data-type"></a>Rufen Sie den Scan-Datentyp ab

Abrufen des decodierten Barcode Bezeichnung Typs ist ganz einfach&mdash;rufen wir einfach [GetName](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies.getname) auf **ScanDataType**.

```cs
private string GetSymbology(BarcodeScannerDataReceivedEventArgs args)
{
    return BarcodeSymbologies.GetName(args.Report.ScanDataType);
}
```

### <a name="get-the-scan-data-label"></a>Erhalten Sie die Beschriftung scan

Um die decodierten Barcode-Bezeichnung zu erhalten, gibt es einige Dinge zu beachten. Nur bestimmte Datentypen enthalten codierten Text, damit Sie zuerst suchen soll, wenn die Symbologie in eine Zeichenfolge konvertiert werden kann, und konvertieren Sie anschließend den Puffer, die wir aus **ScanDataLabel** auf eine codierten UTF-8-Zeichenfolge erhalten.

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

Um die vollständige zu erhalten, konvertieren unformatierte Daten aus der Strichcode wir einfach den Puffer, die, den wir aus **ScanData** in eine Zeichenfolge zu erhalten.

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

Diese Daten werden in der Regel im Format wie aus dem Scanner übermittelt. Header und Trailer Informationen werden entfernt, jedoch, da diese enthalten keine nützliche Informationen für eine Anwendung und sind wahrscheinlich Strichcodescanner-spezifische.

Allgemeine Headerinformationen ist ein Präfix (z. B. ein STX Zeichen). Allgemeine Trailer Informationen ist ein Abschluss-Zeichen (z. B. ein ETX oder CR Zeichen) und ein Block Kontrollkästchen, wenn eine der Scanner generiert wird.

Diese Eigenschaft sollte eine Symbologie Zeichen enthalten, wenn eine der Scanner zurückgegeben wird (z. B. ein **A** für UPC A). Es sollte auch Kontrollkästchen Ziffern enthalten, wenn sie in der Beschriftung vorhanden sind und von der Scanner zurückgegeben. (Beachten Sie, dass sowohl Symbologie Zeichen Kontrollkästchen Ziffern und können möglicherweise nicht vorhanden, je nach Konfiguration Scanner. Der Scanner wird zurücksenden, wenn vorhanden, wird aber nicht erstellen oder berechnen lassen, wenn er nicht vorhanden sind.)

Einige Waren kann mit einem ergänzende Strichcode gekennzeichnet werden. Diese Barcode wird in der Regel rechts neben den wichtigsten Strichcode platziert und besteht aus einer zusätzlichen 2 oder 5 Zeichen von Informationen. Lautet der Scanner waren, die Haupt- und ergänzende Barcodes enthält die ergänzenden Zeichen werden an den hauptpersonen angehängt und das Ergebnis der Anwendung als eine Beschriftung übermittelt wird. (Beachten Sie, dass ein Scanner eine Konfiguration unterstützen kann, die aktiviert oder deaktiviert das Lesen von ergänzende Codes.)

Einige waren möglicherweise mit mehreren Beschriftungen, auch *mit mehreren Symbolen Beschriftungen* oder *mehrstufigen Beschriftungen*genannt gekennzeichnet werden. Diese Barcodes werden in der Regel vertikal angeordnet, und die gleichen oder unterschiedliche Symbologie sein kann. Wenn der Scanner waren, die mehrere Beschriftungen enthält liest, wird jedes Strichcodescanner an die Anwendung als separate Bezeichnung übermittelt. Dies ist aufgrund der aktuellen Mangel an Standardisierung dieser Typen für Strichcodescanner erforderlich. Eine kann nicht für alle Varianten basierend auf den einzelnen Barcode-Daten zu ermitteln. Aus diesem Grund wird die Anwendung muss, um zu bestimmen, wann ein mehrere Bezeichnung Strichcode basierend auf der zurückgegebenen Daten gelesen wurde. (Beachten Sie, dass ein Scanner unterstützen möglicherweise nicht lesen von mehreren Beschriftungen.)

Dieser Wert wird vor einer **DataReceived** -Ereignis ausgelöst werden, an die Anwendung festgelegt.

[!INCLUDE [feedback](./includes/pos-feedback.md)]

## <a name="see-also"></a>Weitere Informationen:
* [Strichcodescanner](pos-barcodescanner.md)
* [ClaimedBarcodeScanner-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies.getname)
* [BarcodeScannerDataReceivedEventArgs-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerdatareceivedeventargs)
* [BarcodeScannerReport-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport)
* [BarcodeSymbologies-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies)