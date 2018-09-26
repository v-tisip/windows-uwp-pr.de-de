---
author: Jwmsft
Description: A text entry box that provides suggestions as the user types.
title: Kombinationsfeld (Dropdown-Liste)
label: Combo box
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
pm-contact: stmoy
design-contact: ''
doc-status: Draft
ms.localizationpriority: medium
ms.openlocfilehash: 4f7592f584227d9b3a93a0ef4cea3ce53cd203ea
ms.sourcegitcommit: e4f3e1b2d08a02b9920e78e802234e5b674e7223
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2018
ms.locfileid: "4205018"
---
# <a name="combo-box"></a><span data-ttu-id="159f9-103">Kombinationsfeld</span><span class="sxs-lookup"><span data-stu-id="159f9-103">Combo box</span></span>

> [!IMPORTANT]
> <span data-ttu-id="159f9-104">In diesem Artikel werden Funktionen beschrieben, die noch nicht veröffentlicht wurden und vor der kommerziellen Freigabe evtl. geändert werden.</span><span class="sxs-lookup"><span data-stu-id="159f9-104">This article describes functionality that hasn’t been released yet and may be substantially modified before it's commercially released.</span></span> <span data-ttu-id="159f9-105">Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.</span><span class="sxs-lookup"><span data-stu-id="159f9-105">Microsoft makes no warranties, express or implied, with respect to the information provided here.</span></span>

<span data-ttu-id="159f9-106">Verwenden Sie ein Kombinationsfeld (auch bekannt als eine Dropdown-Liste), um eine Liste von Elementen, vorhanden sind, die ein Benutzer eine Auswahl treffen kann.</span><span class="sxs-lookup"><span data-stu-id="159f9-106">Use a combo box (also known as a drop-down list) to present a list of items that a user can select from.</span></span> <span data-ttu-id="159f9-107">Ein Kombinationsfeld wird in einem kompakten Zustand gestartet und erweitert, um eine Liste mit auswählbaren Elementen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="159f9-107">A combo box starts in a compact state and expands to show a list of selectable items.</span></span>

<span data-ttu-id="159f9-108">Wenn das Kombinationsfeld geschlossen wird, es zeigt die aktuelle Auswahl oder ist leer, wenn kein Element ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="159f9-108">When the combo box is closed, it either displays the current selection or is empty if there is no selected item.</span></span> <span data-ttu-id="159f9-109">Wenn der Benutzer das Kombinationsfeld erweitert, zeigt es die Liste mit auswählbaren Elementen.</span><span class="sxs-lookup"><span data-stu-id="159f9-109">When the user expands the combo box, it displays the list of selectable items.</span></span>

> <span data-ttu-id="159f9-110">**Wichtige APIs**: [ComboBox-Klasse](/uwp/api/Windows.UI.Xaml.Controls.ComboBox), [IsEditable-Eigenschaft](/uwp/api/windows.ui.xaml.controls.combobox.iseditable), [Text-Eigenschaft](/uwp/api/Windows.UI.Xaml.Controls.ComboBox), [TextSubmitted-Ereignis](/uwp/api/Windows.UI.Xaml.Controls.ComboBox)</span><span class="sxs-lookup"><span data-stu-id="159f9-110">**Important APIs**: [ComboBox class](/uwp/api/Windows.UI.Xaml.Controls.ComboBox), [IsEditable property](/uwp/api/windows.ui.xaml.controls.combobox.iseditable), [Text property](/uwp/api/Windows.UI.Xaml.Controls.ComboBox), [TextSubmitted event](/uwp/api/Windows.UI.Xaml.Controls.ComboBox)</span></span>

<span data-ttu-id="159f9-111">Ein Kombinationsfeld im kompakten Zustand mit einer Kopfzeile.</span><span class="sxs-lookup"><span data-stu-id="159f9-111">A combo box in its compact state with a header.</span></span>

![Beispiel für eine Dropdownliste im kompakten Zustand](images/combo_box_collapsed.png)

## <a name="is-this-the-right-control"></a><span data-ttu-id="159f9-113">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="159f9-113">Is this the right control?</span></span>

