---
author: drewbatgit
ms.assetid: 3b75d881-bdcf-402b-a330-23cd29d68e53
description: "Dieser Artikel enthält eine Liste mit den DeviceInformation-Eigenschaften für Audiogeräte."
title: "Audiogeräte-Informationseigenschaften"
ms.author: drewbat
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 0992c0fc3c6fe9d70b7867275d28e6bba78171ab
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: HT
ms.contentlocale: de-DE
---
# <a name="audio-device-information-properties"></a>Audiogeräte-Informationseigenschaften

Dieser Artikel enthält eine Liste mit den Geräteinformationseigenschaften für Audiogeräte. Unter Windows sind jedem Hardwaregerät [**DeviceInformation**](https://msdn.microsoft.com/library/windows/apps/BR225393)-Eigenschaften mit ausführlichen Geräteinformationen zugeordnet, auf die Sie zurückgreifen können, wenn Sie bestimmte Geräteinformationen benötigen oder eine Geräteauswahl erstellen möchten. Allgemeine Informationen zum Aufzählen von Geräten unter Windows finden Sie unter [Auflisten von Geräten](../devices-sensors/enumerate-devices.md) und [Geräteinformationseigenschaften](../devices-sensors/device-information-properties.md).


|Name|Typ|Beschreibung|
|------------------------------------------------------------|------------|------------------------------------------------------|
|**System.Devices.AudioDevice.Microphone.SensitivityInDbfs**|Double|Gibt die Empfindlichkeit des Mikrofons in Dezibel relativ zu Full-Scale-Einheiten (dBFS) an.|
|**System.Devices.AudioDevice.Microphone.SignalToNoiseRationInDb**|Double|Gibt für das Mikrofon das Signal-Rausch-Verhältnis (SNR) in Dezibeleinheiten (dB) an.|
|**System.Devices.AudioDevice.SpeechProcessingSupported**|Boolean|Gibt an, ob das Audiogerät die Verarbeitung von Sprache unterstützt.|
|**System.Devices.AudioDevice.RawProcessingSupported**|Boolean|Gibt an, ob das Audiogerät die Verarbeitung von Rohdaten unterstützt.|
|**System.Devices.MicrophoneArray.Geometry**|unsigned char[]|Geometriedaten für ein Mikrofonarray.|

## <a name="related-topics"></a>Verwandte Themen

* [Auflisten von Geräten](../devices-sensors/enumerate-devices.md)
* [Geräteinformationseigenschaften](../devices-sensors/device-information-properties.md)
* [Erstellen einer Geräteauswahl](../devices-sensors/build-a-device-selector.md)
* [Medienwiedergabe](media-playback.md)




