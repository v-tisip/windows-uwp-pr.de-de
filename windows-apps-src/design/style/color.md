---
author: QuinnRadich
description: Hier erfahren Sie, wie Sie Akzentfarben und Designs in Ihren UWP-Apps verwenden.
title: Farbe in UWP-Apps
ms.author: quradic
ms.date: 4/7/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
design-contact: karenmui
ms.localizationpriority: medium
ms.openlocfilehash: 19f4d9cde6ee2bc9615f044f18bc5e8828ca1985
ms.sourcegitcommit: 4f6dc806229a8226894c55ceb6d6eab391ec8ab6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2018
ms.locfileid: "4089219"
---
# <a name="color"></a><span data-ttu-id="bb087-104">Farben</span><span class="sxs-lookup"><span data-stu-id="bb087-104">Color</span></span>

![Favoritenbild](images/header-color.svg)

<span data-ttu-id="bb087-106">Farbe bietet eine intuitive Möglichkeit, Informationen an Benutzer in Ihrer App zu übermitteln – sie kann Interaktivität anzuzeigen, Feedback auf Benutzeraktionen geben und Ihrer Benutzeroberfläche ein Gefühl von visueller Kontinuität vermitteln.</span><span class="sxs-lookup"><span data-stu-id="bb087-106">Color provides an intuitive way of communicating information to users in your app: it can be used to indicate interactivity, give feedback to user actions, and give your interface a sense of visual continuity.</span></span> 

<span data-ttu-id="bb087-107">In UWP-Apps werden die Farben in erster Linie durch Akzentfarbe und Design bestimmt.</span><span class="sxs-lookup"><span data-stu-id="bb087-107">In UWP apps, colors are primarily determined by accent color and theme.</span></span> <span data-ttu-id="bb087-108">In diesem Artikel erläutern wir, wie Sie die Farbe in Ihrer App verwenden können, und wie Sie Akzentfarben und Designressourcen verwenden, um Ihre UWP-App in jedem beliebigen Design-Kontext verwendet zu können.</span><span class="sxs-lookup"><span data-stu-id="bb087-108">In this article, we'll discuss how you can use color in your app, and how to use accent color and theme resources to make your UWP app usable in any theme context.</span></span> 

## <a name="color-principles"></a><span data-ttu-id="bb087-109">Farbprinzipien</span><span class="sxs-lookup"><span data-stu-id="bb087-109">Color principles</span></span>

:::row:::
    :::column:::
        **<span data-ttu-id="bb087-110">Verwenden Sie Farbe sinnvoll.</span><span class="sxs-lookup"><span data-stu-id="bb087-110">Use color meaningfully.</span></span>**
<span data-ttu-id="bb087-111">Wenn Farbe sparsam verwendet wird, um wichtige Elemente zu markieren, können sie eine Benutzeroberfläche erstellen, die flüssig und intuitiv ist.</span><span class="sxs-lookup"><span data-stu-id="bb087-111">When color is used sparingly to highlight important elements, it can help create a user interface that is fluid and intuitive.</span></span>
    :::column-end:::
    :::column:::
        **<span data-ttu-id="bb087-112">Verwenden Sie Farbe, um Interaktivität.</span><span class="sxs-lookup"><span data-stu-id="bb087-112">Use color to indicate interactivity.</span></span>**
<span data-ttu-id="bb087-113">Es ist sinnvoll, eine Farbe auszuwählen, die die interaktiven Elementen Ihrer Anwendung angibt.</span><span class="sxs-lookup"><span data-stu-id="bb087-113">It's a good idea to choose one color to indicate elements of your application that are interactive.</span></span> <span data-ttu-id="bb087-114">Beispielsweise verwenden viele Webseiten blauen Text, um einen Link zu kennzeichnen.</span><span class="sxs-lookup"><span data-stu-id="bb087-114">For example, many web pages use blue text to denote a hyperlink.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        **<span data-ttu-id="bb087-115">Farbe ist persönlich.</span><span class="sxs-lookup"><span data-stu-id="bb087-115">Color is personal.</span></span>**
<span data-ttu-id="bb087-116">Benutzer können unter Windows eine Akzentfarbe sowie ein helles oder dunkles Design auswählen, die sich auf der gesamten Benutzeroberfläche widerspiegeln.</span><span class="sxs-lookup"><span data-stu-id="bb087-116">In Windows, users can choose an accent color and a light or dark theme, which are reflected throughout their experience.</span></span> <span data-ttu-id="bb087-117">Sie können auswählen, wie Sie die Akzentfarbe des Benutzers und das Design in Ihre Anwendung integrieren, um ihrer Erfahrung zu personalisieren.</span><span class="sxs-lookup"><span data-stu-id="bb087-117">You can choose how to incorporate the user's accent color and theme into your application, personalizing their experience.</span></span>
    :::column-end:::
    :::column:::
        **<span data-ttu-id="bb087-118">Farbe ist kulturell.</span><span class="sxs-lookup"><span data-stu-id="bb087-118">Color is cultural.</span></span>**
<span data-ttu-id="bb087-119">Achten Sie darauf, wie Farben von Personen aus unterschiedlichen Kulturen interpretiert werden.</span><span class="sxs-lookup"><span data-stu-id="bb087-119">Consider how the colors you use will be interpreted by people from different cultures.</span></span> <span data-ttu-id="bb087-120">In einigen Kulturen wird die Farbe Blau z. B. mit Tugend und Schutz assoziiert, während sie in anderen Trauer darstellt.</span><span class="sxs-lookup"><span data-stu-id="bb087-120">For example, in some cultures the color blue is associated with virtue and protection, while in others it represents mourning.</span></span>
    :::column-end:::
:::row-end:::

## <a name="themes"></a><span data-ttu-id="bb087-121">Designs</span><span class="sxs-lookup"><span data-stu-id="bb087-121">Themes</span></span>

<span data-ttu-id="bb087-122">UWP-Apps können ein helles oder dunkles Anwendungsdesign verwenden.</span><span class="sxs-lookup"><span data-stu-id="bb087-122">UWP apps can use a light or dark application theme.</span></span> <span data-ttu-id="bb087-123">Das Design wirkt sich auf die Farben des App-Hintergrunds, Text, Symbole und [Standardsteuerelemente](../controls-and-patterns/index.md) aus.</span><span class="sxs-lookup"><span data-stu-id="bb087-123">The theme affects the colors of the app's background, text, icons, and [common controls](../controls-and-patterns/index.md).</span></span>

### <a name="light-theme"></a><span data-ttu-id="bb087-124">Helles Design</span><span class="sxs-lookup"><span data-stu-id="bb087-124">Light theme</span></span>

![Helles Design](images/color/light-theme.svg)

### <a name="dark-theme"></a><span data-ttu-id="bb087-126">Dunkles Design</span><span class="sxs-lookup"><span data-stu-id="bb087-126">Dark theme</span></span>

![Dunkles Design](images/color/dark-theme.svg)

<span data-ttu-id="bb087-128">Das Design der UWP-App folgt standardmäßig den Design-Einstellungen des Benutzers aus den Windows-Einstellungen oder dem Standarddesign des Geräts (d.h. dunkel auf XBox).</span><span class="sxs-lookup"><span data-stu-id="bb087-128">By default, your UWP app's theme is the user’s theme preference from Windows Settings or the device's default theme (i.e., dark on XBox).</span></span> <span data-ttu-id="bb087-129">Allerdings können Sie das Design für Ihre UWP-App festlegen.</span><span class="sxs-lookup"><span data-stu-id="bb087-129">However, you can set the theme for your UWP app.</span></span> 

### <a name="changing-the-theme"></a><span data-ttu-id="bb087-130">Ändern des Designs</span><span class="sxs-lookup"><span data-stu-id="bb087-130">Changing the theme</span></span>

<span data-ttu-id="bb087-131">Sie können Designs einfach ändern, indem Sie die **RequestedTheme**-Eigenschaft in `App.xaml`-Datei ändern:</span><span class="sxs-lookup"><span data-stu-id="bb087-131">You can change themes by changing the **RequestedTheme** property in your `App.xaml` file.</span></span>

```XAML
<Application
    x:Class="App9.App"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:App9"
    RequestedTheme="Dark">
</Application>
```

<span data-ttu-id="bb087-132">Das Entfernen der **RequestedTheme**-Eigenschaft bedeutet, dass die Anwendung die Systemeinstellungen des Benutzers verwendet.</span><span class="sxs-lookup"><span data-stu-id="bb087-132">Removing the **RequestedTheme** property means that your application will use the user’s system settings.</span></span>

<span data-ttu-id="bb087-133">Anwender können auch Designs mit hohem Kontrast verwenden, die eine kleine Palette von Farbkombinationen mit hohem Farbkontrast nutzen, durch die die Benutzeroberfläche leichter zu erkennen ist.</span><span class="sxs-lookup"><span data-stu-id="bb087-133">Users can also select the high contrast theme, which uses a small palette of contrasting colors that makes the interface easier to see.</span></span> <span data-ttu-id="bb087-134">In diesem Fall überschreibt das System Ihre RequestedTheme.</span><span class="sxs-lookup"><span data-stu-id="bb087-134">In that case, the system will override your RequestedTheme.</span></span>

### <a name="testing-themes"></a><span data-ttu-id="bb087-135">Testen von Designs</span><span class="sxs-lookup"><span data-stu-id="bb087-135">Testing themes</span></span>

<span data-ttu-id="bb087-136">Wenn Sie kein Design für Ihre App anfordern, sollten Sie unbedingt Ihre App in hellem und dunklem Design testen, um sicherzustellen, dass Ihre App unter allen Umständen lesbar ist.</span><span class="sxs-lookup"><span data-stu-id="bb087-136">If you don't request a theme for your app, make sure to test your app in both light and dark themes to ensure that your app will be legible in all conditions.</span></span>

<span data-ttu-id="bb087-137">**Hinweis:**: In Visual Studio ist das RequestedTheme standardmäßig hell, daher müssen Sie die RequestedTheme ändern, um beide zu testen.</span><span class="sxs-lookup"><span data-stu-id="bb087-137">**Note**: In Visual Studio, the default RequestedTheme is light, so you'll need to change the RequestedTheme to test both.</span></span>

## <a name="theme-brushes"></a><span data-ttu-id="bb087-138">Designpinsel</span><span class="sxs-lookup"><span data-stu-id="bb087-138">Theme brushes</span></span>

