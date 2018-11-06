---
author: laurenhughes
title: App-Paketarchitektur
description: Hier erfahren Sie mehr über die Prozessorarchitekturen, die beim Erstellen des UWP-App-Pakets verwendet werden sollten.
ms.author: lahugh
ms.date: 7/13/2017
ms.topic: article
keywords: Windows10, Uwp, Verpacken, Architektur, Paket-Konfiguration
ms.localizationpriority: medium
ms.openlocfilehash: 3e265df32a8c4168cddced905e7b0712e4601264
ms.sourcegitcommit: e814a13978f33654d8e995584f4b047cb53e0aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "6042280"
---
# <a name="app-package-architectures"></a>App-Paketarchitektur

App-Pakete sind so konfiguriert, dass sie auf einer bestimmte Prozessorarchitektur ausgeführt werden. Durch die Auswahl einer Architektur geben Sie an, auf welchen Geräten Ihre App ausgeführt werden soll. Universelle Windows-Plattform (UWP) Apps können konfiguriert werden, um auf die folgenden Architekturen ausgeführt werden:
- x86
- x64
- ARM

Es ist **dringend** empfohlen, dass Sie alle Architekturen als Ziel Ihrer App-Paket erstellen. Durch Aufheben der Auswahl einer Gerätearchitektur, werden Sie die Anzahl der Geräte, die Ihre App ausführen können, begrenzt. Dies wiederum begrenzt die Menge an Personen, die Ihre App verwenden können!

## <a name="windows-10-devices-and-architectures"></a>Windows 10-Geräte und -Architekturen

> [!div class="mx-tableFixed"]
| UWP-Architektur | Desktop (x86)      | Desktop (x64)      | Desktop (ARM)      | Mobilgeräte             | HoloLens           | Xbox               | IoT Core (geräteabhängig) | Surface Hub        |
|------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|-----------------------------|--------------------|
| x86              | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :x:                | :heavy_check_mark: | :x:                | :heavy_check_mark:          | :heavy_check_mark: |
| x64              | :x:                | :heavy_check_mark: | :x:                | :x:                | :x:                | :heavy_check_mark: | :heavy_check_mark:          | :heavy_check_mark: |
| ARM              | :x:                | :x:                | :heavy_check_mark: | :heavy_check_mark: | :x:                | :x:                | :heavy_check_mark:          | :x:                |
 

Befassen wir uns ausführlicher mit Architekturen. 

### <a name="x86"></a>x86
Das Auswählen der Option x86 ist im Allgemeinen die sicherste Konfiguration für ein App-Paket, da es auf fast jedem Gerät ausgeführt wird. Auf einigen Geräten wird ein App-Paket mit x86 nicht ausgeführt, z.B. Xbox oder einige IoT Core-Geräte. Für einen PC ist jedoch ein x86 Paket ist die sicherste Option und hat die größte Reichweite für die Bereitstellung von Geräten. Ein erheblichen Teil der Windows10-Geräte führen weiterhin die x86 Version von Windows aus. 

### <a name="x64"></a>x64
Diese Konfiguration wird weniger häufig als x86 verwendet. Sie sollten wissen, dass diese Konfiguration für Desktops mit 64-Bit-Versionen von Windows10, [UWP-Apps auf Xbox](https://docs.microsoft.com/windows/uwp/xbox-apps/system-resource-allocation) und Windows10 IoT Core auf Intel Joule reserviert ist.

### <a name="arm"></a>ARM
Die Windows10 on ARM-Konfiguration umfasst Desktop-PCs, mobile Geräte und einige IoT Core-Geräte (Rasperry Pi 2, Raspberry Pi 3 und DragonBoard). Windows10 on ARM-Desktop-PCs sind eine neue Funktion in die Windows-Produktfamilie. Wenn Sie UWP-App-Entwickler sind, sollten Sie ARM-Pakete für den Store für diese PCs übermitteln. 

Sehen Sie sich diesen //Build-Talk an, um eine Demo zu [Windows10 on ARM](https://channel9.msdn.com/Events/Build/2017/P4171) zu sehen und mehr zu erfahren. 

Weitere Informationen zu IoT-Themen finden Sie unter [Bereitstellen einer App mit Visual Studio](https://developer.microsoft.com/windows/iot/Docs/AppDeployment).
