---
author: serenaz
Description: Control that provides top-level app navigation with an automatically adapting, collapsible left navigation menu
title: Navigationsansicht
ms.assetid: ''
label: Navigation view
template: detail.hbs
ms.author: sezhen
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
pm-contact: vasriram
design-contact: kimsea
dev-contact: mitra
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: c7817bf7ff60a52ea48c988bdebd6d4d2eeacdb7
ms.sourcegitcommit: 618741673a26bd718962d4b8f859e632879f9d61
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2018
ms.locfileid: "1992149"
---
# <a name="navigation-view"></a>Navigationsansicht

Das Navigationsansicht-Steuerelement bietet über ein reduzierbares Navigationsmenü ein allgemeines vertikales Layout für App-Bereiche auf oberster Ebene. Dieses Steuerelement dient zur Implementierung des Navigationsbereichsmusters oder Hamburger-Menü-Musters, wobei die Anordnung automatisch an verschiedene Fenstergrößen des Bereichs angepasst wird.

> **Wichtige APIs**: [NavigationView-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview), [NavigationViewItem-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitem), [NavigationViewDisplayMode-Enumeration](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewdisplaymode)

![Beispiel für NavigationView](images/navview_wireframe.png)

## <a name="video-summary"></a>Video-Zusammenfassung

