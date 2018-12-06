---
title: Erweitern des Spielbeispiels
description: Hier erfahren Sie, wie Sie eine XAML-Überlagerung für ein UWP-DirectX-Spiel implementieren.
keywords: DirectX, XAML
ms.date: 10/24/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 7cb1c9f9cf6cbc6cce0c5d4547ed503bb9a06e56
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8740148"
---
# <a name="extend-the-game-sample"></a><span data-ttu-id="f1fe9-104">Erweitern des Spielbeispiels</span><span class="sxs-lookup"><span data-stu-id="f1fe9-104">Extend the game sample</span></span>

<span data-ttu-id="f1fe9-105">Sie sind nun mit den Schlüsselkomponenten eines einfachen dreidimensionalen DirectX 3D-Spiels für die Universelle Windows-Plattform (UWP) vertraut.</span><span class="sxs-lookup"><span data-stu-id="f1fe9-105">At this point we've covered the key components of a basic Universal Windows Platform (UWP) DirectX 3D game.</span></span> <span data-ttu-id="f1fe9-106">Sie können das Framework für ein Spiel (einschließlich Ansichtsanbieter und Renderingpipeline) einrichten und eine einfache Spielschleife implementieren.</span><span class="sxs-lookup"><span data-stu-id="f1fe9-106">You can set up the framework for a game, including the view provider and rendering pipeline, and implement a basic game loop.</span></span> <span data-ttu-id="f1fe9-107">Zudem können Sie ein einfaches Benutzeroberflächenoverlay erstellen und Soundeffekte und Steuerelemente einbauen.</span><span class="sxs-lookup"><span data-stu-id="f1fe9-107">You can also create a basic user interface overlay, incorporate sounds, and implement controls.</span></span> <span data-ttu-id="f1fe9-108">Sie sind auf dem Weg, Ihre eigenes Spiel zu erstellen. Wenn Sie weitere Hilfe und Informationen benötigen, sehen Sie sich diese Ressourcen an.</span><span class="sxs-lookup"><span data-stu-id="f1fe9-108">You're on your way to creating a game of your own, but if you need more help and info, check out these resources.</span></span>

