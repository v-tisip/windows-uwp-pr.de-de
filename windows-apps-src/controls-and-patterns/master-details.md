---
author: Jwmsft
Description: "Beim Master/Details-Muster werden eine Masterliste und die Details für das derzeit ausgewählte Element angezeigt. Dieses Muster wird häufig für E-Mails und Kontaktlisten/Adressbücher verwendet."
title: Master/Details
ms.assetid: 45C9FE8B-ECA6-44BF-8DDE-7D12ED34A7F7
label: Master/details
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.openlocfilehash: 49a586aac0c846cdad02f8448532238bd3eb8551
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="masterdetails-pattern"></a><span data-ttu-id="440ec-105">Master/Details-Muster</span><span class="sxs-lookup"><span data-stu-id="440ec-105">Master/details pattern</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

<span data-ttu-id="440ec-106">Das Master/Details-Muster verfügt über einen Masterbereich (in der Regel mit einer [Listenansicht](lists.md)) und einen Detailbereich für Inhalte.</span><span class="sxs-lookup"><span data-stu-id="440ec-106">The master/details pattern has a master pane (usually with a [list view](lists.md)) and a details pane for content.</span></span> <span data-ttu-id="440ec-107">Wenn ein Element in der Masterliste ausgewählt wird, wird der Detailbereich aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="440ec-107">When an item in the master list is selected, the details pane is updated.</span></span> <span data-ttu-id="440ec-108">Dieses Muster wird häufig für E-Mails und Adressbücher verwendet.</span><span class="sxs-lookup"><span data-stu-id="440ec-108">This pattern is frequently used for email and address books.</span></span>

> <span data-ttu-id="440ec-109">**Wichtige APIs**: [ListView-Klasse](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.ListView), [SplitView-Klasse](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.splitview)</span><span class="sxs-lookup"><span data-stu-id="440ec-109">**Important APIs**: [ListView class](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.ListView), [SplitView class](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.splitview)</span></span>

![Beispiel für das Master/Detail-Muster](images/HIGSecOne_MasterDetail.png)

## <a name="is-this-the-right-pattern"></a><span data-ttu-id="440ec-111">Ist dies das richtige Muster?</span><span class="sxs-lookup"><span data-stu-id="440ec-111">Is this the right pattern?</span></span>

<span data-ttu-id="440ec-112">Master/Details-Muster eignet sich gut für Folgendes:</span><span class="sxs-lookup"><span data-stu-id="440ec-112">The master/details pattern works well if you want to:</span></span>

-   <span data-ttu-id="440ec-113">Erstellen einer E-Mail-App, eines Adressbuchs oder einer anderen App, die auf einem Listen-Details-Layout basiert</span><span class="sxs-lookup"><span data-stu-id="440ec-113">Build an email app, address book, or any app that is based on a list-details layout.</span></span>
-   <span data-ttu-id="440ec-114">Suchen und Priorisieren einer großen Sammlung von Inhalten</span><span class="sxs-lookup"><span data-stu-id="440ec-114">Locate and prioritize a large collection of content.</span></span>
-   <span data-ttu-id="440ec-115">Schnelles Hinzufügen und Entfernen von Elementen aus einer Liste und gleichzeitiges Wechseln zwischen Kontexten</span><span class="sxs-lookup"><span data-stu-id="440ec-115">Allow the quick addition and removal of items from a list while working back-and-forth between contexts.</span></span>

## <a name="choose-the-right-style"></a><span data-ttu-id="440ec-116">Auswählen des richtigen Formats</span><span class="sxs-lookup"><span data-stu-id="440ec-116">Choose the right style</span></span>

<span data-ttu-id="440ec-117">Beim Implementieren des Master/Details-Musters ist es ratsam, je nach Größe der verfügbaren Bildschirmfläche das gestapelte Format oder das Format mit paralleler Anordnung zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="440ec-117">When implementing the master/details pattern, we recommend that you use either the stacked style or the side-by-side style, based on the amount of available screen space.</span></span>

