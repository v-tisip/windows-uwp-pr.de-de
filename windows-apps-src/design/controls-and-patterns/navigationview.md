---
author: QuinnRadich
Description: NavigationView is an adaptive control that implements top-level navigation patterns for your app.
title: Navigationsansicht
template: detail.hbs
ms.author: quradic
ms.date: 06/25/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
pm-contact: yulikl
design-contact: kimsea
dev-contact: ''
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 6c75169f118e2c8ef575fa251a7badc8cfe44247
ms.sourcegitcommit: 00d27738325d6db5b5e481911ae7fac0711b05eb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2018
ms.locfileid: "3664750"
---
# <a name="navigation-view-preview-version"></a>Navigationsansicht (Preview-Version)

> **Dies ist eine Preview-Version**: in diesem Artikel wird beschrieben, eine neue Version des das NavigationView-Steuerelement, das noch in Entwicklung befindet. Um es zu verwenden benötigen nun die [neuesten Windows-Insider-Build und SDK](https://insider.windows.com/for-developers/) oder der [Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).

Das NavigationView-Steuerelement bietet Navigation auf oberster Ebene für Ihre app. Es wird an eine Vielzahl von Bildschirmgrößen unterstützt mehrere Navigation Stile.

> **Windows-UI-Bibliothek-APIs**: [Microsoft.UI.Xaml.Controls.NavigationView-Klasse](/uwp/api/microsoft.ui.xaml.controls.navigationview)

> **Plattform-APIs**: [Windows.UI.Xaml.Controls.NavigationView-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview)

## <a name="get-the-windows-ui-library"></a>Abrufen der Windows-UI-Bibliothek

Dieses Steuerelement ist Bestandteil der Windows-UI-Bibliothek, NuGet-Paket, das neue Steuerelemente und UI-Features für UWP-apps enthält. Weitere Informationen, einschließlich installationsanweisungen finden Sie die [Übersicht über die Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/). 

## <a name="navigation-styles"></a>Navigation Stile

NavigationView unterstützt:

**Linken Navigationsbereich oder Menü**

![Navigationsbereich erweitert](images/displaymode-left.png)

**Oberer Navigationsbereich oder Menü**

![oberen Navigationsleiste](images/displaymode-top.png)

## <a name="is-this-the-right-control"></a>Ist dies das richtige Steuerelement?

NavigationView ist eine adaptive Navigationssteuerelement, das funktioniert gut für:

- Bereitstellen einer konsistenten navigationsumgebungen in der gesamten app.
- Sparen von Platz auf dem Bildschirm auf kleineren Fenstern.
- Organisieren von Zugriff auf viele Navigationskategorien aus.

Für andere Navigationssteuerelemente finden Sie unter [navigationsdesigngrundlagen](../basics/navigation-basics.md).

Wenn die Navigation komplexeres Verhalten erfordert, das von NavigationView nicht unterstützt wird, können Sie stattdessen das [Master/Details](master-details.md)-Muster verwenden.

:::row:::
    :::column:::
        ![Einige image](images/XAML-controls-gallery-app-icon.png)
    :::column-end:::
    ::: Column Span = "2"::: **XAML-Steuerelementekatalog**<br>
        Wenn Sie die XAML-Steuerelementekatalog-app installiert haben, klicken Sie <a href="xamlcontrolsgallery:/item/NavigationView">hier</a> die app zu öffnen und finden Sie unter NavigationView in Aktion zu sehen.

        <a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT">Get the XAML Controls Gallery app (Microsoft Store)</a><br>
        <a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics">Get the source code (GitHub)</a>
    :::column-end:::
:::row-end:::

## <a name="display-modes"></a>Anzeigemodi

NavigationView kann auf unterschiedliche Anzeigemodi festgelegt werden, über die `PaneDisplayMode` Eigenschaft:

:::row:::
    :::column:::
    ### Left
    Displays an expanded left positioned pane.
    :::column-end:::
    :::column span="2":::
    ![left nav pane expanded](images/displaymode-left.png)
    :::column-end:::
:::row-end:::

Wir empfehlen die linke Navigation bei:

- Sie haben eine mittlere bis hohe Anzahl (5-10) wichtiger Navigation auf oberster Ebene Kategorien.
- Gewünschte sehr schwerwiegende Navigationskategorien mit weniger Speicherplatz für die anderen Inhalten der app.

:::row:::
    :::column:::
    ### Top
    Displays a top positioned pane.
    :::column-end:::
    :::column span="2":::
    ![top navigation](images/displaymode-top.png)
    :::column-end:::
:::row-end:::

Wir empfehlen oberen Navigationsleiste wenn:

- Sie haben 5 oder weniger wichtiger Navigationskategorien der obersten Ebene, dass alle zusätzlichen Navigation auf oberster Ebene Kategorien, zu denen in der Dropdownliste landen overflow Menü gelten als weniger wichtig.
- Sie müssen alle Navigationsoptionen auf dem Bildschirm anzeigen.
- Sie möchten mehr Platz für Ihre app-Inhalte.
- Symbole können nicht klar Navigationskategorien Ihrer app beschreiben.

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

![GIF Leftnav standardmäßigen adaptiven Verhaltens](images/displaymode-auto.png)

Passt zwischen LeftMinimal auf kleinen Bildschirmen, LeftCompact für mittelgroße Bildschirme, und von links auf großen Bildschirmen an. Finden Sie im Abschnitt [adaptives Verhalten](#adaptive-behavior) für Weitere Informationen.

## <a name="anatomy"></a>Aufbau

<b>Linke Navigationsleiste</b><br>

![linken Abschnitte von NavigationView](images/leftnav-anatomy.png)

<b>Oben nav</b><br>

![Top Abschnitte von NavigationView](images/topnav-anatomy.png)

## <a name="pane"></a>Bereich

Der Bereich kann positioniert werden im Vordergrund oder auf der linken Seite über die `PanePosition` Eigenschaft.

Hier ist der Aufbau detaillierte Bereich für die linken und oberen Bereich Positionen:

<b>Linke Navigationsleiste</b><br>

![NavigationView Anatomie](images/navview-pane-anatomy-vertical.png)

1. Menü-Taste
1. Navigationselemente
1. Trennzeichen
1. Header
1. AutoSuggestBox (optional)
1. Schaltfläche "Einstellungen" (optional)

<b>Oben nav</b><br>

![NavigationView Anatomie](images/navview-pane-anatomy-horizontal.png)

1. Header
1. Navigationselemente
1. Trennzeichen
1. AutoSuggestBox (optional)
1. Schaltfläche "Einstellungen" (optional)

Die zurück-Schaltfläche angezeigt wird, in der oberen linken Ecke des Bereichs, aber NavigationView nicht automatisch Inhalte auf dem zurück-Stapel hinzu. Zum Aktivieren der Rückwärtsnavigation, finden Sie unter der [Rückwärts Navigation](#backwards-navigation) Abschnitt.

Der NavigationView-Bereich kann auch Folgendes enthalten:

1. Navigationselemente in Form von [NavigationViewItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitem), um zu bestimmten Seiten zu navigieren.
2. Trennzeichen in Form von [NavigationViewItemSeparator](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitemseparator), um Navigationselemente zu gruppieren. Legen Sie die [Opacity](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitemseparator.opacity) -Eigenschaft auf 0, um das Trennzeichen Platz nötig rendern.
3. Header in Form von [NavigationViewItemHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitemheader), zum Beschriften von Gruppen von Elementen.
4. Eine optionale [AutoSuggestBox](auto-suggest-box.md) für die Suche auf app-Ebene zulassen.
5. Ein optionaler Einstiegspunkt für [App-Einstellungen](../app-settings/app-settings-and-data.md). Um das Einstellungen-Element zu verbergen, verwenden Sie die [IsSettingsVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsSettingsVisible) -Eigenschaft.

Im linke Bereich enthält:

6. Menüschaltfläche, um den Bereich öffnen und schließen zu wechseln. Sie können bei größeren App-Fenstern mit geöffnetem Bereich diese Schaltfläche mit der Eigenschaft [IsPaneToggleButtonVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsPaneToggleButtonVisible) ausblenden.

### <a name="pane-footer"></a>Fußzeile

Freier Inhalt in der Fußzeile des Bereichs beim Hinzufügen zur [PaneFooter](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneFooter)-Eigenschaft

:::row:::
    :::column:::
    <b>Linke Navigationsleiste</b><br>
    ![Bereich Fußzeile linke Navigationsleiste](images/navview-freeform-footer-left.png)<br>
    :::column-end:::
    :::column:::
     <b>Oben nav</b><br>
    ![Bereich Header oben nav](images/navview-freeform-footer-top.png)<br>
    :::column-end:::
:::row-end:::

### <a name="pane-header"></a>Header des Bereichs

Formfreie Inhalte in den Bereich Header, wenn die Eigenschaft [PaneHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneHeader) hinzugefügt

:::row:::
    :::column:::
    <b>Linke Navigationsleiste</b><br>
    ![Bereich Header linke Navigationsleiste](images/navview-freeform-header-left.png)<br>
    :::column-end:::
    :::column:::
     <b>Oben nav</b><br>
    ![Bereich Header oben nav](images/navview-freeform-header-top.png)<br>
    :::column-end:::
:::row-end:::

### <a name="pane-content"></a>Bereich Inhalt

Formfreie Inhalte in den Bereich, wenn die Eigenschaft [PaneCustomContent](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneCustomContent) hinzugefügt

:::row:::
    :::column:::
    <b>Linke Navigationsleiste</b><br>
    ![Bereich benutzerdefinierte Contentleft nav](images/navview-freeform-pane-left.png)<br>
    :::column-end:::
    :::column:::
     <b>Oben nav</b><br>
    ![Bereich benutzerdefinierte Inhalte oben nav](images/navview-freeform-pane-top.png)<br>
    :::column-end:::
:::row-end:::

### <a name="visual-style"></a>Visueller Stil

Wenn Hardware-und softwareanforderungen erfüllt sind, verwendet NavigationView automatisch das [Acryl-Material](../style/acrylic.md) in seinem Bereich und [Reveal-Highlight](../style/reveal.md) , nur in der linken Seite.

## <a name="header"></a>Kopfzeile

![Navview allgemeines Bild der Headerbereich](images/nav-header.png)

Der Kopfzeilenbereich der Navigationsschaltfläche in der linken Bereich Position vertikal ausgerichtet ist, und unterhalb des Bereichs in der oberen Bereich Position liegt. Es hat eine feste Höhe von 52 Pixel. Er dient dazu, den Seitentitel der ausgewählten Navigationskategorie aufrechtzuerhalten. Die Kopfzeile ist an den oberen Rand der Seite angedockt und dient als Scroll-Clipping-Punkt für den Inhaltsbereich.

Die Kopfzeile muss sichtbar sein, wenn sich NavigationView im minimierten Anzeigemodus befindet. Sie können die Kopfzeile in anderen Modi ausblenden, die bei größeren Fensterbreiten verwendet werden. Legen Sie dazu die Eigenschaft [AlwaysShowHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.AlwaysShowHeader) auf **false** fest.

## <a name="content"></a>Inhalt

![Allgemeines Bild des Inhaltsbereichs navview](images/nav-content.png)

Im Inhaltsbereich werden die meisten Informationen für die ausgewählte Navigationskategorie angezeigt.

Wir empfehlen, Ränder für Ihren Inhaltsbereich auf 12Pixel festzulegen, wenn sich NavigationView im minimierten Modus befindet. Verwenden Sie andernfalls 24Pixel.

## <a name="adaptive-behavior"></a>Adaptives Verhalten

NavigationView ändert je nach verfügbarem Platz auf dem Bildschirm automatisch den Anzeigemodus. Möglicherweise möchten jedoch das adaptive anzeigemodusverhalten anpassen.

### <a name="default"></a>Standard

Die standardmäßigen adaptiven Verhaltens von NavigationView ist zum Anzeigen einer erweiterten linken Bereich auf großen fensterbreiten, ein Symbol nur Navigationsbereich bei mittelgroßen fensterbreiten und eine Hamburger-Menü-Schaltfläche auf kleine fensterbreiten. Weitere Informationen zu Fenstergrößen für adaptives Verhalten finden Sie unter [Bildschirmgrößen und Breakpoints](../layout/screen-sizes-and-breakpoints-for-responsive-design.md).

![GIF Leftnav standardmäßigen adaptiven Verhaltens](images/displaymode-auto.png)

```xaml
<NavigationView />
```

### <a name="minimal"></a>Minimiert

Ein zweites Allgemeines adaptives Muster ist einen erweiterten linken Bereich auf große fensterbreiten, und ein Hamburger-Menü auf beide kleinen und mittelgroßen fensterbreiten verwenden.

![GIF Leftnav adaptives Verhalten 2](images/adaptive-behavior-minimal.png)

```xaml
<NavigationView CompactModeThresholdWidth="1008" ExpandedModeThresholdWidth="1007" />
```

Wir empfehlen diese Lösung, wenn:

- Mehr Platz für app-Inhalte auf kleinere fensterbreiten gewünschten.
- Die Navigationskategorien werden nicht eindeutig mit Symbolen dargestellt.

### <a name="compact"></a>Kompakt

Ein drittes Allgemeines adaptives Muster ist einen erweiterten linken Bereich auf großen fensterbreiten und ein Symbol nur Navigationsbereich auf beide kleinen und mittelgroßen fensterbreiten verwenden. Ein gutes Beispiel hierfür ist die Mail-app.

![GIF Leftnav adaptives Verhalten 3](images/adaptive-behavior-compact.png)

```xaml
<NavigationView CompactModeThresholdWidth="0" ExpandedModeThresholdWidth="1007" />
```

Wir empfehlen diese Lösung, wenn:

- Es ist wichtig, immer alle Navigationsoptionen auf dem Bildschirm anzeigen.
- die Navigationskategorien können deutlich mit Symbolen dargestellt werden.

### <a name="no-adaptive-behavior"></a>Keine adaptives Verhalten

In einigen Fällen möglicherweise keine adaptives Verhalten überhaupt gewünschte. Sie können den Bereich werden immer erweitert, immer compact oder immer minimale festlegen.

![GIF Leftnav adaptives Verhalten 4](images/adaptive-behavior-none.png)

```xaml
<NavigationView PaneDisplayMode="LeftMinimal" />
```

### <a name="top-to-left-navigation"></a>Oben linken Navigationsbereich

Wir empfehlen die Verwendung der oberen Navigationsleiste auf großen Fenstergrößen und linken Navigationsbereich auf kleinen Fenster Größe wenn:

- Sie haben eine Reihe von gleichmäßig wichtige Navigation auf oberster Ebene Kategorien zusammen angezeigt werden, wenn eine Kategorie in diesen auf dem Bildschirm passt, Sie auf linke Navigation zu gleich Bedeutung zu reduzieren.
- Möchten Sie so viel Inhalt Speicherplatz wie möglich in kleinen Fenstergrößen beibehalten.

Hier ist ein Beispiel angegeben:

![GIF oberen oder linken Nav adaptives Verhalten 1](images/navigation-top-to-left.png)

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

Manchmal müssen apps, um unterschiedliche Daten an den oberen Bereich und linken Bereich zu binden. Im linke Bereich umfasst häufig weitere Elemente für die Navigation.

Hier ist ein Beispiel angegeben:

![GIF oberen oder linken Nav adaptives Verhalten 2](images/navigation-top-to-left2.png)

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

Im Modell Registerkarten sind Auswahl und Fokus gebunden. Eine Aktion, die normalerweise Schichten auch Auswahl Fokus würde. In dem Beispiel unten haben rechten Arrowing verschoben Marke für die Auswahl aus der Anzeige Bildschirmlupe. Sie können dies erreichen, indem Sie die Eigenschaft [SelectionFollowsFocus](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.selectionfollowsfocus) auf aktiviert.

![Screenshot von nur-Text-oberen navview](images/nav-tabs.png)

Nachfolgend finden Sie im XAML-Beispiel für die:

```xaml
<NavigationView PanePosition="Top" SelectionFollowsFocus="Enabled" >
   <NavigationView.MenuItems>
        <NavigationViewItem Content="Display" />
        <NavigationViewItem Content="Magnifier"  />
        <NavigationViewItem Content="Keyboard" />
    </NavigationView.MenuItems>
</NavigationView>

```

Um, Inhalte auszutauschen beim Registerkarte Auswahl zu ändern, verwenden Sie Frames [NavigateWithOptions](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.frame.NavigateToType) Methode FrameNavigationOptions.IsNavigationStackEnabled auf "false" festgelegt und NavigateOptions.TransitionInfoOverride festlegen, um die entsprechenden um parallele Folienanimation. Ein Beispiel finden Sie im [Codebeispiel](#code-example) unten.

Wenn Sie den Standardstil ändern möchten, können Sie NavigationView [MenuItemContainerStyle](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.menuitemcontainerstyle) Eigenschaft überschreiben. Sie können auch die [MenuItemTemplate](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.menuitemtemplate) -Eigenschaft an eine andere Datenvorlage festlegen.

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
    ![Zurück-Schaltfläche auf linke Navigationsleiste](images/leftnav-back.png)
    :::column-end:::
    :::column:::
     <b>Oben nav</b><br>
    ![Zurück-Schaltfläche auf oben nav](images/topnav-back.png)
    :::column-end:::
:::row-end:::

## <a name="code-example"></a>Codebeispiel

> [!NOTE]
> NavigationView sollte als der Stammcontainer Ihrer App dienen, da dieses Steuerelement darauf ausgelegt ist, die volle Breite und Höhe des App-Fensters einzunehmen.
Sie können die Breite der angezeigten Anzeigemodi in der Navigationsansicht mit den Eigenschaften [CompactModeThresholdWidth](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.CompactModeThresholdWidth) und [ExpandedModeThresholdWidth](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.ExpandedModeThresholdWidth) überschreiben.

Im folgenden ist ein End-to-End-Beispiel dafür, wie Sie NavigationView mit einem oberen Navigationsbereich auf großen Fenstergrößen und einem linken Navigationsbereich auf kleinen Fenstergrößen integrieren können.

In diesem Beispiel werden wir davon ausgehen, dass Endbenutzer häufig neue Navigationskategorien auszuwählen, und wir:

- Legen Sie die Eigenschaft [SelectionFollowsFocus](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PanePostion) auf aktiviert
- Verwenden Sie die Frame-Navigation, die nicht Navigationsstapel hinzufügen.
- Behalten Sie den Standardwert für die [ShoulderNavigationEnabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PanePostion) -Eigenschaft, die verwendet wird, um anzugeben, ob linker/rechter Bumper auf einem Gamepad die Navigation auf oberster Ebene Kategorien von Ihrer app navigieren. Der Standardwert ist "WhenSelectionFollowsFocus". Mögliche Werte sind "Immer" und "Never".

Es wird veranschaulicht, wie die Rückwärtsnavigation mit der zurück-Schaltfläche implementiert.

Hier sehen Sie eine Aufzeichnung der Zweck des Beispiels ein:

![NavigationView-End-To-End-Beispiel](images/nav-code-example.gif)

Hier ist der Beispielcode:

> [!NOTE]
> Wenn Sie die [Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/)verwenden, Sie müssen einen Verweis auf das Toolkit hinzufügen: `xmlns:controls="using:Microsoft.UI.Xaml.Controls"`.

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
> Wenn Sie die [Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/)verwenden, Sie müssen einen Verweis auf das Toolkit hinzufügen: `using MUXC = Microsoft.UI.Xaml.Controls;`.

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

Der Hintergrund des Bereichs zeigt in-app-Acryl, wenn sich NavigationView im minimalen, oben oder kompakten Modus befindet. Um dieses Verhalten zu aktualisieren oder die Darstellung des Acrylbereichs anzupassen, ändern Sie die zwei Designressourcen durch Überschreiben Ihrer App.xaml.

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

## <a name="scroll-content-under-top-pane"></a>Scrollen Sie Inhalte unter oberen Bereich

Für eine nahtlose Erscheinungsbild + Gefühl empfohlen Wenn Ihre app-Seiten, die einem ScrollViewer und Navigationsbereich oben positioniert wird, müssen den Bildlauf unterhalb der oberen Navigationsbereich.

Dies kann erfolgen, indem Sie die [CanContentRenderOutsideBounds](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.scrollviewer.cancontentrenderoutsidebounds) -Eigenschaft auf die relevanten ScrollViewer auf "true".

![Navview Scrollen Navigationsbereich](images/nav-scroll-content.png)

Wenn Ihre app sehr lange Bildlauf in Inhalten, empfiehlt es sich, einbinden sticky Header, die an der oberen Navigationsbereich anhängen und bilden eine glatte Oberfläche zu berücksichtigen. 

![Navview Scrollen sticky-Headers](images/nav-scroll-stickyheader.png)

Sie können dies erreichen, indem Sie die Eigenschaft [ContentOverlay](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.ContentOverlay) für NavigationView festlegen. 

In manchen Fällen, wenn der Benutzer nach unten Bildlauf ist, können Sie den Navigationsbereich erreicht, indem Sie die [IsPaneVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.ContentOverlay) -Eigenschaft auf NavigationView auf "false" ausblenden möchten.

![Navview Scrollen ausblenden nav](images/nav-scroll-hidepane.png)

## <a name="related-topics"></a>Verwandte Themen

- [NavigationView-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview)
- [Master/Details](master-details.md)
- [Pivotsteuerelement](tabs-pivot.md)
- [Navigationsgrundlagen](../basics/navigation-basics.md)
- [Übersicht über Fluent Design für UWP](../fluent-design-system/index.md)