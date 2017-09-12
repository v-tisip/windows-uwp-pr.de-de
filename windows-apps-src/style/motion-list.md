---
author: mijacobs
Description: "Mit Listenanimationen können Sie einzelne oder mehrere Elemente in einer Sammlung wie z. B. einem Fotoalbum oder einer Liste mit Suchergebnissen einfügen oder entfernen."
title: "Hinzufügen und Löschen von Animationen in UWP-Apps"
ms.assetid: A85006AE-4992-457a-B514-500B8BEF5DC8
label: Motion--add and delete animations
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 40e4ca48132914140fcd4780876615a5864c3157
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="add-and-delete-animations"></a><span data-ttu-id="faaf1-104">Hinzufügen und Löschen von Animationen</span><span class="sxs-lookup"><span data-stu-id="faaf1-104">Add and delete animations</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

<span data-ttu-id="faaf1-105">Mit Listenanimationen können Sie einzelne oder mehrere Elemente in einer Sammlung wie z. B. einem Fotoalbum oder einer Liste mit Suchergebnissen einfügen oder entfernen.</span><span class="sxs-lookup"><span data-stu-id="faaf1-105">List animations let you insert or remove single or multiple items from a collection, such as a photo album or a list of search results.</span></span>

<div class="important-apis" >
<b><span data-ttu-id="faaf1-106">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="faaf1-106">Important APIs</span></span></b><br/>
<ul>
<li>[**<span data-ttu-id="faaf1-107">AddDeleteThemeTransition-Klasse</span><span class="sxs-lookup"><span data-stu-id="faaf1-107">AddDeleteThemeTransition class</span></span>**](https://msdn.microsoft.com/library/windows/apps/br243048)</li>
</ul>
</div>


## <a name="dos-and-donts"></a><span data-ttu-id="faaf1-108">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="faaf1-108">Do's and don'ts</span></span>


-   <span data-ttu-id="faaf1-109">Verwenden Sie Listenanimationen, um einer bestehenden Menge von Elementen ein einzelnes neues Element hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="faaf1-109">Use list animations to add a single new item to an existing set of items.</span></span> <span data-ttu-id="faaf1-110">Verwenden Sie diese Animationen beispielsweise, wenn eine neue E-Mail eingeht oder ein neues Foto in eine vorhandene Serie importiert wird.</span><span class="sxs-lookup"><span data-stu-id="faaf1-110">For example, use them when a new email arrives or when a new photo is imported into an existing set.</span></span>
-   <span data-ttu-id="faaf1-111">Verwenden Sie Listenanimationen, um einer bestehenden Menge von Elementen mehrere Elemente gleichzeitig hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="faaf1-111">Use list animations to add several items to a set at one time.</span></span> <span data-ttu-id="faaf1-112">Verwenden Sie diese Animationen beispielsweise, wenn Sie eine neue Fotoserie in eine vorhandene Sammlung importieren.</span><span class="sxs-lookup"><span data-stu-id="faaf1-112">For example, use them when you import a new set of photos to an existing collection.</span></span> <span data-ttu-id="faaf1-113">Wenn mehrere Elemente hinzugefügt oder gelöscht werden, sollte der Vorgang für alle Elemente gleichzeitig erfolgen, ohne dass es zwischen den Aktionen für die einzelnen Objekte zu Verzögerungen kommt.</span><span class="sxs-lookup"><span data-stu-id="faaf1-113">The addition or deletion of multiple items should happen at the same time, with no delay between the action on the individual objects.</span></span>
-   <span data-ttu-id="faaf1-114">Verwenden Sie Listenanimationen für das Hinzufügen und Löschen als Paar.</span><span class="sxs-lookup"><span data-stu-id="faaf1-114">Use add and delete list animations as a pair.</span></span> <span data-ttu-id="faaf1-115">Verwenden Sie immer, wenn Sie eine dieser Animationen verwenden, die zugehörige Animation für die entgegengesetzte Aktion.</span><span class="sxs-lookup"><span data-stu-id="faaf1-115">Whenever you use one of these animations, use the corresponding animation for the opposite action.</span></span>
-   <span data-ttu-id="faaf1-116">Verwenden Sie Listenanimationen mit einer Liste von Elementen, in der Sie ein Element oder eine Gruppe von Elementen gleichzeitig hinzufügen oder löschen können.</span><span class="sxs-lookup"><span data-stu-id="faaf1-116">Use list animations with a list of items to which you can add or delete one element or group of elements at once.</span></span>
-   <span data-ttu-id="faaf1-117">Verwenden Sie Listenanimationen nicht, um einen Container anzuzeigen oder zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="faaf1-117">Don't use list animations to display or remove a container.</span></span> <span data-ttu-id="faaf1-118">Diese Animationen sind für Elemente einer bereits angezeigten Auflistung oder Menge vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="faaf1-118">These animations are for members of a collection or set that is already being displayed.</span></span> <span data-ttu-id="faaf1-119">Verwenden Sie Popupanimationen, um einen kurzlebigen Container auf der App-Oberfläche ein- oder auszublenden.</span><span class="sxs-lookup"><span data-stu-id="faaf1-119">Use pop-up animations to show or hide a transient container on top of the app surface.</span></span> <span data-ttu-id="faaf1-120">Verwenden Sie Inhaltsübergangsanimationen, um einen Container, der Teil der App-Oberfläche ist, anzuzeigen oder zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="faaf1-120">Use content transition animations to display or replace a container that is part of the app surface.</span></span>
-   <span data-ttu-id="faaf1-121">Verwenden Sie Listenanimationen nicht für eine vollständige Menge von Elementen.</span><span class="sxs-lookup"><span data-stu-id="faaf1-121">Don't use list animations on an entire set of items.</span></span> <span data-ttu-id="faaf1-122">Verwenden Sie die Inhaltsübergangsanimationen, um eine vollständige Auflistung innerhalb des Containers hinzuzufügen oder zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="faaf1-122">Use the content transition animations to add or remove an entire collection within your container.</span></span>



## <a name="related-articles"></a><span data-ttu-id="faaf1-123">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="faaf1-123">Related articles</span></span>

* [<span data-ttu-id="faaf1-124">Übersicht über Animationen</span><span class="sxs-lookup"><span data-stu-id="faaf1-124">Animations overview</span></span>](https://msdn.microsoft.com/library/windows/apps/mt187350)
* [<span data-ttu-id="faaf1-125">Animieren von Hinzufügungen und Löschungen in Listen</span><span class="sxs-lookup"><span data-stu-id="faaf1-125">Animating list additions and deletions</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/jj649430)
* [<span data-ttu-id="faaf1-126">Schnellstart: Animieren der Benutzeroberfläche mithilfe von Bibliotheksanimationen</span><span class="sxs-lookup"><span data-stu-id="faaf1-126">Quickstart: Animating your UI using library animations</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh452703)
* [**<span data-ttu-id="faaf1-127">AddDeleteThemeTransition-Klasse</span><span class="sxs-lookup"><span data-stu-id="faaf1-127">AddDeleteThemeTransition class</span></span>**](https://msdn.microsoft.com/library/windows/apps/br243048)

 

 




