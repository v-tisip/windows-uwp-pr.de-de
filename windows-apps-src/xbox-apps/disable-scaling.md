---
title: So deaktivieren Sie die Skalierung
description: Anleitung zum Deaktivieren des Standard-Skalierungsfaktors.
ms.date: 02/08/2017
ms.topic: article
keywords: windows 10, uwp
ms.assetid: 6e68c1fc-a407-4c0b-b0f4-e445ccb72ff3
ms.localizationpriority: medium
ms.openlocfilehash: 44688ff40792ba2ee72cbd1d96bae1ac59834efa
ms.sourcegitcommit: b4c502d69a13340f6e3c887aa3c26ef2aeee9cee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "8464757"
---
# <a name="how-to-turn-off-scaling"></a><span data-ttu-id="3f54a-104">So deaktivieren Sie die Skalierung</span><span class="sxs-lookup"><span data-stu-id="3f54a-104">How to turn off scaling</span></span>   
<span data-ttu-id="3f54a-105">Standardmäßig werden Anwendungen für XAML-Apps auf 200Prozent und für HTML-Apps auf 150Prozent skaliert.</span><span class="sxs-lookup"><span data-stu-id="3f54a-105">By default, applications are scaled to 200% for XAML and 150% for HTML apps.</span></span> <span data-ttu-id="3f54a-106">Der Standardskalierungsfaktor kann deaktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="3f54a-106">It is possible to turn off the default scale factor.</span></span> <span data-ttu-id="3f54a-107">Infolgedessen verwendet die Anwendung die tatsächlichen Pixelabmessungen des Geräts (1910 x 1080Pixel).</span><span class="sxs-lookup"><span data-stu-id="3f54a-107">This will cause your application to use the actual pixel dimensions of the device (1910 x 1080 pixels).</span></span>   
   
## <a name="html"></a><span data-ttu-id="3f54a-108">HTML</span><span class="sxs-lookup"><span data-stu-id="3f54a-108">HTML</span></span>   
<span data-ttu-id="3f54a-109">Sie können den Skalierungsfaktor deaktivieren, indem Sie den folgenden Codeausschnitt verwenden:</span><span class="sxs-lookup"><span data-stu-id="3f54a-109">You can opt out of scale factor by using the following code snippet:</span></span> 
   
```
var result = Windows.UI.ViewManagement.ApplicationViewScaling.trySetDisableLayoutScaling(true);
```

<span data-ttu-id="3f54a-110">Oder Sie können eine für das Web geeignete Methode verwenden:</span><span class="sxs-lookup"><span data-stu-id="3f54a-110">Or, you can use a web-friendly method:</span></span>   

```   
@media (max-height: 1080px) {   
    @-ms-viewport {   
        height: 1080px;   
    }   
}   
```

## <a name="xaml"></a><span data-ttu-id="3f54a-111">XAML</span><span class="sxs-lookup"><span data-stu-id="3f54a-111">XAML</span></span>
<span data-ttu-id="3f54a-112">Sie können den Skalierungsfaktor deaktivieren, indem Sie den folgenden Codeausschnitt verwenden:</span><span class="sxs-lookup"><span data-stu-id="3f54a-112">You can opt out of scale factor by using the following code snippet:</span></span>   
   
```
bool result = Windows.UI.ViewManagement.ApplicationViewScaling.TrySetDisableLayoutScaling(true);
```
   
## <a name="directxc"></a><span data-ttu-id="3f54a-113">DirectX/C++</span><span class="sxs-lookup"><span data-stu-id="3f54a-113">DirectX/C++</span></span>   
<span data-ttu-id="3f54a-114">DirectX-/C++-Anwendungen werden nicht skaliert.</span><span class="sxs-lookup"><span data-stu-id="3f54a-114">DirectX/C++ applications are not scaled.</span></span> <span data-ttu-id="3f54a-115">Die automatische Skalierung gilt nur für HTML- und XAML-Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="3f54a-115">Automatic scaling only applies to HTML and XAML applications.</span></span>  

## <a name="see-also"></a><span data-ttu-id="3f54a-116">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3f54a-116">See also</span></span>
- [<span data-ttu-id="3f54a-117">Bewährte Methoden für Xbox</span><span class="sxs-lookup"><span data-stu-id="3f54a-117">Best practices for Xbox</span></span>](tailoring-for-xbox.md)
- [<span data-ttu-id="3f54a-118">UWP auf XboxOne</span><span class="sxs-lookup"><span data-stu-id="3f54a-118">UWP on Xbox One</span></span>](index.md)
