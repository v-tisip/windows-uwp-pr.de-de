---
title: Behandeln von Szenarien mit entfernten Geräten in Direct3D11
description: In diesem Thema wird erläutert, wie Sie die Geräteschnittstellenkette für Direct3D und DXGI neu erstellen, wenn die Grafikkarte entfernt oder neu initialisiert wird.
ms.assetid: 8f905acd-08f3-ff6f-85a5-aaa99acb389a
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, DirectX 11, Gerät verloren gegangen
ms.localizationpriority: medium
ms.openlocfilehash: c11bbf7657644fbf616590f50d75d93f62ed993e
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7846838"
---
# <a name="span-iddevgaminghandlingdevice-lostscenariosspanhandle-device-removed-scenarios-in-direct3d-11"></a><span data-ttu-id="fe85a-104"><span id="dev_gaming.handling_device-lost_scenarios"></span>Behandeln von Szenarien mit entfernten Geräten in Direct3D 11</span><span class="sxs-lookup"><span data-stu-id="fe85a-104"><span id="dev_gaming.handling_device-lost_scenarios"></span>Handle device removed scenarios in Direct3D 11</span></span>



<span data-ttu-id="fe85a-105">In diesem Thema wird erläutert, wie Sie die Geräteschnittstellenkette für Direct3D und DXGI neu erstellen, wenn die Grafikkarte entfernt oder neu initialisiert wird.</span><span class="sxs-lookup"><span data-stu-id="fe85a-105">This topic explains how to recreate the Direct3D and DXGI device interface chain when the graphics adapter is removed or reinitialized.</span></span>

<span data-ttu-id="fe85a-106">In DirectX9 kann für Anwendungen die Bedingung "[Gerät ist nicht mehr auffindbar](https://msdn.microsoft.com/library/windows/desktop/bb174714)" entstehen, bei der das D3D-Gerät nicht mehr betriebsbereit ist.</span><span class="sxs-lookup"><span data-stu-id="fe85a-106">In DirectX 9, applications could encounter a "[device lost](https://msdn.microsoft.com/library/windows/desktop/bb174714)" condition where the D3D device enters a non-operational state.</span></span> <span data-ttu-id="fe85a-107">Wenn eine Direct3D9-Vollbildanwendung den Fokus verliert, ist das Direct3D-Gerät „nicht mehr auffindbar“. Alle Versuche, mit einem nicht auffindbaren Gerät zu zeichnen, sind nicht erfolgreich (ohne Warnung).</span><span class="sxs-lookup"><span data-stu-id="fe85a-107">For example, when a full-screen Direct3D 9 application loses focus, the Direct3D device becomes "lost;" any attempts to draw with a lost device will silently fail.</span></span> <span data-ttu-id="fe85a-108">Für Direct3D11 werden virtuelle Grafikgerätschnittstellen verwendet, damit mehrere Programme dasselbe physische Grafikgerät nutzen können und keine Bedingungen entstehen, in denen Apps die Kontrolle über das Direct3D-Gerät verlieren.</span><span class="sxs-lookup"><span data-stu-id="fe85a-108">Direct3D 11 uses virtual graphics device interfaces, enabling multiple programs to share the same physical graphics device and eliminating conditions where apps lose control of the Direct3D device.</span></span> <span data-ttu-id="fe85a-109">Es ist jedoch weiterhin möglich, dass sich die Verfügbarkeit der Grafikkarte ändert.</span><span class="sxs-lookup"><span data-stu-id="fe85a-109">However, it is still possible for graphics adapter availability to change.</span></span> <span data-ttu-id="fe85a-110">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="fe85a-110">For example:</span></span>

