---
author: muhsinking
Description: Use nested UI to enable multiple actions on a list item
title: Geschachtelte UI bei Listenelementen
label: Nested UI in list items
template: detail.hbs
ms.author: mukin
ms.date: 05/19/2017
ms.topic: article
keywords: Windows10, UWP
ms.assetid: 60a29717-56f2-4388-a9ff-0098e34d5896
pm-contact: chigy
design-contact: kimsea
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: f9bb6daeb01e264cf9cdb0fa9ee9c66738fec972
ms.sourcegitcommit: cbe7cf620622a5e4df7414f9e38dfecec1cfca99
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "7425901"
---
# <a name="nested-ui-in-list-items"></a><span data-ttu-id="2b214-103">Geschachtelte UI bei Listenelementen</span><span class="sxs-lookup"><span data-stu-id="2b214-103">Nested UI in list items</span></span>

 

<span data-ttu-id="2b214-104">Eine geschachtelte UI ist eine Benutzeroberfläche (User Interface, UI) mit geschachtelten Steuerelementen, die in einem Container eingeschlossen sind und auch unabhängig den Fokus erhalten kann.</span><span class="sxs-lookup"><span data-stu-id="2b214-104">Nested UI is a user interface (UI) that exposes nested actionable controls enclosed inside a container that also can take independent focus.</span></span>

<span data-ttu-id="2b214-105">Sie können dem Benutzer mit geschachtelten UIs weitere Optionen zur Verfügung stellen, mit denen sie wichtige Aktionen schneller ausführen können.</span><span class="sxs-lookup"><span data-stu-id="2b214-105">You can use nested UI to present a user with additional options that help accelerate taking important actions.</span></span> <span data-ttu-id="2b214-106">Bedenken Sie jedoch, dass die Benutzeroberfläche komplizierter wird, je mehr Aktionen Sie anbieten.</span><span class="sxs-lookup"><span data-stu-id="2b214-106">However, the more actions you expose, the more complicated your UI becomes.</span></span> <span data-ttu-id="2b214-107">Wenn Sie diese Art von Benutzeroberfläche verwenden, sollten Sie besonders vorsichtig vorgehen.</span><span class="sxs-lookup"><span data-stu-id="2b214-107">You need to take extra care when you choose to use this UI pattern.</span></span> <span data-ttu-id="2b214-108">Dieser Artikel enthält Richtlinien, um die beste Vorgehensweise für Ihre UI zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="2b214-108">This article provides guidelines to help you determine the best course of action for your particular UI.</span></span>

> <span data-ttu-id="2b214-109">**Wichtige APIs**: [ListView-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx), [GridView-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.gridview.aspx)</span><span class="sxs-lookup"><span data-stu-id="2b214-109">**Important APIs**: [ListView class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx), [GridView class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.gridview.aspx)</span></span>

<span data-ttu-id="2b214-110">In diesem Artikel erläutern wir die Erstellung von geschachtelten UIs in [ListView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx)- und in [GridView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.gridview.aspx)-Elementen.</span><span class="sxs-lookup"><span data-stu-id="2b214-110">In this article, we discuss the creation of nested UI in [ListView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx) and [GridView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.gridview.aspx) items.</span></span> <span data-ttu-id="2b214-111">In diesem Abschnitt werden andere Formen von geschachtelten UIs nicht berücksichtigt, aber die hier gegebenen Konzepte lassen sich auf andere UIs übertragen.</span><span class="sxs-lookup"><span data-stu-id="2b214-111">While this section does not talk about other nested UI cases, these concepts are transferrable.</span></span> <span data-ttu-id="2b214-112">Bevor Sie beginnen, sollten Sie mit der allgemeinen Richtlinie für die Verwendung von ListView- und GridView-Steuerelementen in der Benutzeroberfläche vertraut sein, die in den Artikeln [Listen](lists.md) und [Listenansicht und Rasteransicht](listview-and-gridview.md) beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="2b214-112">Before you start, you should be familiar with the general guidance for using ListView or GridView controls in your UI, which is found in the [Lists](lists.md) and [List view and grid view](listview-and-gridview.md) articles.</span></span>

<span data-ttu-id="2b214-113">In diesem Artikel verwenden wir die Begriffe *Liste*, *Listenelement* und *geschachtelte UI* entsprechend den folgenden Definitionen:</span><span class="sxs-lookup"><span data-stu-id="2b214-113">In this article, we use the terms *list*, *list item*, and *nested UI* as defined here:</span></span>
- <span data-ttu-id="2b214-114">*Liste* bezeichnet eine Sammlung von Elementen in einer Listenansicht oder in einer Rasteransicht.</span><span class="sxs-lookup"><span data-stu-id="2b214-114">*List* refers to a collection of items contained in a list view or grid view.</span></span>
- <span data-ttu-id="2b214-115">*Listenelement* bezeichnet ein einzelnes Element in einer Liste, für das der Benutzer bestimmte Aktionen ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="2b214-115">*List item* refers to an individual item that a user can take action on in a list.</span></span>
- <span data-ttu-id="2b214-116">*Geschachtelte UI* bezeichnet UI-Elemente in einem Listenelement, für die der Benutzer bestimmte Aktionen ausführen kann, die sich nicht auf das Listenelement selbst auswirken.</span><span class="sxs-lookup"><span data-stu-id="2b214-116">*Nested UI* refers to UI elements within a list item that a user can take action on separate from taking action on the list item itself.</span></span>

![Komponenten von geschachtelten UIs](images/nested-ui-example-1.png)

