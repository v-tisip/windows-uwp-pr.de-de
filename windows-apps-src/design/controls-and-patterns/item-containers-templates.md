---
author: muhsinking
Description: Use templates to modify the look of items in ListView or GridView controls.
title: Elementcontainer und Vorlagen
label: Item containers and templates
template: detail.hbs
ms.author: mukin
ms.date: 05/19/2017
ms.topic: article
keywords: Windows10, UWP
ms.assetid: d8eb818d-b62e-4314-a612-f29142dbd93f
pm-contact: predavid
design-contact: kimsea
dev-contact: ranjeshj
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: f5a9756a8afc267c9ec8763af49ba02714c2b4f0
ms.sourcegitcommit: e38b334edb82bf2b1474ba686990f4299b8f59c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6847440"
---
# <a name="item-containers-and-templates"></a><span data-ttu-id="ec515-103">Elementcontainer und Vorlagen</span><span class="sxs-lookup"><span data-stu-id="ec515-103">Item containers and templates</span></span>

 

<span data-ttu-id="ec515-104">Die **ListView**- und **GridView**-Steuerelemente verwalten, wie ihre Elemente angeordnet werden (horizontal, vertikal, an welcher Stelle der Umbruch in die nächste Zeile erfolgt, usw.), und wie die Benutzer mit den Elementen interagieren, nicht jedoch, wie die einzelnen Elemente auf dem Bildschirm angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ec515-104">**ListView** and **GridView** controls manage how their items are arranged (horizontal, vertical, wrapping, etc…) and how a user interacts with the items, but not how the individual items are shown on the screen.</span></span> <span data-ttu-id="ec515-105">Die Visualisierung der Elemente wird von Elementcontainern verwaltet.</span><span class="sxs-lookup"><span data-stu-id="ec515-105">Item visualization is managed by item containers.</span></span> <span data-ttu-id="ec515-106">Wenn Sie einer Listenansicht Elemente hinzufügen, werden diese automatisch in einem Container platziert.</span><span class="sxs-lookup"><span data-stu-id="ec515-106">When you add items to a list view they are automatically placed in a container.</span></span> <span data-ttu-id="ec515-107">Der Standardelementcontainer für ListView lautet [ListViewItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.listviewitem.aspx) und für GridView [GridViewItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.gridviewitem.aspx).</span><span class="sxs-lookup"><span data-stu-id="ec515-107">The default item container for ListView is [ListViewItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.listviewitem.aspx); for GridView, it’s [GridViewItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.gridviewitem.aspx).</span></span>

> <span data-ttu-id="ec515-108">**Wichtige APIs**: [ListView-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx), [GridView-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.gridview.aspx), [ItemTemplate-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemtemplate.aspx), [ItemContainerStyle-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemcontainerstyle.aspx)</span><span class="sxs-lookup"><span data-stu-id="ec515-108">**Important APIs**: [ListView class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx), [GridView class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.gridview.aspx), [ItemTemplate property](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemtemplate.aspx), [ItemContainerStyle property](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemcontainerstyle.aspx)</span></span>


> [!NOTE]
> <span data-ttu-id="ec515-109">Sowohl ListView als auch GridView sind von der Klasse [ListViewBase](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.aspx) abgeleitet, sodass sie dieselbe Funktionsweise haben, Daten jedoch unterschiedlich anzeigen.</span><span class="sxs-lookup"><span data-stu-id="ec515-109">ListView and GridView both derive from the [ListViewBase](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.aspx) class, so they have the same functionality, but display data differently.</span></span> <span data-ttu-id="ec515-110">In diesem Artikel beziehen sich Aussagen zur Listenansicht sowohl auf die ListView- als auch die GridView-Steuerelemente, falls nicht anders angegeben.</span><span class="sxs-lookup"><span data-stu-id="ec515-110">In this article, when we talk about list view, the info applies to both the ListView and GridView controls unless otherwise specified.</span></span> <span data-ttu-id="ec515-111">Möglicherweise werden Klassen wie ListView oder ListViewItem genannt. Das Präfix *List* kann jedoch durch *Grid* für das entsprechende Rastersteuerelement ersetzt werden (GridView oder GridViewItem).</span><span class="sxs-lookup"><span data-stu-id="ec515-111">We may refer to classes like ListView or ListViewItem, but the *List* prefix can be replaced with *Grid* for the corresponding grid equivalent (GridView or GridViewItem).</span></span> 

<span data-ttu-id="ec515-112">Diese Containersteuerelemente bestehen aus zwei wichtigen Komponenten, die zusammen die endgültige visuelle Darstellung für ein Element erstellen, die *Datenvorlage* und *Steuerelementvorlage*.</span><span class="sxs-lookup"><span data-stu-id="ec515-112">These container controls consist of two important parts that combine to create the final visuals shown for an item: the *data template* and the *control template*.</span></span>

- <span data-ttu-id="ec515-113">**Datenvorlage**: Sie legen ein [DataTemplate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.datatemplate.aspx) für die [ItemTemplate](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemtemplate.aspx) -Eigenschaft der Listenansicht fest, um anzugeben, wie die einzelnen Datenelemente angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ec515-113">**Data template** - You assign a [DataTemplate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.datatemplate.aspx) to the [ItemTemplate](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemtemplate.aspx) property of the list view to specify how individual data items are shown.</span></span>
- <span data-ttu-id="ec515-114">**Steuerelementvorlage**: Die Steuerelementvorlage ist die Komponente für die Visualisierung des Elements, für die das Framework verantwortlich ist, beispielsweise optische Zustände.</span><span class="sxs-lookup"><span data-stu-id="ec515-114">**Control template** - The control template provides the part of the item visualization that the framework is responsible for, like visual states.</span></span> <span data-ttu-id="ec515-115">Sie können die [ItemContainerStyle](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemcontainerstyle.aspx)-Eigenschaft verwenden, um die Steuerelementvorlage zu ändern.</span><span class="sxs-lookup"><span data-stu-id="ec515-115">You can use the [ItemContainerStyle](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemcontainerstyle.aspx) property to modify the control template.</span></span> <span data-ttu-id="ec515-116">In der Regel tun Sie dies, um die Farben der Listenansicht entsprechend Ihrem Branding zu ändern, oder um zu ändern, wie ausgewählte Elemente angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ec515-116">Typically, you do this to modify the list view colors to match your branding, or change how selected items are shown.</span></span>

<span data-ttu-id="ec515-117">Diese Abbildung zeigt, wie die Steuerelementvorlage und die Datenvorlage zusammen die endgültige optische Darstellung für ein Element festlegen.</span><span class="sxs-lookup"><span data-stu-id="ec515-117">This image shows how the control template and the data template combine to create the final visual for an item.</span></span>

![Listenansicht – Steuerelement- und Datenvorlagen](images/listview-visual-parts.png)

<span data-ttu-id="ec515-119">Nachstehend finden Sie den XAML-Code zur Erstellung dieser Elemente.</span><span class="sxs-lookup"><span data-stu-id="ec515-119">Here's the XAML that creates this item.</span></span> <span data-ttu-id="ec515-120">Die Vorlagen werden zu einem späteren Zeitpunkt erläutert.</span><span class="sxs-lookup"><span data-stu-id="ec515-120">We explain the templates later.</span></span>

```xaml
<ListView Width="220" SelectionMode="Multiple">
    <ListView.ItemTemplate>
        <DataTemplate x:DataType="x:String">
            <Grid Background="Yellow">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="54"/>
                    <ColumnDefinition/>
                </Grid.ColumnDefinitions>
                <Image Source="Assets/placeholder.png" Width="44" Height="44"
                       HorizontalAlignment="Left"/>
                <TextBlock Text="{x:Bind}" Foreground="Black"
                           FontSize="15" Grid.Column="1"
                           VerticalAlignment="Center"
                           Padding="0,0,54,0"/>
            </Grid>
        </DataTemplate>
    </ListView.ItemTemplate>
    <ListView.ItemContainerStyle>
        <Style TargetType="ListViewItem">
            <Setter Property="Background" Value="LightGreen"/>
        </Style>
    </ListView.ItemContainerStyle>
    <x:String>Item 1</x:String>
    <x:String>Item 2</x:String>
    <x:String>Item 3</x:String>
    <x:String>Item 4</x:String>
    <x:String>Item 5</x:String>
</ListView>
```
 
## <a name="prerequisites"></a><span data-ttu-id="ec515-121">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="ec515-121">Prerequisites</span></span>

- <span data-ttu-id="ec515-122">Es wird davon ausgegangen, dass Sie wissen, wie ein Listenansicht-Steuerelement verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ec515-122">We assume that you know how to use a list view control.</span></span> <span data-ttu-id="ec515-123">Weitere Informationen finden Sie in dem Artikel [ListView und GridView](listview-and-gridview.md).</span><span class="sxs-lookup"><span data-stu-id="ec515-123">For more info, see the [ListView and GridView](listview-and-gridview.md) article.</span></span>
- <span data-ttu-id="ec515-124">Weiterhin wird vorausgesetzt, dass Sie die Grundlagen zu Stilen und Vorlagen kennen, auch, wie Sie einen Stil inline oder als Ressource verwenden.</span><span class="sxs-lookup"><span data-stu-id="ec515-124">We also assume that you understand control styles and templates, including how to use a style inline or as a resource.</span></span> <span data-ttu-id="ec515-125">Weitere Informationen finden Sie unter [Formatieren von Steuerelementen](xaml-styles.md) und [Steuerelementvorlagen](control-templates.md).</span><span class="sxs-lookup"><span data-stu-id="ec515-125">For more info, see [Styling controls](xaml-styles.md) and [Control templates](control-templates.md).</span></span>

