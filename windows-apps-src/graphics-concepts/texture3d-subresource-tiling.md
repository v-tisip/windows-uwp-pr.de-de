---
title: Unterteilung von Texture3D-Unterressourcen
description: Diese Tabelle zeigt die Unterteilung von Texture3D-Unterressourcen.
ms.assetid: 210D03E4-CF12-47E0-BA2F-C8D059B17D3E
keywords:
- Unterteilung von Texture3D-Unterressourcen
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: c9c232bc60bbbb3cccc16618d82ec23452c58ee8
ms.sourcegitcommit: b4c502d69a13340f6e3c887aa3c26ef2aeee9cee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "8478219"
---
# <a name="texture3d-subresource-tiling"></a>Unterteilung von Texture3D-Unterressourcen


Diese Tabelle zeigt die Unterteilung von [**Texture3D**](https://msdn.microsoft.com/library/windows/desktop/ff471562)-Unterressourcen. Die Werte in dieser Tabelle berücksichtigen keine Tail-MIP-Verpackungen.

Diese Tabelle nimmt die [**Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff471525)-Unterteilung und dividiert die x/y-Dimensionen jeweils durch 4 und fügt 16 Tiefenebenen hinzu. Alle Kacheln für die erste Ebene (2D-Kachelebene, die die ersten 16 Tiefenebenen definiert) erscheinen vor allen folgenden Ebenen.

**Hinweis:** [**Texture3D**](https://msdn.microsoft.com/library/windows/desktop/ff471562) -Unterstützung in Streamingressourcen ist in der ursprünglichen Implementierung der streaming-Ressourcen verfügbar, aber die gewünschten kachelformen werden hier aufgeführt, in einer zukünftigen Version möglicherweise unterstützt.

 

| Bits/Pixel (1Sample/Pixel) | Kachelabmessungen (Pixel, B x H x T) |
|-----------------------------|---------------------------------|
| 8                           | 64 x 32 x 32                        |
| 16                          | 32 x 32 x 32                        |
| 32                          | 32 x 32 x 16                        |
| 64                          | 32 x 16 x 16                        |
| 128                         | 16 x 16 x 16                        |
| BC1, 4                       | 128 x 64 x 16                       |
| BC2, 3, 5, 6, 7                 | 64 x 64 x 16                        |

 

Format-Bitanzahlen, die bei Streamingressourcen nicht unterstützt werden, sind 96-bpp-Formate, Videoformate, DXGI\_FORMAT\_R1\_UNORM, DXGI\_FORMAT\_R8G8\_B8G8\_UNORM, and DXGI\_FORMAT\_R8R8\_G8B8\_UNORM.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[So unterteilen Sie den Bereich einer Streamingressource](how-a-streaming-resource-s-area-is-tiled.md)

 

 




