---
author: Jwmsft
description: Verwenden Sie den Beispielcode zur Strukturansicht, um eine ausklappbare Struktur (einen ausklappbaren Baum) zu erzeugen.
title: Strukturansicht
label: Tree view
template: detail.hbs
ms.author: jimwalk
ms.localizationpriority: medium
pm-contact: predavid
design-contact: ksulliv
dev-contact: joyate
doc-status: Published
dev_langs:
- csharp
- vb
ms.openlocfilehash: 41e17d299e9bac34e58f3c8ffdffecff19ddac18
ms.sourcegitcommit: e020e9a4d947368a68e4eeba1eea65e9b3a725af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2018
ms.locfileid: "1924393"
---
# <a name="treeview"></a><span data-ttu-id="22a15-103">TreeView</span><span class="sxs-lookup"><span data-stu-id="22a15-103">TreeView</span></span>

<span data-ttu-id="22a15-104">Das XAML-Steuerelement TreeView ermöglicht eine Hierarchieauflistung mit Knoten, die das Aus- und Einblenden von geschachtelten Elementen erlauben.</span><span class="sxs-lookup"><span data-stu-id="22a15-104">The XAML TreeView control enables a hierarchical list with expanding and collapsing nodes that contain nested items.</span></span> <span data-ttu-id="22a15-105">Es kann verwendet werden, um eine Ordnerstruktur oder geschachtelte Beziehungen zwischen Elementen in der Benutzeroberfläche zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="22a15-105">It can be used to illustrate a folder structure or nested relationships in your UI.</span></span>

> <span data-ttu-id="22a15-106">**Wichtige APIs**: [TreeView-Klasse](/uwp/api/windows.ui.xaml.controls.treeview), [TreeViewNode-Klasse](/uwp/api/windows.ui.xaml.controls.treeviewnode)</span><span class="sxs-lookup"><span data-stu-id="22a15-106">**Important APIs**: [TreeView class](/uwp/api/windows.ui.xaml.controls.treeview), [TreeViewNode class](/uwp/api/windows.ui.xaml.controls.treeviewnode)</span></span>

<span data-ttu-id="22a15-107">Die TreeView-APIs unterstützen die folgenden Features:</span><span class="sxs-lookup"><span data-stu-id="22a15-107">The TreeView APIs support the following features:</span></span>

- <span data-ttu-id="22a15-108">Schachtelung von N Ebenen</span><span class="sxs-lookup"><span data-stu-id="22a15-108">N-level nesting</span></span>
- <span data-ttu-id="22a15-109">Aus-/Einblenden von Knoten</span><span class="sxs-lookup"><span data-stu-id="22a15-109">Expanding/collapsing of nodes</span></span>
- <span data-ttu-id="22a15-110">Auswahl einzelner oder mehreren Knoten</span><span class="sxs-lookup"><span data-stu-id="22a15-110">Selection of single or multiple nodes</span></span>

## <a name="is-this-the-right-control"></a><span data-ttu-id="22a15-111">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="22a15-111">Is this the right control?</span></span>

- <span data-ttu-id="22a15-112">Verwenden Sie eine Strukturansicht, wenn Elemente geschachtelte Elemente haben, und dann, wenn es wichtig ist, die hierarchische Beziehung zwischen Elementen und ihren gleichgestellten Elementen und Knoten zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="22a15-112">Use a TreeView when items have nested list items, and if it is important to illustrate the hierarchical relationship of items to their peers and nodes.</span></span>

- <span data-ttu-id="22a15-113">Vermeiden Sie Strukturansicht, wenn die geschachtelte Beziehung eines Elements nicht im Vordergrund steht.</span><span class="sxs-lookup"><span data-stu-id="22a15-113">Avoid using TreeView if highlighting the nested relationship of an item is not a priority.</span></span> <span data-ttu-id="22a15-114">Für die meisten Drilldown-Szenarios eignet sich eine normale ListView</span><span class="sxs-lookup"><span data-stu-id="22a15-114">For most drill-in scenarios, a regular list view is appropriate</span></span>

## <a name="treeview-ui"></a><span data-ttu-id="22a15-115">TreeView-UI</span><span class="sxs-lookup"><span data-stu-id="22a15-115">TreeView UI</span></span>

<span data-ttu-id="22a15-116">Die Strukturansicht verwendet eine Kombination aus Einzügen und Symbolen, um die geschachtelte Beziehung zwischen Ordnern und übergeordneten Knoten bzw. Nicht-Ordnern und untergeordneten Knoten darzustellen.</span><span class="sxs-lookup"><span data-stu-id="22a15-116">The tree view uses a combination of indentation and icons to represent the nested relationship between folder/parent nodes and non-folder/child nodes.</span></span> <span data-ttu-id="22a15-117">Ausgeblendete Knoten verwenden ein Chevron, welches nach rechts zeigt, während eingeblendete Knoten ein Chevron verwenden, das nach unten zeigt.</span><span class="sxs-lookup"><span data-stu-id="22a15-117">Collapsed nodes use a chevron pointing to the right, and expanded nodes use a chevron pointing down.</span></span>

![Das Chevronsymbol in der Strukturansicht](images/treeview_chevron.png)