| <span data-ttu-id="440ec-118">Verfügbare Fensterbreite</span><span class="sxs-lookup"><span data-stu-id="440ec-118">Available window width</span></span> | <span data-ttu-id="440ec-119">Empfohlenes Format</span><span class="sxs-lookup"><span data-stu-id="440ec-119">Recommended style</span></span> |
|------------------------|-------------------|
| <span data-ttu-id="440ec-120">320Epx - 719Epx</span><span class="sxs-lookup"><span data-stu-id="440ec-120">320 epx-719 epx</span></span>        | <span data-ttu-id="440ec-121">Gestapelt</span><span class="sxs-lookup"><span data-stu-id="440ec-121">Stacked</span></span>           |
| <span data-ttu-id="440ec-122">720Epx oder breiter</span><span class="sxs-lookup"><span data-stu-id="440ec-122">720 epx or wider</span></span>       | <span data-ttu-id="440ec-123">Nebeneinander</span><span class="sxs-lookup"><span data-stu-id="440ec-123">Side-by-side</span></span>      |

 
## <a name="stacked-style"></a><span data-ttu-id="440ec-124">Gestapeltes Format</span><span class="sxs-lookup"><span data-stu-id="440ec-124">Stacked style</span></span>

<span data-ttu-id="440ec-125">Im gestapelten Format ist jeweils nur ein Bereich sichtbar: die Master- oder der Detailbereich.</span><span class="sxs-lookup"><span data-stu-id="440ec-125">In the stacked style, only one pane is visible at a time: the master or the details.</span></span>

![Master/Details im Stapelmodus](images/patterns-md-stacked.png)

<span data-ttu-id="440ec-127">Der Benutzer beginnt im Masterbereich und führt einen Drilldown zum Detailbereich durch, indem er ein Element in der Masterliste auswählt.</span><span class="sxs-lookup"><span data-stu-id="440ec-127">The user starts at the master pane and "drills down" to the details pane by selecting an item in the master list.</span></span> <span data-ttu-id="440ec-128">Für den Benutzer sieht es so aus, als ob sich die Masteransicht und die Detailansicht auf zwei getrennten Seiten befinden.</span><span class="sxs-lookup"><span data-stu-id="440ec-128">To the user, it appears as though the master and details views exist on two separate pages.</span></span>

### <a name="create-a-stacked-masterdetails-pattern"></a><span data-ttu-id="440ec-129">Erstellen eines gestapelten Master/Details-Musters</span><span class="sxs-lookup"><span data-stu-id="440ec-129">Create a stacked master/details pattern</span></span>

<span data-ttu-id="440ec-130">Eine Möglichkeit zur Erstellung des gestapelten Master/Details-Musters ist die Verwendung separater Seiten für den Masterbereich und den Detailbereich.</span><span class="sxs-lookup"><span data-stu-id="440ec-130">One way to create the stacked master/details pattern is to use separate pages for the master pane and the details pane.</span></span> <span data-ttu-id="440ec-131">Ordnen Sie die Listenansicht, in der die Masterliste bereitgestellt wird, auf einer Seite und das Inhaltselement für den Detailbereich auf einer separaten Seite an.</span><span class="sxs-lookup"><span data-stu-id="440ec-131">Place the list view that provides the master list on one page, and the content element for the details pane on a separate page.</span></span>

![Teile der Master/Details-Ansicht im gestapelten Format](images/patterns-md-stacked-parts.png)

<span data-ttu-id="440ec-133">Für den Masterbereich eignet sich ein [Listenansicht](lists.md)-Steuerelement gut für die Darstellung von Listen, die Bilder und Text enthalten können.</span><span class="sxs-lookup"><span data-stu-id="440ec-133">For the master pane, a [list view](lists.md) control works well for presenting lists that can contain images and text.</span></span>

<span data-ttu-id="440ec-134">Verwenden Sie für den Detailbereich das am besten geeignete Inhaltselement.</span><span class="sxs-lookup"><span data-stu-id="440ec-134">For the details pane, use the content element that makes the most sense.</span></span> <span data-ttu-id="440ec-135">Wenn viele separate Felder vorhanden sind, erwägen Sie die Verwendung eines Rasterlayouts zum Anordnen der Elemente in einem Formular.</span><span class="sxs-lookup"><span data-stu-id="440ec-135">If you have a lot of separate fields, consider using a grid layout to arrange elements into a form.</span></span>

