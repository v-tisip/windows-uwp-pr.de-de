---
author: Jwmsft
Description: "Steuerelement für die Navigation auf oberster Ebene, das gleichzeitig Platz auf dem Bildschirm spart."
title: Navigationsansicht
ms.assetid: 
label: Navigation view
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
pm-contact: yulikl
design-contact: kimsea
dev-contact: tpaine
doc-status: Published
ms.openlocfilehash: 98ab8a95288e5a0225a2185f7ce037e16209d173
ms.sourcegitcommit: ba0d20f6fad75ce98c25ceead78aab6661250571
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2017
---
# <a name="navigation-view"></a>Navigationsansicht

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

> [!IMPORTANT]
> In diesem Artikel werden Funktionen beschrieben, die noch nicht veröffentlicht wurden und vor der kommerziellen Freigabe evtl. grundlegend geändert werden. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.

Das Navigationsansichts-Steuerelement bietet über ein reduzierbares Navigationsmenü ein allgemeines vertikales Layout für App-Bereiche auf oberster Ebene. Dieses Steuerelement dient der Implementierung des Navigationsbereichsmusters oder Hamburger-Menü-Musters, wobei die Anordnung automatisch an verschiedene Fenstergrößen angepasst wird.

> **Wichtige APIs**: [NavigationView-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview), [NavigationViewItem-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitem), [NavigationViewDisplayMode-Enumeration](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewdisplaymode)

![Beispiel für NavigationView](images/navview_wireframe.png)


## <a name="is-this-the-right-control"></a>Ist dies das richtige Steuerelement?

NavigationView eignet sich gut für:

-  Apps mit vielen Navigationselementen auf oberster Ebene, die einen ähnlichen Typ aufweisen. Dies kann beispielsweise eine Sport-App mit Kategorien wie Football, Baseball, Basketball, Fußball usw. sein.
-  Bereitstellen einer konsistenten Navigationsumgebung über verschiedene Apps hinweg. Der Bereich sollte nur Navigationselemente, keine Aktionen enthalten.
-  Eine mittlere bis hohe Zahl (5-10) an Navigationskategorien der obersten Ebene.
-  Sparen von Platz auf dem Bildschirm von kleineren Fenstern.

Die Naviagationsansicht ist nur eine von mehreren Navigationselementen, die Ihnen zur Verfügung stehen. Weitere Informationen zu Navigationsmustern und anderen Navigationselementen finden Sie unter [Navigationsdesigngrundlagen für UWP-Apps (Universelle Windows-Plattform)](../layout/navigation-basics.md).

Laden Sie die [XAML-Navigationslösung](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/XamlNavigation) von GitHub herunter, um ein Codebeispiel für das Erstellen eines Navigationsbereichsmusters mit SplitView und ListView zu erhalten.

## <a name="navigationview-parts"></a>Teile von NavigationView
Das Steuerelement lässt sich allgemein in drei Abschnitte unterteilen: einen Bereich für die Navigation auf der linken Seite und einen Kopfzeilen- sowie einen Inhaltsbereich auf der rechten Seite.

![Abschnitte von NavigationView](images/navview_sections.png)

### <a name="pane"></a>Bereich

Der Navigationsbereich kann Folgendes enthalten:

- Navigationselemente in Form von [NavigationViewItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitem), um zu bestimmten Seiten zu navigieren
- Trennzeichen in Form von [NavigationViewItemSeparator](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitemseparator), um Navigationselemente zu gruppieren
- Header in Form von [NavigationViewItemHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitemheader), zum Beschriften von Gruppen von Elementen
- Ein optionaler Einstiegspunkt für [App-Einstellungen](../app-settings/app-settings-and-data.md). Verwenden Sie zum Ausblenden des Einstellungselements die Eigenschaft [IsSettingsVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview#Windows_UI_Xaml_Controls_NavigationView_IsSettingsVisible)
- Freier Inhalt in der Fußzeile des Bereichs, wenn es zur [PaneFooter](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview#Windows_UI_Xaml_Controls_NavigationView_PaneFooter)-Eigenschaft hinzugefügt wird

Mit der integrierten Navigationsschaltfläche („Hamburger“-Schaltfläche) können Benutzer den Bereich öffnen und schließen. Sie können bei größeren Appfenstern mit geöffnetem Bereich diese Schaltfläche mit der Eigneschaft [IsPaneToggleButtonVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview#Windows_UI_Xaml_Controls_NavigationView_IsPaneToggleButtonVisible) ausblenden.

### <a name="header"></a>Header

Der Kopfzeilenbereich ist vertikal an der Navigationsschaltfläche ausgerichtet und hat eine feste Höhe. Er dient dazu, den Seitentitel der ausgewählten Navigationskategorie aufrechtzuerhalten. Die Kopfzeile ist an den oberen Rand der Seite angedockt und dient als Scroll-Clipping-Punkt für den Inhaltsbereich.

Die Kopfzeile muss sichtbar sein, wenn sich die Navigationsansicht im minimierten Modus befindet. Sie können die Kopfzeile in anderen Modi ausblenden, die bei größeren Fensterbreiten verwendet werden. Legen Sie dazu die Eigenschaft [AlwaysShowHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview#Windows_UI_Xaml_Controls_NavigationView_AlwaysShowHeader) auf **false** fest.

### <a name="content"></a>Inhalt

Im Inhaltsbereich werden die meisten Informationen für die ausgewählte Navigationskategorie angezeigt. Er kann ein oder mehrere Elemente enthalten und eignet sich gut für zusätzliche untergeordnete Navigationselemente wie [Pivot](tabs-pivot.md).

Wir empfehlen, Ränder auf Inhaltsseiten auf 12px festzulegen, wenn sich NavigationView im minimierten Modus befindet. Verwenden Sie andernfalls 24px.

## <a name="visual-style"></a>Visueller Stil

<div class="microsoft-internal-note">
Redlines für dieses Steuerelement sind verfügbar auf [UNI](http://uni/DesignDepot.FrontEnd/#/ProductNav?t=Fluent%20Design%20System%7CControls%20%26%20Patterns%7CNavigationView).<br/><br/>
</div>

Navigationselemente unterstützen die Ansichtszustände ausgewählt, deaktiviert, Zeiger über, gedrückt und fokussiert.

![Zustände von NavigationView-Elementen: deaktiviert, Zeiger über, gedrückt und fokussiert](images/navview_item-states.png)

Wenn Hardware- und Softwareanforderungen erfüllt sind, verwendet NavigationView in seinem Bereich automatisch das neue [Acryl-Material](../style/acrylic.md) und [Reveal-highlight](../style/reveal.md).


## <a name="navigationview-modes"></a>NavigationView-Modi
Der Navigationsansichtsbereich kann offen oder geschlossen sein und verfügt über drei Optionen für Anzeigemodi:
-  **Minimiert** Nur die „Hamburger“-Schaltfläche bleibt fest, während der Bereich nach Bedarf ein- und ausgeblendet wird.
-  **Kompakt** Der Bereich wird als schmaler Streifen angezeigt, der zur vollen Breite erweitert werden kann.
-  **Erweitert** Der Bereich wird neben dem Inhalt geöffnet. Beim Schließen durch Aktivieren der „Hamburger“-Schaltfläche wird die Breite zu einem schmalen Streifen.

In der Standardeinstellung wählt das System je nach Größe des Bildschirmbereichs, der für das Steuerelement verfügbar ist, automatisch den optimalen Anzeigemodus aus. (Sie können diese Einstellung überschreiben. Nähere Informationen dazu finden Sie im nächsten Abschnitt.)

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
-  Dieser Modus ist besser für mittelgroße Bildschirme wie Tablets und [10-Fuß-Umgebungen](../input-and-devices/designing-for-tv.md) geeignet.
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

## <a name="overriding-the-default-adaptive-behavior"></a>Überschreiben des standardmäßigen adaptiven Verhaltens

Die Navigationsansicht ändert je nach verfügbarem Platz auf dem Bildschirm automatisch den Anzeigemodus.
[!NOTE] NavigationView sollte als der Stammcontainer Ihrer App dienen. Dieses Steuerelement ist darauf ausgelegt, die volle Breite und Höhe des App-Fensters einzunehmen.
Sie können die Breite der angezeigten Anzeigemodi in der Navigationsansicht mit den Eigenschaften [CompactModeThresholdWidth](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview#Windows_UI_Xaml_Controls_NavigationView_CompactModeThresholdWidth) und ExpandedModeThresholdWidth](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview#Windows_UI_Xaml_Controls_NavigationView_ExpandedModeThresholdWidth) überschreiben. Berücksichtigen Sie die folgenden Szenarien, die veranschaulichen, wann Sie das Anzeigemodusverhalten ggf. anpassen sollten.

-  **Häufiges Navigieren** Wenn Sie davon ausgehen, dass Benutzer relativ häufig zwischen App-Bereichen navigieren, sollten Sie überlegen, den Bereich bei geringeren Fensterbreiten eingeblendet zu lassen. Eine Musik-App mit Navigationsbereichen für Songs/Alben/Künstler kann eine Bereichsbreite von 280px verwenden und den erweiterten Modus beibehalten, wenn das App-Fenster breiter als 560px ist.
```xaml
<NavigationView OpenPaneLength=”280” CompactModeThresholdWidth="560" ExpandedModeThresholdWidth=”560”/>
```
-    **Seltenes Navigieren** Wenn Sie davon ausgehen, dass Benutzer sehr selten zwischen App-Bereichen navigieren, sollten Sie überlegen, den Bereich bei größeren Fensterbreiten ausgeblendet zu lassen. Eine Rechner-App mit mehreren Layouts behält möglicherweise auch dann den minimierten Modus bei, wenn die App auf einem 1080p-Display maximiert ist.
```xaml
<NavigationView CompactModeThresholdWidth=”1920” ExpandedModeThresholdWidth=”1920”/>
```
-    **Mehrdeutigkeit** von Symbolen Wenn sich die Navigationsbereiche Ihrer App nicht für aussagekräftige Symbole eignen, vermeiden Sie die Verwendung des kompakten Modus. Eine Bildanzeige-App mit Navigationsbereichen für Sammlungen/Alben/Ordner zeigt NavigationView bei geringen und mittleren Breiten möglicherweise im minimierten Modus und bei großer Breite im erweiterten Modus an.
```xaml
<NavigationView CompactModeThresholdWidth=”1008”/>
```

## <a name="interaction"></a>Interaktion

Wenn Benutzer auf eine Navigationskategorie im Bereich tippen, zeigt NavigationView dieses Element als ausgewählt an und löst ein [ItemInvoked](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview#Windows_UI_Xaml_Controls_NavigationView_ItemInvoked)-Ereignis aus. Wenn durch das Tippen ein neues Element ausgewählt, löst NavigationView ebenfalls ein [SelectionChanged](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview#Windows_UI_Xaml_Controls_NavigationView_SelectionChanged)-Ereignis aus. Es ist Aufgabe Ihrer App, die Kopfzeile und den Inhalt in Reaktion auf diese Benutzerinteraktion mit entsprechenden Informationen zu aktualisieren. Darüber hinaus wird empfohlen, den Fokus programmgesteuert vom Navigationselement zum Inhalt zu verlagern. Wenn Sie den anfänglichen Fokus auf das Laden festlegen, optimieren Sie den Benutzerfluss und verringern die Anzahl der Verschiebungen des Tastaturfokus.

## <a name="how-to-use-navigationview"></a>Verwenden von NavigationView

Es folgt ein einfaches Beispiel dafür, wie Sie NavigationView in Ihre App integrieren können.

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
                    Loaded="NavView_Loaded">
    <!-- Load NavigationViewItems in NavView_Loaded. -->

        <NavigationView.HeaderTemplate>
            <DataTemplate>
                <Grid>
                    <Grid.ColumnDefinitions>
                        <ColumnDefinition Width="Auto"/>
                        <ColumnDefinition/>
                    </Grid.ColumnDefinitions>
                    <TextBlock Style="{StaticResource TitleTextBlockStyle}"
                           FontSize="28"
                           VerticalAlignment="Center"
                           Margin="12,0"
                           Text="Welcome"/>
                    <CommandBar Grid.Column="1"
                            HorizontalAlignment="Right"
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

        <Frame x:Name="ContentFrame">
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
    NavView.MenuItems.Add(new NavigationViewItem()
        { Text = "Apps", Icon = new SymbolIcon(Symbol.AllApps), Tag = "apps" });
    NavView.MenuItems.Add(new NavigationViewItem()
        { Text = "Games", Icon = new SymbolIcon(Symbol.Video), Tag = "games" });
    NavView.MenuItems.Add(new NavigationViewItem()
        { Text = "Music", Icon = new SymbolIcon(Symbol.Audio), Tag = "music" });
    NavView.MenuItems.Add(new NavigationViewItemSeparator());
    NavView.MenuItems.Add(new NavigationViewItem()
        { Text = "My content", Icon = new SymbolIcon(Symbol.Folder), Tag = "content" });

    foreach (NavigationViewItem item in NavView.MenuItems)
    {
        if (item.Tag.ToString() == "play")
        {
            NavView.SelectedItem = item;
            break;
        }
    }
}

private void NavView_ItemInvoked(NavigationView sender, NavigationViewItemInvokedEventArgs args)
{
    if (args.IsSettingsInvoked == true)
    {
        ContentFrame.Navigate(typeof(SettingsPage));
    }
    else
    {
        switch ((args.InvokedItem as NavigationViewItem).Tag)
        {
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
}
```

## <a name="navigation"></a>Navigation

NavigationView zeigt in der Titelleiste Ihrer App nicht automatisch die Zurück-Schaltfläche an und fügt dem Zurück-Stapel auch keinen Inhalt hinzu. Das Steuerelement reagiert nicht automatisch auf Drücken der Zurück-Schaltfläche bzw. -Taste von Software oder Hardware. Im Abschnitt [Navigationsverlauf und Rückwärtsnavigation](../layout/navigation-history-and-backwards-navigation.md) finden Sie weitere Informationen zu diesem Thema und zum Hinzufügen von Unterstützung für die Navigation zu Ihrer App.


## <a name="related-topics"></a>Verwandte Themen

* [NavigationView-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview)
* [Master/Details](master-details.md)
* [Pivotsteuerelement](tabs-pivot.md)
* [Navigationsgrundlagen](../layout/navigation-basics.md)
 

 
