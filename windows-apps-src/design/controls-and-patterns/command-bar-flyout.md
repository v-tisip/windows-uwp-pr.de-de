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
ms.sourcegitcommit: 38f06f1714334273d865935d9afb80efffe97a17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6199810"
---
# <a name="command-bar-flyout"></a><span data-ttu-id="8b572-103">Befehlsleisten-Flyout</span><span class="sxs-lookup"><span data-stu-id="8b572-103">Command bar flyout</span></span>

<span data-ttu-id="8b572-104">Die Befehlsleisten-Flyout können Sie die Benutzer einfachen Zugriff auf allgemeine Aufgaben bereitstellen, indem Sie Befehle in einem schwebenden Symbolleisten im Zusammenhang mit eines Elements auf die UI-Canvas anzeigen.</span><span class="sxs-lookup"><span data-stu-id="8b572-104">The command bar flyout lets you provide users with easy access to common tasks by showing commands in a floating toolbar related to an element on your UI canvas.</span></span>

![Eine erweiterte Text Befehlsleisten-flyout](images/command-bar-flyout-header.png)

> <span data-ttu-id="8b572-106">CommandBarFlyout erfordert Windows 10, Version 1809 ([SDK 17763](https://developer.microsoft.com/windows/downloads/windows-10-sdk)) oder höher, oder in der [Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).</span><span class="sxs-lookup"><span data-stu-id="8b572-106">CommandBarFlyout requires Windows 10, version 1809 ([SDK 17763](https://developer.microsoft.com/windows/downloads/windows-10-sdk)) or later, or the [Windows UI Library](https://docs.microsoft.com/uwp/toolkits/winui/).</span></span>

> - <span data-ttu-id="8b572-107">**Plattform-APIs**: [CommandBarFlyout-Klasse](/uwp/api/windows.ui.xaml.controls.commandbarflyout), [TextCommandBarFlyout-Klasse](/uwp/api/windows.ui.xaml.controls.textcommandbarflyout), [AppBarButton-Klasse](/uwp/api/windows.ui.xaml.controls.appbarbutton), [Klasse "appbartogglebutton"](/uwp/api/windows.ui.xaml.controls.appbartogglebutton), [Klasse "appbarseparator"](/uwp/api/windows.ui.xaml.controls.appbarseparator)</span><span class="sxs-lookup"><span data-stu-id="8b572-107">**Platform APIs**: [CommandBarFlyout class](/uwp/api/windows.ui.xaml.controls.commandbarflyout), [TextCommandBarFlyout class](/uwp/api/windows.ui.xaml.controls.textcommandbarflyout), [AppBarButton class](/uwp/api/windows.ui.xaml.controls.appbarbutton), [AppBarToggleButton class](/uwp/api/windows.ui.xaml.controls.appbartogglebutton), [AppBarSeparator class](/uwp/api/windows.ui.xaml.controls.appbarseparator)</span></span>
>- <span data-ttu-id="8b572-108">**Windows-UI-Bibliothek-APIs**: [CommandBarFlyout-Klasse](/uwp/api/microsoft.ui.xaml.controls.commandbarflyout), [TextCommandBarFlyout-Klasse](/uwp/api/microsoft.ui.xaml.controls.textcommandbarflyout)</span><span class="sxs-lookup"><span data-stu-id="8b572-108">**Windows UI Library APIs**: [CommandBarFlyout class](/uwp/api/microsoft.ui.xaml.controls.commandbarflyout), [TextCommandBarFlyout class](/uwp/api/microsoft.ui.xaml.controls.textcommandbarflyout)</span></span>

<span data-ttu-id="8b572-109">Wie [CommandBar](app-bars.md)hat CommandBarFlyout **PrimaryCommands** und **"secondarycommands"** Eigenschaften, mit denen Sie Befehle hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8b572-109">Like [CommandBar](app-bars.md), CommandBarFlyout has **PrimaryCommands** and **SecondaryCommands** properties you can use to add commands.</span></span> <span data-ttu-id="8b572-110">Sie können entweder Sammlung oder beide Befehle versehen.</span><span class="sxs-lookup"><span data-stu-id="8b572-110">You can place commands in either collection, or both.</span></span> <span data-ttu-id="8b572-111">Wann und wie die primären und sekundären Befehle angezeigt werden, hängt von den Anzeigemodus.</span><span class="sxs-lookup"><span data-stu-id="8b572-111">When and how the primary and secondary commands are displayed depends on the display mode.</span></span>

<span data-ttu-id="8b572-112">Die Befehlsleisten-Flyout verfügt über zwei Anzeigemodi: *reduziert* und *Erweitert*.</span><span class="sxs-lookup"><span data-stu-id="8b572-112">The command bar flyout has two display modes: *collapsed* and *expanded*.</span></span>

- <span data-ttu-id="8b572-113">Im Modus "Collapsed" werden nur die primären Befehle angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8b572-113">In the collapsed mode, only the primary commands are shown.</span></span> <span data-ttu-id="8b572-114">Hat Ihre Befehlsleisten-Flyout primären und sekundären Befehlen, eine "Schaltfläche" Weitere, dargestellt durch Auslassungspunkte \ [• • •] wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8b572-114">If your command bar flyout has both primary and secondary commands, a "see more" button, which is represented by an ellipsis \[•••\], is displayed.</span></span> <span data-ttu-id="8b572-115">So kann der Benutzer Zugriff auf die sekundären Befehle zu erhalten, indem Wechsel zur erweiterten Modus.</span><span class="sxs-lookup"><span data-stu-id="8b572-115">This lets the user get access to the secondary commands by transitioning to expanded mode.</span></span>
- <span data-ttu-id="8b572-116">Im erweiterten Modus werden die primären und sekundären Befehle angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8b572-116">In the expanded mode, both the primary and secondary commands are shown.</span></span> <span data-ttu-id="8b572-117">(Wenn das Steuerelement nur sekundäre Elemente verfügt, werden sie in einer Weise ähnelt dem MenuFlyout-Steuerelement angezeigt.)</span><span class="sxs-lookup"><span data-stu-id="8b572-117">(If the control has only secondary items, they are shown in a way similar to the MenuFlyout control.)</span></span>

## <a name="is-this-the-right-control"></a><span data-ttu-id="8b572-118">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="8b572-118">Is this the right control?</span></span>

<span data-ttu-id="8b572-119">Verwenden Sie das CommandBarFlyout-Steuerelement, um eine Sammlung von Befehlen für dem Benutzer, z. B. Schaltflächen und Menüelementen im Kontext eines Elements auf der app-Canvas anzeigen.</span><span class="sxs-lookup"><span data-stu-id="8b572-119">Use the CommandBarFlyout control to show a collection of commands to the user, such as buttons and menu items, in the context of an element on the app canvas.</span></span>

<span data-ttu-id="8b572-120">Die TextCommandBarFlyout zeigt Textbefehle im TextBlock, TextBox, RichEditBox, RichTextBlock und PasswordBox-Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="8b572-120">The TextCommandBarFlyout displays text commands in TextBox, TextBlock, RichEditBox, RichTextBlock, and PasswordBox controls.</span></span> <span data-ttu-id="8b572-121">Die Befehle sind für die aktuelle Textauswahl automatisch entsprechend konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="8b572-121">The commands are automatically configured appropriately to the current text selection.</span></span> <span data-ttu-id="8b572-122">Verwenden Sie eine CommandBarFlyout, um die Standard-Text-Befehle für Textsteuerelemente ersetzen.</span><span class="sxs-lookup"><span data-stu-id="8b572-122">Use a CommandBarFlyout to replace the default text commands on text controls.</span></span>

<span data-ttu-id="8b572-123">Um kontextbezogene anzuzeigen führen Sie die Befehle auf Listenelemente die Anleitung im [Contextual Befehle für Sammlungen und Listen](collection-commanding.md).</span><span class="sxs-lookup"><span data-stu-id="8b572-123">To show contextual commands on list items follow the guidance in [Contextual commanding for collections and lists](collection-commanding.md).</span></span>

### <a name="commandbarflyout-vs-menuflyout"></a><span data-ttu-id="8b572-124">CommandBarFlyout Vs MenuFlyout</span><span class="sxs-lookup"><span data-stu-id="8b572-124">CommandBarFlyout vs MenuFlyout</span></span>

<span data-ttu-id="8b572-125">Um Befehle in einem Kontextmenü anzuzeigen, können Sie CommandBarFlyout oder MenuFlyout verwenden.</span><span class="sxs-lookup"><span data-stu-id="8b572-125">To show commands in a context menu, you can use CommandBarFlyout or MenuFlyout.</span></span> <span data-ttu-id="8b572-126">CommandBarFlyout wird empfohlen, da es mehr Funktionen als MenuFlyout bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="8b572-126">We recommend CommandBarFlyout because it provides more functionality than MenuFlyout.</span></span> <span data-ttu-id="8b572-127">Sie können CommandBarFlyout mit nur sekundäre Befehle verwenden, erhalten das Verhalten und von einem MenuFlyout aussehen, oder die vollständige Befehlsleisten-Flyout mit primären und sekundären Befehlen.</span><span class="sxs-lookup"><span data-stu-id="8b572-127">You can use CommandBarFlyout with only secondary commands to get the behavior and look of a MenuFlyout, or use the full command bar flyout with both primary and secondary commands.</span></span>

> <span data-ttu-id="8b572-128">Verwandte Informationen finden Sie unter [Flyouts](../controls-and-patterns/dialogs-and-flyouts/flyouts.md), [Menüs und Kontextmenüs](menus.md)und [Befehlsleisten](app-bars.md).</span><span class="sxs-lookup"><span data-stu-id="8b572-128">For related info, see [Flyouts](../controls-and-patterns/dialogs-and-flyouts/flyouts.md), [Menus and context menus](menus.md), and [Command bars](app-bars.md).</span></span>

## <a name="examples"></a><span data-ttu-id="8b572-129">Beispiele</span><span class="sxs-lookup"><span data-stu-id="8b572-129">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="8b572-130">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="8b572-130">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="8b572-131">Wenn Sie die <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> -app installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/CommandBarFlyout">die app zu öffnen und finden Sie unter den CommandBarFlyout in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="8b572-131">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/CommandBarFlyout">open the app and see the CommandBarFlyout in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="8b572-132">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="8b572-132">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="8b572-133">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="8b572-133">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="proactive-vs-reactive-invocation"></a><span data-ttu-id="8b572-134">Im Vergleich zu Zeiten Aufruf proaktive</span><span class="sxs-lookup"><span data-stu-id="8b572-134">Proactive vs. reactive invocation</span></span>

<span data-ttu-id="8b572-135">Es gibt in der Regel zwei Möglichkeiten zum Aufrufen eines Flyout oder das Menü, die mit einem Element auf Ihrer Benutzeroberfläche Canvas zugeordnet ist: _proaktive aufrufen_ und das _reaktive Aufruf_.</span><span class="sxs-lookup"><span data-stu-id="8b572-135">There are typically two ways to invoke a flyout or menu that's associated with an element on your UI canvas: _proactive invocation_ and _reactive invocation_.</span></span>

<span data-ttu-id="8b572-136">Unter proaktive Aufruf werden Befehle automatisch angezeigt, wenn der Benutzer mit dem Element interagiert, die die Befehle zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="8b572-136">In proactive invocation, commands appear automatically when the user interacts with the item that the commands are associated with.</span></span> <span data-ttu-id="8b572-137">Z. B. möglicherweise Formatierungsbefehle Text eingeblendet, wenn der Benutzer Text in einem Textfeld auswählt.</span><span class="sxs-lookup"><span data-stu-id="8b572-137">For example, text formatting commands might pop up when the user selects text in a text box.</span></span> <span data-ttu-id="8b572-138">In diesem Fall akzeptiert die Befehlsleisten-Flyout nicht den Fokus.</span><span class="sxs-lookup"><span data-stu-id="8b572-138">In this case, the command bar flyout does not take focus.</span></span> <span data-ttu-id="8b572-139">Stattdessen zeigt sie geeignete Befehle nahe dem Element, dem mit der Benutzer interagiert.</span><span class="sxs-lookup"><span data-stu-id="8b572-139">Instead, it presents relevant commands close to the item the user is interacting with.</span></span> <span data-ttu-id="8b572-140">Wenn der Benutzer mit den Befehlen interagieren nicht, werden sie geschlossen.</span><span class="sxs-lookup"><span data-stu-id="8b572-140">If the user doesn't interact with the commands, they are dismissed.</span></span>

<span data-ttu-id="8b572-141">Unter reaktive Aufruf werden Befehle in Reaktion auf eine explizite Benutzeraktion angezeigt, die Befehle anfordern; Beispiel: ein Rechtsklick.</span><span class="sxs-lookup"><span data-stu-id="8b572-141">In reactive invocation, commands are shown in response to an explicit user action to request the commands; for example, a right-click.</span></span> <span data-ttu-id="8b572-142">Dies entspricht der herkömmlichen Konzept eines [Kontextmenüs](menus.md).</span><span class="sxs-lookup"><span data-stu-id="8b572-142">This corresponds to the traditional concept of a [context menu](menus.md).</span></span>

<span data-ttu-id="8b572-143">Sie können die CommandBarFlyout in Weise oder sogar eine Mischung der beiden verwenden.</span><span class="sxs-lookup"><span data-stu-id="8b572-143">You can use the CommandBarFlyout in either way, or even a mixture of the two.</span></span>

## <a name="create-a-command-bar-flyout"></a><span data-ttu-id="8b572-144">Erstellen Sie eine Befehlsleisten-flyout</span><span class="sxs-lookup"><span data-stu-id="8b572-144">Create a command bar flyout</span></span>

<span data-ttu-id="8b572-145">In diesem Beispiel wird veranschaulicht, wie ein Befehlsleisten-Flyout zu erstellen und sie proaktiv sowohl reaktiv.</span><span class="sxs-lookup"><span data-stu-id="8b572-145">This example shows how to create a command bar flyout and use it both proactively and reactively.</span></span> <span data-ttu-id="8b572-146">Wenn das Bild getippt wird, wird das Flyout im Modus "Collapsed" angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8b572-146">When the image is tapped, the flyout is shown in its collapsed mode.</span></span> <span data-ttu-id="8b572-147">Wenn als Kontextmenü angezeigt wird, wird das Flyout im erweiterten Modus angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8b572-147">When shown as a context menu, the flyout is shown in its expanded mode.</span></span> <span data-ttu-id="8b572-148">In beiden Fällen kann der Benutzer erweitern oder reduzieren das Flyout, nachdem er geöffnet wird.</span><span class="sxs-lookup"><span data-stu-id="8b572-148">In either case, the user can expand or collapse the flyout after it's opened.</span></span>

![Beispiel für eine "Collapsed" Befehlsleisten-flyout](images/command-bar-flyout-img-collapsed.png)

> _<span data-ttu-id="8b572-150">Ein "Collapsed" Befehlsleisten-flyout</span><span class="sxs-lookup"><span data-stu-id="8b572-150">A collapsed command bar flyout</span></span>_

![Beispiel für eine erweiterte Befehlsleisten-flyout](images/command-bar-flyout-img-expanded.png)

> _<span data-ttu-id="8b572-152">Eine erweiterte Befehlsleisten-flyout</span><span class="sxs-lookup"><span data-stu-id="8b572-152">An expanded command bar flyout</span></span>_

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

### <a name="show-commands-proactively"></a><span data-ttu-id="8b572-153">Befehle proaktiv anzeigen</span><span class="sxs-lookup"><span data-stu-id="8b572-153">Show commands proactively</span></span>

<span data-ttu-id="8b572-154">Wenn Sie Kontextbefehlen proaktiv angezeigt wird, sollte nur die primären Befehle standardmäßig angezeigt werden (die Befehlsleisten-Flyout sollte reduziert werden).</span><span class="sxs-lookup"><span data-stu-id="8b572-154">When you show contextual commands proactively, only the primary commands should be shown by default (the command bar flyout should be collapsed).</span></span> <span data-ttu-id="8b572-155">Platzieren Sie die wichtigsten Befehle in die primäre Befehle Sammlung, und klicken Sie auf zusätzliche Befehle, die normalerweise in einem Kontextmenü in die sekundären Befehle Auflistung würde.</span><span class="sxs-lookup"><span data-stu-id="8b572-155">Place the most important commands in the primary commands collection, and additional commands that would traditionally go in a context menu into the secondary commands collection.</span></span>

<span data-ttu-id="8b572-156">Um Befehle proaktiv anzuzeigen, behandeln Sie in der Regel das Ereignis [Klicken](/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.click) oder [Tapped](/uwp/api/windows.ui.xaml.uielement.tapped) , um die Befehlsleisten-Flyout anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="8b572-156">To proactively show commands, you typically handle the [Click](/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.click) or [Tapped](/uwp/api/windows.ui.xaml.uielement.tapped) event to show the command bar flyout.</span></span> <span data-ttu-id="8b572-157">Legen Sie das Flyout [ShowMode](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.showmode) **vorübergehende** oder **TransientWithDismissOnPointerMoveAway** , um das Flyout im Modus "Collapsed" zu öffnen, ohne den Fokus fest.</span><span class="sxs-lookup"><span data-stu-id="8b572-157">Set the flyout's [ShowMode](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.showmode) to **Transient** or **TransientWithDismissOnPointerMoveAway** to open the flyout in its collapsed mode without taking focus.</span></span>

<span data-ttu-id="8b572-158">Ab Windows 10 Insider Preview, Text-Steuerelemente verfügen über eine **SelectionFlyout** -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="8b572-158">Starting in the Windows 10 Insider Preview, text controls have a **SelectionFlyout** property.</span></span> <span data-ttu-id="8b572-159">Wenn Sie diese Eigenschaft ein Flyout zuordnen, wird er automatisch angezeigt, wenn Text markiert ist.</span><span class="sxs-lookup"><span data-stu-id="8b572-159">When you assign a flyout to this property, it is automatically shown when text is selected.</span></span>

### <a name="show-commands-reactively"></a><span data-ttu-id="8b572-160">Befehle reaktiv anzeigen</span><span class="sxs-lookup"><span data-stu-id="8b572-160">Show commands reactively</span></span>

<span data-ttu-id="8b572-161">Wenn Sie Kontextbefehlen reaktiv, als Kontextmenü angezeigt wird, werden die sekundären Befehle standardmäßig angezeigt (die Befehlsleisten-Flyout sollte erweitert werden).</span><span class="sxs-lookup"><span data-stu-id="8b572-161">When you show contextual commands reactively, as a context menu, the secondary commands are shown by default (the command bar flyout should be expanded).</span></span> <span data-ttu-id="8b572-162">In diesem Fall wird möglicherweise die Befehlsleisten-Flyout primären und sekundären Befehle oder nur sekundäre Befehle.</span><span class="sxs-lookup"><span data-stu-id="8b572-162">In this case, the command bar flyout might have both primary and secondary commands, or secondary commands only.</span></span>

<span data-ttu-id="8b572-163">Um Befehle in einem Kontextmenü anzuzeigen, weisen Sie in der Regel das Flyout der [ContextFlyout](/uwp/api/windows.ui.xaml.uielement.contextflyout) -Eigenschaft eines Benutzeroberflächenelements.</span><span class="sxs-lookup"><span data-stu-id="8b572-163">To show commands in a context menu, you typically assign the flyout to the [ContextFlyout](/uwp/api/windows.ui.xaml.uielement.contextflyout) property of a UI element.</span></span> <span data-ttu-id="8b572-164">Auf diese Weise wird das Flyout Öffnen des Elements behandelt, und Sie müssen nichts weiter tun.</span><span class="sxs-lookup"><span data-stu-id="8b572-164">This way, opening the flyout is handled by the element, and you don't need to do anything more.</span></span>

<span data-ttu-id="8b572-165">Wenn Sie das Flyout (z. B. auf ein Ereignis [RightTapped](/uwp/api/windows.ui.xaml.uielement.righttapped) ) anzeigen behandeln, legen Sie das Flyout [ShowMode](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.showmode) auf **Standard** für das Flyout im erweiterten Modus zu öffnen, und weisen Sie ihm den Fokus.</span><span class="sxs-lookup"><span data-stu-id="8b572-165">If you handle showing the flyout yourself (for example, on a [RightTapped](/uwp/api/windows.ui.xaml.uielement.righttapped) event), set the flyout's [ShowMode](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.showmode) to **Standard** to open the flyout in its expanded mode and give it focus.</span></span>

> [!TIP]
> <span data-ttu-id="8b572-166">Weitere Informationen zu den Optionen, wenn ein Flyout und zur Steuerung der Platzierung der das Flyout angezeigt finden Sie unter [Flyouts](../controls-and-patterns/dialogs-and-flyouts/flyouts.md).</span><span class="sxs-lookup"><span data-stu-id="8b572-166">For more info about options when showing a flyout and how to control placement of the flyout, see [Flyouts](../controls-and-patterns/dialogs-and-flyouts/flyouts.md).</span></span>

## <a name="commands-and-content"></a><span data-ttu-id="8b572-167">Befehle und Inhalt</span><span class="sxs-lookup"><span data-stu-id="8b572-167">Commands and content</span></span>

<span data-ttu-id="8b572-168">Die CommandBarFlyout-Steuerelement verfügt über 2 Eigenschaften Sie Befehle und Inhalte hinzufügen können: [PrimaryCommands](/uwp/api/windows.ui.xaml.controls.commandbarflyout.primarycommands) und ["secondarycommands"](/uwp/api/windows.ui.xaml.controls.commandbarflyout.secondarycommands).</span><span class="sxs-lookup"><span data-stu-id="8b572-168">The CommandBarFlyout control has 2 properties you can use to add commands and content: [PrimaryCommands](/uwp/api/windows.ui.xaml.controls.commandbarflyout.primarycommands) and [SecondaryCommands](/uwp/api/windows.ui.xaml.controls.commandbarflyout.secondarycommands).</span></span>

<span data-ttu-id="8b572-169">Befehlsleistenelemente werden standardmäßig der **PrimaryCommands**-Sammlung hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="8b572-169">By default, command bar items are added to the **PrimaryCommands** collection.</span></span> <span data-ttu-id="8b572-170">Diese Befehle werden angezeigt, in der Befehlsleiste und sowohl die "Collapsed" auch im erweiterten Modus sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="8b572-170">These commands are shown in the command bar and are visible in both the collapsed and expanded modes.</span></span> <span data-ttu-id="8b572-171">Im Gegensatz zu CommandBar primäre Befehle nicht automatisch Überlauf für die sekundären Befehle und möglicherweise abgeschnitten.</span><span class="sxs-lookup"><span data-stu-id="8b572-171">Unlike CommandBar, primary commands do not automatically overflow to the secondary commands and might be truncated.</span></span>

<span data-ttu-id="8b572-172">Sie können auch Befehle zur Auflistung **SecondaryCommands** hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8b572-172">You can also add commands to the **SecondaryCommands** collection.</span></span> <span data-ttu-id="8b572-173">Sekundäre Befehle in das Menü Teil des Steuerelements angezeigt werden und sind nur im erweiterten Modus sichtbar.</span><span class="sxs-lookup"><span data-stu-id="8b572-173">Secondary commands are shown in the menu portion of the control and are visible only in the expanded mode.</span></span>

### <a name="app-bar-buttons"></a><span data-ttu-id="8b572-174">App-Leistenschaltflächen</span><span class="sxs-lookup"><span data-stu-id="8b572-174">App bar buttons</span></span>

<span data-ttu-id="8b572-175">Sie können die PrimaryCommands und "secondarycommands" direkt mit [AppBarButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarbutton.aspx), [AppBarToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbartogglebutton.aspx)und [AppBarSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarseparator.aspx) Steuerelementen auffüllen.</span><span class="sxs-lookup"><span data-stu-id="8b572-175">You can populate the PrimaryCommands and SecondaryCommands directly with [AppBarButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarbutton.aspx), [AppBarToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbartogglebutton.aspx), and [AppBarSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarseparator.aspx) controls.</span></span>

<span data-ttu-id="8b572-176">Die Steuerelemente für die App-Leistenschaltfläche zeichnen sich durch ein Symbol und eine Textbeschriftung aus.</span><span class="sxs-lookup"><span data-stu-id="8b572-176">The app bar button controls are characterized by an icon and text label.</span></span> <span data-ttu-id="8b572-177">Diese Steuerelemente sind für die Verwendung in Befehlsleisten optimiert, und ihre Darstellung ändert, je nachdem, ob das Steuerelement in der Befehlsleiste oder im Überlaufmenü angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8b572-177">These controls are optimized for use in a command bar, and their appearance changes depending on whether the control is shown in the command bar or the overflow menu.</span></span>

- <span data-ttu-id="8b572-178">App-Leistenschaltflächen als primäre Befehle verwendet werden in der Befehlsleiste mit nur ihre Symbol angezeigt. die Beschriftung wird nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8b572-178">App bar buttons used as primary commands are shown in the command bar with only their icon; the text label is not shown.</span></span> <span data-ttu-id="8b572-179">Es wird empfohlen, dass Sie eine QuickInfo verwenden, um einen beschreibenden Text für den Befehl anzuzeigen wie hier gezeigt.</span><span class="sxs-lookup"><span data-stu-id="8b572-179">We recommend that you use a tooltip to show a text description of the command, as shown here.</span></span>
    ```xaml
    <AppBarButton Icon="Copy" ToolTipService.ToolTip="Copy"/>
    ```
- <span data-ttu-id="8b572-180">App-Leistenschaltflächen als sekundäre Befehle verwendet werden Sie im Menü mit der Bezeichnung und Symbol sichtbar angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8b572-180">App bar buttons used as secondary commands are shown in the menu, with both the label and icon visible.</span></span>

### <a name="other-content"></a><span data-ttu-id="8b572-181">Andere Inhalte</span><span class="sxs-lookup"><span data-stu-id="8b572-181">Other content</span></span>

<span data-ttu-id="8b572-182">Sie können andere Steuerelemente auf einem Befehlsleisten-Flyout hinzufügen, indem Sie eine AppBarElementContainer umschließen.</span><span class="sxs-lookup"><span data-stu-id="8b572-182">You can add other controls to a command bar flyout by wrapping them in an AppBarElementContainer.</span></span> <span data-ttu-id="8b572-183">Dadurch können Sie die Steuerelemente wie [DropDownButton]() oder [SplitButton]()hinzugefügt oder Containern wie [StackPanel]() komplexer Benutzeroberflächen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="8b572-183">This lets you add controls like [DropDownButton]() or [SplitButton](), or add containers like [StackPanel]() to create more complex UI.</span></span>

<span data-ttu-id="8b572-184">Um den primären oder sekundären Befehl Sammlungen von einem Befehlsleisten-Flyout hinzugefügt werden, muss ein Element die [ICommandBarElement](/uwp/api/windows.ui.xaml.controls.icommandbarelement) -Schnittstelle implementieren.</span><span class="sxs-lookup"><span data-stu-id="8b572-184">In order to be added to the primary or secondary command collections of a command bar flyout, an element must implement the [ICommandBarElement](/uwp/api/windows.ui.xaml.controls.icommandbarelement) interface.</span></span> <span data-ttu-id="8b572-185">AppBarElementContainer ist ein Wrapper, der diese Schnittstelle implementiert, sodass Sie ein Element zu einer Befehlsleiste hinzufügen können, auch wenn es nicht die Schnittstelle selbst implementieren.</span><span class="sxs-lookup"><span data-stu-id="8b572-185">AppBarElementContainer is a wrapper that implements this interface so you can add an element to a command bar even if it doesn't implement the interface itself.</span></span>

<span data-ttu-id="8b572-186">Hier wird ein AppBarElementContainer verwendet, um zusätzliche Elemente zu einer Befehlsleisten-Flyout hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8b572-186">Here, an AppBarElementContainer is used to add extra elements to a command bar flyout.</span></span> <span data-ttu-id="8b572-187">Die primären Befehle Auswahl an Farben ermöglicht wird ein SplitButton hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="8b572-187">A SplitButton is added to the primary commands to allow selection of colors.</span></span> <span data-ttu-id="8b572-188">StackPanel wird die sekundären Befehle ein komplexeres Layouts für Zoomsteuerelemente zulassen hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="8b572-188">A StackPanel is added to the secondary commands to allow a more complex layout for zoom controls.</span></span>

> [!TIP]
> <span data-ttu-id="8b572-189">Standardmäßig Elemente für die app-Canvas entwickelt möglicherweise nicht dann fehlerhaft in einer Befehlsleiste.</span><span class="sxs-lookup"><span data-stu-id="8b572-189">By default, elements designed for the app canvas might not look right in a command bar.</span></span> <span data-ttu-id="8b572-190">Wenn Sie ein Element mithilfe von AppBarElementContainer hinzufügen, gibt es einige Schritte, die Sie ausführen sollten, um sicherzustellen, das Element, das andere Element auf der Befehl entsprechen:</span><span class="sxs-lookup"><span data-stu-id="8b572-190">When you add an element using AppBarElementContainer, there are some steps you should take to make the element match other command bar elements:</span></span>
>
> - <span data-ttu-id="8b572-191">Überschreiben Sie die Standardpinsel mit [einfache Formatierung](/design/controls-and-patterns/xaml-styles#lightweight-styling) des Elements Hintergrund- und Rand der app-Leistenschaltflächen übereinstimmen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="8b572-191">Override the default brushes with [lightweight styling](/design/controls-and-patterns/xaml-styles#lightweight-styling) to make the element's background and border match the app bar buttons.</span></span>
> - <span data-ttu-id="8b572-192">Anpassen der Größe und Position des Elements.</span><span class="sxs-lookup"><span data-stu-id="8b572-192">Adjust the size and position of the element.</span></span>
> - <span data-ttu-id="8b572-193">Umschließen Sie Symbole in einer Viewbox mit einer Breite und Höhe des 16px.</span><span class="sxs-lookup"><span data-stu-id="8b572-193">Wrap icons in a Viewbox with a Width and Height of 16px.</span></span>

> [!NOTE]
> <span data-ttu-id="8b572-194">Dieses Beispiel zeigt nur die Befehlsleisten-Flyout UI, es nicht den Befehlen implementiert, die angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8b572-194">This example shows only the command bar flyout UI, it does not implement any of the commands that are shown.</span></span> <span data-ttu-id="8b572-195">Weitere Informationen zur Implementierung der Befehle finden Sie unter [Schaltflächen](buttons.md) und [befehlsdesigngrundlagen](../basics/commanding-basics.md).</span><span class="sxs-lookup"><span data-stu-id="8b572-195">For more info about implementing the commands, see [Buttons](buttons.md) and [Command design basics](../basics/commanding-basics.md).</span></span>

![Ein Befehlsleisten-Flyout mit einer Split-Schaltfläche](images/command-bar-flyout-split-button.png)

> _<span data-ttu-id="8b572-197">Ein "Collapsed" Befehlsleisten-Flyout mit einer offenen SplitButton</span><span class="sxs-lookup"><span data-stu-id="8b572-197">A collapsed command bar flyout with an open SplitButton</span></span>_

![Ein Befehlsleisten-Flyout mit komplexen UI](images/command-bar-flyout-custom-ui.png)

> _<span data-ttu-id="8b572-199">Eine erweiterte Befehlsleisten-Flyout mit benutzerdefinierten Zoom UI im Menü ""</span><span class="sxs-lookup"><span data-stu-id="8b572-199">An expanded command bar flyout with custom zoom UI in the menu</span></span>_


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

## <a name="create-a-context-menu-with-secondary-commands-only"></a><span data-ttu-id="8b572-200">Erstellen Sie ein Kontextmenü mit nur sekundäre Befehle</span><span class="sxs-lookup"><span data-stu-id="8b572-200">Create a context menu with secondary commands only</span></span>

<span data-ttu-id="8b572-201">Sie können eine CommandBarFlyout mit nur sekundäre Befehle als [Kontextmenü](menus.md), anstelle einer MenuFlyout verwenden.</span><span class="sxs-lookup"><span data-stu-id="8b572-201">You can use a CommandBarFlyout with only secondary commands as a [context menu](menus.md), in place of a MenuFlyout.</span></span>

![Ein Befehlsleisten-Flyout mit nur sekundäre Befehle](images/command-bar-flyout-context-menu.png)

> _<span data-ttu-id="8b572-203">Befehlsleisten-Flyout als Kontextmenü</span><span class="sxs-lookup"><span data-stu-id="8b572-203">Command bar flyout as a context menu</span></span>_

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

<span data-ttu-id="8b572-204">Sie können auch eine CommandBarFlyout mit einem DropDownButton verwenden, zum Erstellen eines Standardmenüs.</span><span class="sxs-lookup"><span data-stu-id="8b572-204">You can also use a CommandBarFlyout with a DropDownButton to create a standard menu.</span></span>

![Ein Befehlsleisten-Flyout mit als ein Dropdown-Menü "Schaltfläche"](images/command-bar-flyout-dropdown.png)

> _<span data-ttu-id="8b572-206">Ein Dropdown-Menü der Schaltfläche in einem Befehlsleisten-flyout</span><span class="sxs-lookup"><span data-stu-id="8b572-206">A drop down button menu in a command bar flyout</span></span>_

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

## <a name="command-bar-flyouts-for-text-controls"></a><span data-ttu-id="8b572-207">Flyouts auf einer Befehlsleiste für Textsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="8b572-207">Command bar flyouts for text controls</span></span>

<span data-ttu-id="8b572-208">Die [TextCommandBarFlyout](/uwp/api/microsoft.ui.xaml.controls.textcommandbarflyout) ist eine spezielle Befehlsleisten-Flyout, die Befehle zum Bearbeiten von Text enthält.</span><span class="sxs-lookup"><span data-stu-id="8b572-208">The [TextCommandBarFlyout](/uwp/api/microsoft.ui.xaml.controls.textcommandbarflyout) is a specialized command bar flyout that contains commands for editing text.</span></span> <span data-ttu-id="8b572-209">Jedes Textsteuerelement zeigt die TextCommandBarFlyout automatisch als Kontextmenü (Rechtsklick), oder wenn Text markiert ist.</span><span class="sxs-lookup"><span data-stu-id="8b572-209">Each text control shows the TextCommandBarFlyout automatically as a context menu (right-click), or when text is selected.</span></span> <span data-ttu-id="8b572-210">Der Text Befehlsleisten-Flyout passt sich die Textauswahl nur relevante Befehle angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8b572-210">The text command bar flyout adapts to the text selection to only show relevant commands.</span></span>

![Eine reduzierte Text Befehlsleisten-flyout](images/command-bar-flyout-text-selection.png)

> _<span data-ttu-id="8b572-212">Ein Text Befehlsleisten-Flyout auf Textauswahl</span><span class="sxs-lookup"><span data-stu-id="8b572-212">A text command bar flyout on text selection</span></span>_

![Eine erweiterte Text Befehlsleisten-flyout](images/command-bar-flyout-text-full.png)

> _<span data-ttu-id="8b572-214">Eine erweiterte Text Befehlsleisten-flyout</span><span class="sxs-lookup"><span data-stu-id="8b572-214">An expanded text command bar flyout</span></span>_


### <a name="available-commands"></a><span data-ttu-id="8b572-215">Verfügbaren Befehle</span><span class="sxs-lookup"><span data-stu-id="8b572-215">Available commands</span></span>

<span data-ttu-id="8b572-216">Diese Tabelle zeigt die Befehle in einer TextCommandBarFlyout, und wenn diese angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8b572-216">This table shows the commands that are included in a TextCommandBarFlyout, and when they are shown.</span></span>

| <span data-ttu-id="8b572-217">Befehl</span><span class="sxs-lookup"><span data-stu-id="8b572-217">Command</span></span> | <span data-ttu-id="8b572-218">Dargestellt …</span><span class="sxs-lookup"><span data-stu-id="8b572-218">Shown...</span></span> |
| ------- | -------- |
| <span data-ttu-id="8b572-219">Fett</span><span class="sxs-lookup"><span data-stu-id="8b572-219">Bold</span></span> | <span data-ttu-id="8b572-220">Wenn der Text-Steuerelement keine schreibgeschützt (RichEditBox nur) ist.</span><span class="sxs-lookup"><span data-stu-id="8b572-220">when the text control is not read-only (RichEditBox only).</span></span> |
| <span data-ttu-id="8b572-221">Kursiv</span><span class="sxs-lookup"><span data-stu-id="8b572-221">Italic</span></span> | <span data-ttu-id="8b572-222">Wenn der Text-Steuerelement keine schreibgeschützt (RichEditBox nur) ist.</span><span class="sxs-lookup"><span data-stu-id="8b572-222">when the text control is not read-only (RichEditBox only).</span></span> |
| <span data-ttu-id="8b572-223">Unterstreichen</span><span class="sxs-lookup"><span data-stu-id="8b572-223">Underline</span></span> | <span data-ttu-id="8b572-224">Wenn der Text-Steuerelement keine schreibgeschützt (RichEditBox nur) ist.</span><span class="sxs-lookup"><span data-stu-id="8b572-224">when the text control is not read-only (RichEditBox only).</span></span> |
| <span data-ttu-id="8b572-225">Nachweis von Manipulation</span><span class="sxs-lookup"><span data-stu-id="8b572-225">Proofing</span></span> | <span data-ttu-id="8b572-226">Wenn IsSpellCheckEnabled **"true"** ist und falsch geschrieben wird Text ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="8b572-226">when IsSpellCheckEnabled is **true** and misspelled text is selected.</span></span> |
| <span data-ttu-id="8b572-227">Ausschneiden</span><span class="sxs-lookup"><span data-stu-id="8b572-227">Cut</span></span> | <span data-ttu-id="8b572-228">Wenn das Textsteuerelement ist nicht schreibgeschützt, und Text ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="8b572-228">when the text control is not read-only and text is selected.</span></span> |
| <span data-ttu-id="8b572-229">Kopieren</span><span class="sxs-lookup"><span data-stu-id="8b572-229">Copy</span></span> | <span data-ttu-id="8b572-230">Wenn Text ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="8b572-230">when text is selected.</span></span> |
| <span data-ttu-id="8b572-231">Einfügen</span><span class="sxs-lookup"><span data-stu-id="8b572-231">Paste</span></span> | <span data-ttu-id="8b572-232">Wenn das Textsteuerelement ist nicht schreibgeschützt, und die Zwischenablage Inhalt ist.</span><span class="sxs-lookup"><span data-stu-id="8b572-232">when the text control is not read-only and the clipboard has content.</span></span> |
| <span data-ttu-id="8b572-233">Rückgängig machen</span><span class="sxs-lookup"><span data-stu-id="8b572-233">Undo</span></span> | <span data-ttu-id="8b572-234">Wenn eine Aktion, die rückgängig gemacht werden kann.</span><span class="sxs-lookup"><span data-stu-id="8b572-234">when there is an action that can be undone.</span></span> |
| <span data-ttu-id="8b572-235">Alle auswählen</span><span class="sxs-lookup"><span data-stu-id="8b572-235">Select all</span></span> | <span data-ttu-id="8b572-236">Wenn der Text ausgewählt werden können.</span><span class="sxs-lookup"><span data-stu-id="8b572-236">when text can be selected.</span></span> |

### <a name="custom-text-command-bar-flyouts"></a><span data-ttu-id="8b572-237">Benutzerdefinierter Text Flyouts auf einer Befehlsleiste</span><span class="sxs-lookup"><span data-stu-id="8b572-237">Custom text command bar flyouts</span></span>

<span data-ttu-id="8b572-238">TextCommandBarFlyout nicht angepasst werden, und von jedes Textsteuerelement automatisch verwaltet wird.</span><span class="sxs-lookup"><span data-stu-id="8b572-238">TextCommandBarFlyout can't be customized, and is managed automatically by each text control.</span></span> <span data-ttu-id="8b572-239">Allerdings können Sie die standardmäßige TextCommandBarFlyout mit benutzerdefinierten Befehlen ersetzen.</span><span class="sxs-lookup"><span data-stu-id="8b572-239">However, you can replace the default TextCommandBarFlyout with custom commands.</span></span>

- <span data-ttu-id="8b572-240">Um die standardmäßige TextCommandBarFlyout ersetzen, die auf markierten Text angezeigt wird, können Sie erstellen Sie eine benutzerdefinierte CommandBarFlyout (oder andere Flyout-Typ) und weisen sie die **SelectionFlyout** -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="8b572-240">To replace the default TextCommandBarFlyout that's shown on text selection, you can create a custom CommandBarFlyout (or other flyout type) and assign it to the **SelectionFlyout** property.</span></span> <span data-ttu-id="8b572-241">Wenn Sie SelectionFlyout auf **null**festlegen, werden keine Befehle auf Auswahl angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8b572-241">If you set SelectionFlyout to **null**, no commands are shown on selection.</span></span>
- <span data-ttu-id="8b572-242">Um die standardmäßige TextCommandBarFlyout zu ersetzen, die im Kontextmenü angezeigt wird, weisen Sie eine benutzerdefinierte CommandBarFlyout (oder andere Flyout-Typ) der **ContextFlyout** -Eigenschaft auf ein Textsteuerelement.</span><span class="sxs-lookup"><span data-stu-id="8b572-242">To replace the default TextCommandBarFlyout that's shown as the context menu, assign a custom CommandBarFlyout (or other flyout type) to the **ContextFlyout** property on a text control.</span></span> <span data-ttu-id="8b572-243">Wenn Sie ContextFlyout auf **null**festgelegt, wird das Flyout "Menü" angezeigt, die in früheren Versionen des Textsteuerelements anstelle der TextCommandBarFlyout angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8b572-243">If you set ContextFlyout to **null**, the menu flyout shown in previous versions of the text control is shown instead of the TextCommandBarFlyout.</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="8b572-244">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="8b572-244">Get the sample code</span></span>

- <span data-ttu-id="8b572-245">[Beispiel eines XAML-Steuerelementekatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="8b572-245">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>
- [<span data-ttu-id="8b572-246">Beispiel für XAML-Befehle</span><span class="sxs-lookup"><span data-stu-id="8b572-246">XAML Commanding sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=620019)

## <a name="related-articles"></a><span data-ttu-id="8b572-247">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="8b572-247">Related articles</span></span>

- [<span data-ttu-id="8b572-248">Befehlsdesigngrundlagen für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="8b572-248">Command design basics for UWP apps</span></span>](../basics/commanding-basics.md)
- [<span data-ttu-id="8b572-249">CommandBar-Klasse</span><span class="sxs-lookup"><span data-stu-id="8b572-249">CommandBar class</span></span>](https://msdn.microsoft.com/library/windows/apps/dn279427)