> [!VIDEO https://channel9.msdn.com/Events/Windows/Windows-Developer-Day-Fall-Creators-Update/WinDev010/player]

## <a name="is-this-the-right-control"></a>Ist dies das richtige Steuerelement?

NavigationView eignet sich gut für Folgendes:

-  Viele Navigationselementen auf oberster Ebene, die einen ähnlichen Typ aufweisen. (Dies kann beispielsweise eine Sport-App mit Kategorien wie Football, Baseball, Basketball, Fußball usw. sein.)
-  Eine mittlere bis hohe Zahl (5-10) an Navigationskategorien der obersten Ebene.
-  Bereitstellen einer konsistenten Navigationsumgebung. Der Bereich sollte nur Navigationselemente, keine Aktionen enthalten.
-  Sparen von Platz auf dem Bildschirm von kleineren Fenstern.

NavigationView ist nur eine von mehreren Navigationselementen, die Ihnen zur Verfügung stehen. Weitere Informationen zu anderen Navigationsmustern und -Elementen finden Sie unter [Navigationsdesigngrundlagen](../basics/navigation-basics.md).

Das NavigationView-Steuerelement verfügt über viele integrierte Verhaltensweisen, die das einfache Navigationsbereichsmuster implementieren. Wenn die Navigation komplexeres Verhalten erfordert, das von NavigationView nicht unterstützt wird, können Sie stattdessen das [Master/Details](master-details.md)-Muster verwenden.

## <a name="examples"></a>Beispiele
<table>
<th align="left">XAML-Steuerelementekatalog<th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p>Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/NavigationView">die App zu öffnen und NavigationView in Aktion zu sehen</a>.</p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics">Erwerben Sie den Quellcode (GitHub)</a></li>
    </ul>
</td>
</tr>
</table>

## <a name="navigationview-sections"></a>Abschnitte von NavigationView

![Abschnitte von NavigationView](images/navview_sections.png)

### <a name="pane"></a>Bereich

Mit der integrierten Navigationsschaltfläche („Hamburger“-Schaltfläche) können Benutzer den Bereich öffnen und schließen. Sie können bei größeren App-Fenstern mit geöffnetem Bereich diese Schaltfläche mit der Eigenschaft [IsPaneToggleButtonVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsPaneToggleButtonVisible) ausblenden. Bei der Beschriftung neben der Hamburger-Schaltfläche handelt es sich um die [PaneTitle](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneTitle)-Eigenschaft.

Die integrierte Schaltfläche „Zurück“ wird in der oberen linken Ecke des Bereichs angezeigt. Das NavigationView-Steuerelement fügt dem Zurück-Stapel nicht automatisch Inhalte hinzu, weitere Informationen zum Aktivieren der Rückwärtsnavigation finden Sie jedoch im Abschnitt [rückwärts Navigation](#backwards-navigation).

Der NavigationView-Bereich kann auch Folgendes enthalten:

- Navigationselemente in Form von [NavigationViewItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitem), um zu bestimmten Seiten zu navigieren
- Trennzeichen in Form von [NavigationViewItemSeparator](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitemseparator), um Navigationselemente zu gruppieren
- Header in Form von [NavigationViewItemHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitemheader), zum Beschriften von Gruppen von Elementen
- Eine optionale [AutoSuggestBox](auto-suggest-box.md) für die Suche auf App-Ebene
- Ein optionaler Einstiegspunkt für [App-Einstellungen](../app-settings/app-settings-and-data.md). Verwenden Sie zum Ausblenden des Einstellungselements die Eigenschaft [IsSettingsVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsSettingsVisible)
- Freier Inhalt in der Fußzeile des Bereichs beim Hinzufügen zur [PaneFooter](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneFooter)-Eigenschaft

#### <a name="visual-style"></a>Visueller Stil

NavigationView-Elemente unterstützen die Ansichtszustände „Ausgewählt“, „Deaktiviert“, „Zeiger über“, „Gedrückt“ und „Fokussiert“.

![Zustände von NavigationView-Elementen: deaktiviert, Zeiger über, gedrückt und fokussiert](images/navview_item-states.png)

Wenn Hardware- und Softwareanforderungen erfüllt sind, verwendet NavigationView in seinem Bereich automatisch das neue [Acryl-Material](../style/acrylic.md) und [Reveal-highlight](../style/reveal.md).

### <a name="header"></a>Kopfzeile

Der Kopfzeilenbereich ist vertikal an der Navigationsschaltfläche ausgerichtet und hat eine feste Höhe von 52Pixel. Er dient dazu, den Seitentitel der ausgewählten Navigationskategorie aufrechtzuerhalten. Die Kopfzeile ist an den oberen Rand der Seite angedockt und dient als Scroll-Clipping-Punkt für den Inhaltsbereich.

Die Kopfzeile muss sichtbar sein, wenn sich die Navigationsansicht im minimierten Modus befindet. Sie können die Kopfzeile in anderen Modi ausblenden, die bei größeren Fensterbreiten verwendet werden. Legen Sie dazu die Eigenschaft [AlwaysShowHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.AlwaysShowHeader) auf **false** fest.

### <a name="content"></a>Inhalt

Im Inhaltsbereich werden die meisten Informationen für die ausgewählte Navigationskategorie angezeigt. 

Wir empfehlen, Ränder für Ihren Inhaltsbereich auf 12Pixel festzulegen, wenn sich NavigationView im minimierten Modus befindet. Verwenden Sie andernfalls 24Pixel.

## <a name="navigationview-display-modes"></a>Anzeigemodi für NavigationView
Der Navigationsansichtsbereich kann offen oder geschlossen sein und verfügt über drei Optionen für Anzeigemodi:
-  **Minimiert** Nur die „Hamburger“-Schaltfläche bleibt fest, während der Bereich nach Bedarf ein- und ausgeblendet wird.
-  **Kompakt** Der Bereich wird als schmaler Streifen angezeigt, der zur vollen Breite erweitert werden kann.
-  **Erweitert** Der Bereich wird neben dem Inhalt geöffnet. Beim Schließen durch Aktivieren der „Hamburger“-Schaltfläche wird die Breite zu einem schmalen Streifen.

In der Standardeinstellung wählt das System je nach Größe des Bildschirmbereichs, der für das Steuerelement verfügbar ist, automatisch den optimalen Anzeigemodus aus. (Sie können diese Einstellung [überschreiben](#overriding-the-default-adaptive-behavior).)

### <a name="minimal"></a>Minimiert

![NavigationView im minimierten Modus mit geschlossenem und geöffnetem Bereich](images/navview_minimal.png)

-  Ist der Bereich geschlossen, wird er standardmäßig ausgeblendet, und es wird nur die Navigationsschaltfläche angezeigt.
-  Bietet On-Demand-Navigation, die Platz auf dem Bildschirm spart. Ideal für Apps auf Smartphones und Tablets.
-  Durch Drücken der Navigationsschaltfläche wird der Bereich geöffnet und geschlossen, der als eine Überlagerung über der Kopfzeile und dem Inhalt angezeigt wird. Inhalt wird nicht dynamisch umgebrochen.
-  Im geöffneten Zustand stellt er einen vorübergehenden Bereich dar, der durch eine Geste zum einfachen Ausblenden wie Treffen einer Auswahl, Drücken der Zurück-Schaltfläche oder Tippen außerhalb des Bereichs geschlossen werden kann.
-  Das ausgewählte Element wird angezeigt, wenn die Überlagerung des Bereichs geöffnet wird.
-  Wenn Anforderungen erfüllt sind, verwendet der Hintergrund des geöffneten Bereichs [In-App-Acryl](../style/acrylic.md#acrylic-blend-types).
-  NavigationView befindet sich standardmäßig im minimierten Modus, wenn die gesamte Breite kleiner oder gleich 640Pixel ist.

### <a name="compact"></a>Kompakt

![NavigationView im kompakten Modus mit geschlossenem und geöffnetem Bereich](images/navview_compact.png)

-  Ist der Bereich geschlossen, werden ein vertikaler Streifen des Bereichs nur mit Symbolen sowie die Navigationsschaltfläche angezeigt.
-  Zeigen die ausgewählte Position an, während sie nur wenig Platz auf dem Bildschirm belegen.
-  Dieser Modus ist besser für mittelgroße Bildschirme wie Tablets und [10-Fuß-Umgebungen](../devices/designing-for-tv.md) geeignet.
-  Durch Drücken der Navigationsschaltfläche wird der Bereich geöffnet und geschlossen, der als eine Überlagerung über der Kopfzeile und dem Inhalt angezeigt wird. Inhalt wird nicht umgebrochen.
-  Die Kopfzeile ist nicht erforderlich und kann ausgeblendet werden, um Inhalt mehr vertikale Fläche zu bieten.
-  Das ausgewählte Element zeigt einen visuellen Hinweis an, um hervorzuheben, wo sich der Benutzer in der Navigationsstruktur befindet.
-  Wenn Anforderungen erfüllt sind, verwendet der Hintergrund des Bereichs [In-App-Acryl](../style/acrylic.md#acrylic-blend-types).
-  NavigationView befindet sich standardmäßig im kompakten Modus, wenn die gesamte Breite zwischen 641 und 1007px aufweist.

### <a name="expanded"></a>Erweitert

![NavigationView im erweiterten Modus mit geöffnetem Bereich](images/navview_expanded.png)

-  Der Bereich bleibt standardmäßig geöffnet. Dieser Modus ist besser für größere Bildschirme geeignet.
-  Der Bereich wird neben Kopfzeile und Inhalt angezeigt, der innerhalb des verfügbaren Platzes dynamisch umgebrochen wird.
-  Wenn der Bereich mit der Navigationsschaltfläche geschlossen wird, wird der Bereich als ein schmaler Streifen neben dem Header und Inhalt angezeigt.
-  Die Kopfzeile ist nicht erforderlich und kann ausgeblendet werden, um Inhalt mehr vertikale Fläche zu bieten.
-  Das ausgewählte Element zeigt einen visuellen Hinweis an, um hervorzuheben, wo sich Benutzer in der Navigationsstruktur befindet.
-  Wenn Anforderungen erfüllt sind, wird der Hintergrund des Bereichs mit [Hintergrund-Acryl](../style/acrylic.md#acrylic-blend-types) gezeichnet.
-  NavigationView befindet sich standardmäßig im erweiterten Modus, wenn die gesamte Breite mehr als 1007px umfasst.

### <a name="overriding-the-default-adaptive-behavior"></a>Überschreiben des standardmäßigen adaptiven Verhaltens

NavigationView ändert je nach verfügbarem Platz auf dem Bildschirm automatisch den Anzeigemodus.

> [!NOTE]
> NavigationView sollte als der Stammcontainer Ihrer App dienen, da dieses Steuerelement darauf ausgelegt ist, die volle Breite und Höhe des App-Fensters einzunehmen.
Sie können die Breite der angezeigten Anzeigemodi in der Navigationsansicht mit den Eigenschaften [CompactModeThresholdWidth](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.CompactModeThresholdWidth) und [ExpandedModeThresholdWidth](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.ExpandedModeThresholdWidth) überschreiben.

Berücksichtigen Sie die folgenden Szenarien, die veranschaulichen, wann Sie das Anzeigemodusverhalten ggf. anpassen sollten.

- **Häufiges Navigieren** Wenn Sie davon ausgehen, dass Benutzer relativ häufig zwischen App-Bereichen navigieren, sollten Sie überlegen, den Bereich bei geringeren Fensterbreiten eingeblendet zu lassen. Eine Musik-App mit Navigationsbereichen für Songs/Alben/Künstler kann eine Bereichsbreite von 280px verwenden und den erweiterten Modus beibehalten, wenn das App-Fenster breiter als 560px ist.
```xaml
<NavigationView OpenPaneLength="280" CompactModeThresholdWidth="560" ExpandedModeThresholdWidth="560"/>
```

- **Seltenes Navigieren** Wenn Sie davon ausgehen, dass Benutzer sehr selten zwischen App-Bereichen navigieren, sollten Sie überlegen, den Bereich bei größeren Fensterbreiten ausgeblendet zu lassen. Eine Rechner-App mit mehreren Layouts behält möglicherweise auch dann den minimierten Modus bei, wenn die App auf einem 1080p-Display maximiert ist.
```xaml
<NavigationView CompactModeThresholdWidth="1920" ExpandedModeThresholdWidth="1920"/>
```

- **Mehrdeutigkeit** von Symbolen Wenn sich die Navigationsbereiche Ihrer App nicht für aussagekräftige Symbole eignen, vermeiden Sie die Verwendung des kompakten Modus. Eine Bildanzeige-App mit Navigationsbereichen für Sammlungen/Alben/Ordner zeigt NavigationView bei geringen und mittleren Breiten möglicherweise im minimierten Modus und bei großer Breite im erweiterten Modus an.
```xaml
<NavigationView CompactModeThresholdWidth="1008"/>
```

## <a name="interaction"></a>Interaktion

Wenn Benutzer in dem Bereich auf ein Navigationselement tippen, zeigt NavigationView dieses Element als ausgewählt an und löst ein [ItemInvoked](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.ItemInvoked)-Ereignis aus. Wenn durch das Tippen ein neues Element ausgewählt, löst NavigationView ebenfalls ein [SelectionChanged](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.SelectionChanged)-Ereignis aus. 

Es ist Aufgabe Ihrer App, die Kopfzeile und den Inhalt in Reaktion auf diese Benutzerinteraktion mit entsprechenden Informationen zu aktualisieren. Darüber hinaus wird empfohlen, den [Fokus](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.control.FocusState) programmgesteuert vom Navigationselement zum Inhalt zu verlagern. Wenn Sie den anfänglichen Fokus auf das Laden festlegen, optimieren Sie den Benutzerfluss und verringern die Anzahl der Verschiebungen des Tastaturfokus.

## <a name="backwards-navigation"></a>Rückwärtsnavigation
NavigationView verfügt über eine integrierte Schaltfläche „Zurück“, die mit den folgenden Eigenschaften aktiviert werden kann:
- [**IsBackButtonVisible**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsBackButtonVisible) ist eine NavigationViewBackButtonVisible-Enumeration und standardmäßig auf "Auto" festgelegt. Sie dient zum Einblenden/Ausblenden der Schaltfläche „Zurück“. Wenn die Schaltfläche nicht angezeigt wird, wird der Platz für die Darstellung der Schaltfläche „Zurück“ reduziert.
- [**IsBackEnabled**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsBackEnabled) lautet standardmäßig „false“ und kann zum Umschalten des Status der Schaltfläche „Zurück“ verwendet werden.
- [**BackRequested**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.BackRequested) wird ausgelöst, wenn ein Benutzer auf die Schaltfläche „Zurück“ klickt.
    - Wenn im minimalen oder kompakten Modus der NavigationView.Pane als Flyout geöffnet ist und auf die Schaltfläche „Zurück“ geklickt wird, wird der Bereich geschlossen und stattdessen das **PaneClosing**-Ereignis ausgelöst.
    - Wenn IsBackEnabled auf „false“ festgelegt ist, wird es nicht ausgelöst.

![Schaltfläche „Zurück“ der NavigationView](../basics/images/back-nav/NavView.png)

## <a name="code-example"></a>Codebeispiel

Es folgt ein einfaches Beispiel dafür, wie Sie NavigationView in Ihre App integrieren können. 

Es wird veranschaulicht, wie die Rückwärtsnavigation mit der Schaltfläche „Zurück“ der NavigationView implementiert wird. Beachten Sie, dass Sie für die Verwendung der Eigenschaften für die Rückwärtsnavigation [Windows10 Insider Preview (in v10.0.17110.0 eingeführt)](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewSDK) benötigen.

Außerdem wird die Lokalisierung von Inhaltszeichenfolgen für Navigationselemente mit `x:Uid` veranschaulicht. Weitere Informationen zur Lokalisierung finden Sie unter [Lokalisieren von Zeichenfolgen in der Benutzeroberfläche](../../app-resources/localize-strings-ui-manifest.md).

```xaml
<Page
    x:Class="NavigationViewSample.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:NavigationViewSample"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d">

    <NavigationView x:Name="NavView"
                    ItemInvoked="NavView_ItemInvoked"
                    Loaded="NavView_Loaded"
                    BackRequested="NavView_BackRequested">

        <NavigationView.MenuItems>
            <NavigationViewItem x:Uid="HomeNavItem" Content="Home" Tag="home">
                <NavigationViewItem.Icon>
                    <FontIcon Glyph="&#xE10F;"/>
                </NavigationViewItem.Icon>
            </NavigationViewItem>
            <NavigationViewItemSeparator/>
            <NavigationViewItemHeader Content="Main pages"/>
            <NavigationViewItem x:Uid="AppsNavItem" Icon="AllApps" Content="Apps" Tag="apps"/>
            <NavigationViewItem x:Uid="GamesNavItem" Icon="Video" Content="Games" Tag="games"/>
            <NavigationViewItem x:Uid="MusicNavItem" Icon="Audio" Content="Music" Tag="music"/>
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

        <NavigationView.PaneFooter>
            <HyperlinkButton x:Name="MoreInfoBtn"
                             Content="More info"
                             Click="More_Click"
                             Margin="12,0"/>
        </NavigationView.PaneFooter>

        <Frame x:Name="ContentFrame" Margin="24">
            <Frame.ContentTransitions>
                <TransitionCollection>
                    <NavigationThemeTransition/>
                </TransitionCollection>
            </Frame.ContentTransitions>
        </Frame>

    </NavigationView>
</Page>
```

```csharp
private void NavView_Loaded(object sender, RoutedEventArgs e)
{
    // you can also add items in code behind
    NavView.MenuItems.Add(new NavigationViewItemSeparator());
    NavView.MenuItems.Add(new NavigationViewItem()
    { Content = "My content", Icon = new SymbolIcon(Symbol.Folder), Tag = "content" });

    // set the initial SelectedItem 
    foreach (NavigationViewItemBase item in NavView.MenuItems)
    {
        if (item is NavigationViewItem && item.Tag.ToString() == "home")
        {
            NavView.SelectedItem = item;
            break;
        }
    }
            
    ContentFrame.Navigated += On_Navigated;

    // add keyboard accelerators for backwards navigation
    KeyboardAccelerator GoBack = new KeyboardAccelerator();
    GoBack.Key = VirtualKey.GoBack;
    GoBack.Invoked += BackInvoked;
    KeyboardAccelerator AltLeft = new KeyboardAccelerator();
    AltLeft.Key = VirtualKey.Left;
    AltLeft.Invoked += BackInvoked;
    this.KeyboardAccelerators.Add(GoBack);
    this.KeyboardAccelerators.Add(AltLeft);
    // ALT routes here
    AltLeft.Modifiers = VirtualKeyModifiers.Menu;
    
}

private void NavView_ItemInvoked(NavigationView sender, NavigationViewItemInvokedEventArgs args)
{  
    if (args.IsSettingsInvoked)
    {
        ContentFrame.Navigate(typeof(SettingsPage));
    }
    else
    {
        // find NavigationViewItem with Content that equals InvokedItem
        var item = sender.MenuItems.OfType<NavigationViewItem>().First(x => (string)x.Content == (string)args.InvokedItem);
        NavView_Navigate(item as NavigationViewItem);
    }
}

private void NavView_Navigate(NavigationViewItem item)
{
    switch (item.Tag)
    {
        case "home":
            ContentFrame.Navigate(typeof(HomePage));
            break;

        case "apps":
            ContentFrame.Navigate(typeof(AppsPage));
            break;

        case "games":
            ContentFrame.Navigate(typeof(GamesPage));
            break;

        case "music":
            ContentFrame.Navigate(typeof(MusicPage));
            break;

        case "content":
            ContentFrame.Navigate(typeof(MyContentPage));
            break;
    }           
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
    bool navigated = false;

    // don't go back if the nav pane is overlayed
    if (NavView.IsPaneOpen && (NavView.DisplayMode == NavigationViewDisplayMode.Compact || NavView.DisplayMode == NavigationViewDisplayMode.Minimal))
    {
        return false;
    }
    else
    {
        if (ContentFrame.CanGoBack)
        {
            ContentFrame.GoBack();
            navigated = true;
        }
    }
    return navigated;
}

private void On_Navigated(object sender, NavigationEventArgs e)
{
    NavView.IsBackEnabled = ContentFrame.CanGoBack;

    if (ContentFrame.SourcePageType == typeof(SettingsPage))
    {
        NavView.SelectedItem = NavView.SettingsItem as NavigationViewItem;
    }
    else 
    {
        Dictionary<Type, string> lookup = new Dictionary<Type, string>()
        {
            {typeof(HomePage), "home"},
            {typeof(AppsPage), "apps"},
            {typeof(GamesPage), "games"},
            {typeof(MusicPage), "music"},
            {typeof(MyContentPage), "content"}    
        };

        String stringTag = lookup[ContentFrame.SourcePageType];

        // set the new SelectedItem  
        foreach (NavigationViewItemBase item in NavView.MenuItems)
        {
            if (item is NavigationViewItem && item.Tag.Equals(stringTag))
            {
                item.IsSelected = true;
                break;
            }
        }        
    }
}
```

## <a name="customizing-backgrounds"></a>Anpassen von Hintergründen

Legen Sie zum Ändern des Hintergrunds des Hauptbereichs von NavigationView seine `Background`-Eigenschaft auf Ihren bevorzugten Pinsel.

Der Hintergrundbereich verwendet In-App-Acryl, wenn NavigationView im minimalen oder kompakten Modus und das Hintergrund-Acryl im erweiterten Modus ist. Um dieses Verhalten zu aktualisieren oder die Darstellung des Acrylbereichs anzupassen, ändern Sie die zwei Designressourcen durch Überschreiben Ihrer App.xaml.

```xaml
<Application.Resources>
    <ResourceDictionary>
        <AcrylicBrush x:Key="NavigationViewDefaultPaneBackground"
        BackgroundSource="Backdrop" TintColor="Yellow" TintOpacity=".6"/>
        <AcrylicBrush x:Key="NavigationViewExpandedPaneBackground"
        BackgroundSource="HostBackdrop" TintColor="Orange" TintOpacity=".8"/>
    </ResourceDictionary>
</Application.Resources>
```

## <a name="extending-your-app-into-the-title-bar"></a>Erweitern Ihrer App auf die Titelleiste

Für eine nahtlose, fließende Darstellung im Fenster Ihrer App wird empfohlen, die NavigationView und deren Acrylbereich auf den Bereich der Titelleiste Ihrer App zu erweitern. Dadurch werden die visuell unattraktive Form, die durch die Titelleiste erzeugt wird, die einfarbigen NavigationView-Inhalte und der Acrylbereich der NavigationView vermieden.

Fügen Sie dazu den folgenden Code in der Datei App.xaml.cs hinzu.

```csharp
//draw into the title bar
var coreTitleBar = CoreApplication.GetCurrentView().TitleBar;
coreTitleBar.ExtendViewIntoTitleBar = true;

//remove the solid-colored backgrounds behind the caption controls and system back button
var viewTitleBar = ApplicationView.GetForCurrentView().TitleBar;
viewTitleBar.ButtonBackgroundColor = Colors.Transparent;
viewTitleBar.ButtonInactiveBackgroundColor = Colors.Transparent;
viewTitleBar.ButtonForegroundColor = (Color)Resources["SystemBaseHighColor"];
```

Das Zeichnen in die Titelleiste hat den Nebeneffekt, dass der App-Titel ausgeblendet wird. Stellen Sie zur Unterstützung der Benutzer den Titel wieder her, indem Sie einen eigenen TextBlock hinzufügen. Fügen Sie der Stammseite, die Ihre NavigationView enthält, das folgende Markup hinzu.

```xaml
<Grid>
    <TextBlock x:Name="AppTitle"
        xmlns:appmodel="using:Windows.ApplicationModel"
        Text="{x:Bind appmodel:Package.Current.DisplayName}"
        Style="{StaticResource CaptionTextBlockStyle}"
        IsHitTestVisible="False"
        Canvas.ZIndex="1"/>
    

    <NavigationView Canvas.ZIndex="0" ... />

</Grid>
```

Je nach Sichtbarkeit der Schaltfläche „Zurück“ müssen Sie auch die AppTitle-Ränder anpassen. Und wenn sich die App im FullScreenMode befindet, müssen Sie den Abstand für die Zurück-Pfeil auch dann entfernen, wenn die TitleBar Platz für sie reserviert.

```csharp
var coreTitleBar = CoreApplication.GetCurrentView().TitleBar;
Window.Current.SetTitleBar(AppTitle);
coreTitleBar.ExtendViewIntoTitleBar = true;

void UpdateAppTitle()
{
    var full = (ApplicationView.GetForCurrentView().IsFullScreenMode);
    var left = 12 + (full ? 0 : CoreApplication.GetCurrentView().TitleBar.SystemOverlayLeftInset);
    AppTitle.Margin = new Thickness(left, 8, 0, 0);
}

Window.Current.CoreWindow.SizeChanged += (s, e) => UpdateAppTitle();
coreTitleBar.LayoutMetricsChanged += (s, e) => UpdateAppTitle();
```

Weitere Informationen zum Anpassen von Titelleisten, finden Sie unter [Anpassung der Titelleiste](../shell/title-bar.md).

## <a name="related-topics"></a>Verwandte Themen

- [NavigationView-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview)
- [Master/Details](master-details.md)
- [Pivotsteuerelement](tabs-pivot.md)
- [Navigationsgrundlagen](../basics/navigation-basics.md)
- [Übersicht über Fluent Design für UWP](../fluent-design-system/index.md)

