---
author: Jwmsft
Description: Learn how to implement backwards navigation for traversing the user's navigation history within an UWP app.
title: Navigationsverlauf und Rückwärtsnavigation (Windows-Apps)
template: detail.hbs
op-migration-status: ready
ms.author: jimwalk
ms.date: 06/21/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: d2f437db1a1792df22fd084cedee31cb6e590d24
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5942286"
---
# <a name="navigation-history-and-backwards-navigation-for-uwp-apps"></a><span data-ttu-id="19476-103">Navigationsverlauf und Rückwärtsnavigation für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="19476-103">Navigation history and backwards navigation for UWP apps</span></span>

> <span data-ttu-id="19476-104">**Wichtige APIs**: [BackRequested event](https://docs.microsoft.com/uwp/api/Windows.UI.Core.SystemNavigationManager.BackRequested), [SystemNavigationManager class](https://docs.microsoft.com/uwp/api/Windows.UI.Core.SystemNavigationManager), [OnNavigatedTo](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.page.onnavigatedto#Windows_UI_Xaml_Controls_Page_OnNavigatedTo_Windows_UI_Xaml_Navigation_NavigationEventArgs_)</span><span class="sxs-lookup"><span data-stu-id="19476-104">**Important APIs**: [BackRequested event](https://docs.microsoft.com/uwp/api/Windows.UI.Core.SystemNavigationManager.BackRequested), [SystemNavigationManager class](https://docs.microsoft.com/uwp/api/Windows.UI.Core.SystemNavigationManager), [OnNavigatedTo](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.page.onnavigatedto#Windows_UI_Xaml_Controls_Page_OnNavigatedTo_Windows_UI_Xaml_Navigation_NavigationEventArgs_)</span></span>

<span data-ttu-id="19476-105">Die universelle Windows-Plattform (UWP) enthält ein einheitliches System zur Rückwärtsnavigation, mit dem der Navigationsverlauf des Benutzers innerhalb einer App und je nach Gerät von App zu App durchlaufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="19476-105">The Universal Windows Platform (UWP) provides a consistent back navigation system for traversing the user's navigation history within an app and, depending on the device, from app to app.</span></span>

<span data-ttu-id="19476-106">Um die Rückwärtsnavigation in Ihrer App zu implementieren, platzieren Sie einen [Zurück](#Back-button)-Button in der oberen linken Ecke der Benutzeroberfläche Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="19476-106">To implement backwards navigation in your app, place a [back button](#Back-button) at the top left corner of your app's UI.</span></span> <span data-ttu-id="19476-107">Wenn Ihre App das [NavigationView](../controls-and-patterns/navigationview.md)-Steuerelement verwendet, können Sie die integrierte [Zurück-Schaltfläche von NavigationView](../controls-and-patterns/navigationview.md#backwards-navigation) verwenden.</span><span class="sxs-lookup"><span data-stu-id="19476-107">If your app uses the [NavigationView](../controls-and-patterns/navigationview.md) control, then you can use [NavigationView's built-in back button](../controls-and-patterns/navigationview.md#backwards-navigation).</span></span>

<span data-ttu-id="19476-108">Der Benutzer erwartet, dass durch Drücken der Zurück-Schaltfläche die vorherige Seite im Navigationsverlauf der App aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="19476-108">The user expects the back button to navigate to the previous location in the app's navigation history.</span></span> <span data-ttu-id="19476-109">Sie können entscheiden, welche Navigationsaktionen dem Navigationsverlauf hinzugefügt werden sollen und wie auf das Drücken der Zurück-Schaltfläche reagiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="19476-109">Note that it's up to you to decide which navigation actions to add to the navigation history and how to respond to the back button press.</span></span>

## <a name="back-button"></a><span data-ttu-id="19476-110">Zurück-Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="19476-110">Back button</span></span>

<span data-ttu-id="19476-111">Um eine zurück-Schaltfläche zu erstellen, verwenden Sie das [Button](../controls-and-patterns/buttons.md) -Steuerelement mit dem `NavigationBackButtonNormalStyle` Stil, und platzieren Sie die Schaltfläche in der oberen linken Ecke der Benutzeroberfläche Ihrer app (Weitere Informationen finden Sie unter den folgenden XAML-Codebeispielen).</span><span class="sxs-lookup"><span data-stu-id="19476-111">To create a back button, use the [Button](../controls-and-patterns/buttons.md) control with the `NavigationBackButtonNormalStyle` style, and place the button at the top left hand corner of your app's UI (for details, see the XAML code examples below).</span></span>

![Zurück-Schaltfläche oben links in der App-Oberfläche](images/back-nav/BackEnabled.png)

```xaml
<Button Style="{StaticResource NavigationBackButtonNormalStyle}"/>
```

<span data-ttu-id="19476-113">Wenn Ihre App eine obere [CommandBar](../controls-and-patterns/app-bars.md) hat, wird das 44 Pixel hohe Button-Steuerelement nicht sehr gut neben 48 Pixel hohe AppBarButtons passen.</span><span class="sxs-lookup"><span data-stu-id="19476-113">If your app has a top [CommandBar](../controls-and-patterns/app-bars.md), the Button control that is 44px in height will not align with 48px AppBarButtons very nicely.</span></span> <span data-ttu-id="19476-114">Um jedoch Inkonsistenzen zu vermeiden, richten Sie den oberen Teil der Schaltfläche innerhalb der 48 Pixel-Grenzen aus.</span><span class="sxs-lookup"><span data-stu-id="19476-114">However, to avoid inconsistency, align the top of the Button control inside the 48px bounds.</span></span>

![Zurück-Schaltfläche in der oberen Befehlsleiste](images/back-nav/CommandBar.png)

```xaml
<Button VerticalAlignment="Top" HorizontalAlignment="Left" 
Style="{StaticResource NavigationBackButtonNormalStyle}"/>
```

<span data-ttu-id="19476-116">Um UI-Elemente zu minimieren, die sich in Ihrer App bewegen, zeigen Sie eine deaktivierte Zurück-Schaltfläche an, wenn sich nichts im Backstack befindet (siehe Codebeispiel unten).</span><span class="sxs-lookup"><span data-stu-id="19476-116">In order to minimize UI elements moving around in your app, show a disabled back button when there is nothing in the backstack (see code example below).</span></span> <span data-ttu-id="19476-117">Wenn Sie, dass Ihre app nie ein Backstack hat erwarten, müssen Sie jedoch nicht die Schaltfläche "zurück" ständig anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="19476-117">However, if you expect your app will never have a backstack, you don’t need to display the back button at all.</span></span>

![Zustände der Zurück-Schaltfläche](images/back-nav/BackDisabled.png)

## <a name="code-example"></a><span data-ttu-id="19476-119">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="19476-119">Code example</span></span>

<span data-ttu-id="19476-120">Das folgende Codebeispiel demonstriert, wie man das Rückwärtsnavigationsverhalten mit einer Zurück-Schaltfläche implementiert.</span><span class="sxs-lookup"><span data-stu-id="19476-120">The following code example demonstrates how to implement backwards navigation behavior with a back button.</span></span> <span data-ttu-id="19476-121">Der Code reagiert auf das Button-Ereignis [**Click**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.Click) und deaktiviert/aktiviert die Sichtbarkeit der Schaltfläche in [**OnNavigatedTo**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.page.onnavigatedto#Windows_UI_Xaml_Controls_Page_OnNavigatedTo_Windows_UI_Xaml_Navigation_NavigationEventArgs_), das beim Navigieren zu einer neuen Seite aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="19476-121">The code responds to the Button [**Click**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.Click) event and disables/enables the button visibility in [**OnNavigatedTo**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.page.onnavigatedto#Windows_UI_Xaml_Controls_Page_OnNavigatedTo_Windows_UI_Xaml_Navigation_NavigationEventArgs_), which is called when navigating to a new page.</span></span> <span data-ttu-id="19476-122">Das Codebeispiel behandelt auch Eingaben von Hardware- und Softwaresystem-Zurück-Schaltflächen, indem es einen Listener für das [**BackRequested**](https://docs.microsoft.com/uwp/api/windows.ui.core.systemnavigationmanager.BackRequested)-Ereignis registriert.</span><span class="sxs-lookup"><span data-stu-id="19476-122">The code example also handles inputs from hardware and software system back keys by registering a listener for the [**BackRequested**](https://docs.microsoft.com/uwp/api/windows.ui.core.systemnavigationmanager.BackRequested) event.</span></span>

```xaml
<!-- MainPage.xaml -->
<Page x:Class="AppName.MainPage">
...
<Button x:Name="BackButton" Click="Back_Click" Style="{StaticResource NavigationBackButtonNormalStyle}"/>
...
<Page/>
```

<span data-ttu-id="19476-123">Code-Behind:</span><span class="sxs-lookup"><span data-stu-id="19476-123">Code-behind:</span></span>

```csharp
// MainPage.xaml.cs
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

```cppwinrt
// MainPage.cpp
#include "pch.h"
#include "MainPage.h"

#include "winrt/Windows.System.h"
#include "winrt/Windows.UI.Xaml.Controls.h"
#include "winrt/Windows.UI.Xaml.Input.h"
#include "winrt/Windows.UI.Xaml.Navigation.h"

using namespace winrt;
using namespace Windows::Foundation;
using namespace Windows::UI::Xaml;

namespace winrt::PageNavTest::implementation
{
    MainPage::MainPage()
    {
        InitializeComponent();

        Windows::UI::Xaml::Input::KeyboardAccelerator goBack;
        goBack.Key(Windows::System::VirtualKey::GoBack);
        goBack.Invoked({ this, &MainPage::BackInvoked });
        Windows::UI::Xaml::Input::KeyboardAccelerator altLeft;
        altLeft.Key(Windows::System::VirtualKey::Left);
        altLeft.Invoked({ this, &MainPage::BackInvoked });
        KeyboardAccelerators().Append(goBack);
        KeyboardAccelerators().Append(altLeft);
        // ALT routes here.
        altLeft.Modifiers(Windows::System::VirtualKeyModifiers::Menu);
    }

    void MainPage::OnNavigatedTo(Windows::UI::Xaml::Navigation::NavigationEventArgs const& e)
    {
        BackButton().IsEnabled(Frame().CanGoBack());
    }

    void MainPage::Back_Click(IInspectable const&, RoutedEventArgs const&)
    {
        On_BackRequested();
    }

    // Handles system-level BackRequested events and page-level back button Click events.
    bool MainPage::On_BackRequested()
    {
        if (Frame().CanGoBack())
        {
            Frame().GoBack();
            return true;
        }
        return false;
    }

    void MainPage::BackInvoked(Windows::UI::Xaml::Input::KeyboardAccelerator const& sender,
        Windows::UI::Xaml::Input::KeyboardAcceleratorInvokedEventArgs const& args)
    {
        args.Handled(On_BackRequested());
    }
}
```

<span data-ttu-id="19476-124">Wir behandeln, rückwärts Navigation für eine einzelne Seite.</span><span class="sxs-lookup"><span data-stu-id="19476-124">Above, we handle backwards navigation for a single page.</span></span> <span data-ttu-id="19476-125">Sie können die Navigation auf jeder Seite behandeln, wenn Sie bestimmte Seiten aus der Rückwärtsnavigation ausschließen möchten, oder auf Seitenebene Code vor dem Anzeigen der Seite ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="19476-125">You can handle navigation in each page if you want to exclude specific pages from back navigation, or you want to execute page-level code before displaying the page.</span></span>

<span data-ttu-id="19476-126">Um rückwärts Navigation für eine gesamte app behandelt werden, registrieren Sie einen globalen Listener für das [**BackRequested**](https://docs.microsoft.com/uwp/api/windows.ui.core.systemnavigationmanager.BackRequested) -Ereignis in der `App.xaml` Code-Behind-Datei.</span><span class="sxs-lookup"><span data-stu-id="19476-126">To handle backwards navigation for an entire app, you'll register a global listener for the [**BackRequested**](https://docs.microsoft.com/uwp/api/windows.ui.core.systemnavigationmanager.BackRequested) event in the `App.xaml` code-behind file.</span></span>

<span data-ttu-id="19476-127">App.xaml Code-Behind:</span><span class="sxs-lookup"><span data-stu-id="19476-127">App.xaml code-behind:</span></span>

```csharp
// App.xaml.cs
Windows.UI.Core.SystemNavigationManager.GetForCurrentView().BackRequested += App_BackRequested;
Frame rootFrame = Window.Current.Content;
rootFrame.PointerPressed += On_PointerPressed;

private void App_BackRequested(object sender, Windows.UI.Core.BackRequestedEventArgs e)
{
    e.Handled = On_BackRequested();
}

private void On_PointerPressed(object sender, PointerRoutedEventArgs e)
{
    bool isXButton1Pressed =
        e.GetCurrentPoint(sender as UIElement).Properties.PointerUpdateKind == PointerUpdateKind.XButton1Pressed;

    if (isXButton1Pressed)
    {
        e.Handled = On_BackRequested();
    }
}

private bool On_BackRequested()
{
    Frame rootFrame = Window.Current.Content as Frame;
    if (rootFrame.CanGoBack)
    {
        rootFrame.GoBack();
        return true;
    }
    return false;
}
```

```cppwinrt
// App.cpp
#include <winrt/Windows.UI.Core.h>
#include "winrt/Windows.UI.Input.h"
#include "winrt/Windows.UI.Xaml.Input.h"

#include "App.h"
#include "MainPage.h"

using namespace winrt;
...

    Windows::UI::Core::SystemNavigationManager::GetForCurrentView().BackRequested({ this, &App::App_BackRequested });
    Frame rootFrame{ nullptr };
    auto content = Window::Current().Content();
    if (content)
    {
        rootFrame = content.try_as<Frame>();
    }
    rootFrame.PointerPressed({ this, &App::On_PointerPressed });
...

void App::App_BackRequested(IInspectable const& /* sender */, Windows::UI::Core::BackRequestedEventArgs const& e)
{
    e.Handled(On_BackRequested());
}

void App::On_PointerPressed(IInspectable const& sender, Windows::UI::Xaml::Input::PointerRoutedEventArgs const& e)
{
    bool isXButton1Pressed =
        e.GetCurrentPoint(sender.as<UIElement>()).Properties().PointerUpdateKind() == Windows::UI::Input::PointerUpdateKind::XButton1Pressed;

    if (isXButton1Pressed)
    {
        e.Handled(On_BackRequested());
    }
}

// Handles system-level BackRequested events.
bool App::On_BackRequested()
{
    if (Frame().CanGoBack())
    {
        Frame().GoBack();
        return true;
    }
    return false;
}
```

## <a name="optimizing-for-different-device-and-form-factors"></a><span data-ttu-id="19476-128">Optimierung für unterschiedliche Geräte- und Formfaktoren</span><span class="sxs-lookup"><span data-stu-id="19476-128">Optimizing for different device and form factors</span></span>

<span data-ttu-id="19476-129">Diese Anleitung für das Rückwärtsnavigationsdesign gilt für alle Geräte. Verschiedene Geräte und Formfaktoren können jedoch von der Optimierung profitieren.</span><span class="sxs-lookup"><span data-stu-id="19476-129">This backwards navigation design guidance is applicable to all devices, but different device and form factors may benefit from optimization.</span></span> <span data-ttu-id="19476-130">Dies hängt auch von der Hardware-Zurück-Taste ab, der von verschiedenen Shells unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="19476-130">This also depends on the hardware back button supported by different shells.</span></span>

- <span data-ttu-id="19476-131">**Smartphone/Tablet**: Ein Hardware- oder Software-Zurück-Schaltfläche ist auf jedem Smartphone und Tablet vorhanden, aber wir empfehlen, einen In-App-Zurück-Schaltfläche zu verwenden, um die Übersichtlichkeit zu erhöhen.</span><span class="sxs-lookup"><span data-stu-id="19476-131">**Phone/Tablet**: A hardware or software back button is always present on mobile and tablet, but we recommend drawing an in-app back button for clarity.</span></span>
- <span data-ttu-id="19476-132">**Desktop/Hub**: Stellen Sie den In-App-Button in der linken oberen Ecke der Benutzeroberfläche Ihrer App dar.</span><span class="sxs-lookup"><span data-stu-id="19476-132">**Desktop/Hub**: Draw the in-app back button on the top left corner of your app's UI.</span></span>
- <span data-ttu-id="19476-133">**Xbox/TV**: Nutzen Sie keinen Zurück-Schaltfläche. Er macht das UI unnötigerweise unübersichtlich.</span><span class="sxs-lookup"><span data-stu-id="19476-133">**Xbox/TV**: Do not draw a back button, for it will add unnecessary UI clutter.</span></span> <span data-ttu-id="19476-134">Verlassen Sie sich stattdessen auf die Gamepad-Taste B, um rückwärts zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="19476-134">Instead, rely on the Gamepad B button to navigate backwards.</span></span>

<span data-ttu-id="19476-135">Wenn Ihre App auf mehreren Geräten läuft, [erstellen Sie einen benutzerdefinierten visuellen Trigger für die Xbox](../devices/designing-for-tv.md#custom-visual-state-trigger-for-xbox), um die Sichtbarkeit der Schaltfläche umzuschalten.</span><span class="sxs-lookup"><span data-stu-id="19476-135">If your app will run on multiple devices, [create a custom visual trigger for Xbox](../devices/designing-for-tv.md#custom-visual-state-trigger-for-xbox) to toggle the visibility of button.</span></span> <span data-ttu-id="19476-136">Das NavigationView-Steuerelement schaltet automatisch die Sichtbarkeit der Schaltfläche „Zurück” um, wenn Ihre App auf der Xbox läuft.</span><span class="sxs-lookup"><span data-stu-id="19476-136">The NavigationView control will automatically toggle the back button's visibility if your app is running on Xbox.</span></span> 

<span data-ttu-id="19476-137">Wir empfehlen, die folgenden Eingaben für die Rückwärtsnavigation zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="19476-137">We recommend supporting the following inputs for back navigation.</span></span> <span data-ttu-id="19476-138">(Beachten Sie, dass einige dieser Eingaben vom System-BackRequested nicht unterstützt werden und durch separate Ereignisse behandelt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="19476-138">(Note that some of these inputs are not supported by the system BackRequested and must be handled by separate events.)</span></span>

| <span data-ttu-id="19476-139">Eingabe</span><span class="sxs-lookup"><span data-stu-id="19476-139">Input</span></span> | <span data-ttu-id="19476-140">Ereignis</span><span class="sxs-lookup"><span data-stu-id="19476-140">Event</span></span> |
| --- | --- |
| <span data-ttu-id="19476-141">Windows-Rücktaste</span><span class="sxs-lookup"><span data-stu-id="19476-141">Windows-Backspace key</span></span> | <span data-ttu-id="19476-142">BackRequested</span><span class="sxs-lookup"><span data-stu-id="19476-142">BackRequested</span></span> |
| <span data-ttu-id="19476-143">Hardware-Zurück-Taste</span><span class="sxs-lookup"><span data-stu-id="19476-143">Hardware back button</span></span> | <span data-ttu-id="19476-144">BackRequested</span><span class="sxs-lookup"><span data-stu-id="19476-144">BackRequested</span></span> |
| <span data-ttu-id="19476-145">Shell-Tablet-Modus Zurück-Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="19476-145">Shell tablet mode back button</span></span> | <span data-ttu-id="19476-146">BackRequested</span><span class="sxs-lookup"><span data-stu-id="19476-146">BackRequested</span></span> |
| <span data-ttu-id="19476-147">VirtualKey.XButton1</span><span class="sxs-lookup"><span data-stu-id="19476-147">VirtualKey.XButton1</span></span> | <span data-ttu-id="19476-148">PointerPressed</span><span class="sxs-lookup"><span data-stu-id="19476-148">PointerPressed</span></span> |
| <span data-ttu-id="19476-149">VirtualKey.GoBack</span><span class="sxs-lookup"><span data-stu-id="19476-149">VirtualKey.GoBack</span></span> | <span data-ttu-id="19476-150">KeyboardAccelerator.BackInvoked</span><span class="sxs-lookup"><span data-stu-id="19476-150">KeyboardAccelerator.BackInvoked</span></span> |
| <span data-ttu-id="19476-151">ALT + NACH-LINKS</span><span class="sxs-lookup"><span data-stu-id="19476-151">Alt+LeftArrow key</span></span> | <span data-ttu-id="19476-152">KeyboardAccelerator.BackInvoked</span><span class="sxs-lookup"><span data-stu-id="19476-152">KeyboardAccelerator.BackInvoked</span></span> |

<span data-ttu-id="19476-153">Die oben aufgeführten Codebeispiele zeigen, wie man mit diesen Eingaben umgeht.</span><span class="sxs-lookup"><span data-stu-id="19476-153">The code examples provided above demonstrate how to handle all of these inputs.</span></span>

## <a name="system-back-behavior-for-backward-compatibilities"></a><span data-ttu-id="19476-154">System-Rückwärtsverhalten für Rückwärtskompatibilitäten</span><span class="sxs-lookup"><span data-stu-id="19476-154">System back behavior for backward compatibilities</span></span>

<span data-ttu-id="19476-155">Bisher nutzten UWP-Apps [AppViewBackButtonVisibility](https://docs.microsoft.com/uwp/api/windows.ui.core.appviewbackbuttonvisibility) für die Rückwärtsnavigation.</span><span class="sxs-lookup"><span data-stu-id="19476-155">Previously, UWP apps used [AppViewBackButtonVisibility](https://docs.microsoft.com/uwp/api/windows.ui.core.appviewbackbuttonvisibility) for backwards navigation.</span></span> <span data-ttu-id="19476-156">Die API wird weiterhin unterstützt werden, um Abwärtskompatibilität zu gewährleisten, aber wir empfehlen nicht mehr zu verlassen sich [AppViewBackButtonVisibility](https://docs.microsoft.com/uwp/api/windows.ui.core.appviewbackbuttonvisibility).</span><span class="sxs-lookup"><span data-stu-id="19476-156">The API will continue to be supported to ensure backward compatibility, but we no longer recommend relying on [AppViewBackButtonVisibility](https://docs.microsoft.com/uwp/api/windows.ui.core.appviewbackbuttonvisibility).</span></span> <span data-ttu-id="19476-157">Stattdessen sollte Ihre App eine eigene Zurück-Schaltfläche in der App darstellen.</span><span class="sxs-lookup"><span data-stu-id="19476-157">Instead, your app should draw its own in-app back button.</span></span>

<span data-ttu-id="19476-158">Wenn Ihre app weiterhin mithilfe von [AppViewBackButtonVisibility](https://docs.microsoft.com/uwp/api/windows.ui.core.appviewbackbuttonvisibility), klicken Sie dann das System die Benutzeroberfläche gerendert wird, das System zurück-Schaltfläche:</span><span class="sxs-lookup"><span data-stu-id="19476-158">If your app continues using [AppViewBackButtonVisibility](https://docs.microsoft.com/uwp/api/windows.ui.core.appviewbackbuttonvisibility), then the system UI will render the system back button:</span></span>

- <span data-ttu-id="19476-159">Wenn Ihre app **nicht mit Registerkarten**ist, wird die Schaltfläche "zurück" in der Titelleiste gerendert.</span><span class="sxs-lookup"><span data-stu-id="19476-159">If your app is **not tabbed**, then the back button is rendered inside the title bar.</span></span> <span data-ttu-id="19476-160">Die visuellen Erfahrung und den Benutzerinteraktionen für die zurück-Schaltfläche bleiben unverändert aus vorherigen Builds.</span><span class="sxs-lookup"><span data-stu-id="19476-160">The visual experience and user interactions for the back button are unchanged from previous builds.</span></span>

    ![Schaltfläche "zurück" in der Titelleiste](images/nav-back-pc.png)

- <span data-ttu-id="19476-162">Wenn eine app **mit Registerkarten**ist, wird die Schaltfläche "zurück" in einen neuen System nach hinten gerendert wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="19476-162">If an app is **tabbed**, then the back button is rendered inside a new system back bar.</span></span>

    ![System gezeichnet wieder Schaltflächenleiste](images/back-nav/tabs.png)

### <a name="system-back-bar"></a><span data-ttu-id="19476-164">Systemeigene Leiste</span><span class="sxs-lookup"><span data-stu-id="19476-164">System back bar</span></span>

> [!NOTE]
> <span data-ttu-id="19476-165">"Systemeigene Leiste" ist nur eine Beschreibung, nicht offizieller Name.</span><span class="sxs-lookup"><span data-stu-id="19476-165">"System back bar" is only a description, not an official name.</span></span>

<span data-ttu-id="19476-166">Die systemeigene rückwärtsnavigationsleiste ist ein "Band", die zwischen dem registerkartenband und Inhaltsbereich der app eingefügt wird.</span><span class="sxs-lookup"><span data-stu-id="19476-166">The system back bar is a “band” that is inserted between the tab band and the app’s content area.</span></span> <span data-ttu-id="19476-167">Das Band läuft über die Breite der App und enthält die Zurück-Schaltfläche auf der linken Seite.</span><span class="sxs-lookup"><span data-stu-id="19476-167">The band goes across the width of the app, with the back button on the left edge.</span></span> <span data-ttu-id="19476-168">Des Bands ist die vertikale Höhe von 32 Pixel um sicherzustellen, dass ausreichende berührungszielgröße für die Schaltfläche "zurück".</span><span class="sxs-lookup"><span data-stu-id="19476-168">The band has a vertical height of 32 pixels to ensure adequate touch target size for the back button.</span></span>

<span data-ttu-id="19476-169">Die systemeigene Rückwärtsnavigationsleiste wird dynamisch angezeigt, abhängig von der Sichtbarkeit der Zurück-Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="19476-169">The system back bar is displayed dynamically, based on back button visibility.</span></span> <span data-ttu-id="19476-170">Wenn die zurück-Schaltfläche angezeigt wird, die systemeigene rückwärtsnavigationsleiste eingefügt, dass app-Inhalt nach unten 32 Pixel unter dem registerkartenband verschoben.</span><span class="sxs-lookup"><span data-stu-id="19476-170">When the back button is visible, the system back bar is inserted, shifting app content down by 32 pixels below the tab band.</span></span> <span data-ttu-id="19476-171">Wenn die Schaltfläche "zurück" ausgeblendet ist, die systemeigene rückwärtsnavigationsleiste dynamisch entfernt, dass app-Inhalt nach oben 32 Pixel um dem registerkartenband erfüllen verschoben.</span><span class="sxs-lookup"><span data-stu-id="19476-171">When the back button is hidden, the system back bar is dynamically removed, shifting app content up by 32 pixels to meet the tab band.</span></span> <span data-ttu-id="19476-172">Es wird empfohlen, um zu vermeiden, dass Ihre app Benutzeroberfläche verschoben nach oben oder unten, zeichnen eine [Schaltfläche "zurück" in-app](#back-button).</span><span class="sxs-lookup"><span data-stu-id="19476-172">To avoid having your app's UI shift up or down, we recommend drawing an [in-app back button](#back-button).</span></span>

<span data-ttu-id="19476-173">[Anpassungen der Titelleiste](../shell/title-bar.md) wird dabei auf die app-Registerkarte und die systemeigene rückwärtsnavigationsleiste.</span><span class="sxs-lookup"><span data-stu-id="19476-173">[Title bar customizations](../shell/title-bar.md) will carry over to both the app tab and the system back bar.</span></span> <span data-ttu-id="19476-174">Wenn Ihre app Hintergrund und Vordergrund-Farbeigenschaften mit [ApplicationViewTitleBar gibt](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationviewtitlebar), und klicken Sie dann die Farben für die Registerkarte und System angewendet Leiste.</span><span class="sxs-lookup"><span data-stu-id="19476-174">If your app specifies background and foreground color properties with [ApplicationViewTitleBar](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationviewtitlebar), then the colors will be applied to the tab and system back bar.</span></span>

<span data-ttu-id="19476-175">[Anpassungen der Titelleiste](../shell/title-bar.md) wird dabei auf die app-Registerkarte und die systemeigene rückwärtsnavigationsleiste.</span><span class="sxs-lookup"><span data-stu-id="19476-175">[Title bar customizations](../shell/title-bar.md) will carry over to both the app tab and the system back bar.</span></span> <span data-ttu-id="19476-176">Wenn Ihre app Hintergrund und Vordergrund-Farbeigenschaften mit [ApplicationViewTitleBar gibt](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationviewtitlebar), und klicken Sie dann die Farben für die Registerkarte und System angewendet Leiste.</span><span class="sxs-lookup"><span data-stu-id="19476-176">If your app specifies background and foreground color properties with [ApplicationViewTitleBar](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationviewtitlebar), then the colors will be applied to the tab and system back bar.</span></span>

## <a name="guidelines-for-custom-back-navigation-behavior"></a><span data-ttu-id="19476-177">Richtlinien für das benutzerdefinierte Verhalten der Rückwärtsnavigation</span><span class="sxs-lookup"><span data-stu-id="19476-177">Guidelines for custom back navigation behavior</span></span>

<span data-ttu-id="19476-178">Wenn Sie Ihre eigene Zurück-Stapelnavigation bereitstellen möchten, sollte die Benutzeroberfläche mit anderen Apps konsistent sein.</span><span class="sxs-lookup"><span data-stu-id="19476-178">If you choose to provide your own back stack navigation, the experience should be consistent with other apps.</span></span> <span data-ttu-id="19476-179">Wir empfehlen, die folgenden Muster für Navigationsaktionen zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="19476-179">We recommend that you follow the following patterns for navigation actions:</span></span>

<div class="mx-responsive-img">
<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="19476-180">Navigationsaktion</span><span class="sxs-lookup"><span data-stu-id="19476-180">Navigation action</span></span></th>
<th align="left"><span data-ttu-id="19476-181">Zum Navigationsverlauf hinzufügen?</span><span class="sxs-lookup"><span data-stu-id="19476-181">Add to navigation history?</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top;"><strong><span data-ttu-id="19476-182">Seite zu Seite, verschiedene Peer-Gruppen</span><span class="sxs-lookup"><span data-stu-id="19476-182">Page to page, different peer groups</span></span></strong></td>
<td style="vertical-align:top;"><strong><span data-ttu-id="19476-183">Ja</span><span class="sxs-lookup"><span data-stu-id="19476-183">Yes</span></span></strong>
<p><span data-ttu-id="19476-184">In der folgenden Abbildung navigiert der Benutzer von Ebene 1 der App zu Ebene 2. Dabei werden Peer-Gruppen durchlaufen, sodass die Navigation dem Navigationsverlauf hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="19476-184">In this illustration, the user navigates from level 1 of the app to level 2, crossing peer groups, so the navigation is added to the navigation history.</span></span></p>
<p><img src="images/back-nav/nav-pagetopage-diffpeers-imageonly1.png" alt="Navigation across peer groups" /></p>
<p><span data-ttu-id="19476-185">In der nächsten Abbildung navigiert der Benutzer zwischen zwei Peer-Gruppen derselben Ebene. Er durchläuft erneut Peer-Gruppen, sodass die Navigation dem Navigationsverlauf hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="19476-185">In the next illustration, the user navigates between two peer groups at the same level, again crossing peer groups, so the navigation is added to the navigation history.</span></span></p>
<p><img src="images/back-nav/nav-pagetopage-diffpeers-imageonly2.png" alt="Navigation across peer groups" /></p></td>
</tr>
<tr class="even">
<td style="vertical-align:top;"><strong><span data-ttu-id="19476-186">Seite zu Seite, gleiche Peer-Gruppe, kein Bildschirmnavigationselement</span><span class="sxs-lookup"><span data-stu-id="19476-186">Page to page, same peer group, no on-screen navigation element</span></span></strong>
<p><span data-ttu-id="19476-187">Der Benutzer navigiert von einer Seite zu einer anderen mit derselben Peer-Gruppe.</span><span class="sxs-lookup"><span data-stu-id="19476-187">The user navigates from one page to another with the same peer group.</span></span> <span data-ttu-id="19476-188">Es ist nicht auf dem Bildschirm Navigationselement (z. B. <a href="https://docs.microsoft.com/windows/uwp/design/controls-and-patterns/navigationview">NavigationView</a>), die direkte Navigation zu beiden Seiten bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="19476-188">There is no on-screen navigation element (such as <a href="https://docs.microsoft.com/windows/uwp/design/controls-and-patterns/navigationview">NavigationView</a>) that provides direct navigation to both pages.</span></span></p></td>
<td style="vertical-align:top;"><strong><span data-ttu-id="19476-189">Ja</span><span class="sxs-lookup"><span data-stu-id="19476-189">Yes</span></span></strong>
<p><span data-ttu-id="19476-190">In der folgenden Abbildung navigiert zwischen zwei Seiten in derselben Peer-Gruppe und die Navigation dem Navigationsverlauf hinzugefügt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="19476-190">In the following illustration, the user navigates between two pages in the same peer group, and the navigation should be added to the navigation history.</span></span></p>
<p><img src="images/back-nav/nav-pagetopage-samepeer-noosnavelement.png" alt="Navigation within a peer group" /></p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top;"><strong><span data-ttu-id="19476-191">Seite zu Seite, gleiche Peer-Gruppe, mit einem Bildschirmnavigationselement</span><span class="sxs-lookup"><span data-stu-id="19476-191">Page to page, same peer group, with an on-screen navigation element</span></span></strong>
<p><span data-ttu-id="19476-192">Der Benutzer navigiert von einer Seite zu einer anderen in derselben Peer-Gruppe.</span><span class="sxs-lookup"><span data-stu-id="19476-192">The user navigates from one page to another in the same peer group.</span></span> <span data-ttu-id="19476-193">Beide Seiten werden in der gleichen Navigationselement beinhaltet, z. B. <a href="https://docs.microsoft.com/windows/uwp/design/controls-and-patterns/navigationview">NavigationView</a>angezeigt.</span><span class="sxs-lookup"><span data-stu-id="19476-193">Both pages are shown in the same navigation element, such as <a href="https://docs.microsoft.com/windows/uwp/design/controls-and-patterns/navigationview">NavigationView</a>.</span></span></p></td>
<td style="vertical-align:top;"><strong><span data-ttu-id="19476-194">Das kommt darauf an.</span><span class="sxs-lookup"><span data-stu-id="19476-194">It depends</span></span></strong>
<p><span data-ttu-id="19476-195">Ja, dem Navigationsverlauf, mit zwei Ausnahmen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="19476-195">Yes, add to the navigation history, with two notable exceptions.</span></span> <span data-ttu-id="19476-196">Fügen Sie Wenn Sie davon ausgehen, dass Benutzer Ihrer app zwischen Seiten in der Peer-Gruppe häufig wechseln, oder wenn Sie die Navigationshierarchie beibehalten möchten, dann keine dem Navigationsverlauf.</span><span class="sxs-lookup"><span data-stu-id="19476-196">If you expect users of your app to switch between pages in the peer group frequently, or if you wish to preserve the navigational hierarchy, then do not add to the navigation history.</span></span> <span data-ttu-id="19476-197">Wenn der Benutzer in diesem Fall die Zurück-Schaltfläche drückt, wird wieder die letzte Seite aufgerufen, die geöffnet war, bevor der Benutzer zur aktuellen Peer-Gruppe navigierte.</span><span class="sxs-lookup"><span data-stu-id="19476-197">In this case, when the user presses back, go back to the last page before the user navigated to the current peer group.</span></span> </p>
<p><img src="images/back-nav/nav-pagetopage-samepeer-yesosnavelement.png" alt="Navigation across peer groups when a navigation element is present" /></p></td>
</tr>
<tr class="even">
<td style="vertical-align:top;"><strong><span data-ttu-id="19476-198">Anzeigen einer vorübergehenden Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="19476-198">Show a transient UI</span></span></strong>
<p><span data-ttu-id="19476-199">Die App zeigt ein Popupfenster oder ein untergeordnetes Fenster an, z. B. ein Dialogfeld, einen Begrüßungsbildschirm oder eine Bildschirmtastatur. Anderenfalls wechselt die App in einen speziellen Modus, z. B. den Mehrfachauswahlmodus.</span><span class="sxs-lookup"><span data-stu-id="19476-199">The app displays a pop-up or child window, such as a dialog, splash screen, or on-screen keyboard, or the app enters a special mode, such as multiple selection mode.</span></span></p></td>
<td style="vertical-align:top;"><strong><span data-ttu-id="19476-200">Nein</span><span class="sxs-lookup"><span data-stu-id="19476-200">No</span></span></strong>
<p><span data-ttu-id="19476-201">Wenn der Benutzer die Zurück-Schaltfläche drückt, sollte die vorübergehende Benutzeroberfläche geschlossen werden (durch Ausblenden der Bildschirmtastatur, Abbrechen des Dialogfelds usw.) und zur Seite zurückgekehrt werden, die die vorübergehende Benutzeroberfläche aufgerufen hat.</span><span class="sxs-lookup"><span data-stu-id="19476-201">When the user presses the back button, dismiss the transient UI (hide the on-screen keyboard, cancel the dialog, etc) and return to the page that spawned the transient UI.</span></span></p>
<p><img src="images/back-nav/back-transui.png" alt="Showing a transient UI" /></p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top;"><strong><span data-ttu-id="19476-202">Aufzählen von Elementen</span><span class="sxs-lookup"><span data-stu-id="19476-202">Enumerate items</span></span></strong>
<p><span data-ttu-id="19476-203">Die App zeigt die Inhalte für ein Bildschirmelement an, z. B. die Details für das ausgewählte Element in der Master/Details-Liste.</span><span class="sxs-lookup"><span data-stu-id="19476-203">The app displays content for an on-screen item, such as the details for the selected item in master/details list.</span></span></p></td>
<td style="vertical-align:top;"><strong><span data-ttu-id="19476-204">Nein</span><span class="sxs-lookup"><span data-stu-id="19476-204">No</span></span></strong>
<p><span data-ttu-id="19476-205">Das Aufzählen von Elementen ist mit der Navigation innerhalb einer Peer-Gruppe vergleichbar.</span><span class="sxs-lookup"><span data-stu-id="19476-205">Enumerating items is similar to navigating within a peer group.</span></span> <span data-ttu-id="19476-206">Wenn der Benutzer die Zurück-Schaltfläche drückt, sollte zu der Seite navigiert werden, die vor der aktuellen Seite angezeigt wurde, die die Elementenaufzählung enthält.</span><span class="sxs-lookup"><span data-stu-id="19476-206">When the user presses back, navigate to the page that preceded the current page that has the item enumeration.</span></span></p>
<p><img src="images/back-nav/nav-enumerate.png" alt="Iterm enumeration" /></p></td>
</tr>
</tbody>
</table>
</div>

### <a name="resuming"></a><span data-ttu-id="19476-207">Fortsetzen</span><span class="sxs-lookup"><span data-stu-id="19476-207">Resuming</span></span>

<span data-ttu-id="19476-208">Wenn der Benutzer zu einer anderen App wechselt und zu Ihrer App zurückkehrt, wird empfohlen, zur letzten Seite im Navigationsverlauf zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="19476-208">When the user switches to another app and returns to your app, we recommend returning to the last page in the navigation history.</span></span>

## <a name="related-articles"></a><span data-ttu-id="19476-209">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="19476-209">Related articles</span></span>

- [<span data-ttu-id="19476-210">Navigationsgrundlagen</span><span class="sxs-lookup"><span data-stu-id="19476-210">Navigation basics</span></span>](navigation-basics.md)
