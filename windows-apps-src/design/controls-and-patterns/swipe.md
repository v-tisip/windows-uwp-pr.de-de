---
pm-contact: kisai
design-contact: ksulliv
dev-contact: Shmazlou
doc-status: Published
Description: Swipe commanding is a touch accelerator for context menus.
title: Wischen
label: Swipe
template: detail.hbs
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: a75723177e697d3fe4cdae270aba29eabcabf470
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7719415"
---
# <a name="swipe"></a><span data-ttu-id="0b9bf-103">Wischen</span><span class="sxs-lookup"><span data-stu-id="0b9bf-103">Swipe</span></span>

<span data-ttu-id="0b9bf-104">Wischgestenbasierte Befehle sind ein Beschleuniger für Kurzbefehlmenüs. Sie ermöglichen es Benutzern per Toucheingabe, häufig verwendete Aktionen auszuführen, ohne Zustände innerhalb der App zu ändern.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-104">Swipe commanding is an accelerator for context menus that lets users easily access common menu actions by touch, without needing to change states within the app.</span></span>

> <span data-ttu-id="0b9bf-105">**Wichtige APIs**: [SwipeControl](/uwp/api/windows.ui.xaml.controls.swipecontrol), [SwipeItem](/uwp/api/windows.ui.xaml.controls.swipeitem), [ListView class](/uwp/api/Windows.UI.Xaml.Controls.ListView)</span><span class="sxs-lookup"><span data-stu-id="0b9bf-105">**Important APIs**: [SwipeControl](/uwp/api/windows.ui.xaml.controls.swipecontrol), [SwipeItem](/uwp/api/windows.ui.xaml.controls.swipeitem), [ListView class](/uwp/api/Windows.UI.Xaml.Controls.ListView)</span></span>

![Anzeige- und Ausführungsdesigns](images/LightThemeSwipe.png)

## <a name="is-this-the-right-control"></a><span data-ttu-id="0b9bf-107">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="0b9bf-107">Is this the right control?</span></span>

<span data-ttu-id="0b9bf-108">Wischgestenbasierte Befehle sparen Platz.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-108">Swipe commanding saves space.</span></span> <span data-ttu-id="0b9bf-109">Sie eignen sich in Situationen, in denen der gleiche Vorgang mehrmals hintereinander schnell wiederholt wird.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-109">It's useful in situations where the user may perform the same operation on multiple items in quick succession.</span></span> <span data-ttu-id="0b9bf-110">Außerdem ermöglichen Sie „schnelle Aktionen“ für Elemente an, für die kein vollständiges Popup oder keine Zustandsänderung auf der Seite erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-110">And it provides "quick actions" on items that don't need a full popup or state change within the page.</span></span>

<span data-ttu-id="0b9bf-111">Wischgestenbasierte Befehle sollten verwendet werden, wenn Sie über eine große Gruppe von Elementen verfügen, die alle 1-3 Aktionen durchführen, die ein Benutzer möglicherweise regelmäßig ausführen möchte.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-111">You should use swipe commanding when you have a potentially large group of items, and each item has 1-3 actions that a user may want to perform regularly.</span></span> <span data-ttu-id="0b9bf-112">Diese Aktionen können u.a. Folgendes umfassen:</span><span class="sxs-lookup"><span data-stu-id="0b9bf-112">These actions may include, but are not limited to:</span></span>

- <span data-ttu-id="0b9bf-113">Löschen</span><span class="sxs-lookup"><span data-stu-id="0b9bf-113">Deleting</span></span>
- <span data-ttu-id="0b9bf-114">Markieren oder Archivieren</span><span class="sxs-lookup"><span data-stu-id="0b9bf-114">Marking or archiving</span></span>
- <span data-ttu-id="0b9bf-115">Speichern oder Herunterladen</span><span class="sxs-lookup"><span data-stu-id="0b9bf-115">Saving or downloading</span></span>
- <span data-ttu-id="0b9bf-116">Beantworten</span><span class="sxs-lookup"><span data-stu-id="0b9bf-116">Replying</span></span>

## <a name="examples"></a><span data-ttu-id="0b9bf-117">Beispiele</span><span class="sxs-lookup"><span data-stu-id="0b9bf-117">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="0b9bf-118">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="0b9bf-118">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="0b9bf-119">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/SwipeControl">die App zu öffnen und SwipeControl in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-119">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/SwipeControl">open the app and see the SwipeControl in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="0b9bf-120">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="0b9bf-120">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="0b9bf-121">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="0b9bf-121">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="video-summary"></a><span data-ttu-id="0b9bf-122">Video-Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="0b9bf-122">Video summary</span></span>

