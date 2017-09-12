---
author: mijacobs
Description: Randbasierte Animationen blenden UI-Elemente ein oder aus, die vom Bildschirmrand ausgehen.
title: "Animationen für randbasierte Benutzeroberflächenelemente in UWP-Apps"
ms.assetid: 5A8F73B1-F4F6-424b-9EDF-A9766C5DEAE8
label: Motion--edge-based UI
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: a1551396ccc0699dfea9da44fac0390ee567d4f3
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="edge-based-ui-animations"></a><span data-ttu-id="e818b-104">Animationen für randbasierte Benutzeroberflächenelemente</span><span class="sxs-lookup"><span data-stu-id="e818b-104">Edge-based UI animations</span></span>


<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">


<span data-ttu-id="e818b-105">Randbasierte Animationen blenden UI-Elemente ein oder aus, die vom Bildschirmrand ausgehen.</span><span class="sxs-lookup"><span data-stu-id="e818b-105">Edge-based animations show or hide UI that originates from the edge of the screen.</span></span> <span data-ttu-id="e818b-106">Die Aktionen zum Anzeigen und Ausblenden können von Benutzern oder von der App initiiert werden.</span><span class="sxs-lookup"><span data-stu-id="e818b-106">The show and hide actions can be initiated either by the user or by the app.</span></span> <span data-ttu-id="e818b-107">Die UI-Elemente können die Anwendung überlagern oder Teil der Hauptoberfläche der App sein.</span><span class="sxs-lookup"><span data-stu-id="e818b-107">The UI can either overlay the app or be part of the main app surface.</span></span> <span data-ttu-id="e818b-108">Wenn das UI-Element Teil der App-Oberfläche ist, müssen Sie möglicherweise die Größe der restlichen App entsprechend anpassen.</span><span class="sxs-lookup"><span data-stu-id="e818b-108">If the UI is part of the app surface, the rest of the app might need to be resized to accommodate it.</span></span>

<div class="important-apis" >
<b><span data-ttu-id="e818b-109">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="e818b-109">Important APIs</span></span></b><br/>
<ul>
<li>[**<span data-ttu-id="e818b-110">EdgeUIThemeTransition-Klasse</span><span class="sxs-lookup"><span data-stu-id="e818b-110">EdgeUIThemeTransition class</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh702324)</li>
</ul>
</div>


## <a name="dos-and-donts"></a><span data-ttu-id="e818b-111">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="e818b-111">Do's and don'ts</span></span>


-   <span data-ttu-id="e818b-112">Verwenden Sie Animationen für Randbenutzeroberflächen zum Anzeigen oder Ausblenden einer benutzerdefinierten Meldungs- oder Fehlerleiste, die nicht weit in den Bildschirm hineinreicht.</span><span class="sxs-lookup"><span data-stu-id="e818b-112">Use edge UI animations to show or hide a custom message or error bar that does not extend far into the screen.</span></span>
-   <span data-ttu-id="e818b-113">Verwenden Sie Panelanimationen, um Benutzeroberflächen anzuzeigen, die weit in den Bildschirm hineinreichen, beispielsweise ein Aufgabenbereich oder eine benutzerdefinierte Bildschirmtastatur.</span><span class="sxs-lookup"><span data-stu-id="e818b-113">Use panel animations to show UI that slides a significant distance into the screen, such as a task pane or a custom soft keyboard.</span></span>
-   <span data-ttu-id="e818b-114">Lassen Sie die UI von demselben Rand hereingleiten, mit dem sie verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="e818b-114">Slide the UI in from the same edge it will be attached to.</span></span>
-   <span data-ttu-id="e818b-115">Lassen Sie die UI an demselben Rand hinausgleiten, von dem sie hereingekommen ist.</span><span class="sxs-lookup"><span data-stu-id="e818b-115">Slide the UI out to the same edge it came from.</span></span>
-   <span data-ttu-id="e818b-116">Wenn der Inhalt der App aufgrund des Herein- oder Hinausgleitens der Benutzeroberfläche in der Größe angepasst werden muss, verwenden Sie Ein- und Ausblendungsanimationen.</span><span class="sxs-lookup"><span data-stu-id="e818b-116">If the contents of the app need to resize in response to the UI sliding in or out, use fade animations for the resize.</span></span>
    -   <span data-ttu-id="e818b-117">Wenn die Benutzeroberfläche hereingleitet, verwenden Sie nach der Animation für Randbenutzeroberflächen oder Panels eine Ein- oder Ausblendungsanimation.</span><span class="sxs-lookup"><span data-stu-id="e818b-117">If the UI is sliding in, use a fade animation after the edge UI or panel animation.</span></span>
    -   <span data-ttu-id="e818b-118">Wenn die Benutzeroberfläche herausgleitet, verwenden Sie gleichzeitig mit der Animation für Randbenutzeroberflächen oder Panels eine Ein- oder Ausblendungsanimation.</span><span class="sxs-lookup"><span data-stu-id="e818b-118">If the UI is sliding out, use a fade animation at the same time as the edge UI or panel animation.</span></span>
