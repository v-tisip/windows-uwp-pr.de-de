---
description: Hier erfahren Sie, wie Sie Akzentfarben und Designs in Ihren UWP-Apps verwenden.
title: Farbe in UWP-Apps
ms.date: 4/7/2018
ms.topic: article
keywords: Windows10, UWP
design-contact: karenmui
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 55e93cdbeec5aad487d7c03c1877095dc13955b1
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8688775"
---
# <a name="color"></a>Farben

![Favoritenbild](images/header-color.svg)

Farbe bietet eine intuitive Möglichkeit, Informationen an Benutzer in Ihrer App zu übermitteln – sie kann Interaktivität anzuzeigen, Feedback auf Benutzeraktionen geben und Ihrer Benutzeroberfläche ein Gefühl von visueller Kontinuität vermitteln. 

In UWP-Apps werden die Farben in erster Linie durch Akzentfarbe und Design bestimmt. In diesem Artikel erläutern wir, wie Sie die Farbe in Ihrer App verwenden können, und wie Sie Akzentfarben und Designressourcen verwenden, um Ihre UWP-App in jedem beliebigen Design-Kontext verwendet zu können. 

## <a name="color-principles"></a>Farbprinzipien

:::row:::
    :::column:::
        **Use color meaningfully.**
        When color is used sparingly to highlight important elements, it can help create a user interface that is fluid and intuitive.
    :::column-end:::
    :::column:::
        **Use color to indicate interactivity.**
        It's a good idea to choose one color to indicate elements of your application that are interactive. For example, many web pages use blue text to denote a hyperlink.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        **Color is personal.**
        In Windows, users can choose an accent color and a light or dark theme, which are reflected throughout their experience. You can choose how to incorporate the user's accent color and theme into your application, personalizing their experience.
    :::column-end:::
    :::column:::
        **Color is cultural.**
        Consider how the colors you use will be interpreted by people from different cultures. For example, in some cultures the color blue is associated with virtue and protection, while in others it represents mourning.
    :::column-end:::
:::row-end:::

## <a name="themes"></a>Designs

UWP-Apps können ein helles oder dunkles Anwendungsdesign verwenden. Das Design wirkt sich auf die Farben des App-Hintergrunds, Text, Symbole und [Standardsteuerelemente](../controls-and-patterns/index.md) aus.

### <a name="light-theme"></a>Helles Design

![Helles Design](images/color/light-theme.svg)

### <a name="dark-theme"></a>Dunkles Design

![Dunkles Design](images/color/dark-theme.svg)

Das Design der UWP-App folgt standardmäßig den Design-Einstellungen des Benutzers aus den Windows-Einstellungen oder dem Standarddesign des Geräts (d.h. dunkel auf XBox). Allerdings können Sie das Design für Ihre UWP-App festlegen. 

### <a name="changing-the-theme"></a>Ändern des Designs

Sie können Designs einfach ändern, indem Sie die **RequestedTheme**-Eigenschaft in `App.xaml`-Datei ändern:

```XAML
<Application
    x:Class="App9.App"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:App9"
    RequestedTheme="Dark">
</Application>
```

Das Entfernen der **RequestedTheme**-Eigenschaft bedeutet, dass die Anwendung die Systemeinstellungen des Benutzers verwendet.

Anwender können auch Designs mit hohem Kontrast verwenden, die eine kleine Palette von Farbkombinationen mit hohem Farbkontrast nutzen, durch die die Benutzeroberfläche leichter zu erkennen ist. In diesem Fall überschreibt das System Ihre RequestedTheme.

### <a name="testing-themes"></a>Testen von Designs

Wenn Sie kein Design für Ihre App anfordern, sollten Sie unbedingt Ihre App in hellem und dunklem Design testen, um sicherzustellen, dass Ihre App unter allen Umständen lesbar ist.

**Hinweis:**: In Visual Studio ist das RequestedTheme standardmäßig hell, daher müssen Sie die RequestedTheme ändern, um beide zu testen.

## <a name="theme-brushes"></a>Designpinsel