> <span data-ttu-id="2b214-118">Hinweis:&nbsp;&nbsp; ListView und GridView sind beide von der Klasse [ListViewBase](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.aspx) abgeleitet, sodass sie dieselbe Funktionalität haben, sie zeigen die Daten jedoch unterschiedlich an.</span><span class="sxs-lookup"><span data-stu-id="2b214-118">NOTE&nbsp;&nbsp; ListView and GridView both derive from the [ListViewBase](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.aspx) class, so they have the same functionality, but display data differently.</span></span> <span data-ttu-id="2b214-119">In diesem Artikel beziehen sich Aussagen zu Listen sowohl auf die ListView- als auch die GridView-Steuerelemente, wenn nicht anders angegeben.</span><span class="sxs-lookup"><span data-stu-id="2b214-119">In this article, when we talk about lists, the info applies to both the ListView and GridView controls.</span></span>

## <a name="primary-and-secondary-actions"></a><span data-ttu-id="2b214-120">Primäre und sekundäre Aktionen</span><span class="sxs-lookup"><span data-stu-id="2b214-120">Primary and secondary actions</span></span>

<span data-ttu-id="2b214-121">Beim Erstellen einer UI mit einer Liste sollten Sie berücksichtigen, welche Aktionen Benutzer über den Elementen dieser Liste ausführen könnten.</span><span class="sxs-lookup"><span data-stu-id="2b214-121">When creating UI with a list, consider what actions the user might take from those list items.</span></span>  

- <span data-ttu-id="2b214-122">Kann der Benutzer auf das Element klicken, um eine Aktion auszuführen?</span><span class="sxs-lookup"><span data-stu-id="2b214-122">Can a user click on the item to perform an action?</span></span>
    - <span data-ttu-id="2b214-123">In der Regel wird durch das Klicken auf ein Listenelement eine Aktion eingeleitet, dies ist jedoch nicht notwendigerweise so.</span><span class="sxs-lookup"><span data-stu-id="2b214-123">Typically, clicking a list item initiates an action, but it doesn't have too.</span></span>
- <span data-ttu-id="2b214-124">Gibt es mehr als eine Aktion, die der Benutzer ausführen kann?</span><span class="sxs-lookup"><span data-stu-id="2b214-124">Is there more than one action the user can take?</span></span>
    - <span data-ttu-id="2b214-125">Beispiel: Wenn Sie in einer Liste von E-Mail-Nachrichten auf eine E-Mail tippen, wird diese geöffnet.</span><span class="sxs-lookup"><span data-stu-id="2b214-125">For example, tapping an email in a list opens that email.</span></span> <span data-ttu-id="2b214-126">Es kann jedoch noch andere Aktionen geben, die der Benutzer möglicherweise ausführen möchte, ohne die E-Mail vorher zu öffnen, beispielsweise die E-Mail löschen.</span><span class="sxs-lookup"><span data-stu-id="2b214-126">However, there might be other actions, like deleting the email, that the user would want to take without opening it first.</span></span> <span data-ttu-id="2b214-127">Es wäre für den Benutzer hilfreich, auf diese Aktion direkt in der Liste zugreifen zu können.</span><span class="sxs-lookup"><span data-stu-id="2b214-127">It would benefit the user to access this action directly in the list.</span></span>
- <span data-ttu-id="2b214-128">Wie sollten die Aktionen für den Benutzer verfügbar gemacht werden?</span><span class="sxs-lookup"><span data-stu-id="2b214-128">How should the actions be exposed to the user?</span></span>
    - <span data-ttu-id="2b214-129">Berücksichtigen Sie alle Arten von Eingabemöglichkeiten.</span><span class="sxs-lookup"><span data-stu-id="2b214-129">Consider all input types.</span></span> <span data-ttu-id="2b214-130">Manche Formen von geschachtelten UIs eignen sich hervorragend für eine Eingabemethode, funktionieren jedoch möglicherweise nicht mit anderen Methoden.</span><span class="sxs-lookup"><span data-stu-id="2b214-130">Some forms of nested UI work great with one method of input, but might not work with other methods.</span></span>  

<span data-ttu-id="2b214-131">Die *primäre Aktion* ist das, was der Benutzer beim Klicken auf ein Element der Liste erwartet.</span><span class="sxs-lookup"><span data-stu-id="2b214-131">The *primary action* is what the user expects to happen when they press the list item.</span></span>

<span data-ttu-id="2b214-132">*Sekundäre Aktionen* sind in der Regel Abkürzungen für Aktionen über Listenelementen.</span><span class="sxs-lookup"><span data-stu-id="2b214-132">*Secondary actions* are typically accelerators associated with list items.</span></span> <span data-ttu-id="2b214-133">Diese Abkürzungen können zur Verwaltung der Liste dienen oder Aktionen in Zusammenhang mit dem Listenelement aufrufen.</span><span class="sxs-lookup"><span data-stu-id="2b214-133">These accelerators can be for list management or actions related to the list item.</span></span>

## <a name="options-for-secondary-actions"></a><span data-ttu-id="2b214-134">Optionen für sekundäre Aktionen</span><span class="sxs-lookup"><span data-stu-id="2b214-134">Options for secondary actions</span></span>

<span data-ttu-id="2b214-135">Wenn Sie eine Listen-UI erstellen, müssen Sie zunächst sicherstellen, dass Sie alle Eingabemethoden berücksichtigen, die UWP unterstützt.</span><span class="sxs-lookup"><span data-stu-id="2b214-135">When creating list UI, you first need to make sure you account for all input methods that UWP supports.</span></span> <span data-ttu-id="2b214-136">Weitere Informationen zu verschiedenen Arten von Eingaben finden Sie unter [Einführung in Eingaben](../input/index.md).</span><span class="sxs-lookup"><span data-stu-id="2b214-136">For more info about different kinds of input, see [Input primer](../input/index.md).</span></span>

