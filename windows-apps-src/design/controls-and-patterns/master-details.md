---
author: Jwmsft
Description: The master/detail pattern displays a master list and the details for the currently selected item. This pattern is frequently used for email and contact lists/address books.
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
ms.localizationpriority: medium
ms.openlocfilehash: f1236c2ade0423f6e092024e786741f3f3bf6d11
ms.sourcegitcommit: 933e71a31989f8063b020746fdd16e9da94a44c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2018
ms.locfileid: "4532674"
---
# <a name="masterdetails-pattern"></a><span data-ttu-id="5205b-103">Master/Details-Muster</span><span class="sxs-lookup"><span data-stu-id="5205b-103">Master/details pattern</span></span>

 

<span data-ttu-id="5205b-104">Das Master/Details-Muster verfügt über einen Masterbereich (in der Regel mit einer [Listenansicht](lists.md)) und einen Detailbereich für Inhalte.</span><span class="sxs-lookup"><span data-stu-id="5205b-104">The master/details pattern has a master pane (usually with a [list view](lists.md)) and a details pane for content.</span></span> <span data-ttu-id="5205b-105">Wenn ein Element in der Masterliste ausgewählt wird, wird der Detailbereich aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="5205b-105">When an item in the master list is selected, the details pane is updated.</span></span> <span data-ttu-id="5205b-106">Dieses Muster wird häufig für E-Mails und Adressbücher verwendet.</span><span class="sxs-lookup"><span data-stu-id="5205b-106">This pattern is frequently used for email and address books.</span></span>

> <span data-ttu-id="5205b-107">**Wichtige APIs**: [ListView-Klasse](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.ListView), [SplitView-Klasse](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.splitview)</span><span class="sxs-lookup"><span data-stu-id="5205b-107">**Important APIs**: [ListView class](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.ListView), [SplitView class](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.splitview)</span></span>

![Beispiel für das Master/Detail-Muster](images/HIGSecOne_MasterDetail.png)

## <a name="is-this-the-right-pattern"></a><span data-ttu-id="5205b-109">Ist dies das richtige Muster?</span><span class="sxs-lookup"><span data-stu-id="5205b-109">Is this the right pattern?</span></span>

<span data-ttu-id="5205b-110">Master/Details-Muster eignet sich gut für Folgendes:</span><span class="sxs-lookup"><span data-stu-id="5205b-110">The master/details pattern works well if you want to:</span></span>

-   <span data-ttu-id="5205b-111">Erstellen einer E-Mail-App, eines Adressbuchs oder einer anderen App, die auf einem Listen-Details-Layout basiert</span><span class="sxs-lookup"><span data-stu-id="5205b-111">Build an email app, address book, or any app that is based on a list-details layout.</span></span>
-   <span data-ttu-id="5205b-112">Suchen und Priorisieren einer großen Sammlung von Inhalten</span><span class="sxs-lookup"><span data-stu-id="5205b-112">Locate and prioritize a large collection of content.</span></span>
-   <span data-ttu-id="5205b-113">Schnelles Hinzufügen und Entfernen von Elementen aus einer Liste und gleichzeitiges Wechseln zwischen Kontexten</span><span class="sxs-lookup"><span data-stu-id="5205b-113">Allow the quick addition and removal of items from a list while working back-and-forth between contexts.</span></span>

## <a name="choose-the-right-style"></a><span data-ttu-id="5205b-114">Auswählen des richtigen Formats</span><span class="sxs-lookup"><span data-stu-id="5205b-114">Choose the right style</span></span>

<span data-ttu-id="5205b-115">Beim Implementieren des Master/Details-Musters ist es ratsam, je nach Größe der verfügbaren Bildschirmfläche das gestapelte Format oder das Format mit paralleler Anordnung zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="5205b-115">When implementing the master/details pattern, we recommend that you use either the stacked style or the side-by-side style, based on the amount of available screen space.</span></span>