- <span data-ttu-id="159f9-114">Mit einer Dropdownliste können Benutzer einen einzelnen Wert aus einer Reihe von Elementen auswählen, die mit einzelnen Textzeilen angemessen dargestellt werden können.</span><span class="sxs-lookup"><span data-stu-id="159f9-114">Use a drop-down list to let users select a single value from a set of items that can be adequately represented with single lines of text.</span></span>
- <span data-ttu-id="159f9-115">Verwenden Sie eine Liste oder eine Rasteransicht anstelle eines Kombinationsfelds, um Elemente anzuzeigen, die mehrere Textzeilen oder Bilder enthalten.</span><span class="sxs-lookup"><span data-stu-id="159f9-115">Use a list or grid view instead of a combo box to display items that contain multiple lines of text or images.</span></span>
- <span data-ttu-id="159f9-116">Wenn weniger als fünf Elemente vorhanden sind, können Sie stattdessen die Verwendung von [Optionsfeldern](radio-button.md) (wenn nur ein Element ausgewählt werden kann) oder [Kontrollkästchen](checkbox.md) (wenn mehrere Elemente ausgewählt werden können) in Betracht ziehen.</span><span class="sxs-lookup"><span data-stu-id="159f9-116">When there are fewer than five items, consider using [radio buttons](radio-button.md) (if only one item can be selected) or [check boxes](checkbox.md) (if multiple items can be selected).</span></span>
- <span data-ttu-id="159f9-117">Verwenden Sie ein Kombinationsfeld, wenn die Auswahlelemente für den Fluss der App weniger wichtig sind.</span><span class="sxs-lookup"><span data-stu-id="159f9-117">Use a combo box when the selection items are of secondary importance in the flow of your app.</span></span> <span data-ttu-id="159f9-118">Wenn für die Mehrzahl der Benutzer in der Mehrzahl der Situationen die Standardoption empfohlen wird, kann die Anzeige aller Elemente in einer Listenansicht mehr Aufmerksamkeit auf die Optionen ziehen als nötig.</span><span class="sxs-lookup"><span data-stu-id="159f9-118">If the default option is recommended for most users in most situations, showing all the items by using a list view might draw more attention to the options than necessary.</span></span> <span data-ttu-id="159f9-119">Sie können Platz sparen und Ablenkungen reduzieren, indem Sie ein Kombinationsfeld verwenden.</span><span class="sxs-lookup"><span data-stu-id="159f9-119">You can save space and minimize distraction by using a combo box.</span></span>

## <a name="examples"></a><span data-ttu-id="159f9-120">Beispiele</span><span class="sxs-lookup"><span data-stu-id="159f9-120">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="159f9-121">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="159f9-121">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="159f9-122">Wenn Sie die <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> -app installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/ComboBox">die app zu öffnen und finden Sie unter dem Kombinationsfeld in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="159f9-122">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/ComboBox">open the app and see the ComboBox in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="159f9-123">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="159f9-123">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="159f9-124">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="159f9-124">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

<span data-ttu-id="159f9-125">Ein Kombinationsfeld im kompakten Zustand kann eine Kopfzeile anzeigen.</span><span class="sxs-lookup"><span data-stu-id="159f9-125">A combo box in its compact state can show a header.</span></span>

![Beispiel für eine Dropdownliste im kompakten Zustand](images/combo_box_collapsed.png)

<span data-ttu-id="159f9-127">Obwohl Kombinationsfelder erweitert werden, um längere Zeichenfolgen zu unterstützen, sollten Sie extrem lange Zeichenfolgen vermeiden, die nur schwer lesbar sind.</span><span class="sxs-lookup"><span data-stu-id="159f9-127">Although combo boxes expand to support longer string lengths, avoid excessively long strings that are difficult to read.</span></span>

![Beispiel einer Dropdownliste mit einer langen Textzeichenfolge](images/combo_box_listitemstate.png)

<span data-ttu-id="159f9-129">Wenn die Liste in einem Kombinationsfeld lang genug ist, wird eine Bildlaufleiste angezeigt.</span><span class="sxs-lookup"><span data-stu-id="159f9-129">If the collection in a combo box is long enough, a scroll bar will appear to accommodate it.</span></span> <span data-ttu-id="159f9-130">Gruppieren Sie die Elemente in der Liste logisch.</span><span class="sxs-lookup"><span data-stu-id="159f9-130">Group items logically in the list.</span></span>

![Beispiel einer Bildlaufleiste in einer Dropdownliste](images/combo_box_scroll.png)

## <a name="create-a-combo-box"></a><span data-ttu-id="159f9-132">Erstellen Sie ein Kombinationsfeld</span><span class="sxs-lookup"><span data-stu-id="159f9-132">Create a combo box</span></span>

<span data-ttu-id="159f9-133">Durch Hinzufügen von Objekten direkt zur Sammlung [Items](/uwp/api/windows.ui.xaml.controls.itemscontrol.items) oder binden die [ItemsSource](/uwp/api/windows.ui.xaml.controls.itemscontrol.itemssource) -Eigenschaft an eine Datenquelle zu füllen Sie das Kombinationsfeld.</span><span class="sxs-lookup"><span data-stu-id="159f9-133">You populate the combo box by adding objects directly to the [Items](/uwp/api/windows.ui.xaml.controls.itemscontrol.items) collection or by binding the [ItemsSource](/uwp/api/windows.ui.xaml.controls.itemscontrol.itemssource) property to a data source.</span></span> <span data-ttu-id="159f9-134">Elemente, die dem Kombinationsfeld hinzugefügt werden in [ComboBoxItem](/uwp/api/windows.ui.xaml.controls.comboboxitem) Container eingeschlossen.</span><span class="sxs-lookup"><span data-stu-id="159f9-134">Items added to the ComboBox are wrapped in [ComboBoxItem](/uwp/api/windows.ui.xaml.controls.comboboxitem) containers.</span></span>

<span data-ttu-id="159f9-135">Hier ist ein einfaches Kombinationsfeld mit Elementen in XAML hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="159f9-135">Here's a simple combo box with items added in XAML.</span></span>

```xaml
<ComboBox Header="Colors" PlaceholderText="Pick a color" Width="200">
    <x:String>Blue<x:String>
    <x:String>Green<x:String>
    <x:String>Red<x:String>
    <x:String>Yellow<x:String>
</ComboBox>
```

