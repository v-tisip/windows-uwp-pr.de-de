---
Description: Displays images in a collection, such as photos in an album or items in a product details page, one image at a time.
title: Richtlinien für Flip-Ansicht-Steuerelemente
ms.assetid: A4E05D92-1A0E-4CDD-84B9-92199FF8A8A3
label: Flip view
template: detail.hbs
ms.date: 05/19/2017
ms.topic: article
keywords: Windows10, UWP
pm-contact: predavid
design-contact: kimsea
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 9a7fa4b824e0472971fab61935857670fa5b49ee
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8799367"
---
# <a name="flip-view"></a><span data-ttu-id="bbb80-103">Flip-Ansicht</span><span class="sxs-lookup"><span data-stu-id="bbb80-103">Flip view</span></span>

 

<span data-ttu-id="bbb80-104">Verwenden Sie eine Flip-Ansicht zum Durchsuchen von Bildern oder anderen Elementen in einer Sammlung, z. B. von Fotos in einem Album oder von Elementen auf einer Seite mit Produktdetails, wobei jeweils ein Bild gescannt wird.</span><span class="sxs-lookup"><span data-stu-id="bbb80-104">Use a flip view for browsing images or other items in a collection, such as photos in an album or items in a product details page, one item at a time.</span></span> <span data-ttu-id="bbb80-105">Bei Geräten mit Touchscreen erfolgt die Navigation durch die Sammlung mit einer Wischbewegung über ein Element.</span><span class="sxs-lookup"><span data-stu-id="bbb80-105">For touch devices, swiping across an item moves through the collection.</span></span> <span data-ttu-id="bbb80-106">Bei Verwendung mit einer Maus werden beim Zeigen mit der Maus Navigationsschaltflächen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bbb80-106">For a mouse, navigation buttons appear on mouse hover.</span></span> <span data-ttu-id="bbb80-107">Bei Verwendung einer Tastatur erfolgt die Navigation durch die Sammlung mithilfe der Pfeiltasten.</span><span class="sxs-lookup"><span data-stu-id="bbb80-107">For a keyboard, arrow keys move through the collection.</span></span>

> <span data-ttu-id="bbb80-108">**Wichtige APIs**: [FlipView-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.flipview.aspx), [ItemsSource-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemssource.aspx), [ItemTemplate-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemtemplate.aspx)</span><span class="sxs-lookup"><span data-stu-id="bbb80-108">**Important APIs**: [FlipView class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.flipview.aspx), [ItemsSource property](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemssource.aspx), [ItemTemplate property](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemtemplate.aspx)</span></span>


## <a name="is-this-the-right-control"></a><span data-ttu-id="bbb80-109">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="bbb80-109">Is this the right control?</span></span>

<span data-ttu-id="bbb80-110">Die Flip-Ansicht ist zum Durchblättern von Bildern in kleinen bis mittelgroßen Sammlungen (bis zu ungefähr 25 Elementen) am besten geeignet.</span><span class="sxs-lookup"><span data-stu-id="bbb80-110">Flip view is best for perusing images in small to medium collections (up to 25 or so items).</span></span> <span data-ttu-id="bbb80-111">Beispiele für solche Sammlungen sind Elemente auf einer Seite mit Produktdetails oder Fotos in einem Fotoalbum.</span><span class="sxs-lookup"><span data-stu-id="bbb80-111">Examples of such collections include items in a product details page or photos in a photo album.</span></span> <span data-ttu-id="bbb80-112">Obwohl die Flip-Ansicht für die meisten großen Auflistungen nicht empfohlen wird, kann das Steuerelement für das Anzeigen einzelner Bilder in einem Fotoalbum verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bbb80-112">Although we don't recommend flip view for most large collections, the control is common for viewing individual images in a photo album.</span></span>

## <a name="examples"></a><span data-ttu-id="bbb80-113">Beispiele</span><span class="sxs-lookup"><span data-stu-id="bbb80-113">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="bbb80-114">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="bbb80-114">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="bbb80-115">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/FlipView">die App zu öffnen und FlipView in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="bbb80-115">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/FlipView">open the app and see the FlipView in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="bbb80-116">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="bbb80-116">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="bbb80-117">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="bbb80-117">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

