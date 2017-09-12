---
author: Jwmsft
Description: "Ein Steuerelement eines semantischen Zooms ermöglicht Benutzern, zwischen zwei verschiedenen semantischen Ansichten des gleichen Datensatzes zu zoomen."
title: Semantischer Zoom
ms.assetid: B5C21FE7-BA83-4940-9CC1-96F6A2DC28C7
label: Semantic zoom
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
pm-contact: predavid
design-contact: kimsea
doc-status: Published
ms.openlocfilehash: 8b901f6077b3f2eb765b53caf9bba188eae5ff0e
ms.sourcegitcommit: 10f8dcf69d37cdb61562fc9f4d268ccb499c368f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2017
---
# <a name="semantic-zoom"></a><span data-ttu-id="d25a5-104">Semantischer Zoom</span><span class="sxs-lookup"><span data-stu-id="d25a5-104">Semantic zoom</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

<span data-ttu-id="d25a5-105">Mit dem semantischen Zoom können Benutzer zwischen zwei unterschiedlichen Ansichten desselben Inhalts zoomen, um schnell durch große Mengen gruppierter Daten zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="d25a5-105">Semantic zoom lets the user switch between two different views of the same content so that they can quickly navigate through a large set of grouped data.</span></span>
 
- <span data-ttu-id="d25a5-106">Die vergrößerte Ansicht ist die Hauptansicht des Inhalts.</span><span class="sxs-lookup"><span data-stu-id="d25a5-106">The zoomed-in view is the main view of the content.</span></span> <span data-ttu-id="d25a5-107">Dies ist die Hauptansicht, in der Sie einzelne Datenelemente anzeigen.</span><span class="sxs-lookup"><span data-stu-id="d25a5-107">This is the main view where you show individual data items.</span></span> 
- <span data-ttu-id="d25a5-108">Die verkleinerte Ansicht zeigt den gleichen Inhalt auf höherer Ebene.</span><span class="sxs-lookup"><span data-stu-id="d25a5-108">The zoomed-out view is a higher-level view of the same content.</span></span> <span data-ttu-id="d25a5-109">In dieser Ansicht werden normalerweise die Gruppenköpfe für gruppierte Daten angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d25a5-109">You typically show the group headers for a grouped data set in this view.</span></span> 

<span data-ttu-id="d25a5-110">Bei der Anzeige eines Adressbuchs kann der Benutzer beispielsweise schnell zum Buchstaben „W” springen und diesen vergrößern, um die zu dem betreffenden Buchstaben gehörenden Namen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d25a5-110">For example, when viewing an address book, the user could zoom out to quickly jump to the letter "W", and zoom in on that letter to see the names associated with it.</span></span> 

