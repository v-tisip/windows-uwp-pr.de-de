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
ms.sourcegitcommit: a160b91a554f8352de963d9fa37f7df89f8a0e23
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/21/2018
ms.locfileid: "4125705"
---
# <a name="menus-and-context-menus"></a>Menüs und Kontextmenüs

> [!IMPORTANT]
> In diesem Artikel werden Funktionen beschrieben, die noch nicht veröffentlicht wurden und vor der kommerziellen Freigabe evtl. geändert werden. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen. Preview-Features benötigen die [neuesten Windows 10 Insider Preview-Build und SDK](https://insider.windows.com/for-developers/) oder der [Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).

Menüs und Kontextmenüs zeigen auf Anforderung des Benutzers eine Liste von Befehlen oder Optionen an. Verwenden Sie ein Flyout "Menü", um ein einziges, Inline-Menü anzuzeigen. Verwenden Sie eine Menüleiste, um eine Reihe von Menüs in einer horizontalen Zeile in der Regel am oberen Rand eines app-Fensters anzuzeigen. Jedes Menü kann Menüelemente und Untermenüs aufweisen.

![Beispiel für ein typisches Kontextmenü](images/contextmenu_rs2_icons.png)

| **Windows-UI-Bibliothek herunterladen** |
| - |
| Dieses Steuerelement ist Bestandteil der Windows-UI-Bibliothek, NuGet-Paket, das neue Steuerelemente und UI-Features für UWP-apps enthält. Weitere Informationen, einschließlich installationsanweisungen finden Sie die [Übersicht über die Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/). |

| **Plattform-APIs** | **Windows-UI-Bibliothek APIs** |
| - | - |
| [MenuFlyout-Klasse](/uwp/api/windows.ui.xaml.controls.menuflyout), [Menüleiste-Klasse](/uwp/api/windows.ui.xaml.controls.menubar), [ContextFlyout-Eigenschaft](/uwp/api/windows.ui.xaml.uielement.contextflyout), [FlyoutBase.AttachedFlyout-Eigenschaft](/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout) | [Menüleiste-Klasse](/uwp/api/microsoft.ui.xaml.controls.menubar) |

## <a name="is-this-the-right-control"></a>Ist dies das richtige Steuerelement?

Menüs und Kontextmenüs sparen Platz, indem Befehle angeordnet und ausgeblendet werden, bis der Benutzer sie benötigt. Wenn ein bestimmter Befehl häufig verwendet wird und Sie genügend Platz haben, sollten Sie ihn direkt als eigenes Element und nicht in einem Menü platzieren, damit Benutzer das Menü nicht durchlaufen müssen, um ihn aufzurufen.

Menüs und Kontextmenüs sind für das Organisieren von Befehlen. Verwenden Sie ein [Dialogfeld oder Flyout](dialogs.md), um beliebige Inhalte, z. B. eine Benachrichtigung oder eine Bestätigung Anforderung anzuzeigen.

### <a name="menubar-vs-menuflyout"></a>Menüleiste im Vergleich zu MenuFlyout

Um ein Menü in einem Flyout auf ein UI-Element auf Canvas angefügte anzuzeigen, verwenden Sie das MenuFlyout-Steuerelement zum Hosten Ihrer Menüelemente. Sie können ein Flyout "Menü" entweder als reguläre Menü oder als ein Kontextmenü aufrufen. Ein Flyout "Menü" hostet ein einziges auf oberster Ebene Menü (und optional Untermenüs).

Um eine Reihe von mehreren Menüs der obersten Ebene in einer horizontalen Zeile anzuzeigen, verwenden Sie eine Menüleiste. In der Regel positionieren Sie die Menüleiste am oberen Rand des app-Fensters.

### <a name="menubar-vs-commandbar"></a>Menüleiste im Vergleich zu CommandBar

Menüleiste und CommandBar darstellen beide Oberflächen, die Sie verwenden können, um Befehle für Ihre Benutzer verfügbar zu machen. Der Menüleiste bietet eine schnelle und einfache Möglichkeit, eine Reihe von Befehlen für apps verfügbar zu machen, die möglicherweise weitere Organisation oder Gruppierung, und klicken Sie dann eine CommandBar ermöglicht.

Sie können auch eine Menüleiste in Verbindung mit einer CommandBar verwenden. Verwenden Sie die Menüleiste, um den Großteil der Befehle und CommandBar markieren die am häufigsten verwendeten Befehle bereitzustellen.

## <a name="examples"></a>Beispiele

<table>
<th align="left">XAML-Steuerelementekatalog<th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p>Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/MenuFlyout">die App zu öffnen und MenuFlyout in Aktion zu sehen</a>.</p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics">Erwerben Sie den Quellcode (GitHub)</a></li>
    </ul>
</td>
</tr>
</table>

## <a name="menus-vs-context-menus"></a>Vergleich zwischen Menüs und Kontextmenüs

Menüs und Kontextmenüs sind ähnlich Erscheinungsbild und was sie enthalten können. In der Tat können Sie das gleiche Steuerelement [MenuFlyout](https://msdn.microsoft.com/library/windows/apps/dn299030), zu deren Erstellung verwenden. Der Unterschied ist, wie Sie den Benutzer darauf zugreifen lassen.

Wann sollten Sie ein Menü und wann ein Kontextmenü verwenden?

- Ist das übergeordnete Element eine Schaltfläche oder ein anderes Befehlselement, dessen primäre Funktion es ist, weitere Befehle zu präsentieren, verwenden Sie ein Menü.
- Wenn das übergeordnete Element eine andere Art von Element ist, das hauptsächlich einem anderen Zweck dient (z. B. der Anzeige von Text oder einem Bild), verwenden Sie ein Kontextmenü.

Verwenden Sie z. B. ein Menü auf eine Schaltfläche, um bereitzustellen, Filtern und Sortieren Optionen für eine Liste. Der Hauptzweck des Schaltflächen-Steuerelements ist in diesem Szenario, auf ein Menü zuzugreifen.

![Beispiel des Menüs in Mail](images/Mail_Menu.png)

Wenn Sie Befehle (z. B. Ausschneiden, Kopieren und Einfügen) hinzufügen möchten, verwenden Sie ein Kontextmenü anstelle eines Menüs. In diesem Szenario ist die Hauptfunktion des Textelements Text zur Ansicht und zum Bearbeiten anzuzeigen. Weitere Befehle (z. B. Ausschneiden, Kopieren und Einfügen) sind sekundär und gehören in ein Kontextmenü.

![Beispiel des Kurzbefehlmenüs in der Fotogalerie](images/ContextMenu_example.png)

### <a name="menus"></a>Menüs

- Haben Sie einen einzigen Einstiegspunkt (am oberen Bildschirmrand, z. B. über ein Menü „Datei“), der immer angezeigt wird
- Werden in der Regel an eine Schaltfläche oder ein übergeordnetes Menüelement angehängt
- Werden mit der linken Maustaste (oder einer entsprechenden Aktion, z. B. durch Tippen) aufgerufen
- Ein Element über seine [Flyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.button.flyout.aspx) oder [FlyoutBase.AttachedFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout.aspx) -Eigenschaften zugeordnet, oder in einer Menüleiste am oberen Rand des app-Fensters gruppiert.

### <a name="context-menus"></a>Kontextmenüs

- Sind mit einem einzelnen Element verknüpft und zeigen Sekundärbefehle an.
- Werden mit der rechten Maustaste (oder einer entsprechenden Aktion, z. B. durch Tippen und Halten) aufgerufen.
- Sind mit einem Element über dessen [ContextFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx)-Eigenschaft verknüpft.

## <a name="icons"></a>Symbole

Erwägen Sie in folgenden Fällen Symbole für die Menüpunkte einzurichten:

- Die am häufigsten verwendete Elemente.
- Menüelemente, dessen Symbol bekannte oder Standardsymbole ist.
- Menüelemente, dessen Symbol Ihrer Funktionen veranschaulicht.

Fühlen Sie sich nicht dazu verpflichtet, Befehle mit einem Symbol zu versehen, für die keine Standardsymbole vorhanden sind. Kryptische Symbole sind nicht hilfreich, machen das Menü unübersichtlich und hindern Benutzer daran, wichtige Menüpunkte einfach aufzufinden.

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
> Die Größe des Symbols in einem MenuFlyoutItem ist 16x16px. Wenn Sie SymbolIcon, FontIcon oder PathIcon verwenden, wird das Symbol automatisch auf die richtige Größe mit verlustfrei skaliert. Achten Sie bei der Verwendung von BitmapIcon darauf, dass Ihr Element 16x16px groß sein muss.  

## <a name="create-a-menu-flyout-or-a-context-menu"></a>Erstellen Sie ein Flyout "Menü" oder ein Kontextmenü

Um ein Menü-Flyout oder ein Kontextmenü zu erstellen, verwenden Sie die [MenuFlyout-Klasse](https://msdn.microsoft.com/library/windows/apps/dn299030). Sie definieren den Inhalt des Menüs, indem Sie dem MenuFlyout die Objekte [MenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutitem.aspx), [ToggleMenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.togglemenuflyoutitem.aspx) und [MenuFlyoutSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutseparator.aspx) hinzufügen.

Diese Objekte erfüllen folgende Zwecke:

- [MenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutitem.aspx): Ausführen einer sofortigen Aktion
- [ToggleMenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.togglemenuflyoutitem.aspx): Ein- und Ausschalten einer Option
- [MenuFlyoutSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutseparator.aspx)—Optisches Trennen von Menüelementen

Dieses Beispiel erstellt eine [MenuFlyout](https://msdn.microsoft.com/library/windows/apps/dn299030) und verwendet die [ContextFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx) -Eigenschaft, für die meisten Steuerelemente verfügbar MenuFlyout als Kontextmenü angezeigt.

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

Das nächste Beispiel ist nahezu identisch, aber anstelle der [ContextFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx)-Eigenschaft zur Anzeige der [MenuFlyout-Klasse](https://msdn.microsoft.com/library/windows/apps/dn299030) als Kontextmenü wird die [FlyoutBase.ShowAttachedFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.showattachedflyout)-Eigenschaft verwendet, um die Klasse als Menü anzuzeigen.

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

### <a name="light-dismiss"></a>Einfaches ausblenden

Einfach ausgeblendete Steuerelemente wie Menüs, Kontextmenüs und andere Flyouts erhalten in der vorübergehenden Benutzeroberfläche den Tastatur- bzw. Gamepad-Fokus, bis sie nicht mehr angezeigt werden. Um dieses Verhalten optisch zu kennzeichnen, werden diese Steuerelemente auf der Xbox als Überlagerung gezeichnet, wobei Helligkeit bzw. die Sichtbarkeit umgebenden Benutzeroberfläche reduziert wird. Dieses Verhalten lässt sich mit der Eigenschaft  [LightDismissOverlayMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.lightdismissoverlaymode.aspx) anpassen. Standardmäßig nutzen transiente Benutzeroberflächen die einfach auszublendende Überlagerung für die Xbox (**Auto**), jedoch nicht für andere Gerätereihen. Apps können jedoch durchsetzen, dass die Überlagerung ständig **Ein** oder **Aus** ist.

```xaml
<MenuFlyout LightDismissOverlayMode="Off" />
```

## <a name="create-a-menu-bar"></a>Erstellen einer Menüleiste

> **Vorschau**: Menüleiste erfordert die [neuesten Windows 10 Insider Preview-Build und SDK](https://insider.windows.com/for-developers/) oder der [Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).

Sie verwenden die gleichen Elementen Menüs in einer Menüleiste in einem Flyout "Menü" erstellen. Allerdings gruppieren anstelle von Gruppierung von MenuFlyoutItem-Objekten in einer MenuFlyout, Sie können in einem MenuBarItem-Element. Jede MenuBarItem wird als ein Menü der obersten Ebene der Menüleiste hinzugefügt.

![Beispiel für eine Menüleiste](images/menu-bar-submenu.png)

> [!NOTE]
> In diesem Beispiel wird veranschaulicht, wie nur die UI-Struktur erstellt, aber Implementierung einer der Befehle wird nicht angezeigt.

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

## <a name="get-the-sample-code"></a>Beispielcode herunterladen

- [Beispiel eines XAML-Steuerelementekatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.
- [Beispiel für XAML-Kontextmenü](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlContextMenu)

## <a name="related-articles"></a>Verwandte Artikel

- [MenuFlyout-Klasse](https://msdn.microsoft.com/library/windows/apps/dn299030)
- [Menüleiste-Klasse](/uwp/api/Windows.UI.Xaml.Controls.MenuBar)
