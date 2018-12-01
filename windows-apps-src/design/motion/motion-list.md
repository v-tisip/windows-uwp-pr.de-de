---
Description: List animations let you insert or remove single or multiple items from a collection, such as a photo album or a list of search results.
title: Hinzufügen und Löschen von Animationen in UWP-Apps
ms.assetid: A85006AE-4992-457a-B514-500B8BEF5DC8
label: Motion--add and delete animations
template: detail.hbs
ms.date: 05/19/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: c7ca332b73aba067c2ae003d458e8d0d97c7a7e3
ms.sourcegitcommit: d2517e522cacc5240f7dffd5bc1eaa278e3f7768
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8334290"
---
# <a name="add-and-delete-animations"></a><span data-ttu-id="c42e8-103">Hinzufügen und Löschen von Animationen</span><span class="sxs-lookup"><span data-stu-id="c42e8-103">Add and delete animations</span></span>



<span data-ttu-id="c42e8-104">Mit Listenanimationen können Sie einzelne oder mehrere Elemente in einer Sammlung wie z. B. einem Fotoalbum oder einer Liste mit Suchergebnissen einfügen oder entfernen.</span><span class="sxs-lookup"><span data-stu-id="c42e8-104">List animations let you insert or remove single or multiple items from a collection, such as a photo album or a list of search results.</span></span>

> <span data-ttu-id="c42e8-105">**Wichtige APIs**: [**AddDeleteThemeTransition class**](https://msdn.microsoft.com/library/windows/apps/br243048)</span><span class="sxs-lookup"><span data-stu-id="c42e8-105">**Important APIs**: [**AddDeleteThemeTransition class**](https://msdn.microsoft.com/library/windows/apps/br243048)</span></span>


## <a name="dos-and-donts"></a><span data-ttu-id="c42e8-106">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="c42e8-106">Do's and don'ts</span></span>


-   <span data-ttu-id="c42e8-107">Verwenden Sie Listenanimationen, um einer bestehenden Menge von Elementen ein einzelnes neues Element hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="c42e8-107">Use list animations to add a single new item to an existing set of items.</span></span> <span data-ttu-id="c42e8-108">Verwenden Sie diese Animationen beispielsweise, wenn eine neue E-Mail eingeht oder ein neues Foto in eine vorhandene Serie importiert wird.</span><span class="sxs-lookup"><span data-stu-id="c42e8-108">For example, use them when a new email arrives or when a new photo is imported into an existing set.</span></span>
-   <span data-ttu-id="c42e8-109">Verwenden Sie Listenanimationen, um einer bestehenden Menge von Elementen mehrere Elemente gleichzeitig hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="c42e8-109">Use list animations to add several items to a set at one time.</span></span> <span data-ttu-id="c42e8-110">Verwenden Sie diese Animationen beispielsweise, wenn Sie eine neue Fotoserie in eine vorhandene Sammlung importieren.</span><span class="sxs-lookup"><span data-stu-id="c42e8-110">For example, use them when you import a new set of photos to an existing collection.</span></span> <span data-ttu-id="c42e8-111">Wenn mehrere Elemente hinzugefügt oder gelöscht werden, sollte der Vorgang für alle Elemente gleichzeitig erfolgen, ohne dass es zwischen den Aktionen für die einzelnen Objekte zu Verzögerungen kommt.</span><span class="sxs-lookup"><span data-stu-id="c42e8-111">The addition or deletion of multiple items should happen at the same time, with no delay between the action on the individual objects.</span></span>
-   <span data-ttu-id="c42e8-112">Verwenden Sie Listenanimationen für das Hinzufügen und Löschen als Paar.</span><span class="sxs-lookup"><span data-stu-id="c42e8-112">Use add and delete list animations as a pair.</span></span> <span data-ttu-id="c42e8-113">Verwenden Sie immer, wenn Sie eine dieser Animationen verwenden, die zugehörige Animation für die entgegengesetzte Aktion.</span><span class="sxs-lookup"><span data-stu-id="c42e8-113">Whenever you use one of these animations, use the corresponding animation for the opposite action.</span></span>
-   <span data-ttu-id="c42e8-114">Verwenden Sie Listenanimationen mit einer Liste von Elementen, in der Sie ein Element oder eine Gruppe von Elementen gleichzeitig hinzufügen oder löschen können.</span><span class="sxs-lookup"><span data-stu-id="c42e8-114">Use list animations with a list of items to which you can add or delete one element or group of elements at once.</span></span>
-   <span data-ttu-id="c42e8-115">Verwenden Sie Listenanimationen nicht, um einen Container anzuzeigen oder zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="c42e8-115">Don't use list animations to display or remove a container.</span></span> <span data-ttu-id="c42e8-116">Diese Animationen sind für Elemente einer bereits angezeigten Auflistung oder Menge vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="c42e8-116">These animations are for members of a collection or set that is already being displayed.</span></span> <span data-ttu-id="c42e8-117">Verwenden Sie Popupanimationen, um einen kurzlebigen Container auf der App-Oberfläche ein- oder auszublenden.</span><span class="sxs-lookup"><span data-stu-id="c42e8-117">Use pop-up animations to show or hide a transient container on top of the app surface.</span></span> <span data-ttu-id="c42e8-118">Verwenden Sie Inhaltsübergangsanimationen, um einen Container, der Teil der App-Oberfläche ist, anzuzeigen oder zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="c42e8-118">Use content transition animations to display or replace a container that is part of the app surface.</span></span>
-   <span data-ttu-id="c42e8-119">Verwenden Sie Listenanimationen nicht für eine vollständige Menge von Elementen.</span><span class="sxs-lookup"><span data-stu-id="c42e8-119">Don't use list animations on an entire set of items.</span></span> <span data-ttu-id="c42e8-120">Verwenden Sie die Inhaltsübergangsanimationen, um eine vollständige Auflistung innerhalb des Containers hinzuzufügen oder zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="c42e8-120">Use the content transition animations to add or remove an entire collection within your container.</span></span>



## <a name="related-articles"></a><span data-ttu-id="c42e8-121">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="c42e8-121">Related articles</span></span>

* [<span data-ttu-id="c42e8-122">Übersicht über Animationen</span><span class="sxs-lookup"><span data-stu-id="c42e8-122">Animations overview</span></span>](https://msdn.microsoft.com/library/windows/apps/mt187350)
* [<span data-ttu-id="c42e8-123">Animieren von Hinzufügungen und Löschungen in Listen</span><span class="sxs-lookup"><span data-stu-id="c42e8-123">Animating list additions and deletions</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/jj649430)
* [<span data-ttu-id="c42e8-124">Schnellstart: Animieren der Benutzeroberfläche mithilfe von Bibliotheksanimationen</span><span class="sxs-lookup"><span data-stu-id="c42e8-124">Quickstart: Animating your UI using library animations</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh452703)
* [**<span data-ttu-id="c42e8-125">AddDeleteThemeTransition-Klasse</span><span class="sxs-lookup"><span data-stu-id="c42e8-125">AddDeleteThemeTransition class</span></span>**](https://msdn.microsoft.com/library/windows/apps/br243048)

 

 




