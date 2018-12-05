---
description: Anpassen der Titelleiste einer Desktop-App, damit sie das gleiche Erscheinungsbild wie die App aufweist
title: Anpassen der Titelleiste
template: detail.hbs
ms.date: 10/10/2017
ms.topic: article
keywords: Windows10, UWP, Titelleiste
doc-status: Draft
ms.localizationpriority: medium
ms.openlocfilehash: 88c613456525648883735850fe831cb3b67f145c
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8733779"
---
# <a name="title-bar-customization"></a><span data-ttu-id="02c06-104">Anpassen der Titelleiste</span><span class="sxs-lookup"><span data-stu-id="02c06-104">Title bar customization</span></span>



<span data-ttu-id="02c06-105">Wenn Ihre App in einem Desktop-Fenster ausgeführt wird, können Sie die Titelleisten der Fenster anpassen, damit sie das gleiche Erscheinungsbild wie die App aufweisen</span><span class="sxs-lookup"><span data-stu-id="02c06-105">When your app is running in a desktop window, you can customize the title bars to match the personality of your app.</span></span> <span data-ttu-id="02c06-106">Mit den APIs zur Anpassung der Titelleiste können Sie die Farben für die Elemente der Titelleiste angeben, oder Ihren App-Inhalte in den Bereich der Titelleiste anpassen und volle Kontrolle darüber erhalten.</span><span class="sxs-lookup"><span data-stu-id="02c06-106">The title bar customization APIs let you specify colors for title bar elements, or extend your app content into the title bar area and take full control of it.</span></span>

> <span data-ttu-id="02c06-107">**Wichtige APIs**: [ApplicationView.TitleBar-Eigenschaft](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview), [ApplicationViewTitleBar-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationviewtitlebar), [CoreApplicationViewTitleBar-Klasse](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplicationviewtitlebar)</span><span class="sxs-lookup"><span data-stu-id="02c06-107">**Important APIs**: [ApplicationView.TitleBar property](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview), [ApplicationViewTitleBar class](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationviewtitlebar), [CoreApplicationViewTitleBar class](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplicationviewtitlebar)</span></span>

## <a name="how-much-to-customize-the-title-bar"></a><span data-ttu-id="02c06-108">Ausmaße der Anpassung der Titelleiste</span><span class="sxs-lookup"><span data-stu-id="02c06-108">How much to customize the title bar</span></span>

<span data-ttu-id="02c06-109">Es gibt zwei Ebenen der Anpassung, die Sie auf der Titelleiste anwenden können.</span><span class="sxs-lookup"><span data-stu-id="02c06-109">There are two levels of customization that you can apply to the title bar.</span></span>

<span data-ttu-id="02c06-110">Um einfach die Farbe anzupassen, legen Sie die [ApplicationViewTitleBar](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationviewtitlebar)-Eigenschaften fest, um die Farben anzugeben, die Sie für die Elemente der Titelleiste verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="02c06-110">For simple color customization, you can set [ApplicationViewTitleBar](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationviewtitlebar) properties to specify the colors you want to use for title bar elements.</span></span> <span data-ttu-id="02c06-111">Das System behält in diesem Fall die Verantwortung für alle anderen angezeigten Aspekte der Titelleiste bei wie z.B. den App-Titel zeichnen und verschiebbare Bereiche definieren.</span><span class="sxs-lookup"><span data-stu-id="02c06-111">In this case, the system retains responsibility for all other aspects of the title bar, such as drawing the app title and defining draggable areas.</span></span>

<span data-ttu-id="02c06-112">Die andere Möglichkeit ist das Ausblenden der Standard-Titelleiste und das Ersetzen durch Ihren eigenen XAML-Inhalt.</span><span class="sxs-lookup"><span data-stu-id="02c06-112">Your other option is to hide the default title bar and replace it with your own XAML content.</span></span> <span data-ttu-id="02c06-113">Sie können z.B. Text, Schaltflächen oder benutzerdefinierte Menüs im Bereich der Titelleiste platzieren.</span><span class="sxs-lookup"><span data-stu-id="02c06-113">For example, you can place text, buttons, or custom menus in the title bar area.</span></span> <span data-ttu-id="02c06-114">Sie müssen ebenfalls diese Option verwenden, um einen [Acryl](../style/acrylic.md)-Hintergrund in den Bereich der Titelleiste einzufügen.</span><span class="sxs-lookup"><span data-stu-id="02c06-114">You will also need to use this option to extend an [acrylic](../style/acrylic.md) background into the title bar area.</span></span>

<span data-ttu-id="02c06-115">Wenn Sie ein umfassendes Anpassen wünschen, sind Sie für das Ablegen von Inhalten im Bereich der Titelleiste verantwortlich, und Sie können Ihren eigenen verschiebbaren Bereich definieren.</span><span class="sxs-lookup"><span data-stu-id="02c06-115">When you opt for full customization, you are responsible for putting content in the title bar area, and you can define your own draggable region.</span></span> <span data-ttu-id="02c06-116">Die Minimieren-, Maximieren-, Zurück- und Schließ-Schaltflächen sind auch weiterhin verfügbar und vom System verwaltet. Elemente wie z.B. der App-Titel gehören jedoch nicht dazu.</span><span class="sxs-lookup"><span data-stu-id="02c06-116">The system Back, Close, Minimize, and Maximize buttons are still available and handled by the system, but elements like the app title are not.</span></span> <span data-ttu-id="02c06-117">Sie müssen diese Elemente selbst und je nach Anforderungen Ihrer App erstellen.</span><span class="sxs-lookup"><span data-stu-id="02c06-117">You will need to create those elements yourself as needed by your app.</span></span>

> [!NOTE]
> <span data-ttu-id="02c06-118">Das einfache Anpassen der Farbe ist für UWP-Apps mit XAML, DirectX und HTML verfügbar.</span><span class="sxs-lookup"><span data-stu-id="02c06-118">Simple color customization is available to UWP apps using XAML, DirectX, and HTML.</span></span> <span data-ttu-id="02c06-119">Das umfassende Anpassen ist nur für UWP-Apps mit XAML verfügbar.</span><span class="sxs-lookup"><span data-stu-id="02c06-119">Full customization is available only to UWP apps using XAML.</span></span>

