---
ms.assetid: 3b75d881-bdcf-402b-a330-23cd29d68e53
description: Dieser Artikel enthält eine Liste mit den DeviceInformation-Eigenschaften für Audiogeräte.
title: Audiogeräte-Informationseigenschaften
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 443bcc3c0280aca85de31d8c9f3704302432cb76
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "8203868"
---
# <a name="audio-device-information-properties"></a><span data-ttu-id="a080c-104">Audiogeräte-Informationseigenschaften</span><span class="sxs-lookup"><span data-stu-id="a080c-104">Audio device information properties</span></span>

<span data-ttu-id="a080c-105">Dieser Artikel enthält eine Liste mit den Geräteinformationseigenschaften für Audiogeräte.</span><span class="sxs-lookup"><span data-stu-id="a080c-105">This article lists the device information properties related to audio devices.</span></span> <span data-ttu-id="a080c-106">Unter Windows sind jedem Hardwaregerät [**DeviceInformation**](https://msdn.microsoft.com/library/windows/apps/BR225393)-Eigenschaften mit ausführlichen Geräteinformationen zugeordnet, auf die Sie zurückgreifen können, wenn Sie bestimmte Geräteinformationen benötigen oder eine Geräteauswahl erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="a080c-106">On Windows, each hardware device has associated [**DeviceInformation**](https://msdn.microsoft.com/library/windows/apps/BR225393) properties providing detailed information about a device that you can use when you need specific information about the device or when you are building a device selector.</span></span> <span data-ttu-id="a080c-107">Allgemeine Informationen zum Aufzählen von Geräten unter Windows finden Sie unter [Auflisten von Geräten](../devices-sensors/enumerate-devices.md) und [Geräteinformationseigenschaften](../devices-sensors/device-information-properties.md).</span><span class="sxs-lookup"><span data-stu-id="a080c-107">For general information about enumerating devices on Windows, see [Enumerate devices](../devices-sensors/enumerate-devices.md) and [Device information properties](../devices-sensors/device-information-properties.md).</span></span>


|<span data-ttu-id="a080c-108">Name</span><span class="sxs-lookup"><span data-stu-id="a080c-108">Name</span></span>|<span data-ttu-id="a080c-109">Typ</span><span class="sxs-lookup"><span data-stu-id="a080c-109">Type</span></span>|<span data-ttu-id="a080c-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a080c-110">Description</span></span>|
|------------------------------------------------------------|------------|------------------------------------------------------|
|**<span data-ttu-id="a080c-111">System.Devices.AudioDevice.Microphone.SensitivityInDbfs</span><span class="sxs-lookup"><span data-stu-id="a080c-111">System.Devices.AudioDevice.Microphone.SensitivityInDbfs</span></span>**|<span data-ttu-id="a080c-112">Double</span><span class="sxs-lookup"><span data-stu-id="a080c-112">Double</span></span>|<span data-ttu-id="a080c-113">Gibt die Empfindlichkeit des Mikrofons in Dezibel relativ zu Full-Scale-Einheiten (dBFS) an.</span><span class="sxs-lookup"><span data-stu-id="a080c-113">Specifies the microphone sensitivity in decibels relative to full scale (dBFS) units.</span></span>|
|**<span data-ttu-id="a080c-114">System.Devices.AudioDevice.Microphone.SignalToNoiseRatioInDb</span><span class="sxs-lookup"><span data-stu-id="a080c-114">System.Devices.AudioDevice.Microphone.SignalToNoiseRatioInDb</span></span>**|<span data-ttu-id="a080c-115">Double</span><span class="sxs-lookup"><span data-stu-id="a080c-115">Double</span></span>|<span data-ttu-id="a080c-116">Gibt für das Mikrofon das Signal-Rausch-Verhältnis (SNR) in Dezibeleinheiten (dB) an.</span><span class="sxs-lookup"><span data-stu-id="a080c-116">Specifies the microphone signal to noise ratio (SNR) measured in decibel (dB) units.</span></span>|
|**<span data-ttu-id="a080c-117">System.Devices.AudioDevice.SpeechProcessingSupported</span><span class="sxs-lookup"><span data-stu-id="a080c-117">System.Devices.AudioDevice.SpeechProcessingSupported</span></span>**|<span data-ttu-id="a080c-118">Boolean</span><span class="sxs-lookup"><span data-stu-id="a080c-118">Boolean</span></span>|<span data-ttu-id="a080c-119">Gibt an, ob das Audiogerät die Verarbeitung von Sprache unterstützt.</span><span class="sxs-lookup"><span data-stu-id="a080c-119">Indicates whether the audio device supports speech processing.</span></span>|
|**<span data-ttu-id="a080c-120">System.Devices.AudioDevice.RawProcessingSupported</span><span class="sxs-lookup"><span data-stu-id="a080c-120">System.Devices.AudioDevice.RawProcessingSupported</span></span>**|<span data-ttu-id="a080c-121">Boolean</span><span class="sxs-lookup"><span data-stu-id="a080c-121">Boolean</span></span>|<span data-ttu-id="a080c-122">Gibt an, ob das Audiogerät die Verarbeitung von Rohdaten unterstützt.</span><span class="sxs-lookup"><span data-stu-id="a080c-122">Indicates whether the audio device supports raw processing.</span></span>|
|**<span data-ttu-id="a080c-123">System.Devices.MicrophoneArray.Geometry</span><span class="sxs-lookup"><span data-stu-id="a080c-123">System.Devices.MicrophoneArray.Geometry</span></span>**|<span data-ttu-id="a080c-124">unsigned char[]</span><span class="sxs-lookup"><span data-stu-id="a080c-124">unsigned char[]</span></span>|<span data-ttu-id="a080c-125">Geometriedaten für ein Mikrofonarray.</span><span class="sxs-lookup"><span data-stu-id="a080c-125">Geometry data for a microphone array.</span></span>|

## <a name="related-topics"></a><span data-ttu-id="a080c-126">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="a080c-126">Related topics</span></span>

* [<span data-ttu-id="a080c-127">Auflisten von Geräten</span><span class="sxs-lookup"><span data-stu-id="a080c-127">Enumerate devices</span></span>](../devices-sensors/enumerate-devices.md)
* [<span data-ttu-id="a080c-128">Geräteinformationseigenschaften</span><span class="sxs-lookup"><span data-stu-id="a080c-128">Device information properties</span></span>](../devices-sensors/device-information-properties.md)
* [<span data-ttu-id="a080c-129">Erstellen einer Geräteauswahl</span><span class="sxs-lookup"><span data-stu-id="a080c-129">Build a device selector</span></span>](../devices-sensors/build-a-device-selector.md)
* [<span data-ttu-id="a080c-130">Medienwiedergabe</span><span class="sxs-lookup"><span data-stu-id="a080c-130">Media playback</span></span>](media-playback.md)




