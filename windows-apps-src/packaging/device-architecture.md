---
title: App-Paketarchitektur
description: Hier erfahren Sie mehr über die Prozessorarchitekturen, die beim Erstellen des UWP-App-Pakets verwendet werden sollten.
ms.date: 7/13/2017
ms.topic: article
keywords: Windows10, Uwp, Verpacken, Architektur, Paket-Konfiguration
ms.localizationpriority: medium
ms.openlocfilehash: 5ce92f4da57b99638f393125d3aed11a4bd91bb6
ms.sourcegitcommit: 62bc4936ca8ddf1fea03d43a4ede5d14a5755165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "8991596"
---
# <a name="app-package-architectures"></a>App-Paketarchitektur

App-Pakete sind so konfiguriert, dass sie auf einer bestimmte Prozessorarchitektur ausgeführt werden. Durch die Auswahl einer Architektur geben Sie an, auf welchen Geräten Ihre App ausgeführt werden soll. Universelle Windows-Plattform (UWP) Apps können konfiguriert werden, um auf die folgenden Architekturen ausgeführt werden:
- x86
- x64
- ARM
- ARM64

Es ist **dringend** empfohlen, dass Sie alle Architekturen als Ziel Ihrer App-Paket erstellen. Durch Aufheben der Auswahl einer Gerätearchitektur, werden Sie die Anzahl der Geräte, die Ihre App ausführen können, begrenzt. Dies wiederum begrenzt die Menge an Personen, die Ihre App verwenden können!

## <a name="windows-10-devices-and-architectures"></a>Windows 10-Geräte und -Architekturen

> [!div class="mx-tableFixed"]
| UWP-Architektur | Desktop (x86)      | Desktop (x64)      | Desktop (ARM)      | Mobilgeräte             | Windows Mixed Reality und HoloLens           | Xbox               | IoT Core (geräteabhängig) | Surface Hub        |
|------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|-----------------------------|--------------------|
| x86              | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :x:                | :heavy_check_mark: | :x:                | :heavy_check_mark:          | :heavy_check_mark: |
| x64              | :x:                | :heavy_check_mark: | :x:                | :x:                | :x:                | :heavy_check_mark: | :heavy_check_mark:          | :heavy_check_mark: |
| ARM, ARM64              | :x:                | :x:                | :heavy_check_mark: | :heavy_check_mark: | :x:                | :x:                | :heavy_check_mark:          | :x:                |


Befassen wir uns ausführlicher mit Architekturen.

### <a name="x86"></a>x86
Das Auswählen der Option x86 ist im Allgemeinen die sicherste Konfiguration für ein App-Paket, da es auf fast jedem Gerät ausgeführt wird. Auf einigen Geräten wird ein App-Paket mit x86 nicht ausgeführt, z.B. Xbox oder einige IoT Core-Geräte. Für einen PC ist jedoch ein x86 Paket ist die sicherste Option und hat die größte Reichweite für die Bereitstellung von Geräten. Ein erheblichen Teil der Windows10-Geräte führen weiterhin die x86 Version von Windows aus.

### <a name="x64"></a>x64
Diese Konfiguration wird weniger häufig als x86 verwendet. Sie sollten wissen, dass diese Konfiguration für Desktops mit 64-Bit-Versionen von Windows10, [UWP-Apps auf Xbox](https://docs.microsoft.com/windows/uwp/xbox-apps/system-resource-allocation) und Windows10 IoT Core auf Intel Joule reserviert ist.

### <a name="arm-and-arm64"></a>ARM, ARM64
Die Windows10 on ARM-Konfiguration umfasst Desktop-PCs, mobile Geräte und einige IoT Core-Geräte (Rasperry Pi 2, Raspberry Pi 3 und DragonBoard). Windows10 on ARM-Desktop-PCs sind eine neue Funktion in die Windows-Produktfamilie. Wenn Sie UWP-App-Entwickler sind, sollten Sie ARM-Pakete für den Store für diese PCs übermitteln.

>[!NOTE]
> Um Ihrer UWP-Anwendung für die ARM64 nativ Zielplattform zu erstellen, müssen Sie Visual Studio 2017 Version 15.9 oder höher verfügen. Weitere Informationen finden Sie in [diesem Blogbeitrag](https://blogs.windows.com/buildingapps/2018/11/15/official-support-for-windows-10-on-arm-development).

Weitere Informationen finden Sie unter [Windows 10 auf ARM](../porting/apps-on-arm.md). Sehen Sie sich diesen //Build-Talk an, um eine Demo zu [Windows10 on ARM](https://channel9.msdn.com/Events/Build/2017/P4171) zu sehen und mehr zu erfahren.

Weitere Informationen zu IoT-Themen finden Sie unter [Bereitstellen einer App mit Visual Studio](https://developer.microsoft.com/windows/iot/Docs/AppDeployment).
