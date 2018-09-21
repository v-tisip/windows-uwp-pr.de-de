---
author: mijacobs
Description: Menus and context menus display a list of commands or options when the user requests them.
title: Menüs und Kontextmenüs
label: Menus and context menus
template: detail.hbs
ms.author: mijacobs
ms.date: 07/19/2018
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
ms.openlocfilehash: 703667bf22ce11c119463008e868a943d447c7ff
ms.sourcegitcommit: 5dda01da4702cbc49c799c750efe0e430b699502
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/21/2018
ms.locfileid: "4113638"
---
# <a name="menus-and-context-menus"></a><span data-ttu-id="981f6-103">Menüs und Kontextmenüs</span><span class="sxs-lookup"><span data-stu-id="981f6-103">Menus and context menus</span></span>

> [!IMPORTANT]
> <span data-ttu-id="981f6-104">In diesem Artikel werden Funktionen beschrieben, die noch nicht veröffentlicht wurden und vor der kommerziellen Freigabe evtl. geändert werden.</span><span class="sxs-lookup"><span data-stu-id="981f6-104">This article describes functionality that hasn’t been released yet and may be substantially modified before it's commercially released.</span></span> <span data-ttu-id="981f6-105">Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.</span><span class="sxs-lookup"><span data-stu-id="981f6-105">Microsoft makes no warranties, express or implied, with respect to the information provided here.</span></span> <span data-ttu-id="981f6-106">Preview-Funktionen müssen die [neuesten Windows 10 Insider Preview-Build und SDK](https://insider.windows.com/for-developers/) oder der [Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).</span><span class="sxs-lookup"><span data-stu-id="981f6-106">Preview features require the [latest Windows 10 Insider Preview build and SDK](https://insider.windows.com/for-developers/) or the [Windows UI Library](https://docs.microsoft.com/uwp/toolkits/winui/).</span></span>

<span data-ttu-id="981f6-107">Menüs und Kontextmenüs zeigen auf Anforderung des Benutzers eine Liste von Befehlen oder Optionen an.</span><span class="sxs-lookup"><span data-stu-id="981f6-107">Menus and context menus display a list of commands or options when the user requests them.</span></span> <span data-ttu-id="981f6-108">Verwenden Sie ein Flyout "Menü", um ein einziges, Inline-Menü anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="981f6-108">Use a menu flyout to show a single, inline menu.</span></span> <span data-ttu-id="981f6-109">Verwenden Sie eine Menüleiste, um eine Reihe von Menüs in einer horizontalen Zeile in der Regel am oberen Rand eines app-Fensters anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="981f6-109">Use a menu bar to show a set of menus in a horizontal row, typically at the top of an app window.</span></span> <span data-ttu-id="981f6-110">Jedes Menü kann es sich um Menüelemente und Untermenüs aufweisen.</span><span class="sxs-lookup"><span data-stu-id="981f6-110">Each menu can have menu items and sub-menus.</span></span>

![Beispiel für ein typisches Kontextmenü](images/contextmenu_rs2_icons.png)

