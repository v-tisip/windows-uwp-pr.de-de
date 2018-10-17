---
author: TerryWarwick
title: Konfigurieren eines Strichcodescanners
description: Hier erfahren Sie, wie Sie einen Strichcodescanner für die Anwendung konfigurieren.
ms.author: jken
ms.date: 08/29/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Point of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: b33c1d33fe88a09de36e8f80a3034b915d338861
ms.sourcegitcommit: 9354909f9351b9635bee9bb2dc62db60d2d70107
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2018
ms.locfileid: "4694285"
---
# <a name="configure-a-barcode-scanner"></a>Konfigurieren eines Strichcodescanners

Strichcodescanner können in mehreren verschiedenen Modi konfiguriert werden.  Es ist wichtig für Ihren Strichcodescanner, dass er für die Anwendung ordnungsgemäß konfiguriert ist.

Viele Strichcodescanner können im **Tastatur Wedge**-Modus konfiguriert werden. Dabei wird der Strichcodescanner als eine Tastatur auf Windows angezeigt.  Dadurch können Sie Strichcodes in Anwendungen scannen, die keine Strichcodescanner unterstützen, wie Notepad.  Wenn Sie einen Strichcode in diesem Modus scannen, werden die decodierten Daten aus dem Strichcodescanner an der Einfügemarke eingefügt, als ob Sie die Daten über die Tastatur eingegeben.  Wenn Sie mehr Kontrolle über Ihren Strichcodescanner von der UWP-App haben möchten, müssen Sie diesen in einem Modus ohne Tastatur-Wedge konfigurieren.

## <a name="usb-barcode-scanner"></a>USB-Strichcodescanner
Ein USB-verbundener Strichcodescanner muss im **HID POS-Scanner**-Modus mit den Strichcodescannertreiber konfiguriert werden, der in Windows enthalten ist. Dieser Treiber ist eine Implementierung der Spezifikation **HID Point of Sale Usage Tables** auf [USB-HID](http://www.usb.org/developers/hidpage/)veröffentlicht.  Weitere Informationen finden Sie in der Dokumentation der Strichcodescanner oder wenden Sie sich an den Hersteller des Scanners für weitere Anweisungen zum Aktivieren des **POS-HID-Scanner**-Modus.  Wenn der Strichcodescanner als **POS-HID-Scanner** konfiguriert ist, erscheint er im Geräte-Manager unter dem **POS-Strichcodescanner**-Knoten als **POS HID Strichcodescanner**.

Der Hersteller des Strichcodescanners hat möglicherweise einen anbieterspezifischen Treiber, der die UWP Strichcodescanner-APIs in einem anderen Modus als **POS-HID-Scanner** unterstützt.  Wenn Sie bereits mit UWP Strichcodescanner-APIs kompatibel Hersteller bereitgestellte Treiber installiert haben, sehen Sie möglicherweise eine herstellerspezifische unter **POS-Strichcodescanner** im Geräte-Manager aufgeführt.

## <a name="bluetooth-barcode-scanner"></a>Bluetooth-Strichcodescanner
Ein mit Bluetooth verbundener Scanner muss im **Seriellen Port-Protokoll – einfache serielle Schnittstelle (SPP-SSI)**-Modus für die Arbeit mit UWP Strichcodescanner-APIs konfiguriert sein.  Weitere Informationen finden Sie in der Dokumentation der Strichcodescanner oder wenden Sie sich an den Hersteller des Scanners für weitere Anweisungen zum Aktivieren des **SSI-SPP-Modus**.

Vor der Verwendung Ihres Bluetooth-Strichcodescanners müssen Sie es mittels koppeln **Einstellungen > Geräte > Bluetooth & andere Geräte > Bluetooth- oder anderen Gerät hinzufügen**.

Sie können initiieren und steuern den kopplungsprozess mithilfe der [Windows.Devices.Enumeration](https://docs.microsoft.com/uwp/api/windows.devices.enumeration) -Namespace.  Weitere Informationen finden Sie unter [Geräte koppeln](https://docs.microsoft.com/windows/uwp/devices-sensors/pair-devices).

[!INCLUDE [feedback](./includes/pos-feedback.md)]