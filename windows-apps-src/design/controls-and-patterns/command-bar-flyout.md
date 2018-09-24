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
ms.sourcegitcommit: 194ab5aa395226580753869c6b66fce88be83522
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2018
ms.locfileid: "4151369"
---
# <a name="command-bar-flyout"></a><span data-ttu-id="3301e-103">Befehlsleiste flyout</span><span class="sxs-lookup"><span data-stu-id="3301e-103">Command bar flyout</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3301e-104">In diesem Artikel werden Funktionen beschrieben, die noch nicht veröffentlicht wurden und vor der kommerziellen Freigabe evtl. geändert werden.</span><span class="sxs-lookup"><span data-stu-id="3301e-104">This article describes functionality that hasn’t been released yet and may be substantially modified before it's commercially released.</span></span> <span data-ttu-id="3301e-105">Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.</span><span class="sxs-lookup"><span data-stu-id="3301e-105">Microsoft makes no warranties, express or implied, with respect to the information provided here.</span></span> <span data-ttu-id="3301e-106">Preview-Features benötigen die [neuesten Windows 10 Insider Preview-Build und SDK](https://insider.windows.com/for-developers/) oder der [Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).</span><span class="sxs-lookup"><span data-stu-id="3301e-106">Preview features require the [latest Windows 10 Insider Preview build and SDK](https://insider.windows.com/for-developers/) or the [Windows UI Library](https://docs.microsoft.com/uwp/toolkits/winui/).</span></span>

<span data-ttu-id="3301e-107">Das Befehlsleiste Flyout können Sie Benutzer mit einfachen Zugriff auf allgemeine Aufgaben bereitstellen, indem Befehle in einem schwebenden Symbolleisten im Zusammenhang mit eines Elements auf die UI-Canvas angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3301e-107">The command bar flyout lets you provide users with easy access to common tasks by showing commands in a floating toolbar related to an element on your UI canvas.</span></span>

![Eine erweiterte Text Befehlsleiste-flyout](images/command-bar-flyout-text-full.png)

> <span data-ttu-id="3301e-109">Verwandte Informationen finden Sie unter [Flyouts](../controls-and-patterns/dialogs-and-flyouts/flyouts.md), [Menüs und Kontextmenüs](menus.md)und [Befehlsleisten](app-bars.md).</span><span class="sxs-lookup"><span data-stu-id="3301e-109">For related info, see [Flyouts](../controls-and-patterns/dialogs-and-flyouts/flyouts.md), [Menus and context menus](menus.md), and [Command bars](app-bars.md).</span></span>

<span data-ttu-id="3301e-110">Wie [CommandBar](app-bars.md)hat CommandBarFlyout **PrimaryCommands** und **"secondarycommands"** Eigenschaften, mit denen Sie Befehle hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="3301e-110">Like [CommandBar](app-bars.md), CommandBarFlyout has **PrimaryCommands** and **SecondaryCommands** properties you can use to add commands.</span></span> <span data-ttu-id="3301e-111">Sie können entweder Sammlung oder beide Befehle versehen.</span><span class="sxs-lookup"><span data-stu-id="3301e-111">You can place commands in either collection, or both.</span></span> <span data-ttu-id="3301e-112">Wann und wie die primären und sekundären Befehle angezeigt werden, hängt von den Anzeigemodus.</span><span class="sxs-lookup"><span data-stu-id="3301e-112">When and how the primary and secondary commands are displayed depends on the display mode.</span></span>

<span data-ttu-id="3301e-113">Das Befehlsleiste Flyout verfügt über zwei Anzeigemodi: *reduziert* und *Erweitert*.</span><span class="sxs-lookup"><span data-stu-id="3301e-113">The command bar flyout has two display modes: *collapsed* and *expanded*.</span></span>

- <span data-ttu-id="3301e-114">Im Modus "Collapsed" werden nur die primären Befehle angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3301e-114">In the collapsed mode, only the primary commands are shown.</span></span> <span data-ttu-id="3301e-115">Hat der Befehlsleiste Flyout primären und sekundären Befehle, eine "Schaltfläche" Weitere, dargestellt durch Auslassungspunkte \ [• • •] wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3301e-115">If your command bar flyout has both primary and secondary commands, a "see more" button, which is represented by an ellipsis \[•••\], is displayed.</span></span> <span data-ttu-id="3301e-116">Dadurch wird den Benutzer den Zugriff auf die sekundären Befehle Abrufen von erweiterten Modus wechselt.</span><span class="sxs-lookup"><span data-stu-id="3301e-116">This lets the user get access to the secondary commands by transitioning to expanded mode.</span></span>
- <span data-ttu-id="3301e-117">Im erweiterten Modus werden die primären und sekundären Befehle angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3301e-117">In the expanded mode, both the primary and secondary commands are shown.</span></span> <span data-ttu-id="3301e-118">(Wenn das Steuerelement nur sekundäre Elemente verfügt, werden sie in einer Weise ähnelt dem MenuFlyout-Steuerelement angezeigt.)</span><span class="sxs-lookup"><span data-stu-id="3301e-118">(If the control has only secondary items, they are shown in a way similar to the MenuFlyout control.)</span></span>

