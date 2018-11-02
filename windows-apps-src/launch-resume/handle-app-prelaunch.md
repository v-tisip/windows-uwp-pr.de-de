---
author: TylerMSFT
title: Behandeln des Vorabstarts von Apps
description: Erfahren Sie, wie Sie den Vorabstart von Apps durch Überschreiben der OnLaunched-Methode und Aufrufen von CoreApplication.EnablePrelaunch(true) behandeln.
ms.assetid: A4838AC2-22D7-46BA-9EB2-F3C248E22F52
ms.author: twhitney
ms.date: 07/05/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: a13ec942080d7fe517a10b837bea9ae8fae27750
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5946217"
---
# <a name="handle-app-prelaunch"></a><span data-ttu-id="d4130-104">Behandeln des Vorabstarts von Apps</span><span class="sxs-lookup"><span data-stu-id="d4130-104">Handle app prelaunch</span></span>

<span data-ttu-id="d4130-105">Erfahren Sie, wie Sie den Vorabstart von Apps durch außer Kraft setzen der [**OnLaunched**](https://msdn.microsoft.com/library/windows/apps/br242335)-Methode behandeln.</span><span class="sxs-lookup"><span data-stu-id="d4130-105">Learn how to handle app prelaunch by overriding the [**OnLaunched**](https://msdn.microsoft.com/library/windows/apps/br242335) method.</span></span>

## <a name="introduction"></a><span data-ttu-id="d4130-106">Einführung</span><span class="sxs-lookup"><span data-stu-id="d4130-106">Introduction</span></span>

<span data-ttu-id="d4130-107">Wenn verfügbaren Systemressourcen zulassen, die startleistung von UWP-apps auf Desktopgerät Gerätefamilie Geräte verbessern, indem Sie proaktiv Starten des Benutzers am häufigsten verwendeten apps im Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="d4130-107">When available system resources allow, the startup performance of UWP apps on desktop device family devices is improved by proactively launching the user’s most frequently used apps in the background.</span></span> <span data-ttu-id="d4130-108">Eine vorab gestartete App wird kurz nach dem Start in den angehaltenen Zustand versetzt.</span><span class="sxs-lookup"><span data-stu-id="d4130-108">A prelaunched app is put into the suspended state shortly after it is launched.</span></span> <span data-ttu-id="d4130-109">Wenn der Benutzer die App dann aufruft, wird sie fortgesetzt, indem sie vom angehaltenen Zustand in den ausgeführten Zustand versetzt wird. Dies ist schneller als ein Kaltstart der App.</span><span class="sxs-lookup"><span data-stu-id="d4130-109">Then, when the user invokes the app, the app is resumed by bringing it from the suspended state to the running state--which is faster than launching the app cold.</span></span> <span data-ttu-id="d4130-110">Der Benutzer gewinnt den Eindruck, dass die App sehr schnell startet.</span><span class="sxs-lookup"><span data-stu-id="d4130-110">The user's experience is that the app simply launched very quickly.</span></span>

<span data-ttu-id="d4130-111">Vor Windows10 waren die Vorteile des Vorabstarts nicht automatisch für Apps verfügbar.</span><span class="sxs-lookup"><span data-stu-id="d4130-111">Prior to Windows 10, apps did not automatically take advantage of prelaunch.</span></span> <span data-ttu-id="d4130-112">In Windows 10 Version 1511, alle universellen Windows-Plattform (UWP) apps Kandidaten für den Vorabstart eingerichtet wurden.</span><span class="sxs-lookup"><span data-stu-id="d4130-112">In Windows10, version 1511, all Universal Windows Platform (UWP) apps were candidates for being prelaunched.</span></span> <span data-ttu-id="d4130-113">In Windows 10, Version 1607, müssen Sie den Vorabstart aktivieren, in dem Sie [CoreApplication.EnablePrelaunch(true)](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.coreapplication.enableprelaunch.aspx) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="d4130-113">In Windows 10, version 1607, you must opt-in to prelaunch behavior by calling [CoreApplication.EnablePrelaunch(true)](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.coreapplication.enableprelaunch.aspx).</span></span> <span data-ttu-id="d4130-114">Ein empfohlener Bereich für diesen Aufruf ist `OnLaunched()` in der Nähe der `if (e.PrelaunchActivated == false)`-Überprüfung.</span><span class="sxs-lookup"><span data-stu-id="d4130-114">A good place to put this call is within `OnLaunched()` near the location that the `if (e.PrelaunchActivated == false)` check is made.</span></span>

<span data-ttu-id="d4130-115">Ob eine App vorab gestartet wird, ist von den Systemressourcen abhängig.</span><span class="sxs-lookup"><span data-stu-id="d4130-115">Whether an app is prelaunched depends on system resources.</span></span> <span data-ttu-id="d4130-116">Wenn die Systemressourcen ausgelastet sind, werden Apps nicht vorab gestartet.</span><span class="sxs-lookup"><span data-stu-id="d4130-116">If the system is experiencing resource pressure, apps are not prelaunched.</span></span>

<span data-ttu-id="d4130-117">Für einige App-Typen muss u.U. das Startverhalten geändert werden, damit der Vorabstart reibungslos funktioniert.</span><span class="sxs-lookup"><span data-stu-id="d4130-117">Some types of apps may need to change their startup behavior to work well with prelaunch.</span></span> <span data-ttu-id="d4130-118">Beispielsweise kann eine App, die beim Start Musik wiedergibt, ein Spiel, das dem Benutzer beim Start aufwändige visuelle Elemente anzeigt, eine Messaging-App, welche während des Starts die Onlinesichtbarkeit des Benutzers ändert, erkennen, ob die App vorab gestartet wurde und das Startverhalten wie in den folgenden Abschnitten beschrieben ändern.</span><span class="sxs-lookup"><span data-stu-id="d4130-118">For example, an app that plays music when its starts up, a game which assumes the user is present and displays elaborate visuals when the app starts up, a messaging app that changes the user's online visibility during startup, can identify when the app was prelaunched and can change their startup behavior as described in the sections below.</span></span>

<span data-ttu-id="d4130-119">Die Standardvorlagen für XAML-Projekte (C#, VB, C++) und WinJS in passen den Vorabstart in Visual Studio2015 Update3 an.</span><span class="sxs-lookup"><span data-stu-id="d4130-119">The default templates for XAML Projects (C#, VB, C++) and WinJS accommodate prelaunch in Visual Studio 2015 Update 3.</span></span>

## <a name="prelaunch-and-the-app-lifecycle"></a><span data-ttu-id="d4130-120">Vorabstart und App-Lebenszyklus</span><span class="sxs-lookup"><span data-stu-id="d4130-120">Prelaunch and the app lifecycle</span></span>

<span data-ttu-id="d4130-121">Nach dem Vorabstart wechselt die App in den angehaltenen Zustand.</span><span class="sxs-lookup"><span data-stu-id="d4130-121">After an app is prelaunched, it will enter the suspended state.</span></span> <span data-ttu-id="d4130-122">(siehe [Behandeln des Anhaltens von Apps](suspend-an-app.md)).</span><span class="sxs-lookup"><span data-stu-id="d4130-122">(see [Handle app suspend](suspend-an-app.md)).</span></span>

## <a name="detect-and-handle-prelaunch"></a><span data-ttu-id="d4130-123">Erkennen und Behandeln des Vorabstarts</span><span class="sxs-lookup"><span data-stu-id="d4130-123">Detect and handle prelaunch</span></span>

<span data-ttu-id="d4130-124">Apps empfangen das [**LaunchActivatedEventArgs.PrelaunchActivated**](https://msdn.microsoft.com/library/windows/apps/dn263740)-Kennzeichen während der Aktivierung.</span><span class="sxs-lookup"><span data-stu-id="d4130-124">Apps receive the [**LaunchActivatedEventArgs.PrelaunchActivated**](https://msdn.microsoft.com/library/windows/apps/dn263740) flag during activation.</span></span> <span data-ttu-id="d4130-125">Verwenden Sie dieses Flag, um Code auszuführen, der nur ausgeführt werden soll, wenn der Benutzer die app explizit startet wie in der folgenden Änderung [**Application.OnLaunched**](https://msdn.microsoft.com/library/windows/apps/br242335)dargestellt.</span><span class="sxs-lookup"><span data-stu-id="d4130-125">Use this flag to run code that should only run when the user explicitly launches the app, as shown in the following modification to [**Application.OnLaunched**](https://msdn.microsoft.com/library/windows/apps/br242335).</span></span>

```csharp
protected override void OnLaunched(LaunchActivatedEventArgs e)
{
    // CoreApplication.EnablePrelaunch was introduced in Windows 10 version 1607
    bool canEnablePrelaunch = Windows.Foundation.Metadata.ApiInformation.IsMethodPresent("Windows.ApplicationModel.Core.CoreApplication", "EnablePrelaunch");

    // NOTE: Only enable this code if you are targeting a version of Windows 10 prior to version 1607
    // and you want to opt-out of prelaunch.
    // In Windows 10 version 1511, all UWP apps were candidates for prelaunch.
    // Starting in Windows 10 version 1607, the app must opt-in to be prelaunched.
    //if ( !canEnablePrelaunch && e.PrelaunchActivated == true)
    //{
    //    return;
    //}

    Frame rootFrame = Window.Current.Content as Frame;

    // Do not repeat app initialization when the Window already has content,
    // just ensure that the window is active
    if (rootFrame == null)
    {
        // Create a Frame to act as the navigation context and navigate to the first page
        rootFrame = new Frame();

        rootFrame.NavigationFailed += OnNavigationFailed;

        if (e.PreviousExecutionState == ApplicationExecutionState.Terminated)
        {
            //TODO: Load state from previously suspended application
        }

        // Place the frame in the current Window
        Window.Current.Content = rootFrame;
    }

    if (e.PrelaunchActivated == false)
    {
        // On Windows 10 version 1607 or later, this code signals that this app wants to participate in prelaunch
        if (canEnablePrelaunch)
        {
            TryEnablePrelaunch();
        }

        // TODO: This is not a prelaunch activation. Perform operations which
        // assume that the user explicitly launched the app such as updating
        // the online presence of the user on a social network, updating a
        // what's new feed, etc.

        if (rootFrame.Content == null)
        {
            // When the navigation stack isn't restored navigate to the first page,
            // configuring the new page by passing required information as a navigation
            // parameter
            rootFrame.Navigate(typeof(MainPage), e.Arguments);
        }
        // Ensure the current window is active
        Window.Current.Activate();
    }
}

/// <summary>
/// Encapsulates the call to CoreApplication.EnablePrelaunch() so that the JIT
/// won't encounter that call (and prevent the app from running when it doesn't
/// find it), unless this method gets called. This method should only
/// be called when the caller determines that we are running on a system that
/// supports CoreApplication.EnablePrelaunch().
/// </summary>
private void TryEnablePrelaunch()
{
    Windows.ApplicationModel.Core.CoreApplication.EnablePrelaunch(true);
}
```

<span data-ttu-id="d4130-126">Hinweis: die `TryEnablePrelaunch()` funktionieren, oben beschrieben.</span><span class="sxs-lookup"><span data-stu-id="d4130-126">Note the `TryEnablePrelaunch()` function, above.</span></span> <span data-ttu-id="d4130-127">Der Grund der Aufruf zu `CoreApplication.EnablePrelaunch()` wird umgerechnet Out in diese Funktion ist, da, wenn eine Methode aufgerufen wird, das JIT (Just-in-Time-Kompilierung) versucht, die gesamte Methode zu kompilieren.</span><span class="sxs-lookup"><span data-stu-id="d4130-127">The reason the call to `CoreApplication.EnablePrelaunch()` is factored out into this function is because when a method is called, the JIT (just in time compilation) will attempt to compile the entire method.</span></span> <span data-ttu-id="d4130-128">Wenn Ihre app auf einer Version von Windows 10 ausgeführt wird, die nicht unterstützt `CoreApplication.EnablePrelaunch()`, und klicken Sie dann das JIT schlägt fehl.</span><span class="sxs-lookup"><span data-stu-id="d4130-128">If your app is running on a version of Windows 10 that doesn't support `CoreApplication.EnablePrelaunch()`, then the JIT will fail.</span></span> <span data-ttu-id="d4130-129">Durch den Aufruf in eine Methode, die nur aufgerufen wird, wenn die app ermittelt, dass die Plattform unterstützt Zerlegung `CoreApplication.EnablePrelaunch()`, wir dieses Problem zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="d4130-129">By factoring the call into a method that is only called when the app determines that the platform supports `CoreApplication.EnablePrelaunch()`, we avoid that problem.</span></span>

<span data-ttu-id="d4130-130">Es gibt auch im obigen Beispiel code, dass Sie kommentieren können, wenn Ihre app Vorabstart Teilnahme während der Ausführung unter Windows 10, Version 1511 muss.</span><span class="sxs-lookup"><span data-stu-id="d4130-130">There is also code in the example above that you can uncomment if your app needs to opt-out of prelaunch when running on Windows 10, version 1511.</span></span> <span data-ttu-id="d4130-131">In Version 1511, automatisch alle UWP-apps zugelassen wurden in Vorabstart, die möglicherweise nicht für Ihre app geeignet.</span><span class="sxs-lookup"><span data-stu-id="d4130-131">In version 1511, all UWP apps were automatically opted into prelaunch, which may not be appropriate for your app.</span></span>

## <a name="use-the-visibilitychanged-event"></a><span data-ttu-id="d4130-132">Verwenden des VisibilityChanged-Ereignisses</span><span class="sxs-lookup"><span data-stu-id="d4130-132">Use the VisibilityChanged event</span></span>

<span data-ttu-id="d4130-133">Eine durch den Vorabstart aktivierte App ist für den Benutzer nicht sichtbar.</span><span class="sxs-lookup"><span data-stu-id="d4130-133">Apps activated by prelaunch are not visible to the user.</span></span> <span data-ttu-id="d4130-134">Sie wird sichtbar, wenn der Benutzer zur App wechselt.</span><span class="sxs-lookup"><span data-stu-id="d4130-134">They become visible when the user switches to them.</span></span> <span data-ttu-id="d4130-135">Möglicherweise sollen bestimmte Vorgänge verzögert werden, bis das Hauptfenster der App sichtbar wird.</span><span class="sxs-lookup"><span data-stu-id="d4130-135">You may want to delay certain operations until your app's main window becomes visible.</span></span> <span data-ttu-id="d4130-136">Wenn Ihre App z.B. eine Liste mit Neuigkeiten aus einem Feed anzeigt, können Sie die Liste während des [**VisibilityChanged**](https://msdn.microsoft.com/library/windows/apps/hh702458)-Ereignisses aktualisieren, anstatt eine Liste zu verwenden, die beim Vorabstart der App erstellt wurde. Denn diese kann bereits veraltet sein, wenn der Benutzer die App aktiviert.</span><span class="sxs-lookup"><span data-stu-id="d4130-136">For example, if your app displays a list of what's new items from a feed, you could update the list during the [**VisibilityChanged**](https://msdn.microsoft.com/library/windows/apps/hh702458) event rather than use the list that was built when the app was prelaunched because it may become stale by the time the user activates the app.</span></span> <span data-ttu-id="d4130-137">Der folgende Code behandelt das **VisibilityChanged**-Ereignis für **MainPage**:</span><span class="sxs-lookup"><span data-stu-id="d4130-137">The following code handles the **VisibilityChanged** event for **MainPage**:</span></span>

```csharp
public sealed partial class MainPage : Page
{
    public MainPage()
    {
        this.InitializeComponent();

        Window.Current.VisibilityChanged += WindowVisibilityChangedEventHandler;
    }

    void WindowVisibilityChangedEventHandler(System.Object sender, Windows.UI.Core.VisibilityChangedEventArgs e)
    {
        // Perform operations that should take place when the application becomes visible rather than
        // when it is prelaunched, such as building a what's new feed
    }
}
```

## <a name="directx-games-guidance"></a><span data-ttu-id="d4130-138">Leitfaden für DirectX-Spiele</span><span class="sxs-lookup"><span data-stu-id="d4130-138">DirectX games guidance</span></span>

<span data-ttu-id="d4130-139">Für DirectX-Spiele sollte der Vorabstart im Allgemeinen nicht aktiviert werden, da bei vielen DirectX-Spielen Initialisierungsvorgänge ausgeführt werden, bevor der Vorabstart erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="d4130-139">DirectX games should generally not enable prelaunch because many DirectX games do their initialization before prelaunch can be detected.</span></span> <span data-ttu-id="d4130-140">Ab Windows-Version 1607 (Anniversary-Edition) werden Spiele nicht standardmäßig vorab gestartet.</span><span class="sxs-lookup"><span data-stu-id="d4130-140">Starting with Windows 1607, Anniversary edition, your game will not be prelaunched by default.</span></span>  <span data-ttu-id="d4130-141">Wenn Sie den Vorabstart für Ihr Spiel verwenden möchten, rufen Sie [CoreApplication.EnablePrelaunch(true)](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.coreapplication.enableprelaunch.aspx) auf.</span><span class="sxs-lookup"><span data-stu-id="d4130-141">If you do want your game to take advantage of prelaunch, call [CoreApplication.EnablePrelaunch(true)](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.coreapplication.enableprelaunch.aspx).</span></span>

<span data-ttu-id="d4130-142">Wenn Ihr Spiel für eine frühere Version von Windows10 geeignet ist, können Sie den Vorabstart zum Beenden der Anwendung verwenden:</span><span class="sxs-lookup"><span data-stu-id="d4130-142">If your game targets an earlier version of Windows 10, you can handle the prelaunch condition to exit the application:</span></span>

```cppwinrt
void ViewProvider::OnActivated(CoreApplicationView const& /* appView */, Windows::ApplicationModel::Activation::IActivatedEventArgs const& args)
{
    if (args.Kind() == Windows::ApplicationModel::Activation::ActivationKind::Launch)
    {
        auto launchArgs{ args.as<Windows::ApplicationModel::Activation::LaunchActivatedEventArgs>()};
        if (launchArgs.PrelaunchActivated())
        {
            // Opt-out of Prelaunch.
            CoreApplication::Exit();
        }
    }
}

void ViewProvider::Initialize(CoreApplicationView const & appView)
{
    appView.Activated({ this, &App::OnActivated });
}
```

```cpp
void ViewProvider::OnActivated(CoreApplicationView^ appView,IActivatedEventArgs^ args)
{
    if (args->Kind == ActivationKind::Launch)
    {
        auto launchArgs = static_cast<LaunchActivatedEventArgs^>(args);
        if (launchArgs->PrelaunchActivated)
        {
            // Opt-out of Prelaunch
            CoreApplication::Exit();
            return;
        }
    }
}
```

## <a name="winjs-app-guidance"></a><span data-ttu-id="d4130-143">WinJS-App-Leitfaden</span><span class="sxs-lookup"><span data-stu-id="d4130-143">WinJS app guidance</span></span>

<span data-ttu-id="d4130-144">Wenn Ihre WinJS-App für eine frühere Version von Windows10 geeignet ist, können Sie den Vorabstart im [onactivated](https://msdn.microsoft.com/library/windows/apps/br212679.aspx)-Handler behandeln:</span><span class="sxs-lookup"><span data-stu-id="d4130-144">If your WinJS app targets an earlier version of Windows 10, you can handle the prelaunch condition in your [onactivated](https://msdn.microsoft.com/library/windows/apps/br212679.aspx) handler:</span></span>

```javascript
    app.onactivated = function (args) {
        if (!args.detail.prelaunchActivated) {
            // TODO: This is not a prelaunch activation. Perform operations which
            // assume that the user explicitly launched the app such as updating
            // the online presence of the user on a social network, updating a
            // what's new feed, etc.
        }
    }
```

## <a name="general-guidance"></a><span data-ttu-id="d4130-145">Allgemeiner Leitfaden</span><span class="sxs-lookup"><span data-stu-id="d4130-145">General Guidance</span></span>

-   <span data-ttu-id="d4130-146">Apps sollten während des Vorabstarts keine Vorgänge mit langer Ausführungsdauer ausführen, da die App beendet wird, wenn sie nicht schnell angehalten werden kann.</span><span class="sxs-lookup"><span data-stu-id="d4130-146">Apps should not perform long running operations during prelaunch because the app will terminate if it can't be suspended quickly.</span></span>
-   <span data-ttu-id="d4130-147">Apps sollten keine Audiowiedergabe aus [**Application.OnLaunched**](https://msdn.microsoft.com/library/windows/apps/br242335) initiieren, wenn die App vorab gestartet wird, da die App nicht angezeigt wird und daher nicht offensichtlich ist, warum eine Audiowiedergabe stattfindet.</span><span class="sxs-lookup"><span data-stu-id="d4130-147">Apps should not initiate audio playback from [**Application.OnLaunched**](https://msdn.microsoft.com/library/windows/apps/br242335) when the app is prelaunched because the app won't be visible and it won't be apparent why there is audio playing.</span></span>
-   <span data-ttu-id="d4130-148">Apps sollten während des Starts keine Vorgänge ausführen, die voraussetzen, dass die App für den Benutzer sichtbar ist, oder davon ausgehen, dass die App explizit vom Benutzer gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="d4130-148">Apps should not perform any operations during launch which assume that the app is visible to the user, or assume that the app was explicitly launched by the user.</span></span> <span data-ttu-id="d4130-149">Da eine App jetzt ohne explizite Benutzeraktion im Hintergrund gestartet werden kann, sollten Entwickler die Auswirkungen auf den Datenschutz, die Benutzerfreundlichkeit und Leistung berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="d4130-149">Because an app can now be launched in the background without explicit user action, developers should consider the privacy, user experience and performance implications.</span></span>
    -   <span data-ttu-id="d4130-150">Beispielsweise wird der Datenschutz beeinträchtigt, wenn eine soziale App den Benutzerstatus in „Online“ ändert.</span><span class="sxs-lookup"><span data-stu-id="d4130-150">An example privacy consideration is when a social app should change the user state to online.</span></span> <span data-ttu-id="d4130-151">Die App sollte warten, bis der Benutzer zur App wechselt, anstatt den Status beim Vorabstart der App zu ändern.</span><span class="sxs-lookup"><span data-stu-id="d4130-151">It should wait until the user switches to the app instead of changing the status when the app is prelaunched.</span></span>
    -   <span data-ttu-id="d4130-152">Ein Negativbeispiel für die Benutzerfreundlichkeit bietet eine App, z.B. ein Spiel, die beim Start eine Einführungssequenz präsentiert. Diese Einführungssequenz sollte verzögert werden, bis der Benutzer zur App wechselt.</span><span class="sxs-lookup"><span data-stu-id="d4130-152">An example user experience consideration is that if you have an app, such as a game, that displays an introductory sequence when it is launched, you might delay the introductory sequence until the user switches to the app.</span></span>
    -   <span data-ttu-id="d4130-153">Hier ein Beispiel für eine Leistungsbeeinträchtigung: Um die aktuelle Wetterlage abzurufen, sollte gewartet werden, bis der Benutzer zur App wechselt. Die Infos sollten nicht beim Vorabstart der App geladen werden, weil sie erneut geladen werden müssen, wenn die App sichtbar wird, um sicherzustellen, dass die Informationen aktuell sind.</span><span class="sxs-lookup"><span data-stu-id="d4130-153">An example performance implication is that you might wait until the user switches to the app to retrieve the current weather information instead of loading it when the app is prelaunched and then need to load it again when the app becomes visible to ensure that the information is current.</span></span>
-   <span data-ttu-id="d4130-154">Wenn die Live-Kachel Ihrer App beim Start gelöscht wird, stellen Sie diese Aktion bis zum VisibilityChanged-Ereignis zurück.</span><span class="sxs-lookup"><span data-stu-id="d4130-154">If your app clears its Live Tile when launched, defer doing this until the visibility changed event.</span></span>
-   <span data-ttu-id="d4130-155">Die Telemetrie für Ihre App sollte zwischen normalen Kachelaktivierungen und Vorabstartaktivierungen unterscheiden, damit eventuell auftretende Probleme leichter zu identifizieren sind.</span><span class="sxs-lookup"><span data-stu-id="d4130-155">Telemetry for your app should distinguish between normal tile activations and prelaunch activations to make it easier to narrow down the scenario if problems occur.</span></span>
-   <span data-ttu-id="d4130-156">Wenn Sie Microsoft Visual Studio2015 Update 1 und Windows 10, Version 1511, haben Sie können simulieren Vorabstart Ihrer App in Visual Studio2015 mit der Option **Debuggen** &gt; **Andere Debugziele** &gt; **universelle Windows-App Debuggen Vorabstart**.</span><span class="sxs-lookup"><span data-stu-id="d4130-156">If you have Microsoft Visual Studio2015 Update 1, and Windows10, Version 1511, you can simulate prelaunch for App your app in Visual Studio2015 by choosing **Debug** &gt; **Other Debug Targets** &gt; **Debug Windows Universal App PreLaunch**.</span></span>

## <a name="related-topics"></a><span data-ttu-id="d4130-157">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="d4130-157">Related topics</span></span>

* [<span data-ttu-id="d4130-158">App-Lebenszyklus</span><span class="sxs-lookup"><span data-stu-id="d4130-158">App lifecycle</span></span>](app-lifecycle.md)
* [<span data-ttu-id="d4130-159">CoreApplication.EnablePrelaunch</span><span class="sxs-lookup"><span data-stu-id="d4130-159">CoreApplication.EnablePrelaunch</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.coreapplication.enableprelaunch.aspx)
