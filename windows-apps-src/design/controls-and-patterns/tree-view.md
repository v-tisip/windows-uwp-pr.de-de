---
author: Jwmsft
description: Sie können eine erweiterbare Strukturansicht erstellen, indem Sie die ItemsSource an eine hierarchische Datenquelle zu binden, oder Sie erstellen und TreeViewNode-Objekte selbst verwalten können.
title: Strukturansicht
label: Tree view
template: detail.hbs
ms.author: jimwalk
ms.date: 10/02/2018
ms.localizationpriority: medium
pm-contact: predavid
design-contact: ksulliv
dev-contact: joyate
doc-status: Published
dev_langs:
- csharp
- vb
ms.custom: RS5
ms.openlocfilehash: 1a7dfa2605607c3b2440a9ebc46a0b3eb6010287
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7286486"
---
# <a name="treeview"></a><span data-ttu-id="4d5cd-103">TreeView</span><span class="sxs-lookup"><span data-stu-id="4d5cd-103">TreeView</span></span>

<span data-ttu-id="4d5cd-104">Das XAML-Steuerelement TreeView ermöglicht eine Hierarchieauflistung mit Knoten, die das Aus- und Einblenden von geschachtelten Elementen erlauben.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-104">The XAML TreeView control enables a hierarchical list with expanding and collapsing nodes that contain nested items.</span></span> <span data-ttu-id="4d5cd-105">Es kann verwendet werden, um eine Ordnerstruktur oder geschachtelte Beziehungen zwischen Elementen in der Benutzeroberfläche zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-105">It can be used to illustrate a folder structure or nested relationships in your UI.</span></span>

<span data-ttu-id="4d5cd-106">Die TreeView-APIs unterstützen die folgenden Features:</span><span class="sxs-lookup"><span data-stu-id="4d5cd-106">The TreeView APIs support the following features:</span></span>

- <span data-ttu-id="4d5cd-107">Schachtelung von N Ebenen</span><span class="sxs-lookup"><span data-stu-id="4d5cd-107">N-level nesting</span></span>
- <span data-ttu-id="4d5cd-108">Auswahl einzelner oder mehreren Knoten</span><span class="sxs-lookup"><span data-stu-id="4d5cd-108">Selection of single or multiple nodes</span></span>
- <span data-ttu-id="4d5cd-109">(Vorschau) Binden von Daten an die ItemsSource-Eigenschaft auf TreeView- und Objekte in der Strukturansicht</span><span class="sxs-lookup"><span data-stu-id="4d5cd-109">(Preview) Data binding to the ItemsSource property on TreeView and TreeViewItem</span></span>
- <span data-ttu-id="4d5cd-110">(Vorschau) Objekte in der Strukturansicht als Stamm der Elementvorlage Strukturansicht</span><span class="sxs-lookup"><span data-stu-id="4d5cd-110">(Preview) TreeViewItem as the root of the TreeView item template</span></span>
- <span data-ttu-id="4d5cd-111">(Vorschau) Beliebige Arten von Inhalten in einem Objekte in der Strukturansicht</span><span class="sxs-lookup"><span data-stu-id="4d5cd-111">(Preview) Arbitrary types of content in a TreeViewItem</span></span>
- <span data-ttu-id="4d5cd-112">(Vorschau) Drag & drop zwischen Strukturansichten</span><span class="sxs-lookup"><span data-stu-id="4d5cd-112">(Preview) Drag and drop between tree views</span></span>

| **<span data-ttu-id="4d5cd-113">Abrufen der Windows-UI-Bibliothek</span><span class="sxs-lookup"><span data-stu-id="4d5cd-113">Get the Windows UI Library</span></span>** |
| - |
| <span data-ttu-id="4d5cd-114">Dieses Steuerelement ist Bestandteil der Windows-UI-Bibliothek, ein NuGet-Paket, das neue Steuerelemente und UI-Features für UWP-apps enthält.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-114">This control is included as part of the Windows UI Library, a NuGet package that contains new controls and UI features for UWP apps.</span></span> <span data-ttu-id="4d5cd-115">Weitere Informationen, einschließlich installationsanweisungen finden Sie die [Übersicht über die Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).</span><span class="sxs-lookup"><span data-stu-id="4d5cd-115">For more info, including installation instructions, see the [Windows UI Library overview](https://docs.microsoft.com/uwp/toolkits/winui/).</span></span> |

| **<span data-ttu-id="4d5cd-116">Plattform-APIs</span><span class="sxs-lookup"><span data-stu-id="4d5cd-116">Platform APIs</span></span>** | **<span data-ttu-id="4d5cd-117">Windows-UI-Bibliothek APIs</span><span class="sxs-lookup"><span data-stu-id="4d5cd-117">Windows UI Library APIs</span></span>** |
| - | - |
| <span data-ttu-id="4d5cd-118">[TreeView-Klasse](/uwp/api/windows.ui.xaml.controls.treeview), [TreeViewNode-Klasse](/uwp/api/windows.ui.xaml.controls.treeviewnode), [TreeView.ItemsSource-Eigenschaft](/uwp/api/windows.ui.xaml.controls.treeview.itemssource)</span><span class="sxs-lookup"><span data-stu-id="4d5cd-118">[TreeView class](/uwp/api/windows.ui.xaml.controls.treeview), [TreeViewNode class](/uwp/api/windows.ui.xaml.controls.treeviewnode), [TreeView.ItemsSource property](/uwp/api/windows.ui.xaml.controls.treeview.itemssource)</span></span> | <span data-ttu-id="4d5cd-119">[TreeView-Klasse](/uwp/api/microsoft.ui.xaml.controls.treeview), [TreeViewNode-Klasse](/uwp/api/microsoft.ui.xaml.controls.treeviewnode), [TreeView.ItemsSource-Eigenschaft](/uwp/api/microsoft.ui.xaml.controls.treeview.itemssource)</span><span class="sxs-lookup"><span data-stu-id="4d5cd-119">[TreeView class](/uwp/api/microsoft.ui.xaml.controls.treeview), [TreeViewNode class](/uwp/api/microsoft.ui.xaml.controls.treeviewnode), [TreeView.ItemsSource property](/uwp/api/microsoft.ui.xaml.controls.treeview.itemssource)</span></span> |

## <a name="is-this-the-right-control"></a><span data-ttu-id="4d5cd-120">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="4d5cd-120">Is this the right control?</span></span>

- <span data-ttu-id="4d5cd-121">Verwenden Sie eine Strukturansicht, wenn Elemente geschachtelte Elemente haben, und dann, wenn es wichtig ist, die hierarchische Beziehung zwischen Elementen und ihren gleichgestellten Elementen und Knoten zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-121">Use a TreeView when items have nested list items, and if it is important to illustrate the hierarchical relationship of items to their peers and nodes.</span></span>

- <span data-ttu-id="4d5cd-122">Vermeiden Sie Strukturansicht, wenn die geschachtelte Beziehung eines Elements nicht im Vordergrund steht.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-122">Avoid using TreeView if highlighting the nested relationship of an item is not a priority.</span></span> <span data-ttu-id="4d5cd-123">Für die meisten Drilldown-Szenarios eignet sich eine normale ListView</span><span class="sxs-lookup"><span data-stu-id="4d5cd-123">For most drill-in scenarios, a regular list view is appropriate</span></span>

## <a name="examples"></a><span data-ttu-id="4d5cd-124">Beispiele</span><span class="sxs-lookup"><span data-stu-id="4d5cd-124">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="4d5cd-125">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="4d5cd-125">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="4d5cd-126">Wenn Sie die <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> -app installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/TreeView">die app zu öffnen und finden Sie in der Strukturansicht in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-126">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/TreeView">open the app and see the TreeView in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="4d5cd-127">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="4d5cd-127">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="4d5cd-128">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="4d5cd-128">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="treeview-ui"></a><span data-ttu-id="4d5cd-129">TreeView-UI</span><span class="sxs-lookup"><span data-stu-id="4d5cd-129">TreeView UI</span></span>

<span data-ttu-id="4d5cd-130">Die Strukturansicht verwendet eine Kombination aus Einzügen und Symbolen, um die geschachtelte Beziehung zwischen Ordnern und übergeordneten Knoten bzw. Nicht-Ordnern und untergeordneten Knoten darzustellen.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-130">The tree view uses a combination of indentation and icons to represent the nested relationship between folder/parent nodes and non-folder/child nodes.</span></span> <span data-ttu-id="4d5cd-131">Ausgeblendete Knoten verwenden ein Chevron, welches nach rechts zeigt, während eingeblendete Knoten ein Chevron verwenden, das nach unten zeigt.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-131">Collapsed nodes use a chevron pointing to the right, and expanded nodes use a chevron pointing down.</span></span>

![Das Chevronsymbol in der Strukturansicht](images/treeview-simple.png)

<span data-ttu-id="4d5cd-133">Sie können ein Symbol in die Datenvorlage für Strukturansichtselemente einschließen, um Knoten darzustellen.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-133">You can include an icon in the tree view item data template to represent nodes.</span></span> <span data-ttu-id="4d5cd-134">In diesem Fall sollten Sie ein Ordnersymbol nur für Knoten verwenden, die literale Ordner wie etwa die Ordnerstruktur auf einem Datenträger darstellen.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-134">If you do this, you should use a folder icon only for nodes that represent literal folders, such as the folder structure on a disk.</span></span>

![Das Chevron- und Ordnersymbol zusammen in einer Strukturansicht](images/treeview-icons.png)

## <a name="create-a-tree-view"></a><span data-ttu-id="4d5cd-136">Erstellen einer Strukturansicht</span><span class="sxs-lookup"><span data-stu-id="4d5cd-136">Create a tree view</span></span>