-   <span data-ttu-id="e818b-119">Wenden Sie diese Animationen nicht auf Benachrichtigungen an.</span><span class="sxs-lookup"><span data-stu-id="e818b-119">Don't apply these animations to notifications.</span></span> <span data-ttu-id="e818b-120">Benachrichtigungen sollten sich nicht auf der randbasierten Benutzeroberfläche befinden.</span><span class="sxs-lookup"><span data-stu-id="e818b-120">Notifications should not be housed within edge-based UI.</span></span>
-   <span data-ttu-id="e818b-121">Wenden Sie die Animation für Randbenutzeroberflächen oder Panels nicht auf Benutzeroberflächencontainer oder Steuerelemente an, die sich nicht am Rand des Bildschirms befinden.</span><span class="sxs-lookup"><span data-stu-id="e818b-121">Don't apply the edge UI or panel animations to any UI container or control that is not at the edge of the screen.</span></span> <span data-ttu-id="e818b-122">Diese Animationen werden nur für das Anzeigen und Schließen von Benutzeroberflächen am Rand des Bildschirms sowie zum Ändern ihrer Größe verwendet.</span><span class="sxs-lookup"><span data-stu-id="e818b-122">These animations are used only for showing, resizing, and dismissing UI at the edges of the screen.</span></span> <span data-ttu-id="e818b-123">Verwenden Sie zum Verschieben anderer Benutzeroberflächenarten die Animationen für das Ändern der Position.</span><span class="sxs-lookup"><span data-stu-id="e818b-123">To move other types of UI, use reposition animations.</span></span>

    ![Zeigt, wann Sie Rand-UI- oder Panelanimationen verwenden sollten und wann Sie Positionen ändern sollten.](images/edgevsreposition.png)

## <a name="related-articles"></a><span data-ttu-id="e818b-125">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="e818b-125">Related articles</span></span>


**<span data-ttu-id="e818b-126">Für Entwickler</span><span class="sxs-lookup"><span data-stu-id="e818b-126">For developers</span></span>**
* [<span data-ttu-id="e818b-127">Übersicht über Animationen</span><span class="sxs-lookup"><span data-stu-id="e818b-127">Animations overview</span></span>](https://msdn.microsoft.com/library/windows/apps/mt187350)
* [<span data-ttu-id="e818b-128">Animieren der Rand-UI</span><span class="sxs-lookup"><span data-stu-id="e818b-128">Animating edge-based UI</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/jj649428)
* [<span data-ttu-id="e818b-129">Schnellstart: Animieren der Benutzeroberfläche mithilfe von Bibliotheksanimationen</span><span class="sxs-lookup"><span data-stu-id="e818b-129">Quickstart: Animating your UI using library animations</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh452703)
* [**<span data-ttu-id="e818b-130">EdgeUIThemeTransition-Klasse</span><span class="sxs-lookup"><span data-stu-id="e818b-130">EdgeUIThemeTransition class</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh702324)
* [**<span data-ttu-id="e818b-131">PaneThemeTransition-Klasse</span><span class="sxs-lookup"><span data-stu-id="e818b-131">PaneThemeTransition class</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh969160)
* [<span data-ttu-id="e818b-132">Animieren von Ein- und Ausblendungen</span><span class="sxs-lookup"><span data-stu-id="e818b-132">Animating fades</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/jj649429)
* [<span data-ttu-id="e818b-133">Animieren von Änderungen der Position</span><span class="sxs-lookup"><span data-stu-id="e818b-133">Animating repositions</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/jj649434)

 

 




