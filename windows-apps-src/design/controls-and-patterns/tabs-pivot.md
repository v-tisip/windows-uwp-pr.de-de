---
author: serenaz
Description: Tabs and pivots enable users to navigate between frequently accessed content.
title: Registerkarten und Pivots
ms.assetid: 556BC70D-CF5D-4295-A655-D58163CC1824
label: Tabs and pivots
template: detail.hbs
ms.author: sezhen
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
pm-contact: yulikl
design-contact: kimsea
dev-contact: llongley
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 09e88fd070f7e7517e55d6f57563dd7608696770
ms.sourcegitcommit: 2470c6596d67e1f5ca26b44fad56a2f89773e9cc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
ms.locfileid: "1675477"
---
# <a name="pivot-and-tabs"></a>Pivot und Registerkarten



Das Pivot-Steuerelement und das verwandte Registerkartenmuster werden für die Navigation zwischen häufig genutzten verschiedenen Inhaltskategorien verwendet. Pivots ermöglichen die Navigation zwischen mindestens zwei Inhaltsbereichen und nutzen Textheader, um die verschiedenen Inhaltsabschnitte zu bezeichnen.

> **Wichtige APIs**: [Pivot-Klasse](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Pivot)

![Beispiel eines Pivot-Steuerelements](images/pivot_Hero_main.png)