<span data-ttu-id="2b214-137">Nachdem Sie sichergestellt haben, dass Ihre App alle Eingaben unterstützt, die UWP unterstützt, sollten Sie entscheiden, ob die sekundären Aktionen Ihrer App wichtig genug sind, um sie als Abkürzungen in der Hauptliste verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="2b214-137">After you have made sure that your app supports all inputs that UWP supports, you should decide if your app’s secondary actions are important enough to expose as accelerators in the main list.</span></span> <span data-ttu-id="2b214-138">Bedenken Sie, dass Ihre Benutzeroberfläche mit jeder weiteren Aktion, die Sie zur Verfügung stellen, komplizierter wird.</span><span class="sxs-lookup"><span data-stu-id="2b214-138">Remember that the more actions you expose, the more complicated your UI becomes.</span></span> <span data-ttu-id="2b214-139">Möchten Sie die sekundären Aktionen wirklich in der Hauptliste der Benutzeroberfläche verfügbar machen, oder können Sie sie an einer anderen Stelle platzieren?</span><span class="sxs-lookup"><span data-stu-id="2b214-139">Do you really need to expose the secondary actions in the main list UI, or can you put them somewhere else?</span></span>

<span data-ttu-id="2b214-140">Wenn Sie weitere Aktionen in die Hauptlisten-UI aufnehmen möchten, sollten dies Aktionen sein, die jederzeit für alle Eingaben zugänglich sein müssen.</span><span class="sxs-lookup"><span data-stu-id="2b214-140">You might consider exposing additional actions in the main list UI when those actions need to be accessible by any input at all times.</span></span>

<span data-ttu-id="2b214-141">Wenn Sie entscheiden, dass es nicht erforderlich ist, in der Hauptlisten-UI sekundäre Aktionen aufzunehmen, gibt es verschiedene andere Methoden, über die Sie diese für den Benutzer verfügbar machen können.</span><span class="sxs-lookup"><span data-stu-id="2b214-141">If you decide that putting secondary actions in the main list UI is not necessary, there are several other ways you can expose them to the user.</span></span> <span data-ttu-id="2b214-142">Nachfolgend finden Sie einige Möglichkeiten, sekundäre Aktionen an anderen Stellen zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="2b214-142">Here are some options you can consider for where to place secondary actions.</span></span>

### <a name="put-secondary-actions-on-the-detail-page"></a><span data-ttu-id="2b214-143">Platzieren der sekundären Aktionen auf der Detailseite</span><span class="sxs-lookup"><span data-stu-id="2b214-143">Put secondary actions on the detail page</span></span>

<span data-ttu-id="2b214-144">Platzieren Sie die sekundären Aktionen auf der Seite, zu der das Listenelement navigiert, wenn es ausgewählt wird.</span><span class="sxs-lookup"><span data-stu-id="2b214-144">Put the secondary actions on the page that the list item navigates to when it’s pressed.</span></span> <span data-ttu-id="2b214-145">Wenn Sie das Master/Details-Muster verwenden, ist die Detailseite häufig eine gute Stelle für sekundäre Aktionen.</span><span class="sxs-lookup"><span data-stu-id="2b214-145">When you use the master/details pattern, the detail page is often a good place to put secondary actions.</span></span>

<span data-ttu-id="2b214-146">Weitere Informationen finden Sie unter [Master/Details-Muster](master-details.md).</span><span class="sxs-lookup"><span data-stu-id="2b214-146">For more info, see the [Master/detail pattern](master-details.md).</span></span>

### <a name="put-secondary-actions-in-a-context-menu"></a><span data-ttu-id="2b214-147">Platzieren der sekundären Aktionen in einem Kontextmenü</span><span class="sxs-lookup"><span data-stu-id="2b214-147">Put secondary actions in a context menu</span></span>

<span data-ttu-id="2b214-148">Platzieren Sie die sekundären Aktionen in einem Kontextmenü, auf das der Benutzer mit der rechten Maustaste oder durch Drücken und Halten zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="2b214-148">Put the secondary actions in a context menu that the user can access via right-click or press-and-hold.</span></span> <span data-ttu-id="2b214-149">Dies bietet den Vorteil, dass der Benutzer eine Aktion ausführen kann, ohne die Detailseite laden zu müssen, z. B. eine E-Mail löschen.</span><span class="sxs-lookup"><span data-stu-id="2b214-149">This provides the benefit of letting the user perform an action, such as deleting an email, without having to load the detail page.</span></span> <span data-ttu-id="2b214-150">Es ist eine empfohlene Vorgehensweise, diese Optionen außerdem auch auf der Detailseite zur Verfügung zu stellen, da Kontextmenüs als Abkürzung gedacht sind, für die die primäre UI tatsächlich an anderer Stelle vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="2b214-150">It's a good practice to also make these options available on the detail page, as context menus are intended to be accelerators rather than primary UI.</span></span>

<span data-ttu-id="2b214-151">Um sekundäre Aktionen verfügbar zu machen, wenn die Eingabe über ein Gamepad oder eine Fernbedienung erfolgt, empfehlen wir, ein Kontextmenü zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="2b214-151">To expose secondary actions when input is from a gamepad or remote control, we recommend that you use a context menu.</span></span>

