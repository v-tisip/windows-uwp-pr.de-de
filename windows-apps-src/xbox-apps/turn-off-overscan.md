---
title: So wird's gemacht - Zeichnen der Benutzeroberfläche bis zum Bildschirmrand
description: So deaktivieren Sie die automatische Skalierung für den Titelschutzbereich.
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.assetid: 1adb221f-6f70-4255-9329-2046a486ca45
ms.localizationpriority: medium
ms.openlocfilehash: 1ac49d80f1d99a56eff565a0daa8f2f3e9289636
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "8215458"
---
# <a name="how-to-draw-ui-to-the-edge-of-the-screen"></a><span data-ttu-id="836a4-104">So wird's gemacht - Zeichnen der Benutzeroberfläche bis zum Bildschirmrand</span><span class="sxs-lookup"><span data-stu-id="836a4-104">How to draw UI to the edge of the screen</span></span>   
<span data-ttu-id="836a4-105">Standardmäßig befinden sich die Begrenzungen von Anwendungen an den Rändern des Viewports, um den fernsehsicheren Bereich zu berücksichtigen (Weitere Informationen finden Sie unter [Entwerfen für Xbox und Fernsehgeräte](../design/devices/designing-for-tv.md#tv-safe-area)).</span><span class="sxs-lookup"><span data-stu-id="836a4-105">By default, applications will have borders placed at the edges of the viewport to account for the TV-safe area (for more information, see [Designing for Xbox and TV](../design/devices/designing-for-tv.md#tv-safe-area)).</span></span> 

<span data-ttu-id="836a4-106">Wir empfehlen, diese Option zu deaktivieren und bis zum Bildschirmrand zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="836a4-106">We recommend turning this off and drawing to the edge of the screen.</span></span> <span data-ttu-id="836a4-107">Wenn Sie bis zum Bildschirmrand zeichnen möchten, fügen Sie den folgenden Code hinzu, wenn die Anwendung gestartet wird:</span><span class="sxs-lookup"><span data-stu-id="836a4-107">You can draw to the edge of the screen by adding the following code when your application starts:</span></span>
   
```
Windows.UI.ViewManagement.ApplicationView.GetForCurrentView().SetDesiredBoundsMode(Windows.UI.ViewManagement.ApplicationViewBoundsMode.UseCoreWindow);
```
   
> [!NOTE]
> <span data-ttu-id="836a4-108">Für C++-/DirectX-Anwendungen ist dies nicht relevant.</span><span class="sxs-lookup"><span data-stu-id="836a4-108">C++/DirectX applications do not have to worry about this.</span></span> <span data-ttu-id="836a4-109">Das System rendert die Anwendung immer bis zum Bildschirmrand.</span><span class="sxs-lookup"><span data-stu-id="836a4-109">The system will always render your application to the edge of the screen.</span></span>

## <a name="see-also"></a><span data-ttu-id="836a4-110">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="836a4-110">See also</span></span>
- [<span data-ttu-id="836a4-111">Bewährte Methoden für Xbox</span><span class="sxs-lookup"><span data-stu-id="836a4-111">Best practices for Xbox</span></span>](tailoring-for-xbox.md)
- [<span data-ttu-id="836a4-112">UWP auf XboxOne</span><span class="sxs-lookup"><span data-stu-id="836a4-112">UWP on Xbox One</span></span>](index.md)
