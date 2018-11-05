---
author: muhsinking
Description: Use ListView and GridView controls to display and manipulate sets of data, such as a gallery of images or a set of email messages.
title: Listenansicht und Rasteransicht
label: List view and grid view
template: detail.hbs
ms.author: jimwalk
ms.date: 05/20/2017
ms.topic: article
keywords: Windows10, UWP
ms.assetid: f8532ba0-5510-4686-9fcf-87fd7c643e7b
pm-contact: predavid
design-contact: kimsea
dev-contact: ranjeshj
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 1ee00a9af23be945ad27ab4b39eec127ec397894
ms.sourcegitcommit: e814a13978f33654d8e995584f4b047cb53e0aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "6037705"
---
# <a name="list-view-and-grid-view"></a><span data-ttu-id="d59f3-103">Listenansicht und Rasteransicht</span><span class="sxs-lookup"><span data-stu-id="d59f3-103">List view and grid view</span></span>

<span data-ttu-id="d59f3-104">Mit den meisten Anwendungen können Sätze von Daten, beispielsweise eine Bildergalerie oder ein Satz von E-Mails, bearbeitet und angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d59f3-104">Most applications manipulate and display sets of data, such as a gallery of images or a set of email messages.</span></span> <span data-ttu-id="d59f3-105">Das XAML-Benutzeroberflächenframework bietet ListView und GridView-Steuerelemente, die das Anzeigen und Bearbeiten von Daten in Ihrer App vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-105">The XAML UI framework provides ListView and GridView controls that make it easy to display and manipulate data in your app.</span></span>  

> <span data-ttu-id="d59f3-106">**Wichtige APIs**: [ListView-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx), [GridView-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.gridview.aspx), [ItemsSource-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemssource.aspx), [Items-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.items.aspx)</span><span class="sxs-lookup"><span data-stu-id="d59f3-106">**Important APIs**: [ListView class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx), [GridView class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.gridview.aspx), [ItemsSource property](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemssource.aspx), [Items property](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.items.aspx)</span></span>

<span data-ttu-id="d59f3-107">ListView und GridView werden beide von der ListViewBase-Klasse abgeleitet, sodass sie die gleiche Funktionsweise haben, Daten jedoch unterschiedlich anzeigen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-107">ListView and GridView both derive from the ListViewBase class, so they have the same functionality, but display data differently.</span></span> <span data-ttu-id="d59f3-108">In diesem Artikel beziehen sich Aussagen zu ListView sowohl auf die ListView- als auch die GridView-Steuerelemente, wenn nicht anders angegeben.</span><span class="sxs-lookup"><span data-stu-id="d59f3-108">In this article, when we talk about ListView, the info applies to both the ListView and GridView controls unless otherwise specified.</span></span> <span data-ttu-id="d59f3-109">Möglicherweise werden Klassen wie ListView oder ListViewItem genannt. Das Präfix „List“ kann jedoch durch „Grid“ für das entsprechende Rastersteuerelement ersetzt werden (GridView oder GridViewItem).</span><span class="sxs-lookup"><span data-stu-id="d59f3-109">We may refer to classes like ListView or ListViewItem, but the “List” prefix can be replaced with “Grid” for the corresponding grid equivalent (GridView or GridViewItem).</span></span> 

## <a name="is-this-the-right-control"></a><span data-ttu-id="d59f3-110">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="d59f3-110">Is this the right control?</span></span>

<span data-ttu-id="d59f3-111">ListView zeigt Daten vertikal in einer einzelnen Spalte an.</span><span class="sxs-lookup"><span data-stu-id="d59f3-111">The ListView displays data stacked vertically in a single column.</span></span> <span data-ttu-id="d59f3-112">Sie wird häufig für die Anzeige geordneter Listen von Elementen verwendet, z.B. von E-Mails oder Suchergebnissen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-112">It's often used to show an ordered list of items, such as a list of emails or search results.</span></span> 

![Eine Listenansicht mit gruppierten Daten](images/simple-list-view-phone.png)

<span data-ttu-id="d59f3-114">GridView zeigt eine Sammlung von Elementen in Zeilen und Spalten an, für die ein horizontaler Bildlauf durchgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="d59f3-114">The GridView presents a collection of items in rows and columns that can scroll vertically.</span></span> <span data-ttu-id="d59f3-115">Daten werden horizontal angeordnet, bis die Spalten gefüllt sind. Anschließend wird mit der nächsten Zeile fortgefahren.</span><span class="sxs-lookup"><span data-stu-id="d59f3-115">Data is stacked horizontally until it fills the columns, then continues with the next row.</span></span> <span data-ttu-id="d59f3-116">Die Rasteransicht wird häufig für Visualisierungen verwendet, bei denen die Elemente mehr Platz benötigen, z.B. in einer Fotogalerie.</span><span class="sxs-lookup"><span data-stu-id="d59f3-116">It's often used when you need to show a rich visualization of each item that takes more space, such as a photo gallery.</span></span> 

![Beispiel einer Inhaltsbibliothek](images/controls_list_contentlibrary.png)

<span data-ttu-id="d59f3-118">Einen detaillierteren Vergleich und Anleitungen dazu, welches Steuerelement verwendet werden sollte, finden Sie unter [Listen](lists.md).</span><span class="sxs-lookup"><span data-stu-id="d59f3-118">For a more detailed comparison and guidance on which control to use, see [Lists](lists.md).</span></span>

## <a name="examples"></a><span data-ttu-id="d59f3-119">Beispiele</span><span class="sxs-lookup"><span data-stu-id="d59f3-119">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="d59f3-120">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="d59f3-120">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="d59f3-121">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um die App zu öffnen und <a href="xamlcontrolsgallery:/item/ListView">ListView</a> oder <a href="xamlcontrolsgallery:/item/GridView">GridView</a> in Aktion zu sehen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-121">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to open the app and see the <a href="xamlcontrolsgallery:/item/ListView">ListView</a> or <a href="xamlcontrolsgallery:/item/GridView">GridView</a> in action.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="d59f3-122">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="d59f3-122">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="d59f3-123">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="d59f3-123">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="create-a-list-view"></a><span data-ttu-id="d59f3-124">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="d59f3-124">Create a list view</span></span>

<span data-ttu-id="d59f3-125">Die Listenansicht ist ein [ItemsControl](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.aspx), sodass sie eine Sammlung von Elementen jeden Typs enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="d59f3-125">List view is an [ItemsControl](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.aspx), so it can contain a collection of items of any type.</span></span> <span data-ttu-id="d59f3-126">In der [Items](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.items.aspx)-Sammlung müssen Elemente vorhanden sein, bevor auf dem Bildschirm etwas angezeigt werden kann.</span><span class="sxs-lookup"><span data-stu-id="d59f3-126">It must have items in its [Items](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.items.aspx) collection before it can show anything on the screen.</span></span> <span data-ttu-id="d59f3-127">Elemente für die Ansicht können Sie direkt in die [Items](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.items.aspx)-Sammlung einfügen oder alternativ die [ItemsSource](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemssource.aspx)-Eigenschaft als Datenquelle festlegen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-127">To populate the view, you can add items directly to the [Items](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.items.aspx) collection, or set the [ItemsSource](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemssource.aspx) property to a data source.</span></span> 

<span data-ttu-id="d59f3-128">**Wichtig**&nbsp;&nbsp;Sie können Items oder ItemsSource zum Ausfüllen der Liste verwenden, jedoch nicht beide gleichzeitig.</span><span class="sxs-lookup"><span data-stu-id="d59f3-128">**Important**&nbsp;&nbsp;You can use either Items or ItemsSource to populate the list, but you can't use both at the same time.</span></span> <span data-ttu-id="d59f3-129">Wenn Sie die ItemsSource-Eigenschaft festlegen und dann ein Element in XAML hinzufügen, wird das hinzugefügte Element ignoriert.</span><span class="sxs-lookup"><span data-stu-id="d59f3-129">If you set the ItemsSource property and you add an item in XAML, the added item is ignored.</span></span> <span data-ttu-id="d59f3-130">Wenn Sie die ItemsSource-Eigenschaft festlegen und der Items-Sammlung ein Element in Code hinzufügen, wird eine Ausnahme ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="d59f3-130">If you set the ItemsSource property and you add an item to the Items collection in code, an exception is thrown.</span></span>

> <span data-ttu-id="d59f3-131">**Hinweis**&nbsp;&nbsp;Viele Beispiele in diesem Artikel füllen der Einfachheit halber die **Items**-Sammlung direkt aus.</span><span class="sxs-lookup"><span data-stu-id="d59f3-131">**Note**&nbsp;&nbsp;Many of the examples in this article populate the **Items** collection directly for the sake of simplicity.</span></span> <span data-ttu-id="d59f3-132">Häufiger stammen die Elemente in einer Liste jedoch aus einer dynamischen Quelle, z.B. einer Liste von Büchern aus einer Onlinedatenbank.</span><span class="sxs-lookup"><span data-stu-id="d59f3-132">However, it's more common for the items in a list to come from a dynamic source, like a list of books from an online database.</span></span> <span data-ttu-id="d59f3-133">Verwenden Sie für diesen Zweck die **ItemsSource**-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="d59f3-133">You use the **ItemsSource** property for this purpose.</span></span> 