<span data-ttu-id="4d5cd-137">Sie können eine Strukturansicht erstellen, indem Sie die [ItemsSource](/uwp/api/windows.ui.xaml.controls.treeview.itemssource) an eine hierarchische Datenquelle zu binden, oder Sie erstellen und TreeViewNode-Objekte selbst verwalten können.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-137">You can create a tree view by binding the [ItemsSource](/uwp/api/windows.ui.xaml.controls.treeview.itemssource) to a hierarchical data source, or you can create and manage TreeViewNode objects yourself.</span></span>

<span data-ttu-id="4d5cd-138">Um eine Strukturansicht zu erstellen, verwenden Sie ein [Strukturansicht](/uwp/api/windows.ui.xaml.controls.treeview)-Steuerelement und eine Hierarchie von [TreeViewNode](/uwp/api/windows.ui.xaml.controls.treeviewnode)-Objekten.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-138">To create a tree view, you use a [TreeView](/uwp/api/windows.ui.xaml.controls.treeview) control and a hierarchy of [TreeViewNode](/uwp/api/windows.ui.xaml.controls.treeviewnode) objects.</span></span> <span data-ttu-id="4d5cd-139">Sie erstellen die Kontenhierarchie [RootNodes](/uwp/api/windows.ui.xaml.controls.treeview.rootnodes) -Sammlung des Strukturansicht-Steuerelements eine oder mehrere Stammknoten hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-139">You create the node hierarchy by adding one or more root nodes to the TreeView control’s [RootNodes](/uwp/api/windows.ui.xaml.controls.treeview.rootnodes) collection.</span></span> <span data-ttu-id="4d5cd-140">Der Sammlung der untergeordneten Elemente der einzelnen TreeViewNodes können dann weitere Knoten hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-140">Each TreeViewNode can then have more nodes added to its Children collection.</span></span> <span data-ttu-id="4d5cd-141">Sie können Knoten der Strukturansicht auf jede beliebigen Tiefe schachteln.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-141">You can nest tree view nodes to whatever depth you require.</span></span>

<span data-ttu-id="4d5cd-142">Ab der Windows Insider Preview, können Sie eine hierarchische Datenquelle an die [ItemsSource](/uwp/api/windows.ui.xaml.controls.treeview.itemssource) -Eigenschaft, um den Inhalt der Strukturansicht, bieten binden genauso wie mit ListView ItemsSource aus.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-142">Starting in the Windows Insider Preview, you can bind a hierarchical data source to the [ItemsSource](/uwp/api/windows.ui.xaml.controls.treeview.itemssource) property to provide the tree view content, just as you would with ListView's ItemsSource.</span></span> <span data-ttu-id="4d5cd-143">Verwenden Sie entsprechend [ItemTemplate](/uwp/api/windows.ui.xaml.controls.treeview.itemtemplate) (und die optionale ["ItemTemplateSelector"](/uwp/api/windows.ui.xaml.controls.treeview.itemtemplate)) ein DataTemplate-Objekt bereitstellen, die das Element gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-143">Similarly, use [ItemTemplate](/uwp/api/windows.ui.xaml.controls.treeview.itemtemplate) (and the optional [ItemTemplateSelector](/uwp/api/windows.ui.xaml.controls.treeview.itemtemplate)) to provide a DataTemplate that renders the item.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4d5cd-144">ItemsSource ist eine alternative Mechanismus zum TreeView.RootNodes für das Ablegen von Inhalten in das TreeView-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-144">ItemsSource is an alternative mechanism to TreeView.RootNodes for putting content into the TreeView control.</span></span> <span data-ttu-id="4d5cd-145">Sie können nicht gleichzeitig ItemsSource sowohl RootNodes festlegen.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-145">You cannot set both ItemsSource and RootNodes at the same time.</span></span> <span data-ttu-id="4d5cd-146">Bei der Verwendung von ItemsSource Knoten für Sie erstellt, und Sie können diese von TreeView.RootNodes Eigenschaft zugreifen.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-146">When you use ItemsSource, nodes created for you, and you can access them from TreeView.RootNodes property.</span></span>

<span data-ttu-id="4d5cd-147">Im Folgenden finden Sie ein Beispiel für eine einfache in XAML deklarierte Strukturansicht.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-147">Here's an example of a simple tree view declared in XAML.</span></span> <span data-ttu-id="4d5cd-148">Sie fügen die Knoten in der Regel im Code hinzu, aber hier wird die XAML-Hierarchie angezeigt, da sie beim Visualisieren der Erstellung der Knotenhierarchie hilfreich sein kann.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-148">You typically add the nodes in code, but we show the XAML hierarchy here because it can be helpful for visualizing how the hierarchy of nodes is created.</span></span>

```xaml
<TreeView>
    <TreeView.RootNodes>
        <TreeViewNode Content="Flavors" IsExpanded="True">
            <TreeViewNode.Children>
                <TreeViewNode Content="Vanilla"/>
                <TreeViewNode Content="Strawberry"/>
                <TreeViewNode Content="Chocolate"/>
            </TreeViewNode.Children>
        </TreeViewNode>
    </TreeView.RootNodes>
</TreeView>
```

<span data-ttu-id="4d5cd-149">In den meisten Fällen zeigt die Strukturansicht Daten aus einer Datenquelle, sodass Sie in der Regel den Stamm TreeView-Steuerelement in XAML deklariert, jedoch fügen die TreeViewNode-Objekte im Code oder mithilfe der Datenbindung.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-149">In most cases, your tree view displays data from a data source, so you typically declare the root TreeView control in XAML, but add the TreeViewNode objects in code or using data binding.</span></span>

### <a name="bind-to-a-hierarchical-data-source"></a><span data-ttu-id="4d5cd-150">Binden Sie an eine hierarchische Datenquelle</span><span class="sxs-lookup"><span data-stu-id="4d5cd-150">Bind to a hierarchical data source</span></span>

<span data-ttu-id="4d5cd-151">Um eine Strukturansicht, die Verwendung der Datenbindung erstellen zu können, legen Sie eine hierarchische Auflistung der TreeView.ItemsSource-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-151">To create a tree view using data binding, set a hierarchical collection to the TreeView.ItemsSource property.</span></span> <span data-ttu-id="4d5cd-152">Legen Sie dann im ItemTemplate, das untergeordnete Element Items-Sammlung der TreeViewItem.ItemsSource-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-152">Then in the ItemTemplate, set the child items collection to the TreeViewItem.ItemsSource property.</span></span>

```xaml
<TreeView ItemsSource="{x:Bind DataSource}">
    <TreeView.ItemTemplate>
        <DataTemplate x:DataType="local:Item">
            <TreeViewItem ItemsSource="{x:Bind Children}"
                          Content="{x:Bind Name}"/>
        </DataTemplate>
    </TreeView.ItemTemplate>
</TreeView>
```

<span data-ttu-id="4d5cd-153">Finden Sie unter _Verwendung der Datenbindung Strukturansicht_ im Abschnitt "Beispiele" für den vollständigen Code.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-153">See _Tree view using data binding_ the Examples section for the full code.</span></span>

#### <a name="items-and-item-containers"></a><span data-ttu-id="4d5cd-154">Elemente und Elementcontainern</span><span class="sxs-lookup"><span data-stu-id="4d5cd-154">Items and item containers</span></span>

<span data-ttu-id="4d5cd-155">Diese APIs sind den Knoten oder Daten aus dem Container abrufen verfügbar, wenn Sie TreeView.ItemsSource verwenden, und umgekehrt.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-155">If you use TreeView.ItemsSource, these APIs are available to get the node or data item from the container, and vice versa.</span></span>

| **[<span data-ttu-id="4d5cd-156">Objekte in der Strukturansicht</span><span class="sxs-lookup"><span data-stu-id="4d5cd-156">TreeViewItem</span></span>](/uwp/api/windows.ui.xaml.controls.treeviewitem)** | |
| - | - |
| [<span data-ttu-id="4d5cd-157">TreeView.ItemFromContainer</span><span class="sxs-lookup"><span data-stu-id="4d5cd-157">TreeView.ItemFromContainer</span></span>](/uwp/api/windows.ui.xaml.controls.treeview.itemfromcontainer) | <span data-ttu-id="4d5cd-158">Ruft das Datenelement für den angegebenen Objekte in der Strukturansicht Container ab.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-158">Gets the data item for the specified TreeViewItem container.</span></span> |
| [<span data-ttu-id="4d5cd-159">TreeView.ContainerFromItem</span><span class="sxs-lookup"><span data-stu-id="4d5cd-159">TreeView.ContainerFromItem</span></span>](/uwp/api/windows.ui.xaml.controls.treeview.containerfromitem) | <span data-ttu-id="4d5cd-160">Ruft den Container Objekte in der Strukturansicht für das angegebene Datenelement ab.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-160">Gets the TreeViewItem container for the specified data item.</span></span> |

| **[<span data-ttu-id="4d5cd-161">TreeViewNode</span><span class="sxs-lookup"><span data-stu-id="4d5cd-161">TreeViewNode</span></span>](/uwp/api/windows.ui.xaml.controls.treeviewnode)** | |
| - | - |
| [<span data-ttu-id="4d5cd-162">TreeView.NodeFromContainer</span><span class="sxs-lookup"><span data-stu-id="4d5cd-162">TreeView.NodeFromContainer</span></span>](/uwp/api/windows.ui.xaml.controls.treeview.nodefromcontainer) | <span data-ttu-id="4d5cd-163">Ruft den TreeViewNode für den angegebenen Objekte in der Strukturansicht-Container.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-163">Gets the TreeViewNode for the specified TreeViewItem container.</span></span> |
| [<span data-ttu-id="4d5cd-164">TreeView.ContainerFromNode</span><span class="sxs-lookup"><span data-stu-id="4d5cd-164">TreeView.ContainerFromNode</span></span>](/uwp/api/windows.ui.xaml.controls.treeview.containerfromnode) | <span data-ttu-id="4d5cd-165">Ruft den Container Objekte in der Strukturansicht für den angegebenen TreeViewNode ab.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-165">Gets the TreeViewItem container for the specified TreeViewNode.</span></span> |

