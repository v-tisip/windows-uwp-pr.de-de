---
author: mtoepke
title: Portieren der Spielschleife
description: In diesem Thema wird veranschaulicht, wie Sie ein Fenster für ein UWP-Spiel (Universelle Windows-Plattform) implementieren und die Spielschleife portieren. Außerdem wird die Erstellung eines IFrameworkView-Elements zum Steuern eines CoreWindow-Vollbilds erläutert.
ms.assetid: 070dd802-cb27-4672-12ba-a7f036ff495c
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP, Spiele, portieren, Spielschleife, Direct3D9, DirectX11
ms.localizationpriority: medium
ms.openlocfilehash: 4db2ed74144ead22643ece17a7496b6267f7e6b8
ms.sourcegitcommit: 71e8eae5c077a7740e5606298951bb78fc42b22c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6667500"
---
# <a name="port-the-game-loop"></a><span data-ttu-id="4e180-104">Portieren der Spielschleife</span><span class="sxs-lookup"><span data-stu-id="4e180-104">Port the game loop</span></span>



**<span data-ttu-id="4e180-105">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="4e180-105">Summary</span></span>**

-   [<span data-ttu-id="4e180-106">Teil 1: Initialisieren von Direct3D 11</span><span class="sxs-lookup"><span data-stu-id="4e180-106">Part 1: Initialize Direct3D 11</span></span>](simple-port-from-direct3d-9-to-11-1-part-1--initializing-direct3d.md)
-   [<span data-ttu-id="4e180-107">Teil 2: Konvertieren des Renderingframeworks</span><span class="sxs-lookup"><span data-stu-id="4e180-107">Part 2: Convert the rendering framework</span></span>](simple-port-from-direct3d-9-to-11-1-part-2--rendering.md)
-   <span data-ttu-id="4e180-108">Teil 3: Portieren der Spielschleife</span><span class="sxs-lookup"><span data-stu-id="4e180-108">Part 3: Port the game loop</span></span>


