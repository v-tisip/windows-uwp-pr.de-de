---
author: eliotcowley
title: Hinzufügen von visuellem Inhalt zum Marble Maze-Beispiel
description: In diesem Dokument wird beschrieben, wie das Spiel Marble Maze Direct3D und Direct2D in der App-Umgebung der universellen Windows Plattform verwendet wird, sodass Sie die Muster erlernen und anpassen können, wenn Sie mit Ihrem eigenen Spielinhalt arbeiten.
ms.assetid: 6e43422e-e1a1-b79e-2c4b-7d5b4fa88647
ms.author: elcowle
ms.date: 09/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Beispiel, DirectX, Grafiken
ms.localizationpriority: medium
ms.openlocfilehash: 5171578b844829ec590b654194639ed6c8ebbfe1
ms.sourcegitcommit: cbe7cf620622a5e4df7414f9e38dfecec1cfca99
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "7445666"
---
# <a name="adding-visual-content-to-the-marble-maze-sample"></a><span data-ttu-id="39708-104">Hinzufügen von visuellem Inhalt zum Marble Maze-Beispiel</span><span class="sxs-lookup"><span data-stu-id="39708-104">Adding visual content to the Marble Maze sample</span></span>




<span data-ttu-id="39708-105">In diesem Dokument wird beschrieben, wie das Spiel Marble Maze Direct3D und Direct2D in der UWP-App-Umgebung (Universelle Windows-Plattform) verwendet, sodass Sie die Muster erlernen und anpassen können, wenn Sie mit Ihrem eigenen Spielinhalt arbeiten.</span><span class="sxs-lookup"><span data-stu-id="39708-105">This document describes how the Marble Maze game uses Direct3D and Direct2D in the Universal Windows Platform (UWP) app environment so that you can learn the patterns and adapt them when you work with your own game content.</span></span> <span data-ttu-id="39708-106">Informationen dazu, wie visuelle Spielkomponenten in die Anwendungsgesamtstruktur von Marble Maze passen, finden Sie unter [Marble Maze-Anwendungsstruktur](marble-maze-application-structure.md).</span><span class="sxs-lookup"><span data-stu-id="39708-106">To learn how visual game components fit in the overall application structure of Marble Maze, see [Marble Maze application structure](marble-maze-application-structure.md).</span></span>

<span data-ttu-id="39708-107">Bei der Entwicklung der visuellen Aspekte von Marble Maze haben wir die folgenden grundlegenden Schritte ausgeführt:</span><span class="sxs-lookup"><span data-stu-id="39708-107">We followed these basic steps as we developed the visual aspects of Marble Maze:</span></span>

1.  <span data-ttu-id="39708-108">Erstellen eines Basisframeworks zur Initialisierung der Direct3D- und Direct2D-Umgebungen.</span><span class="sxs-lookup"><span data-stu-id="39708-108">Create a basic framework that initializes the Direct3D and Direct2D environments.</span></span>
2.  <span data-ttu-id="39708-109">Verwenden von Bild-Bildbearbeitungsprogrammen zum Entwerfen der 2D- und 3D-Grafiken-Objekte, die im Spiel angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="39708-109">Use image and model editing programs to design the 2D and 3D assets that appear in the game.</span></span>
3.  <span data-ttu-id="39708-110">Stellen Sie sicher, dass 2D- und 3D-Grafiken Objekte ordnungsgemäß geladen und im Spiel angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="39708-110">Ensure that 2D and 3D assets properly load and appear in the game.</span></span>
4.  <span data-ttu-id="39708-111">Integrieren von Vertex- und Pixelshadern zur Verbesserung der visuellen Qualität der Spielobjekte.</span><span class="sxs-lookup"><span data-stu-id="39708-111">Integrate vertex and pixel shaders that enhance the visual quality of the game assets.</span></span>
5.  <span data-ttu-id="39708-112">Integrieren der Spiellogik, beispielsweise Animationen und Benutzereingabe.</span><span class="sxs-lookup"><span data-stu-id="39708-112">Integrate game logic, such as animation and user input.</span></span>

<span data-ttu-id="39708-113">Wir ferner auf 3D-Ressourcen hinzufügen und anschließend auf 2D-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="39708-113">We also focused first on adding 3D assets and then on 2D assets.</span></span> <span data-ttu-id="39708-114">Beispielsweise haben wir den Schwerpunkt zunächst auf die grundlegende Spiellogik gelegt, bevor wir das Menüsystem und den Timer hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="39708-114">For example, we focused on core game logic before we added the menu system and timer.</span></span>

<span data-ttu-id="39708-115">Darüber hinaus mussten wir einige dieser Schritte während des Entwicklungsprozesses mehrmals durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="39708-115">We also needed to iterate through some of these steps multiple times during the development process.</span></span> <span data-ttu-id="39708-116">Angenommen, mussten wir den Gitter- und labyrinthmodellen geändert, wir auch ein Teil des shadercodes ändern, der diese Modelle unterstützt.</span><span class="sxs-lookup"><span data-stu-id="39708-116">For example, as we made changes to the mesh and marble models, we had to also change some of the shader code that supports those models.</span></span>