<span data-ttu-id="2b214-152">Weitere Informationen finden Sie in den [Kontextmenüs und Flyouts](menus.md).</span><span class="sxs-lookup"><span data-stu-id="2b214-152">For more info, see [Context menus and flyouts](menus.md).</span></span>

### <a name="put-secondary-actions-in-hover-ui-to-optimize-for-pointer-input"></a><span data-ttu-id="2b214-153">Optimiertes Platzieren der sekundären Aktionen für die Zeigereingabe in Hover-UIs</span><span class="sxs-lookup"><span data-stu-id="2b214-153">Put secondary actions in hover UI to optimize for pointer input</span></span>

<span data-ttu-id="2b214-154">Wenn Ihre App benutzerfreundlich für Zeigereingaben wie Maus und Stift sein soll, und Sie sekundäre Aktionen nur für diese Eingabemethoden verfügbar machen möchten, können Sie die sekundären Aktionen durch Zeigeeffekte anzeigen.</span><span class="sxs-lookup"><span data-stu-id="2b214-154">If you expect your app to be used frequently with pointer input such as mouse and pen, and want to make secondary actions readily available only to those inputs, then you can show the secondary actions only on hover.</span></span> <span data-ttu-id="2b214-155">Diese Abkürzung wird nur angezeigt, wenn eine Zeigereingabe verwendet wird. Sie müssen daher sicherstellen, dass für andere Eingabetypen ebenfalls eine Möglichkeit verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="2b214-155">This accelerator is visible only when a pointer input is used, so be sure to use the other options to support other input types as well.</span></span>

![Geschachtelte UI, die beim Draufzeigen angezeigt wird](images/nested-ui-hover.png)


<span data-ttu-id="2b214-157">Weitere Informationen finden Sie unter [Mausinteraktionen](../input/mouse-interactions.md).</span><span class="sxs-lookup"><span data-stu-id="2b214-157">For more info, see [Mouse interactions](../input/mouse-interactions.md).</span></span>

## <a name="ui-placement-for-primary-and-secondary-actions"></a><span data-ttu-id="2b214-158">Platzierung der UI für primäre und sekundäre Aktionen</span><span class="sxs-lookup"><span data-stu-id="2b214-158">UI placement for primary and secondary actions</span></span>

<span data-ttu-id="2b214-159">Wenn Sie entscheiden, dass sekundäre Aktionen über die Hauptlisten-UI verfügbar gemacht werden sollen, empfehlen wir die folgenden Richtlinien.</span><span class="sxs-lookup"><span data-stu-id="2b214-159">If you decide that secondary actions should be exposed in the main list UI, we recommend the following guidelines.</span></span>

<span data-ttu-id="2b214-160">Beim Erstellen eines Listenelements mit primären und sekundären Aktionen platzieren Sie die primäre Aktion auf der linken und sekundäre Aktionen auf der rechten Seite.</span><span class="sxs-lookup"><span data-stu-id="2b214-160">When you create a list item with primary and secondary actions, place the primary action to the left and secondary actions to the right.</span></span> <span data-ttu-id="2b214-161">In Kulturen mit Leserichtung von links nach rechts identifizieren Benutzer Aktionen auf der linken Seite des Listenelements eher als primäre Aktion.</span><span class="sxs-lookup"><span data-stu-id="2b214-161">In left-to-right reading cultures, users associate actions on the left side of list item as the primary action.</span></span>

<span data-ttu-id="2b214-162">In der Listen-UI in diesen Beispielen ist der Fluss der Elemente tendenziell horizontal (die UI ist eher breit als hoch).</span><span class="sxs-lookup"><span data-stu-id="2b214-162">In these examples, we talk about list UI where the item flows more horizontally (it is wider than its height).</span></span> <span data-ttu-id="2b214-163">Es besteht dennoch die Möglichkeit, dass einzelne Listenelemente in ihrer Form eher quadratisch sind (höher als breit).</span><span class="sxs-lookup"><span data-stu-id="2b214-163">However, you might have list items that are more square in shape, or taller than their width.</span></span> <span data-ttu-id="2b214-164">Solche Elemente werden in der Regel in einem Raster verwendet.</span><span class="sxs-lookup"><span data-stu-id="2b214-164">Typically, these are items used in a grid.</span></span> <span data-ttu-id="2b214-165">Wenn die Liste bei diesen Elementen keinen vertikalen Bildlauf bietet, können Sie sekundäre Aktionen statt rechts neben dem Element darunter platzieren.</span><span class="sxs-lookup"><span data-stu-id="2b214-165">For these items, if the list doesn't scroll vertically, you can place the secondary actions at the bottom of the list item rather than to the right side.</span></span>

## <a name="consider-all-inputs"></a><span data-ttu-id="2b214-166">Berücksichtigen aller Eingaben</span><span class="sxs-lookup"><span data-stu-id="2b214-166">Consider all inputs</span></span>

