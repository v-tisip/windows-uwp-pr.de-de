---
author: Karl-Bridge-Microsoft
Description: Build UWP apps and custom/templated controls that support platform text scaling.
title: Textskalierung
label: Text scaling
template: detail.hbs
keywords: UWP, Text, Skalierung, Eingabehilfen, "erleichterte Bedienung", "Stellen Text größer", Benutzerinteraktion, Eingabe anzeigen
ms.author: kbridge
ms.date: 08/02/2018
ms.topic: article
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 3110615e43ffa4839d9be6ebf5113fc9d8b7c05f
ms.sourcegitcommit: 9f8010fe67bb3372db1840de9f0be36097ed6258
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "7105262"
---
# <a name="text-scaling"></a><span data-ttu-id="15156-103">Textskalierung</span><span class="sxs-lookup"><span data-stu-id="15156-103">Text scaling</span></span>

![Beispiel für Text, die Skalierung von 100 % auf 225 %](images/coretext/text-scaling-news-hero-small.png)  
*<span data-ttu-id="15156-105">Beispiel für Text, die Skalierung in Windows 10 (100 % bis 225 %)</span><span class="sxs-lookup"><span data-stu-id="15156-105">Example of text scaling in Windows 10 (100% to 225%)</span></span>*

## <a name="overview"></a><span data-ttu-id="15156-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="15156-106">Overview</span></span>

<span data-ttu-id="15156-107">Lesen von Text auf einem Computerbildschirm (von mobilen Gerät, Laptop, desktop-Monitor auf den riesigen Bildschirm von Surface Hub) kann für viele Benutzer schwierig sein.</span><span class="sxs-lookup"><span data-stu-id="15156-107">Reading text on a computer screen (from mobile device to laptop to desktop monitor to the giant screen of a Surface Hub) can be challenging for many people.</span></span> <span data-ttu-id="15156-108">Im Gegensatz dazu finden Sie einige Benutzer die Schriftgrade in apps und Websites verwendet, um größer als erforderlich sein.</span><span class="sxs-lookup"><span data-stu-id="15156-108">Conversely, some users find the font sizes used in apps and web sites to be larger than necessary.</span></span>

<span data-ttu-id="15156-109">Um sicherzustellen, dass Text lesbar ist wie die größtmögliche Anzahl von Benutzern möglich ist, bietet Windows die Möglichkeit für Benutzer, die relative Schriftgröße für das Betriebssystem und die einzelnen Anwendungen zu ändern.</span><span class="sxs-lookup"><span data-stu-id="15156-109">To ensure text is as legible as possible for the broadest range of users, Windows provides the ability for users to change relative font size across both the OS and individual applications.</span></span> <span data-ttu-id="15156-110">Anstatt mithilfe einer Bildschirmlupe-app (was in der Regel nur alles in einem Bereich des Bildschirms vergrößert und führt eine eigene Probleme hinsichtlich der Verwendbarkeit), das Ändern der Auflösung oder verlassen sich DPI-Skalierung (die alles basierend auf der Anzeige und typische Anzeige Größe Abstand), Benutzer können schnell zugreifen, eine Einstellung, um nur-Text, angefangen bei 100 % (die Standardgröße) Größe bis zu 225 %.</span><span class="sxs-lookup"><span data-stu-id="15156-110">Instead of using a magnifier app (which typically just enlarges everything within an area of the screen and introduces its own usability issues), changing display resolution, or relying on DPI scaling (which resizes everything based on display and typical viewing distance), a user can quickly access a setting to resize just text, ranging from 100% (the default size) up to 225%.</span></span>

## <a name="support"></a><span data-ttu-id="15156-111">Support</span><span class="sxs-lookup"><span data-stu-id="15156-111">Support</span></span>

<span data-ttu-id="15156-112">Universelle Windows-Anwendungen (sowohl Standard und PWA), Text standardmäßig Skalierung zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="15156-112">Universal Windows applications (both standard and PWA), support text scaling by default.</span></span>

<span data-ttu-id="15156-113">Wenn Ihre UWP-Anwendung benutzerdefinierte Steuerelemente, benutzerdefinierter Text Flächen, hartcodierten Steuerelement Höhen, älteren Frameworks oder 3rd Party-Frameworks enthält, müssen Sie wahrscheinlich einige Updates für eine konsistente und nützlich Erfahrung für Ihre Benutzer sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="15156-113">If your UWP application includes custom controls, custom text surfaces, hard-coded control heights, older frameworks, or 3rd party frameworks, you likely have to make some updates to ensure a consistent and useful experience for your users.</span></span>  