<span data-ttu-id="bbb80-118">Horizontales Browsen, das bei dem Element ganz links beginnt und bei dem dann nach rechts geblättert wird, ist das typische Layout für eine Flip-Ansicht.</span><span class="sxs-lookup"><span data-stu-id="bbb80-118">Horizontal browsing, starting at the left-most item and flipping right, is the typical layout for a flip view.</span></span> <span data-ttu-id="bbb80-119">Dieses Layout eignet sich im Hochformat oder im Querformat auf allen Geräten:</span><span class="sxs-lookup"><span data-stu-id="bbb80-119">This layout works well in either portrait or landscape orientation on all devices:</span></span>

![Beispiel für das horizontale Layout in der Flip-Ansicht](images/controls_flipview_horizonal.jpg)

<span data-ttu-id="bbb80-121">Eine Flip-Ansicht kann auch vertikal durchsucht werden:</span><span class="sxs-lookup"><span data-stu-id="bbb80-121">A flip view can also be browsed vertically:</span></span>

![Beispiel für eine vertikale Flip-Ansicht](images/controls_flipview_vertical.jpg)

## <a name="create-a-flip-view"></a><span data-ttu-id="bbb80-123">Erstellen einer Flip-Ansicht</span><span class="sxs-lookup"><span data-stu-id="bbb80-123">Create a flip view</span></span>

<span data-ttu-id="bbb80-124">FlipView ist ein [ItemsControl](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.aspx), so dass es eine Sammlung von Elementen jeden Typs enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="bbb80-124">FlipView is an [ItemsControl](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.aspx), so it can contain a collection of items of any type.</span></span> <span data-ttu-id="bbb80-125">Um die Ansicht auszufüllen, fügen Sie der Sammlung [**Items**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.items.aspx) Elemente hinzu, oder legen die Eigenschaft [**ItemsSource**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemssource.aspx) auf eine Datenquelle fest.</span><span class="sxs-lookup"><span data-stu-id="bbb80-125">To populate the view, add items to the [**Items**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.items.aspx) collection, or set the [**ItemsSource**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemssource.aspx) property to a data source.</span></span>

<span data-ttu-id="bbb80-126">Datenelemente werden in der Flip-Ansicht standardmäßig als Zeichenfolgendarstellung des Datenobjekts angezeigt, an das sie gebunden sind.</span><span class="sxs-lookup"><span data-stu-id="bbb80-126">By default, a data item is displayed in the flip view as the string representation of the data object it's bound to.</span></span> <span data-ttu-id="bbb80-127">Um genau anzugeben, wie Elemente in der Flip-Ansicht angezeigt werden, erstellen Sie eine [**DataTemplate**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.datatemplate.aspx), um das Layout der Steuerelemente zu definieren, die für die Anzeige eines einzelnen Elements verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bbb80-127">To specify exactly how items in the flip view are displayed, you create a [**DataTemplate**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.datatemplate.aspx) to define the layout of controls used to display an individual item.</span></span> <span data-ttu-id="bbb80-128">Die Steuerelemente im Layout können an Eigenschaften eines Datenobjekts gebunden werden. Es ist auch möglich, den Inhalt intern zu definieren.</span><span class="sxs-lookup"><span data-stu-id="bbb80-128">The controls in the layout can be bound to properties of a data object, or have content defined inline.</span></span> <span data-ttu-id="bbb80-129">Sie weisen die DataTemplate der Eigenschaft [**DataTemplate**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemtemplate.aspx) von FlipView zu.</span><span class="sxs-lookup"><span data-stu-id="bbb80-129">You assign the DataTemplate to the [**ItemTemplate**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemtemplate.aspx) property of the FlipView.</span></span>

### <a name="add-items-to-the-items-collection"></a><span data-ttu-id="bbb80-130">Hinzufügen von Elementen zur Sammlung Items</span><span class="sxs-lookup"><span data-stu-id="bbb80-130">Add items to the Items collection</span></span>

