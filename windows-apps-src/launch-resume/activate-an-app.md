---
author: TylerMSFT
title: Behandeln der App-Aktivierung
description: Erfahren Sie, wie Sie die App-Aktivierung durch Überschreiben der OnLaunched-Methode behandeln.
ms.assetid: DA9A6A43-F09D-4512-A2AB-9B6132431007
ms.author: twhitney
ms.date: 07/02/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
dev_langs:
- csharp
- cppwinrt
- cpp
- vb
ms.openlocfilehash: 4d69680df1684da756219c180bbe6d47263801b9
ms.sourcegitcommit: e38b334edb82bf2b1474ba686990f4299b8f59c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6847268"
---
# <a name="handle-app-activation"></a><span data-ttu-id="e0668-104">Behandeln der App-Aktivierung</span><span class="sxs-lookup"><span data-stu-id="e0668-104">Handle app activation</span></span>

<span data-ttu-id="e0668-105">Hier erfahren Sie, wie Sie app-Aktivierung durch Überschreiben der [**Application.OnLaunched**](/uwp/api/windows.ui.xaml.application.onlaunched) -Methode behandeln.</span><span class="sxs-lookup"><span data-stu-id="e0668-105">Learn how to handle app activation by overriding the [**Application.OnLaunched**](/uwp/api/windows.ui.xaml.application.onlaunched) method.</span></span>

## <a name="override-the-launch-handler"></a><span data-ttu-id="e0668-106">Überschreiben des Starthandlers</span><span class="sxs-lookup"><span data-stu-id="e0668-106">Override the launch handler</span></span>