-   <span data-ttu-id="fe85a-111">Der Grafiktreiber wird aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="fe85a-111">The graphics driver is upgraded.</span></span>
-   <span data-ttu-id="fe85a-112">Das System führt eine Umstellung von einer energiesparenden Grafikkarte auf eine Grafikkarte mit hoher Leistung durch.</span><span class="sxs-lookup"><span data-stu-id="fe85a-112">The system changes from a power-saving graphics adapter to a performance graphics adapter.</span></span>
-   <span data-ttu-id="fe85a-113">Das Grafikgerät reagiert nicht mehr und wird zurückgesetzt.</span><span class="sxs-lookup"><span data-stu-id="fe85a-113">The graphics device stops responding and is reset.</span></span>
-   <span data-ttu-id="fe85a-114">Eine Grafikkarte wird physisch angeschlossen oder entfernt.</span><span class="sxs-lookup"><span data-stu-id="fe85a-114">A graphics adapter is physically attached or removed.</span></span>

<span data-ttu-id="fe85a-115">Unter diesen Umständen wird von DXGI ein Fehlercode zurückgegeben, der angibt, dass das Direct3D-Gerät neu initialisiert werden muss und die Geräteressourcen neu erstellt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="fe85a-115">When such circumstances arise, DXGI returns an error code indicating that the Direct3D device must be reinitialized and device resources must be recreated.</span></span> <span data-ttu-id="fe85a-116">In dieser exemplarischen Vorgehensweise wird erläutert, wie Direct3D11-Apps und -Spiele Fälle, in denen die Grafikkarte zurückgesetzt, entfernt oder geändert wird, erkennen und darauf reagieren kann.</span><span class="sxs-lookup"><span data-stu-id="fe85a-116">This walkthrough explains how Direct3D 11 apps and games can detect and respond to any circumstance where the graphics adapter is reset, removed, or changed.</span></span> <span data-ttu-id="fe85a-117">Codebeispiele sind in der Vorlage DirectX 11-App (Universal Windows) in Microsoft Visual Studio2015 bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="fe85a-117">Code examples are provided from the DirectX 11 App (Universal Windows) template provided with Microsoft Visual Studio2015.</span></span>

## <a name="instructions"></a><span data-ttu-id="fe85a-118">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="fe85a-118">Instructions</span></span>

### <a name="spanspanstep-1"></a><span data-ttu-id="fe85a-119"><span></span>Schritt1:</span><span class="sxs-lookup"><span data-stu-id="fe85a-119"><span></span>Step 1:</span></span>