### <a name="manage-tree-view-nodes"></a><span data-ttu-id="4d5cd-166">Verwalten von Knoten der Strukturansicht</span><span class="sxs-lookup"><span data-stu-id="4d5cd-166">Manage tree view nodes</span></span>

<span data-ttu-id="4d5cd-167">Diese Strukturansicht ist identisch mit der zuvor in XAML erstellten, aber die Knoten werden stattdessen im Code erstellt.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-167">This tree view is the same as the one created previously in XAML, but the nodes are created in code instead.</span></span>

```xaml
<TreeView x:Name="sampleTreeView"/>
```

```csharp
private void InitializeTreeView()
{
    TreeViewNode rootNode = new TreeViewNode() { Content = "Flavors" };
    rootNode.IsExpanded = true;
    rootNode.Children.Add(new TreeViewNode() { Content = "Vanilla" });
    rootNode.Children.Add(new TreeViewNode() { Content = "Strawberry" });
    rootNode.Children.Add(new TreeViewNode() { Content = "Chocolate" });

    sampleTreeView.RootNodes.Add(rootNode);
}
```

```vb
Private Sub InitializeTreeView()
    Dim rootNode As New TreeViewNode With {.Content = "Flavors", .IsExpanded = True}
    With rootNode.Children
        .Add(New TreeViewNode With {.Content = "Vanilla"})
        .Add(New TreeViewNode With {.Content = "Strawberry"})
        .Add(New TreeViewNode With {.Content = "Chocolate"})
    End With
    sampleTreeView.RootNodes.Add(rootNode)
End Sub
```

<span data-ttu-id="4d5cd-168">Diese APIs sind für die Verwaltung der Datenhierarchie der Strukturansicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-168">These APIs are available for managing the data hierarchy of your tree view.</span></span>

| **[<span data-ttu-id="4d5cd-169">TreeView</span><span class="sxs-lookup"><span data-stu-id="4d5cd-169">TreeView</span></span>](/uwp/api/windows.ui.xaml.controls.treeview)** | |
| - | - |
| [<span data-ttu-id="4d5cd-170">RootNodes</span><span class="sxs-lookup"><span data-stu-id="4d5cd-170">RootNodes</span></span>](/uwp/api/windows.ui.xaml.controls.treeview.rootnodes) | <span data-ttu-id="4d5cd-171">Eine Strukturansicht kann einen oder mehrere Stammknoten aufweisen.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-171">A tree view can have one or more root nodes.</span></span> <span data-ttu-id="4d5cd-172">Fügen Sie der RootNodes-Sammlung ein TreeViewNode-Objekt hinzu, um einen Stammknoten zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-172">Add a TreeViewNode object to the RootNodes collection to create a root node.</span></span> <span data-ttu-id="4d5cd-173">Das **übergeordnete Element** eines Stammknotens hat immer den Wert **null**.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-173">The **Parent** of a root node is always **null**.</span></span> <span data-ttu-id="4d5cd-174">Die **Tiefe** eines Stammknotens beträgt 0.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-174">The **Depth** of a root node is 0.</span></span> |

| **[<span data-ttu-id="4d5cd-175">TreeViewNode</span><span class="sxs-lookup"><span data-stu-id="4d5cd-175">TreeViewNode</span></span>](/uwp/api/windows.ui.xaml.controls.treeviewnode)** | |
| - | - |
| [<span data-ttu-id="4d5cd-176">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="4d5cd-176">Children</span></span>](/uwp/api/windows.ui.xaml.controls.treeviewnode.children) | <span data-ttu-id="4d5cd-177">Fügen Sie der Sammlung der untergeordneten Elemente des TreeViewNode-Objekts einen übergeordneten Knoten hinzu, um eine Knotenhierarchie zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-177">Add TreeViewNode objects to the Children collection of a parent node to create your node hierarchy.</span></span> <span data-ttu-id="4d5cd-178">Ein Knoten ist das **übergeordnete Element** aller Knoten in der Sammlung der **untergeordneten Elemente**.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-178">A node is the **Parent** of all nodes in its **Children** collection.</span></span> |
| [<span data-ttu-id="4d5cd-179">HasChildren</span><span class="sxs-lookup"><span data-stu-id="4d5cd-179">HasChildren</span></span>](/uwp/api/windows.ui.xaml.controls.treeviewnode.haschildren) | <span data-ttu-id="4d5cd-180">Ist **true**, wenn der Knoten untergeordnete Elemente erkannt hat.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-180">**true** if the node has realized children.</span></span> <span data-ttu-id="4d5cd-181">**false** gibt einen leeren Ordner oder ein Element an.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-181">**false** indicates an empty folder or an item.</span></span> |
| [<span data-ttu-id="4d5cd-182">HasUnrealizedChildren</span><span class="sxs-lookup"><span data-stu-id="4d5cd-182">HasUnrealizedChildren</span></span>](/uwp/api/windows.ui.xaml.controls.treeviewnode.hasunrealizedchildren) | <span data-ttu-id="4d5cd-183">Verwenden Sie diese Eigenschaft, wenn Sie Knoten beim Erweitern ausgefüllt werden.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-183">Use this property if you're filling nodes as they're expanded.</span></span> <span data-ttu-id="4d5cd-184">Weitere Informationen finden Sie unter _Ausfüllen eines Knotens, wenn er erweitert wird_ weiter unten in diesem Artikel.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-184">See _Fill a node when it's expanding_ later in this article.</span></span> |
| [<span data-ttu-id="4d5cd-185">Tiefe</span><span class="sxs-lookup"><span data-stu-id="4d5cd-185">Depth</span></span>](/uwp/api/windows.ui.xaml.controls.treeviewnode.depth) | <span data-ttu-id="4d5cd-186">Gibt an, wie weit der Stammknoten von einem untergeordneten Knoten entfernt ist.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-186">Indicates how far from the root node a child node is.</span></span> |
| [<span data-ttu-id="4d5cd-187">Parent</span><span class="sxs-lookup"><span data-stu-id="4d5cd-187">Parent</span></span>](/uwp/api/windows.ui.xaml.controls.treeviewnode.parent) | <span data-ttu-id="4d5cd-188">Ruft den TreeViewNode ab, der die Sammlung der **untergeordneten Elemente** besitzt, zu der dieser Knoten gehört.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-188">Gets the TreeViewNode that owns the **Children** collection that this node is part of.</span></span> |

<span data-ttu-id="4d5cd-189">Die Strukturansicht verwendet die Eigenschaften **HasChildren** und **HasUnrealizedChildren**, um zu ermitteln, ob das Symbol „Erweitern/Reduzieren“ angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-189">The tree view uses the **HasChildren** and **HasUnrealizedChildren** properties to determine whether the expand/collapse icon is shown.</span></span> <span data-ttu-id="4d5cd-190">Wenn eine der Eigenschaften den Wert **true** hat, wird das Symbol angezeigt, andernfalls nicht.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-190">If either property is **true**, the icon is shown; otherwise, it's not shown.</span></span>

## <a name="tree-view-node-content"></a><span data-ttu-id="4d5cd-191">Inhalt des Knotens der Strukturansicht</span><span class="sxs-lookup"><span data-stu-id="4d5cd-191">Tree view node content</span></span>

<span data-ttu-id="4d5cd-192">Sie können das Datenelement, das ein Knoten darstellt, in dessen [Inhalte](/uwp/api/windows.ui.xaml.controls.treeviewnode.content)-Eigenschaft speichern.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-192">You can store the data item that a tree view node represents in its [Content](/uwp/api/windows.ui.xaml.controls.treeviewnode.content) property.</span></span>

<span data-ttu-id="4d5cd-193">Im vorherigen Beispielen war der Inhalt ein einfachen Zeichenfolgenwert.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-193">In the previous examples, the content was a simple string value.</span></span> <span data-ttu-id="4d5cd-194">Hier stellt ein Knoten der Strukturansicht den Ordner „Bilder“ des Benutzers dar. Daher ist die Bildbibliothek [StorageFolder](/uwp/api/windows.storage.storagefolder) der Inhaltseigenschaft des Knotens zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-194">Here, a tree view node represents the user's Pictures folder, so the pictures library [StorageFolder](/uwp/api/windows.storage.storagefolder) is assigned to the node's Content property.</span></span>

```csharp
StorageFolder picturesFolder = KnownFolders.PicturesLibrary;
TreeViewNode pictureNode = new TreeViewNode();
pictureNode.Content = picturesFolder;
```

```vb
Dim picturesFolder As StorageFolder = KnownFolders.PicturesLibrary
Dim pictureNode As New TreeViewNode With {.Content = picturesFolder}
```

<span data-ttu-id="4d5cd-195">Sie können eine [DataTemplate](/uwp/api/windows.ui.xaml.datatemplate) angeben, um festzulegen, wie das Datenelement in der Strukturansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-195">You can provide a [DataTemplate](/uwp/api/windows.ui.xaml.datatemplate) to specify how the data item is displayed in the tree view.</span></span>

