---
author: joannaleecy
title: Definieren des UWP-App-Frameworks für das Spiel
description: Wenn Sie Code für ein UWP-Spiel mit DirectX erstellen, müssen Sie zunächst das Framework erstellen, das die Interaktion der Spielobjekte mit Windows ermöglicht.
ms.assetid: 7beac1eb-ba3d-e15c-44a1-da2f5a79bb3b
ms.author: joanlee
ms.date: 10/24/2017
ms.topic: article
keywords: Windows 10, UWP, Spiele, directx
ms.localizationpriority: medium
ms.openlocfilehash: 3444c71b4e4c610be0b7d92ac6d761340c5dd5c2
ms.sourcegitcommit: f2c9a050a9137a473f28b613968d5782866142c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6253058"
---
#  <a name="define-the-uwp-app-framework"></a><span data-ttu-id="7e2a4-104">Definieren des UWP-App-Frameworks</span><span class="sxs-lookup"><span data-stu-id="7e2a4-104">Define the UWP app framework</span></span>

<span data-ttu-id="7e2a4-105">Erstellen Sie ein Framework, um Ihre Spielobjekte mit Windows interagieren zu lassen, einschließlich der Windows-Runtime Eigenschaften, die Behandlung von Anhalte-/Fortsetzungsereignissen, Änderungen des Fensterfokus und Andocken.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-105">Build a framework to let your game object interact with Windows, including Windows Runtime properties like suspend-resume event handling, changes in window focus, and snapping.</span></span>

<span data-ttu-id="7e2a4-106">Sie müssen zuerst einen Ansichtsanbieter abrufen, mit dem das App-Singleton (also das Windows-Runtime-Objekt, das eine Instanz Ihrer ausgeführten App definiert) auf die benötigten Grafikressourcen zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-106">To set this framework up, first obtain a view provider so that the app singleton, which is the Windows Runtime object that defines an instance of your running app, can access the graphic resources it needs.</span></span> <span data-ttu-id="7e2a4-107">Über die Windows-Runtime ist Ihr Spiel zwar direkt mit der Grafikschnittstelle verbunden, Sie müssen aber angeben, welche Ressourcen Sie benötigen und wie diese behandelt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-107">Through Windows Runtime, your game also has a direct connection with the graphics interface, allowing you to specify the resources needed and how to handle them.</span></span>

<span data-ttu-id="7e2a4-108">Das Ansichtsanbieterobjekt implementiert die __IFrameworkView__-Schnittstelle, die aus einer Reihe von Methoden besteht, die zum Erstellen dieses Spielbeispiels konfiguriert werden müssen.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-108">The view provider object implements the __IFrameworkView__ interface, which consists of a series of methods that needs to be configured to create this game sample.</span></span>