> [!VIDEO https://channel9.msdn.com/Events/Windows/Windows-Developer-Day-Fall-Creators-Update/WinDev015/player]

## <a name="how-does-swipe-work"></a><span data-ttu-id="0b9bf-123">Wie funktioniert das Wischen?</span><span class="sxs-lookup"><span data-stu-id="0b9bf-123">How does Swipe work?</span></span>

<span data-ttu-id="0b9bf-124">UWP-Wischgestenbasierte Befehle verfügen über zwei Modi: [Anzeigen](/uwp/api/windows.ui.xaml.controls.swipemode) und [Ausführen](/uwp/api/windows.ui.xaml.controls.swipemode).</span><span class="sxs-lookup"><span data-stu-id="0b9bf-124">UWP swipe commanding has two modes: [Reveal](/uwp/api/windows.ui.xaml.controls.swipemode) and [Execute](/uwp/api/windows.ui.xaml.controls.swipemode).</span></span> <span data-ttu-id="0b9bf-125">Außerdem werden vier verschiedene Wischrichtungen unterstützt: nach oben, unten, links und rechts.Wischen Richtungen: nach oben, unten, links und rechts.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-125">It also supports four different swipe directions: up, down, left, and right.</span></span>

### <a name="reveal-mode"></a><span data-ttu-id="0b9bf-126">Anzeigemodus</span><span class="sxs-lookup"><span data-stu-id="0b9bf-126">Reveal mode</span></span>

<span data-ttu-id="0b9bf-127">Im Modus „Einblenden“ wischt der Benutzer über ein Element, um ein Menü mit einem oder mehreren Befehlen zu öffnen, und muss explizit darauf tippen, um diesen Befehl auszuführen.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-127">In Reveal mode, the user swipes an item to open a menu of one or more commands and must explicitly tap a command to execute it.</span></span> <span data-ttu-id="0b9bf-128">Wenn der Anwender über ein Element wischt und es loslässt, bleibt das Menü geöffnet, bis entweder ein Befehl ausgewählt wird oder das Menü durch streifen, tippen oder wischen des geöffneten Elements vom Bildschirm erneut geschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-128">When the user swipes and releases an item, the menu remains open until either a command is selected, or the menu is closed again through swiping back, tapping off, or scrolling the opened swipe item off the screen.</span></span>

![Wischen zum Einblenden](images/SwipeCommand-Reveal_v2.gif)

<span data-ttu-id="0b9bf-130">Der Anzeigemodus ist ein sicherer, flexibler Wischmodus und kann für die meisten Aktionen, auch potenziell schädliche Aktionen wie Löschen verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-130">Reveal mode is a safer, more versatile swipe mode, and can be used for most types of menu actions, even potentially destructive actions, such as deletion.</span></span>

<span data-ttu-id="0b9bf-131">Wenn der Benutzer eine der Menüoptionen auswählt, die im geöffneten und positionierten Zustand des Anzeigemodus angezeigt werden, wird der Befehl für dieses Element aufgerufen und das Steuerelement „Wischen“ geschlossen.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-131">When the user selects one of the menu options shown in the reveal's open and resting state, the command for that item is invoked and the swipe control is closed.</span></span>

### <a name="execute-mode"></a><span data-ttu-id="0b9bf-132">Ausführungsmodus</span><span class="sxs-lookup"><span data-stu-id="0b9bf-132">Execute mode</span></span>

<span data-ttu-id="0b9bf-133">Im Ausführungsmodus wischt der Benutzer über ein Element, um einen einzelnen Befehl mit dem Wischvorgang anzuzeigen oder auszuführen.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-133">In Execute mode, the user swipes an item open to reveal and execute a single command with that one swipe.</span></span> <span data-ttu-id="0b9bf-134">Wenn der Benutzer das Element, über das er gewischt hat, loslässt, bevor er über einen Schwellenwert hinaus wischt, wird das Menü wird geschlossen und der Befehl nicht ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-134">If the user releases the item being swiped before they swipe past a threshold, the menu closes and the command is not executed.</span></span> <span data-ttu-id="0b9bf-135">Wenn der Benutzer über den Schwellenwert hinaus wischt und das Element dann loslässt, wird der Befehl sofort ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-135">If the user swipes past the threshold and then releases the item, the command is executed immediately.</span></span>

![Ausführen per Wischen](images/SwipeCommand_Delete_v2.gif)

<span data-ttu-id="0b9bf-137">Wenn der Benutzer seinen Finger nach dem Erreichen des Schwellenwerts nicht loslässt und das Element durch Wischen wieder geschlossen wird, wird weder der Befehl noch eine Aktion für das Element ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-137">If the user does not release their finger after the threshold is reached, and pulls the swipe item closed again, the command is not executed  and no action is performed on the item.</span></span>

<span data-ttu-id="0b9bf-138">Der Ausführungsmodus bietet visuelles Feedback durch Farbe und den Bezeichnungstext, während ein Element gezogen wird.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-138">Execute mode provides more visual feedback through color and label orientation while an item is being swiped.</span></span>

<span data-ttu-id="0b9bf-139">Der Ausführungsmodus ist besonders hilfreich, wenn der Benutzer ihn für eine häufig durchgeführte Aktion verwendet.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-139">Execute is best used when the action the user is performing is most common.</span></span>

<span data-ttu-id="0b9bf-140">Er kann auch für destruktivere Aktionen wie das Löschen eines Elements verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-140">It may also be used for more destructive actions like deleting an item.</span></span> <span data-ttu-id="0b9bf-141">Beachten Sie jedoch, dass „Ausführen“ nur eine Wischaktion in eine Richtung erfordert, während der Benutzer für „Anzeigen“ ausdrücklich auf eine Schaltfläche klicken muss.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-141">However, keep in mind that Execute requires only one action of swiping in a direction, as opposed to Reveal, which requires the user to explicitly click on a button.</span></span>

### <a name="swipe-directions"></a><span data-ttu-id="0b9bf-142">Wischrichtungen</span><span class="sxs-lookup"><span data-stu-id="0b9bf-142">Swipe directions</span></span>

<span data-ttu-id="0b9bf-143">Es kann in alle Richtungen gewischt werden: nach oben, unten, links und rechts.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-143">Swipe works in all cardinal directions: up, down, left, and right.</span></span> <span data-ttu-id="0b9bf-144">Jede Wischrichtung kann eigene Wischelemente oder Inhalte enthalten, es kann allerdings jeweils nur eine Instanz der Richtung für ein einzelnes Element festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-144">Each swipe direction can hold its own swipe items or content, but only one instance of a direction can be set at a time on a single swipe-able element.</span></span>

<span data-ttu-id="0b9bf-145">Beispielsweise sind zwei [LeftItems](/uwp/api/windows.ui.xaml.controls.swipecontrol.LeftItems)-Definitionen für dasselbe SwipeControl nicht möglich.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-145">For example, you cannot have two [LeftItems](/uwp/api/windows.ui.xaml.controls.swipecontrol.LeftItems) definitions on the same SwipeControl.</span></span>

## <a name="how-to-create-a-swipe-command"></a><span data-ttu-id="0b9bf-146">Erstellen eines Wischbefehls</span><span class="sxs-lookup"><span data-stu-id="0b9bf-146">How to create a Swipe command</span></span>

<span data-ttu-id="0b9bf-147">Wischbefehle verfügen über zwei Komponenten, die Sie definieren müssen:</span><span class="sxs-lookup"><span data-stu-id="0b9bf-147">Swipe commands have two components that you need to define:</span></span>

- <span data-ttu-id="0b9bf-148">[SwipeControl](/uwp/api/windows.ui.xaml.controls.swipecontrol), das Inhalte umschließt.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-148">The [SwipeControl](/uwp/api/windows.ui.xaml.controls.swipecontrol), which wraps around your content.</span></span> <span data-ttu-id="0b9bf-149">In einer Sammlung, z.B. eine ListView, befindet sich diese innerhalb der DataTemplate.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-149">In a collection, such as a ListView, this sits within your DataTemplate.</span></span>
- <span data-ttu-id="0b9bf-150">Die Elemente des Menüs „Wischen“, bei denen es sich um mindestens ein [SwipeItem](/uwp/api/windows.ui.xaml.controls.swipeitem)-Objekt handelt, das in direktionalen Containern des Steuerelements „Wischen“ platziert ist: [LeftItems](/uwp/api/windows.ui.xaml.controls.swipecontrol.LeftItems), [RightItems](/uwp/api/windows.ui.xaml.controls.swipecontrol.RightItems), [TopItems](/uwp/api/windows.ui.xaml.controls.swipecontrol.TopItems) oder [BottomItems](/uwp/api/windows.ui.xaml.controls.swipecontrol.BottomItems)</span><span class="sxs-lookup"><span data-stu-id="0b9bf-150">The swipe menu items, which is one or more [SwipeItem](/uwp/api/windows.ui.xaml.controls.swipeitem) objects placed in the swipe control's directional containers: [LeftItems](/uwp/api/windows.ui.xaml.controls.swipecontrol.LeftItems), [RightItems](/uwp/api/windows.ui.xaml.controls.swipecontrol.RightItems), [TopItems](/uwp/api/windows.ui.xaml.controls.swipecontrol.TopItems), or [BottomItems](/uwp/api/windows.ui.xaml.controls.swipecontrol.BottomItems)</span></span>

<span data-ttu-id="0b9bf-151">Inhalte zum Wischen können als Inline-Inhalte platziert oder im Abschnitt „Ressourcen“ Ihrer Seite oder App platziert werden.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-151">Swipe content can be placed inline, or defined in the Resources section of your page or app.</span></span>

<span data-ttu-id="0b9bf-152">Nachfolgend finden Sie ein Beispiel für ein SwipeControl, das Text umschließt.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-152">Here's a simple example of a SwipeControl wrapped around some text.</span></span> <span data-ttu-id="0b9bf-153">Es zeigt die Hierarchie der XAML-Elemente, die zum Erstellen eines Wischbefehls erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-153">It shows the hierarchy of XAML elements required to create a swipe command.</span></span>

```xaml
<SwipeControl HorizontalAlignment="Center" VerticalAlignment="Center">
    <SwipeControl.LeftItems>
        <SwipeItems>
            <SwipeItem Text="Pin">
                <SwipeItem.IconSource>
                    <SymbolIconSource Symbol="Pin"/>
                </SwipeItem.IconSource>
            </SwipeItem>
        </SwipeItems>
    </SwipeControl.LeftItems>

     <!-- Swipeable content -->
    <Border Width="180" Height="44" BorderBrush="Black" BorderThickness="2">
        <TextBlock Text="Swipe to Pin" Margin="4,8,0,0"/>
    </Border>
</SwipeControl>
```

<span data-ttu-id="0b9bf-154">In diesem Thema befassen wir uns mit einem vollständigeren Beispiel dazu, wie Wischbefehle normalerweise in einer Liste verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-154">Now we'll take a look at a more complete example of how you would typically use swipe commands in a list.</span></span> <span data-ttu-id="0b9bf-155">In diesem Beispiel richten Sie einen Löschbefehl ein, der den Ausführungsmodus verwendet, und ein Menü mit anderen Befehlen, die den Anzeigemodus verwenden.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-155">In this example, you'll set up a delete command that uses Execute mode, and a menu of other commands that uses Reveal mode.</span></span> <span data-ttu-id="0b9bf-156">Beide Befehlsgruppen werden im Abschnitt „Ressourcen“ der Seite definiert.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-156">Both sets of commands are defined in the Resources section of the page.</span></span> <span data-ttu-id="0b9bf-157">Sie wenden die Wischbefehle auf die Elemente in einer ListView an.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-157">You'll apply the swipe commands to the items in a ListView.</span></span>

<span data-ttu-id="0b9bf-158">Erstellen Sie zunächst die Wischelemente, die die Befehle darstellen, als Ressourcen auf Seitenebene.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-158">First, create the swipe items, which represent the commands, as page level resources.</span></span> <span data-ttu-id="0b9bf-159">SwipeItem verwendet eine [IconSource](/uwp/api/windows.ui.xaml.controls.iconsource) als Symbol.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-159">SwipeItem uses an [IconSource](/uwp/api/windows.ui.xaml.controls.iconsource) as its icon.</span></span> <span data-ttu-id="0b9bf-160">Erstellen Sie die Symbole ebenfalls als Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-160">Create the icons as resources, too.</span></span>

```xaml
<Page.Resources>
    <SymbolIconSource x:Key="ReplyIcon" Symbol="MailReply"/>
    <SymbolIconSource x:Key="DeleteIcon" Symbol="Delete"/>
    <SymbolIconSource x:Key="PinIcon" Symbol="Pin"/>

    <SwipeItems x:Key="RevealOptions" Mode="Reveal">
        <SwipeItem Text="Reply" IconSource="{StaticResource ReplyIcon}"/>
        <SwipeItem Text="Pin" IconSource="{StaticResource PinIcon}"/>
    </SwipeItems>

    <SwipeItems x:Key="ExecuteDelete" Mode="Execute">
        <SwipeItem Text="Delete" IconSource="{StaticResource DeleteIcon}"
                   Background="Red"/>
    </SwipeItems>
</Page.Resources>
```

<span data-ttu-id="0b9bf-161">Denken Sie daran, die Menüelemente in Ihren Wischinhalten mit knappen und präzisen Beschriftungen beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-161">Remember to keep the menu items in your swipe content to short, concise text labels.</span></span> <span data-ttu-id="0b9bf-162">Diese Aktionen sollten die primären Aktionen werden, die ein Benutzer möglicherweise mehrmals innerhalb eines kurzen Zeitraums ausführen möchte.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-162">These actions should be the primary ones that a user may want to perform multiple times over a short period.</span></span>

<span data-ttu-id="0b9bf-163">Das Einrichten eines Wischbefehls für die Verwendung in einer Sammlung oder ListView erfolgt auf genau die gleiche Weise wie das Definieren eines einzelnen Wischbefehls (wie oben gezeigt), mit der Ausnahme, dass das SwipeControl in einer DataTemplate definiert wird, damit es auf jedes Element in der Sammlung angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-163">Setting up a swipe command to work in a collection or ListView is exactly the same as defining a single swipe command (shown previously), except you define your SwipeControl in a DataTemplate so it's applied to each item in the collection.</span></span>

<span data-ttu-id="0b9bf-164">Hier ist eine ListView mit der SwipeControl, die im DataTemplate-Element angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-164">Here's a ListView with the SwipeControl applied in its item DataTemplate.</span></span> <span data-ttu-id="0b9bf-165">Die Eigenschaften „LeftItems“ und „RightItems“ verweisen auf die Wischelemente, die Sie als Ressourcen erstellen.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-165">The LeftItems and RightItems properties reference the swipe items that you created as resources.</span></span>

```xaml
<ListView x:Name="sampleList" Width="300">
    <ListView.ItemContainerStyle>
        <Style TargetType="ListViewItem">
            <Setter Property="HorizontalContentAlignment" Value="Stretch"/>
            <Setter Property="VerticalContentAlignment" Value="Stretch"/>
        </Style>
    </ListView.ItemContainerStyle>
    <ListView.ItemTemplate>
        <DataTemplate x:DataType="x:String">
            <SwipeControl x:Name="ListViewSwipeContainer"
                          LeftItems="{StaticResource RevealOptions}"
                          RightItems="{StaticResource ExecuteDelete}"
                          Height="60">
                <StackPanel Orientation="Vertical">
                    <TextBlock Text="{x:Bind}" FontSize="18"/>
                    <StackPanel Orientation="Horizontal">
                        <TextBlock Text="Lorem ipsum dolor sit amet, consectetur adipiscing elit..." FontSize="12"/>
                    </StackPanel>
                </StackPanel>
            </SwipeControl>
        </DataTemplate>
    </ListView.ItemTemplate>
    <x:String>Item 1</x:String>
    <x:String>Item 2</x:String>
    <x:String>Item 3</x:String>
    <x:String>Item 4</x:String>
    <x:String>Item 5</x:String>
</ListView>
```

## <a name="handle-an-invoked-swipe-command"></a><span data-ttu-id="0b9bf-166">Behandeln eines aufgerufenen Wischbefehls</span><span class="sxs-lookup"><span data-stu-id="0b9bf-166">Handle an invoked swipe command</span></span>

<span data-ttu-id="0b9bf-167">Um auf einen Wischbefehl zu reagieren, behandeln Sie dessen [Invoked](/uwp/api/windows.ui.xaml.controls.swipeitem.Invoked)-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-167">To act on a swipe command, you handle its [Invoked](/uwp/api/windows.ui.xaml.controls.swipeitem.Invoked) event.</span></span> <span data-ttu-id="0b9bf-168">(Weitere Informationen dazu, wie ein Benutzer einen Befehl aufruft, finden Sie im Abschnitt _Funktionsweise von Wischen_ weiter oben in diesem Artikel.) Ein Wischbefehl befindet sich in der Regel in einer ListView oder in einem listenähnlichen Szenario.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-168">(For more info about a how a user can invoke a command, review the _How does swipe work?_ section earlier in this article.) Typically, a swipe command is in a ListView or list-like scenario.</span></span> <span data-ttu-id="0b9bf-169">Wenn dann ein Befehl aufgerufen wird, können Sie eine Aktion für das gezogene Element ausführen.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-169">In that case, when a command is invoked, you want to perform an action on that swiped item.</span></span>

<span data-ttu-id="0b9bf-170">Gehen Sie zum Behandeln des Invoked-Ereignisses für das zuvor erstellte Wischelement _delete_ wie folgt vor.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-170">Here's how to handle the Invoked event on the _delete_ swipe item you created previously.</span></span>

```xaml
<SwipeItems x:Key="ExecuteDelete" Mode="Execute">
    <SwipeItem Text="Delete" IconSource="{StaticResource DeleteIcon}"
               Background="Red" Invoked="Delete_Invoked"/>
</SwipeItems>
```

<span data-ttu-id="0b9bf-171">Bei dem Datenelement handelt es sich um das SwipeControl von DataContext.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-171">The data item is the DataContext of the SwipeControl.</span></span> <span data-ttu-id="0b9bf-172">In Ihrem Code können Sie auf das Element zugreifen, das durch Abrufen der SwipeControl.DataContext-Eigenschaft aus den Ereignisargumenten gezogen wurde, wie hier gezeigt.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-172">In your code, you can access the item that was swiped by getting the SwipeControl.DataContext property from the event args, as shown here.</span></span>

```csharp
 private void Delete_Invoked(SwipeItem sender, SwipeItemInvokedEventArgs args)
 {
     sampleList.Items.Remove(args.SwipeControl.DataContext);
 }
```

> [!NOTE]
> <span data-ttu-id="0b9bf-173">Hier wurden die Elemente der ListView.Items-Sammlung der Einfachheit halber direkt hinzugefügt, damit das Element ebenfalls auf die gleiche Weise gelöscht wird.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-173">Here, the items were added directly to the ListView.Items collection for simplicity, so the item is also deleted the same way.</span></span> <span data-ttu-id="0b9bf-174">Wenn Sie die ListView.ItemsSource stattdessen auf eine Sammlung festlegen, was üblicher ist, müssen Sie das Element aus der Quellsammlung löschen.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-174">If you instead set the ListView.ItemsSource to a collection, which is more typical, you need to delete the item from the source collection.</span></span>

<span data-ttu-id="0b9bf-175">In diesem speziellen Fall haben Sie das Element aus der Liste entfernt, sodass der endgültige visuelle Zustand des gezogenen Elements nicht von Bedeutung ist.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-175">In this particular instance, you removed the item from the list, so the final visual state of the swiped item isn't important.</span></span> <span data-ttu-id="0b9bf-176">In Situationen, in denen Sie einfach eine Aktion ausführen möchten und die Wischsteuerung danach wieder zuklappen möchten, können Sie die Eigenschaft [BehaviorOnInvoked](/uwp/api/windows.ui.xaml.controls.swipeitem.BehaviorOnInvoked) auf einen der [SwipeBehaviorOnInvoked](/uwp/api/windows.ui.xaml.controls.swipebehavioroninvoked)-Enumerationswerte festlegen.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-176">However, in situations where you simply want to perform an action and then have the swipe collapse again, you can set the [BehaviorOnInvoked](/uwp/api/windows.ui.xaml.controls.swipeitem.BehaviorOnInvoked) property one of the [SwipeBehaviorOnInvoked](/uwp/api/windows.ui.xaml.controls.swipebehavioroninvoked) enum values.</span></span>

- **<span data-ttu-id="0b9bf-177">Auto</span><span class="sxs-lookup"><span data-stu-id="0b9bf-177">Auto</span></span>**
  - <span data-ttu-id="0b9bf-178">Im Ausführungsmodus bleibt das geöffnete Wischelement beim Aufrufen geöffnet.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-178">In Execute mode, the opened swipe item will remain open when invoked.</span></span>
  - <span data-ttu-id="0b9bf-179">Im Anzeigemodus bleibt das geöffnete Wischelement beim Aufrufen reduziert.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-179">In Reveal mode, the opened swipe item will collapse when invoked.</span></span>
- **<span data-ttu-id="0b9bf-180">Schließen</span><span class="sxs-lookup"><span data-stu-id="0b9bf-180">Close</span></span>**
  - <span data-ttu-id="0b9bf-181">Wenn das Element aufgerufen wird, wird das Steuerelement „Wischen“ immer zugeklappt und kehrt unabhängig vom jeweiligen Modus zum Normalzustand zurück.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-181">When the item is invoked, the swipe control will always collapse and return to normal, regardless of the mode.</span></span>
- **<span data-ttu-id="0b9bf-182">RemainOpen</span><span class="sxs-lookup"><span data-stu-id="0b9bf-182">RemainOpen</span></span>**
  - <span data-ttu-id="0b9bf-183">Wenn das Element aufgerufen wird, bleibt das Steuerelement „Wischen“ unabhängig vom jeweiligen Modus immer geöffnet.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-183">When the item is invoked, the swipe control will always stay open, regardless of the mode.</span></span>

<span data-ttu-id="0b9bf-184">Hier wird ein Wischelement vom Typ _Antwort_ so festgelegt, dass es nach dem Aufrufen geschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-184">Here, a _reply_ swipe item is set to close after its invoked.</span></span>

```xaml
<SwipeItem Text="Reply" IconSource="{StaticResource ReplyIcon}"
           Invoked="Reply_Invoked"
           BehaviorOnInvoked = "Close"/>
```

## <a name="dos-and-donts"></a><span data-ttu-id="0b9bf-185">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="0b9bf-185">Dos and don'ts</span></span>

- <span data-ttu-id="0b9bf-186">Verwenden Sie den Wischvorgang nicht bei FlipViews, Hubs oder Pivots.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-186">Don't use swipe in FlipViews, Hubs or Pivots.</span></span> <span data-ttu-id="0b9bf-187">Die Kombination kann aufgrund von in Konflikt stehenden Wischrichtungen für den Benutzer verwirrend sein.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-187">The combination may be confusing for the user because of conflicting swipe directions.</span></span>
- <span data-ttu-id="0b9bf-188">Kombinieren Sie das horizontale Wischen nicht mit horizontaler Navigation bzw. das vertikale Wischen mit vertikaler Navigation.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-188">Don't combine horizontal swipe with horizontal navigation, or vertical swipe with vertical navigation.</span></span>
- <span data-ttu-id="0b9bf-189">Stellen Sie sicher, das der vom Benutzer durchgeführte Wischvorgang dieselbe Aktion ist und konsistent für alle bezogenen, wischfähigen Elemente durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-189">Do make sure what the user is swiping is the same action, and is consistent across all related items that can be swiped.</span></span>
- <span data-ttu-id="0b9bf-190">Verwenden Sie „Wischen“ für die Hauptaktionen, die Benutzer ausführen.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-190">Do use swipe for the main actions a user will want to perform.</span></span>
- <span data-ttu-id="0b9bf-191">Verwenden Sie „Wischen” für Elemente, bei denen die gleiche Aktion mehrmals wiederholt wird.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-191">Do use swipe on items where the same action is repeated many times.</span></span>
- <span data-ttu-id="0b9bf-192">Verwenden Sie horizontales Wischen bei größeren und vertikales Wischen bei kleineren Elementen.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-192">Do use horizontal swiping on wider items, and vertical swiping on taller items.</span></span>
- <span data-ttu-id="0b9bf-193">Verwenden Sie kurze und knappe Beschriftungen.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-193">Do use short, concise text labels.</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="0b9bf-194">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="0b9bf-194">Get the sample code</span></span>

- <span data-ttu-id="0b9bf-195">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="0b9bf-195">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="0b9bf-196">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="0b9bf-196">Related articles</span></span>

- [<span data-ttu-id="0b9bf-197">Listenansicht und Rasteransicht</span><span class="sxs-lookup"><span data-stu-id="0b9bf-197">List view and Grid view</span></span>](listview-and-gridview.md)
- [<span data-ttu-id="0b9bf-198">Elementcontainer und Vorlagen</span><span class="sxs-lookup"><span data-stu-id="0b9bf-198">Item containers and templates</span></span>](item-containers-templates.md)
- [<span data-ttu-id="0b9bf-199">Aktualisieren durch Ziehen</span><span class="sxs-lookup"><span data-stu-id="0b9bf-199">Pull to refresh</span></span>](pull-to-refresh.md)
