---
title: Interoperabilität von DirectX und XAML
description: In Ihrem Spiel für die universelle Windows-Plattform (UWP) können Sie eine Kombination aus Extensible Application Markup Language (XAML) und Microsoft DirectX verwenden.
ms.assetid: 0fb2819a-61ed-129d-6564-0b67debf5c6b
ms.date: 02/08/2017
ms.topic: article
keywords: windows10, uwp, Spiele, directx, xaml-interoperabilität
ms.localizationpriority: medium
ms.openlocfilehash: 058a1458f8990e5f70e7ed0ea4ef1a2b5f4a4956
ms.sourcegitcommit: b4c502d69a13340f6e3c887aa3c26ef2aeee9cee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "8466605"
---
# <a name="directx-and-xaml-interop"></a><span data-ttu-id="b14de-104">Interoperabilität von DirectX und XAML</span><span class="sxs-lookup"><span data-stu-id="b14de-104">DirectX and XAML interop</span></span>



<span data-ttu-id="b14de-105">In Spielen oder Apps für die universelle Windows-Plattform (UWP) können Sie eine Kombination aus Extensible Application Markup Language (XAML) und Microsoft DirectX verwenden.</span><span class="sxs-lookup"><span data-stu-id="b14de-105">You can use Extensible Application Markup Language (XAML) and Microsoft DirectX together in your Universal Windows Platform (UWP) game or app.</span></span> <span data-ttu-id="b14de-106">Dank der Kombination von XAML und DirectX können Sie flexible Frameworks für die Benutzeroberflächen erstellen, die mit den über DirectX gerenderten Inhalten kompatibel sind. Dies ist besonders für grafisch aufwendige Apps von Vorteil.</span><span class="sxs-lookup"><span data-stu-id="b14de-106">The combination of XAML and DirectX lets you build flexible user interface frameworks that interop with your DirectX-rendered content, and is particularly useful for graphics-intensive apps.</span></span> <span data-ttu-id="b14de-107">In diesem Thema beschäftigen wir uns mit der Struktur einer UWP-App mit DirectX und gehen auf wichtige Typen ein, die beim Erstellen Ihrer UWP-App für die Zusammenarbeit mit DirectX erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="b14de-107">This topic explains the structure of a UWP app that uses DirectX and identifies the important types to use when building your UWP app to work with DirectX.</span></span>