<span data-ttu-id="22a15-119">Sie können ein Symbol in die Datenvorlage für Strukturansichtselemente einschließen, um Knoten darzustellen.</span><span class="sxs-lookup"><span data-stu-id="22a15-119">You can include an icon in the tree view item data template to represent nodes.</span></span> <span data-ttu-id="22a15-120">In diesem Fall sollten Sie ein Ordnersymbol nur für Knoten verwenden, die literale Ordner wie etwa die Ordnerstruktur auf einem Datenträger darstellen.</span><span class="sxs-lookup"><span data-stu-id="22a15-120">If you do this, you should use a folder icon only for nodes that represent literal folders, such as the folder structure on a disk.</span></span>

![Das Chevron- und Ordnersymbol zusammen in einer Strukturansicht](images/treeview_chevron_folder.png)

## <a name="create-a-tree-view"></a><span data-ttu-id="22a15-122">Erstellen einer Strukturansicht</span><span class="sxs-lookup"><span data-stu-id="22a15-122">Create a tree view</span></span>

<span data-ttu-id="22a15-123">Um eine Strukturansicht zu erstellen, verwenden Sie ein [Strukturansicht](/uwp/api/windows.ui.xaml.controls.treeview)-Steuerelement und eine Hierarchie von [TreeViewNode](/uwp/api/windows.ui.xaml.controls.treeviewnode)-Objekten.</span><span class="sxs-lookup"><span data-stu-id="22a15-123">To create a tree view, you use a [TreeView](/uwp/api/windows.ui.xaml.controls.treeview) control and a hierarchy of [TreeViewNode](/uwp/api/windows.ui.xaml.controls.treeviewnode) objects.</span></span> <span data-ttu-id="22a15-124">Sie erstellen die Kontenhierarchie, indem Sie der RootNodes-Sammlung des Strukturansicht-Steuerelements mindestens einen Stammknoten hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="22a15-124">You create the node hierarchy by adding one or more root nodes to the TreeView control’s RootNodes collection.</span></span> <span data-ttu-id="22a15-125">Der Sammlung der untergeordneten Elemente der einzelnen TreeViewNodes können dann weitere Knoten hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="22a15-125">Each TreeViewNode can then have more nodes added to its Children collection.</span></span> <span data-ttu-id="22a15-126">Sie können Knoten der Strukturansicht auf jede beliebigen Tiefe schachteln.</span><span class="sxs-lookup"><span data-stu-id="22a15-126">You can nest tree view nodes to whatever depth you require.</span></span>

<span data-ttu-id="22a15-127">Im Folgenden finden Sie ein Beispiel für eine einfache in XAML deklarierte Strukturansicht.</span><span class="sxs-lookup"><span data-stu-id="22a15-127">Here's an example of a simple tree view declared in XAML.</span></span> <span data-ttu-id="22a15-128">Sie fügen die Knoten in der Regel im Code hinzu, aber hier wird die XAML-Hierarchie angezeigt, da sie beim Visualisieren der Erstellung der Knotenhierarchie hilfreich sein kann.</span><span class="sxs-lookup"><span data-stu-id="22a15-128">You typically add the nodes in code, but we show the XAML hierarchy here because it can be helpful for visualizing how the hierarchy of nodes is created.</span></span>

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

<span data-ttu-id="22a15-129">In den meisten Fällen zeigt die Strukturansicht Daten aus einer Datenquelle an. Daher deklarieren Sie das Steuerelement der Stammstrukturansicht in der Regel in XAML, fügen die TreeViewNode-Objekte jedoch im Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="22a15-129">In most cases, your tree view displays data from a data source, so you typically declare the root TreeView control in XAML, but add the TreeViewNode objects in code.</span></span>

<span data-ttu-id="22a15-130">Diese Strukturansicht ist identisch mit der zuvor in XAML erstellten, aber die Knoten werden stattdessen im Code erstellt.</span><span class="sxs-lookup"><span data-stu-id="22a15-130">This tree view is the same as the one created previously in XAML, but the nodes are created in code instead.</span></span>

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

<span data-ttu-id="22a15-131">Diese APIs sind für die Verwaltung der Datenhierarchie der Strukturansicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="22a15-131">These APIs are available for managing the data hierarchy of your tree view.</span></span>

| **[<span data-ttu-id="22a15-132">TreeView</span><span class="sxs-lookup"><span data-stu-id="22a15-132">TreeView</span></span>](/uwp/api/windows.ui.xaml.controls.treeview)** | |
| - | - |
| [<span data-ttu-id="22a15-133">RootNodes</span><span class="sxs-lookup"><span data-stu-id="22a15-133">RootNodes</span></span>](/uwp/api/windows.ui.xaml.controls.treeview.rootnodes) | <span data-ttu-id="22a15-134">Eine Strukturansicht kann einen oder mehrere Stammknoten aufweisen.</span><span class="sxs-lookup"><span data-stu-id="22a15-134">A tree view can have one or more root nodes.</span></span> <span data-ttu-id="22a15-135">Fügen Sie der RootNodes-Sammlung ein TreeViewNode-Objekt hinzu, um einen Stammknoten zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="22a15-135">Add a TreeViewNode object to the RootNodes collection to create a root node.</span></span> <span data-ttu-id="22a15-136">Das **übergeordnete Element** eines Stammknotens hat immer den Wert **null**.</span><span class="sxs-lookup"><span data-stu-id="22a15-136">The **Parent** of a root node is always **null**.</span></span> <span data-ttu-id="22a15-137">Die **Tiefe** eines Stammknotens beträgt 0.</span><span class="sxs-lookup"><span data-stu-id="22a15-137">The **Depth** of a root node is 0.</span></span> |

