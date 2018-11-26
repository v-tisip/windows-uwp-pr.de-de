---
Description: Build UWP apps and custom/templated controls that support platform text scaling.
title: Textskalierung
label: Text scaling
template: detail.hbs
keywords: UWP, Text, Skalierung, Eingabehilfen, "erleichterte Bedienung", "Stellen Text größer", Benutzerinteraktion, Eingabe anzeigen
ms.date: 08/02/2018
ms.topic: article
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: f81c435690c7bf17066be5f49de4994f146fc5c9
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7694047"
---
# <a name="text-scaling"></a>Textskalierung

![Beispiel für Text, die Skalierung von 100 % auf 225 %](images/coretext/text-scaling-news-hero-small.png)  
*Beispiel für Text, die Skalierung in Windows 10 (100 % bis 225 %)*

## <a name="overview"></a>Übersicht

Lesen von Text auf einem Computerbildschirm (von mobilen Gerät, Laptop, desktop-Monitor auf den riesigen Bildschirm von Surface Hub) kann für viele Benutzer schwierig sein. Im Gegensatz dazu finden Sie einige Benutzer die Schriftgrade in apps und Websites verwendet, um größer als erforderlich sein.

Um sicherzustellen, dass Text lesbar ist wie die größtmögliche Anzahl von Benutzern möglich ist, bietet Windows die Möglichkeit für Benutzer, die relative Schriftgröße für das Betriebssystem und die einzelnen Anwendungen zu ändern. Anstatt mithilfe einer Bildschirmlupe-app (was in der Regel nur alles in einem Bereich des Bildschirms vergrößert und führt eine eigene Probleme hinsichtlich der Verwendbarkeit), das Ändern der Auflösung oder verlassen sich DPI-Skalierung (die alles basierend auf der Anzeige und typische Anzeige Größe Abstand), Benutzer können schnell zugreifen, eine Einstellung, um nur-Text, angefangen bei 100 % (die Standardgröße) Größe bis zu 225 %.

## <a name="support"></a>Support

Universelle Windows-Anwendungen (sowohl Standard und PWA), Text standardmäßig Skalierung zu unterstützen.

Wenn Ihre UWP-Anwendung benutzerdefinierte Steuerelemente, benutzerdefinierter Text Flächen, hartcodierten Steuerelement Höhen, älteren Frameworks oder 3rd Party-Frameworks enthält, müssen Sie wahrscheinlich einige Updates für eine konsistente und nützlich Erfahrung für Ihre Benutzer sicherzustellen.  

DirectWrite, GDI und XAML-SwapChainPanels unterstützen nativ Text zu skalieren, keine während Win32-Unterstützung auf Menüs, Symbole und Symbolleisten begrenzt ist.  

<!-- If you want to support text scaling in your application with these frameworks, you’ll need to support the text scaling change event outlined below and provide alternative sizes for your UI and content.   -->

## <a name="user-experience"></a>Benutzerfreundlichkeit

Benutzer können Textanzeige anpassen mit dem stellen Text größer Schieberegler in den Einstellungen -> -> erleichterte Bedienung Vision/Bildschirm.

![Beispiel für Text, die Skalierung von 100 % auf 225 %](images/coretext/text-scaling-settings-100-small.png)  
*Textanzeige von Einstellungen -> erleichterte Bedienung Vision/Bildschirm ->*

## <a name="ux-guidance"></a>Erläuterungen zur Benutzeroberfläche

Wie Text geändert wird, Steuerelemente und Container müssen auch die Größe und umbrechen, um den Text und das neue Layout aufzunehmen. Wie bereits erwähnt abhängig von der app-Frameworks und -Plattform ist der Großteil der Arbeit für Sie erledigt. Die folgenden UX-Richtlinien werden diese Fälle, in denen es nicht behandelt.

### <a name="use-the-platform-controls"></a>Verwenden Sie die Plattformsteuerelemente

Sagten wir dies bereits? Dabei ist zu wiederholen: Wenn möglich, müssen Sie die integrierten Steuerelemente mit den verschiedenen Windows-app-Frameworks bereitgestellten immer verwenden, um die umfassendste Benutzeroberfläche für wenig Aufwand wie möglich erhalten.

Alle UWP-Textsteuerelemente z. B. den vollständigen Text Skalierung Umgebung ohne Anpassung oder Templating unterstützen.

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

![Skalierung von 100 % auf 225 % animierter text](images/coretext/text-scaling.gif)  
*Animierte Text skalieren*

### <a name="use-auto-sizing"></a>Verwenden von Auto-Größe

Geben Sie keine absolute Größen für Ihre Steuerelemente. Wann immer möglich, können Sie die Plattform, die Ihre Steuerelemente automatisch basierend auf Benutzer- und geräteeinstellungen zu ändern.  