<span data-ttu-id="4e180-109">In diesem Thema wird veranschaulicht, wie Sie ein Fenster für ein UWP-Spiel (Universelle Windows-Plattform) implementieren und die Spielschleife übertragen. Außerdem wird die Erstellung eines [**IFrameworkView**](https://msdn.microsoft.com/library/windows/apps/hh700478)-Elements zum Steuern eines [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225)-Vollbilds erläutert.</span><span class="sxs-lookup"><span data-stu-id="4e180-109">Shows how to implement a window for a Universal Windows Platform (UWP) game and how to bring over the game loop, including how to build an [**IFrameworkView**](https://msdn.microsoft.com/library/windows/apps/hh700478) to control a full-screen [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225).</span></span> <span data-ttu-id="4e180-110">Teil 3 der exemplarischen Vorgehensweise [Portieren einer einfachen Direct3D 9-App zu DirectX 11 und UWP](walkthrough--simple-port-from-direct3d-9-to-11-1.md) .</span><span class="sxs-lookup"><span data-stu-id="4e180-110">Part 3 of the [Port a simple Direct3D 9 app to DirectX 11 and UWP](walkthrough--simple-port-from-direct3d-9-to-11-1.md) walkthrough.</span></span>

## <a name="create-a-window"></a><span data-ttu-id="4e180-111">Erstellen eines Fensters</span><span class="sxs-lookup"><span data-stu-id="4e180-111">Create a window</span></span>


<span data-ttu-id="4e180-112">Zum Einrichten eines Desktopfensters mit einem Direct3D 9-Viewport musste das herkömmliche Fensterframework für Desktop-Apps implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="4e180-112">To set up a desktop window with a Direct3D 9 viewport, we had to implement the traditional windowing framework for desktop apps.</span></span> <span data-ttu-id="4e180-113">Es musste ein HWND-Element erstellt, die Fenstergröße festgelegt, ein Rückruf zur Fensterverarbeitung eingerichtet, die Sichtbarkeit hergestellt werden usw.</span><span class="sxs-lookup"><span data-stu-id="4e180-113">We had to create an HWND, set the window size, provide a window processing callback, make it visible, and so on.</span></span>

<span data-ttu-id="4e180-114">Dagegen verfügt die UWP-Umgebung über ein deutlich einfacheres System.</span><span class="sxs-lookup"><span data-stu-id="4e180-114">The UWP environment has a much simpler system.</span></span> <span data-ttu-id="4e180-115">Anstatt ein herkömmliches Fenster einzurichten, wird von einem Microsoft Store-Spiel, für das DirectX verwendet wird, das [**IFrameworkView**](https://msdn.microsoft.com/library/windows/apps/hh700478)-Element implementiert.</span><span class="sxs-lookup"><span data-stu-id="4e180-115">Instead of setting up a traditional window, a Microsoft Store game using DirectX implements [**IFrameworkView**](https://msdn.microsoft.com/library/windows/apps/hh700478).</span></span> <span data-ttu-id="4e180-116">Diese Schnittstelle ist für DirectX-Apps und -Spiele vorhanden, um die direkte Ausführung in einem [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225) innerhalb des App-Containers zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="4e180-116">This interface exists for DirectX apps and games to run directly in a [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225) inside the app container.</span></span>

> <span data-ttu-id="4e180-117">**Hinweis:**  Windows ist eine verwaltete Zeiger auf Ressourcen wie das Quellobjekt für die Anwendung und das [**corewindow-Element**](https://msdn.microsoft.com/library/windows/apps/br208225).</span><span class="sxs-lookup"><span data-stu-id="4e180-117">**Note** Windows supplies managed pointers to resources such as the source application object and the [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225).</span></span> <span data-ttu-id="4e180-118">Finden Sie unter [**Handle to Object Operator (^)**]https://msdn.microsoft.com/library/windows/apps/yk97tc08.aspx.</span><span class="sxs-lookup"><span data-stu-id="4e180-118">See [**Handle to Object Operator (^)**]https://msdn.microsoft.com/library/windows/apps/yk97tc08.aspx.</span></span>

 

<span data-ttu-id="4e180-119">Ihre main-Klasse muss von [**IFrameworkView**](https://msdn.microsoft.com/library/windows/apps/hh700478) erben und die fünf **IFrameworkView**-Methoden implementieren: [**Initialize**](https://msdn.microsoft.com/library/windows/apps/hh700495), [**SetWindow**](https://msdn.microsoft.com/library/windows/apps/hh700509), [**Load**](https://msdn.microsoft.com/library/windows/apps/hh700501), [**Run**](https://msdn.microsoft.com/library/windows/apps/hh700505) und [**Uninitialize**](https://msdn.microsoft.com/library/windows/apps/hh700523).</span><span class="sxs-lookup"><span data-stu-id="4e180-119">Your "main" class needs to inherit from [**IFrameworkView**](https://msdn.microsoft.com/library/windows/apps/hh700478) and implement the five **IFrameworkView** methods: [**Initialize**](https://msdn.microsoft.com/library/windows/apps/hh700495), [**SetWindow**](https://msdn.microsoft.com/library/windows/apps/hh700509), [**Load**](https://msdn.microsoft.com/library/windows/apps/hh700501), [**Run**](https://msdn.microsoft.com/library/windows/apps/hh700505), and [**Uninitialize**](https://msdn.microsoft.com/library/windows/apps/hh700523).</span></span> <span data-ttu-id="4e180-120">Zusätzlich zur Erstellung des **IFrameworkView**-Elements, in dem Ihr Spiel (im Wesentlichen) enthalten ist, müssen Sie eine Factoryklasse implementieren, über die eine Instanz des **IFrameworkView**-Elements erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="4e180-120">In addition to creating the **IFrameworkView**, which is (essentially) where your game will reside, you need to implement a factory class that creates an instance of your **IFrameworkView**.</span></span> <span data-ttu-id="4e180-121">Das Spiel verfügt weiterhin über eine ausführbare Datei mit einer **main()**-Methode. Mithilfe von "main" kann jedoch lediglich die Factory verwendet werden, um die **IFrameworkView**-Instanz zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="4e180-121">Your game still has an executable with a method called **main()**, but all main can do is use the factory to create the **IFrameworkView** instance.</span></span>

<span data-ttu-id="4e180-122">main-Funktion</span><span class="sxs-lookup"><span data-stu-id="4e180-122">Main function</span></span>

```cpp
//-----------------------------------------------------------------------------
// Required method for a DirectX-only app.
// The main function is only used to initialize the app's IFrameworkView class.
//-----------------------------------------------------------------------------
[Platform::MTAThread]
int main(Platform::Array<Platform::String^>^)
{
    auto direct3DApplicationSource = ref new Direct3DApplicationSource();
    CoreApplication::Run(direct3DApplicationSource);
    return 0;
}
```

<span data-ttu-id="4e180-123">IFrameworkView-Factory</span><span class="sxs-lookup"><span data-stu-id="4e180-123">IFrameworkView factory</span></span>

```cpp
//-----------------------------------------------------------------------------
// This class creates our IFrameworkView.
//-----------------------------------------------------------------------------
ref class Direct3DApplicationSource sealed : 
    Windows::ApplicationModel::Core::IFrameworkViewSource
{
public:
    virtual Windows::ApplicationModel::Core::IFrameworkView^ CreateView()
    {
        return ref new Cube11();
    };
};
```

## <a name="port-the-game-loop"></a><span data-ttu-id="4e180-124">Portieren der Spielschleife</span><span class="sxs-lookup"><span data-stu-id="4e180-124">Port the game loop</span></span>


<span data-ttu-id="4e180-125">Sehen wir uns die Spielschleife unserer Direct3D9-Implementierung an.</span><span class="sxs-lookup"><span data-stu-id="4e180-125">Let's look at the game loop from our Direct3D 9 implementation.</span></span> <span data-ttu-id="4e180-126">Dieser Code ist in der main-Funktion der App vorhanden.</span><span class="sxs-lookup"><span data-stu-id="4e180-126">This code exists in the app's main function.</span></span> <span data-ttu-id="4e180-127">Mit jeder Iteration dieser Schleife wird eine Fenstermeldung verarbeitet oder ein Frame gerendert.</span><span class="sxs-lookup"><span data-stu-id="4e180-127">Each iteration of this loop processes a window message or renders a frame.</span></span>

<span data-ttu-id="4e180-128">Spielschleife im Direct3D9-Desktopspiel</span><span class="sxs-lookup"><span data-stu-id="4e180-128">Game loop in Direct3D 9 desktop game</span></span>

```cpp
while(WM_QUIT != msg.message)
{
    // Process window events.
    // Use PeekMessage() so we can use idle time to render the scene. 
    bGotMsg = (PeekMessage(&msg, NULL, 0U, 0U, PM_REMOVE) != 0);

    if(bGotMsg)
    {
        // Translate and dispatch the message
        TranslateMessage(&msg);
        DispatchMessage(&msg);
    }
    else
    {
        // Render a new frame.
        // Render frames during idle time (when no messages are waiting).
        RenderFrame();
    }
}
```

<span data-ttu-id="4e180-129">Die Spielschleife in der UWP-Version unseres Spiels ist ähnlich, dabei jedoch einfacher aufgebaut:</span><span class="sxs-lookup"><span data-stu-id="4e180-129">The game loop is similar - but easier - in the UWP version of our game:</span></span>

<span data-ttu-id="4e180-130">Die Spielschleife befindet sich in der [**IFrameworkView::Run**](https://msdn.microsoft.com/library/windows/apps/hh700505)-Methode (anstatt **main()**), weil die Funktionen des Spiels über die [**IFrameworkView**](https://msdn.microsoft.com/library/windows/apps/hh700478)-Klasse abgewickelt werden.</span><span class="sxs-lookup"><span data-stu-id="4e180-130">The game loop goes in the [**IFrameworkView::Run**](https://msdn.microsoft.com/library/windows/apps/hh700505) method (instead of **main()**) because our game functions within the [**IFrameworkView**](https://msdn.microsoft.com/library/windows/apps/hh700478) class.</span></span>

<span data-ttu-id="4e180-131">Anstatt ein Framework zur Behandlung von Meldungen zu implementieren und [**PeekMessage**](https://msdn.microsoft.com/library/windows/desktop/ms644943) aufzurufen, können wir die [**ProcessEvents**](https://msdn.microsoft.com/library/windows/apps/br208215)-Methode aufrufen, die in das [**CoreDispatcher**](https://msdn.microsoft.com/library/windows/apps/br208211)-Element des App-Fensters integriert ist.</span><span class="sxs-lookup"><span data-stu-id="4e180-131">Instead of implementing a message handling framework and calling [**PeekMessage**](https://msdn.microsoft.com/library/windows/desktop/ms644943), we can call the [**ProcessEvents**](https://msdn.microsoft.com/library/windows/apps/br208215) method built in to our app window's [**CoreDispatcher**](https://msdn.microsoft.com/library/windows/apps/br208211).</span></span> <span data-ttu-id="4e180-132">Es ist nicht erforderlich, dass die Spielschleife über Verzweigungen verfügt und Meldungen behandelt. Rufen Sie einfach **ProcessEvents** auf, und fahren Sie fort.</span><span class="sxs-lookup"><span data-stu-id="4e180-132">There's no need for the game loop to branch and handle messages - just call **ProcessEvents** and proceed.</span></span>

<span data-ttu-id="4e180-133">Spielschleife im Direct3D 11-Microsoft Store-Spiel</span><span class="sxs-lookup"><span data-stu-id="4e180-133">Game loop in Direct3D 11 Microsoft Store game</span></span>

```cpp
// UWP apps should not exit. Use app lifecycle events instead.
while (true)
{
    // Process window events.
    auto dispatcher = CoreWindow::GetForCurrentThread()->Dispatcher;
    dispatcher->ProcessEvents(CoreProcessEventsOption::ProcessAllIfPresent);

    // Render a new frame.
    RenderFrame();
}
```

<span data-ttu-id="4e180-134">Nun verfügen wir über eine UWP-App, von der die gleiche grundlegende Grafikinfrastruktur eingerichtet und der gleiche farbige Würfel wie im DirectX 9-Beispiel gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="4e180-134">Now we have a UWP app that sets up the same basic graphics infrastructure, and renders the same colorful cube, as our DirectX 9 example.</span></span>

## <a name="where-do-i-go-from-here"></a><span data-ttu-id="4e180-135">Wie geht es weiter?</span><span class="sxs-lookup"><span data-stu-id="4e180-135">Where do I go from here?</span></span>


<span data-ttu-id="4e180-136">Richten Sie ein Lesezeichen für [DirectX11-Portierung – Häufig gestellte Fragen](directx-porting-faq.md) ein.</span><span class="sxs-lookup"><span data-stu-id="4e180-136">Bookmark the [DirectX 11 porting FAQ](directx-porting-faq.md).</span></span>

<span data-ttu-id="4e180-137">Die DirectX-UWP-Vorlagen enthalten eine stabile Direct3D-Geräteinfrastruktur, die bereit für die Nutzung mit Ihrem UWP-Spiel ist.</span><span class="sxs-lookup"><span data-stu-id="4e180-137">The DirectX UWP templates include a robust Direct3D device infrastructure that's ready for use with your game.</span></span> <span data-ttu-id="4e180-138">Eine Anleitung zum Auswählen der richtigen Vorlage finden Sie unter [Erstellen eines DirectX-Spieleprojekts aus einer Vorlage](user-interface.md).</span><span class="sxs-lookup"><span data-stu-id="4e180-138">See [Create a DirectX game project from a template](user-interface.md) for guidance on picking the right template.</span></span>

<span data-ttu-id="4e180-139">Lesen Sie sich die folgenden ausführlichen Artikel zur Entwicklung von Microsoft Store-Spielen durch:</span><span class="sxs-lookup"><span data-stu-id="4e180-139">Visit the following in-depth Microsoft Store game game development articles:</span></span>

-   [<span data-ttu-id="4e180-140">Exemplarische Vorgehensweise: Erstellen eines einfachen UWP-Spiels mit DirectX</span><span class="sxs-lookup"><span data-stu-id="4e180-140">Walkthrough: a simple UWP game with DirectX</span></span>](tutorial--create-your-first-uwp-directx-game.md)
-   [<span data-ttu-id="4e180-141">Audio für Spiele</span><span class="sxs-lookup"><span data-stu-id="4e180-141">Audio for games</span></span>](working-with-audio-in-your-directx-game.md)
-   [<span data-ttu-id="4e180-142">Bewegungs-/Blicksteuerungen für Spiele</span><span class="sxs-lookup"><span data-stu-id="4e180-142">Move-look controls for games</span></span>](tutorial--adding-move-look-controls-to-your-directx-game.md)

 

 