| **[<span data-ttu-id="22a15-138">TreeViewNode</span><span class="sxs-lookup"><span data-stu-id="22a15-138">TreeViewNode</span></span>](/uwp/api/windows.ui.xaml.controls.treeviewnode)** | |
| - | - |
| [<span data-ttu-id="22a15-139">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="22a15-139">Children</span></span>](/uwp/api/windows.ui.xaml.controls.treeviewnode.children) | <span data-ttu-id="22a15-140">Fügen Sie der Sammlung der untergeordneten Elemente des TreeViewNode-Objekts einen übergeordneten Knoten hinzu, um eine Knotenhierarchie zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="22a15-140">Add TreeViewNode objects to the Children collection of a parent node to create your node hierarchy.</span></span> <span data-ttu-id="22a15-141">Ein Knoten ist das **übergeordnete Element** aller Knoten in der Sammlung der **untergeordneten Elemente**.</span><span class="sxs-lookup"><span data-stu-id="22a15-141">A node is the **Parent** of all nodes in its **Children** collection.</span></span> |
| [<span data-ttu-id="22a15-142">HasChildren</span><span class="sxs-lookup"><span data-stu-id="22a15-142">HasChildren</span></span>](/uwp/api/windows.ui.xaml.controls.treeviewnode.haschildren) | <span data-ttu-id="22a15-143">Ist **true**, wenn der Knoten untergeordnete Elemente erkannt hat.</span><span class="sxs-lookup"><span data-stu-id="22a15-143">**true** if the node has realized children.</span></span> <span data-ttu-id="22a15-144">**false** gibt einen leeren Ordner oder ein Element an.</span><span class="sxs-lookup"><span data-stu-id="22a15-144">**false** indicates an empty folder or an item.</span></span> |
| [<span data-ttu-id="22a15-145">HasUnrealizedChildren</span><span class="sxs-lookup"><span data-stu-id="22a15-145">HasUnrealizedChildren</span></span>](/uwp/api/windows.ui.xaml.controls.treeviewnode.hasunrealizedchildren) | <span data-ttu-id="22a15-146">Verwenden Sie diese Eigenschaft, wenn Sie Knoten beim Erweitern ausgefüllt werden.</span><span class="sxs-lookup"><span data-stu-id="22a15-146">Use this property if you're filling nodes as they're expanded.</span></span> <span data-ttu-id="22a15-147">Weitere Informationen finden Sie unter _Ausfüllen eines Knotens, wenn er erweitert wird_ weiter unten in diesem Artikel.</span><span class="sxs-lookup"><span data-stu-id="22a15-147">See _Fill a node when it's expanding_ later in this article.</span></span> |
| [<span data-ttu-id="22a15-148">Tiefe</span><span class="sxs-lookup"><span data-stu-id="22a15-148">Depth</span></span>](/uwp/api/windows.ui.xaml.controls.treeviewnode.depth) | <span data-ttu-id="22a15-149">Gibt an, wie weit der Stammknoten von einem untergeordneten Knoten entfernt ist.</span><span class="sxs-lookup"><span data-stu-id="22a15-149">Indicates how far from the root node a child node is.</span></span> |
| [<span data-ttu-id="22a15-150">Parent</span><span class="sxs-lookup"><span data-stu-id="22a15-150">Parent</span></span>](/uwp/api/windows.ui.xaml.controls.treeviewnode.parent) | <span data-ttu-id="22a15-151">Ruft den TreeViewNode ab, der die Sammlung der **untergeordneten Elemente** besitzt, zu der dieser Knoten gehört.</span><span class="sxs-lookup"><span data-stu-id="22a15-151">Gets the TreeViewNode that owns the **Children** collection that this node is part of.</span></span> |

<span data-ttu-id="22a15-152">Die Strukturansicht verwendet die Eigenschaften **HasChildren** und **HasUnrealizedChildren**, um zu ermitteln, ob das Symbol „Erweitern/Reduzieren“ angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="22a15-152">The tree view uses the **HasChildren** and **HasUnrealizedChildren** properties to determine whether the expand/collapse icon is shown.</span></span> <span data-ttu-id="22a15-153">Wenn eine der Eigenschaften den Wert **true** hat, wird das Symbol angezeigt, andernfalls nicht.</span><span class="sxs-lookup"><span data-stu-id="22a15-153">If either property is **true**, the icon is shown; otherwise, it's not shown.</span></span>

## <a name="tree-view-node-content"></a><span data-ttu-id="22a15-154">Inhalt des Knotens der Strukturansicht</span><span class="sxs-lookup"><span data-stu-id="22a15-154">Tree view node content</span></span>

<span data-ttu-id="22a15-155">Sie können das Datenelement, das ein Knoten darstellt, in dessen [Inhalte](/uwp/api/windows.ui.xaml.controls.treeviewnode.content)-Eigenschaft speichern.</span><span class="sxs-lookup"><span data-stu-id="22a15-155">You can store the data item that a tree view node represents in its [Content](/uwp/api/windows.ui.xaml.controls.treeviewnode.content) property.</span></span>