<span data-ttu-id="fe85a-120">Fügen Sie eine Überprüfung auf den Fehler „Gerät entfernt“ in die Renderschleife ein.</span><span class="sxs-lookup"><span data-stu-id="fe85a-120">Include a check for the device removed error in the rendering loop.</span></span> <span data-ttu-id="fe85a-121">Stellen Sie den Frame dar, indem Sie [**IDXGISwapChain::Present**](https://msdn.microsoft.com/library/windows/desktop/bb174576) (bzw. [**Present1**](https://msdn.microsoft.com/library/windows/desktop/hh446797) usw.) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="fe85a-121">Present the frame by calling [**IDXGISwapChain::Present**](https://msdn.microsoft.com/library/windows/desktop/bb174576) (or [**Present1**](https://msdn.microsoft.com/library/windows/desktop/hh446797), and so on).</span></span> <span data-ttu-id="fe85a-122">Prüfen Sie anschließend, ob [**DXGI\_ERROR\_DEVICE\_REMOVED**](https://msdn.microsoft.com/library/windows/desktop/bb509553) or **DXGI\_ERROR\_DEVICE\_RESET** zurückgegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="fe85a-122">Then, check whether it returned [**DXGI\_ERROR\_DEVICE\_REMOVED**](https://msdn.microsoft.com/library/windows/desktop/bb509553) or **DXGI\_ERROR\_DEVICE\_RESET**.</span></span>

<span data-ttu-id="fe85a-123">Zuerst wird in der Vorlage der HRESULT-Wert gespeichert, der von der DXGI-Swapchain zurückgegeben wird:</span><span class="sxs-lookup"><span data-stu-id="fe85a-123">First, the template stores the HRESULT returned by the DXGI swap chain:</span></span>

```cpp
HRESULT hr = m_swapChain->Present(1, 0);
```

<span data-ttu-id="fe85a-124">Nachdem Sie alle anderen Schritte zum Darstellen des Frames ausgeführt haben, führt die Vorlage eine Überprüfung auf den Fehler aufgrund eines entfernten Geräts durch.</span><span class="sxs-lookup"><span data-stu-id="fe85a-124">After taking care of all other work for presenting the frame, the template checks for the device removed error.</span></span> <span data-ttu-id="fe85a-125">Bei Bedarf wird eine Methode zum Behandeln der Bedingung „Gerät entfernt“ aufgerufen:</span><span class="sxs-lookup"><span data-stu-id="fe85a-125">If necessary, it calls a method to handle the device removed condition:</span></span>

```cpp
// If the device was removed either by a disconnection or a driver upgrade, we
// must recreate all device resources.
if (hr == DXGI_ERROR_DEVICE_REMOVED || hr == DXGI_ERROR_DEVICE_RESET)
{
    HandleDeviceLost();
}
else
{
    DX::ThrowIfFailed(hr);
}
```

### <a name="step-2"></a><span data-ttu-id="fe85a-126">Schritt2:</span><span class="sxs-lookup"><span data-stu-id="fe85a-126">Step 2:</span></span>

<span data-ttu-id="fe85a-127">Fügen Sie auch eine Überprüfung auf den Fehler „Gerät entfernt“ ein, wenn Sie auf Änderungen der Fenstergröße reagieren.</span><span class="sxs-lookup"><span data-stu-id="fe85a-127">Also, include a check for the device removed error when responding to window size changes.</span></span> <span data-ttu-id="fe85a-128">Dies ist aus mehreren Gründen ein guter Zeitpunkt zum Prüfen auf [**DXGI\_ERROR\_DEVICE\_REMOVED**](https://msdn.microsoft.com/library/windows/desktop/bb509553) oder **DXGI\_ERROR\_DEVICE\_RESET**:</span><span class="sxs-lookup"><span data-stu-id="fe85a-128">This is a good place to check for [**DXGI\_ERROR\_DEVICE\_REMOVED**](https://msdn.microsoft.com/library/windows/desktop/bb509553) or **DXGI\_ERROR\_DEVICE\_RESET** for several reasons:</span></span>

-   <span data-ttu-id="fe85a-129">Das Ändern der Größe der Swapchain erfordert das Aufrufen des zugrunde liegenden DXGI-Adapters, von dem der Fehler „Gerät entfernt“ zurückgegeben werden kann.</span><span class="sxs-lookup"><span data-stu-id="fe85a-129">Resizing the swap chain requires a call to the underlying DXGI adapter, which can return the device removed error.</span></span>
-   <span data-ttu-id="fe85a-130">Möglicherweise wurde die App auf einen Monitor verschoben, der an ein anderes Grafikgerät angeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="fe85a-130">The app might have moved to a monitor that's attached to a different graphics device.</span></span>
-   <span data-ttu-id="fe85a-131">Wenn ein Grafikgerät entfernt oder zurückgesetzt wird, ändert sich häufig die Desktopauflösung. Dies führt zu einer Änderung der Fenstergröße.</span><span class="sxs-lookup"><span data-stu-id="fe85a-131">When a graphics device is removed or reset, the desktop resolution often changes, resulting in a window size change.</span></span>

<span data-ttu-id="fe85a-132">Die Vorlage überprüft den HRESULT-Wert, der von [**ResizeBuffers**](https://msdn.microsoft.com/library/windows/desktop/bb174577) zurückgegeben wird:</span><span class="sxs-lookup"><span data-stu-id="fe85a-132">The template checks the HRESULT returned by [**ResizeBuffers**](https://msdn.microsoft.com/library/windows/desktop/bb174577):</span></span>

```cpp
// If the swap chain already exists, resize it.
HRESULT hr = m_swapChain->ResizeBuffers(
    2, // Double-buffered swap chain.
    static_cast<UINT>(m_d3dRenderTargetSize.Width),
    static_cast<UINT>(m_d3dRenderTargetSize.Height),
    DXGI_FORMAT_B8G8R8A8_UNORM,
    0
    );

if (hr == DXGI_ERROR_DEVICE_REMOVED || hr == DXGI_ERROR_DEVICE_RESET)
{
    // If the device was removed for any reason, a new device and swap chain will need to be created.
    HandleDeviceLost();

    // Everything is set up now. Do not continue execution of this method. HandleDeviceLost will reenter this method 
    // and correctly set up the new device.
    return;
}
else
{
    DX::ThrowIfFailed(hr);
}
```

### <a name="step-3"></a><span data-ttu-id="fe85a-133">Schritt3:</span><span class="sxs-lookup"><span data-stu-id="fe85a-133">Step 3:</span></span>

<span data-ttu-id="fe85a-134">Wenn die App den Fehler [**DXGI\_ERROR\_DEVICE\_REMOVED**](https://msdn.microsoft.com/library/windows/desktop/bb509553) empfängt, muss sie das Direct3D-Gerät neu initialisieren und alle geräteabhängigen Ressourcen neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="fe85a-134">Any time your app receives the [**DXGI\_ERROR\_DEVICE\_REMOVED**](https://msdn.microsoft.com/library/windows/desktop/bb509553) error, it must reinitialize the Direct3D device and recreate any device-dependent resources.</span></span> <span data-ttu-id="fe85a-135">Geben Sie alle Verweise auf Ressourcen des Grafikgeräts frei, die mit dem vorherigen Direct3D-Gerät erstellt wurden. Diese Ressourcen sind jetzt ungültig, und alle Verweise auf die Swapchain müssen freigegeben werden, bevor eine neue erstellt werden kann.</span><span class="sxs-lookup"><span data-stu-id="fe85a-135">Release any references to graphics device resources created with the previous Direct3D device; those resources are now invalid, and all references to the swap chain must be released before a new one can be created.</span></span>

<span data-ttu-id="fe85a-136">Die HandleDeviceLost-Methode gibt die Swapchain frei und weist die App-Komponenten an, die Geräteressourcen freizugeben:</span><span class="sxs-lookup"><span data-stu-id="fe85a-136">The HandleDeviceLost method releases the swap chain and notifies app components to release device resources:</span></span>

```cpp
m_swapChain = nullptr;

if (m_deviceNotify != nullptr)
{
    // Notify the renderers that device resources need to be released.
    // This ensures all references to the existing swap chain are released so that a new one can be created.
    m_deviceNotify->OnDeviceLost();
}
```

<span data-ttu-id="fe85a-137">Anschließend erstellt sie eine neue Swapchain und initialisiert die geräteabhängigen Ressourcen neu, die von der Geräteverwaltungsklasse gesteuert werden:</span><span class="sxs-lookup"><span data-stu-id="fe85a-137">Then, it creates a new swap chain and reinitializes the device-dependent resources controlled by the device management class:</span></span>

```cpp
// Create the new device and swap chain.
CreateDeviceResources();
m_d2dContext->SetDpi(m_dpi, m_dpi);
CreateWindowSizeDependentResources();
```

<span data-ttu-id="fe85a-138">Nachdem das Gerät und die Swapchain neu eingerichtet wurden, werden die App-Komponenten angewiesen, geräteabhängige Ressourcen neu zu initialisieren:</span><span class="sxs-lookup"><span data-stu-id="fe85a-138">After the device and swap chain have been re-established, it notifies app components to reinitialize device-dependent resources:</span></span>

```cpp
// Create the new device and swap chain.
CreateDeviceResources();
m_d2dContext->SetDpi(m_dpi, m_dpi);
CreateWindowSizeDependentResources();

if (m_deviceNotify != nullptr)
{
    // Notify the renderers that resources can now be created again.
    m_deviceNotify->OnDeviceRestored();
}
```

<span data-ttu-id="fe85a-139">Wenn die HandleDeviceLost-Methode beendet wird, geht die Steuerung wieder auf die Renderschleife über, die dann mit dem Zeichnen des nächsten Frames fortfährt.</span><span class="sxs-lookup"><span data-stu-id="fe85a-139">When the HandleDeviceLost method exits, control returns to the rendering loop, which continues on to draw the next frame.</span></span>

## <a name="remarks"></a><span data-ttu-id="fe85a-140">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="fe85a-140">Remarks</span></span>


### <a name="investigating-the-cause-of-device-removed-errors"></a><span data-ttu-id="fe85a-141">Untersuchen der Ursache für Fehler vom Typ „Gerät entfernt“</span><span class="sxs-lookup"><span data-stu-id="fe85a-141">Investigating the cause of device removed errors</span></span>

<span data-ttu-id="fe85a-142">Wiederkehrende Probleme mit dem DXGI-Fehler „Gerät entfernt“ können darauf hinweisen, dass von Ihrem Grafikcode während einer Zeichenroutine ungültige Bedingungen erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="fe85a-142">Repeat issues with DXGI device removed errors can indicate that your graphics code is creating invalid conditions during a drawing routine.</span></span> <span data-ttu-id="fe85a-143">Außerdem können sie auf einen Hardwarefehler oder einen Fehler in der Grafikkarte hinweisen.</span><span class="sxs-lookup"><span data-stu-id="fe85a-143">It can also indicate a hardware failure or a bug in the graphics driver.</span></span> <span data-ttu-id="fe85a-144">Rufen Sie zum Untersuchen der Fehler vom Typ „Gerät entfernt“ [**ID3D11Device::GetDeviceRemovedReason**](https://msdn.microsoft.com/library/windows/desktop/ff476526) auf, bevor Sie das Direct3D-Gerät freigeben.</span><span class="sxs-lookup"><span data-stu-id="fe85a-144">To investigate the cause of device removed errors, call [**ID3D11Device::GetDeviceRemovedReason**](https://msdn.microsoft.com/library/windows/desktop/ff476526) before releasing the Direct3D device.</span></span> <span data-ttu-id="fe85a-145">Diese Methode gibt einen von sechs möglichen DXGI-Fehlercodes zurück, um die Ursache des Fehlers „Gerät entfernt“ anzugeben:</span><span class="sxs-lookup"><span data-stu-id="fe85a-145">This method returns one of six possible DXGI error codes indicating the reason for the device removed error:</span></span>

-   <span data-ttu-id="fe85a-146">**DXGI\_ERROR\_DEVICE\_HUNG**: Der Grafiktreiber reagiert nicht mehr aufgrund einer ungültigen Kombination von Grafikbefehlen, die von der App gesendet wurden.</span><span class="sxs-lookup"><span data-stu-id="fe85a-146">**DXGI\_ERROR\_DEVICE\_HUNG**: The graphics driver stopped responding because of an invalid combination of graphics commands sent by the app.</span></span> <span data-ttu-id="fe85a-147">Wenn Sie diesen Fehler häufiger erhalten, ist dies ein Hinweis darauf, dass Ihre App zum Hängen des Geräts geführt hat und ein Debugvorgang durchgeführt werden muss.</span><span class="sxs-lookup"><span data-stu-id="fe85a-147">If you get this error repeatedly, it is a likely indication that your app caused the device to hang and needs to be debugged.</span></span>
-   <span data-ttu-id="fe85a-148">**DXGI\_ERROR\_DEVICE\_REMOVED**: Das Grafikgerät wurde physisch entfernt oder ausgeschaltet, oder es wurde ein Treiberupgrade durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="fe85a-148">**DXGI\_ERROR\_DEVICE\_REMOVED**: The graphics device has been physically removed, turned off, or a driver upgrade has occurred.</span></span> <span data-ttu-id="fe85a-149">Dies geschieht von Zeit zu Zeit und ist normal. Die App bzw. das Spiel sollte die Geräteressourcen wie in diesem Thema beschrieben neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="fe85a-149">This happens occasionally and is normal; your app or game should recreate device resources as described in this topic.</span></span>
-   <span data-ttu-id="fe85a-150">**DXGI\_ERROR\_DEVICE\_RESET**: Für das Grafikgerät ist aufgrund eines falsch formatierten Befehls ein Fehler aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="fe85a-150">**DXGI\_ERROR\_DEVICE\_RESET**: The graphics device failed because of a badly formed command.</span></span> <span data-ttu-id="fe85a-151">Wenn Sie diesen Fehler häufig erhalten, kann dies bedeuten, dass vom Code ungültige Zeichenbefehle gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="fe85a-151">If you get this error repeatedly, it may mean that your code is sending invalid drawing commands.</span></span>
-   <span data-ttu-id="fe85a-152">**DXGI\_ERROR\_DRIVER\_INTERNAL\_ERROR**: Der Grafiktreiber hat einen Fehler erkannt und das Gerät zurückgesetzt.</span><span class="sxs-lookup"><span data-stu-id="fe85a-152">**DXGI\_ERROR\_DRIVER\_INTERNAL\_ERROR**: The graphics driver encountered an error and reset the device.</span></span>
-   <span data-ttu-id="fe85a-153">**DXGI\_ERROR\_INVALID\_CALL**: Die Anwendung hat ungültige Parameterdaten bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="fe85a-153">**DXGI\_ERROR\_INVALID\_CALL**: The application provided invalid parameter data.</span></span> <span data-ttu-id="fe85a-154">Auch wenn Sie diesen Fehler nur einmal erhalten, bedeutet dies, dass Ihr Code die Bedingung „Gerät entfernt“ verursacht hat und ein Debugvorgang durchgeführt werden muss.</span><span class="sxs-lookup"><span data-stu-id="fe85a-154">If you get this error even once, it means that your code caused the device removed condition and must be debugged.</span></span>
-   <span data-ttu-id="fe85a-155">**S\_OK**: Wird zurückgegeben, wenn ein Grafikgerät aktiviert, deaktiviert oder zurückgesetzt wird, ohne das aktuelle Grafikgerät ungültig zu machen.</span><span class="sxs-lookup"><span data-stu-id="fe85a-155">**S\_OK**: Returned when a graphics device was enabled, disabled, or reset without invalidating the current graphics device.</span></span> <span data-ttu-id="fe85a-156">Dieser Fehler kann beispielsweise zurückgegeben werden, wenn eine App die [Windows Advanced Rasterization Platform (WARP)](https://msdn.microsoft.com/library/windows/desktop/gg615082) verwendet und ein Hardwareadapter verfügbar wird.</span><span class="sxs-lookup"><span data-stu-id="fe85a-156">For example, this error code can be returned if an app is using [Windows Advanced Rasterization Platform (WARP)](https://msdn.microsoft.com/library/windows/desktop/gg615082) and a hardware adapter becomes available.</span></span>

<span data-ttu-id="fe85a-157">Mit dem folgenden Code wird der Fehlercode [**DXGI\_ERROR\_DEVICE\_REMOVED**](https://msdn.microsoft.com/library/windows/desktop/bb509553) abgerufen und in der Debugkonsole ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="fe85a-157">The following code will retrieve the [**DXGI\_ERROR\_DEVICE\_REMOVED**](https://msdn.microsoft.com/library/windows/desktop/bb509553) error code and print it to the debug console.</span></span> <span data-ttu-id="fe85a-158">Fügen Sie diesen Code am Anfang der HandleDeviceLost-Methode hinzu:</span><span class="sxs-lookup"><span data-stu-id="fe85a-158">Insert this code at the beginning of the HandleDeviceLost method:</span></span>

```cpp
    HRESULT reason = m_d3dDevice->GetDeviceRemovedReason();

#if defined(_DEBUG)
    wchar_t outString[100];
    size_t size = 100;
    swprintf_s(outString, size, L"Device removed! DXGI_ERROR code: 0x%X\n", reason);
    OutputDebugStringW(outString);
#endif
```

<span data-ttu-id="fe85a-159">Ausführlichere Informationen finden Sie unter [**GetDeviceRemovedReason**](https://msdn.microsoft.com/library/windows/desktop/ff476526) und [**DXGI\_ERROR**](https://msdn.microsoft.com/library/windows/desktop/bb509553).</span><span class="sxs-lookup"><span data-stu-id="fe85a-159">For more details, see [**GetDeviceRemovedReason**](https://msdn.microsoft.com/library/windows/desktop/ff476526) and [**DXGI\_ERROR**](https://msdn.microsoft.com/library/windows/desktop/bb509553).</span></span>

### <a name="testing-device-removed-handling"></a><span data-ttu-id="fe85a-160">Testgerät hat Behandlung entfernt</span><span class="sxs-lookup"><span data-stu-id="fe85a-160">Testing Device Removed Handling</span></span>

<span data-ttu-id="fe85a-161">Die Developer-Eingabeaufforderung für Visual Studio unterstützt das Befehlszeilenprogramm „dxcap“ für die Direct3D-Ereigniserfassung und -Wiedergabe im Zusammenhang mit der Visual Studio-Grafikdiagnose.</span><span class="sxs-lookup"><span data-stu-id="fe85a-161">Visual Studio's Developer Command Prompt supports a command line tool 'dxcap' for Direct3D event capture and playback related to the Visual Studio Graphics Diagnostics.</span></span> <span data-ttu-id="fe85a-162">Sie können die Befehlszeilenoption „-forcetdr“ verwenden, während Ihre App ausgeführt wird, die ein GPU-Timeout-Erkennungs- und Wiederherstellungsereignis erzwingt, wodurch DXGI\_ERROR\_DEVICE\_REMOVED ausgelöst wird und Sie Ihren Code zur Fehlerbehandlung testen können.</span><span class="sxs-lookup"><span data-stu-id="fe85a-162">You can use the command line option "-forcetdr" while your app is running which will force a GPU Timeout Detection and Recovery event, thereby triggering DXGI\_ERROR\_DEVICE\_REMOVED and allowing you to test your error handling code.</span></span>

> <span data-ttu-id="fe85a-163">**Hinweis** DXCap und die Unterstützungs-DLLs werden unter „system32/syswow64“ als Teil der Grafiktools für Windows 10 installiert, die nicht mehr über das Windows SDK verteilt werden.</span><span class="sxs-lookup"><span data-stu-id="fe85a-163">**Note** DXCap and its support DLLs are installed into system32/syswow64 as part of the Graphics Tools for Windows 10 which are no longer distributed via the Windows SDK.</span></span> <span data-ttu-id="fe85a-164">Stattdessen werden sie über das bei Bedarf verfügbare Feature „Grafiktools“ bereitgestellt. Dies ist eine optionale Betriebssystemkomponente, die installiert sein muss, um die Grafiktools unter Windows 10 zu aktivieren und zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="fe85a-164">Instead they are provided via the Graphics Tools Feature on Demand that is an optional OS component and must be installed in order to enable and use the Graphics Tools on Windows 10.</span></span> <span data-ttu-id="fe85a-165">Weitere Informationen zum Installieren der Grafiktools für Windows 10 finden Sie hier:</span><span class="sxs-lookup"><span data-stu-id="fe85a-165">More information on how to Install the Graphics Tools for Windows 10 can be found here:</span></span> <https://msdn.microsoft.com/library/mt125501.aspx#InstallGraphicsTools>