| <span data-ttu-id="5205b-116">Verfügbare Fensterbreite</span><span class="sxs-lookup"><span data-stu-id="5205b-116">Available window width</span></span> | <span data-ttu-id="5205b-117">Empfohlenes Format</span><span class="sxs-lookup"><span data-stu-id="5205b-117">Recommended style</span></span> |
|------------------------|-------------------|
| <span data-ttu-id="5205b-118">320Epx - 640Epx</span><span class="sxs-lookup"><span data-stu-id="5205b-118">320 epx-640 epx</span></span>        | <span data-ttu-id="5205b-119">Gestapelt</span><span class="sxs-lookup"><span data-stu-id="5205b-119">Stacked</span></span>           |
| <span data-ttu-id="5205b-120">641Epx oder breiter</span><span class="sxs-lookup"><span data-stu-id="5205b-120">641 epx or wider</span></span>       | <span data-ttu-id="5205b-121">Nebeneinander</span><span class="sxs-lookup"><span data-stu-id="5205b-121">Side-by-side</span></span>      |

 
## <a name="stacked-style"></a><span data-ttu-id="5205b-122">Gestapeltes Format</span><span class="sxs-lookup"><span data-stu-id="5205b-122">Stacked style</span></span>

<span data-ttu-id="5205b-123">Im gestapelten Format ist jeweils nur ein Bereich sichtbar: die Master- oder der Detailbereich.</span><span class="sxs-lookup"><span data-stu-id="5205b-123">In the stacked style, only one pane is visible at a time: the master or the details.</span></span>

![Master/Details im Stapelmodus](images/patterns-md-stacked.png)

<span data-ttu-id="5205b-125">Der Benutzer beginnt im Masterbereich und führt einen Drilldown zum Detailbereich durch, indem er ein Element in der Masterliste auswählt.</span><span class="sxs-lookup"><span data-stu-id="5205b-125">The user starts at the master pane and "drills down" to the details pane by selecting an item in the master list.</span></span> <span data-ttu-id="5205b-126">Für den Benutzer sieht es so aus, als ob sich die Masteransicht und die Detailansicht auf zwei getrennten Seiten befinden.</span><span class="sxs-lookup"><span data-stu-id="5205b-126">To the user, it appears as though the master and details views exist on two separate pages.</span></span>

### <a name="create-a-stacked-masterdetails-pattern"></a><span data-ttu-id="5205b-127">Erstellen eines gestapelten Master/Details-Musters</span><span class="sxs-lookup"><span data-stu-id="5205b-127">Create a stacked master/details pattern</span></span>

<span data-ttu-id="5205b-128">Eine Möglichkeit zur Erstellung des gestapelten Master/Details-Musters ist die Verwendung separater Seiten für den Masterbereich und den Detailbereich.</span><span class="sxs-lookup"><span data-stu-id="5205b-128">One way to create the stacked master/details pattern is to use separate pages for the master pane and the details pane.</span></span> <span data-ttu-id="5205b-129">Ordnen Sie die Masteransicht auf einer Seite und den Detailbereich auf einer separaten Seite an.</span><span class="sxs-lookup"><span data-stu-id="5205b-129">Place the master view on one page, and the details pane on a separate page.</span></span>

![Teile der Master/Details-Ansicht im gestapelten Format](images/patterns-md-stacked-parts.png)

<span data-ttu-id="5205b-131">Für die Seite mit der Masteransicht eignet sich ein [Listenansicht](lists.md)-Steuerelement gut für die Darstellung von Listen, die Bilder und Text enthalten können.</span><span class="sxs-lookup"><span data-stu-id="5205b-131">For the master view page, a [list view](lists.md) control works well for presenting lists that can contain images and text.</span></span> 

<span data-ttu-id="5205b-132">Verwenden Sie für die Seite mit der Detailansicht das am besten geeignete [Inhaltselement](../layout/layout-panels.md).</span><span class="sxs-lookup"><span data-stu-id="5205b-132">For the details view page, use the [content element](../layout/layout-panels.md) that makes the most sense.</span></span> <span data-ttu-id="5205b-133">Wenn viele separate Felder vorhanden sind, können Sie ein Layout vom Typ **Raster** zum Anordnen der Elemente in einem Formular verwenden.</span><span class="sxs-lookup"><span data-stu-id="5205b-133">If you have a lot of separate fields, consider using a **Grid** layout to arrange elements into a form.</span></span>