Registerkarten stellen eine visuelle Variante eines Pivots dar, die eine Kombination aus Symbolen und Text oder nur Symbole verwenden, um Abschnittsinhalte zu gliedern. Registerkarten werden mit dem [Pivot](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.aspx)-Steuerelement erstellt. Das [Pivotbeispiel](http://go.microsoft.com/fwlink/p/?LinkId=619903) zeigt, wie das Pivot-Steuerelement an das Registerkartenmuster angepasst wird.

![Beispiel für Registerkartenmuster](images/tabs.png) 

## <a name="the-pivot-control"></a>Das Pivotsteuerelement

Wenn Sie eine App mit dem Pivot erstellen, sind einige wichtige Designelemente zu berücksichtigen.

- **Headerbeschriftungen.**  Header können über ein Symbol mit Text, nur über ein Symbol oder nur über Text verfügen.
- **Headerausrichtung.**  Header können links ausgerichtet oder zentriert werden.
- **Navigation auf oberster oder auf einer untergeordneten Ebene.**  Pivots können für eine der Navigationsebenen verwendet werden. Optional kann die [Navigationsansicht](navigationview.md) als primäre Ebene dienen und das Pivot als sekundäre.
- **Unterstützung für Touchbewegungen.**  Für Geräte, die Touchbewegungen unterstützen, können Sie zur Navigation zwischen Inhaltskategorien eine von zwei Interaktionen verwenden:
    1. Tippen Sie auf einen Registerkarten-/Pivotheader, um zur gewünschten Kategorie zu navigieren.
    2. Wischen Sie über dem Inhaltsbereich nach links oder rechts, um zur benachbarten Kategorie zu navigieren.

## <a name="examples"></a>Beispiele

<table>
<th align="left">XAML-Steuerelementekatalog<th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p>Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/Pivot">die App zu öffnen und Pivot in Aktion zu sehen</a>.</p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics">Erwerben Sie den Quellcode (GitHub)</a></li>
    </ul>
</td>
</tr>
</table>

Pivot-Steuerelement auf dem Handy

![Beispiel für ein Pivot](images/pivot_example.png)

Registerkartenmuster in der App „Alarm & Uhr“

![Beispiel für ein Registerkartenmuster in „Alarm & Uhr“](images/tabs_alarms-and-clock.png)

## <a name="create-a-pivot-control"></a>Erstellen eines Pivot-Steuerelements

Das [Pivot](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Pivot)-Steuerelement enthält die in diesem Abschnitt beschriebenen grundlegenden Funktionen.

Dieser XAML-Code erzeugt ein grundlegendes Pivot-Steuerelement mit 3 Inhaltsbereichen.

```xaml
<Pivot x:Name="rootPivot" Title="Pivot Title">
    <PivotItem Header="Pivot Item 1">
        <!--Pivot content goes here-->
        <TextBlock Text="Content of pivot item 1."/>
    </PivotItem>
    <PivotItem Header="Pivot Item 2">
        <!--Pivot content goes here-->
        <TextBlock Text="Content of pivot item 2."/>
    </PivotItem>
    <PivotItem Header="Pivot Item 3">
        <!--Pivot content goes here-->
        <TextBlock Text="Content of pivot item 3."/>
    </PivotItem>
</Pivot>
```

### <a name="pivot-items"></a>Pivot-Elemente

Das Pivot-Steuerelement ist ein [ItemsControl](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.aspx), daher kann es eine Sammlung von Elementen jeden Typs enthalten. Jedes zum Pivot-Steuerelement hinzugefügte Element, das nicht ausdrücklich ein [PivotItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivotitem.aspx)-Element ist, wird implizit in ein PivotItem eingeschlossen. Da ein Pivot-Element häufig zum Navigieren zwischen Inhaltsseiten verwendet wird, ist es üblich, die Sammlung von [Elementen](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.items.aspx) direkt mit XAML-UI-Elementen zu füllen. Alternativ können Sie die Eigenschaft [ItemsSource](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemssource.aspx) auf eine Datenquelle festlegen. In der ItemsSource gebundene Elemente können beliebigen Typs sein, wenn es sich jedoch nicht explizit um PivotItems handelt, müssen Sie eine [ItemTemplate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemtemplate.aspx)- und eine [HeaderTemplate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.headertemplate.aspx)-Eigenschaft definieren, um festzulegen, wie die Elemente angezeigt werden sollen.

Mit der Eigenschaft [SelectedItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.selecteditem.aspx) können Sie das aktive Element des Pivot-Steuerelements abrufen oder festlegen. Mit der Eigenschaft [SelectedIndex](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.selectedindex.aspx) können Sie den Index des aktiven Elements abrufen oder festlegen.

### <a name="pivot-headers"></a>Pivotheader

Sie können die Eigenschaften [LeftHeader](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.leftheader.aspx) und [RightHeader](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.rightheader.aspx) verwenden, um weitere Steuerelemente zum Pivotheader hinzuzufügen.

Sie können dem RightHeader des Pivot-Steuerelements z.B. eine [CommandBar](https://docs.microsoft.com/en-us/windows/uwp/controls-and-patterns/app-bars) hinzufügen.

![Beispiel für eine Befehlsleiste im rechten Header des Pivotsteuerelements](images/PivotHeader.png)

```xaml
<Pivot>
    <Pivot.RightHeader>
        <CommandBar OverflowButtonVisibility="Collapsed" Background="Transparent">
                <AppBarButton Icon="Add"/>
                <AppBarSeparator/>
                <AppBarButton Icon="Edit"/>
                <AppBarButton Icon="Delete"/>
                <AppBarSeparator/>
                <AppBarButton Icon="Save"/>
        </CommandBar>
    </Pivot.RightHeader>
</Pivot>
```

### <a name="pivot-interaction"></a>Pivot-Interaktion

Das Steuerelement erkennt die folgenden Touchgesteninteraktionen:

-   Durch Tippen auf den Header eines Pivotelements wird zum Abschnittsinhalt dieses Headers navigiert.
-   Durch Wischen nach links oder rechts auf dem Header eines Pivotelements wird zum benachbarten Abschnitt navigiert.
-   Durch Wischen nach links oder rechts auf einem Abschnittsinhalt wird zum benachbarten Abschnitt navigiert.

![Beispiel für eine Wischbewegung nach links auf dem Abschnittsinhalt](images/pivot_w_hand.png)

Das Steuerelement ist in zwei Modi verfügbar:

**Stationär**

-   Pivots werden nicht verschoben, wenn alle Pivotheader in den zulässigen Bereich passen.
-   Durch Tippen auf eine Pivotbeschriftung wird zur entsprechenden Seite navigiert. Das Pivot selbst wird jedoch nicht verschoben. Das aktive Pivot wird hervorgehoben.

**Karussell**

-   Falls nicht alle Pivotheader in den verfügbaren Bereich passen, werden Pivots in einer Karussellansicht dargestellt.
-   Durch Tippen auf eine Pivotbeschriftung wird die entsprechende Seite aufgerufen, und die aktive Pivotbeschriftung rückt an die erste Position.
-   Pivotelemente in einer Karussellschleife wechseln vom letzten zum ersten Pivotabschnitt.

> **Hinweis** Pivotheader sollten in einer [10-Fuß-Umgebung](../devices/designing-for-tv.md) nicht in einer Karussellansicht dargestellt werden. Legen Sie die [IsHeaderItemsCarouselEnabled](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Pivot.IsHeaderItemsCarouselEnabled)-Eigenschaft auf **false** fest, wenn Ihre App auf der Xbox ausgeführt wird.

### <a name="pivot-focus"></a>Pivotfokus

Der Tastaturfokus wird bei einem Pivotheader standardmäßig mit einem Unterstrich dargestellt.

![Standardfokus als Unterstrich des ausgewählten Headers](images/pivot_focus_selectedHeader.png)

Apps, die über ein benutzerdefiniertes Pivot verfügen und den Unterstrich in visuelle Objekte zur Headerauswahl integrieren, können die [HeaderFocusVisualPlacement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.pivot.HeaderFocusVisualPlacement)-Eigenschaft verwenden, um den Standardwert zu ändern. Wenn `HeaderFocusVisualPlacement="ItemHeaders"`, wird der Fokus um den gesamten Headerbereich gezeichnet.

![Bei der ItemsHeader-Option wird das Fokusrechteck um alle Pivotheader gezeichnet.](images/pivot_focus_headers.png)

## <a name="recommendations"></a>Empfehlungen

- Die Ausrichtung der Registerkarten-/Pivotheader sollte auf der Bildschirmgröße basieren. Bei Bildschirmbreiten unter 720 epx ist die Zentrierung in der Regel besser geeignet. Bei Bildschirmbreiten über 720 epx ist in den meisten Fällen die Linksausrichtung empfehlenswert.
- Vermeiden Sie mehr als 5 Header bei Verwendung des Karussell-Modus (Roundtrip), da mehr als Schleifen verwirrend sein können.
- Verwenden Sie das Registerkartenmuster nur, wenn Ihre Pivotelemente unterschiedliche Symbole besitzen.
- Fügen Sie Text in Pivotelementheader ein, damit Benutzer die Bedeutung der einzelnen Pivotabschnitte verstehen. Symbole sind nicht unbedingt für alle Benutzer selbsterklärend.

## <a name="get-the-sample-code"></a>Beispielcode herunterladen

- [Pivotbeispiel](http://go.microsoft.com/fwlink/p/?LinkId=619903) – Veranschaulicht, wie das Pivot-Steuerelement an das Registerkartenmuster angepasst wird.
- [Beispiel eines XAML-Steuerelementekatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.

## <a name="related-topics"></a>Verwandte Themen

- [Pivot-Klasse](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Pivot)
- [Navigationsdesigngrundlagen](../basics/navigation-basics.md)
