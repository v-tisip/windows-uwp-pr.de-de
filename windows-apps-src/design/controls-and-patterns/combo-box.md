---
author: Jwmsft
Description: A text entry box that provides suggestions as the user types.
title: Kombinationsfeld (Dropdown-Liste)
label: Combo box
template: detail.hbs
ms.author: jimwalk
ms.date: 10/02/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
pm-contact: stmoy
design-contact: ''
doc-status: Draft
ms.localizationpriority: medium
ms.openlocfilehash: 518ce49ddb631e3e914a6c7662b4e74de247c29c
ms.sourcegitcommit: 82c3fc0b06ad490c3456ad18180a6b23ecd9c1a7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2018
ms.locfileid: "5468435"
---
# <a name="combo-box"></a>Kombinationsfeld

Verwenden Sie ein Kombinationsfeld (auch bekannt als eine Dropdown-Liste), um eine Liste von Elementen, vorhanden sind, die ein Benutzer eine Auswahl treffen kann. Ein Kombinationsfeld wird in einem kompakten Zustand gestartet und erweitert, um eine Liste mit auswählbaren Elementen anzuzeigen.

Wenn das Kombinationsfeld geschlossen wird, es zeigt die aktuelle Auswahl oder ist leer, wenn kein Element ausgewählt ist. Wenn der Benutzer das Kombinationsfeld erweitert, zeigt die Liste mit auswählbaren Elementen an.

> **Wichtige APIs**: [ComboBox-Klasse](/uwp/api/Windows.UI.Xaml.Controls.ComboBox), [IsEditable-Eigenschaft](/uwp/api/windows.ui.xaml.controls.combobox.iseditable), [Text-Eigenschaft](/uwp/api/Windows.UI.Xaml.Controls.ComboBox), [TextSubmitted-Ereignis](/uwp/api/Windows.UI.Xaml.Controls.ComboBox)

Ein Kombinationsfeld im kompakten Zustand mit einer Kopfzeile.

![Beispiel für eine Dropdownliste im kompakten Zustand](images/combo_box_collapsed.png)

## <a name="is-this-the-right-control"></a>Ist dies das richtige Steuerelement?

- Mit einer Dropdownliste können Benutzer einen einzelnen Wert aus einer Reihe von Elementen auswählen, die mit einzelnen Textzeilen angemessen dargestellt werden können.
- Verwenden Sie eine Liste oder eine Rasteransicht anstelle eines Kombinationsfelds, um Elemente anzuzeigen, die mehrere Textzeilen oder Bilder enthalten.
- Wenn weniger als fünf Elemente vorhanden sind, können Sie stattdessen die Verwendung von [Optionsfeldern](radio-button.md) (wenn nur ein Element ausgewählt werden kann) oder [Kontrollkästchen](checkbox.md) (wenn mehrere Elemente ausgewählt werden können) in Betracht ziehen.
- Verwenden Sie ein Kombinationsfeld, wenn die Auswahlelemente für den Fluss der App weniger wichtig sind. Wenn für die Mehrzahl der Benutzer in der Mehrzahl der Situationen die Standardoption empfohlen wird, kann die Anzeige aller Elemente in einer Listenansicht mehr Aufmerksamkeit auf die Optionen ziehen als nötig. Sie können Platz sparen und Ablenkungen reduzieren, indem Sie ein Kombinationsfeld verwenden.

## <a name="examples"></a>Beispiele

<table>
<th align="left">XAML-Steuerelementekatalog<th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p>Wenn Sie die <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> -app installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/ComboBox">die app zu öffnen und finden Sie unter dem Kombinationsfeld in Aktion zu sehen</a>.</p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics">Erwerben Sie den Quellcode (GitHub)</a></li>
    </ul>
</td>
</tr>
</table>

Ein Kombinationsfeld im kompakten Zustand kann eine Kopfzeile anzeigen.

![Beispiel für eine Dropdownliste im kompakten Zustand](images/combo_box_collapsed.png)

Obwohl Kombinationsfelder erweitert werden, um längere Zeichenfolgen zu unterstützen, sollten Sie extrem lange Zeichenfolgen vermeiden, die nur schwer lesbar sind.

![Beispiel einer Dropdownliste mit einer langen Textzeichenfolge](images/combo_box_listitemstate.png)

Wenn die Liste in einem Kombinationsfeld lang genug ist, wird eine Bildlaufleiste angezeigt. Gruppieren Sie die Elemente in der Liste logisch.

![Beispiel einer Bildlaufleiste in einer Dropdownliste](images/combo_box_scroll.png)

