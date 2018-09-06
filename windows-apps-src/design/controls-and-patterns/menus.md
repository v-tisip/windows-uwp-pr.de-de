---
author: mijacobs
Description: A flyout is a lightweight popup that is used to temporarily show UI that is related to what the user is currently doing.
title: Menüs und Kontextmenüs
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
ms.localizationpriority: medium
ms.openlocfilehash: e38e9d61e8546d412cc30bad26680243f3a188e4
ms.sourcegitcommit: 53ba430930ecec8ea10c95b390fe6e654fe363e1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "3416611"
---
# <a name="menus-and-context-menus"></a><span data-ttu-id="67993-103">Menüs und Kontextmenüs</span><span class="sxs-lookup"><span data-stu-id="67993-103">Menus and context menus</span></span>



<span data-ttu-id="67993-104">Menüs und Kontextmenüs zeigen auf Anforderung des Benutzers eine Liste von Befehlen oder Optionen an.</span><span class="sxs-lookup"><span data-stu-id="67993-104">Menus and context menus display a list of commands or options when the user requests them.</span></span>

> <span data-ttu-id="67993-105">**Wichtige APIs**: [MenuFlyout-Klasse](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.MenuFlyout), [ContextFlyout-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx), [FlyoutBase.AttachedFlyout-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout.aspx)</span><span class="sxs-lookup"><span data-stu-id="67993-105">**Important APIs**: [MenuFlyout class](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.MenuFlyout), [ContextFlyout property](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx), [FlyoutBase.AttachedFlyout property](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout.aspx)</span></span>

![Beispiel für ein typisches Kontextmenü](images/contextmenu_rs2_icons.png)


## <a name="is-this-the-right-control"></a><span data-ttu-id="67993-107">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="67993-107">Is this the right control?</span></span>
<span data-ttu-id="67993-108">Menüs und Kontextmenüs sparen Platz, indem Befehle angeordnet und ausgeblendet werden, bis der Benutzer sie benötigt.</span><span class="sxs-lookup"><span data-stu-id="67993-108">Menus and context menus save space by organizing commands and hiding them until the user needs them.</span></span> <span data-ttu-id="67993-109">Wenn ein bestimmter Befehl häufig verwendet wird und Sie genügend Platz haben, sollten Sie ihn direkt als eigenes Element und nicht in einem Menü platzieren, damit Benutzer das Menü nicht durchlaufen müssen, um ihn aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="67993-109">If a particular command will be used frequently and you have the space available, consider placing it directly in its own element, rather than in a menu, so that users don't have to go through a menu to get to it.</span></span>

<span data-ttu-id="67993-110">Menüs und Kontextmenüs dienen dazu, Befehle strukturiert anzuordnen. Um beliebige Inhalte anzuzeigen, z. B. eine Benachrichtigung oder die Bestätigung einer Anfrage, verwenden Sie ein [Dialogfeld oder Flyout](dialogs.md).</span><span class="sxs-lookup"><span data-stu-id="67993-110">Menus and context menus are for organizing commands; to display arbitrary content, such as an notification or to request confirmation, use a [dialog or a flyout](dialogs.md).</span></span>  

## <a name="examples"></a><span data-ttu-id="67993-111">Beispiele</span><span class="sxs-lookup"><span data-stu-id="67993-111">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="67993-112">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="67993-112">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="67993-113">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/MenuFlyout">die App zu öffnen und MenuFlyout in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="67993-113">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/MenuFlyout">open the app and see the MenuFlyout in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="67993-114">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="67993-114">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="67993-115">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="67993-115">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="menus-vs-context-menus"></a><span data-ttu-id="67993-116">Vergleich zwischen Menüs und Kontextmenüs</span><span class="sxs-lookup"><span data-stu-id="67993-116">Menus vs. context menus</span></span>