| **<span data-ttu-id="981f6-112">Abrufen der Windows-UI-Bibliothek</span><span class="sxs-lookup"><span data-stu-id="981f6-112">Get the Windows UI Library</span></span>** |
| - |
| <span data-ttu-id="981f6-113">Dieses Steuerelement ist Bestandteil der Windows-UI-Bibliothek, NuGet-Paket, das neue Steuerelemente und UI-Features für UWP-apps enthält.</span><span class="sxs-lookup"><span data-stu-id="981f6-113">This control is included as part of the Windows UI Library, a NuGet package that contains new controls and UI features for UWP apps.</span></span> <span data-ttu-id="981f6-114">Weitere Informationen, einschließlich installationsanweisungen finden Sie die [Übersicht über die Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).</span><span class="sxs-lookup"><span data-stu-id="981f6-114">For more info, including installation instructions, see the [Windows UI Library overview](https://docs.microsoft.com/uwp/toolkits/winui/).</span></span> |

| **<span data-ttu-id="981f6-115">Plattform-APIs</span><span class="sxs-lookup"><span data-stu-id="981f6-115">Platform APIs</span></span>** | **<span data-ttu-id="981f6-116">Windows-UI-Bibliothek APIs</span><span class="sxs-lookup"><span data-stu-id="981f6-116">Windows UI Library APIs</span></span>** |
| - | - |
| <span data-ttu-id="981f6-117">[MenuFlyout-Klasse](/uwp/api/windows.ui.xaml.controls.menuflyout), [Menüleiste-Klasse](/uwp/api/windows.ui.xaml.controls.menubar), [ContextFlyout-Eigenschaft](/uwp/api/windows.ui.xaml.uielement.contextflyout), [FlyoutBase.AttachedFlyout-Eigenschaft](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout)</span><span class="sxs-lookup"><span data-stu-id="981f6-117">[MenuFlyout class](/uwp/api/windows.ui.xaml.controls.menuflyout), [MenuBar class](/uwp/api/windows.ui.xaml.controls.menubar), [ContextFlyout property](/uwp/api/windows.ui.xaml.uielement.contextflyout), [FlyoutBase.AttachedFlyout property](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout)</span></span> | [<span data-ttu-id="981f6-118">Menüleiste-Klasse</span><span class="sxs-lookup"><span data-stu-id="981f6-118">MenuBar class</span></span>](/uwp/api/microsoft.ui.xaml.controls.menubar) |

## <a name="is-this-the-right-control"></a><span data-ttu-id="981f6-119">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="981f6-119">Is this the right control?</span></span>

<span data-ttu-id="981f6-120">Menüs und Kontextmenüs sparen Platz, indem Befehle angeordnet und ausgeblendet werden, bis der Benutzer sie benötigt.</span><span class="sxs-lookup"><span data-stu-id="981f6-120">Menus and context menus save space by organizing commands and hiding them until the user needs them.</span></span> <span data-ttu-id="981f6-121">Wenn ein bestimmter Befehl häufig verwendet wird und Sie genügend Platz haben, sollten Sie ihn direkt als eigenes Element und nicht in einem Menü platzieren, damit Benutzer das Menü nicht durchlaufen müssen, um ihn aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="981f6-121">If a particular command will be used frequently and you have the space available, consider placing it directly in its own element, rather than in a menu, so that users don't have to go through a menu to get to it.</span></span>

<span data-ttu-id="981f6-122">Menüs und Kontextmenüs sind für das Organisieren von Befehlen. Verwenden Sie ein [Dialogfeld oder Flyout](dialogs.md), um beliebige Inhalte, z. B. eine Benachrichtigung oder eine Bestätigung Anforderung anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="981f6-122">Menus and context menus are for organizing commands; to display arbitrary content, such as a notification or confirmation request, use a [dialog or a flyout](dialogs.md).</span></span>

### <a name="menubar-vs-menuflyout"></a><span data-ttu-id="981f6-123">Menüleiste im Vergleich zu MenuFlyout</span><span class="sxs-lookup"><span data-stu-id="981f6-123">MenuBar vs. MenuFlyout</span></span>

<span data-ttu-id="981f6-124">Um ein Menü in einem Flyout auf ein UI-Element auf der Canvas angefügt anzuzeigen, verwenden Sie das MenuFlyout-Steuerelement, um Ihre Menüelemente zu hosten.</span><span class="sxs-lookup"><span data-stu-id="981f6-124">To show a menu in a flyout attached to an on-canvas UI element, use the MenuFlyout control to host your menu items.</span></span> <span data-ttu-id="981f6-125">Sie können ein Menü-Flyout als reguläre Menü oder als Kontextmenü aufrufen.</span><span class="sxs-lookup"><span data-stu-id="981f6-125">You can invoke a menu flyout either as a regular menu or as a context menu.</span></span> <span data-ttu-id="981f6-126">Ein Menü-Flyout hostet ein einziges auf oberster Ebene Menü (und optional Untermenüs).</span><span class="sxs-lookup"><span data-stu-id="981f6-126">A menu flyout hosts a single top-level menu (and optional sub-menus).</span></span>

<span data-ttu-id="981f6-127">Um eine Reihe von mehreren Menüs der obersten Ebene in eine horizontale Reihe anzuzeigen, verwenden Sie eine Menüleiste.</span><span class="sxs-lookup"><span data-stu-id="981f6-127">To show a set of multiple top-level menus in a horizontal row, use a menu bar.</span></span> <span data-ttu-id="981f6-128">Sie positionieren in der Regel die Menüleiste am oberen Rand des app-Fensters.</span><span class="sxs-lookup"><span data-stu-id="981f6-128">You typically position the menu bar at the top of the app window.</span></span>

### <a name="menubar-vs-commandbar"></a><span data-ttu-id="981f6-129">Menüleiste im Vergleich zu CommandBar</span><span class="sxs-lookup"><span data-stu-id="981f6-129">MenuBar vs. CommandBar</span></span>

<span data-ttu-id="981f6-130">Menüleiste und CommandBar darstellen beide Oberflächen, die Sie verwenden können, um Befehle für Ihre Benutzer verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="981f6-130">MenuBar and CommandBar both represent surfaces that you can use to expose commands to your users.</span></span> <span data-ttu-id="981f6-131">Der Menüleiste bietet eine schnelle und einfache Möglichkeit, eine Reihe von Befehlen für apps verfügbar zu machen, die möglicherweise weitere Organisation oder Gruppierung, und klicken Sie dann eine CommandBar ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="981f6-131">The MenuBar provides a quick and simple way to expose a set of commands for apps that might need more organization or grouping then a CommandBar allows.</span></span>

<span data-ttu-id="981f6-132">Sie können auch eine Menüleiste in Verbindung mit einer CommandBar.</span><span class="sxs-lookup"><span data-stu-id="981f6-132">You can also use a MenuBar in conjunction with a CommandBar.</span></span> <span data-ttu-id="981f6-133">Verwenden Sie die Menüleiste, um den Großteil der Befehle und CommandBar markieren die am häufigsten verwendeten Befehle bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="981f6-133">Use the MenuBar to provide the bulk of the commands, and the CommandBar to highlight the most used commands.</span></span>

## <a name="examples"></a><span data-ttu-id="981f6-134">Beispiele</span><span class="sxs-lookup"><span data-stu-id="981f6-134">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="981f6-135">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="981f6-135">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="981f6-136">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/MenuFlyout">die App zu öffnen und MenuFlyout in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="981f6-136">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/MenuFlyout">open the app and see the MenuFlyout in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="981f6-137">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="981f6-137">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="981f6-138">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="981f6-138">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="menus-vs-context-menus"></a><span data-ttu-id="981f6-139">Vergleich zwischen Menüs und Kontextmenüs</span><span class="sxs-lookup"><span data-stu-id="981f6-139">Menus vs. context menus</span></span>

<span data-ttu-id="981f6-140">Menüs und Kontextmenüs sind ähnlich Erscheinungsbild und was sie enthalten können.</span><span class="sxs-lookup"><span data-stu-id="981f6-140">Menus and context menus are similar in how they look and what they can contain.</span></span> <span data-ttu-id="981f6-141">In der Tat können Sie das gleiche Steuerelement, [MenuFlyout](https://msdn.microsoft.com/library/windows/apps/dn299030), zu deren Erstellung verwenden.</span><span class="sxs-lookup"><span data-stu-id="981f6-141">In fact, you can use the same control, [MenuFlyout](https://msdn.microsoft.com/library/windows/apps/dn299030), to create them.</span></span> <span data-ttu-id="981f6-142">Der Unterschied ist, wie Sie den Benutzer darauf zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="981f6-142">The difference is how you let the user access it.</span></span>

<span data-ttu-id="981f6-143">Wann sollten Sie ein Menü und wann ein Kontextmenü verwenden?</span><span class="sxs-lookup"><span data-stu-id="981f6-143">When should you use a menu or a context menu?</span></span>

- <span data-ttu-id="981f6-144">Ist das übergeordnete Element eine Schaltfläche oder ein anderes Befehlselement, dessen primäre Funktion es ist, weitere Befehle zu präsentieren, verwenden Sie ein Menü.</span><span class="sxs-lookup"><span data-stu-id="981f6-144">If the host element is a button or some other command element who's primary role is to present additional commands, use a menu.</span></span>
- <span data-ttu-id="981f6-145">Wenn das übergeordnete Element eine andere Art von Element ist, das hauptsächlich einem anderen Zweck dient (z. B. der Anzeige von Text oder einem Bild), verwenden Sie ein Kontextmenü.</span><span class="sxs-lookup"><span data-stu-id="981f6-145">If the host element is some other type of element that has another primary purpose (such as presenting text or an image), use a context menu.</span></span>

<span data-ttu-id="981f6-146">Verwenden Sie beispielsweise ein Menü auf einer Schaltfläche, um bereitzustellen, Filtern und sortieren die Optionen für eine Liste.</span><span class="sxs-lookup"><span data-stu-id="981f6-146">For example, use a menu on a button to provide filtering and sorting options for a list.</span></span> <span data-ttu-id="981f6-147">Der Hauptzweck des Schaltflächen-Steuerelements ist in diesem Szenario, auf ein Menü zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="981f6-147">In this scenario, the primary purpose of the button control is to provide access to a menu.</span></span>

![Beispiel des Menüs in Mail](images/Mail_Menu.png)

<span data-ttu-id="981f6-149">Wenn Sie Befehle (z. B. Ausschneiden, Kopieren und Einfügen) hinzufügen möchten, verwenden Sie ein Kontextmenü anstelle eines Menüs.</span><span class="sxs-lookup"><span data-stu-id="981f6-149">If you want to add commands (such as cut, copy, and paste) to a text element, use a context menu instead of a menu.</span></span> <span data-ttu-id="981f6-150">In diesem Szenario ist die Hauptfunktion des Textelements Text zur Ansicht und zum Bearbeiten anzuzeigen. Weitere Befehle (z. B. Ausschneiden, Kopieren und Einfügen) sind sekundär und gehören in ein Kontextmenü.</span><span class="sxs-lookup"><span data-stu-id="981f6-150">In this scenario, the primary role of the text element is to present and edit text; additional commands (such as cut, copy, and paste) are secondary and belong in a context menu.</span></span>

![Beispiel des Kurzbefehlmenüs in der Fotogalerie](images/ContextMenu_example.png)

### <a name="menus"></a><span data-ttu-id="981f6-152">Menüs</span><span class="sxs-lookup"><span data-stu-id="981f6-152">Menus</span></span>

- <span data-ttu-id="981f6-153">Haben Sie einen einzigen Einstiegspunkt (am oberen Bildschirmrand, z. B. über ein Menü „Datei“), der immer angezeigt wird</span><span class="sxs-lookup"><span data-stu-id="981f6-153">Have a single entry point (a File menu at the top of the screen, for example) that is always displayed.</span></span>
- <span data-ttu-id="981f6-154">Werden in der Regel an eine Schaltfläche oder ein übergeordnetes Menüelement angehängt</span><span class="sxs-lookup"><span data-stu-id="981f6-154">Are usually attached to a button or a parent menu item.</span></span>
- <span data-ttu-id="981f6-155">Werden mit der linken Maustaste (oder einer entsprechenden Aktion, z. B. durch Tippen) aufgerufen</span><span class="sxs-lookup"><span data-stu-id="981f6-155">Are invoked by left-clicking (or an equivalent action, such as tapping with your finger).</span></span>
- <span data-ttu-id="981f6-156">Werden Elementen über ihre [Flyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.button.flyout.aspx) oder [FlyoutBase.AttachedFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout.aspx) -Eigenschaften zugeordnet sind, oder in einer Menüleiste am oberen Rand des app-Fensters gruppiert.</span><span class="sxs-lookup"><span data-stu-id="981f6-156">Are associated with an element via its [Flyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.button.flyout.aspx) or [FlyoutBase.AttachedFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout.aspx) properties, or grouped in a menu bar at the top of the app window.</span></span>

### <a name="context-menus"></a><span data-ttu-id="981f6-157">Kontextmenüs</span><span class="sxs-lookup"><span data-stu-id="981f6-157">Context menus</span></span>

- <span data-ttu-id="981f6-158">Sind mit einem einzelnen Element verknüpft und zeigen Sekundärbefehle an.</span><span class="sxs-lookup"><span data-stu-id="981f6-158">Are attached to a single element and display secondary commands.</span></span>
- <span data-ttu-id="981f6-159">Werden mit der rechten Maustaste (oder einer entsprechenden Aktion, z. B. durch Tippen und Halten) aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="981f6-159">Are invoked by right clicking (or an equivalent action, such as pressing and holding with your finger).</span></span>
- <span data-ttu-id="981f6-160">Sind mit einem Element über dessen [ContextFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx)-Eigenschaft verknüpft.</span><span class="sxs-lookup"><span data-stu-id="981f6-160">Are associated with an element via its [ContextFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx) property.</span></span>

## <a name="icons"></a><span data-ttu-id="981f6-161">Symbole</span><span class="sxs-lookup"><span data-stu-id="981f6-161">Icons</span></span>

<span data-ttu-id="981f6-162">Erwägen Sie in folgenden Fällen Symbole für die Menüpunkte einzurichten:</span><span class="sxs-lookup"><span data-stu-id="981f6-162">Consider providing menu item icons for:</span></span>

- <span data-ttu-id="981f6-163">Die am häufigsten verwendete Elemente.</span><span class="sxs-lookup"><span data-stu-id="981f6-163">The most commonly used items.</span></span>
- <span data-ttu-id="981f6-164">Menüelemente, dessen Symbol bekannte oder Standardsymbole ist.</span><span class="sxs-lookup"><span data-stu-id="981f6-164">Menu items whose icon is standard or well known.</span></span>
- <span data-ttu-id="981f6-165">Menüelemente, dessen Symbol veranschaulicht was werden kann.</span><span class="sxs-lookup"><span data-stu-id="981f6-165">Menu items whose icon well illustrates what the command does.</span></span>

<span data-ttu-id="981f6-166">Fühlen Sie sich nicht dazu verpflichtet, Befehle mit einem Symbol zu versehen, für die keine Standardsymbole vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="981f6-166">Don't feel obligated to provide icons for commands that don't have a standard visualization.</span></span> <span data-ttu-id="981f6-167">Kryptische Symbole sind nicht hilfreich, machen das Menü unübersichtlich und hindern Benutzer daran, wichtige Menüpunkte einfach aufzufinden.</span><span class="sxs-lookup"><span data-stu-id="981f6-167">Cryptic icons aren’t helpful, create visual clutter, and prevent users from focusing on the important menu items.</span></span>

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

> [!TIP]
> <span data-ttu-id="981f6-169">Die Größe des Symbols in einem MenuFlyoutItem ist 16x16px.</span><span class="sxs-lookup"><span data-stu-id="981f6-169">The size of the icon in a MenuFlyoutItem is 16x16px.</span></span> <span data-ttu-id="981f6-170">Wenn Sie SymbolIcon, FontIcon oder PathIcon verwenden, wird das Symbol automatisch auf die richtige Größe mit verlustfrei skaliert.</span><span class="sxs-lookup"><span data-stu-id="981f6-170">If you use SymbolIcon, FontIcon, or PathIcon, the icon automatically scales to the correct size with no loss of fidelity.</span></span> <span data-ttu-id="981f6-171">Achten Sie bei der Verwendung von BitmapIcon darauf, dass Ihr Element 16x16px groß sein muss.</span><span class="sxs-lookup"><span data-stu-id="981f6-171">If you use BitmapIcon, ensure that your asset is 16x16px.</span></span>  

## <a name="create-a-menu-flyout-or-a-context-menu"></a><span data-ttu-id="981f6-172">Erstellen Sie ein Menü-Flyout oder ein Kontextmenü</span><span class="sxs-lookup"><span data-stu-id="981f6-172">Create a menu flyout or a context menu</span></span>

<span data-ttu-id="981f6-173">Um ein Menü-Flyout oder ein Kontextmenü zu erstellen, verwenden Sie die [MenuFlyout-Klasse](https://msdn.microsoft.com/library/windows/apps/dn299030).</span><span class="sxs-lookup"><span data-stu-id="981f6-173">To create a menu flyout or a context menu, you use the [MenuFlyout class](https://msdn.microsoft.com/library/windows/apps/dn299030).</span></span> <span data-ttu-id="981f6-174">Sie definieren den Inhalt des Menüs, indem Sie dem MenuFlyout die Objekte [MenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutitem.aspx), [ToggleMenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.togglemenuflyoutitem.aspx) und [MenuFlyoutSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutseparator.aspx) hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="981f6-174">You define the contents of the menu by adding [MenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutitem.aspx), [ToggleMenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.togglemenuflyoutitem.aspx), and [MenuFlyoutSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutseparator.aspx) objects to the MenuFlyout.</span></span>

<span data-ttu-id="981f6-175">Diese Objekte erfüllen folgende Zwecke:</span><span class="sxs-lookup"><span data-stu-id="981f6-175">These objects are for:</span></span>

- <span data-ttu-id="981f6-176">[MenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutitem.aspx): Ausführen einer sofortigen Aktion</span><span class="sxs-lookup"><span data-stu-id="981f6-176">[MenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutitem.aspx)—Performing an immediate action.</span></span>
- <span data-ttu-id="981f6-177">[ToggleMenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.togglemenuflyoutitem.aspx): Ein- und Ausschalten einer Option</span><span class="sxs-lookup"><span data-stu-id="981f6-177">[ToggleMenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.togglemenuflyoutitem.aspx)—Switching an option on or off.</span></span>
- <span data-ttu-id="981f6-178">[MenuFlyoutSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutseparator.aspx)—Optisches Trennen von Menüelementen</span><span class="sxs-lookup"><span data-stu-id="981f6-178">[MenuFlyoutSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutseparator.aspx)—Visually separating menu items.</span></span>

<span data-ttu-id="981f6-179">Dieses Beispiel erstellt eine [MenuFlyout](https://msdn.microsoft.com/library/windows/apps/dn299030) und verwendet die [ContextFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx) -Eigenschaft, für die meisten Steuerelemente verfügbar MenuFlyout als Kontextmenü angezeigt.</span><span class="sxs-lookup"><span data-stu-id="981f6-179">This example creates a [MenuFlyout](https://msdn.microsoft.com/library/windows/apps/dn299030) and uses the [ContextFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx) property, a property available to most controls, to show the MenuFlyout as a context menu.</span></span>

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

<span data-ttu-id="981f6-180">Das nächste Beispiel ist nahezu identisch, aber anstelle der [ContextFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx)-Eigenschaft zur Anzeige der [MenuFlyout-Klasse](https://msdn.microsoft.com/library/windows/apps/dn299030) als Kontextmenü wird die [FlyoutBase.ShowAttachedFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.showattachedflyout)-Eigenschaft verwendet, um die Klasse als Menü anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="981f6-180">The next example is nearly identical, but instead of using the [ContextFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx) property to show the [MenuFlyout class](https://msdn.microsoft.com/library/windows/apps/dn299030) as a context menu, the example uses the [FlyoutBase.ShowAttachedFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.showattachedflyout) property to show it as a menu.</span></span>

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

### <a name="light-dismiss"></a><span data-ttu-id="981f6-181">Einfaches ausblenden</span><span class="sxs-lookup"><span data-stu-id="981f6-181">Light dismiss</span></span>

<span data-ttu-id="981f6-182">Einfach ausgeblendete Steuerelemente wie Menüs, Kontextmenüs und andere Flyouts erhalten in der vorübergehenden Benutzeroberfläche den Tastatur- bzw. Gamepad-Fokus, bis sie nicht mehr angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="981f6-182">Light dismiss controls, such as menus, context menus, and other flyouts, trap keyboard and gamepad focus inside the transient UI until dismissed.</span></span> <span data-ttu-id="981f6-183">Um dieses Verhalten optisch zu kennzeichnen, werden diese Steuerelemente auf der Xbox als Überlagerung gezeichnet, wobei Helligkeit bzw. die Sichtbarkeit umgebenden Benutzeroberfläche reduziert wird.</span><span class="sxs-lookup"><span data-stu-id="981f6-183">To provide a visual cue for this behavior, light dismiss controls on Xbox will draw an overlay that dims the visibility of out of scope UI.</span></span> <span data-ttu-id="981f6-184">Dieses Verhalten lässt sich mit der Eigenschaft  [LightDismissOverlayMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.lightdismissoverlaymode.aspx) anpassen.</span><span class="sxs-lookup"><span data-stu-id="981f6-184">This behavior can be modified with the  [LightDismissOverlayMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.lightdismissoverlaymode.aspx) property.</span></span> <span data-ttu-id="981f6-185">Standardmäßig nutzen transiente Benutzeroberflächen die einfach auszublendende Überlagerung für die Xbox (**Auto**), jedoch nicht für andere Gerätereihen. Apps können jedoch durchsetzen, dass die Überlagerung ständig **Ein** oder **Aus** ist.</span><span class="sxs-lookup"><span data-stu-id="981f6-185">By default, transient UIs will draw the light dismiss overlay on Xbox (**Auto**) but not other device families, but apps can choose to force the overlay to be always **On** or always **Off**.</span></span>

```xaml
<MenuFlyout LightDismissOverlayMode="Off" />
```

## <a name="create-a-menu-bar"></a><span data-ttu-id="981f6-186">Erstellen Sie eine Menüleiste</span><span class="sxs-lookup"><span data-stu-id="981f6-186">Create a menu bar</span></span>

> <span data-ttu-id="981f6-187">**Vorschau**: Menüleiste erfordert die [neuesten Windows 10 Insider Preview-Build und SDK](https://insider.windows.com/for-developers/) oder der [Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).</span><span class="sxs-lookup"><span data-stu-id="981f6-187">**Preview**: MenuBar requires the [latest Windows 10 Insider Preview build and SDK](https://insider.windows.com/for-developers/) or the [Windows UI Library](https://docs.microsoft.com/uwp/toolkits/winui/).</span></span>

<span data-ttu-id="981f6-188">Sie verwenden die gleichen Elementen Menüs in einer Menüleiste wie in einem Menü-Flyout zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="981f6-188">You use the same elements to create menus in a menu bar as in a menu flyout.</span></span> <span data-ttu-id="981f6-189">Allerdings gruppieren anstelle von Gruppierung von MenuFlyoutItem-Objekten in einer MenuFlyout, Sie können in einem MenuBarItem-Element.</span><span class="sxs-lookup"><span data-stu-id="981f6-189">However, instead of grouping MenuFlyoutItem objects in a MenuFlyout, you group them in a MenuBarItem element.</span></span> <span data-ttu-id="981f6-190">Jeder MenuBarItem wird als ein Menü der obersten Ebene der Menüleiste hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="981f6-190">Each MenuBarItem is added to the MenuBar as a top level menu.</span></span>

![Beispiel für eine Menüleiste](images/menu-bar-submenu.png)

> [!NOTE]
> <span data-ttu-id="981f6-192">In diesem Beispiel wird veranschaulicht, wie nur die UI-Struktur erstellt, aber Implementierung einer der Befehle wird nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="981f6-192">This example shows only how to create the UI structure, but does not show implementation of any of the commands.</span></span>

```xaml
<MenuBar>
    <MenuBarItem Title="File">
        <MenuFlyoutSubItem Text="New">
            <MenuFlyoutItem Text="Plain Text Document"/>
            <MenuFlyoutItem Text="Rich Text Document"/>
            <MenuFlyoutItem Text="Other Formats..."/>
        </MenuFlyoutSubItem>
        <MenuFlyoutItem Text="Open..."/>
        <MenuFlyoutItem Text="Save">
        <MenuFlyoutSeparator />
        <MenuFlyoutItem Text="Exit"/>
    </MenuBarItem>

    <MenuBarItem Title="Edit">
        <MenuFlyoutItem Text="Undo"/>
        <MenuFlyoutItem Text="Cut"/>
        <MenuFlyoutItem Text="Copy"/>
        <MenuFlyoutItem Text="Paste"/>
    </MenuBarItem>

    <MenuBarItem Title="Help">
        <MenuFlyoutItem Text="About"/>
    </MenuBarItem>
</MenuBar>
```

## <a name="get-the-sample-code"></a><span data-ttu-id="981f6-193">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="981f6-193">Get the sample code</span></span>

- <span data-ttu-id="981f6-194">[Beispiel eines XAML-Steuerelementekatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="981f6-194">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>
- [<span data-ttu-id="981f6-195">Beispiel für XAML-Kontextmenü</span><span class="sxs-lookup"><span data-stu-id="981f6-195">XAML Context menu sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlContextMenu)

## <a name="related-articles"></a><span data-ttu-id="981f6-196">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="981f6-196">Related articles</span></span>

- [<span data-ttu-id="981f6-197">MenuFlyout-Klasse</span><span class="sxs-lookup"><span data-stu-id="981f6-197">MenuFlyout class</span></span>](https://msdn.microsoft.com/library/windows/apps/dn299030)
- [<span data-ttu-id="981f6-198">Menüleiste-Klasse</span><span class="sxs-lookup"><span data-stu-id="981f6-198">MenuBar class</span></span>](/uwp/api/Windows.UI.Xaml.Controls.MenuBar)