## <a name="simple-color-customization"></a><span data-ttu-id="02c06-120">Einfaches Anspassen der Farbe</span><span class="sxs-lookup"><span data-stu-id="02c06-120">Simple color customization</span></span>

<span data-ttu-id="02c06-121">Wenn Sie nur die Farben der Titelleiste und keine weitere Aktion anpassen möchten (z.B. Registerkarten in der Titelleiste einfügen) können Sie die Eigenschaften auf der [ApplicationViewTitleBar](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationviewtitlebar) für Ihre App-Fenster festlegen.</span><span class="sxs-lookup"><span data-stu-id="02c06-121">If you want only to customize the title bar colors and not do anything too fancy (such as putting tabs in your title bar), you can set the color properties on the [ApplicationViewTitleBar](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationviewtitlebar) for your app window.</span></span>

<span data-ttu-id="02c06-122">Dieses Beispiel zeigt, wie Sie eine Instanz der ApplicationViewTitleBar aufrufen und die Farbeigenschaften festlegen.</span><span class="sxs-lookup"><span data-stu-id="02c06-122">This example shows how to get an instance of ApplicationViewTitleBar and set its color properties.</span></span>

```csharp
// using Windows.UI.ViewManagement;

var titleBar = ApplicationView.GetForCurrentView().TitleBar;

// Set active window colors
titleBar.ForegroundColor = Windows.UI.Colors.White;
titleBar.BackgroundColor = Windows.UI.Colors.Green;
titleBar.ButtonForegroundColor = Windows.UI.Colors.White;
titleBar.ButtonBackgroundColor = Windows.UI.Colors.SeaGreen;
titleBar.ButtonHoverForegroundColor = Windows.UI.Colors.White;
titleBar.ButtonHoverBackgroundColor = Windows.UI.Colors.DarkSeaGreen;
titleBar.ButtonPressedForegroundColor = Windows.UI.Colors.Gray;
titleBar.ButtonPressedBackgroundColor = Windows.UI.Colors.LightGreen;

// Set inactive window colors
titleBar.InactiveForegroundColor = Windows.UI.Colors.Gray;
titleBar.InactiveBackgroundColor = Windows.UI.Colors.SeaGreen;
titleBar.ButtonInactiveForegroundColor = Windows.UI.Colors.Gray;
titleBar.ButtonInactiveBackgroundColor = Windows.UI.Colors.SeaGreen;
```