<span data-ttu-id="67993-117">Menüs und Kontextmenüs sind identisch, was ihr Erscheinungsbild und ihren Inhalt angeht.</span><span class="sxs-lookup"><span data-stu-id="67993-117">Menus and context menus are identical in how they look and what they can contain.</span></span> <span data-ttu-id="67993-118">Tatsächlich werden beide mit demselben Steuerelement erstellt, [MenuFlyout](https://msdn.microsoft.com/library/windows/apps/dn299030).</span><span class="sxs-lookup"><span data-stu-id="67993-118">In fact, you use the same control, [MenuFlyout](https://msdn.microsoft.com/library/windows/apps/dn299030), to create them.</span></span> <span data-ttu-id="67993-119">Der einzige Unterschied ist, wie Sie den Benutzer darauf zugreifen lassen.</span><span class="sxs-lookup"><span data-stu-id="67993-119">The only difference is how you let the user access it.</span></span>

<span data-ttu-id="67993-120">Wann sollten Sie ein Menü und wann ein Kontextmenü verwenden?</span><span class="sxs-lookup"><span data-stu-id="67993-120">When should you use a menu or a context menu?</span></span>
* <span data-ttu-id="67993-121">Ist das übergeordnete Element eine Schaltfläche oder ein anderes Befehlselement, dessen primäre Funktion es ist, weitere Befehle zu präsentieren, verwenden Sie ein Menü.</span><span class="sxs-lookup"><span data-stu-id="67993-121">If the host element is a button or some other command element who's primary role is to present additional commands, use a menu.</span></span>
* <span data-ttu-id="67993-122">Wenn das übergeordnete Element eine andere Art von Element ist, das hauptsächlich einem anderen Zweck dient (z. B. der Anzeige von Text oder einem Bild), verwenden Sie ein Kontextmenü.</span><span class="sxs-lookup"><span data-stu-id="67993-122">If the host element is some other type of element that has another primary purpose (such as presenting text or an image), use a context menu.</span></span>

<span data-ttu-id="67993-123">Verwenden Sie beispielsweise ein Menü auf einer Schaltfläche in einem Navigationsbereich, um zusätzliche Navigationsoptionen bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="67993-123">For example, use a menu on a button in a navigation pane to provide additional navigation options.</span></span> <span data-ttu-id="67993-124">Der Hauptzweck des Schaltflächen-Steuerelements ist in diesem Szenario, auf ein Menü zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="67993-124">In this scenario, the primary purpose of the button control is to provide access to a menu.</span></span>

![Beispiel des Menüs in Mail](images/Mail_Menu.png)

<span data-ttu-id="67993-126">Wenn Sie Befehle (z. B. Ausschneiden, Kopieren und Einfügen) hinzufügen möchten, verwenden Sie ein Kontextmenü anstelle eines Menüs.</span><span class="sxs-lookup"><span data-stu-id="67993-126">If you want to add commands (such as cut, copy, and paste) to a text element, use a context menu instead of a menu.</span></span> <span data-ttu-id="67993-127">In diesem Szenario ist die Hauptfunktion des Textelements Text zur Ansicht und zum Bearbeiten anzuzeigen. Weitere Befehle (z. B. Ausschneiden, Kopieren und Einfügen) sind sekundär und gehören in ein Kontextmenü.</span><span class="sxs-lookup"><span data-stu-id="67993-127">In this scenario, the primary role of the text element is to present and edit text; additional commands (such as cut, copy, and paste) are secondary and belong in a context menu.</span></span>

![Beispiel des Kurzbefehlmenüs in der Fotogalerie](images/ContextMenu_example.png) 

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
   <p><b><span data-ttu-id="67993-129">Menüs</span><span class="sxs-lookup"><span data-stu-id="67993-129">Menus</span></span></b></p>
<ul>
<li><span data-ttu-id="67993-130">Haben Sie einen einzigen Einstiegspunkt (am oberen Bildschirmrand, z. B. über ein Menü „Datei“), der immer angezeigt wird</span><span class="sxs-lookup"><span data-stu-id="67993-130">Have a single entry point (a File menu at the top of the screen, for example) that is always displayed.</span></span></li>
<li><span data-ttu-id="67993-131">Werden in der Regel an eine Schaltfläche oder ein übergeordnetes Menüelement angehängt</span><span class="sxs-lookup"><span data-stu-id="67993-131">Are usually attached to a button or a parent menu item.</span></span></li>
<li><span data-ttu-id="67993-132">Werden mit der linken Maustaste (oder einer entsprechenden Aktion, z. B. durch Tippen) aufgerufen</span><span class="sxs-lookup"><span data-stu-id="67993-132">Are invoked by left-clicking (or an equivalent action, such as tapping with your finger).</span></span></li><li><span data-ttu-id="67993-133">Werden Elementen über ihre <a href="https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.button.flyout.aspx">Flyout</a>- oder <a href="https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout.aspx">FlyoutBase.AttachedFlyout</a>-Eigenschaft zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="67993-133">Are associated with an element via its <a href="https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.button.flyout.aspx">Flyout</a> or <a href="https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout.aspx">FlyoutBase.AttachedFlyout</a> properties.</span></span></li>
</ul>
</div>
  <div class="side-by-side-content-right">
   <p><b><span data-ttu-id="67993-134">Kontextmenüs</span><span class="sxs-lookup"><span data-stu-id="67993-134">Context menus</span></span></b></p>

<ul>
<li><span data-ttu-id="67993-135">Sind mit einem einzelnen Element verknüpft und zeigen Sekundärbefehle an.</span><span class="sxs-lookup"><span data-stu-id="67993-135">Are attached to a single element and display secondary commands.</span></span></li>
<li><span data-ttu-id="67993-136">Werden mit der rechten Maustaste (oder einer entsprechenden Aktion, z. B. durch Tippen und Halten) aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="67993-136">Are invoked by right clicking (or an equivalent action, such as pressing and holding with your finger).</span></span></li><li><span data-ttu-id="67993-137">Sind mit einem Element über dessen <a href="https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx">ContextFlyout</a>-Eigenschaft verknüpft.</span><span class="sxs-lookup"><span data-stu-id="67993-137">Are associated with an element via its <a href="https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx">ContextFlyout</a> property.</span></span></li>
</ul>
  </div>
</div>
</div>

## <a name="icons"></a><span data-ttu-id="67993-138">Symbole</span><span class="sxs-lookup"><span data-stu-id="67993-138">Icons</span></span>

<span data-ttu-id="67993-139">Erwägen Sie in folgenden Fällen Symbole für die Menüpunkte einzurichten:</span><span class="sxs-lookup"><span data-stu-id="67993-139">Consider providing menu item icons for:</span></span>

<ul>
<li> <span data-ttu-id="67993-140">Für am häufigsten verwendete Elemente</span><span class="sxs-lookup"><span data-stu-id="67993-140">The most commonly used items</span></span> </li>
<li> <span data-ttu-id="67993-141">Für Menüpunkte, für die allgemein bekannte oder Standardsymbole vorhanden sind</span><span class="sxs-lookup"><span data-stu-id="67993-141">Menu items whose icon is standard or well known</span></span> </li>
<li> <span data-ttu-id="67993-142">Für Menüpunkte, deren Funktion auf einfache Weise mit einem Symbol veranschaulicht werden kann</span><span class="sxs-lookup"><span data-stu-id="67993-142">Menu items whose icon well illustrates what the command does</span></span> </li>
</ul>

<span data-ttu-id="67993-143">Fühlen Sie sich nicht dazu verpflichtet, Befehle mit einem Symbol zu versehen, für die keine Standardsymbole vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="67993-143">Don't feel obligated to provide icons for commands that don't have a standard visualization.</span></span> <span data-ttu-id="67993-144">Kryptische Symbole sind nicht hilfreich, machen das Menü unübersichtlich und hindern Benutzer daran, wichtige Menüpunkte einfach aufzufinden.</span><span class="sxs-lookup"><span data-stu-id="67993-144">Cryptic icons aren’t helpful, create visual clutter, and prevent users from focusing on the important menu items.</span></span>

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
> <span data-ttu-id="67993-146">Die Größe der Symbole für MenuFlyoutItems ist 16x16px.</span><span class="sxs-lookup"><span data-stu-id="67993-146">The size of the icons in MenuFlyoutItems is 16x16px.</span></span> <span data-ttu-id="67993-147">Wenn Sie SymbolIcon, FontIcon oder PathIcon verwenden, wird das Symbol automatisch verlustfrei auf die richtige Größe skaliert.</span><span class="sxs-lookup"><span data-stu-id="67993-147">If you use SymbolIcon, FontIcon, or PathIcon, the icon will automatically scale to the correct size with no loss of fidelity.</span></span> <span data-ttu-id="67993-148">Achten Sie bei der Verwendung von BitmapIcon darauf, dass Ihr Element 16x16px groß sein muss.</span><span class="sxs-lookup"><span data-stu-id="67993-148">If you use BitmapIcon, ensure that your asset is 16x16px.</span></span>  

## <a name="create-a-menu-or-a-context-menu"></a><span data-ttu-id="67993-149">Erstellen eines Menüs bzw. Kontextmenüs</span><span class="sxs-lookup"><span data-stu-id="67993-149">Create a menu or a context menu</span></span>

<span data-ttu-id="67993-150">Um ein Menü oder ein Kontextmenü zu erstellen, verwenden Sie die [MenuFlyout-Klasse](https://msdn.microsoft.com/library/windows/apps/dn299030).</span><span class="sxs-lookup"><span data-stu-id="67993-150">To create a menu or a context menu, you use the [MenuFlyout class](https://msdn.microsoft.com/library/windows/apps/dn299030).</span></span> <span data-ttu-id="67993-151">Sie definieren den Inhalt des Menüs, indem Sie dem MenuFlyout die Objekte [MenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutitem.aspx), [ToggleMenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.togglemenuflyoutitem.aspx) und [MenuFlyoutSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutseparator.aspx) hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="67993-151">You define the contents of the menu by adding [MenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutitem.aspx), [ToggleMenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.togglemenuflyoutitem.aspx), and [MenuFlyoutSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutseparator.aspx) objects to the MenuFlyout.</span></span> <span data-ttu-id="67993-152">Diese Objekte erfüllen folgende Zwecke:</span><span class="sxs-lookup"><span data-stu-id="67993-152">These objects are for:</span></span>
* <span data-ttu-id="67993-153">[MenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutitem.aspx): Ausführen einer sofortigen Aktion</span><span class="sxs-lookup"><span data-stu-id="67993-153">[MenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutitem.aspx)—Performing an immediate action.</span></span>
* <span data-ttu-id="67993-154">[ToggleMenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.togglemenuflyoutitem.aspx): Ein- und Ausschalten einer Option</span><span class="sxs-lookup"><span data-stu-id="67993-154">[ToggleMenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.togglemenuflyoutitem.aspx)—Switching an option on or off.</span></span>
* <span data-ttu-id="67993-155">[MenuFlyoutSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutseparator.aspx)—Optisches Trennen von Menüelementen</span><span class="sxs-lookup"><span data-stu-id="67993-155">[MenuFlyoutSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutseparator.aspx)—Visually separating menu items.</span></span>


<span data-ttu-id="67993-156">In diesem Beispiel wird ein [MenuFlyout-Klasse](https://msdn.microsoft.com/library/windows/apps/dn299030) erstellt, und anschließend wird mit der [ContextFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx)-Eigenschaft, die für die meisten Steuerelemente verfügbar ist, die [MenuFlyout-Klasse](https://msdn.microsoft.com/library/windows/apps/dn299030) als Kontextmenü angezeigt.</span><span class="sxs-lookup"><span data-stu-id="67993-156">This example creates a [MenuFlyout class](https://msdn.microsoft.com/library/windows/apps/dn299030) and uses the [ContextFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx) property, a property available to most controls, to show the [MenuFlyout class](https://msdn.microsoft.com/library/windows/apps/dn299030) as a context menu.</span></span>

````xaml
<Rectangle
  Height="100" Width="100">
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

<span data-ttu-id="67993-157">Das nächste Beispiel ist nahezu identisch, aber anstelle der [ContextFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx)-Eigenschaft zur Anzeige der [MenuFlyout-Klasse](https://msdn.microsoft.com/library/windows/apps/dn299030) als Kontextmenü wird die [FlyoutBase.ShowAttachedFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.showattachedflyout)-Eigenschaft verwendet, um die Klasse als Menü anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="67993-157">The next example is nearly identical, but instead of using the [ContextFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx) property to show the [MenuFlyout class](https://msdn.microsoft.com/library/windows/apps/dn299030) as a context menu, the example uses the [FlyoutBase.ShowAttachedFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.showattachedflyout) property to show it as a menu.</span></span>

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


> <span data-ttu-id="67993-158">Einfach ausgeblendete Steuerelemente wie Menüs, Kontextmenüs und andere Flyouts erhalten in der vorübergehenden Benutzeroberfläche den Tastatur- bzw. Gamepad-Fokus, bis sie nicht mehr angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="67993-158">Light dismiss controls, such as menus, context menus, and other flyouts, trap keyboard and gamepad focus inside the transient UI until dismissed.</span></span> <span data-ttu-id="67993-159">Um dieses Verhalten optisch zu kennzeichnen, werden diese Steuerelemente auf der Xbox als Überlagerung gezeichnet, wobei Helligkeit bzw. die Sichtbarkeit umgebenden Benutzeroberfläche reduziert wird.</span><span class="sxs-lookup"><span data-stu-id="67993-159">To provide a visual cue for this behavior, light dismiss controls on Xbox will draw an overlay that dims the visibility of out of scope UI.</span></span> <span data-ttu-id="67993-160">Dieses Verhalten lässt sich mit der Eigenschaft  [LightDismissOverlayMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.lightdismissoverlaymode.aspx) anpassen.</span><span class="sxs-lookup"><span data-stu-id="67993-160">This behavior can be modified with the  [LightDismissOverlayMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.lightdismissoverlaymode.aspx) property.</span></span> <span data-ttu-id="67993-161">Standardmäßig nutzen transiente Benutzeroberflächen die einfach auszublendende Überlagerung für die Xbox (**Auto**), jedoch nicht für andere Gerätereihen. Apps können jedoch durchsetzen, dass die Überlagerung ständig **Ein** oder **Aus** ist.</span><span class="sxs-lookup"><span data-stu-id="67993-161">By default, transient UIs will draw the light dismiss overlay on Xbox (**Auto**) but not other device families, but apps can choose to force the overlay to be always **On** or always **Off**.</span></span>

> ```xaml
> <MenuFlyout LightDismissOverlayMode="Off" />
> ```

## <a name="get-the-sample-code"></a><span data-ttu-id="67993-162">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="67993-162">Get the sample code</span></span>

- <span data-ttu-id="67993-163">[Beispiel eines XAML-Steuerelementekatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="67993-163">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>
- [<span data-ttu-id="67993-164">Beispiel für XAML-Kontextmenü</span><span class="sxs-lookup"><span data-stu-id="67993-164">XAML Context menu sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlContextMenu)

## <a name="related-articles"></a><span data-ttu-id="67993-165">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="67993-165">Related articles</span></span>

- [<span data-ttu-id="67993-166">MenuFlyout-Klasse</span><span class="sxs-lookup"><span data-stu-id="67993-166">MenuFlyout class</span></span>](https://msdn.microsoft.com/library/windows/apps/dn299030)
