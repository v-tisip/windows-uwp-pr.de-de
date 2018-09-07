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
ms.sourcegitcommit: 00d27738325d6db5b5e481911ae7fac0711b05eb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2018
ms.locfileid: "3660071"
---
# <a name="menus-and-context-menus"></a>Menüs und Kontextmenüs



Menüs und Kontextmenüs zeigen auf Anforderung des Benutzers eine Liste von Befehlen oder Optionen an.

> **Wichtige APIs**: [MenuFlyout-Klasse](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.MenuFlyout), [ContextFlyout-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx), [FlyoutBase.AttachedFlyout-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout.aspx)

![Beispiel für ein typisches Kontextmenü](images/contextmenu_rs2_icons.png)


## <a name="is-this-the-right-control"></a>Ist dies das richtige Steuerelement?
Menüs und Kontextmenüs sparen Platz, indem Befehle angeordnet und ausgeblendet werden, bis der Benutzer sie benötigt. Wenn ein bestimmter Befehl häufig verwendet wird und Sie genügend Platz haben, sollten Sie ihn direkt als eigenes Element und nicht in einem Menü platzieren, damit Benutzer das Menü nicht durchlaufen müssen, um ihn aufzurufen.

Menüs und Kontextmenüs dienen dazu, Befehle strukturiert anzuordnen. Um beliebige Inhalte anzuzeigen, z. B. eine Benachrichtigung oder die Bestätigung einer Anfrage, verwenden Sie ein [Dialogfeld oder Flyout](dialogs.md).  

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