## <a name="create-a-combo-box"></a>Erstellen Sie ein Kombinationsfeld

Durch Hinzufügen von Objekten direkt zur Sammlung [Items](/uwp/api/windows.ui.xaml.controls.itemscontrol.items) oder binden die [ItemsSource](/uwp/api/windows.ui.xaml.controls.itemscontrol.itemssource) -Eigenschaft auf eine Datenquelle zu füllen Sie das Kombinationsfeld. Elemente, die dem Kombinationsfeld hinzugefügt werden in [ComboBoxItem](/uwp/api/windows.ui.xaml.controls.comboboxitem) Container eingeschlossen.

Hier ist ein einfaches Kombinationsfeld mit Elementen in XAML hinzugefügt.

```xaml
<ComboBox Header="Colors" PlaceholderText="Pick a color" Width="200">
    <x:String>Blue<x:String>
    <x:String>Green<x:String>
    <x:String>Red<x:String>
    <x:String>Yellow<x:String>
</ComboBox>
```

Im folgende Beispiel wird veranschaulicht, binden ein Kombinationsfeld an eine Sammlung von FontFamily-Objekten.

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

### <a name="item-selection"></a>Elementauswahl

Wie ListView und GridView wird [der Auswahl](/uwp/api/windows.ui.xaml.controls.primitives.selector), ComboBox abgeleitet, so Sie die Auswahl des Benutzers auf die gleiche Weise standard erhalten.

Sie können abrufen oder des Kombinationsfelds ausgewählte Element durch die Verwendung der [SelectedItem](/uwp/api/windows.ui.xaml.controls.primitives.selector.selecteditem) -Eigenschaft und Abrufen oder festlegen den Index des ausgewählten Elements mithilfe der [SelectedIndex](/uwp/api/windows.ui.xaml.controls.primitives.selector.selectedindex) -Eigenschaft.

Um den Wert einer bestimmten Eigenschaft auf das ausgewählte Datenelement zu erhalten, können Sie die [SelectedValue](/uwp/api/windows.ui.xaml.controls.primitives.selector.selectedvalue) -Eigenschaft verwenden. In diesem Fall legen Sie die [SelectedValuePath](/uwp/api/windows.ui.xaml.controls.primitives.selector.selectedvaluepath) an, welche Eigenschaft auf das ausgewählte Element zum Abrufen des Werts aus.

> [!TIP]
> Wenn Sie SelectedItem oder SelectedIndex an, dass die Standardauswahl festlegen, wird eine Ausnahmebedingung ausgelöst, wenn die Eigenschaft festgelegt ist, bevor die Kombinationsfeld Feld Items-Sammlung gefüllt wird. Es sei denn, Sie Ihre Elemente in XAML definieren, empfiehlt es sich um das Kombinationsfeld Feld Loaded-Ereignis behandeln, und legen SelectedItem oder SelectedIndex im Loaded-Ereignis-Handler.

Sie können diese Eigenschaften in XAML binden oder behandeln das [SelectionChanged](/uwp/api/windows.ui.xaml.controls.primitives.selector.selectionchanged) -Ereignis zum Reagieren auf Änderungen der Auswahl.

In den Ereignisdaten können Ereignishandlercode Sie das ausgewählte Element aus der [SelectionChangedEventArgs.AddedItems](/uwp/api/windows.ui.xaml.controls.selectionchangedeventargs.addeditems) -Eigenschaft abrufen. Das zuvor ausgewählte Element (sofern vorhanden) können Sie aus der [SelectionChangedEventArgs.RemovedItems](/uwp/api/windows.ui.xaml.controls.selectionchangedeventargs.removeditems) -Eigenschaft abrufen. Die Addeditems- und RemovedItems-Sammlungen jedes enthalten nur 1 Element, da das Kombinationsfeld Auswahl mehrerer nicht unterstützt.

In diesem Beispiel wird veranschaulicht, wie das SelectionChanged-Ereignis behandelt, und wie Sie auf das ausgewählte Element binden.

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

#### <a name="selectionchanged-and-keyboard-navigation"></a>SelectionChanged und Tastatur navigation

Standardmäßig tritt ein, das SelectionChanged-Ereignis, wenn ein Benutzer klickt, tippt oder drückt EINGABETASTE auf ein Element in der Liste, um ihre Auswahl zu übernehmen, und das Kombinationsfeld wird geschlossen. Auswahl ändern nicht, wenn der Benutzer das Öffnen Kombinationsfeld mit den Pfeiltasten der Tastatur navigiert.

