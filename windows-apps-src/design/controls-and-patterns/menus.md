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
ms.sourcegitcommit: 9e2c34a5ed3134aeca7eb9490f05b20eb9a3e5df
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2018
ms.locfileid: "3986311"
---
# <a name="menus-and-context-menus"></a><span data-ttu-id="09643-103">Menüs und Kontextmenüs</span><span class="sxs-lookup"><span data-stu-id="09643-103">Menus and context menus</span></span>

> [!IMPORTANT]
> <span data-ttu-id="09643-104">In diesem Artikel werden Funktionen beschrieben, die noch nicht veröffentlicht wurden und vor der kommerziellen Freigabe evtl. geändert werden.</span><span class="sxs-lookup"><span data-stu-id="09643-104">This article describes functionality that hasn’t been released yet and may be substantially modified before it's commercially released.</span></span> <span data-ttu-id="09643-105">Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.</span><span class="sxs-lookup"><span data-stu-id="09643-105">Microsoft makes no warranties, express or implied, with respect to the information provided here.</span></span> <span data-ttu-id="09643-106">Vorschaufeatures erfordern die [neueste Vorabversion von Windows 10 Insider und SDK](https://insider.windows.com/for-developers/) oder [UI-Bibliothek für Windows](https://docs.microsoft.com/uwp/toolkits/winui/).</span><span class="sxs-lookup"><span data-stu-id="09643-106">Preview features require the [latest Windows 10 Insider Preview build and SDK](https://insider.windows.com/for-developers/) or the [Windows UI Library](https://docs.microsoft.com/uwp/toolkits/winui/).</span></span>

<span data-ttu-id="09643-107">Menüs und Kontextmenüs zeigen auf Anforderung des Benutzers eine Liste von Befehlen oder Optionen an.</span><span class="sxs-lookup"><span data-stu-id="09643-107">Menus and context menus display a list of commands or options when the user requests them.</span></span> <span data-ttu-id="09643-108">Verwenden Sie ein Flyout Menü single Inline-Menü angezeigt.</span><span class="sxs-lookup"><span data-stu-id="09643-108">Use a menu flyout to show a single, inline menu.</span></span> <span data-ttu-id="09643-109">Verwenden einer Menüleiste Menüs in einer horizontalen Zeile normalerweise am oberen Rand eines Fensters app anzeigen.</span><span class="sxs-lookup"><span data-stu-id="09643-109">Use a menu bar to show a set of menus in a horizontal row, typically at the top of an app window.</span></span> <span data-ttu-id="09643-110">Jedes Menü können Menüelemente und Untermenüs.</span><span class="sxs-lookup"><span data-stu-id="09643-110">Each menu can have menu items and sub-menus.</span></span>

![Beispiel für ein typisches Kontextmenü](images/contextmenu_rs2_icons.png)