Menüs und Kontextmenüs sind identisch, was ihr Erscheinungsbild und ihren Inhalt angeht. Tatsächlich werden beide mit demselben Steuerelement erstellt, [MenuFlyout](https://msdn.microsoft.com/library/windows/apps/dn299030). Der einzige Unterschied ist, wie Sie den Benutzer darauf zugreifen lassen.

Wann sollten Sie ein Menü und wann ein Kontextmenü verwenden?
* Ist das übergeordnete Element eine Schaltfläche oder ein anderes Befehlselement, dessen primäre Funktion es ist, weitere Befehle zu präsentieren, verwenden Sie ein Menü.
* Wenn das übergeordnete Element eine andere Art von Element ist, das hauptsächlich einem anderen Zweck dient (z. B. der Anzeige von Text oder einem Bild), verwenden Sie ein Kontextmenü.

Verwenden Sie beispielsweise ein Menü auf einer Schaltfläche in einem Navigationsbereich, um zusätzliche Navigationsoptionen bereitzustellen. Der Hauptzweck des Schaltflächen-Steuerelements ist in diesem Szenario, auf ein Menü zuzugreifen.

![Beispiel des Menüs in Mail](images/Mail_Menu.png)

Wenn Sie Befehle (z. B. Ausschneiden, Kopieren und Einfügen) hinzufügen möchten, verwenden Sie ein Kontextmenü anstelle eines Menüs. In diesem Szenario ist die Hauptfunktion des Textelements Text zur Ansicht und zum Bearbeiten anzuzeigen. Weitere Befehle (z. B. Ausschneiden, Kopieren und Einfügen) sind sekundär und gehören in ein Kontextmenü.

![Beispiel des Kurzbefehlmenüs in der Fotogalerie](images/ContextMenu_example.png) 

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
   <p><b>Menüs</b></p>
<ul>
<li>Haben Sie einen einzigen Einstiegspunkt (am oberen Bildschirmrand, z. B. über ein Menü „Datei“), der immer angezeigt wird</li>
<li>Werden in der Regel an eine Schaltfläche oder ein übergeordnetes Menüelement angehängt</li>
<li>Werden mit der linken Maustaste (oder einer entsprechenden Aktion, z. B. durch Tippen) aufgerufen</li><li>Werden Elementen über ihre <a href="https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.button.flyout.aspx">Flyout</a>- oder <a href="https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout.aspx">FlyoutBase.AttachedFlyout</a>-Eigenschaft zugeordnet.</li>
</ul>
</div>
  <div class="side-by-side-content-right">
   <p><b>Kontextmenüs</b></p>

<ul>
<li>Sind mit einem einzelnen Element verknüpft und zeigen Sekundärbefehle an.</li>
<li>Werden mit der rechten Maustaste (oder einer entsprechenden Aktion, z. B. durch Tippen und Halten) aufgerufen.</li><li>Sind mit einem Element über dessen <a href="https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx">ContextFlyout</a>-Eigenschaft verknüpft.</li>
</ul>
  </div>
</div>
</div>

## <a name="icons"></a>Symbole

Erwägen Sie in folgenden Fällen Symbole für die Menüpunkte einzurichten:

<ul>
<li> Für am häufigsten verwendete Elemente </li>
<li> Für Menüpunkte, für die allgemein bekannte oder Standardsymbole vorhanden sind </li>
<li> Für Menüpunkte, deren Funktion auf einfache Weise mit einem Symbol veranschaulicht werden kann </li>
</ul>

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
> Die Größe der Symbole für MenuFlyoutItems ist 16x16px. Wenn Sie SymbolIcon, FontIcon oder PathIcon verwenden, wird das Symbol automatisch verlustfrei auf die richtige Größe skaliert. Achten Sie bei der Verwendung von BitmapIcon darauf, dass Ihr Element 16x16px groß sein muss.  

## <a name="create-a-menu-or-a-context-menu"></a>Erstellen eines Menüs bzw. Kontextmenüs

Um ein Menü oder ein Kontextmenü zu erstellen, verwenden Sie die [MenuFlyout-Klasse](https://msdn.microsoft.com/library/windows/apps/dn299030). Sie definieren den Inhalt des Menüs, indem Sie dem MenuFlyout die Objekte [MenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutitem.aspx), [ToggleMenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.togglemenuflyoutitem.aspx) und [MenuFlyoutSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutseparator.aspx) hinzufügen. Diese Objekte erfüllen folgende Zwecke:
* [MenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutitem.aspx): Ausführen einer sofortigen Aktion
* [ToggleMenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.togglemenuflyoutitem.aspx): Ein- und Ausschalten einer Option
* [MenuFlyoutSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutseparator.aspx)—Optisches Trennen von Menüelementen


In diesem Beispiel wird ein [MenuFlyout-Klasse](https://msdn.microsoft.com/library/windows/apps/dn299030) erstellt, und anschließend wird mit der [ContextFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx)-Eigenschaft, die für die meisten Steuerelemente verfügbar ist, die [MenuFlyout-Klasse](https://msdn.microsoft.com/library/windows/apps/dn299030) als Kontextmenü angezeigt.

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


> Einfach ausgeblendete Steuerelemente wie Menüs, Kontextmenüs und andere Flyouts erhalten in der vorübergehenden Benutzeroberfläche den Tastatur- bzw. Gamepad-Fokus, bis sie nicht mehr angezeigt werden. Um dieses Verhalten optisch zu kennzeichnen, werden diese Steuerelemente auf der Xbox als Überlagerung gezeichnet, wobei Helligkeit bzw. die Sichtbarkeit umgebenden Benutzeroberfläche reduziert wird. Dieses Verhalten lässt sich mit der Eigenschaft  [LightDismissOverlayMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.lightdismissoverlaymode.aspx) anpassen. Standardmäßig nutzen transiente Benutzeroberflächen die einfach auszublendende Überlagerung für die Xbox (**Auto**), jedoch nicht für andere Gerätereihen. Apps können jedoch durchsetzen, dass die Überlagerung ständig **Ein** oder **Aus** ist.

> ```xaml
> <MenuFlyout LightDismissOverlayMode="Off" />
> ```

## <a name="get-the-sample-code"></a>Beispielcode herunterladen

- [Beispiel eines XAML-Steuerelementekatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.
- [Beispiel für XAML-Kontextmenü](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlContextMenu)

## <a name="related-articles"></a>Verwandte Artikel

- [MenuFlyout-Klasse](https://msdn.microsoft.com/library/windows/apps/dn299030)
