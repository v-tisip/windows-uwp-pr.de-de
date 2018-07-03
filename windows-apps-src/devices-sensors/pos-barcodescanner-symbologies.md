---
author: TerryWarwick
title: Arbeiter mit Strichcodescanner-Symbologien
description: Dieser Artikel enthält Informationen über Strichcodescanner-Symbologien.
ms.author: jken
ms.date: 05/3/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Point Of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: f6e03d62316a1b842330f39ac958e4471a895815
ms.sourcegitcommit: dc3389ef2e2c94b324872a086877314d6f963358
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2018
ms.locfileid: "1874525"
---
# <a name="working-with-symbologies"></a>Arbeiten mit Symbologien
Eine [Strichcodesymbologie](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies) ist eine Zuordnung von Daten zu einem bestimmten Strichcodeformat. Einige allgemeinen Symbologien enthalten UPC, Code 128, QR-Code. Die UWP-Strichcodescanner-APIs ermöglichen einer Anwendung, zu steuern, wie der Scanner die Symbologien verarbeitet, ohne manuell den Scanner konfigurieren zu müssen. 

## <a name="determine-which-symbologies-are-supported"></a>Bestimmen Sie, welche Symbologien unterstützt werden 
Da die Anwendung unterschiedliche Strichcodescannermodelle verschiedener Hersteller verwenden kann, sollten Sie den Scanner befragen, um die Liste der Symbologien zu ermitteln, die er unterstützt.  Dies kann nützlich sein, wenn die Anwendung eine bestimmte Symbologie erfordert, die möglicherweise nicht von allen Scannern unterstützt wird oder Sie müssen Symbologien aktivieren, die entweder manuell oder programmgesteuert auf dem Scanner deaktiviert wurden.
Sobald Sie ein [BarcodeScanner](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner)-Objekt über [BarcodeScanner.FromIdAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.fromidasync) erhalten haben, rufen Sie [GetSupportedSymbologiesAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.getsupportedsymbologiesasync#Windows_Devices_PointOfService_BarcodeScanner_GetSupportedSymbologiesAsync) auf, um eine Liste der Symbologien abzurufen, die vom Gerät unterstützt werden.

## <a name="determine-if-a-specific-symbology-is-supported"></a>Bestimmen Sie, ob eine bestimmte Symbologie unterstützt wird
Um festzustellen, ob der Scanner eine bestimmte Symbologie unterstützt, rufen Sie [IsSymbologySupportedAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.issymbologysupportedasync#Windows_Devices_PointOfService_BarcodeScanner_IsSymbologySupportedAsync_System_UInt32_) auf.

## <a name="changing-which-symbologies-are-recognized"></a>Ändern, welche Symbologien erkannt werden
In einigen Fällen möchten Sie möglicherweise eine Teilmenge Symbologien verwenden, die der Strichcodescanner unterstützt.  Dies ist besonders nützlich, um Symbologien zu blockieren, die Sie nicht in Ihrer Anwendung verwenden möchten. Um sicherzustellen, dass ein Benutzer den richtigen Strichcode scannt, können Sie das Scannen auf UPC oder EAN beim Kauf von Element-SKUs beschränken und das Scannen auf Code 128 beim Kauf von Seriennummern beschränken.
Wenn Sie die Symbologien kennen, die der Scanner unterstützt, können Sie die Symbologien festlegen, die Sie erkennen möchten.  Dies ist möglich, nachdem Sie ein [ClaimedBarcodeScanner](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner)-Objekt mithilfe von [ClaimScannerAsyc](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.claimscannerasync#Windows_Devices_PointOfService_BarcodeScanner_ClaimScannerAsync) erstellt haben. Rufen Sie [SetActiveSymbologiesAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.setactivesymbologiesasync#Windows_Devices_PointOfService_ClaimedBarcodeScanner_SetActiveSymbologiesAsync_Windows_Foundation_Collections_IIterable_System_UInt32__) auf, um eine bestimmte Anzahl von Symbologien zu aktivieren. Die in der Liste nicht berücksichtigten Symbologien werden deaktiviert.

## <a name="restricting-scan-data-by-data-length"></a>Einschränken von gescannten Daten nach Datenlänge
Einige Symbologien haben verschiedene Längen z.B. Code 39 oder Code 128.  Strichcodes mit dieser Symbologie können bestimmt werden, wobei jeder verschiedene Daten mit einer bestimmten Länge haben kann. Das Festlegen der bestimmten Länge der Daten, die Sie benötigen, kann ungültige Überprüfungen verhindern.

| Methode    | Beschreibung |
| :-------- | :---------- |
| [SetSymbologyAttributesAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.setsymbologyattributesasync#Windows_Devices_PointOfService_ClaimedBarcodeScanner_SetSymbologyAttributesAsync_System_UInt32_Windows_Devices_PointOfService_BarcodeSymbologyAttributes_) | Ermöglicht das Konfigurieren einer gewünschten Länge decodierter Daten und wie der Scanner die Prüfziffer überprüft. |
| [GetSymbologyAttributesAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.getsymbologyattributesasync#Windows_Devices_PointOfService_ClaimedBarcodeScanner_GetSymbologyAttributesAsync_System_UInt32_) | Ermöglicht das Abrufen der aktuellen Länge und das Überprüfen der Prüfziffer. |

> [!Important] 
> Stellen Sie sicher, dass Ihr Strichcodescanner die Verwendung von Symbologieattributen unterstützt, indem Sie zunächst die folgenden Eigenschaften überprüfen: 
> - [IsDecodeLengthSupported](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologyattributes.isdecodelengthsupported#Windows_Devices_PointOfService_BarcodeSymbologyAttributes_IsDecodeLengthSupported)
> - [ICheckDigitTransmissionSupported](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologyattributes.ischeckdigittransmissionsupported#Windows_Devices_PointOfService_BarcodeSymbologyAttributes_IsCheckDigitTransmissionSupported)
> - [IsCheckDigitValidationSupported](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologyattributes.ischeckdigitvalidationsupported#Windows_Devices_PointOfService_BarcodeSymbologyAttributes_IsCheckDigitValidationSupported)
