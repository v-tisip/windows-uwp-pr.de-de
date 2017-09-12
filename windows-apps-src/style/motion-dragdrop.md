---
author: mijacobs
Description: Verwenden Sie Drag & Drop-Animationen, wenn Benutzer Objekte verschieben, z. B. wenn sie ein Element innerhalb einer Liste verschieben oder ein Element auf einem anderen ablegen.
title: "Animationen für Drag & Drop-Vorgang in UWP-Apps"
ms.assetid: 6064755F-6E24-4901-A4FF-263F05F0DFD6
label: Motion--Drag and drop
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 78e50f411534997cfb06e574fc52e62e1a7bba39
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="drag-animations"></a><span data-ttu-id="c0863-104">Animationen für Drag & Drop-Vorgang</span><span class="sxs-lookup"><span data-stu-id="c0863-104">Drag animations</span></span>


<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

<span data-ttu-id="c0863-105">Verwenden Sie Drag & Drop-Animationen, wenn Benutzer Objekte verschieben, z. B. wenn sie ein Element innerhalb einer Liste verschieben oder ein Element auf einem anderen ablegen.</span><span class="sxs-lookup"><span data-stu-id="c0863-105">Use drag-and-drop animations when users move objects, such as moving an item within a list, or dropping an item on top of another.</span></span>

