---
author: muhsinking
Description: A semantic zoom control allows the user to zoom between two different semantic views of the same data set.
title: Semantischer Zoom
ms.assetid: B5C21FE7-BA83-4940-9CC1-96F6A2DC28C7
label: Semantic zoom
template: detail.hbs
ms.author: mukin
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
pm-contact: predavid
design-contact: kimsea
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 384110e404e5520f9edacc1385242f4aa131a92c
ms.sourcegitcommit: 929fa4b3273862dcdc76b083bf6c3b2c872dd590
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2018
ms.locfileid: "1935840"
---
# <a name="semantic-zoom"></a><span data-ttu-id="7b123-103">Semantischer Zoom</span><span class="sxs-lookup"><span data-stu-id="7b123-103">Semantic zoom</span></span>

 

<span data-ttu-id="7b123-104">Mit dem semantischen Zoom können Benutzer zwischen zwei unterschiedlichen Ansichten desselben Inhalts zoomen, um schnell durch große Mengen gruppierter Daten zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="7b123-104">Semantic zoom lets the user switch between two different views of the same content so that they can quickly navigate through a large set of grouped data.</span></span>
 
- <span data-ttu-id="7b123-105">Die vergrößerte Ansicht ist die Hauptansicht des Inhalts.</span><span class="sxs-lookup"><span data-stu-id="7b123-105">The zoomed-in view is the main view of the content.</span></span> <span data-ttu-id="7b123-106">Dies ist die Hauptansicht, in der Sie einzelne Datenelemente anzeigen.</span><span class="sxs-lookup"><span data-stu-id="7b123-106">This is the main view where you show individual data items.</span></span> 
- <span data-ttu-id="7b123-107">Die verkleinerte Ansicht zeigt den gleichen Inhalt auf höherer Ebene.</span><span class="sxs-lookup"><span data-stu-id="7b123-107">The zoomed-out view is a higher-level view of the same content.</span></span> <span data-ttu-id="7b123-108">In dieser Ansicht werden normalerweise die Gruppenköpfe für gruppierte Daten angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7b123-108">You typically show the group headers for a grouped data set in this view.</span></span> 

<span data-ttu-id="7b123-109">Bei der Anzeige eines Adressbuchs kann der Benutzer beispielsweise schnell zum Buchstaben „W” springen und diesen vergrößern, um die zu dem betreffenden Buchstaben gehörenden Namen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="7b123-109">For example, when viewing an address book, the user could zoom out to quickly jump to the letter "W", and zoom in on that letter to see the names associated with it.</span></span> 

