---
title: Reduzieren der Latenz mit DXGI1.3-Swapchains
description: Verwenden Sie DXGI1.3 zum Reduzieren der geltenden Framelatenz, indem Sie warten, bis die Swapchain den geeigneten Zeitpunkt zum Beginnen mit dem Rendern eines neuen Frames signalisiert.
ms.assetid: c99b97ed-a757-879f-3d55-7ed77133f6ce
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Latenz, DXGI, Swapchains, Directx
ms.localizationpriority: medium
ms.openlocfilehash: ec315cc9ed59a4b3272151f2ee1bb4bde8d9df10
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7834335"
---
# <a name="reduce-latency-with-dxgi-13-swap-chains"></a><span data-ttu-id="36ccb-104">Reduzieren der Latenz mit DXGI 1.3-Swapchains</span><span class="sxs-lookup"><span data-stu-id="36ccb-104">Reduce latency with DXGI 1.3 swap chains</span></span>



<span data-ttu-id="36ccb-105">Verwenden Sie DXGI 1.3 zum Reduzieren der geltenden Framelatenz, indem Sie warten, bis die Swapchain den geeigneten Zeitpunkt zum Beginnen mit dem Rendern eines neuen Frames signalisiert.</span><span class="sxs-lookup"><span data-stu-id="36ccb-105">Use DXGI 1.3 to reduce the effective frame latency by waiting for the swap chain to signal the appropriate time to begin rendering a new frame.</span></span> <span data-ttu-id="36ccb-106">Spiele müssen in der Regel die geringstmögliche Latenz aufweisen, was den Zeitraum vom Eingang der Spielereingabe bis zur Reaktion des Spiels auf die Eingabe betrifft, indem die Anzeige aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="36ccb-106">Games typically need to provide the lowest amount of latency possible from the time the player input is received, to when the game responds to that input by updating the display.</span></span> <span data-ttu-id="36ccb-107">In diesem Thema wird ein Verfahren erläutert, das ab Version Direct3D11.2 verfügbar ist. Damit können Sie in Ihrem Spiel die geltende Framelatenz verringern.</span><span class="sxs-lookup"><span data-stu-id="36ccb-107">This topic explains a technique available starting in Direct3D 11.2 that you can use to minimize the effective frame latency in your game.</span></span>

## <a name="how-does-waiting-on-the-back-buffer-reduce-latency"></a><span data-ttu-id="36ccb-108">Wie kann mit dem Warten auf den Hintergrundpuffer die Latenz reduziert werden?</span><span class="sxs-lookup"><span data-stu-id="36ccb-108">How does waiting on the back buffer reduce latency?</span></span>


