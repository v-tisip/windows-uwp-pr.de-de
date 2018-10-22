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
# <a name="obtain-and-understand-barcode-data"></a>Abrufen und Verstehen von Strichcode-Daten

Nachdem Sie Ihr Strichcodescanner eingerichtet haben, benötigen Sie natürlich eine Möglichkeit, Verständnis der Daten, die Sie scannen. Wenn Sie einen Strichcode scannen, wird das [DataReceived](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.datareceived) -Ereignis ausgelöst. Die [ClaimedBarcodeScanner](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner) sollte dieses Ereignis abonnieren. Das **DataReceived** Ereignis übergibt ein [BarcodeScannerDataReceivedEventArgs](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerdatareceivedeventargs) -Objekt, das Sie verwenden können, um die Strichcode-Daten zugreifen.

## <a name="subscribe-to-the-datareceived-event"></a>Abonnieren Sie das DataReceived-Ereignis

Wenn Sie eine **ClaimedBarcodeScanner**haben, haben sie die **DataReceived** Ereignis abonnieren:

```cs
claimedBarcodeScanner.DataReceived += ClaimedBarcodeScanner_DataReceived;
```

Der Ereignishandler wird die **ClaimedBarcodeScanner** und ein Objekt **BarcodeScannerDataReceivedEventArgs** übergeben werden. Sie können die Strichcode-Daten über dieses Objekt [Bericht](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerdatareceivedeventargs.report#Windows_Devices_PointOfService_BarcodeScannerDataReceivedEventArgs_Report) Eigenschaft Typ [BarcodeScannerReport vom](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport)zugreifen.

```cs
private async void ClaimedBarcodeScanner_DataReceived(ClaimedBarcodeScanner sender, BarcodeScannerDataReceivedEventArgs args)
{
    // Parse the data
}
```

## <a name="get-the-data"></a>Abrufen der Daten

Wenn Sie die **BarcodeScannerReport**haben, können Sie Zugriff auf und Analysieren der Strichcode-Daten. **BarcodeScannerReport** verfügt über drei Eigenschaften:

* [ScanData](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport.scandata): die vollständige, unformatierte Strichcode-Daten.
* [ScanDataLabel](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport.scandatalabel): die decodierten Barcode-Bezeichnung, die nicht in der Kopfzeile, Prüfsumme und andere Informationen enthalten ist.
* [ScanDataType](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport.scandatatype): der decodierten Barcode Label-Typ. Mögliche Werte sind in der [BarcodeSymbologies](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies) -Klasse definiert.

Wenn Sie **ScanDataLabel** oder **ScanDataType**zugreifen möchten, müssen Sie zuerst [IsDecodeDataEnabled](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.isdecodedataenabled#Windows_Devices_PointOfService_ClaimedBarcodeScanner_IsDecodeDataEnabled) auf **"true"** festlegen.

```cs
claimedBarcodeScanner.IsDecodeDataEnabled = true;
```

### <a name="get-the-scan-data-type"></a>Rufen Sie den Scan-Datentyp ab

Abrufen des decodierten Barcode Beschriftung Typs ist ganz einfach&mdash;rufen wir einfach [GetName](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies.getname) auf **ScanDataType**.

```cs
private string GetSymbology(BarcodeScannerDataReceivedEventArgs args)
{
    return BarcodeSymbologies.GetName(args.Report.ScanDataType);
}
```

### <a name="get-the-scan-data-label"></a>Rufen Sie die Beschriftung scan

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

Um die vollständige zu erhalten, konvertieren Sie unformatierte Daten aus der Strichcode wir einfach den Puffer, die, den wir in einer Zeichenfolge aus **ScanData** erhalten.

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

Diese Daten werden in der Regel im Format wie aus dem Scanner übermittelt. Header und Trailer Informationen werden entfernt, jedoch, da diese enthalten keine nützliche Informationen für eine Anwendung und Stichwörtern Scanner für die jeweilige.

Allgemeine Headerinformationen ist ein Präfix (z. B. ein STX Zeichen). Allgemeine Trailer-Informationen sind ein Abschluss-Zeichen (z. B. ein ETX oder CR Zeichen) und ein Block Kontrollkästchen, wenn eine von der Scanner generiert wird.

Diese Eigenschaft sollte eine Symbologie Zeichen enthalten, wenn eine der Scanner zurückgegeben wird (z. B. ein **A** für UPC A). Es sollte auch Kontrollkästchen Ziffern enthalten, wenn sie in der Beschriftung vorhanden sind und von der Scanner zurückgegeben. (Beachten Sie, dass sowohl Symbologie Zeichen Kontrollkästchen Ziffern und können möglicherweise nicht vorhanden, je nach der Konfiguration des Scanner. Der Scanner wird zurücksenden, wenn vorhanden, wird jedoch nicht zu generieren oder berechnen lassen, wenn er nicht vorhanden sind.)

Einige Waren kann mit einem ergänzende Strichcode gekennzeichnet werden. Diese Barcode wird in der Regel rechts neben den wichtigsten Strichcode platziert und besteht aus einer zusätzlichen 2 oder 5 Zeichen von Informationen. Lautet der Scanner waren, die Haupt- und ergänzende Barcodes enthält, die zusätzlichen Zeichen werden an den hauptpersonen angehängt und das Ergebnis wird an die Anwendung als eine Beschriftung übermittelt. (Beachten Sie, dass ein Scanner eine Konfiguration unterstützen kann, die aktiviert oder deaktiviert das Lesen von ergänzende Codes.)

Einige waren möglicherweise mit mehreren Beschriftungen, auch *mit mehreren Symbolen Beschriftungen* oder *mehrstufigen Beschriftungen*genannt gekennzeichnet werden. Diese Barcodes werden in der Regel vertikal angeordnet, und von den gleichen oder unterschiedliche Symbologie sein. Wenn der Scanner waren, die mehrere Beschriftungen enthält liest, wird jede Barcode an die Anwendung als separate Bezeichnung übermittelt. Dies ist aufgrund der aktuellen Mangel an Standardisierung dieser Typen für Barcode erforderlich. Eine kann nicht für alle Varianten basierend auf den einzelnen Barcode-Daten zu ermitteln. Aus diesem Grund wird die Anwendung muss, um zu bestimmen, wann ein mehrere Beschriftung Strichcode basierend auf der zurückgegebenen Daten gelesen wurde. (Beachten Sie, dass ein Scanner kann oder möglicherweise nicht lesen von mehreren Beschriftungen unterstützen.)

Dieser Wert wird vor einem **DataReceived** -Ereignis ausgelöst werden, um die Anwendung festgelegt.

[!INCLUDE [feedback](./includes/pos-feedback.md)]

## <a name="see-also"></a>Weitere Informationen:
* [Strichcodescanner](pos-barcodescanner.md)
* [ClaimedBarcodeScanner-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies.getname)
* [BarcodeScannerDataReceivedEventArgs-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerdatareceivedeventargs)
* [BarcodeScannerReport-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport)
* [BarcodeSymbologies-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies)