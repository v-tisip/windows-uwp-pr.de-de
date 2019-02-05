---
Description: Command bar flyouts give users inline access to your app's most common tasks.
title: Befehlsleisten-Flyout
label: Command bar flyout
template: detail.hbs
ms.date: 10/2/2018
ms.topic: article
keywords: Windows10, UWP
pm-contact: abarlow
design-contact: ksulliv
dev-contact: llongley
doc-status: Draft
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 90c86e071b0e1d2a07d7755ba23cb6418ca0022a
ms.sourcegitcommit: b975c8fc8cf0770dd73d8749733ae5636f2ee296
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2019
ms.locfileid: "9058571"
---
# <a name="command-bar-flyout"></a>Befehlsleisten-Flyout

Das Befehlsleisten-Flyout können Sie Benutzer einfachen Zugriff auf allgemeine Aufgaben bereitstellen, indem Befehle in einem schwebenden Symbolleisten im Zusammenhang mit eines Elements auf die UI-Canvas angezeigt.

![Eine erweiterte Text Befehlsleisten-flyout](images/command-bar-flyout-header.png)

> CommandBarFlyout erfordert Windows 10, Version 1809 ([SDK 17763](https://developer.microsoft.com/windows/downloads/windows-10-sdk)) oder höher, oder in der [Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).

> - **Plattform-APIs**: [CommandBarFlyout-Klasse](/uwp/api/windows.ui.xaml.controls.commandbarflyout)"," [TextCommandBarFlyout-Klasse](/uwp/api/windows.ui.xaml.controls.textcommandbarflyout)"," [AppBarButton-Klasse](/uwp/api/windows.ui.xaml.controls.appbarbutton)"," [Klasse "appbartogglebutton"](/uwp/api/windows.ui.xaml.controls.appbartogglebutton)"," [Klasse "appbarseparator"](/uwp/api/windows.ui.xaml.controls.appbarseparator)
>- **Windows-UI-Bibliothek-APIs**: [CommandBarFlyout-Klasse](/uwp/api/microsoft.ui.xaml.controls.commandbarflyout), [TextCommandBarFlyout-Klasse](/uwp/api/microsoft.ui.xaml.controls.textcommandbarflyout)

Wie [CommandBar](app-bars.md)hat CommandBarFlyout **PrimaryCommands** und **"secondarycommands"** Eigenschaften, mit denen Sie Befehle hinzufügen. Sie können entweder Auflistung, oder beide Befehle versehen. Wann und wie die primären und sekundären Befehle angezeigt werden, hängt von den Anzeigemodus.

Das Befehlsleisten-Flyout verfügt über zwei Anzeigemodi: *reduziert* und *Erweitert*.

- Im Modus "Collapsed" werden nur die primären Befehle angezeigt. Verfügt Ihr Befehlsleisten-Flyout primären und sekundären Befehle, eine "Schaltfläche" Weitere, dargestellt durch eine Ellipse \ [• • •] wird angezeigt. So kann der Benutzer Zugriff auf die sekundären Befehle von Wechsel zur erweiterten Modus zu erhalten.
- Im erweiterten Modus werden die primären und sekundären Befehle angezeigt. (Wenn das Steuerelement nur sekundäre Elemente verfügt, werden sie in einer Weise ähnelt dem MenuFlyout-Steuerelement angezeigt.)

## <a name="is-this-the-right-control"></a>Ist dies das richtige Steuerelement?

Verwenden Sie das CommandBarFlyout-Steuerelement, um eine Sammlung von Befehle für dem Benutzer, z. B. Schaltflächen und Menüelementen im Kontext eines Elements auf der app-Canvas anzeigen.

Die TextCommandBarFlyout zeigt Textbefehle im TextBlock, TextBox, RichEditBox, RichTextBlock und PasswordBox-Steuerelemente. Die Befehle sind für die aktuelle Textauswahl automatisch entsprechend konfiguriert. Verwenden Sie eine CommandBarFlyout, um die Standard-Text-Befehle für Textsteuerelemente ersetzen.

Um kontextbezogene anzeigen führen Sie die Befehle auf Listenelemente die Anleitung im [Contextual Befehle für Sammlungen und Listen](collection-commanding.md).

### <a name="commandbarflyout-vs-menuflyout"></a>CommandBarFlyout Vs MenuFlyout

Um Befehle in einem Kontextmenü anzuzeigen, können Sie CommandBarFlyout oder MenuFlyout verwenden. CommandBarFlyout wird empfohlen, da es mehr Funktionen als MenuFlyout bereitstellt. Sie können CommandBarFlyout mit nur sekundäre Befehle verwenden, erhalten das Verhalten und von einem MenuFlyout, oder verwenden Sie das vollständige Befehlsleisten-Flyout mit primären und sekundären Befehlen.

> Verwandte Informationen finden Sie unter [Flyouts](../controls-and-patterns/dialogs-and-flyouts/flyouts.md), [Menüs und Kontextmenüs](menus.md)und [Befehlsleisten](app-bars.md).

## <a name="examples"></a>Beispiele

<table>
<th align="left">XAML-Steuerelementekatalog<th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p>Wenn Sie die <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> -app installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/CommandBarFlyout">die app zu öffnen und finden Sie unter der CommandBarFlyout in Aktion zu sehen</a>.</p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</a></li>
    <li><a href="https://github.com/Microsoft/Xaml-Controls-Gallery">Erwerben Sie den Quellcode (GitHub)</a></li>
    </ul>
</td>
</tr>
</table>

## <a name="proactive-vs-reactive-invocation"></a>Im Vergleich zu Zeiten Aufruf proaktive

Es gibt in der Regel zwei Möglichkeiten zum Aufrufen eines Flyout oder das Menü ", die mit einem Element auf die UI-Canvas zugeordnet ist: _proaktive aufrufen_ und _reaktive Aufruf_.

Unter proaktive Aufruf werden Befehle automatisch angezeigt, wenn der Benutzer mit dem Element interagiert, die die Befehle zugeordnet sind. Beispielsweise können Text Formatierungsbefehle eingeblendet, wählt der Benutzer Text in einem Textfeld. In diesem Fall wird das Befehlsleisten-Flyout nicht den Fokus erhalten. Stattdessen zeigt sie geeignete Befehle nahe das Element, dem mit der Benutzer interagiert. Wenn der Benutzer mit den Befehlen interagieren nicht, werden sie geschlossen.

In Zeiten Aufruf werden Befehle in Reaktion auf eine explizite Benutzeraktion angezeigt, die Befehle anfordern. Beispiel: eine mit der rechten Maustaste. Dies entspricht dem herkömmliche-Konzept von ein [Kontextmenü](menus.md).

Sie können die Möglichkeit, oder sogar eine Mischung aus den beiden CommandBarFlyout verwenden.

## <a name="create-a-command-bar-flyout"></a>Erstellen Sie eine Befehlsleisten-flyout

Dieses Beispiel zeigt, wie Sie eine Befehlsleisten-Flyout erstellt und reaktiv sowohl proaktiv. Wenn das Bild getippt wird, wird das Flyout im Modus "Collapsed" angezeigt. Wenn als Kontextmenü angezeigt wird, wird das Flyout im erweiterten Modus angezeigt. In beiden Fällen kann der Benutzer erweitern oder reduzieren das Flyout, nachdem er geöffnet wird.

![Beispiel für eine "Collapsed" Befehlsleisten-flyout](images/command-bar-flyout-img-collapsed.png)

> _Eine "Collapsed" Befehlsleisten-flyout_

![Beispiel für eine erweiterte Befehlsleisten-flyout](images/command-bar-flyout-img-expanded.png)

> _Eine erweiterte Befehlsleisten-flyout_

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

### <a name="show-commands-proactively"></a>Befehle proaktiv anzeigen

Wenn Sie proaktiv Kontextbefehlen anzeigen, sollte nur die primären Befehle in der Standardeinstellung angezeigt werden (das Befehlsleisten-Flyout sollte reduziert werden). Platzieren Sie die wichtigsten Befehle in der Auflistung der primäre Befehle und weitere Befehle, die normalerweise in einem Kontextmenü in die sekundären Befehle Auflistung würde.

Um Befehle proaktiv anzuzeigen, behandeln Sie in der Regel das Ereignis [Klicken](/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.click) oder [Tapped](/uwp/api/windows.ui.xaml.uielement.tapped) , um die Befehlsleisten-Flyout anzuzeigen. Legen Sie das Flyout [ShowMode](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.showmode) **vorübergehende** oder **TransientWithDismissOnPointerMoveAway** , um das Flyout im Modus "Collapsed" zu öffnen, ohne den Fokus fest.

Ab Windows 10 Insider Preview, Text-Steuerelemente verfügen über eine **SelectionFlyout** -Eigenschaft. Wenn Sie diese Eigenschaft ein Flyout zuordnen, wird er automatisch angezeigt, wenn Text markiert ist.

### <a name="show-commands-reactively"></a>Befehle reaktiv anzeigen

Wenn Sie Kontextbefehlen reaktiv, als Kontextmenü angezeigt wird, werden die sekundären Befehle standardmäßig angezeigt (das Befehlsleisten-Flyout sollte erweitert werden). In diesem Fall möglicherweise das Befehlsleisten-Flyout primären und sekundären Befehle oder nur sekundäre Befehle.

Um Befehle in einem Kontextmenü anzuzeigen, weisen Sie in der Regel das Flyout der [ContextFlyout](/uwp/api/windows.ui.xaml.uielement.contextflyout) -Eigenschaft eines Benutzeroberflächenelements. Auf diese Weise wird das Flyout Öffnen des Elements behandelt, und Sie müssen nichts weiter tun.

Behandelt das Flyout (z. B. auf ein Ereignis [RightTapped](/uwp/api/windows.ui.xaml.uielement.righttapped) ) angezeigt werden, legen Sie das Flyout [ShowMode](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.showmode) auf **Standard** in das Flyout im erweiterten Modus zu öffnen, und weisen Sie ihm den Fokus.

> [!TIP]
> Weitere Informationen zu den Optionen ein Flyout und Steuern der Platzierung der das Flyout angezeigt finden Sie unter [Flyouts](../controls-and-patterns/dialogs-and-flyouts/flyouts.md).

## <a name="commands-and-content"></a>Befehle und Inhalt

Das CommandBarFlyout-Steuerelement verfügt über 2 Eigenschaften Sie Befehle und Inhalte hinzufügen können: [PrimaryCommands](/uwp/api/windows.ui.xaml.controls.commandbarflyout.primarycommands) und ["secondarycommands"](/uwp/api/windows.ui.xaml.controls.commandbarflyout.secondarycommands).

Befehlsleistenelemente werden standardmäßig der **PrimaryCommands**-Sammlung hinzugefügt. Diese Befehle werden angezeigt, in der Befehlsleiste und sowohl die "Collapsed" auch im erweiterten Modus sichtbar sind. Im Gegensatz zu CommandBar primäre Befehle nicht automatisch Überlauf auf sekundäre Befehle und möglicherweise abgeschnitten.

Sie können auch Befehle zur Auflistung **"secondarycommands"** hinzufügen. Sekundäre Befehle werden im Menü Teil des Steuerelements angezeigt und sind nur im erweiterten Modus sichtbar.

### <a name="app-bar-buttons"></a>App-Leistenschaltflächen

Sie können die PrimaryCommands und "secondarycommands" direkt mit [AppBarButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarbutton.aspx), [AppBarToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbartogglebutton.aspx)und [AppBarSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarseparator.aspx) Steuerelementen auffüllen.

Die Steuerelemente für die App-Leistenschaltfläche zeichnen sich durch ein Symbol und eine Textbeschriftung aus. Diese Steuerelemente sind für die Verwendung in Befehlsleisten optimiert, und ihr Erscheinungsbild ändert, je nachdem, ob das Steuerelement in der Befehlsleiste oder im Überlaufmenü angezeigt wird.

- App-Leistenschaltflächen als primäre Befehle verwendet werden in der Befehlsleiste mit nur ihre Symbol angezeigt. die Beschriftung wird nicht angezeigt. Es wird empfohlen, dass Sie eine QuickInfo verwenden, um eine Beschreibung des Befehls anzuzeigen wie hier gezeigt.
    ```xaml
    <AppBarButton Icon="Copy" ToolTipService.ToolTip="Copy"/>
    ```
- App-Leistenschaltflächen als sekundäre Befehle verwendet werden im Menü mit der Bezeichnung und Symbol sichtbar angezeigt.

### <a name="other-content"></a>Andere Inhalte

Sie können eine Befehlsleisten-Flyout eine AppBarElementContainer umschließen andere Steuerelemente hinzufügen. Auf diese Weise können Sie die Steuerelemente wie [DropDownButton](buttons.md) oder [SplitButton](buttons.md)hinzugefügt oder Containern wie [StackPanel](buttons.md) um komplexere Benutzeroberfläche zu erstellen.

Um den primären oder sekundären Befehl Sammlungen von einem Befehlsleisten-Flyout hinzugefügt werden, muss ein Element die [ICommandBarElement](/uwp/api/windows.ui.xaml.controls.icommandbarelement) -Schnittstelle implementieren. AppBarElementContainer ist ein Wrapper, der diese Schnittstelle implementiert, sodass Sie ein Element zu einer Befehlsleiste hinzufügen können, auch wenn es nicht die Schnittstelle selbst implementiert.

Hier wird ein AppBarElementContainer verwendet, um zusätzliche Elemente zu einer Befehlsleisten-Flyout hinzuzufügen. Die primären Befehle, um die Auswahl an Farben ermöglichen eine SplitButton hinzugefügt. StackPanel wird die sekundären Befehle, um ein komplexeres Layout für Zoomsteuerelemente ermöglichen hinzugefügt.

> [!TIP]
> Standardmäßig Elemente für die app-Canvas zur möglicherweise nicht sehen in einer Befehlsleiste. Wenn Sie ein Element, AppBarElementContainer hinzufügen, gibt es jedoch einige Schritte, die Sie ausführen sollten, um sicherzustellen, das Element, das andere Element auf der Befehl entsprechen:
>
> - Überschreiben Sie die Standardpinsel mit [einfache Formatierung](/windows/uwp/design/controls-and-patterns/xaml-styles#lightweight-styling) des Elements Hintergrund und Rahmen Schaltflächen auf der app entsprechen.
> - Anpassen der Größe und Position des Elements.
> - Umschließen Sie Symbole in einer Viewbox mit einer Breite und Höhe des 16px.

> [!NOTE]
> Dieses Beispiel zeigt nur dem Befehlsleisten-Flyout UI, es keine Befehle implementiert, die angezeigt werden. Weitere Informationen zur Implementierung der Befehle finden Sie unter [Schaltflächen](buttons.md) und [befehlsdesigngrundlagen](../basics/commanding-basics.md).

![Eine Befehlsleisten-Flyout mit einer Split-Schaltfläche](images/command-bar-flyout-split-button.png)

> _Eine "Collapsed" Befehlsleisten-Flyout mit einer offenen SplitButton_

![Eine komplexe Benutzeroberfläche Befehlsleisten-flyout](images/command-bar-flyout-custom-ui.png)

> _Eine erweiterte Befehlsleisten-Flyout mit benutzerdefinierten Zoom UI im Menü ""_


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

## <a name="create-a-context-menu-with-secondary-commands-only"></a>Erstellen Sie ein Kontextmenü mit nur sekundäre Befehle

Sie können eine CommandBarFlyout mit nur sekundäre Befehle als [Kontextmenü](menus.md), anstelle einer MenuFlyout verwenden.

![Eine Befehlsleisten-Flyout mit nur sekundäre Befehle](images/command-bar-flyout-context-menu.png)

> _Befehlsleisten-Flyout als Kontextmenü_

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

Sie können auch eine CommandBarFlyout mit einem DropDownButton verwenden, zum Erstellen eines Standardmenüs.

![Eine Befehlsleisten-Flyout mit als ein Dropdown-Menü "Schaltfläche"](images/command-bar-flyout-dropdown.png)

> _Ein Dropdown-Menü "Schaltfläche" in einem Befehlsleisten-flyout_

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

## <a name="command-bar-flyouts-for-text-controls"></a>Flyouts auf einer Befehlsleiste für Text-Steuerelemente

Die [TextCommandBarFlyout](/uwp/api/microsoft.ui.xaml.controls.textcommandbarflyout) ist eine spezielle Befehlsleisten-Flyout, die Befehle zum Bearbeiten von Text enthält. Jedes Textsteuerelement zeigt die TextCommandBarFlyout automatisch als Kontextmenü (Rechtsklick), oder wenn Text markiert ist. Das Text Befehlsleisten-Flyout passt sich die Textauswahl nur relevante Befehle angezeigt.

![Eine "Collapsed" Text Befehlsleisten-flyout](images/command-bar-flyout-text-selection.png)

> _Ein Text Befehlsleisten-Flyout auf Textauswahl_

![Eine erweiterte Text Befehlsleisten-flyout](images/command-bar-flyout-text-full.png)

> _Eine erweiterte Text Befehlsleisten-flyout_


### <a name="available-commands"></a>Verfügbaren Befehle

Diese Tabelle zeigt die Befehle in einer TextCommandBarFlyout, und wenn diese angezeigt werden.

| Befehl | Dargestellt … |
| ------- | -------- |
| Fett | Wenn das Steuerelement keine schreibgeschützt (RichEditBox nur) ist. |
| Kursiv | Wenn das Steuerelement keine schreibgeschützt (RichEditBox nur) ist. |
| Unterstreichen | Wenn das Steuerelement keine schreibgeschützt (RichEditBox nur) ist. |
| Nachweis von Manipulation | Wenn IsSpellCheckEnabled **"true"** und falsch geschrieben wird Text ausgewählt. |
| Ausschneiden | Wenn das Textsteuerelement ist nicht schreibgeschützt, und Text ausgewählt ist. |
| Kopieren | Wenn Text ausgewählt ist. |
| Einfügen | Wenn das Textsteuerelement ist nicht schreibgeschützt, und die Zwischenablage Inhalt ist. |
| Rückgängig machen | Wenn eine Aktion, die rückgängig gemacht werden können. |
| Alle auswählen | Wenn der Text ausgewählt werden können. |

### <a name="custom-text-command-bar-flyouts"></a>Benutzerdefinierter Text, der Flyouts auf einer Befehlsleiste

TextCommandBarFlyout kann nicht angepasst werden, und von jedes Textsteuerelement automatisch verwaltet wird. Allerdings können Sie die standardmäßige TextCommandBarFlyout mit benutzerdefinierten Befehlen ersetzen.

- Um die standardmäßige TextCommandBarFlyout ersetzen, die auf Textauswahl angezeigt wird, können Sie erstellen Sie eine benutzerdefinierte CommandBarFlyout (oder andere Flyout) und weisen sie die **SelectionFlyout** -Eigenschaft. Wenn Sie SelectionFlyout auf **null**festlegen, werden keine Befehle auf Auswahl angezeigt.
- Um die Standard-TextCommandBarFlyout ersetzen, die im Kontextmenü angezeigt wird, weisen Sie eine benutzerdefinierte CommandBarFlyout (oder andere Flyout-Typ) für die **ContextFlyout** -Eigenschaft für ein Text-Steuerelement. Wenn Sie ContextFlyout auf **null**festgelegt, wird das Flyout "Menü" angezeigt, die in früheren Versionen des Textsteuerelements anstelle der TextCommandBarFlyout angezeigt.

## <a name="get-the-sample-code"></a>Beispielcode herunterladen

- [Beispiel eines XAML-Steuerelementekatalogs](https://github.com/Microsoft/Xaml-Controls-Gallery) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.
- [Beispiel für XAML-Befehle](https://go.microsoft.com/fwlink/p/?LinkId=620019)

## <a name="related-articles"></a>Verwandte Artikel

- [Befehlsdesigngrundlagen für UWP-Apps](../basics/commanding-basics.md)
- [CommandBar-Klasse](https://msdn.microsoft.com/library/windows/apps/dn279427)