In diesem Codeausschnitt aus dem vorherigen Beispiel verwenden wir die `Auto` und `*` Breitenwerte für eine Gruppe von Grid Spalten und ermöglichen die Plattform passen Sie das app-Layout basierend auf der Größe der Elemente innerhalb des Rasters.

``` xaml
<Grid.ColumnDefinitions>
    <ColumnDefinition Width="Auto"/>
    <ColumnDefinition Width="*"/>
    <ColumnDefinition Width="Auto"/>
</Grid.ColumnDefinitions>
```

### <a name="use-text-wrapping"></a>Verwenden Sie den Textumbruch

Um sicherzustellen, dass das Layout Ihrer App als flexibel und anpassbar wie möglich ist, aktivieren Sie den Textumbruch in jedes Steuerelement, das Text enthält (viele Steuerelemente Textumbruch standardmäßig unterstützen keine).

Wenn Sie den Textumbruch nicht angeben, verwendet die Plattform andere Methoden zum Anpassen des Layouts, einschließlich Zuschneiden (siehe vorherigen Beispiel).

Hier verwenden wir die `AcceptsReturn` und `TextWrapping` TextBox-Eigenschaften, um sicherzustellen, dass unsere Layout flexibel wie möglich ist.

``` xaml
<TextBox PlaceholderText="Type something here" 
          AcceptsReturn="True" TextWrapping="Wrap" />
```

![Animierter Text, die Skalierung von 100 % auf 225 % mit Textumbruch](images/coretext/text-scaling-textwrap.gif)  
*Animierte Text Skalieren mit Textumbruch*

### <a name="specify-text-trimming-behavior"></a>Geben Sie Text Kürzung Verhalten

Wenn Textumbruch nicht Verhalten erwünscht ist, können die meisten Textsteuerelemente entweder Ihr Text zuschneiden, oder geben Sie Ellipsen für das Verhalten der Text Kürzung. Zuschneiden wird bevorzugt, Ellipsen, als Ellipsen selbst Speicherplatz belegen.

> [!NOTE]
> Wenn Sie Sie den Text zu beschneiden müssen, abgeschnitten Sie, das Ende der Zeichenfolge, die nicht am Anfang.

In diesem Beispiel zeigen wir, wie Sie Text in einem TextBlock zu beschneiden mithilfe der [TextTrimming](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.textblock.texttrimming) -Eigenschaft.

``` xaml
<TextBlock TextTrimming="Clip">
    The quick brown fox jumped over the lazy dog.
</TextBlock>
```

![Skalierung von 100 % auf 225 % mit Text Zuschneiden Text](images/coretext/text-scaling-clipping-small.png)  
*Text skalieren mit Text Zuschneiden*

### <a name="use-a-tooltip"></a>Verwenden Sie eine QuickInfo

Wenn Sie Text zuschneiden, verwenden Sie QuickInfos, um den vollständigen Text für Ihre Benutzer bereitzustellen.

Hier fügen wir eine QuickInfo in einem TextBlock-Element, die den Textumbruch nicht unterstützt:

``` xaml
<TextBlock TextTrimming="Clip">
    <ToolTipService.ToolTip>
        <ToolTip Content="The quick brown fox jumped over the lazy dog."/>
    </ToolTipService.ToolTip>
    The quick brown fox jumped over the lazy dog.
</TextBlock>
```

### <a name="dont-scale-font-based-icons-or-symbols"></a>Keine Schriftart-basierte Symbole oder Symbole skalieren

Wenn Sie Symbole Schriftart-basierte zur Betonung oder als Ergänzung zu verwenden, deaktivieren Sie die Skalierung auf diese Zeichen.

Legen Sie die Eigenschaft [IsTextScaleFactorEnabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.control.istextscalefactorenabled) auf `false` für die meisten XAML-Steuerelemente.

### <a name="support-text-scaling-natively"></a>Unterstützung für Text nativ Skalierung

Behandeln Sie das [TextScaleFactorChanged](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.uisettings.textscalefactorchanged) UISettings System-Ereignis in Ihren benutzerdefinierten Framework Steuerelemente. Dieses Ereignis wird jedes Mal ausgelöst, wenn der Benutzer den Skalierungsfaktor Text auf seinem System festlegt.

## <a name="summary"></a>Zusammenfassung

Dieses Thema enthält eine Übersicht über Text-Unterstützung in Windows Skalierung und enthält (UX) und Entwickler Richtlinien zum Anpassen der Benutzeroberfläche.

## <a name="related-articles"></a>Verwandte Artikel

### <a name="api-reference"></a>API-Referenz

- [IsTextScaleFactorEnabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.control.istextscalefactorenabled)
- [TextScaleFactorChanged](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.uisettings.textscalefactorchanged)