| **<span data-ttu-id="3301e-119">Windows-UI-Bibliothek herunterladen</span><span class="sxs-lookup"><span data-stu-id="3301e-119">Get the Windows UI Library</span></span>** |
| - |
| <span data-ttu-id="3301e-120">Dieses Steuerelement ist Bestandteil der Windows-UI-Bibliothek, NuGet-Paket, das neue Steuerelemente und UI-Features für UWP-apps enthält.</span><span class="sxs-lookup"><span data-stu-id="3301e-120">This control is included as part of the Windows UI Library, a NuGet package that contains new controls and UI features for UWP apps.</span></span> <span data-ttu-id="3301e-121">Weitere Informationen, einschließlich installationsanweisungen finden Sie die [Übersicht über die Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).</span><span class="sxs-lookup"><span data-stu-id="3301e-121">For more info, including installation instructions, see the [Windows UI Library overview](https://docs.microsoft.com/uwp/toolkits/winui/).</span></span> |

| **<span data-ttu-id="3301e-122">Plattform-APIs</span><span class="sxs-lookup"><span data-stu-id="3301e-122">Platform APIs</span></span>** | **<span data-ttu-id="3301e-123">Windows-UI-Bibliothek APIs</span><span class="sxs-lookup"><span data-stu-id="3301e-123">Windows UI Library APIs</span></span>** |
| - | - |
| <span data-ttu-id="3301e-124">[CommandBarFlyout-Klasse](/uwp/api/windows.ui.xaml.controls.commandbarflyout), [TextCommandBarFlyout-Klasse](/uwp/api/windows.ui.xaml.controls.textcommandbarflyout), [AppBarButton-Klasse](/uwp/api/windows.ui.xaml.controls.appbarbutton), [Klasse "appbartogglebutton"](/uwp/api/windows.ui.xaml.controls.appbartogglebutton), [Klasse "appbarseparator"](/uwp/api/windows.ui.xaml.controls.appbarseparator)</span><span class="sxs-lookup"><span data-stu-id="3301e-124">[CommandBarFlyout class](/uwp/api/windows.ui.xaml.controls.commandbarflyout), [TextCommandBarFlyout class](/uwp/api/windows.ui.xaml.controls.textcommandbarflyout), [AppBarButton class](/uwp/api/windows.ui.xaml.controls.appbarbutton), [AppBarToggleButton class](/uwp/api/windows.ui.xaml.controls.appbartogglebutton), [AppBarSeparator class](/uwp/api/windows.ui.xaml.controls.appbarseparator)</span></span> | <span data-ttu-id="3301e-125">[CommandBarFlyout-Klasse](/uwp/api/microsoft.ui.xaml.controls.commandbarflyout), [TextCommandBarFlyout-Klasse](/uwp/api/microsoft.ui.xaml.controls.textcommandbarflyout)</span><span class="sxs-lookup"><span data-stu-id="3301e-125">[CommandBarFlyout class](/uwp/api/microsoft.ui.xaml.controls.commandbarflyout), [TextCommandBarFlyout class](/uwp/api/microsoft.ui.xaml.controls.textcommandbarflyout)</span></span> |

## <a name="is-this-the-right-control"></a><span data-ttu-id="3301e-126">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="3301e-126">Is this the right control?</span></span>

<span data-ttu-id="3301e-127">Verwenden Sie das CommandBarFlyout-Steuerelement, um eine Sammlung von Befehle für dem Benutzer, z. B. Schaltflächen und Menüelementen im Kontext eines Elements auf der app-Canvas anzeigen.</span><span class="sxs-lookup"><span data-stu-id="3301e-127">Use the CommandBarFlyout control to show a collection of commands to the user, such as buttons and menu items, in the context of an element on the app canvas.</span></span>

<span data-ttu-id="3301e-128">Die TextCommandBarFlyout zeigt Textbefehle im TextBlock, TextBox, RichEditBox, RichTextBlock und PasswordBox-Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="3301e-128">The TextCommandBarFlyout displays text commands in TextBox, TextBlock, RichEditBox, RichTextBlock, and PasswordBox controls.</span></span> <span data-ttu-id="3301e-129">Die Befehle werden automatisch auf die aktuelle Textauswahl entsprechend konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="3301e-129">The commands are automatically configured appropriately to the current text selection.</span></span> <span data-ttu-id="3301e-130">Verwenden Sie eine CommandBarFlyout, um die Standard-Text-Befehle auf Text-Steuerelemente ersetzen.</span><span class="sxs-lookup"><span data-stu-id="3301e-130">Use a CommandBarFlyout to replace the default text commands on text controls.</span></span>

<span data-ttu-id="3301e-131">Um kontextbezogene anzeigen folgen Befehle auf Listenelemente der Anleitung im [Contextual Befehle für Sammlungen und Listen](collection-commanding.md).</span><span class="sxs-lookup"><span data-stu-id="3301e-131">To show contextual commands on list items follow the guidance in [Contextual commanding for collections and lists](collection-commanding.md).</span></span>

### <a name="commandbarflyout-vs-menuflyout"></a><span data-ttu-id="3301e-132">CommandBarFlyout Vs MenuFlyout</span><span class="sxs-lookup"><span data-stu-id="3301e-132">CommandBarFlyout vs MenuFlyout</span></span>

<span data-ttu-id="3301e-133">Um Befehle in einem Kontextmenü angezeigt werden, können Sie CommandBarFlyout oder MenuFlyout verwenden.</span><span class="sxs-lookup"><span data-stu-id="3301e-133">To show commands in a context menu, you can use CommandBarFlyout or MenuFlyout.</span></span> <span data-ttu-id="3301e-134">CommandBarFlyout wird empfohlen, da es mehr Funktionen als MenuFlyout bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="3301e-134">We recommend CommandBarFlyout because it provides more functionality than MenuFlyout.</span></span> <span data-ttu-id="3301e-135">Sie können CommandBarFlyout mit nur sekundäre Befehle verwenden, erhalten das Verhalten und von einem MenuFlyout, oder verwenden Sie das vollständige Befehlsleiste Flyout mit primären und sekundären Befehlen.</span><span class="sxs-lookup"><span data-stu-id="3301e-135">You can use CommandBarFlyout with only secondary commands to get the behavior and look of a MenuFlyout, or use the full command bar flyout with both primary and secondary commands.</span></span>

## <a name="examples"></a><span data-ttu-id="3301e-136">Beispiele</span><span class="sxs-lookup"><span data-stu-id="3301e-136">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="3301e-137">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="3301e-137">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="3301e-138">Wenn Sie die <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> -app installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/CommandBarFlyout">die app zu öffnen und finden Sie unter der CommandBarFlyout in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="3301e-138">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/CommandBarFlyout">open the app and see the CommandBarFlyout in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="3301e-139">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="3301e-139">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="3301e-140">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="3301e-140">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="proactive-vs-reactive-invocation"></a><span data-ttu-id="3301e-141">Im Vergleich zu Zeiten Aufruf proaktive</span><span class="sxs-lookup"><span data-stu-id="3301e-141">Proactive vs. reactive invocation</span></span>

<span data-ttu-id="3301e-142">Es gibt in der Regel zwei Möglichkeiten zum Aufrufen eines Flyouts oder dem Menü ", die mit einem Element auf Ihrer Benutzeroberfläche Canvas verknüpft ist: _proaktive aufrufen_ und das _reaktive Aufruf_.</span><span class="sxs-lookup"><span data-stu-id="3301e-142">There are typically two ways to invoke a flyout or menu that's associated with an element on your UI canvas: _proactive invocation_ and _reactive invocation_.</span></span>

<span data-ttu-id="3301e-143">Unter proaktive Aufruf werden Befehle automatisch angezeigt, wenn der Benutzer mit dem Element interagiert, die die Befehle zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="3301e-143">In proactive invocation, commands appear automatically when the user interacts with the item that the commands are associated with.</span></span> <span data-ttu-id="3301e-144">Z. B. möglicherweise Formatierungsbefehle Text eingeblendet, wenn der Benutzer Text in einem Textfeld auswählt.</span><span class="sxs-lookup"><span data-stu-id="3301e-144">For example, text formatting commands might pop up when the user selects text in a text box.</span></span> <span data-ttu-id="3301e-145">In diesem Fall wird das Befehlsleiste Flyout Fokus nicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="3301e-145">In this case, the command bar flyout does not take focus.</span></span> <span data-ttu-id="3301e-146">Stattdessen stellt es geeignete Befehle nahe dem Element, dem der Benutzer mit interagiert.</span><span class="sxs-lookup"><span data-stu-id="3301e-146">Instead, it presents relevant commands close to the item the user is interacting with.</span></span> <span data-ttu-id="3301e-147">Wenn der Benutzer mit den Befehlen interagieren nicht, werden sie geschlossen.</span><span class="sxs-lookup"><span data-stu-id="3301e-147">If the user doesn't interact with the commands, they are dismissed.</span></span>

<span data-ttu-id="3301e-148">In Zeiten Aufruf werden Befehle in Reaktion auf eine explizite Benutzeraktion angezeigt, die Befehle anfordern. z. B. eine mit der rechten Maustaste.</span><span class="sxs-lookup"><span data-stu-id="3301e-148">In reactive invocation, commands are shown in response to an explicit user action to request the commands; for example, a right-click.</span></span> <span data-ttu-id="3301e-149">Dies entspricht dem herkömmliche Konzept eines [Kontextmenüs](menus.md).</span><span class="sxs-lookup"><span data-stu-id="3301e-149">This corresponds to the traditional concept of a [context menu](menus.md).</span></span>

<span data-ttu-id="3301e-150">Sie können die CommandBarFlyout in Weise oder sogar eine Mischung der beiden verwenden.</span><span class="sxs-lookup"><span data-stu-id="3301e-150">You can use the CommandBarFlyout in either way, or even a mixture of the two.</span></span>

## <a name="create-a-command-bar-flyout"></a><span data-ttu-id="3301e-151">Erstellen Sie ein Befehlsleiste flyout</span><span class="sxs-lookup"><span data-stu-id="3301e-151">Create a command bar flyout</span></span>

> <span data-ttu-id="3301e-152">**Vorschau**: CommandBarFlyout erfordert die [neuesten Windows 10 Insider Preview-Build und SDK](https://insider.windows.com/for-developers/) oder der [Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).</span><span class="sxs-lookup"><span data-stu-id="3301e-152">**Preview**: CommandBarFlyout requires the [latest Windows 10 Insider Preview build and SDK](https://insider.windows.com/for-developers/) or the [Windows UI Library](https://docs.microsoft.com/uwp/toolkits/winui/).</span></span>

<span data-ttu-id="3301e-153">In diesem Beispiel wird veranschaulicht, wie ein Befehlsleiste Flyout erstellen und verwenden sie proaktiv und reaktiv.</span><span class="sxs-lookup"><span data-stu-id="3301e-153">This example shows how to create a command bar flyout and use it both proactively and reactively.</span></span> <span data-ttu-id="3301e-154">Wenn das Bild getippt wird, wird das Flyout im Modus "Collapsed" angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3301e-154">When the image is tapped, the flyout is shown in its collapsed mode.</span></span> <span data-ttu-id="3301e-155">Wenn als Kontextmenü angezeigt wird, wird das Flyout im erweiterten Modus angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3301e-155">When shown as a context menu, the flyout is shown in its expanded mode.</span></span> <span data-ttu-id="3301e-156">In beiden Fällen kann der Benutzer erweitern oder reduzieren das Flyout, nachdem er geöffnet wird.</span><span class="sxs-lookup"><span data-stu-id="3301e-156">In either case, the user can expand or collapse the flyout after it's opened.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="3301e-157">Ein Flyout "Collapsed" Befehlsleiste</span><span class="sxs-lookup"><span data-stu-id="3301e-157">A collapsed command bar flyout</span></span><br/>
        !["Collapsed" Befehlsleiste Flyout-Beispiel](images/command-bar-flyout-img-collapsed.png)
    :::column-end:::
    :::column:::
        <span data-ttu-id="3301e-159">Eine erweiterte Befehlsleiste flyout</span><span class="sxs-lookup"><span data-stu-id="3301e-159">An expanded command bar flyout</span></span><br/>
        ![Beispiel für eine erweiterte Befehlsleiste flyout](images/command-bar-flyout-img-expanded.png)
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

### <a name="show-commands-proactively"></a><span data-ttu-id="3301e-161">Befehle proaktiv anzeigen</span><span class="sxs-lookup"><span data-stu-id="3301e-161">Show commands proactively</span></span>

<span data-ttu-id="3301e-162">Wenn Sie Kontextbefehlen proaktiv angezeigt wird, sollte nur die primären Befehle standardmäßig angezeigt werden (die Leiste-Flyout der Befehl sollte reduziert werden).</span><span class="sxs-lookup"><span data-stu-id="3301e-162">When you show contextual commands proactively, only the primary commands should be shown by default (the command bar flyout should be collapsed).</span></span> <span data-ttu-id="3301e-163">Platzieren Sie die wichtigsten Befehle in der Auflistung primäre Befehle und weitere Befehle, die normalerweise in einem Kontextmenü in die sekundären Befehle Auflistung würde.</span><span class="sxs-lookup"><span data-stu-id="3301e-163">Place the most important commands in the primary commands collection, and additional commands that would traditionally go in a context menu into the secondary commands collection.</span></span>

<span data-ttu-id="3301e-164">Wenn proaktiv Befehle anzeigen möchten, behandeln Sie in der Regel das Ereignis [Klicken](/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.click) oder [Tapped](/uwp/api/windows.ui.xaml.uielement.tapped) , um das Befehlsleiste Flyout anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="3301e-164">To proactively show commands, you typically handle the [Click](/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.click) or [Tapped](/uwp/api/windows.ui.xaml.uielement.tapped) event to show the command bar flyout.</span></span> <span data-ttu-id="3301e-165">Legen Sie das Flyout [ShowMode](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.showmode) **vorübergehende** oder **TransientWithDismissOnPointerMoveAway** , um das Flyout im Modus "Collapsed" zu öffnen, ohne den Fokus fest.</span><span class="sxs-lookup"><span data-stu-id="3301e-165">Set the flyout's [ShowMode](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.showmode) to **Transient** or **TransientWithDismissOnPointerMoveAway** to open the flyout in its collapsed mode without taking focus.</span></span>

<span data-ttu-id="3301e-166">Ab Windows 10 Insider Preview, Textsteuerelemente verfügen über eine **SelectionFlyout** -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="3301e-166">Starting in the Windows 10 Insider Preview, text controls have a **SelectionFlyout** property.</span></span> <span data-ttu-id="3301e-167">Wenn Sie diese Eigenschaft ein Flyout zuordnen, wird es automatisch angezeigt, wenn Text markiert ist.</span><span class="sxs-lookup"><span data-stu-id="3301e-167">When you assign a flyout to this property, it is automatically shown when text is selected.</span></span>

### <a name="show-commands-reactively"></a><span data-ttu-id="3301e-168">Befehle reaktiv anzeigen</span><span class="sxs-lookup"><span data-stu-id="3301e-168">Show commands reactively</span></span>

<span data-ttu-id="3301e-169">Wenn Sie Kontextbefehlen reaktiv, als Kontextmenü angezeigt wird, sind die sekundären Befehle standardmäßig angezeigt (die Leiste-Flyout der Befehl sollte erweitert werden).</span><span class="sxs-lookup"><span data-stu-id="3301e-169">When you show contextual commands reactively, as a context menu, the secondary commands are shown by default (the command bar flyout should be expanded).</span></span> <span data-ttu-id="3301e-170">In diesem Fall wird möglicherweise das Flyout Befehlsleiste primären und sekundären Befehlen oder nur sekundäre Befehle.</span><span class="sxs-lookup"><span data-stu-id="3301e-170">In this case, the command bar flyout might have both primary and secondary commands, or secondary commands only.</span></span>

<span data-ttu-id="3301e-171">Um Befehle in einem Kontextmenü anzuzeigen, weisen Sie in der Regel das Flyout der [ContextFlyout](/uwp/api/windows.ui.xaml.uielement.contextflyout) -Eigenschaft eines Benutzeroberflächenelements.</span><span class="sxs-lookup"><span data-stu-id="3301e-171">To show commands in a context menu, you typically assign the flyout to the [ContextFlyout](/uwp/api/windows.ui.xaml.uielement.contextflyout) property of a UI element.</span></span> <span data-ttu-id="3301e-172">Auf diese Weise wird das Flyout Öffnen des Elements behandelt, und Sie müssen nichts weiter tun.</span><span class="sxs-lookup"><span data-stu-id="3301e-172">This way, opening the flyout is handled by the element, and you don't need to do anything more.</span></span>

<span data-ttu-id="3301e-173">Wenn Sie verarbeiten das Flyout (z. B. auf ein Ereignis [RightTapped](/uwp/api/windows.ui.xaml.uielement.righttapped) ) angezeigt, die das Flyout [ShowMode](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.showmode) in **Standard** , öffnen Sie das Flyout im erweiterten Modus und weisen Sie ihm den Fokus.</span><span class="sxs-lookup"><span data-stu-id="3301e-173">If you handle showing the flyout yourself (for example, on a [RightTapped](/uwp/api/windows.ui.xaml.uielement.righttapped) event), set the the flyout's [ShowMode](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.showmode) to **Standard** to open the flyout in its expanded mode and give it focus.</span></span>

> [!TIP]
> <span data-ttu-id="3301e-174">Weitere Informationen zu den Optionen beim Anzeigen von einem Flyout und zur Platzierung von das Flyout zu steuern finden Sie unter [Flyouts](../controls-and-patterns/dialogs-and-flyouts/flyouts.md).</span><span class="sxs-lookup"><span data-stu-id="3301e-174">For more info about options when showing a flyout and how to control placement of the flyout, see [Flyouts](../controls-and-patterns/dialogs-and-flyouts/flyouts.md).</span></span>

## <a name="commands-and-content"></a><span data-ttu-id="3301e-175">Befehle und Inhalt</span><span class="sxs-lookup"><span data-stu-id="3301e-175">Commands and content</span></span>

<span data-ttu-id="3301e-176">Das CommandBarFlyout-Steuerelement verfügt über 2 Eigenschaften Sie Befehle und Inhalte hinzufügen können: [PrimaryCommands](/uwp/api/windows.ui.xaml.controls.commandbarflyout.primarycommands) und ["secondarycommands"](/uwp/api/windows.ui.xaml.controls.commandbarflyout.secondarycommands).</span><span class="sxs-lookup"><span data-stu-id="3301e-176">The CommandBarFlyout control has 2 properties you can use to add commands and content: [PrimaryCommands](/uwp/api/windows.ui.xaml.controls.commandbarflyout.primarycommands) and [SecondaryCommands](/uwp/api/windows.ui.xaml.controls.commandbarflyout.secondarycommands).</span></span>

<span data-ttu-id="3301e-177">Befehlsleistenelemente werden standardmäßig der **PrimaryCommands**-Sammlung hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="3301e-177">By default, command bar items are added to the **PrimaryCommands** collection.</span></span> <span data-ttu-id="3301e-178">Diese Befehle werden angezeigt, in der Befehlsleiste und sowohl die "Collapsed" auch im erweiterten Modus sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="3301e-178">These commands are shown in the command bar and are visible in both the collapsed and expanded modes.</span></span> <span data-ttu-id="3301e-179">Im Gegensatz zu CommandBar primäre Befehle nicht automatisch Überlauf auf sekundäre Befehle und möglicherweise abgeschnitten.</span><span class="sxs-lookup"><span data-stu-id="3301e-179">Unlike CommandBar, primary commands do not automatically overflow to the secondary commands and might be truncated.</span></span>

<span data-ttu-id="3301e-180">Sie können auch Befehle zur Auflistung **"secondarycommands"** hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="3301e-180">You can also add commands to the **SecondaryCommands** collection.</span></span> <span data-ttu-id="3301e-181">Sekundäre Befehle auf das Menü Teil des Steuerelements angezeigt werden und sind nur im erweiterten Modus sichtbar.</span><span class="sxs-lookup"><span data-stu-id="3301e-181">Secondary commands are shown in the menu portion of the control and are visible only in the expanded mode.</span></span>

### <a name="app-bar-buttons"></a><span data-ttu-id="3301e-182">App-Leistenschaltflächen</span><span class="sxs-lookup"><span data-stu-id="3301e-182">App bar buttons</span></span>

<span data-ttu-id="3301e-183">Sie können die PrimaryCommands und "secondarycommands" direkt mit Steuerelementen [AppBarButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarbutton.aspx), [AppBarToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbartogglebutton.aspx)und [AppBarSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarseparator.aspx) auffüllen.</span><span class="sxs-lookup"><span data-stu-id="3301e-183">You can populate the PrimaryCommands and SecondaryCommands directly with [AppBarButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarbutton.aspx), [AppBarToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbartogglebutton.aspx), and [AppBarSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarseparator.aspx) controls.</span></span>

<span data-ttu-id="3301e-184">Die Steuerelemente für die App-Leistenschaltfläche zeichnen sich durch ein Symbol und eine Textbeschriftung aus.</span><span class="sxs-lookup"><span data-stu-id="3301e-184">The app bar button controls are characterized by an icon and text label.</span></span> <span data-ttu-id="3301e-185">Diese Steuerelemente sind für die Verwendung in Befehlsleisten optimiert, und ihre Darstellung ändert, je nachdem, ob das Steuerelement in der Befehlsleiste oder im Überlaufmenü angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="3301e-185">These controls are optimized for use in a command bar, and their appearance changes depending on whether the control is shown in the command bar or the overflow menu.</span></span>

- <span data-ttu-id="3301e-186">App-Leistenschaltflächen als primäre Befehle verwendet werden in der Befehlsleiste mit nur ihre Symbol angezeigt. die Beschriftung wird nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3301e-186">App bar buttons used as primary commands are shown in the command bar with only their icon; the text label is not shown.</span></span> <span data-ttu-id="3301e-187">Es wird empfohlen, dass Sie eine QuickInfo verwenden, um einen beschreibenden Text für den Befehl anzuzeigen wie hier gezeigt.</span><span class="sxs-lookup"><span data-stu-id="3301e-187">We recommend that you use a tooltip to show a text description of the command, as shown here.</span></span>
    ```xaml
    <AppBarButton Icon="Copy" ToolTipService.ToolTip="Copy"/>
    ```
- <span data-ttu-id="3301e-188">App-Leistenschaltflächen als sekundäre Befehle verwendet werden Sie im Menü mit der Bezeichnung und die Symbol sichtbar angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3301e-188">App bar buttons used as secondary commands are shown in the menu, with both the label and icon visible.</span></span>

### <a name="other-content"></a><span data-ttu-id="3301e-189">Andere Inhalte</span><span class="sxs-lookup"><span data-stu-id="3301e-189">Other content</span></span>

<span data-ttu-id="3301e-190">Sie können ein Befehlsleiste Flyout eine AppBarElementContainer umschließen andere Steuerelemente hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="3301e-190">You can add other controls to a command bar flyout by wrapping them in an AppBarElementContainer.</span></span> <span data-ttu-id="3301e-191">Auf diese Weise können Sie die Steuerelemente wie [DropDownButton]() oder [SplitButton]()hinzugefügt oder Containern wie [StackPanel]() um komplexere Benutzeroberfläche zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="3301e-191">This lets you add controls like [DropDownButton]() or [SplitButton](), or add containers like [StackPanel]() to create more complex UI.</span></span>

> [!NOTE]
> <span data-ttu-id="3301e-192">Um die primären oder sekundären Befehl Sammlungen Befehlsleiste Flyout hinzugefügt werden, muss ein Element die [ICommandBarElement](/uwp/api/windows.ui.xaml.controls.icommandbarelement) -Schnittstelle implementieren.</span><span class="sxs-lookup"><span data-stu-id="3301e-192">In order to be added to the primary or secondary command collections of a command bar flyout, an element must implement the [ICommandBarElement](/uwp/api/windows.ui.xaml.controls.icommandbarelement) interface.</span></span> <span data-ttu-id="3301e-193">AppBarElementContainer ist ein Wrapper, der diese Schnittstelle implementiert, sodass Sie ein Element zu einer Befehlsleiste hinzufügen können, auch wenn es nicht die Schnittstelle selbst implementiert.</span><span class="sxs-lookup"><span data-stu-id="3301e-193">AppBarElementContainer is a wrapper that implements this interface so you can add an element to a command bar even if it doesn't implement the interface itself.</span></span>

<span data-ttu-id="3301e-194">Hier wird ein AppBarElementContainer verwendet, um zusätzliche Elemente ein Befehlsleiste Flyout hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="3301e-194">Here, an AppBarElementContainer is used to add extra elements to a command bar flyout.</span></span> <span data-ttu-id="3301e-195">Die primären Befehle Auswahl an Farben ermöglicht wird ein SplitButton hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="3301e-195">A SplitButton is added to the primary commands to allow selection of colors.</span></span> <span data-ttu-id="3301e-196">StackPanel wird die sekundären Befehle ein komplexeres Layouts für Zoomsteuerelemente zulassen hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="3301e-196">A StackPanel is added to the secondary commands to allow a more complex layout for zoom controls.</span></span>

> [!NOTE]
> <span data-ttu-id="3301e-197">Dieses Beispiel zeigt nur Befehlsleiste Flyout der UI, sie keine Befehle implementiert, die angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="3301e-197">This example shows only the command bar flyout UI, it does not implement any of the commands that are shown.</span></span> <span data-ttu-id="3301e-198">Weitere Informationen zur Implementierung der Befehle finden Sie unter [Schaltflächen](buttons.md) und [befehlsdesigngrundlagen](../basics/commanding-basics.md).</span><span class="sxs-lookup"><span data-stu-id="3301e-198">For more info about implementing the commands, see [Buttons](buttons.md) and [Command design basics](../basics/commanding-basics.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="3301e-199">Ein "Collapsed" Befehlsleiste Flyout mit einer offenen SplitButton</span><span class="sxs-lookup"><span data-stu-id="3301e-199">A collapsed command bar flyout with an open SplitButton</span></span><br/>
        ![Ein Befehlsleiste Flyout mit einer Split-Schaltfläche](images/command-bar-flyout-split-button.png)
    :::column-end:::
    :::column:::
        <span data-ttu-id="3301e-201">Eine erweiterte Befehlsleiste Flyout mit benutzerdefinierten Zoom UI im Menü ""</span><span class="sxs-lookup"><span data-stu-id="3301e-201">An expanded command bar flyout with custom zoom UI in the menu</span></span><br/>
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

## <a name="create-a-context-menu-with-secondary-commands-only"></a><span data-ttu-id="3301e-203">Erstellen Sie ein Kontextmenü mit nur sekundäre Befehle</span><span class="sxs-lookup"><span data-stu-id="3301e-203">Create a context menu with secondary commands only</span></span>

<span data-ttu-id="3301e-204">Sie können eine CommandBarFlyout mit nur sekundäre Befehle als ein [Kontextmenü](menus.md)anstelle einer MenuFlyout verwenden.</span><span class="sxs-lookup"><span data-stu-id="3301e-204">You can use a CommandBarFlyout with only secondary commands as a [context menu](menus.md), in place of a MenuFlyout.</span></span>

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

<span data-ttu-id="3301e-206">Sie können auch eine CommandBarFlyout mit einer DropDownButton verwenden, zum Erstellen eines Standardmenüs.</span><span class="sxs-lookup"><span data-stu-id="3301e-206">You can also use a CommandBarFlyout with a DropDownButton to create a standard menu.</span></span>

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

## <a name="command-bar-flyouts-for-text-controls"></a><span data-ttu-id="3301e-208">Flyouts auf einer Befehlsleiste für Textsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="3301e-208">Command bar flyouts for text controls</span></span>

<span data-ttu-id="3301e-209">Die [TextCommandBarFlyout](/uwp/api/microsoft.ui.xaml.controls.textcommandbarflyout) ist ein spezielles Befehlsleiste Flyout, die Befehle zum Bearbeiten von Text enthält.</span><span class="sxs-lookup"><span data-stu-id="3301e-209">The [TextCommandBarFlyout](/uwp/api/microsoft.ui.xaml.controls.textcommandbarflyout) is a specialized command bar flyout that contains commands for editing text.</span></span> <span data-ttu-id="3301e-210">Jedes Textsteuerelement zeigt die TextCommandBarFlyout automatisch als Kontextmenü (Rechtsklick), oder wenn Text markiert ist.</span><span class="sxs-lookup"><span data-stu-id="3301e-210">Each text control shows the TextCommandBarFlyout automatically as a context menu (right-click), or when text is selected.</span></span> <span data-ttu-id="3301e-211">Die Leiste-Flyout der Text-Befehl passt sich die Textauswahl nur relevante Befehle angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3301e-211">The text command bar flyout adapts to the text selection to only show relevant commands.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="3301e-212">Ein Text Befehlsleiste Flyout für Textauswahl</span><span class="sxs-lookup"><span data-stu-id="3301e-212">A text command bar flyout on text selection</span></span><br/>
        ![Ein "Collapsed" Text Befehlsleiste-flyout](images/command-bar-flyout-text-selection.png)
    :::column-end:::
    :::column:::
        <span data-ttu-id="3301e-214">Eine erweiterte Text Befehlsleiste-flyout</span><span class="sxs-lookup"><span data-stu-id="3301e-214">An expanded text command bar flyout</span></span><br/>
        ![Eine erweiterte Text Befehlsleiste-flyout](images/command-bar-flyout-text-full.png)
    :::column-end:::
:::row-end:::

### <a name="available-commands"></a><span data-ttu-id="3301e-216">Verfügbaren Befehle</span><span class="sxs-lookup"><span data-stu-id="3301e-216">Available commands</span></span>

<span data-ttu-id="3301e-217">Diese Tabelle zeigt die Befehle in einer TextCommandBarFlyout, und wenn diese angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="3301e-217">This table shows the commands that are included in a TextCommandBarFlyout, and when they are shown.</span></span>

| <span data-ttu-id="3301e-218">Befehl</span><span class="sxs-lookup"><span data-stu-id="3301e-218">Command</span></span> | <span data-ttu-id="3301e-219">Dargestellt …</span><span class="sxs-lookup"><span data-stu-id="3301e-219">Shown...</span></span> |
| ------- | -------- |
| <span data-ttu-id="3301e-220">Fett</span><span class="sxs-lookup"><span data-stu-id="3301e-220">Bold</span></span> | <span data-ttu-id="3301e-221">Wenn das Text-Steuerelement keine schreibgeschützt (RichEditBox nur) ist.</span><span class="sxs-lookup"><span data-stu-id="3301e-221">when the text control is not read-only (RichEditBox only).</span></span> |
| <span data-ttu-id="3301e-222">Kursiv</span><span class="sxs-lookup"><span data-stu-id="3301e-222">Italic</span></span> | <span data-ttu-id="3301e-223">Wenn das Text-Steuerelement keine schreibgeschützt (RichEditBox nur) ist.</span><span class="sxs-lookup"><span data-stu-id="3301e-223">when the text control is not read-only (RichEditBox only).</span></span> |
| <span data-ttu-id="3301e-224">Unterstreichen</span><span class="sxs-lookup"><span data-stu-id="3301e-224">Underline</span></span> | <span data-ttu-id="3301e-225">Wenn das Text-Steuerelement keine schreibgeschützt (RichEditBox nur) ist.</span><span class="sxs-lookup"><span data-stu-id="3301e-225">when the text control is not read-only (RichEditBox only).</span></span> |
| <span data-ttu-id="3301e-226">Nachweis von Manipulation</span><span class="sxs-lookup"><span data-stu-id="3301e-226">Proofing</span></span> | <span data-ttu-id="3301e-227">Wenn IsSpellCheckEnabled **"true ist"** und falsch geschrieben wird Text ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="3301e-227">when IsSpellCheckEnabled is **true** and misspelled text is selected.</span></span> |
| <span data-ttu-id="3301e-228">Ausschneiden</span><span class="sxs-lookup"><span data-stu-id="3301e-228">Cut</span></span> | <span data-ttu-id="3301e-229">Wenn das Text-Steuerelement ist nicht schreibgeschützt, und Text ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="3301e-229">when the text control is not read-only and text is selected.</span></span> |
| <span data-ttu-id="3301e-230">Kopieren</span><span class="sxs-lookup"><span data-stu-id="3301e-230">Copy</span></span> | <span data-ttu-id="3301e-231">Wenn Text markiert ist.</span><span class="sxs-lookup"><span data-stu-id="3301e-231">when text is selected.</span></span> |
| <span data-ttu-id="3301e-232">Einfügen</span><span class="sxs-lookup"><span data-stu-id="3301e-232">Paste</span></span> | <span data-ttu-id="3301e-233">Wenn das Steuerelement nicht schreibgeschützt und der Zwischenablage Inhalte.</span><span class="sxs-lookup"><span data-stu-id="3301e-233">when the text control is not read-only and the clipboard has content.</span></span> |
| <span data-ttu-id="3301e-234">Rückgängig machen</span><span class="sxs-lookup"><span data-stu-id="3301e-234">Undo</span></span> | <span data-ttu-id="3301e-235">Wenn eine Aktion, die rückgängig gemacht werden kann.</span><span class="sxs-lookup"><span data-stu-id="3301e-235">when there is an action that can be undone.</span></span> |
| <span data-ttu-id="3301e-236">Alle auswählen</span><span class="sxs-lookup"><span data-stu-id="3301e-236">Select all</span></span> | <span data-ttu-id="3301e-237">Wenn Text ausgewählt werden können.</span><span class="sxs-lookup"><span data-stu-id="3301e-237">when text can be selected.</span></span> |

### <a name="custom-text-command-bar-flyouts"></a><span data-ttu-id="3301e-238">Benutzerdefinierter Text, der Flyouts auf einer Befehlsleiste</span><span class="sxs-lookup"><span data-stu-id="3301e-238">Custom text command bar flyouts</span></span>

<span data-ttu-id="3301e-239">TextCommandBarFlyout nicht angepasst werden kann, und von jedes Textsteuerelement automatisch verwaltet wird.</span><span class="sxs-lookup"><span data-stu-id="3301e-239">TextCommandBarFlyout can't be customized, and is managed automatically by each text control.</span></span> <span data-ttu-id="3301e-240">Allerdings können Sie die standardmäßige TextCommandBarFlyout mit benutzerdefinierten Befehlen ersetzen.</span><span class="sxs-lookup"><span data-stu-id="3301e-240">However, you can replace the default TextCommandBarFlyout with custom commands.</span></span>

- <span data-ttu-id="3301e-241">Um die Standard-TextCommandBarFlyout ersetzen, die auf Textauswahl angezeigt wird, können Sie erstellen Sie eine benutzerdefinierte CommandBarFlyout (oder andere Flyout) und weisen sie die **SelectionFlyout** -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="3301e-241">To replace the default TextCommandBarFlyout that's shown on text selection, you can create a custom CommandBarFlyout (or other flyout type) and assign it to the **SelectionFlyout** property.</span></span> <span data-ttu-id="3301e-242">Wenn Sie SelectionFlyout auf **null**festlegen, werden keine Befehle auf der Auswahl angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3301e-242">If you set SelectionFlyout to **null**, no commands are shown on selection.</span></span>
- <span data-ttu-id="3301e-243">Um die Standard-TextCommandBarFlyout ersetzen, die im Kontextmenü angezeigt wird, weisen Sie eine benutzerdefinierte CommandBarFlyout (oder andere Flyout-Typ) für die **ContextFlyout** -Eigenschaft für ein Text-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="3301e-243">To replace the default TextCommandBarFlyout that's shown as the context menu, assign a custom CommandBarFlyout (or other flyout type) to the **ContextFlyout** property on a text control.</span></span> <span data-ttu-id="3301e-244">Wenn Sie ContextFlyout auf **null**festgelegt, wird das Flyout "Menü" angezeigt, in früheren Versionen des Textsteuerelements anstelle der TextCommandBarFlyout angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3301e-244">If you set ContextFlyout to **null**, the menu flyout shown in previous versions of the text control is shown instead of the TextCommandBarFlyout.</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="3301e-245">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="3301e-245">Get the sample code</span></span>

- <span data-ttu-id="3301e-246">[Beispiel eines XAML-Steuerelementekatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="3301e-246">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>
- [<span data-ttu-id="3301e-247">Beispiel für XAML-Befehle</span><span class="sxs-lookup"><span data-stu-id="3301e-247">XAML Commanding sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=620019)

## <a name="related-articles"></a><span data-ttu-id="3301e-248">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="3301e-248">Related articles</span></span>

- [<span data-ttu-id="3301e-249">Befehlsdesigngrundlagen für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="3301e-249">Command design basics for UWP apps</span></span>](../basics/commanding-basics.md)
- [<span data-ttu-id="3301e-250">CommandBar-Klasse</span><span class="sxs-lookup"><span data-stu-id="3301e-250">CommandBar class</span></span>](https://msdn.microsoft.com/library/windows/apps/dn279427)