Allgemeine Steuerelemente verwenden automatisch [Designpinsel](../controls-and-patterns/xaml-theme-resources.md#the-xaml-color-ramp-and-theme-dependent-brushes), um den Kontrast für helle und dunkle Designs anzupassen.

Hier ist eine Abbildung, wie [AutoSuggestBox](../controls-and-patterns/auto-suggest-box.md) die Designpinsel verwendet:

![Beispiel für Steuerelement-Designpinsel](images/color/theme-brushes.svg)

Die Designpinsel werden für folgende Zwecke verwendet:

- **Base** gilt für Text.
- **ALT** ist das Gegenteil von Base.
- **Chrome** richtet sich an die Elemente der obersten Ebene, z.B. Navigationsbereich oder Befehlsleisten.
- **List** gilt für Steuerelemente.

**Niedrig**/**Mittel**/**Hoch** beziehen sich auf die Intensität der Farben.

### <a name="using-theme-brushes"></a>Verwenden der Designpinsel

:::row:::
    :::column:::
        When creating templates for custom controls, use theme brushes rather than hard code color values. This way, your app can easily adapt to any theme.

        For example, these [item templates for ListView](../controls-and-patterns/item-templates-listview.md) demonstrate how to use theme brushes in a custom template.
    :::column-end:::
    :::column:::
         ![double line list item with icon example](images/color/list-view.svg)
    :::column-end:::
:::row-end:::

```xaml
<ListView ItemsSource="{x:Bind ViewModel.Recordings}">
    <ListView.ItemTemplate>
        <DataTemplate x:Name="DoubleLineDataTemplate" x:DataType="local:Recording">
            <StackPanel Orientation="Horizontal" Height="64" AutomationProperties.Name="{x:Bind CompositionName}">
                <Ellipse Height="48" Width="48" VerticalAlignment="Center">
                    <Ellipse.Fill>
                        <ImageBrush ImageSource="Placeholder.png"/>
                    </Ellipse.Fill>
                </Ellipse>
                <StackPanel Orientation="Vertical" VerticalAlignment="Center" Margin="12,0,0,0">
                    <TextBlock Text="{x:Bind CompositionName}"  Style="{ThemeResource BaseTextBlockStyle}" Foreground="{ThemeResource SystemControlPageTextBaseHighBrush}" />
                    <TextBlock Text="{x:Bind ArtistName}" Style="{ThemeResource BodyTextBlockStyle}" Foreground="{ThemeResource SystemControlPageTextBaseMediumBrush}"/>
                </StackPanel>
            </StackPanel>
        </DataTemplate>
    </ListView.ItemTemplate>
</ListView>
```

Weitere Informationen zur Verwendung von Designpinseln in Ihrer App finden Sie unter [Designressourcen](../controls-and-patterns/xaml-theme-resources.md).

## <a name="accent-color"></a>Akzentfarbe

Allgemeine Steuerelemente verwenden eine Akzentfarbe, um die Zustandsinformationen zu vermitteln. Standardmäßig ist die Akzentfarbe die `SystemAccentColor`, die der Benutzer in den Einstellungen auswählt. Sie können jedoch auch Akzentfarben entsprechend der Marke Ihrer App anpassen.

![Windows-Steuerelemente](images/color/windows-controls.svg)

:::row:::
    :::column:::
        ![user-selected accent header](images/color/user-accent.svg)
        ![user-selected accent color](images/color/user-selected-accent.svg)
    :::column-end:::
    :::column:::
        ![custom accent header](images/color/custom-accent.svg)
        ![custom brand accent color](images/color/brand-color.svg)
    :::column-end:::
:::row-end:::

### <a name="overriding-the-accent-color"></a>Überschreiben der Akzentfarbe

Wenn Sie Ihre App-Akzentfarbe ändern möchten, platzieren Sie den folgenden Code in `app.xaml`.

```xaml
<Application.Resources>
    <ResourceDictionary>
        <Color x:Key="SystemAccentColor">#107C10</Color>
    </ResourceDictionary>
</Application.Resources>
```

### <a name="choosing-an-accent-color"></a>Auswählen einer Akzentfarbe

Wenn Sie eine benutzerdefinierte Akzentfarbe für Ihre App auswählen, stellen Sie sicher, dass Text und Hintergrund, die die Akzentfarbe verwenden, ausreichenden Kontrast für eine optimale Lesbarkeit haben. Um den Kontrast zu testen, können Sie das Farbauswahltool in den Windows-Einstellungen verwenden, oder Sie können diese [online Kontrast-Tools nutzen](https://www.w3.org/TR/WCAG20-TECHS/G18.html#G18-resources).

![Benutzerdefinierter Akzentfarbwähler in den Windows-Einstellungen](images/color/color-picker.svg)

## <a name="accent-color-palette"></a>Akzentfarbpalette

Ein Akzentfarbalgorithmus in der Windows-Shell generiert helle und dunkle Schattierungen der Akzentfarbe.

![Akzentfarbpalette](images/color/accent-color-palette.svg)

Diese Schattierungen sind als [Designressourcen](../controls-and-patterns/xaml-theme-resources.md) verfügbar:

- `SystemAccentColorLight3`
- `SystemAccentColorLight2`
- `SystemAccentColorLight1`
- `SystemAccentColorDark1`
- `SystemAccentColorDark2`
- `SystemAccentColorDark3`

<!-- check this is true -->
Sie können die Akzentfarbpalette auch programmgesteuert mit der [**UISettings.GetColorValue**](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.UISettings#Windows_UI_ViewManagement_UISettings_GetColorValue_Windows_UI_ViewManagement_UIColorType_)-Methode und [**UIColorType**](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.UIColorType)-Enumeration aufrufen.

Sie können die Akzentfarbpalette für Designfarben in Ihrer App verwenden. Hier ist ein Beispiel für die Verwendung der Akzentfarbpalette auf einer Schaltfläche.

![Akzentfarbpalette auf einer Schaltfläche](images/color/color-theme-button.svg)

```xaml
<Page.Resources>
    <ResourceDictionary>
        <ResourceDictionary.ThemeDictionaries>
            <ResourceDictionary x:Key="Light">
                <SolidColorBrush x:Key="ButtonBackground" Color="{ThemeResource SystemAccentColor}"/>
                <SolidColorBrush x:Key="ButtonBackgroundPointerOver" Color="{ThemeResource SystemAccentColorLight1}"/>
                <SolidColorBrush x:Key="ButtonBackgroundPressed" Color="{ThemeResource SystemAccentColorDark1}"/>
            </ResourceDictionary>
        </ResourceDictionary.ThemeDictionaries>
    </ResourceDictionary>
</Page.Resources>

<Button Content="Button"></Button>
```

Wenn Sie farbigen Text auf farbigem Hintergrund verwenden, stellen Sie sicher, dass genügend Kontrast zwischen Text und Hintergrund vorhanden ist. Standardmäßig werden Hyperlinks oder Hypertext in der Akzentfarbe des Benutzers dargestellt. Wenden Sie Varianten der Akzentfarbe im Hintergrund an, sollten Sie eine Variante der ursprüngliche Akzentfarbe verwenden, um den Kontrast von farbigem Text auf farbigem Hintergrund zu optimieren.

Das folgende Diagramm zeigt ein Beispiel für die unterschiedlichen Hell/Dunkel-Töne der Akzentfarbe, und gibt an, wie der Farbtyp auf einer farbige Oberfläche angewendet werden kann.

![Farbe auf Farbe](images/color/color-on-color.svg)

Weitere Informationen zum Verwenden der Stil-Steuerelemente finden Sie unter [XAML-Style](../controls-and-patterns/xaml-styles.md).

## <a name="color-api"></a>Farb-API

Es gibt verschiedene APIs, um Farbe auf Ihrer Anwendung hinzuzufügen. Zuerst kommt die [**Farb**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.colors)-Klasse, die eine umfangreiche Liste vordefinierter Farben implementiert. Auf diese kann automatisch mithilfe der XAML-Eigenschaften zugegriffen werden. Im folgenden Beispiel erstellen wir eine Schaltfläche und legen Sie Farbeigenschaften im Hintergrund und Vordergrund auf Mitglieder der **Farb**-Klasse fest.

```xaml
<Button Background="MediumSlateBlue" Foreground="White">Button text</Button>
```

Sie können Ihre eigenen Farben aus RGB- und hex-Werten mithilfe der [**Farb**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.color)-Struktur in XAML erstellen.

```xaml
<Color x:Key="LightBlue">#FF36C0FF</Color>
```

Sie können auch die gleiche Farbe im Code mit der **FromArgb**-Methode erstellen.

```csharp
Color LightBlue = Color.FromArgb(255,54,192,255);
```

Die Buchstaben "Argb" bedeutet Alpha (Deckkraft), Rot, Grün und Blau, die vier Komponenten einer Farbe. Jedes Argument reicht von 0 bis 255. Sie können den ersten Wert auslassen, was eine standardmäßige Deckkraft von 255 oder 100% undurchsichtig ergibt.

> [!Note]
> Wenn Sie C++ verwenden, müssen Sie Farben mit der [**ColorHelper**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.colorhelper)-Klasse erstellen.

Am häufigsten wird für eine **Farbe** ein Argument für [**SolidColorBrush**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.media.solidcolorbrush) verwendet, das zum Zeichnen von UI-Elementen im Volltonfarbe verwendet werden kann. Diese Pinsel sind in der Regel durch das [**ResourceDictionary**](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.ResourceDictionary) definiert, sodass sie für mehrere Elemente wiederverwendet werden können.

```xaml
<ResourceDictionary>
    <SolidColorBrush x:Key="ButtonBackgroundBrush" Color="#FFFF4F67"/>
    <SolidColorBrush x:Key="ButtonForegroundBrush" Color="White"/>
</ResourceDictionary>
```

Weitere Informationen über die Verwendung der Pinsel finden Sie unter [XAML-Pinsel](brushes.md).

## <a name="scoping-system-colors"></a>Begrenzen von Systemfarben

Zusätzlich zur Definition von Ihre eigenen Farben in Ihrer app, können Sie auch unsere systematized Farben, die gewünschten Regionen in der gesamten app einen Bereich unter Verwendung des **ColorSchemeResources** -Tags. Mithilfe dieser API können Sie nicht nur einfärben und Design große Gruppen von Steuerelementen gleichzeitig durch Festlegen von einige Eigenschaften, sondern auch Sie viele andere System, dass Sie die Vorteile bietet würde nicht in der Regel mit definieren Ihre eigenen benutzerdefinierten Farben manuell erhalten:

- Eine beliebige Farbe mit **ColorSchemeResources** festgelegt werden mit hohem Kontrast.
  * D. h. Ihre app kann an mehrere Personen ohne zusätzliche Design oder Dev Kosten zugegriffen werden
- Können Farben hellen, dunklen oder testanforderungen über beide Designs einfach durch das Festlegen einer Eigenschaft in der API
- Farben festlegen auf **ColorSchemeResources** Kaskadieren sich zu alle ähnliche Steuerelemente, die auch Systemfarbe
  * Dadurch wird sichergestellt, dass Sie eine einheitliche Farbe Story in der gesamten app hat und gleichzeitig das Erscheinungsbild Ihrer Marke
- Alle visuellen Zustände, Animationen und Deckkraft Variationen Effekte ohne stilistisch

### <a name="how-to-use-colorschemeresources"></a>So verwenden Sie ColorSchemeResources

ColorSchemeResources ist eine API, die mitteilt, dass das System, welche Ressourcen verwendet werden, wo beschränkt. ColorSchemeResources muss ein [X: Key](https://docs.microsoft.com/windows/uwp/xaml-platform/x-key-attribute), ausführen, die eine der drei Optionen werden können:
- Standard
  * Die Farbe Änderungen werden im [Licht](https://docs.microsoft.com/windows/uwp/design/style/color#light-theme) und [dunklen](https://docs.microsoft.com/windows/uwp/design/style/color#dark-theme) Design angezeigt werden.
- Licht
  * Die Farbe Änderungen werden nur in einem [hellen Design](https://docs.microsoft.com/windows/uwp/design/style/color#light-theme) angezeigt werden. 
- Dark
  * Die Farbe Änderungen werden nur im [dunklen Design](https://docs.microsoft.com/windows/uwp/design/style/color#dark-theme) angezeigt werden.

Festlegen, X: Key wird sichergestellt, dass Ihre Farben entsprechend auf das System- oder app-Design ändern, sollten Sie eine andere benutzerdefinierte Darstellung in beiden Designs möchten.

### <a name="how-to-apply-scoped-colors"></a>So wenden Sie Bereichsbezogene Farben

Begrenzen der Ressourcen über das **ColorSchemeResources** API in XAML können Sie alle Systemfarbe oder Pinsel, die in unserer Bibliothek [Designressourcen](https://docs.microsoft.com/windows/uwp/design/controls-and-patterns/xaml-theme-resources) und definieren sie innerhalb des Bereichs von einer Seite oder im Container.

Beispielsweise, wenn Sie definiert zwei Systemfarben - **SystemBaseLowColor** und **SystemBaseMediumLowColor** in einem Raster, und klicken Sie dann zwei Schaltflächen auf der Seite eingefügt: innerhalb dieses Raster, und eine außen:

```xaml
<Grid x:Name="Grid_A">
    <Grid.Resources>
        <ColorSchemeResources x:Key="Default" 
        SystemBaseLowColor="LightGreen" 
        SystemBaseMediumLowColor="DarkCyan"/>
    </Grid.Resources>

    <Buton Content="Button_A"/>
</Grid>
<Buton Content="Button_B"/>
```

Erhalten Sie **Button_A** mit den angewendeten neuen Farben und **Button_B** bleiben würde, wie unsere Standardschaltfläche System suchen:

![Bereichsbezogene Systemfarben auf-Taste](images/color/scopedcolors_cyan_button.png)

Da alle unsere Systemfarben zu an andere Steuerelemente und Kaskadieren wirkt Festlegen von **SystemBaseLowColor** und **SystemBaseMediumLowColor** mehr als nur Schaltflächen sich jedoch. In diesem Fall steuert wie **ToggleButton**, **RadioButton** und **Slider** auch diese Farbe ändert, erfolgt nach wird diese Steuerelemente vorgesehen ist, oberhalb des Rasters Exampl Bereich ist.
Wenn Sie ein System Farbe ändern *, nur eine einzelne Steuerelemente* einschränken möchten, können Sie dies tun, durch die Definition von **ColorSchemeResources** innerhalb des Steuerelements Ressourcen:

```xaml
<Grid x:Name="Grid_A">
    <Button Content="Button_A">
        <Button.Resources>
            <ColorSchemeResources x:Key="Default" 
                SystemBaseLowColor="LightGreen" 
                SystemBaseMediumLowColor="DarkCyan"/>
        </Button.Resources>
    </Button>
</Grid>
<Button Content="Button_B"/>
```
Sie müssen im Wesentlichen genaue das gleiche wie vor, aber nun von anderen Steuerelementen hinzugefügt und das Raster werden nicht erlernbare ändert sich die Farbe. Dies ist, da diese Systemfarben nur auf **Button_A** beschränkt werden.

### <a name="nesting-scoped-resources"></a>Schachtelung beschränkt Ressourcen

Schachtelung von Systemfarben ist auch möglich, und erfolgt dies durch das Platzieren von **ColorSchemeResources** in der geschachtelten Elemente innerhalb des Markups von Ihrer app-Layout Ressourcen:

```xaml
<Grid x:Name="Grid_A">
    <Grid.Resources>
        <ColorSchemeResources x:Key="Default"
            SystemBaseLowColor="LightGreen"
            SystemBaseMediumLowColor="DarkCyan"/>
    </Grid.Resources>

    <Button Content="Button_A"/>
    <Grid x:Name="Grid_B">
        <Grid.Resources>
            <ColorSchemeResources x:Key="Default"
                SystemBaseLowColor="Goldenrod"
                SystemBaseMediumLowColor="DarkGoldenrod"/>
        </Grid.Resources>

        <Button Content="Nested Button"/>
    </Grid>
</Grid>
```

In diesem Beispiel **Button_A** erbt Farben in **Grid_A**Ressourcen definieren und **Schaltfläche geschachtelt** ist Farben **Grid_B**Ressourcen erben. Dies bedeutet, die alle anderen Steuerelemente in **Grid_B** platziert wird durch die Erweiterung überprüfen oder **Grid_B**Ressourcen zunächst anwenden, bevor überprüfen oder anwenden **Grid_A**Ressourcen, und schließlich unsere Standardfarben anwenden, wenn nichts auf definiert die Seiten- oder app-Ebene.

Dies eignet sich für eine beliebige Anzahl von geschachtelten Elementen, dessen Ressourcen Farbe Definitionen verfügen.

### <a name="scoping-with-a-resourcedictionary"></a>Bereiche mit einem ResourceDictionary

Sie sind nicht auf einem Container oder den Ressourcen Seite beschränkt und können auch diese Systemfarben in einem ResourceDictionary, die dann zusammengeführt werden kann auf einem beliebigen Bereich die Möglichkeit, die Sie in der Regel ein Wörterbuch zusammenführen möchten.

#### <a name="mycustomthemexaml"></a>MyCustomTheme.xaml

Erstellen Sie zunächst ein ResourceDictionary. Platzieren Sie die **ColorSchemeResources** innerhalb der ThemeDictionaries und überschreiben Sie die gewünschten Systemfarben:

```xaml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" 
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:TestApp">

    <ResourceDictionary.ThemeDictionaries>

        <ColorSchemeResources x:Key="Default"
            SystemBaseLowColor="LightGreen"
            SystemBaseMediumLowColor="DarkCyan"/>
        
    </ResourceDictionary.ThemeDictionaries>
</ResourceDictionary>
```

#### <a name="mainpagexaml"></a>MainPage.xaml

Auf der Seite, das Layout enthält führen Sie einfach zusammen Sie diese Wörterbuch im an den gewünschten Bereich:

```xaml
<Grid x:Name="Grid_A">
    <Grid.Resources>
            <ResourceDictionary>
                <ResourceDictionary.MergedDictionaries>
                    <ResourceDictionary Source="MyCustomTheme.xaml"/>
                </ResourceDictionary.MergedDictionaries>
            </ResourceDictionary>
    </Grid.Resources>
             
    <Button Content="Button_A"/>
</Grid>
```

Nun können alle Ressourcen, Designs und benutzerdefinierte Farben in einem einzigen **MyCustomTheme** Ressourcenverzeichnis platziert und sein beschränkt, bei Bedarf ohne zusätzliche unübersichtliche in Ihrem Layout-Markup kümmern.

### <a name="other-ways-to-define-color-resources"></a>Andere Methoden, um die Farbressourcen definieren

ColorSchemeResources kann auch Systemfarben platziert werden und als Wrapper, anstatt in Zeile direkt darin definieren:

``` xaml
<ColorSchemeResources x:Key="Dark">
    <Color x:Key="SystemBaseLowColor">Goldenrod</Color>
</ColorSchemeResources>
```

## <a name="usability"></a>Benutzerfreundlichkeit

:::row:::
    :::column:::
        ![contrast illustration](images/color/illo-contrast.svg)
    :::column-end:::
    :::column span="2":::
        **Contrast**

        Make sure that elements and images have sufficient contrast to differentiate between them, regardless of the accent color or theme.

        When considering what colors to use in your application, accessiblity should be a primary concern. Use the guidance below to make sure your application is accessible to as many users as possible.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![contrast illustration](images/color/illo-lighting.svg)
    :::column-end:::
    :::column span="2":::
        **Lighting**

        Be aware that variation in ambient lighting can affect the useability of your app. For example, a page with a black background might unreadable outside due to screen glare, while a page with a white background might be painful to look at in a dark room.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![contrast illustration](images/color/illo-colorblindness.svg)
    :::column-end:::
    :::column span="2":::
        **Colorblindness**

        Be aware of how colorblindness could affect the useability of your application. For example, a user with red-green colorblindness will have difficulty distinguishing red and green elements from each other. About **8 percent of men** and **0.5 percent of women** are red-green colorblind, so avoid using these color combinations as the sole differentiator between application elements.
    :::column-end:::
:::row-end:::

## <a name="related-articles"></a>Verwandte Artikel

- [XAML-Formatvorlagen](../controls-and-patterns/xaml-styles.md)
- [XAML-Designressourcen](../controls-and-patterns/xaml-theme-resources.md)
