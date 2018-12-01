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
ms.sourcegitcommit: d2517e522cacc5240f7dffd5bc1eaa278e3f7768
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8345250"
---
# <a name="color"></a><span data-ttu-id="7941c-104">Farben</span><span class="sxs-lookup"><span data-stu-id="7941c-104">Color</span></span>

![Favoritenbild](images/header-color.svg)

<span data-ttu-id="7941c-106">Farbe bietet eine intuitive Möglichkeit, Informationen an Benutzer in Ihrer App zu übermitteln – sie kann Interaktivität anzuzeigen, Feedback auf Benutzeraktionen geben und Ihrer Benutzeroberfläche ein Gefühl von visueller Kontinuität vermitteln.</span><span class="sxs-lookup"><span data-stu-id="7941c-106">Color provides an intuitive way of communicating information to users in your app: it can be used to indicate interactivity, give feedback to user actions, and give your interface a sense of visual continuity.</span></span> 

<span data-ttu-id="7941c-107">In UWP-Apps werden die Farben in erster Linie durch Akzentfarbe und Design bestimmt.</span><span class="sxs-lookup"><span data-stu-id="7941c-107">In UWP apps, colors are primarily determined by accent color and theme.</span></span> <span data-ttu-id="7941c-108">In diesem Artikel erläutern wir, wie Sie die Farbe in Ihrer App verwenden können, und wie Sie Akzentfarben und Designressourcen verwenden, um Ihre UWP-App in jedem beliebigen Design-Kontext verwendet zu können.</span><span class="sxs-lookup"><span data-stu-id="7941c-108">In this article, we'll discuss how you can use color in your app, and how to use accent color and theme resources to make your UWP app usable in any theme context.</span></span> 

## <a name="color-principles"></a><span data-ttu-id="7941c-109">Farbprinzipien</span><span class="sxs-lookup"><span data-stu-id="7941c-109">Color principles</span></span>

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

## <a name="themes"></a><span data-ttu-id="7941c-110">Designs</span><span class="sxs-lookup"><span data-stu-id="7941c-110">Themes</span></span>

<span data-ttu-id="7941c-111">UWP-Apps können ein helles oder dunkles Anwendungsdesign verwenden.</span><span class="sxs-lookup"><span data-stu-id="7941c-111">UWP apps can use a light or dark application theme.</span></span> <span data-ttu-id="7941c-112">Das Design wirkt sich auf die Farben des App-Hintergrunds, Text, Symbole und [Standardsteuerelemente](../controls-and-patterns/index.md) aus.</span><span class="sxs-lookup"><span data-stu-id="7941c-112">The theme affects the colors of the app's background, text, icons, and [common controls](../controls-and-patterns/index.md).</span></span>

### <a name="light-theme"></a><span data-ttu-id="7941c-113">Helles Design</span><span class="sxs-lookup"><span data-stu-id="7941c-113">Light theme</span></span>

![Helles Design](images/color/light-theme.svg)

### <a name="dark-theme"></a><span data-ttu-id="7941c-115">Dunkles Design</span><span class="sxs-lookup"><span data-stu-id="7941c-115">Dark theme</span></span>

![Dunkles Design](images/color/dark-theme.svg)

<span data-ttu-id="7941c-117">Das Design der UWP-App folgt standardmäßig den Design-Einstellungen des Benutzers aus den Windows-Einstellungen oder dem Standarddesign des Geräts (d.h. dunkel auf XBox).</span><span class="sxs-lookup"><span data-stu-id="7941c-117">By default, your UWP app's theme is the user’s theme preference from Windows Settings or the device's default theme (i.e., dark on XBox).</span></span> <span data-ttu-id="7941c-118">Allerdings können Sie das Design für Ihre UWP-App festlegen.</span><span class="sxs-lookup"><span data-stu-id="7941c-118">However, you can set the theme for your UWP app.</span></span> 

### <a name="changing-the-theme"></a><span data-ttu-id="7941c-119">Ändern des Designs</span><span class="sxs-lookup"><span data-stu-id="7941c-119">Changing the theme</span></span>

<span data-ttu-id="7941c-120">Sie können Designs einfach ändern, indem Sie die **RequestedTheme**-Eigenschaft in `App.xaml`-Datei ändern:</span><span class="sxs-lookup"><span data-stu-id="7941c-120">You can change themes by changing the **RequestedTheme** property in your `App.xaml` file.</span></span>

```XAML
<Application
    x:Class="App9.App"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:App9"
    RequestedTheme="Dark">
</Application>
```

<span data-ttu-id="7941c-121">Das Entfernen der **RequestedTheme**-Eigenschaft bedeutet, dass die Anwendung die Systemeinstellungen des Benutzers verwendet.</span><span class="sxs-lookup"><span data-stu-id="7941c-121">Removing the **RequestedTheme** property means that your application will use the user’s system settings.</span></span>

