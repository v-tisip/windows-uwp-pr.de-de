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
ms.sourcegitcommit: a160b91a554f8352de963d9fa37f7df89f8a0e23
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/21/2018
ms.locfileid: "4127113"
---
# <a name="obtain-and-understand-barcode-data"></a>Beziehen und Barcodedaten verstehen

Wenn der Barcodescanner eingerichtet haben, benötigen Sie natürlich eine Möglichkeit zum Verständnis der Daten, die Sie scannen. Beim Scannen von Barcodes wird das [DataReceived](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.datareceived) -Ereignis ausgelöst. Die [ClaimedBarcodeScanner](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner) sollte dieses Ereignis abonnieren. Das **DataReceived** -Ereignis übergibt ein [BarcodeScannerDataReceivedEventArgs](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerdatareceivedeventargs) -Objekt, das mit die Barcode-Daten zugreifen.

## <a name="subscribe-to-the-datareceived-event"></a>Das DataReceived-Ereignis abonnieren

Haben Sie eine **ClaimedBarcodeScanner**haben Sie das **DataReceived** -Ereignis abonnieren:

```cs
claimedBarcodeScanner.DataReceived += ClaimedBarcodeScanner_DataReceived;
```

Der Ereignishandler wird **ClaimedBarcodeScanner** und ein **BarcodeScannerDataReceivedEventArgs** -Objekt übergeben. Sie können dieses Objekt [Bericht](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerdatareceivedeventargs.report#Windows_Devices_PointOfService_BarcodeScannerDataReceivedEventArgs_Report) vom Typ [BarcodeScannerReport](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport), Barcode-Daten zugreifen.

```cs
private async void ClaimedBarcodeScanner_DataReceived(ClaimedBarcodeScanner sender, BarcodeScannerDataReceivedEventArgs args)
{
    // Parse the data
}
```

## <a name="get-the-data"></a>Daten abrufen

Haben Sie **BarcodeScannerReport**, können Zugriff auf und die Barcodedaten analysieren. **BarcodeScannerReport** hat drei Eigenschaften:

* [ScanData](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport.scandata): der vollständige raw Barcodedaten.
* [ScanDataLabel](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport.scandatalabel): die decodierten Strichcode-Etikett, das keinen Header-Prüfsumme und sonstige Informationen enthält.
* [ScanDataType](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport.scandatatype): die decodierten Barcodetyp Bezeichnung. Mögliche Werte sind in der [BarcodeSymbologies](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies) -Klasse definiert.

Sie **ScanDataLabel** oder **ScanDataType**zugreifen möchten, müssen Sie [IsDecodeDataEnabled](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.isdecodedataenabled#Windows_Devices_PointOfService_ClaimedBarcodeScanner_IsDecodeDataEnabled) zuerst auf **true**festlegen.

```cs
claimedBarcodeScanner.IsDecodeDataEnabled = true;
```

### <a name="get-the-scan-data-type"></a>Rufen Sie den Scan-Datentyp ab

Etikettentyp decodierten Barcode ist ganz einfach&mdash;rufen wir einfach [GetName](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies.getname) auf **ScanDataType**.

```cs
private string GetSymbology(BarcodeScannerDataReceivedEventArgs args)
{
    return BarcodeSymbologies.GetName(args.Report.ScanDataType);
}
```

### <a name="get-the-scan-data-label"></a>Die Beschriftung Scan erhalten

Zu decodierten Strichcode-Etikett gibt es einiges zu beachten haben. Nur bestimmte Datentypen enthalten codierten Text, sodass Sie zuerst die Symbologie in eine Zeichenfolge konvertiert werden kann und den Puffer bekommen wir aus **ScanDataLabel** eine codierte UTF-8-Zeichenfolge zu konvertieren.

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

### <a name="get-the-raw-scan-data"></a>Raw Scan Daten

Zu vollständigen konvertieren Rohdaten aus den Barcode wir einfach den Puffer erhalten wir von **ScanData** in eine Zeichenfolge.

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

Diese Daten sind im Allgemeinen das Format vom Scanner geliefert. Header und Trailer Informationen werden entfernt, jedoch enthalten nützliche Informationen für eine Anwendung und Scanner spezifisch sein.

Allgemeine Headerinformationen ist ein Präfix (z. B. ein STX-Zeichen). Anhänger Informationen ist ein Abschlusszeichen (z. B. ein Zeichen ETX oder CR) und ein Blockzeichen Kontrollkästchen einen der Scanner generiert wird.

Diese Eigenschaft sollte Symbologie Zeichen, wenn der Scanner zurückgegeben (z. B. **ein** für UPC-A). Es sollte auch Prüfziffern in der Bezeichnung vorhanden sind und der Scanner zurückgegeben. (Beachten Sie, dass Symbologie Zeichen und Prüfziffern können oder nicht vorhanden sein darf, die Scanner-Konfiguration abhängig. Der Scanner wird zurücksenden, wenn vorhanden, aber nicht erstellen oder berechnen lassen, wenn sie fehlen.)

Einige waren möglicherweise zusätzliche Barcode markiert. Barcode befindet sich normalerweise rechts neben den wichtigsten Barcode und eine weitere zwei oder fünf Zeichen von Informationen aus. Liest der Scanner waren Haupt- und zusätzliche Barcodes enthält zusätzlichen Zeichen sind die wichtigsten Zeichen angehängt und das Ergebnis als eine Bezeichnung an die Anwendung übermittelt. (Beachten Sie, dass ein Scanner eine Konfiguration unterstützt, die aktiviert oder deaktiviert das Lesen des Codes zusätzliche.)

Einige waren möglicherweise mehrere Bezeichnungsfelder bezeichnet *mit mehreren Symbolen* oder *gestuften Etiketten*markiert. Diese Barcodes werden in der Regel vertikal angeordnet und von demselben oder einem anderen Symbologie möglicherweise. Der Scanner waren liest, die mehrere Etiketten enthält, wird jeder Barcode Anwendung als separate Bezeichnung übermittelt. Dies ist aufgrund des aktuellen Mangels von Standardisierung dieser Barcode-Typen. Eine kann nicht alle Varianten basierend auf den einzelnen Barcode-Daten bestimmt. Daher muss die Anwendung bestimmen, wenn mehrere Label Barcode bei den zurückgegebenen Daten gelesen wurden. (Beachten Sie, dass ein Scanner unterstützen mehrere Etiketten lesen.)

Dieser Wert wird vor einem **DataReceived** zu der Anwendung festgelegt.

[!INCLUDE [feedback](./includes/pos-feedback.md)]

## <a name="see-also"></a>Weitere Informationen:
* [Strichcodescanner](pos-barcodescanner.md)
* [ClaimedBarcodeScanner-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies.getname)
* [BarcodeScannerDataReceivedEventArgs-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerdatareceivedeventargs)
* [BarcodeScannerReport-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannerreport)
* [BarcodeSymbologies-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies)