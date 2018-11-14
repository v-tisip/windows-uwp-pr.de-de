---
author: payzer
title: So wird's gemacht - Zeichnen der Benutzeroberfläche bis zum Bildschirmrand
description: So deaktivieren Sie die automatische Skalierung für den Titelschutzbereich.
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.assetid: 1adb221f-6f70-4255-9329-2046a486ca45
ms.localizationpriority: medium
ms.openlocfilehash: 32932845db47ed47b7e80f68cf4e424ba97e85c0
ms.sourcegitcommit: 38f06f1714334273d865935d9afb80efffe97a17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6192211"
---
# <a name="how-to-draw-ui-to-the-edge-of-the-screen"></a>So wird's gemacht - Zeichnen der Benutzeroberfläche bis zum Bildschirmrand   
Standardmäßig befinden sich die Begrenzungen von Anwendungen an den Rändern des Viewports, um den fernsehsicheren Bereich zu berücksichtigen (Weitere Informationen finden Sie unter [Entwerfen für Xbox und Fernsehgeräte](../design/devices/designing-for-tv.md#tv-safe-area)). 

Wir empfehlen, diese Option zu deaktivieren und bis zum Bildschirmrand zu zeichnen. Wenn Sie bis zum Bildschirmrand zeichnen möchten, fügen Sie den folgenden Code hinzu, wenn die Anwendung gestartet wird:
   
```
Windows.UI.ViewManagement.ApplicationView.GetForCurrentView().SetDesiredBoundsMode(Windows.UI.ViewManagement.ApplicationViewBoundsMode.UseCoreWindow);
```
   
> [!NOTE]
> Für C++-/DirectX-Anwendungen ist dies nicht relevant. Das System rendert die Anwendung immer bis zum Bildschirmrand.

## <a name="see-also"></a>Weitere Informationen
- [Bewährte Methoden für Xbox](tailoring-for-xbox.md)
- [UWP auf XboxOne](index.md)