Um ein Kombinationsfeld, das "live aktualisiert" während der Benutzer mit den Pfeiltasten (z. B. eine Schriftart Auswahl Dropdown-Liste) den geöffnete Liste navigiert, [müssen Sie SelectionChangedTrigger](/uwp/api/windows.ui.xaml.controls.combobox.selectionchangedtrigger) auf [immer](/uwp/api/windows.ui.xaml.controls.comboboxselectionchangedtrigger)festgelegt. Dadurch wird das SelectionChanged-Ereignis treten auf, wenn der Fokus auf ein anderes Element in der Liste öffnen geändert wird.

#### <a name="selected-item-behavior-change"></a>Änderung des ausgewählten Elements Verhaltens

Im RS5 (Windows SDK-Version 10.0.NNNNN.0 (Windows 10, Version jjmm), das Verhalten der ausgewählten Elemente wird aktualisiert, um bearbeitbaren Kombinationsfelder unterstützen.

Vor dem RS5, den Wert der SelectedItem-Eigenschaft (und daher SelectedValue und SelectedIndex) wurde, in dem Kombinationsfeld Items-Sammlung erforderlich. Mit dem vorherigen Beispiel wird die Einstellung `colorComboBox.SelectedItem = "Pink"` ergibt:

- SelectedItem = Null
- SelectedValue = Null
- SelectedIndex =-1

In RS5 und höher wird der Wert der SelectedItem-Eigenschaft (und daher SelectedValue und SelectedIndex) ist nicht erforderlich, um in das Kombinationsfeld Items-Sammlung sein. Mit dem vorherigen Beispiel wird die Einstellung `colorComboBox.SelectedItem = "Pink"` ergibt:

- SelectedItem = rosa
- SelectedValue = rosa
- SelectedIndex =-1

### <a name="text-search"></a>Textsuche

Kombinationsfelder unterstützen automatisch die Suche in ihren Sammlungen. Wenn ein Benutzer über eine physische Tastatur Zeichen eingibt, während sich der Fokus auf einem geöffneten oder geschlossenen Kombinationsfeld befindet, werden Vorschläge angezeigt, die der vom Benutzer eingegebenen Zeichenfolge entsprechen. Diese Funktionalität ist besonders bei der Navigation durch eine lange Liste nützlich. Beispielsweise können bei der Interaktion mit einer Dropdownliste, die eine Liste von Bundesstaaten enthält Benutzer die Taste "w", um "Washington" anzuzeigen und schnell auswählen zu drücken. Textsuche ist nicht Groß-/Kleinschreibung berücksichtigt.

Sie können die [IsTextSearchEnabled](/uwp/api/windows.ui.xaml.controls.combobox.istextsearchenabled) -Eigenschaft auf **"false"** zum Deaktivieren dieser Funktion festlegen.

## <a name="make-a-combo-box-editable"></a>Stellen Sie ein Kombinationsfeld bearbeitet werden

> [!IMPORTANT]
> Dieses Feature erfordert die [neuesten Windows 10 Insider Preview-Build und SDK](https://insider.windows.com/for-developers/).

Standardmäßig ein Kombinationsfeld ermöglicht es dem Benutzer aus einer vordefinierten Liste von Optionen auswählen. Es gibt jedoch auch Fälle, in denen die Liste enthält nur eine Teilmenge der gültige Werte, und der Benutzer sollte in der Lage, andere Werte eingeben, die nicht genannt sind. Um dies zu unterstützen, können Sie das Kombinationsfeld bearbeitbar sein.

Um ein Kombinationsfeld bearbeitbar, die [IsEditable](/uwp/api/windows.ui.xaml.controls.combobox.iseditable) -Eigenschaft auf **"true"** festgelegt. Behandeln Sie dann das [TextSubmitted](/uwp/api/Windows.UI.Xaml.Controls.ComboBox) -Ereignis, das mit dem vom Benutzer eingegebenen Wert funktionieren.

Standardmäßig wird der Wert SelectedItem aktualisiert, wenn der Benutzer die benutzerdefinierten Text absendet. Sie können dieses Verhalten überschreiben, indem **Handled** auf **"true"** in den Ereignisargumenten TextSubmitted. Wenn das Ereignis als behandelt markiert ist, wird das Kombinationsfeld wird keine weiteren Maßnahmen nach dem Ereignis und bleibt in der Bearbeitung Zustand. SelectedItem wird nicht aktualisiert werden.

Dieses Beispiel zeigt ein einfaches bearbeitbaren Kombinationsfeld. Die Liste enthält einfache Textzeichenfolgen, und einen beliebigen Wert vom Benutzer eingegebenen wird verwendet, wie Sie eingegeben wurden.

Eine Auswahl "zuletzt verwendete Namen" ermöglicht Benutzern die Eingabe von benutzerdefinierter Zeichenfolgen. Die "RecentlyUsedNames" Liste enthält einige Werte, denen der Benutzer auswählen kann, aber der Benutzer kann auch einen neuen, benutzerdefinierten Wert hinzufügen. Die Eigenschaft "CurrentName" stellt den derzeit eingegebenen Namen.

```xaml
<ComboBox IsEditable="true"
          ItemsSource="{x:Bind RecentlyUsedNames}"
          SelectedItem="{x:Bind CurrentName, Mode=TwoWay}"/>
```

### <a name="text-submitted"></a>Text übermittelt

Sie können das Ereignis [TextSubmitted](/uwp/api/Windows.UI.Xaml.Controls.ComboBox) Arbeit mit den vom Benutzer eingegebenen Wert behandeln. Im Falle Handler, Sie in der Regel überprüft werden kann, dass der Wert, der vom Benutzer eingegebenen gültig ist, verwenden Sie den Wert in Ihrer app. Abhängig von der Situation können Sie auch den Wert auf das Kombinationsfeld Liste von Optionen für die zukünftige Verwendung hinzufügen.

Das TextSubmitted-Ereignis tritt auf, wenn diese Bedingungen erfüllt sind:

- Die IsEditable-Eigenschaft ist **"true"**
- Der Benutzer gibt Text, die nicht mit einen vorhandenen Eintrag in der Liste des Kombinationsfelds übereinstimmt
- Der Benutzer drückt EINGABETASTE oder verlagert den Fokus aus dem Kombinationsfeld.

Das TextSubmitted-Ereignis tritt nicht auf, wenn der Benutzer Text eingibt und dann nach oben oder unten durch die Liste navigiert.

### <a name="sample---validate-input-and-use-locally"></a>Beispiel - Eingabe überprüfen und lokal verwenden

In diesem Beispiel eine Schriftart Größe Auswahl enthält eine Reihe von Werten, die Schriftart Größe Typhierarchie entsprechen, aber der Benutzer möglicherweise Schriftgrößen, die nicht in der Liste sind eingeben.

Wenn der Benutzer einen Wert einfügt, die nicht in der Liste, die Schriftart Größe Updates, aber der Wert wird die Liste der Schriftgrößen nicht hinzugefügt.

Ist der neu eingegebene Wert nicht gültig ist, wird Sie SelectedValue verwenden, um die Text-Eigenschaft auf das letzte Wiederherstellen bekannten guten Wert.

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

### <a name="sample---validate-input-and-add-to-list"></a>Beispiel: Eingabe überprüfen und zur Liste hinzufügen

Hier wird ein "als Favorit speichern Farbauswahl" enthält, die am häufigsten verwendeten bevorzugten Farben (Rot, Blau, Grün, Orange), aber der Benutzer kann eine bevorzugte Farbe, die nicht in der Liste ist eingeben. Wenn der Benutzer eine gültige Farbe (z. B. rosa) hinzufügt, ist die neu eingegebene Farbe der Liste hinzugefügt und als aktive "Bevorzugte Farbe" festgelegt.

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

## <a name="dos-and-donts"></a>Empfohlene und nicht empfohlene Vorgehensweisen

- Schränken Sie den Textinhalt von Kombinationsfeldelementen auf eine einzelne Zeile ein.
- Sortieren Sie die Elemente in einem Kombinationsfeld in der logischsten Reihenfolge. Gruppieren Sie verwandte Optionen, und platzieren Sie die am häufigsten verwendeten Optionen oben in der Liste. Sortieren Sie Namen in alphabetischer Reihenfolge, Zahlen in numerischer Reihenfolge und Datumsangaben in chronologischer Reihenfolge.

## <a name="get-the-sample-code"></a>Beispielcode herunterladen

- [Beispiel eines XAML-Steuerelementekatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.
- [Beispiel für AutoSuggestBox](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlAutoSuggestBox)

## <a name="related-articles"></a>Verwandte Artikel

- [Textsteuerelemente](text-controls.md)
- [Rechtschreibprüfung](text-controls.md)
- [Suche](search.md)
- [TextBox-Klasse](https://msdn.microsoft.com/library/windows/apps/br209683)
- [Windows.UI.Xaml.Controls PasswordBox-Klasse](https://msdn.microsoft.com/library/windows/apps/br227519)
- [StringLength-Eigenschaft](https://msdn.microsoft.com/library/system.string.length.aspx)