<span data-ttu-id="bbb80-131">Sie können der Sammlung [**Items**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.items.aspx) Elemente per XAML oder Code hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="bbb80-131">You can add items to the [**Items**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.items.aspx) collection using XAML or code.</span></span> <span data-ttu-id="bbb80-132">In der Regel fügen Sie Elemente auf diese Weise hinzu, wenn Sie nur über eine geringe Anzahl von Elementen verfügen, die sich nicht ändern und einfach in XAML definiert werden können, oder wenn die Elemente zur Laufzeit im Code generiert werden.</span><span class="sxs-lookup"><span data-stu-id="bbb80-132">You typically add items this way if you have a small number of items that don't change and are easily defined in XAML, or if you generate the items in code at run time.</span></span> <span data-ttu-id="bbb80-133">Hier sehen Sie eine Flip-Ansicht mit inline definierten Elementen.</span><span class="sxs-lookup"><span data-stu-id="bbb80-133">Here's a flip view with items defined inline.</span></span>

```xaml
<FlipView x:Name="flipView1">
    <Image Source="Assets/Logo.png" />
    <Image Source="Assets/SplashScreen.png" />
    <Image Source="Assets/SmallLogo.png" />
</FlipView>
```

```csharp
// Create a new flip view, add content, 
// and add a SelectionChanged event handler.
FlipView flipView1 = new FlipView();
flipView1.Items.Add("Item 1");
flipView1.Items.Add("Item 2");

// Add the flip view to a parent container in the visual tree.
stackPanel1.Children.Add(flipView1);
```

<span data-ttu-id="bbb80-134">Wenn Sie einer Flip-Ansicht Elemente hinzufügen, werden diese automatisch in einem [**FlipViewItem**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.flipviewitem.aspx)-Container platziert.</span><span class="sxs-lookup"><span data-stu-id="bbb80-134">When you add items to a flip view they are automatically placed in a [**FlipViewItem**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.flipviewitem.aspx) container.</span></span> <span data-ttu-id="bbb80-135">Um die Art und Weise zu ändern, wie ein Element angezeigt wird, können Sie dem Elementcontainer einen Stil zuordnen. Legen Sie dazu die [**ItemContainerStyle**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemcontainerstyle.aspx)-Eigenschaft fest.</span><span class="sxs-lookup"><span data-stu-id="bbb80-135">To change how an item is displayed you can apply a style to the item container by setting the [**ItemContainerStyle**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemcontainerstyle.aspx) property.</span></span> 

<span data-ttu-id="bbb80-136">Wenn Sie die Elemente in XAML definieren, werden sie der Sammlung Items automatisch hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="bbb80-136">When you define the items in XAML, they are automatically added to the Items collection.</span></span>

### <a name="set-the-items-source"></a><span data-ttu-id="bbb80-137">Festlegen der Quelle von Elementen</span><span class="sxs-lookup"><span data-stu-id="bbb80-137">Set the items source</span></span>

<span data-ttu-id="bbb80-138">In der Regel verwenden Sie eine Flip-Ansicht, um Daten aus Quellen wie einer Datenbank oder dem Internet anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="bbb80-138">You typically use a flip view to display data from a source such as a database or the Internet.</span></span> <span data-ttu-id="bbb80-139">Um eine Flip-Ansicht aus einer Datenquelle zu füllen, legen Sie deren Eigenschaft [**ItemsSource**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemssource.aspx) auf eine Sammlung mit Datenelementen fest.</span><span class="sxs-lookup"><span data-stu-id="bbb80-139">To populate a flip view from a data source, you set its [**ItemsSource**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemssource.aspx) property to a collection of data items.</span></span>

<span data-ttu-id="bbb80-140">Hier ist die ItemsSource der Flip-Ansicht im Code direkt auf eine Instanz einer Sammlung festgelegt.</span><span class="sxs-lookup"><span data-stu-id="bbb80-140">Here, the flip view's ItemsSource is set in code directly to an instance of a collection.</span></span>

```csharp
// Data source.
List<String> itemsList = new List<string>();
itemsList.Add("Item 1");
itemsList.Add("Item 2");

// Create a new flip view, add content, 
// and add a SelectionChanged event handler.
FlipView flipView1 = new FlipView();
flipView1.ItemsSource = itemsList;
flipView1.SelectionChanged += FlipView_SelectionChanged;

// Add the flip view to a parent container in the visual tree.
stackPanel1.Children.Add(flipView1);
```