> [!NOTE]
> <span data-ttu-id="39708-117">Den Beispielcode für dieses Dokument finden Sie im [DirectX-Beispielspiel Marble Maze](http://go.microsoft.com/fwlink/?LinkId=624011).</span><span class="sxs-lookup"><span data-stu-id="39708-117">The sample code that corresponds to this document is found in the [DirectX Marble Maze game sample](http://go.microsoft.com/fwlink/?LinkId=624011).</span></span>

 
<span data-ttu-id="39708-118">Es folgen einige wichtige Punkte, die in diesem Dokument erläutert werden und die beim Arbeiten mit DirectX und visuellen Spielinhalten relevant sind, und zwar beim Initialisieren der DirectX-Grafikbibliotheken, beim Laden von Szenenressourcen und beim Aktualisieren und Rendern der Szene:</span><span class="sxs-lookup"><span data-stu-id="39708-118">Here are some of the key points that this document discusses for when you work with DirectX and visual game content, namely, when you initialize the DirectX graphics libraries, load scene resources, and update and render the scene:</span></span>

-   <span data-ttu-id="39708-119">Das Hinzufügen von Spielinhalt umfasst normalerweise viele Schritte.</span><span class="sxs-lookup"><span data-stu-id="39708-119">Adding game content typically involves many steps.</span></span> <span data-ttu-id="39708-120">Für diese Schritte ist oftmals auch eine Iteration erforderlich.</span><span class="sxs-lookup"><span data-stu-id="39708-120">These steps also often require iteration.</span></span> <span data-ttu-id="39708-121">Spielentwickler konzentrieren sich oftmals zunächst auf das Hinzufügen von 3D Spielinhalt und anschließend auf 2D Inhalt hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="39708-121">Game developers often focus first on adding 3D game content and then on adding 2D content.</span></span>
-   <span data-ttu-id="39708-122">Erreichen Sie mehr Kunden, und liefern Sie ihnen eine großartiges Spielerlebnis, indem Sie möglichst viele Grafikhardwarekomponenten unterstützen.</span><span class="sxs-lookup"><span data-stu-id="39708-122">Reach more customers and give them all a great experience by supporting the greatest range of graphics hardware as possible.</span></span>
-   <span data-ttu-id="39708-123">Nehmen Sie eine saubere Trennung der Entwurfszeit- und Laufzeitformate vor.</span><span class="sxs-lookup"><span data-stu-id="39708-123">Cleanly separate design-time and run-time formats.</span></span> <span data-ttu-id="39708-124">Strukturieren Sie Ihre Entwurfszeitobjekte, um die Flexibilität zu maximieren und schnelle Inhaltsiterationen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="39708-124">Structure your design-time assets to maximize flexibility and enable rapid iterations on content.</span></span> <span data-ttu-id="39708-125">Formatieren und komprimieren Sie die Objekte so, dass sie zur Laufzeit so effizient wie möglich geladen und gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="39708-125">Format and compress your assets to load and render as efficiently as possible at run time.</span></span>
-   <span data-ttu-id="39708-126">Die Erstellung der Direct3D- und Direct2D-Geräte in einer UWP-App ähnelt weitestgehend der Vorgehensweise für eine klassische Windows-Desktop-App.</span><span class="sxs-lookup"><span data-stu-id="39708-126">You create the Direct3D and Direct2D devices in a UWP app much like you do in a classic Windows desktop app.</span></span> <span data-ttu-id="39708-127">Ein wichtiger Unterschied besteht in der Art und Weise der Zuordnung der Swapchain zum Ausgabefenster.</span><span class="sxs-lookup"><span data-stu-id="39708-127">One important difference is how the swap chain is associated with the output window.</span></span>
-   <span data-ttu-id="39708-128">Stellen Sie beim Entwickeln des Spiels sicher, dass das von Ihnen ausgewählte Gitterformat die wichtigen Szenarien unterstützt.</span><span class="sxs-lookup"><span data-stu-id="39708-128">When you design your game, ensure that the mesh format that you choose supports your key scenarios.</span></span> <span data-ttu-id="39708-129">Wenn für Ihr Spiel beispielsweise eine Kollision erforderlich ist, stellen Sie sicher, dass Sie Kollisionsdaten aus Ihren Gittern abrufen.</span><span class="sxs-lookup"><span data-stu-id="39708-129">For example, if your game requires collision, make sure that you can obtain collision data from your meshes.</span></span>
-   <span data-ttu-id="39708-130">Separieren Sie die Spiellogik von der Renderlogik, indem Sie zunächst alle Szenenobjekte aktualisieren, bevor Sie sie rendern.</span><span class="sxs-lookup"><span data-stu-id="39708-130">Separate game logic from rendering logic by first updating all scene objects before you render them.</span></span>
-   <span data-ttu-id="39708-131">Zeichnen Sie in der Regel Ihre 3D-Szene-Objekten, und dann alle 2D-Objekten, die vor der Szene angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="39708-131">You typically draw your 3D scene objects, and then any 2D objects that appear in front of the scene.</span></span>
-   <span data-ttu-id="39708-132">Synchronisieren Sie die Zeichnung mit der vertikalen Austastung, um sicherzustellen, dass das Spiel keine Zeit für das Zeichen von Frames verwendet, die letztendlich nie auf dem Bildschirm angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="39708-132">Synchronize drawing to the vertical blank to ensure that your game does not spend time drawing frames that will never be actually shown on the display.</span></span> <span data-ttu-id="39708-133">Eine *vertikale austastung* ist die Zeit zwischen den Abschluss eines Frames Zeichnen auf dem Monitor und der nächste Frame beginnt.</span><span class="sxs-lookup"><span data-stu-id="39708-133">A *vertical blank* is the time between when one frame finishes drawing to the monitor and the next frame begins.</span></span>

## <a name="getting-started-with-directx-graphics"></a><span data-ttu-id="39708-134">Erste Schritte mit DirectX-Grafiken</span><span class="sxs-lookup"><span data-stu-id="39708-134">Getting started with DirectX graphics</span></span>


<span data-ttu-id="39708-135">Wenn wir das Spiel Marble Maze universelle Windows-Plattform (UWP) geplant, haben wir uns C++ und Direct3D 11.1 entschieden, da sie sind eine ausgezeichnete Wahl für die Erstellung von 3D-Spielen, die maximale Kontrolle über das Rendern und hohe Leistung erfordern.</span><span class="sxs-lookup"><span data-stu-id="39708-135">When we planned the Marble Maze Universal Windows Platform (UWP) game, we chose C++ and Direct3D 11.1 because they are excellent choices for creating 3D games that require maximum control over rendering and high performance.</span></span> <span data-ttu-id="39708-136">DirectX 11.1 unterstützt Hardware von DirectX 9 bis DirectX 11 und kann Sie daher dabei unterstützen, mehr Kunden auf effizientere Art und Weise zu erreichen, da Sie so den Code für frühere DirectX-Versionen nicht neu schreiben müssen.</span><span class="sxs-lookup"><span data-stu-id="39708-136">DirectX 11.1 supports hardware from DirectX 9 to DirectX 11, and therefore can help you reach more customers more efficiently because you don't have to rewrite code for each of the earlier DirectX versions.</span></span>

<span data-ttu-id="39708-137">Marble Maze verwendet Direct3D 11.1 zum Rendern der 3D Spielobjekte, nämlich die Kugel und das Labyrinth.</span><span class="sxs-lookup"><span data-stu-id="39708-137">Marble Maze uses Direct3D 11.1 to render the 3D game assets, namely the marble and the maze.</span></span> <span data-ttu-id="39708-138">Marble Maze auch Direct2D, DirectWrite und Windows-Bilderstellungskomponente (Windows Imaging Component, WIC) zum Zeichnen der 2D Spielobjekte, beispielsweise der Menüs und des Timers.</span><span class="sxs-lookup"><span data-stu-id="39708-138">Marble Maze also uses Direct2D, DirectWrite, and Windows Imaging Component (WIC) to draw the 2D game assets, such as the menus and the timer.</span></span>

<span data-ttu-id="39708-139">Die Entwicklung eines Spiels erfordert Planung.</span><span class="sxs-lookup"><span data-stu-id="39708-139">Game development requires planning.</span></span> <span data-ttu-id="39708-140">Wenn Sie DirectX-Grafik nicht vertraut sind, empfehlen wir, Sie lesen [DirectX: Erste Schritte](directx-getting-started.md) mit den grundlegenden Konzepten der Erstellung eines UWP-DirectX-Spiels vertraut.</span><span class="sxs-lookup"><span data-stu-id="39708-140">If you are new to DirectX graphics, we recommend that you read [DirectX: Getting started](directx-getting-started.md) to familiarize yourself with the basic concepts of creating a UWP DirectX game.</span></span> <span data-ttu-id="39708-141">Wie Sie dieses Dokuments durchlesen und der Marble Maze-Quellcodes durchgehen, finden Sie in den folgenden Ressourcen für ausführliche Informationen zu DirectX-Grafiken:</span><span class="sxs-lookup"><span data-stu-id="39708-141">As you read this document and work through the Marble Maze source code, you can refer to the following resources for more in-depth information about DirectX graphics:</span></span>

-   <span data-ttu-id="39708-142">[Direct3D 11-Grafiken](https://msdn.microsoft.com/library/windows/desktop/ff476080): Beschreibt Direct3D 11, eine leistungsstarken, hardwarebeschleunigte 3D-Grafiken API zum Rendern von 3D-Geometrie auf der Windows-Plattform.</span><span class="sxs-lookup"><span data-stu-id="39708-142">[Direct3D 11 Graphics](https://msdn.microsoft.com/library/windows/desktop/ff476080): Describes Direct3D 11, a powerful, hardware-accelerated 3D graphics API for rendering 3D geometry on the Windows platform.</span></span>
-   <span data-ttu-id="39708-143">[Direct2D](https://msdn.microsoft.com/library/windows/desktop/dd370990): Beschreibt Direct2D, eine hardwarebeschleunigte, 2D Grafik-API, die bietet hohe Leistung und Rendern mit hoher Qualität für 2D-Geometrie, Bitmaps und Text.</span><span class="sxs-lookup"><span data-stu-id="39708-143">[Direct2D](https://msdn.microsoft.com/library/windows/desktop/dd370990): Describes Direct2D, a hardware-accelerated, 2D graphics API that provides high performance and high-quality rendering for 2D geometry, bitmaps, and text.</span></span>
-   <span data-ttu-id="39708-144">[DirectWrite](https://msdn.microsoft.com/library/windows/desktop/dd368038): Beschreibt Beschreibung von DirectWrite, womit das Rendern von Text in hoher Qualität unterstützt.</span><span class="sxs-lookup"><span data-stu-id="39708-144">[DirectWrite](https://msdn.microsoft.com/library/windows/desktop/dd368038): Describes DirectWrite, which supports high-quality text rendering.</span></span>
-   <span data-ttu-id="39708-145">[Windows-Bilderstellungskomponente](https://msdn.microsoft.com/library/windows/desktop/ee719902): Beschreibt WIC, eine erweiterbare Plattform, die Low-Level-API für digitale Bilder bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="39708-145">[Windows Imaging Component](https://msdn.microsoft.com/library/windows/desktop/ee719902): Describes WIC, an extensible platform that provides low-level API for digital images.</span></span>

### <a name="feature-levels"></a><span data-ttu-id="39708-146">Featureebenen</span><span class="sxs-lookup"><span data-stu-id="39708-146">Feature levels</span></span>

<span data-ttu-id="39708-147">Direct3D 11 führt ein Paradigma mit dem Namen *"featureebenen" trägt*.</span><span class="sxs-lookup"><span data-stu-id="39708-147">Direct3D 11 introduces a paradigm named *feature levels*.</span></span> <span data-ttu-id="39708-148">Eine Featureebene ist ein klar definierter Satz mit GPU-Funktionen.</span><span class="sxs-lookup"><span data-stu-id="39708-148">A feature level is a well-defined set of GPU functionality.</span></span> <span data-ttu-id="39708-149">Mithilfe von Featureebenen können Sie Ihr Spiel für die Ausführung mit früheren Versionen von Direct3D-Hardware vorsehen.</span><span class="sxs-lookup"><span data-stu-id="39708-149">Use feature levels to target your game to run on earlier versions of Direct3D hardware.</span></span> <span data-ttu-id="39708-150">Marble Maze unterstützt die Featureebene 9.1, da keine erweiterten Features von den höheren Ebenen erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="39708-150">Marble Maze supports feature level 9.1 because it requires no advanced features from the higher levels.</span></span> <span data-ttu-id="39708-151">Es wird empfohlen, einen möglichst großen Hardwarebereich zu unterstützen und den Spielinhalt zu skalieren, sodass all Ihre Kunden von einem großartigen Spielerlebnis profitieren können – ganz gleich, ob Sie einen normalen Computer oder Highend-Computer besitzen.</span><span class="sxs-lookup"><span data-stu-id="39708-151">We recommend that you support the greatest range of hardware possible and scale your game content so that your customers that have either high or low-end computers all have a great experience.</span></span> <span data-ttu-id="39708-152">Weitere Informationen zu Featureebenen finden Sie unter [Direct3D11 unter kompatibler Hardware](https://msdn.microsoft.com/library/windows/desktop/ff476872).</span><span class="sxs-lookup"><span data-stu-id="39708-152">For more information about feature levels, see [Direct3D 11 on Downlevel Hardware](https://msdn.microsoft.com/library/windows/desktop/ff476872).</span></span>

## <a name="initializing-direct3d-and-direct2d"></a><span data-ttu-id="39708-153">Initialisieren von Direct3D und Direct2D</span><span class="sxs-lookup"><span data-stu-id="39708-153">Initializing Direct3D and Direct2D</span></span>


<span data-ttu-id="39708-154">Ein Gerät repräsentiert die Grafikkarte.</span><span class="sxs-lookup"><span data-stu-id="39708-154">A device represents the display adapter.</span></span> <span data-ttu-id="39708-155">Die Erstellung der Direct3D- und Direct2D-Geräte in einer UWP-App ähnelt weitestgehend der Vorgehensweise für eine klassische Windows-Desktop-App.</span><span class="sxs-lookup"><span data-stu-id="39708-155">You create the Direct3D and Direct2D devices in a UWP app much like you do in a classic Windows desktop app.</span></span> <span data-ttu-id="39708-156">Der wesentliche Unterschied besteht in der Art und Weise, wie Sie die Direct3D-Swapchain mit dem Windowing-System verbinden.</span><span class="sxs-lookup"><span data-stu-id="39708-156">The main difference is how you connect the Direct3D swap chain to the windowing system.</span></span>

<span data-ttu-id="39708-157">Die **DeviceResources**-Klasse ist eine Grundlage für die Verwaltung von Direct3D und Direct2D.</span><span class="sxs-lookup"><span data-stu-id="39708-157">The **DeviceResources** class is a foundation for managing Direct3D and Direct2D.</span></span> <span data-ttu-id="39708-158">Diese Klasse verarbeitet die allgemeine Infrastruktur, keine spielspezifischen Objekte.</span><span class="sxs-lookup"><span data-stu-id="39708-158">This class handles general infrastructure, not game-specific assets.</span></span> <span data-ttu-id="39708-159">Marble Maze definiert die Klasse **MarbleMazeMain** Handle spielspezifische Ressourcen, das einen Verweis auf ein **DeviceResources** -Objekt, um den Zugriff auf Direct3D und Direct2D zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="39708-159">Marble Maze defines the **MarbleMazeMain** class to handle game-specific assets, which has a reference to a **DeviceResources** object to give it access to Direct3D and Direct2D.</span></span>

<span data-ttu-id="39708-160">Während der Initialisierung erstellt die **DeviceResources** -Konstruktor geräteabhängige Ressourcen und die Direct3D und Direct2D-Geräte.</span><span class="sxs-lookup"><span data-stu-id="39708-160">During initialization, the **DeviceResources** constructor creates device-independent resources and the Direct3D and Direct2D devices.</span></span>

```cpp
// Initialize the Direct3D resources required to run. 
DX::DeviceResources::DeviceResources() :
    m_screenViewport(),
    m_d3dFeatureLevel(D3D_FEATURE_LEVEL_9_1),
    m_d3dRenderTargetSize(),
    m_outputSize(),
    m_logicalSize(),
    m_nativeOrientation(DisplayOrientations::None),
    m_currentOrientation(DisplayOrientations::None),
    m_dpi(-1.0f),
    m_deviceNotify(nullptr)
{
    CreateDeviceIndependentResources();
    CreateDeviceResources();
}
```

<span data-ttu-id="39708-161">Die **DeviceResources**-Klasse separiert diese Funktion, sodass sie leichter reagieren kann, wenn sich die Umgebung ändert.</span><span class="sxs-lookup"><span data-stu-id="39708-161">The **DeviceResources** class separates this functionality so that it can more easily respond when the environment changes.</span></span> <span data-ttu-id="39708-162">Beispielsweise ruft sie die **CreateWindowSizeDependentResources**-Methode auf, wenn sich die Fenstergröße ändert.</span><span class="sxs-lookup"><span data-stu-id="39708-162">For example, it calls the **CreateWindowSizeDependentResources** method when the window size changes.</span></span>

###  <a name="initializing-the-direct2d-directwrite-and-wic-factories"></a><span data-ttu-id="39708-163">Initialisieren der Direct2D-, DirectWrite- und WIC-Factorys</span><span class="sxs-lookup"><span data-stu-id="39708-163">Initializing the Direct2D, DirectWrite, and WIC factories</span></span>

<span data-ttu-id="39708-164">Die **DeviceResources::CreateDeviceIndependentResources**-Methode erstellt die Factorys für Direct2D, DirectWrite und WIC.</span><span class="sxs-lookup"><span data-stu-id="39708-164">The **DeviceResources::CreateDeviceIndependentResources** method creates the factories for Direct2D, DirectWrite, and WIC.</span></span> <span data-ttu-id="39708-165">In DirectX-Grafiken bilden Factorys den Ausgangspunkt zum Erstellen von Grafikressourcen.</span><span class="sxs-lookup"><span data-stu-id="39708-165">In DirectX graphics, factories are the starting points for creating graphics resources.</span></span> <span data-ttu-id="39708-166">Marble Maze gibt **D2D1\_FACTORY\_TYPE\_SINGLE\_THREADED** an, weil dies der Ausführung aller Zeichnungen im Hauptthread dient.</span><span class="sxs-lookup"><span data-stu-id="39708-166">Marble Maze specifies **D2D1\_FACTORY\_TYPE\_SINGLE\_THREADED** because it performs all drawing on the main thread.</span></span>

```cpp
// These are the resources required independent of hardware. 
void DX::DeviceResources::CreateDeviceIndependentResources()
{
    // Initialize Direct2D resources.
    D2D1_FACTORY_OPTIONS options;
    ZeroMemory(&options, sizeof(D2D1_FACTORY_OPTIONS));

#if defined(_DEBUG)
    // If the project is in a debug build, enable Direct2D debugging via SDK Layers.
    options.debugLevel = D2D1_DEBUG_LEVEL_INFORMATION;
#endif

    // Initialize the Direct2D Factory.
    DX::ThrowIfFailed(
        D2D1CreateFactory(
            D2D1_FACTORY_TYPE_SINGLE_THREADED,
            __uuidof(ID2D1Factory2),
            &options,
            &m_d2dFactory
            )
        );

    // Initialize the DirectWrite Factory.
    DX::ThrowIfFailed(
        DWriteCreateFactory(
            DWRITE_FACTORY_TYPE_SHARED,
            __uuidof(IDWriteFactory2),
            &m_dwriteFactory
            )
        );

    // Initialize the Windows Imaging Component (WIC) Factory.
    DX::ThrowIfFailed(
        CoCreateInstance(
            CLSID_WICImagingFactory2,
            nullptr,
            CLSCTX_INPROC_SERVER,
            IID_PPV_ARGS(&m_wicFactory)
            )
        );
}
```

###  <a name="creating-the-direct3d-and-direct2d-devices"></a><span data-ttu-id="39708-167">Erstellen der Direct3D- und Direct2D-Geräte</span><span class="sxs-lookup"><span data-stu-id="39708-167">Creating the Direct3D and Direct2D devices</span></span>

<span data-ttu-id="39708-168">Die **DeviceResources::CreateDeviceResources**-Methode ruft [D3D11CreateDevice](https://msdn.microsoft.com/library/windows/desktop/ff476082) auf, um das Geräteobjekt zu erstellen, das die Direct3D-Grafikkarte repräsentiert.</span><span class="sxs-lookup"><span data-stu-id="39708-168">The **DeviceResources::CreateDeviceResources** method calls [D3D11CreateDevice](https://msdn.microsoft.com/library/windows/desktop/ff476082) to create the device object that represents the Direct3D display adapter.</span></span> <span data-ttu-id="39708-169">Da Marble Maze die Featureebene 9.1 und höher unterstützt, gibt die Methode **deviceresources:: Createdeviceresources** Ebenen 9.1 bis 11.1 im Array **FeatureLevels** an.</span><span class="sxs-lookup"><span data-stu-id="39708-169">Because Marble Maze supports feature level 9.1 and above, the **DeviceResources::CreateDeviceResources** method specifies levels 9.1 through 11.1 in the **featureLevels** array.</span></span> <span data-ttu-id="39708-170">Direct3D geht die Liste der Reihe nach durch und stellt die erste verfügbare Featureebene für die App bereit.</span><span class="sxs-lookup"><span data-stu-id="39708-170">Direct3D walks the list in order and gives the app the first feature level that is available.</span></span> <span data-ttu-id="39708-171">Aus diesem Grund sind die **D3D\_FEATURE\_LEVEL** Arrayeinträge aufgelistet vom höchsten zum niedrigsten Wert, damit die app die höchste Featureebene erhält.</span><span class="sxs-lookup"><span data-stu-id="39708-171">Therefore the **D3D\_FEATURE\_LEVEL** array entries are listed from highest to lowest so that the app will get the highest feature level available.</span></span> <span data-ttu-id="39708-172">Die **DeviceResources::CreateDeviceResources**-Methode erhält das Direct3D 11.1-Gerät durch Abfragen des Direct3D 11-Geräts, das von **D3D11CreateDevice** zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="39708-172">The **DeviceResources::CreateDeviceResources** method obtains the Direct3D 11.1 device by querying the Direct3D 11 device that's returned from **D3D11CreateDevice**.</span></span>

```cpp
// This flag adds support for surfaces with a different color channel ordering
// than the API default. It is required for compatibility with Direct2D.
UINT creationFlags = D3D11_CREATE_DEVICE_BGRA_SUPPORT;

#if defined(_DEBUG)
    if (DX::SdkLayersAvailable())
    {
        // If the project is in a debug build, enable debugging via SDK Layers 
        // with this flag.
        creationFlags |= D3D11_CREATE_DEVICE_DEBUG;
    }
#endif

// This array defines the set of DirectX hardware feature levels this app will support.
// Note the ordering should be preserved.
// Don't forget to declare your application's minimum required feature level in its
// description.  All applications are assumed to support 9.1 unless otherwise stated.
D3D_FEATURE_LEVEL featureLevels[] =
{
    D3D_FEATURE_LEVEL_11_1,
    D3D_FEATURE_LEVEL_11_0,
    D3D_FEATURE_LEVEL_10_1,
    D3D_FEATURE_LEVEL_10_0,
    D3D_FEATURE_LEVEL_9_3,
    D3D_FEATURE_LEVEL_9_2,
    D3D_FEATURE_LEVEL_9_1
};

// Create the Direct3D 11 API device object and a corresponding context.
ComPtr<ID3D11Device> device;
ComPtr<ID3D11DeviceContext> context;

HRESULT hr = D3D11CreateDevice(
    nullptr,                    // Specify nullptr to use the default adapter.
    D3D_DRIVER_TYPE_HARDWARE,   // Create a device using the hardware graphics driver.
    0,                          // Should be 0 unless the driver is D3D_DRIVER_TYPE_SOFTWARE.
    creationFlags,              // Set debug and Direct2D compatibility flags.
    featureLevels,              // List of feature levels this app can support.
    ARRAYSIZE(featureLevels),   // Size of the list above.
    D3D11_SDK_VERSION,          // Always set this to D3D11_SDK_VERSION for UWP apps.
    &device,                    // Returns the Direct3D device created.
    &m_d3dFeatureLevel,         // Returns feature level of device created.
    &context                    // Returns the device immediate context.
    );

if (FAILED(hr))
{
    // If the initialization fails, fall back to the WARP device.
    // For more information on WARP, see:
    // http://go.microsoft.com/fwlink/?LinkId=286690
    DX::ThrowIfFailed(
        D3D11CreateDevice(
            nullptr,
            D3D_DRIVER_TYPE_WARP, // Create a WARP device instead of a hardware device.
            0,
            creationFlags,
            featureLevels,
            ARRAYSIZE(featureLevels),
            D3D11_SDK_VERSION,
            &device,
            &m_d3dFeatureLevel,
            &context
            )
        );
}

// Store pointers to the Direct3D 11.1 API device and immediate context.
DX::ThrowIfFailed(
    device.As(&m_d3dDevice)
    );

DX::ThrowIfFailed(
    context.As(&m_d3dContext)
    );
```

<span data-ttu-id="39708-173">Anschließend erstellt die **DeviceResources::CreateDeviceResources**-Methode das Direct2D-Gerät.</span><span class="sxs-lookup"><span data-stu-id="39708-173">The **DeviceResources::CreateDeviceResources** method then creates the Direct2D device.</span></span> <span data-ttu-id="39708-174">Direct2D verwendet Microsoft DXGI (DirectX Graphics Infrastructure) für die Interoperabilität mit Direct3D.</span><span class="sxs-lookup"><span data-stu-id="39708-174">Direct2D uses Microsoft DirectX Graphics Infrastructure (DXGI) to interoperate with Direct3D.</span></span> <span data-ttu-id="39708-175">DXGI ermöglicht das Freigeben von Videospeicheroberflächen zwischen Grafiklaufzeiten.</span><span class="sxs-lookup"><span data-stu-id="39708-175">DXGI enables video memory surfaces to be shared between graphics runtimes.</span></span> <span data-ttu-id="39708-176">Marble Maze verwendet das zugrunde liegende DXGI-Gerät vom Direct3D-Gerät zum Erstellen des Direct2D-Geräts aus der Direct2D-Factory.</span><span class="sxs-lookup"><span data-stu-id="39708-176">Marble Maze uses the underlying DXGI device from the Direct3D device to create the Direct2D device from the Direct2D factory.</span></span>

```cpp
// Create the Direct2D device object and a corresponding context.
ComPtr<IDXGIDevice3> dxgiDevice;
DX::ThrowIfFailed(
    m_d3dDevice.As(&dxgiDevice)
    );

DX::ThrowIfFailed(
    m_d2dFactory->CreateDevice(dxgiDevice.Get(), &m_d2dDevice)
    );

DX::ThrowIfFailed(
    m_d2dDevice->CreateDeviceContext(
        D2D1_DEVICE_CONTEXT_OPTIONS_NONE,
        &m_d2dContext
        )
    );
```

<span data-ttu-id="39708-177">Weitere Informationen zu DXGI und zur Interoperabilität zwischen Direct2D und Direct3D finden Sie unter [Übersicht über DXGI](https://msdn.microsoft.com/library/windows/desktop/bb205075) und [Übersicht über die Interoperabilität von Direct2D und Direct3D](https://msdn.microsoft.com/library/windows/desktop/dd370966).</span><span class="sxs-lookup"><span data-stu-id="39708-177">For more information about DXGI and interoperability between Direct2D and Direct3D, see [DXGI Overview](https://msdn.microsoft.com/library/windows/desktop/bb205075) and [Direct2D and Direct3D Interoperability Overview](https://msdn.microsoft.com/library/windows/desktop/dd370966).</span></span>

### <a name="associating-direct3d-with-the-view"></a><span data-ttu-id="39708-178">Zuordnen von Direct3D zur Ansicht</span><span class="sxs-lookup"><span data-stu-id="39708-178">Associating Direct3D with the view</span></span>

<span data-ttu-id="39708-179">Die **DeviceResources::CreateWindowSizeDependentResources**-Methode erstellt die Grafikressourcen, die von einer bestimmten Fenstergröße abhängig sind, beispielsweise von der Swapchain und den Direct3D- und Direct2D-Renderzielen.</span><span class="sxs-lookup"><span data-stu-id="39708-179">The **DeviceResources::CreateWindowSizeDependentResources** method creates the graphics resources that depend on a given window size such as the swap chain and Direct3D and Direct2D render targets.</span></span> <span data-ttu-id="39708-180">Ein wichtiger Aspekt, in dem sich eine DirectX-UWP-App von einer Desktop-App unterscheidet, ist die Art und Weise, wie die Swapchain dem Ausgabefenster zugeordnet wird.</span><span class="sxs-lookup"><span data-stu-id="39708-180">One important way that a DirectX UWP app differs from a desktop app is how the swap chain is associated with the output window.</span></span> <span data-ttu-id="39708-181">Eine Swapchain dient der Anzeige des Puffers, in dem das Gerät rendert, auf dem Monitor.</span><span class="sxs-lookup"><span data-stu-id="39708-181">A swap chain is responsible for displaying the buffer to which the device renders on the monitor.</span></span> <span data-ttu-id="39708-182">[Marble Maze-Anwendungsstruktur](marble-maze-application-structure.md) wird beschrieben, wie sich das Windowing-System für eine UWP-app von einer desktop-app unterscheidet.</span><span class="sxs-lookup"><span data-stu-id="39708-182">[Marble Maze application structure](marble-maze-application-structure.md) describes how the windowing system for a UWP app differs from a desktop app.</span></span> <span data-ttu-id="39708-183">Da eine UWP-app mit [HWND](https://msdn.microsoft.com/library/windows/desktop/aa383751) -Objekten nicht funktioniert, muss Marble Maze die [idxgifactory2:: Createswapchainforcorewindow](https://msdn.microsoft.com/library/windows/desktop/hh404559) -Methode zum Zuordnen der geräteausgabe zur Ansicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="39708-183">Because a UWP app does not work with [HWND](https://msdn.microsoft.com/library/windows/desktop/aa383751) objects, Marble Maze must use the [IDXGIFactory2::CreateSwapChainForCoreWindow](https://msdn.microsoft.com/library/windows/desktop/hh404559) method to associate the device output to the view.</span></span> <span data-ttu-id="39708-184">Im folgenden Beispiel wird der Teil der **DeviceResources::CreateWindowSizeDependentResources**-Methode gezeigt, mit dem die Swapchain erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="39708-184">The following example shows the part of the **DeviceResources::CreateWindowSizeDependentResources** method that creates the swap chain.</span></span>

```cpp
// Obtain the final swap chain for this window from the DXGI factory.
DX::ThrowIfFailed(
    dxgiFactory->CreateSwapChainForCoreWindow(
        m_d3dDevice.Get(),
        reinterpret_cast<IUnknown*>(m_window.Get()),
        &swapChainDesc,
        nullptr,
        &m_swapChain
        )
    );
```

<span data-ttu-id="39708-185">Zur Minimierung des Stromverbrauchs, was vor allem für batteriebetriebene Geräte wie Laptops und Tablets wichtig ist, ruft die **DeviceResources::CreateWindowSizeDependentResources**-Methode die [IDXGIDevice1::SetMaximumFrameLatency](https://msdn.microsoft.com/library/windows/desktop/ff471334)-Methode auf, um sicherzustellen, dass das Spiel erst nach der vertikalen Austastung gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="39708-185">To minimize power consumption, which is important to do on battery-powered devices such as laptops and tablets, the **DeviceResources::CreateWindowSizeDependentResources** method calls the [IDXGIDevice1::SetMaximumFrameLatency](https://msdn.microsoft.com/library/windows/desktop/ff471334) method to ensure that the game is rendered only after the vertical blank.</span></span> <span data-ttu-id="39708-186">Die Synchronisierung mit der vertikalen austastung wird im Abschnitt [darstellen der Szene](#presenting-the-scene) in diesem Dokument detaillierter beschrieben.</span><span class="sxs-lookup"><span data-stu-id="39708-186">Synchronizing with the vertical blank is described in greater detail in the section [Presenting the scene](#presenting-the-scene) in this document.</span></span>

```cpp
// Ensure that DXGI does not queue more than one frame at a time. This both 
// reduces latency and ensures that the application will only render after each
// VSync, minimizing power consumption.
DX::ThrowIfFailed(
    dxgiDevice->SetMaximumFrameLatency(1)
    );
```

<span data-ttu-id="39708-187">Die **DeviceResources::CreateWindowSizeDependentResources**-Methode initialisiert die Grafikressourcen anhand einer Vorgehensweise, die für die meisten Spiele geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="39708-187">The **DeviceResources::CreateWindowSizeDependentResources** method initializes graphics resources in a way that works for most games.</span></span>

> [!NOTE]
> <span data-ttu-id="39708-188">Der Begriff *Ansicht* hat in der Windows-Runtime eine andere Bedeutung als in Direct3D.</span><span class="sxs-lookup"><span data-stu-id="39708-188">The term *view* has a different meaning in the Windows Runtime than it has in Direct3D.</span></span> <span data-ttu-id="39708-189">In der Windows-Runtime bezieht sich eine Ansicht auf die Sammlung von Einstellungen zur Benutzeroberfläche für eine App. Dazu gehören auch der Anzeigebereich und das Eingabeverhalten sowie der zum Verarbeiten verwendete Thread.</span><span class="sxs-lookup"><span data-stu-id="39708-189">In the Windows Runtime, a view refers to the collection of user interface settings for an app, including the display area and the input behaviors, plus the thread it uses for processing.</span></span> <span data-ttu-id="39708-190">Die benötigte Konfiguration und die benötigten Einstellungen geben Sie beim Erstellen einer Ansicht an.</span><span class="sxs-lookup"><span data-stu-id="39708-190">You specify the configuration and settings you need when you create a view.</span></span> <span data-ttu-id="39708-191">Der Einrichtungsprozess der App-Ansicht wird unter [Marble Maze-Anwendungsstruktur](marble-maze-application-structure.md) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="39708-191">The process of setting up the app view is described in [Marble Maze application structure](marble-maze-application-structure.md).</span></span>
> <span data-ttu-id="39708-192">In Direct3D hat der Begriff "Ansicht" mehrere Bedeutungen.</span><span class="sxs-lookup"><span data-stu-id="39708-192">In Direct3D, the term view has multiple meanings.</span></span> <span data-ttu-id="39708-193">Eine Ressourcenansicht definiert die unterressourcen, die eine Ressource zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="39708-193">A resource view defines the subresources that a resource can access.</span></span> <span data-ttu-id="39708-194">Wenn beispielsweise ein Texturobjekt einer Shader-Ressourcenansicht zugeordnet wird, kann dieser Shader später auf die Textur zugreifen.</span><span class="sxs-lookup"><span data-stu-id="39708-194">For example, when a texture object is associated with a shader resource view, that shader can later access the texture.</span></span> <span data-ttu-id="39708-195">Ein Vorteil einer Ressourcenansicht besteht darin, dass Daten auf unterschiedliche Art und Weise in verschiedenen Stufen der Rendering-Pipeline interpretiert werden können.</span><span class="sxs-lookup"><span data-stu-id="39708-195">One advantage of a resource view is that you can interpret data in different ways at different stages in the rendering pipeline.</span></span> <span data-ttu-id="39708-196">Weitere Informationen zu Ressourcenansichten finden Sie unter [Ressourcenansichten](https://msdn.microsoft.com/library/windows/desktop/ff476900#Views).</span><span class="sxs-lookup"><span data-stu-id="39708-196">For more information about resource views, see [Resource Views](https://msdn.microsoft.com/library/windows/desktop/ff476900#Views).</span></span>
> <span data-ttu-id="39708-197">Bei der Verwendung im Kontext einer Ansichtstransformation oder Ansichtstransformationsmatrix bezieht sich der Begriff Ansicht auf den Standort und die Ausrichtung der Kamera.</span><span class="sxs-lookup"><span data-stu-id="39708-197">When used in the context of a view transform or view transform matrix, view refers to the location and orientation of the camera.</span></span> <span data-ttu-id="39708-198">Bei einer Ansichtstransformation werden Objekte in der Welt um die Position und Ausrichtung der Kamera herum neu angeordnet.</span><span class="sxs-lookup"><span data-stu-id="39708-198">A view transform relocates objects in the world around the camera’s position and orientation.</span></span> <span data-ttu-id="39708-199">Weitere Informationen zu Ansichtstransformationen finden Sie unter [Ansichtstransformation (Direct3D9)](https://msdn.microsoft.com/library/windows/desktop/bb206342).</span><span class="sxs-lookup"><span data-stu-id="39708-199">For more information about view transforms, see [View Transform (Direct3D 9)](https://msdn.microsoft.com/library/windows/desktop/bb206342).</span></span> <span data-ttu-id="39708-200">Die Verwendung von Ressourcen- und Matrixansichten in Marble Maze werden in diesem Thema detaillierter beschrieben.</span><span class="sxs-lookup"><span data-stu-id="39708-200">How Marble Maze uses resource and matrix views is described in greater detail in this topic.</span></span>

 

## <a name="loading-scene-resources"></a><span data-ttu-id="39708-201">Laden von Szenenressourcen</span><span class="sxs-lookup"><span data-stu-id="39708-201">Loading scene resources</span></span>


<span data-ttu-id="39708-202">Marble Maze verwendet die **BasicLoader** -Klasse, die in **BasicLoader.h**deklariert wird, zum Laden von Texturen und Shader.</span><span class="sxs-lookup"><span data-stu-id="39708-202">Marble Maze uses the **BasicLoader** class, which is declared in **BasicLoader.h**, to load textures and shaders.</span></span> <span data-ttu-id="39708-203">Marble Maze verwendet die **SDKMesh** -Klasse, um die 3D Gitter für die Murmel und das Labyrinth zu laden.</span><span class="sxs-lookup"><span data-stu-id="39708-203">Marble Maze uses the **SDKMesh** class to load the 3D meshes for the maze and the marble.</span></span>

<span data-ttu-id="39708-204">Um eine reagierende App zu gewährleisten, lädt Marble Maze die Szenenressourcen asynchron oder im Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="39708-204">To ensure a responsive app, Marble Maze loads scene resources asynchronously, or in the background.</span></span> <span data-ttu-id="39708-205">Während die Objekte im Hintergrund geladen werden, kann das Spiel auf Fensterereignisse reagieren.</span><span class="sxs-lookup"><span data-stu-id="39708-205">As assets load in the background, your game can respond to window events.</span></span> <span data-ttu-id="39708-206">Dieser Prozess wird in diesem Handbuch unter [Laden von Spielobjekten im Hintergrund](marble-maze-application-structure.md#loading-game-assets-in-the-background) detaillierter erklärt.</span><span class="sxs-lookup"><span data-stu-id="39708-206">This process is explained in greater detail in [Loading game assets in the background](marble-maze-application-structure.md#loading-game-assets-in-the-background) in this guide.</span></span>

###  <a name="loading-the-2d-overlay-and-user-interface"></a><span data-ttu-id="39708-207">Laden die 2D Overlay und die Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="39708-207">Loading the 2D overlay and user interface</span></span>

<span data-ttu-id="39708-208">In Marble Maze ist die Überlagerung das Bild, das am oberen Rand des Bildschirms angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="39708-208">In Marble Maze, the overlay is the image that appears at the top of the screen.</span></span> <span data-ttu-id="39708-209">Die Überlagerung wird immer vor der Szene angezeigt.</span><span class="sxs-lookup"><span data-stu-id="39708-209">The overlay always appears in front of the scene.</span></span> <span data-ttu-id="39708-210">In Marble Maze enthält die Überlagerung das Windows-Logo und die Textzeichenfolge **DirectX Marble Maze Spielbeispiel**.</span><span class="sxs-lookup"><span data-stu-id="39708-210">In Marble Maze, the overlay contains the Windows logo and the text string **DirectX Marble Maze game sample**.</span></span> <span data-ttu-id="39708-211">Die Verwaltung der Überlagerung erfolgt durch die **SampleOverlay** -Klasse, die unter **SampleOverlay.h**definiert ist.</span><span class="sxs-lookup"><span data-stu-id="39708-211">The management of the overlay is performed by the **SampleOverlay** class, which is defined in **SampleOverlay.h**.</span></span> <span data-ttu-id="39708-212">Obwohl wir die Überlagerung als Teil der Direct3D-Beispiele verwenden, können Sie diesen Code anpassen, um beliebige Bilder anzuzeigen, die vor Ihrer Szene erscheinen.</span><span class="sxs-lookup"><span data-stu-id="39708-212">Although we use the overlay as part of the Direct3D samples, you can adapt this code to display any image that appears in front of your scene.</span></span>

<span data-ttu-id="39708-213">Ein wichtiger Aspekt der Überlagerung ist, dass die **SampleOverlay**-Klasse, da sich ihre Inhalte nicht ändern, die zugehörigen Inhalte bei der Initialisierung in einem [ID2D1Bitmap1](https://msdn.microsoft.com/library/windows/desktop/hh404349)-Objekt zeichnet bzw. dort speichert.</span><span class="sxs-lookup"><span data-stu-id="39708-213">One important aspect of the overlay is that, because its contents do not change, the **SampleOverlay** class draws, or caches, its contents to an [ID2D1Bitmap1](https://msdn.microsoft.com/library/windows/desktop/hh404349) object during initialization.</span></span> <span data-ttu-id="39708-214">Beim Zeichnen muss die **SampleOverlay**-Klasse lediglich die Bitmap auf dem Bildschirm zeichnen.</span><span class="sxs-lookup"><span data-stu-id="39708-214">At draw time, the **SampleOverlay** class only has to draw the bitmap to the screen.</span></span> <span data-ttu-id="39708-215">Auf diese Art und Weise müssen nicht für jeden Frame teure Routinen wie Textzeichnungen ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="39708-215">In this way, expensive routines such as text drawing do not have to be performed for every frame.</span></span>

<span data-ttu-id="39708-216">Die Benutzeroberfläche (UI) besteht aus 2D Komponenten, z. B. Menüs und Heads-Up-Displays (HUDs), die vor Ihrer Szene angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="39708-216">The user interface (UI) consists of 2D components, such as menus and heads-up displays (HUDs), which appear in front of your scene.</span></span> <span data-ttu-id="39708-217">Marble Maze definiert die folgenden UI-Elemente:</span><span class="sxs-lookup"><span data-stu-id="39708-217">Marble Maze defines the following UI elements:</span></span>

-   <span data-ttu-id="39708-218">Menüelemente, die dem Benutzer das Starten des Spiels oder das Anzeigen von Bestenlisten ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="39708-218">Menu items that enable the user to start the game or view high scores.</span></span>
-   <span data-ttu-id="39708-219">Einen Timer, der drei Sekunden lang abwärts zählt, bevor das Spiel beginnt.</span><span class="sxs-lookup"><span data-stu-id="39708-219">A timer that counts down for three seconds before play begins.</span></span>
-   <span data-ttu-id="39708-220">Einen Timer, der die verstrichene Spielzeit verfolgt.</span><span class="sxs-lookup"><span data-stu-id="39708-220">A timer that tracks the elapsed play time.</span></span>
-   <span data-ttu-id="39708-221">Eine Tabelle, in der die schnellsten Zeiten aufgelistet werden.</span><span class="sxs-lookup"><span data-stu-id="39708-221">A table that lists the fastest finish times.</span></span>
-   <span data-ttu-id="39708-222">Text, der **pausiert, wenn das Spiel angehalten wurde** .</span><span class="sxs-lookup"><span data-stu-id="39708-222">Text that reads **Paused** when the game is paused.</span></span>

<span data-ttu-id="39708-223">Marble Maze definiert spielspezifische UI-Elemente in **UserInterface.h**.</span><span class="sxs-lookup"><span data-stu-id="39708-223">Marble Maze defines game-specific UI elements in **UserInterface.h**.</span></span> <span data-ttu-id="39708-224">Marble Maze definiert die **ElementBase**-Klasse als Basistyp für alle UI-Elemente.</span><span class="sxs-lookup"><span data-stu-id="39708-224">Marble Maze defines the **ElementBase** class as a base type for all UI elements.</span></span> <span data-ttu-id="39708-225">Die **ElementBase**-Klasse definiert Attribute wie Größe, Position, Ausrichtung und Transparenz eines UI-Elements.</span><span class="sxs-lookup"><span data-stu-id="39708-225">The **ElementBase** class defines attributes such as the size, position, alignment, and visibility of a UI element.</span></span> <span data-ttu-id="39708-226">Zudem kontrolliert sie, wie Elemente aktualisiert und gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="39708-226">It also controls how elements are updated and rendered.</span></span>

```cpp
class ElementBase
{
public:
    virtual void Initialize() { }
    virtual void Update(float timeTotal, float timeDelta) { }
    virtual void Render() { }

    void SetAlignment(AlignType horizontal, AlignType vertical);
    virtual void SetContainer(const D2D1_RECT_F& container);
    void SetVisible(bool visible);

    D2D1_RECT_F GetBounds();

    bool IsVisible() const { return m_visible; }

protected:
    ElementBase();

    virtual void CalculateSize() { }

    Alignment       m_alignment;
    D2D1_RECT_F     m_container;
    D2D1_SIZE_F     m_size;
    bool            m_visible;
};
```

<span data-ttu-id="39708-227">Durch die Bereitstellung einer allgemeinen Basisklasse für UI-Elemente muss die **UserInterface**-Klasse, mit der die Benutzeroberfläche verwaltet wird, lediglich eine Sammlung von **ElementBase**-Objekten enthalten. Dadurch werden die UI-Verwaltung vereinfacht und ein wiederverwendbarer Benutzeroberflächenmanager bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="39708-227">By providing a common base class for UI elements, the **UserInterface** class, which manages the user interface, need only hold a collection of **ElementBase** objects, which simplifies UI management and provides a user interface manager that is reusable.</span></span> <span data-ttu-id="39708-228">Marble Maze definiert Typen, die aus **ElementBase** abgeleitet werden und spielspezifische Verhalten implementieren.</span><span class="sxs-lookup"><span data-stu-id="39708-228">Marble Maze defines types that derive from **ElementBase** that implement game-specific behaviors.</span></span> <span data-ttu-id="39708-229">**HighScoreTable** definiert beispielsweise das Verhalten für die Highscore-Tabelle.</span><span class="sxs-lookup"><span data-stu-id="39708-229">For example, **HighScoreTable** defines the behavior for the high score table.</span></span> <span data-ttu-id="39708-230">Informationen zu diesen Typen finden Sie im Quellcode.</span><span class="sxs-lookup"><span data-stu-id="39708-230">For more info about these types, refer to the source code.</span></span>

> [!NOTE]
> <span data-ttu-id="39708-231">Da Ihnen XAML eine einfachere Erstellung komplexer Benutzeroberflächen ermöglicht, wie sie beispielsweise in Simulations- und Strategiespielen vorkommen, denken Sie darüber nach, für die Definition Ihrer UI XAML zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="39708-231">Because XAML enables you to more easily create complex user interfaces, like those found in simulation and strategy games, consider whether to use XAML to define your UI.</span></span> <span data-ttu-id="39708-232">Informationen dazu, wie Sie eine Benutzeroberfläche in XAML in einem DirectX-UWP-Spiel entwickeln finden Sie unter [Erweitern des beispielspiels](tutorial-resources.md), das sich auf die DirectX-3D beispielshooters bezieht.</span><span class="sxs-lookup"><span data-stu-id="39708-232">For info about how to develop a user interface in XAML in a DirectX UWP game, see [Extend the game sample](tutorial-resources.md), which refers to the DirectX 3D shooting game sample.</span></span>

 

###  <a name="loading-shaders"></a><span data-ttu-id="39708-233">Laden von Shadern</span><span class="sxs-lookup"><span data-stu-id="39708-233">Loading shaders</span></span>

<span data-ttu-id="39708-234">Marble Maze verwendet die **BasicLoader::LoadShader**-Methode zum Laden eines Shaders aus einer Datei.</span><span class="sxs-lookup"><span data-stu-id="39708-234">Marble Maze uses the **BasicLoader::LoadShader** method to load a shader from a file.</span></span>

<span data-ttu-id="39708-235">Shader bilden derzeit in Spielen die grundlegende Einheit der GPU-Programmierung.</span><span class="sxs-lookup"><span data-stu-id="39708-235">Shaders are the fundamental unit of GPU programming in games today.</span></span> <span data-ttu-id="39708-236">Fast alle erfolgt 3D grafikverarbeitung über Shader, unabhängig davon, ob es sich um modelltransformation und szenenbeleuchtung ist oder Verarbeitung von figurengestaltung bis hin zu Tessellation komplexerer Geometrie.</span><span class="sxs-lookup"><span data-stu-id="39708-236">Nearly all 3D graphics processing is driven through shaders, whether it is model transformation and scene lighting, or more complex geometry processing, from character skinning to tessellation.</span></span> <span data-ttu-id="39708-237">Weitere Informationen zum Shader-Programmierungsmodell finden Sie unter [HLSL](https://msdn.microsoft.com/library/windows/desktop/bb509561).</span><span class="sxs-lookup"><span data-stu-id="39708-237">For more information about the shader programming model, see [HLSL](https://msdn.microsoft.com/library/windows/desktop/bb509561).</span></span>

<span data-ttu-id="39708-238">Marble Maze verwendet Vertex- und Pixel-Shader.</span><span class="sxs-lookup"><span data-stu-id="39708-238">Marble Maze uses vertex and pixel shaders.</span></span> <span data-ttu-id="39708-239">Ein Vertex-Shader wird immer für einen Eingabevertex ausgeführt und erzeugt einen Vertex als Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="39708-239">A vertex shader always operates on one input vertex and produces one vertex as output.</span></span> <span data-ttu-id="39708-240">Ein Pixel-Shader verwendet numerische Werte, Texturdaten, interpolierte Vertex-Werte und andere Daten, um eine Pixelfarbe als Ausgabe zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="39708-240">A pixel shader takes numeric values, texture data, interpolated per-vertex values, and other data to produce a pixel color as output.</span></span> <span data-ttu-id="39708-241">Da ein Shader jeweils ein Element transformiert, kann Grafikhardware, die mehrere Shader-Pipelines bereitstellt, Elementgruppen parallel bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="39708-241">Because a shader transforms one element at a time, graphics hardware that provides multiple shader pipelines can process sets of elements in parallel.</span></span> <span data-ttu-id="39708-242">Die Anzahl paralleler Pipelines, die für die GPU zur Verfügung stehen, kann deutlich größer sein als die Anzahl, die für die CPU verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="39708-242">The number of parallel pipelines that are available to the GPU can be vastly greater than the number that is available to the CPU.</span></span> <span data-ttu-id="39708-243">Daher kann der Durchsatz selbst mit einfachen Shadern deutlich verbessert werden.</span><span class="sxs-lookup"><span data-stu-id="39708-243">Therefore, even basic shaders can greatly improve throughput.</span></span>

<span data-ttu-id="39708-244">Die **marblemazemain:: Loaddeferredresources** -Methode lädt einen Vertex-Shader und einen Pixel-Shader, nachdem die Überlagerung geladen wurde.</span><span class="sxs-lookup"><span data-stu-id="39708-244">The **MarbleMazeMain::LoadDeferredResources** method loads one vertex shader and one pixel shader after it loads the overlay.</span></span> <span data-ttu-id="39708-245">Die entwurfstzeitversionen dieser Shader werden in **"basicvertexshader.HLSL"** "bzw." **BasicPixelShader.hlsl**definiert.</span><span class="sxs-lookup"><span data-stu-id="39708-245">The design-time versions of these shaders are defined in **BasicVertexShader.hlsl** and **BasicPixelShader.hlsl**, respectively.</span></span> <span data-ttu-id="39708-246">Marble Maze wendet diese Shader in der Renderphase sowohl auf die Kugel als auch auf das Labyrinth an.</span><span class="sxs-lookup"><span data-stu-id="39708-246">Marble Maze applies these shaders to both the ball and the maze during the rendering phase.</span></span>

<span data-ttu-id="39708-247">Das Marble Maze-Projekt beinhaltet sowohl HLSL (Entwurfszeitformat)- als auch CSO (Laufzeitformat)-Versionen der Shader-Dateien.</span><span class="sxs-lookup"><span data-stu-id="39708-247">The Marble Maze project includes both .hlsl (the design-time format) and .cso (the run-time format) versions of the shader files.</span></span> <span data-ttu-id="39708-248">Zur Erstellungszeit verwendet Visual Studio den Effektcompiler "fxc.exe" zum Kompilieren der HLSL-Quelldatei in einen CSO-Binär-Shader.</span><span class="sxs-lookup"><span data-stu-id="39708-248">At build time, Visual Studio uses the fxc.exe effect-compiler to compile your .hlsl source file into a .cso binary shader.</span></span> <span data-ttu-id="39708-249">Weitere Informationen zum Effektcompiler-Tool finden Sie unter [Effektcompiler-Tool](https://msdn.microsoft.com/library/windows/desktop/bb232919).</span><span class="sxs-lookup"><span data-stu-id="39708-249">For more information about the effect-compiler tool, see [Effect-Compiler Tool](https://msdn.microsoft.com/library/windows/desktop/bb232919).</span></span>

<span data-ttu-id="39708-250">Der Vertex-Shader verwendet die bereitgestellten Modell-, Ansichts- und Projektionsmatrizen zum Umwandeln der Eingabegeometrie.</span><span class="sxs-lookup"><span data-stu-id="39708-250">The vertex shader uses the supplied model, view and projection matrices to transform the input geometry.</span></span> <span data-ttu-id="39708-251">Die Positionsdaten aus der Eingabegeometrie werden umgewandelt und zweimal ausgegeben: einmal im Bildschirmbereich, der zum Rendern benötigt wird, und noch einmal im Raum, um dem Pixel-Shader das Ausführen von Beleuchtungsberechnungen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="39708-251">Position data from the input geometry is transformed and output twice: once in screen space, which is necessary for rendering, and again in world space to enable the pixel shader to perform lighting calculations.</span></span> <span data-ttu-id="39708-252">Der Oberflächennormalvektor wird in einen Raum umgewandelt, der auch vom Pixel-Shader für die Beleuchtung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="39708-252">The surface normal vector is transformed to world space, which is also used by the pixel shader for lighting.</span></span> <span data-ttu-id="39708-253">Die Texturkoordinaten werden unverändert an den Pixel-Shader übergeben.</span><span class="sxs-lookup"><span data-stu-id="39708-253">The texture coordinates are passed through unchanged to the pixel shader.</span></span>

```hlsl
sPSInput main(sVSInput input)
{
    sPSInput output;
    float4 temp = float4(input.pos, 1.0f);
    temp = mul(temp, model);
    output.worldPos = temp.xyz / temp.w;
    temp = mul(temp, view);
    temp = mul(temp, projection);
    output.pos = temp;
    output.tex = input.tex;
    output.norm = mul(float4(input.norm, 0.0f), model).xyz;
    return output;
}
```

<span data-ttu-id="39708-254">Der Pixel-Shader empfängt die Ausgabe des Vertex-Shaders als Eingabe.</span><span class="sxs-lookup"><span data-stu-id="39708-254">The pixel shader receives the output of the vertex shader as input.</span></span> <span data-ttu-id="39708-255">Dieser Shader führt Beleuchtungsberechnungen durch, um einen auslaufenden Blickpunkt nachzuahmen, der über das Labyrinth schwebt und an der Position der Kugel ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="39708-255">This shader performs lighting calculations to mimic a soft-edged spotlight that hovers over the maze and is aligned with the position of the marble.</span></span> <span data-ttu-id="39708-256">Die Beleuchtung ist für die Oberflächen am stärksten, die direkt auf das Licht zeigen.</span><span class="sxs-lookup"><span data-stu-id="39708-256">Lighting is strongest for surfaces that point directly toward the light.</span></span> <span data-ttu-id="39708-257">Die diffuse Komponente läuft auf null aus, während die Oberflächennormale eine senkrechte Position zum Licht einnimmt. Zudem nimmt die Umgebungsbeleuchtung ab, während die Normale vom Licht weg zeigt.</span><span class="sxs-lookup"><span data-stu-id="39708-257">The diffuse component tapers off to zero as the surface normal becomes perpendicular to the light, and the ambient term diminishes as the normal points away from the light.</span></span> <span data-ttu-id="39708-258">Punkte, die sich näher an der Kugel befinden (und demzufolge näher an der Mitte des Blickpunkts), werden stärker beleuchtet.</span><span class="sxs-lookup"><span data-stu-id="39708-258">Points closer to the marble (and therefore closer to the center of the spotlight) are lit more strongly.</span></span> <span data-ttu-id="39708-259">Die Beleuchtung wird jedoch für Punkte unterhalb der Kugel moduliert, um einen sanften Schatten zu simulieren.</span><span class="sxs-lookup"><span data-stu-id="39708-259">However, lighting is modulated for points underneath the marble to simulate a soft shadow.</span></span> <span data-ttu-id="39708-260">In einer echten Umgebung würde ein Objekt wie die weiße Kugel den Blickpunkt diffus auf andere Objekte in der Szene reflektieren.</span><span class="sxs-lookup"><span data-stu-id="39708-260">In a real environment, an object like the white marble would diffusely reflect the spotlight onto other objects in the scene.</span></span> <span data-ttu-id="39708-261">Dies wird für die Oberflächen angenähert, die im Sichtbereich der hellen Kugelhälfte liegen.</span><span class="sxs-lookup"><span data-stu-id="39708-261">This is approximated for the surfaces that are in view of the bright half of the marble.</span></span> <span data-ttu-id="39708-262">Die zusätzlichen Beleuchtungsfaktoren befinden sich im relativen Winkel und Abstand zur Kugel.</span><span class="sxs-lookup"><span data-stu-id="39708-262">The additional illumination factors are in relative angle and distance to the marble.</span></span> <span data-ttu-id="39708-263">Die resultierende Pixelfarbe ist eine Zusammenstellung der Stichprobentextur und dem Ergebnis der Beleuchtungsberechnungen.</span><span class="sxs-lookup"><span data-stu-id="39708-263">The resulting pixel color is a composition of the sampled texture with the result of the lighting calculations.</span></span>

```hlsl
float4 main(sPSInput input) : SV_TARGET
{
    float3 lightDirection = float3(0, 0, -1);
    float3 ambientColor = float3(0.43, 0.31, 0.24);
    float3 lightColor = 1 - ambientColor;
    float spotRadius = 50;

    // Basic ambient (Ka) and diffuse (Kd) lighting from above.
    float3 N = normalize(input.norm);
    float NdotL = dot(N, lightDirection);
    float Ka = saturate(NdotL + 1);
    float Kd = saturate(NdotL);

    // Spotlight.
    float3 vec = input.worldPos - marblePosition;
    float dist2D = sqrt(dot(vec.xy, vec.xy));
    Kd = Kd * saturate(spotRadius / dist2D);

    // Shadowing from ball.
    if (input.worldPos.z > marblePosition.z)
        Kd = Kd * saturate(dist2D / (marbleRadius * 1.5));

    // Diffuse reflection of light off ball.
    float dist3D = sqrt(dot(vec, vec));
    float3 V = normalize(vec);
    Kd += saturate(dot(-V, N)) * saturate(dot(V, lightDirection))
        * saturate(marbleRadius / dist3D);

    // Final composite.
    float4 diffuseTexture = Texture.Sample(Sampler, input.tex);
    float3 color = diffuseTexture.rgb * ((ambientColor * Ka) + (lightColor * Kd));
    return float4(color * lightStrength, diffuseTexture.a);
}
```

> [!WARNING]
> <span data-ttu-id="39708-264">Der kompilierte Pixel-Shader enthält 32 arithmetische Anweisungen und 1 Texturanweisung.</span><span class="sxs-lookup"><span data-stu-id="39708-264">The compiled pixel shader contains 32 arithmetic instructions and 1 texture instruction.</span></span> <span data-ttu-id="39708-265">Dieser Shader sollte auf Desktopcomputern und Tablets im Highend-Bereich gute Ergebnisse liefern.</span><span class="sxs-lookup"><span data-stu-id="39708-265">This shader should perform well on desktop computers and higher-end tablets.</span></span> <span data-ttu-id="39708-266">Ein normaler Computer kann diesen Shader jedoch möglicherweise nicht verarbeiten und weiterhin eine interaktive Framerate bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="39708-266">However, a lower-end computer might not be able to process this shader and still provide an interactive frame rate.</span></span> <span data-ttu-id="39708-267">Ziehen Sie die typische Hardware Ihrer Zielgruppe in Erwägung, und entwickeln Sie die Shader so, dass sie zu den Hardwarefunktionen passen.</span><span class="sxs-lookup"><span data-stu-id="39708-267">Consider the typical hardware of your target audience and design your shaders to meet the capabilities of that hardware.</span></span>

 

<span data-ttu-id="39708-268">Die **marblemazemain:: Loaddeferredresources** -Methode verwendet die **basicloader:: Loadshader** -Methode zum Laden der Shader.</span><span class="sxs-lookup"><span data-stu-id="39708-268">The **MarbleMazeMain::LoadDeferredResources** method uses the **BasicLoader::LoadShader** method to load the shaders.</span></span> <span data-ttu-id="39708-269">Im folgenden Beispiel wird der Vertex-Shader geladen.</span><span class="sxs-lookup"><span data-stu-id="39708-269">The following example loads the vertex shader.</span></span> <span data-ttu-id="39708-270">Das laufzeitformat für diesen Shader lautet **"basicvertexshader.CSO"**.</span><span class="sxs-lookup"><span data-stu-id="39708-270">The run-time format for this shader is **BasicVertexShader.cso**.</span></span> <span data-ttu-id="39708-271">Die **m\_vertexShader**-Membervariable ist ein [ID3D11VertexShader](https://msdn.microsoft.com/library/windows/desktop/ff476641)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="39708-271">The **m\_vertexShader** member variable is an [ID3D11VertexShader](https://msdn.microsoft.com/library/windows/desktop/ff476641) object.</span></span>

```cpp
BasicLoader^ loader = ref new BasicLoader(m_deviceResources->GetD3DDevice());

D3D11_INPUT_ELEMENT_DESC layoutDesc [] =
{
    { "POSITION", 0, DXGI_FORMAT_R32G32B32_FLOAT, 0, 0, D3D11_INPUT_PER_VERTEX_DATA, 0 },
    { "NORMAL", 0, DXGI_FORMAT_R32G32B32_FLOAT, 0, 12, D3D11_INPUT_PER_VERTEX_DATA, 0 },
    { "TEXCOORD", 0, DXGI_FORMAT_R32G32_FLOAT, 0, 24, D3D11_INPUT_PER_VERTEX_DATA, 0 },
    { "TANGENT", 0, DXGI_FORMAT_R32G32B32_FLOAT, 0, 32, D3D11_INPUT_PER_VERTEX_DATA, 0 },
};
m_vertexStride = 44; // must set this to match the size of layoutDesc above

Platform::String^ vertexShaderName = L"BasicVertexShader.cso";
loader->LoadShader(
    vertexShaderName,
    layoutDesc,
    ARRAYSIZE(layoutDesc),
    &m_vertexShader,
    &m_inputLayout
    );
```

<span data-ttu-id="39708-272">Die **m\_inputLayout**-Membervariable ist ein [ID3D11InputLayout](https://msdn.microsoft.com/library/windows/desktop/ff476575)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="39708-272">The **m\_inputLayout** member variable is an [ID3D11InputLayout](https://msdn.microsoft.com/library/windows/desktop/ff476575) object.</span></span> <span data-ttu-id="39708-273">Das Objekt für das Eingabelayout kapselt den Eingabestatus der Eingabeassemblerphase (IA-Phase).</span><span class="sxs-lookup"><span data-stu-id="39708-273">The input-layout object encapsulates the input state of the input assembler (IA) stage.</span></span> <span data-ttu-id="39708-274">Eine Aufgabe der IA-Phase besteht darin, die Effizienz der Shader zu erhöhen. Dazu werden systemgenerierte Werte verwendet, die auch als *Semantik* bezeichnet werden, um nur die Grundtypen oder Vertizes zu verarbeiten, die noch nicht verarbeitet wurden.</span><span class="sxs-lookup"><span data-stu-id="39708-274">One job of the IA stage is to make shaders more efficient by using system-generated values, also known as *semantics*, to process only those primitives or vertices that have not already been processed.</span></span>

<span data-ttu-id="39708-275">Verwenden Sie die [ID3D11Device::CreateInputLayout](https://msdn.microsoft.com/library/windows/desktop/ff476512)-Methode, um ein Eingabelayout aus einem Array mit Eingabeelementbeschreibungen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="39708-275">Use the [ID3D11Device::CreateInputLayout](https://msdn.microsoft.com/library/windows/desktop/ff476512) method to create an input-layout from an array of input-element descriptions.</span></span> <span data-ttu-id="39708-276">Das Array enthält ein oder mehrere Eingabeelemente. Jedes Eingabeelement beschreibt dabei ein Vertex-Datenelement von einem Vertex-Puffer.</span><span class="sxs-lookup"><span data-stu-id="39708-276">The array contains one or more input elements; each input element describes one vertex-data element from one vertex buffer.</span></span> <span data-ttu-id="39708-277">Der vollständige Satz der Eingabeelementbeschreibungen dient der Beschreibung aller Vertex-Datenelemente von sämtlichen Vertex-Puffern, die an die IA-Phase gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="39708-277">The entire set of input-element descriptions describes all of the vertex-data elements from all of the vertex buffers that will be bound to the IA stage.</span></span> 

<span data-ttu-id="39708-278">**LayoutDesc** im obigen Codeausschnitt wird die layoutbeschreibung gezeigt, die Marble Maze verwendet.</span><span class="sxs-lookup"><span data-stu-id="39708-278">**layoutDesc** in the above code snippet shows the layout description that Marble Maze uses.</span></span> <span data-ttu-id="39708-279">Die Layoutbeschreibung beschreibt einen Vertex-Puffer, der vier Vertex-Datenelemente enthält.</span><span class="sxs-lookup"><span data-stu-id="39708-279">The layout description describes a vertex buffer that contains four vertex-data elements.</span></span> <span data-ttu-id="39708-280">Die wichtigen Teile der einzelnen Einträge im Array sind der semantische Name, das Datenformat und das Byte-Offset.</span><span class="sxs-lookup"><span data-stu-id="39708-280">The important parts of each entry in the array are the semantic name, data format, and byte offset .</span></span> <span data-ttu-id="39708-281">Das **POSITION**-Element gibt beispielsweise die Vertex-Position im Objektraum an.</span><span class="sxs-lookup"><span data-stu-id="39708-281">For example, the **POSITION** element specifies the vertex position in object space.</span></span> <span data-ttu-id="39708-282">Es startet beim Byte-Offset 0 und enthält drei Gleitkommakomponenten (für insgesamt 12 Byte).</span><span class="sxs-lookup"><span data-stu-id="39708-282">It starts at byte offset 0 and contains three floating-point components (for a total of 12 bytes).</span></span> <span data-ttu-id="39708-283">Das **NORMAL**-Element gibt den Normalvektor an.</span><span class="sxs-lookup"><span data-stu-id="39708-283">The **NORMAL** element specifies the normal vector.</span></span> <span data-ttu-id="39708-284">Es startet beim Byte-Offset 12, da es im Layout direkt nach **POSITION** erscheint, wofür 12 Byte erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="39708-284">It starts at byte offset 12 because it appears directly after **POSITION** in the layout, which requires 12 bytes.</span></span> <span data-ttu-id="39708-285">Das **NORMAL**-Element enthält eine nicht signierte ganze Zahl mit vier Komponenten und 32 Bit.</span><span class="sxs-lookup"><span data-stu-id="39708-285">The **NORMAL** element contains a four-component, 32-bit unsigned-integer.</span></span>

<span data-ttu-id="39708-286">Vergleichen Sie das Eingabelayout mit der vom Vertex-Shader definierten **sVSInput**-Struktur, wie im folgenden Beispiel dargestellt.</span><span class="sxs-lookup"><span data-stu-id="39708-286">Compare the input layout with the **sVSInput** structure that is defined by the vertex shader, as shown in the following example.</span></span> <span data-ttu-id="39708-287">Die **sVSInput**-Struktur definiert die Elemente **POSITION**, **NORMAL** und **TEXCOORD0**.</span><span class="sxs-lookup"><span data-stu-id="39708-287">The **sVSInput** structure defines the **POSITION**, **NORMAL**, and **TEXCOORD0** elements.</span></span> <span data-ttu-id="39708-288">Die DirectX-Laufzeit ordnet jedes Element im Layout der Eingabestruktur zu, die vom Shader definiert wird.</span><span class="sxs-lookup"><span data-stu-id="39708-288">The DirectX runtime maps each element in the layout to the input structure that is defined by the shader.</span></span>

```hlsl
struct sVSInput
{
    float3 pos : POSITION;
    float3 norm : NORMAL;
    float2 tex : TEXCOORD0;
};

struct sPSInput
{
    float4 pos : SV_POSITION;
    float3 norm : NORMAL;
    float2 tex : TEXCOORD0;
    float3 worldPos : TEXCOORD1;
};

sPSInput main(sVSInput input)
{
    sPSInput output;
    float4 temp = float4(input.pos, 1.0f);
    temp = mul(temp, model);
    output.worldPos = temp.xyz / temp.w;
    temp = mul(temp, view);
    temp = mul(temp, projection);
    output.pos = temp;
    output.tex = input.tex;
    output.norm = mul(float4(input.norm, 0.0f), model).xyz;
    return output;
}
```

<span data-ttu-id="39708-289">Im Dokument [Semantik](https://msdn.microsoft.com/library/windows/desktop/bb509647) werden alle verfügbaren Semantiken detaillierter beschrieben.</span><span class="sxs-lookup"><span data-stu-id="39708-289">The document [Semantics](https://msdn.microsoft.com/library/windows/desktop/bb509647) describes each of the available semantics in greater detail.</span></span>

> [!NOTE]
> <span data-ttu-id="39708-290">In einem Layout können sie zusätzliche Komponenten angeben, die nicht dazu verwendet werden, mehreren Shadern die gemeinsame Verwendung desselben Layouts zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="39708-290">In a layout, you can specify additional components that are not used to enable multiple shaders to share the same layout.</span></span> <span data-ttu-id="39708-291">Beispielsweise wird das **TANGENT**-Element nicht vom Shader verwendet.</span><span class="sxs-lookup"><span data-stu-id="39708-291">For example, the **TANGENT** element is not used by the shader.</span></span> <span data-ttu-id="39708-292">Sie können das **TANGENT**-Element verwenden, wenn Sie mit Techniken wie der Normalzuordnung experimentieren möchten.</span><span class="sxs-lookup"><span data-stu-id="39708-292">You can use the **TANGENT** element if you want to experiment with techniques such as normal mapping.</span></span> <span data-ttu-id="39708-293">Mithilfe der Normalzuordnung, die auch als Bumpmapping bezeichnet wird, können Sie auf den Oberflächen von Objekten den Bumpeffekt erzeugen.</span><span class="sxs-lookup"><span data-stu-id="39708-293">By using normal mapping, also known as bump mapping, you can create the effect of bumps on the surfaces of objects.</span></span> <span data-ttu-id="39708-294">Weitere Informationen zum Bumpmapping finden Sie unter [Bumpmapping (Direct3D 9)](https://msdn.microsoft.com/library/windows/desktop/bb172379).</span><span class="sxs-lookup"><span data-stu-id="39708-294">For more information about bump mapping, see [Bump Mapping (Direct3D 9)](https://msdn.microsoft.com/library/windows/desktop/bb172379).</span></span>

 

<span data-ttu-id="39708-295">Weitere Informationen zu der Eingabeassembly-Phase finden Sie unter [Eingabe-Assembler-Stufe](https://msdn.microsoft.com/library/windows/desktop/bb205116) und [Erste Schritte mit der Eingabe-Assembler-Stufe](https://msdn.microsoft.com/library/windows/desktop/bb205117).</span><span class="sxs-lookup"><span data-stu-id="39708-295">For more information about the input assembly stage, see [Input-Assembler Stage](https://msdn.microsoft.com/library/windows/desktop/bb205116) and [Getting Started with the Input-Assembler Stage](https://msdn.microsoft.com/library/windows/desktop/bb205117).</span></span>

<span data-ttu-id="39708-296">Der Prozess der Verwendung von Vertex- und Pixel-Shadern zum Rendern der Szene wird später in diesem Dokument im Abschnitt [Rendern der Szene](#rendering-the-scene) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="39708-296">The process of using the vertex and pixel shaders to render the scene are described in the section [Rendering the scene](#rendering-the-scene) later in this document.</span></span>

### <a name="creating-the-constant-buffer"></a><span data-ttu-id="39708-297">Erstellen des Konstantenpuffers</span><span class="sxs-lookup"><span data-stu-id="39708-297">Creating the constant buffer</span></span>

<span data-ttu-id="39708-298">Der Direct3D-Puffer gruppiert eine Sammlung von Daten.</span><span class="sxs-lookup"><span data-stu-id="39708-298">Direct3D buffer groups a collection of data.</span></span> <span data-ttu-id="39708-299">Ein Konstantenpuffer ist ein Puffertyp, mit dessen Hilfe Sie Daten an Shader übergeben können.</span><span class="sxs-lookup"><span data-stu-id="39708-299">A constant buffer is a kind of buffer that you can use to pass data to shaders.</span></span> <span data-ttu-id="39708-300">Marble Maze verwendet einen Konstantenpuffer, um die Modellansicht (oder Weltansicht) sowie die Projektmatrizen für das aktive Szenenobjekt aufzunehmen.</span><span class="sxs-lookup"><span data-stu-id="39708-300">Marble Maze uses a constant buffer to hold the model (or world) view, and the projection matrices for the active scene object.</span></span>

<span data-ttu-id="39708-301">Das folgende Beispiel zeigt, wie die **marblemazemain:: Loaddeferredresources** -Methode einen Konstantenpuffer erstellt, der später Matrixdaten aufnimmt.</span><span class="sxs-lookup"><span data-stu-id="39708-301">The following example shows how the **MarbleMazeMain::LoadDeferredResources** method creates a constant buffer that will later hold matrix data.</span></span> <span data-ttu-id="39708-302">In dem Beispiel wird eine **D3D11\_BUFFER\_DESC**-Struktur erstellt, die das **D3D11\_BIND\_CONSTANT\_BUFFER**-Kennzeichen zum Angeben der Verwendung als Konstantenpuffer verwendet.</span><span class="sxs-lookup"><span data-stu-id="39708-302">The example creates a **D3D11\_BUFFER\_DESC** structure that uses the **D3D11\_BIND\_CONSTANT\_BUFFER** flag to specify usage as a constant buffer.</span></span> <span data-ttu-id="39708-303">Anschließend übergibt dieses Beispiel diese Struktur an die [ID3D11Device::CreateBuffer](https://msdn.microsoft.com/library/windows/desktop/ff476501)-Methode.</span><span class="sxs-lookup"><span data-stu-id="39708-303">This example then passes that structure to the [ID3D11Device::CreateBuffer](https://msdn.microsoft.com/library/windows/desktop/ff476501) method.</span></span> <span data-ttu-id="39708-304">Die **M\_constantBuffer**-Variable ist ein [ID3D11Buffer](https://msdn.microsoft.com/library/windows/desktop/ff476351)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="39708-304">The **m\_constantBuffer** variable is an [ID3D11Buffer](https://msdn.microsoft.com/library/windows/desktop/ff476351) object.</span></span>

```cpp
// Create the constant buffer for updating model and camera data.
D3D11_BUFFER_DESC constantBufferDesc = {0};

// Multiple of 16 bytes
constantBufferDesc.ByteWidth = ((sizeof(ConstantBuffer) + 15) / 16) * 16;

constantBufferDesc.Usage               = D3D11_USAGE_DEFAULT;
constantBufferDesc.BindFlags           = D3D11_BIND_CONSTANT_BUFFER;
constantBufferDesc.CPUAccessFlags      = 0;
constantBufferDesc.MiscFlags           = 0;

// This will not be used as a structured buffer, so this parameter is ignored.
constantBufferDesc.StructureByteStride = 0;

DX::ThrowIfFailed(
    m_deviceResources->GetD3DDevice()->CreateBuffer(
        &constantBufferDesc,
        nullptr,    // leave the buffer uninitialized
        &m_constantBuffer
        )
    );
```

<span data-ttu-id="39708-305">Die **marblemazemain:: Update** -Methode aktualisiert später **ConstantBuffer** Objekte, eine für das Labyrinth und eine für das Labyrinth.</span><span class="sxs-lookup"><span data-stu-id="39708-305">The **MarbleMazeMain::Update** method later updates **ConstantBuffer** objects, one for the maze and one for the marble.</span></span> <span data-ttu-id="39708-306">Die **marblemazemain:: Render** -Methode bindet jedes Objekt **ConstantBuffer** dann an den Konstantenpuffer, bevor der einzelnen Objekte gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="39708-306">The **MarbleMazeMain::Render** method then binds each **ConstantBuffer** object to the constant buffer before each object is rendered.</span></span> <span data-ttu-id="39708-307">Das folgende Beispiel zeigt die **ConstantBuffer** -Struktur, die im **MarbleMazeMain.h**befindet.</span><span class="sxs-lookup"><span data-stu-id="39708-307">The following example shows the **ConstantBuffer** structure, which is in **MarbleMazeMain.h**.</span></span>

```cpp
// Describes the constant buffer that draws the meshes.
struct ConstantBuffer
{
    XMFLOAT4X4 model;
    XMFLOAT4X4 view;
    XMFLOAT4X4 projection;

    XMFLOAT3 marblePosition;
    float marbleRadius;
    float lightStrength;
};
```

<span data-ttu-id="39708-308">Um ein besseres Verständnis Zuordnung von Konstantenpuffern zum Shader-Code, vergleichen Sie die Struktur der **ConstantBuffer** in **MarbleMazeMain.h** **ConstantBuffer** Konstantenpuffer, die vom Vertex-Shader in \*\*"basicvertexshader.HLSL" definiert ist \*\*:</span><span class="sxs-lookup"><span data-stu-id="39708-308">To better understand how constant buffers map to shader code, compare the **ConstantBuffer** structure in **MarbleMazeMain.h** to the **ConstantBuffer** constant buffer that is defined by the vertex shader in **BasicVertexShader.hlsl**:</span></span>

```hlsl
cbuffer ConstantBuffer : register(b0)
{
    matrix model;
    matrix view;
    matrix projection;
    float3 marblePosition;
    float marbleRadius;
    float lightStrength;
};
```

<span data-ttu-id="39708-309">Das Layout der **ConstantBuffer**-Struktur stimmt mit dem **cbuffer**-Objekt überein.</span><span class="sxs-lookup"><span data-stu-id="39708-309">The layout of the **ConstantBuffer** structure matches the **cbuffer** object.</span></span> <span data-ttu-id="39708-310">Die **cbuffer**-Variable gibt das Register b0 an. Demnach werden die Daten des Konstantenpuffers im Register 0 gespeichert.</span><span class="sxs-lookup"><span data-stu-id="39708-310">The **cbuffer** variable specifies register b0, which means that the constant buffer data is stored in register 0.</span></span> <span data-ttu-id="39708-311">Die **marblemazemain:: Render** -Methode gibt Register 0 an, wenn sie den Konstantenpuffer aktiviert.</span><span class="sxs-lookup"><span data-stu-id="39708-311">The **MarbleMazeMain::Render** method specifies register 0 when it activates the constant buffer.</span></span> <span data-ttu-id="39708-312">Auf diesen Prozess wird später in diesem Dokument detaillierter eingegangen.</span><span class="sxs-lookup"><span data-stu-id="39708-312">This process is described in greater detail later in this document.</span></span>

<span data-ttu-id="39708-313">Weitere Informationen zu Konstantenpuffern finden Sie unter [Einführung in Puffer in Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476898).</span><span class="sxs-lookup"><span data-stu-id="39708-313">For more information about constant buffers, see [Introduction to Buffers in Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476898).</span></span> <span data-ttu-id="39708-314">Weitere Informationen zum Schlüsselwort Register finden Sie unter [register](https://msdn.microsoft.com/library/windows/desktop/dd607359).</span><span class="sxs-lookup"><span data-stu-id="39708-314">For more information about the register keyword, see [register](https://msdn.microsoft.com/library/windows/desktop/dd607359).</span></span>

###  <a name="loading-meshes"></a><span data-ttu-id="39708-315">Laden von Gittern</span><span class="sxs-lookup"><span data-stu-id="39708-315">Loading meshes</span></span>

<span data-ttu-id="39708-316">Marble Maze verwendet SDK-Mesh als Laufzeitformat, da dieses Format eine grundlegende Methode zum Laden von Gitterdaten für Beispielanwendungen bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="39708-316">Marble Maze uses SDK-Mesh as the run-time format because this format provides a basic way to load mesh data for sample applications.</span></span> <span data-ttu-id="39708-317">Für die Produktionsverwendung sollten Sie ein Gitterformat nutzen, das die spezifischen Anforderungen Ihres Spiels erfüllt.</span><span class="sxs-lookup"><span data-stu-id="39708-317">For production use, you should use a mesh format that meets the specific requirements of your game.</span></span>

<span data-ttu-id="39708-318">Die Methode **marblemazemain:: Loaddeferredresources** lädt die Gitterdaten nach dem Laden der Vertex- und Pixel-Shader.</span><span class="sxs-lookup"><span data-stu-id="39708-318">The **MarbleMazeMain::LoadDeferredResources** method loads mesh data after it loads the vertex and pixel shaders.</span></span> <span data-ttu-id="39708-319">Bei einem Gitter handelt es sich um eine Sammlung von Vertex-Daten, die oftmals Informationen wie Positionen, Normale, Farben, Materialien und Texturkoordinaten enthält.</span><span class="sxs-lookup"><span data-stu-id="39708-319">A mesh is a collection of vertex data that often includes information such as positions, normal data, colors, materials, and texture coordinates.</span></span> <span data-ttu-id="39708-320">Gitter werden normalerweise in 3D authoring-Software in erstellt und verwaltet Dateien, die vom Anwendungscode separiert sind.</span><span class="sxs-lookup"><span data-stu-id="39708-320">Meshes are typically created in 3D authoring software and maintained in files that are separate from application code.</span></span> <span data-ttu-id="39708-321">Die Kugel und das Labyrinth sind zwei Beispiele für Gitter, die im Spiel verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="39708-321">The marble and the maze are two examples of meshes that the game uses.</span></span>

<span data-ttu-id="39708-322">Marble Maze verwendet die **SDKMesh**-Klasse zum Verwalten von Gittern.</span><span class="sxs-lookup"><span data-stu-id="39708-322">Marble Maze uses the **SDKMesh** class to manage meshes.</span></span> <span data-ttu-id="39708-323">Diese Klasse wird in **"sdkmesh.h"** deklariert.</span><span class="sxs-lookup"><span data-stu-id="39708-323">This class is declared in **SDKMesh.h**.</span></span> <span data-ttu-id="39708-324">**SDKMesh** stellt Methoden zum Laden, Rendern und Löschen von Gitterdaten bereit.</span><span class="sxs-lookup"><span data-stu-id="39708-324">**SDKMesh** provides methods to load, render, and destroy mesh data.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="39708-325">Marble Maze verwendet das SDK-Mesh-Format und die **SDKMesh** -Klasse nur zur Veranschaulichung enthält.</span><span class="sxs-lookup"><span data-stu-id="39708-325">Marble Maze uses the SDK-Mesh format and provides the **SDKMesh** class for illustration only.</span></span> <span data-ttu-id="39708-326">Obwohl das SDK-Mesh-Format hilfreich zum Lernen und Erstellen von Prototypen ist, handelt es sich dabei um ein sehr einfaches Format, das die Anforderungen der meisten Spielentwicklungen möglicherweise nicht erfüllt.</span><span class="sxs-lookup"><span data-stu-id="39708-326">Although the SDK-Mesh format is useful for learning, and for creating prototypes, it is a very basic format that might not meet the requirements of most game development.</span></span> <span data-ttu-id="39708-327">Es wird empfohlen, ein Gitterformat zu verwenden, das die spezifischen Anforderungen Ihres Spiels erfüllt.</span><span class="sxs-lookup"><span data-stu-id="39708-327">We recommend that you use a mesh format that meets the specific requirements of your game.</span></span>

 

<span data-ttu-id="39708-328">Das folgende Beispiel zeigt, wie die **marblemazemain:: Loaddeferredresources** -Methode die **sdkmesh:: Create** -Methode zum Laden von Gitterdaten für das Labyrinth und die Kugel verwendet.</span><span class="sxs-lookup"><span data-stu-id="39708-328">The following example shows how the **MarbleMazeMain::LoadDeferredResources** method uses the **SDKMesh::Create** method to load mesh data for the maze and for the ball.</span></span>

```cpp
// Load the meshes.
DX::ThrowIfFailed(
    m_mazeMesh.Create(
        m_deviceResources->GetD3DDevice(),
        L"Media\\Models\\maze1.sdkmesh",
        false
        )
    );

DX::ThrowIfFailed(
    m_marbleMesh.Create(
        m_deviceResources->GetD3DDevice(),
        L"Media\\Models\\marble2.sdkmesh",
        false
        )
    );
```

###  <a name="loading-collision-data"></a><span data-ttu-id="39708-329">Laden von Kollisionsdaten</span><span class="sxs-lookup"><span data-stu-id="39708-329">Loading collision data</span></span>

<span data-ttu-id="39708-330">Obwohl der Schwerpunkt dieses Abschnitts nicht darauf liegt, wie Marble Maze die physikalische Simulation zwischen der Kugel und dem Labyrinth implementiert, gilt es zu beachten, dass die Gittergeometrie für das physikalische System beim Laden der Gitter gelesen wird.</span><span class="sxs-lookup"><span data-stu-id="39708-330">Although this section does not focus on how Marble Maze implements the physics simulation between the marble and the maze, note that mesh geometry for the physics system is read when the meshes are loaded.</span></span>

```cpp
// Extract mesh geometry for the physics system.
DX::ThrowIfFailed(
    ExtractTrianglesFromMesh(
        m_mazeMesh,
        "Mesh_walls",
        m_collision.m_wallTriList
        )
    );

DX::ThrowIfFailed(
    ExtractTrianglesFromMesh(
        m_mazeMesh,
        "Mesh_Floor",
        m_collision.m_groundTriList
        )
    );

DX::ThrowIfFailed(
    ExtractTrianglesFromMesh(
        m_mazeMesh,
        "Mesh_floorSides",
        m_collision.m_floorTriList
        )
    );

m_physics.SetCollision(&m_collision);
float radius = m_marbleMesh.GetMeshBoundingBoxExtents(0).x / 2;
m_physics.SetRadius(radius);
```

<span data-ttu-id="39708-331">Die Möglichkeit, dass Sie kollisionsdaten größtenteils laden, hängt von der Laufzeit-Format, das Sie verwenden.</span><span class="sxs-lookup"><span data-stu-id="39708-331">The way that you load collision data largely depends on the run-time format that you use.</span></span> <span data-ttu-id="39708-332">Weitere Informationen dazu, wie Marble Maze die kollisionsgeometrie aus einer SDK-Mesh-Datei lädt finden Sie unter der **MarbleMazeMain::ExtractTrianglesFromMesh** -Methode im Quellcode.</span><span class="sxs-lookup"><span data-stu-id="39708-332">For more information about how Marble Maze loads the collision geometry from an SDK-Mesh file, see the **MarbleMazeMain::ExtractTrianglesFromMesh** method in the source code.</span></span>

## <a name="updating-game-state"></a><span data-ttu-id="39708-333">Aktualisieren des Spielzustands</span><span class="sxs-lookup"><span data-stu-id="39708-333">Updating game state</span></span>


<span data-ttu-id="39708-334">Marble Maze separiert die Spiellogik von der Renderlogik, indem zunächst alle Szenenobjekte vor dem Rendern aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="39708-334">Marble Maze separates game logic from rendering logic by first updating all scene objects before rendering them.</span></span>

<span data-ttu-id="39708-335">[Marble Maze-Anwendungsstruktur](marble-maze-application-structure.md) wird die hauptspielschleife beschrieben.</span><span class="sxs-lookup"><span data-stu-id="39708-335">[Marble Maze application structure](marble-maze-application-structure.md) describes the main game loop.</span></span> <span data-ttu-id="39708-336">Die Aktualisierung der Szene, die Bestandteil der Spielschleife ist, erfolgt nach dem Verarbeiten von Windows-Ereignissen und Eingaben und vor dem Rendern der Szene.</span><span class="sxs-lookup"><span data-stu-id="39708-336">Updating the scene, which is part of the game loop, happens after Windows events and input are processed and before the scene is rendered.</span></span> <span data-ttu-id="39708-337">Die **marblemazemain:: Update** -Methode übernimmt die Aktualisierung der UI und das Spiel.</span><span class="sxs-lookup"><span data-stu-id="39708-337">The **MarbleMazeMain::Update** method handles the update of the UI and the game.</span></span>

### <a name="updating-the-user-interface"></a><span data-ttu-id="39708-338">Aktualisieren der Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="39708-338">Updating the user interface</span></span>

<span data-ttu-id="39708-339">Die **marblemazemain:: Update** -Methode ruft die **userinterface:: Update** -Methode, um den Zustand der Benutzeroberfläche zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="39708-339">The **MarbleMazeMain::Update** method calls the **UserInterface::Update** method to update the state of the UI.</span></span>

```cpp
UserInterface::GetInstance().Update(
    static_cast<float>(m_timer.GetTotalSeconds()), 
    static_cast<float>(m_timer.GetElapsedSeconds()));
```

<span data-ttu-id="39708-340">Die **UserInterface::Update**-Methode aktualisiert jedes Element in der UI-Sammlung.</span><span class="sxs-lookup"><span data-stu-id="39708-340">The **UserInterface::Update** method updates each element in the UI collection.</span></span>

```cpp
void UserInterface::Update(float timeTotal, float timeDelta)
{
    for (auto iter = m_elements.begin(); iter != m_elements.end(); ++iter)
    {
        (*iter)->Update(timeTotal, timeDelta);
    }
}
```

<span data-ttu-id="39708-341">**ElementBase** (definiert in **UserInterface.h**) abgeleitete Klassen implementieren die **Update** -Methode zum Ausführen spezifischer Verhalten.</span><span class="sxs-lookup"><span data-stu-id="39708-341">Classes that derive from **ElementBase** (defined in **UserInterface.h**) implement the **Update** method to perform specific behaviors.</span></span> <span data-ttu-id="39708-342">Die **StopwatchTimer::Update**-Methode aktualisiert beispielsweise die abgelaufene Zeit anhand der bereitgestellten Menge und aktualisiert den später angezeigten Text.</span><span class="sxs-lookup"><span data-stu-id="39708-342">For example, the **StopwatchTimer::Update** method updates the elapsed time by the provided amount and updates the text that it later displays.</span></span>

```cpp
void StopwatchTimer::Update(float timeTotal, float timeDelta)
{
    if (m_active)
    {
        m_elapsedTime += timeDelta;

        WCHAR buffer[16];
        GetFormattedTime(buffer);
        SetText(buffer);
    }

    TextElement::Update(timeTotal, timeDelta);
}
```

###  <a name="updating-the-scene"></a><span data-ttu-id="39708-343">Aktualisieren der Szene</span><span class="sxs-lookup"><span data-stu-id="39708-343">Updating the scene</span></span>

<span data-ttu-id="39708-344">Die **marblemazemain:: Update** -Methode aktualisiert das Spiel basierend auf den aktuellen Zustand des Computers Zustand (die **GameState**, in **M_gameState**gespeichert).</span><span class="sxs-lookup"><span data-stu-id="39708-344">The **MarbleMazeMain::Update** method updates the game based on the current state of the state machine (the **GameState**, stored in **m_gameState**).</span></span> <span data-ttu-id="39708-345">Wenn das Spiel im aktiven Zustand (**GameState::InGameActive**) befindet, Marble Maze die Kamera, um die Kugel zu verfolgen, updates der ansichtsmatrixteil der Konstantenpuffer, und die physikalische Simulation aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="39708-345">When the game is in the active state (**GameState::InGameActive**), Marble Maze updates the camera to follow the marble, updates the view matrix part of the constant buffers, and updates the physics simulation.</span></span>

<span data-ttu-id="39708-346">Das folgende Beispiel zeigt, wie die **marblemazemain:: Update** -Methode die Position der Kamera aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="39708-346">The following example shows how the **MarbleMazeMain::Update** method updates the position of the camera.</span></span> <span data-ttu-id="39708-347">Marble Maze verwendet die **m\_resetCamera**-Variable für die Kennzeichnung, dass die Kamera für die Anordnung direkt über der Kugel zurückgesetzt werden muss.</span><span class="sxs-lookup"><span data-stu-id="39708-347">Marble Maze uses the **m\_resetCamera** variable to flag that the camera must be reset to be located directly above the marble.</span></span> <span data-ttu-id="39708-348">Die Kamera wird zurückgesetzt, wenn das Spiel startet oder die Kugel durch das Labyrinth fällt.</span><span class="sxs-lookup"><span data-stu-id="39708-348">The camera is reset when the game starts or the marble falls through the maze.</span></span> <span data-ttu-id="39708-349">Wenn das Hauptmenü oder die Highscoreanzeige aktiv ist, wird die Kamera auf eine konstante Position festgelegt.</span><span class="sxs-lookup"><span data-stu-id="39708-349">When the main menu or high score display screen is active, the camera is set at a constant location.</span></span> <span data-ttu-id="39708-350">Andernfalls verwendet Marble Maze den *timeDelta*-Parameter zum Interpolieren der Kameraposition zwischen den Ist- und Zielpositionen.</span><span class="sxs-lookup"><span data-stu-id="39708-350">Otherwise, Marble Maze uses the *timeDelta* parameter to interpolate the position of the camera between its current and target positions.</span></span> <span data-ttu-id="39708-351">Die Zielposition befindet sich leicht über und vor der Kugel.</span><span class="sxs-lookup"><span data-stu-id="39708-351">The target position is slightly above and in front of the marble.</span></span> <span data-ttu-id="39708-352">Die Verwendung der abgelaufenen Framezeit ermöglicht der Kamera das schrittweise Folgen oder Verfolgen der Kugel.</span><span class="sxs-lookup"><span data-stu-id="39708-352">Using the elapsed frame time enables the camera to gradually follow, or chase, the marble.</span></span>

```cpp
static float eyeDistance = 200.0f;
static XMFLOAT3A eyePosition = XMFLOAT3A(0, 0, 0);

// Gradually move the camera above the marble.
XMFLOAT3A targetEyePosition;
XMStoreFloat3A(
    &targetEyePosition, 
    XMLoadFloat3A(&marblePosition) - (XMLoadFloat3A(&g) * eyeDistance));

if (m_resetCamera)
{
    eyePosition = targetEyePosition;
    m_resetCamera = false;
}
else
{
    XMStoreFloat3A(
        &eyePosition, 
        XMLoadFloat3A(&eyePosition) 
            + ((XMLoadFloat3A(&targetEyePosition) - XMLoadFloat3A(&eyePosition)) 
                * min(1, static_cast<float>(m_timer.GetElapsedSeconds()) * 8)
            )
    );
}

// Look at the marble. 
if ((m_gameState == GameState::MainMenu) || (m_gameState == GameState::HighScoreDisplay))
{
    // Override camera position for menus.
    XMStoreFloat3A(
        &eyePosition, 
        XMLoadFloat3A(&marblePosition) + XMVectorSet(75.0f, -150.0f, -75.0f, 0.0f));

    m_camera->SetViewParameters(
        eyePosition, 
        marblePosition, 
        XMFLOAT3(0.0f, 0.0f, -1.0f));
}
else
{
    m_camera->SetViewParameters(eyePosition, marblePosition, XMFLOAT3(0.0f, 1.0f, 0.0f));
}
```

<span data-ttu-id="39708-353">Das folgende Beispiel zeigt, wie die **marblemazemain:: Update** -Methode die Konstantenpuffer für die Kugel und das Labyrinth aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="39708-353">The following example shows how the **MarbleMazeMain::Update** method updates the constant buffers for the marble and the maze.</span></span> <span data-ttu-id="39708-354">Die Modell- oder Weltmatrix des Labyrinths bleibt immer die Identitätsmatrix.</span><span class="sxs-lookup"><span data-stu-id="39708-354">The maze’s model, or world, matrix always remains the identity matrix.</span></span> <span data-ttu-id="39708-355">Außer der Hauptdiagonale, deren Elemente alle Eins lauten, handelt es sich bei der Identitätsmatrix um eine Quadratmatrix, die aus Nullen besteht.</span><span class="sxs-lookup"><span data-stu-id="39708-355">Except for the main diagonal, whose elements are all ones, the identity matrix is a square matrix composed of zeros.</span></span> <span data-ttu-id="39708-356">Die Modellmatrix der Kugel basiert auf der zugehörigen Positionsmatrix multipliziert mit der zugehörigen Rotationsmatrix.</span><span class="sxs-lookup"><span data-stu-id="39708-356">The marble’s model matrix is based on its position matrix times its rotation matrix.</span></span>

```cpp
// Update the model matrices based on the simulation.
XMStoreFloat4x4(&m_mazeConstantBufferData.model, XMMatrixIdentity());

XMStoreFloat4x4(
    &m_marbleConstantBufferData.model, 
    XMMatrixTranspose(
        XMMatrixMultiply(
            marbleRotationMatrix, 
            XMMatrixTranslationFromVector(XMLoadFloat3A(&marblePosition))
        )
    )
);

// Update the view matrix based on the camera.
XMFLOAT4X4 view;
m_camera->GetViewMatrix(&view);
m_mazeConstantBufferData.view = view;
m_marbleConstantBufferData.view = view;
```

<span data-ttu-id="39708-357">Informationen dazu, wie die **marblemazemain:: Update** -Methode Benutzereingabe liest und die Bewegung der Kugel simuliert finden Sie unter [Hinzufügen von Eingaben und Interaktivität zum Marble Maze-Beispiel](adding-input-and-interactivity-to-the-marble-maze-sample.md).</span><span class="sxs-lookup"><span data-stu-id="39708-357">For information about how the **MarbleMazeMain::Update** method reads user input and simulates the motion of the marble, see [Adding input and interactivity to the Marble Maze sample](adding-input-and-interactivity-to-the-marble-maze-sample.md).</span></span>

## <a name="rendering-the-scene"></a><span data-ttu-id="39708-358">Rendern der Szene</span><span class="sxs-lookup"><span data-stu-id="39708-358">Rendering the scene</span></span>


<span data-ttu-id="39708-359">Das Rendern einer Szene umfasst normalerweise die folgenden Schritte.</span><span class="sxs-lookup"><span data-stu-id="39708-359">When a scene is rendered, these steps are typically included.</span></span>

1.  <span data-ttu-id="39708-360">Festlegen des Tiefenschablonenpuffers für das aktuelle Renderziel.</span><span class="sxs-lookup"><span data-stu-id="39708-360">Set the current render target depth-stencil buffer.</span></span>
2.  <span data-ttu-id="39708-361">Löschen der Render- und Schablonenansichten.</span><span class="sxs-lookup"><span data-stu-id="39708-361">Clear the render and stencil views.</span></span>
3.  <span data-ttu-id="39708-362">Vorbereiten der Vertex- und Pixel-Shader für die Zeichnung.</span><span class="sxs-lookup"><span data-stu-id="39708-362">Prepare the vertex and pixel shaders for drawing.</span></span>
4.  <span data-ttu-id="39708-363">Die 3D-Objekte in der Szene zu rendern.</span><span class="sxs-lookup"><span data-stu-id="39708-363">Render the 3D objects in the scene.</span></span>
5.  <span data-ttu-id="39708-364">Rendern Sie 2D-Objekte, die vor der Szene angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="39708-364">Render any 2D object that you want to appear in front of the scene.</span></span>
6.  <span data-ttu-id="39708-365">Darstellen des gerenderten Bilds auf dem Monitor.</span><span class="sxs-lookup"><span data-stu-id="39708-365">Present the rendered image to the monitor.</span></span>

<span data-ttu-id="39708-366">Die **marblemazemain:: Render** -Methode bindet das Renderziel und tiefenschablonen anzeigt, die tiefenschablonenansichten, zeichnet die Szene und zeichnet dann die Überlagerung.</span><span class="sxs-lookup"><span data-stu-id="39708-366">The **MarbleMazeMain::Render** method binds the render target and depth stencil views, clears those views, draws the scene, and then draws the overlay.</span></span>

###  <a name="preparing-the-render-targets"></a><span data-ttu-id="39708-367">Vorbereiten der Renderziele</span><span class="sxs-lookup"><span data-stu-id="39708-367">Preparing the render targets</span></span>

<span data-ttu-id="39708-368">Vor dem Rendern der Szene müssen Sie den Tiefenschablonenpuffer für das aktuelle Renderziel festlegen.</span><span class="sxs-lookup"><span data-stu-id="39708-368">Before you render your scene, you must set the current render target depth-stencil buffer.</span></span> <span data-ttu-id="39708-369">Wenn nicht feststeht, dass die Szene über alle Bildschirmpixel gezeichnet wird, löschen Sie auch die Render- und Schablonenansichten.</span><span class="sxs-lookup"><span data-stu-id="39708-369">If your scene is not guaranteed to draw over every pixel on the screen, also clear the render and stencil views.</span></span> <span data-ttu-id="39708-370">Marble Maze löscht die Render- und Schablonenansichten in jedem Frame, um sicherzustellen, dass keine sichtbaren Artefakte aus dem vorherigen Frame vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="39708-370">Marble Maze clears the render and stencil views on every frame to ensure that there are no visible artifacts from the previous frame.</span></span>

<span data-ttu-id="39708-371">Das folgende Beispiel zeigt, wie die **marblemazemain:: Render** -Methode die [id3d11devicecontext:: omsetrendertargets](https://msdn.microsoft.com/library/windows/desktop/ff476464) -Methode, um das Renderingziel und die Tiefe/Schablone-Puffer festlegen, wie die aktuelle aufruft.</span><span class="sxs-lookup"><span data-stu-id="39708-371">The following example shows how the **MarbleMazeMain::Render** method calls the [ID3D11DeviceContext::OMSetRenderTargets](https://msdn.microsoft.com/library/windows/desktop/ff476464) method to set the render target and the depth-stencil buffer as the current ones.</span></span>

```cpp
auto context = m_deviceResources->GetD3DDeviceContext();

// Reset the viewport to target the whole screen.
auto viewport = m_deviceResources->GetScreenViewport();
context->RSSetViewports(1, &viewport);

// Reset render targets to the screen.
ID3D11RenderTargetView *const targets[1] = 
    { m_deviceResources->GetBackBufferRenderTargetView() };

context->OMSetRenderTargets(1, targets, m_deviceResources->GetDepthStencilView());

// Clear the back buffer and depth stencil view.
context->ClearRenderTargetView(
    m_deviceResources->GetBackBufferRenderTargetView(), 
    DirectX::Colors::Black);

context->ClearDepthStencilView(
    m_deviceResources->GetDepthStencilView(), 
    D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 
    1.0f, 
    0);
```

<span data-ttu-id="39708-372">Die [ID3D11RenderTargetView](https://msdn.microsoft.com/library/windows/desktop/ff476582)-Schnittstelle und die [ID3D11DepthStencilView](https://msdn.microsoft.com/library/windows/desktop/ff476377)-Schnittstelle unterstützen den Texturansichtsmechanismus, der von Direct3D 10 und höher bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="39708-372">The [ID3D11RenderTargetView](https://msdn.microsoft.com/library/windows/desktop/ff476582) and [ID3D11DepthStencilView](https://msdn.microsoft.com/library/windows/desktop/ff476377) interfaces support the texture view mechanism that is provided by Direct3D 10 and later.</span></span> <span data-ttu-id="39708-373">Weitere Informationen zu Texturansichten finden Sie unter [Texturansichten (Direct3D 10)](https://msdn.microsoft.com/library/windows/desktop/bb205128).</span><span class="sxs-lookup"><span data-stu-id="39708-373">For more information about texture views, see [Texture Views (Direct3D 10)](https://msdn.microsoft.com/library/windows/desktop/bb205128).</span></span> <span data-ttu-id="39708-374">Die [OMSetRenderTargets](https://msdn.microsoft.com/library/windows/desktop/ff476464)-Methode bereitet die Ausgabezusammenführungsphase der Direct3D-Pipeline vor.</span><span class="sxs-lookup"><span data-stu-id="39708-374">The [OMSetRenderTargets](https://msdn.microsoft.com/library/windows/desktop/ff476464) method prepares the output-merger stage of the Direct3D pipeline.</span></span> <span data-ttu-id="39708-375">Weitere Informationen zur Ausgabezusammenführungsphase finden Sie unter [Ausgabezusammenführungsphase](https://msdn.microsoft.com/library/windows/desktop/bb205120).</span><span class="sxs-lookup"><span data-stu-id="39708-375">For more information about the output-merger stage, see [Output-Merger Stage](https://msdn.microsoft.com/library/windows/desktop/bb205120).</span></span>

### <a name="preparing-the-vertex-and-pixel-shaders"></a><span data-ttu-id="39708-376">Vorbereiten der Vertex- und Pixel-Shader</span><span class="sxs-lookup"><span data-stu-id="39708-376">Preparing the vertex and pixel shaders</span></span>

<span data-ttu-id="39708-377">Führen Sie vor dem Rendern der Szenenobjekte die folgenden Schritte aus, um die Vertex- und Pixel-Shader für die Zeichnung vorzubereiten:</span><span class="sxs-lookup"><span data-stu-id="39708-377">Before you render the scene objects, perform the following steps to prepare the vertex and pixel shaders for drawing:</span></span>

1.  <span data-ttu-id="39708-378">Legen Sie das Shader-Eingabelayout als aktuelles Layout fest.</span><span class="sxs-lookup"><span data-stu-id="39708-378">Set the shader input layout as the current layout.</span></span>
2.  <span data-ttu-id="39708-379">Legen Sie die Vertex und Pixel-Shader als aktuelle Shader fest.</span><span class="sxs-lookup"><span data-stu-id="39708-379">Set the vertex and pixel shaders as the current shaders.</span></span>
3.  <span data-ttu-id="39708-380">Aktualisieren Sie die Konstantenpuffer mit Daten, die Sie an die Shader übergeben müssen.</span><span class="sxs-lookup"><span data-stu-id="39708-380">Update any constant buffers with data that you have to pass to the shaders.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="39708-381">Marble Maze verwendet Vertex- und Pixel-Shader für alle 3D-Objekte.</span><span class="sxs-lookup"><span data-stu-id="39708-381">Marble Maze uses one pair of vertex and pixel shaders for all 3D objects.</span></span> <span data-ttu-id="39708-382">Wenn für Ihr Spiel mehrere Shader-Paare verwendet werden, müssen Sie diese Schritte immer dann ausführen, wenn Sie Objekte zeichnen, für die verschiedene Shader verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="39708-382">If your game uses more than one pair of shaders, you must perform these steps each time you draw objects that use different shaders.</span></span> <span data-ttu-id="39708-383">Zur Reduzierung des Aufwands bezüglich der Änderung des Shader-Zustands wird empfohlen, die Renderaufrufe für alle Objekte zu gruppieren, die dieselben Shader verwenden.</span><span class="sxs-lookup"><span data-stu-id="39708-383">To reduce the overhead that is associated with changing the shader state, we recommend that you group render calls for all objects that use the same shaders.</span></span>

 

<span data-ttu-id="39708-384">Im Abschnitt [Laden von Shadern](#loading-shaders) in diesem Dokument wird beschrieben, wie das Eingabelayout beim Erstellen des Vertex-Shaders erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="39708-384">The section [Loading shaders](#loading-shaders) in this document describes how the input layout is created when the vertex shader is created.</span></span> <span data-ttu-id="39708-385">Das folgende Beispiel zeigt, wie die **marblemazemain:: Render** -Methode die [id3d11devicecontext:: iasetinputlayout](https://msdn.microsoft.com/library/windows/desktop/ff476454) -Methode verwendet, um dieses Layout als aktuelles Layout festzulegen.</span><span class="sxs-lookup"><span data-stu-id="39708-385">The following example shows how the **MarbleMazeMain::Render** method uses the [ID3D11DeviceContext::IASetInputLayout](https://msdn.microsoft.com/library/windows/desktop/ff476454) method to set this layout as the current layout.</span></span>

```cpp
m_deviceResources->GetD3DDeviceContext()->IASetInputLayout(m_inputLayout.Get());
```

<span data-ttu-id="39708-386">Das folgende Beispiel zeigt, wie die **marblemazemain:: Render** -Methode der [id3d11devicecontext:: vssetshader](https://msdn.microsoft.com/library/windows/desktop/ff476493) und [id3d11devicecontext:: pssetshader](https://msdn.microsoft.com/library/windows/desktop/ff476472) -Methode verwendet, um die Vertex- und Pixel-Shader als aktuelle Shader festzulegen, bzw..</span><span class="sxs-lookup"><span data-stu-id="39708-386">The following example shows how the **MarbleMazeMain::Render** method uses the [ID3D11DeviceContext::VSSetShader](https://msdn.microsoft.com/library/windows/desktop/ff476493) and [ID3D11DeviceContext::PSSetShader](https://msdn.microsoft.com/library/windows/desktop/ff476472) methods to set the vertex and pixel shaders as the current shaders, respectively.</span></span>

```cpp
// Set the vertex shader stage state.
m_deviceResources->GetD3DDeviceContext()->VSSetShader(
    m_vertexShader.Get(),   // use this vertex shader
    nullptr,                // don't use shader linkage
    0);                     // don't use shader linkage

m_deviceResources->GetD3DDeviceContext()->PSSetShader(
    m_pixelShader.Get(),    // use this pixel shader
    nullptr,                // don't use shader linkage
    0);                     // don't use shader linkage

m_deviceResources->GetD3DDeviceContext()->PSSetSamplers(
    0,                          // starting at the first sampler slot
    1,                          // set one sampler binding
    m_sampler.GetAddressOf());  // to use this sampler
```

<span data-ttu-id="39708-387">Nach **marblemazemain:: Render** die Shader und das zugehörige eingabelayout festlegt, verwendet es die [id3d11devicecontext:: updatesubresource](https://msdn.microsoft.com/library/windows/desktop/ff476486) -Methode, um den Konstantenpuffer mit den Modell-, Ansichts- und projektionsmatrizen für das Labyrinth zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="39708-387">After **MarbleMazeMain::Render** sets the shaders and their input layout, it uses the [ID3D11DeviceContext::UpdateSubresource](https://msdn.microsoft.com/library/windows/desktop/ff476486) method to update the constant buffer with the model, view, and projection matrices for the maze.</span></span> <span data-ttu-id="39708-388">Die **UpdateSubresource**-Methode kopiert die Matrixdaten aus dem CPU-Speicher in den GPU-Speicher.</span><span class="sxs-lookup"><span data-stu-id="39708-388">The **UpdateSubresource** method copies the matrix data from CPU memory to GPU memory.</span></span> <span data-ttu-id="39708-389">Denken Sie daran, dass die Modell- und ansichtskomponenten der **ConstantBuffer** -Struktur in der Methode **marblemazemain:: Update** aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="39708-389">Recall that the model and view components of the **ConstantBuffer** structure are updated in the **MarbleMazeMain::Update** method.</span></span> <span data-ttu-id="39708-390">Anschließend ruft die **marblemazemain:: Render** -Methode die [id3d11devicecontext:: vssetconstantbuffers](https://msdn.microsoft.com/library/windows/desktop/ff476491) und [id3d11devicecontext:: pssetconstantbuffers](https://msdn.microsoft.com/library/windows/desktop/ff476470) -Methoden, um diesen Konstantenpuffer als aktuellen Puffer festzulegen.</span><span class="sxs-lookup"><span data-stu-id="39708-390">The **MarbleMazeMain::Render** method then calls the [ID3D11DeviceContext::VSSetConstantBuffers](https://msdn.microsoft.com/library/windows/desktop/ff476491) and [ID3D11DeviceContext::PSSetConstantBuffers](https://msdn.microsoft.com/library/windows/desktop/ff476470) methods to set this constant buffer as the current one.</span></span>

```cpp
// Update the constant buffer with the new data.
m_deviceResources->GetD3DDeviceContext()->UpdateSubresource(
    m_constantBuffer.Get(),
    0,
    nullptr,
    &m_mazeConstantBufferData,
    0,
    0);

m_deviceResources->GetD3DDeviceContext()->VSSetConstantBuffers(
    0,                                  // starting at the first constant buffer slot
    1,                                  // set one constant buffer binding
    m_constantBuffer.GetAddressOf());   // to use this buffer

m_deviceResources->GetD3DDeviceContext()->PSSetConstantBuffers(
    0,                                  // starting at the first constant buffer slot
    1,                                  // set one constant buffer binding
    m_constantBuffer.GetAddressOf());   // to use this buffer
```

<span data-ttu-id="39708-391">Die **marblemazemain:: Render** -Methode führt ähnliche Schritte aus, um die zu rendernde Kugel vorzubereiten.</span><span class="sxs-lookup"><span data-stu-id="39708-391">The **MarbleMazeMain::Render** method performs similar steps to prepare the marble to be rendered.</span></span>

### <a name="rendering-the-maze-and-the-marble"></a><span data-ttu-id="39708-392">Rendern des Labyrinths und der Kugel</span><span class="sxs-lookup"><span data-stu-id="39708-392">Rendering the maze and the marble</span></span>

<span data-ttu-id="39708-393">Nachdem Sie die aktuellen Shader aktiviert haben, können Sie die Szenenobjekte zeichnen.</span><span class="sxs-lookup"><span data-stu-id="39708-393">After you activate the current shaders, you can draw your scene objects.</span></span> <span data-ttu-id="39708-394">Die **marblemazemain:: Render** -Methode ruft die **sdkmesh:: Render** -Methode, um das Labyrinth-Gitter zu rendern.</span><span class="sxs-lookup"><span data-stu-id="39708-394">The **MarbleMazeMain::Render** method calls the **SDKMesh::Render** method to render the maze mesh.</span></span>

```cpp
m_mazeMesh.Render(
    m_deviceResources->GetD3DDeviceContext(), 
    0, 
    INVALID_SAMPLER_SLOT, 
    INVALID_SAMPLER_SLOT);
```

<span data-ttu-id="39708-395">Die **marblemazemain:: Render** -Methode führt ähnliche Schritte aus, um die Kugel zu rendern.</span><span class="sxs-lookup"><span data-stu-id="39708-395">The **MarbleMazeMain::Render** method performs similar steps to render the marble.</span></span>

<span data-ttu-id="39708-396">Wie bereits in diesem Dokument erwähnt wurde, wird die **SDKMesh**-Klasse zu Demonstrationszwecken bereitgestellt. Sie wird jedoch nicht für die Verwendung in einem Spiel in Produktionsqualität empfohlen.</span><span class="sxs-lookup"><span data-stu-id="39708-396">As mentioned earlier in this document, the **SDKMesh** class is provided for demonstration purposes, but we do not recommend it for use in a production-quality game.</span></span> <span data-ttu-id="39708-397">Beachten Sie jedoch, dass die **SDKMesh::RenderMesh**-Methode, die von **SDKMesh::Render** aufgerufen wird, die [ID3D11DeviceContext::IASetVertexBuffers](https://msdn.microsoft.com/library/windows/desktop/ff476456)-Methode und die [ID3D11DeviceContext::IASetIndexBuffer](https://msdn.microsoft.com/library/windows/desktop/ff476453)-Methode zum Festlegen der aktuellen Vertex- und Indexpuffer verwendet, mit deren Hilfe das Gitter definiert wird. Die [ID3D11DeviceContext::DrawIndexed](https://msdn.microsoft.com/library/windows/desktop/ff476410)-Methode wird zum Zeichnen der Puffer verwendet.</span><span class="sxs-lookup"><span data-stu-id="39708-397">However, notice that the **SDKMesh::RenderMesh** method, which is called by **SDKMesh::Render**, uses the [ID3D11DeviceContext::IASetVertexBuffers](https://msdn.microsoft.com/library/windows/desktop/ff476456) and [ID3D11DeviceContext::IASetIndexBuffer](https://msdn.microsoft.com/library/windows/desktop/ff476453) methods to set the current vertex and index buffers that define the mesh, and the [ID3D11DeviceContext::DrawIndexed](https://msdn.microsoft.com/library/windows/desktop/ff476410) method to draw the buffers.</span></span> <span data-ttu-id="39708-398">Weitere Informationen zum Arbeiten mit Vertex- und Indexpuffern finden Sie unter [Einführung in Puffer in Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476898).</span><span class="sxs-lookup"><span data-stu-id="39708-398">For more information about how to work with vertex and index buffers, see [Introduction to Buffers in Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476898).</span></span>

### <a name="drawing-the-user-interface-and-overlay"></a><span data-ttu-id="39708-399">Zeichnen der Benutzeroberfläche und Überlagerung</span><span class="sxs-lookup"><span data-stu-id="39708-399">Drawing the user interface and overlay</span></span>

<span data-ttu-id="39708-400">Nach der 3D-Szene Objekte gezeichnet, zeichnet Marble Maze die 2D UI-Elemente, die vor der Szene angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="39708-400">After drawing 3D scene objects, Marble Maze draws the 2D UI elements that appear in front of the scene.</span></span>

<span data-ttu-id="39708-401">Die **marblemazemain:: Render** -Methode endet mit dem Zeichnen der Benutzeroberfläche und der Überlagerung.</span><span class="sxs-lookup"><span data-stu-id="39708-401">The **MarbleMazeMain::Render** method ends by drawing the user interface and the overlay.</span></span>

```cpp
// Draw the user interface and the overlay.
UserInterface::GetInstance().Render(m_deviceResources->GetOrientationTransform2D());

m_deviceResources->GetD3DDeviceContext()->BeginEventInt(L"Render Overlay", 0);
m_sampleOverlay->Render();
m_deviceResources->GetD3DDeviceContext()->EndEvent();
```

<span data-ttu-id="39708-402">Die **UserInterface::Render**-Methode verwendet ein [ID2D1DeviceContext](https://msdn.microsoft.com/library/windows/desktop/hh404479)-Objekt zum Zeichnen der UI-Elemente.</span><span class="sxs-lookup"><span data-stu-id="39708-402">The **UserInterface::Render** method uses an [ID2D1DeviceContext](https://msdn.microsoft.com/library/windows/desktop/hh404479) object to draw the UI elements.</span></span> <span data-ttu-id="39708-403">Diese Methode legt den Zeichnungszustand fest, sie zeichnet alle aktiven UI-Elemente und stellt dann den vorherigen Zeichnungszustand wieder her.</span><span class="sxs-lookup"><span data-stu-id="39708-403">This method sets the drawing state, draws all active UI elements, and then restores the previous drawing state.</span></span>

```cpp
void UserInterface::Render(D2D1::Matrix3x2F orientation2D)
{
    m_d2dContext->SaveDrawingState(m_stateBlock.Get());
    m_d2dContext->BeginDraw();
    m_d2dContext->SetTransform(orientation2D);

    m_d2dContext->SetTextAntialiasMode(D2D1_TEXT_ANTIALIAS_MODE_GRAYSCALE);

    for (auto iter = m_elements.begin(); iter != m_elements.end(); ++iter)
    {
        if ((*iter)->IsVisible())
            (*iter)->Render();
    }

    // We ignore D2DERR_RECREATE_TARGET here. This error indicates that the device
    // is lost. It will be handled during the next call to Present.
    HRESULT hr = m_d2dContext->EndDraw();
    if (hr != D2DERR_RECREATE_TARGET)
    {
        DX::ThrowIfFailed(hr);
    }

    m_d2dContext->RestoreDrawingState(m_stateBlock.Get());
}
```

<span data-ttu-id="39708-404">Die **SampleOverlay::Render**-Methode verwendet eine ähnliche Technik zum Zeichnen der Überlagerungsbitmap.</span><span class="sxs-lookup"><span data-stu-id="39708-404">The **SampleOverlay::Render** method uses a similar technique to draw the overlay bitmap.</span></span>

###  <a name="presenting-the-scene"></a><span data-ttu-id="39708-405">Darstellen der Szene</span><span class="sxs-lookup"><span data-stu-id="39708-405">Presenting the scene</span></span>

<span data-ttu-id="39708-406">Nach dem Zeichnen aller 2D- und 3D-Grafiken szenenobjekte stellt Marble Maze das gerenderte Bild auf dem Monitor dar.</span><span class="sxs-lookup"><span data-stu-id="39708-406">After drawing all 2D and 3D scene objects, Marble Maze presents the rendered image to the monitor.</span></span> <span data-ttu-id="39708-407">Das Spiel synchronisiert die Zeichnung mit der vertikalen Austastung, um sicherzustellen, dass keine Zeit für das Zeichnen von Frames verwendet wird, die letztendlich nie auf dem Bildschirm angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="39708-407">It synchronizes drawing to the vertical blank to ensure that time is not spent time drawing frames that will never be actually shown on the display.</span></span> <span data-ttu-id="39708-408">Marble Maze verarbeitet beim Darstellen der Szene auch Geräteänderungen.</span><span class="sxs-lookup"><span data-stu-id="39708-408">Marble Maze also handles device changes when it presents the scene.</span></span>

<span data-ttu-id="39708-409">Nachdem die **marblemazemain:: Render** -Methode zurückgegeben wird, ruft die spielschleife die **dx** -Methode, um das gerenderte Bild auf dem Monitor senden oder anzeigen.</span><span class="sxs-lookup"><span data-stu-id="39708-409">After the **MarbleMazeMain::Render** method returns, the game loop calls the **DX::DeviceResources::Present** method to send the rendered image to the monitor or display.</span></span> <span data-ttu-id="39708-410">Die **dx** -Methode ruft [idxgiswapchain:: Present](https://msdn.microsoft.com/library/windows/desktop/bb174576) , um den aktuellen Vorgang auszuführen, wie im folgenden Beispiel dargestellt:</span><span class="sxs-lookup"><span data-stu-id="39708-410">The **DX::DeviceResources::Present** method calls [IDXGISwapChain::Present](https://msdn.microsoft.com/library/windows/desktop/bb174576) to perform the present operation, as shown in the following example:</span></span>

```cpp
// The first argument instructs DXGI to block until VSync, putting the application
// to sleep until the next VSync. This ensures we don't waste any cycles rendering
// frames that will never be displayed to the screen.
HRESULT hr = m_swapChain->Present(1, 0);
```

<span data-ttu-id="39708-411">In diesem Beispiel ist **M\_swapChain** ein [IDXGISwapChain1](https://msdn.microsoft.com/library/windows/desktop/hh404631)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="39708-411">In this example, **m\_swapChain** is an [IDXGISwapChain1](https://msdn.microsoft.com/library/windows/desktop/hh404631) object.</span></span> <span data-ttu-id="39708-412">Die Initialisierung dieses Objekts wird im Abschnitt [Initialisieren von Direct3D und Direct2D](#initializing-direct3d-and-direct2d) in diesem Dokument beschrieben.</span><span class="sxs-lookup"><span data-stu-id="39708-412">The initialization of this object is described in the section [Initializing Direct3D and Direct2D](#initializing-direct3d-and-direct2d) in this document.</span></span>

<span data-ttu-id="39708-413">Der erste Parameter für [idxgiswapchain:: Present](https://msdn.microsoft.com/library/windows/desktop/hh446797), *SyncInterval*, gibt die Anzahl der vertikalen Leerzeichen warten soll, bevor der Frame dargestellt wird.</span><span class="sxs-lookup"><span data-stu-id="39708-413">The first parameter to [IDXGISwapChain::Present](https://msdn.microsoft.com/library/windows/desktop/hh446797), *SyncInterval*, specifies the number of vertical blanks to wait before presenting the frame.</span></span> <span data-ttu-id="39708-414">Marble Maze gibt den Wert 1 an, sodass bis zur nächsten vertikalen Austastung gewartet wird.</span><span class="sxs-lookup"><span data-stu-id="39708-414">Marble Maze specifies 1 so that it waits until the next vertical blank.</span></span>

<span data-ttu-id="39708-415">Die [idxgiswapchain:: Present](https://msdn.microsoft.com/library/windows/desktop/bb174576) -Methode gibt einen Fehlercode, der angibt, dass das Gerät entfernt wurde oder ein anderer Fehler aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="39708-415">The [IDXGISwapChain::Present](https://msdn.microsoft.com/library/windows/desktop/bb174576) method returns an error code that indicates that the device was removed or otherwise failed.</span></span> <span data-ttu-id="39708-416">In diesem Fall initialisiert Marble Maze das Gerät erneut.</span><span class="sxs-lookup"><span data-stu-id="39708-416">In this case, Marble Maze reinitializes the device.</span></span>

```cpp
// If the device was removed either by a disconnection or a driver upgrade, we
// must recreate all device resources.
if (hr == DXGI_ERROR_DEVICE_REMOVED)
{
    HandleDeviceLost();
}
else
{
    DX::ThrowIfFailed(hr);
}
```

## <a name="next-steps"></a><span data-ttu-id="39708-417">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="39708-417">Next steps</span></span>


<span data-ttu-id="39708-418">Lesen Sie den Abschnitt [Hinzufügen von Eingaben und Interaktivität zum Marble Maze-Beispiel](adding-input-and-interactivity-to-the-marble-maze-sample.md), um Informationen zu einigen wichtigen Verfahren zu erhalten, die Sie beim Arbeiten mit Eingabegeräten beachten sollten.</span><span class="sxs-lookup"><span data-stu-id="39708-418">Read [Adding input and interactivity to the Marble Maze sample](adding-input-and-interactivity-to-the-marble-maze-sample.md) for information about some of the key practices to keep in mind when you work with input devices.</span></span> <span data-ttu-id="39708-419">In diesem Dokument wird beschrieben, wie Marble Maze Touch, Beschleunigungsmesser, Xbox-Controller und Mauseingabe unterstützt.</span><span class="sxs-lookup"><span data-stu-id="39708-419">This document discusses how Marble Maze supports touch, accelerometer, Xbox controllers, and mouse input.</span></span>

## <a name="related-topics"></a><span data-ttu-id="39708-420">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="39708-420">Related topics</span></span>


* [<span data-ttu-id="39708-421">Hinzufügen von Eingaben und Interaktivität zum Marble Maze-Beispiel</span><span class="sxs-lookup"><span data-stu-id="39708-421">Adding input and interactivity to the Marble Maze sample</span></span>](adding-input-and-interactivity-to-the-marble-maze-sample.md)
* [<span data-ttu-id="39708-422">Marble Maze-Anwendungsstruktur</span><span class="sxs-lookup"><span data-stu-id="39708-422">Marble Maze application structure</span></span>](marble-maze-application-structure.md)
* [<span data-ttu-id="39708-423">Entwickeln von Marble Maze, einem UWP-Spiel in C++ und DirectX</span><span class="sxs-lookup"><span data-stu-id="39708-423">Developing Marble Maze, a UWP game in C++ and DirectX</span></span>](developing-marble-maze-a-windows-store-game-in-cpp-and-directx.md)

 

 




