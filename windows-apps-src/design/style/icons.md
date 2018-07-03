---
author: mijacobs
Description: Good icons harmonize with typography and with the rest of the design language. They don’t mix metaphors, and they communicate only what’s needed, as speedily and simply as possible.
title: Symbole
ms.assetid: b90ac02d-5467-4304-99bd-292d6272a014
label: Icons
template: detail.hbs
ms.author: mijacobs
ms.date: 05/02/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
design-contact: Judysa
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 077967c37f76c8f1d0942f365344de65db13b041
ms.sourcegitcommit: ce45a2bc5ca6794e97d188166172f58590e2e434
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2018
ms.locfileid: "1983573"
---
# <a name="icons-for-uwp-apps"></a>Symbole für UWP-Apps

![Headerbild für Symbole](images/icons/header-icons.png)

Symbole bieten eine visuelle Kurzform für eine Aktion, ein Konzept oder ein Produkt. Durch das Komprimieren der Bedeutung in ein symbolisches Bild können Symbole Sprachhürden überwinden und dazu beitragen, eine sehr wertvolle Ressource zu sparen: Platz auf dem Bildschirm. 

Symbole können in Apps angezeigt werden – und außerhalb von Apps: 

:::row::: :::column::: **Symbole in der App**

        ![icons inside the app](images/icons/inside-icons.png)
        Inside your app, you use icons to represent an action, such as copying text or navigating to the settings page.
    :::column-end:::
    :::column:::
        **Icons outside the app**

        ![icons outside the app](images/icons/outside-icons.jpg)
         Outside your app, Windows uses an icon to represent your app in the start menu and in the taskbar. If the user chooses to pin your app to the start menu, your app's start tile can feature your app's icon. Your app's icon appears in the title bar and you can choose to create a splash screen with your app's logo.
    :::column-end:::
:::row-end:::

In diesem Artikel werden Symbole in Ihrer App beschrieben. Informationen zu Symbolen außerhalb Ihrer App (App-Symbole) finden Sie im [Artikel zu App- und Kachelsymbolen](/windows/uwp/design/shell/tiles-and-notifications/app-assets).

## <a name="when-to-use-icons"></a>Wann Symbole verwendet werden sollten

Symbole können Platz sparen, aber wann ist eine Verwendung sinnvoll? 

