---
author: payzer
title: "So wird&quot;s gemacht - Zeichnen der Benutzeroberfläche bis zum Bildschirmrand"
description: 
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP"
ms.assetid: 1adb221f-6f70-4255-9329-2046a486ca45
translationtype: Human Translation
ms.sourcegitcommit: 5645eee3dc2ef67b5263b08800b0f96eb8a0a7da
ms.openlocfilehash: 9a221672391dfbfb4af664438448307800020c6f
ms.lasthandoff: 02/08/2017

---

# <a name="how-to-draw-ui-to-the-edge-of-the-screen"></a>So wird's gemacht - Zeichnen der Benutzeroberfläche bis zum Bildschirmrand   
Standardmäßig befinden sich die Begrenzungen von Anwendungen an den Rändern des Viewports, um den fernsehsicheren Bereich zu berücksichtigen (Weitere Informationen finden Sie unter [Entwerfen für Xbox und Fernsehgeräte](../input-and-devices/designing-for-tv.md#tv-safe-area)). 

Wir empfehlen, diese Option zu deaktivieren und bis zum Bildschirmrand zu zeichnen. Wenn Sie bis zum Bildschirmrand zeichnen möchten, fügen Sie den folgenden Code hinzu, wenn die Anwendung gestartet wird:
   
```
Windows.UI.ViewManagement.ApplicationView.GetForCurrentView().SetDesiredBoundsMode(Windows.UI.ViewManagement.ApplicationViewBoundsMode.UseCoreWindow);
```
   
> [!NOTE]
> Für C++-/DirectX-Anwendungen ist dies nicht relevant. Das System rendert die Anwendung immer bis zum Bildschirmrand.

## <a name="see-also"></a>Weitere Informationen
- [Bewährte Methoden für Xbox](tailoring-for-xbox.md)
- [UWP auf Xbox One](index.md)