> [!NOTE]
> <span data-ttu-id="4d5cd-196">In Windows10, Version 1803, müssen Sie Vorlage für das TreeView-Steuerelement umschreiben und eine benutzerdefinierte ItemTemplate festlegen, falls der Inhalt keine Zeichenfolge ist.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-196">In Windows 10, version 1803, you have to retemplate the TreeView control and specify a custom ItemTemplate if your content is not a string.</span></span> <span data-ttu-id="4d5cd-197">Weitere Informationen finden Sie im vollständigen Beispiel am Anfang dieses Artikels.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-197">For more info, see the full example at the end of this article.</span></span> <span data-ttu-id="4d5cd-198">In späteren Versionen wird festlegen Sie die [TreeView.ItemTemplate](/uwp/api/windows.ui.xaml.controls.treeview.itemtemplate) -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-198">In later versions, set the [TreeView.ItemTemplate](/uwp/api/windows.ui.xaml.controls.treeview.itemtemplate) property.</span></span>

### <a name="item-container-style"></a><span data-ttu-id="4d5cd-199">Elementcontainerstil</span><span class="sxs-lookup"><span data-stu-id="4d5cd-199">Item container style</span></span>

<span data-ttu-id="4d5cd-200">An, ob Sie die ItemsSource oder RootNodes, die eigentlichen Elemente zur Anzeige von jedem Knoten – verwenden den "Container" bezeichnet – ist ein [Objekte in der Strukturansicht](/uwp/api/windows.ui.xaml.controls.treeviewitem) -Objekt.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-200">Whether you use ItemsSource or RootNodes, the actual elements used to display each node – called the "container" – is a [TreeViewItem](/uwp/api/windows.ui.xaml.controls.treeviewitem) object.</span></span> <span data-ttu-id="4d5cd-201">Sie können den Container mit der Strukturansicht formatieren ItemContainerStyle oder ItemContainerStyleSelector Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-201">You can style the container using the TreeView's ItemContainerStyle or ItemContainerStyleSelector properties.</span></span>

### <a name="item-template-selectors"></a><span data-ttu-id="4d5cd-202">Element Vorlage Selektoren</span><span class="sxs-lookup"><span data-stu-id="4d5cd-202">Item template selectors</span></span>

<span data-ttu-id="4d5cd-203">Sie können auch eine andere Datenvorlage für Ansichtselemente Struktur basierend auf dem Typ des Elements festlegen.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-203">You can choose to set a different DataTemplate for the tree view items based on the type of item.</span></span> <span data-ttu-id="4d5cd-204">In einer app für den Datei-Explorer, könnten Sie beispielsweise eine Datenvorlage für Ordner und einen weiteren für Dateien verwenden.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-204">For example, in a file explorer app, you could use one data template for folders, and another for files.</span></span>

![Ordner und Dateien, die mit unterschiedlichen Datenvorlagen](images/treeview-icons.png)

<span data-ttu-id="4d5cd-206">Hier ist ein Beispiel für das Erstellen und verwenden Sie ein elementvorlagenselektor.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-206">Here is an example of how to create and use an item template selector.</span></span>

```xaml
<Page.Resources>
    <DataTemplate x:Key="FolderTemplate" x:DataType="local:ExplorerItem">
        <TreeViewItem ItemsSource="{x:Bind Children}">
            <StackPanel Orientation="Horizontal">
                <Image Width="20" Source="Assets/folder.png"/>
                <TextBlock Text="{x:Bind Name}" />
            </StackPanel>
        </TreeViewItem>
    </DataTemplate>

    <DataTemplate x:Key="FileTemplate" x:DataType="local:ExplorerItem">
        <TreeViewItem>
            <StackPanel Orientation="Horizontal">
                <Image Width="20" Source="Assets/file.png"/>
                <TextBlock Text="{Binding Name}"/>
            </StackPanel>
        </TreeViewItem>
    </DataTemplate>

    <local:ExplorerItemTemplateSelector
            x:Key="ExplorerItemTemplateSelector"
            FolderTemplate="{StaticResource FolderTemplate}"
            FileTemplate="{StaticResource FileTemplate}" />
</Page.Resources>

<Grid>
    <TreeView ItemsSource="{x:Bind DataSource}"
              ItemTemplateSelector="{StaticResource ExplorerItemTemplateSelector}"/>
</Grid>
```

```csharp
public class ExplorerItemTemplateSelector : DataTemplateSelector
{
    public DataTemplate FolderTemplate { get; set; }
    public DataTemplate FileTemplate { get; set; }

    protected override DataTemplate SelectTemplateCore(object item)
    {
        var explorerItem = (ExplorerItem)item;
        if (explorerItem.Type == ExplorerItem.ExplorerItemType.Folder) return FolderTemplate;

        return FileTemplate;
    }
}
```

## <a name="interacting-with-a-tree-view"></a><span data-ttu-id="4d5cd-207">Interagieren mit einer Strukturansicht</span><span class="sxs-lookup"><span data-stu-id="4d5cd-207">Interacting with a tree view</span></span>

<span data-ttu-id="4d5cd-208">Sie können eine Strukturansicht konfigurieren, damit Benutzer auf verschiedene Weise mit ihr interagieren können:</span><span class="sxs-lookup"><span data-stu-id="4d5cd-208">You can configure a tree view to let a user interact with it in several different ways:</span></span>

- <span data-ttu-id="4d5cd-209">Knoten erweitern oder reduzieren</span><span class="sxs-lookup"><span data-stu-id="4d5cd-209">expand or collapse nodes</span></span>
- <span data-ttu-id="4d5cd-210">Einfach- oder Mehrfachauswahlelemente</span><span class="sxs-lookup"><span data-stu-id="4d5cd-210">single- or multi-select items</span></span>
- <span data-ttu-id="4d5cd-211">Element durch Klicken aufrufen</span><span class="sxs-lookup"><span data-stu-id="4d5cd-211">click to invoke an item</span></span>

### <a name="expandcollapse"></a><span data-ttu-id="4d5cd-212">Erweitern/Reduzieren</span><span class="sxs-lookup"><span data-stu-id="4d5cd-212">Expand/collapse</span></span>

<span data-ttu-id="4d5cd-213">Jeder Strukturknoten, der über untergeordnete Elementen verfügt, kann durch Klicken auf das Erweitern/Reduzieren-Symbol erweitert oder reduziert werden.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-213">Any tree view node that has children can always be expanded or collapsed by clicking the expand/collapse glyph.</span></span> <span data-ttu-id="4d5cd-214">Knoten lassen sich auch programmgesteuert erweitern oder reduzieren und reagieren, wenn der Zustand eines Knotens geändert wird.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-214">You can also expand or collapse a node programmatically, and respond when a node changes state.</span></span>

#### <a name="expandcollapse-a-node-programmatically"></a><span data-ttu-id="4d5cd-215">Programmgesteuertes Erweitern/Reduzieren von Knoten</span><span class="sxs-lookup"><span data-stu-id="4d5cd-215">Expand/collapse a node programmatically</span></span>

<span data-ttu-id="4d5cd-216">Es gibt 2 Methoden den Knoten einer Strukturansicht in Ihrem Code zu erweitern oder zu reduzieren.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-216">There are 2 ways you can expand or collapse a tree view node in your code.</span></span>

- <span data-ttu-id="4d5cd-217">Die [TreeView](/uwp/api/windows.ui.xaml.controls.treeview)-Klasse verfügt über die Methoden [Reduzieren](/uwp/api/windows.ui.xaml.controls.treeview.collapse) und [Erweitern](/uwp/api/windows.ui.xaml.controls.treeview.expand).</span><span class="sxs-lookup"><span data-stu-id="4d5cd-217">The [TreeView](/uwp/api/windows.ui.xaml.controls.treeview) class has the [Collapse](/uwp/api/windows.ui.xaml.controls.treeview.collapse) and [Expand](/uwp/api/windows.ui.xaml.controls.treeview.expand) methods.</span></span> <span data-ttu-id="4d5cd-218">Wenn Sie diese Methoden aufrufen, übergeben Sie den TreeViewNode, den Sie erweitern oder reduzieren möchten.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-218">When you call these methods, you pass in the TreeViewNode that you want to expand or collapse.</span></span>

- <span data-ttu-id="4d5cd-219">Jeder [TreeViewNode](/uwp/api/windows.ui.xaml.controls.treeviewnode) verfügt über die Eigenschaft [IsExpanded](/uwp/api/windows.ui.xaml.controls.treeviewnode.isexpanded).</span><span class="sxs-lookup"><span data-stu-id="4d5cd-219">Each [TreeViewNode](/uwp/api/windows.ui.xaml.controls.treeviewnode) has the [IsExpanded](/uwp/api/windows.ui.xaml.controls.treeviewnode.isexpanded) property.</span></span> <span data-ttu-id="4d5cd-220">Mit dieser Eigenschaft können Sie den Status eines Knotens überprüfen oder ihn so festlegen, dass sein Zustand geändert wird.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-220">You can use this property to check the state of a node, or set it to change the state.</span></span> <span data-ttu-id="4d5cd-221">Diese Eigenschaft lässt sich auch in XAML einstellen, um den Anfangszustand eines Knotens festzulegen.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-221">You can also set this property in XAML to set the initial state of a node.</span></span>

### <a name="fill-a-node-when-its-expanding"></a><span data-ttu-id="4d5cd-222">Ausfüllen eines Knotens, wenn er erweitert wird</span><span class="sxs-lookup"><span data-stu-id="4d5cd-222">Fill a node when it's expanding</span></span>

<span data-ttu-id="4d5cd-223">Sie müssen möglicherweise eine große Anzahl von Knoten in der Strukturansicht anzeigen, oder Sie wissen möglicherweise nicht vorab, wie viele Knoten diese aufweisen wird.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-223">You might need to show a large number of nodes in your tree view, or you might not know ahead of time how many nodes it will have.</span></span> <span data-ttu-id="4d5cd-224">Das TreeView-Steuerelement ist nicht virtualisiert, damit Sie Ressourcen verwalten können, indem Sie jeden Knoten ausfüllen, wenn er erweitert wird, und die untergeordneten Knoten entfernen, wenn sie reduziert werden.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-224">The TreeView control is not virtualized, so you can manage resources by filling each node as it's expanded, and removing the child nodes when it's collapsed.</span></span>