<span data-ttu-id="22a15-156">Im vorherigen Beispielen war der Inhalt ein einfachen Zeichenfolgenwert.</span><span class="sxs-lookup"><span data-stu-id="22a15-156">In the previous examples, the content was a simple string value.</span></span> <span data-ttu-id="22a15-157">Hier stellt ein Knoten der Strukturansicht den Ordner „Bilder“ des Benutzers dar. Daher ist die Bildbibliothek [StorageFolder](/uwp/api/windows.storage.storagefolder) der Inhaltseigenschaft des Knotens zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="22a15-157">Here, a tree view node represents the user's Pictures folder, so the pictures library [StorageFolder](/uwp/api/windows.storage.storagefolder) is assigned to the node's Content property.</span></span>

```csharp
StorageFolder picturesFolder = KnownFolders.PicturesLibrary;
TreeViewNode pictureNode = new TreeViewNode();
pictureNode.Content = picturesFolder;
```

```vb
Dim picturesFolder As StorageFolder = KnownFolders.PicturesLibrary
Dim pictureNode As New TreeViewNode With {.Content = picturesFolder}
```

<span data-ttu-id="22a15-158">Sie können eine [DataTemplate](/uwp/api/windows.ui.xaml.datatemplate) angeben, um festzulegen, wie das Datenelement in der Strukturansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="22a15-158">You can provide a [DataTemplate](/uwp/api/windows.ui.xaml.datatemplate) to specify how the data item is displayed in the tree view.</span></span>

> [!NOTE]
> <span data-ttu-id="22a15-159">In Windows10, Version 1803, müssen Sie Vorlage für das TreeView-Steuerelement umschreiben und eine benutzerdefinierte ItemTemplate festlegen, falls der Inhalt keine Zeichenfolge ist.</span><span class="sxs-lookup"><span data-stu-id="22a15-159">In Windows 10, version 1803, you have to retemplate the TreeView control and specify a custom ItemTemplate if your content is not a string.</span></span> <span data-ttu-id="22a15-160">Weitere Informationen finden Sie im vollständigen Beispiel am Anfang dieses Artikels.</span><span class="sxs-lookup"><span data-stu-id="22a15-160">For more info, see the full example at the end of this article.</span></span>

## <a name="interacting-with-a-tree-view"></a><span data-ttu-id="22a15-161">Interagieren mit einer Strukturansicht</span><span class="sxs-lookup"><span data-stu-id="22a15-161">Interacting with a tree view</span></span>

<span data-ttu-id="22a15-162">Sie können eine Strukturansicht konfigurieren, damit Benutzer auf verschiedene Weise mit ihr interagieren können:</span><span class="sxs-lookup"><span data-stu-id="22a15-162">You can configure a tree view to let a user interact with it in several different ways:</span></span>

- <span data-ttu-id="22a15-163">Knoten erweitern oder reduzieren</span><span class="sxs-lookup"><span data-stu-id="22a15-163">expand or collapse nodes</span></span>
- <span data-ttu-id="22a15-164">Einfach- oder Mehrfachauswahlelemente</span><span class="sxs-lookup"><span data-stu-id="22a15-164">single- or multi-select items</span></span>
- <span data-ttu-id="22a15-165">Element durch Klicken aufrufen</span><span class="sxs-lookup"><span data-stu-id="22a15-165">click to invoke an item</span></span>

### <a name="expandcollapse"></a><span data-ttu-id="22a15-166">Erweitern/Reduzieren</span><span class="sxs-lookup"><span data-stu-id="22a15-166">Expand/collapse</span></span>

<span data-ttu-id="22a15-167">Jeder Strukturknoten, der über untergeordnete Elementen verfügt, kann durch Klicken auf das Erweitern/Reduzieren-Symbol erweitert oder reduziert werden.</span><span class="sxs-lookup"><span data-stu-id="22a15-167">Any tree view node that has children can always be expanded or collapsed by clicking the expand/collapse glyph.</span></span> <span data-ttu-id="22a15-168">Knoten lassen sich auch programmgesteuert erweitern oder reduzieren und reagieren, wenn der Zustand eines Knotens geändert wird.</span><span class="sxs-lookup"><span data-stu-id="22a15-168">You can also expand or collapse a node programmatically, and respond when a node changes state.</span></span>

#### <a name="expandcollapse-a-node-programmatically"></a><span data-ttu-id="22a15-169">Programmgesteuertes Erweitern/Reduzieren von Knoten</span><span class="sxs-lookup"><span data-stu-id="22a15-169">Expand/collapse a node programmatically</span></span>

<span data-ttu-id="22a15-170">Es gibt 2 Methoden den Knoten einer Strukturansicht in Ihrem Code zu erweitern oder zu reduzieren.</span><span class="sxs-lookup"><span data-stu-id="22a15-170">There are 2 ways you can expand or collapse a tree view node in your code.</span></span>

- <span data-ttu-id="22a15-171">Die [TreeView](/uwp/api/windows.ui.xaml.controls.treeview)-Klasse verfügt über die Methoden [Reduzieren](/uwp/api/windows.ui.xaml.controls.treeview.collapse) und [Erweitern](/uwp/api/windows.ui.xaml.controls.treeview.expand).</span><span class="sxs-lookup"><span data-stu-id="22a15-171">The [TreeView](/uwp/api/windows.ui.xaml.controls.treeview) class has the [Collapse](/uwp/api/windows.ui.xaml.controls.treeview.collapse) and [Expand](/uwp/api/windows.ui.xaml.controls.treeview.expand) methods.</span></span> <span data-ttu-id="22a15-172">Wenn Sie diese Methoden aufrufen, übergeben Sie den TreeViewNode, den Sie erweitern oder reduzieren möchten.</span><span class="sxs-lookup"><span data-stu-id="22a15-172">When you call these methods, you pass in the TreeViewNode that you want to expand or collapse.</span></span>