> <span data-ttu-id="7b123-110">**Wichtige APIs**: [SemanticZoom-Klasse](https://msdn.microsoft.com/library/windows/apps/hh702601), [ListView-Klasse](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.listview.aspx), [GridView-Klasse](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.gridview.aspx)</span><span class="sxs-lookup"><span data-stu-id="7b123-110">**Important APIs**: [SemanticZoom class](https://msdn.microsoft.com/library/windows/apps/hh702601), [ListView class](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.listview.aspx), [GridView class](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.gridview.aspx)</span></span>

<span data-ttu-id="7b123-111">**Features**:</span><span class="sxs-lookup"><span data-stu-id="7b123-111">**Features**:</span></span>

-   <span data-ttu-id="7b123-112">Die Größe der verkleinerten Ansicht ist durch die Grenzen des Steuerelements für semantischen Zoom beschränkt.</span><span class="sxs-lookup"><span data-stu-id="7b123-112">The size of the zoomed-out view is constrained by the bounds of the semantic zoom control.</span></span>
-   <span data-ttu-id="7b123-113">Durch Tippen auf einen Gruppenkopf wird zwischen Ansichten gewechselt.</span><span class="sxs-lookup"><span data-stu-id="7b123-113">Tapping on a group header toggles views.</span></span> <span data-ttu-id="7b123-114">Auch Zusammendrücken kann als Möglichkeit zum Wechseln zwischen den Ansichten aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="7b123-114">Pinching as a way to toggle between views can be enabled.</span></span>
-   <span data-ttu-id="7b123-115">Aktive Kopfzeilen wechseln zwischen Ansichten.</span><span class="sxs-lookup"><span data-stu-id="7b123-115">Active headers switch between views.</span></span>

## <a name="is-this-the-right-control"></a><span data-ttu-id="7b123-116">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="7b123-116">Is this the right control?</span></span>

<span data-ttu-id="7b123-117">Verwenden Sie das Steuerelement **SemanticZoom**, wenn Sie einen gruppierten Datensatz anzeigen müssen, der so groß ist, dass er auf einer oder zwei Seiten nicht ganz angezeigt werden kann.</span><span class="sxs-lookup"><span data-stu-id="7b123-117">Use a **SemanticZoom** control when you need to show a grouped data set that's large enough that it can’t all be shown on one or two pages.</span></span>

<span data-ttu-id="7b123-118">Der semantische Zoom ist nicht mit dem optischen Zoom zu verwechseln.</span><span class="sxs-lookup"><span data-stu-id="7b123-118">Don't confuse semantic zooming with optical zooming.</span></span> <span data-ttu-id="7b123-119">Sie zeigen zwar das gleiche Interaktions- und Grundverhalten (d.h. sie zeigen je nach Zoomfaktor mehr oder weniger Details an), der optische Zoom betrifft jedoch die Größenanpassung für einen Inhaltsbereich oder ein Objekt wie etwa ein Foto.</span><span class="sxs-lookup"><span data-stu-id="7b123-119">While they share both the same interaction and basic behavior (displaying more or less detail based on a zoom factor), optical zoom refers to the adjustment of magnification for a content area or object such as a photograph.</span></span> <span data-ttu-id="7b123-120">Informationen zu einem Steuerelement, das optisches Zooming durchführt, finden Sie im Artikel über das Steuerelement [ScrollViewer](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.aspx).</span><span class="sxs-lookup"><span data-stu-id="7b123-120">For info about a control that performs optical zooming, see the [ScrollViewer](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.aspx) control.</span></span>

## <a name="examples"></a><span data-ttu-id="7b123-121">Beispiele</span><span class="sxs-lookup"><span data-stu-id="7b123-121">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="7b123-122">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="7b123-122">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="7b123-123">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/SemanticZoom">die App zu öffnen und SemanticZoom in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="7b123-123">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/SemanticZoom">open the app and see the SemanticZoom in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="7b123-124">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="7b123-124">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="7b123-125">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="7b123-125">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

**<span data-ttu-id="7b123-126">Fotos-App</span><span class="sxs-lookup"><span data-stu-id="7b123-126">Photos app</span></span>**

<span data-ttu-id="7b123-127">Hier ist ein in der Fotos-App verwendeter semantischer Zoom.</span><span class="sxs-lookup"><span data-stu-id="7b123-127">Here's a semantic zoom used in the Photos app.</span></span> <span data-ttu-id="7b123-128">Fotos werden nach Monat gruppiert.</span><span class="sxs-lookup"><span data-stu-id="7b123-128">Photos are grouped by month.</span></span> <span data-ttu-id="7b123-129">Durch Auswahl einer Monatskopfzeile in der standardmäßigen Rasteransicht wird die Ansicht der Monatsliste verkleinert, um schneller navigieren zu können.</span><span class="sxs-lookup"><span data-stu-id="7b123-129">Selecting a month header in the default grid view zooms out to the month list view for quicker navigation.</span></span>

![In der Fotos-App verwendeter semantischer Zoom](images/control-examples/semantic-zoom-photos.png)

**<span data-ttu-id="7b123-131">Adressbuch</span><span class="sxs-lookup"><span data-stu-id="7b123-131">Address book</span></span>**

<span data-ttu-id="7b123-132">Ein Adressbuch ist ein weiteres Beispiel für einen Datensatz, der sich mit einem Steuerelement für semantisches Zoomen sehr viel einfacher durchblättern lässt.</span><span class="sxs-lookup"><span data-stu-id="7b123-132">An address book is another example of a data set that can be much easier to navigate using semantic zoom.</span></span> <span data-ttu-id="7b123-133">Sie können die verkleinerte Ansicht verwenden, um schnell zu dem gewünschten Buchstaben zu springen (linkes Bild), während die vergrößerte Ansicht die einzelnen Datenelemente zeigt (rechtes Bild).</span><span class="sxs-lookup"><span data-stu-id="7b123-133">You can use the zoomed-out view to quickly jump to the letter you need (left image), while the zoomed-in view displays the individual data items (right image).</span></span>

![Beispiel für semantischen Zoom in einer Kontaktliste](images/semanticzoom-win10.png)

## <a name="create-a-semantic-zoom"></a><span data-ttu-id="7b123-135">Erstellen eines semantischen Zooms</span><span class="sxs-lookup"><span data-stu-id="7b123-135">Create a semantic zoom</span></span>

<span data-ttu-id="7b123-136">Das Steuerelement **SemanticZoom** verfügt über keine visuelle Darstellung.</span><span class="sxs-lookup"><span data-stu-id="7b123-136">The **SemanticZoom** control doesn’t have any visual representation of its own.</span></span> <span data-ttu-id="7b123-137">Es handelt sich um ein Hoststeuerelement, das den Übergang zwischen zwei anderen Steuerelementen steuert, die die Ansichten für Ihre Inhalte bereitstellen, in der Regel die Steuerelemente **ListView** oder **GridView**.</span><span class="sxs-lookup"><span data-stu-id="7b123-137">It’s a host control that manages the transition between 2 other controls that provide the views of your content, typically **ListView** or **GridView** controls.</span></span>  <span data-ttu-id="7b123-138">Sie legen die Ansicht-Steuerelemente auf die [ZoomedInView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.semanticzoom.zoomedinview.aspx)- und [ZoomedOutView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.semanticzoom.zoomedoutview.aspx)-Eigenschaften von SemanticZoom fest.</span><span class="sxs-lookup"><span data-stu-id="7b123-138">You set the view controls to the [ZoomedInView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.semanticzoom.zoomedinview.aspx) and [ZoomedOutView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.semanticzoom.zoomedoutview.aspx) properties of the SemanticZoom.</span></span>

<span data-ttu-id="7b123-139">Sie benötigen für einen semantischen Zoom folgende drei Elemente:</span><span class="sxs-lookup"><span data-stu-id="7b123-139">The 3 elements you need for a semantic zoom are:</span></span>
- <span data-ttu-id="7b123-140">Eine gruppierte Datenquelle</span><span class="sxs-lookup"><span data-stu-id="7b123-140">A grouped data source</span></span>
- <span data-ttu-id="7b123-141">Eine vergrößerte Ansicht, die Daten auf Elementebene anzeigt</span><span class="sxs-lookup"><span data-stu-id="7b123-141">A zoomed-in view that shows the item-level data.</span></span>
- <span data-ttu-id="7b123-142">Eine verkleinerte Ansicht, die die Daten auf Gruppenebene anzeigt</span><span class="sxs-lookup"><span data-stu-id="7b123-142">A zoomed-out view that shows the group-level data.</span></span>

<span data-ttu-id="7b123-143">Bevor Sie einen semantischen Zoom verwenden, sollten Sie wissen, wie Sie eine Listenansicht mit gruppierten Daten verwenden.</span><span class="sxs-lookup"><span data-stu-id="7b123-143">Before you use a semantic zoom, you should understand how to use a list view with grouped data.</span></span> <span data-ttu-id="7b123-144">Weitere Informationen finden Sie unter [Listenansicht und Rasteransicht](listview-and-gridview.md) und [Gruppieren von Elementen in einer Liste]().</span><span class="sxs-lookup"><span data-stu-id="7b123-144">For more info, see [List view and grid view](listview-and-gridview.md) and [Grouping items in a list]().</span></span> 

> <span data-ttu-id="7b123-145">**Hinweis**:&nbsp;&nbsp;Um die vergrößerte und verkleinerte Ansicht des SemanticZoom-Steuerelements zu definieren, können Sie zwei beliebige Steuerelemente verwenden, die die Benutzeroberfläche [ISemanticZoomInformation](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.isemanticzoominformation.aspx) implementieren.</span><span class="sxs-lookup"><span data-stu-id="7b123-145">**Note**&nbsp;&nbsp;To define the zoomed-in view and the zoomed-out view of the SemanticZoom control, you can use any two controls that implement the [ISemanticZoomInformation](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.isemanticzoominformation.aspx) interface.</span></span> <span data-ttu-id="7b123-146">Das XAML-Framework bietet drei Steuerelemente, die diese Schnittstelle implementieren: ListView, GridView und Hub.</span><span class="sxs-lookup"><span data-stu-id="7b123-146">The XAML framework provides 3 controls that implement this interface: ListView, GridView, and Hub.</span></span>
 
 <span data-ttu-id="7b123-147">Dieser XAML-Code zeigt die Struktur des SemanticZoom-Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="7b123-147">This XAML shows the structure of the SemanticZoom control.</span></span> <span data-ttu-id="7b123-148">Sie weisen weitere Steuerelemente den Eigenschaften „ZoomedInView” und „ZoomedOutView” zu.</span><span class="sxs-lookup"><span data-stu-id="7b123-148">You assign other controls to the ZoomedInView and ZoomedOutView properties.</span></span>
 
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
 
<span data-ttu-id="7b123-149">Die folgenden Beispiele stammen von der Seite „SemanticZoom” des [Beispiels für XAML-UI-Grundlagen](http://go.microsoft.com/fwlink/p/?LinkId=619992).</span><span class="sxs-lookup"><span data-stu-id="7b123-149">The examples here are taken from the SemanticZoom page of the [XAML UI Basics sample](http://go.microsoft.com/fwlink/p/?LinkId=619992).</span></span> <span data-ttu-id="7b123-150">Sie können das Beispiel herunterladen, um den kompletten Code anzuzeigen, einschließlich der Datenquelle.</span><span class="sxs-lookup"><span data-stu-id="7b123-150">You can download the sample to see the complete code including the data source.</span></span> <span data-ttu-id="7b123-151">Dieser semantische Zoom verwendet eine GridView, um die vergrößerte Ansicht und eine ListView für die verkleinerte Ansicht bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="7b123-151">This semantic zoom uses a GridView to supply the zoomed-in view and a ListView for the zoomed-out view.</span></span>
  
**<span data-ttu-id="7b123-152">Definieren der vergrößerten Ansicht</span><span class="sxs-lookup"><span data-stu-id="7b123-152">Define the zoomed-in view</span></span>**

<span data-ttu-id="7b123-153">Hier sehen Sie das GridView-Steuerelement für die vergrößerte Ansicht.</span><span class="sxs-lookup"><span data-stu-id="7b123-153">Here's the GridView control for the zoomed-in view.</span></span> <span data-ttu-id="7b123-154">Die vergrößerte Ansicht sollte die einzelnen Datenelemente in Gruppen anzeigen.</span><span class="sxs-lookup"><span data-stu-id="7b123-154">The zoomed-in view should display the individual data items in groups.</span></span> <span data-ttu-id="7b123-155">Dieses Beispiel zeigt, wie die Elemente in einem Raster mit einem Bild und Text angezeigt werden sollten.</span><span class="sxs-lookup"><span data-stu-id="7b123-155">This example shows how to display the items in a grid with an image and text.</span></span> 

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
 
<span data-ttu-id="7b123-156">Die Darstellung der Gruppenkopfzeilen wird in der Ressource `ZoomedInGroupHeaderTemplate` definiert.</span><span class="sxs-lookup"><span data-stu-id="7b123-156">The look of the group headers is defined in the `ZoomedInGroupHeaderTemplate` resource.</span></span> <span data-ttu-id="7b123-157">Die Darstellung der Elemente wird in der Ressource `ZoomedInTemplate` definiert.</span><span class="sxs-lookup"><span data-stu-id="7b123-157">The look of the items is defined in the `ZoomedInTemplate` resource.</span></span> 

```xaml
<DataTemplate x:Key="ZoomedInGroupHeaderTemplate" x:DataType="data:ControlInfoDataGroup">
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

**<span data-ttu-id="7b123-158">Definieren der verkleinerten Ansicht</span><span class="sxs-lookup"><span data-stu-id="7b123-158">Define the zoomed-out view</span></span>**

<span data-ttu-id="7b123-159">Dieser XAML-Code definiert ein ListView-Steuerelement für die verkleinerte Ansicht.</span><span class="sxs-lookup"><span data-stu-id="7b123-159">This XAML defines a ListView control for the zoomed-out view.</span></span> <span data-ttu-id="7b123-160">Dieses Beispiel zeigt, wie die Gruppenkopfzeilen als Text in einer Liste angezeigt werden sollten.</span><span class="sxs-lookup"><span data-stu-id="7b123-160">This example shows how to display the group headers as text in a list.</span></span>

```xaml
<SemanticZoom.ZoomedOutView>
    <ListView ItemsSource="{x:Bind cvsGroups.View.CollectionGroups}" 
              SelectionMode="None" 
              ItemTemplate="{StaticResource ZoomedOutTemplate}" />
</SemanticZoom.ZoomedOutView>
```

 <span data-ttu-id="7b123-161">Die Darstellung wird in der Ressource `ZoomedOutTemplate` definiert.</span><span class="sxs-lookup"><span data-stu-id="7b123-161">The look is defined in the `ZoomedOutTemplate` resource.</span></span>
 
```xaml    
<DataTemplate x:Key="ZoomedOutTemplate" x:DataType="wuxdata:ICollectionViewGroup">
    <TextBlock Text="{x:Bind Group.(data:ControlInfoDataGroup.Title)}" 
               Style="{StaticResource SubtitleTextBlockStyle}" TextWrapping="Wrap"/>
</DataTemplate>
```

**<span data-ttu-id="7b123-162">Synchronisieren der Ansichten</span><span class="sxs-lookup"><span data-stu-id="7b123-162">Synchronize the views</span></span>**

<span data-ttu-id="7b123-163">Die vergrößerte und verkleinerte Ansicht sollten synchronisiert werden, sodass für den Fall, dass ein Benutzer eine Gruppe in der verkleinerten Ansicht auswählt, die Details dieser Gruppe in der vergrößerten Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7b123-163">The zoomed-in view and zoomed-out view should be synchronized, so if a user selects a group in the zoomed-out view, the details of that same group are shown in the zoomed-in view.</span></span> <span data-ttu-id="7b123-164">Sie können eine [CollectionViewSource](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.data.collectionviewsource.aspx) verwenden oder Code hinzufügen, um die Ansichten zu synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="7b123-164">You can use a [CollectionViewSource](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.data.collectionviewsource.aspx) or add code to synchronize the views.</span></span>

<span data-ttu-id="7b123-165">Alle Steuerelemente, die Sie an die gleiche CollectionViewSource binden, verfügen immer über das gleiche aktuelle Element.</span><span class="sxs-lookup"><span data-stu-id="7b123-165">Any controls that you bind to the same CollectionViewSource always have the same current item.</span></span> <span data-ttu-id="7b123-166">Wenn beide Ansichten die gleiche CollectionViewSource als Datenquelle verwenden, synchronisiert die CollectionViewSource die Ansichten automatisch.</span><span class="sxs-lookup"><span data-stu-id="7b123-166">If both views use the same CollectionViewSource as their data source, the CollectionViewSource synchronizes the views automatically.</span></span> <span data-ttu-id="7b123-167">Weitere Informationen finden Sie unter [CollectionViewSource](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.data.collectionviewsource.aspx).</span><span class="sxs-lookup"><span data-stu-id="7b123-167">For more info, see [CollectionViewSource](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.data.collectionviewsource.aspx).</span></span>

<span data-ttu-id="7b123-168">Wenn Sie keine CollectionViewSource verwenden, um die Ansichten zu synchronisieren, sollten Sie das [ViewChangeStarted](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.semanticzoom.viewchangestarted.aspx)-Ereignis behandeln und die Elemente wie hier gezeigt im Ereignishandler synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="7b123-168">If you don't use a CollectionViewSource to synchronize the views, you should handle the [ViewChangeStarted](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.semanticzoom.viewchangestarted.aspx) event and synchronize the items in the event handler, as shown here.</span></span>

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

## <a name="recommendations"></a><span data-ttu-id="7b123-169">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="7b123-169">Recommendations</span></span>

-   <span data-ttu-id="7b123-170">Stellen Sie bei Verwendung des semantischen Zooms in Ihrer App sicher, dass sich das Elementlayout und die Verschieberichtung nicht basierend auf der Zoomstufe ändern.</span><span class="sxs-lookup"><span data-stu-id="7b123-170">When using semantic zoom in your app, be sure that the item layout and panning direction don't change based on the zoom level.</span></span> <span data-ttu-id="7b123-171">Layouts und Verschiebeinteraktionen sollten auf allen Zoomstufen konsistent und vorhersehbar sein.</span><span class="sxs-lookup"><span data-stu-id="7b123-171">Layouts and panning interactions should be consistent and predictable across zoom levels.</span></span>
-   <span data-ttu-id="7b123-172">Der semantische Zoom ermöglicht Benutzern das schnelle Wechseln zu Inhalten; beschränken Sie daher die Anzahl der Seiten oder Bildschirme in der verkleinerten Ansicht auf drei.</span><span class="sxs-lookup"><span data-stu-id="7b123-172">Semantic zoom enables the user to jump quickly to content, so limit the number of pages/screens to three in the zoomed-out mode.</span></span> <span data-ttu-id="7b123-173">Zu viel Verschiebung beeinträchtigt die praktische Nutzung des semantischen Zooms.</span><span class="sxs-lookup"><span data-stu-id="7b123-173">Too much panning diminishes the practicality of semantic zoom.</span></span>
-   <span data-ttu-id="7b123-174">Vermeiden Sie das Verwenden des semantischen Zooms, um den Umfang der Inhalte zu ändern.</span><span class="sxs-lookup"><span data-stu-id="7b123-174">Avoid using semantic zoom to change the scope of the content.</span></span> <span data-ttu-id="7b123-175">So sollte beispielsweise ein Fotoalbum nicht zu einer Ordneransicht im Datei-Explorer wechseln.</span><span class="sxs-lookup"><span data-stu-id="7b123-175">For example, a photo album shouldn't switch to a folder view in File Explorer.</span></span>
-   <span data-ttu-id="7b123-176">Verwenden Sie eine Struktur und Semantik, die für die Ansicht wichtig sind.</span><span class="sxs-lookup"><span data-stu-id="7b123-176">Use a structure and semantics that are essential to the view.</span></span>
-   <span data-ttu-id="7b123-177">Verwenden Sie Gruppennamen für Elemente in einer gruppierten Auflistung.</span><span class="sxs-lookup"><span data-stu-id="7b123-177">Use group names for items in a grouped collection.</span></span>
-   <span data-ttu-id="7b123-178">Verwenden Sie die Sortierreihenfolge für eine nicht gruppierte, jedoch sortierte Sammlung, beispielsweise chronologisch für Datumsangaben oder alphabetisch für Namenslisten.</span><span class="sxs-lookup"><span data-stu-id="7b123-178">Use sort ordering for a collection that is ungrouped but sorted, such as chronological for dates or alphabetical for a list of names.</span></span>


## <a name="get-the-sample-code"></a><span data-ttu-id="7b123-179">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="7b123-179">Get the sample code</span></span>

- <span data-ttu-id="7b123-180">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="7b123-180">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>


## <a name="related-articles"></a><span data-ttu-id="7b123-181">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="7b123-181">Related articles</span></span>

- [<span data-ttu-id="7b123-182">Navigationsdesigngrundlagen</span><span class="sxs-lookup"><span data-stu-id="7b123-182">Navigation design basics</span></span>](../basics/navigation-basics.md)
- [<span data-ttu-id="7b123-183">Listenansicht und Rasteransicht</span><span class="sxs-lookup"><span data-stu-id="7b123-183">List view and grid view</span></span>](listview-and-gridview.md)
- [<span data-ttu-id="7b123-184">Elementcontainer und Vorlagen</span><span class="sxs-lookup"><span data-stu-id="7b123-184">Item containers and templates</span></span>](item-containers-templates.md)