<div class="important-apis" >
<b><span data-ttu-id="c0863-106">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="c0863-106">Important APIs</span></span></b><br/>
<ul>
<li>[**<span data-ttu-id="c0863-107">DragItemThemeAnimation-Klasse</span><span class="sxs-lookup"><span data-stu-id="c0863-107">DragItemThemeAnimation class</span></span>**](https://msdn.microsoft.com/library/windows/apps/br243174)</li>
</ul>
</div>


## <a name="dos-and-donts"></a><span data-ttu-id="c0863-108">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="c0863-108">Do's and don'ts</span></span>


**<span data-ttu-id="c0863-109">Animation für das Starten des Ziehens</span><span class="sxs-lookup"><span data-stu-id="c0863-109">Drag start animation</span></span>**

-   <span data-ttu-id="c0863-110">Verwenden Sie die Animation für das Starten des Ziehens, wenn Benutzer beginnen, ein Objekt zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="c0863-110">Use the drag start animation when the user begins to move an object.</span></span>
-   <span data-ttu-id="c0863-111">Nehmen Sie betroffene Objekte nur dann in die Animation auf, wenn andere Objekte vorhanden sind, die von dem Drag & Drop-Vorgang betroffen sein können.</span><span class="sxs-lookup"><span data-stu-id="c0863-111">Include affected objects in the animation if and only if there are other objects that can be affected by the drag-and-drop operation.</span></span>
-   <span data-ttu-id="c0863-112">Verwenden Sie die Animation für das Beenden des Ziehens, um eine mit der Animation für das Starten des Ziehens begonnene Animationssequenz abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="c0863-112">Use the drag end animation to complete any animation sequence that began with the drag start animation.</span></span> <span data-ttu-id="c0863-113">Dadurch wird die Größenänderung des gezogenen Objekts, die durch die Animation für das Starten des Ziehens ausgelöst wurde, zurückgesetzt.</span><span class="sxs-lookup"><span data-stu-id="c0863-113">This reverses the size change in the dragged object that was caused by the drag start animation.</span></span>

**<span data-ttu-id="c0863-114">Animation für das Beenden des Ziehens</span><span class="sxs-lookup"><span data-stu-id="c0863-114">Drag end animation</span></span>**

-   <span data-ttu-id="c0863-115">Verwenden Sie die Animation für das Beenden des Ziehens, wenn Benutzer ein gezogenes Objekt ablegen.</span><span class="sxs-lookup"><span data-stu-id="c0863-115">Use the drag end animation when the user drops a dragged object.</span></span>
-   <span data-ttu-id="c0863-116">Verwenden Sie die Animation für das Beenden des Ziehens zusammen mit Animationen für das Hinzufügen und Löschen bei Listen.</span><span class="sxs-lookup"><span data-stu-id="c0863-116">Use the drag end animation in combination with add and delete animations for lists.</span></span>
-   <span data-ttu-id="c0863-117">Nehmen Sie betroffene Objekte nur dann in die Animation für das Beenden des Ziehens auf, wenn Sie die gleichen Objekte in die Animation für das Starten des Ziehens aufgenommen haben.</span><span class="sxs-lookup"><span data-stu-id="c0863-117">Include affected objects in the drag end animation if and only if you included those same affected objects in the drag start animation.</span></span>
-   <span data-ttu-id="c0863-118">Verwenden Sie die Animation für das Beenden des Ziehens nicht, wenn Sie vorher nicht die Animation für das Starten des Ziehens verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="c0863-118">Don't use the drag end animation if you have not first used the drag start animation.</span></span> <span data-ttu-id="c0863-119">Sie müssen beide Animationen verwenden, damit die Objekte nach Abschluss der Ziehsequenz wieder zu ihrer ursprünglichen Größe zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="c0863-119">You need to use both animations to return objects to their original sizes after the drag sequence is complete.</span></span>

**<span data-ttu-id="c0863-120">Animation für das Starten des Zwischenziehens</span><span class="sxs-lookup"><span data-stu-id="c0863-120">Drag between enter animation</span></span>**

-   <span data-ttu-id="c0863-121">Verwenden Sie die Animation für das Starten des Zwischenziehens, wenn Benutzer die Ziehquelle in einen Ablagebereich ziehen, in dem sie zwischen zwei anderen Objekten abgelegt werden kann.</span><span class="sxs-lookup"><span data-stu-id="c0863-121">Use the drag between enter animation when the user drags the drag source into a drop area where it can be dropped between two other objects.</span></span>
-   <span data-ttu-id="c0863-122">Wählen Sie einen angemessenen Zielbereich zum Ablegen aus.</span><span class="sxs-lookup"><span data-stu-id="c0863-122">Choose a reasonable drop target area.</span></span> <span data-ttu-id="c0863-123">Dieser Bereich sollte nicht so klein sein, dass es den Benutzern schwerfällt, die Ziehquelle zum Ablegen zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="c0863-123">This area should not be so small that it is difficult for the user to position the drag source for the drop.</span></span>
-   <span data-ttu-id="c0863-124">Als Richtung für das Verschieben betroffener Objekte, um den Ablagebereich anzuzeigen, empfiehlt es sich, die Objekte direkt auseinanderzuziehen.</span><span class="sxs-lookup"><span data-stu-id="c0863-124">The recommended direction to move affected objects to show the drop area is directly apart from each other.</span></span> <span data-ttu-id="c0863-125">Ob es sich um eine vertikale oder horizontale Bewegung handelt, hängt davon ab, wie die betroffenen Objekte zueinander ausgerichtet sind.</span><span class="sxs-lookup"><span data-stu-id="c0863-125">Whether they move vertically or horizontally depends on the orientation of the affected objects to each other.</span></span>
-   <span data-ttu-id="c0863-126">Verwenden Sie die Animation für das Starten des Zwischenziehens nicht, wenn die Ziehquelle nicht in einem Bereich abgelegt werden kann.</span><span class="sxs-lookup"><span data-stu-id="c0863-126">Don't use the drag between enter animation if the drag source cannot be dropped in an area.</span></span> <span data-ttu-id="c0863-127">An der Animation für das Starten des Zwischenziehens erkennen Benutzer, dass die Ziehquelle zwischen den betroffenen Objekten abgelegt werden kann.</span><span class="sxs-lookup"><span data-stu-id="c0863-127">The drag between enter animation tells the user that the drag source can be dropped between the affected objects.</span></span>

**<span data-ttu-id="c0863-128">Animation für das Beenden des Zwischenziehens</span><span class="sxs-lookup"><span data-stu-id="c0863-128">Drag between leave animation</span></span>**

-   <span data-ttu-id="c0863-129">Verwenden Sie die Animation für das Beenden des Zwischenziehens, wenn Benutzer ein Objekt von einem Bereich wegziehen, in dem es zwischen zwei anderen Objekten abgelegt werden könnte.</span><span class="sxs-lookup"><span data-stu-id="c0863-129">Use the drag between leave animation when the user drags an object away from an area where it could have been dropped between two other objects.</span></span>
-   <span data-ttu-id="c0863-130">Verwenden Sie die Animation für das Beenden des Zwischenziehens nicht, wenn Sie zuvor nicht die Animation für das Starten des Zwischenziehens verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="c0863-130">Don't use the drag between leave animation if you have not first used the drag between enter animation.</span></span>


## <a name="related-articles"></a><span data-ttu-id="c0863-131">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="c0863-131">Related articles</span></span>

**<span data-ttu-id="c0863-132">Für Entwickler</span><span class="sxs-lookup"><span data-stu-id="c0863-132">For developers</span></span>**
* [<span data-ttu-id="c0863-133">Übersicht über Animationen</span><span class="sxs-lookup"><span data-stu-id="c0863-133">Animations overview</span></span>](https://msdn.microsoft.com/library/windows/apps/mt187350)
* [<span data-ttu-id="c0863-134">Animieren von Drag & Drop-Sequenzen</span><span class="sxs-lookup"><span data-stu-id="c0863-134">Animating drag-and-drop sequences</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/jj649427)
* [<span data-ttu-id="c0863-135">Schnellstart: Animieren der Benutzeroberfläche mithilfe von Bibliotheksanimationen</span><span class="sxs-lookup"><span data-stu-id="c0863-135">Quickstart: Animating your UI using library animations</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh452703)
* [**<span data-ttu-id="c0863-136">DragItemThemeAnimation-Klasse</span><span class="sxs-lookup"><span data-stu-id="c0863-136">DragItemThemeAnimation class</span></span>**](https://msdn.microsoft.com/library/windows/apps/br243174)
* [**<span data-ttu-id="c0863-137">DropTargetItemThemeAnimation-Klasse</span><span class="sxs-lookup"><span data-stu-id="c0863-137">DropTargetItemThemeAnimation class</span></span>**](https://msdn.microsoft.com/library/windows/apps/br243186)
* [**<span data-ttu-id="c0863-138">DragOverThemeAnimation-Klasse</span><span class="sxs-lookup"><span data-stu-id="c0863-138">DragOverThemeAnimation class</span></span>**](https://msdn.microsoft.com/library/windows/apps/br243180)


 




