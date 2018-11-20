---
author: jwmsft
ms.assetid: 26DF15E8-2C05-4174-A714-7DF2E8273D32
title: Optimieren der ListView- und GridView-Benutzeroberfläche
description: Verbessern Sie die Leistung und Startzeit von ListView und GridView durch UI-Virtualisierung, Elementreduzierung und die progressive Aktualisierung von Elementen.
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 25eeea58e1e03eedfca3aaafda1cee13cac1f3c4
ms.sourcegitcommit: cbe7cf620622a5e4df7414f9e38dfecec1cfca99
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "7418423"
---
# <a name="listview-and-gridview-ui-optimization"></a><span data-ttu-id="69555-104">Optimieren der ListView- und GridView-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="69555-104">ListView and GridView UI optimization</span></span>


<span data-ttu-id="69555-105">**Hinweis:**  Weitere Einzelheiten finden Sie in der Sitzung //build/ [Erhebliches Erhöhen der Leistung bei der Interaktion von Benutzern mit großen Mengen von Daten in GridView und ListView](https://channel9.msdn.com/events/build/2013/3-158).</span><span class="sxs-lookup"><span data-stu-id="69555-105">**Note** For more details, see the //build/ session [Dramatically Increase Performance when Users Interact with Large Amounts of Data in GridView and ListView](https://channel9.msdn.com/events/build/2013/3-158).</span></span>