| **<span data-ttu-id="09643-112">Abrufen der Windows-UI-Bibliothek</span><span class="sxs-lookup"><span data-stu-id="09643-112">Get the Windows UI Library</span></span>** |
| - |
| <span data-ttu-id="09643-113">Dieses Steuerelement ist Bestandteil der Windows-Benutzeroberfläche Bibliothek ein NuGet-Paket, neue Steuerelemente und Features der Benutzeroberfläche für UWP-apps enthält.</span><span class="sxs-lookup"><span data-stu-id="09643-113">This control is included as part of the Windows UI Library, a NuGet package that contains new controls and UI features for UWP apps.</span></span> <span data-ttu-id="09643-114">Weitere Informationen einschließlich Installationshinweise finden Sie in der [UI-Bibliothek für Windows-Übersicht](https://docs.microsoft.com/uwp/toolkits/winui/).</span><span class="sxs-lookup"><span data-stu-id="09643-114">For more info, including installation instructions, see the [Windows UI Library overview](https://docs.microsoft.com/uwp/toolkits/winui/).</span></span> |

| **<span data-ttu-id="09643-115">Plattform-APIs</span><span class="sxs-lookup"><span data-stu-id="09643-115">Platform APIs</span></span>** | **<span data-ttu-id="09643-116">Windows-UI Library-APIs</span><span class="sxs-lookup"><span data-stu-id="09643-116">Windows UI Library APIs</span></span>** |
| - | - |
| <span data-ttu-id="09643-117">[MenuFlyout-Klasse](/uwp/api/windows.ui.xaml.controls.menuflyout) [MenuBar-Klasse](/uwp/api/windows.ui.xaml.controls.menubar) [ContextFlyout Eigenschaft](/uwp/api/windows.ui.xaml.uielement.contextflyout) [FlyoutBase.AttachedFlyout-Eigenschaft](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout)</span><span class="sxs-lookup"><span data-stu-id="09643-117">[MenuFlyout class](/uwp/api/windows.ui.xaml.controls.menuflyout), [MenuBar class](/uwp/api/windows.ui.xaml.controls.menubar), [ContextFlyout property](/uwp/api/windows.ui.xaml.uielement.contextflyout), [FlyoutBase.AttachedFlyout property](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout)</span></span> | [<span data-ttu-id="09643-118">MenuBar-Klasse</span><span class="sxs-lookup"><span data-stu-id="09643-118">MenuBar class</span></span>](/uwp/api/microsoft.ui.xaml.controls.menubar) |

## <a name="is-this-the-right-control"></a><span data-ttu-id="09643-119">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="09643-119">Is this the right control?</span></span>

<span data-ttu-id="09643-120">Menüs und Kontextmenüs sparen Platz, indem Befehle angeordnet und ausgeblendet werden, bis der Benutzer sie benötigt.</span><span class="sxs-lookup"><span data-stu-id="09643-120">Menus and context menus save space by organizing commands and hiding them until the user needs them.</span></span> <span data-ttu-id="09643-121">Wenn ein bestimmter Befehl häufig verwendet wird und Sie genügend Platz haben, sollten Sie ihn direkt als eigenes Element und nicht in einem Menü platzieren, damit Benutzer das Menü nicht durchlaufen müssen, um ihn aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="09643-121">If a particular command will be used frequently and you have the space available, consider placing it directly in its own element, rather than in a menu, so that users don't have to go through a menu to get to it.</span></span>

<span data-ttu-id="09643-122">Menüs und Kontextmenüs sind für Befehle angeordnet. Verwenden Sie ein [Dialogfeld oder ein Flyout](dialogs.md), um beliebige Inhalte wie eine Anforderung Benachrichtigung oder eine Bestätigung anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="09643-122">Menus and context menus are for organizing commands; to display arbitrary content, such as a notification or confirmation request, use a [dialog or a flyout](dialogs.md).</span></span>

### <a name="menubar-vs-menuflyout"></a><span data-ttu-id="09643-123">Menüleiste im Vergleich zu MenuFlyout</span><span class="sxs-lookup"><span data-stu-id="09643-123">MenuBar vs. MenuFlyout</span></span>

<span data-ttu-id="09643-124">Können Sie MenuFlyout-Steuerelement einem Menü in ein Flyout ein Benutzeroberflächenelement auf Leinwand verbunden anzuzeigen die Menüelementen speichern.</span><span class="sxs-lookup"><span data-stu-id="09643-124">To show a menu in a flyout attached to an on-canvas UI element, use the MenuFlyout control to host your menu items.</span></span> <span data-ttu-id="09643-125">Sie können ein Menü Flyout eine Speisekarte oder ein Kontextmenü aufrufen.</span><span class="sxs-lookup"><span data-stu-id="09643-125">You can invoke a menu flyout either as a regular menu or as a context menu.</span></span> <span data-ttu-id="09643-126">Ein Flyout Menü enthält ein Menü der obersten Ebene (und optional Untermenüs).</span><span class="sxs-lookup"><span data-stu-id="09643-126">A menu flyout hosts a single top-level menu (and optional sub-menus).</span></span>

<span data-ttu-id="09643-127">Um mehrere Menüs der obersten Ebene in einer horizontalen Zeile anzuzeigen, verwenden Sie eine Menüleiste.</span><span class="sxs-lookup"><span data-stu-id="09643-127">To show a set of multiple top-level menus in a horizontal row, use a menu bar.</span></span> <span data-ttu-id="09643-128">In der Regel positionieren Sie die Menüleiste am oberen Fensterrand app.</span><span class="sxs-lookup"><span data-stu-id="09643-128">You typically position the menu bar at the top of the app window.</span></span>

### <a name="menubar-vs-commandbar"></a><span data-ttu-id="09643-129">Menüleiste und CommandBar</span><span class="sxs-lookup"><span data-stu-id="09643-129">MenuBar vs. CommandBar</span></span>

<span data-ttu-id="09643-130">Menüleiste und CommandBar repräsentieren beide Flächen, mit denen Sie Befehle für die Benutzer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="09643-130">MenuBar and CommandBar both represent surfaces that you can use to expose commands to your users.</span></span> <span data-ttu-id="09643-131">Die Menüleiste ermöglicht das schnelle und einfache Befehle für apps verfügbar machen, die möglicherweise weitere Organisation oder Gruppierung dann eine Symbolleiste ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="09643-131">The MenuBar provides a quick and simple way to expose a set of commands for apps that might need more organization or grouping then a CommandBar allows.</span></span>

<span data-ttu-id="09643-132">Sie können auch eine Menüleiste in Verbindung mit einem CommandBar.</span><span class="sxs-lookup"><span data-stu-id="09643-132">You can also use a MenuBar in conjunction with a CommandBar.</span></span> <span data-ttu-id="09643-133">Verwenden der Menüleiste für den Großteil der Befehle und CommandBar markieren Sie die am häufigsten verwendeten Befehle.</span><span class="sxs-lookup"><span data-stu-id="09643-133">Use the MenuBar to provide the bulk of the commands, and the CommandBar to highlight the most used commands.</span></span>

## <a name="examples"></a><span data-ttu-id="09643-134">Beispiele</span><span class="sxs-lookup"><span data-stu-id="09643-134">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="09643-135">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="09643-135">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="09643-136">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/MenuFlyout">die App zu öffnen und MenuFlyout in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="09643-136">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/MenuFlyout">open the app and see the MenuFlyout in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="09643-137">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="09643-137">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="09643-138">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="09643-138">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="menus-vs-context-menus"></a><span data-ttu-id="09643-139">Vergleich zwischen Menüs und Kontextmenüs</span><span class="sxs-lookup"><span data-stu-id="09643-139">Menus vs. context menus</span></span>

<span data-ttu-id="09643-140">Menüs und Kontextmenüs sind ähnlich wie sie Aussehen und was sie enthalten können.</span><span class="sxs-lookup"><span data-stu-id="09643-140">Menus and context menus are similar in how they look and what they can contain.</span></span> <span data-ttu-id="09643-141">Tatsächlich können Sie das gleiche Steuerelement [MenuFlyout](https://msdn.microsoft.com/library/windows/apps/dn299030)erstellen.</span><span class="sxs-lookup"><span data-stu-id="09643-141">In fact, you can use the same control, [MenuFlyout](https://msdn.microsoft.com/library/windows/apps/dn299030), to create them.</span></span> <span data-ttu-id="09643-142">Der Unterschied ist wie den Benutzer darauf zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="09643-142">The difference is how you let the user access it.</span></span>

<span data-ttu-id="09643-143">Wann sollten Sie ein Menü und wann ein Kontextmenü verwenden?</span><span class="sxs-lookup"><span data-stu-id="09643-143">When should you use a menu or a context menu?</span></span>

- <span data-ttu-id="09643-144">Ist das übergeordnete Element eine Schaltfläche oder ein anderes Befehlselement, dessen primäre Funktion es ist, weitere Befehle zu präsentieren, verwenden Sie ein Menü.</span><span class="sxs-lookup"><span data-stu-id="09643-144">If the host element is a button or some other command element who's primary role is to present additional commands, use a menu.</span></span>
- <span data-ttu-id="09643-145">Wenn das übergeordnete Element eine andere Art von Element ist, das hauptsächlich einem anderen Zweck dient (z. B. der Anzeige von Text oder einem Bild), verwenden Sie ein Kontextmenü.</span><span class="sxs-lookup"><span data-stu-id="09643-145">If the host element is some other type of element that has another primary purpose (such as presenting text or an image), use a context menu.</span></span>

<span data-ttu-id="09643-146">Z. B. ein Menü auf einer Schaltfläche zu Filter- und Sortieroptionen für eine Liste.</span><span class="sxs-lookup"><span data-stu-id="09643-146">For example, use a menu on a button to provide filtering and sorting options for a list.</span></span> <span data-ttu-id="09643-147">Der Hauptzweck des Schaltflächen-Steuerelements ist in diesem Szenario, auf ein Menü zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="09643-147">In this scenario, the primary purpose of the button control is to provide access to a menu.</span></span>

![Beispiel des Menüs in Mail](images/Mail_Menu.png)

<span data-ttu-id="09643-149">Wenn Sie Befehle (z. B. Ausschneiden, Kopieren und Einfügen) hinzufügen möchten, verwenden Sie ein Kontextmenü anstelle eines Menüs.</span><span class="sxs-lookup"><span data-stu-id="09643-149">If you want to add commands (such as cut, copy, and paste) to a text element, use a context menu instead of a menu.</span></span> <span data-ttu-id="09643-150">In diesem Szenario ist die Hauptfunktion des Textelements Text zur Ansicht und zum Bearbeiten anzuzeigen. Weitere Befehle (z. B. Ausschneiden, Kopieren und Einfügen) sind sekundär und gehören in ein Kontextmenü.</span><span class="sxs-lookup"><span data-stu-id="09643-150">In this scenario, the primary role of the text element is to present and edit text; additional commands (such as cut, copy, and paste) are secondary and belong in a context menu.</span></span>

![Beispiel des Kurzbefehlmenüs in der Fotogalerie](images/ContextMenu_example.png)

### <a name="menus"></a><span data-ttu-id="09643-152">Menüs</span><span class="sxs-lookup"><span data-stu-id="09643-152">Menus</span></span>

- <span data-ttu-id="09643-153">Haben Sie einen einzigen Einstiegspunkt (am oberen Bildschirmrand, z. B. über ein Menü „Datei“), der immer angezeigt wird</span><span class="sxs-lookup"><span data-stu-id="09643-153">Have a single entry point (a File menu at the top of the screen, for example) that is always displayed.</span></span>
- <span data-ttu-id="09643-154">Werden in der Regel an eine Schaltfläche oder ein übergeordnetes Menüelement angehängt</span><span class="sxs-lookup"><span data-stu-id="09643-154">Are usually attached to a button or a parent menu item.</span></span>
- <span data-ttu-id="09643-155">Werden mit der linken Maustaste (oder einer entsprechenden Aktion, z. B. durch Tippen) aufgerufen</span><span class="sxs-lookup"><span data-stu-id="09643-155">Are invoked by left-clicking (or an equivalent action, such as tapping with your finger).</span></span>
- <span data-ttu-id="09643-156">Zugeordnete Elemente über seine Eigenschaften [Flyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.button.flyout.aspx) oder [FlyoutBase.AttachedFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout.aspx) oder in der Menüleiste am oberen Fensterrand app gruppiert.</span><span class="sxs-lookup"><span data-stu-id="09643-156">Are associated with an element via its [Flyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.button.flyout.aspx) or [FlyoutBase.AttachedFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout.aspx) properties, or grouped in a menu bar at the top of the app window.</span></span>

### <a name="context-menus"></a><span data-ttu-id="09643-157">Kontextmenüs</span><span class="sxs-lookup"><span data-stu-id="09643-157">Context menus</span></span>

- <span data-ttu-id="09643-158">Sind mit einem einzelnen Element verknüpft und zeigen Sekundärbefehle an.</span><span class="sxs-lookup"><span data-stu-id="09643-158">Are attached to a single element and display secondary commands.</span></span>
- <span data-ttu-id="09643-159">Werden mit der rechten Maustaste (oder einer entsprechenden Aktion, z. B. durch Tippen und Halten) aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="09643-159">Are invoked by right clicking (or an equivalent action, such as pressing and holding with your finger).</span></span>
- <span data-ttu-id="09643-160">Sind mit einem Element über dessen [ContextFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx)-Eigenschaft verknüpft.</span><span class="sxs-lookup"><span data-stu-id="09643-160">Are associated with an element via its [ContextFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx) property.</span></span>

## <a name="icons"></a><span data-ttu-id="09643-161">Symbole</span><span class="sxs-lookup"><span data-stu-id="09643-161">Icons</span></span>

<span data-ttu-id="09643-162">Erwägen Sie in folgenden Fällen Symbole für die Menüpunkte einzurichten:</span><span class="sxs-lookup"><span data-stu-id="09643-162">Consider providing menu item icons for:</span></span>

- <span data-ttu-id="09643-163">Die am verwendeten häufigsten Elemente.</span><span class="sxs-lookup"><span data-stu-id="09643-163">The most commonly used items.</span></span>
- <span data-ttu-id="09643-164">Menüelemente, dessen Symbol standard oder bekannt ist.</span><span class="sxs-lookup"><span data-stu-id="09643-164">Menu items whose icon is standard or well known.</span></span>
- <span data-ttu-id="09643-165">Elemente, deren Symbol gut veranschaulicht Ihrer Funktionen.</span><span class="sxs-lookup"><span data-stu-id="09643-165">Menu items whose icon well illustrates what the command does.</span></span>

<span data-ttu-id="09643-166">Fühlen Sie sich nicht dazu verpflichtet, Befehle mit einem Symbol zu versehen, für die keine Standardsymbole vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="09643-166">Don't feel obligated to provide icons for commands that don't have a standard visualization.</span></span> <span data-ttu-id="09643-167">Kryptische Symbole sind nicht hilfreich, machen das Menü unübersichtlich und hindern Benutzer daran, wichtige Menüpunkte einfach aufzufinden.</span><span class="sxs-lookup"><span data-stu-id="09643-167">Cryptic icons aren’t helpful, create visual clutter, and prevent users from focusing on the important menu items.</span></span>

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
> <span data-ttu-id="09643-169">Die Größe des Symbols in einem MenuFlyoutItem ist 16x16px.</span><span class="sxs-lookup"><span data-stu-id="09643-169">The size of the icon in a MenuFlyoutItem is 16x16px.</span></span> <span data-ttu-id="09643-170">Verwenden Sie SymbolIcon, FontIcon oder PathIcon, skaliert das Symbol automatisch an die richtige Größe ohne Verlust an Genauigkeit.</span><span class="sxs-lookup"><span data-stu-id="09643-170">If you use SymbolIcon, FontIcon, or PathIcon, the icon automatically scales to the correct size with no loss of fidelity.</span></span> <span data-ttu-id="09643-171">Achten Sie bei der Verwendung von BitmapIcon darauf, dass Ihr Element 16x16px groß sein muss.</span><span class="sxs-lookup"><span data-stu-id="09643-171">If you use BitmapIcon, ensure that your asset is 16x16px.</span></span>  

## <a name="create-a-menu-flyout-or-a-context-menu"></a><span data-ttu-id="09643-172">Ein Flyout Menü oder ein Kontextmenü erstellen</span><span class="sxs-lookup"><span data-stu-id="09643-172">Create a menu flyout or a context menu</span></span>

<span data-ttu-id="09643-173">Um ein Flyout Menü oder ein Kontextmenü erstellen, verwenden Sie die [MenuFlyout-Klasse](https://msdn.microsoft.com/library/windows/apps/dn299030).</span><span class="sxs-lookup"><span data-stu-id="09643-173">To create a menu flyout or a context menu, you use the [MenuFlyout class](https://msdn.microsoft.com/library/windows/apps/dn299030).</span></span> <span data-ttu-id="09643-174">Sie definieren den Inhalt des Menüs, indem Sie dem MenuFlyout die Objekte [MenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutitem.aspx), [ToggleMenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.togglemenuflyoutitem.aspx) und [MenuFlyoutSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutseparator.aspx) hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="09643-174">You define the contents of the menu by adding [MenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutitem.aspx), [ToggleMenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.togglemenuflyoutitem.aspx), and [MenuFlyoutSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutseparator.aspx) objects to the MenuFlyout.</span></span>

<span data-ttu-id="09643-175">Diese Objekte erfüllen folgende Zwecke:</span><span class="sxs-lookup"><span data-stu-id="09643-175">These objects are for:</span></span>

- <span data-ttu-id="09643-176">[MenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutitem.aspx): Ausführen einer sofortigen Aktion</span><span class="sxs-lookup"><span data-stu-id="09643-176">[MenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutitem.aspx)—Performing an immediate action.</span></span>
- <span data-ttu-id="09643-177">[ToggleMenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.togglemenuflyoutitem.aspx): Ein- und Ausschalten einer Option</span><span class="sxs-lookup"><span data-stu-id="09643-177">[ToggleMenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.togglemenuflyoutitem.aspx)—Switching an option on or off.</span></span>
- <span data-ttu-id="09643-178">[MenuFlyoutSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutseparator.aspx)—Optisches Trennen von Menüelementen</span><span class="sxs-lookup"><span data-stu-id="09643-178">[MenuFlyoutSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutseparator.aspx)—Visually separating menu items.</span></span>

<span data-ttu-id="09643-179">In diesem Beispiel wird ein [MenuFlyout](https://msdn.microsoft.com/library/windows/apps/dn299030) erstellt und verwendet die [ContextFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx) Eigenschaft für die meisten Steuerelemente verfügbar MenuFlyout als Kontextmenü angezeigt.</span><span class="sxs-lookup"><span data-stu-id="09643-179">This example creates a [MenuFlyout](https://msdn.microsoft.com/library/windows/apps/dn299030) and uses the [ContextFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx) property, a property available to most controls, to show the MenuFlyout as a context menu.</span></span>

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

<span data-ttu-id="09643-180">Das nächste Beispiel ist nahezu identisch, aber anstelle der [ContextFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx)-Eigenschaft zur Anzeige der [MenuFlyout-Klasse](https://msdn.microsoft.com/library/windows/apps/dn299030) als Kontextmenü wird die [FlyoutBase.ShowAttachedFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.showattachedflyout)-Eigenschaft verwendet, um die Klasse als Menü anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="09643-180">The next example is nearly identical, but instead of using the [ContextFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx) property to show the [MenuFlyout class](https://msdn.microsoft.com/library/windows/apps/dn299030) as a context menu, the example uses the [FlyoutBase.ShowAttachedFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.showattachedflyout) property to show it as a menu.</span></span>

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

### <a name="light-dismiss"></a><span data-ttu-id="09643-181">Licht ausschalten</span><span class="sxs-lookup"><span data-stu-id="09643-181">Light dismiss</span></span>

<span data-ttu-id="09643-182">Einfach ausgeblendete Steuerelemente wie Menüs, Kontextmenüs und andere Flyouts erhalten in der vorübergehenden Benutzeroberfläche den Tastatur- bzw. Gamepad-Fokus, bis sie nicht mehr angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="09643-182">Light dismiss controls, such as menus, context menus, and other flyouts, trap keyboard and gamepad focus inside the transient UI until dismissed.</span></span> <span data-ttu-id="09643-183">Um dieses Verhalten optisch zu kennzeichnen, werden diese Steuerelemente auf der Xbox als Überlagerung gezeichnet, wobei Helligkeit bzw. die Sichtbarkeit umgebenden Benutzeroberfläche reduziert wird.</span><span class="sxs-lookup"><span data-stu-id="09643-183">To provide a visual cue for this behavior, light dismiss controls on Xbox will draw an overlay that dims the visibility of out of scope UI.</span></span> <span data-ttu-id="09643-184">Dieses Verhalten lässt sich mit der Eigenschaft  [LightDismissOverlayMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.lightdismissoverlaymode.aspx) anpassen.</span><span class="sxs-lookup"><span data-stu-id="09643-184">This behavior can be modified with the  [LightDismissOverlayMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.lightdismissoverlaymode.aspx) property.</span></span> <span data-ttu-id="09643-185">Standardmäßig nutzen transiente Benutzeroberflächen die einfach auszublendende Überlagerung für die Xbox (**Auto**), jedoch nicht für andere Gerätereihen. Apps können jedoch durchsetzen, dass die Überlagerung ständig **Ein** oder **Aus** ist.</span><span class="sxs-lookup"><span data-stu-id="09643-185">By default, transient UIs will draw the light dismiss overlay on Xbox (**Auto**) but not other device families, but apps can choose to force the overlay to be always **On** or always **Off**.</span></span>

```xaml
<MenuFlyout LightDismissOverlayMode="Off" />
```

## <a name="create-a-menu-bar"></a><span data-ttu-id="09643-186">Erstellen einer Menüleiste</span><span class="sxs-lookup"><span data-stu-id="09643-186">Create a menu bar</span></span>

> <span data-ttu-id="09643-187">**Vorschau**: MenuBar erfordert die [neueste Vorabversion von Windows 10 Insider und SDK](https://insider.windows.com/for-developers/) oder [UI-Bibliothek für Windows](https://docs.microsoft.com/uwp/toolkits/winui/).</span><span class="sxs-lookup"><span data-stu-id="09643-187">**Preview**: MenuBar requires the [latest Windows 10 Insider Preview build and SDK](https://insider.windows.com/for-developers/) or the [Windows UI Library](https://docs.microsoft.com/uwp/toolkits/winui/).</span></span>

<span data-ttu-id="09643-188">Sie verwenden die gleichen Elemente Menüs in der Menüleiste im Menü Flyout erstellen.</span><span class="sxs-lookup"><span data-stu-id="09643-188">You use the same elements to create menus in a menu bar as in a menu flyout.</span></span> <span data-ttu-id="09643-189">Allerdings gruppieren statt Gruppierung von Objekten in einem MenuFlyout MenuFlyoutItem, Sie in einem MenuBarItem-Element.</span><span class="sxs-lookup"><span data-stu-id="09643-189">However, instead of grouping MenuFlyoutItem objects in a MenuFlyout, you group them in a MenuBarItem element.</span></span> <span data-ttu-id="09643-190">Jedes MenuBarItem wird der Menüleiste ein Menü der obersten Ebene hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="09643-190">Each MenuBarItem is added to the MenuBar as a top level menu.</span></span>

![Beispiel einer Menüleiste](images/menu-bar-submenu.png)

> [!NOTE]
> <span data-ttu-id="09643-192">Dieses Beispiel zeigt, wie die Benutzeroberfläche Struktur jedoch zeigt keine Implementierung einer der Befehle.</span><span class="sxs-lookup"><span data-stu-id="09643-192">This example shows only how to create the UI structure, but does not show implementation of any of the commands.</span></span>

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

## <a name="get-the-sample-code"></a><span data-ttu-id="09643-193">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="09643-193">Get the sample code</span></span>

- <span data-ttu-id="09643-194">[Beispiel eines XAML-Steuerelementekatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="09643-194">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>
- [<span data-ttu-id="09643-195">Beispiel für XAML-Kontextmenü</span><span class="sxs-lookup"><span data-stu-id="09643-195">XAML Context menu sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlContextMenu)

## <a name="related-articles"></a><span data-ttu-id="09643-196">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="09643-196">Related articles</span></span>

- [<span data-ttu-id="09643-197">MenuFlyout-Klasse</span><span class="sxs-lookup"><span data-stu-id="09643-197">MenuFlyout class</span></span>](https://msdn.microsoft.com/library/windows/apps/dn299030)
- [<span data-ttu-id="09643-198">MenuBar-Klasse</span><span class="sxs-lookup"><span data-stu-id="09643-198">MenuBar class</span></span>](/uwp/api/Windows.UI.Xaml.Controls.MenuBar)