## <a name="side-by-side-style"></a><span data-ttu-id="440ec-136">Format mit paralleler Anordnung</span><span class="sxs-lookup"><span data-stu-id="440ec-136">Side-by-side style</span></span>

<span data-ttu-id="440ec-137">Im Format mit paralleler Anordnung sind Master- und Detailbereich gleichzeitig sichtbar.</span><span class="sxs-lookup"><span data-stu-id="440ec-137">In the side-by-side style, the master pane and details pane are visible at the same time.</span></span>

![Das Master/Details-Muster](images/patterns-masterdetail-400x227.png)

<span data-ttu-id="440ec-139">Für die Liste im Masterbereich wird eine visuelle Auswahlmethode genutzt, um das derzeit ausgewählte Element anzugeben.</span><span class="sxs-lookup"><span data-stu-id="440ec-139">The list in the master pane has a selection visual to indicate the currently selected item.</span></span> <span data-ttu-id="440ec-140">Wenn in der Masterliste ein neues Element ausgewählt wird, wird der Detailbereich aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="440ec-140">Selecting a new item in the master list updates the details pane.</span></span>

### <a name="create-a-side-by-side-masterdetails-pattern"></a><span data-ttu-id="440ec-141">Erstellen eines parallelen Master/Details-Musters</span><span class="sxs-lookup"><span data-stu-id="440ec-141">Create a side-by-side master/details pattern</span></span>

<span data-ttu-id="440ec-142">Für den Masterbereich eignet sich ein [Listenansicht](lists.md)-Steuerelement gut für die Darstellung von Listen, die Bilder und Text enthalten können.</span><span class="sxs-lookup"><span data-stu-id="440ec-142">For the master pane, a [list view](lists.md) control works well for presenting lists that can contain images and text.</span></span>

<span data-ttu-id="440ec-143">Verwenden Sie für den Detailbereich das am besten geeignete Inhaltselement.</span><span class="sxs-lookup"><span data-stu-id="440ec-143">For the details pane, use the content element that makes the most sense.</span></span> <span data-ttu-id="440ec-144">Sind mehrere separate Felder vorhanden, sollten Sie die Verwendung eines Rasterlayouts erwägen, um die Elemente als Formular anzuordnen.</span><span class="sxs-lookup"><span data-stu-id="440ec-144">If you have a lot of separate fields, consider using a grid layout to arrange elements into a form.</span></span>

## <a name="get-the-code-samples"></a><span data-ttu-id="440ec-145">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="440ec-145">Get the code samples</span></span>

<span data-ttu-id="440ec-146">Beispielcode, der das Master/Detail-Muster veranschaulicht, finden Sie hier:</span><span class="sxs-lookup"><span data-stu-id="440ec-146">For sample code that shows the master/details pattern, see these samples:</span></span> 

- [<span data-ttu-id="440ec-147">Beispieldatenbank Kundenbestellung</span><span class="sxs-lookup"><span data-stu-id="440ec-147">Customer orders database sample</span></span>](https://github.com/Microsoft/Windows-appsample-customers-orders-database) 
- [<span data-ttu-id="440ec-148">Beispiele für Raster- und Listenansicht</span><span class="sxs-lookup"><span data-stu-id="440ec-148">ListView and GridView sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619900)
- [<span data-ttu-id="440ec-149">RSS-Reader-Beispiel</span><span class="sxs-lookup"><span data-stu-id="440ec-149">RSS Reader sample</span></span>](https://github.com/Microsoft/Windows-appsample-rssreader)

## <a name="related-articles"></a><span data-ttu-id="440ec-150">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="440ec-150">Related articles</span></span>

- [<span data-ttu-id="440ec-151">Listen</span><span class="sxs-lookup"><span data-stu-id="440ec-151">Lists</span></span>](lists.md)
- [<span data-ttu-id="440ec-152">Suche</span><span class="sxs-lookup"><span data-stu-id="440ec-152">Search</span></span>](search.md)
- [<span data-ttu-id="440ec-153">App- und Befehlsleisten</span><span class="sxs-lookup"><span data-stu-id="440ec-153">App and command bars</span></span>](app-bars.md)
- [<span data-ttu-id="440ec-154">Listenansichtsklasse</span><span class="sxs-lookup"><span data-stu-id="440ec-154">ListView class</span></span>](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.ListView)