<span data-ttu-id="15156-114">DirectWrite, GDI und XAML-SwapChainPanels unterstützen nativ Text zu skalieren, keine während Win32-Unterstützung auf Menüs, Symbole und Symbolleisten begrenzt ist.</span><span class="sxs-lookup"><span data-stu-id="15156-114">DirectWrite, GDI, and XAML SwapChainPanels do not natively support text scaling, while Win32 support is limited to menus, icons, and toolbars.</span></span>  

<!-- If you want to support text scaling in your application with these frameworks, you’ll need to support the text scaling change event outlined below and provide alternative sizes for your UI and content.   -->

## <a name="user-experience"></a><span data-ttu-id="15156-115">Benutzerfreundlichkeit</span><span class="sxs-lookup"><span data-stu-id="15156-115">User experience</span></span>

<span data-ttu-id="15156-116">Benutzer können Textanzeige anpassen mit dem stellen Text größer Schieberegler in den Einstellungen -> -> erleichterte Bedienung Vision/Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="15156-116">Users can adjust text scale with the Make text bigger slider on the Settings -> Ease of Access -> Vision/Display screen.</span></span>

![Beispiel für Text, die Skalierung von 100 % auf 225 %](images/coretext/text-scaling-settings-100-small.png)  
*<span data-ttu-id="15156-118">Textanzeige von Einstellungen -> erleichterte Bedienung Vision/Bildschirm -></span><span class="sxs-lookup"><span data-stu-id="15156-118">Text scale setting from Settings -> Ease of Access -> Vision/Display screen</span></span>*

## <a name="ux-guidance"></a><span data-ttu-id="15156-119">Erläuterungen zur Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="15156-119">UX guidance</span></span>

<span data-ttu-id="15156-120">Wie Text geändert wird, Steuerelemente und Container müssen auch die Größe und umbrechen, um den Text und das neue Layout aufzunehmen.</span><span class="sxs-lookup"><span data-stu-id="15156-120">As text is resized, controls and containers must also resize and reflow to accommodate the text and its new layout.</span></span> <span data-ttu-id="15156-121">Wie bereits erwähnt abhängig von der app-Frameworks und -Plattform ist der Großteil der Arbeit für Sie erledigt.</span><span class="sxs-lookup"><span data-stu-id="15156-121">As mentioned previously, depending on the app, framework, and platform, much of this work is done for you.</span></span> <span data-ttu-id="15156-122">Die folgenden UX-Richtlinien werden diese Fälle, in denen es nicht behandelt.</span><span class="sxs-lookup"><span data-stu-id="15156-122">The following UX guidance covers those cases where it's not.</span></span>

### <a name="use-the-platform-controls"></a><span data-ttu-id="15156-123">Verwenden Sie die Plattformsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="15156-123">Use the platform controls</span></span>

<span data-ttu-id="15156-124">Sagten wir dies bereits?</span><span class="sxs-lookup"><span data-stu-id="15156-124">Did we say this already?</span></span> <span data-ttu-id="15156-125">Dabei ist zu wiederholen: Wenn möglich, müssen Sie die integrierten Steuerelemente mit den verschiedenen Windows-app-Frameworks bereitgestellten immer verwenden, um die umfassendste Benutzeroberfläche für wenig Aufwand wie möglich erhalten.</span><span class="sxs-lookup"><span data-stu-id="15156-125">It's worth repeating: When possible, always use the built-in controls provided with the various Windows app frameworks to get the most comprehensive user experience possible for the least amount of effort.</span></span>

<span data-ttu-id="15156-126">Alle UWP-Textsteuerelemente z. B. den vollständigen Text Skalierung Umgebung ohne Anpassung oder Templating unterstützen.</span><span class="sxs-lookup"><span data-stu-id="15156-126">For example, all UWP text controls support the full text scaling experience without any customization or templating.</span></span>

<span data-ttu-id="15156-127">Hier ist ein Codeausschnitt aus einer einfachen UWP-app, die eine Reihe von standard-Text-Steuerelemente enthält:</span><span class="sxs-lookup"><span data-stu-id="15156-127">Here's a snippet from a basic UWP app that includes a couple of standard text controls:</span></span>

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
*<span data-ttu-id="15156-129">Animierte Text skalieren</span><span class="sxs-lookup"><span data-stu-id="15156-129">Animated text scaling</span></span>*

### <a name="use-auto-sizing"></a><span data-ttu-id="15156-130">Verwenden von Auto-Größe</span><span class="sxs-lookup"><span data-stu-id="15156-130">Use auto-sizing</span></span>

