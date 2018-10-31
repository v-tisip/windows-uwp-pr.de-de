---
author: drewbatgit
ms.assetid: 3E0FBB43-F6A4-4558-AA89-20E7760BA73F
description: Dieser Artikel enthält eine Liste der Dynamic Adaptive Streaming over HTTP (DASH)-Profile, die für UWP-Apps unterstützt werden.
title: Dynamic Adaptive Streaming over HTTP (DASH)-Profilunterstützung
ms.author: drewbat
ms.date: 02/15/2017
ms.topic: article
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 7a4ec9f9e81010d39af496da156afa676f4b3714
ms.sourcegitcommit: ca96031debe1e76d4501621a7680079244ef1c60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5839447"
---
# <a name="dynamic-adaptive-streaming-over-http-dash-profile-support"></a>Dynamic Adaptive Streaming over HTTP (DASH)-Profilunterstützung


## <a name="supported-dash-profiles"></a>Unterstützte DASH-Profile
In der folgenden Tabelle sind die DASH-Profile aufgeführt, die für UWP-Apps unterstützt werden.

|Tag | Manifesttyp | Hinweise|Juliversion von Windows 10|Windows 10, Version 1511|Windows 10, Version 1607 |Windows 10, Version 1607 |Windows 10, Version 1703|
|----------------|------|-------|-----------|--------------|---------|-------|--------|
|urn:mpeg&#58;dash:profile:isoff-live:2011 | Statisch |     |Unterstützt            |  Unterstützt              | Unterstützt        |Unterstützt| Unterstützt|
|urn:mpeg&#58;dash:profile:isoff-main:2011 |        | Beste Leistung | Unterstützt            |  Unterstützt              | Unterstützt        |Unterstützt| Unterstützt|
|urn:mpeg&#58;dash:profile:isoff-live:2011 | Dynamisch | $Time$ wird in Segmentvorlagen unterstützt, aber $Number$ nicht. | Nicht unterstützt            | Nicht unterstützt              | Nicht unterstützt        |Nicht unterstützt| Unterstützt|


## <a name="unsupported-dash-profiles"></a>Nicht unterstützte DASH-Profile
Profile, die nicht in der obigen Tabelle aufgeführt sind, werden nicht unterstützt, einschließlich, aber nicht beschränkt auf folgende:

* urn:mpeg&#58;dash:profile:full:2011
* urn:mpeg&#58;dash:profile:isoff-on-demand:2011
* urn:mpeg&#58;dash:profile:mp2t-main:2011
* urn:mpeg&#58;dash:profile:mp2t-simple:2011


## <a name="related-topics"></a>Verwandte Themen

* [Medienwiedergabe](media-playback.md)
* [Adaptives Streaming](adaptive-streaming.md)
 

 