<span data-ttu-id="159f9-136">Im folgende Beispiel wird veranschaulicht, binden ein Kombinationsfeld an eine Sammlung von FontFamily-Objekten.</span><span class="sxs-lookup"><span data-stu-id="159f9-136">The following example demonstrates binding a combo box to a collection of FontFamily objects.</span></span>

```xaml
<ComboBox x:Name="FontsCombo" Header="Fonts" Height="44" Width="296"
          ItemsSource="{x:Bind fonts}" DisplayMemberPath="Source"/>
```

```csharp
ObservableCollection<FontFamily> fonts = new ObservableCollection<FontFamily>();

public MainPage()
{
    this.InitializeComponent();
    fonts.Add(new FontFamily("Arial"));
    fonts.Add(new FontFamily("Courier New"));
    fonts.Add(new FontFamily("Times New Roman"));
}
```

### <a name="item-selection"></a><span data-ttu-id="159f9-137">Elementauswahl</span><span class="sxs-lookup"><span data-stu-id="159f9-137">Item selection</span></span>

<span data-ttu-id="159f9-138">Wie ListView und GridView wird ComboBox- [Selektor](/uwp/api/windows.ui.xaml.controls.primitives.selector), abgeleitet, sodass die Auswahl des Benutzers erhalten Sie in der gleichen Standardmethode können.</span><span class="sxs-lookup"><span data-stu-id="159f9-138">Like ListView and GridView, ComboBox is derived from [Selector](/uwp/api/windows.ui.xaml.controls.primitives.selector), so you can get the user’s selection in the same standard way.</span></span>

<span data-ttu-id="159f9-139">Sie können abrufen oder des Kombinationsfelds ausgewählte Element durch die Verwendung der [SelectedItem](/uwp/api/windows.ui.xaml.controls.primitives.selector.selecteditem) -Eigenschaft, und Abrufen oder festlegen den Index des ausgewählten Elements mithilfe der [SelectedIndex](/uwp/api/windows.ui.xaml.controls.primitives.selector.selectedindex) -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="159f9-139">You can get or set the combo box's selected item by using the [SelectedItem](/uwp/api/windows.ui.xaml.controls.primitives.selector.selecteditem) property, and get or set the index of the selected item by using the [SelectedIndex](/uwp/api/windows.ui.xaml.controls.primitives.selector.selectedindex) property.</span></span>

<span data-ttu-id="159f9-140">Um den Wert einer bestimmten Eigenschaft auf das ausgewählte Datenelement zu erhalten, können Sie die [SelectedValue](/uwp/api/windows.ui.xaml.controls.primitives.selector.selectedvalue) -Eigenschaft verwenden.</span><span class="sxs-lookup"><span data-stu-id="159f9-140">To get the value of a particular property on the selected data item, you can use the [SelectedValue](/uwp/api/windows.ui.xaml.controls.primitives.selector.selectedvalue) property.</span></span> <span data-ttu-id="159f9-141">In diesem Fall legen Sie die [SelectedValuePath](/uwp/api/windows.ui.xaml.controls.primitives.selector.selectedvaluepath) an, welche Eigenschaft für das ausgewählte Element auf den Wert abgerufen.</span><span class="sxs-lookup"><span data-stu-id="159f9-141">In this case, set the [SelectedValuePath](/uwp/api/windows.ui.xaml.controls.primitives.selector.selectedvaluepath) to specify which property on the selected item to get the value from.</span></span>

> [!TIP]
> <span data-ttu-id="159f9-142">Wenn Sie SelectedItem oder SelectedIndex an, dass die Standardeinstellung festlegen, wird eine Ausnahmebedingung ausgelöst, wenn die Eigenschaft festgelegt ist, bevor die Kombinationsfeld Feld Items-Sammlung gefüllt wird.</span><span class="sxs-lookup"><span data-stu-id="159f9-142">If you set SelectedItem or SelectedIndex to indicate the default selection, an exception occurs if the property is set before the combo box Items collection is populated.</span></span> <span data-ttu-id="159f9-143">Es sei denn, Sie Ihre Elemente in XAML definieren, empfiehlt es sich das Kombinationsfeld Feld Loaded-Ereignis behandeln, und legen Sie SelectedItem oder SelectedIndex im Ereignishandler Loaded-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="159f9-143">Unless you define your Items in XAML, it's best to handle the combo box Loaded event, and set SelectedItem or SelectedIndex in the Loaded event handler.</span></span>

<span data-ttu-id="159f9-144">Sie können diese Eigenschaften in XAML binden oder behandeln Sie das [SelectionChanged](/uwp/api/windows.ui.xaml.controls.primitives.selector.selectionchanged) -Ereignis zum Reagieren auf Änderungen der Auswahl.</span><span class="sxs-lookup"><span data-stu-id="159f9-144">You can bind to these properties in XAML, or handle the [SelectionChanged](/uwp/api/windows.ui.xaml.controls.primitives.selector.selectionchanged) event to respond to selection changes.</span></span>

