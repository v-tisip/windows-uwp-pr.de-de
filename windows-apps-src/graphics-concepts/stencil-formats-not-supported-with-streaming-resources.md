---
title: "Von den Streamingressourcen nicht unterstützte Schablonenformate"
description: "Formate, die Schablonen enthalten, werden von Streamingressourcen nicht unterstützt."
ms.assetid: 90A572A4-3C76-4795-BAE9-FCC72B5F07AD
keywords:
- "Von den Streamingressourcen nicht unterstützte Schablonenformate"
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 96eb1ec610b5aba743caf92584f52f5785046155
ms.lasthandoff: 02/07/2017

---

# <a name="stencil-formats-not-supported-with-streaming-resources"></a>Von den Streamingressourcen nicht unterstützte Schablonenformate


Formate, die Schablonen enthalten, werden von Streamingressourcen nicht unterstützt.

Zu den Formaten, die Schablonen enthalten, gehören DXGI\_FORMAT\_D24\_UNORM\_S8\_UINT (sowie zugehörige Formate in der R24G8-Familie) und DXGI\_FORMAT\_D32\_FLOAT\_S8X24\_UINT (sowie zugehörige Formate in der R32G8X24-Familie).

Einige Implementierungen speichern Tiefen- und Schabloneninformationen in separaten Zuordnungen, andere speichern sie zusammen. Die Kachelverwaltung für die beiden Schemas müsste unterschiedlich sein, und keine API kann die Unterschiede abstrahieren oder rationalisieren. Wir empfehlen für zukünftige Hardware die Unterstützung unabhängiger Tiefen- und Schablonenoberflächen, die voneinander unabhängige Kacheln verwenden.

Die 32-Bit-Tiefe müsste 128 x 128 Kacheln und die 8-Bit Schablone müsste 256 x 256 Kacheln haben. Daher würde es Anwendungen mit einer Diskrepanz in der Kachelform zwischen Tiefe und Schablone geben. Aber das gleiche Problem besteht bereits bei anderen Formaten von Renderzieloberflächen.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Geräte- und prozessübergreifende Streamingressourcen](streaming-resource-cross-process-and-device-sharing.md)

 

 





