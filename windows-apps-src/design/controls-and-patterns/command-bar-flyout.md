---
author: jwmsft
Description: Command bar flyouts give users inline access to your app's most common tasks.
title: Befehlsleisten-Flyout
label: Command bar flyout
template: detail.hbs
ms.author: jimwalk
ms.date: 10/2/2018
ms.topic: article
keywords: Windows10, UWP
pm-contact: abarlow
design-contact: ksulliv
dev-contact: llongley
doc-status: Draft
ms.localizationpriority: medium
ms.openlocfilehash: 95d99c41ff2679e3ef3e0471dd583fe78458922c
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "5919158"
---
# <a name="command-bar-flyout"></a>Befehlsleisten-Flyout

Befehl Bar Flyout können Sie Benutzer schnellen Zugriff auf häufige Aufgaben zeigen Befehle eine schwebende Werkzeugleiste ein Element auf der Leinwand UI bereitstellen.

![Eine erweiterte Text Command Bar flyout](images/command-bar-flyout-header.png)

> CommandBarFlyout erfordert Windows 10 Version 1809 ([SDK 17763](https://developer.microsoft.com/windows/downloads/windows-10-sdk)) oder höher, oder [Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).

> - **Plattform-APIs**: [CommandBarFlyout Klasse](/uwp/api/windows.ui.xaml.controls.commandbarflyout) [TextCommandBarFlyout Klasse](/uwp/api/windows.ui.xaml.controls.textcommandbarflyout) [AppBarButton Klasse](/uwp/api/windows.ui.xaml.controls.appbarbutton), [AppBarToggleButton-Klasse](/uwp/api/windows.ui.xaml.controls.appbartogglebutton), [AppBarSeparator-Klasse](/uwp/api/windows.ui.xaml.controls.appbarseparator)
>- **Windows-UI Library-APIs**: [CommandBarFlyout Klasse](/uwp/api/microsoft.ui.xaml.controls.commandbarflyout), [TextCommandBarFlyout-Klasse](/uwp/api/microsoft.ui.xaml.controls.textcommandbarflyout)

Wie [CommandBar](app-bars.md)hat CommandBarFlyout **PrimaryCommands** und **SecondaryCommands** Eigenschaften, Befehle hinzufügen. Sie können Befehle in Auflistung oder beiden platzieren. Wann und wie die primären und sekundären Befehle angezeigt werden, hängt von den Anzeigemodus.

Flyout-Leiste Befehl verfügt über zwei Anzeigemodi: *reduziert* und *Erweitert*.

- Im reduzierten Modus werden nur die primäre Befehle angezeigt. Der Befehl Balken Flyout hat primäre und sekundäre Befehle eine Schaltfläche "Weitere Informationen", vertreten durch Auslassungspunkte \ [•••\] wird angezeigt. Dies ermöglicht den Benutzer Zugriff auf die sekundären Befehle vom erweiterten Modus wechselt.
- Im erweiterten Modus werden die primären und sekundären Befehle angezeigt. (Wenn das Steuerelement nur sekundäre Elemente verfügt, werden sie ähnlich wie das MenuFlyout-Steuerelement angezeigt.)

## <a name="is-this-the-right-control"></a>Ist dies das richtige Steuerelement?

Mithilfe des CommandBarFlyout-Steuerelements eine Sammlung von Befehlen, wie Schaltflächen und Menüelemente im Kontext eines Elements auf der Leinwand app anzeigen.

Der TextCommandBarFlyout zeigt Befehle in TextBox, TextBlock-, RichEditBox, RichTextBlock und PasswordBox-Steuerelemente. Die Befehle werden automatisch auf die aktuelle Textauswahl entsprechend konfiguriert. Verwenden Sie ein CommandBarFlyout Text Standardbefehle auf Textsteuerelemente ersetzen.

Kontextbezogene Anzeige folgen Befehle für Listenelemente Handbuchs [kontextuelle Befehle für Sammlungen und Listen](collection-commanding.md)

### <a name="commandbarflyout-vs-menuflyout"></a>CommandBarFlyout gegen MenuFlyout

Um Befehle im Kontextmenü angezeigt wird, können Sie CommandBarFlyout oder MenuFlyout. CommandBarFlyout wird empfohlen, da dadurch mehr Funktionen als MenuFlyout. Können CommandBarFlyout mit sekundären Befehle das Verhalten und Aussehen einer MenuFlyout oder vollständigen Befehl Bar Flyout mit primären und sekundären Befehlen verwenden.

> Verwandte Informationen finden Sie unter [Flyout](../controls-and-patterns/dialogs-and-flyouts/flyouts.md), [Menüs und Kontextmenüs](menus.md)und [Symbolleisten](app-bars.md).

## <a name="examples"></a>Beispiele

<table>
<th align="left">XAML-Steuerelementekatalog<th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p>Wenn Sie <strong style="font-weight: semi-bold">XAML-Steuerelementsammlungen</strong> app installiert haben, klicken Sie hier zu <a href="xamlcontrolsgallery:/item/CommandBarFlyout">Öffnen die Anwendung CommandBarFlyout in Aktion</a>.</p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics">Erwerben Sie den Quellcode (GitHub)</a></li>
    </ul>
</td>
</tr>
</table>

## <a name="proactive-vs-reactive-invocation"></a>Proaktive und reaktive Aufruf

Zweierlei normalerweise zum Aufrufen einer Flyout oder einem Menü ein Element auf der Leinwand UI zugeordnet hat: _Aufruf proaktive_ und _reaktive Aufruf_.

Proaktive Aufruf werden Befehle automatisch bei die Befehlen zugeordnet sind das Element der Benutzer interagiert. Beispielsweise können Text Formatierungsbefehle eingeblendet, wenn der Benutzer Text in ein Textfeld markiert. In diesem Fall übernimmt das Befehl Balken Flyout Fokus. Stattdessen stellt Befehlen nahe das Element, dem mit der Benutzer interagiert. Wenn der Benutzer die Befehle interagieren nicht, werden sie geschlossen.

Reaktive Aufruf werden Befehle auf einer expliziten Benutzeraktion Anfordern der Befehle angezeigt. beispielsweise eine Maustaste. Dies entspricht der herkömmlichen Konzepts für ein [Kontextmenü](menus.md).

CommandBarFlyout Weg oder auch eine Mischung aus beiden können.

## <a name="create-a-command-bar-flyout"></a>Ein Befehl Bar Flyout erstellen

Dieses Beispiel zeigt, wie ein Befehl Bar Flyout und proaktiv und reaktiv. Wenn das Bild getippt wird, wird Flyout im reduzierten Modus angezeigt. Wenn ein Kontextmenü, wird das Flyout im erweiterten Modus angezeigt. In beiden Fällen kann der Benutzer erweitern oder reduzieren das Flyout nach öffnen.

![Beispiel für eine reduzierte Befehl Bar flyout](images/command-bar-flyout-img-collapsed.png)

> _Ein Flyout reduzierten Befehl bar_

![Beispiel für einen Flyout expandierte Befehl bar](images/command-bar-flyout-img-expanded.png)

> _Ein Flyout expandierte Befehl bar_

```xaml
<Grid>
    <Grid.Resources>
        <CommandBarFlyout x:Name="ImageCommandsFlyout">
            <AppBarButton Icon="OutlineStar" ToolTipService.ToolTip="Favorite"/>
            <AppBarButton Icon="Copy" ToolTipService.ToolTip="Copy"/>
            <AppBarButton Icon="Share" ToolTipService.ToolTip="Share"/>
            <CommandBarFlyout.SecondaryCommands>
                <AppBarButton Label="Select all"/>
                <AppBarButton Label="Delete" Icon="Delete"/>
            </CommandBarFlyout.SecondaryCommands>
        </CommandBarFlyout>
    </Grid.Resources>

    <Image Source="Assets/image1.png" Width="300"
           Tapped="Image_Tapped" FlyoutBase.AttachedFlyout="{x:Bind ImageCommandsFlyout}"
           ContextFlyout="{x:Bind ImageCommandsFlyout}"/>
</Grid>
```

```csharp
private void Image_Tapped(object sender, TappedRoutedEventArgs e)
{
    var flyout = FlyoutBase.GetAttachedFlyout((FrameworkElement)sender);
    var options = new FlyoutShowOptions()
    {
        // Position shows the flyout next to the pointer.
        // "Transient" ShowMode makes the flyout open in its collapsed state.
        Position = e.GetPosition((FrameworkElement)sender),
        ShowMode = FlyoutShowMode.Transient
    };
    flyout?.ShowAt((FrameworkElement)sender, options);
}
```

### <a name="show-commands-proactively"></a>Proaktiv Befehle anzeigen

Wenn Sie proaktiv Kontextmenüs anzeigen, soll die primären Befehle standardmäßig angezeigt werden (das Befehl Balken Flyout sollte ausgeblendet). Setzen Sie die wichtigsten Befehle in primären Commands-Auflistung und zusätzliche Befehle, die normalerweise in einem Kontextmenü in sekundären Commands-Auflistung werden.

Proaktiv zeigen Befehle werden normalerweise Flyout der Befehl Balken zeigen das [Klicken](/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.click) oder [Tapped](/uwp/api/windows.ui.xaml.uielement.tapped) -Ereignis behandeln. Festlegen Sie das Flyout [ShowMode](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.showmode) **vorübergehende** oder **TransientWithDismissOnPointerMoveAway** Flyout im reduzierten Modus öffnen, ohne den Fokus

Ab Windows 10 Insider Preview Textsteuerelemente verfügen über eine **SelectionFlyout** -Eigenschaft. Wenn dieser Eigenschaft ein Flyout zuweisen, wird automatisch angezeigt, wenn Text markiert ist.

### <a name="show-commands-reactively"></a>Reaktiv Befehle anzeigen

Wenn Sie Kontextmenüs reaktiv ein Kontextmenü anzeigen, sind sekundäre Befehle angezeigt (Befehl Bar Flyout sollte erweitert werden). In diesem Fall möglicherweise Flyout Bar Befehl primäre und sekundäre Befehle oder sekundäre Befehle.

Um Befehle im Kontextmenü anzuzeigen, weisen Sie normalerweise Flyout das [ContextFlyout](/uwp/api/windows.ui.xaml.uielement.contextflyout) -Eigenschaft eines Benutzeroberflächenelements. So öffnen das Flyout vom Element erfolgt und Sie müssen nichts weiter tun.

Behandeln der Flyout (z. B. in ein [RightTapped](/uwp/api/windows.ui.xaml.uielement.righttapped) -Ereignis) mit Setzen der Flyout [ShowMode](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.showmode) **Standard** Flyout im erweiterten Modus öffnen und erhält den Eingabefokus.

> [!TIP]
> Weitere Informationen zu Optionen, wenn ein Flyout und steuern die Platzierung der Flyout anzeigen Sie [Flyout](../controls-and-patterns/dialogs-and-flyouts/flyouts.md)

## <a name="commands-and-content"></a>Befehle und Inhalt

Das CommandBarFlyout-Steuerelement verfügt über 2 Eigenschaften Sie Befehle und Inhalt hinzufügen können: [PrimaryCommands](/uwp/api/windows.ui.xaml.controls.commandbarflyout.primarycommands) und [SecondaryCommands](/uwp/api/windows.ui.xaml.controls.commandbarflyout.secondarycommands).

Befehlsleistenelemente werden standardmäßig der **PrimaryCommands**-Sammlung hinzugefügt. Diese Befehle werden in der Befehlszeile angezeigt und werden in den Modi bzw. angezeigt. Im Gegensatz zu CommandBar primäre Befehle nicht automatisch Überlauf zu sekundären Befehle und möglicherweise abgeschnitten.

Sie können auch Befehle zur **SecondaryCommands** -Auflistung hinzufügen. Sekundäre Befehle im Menü Bereich des Steuerelements angezeigt werden und werden nur im erweiterten Modus angezeigt.

### <a name="app-bar-buttons"></a>App-Leistenschaltflächen

Sie können direkt mit [AppBarButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarbutton.aspx), [AppBarToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbartogglebutton.aspx)und [AppBarSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarseparator.aspx) PrimaryCommands und SecondaryCommands auffüllen.

Die Steuerelemente für die App-Leistenschaltfläche zeichnen sich durch ein Symbol und eine Textbeschriftung aus. Diese Steuerelemente sind für die Verwendung in einer Befehlsleiste optimiert und ihre Darstellung abhängig, ob das Steuerelement der Befehlsleiste oder Überlaufmenü angezeigt wird.

- App Schaltflächen als primäre Befehle werden in der Befehlszeile mit dem Symbol angezeigt. die Beschriftung wird nicht angezeigt. Es wird empfohlen, QuickInfo mit eine Beschreibung des Befehls angezeigt wie folgt.
    ```xaml
    <AppBarButton Icon="Copy" ToolTipService.ToolTip="Copy"/>
    ```
- App Schaltflächen als sekundäre Befehle erscheinen im Menü mit der Bezeichnung und Symbol sichtbar.

### <a name="other-content"></a>Andere Inhalte

Einbinden in eine AppBarElementContainer können Sie andere Steuerelemente zu einem Befehl Bar Flyout hinzufügen. So können Sie die Steuerelemente wie [DropDownButton]() oder [SplitButton]()hinzugefügt oder Containern wie [StackPanel]() komplexe Benutzeroberflächen erstellen.

Um zu den primären oder sekundären Befehl ein Befehl Bar Flyout hinzugefügt werden, muss ein Element die [ICommandBarElement](/uwp/api/windows.ui.xaml.controls.icommandbarelement) -Schnittstelle implementieren. AppBarElementContainer ist ein Wrapper, der diese Schnittstelle implementiert, Sie ein Element zu einer Befehlsleiste hinzufügen können, auch wenn sie nicht die Schnittstelle selbst implementieren.

Hier wird ein AppBarElementContainer verwendet, ein Flyout Befehl Leiste zusätzliche Elemente hinzugefügt. Primäre Befehle zu Farben ein SplitButton hinzugefügt. Die sekundäre Befehle zu einem komplexeren Layout Zoomsteuerelemente StackPanel hinzugefügt.

> [!TIP]
> Standardmäßig Elemente für die Arbeitsfläche app möglicherweise nicht sehen in einer Befehlsleiste. Wenn Sie ein Element mit AppBarElementContainer hinzufügen, sind einige Schritte sollten Sie auf das Element andere Command Bar-Elemente entsprechen:
>
> - Standardpinsel mit [einfachen Stilen](/design/controls-and-patterns/xaml-styles#lightweight-styling) Hintergrund und Schaltflächen der app übereinstimmen Grenzen des Elements zu überschreiben.
> - Passen Sie die Größe und Position des Elements.
> - Umbrechen Sie Symbole in einer Viewbox mit einer Breite und Höhe des 16px.

> [!NOTE]
> Dieses Beispiel zeigt nur dem Befehl Bar Flyout Benutzeroberfläche es keinen Befehl implementiert, die angezeigt werden. Weitere Informationen zur Implementierung der Befehle finden Sie unter [Schaltflächen](buttons.md) und [Grundlagen Befehls](../basics/commanding-basics.md).

![Ein Befehl Bar Flyout mit einer Trennschaltfläche](images/command-bar-flyout-split-button.png)

> _Eine reduzierte Befehl Bar Flyout mit offenen SplitButton_

![Ein Befehl Bar Flyout mit komplexen Benutzeroberfläche](images/command-bar-flyout-custom-ui.png)

> _Ein Flyout expandierte Befehl Leiste mit benutzerdefinierten Zoom Benutzeroberfläche im Menü_


```xaml
<CommandBarFlyout>
    <AppBarButton Icon="Cut" ToolTipService.ToolTip="Cut"/>
    <AppBarButton Icon="Copy" ToolTipService.ToolTip="Copy"/>
    <AppBarButton Icon="Paste" ToolTipService.ToolTip="Paste"/>
    <!-- Alignment controls -->
    <AppBarElementContainer>
        <SplitButton ToolTipService.ToolTip="Alignment">
            <SplitButton.Resources>
                <!-- Override default brushes to make the SplitButton 
                     match other command bar elements. -->
                <Style TargetType="SplitButton">
                    <Setter Property="Height" Value="38"/>
                </Style>
                <SolidColorBrush x:Key="SplitButtonBackground"
                                 Color="Transparent"/>
                <SolidColorBrush x:Key="SplitButtonBackgroundPressed"
                                 Color="{ThemeResource SystemListMediumColor}"/>
                <SolidColorBrush x:Key="SplitButtonBackgroundPointerOver"
                                 Color="{ThemeResource SystemListLowColor}"/>
                <SolidColorBrush x:Key="SplitButtonBorderBrush" Color="Transparent"/>
                <SolidColorBrush x:Key="SplitButtonBorderBrushPointerOver"
                                 Color="Transparent"/>
                <SolidColorBrush x:Key="SplitButtonBorderBrushChecked"
                                 Color="Transparent"/>
            </SplitButton.Resources>
            <SplitButton.Content>
                <Viewbox Width="16" Height="16" Margin="0,2,0,0">
                    <SymbolIcon Symbol="AlignLeft"/>
                </Viewbox>
            </SplitButton.Content>
            <SplitButton.Flyout>
                <MenuFlyout>
                    <MenuFlyoutItem Icon="AlignLeft" Text="Align left"/>
                    <MenuFlyoutItem Icon="AlignCenter" Text="Center"/>
                    <MenuFlyoutItem Icon="AlignRight" Text="Align right"/>
                </MenuFlyout>
            </SplitButton.Flyout>
        </SplitButton>
    </AppBarElementContainer>
    <!-- end Alignment controls -->
    <CommandBarFlyout.SecondaryCommands>
        <!-- Zoom controls -->
        <AppBarElementContainer>
            <AppBarElementContainer.Resources>
                <!-- Override default brushes to make the Buttons 
                     match other command bar elements. -->
                <SolidColorBrush x:Key="ButtonBackground"
                                 Color="Transparent"/>
                <SolidColorBrush x:Key="ButtonBackgroundPressed"
                                 Color="{ThemeResource SystemListMediumColor}"/>
                <SolidColorBrush x:Key="ButtonBackgroundPointerOver"
                                 Color="{ThemeResource SystemListLowColor}"/>
                <SolidColorBrush x:Key="ButtonBorderBrush"
                                 Color="Transparent"/>
                <SolidColorBrush x:Key="ButtonBorderBrushPointerOver"
                                 Color="Transparent"/>
                <SolidColorBrush x:Key="ButtonBorderBrushChecked"
                                 Color="Transparent"/>
                <Style TargetType="TextBlock">
                    <Setter Property="VerticalAlignment" Value="Center"/>
                </Style>
                <Style TargetType="Button">
                    <Setter Property="Height" Value="40"/>
                    <Setter Property="Width" Value="40"/>
                </Style>
            </AppBarElementContainer.Resources>
            <Grid Margin="12,-4">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="Auto"/>
                    <ColumnDefinition Width="76"/>
                    <ColumnDefinition Width="Auto"/>
                </Grid.ColumnDefinitions>
                <Viewbox Width="16" Height="16" Margin="0,2,0,0">
                    <SymbolIcon Symbol="Zoom"/>
                </Viewbox>
                <TextBlock Text="Zoom" Margin="10,0,0,0" Grid.Column="1"/>
                <StackPanel Orientation="Horizontal" Grid.Column="2">
                    <Button ToolTipService.ToolTip="Zoom out">
                        <Viewbox Width="16" Height="16">
                            <SymbolIcon Symbol="ZoomOut"/>
                        </Viewbox>
                    </Button>
                    <TextBlock Text="50%" Width="40"
                               HorizontalTextAlignment="Center"/>
                    <Button ToolTipService.ToolTip="Zoom in">
                        <Viewbox Width="16" Height="16">
                            <SymbolIcon Symbol="ZoomIn"/>
                        </Viewbox>
                    </Button>
                </StackPanel>
            </Grid>
        </AppBarElementContainer>
        <!-- end Zoom controls -->
        <AppBarSeparator/>
        <AppBarButton Label="Undo" Icon="Undo"/>
        <AppBarButton Label="Redo" Icon="Redo"/>
        <AppBarButton Label="Select all" Icon="SelectAll"/>
    </CommandBarFlyout.SecondaryCommands>
</CommandBarFlyout>
```

## <a name="create-a-context-menu-with-secondary-commands-only"></a>Erstellen eines Kontextmenüs mit sekundären Befehle

Ein CommandBarFlyout können mit sekundären Befehlen ein [Kontextmenü](menus.md)anstelle einer MenuFlyout.

![Ein Befehl Bar Flyout mit sekundären Befehle](images/command-bar-flyout-context-menu.png)

> _Befehl Bar Flyout als Kontextmenü_

```xaml
<Grid>
    <Grid.Resources>
        <!-- A command bar flyout with only secondary commands. -->
        <CommandBarFlyout x:Name="ContextMenu">
            <CommandBarFlyout.SecondaryCommands>
                <AppBarButton Label="Copy" Icon="Copy"/>
                <AppBarButton Label="Save" Icon="Save"/>
                <AppBarButton Label="Print" Icon="Print"/>
                <AppBarSeparator />
                <AppBarButton Label="Properties"/>
            </CommandBarFlyout.SecondaryCommands>
        </CommandBarFlyout>
    </Grid.Resources>

    <Image Source="Assets/image1.png" Width="300"
           ContextFlyout="{x:Bind ContextMenu}"/>
</Grid>
```

Auch können ein CommandBarFlyout mit einem DropDownButton Sie ein Standardmenü erstellen.

![Ein Befehl Bar Flyout mit als Dropdown-Schaltfläche](images/command-bar-flyout-dropdown.png)

> _Ein Dropdown-Menü der Schaltfläche in einem Befehl Bar flyout_

```xaml
<CommandBarFlyout>
    <AppBarButton Icon="Placeholder"/>
    <AppBarElementContainer>
        <DropDownButton Content="Mail">
            <DropDownButton.Resources>
                <!-- Override default brushes to make the DropDownButton 
                     match other command bar elements. -->
                <Style TargetType="DropDownButton">
                    <Setter Property="Height" Value="38"/>
                </Style>
                <SolidColorBrush x:Key="ButtonBackground"
                                 Color="Transparent"/>
                <SolidColorBrush x:Key="ButtonBackgroundPressed"
                                 Color="{ThemeResource SystemListMediumColor}"/>
                <SolidColorBrush x:Key="ButtonBackgroundPointerOver"
                                 Color="{ThemeResource SystemListLowColor}"/>

                <SolidColorBrush x:Key="ButtonBorderBrush"
                                 Color="Transparent"/>
                <SolidColorBrush x:Key="ButtonBorderBrushPointerOver"
                                 Color="Transparent"/>
                <SolidColorBrush x:Key="ButtonBorderBrushChecked"
                                 Color="Transparent"/>
            </DropDownButton.Resources>
            <DropDownButton.Flyout>
                <CommandBarFlyout Placement="BottomEdgeAlignedLeft">
                    <CommandBarFlyout.SecondaryCommands>
                        <AppBarButton Icon="MailReply" Label="Reply"/>
                        <AppBarButton Icon="MailReplyAll" Label="Reply all"/>
                        <AppBarButton Icon="MailForward" Label="Forward"/>
                    </CommandBarFlyout.SecondaryCommands>
                </CommandBarFlyout>
            </DropDownButton.Flyout>
        </DropDownButton>
    </AppBarElementContainer>
    <AppBarButton Icon="Placeholder"/>
    <AppBarButton Icon="Placeholder"/>
</CommandBarFlyout>
```

## <a name="command-bar-flyouts-for-text-controls"></a>Befehl Bar Flyout für Text-Steuerelemente

[TextCommandBarFlyout](/uwp/api/microsoft.ui.xaml.controls.textcommandbarflyout) ist eine spezielle Befehl Bar Flyout, das Befehle zum Bearbeiten von Text enthält. Jedes Textsteuerelement wird der TextCommandBarFlyout automatisch als Kontextmenü (rechte Maustaste) oder wenn Text ausgewählt ist. Text Command Bar Flyout passt die Textauswahl nur Befehlen angezeigt.

![Ein Flyout reduzierten Text Befehl bar](images/command-bar-flyout-text-selection.png)

> _Ein Flyout Text Befehl Bar auf markierten text_

![Eine erweiterte Text Command Bar flyout](images/command-bar-flyout-text-full.png)

> _Eine erweiterte Text Command Bar flyout_


### <a name="available-commands"></a>Verfügbare Befehle

Der Tabelle werden die Befehle in einer TextCommandBarFlyout und wenn sie angezeigt werden.

| Befehl | Angezeigt. |
| ------- | -------- |
| Fett | ist das Steuerelement nicht schreibgeschützt (RichEditBox nur). |
| Kursiv | ist das Steuerelement nicht schreibgeschützt (RichEditBox nur). |
| Unterstreichen | ist das Steuerelement nicht schreibgeschützt (RichEditBox nur). |
| Rechtschreibprüfung | Wenn IsSpellCheckEnabled **Wahr** und falsch ist Text markiert. |
| Ausschneiden | Wenn das Steuerelement nicht schreibgeschützt und Text markiert. |
| Kopieren | Wenn Text ausgewählt ist. |
| Einfügen | Wenn das Steuerelement nicht schreibgeschützt und Zwischenablage Inhalt. |
| Rückgängig machen | Wenn eine Aktion, die rückgängig gemacht werden kann. |
| Alle auswählen | Wenn Text ausgewählt werden kann. |

### <a name="custom-text-command-bar-flyouts"></a>Benutzerdefinierten Text Command Bar Flyout

TextCommandBarFlyout kann nicht angepasst werden und von den einzelnen Steuerelementen Text automatisch verwaltet wird. Allerdings können Sie die Standard-TextCommandBarFlyout mit benutzerdefinierten Befehlen ersetzen.

- Standard TextCommandBarFlyout ersetzen, die auf markierten Text angezeigt wird, können erstellen Sie eine benutzerdefinierte CommandBarFlyout (oder andere Flyout) und der **SelectionFlyout** -Eigenschaft zuweisen. Wenn SelectionFlyout auf **null**festgelegt wird, werden keine Befehle auf Auswahl angezeigt.
- Standard TextCommandBarFlyout ersetzen, die im Kontextmenü angezeigt wird, weisen Sie benutzerdefinierte CommandBarFlyout oder sonstige Flyout **ContextFlyout** -Eigenschaft für ein Textfeld-Steuerelement. ContextFlyout auf **null**festgelegt wird, wird in früheren Versionen des Steuerelements angezeigte Menü-Flyout anstelle der TextCommandBarFlyout angezeigt.

## <a name="get-the-sample-code"></a>Beispielcode herunterladen

- [Beispiel eines XAML-Steuerelementekatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.
- [Beispiel für XAML-Befehle](http://go.microsoft.com/fwlink/p/?LinkId=620019)

## <a name="related-articles"></a>Verwandte Artikel

- [Befehlsdesigngrundlagen für UWP-Apps](../basics/commanding-basics.md)
- [CommandBar-Klasse](https://msdn.microsoft.com/library/windows/apps/dn279427)
