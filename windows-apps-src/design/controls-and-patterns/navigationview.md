---
author: jwmsft
Description: NavigationView is an adaptive control that implements top-level navigation patterns for your app.
title: Navigationsansicht
template: detail.hbs
ms.author: jimwalk
ms.date: 10/02/2018
ms.topic: article
keywords: Windows 10, UWP
pm-contact: yulikl
design-contact: kimsea
dev-contact: ''
doc-status: Published
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: d8164571644c4e8ef84cae896fb7dce2265219e5
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7303603"
---
# <a name="navigation-view"></a>Navigationsansicht

Das NavigationView-Steuerelement bietet Navigation auf oberster Ebene für Ihre app. Es mit einer Vielzahl von Bildschirmgrößen anpasst und _oberen_ und _linken_ Navigationsbereich Formate unterstützt.

![oberen Navigationsleiste](images/nav-view-header.png)<br/>
_Navigationsansicht unterstützt sowohl am oberen und linken Navigationsbereich oder Menü_

> **Plattform-APIs**: [Windows.UI.Xaml.Controls.NavigationView-Klasse](/uwp/api/windows.ui.xaml.controls.navigationview)
>
> **Windows-UI-Bibliothek-APIs**: [Microsoft.UI.Xaml.Controls.NavigationView-Klasse](/uwp/api/microsoft.ui.xaml.controls.navigationview)
>
> Einige Features von NavigationView, z. B. _Top_ -Navigation, erfordern Windows 10, Version 1809 ([SDK 17763](https://developer.microsoft.com/windows/downloads/windows-10-sdk)) oder höher, oder in der [Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).

## <a name="is-this-the-right-control"></a>Ist dies das richtige Steuerelement?

NavigationView ist eine adaptive Navigationssteuerelement, das funktioniert gut für:

- Bereitstellen einer konsistenten navigationsumgebungen in der gesamten app.
- Sparen von Platz auf dem Bildschirm auf kleineren Fenstern.
- Organisieren von Zugriff auf viele Navigationskategorien.

Andere navigationsmuster finden Sie unter [navigationsdesigngrundlagen](../basics/navigation-basics.md).

## <a name="examples"></a>Beispiele

<table>
<th align="left">XAML-Steuerelementekatalog<th>
<tr>
<td><img src="images/XAML-controls-gallery-app-icon.png" alt="XAML controls gallery" width="168"></img></td>
<td>
    <p>Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/NavigationView">die App zu öffnen und NavigationView in Aktion zu sehen</a>.</p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics">Erwerben Sie den Quellcode (GitHub)</a></li>
    </ul>
</td>
</tr>
</table>

## <a name="display-modes"></a>Anzeigemodi

> Die Eigenschaft PaneDisplayMode erfordert Windows 10, Version 1809 ([SDK 17763](https://developer.microsoft.com/windows/downloads/windows-10-sdk)) oder höher, oder in der [Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).

Sie können die PaneDisplayMode-Eigenschaft verwenden, um verschiedene Navigation Stilen zu konfigurieren oder Anzeigemodi für die NavigationView.

:::row:::
    :::column:::
    ### <a name="top"></a>Oben
    Der Bereich wird oberhalb des Inhalts positioniert.</br>
    `PaneDisplayMode="Top"`
    :::column-end:::
    :::column span="2":::
    ![Beispiel für die Navigation oben](images/displaymode-top.png)
    :::column-end:::
:::row-end:::

Wir empfehlen _oberen_ Navigationsbereich bei:

- Sie haben 5 oder weniger Kategorien der Navigation auf oberster Ebene, die ebenso wichtig sind, und alle zusätzlichen Navigation auf oberster Ebene, die Kategorien, zu denen in der Dropdownliste Überlaufmenü landen weniger wichtig eingestuft werden.
- Sie müssen alle Navigationsoptionen auf dem Bildschirm anzeigen.
- Sie möchten mehr Platz für app-Inhalt.
- Symbole können nicht klar Navigationskategorien Ihrer app beschreiben.

:::row:::
    :::column:::
    ### <a name="left"></a>Links
    Der Bereich erweitert und auf der linken Seite des Inhalts positioniert.</br>
    `PaneDisplayMode="Left"`
    :::column-end:::
    :::column span="2":::
    ![Beispiel für erweiterte linken Navigationsbereich](images/displaymode-left.png)
    :::column-end:::
:::row-end:::

Wir empfehlen die _linke_ Navigation bei:

- Sie haben 5 bis 10 ebenso wichtig Navigation auf oberster Ebene Kategorien.
- Navigationskategorien sehr hervorgehoben, mit weniger Speicherplatz für andere app-Inhalte werden soll.

:::row:::
    :::column:::
    ### <a name="leftcompact"></a>LeftCompact
    Der Bereich zeigt nur die Symbole bis geöffnet, und auf der linken Seite des Inhalts positioniert wird.</br>
    `PaneDisplayMode="LeftCompact"`
    :::column-end:::
    :::column span="2":::
    ![Beispiel für compact linken Navigationsbereich](images/displaymode-leftcompact.png)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
    ### <a name="leftminimal"></a>LeftMinimal
    Nur die Menütaste wird angezeigt, bis das Fenster geöffnet ist. Beim Öffnen, wird es auf der linken Seite des Inhalts positioniert.</br>
    `PaneDisplayMode="LeftMinimal"`
    :::column-end:::
    :::column span="2":::
    ![Beispiel für die minimale linken Navigationsbereich](images/displaymode-leftminimal.png)
    :::column-end:::
:::row-end:::

### <a name="auto"></a>Auto

Standardmäßig ist PaneDisplayMode auf Auto festgelegt. Im Auto-Modus Navigationsansicht anpasst zwischen LeftMinimal, wenn das Fenster schmaler, um LeftCompact ist, und anschließend links im Fenster vergrößert wird. Weitere Informationen finden Sie im Abschnitt [adaptives Verhalten](#adaptive-behavior) .

![Linke Navigation standardmäßigen adaptiven Verhaltens](images/displaymode-auto.png)<br/>
_Navigation Ansicht standardmäßigen adaptiven Verhaltens_

## <a name="anatomy"></a>Aufbau

Diese Bilder zeigen das Layout der Bereich, Header und Inhalt Bereiche des Steuerelements für die _am oberen_ oder _linken_ Navigationsbereich konfiguriert.

![Layout der oberen Navigationsleiste anzeigen](images/topnav-anatomy.png)<br/>
_Layout der oberen Navigationsleiste_

![Layout des linken Navigationsbereich anzeigen](images/leftnav-anatomy.png)<br/>
_Linke Navigationslayout_

### <a name="pane"></a>Bereich

Die Eigenschaft PaneDisplayMode können Sie um den Bereich über dem Inhalt oder auf der linken Seite des Inhalts zu positionieren.

Der NavigationView-Bereich kann Folgendes enthalten:

- [NavigationViewItem](/uwp/api/windows.ui.xaml.controls.navigationviewitem) -Objekte. Navigationselemente zu bestimmten Seiten zu navigieren.
- [NavigationViewItemSeparator](/uwp/api/windows.ui.xaml.controls.navigationviewitemseparator) -Objekte. Trennzeichen Navigationselemente zu gruppieren. Legen Sie die [Opacity](/uwp/api/windows.ui.xaml.controls.navigationviewitemseparator.opacity) -Eigenschaft auf 0 fest, um das Trennzeichen Platz nötig rendern.
- [NavigationViewItemHeader](/uwp/api/windows.ui.xaml.controls.navigationviewitemheader) -Objekte. Header zum Beschriften von Gruppen von Elementen.
- Ein optionales [AutoSuggestBox](auto-suggest-box.md) -Steuerelement für die app-Ebene Suche zulassen. Weisen Sie das Steuerelement, um die [NavigationView.AutoSuggestBox](/uwp/api/windows.ui.xaml.controls.navigationview.autosuggestbox) -Eigenschaft.
- Ein optionaler Einstiegspunkt für [App-Einstellungen](../app-settings/app-settings-and-data.md). Um die Einstellungen Element auszublenden, die [IsSettingsVisible](/uwp/api/windows.ui.xaml.controls.navigationview.IsSettingsVisible) -Eigenschaft auf **"false"** festgelegt.

Der linke Bereich enthält auch:

- Eine Schaltfläche zum Umschalten des Bereichs geöffnet und geschlossen. Sie können bei größeren App-Fenstern mit geöffnetem Bereich diese Schaltfläche mit der Eigenschaft [IsPaneToggleButtonVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsPaneToggleButtonVisible) ausblenden.

Die Navigationsansicht hat eine zurück-Schaltfläche, die sich in der oberen linken Ecke des Bereichs befindet. Es jedoch nicht automatisch behandeln rückwärts Navigation und Hinzufügen von Inhalten zu dem zurück-Stapel. Zum Aktivieren der Rückwärtsnavigation, finden Sie unter der [Rückwärts Navigation](#backwards-navigation) Abschnitt.

Hier ist der Aufbau detaillierte Bereich für die Positionen oberen und linken Bereich.

#### <a name="top-navigation-pane"></a>Im oberen Navigationsbereich

![Navigation Ansicht oberen Bereich Anatomie](images/navview-pane-anatomy-horizontal.png)

1. Header
1. Navigationselemente
1. Trennzeichen
1. AutoSuggestBox (optional)
1. Schaltfläche "Einstellungen" (optional)

#### <a name="left-navigation-pane"></a>Linken Navigationsbereich

![Links Bereich Anatomie Navigationsansicht](images/navview-pane-anatomy-vertical.png)

1. Menü-Taste
1. Navigationselemente
1. Trennzeichen
1. Header
1. AutoSuggestBox (optional)
1. Schaltfläche "Einstellungen" (optional)

#### <a name="pane-footer"></a>Fußzeile

Sie können formfreie Inhalte in der Fußzeile des platzieren, indem Sie es an die Eigenschaft [PaneFooter](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneFooter) hinzufügen.

:::row:::
    :::column:::
    ![Bereich Fußzeile oben nav](images/navview-freeform-footer-top.png)<br>
     _Oberen Fußzeile_<br>
    :::column-end:::
    :::column:::
    ![Bereich Fußzeile linke Navigationsleiste](images/navview-freeform-footer-left.png)<br>
    _Linke Fußzeile_<br>
    :::column-end:::
:::row-end:::

#### <a name="pane-title-and-header"></a>Bereich Titel und header

Sie können im Bereich Headerbereich Textinhalt platzieren, durch Festlegen der [PaneTitle](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneTitle) -Eigenschaft. Sie akzeptiert eine Zeichenfolge und zeigt den Text neben der Schaltfläche "Menü".

Zum Hinzufügen von nicht-Text-Inhalt, z. B. ein Bild oder ein Logo, können Sie jedes Element im Header des Bereichs platzieren, indem Sie es an die Eigenschaft [PaneHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneHeader) hinzufügen.

Wenn PaneTitle sowohl PaneHeader festgelegt sind, wird der Inhalt horizontal neben die Menütaste, mit der nächstgelegenen die Menütaste PaneTitle gestapelt.

:::row:::
    :::column:::
    ![Bereich Header oben nav](images/navview-freeform-header-top.png)<br>
     _Oberen Bereich header_<br>
    :::column-end:::
    :::column:::
    ![Bereich Header linke Navigationsleiste](images/navview-freeform-header-left.png)<br>
    _Linken Bereich header_<br>
    :::column-end:::
:::row-end:::

#### <a name="pane-content"></a>Bereich Inhalt

Sie können formfreie Inhalte im Bereich platzieren, indem Sie es an die Eigenschaft [PaneCustomContent](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneCustomContent) hinzufügen.

:::row:::
    :::column:::
    ![Bereich benutzerdefinierte Inhalte oben nav](images/navview-freeform-pane-top.png)<br>
     _Benutzerdefinierte Inhalte oberen Bereich_<br>
    :::column-end:::
    :::column:::
    ![Bereich Benutzerinhalte linke Navigationsleiste](images/navview-freeform-pane-left.png)<br>
    _Linken Bereich benutzerdefiniertem Inhalt_<br>
    :::column-end:::
:::row-end:::

### <a name="header"></a>Kopfzeile

Sie können einen Seitentitel hinzufügen, indem die [Header](/uwp/api/windows.ui.xaml.controls.navigationview.header) -Eigenschaft.

![Beispiel für die Navigation Ansichtsbereich header](images/nav-header.png)<br/>
_Navigation Ansicht header_

Der Kopfzeilenbereich der Navigationsschaltfläche an der linken Seite Position vertikal ausgerichtet ist, und unterhalb des Bereichs in der oberen Bereich Position liegt. Es hat eine feste Höhe von 52 Pixel. Er dient dazu, den Seitentitel der ausgewählten Navigationskategorie aufrechtzuerhalten. Die Kopfzeile ist an den oberen Rand der Seite angedockt und dient als Scroll-Clipping-Punkt für den Inhaltsbereich.

Die Kopfzeile ist jedes Mal, wenn der NavigationView im minimierten Anzeigemodus ist sichtbar. Sie können die Kopfzeile in anderen Modi ausblenden, die bei größeren Fensterbreiten verwendet werden. Um die Kopfzeile auszublenden, die [AlwaysShowHeader](/uwp/api/windows.ui.xaml.controls.navigationview.AlwaysShowHeader) -Eigenschaft auf **"false"** festgelegt.

### <a name="content"></a>Inhalt

![Beispiel für die Navigation Ansicht Inhaltsbereich](images/nav-content.png)<br/>
_Inhalt der Navigation anzeigen_

Im Inhaltsbereich werden die meisten Informationen für die ausgewählte Navigationskategorie angezeigt.

Wir empfehlen 12px Ränder für Ihren Inhaltsbereich, wenn sich NavigationView im **minimierten** Modus befindet und 24 Ränder andernfalls.

## <a name="adaptive-behavior"></a>Adaptives Verhalten

Standardmäßig ändert die Navigationsansicht automatisch den Anzeigemodus basierend auf der Größe des Bildschirmbereichs verfügbar sind. Die [CompactModeThresholdWidth](/uwp/api/windows.ui.xaml.controls.navigationview.compactmodethresholdwidth) und [ExpandedModeThresholdWidth](/uwp/api/windows.ui.xaml.controls.navigationview.expandedmodethresholdwidth) Eigenschaften geben die Haltepunkte, an denen der Anzeigemodus ändert. Sie können diese Werte, um das adaptive anzeigemodusverhalten anpassen ändern.

### <a name="default"></a>Standard

Wenn PaneDisplayMode auf den Standardwert **Auto**festgelegt ist, ist das adaptive Verhalten anzeigen:

- Eine erweiterte linken Bereich auf großen fensterbreiten (1008 Pixel oder größer).
- Links, nur Symbol, ein Navigationsbereich (LeftCompact) bei mittelgroßen fensterbreiten (641 Pixel bis 1007 Pixel).
- Nur eine Menüschaltfläche (LeftMinimal) für kleine fensterbreiten (640 Pixel oder weniger).

Weitere Informationen zu Fenstergrößen für adaptives Verhalten finden Sie unter [Bildschirmgrößen und Breakpoints](../layout/screen-sizes-and-breakpoints-for-responsive-design.md).

![Linke Navigation standardmäßigen adaptiven Verhaltens](images/displaymode-auto.png)<br/>
_Navigation Ansicht standardmäßigen adaptiven Verhaltens_

### <a name="minimal"></a>Minimiert

Ein zweites Allgemeines adaptives Muster ist einen erweiterten linken Bereich auf großen fensterbreiten und nur eine Schaltfläche auf beiden kleinen und mittelgroßen fensterbreiten verwenden.

Wir empfehlen diese Lösung, wenn:

- Sie möchten mehr Platz für app-Inhalte auf kleinere fensterbreiten.
- Die Navigationskategorien werden nicht eindeutig mit Symbolen dargestellt.

![Minimale adaptives Verhalten linken Navigationsbereich](images/adaptive-behavior-minimal.png)<br/>
_Ansicht "minimal" adaptive Navigationsverhalten_

Um dieses Verhalten zu konfigurieren, legen Sie CompactModeThresholdWidth auf die Breite, die den Bereich zu reduzieren soll. Hier ist der Standardwert von 640, 1007 geändert. Sie sollten auch ExpandedModeThresholdWidth, um sicherzustellen, dass die Werte nicht zu Konflikten festlegen.

```xaml
<NavigationView CompactModeThresholdWidth="1007" ExpandedModeThresholdWidth="1007"/>
```

### <a name="compact"></a>Kompakt

Ein drittes Allgemeines adaptives Muster ist einen erweiterten linken Bereich auf großen fensterbreiten und eine LeftCompact, nur Symbol, Navigationsbereich auf beiden kleinen und mittelgroßen fensterbreiten verwenden.

Wir empfehlen diese Lösung, wenn:

- Es ist wichtig, immer alle Navigationsoptionen auf dem Bildschirm angezeigt werden.
- Die Navigationskategorien können deutlich mit Symbolen dargestellt werden.

![Linke Navigation compact adaptives Verhalten](images/adaptive-behavior-compact.png)<br/>
_Ansicht "compact" adaptive Navigationsverhalten_

Um dieses Verhalten zu konfigurieren, legen Sie CompactModeThresholdWidth auf 0 fest.

```xaml
<NavigationView CompactModeThresholdWidth="0"/>
```

### <a name="no-adaptive-behavior"></a>Keine adaptives Verhalten

Um die automatische adaptives Verhalten zu deaktivieren, legen Sie PaneDisplayMode auf einen anderen Wert als automatisch. Hier wird es festgelegt LeftMinimal, sodass nur die Menütaste unabhängig von der Breite des Fensters angezeigt wird.

![Linke Navigationsleiste keine adaptives Verhalten](images/adaptive-behavior-none.png)<br/>
_Navigationsansicht mit PaneDisplayMode LeftMinimal festgelegt_

```xaml
<NavigationView PaneDisplayMode="LeftMinimal" />
```

Wie zuvor im Abschnitt _Anzeigemodi_ beschrieben, können Sie den Bereich werden immer am oberen, immer vergrößert, immer compact oder immer minimale festlegen. Sie können auch die Anzeigemodi selbst im app-Code verwalten. Ein Beispiel hierfür wird im nächsten Abschnitt angezeigt.

### <a name="top-to-left-navigation"></a>Oberen, linken Navigationsbereich

Wenn Sie oberen Navigationsleiste in Ihrer app verwenden, reduzieren Navigationselemente in ein Überlaufmenü das Fenster Breite sich verringert. Wenn Ihre app-Fenster schmaler ist, können sie ein besseres Benutzererlebnis, um die PaneDisplayMode von oben LeftMinimal Navigation, statt alles, was die Elemente in das Überlaufmenü reduzieren Hinweisen zu wechseln bereitstellen.

Wir empfehlen die Verwendung der oberen Navigationsleiste auf großen Fenstergrößen und linken Navigationsbereich auf kleinen Fenster Größe bei:

- Sie haben eine Reihe von gleichermaßen wichtig Navigation auf oberster Ebene Kategorien zusammen angezeigt werden, wenn eine Kategorie in diesen nicht auf dem Bildschirm passt, die linke Navigation, damit sie genauso wichtig wie erhalten Sie reduzieren.
- Möchten Sie so viel Inhalt Speicherplatz wie möglich in kleinen Fenstergrößen beibehalten.

Dieses Beispiel zeigt, wie Sie eine Eigenschaft [VisualStateManager](/uwp/api/Windows.UI.Xaml.VisualStateManager) und [AdaptiveTrigger.MinWindowWidth](/uwp/api/windows.ui.xaml.adaptivetrigger.minwindowwidth) verwenden, um zwischen den oberen und LeftMinimal Navigation wechseln.

![Beispiel für oberen oder linken adaptives Verhalten 1](images/navigation-top-to-left.png)

```xaml
<Grid >
    <NavigationView x:Name="NavigationViewControl" >
        <NavigationView.MenuItems>
            <NavigationViewItem Content="A" x:Name="A" />
            <NavigationViewItem Content="B" x:Name="B" />
            <NavigationViewItem Content="C" x:Name="C" />
        </NavigationView.MenuItems>
    </NavigationView>

    <VisualStateManager.VisualStateGroups>
        <VisualStateGroup>
            <VisualState>
                <VisualState.StateTriggers>
                    <AdaptiveTrigger
                        MinWindowWidth="{x:Bind NavigationViewControl.CompactModeThresholdWidth}" />
                </VisualState.StateTriggers>

                <VisualState.Setters>
                    <Setter Target="NavigationViewControl.PaneDisplayMode" Value="Top"/>
                </VisualState.Setters>
            </VisualState>
        </VisualStateGroup>
    </VisualStateManager.VisualStateGroups>
</Grid>

```

> [!TIP]
> Wenn Sie AdaptiveTrigger.MinWindowWidth verwenden, wird der visuelle Zustand ausgelöst, wenn das Fenster breiter als die angegebene minimale Breite ist. Dies bedeutet, dass die standardmäßigen XAML-Code definiert das schmale Fenster, und die VisualState Änderungen, die angewendet werden, wenn das Fenster vergrößert wird. Die standardmäßige PaneDisplayMode Navigationsansicht Auto ist, sodass, wenn die Fensterbreite kleiner oder gleich CompactModeThresholdWidth ist, LeftMinimal Navigation verwendet wird. Wenn das Fenster vergrößert wird, die VisualState überschreibt die standardmäßige und oberen Navigationsleiste dient.

## <a name="navigation"></a>Navigation

Die Navigationsansicht ausführen nicht automatisch alle Navigationsaufgaben. Wenn der Benutzer auf ein Navigationselement tippt, wird die Navigationsansicht zeigt dieses Element als ausgewählt und löst ein [ItemInvoked](/uwp/api/windows.ui.xaml.controls.navigationview.ItemInvoked) -Ereignis. Wenn das Tippen ein neues Element ausgewählt wird, wird ein [SelectionChanged](/uwp/api/windows.ui.xaml.controls.navigationview.SelectionChanged) -Ereignis auch ausgelöst.

Sie können entweder-Ereignis, um Aufgaben im Zusammenhang mit der gewünschten Navigation behandeln. Sie behandeln soll, hängt das Verhalten, die, das Sie für Ihre app verwenden möchten. In der Regel für die angeforderte Seite navigieren und Navigation Ansicht Header in Reaktion auf diese Ereignisse zu aktualisieren.

**ItemInvoked** wird jedes Mal, die der Benutzer auf ein Navigationselement tippt ausgelöst, auch wenn es bereits aktiviert ist. (Das Element kann auch mit einer entsprechenden Aktion, die mit der Maus, Tastatur oder andere Eingabetypen aufgerufen werden. Weitere Informationen finden Sie unter [Eingabe und Interaktionen](../input/index.md).) Wenn Sie in der ItemInvoked-Ereignishandler navigieren, wird standardmäßig die Seite wird neu geladen werden, und ein doppelter Eintrag ist Navigationsstapel hinzugefügt. Wenn Sie navigieren, wenn ein Element aufgerufen wird, sollten Sie verbieten Neuladen der Seite oder stellen Sie sicher, dass dieser Eintrag nicht in der navigationsbackstack erstellt wird, wenn die Seite neu geladen wird. (Siehe Codebeispiele.)

**SelectionChanged** kann von einem Benutzer Aufrufen eines Elements, das derzeit ausgewählte ist oder das ausgewählte Element programmgesteuert ändern ausgelöst werden. Wenn die Änderung der Auswahl tritt auf, da ein Benutzer ein Element aufgerufen wird, tritt das ItemInvoked-Ereignis zuerst. Wenn die Änderung der Auswahl programmgesteuerten ist, wird die ItemInvoked nicht ausgelöst.

### <a name="backwards-navigation"></a>Rückwärtsnavigation

NavigationView verfügt über eine integrierte Schaltfläche "zurück". wie bei Vorwärtsnavigation, sie jedoch nicht ausführen, rückwärts Navigation automatisch. Wenn der Benutzer die zurück-Schaltfläche tippt, wird das [BackRequested](/uwp/api/windows.ui.xaml.controls.navigationview.BackRequested) -Ereignis ausgelöst. Sie behandeln dieses Ereignis, um rückwärts Navigation durchgeführt. Weitere Informationen und Codebeispiele finden Sie unter [Navigationsverlauf und Rückwärtsnavigation Navigation](../basics/navigation-history-and-backwards-navigation.md).

Im minimalen oder kompakten Modus ist als Flyout geöffnet die Navigationsansicht Bereich. In diesem Fall wird die zurück-Schaltfläche klicken Schließen des Bereichs und stattdessen das **PaneClosing** -Ereignis auslösen.

Sie können ausblenden oder deaktivieren die zurück-Schaltfläche durch Festlegen dieser Eigenschaften:

- [IsBackButtonVisible](/uwp/api/windows.ui.xaml.controls.navigationview.IsBackButtonVisible): Verwenden Sie zum ein- und Ausblenden der Schaltfläche "zurück". Diese Eigenschaft akzeptiert einen Wert von der [NavigationViewBackButtonVisible](/uwp/api/windows.ui.xaml.controls.navigationviewbackbuttonvisible) -Enumeration und standardmäßig auf **Auto** festgelegt ist. Wenn die Schaltfläche "Collapsed" ist, wird keine Leerzeichen im Layout dafür reserviert.
- [IsBackEnabled](/uwp/api/windows.ui.xaml.controls.navigationview.IsBackEnabled): Verwenden Sie zum Aktivieren oder deaktivieren die Schaltfläche "zurück". Diese Eigenschaft der Eigenschaft [CanGoBack](/uwp/api/windows.ui.xaml.controls.frame.cangoback) Ihrer Navigations-Frame können Sie Daten gebunden werden. **BackRequested** wird nicht ausgelöst, wenn **IsBackEnabled** auf **"false"** festgelegt ist.

:::row:::
    :::column:::
        ![Navigation view back button in the left navigation pane](images/leftnav-back.png)<br/>
        _The back button in the left navigation pane_
    :::column-end:::
    :::column:::
        ![Navigation view back button in the top navigation pane](images/topnav-back.png)<br/>
        _The back button in the top navigation pane_
    :::column-end:::
:::row-end:::

## <a name="code-example"></a>Codebeispiel

Dieses Beispiel zeigt, wie Sie NavigationView mit einem oberen Navigationsbereich auf großen Fenstergrößen und einem linken Navigationsbereich auf kleinen Fenstergrößen verwenden können. Es kann an Navigation mit Links angepasst werden, indem Sie die _oberen_ Navigationsbereich Einstellungen im VisualStateManager entfernen.

Das Beispiel zeigt eine empfohlene Vorgehensweise zur Navigation richten, das für viele häufige Szenarien geeignet ist. Es wird veranschaulicht, wie die Rückwärtsnavigation mit der zurück-Schaltfläche und Tastatur-Navigation NavigationView implementiert wird.

Dieser Code wird davon ausgegangen, dass die app Seiten mit den folgenden Namen zu navigieren enthält: _HomePage_, _AppsPage_, _GamesPage_, _MusicPage_, _MyContentPage_und _DruckerÄndernDruckereinstellungenSeite_. Code für diese Seiten wird nicht angezeigt.

> [!IMPORTANT]
> Informationen zu app Seiten wird in einem [ValueTuple](https://docs.microsoft.com/dotnet/api/system.valuetuple)gespeichert. Diese Struktur erfordert, dass die Mindestversion für Ihre app-Projekt SDK 17763 oder größer sein muss. Wenn Sie die WinUI Version von NavigationView für frühere Versionen von Windows 10 verwenden, können Sie stattdessen das [System.ValueTuple NuGet-Paket](https://www.nuget.org/packages/System.ValueTuple/) .

> [!IMPORTANT]
> Dieser Code zeigt, wie Sie die [UI-Bibliothek für Windows](https://docs.microsoft.com/uwp/toolkits/winui/) -Version von NavigationView verwenden. Wenn Sie stattdessen die Plattformversion von NavigationView verwenden, muss die Mindestversion für Ihre app-Projekt SDK 17763 oder höher sein. Um die Plattformversion verwenden möchten, entfernen Sie alle Verweise auf `muxc:`.

```xaml
<!-- xmlns:muxc="using:Microsoft.UI.Xaml.Controls" -->
<Grid>
    <muxc:NavigationView x:Name="NavView"
                         Loaded="NavView_Loaded"
                         ItemInvoked="NavView_ItemInvoked"
                         BackRequested="NavView_BackRequested">
        <muxc:NavigationView.MenuItems>
            <muxc:NavigationViewItem Tag="home" Icon="Home" Content="Home"/>
            <muxc:NavigationViewItemSeparator/>
            <muxc:NavigationViewItemHeader x:Name="MainPagesHeader"
                                           Content="Main pages"/>
            <muxc:NavigationViewItem Tag="apps" Content="Apps">
                <muxc:NavigationViewItem.Icon>
                    <FontIcon FontFamily="Segoe MDL2 Assets" Glyph="&#xEB3C;"/>
                </muxc:NavigationViewItem.Icon>
            </muxc:NavigationViewItem>
            <muxc:NavigationViewItem Tag="games" Content="Games">
                <muxc:NavigationViewItem.Icon>
                    <FontIcon FontFamily="Segoe MDL2 Assets" Glyph="&#xE7FC;"/>
                </muxc:NavigationViewItem.Icon>
            </muxc:NavigationViewItem>
            <muxc:NavigationViewItem Tag="music" Icon="Audio" Content="Music"/>
        </muxc:NavigationView.MenuItems>

        <muxc:NavigationView.AutoSuggestBox>
            <!-- See AutoSuggestBox documentation for
                 more info about how to implement search. -->
            <AutoSuggestBox x:Name="NavViewSearchBox" QueryIcon="Find"/>
        </muxc:NavigationView.AutoSuggestBox>

        <ScrollViewer>
            <Frame x:Name="ContentFrame" Padding="12,0,12,24" IsTabStop="True"
                   NavigationFailed="ContentFrame_NavigationFailed"/>
        </ScrollViewer>
    </muxc:NavigationView>

    <VisualStateManager.VisualStateGroups>
        <VisualStateGroup>
            <VisualState>
                <VisualState.StateTriggers>
                    <AdaptiveTrigger
                        MinWindowWidth="{x:Bind NavView.CompactModeThresholdWidth}"/>
                </VisualState.StateTriggers>
                <VisualState.Setters>
                    <!-- Remove the next 3 lines for left-only navigation. -->
                    <Setter Target="NavView.PaneDisplayMode" Value="Top"/>
                    <Setter Target="NavViewSearchBox.Width" Value="200"/>
                    <Setter Target="MainPagesHeader.Visibility" Value="Collapsed"/>
                    <!-- Leave the next line for left-only navigation. -->
                    <Setter Target="ContentFrame.Padding" Value="24,0,24,24"/>
                </VisualState.Setters>
            </VisualState>
        </VisualStateGroup>
    </VisualStateManager.VisualStateGroups>
</Grid>
```

> [!IMPORTANT]
> Dieser Code zeigt, wie Sie die [UI-Bibliothek für Windows](https://docs.microsoft.com/uwp/toolkits/winui/) -Version von NavigationView verwenden. Wenn Sie stattdessen die Plattformversion von NavigationView verwenden, muss die Mindestversion für Ihre app-Projekt SDK 17763 oder höher sein. Um die Plattformversion verwenden möchten, entfernen Sie alle Verweise auf `muxc`.

```csharp
// Add "using" for WinUI controls.
// using muxc = Microsoft.UI.Xaml.Controls;

private void ContentFrame_NavigationFailed(object sender, NavigationFailedEventArgs e)
{
    throw new Exception("Failed to load Page " + e.SourcePageType.FullName);
}

// List of ValueTuple holding the Navigation Tag and the relative Navigation Page
private readonly List<(string Tag, Type Page)> _pages = new List<(string Tag, Type Page)>
{
    ("home", typeof(HomePage)),
    ("apps", typeof(AppsPage)),
    ("games", typeof(GamesPage)),
    ("music", typeof(MusicPage)),
};

private void NavView_Loaded(object sender, RoutedEventArgs e)
{
    // You can also add items in code.
    NavView.MenuItems.Add(new muxc.NavigationViewItemSeparator());
    NavView.MenuItems.Add(new muxc.NavigationViewItem
    {
        Content = "My content",
        Icon = new SymbolIcon((Symbol)0xF1AD),
        Tag = "content"
    });
    _pages.Add(("content", typeof(MyContentPage)));

    // Add handler for ContentFrame navigation.
    ContentFrame.Navigated += On_Navigated;

    // NavView doesn't load any page by default, so load home page.
    NavView.SelectedItem = NavView.MenuItems[0];
    // If navigation occurs on SelectionChanged, this isn't needed.
    // Because we use ItemInvoked to navigate, we need to call Navigate
    // here to load the home page.
    NavView_Navigate("home", new EntranceNavigationTransitionInfo());

    // Add keyboard accelerators for backwards navigation.
    var goBack = new KeyboardAccelerator { Key = VirtualKey.GoBack };
    goBack.Invoked += BackInvoked;
    this.KeyboardAccelerators.Add(goBack);

    // ALT routes here
    var altLeft = new KeyboardAccelerator
    {
        Key = VirtualKey.Left,
        Modifiers = VirtualKeyModifiers.Menu
    };
    altLeft.Invoked += BackInvoked;
    this.KeyboardAccelerators.Add(altLeft);
}

private void NavView_ItemInvoked(muxc.NavigationView sender,
                                 muxc.NavigationViewItemInvokedEventArgs args)
{
    if (args.IsSettingsInvoked == true)
    {
        NavView_Navigate("settings", args.RecommendedNavigationTransitionInfo);
    }
    else if (args.InvokedItemContainer != null)
    {
        var navItemTag = args.InvokedItemContainer.Tag.ToString();
        NavView_Navigate(navItemTag, args.RecommendedNavigationTransitionInfo);
    }
}

<!-- NavView_SelectionChanged is not used in this example, but is shown for completeness.
     You will typically handle either ItemInvoked or SelectionChanged to perform navigation,
     but not both. -->
private void NavView_SelectionChanged(muxc.NavigationView sender,
                                      muxc.NavigationViewSelectionChangedEventArgs args)
{
    if (args.IsSettingsSelected == true)
    {
        NavView_Navigate("settings", args.RecommendedNavigationTransitionInfo);
    }
    else if (args.SelectedItemContainer != null)
    {
        var navItemTag = args.SelectedItemContainer.Tag.ToString();
        NavView_Navigate(navItemTag, args.RecommendedNavigationTransitionInfo);
    }
}

private void NavView_Navigate(string navItemTag, NavigationTransitionInfo transitionInfo)
{
    Type _page = null;
    if (navItemTag == "settings")
    {
        _page = typeof(SettingsPage);
    }
    else
    {
        var item = _pages.FirstOrDefault(p => p.Tag.Equals(navItemTag));
        _page = item.Page;
    }
    // Get the page type before navigation so you can prevent duplicate
    // entries in the backstack.
    var preNavPageType = ContentFrame.CurrentSourcePageType;

    // Only navigate if the selected page isn't currently loaded.
    if (!(_page is null) && !Type.Equals(preNavPageType, _page))
    {
        ContentFrame.Navigate(_page, null, transitionInfo);
    }
}

private void NavView_BackRequested(muxc.NavigationView sender,
                                   muxc.NavigationViewBackRequestedEventArgs args)
{
    On_BackRequested();
}

private void BackInvoked(KeyboardAccelerator sender,
                         KeyboardAcceleratorInvokedEventArgs args)
{
    On_BackRequested();
    args.Handled = true;
}

private bool On_BackRequested()
{
    if (!ContentFrame.CanGoBack)
        return false;

    // Don't go back if the nav pane is overlayed.
    if (NavView.IsPaneOpen &&
        (NavView.DisplayMode == muxc.NavigationViewDisplayMode.Compact ||
         NavView.DisplayMode == muxc.NavigationViewDisplayMode.Minimal))
        return false;

    ContentFrame.GoBack();
    return true;
}

private void On_Navigated(object sender, NavigationEventArgs e)
{
    NavView.IsBackEnabled = ContentFrame.CanGoBack;

    if (ContentFrame.SourcePageType == typeof(SettingsPage))
    {
        // SettingsItem is not part of NavView.MenuItems, and doesn't have a Tag.
        NavView.SelectedItem = (muxc.NavigationViewItem)NavView.SettingsItem;
        NavView.Header = "Settings";
    }
    else if (ContentFrame.SourcePageType != null)
    {
        var item = _pages.FirstOrDefault(p => p.Page == e.SourcePageType);

        NavView.SelectedItem = NavView.MenuItems
            .OfType<muxc.NavigationViewItem>()
            .First(n => n.Tag.Equals(item.Tag));

        NavView.Header =
            ((muxc.NavigationViewItem)NavView.SelectedItem)?.Content?.ToString();
    }
}
```

## <a name="navigation-view-customization"></a>Anpassung der Navigation-Ansicht

### <a name="pane-backgrounds"></a>Bereichshintergründe

Standardmäßig verwendet der NavigationView-Bereich einen anderen Hintergrund abhängig vom Anzeigemodus:

- der Bereich ist eine graue Volltonfarbe wird auf der linken Seite, Side-by-Side mit dem Inhalt (im linken Modus) erweitert.
- im Bereich wird in-app-Acryl geöffneten als Overlay Inhalt (im oberen, minimalen oder kompakten Modus).

Um den Hintergrund des Bereichs zu ändern, können Sie die XAML-Designressourcen verwendet, um den Hintergrund in jedem Modus Rendern überschreiben. (Diese Technik ist anstatt eine einzelne PaneBackground Eigenschaft verwendet um die verschiedene Hintergründen für unterschiedliche Anzeigemodi unterstützen.)

Diese Tabelle zeigt, welche Designressource in jeder Anzeigemodus verwendet wird.

| Anzeigemodus | Designressource |
| ------------ | -------------- |
| Links | NavigationViewExpandedPaneBackground |
| LeftCompact<br/>LeftMinimal | NavigationViewDefaultPaneBackground |
| Oben | NavigationViewTopPaneBackground |

Dieses Beispiel zeigt, wie die Designressourcen in "App.xaml" außer Kraft gesetzt wird. Wenn Sie Designressourcen überschreiben, sollten Sie immer "Default" und "HighContrast" Ressourcenwörterbücher mindestens und Wörterbücher für "Light" oder "Dark" Ressourcen bereitstellen nach Bedarf. Weitere Informationen finden Sie unter [ResourceDictionary.ThemeDictionaries](/uwp/api/windows.ui.xaml.resourcedictionary.themedictionaries).

> [!IMPORTANT]
> Dieser Code zeigt, wie Sie die [UI-Bibliothek für Windows](https://docs.microsoft.com/uwp/toolkits/winui/) -Version des AcrylicBrush zu verwenden. Wenn Sie stattdessen die Plattformversion des AcrylicBrush verwenden, muss die Mindestversion für Ihre app-Projekt SDK 16299 oder höher sein. Um die Plattformversion verwenden möchten, entfernen Sie alle Verweise auf `muxm:`.

```xaml
<Application
    <!-- ... -->
    xmlns:muxm="using:Microsoft.UI.Xaml.Media">
    <Application.Resources>
        <ResourceDictionary>
            <ResourceDictionary.MergedDictionaries>
                <XamlControlsResources xmlns="using:Microsoft.UI.Xaml.Controls"/>
                <ResourceDictionary>
                    <ResourceDictionary.ThemeDictionaries>
                        <ResourceDictionary x:Key="Default">
                            <!-- The "Default" theme dictionary is used unless a specific
                                 light, dark, or high contrast dictionary is provided. These
                                 resources should be tested with both the light and dark themes,
                                 and specific light or dark resources provided as needed. -->
                            <muxm:AcrylicBrush x:Key="NavigationViewDefaultPaneBackground"
                                   BackgroundSource="Backdrop"
                                   TintColor="LightSlateGray"
                                   TintOpacity=".6"/>
                            <muxm:AcrylicBrush x:Key="NavigationViewTopPaneBackground"
                                   BackgroundSource="Backdrop"
                                   TintColor="{ThemeResource SystemAccentColor}"
                                   TintOpacity=".6"/>
                            <LinearGradientBrush x:Key="NavigationViewExpandedPaneBackground"
                                     StartPoint="0.5,0" EndPoint="0.5,1">
                                <GradientStop Color="LightSlateGray" Offset="0.0" />
                                <GradientStop Color="White" Offset="1.0" />
                            </LinearGradientBrush>
                        </ResourceDictionary>
                        <ResourceDictionary x:Key="HighContrast">
                            <!-- Always include a "HighContrast" dictionary when you override
                                 theme resources. This empty dictionary ensures that the 
                                 default high contrast resources are used when the user
                                 turns on high contrast mode. -->
                        </ResourceDictionary>
                    </ResourceDictionary.ThemeDictionaries>
                </ResourceDictionary>
            </ResourceDictionary.MergedDictionaries>
        </ResourceDictionary>
    </Application.Resources>
</Application>
```

## <a name="related-topics"></a>Verwandte Themen

- [NavigationView-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview)
- [Master/Details](master-details.md)
- [Navigationsgrundlagen](../basics/navigation-basics.md)
- [Übersicht über Fluent Design für UWP](../fluent-design-system/index.md)