<span data-ttu-id="bbb80-141">Sie können auch die ItemsSource-Eigenschaft an eine Sammlung in XAML binden.</span><span class="sxs-lookup"><span data-stu-id="bbb80-141">You can also bind the ItemsSource property to a collection in XAML.</span></span> <span data-ttu-id="bbb80-142">Weitere Informationen finden Sie unter [Datenbindung mit XAML](../../data-binding/data-binding-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="bbb80-142">For more info, see [Data binding with XAML](../../data-binding/data-binding-quickstart.md).</span></span>

<span data-ttu-id="bbb80-143">Hier wird die ItemsSource an eine [**CollectionViewSource**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.data.collectionviewsource.aspx) mit dem Namen `itemsViewSource` gebunden.</span><span class="sxs-lookup"><span data-stu-id="bbb80-143">Here, the ItemsSource is bound to a [**CollectionViewSource**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.data.collectionviewsource.aspx) named `itemsViewSource`.</span></span> 

```xaml
<Page.Resources>
    <!-- Collection of items displayed by this page -->
    <CollectionViewSource x:Name="itemsViewSource" Source="{Binding Items}"/>
</Page.Resources>

...

<FlipView x:Name="itemFlipView" 
          ItemsSource="{Binding Source={StaticResource itemsViewSource}}"/>
```

><span data-ttu-id="bbb80-144">**Hinweis**&nbsp;&nbsp;Sie können eine Flip-Ansicht auffüllen, indem Sie entweder der Items-Sammlung Elemente hinzufügen oder die ItemsSource-Eigenschaft festlegen. Die beiden Methoden können jedoch nicht gleichzeitig verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bbb80-144">**Note**&nbsp;&nbsp;You can populate a flip view either by adding items to its Items collection, or by setting its ItemsSource property, but you can't use both ways at the same time.</span></span> <span data-ttu-id="bbb80-145">Wenn Sie die ItemsSource-Eigenschaft festlegen und dann ein Element in XAML hinzufügen, wird das hinzugefügte Element ignoriert.</span><span class="sxs-lookup"><span data-stu-id="bbb80-145">If you set the ItemsSource property and you add an item in XAML, the added item is ignored.</span></span> <span data-ttu-id="bbb80-146">Wenn Sie die ItemsSource-Eigenschaft festlegen und der Items-Sammlung ein Element in Code hinzufügen, wird eine Ausnahme ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="bbb80-146">If you set the ItemsSource property and you add an item to the Items collection in code, an exception is thrown.</span></span>

### <a name="specify-the-look-of-the-items"></a><span data-ttu-id="bbb80-147">Festlegen der Darstellung der Elemente</span><span class="sxs-lookup"><span data-stu-id="bbb80-147">Specify the look of the items</span></span>

<span data-ttu-id="bbb80-148">Datenelemente werden in der Flip-Ansicht standardmäßig als Zeichenfolgendarstellung des Datenobjekts angezeigt, an das sie gebunden sind.</span><span class="sxs-lookup"><span data-stu-id="bbb80-148">By default, a data item is displayed in the flip view as the string representation of the data object it's bound to.</span></span> <span data-ttu-id="bbb80-149">In der Regel möchten Sie eine ansprechendere Darstellung Ihrer Daten anzeigen.</span><span class="sxs-lookup"><span data-stu-id="bbb80-149">You typically want to show a more rich presentation of your data.</span></span> <span data-ttu-id="bbb80-150">Um genau anzugeben, wie Elemente in der Flip-Ansicht angezeigt werden, erstellen Sie eine [**DataTemplate**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.datatemplate.aspx).</span><span class="sxs-lookup"><span data-stu-id="bbb80-150">To specify exactly how items in the flip view are displayed, you create a [**DataTemplate**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.datatemplate.aspx).</span></span> <span data-ttu-id="bbb80-151">Der XAML-Code in der DataTemplate definiert das Layout und die Darstellung von Steuerelementen, die zum Anzeigen eines einzelnen Elements verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bbb80-151">The XAML in the DataTemplate defines the layout and appearance of controls used to display an individual item.</span></span> <span data-ttu-id="bbb80-152">Die Steuerelemente im Layout können an Eigenschaften eines Datenobjekts gebunden werden. Es ist auch möglich, den Inhalt intern zu definieren.</span><span class="sxs-lookup"><span data-stu-id="bbb80-152">The controls in the layout can be bound to properties of a data object, or have content defined inline.</span></span> <span data-ttu-id="bbb80-153">Die DataTemplate ist der Eigenschaft [**ItemTemplate**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemtemplate.aspx) des FlipView-Steuerelements zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="bbb80-153">The DataTemplate is assigned to the [**ItemTemplate**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemtemplate.aspx) property of the FlipView control.</span></span>

<span data-ttu-id="bbb80-154">In diesem Beispiel wird die ItemTemplate einer FlipView inline definiert.</span><span class="sxs-lookup"><span data-stu-id="bbb80-154">In this example, the ItemTemplate of a FlipView is defined inline.</span></span> <span data-ttu-id="bbb80-155">Dem Bild wird eine Überlagerung hinzugefügt, um den Bildnamen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="bbb80-155">An overlay is added to the image to display the image name.</span></span> 

```XAML
<FlipView x:Name="flipView1" Width="480" Height="270" 
          BorderBrush="Black" BorderThickness="1">
    <FlipView.ItemTemplate>
        <DataTemplate>
            <Grid>
                <Image Width="480" Height="270" Stretch="UniformToFill"
                       Source="{Binding Image}"/>
                <Border Background="#A5000000" Height="80" VerticalAlignment="Bottom">
                    <TextBlock Text="{Binding Name}" 
                               FontFamily="Segoe UI" FontSize="26.667" 
                               Foreground="#CCFFFFFF" Padding="15,20"/>
                </Border>
            </Grid>
        </DataTemplate>
    </FlipView.ItemTemplate>
</FlipView>
```

<span data-ttu-id="bbb80-156">Hier sehen Sie das durch die Datenvorlage definierte Layout.</span><span class="sxs-lookup"><span data-stu-id="bbb80-156">Here's what the layout defined by the data template looks like.</span></span>

<span data-ttu-id="bbb80-157">Datenvorlage für die Flip-Ansicht.</span><span class="sxs-lookup"><span data-stu-id="bbb80-157">Flip view data template.</span></span>

### <a name="set-the-orientation-of-the-flip-view"></a><span data-ttu-id="bbb80-158">Festlegen der Ausrichtung der Flip-Ansicht</span><span class="sxs-lookup"><span data-stu-id="bbb80-158">Set the orientation of the flip view</span></span>

<span data-ttu-id="bbb80-159">Standardmäßig blättert die Flip-Ansicht horizontal.</span><span class="sxs-lookup"><span data-stu-id="bbb80-159">By default, the flip view flips horizontally.</span></span> <span data-ttu-id="bbb80-160">Damit sie vertikal blättert, verwenden Sie ein StackPanel-Element mit vertikaler Ausrichtung als [**ItemsPanel**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemspanel.aspx) der Flip-Ansicht.</span><span class="sxs-lookup"><span data-stu-id="bbb80-160">To make the it flip vertically, use a stack panel with a vertical orientation as the flip view's [**ItemsPanel**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemspanel.aspx).</span></span>

<span data-ttu-id="bbb80-161">Dieses Beispiel zeigt, wie ein StackPanel-Element mit vertikaler Ausrichtung als ItemsPanel einer FlipView verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="bbb80-161">This example shows how to use a stack panel with a vertical orientation as the ItemsPanel of a FlipView.</span></span>

```XAML
<FlipView x:Name="flipViewVertical" Width="480" Height="270" 
          BorderBrush="Black" BorderThickness="1">
    
    <!-- Use a vertical stack panel for vertical flipping. -->
    <FlipView.ItemsPanel>
        <ItemsPanelTemplate>
            <VirtualizingStackPanel Orientation="Vertical"/>
        </ItemsPanelTemplate>
    </FlipView.ItemsPanel>
    
    <FlipView.ItemTemplate>
        <DataTemplate>
            <Grid>
                <Image Width="480" Height="270" Stretch="UniformToFill"
                       Source="{Binding Image}"/>
                <Border Background="#A5000000" Height="80" VerticalAlignment="Bottom">
                    <TextBlock Text="{Binding Name}" 
                               FontFamily="Segoe UI" FontSize="26.667" 
                               Foreground="#CCFFFFFF" Padding="15,20"/>
                </Border>
            </Grid>
        </DataTemplate>
    </FlipView.ItemTemplate>
</FlipView>
```

<span data-ttu-id="bbb80-162">So sieht die Flip-Ansicht mit vertikale Ausrichtung aus.</span><span class="sxs-lookup"><span data-stu-id="bbb80-162">Here's what the flip view looks like with a vertical orientation.</span></span>

![Beispiel für eine vertikale Flip-Ansicht](images/controls_flipview_vertical.jpg)

## <a name="adding-a-context-indicator"></a><span data-ttu-id="bbb80-164">Hinzufügen einer Kontextanzeige</span><span class="sxs-lookup"><span data-stu-id="bbb80-164">Adding a context indicator</span></span>

<span data-ttu-id="bbb80-165">Eine Kontextanzeige in einer Flip-Ansicht stellt einen nützlichen Referenzpunkt dar.</span><span class="sxs-lookup"><span data-stu-id="bbb80-165">A context indicator in a flip view provides a useful point of reference.</span></span> <span data-ttu-id="bbb80-166">Die Punkte in einer standardmäßigen Kontextanzeige sind nicht interaktiv.</span><span class="sxs-lookup"><span data-stu-id="bbb80-166">The dots in a standard context indicator aren't interactive.</span></span> <span data-ttu-id="bbb80-167">Wie in diesem Beispiel gezeigt, ist die beste Position in der Regel zentriert und unterhalb des Katalogs:</span><span class="sxs-lookup"><span data-stu-id="bbb80-167">As seen in this example, the best placement is usually centered and below the gallery:</span></span>

![Beispiel für eine Seitenanzeige](images/controls_pageindicator.png)

<span data-ttu-id="bbb80-169">Für größere Sammlungen (10-25 Elemente) kann eine Anzeige mit mehr Kontext, z. B. ein Bildstreifen, nützlich sein.</span><span class="sxs-lookup"><span data-stu-id="bbb80-169">For larger collections (10-25 items), consider using an indicator that provides more context, such as a film strip of thumbnails.</span></span> <span data-ttu-id="bbb80-170">Im Gegensatz zu einer Kontextanzeige, die einfache Punkte verwendet, zeigt jede Miniaturansicht auf dem Bildstreifen eine kleine Version des entsprechenden Bilds und sollte ausgewählt werden können:</span><span class="sxs-lookup"><span data-stu-id="bbb80-170">Unlike a context indicator that uses simple dots, each thumbnail in the film strip shows a small version of the corresponding image and should be selectable:</span></span>

![Beispiel für die Kontextanzeige](images/controls_contextindicator.jpg)

<span data-ttu-id="bbb80-172">Beispielcode, der veranschaulicht, wie Sie einem FlipView-Element eine Kontextanzeige hinzufügen, finden Sie unter [Beispiel für XAML FlipView](http://go.microsoft.com/fwlink/p/?LinkID=311760).</span><span class="sxs-lookup"><span data-stu-id="bbb80-172">For example code that shows how to add a context indicator to a FlipView, see [XAML FlipView sample](http://go.microsoft.com/fwlink/p/?LinkID=311760).</span></span>

## <a name="dos-and-donts"></a><span data-ttu-id="bbb80-173">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="bbb80-173">Do's and don'ts</span></span>

-   <span data-ttu-id="bbb80-174">Flip-Ansichten sind am besten für Sammlungen von bis zu 25 Elementen geeignet.</span><span class="sxs-lookup"><span data-stu-id="bbb80-174">Flip views work best for collections of up to 25 or so items.</span></span>
-   <span data-ttu-id="bbb80-175">Vermeiden Sie ein Flip-Ansicht-Steuerelement für größere Sammlungen, da das wiederholte Blättern durch die einzelnen Elemente mühsam sein kann.</span><span class="sxs-lookup"><span data-stu-id="bbb80-175">Avoid using a flip view control for larger collections, as the repetitive motion of flipping through each item can be tedious.</span></span> <span data-ttu-id="bbb80-176">Eine Ausnahme stellen Fotoalben dar, die häufig Hunderte oder Tausende von Bildern enthalten.</span><span class="sxs-lookup"><span data-stu-id="bbb80-176">An exception would be for photo albums, which often have hundreds or thousands of images.</span></span> <span data-ttu-id="bbb80-177">Fotoalben wechseln nach dem Auswählen eines Fotos in der Rasteransicht fast immer zur Flip-Ansicht.</span><span class="sxs-lookup"><span data-stu-id="bbb80-177">Photo albums almost always switch to a flip view once a photo has been selected in the grid view layout.</span></span> <span data-ttu-id="bbb80-178">Erwägen Sie für andere große Sammlungen eine [Listen- oder Rasteransicht](lists.md).</span><span class="sxs-lookup"><span data-stu-id="bbb80-178">For other large collections, consider a [List view or grid view](lists.md).</span></span>
-   <span data-ttu-id="bbb80-179">Für Kontextanzeigen:</span><span class="sxs-lookup"><span data-stu-id="bbb80-179">For context indicators:</span></span>
    -   <span data-ttu-id="bbb80-180">Die Reihenfolge der Punkte (oder anderer visueller Kennzeichnungen, die Sie verwenden) funktioniert am besten zentriert und unter einem horizontal verschiebbaren Katalog.</span><span class="sxs-lookup"><span data-stu-id="bbb80-180">The order of dots (or whichever visual marker you choose) works best when centered and below a horizontally-panning gallery.</span></span>
    -   <span data-ttu-id="bbb80-181">Wenn Sie eine Kontextanzeige in einer vertikal verschiebbaren Galerie anzeigen möchten, funktioniert diese am besten zentriert und rechts neben den Bildern.</span><span class="sxs-lookup"><span data-stu-id="bbb80-181">If you want a context indicator in a vertically-panning gallery, it works best centered and to the right of the images.</span></span>
    -   <span data-ttu-id="bbb80-182">Der hervorgehobene Punkt gibt das aktuelle Element an.</span><span class="sxs-lookup"><span data-stu-id="bbb80-182">The highlighted dot indicates the current item.</span></span> <span data-ttu-id="bbb80-183">In der Regel ist der hervorgehobene Punkt weiß, und die anderen Punkte werden grau dargestellt.</span><span class="sxs-lookup"><span data-stu-id="bbb80-183">Usually the highlighted dot is white and the other dots are gray.</span></span>
    -   <span data-ttu-id="bbb80-184">Die Anzahl von Punkten kann variieren. Verwenden Sie jedoch nicht so viele Punkte, dass der Benutzer die Orientierung verliert – in der Regel sollten höchstens 10 Punkte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bbb80-184">The number of dots can vary, but don't have so many that the user might struggle to find his or her place - 10 dots is usually the maximum number to show.</span></span>

## <a name="globalization-and-localization-checklist"></a><span data-ttu-id="bbb80-185">Prüfliste für Globalisierung und Lokalisierung</span><span class="sxs-lookup"><span data-stu-id="bbb80-185">Globalization and localization checklist</span></span>

<table>
<tr>
<th><span data-ttu-id="bbb80-186">Aspekte der Bidirektionalität</span><span class="sxs-lookup"><span data-stu-id="bbb80-186">Bi-directional considerations</span></span></th><td><span data-ttu-id="bbb80-187">Verwenden Sie die standardmäßige Spiegelung für Rechts-nach-links-Sprachen.</span><span class="sxs-lookup"><span data-stu-id="bbb80-187">Use standard mirroring for RTL languages.</span></span> <span data-ttu-id="bbb80-188">Die Steuerelemente „Zurück“ und „Vorwärts“ sollten auf der Richtung der Schrift beruhen. Bei Rechts-nach-links-Schriften sollte daher die rechte Schaltfläche die Rückwärtsnavigation und die linke Schaltfläche die Vorwärtsnavigation ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="bbb80-188">The back and forward controls should be based on the language's direction, so for RTL languages, the right button should navigate backwards and the left button should navigate forward.</span></span></td>
</tr>

</table>

## <a name="get-the-sample-code"></a><span data-ttu-id="bbb80-189">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="bbb80-189">Get the sample code</span></span>

- <span data-ttu-id="bbb80-190">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="bbb80-190">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="bbb80-191">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="bbb80-191">Related articles</span></span>

- [<span data-ttu-id="bbb80-192">Richtlinien für Listen</span><span class="sxs-lookup"><span data-stu-id="bbb80-192">Guidelines for lists</span></span>](lists.md)
- [**<span data-ttu-id="bbb80-193">FlipView-Klasse</span><span class="sxs-lookup"><span data-stu-id="bbb80-193">FlipView class</span></span>**](https://msdn.microsoft.com/library/windows/apps/br242678)
