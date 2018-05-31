---
author: drewbatgit
ms.assetid: 3b75d881-bdcf-402b-a330-23cd29d68e53
description: Dieser Artikel enthält eine Liste mit den DeviceInformation-Eigenschaften für Audiogeräte.
title: Audiogeräte-Informationseigenschaften
ms.author: drewbat
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: c221e3d77419ca02b46e8be227f3b943fe8dc241
ms.sourcegitcommit: ef5a1e1807313a2caa9c9b35ea20b129ff7155d0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
ms.locfileid: "1639010"
---
# <a name="audio-device-information-properties"></a>Audiogeräte-Informationseigenschaften

Dieser Artikel enthält eine Liste mit den Geräteinformationseigenschaften für Audiogeräte. Unter Windows sind jedem Hardwaregerät [**DeviceInformation**](https://msdn.microsoft.com/library/windows/apps/BR225393)-Eigenschaften mit ausführlichen Geräteinformationen zugeordnet, auf die Sie zurückgreifen können, wenn Sie bestimmte Geräteinformationen benötigen oder eine Geräteauswahl erstellen möchten. Allgemeine Informationen zum Aufzählen von Geräten unter Windows finden Sie unter [Auflisten von Geräten](../devices-sensors/enumerate-devices.md) und [Geräteinformationseigenschaften](../devices-sensors/device-information-properties.md).


|Name|Typ|Beschreibung|
|------------------------------------------------------------|------------|------------------------------------------------------|
|**System.Devices.AudioDevice.Microphone.SensitivityInDbfs**|Double|Gibt die Empfindlichkeit des Mikrofons in Dezibel relativ zu Full-Scale-Einheiten (dBFS) an.|
|**System.Devices.AudioDevice.Microphone.SignalToNoiseRatioInDb**|Double|Gibt für das Mikrofon das Signal-Rausch-Verhältnis (SNR) in Dezibeleinheiten (dB) an.|
|**System.Devices.AudioDevice.SpeechProcessingSupported**|Boolean|Gibt an, ob das Audiogerät die Verarbeitung von Sprache unterstützt.|
|**System.Devices.AudioDevice.RawProcessingSupported**|Boolean|Gibt an, ob das Audiogerät die Verarbeitung von Rohdaten unterstützt.|
|**System.Devices.MicrophoneArray.Geometry**|unsigned char[]|Geometriedaten für ein Mikrofonarray.|

## <a name="related-topics"></a>Verwandte Themen

* [Auflisten von Geräten](../devices-sensors/enumerate-devices.md)
* [Geräteinformationseigenschaften](../devices-sensors/device-information-properties.md)
* [Erstellen einer Geräteauswahl](../devices-sensors/build-a-device-selector.md)
* [Medienwiedergabe](media-playback.md)




