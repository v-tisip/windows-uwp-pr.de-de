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
# <a name="command-bar-flyout"></a><span data-ttu-id="8057b-103">Befehlsleisten-Flyout</span><span class="sxs-lookup"><span data-stu-id="8057b-103">Command bar flyout</span></span>

<span data-ttu-id="8057b-104">Befehl Bar Flyout können Sie Benutzer schnellen Zugriff auf häufige Aufgaben zeigen Befehle eine schwebende Werkzeugleiste ein Element auf der Leinwand UI bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="8057b-104">The command bar flyout lets you provide users with easy access to common tasks by showing commands in a floating toolbar related to an element on your UI canvas.</span></span>

![Eine erweiterte Text Command Bar flyout](images/command-bar-flyout-header.png)

> <span data-ttu-id="8057b-106">CommandBarFlyout erfordert Windows 10 Version 1809 ([SDK 17763](https://developer.microsoft.com/windows/downloads/windows-10-sdk)) oder höher, oder [Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).</span><span class="sxs-lookup"><span data-stu-id="8057b-106">CommandBarFlyout requires Windows 10, version 1809 ([SDK 17763](https://developer.microsoft.com/windows/downloads/windows-10-sdk)) or later, or the [Windows UI Library](https://docs.microsoft.com/uwp/toolkits/winui/).</span></span>

> - <span data-ttu-id="8057b-107">**Plattform-APIs**: [CommandBarFlyout Klasse](/uwp/api/windows.ui.xaml.controls.commandbarflyout) [TextCommandBarFlyout Klasse](/uwp/api/windows.ui.xaml.controls.textcommandbarflyout) [AppBarButton Klasse](/uwp/api/windows.ui.xaml.controls.appbarbutton), [AppBarToggleButton-Klasse](/uwp/api/windows.ui.xaml.controls.appbartogglebutton), [AppBarSeparator-Klasse](/uwp/api/windows.ui.xaml.controls.appbarseparator)</span><span class="sxs-lookup"><span data-stu-id="8057b-107">**Platform APIs**: [CommandBarFlyout class](/uwp/api/windows.ui.xaml.controls.commandbarflyout), [TextCommandBarFlyout class](/uwp/api/windows.ui.xaml.controls.textcommandbarflyout), [AppBarButton class](/uwp/api/windows.ui.xaml.controls.appbarbutton), [AppBarToggleButton class](/uwp/api/windows.ui.xaml.controls.appbartogglebutton), [AppBarSeparator class](/uwp/api/windows.ui.xaml.controls.appbarseparator)</span></span>
>- <span data-ttu-id="8057b-108">**Windows-UI Library-APIs**: [CommandBarFlyout Klasse](/uwp/api/microsoft.ui.xaml.controls.commandbarflyout), [TextCommandBarFlyout-Klasse](/uwp/api/microsoft.ui.xaml.controls.textcommandbarflyout)</span><span class="sxs-lookup"><span data-stu-id="8057b-108">**Windows UI Library APIs**: [CommandBarFlyout class](/uwp/api/microsoft.ui.xaml.controls.commandbarflyout), [TextCommandBarFlyout class](/uwp/api/microsoft.ui.xaml.controls.textcommandbarflyout)</span></span>

<span data-ttu-id="8057b-109">Wie [CommandBar](app-bars.md)hat CommandBarFlyout **PrimaryCommands** und **SecondaryCommands** Eigenschaften, Befehle hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8057b-109">Like [CommandBar](app-bars.md), CommandBarFlyout has **PrimaryCommands** and **SecondaryCommands** properties you can use to add commands.</span></span> <span data-ttu-id="8057b-110">Sie können Befehle in Auflistung oder beiden platzieren.</span><span class="sxs-lookup"><span data-stu-id="8057b-110">You can place commands in either collection, or both.</span></span> <span data-ttu-id="8057b-111">Wann und wie die primären und sekundären Befehle angezeigt werden, hängt von den Anzeigemodus.</span><span class="sxs-lookup"><span data-stu-id="8057b-111">When and how the primary and secondary commands are displayed depends on the display mode.</span></span>

<span data-ttu-id="8057b-112">Flyout-Leiste Befehl verfügt über zwei Anzeigemodi: *reduziert* und *Erweitert*.</span><span class="sxs-lookup"><span data-stu-id="8057b-112">The command bar flyout has two display modes: *collapsed* and *expanded*.</span></span>

- <span data-ttu-id="8057b-113">Im reduzierten Modus werden nur die primäre Befehle angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8057b-113">In the collapsed mode, only the primary commands are shown.</span></span> <span data-ttu-id="8057b-114">Der Befehl Balken Flyout hat primäre und sekundäre Befehle eine Schaltfläche "Weitere Informationen", vertreten durch Auslassungspunkte \ [•••\] wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8057b-114">If your command bar flyout has both primary and secondary commands, a "see more" button, which is represented by an ellipsis \[•••\], is displayed.</span></span> <span data-ttu-id="8057b-115">Dies ermöglicht den Benutzer Zugriff auf die sekundären Befehle vom erweiterten Modus wechselt.</span><span class="sxs-lookup"><span data-stu-id="8057b-115">This lets the user get access to the secondary commands by transitioning to expanded mode.</span></span>
- <span data-ttu-id="8057b-116">Im erweiterten Modus werden die primären und sekundären Befehle angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8057b-116">In the expanded mode, both the primary and secondary commands are shown.</span></span> <span data-ttu-id="8057b-117">(Wenn das Steuerelement nur sekundäre Elemente verfügt, werden sie ähnlich wie das MenuFlyout-Steuerelement angezeigt.)</span><span class="sxs-lookup"><span data-stu-id="8057b-117">(If the control has only secondary items, they are shown in a way similar to the MenuFlyout control.)</span></span>

## <a name="is-this-the-right-control"></a><span data-ttu-id="8057b-118">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="8057b-118">Is this the right control?</span></span>

<span data-ttu-id="8057b-119">Mithilfe des CommandBarFlyout-Steuerelements eine Sammlung von Befehlen, wie Schaltflächen und Menüelemente im Kontext eines Elements auf der Leinwand app anzeigen.</span><span class="sxs-lookup"><span data-stu-id="8057b-119">Use the CommandBarFlyout control to show a collection of commands to the user, such as buttons and menu items, in the context of an element on the app canvas.</span></span>

<span data-ttu-id="8057b-120">Der TextCommandBarFlyout zeigt Befehle in TextBox, TextBlock-, RichEditBox, RichTextBlock und PasswordBox-Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="8057b-120">The TextCommandBarFlyout displays text commands in TextBox, TextBlock, RichEditBox, RichTextBlock, and PasswordBox controls.</span></span> <span data-ttu-id="8057b-121">Die Befehle werden automatisch auf die aktuelle Textauswahl entsprechend konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="8057b-121">The commands are automatically configured appropriately to the current text selection.</span></span> <span data-ttu-id="8057b-122">Verwenden Sie ein CommandBarFlyout Text Standardbefehle auf Textsteuerelemente ersetzen.</span><span class="sxs-lookup"><span data-stu-id="8057b-122">Use a CommandBarFlyout to replace the default text commands on text controls.</span></span>

<span data-ttu-id="8057b-123">Kontextbezogene Anzeige folgen Befehle für Listenelemente Handbuchs [kontextuelle Befehle für Sammlungen und Listen](collection-commanding.md)</span><span class="sxs-lookup"><span data-stu-id="8057b-123">To show contextual commands on list items follow the guidance in [Contextual commanding for collections and lists](collection-commanding.md).</span></span>

### <a name="commandbarflyout-vs-menuflyout"></a><span data-ttu-id="8057b-124">CommandBarFlyout gegen MenuFlyout</span><span class="sxs-lookup"><span data-stu-id="8057b-124">CommandBarFlyout vs MenuFlyout</span></span>

<span data-ttu-id="8057b-125">Um Befehle im Kontextmenü angezeigt wird, können Sie CommandBarFlyout oder MenuFlyout.</span><span class="sxs-lookup"><span data-stu-id="8057b-125">To show commands in a context menu, you can use CommandBarFlyout or MenuFlyout.</span></span> <span data-ttu-id="8057b-126">CommandBarFlyout wird empfohlen, da dadurch mehr Funktionen als MenuFlyout.</span><span class="sxs-lookup"><span data-stu-id="8057b-126">We recommend CommandBarFlyout because it provides more functionality than MenuFlyout.</span></span> <span data-ttu-id="8057b-127">Können CommandBarFlyout mit sekundären Befehle das Verhalten und Aussehen einer MenuFlyout oder vollständigen Befehl Bar Flyout mit primären und sekundären Befehlen verwenden.</span><span class="sxs-lookup"><span data-stu-id="8057b-127">You can use CommandBarFlyout with only secondary commands to get the behavior and look of a MenuFlyout, or use the full command bar flyout with both primary and secondary commands.</span></span>

> <span data-ttu-id="8057b-128">Verwandte Informationen finden Sie unter [Flyout](../controls-and-patterns/dialogs-and-flyouts/flyouts.md), [Menüs und Kontextmenüs](menus.md)und [Symbolleisten](app-bars.md).</span><span class="sxs-lookup"><span data-stu-id="8057b-128">For related info, see [Flyouts](../controls-and-patterns/dialogs-and-flyouts/flyouts.md), [Menus and context menus](menus.md), and [Command bars](app-bars.md).</span></span>

## <a name="examples"></a><span data-ttu-id="8057b-129">Beispiele</span><span class="sxs-lookup"><span data-stu-id="8057b-129">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="8057b-130">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="8057b-130">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="8057b-131">Wenn Sie <strong style="font-weight: semi-bold">XAML-Steuerelementsammlungen</strong> app installiert haben, klicken Sie hier zu <a href="xamlcontrolsgallery:/item/CommandBarFlyout">Öffnen die Anwendung CommandBarFlyout in Aktion</a>.</span><span class="sxs-lookup"><span data-stu-id="8057b-131">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/CommandBarFlyout">open the app and see the CommandBarFlyout in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="8057b-132">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="8057b-132">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="8057b-133">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="8057b-133">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="proactive-vs-reactive-invocation"></a><span data-ttu-id="8057b-134">Proaktive und reaktive Aufruf</span><span class="sxs-lookup"><span data-stu-id="8057b-134">Proactive vs. reactive invocation</span></span>

<span data-ttu-id="8057b-135">Zweierlei normalerweise zum Aufrufen einer Flyout oder einem Menü ein Element auf der Leinwand UI zugeordnet hat: _Aufruf proaktive_ und _reaktive Aufruf_.</span><span class="sxs-lookup"><span data-stu-id="8057b-135">There are typically two ways to invoke a flyout or menu that's associated with an element on your UI canvas: _proactive invocation_ and _reactive invocation_.</span></span>

<span data-ttu-id="8057b-136">Proaktive Aufruf werden Befehle automatisch bei die Befehlen zugeordnet sind das Element der Benutzer interagiert.</span><span class="sxs-lookup"><span data-stu-id="8057b-136">In proactive invocation, commands appear automatically when the user interacts with the item that the commands are associated with.</span></span> <span data-ttu-id="8057b-137">Beispielsweise können Text Formatierungsbefehle eingeblendet, wenn der Benutzer Text in ein Textfeld markiert.</span><span class="sxs-lookup"><span data-stu-id="8057b-137">For example, text formatting commands might pop up when the user selects text in a text box.</span></span> <span data-ttu-id="8057b-138">In diesem Fall übernimmt das Befehl Balken Flyout Fokus.</span><span class="sxs-lookup"><span data-stu-id="8057b-138">In this case, the command bar flyout does not take focus.</span></span> <span data-ttu-id="8057b-139">Stattdessen stellt Befehlen nahe das Element, dem mit der Benutzer interagiert.</span><span class="sxs-lookup"><span data-stu-id="8057b-139">Instead, it presents relevant commands close to the item the user is interacting with.</span></span> <span data-ttu-id="8057b-140">Wenn der Benutzer die Befehle interagieren nicht, werden sie geschlossen.</span><span class="sxs-lookup"><span data-stu-id="8057b-140">If the user doesn't interact with the commands, they are dismissed.</span></span>

<span data-ttu-id="8057b-141">Reaktive Aufruf werden Befehle auf einer expliziten Benutzeraktion Anfordern der Befehle angezeigt. beispielsweise eine Maustaste.</span><span class="sxs-lookup"><span data-stu-id="8057b-141">In reactive invocation, commands are shown in response to an explicit user action to request the commands; for example, a right-click.</span></span> <span data-ttu-id="8057b-142">Dies entspricht der herkömmlichen Konzepts für ein [Kontextmenü](menus.md).</span><span class="sxs-lookup"><span data-stu-id="8057b-142">This corresponds to the traditional concept of a [context menu](menus.md).</span></span>

<span data-ttu-id="8057b-143">CommandBarFlyout Weg oder auch eine Mischung aus beiden können.</span><span class="sxs-lookup"><span data-stu-id="8057b-143">You can use the CommandBarFlyout in either way, or even a mixture of the two.</span></span>

## <a name="create-a-command-bar-flyout"></a><span data-ttu-id="8057b-144">Ein Befehl Bar Flyout erstellen</span><span class="sxs-lookup"><span data-stu-id="8057b-144">Create a command bar flyout</span></span>

<span data-ttu-id="8057b-145">Dieses Beispiel zeigt, wie ein Befehl Bar Flyout und proaktiv und reaktiv.</span><span class="sxs-lookup"><span data-stu-id="8057b-145">This example shows how to create a command bar flyout and use it both proactively and reactively.</span></span> <span data-ttu-id="8057b-146">Wenn das Bild getippt wird, wird Flyout im reduzierten Modus angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8057b-146">When the image is tapped, the flyout is shown in its collapsed mode.</span></span> <span data-ttu-id="8057b-147">Wenn ein Kontextmenü, wird das Flyout im erweiterten Modus angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8057b-147">When shown as a context menu, the flyout is shown in its expanded mode.</span></span> <span data-ttu-id="8057b-148">In beiden Fällen kann der Benutzer erweitern oder reduzieren das Flyout nach öffnen.</span><span class="sxs-lookup"><span data-stu-id="8057b-148">In either case, the user can expand or collapse the flyout after it's opened.</span></span>

![Beispiel für eine reduzierte Befehl Bar flyout](images/command-bar-flyout-img-collapsed.png)

> _<span data-ttu-id="8057b-150">Ein Flyout reduzierten Befehl bar</span><span class="sxs-lookup"><span data-stu-id="8057b-150">A collapsed command bar flyout</span></span>_

![Beispiel für einen Flyout expandierte Befehl bar](images/command-bar-flyout-img-expanded.png)

> _<span data-ttu-id="8057b-152">Ein Flyout expandierte Befehl bar</span><span class="sxs-lookup"><span data-stu-id="8057b-152">An expanded command bar flyout</span></span>_

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

### <a name="show-commands-proactively"></a><span data-ttu-id="8057b-153">Proaktiv Befehle anzeigen</span><span class="sxs-lookup"><span data-stu-id="8057b-153">Show commands proactively</span></span>

<span data-ttu-id="8057b-154">Wenn Sie proaktiv Kontextmenüs anzeigen, soll die primären Befehle standardmäßig angezeigt werden (das Befehl Balken Flyout sollte ausgeblendet).</span><span class="sxs-lookup"><span data-stu-id="8057b-154">When you show contextual commands proactively, only the primary commands should be shown by default (the command bar flyout should be collapsed).</span></span> <span data-ttu-id="8057b-155">Setzen Sie die wichtigsten Befehle in primären Commands-Auflistung und zusätzliche Befehle, die normalerweise in einem Kontextmenü in sekundären Commands-Auflistung werden.</span><span class="sxs-lookup"><span data-stu-id="8057b-155">Place the most important commands in the primary commands collection, and additional commands that would traditionally go in a context menu into the secondary commands collection.</span></span>

<span data-ttu-id="8057b-156">Proaktiv zeigen Befehle werden normalerweise Flyout der Befehl Balken zeigen das [Klicken](/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.click) oder [Tapped](/uwp/api/windows.ui.xaml.uielement.tapped) -Ereignis behandeln.</span><span class="sxs-lookup"><span data-stu-id="8057b-156">To proactively show commands, you typically handle the [Click](/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.click) or [Tapped](/uwp/api/windows.ui.xaml.uielement.tapped) event to show the command bar flyout.</span></span> <span data-ttu-id="8057b-157">Festlegen Sie das Flyout [ShowMode](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.showmode) **vorübergehende** oder **TransientWithDismissOnPointerMoveAway** Flyout im reduzierten Modus öffnen, ohne den Fokus</span><span class="sxs-lookup"><span data-stu-id="8057b-157">Set the flyout's [ShowMode](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.showmode) to **Transient** or **TransientWithDismissOnPointerMoveAway** to open the flyout in its collapsed mode without taking focus.</span></span>

<span data-ttu-id="8057b-158">Ab Windows 10 Insider Preview Textsteuerelemente verfügen über eine **SelectionFlyout** -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="8057b-158">Starting in the Windows 10 Insider Preview, text controls have a **SelectionFlyout** property.</span></span> <span data-ttu-id="8057b-159">Wenn dieser Eigenschaft ein Flyout zuweisen, wird automatisch angezeigt, wenn Text markiert ist.</span><span class="sxs-lookup"><span data-stu-id="8057b-159">When you assign a flyout to this property, it is automatically shown when text is selected.</span></span>

### <a name="show-commands-reactively"></a><span data-ttu-id="8057b-160">Reaktiv Befehle anzeigen</span><span class="sxs-lookup"><span data-stu-id="8057b-160">Show commands reactively</span></span>

<span data-ttu-id="8057b-161">Wenn Sie Kontextmenüs reaktiv ein Kontextmenü anzeigen, sind sekundäre Befehle angezeigt (Befehl Bar Flyout sollte erweitert werden).</span><span class="sxs-lookup"><span data-stu-id="8057b-161">When you show contextual commands reactively, as a context menu, the secondary commands are shown by default (the command bar flyout should be expanded).</span></span> <span data-ttu-id="8057b-162">In diesem Fall möglicherweise Flyout Bar Befehl primäre und sekundäre Befehle oder sekundäre Befehle.</span><span class="sxs-lookup"><span data-stu-id="8057b-162">In this case, the command bar flyout might have both primary and secondary commands, or secondary commands only.</span></span>

<span data-ttu-id="8057b-163">Um Befehle im Kontextmenü anzuzeigen, weisen Sie normalerweise Flyout das [ContextFlyout](/uwp/api/windows.ui.xaml.uielement.contextflyout) -Eigenschaft eines Benutzeroberflächenelements.</span><span class="sxs-lookup"><span data-stu-id="8057b-163">To show commands in a context menu, you typically assign the flyout to the [ContextFlyout](/uwp/api/windows.ui.xaml.uielement.contextflyout) property of a UI element.</span></span> <span data-ttu-id="8057b-164">So öffnen das Flyout vom Element erfolgt und Sie müssen nichts weiter tun.</span><span class="sxs-lookup"><span data-stu-id="8057b-164">This way, opening the flyout is handled by the element, and you don't need to do anything more.</span></span>

<span data-ttu-id="8057b-165">Behandeln der Flyout (z. B. in ein [RightTapped](/uwp/api/windows.ui.xaml.uielement.righttapped) -Ereignis) mit Setzen der Flyout [ShowMode](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.showmode) **Standard** Flyout im erweiterten Modus öffnen und erhält den Eingabefokus.</span><span class="sxs-lookup"><span data-stu-id="8057b-165">If you handle showing the flyout yourself (for example, on a [RightTapped](/uwp/api/windows.ui.xaml.uielement.righttapped) event), set the flyout's [ShowMode](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.showmode) to **Standard** to open the flyout in its expanded mode and give it focus.</span></span>

> [!TIP]
> <span data-ttu-id="8057b-166">Weitere Informationen zu Optionen, wenn ein Flyout und steuern die Platzierung der Flyout anzeigen Sie [Flyout](../controls-and-patterns/dialogs-and-flyouts/flyouts.md)</span><span class="sxs-lookup"><span data-stu-id="8057b-166">For more info about options when showing a flyout and how to control placement of the flyout, see [Flyouts](../controls-and-patterns/dialogs-and-flyouts/flyouts.md).</span></span>

## <a name="commands-and-content"></a><span data-ttu-id="8057b-167">Befehle und Inhalt</span><span class="sxs-lookup"><span data-stu-id="8057b-167">Commands and content</span></span>

<span data-ttu-id="8057b-168">Das CommandBarFlyout-Steuerelement verfügt über 2 Eigenschaften Sie Befehle und Inhalt hinzufügen können: [PrimaryCommands](/uwp/api/windows.ui.xaml.controls.commandbarflyout.primarycommands) und [SecondaryCommands](/uwp/api/windows.ui.xaml.controls.commandbarflyout.secondarycommands).</span><span class="sxs-lookup"><span data-stu-id="8057b-168">The CommandBarFlyout control has 2 properties you can use to add commands and content: [PrimaryCommands](/uwp/api/windows.ui.xaml.controls.commandbarflyout.primarycommands) and [SecondaryCommands](/uwp/api/windows.ui.xaml.controls.commandbarflyout.secondarycommands).</span></span>

<span data-ttu-id="8057b-169">Befehlsleistenelemente werden standardmäßig der **PrimaryCommands**-Sammlung hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="8057b-169">By default, command bar items are added to the **PrimaryCommands** collection.</span></span> <span data-ttu-id="8057b-170">Diese Befehle werden in der Befehlszeile angezeigt und werden in den Modi bzw. angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8057b-170">These commands are shown in the command bar and are visible in both the collapsed and expanded modes.</span></span> <span data-ttu-id="8057b-171">Im Gegensatz zu CommandBar primäre Befehle nicht automatisch Überlauf zu sekundären Befehle und möglicherweise abgeschnitten.</span><span class="sxs-lookup"><span data-stu-id="8057b-171">Unlike CommandBar, primary commands do not automatically overflow to the secondary commands and might be truncated.</span></span>

<span data-ttu-id="8057b-172">Sie können auch Befehle zur **SecondaryCommands** -Auflistung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8057b-172">You can also add commands to the **SecondaryCommands** collection.</span></span> <span data-ttu-id="8057b-173">Sekundäre Befehle im Menü Bereich des Steuerelements angezeigt werden und werden nur im erweiterten Modus angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8057b-173">Secondary commands are shown in the menu portion of the control and are visible only in the expanded mode.</span></span>

### <a name="app-bar-buttons"></a><span data-ttu-id="8057b-174">App-Leistenschaltflächen</span><span class="sxs-lookup"><span data-stu-id="8057b-174">App bar buttons</span></span>

<span data-ttu-id="8057b-175">Sie können direkt mit [AppBarButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarbutton.aspx), [AppBarToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbartogglebutton.aspx)und [AppBarSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarseparator.aspx) PrimaryCommands und SecondaryCommands auffüllen.</span><span class="sxs-lookup"><span data-stu-id="8057b-175">You can populate the PrimaryCommands and SecondaryCommands directly with [AppBarButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarbutton.aspx), [AppBarToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbartogglebutton.aspx), and [AppBarSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarseparator.aspx) controls.</span></span>

<span data-ttu-id="8057b-176">Die Steuerelemente für die App-Leistenschaltfläche zeichnen sich durch ein Symbol und eine Textbeschriftung aus.</span><span class="sxs-lookup"><span data-stu-id="8057b-176">The app bar button controls are characterized by an icon and text label.</span></span> <span data-ttu-id="8057b-177">Diese Steuerelemente sind für die Verwendung in einer Befehlsleiste optimiert und ihre Darstellung abhängig, ob das Steuerelement der Befehlsleiste oder Überlaufmenü angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8057b-177">These controls are optimized for use in a command bar, and their appearance changes depending on whether the control is shown in the command bar or the overflow menu.</span></span>

- <span data-ttu-id="8057b-178">App Schaltflächen als primäre Befehle werden in der Befehlszeile mit dem Symbol angezeigt. die Beschriftung wird nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8057b-178">App bar buttons used as primary commands are shown in the command bar with only their icon; the text label is not shown.</span></span> <span data-ttu-id="8057b-179">Es wird empfohlen, QuickInfo mit eine Beschreibung des Befehls angezeigt wie folgt.</span><span class="sxs-lookup"><span data-stu-id="8057b-179">We recommend that you use a tooltip to show a text description of the command, as shown here.</span></span>
    ```xaml
    <AppBarButton Icon="Copy" ToolTipService.ToolTip="Copy"/>
    ```
- <span data-ttu-id="8057b-180">App Schaltflächen als sekundäre Befehle erscheinen im Menü mit der Bezeichnung und Symbol sichtbar.</span><span class="sxs-lookup"><span data-stu-id="8057b-180">App bar buttons used as secondary commands are shown in the menu, with both the label and icon visible.</span></span>

### <a name="other-content"></a><span data-ttu-id="8057b-181">Andere Inhalte</span><span class="sxs-lookup"><span data-stu-id="8057b-181">Other content</span></span>

<span data-ttu-id="8057b-182">Einbinden in eine AppBarElementContainer können Sie andere Steuerelemente zu einem Befehl Bar Flyout hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8057b-182">You can add other controls to a command bar flyout by wrapping them in an AppBarElementContainer.</span></span> <span data-ttu-id="8057b-183">So können Sie die Steuerelemente wie [DropDownButton]() oder [SplitButton]()hinzugefügt oder Containern wie [StackPanel]() komplexe Benutzeroberflächen erstellen.</span><span class="sxs-lookup"><span data-stu-id="8057b-183">This lets you add controls like [DropDownButton]() or [SplitButton](), or add containers like [StackPanel]() to create more complex UI.</span></span>

<span data-ttu-id="8057b-184">Um zu den primären oder sekundären Befehl ein Befehl Bar Flyout hinzugefügt werden, muss ein Element die [ICommandBarElement](/uwp/api/windows.ui.xaml.controls.icommandbarelement) -Schnittstelle implementieren.</span><span class="sxs-lookup"><span data-stu-id="8057b-184">In order to be added to the primary or secondary command collections of a command bar flyout, an element must implement the [ICommandBarElement](/uwp/api/windows.ui.xaml.controls.icommandbarelement) interface.</span></span> <span data-ttu-id="8057b-185">AppBarElementContainer ist ein Wrapper, der diese Schnittstelle implementiert, Sie ein Element zu einer Befehlsleiste hinzufügen können, auch wenn sie nicht die Schnittstelle selbst implementieren.</span><span class="sxs-lookup"><span data-stu-id="8057b-185">AppBarElementContainer is a wrapper that implements this interface so you can add an element to a command bar even if it doesn't implement the interface itself.</span></span>

<span data-ttu-id="8057b-186">Hier wird ein AppBarElementContainer verwendet, ein Flyout Befehl Leiste zusätzliche Elemente hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="8057b-186">Here, an AppBarElementContainer is used to add extra elements to a command bar flyout.</span></span> <span data-ttu-id="8057b-187">Primäre Befehle zu Farben ein SplitButton hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="8057b-187">A SplitButton is added to the primary commands to allow selection of colors.</span></span> <span data-ttu-id="8057b-188">Die sekundäre Befehle zu einem komplexeren Layout Zoomsteuerelemente StackPanel hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="8057b-188">A StackPanel is added to the secondary commands to allow a more complex layout for zoom controls.</span></span>

> [!TIP]
> <span data-ttu-id="8057b-189">Standardmäßig Elemente für die Arbeitsfläche app möglicherweise nicht sehen in einer Befehlsleiste.</span><span class="sxs-lookup"><span data-stu-id="8057b-189">By default, elements designed for the app canvas might not look right in a command bar.</span></span> <span data-ttu-id="8057b-190">Wenn Sie ein Element mit AppBarElementContainer hinzufügen, sind einige Schritte sollten Sie auf das Element andere Command Bar-Elemente entsprechen:</span><span class="sxs-lookup"><span data-stu-id="8057b-190">When you add an element using AppBarElementContainer, there are some steps you should take to make the element match other command bar elements:</span></span>
>
> - <span data-ttu-id="8057b-191">Standardpinsel mit [einfachen Stilen](/design/controls-and-patterns/xaml-styles#lightweight-styling) Hintergrund und Schaltflächen der app übereinstimmen Grenzen des Elements zu überschreiben.</span><span class="sxs-lookup"><span data-stu-id="8057b-191">Override the default brushes with [lightweight styling](/design/controls-and-patterns/xaml-styles#lightweight-styling) to make the element's background and border match the app bar buttons.</span></span>
> - <span data-ttu-id="8057b-192">Passen Sie die Größe und Position des Elements.</span><span class="sxs-lookup"><span data-stu-id="8057b-192">Adjust the size and position of the element.</span></span>
> - <span data-ttu-id="8057b-193">Umbrechen Sie Symbole in einer Viewbox mit einer Breite und Höhe des 16px.</span><span class="sxs-lookup"><span data-stu-id="8057b-193">Wrap icons in a Viewbox with a Width and Height of 16px.</span></span>

> [!NOTE]
> <span data-ttu-id="8057b-194">Dieses Beispiel zeigt nur dem Befehl Bar Flyout Benutzeroberfläche es keinen Befehl implementiert, die angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8057b-194">This example shows only the command bar flyout UI, it does not implement any of the commands that are shown.</span></span> <span data-ttu-id="8057b-195">Weitere Informationen zur Implementierung der Befehle finden Sie unter [Schaltflächen](buttons.md) und [Grundlagen Befehls](../basics/commanding-basics.md).</span><span class="sxs-lookup"><span data-stu-id="8057b-195">For more info about implementing the commands, see [Buttons](buttons.md) and [Command design basics](../basics/commanding-basics.md).</span></span>

![Ein Befehl Bar Flyout mit einer Trennschaltfläche](images/command-bar-flyout-split-button.png)

> _<span data-ttu-id="8057b-197">Eine reduzierte Befehl Bar Flyout mit offenen SplitButton</span><span class="sxs-lookup"><span data-stu-id="8057b-197">A collapsed command bar flyout with an open SplitButton</span></span>_

![Ein Befehl Bar Flyout mit komplexen Benutzeroberfläche](images/command-bar-flyout-custom-ui.png)

> _<span data-ttu-id="8057b-199">Ein Flyout expandierte Befehl Leiste mit benutzerdefinierten Zoom Benutzeroberfläche im Menü</span><span class="sxs-lookup"><span data-stu-id="8057b-199">An expanded command bar flyout with custom zoom UI in the menu</span></span>_


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

## <a name="create-a-context-menu-with-secondary-commands-only"></a><span data-ttu-id="8057b-200">Erstellen eines Kontextmenüs mit sekundären Befehle</span><span class="sxs-lookup"><span data-stu-id="8057b-200">Create a context menu with secondary commands only</span></span>

<span data-ttu-id="8057b-201">Ein CommandBarFlyout können mit sekundären Befehlen ein [Kontextmenü](menus.md)anstelle einer MenuFlyout.</span><span class="sxs-lookup"><span data-stu-id="8057b-201">You can use a CommandBarFlyout with only secondary commands as a [context menu](menus.md), in place of a MenuFlyout.</span></span>

![Ein Befehl Bar Flyout mit sekundären Befehle](images/command-bar-flyout-context-menu.png)

> _<span data-ttu-id="8057b-203">Befehl Bar Flyout als Kontextmenü</span><span class="sxs-lookup"><span data-stu-id="8057b-203">Command bar flyout as a context menu</span></span>_

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

<span data-ttu-id="8057b-204">Auch können ein CommandBarFlyout mit einem DropDownButton Sie ein Standardmenü erstellen.</span><span class="sxs-lookup"><span data-stu-id="8057b-204">You can also use a CommandBarFlyout with a DropDownButton to create a standard menu.</span></span>

![Ein Befehl Bar Flyout mit als Dropdown-Schaltfläche](images/command-bar-flyout-dropdown.png)

> _<span data-ttu-id="8057b-206">Ein Dropdown-Menü der Schaltfläche in einem Befehl Bar flyout</span><span class="sxs-lookup"><span data-stu-id="8057b-206">A drop down button menu in a command bar flyout</span></span>_

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

## <a name="command-bar-flyouts-for-text-controls"></a><span data-ttu-id="8057b-207">Befehl Bar Flyout für Text-Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="8057b-207">Command bar flyouts for text controls</span></span>

<span data-ttu-id="8057b-208">[TextCommandBarFlyout](/uwp/api/microsoft.ui.xaml.controls.textcommandbarflyout) ist eine spezielle Befehl Bar Flyout, das Befehle zum Bearbeiten von Text enthält.</span><span class="sxs-lookup"><span data-stu-id="8057b-208">The [TextCommandBarFlyout](/uwp/api/microsoft.ui.xaml.controls.textcommandbarflyout) is a specialized command bar flyout that contains commands for editing text.</span></span> <span data-ttu-id="8057b-209">Jedes Textsteuerelement wird der TextCommandBarFlyout automatisch als Kontextmenü (rechte Maustaste) oder wenn Text ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="8057b-209">Each text control shows the TextCommandBarFlyout automatically as a context menu (right-click), or when text is selected.</span></span> <span data-ttu-id="8057b-210">Text Command Bar Flyout passt die Textauswahl nur Befehlen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8057b-210">The text command bar flyout adapts to the text selection to only show relevant commands.</span></span>

![Ein Flyout reduzierten Text Befehl bar](images/command-bar-flyout-text-selection.png)

> _<span data-ttu-id="8057b-212">Ein Flyout Text Befehl Bar auf markierten text</span><span class="sxs-lookup"><span data-stu-id="8057b-212">A text command bar flyout on text selection</span></span>_

![Eine erweiterte Text Command Bar flyout](images/command-bar-flyout-text-full.png)

> _<span data-ttu-id="8057b-214">Eine erweiterte Text Command Bar flyout</span><span class="sxs-lookup"><span data-stu-id="8057b-214">An expanded text command bar flyout</span></span>_


### <a name="available-commands"></a><span data-ttu-id="8057b-215">Verfügbare Befehle</span><span class="sxs-lookup"><span data-stu-id="8057b-215">Available commands</span></span>

<span data-ttu-id="8057b-216">Der Tabelle werden die Befehle in einer TextCommandBarFlyout und wenn sie angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8057b-216">This table shows the commands that are included in a TextCommandBarFlyout, and when they are shown.</span></span>

| <span data-ttu-id="8057b-217">Befehl</span><span class="sxs-lookup"><span data-stu-id="8057b-217">Command</span></span> | <span data-ttu-id="8057b-218">Angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8057b-218">Shown...</span></span> |
| ------- | -------- |
| <span data-ttu-id="8057b-219">Fett</span><span class="sxs-lookup"><span data-stu-id="8057b-219">Bold</span></span> | <span data-ttu-id="8057b-220">ist das Steuerelement nicht schreibgeschützt (RichEditBox nur).</span><span class="sxs-lookup"><span data-stu-id="8057b-220">when the text control is not read-only (RichEditBox only).</span></span> |
| <span data-ttu-id="8057b-221">Kursiv</span><span class="sxs-lookup"><span data-stu-id="8057b-221">Italic</span></span> | <span data-ttu-id="8057b-222">ist das Steuerelement nicht schreibgeschützt (RichEditBox nur).</span><span class="sxs-lookup"><span data-stu-id="8057b-222">when the text control is not read-only (RichEditBox only).</span></span> |
| <span data-ttu-id="8057b-223">Unterstreichen</span><span class="sxs-lookup"><span data-stu-id="8057b-223">Underline</span></span> | <span data-ttu-id="8057b-224">ist das Steuerelement nicht schreibgeschützt (RichEditBox nur).</span><span class="sxs-lookup"><span data-stu-id="8057b-224">when the text control is not read-only (RichEditBox only).</span></span> |
| <span data-ttu-id="8057b-225">Rechtschreibprüfung</span><span class="sxs-lookup"><span data-stu-id="8057b-225">Proofing</span></span> | <span data-ttu-id="8057b-226">Wenn IsSpellCheckEnabled **Wahr** und falsch ist Text markiert.</span><span class="sxs-lookup"><span data-stu-id="8057b-226">when IsSpellCheckEnabled is **true** and misspelled text is selected.</span></span> |
| <span data-ttu-id="8057b-227">Ausschneiden</span><span class="sxs-lookup"><span data-stu-id="8057b-227">Cut</span></span> | <span data-ttu-id="8057b-228">Wenn das Steuerelement nicht schreibgeschützt und Text markiert.</span><span class="sxs-lookup"><span data-stu-id="8057b-228">when the text control is not read-only and text is selected.</span></span> |
| <span data-ttu-id="8057b-229">Kopieren</span><span class="sxs-lookup"><span data-stu-id="8057b-229">Copy</span></span> | <span data-ttu-id="8057b-230">Wenn Text ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="8057b-230">when text is selected.</span></span> |
| <span data-ttu-id="8057b-231">Einfügen</span><span class="sxs-lookup"><span data-stu-id="8057b-231">Paste</span></span> | <span data-ttu-id="8057b-232">Wenn das Steuerelement nicht schreibgeschützt und Zwischenablage Inhalt.</span><span class="sxs-lookup"><span data-stu-id="8057b-232">when the text control is not read-only and the clipboard has content.</span></span> |
| <span data-ttu-id="8057b-233">Rückgängig machen</span><span class="sxs-lookup"><span data-stu-id="8057b-233">Undo</span></span> | <span data-ttu-id="8057b-234">Wenn eine Aktion, die rückgängig gemacht werden kann.</span><span class="sxs-lookup"><span data-stu-id="8057b-234">when there is an action that can be undone.</span></span> |
| <span data-ttu-id="8057b-235">Alle auswählen</span><span class="sxs-lookup"><span data-stu-id="8057b-235">Select all</span></span> | <span data-ttu-id="8057b-236">Wenn Text ausgewählt werden kann.</span><span class="sxs-lookup"><span data-stu-id="8057b-236">when text can be selected.</span></span> |

### <a name="custom-text-command-bar-flyouts"></a><span data-ttu-id="8057b-237">Benutzerdefinierten Text Command Bar Flyout</span><span class="sxs-lookup"><span data-stu-id="8057b-237">Custom text command bar flyouts</span></span>

<span data-ttu-id="8057b-238">TextCommandBarFlyout kann nicht angepasst werden und von den einzelnen Steuerelementen Text automatisch verwaltet wird.</span><span class="sxs-lookup"><span data-stu-id="8057b-238">TextCommandBarFlyout can't be customized, and is managed automatically by each text control.</span></span> <span data-ttu-id="8057b-239">Allerdings können Sie die Standard-TextCommandBarFlyout mit benutzerdefinierten Befehlen ersetzen.</span><span class="sxs-lookup"><span data-stu-id="8057b-239">However, you can replace the default TextCommandBarFlyout with custom commands.</span></span>

- <span data-ttu-id="8057b-240">Standard TextCommandBarFlyout ersetzen, die auf markierten Text angezeigt wird, können erstellen Sie eine benutzerdefinierte CommandBarFlyout (oder andere Flyout) und der **SelectionFlyout** -Eigenschaft zuweisen.</span><span class="sxs-lookup"><span data-stu-id="8057b-240">To replace the default TextCommandBarFlyout that's shown on text selection, you can create a custom CommandBarFlyout (or other flyout type) and assign it to the **SelectionFlyout** property.</span></span> <span data-ttu-id="8057b-241">Wenn SelectionFlyout auf **null**festgelegt wird, werden keine Befehle auf Auswahl angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8057b-241">If you set SelectionFlyout to **null**, no commands are shown on selection.</span></span>
- <span data-ttu-id="8057b-242">Standard TextCommandBarFlyout ersetzen, die im Kontextmenü angezeigt wird, weisen Sie benutzerdefinierte CommandBarFlyout oder sonstige Flyout **ContextFlyout** -Eigenschaft für ein Textfeld-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="8057b-242">To replace the default TextCommandBarFlyout that's shown as the context menu, assign a custom CommandBarFlyout (or other flyout type) to the **ContextFlyout** property on a text control.</span></span> <span data-ttu-id="8057b-243">ContextFlyout auf **null**festgelegt wird, wird in früheren Versionen des Steuerelements angezeigte Menü-Flyout anstelle der TextCommandBarFlyout angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8057b-243">If you set ContextFlyout to **null**, the menu flyout shown in previous versions of the text control is shown instead of the TextCommandBarFlyout.</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="8057b-244">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="8057b-244">Get the sample code</span></span>

- <span data-ttu-id="8057b-245">[Beispiel eines XAML-Steuerelementekatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="8057b-245">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>
- [<span data-ttu-id="8057b-246">Beispiel für XAML-Befehle</span><span class="sxs-lookup"><span data-stu-id="8057b-246">XAML Commanding sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=620019)

## <a name="related-articles"></a><span data-ttu-id="8057b-247">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="8057b-247">Related articles</span></span>

- [<span data-ttu-id="8057b-248">Befehlsdesigngrundlagen für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="8057b-248">Command design basics for UWP apps</span></span>](../basics/commanding-basics.md)
- [<span data-ttu-id="8057b-249">CommandBar-Klasse</span><span class="sxs-lookup"><span data-stu-id="8057b-249">CommandBar class</span></span>](https://msdn.microsoft.com/library/windows/apps/dn279427)