<span data-ttu-id="7e2a4-109">Sie müssen diese fünf Methoden implementieren, die vom App-Singleton aufgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-109">You'll need to implement these five methods that the app singleton calls:</span></span>
* [__<span data-ttu-id="7e2a4-110">Initialize</span><span class="sxs-lookup"><span data-stu-id="7e2a4-110">Initialize</span></span>__](#initialize-the-view-provider)
* [__<span data-ttu-id="7e2a4-111">SetWindow</span><span class="sxs-lookup"><span data-stu-id="7e2a4-111">SetWindow</span></span>__](#configure-the-window-and-display-behavior)
* [__<span data-ttu-id="7e2a4-112">Load</span><span class="sxs-lookup"><span data-stu-id="7e2a4-112">Load</span></span>__](#load-method-of-the-view-provider)
* [__<span data-ttu-id="7e2a4-113">Run</span><span class="sxs-lookup"><span data-stu-id="7e2a4-113">Run</span></span>__](#run-method-of-the-view-provider)
* [__<span data-ttu-id="7e2a4-114">Uninitialize</span><span class="sxs-lookup"><span data-stu-id="7e2a4-114">Uninitialize</span></span>__](#uninitialize-method-of-the-view-provider)

<span data-ttu-id="7e2a4-115">Die __Initialize__-Methode wird beim Starten der App aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-115">The __Initialize__ method is called on application launch.</span></span> <span data-ttu-id="7e2a4-116">Die __SetWindow__-Methode wird nach __Initialize__ aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-116">__SetWindow__ method is called after __Initialize__.</span></span> <span data-ttu-id="7e2a4-117">Es wird dann __Load__ aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-117">And then the __Load__ method is called.</span></span> <span data-ttu-id="7e2a4-118">Wenn das Spiel fortgesetzt wird, wird die __Run__-Methode aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-118">The __Run__ method is when the game is running.</span></span> <span data-ttu-id="7e2a4-119">Wenn das Spiel beendet wird, wird die __Uninitialize__-Methode aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-119">When the game ends, the __Uninitialize__ method is called.</span></span> <span data-ttu-id="7e2a4-120">Weitere Informationen finden Sie unter [__IFrameworkView__ API-Referenz](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-120">For more info, see [__IFrameworkView__ API reference](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview).</span></span> 

>[!Note]
><span data-ttu-id="7e2a4-121">Wenn Sie den neuesten Code für dieses Beispiel noch nicht heruntergeladen haben, wechseln Sie zu [Direct3D-Spielbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Simple3DGameDX).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-121">If you haven't downloaded the latest game code for this sample, go to [Direct3D game sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Simple3DGameDX).</span></span> <span data-ttu-id="7e2a4-122">Dieses Beispiel gehört zu einer großen Sammlung von UWP-Featurebeispielen.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-122">This sample is part of a large collection of UWP feature samples.</span></span> <span data-ttu-id="7e2a4-123">Anweisungen zum Herunterladen des Beispiels finden Sie unter [Abrufen der UWP-Beispiele von GitHub](https://docs.microsoft.com/windows/uwp/get-started/get-uwp-app-samples).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-123">For instructions on how to download the sample, see [Get the UWP samples from GitHub](https://docs.microsoft.com/windows/uwp/get-started/get-uwp-app-samples).</span></span>

## <a name="objective"></a><span data-ttu-id="7e2a4-124">Ziel</span><span class="sxs-lookup"><span data-stu-id="7e2a4-124">Objective</span></span>

<span data-ttu-id="7e2a4-125">Richten Sie das Framework für ein UWP-DirectX-Spiel ein und implementieren den Zustandsautomaten, der den allgemeinen Spielablauf definiert.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-125">Set up the framework for a Universal Windows Platform (UWP) DirectX game and implement the state machine that defines the overall game flow.</span></span>

## <a name="define-the-view-provider-factory-and-view-provider-object"></a><span data-ttu-id="7e2a4-126">Die Ansichtsanbieterfactory und das Ansichtsanbieterobjekt werden definiert</span><span class="sxs-lookup"><span data-stu-id="7e2a4-126">Define the view provider factory and view provider object</span></span>

<span data-ttu-id="7e2a4-127">Sehen wir uns die __wichtigsten__ Schleifen in __App.cpp__ an.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-127">Let's examine the __main__ loop in __App.cpp__.</span></span> 

<span data-ttu-id="7e2a4-128">In diesem Schritterstellen wir eine Factory für die Ansicht (implementiert __IFrameworkViewSource__), wodurch wiederum Instanzen des Ansichtsanbieterobjekts erstellt werden (implementiert __IFrameworkView__), das die Ansicht definiert.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-128">In this step, we create a factory for the view (implements __IFrameworkViewSource__), which in turn creates instances of the view provider object (implements __IFrameworkView__) that defines the view.</span></span>

### <a name="main-method"></a><span data-ttu-id="7e2a4-129">Main-Methode</span><span class="sxs-lookup"><span data-stu-id="7e2a4-129">Main method</span></span>

<span data-ttu-id="7e2a4-130">Erstellen Sie ein neues __DirectXApplicationSource__, wenn Sie den GitHub-Beispielcode geladen haben.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-130">Create a new __DirectXApplicationSource__ if you have the GitHub sample code loaded.</span></span> <span data-ttu-id="7e2a4-131">(Verwenden Sie __Direct3DApplicationSource__ bei Verwendung der ursprünglichen DirectX-Vorlage). Hierbei handelt es sich um die Ansichtsanbieterfactory, die __IFrameworkViewSource__ implementiert.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-131">(Use __Direct3DApplicationSource__ if you're using the original DirectX template) This is the view provider factory that implements __IFrameworkViewSource__.</span></span> <span data-ttu-id="7e2a4-132">Die Ansichtsanbieterfactory-Schnittstelle __IFrameworkViewSource__ verfügt über eine einzelne Methode __CreateView__, die definiert wird.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-132">The view provider factory's __IFrameworkViewSource__ interface has a single method, __CreateView__, defined.</span></span>

<span data-ttu-id="7e2a4-133">In __CoreApplication:: Run__ wird die __CreateView__-Methode aufgerufen, indem Sie das App-Singleton an __Direct3DApplicationSource__ oder __DirectXApplicationSource__ übergeben.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-133">In __CoreApplication::Run__, the __CreateView__ method is called by the app singleton when __Direct3DApplicationSource__ or __DirectXApplicationSource__ is passed.</span></span>

<span data-ttu-id="7e2a4-134">__CreateView__ gibt einen Verweis auf eine neue Instanz des App-Objekts an, das __IFrameworkView__ implementiert, was das __App__-Klassenobjekt in diesem Beispiel ist.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-134">__CreateView__ returns a reference to a new instance of your app object that implements __IFrameworkView__, which is the __App__ class object in this sample.</span></span> <span data-ttu-id="7e2a4-135">Das __App__-Klassenobjekt ist das Ansichtsanbieterobjekt.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-135">The __App__ class object is the view provider object.</span></span>

```cpp
// The main function is only used to initialize our IFrameworkView class.
[Platform::MTAThread]
int main(Platform::Array<Platform::String^>^)
{
    auto directXApplicationSource = ref new DirectXApplicationSource();
    CoreApplication::Run(directXApplicationSource);
    return 0;
}

//--------------------------------------------------------------------------------------

IFrameworkView^ DirectXApplicationSource::CreateView()
{
    return ref new App();
}
```

## <a name="initialize-the-view-provider"></a><span data-ttu-id="7e2a4-136">Initialisieren des Ansichtsanbieter</span><span class="sxs-lookup"><span data-stu-id="7e2a4-136">Initialize the view provider</span></span>

<span data-ttu-id="7e2a4-137">Nachdem das Ansichtsanbieterobjekt erstellt wurde, ruft das App-Singleton die [**Initialize**](https://msdn.microsoft.com/library/windows/apps/hh700495)-Methode beim Starten der Anwendung auf.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-137">After the view provider object is created, the app singleton calls the [**Initialize**](https://msdn.microsoft.com/library/windows/apps/hh700495) method on application launch.</span></span> <span data-ttu-id="7e2a4-138">Daher müssen die elementaren Verhaltensweisen eines UWP-Spiels unbedingt von dieser Methode behandelt werden. Hierzu zählt beispielsweise die Behandlung der Aktivierung des Hauptfensters. Außerdem muss von der Methode sichergestellt werden, dass das Spiel eine überraschende Unterbrechung (sowie eine mögliche spätere Fortsetzung) behandeln kann.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-138">Therefore, it is crucial that this method handles the most fundamental behaviors of a UWP game, such as handling the activation of the main window and making sure that the game can handle a sudden suspend (and a possible later resume) event.</span></span>

<span data-ttu-id="7e2a4-139">Dann kann die Spiele-App eine angehaltene Nachricht behandeln (oder fortsetzen).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-139">At this point, the game app can handle a suspend (or resume) message.</span></span> <span data-ttu-id="7e2a4-140">Aber es gibt immer noch kein Fenster, und das Spiel ist noch nicht initialisiert.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-140">But there's still no window to work with and the game is uninitialized.</span></span> <span data-ttu-id="7e2a4-141">Wir haben also noch ein wenig Arbeit vor uns.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-141">There's a few more things that need to happen!</span></span>

### <a name="appinitialize-method"></a><span data-ttu-id="7e2a4-142">App::Initialize-Methode</span><span class="sxs-lookup"><span data-stu-id="7e2a4-142">App::Initialize method</span></span>

<span data-ttu-id="7e2a4-143">Bei dieser Methode können Sie verschiedene Ereignishandler für das Aktivieren, Anhalten und Fortsetzen des Spiels erstellen.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-143">In this method, create various event handlers for activating, suspending, and resuming the game.</span></span>

<span data-ttu-id="7e2a4-144">Ressourcenzugriff des Geräts zulassen</span><span class="sxs-lookup"><span data-stu-id="7e2a4-144">Get access to the device resources.</span></span> <span data-ttu-id="7e2a4-145">Die __make_shared__-Funktion dient zum Erstellen von __Shared_ptr__, wenn die Speicherressource zum ersten Mal erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-145">The __make_shared__ function is used to create a __shared_ptr__ when the memory resource is created for the first time.</span></span> <span data-ttu-id="7e2a4-146">Ein Vorteil der Verwendung von __Make_shared__ ist, dass sie ausnahmesicher ist.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-146">An advantage of using __make_shared__ is that it's exception-safe.</span></span> <span data-ttu-id="7e2a4-147">Sie verwendet auch den gleichen Aufruf, um den Arbeitsspeicher für Kontrollblock und die Ressource zuzuweisen und reduziert daher den Aufwand für die Erstellung.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-147">It also uses the same call to allocate the memory for the control block and the resource and therefore reduces the construction overhead.</span></span>

```cpp
void App::Initialize(
    CoreApplicationView^ applicationView
    )
{
    // Register event handlers for app lifecycle. This example includes Activated, so that we
    // can make the CoreWindow active and start rendering on the window.
    applicationView->Activated +=
        ref new TypedEventHandler<CoreApplicationView^, IActivatedEventArgs^>(this, &App::OnActivated);

    CoreApplication::Suspending +=
        ref new EventHandler<SuspendingEventArgs^>(this, &App::OnSuspending);

    CoreApplication::Resuming +=
        ref new EventHandler<Platform::Object^>(this, &App::OnResuming);

    // At this point we have access to the device. 
    // We can create the device-dependent resources.
    m_deviceResources = std::make_shared<DX::DeviceResources>();
}
```

## <a name="configure-the-window-and-display-behaviors"></a><span data-ttu-id="7e2a4-148">Konfigurieren Sie das Fenster und Anzeigeverhalten</span><span class="sxs-lookup"><span data-stu-id="7e2a4-148">Configure the window and display behaviors</span></span>

<span data-ttu-id="7e2a4-149">Nun sehen wir uns die Implementierung von [__SetWindow__](https://msdn.microsoft.com/library/windows/apps/hh700509) an.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-149">Now, let's look at the implementation of [__SetWindow__](https://msdn.microsoft.com/library/windows/apps/hh700509).</span></span> <span data-ttu-id="7e2a4-150">In der __SetWindow__-Methode konfigurieren Sie das Fenster und Anzeigeverhalten.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-150">In the __SetWindow__ method, you configure the window and display behaviors.</span></span>

### <a name="appsetwindow-method"></a><span data-ttu-id="7e2a4-151">App::SetWindow-Methode</span><span class="sxs-lookup"><span data-stu-id="7e2a4-151">App::SetWindow method</span></span>

<span data-ttu-id="7e2a4-152">Das App-Singleton stellt ein [__CoreWindow__](https://msdn.microsoft.com/library/windows/apps/br208225)-Objekt bereit, das das Hauptfenster des Spiels darstellt, und macht seine Ressourcen und Ereignisse für das Spiel verfügbar.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-152">The app singleton provides a [__CoreWindow__](https://msdn.microsoft.com/library/windows/apps/br208225) object that represents the game's main window, and makes its resources and events available to the game.</span></span> <span data-ttu-id="7e2a4-153">Jetzt kann das Spiel die grundlegenden Benutzeroberflächenkomponenten und Ereignisse hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-153">Now that there's a window to work with, the game can now start adding in the basic UI components and events.</span></span>

<span data-ttu-id="7e2a4-154">Erstellen Sie dann einen Zeiger mit der __CoreCursor__-Methode, die von den Bedienelemente und von der Maus- und auch von der Fingereingabesteuerung genutzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-154">Then, create a pointer using __CoreCursor__ method which can be used by both mouse and touch controls.</span></span>

<span data-ttu-id="7e2a4-155">Erstellen Sie zuletzt grundlegende Ereignisse für die Fenster, Größe, schließen und DPI-Änderungen (wenn sich das Anzeigegerät ändert).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-155">Lastly, create basic events for window resizing, closing, and DPI changes (if the display device changes).</span></span> <span data-ttu-id="7e2a4-156">Weitere Informationen zu den Ereignissen finden Sie unter [Ereignisbehandlung](tutorial-game-flow-management.md#events-handling).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-156">For more info about the events, go to [Event Handling](tutorial-game-flow-management.md#events-handling).</span></span>

```cpp
void App::SetWindow(
    CoreWindow^ window
    )
{
    // Codes added to modify the original DirectX template project
    window->PointerCursor = ref new CoreCursor(CoreCursorType::Arrow, 0);

    PointerVisualizationSettings^ visualizationSettings = PointerVisualizationSettings::GetForCurrentView();
    visualizationSettings->IsContactFeedbackEnabled = false;
    visualizationSettings->IsBarrelButtonFeedbackEnabled = false;
    // --end of codes added
    
    m_deviceResources->SetWindow(window);

    window->Activated +=
        ref new TypedEventHandler<CoreWindow^, WindowActivatedEventArgs^>(this, &App::OnWindowActivationChanged);

    window->SizeChanged +=
        ref new TypedEventHandler<CoreWindow^, WindowSizeChangedEventArgs^>(this, &App::OnWindowSizeChanged);

    window->VisibilityChanged +=
        ref new TypedEventHandler<CoreWindow^, VisibilityChangedEventArgs^>(this, &App::OnVisibilityChanged);
        
    window->Closed +=
        ref new TypedEventHandler<CoreWindow^, CoreWindowEventArgs^>(this, &App::OnWindowClosed);

    DisplayInformation^ currentDisplayInformation = DisplayInformation::GetForCurrentView();

    currentDisplayInformation->DpiChanged +=
        ref new TypedEventHandler<DisplayInformation^, Platform::Object^>(this, &App::OnDpiChanged);

    currentDisplayInformation->OrientationChanged +=
        ref new TypedEventHandler<DisplayInformation^, Object^>(this, &App::OnOrientationChanged);
    
    // Codes added to modify the original DirectX template project
    currentDisplayInformation->StereoEnabledChanged +=
        ref new TypedEventHandler<DisplayInformation^, Platform::Object^>(this, &App::OnStereoEnabledChanged);
    // --end of codes added
    
    DisplayInformation::DisplayContentsInvalidated +=
        ref new TypedEventHandler<DisplayInformation^, Platform::Object^>(this, &App::OnDisplayContentsInvalidated);
}
```

## <a name="load-method-of-the-view-provider"></a><span data-ttu-id="7e2a4-157">Die Load-Methode des Ansichtsanbieters</span><span class="sxs-lookup"><span data-stu-id="7e2a4-157">Load method of the view provider</span></span>

<span data-ttu-id="7e2a4-158">Nachdem das Hauptfenster festgelegt ist, ruft das App-Singleton die [__Load__](https://msdn.microsoft.com/library/windows/apps/hh700501)-Methode auf.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-158">After the main window is set, the app singleton calls [__Load__](https://msdn.microsoft.com/library/windows/apps/hh700501).</span></span> <span data-ttu-id="7e2a4-159">Diese Methode verwendet eine Reihe asynchroner Aufgaben, um die Spielobjekte zu erstellen, Grafikressourcen zu laden und den Zustandsautomaten des Spiels zu initialisieren.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-159">A set of asynchronous tasks is used in this method to create the game objects, load graphics resources, and initialize the game’s state machine.</span></span> <span data-ttu-id="7e2a4-160">Diese Methode eignet sich auch besser zum Vorabrufen von Spieldaten oder Ressourcen als **SetWindow** oder **Initialize**.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-160">If you want to pre-fetch game data or assets, this is a better place for it than in **SetWindow** or **Initialize**.</span></span> 

<span data-ttu-id="7e2a4-161">Da Windows zeitliche Beschränkungen auferlegen kann, bevor Ihr Spiel Eingaben verarbeitet, können Sie mithilfe des asynchronen Aufgabenmusters die __Load__-Methode schnell abschließen, damit die Verarbeitung der Eingabe beginnen kann.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-161">Because Windows imposes restrictions on the time your game can take before it must start processing input, by using the async task pattern, you need to design for the __Load__ method to complete quickly so it can start processing input.</span></span> <span data-ttu-id="7e2a4-162">Falls das Laden einige Zeit dauert (etwa aufgrund einer Vielzahl von Ressourcen), sollten Sie für Benutzer eine regelmäßig aktualisierte Statusleiste bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-162">If loading takes awhile or if there are lots of resources, provide your users with a regularly updated progress bar.</span></span> <span data-ttu-id="7e2a4-163">In der Methode treffen wir alle nötigen Vorbereitungen für den Spielstart (wie Festlegen aller Startzustände oder globalen Werte).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-163">This method is also used to do any necessary preparations before the game begins, like setting any starting states or global values.</span></span>

<span data-ttu-id="7e2a4-164">Wenn Sie mit den Konzepten der asynchronen Programmierung und Task-Parallelität nicht vertraut sind, wechseln Sie zu [asynchrone Programmierung in C++](https://docs.microsoft.com/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-164">If you are new to asynchronous programming and task parallelism concepts, go to [Asynchronous programming in C++](https://docs.microsoft.com/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps).</span></span>

### <a name="appload-method"></a><span data-ttu-id="7e2a4-165">App::Load-Methode</span><span class="sxs-lookup"><span data-stu-id="7e2a4-165">App::Load method</span></span>

<span data-ttu-id="7e2a4-166">Erstellen Sie die __GameMain__-Klasse, die Ladeaufgaben enthält.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-166">Create the __GameMain__ class that contains the loading tasks.</span></span>

```cpp
void App::Load(
    Platform::String^ entryPoint
    )
{
        if (!m_main)
    {
        m_main = std::unique_ptr<GameMain>(new GameMain(m_deviceResources));
    }
}
````

### <a name="gamemain-constructor"></a><span data-ttu-id="7e2a4-167">GameMain-Konstruktor</span><span class="sxs-lookup"><span data-stu-id="7e2a4-167">GameMain constructor</span></span>

* <span data-ttu-id="7e2a4-168">Erstellen und initialisieren Sie den Spielrenderer.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-168">Create and initialize the game renderer.</span></span> <span data-ttu-id="7e2a4-169">Weitere Informationen finden Sie unter [Rendering-Framework I: Einführung in das Rendering](tutorial--assembling-the-rendering-pipeline.md).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-169">For more information, see [Rendering framework I: Intro to rendering](tutorial--assembling-the-rendering-pipeline.md).</span></span>
* <span data-ttu-id="7e2a4-170">Erstellen Sie die Initialisierung des Simple3Dgame-Objekts.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-170">Create the initialize the Simple3Dgame object.</span></span> <span data-ttu-id="7e2a4-171">Weitere Informationen finden Sie unter [Definieren des Hauptobjekts für das Spiel](tutorial--defining-the-main-game-loop.md).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-171">For more information, see [Define the main game object](tutorial--defining-the-main-game-loop.md).</span></span>    
* <span data-ttu-id="7e2a4-172">Erstellen Sie das UI-Steuerelement und die Überlagerung von Spieledaten zum Anzeigen einer Statusleiste, während die Ressourcendateien geladen werden.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-172">Create the game UI control object and display game info overlay to show a progress bar as the resource files load.</span></span> <span data-ttu-id="7e2a4-173">Weitere Informationen finden Sie unter [Hinzufügen einer Benutzeroberfläche](tutorial--adding-a-user-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-173">For more information, see [Adding a user interface](tutorial--adding-a-user-interface.md).</span></span>
* <span data-ttu-id="7e2a4-174">Erstellen Sie den Controller, damit er die Eingaben des Controllers (Fingereingabe, Maus oder Xbox-Controller) lesen kann.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-174">Create the controller so it can read input from the controller (touch, mouse, or XBox wireless controller).</span></span> <span data-ttu-id="7e2a4-175">Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen](tutorial--adding-controls.md).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-175">For more information, see [Adding controls](tutorial--adding-controls.md).</span></span>
* <span data-ttu-id="7e2a4-176">Nach dem Initialisieren des Controllers definieren wir zwei rechteckige Bereiche in den Ecken unten links und unten rechts auf dem Bildschirm für die Bewegungs- bzw. Kamerasteuerungen.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-176">After the controller is initialized, we defined two rectangular areas in the lower-left and lower-right corners of the screen for the move and camera touch controls, respectively.</span></span> <span data-ttu-id="7e2a4-177">Der Spieler verwendet das durch den Aufruf von **SetMoveRect** definierte Rechteck links unten als virtuelles Bedienfeld, um die Kamera vor und zurück sowie seitlich zu bewegen.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-177">The player uses the lower-left rectangle, defined by the call to **SetMoveRect**, as a virtual control pad for moving the camera forward and backward, and side to side.</span></span> <span data-ttu-id="7e2a4-178">Das durch die **SetFireRect**-Methode definierte Rechteck rechts unten wird als virtuelle Taste zum Abfeuern der Munition verwendet.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-178">The lower-right rectangle, defined by the **SetFireRect** method, is used as a virtual button to fire the ammo.</span></span>
* <span data-ttu-id="7e2a4-179">Verwenden Sie __create_task__ und __create_task::then__, um das Laden von Ressourcen in zwei getrennte Phasen zu unterteilen.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-179">Use __create_task__ and __create_task::then__ to break resource loading into two separate stages.</span></span> <span data-ttu-id="7e2a4-180">Da der Zugriff auf den Direct3D11-Gerätekontext auf den Thread beschränkt ist, auf dem der Gerätekontext beim Zugriff auf das Direct3D11-Gerät erstellt wurde und die Erstellung des Objekts den Threadbeschränkungen unterliegt, bedeutet dies, dass die **CreateGameDeviceResourcesAsync**-Aufgabe in einem separaten Thread ausgeführt werden kann, von der Aufgabe zur Vervollständigung (*FinalizeCreateGameDeviceResources*), die im Originalthread ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-180">Because access to the Direct3D 11 device context is restricted to the thread the device context was created on while access to the Direct3D 11 device for object creation is free-threaded, this means that the **CreateGameDeviceResourcesAsync** task can run on a separate thread from the completion task (*FinalizeCreateGameDeviceResources*), which runs on the original thread.</span></span> <span data-ttu-id="7e2a4-181">Wir verwenden ein ähnliches Muster zum Laden von Levelressourcen mit **LoadLevelAsync** und **FinalizeLoadLevel**.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-181">We use a similar pattern for loading level resources with **LoadLevelAsync** and **FinalizeLoadLevel**.</span></span>

```cpp
GameMain::GameMain(const std::shared_ptr<DX::DeviceResources>& deviceResources) :
    m_deviceResources(deviceResources),
    m_windowClosed(false),
    m_haveFocus(false),
    m_gameInfoOverlayCommand(GameInfoOverlayCommand::None),
    m_visible(true),
    m_loadingCount(0),
    m_updateState(UpdateEngineState::WaitingForResources)
{
    m_deviceResources->RegisterDeviceNotify(this);

    m_renderer = ref new GameRenderer(m_deviceResources);
    m_game = ref new Simple3DGame();

    m_uiControl = m_renderer->GameUIControl();

    m_controller = ref new MoveLookController(CoreWindow::GetForCurrentThread());

    auto bounds = m_deviceResources->GetLogicalSize();

    m_controller->SetMoveRect(
        XMFLOAT2(0.0f, bounds.Height - GameConstants::TouchRectangleSize),
        XMFLOAT2(GameConstants::TouchRectangleSize, bounds.Height)
        );
    m_controller->SetFireRect(
        XMFLOAT2(bounds.Width - GameConstants::TouchRectangleSize, bounds.Height - GameConstants::TouchRectangleSize),
        XMFLOAT2(bounds.Width, bounds.Height)
        );

    SetGameInfoOverlay(GameInfoOverlayState::Loading);
    m_uiControl->SetAction(GameInfoOverlayCommand::None);
    m_uiControl->ShowGameInfoOverlay();

    create_task([this]()
    {
        // Asynchronously initialize the game class and load the renderer device resources.
        // By doing all this asynchronously, the game gets to its main loop more quickly
        // and in parallel all the necessary resources are loaded on other threads.
        m_game->Initialize(m_controller, m_renderer);

        return m_renderer->CreateGameDeviceResourcesAsync(m_game);

    }).then([this]()
    {
        // The finalize code needs to run in the same thread context
        // as the m_renderer object was created because the D3D device context
        // can ONLY be accessed on a single thread.
        m_renderer->FinalizeCreateGameDeviceResources();

        InitializeGameState();

        if (m_updateState == UpdateEngineState::WaitingForResources)
        {
            // In the middle of a game so spin up the async task to load the level.
            return m_game->LoadLevelAsync().then([this]()
            {
                // The m_game object may need to deal with D3D device context work so
                // again the finalize code needs to run in the same thread
                // context as the m_renderer object was created because the D3D
                // device context can ONLY be accessed on a single thread.
                m_game->FinalizeLoadLevel();
                m_game->SetCurrentLevelToSavedState();
                m_updateState = UpdateEngineState::ResourcesLoaded;

            }, task_continuation_context::use_current());
        }
        else
        {
            // The game is not in the middle of a level so there aren't any level
            // resources to load.  Creating a no-op task so that in both cases
            // the same continuation logic is used.
            return create_task([]()
            {
            });
        }
    }, task_continuation_context::use_current()).then([this]()
    {
        // Since Game loading is an async task, the app visual state
        // may be too small or not have focus.  Put the state machine
        // into the correct state to reflect these cases.

        if (m_deviceResources->GetLogicalSize().Width < GameConstants::MinPlayableWidth)
        {
            m_updateStateNext = m_updateState;
            m_updateState = UpdateEngineState::TooSmall;
            m_controller->Active(false);
            m_uiControl->HideGameInfoOverlay();
            m_uiControl->ShowTooSmall();
            m_renderNeeded = true;
        }
        else if (!m_haveFocus)
        {
            m_updateStateNext = m_updateState;
            m_updateState = UpdateEngineState::Deactivated;
            m_controller->Active(false);
            m_uiControl->SetAction(GameInfoOverlayCommand::None);
            m_renderNeeded = true;
        }
    }, task_continuation_context::use_current());
}
```

## <a name="run-method-of-the-view-provider"></a><span data-ttu-id="7e2a4-182">Die Run-Methode des Ansichtsanbieters</span><span class="sxs-lookup"><span data-stu-id="7e2a4-182">Run method of the view provider</span></span>

<span data-ttu-id="7e2a4-183">Die drei zuvor beschriebenen Methoden: __Initialize__, __SetWindow__ und __Load__ haben die Vorbereitung abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-183">The earlier three methods: __Initialize__, __SetWindow__, and __Load__ have set the stage.</span></span> <span data-ttu-id="7e2a4-184">Das Spiel kann jetzt auf die **Run**-Methode weitergehen und der Spaß kann beginnen!</span><span class="sxs-lookup"><span data-stu-id="7e2a4-184">Now the game can progress to the **Run** method, starting the fun!</span></span> <span data-ttu-id="7e2a4-185">Die Ereignisse, die es für den Wechsel des Spielzustands nutzt, werden verteilt und verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-185">The events that it uses to transition between game states are dispatched and processed.</span></span> <span data-ttu-id="7e2a4-186">Die Grafik wird im Rahmen der Spielschleifendurchläufe aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-186">Graphics are updated as the game loop cycles.</span></span>

### <a name="apprun"></a><span data-ttu-id="7e2a4-187">App::Run</span><span class="sxs-lookup"><span data-stu-id="7e2a4-187">App::Run</span></span>

<span data-ttu-id="7e2a4-188">Starten Sie eine __While__-Schleife, die beendet wird, wenn der Spieler das Spielfenster schließt.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-188">Start a __while__ loop that terminates when the player closes the game window.</span></span>

<span data-ttu-id="7e2a4-189">Der Beispielcode geht im Zustandsautomaten der Spielengine in einen von zweiZuständen über:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-189">The sample code transitions to one of two states in the game engine state machine:</span></span>
    * <span data-ttu-id="7e2a4-190">__Deactivated__: Das Spielfenster wird deaktiviert (verliert also den Fokus) oder angedockt.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-190">__Deactivated__: The game window gets deactivated (loses focus) or snapped.</span></span> <span data-ttu-id="7e2a4-191">In diesem Fall hält das Spiel die Ereignisverarbeitung an und wartet auf den Fensterfokus bzw. darauf, dass das Fenster wieder abgedockt wird.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-191">When this happens, the game suspends event processing and waits for the window to focus or unsnap.</span></span>
    * <span data-ttu-id="7e2a4-192">__TooSmall__: Das Spiel aktualisiert den eigenen Zustand und rendert die Grafik für die Anzeige.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-192">__TooSmall__: The game updates its own state and renders the graphics for display.</span></span>

<span data-ttu-id="7e2a4-193">Wenn Ihr Spiel den Fokus hat, müssen Sie jedes in der Meldungswarteschlange eingehende Ereignis behandeln. Daher müssen Sie [**CoreWindowDispatch.ProcessEvents**](https://msdn.microsoft.com/library/windows/apps/br208215) mit der Option **ProcessAllIfPresent** aufrufen.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-193">When your game has focus, you must handle every event in the message queue as it arrives, and so you must call [**CoreWindowDispatch.ProcessEvents**](https://msdn.microsoft.com/library/windows/apps/br208215) with the **ProcessAllIfPresent** option.</span></span> <span data-ttu-id="7e2a4-194">Andere Optionen können zu einer verzögerten Verarbeitung von Meldungsereignissen führen. So entsteht der Eindruck, dass das Spiel nicht reagiert oder Toucheingaben nur träge umgesetzt werden.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-194">Other options can cause delays in processing message events, which can make your game feel unresponsive, or result in touch behaviors that feel sluggish and not "sticky".</span></span>

<span data-ttu-id="7e2a4-195">Wenn die App nicht sichtbar ist, angehalten oder angedockt wurde, möchten wir nicht, dass sie Meldungen ausgibt, die niemals ankommen, und dabei auch noch Ressourcen beansprucht.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-195">When the game is not visible, suspended or snapped, you don't want it to consume any resources cycling to dispatch messages that will never arrive.</span></span> <span data-ttu-id="7e2a4-196">Daher muss das Spiel **ProcessOneAndAllPending** verwenden, was eine Blockierung bis zum Eingang eines Ereignisses zur Folge hat. Dieses Ereignis wird dann zusammen mit anderen Ereignissen verarbeitet, die während der Verarbeitung des ersten Ereignisses in der Prozesswarteschlange eingehen.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-196">In this case, your game must use **ProcessOneAndAllPending**, which blocks until it gets an event, and then processes that event and any others that arrive in the process queue during the processing of the first.</span></span> <span data-ttu-id="7e2a4-197">[**ProcessEvents**](https://msdn.microsoft.com/library/windows/apps/br208215) springt nach der Verarbeitung der Warteschlange sofort wieder zurück.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-197">[**ProcessEvents**](https://msdn.microsoft.com/library/windows/apps/br208215) then immediately returns after the queue has been processed.</span></span>

```cpp
void App::Run()
{
    m_main->Run();
}

void GameMain::Run()
{
    while (!m_windowClosed)
    {
        if (m_visible)
        {
            switch (m_updateState)
            {
            case UpdateEngineState::Deactivated:
            case UpdateEngineState::TooSmall:
                if (m_updateStateNext == UpdateEngineState::WaitingForResources)
                {
                    WaitingForResourceLoading();
                    m_renderNeeded = true;
                }
                else if (m_updateStateNext == UpdateEngineState::ResourcesLoaded)
                {
                    // In the device lost case, we transition to the final waiting state
                    // and make sure the display is updated.
                    switch (m_pressResult)
                    {
                    case PressResultState::LoadGame:
                        SetGameInfoOverlay(GameInfoOverlayState::GameStats);
                        break;

                    case PressResultState::PlayLevel:
                        SetGameInfoOverlay(GameInfoOverlayState::LevelStart);
                        break;

                    case PressResultState::ContinueLevel:
                        SetGameInfoOverlay(GameInfoOverlayState::Pause);
                        break;
                    }
                    m_updateStateNext = UpdateEngineState::WaitingForPress;
                    m_uiControl->ShowGameInfoOverlay();
                    m_renderNeeded = true;
                }

                if (!m_renderNeeded)
                {
                    // The App is not currently the active window and not in a transient state so just wait for events.
                    CoreWindow::GetForCurrentThread()->Dispatcher->ProcessEvents(CoreProcessEventsOption::ProcessOneAndAllPending);
                    break;
                }
                // otherwise fall through and do normal processing to get the rendering handled.
            default:
                CoreWindow::GetForCurrentThread()->Dispatcher->ProcessEvents(CoreProcessEventsOption::ProcessAllIfPresent);
                Update();
                m_renderer->Render();
                m_deviceResources->Present();
                m_renderNeeded = false;
            }
        }
        else
        {
            CoreWindow::GetForCurrentThread()->Dispatcher->ProcessEvents(CoreProcessEventsOption::ProcessOneAndAllPending);
        }
    }
    m_game->OnSuspending();  // exiting due to window close.  Make sure to save state.
}
```

## <a name="uninitialize-method-of-the-view-provider"></a><span data-ttu-id="7e2a4-198">Die Uninitialize-Methode des Ansichtsanbieters</span><span class="sxs-lookup"><span data-stu-id="7e2a4-198">Uninitialize method of the view provider</span></span>

<span data-ttu-id="7e2a4-199">Wenn der Benutzer letztendlich die Sitzung beendet, müssen wir sie bereinigen.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-199">When the user eventually ends the game session, we need to clean up.</span></span> <span data-ttu-id="7e2a4-200">An dieser Stelle kommt die **Uninitialize**-Eigenschaft ins Spiel.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-200">This is where **Uninitialize** comes in.</span></span>

<span data-ttu-id="7e2a4-201">In Windows 10 beim Schließen des app-Fensters nicht die Beendigung des app Prozesses, aber stattdessen wird des Zustands des app-Singleton in den Speicher.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-201">In Windows10, closing the app window doesn't kill the app's process, but instead it writes the state of the app singleton to memory.</span></span> <span data-ttu-id="7e2a4-202">Sollte eine besondere Aktion wie eine spezielle Bereinigung von Ressourcen erforderlich sein, wenn das System diesen Speicher freigeben muss, platzieren Sie den Code für diese Bereinigung in dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-202">If anything special must happen when the system must reclaim this memory, including any special cleanup of resources, then put the code for that cleanup in this method.</span></span>

### <a name="app-uninitialize"></a><span data-ttu-id="7e2a4-203">App:: Uninitialize</span><span class="sxs-lookup"><span data-stu-id="7e2a4-203">App:: Uninitialize</span></span>

```cpp
void App::Uninitialize()
{
}
```

## <a name="tips"></a><span data-ttu-id="7e2a4-204">Tipps</span><span class="sxs-lookup"><span data-stu-id="7e2a4-204">Tips</span></span>

<span data-ttu-id="7e2a4-205">Erstellen Sie Ihren Startcode bei der Entwicklung Ihres eigenen Spiels mithilfe dieser Methoden.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-205">When developing your own game, design your startup code around these methods.</span></span> <span data-ttu-id="7e2a4-206">Es folgt eine Liste mit einfachen Vorschlägen für die einzelnen Methoden:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-206">Here's a simple list of basic suggestions for each method:</span></span>

-   <span data-ttu-id="7e2a4-207">Verwenden Sie **Initialize**, um Ihre Hauptklassen zuzuordnen und die grundlegenden Ereignishandler zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-207">Use **Initialize** to allocate your main classes and connect up the basic event handlers.</span></span>
-   <span data-ttu-id="7e2a4-208">Verwenden Sie **SetWindow**, um das Hauptfenster zu erstellen und fensterspezifische Ereignisse zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-208">Use **SetWindow** to create your main window and connect any window-specific events.</span></span>
-   <span data-ttu-id="7e2a4-209">Verwenden Sie **Load** für verbleibende Einrichtungsaufgaben und um das asynchrone Erstellen von Objekten und Laden von Ressourcen zu initiieren.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-209">Use **Load** to handle any remaining setup, and to initiate the async creation of objects and loading of resources.</span></span> <span data-ttu-id="7e2a4-210">Wenn temporäre Dateien oder Daten erstellt werden müssen, wie beispielsweise Assets, die im Rahmen von Prozeduren generiert werden, ist dies hier ebenfalls die richtige Stelle.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-210">If you need to create any temporary files or data, such as procedurally generated assets, do it here too.</span></span>


## <a name="next-steps"></a><span data-ttu-id="7e2a4-211">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="7e2a4-211">Next steps</span></span>

<span data-ttu-id="7e2a4-212">Dies schließt die grundlegende Struktur eines UWP-Spiels mit DirectX ab.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-212">This covers the basic structure of a UWP game with DirectX.</span></span> <span data-ttu-id="7e2a4-213">Bedenken Sie diese fünf Methoden in anderen Bereichen, da diese in anderen Abschnitten erneut aufgegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-213">Keep these five methods in mind as we'll reference them in other parts of this walkthrough.</span></span> <span data-ttu-id="7e2a4-214">Als Nächstes nehmen wir einen detaillierten Einblick in die Verwaltung der Spielzustände und der Ereignisbehandlung unter [Spielablaufverwaltung](tutorial-game-flow-management.md), damit das Spiel fortgesetzt wird.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-214">Next, we'll take an in-depth look at how to manage game states and event handling to keep the game going under [Game flow management](tutorial-game-flow-management.md).</span></span>