> [!NOTE]
> <span data-ttu-id="02c06-123">Dieser Code kann in die [OnLaunched](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application.onlaunched)-Methode Ihre App eingefügt werden (_App.xaml.cs_) – nach dem Aufruf von [Window.Activate](https://docs.microsoft.com/uwp/api/windows.ui.xaml.window.Activate) oder auf der ersten Seite Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="02c06-123">This code can be placed in your app's [OnLaunched](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application.onlaunched) method (_App.xaml.cs_), after the call to [Window.Activate](https://docs.microsoft.com/uwp/api/windows.ui.xaml.window.Activate), or in your app's first page.</span></span>

> [!TIP]
> <span data-ttu-id="02c06-124">Das Windows Community Toolkit enthält Erweiterungen, mit denen Sie diese Farbeigenschaften in XAML festlegen können.</span><span class="sxs-lookup"><span data-stu-id="02c06-124">The Windows Community Toolkit provides extensions that let you set these color properties in XAML.</span></span> <span data-ttu-id="02c06-125">Weitere Informationen finden Sie in der [Windows Community Toolkit-Dokumentation](https://docs.microsoft.com/windows/uwpcommunitytoolkit/extensions/viewextensions).</span><span class="sxs-lookup"><span data-stu-id="02c06-125">For more info, see the [Windows Community Toolkit documentation](https://docs.microsoft.com/windows/uwpcommunitytoolkit/extensions/viewextensions).</span></span>

<span data-ttu-id="02c06-126">Es gibt einige Dinge, die beim Festlegen von Farben für Titelleisten beachtet werden müssen:</span><span class="sxs-lookup"><span data-stu-id="02c06-126">There are a few things to be aware of when setting title bar colors:</span></span>

- <span data-ttu-id="02c06-127">Die Hintergrundfarbe der Schaltfläche wird nicht auf den Zeigeeffekt und das Gedrückthalten der Schaltfläche "Schließen" angewendet.</span><span class="sxs-lookup"><span data-stu-id="02c06-127">The button background color is not applied to the close button hover and pressed states.</span></span> <span data-ttu-id="02c06-128">Die Schaltfläche "Schließen" verwendet immer die systemdefinierte Farbe für diese Zustände.</span><span class="sxs-lookup"><span data-stu-id="02c06-128">The close button always uses the system-defined color for those states.</span></span>
- <span data-ttu-id="02c06-129">Die Farbeigenschaften der Schaltfläche gelten für die Systemschaltfläche "Zurück", wenn sie verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="02c06-129">The button color properties are applied to the system back button when it's used.</span></span> <span data-ttu-id="02c06-130">([Siehe Navigationsverlauf und Rückwärtsnavigation](../basics/navigation-history-and-backwards-navigation.md).)</span><span class="sxs-lookup"><span data-stu-id="02c06-130">([See Navigation history and backwards navigation](../basics/navigation-history-and-backwards-navigation.md).)</span></span>
- <span data-ttu-id="02c06-131">Das Festlegen der Farbeigenschaft auf **null** setzt es auf die Standardfarbe für das System zurück.</span><span class="sxs-lookup"><span data-stu-id="02c06-131">Setting a color property to **null** resets it to the default system color.</span></span>
- <span data-ttu-id="02c06-132">Sie können keine transparenten Farben festlegen.</span><span class="sxs-lookup"><span data-stu-id="02c06-132">You can't set transparent colors.</span></span> <span data-ttu-id="02c06-133">Die Alpha-Farbkanal wird ignoriert.</span><span class="sxs-lookup"><span data-stu-id="02c06-133">The color's alpha channel is ignored.</span></span>

<span data-ttu-id="02c06-134">Windows bietet dem Benutzer die Möglichkeit, die ausgewählte [Akzentfarbe](https://docs.microsoft.com/windows/uwp/style/color#accent-color) auf die Titelleiste anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="02c06-134">Windows gives a user the option to apply their selected [accent color](https://docs.microsoft.com/windows/uwp/style/color#accent-color) to the title bar.</span></span> <span data-ttu-id="02c06-135">Wenn Sie eine Titelfarbe festlegen, wird empfohlen, dass Sie alle Farben explizit festlegen.</span><span class="sxs-lookup"><span data-stu-id="02c06-135">If you set any title bar color, we recommend that you explicitly set all the colors.</span></span> <span data-ttu-id="02c06-136">Dadurch wird sichergestellt, dass keine unerwünschten Farbkombinationen erhalten werden, die bei benutzerdefinierten Farbeinstellungen auftreten.</span><span class="sxs-lookup"><span data-stu-id="02c06-136">This ensures that there are no unintended color combinations that occur because of user defined color settings.</span></span>

## <a name="full-customization"></a><span data-ttu-id="02c06-137">Die umfassende Anpassung</span><span class="sxs-lookup"><span data-stu-id="02c06-137">Full customization</span></span>

<span data-ttu-id="02c06-138">Wenn Sie die umfassende Anpassung der Titelleiste wünschen, wird Ihr App-Clientbereich über das gesamte Fenster erweitert, einschließlich des Bereichs der Titelleiste.</span><span class="sxs-lookup"><span data-stu-id="02c06-138">When you opt-in to full title bar customization, your app’s client area is extended to cover the entire window, including the title bar area.</span></span> <span data-ttu-id="02c06-139">Sie sind für das Zeichnen und die Eingabe-Behandlung für das gesamte Fenster mit Ausnahme der Titelleistenschaltfläche verantwortlich, die auf dem App-Canvas überlagert werden.</span><span class="sxs-lookup"><span data-stu-id="02c06-139">You are responsible for drawing and input-handling for the entire window except the caption buttons, which are overlaid on top of the app’s canvas.</span></span>

<span data-ttu-id="02c06-140">Legen Sie zum Ausblenden der Standard-Titelleiste und zum Erweitern des Inhalts in den Bereich der Titelleiste die [CoreApplicationViewTitleBar.ExtendViewIntoTitleBar](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplicationviewtitlebar)-Eigenschaft auf **true** fest.</span><span class="sxs-lookup"><span data-stu-id="02c06-140">To hide the default title bar and extend your content into the title bar area, set the [CoreApplicationViewTitleBar.ExtendViewIntoTitleBar](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplicationviewtitlebar) property to **true**.</span></span>

<span data-ttu-id="02c06-141">Dieses Beispiel zeigt, wie Sie die CoreApplicationViewTitleBar erhalten und legen die Eigenschaft ExtendViewIntoTitleBar auf **true** fest.</span><span class="sxs-lookup"><span data-stu-id="02c06-141">This example shows how to get the CoreApplicationViewTitleBar and set the ExtendViewIntoTitleBar property to **true**.</span></span> <span data-ttu-id="02c06-142">Dies kann in der [OnLaunched](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application.onlaunched)-Methode der App (_App.xaml.cs_) oder auf der ersten Seite Ihrer App durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="02c06-142">This can be done in your app's [OnLaunched](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application.onlaunched) method (_App.xaml.cs_), or in your app's first page.</span></span>

```csharp
// using Windows.ApplicationModel.Core;

// Hide default title bar.
var coreTitleBar = CoreApplication.GetCurrentView().TitleBar;
coreTitleBar.ExtendViewIntoTitleBar = true;
```

> [!TIP]
> <span data-ttu-id="02c06-143">Diese Einstellung wird beibehalten, wenn Ihre App beendet und neu gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="02c06-143">This setting persists when your app is closed and restarted.</span></span> <span data-ttu-id="02c06-144">Wenn Sie in Visual Studio ExtendViewIntoTitleBar auf **true** festlegen und dann die Standardeinstellungen wiederherstellen möchten, sollten Sie es explizit auf **false** festlegen und Ihre App ausführen, um die beibehaltene Einstellung zu überschrieben.</span><span class="sxs-lookup"><span data-stu-id="02c06-144">In Visual Studio, if you set ExtendViewIntoTitleBar to **true**, and then want to revert to the default, you should explicitly set it to **false** and run your app to overwrite the persisted setting.</span></span>

### <a name="draggable-regions"></a><span data-ttu-id="02c06-145">Ziehbare Bereiche</span><span class="sxs-lookup"><span data-stu-id="02c06-145">Draggable regions</span></span>

<span data-ttu-id="02c06-146">Der ziehbare Bereich der Titelleiste definiert, worauf der Benutzer klicken das Fenster verschieben kann (im Gegensatz zum einfachen Ziehen von Inhalten innerhalb des App-Canvas).</span><span class="sxs-lookup"><span data-stu-id="02c06-146">The draggable region of the title bar defines where the user can click and drag to move the window around (as opposed to simply dragging content within the app’s canvas).</span></span> <span data-ttu-id="02c06-147">Sie geben den ziehbaren Bereich durch Aufrufen der [Window.SetTitleBar](https://docs.microsoft.com/uwp/api/windows.ui.xaml.window.settitlebar)-Methode und der Übergabe eines UIElements an, das den verschiebbare Bereich definiert.</span><span class="sxs-lookup"><span data-stu-id="02c06-147">You specify the draggable region by calling the [Window.SetTitleBar](https://docs.microsoft.com/uwp/api/windows.ui.xaml.window.settitlebar) method and passing in a UIElement that defines the draggable region.</span></span> <span data-ttu-id="02c06-148">(Das UIElement ist häufig ein Panel, das andere Elemente enthält.)</span><span class="sxs-lookup"><span data-stu-id="02c06-148">(The UIElement is often a panel that contains other elements.)</span></span>

<span data-ttu-id="02c06-149">Hier erfahren Sie, wie ein Raster mit Inhalten als ziehbare Region der Titelleiste festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="02c06-149">Here's how to set a Grid of content as the draggable title bar region.</span></span> <span data-ttu-id="02c06-150">Dieser Code wird XAML und CodeBehind für die erste Seite Ihrer App hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="02c06-150">This code goes in the XAML and code-behind for your app's first page.</span></span> <span data-ttu-id="02c06-151">Den vollständigen Code finden Sie im Abschnitt [umfassendes Anpassungsbeispiel](./title-bar.md#full-customization-example).</span><span class="sxs-lookup"><span data-stu-id="02c06-151">See the [Full customization example](./title-bar.md#full-customization-example) section for the full code.</span></span>

```xaml
<Grid x:Name="AppTitleBar" Background="Transparent">
    <!-- Width of the padding columns is set in LayoutMetricsChanged handler. -->
    <!-- Using padding columns instead of Margin ensures that the background
         paints the area under the caption control buttons (for transparent buttons). -->
    <Grid.ColumnDefinitions>
        <ColumnDefinition x:Name="LeftPaddingColumn" Width="0"/>
        <ColumnDefinition/>
        <ColumnDefinition x:Name="RightPaddingColumn" Width="0"/>
    </Grid.ColumnDefinitions>
    <Image Source="Assets/Square44x44Logo.png" 
           Grid.Column="1" HorizontalAlignment="Left" 
           Width="20" Height="20" Margin="12,0"/>
    <TextBlock Text="Custom Title Bar" 
               Grid.Column="1" 
               Style="{StaticResource CaptionTextBlockStyle}" 
               Margin="44,8,0,0"/>
</Grid>
```

```csharp
public MainPage()
{
    this.InitializeComponent();

    var coreTitleBar = CoreApplication.GetCurrentView().TitleBar;
    coreTitleBar.ExtendViewIntoTitleBar = true;

    // Set XAML element as a draggable region.
    AppTitleBar.Height = coreTitleBar.Height;
    Window.Current.SetTitleBar(AppTitleBar);
}
```

<span data-ttu-id="02c06-152">UIElement (`AppTitleBar`) ist Teil des XAML-Codes für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="02c06-152">The UIElement (`AppTitleBar`) is part of the XAML for your app.</span></span> <span data-ttu-id="02c06-153">Sie können die Titelleiste entweder in einer Stammseite deklarieren und festlegen, die sich nicht ändert, oder eine Region der Titelleiste auf jeder Seite deklarieren und festlegen, auf die Ihre App navigieren kann.</span><span class="sxs-lookup"><span data-stu-id="02c06-153">You can either declare and set the title bar in a root page that doesn’t change, or declare and set a title bar region in each page that your app can navigate to.</span></span> <span data-ttu-id="02c06-154">Wenn Sie diese auf jeder Seite festlegen, sollten Sie sicherstellen, dass der ziehbare Bereich konsistent bleibt, wenn ein Benutzer in Ihrer App navigiert.</span><span class="sxs-lookup"><span data-stu-id="02c06-154">If you set it in each page, you should make sure the draggable region stays consistent as a user navigates around your app.</span></span>

<span data-ttu-id="02c06-155">Rufen Sie SetTitleBar auf, um auf ein neues Titelleisten-Element zu wechseln, während die App ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="02c06-155">You can call SetTitleBar to switch to a new title bar element while your app is running.</span></span> <span data-ttu-id="02c06-156">Sie können auch **null** als Parameter für SetTitleBar übergeben, um das standardmäßige Ziehverhalten wiederherzustellen.</span><span class="sxs-lookup"><span data-stu-id="02c06-156">You can also pass **null** as the parameter to SetTitleBar to revert to the default dragging behavior.</span></span> <span data-ttu-id="02c06-157">(Siehe "Ziehbarer Standardbereich" für weitere Informationen).</span><span class="sxs-lookup"><span data-stu-id="02c06-157">(See "Default draggable region" for more info.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="02c06-158">Der ziehbare Bereich muss auf Treffer getestet werden, d. h. Sie müssen für einige Elemente möglicherweise einen transparenten Hintergrundpinsel festlegen.</span><span class="sxs-lookup"><span data-stu-id="02c06-158">The draggable region you specify needs to be hit testable, which means, for some elements, you might need to set a transparent background brush.</span></span> <span data-ttu-id="02c06-159">Weitere Informationen finden Sie in den Hinweisen auf [VisualTreeHelper.FindElementsInHostCoordinates](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.visualtreehelper.findelementsinhostcoordinates).</span><span class="sxs-lookup"><span data-stu-id="02c06-159">See the remarks on [VisualTreeHelper.FindElementsInHostCoordinates](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.visualtreehelper.findelementsinhostcoordinates) for more info.</span></span>
>
><span data-ttu-id="02c06-160">Wenn Sie ein Raster als ziehbare Region definieren, legen Sie z.B. `Background="Transparent"` fest, um es ziehbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="02c06-160">For example, if you define a Grid as your draggable region, set `Background="Transparent"` to make it draggable.</span></span>
>
><span data-ttu-id="02c06-161">Dieses Raster wird nicht gezogen (nur die sichtbaren Elemente darin): `<Grid x:Name="AppTitleBar">`.</span><span class="sxs-lookup"><span data-stu-id="02c06-161">This Grid is not draggable (but visible elements within it are): `<Grid x:Name="AppTitleBar">`.</span></span>
>
><span data-ttu-id="02c06-162">Dieses Raster sieht genauso aus, das gesamte Raster ist allerdings ziehbar: `<Grid x:Name="AppTitleBar" Background="Transparent">`.</span><span class="sxs-lookup"><span data-stu-id="02c06-162">This Grid looks the same, but the whole Grid is draggable: `<Grid x:Name="AppTitleBar" Background="Transparent">`.</span></span>

#### <a name="default-draggable-region"></a><span data-ttu-id="02c06-163">Ziehbarer Standardbereich</span><span class="sxs-lookup"><span data-stu-id="02c06-163">Default draggable region</span></span>

<span data-ttu-id="02c06-164">Wenn Sie keinen ziehbaren Bereich angeben, wird ein Rechteck, das die Breite des Fensters und die Höhe der Titelleistenschaltfläche hat, am oberen Rand des Fensters positioniert und als ziehbare Standardregion festgelegt.</span><span class="sxs-lookup"><span data-stu-id="02c06-164">If you don’t specify a draggable region, a rectangle that is the width of the window, the height of the caption buttons, and positioned along the top edge of the window is set as the default draggable region.</span></span>

<span data-ttu-id="02c06-165">Wenn Sie einen verschiebbare Bereich definieren, verkleinert das System die ziehbaren Standardregion auf einen kleinen Bereich der Größe der Titelleistenschaltfläche, der links neben der Titelleistenschaltfläche (oder auf der rechten Seite der Titelleistenschaltfläche auf der linken Seite des Fensters) positioniert wird.</span><span class="sxs-lookup"><span data-stu-id="02c06-165">If you do define a draggable region, the system shrinks the default draggable region down to a small area the size of a caption button, positioned to the left of the caption buttons (or to the right if the captions buttons are on the left side of the window).</span></span> <span data-ttu-id="02c06-166">Dadurch wird sichergestellt, dass immer ein konsistenter Bereich vorhanden ist, den der Benutzer ziehen kann.</span><span class="sxs-lookup"><span data-stu-id="02c06-166">This ensures that there is always a consistent area the user can drag.</span></span>

### <a name="system-caption-buttons"></a><span data-ttu-id="02c06-167">System-Titelleistenschaltflächen</span><span class="sxs-lookup"><span data-stu-id="02c06-167">System caption buttons</span></span>

<span data-ttu-id="02c06-168">Das System reserviert die obere linke oder obere rechte Ecke des App-Fensters für die Titelleistenschaltflächen des Systems (Minimieren-, Maximieren-, Zurück- und Schließ-Schaltflächen).</span><span class="sxs-lookup"><span data-stu-id="02c06-168">The system reserves the upper-left or upper-right corner of the app window for the system caption buttons (Back, Minimize, Maximize, Close).</span></span> <span data-ttu-id="02c06-169">Das System behält die Kontrolle über den Titelleistensteuerungsbereich, um die Mindestfunktionen für das Ziehen, Minimieren, Maximieren und Schließen des Fensters zu garantieren.</span><span class="sxs-lookup"><span data-stu-id="02c06-169">The system retains control of the caption control area to guarantee that minimum functionality is provided for dragging, minimizing, maximizing, and closing the window.</span></span> <span data-ttu-id="02c06-170">Das System zeichnet die Schaltfläche "Schließen" in der oberen rechten Ecke für von links nach rechts gelesene Sprachen und die linke obere Ecke für von rechts nach links gelesene Sprachen.</span><span class="sxs-lookup"><span data-stu-id="02c06-170">The system draws the Close button in the upper-right for left-to-right languages and the upper-left for right-to-left languages.</span></span>

<span data-ttu-id="02c06-171">Die Größe und Position des Titelleistensteuerungsbereichs wird von der CoreApplicationViewTitleBar-Klasse mitgeteilt, damit Sie das Layout der Titel Ihrer Benutzeroberfläche berücksichtigen können.</span><span class="sxs-lookup"><span data-stu-id="02c06-171">The dimensions and position of the caption control area is communicated by the CoreApplicationViewTitleBar class so that you can account for it in the layout of your title bar UI.</span></span> <span data-ttu-id="02c06-172">Die Breite der reservierten Region auf jeder Seite wird durch die [SystemOverlayLeftInset](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplicationviewtitlebar.SystemOverlayLeftInset) oder [SystemOverlayRightInset](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplicationviewtitlebar.SystemOverlayRightInset)-Eigenschaften angegeben und die Höhe wird durch die [Height](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplicationviewtitlebar.Height)-Eigenschaft angegeben.</span><span class="sxs-lookup"><span data-stu-id="02c06-172">The width of the reserved region on each side is given by the [SystemOverlayLeftInset](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplicationviewtitlebar.SystemOverlayLeftInset) or [SystemOverlayRightInset](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplicationviewtitlebar.SystemOverlayRightInset) properties, and its height is given by the [Height](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplicationviewtitlebar.Height) property.</span></span>

<span data-ttu-id="02c06-173">Sie können Inhalte unter den Titelleistensteuerungsbereich zeichnen, der von diesen Eigenschaften definiert wird wie z.B. Ihren App-Hintergrund, aber Sie sollten kein Benutzeroberflächenelemente dort zeichnen, mit denen der Benutzer interagieren kann.</span><span class="sxs-lookup"><span data-stu-id="02c06-173">You can draw content underneath the caption control area defined by these properties, such as your app background, but you should not put any UI that you expect the user to be able to interact with.</span></span> <span data-ttu-id="02c06-174">Er erhält keine Eingaben, da die Eingabe für die Titelsteuerungen vom System behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="02c06-174">It does not receive any input because input for the caption controls is handled by the system.</span></span>

<span data-ttu-id="02c06-175">Sie können das [LayoutMetricsChanged](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplicationviewtitlebar.LayoutMetricsChanged)-Ereignis so festlegen, dass es auf die Änderungen der Größe der Titelleistenschaltfläche reagiert.</span><span class="sxs-lookup"><span data-stu-id="02c06-175">You can handle the [LayoutMetricsChanged](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplicationviewtitlebar.LayoutMetricsChanged) event to respond to changes in the size of the caption buttons.</span></span> <span data-ttu-id="02c06-176">Dies kann beispielsweise der Fall sein, wenn die Schaltfläche des Systems „Zurück” angezeigt oder ausgeblendet wird.</span><span class="sxs-lookup"><span data-stu-id="02c06-176">For example, this can happen when the system back button is shown or hidden.</span></span> <span data-ttu-id="02c06-177">Verwenden Sie dieses Ereignis, um das Positionieren von Benutzeroberflächenelementen zu überprüfen und aktualisieren, die von der Größe der Titelleiste abhängen.</span><span class="sxs-lookup"><span data-stu-id="02c06-177">Handle this event to verify and update the positioning of UI elements that depend on the title bar's size.</span></span>

<span data-ttu-id="02c06-178">In diesem Beispiel wird veranschaulicht, wie das Layouts der Titelleiste für Änderungen der Systemschaltflächen wie „Zurück” angezeigt oder ausgeblendet wird.</span><span class="sxs-lookup"><span data-stu-id="02c06-178">This example shows how to adjust the layout of your title bar to account for changes like the system back button being shown or hidden.</span></span> `AppTitleBar`<span data-ttu-id="02c06-179">, `LeftPaddingColumn`, und `RightPaddingColumn` werden im zuvor gezeigten XAML-Code deklariert.</span><span class="sxs-lookup"><span data-stu-id="02c06-179">, `LeftPaddingColumn`, and `RightPaddingColumn` are declared in the XAML shown previously.</span></span>

```csharp
private void CoreTitleBar_LayoutMetricsChanged(CoreApplicationViewTitleBar sender, object args)
{
    UpdateTitleBarLayout(sender);
}

private void UpdateTitleBarLayout(CoreApplicationViewTitleBar coreTitleBar)
{
    // Get the size of the caption controls area and back button 
    // (returned in logical pixels), and move your content around as necessary.
    LeftPaddingColumn.Width = new GridLength(coreTitleBar.SystemOverlayLeftInset);
    RightPaddingColumn.Width = new GridLength(coreTitleBar.SystemOverlayRightInset);
    TitleBarButton.Margin = new Thickness(0,0,coreTitleBar.SystemOverlayRightInset,0);

    // Update title bar control size as needed to account for system size changes.
    AppTitleBar.Height = coreTitleBar.Height;
}
```

### <a name="interactive-content"></a><span data-ttu-id="02c06-180">interaktiver Inhalt</span><span class="sxs-lookup"><span data-stu-id="02c06-180">Interactive content</span></span>

<span data-ttu-id="02c06-181">Sie können interaktive Steuerelemente, z.B. Schaltflächen, Menüs oder ein Suchfeld im oberen Teil der App festlegen, sodass sie in der Titelleiste angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="02c06-181">You can place interactive controls, like buttons, menus, or a search box, in the top part of the app so they appear to be in the title bar.</span></span> <span data-ttu-id="02c06-182">Es gibt jedoch einige Regeln, damit Ihre interaktiven Elemente die Benutzereingaben erhalten.</span><span class="sxs-lookup"><span data-stu-id="02c06-182">However, there are a few rules you must follow to unsure that your interactive elements receive user input.</span></span>
- <span data-ttu-id="02c06-183">Rufen Sie SetTitleBar auf, um einen Bereich als ziehbare Region der Titelleiste zu definieren.</span><span class="sxs-lookup"><span data-stu-id="02c06-183">You must call SetTitleBar to define an area as the draggable title bar region.</span></span> <span data-ttu-id="02c06-184">Falls nicht, setzt das System die ziehbare Standardregion am oberen Rand der Seite fest.</span><span class="sxs-lookup"><span data-stu-id="02c06-184">If you don’t, the system sets the default draggable region at the top of the page.</span></span> <span data-ttu-id="02c06-185">Das System wird dann alle Benutzereingaben in diesem Bereich behandeln und verhindern, dass Eingaben ihre Steuerelemente erreichen.</span><span class="sxs-lookup"><span data-stu-id="02c06-185">The system will then handle all user input to this area, and prevent input from reaching your controls.</span></span>
- <span data-ttu-id="02c06-186">Legen Sie die interaktiven Steuerelemente am oberen Rand des ziehbaren Bereichs fest, der durch den Aufruf von SetTitleBar (mit einer höheren Z-Reihenfolge) definiert ist.</span><span class="sxs-lookup"><span data-stu-id="02c06-186">Place your interactive controls over the top of the draggable region defined by the call to SetTitleBar (with a higher z-order).</span></span> <span data-ttu-id="02c06-187">Legen Sie die interaktiven Steuerelemente des UIElements, die als SetTitleBar übergeben wurden, nicht als untergeordnete Elemente fest.</span><span class="sxs-lookup"><span data-stu-id="02c06-187">Don’t make your interactive controls children of the UIElement passed to SetTitleBar.</span></span> <span data-ttu-id="02c06-188">Nachdem Sie ein Element an SetTitleBar übergeben haben, behandelt das System es wie die System-Titelleiste und behandelt alle Zeigereingaben auf das Element.</span><span class="sxs-lookup"><span data-stu-id="02c06-188">After you pass an element to SetTitleBar, the system treats it like the system title bar and handles all pointer input to that element.</span></span>

<span data-ttu-id="02c06-189">Hier verfügt das `TitleBarButton`-Element über eine höhere Z-Reihenfolge als `AppTitleBar`, damit es Benutzereingaben empfängt.</span><span class="sxs-lookup"><span data-stu-id="02c06-189">Here, the `TitleBarButton` element has a higher z-order than `AppTitleBar`, so it receives user input.</span></span>

```xaml
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition />
    </Grid.RowDefinitions>

    <Grid x:Name="AppTitleBar" Background="Transparent">
        <!-- Width of the padding columns is set in LayoutMetricsChanged handler. -->
        <!-- Using padding columns instead of Margin ensures that the background
             paints the area under the caption control buttons (for transparent buttons). -->
        <Grid.ColumnDefinitions>
            <ColumnDefinition x:Name="LeftPaddingColumn" Width="0"/>
            <ColumnDefinition/>
            <ColumnDefinition x:Name="RightPaddingColumn" Width="0"/>
        </Grid.ColumnDefinitions>
        <Image Source="Assets/Square44x44Logo.png"
               Grid.Column="1" HorizontalAlignment="Left"
               Width="20" Height="20" Margin="12,0"/>
        <TextBlock Text="Custom Title Bar"
                   Grid.Column="1"
                   Style="{StaticResource CaptionTextBlockStyle}"
                   Margin="44,8,0,0"/>
    </Grid>

    <!-- This Button has a higher z-order than AppTitleBar, 
         so it receives user input. -->
    <Button x:Name="TitleBarButton" Content="Button in the title bar"
        HorizontalAlignment="Right"/>
</Grid>
```

### <a name="transparency-in-caption-buttons"></a><span data-ttu-id="02c06-190">Transparenz in Titelleistenschaltflächen</span><span class="sxs-lookup"><span data-stu-id="02c06-190">Transparency in caption buttons</span></span>

<span data-ttu-id="02c06-191">Wenn Sie ExtendViewIntoTitleBar auf **true** festlegen, können Sie den Hintergrund der Titelleistenschaltflächen transparent machen, damit der App-Hintergrund durchscheint.</span><span class="sxs-lookup"><span data-stu-id="02c06-191">When you set ExtendViewIntoTitleBar to **true**, you can make the background of the caption buttons transparent to let your app background show through.</span></span> <span data-ttu-id="02c06-192">Generell wird der Hintergrund auf [Colors.Transparent](https://docs.microsoft.com/uwp/api/windows.ui.colors.Transparent) für vollständigen Transparenz festgelegt.</span><span class="sxs-lookup"><span data-stu-id="02c06-192">You typically set the background to [Colors.Transparent](https://docs.microsoft.com/uwp/api/windows.ui.colors.Transparent) for full transparency.</span></span> <span data-ttu-id="02c06-193">Legen Sie für eine partielle Transparenz den Alpha-Kanal für die [Farbe](https://docs.microsoft.com/uwp/api/windows.ui.color) auf die Eigenschaft fest.</span><span class="sxs-lookup"><span data-stu-id="02c06-193">For partial transparency, set the alpha channel for the [Color](https://docs.microsoft.com/uwp/api/windows.ui.color) you set the property to.</span></span>

<span data-ttu-id="02c06-194">Diese ApplicationViewTitleBar-Eigenschaften können transparent sein:</span><span class="sxs-lookup"><span data-stu-id="02c06-194">These ApplicationViewTitleBar properties can be transparent:</span></span>

- <span data-ttu-id="02c06-195">ButtonBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="02c06-195">ButtonBackgroundColor</span></span>
- <span data-ttu-id="02c06-196">ButtonHoverBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="02c06-196">ButtonHoverBackgroundColor</span></span>
- <span data-ttu-id="02c06-197">ButtonPressedBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="02c06-197">ButtonPressedBackgroundColor</span></span>
- <span data-ttu-id="02c06-198">ButtonInactiveBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="02c06-198">ButtonInactiveBackgroundColor</span></span>

<span data-ttu-id="02c06-199">Die Hintergrundfarbe der Schaltfläche wird nicht auf den Zeigeeffekt und das Gedrückthalten der Schaltfläche "Schließen" angewendet.</span><span class="sxs-lookup"><span data-stu-id="02c06-199">The button background color is not applied to the close button hover and pressed states.</span></span> <span data-ttu-id="02c06-200">Die Schaltfläche "Schließen" verwendet immer die systemdefinierte Farbe für diese Zustände.</span><span class="sxs-lookup"><span data-stu-id="02c06-200">The close button always uses the system-defined color for those states.</span></span>

<span data-ttu-id="02c06-201">Alle anderen Farbeigenschaften werden auch weiterhin den Alphakanal ignorieren.</span><span class="sxs-lookup"><span data-stu-id="02c06-201">All other color properties will continue to ignore the alpha channel.</span></span> <span data-ttu-id="02c06-202">Wenn ExtendViewIntoTitleBar auf **false** festgelegt wird, wird der Alpha-Kanal immer für alle ApplicationViewTitleBar-Farbeigenschaften ignoriert.</span><span class="sxs-lookup"><span data-stu-id="02c06-202">If ExtendViewIntoTitleBar is set to **false**, the alpha channel is always ignored for all ApplicationViewTitleBar color properties.</span></span>

### <a name="full-screen-and-tablet-mode"></a><span data-ttu-id="02c06-203">Vollbildschirm- und Tablet-Modus</span><span class="sxs-lookup"><span data-stu-id="02c06-203">Full screen and tablet mode</span></span>

<span data-ttu-id="02c06-204">Wenn Ihre App im _Vollbildmodus_ oder _Tablet-Modus_ ausgeführt wird, blendet das System die Titelleisten- und Untertitel-Steuerungschaltflächen aus.</span><span class="sxs-lookup"><span data-stu-id="02c06-204">When your app runs in _full screen_ or _tablet mode_, the system hides the title bar and caption control buttons.</span></span> <span data-ttu-id="02c06-205">Der Benutzer kann allerdings die Titelleiste aufrufen, um sie als Overlay über der Benutzeroberfläche anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="02c06-205">However, the user can invoke the title bar to have it shown as an overlay on top of the app’s UI.</span></span>
<span data-ttu-id="02c06-206">Sie können das [CoreApplicationViewTitleBar.IsVisibleChanged](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplicationviewtitlebar.IsVisibleChanged)-Ereignis so festlegen, dass Sie benachrichtigt werden, wenn die Titelleiste aufgerufen oder ausgeblendet wird und den benutzerdefinierten Inhalt Ihrer Titelleiste nach Wunsch anzuzeigen oder auszublenden.</span><span class="sxs-lookup"><span data-stu-id="02c06-206">You can handle the [CoreApplicationViewTitleBar.IsVisibleChanged](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplicationviewtitlebar.IsVisibleChanged) event to be notified when the title bar is hidden or invoked, and show or hide your custom title bar content as needed.</span></span>

<span data-ttu-id="02c06-207">In diesem Beispiel wird veranschaulicht, wie IsVisibleChanged zum Einblenden und Ausblenden des oben dargestellten `AppTitleBar`- Elements behandelt wird.</span><span class="sxs-lookup"><span data-stu-id="02c06-207">This example shows how to handle IsVisibleChanged to show and hide the `AppTitleBar` element shown previously.</span></span>

```csharp
public MainPage()
{
    this.InitializeComponent();

    var coreTitleBar = CoreApplication.GetCurrentView().TitleBar;

    // Register a handler for when the title bar visibility changes.
    // For example, when the title bar is invoked in full screen mode.
    coreTitleBar.IsVisibleChanged += CoreTitleBar_IsVisibleChanged;
}

private void CoreTitleBar_IsVisibleChanged(CoreApplicationViewTitleBar sender, object args)
{
    if (sender.IsVisible)
    {
        AppTitleBar.Visibility = Visibility.Visible;
    }
    else
    {
        AppTitleBar.Visibility = Visibility.Collapsed;
    }
}
```

>[!NOTE]
><span data-ttu-id="02c06-208">Der _Vollbild_ Modus kann nur angezeigt werden, wenn er von Ihrer App unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="02c06-208">_Full screen_ mode can be entered only if supported by your app.</span></span> <span data-ttu-id="02c06-209">Weitere Informationen finden Sie unter [ApplicationView.IsFullScreenMode](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.IsFullScreenMode).</span><span class="sxs-lookup"><span data-stu-id="02c06-209">See [ApplicationView.IsFullScreenMode](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.IsFullScreenMode) for more info.</span></span> <span data-ttu-id="02c06-210">[_Tablet-Modus_](https://support.microsoft.com/help/17210/windows-10-use-your-pc-like-a-tablet) ist eine Option auf unterstützter Hardware, damit ein Benutzer auswählen kann, ob eine App im Tablet-Modus ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="02c06-210">[_Tablet mode_](https://support.microsoft.com/help/17210/windows-10-use-your-pc-like-a-tablet) is a user option on supported hardware, so a user can choose to run any app in tablet mode.</span></span>

## <a name="full-customization-example"></a><span data-ttu-id="02c06-211">Umfassendes Anpassungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="02c06-211">Full customization example</span></span>

```xaml
<Page
    x:Class="CustomTitleBar.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:CustomTitleBar"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d">

    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto"/>
            <RowDefinition />
        </Grid.RowDefinitions>

        <Grid x:Name="AppTitleBar" Background="Transparent">
            <!-- Width of the padding columns is set in LayoutMetricsChanged handler. -->
            <!-- Using padding columns instead of Margin ensures that the background
                 paints the area under the caption control buttons (for transparent buttons). -->
            <Grid.ColumnDefinitions>
                <ColumnDefinition x:Name="LeftPaddingColumn" Width="0"/>
                <ColumnDefinition/>
                <ColumnDefinition x:Name="RightPaddingColumn" Width="0"/>
            </Grid.ColumnDefinitions>
            <Image Source="Assets/Square44x44Logo.png" 
                   Grid.Column="1" HorizontalAlignment="Left" 
                   Width="20" Height="20" Margin="12,0"/>
            <TextBlock Text="Custom Title Bar" 
                       Grid.Column="1" 
                       Style="{StaticResource CaptionTextBlockStyle}" 
                       Margin="44,8,0,0"/>
        </Grid>

        <!-- This Button has a higher z-order than MyTitleBar, 
             so it receives user input. -->
        <Button x:Name="TitleBarButton" Content="Button in the title bar"
                HorizontalAlignment="Right"/>
    </Grid>
</Page>
```

```csharp
public MainPage()
{
    this.InitializeComponent();

    // Hide default title bar.
    var coreTitleBar = CoreApplication.GetCurrentView().TitleBar;
    coreTitleBar.ExtendViewIntoTitleBar = true;
    UpdateTitleBarLayout(coreTitleBar);

    // Set XAML element as a draggable region.
    Window.Current.SetTitleBar(AppTitleBar);

    // Register a handler for when the size of the overlaid caption control changes.
    // For example, when the app moves to a screen with a different DPI.
    coreTitleBar.LayoutMetricsChanged += CoreTitleBar_LayoutMetricsChanged;

    // Register a handler for when the title bar visibility changes.
    // For example, when the title bar is invoked in full screen mode.
    coreTitleBar.IsVisibleChanged += CoreTitleBar_IsVisibleChanged;
}

private void CoreTitleBar_LayoutMetricsChanged(CoreApplicationViewTitleBar sender, object args)
{
    UpdateTitleBarLayout(sender);
}

private void UpdateTitleBarLayout(CoreApplicationViewTitleBar coreTitleBar)
{
    // Get the size of the caption controls area and back button 
    // (returned in logical pixels), and move your content around as necessary.
    LeftPaddingColumn.Width = new GridLength(coreTitleBar.SystemOverlayLeftInset);
    RightPaddingColumn.Width = new GridLength(coreTitleBar.SystemOverlayRightInset);
    TitleBarButton.Margin = new Thickness(0,0,coreTitleBar.SystemOverlayRightInset,0);

    // Update title bar control size as needed to account for system size changes.
    AppTitleBar.Height = coreTitleBar.Height;
}

private void CoreTitleBar_IsVisibleChanged(CoreApplicationViewTitleBar sender, object args)
{
    if (sender.IsVisible)
    {
        AppTitleBar.Visibility = Visibility.Visible;
    }
    else
    {
        AppTitleBar.Visibility = Visibility.Collapsed;
    }
}
```

## <a name="dos-and-donts"></a><span data-ttu-id="02c06-212">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="02c06-212">Do's and don'ts</span></span>

- <span data-ttu-id="02c06-213">Stellen Sie offensichtlich dar, ob das Fenster aktiv oder inaktiv ist.</span><span class="sxs-lookup"><span data-stu-id="02c06-213">Do make is obvious when your window is active or inactive.</span></span> <span data-ttu-id="02c06-214">Ändern Sie mindestens die Farbe von Text, Symbolen und Schaltflächen in der Titelleiste.</span><span class="sxs-lookup"><span data-stu-id="02c06-214">At a minimum, change the color of the text, icons, and buttons in your title bar.</span></span>
- <span data-ttu-id="02c06-215">Definieren Sie einen ziehbaren Bereich am oberen Rand des App-Canvas.</span><span class="sxs-lookup"><span data-stu-id="02c06-215">Do define a draggable region along the top edge of the app canvas.</span></span> <span data-ttu-id="02c06-216">Durch das Abstimmen der Platzierung der System-Titelleisten sind diese einfacher zu finden.</span><span class="sxs-lookup"><span data-stu-id="02c06-216">Matching the placement of system title bars makes it easier for users to find.</span></span>
- <span data-ttu-id="02c06-217">Definieren Sie einen ziehbaren Bereich, der mit der visuellen Titelleiste (sofern vorhanden) in der App Canvas übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="02c06-217">Do define a draggable region that matches the visual title bar (if any) on the app’s canvas.</span></span>

## <a name="related-articles"></a><span data-ttu-id="02c06-218">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="02c06-218">Related articles</span></span>

- [<span data-ttu-id="02c06-219">Acryl</span><span class="sxs-lookup"><span data-stu-id="02c06-219">Acrylic</span></span>](../style/acrylic.md)
- [<span data-ttu-id="02c06-220">Farbe</span><span class="sxs-lookup"><span data-stu-id="02c06-220">Color</span></span>](../style/color.md)