## <a name="the-data"></a><span data-ttu-id="ec515-126">Die Daten</span><span class="sxs-lookup"><span data-stu-id="ec515-126">The data</span></span>

<span data-ttu-id="ec515-127">Bevor wir tiefer in die Materie eintauchen, we Datenelemente in einer Listenansicht angezeigt werden, müssen wir die Daten, die angezeigt werden sollen, kennen.</span><span class="sxs-lookup"><span data-stu-id="ec515-127">Before we look deeper into how to show data items in a list view, we need to understand the data to be shown.</span></span> <span data-ttu-id="ec515-128">In diesem Beispiel erstellen wir einen Datentyp namens `NamedColor`.</span><span class="sxs-lookup"><span data-stu-id="ec515-128">In this example, we create a data type called `NamedColor`.</span></span> <span data-ttu-id="ec515-129">Es besteht aus einem Farbnamen, einem Farbwert und einem **SolidColorBrush**-Objekt für die Farbe, die als 3 Eigenschaften verfügbar sind, `Name`, `Color` und `Brush`.</span><span class="sxs-lookup"><span data-stu-id="ec515-129">It combines a color name, color value, and a **SolidColorBrush** for the color, which are exposed as 3 properties: `Name`, `Color`, and `Brush`.</span></span>
 
