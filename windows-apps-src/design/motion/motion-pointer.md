---
Description: Use pointer animations to provide users with visual feedback when the user taps on an item.
title: Animationen für Zeigerklicks in UWP-Apps
ms.assetid: EEB10A2C-629A-4705-8468-4D019D74DDFF
ms.date: 08/9/2017
ms.topic: article
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 8cedab3f589f41b791a6c387ec776dc4c8ee23a6
ms.sourcegitcommit: b5c9c18e70625ab770946b8243f3465ee1013184
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "7964710"
---
# <a name="pointer-click-animations"></a><span data-ttu-id="fc229-103">Animationen für Zeigerklicks</span><span class="sxs-lookup"><span data-stu-id="fc229-103">Pointer click animations</span></span>



<span data-ttu-id="fc229-104">Verwenden Sie Zeigeranimationen, um Benutzern visuelles Feedback zu liefern, wenn diese auf ein Element tippen.</span><span class="sxs-lookup"><span data-stu-id="fc229-104">Use pointer animations to provide users with visual feedback when the user taps on an item.</span></span> <span data-ttu-id="fc229-105">Bei der Animation für „Zeiger nach unten“ wird das gedrückte Element leicht verkleinert und geneigt. Sie wird wiedergegeben, wenn erstmalig auf ein Element getippt wird.</span><span class="sxs-lookup"><span data-stu-id="fc229-105">The pointer down animation slightly shrinks and tilts the pressed item, and plays when an item is first tapped.</span></span> <span data-ttu-id="fc229-106">Die Animation für „Zeiger nach oben“, mit der der ursprüngliche Zustand des Elements wiederhergestellt wird, wird beim Loslassen des Zeigers wiedergegeben.</span><span class="sxs-lookup"><span data-stu-id="fc229-106">The pointer up animation, which restores the item to its original position, is played when the user releases the pointer.</span></span>


> <span data-ttu-id="fc229-107">**Wichtige APIs**: [**PointerUpThemeAnimation class**](https://msdn.microsoft.com/library/windows/apps/hh969168), [**PointerDownThemeAnimation class**](https://msdn.microsoft.com/library/windows/apps/hh969164)</span><span class="sxs-lookup"><span data-stu-id="fc229-107">**Important APIs**: [**PointerUpThemeAnimation class**](https://msdn.microsoft.com/library/windows/apps/hh969168), [**PointerDownThemeAnimation class**](https://msdn.microsoft.com/library/windows/apps/hh969164)</span></span>


## <a name="dos-and-donts"></a><span data-ttu-id="fc229-108">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="fc229-108">Do's and don'ts</span></span>

-   <span data-ttu-id="fc229-109">Wenn Sie eine Animation für „Zeiger hoch“ verwenden, sollte die Animation ausgelöst werden, nachdem der Benutzer den Zeiger losgelassen hat.</span><span class="sxs-lookup"><span data-stu-id="fc229-109">When you use a pointer up animation, immediately trigger the animation when the user releases the pointer.</span></span> <span data-ttu-id="fc229-110">Auf diese Weise erhalten Benutzer umgehend Feedback, dass ihre Aktion erkannt wurde. Dies gilt auch, wenn die durch das Tippen ausgelöste Aktion (beispielsweise das Navigieren zu einer neuen Seite) langsamer reagiert.</span><span class="sxs-lookup"><span data-stu-id="fc229-110">This provides instant feedback to the user that their action has been recognized, even if the action triggered by the tap (such as navigating to a new page) is slower to respond.</span></span>

## <a name="related-articles"></a><span data-ttu-id="fc229-111">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="fc229-111">Related articles</span></span>

* [<span data-ttu-id="fc229-112">Übersicht über Animationen</span><span class="sxs-lookup"><span data-stu-id="fc229-112">Animations overview</span></span>](https://msdn.microsoft.com/library/windows/apps/mt187350)
* [<span data-ttu-id="fc229-113">Animieren von Zeigerklicks</span><span class="sxs-lookup"><span data-stu-id="fc229-113">Animating pointer clicks</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/jj649432)
* [<span data-ttu-id="fc229-114">Schnellstart: Animieren der Benutzeroberfläche mithilfe von Bibliotheksanimationen</span><span class="sxs-lookup"><span data-stu-id="fc229-114">Quickstart: Animating your UI using library animations</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh452703)
* [**<span data-ttu-id="fc229-115">PointerUpThemeAnimation-Klasse</span><span class="sxs-lookup"><span data-stu-id="fc229-115">PointerUpThemeAnimation class</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh969168)
* [**<span data-ttu-id="fc229-116">PointerDownThemeAnimation-Klasse</span><span class="sxs-lookup"><span data-stu-id="fc229-116">PointerDownThemeAnimation class</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh969164)

 

 