- <span data-ttu-id="22a15-173">Jeder [TreeViewNode](/uwp/api/windows.ui.xaml.controls.treeviewnode) verfügt über die Eigenschaft [IsExpanded](/uwp/api/windows.ui.xaml.controls.treeviewnode.isexpanded).</span><span class="sxs-lookup"><span data-stu-id="22a15-173">Each [TreeViewNode](/uwp/api/windows.ui.xaml.controls.treeviewnode) has the [IsExpanded](/uwp/api/windows.ui.xaml.controls.treeviewnode.isexpanded) property.</span></span> <span data-ttu-id="22a15-174">Mit dieser Eigenschaft können Sie den Status eines Knotens überprüfen oder ihn so festlegen, dass sein Zustand geändert wird.</span><span class="sxs-lookup"><span data-stu-id="22a15-174">You can use this property to check the state of a node, or set it to change the state.</span></span> <span data-ttu-id="22a15-175">Diese Eigenschaft lässt sich auch in XAML einstellen, um den Anfangszustand eines Knotens festzulegen.</span><span class="sxs-lookup"><span data-stu-id="22a15-175">You can also set this property in XAML to set the initial state of a node.</span></span>

### <a name="fill-a-node-when-its-expanding"></a><span data-ttu-id="22a15-176">Ausfüllen eines Knotens, wenn er erweitert wird</span><span class="sxs-lookup"><span data-stu-id="22a15-176">Fill a node when it's expanding</span></span>

<span data-ttu-id="22a15-177">Sie müssen möglicherweise eine große Anzahl von Knoten in der Strukturansicht anzeigen, oder Sie wissen möglicherweise nicht vorab, wie viele Knoten diese aufweisen wird.</span><span class="sxs-lookup"><span data-stu-id="22a15-177">You might need to show a large number of nodes in your tree view, or you might not know ahead of time how many nodes it will have.</span></span> <span data-ttu-id="22a15-178">Das TreeView-Steuerelement ist nicht virtualisiert, damit Sie Ressourcen verwalten können, indem Sie jeden Knoten ausfüllen, wenn er erweitert wird, und die untergeordneten Knoten entfernen, wenn sie reduziert werden.</span><span class="sxs-lookup"><span data-stu-id="22a15-178">The TreeView control is not virtualized, so you can manage resources by filling each node as it's expanded, and removing the child nodes when it's collapsed.</span></span>

<span data-ttu-id="22a15-179">Behandeln Sie das [Erweitern](/uwp/api/windows.ui.xaml.controls.treeview.expand)-Ereignis und verwenden Sie die [HasUnrealizedChildren](/uwp/api/windows.ui.xaml.controls.treeviewnode.hasunrealizedchildren) -Eigenschaft, um einem Knoten untergeordnete Elemente hinzuzufügen, wenn er erweitert wird.</span><span class="sxs-lookup"><span data-stu-id="22a15-179">Handle the [Expanding](/uwp/api/windows.ui.xaml.controls.treeview.expand) event and use the [HasUnrealizedChildren](/uwp/api/windows.ui.xaml.controls.treeviewnode.hasunrealizedchildren) property to add children to a node when it's being expanded.</span></span> <span data-ttu-id="22a15-180">Die HasUnrealizedChildren-Eigenschaft gibt an, ob der Knoten ausgefüllt werden muss oder ob dessen Sammlung der untergeordneten Elemente bereits aufgefüllt wurde.</span><span class="sxs-lookup"><span data-stu-id="22a15-180">The HasUnrealizedChildren property indicates whether the node needs to be filled, or if its Children collection has already been populated.</span></span> <span data-ttu-id="22a15-181">Es ist wichtig, dass dieser Wert nicht durch den TreeViewNode festgelegt, sondern von Ihnen in Ihrem App-Code verwaltet wird.</span><span class="sxs-lookup"><span data-stu-id="22a15-181">It's important to remember that the TreeViewNode doesn't set this value, you need need to manage it in your app code.</span></span>

<span data-ttu-id="22a15-182">Im Folgenden finden Sie ein Beispiel für diese verwendeten APIs.</span><span class="sxs-lookup"><span data-stu-id="22a15-182">Here's an example of these APIs in use.</span></span> <span data-ttu-id="22a15-183">Der vollständige Beispielcode ist am Ende dieses Artikels aufgeführt, darunter die Implementierung des „FillTreeNode”.</span><span class="sxs-lookup"><span data-stu-id="22a15-183">See the complete example code at the end of this article for context, including the implemetation of 'FillTreeNode'.</span></span>

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