<span data-ttu-id="7941c-122">Anwender können auch Designs mit hohem Kontrast verwenden, die eine kleine Palette von Farbkombinationen mit hohem Farbkontrast nutzen, durch die die Benutzeroberfläche leichter zu erkennen ist.</span><span class="sxs-lookup"><span data-stu-id="7941c-122">Users can also select the high contrast theme, which uses a small palette of contrasting colors that makes the interface easier to see.</span></span> <span data-ttu-id="7941c-123">In diesem Fall überschreibt das System Ihre RequestedTheme.</span><span class="sxs-lookup"><span data-stu-id="7941c-123">In that case, the system will override your RequestedTheme.</span></span>

### <a name="testing-themes"></a><span data-ttu-id="7941c-124">Testen von Designs</span><span class="sxs-lookup"><span data-stu-id="7941c-124">Testing themes</span></span>

<span data-ttu-id="7941c-125">Wenn Sie kein Design für Ihre App anfordern, sollten Sie unbedingt Ihre App in hellem und dunklem Design testen, um sicherzustellen, dass Ihre App unter allen Umständen lesbar ist.</span><span class="sxs-lookup"><span data-stu-id="7941c-125">If you don't request a theme for your app, make sure to test your app in both light and dark themes to ensure that your app will be legible in all conditions.</span></span>

<span data-ttu-id="7941c-126">**Hinweis:**: In Visual Studio ist das RequestedTheme standardmäßig hell, daher müssen Sie die RequestedTheme ändern, um beide zu testen.</span><span class="sxs-lookup"><span data-stu-id="7941c-126">**Note**: In Visual Studio, the default RequestedTheme is light, so you'll need to change the RequestedTheme to test both.</span></span>

## <a name="theme-brushes"></a><span data-ttu-id="7941c-127">Designpinsel</span><span class="sxs-lookup"><span data-stu-id="7941c-127">Theme brushes</span></span>

