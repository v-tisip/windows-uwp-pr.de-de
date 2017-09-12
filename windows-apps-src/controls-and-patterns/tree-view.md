---
author: Jwmsft
Description: Verwenden Sie den Beispielcode zur Strukturansicht, um eine ausklappbare Struktur (einen ausklappbaren Baum) zu erzeugen.
title: Strukturansicht
label: Tree view
template: detail.hbs
ms.openlocfilehash: c7ad99d20fe30ea4b94ad62de45b3832aae3805e
ms.sourcegitcommit: b42d14c775efbf449a544ddb881abd1c65c1ee86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2017
---
# <a name="hierarchical-layout-with-treeview"></a><span data-ttu-id="0b135-103">Hierarchisches Layout mit Strukturansicht</span><span class="sxs-lookup"><span data-stu-id="0b135-103">Hierarchical layout with TreeView</span></span>
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

<span data-ttu-id="0b135-104">Eine Strukturansicht ist eine Hierarchieauflistung mit Knoten, die das Aus- und Einblenden von geschachtelten Elementen erlauben.</span><span class="sxs-lookup"><span data-stu-id="0b135-104">A TreeView is a hierarchical list pattern with expanding and collapsing nodes that contain nested items.</span></span> <span data-ttu-id="0b135-105">Geschachtelte Elemente können zusätzliche Knoten oder reguläre Listenelemente sein.</span><span class="sxs-lookup"><span data-stu-id="0b135-105">Nested items can be additional nodes or regular list items.</span></span> <span data-ttu-id="0b135-106">Sie können eine [ListView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx) zum Erstellen einer Strukturansicht benutzen, um eine Ordnerstruktur oder geschachtelte Beziehungen zwischen Elementen in der UI zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="0b135-106">You can use a [ListView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx) to build a tree view to illustrate a folder structure or nested relationships in your UI.</span></span>