<span data-ttu-id="15156-131">Geben Sie keine absolute Größen für Ihre Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="15156-131">Don't specify absolute sizes for your controls.</span></span> <span data-ttu-id="15156-132">Wann immer möglich, können Sie die Plattform, die Ihre Steuerelemente automatisch basierend auf Benutzer- und geräteeinstellungen zu ändern.</span><span class="sxs-lookup"><span data-stu-id="15156-132">Whenever possible, let the platform resize your controls automatically based on user and device settings.</span></span>  

<span data-ttu-id="15156-133">In diesem Codeausschnitt aus dem vorherigen Beispiel verwenden wir die `Auto` und `*` Breitenwerte für eine Gruppe von Grid Spalten und ermöglichen die Plattform passen Sie das app-Layout basierend auf der Größe der Elemente innerhalb des Rasters.</span><span class="sxs-lookup"><span data-stu-id="15156-133">In this snippet from the previous example, we use the `Auto` and `*` width values for a set of grid columns and let the platform adjust the app layout based on the size of the elements contained within the grid.</span></span>

``` xaml
<Grid.ColumnDefinitions>
    <ColumnDefinition Width="Auto"/>
    <ColumnDefinition Width="*"/>
    <ColumnDefinition Width="Auto"/>
</Grid.ColumnDefinitions>
```

### <a name="use-text-wrapping"></a><span data-ttu-id="15156-134">Verwenden Sie den Textumbruch</span><span class="sxs-lookup"><span data-stu-id="15156-134">Use text wrapping</span></span>

<span data-ttu-id="15156-135">Um sicherzustellen, dass das Layout Ihrer App als flexibel und anpassbar wie möglich ist, aktivieren Sie den Textumbruch in jedes Steuerelement, das Text enthält (viele Steuerelemente Textumbruch standardmäßig unterstützen keine).</span><span class="sxs-lookup"><span data-stu-id="15156-135">To ensure the layout of your app is as flexible and adaptable as possible, enable text wrapping in any control that contains text (many controls do not support text wrapping by default).</span></span>

<span data-ttu-id="15156-136">Wenn Sie den Textumbruch nicht angeben, verwendet die Plattform andere Methoden zum Anpassen des Layouts, einschließlich Zuschneiden (siehe vorherigen Beispiel).</span><span class="sxs-lookup"><span data-stu-id="15156-136">If you don't specify text wrapping, the platform uses other methods to adjust the layout, including clipping (see previous example).</span></span>

<span data-ttu-id="15156-137">Hier verwenden wir die `AcceptsReturn` und `TextWrapping` TextBox-Eigenschaften, um sicherzustellen, dass unsere Layout flexibel wie möglich ist.</span><span class="sxs-lookup"><span data-stu-id="15156-137">Here, we use the `AcceptsReturn` and `TextWrapping` TextBox properties to ensure our layout is as flexible as possible.</span></span>

``` xaml
<TextBox PlaceholderText="Type something here" 
          AcceptsReturn="True" TextWrapping="Wrap" />
```

![Animierter Text, die Skalierung von 100 % auf 225 % mit Textumbruch](images/coretext/text-scaling-textwrap.gif)  
*<span data-ttu-id="15156-139">Animierte Text Skalieren mit Textumbruch</span><span class="sxs-lookup"><span data-stu-id="15156-139">Animated text scaling with text wrapping</span></span>*

### <a name="specify-text-trimming-behavior"></a><span data-ttu-id="15156-140">Geben Sie Text Kürzung Verhalten</span><span class="sxs-lookup"><span data-stu-id="15156-140">Specify text trimming behavior</span></span>

<span data-ttu-id="15156-141">Wenn Textumbruch nicht Verhalten erwünscht ist, können die meisten Textsteuerelemente entweder Ihr Text zuschneiden, oder geben Sie Ellipsen für das Verhalten der Text Kürzung.</span><span class="sxs-lookup"><span data-stu-id="15156-141">If text wrapping is not the preferred behavior, most text controls let either clip your text or specify ellipses for the text trimming behavior.</span></span> <span data-ttu-id="15156-142">Zuschneiden wird bevorzugt, Ellipsen, als Ellipsen selbst Speicherplatz belegen.</span><span class="sxs-lookup"><span data-stu-id="15156-142">Clipping is preferred to ellipses as ellipses take up space themselves.</span></span>

> [!NOTE]
> <span data-ttu-id="15156-143">Wenn Sie Sie den Text zu beschneiden müssen, abgeschnitten Sie, das Ende der Zeichenfolge, die nicht am Anfang.</span><span class="sxs-lookup"><span data-stu-id="15156-143">If you need to clip your text, clip the end of the string, not the beginning.</span></span>

<span data-ttu-id="15156-144">In diesem Beispiel zeigen wir, wie Sie Text in einem TextBlock zu beschneiden mithilfe der [TextTrimming](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.textblock.texttrimming) -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="15156-144">In this example, we show how to clip text in a TextBlock using the [TextTrimming](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.textblock.texttrimming) property.</span></span>

