---
author: serenaz
Description: The Universal Windows Platform (UWP) provides a consistent back navigation system for traversing the user's navigation history within an app and, depending on the device, from app to app.
title: Navigationsverlauf und Rückwärtsnavigation (Windows-Apps)
ms.assetid: e9876b4c-242d-402d-a8ef-3487398ed9b3
isNew: true
label: History and backwards navigation
template: detail.hbs
op-migration-status: ready
ms.author: sezhen
ms.date: 11/22/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 824f0e83408893bf95d856067282b1fea1313876
ms.sourcegitcommit: 588171ea8cb629d2dd6aa2080e742dc8ce8584e5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "1895407"
---
#  <a name="navigation-history-and-backwards-navigation-for-uwp-apps"></a><span data-ttu-id="87e64-103">Navigationsverlauf und Rückwärtsnavigation für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="87e64-103">Navigation history and backwards navigation for UWP apps</span></span>

> <span data-ttu-id="87e64-104">**Wichtige APIs**: [BackRequested event](https://docs.microsoft.com/uwp/api/Windows.UI.Core.SystemNavigationManager.BackRequested), [SystemNavigationManager class](https://docs.microsoft.com/uwp/api/Windows.UI.Core.SystemNavigationManager), [OnNavigatedTo](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.page.onnavigatedto#Windows_UI_Xaml_Controls_Page_OnNavigatedTo_Windows_UI_Xaml_Navigation_NavigationEventArgs_)</span><span class="sxs-lookup"><span data-stu-id="87e64-104">**Important APIs**: [BackRequested event](https://docs.microsoft.com/uwp/api/Windows.UI.Core.SystemNavigationManager.BackRequested), [SystemNavigationManager class](https://docs.microsoft.com/uwp/api/Windows.UI.Core.SystemNavigationManager), [OnNavigatedTo](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.page.onnavigatedto#Windows_UI_Xaml_Controls_Page_OnNavigatedTo_Windows_UI_Xaml_Navigation_NavigationEventArgs_)</span></span>

<span data-ttu-id="87e64-105">Die universelle Windows-Plattform (UWP) enthält ein einheitliches System zur Rückwärtsnavigation, mit dem der Navigationsverlauf des Benutzers innerhalb einer App und je nach Gerät von App zu App durchlaufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="87e64-105">The Universal Windows Platform (UWP) provides a consistent back navigation system for traversing the user's navigation history within an app and, depending on the device, from app to app.</span></span>

<span data-ttu-id="87e64-106">Um die Rückwärtsnavigation in Ihrer App zu implementieren, platzieren Sie einen [Zurück](#Back-button)-Button in der oberen linken Ecke der Benutzeroberfläche Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="87e64-106">To implement backwards navigation in your app, place a [back button](#Back-button) at the top left corner of your app's UI.</span></span> <span data-ttu-id="87e64-107">Wenn Ihre App das [NavigationView](../controls-and-patterns/navigationview.md)-Steuerelement verwendet, können Sie die integrierte [Zurück-Schaltfläche von NavigationView](../controls-and-patterns/navigationview.md#backwards-navigation) verwenden.</span><span class="sxs-lookup"><span data-stu-id="87e64-107">If your app uses the [NavigationView](../controls-and-patterns/navigationview.md) control, then you can use [NavigationView's built-in back button](../controls-and-patterns/navigationview.md#backwards-navigation).</span></span> 

<span data-ttu-id="87e64-108">Der Benutzer erwartet, dass durch Drücken der Zurück-Schaltfläche die vorherige Seite im Navigationsverlauf der App aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="87e64-108">The user expects the back button to navigate to the previous location in the app's navigation history.</span></span> <span data-ttu-id="87e64-109">Sie können entscheiden, welche Navigationsaktionen dem Navigationsverlauf hinzugefügt werden sollen und wie auf das Drücken der Zurück-Schaltfläche reagiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="87e64-109">Note that it's up to you to decide which navigation actions to add to the navigation history and how to respond to the back button press.</span></span>

## <a name="back-button"></a><span data-ttu-id="87e64-110">Zurück-Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="87e64-110">Back button</span></span>

<span data-ttu-id="87e64-111">Um einen Zurück-Schaltfläche zu erstellen, verwenden Sie das [Button](../controls-and-patterns/buttons.md)-Steuerelement mit dem `NavigationBackButtonNormalStyle`-Stil, und platzieren Sie die Schaltfläche in der oberen linken Ecke der Benutzeroberfläche Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="87e64-111">To create a back button, use the [Button](../controls-and-patterns/buttons.md) control with the `NavigationBackButtonNormalStyle` style, and place the button at the top left hand corner of your app's UI.</span></span>

![Zurück-Schaltfläche oben links in der App-Oberfläche](images/back-nav/BackEnabled.png)

```xaml
<Button Style="{StaticResource NavigationBackButtonNormalStyle}"/>
```

<span data-ttu-id="87e64-113">Wenn Ihre App eine obere [CommandBar](../controls-and-patterns/app-bars.md) hat, wird das 44 Pixel hohe Button-Steuerelement nicht sehr gut neben 48 Pixel hohe AppBarButtons passen.</span><span class="sxs-lookup"><span data-stu-id="87e64-113">If your app has a top [CommandBar](../controls-and-patterns/app-bars.md), the Button control that is 44px in height will not align with 48px AppBarButtons very nicely.</span></span> <span data-ttu-id="87e64-114">Um jedoch Inkonsistenzen zu vermeiden, richten Sie den oberen Teil der Schaltfläche innerhalb der 48 Pixel-Grenzen aus.</span><span class="sxs-lookup"><span data-stu-id="87e64-114">However, to avoid inconsistency, align the top of the Button control inside the 48px bounds.</span></span>

![Zurück-Schaltfläche in der oberen Befehlsleiste](images/back-nav/CommandBar.png)

```xaml
<Button VerticalAlignment="Top" HorizontalAlignment="Left" 
Style="{StaticResource NavigationBackButtonNormalStyle}"/>
```

<span data-ttu-id="87e64-116">Um UI-Elemente zu minimieren, die sich in Ihrer App bewegen, zeigen Sie eine deaktivierte Zurück-Schaltfläche an, wenn sich nichts im Backstack befindet (siehe Codebeispiel unten).</span><span class="sxs-lookup"><span data-stu-id="87e64-116">In order to minimize UI elements moving around in your app, show a disabled back button when there is nothing in the backstack (see code example below).</span></span>

![Zustände der Zurück-Schaltfläche](images/back-nav/BackDisabled.png)

## <a name="code-example"></a><span data-ttu-id="87e64-118">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="87e64-118">Code example</span></span>

<span data-ttu-id="87e64-119">Das folgende Codebeispiel demonstriert, wie man das Rückwärtsnavigationsverhalten mit einer Zurück-Schaltfläche implementiert.</span><span class="sxs-lookup"><span data-stu-id="87e64-119">The following code example demonstrates how to implement backwards navigation behavior with a back button.</span></span> <span data-ttu-id="87e64-120">Der Code reagiert auf das Button-Ereignis [**Click**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.Click) und deaktiviert/aktiviert die Sichtbarkeit der Schaltfläche in [**OnNavigatedTo**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.page.onnavigatedto#Windows_UI_Xaml_Controls_Page_OnNavigatedTo_Windows_UI_Xaml_Navigation_NavigationEventArgs_), das beim Navigieren zu einer neuen Seite aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="87e64-120">The code responds to the Button [**Click**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.Click) event and disables/enables the button visibility in [**OnNavigatedTo**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.page.onnavigatedto#Windows_UI_Xaml_Controls_Page_OnNavigatedTo_Windows_UI_Xaml_Navigation_NavigationEventArgs_), which is called when navigating to a new page.</span></span> <span data-ttu-id="87e64-121">Das Codebeispiel behandelt auch Eingaben von Hardware- und Softwaresystem-Zurück-Schaltflächen, indem es einen Listener für das [**BackRequested**](https://docs.microsoft.com/uwp/api/windows.ui.core.systemnavigationmanager.BackRequested)-Ereignis registriert.</span><span class="sxs-lookup"><span data-stu-id="87e64-121">The code example also handles inputs from hardware and software system back keys by registering a listener for the [**BackRequested**](https://docs.microsoft.com/uwp/api/windows.ui.core.systemnavigationmanager.BackRequested) event.</span></span>

```xaml
<Page x:Class="AppName.MainPage">
...
<Button x:Name="BackButton" Click="Back_Click" Style="{StaticResource NavigationBackButtonNormalStyle}"/>
...
<Page/>
```

<span data-ttu-id="87e64-122">Code-Behind:</span><span class="sxs-lookup"><span data-stu-id="87e64-122">Code-behind:</span></span>

```csharp
public MainPage()
{
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

protected override void OnNavigatedTo(NavigationEventArgs e)
{
    BackButton.IsEnabled = this.Frame.CanGoBack;
}

private void Back_Click(object sender, RoutedEventArgs e)
{
    On_BackRequested();
}

// Handles system-level BackRequested events and page-level back button Click events
private bool On_BackRequested()
{
    if (this.Frame.CanGoBack)
    {
        this.Frame.GoBack();
        return true;
    }
    return false;
}

private void BackInvoked (KeyboardAccelerator sender, KeyboardAcceleratorInvokedEventArgs args)
{
    On_BackRequested();
    args.Handled = true;
}
```

<span data-ttu-id="87e64-123">Hier registrieren wir einen globalen Listener für das [**BackRequested**](https://docs.microsoft.com/uwp/api/windows.ui.core.systemnavigationmanager.BackRequested)-Ereignis in der Code-Behind-Datei für `App.xaml`.</span><span class="sxs-lookup"><span data-stu-id="87e64-123">Here, we register a global listener for the [**BackRequested**](https://docs.microsoft.com/uwp/api/windows.ui.core.systemnavigationmanager.BackRequested) event in the `App.xaml` code-behind file.</span></span> <span data-ttu-id="87e64-124">Sie können sich für dieses Ereignis auf jeder Seite registrieren, wenn Sie bestimmte Seiten aus der Rückwärtsnavigation ausschließen oder vor dem Anzeigen der Seite Seitenebenencode ausführen möchten.</span><span class="sxs-lookup"><span data-stu-id="87e64-124">You can register for this event in each page if you want to exclude specific pages from back navigation, or you want to execute page-level code before displaying the page.</span></span>

<span data-ttu-id="87e64-125">App.xaml Code-Behind:</span><span class="sxs-lookup"><span data-stu-id="87e64-125">App.xaml code-behind:</span></span>

```csharp
Windows.UI.Core.SystemNavigationManager.GetForCurrentView().BackRequested += App_BackRequested;
Frame rootFrame = Window.Current.Content;
rootFrame.PointerPressed += On_PointerPressed;

private void App_BackRequested(object sender, Windows.UI.Core.BackRequestedEventArgs e)
{
    e.Handled = On_BackRequested();
}

private void On_PointerPressed(object sender, PointerRoutedEventArgs e)
{
    bool isXButton1Pressed = e.GetCurrentPoint(sender as UIElement).Properties.PointerUpdateKind == PointerUpdateKind.XButton1Pressed;

    if (isXButton1Pressed)
    {
        e.Handled = On_BackRequested();
    }
}
```

## <a name="optimizing-for-different-device-and-form-factors"></a><span data-ttu-id="87e64-126">Optimierung für unterschiedliche Geräte- und Formfaktoren</span><span class="sxs-lookup"><span data-stu-id="87e64-126">Optimizing for different device and form factors</span></span>

<span data-ttu-id="87e64-127">Diese Anleitung für das Rückwärtsnavigationsdesign gilt für alle Geräte. Verschiedene Geräte und Formfaktoren können jedoch von der Optimierung profitieren.</span><span class="sxs-lookup"><span data-stu-id="87e64-127">This backwards navigation design guidance is applicable to all devices, but different device and form factors may benefit from optimization.</span></span> <span data-ttu-id="87e64-128">Dies hängt auch von der Hardware-Zurück-Taste ab, der von verschiedenen Shells unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="87e64-128">This also depends on the hardware back button supported by different shells.</span></span>

- <span data-ttu-id="87e64-129">**Smartphone/Tablet**: Ein Hardware- oder Software-Zurück-Schaltfläche ist auf jedem Smartphone und Tablet vorhanden, aber wir empfehlen, einen In-App-Zurück-Schaltfläche zu verwenden, um die Übersichtlichkeit zu erhöhen.</span><span class="sxs-lookup"><span data-stu-id="87e64-129">**Phone/Tablet**: A hardware or software back button is always present on mobile and tablet, but we recommend drawing an in-app back button for clarity.</span></span>
- <span data-ttu-id="87e64-130">**Desktop/Hub**: Stellen Sie den In-App-Button in der linken oberen Ecke der Benutzeroberfläche Ihrer App dar.</span><span class="sxs-lookup"><span data-stu-id="87e64-130">**Desktop/Hub**: Draw the in-app back button on the top left corner of your app's UI.</span></span>
- <span data-ttu-id="87e64-131">**Xbox/TV**: Nutzen Sie keinen Zurück-Schaltfläche. Er macht das UI unnötigerweise unübersichtlich.</span><span class="sxs-lookup"><span data-stu-id="87e64-131">**Xbox/TV**: Do not draw a back button, for it will add unnecessary UI clutter.</span></span> <span data-ttu-id="87e64-132">Verlassen Sie sich stattdessen auf die Gamepad-Taste B, um rückwärts zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="87e64-132">Instead, rely on the Gamepad B button to navigate backwards.</span></span>

<span data-ttu-id="87e64-133">Wenn Ihre App auf mehreren Geräten läuft, [erstellen Sie einen benutzerdefinierten visuellen Trigger für die Xbox](../devices/designing-for-tv.md#custom-visual-state-trigger-for-xbox), um die Sichtbarkeit der Schaltfläche umzuschalten.</span><span class="sxs-lookup"><span data-stu-id="87e64-133">If your app will run on multiple devices, [create a custom visual trigger for Xbox](../devices/designing-for-tv.md#custom-visual-state-trigger-for-xbox) to toggle the visibility of button.</span></span> <span data-ttu-id="87e64-134">Das NavigationView-Steuerelement schaltet automatisch die Sichtbarkeit der Schaltfläche „Zurück” um, wenn Ihre App auf der Xbox läuft.</span><span class="sxs-lookup"><span data-stu-id="87e64-134">The NavigationView control will automatically toggle the back button's visibility if your app is running on Xbox.</span></span> 

<span data-ttu-id="87e64-135">Wir empfehlen, die folgenden Eingaben für die Rückwärtsnavigation zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="87e64-135">We recommend supporting the following inputs for back navigation.</span></span> <span data-ttu-id="87e64-136">(Beachten Sie, dass einige dieser Eingaben vom System-BackRequested nicht unterstützt werden und durch separate Ereignisse behandelt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="87e64-136">(Note that some of these inputs are not supported by the system BackRequested and must be handled by separate events.)</span></span>

| <span data-ttu-id="87e64-137">Eingabe</span><span class="sxs-lookup"><span data-stu-id="87e64-137">Input</span></span> | <span data-ttu-id="87e64-138">Ereignis</span><span class="sxs-lookup"><span data-stu-id="87e64-138">Event</span></span> |
| --- | --- |
| <span data-ttu-id="87e64-139">Windows-Rücktaste</span><span class="sxs-lookup"><span data-stu-id="87e64-139">Windows-Backspace key</span></span> | <span data-ttu-id="87e64-140">BackRequested</span><span class="sxs-lookup"><span data-stu-id="87e64-140">BackRequested</span></span> |
| <span data-ttu-id="87e64-141">Hardware-Zurück-Taste</span><span class="sxs-lookup"><span data-stu-id="87e64-141">Hardware back button</span></span> | <span data-ttu-id="87e64-142">BackRequested</span><span class="sxs-lookup"><span data-stu-id="87e64-142">BackRequested</span></span> |
| <span data-ttu-id="87e64-143">Shell-Tablet-Modus Zurück-Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="87e64-143">Shell tablet mode back button</span></span> | <span data-ttu-id="87e64-144">BackRequested</span><span class="sxs-lookup"><span data-stu-id="87e64-144">BackRequested</span></span> |
| <span data-ttu-id="87e64-145">VirtualKey.XButton1</span><span class="sxs-lookup"><span data-stu-id="87e64-145">VirtualKey.XButton1</span></span> | <span data-ttu-id="87e64-146">PointerPressed</span><span class="sxs-lookup"><span data-stu-id="87e64-146">PointerPressed</span></span> |
| <span data-ttu-id="87e64-147">VirtualKey.GoBack</span><span class="sxs-lookup"><span data-stu-id="87e64-147">VirtualKey.GoBack</span></span> | <span data-ttu-id="87e64-148">KeyboardAccelerator.BackInvoked</span><span class="sxs-lookup"><span data-stu-id="87e64-148">KeyboardAccelerator.BackInvoked</span></span> |
| <span data-ttu-id="87e64-149">ALT + NACH-LINKS</span><span class="sxs-lookup"><span data-stu-id="87e64-149">Alt+LeftArrow key</span></span> | <span data-ttu-id="87e64-150">KeyboardAccelerator.BackInvoked</span><span class="sxs-lookup"><span data-stu-id="87e64-150">KeyboardAccelerator.BackInvoked</span></span> |

<span data-ttu-id="87e64-151">Die oben aufgeführten Codebeispiele zeigen, wie man mit diesen Eingaben umgeht.</span><span class="sxs-lookup"><span data-stu-id="87e64-151">The code examples provided above demonstrate how to handle all of these inputs.</span></span>

## <a name="system-back-behavior-for-backward-compatibilities"></a><span data-ttu-id="87e64-152">System-Rückwärtsverhalten für Rückwärtskompatibilitäten</span><span class="sxs-lookup"><span data-stu-id="87e64-152">System back behavior for backward compatibilities</span></span>

<span data-ttu-id="87e64-153">Bisher nutzten UWP-Apps [AppViewBackButtonVisibility](https://docs.microsoft.com/uwp/api/windows.ui.core.appviewbackbuttonvisibility) für die Rückwärtsnavigation.</span><span class="sxs-lookup"><span data-stu-id="87e64-153">Previously, UWP apps used [AppViewBackButtonVisibility](https://docs.microsoft.com/uwp/api/windows.ui.core.appviewbackbuttonvisibility) for backwards navigation.</span></span> <span data-ttu-id="87e64-154">Die API wird aus Gründen der Abwärtskompatibilität weiterhin unterstützt, aber wir empfehlen nicht mehr, sich auf die Schaltfläche „Zurück” in der Titelleiste zu verlassen.</span><span class="sxs-lookup"><span data-stu-id="87e64-154">The API will continue to be supported for backward compatibility, but we no longer recommend relying on the title bar back button.</span></span> <span data-ttu-id="87e64-155">Stattdessen sollte Ihre App eine eigene Zurück-Schaltfläche in der App darstellen.</span><span class="sxs-lookup"><span data-stu-id="87e64-155">Instead, your app should draw its own in-app back button.</span></span>

<span data-ttu-id="87e64-156">Wenn Ihre App weiterhin [AppViewBackButtonVisibility](https://docs.microsoft.com/uwp/api/windows.ui.core.appviewbackbuttonvisibility) verwendet, wird die Zurück-Schaltfläche wie gewohnt in der Titelleiste angezeigt.</span><span class="sxs-lookup"><span data-stu-id="87e64-156">If your app continues to use [AppViewBackButtonVisibility](https://docs.microsoft.com/uwp/api/windows.ui.core.appviewbackbuttonvisibility), then the back button will be rendered inside the title bar as usual.</span></span>

![Zurück-Schaltfläche in der Titelleiste](images/nav-back-pc.png)

## <a name="guidelines-for-custom-back-navigation-behavior"></a><span data-ttu-id="87e64-158">Richtlinien für das benutzerdefinierte Verhalten der Rückwärtsnavigation</span><span class="sxs-lookup"><span data-stu-id="87e64-158">Guidelines for custom back navigation behavior</span></span>

<span data-ttu-id="87e64-159">Wenn Sie Ihre eigene Zurück-Stapelnavigation bereitstellen möchten, sollte die Benutzeroberfläche mit anderen Apps konsistent sein.</span><span class="sxs-lookup"><span data-stu-id="87e64-159">If you choose to provide your own back stack navigation, the experience should be consistent with other apps.</span></span> <span data-ttu-id="87e64-160">Wir empfehlen, die folgenden Muster für Navigationsaktionen zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="87e64-160">We recommend that you follow the following patterns for navigation actions:</span></span>

<div class="mx-responsive-img">
<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="87e64-161">Navigationsaktion</span><span class="sxs-lookup"><span data-stu-id="87e64-161">Navigation action</span></span></th>
<th align="left"><span data-ttu-id="87e64-162">Zum Navigationsverlauf hinzufügen?</span><span class="sxs-lookup"><span data-stu-id="87e64-162">Add to navigation history?</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top;"><strong><span data-ttu-id="87e64-163">Seite zu Seite, verschiedene Peer-Gruppen</span><span class="sxs-lookup"><span data-stu-id="87e64-163">Page to page, different peer groups</span></span></strong></td>
<td style="vertical-align:top;"><strong><span data-ttu-id="87e64-164">Ja</span><span class="sxs-lookup"><span data-stu-id="87e64-164">Yes</span></span></strong>
<p><span data-ttu-id="87e64-165">In der folgenden Abbildung navigiert der Benutzer von Ebene 1 der App zu Ebene 2. Dabei werden Peer-Gruppen durchlaufen, sodass die Navigation dem Navigationsverlauf hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="87e64-165">In this illustration, the user navigates from level 1 of the app to level 2, crossing peer groups, so the navigation is added to the navigation history.</span></span></p>
<p><img src="images/back-nav/nav-pagetopage-diffpeers-imageonly1.png" alt="Navigation across peer groups" /></p>
<p><span data-ttu-id="87e64-166">In der nächsten Abbildung navigiert der Benutzer zwischen zwei Peer-Gruppen derselben Ebene. Er durchläuft erneut Peer-Gruppen, sodass die Navigation dem Navigationsverlauf hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="87e64-166">In the next illustration, the user navigates between two peer groups at the same level, again crossing peer groups, so the navigation is added to the navigation history.</span></span></p>
<p><img src="images/back-nav/nav-pagetopage-diffpeers-imageonly2.png" alt="Navigation across peer groups" /></p></td>
</tr>
<tr class="even">
<td style="vertical-align:top;"><strong><span data-ttu-id="87e64-167">Seite zu Seite, gleiche Peer-Gruppe, kein Bildschirmnavigationselement</span><span class="sxs-lookup"><span data-stu-id="87e64-167">Page to page, same peer group, no on-screen navigation element</span></span></strong>
<p><span data-ttu-id="87e64-168">Der Benutzer navigiert von einer Seite zu einer anderen mit derselben Peer-Gruppe.</span><span class="sxs-lookup"><span data-stu-id="87e64-168">The user navigates from one page to another with the same peer group.</span></span> <span data-ttu-id="87e64-169">Es gibt kein Navigationselement, das immer vorhanden ist (wie ein oberer Navigationsbereich oder ein angedockter Navigationsbereich) und das eine direkte Navigation zu beiden Seiten ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="87e64-169">There is no navigation element that is always present (such as a top navigation pane or a docked left navigation pane) that provides direct navigation to both pages.</span></span></p></td>
<td style="vertical-align:top;"><strong><span data-ttu-id="87e64-170">Ja</span><span class="sxs-lookup"><span data-stu-id="87e64-170">Yes</span></span></strong>
<p><span data-ttu-id="87e64-171">In der folgenden Abbildung navigiert der Benutzer zwischen zwei Seiten in derselben Peer-Gruppe.</span><span class="sxs-lookup"><span data-stu-id="87e64-171">In the following illustration, the user navigates between two pages in the same peer group.</span></span> <span data-ttu-id="87e64-172">Die Seiten verwenden keinen oberen oder angedockten Navigationsbereich, sodass die Navigation dem Navigationsverlauf hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="87e64-172">The pages don't use a top nav bar or a docked left nav pane, so the navigation is added to the navigation history.</span></span></p>
<p><img src="images/back-nav/nav-pagetopage-samepeer-noosnavelement.png" alt="Navigation within a peer group" /></p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top;"><strong><span data-ttu-id="87e64-173">Seite zu Seite, gleiche Peer-Gruppe, mit einem Bildschirmnavigationselement</span><span class="sxs-lookup"><span data-stu-id="87e64-173">Page to page, same peer group, with an on-screen navigation element</span></span></strong>
<p><span data-ttu-id="87e64-174">Der Benutzer navigiert von einer Seite zu einer anderen in derselben Peer-Gruppe.</span><span class="sxs-lookup"><span data-stu-id="87e64-174">The user navigates from one page to another in the same peer group.</span></span> <span data-ttu-id="87e64-175">Beide Seiten werden im gleichen Navigationselement angezeigt.</span><span class="sxs-lookup"><span data-stu-id="87e64-175">Both pages are shown in the same navigation element.</span></span> <span data-ttu-id="87e64-176">Beide Seiten verwenden beispielsweise das gleiche Element für den oberen Bereich, oder beide Seiten werden in einem angedockten linken Navigationsbereich angezeigt.</span><span class="sxs-lookup"><span data-stu-id="87e64-176">For example, both pages use the same top pane element, or both pages appear in a docked left navigation pane.</span></span></p></td>
<td style="vertical-align:top;"><strong><span data-ttu-id="87e64-177">Das kommt darauf an.</span><span class="sxs-lookup"><span data-stu-id="87e64-177">It depends</span></span></strong>
<p><span data-ttu-id="87e64-178">Ja, fügen Sie es dem Navigationsverlauf hinzu, jedoch mit zwei Ausnahmen.</span><span class="sxs-lookup"><span data-stu-id="87e64-178">Yes, add to the navigation history, but with 2 notable exceptions.</span></span> <span data-ttu-id="87e64-179">Wenn Sie davon ausgehen, dass Benutzer Ihrer App häufig zwischen Seiten in der Peer-Gruppe wechseln, oder wenn Sie den Navigationszustand/-verlauf innerhalb einer Seite einer Peer-Gruppe beibehalten möchten, dann fügen Sie es dem Navigationsverlauf nicht hinzu.</span><span class="sxs-lookup"><span data-stu-id="87e64-179">If you expect users of your app to switch between pages in the peer group frequently, or if you wish to preserve the navigational state/history within a page of the peer group, then do not add to the navigation history.</span></span> <span data-ttu-id="87e64-180">Wenn der Benutzer in diesem Fall die Zurück-Schaltfläche drückt, wird wieder die letzte Seite aufgerufen, die geöffnet war, bevor der Benutzer zur aktuellen Peer-Gruppe navigierte.</span><span class="sxs-lookup"><span data-stu-id="87e64-180">In this case, when the user presses back, go back to the last page before the user navigated to the current peer group.</span></span> </p>
<p><img src="images/back-nav/nav-pagetopage-samepeer-yesosnavelement.png" alt="Navigation across peer groups when a navigation element is present" /></p></td>
</tr>
<tr class="even">
<td style="vertical-align:top;"><strong><span data-ttu-id="87e64-181">Anzeigen einer vorübergehenden Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="87e64-181">Show a transient UI</span></span></strong>
<p><span data-ttu-id="87e64-182">Die App zeigt ein Popupfenster oder ein untergeordnetes Fenster an, z. B. ein Dialogfeld, einen Begrüßungsbildschirm oder eine Bildschirmtastatur. Anderenfalls wechselt die App in einen speziellen Modus, z. B. den Mehrfachauswahlmodus.</span><span class="sxs-lookup"><span data-stu-id="87e64-182">The app displays a pop-up or child window, such as a dialog, splash screen, or on-screen keyboard, or the app enters a special mode, such as multiple selection mode.</span></span></p></td>
<td style="vertical-align:top;"><strong><span data-ttu-id="87e64-183">Nein</span><span class="sxs-lookup"><span data-stu-id="87e64-183">No</span></span></strong>
<p><span data-ttu-id="87e64-184">Wenn der Benutzer die Zurück-Schaltfläche drückt, sollte die vorübergehende Benutzeroberfläche geschlossen werden (durch Ausblenden der Bildschirmtastatur, Abbrechen des Dialogfelds usw.) und zur Seite zurückgekehrt werden, die die vorübergehende Benutzeroberfläche aufgerufen hat.</span><span class="sxs-lookup"><span data-stu-id="87e64-184">When the user presses the back button, dismiss the transient UI (hide the on-screen keyboard, cancel the dialog, etc) and return to the page that spawned the transient UI.</span></span></p>
<p><img src="images/back-nav/back-transui.png" alt="Showing a transient UI" /></p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top;"><strong><span data-ttu-id="87e64-185">Aufzählen von Elementen</span><span class="sxs-lookup"><span data-stu-id="87e64-185">Enumerate items</span></span></strong>
<p><span data-ttu-id="87e64-186">Die App zeigt die Inhalte für ein Bildschirmelement an, z. B. die Details für das ausgewählte Element in der Master/Details-Liste.</span><span class="sxs-lookup"><span data-stu-id="87e64-186">The app displays content for an on-screen item, such as the details for the selected item in master/details list.</span></span></p></td>
<td style="vertical-align:top;"><strong><span data-ttu-id="87e64-187">Nein</span><span class="sxs-lookup"><span data-stu-id="87e64-187">No</span></span></strong>
<p><span data-ttu-id="87e64-188">Das Aufzählen von Elementen ist mit der Navigation innerhalb einer Peer-Gruppe vergleichbar.</span><span class="sxs-lookup"><span data-stu-id="87e64-188">Enumerating items is similar to navigating within a peer group.</span></span> <span data-ttu-id="87e64-189">Wenn der Benutzer die Zurück-Schaltfläche drückt, sollte zu der Seite navigiert werden, die vor der aktuellen Seite angezeigt wurde, die die Elementenaufzählung enthält.</span><span class="sxs-lookup"><span data-stu-id="87e64-189">When the user presses back, navigate to the page that preceded the current page that has the item enumeration.</span></span></p>
<p><img src="images/back-nav/nav-enumerate.png" alt="Iterm enumeration" /></p></td>
</tr>
</tbody>
</table>
</div>

### <a name="resuming"></a><span data-ttu-id="87e64-190">Fortsetzen</span><span class="sxs-lookup"><span data-stu-id="87e64-190">Resuming</span></span>

<span data-ttu-id="87e64-191">Wenn der Benutzer zu einer anderen App wechselt und zu Ihrer App zurückkehrt, wird empfohlen, zur letzten Seite im Navigationsverlauf zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="87e64-191">When the user switches to another app and returns to your app, we recommend returning to the last page in the navigation history</span></span>

## <a name="related-articles"></a><span data-ttu-id="87e64-192">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="87e64-192">Related articles</span></span>

- [<span data-ttu-id="87e64-193">Navigationsgrundlagen</span><span class="sxs-lookup"><span data-stu-id="87e64-193">Navigation basics</span></span>](navigation-basics.md)