:::row::: :::column::: ![Sinnvoll](images/do.svg) ![Standardbild für Symbole](images/icons/icons-standard.svg)<br>

        Use an icon for actions, like cut, copy, paste, and save, or for navigation items in a navigation menu.
    :::column-end:::
    :::column:::
        ![don't](images/dont.svg)
        ![icons concept image](images/icons/icons-concept.svg)<br>

        Use an icon if one already exists for the concept you want to represent. (To see whether an icon exists, check the Segoe icon list.)
    :::column-end:::
:::row-end:::

:::row::: :::column::: ![Sinnvoll](images/do.svg) ![Einkaufswagensymbol](images/icons/icon-shopping-cart.svg)<br>

        Use an icon if it's easy for the user to understand what the icon means and it's simple enough to be clear at small sizes.
    :::column-end:::
    :::column:::
        ![dont](images/dont.svg)
        ![icons concept image](images/icons/icon-bad-example.png)<br>

        Don't use an icon if its meaning isn't clear, or if making it clear requires a complex shape.
    :::column-end:::
:::row-end:::



## <a name="using-the-right-type-of-icon"></a>Verwendung der richtigen Art von Symbol

Es gibt viele Möglichkeiten, ein Symbol zu erstellen. Sie können eine Symbolschriftart wie Segoe MDL2 Assets verwenden. Sie können ein eigenes vektorbasiertes Bild erstellen. Sie können sogar ein Bitmap-Bild verwenden, auch wenn das nicht empfohlen wird. Hier ist eine Übersicht über die verschiedenen Möglichkeiten zum Hinzufügen eines Symbols zu Ihrer App. 

### <a name="use-a-predefined-icon"></a>Verwenden eines vordefinierten Symbols
:::row::: :::column::: Microsoft bietet mehr als 1.000 Symbole in Form der Segoe MDL2 Assets-Schrift. Möglicherweise ist es nicht intuitiv, ein Symbol aus einer Schriftart zu nehmen, aber unsere Schriftanzeigetechnologie bedeutet, dass diese Symbole klar und scharf auf jedem Bildschirm, bei jeder Auflösung und in jeder Größe angezeigt werden. :::column-end::: :::column::: ![Vordefiniertes Symbolbild](images/icons/predefined-icon.png) :::column-end::: :::row-end:::

### <a name="use-a-font"></a>Verwenden einer Schriftart
:::row::: :::column::: Sie müssen nicht die Segoe MDL2 Assets-Schrift verwenden, sondern können jede Schriftart nutzen, die der Benutzer auf seinem System installiert hat, z. B. Wingdings oder Webdings.
:::column-end::: :::column::: ![Wingdings-Bild](images/icons/wingdings.png) :::column-end::: :::row-end:::

### <a name="use-a-scalable-vector-graphics-svg-file"></a>Verwenden einer SVG-Datei (Scalable Vector Graphics)
:::row::: :::column::: SVG-Ressourcen sind ideal für Symbole geeignet, weil sie in jeder Größe oder Auflösung immer gestochen scharf aussehen. Die meisten Zeichenanwendungen können in das SVG-Format exportieren. :::column-end::: :::column::: ![SVG-Bild](images/icons/icon-scale.gif) :::column-end::: :::row-end:::

### <a name="use-geometry-objects"></a>Verwenden geometrischer Objekte
::: Zeile:::::: Spalte::: Wie SVG-Dateien sind Geometrien eine vektorbasierte Ressource und werden deshalb immer gestochen scharf dargestellt. Das Erstellen einer Geometrie ist jedoch kompliziert, da Sie jeden Punkt und jede Kurve einzeln angeben müssen. Es ist wirklich nur eine gute Option, wenn Sie das Symbol ändern müssen, während Ihre App ausgeführt wird (z.B. um es zu animieren). Anweisungen finden Sie unter [Befehle zum Verschieben und Zeichnen von Geometrien](../../xaml-platform/move-draw-commands-syntax.md). :::column-end::: :::column::: ![Bild eines Geometrieobjekts](images/icons/geometry-objects.png) :::column-end::: :::row-end:::

### <a name="you-can-also-use-a-bitmap-image-such-as-png-gif-or-jpeg-although-we-dont-recommend-it"></a>Sie können auf ein Bitmap-Bild wie PNG, GIF oder JPEG verwenden, auch wenn das nicht empfohlen wird.
:::row::: :::column::: Bitmap-Bilder werden in einer bestimmten Größe erstellt, sodass sie je nach gewünschter Symbolgröße und Auflösung des Bildschirms vergrößert oder verkleinert werden müssen. Wenn das Bild verkleinert wird, kann es verschwommen angezeigt werden. Wenn es vergrößert wird, kann es eckig und verpixelt aussehen. Wenn Sie ein Bitmap-Bild verwenden müssen, empfehlen wir die Verwendung einer PNG- oder GIF-Datei anstelle des JPEG-Formats. :::column-end::: :::column::: ![Nicht sinnvoll](images/dont.svg) ![Bitmap-Bild](images/icons/bitmap-image.png) :::column-end::: :::row-end:::

## <a name="make-the-icon-do-something"></a>Festlegen einer Aktion für das Symbol

Sobald Sie ein Symbol haben, besteht der nächste Schritt darin, es Aktion ausführen zu lassen, indem Sie ihm einen Befehl oder eine Navigationsaktion zuordnen. Am einfachsten können Sie dies erreichen, indem Sie das Symbol zu einer Schaltfläche oder Befehlsleiste hinzufügen. 

![Befehlsleistenbild](images/icons/app-bar-desktop.svg)

## <a name="create-an-icon-button"></a>Erstellen einer Symbolschaltfläche

Sie können ein Symbol in eine Standardschaltfläche einfügen. Da Sie Schaltflächen an vielfältigeren Orten verwenden können, erhalten Sie damit etwas mehr Flexibilität, welcher Stelle Ihr Aktionssymbol angezeigt wird. 

Es gibt verschiedene Möglichkeiten, ein Symbol zu einer Schaltfläche hinzuzufügen:

:::row::: :::column span="2"::: <b>Schritt 1</b><br>
        Legen Sie die Schriftfamilie der Schaltfläche auf `Segoe MDL2 Assets` und seine Inhaltseigenschaft auf den Unicode-Wert des gewünschten Symbols fest: ::column-end::: :::column::: ![Erstellen einer Symbolschaltfläche – Schritt1](images/icons/create-icon-step-1.svg) :::column-end::: :::row-end:::

```xaml 
<Button FontFamily="Segoe MDL2 Assets" Content="&#xE102;" />
```

:::row::: :::column span="2"::: <b>Schritt 2</b><br>
        Sie können eins der Symbolelementobjekte verwenden: [BitmapIcon](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.bitmapicon), [FontIcon](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.fonticon), [PathIcon](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.pathicon) oder [SymbolIcon](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.symbolicon). Damit werden Ihnen mehr Symboltypen zur Auswahl gestellt, und Sie können bei Bedarf Symbole und andere Arten von Inhalten wie Text kombinieren: :::column-end::: :::column::: ![Erstellen einer Symbolschaltfläche – Schritt2](images/icons/icon-text-step-2.svg) :::column-end::: :::row-end:::

```xaml 
<Button>
    <StackPanel>
        <SymbolIcon Symbol="Play" />
        <TextBlock>Play the movie</TextBlock>
    </StackPanel>
</Button>
```

## <a name="create-a-series-of-icons-in-a-command-bar"></a>Erstellen einer Reihe von Symbolen in einer Befehlsleiste

:::row::: :::column span::: Wenn Sie eine Reihe von Befehlen haben, die zusammengehöhren, z.B. Ausschneiden/Kopieren/Einfügen oder eine Reihe von Zeichenbefehlen für ein Fotobearbeitungsprogramm, setzen Sie diese zusammen in eine [Befehlsleiste](../controls-and-patterns/app-bars.md). Eine Befehlsleiste enthält eine oder mehrere Schaltflächen oder Umschaltflächen der App-Leiste, die jeweils eine Aktion darstellen. Jede Schaltfläche verfügt über eine [Symbol](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.appbarbutton#Windows_UI_Xaml_Controls_AppBarButton_Icon)-Eigenschaft, mit der Sie steuern, welches Symbol angezeigt wird. Es gibt eine Vielzahl von Möglichkeiten, um das Symbol anzugeben. :::column-end::: :::column::: ![Beispiel einer Befehlsleiste mit Symbolen](images/icons/create-icon-command-bar.svg) :::column-end::: :::row-end:::

Die einfachste Möglichkeit ist die Verwendung der von uns bereitgestellten Liste vordefinierter Symbole: Geben Sie einfach den Namen des Symbols an, z.B. „Zurück“ oder „Beenden“, und das System zeichnet das entsprechende Symbol: 

``` xaml
<CommandBar>
    <AppBarToggleButton Icon="Shuffle" Label="Shuffle" Click="AppBarButton_Click" />
    <AppBarToggleButton Icon="RepeatAll" Label="Repeat" Click="AppBarButton_Click"/>
    <AppBarSeparator/>
    <AppBarButton Icon="Back" Label="Back" Click="AppBarButton_Click"/>
    <AppBarButton Icon="Stop" Label="Stop" Click="AppBarButton_Click"/>
    <AppBarButton Icon="Play" Label="Play" Click="AppBarButton_Click"/>
    <AppBarButton Icon="Forward" Label="Forward" Click="AppBarButton_Click"/>
</CommandBar>

```
Die vollständige Liste mit Symbolnamen finden Sie in der [Symbolenumeration](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.symbol). 

Es gibt andere Möglichkeiten zum Bereitstellen von Symbolen für eine Schaltfläche in einer Befehlsleiste:

+ [FontIcon](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.fonticon): Das Symbol basiert auf einer Glyphe aus der angegebenen Schriftartfamilie.
+ [BitmapIcon](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.bitmapicon): Das Symbol basiert auf einer Bitmapbilddatei mit dem festgelegten **URI**.
+ [PathIcon](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.pathicon): Das Symbol basiert auf [Path](/uwp/api/windows.ui.xaml.shapes.path)-Daten.

Weitere Informationen zu Befehlszeilen finden Sie im [Artikel zu Befehlsleisten](../controls-and-patterns/app-bars.md). 



## <a name="related-articles"></a>Verwandte Artikel

* [Richtlinien für die Ressourcen für Kacheln und Symbole](../shell/tiles-and-notifications/app-assets.md)