<span data-ttu-id="5205b-134">Weitere Informationen zur Navigation zwischen Seiten finden Sie unter [Navigationsverlauf und Rückwärtsnavigation für UWP-Apps](../basics/navigation-history-and-backwards-navigation.md).</span><span class="sxs-lookup"><span data-stu-id="5205b-134">For navigation between pages, see [navigation history and backwards navigation for UWP apps](../basics/navigation-history-and-backwards-navigation.md).</span></span>

## <a name="side-by-side-style"></a><span data-ttu-id="5205b-135">Format mit paralleler Anordnung</span><span class="sxs-lookup"><span data-stu-id="5205b-135">Side-by-side style</span></span>

<span data-ttu-id="5205b-136">Im Format mit paralleler Anordnung sind Master- und Detailbereich gleichzeitig sichtbar.</span><span class="sxs-lookup"><span data-stu-id="5205b-136">In the side-by-side style, the master pane and details pane are visible at the same time.</span></span>

![Das Master/Details-Muster](images/patterns-masterdetail-400x227.png)

<span data-ttu-id="5205b-138">Für die Liste im Masterbereich wird eine visuelle Auswahlmethode genutzt, um das derzeit ausgewählte Element anzugeben.</span><span class="sxs-lookup"><span data-stu-id="5205b-138">The list in the master pane has a selection visual to indicate the currently selected item.</span></span> <span data-ttu-id="5205b-139">Wenn in der Masterliste ein neues Element ausgewählt wird, wird der Detailbereich aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="5205b-139">Selecting a new item in the master list updates the details pane.</span></span>

### <a name="create-a-side-by-side-masterdetails-pattern"></a><span data-ttu-id="5205b-140">Erstellen eines parallelen Master/Details-Musters</span><span class="sxs-lookup"><span data-stu-id="5205b-140">Create a side-by-side master/details pattern</span></span>

<span data-ttu-id="5205b-141">Eine Möglichkeit zur Erstellung eines parallelen Master/Details-Musters ist die Verwendung des Steuerelements für die [geteilte Ansicht](split-view.md).</span><span class="sxs-lookup"><span data-stu-id="5205b-141">One way to create a side-by-side master/details pattern is to use the [split view](split-view.md) control.</span></span> <span data-ttu-id="5205b-142">Ordnen Sie die Masteransicht im Bereich der geteilten Ansicht und die Detailansicht im Inhaltsbereich der geteilten Ansicht an.</span><span class="sxs-lookup"><span data-stu-id="5205b-142">Place the master view in the split view pane, and the details view in the split view content.</span></span>

![Teile der geteilten Master/Detailansicht](images/patterns_md_splitview_parts.png)

<span data-ttu-id="5205b-144">Für den Masterbereich eignet sich ein [Listenansicht](lists.md)-Steuerelement gut für die Darstellung von Listen, die Bilder und Text enthalten können.</span><span class="sxs-lookup"><span data-stu-id="5205b-144">For the master pane, a [list view](lists.md) control works well for presenting lists that can contain images and text.</span></span>

<span data-ttu-id="5205b-145">Verwenden Sie für den Detailinhalt das am besten geeignete [Inhaltselement](../layout/layout-panels.md).</span><span class="sxs-lookup"><span data-stu-id="5205b-145">For the details content, use the [content element](../layout/layout-panels.md) that makes the most sense.</span></span> <span data-ttu-id="5205b-146">Wenn viele separate Felder vorhanden sind, können Sie ein Layout vom Typ **Raster** zum Anordnen der Elemente in einem Formular verwenden.</span><span class="sxs-lookup"><span data-stu-id="5205b-146">If you have a lot of separate fields, consider using a **Grid** layout to arrange elements into a form.</span></span>

## <a name="adaptive-layout"></a><span data-ttu-id="5205b-147">Adaptives Layout</span><span class="sxs-lookup"><span data-stu-id="5205b-147">Adaptive layout</span></span>