<span data-ttu-id="69555-106">Verbessern Sie die Leistung und Startzeit von [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) und [**GridView**](https://msdn.microsoft.com/library/windows/apps/BR242705) durch UI-Virtualisierung, Elementreduzierung und die progressive Aktualisierung von Elementen.</span><span class="sxs-lookup"><span data-stu-id="69555-106">Improve [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) and [**GridView**](https://msdn.microsoft.com/library/windows/apps/BR242705) performance and startup time through UI virtualization, element reduction, and progressive updating of items.</span></span> <span data-ttu-id="69555-107">Weitere Informationen zu Datenvirtualisierungstechniken finden Sie unter [Virtualisierung von ListView- und GridView-Daten](listview-and-gridview-data-optimization.md).</span><span class="sxs-lookup"><span data-stu-id="69555-107">For data virtualization techniques, see [ListView and GridView data virtualization](listview-and-gridview-data-optimization.md).</span></span>

## <a name="two-key-factors-in-collection-performance"></a><span data-ttu-id="69555-108">Zwei wichtige Faktoren für die Sammlungsleistung</span><span class="sxs-lookup"><span data-stu-id="69555-108">Two key factors in collection performance</span></span>

<span data-ttu-id="69555-109">Das Bearbeiten von Sammlungen ist ein gängiges Szenario.</span><span class="sxs-lookup"><span data-stu-id="69555-109">Manipulating collections is a common scenario.</span></span> <span data-ttu-id="69555-110">Eine Bildanzeige besitzt Sammlungen von Fotos, ein Leser besitzt Sammlungen von Artikeln/Büchern/Geschichten, und eine Shopping-App verfügt über Sammlungen von Produkten.</span><span class="sxs-lookup"><span data-stu-id="69555-110">A photo viewer has collections of photos, a reader has collections of articles/books/stories, and a shopping app has collections of products.</span></span> <span data-ttu-id="69555-111">In diesem Thema erfahren Sie, wie Sie vorgehen können, damit Ihre App Sammlungen effizient bearbeiten kann.</span><span class="sxs-lookup"><span data-stu-id="69555-111">This topic shows what you can do to make your app efficient at manipulating collections.</span></span>

<span data-ttu-id="69555-112">Es gibt zwei wichtige Leistungsfaktoren für Sammlungen: einerseits die vom UI-Thread benötige Zeit zum Erstellen von Elementen und andererseits den vom Rohdatensatz und den UI-Elementen zum Rendern dieser Daten verwendeten Arbeitsspeicher.</span><span class="sxs-lookup"><span data-stu-id="69555-112">There are two key factors in performance when it comes to collections: one is the time spent by the UI thread creating items; the other is the memory used by both the raw data set and the UI elements used to render that data.</span></span>

<span data-ttu-id="69555-113">Für reibungslose Verschiebungen/Bildläufe ist es wichtig, dass der UI-Thread eine effiziente und intelligente Instanziierung, Datenbindung und Anordnung von Elementen vornimmt.</span><span class="sxs-lookup"><span data-stu-id="69555-113">For smooth panning/scrolling, it's vital that the UI thread do an efficient and smart job of instantiating, data-binding, and laying out items.</span></span>

## <a name="ui-virtualization"></a><span data-ttu-id="69555-114">UI-Virtualisierung</span><span class="sxs-lookup"><span data-stu-id="69555-114">UI virtualization</span></span>

<span data-ttu-id="69555-115">Die Virtualisierung der Benutzeroberfläche ist die wichtigste Verbesserung, die Sie vornehmen können.</span><span class="sxs-lookup"><span data-stu-id="69555-115">UI virtualization is the most important improvement you can make.</span></span> <span data-ttu-id="69555-116">Dies bedeutet, dass die Benutzeroberflächenelemente, die die Objekte darstellen, bei Bedarf erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="69555-116">This means that UI elements representing the items are created on demand.</span></span> <span data-ttu-id="69555-117">Für ein an eine Sammlung von 1000 Elementen gebundenes Elementsteuerelement wäre es eine Verschwendung von Ressourcen, die Benutzeroberfläche für alle Elemente gleichzeitig zu erstellen, da sie nicht alle auf einmal angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="69555-117">For an items control bound to a 1000-item collection, it would be a waste of resources to create the UI for all the items at the same time, because they can't all be displayed at the same time.</span></span> <span data-ttu-id="69555-118">[**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) und [**GridView**](https://msdn.microsoft.com/library/windows/apps/BR242705) (und andere von [**ItemsControl**](https://msdn.microsoft.com/library/windows/apps/BR242803) abgeleitete Standardsteuerelemente) führen die Virtualisierung der Benutzeroberfläche für Sie durch.</span><span class="sxs-lookup"><span data-stu-id="69555-118">[**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) and [**GridView**](https://msdn.microsoft.com/library/windows/apps/BR242705) (and other standard [**ItemsControl**](https://msdn.microsoft.com/library/windows/apps/BR242803)-derived controls) perform UI virtualization for you.</span></span> <span data-ttu-id="69555-119">Wenn Elemente kurz davor sind, per Bildlauf in der Ansicht angezeigt zu werden (einige Seiten davon entfernt), generiert das Framework die Benutzeroberfläche für die Elemente und speichert sie zwischen.</span><span class="sxs-lookup"><span data-stu-id="69555-119">When items are close to being scrolled into view (a few pages away), the framework generates the UI for the items and caches them.</span></span> <span data-ttu-id="69555-120">Wenn es unwahrscheinlich ist, dass die Elemente erneut angezeigt werden, gibt das Framework den Arbeitsspeicher wieder frei.</span><span class="sxs-lookup"><span data-stu-id="69555-120">When it's unlikely that the items will be shown again, the framework re-claims the memory.</span></span>

<span data-ttu-id="69555-121">Wenn Sie eine benutzerdefinierte ItemsPanel-Vorlage bereitstellen (siehe [**ItemsPanel**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemspanel.aspx)), ist es wichtig, dass Sie ein Virtualisierungspanel wie [**ItemsWrapGrid**](https://msdn.microsoft.com/library/windows/apps/Dn298849) oder [**ItemsStackPanel**](https://msdn.microsoft.com/library/windows/apps/Dn298795) verwenden.</span><span class="sxs-lookup"><span data-stu-id="69555-121">If you provide a custom items panel template (see [**ItemsPanel**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemspanel.aspx)) then make sure you use a virtualizing panel such as [**ItemsWrapGrid**](https://msdn.microsoft.com/library/windows/apps/Dn298849) or [**ItemsStackPanel**](https://msdn.microsoft.com/library/windows/apps/Dn298795).</span></span> <span data-ttu-id="69555-122">Wenn Sie [**VariableSizedWrapGrid**](https://msdn.microsoft.com/library/windows/apps/BR227651), [**WrapGrid**](https://msdn.microsoft.com/library/windows/apps/BR227717) oder [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/BR209635) verwenden, erhalten Sie keine Virtualisierung.</span><span class="sxs-lookup"><span data-stu-id="69555-122">If you use [**VariableSizedWrapGrid**](https://msdn.microsoft.com/library/windows/apps/BR227651), [**WrapGrid**](https://msdn.microsoft.com/library/windows/apps/BR227717), or [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/BR209635), then you will not get virtualization.</span></span> <span data-ttu-id="69555-123">Darüber hinaus werden die folgenden [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878)-Ereignisse nur ausgelöst, wenn [**ItemsWrapGrid**](https://msdn.microsoft.com/library/windows/apps/Dn298849) oder [**ItemsStackPanel**](https://msdn.microsoft.com/library/windows/apps/Dn298795) verwendet werden: [**ChoosingGroupHeaderContainer**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.choosinggroupheadercontainer), [**ChoosingItemContainer**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.choosingitemcontainer) und [**ContainerContentChanging**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.containercontentchanging).</span><span class="sxs-lookup"><span data-stu-id="69555-123">Additionally, the following [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) events are raised only when using an [**ItemsWrapGrid**](https://msdn.microsoft.com/library/windows/apps/Dn298849) or an [**ItemsStackPanel**](https://msdn.microsoft.com/library/windows/apps/Dn298795): [**ChoosingGroupHeaderContainer**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.choosinggroupheadercontainer), [**ChoosingItemContainer**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.choosingitemcontainer), and [**ContainerContentChanging**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.containercontentchanging).</span></span>

<span data-ttu-id="69555-124">Das Viewport-Konzept ist für die UI-Virtualisierung entscheidend, da das Framework die Elemente erstellen muss, die voraussichtlich angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="69555-124">The concept of a viewport is critical to UI virtualization because the framework must create the elements that are likely to be shown.</span></span> <span data-ttu-id="69555-125">Allgemein gilt: Der Viewport einer [**ItemsControl**](https://msdn.microsoft.com/library/windows/apps/BR242803)-Klasse entspricht dem Umfang des logischen Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="69555-125">In general, the viewport of an [**ItemsControl**](https://msdn.microsoft.com/library/windows/apps/BR242803) is the extent of the logical control.</span></span> <span data-ttu-id="69555-126">So entspricht beispielsweise der Viewport einer [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878)-Klasse der Breite und Höhe des **ListView**-Elements.</span><span class="sxs-lookup"><span data-stu-id="69555-126">For example, the viewport of a [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) is the width and height of the **ListView** element.</span></span> <span data-ttu-id="69555-127">Einige Panels gewähren untergeordneten Elementen unbegrenzten Speicherplatz. Beispiele hierfür sind [**ScrollViewer**](https://msdn.microsoft.com/library/windows/apps/BR209527) und ein [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704)-Objekt mit Zeilen oder Spalten mit automatischer Größenanpassung.</span><span class="sxs-lookup"><span data-stu-id="69555-127">Some panels allow child elements unlimited space, examples being [**ScrollViewer**](https://msdn.microsoft.com/library/windows/apps/BR209527) and a [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704), with auto-sized rows or columns.</span></span> <span data-ttu-id="69555-128">Wird ein virtualisiertes **ItemsControl**-Objekt in einem dieser Panel platziert, nimmt es ausreichend Platz ein, um alle Elemente anzuzeigen, wodurch die Virtualisierung vereitelt wird.</span><span class="sxs-lookup"><span data-stu-id="69555-128">When a virtualized **ItemsControl** is placed in a panel like that, it takes enough room to display all of its items, which defeats virtualization.</span></span> <span data-ttu-id="69555-129">Stellen Sie die Virtualisierung wieder her, indem Sie die Breite und Höhe für das **ItemsControl**-Objekt festlegen.</span><span class="sxs-lookup"><span data-stu-id="69555-129">Restore virtualization by setting a width and height on the **ItemsControl**.</span></span>

## <a name="element-reduction-per-item"></a><span data-ttu-id="69555-130">Elementreduzierung pro Element</span><span class="sxs-lookup"><span data-stu-id="69555-130">Element reduction per item</span></span>

<span data-ttu-id="69555-131">Halten Sie die Anzahl von Benutzeroberflächenelementen, die zum Rendern Ihrer Elemente verwendet werden, vertretbar gering.</span><span class="sxs-lookup"><span data-stu-id="69555-131">Keep the number of UI elements used to render your items to a reasonable minimum.</span></span>

<span data-ttu-id="69555-132">Wenn ein Elementsteuerelement erstmalig angezeigt wird, werden alle zum Rendern eines mit Elementen gefüllten Viewports erforderlichen Elemente erstellt.</span><span class="sxs-lookup"><span data-stu-id="69555-132">When an items control is first shown, all the elements needed to render a viewport full of items are created.</span></span> <span data-ttu-id="69555-133">Während sich die Elemente dem Viewport nähern, aktualisiert das Framework zudem die Benutzeroberflächenelemente in zwischengespeicherten Elementvorlagen mit den gebundenen Datenobjekten.</span><span class="sxs-lookup"><span data-stu-id="69555-133">Also, as items approach the viewport, the framework updates the UI elements in cached item templates with the bound data objects.</span></span> <span data-ttu-id="69555-134">Die Minimierung der Komplexität des Markups in Vorlagen zahlt sich hinsichtlich des Arbeitsspeichers und des Zeitaufwands für den UI-Thread aus, da die Reaktionsfähigkeit insbesondere beim Schwenken/Bildlauf verbessert wird.</span><span class="sxs-lookup"><span data-stu-id="69555-134">Minimizing the complexity of the markup inside templates pays off in memory and in time spent on the UI thread, improving responsiveness especially while panning/scrolling.</span></span> <span data-ttu-id="69555-135">Die betreffenden Vorlagen sind die Elementvorlage (siehe [**ItemTemplate**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemtemplate.aspx)) und die Steuerelementvorlage eines [**ListViewItem**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewitem.aspx)- oder [**GridViewItem**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.gridviewitem.aspx)-Objekts (die Elementsteuerelementvorlage oder [**ItemContainerStyle**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemcontainerstyle)).</span><span class="sxs-lookup"><span data-stu-id="69555-135">The templates in question are the item template (see [**ItemTemplate**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemtemplate.aspx)) and the control template of a [**ListViewItem**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewitem.aspx) or a [**GridViewItem**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.gridviewitem.aspx) (the item control template, or [**ItemContainerStyle**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemcontainerstyle)).</span></span> <span data-ttu-id="69555-136">Der Vorteil auch einer geringen Reduzierung der Elementanzahl wird durch die Anzahl der angezeigten Elemente multipliziert.</span><span class="sxs-lookup"><span data-stu-id="69555-136">The benefit of even a small reduction in element count is multiplied by the number of items displayed.</span></span>

<span data-ttu-id="69555-137">Beispiele zur Elementreduzierung finden Sie unter [Optimieren des XAML-Markups](optimize-xaml-loading.md).</span><span class="sxs-lookup"><span data-stu-id="69555-137">For examples of element reduction, see [Optimize your XAML markup](optimize-xaml-loading.md).</span></span>

<span data-ttu-id="69555-138">Die standardmäßigen Steuerelementvorlagen für [**ListViewItem**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewitem.aspx) und [**GridViewItem**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.gridviewitem.aspx) enthalten ein [**ListViewItemPresenter**](https://msdn.microsoft.com/library/windows/apps/Dn298500)-Element.</span><span class="sxs-lookup"><span data-stu-id="69555-138">The default control templates for [**ListViewItem**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewitem.aspx) and [**GridViewItem**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.gridviewitem.aspx) contain a [**ListViewItemPresenter**](https://msdn.microsoft.com/library/windows/apps/Dn298500) element.</span></span> <span data-ttu-id="69555-139">Dieser Presenter ist ein einzelnes optimiertes Element, das komplexe visuelle Elemente für Fokus, Auswahl und andere visuelle Zustände anzeigt.</span><span class="sxs-lookup"><span data-stu-id="69555-139">This presenter is a single optimized element that displays complex visuals for focus, selection, and other visual states.</span></span> <span data-ttu-id="69555-140">Wenn Sie bereits über benutzerdefinierte Elementsteuerelementvorlagen verfügen ([**ItemContainerStyle**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemcontainerstyle)) oder zukünftig eine Kopie einer Elementsteuerelementvorlage bearbeiten, wird empfohlen, dass Sie ein **ListViewItemPresenter**-Element verwenden, da dieses Element in der Mehrzahl der Fälle ein optimales Gleichgewicht zwischen Leistung und Anpassbarkeit bietet.</span><span class="sxs-lookup"><span data-stu-id="69555-140">If you already have custom item control templates ([**ItemContainerStyle**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemcontainerstyle)), or if in future you edit a copy of an item control template, then we recommend you use a **ListViewItemPresenter** because that element will give you optimum balance between performance and customizability in the majority of cases.</span></span> <span data-ttu-id="69555-141">Sie können den Presenter anpassen, indem Sie dessen Eigenschaften festlegen.</span><span class="sxs-lookup"><span data-stu-id="69555-141">You customize the presenter by setting properties on it.</span></span> <span data-ttu-id="69555-142">Im folgenden Markup-Beispiel wird z.B. das standardmäßig beim Auswählen eines Elements angezeigte Häkchen entfernt und die Hintergrundfarbe des ausgewählten Elements in Orange geändert.</span><span class="sxs-lookup"><span data-stu-id="69555-142">For example, here's markup that removes the check mark that appears by default when an item is selected, and changes the background color of the selected item to orange.</span></span>

```xml
...
<ListView>
 ...
 <ListView.ItemContainerStyle>
 <Style TargetType="ListViewItem">
 <Setter Property="Template">
 <Setter.Value>
 <ControlTemplate TargetType="ListViewItem">
 <ListViewItemPresenter SelectionCheckMarkVisualEnabled="False" SelectedBackground="Orange"/>
 </ControlTemplate>
 </Setter.Value>
 </Setter>
 </Style>
 </ListView.ItemContainerStyle>
</ListView>
<!-- ... -->
```

<span data-ttu-id="69555-143">Es sind ca. 25 Eigenschaften mit selbstbeschreibenden Namen wie [**SelectionCheckMarkVisualEnabled**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.listviewitempresenter.selectioncheckmarkvisualenabled.aspx) und [**SelectedBackground**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.listviewitempresenter.selectedbackground.aspx) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="69555-143">There are about 25 properties with self-describing names similar to [**SelectionCheckMarkVisualEnabled**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.listviewitempresenter.selectioncheckmarkvisualenabled.aspx) and [**SelectedBackground**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.listviewitempresenter.selectedbackground.aspx).</span></span> <span data-ttu-id="69555-144">Sollten sich die Presentertypen für Ihren Zweck als nicht ausreichend anpassbar erweisen, können Sie stattdessen eine Kopie der `ListViewItemExpanded` - oder `GridViewItemExpanded` -Steuerelementvorlage bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="69555-144">Should the presenter types prove not to be customizable enough for your use case, you can edit a copy of the `ListViewItemExpanded` or `GridViewItemExpanded` control template instead.</span></span> <span data-ttu-id="69555-145">Diese befinden sich in `\Program Files (x86)\Windows Kits\10\DesignTime\CommonConfiguration\Neutral\UAP\<version>\Generic\generic.xaml`.</span><span class="sxs-lookup"><span data-stu-id="69555-145">These can be found in `\Program Files (x86)\Windows Kits\10\DesignTime\CommonConfiguration\Neutral\UAP\<version>\Generic\generic.xaml`.</span></span> <span data-ttu-id="69555-146">Beachten Sie, dass die Verwendung dieser Vorlagen bedeutet, dass Sie für die gesteigerte Anpassbarkeit einen Teil der Leistung einbüßen.</span><span class="sxs-lookup"><span data-stu-id="69555-146">Be aware that using these templates means trading some performance for the increase in customization.</span></span>

<span id="update-items-incrementally"/>

## <a name="update-listview-and-gridview-items-progressively"></a><span data-ttu-id="69555-147">Progressives Aktualisieren von ListView- und GridView-Elementen</span><span class="sxs-lookup"><span data-stu-id="69555-147">Update ListView and GridView items progressively</span></span>

<span data-ttu-id="69555-148">Wenn Sie die Datenvirtualisierung verwenden, können Sie für [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) und [**GridView**](https://msdn.microsoft.com/library/windows/apps/BR242705) eine hohe Reaktionsfähigkeit erhalten. Konfigurieren Sie das Steuerelement zu diesem Zweck so, dass für die noch zu ladenden Elemente temporäre UI-Elemente gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="69555-148">If you're using data virtualization then you can keep [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) and [**GridView**](https://msdn.microsoft.com/library/windows/apps/BR242705) responsiveness high by configuring the control to render temporary UI elements for the items still being (down)loaded.</span></span> <span data-ttu-id="69555-149">Die temporären Elemente werden dann beim Laden der Daten schrittweise durch die eigentlichen UI-Elemente ersetzt.</span><span class="sxs-lookup"><span data-stu-id="69555-149">The temporary elements are then progressively replaced with actual UI as data loads.</span></span>

<span data-ttu-id="69555-150">Egal, von wo die Daten geladen werden (lokaler Datenträger, Netzwerk oder Cloud), kann ein Benutzer ein [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878)- oder [**GridView**](https://msdn.microsoft.com/library/windows/apps/BR242705)-Element so schnell schwenken/durchlaufen, dass es nicht möglich ist, alle Elemente originalgetreu zu rendern, während gleichzeitig eine flüssige Verschiebung bzw. ein gleichmäßiger Bildlauf gewährleistet wird.</span><span class="sxs-lookup"><span data-stu-id="69555-150">Also—no matter where you're loading data from (local disk, network, or cloud)—a user can pan/scroll a [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) or [**GridView**](https://msdn.microsoft.com/library/windows/apps/BR242705) so rapidly that it's not possible to render each item with full fidelity while preserving smooth panning/scrolling.</span></span> <span data-ttu-id="69555-151">Um die Gleichmäßigkeit der Verschiebung bzw. des Bildlaufs zu erhalten, können Sie zusätzlich zur Verwendung von Platzhaltern das Element in mehreren Phasen rendern.</span><span class="sxs-lookup"><span data-stu-id="69555-151">To preserve smooth panning/scrolling you can choose to render an item in multiple phases in addition to using placeholders.</span></span>

<span data-ttu-id="69555-152">Ein Beispiel für diese Verfahren findet sich häufig bei Fotoanzeige-Apps: Auch wenn nicht alle Bilder geladen und angezeigt wurden, kann der Benutzer dennoch Verschiebungen/Bildläufe vornehmen und mit der Sammlung interagieren.</span><span class="sxs-lookup"><span data-stu-id="69555-152">An example of these techniques is often seen in photo-viewing apps: even though not all of the images have been loaded and displayed, the user can still pan/scroll and interact with the collection.</span></span> <span data-ttu-id="69555-153">Für ein „Filmelement“ können Sie z.B. in der ersten Phase den Titel anzeigen, während die Altersfreigabe in der zweiten und ein Bild des Posters in der dritten Phase angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="69555-153">Or, for a "movie" item, you could show the title in the first phase, the rating in the second phase, and an image of the poster in the third phase.</span></span> <span data-ttu-id="69555-154">Der Benutzer sieht die wichtigsten Daten zu den einzelnen Elementen so früh wie möglich, d.h., es können sofort Maßnahmen ergriffen werden.</span><span class="sxs-lookup"><span data-stu-id="69555-154">The user sees the most important data about each item as early as possible, and that means they're able to take action at once.</span></span> <span data-ttu-id="69555-155">Anschließend werden die weniger wichtigen Informationen ausgefüllt.</span><span class="sxs-lookup"><span data-stu-id="69555-155">Then the less important info is filled-in as time allows.</span></span> <span data-ttu-id="69555-156">Hier folgen die Plattformfeatures, mit denen Sie diese Verfahren implementieren können.</span><span class="sxs-lookup"><span data-stu-id="69555-156">Here are the platform features you can use to implement these techniques.</span></span>

### <a name="placeholders"></a><span data-ttu-id="69555-157">Platzhalter</span><span class="sxs-lookup"><span data-stu-id="69555-157">Placeholders</span></span>

<span data-ttu-id="69555-158">Das Feature der temporären Platzhalter für visuelle Elemente ist standardmäßig aktiviert und wird über die [**ShowsScrollingPlaceholders**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.showsscrollingplaceholders)-Eigenschaft gesteuert.</span><span class="sxs-lookup"><span data-stu-id="69555-158">The temporary placeholder visuals feature is on by default, and it's controlled with the [**ShowsScrollingPlaceholders**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.showsscrollingplaceholders) property.</span></span> <span data-ttu-id="69555-159">Bei der schnellen Verschiebung bzw. einem schnellen Bildlauf bietet dieses Feature dem Benutzer einen visuellen Hinweis, dass es weitere anzuzeigende Elemente gibt, während gleichzeitig die Gleichmäßigkeit beibehalten wird.</span><span class="sxs-lookup"><span data-stu-id="69555-159">During fast panning/scrolling, this feature gives the user a visual hint that there are more items yet to fully display while also preserving smoothness.</span></span> <span data-ttu-id="69555-160">Bei Verwendung eines der folgenden Verfahren können Sie **ShowsScrollingPlaceholders** auf „false“ festlegen, wenn die Platzhalter vom System gerendert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="69555-160">If you use one of the techniques below then you can set **ShowsScrollingPlaceholders** to false if you prefer not to have the system render placeholders.</span></span>

**<span data-ttu-id="69555-161">Progressive Aktualisierung von Datenvorlagen mithilfe von x:Phase</span><span class="sxs-lookup"><span data-stu-id="69555-161">Progressive data template updates using x:Phase</span></span>**

<span data-ttu-id="69555-162">Im Folgenden wird beschrieben, wie Sie das [x:Phase-Attribut](https://msdn.microsoft.com/library/windows/apps/Mt204790) mit [{x:Bind}](https://msdn.microsoft.com/library/windows/apps/Mt204783)-Bindungen verwenden, um die progressive Aktualisierung von Datenvorlagen zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="69555-162">Here's how to use the [x:Phase attribute](https://msdn.microsoft.com/library/windows/apps/Mt204790) with [{x:Bind}](https://msdn.microsoft.com/library/windows/apps/Mt204783) bindings to implement progressive data template updates.</span></span>

1.  <span data-ttu-id="69555-163">So sieht die Bindungsquelle aus (dies ist die Datenquelle, die zum Binden verwendet wird).</span><span class="sxs-lookup"><span data-stu-id="69555-163">Here's what the binding source looks like (this is the data source that we'll bind to).</span></span>

    ```csharp
    namespace LotsOfItems
    {
        public class ExampleItem
        {
            public string Title { get; set; }
            public string Subtitle { get; set; }
            public string Description { get; set; }
        }

        public class ExampleItemViewModel
        {
            private ObservableCollection<ExampleItem> exampleItems = new ObservableCollection<ExampleItem>();
            public ObservableCollection<ExampleItem> ExampleItems { get { return this.exampleItems; } }

            public ExampleItemViewModel()
            {
                for (int i = 1; i < 150000; i++)
                {
                    this.exampleItems.Add(new ExampleItem(){
                        Title = "Title: " + i.ToString(),
                        Subtitle = "Sub: " + i.ToString(),
                        Description = "Desc: " + i.ToString()
                    });
                }
            }
        }
    }
    ```
2.  <span data-ttu-id="69555-164">Im Folgenden sehen Sie das Markup, das `DeferMainPage.xaml` enthält.</span><span class="sxs-lookup"><span data-stu-id="69555-164">Here's the markup that `DeferMainPage.xaml` contains.</span></span> <span data-ttu-id="69555-165">Die Rasteransicht enthält eine Elementvorlage mit Elementen, die an die Eigenschaften **Title**, **Subtitle** und **Description** der **MyItem**-Klasse gebunden sind.</span><span class="sxs-lookup"><span data-stu-id="69555-165">The grid view contains an item template with elements bound to the **Title**, **Subtitle**, and **Description** properties of the **MyItem** class.</span></span> <span data-ttu-id="69555-166">Beachten Sie, dass für **X: Phase** der Standardwert 0 ist.</span><span class="sxs-lookup"><span data-stu-id="69555-166">Note that **x:Phase** defaults to 0.</span></span> <span data-ttu-id="69555-167">Hier werden die Elemente anfänglich nur mit dem sichtbaren Titel gerendert.</span><span class="sxs-lookup"><span data-stu-id="69555-167">Here, items will be initially rendered with just the title visible.</span></span> <span data-ttu-id="69555-168">Anschließend erhält der Untertitel eine Datenbindung, der für alle Elemente usw. sichtbar gemacht wird, bis alle Phasen verarbeitet wurden.</span><span class="sxs-lookup"><span data-stu-id="69555-168">Then the subtitle element will be data bound and made visible for all the items and so on until all the phases have been processed.</span></span>
    ```xml
    <Page
        x:Class="LotsOfItems.DeferMainPage"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:lotsOfItems="using:LotsOfItems"
        mc:Ignorable="d">

        <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
            <GridView ItemsSource="{x:Bind ViewModel.ExampleItems}">
                <GridView.ItemTemplate>
                    <DataTemplate x:DataType="lotsOfItems:ExampleItem">
                        <StackPanel Height="100" Width="100" Background="OrangeRed">
                            <TextBlock Text="{x:Bind Title}"/>
                            <TextBlock Text="{x:Bind Subtitle}" x:Phase="1"/>
                            <TextBlock Text="{x:Bind Description}" x:Phase="2"/>
                        </StackPanel>
                    </DataTemplate>
                </GridView.ItemTemplate>
            </GridView>
        </Grid>
    </Page>
    ```

3.  <span data-ttu-id="69555-169">Wenn Sie die App jetzt ausführen und eine schnelle Verschiebung bzw. einen schnellen Bildlauf in der Rasteransicht durchführen, werden Sie erkennen, dass jedes neue Element auf dem Bildschirm angezeigt wird. Zunächst wird es als dunkelgraues Rechteck dargestellt (dank der [**ShowsScrollingPlaceholders**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.showsscrollingplaceholders)-Eigenschaft mit dem Standardwert **true**), dann folgen Titel, Untertitel und abschließend die Beschreibung.</span><span class="sxs-lookup"><span data-stu-id="69555-169">If you run the app now and pan/scroll quickly through the grid view then you'll notice that as each new item appears on the screen, at first it is rendered as a dark gray rectangle (thanks to the [**ShowsScrollingPlaceholders**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.showsscrollingplaceholders) property defaulting to **true**), then the title appears, followed by subtitle, followed by description.</span></span>

**<span data-ttu-id="69555-170">Progressive Aktualisierung von Datenvorlagen mithilfe von ContainerContentChanging</span><span class="sxs-lookup"><span data-stu-id="69555-170">Progressive data template updates using ContainerContentChanging</span></span>**

<span data-ttu-id="69555-171">Die allgemeine Strategie für das [**ContainerContentChanging**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.containercontentchanging)-Ereignis ist die Verwendung von **Opacity**, um Elemente auszublenden, die nicht sofort sichtbar sein müssen.</span><span class="sxs-lookup"><span data-stu-id="69555-171">The general strategy for the [**ContainerContentChanging**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.containercontentchanging) event is to use **Opacity** to hide elements that don’t need to be immediately visible.</span></span> <span data-ttu-id="69555-172">Wenn Elemente wiederverwendet werden, behalten sie ihre alten Werte, daher möchten wir diese Elemente ausblenden, bis wir diese Werte über das neue Datenelement aktualisiert haben.</span><span class="sxs-lookup"><span data-stu-id="69555-172">When elements are recycled, they will retain their old values so we want to hide those elements until we've updated those values from the new data item.</span></span> <span data-ttu-id="69555-173">Wir verwenden die **Phase**-Eigenschaft für die Ereignisargumente, um zu bestimmen, welche Elemente aktualisiert und angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="69555-173">We use the **Phase** property on the event arguments to determine which elements to update and show.</span></span> <span data-ttu-id="69555-174">Wenn weitere Phasen erforderlich sind, registrieren wir einen Rückruf.</span><span class="sxs-lookup"><span data-stu-id="69555-174">If additional phases are needed, we register a callback.</span></span>

1.  <span data-ttu-id="69555-175">Wir verwenden dieselbe Bindungsquelle wie für **x:Phase**.</span><span class="sxs-lookup"><span data-stu-id="69555-175">We'll use the same binding source as for **x:Phase**.</span></span>

2.  <span data-ttu-id="69555-176">Im Folgenden sehen Sie das Markup, das `MainPage.xaml` enthält.</span><span class="sxs-lookup"><span data-stu-id="69555-176">Here's the markup that `MainPage.xaml` contains.</span></span> <span data-ttu-id="69555-177">Die Rasteransicht deklariert einen Handler für ihr [**ContainerContentChanging**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.containercontentchanging)-Ereignis. Zudem enthält sie eine Elementvorlage mit Elementen, die zum Anzeigen der Eigenschaften **Title**, **Subtitle** und **Description** der **MyItem**-Klasse verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="69555-177">The grid view declares a handler to its [**ContainerContentChanging**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.containercontentchanging) event, and it contains an item template with elements used to display the **Title**, **Subtitle**, and **Description** properties of the **MyItem** class.</span></span> <span data-ttu-id="69555-178">Damit Sie mit **ContainerContentChanging** die maximalen Leistungsvorteile erreichen, werden im Markup keine Bindungen verwendet. Stattdessen werden die Werte programmgesteuert zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="69555-178">To get the maximum performance benefits of using **ContainerContentChanging**, we don't use bindings in the markup but we instead assign values programmatically.</span></span> <span data-ttu-id="69555-179">Eine Ausnahme stellt hier das Element zum Anzeigen des Titels dar, das wir in Phase 0 erwarten.</span><span class="sxs-lookup"><span data-stu-id="69555-179">The exception here is the element displaying the title, which we consider to be in phase 0.</span></span>
    ```xml
    <Page
        x:Class="LotsOfItems.MainPage"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:lotsOfItems="using:LotsOfItems"
        mc:Ignorable="d">

        <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
            <GridView ItemsSource="{x:Bind ViewModel.ExampleItems}" ContainerContentChanging="GridView_ContainerContentChanging">
                <GridView.ItemTemplate>
                    <DataTemplate x:DataType="lotsOfItems:ExampleItem">
                        <StackPanel Height="100" Width="100" Background="OrangeRed">
                            <TextBlock Text="{x:Bind Title}"/>
                            <TextBlock Opacity="0"/>
                            <TextBlock Opacity="0"/>
                        </StackPanel>
                    </DataTemplate>
                </GridView.ItemTemplate>
            </GridView>
        </Grid>
    </Page>
    ```
3.  <span data-ttu-id="69555-180">Abschließend folgt hier die Implementierung des [**ContainerContentChanging**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.containercontentchanging)-Ereignishandlers.</span><span class="sxs-lookup"><span data-stu-id="69555-180">Lastly, here's the implementation of the [**ContainerContentChanging**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.containercontentchanging) event handler.</span></span> <span data-ttu-id="69555-181">Dieser Code zeigt auch, wie eine Eigenschaft vom Typ **RecordingViewModel** der **MainPage**-Klasse hinzugefügt wird, um die Klasse der Bindungsquelle über die Klasse verfügbar zu machen, die unsere Markupseite darstellt.</span><span class="sxs-lookup"><span data-stu-id="69555-181">This code also shows how we add a property of type **RecordingViewModel** to **MainPage** to expose the binding source class from the class that represents our page of markup.</span></span> <span data-ttu-id="69555-182">Solange keine [{Binding}](https://msdn.microsoft.com/library/windows/apps/Mt204782)-Bindungen in Ihrer Datenvorlage vorliegen, markieren Sie das Ereignisargumentobjekt in der ersten Phase des Handlers als behandelt, um dem Element einen Hinweis zu geben, dass es keinen Datenkontext festlegen muss.</span><span class="sxs-lookup"><span data-stu-id="69555-182">As long as you don't have any [{Binding}](https://msdn.microsoft.com/library/windows/apps/Mt204782) bindings in your data template, then mark the event arguments object as handled in the first phase of the handler to hint to the item that it needn't set a data context.</span></span>
    ```csharp
    namespace LotsOfItems
    {
        /// <summary>
        /// An empty page that can be used on its own or navigated to within a Frame.
        /// </summary>
        public sealed partial class MainPage : Page
        {
            public MainPage()
            {
                this.InitializeComponent();
                this.ViewModel = new ExampleItemViewModel();
            }

            public ExampleItemViewModel ViewModel { get; set; }

            // Display each item incrementally to improve performance.
            private void GridView_ContainerContentChanging(ListViewBase sender, ContainerContentChangingEventArgs args)
            {
                if (args.Phase != 0)
                {
                    throw new System.Exception("We should be in phase 0, but we are not.");
                }

                // It's phase 0, so this item's title will already be bound and displayed.

                args.RegisterUpdateCallback(this.ShowSubtitle);

                args.Handled = true;
            }

            private void ShowSubtitle(ListViewBase sender, ContainerContentChangingEventArgs args)
            {
                if (args.Phase != 1)
                {
                    throw new System.Exception("We should be in phase 1, but we are not.");
                }

                // It's phase 1, so show this item's subtitle.
                var templateRoot = args.ItemContainer.ContentTemplateRoot as StackPanel;
                var textBlock = templateRoot.Children[1] as TextBlock;
                textBlock.Text = (args.Item as ExampleItem).Subtitle;
                textBlock.Opacity = 1;

                args.RegisterUpdateCallback(this.ShowDescription);
            }

            private void ShowDescription(ListViewBase sender, ContainerContentChangingEventArgs args)
            {
                if (args.Phase != 2)
                {
                    throw new System.Exception("We should be in phase 2, but we are not.");
                }

                // It's phase 2, so show this item's description.
                var templateRoot = args.ItemContainer.ContentTemplateRoot as StackPanel;
                var textBlock = templateRoot.Children[2] as TextBlock;
                textBlock.Text = (args.Item as ExampleItem).Description;
                textBlock.Opacity = 1;
            }
        }
    }
    ```

4.  <span data-ttu-id="69555-183">Wenn Sie die App jetzt ausführen und schnell schwenken oder einen schnellen Bildlauf in der Rasteransicht durchführen, sehen Sie dasselbe Verhalten wie für **x:Phase**.</span><span class="sxs-lookup"><span data-stu-id="69555-183">If you run the app now and pan/scroll quickly through the grid view then you'll see the same behavior as for as for **x:Phase**.</span></span>

## <a name="container-recycling-with-heterogeneous-collections"></a><span data-ttu-id="69555-184">Containerwiederverwendung mit heterogenen Sammlungen</span><span class="sxs-lookup"><span data-stu-id="69555-184">Container-recycling with heterogeneous collections</span></span>

<span data-ttu-id="69555-185">In einigen Anwendungen benötigen Sie verschiedene Benutzeroberflächen für unterschiedliche Elementtypen innerhalb einer Sammlung.</span><span class="sxs-lookup"><span data-stu-id="69555-185">In some applications, you need to have different UI for different types of item within a collection.</span></span> <span data-ttu-id="69555-186">Dies kann zu Situationen führen, in denen die Virtualisierungspanels die visuellen Elemente, die zur Elementanzeige dienen, nicht wiederverwenden können.</span><span class="sxs-lookup"><span data-stu-id="69555-186">This can create a situation where it is impossible for virtualizing panels to reuse/recycle the visual elements used to display the items.</span></span> <span data-ttu-id="69555-187">Wenn die visuellen Elemente eines Element beim Schwenken neu erstellt werden müssen, gehen viele Leistungsvorteile der Virtualisierung verloren.</span><span class="sxs-lookup"><span data-stu-id="69555-187">Recreating the visual elements for an item during panning undoes many of the performance wins provided by virtualization.</span></span> <span data-ttu-id="69555-188">Mit etwas Planung können Virtualisierungspanels jedoch die Elemente wiederverwenden.</span><span class="sxs-lookup"><span data-stu-id="69555-188">However, a little planning can allow virtualizing panels to reuse the elements.</span></span> <span data-ttu-id="69555-189">Entwicklern stehen je nach Szenario zwei Optionen zur Verfügung: das [**ChoosingItemContainer**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.choosingitemcontainer)-Ereignis oder ein Elementvorlagenselektor.</span><span class="sxs-lookup"><span data-stu-id="69555-189">Developers have a couple of options depending on their scenario: the [**ChoosingItemContainer**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.choosingitemcontainer) event, or an item template selector.</span></span> <span data-ttu-id="69555-190">Der Ansatz mit **ChoosingItemContainer** bietet eine bessere Leistung.</span><span class="sxs-lookup"><span data-stu-id="69555-190">The **ChoosingItemContainer** approach has better performance.</span></span>

**<span data-ttu-id="69555-191">Das ChoosingItemContainer-Ereignis</span><span class="sxs-lookup"><span data-stu-id="69555-191">The ChoosingItemContainer event</span></span>**

<span data-ttu-id="69555-192">[**ChoosingItemContainer**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.choosingitemcontainer) ist ein Ereignis, mit dem Sie ein Element (**ListViewItem**/**GridViewItem**) für [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878)/[**GridView**](https://msdn.microsoft.com/library/windows/apps/BR242705) bereitstellen können, wenn ein neues Element beim Starten oder Wiederverwenden erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="69555-192">[**ChoosingItemContainer**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.choosingitemcontainer) is an event that allows you to provide an item (**ListViewItem**/**GridViewItem**) to the [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878)/[**GridView**](https://msdn.microsoft.com/library/windows/apps/BR242705) whenever a new item is needed during start-up or recycling.</span></span> <span data-ttu-id="69555-193">Sie können einen Container basierend auf dem Typ des Datenelements erstellen, das der Container anzeigen soll (im folgenden Beispiel dargestellt).</span><span class="sxs-lookup"><span data-stu-id="69555-193">You can create a container based on the type of data item the container will display (shown in the example below).</span></span> <span data-ttu-id="69555-194">**ChoosingItemContainer** ist die leistungsfähigere Möglichkeit zur Verwendung unterschiedlicher Datenvorlagen für verschiedene Elemente.</span><span class="sxs-lookup"><span data-stu-id="69555-194">**ChoosingItemContainer** is the higher-performing way to use different data templates for different items.</span></span> <span data-ttu-id="69555-195">Die Containerzwischenspeicherung kann mit **ChoosingItemContainer** erzielt werden.</span><span class="sxs-lookup"><span data-stu-id="69555-195">Container caching is something that can be achieved using **ChoosingItemContainer**.</span></span> <span data-ttu-id="69555-196">Wenn Sie beispielsweise fünf verschiedene Vorlagen besitzen, wobei eine Vorlage um eine Größenordnung häufiger als die anderen verwendet wird, können Sie mit ChoosingItemContainer nicht nur Elemente im benötigten Verhältnis erstellen, sondern auch eine passende Anzahl von Elementen im Zwischenspeicher speichern, die dann zur Wiederverwendung zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="69555-196">For example, if you have five different templates, with one template occurring an order of magnitude more often than the others, then ChoosingItemContainer allows you not only to create items at the ratios needed but also to keep an appropriate number of elements cached and available for recycling.</span></span> <span data-ttu-id="69555-197">[**ChoosingGroupHeaderContainer**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.choosinggroupheadercontainer) bietet die gleiche Funktionalität für Gruppenheader.</span><span class="sxs-lookup"><span data-stu-id="69555-197">[**ChoosingGroupHeaderContainer**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.choosinggroupheadercontainer) provides the same functionality for group headers.</span></span>

```csharp
// Example shows how to use ChoosingItemContainer to return the correct
// DataTemplate when one is available. This example shows how to return different 
// data templates based on the type of FileItem. Available ListViewItems are kept
// in two separate lists based on the type of DataTemplate needed.
private void ListView_ChoosingItemContainer
    (ListViewBase sender, ChoosingItemContainerEventArgs args)
{
    // Determines type of FileItem from the item passed in.
    bool special = args.Item is DifferentFileItem;

    // Uses the Tag property to keep track of whether a particular ListViewItem's 
    // datatemplate should be a simple or a special one.
    string tag = special ? "specialFiles" : "simpleFiles";

    // Based on the type of datatemplate needed return the correct list of 
    // ListViewItems, this could have also been handled with a hash table. These 
    // two lists are being used to keep track of ItemContainers that can be reused.
    List<UIElement> relevantStorage = special ? specialFileItemTrees : simpleFileItemTrees;

    // args.ItemContainer is used to indicate whether the ListView is proposing an 
    // ItemContainer (ListViewItem) to use. If args.Itemcontainer, then there was a 
    // recycled ItemContainer available to be reused.
    if (args.ItemContainer != null)
    {
        // The Tag is being used to determine whether this is a special file or 
        // a simple file.
        if (args.ItemContainer.Tag.Equals(tag))
        {
            // Great: the system suggested a container that is actually going to 
            // work well.
        }
        else
        {
            // the ItemContainer's datatemplate does not match the needed 
            // datatemplate.
            args.ItemContainer = null;
        }
    }

    if (args.ItemContainer == null)
    {
        // see if we can fetch from the correct list.
        if (relevantStorage.Count > 0)
        {
            args.ItemContainer = relevantStorage[0] as SelectorItem;
        }
        else
        {
            // there aren't any (recycled) ItemContainers available. So a new one 
            // needs to be created.
            ListViewItem item = new ListViewItem();
            item.ContentTemplate = this.Resources[tag] as DataTemplate;
            item.Tag = tag;
            args.ItemContainer = item;
        }
    }
}
```

**<span data-ttu-id="69555-198">Elementvorlagenselektor</span><span class="sxs-lookup"><span data-stu-id="69555-198">Item template selector</span></span>**

<span data-ttu-id="69555-199">Ein Elementvorlagenselektor ([**DataTemplateSelector**](https://msdn.microsoft.com/library/windows/apps/BR209469)) ermöglicht es einer App, zur Laufzeit eine andere Elementvorlage basierend auf dem Typ des angezeigten Datenelements zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="69555-199">An item template selector ([**DataTemplateSelector**](https://msdn.microsoft.com/library/windows/apps/BR209469)) allows an app to return a different item template at runtime based on the type of the data item that will be displayed.</span></span> <span data-ttu-id="69555-200">Dadurch wird die Entwicklung zwar produktiver, es erschwert jedoch die UI-Virtualisierung, da nicht jede Elementvorlage für jedes Datenelement wiederverwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="69555-200">This makes development more productive, but it makes UI virtualization more difficult because not every item template can be reused for every data item.</span></span>

<span data-ttu-id="69555-201">Wenn ein Element (**ListViewItem**/**GridViewItem**) wiederverwendet wird, muss das Framework entscheiden, ob die zur Verwendung in der Wiederverwendungswarteschlange (einem Zwischenspeicher von Elementen, die zurzeit nicht zur Datenanzeige verwendet werden) verfügbaren Elemente über eine Elementvorlage verfügen, die der gewünschten Vorlage für das aktuelle Datenelement entspricht.</span><span class="sxs-lookup"><span data-stu-id="69555-201">When recycling an item (**ListViewItem**/**GridViewItem**), the framework must decide whether the items that are available for use in the recycle queue (the recycle queue is a cache of items that are not currently being used to display data) have an item template that will match the one desired by the current data item.</span></span> <span data-ttu-id="69555-202">Wenn die Wiederverwendungswarteschlange keine Elemente mit der passenden Elementvorlage enthält, wird ein neues Element erstellt, und die passende Elementvorlage wird dafür instanziiert.</span><span class="sxs-lookup"><span data-stu-id="69555-202">If there are no items in the recycle queue with the appropriate item template then a new item is created, and the appropriate item template is instantiated for it.</span></span> <span data-ttu-id="69555-203">Enthält die Wiederverwendungswarteschlange ein Element mit der passenden Elementvorlage, wird dieses Element aus der Wiederverwendungswarteschlange entfernt und für das aktuelle Datenelement verwendet.</span><span class="sxs-lookup"><span data-stu-id="69555-203">If, on other hand, the recycle queue contains an item with the appropriate item template then that item is removed from the recycle queue and is used for the current data item.</span></span> <span data-ttu-id="69555-204">Ein Elementvorlagenselektor eignet sich in Situationen, in denen nur eine geringe Anzahl von Elementvorlagen verwendet wird und eine flache Verteilung in der Sammlung der Elemente vorliegt, die unterschiedliche Elementvorlagen verwenden.</span><span class="sxs-lookup"><span data-stu-id="69555-204">An item template selector works in situations where only a small number of item templates are used and there is a flat distribution throughout the collection of items that use different item templates.</span></span>

<span data-ttu-id="69555-205">Bei einer ungleichmäßigen Verteilung von Elementen, die unterschiedliche Elementvorlagen verwenden, müssen während des Schwenkens wahrscheinlich neue Elementvorlagen erstellt werden, was viele der Vorteile der Virtualisierung zunichtemacht.</span><span class="sxs-lookup"><span data-stu-id="69555-205">When there is an uneven distribution of items that use different item templates then new item templates will likely need to be created during panning, and this negates many of the gains provided by virtualization.</span></span> <span data-ttu-id="69555-206">Zudem berücksichtigt ein Elementvorlagenselektor nur fünf mögliche Kandidaten beim Auswerten, ob ein bestimmter Container für das aktuelle Datenelement wiederverwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="69555-206">Additionally, an item template selector only considers five possible candidates when evaluating whether a particular container can be reused for the current data item.</span></span> <span data-ttu-id="69555-207">Daher sollten Sie sorgfältig überlegen, ob Ihre Daten für die Verwendung eines Elementvorlagenselektors geeignet sind, bevor Sie ihn in Ihrer App verwenden.</span><span class="sxs-lookup"><span data-stu-id="69555-207">So you should carefully consider whether your data is appropriate for use with an item template selector before using one in your app.</span></span> <span data-ttu-id="69555-208">Wenn Ihre Sammlung überwiegend homogen ist, gibt der Selektor in den meisten Fällen (möglicherweise immer) denselben Typ zurück.</span><span class="sxs-lookup"><span data-stu-id="69555-208">If your collection is mostly homogeneous then the selector is returning the same type most (possibly all) of the time.</span></span> <span data-ttu-id="69555-209">Seien Sie sich jedoch bewusst, welche Folgen diese seltenen Homogenitätsausnahmen für Sie haben, und überlegen Sie, ob die Verwendung von [**ChoosingItemContainer**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.choosingitemcontainer) (oder zwei Elementsteuerelementen) nicht vorzuziehen wäre.</span><span class="sxs-lookup"><span data-stu-id="69555-209">Just be aware of the price you're paying for the rare exceptions to that homegeneity, and consider whether using [**ChoosingItemContainer**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.choosingitemcontainer) (or two items controls) is preferable.</span></span>

 