<span data-ttu-id="159f9-145">Im Ereignishandlercode Sie das ausgewählte Element aus der Eigenschaft [SelectionChangedEventArgs.AddedItems](/uwp/api/windows.ui.xaml.controls.selectionchangedeventargs.addeditems) erhalten.</span><span class="sxs-lookup"><span data-stu-id="159f9-145">In the event handler code, you can get the selected item from the [SelectionChangedEventArgs.AddedItems](/uwp/api/windows.ui.xaml.controls.selectionchangedeventargs.addeditems) property.</span></span> <span data-ttu-id="159f9-146">Sie können das zuvor ausgewählte Element (sofern vorhanden) aus der Eigenschaft [SelectionChangedEventArgs.RemovedItems](/uwp/api/windows.ui.xaml.controls.selectionchangedeventargs.removeditems) abrufen.</span><span class="sxs-lookup"><span data-stu-id="159f9-146">You can get the previously selected item (if any) from the [SelectionChangedEventArgs.RemovedItems](/uwp/api/windows.ui.xaml.controls.selectionchangedeventargs.removeditems) property.</span></span> <span data-ttu-id="159f9-147">Die Addeditems- und RemovedItems-Sammlungen jedes enthalten nur 1 Element, da das Kombinationsfeld Auswahl mehrerer nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="159f9-147">The AddedItems and RemovedItems collections each contain only 1 item because combo box does not support multiple selection.</span></span>

<span data-ttu-id="159f9-148">In diesem Beispiel wird veranschaulicht, wie das SelectionChanged-Ereignis behandelt, und wie Sie auf das ausgewählte Element binden.</span><span class="sxs-lookup"><span data-stu-id="159f9-148">This example shows how to handle the SelectionChanged event, and also how to bind to the selected item.</span></span>

```xaml
<StackPanel>
    <ComboBox x:Name="colorComboBox" Width="200"
              Header="Colors" PlaceholderText="Pick a color"
              SelectionChanged="ColorComboBox_SelectionChanged">
        <x:String>Blue</x:String>
        <x:String>Green</x:String>
        <x:String>Red</x:String>
        <x:String>Yellow</x:String>
    </ComboBox>

    <Rectangle x:Name="colorRectangle" Height="30" Width="100"
               Margin="0,8,0,0" HorizontalAlignment="Left"/>

    <TextBlock Text="{x:Bind colorComboBox.SelectedIndex, Mode=OneWay}"/>
    <TextBlock Text="{x:Bind colorComboBox.SelectedItem, Mode=OneWay}"/>
</StackPanel>
```

```csharp
private void ColorComboBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
{
    // Add "using Windows.UI;" for Color and Colors.
    string colorName = e.AddedItems[0].ToString();
    Color color;
    switch (colorName)
    {
        case "Yellow":
            color = Colors.Yellow;
            break;
        case "Green":
            color = Colors.Green;
            break;
        case "Blue":
            color = Colors.Blue;
            break;
        case "Red":
            color = Colors.Red;
            break;
    }
    colorRectangle.Fill = new SolidColorBrush(color);
}
```

#### <a name="selectionchanged-and-keyboard-navigation"></a><span data-ttu-id="159f9-149">SelectionChanged und Tastatur navigation</span><span class="sxs-lookup"><span data-stu-id="159f9-149">SelectionChanged and keyboard navigation</span></span>

<span data-ttu-id="159f9-150">Standardmäßig tritt ein, das SelectionChanged-Ereignis, wenn ein Benutzer klickt, tippt oder drückt, geben Sie auf ein Element in der Liste, um ihre Auswahl zu übernehmen, und das Kombinationsfeld wird geschlossen.</span><span class="sxs-lookup"><span data-stu-id="159f9-150">By default, the SelectionChanged event occurs when a user clicks, taps, or presses Enter on an item in the list to commit their selection, and the combo box closes.</span></span> <span data-ttu-id="159f9-151">Auswahl ändern nicht, wenn der Benutzer das Öffnen Kombinationsfeld mit den Pfeiltasten der Tastatur navigiert.</span><span class="sxs-lookup"><span data-stu-id="159f9-151">Selection doesn't change when the user navigates the open combo box list with the keyboard arrow keys.</span></span>

<span data-ttu-id="159f9-152">Um ein Kombinationsfeld, das "live aktualisiert" während der Benutzer die Liste öffnen mit den Pfeiltasten (z. B. eine Schriftart Auswahl Dropdown-Liste) navigiert, [müssen Sie SelectionChangedTrigger](/uwp/api/windows.ui.xaml.controls.combobox.selectionchangedtrigger) auf [immer](/uwp/api/windows.ui.xaml.controls.comboboxselectionchangedtrigger)festgelegt.</span><span class="sxs-lookup"><span data-stu-id="159f9-152">To make a combo box that "live updates" while the user is navigating the open list with the arrow keys (like a Font selection drop-down), set [SelectionChangedTrigger](/uwp/api/windows.ui.xaml.controls.combobox.selectionchangedtrigger) to [Always](/uwp/api/windows.ui.xaml.controls.comboboxselectionchangedtrigger).</span></span> <span data-ttu-id="159f9-153">Dadurch wird das SelectionChanged-Ereignis auftreten, wenn der Fokus auf ein anderes Element in der Liste öffnen geändert wird.</span><span class="sxs-lookup"><span data-stu-id="159f9-153">This causes the SelectionChanged event to occur when focus changes to another item in the open list.</span></span>

#### <a name="selected-item-behavior-change"></a><span data-ttu-id="159f9-154">Änderung des ausgewählten Elements Verhaltens</span><span class="sxs-lookup"><span data-stu-id="159f9-154">Selected item behavior change</span></span>