<span data-ttu-id="4d5cd-225">Behandeln Sie das [Erweitern](/uwp/api/windows.ui.xaml.controls.treeview.expand)-Ereignis und verwenden Sie die [HasUnrealizedChildren](/uwp/api/windows.ui.xaml.controls.treeviewnode.hasunrealizedchildren) -Eigenschaft, um einem Knoten untergeordnete Elemente hinzuzufügen, wenn er erweitert wird.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-225">Handle the [Expanding](/uwp/api/windows.ui.xaml.controls.treeview.expand) event and use the [HasUnrealizedChildren](/uwp/api/windows.ui.xaml.controls.treeviewnode.hasunrealizedchildren) property to add children to a node when it's being expanded.</span></span> <span data-ttu-id="4d5cd-226">Die HasUnrealizedChildren-Eigenschaft gibt an, ob der Knoten ausgefüllt werden muss oder ob dessen Sammlung der untergeordneten Elemente bereits aufgefüllt wurde.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-226">The HasUnrealizedChildren property indicates whether the node needs to be filled, or if its Children collection has already been populated.</span></span> <span data-ttu-id="4d5cd-227">Es ist wichtig zu beachten, dass der TreeViewNode nicht diesen Wert festlegen, müssen Sie es in Ihrem app Code zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-227">It's important to remember that the TreeViewNode doesn't set this value, you need to manage it in your app code.</span></span>

<span data-ttu-id="4d5cd-228">Im Folgenden finden Sie ein Beispiel für diese verwendeten APIs.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-228">Here's an example of these APIs in use.</span></span> <span data-ttu-id="4d5cd-229">Der vollständige Beispielcode ist am Ende dieses Artikels aufgeführt, darunter die Implementierung des „FillTreeNode”.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-229">See the complete example code at the end of this article for context, including the implemetation of 'FillTreeNode'.</span></span>

```csharp
private void SampleTreeView_Expanding(TreeView sender, TreeViewExpandingEventArgs args)
{
    if (args.Node.HasUnrealizedChildren)
    {
        FillTreeNode(args.Node);
    }
}
```

```vb
Private Sub SampleTreeView_Expanding(sender As TreeView, args As TreeViewExpandingEventArgs)
    If args.Node.HasUnrealizedChildren Then
        FillTreeNode(args.Node)
    End If
End Sub
```

<span data-ttu-id="4d5cd-230">Es ist nicht erforderlich, Sie können jedoch auch das [Reduziert](/uwp/api/windows.ui.xaml.controls.treeview.collapsed)-Ereignis behandeln und die untergeordneten Knoten entfernen, wenn der übergeordnete Knoten geschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-230">It's not required, but you might want to also handle the [Collapsed](/uwp/api/windows.ui.xaml.controls.treeview.collapsed) event and remove the child nodes when the parent node is closed.</span></span> <span data-ttu-id="4d5cd-231">Dies kann wichtig sein, wenn die Strukturansicht viele Knoten aufweist oder die Knotendaten viele Ressourcen nutzen.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-231">This can be important if your tree view has many nodes, or if the node data uses a lot of resources.</span></span> <span data-ttu-id="4d5cd-232">Berücksichtigen Sie potenzielle Leistungseinbußen durch das Ausfüllen eines Knotens bei jedem Öffnen im Vergleich zur Beibehaltung der untergeordneten Elemente an einem geschlossenen Knoten.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-232">You should consider the performance impact of filling a node each time it's opened versus leaving the children on a closed node.</span></span> <span data-ttu-id="4d5cd-233">Welche Option jeweils geeignet ist, hängt von Ihrer App ab.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-233">The best option will depend on your app.</span></span>

<span data-ttu-id="4d5cd-234">Nachfolgend finden Sie ein Beispiel für einen Handler für das Reduziert-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-234">Here's an example of a handler for the Collapsed event.</span></span>

```csharp
private void SampleTreeView_Collapsed(TreeView sender, TreeViewCollapsedEventArgs args)
{
    args.Node.Children.Clear();
    args.Node.HasUnrealizedChildren = true;
}
```

```vb
Private Sub SampleTreeView_Collapsed(sender As TreeView, args As TreeViewCollapsedEventArgs)
    args.Node.Children.Clear()
    args.Node.HasUnrealizedChildren = True
End Sub
```

### <a name="invoking-an-item"></a><span data-ttu-id="4d5cd-235">Aufrufen eines Elements</span><span class="sxs-lookup"><span data-stu-id="4d5cd-235">Invoking an item</span></span>

<span data-ttu-id="4d5cd-236">Ein Benutzer kann eine Aktion (behandelt das Element wie eine Schaltfläche) aufrufen, statt das Element auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-236">A user can invoke an action (treating the item like a button) instead of selecting the item.</span></span> <span data-ttu-id="4d5cd-237">Sie behandeln das [ItemInvoked](/uwp/api/windows.ui.xaml.controls.treeview.iteminvoked)-Ereignis, um auf diese Benutzerinteraktion zu reagieren.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-237">You handle the [ItemInvoked](/uwp/api/windows.ui.xaml.controls.treeview.iteminvoked) event to respond to this user interaction.</span></span>

> [!NOTE]
> <span data-ttu-id="4d5cd-238">Im Gegensatz zur ListView, die über die [IsItemClickEnabled](/uwp/api/windows.ui.xaml.controls.listviewbase.isitemclickenabled)-Eigenschaft verfügt, ist das Aufrufen eines Elements für die Strukturansicht immer aktiviert.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-238">Unlike ListView, which has the [IsItemClickEnabled](/uwp/api/windows.ui.xaml.controls.listviewbase.isitemclickenabled) property, invoking an item is always enabled on the tree view.</span></span> <span data-ttu-id="4d5cd-239">Sie können weiterhin auswählen, ob das Ereignis behandelt werden soll oder nicht.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-239">You can still choose whether to handle the event or not.</span></span>

**<span data-ttu-id="4d5cd-240">[TreeViewItemInvokedEventArgs](/uwp/api/windows.ui.xaml.controls.treeviewiteminvokedeventargs)-Klasse</span><span class="sxs-lookup"><span data-stu-id="4d5cd-240">[TreeViewItemInvokedEventArgs](/uwp/api/windows.ui.xaml.controls.treeviewiteminvokedeventargs) class</span></span>**

<span data-ttu-id="4d5cd-241">Die ItemInvoked-Ereignisargumente ermöglichen Ihnen den Zugriff auf das aufgerufene Element.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-241">The ItemInvoked event args give you access to the invoked item.</span></span> <span data-ttu-id="4d5cd-242">Die [InvokedItem](/uwp/api/windows.ui.xaml.controls.treeviewiteminvokedeventargs.invokeditem)-Eigenschaft verfügt über den Knoten, der aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-242">The [InvokedItem](/uwp/api/windows.ui.xaml.controls.treeviewiteminvokedeventargs.invokeditem) property has the node that was invoked.</span></span> <span data-ttu-id="4d5cd-243">Sie können eine Umwandlung in TreeViewNode durchführen, um das Datenelement aus der TreeViewNode.Content-Eigenschaft abzurufen.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-243">You can cast it to TreeViewNode and get the data item from the TreeViewNode.Content property.</span></span>

<span data-ttu-id="4d5cd-244">Nachfolgend finden Sie ein Beispiel für einen ItemInvoked-Ereignishandler.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-244">Here's an example of an ItemInvoked event handler.</span></span> <span data-ttu-id="4d5cd-245">Das Datenelement ist ein [IStorageItem](/uwp/api/windows.storage.istorageitem), und in diesem Beispiel werden lediglich einige Informationen über die Datei und die Struktur angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-245">The data item is an [IStorageItem](/uwp/api/windows.storage.istorageitem), and this example just displays some info about the file and tree.</span></span> <span data-ttu-id="4d5cd-246">Auch wenn der Knoten ein Ordnerknoten ist, es erweitert oder reduziert den Knoten gleichzeitig.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-246">Also, if the node is a folder node, it expands or collapses the node at the same time.</span></span> <span data-ttu-id="4d5cd-247">Andernfalls wird der Knoten nur dann erweitert oder reduziert, wenn auf die Chevron-Schaltfläche geklickt wird.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-247">Otherwise, the node expands or collapses only when the chevron is clicked.</span></span>

```csharp
private void SampleTreeView_ItemInvoked(TreeView sender, TreeViewItemInvokedEventArgs args)
{
    var node = args.InvokedItem as TreeViewNode;
    if (node.Content is IStorageItem item)
    {
        FileNameTextBlock.Text = item.Name;
        FilePathTextBlock.Text = item.Path;
        TreeDepthTextBlock.Text = node.Depth.ToString();

        if (node.Content is StorageFolder)
        {
            node.IsExpanded = !node.IsExpanded;
        }
    }
}
```

```vb
Private Sub SampleTreeView_ItemInvoked(sender As TreeView, args As TreeViewItemInvokedEventArgs)
    Dim node = TryCast(args.InvokedItem, TreeViewNode)
    Dim item = TryCast(node.Content, IStorageItem)
    If item IsNot Nothing Then
        FileNameTextBlock.Text = item.Name
        FilePathTextBlock.Text = item.Path
        TreeDepthTextBlock.Text = node.Depth.ToString()
        If TypeOf node.Content Is StorageFolder Then
            node.IsExpanded = Not node.IsExpanded
        End If
    End If
End Sub
```

