---
author: mijacobs
Description: "Verwenden Sie Ein- und Ausblendungsanimationen, um Elemente anzuzeigen oder nicht anzuzeigen. Die beiden üblichen Animationen dieser Art sind das Einblenden und das Ausblenden."
title: Ein-und Ausblendungsanimationen in UWP-Apps
ms.assetid: 975E5EE3-EFBE-4159-8D10-3C94143DD07F
label: Motion--fades
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 2090d68bfc2e4dc1e1c6770a17241cd1cffcffb4
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="fade-animations"></a><span data-ttu-id="cbbc7-105">Ein- und Ausblendungsanimationen</span><span class="sxs-lookup"><span data-stu-id="cbbc7-105">Fade animations</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

<span data-ttu-id="cbbc7-106">Verwenden Sie Ein- und Ausblendungsanimationen, um Elemente anzuzeigen oder nicht anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="cbbc7-106">Use fade animations to bring items into a view or to take items out of a view.</span></span> <span data-ttu-id="cbbc7-107">Die beiden üblichen Animationen dieser Art sind das Einblenden und das Ausblenden.</span><span class="sxs-lookup"><span data-stu-id="cbbc7-107">The two common fade animations are fade-in and fade-out.</span></span>

<div class="important-apis" >
<b><span data-ttu-id="cbbc7-108">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="cbbc7-108">Important APIs</span></span></b><br/>
<ul>
<li>[**<span data-ttu-id="cbbc7-109">FadeInThemeAnimation-Klasse</span><span class="sxs-lookup"><span data-stu-id="cbbc7-109">FadeInThemeAnimation class</span></span>**](https://msdn.microsoft.com/library/windows/apps/br210298)</li>
<li>[**<span data-ttu-id="cbbc7-110">FadeOutThemeAnimation-Klasse</span><span class="sxs-lookup"><span data-stu-id="cbbc7-110">FadeOutThemeAnimation class</span></span>**](https://msdn.microsoft.com/library/windows/apps/br210302)</li>
</ul>
</div>


## <a name="dos-and-donts"></a><span data-ttu-id="cbbc7-111">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="cbbc7-111">Do's and don'ts</span></span>


-   <span data-ttu-id="cbbc7-112">Wenn die App zwischen nicht verbundenen oder textlastigen Elementen wechselt, sollten Sie eine Ausblendungsanimation gefolgt von einer Einblendungsanimation verwenden.</span><span class="sxs-lookup"><span data-stu-id="cbbc7-112">When your app transitions between unrelated or text-heavy elements, use a fade-out followed by a fade-in.</span></span> <span data-ttu-id="cbbc7-113">Auf diese Weise kann das ausgehende Objekt vollständig ausgeblendet werden, bevor das eingehende Objekt sichtbar wird.</span><span class="sxs-lookup"><span data-stu-id="cbbc7-113">This allows the outgoing object to completely disappear before the incoming object is visible.</span></span>
-   <span data-ttu-id="cbbc7-114">Blenden Sie die eingehenden Elemente über den ausgehenden Elementen ein, wenn die Größe der Elemente konstant bleibt und die Benutzer den Eindruck haben sollen, das gleiche Element zu sehen.</span><span class="sxs-lookup"><span data-stu-id="cbbc7-114">Fade in the incoming element or elements on top of the outgoing elements if the size of the elements remains constant, and if you want the user to feel that they're looking at the same item.</span></span> <span data-ttu-id="cbbc7-115">Sobald die Einblendung abgeschlossen ist, kann das ausgehende Element entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="cbbc7-115">Once the fade-in is complete, the outgoing item can be removed.</span></span> <span data-ttu-id="cbbc7-116">Diese Vorgehensweise ist nur dann geeignet, wenn das ausgehende Element vom eingehenden Element vollständig verdeckt wird.</span><span class="sxs-lookup"><span data-stu-id="cbbc7-116">This is only a viable option when the outgoing item will be completely covered by the incoming item.</span></span>
-   <span data-ttu-id="cbbc7-117">Vermeiden Sie es, dass bei Ein- und Ausblendungsanimationen Elemente einer Liste hinzugefügt oder daraus gelöscht werden sollen.</span><span class="sxs-lookup"><span data-stu-id="cbbc7-117">Avoid fade animations to add or delete items in a list.</span></span> <span data-ttu-id="cbbc7-118">Verwenden Sie stattdessen die zu diesem Zweck erstellten Listenanimationen.</span><span class="sxs-lookup"><span data-stu-id="cbbc7-118">Instead, use the list animations created for that purpose.</span></span>
-   <span data-ttu-id="cbbc7-119">Verwenden Sie Ein- und Ausblendungsanimationen möglichst nicht, um den gesamten Inhalt einer Seite zu ändern.</span><span class="sxs-lookup"><span data-stu-id="cbbc7-119">Avoid fade animations to change the entire contents of a page.</span></span> <span data-ttu-id="cbbc7-120">Verwenden Sie stattdessen die zu diesem Zweck erstellten Seitenübergangsanimationen.</span><span class="sxs-lookup"><span data-stu-id="cbbc7-120">Instead, use the page transition animations created for that purpose.</span></span>
-   <span data-ttu-id="cbbc7-121">Ausblenden ist eine gute Möglichkeit, um ein Element zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="cbbc7-121">Fade-out is a subtle way to remove an element.</span></span>
## <a name="related-articles"></a><span data-ttu-id="cbbc7-122">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="cbbc7-122">Related articles</span></span>

* [<span data-ttu-id="cbbc7-123">Übersicht über Animationen</span><span class="sxs-lookup"><span data-stu-id="cbbc7-123">Animations overview</span></span>](https://msdn.microsoft.com/library/windows/apps/mt187350)
* [<span data-ttu-id="cbbc7-124">Animieren von Ein- und Ausblendungen</span><span class="sxs-lookup"><span data-stu-id="cbbc7-124">Animating fades</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/jj649429)
* [<span data-ttu-id="cbbc7-125">Schnellstart: Animieren der Benutzeroberfläche mithilfe von Bibliotheksanimationen</span><span class="sxs-lookup"><span data-stu-id="cbbc7-125">Quickstart: Animating your UI using library animations</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh452703)
* [**<span data-ttu-id="cbbc7-126">FadeInThemeAnimation-Klasse</span><span class="sxs-lookup"><span data-stu-id="cbbc7-126">FadeInThemeAnimation class</span></span>**](https://msdn.microsoft.com/library/windows/apps/br210298)
* [**<span data-ttu-id="cbbc7-127">FadeOutThemeAnimation-Klasse</span><span class="sxs-lookup"><span data-stu-id="cbbc7-127">FadeOutThemeAnimation class</span></span>**](https://msdn.microsoft.com/library/windows/apps/br210302)

 

 