### <a name="add-items-to-the-items-collection"></a><span data-ttu-id="d59f3-134">Hinzufügen von Elementen zur Sammlung Items</span><span class="sxs-lookup"><span data-stu-id="d59f3-134">Add items to the Items collection</span></span>

<span data-ttu-id="d59f3-135">Die Elemente können der [Items](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.items.aspx)-Sammlung mittels XAML oder Code hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="d59f3-135">You can add items to the [Items](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.items.aspx) collection using XAML or code.</span></span> <span data-ttu-id="d59f3-136">In der Regel fügen Sie Elemente auf diese Weise hinzu, wenn Sie nur über eine geringe Anzahl von Elementen verfügen, die sich nicht ändern und einfach in XAML definiert werden können, oder wenn die Elemente zur Laufzeit im Code generiert werden.</span><span class="sxs-lookup"><span data-stu-id="d59f3-136">You typically add items this way if you have a small number of items that don't change and are easily defined in XAML, or if you generate the items in code at run time.</span></span> 

<span data-ttu-id="d59f3-137">Hier sehen Sie eine Listenansicht mit inline in XAML definierten Elementen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-137">Here's a list view with items defined inline in XAML.</span></span> <span data-ttu-id="d59f3-138">Wenn Sie die Elemente in XAML definieren, werden sie der Sammlung Items automatisch hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="d59f3-138">When you define the items in XAML, they are automatically added to the Items collection.</span></span>

**<span data-ttu-id="d59f3-139">XAML</span><span class="sxs-lookup"><span data-stu-id="d59f3-139">XAML</span></span>**
```xaml
<ListView x:Name="listView1"> 
   <x:String>Item 1</x:String> 
   <x:String>Item 2</x:String> 
   <x:String>Item 3</x:String> 
   <x:String>Item 4</x:String> 
   <x:String>Item 5</x:String> 
</ListView>  
```

<span data-ttu-id="d59f3-140">Hier sehen Sie die Listenansicht in Code erstellt.</span><span class="sxs-lookup"><span data-stu-id="d59f3-140">Here's the list view created in code.</span></span> <span data-ttu-id="d59f3-141">Die resultierende Liste ist mit der zuvor in XAML erstellten Liste identisch.</span><span class="sxs-lookup"><span data-stu-id="d59f3-141">The resulting list is the same as the one created previously in XAML.</span></span>

**<span data-ttu-id="d59f3-142">C#</span><span class="sxs-lookup"><span data-stu-id="d59f3-142">C#</span></span>**
```csharp
// Create a new ListView and add content. 
ListView listView1 = new ListView(); 
listView1.Items.Add("Item 1"); 
listView1.Items.Add("Item 2"); 
listView1.Items.Add("Item 3"); 
listView1.Items.Add("Item 4"); 
listView1.Items.Add("Item 5");
 
// Add the ListView to a parent container in the visual tree. 
stackPanel1.Children.Add(listView1); 
```

<span data-ttu-id="d59f3-143">ListView sieht wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="d59f3-143">The ListView looks like this.</span></span>

![Eine einfache Listenansicht](images/listview-simple.png)

### <a name="set-the-items-source"></a><span data-ttu-id="d59f3-145">Festlegen der Quelle von Elementen</span><span class="sxs-lookup"><span data-stu-id="d59f3-145">Set the items source</span></span>

<span data-ttu-id="d59f3-146">In der Regel verwenden Sie eine Listenansicht, um Daten aus Quellen wie einer Datenbank oder dem Internet anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-146">You typically use a list view to display data from a source such as a database or the Internet.</span></span> <span data-ttu-id="d59f3-147">Um eine Datenquelle für die Listenansicht zu verwenden, müssen Sie eine Sammlung von Datenelementen als deren [ItemsSource](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemssource.aspx)-Eigenschaft festlegen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-147">To populate a list view from a data source, you set its [ItemsSource](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemssource.aspx) property to a collection of data items.</span></span>

<span data-ttu-id="d59f3-148">Hier ist die ItemsSource der Listenansicht im Code direkt auf eine Instanz einer Sammlung festgelegt.</span><span class="sxs-lookup"><span data-stu-id="d59f3-148">Here, the list view's ItemsSource is set in code directly to an instance of a collection.</span></span>

**<span data-ttu-id="d59f3-149">C#</span><span class="sxs-lookup"><span data-stu-id="d59f3-149">C#</span></span>**
```csharp 
// Instead of hard coded items, the data could be pulled 
// asynchronously from a database or the internet.
ObservableCollection<string> listItems = new ObservableCollection<string>();
listItems.Add("Item 1");
listItems.Add("Item 2");
listItems.Add("Item 3");
listItems.Add("Item 4");
listItems.Add("Item 5");

// Create a new list view, add content, 
ListView itemListView = new ListView();
itemListView.ItemsSource = listItems;

// Add the list view to a parent container in the visual tree.
stackPanel1.Children.Add(itemListView);
```