<span data-ttu-id="36ccb-109">Bei der Flipmodell-Swapchain werden „Flips“ des Hintergrundpuffers jeweils in die Warteschlange eingereiht, wenn vom Spiel [**IDXGISwapChain::Present**](https://msdn.microsoft.com/library/windows/desktop/bb174576) aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="36ccb-109">With the flip model swap chain, back buffer "flips" are queued whenever your game calls [**IDXGISwapChain::Present**](https://msdn.microsoft.com/library/windows/desktop/bb174576).</span></span> <span data-ttu-id="36ccb-110">Wenn von der Renderschleife „Present()“ aufgerufen wird, blockiert das System den Thread, bis die Darstellung eines vorherigen Frames abgeschlossen ist. So wird in der Warteschlange Platz für den neuen Frame geschaffen, bevor dieser dargestellt wird.</span><span class="sxs-lookup"><span data-stu-id="36ccb-110">When the rendering loop calls Present(), the system blocks the thread until it is done presenting a prior frame, making room to queue up the new frame, before it actually presents.</span></span> <span data-ttu-id="36ccb-111">Dies verursacht zusätzliche Latenz zwischen dem Zeitpunkt, zu dem vom Spiel ein Frame gezeichnet wird, und dem Zeitpunkt, zu dem die Anzeige des Frames vom System zugelassen wird.</span><span class="sxs-lookup"><span data-stu-id="36ccb-111">This causes extra latency between the time the game draws a frame and the time the system allows it to display that frame.</span></span> <span data-ttu-id="36ccb-112">In vielen Fällen wird vom System ein stabiles Gleichgewicht erreicht, bei dem vom Spiel zwischen dem Rendern und Darstellen des Frames immer nahezu einen ganzen zusätzlichen Frame lang abgewartet wird.</span><span class="sxs-lookup"><span data-stu-id="36ccb-112">In many cases, the system will reach a stable equilibrium where the game is always waiting almost a full extra frame between the time it renders and the time it presents each frame.</span></span> <span data-ttu-id="36ccb-113">Es ist besser zu warten, bis das System zum Akzeptieren eines neuen Frames bereit ist, als den Frame basierend auf den aktuellen Daten zu rendern und sofort in die Warteschlange einzureihen.</span><span class="sxs-lookup"><span data-stu-id="36ccb-113">It's better to wait until the system is ready to accept a new frame, then render the frame based on current data and queue the frame immediately.</span></span>

<span data-ttu-id="36ccb-114">Erstellen Sie eine Swapchain mit Wartemöglichkeit, indem Sie das [**DXGI\_SWAP\_CHAIN\_FLAG\_FRAME\_LATENCY\_WAITABLE\_OBJECT**](https://msdn.microsoft.com/library/windows/desktop/bb173076)-Flag verwenden.</span><span class="sxs-lookup"><span data-stu-id="36ccb-114">Create a waitable swap chain with the [**DXGI\_SWAP\_CHAIN\_FLAG\_FRAME\_LATENCY\_WAITABLE\_OBJECT**](https://msdn.microsoft.com/library/windows/desktop/bb173076) flag.</span></span> <span data-ttu-id="36ccb-115">Swapchains, die auf diese Art erstellt werden, können Ihre Renderschleife benachrichtigen, wenn das System zum Akzeptieren eines neuen Frames bereit ist.</span><span class="sxs-lookup"><span data-stu-id="36ccb-115">Swap chains created this way can notify your rendering loop when the system is actually ready to accept a new frame.</span></span> <span data-ttu-id="36ccb-116">So kann das Spiel anhand der aktuellen Daten rendern und das Ergebnis sofort in die vorhandene Warteschlange einfügen.</span><span class="sxs-lookup"><span data-stu-id="36ccb-116">This allows your game to render based on current data and then put the result in the present queue right away.</span></span>

## <a name="step-1-create-a-waitable-swap-chain"></a><span data-ttu-id="36ccb-117">Schritt 1: Erstellen einer Swapchain mit Wartemöglichkeit</span><span class="sxs-lookup"><span data-stu-id="36ccb-117">Step 1: Create a waitable swap chain</span></span>


<span data-ttu-id="36ccb-118">Geben Sie das [**DXGI\_SWAP\_CHAIN\_FLAG\_FRAME\_LATENCY\_WAITABLE\_OBJECT**](https://msdn.microsoft.com/library/windows/desktop/bb173076)-Flag an, wenn Sie [**CreateSwapChainForCoreWindow**](https://msdn.microsoft.com/library/windows/desktop/hh404559) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="36ccb-118">Specify the [**DXGI\_SWAP\_CHAIN\_FLAG\_FRAME\_LATENCY\_WAITABLE\_OBJECT**](https://msdn.microsoft.com/library/windows/desktop/bb173076) flag when you call [**CreateSwapChainForCoreWindow**](https://msdn.microsoft.com/library/windows/desktop/hh404559).</span></span>

```cpp
swapChainDesc.Flags = DXGI_SWAP_CHAIN_FLAG_FRAME_LATENCY_WAITABLE_OBJECT; // Enable GetFrameLatencyWaitableObject().
```

> <span data-ttu-id="36ccb-119">**Hinweis:**  Flags dieses Flag kann nicht hinzugefügt oder entfernt werden mithilfe von [**ResizeBuffers**](https://msdn.microsoft.com/library/windows/desktop/bb174577).</span><span class="sxs-lookup"><span data-stu-id="36ccb-119">**Note** In contrast to some flags, this flag can't be added or removed using [**ResizeBuffers**](https://msdn.microsoft.com/library/windows/desktop/bb174577).</span></span> <span data-ttu-id="36ccb-120">Von DXGI wird ein Fehlercode zurückgegeben, wenn dieses Flag anders als bei der Erstellung der Swapchain festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="36ccb-120">DXGI returns an error code if this flag is set differently from when the swap chain was created.</span></span>

 

```cpp
// If the swap chain already exists, resize it.
HRESULT hr = m_swapChain->ResizeBuffers(
    2, // Double-buffered swap chain.
    static_cast<UINT>(m_d3dRenderTargetSize.Width),
    static_cast<UINT>(m_d3dRenderTargetSize.Height),
    DXGI_FORMAT_B8G8R8A8_UNORM,
    DXGI_SWAP_CHAIN_FLAG_FRAME_LATENCY_WAITABLE_OBJECT // Enable GetFrameLatencyWaitableObject().
    );
```

## <a name="step-2-set-the-frame-latency"></a><span data-ttu-id="36ccb-121">Schritt 2: Festlegen der Framelatenz</span><span class="sxs-lookup"><span data-stu-id="36ccb-121">Step 2: Set the frame latency</span></span>


<span data-ttu-id="36ccb-122">Legen Sie die Framelatenz mit der [**IDXGISwapChain2::SetMaximumFrameLatency**](https://msdn.microsoft.com/library/windows/desktop/dn268313)-API fest, anstatt [**IDXGIDevice1::SetMaximumFrameLatency**](https://msdn.microsoft.com/library/windows/desktop/ff471334) aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="36ccb-122">Set the frame latency with the [**IDXGISwapChain2::SetMaximumFrameLatency**](https://msdn.microsoft.com/library/windows/desktop/dn268313) API, instead of calling [**IDXGIDevice1::SetMaximumFrameLatency**](https://msdn.microsoft.com/library/windows/desktop/ff471334).</span></span>

<span data-ttu-id="36ccb-123">Standardmäßig ist die Framelatenz für Swapchains mit Wartemöglichkeit auf 1 festgelegt. Dies führt zur geringstmöglichen Latenz, jedoch auch zu einer Reduzierung der CPU-GPU-Parallelität.</span><span class="sxs-lookup"><span data-stu-id="36ccb-123">By default, the frame latency for waitable swap chains is set to 1, which results in the least possible latency but also reduces CPU-GPU parallelism.</span></span> <span data-ttu-id="36ccb-124">Falls Sie eine höhere CPU-GPU-Parallelität benötigen, um 60 F/s zu erzielen – also wenn die CPU und GPU jeweils weniger als 16,7 ms pro Frame für die Verarbeitung des Renderns aufwendet, die Summe jedoch größer als 16,7 ms ist – legen Sie die Framelatenz auf 2 fest.</span><span class="sxs-lookup"><span data-stu-id="36ccb-124">If you need increased CPU-GPU parallelism to achieve 60 FPS - that is, if the CPU and GPU each spend less than 16.7 ms a frame processing rendering work, but their combined sum is greater than 16.7 ms — set the frame latency to 2.</span></span> <span data-ttu-id="36ccb-125">Auf diese Weise können von der GPU Verarbeitungsschritte ausgeführt werden, die von der CPU während des vorherigen Frames in die Warteschlange eingereiht wurden, während die CPU unabhängig davon gleichzeitig Renderbefehle für den aktuellen Frame übermitteln kann.</span><span class="sxs-lookup"><span data-stu-id="36ccb-125">This allows the GPU to process work queued up by the CPU during the previous frame, while at the same time allowing the CPU to submit rendering commands for the current frame independently.</span></span>

```cpp
// Swapchains created with the DXGI_SWAP_CHAIN_FLAG_FRAME_LATENCY_WAITABLE_OBJECT flag use their
// own per-swapchain latency setting instead of the one associated with the DXGI device. The
// default per-swapchain latency is 1, which ensures that DXGI does not queue more than one frame
// at a time. This both reduces latency and ensures that the application will only render after
// each VSync, minimizing power consumption.
//DX::ThrowIfFailed(
//    swapChain2->SetMaximumFrameLatency(1)
//    );
```

## <a name="step-3-get-the-waitable-object-from-the-swap-chain"></a><span data-ttu-id="36ccb-126">Schritt 3: Abrufen des Objekts mit Wartemöglichkeit aus der Swapchain</span><span class="sxs-lookup"><span data-stu-id="36ccb-126">Step 3: Get the waitable object from the swap chain</span></span>


<span data-ttu-id="36ccb-127">Rufen Sie [**IDXGISwapChain2::GetFrameLatencyWaitableObject**](https://msdn.microsoft.com/library/windows/desktop/dn268309) auf, um das „wait“-Handle abzurufen.</span><span class="sxs-lookup"><span data-stu-id="36ccb-127">Call [**IDXGISwapChain2::GetFrameLatencyWaitableObject**](https://msdn.microsoft.com/library/windows/desktop/dn268309) to retrieve the wait handle.</span></span> <span data-ttu-id="36ccb-128">Das „wait“-Handle ist ein Zeiger auf das Objekt mit Wartemöglichkeit.</span><span class="sxs-lookup"><span data-stu-id="36ccb-128">The wait handle is a pointer to the waitable object.</span></span> <span data-ttu-id="36ccb-129">Speichern Sie dieses Handle für die Verwendung durch die Renderschleife.</span><span class="sxs-lookup"><span data-stu-id="36ccb-129">Store this handle for use by your rendering loop.</span></span>

```cpp
// Get the frame latency waitable object, which is used by the WaitOnSwapChain method. This
// requires that swap chain be created with the DXGI_SWAP_CHAIN_FLAG_FRAME_LATENCY_WAITABLE_OBJECT
// flag.
m_frameLatencyWaitableObject = swapChain2->GetFrameLatencyWaitableObject();
```

## <a name="step-4-wait-before-rendering-each-frame"></a><span data-ttu-id="36ccb-130">Schritt4: Warten vor dem Rendern der einzelnen Frames</span><span class="sxs-lookup"><span data-stu-id="36ccb-130">Step 4: Wait before rendering each frame</span></span>


<span data-ttu-id="36ccb-131">Die Renderschleife sollte warten, bis die Swapchain über das Objekt mit Wartemöglichkeit ein Signal sendet, bevor sie mit dem Rendern eines Frames beginnt.</span><span class="sxs-lookup"><span data-stu-id="36ccb-131">Your rendering loop should wait for the swap chain to signal via the waitable object before it begins rendering every frame.</span></span> <span data-ttu-id="36ccb-132">Dies gilt auch für den ersten Frame, der mit der Swapchain gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="36ccb-132">This includes the first frame rendered with the swap chain.</span></span> <span data-ttu-id="36ccb-133">Verwenden Sie [**WaitForSingleObjectEx**](https://msdn.microsoft.com/library/windows/desktop/ms687036), und stellen Sie das in Schritt 2 abgerufene „wait“-Handle bereit, um den Start eines Frames zu signalisieren.</span><span class="sxs-lookup"><span data-stu-id="36ccb-133">Use [**WaitForSingleObjectEx**](https://msdn.microsoft.com/library/windows/desktop/ms687036), providing the wait handle retrieved in Step 2, to signal the start of each frame.</span></span>

<span data-ttu-id="36ccb-134">Im folgenden Beispiel wird die Renderschleife aus dem DirectXLatency-Beispiel veranschaulicht:</span><span class="sxs-lookup"><span data-stu-id="36ccb-134">The following example shows the render loop from the DirectXLatency sample:</span></span>

```cpp
while (!m_windowClosed)
{
    if (m_windowVisible)
    {
        // Block this thread until the swap chain is finished presenting. Note that it is
        // important to call this before the first Present in order to minimize the latency
        // of the swap chain.
        m_deviceResources->WaitOnSwapChain();

        // Process any UI events in the queue.
        CoreWindow::GetForCurrentThread()->Dispatcher->ProcessEvents(CoreProcessEventsOption::ProcessAllIfPresent);

        // Update app state in response to any UI events that occurred.
        m_main->Update();

        // Render the scene.
        m_main->Render();

        // Present the scene.
        m_deviceResources->Present();
    }
    else
    {
        // The window is hidden. Block until a UI event occurs.
        CoreWindow::GetForCurrentThread()->Dispatcher->ProcessEvents(CoreProcessEventsOption::ProcessOneAndAllPending);
    }
}
```

<span data-ttu-id="36ccb-135">Im folgenden Beispiel wird der WaitForSingleObjectEx-Aufruf aus dem DirectXLatency-Beispiel veranschaulicht:</span><span class="sxs-lookup"><span data-stu-id="36ccb-135">The following example shows the WaitForSingleObjectEx call from the DirectXLatency sample:</span></span>

```cpp
// Block the current thread until the swap chain has finished presenting.
void DX::DeviceResources::WaitOnSwapChain()
{
    DWORD result = WaitForSingleObjectEx(
        m_frameLatencyWaitableObject,
        1000, // 1 second timeout (shouldn't ever occur)
        true
        );
}
```

## <a name="what-should-my-game-do-while-it-waits-for-the-swap-chain-to-present"></a><span data-ttu-id="36ccb-136">Wie soll sich das Spiel verhalten, während es auf die Swapchain wartet?</span><span class="sxs-lookup"><span data-stu-id="36ccb-136">What should my game do while it waits for the swap chain to present?</span></span>


<span data-ttu-id="36ccb-137">Falls Ihr Spiel nicht über Aufgaben verfügt, die zu einer Blockierung der Renderschleife führen, kann die Nutzung des Wartens auf die Swapchain vorteilhaft sein, weil so Energie gespart wird. Dies ist besonders für mobile Geräte wichtig.</span><span class="sxs-lookup"><span data-stu-id="36ccb-137">If your game doesn’t have any tasks that block on the render loop, letting it wait for the swap chain to present can be advantageous because it saves power, which is especially important on mobile devices.</span></span> <span data-ttu-id="36ccb-138">Andernfalls können Sie das Multithreading nutzen, um Verarbeitungsschritte auszuführen, während das Spiel auf die Swapchain wartet.</span><span class="sxs-lookup"><span data-stu-id="36ccb-138">Otherwise, you can use multithreading to accomplish work while your game is waiting for the swap chain to present.</span></span> <span data-ttu-id="36ccb-139">Unten sind einige Aufgaben aufgeführt, die vom Spiel ausgeführt werden können:</span><span class="sxs-lookup"><span data-stu-id="36ccb-139">Here are just a few tasks that your game can complete:</span></span>

-   <span data-ttu-id="36ccb-140">Verarbeiten von Netzwerkereignissen</span><span class="sxs-lookup"><span data-stu-id="36ccb-140">Process network events</span></span>
-   <span data-ttu-id="36ccb-141">Aktualisieren der künstlichen Intelligenz</span><span class="sxs-lookup"><span data-stu-id="36ccb-141">Update the AI</span></span>
-   <span data-ttu-id="36ccb-142">CPU-basierte Physik</span><span class="sxs-lookup"><span data-stu-id="36ccb-142">CPU-based physics</span></span>
-   <span data-ttu-id="36ccb-143">Rendern mit verzögertem Kontext (auf unterstützten Geräten)</span><span class="sxs-lookup"><span data-stu-id="36ccb-143">Deferred-context rendering (on supported devices)</span></span>
-   <span data-ttu-id="36ccb-144">Laden von Ressourcen</span><span class="sxs-lookup"><span data-stu-id="36ccb-144">Asset loading</span></span>

<span data-ttu-id="36ccb-145">Weitere Informationen zur Programmierung mit Multithreading unter Windows finden Sie in den folgenden verwandten Themen.</span><span class="sxs-lookup"><span data-stu-id="36ccb-145">For more information about multithreaded programming in Windows, see the following related topics.</span></span>

## <a name="related-topics"></a><span data-ttu-id="36ccb-146">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="36ccb-146">Related topics</span></span>


* [<span data-ttu-id="36ccb-147">DirectXLatency-Beispiel</span><span class="sxs-lookup"><span data-stu-id="36ccb-147">DirectXLatency sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=317361)
* [**<span data-ttu-id="36ccb-148">IDXGISwapChain2::GetFrameLatencyWaitableObject</span><span class="sxs-lookup"><span data-stu-id="36ccb-148">IDXGISwapChain2::GetFrameLatencyWaitableObject</span></span>**](https://msdn.microsoft.com/library/windows/desktop/dn268309)
* [**<span data-ttu-id="36ccb-149">WaitForSingleObjectEx</span><span class="sxs-lookup"><span data-stu-id="36ccb-149">WaitForSingleObjectEx</span></span>**](https://msdn.microsoft.com/library/windows/desktop/ms687036)
* [**<span data-ttu-id="36ccb-150">Windows.System.Threading</span><span class="sxs-lookup"><span data-stu-id="36ccb-150">Windows.System.Threading</span></span>**](https://msdn.microsoft.com/library/windows/apps/br229642)
* [<span data-ttu-id="36ccb-151">Asynchrone Programmierung in C++</span><span class="sxs-lookup"><span data-stu-id="36ccb-151">Asynchronous programming in C++</span></span>](https://msdn.microsoft.com/library/windows/apps/mt187334)
* [<span data-ttu-id="36ccb-152">Prozesse und Threads</span><span class="sxs-lookup"><span data-stu-id="36ccb-152">Processes and Threads</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms684841)
* [<span data-ttu-id="36ccb-153">Synchronisierung</span><span class="sxs-lookup"><span data-stu-id="36ccb-153">Synchronization</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms686353)
* [<span data-ttu-id="36ccb-154">Verwenden von Ereignisobjekten (Windows)</span><span class="sxs-lookup"><span data-stu-id="36ccb-154">Using Event Objects (Windows)</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms686915)

 

 




