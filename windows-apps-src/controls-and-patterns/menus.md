---
author: mijacobs
Description: "Ein Flyout ist ein kleines Popupmenü, das vorübergehend UI zu aktuellen Benutzeraktionen anzeigt."
title: "Menüs und Kontextmenüs"
label: Menus and context menus
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.assetid: 0327d8c1-8329-4be2-84e3-66e1e9a0aa60
pm-contact: yulikl
design-contact: kimsea
dev-contact: llongley
doc-status: Published
ms.openlocfilehash: a53c71e999b94e2ad25ad21b9eec09b81681c0a4
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="menus-and-context-menus"></a><span data-ttu-id="fba55-104">Menüs und Kontextmenüs</span><span class="sxs-lookup"><span data-stu-id="fba55-104">Menus and context menus</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

<span data-ttu-id="fba55-105">Menüs und Kontextmenüs zeigen auf Anforderung des Benutzers eine Liste von Befehlen oder Optionen an.</span><span class="sxs-lookup"><span data-stu-id="fba55-105">Menus and context menus display a list of commands or options when the user requests them.</span></span>

> <span data-ttu-id="fba55-106">**Wichtige APIs**: [MenuFlyout-Klasse](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.MenuFlyout), [ContextFlyout-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx), [FlyoutBase.AttachedFlyout-Eigenschaft](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout.aspx)</span><span class="sxs-lookup"><span data-stu-id="fba55-106">**Important APIs**: [MenuFlyout class](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.MenuFlyout), [ContextFlyout property](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx), [FlyoutBase.AttachedFlyout property](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout.aspx)</span></span>

![Beispiel für ein typisches Kontextmenü](images/contextmenu_rs2_icons.png)


## <a name="is-this-the-right-control"></a><span data-ttu-id="fba55-108">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="fba55-108">Is this the right control?</span></span>
<span data-ttu-id="fba55-109">Menüs und Kontextmenüs sparen Platz, indem Befehle angeordnet und ausgeblendet werden, bis der Benutzer sie benötigt.</span><span class="sxs-lookup"><span data-stu-id="fba55-109">Menus and context menus save space by organizing commands and hiding them until the user needs them.</span></span> <span data-ttu-id="fba55-110">Wenn ein bestimmter Befehl häufig verwendet wird und Sie genügend Platz haben, sollten Sie ihn direkt als eigenes Element und nicht in einem Menü platzieren, damit Benutzer das Menü nicht durchlaufen müssen, um ihn aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="fba55-110">If a particular command will be used frequently and you have the space available, consider placing it directly in its own element, rather than in a menu, so that users don't have to go through a menu to get to it.</span></span>

<span data-ttu-id="fba55-111">Menüs und Kontextmenüs dienen dazu, Befehle strukturiert anzuordnen. Um beliebige Inhalte anzuzeigen, z. B. eine Benachrichtigung oder die Bestätigung einer Anfrage, verwenden Sie ein [Dialogfeld oder Flyout](dialogs.md).</span><span class="sxs-lookup"><span data-stu-id="fba55-111">Menus and context menus are for organizing commands; to display arbitrary content, such as an notification or to request confirmation, use a [dialog or a flyout](dialogs.md).</span></span>  


## <a name="menus-vs-context-menus"></a><span data-ttu-id="fba55-112">Vergleich zwischen Menüs und Kontextmenüs</span><span class="sxs-lookup"><span data-stu-id="fba55-112">Menus vs. context menus</span></span>

<span data-ttu-id="fba55-113">Menüs und Kontextmenüs sind identisch, was ihr Erscheinungsbild und ihren Inhalt angeht.</span><span class="sxs-lookup"><span data-stu-id="fba55-113">Menus and context menus are identical in how they look and what they can contain.</span></span> <span data-ttu-id="fba55-114">Tatsächlich werden beide mit demselben Steuerelement erstellt, [MenuFlyout](https://msdn.microsoft.com/library/windows/apps/dn299030).</span><span class="sxs-lookup"><span data-stu-id="fba55-114">In fact, you use the same control, [MenuFlyout](https://msdn.microsoft.com/library/windows/apps/dn299030), to create them.</span></span> <span data-ttu-id="fba55-115">Der einzige Unterschied ist, wie Sie den Benutzer darauf zugreifen lassen.</span><span class="sxs-lookup"><span data-stu-id="fba55-115">The only difference is how you let the user access it.</span></span>

<span data-ttu-id="fba55-116">Wann sollten Sie ein Menü und wann ein Kontextmenü verwenden?</span><span class="sxs-lookup"><span data-stu-id="fba55-116">When should you use a menu or a context menu?</span></span>
* <span data-ttu-id="fba55-117">Ist das übergeordnete Element eine Schaltfläche oder ein anderes Befehlselement, dessen primäre Funktion es ist, weitere Befehle zu präsentieren, verwenden Sie ein Menü.</span><span class="sxs-lookup"><span data-stu-id="fba55-117">If the host element is a button or some other command element who's primary role is to present additional commands, use a menu.</span></span>
* <span data-ttu-id="fba55-118">Wenn das übergeordnete Element eine andere Art von Element ist, das hauptsächlich einem anderen Zweck dient (z. B. der Anzeige von Text oder einem Bild), verwenden Sie ein Kontextmenü.</span><span class="sxs-lookup"><span data-stu-id="fba55-118">If the host element is some other type of element that has another primary purpose (such as presenting text or an image), use a context menu.</span></span>

<span data-ttu-id="fba55-119">Verwenden Sie beispielsweise ein Menü auf einer Schaltfläche in einem Navigationsbereich, um zusätzliche Navigationsoptionen bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="fba55-119">For example, use a menu on a button in a navigation pane to provide additional navigation options.</span></span> <span data-ttu-id="fba55-120">Der Hauptzweck des Schaltflächen-Steuerelements ist in diesem Szenario, auf ein Menü zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="fba55-120">In this scenario, the primary purpose of the button control is to provide access to a menu.</span></span>

<span data-ttu-id="fba55-121">Wenn Sie Befehle (z. B. Ausschneiden, Kopieren und Einfügen) hinzufügen möchten, verwenden Sie ein Kontextmenü anstelle eines Menüs.</span><span class="sxs-lookup"><span data-stu-id="fba55-121">If you want to add commands (such as cut, copy, and paste) to a text element, use a context menu instead of a menu.</span></span> <span data-ttu-id="fba55-122">In diesem Szenario ist die Hauptfunktion des Textelements Text zur Ansicht und zum Bearbeiten anzuzeigen. Weitere Befehle (z. B. Ausschneiden, Kopieren und Einfügen) sind sekundär und gehören in ein Kontextmenü.</span><span class="sxs-lookup"><span data-stu-id="fba55-122">In this scenario, the primary role of the text element is to present and edit text; additional commands (such as cut, copy, and paste) are secondary and belong in a context menu.</span></span>

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
   <p><b><span data-ttu-id="fba55-123">Menüs</span><span class="sxs-lookup"><span data-stu-id="fba55-123">Menus</span></span></b></p>
<ul>
<li><span data-ttu-id="fba55-124">Haben Sie einen einzigen Einstiegspunkt (am oberen Bildschirmrand, z. B. über ein Menü „Datei“), der immer angezeigt wird</span><span class="sxs-lookup"><span data-stu-id="fba55-124">Have a single entry point (a File menu at the top of the screen, for example) that is always displayed.</span></span></li>
<li><span data-ttu-id="fba55-125">Werden in der Regel an eine Schaltfläche oder ein übergeordnetes Menüelement angehängt</span><span class="sxs-lookup"><span data-stu-id="fba55-125">Are usually attached to a button or a parent menu item.</span></span></li>
<li><span data-ttu-id="fba55-126">Werden mit der linken Maustaste (oder einer entsprechenden Aktion, z. B. durch Tippen) aufgerufen</span><span class="sxs-lookup"><span data-stu-id="fba55-126">Are invoked by left-clicking (or an equivalent action, such as tapping with your finger).</span></span></li><li><span data-ttu-id="fba55-127">Werden Elementen über ihre [Flyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.button.flyout.aspx)- oder [FlyoutBase.AttachedFlyout](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout.aspx)-Eigenschaft zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="fba55-127">Are associated with an element via its [Flyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.button.flyout.aspx) or [FlyoutBase.AttachedFlyout](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout.aspx) properties.</span></span></li>
</ul>
</div>
  <div class="side-by-side-content-right">
   <p><b><span data-ttu-id="fba55-128">Kontextmenüs</span><span class="sxs-lookup"><span data-stu-id="fba55-128">Context menus</span></span></b></p>

<ul>
<li><span data-ttu-id="fba55-129">Sind mit einem einzelnen Element verknüpft und zeigen Sekundärbefehle an.</span><span class="sxs-lookup"><span data-stu-id="fba55-129">Are attached to a single element and display secondary commands.</span></span></li>
<li><span data-ttu-id="fba55-130">Werden mit der rechten Maustaste (oder einer entsprechenden Aktion, z. B. durch Tippen und Halten) aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="fba55-130">Are invoked by right clicking (or an equivalent action, such as pressing and holding with your finger).</span></span></li><li><span data-ttu-id="fba55-131">Sind mit einem Element über dessen [ContextFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx)-Eigenschaft verknüpft.</span><span class="sxs-lookup"><span data-stu-id="fba55-131">Are associated with an element via its [ContextFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx) property.</span></span></li>
</ul>
  </div>
</div>
</div>

## <a name="icons"></a><span data-ttu-id="fba55-132">Symbole</span><span class="sxs-lookup"><span data-stu-id="fba55-132">Icons</span></span>

<span data-ttu-id="fba55-133">Erwägen Sie in folgenden Fällen Symbole für die Menüpunkte einzurichten:</span><span class="sxs-lookup"><span data-stu-id="fba55-133">Consider providing menu item icons for:</span></span>

<ul>
<li> <span data-ttu-id="fba55-134">Für am häufigsten verwendete Elemente</span><span class="sxs-lookup"><span data-stu-id="fba55-134">The most commonly used items</span></span> </li>
<li> <span data-ttu-id="fba55-135">Für Menüpunkte, für die allgemein bekannte oder Standardsymbole vorhanden sind</span><span class="sxs-lookup"><span data-stu-id="fba55-135">Menu items whose icon is standard or well known</span></span> </li>
<li> <span data-ttu-id="fba55-136">Für Menüpunkte, deren Funktion auf einfache Weise mit einem Symbol veranschaulicht werden kann</span><span class="sxs-lookup"><span data-stu-id="fba55-136">Menu items whose icon well illustrates what the command does</span></span> </li>
</ul>

<span data-ttu-id="fba55-137">Fühlen Sie sich nicht dazu verpflichtet, alle Menüpunkte mit einem Symbol zu versehen. Insbesondere dann, wenn es sich um ein langes Menü handelt oder keine Standardsymbole vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="fba55-137">Do not feel obligated to provide icons for every menu item, especially if the menu is long, or the command does not have a standard visualization.</span></span> <span data-ttu-id="fba55-138">Kryptische Symbole sind nicht hilfreich, machen das Menü unübersichtlich und hindern Benutzer daran, wichtige Menüpunkte einfach aufzufinden.</span><span class="sxs-lookup"><span data-stu-id="fba55-138">Cryptic icons aren’t helpful, create visual clutter, and prevent users from focusing on the important menu items.</span></span>

![Beispiel für ein Kontextmenü mit Symbolen](images/contextmenu_rs2_icons.png)

````xaml
<MenuFlyout>
  <MenuFlyoutItem Text="Share" >
    <MenuFlyoutItem.Icon>
      <FontIcon Glyph="&#xE72D;" />
    </MenuFlyoutItem.Icon>
  </MenuFlyoutItem>
  <MenuFlyoutItem Text="Copy" Icon="Copy" />
  <MenuFlyoutItem Text="Delete" Icon="Delete" />
  <MenuFlyoutSeparator />
  <MenuFlyoutItem Text="Rename" />
  <MenuFlyoutItem Text="Select" />
</MenuFlyout>
````
> <span data-ttu-id="fba55-140">Die Größe der Symbole für MenuFlyoutItems ist 16x16px.</span><span class="sxs-lookup"><span data-stu-id="fba55-140">The size of the icons in MenuFlyoutItems is 16x16px.</span></span> <span data-ttu-id="fba55-141">Wenn Sie SymbolIcon, FontIcon oder PathIcon verwenden, wird das Symbol automatisch verlustfrei auf die richtige Größe skaliert.</span><span class="sxs-lookup"><span data-stu-id="fba55-141">If you use SymbolIcon, FontIcon, or PathIcon, the icon will automatically scale to the correct size with no loss of fidelity.</span></span> <span data-ttu-id="fba55-142">Achten Sie bei der Verwendung von BitmapIcon darauf, dass Ihr Element 16x16px groß sein muss.</span><span class="sxs-lookup"><span data-stu-id="fba55-142">If you use BitmapIcon, ensure that your asset is 16x16px.</span></span>  

## <a name="create-a-menu-or-a-context-menu"></a><span data-ttu-id="fba55-143">Erstellen eines Menüs bzw. Kontextmenüs</span><span class="sxs-lookup"><span data-stu-id="fba55-143">Create a menu or a context menu</span></span>

<span data-ttu-id="fba55-144">Um ein Menü oder ein Kontextmenü zu erstellen, verwenden Sie die [MenuFlyout-Klasse](https://msdn.microsoft.com/library/windows/apps/dn299030).</span><span class="sxs-lookup"><span data-stu-id="fba55-144">To create a menu or a content menu, you use the [MenuFlyout class](https://msdn.microsoft.com/library/windows/apps/dn299030).</span></span> <span data-ttu-id="fba55-145">Sie definieren den Inhalt des Menüs, indem Sie dem MenuFlyout [MenuFlyoutItem](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutitem.aspx)-, [ToggleMenuFlyoutItem](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/windows.ui.xaml.controls.togglemenuflyoutitem.aspx)- und [MenuFlyoutSeparator](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutseparator.aspx)-Objekte hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="fba55-145">You define the contents of the menu by adding [MenuFlyoutItem](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutitem.aspx), [ToggleMenuFlyoutItem](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/windows.ui.xaml.controls.togglemenuflyoutitem.aspx), and [MenuFlyoutSeparator](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutseparator.aspx) objects to the MenuFlyout.</span></span> <span data-ttu-id="fba55-146">Diese Objekte erfüllen folgende Zwecke:</span><span class="sxs-lookup"><span data-stu-id="fba55-146">These objects are for:</span></span>
* <span data-ttu-id="fba55-147">[MenuFlyoutItem](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutitem.aspx): Ausführen einer sofortigen Aktion</span><span class="sxs-lookup"><span data-stu-id="fba55-147">[MenuFlyoutItem](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutitem.aspx)—Performing an immediate action.</span></span>
* <span data-ttu-id="fba55-148">[ToggleMenuFlyoutItem](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/windows.ui.xaml.controls.togglemenuflyoutitem.aspx): Ein- und Ausschalten einer Option</span><span class="sxs-lookup"><span data-stu-id="fba55-148">[ToggleMenuFlyoutItem](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/windows.ui.xaml.controls.togglemenuflyoutitem.aspx)—Switching an option on or off.</span></span>
* <span data-ttu-id="fba55-149">[MenuFlyoutSeparator](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutseparator.aspx)—Optisches Trennen von Menüelementen</span><span class="sxs-lookup"><span data-stu-id="fba55-149">[MenuFlyoutSeparator](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutseparator.aspx)—Visually separating menu items.</span></span>


<span data-ttu-id="fba55-150">In diesem Beispiel wird ein [MenuFlyout-Klasse](https://msdn.microsoft.com/library/windows/apps/dn299030) erstellt, und anschließend wird mit der [ContextFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx)-Eigenschaft, die für die meisten Steuerelemente verfügbar ist, die [MenuFlyout-Klasse](https://msdn.microsoft.com/library/windows/apps/dn299030) als Kontextmenü angezeigt.</span><span class="sxs-lookup"><span data-stu-id="fba55-150">This example creates a [MenuFlyout class](https://msdn.microsoft.com/library/windows/apps/dn299030) and uses the [ContextFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx) property, a property available to most controls, to show the [MenuFlyout class](https://msdn.microsoft.com/library/windows/apps/dn299030) as a context menu.</span></span>

````xaml
<Rectangle
  Height="100" Width="100"
  Tapped="Rectangle_Tapped">
  <Rectangle.ContextFlyout>
    <MenuFlyout>
      <MenuFlyoutItem Text="Change color" Click="ChangeColorItem_Click" />
    </MenuFlyout>
  </Rectangle.ContextFlyout>
  <Rectangle.Fill>
    <SolidColorBrush x:Name="rectangleFill" Color="Red" />
  </Rectangle.Fill>
</Rectangle>
````

````csharp
private void ChangeColorItem_Click(object sender, RoutedEventArgs e)
{
    // Change the color from red to blue or blue to red.
    if (rectangleFill.Color == Windows.UI.Colors.Red)
    {
        rectangleFill.Color = Windows.UI.Colors.Blue;
    }
    else
    {
        rectangleFill.Color = Windows.UI.Colors.Red;
    }
}
````

<span data-ttu-id="fba55-151">Das nächste Beispiel ist nahezu identisch, aber anstelle der [ContextFlyout](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx)-Eigenschaft zur Anzeige der [MenuFlyout-Klasse](https://msdn.microsoft.com/library/windows/apps/dn299030) als Kontextmenü wird die [FlyoutBase.ShowAttachedFlyout](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.showattachedflyout)-Eigenschaft verwendet, um die Klasse als Menü anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="fba55-151">The next example is nearly identical, but instead of using the [ContextFlyout](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx) property to show the [MenuFlyout class](https://msdn.microsoft.com/library/windows/apps/dn299030) as a context menu, the example uses the [FlyoutBase.ShowAttachedFlyout](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.showattachedflyout) property to show it as a menu.</span></span>

````xaml
<Rectangle
  Height="100" Width="100"
  Tapped="Rectangle_Tapped">
  <FlyoutBase.AttachedFlyout>
    <MenuFlyout>
      <MenuFlyoutItem Text="Change color" Click="ChangeColorItem_Click" />
    </MenuFlyout>
  </FlyoutBase.AttachedFlyout>
  <Rectangle.Fill>
    <SolidColorBrush x:Name="rectangleFill" Color="Red" />
  </Rectangle.Fill>
</Rectangle>
````

````csharp
private void Rectangle_Tapped(object sender, TappedRoutedEventArgs e)
{
    FlyoutBase.ShowAttachedFlyout((FrameworkElement)sender);
}

private void ChangeColorItem_Click(object sender, RoutedEventArgs e)
{
    // Change the color from red to blue or blue to red.
    if (rectangleFill.Color == Windows.UI.Colors.Red)
    {
        rectangleFill.Color = Windows.UI.Colors.Blue;
    }
    else
    {
        rectangleFill.Color = Windows.UI.Colors.Red;
    }
}
````


> <span data-ttu-id="fba55-152">Einfach ausgeblendete Steuerelemente wie Menüs, Kontextmenüs und andere Flyouts erhalten in der vorübergehenden Benutzeroberfläche den Tastatur- bzw. Gamepad-Fokus, bis sie nicht mehr angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="fba55-152">Light dismiss controls, such as menus, context menus, and other flyouts, trap keyboard and gamepad focus inside the transient UI until dismissed.</span></span> <span data-ttu-id="fba55-153">Um dieses Verhalten optisch zu kennzeichnen, werden diese Steuerelemente auf der Xbox als Überlagerung gezeichnet, wobei Helligkeit bzw. die Sichtbarkeit umgebenden Benutzeroberfläche reduziert wird.</span><span class="sxs-lookup"><span data-stu-id="fba55-153">To provide a visual cue for this behavior, light dismiss controls on Xbox will draw an overlay that dims the visibility of out of scope UI.</span></span> <span data-ttu-id="fba55-154">Dieses Verhalten lässt sich mit der Eigenschaft  [LightDismissOverlayMode](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.lightdismissoverlaymode.aspx) anpassen.</span><span class="sxs-lookup"><span data-stu-id="fba55-154">This behavior can be modified with the  [LightDismissOverlayMode](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.lightdismissoverlaymode.aspx) property.</span></span> <span data-ttu-id="fba55-155">Standardmäßig nutzen transiente Benutzeroberflächen die einfach auszublendende Überlagerung für die Xbox (**Auto**), jedoch nicht für andere Gerätereihen. Apps können jedoch durchsetzen, dass die Überlagerung ständig **Ein** oder **Aus** ist.</span><span class="sxs-lookup"><span data-stu-id="fba55-155">By default, transient UIs will draw the light dismiss overlay on Xbox (**Auto**) but not other device families, but apps can choose to force the overlay to be always **On** or always **Off**.</span></span>

> ```xaml
> <MenuFlyout LightDismissOverlayMode="Off" />
> ```

## <a name="get-the-sample-code"></a><span data-ttu-id="fba55-156">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="fba55-156">Get the sample code</span></span>
*   [<span data-ttu-id="fba55-157">Beispiel für XAML-UI-Grundlagen</span><span class="sxs-lookup"><span data-stu-id="fba55-157">XAML UI basics sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/XamlUIBasics)<br/>
    <span data-ttu-id="fba55-158">Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="fba55-158">See all of the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="fba55-159">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="fba55-159">Related articles</span></span>

- [<span data-ttu-id="fba55-160">MenuFlyout-Klasse</span><span class="sxs-lookup"><span data-stu-id="fba55-160">MenuFlyout class</span></span>](https://msdn.microsoft.com/library/windows/apps/dn299030)