<span data-ttu-id="22a15-184">Es ist nicht erforderlich, Sie können jedoch auch das [Reduziert](/uwp/api/windows.ui.xaml.controls.treeview.collapsed)-Ereignis behandeln und die untergeordneten Knoten entfernen, wenn der übergeordnete Knoten geschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="22a15-184">It's not required, but you might want to also handle the [Collapsed](/uwp/api/windows.ui.xaml.controls.treeview.collapsed) event and remove the child nodes when the parent node is closed.</span></span> <span data-ttu-id="22a15-185">Dies kann wichtig sein, wenn die Strukturansicht viele Knoten aufweist oder die Knotendaten viele Ressourcen nutzen.</span><span class="sxs-lookup"><span data-stu-id="22a15-185">This can be important if your tree view has many nodes, or if the node data uses a lot of resources.</span></span> <span data-ttu-id="22a15-186">Berücksichtigen Sie potenzielle Leistungseinbußen durch das Ausfüllen eines Knotens bei jedem Öffnen im Vergleich zur Beibehaltung der untergeordneten Elemente an einem geschlossenen Knoten.</span><span class="sxs-lookup"><span data-stu-id="22a15-186">You should consider the performance impact of filling a node each time it's opened versus leaving the children on a closed node.</span></span> <span data-ttu-id="22a15-187">Welche Option jeweils geeignet ist, hängt von Ihrer App ab.</span><span class="sxs-lookup"><span data-stu-id="22a15-187">The best option will depend on your app.</span></span>

<span data-ttu-id="22a15-188">Nachfolgend finden Sie ein Beispiel für einen Handler für das Reduziert-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="22a15-188">Here's an example of a handler for the Collapsed event.</span></span>

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

### <a name="invoking-an-item"></a><span data-ttu-id="22a15-189">Aufrufen eines Elements</span><span class="sxs-lookup"><span data-stu-id="22a15-189">Invoking an item</span></span>

<span data-ttu-id="22a15-190">Ein Benutzer kann eine Aktion (behandelt das Element wie eine Schaltfläche) aufrufen, statt das Element auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="22a15-190">A user can invoke an action (treating the item like a button) instead of selecting the item.</span></span> <span data-ttu-id="22a15-191">Sie behandeln das [ItemInvoked](/uwp/api/windows.ui.xaml.controls.treeview.iteminvoked)-Ereignis, um auf diese Benutzerinteraktion zu reagieren.</span><span class="sxs-lookup"><span data-stu-id="22a15-191">You handle the [ItemInvoked](/uwp/api/windows.ui.xaml.controls.treeview.iteminvoked) event to respond to this user interaction.</span></span>

> [!NOTE]
> <span data-ttu-id="22a15-192">Im Gegensatz zur ListView, die über die [IsItemClickEnabled](/uwp/api/windows.ui.xaml.controls.listviewbase.isitemclickenabled)-Eigenschaft verfügt, ist das Aufrufen eines Elements für die Strukturansicht immer aktiviert.</span><span class="sxs-lookup"><span data-stu-id="22a15-192">Unlike ListView, which has the [IsItemClickEnabled](/uwp/api/windows.ui.xaml.controls.listviewbase.isitemclickenabled) property, invoking an item is always enabled on the tree view.</span></span> <span data-ttu-id="22a15-193">Sie können weiterhin auswählen, ob das Ereignis behandelt werden soll oder nicht.</span><span class="sxs-lookup"><span data-stu-id="22a15-193">You can still choose whether to handle the event or not.</span></span>

**<span data-ttu-id="22a15-194">[TreeViewItemInvokedEventArgs](/uwp/api/windows.ui.xaml.controls.treeviewiteminvokedeventargs)-Klasse</span><span class="sxs-lookup"><span data-stu-id="22a15-194">[TreeViewItemInvokedEventArgs](/uwp/api/windows.ui.xaml.controls.treeviewiteminvokedeventargs) class</span></span>**

<span data-ttu-id="22a15-195">Die ItemInvoked-Ereignisargumente ermöglichen Ihnen den Zugriff auf das aufgerufene Element.</span><span class="sxs-lookup"><span data-stu-id="22a15-195">The ItemInvoked event args give you acces to the invoked item.</span></span> <span data-ttu-id="22a15-196">Die [InvokedItem](/uwp/api/windows.ui.xaml.controls.treeviewiteminvokedeventargs.invokeditem)-Eigenschaft verfügt über den Knoten, der aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="22a15-196">The [InvokedItem](/uwp/api/windows.ui.xaml.controls.treeviewiteminvokedeventargs.invokeditem) property has the node that was invoked.</span></span> <span data-ttu-id="22a15-197">Sie können eine Umwandlung in TreeViewNode durchführen, um das Datenelement aus der TreeViewNode.Content-Eigenschaft abzurufen.</span><span class="sxs-lookup"><span data-stu-id="22a15-197">You can cast it to TreeViewNode and get the data item from the TreeViewNode.Content property.</span></span>

<span data-ttu-id="22a15-198">Nachfolgend finden Sie ein Beispiel für einen ItemInvoked-Ereignishandler.</span><span class="sxs-lookup"><span data-stu-id="22a15-198">Here's an example of an ItemInvoked event handler.</span></span> <span data-ttu-id="22a15-199">Das Datenelement ist ein [IStorageItem](/uwp/api/windows.storage.istorageitem), und in diesem Beispiel werden lediglich einige Informationen über die Datei und die Struktur angezeigt.</span><span class="sxs-lookup"><span data-stu-id="22a15-199">The data item is an [IStorageItem](/uwp/api/windows.storage.istorageitem), and this example just displays some info about the file and tree.</span></span> <span data-ttu-id="22a15-200">Wenn der Knoten ein Ordnerknoten ist, erweitert oder reduziert er den Knoten gleichzeitig.</span><span class="sxs-lookup"><span data-stu-id="22a15-200">Also, if the node is a folder node, it expands or collpases the node at the same time.</span></span> <span data-ttu-id="22a15-201">Andernfalls wird der Knoten nur dann erweitert oder reduziert, wenn auf die Chevron-Schaltfläche geklickt wird.</span><span class="sxs-lookup"><span data-stu-id="22a15-201">Otherwise, the node expands or collapses only when the chevron is clicked.</span></span>

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