``` xaml
<TextBlock TextTrimming="Clip">
    The quick brown fox jumped over the lazy dog.
</TextBlock>
```

![Skalierung von 100 % auf 225 % mit Text Zuschneiden Text](images/coretext/text-scaling-clipping-small.png)  
*<span data-ttu-id="15156-146">Text skalieren mit Text Zuschneiden</span><span class="sxs-lookup"><span data-stu-id="15156-146">Text scaling with text clipping</span></span>*

### <a name="use-a-tooltip"></a><span data-ttu-id="15156-147">Verwenden Sie eine QuickInfo</span><span class="sxs-lookup"><span data-stu-id="15156-147">Use a tooltip</span></span>

<span data-ttu-id="15156-148">Wenn Sie Text zuschneiden, verwenden Sie QuickInfos, um den vollständigen Text für Ihre Benutzer bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="15156-148">If you clip text, use a tooltip to provide the full text to your users.</span></span>

<span data-ttu-id="15156-149">Hier fügen wir eine QuickInfo in einem TextBlock-Element, die den Textumbruch nicht unterstützt:</span><span class="sxs-lookup"><span data-stu-id="15156-149">Here, we add a tooltip to a TextBlock that doesn't support text wrapping:</span></span>

``` xaml
<TextBlock TextTrimming="Clip">
    <ToolTipService.ToolTip>
        <ToolTip Content="The quick brown fox jumped over the lazy dog."/>
    </ToolTipService.ToolTip>
    The quick brown fox jumped over the lazy dog.
</TextBlock>
```

### <a name="dont-scale-font-based-icons-or-symbols"></a><span data-ttu-id="15156-150">Keine Schriftart-basierte Symbole oder Symbole skalieren</span><span class="sxs-lookup"><span data-stu-id="15156-150">Don’t scale font-based icons or symbols</span></span>

<span data-ttu-id="15156-151">Wenn Sie Symbole Schriftart-basierte zur Betonung oder als Ergänzung zu verwenden, deaktivieren Sie die Skalierung auf diese Zeichen.</span><span class="sxs-lookup"><span data-stu-id="15156-151">When using font-based icons for emphasis or decoration, disable scaling on these characters.</span></span>

<span data-ttu-id="15156-152">Legen Sie die Eigenschaft [IsTextScaleFactorEnabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.control.istextscalefactorenabled) auf `false` für die meisten XAML-Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="15156-152">Set the [IsTextScaleFactorEnabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.control.istextscalefactorenabled) property to `false` for most XAML controls.</span></span>

### <a name="support-text-scaling-natively"></a><span data-ttu-id="15156-153">Unterstützung für Text nativ Skalierung</span><span class="sxs-lookup"><span data-stu-id="15156-153">Support text scaling natively</span></span>

<span data-ttu-id="15156-154">Behandeln Sie das [TextScaleFactorChanged](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.uisettings.textscalefactorchanged) UISettings System-Ereignis in Ihren benutzerdefinierten Framework Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="15156-154">Handle the [TextScaleFactorChanged](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.uisettings.textscalefactorchanged) UISettings system event in your custom framework and controls.</span></span> <span data-ttu-id="15156-155">Dieses Ereignis wird jedes Mal ausgelöst, wenn der Benutzer den Skalierungsfaktor Text auf seinem System festlegt.</span><span class="sxs-lookup"><span data-stu-id="15156-155">This event is raised each time the user sets the text scaling factor on their system.</span></span>

## <a name="summary"></a><span data-ttu-id="15156-156">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="15156-156">Summary</span></span>

<span data-ttu-id="15156-157">Dieses Thema enthält eine Übersicht über Text-Unterstützung in Windows Skalierung und enthält (UX) und Entwickler Richtlinien zum Anpassen der Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="15156-157">This topic provides an overview of text scaling support in Windows and includes UX and developer guidance on how to customize the user experience.</span></span>

## <a name="related-articles"></a><span data-ttu-id="15156-158">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="15156-158">Related articles</span></span>

### <a name="api-reference"></a><span data-ttu-id="15156-159">API-Referenz</span><span class="sxs-lookup"><span data-stu-id="15156-159">API reference</span></span>

- [<span data-ttu-id="15156-160">IsTextScaleFactorEnabled</span><span class="sxs-lookup"><span data-stu-id="15156-160">IsTextScaleFactorEnabled</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.control.istextscalefactorenabled)
- [<span data-ttu-id="15156-161">TextScaleFactorChanged</span><span class="sxs-lookup"><span data-stu-id="15156-161">TextScaleFactorChanged</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.uisettings.textscalefactorchanged)