<span data-ttu-id="7941c-128">Allgemeine Steuerelemente verwenden automatisch [Designpinsel](../controls-and-patterns/xaml-theme-resources.md#the-xaml-color-ramp-and-theme-dependent-brushes), um den Kontrast für helle und dunkle Designs anzupassen.</span><span class="sxs-lookup"><span data-stu-id="7941c-128">Common controls automatically use [theme brushes](../controls-and-patterns/xaml-theme-resources.md#the-xaml-color-ramp-and-theme-dependent-brushes) to adjust contrast for light and dark themes.</span></span>

<span data-ttu-id="7941c-129">Hier ist eine Abbildung, wie [AutoSuggestBox](../controls-and-patterns/auto-suggest-box.md) die Designpinsel verwendet:</span><span class="sxs-lookup"><span data-stu-id="7941c-129">For example, here's an illustration of how the [AutoSuggestBox](../controls-and-patterns/auto-suggest-box.md) uses theme brushes:</span></span>

![Beispiel für Steuerelement-Designpinsel](images/color/theme-brushes.svg)

<span data-ttu-id="7941c-131">Die Designpinsel werden für folgende Zwecke verwendet:</span><span class="sxs-lookup"><span data-stu-id="7941c-131">The theme brushes are used for the following purposes:</span></span>

- <span data-ttu-id="7941c-132">**Base** gilt für Text.</span><span class="sxs-lookup"><span data-stu-id="7941c-132">**Base** is for text.</span></span>
- <span data-ttu-id="7941c-133">**ALT** ist das Gegenteil von Base.</span><span class="sxs-lookup"><span data-stu-id="7941c-133">**Alt** is the inverse of Base.</span></span>
- <span data-ttu-id="7941c-134">**Chrome** richtet sich an die Elemente der obersten Ebene, z.B. Navigationsbereich oder Befehlsleisten.</span><span class="sxs-lookup"><span data-stu-id="7941c-134">**Chrome** is for top-level elements, such as navigation panes or command bars.</span></span>
- <span data-ttu-id="7941c-135">**List** gilt für Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="7941c-135">**List** is for list controls.</span></span>

<span data-ttu-id="7941c-136">**Niedrig**/**Mittel**/**Hoch** beziehen sich auf die Intensität der Farben.</span><span class="sxs-lookup"><span data-stu-id="7941c-136">**Low**/**Medium**/**High** refer to the intensity of the color.</span></span>

### <a name="using-theme-brushes"></a><span data-ttu-id="7941c-137">Verwenden der Designpinsel</span><span class="sxs-lookup"><span data-stu-id="7941c-137">Using theme brushes</span></span>

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

<span data-ttu-id="7941c-138">Weitere Informationen zur Verwendung von Designpinseln in Ihrer App finden Sie unter [Designressourcen](../controls-and-patterns/xaml-theme-resources.md).</span><span class="sxs-lookup"><span data-stu-id="7941c-138">For more information about how to use theme brushes in your app, see [Theme Resources](../controls-and-patterns/xaml-theme-resources.md).</span></span>

## <a name="accent-color"></a><span data-ttu-id="7941c-139">Akzentfarbe</span><span class="sxs-lookup"><span data-stu-id="7941c-139">Accent color</span></span>

<span data-ttu-id="7941c-140">Allgemeine Steuerelemente verwenden eine Akzentfarbe, um die Zustandsinformationen zu vermitteln.</span><span class="sxs-lookup"><span data-stu-id="7941c-140">Common controls use an accent color to convey state information.</span></span> <span data-ttu-id="7941c-141">Standardmäßig ist die Akzentfarbe die `SystemAccentColor`, die der Benutzer in den Einstellungen auswählt.</span><span class="sxs-lookup"><span data-stu-id="7941c-141">By default, the accent color is the `SystemAccentColor` that users select in their Settings.</span></span> <span data-ttu-id="7941c-142">Sie können jedoch auch Akzentfarben entsprechend der Marke Ihrer App anpassen.</span><span class="sxs-lookup"><span data-stu-id="7941c-142">However, you can also customize your app's accent color to reflect your brand.</span></span>

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

### <a name="overriding-the-accent-color"></a><span data-ttu-id="7941c-144">Überschreiben der Akzentfarbe</span><span class="sxs-lookup"><span data-stu-id="7941c-144">Overriding the accent color</span></span>

<span data-ttu-id="7941c-145">Wenn Sie Ihre App-Akzentfarbe ändern möchten, platzieren Sie den folgenden Code in `app.xaml`.</span><span class="sxs-lookup"><span data-stu-id="7941c-145">To change your app's accent color, place the following code in `app.xaml`.</span></span>

```xaml
<Application.Resources>
    <ResourceDictionary>
        <Color x:Key="SystemAccentColor">#107C10</Color>
    </ResourceDictionary>
</Application.Resources>
```

### <a name="choosing-an-accent-color"></a><span data-ttu-id="7941c-146">Auswählen einer Akzentfarbe</span><span class="sxs-lookup"><span data-stu-id="7941c-146">Choosing an accent color</span></span>

<span data-ttu-id="7941c-147">Wenn Sie eine benutzerdefinierte Akzentfarbe für Ihre App auswählen, stellen Sie sicher, dass Text und Hintergrund, die die Akzentfarbe verwenden, ausreichenden Kontrast für eine optimale Lesbarkeit haben.</span><span class="sxs-lookup"><span data-stu-id="7941c-147">If you select a custom accent color for your app, please make sure that text and backgrounds that use the accent color have sufficient contrast for optimal readability.</span></span> <span data-ttu-id="7941c-148">Um den Kontrast zu testen, können Sie das Farbauswahltool in den Windows-Einstellungen verwenden, oder Sie können diese [online Kontrast-Tools nutzen](https://www.w3.org/TR/WCAG20-TECHS/G18.html#G18-resources).</span><span class="sxs-lookup"><span data-stu-id="7941c-148">To test contrast, you can use the color picker tool in Windows Settings, or you can use these [online contrast tools](https://www.w3.org/TR/WCAG20-TECHS/G18.html#G18-resources).</span></span>

![Benutzerdefinierter Akzentfarbwähler in den Windows-Einstellungen](images/color/color-picker.svg)

## <a name="accent-color-palette"></a><span data-ttu-id="7941c-150">Akzentfarbpalette</span><span class="sxs-lookup"><span data-stu-id="7941c-150">Accent color palette</span></span>

<span data-ttu-id="7941c-151">Ein Akzentfarbalgorithmus in der Windows-Shell generiert helle und dunkle Schattierungen der Akzentfarbe.</span><span class="sxs-lookup"><span data-stu-id="7941c-151">An accent color algorithm in the Windows shell generates light and dark shades of the accent color.</span></span>

![Akzentfarbpalette](images/color/accent-color-palette.svg)

<span data-ttu-id="7941c-153">Diese Schattierungen sind als [Designressourcen](../controls-and-patterns/xaml-theme-resources.md) verfügbar:</span><span class="sxs-lookup"><span data-stu-id="7941c-153">These shades can be accessed as [theme resources](../controls-and-patterns/xaml-theme-resources.md):</span></span>

- `SystemAccentColorLight3`
- `SystemAccentColorLight2`
- `SystemAccentColorLight1`
- `SystemAccentColorDark1`
- `SystemAccentColorDark2`
- `SystemAccentColorDark3`

<!-- check this is true -->
<span data-ttu-id="7941c-154">Sie können die Akzentfarbpalette auch programmgesteuert mit der [**UISettings.GetColorValue**](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.UISettings#Windows_UI_ViewManagement_UISettings_GetColorValue_Windows_UI_ViewManagement_UIColorType_)-Methode und [**UIColorType**](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.UIColorType)-Enumeration aufrufen.</span><span class="sxs-lookup"><span data-stu-id="7941c-154">You can also access the accent color palette programmatically with the [**UISettings.GetColorValue**](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.UISettings#Windows_UI_ViewManagement_UISettings_GetColorValue_Windows_UI_ViewManagement_UIColorType_) method and [**UIColorType**](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.UIColorType) enum.</span></span>

<span data-ttu-id="7941c-155">Sie können die Akzentfarbpalette für Designfarben in Ihrer App verwenden.</span><span class="sxs-lookup"><span data-stu-id="7941c-155">You can use the accent color palette for color theming in your app.</span></span> <span data-ttu-id="7941c-156">Hier ist ein Beispiel für die Verwendung der Akzentfarbpalette auf einer Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="7941c-156">Below is an example of how you can use the accent color palette on a button.</span></span>

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

<span data-ttu-id="7941c-158">Wenn Sie farbigen Text auf farbigem Hintergrund verwenden, stellen Sie sicher, dass genügend Kontrast zwischen Text und Hintergrund vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="7941c-158">When using colored text on a colored background, make sure there is enough contrast between text and background.</span></span> <span data-ttu-id="7941c-159">Standardmäßig werden Hyperlinks oder Hypertext in der Akzentfarbe des Benutzers dargestellt.</span><span class="sxs-lookup"><span data-stu-id="7941c-159">By default, hyperlink or hypertext will use the accent color.</span></span> <span data-ttu-id="7941c-160">Wenden Sie Varianten der Akzentfarbe im Hintergrund an, sollten Sie eine Variante der ursprüngliche Akzentfarbe verwenden, um den Kontrast von farbigem Text auf farbigem Hintergrund zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="7941c-160">If you apply variations of the accent color to the background, you should use a variation of the original accent color to optimize the contrast of colored text on a colored background.</span></span>

<span data-ttu-id="7941c-161">Das folgende Diagramm zeigt ein Beispiel für die unterschiedlichen Hell/Dunkel-Töne der Akzentfarbe, und gibt an, wie der Farbtyp auf einer farbige Oberfläche angewendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="7941c-161">The chart below illustrates an example of the various light/dark shades of accent color, and how colored type can be applied on a colored surface.</span></span>

![Farbe auf Farbe](images/color/color-on-color.svg)

<span data-ttu-id="7941c-163">Weitere Informationen zum Verwenden der Stil-Steuerelemente finden Sie unter [XAML-Style](../controls-and-patterns/xaml-styles.md).</span><span class="sxs-lookup"><span data-stu-id="7941c-163">For more information about styling controls, see [XAML styles](../controls-and-patterns/xaml-styles.md).</span></span>

## <a name="color-api"></a><span data-ttu-id="7941c-164">Farb-API</span><span class="sxs-lookup"><span data-stu-id="7941c-164">Color API</span></span>

<span data-ttu-id="7941c-165">Es gibt verschiedene APIs, um Farbe auf Ihrer Anwendung hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="7941c-165">There are several APIs that can be used to add color to your application.</span></span> <span data-ttu-id="7941c-166">Zuerst kommt die [**Farb**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.colors)-Klasse, die eine umfangreiche Liste vordefinierter Farben implementiert.</span><span class="sxs-lookup"><span data-stu-id="7941c-166">First, the [**Colors**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.colors) class, which implements a large list of predefined colors.</span></span> <span data-ttu-id="7941c-167">Auf diese kann automatisch mithilfe der XAML-Eigenschaften zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="7941c-167">These can be accessed automatically with XAML properties.</span></span> <span data-ttu-id="7941c-168">Im folgenden Beispiel erstellen wir eine Schaltfläche und legen Sie Farbeigenschaften im Hintergrund und Vordergrund auf Mitglieder der **Farb**-Klasse fest.</span><span class="sxs-lookup"><span data-stu-id="7941c-168">In the example below, we create a button and set the background and foreground color properties to members of the **Colors** class.</span></span>

```xaml
<Button Background="MediumSlateBlue" Foreground="White">Button text</Button>
```

<span data-ttu-id="7941c-169">Sie können Ihre eigenen Farben aus RGB- und hex-Werten mithilfe der [**Farb**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.color)-Struktur in XAML erstellen.</span><span class="sxs-lookup"><span data-stu-id="7941c-169">You can create your own colors from RGB or hex values using the [**Color**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.color) struct in XAML.</span></span>

```xaml
<Color x:Key="LightBlue">#FF36C0FF</Color>
```

<span data-ttu-id="7941c-170">Sie können auch die gleiche Farbe im Code mit der **FromArgb**-Methode erstellen.</span><span class="sxs-lookup"><span data-stu-id="7941c-170">You can also create the same color in code by using the **FromArgb** method.</span></span>

```csharp
Color LightBlue = Color.FromArgb(255,54,192,255);
```

<span data-ttu-id="7941c-171">Die Buchstaben "Argb" bedeutet Alpha (Deckkraft), Rot, Grün und Blau, die vier Komponenten einer Farbe.</span><span class="sxs-lookup"><span data-stu-id="7941c-171">The letters "Argb" stands for Alpha (opacity), Red, Green, and Blue, which are the four components of a color.</span></span> <span data-ttu-id="7941c-172">Jedes Argument reicht von 0 bis 255.</span><span class="sxs-lookup"><span data-stu-id="7941c-172">Each argument can range from 0 to 255.</span></span> <span data-ttu-id="7941c-173">Sie können den ersten Wert auslassen, was eine standardmäßige Deckkraft von 255 oder 100% undurchsichtig ergibt.</span><span class="sxs-lookup"><span data-stu-id="7941c-173">You can choose to omit the first value, which will give you a default opacity of 255, or 100% opaque.</span></span>

> [!Note]
> <span data-ttu-id="7941c-174">Wenn Sie C++ verwenden, müssen Sie Farben mit der [**ColorHelper**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.colorhelper)-Klasse erstellen.</span><span class="sxs-lookup"><span data-stu-id="7941c-174">If you're using C++, you must create colors by using the [**ColorHelper**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.colorhelper) class.</span></span>

<span data-ttu-id="7941c-175">Am häufigsten wird für eine **Farbe** ein Argument für [**SolidColorBrush**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.media.solidcolorbrush) verwendet, das zum Zeichnen von UI-Elementen im Volltonfarbe verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="7941c-175">The most common use for a **Color** is as an argument for a [**SolidColorBrush**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.media.solidcolorbrush), which can be used to paint UI elements a single solid color.</span></span> <span data-ttu-id="7941c-176">Diese Pinsel sind in der Regel durch das [**ResourceDictionary**](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.ResourceDictionary) definiert, sodass sie für mehrere Elemente wiederverwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="7941c-176">These brushes are generally defined in a [**ResourceDictionary**](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.ResourceDictionary), so they can be reused for multiple elements.</span></span>

```xaml
<ResourceDictionary>
    <SolidColorBrush x:Key="ButtonBackgroundBrush" Color="#FFFF4F67"/>
    <SolidColorBrush x:Key="ButtonForegroundBrush" Color="White"/>
</ResourceDictionary>
```

<span data-ttu-id="7941c-177">Weitere Informationen über die Verwendung der Pinsel finden Sie unter [XAML-Pinsel](brushes.md).</span><span class="sxs-lookup"><span data-stu-id="7941c-177">For more information on how to use brushes, see [XAML brushes](brushes.md).</span></span>

## <a name="scoping-system-colors"></a><span data-ttu-id="7941c-178">Begrenzen von Systemfarben</span><span class="sxs-lookup"><span data-stu-id="7941c-178">Scoping system colors</span></span>

<span data-ttu-id="7941c-179">Zusätzlich zur Definition von Ihre eigenen Farben in Ihrer app, können Sie auch unsere systematized Farben, die gewünschten Regionen in der gesamten app einen Bereich unter Verwendung des **ColorSchemeResources** -Tags.</span><span class="sxs-lookup"><span data-stu-id="7941c-179">In addition to defining your own colors in your app, you can also scope our systematized colors to desired regions throughout your app by using the **ColorSchemeResources** tag.</span></span> <span data-ttu-id="7941c-180">Mithilfe dieser API können Sie nicht nur einfärben und Design große Gruppen von Steuerelementen gleichzeitig durch Festlegen von einige Eigenschaften, sondern auch Sie viele andere System, dass Sie die Vorteile bietet würde nicht in der Regel mit definieren Ihre eigenen benutzerdefinierten Farben manuell erhalten:</span><span class="sxs-lookup"><span data-stu-id="7941c-180">This API allows you to not only colorize and theme large groups of controls at once by setting a few properties, but also gives you many other system benefits that you wouldn't normally get with defining your own custom colors manually:</span></span>

- <span data-ttu-id="7941c-181">Eine beliebige Farbe mit **ColorSchemeResources** festgelegt werden mit hohem Kontrast.</span><span class="sxs-lookup"><span data-stu-id="7941c-181">Any color set using **ColorSchemeResources** will not effect High Contrast</span></span>
  * <span data-ttu-id="7941c-182">D. h. Ihre app kann an mehrere Personen ohne zusätzliche Design oder Dev Kosten zugegriffen werden</span><span class="sxs-lookup"><span data-stu-id="7941c-182">Meaning your app will be accessible to more people without any additional design or dev cost</span></span>
- <span data-ttu-id="7941c-183">Können Farben hellen, dunklen oder testanforderungen über beide Designs einfach durch das Festlegen einer Eigenschaft in der API</span><span class="sxs-lookup"><span data-stu-id="7941c-183">Can easily set colors to Light, Dark or pervasive across both themes by setting one property on the API</span></span>
- <span data-ttu-id="7941c-184">Farben festlegen auf **ColorSchemeResources** Kaskadieren sich zu alle ähnliche Steuerelemente, die auch Systemfarbe</span><span class="sxs-lookup"><span data-stu-id="7941c-184">Colors set on **ColorSchemeResources** will cascade down to all similar controls that also use that system color</span></span>
  * <span data-ttu-id="7941c-185">Dadurch wird sichergestellt, dass Sie eine einheitliche Farbe Story in der gesamten app hat und gleichzeitig das Erscheinungsbild Ihrer Marke</span><span class="sxs-lookup"><span data-stu-id="7941c-185">This ensures that you will have a consistent color story across your app while maintaining the look of your brand</span></span>
- <span data-ttu-id="7941c-186">Alle visuellen Zustände, Animationen und Deckkraft Variationen Effekte ohne stilistisch</span><span class="sxs-lookup"><span data-stu-id="7941c-186">Effects all visual states, animations and opacity variations without needing to re-template</span></span>

### <a name="how-to-use-colorschemeresources"></a><span data-ttu-id="7941c-187">So verwenden Sie ColorSchemeResources</span><span class="sxs-lookup"><span data-stu-id="7941c-187">How to use ColorSchemeResources</span></span>

<span data-ttu-id="7941c-188">ColorSchemeResources ist eine API, die mitteilt, dass das System, welche Ressourcen verwendet werden, wo beschränkt.</span><span class="sxs-lookup"><span data-stu-id="7941c-188">ColorSchemeResources is an API that tells the system what resources are being scoped where.</span></span> <span data-ttu-id="7941c-189">ColorSchemeResources muss ein [X: Key](https://docs.microsoft.com/windows/uwp/xaml-platform/x-key-attribute), ausführen, die eine der drei Optionen werden können:</span><span class="sxs-lookup"><span data-stu-id="7941c-189">ColorSchemeResources must take an [x:Key](https://docs.microsoft.com/windows/uwp/xaml-platform/x-key-attribute), that can be one of three choices:</span></span>
- <span data-ttu-id="7941c-190">Standard</span><span class="sxs-lookup"><span data-stu-id="7941c-190">Default</span></span>
  * <span data-ttu-id="7941c-191">Die Farbe Änderungen werden im [Licht](https://docs.microsoft.com/windows/uwp/design/style/color#light-theme) und [dunklen](https://docs.microsoft.com/windows/uwp/design/style/color#dark-theme) Design angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7941c-191">Will show your color changes in both [Light](https://docs.microsoft.com/windows/uwp/design/style/color#light-theme) and [Dark](https://docs.microsoft.com/windows/uwp/design/style/color#dark-theme) theme</span></span>
- <span data-ttu-id="7941c-192">Licht</span><span class="sxs-lookup"><span data-stu-id="7941c-192">Light</span></span>
  * <span data-ttu-id="7941c-193">Die Farbe Änderungen werden nur in einem [hellen Design](https://docs.microsoft.com/windows/uwp/design/style/color#light-theme) angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7941c-193">Will show your color changes only in [Light theme](https://docs.microsoft.com/windows/uwp/design/style/color#light-theme)</span></span> 
- <span data-ttu-id="7941c-194">Dark</span><span class="sxs-lookup"><span data-stu-id="7941c-194">Dark</span></span>
  * <span data-ttu-id="7941c-195">Die Farbe Änderungen werden nur im [dunklen Design](https://docs.microsoft.com/windows/uwp/design/style/color#dark-theme) angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7941c-195">Will show your color changes only in [Dark theme](https://docs.microsoft.com/windows/uwp/design/style/color#dark-theme)</span></span>

<span data-ttu-id="7941c-196">Festlegen, X: Key wird sichergestellt, dass Ihre Farben entsprechend auf das System- oder app-Design ändern, sollten Sie eine andere benutzerdefinierte Darstellung in beiden Designs möchten.</span><span class="sxs-lookup"><span data-stu-id="7941c-196">Setting that x:Key will ensure that your colors change appropriately to the system or app theme, should you want a different custom appearance when in either theme.</span></span>

### <a name="how-to-apply-scoped-colors"></a><span data-ttu-id="7941c-197">So wenden Sie Bereichsbezogene Farben</span><span class="sxs-lookup"><span data-stu-id="7941c-197">How to apply scoped colors</span></span>

<span data-ttu-id="7941c-198">Begrenzen der Ressourcen über das **ColorSchemeResources** API in XAML können Sie alle Systemfarbe oder Pinsel, die in unserer Bibliothek [Designressourcen](https://docs.microsoft.com/windows/uwp/design/controls-and-patterns/xaml-theme-resources) und definieren sie innerhalb des Bereichs von einer Seite oder im Container.</span><span class="sxs-lookup"><span data-stu-id="7941c-198">Scoping resources through the **ColorSchemeResources** API in XAML allows you to take any system color or brush that's in our [theme resources](https://docs.microsoft.com/windows/uwp/design/controls-and-patterns/xaml-theme-resources) library and redefine them within the scope of a page or container.</span></span>

<span data-ttu-id="7941c-199">Beispielsweise, wenn Sie definiert zwei Systemfarben - **SystemBaseLowColor** und **SystemBaseMediumLowColor** in einem Raster, und klicken Sie dann zwei Schaltflächen auf der Seite eingefügt: innerhalb dieses Raster, und eine außen:</span><span class="sxs-lookup"><span data-stu-id="7941c-199">For example, if you defined two system colors - **SystemBaseLowColor** and **SystemBaseMediumLowColor** inside a grid, and then placed two buttons on your page: one inside that grid, and one outside:</span></span>

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

<span data-ttu-id="7941c-200">Erhalten Sie **Button_A** mit den angewendeten neuen Farben und **Button_B** bleiben würde, wie unsere Standardschaltfläche System suchen:</span><span class="sxs-lookup"><span data-stu-id="7941c-200">You would get **Button_A** with the applied new colors, and **Button_B** would remain looking like our system default button:</span></span>

![Bereichsbezogene Systemfarben auf-Taste](images/color/scopedcolors_cyan_button.png)

<span data-ttu-id="7941c-202">Da alle unsere Systemfarben zu an andere Steuerelemente und Kaskadieren wirkt Festlegen von **SystemBaseLowColor** und **SystemBaseMediumLowColor** mehr als nur Schaltflächen sich jedoch.</span><span class="sxs-lookup"><span data-stu-id="7941c-202">However, since all our system colors cascade down to other controls too, setting **SystemBaseLowColor** and **SystemBaseMediumLowColor** will affect more than just buttons.</span></span> <span data-ttu-id="7941c-203">In diesem Fall steuert wie **ToggleButton**, **RadioButton** und **Slider** auch diese Farbe ändert, erfolgt nach wird diese Steuerelemente vorgesehen ist, oberhalb des Rasters Exampl Bereich ist.</span><span class="sxs-lookup"><span data-stu-id="7941c-203">In this case, controls like **ToggleButton**, **RadioButton** and **Slider** will also be effected by these system color changes, should those controls be put in above exampl grid's scope.</span></span>
<span data-ttu-id="7941c-204">Wenn Sie ein System Farbe ändern *, nur eine einzelne Steuerelemente* einschränken möchten, können Sie dies tun, durch die Definition von **ColorSchemeResources** innerhalb des Steuerelements Ressourcen:</span><span class="sxs-lookup"><span data-stu-id="7941c-204">If you wish to scope a system color change *to a single controls only* you can do so by defining **ColorSchemeResources** within that control's resources:</span></span>

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
<span data-ttu-id="7941c-205">Sie müssen im Wesentlichen genaue das gleiche wie vor, aber nun von anderen Steuerelementen hinzugefügt und das Raster werden nicht erlernbare ändert sich die Farbe.</span><span class="sxs-lookup"><span data-stu-id="7941c-205">You essentially have the exact same thing as before, but now any other controls added to the grid will not pick up the color changes.</span></span> <span data-ttu-id="7941c-206">Dies ist, da diese Systemfarben nur auf **Button_A** beschränkt werden.</span><span class="sxs-lookup"><span data-stu-id="7941c-206">This is because those system colors are scoped to **Button_A** only.</span></span>

### <a name="nesting-scoped-resources"></a><span data-ttu-id="7941c-207">Schachtelung beschränkt Ressourcen</span><span class="sxs-lookup"><span data-stu-id="7941c-207">Nesting scoped resources</span></span>

<span data-ttu-id="7941c-208">Schachtelung von Systemfarben ist auch möglich, und erfolgt dies durch das Platzieren von **ColorSchemeResources** in der geschachtelten Elemente innerhalb des Markups von Ihrer app-Layout Ressourcen:</span><span class="sxs-lookup"><span data-stu-id="7941c-208">Nesting system colors is also possible, and is done so by placing **ColorSchemeResources** in the nested elements' resources within the markup of your app layout:</span></span>

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

<span data-ttu-id="7941c-209">In diesem Beispiel **Button_A** erbt Farben in **Grid_A**Ressourcen definieren und **Schaltfläche geschachtelt** ist Farben **Grid_B**Ressourcen erben.</span><span class="sxs-lookup"><span data-stu-id="7941c-209">In this example, **Button_A** is inheriting colors define in **Grid_A**'s resources, and **Nested Button** is inheriting colors from **Grid_B**'s resources.</span></span> <span data-ttu-id="7941c-210">Dies bedeutet, die alle anderen Steuerelemente in **Grid_B** platziert wird durch die Erweiterung überprüfen oder **Grid_B**Ressourcen zunächst anwenden, bevor überprüfen oder anwenden **Grid_A**Ressourcen, und schließlich unsere Standardfarben anwenden, wenn nichts auf definiert die Seiten- oder app-Ebene.</span><span class="sxs-lookup"><span data-stu-id="7941c-210">By extension, this means that any other controls placed within **Grid_B** will check or apply **Grid_B**'s resources first, before checking or applying **Grid_A**'s resources, and finally applying our default colors if nothing is defined at the page or app level.</span></span>

<span data-ttu-id="7941c-211">Dies eignet sich für eine beliebige Anzahl von geschachtelten Elementen, dessen Ressourcen Farbe Definitionen verfügen.</span><span class="sxs-lookup"><span data-stu-id="7941c-211">This works for any number of nested elements whose resources have color definitions.</span></span>

### <a name="scoping-with-a-resourcedictionary"></a><span data-ttu-id="7941c-212">Bereiche mit einem ResourceDictionary</span><span class="sxs-lookup"><span data-stu-id="7941c-212">Scoping with a ResourceDictionary</span></span>

<span data-ttu-id="7941c-213">Sie sind nicht auf einem Container oder den Ressourcen Seite beschränkt und können auch diese Systemfarben in einem ResourceDictionary, die dann zusammengeführt werden kann auf einem beliebigen Bereich die Möglichkeit, die Sie in der Regel ein Wörterbuch zusammenführen möchten.</span><span class="sxs-lookup"><span data-stu-id="7941c-213">You are not limited to a container or page’s resources, and can also define these system colors in a ResourceDictionary that can then be merged at any scope the way you normally would merge a dictionary.</span></span>

#### <a name="mycustomthemexaml"></a><span data-ttu-id="7941c-214">MyCustomTheme.xaml</span><span class="sxs-lookup"><span data-stu-id="7941c-214">MyCustomTheme.xaml</span></span>

<span data-ttu-id="7941c-215">Erstellen Sie zunächst ein ResourceDictionary.</span><span class="sxs-lookup"><span data-stu-id="7941c-215">First, you would create a ResourceDictionary.</span></span> <span data-ttu-id="7941c-216">Platzieren Sie die **ColorSchemeResources** innerhalb der ThemeDictionaries und überschreiben Sie die gewünschten Systemfarben:</span><span class="sxs-lookup"><span data-stu-id="7941c-216">Then place the **ColorSchemeResources** within the ThemeDictionaries and override the desired system colors:</span></span>

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

#### <a name="mainpagexaml"></a><span data-ttu-id="7941c-217">MainPage.xaml</span><span class="sxs-lookup"><span data-stu-id="7941c-217">MainPage.xaml</span></span>

<span data-ttu-id="7941c-218">Auf der Seite, das Layout enthält führen Sie einfach zusammen Sie diese Wörterbuch im an den gewünschten Bereich:</span><span class="sxs-lookup"><span data-stu-id="7941c-218">On the page containing your layout, simply merge that dictionary in at the scope you want:</span></span>

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

<span data-ttu-id="7941c-219">Nun können alle Ressourcen, Designs und benutzerdefinierte Farben in einem einzigen **MyCustomTheme** Ressourcenverzeichnis platziert und sein beschränkt, bei Bedarf ohne zusätzliche unübersichtliche in Ihrem Layout-Markup kümmern.</span><span class="sxs-lookup"><span data-stu-id="7941c-219">Now, all resources, theming, and custom colors can be placed in a single **MyCustomTheme** resource dictionary and scoped where needed without having to worry about extra clutter in your layout markup.</span></span>

### <a name="other-ways-to-define-color-resources"></a><span data-ttu-id="7941c-220">Andere Methoden, um die Farbressourcen definieren</span><span class="sxs-lookup"><span data-stu-id="7941c-220">Other ways to define color resources</span></span>

<span data-ttu-id="7941c-221">ColorSchemeResources kann auch Systemfarben platziert werden und als Wrapper, anstatt in Zeile direkt darin definieren:</span><span class="sxs-lookup"><span data-stu-id="7941c-221">ColorSchemeResources also allows for system colors to be placed and defining directly within it as a wrapper, rather than in line:</span></span>

``` xaml
<ColorSchemeResources x:Key="Dark">
    <Color x:Key="SystemBaseLowColor">Goldenrod</Color>
</ColorSchemeResources>
```

## <a name="usability"></a><span data-ttu-id="7941c-222">Benutzerfreundlichkeit</span><span class="sxs-lookup"><span data-stu-id="7941c-222">Usability</span></span>

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

## <a name="related-articles"></a><span data-ttu-id="7941c-223">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="7941c-223">Related articles</span></span>

- [<span data-ttu-id="7941c-224">XAML-Formatvorlagen</span><span class="sxs-lookup"><span data-stu-id="7941c-224">XAML Styles</span></span>](../controls-and-patterns/xaml-styles.md)
- [<span data-ttu-id="7941c-225">XAML-Designressourcen</span><span class="sxs-lookup"><span data-stu-id="7941c-225">XAML Theme Resources</span></span>](../controls-and-patterns/xaml-theme-resources.md)