### <a name="item-selection"></a><span data-ttu-id="4d5cd-248">Elementauswahl</span><span class="sxs-lookup"><span data-stu-id="4d5cd-248">Item selection</span></span>

<span data-ttu-id="4d5cd-249">Das TreeView-Steuerelement unterstützt sowohl die Einzelauswahl als auch die Mehrfachauswahl.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-249">The TreeView control supports both single-selection and multi-selection.</span></span> <span data-ttu-id="4d5cd-250">Die Auswahl von Knoten ist standardmäßig deaktiviert, Sie können die [TreeView.SelectionMode](/uwp/api/windows.ui.xaml.controls.treeview.selectionmode)-Eigenschaft jedoch festlegen, um die Auswahl von Knoten zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-250">By default, selection of nodes is turned off, but you can set the [TreeView.SelectionMode](/uwp/api/windows.ui.xaml.controls.treeview.selectionmode) property to allow selection of nodes.</span></span> <span data-ttu-id="4d5cd-251">Die [TreeViewSelectionMode](/uwp/api/windows.ui.xaml.controls.treeviewselectionmode)-Werte sind **Keine**, **Einzelne** und **Mehrere**.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-251">The [TreeViewSelectionMode](/uwp/api/windows.ui.xaml.controls.treeviewselectionmode) values are **None**, **Single**, and **Multiple**.</span></span>

#### <a name="multiple-selection"></a><span data-ttu-id="4d5cd-252">Mehrfachauswahl</span><span class="sxs-lookup"><span data-stu-id="4d5cd-252">Multiple selection</span></span>

<span data-ttu-id="4d5cd-253">Wenn mehrere Auswahl aktiviert ist, wird ein Kontrollkästchen neben jedem Strukturknoten angezeigt und ausgewählte Elemente werden hervorgehoben.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-253">When multiple selection is enabled, a checkbox is shown next to each tree view node, and selected items are highlighted.</span></span> <span data-ttu-id="4d5cd-254">Ein Benutzer kann ein Element mithilfe eines Kontrollkästchens aktivieren oder deaktivieren. Das Element kann weiterhin aufgerufen werden, indem darauf geklickt wird.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-254">A user can select or de-select an item by using the checkbox; clicking the item still causes it to be invoked.</span></span>

<span data-ttu-id="4d5cd-255">Auswählen oder die Auswahl eines übergeordneter Knotens wird aktivieren oder Deaktivieren aller untergeordneten Elemente unter diesem Knoten.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-255">Selecting or de-selecting a parent node will select or de-select all children under that node.</span></span> <span data-ttu-id="4d5cd-256">Wenn einige, aber nicht alle, die untergeordneten Elemente unter einem übergeordneten Knoten ausgewählt werden, das Kontrollkästchen für den übergeordneten Knoten wird angezeigt als unbestimmt (mit einer Blackbox ausgefüllt).</span><span class="sxs-lookup"><span data-stu-id="4d5cd-256">If some, but not all, of the children under a parent node are selected, the checkbox for the parent node is shown as indeterminate (filled with a black box).</span></span>

![Mehrfachauswahl in einer Strukturansicht](images/treeview-selection.png)

<span data-ttu-id="4d5cd-258">Auswählen oder die Auswahl eines übergeordneter Knotens wird aktivieren oder Deaktivieren aller untergeordneten Elemente unter diesem Knoten.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-258">Selecting or de-selecting a parent node will select or de-select all children under that node.</span></span> <span data-ttu-id="4d5cd-259">Wenn einige, aber nicht alle, die untergeordneten Elemente unter einem übergeordneten Knoten ausgewählt werden, das Kontrollkästchen für den übergeordneten Knoten wird angezeigt als unbestimmt (mit einer Blackbox ausgefüllt).</span><span class="sxs-lookup"><span data-stu-id="4d5cd-259">If some, but not all, of the children under a parent node are selected, the checkbox for the parent node is shown as indeterminate (filled with a black box).</span></span>

![Mehrfachauswahl in einer Strukturansicht](images/treeview-selection.png)

<span data-ttu-id="4d5cd-261">Ausgewählte Knoten werden der [SelectedNodes](/uwp/api/windows.ui.xaml.controls.treeview.selectednodes)-Sammlung der Strukturansicht hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-261">Selected nodes are added to the tree view's [SelectedNodes](/uwp/api/windows.ui.xaml.controls.treeview.selectednodes) collection.</span></span> <span data-ttu-id="4d5cd-262">Sie können die [SelectAll](/uwp/api/windows.ui.xaml.controls.treeview.selectall)-Methode aufrufen, um alle Knoten in einer Strukturansicht auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-262">You can call the [SelectAll](/uwp/api/windows.ui.xaml.controls.treeview.selectall) method to select all the nodes in a tree view.</span></span>

> [!NOTE]
> <span data-ttu-id="4d5cd-263">Wenn Sie **SelectAll** aufrufen, werden alle realisierten Knoten ungeachtet der SelectionMode ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-263">If you call **SelectAll**, all realized nodes are selected, regardless of the SelectionMode.</span></span> <span data-ttu-id="4d5cd-264">Um ein einheitliches Benutzererlebnis zu ermöglichen, sollten Sie SelectAll nur dann aufrufen, wenn SelectionMode auf **Mehrere** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-264">To provide a consistent user experience, you should only call SelectAll if SelectionMode is **Multiple**.</span></span>

#### <a name="selection-and-realizedunrealized-nodes"></a><span data-ttu-id="4d5cd-265">Auswahl und realisierte/nicht realisierte Knoten</span><span class="sxs-lookup"><span data-stu-id="4d5cd-265">Selection and realized/unrealized nodes</span></span>

<span data-ttu-id="4d5cd-266">Wenn die Strukturansicht nicht realisierte Knoten aufweist, werden sie bei der Auswahl nicht berücksichtigt.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-266">If your tree view has unrealized nodes, they are not taken into account for selection.</span></span> <span data-ttu-id="4d5cd-267">Beachten Sie bei der Auswahl mit nicht realisierten Knoten Folgendes.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-267">Here are some things you need to keep in mind regarding selection with unrealized nodes.</span></span>

- <span data-ttu-id="4d5cd-268">Wenn ein Benutzer einen übergeordneten Knoten auswählt, werden auch alle realisierten untergeordneten Elemente ausgewählt, die sich unter diesem übergeordneten Element befinden.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-268">If a user selects a parent node, all the realized children under that parent are also selected.</span></span> <span data-ttu-id="4d5cd-269">Wenn alle untergeordneten Knoten ausgewählt werden, wird der übergeordnete Knoten entsprechend ebenfalls ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-269">Similarly, if all the child nodes are selected, the parent node also becomes selected.</span></span>
- <span data-ttu-id="4d5cd-270">Bei der SelectAll-Methode werden der SelectedNodes-Sammlung nur realisierte Knoten hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-270">The SelectAll method only adds realized nodes to the SelectedNodes collection.</span></span>
- <span data-ttu-id="4d5cd-271">Wenn ein übergeordneter Knoten mit nicht realisierten untergeordneten Elementen ausgewählt wird, werden die untergeordneten Elemente ausgewählt, sobald sie realisiert werden.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-271">If a parent node with unrealized children is selected, the children will be selected as they are realized.</span></span>

## <a name="code-examples"></a><span data-ttu-id="4d5cd-272">Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="4d5cd-272">Code examples</span></span>

### <a name="tree-view-using-xaml"></a><span data-ttu-id="4d5cd-273">Strukturansicht mit XAML</span><span class="sxs-lookup"><span data-stu-id="4d5cd-273">Tree view using XAML</span></span>

<span data-ttu-id="4d5cd-274">Dieses Beispiel zeigt, wie in XAML eine einfache Struktur für eine Strukturansicht erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-274">This example shows how to create a simple tree view structure in XAML.</span></span> <span data-ttu-id="4d5cd-275">Die Strukturansicht zeigt in Kategorien angeordnete Eissorten und Garnierungen, die der Benutzer auswählen kann.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-275">The tree view shows ice cream flavors and toppings that the user can choose from, arranged in categories.</span></span> <span data-ttu-id="4d5cd-276">Die Mehrfachauswahl ist aktiviert, und wenn der Benutzer auf eine Schaltfläche klickt, werden die SelectedItems in der Haupt-App-UI angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-276">Multi-selection is enabled, and when the user clicks a button, the SelectedItems are displayed in the main app UI.</span></span>

```xaml
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}" Padding="100">
    <SplitView IsPaneOpen="True"
               DisplayMode="Inline"
               OpenPaneLength="296">
        <SplitView.Pane>
            <TreeView x:Name="DessertTree" SelectionMode="Multiple">
                <TreeView.RootNodes>
                    <TreeViewNode Content="Flavors" IsExpanded="True">
                        <TreeViewNode.Children>
                            <TreeViewNode Content="Vanilla"/>
                            <TreeViewNode Content="Strawberry"/>
                            <TreeViewNode Content="Chocolate"/>
                        </TreeViewNode.Children>
                    </TreeViewNode>

                    <TreeViewNode Content="Toppings">
                        <TreeViewNode.Children>
                            <TreeViewNode Content="Candy">
                                <TreeViewNode.Children>
                                    <TreeViewNode Content="Chocolate"/>
                                    <TreeViewNode Content="Mint"/>
                                    <TreeViewNode Content="Sprinkles"/>
                                </TreeViewNode.Children>
                            </TreeViewNode>
                            <TreeViewNode Content="Fruits">
                                <TreeViewNode.Children>
                                    <TreeViewNode Content="Mango"/>
                                    <TreeViewNode Content="Peach"/>
                                    <TreeViewNode Content="Kiwi"/>
                                </TreeViewNode.Children>
                            </TreeViewNode>
                            <TreeViewNode Content="Berries">
                                <TreeViewNode.Children>
                                    <TreeViewNode Content="Strawberry"/>
                                    <TreeViewNode Content="Blueberry"/>
                                    <TreeViewNode Content="Blackberry"/>
                                </TreeViewNode.Children>
                            </TreeViewNode>
                        </TreeViewNode.Children>
                    </TreeViewNode>
                </TreeView.RootNodes>
            </TreeView>
        </SplitView.Pane>

        <StackPanel Grid.Column="1" Margin="12,0">
            <Button Content="Select all" Click="SelectAllButton_Click"/>
            <Button Content="Create order" Click="OrderButton_Click" Margin="0,12"/>
            <TextBlock Text="Your flavor selections:" Style="{StaticResource CaptionTextBlockStyle}"/>
            <TextBlock x:Name="FlavorList" Margin="0,0,0,12"/>
            <TextBlock Text="Your topping selections:" Style="{StaticResource CaptionTextBlockStyle}"/>
            <TextBlock x:Name="ToppingList"/>
        </StackPanel>
    </SplitView>
</Grid>
```