<span data-ttu-id="b14de-108">Wenn Ihre App hauptsächlich 2-D-Rendering verwendet, empfiehlt sich unter Umständen die Verwendung der [Win2D](https://github.com/microsoft/win2d) Windows-Runtime-Bibliothek.</span><span class="sxs-lookup"><span data-stu-id="b14de-108">If your app mainly focuses on 2D rendering, you may want to use the [Win2D](https://github.com/microsoft/win2d) Windows Runtime library.</span></span> <span data-ttu-id="b14de-109">Diese Bibliothek wird von Microsoft verwaltet und basiert auf den Direct2D-Kerntechnologien.</span><span class="sxs-lookup"><span data-stu-id="b14de-109">This library is maintained by Microsoft and built on top of the core Direct2D technologies.</span></span> <span data-ttu-id="b14de-110">Sie trägt erheblich zur Vereinfachung des Verwendungsmusters für die Implementierung von 2D-Grafik bei und enthält hilfreiche Abstraktionen für einige der in diesem Dokument beschriebenen Techniken.</span><span class="sxs-lookup"><span data-stu-id="b14de-110">It greatly simplifies the usage pattern to implement 2D graphics and includes helpful abstractions for some of the techniques described in this document.</span></span> <span data-ttu-id="b14de-111">Ausführlichere Informationen finden Sie auf der Projektseite.</span><span class="sxs-lookup"><span data-stu-id="b14de-111">See the project page for more details.</span></span> <span data-ttu-id="b14de-112">Bei diesem Dokument handelt es sich um einen Leitfaden für App-Entwickler, die sich *gegen* die Verwendung von Win2D entschieden haben.</span><span class="sxs-lookup"><span data-stu-id="b14de-112">This document covers guidance for app developers who choose *not* to use Win2D.</span></span>

> <span data-ttu-id="b14de-113">**Hinweis:** DirectX-APIs sind nicht als Windows-Runtime-Typen definiert, verwenden Sie normalerweise für VisualC++-komponentenerweiterungen (C++ / CX) XAML-UWP-Komponenten zu entwickeln, die mit DirectX kompatible.</span><span class="sxs-lookup"><span data-stu-id="b14de-113">**Note**DirectX APIs are not defined as Windows Runtime types, so you typically use VisualC++ component extensions (C++/CX) to develop XAML UWP components that interoperate with DirectX.</span></span> <span data-ttu-id="b14de-114">Sie können UWP-DirectX-Apps auch mit C# und XAML erstellen, indem Sie die DirectX-Aufrufe in eine separate Windows-Runtime-Metadatendatei einschließen.</span><span class="sxs-lookup"><span data-stu-id="b14de-114">Also, you can create a UWP app with C# and XAML that uses DirectX, if you wrap the DirectX calls in a separate Windows Runtime metadata file.</span></span>

 

## <a name="xaml-and-directx"></a><span data-ttu-id="b14de-115">XAML und DirectX</span><span class="sxs-lookup"><span data-stu-id="b14de-115">XAML and DirectX</span></span>

<span data-ttu-id="b14de-116">DirectX bietet mit Direct2D und Microsoft Direct3D zwei leistungsstarke Bibliotheken für 2D- und 3D-Grafiken.</span><span class="sxs-lookup"><span data-stu-id="b14de-116">DirectX provides two powerful libraries for 2D and 3D graphics: Direct2D and Microsoft Direct3D.</span></span> <span data-ttu-id="b14de-117">Obwohl XAML grundlegende 2D-Grundtypen und -Effekte unterstützt, erfordern zahlreiche Apps, wie Modellierungs-Apps und Spiele, eine komplexere Grafikunterstützung.</span><span class="sxs-lookup"><span data-stu-id="b14de-117">Although XAML provides support for basic 2D primitives and effects, many apps, such as modeling and gaming, need more complex graphics support.</span></span> <span data-ttu-id="b14de-118">In diesen Fällen können Sie Grafiken teilweise oder vollständig mit Direct2D und Direct3D rendern und XAML für alles andere verwenden.</span><span class="sxs-lookup"><span data-stu-id="b14de-118">For these, you can use Direct2D and Direct3D to render part or all of the graphics and use XAML for everything else.</span></span>

<span data-ttu-id="b14de-119">Wenn Sie eine benutzerdefinierte Interoperabilität zwischen XAML und DirectX implementieren möchten, müssen Sie mit den beiden folgenden Konzepten vertraut sein:</span><span class="sxs-lookup"><span data-stu-id="b14de-119">If you are implementing custom XAML and DirectX interop, you need to know these two concepts:</span></span>

-   <span data-ttu-id="b14de-120">Bei gemeinsam genutzten Flächen (Shared Surfaces) handelt es sich um Anzeigebereiche bestimmter Größe, die von XAML definiert werden. In diesen Bereichen können Sie indirekt mit DirectX und [Windows::UI::Xaml::Media::ImageSource](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.imagesource.aspx)-Typen zeichnen.</span><span class="sxs-lookup"><span data-stu-id="b14de-120">Shared surfaces are sized regions of the display, defined by XAML, that you can use DirectX to draw into indirectly, using [Windows::UI::Xaml::Media::ImageSource](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.imagesource.aspx) types.</span></span> <span data-ttu-id="b14de-121">Bei gemeinsam genutzten Flächen steuern Sie nicht, wann genau neuer Inhalt auf dem Bildschirm angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b14de-121">For shared surfaces, you don't control the precise timing for when new content appears on-screen.</span></span> <span data-ttu-id="b14de-122">Stattdessen werden Änderungen an den gemeinsam genutzten Flächen mit den Updates des XAML-Frameworks synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="b14de-122">Rather, updates to the shared surface are synced to the XAML framework's updates.</span></span>
-   <span data-ttu-id="b14de-123">[Swapchains](https://msdn.microsoft.com/library/windows/desktop/bb206356(v=vs.85).aspx) stellen eine Sammlung von Puffern dar, die verwendet werden, um Grafiken mit minimaler Verzögerung anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b14de-123">[Swap chains](https://msdn.microsoft.com/library/windows/desktop/bb206356(v=vs.85).aspx) represent a collection of buffers used to display graphics at minimal latency.</span></span> <span data-ttu-id="b14de-124">Swapchains werden üblicherweise mit 60Frames pro Sekunde und separat vom UI-Thread aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="b14de-124">Typically, swap chains are updated at 60 frames per second separately from the UI thread.</span></span> <span data-ttu-id="b14de-125">Im Gegensatz zu CPU-Ressourcen haben Swapchains allerdings einen höheren Arbeitsspeicherbedarf, um schnelle Aktualisierungen zu unterstützen, und ihre Verwendung ist komplizierter, da mehrere Threads verwaltet werden müssen.</span><span class="sxs-lookup"><span data-stu-id="b14de-125">However, swap chains use more memory and CPU resources in order to support rapid updates, and are more difficult to use since you have to manage multiple threads.</span></span>

<span data-ttu-id="b14de-126">Überlegen Sie sich, wofür Sie DirectX verwenden.</span><span class="sxs-lookup"><span data-stu-id="b14de-126">Consider what you are using DirectX for.</span></span> <span data-ttu-id="b14de-127">Wird es für die Zusammenstellung und Animierung eines einzelnen Steuerelements verwendet, das in die Abmessungen des Anzeigefensters passt?</span><span class="sxs-lookup"><span data-stu-id="b14de-127">Will it be used to composite or animate a single control that fits within the dimensions of the display window?</span></span> <span data-ttu-id="b14de-128">Wird eine Ausgabe enthalten sein, die wie in einem Spiel in Echtzeit gerendert und gesteuert werden muss?</span><span class="sxs-lookup"><span data-stu-id="b14de-128">Will it contain output that needs to be rendered and controlled in real-time, as in a game?</span></span> <span data-ttu-id="b14de-129">In diesen Fällen empfiehlt sich wahrscheinlich die Implementierung einer Swapchain.</span><span class="sxs-lookup"><span data-stu-id="b14de-129">If so, you will probably need to implement a swap chain.</span></span> <span data-ttu-id="b14de-130">Andernfalls können Sie normalerweise auch eine gemeinsam genutzte Fläche verwenden.</span><span class="sxs-lookup"><span data-stu-id="b14de-130">Otherwise, should be fine using a shared surface.</span></span>

<span data-ttu-id="b14de-131">Nachdem Sie sich überlegt haben, wie DirectX verwendet werden soll, können Sie einen den folgenden Windows-Runtime-Typen verwenden, um DirectX-Rendering in eine UWP-App zu integrieren:</span><span class="sxs-lookup"><span data-stu-id="b14de-131">Once you've determined how you intend to use DirectX, you use one of these Windows Runtime types to incorporate DirectX rendering into your UWP app:</span></span>

-   <span data-ttu-id="b14de-132">Wenn Sie ein statisches Bild erstellen oder ein komplexes Bild in ereignisgesteuerten Intervallen zeichnen möchten, zeichnen Sie mit [Windows::UI::Xaml::Media::Imaging::SurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702041) in eine gemeinsam genutzte Fläche.</span><span class="sxs-lookup"><span data-stu-id="b14de-132">If you want to compose a static image, or draw a complex image on event-driven intervals, draw to a shared surface with [Windows::UI::Xaml::Media::Imaging::SurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702041).</span></span> <span data-ttu-id="b14de-133">Dieser Typ ermöglicht die Behandlung einer DirectX-Zeichenoberfläche von bestimmter Größe.</span><span class="sxs-lookup"><span data-stu-id="b14de-133">This type handles a sized DirectX drawing surface.</span></span> <span data-ttu-id="b14de-134">In der Regel wird dieser Typ beim Erstellen eines Bilds oder einer Textur als Bitmap verwendet, um in einem Dokument oder als UI-Element angezeigt zu werden.</span><span class="sxs-lookup"><span data-stu-id="b14de-134">Typically, you use this type when composing an image or texture as a bitmap for display in a document or UI element.</span></span> <span data-ttu-id="b14de-135">Der Typ ist in Szenarien mit Echtzeitinteraktivität wie hochleistungsfähige Spiele nicht gut geeignet.</span><span class="sxs-lookup"><span data-stu-id="b14de-135">It doesn't work well for real-time interactivity, such as a high-performance game.</span></span> <span data-ttu-id="b14de-136">Dies liegt daran, dass Updates des **SurfaceImageSource**-Objekts mit Updates der XAML-Benutzeroberfläche synchronisiert werden. Somit kann es zu Verzögerungen beim visuellen Feedback kommen, z.B. in Form einer schwankenden Bildrate oder einer wahrgenommenen verzögerten Reaktion auf Echtzeiteingaben.</span><span class="sxs-lookup"><span data-stu-id="b14de-136">That's because updates to a **SurfaceImageSource** object are synced to XAML user interface updates, and that can introduce latency into the visual feedback you provide to the user, like a fluctuating frame rate or a perceived poor response to real-time input.</span></span> <span data-ttu-id="b14de-137">Die Aktualisierungen sind jedoch noch schnell genug für dynamische Steuerelemente oder Datensimulationen.</span><span class="sxs-lookup"><span data-stu-id="b14de-137">Updates are still quick enough for dynamic controls or data simulations, though!</span></span>

-   <span data-ttu-id="b14de-138">Wenn die Größe des Bilds den verfügbaren Platz auf dem Bildschirm übersteigt und es vom Benutzer verschoben und gezoomt werden kann, verwenden Sie [Windows::UI::Xaml::Media::Imaging::VirtualSurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702050).</span><span class="sxs-lookup"><span data-stu-id="b14de-138">If the image is larger than the provided screen real estate, and can be panned or zoomed by the user, use [Windows::UI::Xaml::Media::Imaging::VirtualSurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702050).</span></span> <span data-ttu-id="b14de-139">Dieser Typ ermöglicht die Behandlung einer DirectX-Zeichenoberfläche, die größer als der Bildschirm ist.</span><span class="sxs-lookup"><span data-stu-id="b14de-139">This type handles a sized DirectX drawing surface that is larger than the screen.</span></span> <span data-ttu-id="b14de-140">Wie [SurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702041) wird dies für die dynamische Erstellung eines komplexen Bilds oder Steuerelements verwendet.</span><span class="sxs-lookup"><span data-stu-id="b14de-140">Like [SurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702041), you use this when composing a complex image or control dynamically.</span></span> <span data-ttu-id="b14de-141">Und wie **SurfaceImageSource** ist diese Klasse nicht gut für hochleistungsfähige Spiele geeignet.</span><span class="sxs-lookup"><span data-stu-id="b14de-141">And, also like **SurfaceImageSource**, it doesn't work well for high-performance games.</span></span> <span data-ttu-id="b14de-142">Beispielhafte XAML-Elemente, welche die Klasse **VirtualSurfaceImageSource** verwenden können, sind Kartensteuerelemente oder Viewer für große Dokumente mit hoher Bilddichte.</span><span class="sxs-lookup"><span data-stu-id="b14de-142">Some examples of XAML elements that could use a **VirtualSurfaceImageSource** are map controls, or a large, image-dense document viewer.</span></span>

-   <span data-ttu-id="b14de-143">Wenn Sie DirectX verwenden, um Grafiken zu präsentieren, die in Echtzeit oder in regelmäßigen Intervallen mit niedriger Verzögerung aktualisiert werden müssen, verwenden Sie die Klasse [SwapChainPanel](https://msdn.microsoft.com/library/windows/apps/dn252834). So können Sie Grafiken aktualisieren, ohne dass eine Synchronisierung mit dem Aktualisierungstimer des XAML-Frameworks erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="b14de-143">If you are using DirectX to present graphics updated in real-time, or in a situation where the updates must come on regular low-latency intervals, use the [SwapChainPanel](https://msdn.microsoft.com/library/windows/apps/dn252834) class, so you can refresh the graphics without syncing to the XAML framework refresh timer.</span></span> <span data-ttu-id="b14de-144">Mit diesem Typ können Sie direkt auf die Swapchain ([IDXGISwapChain1](https://msdn.microsoft.com/library/windows/desktop/hh404631)) der Grafikhardware zugreifen und XAML oberhalb des Renderziels anordnen.</span><span class="sxs-lookup"><span data-stu-id="b14de-144">This type enables you to access the graphics device's swap chain ([IDXGISwapChain1](https://msdn.microsoft.com/library/windows/desktop/hh404631)) directly and layer XAML atop the render target.</span></span> <span data-ttu-id="b14de-145">Dieser Typ ist hervorragend für Spiele und DirectX-Apps mit Vollbildansicht geeignet, in denen eine XAML-basierte Benutzeroberfläche erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="b14de-145">This type works great for games and full-screen DirectX apps that require a XAML-based user interface.</span></span> <span data-ttu-id="b14de-146">Wenn Sie diese Vorgehensweise wählen, sollten Sie sich mit DirectX sehr gut auskennen, z.B. in Bezug auf die Bereiche Microsoft DirectX Graphics Infrastructure (DXGI), Direct2D und Direct3D.</span><span class="sxs-lookup"><span data-stu-id="b14de-146">You must know DirectX well to use this approach, including the Microsoft DirectX Graphics Infrastructure (DXGI), Direct2D, and Direct3D technologies.</span></span> <span data-ttu-id="b14de-147">Weitere Informationen finden Sie unter [Programmieranleitung für Direct3D11](https://msdn.microsoft.com/library/windows/desktop/ff476345).</span><span class="sxs-lookup"><span data-stu-id="b14de-147">For more info, see [Programming Guide for Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476345).</span></span>

## <a name="surfaceimagesource"></a><span data-ttu-id="b14de-148">SurfaceImageSource</span><span class="sxs-lookup"><span data-stu-id="b14de-148">SurfaceImageSource</span></span>


<span data-ttu-id="b14de-149">[SurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702041) bietet gemeinsam genutzte Flächen, in die mit DirectX gezeichnet werden kann, und setzt die einzelnen Bestandteile dann zu App-Inhalten zusammen.</span><span class="sxs-lookup"><span data-stu-id="b14de-149">[SurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702041) provides DirectX shared surfaces to draw into and then composes the bits into app content.</span></span>

<span data-ttu-id="b14de-150">Im Folgenden erfahren Sie mehr über die grundlegende Vorgehensweise zum Erstellen und Aktualisieren eines [SurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702041)-Objekts im CodeBehind.</span><span class="sxs-lookup"><span data-stu-id="b14de-150">Here is the basic process for creating and updating a [SurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702041) object in the code-behind:</span></span>

1.  <span data-ttu-id="b14de-151">Legen Sie die Größe der gemeinsam genutzten Fläche fest, indem Sie die Werte für die Höhe und Breite an den Konstruktor [SurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702041) übergeben.</span><span class="sxs-lookup"><span data-stu-id="b14de-151">Define the size of the shared surface by passing the height and width to the [SurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702041) constructor.</span></span> <span data-ttu-id="b14de-152">Sie können ebenfalls festlegen, ob für die gemeinsam genutzte Fläche Alpha-Unterstützung (Deckkraft) erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="b14de-152">You can also indicate whether the surface needs alpha (opacity) support.</span></span>

    <span data-ttu-id="b14de-153">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="b14de-153">For example:</span></span>

    `SurfaceImageSource^ surfaceImageSource = ref new SurfaceImageSource(400, 300);`

2.  <span data-ttu-id="b14de-154">Rufen Sie einen Zeiger zu [ISurfaceImageSourceNativeWithD2D](https://msdn.microsoft.com/library/windows/desktop/dn302137) ab.</span><span class="sxs-lookup"><span data-stu-id="b14de-154">Get a pointer to [ISurfaceImageSourceNativeWithD2D](https://msdn.microsoft.com/library/windows/desktop/dn302137).</span></span> <span data-ttu-id="b14de-155">Wandeln Sie das [SurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702041)-Objekt als [IInspectable](https://msdn.microsoft.com/library/windows/desktop/br205821) (oder **IUnknown**) um, und rufen Sie **QueryInterface** für dieses auf, um die zugrunde liegende **ISurfaceImageSourceNativeWithD2D**-Implementierung abzurufen.</span><span class="sxs-lookup"><span data-stu-id="b14de-155">Cast the [SurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702041) object as [IInspectable](https://msdn.microsoft.com/library/windows/desktop/br205821) (or **IUnknown**), and call **QueryInterface** on it to get the underlying **ISurfaceImageSourceNativeWithD2D** implementation.</span></span> <span data-ttu-id="b14de-156">Die für diese Implementierung festgelegten Methoden verwenden Sie dann, um das entsprechende Gerät festzulegen und die Zeichenoperationen auszuführen.</span><span class="sxs-lookup"><span data-stu-id="b14de-156">You use the methods defined on this implementation to set the device and run the draw operations.</span></span>

    ```cpp
    Microsoft::WRL::ComPtr<ISurfaceImageSourceNativeWithD2D> m_sisNativeWithD2D;

    // ...

    IInspectable* sisInspectable = 
        (IInspectable*) reinterpret_cast<IInspectable*>(surfaceImageSource);

    sisInspectable->QueryInterface(
        __uuidof(ISurfaceImageSourceNativeWithD2D), 
        (void **)&m_sisNativeWithD2D);
    ```

3.  <span data-ttu-id="b14de-157">Erstellen Sie das DXGI- und das D2D-Gerät, indem Sie zunächst [D3D11CreateDevice](https://msdn.microsoft.com/library/windows/desktop/ff476082) und [D2D1CreateDevice](https://msdn.microsoft.com/library/windows/desktop/hh404272(v=vs.85).aspx) aufrufen und das Gerät sowie den Kontext dann an [ISurfaceImageSourceNativeWithD2D::SetDevice](https://msdn.microsoft.com/library/dn302141.aspx) übergeben.</span><span class="sxs-lookup"><span data-stu-id="b14de-157">Create the DXGI and D2D devices by first calling [D3D11CreateDevice](https://msdn.microsoft.com/library/windows/desktop/ff476082) and [D2D1CreateDevice](https://msdn.microsoft.com/library/windows/desktop/hh404272(v=vs.85).aspx) then passing the device and context to [ISurfaceImageSourceNativeWithD2D::SetDevice](https://msdn.microsoft.com/library/dn302141.aspx).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="b14de-158">Wenn Sie über einen Hintergrundthread in Ihr **SurfaceImageSource** zeichnen, müssen Sie außerdem sicherstellen, dass der Multithread-Zugriff auf dem DXGI-Gerät aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="b14de-158">If you will be drawing to your **SurfaceImageSource** from a background thread, you'll also need to ensure that the DXGI device has enabled multi-threaded access.</span></span> <span data-ttu-id="b14de-159">Dies sollte aus Leistungsgründen beim Zeichnen über einen Hintergrundthread erfolgen.</span><span class="sxs-lookup"><span data-stu-id="b14de-159">This should only be done if you will be drawing from a background thread, for performance reasons.</span></span>

    <span data-ttu-id="b14de-160">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="b14de-160">For example:</span></span>

    ```cpp
    Microsoft::WRL::ComPtr<ID3D11Device> m_d3dDevice;
    Microsoft::WRL::ComPtr<ID3D11DeviceContext> m_d3dContext;
    Microsoft::WRL::ComPtr<ID2D1Device> m_d2dDevice;

    // Create the DXGI device
    D3D11CreateDevice(
            NULL,
            D3D_DRIVER_TYPE_HARDWARE,
            NULL,
            flags,
            featureLevels,
            ARRAYSIZE(featureLevels),
            D3D11_SDK_VERSION,
            &m_d3dDevice,
            NULL,
            &m_d3dContext);

    Microsoft::WRL::ComPtr<IDXGIDevice> dxgiDevice;
    m_d3dDevice.As(&dxgiDevice);

    // To enable multi-threaded access (optional)
    Microsoft::WRL::ComPtr<ID3D10Multithread> d3dMultiThread;

    m_d3dDevice->QueryInterface(
        __uuidof(ID3D10Multithread), 
        (void **) &d3dMultiThread);

    d3dMultiThread->SetMultithreadProtected(TRUE);

    // Create the D2D device
    D2D1CreateDevice(m_dxgiDevice.Get(), NULL, &m_d2dDevice);

    // Set the D2D device
    m_sisNativeWithD2D->SetDevice(m_d2dDevice.Get());
    ```

4.  <span data-ttu-id="b14de-161">Stellen Sie einen Zeiger für das [ID2D1DeviceContext](https://msdn.microsoft.com/library/windows/desktop/bb174565)-Objekt zur Methode [ISurfaceImageSourceNativeWithD2D::BeginDraw](https://msdn.microsoft.com/library/dn302138.aspx) bereit, und verwenden Sie den zurückgegebenen Kontext für das Zeichnen, um die Inhalte des gewünschten Rechtecks innerhalb von **SurfaceImageSource** zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="b14de-161">Provide a pointer to [ID2D1DeviceContext](https://msdn.microsoft.com/library/windows/desktop/bb174565) object to [ISurfaceImageSourceNativeWithD2D::BeginDraw](https://msdn.microsoft.com/library/dn302138.aspx), and use the returned drawing context to draw the contents of the desired rectangle within the **SurfaceImageSource**.</span></span> <span data-ttu-id="b14de-162">**ISurfaceImageSourceNativeWithD2D::BeginDraw** und die Zeichenbefehle können über einen Hintergrundthread aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="b14de-162">**ISurfaceImageSourceNativeWithD2D::BeginDraw** and the drawing commands can be called from a background thread.</span></span> <span data-ttu-id="b14de-163">Es wird nur in dem Bereich gezeichnet, der im Parameter *updateRect* für Updates festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="b14de-163">Only the area specified for update in the *updateRect* parameter is drawn.</span></span>

    <span data-ttu-id="b14de-164">Die Methode gibt den X-Y-Punkt-Offset für das Zielrechteck als *offset*-Parameter zurück.</span><span class="sxs-lookup"><span data-stu-id="b14de-164">This method returns the point (x,y) offset of the updated target rectangle in the *offset* parameter.</span></span> <span data-ttu-id="b14de-165">Mit diesem Offset können Sie festlegen, wo Ihr aktualisierter Inhalt mit dem **ID2D1DeviceContext** gezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="b14de-165">You use this offset to determine where to draw your updated content with the **ID2D1DeviceContext**.</span></span>

    ```cpp
    Microsoft::WRL::ComPtr<ID2D1DeviceContext> drawingContext;

    HRESULT beginDrawHR = m_sisNative->BeginDraw(
        updateRect, 
        &drawingContext, 
        &offset);

    if (beginDrawHR == DXGI_ERROR_DEVICE_REMOVED 
        || beginDrawHR == DXGI_ERROR_DEVICE_RESET
        || beginDrawHR == D2DERR_RECREATE_TARGET)
    {
        // The D3D and D2D device was lost and need to be re-created.
        // Recovery steps are:
        // 1) Re-create the D3D and D2D devices
        // 2) Call ISurfaceImageSourceNativeWithD2D::SetDevice with the new D2D
        //    device
        // 3) Redraw the contents of the SurfaceImageSource
    }
    else if (beginDrawHR == E_SURFACE_CONTENTS_LOST)
    {
        // The devices were not lost but the entire contents of the surface
        // were. Recovery steps are:
        // 1) Call ISurfaceImageSourceNativeWithD2D::SetDevice with the D2D 
        //    device again
        // 2) Redraw the entire contents of the SurfaceImageSource
    }
    else 
    {
        // Draw your updated rectangle with the drawingContext
    }
    ```

5. <span data-ttu-id="b14de-166">Rufen Sie [ISurfaceImageSourceNativeWithD2D::EndDraw](https://msdn.microsoft.com/library/dn302139.aspx) auf, um die Bitmap fertigzustellen.</span><span class="sxs-lookup"><span data-stu-id="b14de-166">Call [ISurfaceImageSourceNativeWithD2D::EndDraw](https://msdn.microsoft.com/library/dn302139.aspx) to complete the bitmap.</span></span> <span data-ttu-id="b14de-167">Die Bitmap kann als Quelle für ein XAML [Image](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.aspx) oder [ImageBrush](https://msdn.microsoft.com/library/windows/apps/br210101) verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b14de-167">The bitmap can be used as a source for a XAML [Image](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.aspx) or [ImageBrush](https://msdn.microsoft.com/library/windows/apps/br210101).</span></span> <span data-ttu-id="b14de-168">**ISurfaceImageSourceNativeWithD2D::EndDraw** darf nur über den UI-Thread aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="b14de-168">**ISurfaceImageSourceNativeWithD2D::EndDraw** must be called only from the UI thread.</span></span>

    ```cpp
    m_sisNative->EndDraw();

    // ...
    // The SurfaceImageSource object's underlying 
    // ISurfaceImageSourceNativeWithD2D object contains the completed bitmap.

    ImageBrush^ brush = ref new ImageBrush();
    brush->ImageSource = surfaceImageSource;
    ```

    > [!NOTE]
    > <span data-ttu-id="b14de-169">Das Aufrufen von [SurfaceImageSource::SetSource](https://msdn.microsoft.com/library/windows/apps/br243255) (übernommen von **IBitmapSource::SetSource**) löst zurzeit eine Ausnahme aus.</span><span class="sxs-lookup"><span data-stu-id="b14de-169">Calling [SurfaceImageSource::SetSource](https://msdn.microsoft.com/library/windows/apps/br243255) (inherited from **IBitmapSource::SetSource**) currently throws an exception.</span></span> <span data-ttu-id="b14de-170">Rufen Sie es nicht vom [SurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702041)-Objekt aus auf.</span><span class="sxs-lookup"><span data-stu-id="b14de-170">Do not call it from your [SurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702041) object.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b14de-171">Anwendungen dürfen nicht in **SurfaceImageSource** zeichnen, wenn das ihnen zugeordnete [Fenster](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Window) ausgeblendet ist. Andernfalls schlagen die **ISurfaceImageSourceNativeWithD2D**-APIs fehl.</span><span class="sxs-lookup"><span data-stu-id="b14de-171">Applications must avoid drawing to **SurfaceImageSource** while their associated [Window](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Window) is hidden, otherwise **ISurfaceImageSourceNativeWithD2D** APIs will fail.</span></span> <span data-ttu-id="b14de-172">Registrieren Sie sich dazu als ein Ereignislistener für das [Window.VisibilityChanged](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Window.VisibilityChanged) Ereignis, um Änderungen an der Sichtbarkeit nachverfolgen zu können.</span><span class="sxs-lookup"><span data-stu-id="b14de-172">To accomplish this, register as an event listener for the [Window.VisibilityChanged](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Window.VisibilityChanged) event to track visibility changes.</span></span>

## <a name="virtualsurfaceimagesource"></a><span data-ttu-id="b14de-173">VirtualSurfaceImageSource</span><span class="sxs-lookup"><span data-stu-id="b14de-173">VirtualSurfaceImageSource</span></span>

<span data-ttu-id="b14de-174">[VirtualSurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702050) erweitert [SurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702041), wenn die Inhalte potenziell zu groß sind, um auf dem Bildschirm angezeigt zu werden, und die Inhalte virtualisiert werden müssen, um ein optimales Rendering zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="b14de-174">[VirtualSurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702050) extends [SurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702041) when the content is potentially larger than what can fit on screen and so the content must be virtualized to render optimally.</span></span>

<span data-ttu-id="b14de-175">[VirtualSurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702050) unterscheidet sich von [SurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702041) durch die Verwendung der Callback-Methode [IVirtualSurfaceImageSourceCallbacksNative::UpdatesNeeded](https://msdn.microsoft.com/library/windows/desktop/hh848337). Die Callback-Methode wird implementiert, um bestimmte Bereiche der Fläche zu aktualisieren, sobald sie auf dem Bildschirm angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b14de-175">[VirtualSurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702050) differs from [SurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702041) in that it uses a callback, [IVirtualSurfaceImageSourceCallbacksNative::UpdatesNeeded](https://msdn.microsoft.com/library/windows/desktop/hh848337), that you implement to update regions of the surface as they become visible on the screen.</span></span> <span data-ttu-id="b14de-176">Somit müssen Sie keine ausgeblendeten Bereiche löschen, da das XAML-Framework diese Aufgabe für Sie übernimmt.</span><span class="sxs-lookup"><span data-stu-id="b14de-176">You do not need to clear regions that are hidden, as the XAML framework takes care of that for you.</span></span>

<span data-ttu-id="b14de-177">Im Folgenden erfahren Sie mehr über die grundlegende Vorgehensweise zum Erstellen und Aktualisieren eines [VirtualSurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702050)-Objekts im CodeBehind:</span><span class="sxs-lookup"><span data-stu-id="b14de-177">Here is the basic process for creating and updating a [VirtualSurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702050) object in the code-behind:</span></span>

1.  <span data-ttu-id="b14de-178">Erstellen Sie eine Instanz von [VirtualSurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702050) in der gewünschten Größe.</span><span class="sxs-lookup"><span data-stu-id="b14de-178">Create an instance of [VirtualSurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702050) with the size that you want.</span></span> <span data-ttu-id="b14de-179">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="b14de-179">For example:</span></span>

    ```cpp
    VirtualSurfaceImageSource^ virtualSIS = 
        ref new VirtualSurfaceImageSource(2000, 2000);
    ```

2.  <span data-ttu-id="b14de-180">Rufen Sie Zeiger zu [IVirtualSurfaceImageSourceNative](https://msdn.microsoft.com/library/windows/desktop/hh848328) und [ISurfaceImageSourceNativeWithD2D](https://msdn.microsoft.com/library/windows/desktop/dn302137) ab.</span><span class="sxs-lookup"><span data-stu-id="b14de-180">Get pointers to [IVirtualSurfaceImageSourceNative](https://msdn.microsoft.com/library/windows/desktop/hh848328) and [ISurfaceImageSourceNativeWithD2D](https://msdn.microsoft.com/library/windows/desktop/dn302137).</span></span> <span data-ttu-id="b14de-181">Wandeln Sie das [VirtualSurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702050)-Objekt als [IInspectable](https://msdn.microsoft.com/library/windows/desktop/br205821) oder [IUnknown](https://msdn.microsoft.com/library/windows/desktop/ms680509) um, und rufen Sie [QueryInterface](https://msdn.microsoft.com/library/windows/desktop/ms682521) für dieses auf, um die zugrunde liegenden **IVirtualSurfaceImageSourceNative**- und **ISurfaceImageSourceNativeWithD2D**-Implementierungen abzurufen.</span><span class="sxs-lookup"><span data-stu-id="b14de-181">Cast the [VirtualSurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702050) object as [IInspectable](https://msdn.microsoft.com/library/windows/desktop/br205821) or [IUnknown](https://msdn.microsoft.com/library/windows/desktop/ms680509), and call [QueryInterface](https://msdn.microsoft.com/library/windows/desktop/ms682521) on it to get the underlying **IVirtualSurfaceImageSourceNative** and **ISurfaceImageSourceNativeWithD2D** implementations.</span></span> <span data-ttu-id="b14de-182">Die für diese Implementierungen festgelegten Methoden verwenden Sie dann, um das entsprechende Gerät festzulegen und die Zeichenoperationen auszuführen.</span><span class="sxs-lookup"><span data-stu-id="b14de-182">You use the methods defined on these implementations to set the device and run the draw operations.</span></span>

    ```cpp
    Microsoft::WRL::ComPtr<IVirtualSurfaceImageSourceNative>  m_vsisNative;
    Microsoft::WRL::ComPtr<ISurfaceImageSourceNativeWithD2D> m_sisNativeWithD2D;

    // ...

    IInspectable* vsisInspectable = 
        (IInspectable*) reinterpret_cast<IInspectable*>(virtualSIS);

    vsisInspectable->QueryInterface(
        __uuidof(IVirtualSurfaceImageSourceNative), 
        (void **) &m_vsisNative);

    vsisInspectable->QueryInterface(
        __uuidof(ISurfaceImageSourceNativeWithD2D), 
        (void **) &m_sisNativeWithD2D);
    ```

3.  <span data-ttu-id="b14de-183">Erstellen Sie das DXGI- und das D2D-Gerät, indem Sie zunächst **D3D11CreateDevice** und **D2D1CreateDevice** aufrufen und das D2D-Gerät dann an **ISurfaceImageSourceNativeWithD2D::SetDevice** übergeben.</span><span class="sxs-lookup"><span data-stu-id="b14de-183">Create the DXGI and D2D devices by first calling **D3D11CreateDevice** and **D2D1CreateDevice**, and then pass the D2D device to **ISurfaceImageSourceNativeWithD2D::SetDevice**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b14de-184">Wenn Sie über einen Hintergrundthread in Ihr **VirtualSurfaceImageSource** zeichnen, müssen Sie außerdem sicherstellen, dass der Multithread-Zugriff auf dem DXGI-Gerät aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="b14de-184">If you will be drawing to your **VirtualSurfaceImageSource** from a background thread, you'll also need to ensure that the DXGI device has enabled multi-threaded access.</span></span> <span data-ttu-id="b14de-185">Dies sollte aus Leistungsgründen beim Zeichnen über einen Hintergrundthread erfolgen.</span><span class="sxs-lookup"><span data-stu-id="b14de-185">This should only be done if you will be drawing from a background thread, for performance reasons.</span></span>

    <span data-ttu-id="b14de-186">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="b14de-186">For example:</span></span>

    ```cpp
    Microsoft::WRL::ComPtr<ID3D11Device> m_d3dDevice;
    Microsoft::WRL::ComPtr<ID3D11DeviceContext> m_d3dContext;
    Microsoft::WRL::ComPtr<ID2D1Device> m_d2dDevice;

    // Create the DXGI device
    D3D11CreateDevice(
            NULL,
            D3D_DRIVER_TYPE_HARDWARE,
            NULL,
            flags,
            featureLevels,
            ARRAYSIZE(featureLevels),
            D3D11_SDK_VERSION,
            &m_d3dDevice,
            NULL,
            &m_d3dContext);  

    Microsoft::WRL::ComPtr<IDXGIDevice> dxgiDevice;
    m_d3dDevice.As(&dxgiDevice);
    
    // To enable multi-threaded access (optional)
    Microsoft::WRL::ComPtr<ID3D10Multithread> d3dMultiThread;

    m_d3dDevice->QueryInterface(
        __uuidof(ID3D10Multithread), 
        (void **) &d3dMultiThread);

    d3dMultiThread->SetMultithreadProtected(TRUE);

    // Create the D2D device
    D2D1CreateDevice(m_dxgiDevice.Get(), NULL, &m_d2dDevice);

    // Set the D2D device
    m_vsisNativeWithD2D->SetDevice(m_d2dDevice.Get());

    m_vsisNative->SetDevice(dxgiDevice.Get());
    ```

4.  <span data-ttu-id="b14de-187">Rufen Sie [IVirtualSurfaceImageSourceNative::RegisterForUpdatesNeeded](https://msdn.microsoft.com/library/windows/desktop/hh848334) auf, wodurch eine Referenz zu Ihrer Implementierung von [IVirtualSurfaceUpdatesCallbackNative](https://msdn.microsoft.com/library/windows/desktop/hh848336) übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="b14de-187">Call [IVirtualSurfaceImageSourceNative::RegisterForUpdatesNeeded](https://msdn.microsoft.com/library/windows/desktop/hh848334), passing in a reference to your implementation of [IVirtualSurfaceUpdatesCallbackNative](https://msdn.microsoft.com/library/windows/desktop/hh848336).</span></span>

    ```cpp
    class MyContentImageSource : public IVirtualSurfaceUpdatesCallbackNative
    {
    // ...
      private:
         virtual HRESULT STDMETHODCALLTYPE UpdatesNeeded() override;
    }

    // ...

    HRESULT STDMETHODCALLTYPE MyContentImageSource::UpdatesNeeded()
    {
      // .. Perform drawing here ...
    }

    void MyContentImageSource::Initialize()
    {
      // ...
      m_vsisNative->RegisterForUpdatesNeeded(this);
      // ...
    }
    ```

    <span data-ttu-id="b14de-188">Das Framework ruft Ihre Implementierung von [IVirtualSurfaceUpdatesCallbackNative::UpdatesNeeded](https://msdn.microsoft.com/library/windows/desktop/hh848334) auf, wenn ein Bereich von [VirtualSurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702050) aktualisiert werden muss.</span><span class="sxs-lookup"><span data-stu-id="b14de-188">The framework calls your implementation of [IVirtualSurfaceUpdatesCallbackNative::UpdatesNeeded](https://msdn.microsoft.com/library/windows/desktop/hh848334) when a region of the [VirtualSurfaceImageSource](https://msdn.microsoft.com/library/windows/apps/hh702050) needs to be updated.</span></span>

    <span data-ttu-id="b14de-189">Dieser Fall kann eintreten, wenn das Framework den Bereich bestimmt, der gezeichnet werden muss (etwa wenn der Benutzer die Ansicht der Fläche verschiebt oder zoomt), oder wenn die App die Methode [IVirtualSurfaceImageSourceNative::Invalidate](https://msdn.microsoft.com/library/windows/desktop/hh848332) in diesem Bereich aufgerufen hat.</span><span class="sxs-lookup"><span data-stu-id="b14de-189">This can happen either when the framework determines the region needs to be drawn (such as when the user pans or zooms the view of the surface), or after the app has called [IVirtualSurfaceImageSourceNative::Invalidate](https://msdn.microsoft.com/library/windows/desktop/hh848332) on that region.</span></span>

5.  <span data-ttu-id="b14de-190">Verwenden Sie innerhalb der Methode [IVirtualSurfaceImageSourceNative::UpdatesNeeded](https://msdn.microsoft.com/library/windows/desktop/hh848337) die Methoden [IVirtualSurfaceImageSourceNative::GetUpdateRectCount](https://msdn.microsoft.com/library/windows/desktop/hh848329) und [IVirtualSurfaceImageSourceNative::GetUpdateRects](https://msdn.microsoft.com/library/windows/desktop/hh848330), um zu bestimmen, welche Bereiche der Fläche gezeichnet werden müssen.</span><span class="sxs-lookup"><span data-stu-id="b14de-190">In [IVirtualSurfaceImageSourceNative::UpdatesNeeded](https://msdn.microsoft.com/library/windows/desktop/hh848337), use the [IVirtualSurfaceImageSourceNative::GetUpdateRectCount](https://msdn.microsoft.com/library/windows/desktop/hh848329) and [IVirtualSurfaceImageSourceNative::GetUpdateRects](https://msdn.microsoft.com/library/windows/desktop/hh848330) methods to determine which region(s) of the surface must be drawn.</span></span>

    ```cpp
    HRESULT STDMETHODCALLTYPE MyContentImageSource::UpdatesNeeded()
    {
        HRESULT hr = S_OK;

        try
        {
            ULONG drawingBoundsCount = 0;  
            m_vsisNative->GetUpdateRectCount(&drawingBoundsCount);

            std::unique_ptr<RECT[]> drawingBounds(
                new RECT[drawingBoundsCount]);

            m_vsisNative->GetUpdateRects(
                drawingBounds.get(), 
                drawingBoundsCount);
            
            for (ULONG i = 0; i < drawingBoundsCount; ++i)
            {
                // Drawing code here ...
            }
        }
        catch (Platform::Exception^ exception)
        {
            hr = exception->HResult;
        }

        return hr;
    }
    ```

6.  <span data-ttu-id="b14de-191">Führen Sie schließlich für jeden Bereich, der aktualisiert werden soll, Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="b14de-191">Lastly, for each region that must be updated:</span></span>

    1.  <span data-ttu-id="b14de-192">Stellen Sie einen Zeiger für das **ID2D1DeviceContext**-Objekt zur Methode **ISurfaceImageSourceNativeWithD2D::BeginDraw** bereit, und verwenden Sie den zurückgegebenen Kontext für das Zeichnen, um die Inhalte des gewünschten Rechtecks innerhalb von **SurfaceImageSource** zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="b14de-192">Provide a pointer to the **ID2D1DeviceContext** object to **ISurfaceImageSourceNativeWithD2D::BeginDraw**, and use the returned drawing context to draw the contents of the desired rectangle within the **SurfaceImageSource**.</span></span> <span data-ttu-id="b14de-193">**ISurfaceImageSourceNativeWithD2D::BeginDraw** und die Zeichenbefehle können über einen Hintergrundthread aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="b14de-193">**ISurfaceImageSourceNativeWithD2D::BeginDraw** and the drawing commands can be called from a background thread.</span></span> <span data-ttu-id="b14de-194">Es wird nur in dem Bereich gezeichnet, der im Parameter *updateRect* für Updates festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="b14de-194">Only the area specified for update in the *updateRect* parameter is drawn.</span></span>

        <span data-ttu-id="b14de-195">Die Methode gibt den X-Y-Punkt-Offset für das Zielrechteck als *offset*-Parameter zurück.</span><span class="sxs-lookup"><span data-stu-id="b14de-195">This method returns the point (x,y) offset of the updated target rectangle in the *offset* parameter.</span></span> <span data-ttu-id="b14de-196">Mit diesem Offset können Sie festlegen, wo Ihr aktualisierter Inhalt mit dem **ID2D1DeviceContext** gezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="b14de-196">You use this offset to determine where to draw your updated content with the **ID2D1DeviceContext**.</span></span>

        ```cpp
        Microsoft::WRL::ComPtr<ID2D1DeviceContext> drawingContext;

        HRESULT beginDrawHR = m_sisNative->BeginDraw(
            updateRect, 
            &drawingContext, 
            &offset);

        if (beginDrawHR == DXGI_ERROR_DEVICE_REMOVED 
            || beginDrawHR == DXGI_ERROR_DEVICE_RESET 
            || beginDrawHR == D2DERR_RECREATE_TARGET)
        {
            // The D3D and D2D devices were lost and need to be re-created.
            // Recovery steps are:
            // 1) Re-create the D3D and D2D devices
            // 2) Call ISurfaceImageSourceNativeWithD2D::SetDevice with the 
            //    new D2D device
            // 3) Redraw the contents of the VirtualSurfaceImageSource
        }
        else if (beginDrawHR == E_SURFACE_CONTENTS_LOST)
        {
            // The devices were not lost but the entire contents of the 
            // surface were lost. Recovery steps are:
            // 1) Call ISurfaceImageSourceNativeWithD2D::SetDevice with the 
            //    D2D device again
            // 2) Redraw the entire contents of the VirtualSurfaceImageSource
        }
        else
        {
            // Draw your updated rectangle with the drawingContext
        }
        ```

    2.  <span data-ttu-id="b14de-197">Zeichnen Sie Ihre spezifischen Inhalte in diesem Bereich. Achten Sie aber darauf, dass Sie das Zeichnen auf die begrenzten Bereiche beschränken, um die optimale Leistung sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="b14de-197">Draw the specific content to that region, but constrain your drawing to the bounded regions for better performance.</span></span>

    3.  <span data-ttu-id="b14de-198">Rufen Sie **ISurfaceImageSourceNativeWithD2D::EndDraw** auf.</span><span class="sxs-lookup"><span data-stu-id="b14de-198">Call **ISurfaceImageSourceNativeWithD2D::EndDraw**.</span></span> <span data-ttu-id="b14de-199">Als Ergebnis erhalten Sie eine Bitmap.</span><span class="sxs-lookup"><span data-stu-id="b14de-199">The result is a bitmap.</span></span>

> [!NOTE]
> <span data-ttu-id="b14de-200">Anwendungen dürfen nicht in **SurfaceImageSource** zeichnen, wenn das ihnen zugeordnete [Fenster](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Window) ausgeblendet ist. Andernfalls schlagen die **ISurfaceImageSourceNativeWithD2D**-APIs fehl.</span><span class="sxs-lookup"><span data-stu-id="b14de-200">Applications must avoid drawing to **SurfaceImageSource** while their associated [Window](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Window) is hidden, otherwise **ISurfaceImageSourceNativeWithD2D** APIs will fail.</span></span> <span data-ttu-id="b14de-201">Registrieren Sie sich dazu als ein Ereignislistener für das [Window.VisibilityChanged](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Window.VisibilityChanged) Ereignis, um Änderungen an der Sichtbarkeit nachverfolgen zu können.</span><span class="sxs-lookup"><span data-stu-id="b14de-201">To accomplish this, register as an event listener for the [Window.VisibilityChanged](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Window.VisibilityChanged) event to track visibility changes.</span></span>

## <a name="swapchainpanel-and-gaming"></a><span data-ttu-id="b14de-202">SwapChainPanel und Gaming</span><span class="sxs-lookup"><span data-stu-id="b14de-202">SwapChainPanel and gaming</span></span>


<span data-ttu-id="b14de-203">[SwapChainPanel](https://msdn.microsoft.com/library/windows/apps/dn252834) ist der Windows-Runtime-Typ, der für die Unterstützung von High-End-Grafik und -Spielen mit direkter Swapchain-Verwaltung entwickelt wurde.</span><span class="sxs-lookup"><span data-stu-id="b14de-203">[SwapChainPanel](https://msdn.microsoft.com/library/windows/apps/dn252834) is the Windows Runtime type designed to support high-performance graphics and gaming, where you manage the swap chain directly.</span></span> <span data-ttu-id="b14de-204">Sie erstellen in diesem Fall Ihre eigene DirectX-Swapchain und verwalten die Präsentation Ihrer gerenderten Inhalte selbst.</span><span class="sxs-lookup"><span data-stu-id="b14de-204">In this case, you create your own DirectX swap chain and manage the presentation of your rendered content.</span></span>

<span data-ttu-id="b14de-205">Es gibt gewisse Einschränkungen für den [SwapChainPanel](https://msdn.microsoft.com/library/windows/apps/dn252834)-Typ, um die bestmögliche Leistungsfähigkeit sicherzustellen:</span><span class="sxs-lookup"><span data-stu-id="b14de-205">To ensure good performance, there are certain limitations to the [SwapChainPanel](https://msdn.microsoft.com/library/windows/apps/dn252834) type:</span></span>

-   <span data-ttu-id="b14de-206">Es sind nicht mehr als vier [SwapChainPanel](https://msdn.microsoft.com/library/windows/apps/dn252834)-Instanzen pro App vorhanden.</span><span class="sxs-lookup"><span data-stu-id="b14de-206">There are no more than 4 [SwapChainPanel](https://msdn.microsoft.com/library/windows/apps/dn252834) instances per app.</span></span>
-   <span data-ttu-id="b14de-207">Höhe und Breite der DirectX-Swapchain (in [DXGI\_SWAP\_CHAIN\_DESC1](https://msdn.microsoft.com/library/windows/desktop/hh404528)) müssen auf die aktuellen Abmessungen des Swapchain-Elements festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="b14de-207">You should set the DirectX swap chain's height and width (in [DXGI\_SWAP\_CHAIN\_DESC1](https://msdn.microsoft.com/library/windows/desktop/hh404528)) to the current dimensions of the swap chain element.</span></span> <span data-ttu-id="b14de-208">Andernfalls werden die Inhalte (unter Verwendung von **DXGI\_SCALING\_STRETCH**) passend skaliert.</span><span class="sxs-lookup"><span data-stu-id="b14de-208">If you don't, the display content will be scaled (using **DXGI\_SCALING\_STRETCH**) to fit.</span></span>
-   <span data-ttu-id="b14de-209">Sie müssen den Skalierungsmodus der DirectX-Swapchain (in [DXGI\_SWAP\_CHAIN\_DESC1](https://msdn.microsoft.com/library/windows/desktop/hh404528)) als **DXGI\_SCALING\_STRETCH** festlegen.</span><span class="sxs-lookup"><span data-stu-id="b14de-209">You must set the DirectX swap chain's scaling mode (in [DXGI\_SWAP\_CHAIN\_DESC1](https://msdn.microsoft.com/library/windows/desktop/hh404528)) to **DXGI\_SCALING\_STRETCH**.</span></span>
-   <span data-ttu-id="b14de-210">Sie können den Alphamodus der DirectX-Swapchain (in [DXGI\_SWAP\_CHAIN\_DESC1](https://msdn.microsoft.com/library/windows/desktop/hh404528)) nicht als **DXGI\_ALPHA\_MODE\_PREMULTIPLIED** festlegen.</span><span class="sxs-lookup"><span data-stu-id="b14de-210">You can't set the DirectX swap chain's alpha mode (in [DXGI\_SWAP\_CHAIN\_DESC1](https://msdn.microsoft.com/library/windows/desktop/hh404528)) to **DXGI\_ALPHA\_MODE\_PREMULTIPLIED**.</span></span>
-   <span data-ttu-id="b14de-211">Sie müssen die DirectX-Swapchain erstellen, indem Sie [IDXGIFactory2::CreateSwapChainForComposition](https://msdn.microsoft.com/library/windows/desktop/hh404558) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="b14de-211">You must create the DirectX swap chain by calling [IDXGIFactory2::CreateSwapChainForComposition](https://msdn.microsoft.com/library/windows/desktop/hh404558).</span></span>

<span data-ttu-id="b14de-212">[SwapChainPanel](https://msdn.microsoft.com/library/windows/apps/dn252834) wird basierend auf den Anforderungen Ihrer App aktualisiert und nicht entsprechend den Updates des XAML-Frameworks.</span><span class="sxs-lookup"><span data-stu-id="b14de-212">You update the [SwapChainPanel](https://msdn.microsoft.com/library/windows/apps/dn252834) based on the needs of your app, and not the updates of the XAML framework.</span></span> <span data-ttu-id="b14de-213">Wenn Sie die Updates von **SwapChainPanel** mit denen des XAML-Frameworks synchronisieren möchten, registrieren Sie dieses für das Ereignis [Windows::UI::Xaml::Media::CompositionTarget::Rendering](https://msdn.microsoft.com/library/windows/apps/br228127).</span><span class="sxs-lookup"><span data-stu-id="b14de-213">If you need to synchronize the updates of **SwapChainPanel** to those of the XAML framework, register for the [Windows::UI::Xaml::Media::CompositionTarget::Rendering](https://msdn.microsoft.com/library/windows/apps/br228127) event.</span></span> <span data-ttu-id="b14de-214">Andernfalls müssen Sie sämtliche threadübergreifenden Probleme berücksichtigen, wenn Sie versuchen, die XAML-Elemente über einen Thread zu aktualisieren, bei dem es sich nicht um den Thread handelt, der die Klasse **SwapChainPanel** aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="b14de-214">Otherwise, you must consider any cross-thread issues if you try to update the XAML elements from a different thread than the one updating the **SwapChainPanel**.</span></span>

<span data-ttu-id="b14de-215">Falls Sie in **SwapChainPanel** Zeigereingaben mit geringer Verzögerung empfangen müssen, verwenden Sie [SwapChainPanel::CreateCoreIndependentInputSource](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.swapchainpanel.createcoreindependentinputsource).</span><span class="sxs-lookup"><span data-stu-id="b14de-215">If you need to receive low-latency pointer input to your **SwapChainPanel**, use [SwapChainPanel::CreateCoreIndependentInputSource](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.swapchainpanel.createcoreindependentinputsource).</span></span> <span data-ttu-id="b14de-216">Das von dieser Methode zurückgegebene [CoreIndependentInputSource](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.coreindependentinputsource)-Objekt ermöglicht den Empfang von Eingabeereignissen mit minimaler Verzögerung in einem Hintergrundthread.</span><span class="sxs-lookup"><span data-stu-id="b14de-216">This method returns a [CoreIndependentInputSource](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.coreindependentinputsource) object that can be used to receive input events at minimal latency on a background thread.</span></span> <span data-ttu-id="b14de-217">Hinweis: Nach dem Aufrufen dieser Methode werden keine normalen XAML-Zeigereingabeereignisse für **SwapChainPanel** mehr ausgelöst, da alle Eingaben in den Hintergrundthread umgeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="b14de-217">Note that once this method is called, normal XAML pointer input events will not be fired for the **SwapChainPanel**, since all input will be redirected to the background thread.</span></span>


> <span data-ttu-id="b14de-218">**Hinweis:**   Im Allgemeinen sollten Ihre DirectX-Apps Swapchains im Querformat und entsprechend der angezeigten Fenstergröße erstellen (in den meisten MicrosoftStore-Spielen für gewöhnlich die native Bildschirmauflösung).</span><span class="sxs-lookup"><span data-stu-id="b14de-218">**Note**   In general, your DirectX apps should create swap chains in landscape orientation, and equal to the display window size (which is usually the native screen resolution in most Microsoft Store games).</span></span> <span data-ttu-id="b14de-219">Dadurch wird sichergestellt, dass Ihre App die optimale Swapchain-Implementierung verwendet, wenn sie über keine sichtbaren XAML-Overlays verfügt.</span><span class="sxs-lookup"><span data-stu-id="b14de-219">This ensures that your app uses the optimal swap chain implementation when it doesn't have any visible XAML overlay.</span></span> <span data-ttu-id="b14de-220">Wenn die App in das Hochformat gedreht wird, sollte sie [IDXGISwapChain1::SetRotation](https://msdn.microsoft.com/library/windows/desktop/hh446801) in der vorhandenen Swapchain aufrufen, eine Umwandlung des Inhalts anwenden, wenn erforderlich, und anschließend erneut [SetSwapChain](https://msdn.microsoft.com/library/windows/desktop/dn302144) auf der gleichen Swapchain aufrufen.</span><span class="sxs-lookup"><span data-stu-id="b14de-220">If the app is rotated to portrait mode, your app should call [IDXGISwapChain1::SetRotation](https://msdn.microsoft.com/library/windows/desktop/hh446801) on the existing swap chain, apply a transform to the content if needed, and then call [SetSwapChain](https://msdn.microsoft.com/library/windows/desktop/dn302144) again on the same swap chain.</span></span> <span data-ttu-id="b14de-221">Darüber hinaus sollte Ihre App jedes Mal erneut **SetSwapChain** auf der gleichen Swapchain aufrufen, wenn die Größe der Swapchain geändert wird, indem [IDXGISwapChain::ResizeBuffers](https://msdn.microsoft.com/library/windows/desktop/bb174577) aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="b14de-221">Similarly, your app should call **SetSwapChain** again on the same swap chain whenever the swap chain is resized by calling [IDXGISwapChain::ResizeBuffers](https://msdn.microsoft.com/library/windows/desktop/bb174577).</span></span>


 

<span data-ttu-id="b14de-222">Im Folgenden erfahren Sie mehr über die grundlegende Vorgehensweise zum Erstellen und Aktualisieren eines [SwapChainPanel](https://msdn.microsoft.com/library/windows/apps/dn252834)-Objekts im CodeBehind:</span><span class="sxs-lookup"><span data-stu-id="b14de-222">Here is basic process for creating and updating a [SwapChainPanel](https://msdn.microsoft.com/library/windows/apps/dn252834) object in the code-behind:</span></span>

1.  <span data-ttu-id="b14de-223">Rufen Sie eine Instanz eines Swapchainbereichs für Ihre App ab.</span><span class="sxs-lookup"><span data-stu-id="b14de-223">Get an instance of a swap chain panel for your app.</span></span> <span data-ttu-id="b14de-224">Die Instanzen sind in XAML mit dem Tag `<SwapChainPanel>` gekennzeichnet.</span><span class="sxs-lookup"><span data-stu-id="b14de-224">The instances are indicated in your XAML with the `<SwapChainPanel>` tag.</span></span>

    `Windows::UI::Xaml::Controls::SwapChainPanel^ swapChainPanel;`

    <span data-ttu-id="b14de-225">Unten finden Sie ein Beispiel für das Tag `<SwapChainPanel>`.</span><span class="sxs-lookup"><span data-stu-id="b14de-225">Here is an example `<SwapChainPanel>` tag.</span></span>

    ```xml
    <SwapChainPanel x:Name="swapChainPanel">
        <SwapChainPanel.ColumnDefinitions>
            <ColumnDefinition Width="300*"/>
            <ColumnDefinition Width="1069*"/>
        </SwapChainPanel.ColumnDefinitions>
    …
    ```

2.  <span data-ttu-id="b14de-226">Rufen Sie einen Zeiger zur Schnittstelle [ISwapChainPanelNative](https://msdn.microsoft.com/library/windows/desktop/dn302143) ab.</span><span class="sxs-lookup"><span data-stu-id="b14de-226">Get a pointer to [ISwapChainPanelNative](https://msdn.microsoft.com/library/windows/desktop/dn302143).</span></span> <span data-ttu-id="b14de-227">Wandeln Sie das [SwapChainPanel](https://msdn.microsoft.com/library/windows/apps/dn252834)-Objekt als [IInspectable](https://msdn.microsoft.com/library/windows/desktop/br205821) (oder **IUnknown**) um, und rufen Sie **QueryInterface** für dieses auf, um die zugrunde liegende **ISwapChainPanelNative**-Implementierung abzurufen.</span><span class="sxs-lookup"><span data-stu-id="b14de-227">Cast the [SwapChainPanel](https://msdn.microsoft.com/library/windows/apps/dn252834) object as [IInspectable](https://msdn.microsoft.com/library/windows/desktop/br205821) (or **IUnknown**), and call **QueryInterface** on it to get the underlying **ISwapChainPanelNative** implementation.</span></span>

    ```cpp
    Microsoft::WRL::ComPtr<ISwapChainPanelNative> m_swapChainNative;
    // ...
    IInspectable* panelInspectable = (IInspectable*) reinterpret_cast<IInspectable*>(swapChainPanel);
    panelInspectable->QueryInterface(__uuidof(ISwapChainPanelNative), (void **)&m_swapChainNative);
    ```

3.  <span data-ttu-id="b14de-228">Erstellen Sie das DXGI-Gerät und die Swapchain, und legen Sie für die Swapchain [ISwapChainPanelNative](https://msdn.microsoft.com/library/windows/desktop/dn302143) fest, indem Sie diese an [SetSwapChain](https://msdn.microsoft.com/library/windows/desktop/dn302144) übergeben.</span><span class="sxs-lookup"><span data-stu-id="b14de-228">Create the DXGI device and the swap chain, and set the swap chain to [ISwapChainPanelNative](https://msdn.microsoft.com/library/windows/desktop/dn302143) by passing it to [SetSwapChain](https://msdn.microsoft.com/library/windows/desktop/dn302144).</span></span>

    ```cpp
    Microsoft::WRL::ComPtr<IDXGISwapChain1>               m_swapChain;    
    // ...
    DXGI_SWAP_CHAIN_DESC1 swapChainDesc = {0};
            swapChainDesc.Width = m_bounds.Width;
            swapChainDesc.Height = m_bounds.Height;
            swapChainDesc.Format = DXGI_FORMAT_B8G8R8A8_UNORM;           // This is the most common swapchain format.
            swapChainDesc.Stereo = false; 
            swapChainDesc.SampleDesc.Count = 1;                          // Don't use multi-sampling.
            swapChainDesc.SampleDesc.Quality = 0;
            swapChainDesc.BufferUsage = DXGI_USAGE_RENDER_TARGET_OUTPUT;
            swapChainDesc.BufferCount = 2;
            swapChainDesc.Scaling = DXGI_SCALING_STRETCH;
            swapChainDesc.SwapEffect = DXGI_SWAP_EFFECT_FLIP_SEQUENTIAL; // We recommend using this swap effect for all. applications
            swapChainDesc.Flags = 0;
                    
    // QI for DXGI device
    Microsoft::WRL::ComPtr<IDXGIDevice> dxgiDevice;
    m_d3dDevice.As(&dxgiDevice);

    // Get the DXGI adapter.
    Microsoft::WRL::ComPtr<IDXGIAdapter> dxgiAdapter;
    dxgiDevice->GetAdapter(&dxgiAdapter);

    // Get the DXGI factory.
    Microsoft::WRL::ComPtr<IDXGIFactory2> dxgiFactory;
    dxgiAdapter->GetParent(__uuidof(IDXGIFactory2), &dxgiFactory);
    // Create a swap chain by calling CreateSwapChainForComposition.
    dxgiFactory->CreateSwapChainForComposition(
                m_d3dDevice.Get(),
                &swapChainDesc,
                nullptr,        // Allow on any display. 
                &m_swapChain
                );
            
    m_swapChainNative->SetSwapChain(m_swapChain.Get());
    ```

4.  <span data-ttu-id="b14de-229">Zeichnen Sie in die DirectX-Swapchain, und präsentieren Sie sie, um die Inhalte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b14de-229">Draw to the DirectX swap chain, and present it to display the contents.</span></span>

    ```cpp
    HRESULT hr = m_swapChain->Present(1, 0);
    ```

    <span data-ttu-id="b14de-230">Die XAML-Elemente werden aktualisiert, wenn das Windows-Runtime-Layout/die Rendering-Logik ein Update signalisiert.</span><span class="sxs-lookup"><span data-stu-id="b14de-230">The XAML elements are refreshed when the Windows Runtime layout/render logic signals an update.</span></span>

## <a name="related-topics"></a><span data-ttu-id="b14de-231">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="b14de-231">Related topics</span></span>

* [<span data-ttu-id="b14de-232">Win2D</span><span class="sxs-lookup"><span data-stu-id="b14de-232">Win2D</span></span>](http://microsoft.github.io/Win2D/html/Introduction.htm)
* [<span data-ttu-id="b14de-233">SurfaceImageSource</span><span class="sxs-lookup"><span data-stu-id="b14de-233">SurfaceImageSource</span></span>](https://msdn.microsoft.com/library/windows/apps/hh702041)
* [<span data-ttu-id="b14de-234">VirtualSurfaceImageSource</span><span class="sxs-lookup"><span data-stu-id="b14de-234">VirtualSurfaceImageSource</span></span>](https://msdn.microsoft.com/library/windows/apps/hh702050)
* [<span data-ttu-id="b14de-235">SwapChainPanel</span><span class="sxs-lookup"><span data-stu-id="b14de-235">SwapChainPanel</span></span>](https://msdn.microsoft.com/library/windows/apps/dn252834)
* [<span data-ttu-id="b14de-236">ISwapChainPanelNative</span><span class="sxs-lookup"><span data-stu-id="b14de-236">ISwapChainPanelNative</span></span>](https://msdn.microsoft.com/library/windows/desktop/dn302143)
* [<span data-ttu-id="b14de-237">Programmieranleitung für Direct3D11</span><span class="sxs-lookup"><span data-stu-id="b14de-237">Programming Guide for Direct3D 11</span></span>](https://msdn.microsoft.com/library/windows/desktop/ff476345)

 

 