### <a name="item-selection"></a><span data-ttu-id="22a15-202">Elementauswahl</span><span class="sxs-lookup"><span data-stu-id="22a15-202">Item selection</span></span>

<span data-ttu-id="22a15-203">Das TreeView-Steuerelement unterstützt sowohl die Einzelauswahl als auch die Mehrfachauswahl.</span><span class="sxs-lookup"><span data-stu-id="22a15-203">The TreeView control supports both single-selection and multi-selection.</span></span> <span data-ttu-id="22a15-204">Die Auswahl von Knoten ist standardmäßig deaktiviert, Sie können die [TreeView.SelectionMode](/uwp/api/windows.ui.xaml.controls.treeview.selectionmode)-Eigenschaft jedoch festlegen, um die Auswahl von Knoten zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="22a15-204">By default, selection of nodes is turned off, but you can set the [TreeView.SelectionMode](/uwp/api/windows.ui.xaml.controls.treeview.selectionmode) property to allow selection of nodes.</span></span> <span data-ttu-id="22a15-205">Die [TreeViewSelectionMode](/uwp/api/windows.ui.xaml.controls.treeviewselectionmode)-Werte sind **Keine**, **Einzelne** und **Mehrere**.</span><span class="sxs-lookup"><span data-stu-id="22a15-205">The [TreeViewSelectionMode](/uwp/api/windows.ui.xaml.controls.treeviewselectionmode) values are **None**, **Single**, and **Multiple**.</span></span>

<span data-ttu-id="22a15-206">Wenn die Auswahl aktiviert ist, wird ein Kontrollkästchen neben jedem Knoten einer Strukturansicht angezeigt und ausgewählte Elemente werden hervorgehoben.</span><span class="sxs-lookup"><span data-stu-id="22a15-206">When selection is enabled, a checkbox is shown next to each tree view node, and selected items are highlighted.</span></span> <span data-ttu-id="22a15-207">Ein Benutzer kann ein Element mithilfe eines Kontrollkästchens aktivieren oder deaktivieren. Das Element kann weiterhin aufgerufen werden, indem darauf geklickt wird.</span><span class="sxs-lookup"><span data-stu-id="22a15-207">A user can select or de-select an item by using the checkbox; clicking the item still causes it to be invoked.</span></span>

<span data-ttu-id="22a15-208">Ausgewählte Knoten werden der [SelectedNodes](/uwp/api/windows.ui.xaml.controls.treeview.selectednodes)-Sammlung der Strukturansicht hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="22a15-208">Selected nodes are added to the tree view's [SelectedNodes](/uwp/api/windows.ui.xaml.controls.treeview.selectednodes) collection.</span></span> <span data-ttu-id="22a15-209">Sie können die [SelectAll](/uwp/api/windows.ui.xaml.controls.treeview.selectall)-Methode aufrufen, um alle Knoten in einer Strukturansicht auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="22a15-209">You can call the [SelectAll](/uwp/api/windows.ui.xaml.controls.treeview.selectall) method to select all the nodes in a tree view.</span></span>

> [!NOTE]
> <span data-ttu-id="22a15-210">Wenn Sie **SelectAll** aufrufen, werden alle realisierten Knoten ungeachtet der SelectionMode ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="22a15-210">If you call **SelectAll**, all realized nodes are selected, regardless of the SelectionMode.</span></span> <span data-ttu-id="22a15-211">Um ein einheitliches Benutzererlebnis zu ermöglichen, sollten Sie SelectAll nur dann aufrufen, wenn SelectionMode auf **Mehrere** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="22a15-211">To provide a consistent user experience, you should only call SelectAll if SelectionMode is **Multiple**.</span></span>

#### <a name="selection-and-realizedunrealized-nodes"></a><span data-ttu-id="22a15-212">Auswahl und realisierte/nicht realisierte Knoten</span><span class="sxs-lookup"><span data-stu-id="22a15-212">Selection and realized/unrealized nodes</span></span>

<span data-ttu-id="22a15-213">Wenn die Strukturansicht nicht realisierte Knoten aufweist, werden sie bei der Auswahl nicht berücksichtigt.</span><span class="sxs-lookup"><span data-stu-id="22a15-213">If your tree view has unrealized nodes, they are not taken into account for selection.</span></span> <span data-ttu-id="22a15-214">Beachten Sie bei der Auswahl mit nicht realisierten Knoten Folgendes.</span><span class="sxs-lookup"><span data-stu-id="22a15-214">Here are some things you need to keep in mind regarding selection with unrealized nodes.</span></span>

