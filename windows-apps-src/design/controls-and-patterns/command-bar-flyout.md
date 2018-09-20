---
author: jwmsft
Description: Command bar flyouts give users inline access to your app's most common tasks.
title: Befehlsleiste flyout
label: Command bar flyout
template: detail.hbs
ms.author: jimwalk
ms.date: 07/19/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
pm-contact: abarlow
design-contact: ksulliv
dev-contact: llongley
doc-status: Draft
ms.localizationpriority: medium
ms.openlocfilehash: ec532749fc2dacfc56e80ee2830da36f71c75b2f
ms.sourcegitcommit: 4f6dc806229a8226894c55ceb6d6eab391ec8ab6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2018
ms.locfileid: "4086357"
---
# <a name="command-bar-flyout"></a>Befehlsleiste flyout

> [!IMPORTANT]
> In diesem Artikel werden Funktionen beschrieben, die noch nicht veröffentlicht wurden und vor der kommerziellen Freigabe evtl. geändert werden. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen. Preview-Funktionen müssen die [neuesten Windows 10 Insider Preview-Build und SDK](https://insider.windows.com/for-developers/) oder der [Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).

Flyout der Befehl-Leiste können Sie Benutzer einfacher Zugriff auf allgemeine Aufgaben bereitstellen, indem Befehle in einem schwebenden Symbolleisten im Zusammenhang mit eines Elements auf die UI-Canvas angezeigt.

![Eine erweiterte Text Befehlsleiste-flyout](images/command-bar-flyout-text-full.png)

> Verwandte Informationen finden Sie unter [Flyouts](../controls-and-patterns/dialogs-and-flyouts/flyouts.md), [Menüs und Kontextmenüs](menus.md)und [Befehlsleisten](app-bars.md).

Wie [CommandBar](app-bars.md)hat CommandBarFlyout **PrimaryCommands** und **"secondarycommands"** Eigenschaften, mit denen Sie Befehle hinzufügen. Sie können entweder Sammlung oder beide Befehle versehen. Wann und wie die primären und sekundären Befehle angezeigt werden, hängt von den Anzeigemodus.

Das Befehlsleiste Flyout verfügt über zwei Anzeigemodi: *reduziert* und *Erweitert*.

- Im Modus "Collapsed" werden nur die primären Befehle angezeigt. Hat der Befehlsleiste Flyout primäre und sekundäre Befehle, eine "Schaltfläche" Weitere, dargestellt durch Auslassungspunkte \ [• • •] wird angezeigt. So kann der Benutzer Zugriff auf die sekundären Befehle zu erhalten, indem Übergang zum erweiterten Modus.
- Im erweiterten Modus werden die primären und sekundären Befehle angezeigt. (Wenn das Steuerelement nur sekundäre Elemente verfügt, werden sie in einer Weise ähnelt dem MenuFlyout-Steuerelement angezeigt.)

| **Abrufen der Windows-UI-Bibliothek** |
| - |
| Dieses Steuerelement ist Bestandteil der Windows-UI-Bibliothek, NuGet-Paket, das neue Steuerelemente und UI-Features für UWP-apps enthält. Weitere Informationen, einschließlich installationsanweisungen finden Sie die [Übersicht über die Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/). |

| **Plattform-APIs** | **Windows-UI-Bibliothek APIs** |
| - | - |
| [CommandBarFlyout-Klasse](/uwp/api/windows.ui.xaml.controls.commandbarflyout)"," [TextCommandBarFlyout Klasse](/uwp/api/windows.ui.xaml.controls.textcommandbarflyout)"," [AppBarButton-Klasse](/uwp/api/windows.ui.xaml.controls.appbarbutton)"," [Klasse "appbartogglebutton"](/uwp/api/windows.ui.xaml.controls.appbartogglebutton)"," [Klasse "appbarseparator"](/uwp/api/windows.ui.xaml.controls.appbarseparator) | [CommandBarFlyout-Klasse](/uwp/api/microsoft.ui.xaml.controls.commandbarflyout), [TextCommandBarFlyout-Klasse](/uwp/api/microsoft.ui.xaml.controls.textcommandbarflyout) |

## <a name="is-this-the-right-control"></a>Ist dies das richtige Steuerelement?

Verwenden Sie das CommandBarFlyout-Steuerelement, um eine Sammlung von Befehle für dem Benutzer, z. B. Schaltflächen und Menüelementen im Kontext eines Elements auf der app-Canvas anzeigen.

Die TextCommandBarFlyout zeigt Textbefehle im TextBlock, TextBox, RichEditBox, RichTextBlock und PasswordBox-Steuerelemente. Die Befehle sind für die aktuelle Textauswahl automatisch entsprechend konfiguriert. Verwenden Sie eine CommandBarFlyout, um die Standard-Text-Befehle für Textsteuerelemente ersetzen.

Um kontextbezogene anzeigen führen Sie die Befehle auf Listenelemente die Anleitung im [Contextual Befehle für Sammlungen und Listen](collection-commanding.md).

### <a name="commandbarflyout-vs-menuflyout"></a>CommandBarFlyout Vs MenuFlyout

Um Befehle in einem Kontextmenü anzuzeigen, können Sie CommandBarFlyout oder MenuFlyout verwenden. CommandBarFlyout wird empfohlen, da sie mehr Funktionen als MenuFlyout enthält. Sie können CommandBarFlyout mit nur sekundäre Befehle verwenden, um den erhalten und von einem MenuFlyout aussehen, oder verwenden das vollständige Befehlsleiste Flyout mit primären und sekundären Befehlen.

## <a name="examples"></a>Beispiele

<table>
<th align="left">XAML-Steuerelementekatalog<th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p>Wenn Sie die <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> -app installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/CommandBarFlyout">die app zu öffnen und finden Sie unter der CommandBarFlyout in Aktion zu sehen</a>.</p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics">Erwerben Sie den Quellcode (GitHub)</a></li>
    </ul>
</td>
</tr>
</table>

## <a name="proactive-vs-reactive-invocation"></a>Im Vergleich zu Zeiten Aufruf proaktive

Es gibt in der Regel zwei Möglichkeiten zum Aufrufen eines Flyout oder das Menü, die ein Element auf Ihre UI-Canvas zugeordnet ist: _proaktive aufrufen_ und _reaktive Aufruf_.

Proaktive Aufruf werden Befehle automatisch angezeigt, wenn der Benutzer mit dem Element interagiert, die die Befehle zugeordnet werden. Beispielsweise möglicherweise Text Formatierungsbefehle angezeigt werden, wenn der Benutzer Text in einem Textfeld auswählt. In diesem Fall wird das Befehlsleiste Flyout nicht den Fokus erhalten. Stattdessen zeigt sie geeignete Befehle nahe dem Element, dem mit der Benutzer interagiert. Wenn der Benutzer mit den Befehlen interagieren nicht, werden sie geschlossen.

In Zeiten Aufruf werden Befehle in Reaktion auf eine explizite Benutzeraktion angezeigt, um die Befehle anzufordern. Beispiel: eine mit der rechten Maustaste. Dies entspricht das herkömmliche Konzept der ein [Kontextmenü](menus.md).

Sie können die CommandBarFlyout in Weise oder sogar eine Mischung aus den beiden verwenden.

## <a name="create-a-command-bar-flyout"></a>Erstellen Sie ein Befehlsleiste-flyout

> **Vorschau**: CommandBarFlyout erfordert die [neuesten Windows 10 Insider Preview-Build und SDK](https://insider.windows.com/for-developers/) oder der [Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).

Dieses Beispiel zeigt, wie Sie ein Befehlsleiste Flyout erstellt und sowohl proaktiv und reaktiv. Wenn das Bild getippt wird, wird das Flyout im Modus "Collapsed" angezeigt. Wenn als Kontextmenü angezeigt wird, wird das Flyout im erweiterten Modus angezeigt. In beiden Fällen kann der Benutzer erweitern oder reduzieren das Flyout, nachdem er geöffnet wird.

:::row:::
    :::column:::
        Ein "Collapsed" Befehlsleiste-flyout<br/>
        !["Collapsed" Befehlsleiste Flyout-Beispiel](images/command-bar-flyout-img-collapsed.png)
    :::column-end:::
    :::column:::
        Eine erweiterte Befehlsleiste-flyout<br/>
        ![Beispiel für eine erweiterte Befehlsleiste-flyout](images/command-bar-flyout-img-expanded.png)
    :::column-end:::
:::row-end:::

```xaml
<Grid>
    <Grid.Resources>
        <CommandBarFlyout x:Name="ImageCommandsFlyout">
            <AppBarButton Icon="OutlineStar" ToolTipService.ToolTip="Favorite"/>
            <AppBarButton Icon="Copy" ToolTipService.ToolTip="Copy"/>
            <AppBarButton Icon="Share" ToolTipService.ToolTip="Share"/>
            <CommandBarFlyout.SecondaryCommands>
                <AppBarButton Label="Rotate" Icon="Rotate"/>
                <AppBarButton Label="Delete" Icon="Delete"/>
            </CommandBarFlyout.SecondaryCommands>
        </CommandBarFlyout>
    </Grid.Resources>

    <Image Source="Assets/licorice.png" Width="300"
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

Wenn Sie proaktiv Kontextbefehlen anzeigen, sollte nur die primären Befehle in der Standardeinstellung angezeigt werden (die Leiste-Flyout der Befehl sollte reduziert werden). Platzieren Sie die wichtigsten Befehle in der Auflistung der primäre Befehle und weitere Befehle, die normalerweise in einem Kontextmenü in die sekundären Befehle Auflistung würde.

Zum Einblenden von Befehlen proaktiv behandeln Sie in der Regel das [Klicken](/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.click) oder [Tapped](/uwp/api/windows.ui.xaml.uielement.tapped) -Ereignis, um das Befehlsleiste Flyout anzuzeigen. Legen Sie das Flyout [ShowMode](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.showmode) **vorübergehende** oder **TransientWithDismissOnPointerMoveAway** , um das Flyout im Modus "Collapsed" zu öffnen, ohne den Fokus fest.

Ab Windows 10 Insider Preview, Textsteuerelemente verfügen über eine **SelectionFlyout** -Eigenschaft. Wenn Sie diese Eigenschaft ein Flyout zuordnen, wird er automatisch angezeigt, wenn Text markiert ist.

### <a name="show-commands-reactively"></a>Befehle reaktiv anzeigen

Wenn Sie Kontextbefehlen reaktiv als Kontextmenü angezeigt wird, werden die sekundären Befehle standardmäßig angezeigt (die Leiste-Flyout der Befehl sollte erweitert werden). In diesem Fall wird möglicherweise das Befehlsleiste Flyout primären und sekundären Befehlen oder nur sekundäre Befehle.

Um Befehle in einem Kontextmenü anzuzeigen, weisen Sie in der Regel das Flyout [ContextFlyout](/uwp/api/windows.ui.xaml.uielement.contextflyout) -Eigenschaft eines Benutzeroberflächenelements. Auf diese Weise wird das Flyout Öffnen des Elements behandelt, und Sie müssen nichts weiter tun.

Legen Sie das Flyout (z. B. auf ein Ereignis [RightTapped](/uwp/api/windows.ui.xaml.uielement.righttapped) ) mit behandelt werden, die das Flyout [ShowMode](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.showmode) in **Standard** , öffnen Sie das Flyout im erweiterten Modus und weisen Sie ihm den Fokus.

> [!TIP]
> Weitere Informationen zu den Optionen ein Flyout und Steuerung des Platzierung der das Flyout angezeigt finden Sie unter [Flyouts](../controls-and-patterns/dialogs-and-flyouts/flyouts.md).

## <a name="commands-and-content"></a>Befehle und Inhalt

Das CommandBarFlyout-Steuerelement verfügt über 2 Eigenschaften Sie Befehle und Inhalte hinzufügen können: [PrimaryCommands](/uwp/api/windows.ui.xaml.controls.commandbarflyout.primarycommands) und ["secondarycommands"](/uwp/api/windows.ui.xaml.controls.commandbarflyout.secondarycommands).

Befehlsleistenelemente werden standardmäßig der **PrimaryCommands**-Sammlung hinzugefügt. Diese Befehle werden angezeigt, in der Befehlsleiste und werden in den Modi "Collapsed" und erweiterten angezeigt. Im Gegensatz zu CommandBar primäre Befehle nicht automatisch Überlauf auf sekundäre Befehle und möglicherweise abgeschnitten.

Sie können auch Befehle zur Auflistung **"secondarycommands"** hinzufügen. Sekundäre Befehle werden im Menü Teil des Steuerelements angezeigt und werden nur im erweiterten Modus angezeigt.

### <a name="app-bar-buttons"></a>App-Leistenschaltflächen

Sie können die PrimaryCommands und "secondarycommands" direkt mit Steuerelementen [AppBarButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarbutton.aspx), [AppBarToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbartogglebutton.aspx)und [AppBarSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarseparator.aspx) auffüllen.

Die Steuerelemente für die App-Leistenschaltfläche zeichnen sich durch ein Symbol und eine Textbeschriftung aus. Diese Steuerelemente sind für die Verwendung in Befehlsleisten optimiert, und ihr Erscheinungsbild ändert, je nachdem, ob das Steuerelement in der Befehlsleiste oder im Überlaufmenü angezeigt wird.

- Als primäre Befehle verwendete Schaltflächen werden in der Befehlsleiste mit nur ihre Symbol angezeigt. die Beschriftung wird nicht angezeigt. Es wird empfohlen, dass Sie eine QuickInfo verwenden, um einen beschreibenden Text für den Befehl anzuzeigen wie hier gezeigt.
    ```xaml
    <AppBarButton Icon="Copy" ToolTipService.ToolTip="Copy"/>
    ```
- Schaltflächen als sekundäre Befehle verwendet werden im Menü mit der Bezeichnung und die Symbol sichtbar angezeigt.

### <a name="other-content"></a>Andere Inhalte

Sie können ein Befehlsleiste Flyout eine AppBarElementContainer umschließen andere Steuerelemente hinzufügen. So können Sie das Hinzufügen von Steuerelementen wie [DropDownButton]() oder [SplitButton]()oder Hinzufügen von Containern wie [StackPanel]() um komplexere Benutzeroberfläche zu erstellen.

> [!NOTE]
> Um die primären oder sekundären Befehl Sammlungen Befehlsleiste Flyout hinzugefügt werden, muss ein Element die [ICommandBarElement](/uwp/api/windows.ui.xaml.controls.icommandbarelement) -Schnittstelle implementieren. AppBarElementContainer ist ein Wrapper, der diese Schnittstelle implementiert, sodass Sie ein Element zu einer Befehlsleiste hinzufügen können, auch wenn es nicht die Schnittstelle selbst implementiert.

Hier wird ein AppBarElementContainer verwendet, um zusätzliche Elemente ein Befehlsleiste Flyout hinzufügen. Die primären Befehle, um die Auswahl an Farben ermöglichen eine SplitButton hinzugefügt. StackPanel wird die sekundären Befehle ein komplexeres Layouts für Zoomsteuerelemente zulassen hinzugefügt.

> [!NOTE]
> Dieses Beispiel zeigt nur dem Befehlsleiste Flyout UI, es keine Befehle implementiert, die angezeigt werden. Weitere Informationen zur Implementierung der Befehle finden Sie [Schaltflächen](buttons.md) und [befehlsdesigngrundlagen](../basics/commanding-basics.md).

:::row:::
    :::column:::
        Ein "Collapsed" Befehlsleiste Flyout mit einer offenen SplitButton<br/>
        ![Ein Befehlsleiste Flyout mit einer Split-Schaltfläche](images/command-bar-flyout-split-button.png)
    :::column-end:::
    :::column:::
        Eine erweiterte Befehlsleiste Flyout mit benutzerdefinierten Zoom UI im Menü ""<br/>
        ![Ein Befehlsleiste Flyout mit komplexen UI](images/command-bar-flyout-complex-ui.png)
    :::column-end:::
:::row-end:::

```xaml
<CommandBarFlyout>
    <AppBarButton Icon="Cut" ToolTipService.ToolTip="Cut"/>
    <AppBarButton Icon="Copy" ToolTipService.ToolTip="Copy"/>
    <AppBarButton Icon="Paste" ToolTipService.ToolTip="Paste"/>
    <!-- Color controls -->
    <AppBarElementContainer>
        <SplitButton Height="Auto" Margin="0,4,0,0"
                     ToolTipService.ToolTip="Colors"
                     Background="{ThemeResource AppBarItemBackgroundThemeBrush}">
            <SplitButton.Content>
                <Rectangle Width="20" Height="20">
                    <Rectangle.Fill>
                        <SolidColorBrush Color="Red"/>
                    </Rectangle.Fill>
                </Rectangle>
            </SplitButton.Content>
            <SplitButton.Flyout>
                <MenuFlyout>
                    <MenuFlyoutItem Text="Red"/>
                    <MenuFlyoutItem Text="Yellow"/>
                    <MenuFlyoutItem Text="Green"/>
                    <MenuFlyoutItem Text="Blue"/>
                </MenuFlyout>
            </SplitButton.Flyout>
        </SplitButton>
    </AppBarElementContainer>
    <!-- end Color controls -->
    <CommandBarFlyout.SecondaryCommands>
        <!-- Zoom controls -->
        <AppBarElementContainer>
            <AppBarElementContainer.Resources>
                <Style TargetType="Button">
                    <Setter Property="Background"
                            Value="{ThemeResource AppBarItemBackgroundThemeBrush}"/>
                </Style>
                <Style TargetType="TextBlock">
                    <Setter Property="VerticalAlignment" Value="Center"/>
                </Style>
            </AppBarElementContainer.Resources>
            <Grid Margin="12,0">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="86"/>
                    <ColumnDefinition Width="Auto"/>
                </Grid.ColumnDefinitions>
                <TextBlock Text="Zoom"/>
                <StackPanel Orientation="Horizontal" Grid.Column="1">
                    <Button>
                        <SymbolIcon Symbol="Remove"/>
                    </Button>
                    <TextBlock Text="50%" Width="40"
                               HorizontalTextAlignment="Center"/>
                    <Button>
                        <SymbolIcon Symbol="Add"/>
                    </Button>
                </StackPanel>
            </Grid>
        </AppBarElementContainer>
        <!-- end Zoom controls -->
        <AppBarSeparator/>
        <AppBarButton Label="Undo" Icon="Undo"/>
        <AppBarButton Label="Redo" Icon="Redo"/>
        <AppBarButton Label="Select all"/>
    </CommandBarFlyout.SecondaryCommands>
</CommandBarFlyout>
```

## <a name="create-a-context-menu-with-secondary-commands-only"></a>Erstellen Sie ein Kontextmenü mit nur sekundäre Befehle

Sie können eine CommandBarFlyout mit nur sekundäre Befehle als [Kontextmenü](menus.md), anstelle einer MenuFlyout verwenden.

![Ein Befehlsleiste Flyout mit nur sekundäre Befehle](images/command-bar-flyout-context-menu.png)

```xaml
<Grid>
    <Grid.Resources>
        <!-- A command bar flyout with only secondary commands. -->
        <CommandBarFlyout x:Name="ContextMenu">
            <CommandBarFlyout.SecondaryCommands>
                <AppBarButton Label="Pin" Icon="Pin"/>
                <AppBarButton Label="Unpin" Icon="UnPin"/>
                <AppBarButton Label="Copy" Icon="Copy"/>
                <AppBarSeparator />
                <AppBarButton Label="Properties"/>
            </CommandBarFlyout.SecondaryCommands>
        </CommandBarFlyout>
    </Grid.Resources>

    <Image Source="Assets/licorice.png" Width="300"
           ContextFlyout="{x:Bind ContextMenu}"/>
</Grid>
```

Sie können auch eine CommandBarFlyout mit einem DropDownButton verwenden, zum Erstellen eines Standardmenüs.

![Ein Befehlsleiste Flyout mit als ein Dropdown-Menü "Schaltfläche"](images/command-bar-flyout-button-menu.png)

```xaml
<DropDownButton Content="Mail">
    <DropDownButton.Flyout>
        <CommandBarFlyout Placement="BottomEdgeAlignedLeft">
            <CommandBarFlyout.SecondaryCommands>
                <AppBarButton Icon="MailForward" Label="Forward"/>
                <AppBarButton Icon="MailReply" Label="Reply"/>
                <AppBarButton Icon="MailReplyAll" Label="Reply all"/>
            </CommandBarFlyout.SecondaryCommands>
        </CommandBarFlyout>
    </DropDownButton.Flyout>
</DropDownButton>
```

## <a name="command-bar-flyouts-for-text-controls"></a>Flyouts auf einer Befehlsleiste für Textsteuerelemente

Die [TextCommandBarFlyout](/uwp/api/microsoft.ui.xaml.controls.textcommandbarflyout) ist ein spezielles Befehlsleiste Flyout, die Befehle zum Bearbeiten von Text enthält. Jedes Textsteuerelement zeigt die TextCommandBarFlyout automatisch als Kontextmenü (Rechtsklick), oder wenn Text markiert ist. Die Leiste-Flyout der Text-Befehl passt sich die Textauswahl nur relevante Befehle angezeigt.

:::row:::
    :::column:::
        Ein Flyout Text Befehlsleiste, auf die Textauswahl<br/>
        ![Ein reduzierter Text Befehlsleiste-flyout](images/command-bar-flyout-text-selection.png)
    :::column-end:::
    :::column:::
        Eine erweiterte Text Befehlsleiste-flyout<br/>
        ![Eine erweiterte Text Befehlsleiste-flyout](images/command-bar-flyout-text-full.png)
    :::column-end:::
:::row-end:::

### <a name="available-commands"></a>Verfügbaren Befehle

Diese Tabelle zeigt die Befehle in einer TextCommandBarFlyout, und wenn diese angezeigt werden.

| Befehl | Gezeigt … |
| ------- | -------- |
| Fett | Wenn das Steuerelement keine schreibgeschützt (RichEditBox nur) ist. |
| Kursiv | Wenn das Steuerelement keine schreibgeschützt (RichEditBox nur) ist. |
| Unterstreichen | Wenn das Steuerelement keine schreibgeschützt (RichEditBox nur) ist. |
| Nachweis von Manipulation | Wenn IsSpellCheckEnabled **"true ist"** und falsch geschrieben wird Text ausgewählt. |
| Ausschneiden | Wenn das Textsteuerelement ist nicht schreibgeschützt, und Text ausgewählt ist. |
| Kopieren | Wenn Text ausgewählt ist. |
| Einfügen | Wenn das Textsteuerelement ist nicht schreibgeschützt, und die Zwischenablage Inhalt ist. |
| Rückgängig machen | Wenn eine Aktion, die rückgängig gemacht werden können. |
| Alle auswählen | Wenn der Text ausgewählt werden können. |

### <a name="custom-text-command-bar-flyouts"></a>Benutzerdefinierter Text, der Flyouts auf einer Befehlsleiste

TextCommandBarFlyout nicht angepasst werden, und von jedes Textsteuerelement automatisch verwaltet wird. Allerdings können Sie die standardmäßige TextCommandBarFlyout mit benutzerdefinierten Befehlen ersetzen.

- Um die standardmäßige TextCommandBarFlyout ersetzen, die auf Textauswahl angezeigt wird, können Sie Erstellen einer benutzerdefinierten CommandBarFlyout (oder andere Flyout-Typ) und weisen sie die **SelectionFlyout** -Eigenschaft. Wenn Sie SelectionFlyout auf **null**festlegen, werden keine Befehle auf Auswahl angezeigt.
- Um die standardmäßige TextCommandBarFlyout ersetzen, die im Kontextmenü angezeigt wird, weisen Sie eine benutzerdefinierte CommandBarFlyout (oder andere Flyout-Typ) für die **ContextFlyout** -Eigenschaft für ein Text-Steuerelement. Wenn Sie ContextFlyout auf **null**festgelegt, wird das Flyout "Menü" angezeigt, die in früheren Versionen des Textsteuerelements anstelle der TextCommandBarFlyout angezeigt.

## <a name="get-the-sample-code"></a>Beispielcode herunterladen

- [Beispiel eines XAML-Steuerelementekatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.
- [Beispiel für XAML-Befehle](http://go.microsoft.com/fwlink/p/?LinkId=620019)

## <a name="related-articles"></a>Verwandte Artikel

- [Befehlsdesigngrundlagen für UWP-Apps](../basics/commanding-basics.md)
- [CommandBar-Klasse](https://msdn.microsoft.com/library/windows/apps/dn279427)