<span data-ttu-id="d59f3-150">Sie können die ItemsSource-Eigenschaft auch an eine Sammlung in XAML binden.</span><span class="sxs-lookup"><span data-stu-id="d59f3-150">You can also bind the ItemsSource property to a collection in XAML.</span></span> <span data-ttu-id="d59f3-151">Weitere Informationen zur Datenbindung finden Sie unter [Übersicht über Datenbindung](https://msdn.microsoft.com/windows/uwp/data-binding/data-binding-quickstart).</span><span class="sxs-lookup"><span data-stu-id="d59f3-151">For more info about data binding, see [Data binding overview](https://msdn.microsoft.com/windows/uwp/data-binding/data-binding-quickstart).</span></span>

<span data-ttu-id="d59f3-152">Hier wird ItemsSource an eine öffentliche Eigenschaft mit dem Namen `Items` gebunden, die die private Datensammlung der Seite verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="d59f3-152">Here, the ItemsSource is bound to a public property named `Items` that exposes the Page's private data collection.</span></span>

**<span data-ttu-id="d59f3-153">XAML</span><span class="sxs-lookup"><span data-stu-id="d59f3-153">XAML</span></span>**
```xaml
<ListView x:Name="itemListView" ItemsSource="{x:Bind Items}"/>
```

**<span data-ttu-id="d59f3-154">C#</span><span class="sxs-lookup"><span data-stu-id="d59f3-154">C#</span></span>**
```csharp
private ObservableCollection<string> _items = new ObservableCollection<string>();

public ObservableCollection<string> Items
{
    get { return this._items; }
}

protected override void OnNavigatedTo(NavigationEventArgs e)
{
    base.OnNavigatedTo(e);

    // Instead of hard coded items, the data could be pulled 
    // asynchronously from a database or the internet.
    Items.Add("Item 1");
    Items.Add("Item 2");
    Items.Add("Item 3");
    Items.Add("Item 4");
    Items.Add("Item 5");
}
```

<span data-ttu-id="d59f3-155">Wenn Sie in der Listenansicht gruppierte Daten anzeigen müssen, müssen Sie an eine [CollectionViewSource](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.data.collectionviewsource.aspx) binden.</span><span class="sxs-lookup"><span data-stu-id="d59f3-155">If you need to show grouped data in your list view, you must bind to a [CollectionViewSource](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.data.collectionviewsource.aspx).</span></span> <span data-ttu-id="d59f3-156">Die CollectionViewSource dient als Proxy für die Sammlungsklasse in XAML und ermöglicht die Unterstützung für Gruppierungen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-156">The CollectionViewSource acts as a proxy for the collection class in XAML and enables grouping support.</span></span> <span data-ttu-id="d59f3-157">Weitere Informationen finden Sie unter [CollectionViewSource](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.data.collectionviewsource.aspx).</span><span class="sxs-lookup"><span data-stu-id="d59f3-157">For more info, see [CollectionViewSource](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.data.collectionviewsource.aspx).</span></span>

## <a name="data-template"></a><span data-ttu-id="d59f3-158">Datenvorlage</span><span class="sxs-lookup"><span data-stu-id="d59f3-158">Data template</span></span>

<span data-ttu-id="d59f3-159">Die Datenvorlage eines Elements definiert die Darstellung der Daten.</span><span class="sxs-lookup"><span data-stu-id="d59f3-159">An item’s data template defines how the data is visualized.</span></span> <span data-ttu-id="d59f3-160">Datenelemente werden in der Listenansicht standardmäßig als Zeichenfolgendarstellung des Datenobjekts angezeigt, an das sie gebunden sind.</span><span class="sxs-lookup"><span data-stu-id="d59f3-160">By default, a data item is displayed in the list view as the string representation of the data object it's bound to.</span></span> <span data-ttu-id="d59f3-161">Sie können die Zeichenfolgendarstellung einer bestimmten Eigenschaft des Datenelements anzeigen, indem Sie den [DisplayMemberPath](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.displaymemberpath.aspx) zur Eigenschaft festlegen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-161">You can show the string representation of a particular property of the data item by setting the [DisplayMemberPath](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.displaymemberpath.aspx) to that property.</span></span>

<span data-ttu-id="d59f3-162">In der Regel möchten Sie jedoch eine ansprechendere Darstellung Ihrer Daten anzeigen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-162">However, you typically want to show a more rich presentation of your data.</span></span> <span data-ttu-id="d59f3-163">Um genau anzugeben, wie Elemente in der Listenansicht angezeigt werden, müssen Sie ein [DataTemplate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.datatemplate.aspx) erstellen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-163">To specify exactly how items in the list view are displayed, you create a [DataTemplate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.datatemplate.aspx).</span></span> <span data-ttu-id="d59f3-164">Der XAML-Code in der DataTemplate definiert das Layout und die Darstellung von Steuerelementen, die zum Anzeigen eines einzelnen Elements verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="d59f3-164">The XAML in the DataTemplate defines the layout and appearance of controls used to display an individual item.</span></span> <span data-ttu-id="d59f3-165">Die Steuerelemente im Layout können an Eigenschaften eines Datenobjekts gebunden werden. Es ist auch möglich, statischen Inhalt intern zu definieren.</span><span class="sxs-lookup"><span data-stu-id="d59f3-165">The controls in the layout can be bound to properties of a data object, or have static content defined inline.</span></span> <span data-ttu-id="d59f3-166">Weisen Sie das DataTemplate der [ItemTemplate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemtemplate.aspx)-Eigenschaft des Listensteuerelements zu.</span><span class="sxs-lookup"><span data-stu-id="d59f3-166">You assign the DataTemplate to the [ItemTemplate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemtemplate.aspx) property of the list control.</span></span>

<span data-ttu-id="d59f3-167">In diesem Beispiel ist das Datenelement eine einfache Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="d59f3-167">In this example, the data item is a simple string.</span></span> <span data-ttu-id="d59f3-168">Verwenden Sie eine DataTemplate, um auf der linken Seite der Zeichenfolge ein Bild hinzuzufügen und die Zeichenfolge in Aquamarin anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-168">You use a DataTemplate to add an image to the left of the string, and show the string in teal.</span></span>

> <span data-ttu-id="d59f3-169">**Hinweis**:&nbsp;&nbsp;Wenn Sie die [x:Bind-Markuperweiterung](https://msdn.microsoft.com/windows/uwp/xaml-platform/x-bind-markup-extension) in einem DataTemplate verwenden, müssen Sie den DataType (`x:DataType`) für das DataTemplate angeben.</span><span class="sxs-lookup"><span data-stu-id="d59f3-169">**Note**&nbsp;&nbsp;When you use the [x:Bind markup extension](https://msdn.microsoft.com/windows/uwp/xaml-platform/x-bind-markup-extension) in a DataTemplate, you have to specify the DataType (`x:DataType`) on the DataTemplate.</span></span>

**<span data-ttu-id="d59f3-170">XAML</span><span class="sxs-lookup"><span data-stu-id="d59f3-170">XAML</span></span>**
```XAML
<ListView x:Name="listView1">
    <ListView.ItemTemplate>
        <DataTemplate x:DataType="x:String">
            <Grid>
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="47"/>
                    <ColumnDefinition/>
                </Grid.ColumnDefinitions>
                <Image Source="Assets/placeholder.png" Width="32" Height="32" 
                       HorizontalAlignment="Left"/>
                <TextBlock Text="{x:Bind}" Foreground="Teal" 
                           FontSize="15" Grid.Column="1"/>
            </Grid> 
        </DataTemplate>
    </ListView.ItemTemplate>
    <x:String>Item 1</x:String>
    <x:String>Item 2</x:String>
    <x:String>Item 3</x:String>
    <x:String>Item 4</x:String>
    <x:String>Item 5</x:String>
</ListView>
```

<span data-ttu-id="d59f3-171">So sehen die Datenelemente aus, wenn sie mit dieser Datenvorlage angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d59f3-171">Here's what the data items look like when displayed with this data template.</span></span>

![Elemente in der Listenansicht mit einer Datenvorlage](images/listview-itemstemplate.png)

<span data-ttu-id="d59f3-173">Datenvorlagen sind der bevorzugte Weg für die Definition des Aussehens Ihrer Listenansicht.</span><span class="sxs-lookup"><span data-stu-id="d59f3-173">Data templates are the primary way you define the look of your list view.</span></span> <span data-ttu-id="d59f3-174">Sie können auch eine erhebliche Auswirkung auf die Leistung haben, wenn in der Liste eine große Anzahl von Elementen angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d59f3-174">They can also have a significant impact on performance if your list displays a large number of items.</span></span> <span data-ttu-id="d59f3-175">In diesem Artikel werden für die meisten Beispiele einfache Zeichenfolgendaten verwendet, und es wird keine Datenvorlage angegeben.</span><span class="sxs-lookup"><span data-stu-id="d59f3-175">In this article, we use simple string data for most of the examples, and don't specify a data template.</span></span> <span data-ttu-id="d59f3-176">Weitere Informationen und Beispiele zur Verwendung von Datenvorlagen und Elementcontainern zur Definition des Aussehens von Elementen in Ihrer Liste oder Ihrem Raster finden Sie unter [Elementcontainer und Vorlagen](item-containers-templates.md).</span><span class="sxs-lookup"><span data-stu-id="d59f3-176">For more info and examples of how to use data templates and item containers to define the look of items in your list or grid, see [Item containers and templates](item-containers-templates.md).</span></span> 

## <a name="change-the-layout-of-items"></a><span data-ttu-id="d59f3-177">Ändern des Layouts von Elementen</span><span class="sxs-lookup"><span data-stu-id="d59f3-177">Change the layout of items</span></span>

<span data-ttu-id="d59f3-178">Wenn Sie Elemente zu einer Listen- oder Rasteransicht hinzufügen, bricht das Steuerelement automatisch alle Elemente in einem Elementcontainer um und ordnet anschließend alle Elementcontainer an.</span><span class="sxs-lookup"><span data-stu-id="d59f3-178">When you add items to a list view or grid view, the control automatically wraps each item in an item container and then lays out all of the item containers.</span></span> <span data-ttu-id="d59f3-179">Die Anordnung dieser Elementcontainer ist vom [ItemsPanel](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemspanel.aspx) des Steuerelements abhängig.</span><span class="sxs-lookup"><span data-stu-id="d59f3-179">How these item containers are laid out depends on the [ItemsPanel](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemspanel.aspx) of the control.</span></span>  
- <span data-ttu-id="d59f3-180">Standardmäßig verwendet **ListView** ein [ItemsStackPanel](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemsstackpanel.aspx), das eine vertikale Liste wie diese erzeugt.</span><span class="sxs-lookup"><span data-stu-id="d59f3-180">By default, **ListView** uses an [ItemsStackPanel](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemsstackpanel.aspx), which produces a vertical list, like this.</span></span>

![Eine einfache Listenansicht](images/listview-simple.png)

- <span data-ttu-id="d59f3-182">**GridView** verwendet ein [ItemsWrapGrid](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemswrapgrid.aspx), das Elemente horizontal hinzufügt, diese anschließend umbricht und einen vertikalen Bildlauf ausführt, wie hier gezeigt.</span><span class="sxs-lookup"><span data-stu-id="d59f3-182">**GridView** uses an [ItemsWrapGrid](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemswrapgrid.aspx), which adds items horizontally, and wraps and scrolls vertically, like this.</span></span>

![Eine einfache Rasteransicht](images/gridview-simple.png)

<span data-ttu-id="d59f3-184">Sie können das Layout von Elementen ändern, indem Sie Eigenschaften im Elementpanel anpassen oder das Standardpanel durch ein anderes Panel ersetzen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-184">You can modify the layout of items by adjusting properties on the items panel, or you can replace the default panel with another panel.</span></span>

> <span data-ttu-id="d59f3-185">Hinweis&nbsp;&nbsp;Achten Sie darauf, dass Sie keine Virtualisierung deaktivieren, wenn Sie ItemsPanel ändern.</span><span class="sxs-lookup"><span data-stu-id="d59f3-185">Note&nbsp;&nbsp;Be careful to not disable virtualization if you change the ItemsPanel.</span></span> <span data-ttu-id="d59f3-186">Sowohl **ItemsStackPanel** als auch **ItemsWrapGrid** unterstützen Virtualisierung, damit diese sicher verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="d59f3-186">Both **ItemsStackPanel** and **ItemsWrapGrid** support virtualization, so these are safe to use.</span></span> <span data-ttu-id="d59f3-187">Wenn Sie ein anderes Panel verwenden, könnten Sie die Virtualisierung deaktivieren und die Leistung der Listenansicht beeinträchtigen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-187">If you use any other panel, you might disable virtualization and slow the performance of the list view.</span></span> <span data-ttu-id="d59f3-188">Weitere Informationen finden Sie in den Artikeln zur Listenansicht unter [Leistung](https://msdn.microsoft.com/windows/uwp/debug-test-perf/performance-and-xaml-ui).</span><span class="sxs-lookup"><span data-stu-id="d59f3-188">For more info, see the list view articles under [Performance](https://msdn.microsoft.com/windows/uwp/debug-test-perf/performance-and-xaml-ui).</span></span> 

<span data-ttu-id="d59f3-189">In diesem Beispiel wird gezeigt, wie eine **ListView** ihre Elementcontainer in einer horizontalen Liste anordnet, indem die [Orientation](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemsstackpanel.orientation.aspx)-Eigenschaft von **ItemsStackPanel** geändert wird.</span><span class="sxs-lookup"><span data-stu-id="d59f3-189">This example shows how to make a **ListView** lay out its item containers in a horizontal list by changing the [Orientation](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemsstackpanel.orientation.aspx) property of the **ItemsStackPanel**.</span></span>
<span data-ttu-id="d59f3-190">Da die Listenansicht standardmäßig den vertikalen Bildlauf verwendet, müssen Sie auch einige Eigenschaften im internen [ScrollViewer](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.aspx) der Listenansicht anpassen, damit der Bildlauf horizontal durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="d59f3-190">Because the list view scrolls vertically by default, you also need to adjust some properties on the list view’s internal [ScrollViewer](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.aspx) to make it scroll horizontally.</span></span>
- <span data-ttu-id="d59f3-191">[ScrollViewer.HorizontalScrollMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.horizontalscrollmode.aspx) zu **Enabled** oder **Auto**</span><span class="sxs-lookup"><span data-stu-id="d59f3-191">[ScrollViewer.HorizontalScrollMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.horizontalscrollmode.aspx) to **Enabled** or **Auto**</span></span>
- <span data-ttu-id="d59f3-192">[ScrollViewer.HorizontalScrollBarVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.horizontalscrollbarvisibility.aspx) zu **Auto**</span><span class="sxs-lookup"><span data-stu-id="d59f3-192">[ScrollViewer.HorizontalScrollBarVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.horizontalscrollbarvisibility.aspx) to **Auto**</span></span> 
- <span data-ttu-id="d59f3-193">[ScrollViewer.VerticalScrollMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.verticalscrollmode.aspx) zu **Disabled**</span><span class="sxs-lookup"><span data-stu-id="d59f3-193">[ScrollViewer.VerticalScrollMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.verticalscrollmode.aspx) to **Disabled**</span></span> 
- <span data-ttu-id="d59f3-194">[ScrollViewer.VerticalScrollBarVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.verticalscrollbarvisibility.aspx) zu **Hidden**</span><span class="sxs-lookup"><span data-stu-id="d59f3-194">[ScrollViewer.VerticalScrollBarVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.verticalscrollbarvisibility.aspx) to **Hidden**</span></span> 

> <span data-ttu-id="d59f3-195">**Hinweis**&nbsp;&nbsp;Diese Beispiele werden mit unbeschränkter Breite der Listenansicht gezeigt, sodass die horizontalen Bildlaufleisten nicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d59f3-195">**Note**&nbsp;&nbsp;These examples are shown with the list view width unconstrained, so the horizontal scrollbars are not shown.</span></span> <span data-ttu-id="d59f3-196">Wenn Sie diesen Code ausführen, können Sie für ListView `Width="180"` festlegen, um die Bildlaufleisten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-196">If you run this code, you can set `Width="180"` on the ListView to make the scrollbars show.</span></span>

**<span data-ttu-id="d59f3-197">XAML</span><span class="sxs-lookup"><span data-stu-id="d59f3-197">XAML</span></span>**
```xaml
<ListView Height="60" 
          ScrollViewer.HorizontalScrollMode="Enabled" 
          ScrollViewer.HorizontalScrollBarVisibility="Auto"
          ScrollViewer.VerticalScrollMode="Disabled"
          ScrollViewer.VerticalScrollBarVisibility="Hidden">
    <ListView.ItemsPanel>
        <ItemsPanelTemplate>
            <ItemsStackPanel Orientation="Horizontal"/>
        </ItemsPanelTemplate>
    </ListView.ItemsPanel>
    <x:String>Item 1</x:String>
    <x:String>Item 2</x:String>
    <x:String>Item 3</x:String>
    <x:String>Item 4</x:String>
    <x:String>Item 5</x:String>
</ListView>
```

<span data-ttu-id="d59f3-198">Die resultierende Liste sieht wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="d59f3-198">The resulting list looks like this.</span></span>

![Eine horizontale Listenansicht](images/listview-horizontal.png)

 <span data-ttu-id="d59f3-200">Im nächsten Beispiel ordnet **ListView** Elemente in einer Liste an, die vertikal umbrochen wird, indem **ItemsWrapGrid** anstelle von **ItemsStackPanel** verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d59f3-200">In the next example, the **ListView** lays out items in a vertical wrapping list by using an **ItemsWrapGrid** instead of an **ItemsStackPanel**.</span></span> 
 
> <span data-ttu-id="d59f3-201">**Note**&nbsp;&nbsp;Die Höhe der Listeneinsicht muss eingeschränkt werden, um das Steuerelement zu zwingen, die Container umzubrechen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-201">**Note**&nbsp;&nbsp;The height of the list view must be constrained to force the control to wrap the containers.</span></span>

**<span data-ttu-id="d59f3-202">XAML</span><span class="sxs-lookup"><span data-stu-id="d59f3-202">XAML</span></span>**
```xaml
<ListView Height="100"
          ScrollViewer.HorizontalScrollMode="Enabled" 
          ScrollViewer.HorizontalScrollBarVisibility="Auto"
          ScrollViewer.VerticalScrollMode="Disabled"
          ScrollViewer.VerticalScrollBarVisibility="Hidden">
    <ListView.ItemsPanel>
        <ItemsPanelTemplate>
            <ItemsWrapGrid/>
        </ItemsPanelTemplate>
    </ListView.ItemsPanel>
    <x:String>Item 1</x:String>
    <x:String>Item 2</x:String>
    <x:String>Item 3</x:String>
    <x:String>Item 4</x:String>
    <x:String>Item 5</x:String>
</ListView>
```

<span data-ttu-id="d59f3-203">Die resultierende Liste sieht wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="d59f3-203">The resulting list looks like this.</span></span>

![Eine Listenansicht mit Rasterlayout](images/listview-itemswrapgrid.png)

<span data-ttu-id="d59f3-205">Wenn Sie in Ihrer Listenansicht gruppierte Daten anzeigen möchten, bestimmt ItemsPanel die Anordnung der Elementgruppen, nicht die Anordnung der einzelnen Elemente. Wenn das horizontale ItemsStackPanel, das zuvor gezeigt wurde, zur Anzeige gruppierter Daten verwendet wird, werden die Gruppen horizontal angeordnet. Die Elemente in den einzelnen Gruppen werden jedoch weiterhin vertikal angeordnet, wie hier gezeigt.</span><span class="sxs-lookup"><span data-stu-id="d59f3-205">If you show grouped data in your list view, the ItemsPanel determines how the item groups are layed out, not how the individual items are layed out. For example, if the horizontal ItemsStackPanel shown previously is used to show grouped data, the groups are arranged horizontally, but the items in each group are still stacked vertically, as shown here.</span></span>

![Eine gruppierte horizontale Listenansicht](images/listview-horizontal-groups.png)

## <a name="item-selection-and-interaction"></a><span data-ttu-id="d59f3-207">Auswahl von Elementen und Interaktion</span><span class="sxs-lookup"><span data-stu-id="d59f3-207">Item selection and interaction</span></span>

<span data-ttu-id="d59f3-208">Sie können aus verschiedenen Möglichkeiten wählen, wie Benutzer mit einer Listenansicht interagieren können.</span><span class="sxs-lookup"><span data-stu-id="d59f3-208">You can choose from various ways to let a user interact with a list view.</span></span> <span data-ttu-id="d59f3-209">Standardmäßig können Benutzer ein einzelnes Element auswählen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-209">By default, a user can select a single item.</span></span> <span data-ttu-id="d59f3-210">Sie können die [SelectionMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.selectionmode.aspx)-Eigenschaft ändern, um eine Mehrfachauswahl zu ermöglichen oder die Auswahl zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="d59f3-210">You can change the [SelectionMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.selectionmode.aspx) property to enable multi-selection or to disable selection.</span></span> <span data-ttu-id="d59f3-211">Sie können die Eigenschaft [IsItemClickEnabled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.isitemclickenabled.aspx) festlegen, sodass ein Benutzer auf ein Element klickt, um eine Aktion aufzurufen (wie bei einer Schaltfläche), statt das Element auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-211">You can set the [IsItemClickEnabled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.isitemclickenabled.aspx) property so that a user clicks an item to invoke an action (like a button) instead of selecting the item.</span></span>

> <span data-ttu-id="d59f3-212">**Hinweis**&nbsp;&nbsp;Sowohl ListView als auch GridView verwenden für ihre SelectionMode-Eigenschaften die [ListViewSelectionMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewselectionmode.aspx)-Enumeration.</span><span class="sxs-lookup"><span data-stu-id="d59f3-212">**Note**&nbsp;&nbsp;Both ListView and GridView use the [ListViewSelectionMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewselectionmode.aspx) enumeration for their SelectionMode properties.</span></span> <span data-ttu-id="d59f3-213">IsItemClickEnabled ist standardmäßig **False**. Daher müssen Sie es lediglich festlegen, um den Klickmodus zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="d59f3-213">IsItemClickEnabled is **False** by default, so you need to set it only to enable click mode.</span></span>

<span data-ttu-id="d59f3-214">In der folgenden Tabelle werden die Arten gezeigt, wie Benutzer mit einer Listenansicht interagieren können und wie Sie auf die jeweilige Interaktion reagieren können.</span><span class="sxs-lookup"><span data-stu-id="d59f3-214">This table shows the ways a user can interact with a list view, and how you can respond to the interaction.</span></span>

<span data-ttu-id="d59f3-215">Um diese Interaktion zu ermöglichen:</span><span class="sxs-lookup"><span data-stu-id="d59f3-215">To enable this interaction:</span></span> | <span data-ttu-id="d59f3-216">Verwenden Sie diese Einstellungen:</span><span class="sxs-lookup"><span data-stu-id="d59f3-216">Use these settings:</span></span> | <span data-ttu-id="d59f3-217">Behandeln Sie dieses Ereignis:</span><span class="sxs-lookup"><span data-stu-id="d59f3-217">Handle this event:</span></span> | <span data-ttu-id="d59f3-218">Verwenden Sie diese Eigenschaft zum Abrufen des ausgewählten Elements:</span><span class="sxs-lookup"><span data-stu-id="d59f3-218">Use this property to get the selected item:</span></span>
----------------------------|---------------------|--------------------|--------------------------------------------
<span data-ttu-id="d59f3-219">Keine Interaktion</span><span class="sxs-lookup"><span data-stu-id="d59f3-219">No interaction</span></span> | <span data-ttu-id="d59f3-220">[SelectionMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.selectionmode.aspx) = **None**, [IsItemClickEnabled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.isitemclickenabled.aspx) = **False**</span><span class="sxs-lookup"><span data-stu-id="d59f3-220">[SelectionMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.selectionmode.aspx) = **None**, [IsItemClickEnabled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.isitemclickenabled.aspx) = **False**</span></span> | <span data-ttu-id="d59f3-221">Nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="d59f3-221">N/A</span></span> | <span data-ttu-id="d59f3-222">Nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="d59f3-222">N/A</span></span> 
<span data-ttu-id="d59f3-223">Einzelauswahl</span><span class="sxs-lookup"><span data-stu-id="d59f3-223">Single selection</span></span> | <span data-ttu-id="d59f3-224">SelectionMode = **Single**, IsItemClickEnabled = **False**</span><span class="sxs-lookup"><span data-stu-id="d59f3-224">SelectionMode = **Single**, IsItemClickEnabled = **False**</span></span> | [<span data-ttu-id="d59f3-225">SelectionChanged</span><span class="sxs-lookup"><span data-stu-id="d59f3-225">SelectionChanged</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.selector.selectionchanged.aspx) | <span data-ttu-id="d59f3-226">[SelectedItem](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.selector.selecteditem.aspx), [SelectedIndex](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.selector.selectedindex.aspx)</span><span class="sxs-lookup"><span data-stu-id="d59f3-226">[SelectedItem](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.selector.selecteditem.aspx), [SelectedIndex](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.selector.selectedindex.aspx)</span></span>  
<span data-ttu-id="d59f3-227">Mehrfachauswahl</span><span class="sxs-lookup"><span data-stu-id="d59f3-227">Multiple selection</span></span> | <span data-ttu-id="d59f3-228">SelectionMode = **Multiple**, IsItemClickEnabled = **False**</span><span class="sxs-lookup"><span data-stu-id="d59f3-228">SelectionMode = **Multiple**, IsItemClickEnabled = **False**</span></span> | [<span data-ttu-id="d59f3-229">SelectionChanged</span><span class="sxs-lookup"><span data-stu-id="d59f3-229">SelectionChanged</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.selector.selectionchanged.aspx) | [<span data-ttu-id="d59f3-230">SelectedItems</span><span class="sxs-lookup"><span data-stu-id="d59f3-230">SelectedItems</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.selecteditems.aspx)  
<span data-ttu-id="d59f3-231">Erweiterte Auswahl</span><span class="sxs-lookup"><span data-stu-id="d59f3-231">Extended selection</span></span> | <span data-ttu-id="d59f3-232">SelectionMode = **Extended**, IsItemClickEnabled = **False**</span><span class="sxs-lookup"><span data-stu-id="d59f3-232">SelectionMode = **Extended**, IsItemClickEnabled = **False**</span></span> | [<span data-ttu-id="d59f3-233">SelectionChanged</span><span class="sxs-lookup"><span data-stu-id="d59f3-233">SelectionChanged</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.selector.selectionchanged.aspx) | [<span data-ttu-id="d59f3-234">SelectedItems</span><span class="sxs-lookup"><span data-stu-id="d59f3-234">SelectedItems</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.selecteditems.aspx)  
<span data-ttu-id="d59f3-235">Klicken</span><span class="sxs-lookup"><span data-stu-id="d59f3-235">Click</span></span> | <span data-ttu-id="d59f3-236">SelectionMode = **None**, IsItemClickEnabled = **True**</span><span class="sxs-lookup"><span data-stu-id="d59f3-236">SelectionMode = **None**, IsItemClickEnabled = **True**</span></span> | [<span data-ttu-id="d59f3-237">ItemClick</span><span class="sxs-lookup"><span data-stu-id="d59f3-237">ItemClick</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.itemclick.aspx) | <span data-ttu-id="d59f3-238">Nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="d59f3-238">N/A</span></span> 

> <span data-ttu-id="d59f3-239">**Hinweis**&nbsp;&nbsp;Ab Windows10 können Sie IsItemClickEnabled aktivieren, um ein ItemClick-Ereignis auszulösen, während SelectionMode ebenfalls auf Single, Multiple oder Extended festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="d59f3-239">**Note**&nbsp;&nbsp;Starting in Windows 10, you can enable IsItemClickEnabled to raise an ItemClick event while SelectionMode is also set to Single, Multiple, or Extended.</span></span> <span data-ttu-id="d59f3-240">Wenn Sie dies tun, wird zuerst das ItemClick-Ereignis und anschließend das SelectionChanged-Ereignis ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="d59f3-240">If you do this, the ItemClick event is raised first, and then the SelectionChanged event is raised.</span></span> <span data-ttu-id="d59f3-241">In einigen Fällen, wenn Sie beispielsweise zu einer anderen Seite im ItemClick-Ereignishandler navigieren, wird das SelectionChanged-Ereignis nicht ausgelöst, und das Element wird nicht ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="d59f3-241">In some cases, like if you navigate to another page in the ItemClick event handler, the SelectionChanged event is not raised and the item is not selected.</span></span>

<span data-ttu-id="d59f3-242">Sie können diese Eigenschaften in XAML oder im Code festlegen, wie hier gezeigt.</span><span class="sxs-lookup"><span data-stu-id="d59f3-242">You can set these properties in XAML or in code, as shown here.</span></span>

**<span data-ttu-id="d59f3-243">XAML</span><span class="sxs-lookup"><span data-stu-id="d59f3-243">XAML</span></span>**
```xaml
<ListView x:Name="myListView" SelectionMode="Multiple"/>

<GridView x:Name="myGridView" SelectionMode="None" IsItemClickEnabled="True"/> 
```

**<span data-ttu-id="d59f3-244">C#</span><span class="sxs-lookup"><span data-stu-id="d59f3-244">C#</span></span>**
```csharp
myListView.SelectionMode = ListViewSelectionMode.Multiple; 

myGridView.SelectionMode = ListViewSelectionMode.None;
myGridView.IsItemClickEnabled = true;
```

### <a name="read-only"></a><span data-ttu-id="d59f3-245">Schreibgeschützt</span><span class="sxs-lookup"><span data-stu-id="d59f3-245">Read-only</span></span>

<span data-ttu-id="d59f3-246">Sie können die Eigenschaft SelectionMode auf **ListViewSelectionMode.None** festlegen, um die Elementauswahl zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="d59f3-246">You can set the SelectionMode property to **ListViewSelectionMode.None** to disable item selection.</span></span> <span data-ttu-id="d59f3-247">Dadurch wird das Steuerelement im schreibgeschützten Modus ausgeführt und kann zwar zum Anzeigen von Daten, nicht jedoch für die Interaktion mit ihm verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="d59f3-247">This puts the control in read only mode, to be used for displaying data, but not for interacting with it.</span></span> <span data-ttu-id="d59f3-248">Das Steuerelement selbst ist nicht deaktiviert ist, nur die Elementauswahl ist deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="d59f3-248">The control itself is not disabled, only item selection is disabled.</span></span>

### <a name="single-selection"></a><span data-ttu-id="d59f3-249">Einzelauswahl</span><span class="sxs-lookup"><span data-stu-id="d59f3-249">Single selection</span></span>

<span data-ttu-id="d59f3-250">In der folgenden Tabelle werden die Tastatur-, Maus- und Touchinteraktionen beschrieben, wenn SelectionMode **Single** ist.</span><span class="sxs-lookup"><span data-stu-id="d59f3-250">This table describes the keyboard, mouse, and touch interactions when SelectionMode is **Single**.</span></span>

<span data-ttu-id="d59f3-251">Zusatztaste</span><span class="sxs-lookup"><span data-stu-id="d59f3-251">Modifier key</span></span> | <span data-ttu-id="d59f3-252">Interaktion</span><span class="sxs-lookup"><span data-stu-id="d59f3-252">Interaction</span></span>
-------------|------------
<span data-ttu-id="d59f3-253">Keine</span><span class="sxs-lookup"><span data-stu-id="d59f3-253">None</span></span> | <li><span data-ttu-id="d59f3-254">Ein Benutzer kann ein einzelnes Element mit der LEERTASTE, per Mausklick oder durch Tippen auswählen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-254">A user can select a single item using the space bar, mouse click, or touch tap.</span></span></li>
<span data-ttu-id="d59f3-255">STRG</span><span class="sxs-lookup"><span data-stu-id="d59f3-255">Ctrl</span></span> | <li><span data-ttu-id="d59f3-256">Ein Benutzer kann die Auswahl eines einzelnen Elements mit der LEERTASTE, per Mausklick oder durch Tippen aufheben.</span><span class="sxs-lookup"><span data-stu-id="d59f3-256">A user can deselect a single item using the space bar, mouse click, or touch tap.</span></span></li><li><span data-ttu-id="d59f3-257">Mit den Pfeiltasten kann ein Benutzer den Fokus unabhängig von der Auswahl verschieben.</span><span class="sxs-lookup"><span data-stu-id="d59f3-257">Using the arrow keys, a user can move focus independently of selection.</span></span></li>

<span data-ttu-id="d59f3-258">Wenn der SelectionMode auf **Single** eingestellt ist, erhalten Sie das ausgewählte Datenelement über die [SelectedItem](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.selector.selecteditem.aspx)-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="d59f3-258">When SelectionMode is **Single**, you can get the selected data item from the [SelectedItem](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.selector.selecteditem.aspx) property.</span></span> <span data-ttu-id="d59f3-259">Den Index der Sammlung des ausgewählten Elements erhalten Sie mithilfe der [SelectedIndex](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.selector.selectedindex.aspx)-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="d59f3-259">You can get the index in the collection of the selected item using the [SelectedIndex](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.selector.selectedindex.aspx) property.</span></span> <span data-ttu-id="d59f3-260">Wenn kein Element ausgewählt ist, ist SelectedItem **null**, und SelectedIndex ist -1.</span><span class="sxs-lookup"><span data-stu-id="d59f3-260">If no item is selected, SelectedItem is **null**, and SelectedIndex is -1.</span></span> 
 
<span data-ttu-id="d59f3-261">Wenn Sie versuchen, ein Element festzulegen, das nicht in der **Items**-Sammlung enthalten ist, wird der Vorgang ignoriert, und **SelectedItem** ist **null**.</span><span class="sxs-lookup"><span data-stu-id="d59f3-261">If you try to set an item that is not in the **Items** collection as the **SelectedItem**, the operation is ignored and SelectedItem is**null**.</span></span> <span data-ttu-id="d59f3-262">Wenn Sie jedoch versuchen, **SelectedIndex** auf einen Index festzulegen, die außerhalb des Bereichs der **Items** in der Liste ist, wird eine **System.ArgumentException**-Ausnahme ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="d59f3-262">However, if you try to set the **SelectedIndex** to an index that's out of the range of the **Items** in the list, a **System.ArgumentException** exception occurs.</span></span> 

### <a name="multiple-selection"></a><span data-ttu-id="d59f3-263">Mehrfachauswahl</span><span class="sxs-lookup"><span data-stu-id="d59f3-263">Multiple selection</span></span>

<span data-ttu-id="d59f3-264">In der folgenden Tabelle werden die Tastatur-, Maus- und Touchinteraktionen beschrieben, wenn SelectionMode **Multiple** ist.</span><span class="sxs-lookup"><span data-stu-id="d59f3-264">This table describes the keyboard, mouse, and touch interactions when SelectionMode is **Multiple**.</span></span>

<span data-ttu-id="d59f3-265">Zusatztaste</span><span class="sxs-lookup"><span data-stu-id="d59f3-265">Modifier key</span></span> | <span data-ttu-id="d59f3-266">Interaktion</span><span class="sxs-lookup"><span data-stu-id="d59f3-266">Interaction</span></span>
-------------|------------
<span data-ttu-id="d59f3-267">Keine</span><span class="sxs-lookup"><span data-stu-id="d59f3-267">None</span></span> | <li><span data-ttu-id="d59f3-268">Ein Benutzer kann mehrerer Objekte mit der LEERTASTE, per Mausklick oder durch Tippen auswählen, um die Auswahl zum fokussierten Element zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="d59f3-268">A user can select multiple items using the space bar, mouse click, or touch tap to toggle selection on the focused item.</span></span></li><li><span data-ttu-id="d59f3-269">Mit den Pfeiltasten kann ein Benutzer den Fokus unabhängig von der Auswahl verschieben.</span><span class="sxs-lookup"><span data-stu-id="d59f3-269">Using the arrow keys, a user can move focus independently of selection.</span></span></li>
<span data-ttu-id="d59f3-270">UMSCHALTTASTE</span><span class="sxs-lookup"><span data-stu-id="d59f3-270">Shift</span></span> | <li><span data-ttu-id="d59f3-271">Benutzer können mehrere zusammenhängende Elemente auswählen, indem sie auf das erste Element in der Auswahl und anschließend auf das letzte Element in der Auswahl klicken oder tippen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-271">A user can select multiple contiguous items by clicking or tapping the first item in the selection and then the last item in the selection.</span></span></li><li><span data-ttu-id="d59f3-272">Mit den Pfeiltasten können Benutzer eine zusammenhängende Auswahl beginnend mit dem ausgewählten Element erstellen, wenn die UMSCHALTTASTE gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="d59f3-272">Using the arrow keys, a user can create a contiguous selection starting with the item selected when Shift is pressed.</span></span></li>

### <a name="extended-selection"></a><span data-ttu-id="d59f3-273">Erweiterte Auswahl</span><span class="sxs-lookup"><span data-stu-id="d59f3-273">Extended selection</span></span>

<span data-ttu-id="d59f3-274">In der folgenden Tabelle werden die Tastatur-, Maus- und Touchinteraktionen beschrieben, wenn SelectionMode **Extended** ist.</span><span class="sxs-lookup"><span data-stu-id="d59f3-274">This table describes the keyboard, mouse, and touch interactions when SelectionMode is **Extended**.</span></span>

<span data-ttu-id="d59f3-275">Zusatztaste</span><span class="sxs-lookup"><span data-stu-id="d59f3-275">Modifier key</span></span> | <span data-ttu-id="d59f3-276">Interaktion</span><span class="sxs-lookup"><span data-stu-id="d59f3-276">Interaction</span></span>
-------------|------------
<span data-ttu-id="d59f3-277">Keine</span><span class="sxs-lookup"><span data-stu-id="d59f3-277">None</span></span> | <li><span data-ttu-id="d59f3-278">Das Verhalten ist mit der Auswahl **Single** identisch.</span><span class="sxs-lookup"><span data-stu-id="d59f3-278">The behavior is the same as **Single** selection.</span></span></li>
<span data-ttu-id="d59f3-279">STRG</span><span class="sxs-lookup"><span data-stu-id="d59f3-279">Ctrl</span></span> | <li><span data-ttu-id="d59f3-280">Ein Benutzer kann mehrerer Objekte mit der LEERTASTE, per Mausklick oder durch Tippen auswählen, um die Auswahl zum fokussierten Element zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="d59f3-280">A user can select multiple items using the space bar, mouse click, or touch tap to toggle selection on the focused item.</span></span></li><li><span data-ttu-id="d59f3-281">Mit den Pfeiltasten kann ein Benutzer den Fokus unabhängig von der Auswahl verschieben.</span><span class="sxs-lookup"><span data-stu-id="d59f3-281">Using the arrow keys, a user can move focus independently of selection.</span></span></li>
<span data-ttu-id="d59f3-282">UMSCHALTTASTE</span><span class="sxs-lookup"><span data-stu-id="d59f3-282">Shift</span></span> | <li><span data-ttu-id="d59f3-283">Benutzer können mehrere zusammenhängende Elemente auswählen, indem sie auf das erste Element in der Auswahl und anschließend auf das letzte Element in der Auswahl klicken oder tippen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-283">A user can select multiple contiguous items by clicking or tapping the first item in the selection and then the last item in the selection.</span></span></li><li><span data-ttu-id="d59f3-284">Mit den Pfeiltasten können Benutzer eine zusammenhängende Auswahl beginnend mit dem ausgewählten Element erstellen, wenn die UMSCHALTTASTE gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="d59f3-284">Using the arrow keys, a user can create a contiguous selection starting with the item selected when Shift is pressed.</span></span></li>

<span data-ttu-id="d59f3-285">Wenn der SelectionMode auf **Multiple** oder **Extended** eingestellt ist, erhalten Sie die ausgewählten Datenelemente über die [SelectedItems](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.selecteditems.aspx)-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="d59f3-285">When SelectionMode is **Multiple** or **Extended**, you can get the selected data items from the [SelectedItems](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.selecteditems.aspx) property.</span></span> 

<span data-ttu-id="d59f3-286">Die Eigenschaften **SelectedIndex**, **SelectedItem** und **SelectedItems** sind synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="d59f3-286">The **SelectedIndex**, **SelectedItem**, and **SelectedItems** properties are synchronized.</span></span> <span data-ttu-id="d59f3-287">Wenn Sie beispielsweise SelectedIndex auf-1 festlegen, wird SelectedItem auf **null** festgelegt und SelectedItems ist leer. Wenn Sie SelectedItem auf **null** festlegen, wird SelectedIndex auf-1 festgelegt und SelectedItems ist leer.</span><span class="sxs-lookup"><span data-stu-id="d59f3-287">For example, if you set SelectedIndex to -1, SelectedItem is set to **null** and SelectedItems is empty; if you set SelectedItem to **null**, SelectedIndex is set to -1 and SelectedItems is empty.</span></span>

<span data-ttu-id="d59f3-288">Im Mehrfachauswahlmodus enthält **SelectedItem** das Element, das zuerst ausgewählt wurde, und **Selectedindex** enthält den Index des Elements, das zuerst ausgewählt wurde.</span><span class="sxs-lookup"><span data-stu-id="d59f3-288">In multi-select mode, **SelectedItem** contains the item that was selected first, and **Selectedindex** contains the index of the item that was selected first.</span></span> 

### <a name="respond-to-selection-changes"></a><span data-ttu-id="d59f3-289">Reagieren auf Änderungen der Auswahl</span><span class="sxs-lookup"><span data-stu-id="d59f3-289">Respond to selection changes</span></span>

<span data-ttu-id="d59f3-290">Um auf Änderungen der Auswahl in einer Listenansicht zu reagieren, müssen Sie das [SelectionChanged](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.selector.selectionchanged.aspx)-Event bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="d59f3-290">To respond to selection changes in a list view, handle the [SelectionChanged](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.selector.selectionchanged.aspx) event.</span></span> <span data-ttu-id="d59f3-291">Im Code des Ereignis-Handlers können Sie die Liste der ausgewählten Elemente über die [SelectionChangedEventArgs.AddedItems](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.selectionchangedeventargs.addeditems.aspx)-Eigenschaft abrufen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-291">In the event handler code, you can get the list of selected items from the [SelectionChangedEventArgs.AddedItems](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.selectionchangedeventargs.addeditems.aspx) property.</span></span> <span data-ttu-id="d59f3-292">Sie können alle Elemente abrufen, deren Auswahl über die [SelectionChangedEventArgs.RemovedItems](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.selectionchangedeventargs.removeditems.aspx)-Eigenschaft aufgehoben wurde.</span><span class="sxs-lookup"><span data-stu-id="d59f3-292">You can get any items that were deselected from the [SelectionChangedEventArgs.RemovedItems](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.selectionchangedeventargs.removeditems.aspx) property.</span></span> <span data-ttu-id="d59f3-293">Die AddedItems- und RemovedItems-Sammlungen enthalten höchstens 1 Element, wenn der Benutzer keinen Bereich von Elementen auswählt, indem er die UMSCHALTTASTE gedrückt hält.</span><span class="sxs-lookup"><span data-stu-id="d59f3-293">The AddedItems and RemovedItems collections contain at most 1 item unless the user selects a range of items by holding down the Shift key.</span></span>

<span data-ttu-id="d59f3-294">In diesem Beispiel werden die Behandlung des **SelectionChanged**-Ereignisses und der Zugriff auf die verschiedenen Elementsammlungen gezeigt.</span><span class="sxs-lookup"><span data-stu-id="d59f3-294">This example shows how to handle the **SelectionChanged** event and access the various items collections.</span></span>

**<span data-ttu-id="d59f3-295">XAML</span><span class="sxs-lookup"><span data-stu-id="d59f3-295">XAML</span></span>**
```xaml
<StackPanel HorizontalAlignment="Right">
    <ListView x:Name="listView1" SelectionMode="Multiple" 
              SelectionChanged="ListView1_SelectionChanged">
        <x:String>Item 1</x:String>
        <x:String>Item 2</x:String>
        <x:String>Item 3</x:String>
        <x:String>Item 4</x:String>
        <x:String>Item 5</x:String>
    </ListView>
    <TextBlock x:Name="selectedItem"/>
    <TextBlock x:Name="selectedIndex"/>
    <TextBlock x:Name="selectedItemCount"/>
    <TextBlock x:Name="addedItems"/>
    <TextBlock x:Name="removedItems"/>
</StackPanel> 
```

**<span data-ttu-id="d59f3-296">C#</span><span class="sxs-lookup"><span data-stu-id="d59f3-296">C#</span></span>**
```csharp
private void ListView1_SelectionChanged(object sender, SelectionChangedEventArgs e)
{
    if (listView1.SelectedItem != null)
    {
        selectedItem.Text = 
            "Selected item: " + listView1.SelectedItem.ToString();
    }
    else
    {
        selectedItem.Text = 
            "Selected item: null";
    }
    selectedIndex.Text = 
        "Selected index: " + listView1.SelectedIndex.ToString();
    selectedItemCount.Text = 
        "Items selected: " + listView1.SelectedItems.Count.ToString();
    addedItems.Text = 
        "Added: " + e.AddedItems.Count.ToString();
    removedItems.Text = 
        "Removed: " + e.RemovedItems.Count.ToString();
}
```

### <a name="click-mode"></a><span data-ttu-id="d59f3-297">Klickmodus</span><span class="sxs-lookup"><span data-stu-id="d59f3-297">Click mode</span></span>

<span data-ttu-id="d59f3-298">Sie können eine Listenansicht so ändern, dass die Benutzer auf die Elemente wie auf Schaltflächen klicken, anstatt sie auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-298">You can change a list view so that a user clicks items like buttons instead of selecting them.</span></span> <span data-ttu-id="d59f3-299">Das bietet sich z.B. an, wenn Ihre App zu einer neuen Seite navigieren soll, wenn ein Benutzer auf ein Element in der Liste oder im Raster klickt.</span><span class="sxs-lookup"><span data-stu-id="d59f3-299">For example, this is useful when your app navigates to a new page when your user clicks an item in a list or grid.</span></span> <span data-ttu-id="d59f3-300">So aktivieren Sie dieses Verhalten</span><span class="sxs-lookup"><span data-stu-id="d59f3-300">To enable this behavior:</span></span>
- <span data-ttu-id="d59f3-301">Legen Sie **SelectionMode** auf **None** fest.</span><span class="sxs-lookup"><span data-stu-id="d59f3-301">Set **SelectionMode** to **None**.</span></span>
- <span data-ttu-id="d59f3-302">Legen Sie **IsItemClickEnabled** auf **true** fest.</span><span class="sxs-lookup"><span data-stu-id="d59f3-302">Set **IsItemClickEnabled** to **true**.</span></span>
- <span data-ttu-id="d59f3-303">Behandeln Sie das **ItemClick**-Ereignis, um eine Aktion auszuführen, wenn der Benutzer auf ein Element klickt.</span><span class="sxs-lookup"><span data-stu-id="d59f3-303">Handle the **ItemClick** event to do something when your user clicks an item.</span></span>

<span data-ttu-id="d59f3-304">Dies ist eine Listenansicht mit Elementen, auf die geklickt werden kann.</span><span class="sxs-lookup"><span data-stu-id="d59f3-304">Here's a list view with clickable items.</span></span> <span data-ttu-id="d59f3-305">Der Code im Ereignishandler ItemClick navigiert zu einer neuen Seite.</span><span class="sxs-lookup"><span data-stu-id="d59f3-305">The code in the ItemClick event handler navigates to a new page.</span></span>

**<span data-ttu-id="d59f3-306">XAML</span><span class="sxs-lookup"><span data-stu-id="d59f3-306">XAML</span></span>**
```xaml
<ListView SelectionMode="None"
          IsItemClickEnabled="True" 
          ItemClick="ListView1_ItemClick">
    <x:String>Page 1</x:String>
    <x:String>Page 2</x:String>
    <x:String>Page 3</x:String>
    <x:String>Page 4</x:String>
    <x:String>Page 5</x:String>
</ListView>
```

**<span data-ttu-id="d59f3-307">C#</span><span class="sxs-lookup"><span data-stu-id="d59f3-307">C#</span></span>**
```csharp
private void ListView1_ItemClick(object sender, ItemClickEventArgs e)
{
    switch (e.ClickedItem.ToString())
    {
        case "Page 1":
            this.Frame.Navigate(typeof(Page1));
            break;

        case "Page 2":
            this.Frame.Navigate(typeof(Page2));
            break;

        case "Page 3":
            this.Frame.Navigate(typeof(Page3));
            break;

        case "Page 4":
            this.Frame.Navigate(typeof(Page4));
            break;

        case "Page 5":
            this.Frame.Navigate(typeof(Page5));
            break;

        default:
            break;
    }
}
```

### <a name="select-a-range-of-items-programmatically"></a><span data-ttu-id="d59f3-308">Programmgesteuerte Auswahl eines Elementbereichs</span><span class="sxs-lookup"><span data-stu-id="d59f3-308">Select a range of items programmatically</span></span>

<span data-ttu-id="d59f3-309">In manchen Fällen müssen Sie die Elementauswahl einer Listenansicht programmgesteuert bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="d59f3-309">Sometimes, you need to manipulate a list view’s item selection programmatically.</span></span> <span data-ttu-id="d59f3-310">Angenommen, es gibt eine Schaltfläche **Alles auswählen**, um einen Benutzer alle Elemente in einer Liste auswählen zu lassen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-310">For example, you might have a **Select all** button to let a user select all items in a list.</span></span> <span data-ttu-id="d59f3-311">In diesem Fall ist es in der Regel nicht sehr effizient, der Sammlung SelectedItems Elemente einzeln hinzuzufügen oder Elemente einzeln aus dieser zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-311">In this case, it’s usually not very efficient to add and remove items from the SelectedItems collection one by one.</span></span> <span data-ttu-id="d59f3-312">Jedes Element führt zu einem SelectionChanged-Ereignis. Wenn Sie direkt mit den Elementen arbeiten und nicht mit Indexwerten, wird die Virtualisierung des betreffenden Elements deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="d59f3-312">Each item change causes a SelectionChanged event to occur, and when you work with the items directly instead of working with index values, the item is de-virtualized.</span></span>

<span data-ttu-id="d59f3-313">Mittels der Methoden [SelectAll](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.selectall.aspx), [SelectRange](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.selectrange.aspx) und [DeselectRange](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.deselectrange.aspx) lässt sich die Auswahl auf effizientere Weise ändern als über die SelectedItems-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="d59f3-313">The [SelectAll](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.selectall.aspx), [SelectRange](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.selectrange.aspx), and [DeselectRange](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.deselectrange.aspx) methods provide a more efficient way to modify the selection than using the SelectedItems property.</span></span> <span data-ttu-id="d59f3-314">Diese Methoden führen mithilfe von Elementindexbereichen Auswahlen durch oder heben Auswahlen auf.</span><span class="sxs-lookup"><span data-stu-id="d59f3-314">These methods select or deselect using ranges of item indexes.</span></span> <span data-ttu-id="d59f3-315">Elemente, die virtualisiert sind, bleiben virtualisiert, da nur der Index verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d59f3-315">Items that are virtualized remain virtualized, because only the index is used.</span></span> <span data-ttu-id="d59f3-316">Alle Elemente im angegebenen Bereich werden ausgewählt (bzw. die Auswahl aller Elemente im angegeben Bereich wird aufgehoben), unabhängig vom ursprünglichen Auswahlzustand.</span><span class="sxs-lookup"><span data-stu-id="d59f3-316">All items in the specified range are selected (or deselected), regardless of their original selection state.</span></span> <span data-ttu-id="d59f3-317">Das SelectionChanged-Ereignis tritt nur einmal für jeden Aufruf dieser Methoden auf.</span><span class="sxs-lookup"><span data-stu-id="d59f3-317">The SelectionChanged event occurs only once for each call to these methods.</span></span>

> <span data-ttu-id="d59f3-318">**Wichtig**&nbsp;&nbsp;Sie sollten diese Methoden nur aufrufen, wenn die SelectionMode-Eigenschaft auf Multiple oder Extended festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="d59f3-318">**Important**&nbsp;&nbsp;You should call these methods only when the SelectionMode property is set to Multiple or Extended.</span></span> <span data-ttu-id="d59f3-319">Wenn Sie SelectRange aufrufen, wenn der Auswahlmodus Single oder None ist, wird eine Ausnahme ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="d59f3-319">If you call SelectRange when the SelectionMode is Single or None, an exception is thrown.</span></span>

<span data-ttu-id="d59f3-320">Verwenden Sie bei der Auswahl von Elementen mit Indexbereichen die [SelectedRanges](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.selectedranges.aspx)-Eigenschaft, um alle ausgewählten Bereiche in der Liste abzurufen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-320">When you select items using index ranges, use the [SelectedRanges](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.selectedranges.aspx) property to get all selected ranges in the list.</span></span>

<span data-ttu-id="d59f3-321">Wenn ItemsSource [IItemsRangeInfo](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.data.iitemsrangeinfo.aspx) implementiert, und Sie diese Methoden verwenden, um die Auswahl zu ändern, werden die Eigenschaften **AddedItems** und **RemovedItems** in SelectionChangedEventArgs nicht festgelegt.</span><span class="sxs-lookup"><span data-stu-id="d59f3-321">If the ItemsSource implements [IItemsRangeInfo](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.data.iitemsrangeinfo.aspx), and you use these methods to modify the selection, the **AddedItems** and **RemovedItems** properties are not set in the SelectionChangedEventArgs.</span></span> <span data-ttu-id="d59f3-322">Das Festlegen dieser Eigenschaften erfordert die Deaktivierung der Virtualisierung des Elementobjekts.</span><span class="sxs-lookup"><span data-stu-id="d59f3-322">Setting these properties requires de-virtualizing the item object.</span></span> <span data-ttu-id="d59f3-323">Verwenden Sie zum Abrufen der Elemente stattdessen die Eigenschaft **SelectedRanges**.</span><span class="sxs-lookup"><span data-stu-id="d59f3-323">Use the **SelectedRanges** property to get the items instead.</span></span>

<span data-ttu-id="d59f3-324">Sie können alle Elemente in einer Sammlung auswählen, indem Sie die SelectAll-Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-324">You can select all items in a collection by calling the SelectAll method.</span></span> <span data-ttu-id="d59f3-325">Es gibt jedoch keine entsprechende Methode, um die Auswahl aller Elemente aufzuheben.</span><span class="sxs-lookup"><span data-stu-id="d59f3-325">However, there is no corresponding method to deselect all items.</span></span> <span data-ttu-id="d59f3-326">Sie können die Auswahl aller Elemente aufheben, indem Sie DeselectRange aufrufen und einen [ItemIndexRange](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.data.itemindexrange.aspx) mit einem Wert für [FirstIndex](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.data.itemindexrange.firstindex.aspx) von 0 und einem Wert für [Length](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.data.itemindexrange.length.aspx) übergeben, der der Anzahl der Elemente in der Sammlung entspricht.</span><span class="sxs-lookup"><span data-stu-id="d59f3-326">You can deselect all items by calling DeselectRange and passing an [ItemIndexRange](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.data.itemindexrange.aspx) with a [FirstIndex](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.data.itemindexrange.firstindex.aspx) value of 0 and a [Length](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.data.itemindexrange.length.aspx) value equal to the number of items in the collection.</span></span> 

**<span data-ttu-id="d59f3-327">XAML</span><span class="sxs-lookup"><span data-stu-id="d59f3-327">XAML</span></span>**
```xaml
<StackPanel Width="160">
    <Button Content="Select all" Click="SelectAllButton_Click"/>
    <Button Content="Deselect all" Click="DeselectAllButton_Click"/>
    <ListView x:Name="listView1" SelectionMode="Multiple">
        <x:String>Item 1</x:String>
        <x:String>Item 2</x:String>
        <x:String>Item 3</x:String>
        <x:String>Item 4</x:String>
        <x:String>Item 5</x:String>
    </ListView>
</StackPanel>
```

**<span data-ttu-id="d59f3-328">C#</span><span class="sxs-lookup"><span data-stu-id="d59f3-328">C#</span></span>**
```csharp
private void SelectAllButton_Click(object sender, RoutedEventArgs e)
{
    if (listView1.SelectionMode == ListViewSelectionMode.Multiple ||
        listView1.SelectionMode == ListViewSelectionMode.Extended)
    {
        listView1.SelectAll();
    }
}

private void DeselectAllButton_Click(object sender, RoutedEventArgs e)
{
    if (listView1.SelectionMode == ListViewSelectionMode.Multiple ||
        listView1.SelectionMode == ListViewSelectionMode.Extended)
    {
        listView1.DeselectRange(new ItemIndexRange(0, (uint)listView1.Items.Count));
    }
}
```

<span data-ttu-id="d59f3-329">Informationen zum Ändern der Darstellung ausgewählter Elemente finden Sie unter [Elementcontainer und Vorlagen](item-containers-templates.md).</span><span class="sxs-lookup"><span data-stu-id="d59f3-329">For info about how to change the look of selected items, see [Item containers and templates](item-containers-templates.md).</span></span>

### <a name="drag-and-drop"></a><span data-ttu-id="d59f3-330">Drag&Drop</span><span class="sxs-lookup"><span data-stu-id="d59f3-330">Drag and drop</span></span>

<span data-ttu-id="d59f3-331">ListView- und GridView-Steuerelemente unterstützen Drag & Drop für Elemente innerhalb von ihnen und zwischen ihnen und anderen ListView- und GridView-Steuerelementen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-331">ListView and GridView controls support drag and drop of items within themselves, and between themselves and other ListView and GridView controls.</span></span> <span data-ttu-id="d59f3-332">Weitere Informationen zur Implementierung des Musters für Drag & Drop finden Sie unter [Drag & Drop](https://msdn.microsoft.com/windows/uwp/design/input/drag-and-drop).</span><span class="sxs-lookup"><span data-stu-id="d59f3-332">For more info about implementing the drag and drop pattern, see [Drag and drop](https://msdn.microsoft.com/windows/uwp/design/input/drag-and-drop).</span></span> 

## <a name="get-the-sample-code"></a><span data-ttu-id="d59f3-333">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="d59f3-333">Get the sample code</span></span>

- <span data-ttu-id="d59f3-334">[XAML-Beispiel für ListView und GridView](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlListView) – Veranschaulicht die ListView- und GridView-Steuerelementen.</span><span class="sxs-lookup"><span data-stu-id="d59f3-334">[XAML ListView and GridView sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlListView) - Demonstrates the ListView and GridView controls.</span></span>
- <span data-ttu-id="d59f3-335">[XAML-Drag&Drop-Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlDragAndDrop) – Veranschaulicht Drag&Drop mit dem ListView-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="d59f3-335">[XAML Drag and drop sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlDragAndDrop) - Demonstrates drag and drop with the ListView control.</span></span>
- <span data-ttu-id="d59f3-336">[Beispiel eines XAML-Steuerelementekatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="d59f3-336">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="d59f3-337">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="d59f3-337">Related articles</span></span>

- [<span data-ttu-id="d59f3-338">Listen</span><span class="sxs-lookup"><span data-stu-id="d59f3-338">Lists</span></span>](lists.md)
- [<span data-ttu-id="d59f3-339">Elementcontainer und Vorlagen</span><span class="sxs-lookup"><span data-stu-id="d59f3-339">Item containers and templates</span></span>](item-containers-templates.md)
- [<span data-ttu-id="d59f3-340">Drag&Drop</span><span class="sxs-lookup"><span data-stu-id="d59f3-340">Drag and drop</span></span>](https://msdn.microsoft.com/windows/uwp/app-to-app/drag-and-drop)
