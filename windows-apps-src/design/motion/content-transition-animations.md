---
Description: Content transition animations let you change the content of an area of the screen while keeping the container or background constant. New content fades in. If there is existing content to be replaced, that content fades out.
title: Richtlinien für Inhaltsübergangsanimationen
ms.assetid: 0188FDB4-E183-466f-8A03-EE3FF5C474B1
template: detail.hbs
ms.date: 05/19/2017
ms.topic: article
keywords: Windows10, UWP
pm-contact: stmoy
design-contact: conrwi
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 096cc0aaa9b0580eb6b45328a3243ba75d82f202
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "8872218"
---
# <a name="content-transition-animations"></a><span data-ttu-id="8e9d1-103">Inhaltsübergangsanimationen</span><span class="sxs-lookup"><span data-stu-id="8e9d1-103">Content transition animations</span></span>



<span data-ttu-id="8e9d1-104">Mithilfe von Inhaltsübergangsanimationen können Sie den Inhalt eines Bildschirmbereichs ändern und gleichzeitig den Container oder Hintergrund unverändert lassen.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-104">Content transition animations let you change the content of an area of the screen while keeping the container or background constant.</span></span> <span data-ttu-id="8e9d1-105">Neuer Inhalt wird eingeblendet.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-105">New content fades in.</span></span> <span data-ttu-id="8e9d1-106">Muss vorhandener Inhalt ersetzt werden, wird dieser Inhalt ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-106">If there is existing content to be replaced, that content fades out.</span></span>

> <span data-ttu-id="8e9d1-107">**Wichtige APIs**: [**ContentThemeTransition class (XAML)**](https://msdn.microsoft.com/library/windows/apps/br243104)</span><span class="sxs-lookup"><span data-stu-id="8e9d1-107">**Important APIs**: [**ContentThemeTransition class (XAML)**](https://msdn.microsoft.com/library/windows/apps/br243104)</span></span>

## <a name="dos-and-donts"></a><span data-ttu-id="8e9d1-108">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="8e9d1-108">Do's and don'ts</span></span>


-   <span data-ttu-id="8e9d1-109">Verwenden Sie eine Eingangsanimation, wenn mehrere neue Elemente in einen leeren Container aufgenommen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-109">Use an entrance animation when there is a set of new items to bring into an empty container.</span></span> <span data-ttu-id="8e9d1-110">Beispielsweise ist nach dem anfänglichen Laden einer App ein Teil des Inhalts nicht sofort für die Anzeige verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-110">For example, after the initial load of an app, part of the app's content might not be immediately available for display.</span></span> <span data-ttu-id="8e9d1-111">Wenn der Inhalt bereit zum Anzeigen ist, nehmen Sie diesen verzögerten Inhalt mithilfe einer Inhaltsübergangsanimation in die Ansicht auf.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-111">When that content is ready to be shown, use a content transition animation to bring that late content into the view.</span></span>
-   <span data-ttu-id="8e9d1-112">Mit Inhaltsübergängen können Sie einen Satz Inhalt durch einen anderen ersetzen, der sich bereits im gleichen Container in einer Ansicht befindet.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-112">Use content transitions to replace one set of content with another set of content that already resides in the same container within a view.</span></span>
-   <span data-ttu-id="8e9d1-113">Wenn Sie neuen Inhalt aufnehmen, ziehen Sie diesen (von unten nach oben) entgegen dem normalen Seitenfluss oder der Leserichtung in die Ansicht.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-113">When bringing in new content, slide that content up (from bottom to top) into the view against the general page flow or reading order.</span></span>
-   <span data-ttu-id="8e9d1-114">Stellen Sie neue Inhalte auf logische Art und Weise vor. Geben Sie beispielsweise die wichtigsten Inhalte zuletzt bekannt.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-114">Introduce new content in a logical manner, for example, introduce the most important piece of content last.</span></span>
-   <span data-ttu-id="8e9d1-115">Wenn Sie den Inhalt mehrerer Container aktualisieren möchten, lösen Sie alle Übergangsanimationen ohne Staffelung oder Verzögerung gleichzeitig aus.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-115">If you have more than one container whose content is to be updated, trigger all of the transition animations simultaneously without any staggering or delay.</span></span>
-   <span data-ttu-id="8e9d1-116">Verwenden Sie Inhaltsübergangsanimationen nicht, wenn sich die gesamte Seite ändert.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-116">Don't use content transition animations when the entire page is changing.</span></span> <span data-ttu-id="8e9d1-117">Verwenden Sie in diesem Fall die Seitenübergangsanimationen.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-117">In that case, use the page transition animations instead.</span></span>
-   <span data-ttu-id="8e9d1-118">Verwenden Sie Inhaltsübergangsanimationen nicht, wenn der Inhalt nur aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-118">Don't use content transition animations if the content is only refreshing.</span></span> <span data-ttu-id="8e9d1-119">Inhaltsübergangsanimationen sollen auf Bewegungen hinweisen.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-119">Content transition animations are meant to show movement.</span></span> <span data-ttu-id="8e9d1-120">Verwenden Sie für Aktualisierungen Ein- und Ausblendungsanimationen.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-120">For refreshes, use fade animations.</span></span>



## <a name="related-articles"></a><span data-ttu-id="8e9d1-121">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="8e9d1-121">Related articles</span></span>

**<span data-ttu-id="8e9d1-122">Für Entwickler (XAML)</span><span class="sxs-lookup"><span data-stu-id="8e9d1-122">For developers (XAML)</span></span>**
* [<span data-ttu-id="8e9d1-123">Übersicht über Animationen</span><span class="sxs-lookup"><span data-stu-id="8e9d1-123">Animations overview</span></span>](https://msdn.microsoft.com/library/windows/apps/mt187350)
* [<span data-ttu-id="8e9d1-124">Animieren von Inhaltsübergängen</span><span class="sxs-lookup"><span data-stu-id="8e9d1-124">Animating content transitions</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/jj649426)
* [<span data-ttu-id="8e9d1-125">Schnellstart: Animieren der Benutzeroberfläche mithilfe von Bibliothekanimationen</span><span class="sxs-lookup"><span data-stu-id="8e9d1-125">Quickstart: Animating your UI using library animations</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh452703)
* [**<span data-ttu-id="8e9d1-126">ContentThemeTransition-Klasse</span><span class="sxs-lookup"><span data-stu-id="8e9d1-126">ContentThemeTransition class</span></span>**](https://msdn.microsoft.com/library/windows/apps/br243104)

 

 




