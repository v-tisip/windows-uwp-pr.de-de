---
author: serenaz
Description: NavigationView is an adaptive control that implements top-level navigation patterns for your app.
title: Navigationsansicht
template: detail.hbs
ms.author: sezhen
ms.date: 08/06/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
pm-contact: yulikl
design-contact: kimsea
dev-contact: ''
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 4c0857005d584b1fde0eb52a6ab0ef5ec29eaf44
ms.sourcegitcommit: 9c79fdab9039ff592edf7984732d300a14e81d92
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2018
ms.locfileid: "2810910"
---
# <a name="navigation-view-preview-version"></a>Navigationsansicht (Vorabversion)

> **Dies ist eine Vorabversion**: in diesem Artikel wird eine neue Version des NavigationView-Steuerelements, das noch in der Entwicklung ist. Für dessen Verwendung benötigen nun die [aktuellsten Windows-Insider Build und SDK](https://insider.windows.com/for-developers/) oder der [Bibliothek für Windows-Benutzeroberfläche](https://docs.microsoft.com/uwp/toolkits/winui/).

Das Steuerelement NavigationView bietet Navigation für Ihre app auf oberster Ebene. Es wird an eine Vielzahl von Bildschirm Größen unterstützt mehrere Navigation Formatvorlagen.

> **Windows-UI-Bibliothek-APIs**: [Microsoft.UI.Xaml.Controls.NavigationView-Klasse](/uwp/api/microsoft.ui.xaml.controls.navigationview)

> **Plattform-APIs**: [Windows.UI.Xaml.Controls.NavigationView-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview)

## <a name="get-the-windows-ui-library"></a>Abrufen der Windows-UI-Bibliothek

Dieses Steuerelement ist Bestandteil der Windows-UI-Bibliothek, ein NuGet-Paket, das neue Steuerelemente und Features der Benutzeroberfläche für apps UWP enthält. Weitere Informationen, einschließlich Installationshinweise finden Sie unter [Übersicht über die Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/). 

## <a name="navigation-styles"></a>Navigation Formatvorlagen

NavigationView werden unterstützt:

**Im linken Navigationsbereich oder im Menü**

![Navigationsbereich erweitert](images/displaymode-left.png)

**Im oberen Navigationsbereich oder im Menü**

![der oberen Navigationsleiste](images/displaymode-top.png)

## <a name="is-this-the-right-control"></a>Ist dies das richtige Steuerelement?

NavigationView ist eine adaptive Navigationssteuerelement, die für gut funktioniert:

- Bereitstellen einer konsistenten Navigationsfunktionen für in der gesamten Ihrer app.
- Bildschirm Immobilien kleinere Windows beibehalten.
- Zugriff auf viele Navigationskategorien organisieren.

Andere Navigationssteuerelemente finden Sie unter [Grundlagen der Navigation Entwurf](../basics/navigation-basics.md).

Wenn die Navigation komplexeres Verhalten erfordert, das von NavigationView nicht unterstützt wird, können Sie stattdessen das [Master/Details](master-details.md)-Muster verwenden.

:::row:::
    :::column:::
        ![Einige Bild](images/XAML-controls-gallery-app-icon.png)
    :::column-end:::
    ::: Spaltenbreite = "2"::: **XAML-Steuerelemente-Sammlung**<br>
        Wenn Sie die Verwendung von XAML-Steuerelemente-Sammlung app installiert haben, klicken Sie auf <a href="xamlcontrolsgallery:/item/NavigationView">hier</a> öffnen Sie die app und finden Sie unter NavigationView in Aktion.

        <a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT">Get the XAML Controls Gallery app (Microsoft Store)</a><br>
        <a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics">Get the source code (GitHub)</a>
    :::column-end:::
:::row-end:::

## <a name="display-modes"></a>Anzeigemodi

NavigationView verschiedenen Anzeigemodi festgelegt werden kann, über die `PaneDisplayMode` Eigenschaft:

:::row:::
    :::column:::
    ### Left
    Displays an expanded left positioned pane.
    :::column-end:::
    :::column span="2":::
    ![left nav pane expanded](images/displaymode-left.png)
    :::column-end:::
:::row-end:::

Wir empfehlen linken Navigationsbereich wenn:

- Sie haben eine mittlere bis hohe Anzahl (5-10) gleichermaßen wichtig Navigation auf oberster Ebene Kategorien.
- Sie wünschen sich sehr wichtigsten Navigationskategorien mit weniger Speicherplatz für andere app-Inhalte.

:::row:::
    :::column:::
    ### Top
    Displays a top positioned pane.
    :::column-end:::
    :::column span="2":::
    ![top navigation](images/displaymode-top.png)
    :::column-end:::
:::row-end:::

Wir empfehlen, dass der oberen Navigationsleiste wenn:

- Sie haben 5 oder weniger Kategorien gleichermaßen wichtig Navigation auf oberster Ebene, sodass zusätzliche Navigation auf oberster Ebene Kategorien, die in der Dropdownliste landen Überlauf im Menü gelten als weniger wichtig.
- Sie müssen alle Navigationsoptionen auf Bildschirm anzeigen.
- Sie wünschen mehr Platz für Ihre app-Inhalte.
- Symbole können nicht eindeutig Ihrer app Navigationskategorien beschreiben.

:::row:::
    :::column:::
    ### LeftCompact
    Displays a thin sliver with icons on the left.
    :::column-end:::
    :::column span="2":::
    ![nav pane compact](images/displaymode-leftcompact.png)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
    ### LeftMinimal
    Displays only the menu button.
    :::column-end:::
    :::column span="2":::
    ![nav pane minimal](images/displaymode-leftminimal.png)
    :::column-end:::
:::row-end:::

### <a name="auto"></a>Auto

![GIF Leftnav adaptive Standardverhalten](images/displaymode-auto.png)

Passt zwischen LeftMinimal auf kleinen Bildschirmen, LeftCompact auf mittlere Bildschirmen und Links auf großen Bildschirmen. Finden Sie weitere Informationen im Abschnitt [adaptive Verhalten](#adaptive-behavior) .

## <a name="anatomy"></a>Aufbau

<b>Linke Navigationsleiste</b><br>

![linken NavigationView Abschnitte](images/leftnav-anatomy.png)

<b>Oben nav</b><br>

![Top-NavigationView Abschnitte](images/topnav-anatomy.png)

## <a name="pane"></a>Bereich

Im Bereich kann positioniert werden im Vordergrund oder auf der linken Seite, über die `PanePosition` Eigenschaft.

Hier wird die detaillierte Bereich Aufbau für die linken und oberen Bereich Positionen:

<b>Linke Navigationsleiste</b><br>

![NavigationView Aufbau](images/navview-pane-anatomy-vertical.png)

1. Menü-Taste
1. Navigationselemente
1. Trennzeichen
1. Header
1. AutoSuggestBox (optional)
1. Schaltfläche "Einstellungen" (optional)

<b>Oben nav</b><br>

![NavigationView Aufbau](images/navview-pane-anatomy-horizontal.png)

1. Header
1. Navigationselemente
1. Trennzeichen
1. AutoSuggestBox (optional)
1. Schaltfläche "Einstellungen" (optional)

Die zurück-Schaltfläche wird angezeigt, in der oberen linken Ecke des Bereichs, aber NavigationView werden Inhalte nicht automatisch auf den Back-Stapel hinzugefügt. Für die Abwärtskompatibilität Navigation, finden Sie unter der [Rückwärts Navigation](#backwards-navigation) Abschnitt.

Auch kann im Bereich NavigationView enthalten:

1. Navigationselemente in Form von [NavigationViewItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitem), für die Navigation zu bestimmten Seiten.
2. Trennlinien, in Form von [NavigationViewItemSeparator](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitemseparator), zum Gruppieren von Navigationselemente. Legen Sie die [Durchlässigkeit](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitemseparator.opacity) -Eigenschaft auf 0, um das Trennzeichen als Speicherplatz zu rendern.
3. Kopfzeilen in Form von [NavigationViewItemHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitemheader), zum Beschriften Gruppen von Elementen.
4. Eine optionale [AutoSuggestBox](auto-suggest-box.md) app-Level Search zulässt.
5. Ein optionaler Einstiegspunkt für [App-Einstellungen](../app-settings/app-settings-and-data.md). Wenn das Element Settings ausblenden möchten, verwenden Sie die [IsSettingsVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsSettingsVisible) -Eigenschaft.

Der linke Bereich enthält:

6. Menüschaltfläche, um den Bereich öffnen und schließen zu wechseln. Sie können bei größeren App-Fenstern mit geöffnetem Bereich diese Schaltfläche mit der Eigenschaft [IsPaneToggleButtonVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsPaneToggleButtonVisible) ausblenden.

### <a name="pane-footer"></a>Bereich-Fußzeile

Freier Inhalt in der Fußzeile des Bereichs beim Hinzufügen zur [PaneFooter](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneFooter)-Eigenschaft

:::row:::
    :::column:::
    <b>Linke Navigationsleiste</b><br>
    ![Bereich Fußzeile linke Navigationsleiste](images/navview-freeform-footer-left.png)<br>
    :::column-end:::
    :::column:::
     <b>Oben nav</b><br>
    ![Bereich Kopfzeile oben nav](images/navview-freeform-footer-top.png)<br>
    :::column-end:::
:::row-end:::

### <a name="pane-header"></a>Header des Bereichs

Formfreies Inhalte in den Bereich Kopfzeile, wenn die Eigenschaft [PaneHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneHeader) hinzugefügt

:::row:::
    :::column:::
    <b>Linke Navigationsleiste</b><br>
    ![Bereich Kopfzeile linke Navigationsleiste](images/navview-freeform-header-left.png)<br>
    :::column-end:::
    :::column:::
     <b>Oben nav</b><br>
    ![Bereich Kopfzeile oben nav](images/navview-freeform-header-top.png)<br>
    :::column-end:::
:::row-end:::

### <a name="pane-content"></a>Bereich Inhalt

Formfreies Inhalte im Bereich, wenn die Eigenschaft [PaneCustomContent](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneCustomContent) hinzugefügt

:::row:::
    :::column:::
    <b>Linke Navigationsleiste</b><br>
    ![Im Bereich benutzerdefinierte Contentleft nav](images/navview-freeform-pane-left.png)<br>
    :::column-end:::
    :::column:::
     <b>Oben nav</b><br>
    ![Im Bereich benutzerdefinierte Content oben nav](images/navview-freeform-pane-top.png)<br>
    :::column-end:::
:::row-end:::

### <a name="visual-style"></a>Visueller Stil

Wenn Hardware-und softwareanforderungen erfüllt sind, verwendet NavigationView automatisch dem [Acryl Material](../style/acrylic.md) in den Bereich und nur in den linken Bereich [Hervorhebung anzuzeigen](../style/reveal.md) .

## <a name="header"></a>Kopfzeile

![Navview generische Bild des Kopfbereich](images/nav-header.png)

Im Kopfbereich die Navigationsschaltfläche an der Position des linken Bereich vertikal ausgerichtet ist, und unterhalb des Bereichs in die Position des oberen Bereich liegt. Es wurde eine feste Höhe von 52 px. Er dient dazu, den Seitentitel der ausgewählten Navigationskategorie aufrechtzuerhalten. Die Kopfzeile ist an den oberen Rand der Seite angedockt und dient als Scroll-Clipping-Punkt für den Inhaltsbereich.

Die Kopfzeile muss sichtbar sein, wenn NavigationView in der minimale Anzeigemodus befindet. Sie können die Kopfzeile in anderen Modi ausblenden, die bei größeren Fensterbreiten verwendet werden. Legen Sie dazu die Eigenschaft [AlwaysShowHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.AlwaysShowHeader) auf **false** fest.

## <a name="content"></a>Inhalt

![Navview generische Bild des Inhaltsbereich](images/nav-content.png)

Im Inhaltsbereich werden die meisten Informationen für die ausgewählte Navigationskategorie angezeigt.

Wir empfehlen, Ränder für Ihren Inhaltsbereich auf 12Pixel festzulegen, wenn sich NavigationView im minimierten Modus befindet. Verwenden Sie andernfalls 24Pixel.

## <a name="adaptive-behavior"></a>Adaptives Verhalten

NavigationView ändert je nach verfügbarem Platz auf dem Bildschirm automatisch den Anzeigemodus. Sie möchten jedoch das Verhalten adaptive Modus anpassen.

### <a name="default"></a>Standard

Das adaptive Standardverhalten von NavigationView ist eine erweiterte linken Bereich auf große Fenster Breiten, eine linke nur Symbol-Navigationsleiste Bereich auf mittlere Fenster Breiten und eine Menüschaltfläche Hamburger auf kleinen Fenster Breite angezeigt. Weitere Informationen zu Fenstergrößen für adaptive Verhalten finden Sie unter [Bildschirmgrößen und Haltepunkte](../layout/screen-sizes-and-breakpoints-for-responsive-design.md).

![GIF Leftnav adaptive Standardverhalten](images/displaymode-auto.png)

```xaml
<NavigationView />
```

### <a name="minimal"></a>Minimiert

Ein zweites allgemeine adaptives Muster ist die Verwendung einen erweiterten linken Bereich auf große Fenster Breiten und ein Hamburger Menü auf beide Breiten mittleren und kleinen Fenster.

![GIF Leftnav adaptive Verhalten 2](images/adaptive-behavior-minimal.png)

```xaml
<NavigationView CompactModeThresholdWidth="1008" ExpandedModeThresholdWidth="1007" />
```

Es wird empfohlen, diese Lösung, wenn:

- Sie wünschen sich mehr Platz für app-Inhalten auf kleineren Fenster breiten.
- Ihre Navigationskategorien werden nicht eindeutig mit Symbolen dargestellt.

### <a name="compact"></a>Kompakt

Ein drittes Allgemeines adaptives Muster ist die Verwendung einen erweiterten linken Bereich auf große Fenster Breiten und eine linke nur Symbol-Navigationsleiste Bereich auf beide Breiten mittleren und kleinen Fenster. Gutes Beispiel hierfür ist die Mail-app.

![GIF Leftnav adaptive Verhalten 3](images/adaptive-behavior-compact.png)

```xaml
<NavigationView CompactModeThresholdWidth="0" ExpandedModeThresholdWidth="1007" />
```

Es wird empfohlen, diese Lösung, wenn:

- Es ist wichtig, alle Navigationsoptionen auf Bildschirm immer anzeigen.
- Ihre Navigationskategorien können deutlich mit Symbolen dargestellt werden.

### <a name="no-adaptive-behavior"></a>Kein adaptive Verhalten

Manchmal kann eine beliebige adaptive Verhalten nicht in allen wünschen. Sie können den Bereich erweitert, immer compact oder immer minimale immer ist festlegen.

![GIF Leftnav adaptive Verhalten 4](images/adaptive-behavior-none.png)

```xaml
<NavigationView PaneDisplayMode="LeftMinimal" />
```

### <a name="top-to-left-navigation"></a>Oben links

Wir empfehlen die Verwendung der oberen Navigationsleiste auf große Fenstergrößen und linken Navigationsbereich auf kleinen Fenster passt, wenn:

- Sie haben eine Reihe von gleichermaßen wichtig Navigation auf oberster Ebene Kategorien zusammen angezeigt werden, wenn eine Kategorie in den folgenden Bildschirm passt, zum linken Navigationsbereich gleich Wichtigkeit geben Sie reduzieren.
- Wie viel Inhalt Speicherplatz wie möglich in kleinen Fenstergrößen beibehalten werden soll.

Hier ist ein Beispiel angegeben:

![GIF oberen oder linken Nav adaptive Verhalten 1](images/navigation-top-to-left.png)

```xaml
<Grid >
    <VisualStateManager.VisualStateGroups>
        <VisualStateGroup>
            <VisualState>
                <VisualState.StateTriggers>
                    <AdaptiveTrigger MinWindowWidth="{x:Bind NavigationViewControl.CompactModeThresholdWidth}" />
                </VisualState.StateTriggers>

                <VisualState.Setters>
                    <Setter Target="NavigationViewControl.PaneDisplayMode" Value="Top"/>
                </VisualState.Setters>
            </VisualState>
        </VisualStateGroup>
    </VisualStateManager.VisualStateGroups>

    <NavigationView x:Name="NavigationViewControl" >
        <NavigationView.MenuItems>
            <NavigationViewItem Content="A" x:Name="A" />
            <NavigationViewItem Content="B" x:Name="B" />
            <NavigationViewItem Content="C" x:Name="C" />
        </NavigationView.MenuItems>
    </NavigationView>
</Grid>

```

In einigen Fällen müssen apps, andere Daten an den oberen Bereich und den linken Bereich gebunden. Im linke Bereich enthält häufig weitere Elemente für die Navigation.

Hier ist ein Beispiel angegeben:

![GIF oberen oder linken Nav adaptive Verhalten 2](images/navigation-top-to-left2.png)

```xaml
<Page >
    <Page.Resources>
        <DataTemplate x:name="navItem_top_temp" x:DataType="models:Item">
            <NavigationViewItem Background= Icon={x:Bind TopIcon}, Content={x:Bind TopContent}, Visibility={x:Bind TopVisibility} />
        </DataTemplate>

        <DataTemplate x:name="navItem_temp" x:DataType="models:Item">
            <NavigationViewItem Icon={x:Bind Icon}, Content={x:Bind Content}, Visibility={x:Bind Visibility} />
        </DataTemplate>
        
        <services:NavViewDataTemplateSelector x:Key="navview_selector" 
              NavItemTemplate="{StaticResource navItem_temp}" 
              NavItemTopTemplate="{StaticResource navItem_top_temp}" 
              NavPaneDisplayMode="{x:Bind NavigationViewControl.PaneDisplayMode}">
        </services:NavViewDataTemplateSelector>
    </Page.Resources>

    <Grid >
        <VisualStateManager.VisualStateGroups>
            <VisualStateGroup>
                <VisualState>
                    <VisualState.StateTriggers>
                        <AdaptiveTrigger MinWindowWidth="{x:Bind NavigationViewControl.CompactModeThresholdWidth}" />
                    </VisualState.StateTriggers>

                    <VisualState.Setters>
                        <Setter Target="NavigationViewControl.PaneDisplayMode" Value="Top"/>
                    </VisualState.Setters>
                </VisualState>
            </VisualStateGroup>
        </VisualStateManager.VisualStateGroups>

        <NavView x:Name='NavigationViewControl' MenuItemsSource={x:Bind items}   
                 PanePosition = "Top" MenuItemTemplateSelector="navview_selector" />
    </Grid>
</Page>

```

```csharp
ObservableCollection<Item> items = new ObservableCollection<Item>();
items.Add(new Item() {
    Content = "Aa",
    TopContent ="A",
    Icon = new BitmapIcon() { UriSource = new Uri("ms-appx:///testimage.jpg") },
    TopIcon = new BitmapIcon(),
    ItemVisibility = Visibility.Visible,
    TopItemVisiblity = Visibility.Visible 
});
items.Add(new Item() {
    Content = "Bb",
    TopContent = "B",
    Icon = new BitmapIcon() { UriSource = new Uri("ms-appx:///testimage.jpg") },
    TopIcon = new BitmapIcon(),
    ItemVisibility = Visibility.Visible,
    TopItemVisiblity = Visibility.Visible 
});
items.Add(new Item() {
    Content = "Cc",
    TopContent = "C",
    Icon = new BitmapIcon() { UriSource = new Uri("ms-appx:///testimage.jpg") },
    TopIcon = new BitmapIcon(),
    ItemVisibility = Visibility.Visible,
    TopItemVisiblity = Visibility.Visible 
});

public class NavViewDataTemplateSelector : DataTemplateSelector
    {
        public DataTemplate NavItemTemplate { get; set; }

        public DataTemplate NavItemTopTemplate { get; set; }    

     public NavigationViewPaneDisplayMode NavPaneDisplayMode { get; set; }

        protected override DataTemplate SelectTemplateCore(object item)
        {
            Item currItem = item as Item;
            if (NavPaneDisplayMode == NavigationViewPanePosition.Top)
                return NavItemTopTemplate;
            else 
                return NavItemTemplate;
        }   

    }

```

## <a name="interaction"></a>Interaktion

Wenn Benutzer in dem Bereich auf ein Navigationselement tippen, zeigt NavigationView dieses Element als ausgewählt an und löst ein [ItemInvoked](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.ItemInvoked)-Ereignis aus. Wenn durch das Tippen ein neues Element ausgewählt, löst NavigationView ebenfalls ein [SelectionChanged](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.SelectionChanged)-Ereignis aus.

Es ist Aufgabe Ihrer App, die Kopfzeile und den Inhalt in Reaktion auf diese Benutzerinteraktion mit entsprechenden Informationen zu aktualisieren. Darüber hinaus wird empfohlen, den [Fokus](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.control.FocusState) programmgesteuert vom Navigationselement zum Inhalt zu verlagern. Wenn Sie den anfänglichen Fokus auf das Laden festlegen, optimieren Sie den Benutzerfluss und verringern die Anzahl der Verschiebungen des Tastaturfokus.

### <a name="tabs"></a>Registerkarten

Im Modell Registerkarten sind Auswahl und Fokus gebunden. Eine Aktion, die normalerweise Schichten auch Auswahl Fokus würde. In den unter Beispiel rechten Arrowing würde verschieben Sie das Symbol Auswahl aus der Anzeige auf Bildschirmlupe. Sie können dies erreichen, indem Sie die [SelectionFollowsFocus](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.selectionfollowsfocus) -Eigenschaft auf aktiviert festlegen.

![Screenshot des nur-Text-Top navview](images/nav-tabs.png)

Hier wird die Verwendung von XAML-Beispiel für diese:

```xaml
<NavigationView PanePosition="Top" SelectionFollowsFocus="Enabled" >
   <NavigationView.MenuItems>
        <NavigationViewItem Content="Display" />
        <NavigationViewItem Content="Magnifier"  />
        <NavigationViewItem Content="Keyboard" />
    </NavigationView.MenuItems>
</NavigationView>

```

So ersetzen Sie Inhalte beim Ändern der Auswahl der Registerkarte kann des Rahmens [NavigateWithOptions](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.frame.NavigateToType) -Methode mit FrameNavigationOptions.IsNavigationStackEnabled auf False festgelegt ist, und NavigateOptions.TransitionInfoOverride auf den entsprechenden zum parallelen festgelegt Folienanimationen. Ein Beispiel finden Sie unter folgenden [Codebeispiel wird](#code-example) .

Wenn Sie den Standard-Formatvorlage ändern möchten, können Sie NavigationViews [MenuItemContainerStyle](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.menuitemcontainerstyle) -Eigenschaft außer Kraft setzen. Sie können auch die [MenuItemTemplate](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.menuitemtemplate) -Eigenschaft an eine andere Vorlage festlegen.

## <a name="backwards-navigation"></a>Rückwärtsnavigation

NavigationView verfügt über eine integrierte Schaltfläche „Zurück“, die mit den folgenden Eigenschaften aktiviert werden kann:

- [**IsBackButtonVisible**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsBackButtonVisible) ist eine NavigationViewBackButtonVisible-Enumeration und standardmäßig auf "Auto" festgelegt. Sie dient zum Einblenden/Ausblenden der Schaltfläche „Zurück“. Wenn die Schaltfläche nicht angezeigt wird, wird der Platz für die Darstellung der Schaltfläche „Zurück“ reduziert.
- [**IsBackEnabled**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsBackEnabled) lautet standardmäßig „false“ und kann zum Umschalten des Status der Schaltfläche „Zurück“ verwendet werden.
- [**BackRequested**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.BackRequested) wird ausgelöst, wenn ein Benutzer auf die Schaltfläche „Zurück“ klickt.
    - Wenn im minimalen oder kompakten Modus der NavigationView.Pane als Flyout geöffnet ist und auf die Schaltfläche „Zurück“ geklickt wird, wird der Bereich geschlossen und stattdessen das **PaneClosing**-Ereignis ausgelöst.
    - Wenn IsBackEnabled auf „false“ festgelegt ist, wird es nicht ausgelöst.

:::row:::
    :::column:::
    <b>Linke Navigationsleiste</b><br>
    ![NavigationView zurück-Schaltfläche auf linke Navigationsleiste](images/leftnav-back.png)
    :::column-end:::
    :::column:::
     <b>Oben nav</b><br>
    ![NavigationView zurück-Schaltfläche auf der oberen nav](images/topnav-back.png)
    :::column-end:::
:::row-end:::

## <a name="code-example"></a>Codebeispiel

> [!NOTE]
> NavigationView sollte als der Stammcontainer Ihrer App dienen, da dieses Steuerelement darauf ausgelegt ist, die volle Breite und Höhe des App-Fensters einzunehmen.
Sie können die Breite der angezeigten Anzeigemodi in der Navigationsansicht mit den Eigenschaften [CompactModeThresholdWidth](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.CompactModeThresholdWidth) und [ExpandedModeThresholdWidth](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.ExpandedModeThresholdWidth) überschreiben.

Es folgt ein Beispiel für End-to-End-wie Sie mit einem obersten Navigationsbereich auf große Fenstergrößen und einem linken Navigationsbereich auf kleine Fenstergrößen NavigationView integrieren können.

In diesem Beispiel wir erwarten Endbenutzer häufig neue Navigationskategorien auswählen und daher empfohlen:

- Legen Sie die [SelectionFollowsFocus](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PanePostion) -Eigenschaft auf aktiviert
- Verwenden Sie Frame-Navigation, die nicht dem Navigations-Stack hinzufügen.
- Behalten Sie den Standardwert auf die [ShoulderNavigationEnabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PanePostion) -Eigenschaft, die verwendet wird, um anzugeben, ob links/rechts Rückstoßelementen auf einem Gamepad die Navigation auf oberster Ebene Kategorien Ihrer App navigieren. Der Standardwert ist "WhenSelectionFollowsFocus". Die anderen möglichen Werte sind "Immer" und "Nie".

Es wird gezeigt, wie Navigation mit NavigationViews zurück-Schaltfläche rückwärts implementieren wird.

Hier ist eine Aufzeichnung der Zweck des Beispiels aus:

![NavigationView End-To-End-Beispiel](images/nav-code-example.gif)

Nachfolgend finden Sie im Beispielcode für:

> [!NOTE]
> Wenn Sie die [UI-Bibliothek für Windows](https://docs.microsoft.com/uwp/toolkits/winui/)verwenden, müssen Sie einen Verweis auf das Toolkit hinzufügen: `xmlns:controls="using:Microsoft.UI.Xaml.Controls"`.

```xaml
<Page
    x:Class="NavigationViewSample.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:NavigationViewSample"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d">

    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
        <VisualStateManager.VisualStateGroups>
            <VisualStateGroup>
                <VisualState>
                    <VisualState.StateTriggers>
                        <AdaptiveTrigger MinWindowWidth="{x:Bind NavView.CompactModeThresholdWidth}" />
                    </VisualState.StateTriggers>

                    <VisualState.Setters>
                        <Setter Target="NavView.PaneDisplayMode" Value="Top"/>
                    </VisualState.Setters>
                </VisualState>
            </VisualStateGroup>
        </VisualStateManager.VisualStateGroups>

        <NavigationView x:Name="NavView"
                    SelectionFollowsFocus="Enabled"
                    ItemInvoked="NavView_ItemInvoked"
                    IsSettingsVisible="True"
                    Loaded="NavView_Loaded"
                    BackRequested="NavView_BackRequested"
                    Header="Welcome">

            <NavigationView.MenuItems>
                <NavigationViewItem Content="Home" x:Name="home" Tag="home">
                    <NavigationViewItem.Icon>
                        <FontIcon Glyph="&#xE10F;"/>
                    </NavigationViewItem.Icon>
                </NavigationViewItem>
                <NavigationViewItemSeparator/>
                <NavigationViewItemHeader Content="Main pages"/>
                <NavigationViewItem Icon="AllApps" Content="Apps" x:Name="apps" Tag="apps"/>
                <NavigationViewItem Icon="Video" Content="Games" x:Name="games" Tag="games"/>
                <NavigationViewItem Icon="Audio" Content="Music" x:Name="music" Tag="music"/>
            </NavigationView.MenuItems>

            <NavigationView.AutoSuggestBox>
                <AutoSuggestBox x:Name="ASB" QueryIcon="Find"/>
            </NavigationView.AutoSuggestBox>

            <NavigationView.HeaderTemplate>
                <DataTemplate>
                    <Grid Margin="24,10,0,0">
                        <Grid.ColumnDefinitions>
                            <ColumnDefinition Width="Auto"/>
                            <ColumnDefinition/>
                        </Grid.ColumnDefinitions>
                        <TextBlock Style="{StaticResource TitleTextBlockStyle}"
                           FontSize="28"
                           VerticalAlignment="Center"
                           Text="Welcome"/>
                        <CommandBar Grid.Column="1"
                            HorizontalAlignment="Right"
                            VerticalAlignment="Top"
                            DefaultLabelPosition="Right"
                            Background="{ThemeResource SystemControlBackgroundAltHighBrush}">
                            <AppBarButton Label="Refresh" Icon="Refresh"/>
                            <AppBarButton Label="Import" Icon="Import"/>
                        </CommandBar>
                    </Grid>
                </DataTemplate>
            </NavigationView.HeaderTemplate>

            <Frame x:Name="ContentFrame" Margin="24"/>

        </NavigationView>
    </Grid>
</Page>
```

> [!NOTE]
> Wenn Sie die [UI-Bibliothek für Windows](https://docs.microsoft.com/uwp/toolkits/winui/)verwenden, müssen Sie einen Verweis auf das Toolkit hinzufügen: `using MUXC = Microsoft.UI.Xaml.Controls;`.

```csharp
// List of ValueTuple holding the Navigation Tag and the relative Navigation Page 
private readonly IList<(string Tag, Type Page)> _pages = new List<(string Tag, Type Page)>
{
    ("home", typeof(HomePage)),
    ("apps", typeof(AppsPage)),
    ("games", typeof(GamesPage)),
    ("music", typeof(MusicPage)),
};

private void NavView_Loaded(object sender, RoutedEventArgs e)
{
    // You can also add items in code behind
    NavView.MenuItems.Add(new NavigationViewItemSeparator());
    NavView.MenuItems.Add(new NavigationViewItem
    {
        Content = "My content",
        Icon = new SymbolIcon(Symbol.Folder),
        Tag = "content"
    });
    _pages.Add(("content", typeof(MyContentPage)));

    ContentFrame.Navigated += On_Navigated;

    // NavView doesn't load any page by default: you need to specify it
    NavView_Navigate("home");

    // Add keyboard accelerators for backwards navigation
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

private void NavView_ItemInvoked(NavigationView sender, NavigationViewItemInvokedEventArgs args)
{

    if (args.IsSettingsInvoked)
        ContentFrame.Navigate(typeof(SettingsPage));
    else
    {
        // Getting the Tag from Content (args.InvokedItem is the content of NavigationViewItem)
        var navItemTag = NavView.MenuItems
            .OfType<NavigationViewItem>()
            .First(i => args.InvokedItem.Equals(i.Content))
            .Tag.ToString();

        NavView_Navigate(navItemTag);
    }
}

private void NavView_Navigate(string navItemTag)
{
    var item = _pages.First(p => p.Tag.Equals(navItemTag));
    ContentFrame.Navigate(item.Page);
}

private void NavView_BackRequested(NavigationView sender, NavigationViewBackRequestedEventArgs args)
{
    On_BackRequested();
}

private void BackInvoked(KeyboardAccelerator sender, KeyboardAcceleratorInvokedEventArgs args)
{
    On_BackRequested();
    args.Handled = true;
}

private bool On_BackRequested()
{
    if (!ContentFrame.CanGoBack)
        return false;

    // Don't go back if the nav pane is overlayed
    if (NavView.IsPaneOpen &&
        (NavView.DisplayMode == NavigationViewDisplayMode.Compact ||
        NavView.DisplayMode == NavigationViewDisplayMode.Minimal))
        return false;

    ContentFrame.GoBack();
    return true;
}

private void On_Navigated(object sender, NavigationEventArgs e)
{
    NavView.IsBackEnabled = ContentFrame.CanGoBack;

    if (ContentFrame.SourcePageType == typeof(SettingsPage))
    {
        // SettingsItem is not part of NavView.MenuItems, and doesn't have a Tag
        NavView.SelectedItem = (NavigationViewItem)NavView.SettingsItem;
    }
    else
    {
        var item = _pages.First(p => p.Page == e.SourcePageType);

        NavView.SelectedItem = NavView.MenuItems
            .OfType<NavigationViewItem>()
            .First(n => n.Tag.Equals(item.Tag));
    }
}
```

## <a name="customizing-backgrounds"></a>Anpassen von Hintergründen

Legen Sie zum Ändern des Hintergrunds des Hauptbereichs von NavigationView seine `Background`-Eigenschaft auf Ihren bevorzugten Pinsel.

Im Bereich Hintergrund zeigt Acryl in-app, wenn NavigationView im oberen Bereich Minimal, oder Compact Modus befindet. Um dieses Verhalten zu aktualisieren oder die Darstellung des Acrylbereichs anzupassen, ändern Sie die zwei Designressourcen durch Überschreiben Ihrer App.xaml.

```xaml
<Application.Resources>
    <ResourceDictionary>
        <AcrylicBrush x:Key="NavigationViewDefaultPaneBackground"
        BackgroundSource="Backdrop" TintColor="Yellow" TintOpacity=".6"/>
        <AcrylicBrush x:Key="NavigationViewTopPaneBackground"
        BackgroundSource="Backdrop" TintColor="Yellow" TintOpacity=".6"/>
        <AcrylicBrush x:Key="NavigationViewExpandedPaneBackground"
        BackgroundSource="HostBackdrop" TintColor="Orange" TintOpacity=".8"/>
    </ResourceDictionary>
</Application.Resources>
```

## <a name="scroll-content-under-top-pane"></a>Scroll-Inhalte unter oberer Bereich

Für eine nahtlose aussehen + Verhalten empfohlen Wenn Ihre app verfügt, Seiten, die ein ScrollViewer verwenden und im Navigationsbereich oben positioniert wird, mit der Content Bildlaufleiste unterhalb der obersten Navigationsbereich.

Dies kann durch Festlegen der [CanContentRenderOutsideBounds](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.scrollviewer.cancontentrenderoutsidebounds) -Eigenschaft auf den entsprechenden ScrollViewer auf "true" erreicht werden.

![Navview Scroll Navigationsbereich](images/nav-scroll-content.png)

Wenn Ihre app sehr lange Blättern Inhalt verfügt, empfiehlt es sich, das Einbinden Kurznotiz Header, die an der oberen Navigationsbereich anzufügen und zu bilden eine glatte Fläche berücksichtigt werden sollten. 

![Kurznotiz Navview Scroll-header](images/nav-scroll-stickyheader.png)

Sie können dies erreichen, indem Sie die [ContentOverlay](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.ContentOverlay) -Eigenschaft auf NavigationView festlegen. 

Manchmal, wenn der Benutzer nach unten verschieben des Fensterinhalts ist, können Sie den Navigationsbereich erreicht, indem Sie die [IsPaneVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.ContentOverlay) -Eigenschaft auf NavigationView auf "false" ausblenden möchten.

![Navview Scroll ausblenden nav](images/nav-scroll-hidepane.png)

## <a name="related-topics"></a>Verwandte Themen

- [NavigationView-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview)
- [Master/Details](master-details.md)
- [Pivotsteuerelement](tabs-pivot.md)
- [Navigationsgrundlagen](../basics/navigation-basics.md)
- [Übersicht über Fluent Design für UWP](../fluent-design-system/index.md)