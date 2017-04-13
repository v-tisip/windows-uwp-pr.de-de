---
author: drewbatgit
ms.assetid: 3E0FBB43-F6A4-4558-AA89-20E7760BA73F
description: "Dieser Artikel enthält eine Liste der Dynamic Adaptive Streaming over HTTP (DASH)-Profile, die für UWP-Apps unterstützt werden."
title: "Dynamic Adaptive Streaming over HTTP (DASH)-Profilunterstützung"
ms.author: drewbat
ms.date: 02/15/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.openlocfilehash: 9ca8f2d1783a73ae38fed1d3ee1e58b809ddd2aa
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="dynamic-adaptive-streaming-over-http-dash-profile-support"></a>Dynamic Adaptive Streaming over HTTP (DASH)-Profilunterstützung
In der folgenden Tabelle sind die DASH-Profile aufgeführt, die für UWP-Apps unterstützt werden.



|Tag | Manifesttyp | Hinweise|Juliversion von Windows 10|Windows 10, Version 1511|Windows 10, Version 1607 |Windows 10, Version 1607 |Windows 10, Version 1703|
|----------------|------|-------|-----------|--------------|---------|-------|--------|
|urn:mpeg:dash:profile:isoff-live:2011 | Statisch |     |Unterstützt            |  Unterstützt              | Unterstützt        |Unterstützt| Unterstützt|
|urn:mpeg:dash:profile:isoff-main:2011 |        | Beste Leistung | Unterstützt            |  Unterstützt              | Unterstützt        |Unterstützt| Unterstützt|
|urn:mpeg:dash:profile:isoff-live:2011 | Dynamisch | $Time$ wird in Segmentvorlagen unterstützt, aber $Number$ nicht. | Nicht unterstützt            | Nicht unterstützt              | Nicht unterstützt        |Nicht unterstützt| Unterstützt|


## <a name="related-topics"></a>Verwandte Themen

* [Medienwiedergabe](media-playback.md)
* [Adaptives Streaming](adaptive-streaming.md)
 

 