<span data-ttu-id="0b135-107">Das [Strukturansicht-Beispiel](http://go.microsoft.com/fwlink/?LinkId=785018) ist eine Referenzimplementierung, das mit der **ListView** erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="0b135-107">The [TreeView sample](http://go.microsoft.com/fwlink/?LinkId=785018) is a reference implementation built using **ListView**.</span></span> <span data-ttu-id="0b135-108">Es ist kein eigenständiges Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="0b135-108">It is not a standalone control.</span></span> <span data-ttu-id="0b135-109">Für die Strukturansicht im Bereich "Favoriten" des Microsoft Edge Browsers wird diese Referenzimplementierung genutzt.</span><span class="sxs-lookup"><span data-stu-id="0b135-109">The TreeView seen in the Favorites Pane in the Microsoft Edge browser uses this reference implementation.</span></span>

<span data-ttu-id="0b135-110">Das Beispiel unterstützt:</span><span class="sxs-lookup"><span data-stu-id="0b135-110">The sample supports:</span></span>
- <span data-ttu-id="0b135-111">Die Schachtelung von N Ebenen</span><span class="sxs-lookup"><span data-stu-id="0b135-111">N-level nesting</span></span>
- <span data-ttu-id="0b135-112">Das Ein-/Ausblenden von Knoten</span><span class="sxs-lookup"><span data-stu-id="0b135-112">Expanding/collapsing of nodes</span></span>
- <span data-ttu-id="0b135-113">Ziehen und Ablegen von Knoten in der Strukturansicht</span><span class="sxs-lookup"><span data-stu-id="0b135-113">Dragging and dropping of nodes within the TreeView</span></span>
- <span data-ttu-id="0b135-114">Integrierte Eingabehilfen</span><span class="sxs-lookup"><span data-stu-id="0b135-114">Built-in accessibility</span></span>

![Die Strukturansicht im Referenzbeispiel](images/tree-view-sample.png) | ![Die Strukturansicht im Edge-Browser](images/tree-view-edge.png)
-- | --
<span data-ttu-id="0b135-117">Referenzbeispiel für die Strukturansicht</span><span class="sxs-lookup"><span data-stu-id="0b135-117">TreeView reference sample</span></span> | <span data-ttu-id="0b135-118">Die Strukturansicht im Edge-Browser</span><span class="sxs-lookup"><span data-stu-id="0b135-118">TreeView in Edge browser</span></span>

## <a name="is-this-the-right-pattern"></a><span data-ttu-id="0b135-119">Ist dies das richtige Muster?</span><span class="sxs-lookup"><span data-stu-id="0b135-119">Is this the right pattern?</span></span>

- <span data-ttu-id="0b135-120">Verwenden Sie eine Strukturansicht, wenn Elemente geschachtelte Elemente haben, und dann, wenn es wichtig ist, die hierarchische Beziehung zwischen Elementen und ihren gleichgestellten Elementen und Knoten zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="0b135-120">Use a TreeView when items have nested list items, and if it is important to illustrate the hierarchical relationship of items to their peers and nodes.</span></span>

- <span data-ttu-id="0b135-121">Vermeiden Sie Strukturansicht, wenn die geschachtelte Beziehung eines Elements nicht im Vordergrund steht.</span><span class="sxs-lookup"><span data-stu-id="0b135-121">Avoid using TreeView if highlighting the nested relationship of an item is not a priority.</span></span> <span data-ttu-id="0b135-122">Für die meisten Drilldown-Szenarios eignet sich eine normale ListView</span><span class="sxs-lookup"><span data-stu-id="0b135-122">For most drill-in scenarios, a regular list view is appropriate</span></span>

## <a name="treeview-ui-structure"></a><span data-ttu-id="0b135-123">Strukturansicht "UI-Struktur"</span><span class="sxs-lookup"><span data-stu-id="0b135-123">TreeView UI structure</span></span>

<span data-ttu-id="0b135-124">Sie können Symbole benutzen, um Knoten in einer Strukturansicht zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="0b135-124">You can use icons to represent nodes in a TreeView.</span></span> <span data-ttu-id="0b135-125">Es kann eine Kombination aus Einzügen und Symbolen verwendet werden, um die geschachtelte Beziehung zwischen Ordnern und übergeordneten Knoten bzw. Nicht-Ordnern und untergeordneten Knoten darzustellen.</span><span class="sxs-lookup"><span data-stu-id="0b135-125">A combination of indentation and icons can be used to represent the nested relationship between folder/parent nodes and non-folder/child nodes.</span></span> <span data-ttu-id="0b135-126">Im Folgenden eine Anleitung zur Umsetzung.</span><span class="sxs-lookup"><span data-stu-id="0b135-126">Here is guidance on how to do so.</span></span>

### <a name="icons"></a><span data-ttu-id="0b135-127">Symbole</span><span class="sxs-lookup"><span data-stu-id="0b135-127">Icons</span></span>

<span data-ttu-id="0b135-128">Benutzen Sie Symbole, um anzuzeigen, dass es sich bei einem Element um einen Knoten handelt, und außerdem, um anzuzeigen, in welchem Zustand sich der Knoten befindet (ein- oder ausgeblendet).</span><span class="sxs-lookup"><span data-stu-id="0b135-128">Use icons to indicate that an item is a node, as well as what state the node is in (expanded or collapsed).</span></span>

#### <a name="chevron"></a><span data-ttu-id="0b135-129">Chevron</span><span class="sxs-lookup"><span data-stu-id="0b135-129">Chevron</span></span>

<span data-ttu-id="0b135-130">Aus Gründen der Konsistenz sollten ausgeblendete Knoten ein Chevron haben, welches nach rechts zeigt, während eingeblendete Knoten ein Chevron haben, das nach unten zeigt.</span><span class="sxs-lookup"><span data-stu-id="0b135-130">For consistency, collapsed nodes should use a chevron pointing to the right, and expanded nodes should use a chevron pointing down.</span></span>

![Verwendung des Chevronsymbols in der Strukturansicht](images/treeview_chevron.png)

#### <a name="folder"></a><span data-ttu-id="0b135-132">Ordner</span><span class="sxs-lookup"><span data-stu-id="0b135-132">Folder</span></span>

<span data-ttu-id="0b135-133">Verwenden Sie ein Ordnersymbol ausschließlich als Darstellung für tatsächliche Ordner.</span><span class="sxs-lookup"><span data-stu-id="0b135-133">Use a folder icon only for literal representations of folders.</span></span>

![Verwendung des Ordnersymbols in der Strukturansicht](images/treeview_folder.png)

#### <a name="chevron-and-folder"></a><span data-ttu-id="0b135-135">Chevron und Ordner</span><span class="sxs-lookup"><span data-stu-id="0b135-135">Chevron and Folder</span></span>

<span data-ttu-id="0b135-136">Eine Kombination aus einem Chevron und einem Ordner sollte nur dann verwendet werden, wenn die Listenelemente, die selbst keine Knoten sind, in der Strukturansicht auch Symbole haben.</span><span class="sxs-lookup"><span data-stu-id="0b135-136">A combination of a chevron and a folder should be used only if non-node list items in the TreeView also have icons.</span></span>

![Verwendung der Chevron- und Ordnersymbole zusammen in einer Strukturansicht.](images/treeview_chevron_folder.png)

#### <a name="redlines-for-indentation-of-folders-and-non-folder-nodes"></a><span data-ttu-id="0b135-138">Redlines für den Einzug von Ordnern und Knoten, die keine Ordner sind</span><span class="sxs-lookup"><span data-stu-id="0b135-138">Redlines for indentation of folders and non-folder nodes</span></span>

<span data-ttu-id="0b135-139">Verwenden Sie Redlines wie in dem Bildschirmfoto unten für den Einzug von Ordnern und Knoten, die keine Ordner sind.</span><span class="sxs-lookup"><span data-stu-id="0b135-139">Use the redlines in the screenshot below for indentation of folder and non-folder nodes.</span></span>

![Redlines für den Einzug von Ordnern und Knoten, die keine Ordner sind](images/treeview_chevron_folder_indent_rl.png)

## <a name="building-a-treeview"></a><span data-ttu-id="0b135-141">Erstellen einer Strukturansicht</span><span class="sxs-lookup"><span data-stu-id="0b135-141">Building a TreeView</span></span>

<span data-ttu-id="0b135-142">Die Strukturansicht hat die folgenden Hauptklassen.</span><span class="sxs-lookup"><span data-stu-id="0b135-142">TreeView has the following main classes.</span></span> <span data-ttu-id="0b135-143">Jede dieser Klassen wird definiert und in die Referenzimplementierung eingebunden.</span><span class="sxs-lookup"><span data-stu-id="0b135-143">All of these are defined and included in the reference implementation.</span></span>

> <span data-ttu-id="0b135-144">**Hinweis**&nbsp;&nbsp;Die Struktur ist als [Komponente für Windows-Runtime](https://msdn.microsoft.com/windows/uwp/winrt-components/index) implementiert, geschrieben in C++, d. h. es kann darauf von jeder UWP-App in jeder Sprache Bezug genommen werden.</span><span class="sxs-lookup"><span data-stu-id="0b135-144">**Note**&nbsp;&nbsp;TreeView is implemented as a [Windows Runtime component](https://msdn.microsoft.com/windows/uwp/winrt-components/index) written in C++, so it can be referenced by a UWP app in any language.</span></span> <span data-ttu-id="0b135-145">In diesem Beispiel befindet sich der Code der Strukturansicht im Ordner *cpp/Control*.</span><span class="sxs-lookup"><span data-stu-id="0b135-145">In the sample, the TreeView code is located in the *cpp/Control* folder.</span></span> <span data-ttu-id="0b135-146">Es gibt keinen entsprechenden *cs/Control*-Ordner für C#.</span><span class="sxs-lookup"><span data-stu-id="0b135-146">There is no corresponding *cs/Control* folder for C#.</span></span>

- <span data-ttu-id="0b135-147">Die `TreeNode`-Klasse implementiert das hierarchische Layout für die Strukturansicht.</span><span class="sxs-lookup"><span data-stu-id="0b135-147">The `TreeNode` class implements the hierarchical layout for the TreeView.</span></span> <span data-ttu-id="0b135-148">Sie enthält außerdem die Daten, die in der Vorlage an sie gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="0b135-148">It also holds the data that will be bound to it in the items template.</span></span>
- <span data-ttu-id="0b135-149">Die `TreeView`-Klasse implementiert Ereignisse für ItemClick, das Ausklappen/Zuklappen von Ordnern, und die Initiierung von Zieh-Vorgang.</span><span class="sxs-lookup"><span data-stu-id="0b135-149">The `TreeView` class implements events for ItemClick, expand/collapse of folders, and drag initiation.</span></span>
- <span data-ttu-id="0b135-150">Die `TreeViewItem` Klasse implementiert die Ereignisse für den Drop-Vorgang.</span><span class="sxs-lookup"><span data-stu-id="0b135-150">The `TreeViewItem` class implements the events for the drop operation.</span></span>
- <span data-ttu-id="0b135-151">Die `ViewModel`-Klasse fasst die Liste der Objekte in der Strukturansicht zusammen, damit Vorgänge wie Tastaturnavigation und Drag & Drop aus der ListView übernommen werden können.</span><span class="sxs-lookup"><span data-stu-id="0b135-151">The `ViewModel` class flattens the list of TreeViewItems so that operations such as keyboard navigation, and drag-and-drop can be inherited from ListView.</span></span>

## <a name="create-a-data-template-for-your-treeviewitem"></a><span data-ttu-id="0b135-152">Erstellen einer Datenvorlage für Ihre Objekte in der Strukturansicht</span><span class="sxs-lookup"><span data-stu-id="0b135-152">Create a data template for your TreeViewItem</span></span>

<span data-ttu-id="0b135-153">Hier sehen Sie einen Abschnitt der XAML, die die Datenvorlage für Ordner und Elemente, die keine Ordner sind, erstellt.</span><span class="sxs-lookup"><span data-stu-id="0b135-153">Here is the section of the XAML that sets up the data template for folder and non-folder type items.</span></span>
- <span data-ttu-id="0b135-154">Um ein Element der ListView als Ordner zu spezifizieren, müssen Sie explizit die [AllowDrop](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.allowdrop.aspx)-Eigenschaft auf **true** für dieses Element setzen.</span><span class="sxs-lookup"><span data-stu-id="0b135-154">To specify a ListViewItem as a folder, you will need to explicitly set the [AllowDrop](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.allowdrop.aspx) property to **true** on that ListViewItem.</span></span> <span data-ttu-id="0b135-155">Dieses XAML zeigt Ihnen eine Möglichkeit dafür.</span><span class="sxs-lookup"><span data-stu-id="0b135-155">This XAML shows you one way to do so.</span></span>
- <span data-ttu-id="0b135-156">Wenn Sie ein Element der ListView nicht als Ordner definieren wollen, müssen Sie keine Eigenschaft auf das Element selbst festlegen.</span><span class="sxs-lookup"><span data-stu-id="0b135-156">To specify a ListViewItem as a non-folder, you do not need to specify any property on the ListViewItem itself.</span></span> <span data-ttu-id="0b135-157">Setzen Sie einfach die AllowDrop-Eigenschaft in der ListView auf True.</span><span class="sxs-lookup"><span data-stu-id="0b135-157">Just set the AllowDrop property to True on the ListView.</span></span>
- <span data-ttu-id="0b135-158">Sie können die Symbole für ein- oder ausgeblendete Ordner bzw. Chevron-Zeichen benutzen, um visuell anzuzeigen, ob ein Ordner ein- oder ausgeblendet ist.</span><span class="sxs-lookup"><span data-stu-id="0b135-158">You can use expanded/collapsed folder icons or chevrons to visually indicate if a folder is expanded or collapsed.</span></span>
- <span data-ttu-id="0b135-159">Nutzen Sie die Möglichkeit, in diesem Beispiel verschiedene Symbole zu wählen, die für den ein- und ausgeklappten Zustand benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="0b135-159">You can use converters to choose the different icons needed for the expanded versus the collapsed state as seen in this example.</span></span>

```xaml
<!-- MainPage.xaml -->
<DataTemplate x:Key="TreeViewItemDataTemplate">
    <StackPanel Orientation="Horizontal" Height="40" Margin="{Binding Depth, Converter={StaticResource IntToIndConverter}}" AllowDrop="{Binding Data.IsFolder}">
        <FontIcon x:Name="expandCollapseChevron"
                  Glyph="{Binding IsExpanded, Converter={StaticResource expandCollapseGlyphConverter}}"
                  Visibility="{Binding Data.IsFolder, Converter={StaticResource booleanToVisibilityConverter}}"                           
                  FontSize="12"
                  Margin="12,8,12,8"
                  FontFamily="Segoe MDL2 Assets"                          
                  />
        <Grid>
            <FontIcon x:Name ="expandCollapseFolder"
                      Glyph="{Binding IsExpanded, Converter={StaticResource folderGlyphConverter}}"
                      Foreground="#FFFFE793"
                      FontSize="16"
                      Margin="0,8,12,8"
                      FontFamily="Segoe MDL2 Assets"
                      Visibility="{Binding Data.IsFolder, Converter={StaticResource booleanToVisibilityConverter}}"
                      />

            <FontIcon x:Name ="nonFolderIcon"
                      Glyph="&#xE160;"
                      Foreground="{ThemeResource SystemControlForegroundBaseLowBrush}"
                      FontSize="12"
                      Margin="20,8,12,8"
                      FontFamily="Segoe MDL2 Assets"
                      Visibility="{Binding Data.IsFolder, Converter={StaticResource inverseBooleanToVisibilityConverter}}"
                      />

            <FontIcon x:Name ="expandCollapseFolderOutline"
                      Glyph="{Binding IsExpanded, Converter={StaticResource folderOutlineGlyphConverter}}"
                      Foreground="#FFECC849"
                      FontSize="16"
                      Margin="0,8,12,8"
                      FontFamily="Segoe MDL2 Assets"
                      Visibility="{Binding Data.IsFolder, Converter={StaticResource booleanToVisibilityConverter}}"/>
        </Grid>

        <TextBlock Text="{Binding Data.Name}"
                   HorizontalAlignment="Stretch"
                   VerticalAlignment="Center"  
                   FontWeight="Medium"
                   FontFamily="Segoe MDL2 Assests"                           
                   Style="{ThemeResource BodyTextBlockStyle}"/>
    </StackPanel>
</DataTemplate>
```

## <a name="set-up-the-data-in-your-treeview"></a><span data-ttu-id="0b135-160">Richten Sie die Daten in der Strukturansicht ein</span><span class="sxs-lookup"><span data-stu-id="0b135-160">Set up the data in your TreeView</span></span>

<span data-ttu-id="0b135-161">Im Folgenden ist der Code, der die Daten in der beispielhaften Strukturansicht liefert.</span><span class="sxs-lookup"><span data-stu-id="0b135-161">Here is the code that sets up the data in the TreeView sample.</span></span>

```csharp
 public MainPage()
 {
     this.InitializeComponent();

     TreeNode workFolder = CreateFolderNode("Work Documents");
     workFolder.Add(CreateFileNode("Feature Functional Spec"));
     workFolder.Add(CreateFileNode("Feature Schedule"));
     workFolder.Add(CreateFileNode("Overall Project Plan"));
     workFolder.Add(CreateFileNode("Feature Resource allocation"));
     sampleTreeView.RootNode.Add(workFolder);

     TreeNode remodelFolder = CreateFolderNode("Home Remodel");
     remodelFolder.IsExpanded = true;
     remodelFolder.Add(CreateFileNode("Contactor Contact Information"));
     remodelFolder.Add(CreateFileNode("Paint Color Scheme"));
     remodelFolder.Add(CreateFileNode("Flooring woodgrain types"));
     remodelFolder.Add(CreateFileNode("Kitchen cabinet styles"));

     TreeNode personalFolder = CreateFolderNode("Personal Documents");
     personalFolder.IsExpanded = true;
     personalFolder.Add(remodelFolder);

     sampleTreeView.RootNode.Add(personalFolder);
 }

 private static TreeNode CreateFileNode(string name)
 {
     return new TreeNode() { Data = new FileSystemData(name) };
 }

 private static TreeNode CreateFolderNode(string name)
 {
     return new TreeNode() { Data = new FileSystemData(name) { IsFolder = true } };
 }
```

<span data-ttu-id="0b135-162">Sobald Sie mit den oben genannten Schritten fertig sind, erhalten Sie eine vollständig aufgefüllte Strukturansicht bzw. ein hierarchisches Layout mit n Verschachtelungen, Unterstützung für das Ein-/Ausblenden von Ordnern, die Drag & Drop-Funktion zwischen Ordnern und integrierte Eingabehilfen.</span><span class="sxs-lookup"><span data-stu-id="0b135-162">Once you’re done with the above steps, you will have a fully populated TreeView/Hierarchical layout with n-level nesting, support for expand/collapse of folders, dragging and dropping between folders, and accessibility built in.</span></span>

<span data-ttu-id="0b135-163">Um dem Benutzer die Möglichkeit zu geben, Elemente in der Strukturansicht hinzuzufügen oder zu entfernen, wird Ihnen empfohlen, ein Kontextmenü einzusetzen, welches dem Benutzer diese Optionen zugänglich macht.</span><span class="sxs-lookup"><span data-stu-id="0b135-163">To provide the user the ability to add/remove items from the TreeView, we recommend you add a context menu to expose those options to the user.</span></span>


## <a name="related-articles"></a><span data-ttu-id="0b135-164">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="0b135-164">Related articles</span></span>

- [<span data-ttu-id="0b135-165">Beispiel für die Strukturansicht</span><span class="sxs-lookup"><span data-stu-id="0b135-165">TreeView sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=785018)
- [**<span data-ttu-id="0b135-166">ListView</span><span class="sxs-lookup"><span data-stu-id="0b135-166">ListView</span></span>**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx)
- [<span data-ttu-id="0b135-167">ListView und Gitteransicht</span><span class="sxs-lookup"><span data-stu-id="0b135-167">ListView and GridView</span></span>](listview-and-gridview.md)
