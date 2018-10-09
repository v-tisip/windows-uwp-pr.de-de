---
author: Jwmsft
Description: Provides a list by function of some of the controls that you can use in your apps.
title: Steuerelemente nach Funktion
ms.assetid: 8DB4347B-91D6-4659-91F2-80ECF7BBB596
label: Controls by function
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 0840bab2e039ec55ea4070f8dad39c0ae4e74bbc
ms.sourcegitcommit: 49aab071aa2bd88f1c165438ee7e5c854b3e4f61
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2018
ms.locfileid: "4464853"
---
# <a name="controls-by-function"></a>Steuerelemente nach Funktion

Das XAML-Benutzeroberflächenframework für Windows bietet eine umfangreiche Bibliothek von Steuerelementen, welche die Entwicklung von Benutzeroberflächen unterstützen. Einige dieser Steuerelemente weisen eine visuelle Darstellung auf. Andere fungieren als Container für andere Steuerelemente oder Inhalte (z.B. Bilder und Medien). 

Laden Sie das [Beispiel für XAML-UI-Grundlagen](http://go.microsoft.com/fwlink/p/?LinkId=619992) herunter, um sich zahlreiche Windows-UI-Steuerelemente in Aktion anzusehen.

<table>
<th align="left">XAML-Steuerelementekatalog<th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p>Wenn Sie die <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> -app installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/NavigationView">die app zu öffnen und finden Sie unter der NavigationView in Aktion zu sehen</a> </p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics">Erwerben Sie den Quellcode (GitHub)</a></li>
    </ul>
</td>
</tr>
</table>


Die folgende nach Funktionen geordnete Liste enthält die allgemeinen XAML-Steuerelemente, die Sie in Ihrer App verwenden können.

## <a name="appbars-and-commands"></a>App-Leisten und -Befehle

### <a name="app-bar"></a>App-Leiste
Eine Symbolleiste für anwendungsspezifische Befehle. Siehe Befehlsleiste.

Referenz: [AppBar](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbar.aspx) 

### <a name="app-bar-button"></a>App-Leistenschaltfläche
Eine Schaltfläche, die Befehle in Form einer App-Leiste anzeigt.

![Symbole für App-Leistenschaltflächen](images/controls/app-bar-buttons.png) 

Referenz: [AppBarButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarbutton.aspx), [SymbolIcon](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.symbolicon.aspx), [BitmapIcon](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.bitmapicon.aspx), [FontIcon](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.fonticon.aspx), [PathIcon](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pathicon.aspx) 

Design und Vorgehensweise: [App-Leiste und Befehlsleiste](app-bars.md) 

Beispielcode: [Beispiel für XAML-Befehle](http://go.microsoft.com/fwlink/p/?LinkId=620019)

### <a name="app-bar-separator"></a>Trennzeichen der App-Leiste
Trennt Befehlsgruppen in einer Befehlsleiste grafisch.

Referenz: [AppBarSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarseparator.aspx) 

Beispielcode: [Beispiel für XAML-Befehle](http://go.microsoft.com/fwlink/p/?LinkId=620019)

### <a name="app-bar-toggle-button"></a>Umschaltfläche der App-Leiste
Eine Schaltfläche zum Wechseln zwischen den Befehlen in einer Befehlsleiste.

Referenz: [AppBarToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbartogglebutton.aspx) 

Beispielcode: [Beispiel für XAML-Befehle](http://go.microsoft.com/fwlink/p/?LinkId=620019)

### <a name="command-bar"></a>Befehlsleiste
Eine spezielle App-Leiste zum Ändern der Größe von Schaltflächenelementen auf der App-Leiste.

![Befehlsleistensteuerelement](images/command-bar-compact.png)

```xaml
<CommandBar>
    <AppBarButton Icon="Back" Label="Back" Click="AppBarButton_Click"/>
    <AppBarButton Icon="Stop" Label="Stop" Click="AppBarButton_Click"/>
    <AppBarButton Icon="Play" Label="Play" Click="AppBarButton_Click"/>
</CommandBar>
```
Referenz: [CommandBar](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.commandbar.aspx) 

Design und Vorgehensweise: [App-Leiste und Befehlsleiste](app-bars.md)

Beispielcode: [Beispiel für XAML-Befehle](http://go.microsoft.com/fwlink/p/?LinkId=620019)

## <a name="buttons"></a>Schaltflächen

### <a name="button"></a>Button
Ein Steuerelement, das auf Benutzereingaben reagiert und ein **Click**-Ereignis auslöst.

![Standardschaltfläche](images/controls/button.png)

```xaml
<Button x:Name="button1" Content="Button" 
        Click="Button_Click" />
```

Referenz: [Button](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.button.aspx) 

Design und Vorgehensweise: [Richtlinien für Schaltflächen](buttons.md) 

### <a name="hyperlink"></a>Hyperlink
Siehe „Linkschaltfläche“.

### <a name="hyperlink-button"></a>Linkschaltfläche
Eine Schaltfläche, die als markierter Text dargestellt wird und den angegebenen URI in einem Browser öffnet.

![Linkschaltfläche](images/controls/hyperlink-button.png)

```xaml
<HyperlinkButton Content="www.microsoft.com" 
                 NavigateUri="http://www.microsoft.com"/>
```

Referenz: [HyperlinkButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.hyperlinkbutton.aspx) 

Design und Vorgehensweise: [Richtlinien für Hyperlinks](hyperlinks.md)

### <a name="repeat-button"></a>Wiederholungsschaltfläche
Eine Schaltfläche, die ihr **Click**-Ereignis auslöst, das andauert, solange die Schaltfläche betätigt wird. 

![Ein Schaltflächen-Steuerelement zum Wiederholen](images/controls/repeat-button.png) 

```xaml
<RepeatButton x:Name="repeatButton1" Content="Repeat Button" 
              Click="RepeatButton_Click" />
```

Referenz: [RepeatButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.primitives.repeatbutton.aspx) 

Design und Vorgehensweise: [Richtlinien für Schaltflächen](buttons.md) 

## <a name="collectiondata-controls"></a>Sammlungs-/Datensteuerelemente

### <a name="flip-view"></a>Flip-Ansicht
Ein Steuerelement, das eine Sammlung von Elementen darstellt, durch die der Benutzer jeweils einzeln blättern kann.

```xaml
<FlipView x:Name="flipView1" SelectionChanged="FlipView_SelectionChanged">
    <Image Source="Assets/Logo.png" />
    <Image Source="Assets/SplashScreen.png" />
    <Image Source="Assets/SmallLogo.png" />
</FlipView>
```

Referenz: [FlipView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.flipview.aspx) 

Design und Vorgehensweise: [Richtlinien für Flip-Ansicht](flipview.md) 

### <a name="grid-view"></a>Rasteransicht
Ein Steuerelement, das eine Sammlung von Elementen in Zeilen und Spalten darstellt, für die ein vertikaler Bildlauf durchgeführt werden kann.

```xaml
<GridView x:Name="gridView1" SelectionChanged="GridView_SelectionChanged">
    <x:String>Item 1</x:String>
    <x:String>Item 2</x:String>
</GridView>
```

Referenz: [GridView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.gridview.aspx) 

Design und Vorgehensweise: [Listen](lists.md) 

Beispielcode: [ListView-Beispiel](http://go.microsoft.com/fwlink/p/?LinkId=619900)

### <a name="items-control"></a>Elementsteuerelement
Ein Steuerelement, das eine Sammlung von Elementen auf einer Benutzeroberfläche darstellt, die durch eine Datenvorlage angegeben wird. 

```xaml
<ItemsControl/>
```

Referenz: [ItemsControl](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.aspx) 

### <a name="list-view"></a>Listenansicht
Ein Steuerelement, das eine Sammlung von Elementen in einer Liste darstellt, für die ein horizontaler Bildlauf durchgeführt werden kann.

```xaml
<ListView x:Name="listView1" SelectionChanged="ListView_SelectionChanged">
    <x:String>Item 1</x:String>
    <x:String>Item 2</x:String>
</ListView>
```

Referenz: [ListView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.listview.aspx) 

Design und Vorgehensweise: [Listen](lists.md) 

Beispielcode: [ListView-Beispiel](http://go.microsoft.com/fwlink/p/?LinkId=619900)

## <a name="date-and-time-controls"></a>Datums- und Uhrzeitsteuerelemente

### <a name="calendar-date-picker"></a>Kalenderdatumsauswahl
Ein Steuerelement, mit dem Benutzer ein Datum über eine Kalender-Dropdownanzeige auswählen können.

![Kalenderdatumsauswahl mit offener Kalenderansicht](images/controls/calendar-date-picker-open.png)

```xaml
<CalendarDatePicker/>
```

Referenz: [CalendarDatePicker](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.aspx) 

Design und Vorgehensweise: [Richtlinien für Datums- und Uhrzeitsteuerelemente](date-and-time.md)
 
### <a name="calendar-view"></a>Kalenderansicht
Eine konfigurierbare Kalenderanzeige, in der Benutzer ein einzelnes Datum oder mehrere Daten auswählen können.

```xaml
<CalendarView/>
```

Referenz: [CalendarView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendarview.aspx) 

Design und Vorgehensweise: [Richtlinien für Datums- und Uhrzeitsteuerelemente](date-and-time.md) 

### <a name="date-picker"></a>Datumsauswahl
Ein Steuerelement, mit dem ein Benutzer ein Datum auswählen kann.

![Datumsauswahlsteuerelement](images/controls/date-picker.png)

```xaml
<DatePicker Header="Arrival Date"/>
```

Referenz: [DatePicker](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.datepicker.aspx) 

Design und Vorgehensweise: [Richtlinien für Datums- und Uhrzeitsteuerelemente](date-and-time.md)
 
### <a name="time-picker"></a>Uhrzeitauswahl
Ein Steuerelement, mit dem ein Benutzer einen Zeitwert auswählen kann.

![TimePicker-Steuerelement](images/controls/time-picker.png) 

```xaml
<TimePicker Header="Arrival Time"/>
```

Referenz: [TimePicker](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.timepicker.aspx) 

Design und Vorgehensweise: [Richtlinien für Datums- und Uhrzeitsteuerelemente](date-and-time.md)

## <a name="flyouts"></a>Flyouts

### <a name="context-menu"></a>Kontextmenü
Siehe „Menü-Flyout“ und „Popupmenü“.

### <a name="flyout"></a>Flyout
Zeigt eine Meldung an, die einen Benutzereingriff erfordert. (Im Gegensatz zu einem Dialogfeld wird von einem Flyout kein separates Fenster erstellt und keine Benutzerinteraktion blockiert.)

![Flyout-Steuerelement](images/controls/flyout.png)

```xaml
<Flyout>
    <StackPanel>
        <TextBlock Text="All items will be removed. Do you want to continue?"/>
        <Button Click="DeleteConfirmation_Click" Content="Yes, empty my cart"/>
    </StackPanel>
</Flyout>
```

Referenz: [Flyout](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.flyout.aspx) 

Design und Vorgehensweise: [Flyouts](dialogs-and-flyouts/flyouts.md) 

### <a name="menu-flyout"></a>Menü-Flyout
Zeigt vorübergehend eine Liste der Befehle oder Optionen im Kontext der Benutzeraktion an.

![Menü-Flyoutsteuerelement](images/controls/menu-flyout.png) 

```xaml
<MenuFlyout>
    <MenuFlyoutItem Text="Reset" Click="Reset_Click"/>
    <MenuFlyoutSeparator/>
    <ToggleMenuFlyoutItem Text="Shuffle" 
                          IsChecked="{Binding IsShuffleEnabled, Mode=TwoWay}"/>
    <ToggleMenuFlyoutItem Text="Repeat" 
                          IsChecked="{Binding IsRepeatEnabled, Mode=TwoWay}"/>
</MenuFlyout>
```

Referenz: [MenuFlyout](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyout.aspx), [MenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutitem.aspx), [MenuFlyoutSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutseparator.aspx), [ToggleMenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.togglemenuflyoutitem.aspx) 

Design und Vorgehensweise: [Menüs und Kontextmenüs](menus.md) 

Beispielcode: [Beispiel für XAML-Kontextmenü](http://go.microsoft.com/fwlink/p/?LinkId=620021)

### <a name="popup-menu"></a>Popupmenü
Ein benutzerdefiniertes Menü mit von Ihnen angegebenen Befehlen.

Referenz: [PopupMenu](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.popups.popupmenu.aspx) 

Design und Vorgehensweise: [Dialogfelder](dialogs-and-flyouts/dialogs.md) 

### <a name="tooltip"></a>QuickInfo
Ein Popupfenster, das Informationen zu einem Element anzeigt. 
 
![QuickInfo-Steuerelement](images/controls/tool-tip.png)

```xaml
<Button Content="Button" Click="Button_Click" 
        ToolTipService.ToolTip="Click to perform action" />
```

Referenz: [ToolTip](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.tooltip.aspx), [ToolTipService](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.tooltipservice.aspx) 

Design und Vorgehensweise: Richtlinien für QuickInfos 

## <a name="images"></a>Bilder

### <a name="image"></a>Image
Ein Steuerelement, das ein Bild darstellt.

```xaml
<Image Source="Assets/Logo.png" />
```

Referenz: [Image](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.image.aspx) 

Design und Vorgehensweise: [Image und ImageBrush](images-imagebrushes.md) 

Beispielcode: [Beispiel für XAML-Bilder](http://go.microsoft.com/fwlink/p/?linkid=226867)

## <a name="graphics-and-ink"></a>Grafiken und Freihandstriche

### <a name="inkcanvas"></a>InkCanvas
Ein Steuerelement, das Freihandstriche empfängt und anzeigt.

```xaml
<InkCanvas/>
```

Referenz: [InkCanvas](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.inkcanvas.aspx) 

### <a name="shapes"></a>Formen
Verschiedene grafische Speichermodusobjekte, die als Ellipsen, Rechtecke, Linien, Bézierpfade usw. dargestellt werden können.

![Ein Polygon](images/controls/shapes-polygon.png) 
![Ein Pfad](images/controls/shapes-path.png) 

```xaml
<Ellipse/>
<Path/>
<Rectangle/>
```

Referenz: [Shapes](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.shapes.shape.aspx) 

So wird's gemacht: [Zeichnen von Formen](../../graphics/drawing-shapes.md) 

Beispielcode: [Beispiel für vektorbasierte XAML-Zeichnung](http://go.microsoft.com/fwlink/p/?linkid=226866)

## <a name="layout-controls"></a>Layoutsteuerelemente

### <a name="border"></a>Rahmen
Ein Containersteuerelement, das einen Rahmen, einen Hintergrund oder beides um ein anderes Objekt herum zeichnet.

![Ein Rahmen um zwei Rechtecke](images/controls/border.png) 

```xaml
<Border BorderBrush="Blue" BorderThickness="4" 
        Height="108" Width="64" 
        Padding="8" CornerRadius="4">
    <Canvas>
        <Rectangle Fill="Orange"/>
        <Rectangle Fill="Green" Margin="0,44"/>
    </Canvas>
</Border>
```

Referenz: [Border](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.border.aspx)

### <a name="canvas"></a>Canvas
Ein Layoutpanel, das die absolute Positionierung untergeordneter Elemente relativ zur oberen linken Ecke der Canvas unterstützt.
 
![Canvas-Layoutpanel](images/controls/canvas.png) 

```xaml
<Canvas Width="120" Height="120">
    <Rectangle Fill="Red"/>
    <Rectangle Fill="Blue" Canvas.Left="20" Canvas.Top="20"/>
    <Rectangle Fill="Green" Canvas.Left="40" Canvas.Top="40"/>
    <Rectangle Fill="Orange" Canvas.Left="60" Canvas.Top="60"/>
</Canvas>
```

Referenz: [Canvas](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.canvas.aspx)
 
### <a name="grid"></a>Raster
Ein Layoutpanel, das die Anordnung von untergeordneten Elementen in Zeilen und Spalten unterstützt.

![Raster-Layoutpanel](images/controls/grid.png) 

```xaml
<Grid>
    <Grid.RowDefinitions>
        <RowDefinition Height="50"/>
        <RowDefinition Height="50"/>
    </Grid.RowDefinitions>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="50"/>
        <ColumnDefinition Width="50"/>
    </Grid.ColumnDefinitions>
    <Rectangle Fill="Red"/>
    <Rectangle Fill="Blue" Grid.Row="1"/>
    <Rectangle Fill="Green" Grid.Column="1"/>
    <Rectangle Fill="Orange" Grid.Row="1" Grid.Column="1"/>
</Grid>
```

Referenz: [Grid](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.grid.aspx)
 
### <a name="panning-scroll-viewer"></a>Verschiebungs-Bildlaufanzeige
Siehe „Bildlaufanzeige“.

### <a name="relativepanel"></a>RelativePanel
Ein Bereich, in dem Sie untergeordnete Objekte relativ zueinander oder in Relation zum übergeordneten Objekt positionieren und ausrichten können.

![RelativePanel-Layoutpanel](images/controls/relative-panel.png) 

```xaml
<RelativePanel>
    <TextBox x:Name="textBox1" RelativePanel.AlignLeftWithPanel="True"/>
    <Button Content="Submit" RelativePanel.Below="textBox1"/>
</RelativePanel>
```

Referenz: [RelativePanel](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.relativepanel.aspx)

### <a name="scroll-bar"></a>Bildlaufleiste
Siehe Bildlaufanzeige. (ScrollBar ist ein Element von ScrollViewer. Es wird normalerweise nicht als eigenständiges Steuerelement verwendet.)

Referenz: [ScrollBar](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.primitives.scrollbar.aspx)
 
### <a name="scroll-viewer"></a>Bildlaufanzeige
Ein Containersteuerelement, mit dem der Benutzer Inhalte verschieben und vergrößern/verkleinern kann.

```xaml
<ScrollViewer ZoomMode="Enabled" MaxZoomFactor="10" 
              HorizontalScrollMode="Enabled" 
              HorizontalScrollBarVisibility="Visible"
              Height="200" Width="200">
    <Image Source="Assets/Logo.png" Height="400" Width="400"/>
</ScrollViewer>
```

Referenz: [ScrollViewer](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.scrollviewer.aspx)

Design und Vorgehensweise: [Bildlaufleisten](scroll-controls.md) 

Beispielcode: [Beispiel für XAML-Bildlauf, -Verschiebung und -Zoom](http://go.microsoft.com/fwlink/p/?linkid=238577)

### <a name="stack-panel"></a>StackPanel
Ein Layoutpanel, das untergeordnete Elemente in einer einzelnen Zeile anordnet. Die Zeile kann horizontal oder vertikal ausgerichtet werden.

![StackPanel-Layoutsteuerelement](images/controls/stack-panel.png) 

```xaml
<StackPanel>
    <Rectangle Fill="Red"/>
    <Rectangle Fill="Blue"/>
    <Rectangle Fill="Green"/>
    <Rectangle Fill="Orange"/>
</StackPanel>
```

Referenz: [StackPanel](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.stackpanel.aspx)
 
### <a name="variablesizedwrapgrid"></a>VariableSizedWrapGrid
Ein Layoutpanel, das die Anordnung von untergeordneten Elementen in Zeilen und Spalten unterstützt. Jedes untergeordnete Element kann sich über mehrere Zeilen und Spalten erstrecken.

![Umbruchraster-Layoutpanel mit variabler Größe](images/controls/variable-sized-wrap-grid.png) 

```xaml
<VariableSizedWrapGrid MaximumRowsOrColumns="3" ItemHeight="44" ItemWidth="44">
    <Rectangle Fill="Red"/>
    <Rectangle Fill="Blue" Height="80" 
               VariableSizedWrapGrid.RowSpan="2"/>
    <Rectangle Fill="Green" Width="80" 
               VariableSizedWrapGrid.ColumnSpan="2"/>
    <Rectangle Fill="Orange" Height="80" Width="80" 
               VariableSizedWrapGrid.RowSpan="2" 
               VariableSizedWrapGrid.ColumnSpan="2"/>
</VariableSizedWrapGrid>
```

Referenz: [VariableSizedWrapGrid](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.variablesizedwrapgrid.aspx)

### <a name="viewbox"></a>Viewbox
Ein Containersteuerelement, das seinen Inhalt auf eine angegebene Größe skaliert.

![Viewbox-Steuerelement](images/controls/view-box.png) 

```xaml
<Viewbox MaxWidth="25" MaxHeight="25">
    <Image Source="Assets/Logo.png"/>
</Viewbox>
<Viewbox MaxWidth="75" MaxHeight="75">
    <Image Source="Assets/Logo.png"/>
</Viewbox>
<Viewbox MaxWidth="150" MaxHeight="150">
    <Image Source="Assets/Logo.png"/>
</Viewbox>
```

Referenz: [Viewbox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.viewbox.aspx)
 
### <a name="zooming-scroll-viewer"></a>Zoombildlaufanzeige
Siehe „Bildlaufanzeige“.

## <a name="media-controls"></a>Mediensteuerelemente

### <a name="audio"></a>Audio
Siehe „Medienelement“.

### <a name="media-element"></a>Medienelement
Ein Steuerelement, das Audio- und Videoinhalte wiedergibt.

```xaml
<MediaElement x:Name="myMediaElement"/>
```

Referenz: [MediaElement](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.mediaelement.aspx) 

Design und Vorgehensweise: [Richtlinien für Mediaplayer](media-playback.md)

### <a name="mediatransportcontrols"></a>MediaTransportControls
Ein Steuerelement, das Wiedergabesteuerelemente für eine „MediaElement“-Klasse bereitstellt.

![Medienelement mit Transportsteuerelementen](images/controls/media-transport-controls.png) 

```xaml
<MediaTransportControls MediaElement="myMediaElement"/>
```

Referenz: [MediaTransportControls](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.mediatransportcontrols.aspx) 

Design und Vorgehensweise: [Richtlinien für Mediaplayer](media-playback.md) 

Beispielcode: [Beispiel für die Steuerelemente für den Medientransport](http://go.microsoft.com/fwlink/p/?LinkId=620023)

### <a name="video"></a>Video
Siehe „Medienelement“.

## <a name="navigation"></a>Navigation

### <a name="navigationview"></a>NavigationView

Eine anpassungsfähige Container und flexible Navigationsmodell, der im linken Navigationsbereich, oberen Navigationsleiste und registerkartenmuster implementiert.

Referenz: [NavigationView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview)

Design und Vorgehensweise: [Handbuch für NavigationView-Steuerelement](navigationview.md)

### <a name="splitview"></a>SplitView

Ein Containersteuerelement mit zwei Ansichten: einer Ansicht für den Hauptinhalt und einer weiteren Ansicht, die in der Regel für ein Navigationsmenü verwendet wird.

![Steuerelement für geteilte Ansicht](images/controls/split-view.png) 

```xaml
<SplitView>
    <SplitView.Pane>
        <!-- Menu content -->
    </SplitView.Pane>
    <SplitView.Content>
        <!-- Main content -->
    </SplitView.Content>
</SplitView>
```

Referenz: [SplitView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.splitview.aspx) 

Design und Vorgehensweise: [Richtlinien für das Steuerelement für die geteilte Ansicht](split-view.md)

### <a name="web-view"></a>Webansicht

Ein Containersteuerelement, das Webinhalt hostet.

```xaml
<WebView x:Name="webView1" Source="http://dev.windows.com" 
         Height="400" Width="800"/>
```

Referenz: [WebView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx) 

Design und Vorgehensweise: Richtlinien für Webansichten 

Beispielcode: [Beispiel für XAML-WebView-Steuerelement](http://go.microsoft.com/fwlink/p/?linkid=238582)

### <a name="semantic-zoom"></a>Semantischer Zoom

Ein Containersteuerelement, das es dem Benutzer ermöglicht, zwischen zwei Ansichten einer Sammlung zu zoomen.

```xaml
<SemanticZoom>
    <ZoomedInView>
        <GridView></GridView>
    </ZoomedInView>
    <ZoomedOutView>
        <GridView></GridView>
    </ZoomedOutView>
</SemanticZoom>
```

Referenz: [SemanticZoom](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.semanticzoom.aspx) 

Design und Vorgehensweise: [Richtlinien für den semantischen Zoom](semantic-zoom.md)

Beispielcode: [Beispiel für XAML-GridView-Gruppierung und -SemanticZoom](http://go.microsoft.com/fwlink/p/?linkid=226564)

## <a name="progress-controls"></a>Statussteuerelemente

### <a name="progress-bar"></a>Statusleiste
Ein Steuerelement, das den Fortschritt durch Anzeigen einer Leiste angibt.

![Statusleistensteuerelement](images/controls/progress-bar-determinate.png)

Eine Fortschrittsleiste, die einen bestimmten Wert anzeigt.

```xaml
<ProgressBar x:Name="progressBar1" Value="50" Width="100"/>
```

![Steuerelement für unbestimmte Statusanzeige](images/controls/progress-bar-indeterminate.png)

Eine Fortschrittsleiste, die einen unbestimmten Fortschritt anzeigt.

```xaml
<ProgressBar x:Name="indeterminateProgressBar1" IsIndeterminate="True" Width="100"/>
```

Referenz: [ProgressBar](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.progressbar.aspx) 

Design und Vorgehensweise: [Richtlinien für Statussteuerelemente](progress-controls.md) 

### <a name="progress-ring"></a>Statusring
Ein Steuerelement, das den Status durch Anzeigen eines Rings angibt. 

![Statusringsteuerelement](images/controls/progress-ring.png) 

```xaml
<ProgressRing x:Name="progressRing1" IsActive="True"/>
```

Referenz: [ProgressRing](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.progressring.aspx) 

Design und Vorgehensweise: [Richtlinien für Statussteuerelemente](progress-controls.md) 

## <a name="text-controls"></a>Textsteuerelemente

### <a name="auto-suggest-box"></a>Feld mit automatischen Vorschlägen
Ein Texteingabefeld, das Text vorschlägt, während der Benutzer Zeichen eingibt.

![Feld mit automatischen Vorschlägen für die Suche](images/controls/auto-suggest-box.png) 

Referenz: [AutoSuggestBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestbox.aspx)

Design und Vorgehensweise: [Textsteuerelemente](text-controls.md), [Richtlinien für Feldsteuerelement mit automatischen Vorschlägen](auto-suggest-box.md)

Beispielcode: [Beispiel für AutoSuggestBox-Migration](http://go.microsoft.com/fwlink/p/?LinkId=619996)

### <a name="multi-line-text-box"></a>Mehrzeiliges Textfeld
Siehe „Textfeld“.

### <a name="password-box"></a>Kennwortfeld
Ein Steuerelement für die Kennworteingabe.

 ![Ein Kennwortfeld](images/controls/password-box.png)

```xaml
<PasswordBox x:Name="passwordBox1" 
             PasswordChanged="PasswordBox_PasswordChanged" />
```

Referenz: [PasswordBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.aspx) 

Design und Vorgehensweise: [Textsteuerelemente](text-controls.md), [Richtlinien für Kennwortfelder](password-box.md) 

Beispielcode: [Beispiel für die XAML-Textanzeige](http://go.microsoft.com/fwlink/p/?linkid=238579), [Beispiel für die XAML-Textbearbeitung](http://go.microsoft.com/fwlink/p/?linkid=251417)

### <a name="rich-edit-box"></a>Rich-Edit-Feld
Ein Steuerelement, mit dem der Benutzer Rich-Text-Dokumente mit Inhalten wie formatiertem Text, Links und Bildern bearbeiten kann.

```xaml
<RichEditBox />
```

Referenz: [RichEditBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.aspx) 

Design und Vorgehensweise: [Textsteuerelemente](text-controls.md), [Richtlinien für RichEditBox-Steuerelement](rich-edit-box.md)

Beispielcode: [Beispiel für XAML-Text](http://go.microsoft.com/fwlink/p/?linkid=238578)

### <a name="search-box"></a>Suchfeld
Siehe „Feld mit automatischen Vorschlägen“.

### <a name="single-line-text-box"></a>Einzeiliges Textfeld
Siehe „Textfeld“.

### <a name="static-textparagraph"></a>Statischer Text/Absatz
Siehe „Textblock“.

### <a name="text-block"></a>Textblock
Ein Steuerelement, das Text angezeigt.

![Textblocksteuerelement](images/controls/text-block.png) 

```xaml
<TextBlock x:Name="textBlock1" Text="I am a TextBlock"/>
```

Referenz: [TextBlock](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.aspx), [RichTextBlock](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richtextblock.aspx) 

Design und Vorgehensweise: [Textsteuerelemente](text-controls.md), [TextBlock](text-block.md), [Richtlinie für Rich-Text-Blocksteuerelemente](rich-text-block.md)

Beispielcode: [Beispiel für XAML-Text](http://go.microsoft.com/fwlink/p/?linkid=238578)

### <a name="text-box"></a>Textfeld
Ein einzeiliges oder mehrzeiliges Nur-Text-Feld.

![Textfeldsteuerelement](images/controls/text-box.png) 

```xaml
<TextBox x:Name="textBox1" Text="I am a TextBox" 
         TextChanged="TextBox_TextChanged"/>
```

Referenz: [TextBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textbox.aspx) 

Design und Vorgehensweise: [Textsteuerelemente](text-controls.md), [TextBox](text-box.md) 

Beispielcode: [Beispiel für XAML-Text](http://go.microsoft.com/fwlink/p/?linkid=238578)

## <a name="selection-controls"></a>Auswahlsteuerelemente

### <a name="check-box"></a>Kontrollkästchen
Ein Steuerelement, das der Benutzer aktivieren und deaktivieren kann.

![Die drei Zustände eines Kontrollkästchens](images/templates-checkbox-states-default.png)

```xaml
<CheckBox x:Name="checkbox1" Content="CheckBox" 
          Checked="CheckBox_Checked"/>
```

Referenz: [CheckBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.checkbox.aspx) 

Design und Vorgehensweise: [Richtlinien für Kontrollkästchen](checkbox.md) 

### <a name="combo-box"></a>Kombinationsfeld
Eine Dropdownliste mit Elementen, in der ein Benutzer eine Auswahl treffen kann.

![Offenes Kombinationsfeld](images/controls/combo-box-open.png) 

```xaml
<ComboBox x:Name="comboBox1" Width="100"
          SelectionChanged="ComboBox_SelectionChanged">
    <x:String>Item 1</x:String>
    <x:String>Item 2</x:String>
    <x:String>Item 3</x:String>
</ComboBox>
```

Referenz: [ComboBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.combobox.aspx) 

Design und Vorgehensweise: [Listen](lists.md) 

### <a name="list-box"></a>Listenfeld
Ein Steuerelement, das eine Inlineliste mit Elementen darstellt, aus der ein Benutzer eine Auswahl treffen kann. 

![Listenfeldsteuerelement](images/controls/list-box.png)

```xaml
<ListBox x:Name="listBox1" Width="100"
         SelectionChanged="ListBox_SelectionChanged">
    <x:String>Item 1</x:String>
    <x:String>Item 2</x:String>
    <x:String>Item 3</x:String>
</ListBox>
```

Referenz: [ListBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.listbox.aspx) 

Design und Vorgehensweise: [Listen](lists.md) 

### <a name="radio-button"></a>Optionsfeld
Ein Steuerelement, das es einem Benutzer ermöglicht, eine einzelne Option aus einer Gruppe von Optionen auszuwählen. Gruppierte Optionsfelder schließen sich gegenseitig aus.

![Optionsfeldsteuerelemente](images/controls/radio-button.png)

```xaml
<RadioButton x:Name="radioButton1" Content="RadioButton 1" GroupName="Group1" 
             Checked="RadioButton_Checked"/>
<RadioButton x:Name="radioButton2" Content="RadioButton 2" GroupName="Group1" 
             Checked="RadioButton_Checked" IsChecked="True"/>
<RadioButton x:Name="radioButton3" Content="RadioButton 3" GroupName="Group1" 
             Checked="RadioButton_Checked"/>
```

Referenz: [RadioButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.radiobutton.aspx) 

Design und Vorgehensweise: [Richtlinien für Optionsfelder](radio-button.md)
 
### <a name="slider"></a>Schieberegler
Ein Steuerelement, über das der Benutzer aus einer Reihe von Werten auswählen kann, indem er ein Schiebereglersteuerelement über einen Bereich verschiebt.

![Schiebereglersteuerelement](images/controls/slider.png)

```xaml
<Slider x:Name="slider1" Width="100" ValueChanged="Slider_ValueChanged" />
```

Referenz: [Slider](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.slider.aspx) 

Design und Vorgehensweise: [Richtlinien für Schieberegler](slider.md) 

### <a name="toggle-button"></a>Umschalter
Eine Schaltfläche, mit der zwischen zwei Zuständen gewechselt werden kann.

```xaml
<ToggleButton x:Name="toggleButton1" Content="Button" 
              Checked="ToggleButton_Checked"/>
```

Referenz: [ToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.primitives.togglebutton.aspx)

Design und Vorgehensweise: [Richtlinien für Umschaltsteuerelemente](toggles.md) 

### <a name="toggle-switch"></a>Umschalter
Ein Schalter, mit dem zwischen zwei Zuständen hin und her geschaltet werden kann.

![Umschaltersteuerelement](images/controls/toggle-switch.png) 

```xaml
<ToggleSwitch x:Name="toggleSwitch1" Header="ToggleSwitch" 
              OnContent="On" OffContent="Off" 
              Toggled="ToggleSwitch_Toggled"/>
```

Referenz: [ToggleSwitch](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.toggleswitch.aspx) 

Design und Vorgehensweise: [Richtlinien für Umschaltsteuerelemente](toggles.md) 