<span data-ttu-id="bb087-139">Allgemeine Steuerelemente verwenden automatisch [Designpinsel](../controls-and-patterns/xaml-theme-resources.md#the-xaml-color-ramp-and-theme-dependent-brushes), um den Kontrast für helle und dunkle Designs anzupassen.</span><span class="sxs-lookup"><span data-stu-id="bb087-139">Common controls automatically use [theme brushes](../controls-and-patterns/xaml-theme-resources.md#the-xaml-color-ramp-and-theme-dependent-brushes) to adjust contrast for light and dark themes.</span></span>

<span data-ttu-id="bb087-140">Hier ist eine Abbildung, wie [AutoSuggestBox](../controls-and-patterns/auto-suggest-box.md) die Designpinsel verwendet:</span><span class="sxs-lookup"><span data-stu-id="bb087-140">For example, here's an illustration of how the [AutoSuggestBox](../controls-and-patterns/auto-suggest-box.md) uses theme brushes:</span></span>

![Beispiel für Steuerelement-Designpinsel](images/color/theme-brushes.svg)

<span data-ttu-id="bb087-142">Die Designpinsel werden für folgende Zwecke verwendet:</span><span class="sxs-lookup"><span data-stu-id="bb087-142">The theme brushes are used for the following purposes:</span></span>

- <span data-ttu-id="bb087-143">**Base** gilt für Text.</span><span class="sxs-lookup"><span data-stu-id="bb087-143">**Base** is for text.</span></span>
- <span data-ttu-id="bb087-144">**ALT** ist das Gegenteil von Base.</span><span class="sxs-lookup"><span data-stu-id="bb087-144">**Alt** is the inverse of Base.</span></span>
- <span data-ttu-id="bb087-145">**Chrome** richtet sich an die Elemente der obersten Ebene, z.B. Navigationsbereich oder Befehlsleisten.</span><span class="sxs-lookup"><span data-stu-id="bb087-145">**Chrome** is for top-level elements, such as navigation panes or command bars.</span></span>
- <span data-ttu-id="bb087-146">**List** gilt für Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="bb087-146">**List** is for list controls.</span></span>

<span data-ttu-id="bb087-147">**Niedrig**/**Mittel**/**Hoch** beziehen sich auf die Intensität der Farben.</span><span class="sxs-lookup"><span data-stu-id="bb087-147">**Low**/**Medium**/**High** refer to the intensity of the color.</span></span>

### <a name="using-theme-brushes"></a><span data-ttu-id="bb087-148">Verwenden der Designpinsel</span><span class="sxs-lookup"><span data-stu-id="bb087-148">Using theme brushes</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="bb087-149">Beim Erstellen von Vorlagen für benutzerdefinierte Steuerelemente, verwenden Sie Designpinsel anstelle von hartcodierten Farbwerten.</span><span class="sxs-lookup"><span data-stu-id="bb087-149">When creating templates for custom controls, use theme brushes rather than hard code color values.</span></span> <span data-ttu-id="bb087-150">Auf diese Weise lässt sich Ihre App problemlos auf alle Designs anpassen.</span><span class="sxs-lookup"><span data-stu-id="bb087-150">This way, your app can easily adapt to any theme.</span></span>

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

<span data-ttu-id="bb087-151">Weitere Informationen zur Verwendung von Designpinseln in Ihrer App finden Sie unter [Designressourcen](../controls-and-patterns/xaml-theme-resources.md).</span><span class="sxs-lookup"><span data-stu-id="bb087-151">For more information about how to use theme brushes in your app, see [Theme Resources](../controls-and-patterns/xaml-theme-resources.md).</span></span>

## <a name="accent-color"></a><span data-ttu-id="bb087-152">Akzentfarbe</span><span class="sxs-lookup"><span data-stu-id="bb087-152">Accent color</span></span>

<span data-ttu-id="bb087-153">Allgemeine Steuerelemente verwenden eine Akzentfarbe, um die Zustandsinformationen zu vermitteln.</span><span class="sxs-lookup"><span data-stu-id="bb087-153">Common controls use an accent color to convey state information.</span></span> <span data-ttu-id="bb087-154">Standardmäßig ist die Akzentfarbe die `SystemAccentColor`, die der Benutzer in den Einstellungen auswählt.</span><span class="sxs-lookup"><span data-stu-id="bb087-154">By default, the accent color is the `SystemAccentColor` that users select in their Settings.</span></span> <span data-ttu-id="bb087-155">Sie können jedoch auch Akzentfarben entsprechend der Marke Ihrer App anpassen.</span><span class="sxs-lookup"><span data-stu-id="bb087-155">However, you can also customize your app's accent color to reflect your brand.</span></span>

![Windows-Steuerelemente](images/color/windows-controls.svg)

:::row:::
    :::column:::
        ![vom Benutzer ausgewählte Akzent-Header](images/color/user-accent.svg) ![vom Benutzer ausgewählte Akzentfarbe](images/color/user-selected-accent.svg)
    :::column-end:::
    :::column:::
        ![Benutzerdefinierte Akzentfarbe Header](images/color/custom-accent.svg) ![benutzerdefinierte Marke Akzentfarbe](images/color/brand-color.svg)
    :::column-end:::
:::row-end:::

### <a name="overriding-the-accent-color"></a><span data-ttu-id="bb087-159">Überschreiben der Akzentfarbe</span><span class="sxs-lookup"><span data-stu-id="bb087-159">Overriding the accent color</span></span>

<span data-ttu-id="bb087-160">Wenn Sie Ihre App-Akzentfarbe ändern möchten, platzieren Sie den folgenden Code in `app.xaml`.</span><span class="sxs-lookup"><span data-stu-id="bb087-160">To change your app's accent color, place the following code in `app.xaml`.</span></span>

```xaml
<Application.Resources>
    <ResourceDictionary>
        <Color x:Key="SystemAccentColor">#107C10</Color>
    </ResourceDictionary>
</Application.Resources>
```

### <a name="choosing-an-accent-color"></a><span data-ttu-id="bb087-161">Auswählen einer Akzentfarbe</span><span class="sxs-lookup"><span data-stu-id="bb087-161">Choosing an accent color</span></span>

<span data-ttu-id="bb087-162">Wenn Sie eine benutzerdefinierte Akzentfarbe für Ihre App auswählen, stellen Sie sicher, dass Text und Hintergrund, die die Akzentfarbe verwenden, ausreichenden Kontrast für eine optimale Lesbarkeit haben.</span><span class="sxs-lookup"><span data-stu-id="bb087-162">If you select a custom accent color for your app, please make sure that text and backgrounds that use the accent color have sufficient contrast for optimal readability.</span></span> <span data-ttu-id="bb087-163">Um den Kontrast zu testen, können Sie das Farbauswahltool in den Windows-Einstellungen verwenden, oder Sie können diese [online Kontrast-Tools nutzen](https://www.w3.org/TR/WCAG20-TECHS/G18.html#G18-resources).</span><span class="sxs-lookup"><span data-stu-id="bb087-163">To test contrast, you can use the color picker tool in Windows Settings, or you can use these [online contrast tools](https://www.w3.org/TR/WCAG20-TECHS/G18.html#G18-resources).</span></span>

![Benutzerdefinierter Akzentfarbwähler in den Windows-Einstellungen](images/color/color-picker.svg)

## <a name="accent-color-palette"></a><span data-ttu-id="bb087-165">Akzentfarbpalette</span><span class="sxs-lookup"><span data-stu-id="bb087-165">Accent color palette</span></span>

<span data-ttu-id="bb087-166">Ein Akzentfarbalgorithmus in der Windows-Shell generiert helle und dunkle Schattierungen der Akzentfarbe.</span><span class="sxs-lookup"><span data-stu-id="bb087-166">An accent color algorithm in the Windows shell generates light and dark shades of the accent color.</span></span>

![Akzentfarbpalette](images/color/accent-color-palette.svg)

<span data-ttu-id="bb087-168">Diese Schattierungen sind als [Designressourcen](../controls-and-patterns/xaml-theme-resources.md) verfügbar:</span><span class="sxs-lookup"><span data-stu-id="bb087-168">These shades can be accessed as [theme resources](../controls-and-patterns/xaml-theme-resources.md):</span></span>

- `SystemAccentColorLight3`
- `SystemAccentColorLight2`
- `SystemAccentColorLight1`
- `SystemAccentColorDark1`
- `SystemAccentColorDark2`
- `SystemAccentColorDark3`

<!-- check this is true -->
<span data-ttu-id="bb087-169">Sie können die Akzentfarbpalette auch programmgesteuert mit der [**UISettings.GetColorValue**](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.UISettings#Windows_UI_ViewManagement_UISettings_GetColorValue_Windows_UI_ViewManagement_UIColorType_)-Methode und [**UIColorType**](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.UIColorType)-Enumeration aufrufen.</span><span class="sxs-lookup"><span data-stu-id="bb087-169">You can also access the accent color palette programmatically with the [**UISettings.GetColorValue**](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.UISettings#Windows_UI_ViewManagement_UISettings_GetColorValue_Windows_UI_ViewManagement_UIColorType_) method and [**UIColorType**](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.UIColorType) enum.</span></span>

<span data-ttu-id="bb087-170">Sie können die Akzentfarbpalette für Designfarben in Ihrer App verwenden.</span><span class="sxs-lookup"><span data-stu-id="bb087-170">You can use the accent color palette for color theming in your app.</span></span> <span data-ttu-id="bb087-171">Hier ist ein Beispiel für die Verwendung der Akzentfarbpalette auf einer Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="bb087-171">Below is an example of how you can use the accent color palette on a button.</span></span>

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

<span data-ttu-id="bb087-173">Wenn Sie farbigen Text auf farbigem Hintergrund verwenden, stellen Sie sicher, dass genügend Kontrast zwischen Text und Hintergrund vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="bb087-173">When using colored text on a colored background, make sure there is enough contrast between text and background.</span></span> <span data-ttu-id="bb087-174">Standardmäßig werden Hyperlinks oder Hypertext in der Akzentfarbe des Benutzers dargestellt.</span><span class="sxs-lookup"><span data-stu-id="bb087-174">By default, hyperlink or hypertext will use the accent color.</span></span> <span data-ttu-id="bb087-175">Wenden Sie Varianten der Akzentfarbe im Hintergrund an, sollten Sie eine Variante der ursprüngliche Akzentfarbe verwenden, um den Kontrast von farbigem Text auf farbigem Hintergrund zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="bb087-175">If you apply variations of the accent color to the background, you should use a variation of the original accent color to optimize the contrast of colored text on a colored background.</span></span>

<span data-ttu-id="bb087-176">Das folgende Diagramm zeigt ein Beispiel für die unterschiedlichen Hell/Dunkel-Töne der Akzentfarbe, und gibt an, wie der Farbtyp auf einer farbige Oberfläche angewendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="bb087-176">The chart below illustrates an example of the various light/dark shades of accent color, and how colored type can be applied on a colored surface.</span></span>

![Farbe auf Farbe](images/color/color-on-color.svg)

<span data-ttu-id="bb087-178">Weitere Informationen zum Verwenden der Stil-Steuerelemente finden Sie unter [XAML-Style](../controls-and-patterns/xaml-styles.md).</span><span class="sxs-lookup"><span data-stu-id="bb087-178">For more information about styling controls, see [XAML styles](../controls-and-patterns/xaml-styles.md).</span></span>

## <a name="color-api"></a><span data-ttu-id="bb087-179">Farb-API</span><span class="sxs-lookup"><span data-stu-id="bb087-179">Color API</span></span>

<span data-ttu-id="bb087-180">Es gibt verschiedene APIs, um Farbe auf Ihrer Anwendung hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="bb087-180">There are several APIs that can be used to add color to your application.</span></span> <span data-ttu-id="bb087-181">Zuerst kommt die [**Farb**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.colors)-Klasse, die eine umfangreiche Liste vordefinierter Farben implementiert.</span><span class="sxs-lookup"><span data-stu-id="bb087-181">First, the [**Colors**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.colors) class, which implements a large list of predefined colors.</span></span> <span data-ttu-id="bb087-182">Auf diese kann automatisch mithilfe der XAML-Eigenschaften zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="bb087-182">These can be accessed automatically with XAML properties.</span></span> <span data-ttu-id="bb087-183">Im folgenden Beispiel erstellen wir eine Schaltfläche und legen Sie Farbeigenschaften im Hintergrund und Vordergrund auf Mitglieder der **Farb**-Klasse fest.</span><span class="sxs-lookup"><span data-stu-id="bb087-183">In the example below, we create a button and set the background and foreground color properties to members of the **Colors** class.</span></span>

```xaml
<Button Background="MediumSlateBlue" Foreground="White">Button text</Button>
```

<span data-ttu-id="bb087-184">Sie können Ihre eigenen Farben aus RGB- und hex-Werten mithilfe der [**Farb**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.color)-Struktur in XAML erstellen.</span><span class="sxs-lookup"><span data-stu-id="bb087-184">You can create your own colors from RGB or hex values using the [**Color**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.color) struct in XAML.</span></span>

```xaml
<Color x:Key="LightBlue">#FF36C0FF</Color>
```

<span data-ttu-id="bb087-185">Sie können auch die gleiche Farbe im Code mit der **FromArgb**-Methode erstellen.</span><span class="sxs-lookup"><span data-stu-id="bb087-185">You can also create the same color in code by using the **FromArgb** method.</span></span>

```csharp
Color LightBlue = Color.FromArgb(255,54,192,255);
```

<span data-ttu-id="bb087-186">Die Buchstaben "Argb" bedeutet Alpha (Deckkraft), Rot, Grün und Blau, die vier Komponenten einer Farbe.</span><span class="sxs-lookup"><span data-stu-id="bb087-186">The letters "Argb" stands for Alpha (opacity), Red, Green, and Blue, which are the four components of a color.</span></span> <span data-ttu-id="bb087-187">Jedes Argument reicht von 0 bis 255.</span><span class="sxs-lookup"><span data-stu-id="bb087-187">Each argument can range from 0 to 255.</span></span> <span data-ttu-id="bb087-188">Sie können den ersten Wert auslassen, was eine standardmäßige Deckkraft von 255 oder 100% undurchsichtig ergibt.</span><span class="sxs-lookup"><span data-stu-id="bb087-188">You can choose to omit the first value, which will give you a default opacity of 255, or 100% opaque.</span></span>

> [!Note]
> <span data-ttu-id="bb087-189">Wenn Sie C++ verwenden, müssen Sie Farben mit der [**ColorHelper**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.colorhelper)-Klasse erstellen.</span><span class="sxs-lookup"><span data-stu-id="bb087-189">If you're using C++, you must create colors by using the [**ColorHelper**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.colorhelper) class.</span></span>

<span data-ttu-id="bb087-190">Am häufigsten wird für eine **Farbe** ein Argument für [**SolidColorBrush**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.media.solidcolorbrush) verwendet, das zum Zeichnen von UI-Elementen im Volltonfarbe verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="bb087-190">The most common use for a **Color** is as an argument for a [**SolidColorBrush**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.media.solidcolorbrush), which can be used to paint UI elements a single solid color.</span></span> <span data-ttu-id="bb087-191">Diese Pinsel sind in der Regel durch das [**ResourceDictionary**](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.ResourceDictionary) definiert, sodass sie für mehrere Elemente wiederverwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="bb087-191">These brushes are generally defined in a [**ResourceDictionary**](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.ResourceDictionary), so they can be reused for multiple elements.</span></span>

```xaml
<ResourceDictionary>
    <SolidColorBrush x:Key="ButtonBackgroundBrush" Color="#FFFF4F67"/>
    <SolidColorBrush x:Key="ButtonForegroundBrush" Color="White"/>
</ResourceDictionary>
```

<span data-ttu-id="bb087-192">Weitere Informationen über die Verwendung der Pinsel finden Sie unter [XAML-Pinsel](brushes.md).</span><span class="sxs-lookup"><span data-stu-id="bb087-192">For more information on how to use brushes, see [XAML brushes](brushes.md).</span></span>

## <a name="usability"></a><span data-ttu-id="bb087-193">Benutzerfreundlichkeit</span><span class="sxs-lookup"><span data-stu-id="bb087-193">Usability</span></span>

:::row:::
    :::column:::
        ![Abbildung mit hohem Kontrast](images/color/illo-contrast.svg)
    :::column-end:::
    <span data-ttu-id="bb087-195">::: Column Span = "2"::: **Kontrast**</span><span class="sxs-lookup"><span data-stu-id="bb087-195">:::column span="2"::: **Contrast**</span></span>

        Make sure that elements and images have sufficient contrast to differentiate between them, regardless of the accent color or theme.

        When considering what colors to use in your application, accessiblity should be a primary concern. Use the guidance below to make sure your application is accessible to as many users as possible.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![Abbildung mit hohem Kontrast](images/color/illo-lighting.svg)
    :::column-end:::
    <span data-ttu-id="bb087-197">::: Column Span = "2"::: **Beleuchtung**</span><span class="sxs-lookup"><span data-stu-id="bb087-197">:::column span="2"::: **Lighting**</span></span>

        Be aware that variation in ambient lighting can affect the useability of your app. For example, a page with a black background might unreadable outside due to screen glare, while a page with a white background might be painful to look at in a dark room.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![Abbildung mit hohem Kontrast](images/color/illo-colorblindness.svg)
    :::column-end:::
    <span data-ttu-id="bb087-199">::: Column Span = "2"::: **Farbenblindheit**</span><span class="sxs-lookup"><span data-stu-id="bb087-199">:::column span="2"::: **Colorblindness**</span></span>

        Be aware of how colorblindness could affect the useability of your application. For example, a user with red-green colorblindness will have difficulty distinguishing red and green elements from each other. About **8 percent of men** and **0.5 percent of women** are red-green colorblind, so avoid using these color combinations as the sole differentiator between application elements.
    :::column-end:::
:::row-end:::

## <a name="related-articles"></a><span data-ttu-id="bb087-200">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="bb087-200">Related articles</span></span>

- [<span data-ttu-id="bb087-201">XAML-Formatvorlagen</span><span class="sxs-lookup"><span data-stu-id="bb087-201">XAML Styles</span></span>](../controls-and-patterns/xaml-styles.md)
- [<span data-ttu-id="bb087-202">XAML-Designressourcen</span><span class="sxs-lookup"><span data-stu-id="bb087-202">XAML Theme Resources</span></span>](../controls-and-patterns/xaml-theme-resources.md)