```csharp
private void OrderButton_Click(object sender, RoutedEventArgs e)
{
    FlavorList.Text = string.Empty;
    ToppingList.Text = string.Empty;

    foreach (TreeViewNode node in DessertTree.SelectedNodes)
    {
        if (node.Parent.Content?.ToString() == "Flavors")
        {
            FlavorList.Text += node.Content + "; ";
        }
        else if (node.HasChildren == false)
        {
            ToppingList.Text += node.Content + "; ";
        }
    }
}

private void SelectAllButton_Click(object sender, RoutedEventArgs e)
{
    if (DessertTree.SelectionMode == TreeViewSelectionMode.Multiple)
    {
        DessertTree.SelectAll();
    }
}
```

```vb
Private Sub OrderButton_Click(sender As Object, e As RoutedEventArgs)
    FlavorList.Text = String.Empty
    ToppingList.Text = String.Empty
    For Each node As TreeViewNode In DessertTree.SelectedNodes
        If node.Parent.Content?.ToString() = "Flavors" Then
            FlavorList.Text += node.Content & "; "
        ElseIf node.HasChildren = False Then
            ToppingList.Text += node.Content & "; "
        End If
    Next
End Sub

Private Sub SelectAllButton_Click(sender As Object, e As RoutedEventArgs)
    If DessertTree.SelectionMode = TreeViewSelectionMode.Multiple Then
        DessertTree.SelectAll()
    End If
End Sub
```

### <a name="tree-view-using-data-binding"></a><span data-ttu-id="4d5cd-277">Verwenden der Datenbindung Strukturansicht</span><span class="sxs-lookup"><span data-stu-id="4d5cd-277">Tree view using data binding</span></span>

<span data-ttu-id="4d5cd-278">Dieses Beispiel zeigt, wie Sie die gleichen Strukturansicht wie im vorherigen Beispiel zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-278">This example shows how to create the same tree view as the previous example.</span></span> <span data-ttu-id="4d5cd-279">Anstelle der Datenhierarchie in XAML zu erstellen, die Daten jedoch im Code erstellt und für die Strukturansicht ItemsSource-Eigenschaft gebunden.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-279">However, instead of creating the data hierarchy in XAML, the data is created in code and bound to the tree view's ItemsSource property.</span></span> <span data-ttu-id="4d5cd-280">(Im vorherigen Beispiel gezeigt Ereignishandler der Schaltfläche gelten für dieses Beispiel auch.)</span><span class="sxs-lookup"><span data-stu-id="4d5cd-280">(The button event handlers shown in the previous example apply to this example also.)</span></span>

```xaml
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}" Padding="100">
    <SplitView IsPaneOpen="True"
               DisplayMode="Inline"
               OpenPaneLength="296">
        <SplitView.Pane>
            <TreeView Name="DessertTree"
                      SelectionMode="Multiple"
                      ItemsSource="{x:Bind DataSource}">
                <TreeView.ItemTemplate>
                    <DataTemplate x:DataType="local:Item">
                        <TreeViewItem ItemsSource="{x:Bind Children}"
                                      Content="{x:Bind Name}"/>
                    </DataTemplate>
                </TreeView.ItemTemplate>
            </TreeView>
        </SplitView.Pane>

        <StackPanel Grid.Column="1" Margin="12,0">
            <Button Content="Select all" Click="SelectAllButton_Click"/>
            <Button Content="Create order" Click="OrderButton_Click" Margin="0,12"/>
            <TextBlock Text="Your flavor selections:" Style="{StaticResource CaptionTextBlockStyle}"/>
            <TextBlock x:Name="FlavorList" Margin="0,0,0,12"/>
            <TextBlock Text="Your topping selections:" Style="{StaticResource CaptionTextBlockStyle}"/>
            <TextBlock x:Name="ToppingList"/>
        </StackPanel>
    </SplitView>
</Grid>
```

```csharp
public sealed partial class MainPage : Page
{
    private ObservableCollection<Item> DataSource = new ObservableCollection<Item>();

    public MainPage()
    {
        this.InitializeComponent();
        DataSource = GetDessertData();
    }

    private ObservableCollection<Item> GetDessertData()
    {
        var list = new ObservableCollection<Item>();
        Item flavorsCategory = new Item()
        {
            Name = "Flavors",
            Children =
            {
                new Item() { Name = "Vanilla" },
                new Item() { Name = "Strawberry" },
                new Item() { Name = "Chocolate" }
            }
        };
        Item toppingsCategory = new Item()
        {
            Name = "Toppings",
            Children =
            {
                new Item()
                {
                    Name = "Candy",
                    Children =
                    {
                        new Item() { Name = "Chocolate" },
                        new Item() { Name = "Mint" },
                        new Item() { Name = "Sprinkles" }
                    }
                },
                new Item()
                {
                    Name = "Fruits",
                    Children =
                    {
                        new Item() { Name = "Mango" },
                        new Item() { Name = "Peach" },
                        new Item() { Name = "Kiwi" }
                    }
                },
                new Item()
                {
                    Name = "Berries",
                    Children =
                    {
                        new Item() { Name = "Strawberry" },
                        new Item() { Name = "Blueberry" },
                        new Item() { Name = "Blackberry" }
                    }
                }
            }
        };

        list.Add(flavorsCategory);
        list.Add(toppingsCategory);
        return list;
    }

    // Button event handlers...
}

public class Item
{
    public string Name { get; set; }
    public ObservableCollection<Item> Children { get; set; } = new ObservableCollection<Item>();

    public override string ToString()
    {
        return Name;
    }
}
```

### <a name="pictures-and-music-library-tree-view"></a><span data-ttu-id="4d5cd-281">Baumstruktur für Bild- und Musikbibliotheken</span><span class="sxs-lookup"><span data-stu-id="4d5cd-281">Pictures and Music Library tree view</span></span>

<span data-ttu-id="4d5cd-282">Dieses Beispiel zeigt, wie eine Strukturansicht erstellt wird, die den Inhalt und die Struktur der Bild- und Musikbibliotheken von Benutzern anzeigt.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-282">This example shows how to create a tree view that shows the contents and structure of the users Pictures and Music libraries.</span></span> <span data-ttu-id="4d5cd-283">Da die Anzahl der Elemente vorab nicht bekannt sein kann, wird jeder Knoten beim Erweitern gefüllt und beim Reduzieren geleert.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-283">The number of items can't be known ahead of time, so each node is filled when it's expanded, and emptied when it's collapsed.</span></span>