<span data-ttu-id="ec515-130">Anschließend wird der **Liste** für jede benannte Farbe in der Klasse [Colors](https://msdn.microsoft.com/library/windows/apps/windows.ui.colors.aspx) ein `NamedColor`-Objekt hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="ec515-130">We then populate a **List** with a `NamedColor` object for each named color in the [Colors](https://msdn.microsoft.com/library/windows/apps/windows.ui.colors.aspx) class.</span></span> <span data-ttu-id="ec515-131">Die Liste wird als [ItemsSource](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemssource.aspx) für die Listenansicht festgelegt.</span><span class="sxs-lookup"><span data-stu-id="ec515-131">The list is set as the [ItemsSource](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemssource.aspx) for the list view.</span></span>

<span data-ttu-id="ec515-132">Nachstehend finden Sie den Code, um die Klasse zu definiert und die `NamedColors`-Liste einzupflegen.</span><span class="sxs-lookup"><span data-stu-id="ec515-132">Here’s the code to define the class and populate the `NamedColors` list.</span></span>

**<span data-ttu-id="ec515-133">C#</span><span class="sxs-lookup"><span data-stu-id="ec515-133">C#</span></span>**
```csharp
using System.Collections.Generic;
using System.Linq;
using System.Reflection;
using Windows.UI;
using Windows.UI.Xaml.Controls;
using Windows.UI.Xaml.Media;

namespace ColorsListApp
{
    public sealed partial class MainPage : Page
    {
        // The list of colors won't change after it's populated, so we use List<T>. 
        // If the data can change, we should use an ObservableCollection<T> intead.
        List<NamedColor> NamedColors = new List<NamedColor>();

        public MainPage()
        {
            this.InitializeComponent();

            // Use reflection to get all the properties of the Colors class.
            IEnumerable<PropertyInfo> propertyInfos = typeof(Colors).GetRuntimeProperties();

            // For each property, create a NamedColor with the property name (color name),
            // and property value (color value). Add it the NamedColors list.
            for (int i = 0; i < propertyInfos.Count(); i++)
            {
                NamedColors.Add(new NamedColor(propertyInfos.ElementAt(i).Name,
                                    (Color)propertyInfos.ElementAt(i).GetValue(null)));
            }

            colorsListView.ItemsSource = NamedColors;
        }
    }

    class NamedColor
    {
        public NamedColor(string colorName, Color colorValue)
        {
            Name = colorName;
            Color = colorValue;
        }

        public string Name { get; set; }

        public Color Color { get; set; }

        public SolidColorBrush Brush
        {
            get { return new SolidColorBrush(Color); }
        }
    }
}
```

## <a name="data-template"></a><span data-ttu-id="ec515-134">Datenvorlage</span><span class="sxs-lookup"><span data-stu-id="ec515-134">Data template</span></span>

<span data-ttu-id="ec515-135">Sie geben eine Datenvorlage an, um der Listenansicht mitzuteilen, wie das Datenelement angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="ec515-135">You specify a data template to tell the list view how your data item should be shown.</span></span> 

<span data-ttu-id="ec515-136">Datenelemente werden in der Listenansicht standardmäßig als Zeichenfolgendarstellung des Datenobjekts angezeigt, an das sie gebunden sind.</span><span class="sxs-lookup"><span data-stu-id="ec515-136">By default, a data item is displayed in the list view as the string representation of the data object it's bound to.</span></span> <span data-ttu-id="ec515-137">Wenn Sie die „NamedColors“-Daten in einer Listenansicht anzeigen, ohne der Listenansicht mitzuteilen, wie sie aussehen sollten, wird der Inhalt so angezeigt, wie von der **ToString**-Methode zurückgegeben. Dies sieht dann so aus.</span><span class="sxs-lookup"><span data-stu-id="ec515-137">If you show the 'NamedColors' data in a list view without telling the list view how it should look, it just shows whatever the **ToString** method returns, like this.</span></span>

**<span data-ttu-id="ec515-138">XAML</span><span class="sxs-lookup"><span data-stu-id="ec515-138">XAML</span></span>**
```xaml
<ListView x:Name="colorsListView"/>
```

![Listenansicht mit einer Zeichenfolgendarstellung der Elemente](images/listview-no-template.png)

<span data-ttu-id="ec515-140">Sie können die Zeichenfolgendarstellung einer bestimmten Eigenschaft des Datenelements anzeigen, indem Sie den [DisplayMemberPath](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.displaymemberpath.aspx) zur Eigenschaft festlegen.</span><span class="sxs-lookup"><span data-stu-id="ec515-140">You can show the string representation of a particular property of the data item by setting the [DisplayMemberPath](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.displaymemberpath.aspx) to that property.</span></span> <span data-ttu-id="ec515-141">Hier legen Sie „DisplayMemberPath“ auf den Wert für die `Name`-Eigenschaft des `NamedColor`-Elements fest.</span><span class="sxs-lookup"><span data-stu-id="ec515-141">Here, you set DisplayMemberPath to the `Name` property of the `NamedColor` item.</span></span>

**<span data-ttu-id="ec515-142">XAML</span><span class="sxs-lookup"><span data-stu-id="ec515-142">XAML</span></span>**
```xaml
<ListView x:Name="colorsListView" DisplayMemberPath="Name" />
```

<span data-ttu-id="ec515-143">Die Listenansicht zeigt jetzt die Elemente nach Namen sortiert an, wie in dieser hier dargestellt.</span><span class="sxs-lookup"><span data-stu-id="ec515-143">The list view now displays items by name, as shown here.</span></span> <span data-ttu-id="ec515-144">Das ist bereits sinnvoller, aber diese Darstellung ist nicht sehr interessant und bewirkt, dass viele Informationen ausgeblendet bleiben.</span><span class="sxs-lookup"><span data-stu-id="ec515-144">It’s more useful, but it’s not very interesting and leaves a lot of information hidden.</span></span>

![Listenansicht mit einer Zeichenfolgendarstellung einer Element-Eigenschaft](images/listview-display-member-path.png)

<span data-ttu-id="ec515-146">In der Regel möchten Sie eine ansprechendere Darstellung Ihrer Daten anzeigen.</span><span class="sxs-lookup"><span data-stu-id="ec515-146">You typically want to show a more rich presentation of your data.</span></span> <span data-ttu-id="ec515-147">Um genau anzugeben, wie Elemente in der Listenansicht angezeigt werden, müssen Sie ein [DataTemplate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.datatemplate.aspx) erstellen.</span><span class="sxs-lookup"><span data-stu-id="ec515-147">To specify exactly how items in the list view are displayed, you create a [DataTemplate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.datatemplate.aspx).</span></span> <span data-ttu-id="ec515-148">Der XAML-Code in der DataTemplate definiert das Layout und die Darstellung von Steuerelementen, die zum Anzeigen eines einzelnen Elements verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ec515-148">The XAML in the DataTemplate defines the layout and appearance of controls used to display an individual item.</span></span> <span data-ttu-id="ec515-149">Die Steuerelemente im Layout können an Eigenschaften eines Datenobjekts gebunden werden. Es ist auch möglich, statischen Inhalt intern zu definieren.</span><span class="sxs-lookup"><span data-stu-id="ec515-149">The controls in the layout can be bound to properties of a data object, or have static content defined inline.</span></span> <span data-ttu-id="ec515-150">Weisen Sie das DataTemplate der [ItemTemplate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemtemplate.aspx)-Eigenschaft des Listensteuerelements zu.</span><span class="sxs-lookup"><span data-stu-id="ec515-150">You assign the DataTemplate to the [ItemTemplate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemtemplate.aspx) property of the list control.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec515-151">Sie können **ItemTemplate** und **DisplayMemberPath** nicht gleichzeitig verwenden.</span><span class="sxs-lookup"><span data-stu-id="ec515-151">You can’t use a **ItemTemplate** and **DisplayMemberPath** at the same time.</span></span> <span data-ttu-id="ec515-152">Wenn beide Eigenschaften festgelegt sind, wird eine Ausnahmebedingung ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="ec515-152">If both properties are set, an exception occurs.</span></span>

<span data-ttu-id="ec515-153">Hier definieren Sie ein DataTemplate-Objekt, das ein [Rechteck](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.rectangle.aspx) in der Farbe des Elements zusammen mit dem Farbnamen und den RGB-Werten anzeigt.</span><span class="sxs-lookup"><span data-stu-id="ec515-153">Here, you define a DataTemplate that shows a [Rectangle](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.rectangle.aspx) in the color of the item, along with the color name and RGB values.</span></span> 

> [!NOTE]
> <span data-ttu-id="ec515-154">Wenn Sie die [x:Bind-Markuperweiterung](https://msdn.microsoft.com/windows/uwp/xaml-platform/x-bind-markup-extension) in DataTemplate verwenden, müssen Sie DataType (`x:DataType`) für DataTemplate angeben.</span><span class="sxs-lookup"><span data-stu-id="ec515-154">When you use the [x:Bind markup extension](https://msdn.microsoft.com/windows/uwp/xaml-platform/x-bind-markup-extension) in a DataTemplate, you have to specify the DataType (`x:DataType`) on the DataTemplate.</span></span>

**<span data-ttu-id="ec515-155">XAML</span><span class="sxs-lookup"><span data-stu-id="ec515-155">XAML</span></span>**
```XAML
<ListView x:Name="colorsListView">
    <ListView.ItemTemplate>
        <DataTemplate x:DataType="local:NamedColor">
            <Grid>
                <Grid.ColumnDefinitions>
                    <ColumnDefinition MinWidth="54"/>
                    <ColumnDefinition Width="32"/>
                    <ColumnDefinition Width="32"/>
                    <ColumnDefinition Width="32"/>
                    <ColumnDefinition/>
                </Grid.ColumnDefinitions>
                <Grid.RowDefinitions>
                    <RowDefinition/>
                    <RowDefinition/>
                </Grid.RowDefinitions>
                <Rectangle Width="44" Height="44" Fill="{x:Bind Brush}" Grid.RowSpan="2"/>
                <TextBlock Text="{x:Bind Name}" Grid.Column="1" Grid.ColumnSpan="4"/>
                <TextBlock Text="{x:Bind Color.R}" Grid.Column="1" Grid.Row="1" Foreground="Red"/>
                <TextBlock Text="{x:Bind Color.G}" Grid.Column="2" Grid.Row="1" Foreground="Green"/>
                <TextBlock Text="{x:Bind Color.B}" Grid.Column="3" Grid.Row="1" Foreground="Blue"/>
            </Grid>
        </DataTemplate>
    </ListView.ItemTemplate>
</ListView>
```

<span data-ttu-id="ec515-156">So sehen die Datenelemente aus, wenn sie mit dieser Datenvorlage angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ec515-156">Here's what the data items look like when they're displayed with this data template.</span></span>

![Elemente in der Listenansicht mit einer Datenvorlage](images/listview-data-template-0.png)

<span data-ttu-id="ec515-158">Möglicherweise möchten Sie die Daten in einem GridView anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="ec515-158">You might want to show the data in a GridView.</span></span> <span data-ttu-id="ec515-159">Hier sehen Sie eine andere Datenvorlage, die die Daten besser geeignet für ein Rasterlayout anzeigt.</span><span class="sxs-lookup"><span data-stu-id="ec515-159">Here's another data template that displays the data in a way that's more appropriate for a grid layout.</span></span> <span data-ttu-id="ec515-160">Dieses Mal ist die Datenvorlage als Ressource definiert, nicht in dem XAML-Code für das GridView-Objekt.</span><span class="sxs-lookup"><span data-stu-id="ec515-160">This time, the data template is defined as a resource rather than inline with the XAML for the GridView.</span></span>


**<span data-ttu-id="ec515-161">XAML</span><span class="sxs-lookup"><span data-stu-id="ec515-161">XAML</span></span>**
```xaml
<Page.Resources>
    <DataTemplate x:Key="namedColorItemGridTemplate" x:DataType="local:NamedColor">
        <Grid>
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="32"/>
                <ColumnDefinition Width="32"/>
                <ColumnDefinition Width="32"/>
            </Grid.ColumnDefinitions>
            <Grid.RowDefinitions>
                <RowDefinition Height="96"/>
                <RowDefinition/>
                <RowDefinition/>
            </Grid.RowDefinitions>
    
            <Rectangle Width="96" Height="96" Fill="{x:Bind Brush}" Grid.ColumnSpan="3" />
            <!-- Name -->
            <Border Background="#AAFFFFFF" Grid.ColumnSpan="3" Height="40" VerticalAlignment="Top">
                <TextBlock Text="{x:Bind Name}" TextWrapping="Wrap" Margin="4,0,0,0"/>
            </Border>
            <!-- RGB -->
            <Border Background="Gainsboro" Grid.Row="1" Grid.ColumnSpan="3"/>
            <TextBlock Text="{x:Bind Color.R}" Foreground="Red"
                   Grid.Column="0" Grid.Row="1" HorizontalAlignment="Center"/>
            <TextBlock Text="{x:Bind Color.G}" Foreground="Green"
                   Grid.Column="1" Grid.Row="1" HorizontalAlignment="Center"/>
            <TextBlock Text="{x:Bind Color.B}" Foreground="Blue" 
                   Grid.Column="2" Grid.Row="1" HorizontalAlignment="Center"/>
            <!-- HEX -->
            <Border Background="Gray" Grid.Row="2" Grid.ColumnSpan="3">
                <TextBlock Text="{x:Bind Color}" Foreground="White" Margin="4,0,0,0"/>
            </Border>
        </Grid>
    </DataTemplate>
</Page.Resources>

...

<GridView x:Name="colorsGridView" 
          ItemTemplate="{StaticResource namedColorItemGridTemplate}"/>
```

<span data-ttu-id="ec515-162">Wenn die Daten mithilfe dieser Datenvorlage in einem Raster angezeigt werden, sieht dies wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="ec515-162">When the data is shown in a grid using this data template, it looks like this.</span></span>

![Elemente in der Rasteransicht mit einer Datenvorlage](images/gridview-data-template.png)

### <a name="performance-considerations"></a><span data-ttu-id="ec515-164">Leistungsaspekte</span><span class="sxs-lookup"><span data-stu-id="ec515-164">Performance considerations</span></span>

<span data-ttu-id="ec515-165">Datenvorlagen sind der bevorzugte Weg für die Definition des Aussehens Ihrer Listenansicht.</span><span class="sxs-lookup"><span data-stu-id="ec515-165">Data templates are the primary way you define the look of your list view.</span></span> <span data-ttu-id="ec515-166">Sie können auch eine erhebliche Auswirkung auf die Leistung haben, wenn in der Liste eine große Anzahl von Elementen angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ec515-166">They can also have a significant impact on performance if your list displays a large number of items.</span></span> 

<span data-ttu-id="ec515-167">Bei einer Datenvorlage wird für jedes Element in der Listenansicht eine Instanz von jedem XAML-Elements erstellt.</span><span class="sxs-lookup"><span data-stu-id="ec515-167">An instance of every XAML element in a data template is created for each item in the list view.</span></span> <span data-ttu-id="ec515-168">Die Rastervorlage im vorherigen Beispiel hat beispielsweise 10XAML-Elemente (1Raster, 1Rechteck, 3Rahmen, 5Textblöcke).</span><span class="sxs-lookup"><span data-stu-id="ec515-168">For example, the grid template in the previous example has 10 XAML elements (1 Grid, 1 Rectangle, 3 Borders, 5 TextBlocks).</span></span> <span data-ttu-id="ec515-169">Bei einer GridView, die auf dem Bildschirm mithilfe dieser Datenvorlage 20Elemente anzeigt, werden mindestens 200Elemente (20\*10=200) erstellt.</span><span class="sxs-lookup"><span data-stu-id="ec515-169">A GridView that shows 20 items on screen using this data template creates at least 200 elements (20\*10=200).</span></span> <span data-ttu-id="ec515-170">Wenn Sie die Anzahl der Elemente in einer Datenvorlage verringern, kann die Gesamtanzahl der Elemente, die für die Listenansicht erstellt werden müssen, erheblich reduziert werden.</span><span class="sxs-lookup"><span data-stu-id="ec515-170">Reducing the number of elements in a data template can greatly reduce the total number of elements created for your list view.</span></span> <span data-ttu-id="ec515-171">Weitere Informationen finden Sie unter [ListView und GridView-UI Optimierung: Reduzierung der Anzahl der Element pro Element](https://msdn.microsoft.com/windows/uwp/debug-test-perf/optimize-gridview-and-listview#element-reduction-per-item).</span><span class="sxs-lookup"><span data-stu-id="ec515-171">For more info, see [ListView and GridView UI optimization: Element count reduction per item](https://msdn.microsoft.com/windows/uwp/debug-test-perf/optimize-gridview-and-listview#element-reduction-per-item).</span></span>

 <span data-ttu-id="ec515-172">Betrachten Sie diesen Ausschnitt der Rasterdatenvorlage.</span><span class="sxs-lookup"><span data-stu-id="ec515-172">Consider this section  of the grid data template.</span></span> <span data-ttu-id="ec515-173">Sehen wir uns an, wodurch wir die Anzahl der Elemente verringern können.</span><span class="sxs-lookup"><span data-stu-id="ec515-173">Let's look at a few things that reduce the element count.</span></span>

**<span data-ttu-id="ec515-174">XAML</span><span class="sxs-lookup"><span data-stu-id="ec515-174">XAML</span></span>**
```xaml
<!-- RGB -->
<Border Background="Gainsboro" Grid.Row="1" Grid.ColumnSpan="3"/>
<TextBlock Text="{x:Bind Color.R}" Foreground="Red"
           Grid.Column="0" Grid.Row="1" HorizontalAlignment="Center"/>
<TextBlock Text="{x:Bind Color.G}" Foreground="Green"
           Grid.Column="1" Grid.Row="1" HorizontalAlignment="Center"/>
<TextBlock Text="{x:Bind Color.B}" Foreground="Blue" 
           Grid.Column="2" Grid.Row="1" HorizontalAlignment="Center"/>
```

 - <span data-ttu-id="ec515-175">Erstens: Das Layout verwendet nur ein Raster.</span><span class="sxs-lookup"><span data-stu-id="ec515-175">First, the layout uses a single Grid.</span></span> <span data-ttu-id="ec515-176">Sie verwenden ein einspaltiges Raster und platzieren diese 3Textblöcke in ein „StackPanel“-Objekt, aber in einer Datenvorlage, die in vielfältigen Varianten erstellt wird, sollten Sie nach Möglichkeiten suchen, die Einbettung von Layoutpanels in andere Layoutpanele zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="ec515-176">You could have a single-column Grid and place these 3 TextBlocks in a StackPanel, but in a data template that gets created many times, you should look for ways to avoid embedding layout panels within other layout panels.</span></span>
 - <span data-ttu-id="ec515-177">Zweitens: Sie können ein „Border“-Steuerelement verwenden, mit dem ein Hintergrund gerendert wird, ohne dass wirklich Elemente innerhalb des „Border“-Elements positioniert werden.</span><span class="sxs-lookup"><span data-stu-id="ec515-177">Second, you can use a Border control to render a background without actually placing items within the Border element.</span></span> <span data-ttu-id="ec515-178">Ein „Border“-Element kann nur ein untergeordnetes Element haben, daher benötigen Sie ein zusätzliches Layoutpanel für die 3„TextBlock“-Elemente in dem „Border“-Element in dem XAML-Code.</span><span class="sxs-lookup"><span data-stu-id="ec515-178">A Border element can have only one child element, so you would need to add an additional layout panel to host the 3 TextBlock elements within the Border element in XAML.</span></span> <span data-ttu-id="ec515-179">Da die „TextBlock“-Elemente nicht dem „Border“-Element untergeordnet werden, benötigen Sie kein Panel, um diese Textblöcke aufzunehmen.</span><span class="sxs-lookup"><span data-stu-id="ec515-179">By not making the TextBlocks children of the Border, you eliminate the need for a panel to hold the TextBlocks.</span></span>
 - <span data-ttu-id="ec515-180">Schließlich können Sie die Textblöcke innerhalb eines StackPanel-Elements platzieren und die Rahmeneigenschaften an dem StackPanel-Element festlegen statt über eine explizites „Border“-Element.</span><span class="sxs-lookup"><span data-stu-id="ec515-180">Finally, you could place the TextBlocks inside a StackPanel, and set the border properties on the StackPanel rather than using an explicit Border element.</span></span> <span data-ttu-id="ec515-181">Das „Border“-Element ist jedoch ein weniger Ressourcen beanspruchendes Steuerelement als das StackPanel-Element. Damit wirkt es sich weniger nachteilig auf die Systemleistung aus, wenn das Element häufig neu gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="ec515-181">However, the Border element is a more lightweight control than a StackPanel, so it has less of an impact on performance when rendered many times over.</span></span>

## <a name="control-template"></a><span data-ttu-id="ec515-182">Steuerelementvorlage</span><span class="sxs-lookup"><span data-stu-id="ec515-182">Control template</span></span>
<span data-ttu-id="ec515-183">Eine Steuerelementvorlage für ein Element enthält die optischen Elemente zur Anzeige des Zustands wie Auswahl, Draufzeigen und Fokus.</span><span class="sxs-lookup"><span data-stu-id="ec515-183">An item’s control template contains the visuals that display state, like selection, pointer over, and focus.</span></span> <span data-ttu-id="ec515-184">Diese visuellen Elemente werden über oder unter der Datenvorlage gerendert.</span><span class="sxs-lookup"><span data-stu-id="ec515-184">These visuals are rendered either on top of or below the data template.</span></span> <span data-ttu-id="ec515-185">Hier ist eine Liste mit häufig verwendeten visuellen Standardelementen, wie sie von der ListView-Steuerelementvorlage gezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="ec515-185">Some of the common default visuals drawn by the ListView control template are shown here.</span></span>

- <span data-ttu-id="ec515-186">Draufzeigen: Eine hellgraues Rechteck, das unter der Datenvorlage gezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="ec515-186">Hover – A light gray rectangle drawn below the data template.</span></span>  
- <span data-ttu-id="ec515-187">Auswahl: Eine hellblaues Rechteck, das unter der Datenvorlage gezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="ec515-187">Selection – A light blue rectangle drawn below the data template.</span></span> 
- <span data-ttu-id="ec515-188">Tastaturfokus: Ein schwarzweiß gepunkteter Rahmen, der über der Datenvorlage gezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="ec515-188">Keyboard focus– A black and white dotted border drown on top of the item template.</span></span> 

![Visuelle Elemente zum Anzeigen des Zustands in Listenansichten](images/listview-state-visuals.png)

<span data-ttu-id="ec515-190">Die Listenansicht kombiniert die Elemente aus der Datenvorlage und aus der Steuerelementvorlage, um die endgültigen visuellen Elemente zu erstellen, die auf dem Bildschirm gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="ec515-190">The list view combines the elements from the data template and control template to create the final visuals rendered on the screen.</span></span> <span data-ttu-id="ec515-191">Hier werden die visuellen Elemente für den Zustand im Kontext einer Listenansicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ec515-191">Here, the state visuals are shown in the context of a list view.</span></span>

![Listenansicht mit Elementen in unterschiedlichen Zuständen](images/listview-states.png)

### <a name="listviewitempresenter"></a><span data-ttu-id="ec515-193">ListViewItemPresenter</span><span class="sxs-lookup"><span data-stu-id="ec515-193">ListViewItemPresenter</span></span>

<span data-ttu-id="ec515-194">Wie bereits zuvor bei den Datenvorlagen erwähnt kann die Anzahl der für die einzelnen Elemente erstellten XAML-Elemente XAML erhebliche Auswirkungen auf die Leistung einer Listenansicht haben.</span><span class="sxs-lookup"><span data-stu-id="ec515-194">As we noted previously about data templates, the number of XAML elements created for each item can have a significant impact on the performance of a list view.</span></span> <span data-ttu-id="ec515-195">Da die Datenvorlage und die Steuerelementvorlage kombiniert werden, um die einzelnen Elemente anzuzeigen, stellen auch die Elemente aus beiden Vorlagen einen Faktor bei der Bestimmung der tatsächlichen Anzahl der für die Anzeige benötigten Elemente dar.</span><span class="sxs-lookup"><span data-stu-id="ec515-195">Because the data template and control template are combined to display each item, the actual number of elements needed to display an item includes the elements in both templates.</span></span>

<span data-ttu-id="ec515-196">Die Steuerelemente „ListView“ und „GridView“ sind dahingegehend optimiert, dass die Anzahl der pro Element erstellten XAML-Elemente reduziert wird.</span><span class="sxs-lookup"><span data-stu-id="ec515-196">The ListView and GridView controls are optimized to reduce the number of XAML elements created per item.</span></span> <span data-ttu-id="ec515-197">Die visuellen Elemente für **ListViewItem** werden über den [ListViewItemPresenter](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.listviewitempresenter.aspx) erstellt. Dies ist ein spezielles XAML-Element, das komplexe visuelle Objekte für Fokus, Auswahl und andere visuelle Zustände anzeigt, ohne dass zahlreiche UIElements verwaltet werden müssen.</span><span class="sxs-lookup"><span data-stu-id="ec515-197">The **ListViewItem** visuals are created by the [ListViewItemPresenter](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.listviewitempresenter.aspx), which is a special XAML element that displays complex visuals for focus, selection, and other visual states, without the overhead of numerous UIElements.</span></span>
 
> [!NOTE]
> <span data-ttu-id="ec515-198">In UWP-Apps für Windows10 verwendet sowohl **ListViewItem** als auch **GridViewItem** den **ListViewItemPresenter**. „GridViewItemPresenter“ ist veraltet und sollte nicht mehr verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ec515-198">In UWP apps for Windows 10, both **ListViewItem** and **GridViewItem** use **ListViewItemPresenter**; the GridViewItemPresenter is deprecated and you should not use it.</span></span> <span data-ttu-id="ec515-199">ListViewItem und GridViewItem werden standardmäßig unterschiedlich angezeigt, weil sie für ListViewItemPresenter unterschiedliche Eigenschaftswerte festlegen.)</span><span class="sxs-lookup"><span data-stu-id="ec515-199">ListViewItem and GridViewItem set different property values on ListViewItemPresenter to achieve different default looks.)</span></span>

<span data-ttu-id="ec515-200">Um das Aussehen der Elementcontainer zu ändern, verwenden Sie die [ItemContainerStyle](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemcontainerstyle.aspx)-Eigenschaft und stellen Sie einen [Stil](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.style.aspx) bereit, indem Sie für den zugehörigen [TargetType](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.style.targettype.aspx) **ListViewItem** oder **GridViewItem** als Wert festlegen.</span><span class="sxs-lookup"><span data-stu-id="ec515-200">To modify the look of the item container, use the [ItemContainerStyle](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemcontainerstyle.aspx) property and provide a [Style](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.style.aspx) with its [TargetType](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.style.targettype.aspx) set to **ListViewItem** or **GridViewItem**.</span></span>

<span data-ttu-id="ec515-201">In diesem Beispiel fügen Sie dem ListViewItem Abstände hinzu, um die Elemente in der Liste deutlicher voneinander zu trennen.</span><span class="sxs-lookup"><span data-stu-id="ec515-201">In this example, you add padding to the ListViewItem to create some space between the items in the list.</span></span>

```xaml
<ListView x:Name="colorsListView">
    <ListView.ItemTemplate>
        <!-- DataTemplate XAML shown in previous ListView example -->
    </ListView.ItemTemplate>

    <ListView.ItemContainerStyle>
        <Style TargetType="ListViewItem">
            <Setter Property="Padding" Value="0,4"/>
        </Style>
    </ListView.ItemContainerStyle>
</ListView>
```

<span data-ttu-id="ec515-202">Jetzt sieht die Listenansicht mit etwas mehr Platz zwischen den Elementen so aus.</span><span class="sxs-lookup"><span data-stu-id="ec515-202">Now the list view looks like this with space between the items.</span></span>

![Elemente in der Listenansicht mit Abständen](images/listview-data-template-1.png)

<span data-ttu-id="ec515-204">Im Standardstil des ListViewItem ist die **ContentMargin**-Eigenschaft des ListViewItemPresenter über ein [TemplateBinding](https://msdn.microsoft.com/windows/uwp/xaml-platform/templatebinding-markup-extension) mit der **Padding**-Eigenschaft des ListViewItem verknüpft (`<ListViewItemPresenter ContentMargin="{TemplateBinding Padding}"/>`).</span><span class="sxs-lookup"><span data-stu-id="ec515-204">In the ListViewItem default style, the ListViewItemPresenter **ContentMargin** property has a [TemplateBinding](https://msdn.microsoft.com/windows/uwp/xaml-platform/templatebinding-markup-extension) to the ListViewItem **Padding** property (`<ListViewItemPresenter ContentMargin="{TemplateBinding Padding}"/>`).</span></span> <span data-ttu-id="ec515-205">Wenn wir die „Padding“-Eigenschaft festlegen, wird dieser Wert eigentlich an die „ContentMargin“-Eigenschaft des „ListViewItemPresenter“ übergeben.</span><span class="sxs-lookup"><span data-stu-id="ec515-205">When we set the Padding property, that value is really being passed to the ListViewItemPresenter ContentMargin property.</span></span>

<span data-ttu-id="ec515-206">Um andere ListViewItemPresenter-Eigenschaften zu ändern, die nicht per Vorlage an ListViewItems-Eigenschaften gebunden sind, müssen Sie die Vorlage für ListViewItem mit einem neuen ListViewItemPresenter umschreiben, dessen Eigenschaften Sie dann ändern können.</span><span class="sxs-lookup"><span data-stu-id="ec515-206">To modify other ListViewItemPresenter properties that aren't template bound to ListViewItems properties, you need to retemplate the ListViewItem with a new ListViewItemPresenter that you can modify properties on.</span></span> 

> [!NOTE]
> <span data-ttu-id="ec515-207">Mit den Standardformaten von ListViewItem und GridViewItem werden zahlreiche Eigenschaften für ListViewItemPresenter festgelegt.</span><span class="sxs-lookup"><span data-stu-id="ec515-207">ListViewItem and GridViewItem default styles set a lot of properties on ListViewItemPresenter.</span></span> <span data-ttu-id="ec515-208">Es wird empfohlen, mit einer Kopie des Standardstils zu beginnen und nur die Eigenschaften zu ändern, bei denen dies erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="ec515-208">You should always start with a copy of the default style and modify only the properties you need too.</span></span> <span data-ttu-id="ec515-209">Andernfalls werden die visuellen Elemente wahrscheinlich nicht so wie angezeigt, die Sie es erwarten, da einige Eigenschaften nicht richtig festgelegt sein werden.</span><span class="sxs-lookup"><span data-stu-id="ec515-209">Otherwise, the visuals will probably not show up the way you expect because some properties won't be set correctly.</span></span>

**<span data-ttu-id="ec515-210">So erstellen Sie eine Kopie der Standardvorlage in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ec515-210">To make a copy of the default template in Visual Studio</span></span>**
 
1. <span data-ttu-id="ec515-211">Öffnen Sie das Dokumentgliederungsfenster (**Ansicht > Andere Fenster > Dokumentgliederung**).</span><span class="sxs-lookup"><span data-stu-id="ec515-211">Open the Document Outline pane (**View > Other Windows > Document Outline**).</span></span>
2. <span data-ttu-id="ec515-212">Wählen Sie das Listen- oder Rasterelement aus, das Sie ändern möchten.</span><span class="sxs-lookup"><span data-stu-id="ec515-212">Select the list or grid element to modify.</span></span> <span data-ttu-id="ec515-213">In diesem Beispiel ändern Sie das `colorsGridView`-Element.</span><span class="sxs-lookup"><span data-stu-id="ec515-213">In this example, you modify the `colorsGridView` element.</span></span>
3. <span data-ttu-id="ec515-214">Klicken mit der rechten Maustaste, und wählen Sie **Weitere Vorlagen bearbeiten > Erzeugten Elementcontainer bearbeiten (ItemContainerStyle) > Kopie bearbeiten**.</span><span class="sxs-lookup"><span data-stu-id="ec515-214">Right-click and select **Edit Additional Templates > Edit Generated Item Container (ItemContainerStyle) > Edit a Copy**.</span></span>
    ![Visual Studio-Editor](images/listview-itemcontainerstyle-vs.png)
4. <span data-ttu-id="ec515-216">Geben Sie im Dialogfeld „Stilressource erstellen“ einen Namen für den Stil ein.</span><span class="sxs-lookup"><span data-stu-id="ec515-216">In the Create Style Resource dialog, enter a name for the style.</span></span> <span data-ttu-id="ec515-217">In diesem Beispiel verwenden Sie `colorsGridViewItemStyle`.</span><span class="sxs-lookup"><span data-stu-id="ec515-217">In this example, you use `colorsGridViewItemStyle`.</span></span>
    <span data-ttu-id="ec515-218">![Visual Studio-Dialogfeld „Stilressource erstellen“ (images/listview-style-resource-vs.png)</span><span class="sxs-lookup"><span data-stu-id="ec515-218">![Visual Studio Create Style Resource dialog(images/listview-style-resource-vs.png)</span></span>

<span data-ttu-id="ec515-219">Anschließend wird Ihrer App eine Kopie des Standardstils als Ressource hinzugefügt, und die **GridView.ItemContainerStyle**-Eigenschaft wird auf diese Ressource festgelegt, wie in diesem XAML-Code dargestellt.</span><span class="sxs-lookup"><span data-stu-id="ec515-219">A copy of the default style is added to your app as a resource, and the **GridView.ItemContainerStyle** property is set to that resource, as shown in this XAML.</span></span> 

```xaml
<Style x:Key="colorsGridViewItemStyle" TargetType="GridViewItem">
    <Setter Property="FontFamily" Value="{ThemeResource ContentControlThemeFontFamily}"/>
    <Setter Property="FontSize" Value="{ThemeResource ControlContentThemeFontSize}" />
    <Setter Property="Background" Value="Transparent"/>
    <Setter Property="Foreground" Value="{ThemeResource SystemControlForegroundBaseHighBrush}"/>
    <Setter Property="TabNavigation" Value="Local"/>
    <Setter Property="IsHoldingEnabled" Value="True"/>
    <Setter Property="HorizontalContentAlignment" Value="Center"/>
    <Setter Property="VerticalContentAlignment" Value="Center"/>
    <Setter Property="Margin" Value="0,0,4,4"/>
    <Setter Property="MinWidth" Value="{ThemeResource GridViewItemMinWidth}"/>
    <Setter Property="MinHeight" Value="{ThemeResource GridViewItemMinHeight}"/>
    <Setter Property="Template">
        <Setter.Value>
            <ControlTemplate TargetType="GridViewItem">
                <ListViewItemPresenter 
                    CheckBrush="{ThemeResource SystemControlForegroundBaseMediumHighBrush}" 
                    ContentMargin="{TemplateBinding Padding}" 
                    CheckMode="Overlay" 
                    ContentTransitions="{TemplateBinding ContentTransitions}" 
                    CheckBoxBrush="{ThemeResource SystemControlBackgroundChromeMediumBrush}" 
                    DragForeground="{ThemeResource ListViewItemDragForegroundThemeBrush}" 
                    DragOpacity="{ThemeResource ListViewItemDragThemeOpacity}" 
                    DragBackground="{ThemeResource ListViewItemDragBackgroundThemeBrush}" 
                    DisabledOpacity="{ThemeResource ListViewItemDisabledThemeOpacity}" 
                    FocusBorderBrush="{ThemeResource SystemControlForegroundAltHighBrush}" 
                    FocusSecondaryBorderBrush="{ThemeResource SystemControlForegroundBaseHighBrush}" 
                    HorizontalContentAlignment="{TemplateBinding HorizontalContentAlignment}" 
                    PointerOverForeground="{ThemeResource SystemControlForegroundBaseHighBrush}" 
                    PressedBackground="{ThemeResource SystemControlHighlightListMediumBrush}" 
                    PlaceholderBackground="{ThemeResource ListViewItemPlaceholderBackgroundThemeBrush}" 
                    PointerOverBackground="{ThemeResource SystemControlHighlightListLowBrush}" 
                    ReorderHintOffset="{ThemeResource GridViewItemReorderHintThemeOffset}" 
                    SelectedPressedBackground="{ThemeResource SystemControlHighlightListAccentHighBrush}" 
                    SelectionCheckMarkVisualEnabled="True" 
                    SelectedForeground="{ThemeResource SystemControlForegroundBaseHighBrush}" 
                    SelectedPointerOverBackground="{ThemeResource SystemControlHighlightListAccentMediumBrush}" 
                    SelectedBackground="{ThemeResource SystemControlHighlightAccentBrush}" 
                    VerticalContentAlignment="{TemplateBinding VerticalContentAlignment}"/>
            </ControlTemplate>
        </Setter.Value>
    </Setter>
</Style>

...

<GridView x:Name="colorsGridView" ItemContainerStyle="{StaticResource colorsGridViewItemStyle}"/>
```

<span data-ttu-id="ec515-220">Jetzt können Sie Eigenschaften für den ListViewItemPresenter ändern, so dass Sie die Kontrollkästchen für Auswahl, die Positionierung der Elemente und die Pinselfarben für die visuelle Zustände ändern können.</span><span class="sxs-lookup"><span data-stu-id="ec515-220">You can now modify properties on the ListViewItemPresenter to control the selection check box, item positioning, and brush colors for visual states.</span></span> 

#### <a name="inline-and-overlay-selection-visuals"></a><span data-ttu-id="ec515-221">Inline und Overlay Auswahlelemente</span><span class="sxs-lookup"><span data-stu-id="ec515-221">Inline and Overlay selection visuals</span></span>

<span data-ttu-id="ec515-222">ListView und GridView weisen, je nach Steuerelement und [SelectionMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.selectionmode.aspx), auf unterschiedliche Weise darauf hin, welche Elemente ausgewählt sind.</span><span class="sxs-lookup"><span data-stu-id="ec515-222">ListView and GridView indicate selected items in different ways depending on the control and the [SelectionMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.selectionmode.aspx).</span></span> <span data-ttu-id="ec515-223">Weitere Informationen zur Auswahl der Listenansicht finden Sie unter [ListView und GridView](listview-and-gridview.md).</span><span class="sxs-lookup"><span data-stu-id="ec515-223">For more info about list view selection, see [ListView and GridView](listview-and-gridview.md).</span></span> 

<span data-ttu-id="ec515-224">Wenn **SelectionMode** auf **Multiple** festgelegt ist, wird in der Steuerelementvorlage für das Element ein Kontrollkästchen zur Auswahl angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ec515-224">When **SelectionMode** is set to **Multiple**, a selection check box is shown as part of the item's control template.</span></span> <span data-ttu-id="ec515-225">Sie können im Mehrfachauswahlmodus das Kontrollkästchen zur Auswahl über die [SelectionCheckMarkVisualEnabled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.listviewitempresenter.selectioncheckmarkvisualenabled.aspx)-Eigenschaft deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="ec515-225">You can use the [SelectionCheckMarkVisualEnabled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.listviewitempresenter.selectioncheckmarkvisualenabled.aspx) property to turn off the selection check box in Multiple selection mode.</span></span> <span data-ttu-id="ec515-226">Diese Eigenschaft wird jedoch in den anderen Auswahlmodi ignoriert, daher können Sie das Kontrollkästchen im erweiterten oder im Einzelauswahlmodus nicht aktivieren.</span><span class="sxs-lookup"><span data-stu-id="ec515-226">However, this property is ignored in other selection modes, so you can't turn on the check box in Extended or Single selection mode.</span></span>

<span data-ttu-id="ec515-227">Sie können über die [CheckMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.listviewitempresenter.checkmode.aspx)-Eigenschaft festlegen, ob das Kontrollkästchen im Inlineformat oder im Overlayformat angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ec515-227">You can set the [CheckMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.listviewitempresenter.checkmode.aspx) property to specify whether the check box is shown using the inline style or overlay style.</span></span>

- <span data-ttu-id="ec515-228">**Inline**: Bei diesem Stil wird das Kontrollkästchen links neben dem Inhalt angezeigt. Der Hintergrund des Elementcontainers wird farbig hervorgehoben, um darauf hinzuweisen, dass es ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="ec515-228">**Inline**: This style shows the check box to the left of the content, and colors the background of the item container to indicate selection.</span></span> <span data-ttu-id="ec515-229">Dies ist der Standardstil für ListView.</span><span class="sxs-lookup"><span data-stu-id="ec515-229">This is the default style for ListView.</span></span>
- <span data-ttu-id="ec515-230">**Overlay**: Bei diesem Stil wird das Kontrollkästchen über dem Inhalt angezeigt. Es wird nur der Rahmen des Elementcontainers farbig hervorgehoben, um darauf hinzuweisen, dass es ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="ec515-230">**Overlay**: This style shows the check box on top of the content, and colors only the border of the item container to indicate selection.</span></span> <span data-ttu-id="ec515-231">Dies ist der Standardstil für GridView.</span><span class="sxs-lookup"><span data-stu-id="ec515-231">This is the default style for GridView.</span></span>

<span data-ttu-id="ec515-232">Die folgende Tabelle zeigt die visuellen Standardelemente, mit denen auf eine Auswahl hingewiesen wird.</span><span class="sxs-lookup"><span data-stu-id="ec515-232">This table shows the default visuals used to indicate selection.</span></span>

<span data-ttu-id="ec515-233">SelectionMode:&nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="ec515-233">SelectionMode:&nbsp;&nbsp;</span></span> | <span data-ttu-id="ec515-234">Einzelauswahl/erweitert</span><span class="sxs-lookup"><span data-stu-id="ec515-234">Single/Extended</span></span> | <span data-ttu-id="ec515-235">Mehrfachauswahl</span><span class="sxs-lookup"><span data-stu-id="ec515-235">Multiple</span></span>
---------------|-----------------|---------
<span data-ttu-id="ec515-236">Inline</span><span class="sxs-lookup"><span data-stu-id="ec515-236">Inline</span></span> | ![Einfache oder erweiterte Inlineauswahl](images/listview-single-selection.png) | ![Inline-Mehrfachauswahl](images/listview-multi-selection.png)
<span data-ttu-id="ec515-239">Überlagerung</span><span class="sxs-lookup"><span data-stu-id="ec515-239">Overlay</span></span> | ![Einfache oder erweiterte Auswahl von Überlagerungen](images/gridview-single-selection.png) | ![Mehrfachauswahl von Überlagerungen](images/gridview-multi-selection.png)

> [!NOTE]
> <span data-ttu-id="ec515-242">In diesem und den folgenden Beispielen werden einfache Zeichenfolgen-Datenelemente ohne Datenvorlagen angezeigt, um zu zeigen, wie sich die visuellen Elemente der Steuerelementvorlage auswirken.</span><span class="sxs-lookup"><span data-stu-id="ec515-242">In this and the following examples, simple string data items are shown without data templates to emphasize the visuals provided by the control template.</span></span>

<span data-ttu-id="ec515-243">Es gibt auch verschiedene Pinseleigenschaften, mit denen die Farben des Kontrollkästchens geändert werden können.</span><span class="sxs-lookup"><span data-stu-id="ec515-243">There are also several brush properties to change the colors of the check box.</span></span> <span data-ttu-id="ec515-244">Wir sehen uns nun diese und weitere Pinseleigenschaften an.</span><span class="sxs-lookup"><span data-stu-id="ec515-244">We'll look at these next along with other brush properties.</span></span>

#### <a name="brushes"></a><span data-ttu-id="ec515-245">Pinsel</span><span class="sxs-lookup"><span data-stu-id="ec515-245">Brushes</span></span> 

<span data-ttu-id="ec515-246">Viele Eigenschaften legen den Pinsel für die verschiedenen visuellen Zustände fest.</span><span class="sxs-lookup"><span data-stu-id="ec515-246">Many of the properties specify the brushes used for different visual states.</span></span> <span data-ttu-id="ec515-247">Möglicherweise möchten Sie diese anpassen, beispielsweise, um Ihre App mit Ihrem Branding zu versehen.</span><span class="sxs-lookup"><span data-stu-id="ec515-247">You might want to modify these to match the color of your brand.</span></span> 

<span data-ttu-id="ec515-248">Diese Tabelle enthält häufig verwendete visuelle Zustände und Auswahlzustände für ListViewItem, sowie die Pinsel zum Rendern der visuellen Elemente für die einzelnen Zustände.</span><span class="sxs-lookup"><span data-stu-id="ec515-248">This table shows the Common and Selection visual states for ListViewItem, and the brushes used to render the visuals for each state.</span></span> <span data-ttu-id="ec515-249">Die Bilder zeigen die Effekte der Pinsel auf die visuellen Inline- und Überlagerungsstile für die Auswahl.</span><span class="sxs-lookup"><span data-stu-id="ec515-249">The images show the effects of the brushes on both the inline and overlay selection visual styles.</span></span>

> [!NOTE]
> <span data-ttu-id="ec515-250">In dieser Tabelle sind die geänderten Farbwerte für die Pinsel hartcodierte benannte Farben, und die Farben werden ausgewählt, um deutlicher zu machen, an welchen Stellen in der Vorlage sie angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="ec515-250">In this table, the modified color values for the brushes are hardcoded named colors and the colors are selected to make it more apparent where they are applied in the template.</span></span> <span data-ttu-id="ec515-251">Diese sind nicht die Standardfarben für die visuellen Zustände.</span><span class="sxs-lookup"><span data-stu-id="ec515-251">These are not the default colors for the visual states.</span></span> <span data-ttu-id="ec515-252">Wenn Sie die Standardfarben in der App ändern, sollten Sie Pinselressourcen verwenden, um die Farbwerte entsprechend der Standardvorlage zu ändern.</span><span class="sxs-lookup"><span data-stu-id="ec515-252">If you modify the default colors in your app, you should use brush resources to modify the color values as done in the default template.</span></span>

<span data-ttu-id="ec515-253">Zustand/Pinselname</span><span class="sxs-lookup"><span data-stu-id="ec515-253">State/Brush name</span></span> | <span data-ttu-id="ec515-254">Inlineformat</span><span class="sxs-lookup"><span data-stu-id="ec515-254">Inline style</span></span> | <span data-ttu-id="ec515-255">Overlaystil</span><span class="sxs-lookup"><span data-stu-id="ec515-255">Overlay style</span></span>
------------|--------------|--------------
<b><span data-ttu-id="ec515-256">Normal</span><span class="sxs-lookup"><span data-stu-id="ec515-256">Normal</span></span></b><ul><li><b><span data-ttu-id="ec515-257">CheckBoxBrush="Red"</span><span class="sxs-lookup"><span data-stu-id="ec515-257">CheckBoxBrush="Red"</span></span></b></li></ul> | ![Inlineelementauswahl (normal)](images/listview-item-normal.png) | ![Overlayelementauswahl (normal)](images/gridview-item-normal.png)
<b><span data-ttu-id="ec515-260">PointerOver</span><span class="sxs-lookup"><span data-stu-id="ec515-260">PointerOver</span></span></b><ul><li><b><span data-ttu-id="ec515-261">PointerOverForeground="DarkOrange"</span><span class="sxs-lookup"><span data-stu-id="ec515-261">PointerOverForeground="DarkOrange"</span></span></b></li><li><b><span data-ttu-id="ec515-262">PointerOverBackground="MistyRose"</span><span class="sxs-lookup"><span data-stu-id="ec515-262">PointerOverBackground="MistyRose"</span></span></b></li><li><span data-ttu-id="ec515-263">CheckBoxBrush="Red"</span><span class="sxs-lookup"><span data-stu-id="ec515-263">CheckBoxBrush="Red"</span></span></li></ul> | ![Inline-Elementauswahlzeiger über](images/listview-item-pointerover.png) | ![Overlyelementauswahl (Hover)](images/gridview-item-pointerover.png)
<b><span data-ttu-id="ec515-266">Gedrückt</span><span class="sxs-lookup"><span data-stu-id="ec515-266">Pressed</span></span></b><ul><li><b><span data-ttu-id="ec515-267">PressedBackground="LightCyan"</span><span class="sxs-lookup"><span data-stu-id="ec515-267">PressedBackground="LightCyan"</span></span></b></li><li><span data-ttu-id="ec515-268">PointerOverForeground="DarkOrange"</span><span class="sxs-lookup"><span data-stu-id="ec515-268">PointerOverForeground="DarkOrange"</span></span></li><li><span data-ttu-id="ec515-269">CheckBoxBrush="Red"</span><span class="sxs-lookup"><span data-stu-id="ec515-269">CheckBoxBrush="Red"</span></span></li></ul> | ![Inlineelementauswahl (gedrückt)](images/listview-item-pressed.png) | ![Overlayelementauswahl (gedrückt)](images/gridview-item-pressed.png)
<b><span data-ttu-id="ec515-272">Ausgewählt</span><span class="sxs-lookup"><span data-stu-id="ec515-272">Selected</span></span></b><ul><li><b><span data-ttu-id="ec515-273">SelectedForeground="Navy"</span><span class="sxs-lookup"><span data-stu-id="ec515-273">SelectedForeground="Navy"</span></span></b></li><li><b><span data-ttu-id="ec515-274">SelectedBackground="Khaki"</span><span class="sxs-lookup"><span data-stu-id="ec515-274">SelectedBackground="Khaki"</span></span></b></li><li><b><span data-ttu-id="ec515-275">CheckBrush="Green"</span><span class="sxs-lookup"><span data-stu-id="ec515-275">CheckBrush="Green"</span></span></b></li><li><span data-ttu-id="ec515-276">CheckBoxBrush="Red" (nur Inline)</span><span class="sxs-lookup"><span data-stu-id="ec515-276">CheckBoxBrush="Red" (inline only)</span></span></li></ul> | ![Inlineelementauswahl aktiviert](images/listview-item-selected.png) | ![Overlayelementauswahl aktiviert](images/gridview-item-selected.png)
<b><span data-ttu-id="ec515-279">PointerOverSelected</span><span class="sxs-lookup"><span data-stu-id="ec515-279">PointerOverSelected</span></span></b><ul><li><b><span data-ttu-id="ec515-280">SelectedPointerOverBackground="Lavender"</span><span class="sxs-lookup"><span data-stu-id="ec515-280">SelectedPointerOverBackground="Lavender"</span></span></b></li><li><span data-ttu-id="ec515-281">SelectedForeground="Navy"</span><span class="sxs-lookup"><span data-stu-id="ec515-281">SelectedForeground="Navy"</span></span></li><li><span data-ttu-id="ec515-282">SelectedBackground="Khaki" (nur Overlay)</span><span class="sxs-lookup"><span data-stu-id="ec515-282">SelectedBackground="Khaki" (overlay only)</span></span></li><li><span data-ttu-id="ec515-283">CheckBrush="Green"</span><span class="sxs-lookup"><span data-stu-id="ec515-283">CheckBrush="Green"</span></span></li><li><span data-ttu-id="ec515-284">CheckBoxBrush="Red" (nur Inline)</span><span class="sxs-lookup"><span data-stu-id="ec515-284">CheckBoxBrush="Red" (inline only)</span></span></li></ul> | ![Inline-Element Auswahlzeiger über ausgewählt](images/listview-item-pointeroverselected.png) | ![Overlayelementauswahl (Hover)](images/gridview-item-pointeroverselected.png)
<b><span data-ttu-id="ec515-287">PressedSelected</span><span class="sxs-lookup"><span data-stu-id="ec515-287">PressedSelected</span></span></b><ul><li><b><span data-ttu-id="ec515-288">SelectedPressedBackground="MediumTurquoise"</span><span class="sxs-lookup"><span data-stu-id="ec515-288">SelectedPressedBackground="MediumTurquoise"</span></span></b></li></li><li><span data-ttu-id="ec515-289">SelectedForeground="Navy"</span><span class="sxs-lookup"><span data-stu-id="ec515-289">SelectedForeground="Navy"</span></span></li><li><span data-ttu-id="ec515-290">SelectedBackground="Khaki" (nur Overlay)</span><span class="sxs-lookup"><span data-stu-id="ec515-290">SelectedBackground="Khaki" (overlay only)</span></span></li><li><span data-ttu-id="ec515-291">CheckBrush="Green"</span><span class="sxs-lookup"><span data-stu-id="ec515-291">CheckBrush="Green"</span></span></li><li><span data-ttu-id="ec515-292">CheckBoxBrush="Red" (nur Inline)</span><span class="sxs-lookup"><span data-stu-id="ec515-292">CheckBoxBrush="Red" (inline only)</span></span></li></ul> | ![Inlineelementauswahl (markiert)](images/listview-item-pressedselected.png) | ![Overlayelementauswahl (markiert)](images/gridview-item-pressedselected.png)
<b><span data-ttu-id="ec515-295">Im Vordergrund</span><span class="sxs-lookup"><span data-stu-id="ec515-295">Focused</span></span></b><ul><li><b><span data-ttu-id="ec515-296">FocusBorderBrush="Crimson"</span><span class="sxs-lookup"><span data-stu-id="ec515-296">FocusBorderBrush="Crimson"</span></span></b></li><li><b><span data-ttu-id="ec515-297">FocusSecondaryBorderBrush="Gold"</span><span class="sxs-lookup"><span data-stu-id="ec515-297">FocusSecondaryBorderBrush="Gold"</span></span></b></li><li><span data-ttu-id="ec515-298">CheckBoxBrush="Red"</span><span class="sxs-lookup"><span data-stu-id="ec515-298">CheckBoxBrush="Red"</span></span></li></ul> | ![Inlineelementauswahl (Vordergrund)](images/listview-item-focused.png) | ![Overlayelementauswahl (Vordergrund)](images/gridview-item-focused.png)

<span data-ttu-id="ec515-301">ListViewItemPresenter hat noch andere Pinseleigenschaften für Datenplatzhalter und Drag&Drop-Zustände.</span><span class="sxs-lookup"><span data-stu-id="ec515-301">ListViewItemPresenter has other brush properties for data placeholders and drag states.</span></span> <span data-ttu-id="ec515-302">Wenn Sie in der Listenansicht inkrementelles Laden oder Drag&Drop verwenden, sollten Sie überlegen, ob Sie auch diese zusätzlichen Pinseleigenschaften ändern müssen.</span><span class="sxs-lookup"><span data-stu-id="ec515-302">If you use incremental loading or drag and drop in your list view, you should consider whether you need to also modify these additional brush properties.</span></span> <span data-ttu-id="ec515-303">Informationen finden Sie in der ListViewItemPresenter-Klasse mit einer vollständigen Liste der Eigenschaften, die Sie ändern können.</span><span class="sxs-lookup"><span data-stu-id="ec515-303">See the ListViewItemPresenter class for the complete list of properties you can modify.</span></span> 

### <a name="expanded-xaml-item-templates"></a><span data-ttu-id="ec515-304">Erweiterte XAML-Elementvorlagen</span><span class="sxs-lookup"><span data-stu-id="ec515-304">Expanded XAML item templates</span></span>

<span data-ttu-id="ec515-305">Wenn Sie weitere Änderungen vornehmen müssen als es von den **ListViewItemPresenter** Eigenschaften erlaubt ist – Wenn Sie die Position des Kontrollkästchens ändern müssen z. B. - können Sie die *ListViewItemExpanded* oder *GridViewItemExpanded* Vorlagen verwenden.</span><span class="sxs-lookup"><span data-stu-id="ec515-305">If you need to make more modifications than what is allowed by the **ListViewItemPresenter** properties - if you need to change the position of the check box, for example - you can use the *ListViewItemExpanded* or *GridViewItemExpanded* templates.</span></span> <span data-ttu-id="ec515-306">Diese Vorlagen sind in den Standardstilen in „generic.xaml“ enthalten.</span><span class="sxs-lookup"><span data-stu-id="ec515-306">These templates are included with the default styles in generic.xaml.</span></span> <span data-ttu-id="ec515-307">Sie basieren auf dem standardmäßigen XAML-Konstruktionsschema für alle visuellen Elemente der einzelnen UIElements.</span><span class="sxs-lookup"><span data-stu-id="ec515-307">They follow the standard XAML pattern of building all the visuals from individual UIElements.</span></span>

<span data-ttu-id="ec515-308">Wie bereits erwähnt, hat die Anzahl von UIElements in einer Elementvorlage erhebliche Auswirkungen auf die Leistung der Listenansicht.</span><span class="sxs-lookup"><span data-stu-id="ec515-308">As mentioned previously, the number of UIElements in an item template has a significant impact on the performance of your list view.</span></span> <span data-ttu-id="ec515-309">Wenn Sie ListViewItemPresenter durch erweiterte XAML-Vorlagen ersetzen, erhöht sich die Anzahl der Elemente erheblich. Wenn in der Listenansicht eine große Anzahl von Elementen angezeigt wird oder die Leistung von Bedeutung ist, wird davon abgeraten.</span><span class="sxs-lookup"><span data-stu-id="ec515-309">Replacing ListViewItemPresenter with the expanded XAML templates greatly increases the element count, and is not recommended when your list view will show a large number of items or when performance is a concern.</span></span>

> [!NOTE]
> <span data-ttu-id="ec515-310">**ListViewItemPresenter** wird nur unterstützt, wenn das [ItemsPanel](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemspanel.aspx) der Listenansicht einem [ItemsWrapGrid](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemswrapgrid.aspx) oder einem [ItemsStackPanel](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemsstackpanel.aspx) entspricht.</span><span class="sxs-lookup"><span data-stu-id="ec515-310">**ListViewItemPresenter** is supported only when the list view’s [ItemsPanel](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemscontrol.itemspanel.aspx) is an [ItemsWrapGrid](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemswrapgrid.aspx) or [ItemsStackPanel](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemsstackpanel.aspx).</span></span> <span data-ttu-id="ec515-311">Wenn Sie das ItemsPanel ändern und [VariableSizedWrapGrid](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.variablesizedwrapgrid.aspx), [WrapGrid](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.wrapgrid.aspx) oder [StackPanel](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.stackpanel.aspx) verwenden, wechselt die Elementvorlage automatisch zur erweiterten XAML-Vorlage.</span><span class="sxs-lookup"><span data-stu-id="ec515-311">If you change the ItemsPanel to use [VariableSizedWrapGrid](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.variablesizedwrapgrid.aspx), [WrapGrid](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.wrapgrid.aspx), or [StackPanel](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.stackpanel.aspx), then the item template is automatically switched to the expanded XAML template.</span></span> <span data-ttu-id="ec515-312">Weitere Informationen finden Sie unter [Optimieren der ListView- und GridView-Benutzeroberfläche](https://msdn.microsoft.com/windows/uwp/debug-test-perf/optimize-gridview-and-listview).</span><span class="sxs-lookup"><span data-stu-id="ec515-312">For more info, see [ListView and GridView UI optimization](https://msdn.microsoft.com/windows/uwp/debug-test-perf/optimize-gridview-and-listview).</span></span>

<span data-ttu-id="ec515-313">Um eine erweiterte XAML-Vorlage anzupassen, müssen Sie eine Kopie von Ihrer App erstellen und die **ItemContainerStyle**-Eigenschaft auf diese Kopie festlegen.</span><span class="sxs-lookup"><span data-stu-id="ec515-313">To customize an expanded XAML template, you need to make a copy of it in your app, and set the **ItemContainerStyle** property to your copy.</span></span>

**<span data-ttu-id="ec515-314">So kopieren Sie die erweiterte Vorlage</span><span class="sxs-lookup"><span data-stu-id="ec515-314">To copy the expanded template</span></span>**
1. <span data-ttu-id="ec515-315">Legen Sie die ItemContainerStyle-Eigenschaft für Ihren ListView oder GridView wie hier dargestellt fest.</span><span class="sxs-lookup"><span data-stu-id="ec515-315">Set the ItemContainerStyle property as shown here for your ListView or GridView.</span></span>
    ```xaml
    <ListView ItemContainerStyle="{StaticResource ListViewItemExpanded}"/>
    <GridView ItemContainerStyle="{StaticResource GridViewItemExpanded}"/>
    ```
2. <span data-ttu-id="ec515-316">Erweitern Sie im Eigenschaftenbereich von Visual Studio den Abschnitt „Verschiedenes“, und suchen Sie die „ItemContainerStyle“-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="ec515-316">In the Visual Studio Properties pane, expand the Miscellaneous section and find the ItemContainerStyle property.</span></span> <span data-ttu-id="ec515-317">(Stellen Sie sicher, dass ListView oder GridView ausgewählt ist.)</span><span class="sxs-lookup"><span data-stu-id="ec515-317">(Make sure the ListView or GridView is selected.)</span></span>
3. <span data-ttu-id="ec515-318">Klicken Sie auf den Eigenschaftenmarker für die ItemContainerStyle-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="ec515-318">Click the property marker for the ItemContainerStyle property.</span></span> <span data-ttu-id="ec515-319">(Das ist das kleine Feld neben dem Textfeld.</span><span class="sxs-lookup"><span data-stu-id="ec515-319">(It’s the small box next to the TextBox.</span></span> <span data-ttu-id="ec515-320">Es wird grün angezeigt, um darauf hinzuweisen, dass eine StaticResource festgelegt ist.) Das Eigenschaftenmenü wird geöffnet.</span><span class="sxs-lookup"><span data-stu-id="ec515-320">It’s coloreed green to show that it’s set to a StaticResource.) The property menu opens.</span></span>
4. <span data-ttu-id="ec515-321">Wählen Sie im Eigenschaftsmenü die Option **In neue Ressource konvertieren** aus.</span><span class="sxs-lookup"><span data-stu-id="ec515-321">In the property menu, click **Convert to New Resource**.</span></span> 
    
    ![Visual Studio-Eigenschaftenmenü](images/listview-convert-resource-vs.png)
5. <span data-ttu-id="ec515-323">Geben Sie im Dialogfeld „Stilressource erstellen“ einen Namen für die Ressource ein, und klicken Sie dann auf „OK“.</span><span class="sxs-lookup"><span data-stu-id="ec515-323">In the Create Style Resource dialog, enter a name for the resource and click OK.</span></span>

<span data-ttu-id="ec515-324">Eine Kopie der erweiterten Vorlage von generic.xaml wird in Ihrer App erstellt, die Sie bei Bedarf ändern können.</span><span class="sxs-lookup"><span data-stu-id="ec515-324">A copy of the expanded template from generic.xaml is created in your app, which you can modify as needed.</span></span>


## <a name="related-articles"></a><span data-ttu-id="ec515-325">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="ec515-325">Related articles</span></span>

- [<span data-ttu-id="ec515-326">Listen</span><span class="sxs-lookup"><span data-stu-id="ec515-326">Lists</span></span>](lists.md)
- [<span data-ttu-id="ec515-327">ListView und GridView</span><span class="sxs-lookup"><span data-stu-id="ec515-327">ListView and GridView</span></span>](listview-and-gridview.md)