<span data-ttu-id="2b214-167">Bei der Entscheidung, eine geschachtelte UI zu verwenden, sollten Sie auch die Benutzerfreundlichkeit bei allen Eingabetypen evaluieren.</span><span class="sxs-lookup"><span data-stu-id="2b214-167">When deciding to use nested UI, also evaluate the user experience with all input types.</span></span> <span data-ttu-id="2b214-168">Wie bereits erwähnt eignen sich geschachtelte UIs gut für bestimmte Eingabetypen.</span><span class="sxs-lookup"><span data-stu-id="2b214-168">As mentioned earlier, nested UI works great for some input types.</span></span> <span data-ttu-id="2b214-169">Leider gibt es andere Eingabetypen, für die sie nicht so gut geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="2b214-169">However, it does not always work great for some other.</span></span> <span data-ttu-id="2b214-170">Insbesondere problematisch ist der Zugriff auf geschachtelte UI-Elemente über Tastatur, Controller und bei Eingabe über eine Fernbedienung.</span><span class="sxs-lookup"><span data-stu-id="2b214-170">In particular, keyboard, controller, and remote inputs can have difficulty accessing nested UI elements.</span></span> <span data-ttu-id="2b214-171">Folge unbedingt den Richtlinien unten, um sicherzustellen, dass Ihre UWP-App mit allen Eingabetypen verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="2b214-171">Be sure to follow the guidance below to ensure your UWP works with all input types.</span></span>

## <a name="nested-ui-handling"></a><span data-ttu-id="2b214-172">Behandeln von geschachtelten UIs</span><span class="sxs-lookup"><span data-stu-id="2b214-172">Nested UI handling</span></span>

<span data-ttu-id="2b214-173">Wenn mehr als eine Aktion im Listenelement geschachtelt ist, empfehlen wir diese Richtlinien, um die Navigation über Tastatur, Gamepad, Fernbedienung und andere nicht zeigerorientierte Eingabetypen zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="2b214-173">When you have more than one action nested in the list item, we recommend this guidance to handle navigation with a keyboard, gamepad, remote control, or other non-pointer input.</span></span>

### <a name="nested-ui-where-list-items-perform-an-action"></a><span data-ttu-id="2b214-174">Geschachtelte UI, deren Elemente eine Aktion ausführen</span><span class="sxs-lookup"><span data-stu-id="2b214-174">Nested UI where list items perform an action</span></span>

<span data-ttu-id="2b214-175">Wenn Ihre Listen-UI mit geschachtelten Elementen Aktionen unterstützt wie Aufrufen, Auswählen (Einzel- oder Mehrfachauswahl) oder Ziehen und Ablegen, empfehlen wir die folgenden pfeilorientierten Verfahren zum Navigieren in geschachtelten UI-Elementen.</span><span class="sxs-lookup"><span data-stu-id="2b214-175">If your list UI with nested elements supports actions such as invoking, selection (single or multiple), or drag-and-drop operations, we recommend these arrowing techniques to navigate through your nested UI elements.</span></span>

![Komponenten von geschachtelten UIs](images/nested-ui-navigation.png)

**<span data-ttu-id="2b214-177">Gamepad</span><span class="sxs-lookup"><span data-stu-id="2b214-177">Gamepad</span></span>**

<span data-ttu-id="2b214-178">Leiten Sie den Benutzer bei der Eingabe über ein Gamepad wie folgt:</span><span class="sxs-lookup"><span data-stu-id="2b214-178">When input is from a gamepad, provide this user experience:</span></span>

- <span data-ttu-id="2b214-179">Von **A** aus übergibt die Richtungstaste nach rechts den Fokus an **B**.</span><span class="sxs-lookup"><span data-stu-id="2b214-179">From **A**, right directional key puts focus on **B**.</span></span>
- <span data-ttu-id="2b214-180">Von **B** aus übergibt die Richtungstaste nach rechts den Fokus an **C**.</span><span class="sxs-lookup"><span data-stu-id="2b214-180">From **B**, right directional key puts focus on **C**.</span></span>
- <span data-ttu-id="2b214-181">Von **C** aus übergibt die Richtungstaste nach rechts den Fokus an ein fokussierbares UI-Element rechts davon, falls ein solches Element vorhanden ist, ansonsten ist der Taste keine Aktion zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="2b214-181">From **C**, right directional key is either no op, or if there is a focusable UI element to the right of List, put the focus there.</span></span>
- <span data-ttu-id="2b214-182">Von **C** aus übergibt die Richtungstaste nach links den Fokus an **B**.</span><span class="sxs-lookup"><span data-stu-id="2b214-182">From **C**, left directional key puts focus on **B**.</span></span>
- <span data-ttu-id="2b214-183">Von **B** aus übergibt die Richtungstaste nach links den Fokus an **A**.</span><span class="sxs-lookup"><span data-stu-id="2b214-183">From **B**, left directional key puts focus on **A**.</span></span>
- <span data-ttu-id="2b214-184">Von **A** aus übergibt die Richtungstaste nach links den Fokus an ein fokussierbares UI-Element rechts davon, falls ein solches Element vorhanden ist, ansonsten ist der Taste keine Aktion zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="2b214-184">From **A**, left directional key is either no op, or if there is a focusable UI element to the right of List, put the focus there.</span></span>
- <span data-ttu-id="2b214-185">Von **A**, **B** oder **C** aus übergibt die Richtungstaste nach unten den Fokus an **D**.</span><span class="sxs-lookup"><span data-stu-id="2b214-185">From **A**, **B**, or **C**, down directional key puts focus on **D**.</span></span>
- <span data-ttu-id="2b214-186">Von einem UI-Element links neben dem Listenelement aus übergibt die Richtungstaste nach rechts den Fokus an **A**.</span><span class="sxs-lookup"><span data-stu-id="2b214-186">From UI element to the left of List Item, right directional key puts focus on **A**.</span></span>
- <span data-ttu-id="2b214-187">Von einem UI-Element rechts neben dem Listenelement übergibt die Richtungstaste nach links den Fokus an **A**.</span><span class="sxs-lookup"><span data-stu-id="2b214-187">From UI element to the right of List Item, left directional key puts focus on **A**.</span></span>

