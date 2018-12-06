---
Description: Build UWP apps and custom/templated controls that support platform text scaling.
title: Textskalierung
label: Text scaling
template: detail.hbs
keywords: UWP, Text, Skalierung, Barrierefreiheit, "erleichterte Bedienung" anzeigen "Stellen Text größer", Benutzerinteraktion, Eingabe
ms.date: 08/02/2018
ms.topic: article
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: f81c435690c7bf17066be5f49de4994f146fc5c9
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8742557"
---
# <a name="text-scaling"></a>Textskalierung

![Beispiel für Text, die Skalierung von 100 % und 225 %](images/coretext/text-scaling-news-hero-small.png)  
*Beispiel für Text Skalierung in Windows 10 (100 % bis 225 %)*

## <a name="overview"></a>Übersicht

Lesen von Text auf einem Computerbildschirm (von mobilen Gerät, Laptop, desktop-Monitor auf dem großen Bildschirm von Surface Hub) kann für viele schwierig sein. Im Gegensatz dazu finden Sie einige Benutzer die Schriftgrade in apps und Websites verwendet, um größer als erforderlich sein.

Um sicherzustellen, dass Text lesbar ist wie für die IT. Benutzer möglich ist, bietet Windows die Möglichkeit für Benutzer relativen Schriftgrad über das Betriebssystem und die einzelnen Anwendungen zu ändern. Anstelle eine Bildschirmlupe-app (die in der Regel nur alles in einem Bereich des Bildschirms vergrößert und führt eine eigene Probleme hinsichtlich der Verwendbarkeit) verwenden, ändern Auflösung oder verlassen sich DPI-Skalierung (die alles basierend auf der Anzeige und typische Anzeige ändert Abstand), Benutzer können schnell zugreifen, eine Einstellung, um nur-Text, angefangen bei 100 % (die Standardgröße) Größe bis zu 225 %.

## <a name="support"></a>Support

Universelle Windows-Anwendungen (sowohl Standard und PWA), Text, die standardmäßig Skalierung unterstützen.

Wenn Ihre UWP-Anwendung benutzerdefinierte Steuerelemente, benutzerdefinierter Text, der Flächen, hartcodierten Steuerelement Höhen, älteren Frameworks oder 3rd Party-Frameworks enthält, müssen Sie wahrscheinlich einige Updates für eine konsistente und hilfreich Erfahrung für Benutzer sicherzustellen.  

DirectWrite, GDI und XAML-SwapChainPanels unterstützen nativ Text zu skalieren, keine während Win32-Unterstützung auf Menüs, Symbole und Symbolleisten begrenzt ist.  

<!-- If you want to support text scaling in your application with these frameworks, you’ll need to support the text scaling change event outlined below and provide alternative sizes for your UI and content.   -->

## <a name="user-experience"></a>Benutzerfreundlichkeit

Benutzer können Textanzeige anpassen mit der können den Text größer Schieberegler in den Einstellungen -> -> erleichterte Bedienung Vision/Bildschirm.

![Beispiel für Text, die Skalierung von 100 % und 225 %](images/coretext/text-scaling-settings-100-small.png)  
*Textanzeige von Einstellungen -> erleichterte Bedienung Vision/Bildschirm ->*

## <a name="ux-guidance"></a>Erläuterungen zur Benutzeroberfläche

Wie Text geändert wird, Steuerelemente und Container müssen auch die Größe und umbrechen, um den Text und das neue Layout aufzunehmen. Wie bereits erwähnt abhängig von der app-Framework und Plattform erfolgt Großteil der Arbeit für Sie. Die folgende UX-Richtlinien werden diese Fälle, in denen es nicht behandelt.

### <a name="use-the-platform-controls"></a>Verwenden Sie die Plattformsteuerelemente

Sagten wir dies bereits? Dabei ist zu wiederholen: Wenn möglich, müssen Sie die integrierten Steuerelemente mit den verschiedenen Windows-app-Frameworks bereitgestellten immer verwenden, um die umfassendste Benutzeroberfläche für die am wenigsten Zeit Aufwand erzielen.

Alle UWP-Textsteuerelemente z. B. den vollständigen Text Skalierung Erfahrung ohne Anpassung oder Templating unterstützen.

Hier ist ein Codeausschnitt aus einer einfachen UWP-app, die eine Reihe von standard-Text-Steuerelemente enthält:

``` xaml
<Grid>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="Auto" />
        <RowDefinition Height="Auto"/>
    </Grid.RowDefinitions>
    <TextBlock Grid.Row="0" 
                Style="{ThemeResource TitleTextBlockStyle}"
                Text="Text scaling test" 
                HorizontalTextAlignment="Center" />
    <Grid Grid.Row="1">
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="Auto"/>
            <ColumnDefinition Width="*"/>
            <ColumnDefinition Width="Auto"/>
        </Grid.ColumnDefinitions>
        <Image Grid.Column="0" 
                Source="Assets/StoreLogo.png" 
                Width="450" Height="450"/>
        <StackPanel Grid.Column="1" 
                    HorizontalAlignment="Center">
            <TextBlock TextWrapping="WrapWholeWords">
                The quick brown fox jumped over the lazy dog.
            </TextBlock>
            <TextBox PlaceholderText="Type something here" />
        </StackPanel>
        <Image Grid.Column="2" 
                Source="Assets/StoreLogo.png" 
                Width="450" Height="450"/>
    </Grid>
    <TextBlock Grid.Row="2" 
                Style="{ThemeResource TitleTextBlockStyle}"
                Text="Text scaling test footer" 
                HorizontalTextAlignment="Center" />
</Grid>
```