<span data-ttu-id="e0668-107">Wenn eine app, aus irgendeinem Grund aktiviert wird, sendet das System das [**CoreApplicationView.Activated**](/uwp/api/windows.applicationmodel.core.coreapplicationview.activated) -Ereignis.</span><span class="sxs-lookup"><span data-stu-id="e0668-107">When an app is activated, for any reason, the system sends the [**CoreApplicationView.Activated**](/uwp/api/windows.applicationmodel.core.coreapplicationview.activated) event.</span></span> <span data-ttu-id="e0668-108">Eine Liste der Aktivierungstypen finden Sie in der [**ActivationKind**](https://msdn.microsoft.com/library/windows/apps/br224693)-Enumeration.</span><span class="sxs-lookup"><span data-stu-id="e0668-108">For a list of activation types, see the [**ActivationKind**](https://msdn.microsoft.com/library/windows/apps/br224693) enumeration.</span></span>

<span data-ttu-id="e0668-109">Die [**Windows.UI.Xaml.Application**](https://msdn.microsoft.com/library/windows/apps/br242324)-Klasse definiert Methoden, die außer Kraft gesetzt werden können, um die verschiedenen Aktivierungstypen zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="e0668-109">The [**Windows.UI.Xaml.Application**](https://msdn.microsoft.com/library/windows/apps/br242324) class defines methods you can override to handle the various activation types.</span></span> <span data-ttu-id="e0668-110">Verschiedene Aktivierungstypen verfügen über eine spezifische Methode, die außer Kraft gesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="e0668-110">Several of the activation types have a specific method that you can override.</span></span> <span data-ttu-id="e0668-111">Setzen Sie für die übrigen Aktivierungstypen die [**OnActivated**](https://msdn.microsoft.com/library/windows/apps/br242330)-Methode außer Kraft.</span><span class="sxs-lookup"><span data-stu-id="e0668-111">For the other activation types, override the [**OnActivated**](https://msdn.microsoft.com/library/windows/apps/br242330) method.</span></span>

<span data-ttu-id="e0668-112">Definieren Sie die Klasse für Ihre Anwendung.</span><span class="sxs-lookup"><span data-stu-id="e0668-112">Define the class for your application.</span></span>

```xml
<Application
    x:Class="AppName.App"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
```

<span data-ttu-id="e0668-113">Überschreiben Sie die [**OnLaunched**](https://msdn.microsoft.com/library/windows/apps/br242335)-Methode.</span><span class="sxs-lookup"><span data-stu-id="e0668-113">Override the [**OnLaunched**](https://msdn.microsoft.com/library/windows/apps/br242335) method.</span></span> <span data-ttu-id="e0668-114">Diese Methode wird immer dann aufgerufen, wenn der Benutzer die App startet.</span><span class="sxs-lookup"><span data-stu-id="e0668-114">This method is called whenever the user launches the app.</span></span> <span data-ttu-id="e0668-115">Der [**LaunchActivatedEventArgs**](https://msdn.microsoft.com/library/windows/apps/br224731)-Parameter enthält den vorherigen Status der App sowie die Aktivierungsargumente.</span><span class="sxs-lookup"><span data-stu-id="e0668-115">The [**LaunchActivatedEventArgs**](https://msdn.microsoft.com/library/windows/apps/br224731) parameter contains the previous state of your app and the activation arguments.</span></span>

> [!NOTE]
> <span data-ttu-id="e0668-116">Unter Windows nicht das Starten einer angehaltenen app über die startkachel oder app-Liste diese Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="e0668-116">On Windows, launching a suspended app from Start tile or app list doesn't call this method.</span></span>

```csharp
using System;
using Windows.ApplicationModel.Activation;
using Windows.UI.Xaml;

namespace AppName
{
   public partial class App
   {
      async protected override void OnLaunched(LaunchActivatedEventArgs args)
      {
         EnsurePageCreatedAndActivate();
      }

      // Creates the MainPage if it isn't already created.  Also activates
      // the window so it takes foreground and input focus.
      private MainPage EnsurePageCreatedAndActivate()
      {
         if (Window.Current.Content == null)
         {
             Window.Current.Content = new MainPage();
         }

         Window.Current.Activate();
         return Window.Current.Content as MainPage;
      }
   }
}
```

```vb
Class App
   Protected Overrides Sub OnLaunched(args As LaunchActivatedEventArgs)
      Window.Current.Content = New MainPage()
      Window.Current.Activate()
   End Sub
End Class
```

```cppwinrt
...
#include "MainPage.h"
#include "winrt/Windows.ApplicationModel.Activation.h"
#include "winrt/Windows.UI.Xaml.h"
#include "winrt/Windows.UI.Xaml.Controls.h"
...
using namespace winrt;
using namespace Windows::ApplicationModel::Activation;
using namespace Windows::UI::Xaml;
using namespace Windows::UI::Xaml::Controls;

struct App : AppT<App>
{
    App();

    /// <summary>
    /// Invoked when the application is launched normally by the end user.  Other entry points
    /// will be used such as when the application is launched to open a specific file.
    /// </summary>
    /// <param name="e">Details about the launch request and process.</param>
    void OnLaunched(LaunchActivatedEventArgs const& e)
    {
        Frame rootFrame{ nullptr };
        auto content = Window::Current().Content();
        if (content)
        {
            rootFrame = content.try_as<Frame>();
        }

        // Do not repeat app initialization when the Window already has content,
        // just ensure that the window is active
        if (rootFrame == nullptr)
        {
            // Create a Frame to act as the navigation context and associate it with
            // a SuspensionManager key
            rootFrame = Frame();

            rootFrame.NavigationFailed({ this, &App::OnNavigationFailed });

            if (e.PreviousExecutionState() == ApplicationExecutionState::Terminated)
            {
                // Restore the saved session state only when appropriate, scheduling the
                // final launch steps after the restore is complete
            }

            if (e.PrelaunchActivated() == false)
            {
                if (rootFrame.Content() == nullptr)
                {
                    // When the navigation stack isn't restored navigate to the first page,
                    // configuring the new page by passing required information as a navigation
                    // parameter
                    rootFrame.Navigate(xaml_typename<BlankApp1::MainPage>(), box_value(e.Arguments()));
                }
                // Place the frame in the current Window
                Window::Current().Content(rootFrame);
                // Ensure the current window is active
                Window::Current().Activate();
            }
        }
        else
        {
            if (e.PrelaunchActivated() == false)
            {
                if (rootFrame.Content() == nullptr)
                {
                    // When the navigation stack isn't restored navigate to the first page,
                    // configuring the new page by passing required information as a navigation
                    // parameter
                    rootFrame.Navigate(xaml_typename<BlankApp1::MainPage>(), box_value(e.Arguments()));
                }
                // Ensure the current window is active
                Window::Current().Activate();
            }
        }
    }
};
```

```cpp
using namespace Windows::ApplicationModel::Activation;
using namespace Windows::Foundation;
using namespace Windows::UI::Xaml;
using namespace AppName;
void App::OnLaunched(LaunchActivatedEventArgs^ args)
{
   EnsurePageCreatedAndActivate();
}

// Creates the MainPage if it isn't already created.  Also activates
// the window so it takes foreground and input focus.
void App::EnsurePageCreatedAndActivate()
{
    if (_mainPage == nullptr)
    {
        // Save the MainPage for use if we get activated later
        _mainPage = ref new MainPage();
    }
    Window::Current->Content = _mainPage;
    Window::Current->Activate();
}
```

## <a name="restore-application-data-if-app-was-suspended-then-terminated"></a><span data-ttu-id="e0668-117">Wiederherstellen von App-Daten, wenn die App angehalten und dann beendet wurde</span><span class="sxs-lookup"><span data-stu-id="e0668-117">Restore application data if app was suspended then terminated</span></span>

<span data-ttu-id="e0668-118">Wenn der Benutzer zur beendeten App wechselt, sendet das System das [**Activated**](https://msdn.microsoft.com/library/windows/apps/br225018)-Ereignis, wobei [**Kind**](https://msdn.microsoft.com/library/windows/apps/br224728) auf **Launch** und [**PreviousExecutionState**](https://msdn.microsoft.com/library/windows/apps/br224729) auf **Terminated** oder **ClosedByUser** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="e0668-118">When the user switches to your terminated app, the system sends the [**Activated**](https://msdn.microsoft.com/library/windows/apps/br225018) event, with [**Kind**](https://msdn.microsoft.com/library/windows/apps/br224728) set to **Launch** and [**PreviousExecutionState**](https://msdn.microsoft.com/library/windows/apps/br224729) set to **Terminated** or **ClosedByUser**.</span></span> <span data-ttu-id="e0668-119">Von der App werden die gespeicherten Anwendungsdaten geladen, und der angezeigte Inhalt wird aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="e0668-119">The app should load its saved application data and refresh its displayed content.</span></span>

```csharp
async protected override void OnLaunched(LaunchActivatedEventArgs args)
{
   if (args.PreviousExecutionState == ApplicationExecutionState.Terminated ||
       args.PreviousExecutionState == ApplicationExecutionState.ClosedByUser)
   {
      // TODO: Populate the UI with the previously saved application data
   }
   else
   {
      // TODO: Populate the UI with defaults
   }

   EnsurePageCreatedAndActivate();
}
```

```vb
Protected Overrides Sub OnLaunched(args As Windows.ApplicationModel.Activation.LaunchActivatedEventArgs)
   Dim restoreState As Boolean = False

   Select Case args.PreviousExecutionState
      Case ApplicationExecutionState.Terminated
         ' TODO: Populate the UI with the previously saved application data
         restoreState = True
      Case ApplicationExecutionState.ClosedByUser
         ' TODO: Populate the UI with the previously saved application data
         restoreState = True
      Case Else
         ' TODO: Populate the UI with defaults
   End Select

   Window.Current.Content = New MainPage(restoreState)
   Window.Current.Activate()
End Sub
```

```cppwinrt
void App::OnLaunched(Windows::ApplicationModel::Activation::LaunchActivatedEventArgs const& e)
{
    if (e.PreviousExecutionState() == ApplicationExecutionState::Terminated ||
        e.PreviousExecutionState() == ApplicationExecutionState::ClosedByUser)
    {
        // Populate the UI with the previously saved application data.
    }
    else
    {
        // Populate the UI with defaults.
    }
    ...
}
```

```cpp
void App::OnLaunched(Windows::ApplicationModel::Activation::LaunchActivatedEventArgs^ args)
{
   if (args->PreviousExecutionState == ApplicationExecutionState::Terminated ||
       args->PreviousExecutionState == ApplicationExecutionState::ClosedByUser)
   {
      // TODO: Populate the UI with the previously saved application data
   }
   else
   {
      // TODO: Populate the UI with defaults
   }

   EnsurePageCreatedAndActivate();
}
```

<span data-ttu-id="e0668-120">Wenn der Wert von [**PreviousExecutionState**](https://msdn.microsoft.com/library/windows/apps/br224729) gleich **NotRunning** ist, konnten die Anwendungsdaten von der App nicht erfolgreich gespeichert werden. Die App muss in diesem Fall neu gestartet werden, als ob sie erstmalig gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="e0668-120">If the value of [**PreviousExecutionState**](https://msdn.microsoft.com/library/windows/apps/br224729) is **NotRunning**, the app failed to save its application data successfully and the app should start over as if it were being initially launched.</span></span>

## <a name="remarks"></a><span data-ttu-id="e0668-121">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="e0668-121">Remarks</span></span>

> [!NOTE]
> <span data-ttu-id="e0668-122">Apps können die Initialisierung überspringen, wenn für das aktuelle Fenster bereits Inhalte festgelegt wurden.</span><span class="sxs-lookup"><span data-stu-id="e0668-122">Apps can skip initialization if there is already content set on the current window.</span></span> <span data-ttu-id="e0668-123">Sie können überprüfen, dass die [**LaunchActivatedEventArgs.TileId**](https://msdn.microsoft.com/library/windows/apps/br224736) -Eigenschaft, um zu ermitteln, ob die app über eine primäre oder sekundäre Kachel gestartet wurde und, basierend auf dieser Information, entscheiden, ob ein neuer darstellen oder Fortsetzen der app-Erfahrung werden soll.</span><span class="sxs-lookup"><span data-stu-id="e0668-123">You can check the [**LaunchActivatedEventArgs.TileId**](https://msdn.microsoft.com/library/windows/apps/br224736) property to determine whether the app was launched from a primary or a secondary tile and, based on that information, decide whether you should present a fresh or resume app experience.</span></span>

## <a name="important-apis"></a><span data-ttu-id="e0668-124">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="e0668-124">Important APIs</span></span>
* [<span data-ttu-id="e0668-125">Windows.ApplicationModel.Activation</span><span class="sxs-lookup"><span data-stu-id="e0668-125">Windows.ApplicationModel.Activation</span></span>](https://msdn.microsoft.com/library/windows/apps/br224766)
* [<span data-ttu-id="e0668-126">Windows.UI.Xaml.Application</span><span class="sxs-lookup"><span data-stu-id="e0668-126">Windows.UI.Xaml.Application</span></span>](https://msdn.microsoft.com/library/windows/apps/br242324)

## <a name="related-topics"></a><span data-ttu-id="e0668-127">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="e0668-127">Related topics</span></span>
* [<span data-ttu-id="e0668-128">Behandeln des Anhaltens von Apps</span><span class="sxs-lookup"><span data-stu-id="e0668-128">Handle app suspend</span></span>](suspend-an-app.md)
* [<span data-ttu-id="e0668-129">Behandeln der App-Fortsetzung</span><span class="sxs-lookup"><span data-stu-id="e0668-129">Handle app resume</span></span>](resume-an-app.md)
* [<span data-ttu-id="e0668-130">Richtlinien für das Anhalten und Fortsetzen von Apps</span><span class="sxs-lookup"><span data-stu-id="e0668-130">Guidelines for app suspend and resume</span></span>](https://msdn.microsoft.com/library/windows/apps/hh465088)
* [<span data-ttu-id="e0668-131">App-Lebenszyklus</span><span class="sxs-lookup"><span data-stu-id="e0668-131">App lifecycle</span></span>](app-lifecycle.md)
