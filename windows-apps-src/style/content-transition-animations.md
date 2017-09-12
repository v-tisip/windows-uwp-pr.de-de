---
author: mijacobs
Description: "Mithilfe von Inhaltsübergangsanimationen können Sie den Inhalt eines Bildschirmbereichs ändern und gleichzeitig den Container oder Hintergrund unverändert lassen. Neuer Inhalt wird eingeblendet. Muss vorhandener Inhalt ersetzt werden, wird dieser Inhalt ausgeblendet."
title: "Richtlinien für Inhaltsübergangsanimationen"
ms.assetid: 0188FDB4-E183-466f-8A03-EE3FF5C474B1
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
pm-contact: stmoy
design-contact: conrwi
doc-status: Published
ms.openlocfilehash: 881059e8ec15ec1006a15f453e5f488ed8d04bed
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="content-transition-animations"></a><span data-ttu-id="2f846-106">Inhaltsübergangsanimationen</span><span class="sxs-lookup"><span data-stu-id="2f846-106">Content transition animations</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

<span data-ttu-id="2f846-107">Mithilfe von Inhaltsübergangsanimationen können Sie den Inhalt eines Bildschirmbereichs ändern und gleichzeitig den Container oder Hintergrund unverändert lassen.</span><span class="sxs-lookup"><span data-stu-id="2f846-107">Content transition animations let you change the content of an area of the screen while keeping the container or background constant.</span></span> <span data-ttu-id="2f846-108">Neuer Inhalt wird eingeblendet.</span><span class="sxs-lookup"><span data-stu-id="2f846-108">New content fades in.</span></span> <span data-ttu-id="2f846-109">Muss vorhandener Inhalt ersetzt werden, wird dieser Inhalt ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="2f846-109">If there is existing content to be replaced, that content fades out.</span></span>

<div class="important-apis" >
<b><span data-ttu-id="2f846-110">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="2f846-110">Important APIs</span></span></b><br/>
<ul>
<li>[**<span data-ttu-id="2f846-111">ContentThemeTransition-Klasse (XAML)</span><span class="sxs-lookup"><span data-stu-id="2f846-111">ContentThemeTransition class (XAML)</span></span>**](https://msdn.microsoft.com/library/windows/apps/br243104)</li>
</ul>
</div>

## <a name="dos-and-donts"></a><span data-ttu-id="2f846-112">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="2f846-112">Do's and don'ts</span></span>


-   <span data-ttu-id="2f846-113">Verwenden Sie eine Eingangsanimation, wenn mehrere neue Elemente in einen leeren Container aufgenommen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="2f846-113">Use an entrance animation when there is a set of new items to bring into an empty container.</span></span> <span data-ttu-id="2f846-114">Beispielsweise ist nach dem anfänglichen Laden einer App ein Teil des Inhalts nicht sofort für die Anzeige verfügbar.</span><span class="sxs-lookup"><span data-stu-id="2f846-114">For example, after the initial load of an app, part of the app's content might not be immediately available for display.</span></span> <span data-ttu-id="2f846-115">Wenn der Inhalt bereit zum Anzeigen ist, nehmen Sie diesen verzögerten Inhalt mithilfe einer Inhaltsübergangsanimation in die Ansicht auf.</span><span class="sxs-lookup"><span data-stu-id="2f846-115">When that content is ready to be shown, use a content transition animation to bring that late content into the view.</span></span>
-   <span data-ttu-id="2f846-116">Mit Inhaltsübergängen können Sie einen Satz Inhalt durch einen anderen ersetzen, der sich bereits im gleichen Container in einer Ansicht befindet.</span><span class="sxs-lookup"><span data-stu-id="2f846-116">Use content transitions to replace one set of content with another set of content that already resides in the same container within a view.</span></span>
-   <span data-ttu-id="2f846-117">Wenn Sie neuen Inhalt aufnehmen, ziehen Sie diesen (von unten nach oben) entgegen dem normalen Seitenfluss oder der Leserichtung in die Ansicht.</span><span class="sxs-lookup"><span data-stu-id="2f846-117">When bringing in new content, slide that content up (from bottom to top) into the view against the general page flow or reading order.</span></span>
-   <span data-ttu-id="2f846-118">Stellen Sie neue Inhalte auf logische Art und Weise vor. Geben Sie beispielsweise die wichtigsten Inhalte zuletzt bekannt.</span><span class="sxs-lookup"><span data-stu-id="2f846-118">Introduce new content in a logical manner, for example, introduce the most important piece of content last.</span></span>
-   <span data-ttu-id="2f846-119">Wenn Sie den Inhalt mehrerer Container aktualisieren möchten, lösen Sie alle Übergangsanimationen ohne Staffelung oder Verzögerung gleichzeitig aus.</span><span class="sxs-lookup"><span data-stu-id="2f846-119">If you have more than one container whose content is to be updated, trigger all of the transition animations simultaneously without any staggering or delay.</span></span>
-   <span data-ttu-id="2f846-120">Verwenden Sie Inhaltsübergangsanimationen nicht, wenn sich die gesamte Seite ändert.</span><span class="sxs-lookup"><span data-stu-id="2f846-120">Don't use content transition animations when the entire page is changing.</span></span> <span data-ttu-id="2f846-121">Verwenden Sie in diesem Fall die Seitenübergangsanimationen.</span><span class="sxs-lookup"><span data-stu-id="2f846-121">In that case, use the page transition animations instead.</span></span>
-   <span data-ttu-id="2f846-122">Verwenden Sie Inhaltsübergangsanimationen nicht, wenn der Inhalt nur aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="2f846-122">Don't use content transition animations if the content is only refreshing.</span></span> <span data-ttu-id="2f846-123">Inhaltsübergangsanimationen sollen auf Bewegungen hinweisen.</span><span class="sxs-lookup"><span data-stu-id="2f846-123">Content transition animations are meant to show movement.</span></span> <span data-ttu-id="2f846-124">Verwenden Sie für Aktualisierungen Ein- und Ausblendungsanimationen.</span><span class="sxs-lookup"><span data-stu-id="2f846-124">For refreshes, use fade animations.</span></span>



## <a name="related-articles"></a><span data-ttu-id="2f846-125">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="2f846-125">Related articles</span></span>

**<span data-ttu-id="2f846-126">Für Entwickler (XAML)</span><span class="sxs-lookup"><span data-stu-id="2f846-126">For developers (XAML)</span></span>**
* [<span data-ttu-id="2f846-127">Übersicht über Animationen</span><span class="sxs-lookup"><span data-stu-id="2f846-127">Animations overview</span></span>](https://msdn.microsoft.com/library/windows/apps/mt187350)
* [<span data-ttu-id="2f846-128">Animieren von Inhaltsübergängen</span><span class="sxs-lookup"><span data-stu-id="2f846-128">Animating content transitions</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/jj649426)
* [<span data-ttu-id="2f846-129">Schnellstart: Animieren der Benutzeroberfläche mithilfe von Bibliothekanimationen</span><span class="sxs-lookup"><span data-stu-id="2f846-129">Quickstart: Animating your UI using library animations</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh452703)
* [**<span data-ttu-id="2f846-130">ContentThemeTransition-Klasse</span><span class="sxs-lookup"><span data-stu-id="2f846-130">ContentThemeTransition class</span></span>**](https://msdn.microsoft.com/library/windows/apps/br243104)

 

 