![Skalierung von 100 % und 225 % animierten text](images/coretext/text-scaling.gif)  
*Animierte Text skalieren*

### <a name="use-auto-sizing"></a>Verwenden Sie die automatische größenanpassung

Geben Sie absolute Größen für Ihre Steuerelemente. Wann immer möglich, können Sie die Plattform Ihre Steuerelemente automatisch basierend auf Benutzer- und geräteeinstellungen zu ändern.  

In diesem Codeausschnitt aus dem vorherigen Beispiel verwenden wir die `Auto` und `*` Breitenwerte für eine Gruppe von Rasterspalten und ermöglichen Sie die Plattform passen Sie das app-Layout basierend auf der Größe der Elemente innerhalb des Rasters.

``` xaml
<Grid.ColumnDefinitions>
    <ColumnDefinition Width="Auto"/>
    <ColumnDefinition Width="*"/>
    <ColumnDefinition Width="Auto"/>
</Grid.ColumnDefinitions>
```

### <a name="use-text-wrapping"></a>Verwenden Sie den Textumbruch

Um sicherzustellen, dass das Layout Ihrer App weniger flexibel und anpassbar wie möglich ist, Aktivieren von Textumbruch in jedem Steuerelement, das Text enthält (viele Steuerelemente nicht Textumbruch standardmäßig unterstützt).

Wenn Sie den Textumbruch nicht angeben, verwendet die Plattform andere Methoden, um das Layout, einschließlich Clipping anpassen (siehe vorherigen Beispiel).

Hier verwenden wir die `AcceptsReturn` und `TextWrapping` TextBox-Eigenschaften, um sicherzustellen, dass unsere Layout flexibel wie möglich ist.

``` xaml
<TextBox PlaceholderText="Type something here" 
          AcceptsReturn="True" TextWrapping="Wrap" />
```

![Animierter Text, die Skalierung von 100 % und 225 % mit Textumbruch](images/coretext/text-scaling-textwrap.gif)  
*Animierte Text Skalieren mit Textumbruch*

### <a name="specify-text-trimming-behavior"></a>Geben Sie Text Zuschneiden Verhalten

Wenn Textumbruch nicht das gewünschte Verhalten ist, können die meisten Textsteuerelemente entweder Ihr Text zuschneiden, oder geben Sie Ellipsen für das Text Zuschneiden Verhalten. Zuschneiden wird für Ellipsen bevorzugt, wie Ellipsen selbst Speicherplatz belegen.

> [!NOTE]
> Wenn Sie Sie den Text zu beschneiden müssen, clip am Ende der Zeichenfolge, die nicht am Anfang.

In diesem Beispiel zeigen wir, wie Sie Text in einem TextBlock zu beschneiden mithilfe der [TextTrimming](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.textblock.texttrimming) -Eigenschaft.

``` xaml
<TextBlock TextTrimming="Clip">
    The quick brown fox jumped over the lazy dog.
</TextBlock>
```

![Skalierung von 100 % und 225 % mit Text Zuschneiden Text](images/coretext/text-scaling-clipping-small.png)  
*Text skalieren mit Text Zuschneiden*

### <a name="use-a-tooltip"></a>Verwenden Sie eine QuickInfo

Wenn Sie Text zuschneiden, verwenden Sie QuickInfos, um den vollständigen Text für Ihre Benutzer bereitzustellen.

Hier fügen wir eine QuickInfo in ein TextBlock-Element, das Text umbrochen nicht unterstützt:

``` xaml
<TextBlock TextTrimming="Clip">
    <ToolTipService.ToolTip>
        <ToolTip Content="The quick brown fox jumped over the lazy dog."/>
    </ToolTipService.ToolTip>
    The quick brown fox jumped over the lazy dog.
</TextBlock>
```

### <a name="dont-scale-font-based-icons-or-symbols"></a>Nicht die Skalierung Schriftart schriftartbasierter Symbole oder Symbole

Wenn Sie Symbole Schriftart-basierte zur Betonung oder als Ergänzung zu verwenden, deaktivieren Sie auf diese Zeichen Skalierung aus.

Legen Sie die Eigenschaft [IsTextScaleFactorEnabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.control.istextscalefactorenabled) auf `false` für die meisten XAML-Steuerelemente.

### <a name="support-text-scaling-natively"></a>Unterstützung für Text nativ Skalierung

Behandeln Sie das [TextScaleFactorChanged](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.uisettings.textscalefactorchanged) UISettings System-Ereignis in Ihren benutzerdefinierten Framework Steuerelemente. Dieses Ereignis wird jedes Mal ausgelöst, wenn der Benutzer den Skalierungsfaktor Text auf ihrem System festlegt.

## <a name="summary"></a>Zusammenfassung

Dieses Thema enthält eine Übersicht über Text-Unterstützung in Windows-Skalierung und enthält (UX) und Entwickler Richtlinien zum Anpassen der Benutzeroberfläche.

## <a name="related-articles"></a>Verwandte Artikel

### <a name="api-reference"></a>API-Referenz

- [IsTextScaleFactorEnabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.control.istextscalefactorenabled)
- [TextScaleFactorChanged](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.uisettings.textscalefactorchanged)
