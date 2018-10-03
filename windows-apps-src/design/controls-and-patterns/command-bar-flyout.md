---
author: jwmsft
Description: Command bar flyouts give users inline access to your app's most common tasks.
title: Befehlsleiste flyout
label: Command bar flyout
template: detail.hbs
ms.author: jimwalk
ms.date: 10/2/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
pm-contact: abarlow
design-contact: ksulliv
dev-contact: llongley
doc-status: Draft
ms.localizationpriority: medium
ms.openlocfilehash: ed17299051ae7da32f238eb57876b81597c8effa
ms.sourcegitcommit: 1938851dc132c60348f9722daf994b86f2ead09e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "4258513"
---
# <a name="command-bar-flyout"></a><span data-ttu-id="27c35-103">Befehlsleiste flyout</span><span class="sxs-lookup"><span data-stu-id="27c35-103">Command bar flyout</span></span>

<span data-ttu-id="27c35-104">Das Befehlsleiste Flyout können Sie Benutzer einfachen Zugriff auf allgemeine Aufgaben bereitstellen, indem Befehle in einem schwebenden Symbolleisten im Zusammenhang mit einem Element auf die UI-Canvas angezeigt.</span><span class="sxs-lookup"><span data-stu-id="27c35-104">The command bar flyout lets you provide users with easy access to common tasks by showing commands in a floating toolbar related to an element on your UI canvas.</span></span>

![Eine erweiterte Text Befehlsleiste-flyout](images/command-bar-flyout-text-full.png)

> <span data-ttu-id="27c35-106">Weitere Informationen finden Sie unter [Flyouts](../controls-and-patterns/dialogs-and-flyouts/flyouts.md), [Menüs und Kontextmenüs](menus.md)und [Befehlsleisten](app-bars.md).</span><span class="sxs-lookup"><span data-stu-id="27c35-106">For related info, see [Flyouts](../controls-and-patterns/dialogs-and-flyouts/flyouts.md), [Menus and context menus](menus.md), and [Command bars](app-bars.md).</span></span>

<span data-ttu-id="27c35-107">Wie [CommandBar](app-bars.md)hat CommandBarFlyout **PrimaryCommands** und **"secondarycommands"** Eigenschaften, mit denen Sie Befehle hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="27c35-107">Like [CommandBar](app-bars.md), CommandBarFlyout has **PrimaryCommands** and **SecondaryCommands** properties you can use to add commands.</span></span> <span data-ttu-id="27c35-108">Sie können entweder Sammlung oder beide Befehle versehen.</span><span class="sxs-lookup"><span data-stu-id="27c35-108">You can place commands in either collection, or both.</span></span> <span data-ttu-id="27c35-109">Wann und wie die primären und sekundären Befehle angezeigt werden, hängt von den Anzeigemodus.</span><span class="sxs-lookup"><span data-stu-id="27c35-109">When and how the primary and secondary commands are displayed depends on the display mode.</span></span>

<span data-ttu-id="27c35-110">Das Befehlsleiste Flyout verfügt über zwei Anzeigemodi: *reduziert* und *Erweitert*.</span><span class="sxs-lookup"><span data-stu-id="27c35-110">The command bar flyout has two display modes: *collapsed* and *expanded*.</span></span>

- <span data-ttu-id="27c35-111">Im Modus "Collapsed" werden nur die primären Befehle angezeigt.</span><span class="sxs-lookup"><span data-stu-id="27c35-111">In the collapsed mode, only the primary commands are shown.</span></span> <span data-ttu-id="27c35-112">Hat der Befehlsleiste Flyout primären und sekundären Befehle, eine "Schaltfläche" Weitere, dargestellt durch Auslassungspunkte \ [• • •] wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="27c35-112">If your command bar flyout has both primary and secondary commands, a "see more" button, which is represented by an ellipsis \[•••\], is displayed.</span></span> <span data-ttu-id="27c35-113">Dadurch wird den Benutzer den Zugriff auf die sekundären Befehle Abrufen von erweiterten Modus wechselt.</span><span class="sxs-lookup"><span data-stu-id="27c35-113">This lets the user get access to the secondary commands by transitioning to expanded mode.</span></span>
- <span data-ttu-id="27c35-114">Im erweiterten Modus werden die primären und sekundären Befehle angezeigt.</span><span class="sxs-lookup"><span data-stu-id="27c35-114">In the expanded mode, both the primary and secondary commands are shown.</span></span> <span data-ttu-id="27c35-115">(Wenn das Steuerelement nur sekundäre Elemente verfügt, werden sie in einer Weise ähnelt dem MenuFlyout-Steuerelement angezeigt.)</span><span class="sxs-lookup"><span data-stu-id="27c35-115">(If the control has only secondary items, they are shown in a way similar to the MenuFlyout control.)</span></span>