<span data-ttu-id="159f9-155">In RS5 (Windows SDK-Version 10.0.NNNNN.0 (Windows 10, Version jjmm), das Verhalten der ausgewählten Elemente wird aktualisiert, um bearbeitbaren Kombinationsfelder unterstützen.</span><span class="sxs-lookup"><span data-stu-id="159f9-155">In RS5 (Windows SDK version 10.0.NNNNN.0 (Windows 10, version YYMM), the behavior of selected items is updated to support editable combo boxes.</span></span>

<span data-ttu-id="159f9-156">Vor dem RS5, den Wert der SelectedItem-Eigenschaft (und daher SelectedValue und SelectedIndex) wurde in das Kombinationsfeld Items-Sammlung erforderlich.</span><span class="sxs-lookup"><span data-stu-id="159f9-156">Prior to RS5, the value of the SelectedItem property (and therefore, SelectedValue and SelectedIndex) was required to be in the combo box's Items collection.</span></span> <span data-ttu-id="159f9-157">Im vorherigen Beispiel, Einstellung `colorComboBox.SelectedItem = "Pink"` ergibt:</span><span class="sxs-lookup"><span data-stu-id="159f9-157">Using the previous example, setting `colorComboBox.SelectedItem = "Pink"` results in:</span></span>

- <span data-ttu-id="159f9-158">SelectedItem = Null</span><span class="sxs-lookup"><span data-stu-id="159f9-158">SelectedItem = null</span></span>
- <span data-ttu-id="159f9-159">SelectedValue = Null</span><span class="sxs-lookup"><span data-stu-id="159f9-159">SelectedValue = null</span></span>
- <span data-ttu-id="159f9-160">SelectedIndex =-1</span><span class="sxs-lookup"><span data-stu-id="159f9-160">SelectedIndex = -1</span></span>

<span data-ttu-id="159f9-161">In RS5 und höher der Wert der SelectedItem-Eigenschaft (und daher SelectedValue und SelectedIndex) ist nicht erforderlich, in dem Kombinationsfeld Items-Sammlung.</span><span class="sxs-lookup"><span data-stu-id="159f9-161">In RS5 and later, the value of the SelectedItem property (and therefore, SelectedValue and SelectedIndex) is not required to be in the combo box's Items collection.</span></span> <span data-ttu-id="159f9-162">Im vorherigen Beispiel, Einstellung `colorComboBox.SelectedItem = "Pink"` ergibt:</span><span class="sxs-lookup"><span data-stu-id="159f9-162">Using the previous example, setting `colorComboBox.SelectedItem = "Pink"` results in:</span></span>

- <span data-ttu-id="159f9-163">SelectedItem = rosa</span><span class="sxs-lookup"><span data-stu-id="159f9-163">SelectedItem = Pink</span></span>
- <span data-ttu-id="159f9-164">SelectedValue = rosa</span><span class="sxs-lookup"><span data-stu-id="159f9-164">SelectedValue = Pink</span></span>
- <span data-ttu-id="159f9-165">SelectedIndex =-1</span><span class="sxs-lookup"><span data-stu-id="159f9-165">SelectedIndex = -1</span></span>

### <a name="text-search"></a><span data-ttu-id="159f9-166">Textsuche</span><span class="sxs-lookup"><span data-stu-id="159f9-166">Text Search</span></span>

<span data-ttu-id="159f9-167">Kombinationsfelder unterstützen automatisch die Suche in ihren Sammlungen.</span><span class="sxs-lookup"><span data-stu-id="159f9-167">Combo boxes automatically support search within their collections.</span></span> <span data-ttu-id="159f9-168">Wenn ein Benutzer über eine physische Tastatur Zeichen eingibt, während sich der Fokus auf einem geöffneten oder geschlossenen Kombinationsfeld befindet, werden Vorschläge angezeigt, die der vom Benutzer eingegebenen Zeichenfolge entsprechen.</span><span class="sxs-lookup"><span data-stu-id="159f9-168">As users type characters on a physical keyboard while focused on an open or closed combo box, candidates matching the user's string are brought into view.</span></span> <span data-ttu-id="159f9-169">Diese Funktionalität ist besonders bei der Navigation durch eine lange Liste nützlich.</span><span class="sxs-lookup"><span data-stu-id="159f9-169">This functionality is especially helpful when navigating a long list.</span></span> <span data-ttu-id="159f9-170">Beispielsweise können bei der Interaktion mit einer Dropdownliste mit einer Liste Zuständen Benutzer die "w" drücken, um "Washington" anzuzeigen und schnell auswählen zu.</span><span class="sxs-lookup"><span data-stu-id="159f9-170">For example, when interacting with a drop-down containing a list of states, users can press the "w" key to bring "Washington" into view for quick selection.</span></span> <span data-ttu-id="159f9-171">Textsuche ist nicht Groß-/Kleinschreibung berücksichtigt.</span><span class="sxs-lookup"><span data-stu-id="159f9-171">The text search is not case-sensitive.</span></span>

<span data-ttu-id="159f9-172">Sie können die [IsTextSearchEnabled](/uwp/api/windows.ui.xaml.controls.combobox.istextsearchenabled) -Eigenschaft auf **"false"** zum Deaktivieren dieser Funktion festlegen.</span><span class="sxs-lookup"><span data-stu-id="159f9-172">You can set the [IsTextSearchEnabled](/uwp/api/windows.ui.xaml.controls.combobox.istextsearchenabled) property to **false** to disable this functionality.</span></span>

## <a name="make-a-combo-box-editable"></a><span data-ttu-id="159f9-173">Stellen Sie ein Kombinationsfeld bearbeitet werden</span><span class="sxs-lookup"><span data-stu-id="159f9-173">Make a combo box editable</span></span>

> [!IMPORTANT]
> <span data-ttu-id="159f9-174">Dieses Feature erfordert die [neuesten Windows 10 Insider Preview-Build und SDK](https://insider.windows.com/for-developers/).</span><span class="sxs-lookup"><span data-stu-id="159f9-174">This feature requires the [latest Windows 10 Insider Preview build and SDK](https://insider.windows.com/for-developers/).</span></span>

<span data-ttu-id="159f9-175">Standardmäßig ein Kombinationsfeld ermöglicht es dem Benutzer aus einer vordefinierten Liste von Optionen auswählen.</span><span class="sxs-lookup"><span data-stu-id="159f9-175">By default, a combo box lets the user select from a pre-defined list of options.</span></span> <span data-ttu-id="159f9-176">Es gibt jedoch auch Fälle, in denen die Liste enthält nur eine Teilmenge der gültige Werte, und der Benutzer sollte in der Lage, andere Werte einzugeben, die nicht aufgelistet werden.</span><span class="sxs-lookup"><span data-stu-id="159f9-176">However, there are cases where the list contains only a subset of valid values, and the user should be able to enter other values that aren't listed.</span></span> <span data-ttu-id="159f9-177">Um dies zu unterstützen, können Sie das Kombinationsfeld bearbeitbar.</span><span class="sxs-lookup"><span data-stu-id="159f9-177">To support this, you can make the combo box editable.</span></span>

<span data-ttu-id="159f9-178">Um ein Kombinationsfeld bearbeitbar, die [IsEditable](/uwp/api/windows.ui.xaml.controls.combobox.iseditable) -Eigenschaft auf **"true"** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="159f9-178">To make a combo box editable, set the [IsEditable](/uwp/api/windows.ui.xaml.controls.combobox.iseditable) property to **true**.</span></span> <span data-ttu-id="159f9-179">Behandeln Sie dann das [TextSubmitted](/uwp/api/Windows.UI.Xaml.Controls.ComboBox) -Ereignis, das mit dem Wert, der vom Benutzer eingegebenen funktionieren.</span><span class="sxs-lookup"><span data-stu-id="159f9-179">Then, handle the [TextSubmitted](/uwp/api/Windows.UI.Xaml.Controls.ComboBox) event to work with the value entered by the user.</span></span>

<span data-ttu-id="159f9-180">Standardmäßig wird der SelectedItem-Wert aktualisiert, wenn der Benutzer benutzerdefinierten Text absendet.</span><span class="sxs-lookup"><span data-stu-id="159f9-180">By default, the SelectedItem value is updated when the user commits custom text.</span></span> <span data-ttu-id="159f9-181">Sie können dieses Verhalten überschreiben, indem **Handled** auf **"true"** in den Ereignisargumenten TextSubmitted.</span><span class="sxs-lookup"><span data-stu-id="159f9-181">You can override this behavior by setting **Handled** to **true** in the TextSubmitted event args.</span></span> <span data-ttu-id="159f9-182">Wenn das Ereignis als behandelt markiert ist, wird das Kombinationsfeld wird keine weiteren Maßnahmen nach dem Ereignis und bleibt in der Bearbeitung Zustand.</span><span class="sxs-lookup"><span data-stu-id="159f9-182">When the event is marked as handled, the combo box will take no further action after the event and will stay in the editing state.</span></span> <span data-ttu-id="159f9-183">SelectedItem wird nicht aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="159f9-183">SelectedItem will not be updated.</span></span>

<span data-ttu-id="159f9-184">Dieses Beispiel zeigt ein einfaches bearbeitbaren Kombinationsfeld.</span><span class="sxs-lookup"><span data-stu-id="159f9-184">This example shows a simple editable combo box.</span></span> <span data-ttu-id="159f9-185">Die Liste enthält einfache Zeichenfolgen, und einen beliebigen Wert, der vom Benutzer eingegebenen wird verwendet, wie Sie eingegeben wurden.</span><span class="sxs-lookup"><span data-stu-id="159f9-185">The list contains simple strings, and any value entered by the user is used as entered.</span></span>

<span data-ttu-id="159f9-186">Eine Auswahl "zuletzt verwendete Namen" ermöglicht Benutzern die Eingabe von benutzerdefinierter Zeichenfolgen.</span><span class="sxs-lookup"><span data-stu-id="159f9-186">A "recently used names" chooser lets the user enter custom strings.</span></span> <span data-ttu-id="159f9-187">Die "RecentlyUsedNames" Liste enthält einige Werte, denen der Benutzer auswählen kann, aber der Benutzer kann auch einen neuen, benutzerdefinierten Wert hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="159f9-187">The 'RecentlyUsedNames' list contains some values that the user can choose from, but the user can also add a new, custom value.</span></span> <span data-ttu-id="159f9-188">Die "CurrentName"-Eigenschaft darstellt, der derzeit eingegebene Name.</span><span class="sxs-lookup"><span data-stu-id="159f9-188">The 'CurrentName' property represents the currently entered name.</span></span>

```xaml
<ComboBox IsEditable="true"
          ItemsSource="{x:Bind RecentlyUsedNames}"
          SelectedItem="{x:Bind CurrentName, Mode=TwoWay}"/>
```

### <a name="text-submitted"></a><span data-ttu-id="159f9-189">Text übermittelt</span><span class="sxs-lookup"><span data-stu-id="159f9-189">Text submitted</span></span>

<span data-ttu-id="159f9-190">Sie können das Ereignis [TextSubmitted](/uwp/api/Windows.UI.Xaml.Controls.ComboBox) arbeiten mit dem Wert, der vom Benutzer eingegebenen behandeln.</span><span class="sxs-lookup"><span data-stu-id="159f9-190">You can handle the [TextSubmitted](/uwp/api/Windows.UI.Xaml.Controls.ComboBox) event to work with the value entered by the user.</span></span> <span data-ttu-id="159f9-191">Im Ereignis-Handler Sie in der Regel überprüft werden kann, dass der Wert, der vom Benutzer eingegebenen gültig ist, verwenden Sie den Wert in Ihrer app.</span><span class="sxs-lookup"><span data-stu-id="159f9-191">In the event handler, you will typically validate that the value entered by the user is valid, then use the value in your app.</span></span> <span data-ttu-id="159f9-192">Abhängig von der Situation können Sie auch den Wert des Kombinationsfelds Liste der Optionen für die zukünftige Verwendung hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="159f9-192">Depending on the situation, you might also add the value to the combo box’s list of options for future use.</span></span>

<span data-ttu-id="159f9-193">Das TextSubmitted-Ereignis tritt auf, wenn diese Bedingungen erfüllt sind:</span><span class="sxs-lookup"><span data-stu-id="159f9-193">The TextSubmitted event occurs when these conditions are met:</span></span>

- <span data-ttu-id="159f9-194">Die IsEditable-Eigenschaft ist **"true"**</span><span class="sxs-lookup"><span data-stu-id="159f9-194">The IsEditable property is **true**</span></span>
- <span data-ttu-id="159f9-195">Der Benutzer gibt Text, die nicht mit einen vorhandenen Eintrag in der Liste des Kombinationsfelds übereinstimmt</span><span class="sxs-lookup"><span data-stu-id="159f9-195">The user enters text that does not match an existing entry in the combo box list</span></span>
- <span data-ttu-id="159f9-196">Der Benutzer drückt EINGABETASTE oder aus dem Kombinationsfeld den Fokus.</span><span class="sxs-lookup"><span data-stu-id="159f9-196">The user presses Enter, or moves focus from the combo box.</span></span>

<span data-ttu-id="159f9-197">Das TextSubmitted-Ereignis tritt nicht auf, wenn der Benutzer Text eingibt, und klicken Sie dann nach oben oder unten durch die Liste navigiert.</span><span class="sxs-lookup"><span data-stu-id="159f9-197">The TextSubmitted event does not occur if the user enters text and then navigates up or down through the list.</span></span>

### <a name="sample---validate-input-and-use-locally"></a><span data-ttu-id="159f9-198">Beispiel - Eingabe überprüfen und lokal verwenden</span><span class="sxs-lookup"><span data-stu-id="159f9-198">Sample - Validate input and use locally</span></span>

<span data-ttu-id="159f9-199">In diesem Beispiel eine Schriftart Größe Auswahl enthält eine Reihe von Werten, die Schriftart Größe Typhierarchie entsprechen, aber der Benutzer möglicherweise Schriftgrößen, die nicht in der Liste eingeben.</span><span class="sxs-lookup"><span data-stu-id="159f9-199">In this examle, a font size chooser contains a set of values corresponding to the font size ramp, but the user may enter font sizes that are not in the list.</span></span>

<span data-ttu-id="159f9-200">Wenn der Benutzer einen Wert einfügt, die nicht in der Liste, die Schriftart Größe Updates, aber der Wert wird die Liste der Schriftgrößen nicht hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="159f9-200">When the user adds a value that's not in the list, the font size updates, but the value is not added to the list of font sizes.</span></span>

<span data-ttu-id="159f9-201">Ist der neu eingegebene Wert nicht gültig ist, wird Sie SelectedValue verwenden, um die Text-Eigenschaft auf das letzte Wiederherstellen bekannten guten Wert.</span><span class="sxs-lookup"><span data-stu-id="159f9-201">If the newly entered value is not valid, you use the SelectedValue to revert the Text property to the last known good value.</span></span>

```xaml
<ComboBox x:Name="fontSizeComboBox"
          IsEditable="true"
          ItemsSource="{x:Bind ListOfFontSizes}"
          TextSubmitted="FontSizeComboBox_TextSubmitted"/>
```

```csharp
private void FontSizeComboBox_TextSubmitted(ComboBox sender, ComboBoxTextSubmittedEventArgs e)
{
    if (byte.TryParse(e.Text, out double newValue))
    {
        // Update the app’s font size.
        _fontSize = newValue;
    }
    else
    {
        // If the item is invalid, reject it and revert the text.
        // Mark the event as handled so the framework doesn’t update the selected item.
        sender.Text = sender.SelectedValue.ToString();
        e.Handled = true;
    }
}
```

### <a name="sample---validate-input-and-add-to-list"></a><span data-ttu-id="159f9-202">Beispiel: Eingabe überprüfen und zur Liste hinzufügen</span><span class="sxs-lookup"><span data-stu-id="159f9-202">Sample - Validate input and add to list</span></span>

<span data-ttu-id="159f9-203">Hier wird ein "als Favorit speichern Farbauswahl" enthält, die am häufigsten verwendeten bevorzugten Farben (Rot, Blau, Grün, Orange), aber der Benutzer kann eine bevorzugte Farbe, die nicht in der Liste ist eingeben.</span><span class="sxs-lookup"><span data-stu-id="159f9-203">Here, a "favorite color chooser" contains the most common favorite colors (Red, Blue, Green, Orange), but the user may enter a favorite color that's not in the list.</span></span> <span data-ttu-id="159f9-204">Wenn der Benutzer eine gültige Farbe (z. B. rosa) hinzufügt, ist die neu eingegebene Farbe der Liste hinzugefügt und als aktive "Bevorzugte Farbe" festgelegt.</span><span class="sxs-lookup"><span data-stu-id="159f9-204">When the user adds a valid color (like Pink), the newly entered color is added to the list and set as the active "favorite color".</span></span>

```xaml
<ComboBox x:Name="favoriteColorComboBox"
          IsEditable="true"
          ItemsSource="{x:Bind ListOfColors}"
          TextSubmitted="FavoriteColorComboBox_TextSubmitted"/>
```

```csharp
private void FavoriteColorComboBox_TextSubmitted(ComboBox sender, ComboBoxTextSubmittedEventArgs e)
{
    if (IsValid(e.Text))
    {
        FavoriteColor newColor = new FavoriteColor()
        {
            ColorName = e.Text,
            Color = ColorFromStringConverter(e.Text)
        }
        ListOfColors.Add(newColor);
    }
    else
    {
        // If the item is invalid, reject it but do not revert the text.
        // Mark the event as handled so the framework doesn’t update the selected item.
        e.Handled = true;
    }
}

bool IsValid(string Text)
{
    // Validate that the string is: not empty; a color.
}
```

## <a name="dos-and-donts"></a><span data-ttu-id="159f9-205">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="159f9-205">Do's and don'ts</span></span>

- <span data-ttu-id="159f9-206">Schränken Sie den Textinhalt von Kombinationsfeldelementen auf eine einzelne Zeile ein.</span><span class="sxs-lookup"><span data-stu-id="159f9-206">Limit the text content of combo box items to a single line.</span></span>
- <span data-ttu-id="159f9-207">Sortieren Sie die Elemente in einem Kombinationsfeld in der logischsten Reihenfolge.</span><span class="sxs-lookup"><span data-stu-id="159f9-207">Sort items in a combo box in the most logical order.</span></span> <span data-ttu-id="159f9-208">Gruppieren Sie verwandte Optionen, und platzieren Sie die am häufigsten verwendeten Optionen oben in der Liste.</span><span class="sxs-lookup"><span data-stu-id="159f9-208">Group together related options and place the most common options at the top.</span></span> <span data-ttu-id="159f9-209">Sortieren Sie Namen in alphabetischer Reihenfolge, Zahlen in numerischer Reihenfolge und Datumsangaben in chronologischer Reihenfolge.</span><span class="sxs-lookup"><span data-stu-id="159f9-209">Sort names in alphabetical order, numbers in numerical order, and dates in chronological order.</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="159f9-210">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="159f9-210">Get the sample code</span></span>

- <span data-ttu-id="159f9-211">[Beispiel eines XAML-Steuerelementekatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="159f9-211">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>
- [<span data-ttu-id="159f9-212">Beispiel für AutoSuggestBox</span><span class="sxs-lookup"><span data-stu-id="159f9-212">AutoSuggestBox sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlAutoSuggestBox)

## <a name="related-articles"></a><span data-ttu-id="159f9-213">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="159f9-213">Related articles</span></span>

- [<span data-ttu-id="159f9-214">Textsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="159f9-214">Text controls</span></span>](text-controls.md)
- [<span data-ttu-id="159f9-215">Rechtschreibprüfung</span><span class="sxs-lookup"><span data-stu-id="159f9-215">Spell checking</span></span>](text-controls.md)
- [<span data-ttu-id="159f9-216">Suche</span><span class="sxs-lookup"><span data-stu-id="159f9-216">Search</span></span>](search.md)
- [<span data-ttu-id="159f9-217">TextBox-Klasse</span><span class="sxs-lookup"><span data-stu-id="159f9-217">TextBox class</span></span>](https://msdn.microsoft.com/library/windows/apps/br209683)
- [<span data-ttu-id="159f9-218">Windows.UI.Xaml.Controls PasswordBox-Klasse</span><span class="sxs-lookup"><span data-stu-id="159f9-218">Windows.UI.Xaml.Controls PasswordBox class</span></span>](https://msdn.microsoft.com/library/windows/apps/br227519)
- [<span data-ttu-id="159f9-219">StringLength-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="159f9-219">String.Length property</span></span>](https://msdn.microsoft.com/library/system.string.length.aspx)
