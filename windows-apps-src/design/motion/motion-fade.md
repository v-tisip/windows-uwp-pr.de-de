---
author: mijacobs
Description: Use fade animations to bring items into a view or to take items out of a view. The two common fade animations are fade-in and fade-out.
title: Ein-und Ausblendungsanimationen in UWP-Apps
ms.assetid: 975E5EE3-EFBE-4159-8D10-3C94143DD07F
label: Motion--fades
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: d2a9745e35f19066b094b2be187620858166dbd5
ms.sourcegitcommit: 38f06f1714334273d865935d9afb80efffe97a17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6203905"
---
# <a name="fade-animations"></a><span data-ttu-id="a8984-103">Ein- und Ausblendungsanimationen</span><span class="sxs-lookup"><span data-stu-id="a8984-103">Fade animations</span></span>



<span data-ttu-id="a8984-104">Verwenden Sie Ein- und Ausblendungsanimationen, um Elemente anzuzeigen oder nicht anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a8984-104">Use fade animations to bring items into a view or to take items out of a view.</span></span> <span data-ttu-id="a8984-105">Die beiden üblichen Animationen dieser Art sind das Einblenden und das Ausblenden.</span><span class="sxs-lookup"><span data-stu-id="a8984-105">The two common fade animations are fade-in and fade-out.</span></span>

> <span data-ttu-id="a8984-106">**Wichtige APIs**: [**FadeInThemeAnimation class**](https://msdn.microsoft.com/library/windows/apps/br210298), [**FadeOutThemeAnimation class**](https://msdn.microsoft.com/library/windows/apps/br210302)</span><span class="sxs-lookup"><span data-stu-id="a8984-106">**Important APIs**: [**FadeInThemeAnimation class**](https://msdn.microsoft.com/library/windows/apps/br210298), [**FadeOutThemeAnimation class**](https://msdn.microsoft.com/library/windows/apps/br210302)</span></span>


## <a name="dos-and-donts"></a><span data-ttu-id="a8984-107">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="a8984-107">Do's and don'ts</span></span>


-   <span data-ttu-id="a8984-108">Wenn die App zwischen nicht verbundenen oder textlastigen Elementen wechselt, sollten Sie eine Ausblendungsanimation gefolgt von einer Einblendungsanimation verwenden.</span><span class="sxs-lookup"><span data-stu-id="a8984-108">When your app transitions between unrelated or text-heavy elements, use a fade-out followed by a fade-in.</span></span> <span data-ttu-id="a8984-109">Auf diese Weise kann das ausgehende Objekt vollständig ausgeblendet werden, bevor das eingehende Objekt sichtbar wird.</span><span class="sxs-lookup"><span data-stu-id="a8984-109">This allows the outgoing object to completely disappear before the incoming object is visible.</span></span>
-   <span data-ttu-id="a8984-110">Blenden Sie die eingehenden Elemente über den ausgehenden Elementen ein, wenn die Größe der Elemente konstant bleibt und die Benutzer den Eindruck haben sollen, das gleiche Element zu sehen.</span><span class="sxs-lookup"><span data-stu-id="a8984-110">Fade in the incoming element or elements on top of the outgoing elements if the size of the elements remains constant, and if you want the user to feel that they're looking at the same item.</span></span> <span data-ttu-id="a8984-111">Sobald die Einblendung abgeschlossen ist, kann das ausgehende Element entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="a8984-111">Once the fade-in is complete, the outgoing item can be removed.</span></span> <span data-ttu-id="a8984-112">Diese Vorgehensweise ist nur dann geeignet, wenn das ausgehende Element vom eingehenden Element vollständig verdeckt wird.</span><span class="sxs-lookup"><span data-stu-id="a8984-112">This is only a viable option when the outgoing item will be completely covered by the incoming item.</span></span>
-   <span data-ttu-id="a8984-113">Vermeiden Sie es, dass bei Ein- und Ausblendungsanimationen Elemente einer Liste hinzugefügt oder daraus gelöscht werden sollen.</span><span class="sxs-lookup"><span data-stu-id="a8984-113">Avoid fade animations to add or delete items in a list.</span></span> <span data-ttu-id="a8984-114">Verwenden Sie stattdessen die zu diesem Zweck erstellten Listenanimationen.</span><span class="sxs-lookup"><span data-stu-id="a8984-114">Instead, use the list animations created for that purpose.</span></span>
-   <span data-ttu-id="a8984-115">Verwenden Sie Ein- und Ausblendungsanimationen möglichst nicht, um den gesamten Inhalt einer Seite zu ändern.</span><span class="sxs-lookup"><span data-stu-id="a8984-115">Avoid fade animations to change the entire contents of a page.</span></span> <span data-ttu-id="a8984-116">Verwenden Sie stattdessen die zu diesem Zweck erstellten Seitenübergangsanimationen.</span><span class="sxs-lookup"><span data-stu-id="a8984-116">Instead, use the page transition animations created for that purpose.</span></span>
-   <span data-ttu-id="a8984-117">Ausblenden ist eine gute Möglichkeit, um ein Element zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="a8984-117">Fade-out is a subtle way to remove an element.</span></span>
## <a name="related-articles"></a><span data-ttu-id="a8984-118">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="a8984-118">Related articles</span></span>

* [<span data-ttu-id="a8984-119">Übersicht über Animationen</span><span class="sxs-lookup"><span data-stu-id="a8984-119">Animations overview</span></span>](https://msdn.microsoft.com/library/windows/apps/mt187350)
* [<span data-ttu-id="a8984-120">Animieren von Ein- und Ausblendungen</span><span class="sxs-lookup"><span data-stu-id="a8984-120">Animating fades</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/jj649429)
* [<span data-ttu-id="a8984-121">Schnellstart: Animieren der Benutzeroberfläche mithilfe von Bibliotheksanimationen</span><span class="sxs-lookup"><span data-stu-id="a8984-121">Quickstart: Animating your UI using library animations</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh452703)
* [**<span data-ttu-id="a8984-122">FadeInThemeAnimation-Klasse</span><span class="sxs-lookup"><span data-stu-id="a8984-122">FadeInThemeAnimation class</span></span>**](https://msdn.microsoft.com/library/windows/apps/br210298)
* [**<span data-ttu-id="a8984-123">FadeOutThemeAnimation-Klasse</span><span class="sxs-lookup"><span data-stu-id="a8984-123">FadeOutThemeAnimation class</span></span>**](https://msdn.microsoft.com/library/windows/apps/br210302)

 

 