| **<span data-ttu-id="27c35-116">Abrufen der Windows-UI-Bibliothek</span><span class="sxs-lookup"><span data-stu-id="27c35-116">Get the Windows UI Library</span></span>** |
| - |
| <span data-ttu-id="27c35-117">Dieses Steuerelement ist Bestandteil der Windows-UI-Bibliothek, NuGet-Paket, das neue Steuerelemente und UI-Features für UWP-apps enthält.</span><span class="sxs-lookup"><span data-stu-id="27c35-117">This control is included as part of the Windows UI Library, a NuGet package that contains new controls and UI features for UWP apps.</span></span> <span data-ttu-id="27c35-118">Weitere Informationen, einschließlich installationsanweisungen finden Sie die [Übersicht über die Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).</span><span class="sxs-lookup"><span data-stu-id="27c35-118">For more info, including installation instructions, see the [Windows UI Library overview](https://docs.microsoft.com/uwp/toolkits/winui/).</span></span> |

| **<span data-ttu-id="27c35-119">Plattform-APIs</span><span class="sxs-lookup"><span data-stu-id="27c35-119">Platform APIs</span></span>** | **<span data-ttu-id="27c35-120">Windows-UI-Bibliothek APIs</span><span class="sxs-lookup"><span data-stu-id="27c35-120">Windows UI Library APIs</span></span>** |
| - | - |
| <span data-ttu-id="27c35-121">[CommandBarFlyout-Klasse](/uwp/api/windows.ui.xaml.controls.commandbarflyout)"," [TextCommandBarFlyout Klasse](/uwp/api/windows.ui.xaml.controls.textcommandbarflyout)"," [AppBarButton-Klasse](/uwp/api/windows.ui.xaml.controls.appbarbutton)"," [Klasse "appbartogglebutton"](/uwp/api/windows.ui.xaml.controls.appbartogglebutton)"," [Klasse "appbarseparator"](/uwp/api/windows.ui.xaml.controls.appbarseparator)</span><span class="sxs-lookup"><span data-stu-id="27c35-121">[CommandBarFlyout class](/uwp/api/windows.ui.xaml.controls.commandbarflyout), [TextCommandBarFlyout class](/uwp/api/windows.ui.xaml.controls.textcommandbarflyout), [AppBarButton class](/uwp/api/windows.ui.xaml.controls.appbarbutton), [AppBarToggleButton class](/uwp/api/windows.ui.xaml.controls.appbartogglebutton), [AppBarSeparator class](/uwp/api/windows.ui.xaml.controls.appbarseparator)</span></span> | <span data-ttu-id="27c35-122">[CommandBarFlyout-Klasse](/uwp/api/microsoft.ui.xaml.controls.commandbarflyout), [TextCommandBarFlyout-Klasse](/uwp/api/microsoft.ui.xaml.controls.textcommandbarflyout)</span><span class="sxs-lookup"><span data-stu-id="27c35-122">[CommandBarFlyout class](/uwp/api/microsoft.ui.xaml.controls.commandbarflyout), [TextCommandBarFlyout class](/uwp/api/microsoft.ui.xaml.controls.textcommandbarflyout)</span></span> |

## <a name="is-this-the-right-control"></a><span data-ttu-id="27c35-123">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="27c35-123">Is this the right control?</span></span>

<span data-ttu-id="27c35-124">Verwenden Sie das CommandBarFlyout-Steuerelement, um eine Sammlung von Befehlen für dem Benutzer, z. B. Schaltflächen und Menüelementen im Kontext eines Elements auf der app-Canvas anzeigen.</span><span class="sxs-lookup"><span data-stu-id="27c35-124">Use the CommandBarFlyout control to show a collection of commands to the user, such as buttons and menu items, in the context of an element on the app canvas.</span></span>

<span data-ttu-id="27c35-125">Die TextCommandBarFlyout zeigt Text-Befehlen im TextBlock, TextBox, RichEditBox, RichTextBlock und PasswordBox-Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="27c35-125">The TextCommandBarFlyout displays text commands in TextBox, TextBlock, RichEditBox, RichTextBlock, and PasswordBox controls.</span></span> <span data-ttu-id="27c35-126">Die Befehle sind für die aktuelle Textauswahl automatisch entsprechend konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="27c35-126">The commands are automatically configured appropriately to the current text selection.</span></span> <span data-ttu-id="27c35-127">Verwenden Sie eine CommandBarFlyout, um die Standard-Text-Befehle auf Text-Steuerelemente ersetzen.</span><span class="sxs-lookup"><span data-stu-id="27c35-127">Use a CommandBarFlyout to replace the default text commands on text controls.</span></span>

<span data-ttu-id="27c35-128">Um kontextbezogene anzuzeigen führen Sie die Befehle auf Listenelemente die Anleitung im [Contextual Befehle für Sammlungen und Listen](collection-commanding.md).</span><span class="sxs-lookup"><span data-stu-id="27c35-128">To show contextual commands on list items follow the guidance in [Contextual commanding for collections and lists](collection-commanding.md).</span></span>

### <a name="commandbarflyout-vs-menuflyout"></a><span data-ttu-id="27c35-129">CommandBarFlyout Vs MenuFlyout</span><span class="sxs-lookup"><span data-stu-id="27c35-129">CommandBarFlyout vs MenuFlyout</span></span>

<span data-ttu-id="27c35-130">Um Befehle in einem Kontextmenü angezeigt werden, können Sie CommandBarFlyout oder MenuFlyout verwenden.</span><span class="sxs-lookup"><span data-stu-id="27c35-130">To show commands in a context menu, you can use CommandBarFlyout or MenuFlyout.</span></span> <span data-ttu-id="27c35-131">CommandBarFlyout wird empfohlen, da es mehr Funktionen als MenuFlyout bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="27c35-131">We recommend CommandBarFlyout because it provides more functionality than MenuFlyout.</span></span> <span data-ttu-id="27c35-132">Sie können CommandBarFlyout mit nur sekundäre Befehle verwenden, um das Verhalten abzurufen und Darstellung des ein MenuFlyout oder verwenden Sie das vollständige Befehlsleiste Flyout mit primären und sekundären Befehlen.</span><span class="sxs-lookup"><span data-stu-id="27c35-132">You can use CommandBarFlyout with only secondary commands to get the behavior and look of a MenuFlyout, or use the full command bar flyout with both primary and secondary commands.</span></span>

## <a name="examples"></a><span data-ttu-id="27c35-133">Beispiele</span><span class="sxs-lookup"><span data-stu-id="27c35-133">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="27c35-134">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="27c35-134">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="27c35-135">Wenn Sie die <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> -app installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/CommandBarFlyout">die app zu öffnen und finden Sie unter der CommandBarFlyout in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="27c35-135">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/CommandBarFlyout">open the app and see the CommandBarFlyout in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="27c35-136">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="27c35-136">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="27c35-137">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="27c35-137">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="proactive-vs-reactive-invocation"></a><span data-ttu-id="27c35-138">Im Vergleich zu Zeiten Aufruf proaktive</span><span class="sxs-lookup"><span data-stu-id="27c35-138">Proactive vs. reactive invocation</span></span>

<span data-ttu-id="27c35-139">Es gibt in der Regel zwei Möglichkeiten zum Aufrufen eines Flyouts oder Menü, die mit einem Element auf die UI-Canvas verknüpft ist: _proaktive aufrufen_ und _reaktive Aufruf_.</span><span class="sxs-lookup"><span data-stu-id="27c35-139">There are typically two ways to invoke a flyout or menu that's associated with an element on your UI canvas: _proactive invocation_ and _reactive invocation_.</span></span>

<span data-ttu-id="27c35-140">Proaktive Aufruf werden Befehle automatisch angezeigt, wenn der Benutzer mit dem Element interagiert, die die Befehle zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="27c35-140">In proactive invocation, commands appear automatically when the user interacts with the item that the commands are associated with.</span></span> <span data-ttu-id="27c35-141">Z. B. möglicherweise Formatierungsbefehle Text eingeblendet, wenn der Benutzer Text in einem Textfeld auswählt.</span><span class="sxs-lookup"><span data-stu-id="27c35-141">For example, text formatting commands might pop up when the user selects text in a text box.</span></span> <span data-ttu-id="27c35-142">In diesem Fall wird das Befehlsleiste Flyout Fokus nicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="27c35-142">In this case, the command bar flyout does not take focus.</span></span> <span data-ttu-id="27c35-143">Stattdessen zeigt sie geeignete Befehle nahe dem Element, dem der Benutzer mit interagiert.</span><span class="sxs-lookup"><span data-stu-id="27c35-143">Instead, it presents relevant commands close to the item the user is interacting with.</span></span> <span data-ttu-id="27c35-144">Wenn der Benutzer mit den Befehlen interagieren nicht, werden sie geschlossen.</span><span class="sxs-lookup"><span data-stu-id="27c35-144">If the user doesn't interact with the commands, they are dismissed.</span></span>

<span data-ttu-id="27c35-145">Reaktive Aufruf werden Befehle in Reaktion auf eine explizite Benutzeraktion angezeigt, die Befehle anfordern. Beispiel: eine mit der rechten Maustaste.</span><span class="sxs-lookup"><span data-stu-id="27c35-145">In reactive invocation, commands are shown in response to an explicit user action to request the commands; for example, a right-click.</span></span> <span data-ttu-id="27c35-146">Dies entspricht dem herkömmliche Konzept eines [Kontextmenüs](menus.md).</span><span class="sxs-lookup"><span data-stu-id="27c35-146">This corresponds to the traditional concept of a [context menu](menus.md).</span></span>

<span data-ttu-id="27c35-147">Sie können die CommandBarFlyout in Weise oder sogar eine Mischung der beiden verwenden.</span><span class="sxs-lookup"><span data-stu-id="27c35-147">You can use the CommandBarFlyout in either way, or even a mixture of the two.</span></span>

## <a name="create-a-command-bar-flyout"></a><span data-ttu-id="27c35-148">Erstellen Sie ein Befehlsleiste-flyout</span><span class="sxs-lookup"><span data-stu-id="27c35-148">Create a command bar flyout</span></span>

> <span data-ttu-id="27c35-149">**Vorschau**: CommandBarFlyout erfordert die [neuesten Windows 10 Insider Preview-Build und SDK](https://insider.windows.com/for-developers/) oder der [Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).</span><span class="sxs-lookup"><span data-stu-id="27c35-149">**Preview**: CommandBarFlyout requires the [latest Windows 10 Insider Preview build and SDK](https://insider.windows.com/for-developers/) or the [Windows UI Library](https://docs.microsoft.com/uwp/toolkits/winui/).</span></span>

<span data-ttu-id="27c35-150">In diesem Beispiel wird veranschaulicht, wie ein Befehlsleiste Flyout erstellen und verwenden sie proaktiv und reaktiv.</span><span class="sxs-lookup"><span data-stu-id="27c35-150">This example shows how to create a command bar flyout and use it both proactively and reactively.</span></span> <span data-ttu-id="27c35-151">Wenn das Bild getippt wird, wird das Flyout im Modus "Collapsed" angezeigt.</span><span class="sxs-lookup"><span data-stu-id="27c35-151">When the image is tapped, the flyout is shown in its collapsed mode.</span></span> <span data-ttu-id="27c35-152">Wenn als Kontextmenü angezeigt wird, wird das Flyout im erweiterten Modus angezeigt.</span><span class="sxs-lookup"><span data-stu-id="27c35-152">When shown as a context menu, the flyout is shown in its expanded mode.</span></span> <span data-ttu-id="27c35-153">In beiden Fällen kann der Benutzer erweitern oder reduzieren das Flyout, nachdem er geöffnet wird.</span><span class="sxs-lookup"><span data-stu-id="27c35-153">In either case, the user can expand or collapse the flyout after it's opened.</span></span>

:::row:::
    :::column:::
        A collapsed command bar flyout<br/>
        ![Example of a collapsed command bar flyout](images/command-bar-flyout-img-collapsed.png)
    :::column-end:::
    :::column:::
        An expanded command bar flyout<br/>
        ![Example of an expanded command bar flyout](images/command-bar-flyout-img-expanded.png)
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

### <a name="show-commands-proactively"></a><span data-ttu-id="27c35-154">Befehle proaktiv anzeigen</span><span class="sxs-lookup"><span data-stu-id="27c35-154">Show commands proactively</span></span>

<span data-ttu-id="27c35-155">Wenn Sie Kontextbefehlen proaktiv angezeigt wird, sollte nur die primären Befehle standardmäßig angezeigt werden (die Leiste-Flyout der Befehl sollte reduziert werden).</span><span class="sxs-lookup"><span data-stu-id="27c35-155">When you show contextual commands proactively, only the primary commands should be shown by default (the command bar flyout should be collapsed).</span></span> <span data-ttu-id="27c35-156">Platzieren Sie die wichtigsten Befehle, in die primäre Befehle Sammlung, und klicken Sie auf zusätzliche Befehle, die normalerweise in einem Kontextmenü in die sekundären Befehle Auflistung würde.</span><span class="sxs-lookup"><span data-stu-id="27c35-156">Place the most important commands in the primary commands collection, and additional commands that would traditionally go in a context menu into the secondary commands collection.</span></span>

<span data-ttu-id="27c35-157">Um Befehle proaktiv angezeigt werden soll, behandeln Sie in der Regel das [Klicken](/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.click) oder [Tapped](/uwp/api/windows.ui.xaml.uielement.tapped) -Ereignis, um das Befehlsleiste Flyout anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="27c35-157">To proactively show commands, you typically handle the [Click](/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.click) or [Tapped](/uwp/api/windows.ui.xaml.uielement.tapped) event to show the command bar flyout.</span></span> <span data-ttu-id="27c35-158">Legen Sie das Flyout [ShowMode](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.showmode) **vorübergehende** oder **TransientWithDismissOnPointerMoveAway** , um das Flyout im Modus "Collapsed" zu öffnen, ohne den Fokus fest.</span><span class="sxs-lookup"><span data-stu-id="27c35-158">Set the flyout's [ShowMode](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.showmode) to **Transient** or **TransientWithDismissOnPointerMoveAway** to open the flyout in its collapsed mode without taking focus.</span></span>

<span data-ttu-id="27c35-159">Ab Windows 10 Insider Preview, Text-Steuerelemente verfügen über eine **SelectionFlyout** -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="27c35-159">Starting in the Windows 10 Insider Preview, text controls have a **SelectionFlyout** property.</span></span> <span data-ttu-id="27c35-160">Wenn Sie diese Eigenschaft ein Flyout zuordnen, wird er automatisch angezeigt, wenn Text markiert ist.</span><span class="sxs-lookup"><span data-stu-id="27c35-160">When you assign a flyout to this property, it is automatically shown when text is selected.</span></span>

### <a name="show-commands-reactively"></a><span data-ttu-id="27c35-161">Befehle reaktiv anzeigen</span><span class="sxs-lookup"><span data-stu-id="27c35-161">Show commands reactively</span></span>

<span data-ttu-id="27c35-162">Wenn Sie Kontextbefehlen reaktiv, als Kontextmenü angezeigt wird, werden die sekundären Befehle standardmäßig angezeigt (die Leiste-Flyout der Befehl sollte erweitert werden).</span><span class="sxs-lookup"><span data-stu-id="27c35-162">When you show contextual commands reactively, as a context menu, the secondary commands are shown by default (the command bar flyout should be expanded).</span></span> <span data-ttu-id="27c35-163">In diesem Fall wird möglicherweise das Befehlsleiste Flyout primären und sekundären Befehle oder nur sekundäre Befehle.</span><span class="sxs-lookup"><span data-stu-id="27c35-163">In this case, the command bar flyout might have both primary and secondary commands, or secondary commands only.</span></span>

<span data-ttu-id="27c35-164">Um Befehle in einem Kontextmenü anzuzeigen, weisen Sie in der Regel das Flyout der [ContextFlyout](/uwp/api/windows.ui.xaml.uielement.contextflyout) -Eigenschaft eines Benutzeroberflächenelements.</span><span class="sxs-lookup"><span data-stu-id="27c35-164">To show commands in a context menu, you typically assign the flyout to the [ContextFlyout](/uwp/api/windows.ui.xaml.uielement.contextflyout) property of a UI element.</span></span> <span data-ttu-id="27c35-165">Auf diese Weise wird das Flyout Öffnen des Elements behandelt, und Sie müssen nichts weiter tun.</span><span class="sxs-lookup"><span data-stu-id="27c35-165">This way, opening the flyout is handled by the element, and you don't need to do anything more.</span></span>

<span data-ttu-id="27c35-166">Wenn Sie verarbeiten das Flyout (z. B. auf ein Ereignis [RightTapped](/uwp/api/windows.ui.xaml.uielement.righttapped) ) angezeigt, die das Flyout [ShowMode](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.showmode) in **Standard** , öffnen Sie das Flyout im erweiterten Modus und weisen Sie ihm den Fokus.</span><span class="sxs-lookup"><span data-stu-id="27c35-166">If you handle showing the flyout yourself (for example, on a [RightTapped](/uwp/api/windows.ui.xaml.uielement.righttapped) event), set the the flyout's [ShowMode](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.showmode) to **Standard** to open the flyout in its expanded mode and give it focus.</span></span>

> [!TIP]
> <span data-ttu-id="27c35-167">Weitere Informationen zu den Optionen beim Anzeigen von einem Flyout und zur Platzierung von das Flyout zu steuern finden Sie unter [Flyouts](../controls-and-patterns/dialogs-and-flyouts/flyouts.md).</span><span class="sxs-lookup"><span data-stu-id="27c35-167">For more info about options when showing a flyout and how to control placement of the flyout, see [Flyouts](../controls-and-patterns/dialogs-and-flyouts/flyouts.md).</span></span>

## <a name="commands-and-content"></a><span data-ttu-id="27c35-168">Befehle und Inhalt</span><span class="sxs-lookup"><span data-stu-id="27c35-168">Commands and content</span></span>

<span data-ttu-id="27c35-169">Das CommandBarFlyout-Steuerelement verfügt über 2 Eigenschaften Sie Befehle und Inhalte hinzufügen können: [PrimaryCommands](/uwp/api/windows.ui.xaml.controls.commandbarflyout.primarycommands) und ["secondarycommands"](/uwp/api/windows.ui.xaml.controls.commandbarflyout.secondarycommands).</span><span class="sxs-lookup"><span data-stu-id="27c35-169">The CommandBarFlyout control has 2 properties you can use to add commands and content: [PrimaryCommands](/uwp/api/windows.ui.xaml.controls.commandbarflyout.primarycommands) and [SecondaryCommands](/uwp/api/windows.ui.xaml.controls.commandbarflyout.secondarycommands).</span></span>

<span data-ttu-id="27c35-170">Befehlsleistenelemente werden standardmäßig der **PrimaryCommands**-Sammlung hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="27c35-170">By default, command bar items are added to the **PrimaryCommands** collection.</span></span> <span data-ttu-id="27c35-171">Diese Befehle werden angezeigt, in der Befehlsleiste und sowohl die "Collapsed" auch im erweiterten Modus sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="27c35-171">These commands are shown in the command bar and are visible in both the collapsed and expanded modes.</span></span> <span data-ttu-id="27c35-172">Im Gegensatz zu CommandBar primäre Befehle nicht automatisch Überlauf zu die sekundären Befehle und möglicherweise abgeschnitten.</span><span class="sxs-lookup"><span data-stu-id="27c35-172">Unlike CommandBar, primary commands do not automatically overflow to the secondary commands and might be truncated.</span></span>

<span data-ttu-id="27c35-173">Sie können auch Befehle zur Auflistung **"secondarycommands"** hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="27c35-173">You can also add commands to the **SecondaryCommands** collection.</span></span> <span data-ttu-id="27c35-174">Sekundäre Befehle werden im Menü Teil des Steuerelements angezeigt und sind nur im erweiterten Modus sichtbar.</span><span class="sxs-lookup"><span data-stu-id="27c35-174">Secondary commands are shown in the menu portion of the control and are visible only in the expanded mode.</span></span>

### <a name="app-bar-buttons"></a><span data-ttu-id="27c35-175">App-Leistenschaltflächen</span><span class="sxs-lookup"><span data-stu-id="27c35-175">App bar buttons</span></span>

<span data-ttu-id="27c35-176">Sie können die PrimaryCommands und "secondarycommands" direkt mit Steuerelementen [AppBarButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarbutton.aspx), [AppBarToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbartogglebutton.aspx)und [AppBarSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarseparator.aspx) auffüllen.</span><span class="sxs-lookup"><span data-stu-id="27c35-176">You can populate the PrimaryCommands and SecondaryCommands directly with [AppBarButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarbutton.aspx), [AppBarToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbartogglebutton.aspx), and [AppBarSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarseparator.aspx) controls.</span></span>

<span data-ttu-id="27c35-177">Die Steuerelemente für die App-Leistenschaltfläche zeichnen sich durch ein Symbol und eine Textbeschriftung aus.</span><span class="sxs-lookup"><span data-stu-id="27c35-177">The app bar button controls are characterized by an icon and text label.</span></span> <span data-ttu-id="27c35-178">Diese Steuerelemente sind für die Verwendung in Befehlsleisten optimiert, und ihre Darstellung ändert, je nachdem, ob das Steuerelement in der Befehlsleiste oder im Überlaufmenü angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="27c35-178">These controls are optimized for use in a command bar, and their appearance changes depending on whether the control is shown in the command bar or the overflow menu.</span></span>

- <span data-ttu-id="27c35-179">App-Leistenschaltflächen als primäre Befehle verwendet werden in der Befehlsleiste mit nur ihre Symbol angezeigt. die Beschriftung wird nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="27c35-179">App bar buttons used as primary commands are shown in the command bar with only their icon; the text label is not shown.</span></span> <span data-ttu-id="27c35-180">Es wird empfohlen, dass Sie eine QuickInfo verwenden, um einen beschreibenden Text für den Befehl anzuzeigen wie hier gezeigt.</span><span class="sxs-lookup"><span data-stu-id="27c35-180">We recommend that you use a tooltip to show a text description of the command, as shown here.</span></span>
    ```xaml
    <AppBarButton Icon="Copy" ToolTipService.ToolTip="Copy"/>
    ```
- <span data-ttu-id="27c35-181">App-Leistenschaltflächen als sekundäre Befehle verwendet werden im Menü mit der Bezeichnung und die Symbol sichtbar angezeigt.</span><span class="sxs-lookup"><span data-stu-id="27c35-181">App bar buttons used as secondary commands are shown in the menu, with both the label and icon visible.</span></span>

### <a name="other-content"></a><span data-ttu-id="27c35-182">Andere Inhalte</span><span class="sxs-lookup"><span data-stu-id="27c35-182">Other content</span></span>

<span data-ttu-id="27c35-183">Sie können ein Befehlsleiste Flyout eine AppBarElementContainer umschließen andere Steuerelemente hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="27c35-183">You can add other controls to a command bar flyout by wrapping them in an AppBarElementContainer.</span></span> <span data-ttu-id="27c35-184">Auf diese Weise können Sie die Steuerelemente wie [DropDownButton]() oder [SplitButton]()hinzugefügt oder Containern wie [StackPanel]() um komplexere Benutzeroberfläche zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="27c35-184">This lets you add controls like [DropDownButton]() or [SplitButton](), or add containers like [StackPanel]() to create more complex UI.</span></span>

> [!NOTE]
> <span data-ttu-id="27c35-185">Um die primären oder sekundären Befehl Sammlungen Befehlsleiste Flyout hinzugefügt werden, muss ein Element die [ICommandBarElement](/uwp/api/windows.ui.xaml.controls.icommandbarelement) -Schnittstelle implementieren.</span><span class="sxs-lookup"><span data-stu-id="27c35-185">In order to be added to the primary or secondary command collections of a command bar flyout, an element must implement the [ICommandBarElement](/uwp/api/windows.ui.xaml.controls.icommandbarelement) interface.</span></span> <span data-ttu-id="27c35-186">AppBarElementContainer ist ein Wrapper, der diese Schnittstelle implementiert, sodass Sie ein Element zu einer Befehlsleiste hinzufügen können, selbst wenn sie nicht die Schnittstelle selbst implementiert.</span><span class="sxs-lookup"><span data-stu-id="27c35-186">AppBarElementContainer is a wrapper that implements this interface so you can add an element to a command bar even if it doesn't implement the interface itself.</span></span>

<span data-ttu-id="27c35-187">Hier wird ein AppBarElementContainer verwendet, um zusätzliche Elemente ein Befehlsleiste Flyout hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="27c35-187">Here, an AppBarElementContainer is used to add extra elements to a command bar flyout.</span></span> <span data-ttu-id="27c35-188">Die primären Befehle Auswahl an Farben ermöglicht wird ein SplitButton hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="27c35-188">A SplitButton is added to the primary commands to allow selection of colors.</span></span> <span data-ttu-id="27c35-189">StackPanel wird die sekundären Befehle ein komplexeres Layouts für Zoomsteuerelemente zulassen hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="27c35-189">A StackPanel is added to the secondary commands to allow a more complex layout for zoom controls.</span></span>

> [!NOTE]
> <span data-ttu-id="27c35-190">Dieses Beispiel zeigt nur dem Befehlsleiste Flyout UI, sie keine Befehle implementiert, die angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="27c35-190">This example shows only the command bar flyout UI, it does not implement any of the commands that are shown.</span></span> <span data-ttu-id="27c35-191">Weitere Informationen zur Implementierung der Befehle finden Sie unter [Schaltflächen](buttons.md) und [befehlsdesigngrundlagen](../basics/commanding-basics.md).</span><span class="sxs-lookup"><span data-stu-id="27c35-191">For more info about implementing the commands, see [Buttons](buttons.md) and [Command design basics](../basics/commanding-basics.md).</span></span>

:::row:::
    :::column:::
        A collapsed command bar flyout with an open SplitButton<br/>
        ![A command bar flyout with a split button](images/command-bar-flyout-split-button.png)
    :::column-end:::
    :::column:::
        An expanded command bar flyout with custom zoom UI in the menu<br/>
        ![A command bar flyout with complex UI](images/command-bar-flyout-complex-ui.png)
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

## <a name="create-a-context-menu-with-secondary-commands-only"></a><span data-ttu-id="27c35-192">Erstellen Sie ein Kontextmenü mit nur sekundäre Befehle</span><span class="sxs-lookup"><span data-stu-id="27c35-192">Create a context menu with secondary commands only</span></span>

<span data-ttu-id="27c35-193">Sie können eine CommandBarFlyout mit nur sekundäre Befehle als [Kontextmenü](menus.md), anstelle einer MenuFlyout verwenden.</span><span class="sxs-lookup"><span data-stu-id="27c35-193">You can use a CommandBarFlyout with only secondary commands as a [context menu](menus.md), in place of a MenuFlyout.</span></span>

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

<span data-ttu-id="27c35-195">Sie können auch eine CommandBarFlyout mit einem DropDownButton verwenden, zum Erstellen eines Standardmenüs.</span><span class="sxs-lookup"><span data-stu-id="27c35-195">You can also use a CommandBarFlyout with a DropDownButton to create a standard menu.</span></span>

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

## <a name="command-bar-flyouts-for-text-controls"></a><span data-ttu-id="27c35-197">Flyouts auf einer Befehlsleiste für Textsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="27c35-197">Command bar flyouts for text controls</span></span>

<span data-ttu-id="27c35-198">Die [TextCommandBarFlyout](/uwp/api/microsoft.ui.xaml.controls.textcommandbarflyout) ist ein spezielles Befehlsleiste Flyout, die Befehle zum Bearbeiten von Text enthält.</span><span class="sxs-lookup"><span data-stu-id="27c35-198">The [TextCommandBarFlyout](/uwp/api/microsoft.ui.xaml.controls.textcommandbarflyout) is a specialized command bar flyout that contains commands for editing text.</span></span> <span data-ttu-id="27c35-199">Jedes Textsteuerelement zeigt die TextCommandBarFlyout automatisch als Kontextmenü (Rechtsklick), oder wenn Text markiert ist.</span><span class="sxs-lookup"><span data-stu-id="27c35-199">Each text control shows the TextCommandBarFlyout automatically as a context menu (right-click), or when text is selected.</span></span> <span data-ttu-id="27c35-200">Die Leiste-Flyout der Text-Befehl passt sich die Textauswahl nur relevante Befehle angezeigt.</span><span class="sxs-lookup"><span data-stu-id="27c35-200">The text command bar flyout adapts to the text selection to only show relevant commands.</span></span>

:::row:::
    :::column:::
        A text command bar flyout on text selection<br/>
        ![A collapsed text command bar flyout](images/command-bar-flyout-text-selection.png)
    :::column-end:::
    :::column:::
        An expanded text command bar flyout<br/>
        ![An expanded text command bar flyout](images/command-bar-flyout-text-full.png)
    :::column-end:::
:::row-end:::

### <a name="available-commands"></a><span data-ttu-id="27c35-201">Verfügbaren Befehle</span><span class="sxs-lookup"><span data-stu-id="27c35-201">Available commands</span></span>

<span data-ttu-id="27c35-202">Diese Tabelle zeigt die Befehle in einer TextCommandBarFlyout, und wenn diese angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="27c35-202">This table shows the commands that are included in a TextCommandBarFlyout, and when they are shown.</span></span>

| <span data-ttu-id="27c35-203">Befehl</span><span class="sxs-lookup"><span data-stu-id="27c35-203">Command</span></span> | <span data-ttu-id="27c35-204">Dargestellt …</span><span class="sxs-lookup"><span data-stu-id="27c35-204">Shown...</span></span> |
| ------- | -------- |
| <span data-ttu-id="27c35-205">Fett</span><span class="sxs-lookup"><span data-stu-id="27c35-205">Bold</span></span> | <span data-ttu-id="27c35-206">Wenn das Steuerelement keine schreibgeschützt (RichEditBox nur) ist.</span><span class="sxs-lookup"><span data-stu-id="27c35-206">when the text control is not read-only (RichEditBox only).</span></span> |
| <span data-ttu-id="27c35-207">Kursiv</span><span class="sxs-lookup"><span data-stu-id="27c35-207">Italic</span></span> | <span data-ttu-id="27c35-208">Wenn das Steuerelement keine schreibgeschützt (RichEditBox nur) ist.</span><span class="sxs-lookup"><span data-stu-id="27c35-208">when the text control is not read-only (RichEditBox only).</span></span> |
| <span data-ttu-id="27c35-209">Unterstreichen</span><span class="sxs-lookup"><span data-stu-id="27c35-209">Underline</span></span> | <span data-ttu-id="27c35-210">Wenn das Steuerelement keine schreibgeschützt (RichEditBox nur) ist.</span><span class="sxs-lookup"><span data-stu-id="27c35-210">when the text control is not read-only (RichEditBox only).</span></span> |
| <span data-ttu-id="27c35-211">Nachweis von Manipulation</span><span class="sxs-lookup"><span data-stu-id="27c35-211">Proofing</span></span> | <span data-ttu-id="27c35-212">Wenn IsSpellCheckEnabled **"true ist"** und falsch geschrieben wird Text ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="27c35-212">when IsSpellCheckEnabled is **true** and misspelled text is selected.</span></span> |
| <span data-ttu-id="27c35-213">Ausschneiden</span><span class="sxs-lookup"><span data-stu-id="27c35-213">Cut</span></span> | <span data-ttu-id="27c35-214">Wenn das Text-Steuerelement ist nicht schreibgeschützt, und Text ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="27c35-214">when the text control is not read-only and text is selected.</span></span> |
| <span data-ttu-id="27c35-215">Kopieren</span><span class="sxs-lookup"><span data-stu-id="27c35-215">Copy</span></span> | <span data-ttu-id="27c35-216">Wenn Text ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="27c35-216">when text is selected.</span></span> |
| <span data-ttu-id="27c35-217">Einfügen</span><span class="sxs-lookup"><span data-stu-id="27c35-217">Paste</span></span> | <span data-ttu-id="27c35-218">Wenn das Text-Steuerelement ist nicht schreibgeschützt, und die Zwischenablage Inhalt ist.</span><span class="sxs-lookup"><span data-stu-id="27c35-218">when the text control is not read-only and the clipboard has content.</span></span> |
| <span data-ttu-id="27c35-219">Rückgängig machen</span><span class="sxs-lookup"><span data-stu-id="27c35-219">Undo</span></span> | <span data-ttu-id="27c35-220">Wenn eine Aktion, die rückgängig gemacht werden kann.</span><span class="sxs-lookup"><span data-stu-id="27c35-220">when there is an action that can be undone.</span></span> |
| <span data-ttu-id="27c35-221">Alle auswählen</span><span class="sxs-lookup"><span data-stu-id="27c35-221">Select all</span></span> | <span data-ttu-id="27c35-222">Wenn Text ausgewählt werden können.</span><span class="sxs-lookup"><span data-stu-id="27c35-222">when text can be selected.</span></span> |

### <a name="custom-text-command-bar-flyouts"></a><span data-ttu-id="27c35-223">Benutzerdefinierter Text, der Flyouts auf einer Befehlsleiste</span><span class="sxs-lookup"><span data-stu-id="27c35-223">Custom text command bar flyouts</span></span>

<span data-ttu-id="27c35-224">TextCommandBarFlyout nicht angepasst werden kann, und von jedes Textsteuerelement automatisch verwaltet wird.</span><span class="sxs-lookup"><span data-stu-id="27c35-224">TextCommandBarFlyout can't be customized, and is managed automatically by each text control.</span></span> <span data-ttu-id="27c35-225">Allerdings können Sie die standardmäßige TextCommandBarFlyout mit benutzerdefinierten Befehlen ersetzen.</span><span class="sxs-lookup"><span data-stu-id="27c35-225">However, you can replace the default TextCommandBarFlyout with custom commands.</span></span>

- <span data-ttu-id="27c35-226">Um die standardmäßige TextCommandBarFlyout ersetzen, die auf markierten Text angezeigt wird, können Sie erstellen Sie eine benutzerdefinierte CommandBarFlyout (oder andere Flyout) und weisen sie die **SelectionFlyout** -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="27c35-226">To replace the default TextCommandBarFlyout that's shown on text selection, you can create a custom CommandBarFlyout (or other flyout type) and assign it to the **SelectionFlyout** property.</span></span> <span data-ttu-id="27c35-227">Wenn Sie SelectionFlyout auf **null**festlegen, werden keine Befehle auf Auswahl angezeigt.</span><span class="sxs-lookup"><span data-stu-id="27c35-227">If you set SelectionFlyout to **null**, no commands are shown on selection.</span></span>
- <span data-ttu-id="27c35-228">Um die Standard-TextCommandBarFlyout ersetzen, die im Kontextmenü angezeigt wird, weisen Sie eine benutzerdefinierte CommandBarFlyout (oder andere Flyout-Typ) für die **ContextFlyout** -Eigenschaft für ein Text-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="27c35-228">To replace the default TextCommandBarFlyout that's shown as the context menu, assign a custom CommandBarFlyout (or other flyout type) to the **ContextFlyout** property on a text control.</span></span> <span data-ttu-id="27c35-229">Wenn Sie ContextFlyout auf **null**festgelegt, wird das Flyout "Menü" angezeigt, in früheren Versionen des Textsteuerelements anstelle der TextCommandBarFlyout angezeigt.</span><span class="sxs-lookup"><span data-stu-id="27c35-229">If you set ContextFlyout to **null**, the menu flyout shown in previous versions of the text control is shown instead of the TextCommandBarFlyout.</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="27c35-230">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="27c35-230">Get the sample code</span></span>

- <span data-ttu-id="27c35-231">[Beispiel eines XAML-Steuerelementekatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="27c35-231">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>
- [<span data-ttu-id="27c35-232">Beispiel für XAML-Befehle</span><span class="sxs-lookup"><span data-stu-id="27c35-232">XAML Commanding sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=620019)

## <a name="related-articles"></a><span data-ttu-id="27c35-233">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="27c35-233">Related articles</span></span>

- [<span data-ttu-id="27c35-234">Befehlsdesigngrundlagen für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="27c35-234">Command design basics for UWP apps</span></span>](../basics/commanding-basics.md)
- [<span data-ttu-id="27c35-235">CommandBar-Klasse</span><span class="sxs-lookup"><span data-stu-id="27c35-235">CommandBar class</span></span>](https://msdn.microsoft.com/library/windows/apps/dn279427)
