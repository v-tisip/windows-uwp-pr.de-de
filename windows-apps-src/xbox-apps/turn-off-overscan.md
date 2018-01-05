---
author: payzer
title: "So wird&quot;s gemacht - Zeichnen der Benutzeroberfläche bis zum Bildschirmrand"
description: "So deaktivieren Sie die automatische Skalierung für den Titelschutzbereich."
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.assetid: 1adb221f-6f70-4255-9329-2046a486ca45
ms.openlocfilehash: 30fc3e357eaea0d36a5deba1b0ea85c2d9bc990e
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: HT
ms.contentlocale: de-DE
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
- [UWP auf XboxOne](index.md)