-   [<span data-ttu-id="f1fe9-109">DirectX-Grafiken und -Spiele</span><span class="sxs-lookup"><span data-stu-id="f1fe9-109">DirectX Graphics and Gaming</span></span>](https://msdn.microsoft.com/library/windows/desktop/ee663274)
-   [<span data-ttu-id="f1fe9-110">Übersicht über Direct3D11</span><span class="sxs-lookup"><span data-stu-id="f1fe9-110">Direct3D 11 Overview</span></span>](https://msdn.microsoft.com/library/windows/desktop/ff476345)
-   [<span data-ttu-id="f1fe9-111">Referenz für Direct3D11</span><span class="sxs-lookup"><span data-stu-id="f1fe9-111">Direct3D 11 Reference</span></span>](https://msdn.microsoft.com/library/windows/desktop/ff476147)

## <a name="using-xaml-for-the-overlay"></a><span data-ttu-id="f1fe9-112">Verwenden von XAML für die Überlagerung</span><span class="sxs-lookup"><span data-stu-id="f1fe9-112">Using XAML for the overlay</span></span>


<span data-ttu-id="f1fe9-113">Eine Alternative, auf die wir noch nicht näher eingegangen sind, ist die Verwendung von XAML anstelle von [Direct2D](https://msdn.microsoft.com/library/windows/desktop/dd370990) für das Overlay.</span><span class="sxs-lookup"><span data-stu-id="f1fe9-113">One alternative that we didn't discuss in depth is the use of XAML instead of [Direct2D](https://msdn.microsoft.com/library/windows/desktop/dd370990) for the overlay.</span></span> <span data-ttu-id="f1fe9-114">XAML hat gegenüber Direct2D viele Vorteile, insbesondere für die Zeichnung der Elemente der Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="f1fe9-114">XAML has many benefits over Direct2D for drawing user interface elements.</span></span> <span data-ttu-id="f1fe9-115">Der wichtigste Vorteil ist, dass es macht: das Windows 10-Erscheinungsbild in Ihrem DirectX-Spiel komfortabler.</span><span class="sxs-lookup"><span data-stu-id="f1fe9-115">The most important benefit is that it makes incorporating the Windows10 look and feel into your DirectX game more convenient.</span></span> <span data-ttu-id="f1fe9-116">Viele der allgemeinen Elemente, Stile und Verhalten, die eine UWP-App ausmachen, sind eng in das XAML-Modell integriert und ersparen einem Spieleentwickler eine Menge Arbeit bei der Implementierung.</span><span class="sxs-lookup"><span data-stu-id="f1fe9-116">Many of the common elements, styles, and behaviors that define a UWP app are tightly integrated into the XAML model, making it far less work for a game developer to implement.</span></span> <span data-ttu-id="f1fe9-117">Falls Ihr eigenes Spieldesign eine komplizierte Benutzeroberfläche hat, empfiehlt sich unter Umständen die Verwendung von XAML anstelle von Direct2D.</span><span class="sxs-lookup"><span data-stu-id="f1fe9-117">If your own game design has a complicated user interface, consider using XAML instead of Direct2D.</span></span>

<span data-ttu-id="f1fe9-118">Mit XAML können wir eine Spielschnittstelle erstellen, die der vorher in Direct2D erstellten ähnelt.</span><span class="sxs-lookup"><span data-stu-id="f1fe9-118">With XAML, we can make a game interface that looks similar to the Direct2D one made earlier.</span></span>

### <a name="xaml"></a><span data-ttu-id="f1fe9-119">XAML</span><span class="sxs-lookup"><span data-stu-id="f1fe9-119">XAML</span></span>
![XAML-Überlagerung](./images/simple-dx-game-extend-xaml.PNG)

### <a name="direct2d"></a><span data-ttu-id="f1fe9-121">Direct2D</span><span class="sxs-lookup"><span data-stu-id="f1fe9-121">Direct2D</span></span>
![D2D-Überlagerung](./images/simple-dx-game-extend-d2d.PNG)

<span data-ttu-id="f1fe9-123">Während sie ähnliche Ergebnisse erhalten, gibt es eine Reihe von Unterschieden zwischen dem Implementieren von Direct2D- und XAML-Schnittstellen.</span><span class="sxs-lookup"><span data-stu-id="f1fe9-123">While they have similar end results, there are a number of differences between implementing Direct2D and XAML interfaces.</span></span>

<span data-ttu-id="f1fe9-124">Funktion</span><span class="sxs-lookup"><span data-stu-id="f1fe9-124">Feature</span></span> | <span data-ttu-id="f1fe9-125">XAML</span><span class="sxs-lookup"><span data-stu-id="f1fe9-125">XAML</span></span>| <span data-ttu-id="f1fe9-126">Direct2D</span><span class="sxs-lookup"><span data-stu-id="f1fe9-126">Direct2D</span></span>
:----------|:----------- | :-----------
<span data-ttu-id="f1fe9-127">Definieren der Überlagerung</span><span class="sxs-lookup"><span data-stu-id="f1fe9-127">Defining overlay</span></span> | <span data-ttu-id="f1fe9-128">In einer XAML-Datei definiert `\*.xaml`.</span><span class="sxs-lookup"><span data-stu-id="f1fe9-128">Defined in a XAML file, `\*.xaml`.</span></span> <span data-ttu-id="f1fe9-129">Wenn Sie XAML-Code verstehen, wird das Erstellen und Konfigurieren von komplizierteren Overlays einfacher gegenüber Direct2D.</span><span class="sxs-lookup"><span data-stu-id="f1fe9-129">Once understanding XAML, creating and configuring more complicated overlays are made simpiler when compared to Direct2D.</span></span>| <span data-ttu-id="f1fe9-130">Sie definieren das Overlay als Sammlung von Direct2D-Grundtypen und [DirectWrite](https://msdn.microsoft.com/library/windows/desktop/dd368038)-Zeichenfolgen, die manuell platziert und in einen Direct2D-Zielpuffer geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="f1fe9-130">Defined as a collection of Direct2D primitives and [DirectWrite](https://msdn.microsoft.com/library/windows/desktop/dd368038) strings manually placed and written to a Direct2D target buffer.</span></span> 
<span data-ttu-id="f1fe9-131">Benutzeroberflächenelemente</span><span class="sxs-lookup"><span data-stu-id="f1fe9-131">User interface elements</span></span> | <span data-ttu-id="f1fe9-132">Die XAML UI-Elemente basieren auf standardisierten Elementen, die Teil der XAML-APIs der Windows-Runtime sind. Hierzu gehören unter anderem [**Windows::UI::Xaml**](https://msdn.microsoft.com/library/windows/apps/br209045) und [**Windows::UI::Xaml::Controls**](https://msdn.microsoft.com/library/windows/apps/br227716).</span><span class="sxs-lookup"><span data-stu-id="f1fe9-132">XAML user interface elements come from standardized elements that are part of the Windows Runtime XAML APIs, including [**Windows::UI::Xaml**](https://msdn.microsoft.com/library/windows/apps/br209045) and [**Windows::UI::Xaml::Controls**](https://msdn.microsoft.com/library/windows/apps/br227716).</span></span> <span data-ttu-id="f1fe9-133">Der Code zum Behandeln des Verhaltens der XAML-UI-Elemente ist in der CodeBehind-Datei „Main.xaml.cpp“ definiert.</span><span class="sxs-lookup"><span data-stu-id="f1fe9-133">The code that handles the behavior of the XAML user interface elements is defined in a codebehind file, Main.xaml.cpp.</span></span> | <span data-ttu-id="f1fe9-134">Einfache Formen können z.B. wie Rechtecke und Ellipsen gezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="f1fe9-134">Simple shapes can be drawn like rectangles and ellipses.</span></span>
<span data-ttu-id="f1fe9-135">Größenanpassung der Fenster</span><span class="sxs-lookup"><span data-stu-id="f1fe9-135">Window resizing</span></span> | <span data-ttu-id="f1fe9-136">Behandelt Größenänderungen und Statusänderungsereignisse, transformiert dabei das Overlay entsprechend</span><span class="sxs-lookup"><span data-stu-id="f1fe9-136">Naturally handles resize and view state change events, transforming the overlay accordingly</span></span> | <span data-ttu-id="f1fe9-137">Es muss manuell angegeben werden, wie die Overlaykomponenten neu gezeichnet werden muss</span><span class="sxs-lookup"><span data-stu-id="f1fe9-137">Need to manually specify how to redraw the overlay's components.</span></span>


<span data-ttu-id="f1fe9-138">Ein weiterer wichtiger Unterschied ist die [Swapkette](https://docs.microsoft.com/windows/uwp/graphics-concepts/swap-chains).</span><span class="sxs-lookup"><span data-stu-id="f1fe9-138">Another big difference involves the [swap chain](https://docs.microsoft.com/windows/uwp/graphics-concepts/swap-chains).</span></span> <span data-ttu-id="f1fe9-139">Die Swapchain muss nicht direkt mit einem [**Windows::UI::Core::CoreWindow**](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow)-Objekt verknüpft werden.</span><span class="sxs-lookup"><span data-stu-id="f1fe9-139">You don't have to attach the swap chain to a [**Windows::UI::Core::CoreWindow**](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow) object.</span></span> <span data-ttu-id="f1fe9-140">Stattdessen ordnet eine DirectX-App mit XAML eine Swapchain zu, wenn ein neues [**SwapChainPanel**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.swapchainpanel)-Objekt konstruiert wird.</span><span class="sxs-lookup"><span data-stu-id="f1fe9-140">Instead, a DirectX app that incorporates XAML associates a swap chain when a new [**SwapChainPanel**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.swapchainpanel) object is constructed.</span></span> 

<span data-ttu-id="f1fe9-141">Der folgende Codeausschnitt zeigt, wie Sie XAML-Code für das **SwapChainPanel** in der [**DirectXPage.xaml**](https://github.com/Microsoft/Windows-universal-samples/blob/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/Simple3DGameXaml/cpp/DirectXPage.xaml)-Datei deklarieren.</span><span class="sxs-lookup"><span data-stu-id="f1fe9-141">The following snippet show how to declare XAML for the **SwapChainPanel** in the [**DirectXPage.xaml**](https://github.com/Microsoft/Windows-universal-samples/blob/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/Simple3DGameXaml/cpp/DirectXPage.xaml) file.</span></span>
```xml
<Page
    x:Class="Simple3DGameXaml.DirectXPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:Simple3DGameXaml"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d">


    <SwapChainPanel x:Name="DXSwapChainPanel">

    <!-- ... XAML user controls and elements -->

    </SwapChainPanel>
</Page>
```

<span data-ttu-id="f1fe9-142">Das **SwapChainPanel**-Objekt wird als [**Content**](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Window.Content)-Eigenschaft des aktuellen Fensterobjekts festgelegt, das [beim Start](https://github.com/Microsoft/Windows-universal-samples/blob/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/Simple3DGameXaml/cpp/App.xaml.cpp#L45-L51)  durch das Singleton erstellt wurde</span><span class="sxs-lookup"><span data-stu-id="f1fe9-142">The **SwapChainPanel** object is set as the [**Content**](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Window.Content) property of the current window object created [at launch](https://github.com/Microsoft/Windows-universal-samples/blob/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/Simple3DGameXaml/cpp/App.xaml.cpp#L45-L51) by the app singleton.</span></span>

```cpp
void App::OnLaunched(_In_ LaunchActivatedEventArgs^ /* args */)
{
    m_mainPage = ref new DirectXPage();

    Window::Current->Content = m_mainPage;
    // Bring the application to the foreground so that it's visible
    Window::Current->Activate();
}
```


<span data-ttu-id="f1fe9-143">Um die konfigurierte Swapchain der [**SwapChainPanel**](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.SwapChainPanel)-Bereichsinstanz zuzuordnen, die Sie mit XAML definiert haben, müssen Sie einen Zeiger auf die zugrunde liegende Implementierung der systemeigenen [**ISwapChainPanelNative**](https://msdn.microsoft.com/library/dn302143)-Schnittstelle abrufen und in einem entsprechenden Aufruf von [**ISwapChainPanelNative::SetSwapChain**](https://msdn.microsoft.com/library/windows/desktop/dn302144) Ihre konfigurierte Swapchain übergeben.</span><span class="sxs-lookup"><span data-stu-id="f1fe9-143">To attach the configured swap chain to the [**SwapChainPanel**](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.SwapChainPanel) instance defined by your XAML, you must obtain a pointer to the underlying native [**ISwapChainPanelNative**](https://msdn.microsoft.com/library/dn302143) interface implementation and call [**ISwapChainPanelNative::SetSwapChain**](https://msdn.microsoft.com/library/windows/desktop/dn302144) on it, passing it your configured swap chain.</span></span> 

<span data-ttu-id="f1fe9-144">Der folgende Codeausschnitt aus [**DX::DeviceResources::CreateWindowSizeDependentResources**](https://github.com/Microsoft/Windows-universal-samples/blob/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/Simple3DGameXaml/cpp/Common/DeviceResources.cpp#L218-L521) gibt Details für DirectX/XAML-Interoperabilität an:</span><span class="sxs-lookup"><span data-stu-id="f1fe9-144">The following snippet from  [**DX::DeviceResources::CreateWindowSizeDependentResources**](https://github.com/Microsoft/Windows-universal-samples/blob/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/Simple3DGameXaml/cpp/Common/DeviceResources.cpp#L218-L521) details this for DirectX/XAML interop:</span></span>

```cpp
        ComPtr<IDXGIDevice3> dxgiDevice;
        DX::ThrowIfFailed(
            m_d3dDevice.As(&dxgiDevice)
            );

        ComPtr<IDXGIAdapter> dxgiAdapter;
        DX::ThrowIfFailed(
            dxgiDevice->GetAdapter(&dxgiAdapter)
            );

        ComPtr<IDXGIFactory2> dxgiFactory;
        DX::ThrowIfFailed(
            dxgiAdapter->GetParent(IID_PPV_ARGS(&dxgiFactory))
            );

        // When using XAML interop, the swap chain must be created for composition.
        DX::ThrowIfFailed(
            dxgiFactory->CreateSwapChainForComposition(
                m_d3dDevice.Get(),
                &swapChainDesc,
                nullptr,
                &m_swapChain
                )
            );

        // Associate swap chain with SwapChainPanel
        // UI changes will need to be dispatched back to the UI thread
        m_swapChainPanel->Dispatcher->RunAsync(CoreDispatcherPriority::High, ref new DispatchedHandler([=]()
        {
            // Get backing native interface for SwapChainPanel
            ComPtr<ISwapChainPanelNative> panelNative;
            DX::ThrowIfFailed(
                reinterpret_cast<IUnknown*>(m_swapChainPanel)->QueryInterface(IID_PPV_ARGS(&panelNative))
                );
            DX::ThrowIfFailed(
                panelNative->SetSwapChain(m_swapChain.Get())
                );
        }, CallbackContext::Any));

        // Ensure that DXGI does not queue more than one frame at a time. This both reduces latency and
        // ensures that the application will only render after each VSync, minimizing power consumption.
        DX::ThrowIfFailed(
            dxgiDevice->SetMaximumFrameLatency(1)
            );
    }
```

<span data-ttu-id="f1fe9-145">Weitere Informationen zu diesem Prozess finden Sie unter [Interoperabilität von DirectX und XAML](directx-and-xaml-interop.md).</span><span class="sxs-lookup"><span data-stu-id="f1fe9-145">For more info about this process, see [DirectX and XAML interop](directx-and-xaml-interop.md).</span></span>

## <a name="sample"></a><span data-ttu-id="f1fe9-146">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f1fe9-146">Sample</span></span>

<span data-ttu-id="f1fe9-147">Eine Version des Spiels, die XAML für das Overlay verwendet, finden Sie in [Beispiel für einen Direct3D-Shooter (XAML)](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Simple3DGameXaml).</span><span class="sxs-lookup"><span data-stu-id="f1fe9-147">To download the version of this game that uses XAML for the overlay, go to the [Direct3D shooting game sample (XAML)](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Simple3DGameXaml).</span></span>


<span data-ttu-id="f1fe9-148">(Im Gegensatz zur in den anderen Themen behandelten Version des Spielbeispiels definiert die XAML-Version ihr Framework nicht in den Dateien [App.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/Simple3DGameDX/cpp/App.cpp) und [GameInfoOverlay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp), sondern in den Dateien [App.xaml.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/Simple3DGameXaml/cpp/App.xaml.cpp) und [DirectXPage.xaml.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/Simple3DGameXaml/cpp/DirectXPage.xaml.cpp).)</span><span class="sxs-lookup"><span data-stu-id="f1fe9-148">Unlike the version of the game sample discussed in the rest of these topics, the XAML version defines its framework in the [App.xaml.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/Simple3DGameXaml/cpp/App.xaml.cpp) and [DirectXPage.xaml.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/Simple3DGameXaml/cpp/DirectXPage.xaml.cpp) files, instead of [App.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/Simple3DGameDX/cpp/App.cpp) and [GameInfoOverlay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp), respectively.</span></span>