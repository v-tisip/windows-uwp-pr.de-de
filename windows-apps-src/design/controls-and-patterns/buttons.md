---
author: serenaz
Description: A button gives the user a way to trigger an immediate action.
title: Schaltflächen
label: Buttons
template: detail.hbs
ms.author: sezhen
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.assetid: f04d1a3c-7dcd-4bc8-9586-3396923b312e
pm-contact: kisai
design-contact: kimsea
dev-contact: mitra
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: f0bf7731a8480fb4f6d81368227ad6259780381b
ms.sourcegitcommit: c6d6f8b54253e79354f8db14e5cf3b113a3e5014
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "2836720"
---
# <a name="buttons"></a>Schaltflächen

> [!IMPORTANT]
> In diesem Artikel werden Funktionen beschrieben, die noch nicht veröffentlicht wurden und vor der kommerziellen Freigabe evtl. geändert werden. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen. Preview-Features erfordern die [aktuellsten Windows 10 Insider Preview Build und SDK](https://insider.windows.com/for-developers/) oder der [Bibliothek für Windows-Benutzeroberfläche](https://docs.microsoft.com/uwp/toolkits/winui/).

Eine Schaltfläche ermöglicht dem Benutzer das unmittelbare Auslösen einer Aktion. Einige Schaltflächen sind für bestimmte Aufgaben wie das Navigation, wiederholte Aktionen oder einer Präsentation Menüs spezialisierten.

![Beispiel für Schaltflächen](images/controls/button.png)

Das Verwendung von XAML-Framework bietet ein standard Button-Steuerelement als auch mehrere spezielle Button-Steuerelemente.

Steuerelement | Beschreibung
------- | -----------
[Button](/uwp/api/windows.ui.xaml.controls.button) | Initiiert eine sofortige Aktion an. Kann mit einem Click-Ereignis oder den Befehl Bindung verwendet werden.
[RepeatButton](/uwp/api/windows.ui.xaml.controls.primitives.repeatbutton) | Eine Schaltfläche, die gedrückte kontinuierlich ein Click-Ereignis auslöst.
[HyperlinkButton](/uwp/api/windows.ui.xaml.controls.hyperlinkbutton) | Eine Schaltfläche, die formatiert wurde, wie ein Hyperlink, für die Navigation. Weitere Informationen finden Sie unter [Hyperlinks](hyperlinks.md).
[DropDownButton](/uwp/api/windows.ui.xaml.controls.dropdownbutton) | (Vorschau) Eine Schaltfläche mit ein Chevron festgelegt, um eine angefügte flyoutmenü zu öffnen.
[SplitButton](/uwp/api/windows.ui.xaml.controls.splitbutton) | (Vorschau) Eine Schaltfläche mit zwei Seiten. Andererseits initiiert eine Aktion, und die anderen Seite wird ein Menü geöffnet.
[ToggleSplitButton](/uwp/api/windows.ui.xaml.controls.togglesplitbutton) | (Vorschau) Eine Umschaltfläche mit zwei Seiten. Andererseits ein-/ausschalten umgeschaltet, und die anderen Seite wird ein Menü geöffnet.

| **Abrufen der Windows-UI-Bibliothek** |
| - |
| DropDownButton, SplitButton und ToggleSplitButton sind Bestandteil der Windows-UI-Bibliothek, ein NuGet-Paket, das neue Steuerelemente und Features der Benutzeroberfläche für apps UWP enthält. Weitere Informationen, einschließlich Installationshinweise finden Sie unter [Übersicht über die Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/). |

| **Plattform-APIs** | **Windows-UI Library-APIs** |
| - | - |
| Haben [click-Ereignis](/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.click), [Command-Eigenschaft](/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.command) | [DropDownButton-Klasse](/uwp/api/microsoft.ui.xaml.controls.dropdownbutton), [SplitButton-Klasse](/uwp/api/microsoft.ui.xaml.controls.splitbutton), [ToggleSplitButton-Klasse](/uwp/api/microsoft.ui.xaml.controls.togglesplitbutton) |

## <a name="is-this-the-right-control"></a>Ist dies das richtige Steuerelement?

Verwenden Sie eine **Schaltfläche** ermöglichen den Benutzer eine sofortige Aktion, wie etwa Absenden eines Formulars zu initiieren.

Verwenden Sie eine Schaltfläche nicht, wenn die Aktion zum Navigieren zu einer anderen Seite; Verwenden Sie stattdessen eine [HyperlinkButton](/uwp/api/windows.ui.xaml.controls.hyperlinkbutton) . Weitere Informationen finden Sie unter [Hyperlinks](hyperlinks.md).
> Ausnahme: Für die Navigation in einem Assistenten können die Schaltflächen „Zurück“ und „Weiter“ verwendet werden. Für andere Arten von verwenden Abwärtskompatibilität Navigation oder die Navigation zu einer oberen Ebene, Sie eine [Schaltfläche "zurück"](../basics/navigation-history-and-backwards-navigation.md).

Verwenden Sie eine **RepeatButton** , wenn der Benutzer eine Aktion wiederholt auslösen möchten. Verwenden Sie beispielsweise eine RepeatButton erhöhen oder verringern eines Wertes in einen Leistungsindikator.

Verwenden Sie eine **DropDownButton** , wenn die Schaltfläche ein flyoutmenü verfügt, weitere Optionen enthält. Das standardmäßige Chevron bietet einen visuellen Hinweis, dass die Schaltfläche ein flyoutmenü enthält.

Verwenden Sie eine **SplitButton** , wenn Sie möchten den Benutzer können sofortige eine Aktion zu initiieren, oder wählen unabhängig voneinander zusätzliche Optionen.

## <a name="examples"></a>Beispiele

<table>
<th align="left">XAML-Steuerelementekatalog<th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p>Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/Button">die App zu öffnen und die Schaltfläche in Aktion zu sehen</a>.</p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics">Erwerben Sie den Quellcode (GitHub)</a></li>
    </ul>
</td>
</tr>
</table>

In diesem Beispiel werden zwei Schaltflächen („Zulassen“ und „Blockieren“) in einem Dialogfeld verwendet, über das Zugriff auf den Standort des Benutzers angefordert wird.

![Beispiel für Schaltflächen in einem Dialogfeld](images/dialogs/dialog_RS2_two_button.png)

## <a name="create-a-button"></a>Erstellen einer Schaltfläche

Dieses Beispiel zeigt eine Schaltfläche, die auf einen Mausklick reagiert.

Erstellen Sie die Schaltfläche in XAML.

```xaml
<Button Content="Subscribe" Click="SubscribeButton_Click"/>
```

Sie können die Schaltfläche auch in Code erstellen.

```csharp
Button subscribeButton = new Button();
subscribeButton.Content = "Subscribe";
subscribeButton.Click += SubscribeButton_Click;

// Add the button to a parent container in the visual tree.
stackPanel1.Children.Add(subscribeButton);
```

Behandeln Sie das Click-Ereignis.

```csharp
private async void SubscribeButton_Click(object sender, RoutedEventArgs e)
{
    // Call app specific code to subscribe to the service. For example:
    ContentDialog subscribeDialog = new ContentDialog
    {
        Title = "Subscribe to App Service?",
        Content = "Listen, watch, and play in high definition for only $9.99/month. Free to try, cancel anytime.",
        CloseButtonText = "Not Now",
        PrimaryButtonText = "Subscribe",
        SecondaryButtonText = "Try it"
    };

    ContentDialogResult result = await subscribeDialog.ShowAsync();
}
```

### <a name="button-interaction"></a>Interaktion mit Schaltflächen

Wenn Sie mit einem Finger oder Stift auf eine Schaltfläche tippen oder mit der linken Maustaste darauf klicken, löst die Schaltfläche das [Click](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.buttonbase.click.aspx)-Ereignis aus. Bei einer Schaltfläche mit Tastaturfokus wird das Click-Ereignis auch durch Drücken der Eingabe- oder Leertaste ausgelöst.

Sie können für eine Schaltfläche generell keine Low-Level-Ereignisse des Typs [PointerPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.pointerpressed.aspx) behandeln, da sie stattdessen mit dem Click-Verhalten konfiguriert ist. Weitere Informationen finden Sie unter [Übersicht über Ereignisse und Routingereignisse](https://msdn.microsoft.com/library/windows/apps/mt185584.aspx).

Durch Änderung der Eigenschaft [ClickMode](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.clickmode) können Sie anpassen, wie eine Schaltfläche Click-Ereignisse auslöst. Der ClickMode-Standardwert ist **Version**, Sie können den ClickMode einer Schaltfläche jedoch auch auf **Zeigen** oder **Drücken** festlegen. Wenn als ClickMode-Wert **Hover** festgelegt ist, kann das Click-Event nicht über die Tastatur oder durch Berührung ausgelöst werden.


### <a name="button-content"></a>Inhalt von Schaltflächen

„Button“ ist ein Element des Typs [ContentControl](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.contentcontrol.aspx). Die zugehörige XAML-Inhaltseigenschaft ist [Content](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.contentcontrol.content.aspx). Mit ihr lässt sich in XAML folgende Syntax nutzen: `<Button>A button's content</Button>`. Sie können jedes Objekt als Inhalt der Schaltfläche festlegen. Wenn der Inhalt ein [UIElement](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.uielement.aspx) ist, wird er in der Schaltfläche gerendert. Wenn es sich beim Inhalt um einen anderen Objekttyp handelt, wird die entsprechende Zeichenfolgendarstellung in der Schaltfläche angezeigt.

Der Inhalt einer Schaltfläche ist für gewöhnlich Text. Nachstehend finden Sie Entwurfsempfehlungen für Schaltflächen mit Textinhalt:
-   Verwenden Sie kurze, spezifische und selbsterklärende Texte, aus denen die Funktion einer Schaltfläche eindeutig hervorgeht. In der Regel umfasst der Schaltflächen-Textinhalt ein einzelnes Wort: ein Verb.
-   Verwenden Sie die standardmäßige Schriftart, es sei denn, Sie müssen entsprechend Ihren Markenrichtlinien eine andere verwenden.
-   Vermeiden Sie für kürzeren Text schmale Befehlsschaltflächen, indem Sie eine Schaltflächen-Mindestbreite von 120Pixel verwenden.
- Vermeiden Sie für längeren Text breite Befehlsschaltflächen, indem Sie Text auf eine maximale Länge von 26Zeichen beschränken.
-   Wenn der Textinhalt der Schaltfläche dynamisch ist (beispielsweise wenn er [lokalisiert](../globalizing/globalizing-portal.md) ist), ziehen Sie die Größenänderung der Schaltfläche und das in Betracht, was mit den Steuerelementen herum passiert.

<table>
<tr>
<td> <b>Folgendes muss geändert werden:</b><br> Schaltflächen mit überlaufendem Text. </td>
<td> <img src="images/button-wraptext.png"/> </td>
</tr>
<tr>
<td> <b>Option 1:</b><br> Vergrößern Sie die Breite der Schaltflächen, stapeln Sie Schaltflächen und brechen Sie Text um, wenn er mehr als 26Zeichen umfasst. </td>
<td> <img src="images/button-wraptext1.png"> </td>
</tr>
<tr>
<td> <b>Option 2:</b><br> Erhöhen Sie die Schaltflächenhöhe und brechen Sie Text um. </td>
<td> <img src="images/button-wraptext2.png"> </td>
</tr>
</table>

Sie können auch die visuellen Elemente anpassen, die die Darstellung der Schaltfläche ausmachen. Sie können beispielsweise den Text durch ein Symbol ersetzen oder ein Symbol und Text verwenden.

Im folgenden Beispiel wird ein **StackPanel**-Element, das ein Bild und Text enthält, als Inhalt einer Schaltfläche festgelegt.

```xaml
<Button Click="Button_Click"
        Background="LightGray"
        Height="100" Width="80">
    <StackPanel>
        <Image Source="Assets/Photo.png" Height="62"/>
        <TextBlock Text="Photos" Foreground="Black"
                   HorizontalAlignment="Center"/>
    </StackPanel>
</Button>
```

Die Schaltfläche sieht wie folgt aus.

![Eine Schaltfläche mit Bild- und Textinhalt](images/button-orange.png)

## <a name="create-a-repeat-button"></a>Erstellen einer Wiederholungsschaltfläche

Eine Schaltfläche des Typs [RepeatButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.aspx) ist eine Schaltfläche, die das [Click](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.buttonbase.click.aspx)-Ereignis ab dem Moment des Klickens oder Drückens auf die Schaltfläche solange wiederholt auslöst, bis der Benutzer die Maustaste loslässt oder nicht mehr auf die Schaltfläche drückt. Über die Eigenschaft [Delay](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.delay.aspx) können Sie festlegen, wie lange eine Schaltfläche des Typs„RepeatButton“ nach dem Klicken oder Drücken wartet, bevor sie mit der Wiederholung der Click-Aktion beginnt. Über die Eigenschaft [Interval](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.interval.aspx) können Sie den Zeitintervall zwischen den einzelnen Wiederholungen der Click-Aktion definieren. Die Zeiten beider Eigenschaften werden in Millisekunden angegeben.

Das folgende Beispiel zeigt zwei „RepeatButton“-Steuerelemente. Ihre jeweiligen Click-Ereignisse dienen dazu, den Wert in einem Textblock zu erhöhen oder zu verringern.

```xaml
<StackPanel>
    <RepeatButton Width="100" Delay="500" Interval="100" Click="Increase_Click">Increase</RepeatButton>
    <RepeatButton Width="100" Delay="500" Interval="100" Click="Decrease_Click">Decrease</RepeatButton>
    <TextBlock x:Name="clickTextBlock" Text="Number of Clicks:" />
</StackPanel>
```

```csharp
private static int _clicks = 0;
private void Increase_Click(object sender, RoutedEventArgs e)
{
    _clicks += 1;
    clickTextBlock.Text = "Number of Clicks: " + _clicks;
}

private void Decrease_Click(object sender, RoutedEventArgs e)
{
    if(_clicks > 0)
    {
        _clicks -= 1;
        clickTextBlock.Text = "Number of Clicks: " + _clicks;
    }
}
```

## <a name="create-a-drop-down-button"></a>Erstellen Sie ein Dropdown-Schaltfläche

> **Vorschau**: DropDownButton erfordert die [aktuellsten Windows 10 Insider Preview Build und SDK](https://insider.windows.com/for-developers/) oder der [Bibliothek für Windows-Benutzeroberfläche](https://docs.microsoft.com/uwp/toolkits/winui/).

Eine [DropDownButton](/uwp/api/windows.ui.xaml.controls.dropdownbutton) ist eine Schaltfläche, die einem Chevron festgelegt als ein optischer Indikator zeigt an, dass es eine angefügte flyoutmenü verfügt, weitere Optionen enthält. Es hat die gleiche Wirkung wie einer Standardschaltfläche mit einem Dropdown; nur die Darstellung unterscheidet.

Die Dropdown-Schaltfläche erbt das Click-Ereignis, aber in der Regel verwenden Sie es. Verwenden Sie die Dropdown-Eigenschaft zum Anfügen einer flyoutmenü und Aufrufen von Aktionen mithilfe von Menüoptionen in der Dropdown. Das Flyout wird beim Klicken auf die Schaltfläche automatisch geöffnet.

> [!TIP]
> Weitere Informationen zu Flyouts finden Sie unter [Menüs und Kontextmenüs](menus.md).

### <a name="example---drop-down-button"></a>Beispiel - Dropdown-Schaltfläche

In diesem Beispiel wird gezeigt, wie eine Dropdown-Schaltfläche mit einer flyoutmenü erstellen, Befehle für die Ausrichtung von Absätzen in einem RichEditBox enthält. (Weitere Informationen und Code finden Sie unter [Rich Eingabefelds](rich-edit-box.md)).

![Ein Dropdown-Schaltfläche mit Befehle für das Ausrichten](images/drop-down-button-align.png)

```xaml
<DropDownButton ToolTipService.ToolTip="Alignment">
    <TextBlock FontFamily="Segoe MDL2 Assets" FontSize="16" Text="&#xE8E4;"/>
    <DropDownButton.Flyout>
        <MenuFlyout Placement="BottomEdgeAlignedLeft">
            <MenuFlyoutItem Text="Left" Icon="AlignLeft" Tag="left"
                            Click="AlignmentMenuFlyoutItem_Click"/>
            <MenuFlyoutItem Text="Center" Icon="AlignCenter" Tag="center"
                            Click="AlignmentMenuFlyoutItem_Click"/>
            <MenuFlyoutItem Text="Right" Icon="AlignRight" Tag="right"
                            Click="AlignmentMenuFlyoutItem_Click"/>
        </MenuFlyout>
    </DropDownButton.Flyout>
</DropDownButton>
```

```csharp
private void AlignmentMenuFlyoutItem_Click(object sender, RoutedEventArgs e)
{
    var option = ((MenuFlyoutItem)sender).Tag.ToString();

    Windows.UI.Text.ITextSelection selectedText = editor.Document.Selection;
    if (selectedText != null)
    {
        // Apply the alignment to the selected paragraphs.
        var paragraphFormatting = selectedText.ParagraphFormat;
        if (option == "left")
        {
            paragraphFormatting.Alignment = Windows.UI.Text.ParagraphAlignment.Left;
        }
        else if (option == "center")
        {
            paragraphFormatting.Alignment = Windows.UI.Text.ParagraphAlignment.Center;
        }
        else if (option == "right")
        {
            paragraphFormatting.Alignment = Windows.UI.Text.ParagraphAlignment.Right;
        }
    }
}
```

## <a name="create-a-split-button"></a>Erstellen Sie eine Trennschaltfläche

> **Vorschau**: SplitButton erfordert die [aktuellsten Windows 10 Insider Preview Build und SDK](https://insider.windows.com/for-developers/) oder der [Bibliothek für Windows-Benutzeroberfläche](https://docs.microsoft.com/uwp/toolkits/winui/).

Ein [SplitButton](/uwp/api/windows.ui.xaml.controls.splitbutton) besteht aus zwei Teilen, die separat aufgerufen werden können. Ein Teil einer Standardschaltfläche Verhalten und sofortige eine Aktion aufruft. Andererseits Ruft ein flyoutmenü, die zusätzliche Optionen, mit denen der Benutzer auswählen können.

> [!NOTE]
> Wenn mit Touch aufgerufen, verhält sich wie ein Dropdown-Schaltfläche Trennschaltfläche; Beide Hälften der Schaltfläche Aufrufen der Dropdown. Mit anderen Methoden der Eingabe kann Benutzer entweder Hälfte der Schaltfläche separat aufrufen.

Das normale Verhalten für eine Trennschaltfläche ist:

- Wenn der Benutzer auf das Schaltfläche Webpart klickt, behandeln Sie das Click-Ereignis, um die Option aufrufen, die derzeit in der Dropdownliste ausgewählt ist.
- Die Dropdownliste geöffnet ist, Handle Aufruf der Elemente in der Dropdown-Liste beide ändern die option ausgewählt ist, und rufen Sie sie. Es ist wichtig, die das Dropdown-Element aufgerufen werden, da die Schaltfläche Click-Ereignis tritt nicht auf, wenn die Verwendung von Touch.

> [!TIP]
> Es gibt viele Methoden, um Elemente in der Dropdownliste nach unten zu platzieren und deren Aufruf behandeln. Wenn Sie eine ListView oder GridView verwenden, ist eine Möglichkeit, das SelectionChanged-Ereignis behandeln. Wenn Sie dies tun, [SingleSelectionFollowsFocus](/uwp/api/windows.ui.xaml.controls.listviewbase.singleselectionfollowsfocus) auf **false**festgelegt. Auf diese Weise können Benutzer die Optionen über die Tastatur ohne das Element auf jeder Änderung aufrufen zu navigieren.

### <a name="example---split-button"></a>Beispiel - Trennschaltfläche

In diesem Beispiel wird gezeigt, wie eine Trennschaltfläche erstellen, die verwendet wird, um die Vordergrundfarbe des ausgewählten Texts in einem RichEditBox ändern. (Weitere Informationen und Code finden Sie unter [Rich Eingabefelds](rich-edit-box.md)).

![Eine Trennschaltfläche für die Auswahl von Vordergrundfarbe](images/split-button-rtb.png)

```xaml
<SplitButton ToolTipService.ToolTip="Foreground color"
             Click="BrushButtonClick">
    <Border x:Name="SelectedColorBorder" Width="20" Height="20"/>
    <SplitButton.Flyout>
        <Flyout x:Name="BrushFlyout" Placement="BottomEdgeAlignedLeft">
            <!-- Set SingleSelectionFollowsFocus="False"
                 so that keyboard navigation works correctly. -->
            <GridView ItemsSource="{x:Bind ColorOptions}" 
                      SelectionChanged="BrushSelectionChanged"
                      SingleSelectionFollowsFocus="False"
                      SelectedIndex="0" Padding="0">
                <GridView.ItemTemplate>
                    <DataTemplate>
                        <Rectangle Fill="{Binding}" Width="20" Height="20"/>
                    </DataTemplate>
                </GridView.ItemTemplate>
                <GridView.ItemContainerStyle>
                    <Style TargetType="GridViewItem">
                        <Setter Property="Margin" Value="2"/>
                        <Setter Property="MinWidth" Value="0"/>
                        <Setter Property="MinHeight" Value="0"/>
                    </Style>
                </GridView.ItemContainerStyle>
            </GridView>
        </Flyout>
    </SplitButton.Flyout>
</SplitButton>
```

```csharp
public sealed partial class MainPage : Page
{
    // Color options that are bound to the grid in the split button flyout.
    private List<SolidColorBrush> ColorOptions = new List<SolidColorBrush>();
    private SolidColorBrush CurrentColorBrush = null;

    public MainPage()
    {
        this.InitializeComponent();

        // Add color brushes to the collection.
        ColorOptions.Add(new SolidColorBrush(Colors.Black));
        ColorOptions.Add(new SolidColorBrush(Colors.Red));
        ColorOptions.Add(new SolidColorBrush(Colors.Orange));
        ColorOptions.Add(new SolidColorBrush(Colors.Yellow));
        ColorOptions.Add(new SolidColorBrush(Colors.Green));
        ColorOptions.Add(new SolidColorBrush(Colors.Blue));
        ColorOptions.Add(new SolidColorBrush(Colors.Indigo));
        ColorOptions.Add(new SolidColorBrush(Colors.Violet));
        ColorOptions.Add(new SolidColorBrush(Colors.White));
    }

    private void BrushButtonClick(object sender, object e)
    {
        // When the button part of the split button is clicked,
        // apply the selected color.
        ChangeColor();
    }

    private void BrushSelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        // When the flyout part of the split button is opened and the user selects
        // an option, set their choice as the current color, apply it, then close the flyout.
        CurrentColorBrush = (SolidColorBrush)e.AddedItems[0];
        SelectedColorBorder.Background = CurrentColorBrush;
        ChangeColor();
        BrushFlyout.Hide();
    }

    private void ChangeColor()
    {
        // Apply the color to the selected text in a RichEditBox.
        Windows.UI.Text.ITextSelection selectedText = editor.Document.Selection;
        if (selectedText != null)
        {
            Windows.UI.Text.ITextCharacterFormat charFormatting = selectedText.CharacterFormat;
            charFormatting.ForegroundColor = CurrentColorBrush.Color;
            selectedText.CharacterFormat = charFormatting;
        }
    }
}
```

## <a name="create-a-toggle-split-button"></a>Erstellen Sie eine geteilte Umschaltfläche

> **Vorschau**: ToggleSplitButton erfordert die [aktuellsten Windows 10 Insider Preview Build und SDK](https://insider.windows.com/for-developers/) oder der [Bibliothek für Windows-Benutzeroberfläche](https://docs.microsoft.com/uwp/toolkits/winui/).

Eine [ToggleSplitButton](/uwp/api/windows.ui.xaml.controls.togglesplitbutton) besteht aus zwei Teilen, die separat aufgerufen werden können. Einerseits verhält sich wie eine Umschaltfläche, die aktiviert oder deaktiviert werden können. Andererseits Ruft ein flyoutmenü, die zusätzliche Optionen, mit denen der Benutzer auswählen können.

Eine Umschaltfläche Teilen wird in der Regel verwendet, aktivieren oder Deaktivieren eines Features, wenn das Feature für mehrere Optionen wurde, denen der Benutzer auswählen können. Beispielsweise könnte in einem Dokument-Editor Hiermit Listen aktivieren oder deaktivieren, während die Dropdownliste verwendet wird, um den Stil der Liste wählen.

> [!NOTE]
> Wenn mit Touch aufgerufen, verhält sich wie ein Dropdown-Schaltfläche Trennschaltfläche. Mit anderen Methoden der Eingabe kann Benutzer entweder Hälfte der Schaltfläche separat aufrufen. Touchscreens aufrufen, beide Hälften der Schaltfläche für die flyoutmenü. Daher müssen Sie eine Option in den Inhalt der flyoutmenü in aktiviert oder deaktiviert die Umschaltfläche einbeziehen.

### <a name="differences-with-togglebutton"></a>Unterschiede mit ToggleButton-Objekt

Im Gegensatz zu [ToggleButton](/uwp/api/windows.ui.xaml.controls.primitives.togglebutton)verfügt ToggleSplitButton nicht unbestimmten Zustand befindet. Daher sollten Sie diese Unterschiede bedenken:

- ToggleSplitButton muss sich nicht auf einem **IsThreeState** -Eigenschaft oder **Indeterminate** -Ereignis aus.
- Die [ToggleSplitButton.IsChecked](/uwp/api/windows.ui.xaml.controls.togglesplitbutton.ischecked) -Eigenschaft ist nur ein **Bool**, nicht **NULL-Werte zulässt Bool**.
- ToggleSplitButton hat nur das [IsCheckedChanged](/uwp/api/windows.ui.xaml.controls.togglesplitbutton.ischeckedchanged) -Ereignis. Es hat keine separate **aktiviert** und **deaktiviert** Ereignisse.

### <a name="example---toggle-split-button"></a>Beispiel - Umschaltfläche unterteilte Schaltfläche

Das folgende Beispiel zeigt, wie eine Umschaltfläche Trennschaltfläche listenformatierung ein- oder ausschalten aktivieren verwendet werden, und Ändern des Stils eines der Liste in einem RichEditBox. (Weitere Informationen und Code finden Sie unter [Rich Eingabefelds](rich-edit-box.md)).

![Eine Umschaltfläche geteilten für die Auswahl von Listenformaten](images/toggle-split-button-open.png)

```xaml
<ToggleSplitButton x:Name="ListButton"
                   ToolTipService.ToolTip="List style"
                   Click="ListButton_Click"
                   IsCheckedChanged="ListStyleButton_IsCheckedChanged">
    <TextBlock FontFamily="Segoe MDL2 Assets" FontSize="16" Text="&#xE8FD;"/>
    <ToggleSplitButton.Flyout>
        <Flyout Placement="BottomEdgeAlignedLeft">
            <ListView x:Name="ListStylesListView"
                      SelectionChanged="ListStylesListView_SelectionChanged" 
                      SingleSelectionFollowsFocus="False">
                <StackPanel Tag="bullet" Orientation="Horizontal">
                    <FontIcon FontFamily="Segoe MDL2 Assets" Glyph="&#xE7C8;"/>
                    <TextBlock Text="Bullet" Margin="8,0"/>
                </StackPanel>
                <StackPanel Tag="alpha" Orientation="Horizontal">
                    <TextBlock Text="A" FontSize="24" Margin="2,0"/>
                    <TextBlock Text="Alpha" Margin="8"/>
                </StackPanel>
                <StackPanel Tag="numeric" Orientation="Horizontal">
                    <FontIcon FontFamily="Segoe MDL2 Assets" Glyph="&#xF146;"/>
                    <TextBlock Text="Numeric" Margin="8,0"/>
                </StackPanel>
                <TextBlock Tag="none" Text="None" Margin="28,0"/>
            </ListView>
        </Flyout>
    </ToggleSplitButton.Flyout>
</ToggleSplitButton>
```

```csharp
private void ListStyleButton_IsCheckedChanged(ToggleSplitButton sender, ToggleSplitButtonIsCheckedChangedEventArgs args)
{
    // Use the toggle button to turn the selected list style on or off.
    if (((ToggleSplitButton)sender).IsChecked == true)
    {
        // On. Apply the list style selected in the drop down to the selected text.
        var listStyle = ((FrameworkElement)(ListStylesListView.SelectedItem)).Tag.ToString();
        ApplyListStyle(listStyle);
    }
    else
    {
        // Off. Make the selected text not a list,
        // but don't change the list style selected in the drop down.
        ApplyListStyle("none");
    }
}

private void ListStylesListView_SelectionChanged(object sender, SelectionChangedEventArgs e)
{
    var listStyle = ((FrameworkElement)(e.AddedItems[0])).Tag.ToString();

    if (ListButton.IsChecked == true)
    {
        // Toggle button is on. Turn it off...
        if (listStyle == "none")
        {
            ListButton.IsChecked = false;
        }
        else
        {
            // or apply the new selection.
            ApplyListStyle(listStyle);
        }
    }
    else
    {
        // Toggle button is off. Turn it on, which will apply the selection
        // in the IsCheckedChanged event handler.
        ListButton.IsChecked = true;
    }
}

private void ApplyListStyle(string listStyle)
{
    Windows.UI.Text.ITextSelection selectedText = editor.Document.Selection;
    if (selectedText != null)
    {
        // Apply the list style to the selected text.
        var paragraphFormatting = selectedText.ParagraphFormat;
        if (listStyle == "none")
        {  
            paragraphFormatting.ListType = Windows.UI.Text.MarkerType.None;
        }
        else if (listStyle == "bullet")
        {
            paragraphFormatting.ListType = Windows.UI.Text.MarkerType.Bullet;
        }
        else if (listStyle == "numeric")
        {
            paragraphFormatting.ListType = Windows.UI.Text.MarkerType.Arabic;
        }
        else if (listStyle == "alpha")
        {
            paragraphFormatting.ListType = Windows.UI.Text.MarkerType.UppercaseEnglishLetter;
        }
        selectedText.ParagraphFormat = paragraphFormatting;
    }
}
```

## <a name="recommendations"></a>Empfehlungen

- Der Zweck und Status einer Schaltfläche müssen für den Benutzer eindeutig sein.
- Wenn mehrere Schaltflächen für die gleiche Entscheidung (z.B. in einem Bestätigungsdialogfeld) vorhanden sind, stellen Sie die Schaltflächen für den Commit in der folgenden Reihenfolge dar, wobei [Ausführen] und [Nicht ausführen] bestimmte Antworten auf die Hauptanweisung sind:
    - OK/[Ausführen]/Ja
    - [Nicht ausführen]/Nein
    - Abbrechen
- Stellen Sie dem Benutzer jeweils nur zwei Schaltflächen zur Verfügung, beispielsweise „Akzeptieren“ und „Abbrechen“. Wenn Sie dem Benutzer mehr Aktionen zur Verfügung stellen möchten, sollten Sie [Kontrollkästchen](checkbox.md) oder [Optionsfelder](radio-button.md) verwenden, über die der Benutzer Aktionen mit einer einzelnen Befehlsschaltfläche auslösen kann.
- Für eine Aktion, die auf mehreren Seiten in Ihrer App verfügbar sein muss, sollten Sie die Verwendung einer [unteren App-Leiste](app-bars.md) in Erwägung ziehen, anstatt eine Schaltfläche auf mehreren Seiten zu duplizieren.

### <a name="recommended-single-button-layout"></a>Empfehlungen für Layouts mit einer einzigen Schaltfläche

Wenn in Ihrem Layout nur eine einzige Schaltfläche benötigt wird, sollten Sie diese je nach ihrem Containerkontext entweder linksbündig oder rechtsbündig ausrichten.

- In Dialogfeldern mit nur einer einzigen Schaltfläche sollte die Schaltfläche **rechtsbündig** ausgerichtet sein. Stellen Sie bei Dialogfeldern mit nur einer einzigen Schaltfläche sicher, dass die Schaltfläche die sichere, nicht destruktive Aktion ausführt. Wenn Sie die Klasse [ContentDialog](dialogs.md) verwenden und nur eine einzige Schaltfläche definieren, wird diese Schaltfläche automatisch rechtsbündig ausgerichtet.

![Schaltfläche in einem Dialogfeld](images/pushbutton_doc_dialog.png)

- Wird die Schaltfläche als Teil einer Containerbenutzeroberfläche angezeigt (z.B. innerhalb einer Popupbenachrichtigung, eines Flyouts oder eines Listenansicht-Elements), sollten Sie die Schaltfläche innerhalb des Containers **rechtsbündig** ausrichten.

![Eine Schaltfläche in einem Container](images/pushbutton_doc_container.png)

- Auf Seiten mit einer einzigen Schaltfläche (z.B. einer Einstellungsseite mit einer „Anwenden“-Schaltfläche am unteren Rand) sollten Sie die Schaltfläche **linksbündig** ausrichten. Das gewährleistet, dass die Schaltfläche passend zum übrigen Seiteninhalt ausgerichtet ist.

![Eine Schaltfläche auf einer Seite](images/pushbutton_doc_page.png)

## <a name="back-buttons"></a>„Zurück“-Schaltflächen

Die Zurück-Schaltfläche ist ein durch das System bereitgestelltes UI-Element, das die Rückwärtsnavigation über den Back-Stapel oder den Navigationsverlauf des Benutzers ermöglicht. Sie müssen keine eigene Zurück-Schaltfläche erstellen, aber unter Umständen ist etwas Aufwand erforderlich, um eine gute Rückwärtsnavigation zu ermöglichen. Weitere Informationen finden Sie unter [Verlauf und Rückwärtsnavigation](../basics/navigation-history-and-backwards-navigation.md).

## <a name="get-the-sample-code"></a>Beispielcode herunterladen

- [Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.

## <a name="related-articles"></a>Verwandte Artikel

- [Button-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.button.aspx)
- [Optionsfelder](radio-button.md)
- [Kontrollkästchen](checkbox.md)
- [Umschalter](toggles.md)
