---
author: drewbatgit
ms.assetid: 3E0FBB43-F6A4-4558-AA89-20E7760BA73F
description: Dieser Artikel enthält eine Liste der Dynamic Adaptive Streaming over HTTP (DASH)-Profile, die für UWP-Apps unterstützt werden.
title: Dynamic Adaptive Streaming over HTTP (DASH)-Profilunterstützung
ms.author: drewbat
ms.date: 02/15/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: c411d479430f793d85863f66c64758155b8a5758
ms.sourcegitcommit: 517c83baffd344d4c705bc644d7c6d2b1a4c7e1a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
ms.locfileid: "1842337"
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
 

 