<span data-ttu-id="4d5cd-284">Eine benutzerdefinierte Elementvorlage wird verwendet, um die Datenelemente vom Typ [IStorageItem](/uwp/api/windows.storage.istorageitem) anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-284">A custom item template is used to display the data items, which are of type [IStorageItem](/uwp/api/windows.storage.istorageitem).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4d5cd-285">Für den Code in diesem Beispiel sind die Funktionen PicturesLibrary und MusicLibrary erforderlich.</span><span class="sxs-lookup"><span data-stu-id="4d5cd-285">The code in this example requires the picturesLibrary and musicLibrary capabilities.</span></span> <span data-ttu-id="4d5cd-286">Weitere Informationen zum Dateizugriff finden Sie unter [Berechtigungen für den Dateizugriff](../../files/file-access-permissions.md), [Aufzählen und Abfragen von Dateien und Ordnern](../../files/quickstart-listing-files-and-folders.md) und [Dateien und Ordner in den Musik-, Bild- und Videobibliotheken](../../files/quickstart-managing-folders-in-the-music-pictures-and-videos-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="4d5cd-286">For more info about file access, see [File access permissions](../../files/file-access-permissions.md), [Enumerate and query files and folders](../../files/quickstart-listing-files-and-folders.md), and [Files and folders in the Music, Pictures, and Videos libraries](../../files/quickstart-managing-folders-in-the-music-pictures-and-videos-libraries.md).</span></span>

```xaml
<Page
    x:Class="TreeViewApp1.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:TreeViewApp1"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d">
    <Page.Resources>
        <DataTemplate x:Key="TreeViewItemDataTemplate">
            <Grid Height="44">
                <TextBlock
                    Text="{Binding Content.DisplayName}"
                    HorizontalAlignment="Left"
                    VerticalAlignment="Center"
                    Style="{ThemeResource BodyTextBlockStyle}"/>
            </Grid>
        </DataTemplate>

        <Style TargetType="TreeView">
            <Setter Property="IsTabStop" Value="False" />
            <Setter Property="Template">
                <Setter.Value>
                    <ControlTemplate TargetType="TreeView">
                        <TreeViewList x:Name="ListControl"
                                      ItemTemplate="{StaticResource TreeViewItemDataTemplate}"
                                      ItemContainerStyle="{StaticResource TreeViewItemStyle}"
                                      CanDragItems="True"
                                      AllowDrop="True"
                                      CanReorderItems="True">
                            <TreeViewList.ItemContainerTransitions>
                                <TransitionCollection>
                                    <ContentThemeTransition />
                                    <ReorderThemeTransition />
                                    <EntranceThemeTransition IsStaggeringEnabled="False" />
                                </TransitionCollection>
                            </TreeViewList.ItemContainerTransitions>
                        </TreeViewList>
                    </ControlTemplate>
                </Setter.Value>
            </Setter>
        </Style>
    </Page.Resources>

    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
        <SplitView IsPaneOpen="True"
                   DisplayMode="Inline"
                   OpenPaneLength="296">
            <SplitView.Pane>
                <Grid>
                    <Grid.RowDefinitions>
                        <RowDefinition Height="Auto"/>
                        <RowDefinition/>
                    </Grid.RowDefinitions>
                    <Button Content="Refresh tree" Click="RefreshButton_Click" Margin="24,12"/>
                    <TreeView x:Name="sampleTreeView" Grid.Row="1" SelectionMode="Single"
                              Expanding="SampleTreeView_Expanding"
                              Collapsed="SampleTreeView_Collapsed"
                              ItemInvoked="SampleTreeView_ItemInvoked"/>
                </Grid>
            </SplitView.Pane>

            <StackPanel Grid.Column="1" Margin="12,72">
                <TextBlock Text="File name:" Style="{StaticResource CaptionTextBlockStyle}"/>
                <TextBlock x:Name="FileNameTextBlock" Margin="0,0,0,12"/>

                <TextBlock Text="File path:" Style="{StaticResource CaptionTextBlockStyle}"/>
                <TextBlock x:Name="FilePathTextBlock" Margin="0,0,0,12"/>

                <TextBlock Text="Tree depth:" Style="{StaticResource CaptionTextBlockStyle}"/>
                <TextBlock x:Name="TreeDepthTextBlock" Margin="0,0,0,12"/>
            </StackPanel>
        </SplitView>
    </Grid>
</Page>
```

```csharp
public MainPage()
{
    this.InitializeComponent();
    InitializeTreeView();
}

private void InitializeTreeView()
{
    // A TreeView can have more than 1 root node. The Pictures library
    // and the Music library will each be a root node in the tree.
    // Get Pictures library.
    StorageFolder picturesFolder = KnownFolders.PicturesLibrary;
    TreeViewNode pictureNode = new TreeViewNode();
    pictureNode.Content = picturesFolder;
    pictureNode.IsExpanded = true;
    pictureNode.HasUnrealizedChildren = true;
    sampleTreeView.RootNodes.Add(pictureNode);
    FillTreeNode(pictureNode);

    // Get Music library.
    StorageFolder musicFolder = KnownFolders.MusicLibrary;
    TreeViewNode musicNode = new TreeViewNode();
    musicNode.Content = musicFolder;
    musicNode.IsExpanded = true;
    musicNode.HasUnrealizedChildren = true;
    sampleTreeView.RootNodes.Add(musicNode);
    FillTreeNode(musicNode);
}

private async void FillTreeNode(TreeViewNode node)
{
    // Get the contents of the folder represented by the current tree node.
    // Add each item as a new child node of the node that's being expanded.

    // Only process the node if it's a folder and has unrealized children.
    StorageFolder folder = null;
    if (node.Content is StorageFolder && node.HasUnrealizedChildren == true)
    {
        folder = node.Content as StorageFolder;
    }
    else
    {
        // The node isn't a folder, or it's already been filled.
        return;
    }

    IReadOnlyList<IStorageItem> itemsList = await folder.GetItemsAsync();

    if (itemsList.Count == 0)
    {
        // The item is a folder, but it's empty. Leave HasUnrealizedChildren = true so
        // that the chevron appears, but don't try to process children that aren't there.
        return;
    }

    foreach (var item in itemsList)
    {
        var newNode = new TreeViewNode();
        newNode.Content = item;

        if (item is StorageFolder)
        {
            // If the item is a folder, set HasUnrealizedChildren to true. 
            // This makes the collapsed chevron show up.
            newNode.HasUnrealizedChildren = true;
        }
        else
        {
            // Item is StorageFile. No processing needed for this scenario.
        }
        node.Children.Add(newNode);
    }
    // Children were just added to this node, so set HasUnrealizedChildren to false.
    node.HasUnrealizedChildren = false;
}

private void SampleTreeView_Expanding(TreeView sender, TreeViewExpandingEventArgs args)
{
    if (args.Node.HasUnrealizedChildren)
    {
        FillTreeNode(args.Node);
    }
}

private void SampleTreeView_Collapsed(TreeView sender, TreeViewCollapsedEventArgs args)
{
    args.Node.Children.Clear();
    args.Node.HasUnrealizedChildren = true;
}

private void SampleTreeView_ItemInvoked(TreeView sender, TreeViewItemInvokedEventArgs args)
{
    var node = args.InvokedItem as TreeViewNode;
    if (node.Content is IStorageItem item)
    {
        FileNameTextBlock.Text = item.Name;
        FilePathTextBlock.Text = item.Path;
        TreeDepthTextBlock.Text = node.Depth.ToString();

        if (node.Content is StorageFolder)
        {
            node.IsExpanded = !node.IsExpanded;
        }
    }
}

private void RefreshButton_Click(object sender, RoutedEventArgs e)
{
    sampleTreeView.RootNodes.Clear();
    InitializeTreeView();
}
```

```vb
Public Sub New()
    InitializeComponent()
    InitializeTreeView()
End Sub

Private Sub InitializeTreeView()
    ' A TreeView can have more than 1 root node. The Pictures library
    ' and the Music library will each be a root node in the tree.
    ' Get Pictures library.
    Dim picturesFolder As StorageFolder = KnownFolders.PicturesLibrary
    Dim pictureNode As New TreeViewNode With {
        .Content = picturesFolder,
        .IsExpanded = True,
        .HasUnrealizedChildren = True
    }
    sampleTreeView.RootNodes.Add(pictureNode)
    FillTreeNode(pictureNode)

    ' Get Music library.
    Dim musicFolder As StorageFolder = KnownFolders.MusicLibrary
    Dim musicNode As New TreeViewNode With {
        .Content = musicFolder,
        .IsExpanded = True,
        .HasUnrealizedChildren = True
    }
    sampleTreeView.RootNodes.Add(musicNode)
    FillTreeNode(musicNode)
End Sub

Private Async Sub FillTreeNode(node As TreeViewNode)
    ' Get the contents of the folder represented by the current tree node.
    ' Add each item as a new child node of the node that's being expanded.

    ' Only process the node if it's a folder and has unrealized children.
    Dim folder As StorageFolder = Nothing
    If TypeOf node.Content Is StorageFolder AndAlso node.HasUnrealizedChildren Then
        folder = TryCast(node.Content, StorageFolder)
    Else
        ' The node isn't a folder, or it's already been filled.
        Return
    End If

    Dim itemsList As IReadOnlyList(Of IStorageItem) = Await folder.GetItemsAsync()
    If itemsList.Count = 0 Then
        ' The item is a folder, but it's empty. Leave HasUnrealizedChildren = true so
        ' that the chevron appears, but don't try to process children that aren't there.
        Return
    End If

    For Each item In itemsList
        Dim newNode As New TreeViewNode With {
            .Content = item
        }
        If TypeOf item Is StorageFolder Then
            ' If the item is a folder, set HasUnrealizedChildren to True.
            ' This makes the collapsed chevron show up.
            newNode.HasUnrealizedChildren = True
        Else
            ' Item is StorageFile. No processing needed for this scenario.
        End If
        node.Children.Add(newNode)
    Next

    ' Children were just added to this node, so set HasUnrealizedChildren to False.
    node.HasUnrealizedChildren = False
End Sub

Private Sub SampleTreeView_Expanding(sender As TreeView, args As TreeViewExpandingEventArgs)
    If args.Node.HasUnrealizedChildren Then
        FillTreeNode(args.Node)
    End If
End Sub

Private Sub SampleTreeView_Collapsed(sender As TreeView, args As TreeViewCollapsedEventArgs)
    args.Node.Children.Clear()
    args.Node.HasUnrealizedChildren = True
End Sub

Private Sub SampleTreeView_ItemInvoked(sender As TreeView, args As TreeViewItemInvokedEventArgs)
    Dim node = TryCast(args.InvokedItem, TreeViewNode)
    Dim item = TryCast(node.Content, IStorageItem)
    If item IsNot Nothing Then
        FileNameTextBlock.Text = item.Name
        FilePathTextBlock.Text = item.Path
        TreeDepthTextBlock.Text = node.Depth.ToString()
        If TypeOf node.Content Is StorageFolder Then
            node.IsExpanded = Not node.IsExpanded
        End If
    End If
End Sub

Private Sub RefreshButton_Click(sender As Object, e As RoutedEventArgs)
    sampleTreeView.RootNodes.Clear()
    InitializeTreeView()
End Sub
```

## <a name="related-articles"></a><span data-ttu-id="4d5cd-287">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="4d5cd-287">Related articles</span></span>

- [<span data-ttu-id="4d5cd-288">TreeView-Klasse</span><span class="sxs-lookup"><span data-stu-id="4d5cd-288">TreeView class</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.treeview)
- [<span data-ttu-id="4d5cd-289">ListView-Klasse</span><span class="sxs-lookup"><span data-stu-id="4d5cd-289">ListView class</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx)
- [<span data-ttu-id="4d5cd-290">ListView und GridView</span><span class="sxs-lookup"><span data-stu-id="4d5cd-290">ListView and GridView</span></span>](listview-and-gridview.md)