**<span data-ttu-id="2b214-188">Tastatur</span><span class="sxs-lookup"><span data-stu-id="2b214-188">Keyboard</span></span>**

<span data-ttu-id="2b214-189">Bei Eingabe über eine Tastatur sollte der Benutzer wie folgt geleitet werden:</span><span class="sxs-lookup"><span data-stu-id="2b214-189">When input is from a keyboard, this is the experience user gets:</span></span>

- <span data-ttu-id="2b214-190">Von **A** aus übergibt die Tabulatortaste den Fokus an **B**.</span><span class="sxs-lookup"><span data-stu-id="2b214-190">From **A**, tab key puts focus on **B**.</span></span>
- <span data-ttu-id="2b214-191">Von **B** aus übergibt die Tabulatortaste den Fokus an **C**.</span><span class="sxs-lookup"><span data-stu-id="2b214-191">From **B**, tab key puts focus on **C**.</span></span>
- <span data-ttu-id="2b214-192">Von **C** aus übergibt die Tabulatortaste den Fokus an das nächste fokussierbare UI-Element in der Aktivierreihenfolge.</span><span class="sxs-lookup"><span data-stu-id="2b214-192">From **C**, tab key puts focus on next focusable UI element in the tab order.</span></span>
- <span data-ttu-id="2b214-193">Von **C** aus übergibt die Tastenkombination Umschalt+Tabulatortaste den Fokus an **B**.</span><span class="sxs-lookup"><span data-stu-id="2b214-193">From **C**, shift+tab key puts focus on **B**.</span></span>
- <span data-ttu-id="2b214-194">Von **B** aus übergeben die Tastenkombination Umschalt+Tabulatortaste und die Pfeiltaste nach links den Fokus an **A**.</span><span class="sxs-lookup"><span data-stu-id="2b214-194">From **B**, shift+tab or left arrow key puts focus on **A**.</span></span>
- <span data-ttu-id="2b214-195">Von **A** aus übergibt die Tastenkombination Umschalt+Tabulatortaste den Fokus an das nächste fokussierbare UI-Element in der umgekehrten Aktivierreihenfolge.</span><span class="sxs-lookup"><span data-stu-id="2b214-195">From **A**, shift+tab key puts focus on next focusable UI element in the reverse tab order.</span></span>
- <span data-ttu-id="2b214-196">Von **A**, **B** oder **C** aus übergibt die Pfeiltaste nach unten den Fokus an **D**.</span><span class="sxs-lookup"><span data-stu-id="2b214-196">From **A**, **B**, or **C**, down arrow key puts focus on **D**.</span></span>
- <span data-ttu-id="2b214-197">Von einem UI-Element links neben dem Listenelement aus übergibt die Tabulatortaste den Fokus an **A**.</span><span class="sxs-lookup"><span data-stu-id="2b214-197">From UI element to the left of List Item, tab key puts focus on **A**.</span></span>
- <span data-ttu-id="2b214-198">Von UI-Element rechts neben dem Listenelement aus übergibt die Tastenkombination Umschalt+Tabulatortaste den Fokus an **C**.</span><span class="sxs-lookup"><span data-stu-id="2b214-198">From UI element to the right of List Item, shift tab key puts focus on **C**.</span></span>

<span data-ttu-id="2b214-199">Um diese UI so zur Verfügung zu stellen, legen Sie [IsItemClickEnabled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.isitemclickenabled.aspx) für Ihre Liste auf **true** fest.</span><span class="sxs-lookup"><span data-stu-id="2b214-199">To achieve this UI, set [IsItemClickEnabled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.isitemclickenabled.aspx) to **true** on your list.</span></span> <span data-ttu-id="2b214-200">[SelectionMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.selectionmode.aspx) kann ein beliebiger Wert sein.</span><span class="sxs-lookup"><span data-stu-id="2b214-200">[SelectionMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.selectionmode.aspx) can be any value.</span></span>