<span data-ttu-id="5205b-148">Um ein Master/Details-Muster für jede Bildschirmgröße zu implementieren, erstellen Sie eine reaktionsfähige Benutzeroberfläche mit einem [adaptiven Layout](../layout/layouts-with-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="5205b-148">To implement a master/details pattern for any screen size, create a responsive UI with an [adaptive layout](../layout/layouts-with-xaml.md).</span></span>

![Adaptives Master/Details-Layout](images/patterns_masterdetail.png)

### <a name="create-an-adaptive-masterdetails-pattern"></a><span data-ttu-id="5205b-150">Erstellen eines adaptiven Master/Detail-Musters</span><span class="sxs-lookup"><span data-stu-id="5205b-150">Create an adaptive master/details pattern</span></span>
<span data-ttu-id="5205b-151">Um ein adaptives Layout zu erstellen, definieren Sie verschiedene [**VisualStates**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.visualstate) für Ihre Benutzeroberfläche, und deklarieren Sie Haltepunkte für die verschiedenen Zustände mit [**AdaptiveTriggers**](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.AdaptiveTrigger).</span><span class="sxs-lookup"><span data-stu-id="5205b-151">To create an adaptive layout, define different [**VisualStates**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.visualstate) for your UI, and declare breakpoints for the different states with [**AdaptiveTriggers**](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.AdaptiveTrigger).</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="5205b-152">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="5205b-152">Get the sample code</span></span>

<span data-ttu-id="5205b-153">In den folgenden Beispielen implementieren Sie das Master/Detail-Muster mit adaptiven Layouts und veranschaulichen das Binden von Daten an statische, Datenbank- und Online-Ressourcen:</span><span class="sxs-lookup"><span data-stu-id="5205b-153">The following samples implement the master/details pattern with adaptive layouts and demonstrate data binding to static, database, and online resources:</span></span> 
- [<span data-ttu-id="5205b-154">Master/Details-Beispiel</span><span class="sxs-lookup"><span data-stu-id="5205b-154">Master/detail sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlMasterDetail) 
- [<span data-ttu-id="5205b-155">Beispiel für Master/Details sowie Auswahl</span><span class="sxs-lookup"><span data-stu-id="5205b-155">Master/Details plus Selection sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlListView)
- [<span data-ttu-id="5205b-156">Master/Detail-Beispiel für Windows Template Studio</span><span class="sxs-lookup"><span data-stu-id="5205b-156">Windows Template Studio Master/Detail sample</span></span>](https://github.com/Microsoft/WindowsTemplateStudio/tree/master/templates/Uwp/Pages/MasterDetail)
- [<span data-ttu-id="5205b-157">Beispieldatenbank Kundenbestellung</span><span class="sxs-lookup"><span data-stu-id="5205b-157">Customer orders database sample</span></span>](https://github.com/Microsoft/Windows-appsample-customers-orders-database)
- [<span data-ttu-id="5205b-158">RSS-Reader-Beispiel</span><span class="sxs-lookup"><span data-stu-id="5205b-158">RSS Reader sample</span></span>](https://github.com/Microsoft/Windows-appsample-rssreader)

## <a name="related-articles"></a><span data-ttu-id="5205b-159">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="5205b-159">Related articles</span></span>

- [<span data-ttu-id="5205b-160">Listen</span><span class="sxs-lookup"><span data-stu-id="5205b-160">Lists</span></span>](lists.md)
- [<span data-ttu-id="5205b-161">Suche</span><span class="sxs-lookup"><span data-stu-id="5205b-161">Search</span></span>](search.md)
- [<span data-ttu-id="5205b-162">App- und Befehlsleisten</span><span class="sxs-lookup"><span data-stu-id="5205b-162">App and command bars</span></span>](app-bars.md)
- [<span data-ttu-id="5205b-163">ListView-Klasse</span><span class="sxs-lookup"><span data-stu-id="5205b-163">ListView class</span></span>](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.ListView)
- [<span data-ttu-id="5205b-164">SplitView-Klasse</span><span class="sxs-lookup"><span data-stu-id="5205b-164">SplitView class</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.splitview)