- <span data-ttu-id="22a15-215">Wenn ein Benutzer einen übergeordneten Knoten auswählt, werden auch alle realisierten untergeordneten Elemente ausgewählt, die sich unter diesem übergeordneten Element befinden.</span><span class="sxs-lookup"><span data-stu-id="22a15-215">If a user selects a parent node, all the realized children under that parent are also selected.</span></span> <span data-ttu-id="22a15-216">Wenn alle untergeordneten Knoten ausgewählt werden, wird der übergeordnete Knoten entsprechend ebenfalls ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="22a15-216">Similarly, if all the child nodes are selected, the parent node also becomes selected.</span></span>
- <span data-ttu-id="22a15-217">Bei der SelectAll-Methode werden der SelectedNodes-Sammlung nur realisierte Knoten hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="22a15-217">The SelectAll method only adds realized nodes to the SelectedNodes collection.</span></span>
- <span data-ttu-id="22a15-218">Wenn ein übergeordneter Knoten mit nicht realisierten untergeordneten Elementen ausgewählt wird, werden die untergeordneten Elemente ausgewählt, sobald sie realisiert werden.</span><span class="sxs-lookup"><span data-stu-id="22a15-218">If a parent node with unrealized children is selected, the children will be selected as they are realized.</span></span>

## <a name="code-examples"></a><span data-ttu-id="22a15-219">Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="22a15-219">Code examples</span></span>

### <a name="tree-view-with-selection-enabled"></a><span data-ttu-id="22a15-220">Strukturansicht mit aktivierter Auswahl</span><span class="sxs-lookup"><span data-stu-id="22a15-220">Tree view with selection enabled</span></span>

<span data-ttu-id="22a15-221">Dieses Beispiel zeigt, wie in XAML eine einfache Struktur für eine Strukturansicht erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="22a15-221">This example shows how to create a simple tree view structure in XAML.</span></span> <span data-ttu-id="22a15-222">Die Strukturansicht zeigt in Kategorien angeordnete Eissorten und Garnierungen, die der Benutzer auswählen kann.</span><span class="sxs-lookup"><span data-stu-id="22a15-222">The tree view shows ice cream flavors and toppings that the user can choose from, arranged in categories.</span></span> <span data-ttu-id="22a15-223">Die Mehrfachauswahl ist aktiviert, und wenn der Benutzer auf eine Schaltfläche klickt, werden die SelectedItems in der Haupt-App-UI angezeigt.</span><span class="sxs-lookup"><span data-stu-id="22a15-223">Multi-selection is enabled, and when the user clicks a button, the SelectedItems are displayed in the main app UI.</span></span>

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

### <a name="pictures-and-music-library-tree-view"></a><span data-ttu-id="22a15-224">Baumstruktur für Bild- und Musikbibliotheken</span><span class="sxs-lookup"><span data-stu-id="22a15-224">Pictures and Music Library tree view</span></span>

<span data-ttu-id="22a15-225">Dieses Beispiel zeigt, wie eine Strukturansicht erstellt wird, die den Inhalt und die Struktur der Bild- und Musikbibliotheken von Benutzern anzeigt.</span><span class="sxs-lookup"><span data-stu-id="22a15-225">This example shows how to create a tree view that shows the contents and structure of the users Pictures and Music libraries.</span></span> <span data-ttu-id="22a15-226">Da die Anzahl der Elemente vorab nicht bekannt sein kann, wird jeder Knoten beim Erweitern gefüllt und beim Reduzieren geleert.</span><span class="sxs-lookup"><span data-stu-id="22a15-226">The number of items can't be known ahead of time, so each node is filled when it's expanded, and emptied when it's collapsed.</span></span>

<span data-ttu-id="22a15-227">Eine benutzerdefinierte Elementvorlage wird verwendet, um die Datenelemente vom Typ [IStorageItem](/uwp/api/windows.storage.istorageitem) anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="22a15-227">A custom item template is used to display the data items, which are of type [IStorageItem](/uwp/api/windows.storage.istorageitem).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="22a15-228">Für den Code in diesem Beispiel sind die Funktionen PicturesLibrary und MusicLibrary erforderlich.</span><span class="sxs-lookup"><span data-stu-id="22a15-228">The code in this example requires the picturesLibrary and musicLibrary capabilities.</span></span> <span data-ttu-id="22a15-229">Weitere Informationen zum Dateizugriff finden Sie unter [Berechtigungen für den Dateizugriff](../../files/file-access-permissions.md), [Aufzählen und Abfragen von Dateien und Ordnern](../../files/quickstart-listing-files-and-folders.md) und [Dateien und Ordner in den Musik-, Bild- und Videobibliotheken](../../files/quickstart-managing-folders-in-the-music-pictures-and-videos-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="22a15-229">For more info about file access, see [File access permissions](../../files/file-access-permissions.md), [Enumerate and query files and folders](../../files/quickstart-listing-files-and-folders.md), and [Files and folders in the Music, Pictures, and Videos libraries](../../files/quickstart-managing-folders-in-the-music-pictures-and-videos-libraries.md).</span></span>

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

## <a name="related-articles"></a><span data-ttu-id="22a15-230">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="22a15-230">Related articles</span></span>

- [<span data-ttu-id="22a15-231">TreeView-Klasse</span><span class="sxs-lookup"><span data-stu-id="22a15-231">TreeView class</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.treeview)
- [<span data-ttu-id="22a15-232">ListView-Klasse</span><span class="sxs-lookup"><span data-stu-id="22a15-232">ListView class</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx)
- [<span data-ttu-id="22a15-233">ListView und GridView</span><span class="sxs-lookup"><span data-stu-id="22a15-233">ListView and GridView</span></span>](listview-and-gridview.md)