<span data-ttu-id="2b214-201">Der Code zur Implementierung dieses Verhaltens finden Sie im Abschnitt [Beispiel](#example) dieses Artikels.</span><span class="sxs-lookup"><span data-stu-id="2b214-201">For the code to implement this, see the [Example](#example) section of this article.</span></span>

### <a name="nested-ui-where-list-items-do-not-perform-an-action"></a><span data-ttu-id="2b214-202">Geschachtelte UI, deren Listenelemente keine Aktion ausführen</span><span class="sxs-lookup"><span data-stu-id="2b214-202">Nested UI where list items do not perform an action</span></span>

<span data-ttu-id="2b214-203">Sie können eine Listenansicht auch verwenden, weil sie die Inhalte visuell optimiert darstellt und ein bestimmtes Bildlaufverhalten bietet, ohne dass den Listenelementen eine Aktion zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="2b214-203">You might use a list view because it provides virtualization and optimized scrolling behavior, but not have an action associated with a list item.</span></span> <span data-ttu-id="2b214-204">Diese Benutzeroberflächen verwenden die Listendarstellung, um Elemente zu gruppieren und sicherzustellen, dass alle Listenelemente beim Bildlauf gemeinsam bewegt werden.</span><span class="sxs-lookup"><span data-stu-id="2b214-204">These UIs typically use the list item only to group elements and ensure they scroll as a set.</span></span>

<span data-ttu-id="2b214-205">Diese Art von UI ist sehr viel komplizierter als die vorherigen Beispiele, es sind zahlreiche geschachtelte Elemente vorhanden, über die der Benutzer Aktionen ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="2b214-205">This kind of UI tends to be much more complicated than the previous examples, with a lot of nested elements that the user can take action on.</span></span>

![Komponenten von geschachtelten UIs](images/nested-ui-grouping.png)


<span data-ttu-id="2b214-207">Um diese UI so zur Verfügung zu stellen, legen Sie die folgenden Eigenschaften in der Liste fest:</span><span class="sxs-lookup"><span data-stu-id="2b214-207">To achieve this UI, set the following properties on your list:</span></span>
- <span data-ttu-id="2b214-208">[SelectionMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.selectionmode.aspx) auf **None**.</span><span class="sxs-lookup"><span data-stu-id="2b214-208">[SelectionMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.selectionmode.aspx) to **None**.</span></span>
- <span data-ttu-id="2b214-209">[IsItemClickEnabled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.isitemclickenabled.aspx) auf **false**.</span><span class="sxs-lookup"><span data-stu-id="2b214-209">[IsItemClickEnabled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.isitemclickenabled.aspx) to **false**.</span></span>
- <span data-ttu-id="2b214-210">[IsFocusEngagementEnabled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.control.isfocusengagementenabled.aspx) auf **true**.</span><span class="sxs-lookup"><span data-stu-id="2b214-210">[IsFocusEngagementEnabled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.control.isfocusengagementenabled.aspx) to **true**.</span></span>

```xaml
<ListView SelectionMode="None" IsItemClickEnabled="False" >
    <ListView.ItemContainerStyle>
         <Style TargetType="ListViewItem">
             <Setter Property="IsFocusEngagementEnabled" Value="True"/>
         </Style>
    </ListView.ItemContainerStyle>
</ListView>
```

<span data-ttu-id="2b214-211">Wenn die Listenelemente keine Aktion ausführen, empfehlen wir die folgenden Richtlinien, um die Navigation mit einem Gamepad oder Tastatur zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="2b214-211">When the list items do not perform an action, we recommend this guidance to handle navigation with a gamepad or keyboard.</span></span>

**<span data-ttu-id="2b214-212">Gamepad</span><span class="sxs-lookup"><span data-stu-id="2b214-212">Gamepad</span></span>**

<span data-ttu-id="2b214-213">Leiten Sie den Benutzer bei der Eingabe über ein Gamepad wie folgt:</span><span class="sxs-lookup"><span data-stu-id="2b214-213">When input is from a gamepad, provide this user experience:</span></span>

- <span data-ttu-id="2b214-214">Von einem Listenelement aus übergibt die Richtungstaste nach unten den Fokus an das nächste Listenelement.</span><span class="sxs-lookup"><span data-stu-id="2b214-214">From List Item, down directional key puts focus on next List Item.</span></span>
- <span data-ttu-id="2b214-215">Von einem Listenelement aus übergibt die Richtungstaste nach links bzw. rechts den Fokus an ein fokussierbares UI-Element rechts bzw. links davon, falls ein solches Element vorhanden ist, ansonsten ist der Taste keine Aktion zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="2b214-215">From List Item, left/right key is either no op, or if there is a focusable UI element to the right of List, put the focus there.</span></span>
- <span data-ttu-id="2b214-216">Von einem Listenelement aus übergibt die Taste „A“ den Fokus an das geschachtelte Listenelement in der Reihenfolge oben/unten und links/rechts.</span><span class="sxs-lookup"><span data-stu-id="2b214-216">From List Item, 'A' button puts the focus on Nested UI in top/down left/right priority.</span></span>
- <span data-ttu-id="2b214-217">Folgen Sie in der geschachtelten UI dem XY-Fokusnavigationsmodell.</span><span class="sxs-lookup"><span data-stu-id="2b214-217">While inside Nested UI, follow the XY Focus navigation model.</span></span>  <span data-ttu-id="2b214-218">Der Fokus kann die geschachtelte UI in dem aktuellen Listenelement erst verlassen, wenn der Benutzer die Taste „B“ drückt, die den Fokus an das Listenelement zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="2b214-218">Focus can only navigate around Nested UI contained inside the current List Item until user presses 'B' button, which puts the focus back onto the List Item.</span></span>

**<span data-ttu-id="2b214-219">Tastatur</span><span class="sxs-lookup"><span data-stu-id="2b214-219">Keyboard</span></span>**

<span data-ttu-id="2b214-220">Bei Eingabe über eine Tastatur sollte der Benutzer wie folgt geleitet werden:</span><span class="sxs-lookup"><span data-stu-id="2b214-220">When input is from a keyboard, this is the experience user gets:</span></span>

- <span data-ttu-id="2b214-221">Von einem Listenelement aus übergibt die Pfeiltaste nach unten den Fokus an das nächste Listenelement.</span><span class="sxs-lookup"><span data-stu-id="2b214-221">From List Item, down arrow key puts focus on the next List Item.</span></span>
- <span data-ttu-id="2b214-222">In dem Listenelement ist der Pfeiltaste nach links bzw. rechts keine Aktion zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="2b214-222">From List Item, pressing left/right key is no op.</span></span>
- <span data-ttu-id="2b214-223">Von einem Listenelement aus übergibt die Tabulatortaste den Fokus an das nächste fokussierbare Element in dem geschachtelten UI-Element.</span><span class="sxs-lookup"><span data-stu-id="2b214-223">From List Item, pressing tab key puts focus on the next tab stop amongst the Nested UI item.</span></span>
- <span data-ttu-id="2b214-224">Von einem der geschachtelten UI-Elemente aus durchläuft der Fokus beim Drücken der Tabulatortaste die geschachtelte UI in der Aktivierreihenfolge.</span><span class="sxs-lookup"><span data-stu-id="2b214-224">From one of the Nested UI items, pressing tab traverses the nested UI items in tab order.</span></span>  <span data-ttu-id="2b214-225">Nachdem alle Elemente der geschachtelten UI durchlaufen wurden, erhält den Fokus das nächste Steuerelement, das in der Aktivierreihenfolge auf ListView folgt.</span><span class="sxs-lookup"><span data-stu-id="2b214-225">Once all the Nested UI items are traveled to, it puts the focus onto the next control in tab order after ListView.</span></span>
- <span data-ttu-id="2b214-226">Bei der Tastenkombination Umschalt+Tabulatortaste wird das Aktivierungsverhalten umgekehrt.</span><span class="sxs-lookup"><span data-stu-id="2b214-226">Shift+Tab behaves in reverse direction from tab behavior.</span></span>

## <a name="example"></a><span data-ttu-id="2b214-227">Beispiel</span><span class="sxs-lookup"><span data-stu-id="2b214-227">Example</span></span>

<span data-ttu-id="2b214-228">Dieses Beispiel zeigt, wie Sie eine [geschachtelte UI implementieren, in denen Listenelemente eine Aktion ausführen](#nested-ui-where-list-items-perform-an-action).</span><span class="sxs-lookup"><span data-stu-id="2b214-228">This example shows how to implement [nested UI where list items perform an action](#nested-ui-where-list-items-perform-an-action).</span></span>

```xaml
<ListView SelectionMode="None" IsItemClickEnabled="True"
          ChoosingItemContainer="listview1_ChoosingItemContainer"/>
```

```csharp
private void OnListViewItemKeyDown(object sender, KeyRoutedEventArgs e)
{
    // Code to handle going in/out of nested UI with gamepad and remote only.
    if (e.Handled == true)
    {
        return;
    }

    var focusedElementAsListViewItem = FocusManager.GetFocusedElement() as ListViewItem;
    if (focusedElementAsListViewItem != null)
    {
        // Focus is on the ListViewItem.
        // Go in with Right arrow.
        Control candidate = null;

        switch (e.OriginalKey)
        {
            case Windows.System.VirtualKey.GamepadDPadRight:
            case Windows.System.VirtualKey.GamepadLeftThumbstickRight:
                var rawPixelsPerViewPixel = DisplayInformation.GetForCurrentView().RawPixelsPerViewPixel;
                GeneralTransform generalTransform = focusedElementAsListViewItem.TransformToVisual(null);
                Point startPoint = generalTransform.TransformPoint(new Point(0, 0));
                Rect hintRect = new Rect(startPoint.X * rawPixelsPerViewPixel, startPoint.Y * rawPixelsPerViewPixel, 1, focusedElementAsListViewItem.ActualHeight * rawPixelsPerViewPixel);
                candidate = FocusManager.FindNextFocusableElement(FocusNavigationDirection.Right, hintRect) as Control;
                break;
        }

        if (candidate != null)
        {
            candidate.Focus(FocusState.Keyboard);
            e.Handled = true;
        }
    }
    else
    {
        // Focus is inside the ListViewItem.
        FocusNavigationDirection direction = FocusNavigationDirection.None;
        switch (e.OriginalKey)
        {
            case Windows.System.VirtualKey.GamepadDPadUp:
            case Windows.System.VirtualKey.GamepadLeftThumbstickUp:
                direction = FocusNavigationDirection.Up;
                break;
            case Windows.System.VirtualKey.GamepadDPadDown:
            case Windows.System.VirtualKey.GamepadLeftThumbstickDown:
                direction = FocusNavigationDirection.Down;
                break;
            case Windows.System.VirtualKey.GamepadDPadLeft:
            case Windows.System.VirtualKey.GamepadLeftThumbstickLeft:
                direction = FocusNavigationDirection.Left;
                break;
            case Windows.System.VirtualKey.GamepadDPadRight:
            case Windows.System.VirtualKey.GamepadLeftThumbstickRight:
                direction = FocusNavigationDirection.Right;
                break;
            default:
                break;
        }

        if (direction != FocusNavigationDirection.None)
        {
            Control candidate = FocusManager.FindNextFocusableElement(direction) as Control;
            if (candidate != null)
            {
                ListViewItem listViewItem = sender as ListViewItem;

                // If the next focusable candidate to the left is outside of ListViewItem,
                // put the focus on ListViewItem.
                if (direction == FocusNavigationDirection.Left &&
                    !listViewItem.IsAncestorOf(candidate))
                {
                    listViewItem.Focus(FocusState.Keyboard);
                }
                else
                {
                    candidate.Focus(FocusState.Keyboard);
                }
            }

            e.Handled = true;
        }
    }
}

private void listview1_ChoosingItemContainer(ListViewBase sender, ChoosingItemContainerEventArgs args)
{
    if (args.ItemContainer == null)
    {
        args.ItemContainer = new ListViewItem();
        args.ItemContainer.KeyDown += OnListViewItemKeyDown;
    }
}
```

```csharp
// DependencyObjectExtensions.cs definition.
public static class DependencyObjectExtensions
{
    public static bool IsAncestorOf(this DependencyObject parent, DependencyObject child)
    {
        DependencyObject current = child;
        bool isAncestor = false;

        while (current != null && !isAncestor)
        {
            if (current == parent)
            {
                isAncestor = true;
            }

            current = VisualTreeHelper.GetParent(current);
        }

        return isAncestor;
    }
}
```
