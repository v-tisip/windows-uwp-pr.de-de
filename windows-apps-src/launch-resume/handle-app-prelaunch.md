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
ms.sourcegitcommit: f2c9a050a9137a473f28b613968d5782866142c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2018
ms.locfileid: "6269277"
---
# <a name="handle-app-prelaunch"></a>Behandeln des Vorabstarts von Apps

Erfahren Sie, wie Sie den Vorabstart von Apps durch außer Kraft setzen der [**OnLaunched**](https://msdn.microsoft.com/library/windows/apps/br242335)-Methode behandeln.

## <a name="introduction"></a>Einführung

Wenn verfügbaren Systemressourcen ermöglichen, die startleistung von UWP-apps auf Desktopgerät Gerätefamilie Geräte verbessern, indem Sie proaktiv Starten des Benutzers am häufigsten verwendeten apps im Hintergrund. Eine vorab gestartete App wird kurz nach dem Start in den angehaltenen Zustand versetzt. Wenn der Benutzer die App dann aufruft, wird sie fortgesetzt, indem sie vom angehaltenen Zustand in den ausgeführten Zustand versetzt wird. Dies ist schneller als ein Kaltstart der App. Der Benutzer gewinnt den Eindruck, dass die App sehr schnell startet.

Vor Windows10 waren die Vorteile des Vorabstarts nicht automatisch für Apps verfügbar. In Windows 10 Version 1511, alle universellen Windows-Plattform (UWP) apps Kandidaten für den Vorabstart eingerichtet wurden. In Windows 10, Version 1607, müssen Sie den Vorabstart aktivieren, in dem Sie [CoreApplication.EnablePrelaunch(true)](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.coreapplication.enableprelaunch.aspx) aufrufen. Ein empfohlener Bereich für diesen Aufruf ist `OnLaunched()` in der Nähe der `if (e.PrelaunchActivated == false)`-Überprüfung.

Ob eine App vorab gestartet wird, ist von den Systemressourcen abhängig. Wenn die Systemressourcen ausgelastet sind, werden Apps nicht vorab gestartet.

Für einige App-Typen muss u.U. das Startverhalten geändert werden, damit der Vorabstart reibungslos funktioniert. Beispielsweise kann eine App, die beim Start Musik wiedergibt, ein Spiel, das dem Benutzer beim Start aufwändige visuelle Elemente anzeigt, eine Messaging-App, welche während des Starts die Onlinesichtbarkeit des Benutzers ändert, erkennen, ob die App vorab gestartet wurde und das Startverhalten wie in den folgenden Abschnitten beschrieben ändern.

Die Standardvorlagen für XAML-Projekte (C#, VB, C++) und WinJS in passen den Vorabstart in Visual Studio2015 Update3 an.

## <a name="prelaunch-and-the-app-lifecycle"></a>Vorabstart und App-Lebenszyklus

Nach dem Vorabstart wechselt die App in den angehaltenen Zustand. (siehe [Behandeln des Anhaltens von Apps](suspend-an-app.md)).

## <a name="detect-and-handle-prelaunch"></a>Erkennen und Behandeln des Vorabstarts

Apps empfangen das [**LaunchActivatedEventArgs.PrelaunchActivated**](https://msdn.microsoft.com/library/windows/apps/dn263740)-Kennzeichen während der Aktivierung. Verwenden Sie dieses Flag, um Code auszuführen, der nur ausgeführt werden soll, wenn der Benutzer die app explizit startet wie in der folgenden Änderung [**Application.OnLaunched**](https://msdn.microsoft.com/library/windows/apps/br242335)dargestellt.

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

Hinweis: die `TryEnablePrelaunch()` funktionieren, oben beschrieben. Der Grund der Aufruf zu `CoreApplication.EnablePrelaunch()` ist Ressourcenauswahl Out in diese Funktion ist, da, wenn eine Methode aufgerufen wird, die JIT (Just-in-Time-Kompilierung) versucht, die gesamte Methode zu kompilieren. Wenn Ihre app auf einer Version von Windows 10 ausgeführt wird, die nicht unterstützt `CoreApplication.EnablePrelaunch()`, und klicken Sie dann die JIT schlägt fehl. Durch den Aufruf in eine Methode, die nur aufgerufen wird, wenn die app ermittelt, dass die Plattform unterstützt Zerlegung `CoreApplication.EnablePrelaunch()`, wir dieses Problem zu vermeiden.

Es gibt auch im obigen Beispiel code, dass Sie kommentieren können, wenn Ihre app Vorabstart Teilnahme während der Ausführung unter Windows 10, Version 1511 muss. In Version 1511, automatisch alle UWP-apps zugelassen wurden in Vorabstart, die möglicherweise nicht für Ihre app geeignet.

## <a name="use-the-visibilitychanged-event"></a>Verwenden des VisibilityChanged-Ereignisses

Eine durch den Vorabstart aktivierte App ist für den Benutzer nicht sichtbar. Sie wird sichtbar, wenn der Benutzer zur App wechselt. Möglicherweise sollen bestimmte Vorgänge verzögert werden, bis das Hauptfenster der App sichtbar wird. Wenn Ihre App z.B. eine Liste mit Neuigkeiten aus einem Feed anzeigt, können Sie die Liste während des [**VisibilityChanged**](https://msdn.microsoft.com/library/windows/apps/hh702458)-Ereignisses aktualisieren, anstatt eine Liste zu verwenden, die beim Vorabstart der App erstellt wurde. Denn diese kann bereits veraltet sein, wenn der Benutzer die App aktiviert. Der folgende Code behandelt das **VisibilityChanged**-Ereignis für **MainPage**:

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

## <a name="directx-games-guidance"></a>Leitfaden für DirectX-Spiele

Für DirectX-Spiele sollte der Vorabstart im Allgemeinen nicht aktiviert werden, da bei vielen DirectX-Spielen Initialisierungsvorgänge ausgeführt werden, bevor der Vorabstart erkannt wird. Ab Windows-Version 1607 (Anniversary-Edition) werden Spiele nicht standardmäßig vorab gestartet.  Wenn Sie den Vorabstart für Ihr Spiel verwenden möchten, rufen Sie [CoreApplication.EnablePrelaunch(true)](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.coreapplication.enableprelaunch.aspx) auf.

Wenn Ihr Spiel für eine frühere Version von Windows10 geeignet ist, können Sie den Vorabstart zum Beenden der Anwendung verwenden:

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

## <a name="winjs-app-guidance"></a>WinJS-App-Leitfaden

Wenn Ihre WinJS-App für eine frühere Version von Windows10 geeignet ist, können Sie den Vorabstart im [onactivated](https://msdn.microsoft.com/library/windows/apps/br212679.aspx)-Handler behandeln:

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

## <a name="general-guidance"></a>Allgemeiner Leitfaden

-   Apps sollten während des Vorabstarts keine Vorgänge mit langer Ausführungsdauer ausführen, da die App beendet wird, wenn sie nicht schnell angehalten werden kann.
-   Apps sollten keine Audiowiedergabe aus [**Application.OnLaunched**](https://msdn.microsoft.com/library/windows/apps/br242335) initiieren, wenn die App vorab gestartet wird, da die App nicht angezeigt wird und daher nicht offensichtlich ist, warum eine Audiowiedergabe stattfindet.
-   Apps sollten während des Starts keine Vorgänge ausführen, die voraussetzen, dass die App für den Benutzer sichtbar ist, oder davon ausgehen, dass die App explizit vom Benutzer gestartet wurde. Da eine App jetzt ohne explizite Benutzeraktion im Hintergrund gestartet werden kann, sollten Entwickler die Auswirkungen auf den Datenschutz, die Benutzerfreundlichkeit und Leistung berücksichtigen.
    -   Beispielsweise wird der Datenschutz beeinträchtigt, wenn eine soziale App den Benutzerstatus in „Online“ ändert. Die App sollte warten, bis der Benutzer zur App wechselt, anstatt den Status beim Vorabstart der App zu ändern.
    -   Ein Negativbeispiel für die Benutzerfreundlichkeit bietet eine App, z.B. ein Spiel, die beim Start eine Einführungssequenz präsentiert. Diese Einführungssequenz sollte verzögert werden, bis der Benutzer zur App wechselt.
    -   Hier ein Beispiel für eine Leistungsbeeinträchtigung: Um die aktuelle Wetterlage abzurufen, sollte gewartet werden, bis der Benutzer zur App wechselt. Die Infos sollten nicht beim Vorabstart der App geladen werden, weil sie erneut geladen werden müssen, wenn die App sichtbar wird, um sicherzustellen, dass die Informationen aktuell sind.
-   Wenn die Live-Kachel Ihrer App beim Start gelöscht wird, stellen Sie diese Aktion bis zum VisibilityChanged-Ereignis zurück.
-   Die Telemetrie für Ihre App sollte zwischen normalen Kachelaktivierungen und Vorabstartaktivierungen unterscheiden, damit eventuell auftretende Probleme leichter zu identifizieren sind.
-   Wenn Sie Microsoft Visual Studio2015 Update 1 und Windows 10, Version 1511, haben Sie können Vorabstart simulieren Ihrer App in Visual Studio2015 mit der Option **Debuggen** &gt; **Andere Debugziele** &gt; **universelle Windows-App Debuggen Vorabstart**.

## <a name="related-topics"></a>Verwandte Themen

* [App-Lebenszyklus](app-lifecycle.md)
* [CoreApplication.EnablePrelaunch](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.coreapplication.enableprelaunch.aspx)