> <span data-ttu-id="d25a5-111">**Wichtige APIs**: [SemanticZoom-Klasse](https://msdn.microsoft.com/library/windows/apps/hh702601), [ListView-Klasse](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.listview.aspx), [GridView-Klasse](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.gridview.aspx)</span><span class="sxs-lookup"><span data-stu-id="d25a5-111">**Important APIs**: [SemanticZoom class](https://msdn.microsoft.com/library/windows/apps/hh702601), [ListView class](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.listview.aspx), [GridView class](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.gridview.aspx)</span></span>

<span data-ttu-id="d25a5-112">**Features**:</span><span class="sxs-lookup"><span data-stu-id="d25a5-112">**Features**:</span></span>

-   <span data-ttu-id="d25a5-113">Die Größe der verkleinerten Ansicht ist durch die Grenzen des Steuerelements für semantischen Zoom beschränkt.</span><span class="sxs-lookup"><span data-stu-id="d25a5-113">The size of the zoomed-out view is constrained by the bounds of the semantic zoom control.</span></span>
-   <span data-ttu-id="d25a5-114">Durch Tippen auf einen Gruppenkopf wird zwischen Ansichten gewechselt.</span><span class="sxs-lookup"><span data-stu-id="d25a5-114">Tapping on a group header toggles views.</span></span> <span data-ttu-id="d25a5-115">Auch Zusammendrücken kann als Möglichkeit zum Wechseln zwischen den Ansichten aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="d25a5-115">Pinching as a way to toggle between views can be enabled.</span></span>
-   <span data-ttu-id="d25a5-116">Aktive Kopfzeilen wechseln zwischen Ansichten.</span><span class="sxs-lookup"><span data-stu-id="d25a5-116">Active headers switch between views.</span></span>

## <a name="is-this-the-right-control"></a><span data-ttu-id="d25a5-117">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="d25a5-117">Is this the right control?</span></span>

<span data-ttu-id="d25a5-118">Verwenden Sie das Steuerelement **SemanticZoom**, wenn Sie einen gruppierten Datensatz anzeigen müssen, der so groß ist, dass er auf einer oder zwei Seiten nicht ganz angezeigt werden kann.</span><span class="sxs-lookup"><span data-stu-id="d25a5-118">Use a **SemanticZoom** control when you need to show a grouped data set that's large enough that it can’t all be shown on one or two pages.</span></span>

<span data-ttu-id="d25a5-119">Der semantische Zoom ist nicht mit dem optischen Zoom zu verwechseln.</span><span class="sxs-lookup"><span data-stu-id="d25a5-119">Don't confuse semantic zooming with optical zooming.</span></span> <span data-ttu-id="d25a5-120">Sie zeigen zwar das gleiche Interaktions- und Grundverhalten (d.h. sie zeigen je nach Zoomfaktor mehr oder weniger Details an), der optische Zoom betrifft jedoch die Größenanpassung für einen Inhaltsbereich oder ein Objekt wie etwa ein Foto.</span><span class="sxs-lookup"><span data-stu-id="d25a5-120">While they share both the same interaction and basic behavior (displaying more or less detail based on a zoom factor), optical zoom refers to the adjustment of magnification for a content area or object such as a photograph.</span></span> <span data-ttu-id="d25a5-121">Informationen zu einem Steuerelement, das optisches Zooming durchführt, finden Sie im Artikel über das Steuerelement [ScrollViewer](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.aspx).</span><span class="sxs-lookup"><span data-stu-id="d25a5-121">For info about a control that performs optical zooming, see the [ScrollViewer](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.aspx) control.</span></span>

## <a name="examples"></a><span data-ttu-id="d25a5-122">Beispiele</span><span class="sxs-lookup"><span data-stu-id="d25a5-122">Examples</span></span>

**<span data-ttu-id="d25a5-123">Fotos-App</span><span class="sxs-lookup"><span data-stu-id="d25a5-123">Photos app</span></span>**

<span data-ttu-id="d25a5-124">Hier ist ein in der Fotos-App verwendeter semantischer Zoom.</span><span class="sxs-lookup"><span data-stu-id="d25a5-124">Here's a semantic zoom used in the Photos app.</span></span> <span data-ttu-id="d25a5-125">Fotos werden nach Monat gruppiert.</span><span class="sxs-lookup"><span data-stu-id="d25a5-125">Photos are grouped by month.</span></span> <span data-ttu-id="d25a5-126">Durch Auswahl einer Monatskopfzeile in der standardmäßigen Rasteransicht wird die Ansicht der Monatsliste verkleinert, um schneller navigieren zu können.</span><span class="sxs-lookup"><span data-stu-id="d25a5-126">Selecting a month header in the default grid view zooms out to the month list view for quicker navigation.</span></span>

![In der Fotos-App verwendeter semantischer Zoom](images/control-examples/semantic-zoom-photos.png)

**<span data-ttu-id="d25a5-128">Adressbuch</span><span class="sxs-lookup"><span data-stu-id="d25a5-128">Address book</span></span>**

<span data-ttu-id="d25a5-129">Ein Adressbuch ist ein weiteres Beispiel für einen Datensatz, der sich mit einem Steuerelement für semantisches Zoomen sehr viel einfacher durchblättern lässt.</span><span class="sxs-lookup"><span data-stu-id="d25a5-129">An address book is another example of a data set that can be much easier to navigate using semantic zoom.</span></span> <span data-ttu-id="d25a5-130">Sie können die verkleinerte Ansicht verwenden, um schnell zu dem gewünschten Buchstaben zu springen (linkes Bild), während die vergrößerte Ansicht die einzelnen Datenelemente zeigt (rechtes Bild).</span><span class="sxs-lookup"><span data-stu-id="d25a5-130">You can use the zoomed-out view to quickly jump to the letter you need (left image), while the zoomed-in view displays the individual data items (right image).</span></span>

![Beispiel für semantischen Zoom in einer Kontaktliste](images/semanticzoom-win10.png)

## <a name="create-a-semantic-zoom"></a><span data-ttu-id="d25a5-132">Erstellen eines semantischen Zooms</span><span class="sxs-lookup"><span data-stu-id="d25a5-132">Create a semantic zoom</span></span>

<span data-ttu-id="d25a5-133">Das Steuerelement **SemanticZoom** verfügt über keine visuelle Darstellung.</span><span class="sxs-lookup"><span data-stu-id="d25a5-133">The **SemanticZoom** control doesn’t have any visual representation of its own.</span></span> <span data-ttu-id="d25a5-134">Es handelt sich um ein Hoststeuerelement, das den Übergang zwischen zwei anderen Steuerelementen steuert, die die Ansichten für Ihre Inhalte bereitstellen, in der Regel die Steuerelemente **ListView** oder **GridView**.</span><span class="sxs-lookup"><span data-stu-id="d25a5-134">It’s a host control that manages the transition between 2 other controls that provide the views of your content, typically **ListView** or **GridView** controls.</span></span>  <span data-ttu-id="d25a5-135">Sie legen die Ansicht-Steuerelemente auf die [ZoomedInView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.semanticzoom.zoomedinview.aspx)- und [ZoomedOutView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.semanticzoom.zoomedoutview.aspx)-Eigenschaften von SemanticZoom fest.</span><span class="sxs-lookup"><span data-stu-id="d25a5-135">You set the view controls to the [ZoomedInView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.semanticzoom.zoomedinview.aspx) and [ZoomedOutView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.semanticzoom.zoomedoutview.aspx) properties of the SemanticZoom.</span></span>

<span data-ttu-id="d25a5-136">Sie benötigen für einen semantischen Zoom folgende drei Elemente:</span><span class="sxs-lookup"><span data-stu-id="d25a5-136">The 3 elements you need for a semantic zoom are:</span></span>
- <span data-ttu-id="d25a5-137">Eine gruppierte Datenquelle</span><span class="sxs-lookup"><span data-stu-id="d25a5-137">A grouped data source</span></span>
- <span data-ttu-id="d25a5-138">Eine vergrößerte Ansicht, die Daten auf Elementebene anzeigt</span><span class="sxs-lookup"><span data-stu-id="d25a5-138">A zoomed-in view that shows the item-level data.</span></span>
- <span data-ttu-id="d25a5-139">Eine verkleinerte Ansicht, die die Daten auf Gruppenebene anzeigt</span><span class="sxs-lookup"><span data-stu-id="d25a5-139">A zoomed-out view that shows the group-level data.</span></span>

<span data-ttu-id="d25a5-140">Bevor Sie einen semantischen Zoom verwenden, sollten Sie wissen, wie Sie eine Listenansicht mit gruppierten Daten verwenden.</span><span class="sxs-lookup"><span data-stu-id="d25a5-140">Before you use a semantic zoom, you should understand how to use a list view with grouped data.</span></span> <span data-ttu-id="d25a5-141">Weitere Informationen finden Sie unter [Listenansicht und Rasteransicht](listview-and-gridview.md) und [Gruppieren von Elementen in einer Liste]().</span><span class="sxs-lookup"><span data-stu-id="d25a5-141">For more info, see [List view and grid view](listview-and-gridview.md) and [Grouping items in a list]().</span></span> 

> <span data-ttu-id="d25a5-142">**Hinweis**:&nbsp;&nbsp;Um die vergrößerte und verkleinerte Ansicht des SemanticZoom-Steuerelements zu definieren, können Sie zwei beliebige Steuerelemente verwenden, die die Benutzeroberfläche [ISemanticZoomInformation](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.isemanticzoominformation.aspx) implementieren.</span><span class="sxs-lookup"><span data-stu-id="d25a5-142">**Note**&nbsp;&nbsp;To define the zoomed-in view and the zoomed-out view of the SemanticZoom control, you can use any two controls that implement the [ISemanticZoomInformation](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.isemanticzoominformation.aspx) interface.</span></span> <span data-ttu-id="d25a5-143">Das XAML-Framework bietet drei Steuerelemente, die diese Schnittstelle implementieren: ListView, GridView und Hub.</span><span class="sxs-lookup"><span data-stu-id="d25a5-143">The XAML framework provides 3 controls that implement this interface: ListView, GridView, and Hub.</span></span>
 
 <span data-ttu-id="d25a5-144">Dieser XAML-Code zeigt die Struktur des SemanticZoom-Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="d25a5-144">This XAML shows the structure of the SemanticZoom control.</span></span> <span data-ttu-id="d25a5-145">Sie weisen weitere Steuerelemente den Eigenschaften „ZoomedInView” und „ZoomedOutView” zu.</span><span class="sxs-lookup"><span data-stu-id="d25a5-145">You assign other controls to the ZoomedInView and ZoomedOutView properties.</span></span>
 
 ```xaml
<SemanticZoom>
    <SemanticZoom.ZoomedInView>
        <!-- Put the GridView for the zoomed in view here. -->   
    </SemanticZoom.ZoomedInView>

    <SemanticZoom.ZoomedOutView>
        <!-- Put the ListView for the zoomed out view here. -->       
    </SemanticZoom.ZoomedOutView>
</SemanticZoom>
 ```
 
<span data-ttu-id="d25a5-146">Die folgenden Beispiele stammen von der Seite „SemanticZoom” des [Beispiels für XAML-UI-Grundlagen](http://go.microsoft.com/fwlink/p/?LinkId=619992).</span><span class="sxs-lookup"><span data-stu-id="d25a5-146">The examples here are taken from the SemanticZoom page of the [XAML UI Basics sample](http://go.microsoft.com/fwlink/p/?LinkId=619992).</span></span> <span data-ttu-id="d25a5-147">Sie können das Beispiel herunterladen, um den kompletten Code anzuzeigen, einschließlich der Datenquelle.</span><span class="sxs-lookup"><span data-stu-id="d25a5-147">You can download the sample to see the complete code including the data source.</span></span> <span data-ttu-id="d25a5-148">Dieser semantische Zoom verwendet eine GridView, um die vergrößerte Ansicht und eine ListView für die verkleinerte Ansicht bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="d25a5-148">This semantic zoom uses a GridView to supply the zoomed-in view and a ListView for the zoomed-out view.</span></span>
  
**<span data-ttu-id="d25a5-149">Definieren der vergrößerten Ansicht</span><span class="sxs-lookup"><span data-stu-id="d25a5-149">Define the zoomed-in view</span></span>**

<span data-ttu-id="d25a5-150">Hier sehen Sie das GridView-Steuerelement für die vergrößerte Ansicht.</span><span class="sxs-lookup"><span data-stu-id="d25a5-150">Here's the GridView control for the zoomed-in view.</span></span> <span data-ttu-id="d25a5-151">Die vergrößerte Ansicht sollte die einzelnen Datenelemente in Gruppen anzeigen.</span><span class="sxs-lookup"><span data-stu-id="d25a5-151">The zoomed-in view should display the individual data items in groups.</span></span> <span data-ttu-id="d25a5-152">Dieses Beispiel zeigt, wie die Elemente in einem Raster mit einem Bild und Text angezeigt werden sollten.</span><span class="sxs-lookup"><span data-stu-id="d25a5-152">This example shows how to display the items in a grid with an image and text.</span></span> 

```xaml
<SemanticZoom.ZoomedInView>
    <GridView ItemsSource="{x:Bind cvsGroups.View}" 
              ScrollViewer.IsHorizontalScrollChainingEnabled="False" 
              SelectionMode="None" 
              ItemTemplate="{StaticResource ZoomedInTemplate}">
        <GridView.GroupStyle>
            <GroupStyle HeaderTemplate="{StaticResource ZoomedInGroupHeaderTemplate}"/>
        </GridView.GroupStyle>
    </GridView>
</SemanticZoom.ZoomedInView>
```
 
<span data-ttu-id="d25a5-153">Die Darstellung der Gruppenkopfzeilen wird in der Ressource `ZoomedInGroupHeaderTemplate` definiert.</span><span class="sxs-lookup"><span data-stu-id="d25a5-153">The look of the group headers is defined in the `ZoomedInGroupHeaderTemplate` resource.</span></span> <span data-ttu-id="d25a5-154">Die Darstellung der Elemente wird in der Ressource `ZoomedInTemplate` definiert.</span><span class="sxs-lookup"><span data-stu-id="d25a5-154">The look of the items is defined in the `ZoomedInTemplate` resource.</span></span> 

```xaml
<DataTemplate x:Key="" x:DataType="data:ControlInfoDataGroup">
    <TextBlock Text="{x:Bind Title}" 
               Foreground="{ThemeResource ApplicationForegroundThemeBrush}" 
               Style="{StaticResource SubtitleTextBlockStyle}"/>
</DataTemplate>

<DataTemplate x:Key="ZoomedInTemplate" x:DataType="data:ControlInfoDataItem">
    <StackPanel Orientation="Horizontal" MinWidth="200" Margin="12,6,0,6">
        <Image Source="{x:Bind ImagePath}" Height="80" Width="80"/>
        <StackPanel Margin="20,0,0,0">
            <TextBlock Text="{x:Bind Title}" 
                       Style="{StaticResource BaseTextBlockStyle}"/>
            <TextBlock Text="{x:Bind Subtitle}" 
                       TextWrapping="Wrap" HorizontalAlignment="Left" 
                       Width="300" Style="{StaticResource BodyTextBlockStyle}"/>
        </StackPanel>
    </StackPanel>
</DataTemplate>
```

**<span data-ttu-id="d25a5-155">Definieren der verkleinerten Ansicht</span><span class="sxs-lookup"><span data-stu-id="d25a5-155">Define the zoomed-out view</span></span>**

<span data-ttu-id="d25a5-156">Dieser XAML-Code definiert ein ListView-Steuerelement für die verkleinerte Ansicht.</span><span class="sxs-lookup"><span data-stu-id="d25a5-156">This XAML defines a ListView control for the zoomed-out view.</span></span> <span data-ttu-id="d25a5-157">Dieses Beispiel zeigt, wie die Gruppenkopfzeilen als Text in einer Liste angezeigt werden sollten.</span><span class="sxs-lookup"><span data-stu-id="d25a5-157">This example shows how to display the group headers as text in a list.</span></span>

```xaml
<SemanticZoom.ZoomedOutView>
    <ListView ItemsSource="{x:Bind cvsGroups.View.CollectionGroups}" 
              SelectionMode="None" 
              ItemTemplate="{StaticResource ZoomedOutTemplate}" />
</SemanticZoom.ZoomedOutView>
```

 <span data-ttu-id="d25a5-158">Die Darstellung wird in der Ressource `ZoomedOutTemplate` definiert.</span><span class="sxs-lookup"><span data-stu-id="d25a5-158">The look is defined in the `ZoomedOutTemplate` resource.</span></span>
 
```xaml    
<DataTemplate x:Key="ZoomedOutTemplate" x:DataType="wuxdata:ICollectionViewGroup">
    <TextBlock Text="{x:Bind Group.(data:ControlInfoDataGroup.Title)}" 
               Style="{StaticResource SubtitleTextBlockStyle}" TextWrapping="Wrap"/>
</DataTemplate>
```

**<span data-ttu-id="d25a5-159">Synchronisieren der Ansichten</span><span class="sxs-lookup"><span data-stu-id="d25a5-159">Synchronize the views</span></span>**

<span data-ttu-id="d25a5-160">Die vergrößerte und verkleinerte Ansicht sollten synchronisiert werden, sodass für den Fall, dass ein Benutzer eine Gruppe in der verkleinerten Ansicht auswählt, die Details dieser Gruppe in der vergrößerten Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d25a5-160">The zoomed-in view and zoomed-out view should be synchronized, so if a user selects a group in the zoomed-out view, the details of that same group are shown in the zoomed-in view.</span></span> <span data-ttu-id="d25a5-161">Sie können eine [CollectionViewSource](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.data.collectionviewsource.aspx) verwenden oder Code hinzufügen, um die Ansichten zu synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="d25a5-161">You can use a [CollectionViewSource](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.data.collectionviewsource.aspx) or add code to synchronize the views.</span></span>

<span data-ttu-id="d25a5-162">Alle Steuerelemente, die Sie an die gleiche CollectionViewSource binden, verfügen immer über das gleiche aktuelle Element.</span><span class="sxs-lookup"><span data-stu-id="d25a5-162">Any controls that you bind to the same CollectionViewSource always have the same current item.</span></span> <span data-ttu-id="d25a5-163">Wenn beide Ansichten die gleiche CollectionViewSource als Datenquelle verwenden, synchronisiert die CollectionViewSource die Ansichten automatisch.</span><span class="sxs-lookup"><span data-stu-id="d25a5-163">If both views use the same CollectionViewSource as their data source, the CollectionViewSource synchronizes the views automatically.</span></span> <span data-ttu-id="d25a5-164">Weitere Informationen finden Sie unter [CollectionViewSource](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.data.collectionviewsource.aspx).</span><span class="sxs-lookup"><span data-stu-id="d25a5-164">For more info, see [CollectionViewSource](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.data.collectionviewsource.aspx).</span></span>

<span data-ttu-id="d25a5-165">Wenn Sie keine CollectionViewSource verwenden, um die Ansichten zu synchronisieren, sollten Sie das [ViewChangeStarted](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.semanticzoom.viewchangestarted.aspx)-Ereignis behandeln und die Elemente wie hier gezeigt im Ereignishandler synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="d25a5-165">If you don't use a CollectionViewSource to synchronize the views, you should handle the [ViewChangeStarted](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.semanticzoom.viewchangestarted.aspx) event and synchronize the items in the event handler, as shown here.</span></span>

```xaml
<SemanticZoom x:Name="semanticZoom" ViewChangeStarted="SemanticZoom_ViewChangeStarted">
```

```csharp
private void SemanticZoom_ViewChangeStarted(object sender, SemanticZoomViewChangedEventArgs e)
{
    if (e.IsSourceZoomedInView == false)
    {
        e.DestinationItem.Item = e.SourceItem.Item;
    }
}
```

## <a name="recommendations"></a><span data-ttu-id="d25a5-166">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="d25a5-166">Recommendations</span></span>

-   <span data-ttu-id="d25a5-167">Stellen Sie bei Verwendung des semantischen Zooms in Ihrer App sicher, dass sich das Elementlayout und die Verschieberichtung nicht basierend auf der Zoomstufe ändern.</span><span class="sxs-lookup"><span data-stu-id="d25a5-167">When using semantic zoom in your app, be sure that the item layout and panning direction don't change based on the zoom level.</span></span> <span data-ttu-id="d25a5-168">Layouts und Verschiebeinteraktionen sollten auf allen Zoomstufen konsistent und vorhersehbar sein.</span><span class="sxs-lookup"><span data-stu-id="d25a5-168">Layouts and panning interactions should be consistent and predictable across zoom levels.</span></span>
-   <span data-ttu-id="d25a5-169">Der semantische Zoom ermöglicht Benutzern das schnelle Wechseln zu Inhalten; beschränken Sie daher die Anzahl der Seiten oder Bildschirme in der verkleinerten Ansicht auf drei.</span><span class="sxs-lookup"><span data-stu-id="d25a5-169">Semantic zoom enables the user to jump quickly to content, so limit the number of pages/screens to three in the zoomed-out mode.</span></span> <span data-ttu-id="d25a5-170">Zu viel Verschiebung beeinträchtigt die praktische Nutzung des semantischen Zooms.</span><span class="sxs-lookup"><span data-stu-id="d25a5-170">Too much panning diminishes the practicality of semantic zoom.</span></span>
-   <span data-ttu-id="d25a5-171">Vermeiden Sie das Verwenden des semantischen Zooms, um den Umfang der Inhalte zu ändern.</span><span class="sxs-lookup"><span data-stu-id="d25a5-171">Avoid using semantic zoom to change the scope of the content.</span></span> <span data-ttu-id="d25a5-172">So sollte beispielsweise ein Fotoalbum nicht zu einer Ordneransicht im Datei-Explorer wechseln.</span><span class="sxs-lookup"><span data-stu-id="d25a5-172">For example, a photo album shouldn't switch to a folder view in File Explorer.</span></span>
-   <span data-ttu-id="d25a5-173">Verwenden Sie eine Struktur und Semantik, die für die Ansicht wichtig sind.</span><span class="sxs-lookup"><span data-stu-id="d25a5-173">Use a structure and semantics that are essential to the view.</span></span>
-   <span data-ttu-id="d25a5-174">Verwenden Sie Gruppennamen für Elemente in einer gruppierten Auflistung.</span><span class="sxs-lookup"><span data-stu-id="d25a5-174">Use group names for items in a grouped collection.</span></span>
-   <span data-ttu-id="d25a5-175">Verwenden Sie die Sortierreihenfolge für eine nicht gruppierte, jedoch sortierte Sammlung, beispielsweise chronologisch für Datumsangaben oder alphabetisch für Namenslisten.</span><span class="sxs-lookup"><span data-stu-id="d25a5-175">Use sort ordering for a collection that is ungrouped but sorted, such as chronological for dates or alphabetical for a list of names.</span></span>


## <a name="get-the-sample-code"></a><span data-ttu-id="d25a5-176">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="d25a5-176">Get the sample code</span></span>

- [<span data-ttu-id="d25a5-177">Einfaches Beispiel für eine XAML-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="d25a5-177">XAML UI Basics sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619992)


## <a name="related-articles"></a><span data-ttu-id="d25a5-178">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="d25a5-178">Related articles</span></span>

- [<span data-ttu-id="d25a5-179">Navigationsdesigngrundlagen</span><span class="sxs-lookup"><span data-stu-id="d25a5-179">Navigation design basics</span></span>](../layout/navigation-basics.md)
- [<span data-ttu-id="d25a5-180">Listenansicht und Rasteransicht</span><span class="sxs-lookup"><span data-stu-id="d25a5-180">List view and grid view</span></span>](listview-and-gridview.md)
- [<span data-ttu-id="d25a5-181">Vorlagen für Listenansichtselemente</span><span class="sxs-lookup"><span data-stu-id="d25a5-181">List view item templates</span></span>](listview-item-templates.md)





