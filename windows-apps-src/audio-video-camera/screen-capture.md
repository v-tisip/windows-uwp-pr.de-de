---
author: eliotcowley
title: Bildschirmaufnahme
description: Der Windows.Graphics.Capture-Namespace enthält APIs zum Abrufen von Frames aus einer Anzeige oder einem Anwendungsfenster, um Videostreams zu erstellen oder gemeinsame und interaktive Benutzeroberflächen zu erstellen.
ms.assetid: 349C959D-9C74-44E7-B5F6-EBDB5CA87B9F
ms.author: elcowle
ms.date: 10/09/2018
ms.topic: article
keywords: Windows10, UWP, Bildschirmaufnahme
ms.localizationpriority: medium
ms.openlocfilehash: d28ed1fce79a815155180ab8a3c708e2c8bf8916
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5561150"
---
# <a name="screen-capture"></a><span data-ttu-id="c39d1-104">Bildschirmaufnahme</span><span class="sxs-lookup"><span data-stu-id="c39d1-104">Screen capture</span></span>

<span data-ttu-id="c39d1-105">Ab Windows 10,Version 1803, enthält der [Windows.Graphics.Capture](https://docs.microsoft.com/uwp/api/windows.graphics.capture) APIs zum Abrufen von Frames aus einer Anzeige oder einem Anwendungsfenster, um Videostreams zu erstellen oder gemeinsame und interaktive Benutzeroberflächen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="c39d1-105">Starting in Windows 10, version 1803, the [Windows.Graphics.Capture](https://docs.microsoft.com/uwp/api/windows.graphics.capture) namespace provides APIs to acquire frames from a display or application window, to create video streams or snapshots to build collaborative and interactive experiences.</span></span>

<span data-ttu-id="c39d1-106">Mit der Bildschirmaufnahme können Entwickler sichere System-UIs für Endbenutzer aufrufen, um das Fenster für die Anzeige oder die Anwendung für die Aufzeichnung auszuwählen. Es wird ein gelber Rahmen mit einer Benachrichtigung vom System um das aktiv erfasste Element herum gezeichnet.</span><span class="sxs-lookup"><span data-stu-id="c39d1-106">With screen capture, developers invoke secure system UI for end users to pick the display or application window to be captured, and a yellow notification border is drawn by the system around the actively captured item.</span></span> <span data-ttu-id="c39d1-107">Im Fall von mehreren gleichzeitigen Aufnahmesitzungen wird ein gelber Rahmen um jedes erfasste Element gezeichnet.</span><span class="sxs-lookup"><span data-stu-id="c39d1-107">In the case of multiple simultaneous capture sessions, a yellow border is drawn around each item being captured.</span></span>

> [!NOTE]
> <span data-ttu-id="c39d1-108">Die Bildschirmaufnahme APIs werden nur für Desktop- und immersives Windows Mixed Reality-Headsets unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c39d1-108">The screen capture APIs are only supported on desktop and Windows Mixed Reality immersive headsets.</span></span>

## <a name="add-the-screen-capture-capability"></a><span data-ttu-id="c39d1-109">Hinzufügen der Bildschirmaufnahmefunktion</span><span class="sxs-lookup"><span data-stu-id="c39d1-109">Add the screen capture capability</span></span>

<span data-ttu-id="c39d1-110">Die APIs finden Sie in der **Windows.Graphics.Capture** -Namespace erfordern eine allgemeine Funktion in Ihrem App Manifest deklariert werden:</span><span class="sxs-lookup"><span data-stu-id="c39d1-110">The APIs found in the **Windows.Graphics.Capture** namespace require a general capability to be declared in your application's manifest:</span></span>
    
1. <span data-ttu-id="c39d1-111">Öffnen Sie **"Package.appxmanifest"** im **Projektmappen-Explorer**.</span><span class="sxs-lookup"><span data-stu-id="c39d1-111">Open **Package.appxmanifest** in the **Solution Explorer**.</span></span>
2. <span data-ttu-id="c39d1-112">Wählen Sie die Registerkarte **Funktionen** aus.</span><span class="sxs-lookup"><span data-stu-id="c39d1-112">Select the **Capabilities** tab.</span></span>
3. <span data-ttu-id="c39d1-113">Überprüfen Sie **Grafiken zu erfassen**.</span><span class="sxs-lookup"><span data-stu-id="c39d1-113">Check **Graphics Capture**.</span></span>

![Grafik-Erfassung](images/screen-capture-1.png)

## <a name="launch-the-system-ui-to-start-screen-capture"></a><span data-ttu-id="c39d1-115">Starten Sie die System-Benutzeroberfläche, um die Bildschirmaufnahme zu starten</span><span class="sxs-lookup"><span data-stu-id="c39d1-115">Launch the system UI to start screen capture</span></span>

<span data-ttu-id="c39d1-116">Vor dem Starten der Systembenutzeroberfläche sollten Sie überprüfen, ob Ihre Anwendung momentan Bildschirmaufnahmen erstellen kann.</span><span class="sxs-lookup"><span data-stu-id="c39d1-116">Before launching the system UI, you can check to see if your application is currently able to take screen captures.</span></span> <span data-ttu-id="c39d1-117">Es gibt verschiedene Gründe, warum die Anwendung möglicherweise keine Bildschirmaufnahme erstellen kann, z.B. wenn das Gerät die Hardwareanforderungen nicht erfüllt, oder wenn die Anwendung für die Aufnahme Bildschirmaufnahmen blockiert.</span><span class="sxs-lookup"><span data-stu-id="c39d1-117">There are several reasons why your application might not be able to use screen capture, including if the device does not meet hardware requirements or if the application targeted for capture blocks screen capture.</span></span> <span data-ttu-id="c39d1-118">Verwenden Sie die **IsSupported**-Methode in der [GraphicsCaptureSession](https://docs.microsoft.com/uwp/api/windows.graphics.capture.graphicscapturesession)-Klasse, um zu bestimmen, ob UWP.Bildschirmaufnahmen unterstützt werden:</span><span class="sxs-lookup"><span data-stu-id="c39d1-118">Use the **IsSupported** method in the [GraphicsCaptureSession](https://docs.microsoft.com/uwp/api/windows.graphics.capture.graphicscapturesession) class to determine if UWP screen capture is supported:</span></span>

```cs
// This runs when the application starts.
public void OnInitialization()
{
    if (!GraphicsCaptureSession.IsSupported()) 
    {
        // Hide the capture UI if screen capture is not supported.
        CaptureButton.Visibility = Visibility.Collapsed; 
    }    
}
```

<span data-ttu-id="c39d1-119">Nachdem Sie überprüft haben, dass Bildschirmaufnahmen unterstützt werden, verwenden Sie die [GraphicsCapturePicker](https://docs.microsoft.com/uwp/api/windows.graphics.capture.graphicscapturepicker)-Klasse verwenden, um die System-Auswahl-UI aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="c39d1-119">Once you've verified that screen capture is supported, use the [GraphicsCapturePicker](https://docs.microsoft.com/uwp/api/windows.graphics.capture.graphicscapturepicker) class to invoke the system picker UI.</span></span> <span data-ttu-id="c39d1-120">Der Benutzer verwendet die Benutzeroberfläche, um das Anzeige- oder Anwendungsfenster für die auszuführende Bildschirmaufnahmen auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="c39d1-120">The end user uses this UI to select the display or application window of which to take screen captures.</span></span> <span data-ttu-id="c39d1-121">Die Auswahl gibt [GraphicsCaptureItem](https://docs.microsoft.com/uwp/api/windows.graphics.capture.graphicscaptureitem)zurück, das verwendet wird, um eine **GraphicsCaptureSession** zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="c39d1-121">The picker will return a [GraphicsCaptureItem](https://docs.microsoft.com/uwp/api/windows.graphics.capture.graphicscaptureitem) that will be used to create a **GraphicsCaptureSession**:</span></span>

```cs
public async Task StartCaptureAsync() 
{ 
    // The GraphicsCapturePicker follows the same pattern the 
    // file pickers do. 
    var picker = new GraphicsCapturePicker(); 
    GraphicsCaptureItem item = await picker.PickSingleItemAsync(); 

    // The item may be null if the user dismissed the 
    // control without making a selection or hit Cancel. 
    if (item != null) 
    {
        // We'll define this method later in the document.
        StartCaptureInternal(item); 
    } 
}
```

<span data-ttu-id="c39d1-122">Da dies Benutzeroberflächencode ist, muss sie für den UI-Thread aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="c39d1-122">Because this is UI code, it needs to be called on the UI thread.</span></span> <span data-ttu-id="c39d1-123">Wenn Sie es aus CodeBehind für eine Seite Ihrer Anwendung (z. B. **"MainPage.Xaml.cs"**) aufrufen sind für Sie erfolgt dies automatisch, aber wenn nicht, Sie können sie für die Ausführung der UI-Thread mit dem folgenden Code erzwingen:</span><span class="sxs-lookup"><span data-stu-id="c39d1-123">If you're calling it from the code-behind for a page of your application (like **MainPage.xaml.cs**) this is done for you automatically, but if not, you can force it to run on the UI thread with the following code:</span></span>

```cs
CoreWindow window = CoreApplication.MainView.CoreWindow;
           
await window.Dispatcher.RunAsync(CoreDispatcherPriority.Normal, async () =>
{
    await StartCaptureAsync();
});
```

## <a name="create-a-capture-frame-pool-and-capture-session"></a><span data-ttu-id="c39d1-124">Erstellen Sie ein Frameerfassungspool und eine Sammlungssitzung</span><span class="sxs-lookup"><span data-stu-id="c39d1-124">Create a capture frame pool and capture session</span></span>

<span data-ttu-id="c39d1-125">Mithilfe der **GraphicsCaptureItem** erstellen Sie ein [Direct3D11CaptureFramePool](https://docs.microsoft.com/uwp/api/windows.graphics.capture.direct3d11captureframepool) mit Ihrem D3D-Gerät, das unterstützte Pixel-Format (**DXGI\_FORMAT\_B8G8R8A8\_UNORM**), und die Anzahl der gewünschten Frames (die eine ganze Zahl sein können), und die Framegröße.</span><span class="sxs-lookup"><span data-stu-id="c39d1-125">Using the **GraphicsCaptureItem**, you will create a [Direct3D11CaptureFramePool](https://docs.microsoft.com/uwp/api/windows.graphics.capture.direct3d11captureframepool) with your D3D device, supported pixel format (**DXGI\_FORMAT\_B8G8R8A8\_UNORM**), number of desired frames (which can be any integer), and frame size.</span></span> <span data-ttu-id="c39d1-126">Die **ContentSize**-Eigenschaft der **GraphicsCaptureItem**-Klasse kann ebenfalls als Anzahl der Frames verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="c39d1-126">The **ContentSize** property of the **GraphicsCaptureItem** class can be used as the size of your frame:</span></span>

```cs
private GraphicsCaptureItem _item;
private Direct3D11CaptureFramePool _framePool;
private CanvasDevice _canvasDevice;
private GraphicsCaptureSession _session;

public void StartCaptureInternal(GraphicsCaptureItem item) 
{
    _item = item;

    _framePool = Direct3D11CaptureFramePool.Create( 
        _canvasDevice, // D3D device 
        DirectXPixelFormat.B8G8R8A8UIntNormalized, // Pixel format 
        2, // Number of frames 
        _item.Size); // Size of the buffers   
} 
```

<span data-ttu-id="c39d1-127">Als Nächstes rufen Sie eine Instanz der **GraphicsCaptureSession**-Klasse für Ihren **Direct3D11CaptureFramePool** durch Übergabe der **GraphicsCaptureItem** auf der **CreateCaptureSession**-Methode auf:</span><span class="sxs-lookup"><span data-stu-id="c39d1-127">Next, get an instance of the **GraphicsCaptureSession** class for your **Direct3D11CaptureFramePool** by passing the **GraphicsCaptureItem** to the **CreateCaptureSession** method:</span></span>

```cs
_session = _framePool.CreateCaptureSession(_item);
```

<span data-ttu-id="c39d1-128">Nachdem der Benutzer die Zustimmung für die Aufnahme eines Anwendungsfensters oder einer Anzeige in der System-Benutzeroberfläche erteilt hat, kann die **GraphicsCaptureItem** auf mehrere **CaptureSession**-Objekte angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="c39d1-128">Once the user has explicitly given consent to capturing an application window or display in the system UI, the **GraphicsCaptureItem** can be associated to multiple **CaptureSession** objects.</span></span> <span data-ttu-id="c39d1-129">Auf diese Weise kann die Anwendung das gleiche Element für verschiedene Umgebungen erfassen.</span><span class="sxs-lookup"><span data-stu-id="c39d1-129">This way your application can choose to capture the same item for various experiences.</span></span>

<span data-ttu-id="c39d1-130">Um mehrere Elemente gleichzeitig zu erfassen, muss die Anwendung eine Sammlungssitzung für jedes aufzuzeichnende Element erstellen, was das Aufrufen der Dateiauswahl-UI für jedes Element erfordert, das erfasst werden muss.</span><span class="sxs-lookup"><span data-stu-id="c39d1-130">To capture multiple items at the same time, your application must create a capture session for each item to be captured, which requires invoking the picker UI for each item that is to be captured.</span></span>

## <a name="acquire-capture-frames"></a><span data-ttu-id="c39d1-131">Erwerben von Aufnahmeframes</span><span class="sxs-lookup"><span data-stu-id="c39d1-131">Acquire capture frames</span></span>

<span data-ttu-id="c39d1-132">Rufen Sie nach der Erstellung des Frame-Pool und der Aufnahmesitzung die **StartCapture**-Methode für Ihre **GraphicsCaptureSession**-Instanz auf, die das System benachrichtigt, die Aufnahmeframes an Ihre App zu senden:</span><span class="sxs-lookup"><span data-stu-id="c39d1-132">With your frame pool and capture session created, call the **StartCapture** method on your **GraphicsCaptureSession** instance to notify the system to start sending capture frames to your app:</span></span>

```cs
_session.StartCapture();
```

<span data-ttu-id="c39d1-133">Um diese Aufnahmeframes zu erwerben, die [Direct3D11CaptureFrame](https://docs.microsoft.com/uwp/api/windows.graphics.capture.direct3d11captureframe)-Objekte sind, können Sie das **Direct3D11CaptureFramePool.FrameArrived**-Ereignis verwenden:</span><span class="sxs-lookup"><span data-stu-id="c39d1-133">To acquire these capture frames, which are [Direct3D11CaptureFrame](https://docs.microsoft.com/uwp/api/windows.graphics.capture.direct3d11captureframe) objects, you can use the **Direct3D11CaptureFramePool.FrameArrived** event:</span></span>

```cs
_framePool.FrameArrived += (s, a) => 
{ 
    // The FrameArrived event fires for every frame on the thread that         
    // created the Direct3D11CaptureFramePool. This means we don't have to 
    // do a null-check here, as we know we're the only one  
    // dequeueing frames in our application.  

    // NOTE: Disposing the frame retires it and returns  
    // the buffer to the pool.
    using (var frame = _framePool.TryGetNextFrame()) 
    {
        // We'll define this method later in the document.
        ProcessFrame(frame); 
    }  
}; 
```

<span data-ttu-id="c39d1-134">Es wird empfohlen, den UI-Thread für **FrameArrived** nach Möglichkeit zu vermeiden, da dieses Ereignis jedes Mal ausgelöst wird, wenn ein neuer Frame verfügbar ist, was häufig vorkommt.</span><span class="sxs-lookup"><span data-stu-id="c39d1-134">It is recommended to avoid using the UI thread if possible for **FrameArrived**, as this event will be raised every time a new frame is available, which will be frequent.</span></span> <span data-ttu-id="c39d1-135">Wenn Sie sich entscheiden, **FrameArrived** im UI-Thread zu übernehmen, überlegen Sie, wie viel Arbeit Sie jedes Mal machen, wenn das Ereignis ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="c39d1-135">If you do choose to listen to **FrameArrived** on the UI thread, be mindful of how much work you're doing every time the event fires.</span></span>

<span data-ttu-id="c39d1-136">Alternativ können Sie manuell Frames mit der **Direct3D11CaptureFramePool.TryGetNextFrame**-Methode ziehen, bis Sie alle Frames haben, die Sie benötigen.</span><span class="sxs-lookup"><span data-stu-id="c39d1-136">Alternatively, you can manually pull frames with the **Direct3D11CaptureFramePool.TryGetNextFrame** method until you get all of the frames that you need.</span></span>

<span data-ttu-id="c39d1-137">Das **Direct3D11CaptureFrame**-Objekt enthält die Eigenschaften **ContentSize**, **Surface** und **SystemRelativeTime**.</span><span class="sxs-lookup"><span data-stu-id="c39d1-137">The **Direct3D11CaptureFrame** object contains the properties **ContentSize**, **Surface**, and **SystemRelativeTime**.</span></span> <span data-ttu-id="c39d1-138">Die **SystemRelativeTime** ist die QPC ([QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904))-Zeit, die zum Synchronisieren von anderen Medienelemente verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="c39d1-138">The **SystemRelativeTime** is QPC ([QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904)) time that can be used to synchronize other media elements.</span></span>

## <a name="processing-capture-frames"></a><span data-ttu-id="c39d1-139">Verarbeiten von Aufnahmeframes</span><span class="sxs-lookup"><span data-stu-id="c39d1-139">Processing capture frames</span></span>

<span data-ttu-id="c39d1-140">Frames aus **Direct3D11CaptureFramePool** werden beim Aufrufen von **TryGetNextFrame** ausgecheckt, und gemäß der Lebensdauer des **Direct3D11CaptureFrame**-Objekts wieder eingecheckt.</span><span class="sxs-lookup"><span data-stu-id="c39d1-140">Each frame from the **Direct3D11CaptureFramePool** is checked out when calling **TryGetNextFrame**, and checked back in according to the lifetime of the **Direct3D11CaptureFrame** object.</span></span> <span data-ttu-id="c39d1-141">Für systemeigene Anwendungen reicht das Veröffentlichen des **Direct3D11CaptureFrame**-Objekts aus, um die Frame zurück in den Frame-Pool einzuchecken.</span><span class="sxs-lookup"><span data-stu-id="c39d1-141">For native applications, releasing the **Direct3D11CaptureFrame** object is enough to check the frame back in to the frame pool.</span></span> <span data-ttu-id="c39d1-142">Für verwaltete Anwendungen wird empfohlen, die **Direct3D11CaptureFrame.Dispose** (**Schließen** in C++)-Methode zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="c39d1-142">For managed applications, it is recommended to use the **Direct3D11CaptureFrame.Dispose** (**Close** in C++) method.</span></span> <span data-ttu-id="c39d1-143">**Direct3D11CaptureFrame** implementiert die [IClosable](https://docs.microsoft.com/uwp/api/Windows.Foundation.IClosable)-Schnittstelle, die als [IDisposable](https://msdn.microsoft.com/library/system.idisposable.aspx) für C#-Aufrufer projiziert wird.</span><span class="sxs-lookup"><span data-stu-id="c39d1-143">**Direct3D11CaptureFrame** implements the [IClosable](https://docs.microsoft.com/uwp/api/Windows.Foundation.IClosable) interface, which is projected as [IDisposable](https://msdn.microsoft.com/library/system.idisposable.aspx) for C# callers.</span></span>

<span data-ttu-id="c39d1-144">Anwendungen sollten weder Verweise auf **Direct3D11CaptureFrame**-Objekte speichern, noch Verweise auf die zugrunde liegende Direct3D-Oberfläche speichern, nachdem der Frame erneut eingecheckt wurde.</span><span class="sxs-lookup"><span data-stu-id="c39d1-144">Applications should not save references to **Direct3D11CaptureFrame** objects, nor should they save references to the underlying Direct3D surface after the frame has been checked back in.</span></span>

<span data-ttu-id="c39d1-145">Während der Verarbeitung eines Frames, empfiehlt es sich, dass Anwendungen die [ID3D11Multithread](https://msdn.microsoft.com/library/windows/desktop/mt644886)-Sperre auf dem gleichen Gerät wie das **Direct3D11CaptureFramePool**-Objekt verwenden.</span><span class="sxs-lookup"><span data-stu-id="c39d1-145">While processing a frame, it is recommended that applications take the [ID3D11Multithread](https://msdn.microsoft.com/library/windows/desktop/mt644886) lock on the same device that is associated with the **Direct3D11CaptureFramePool** object.</span></span>

<span data-ttu-id="c39d1-146">Die zugrunde liegende Direct3D-Oberfläche gibt immer die Größe an, die beim Erstellen (oder neuerstellen) von **Direct3D11CaptureFramePool** angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="c39d1-146">The underlying Direct3D surface will always be the size specified when creating (or recreating) the **Direct3D11CaptureFramePool**.</span></span> <span data-ttu-id="c39d1-147">Wenn der Inhalt größer als der Frame ist, werden die Inhalte auf die Größe des Frame zugeschnitten.</span><span class="sxs-lookup"><span data-stu-id="c39d1-147">If content is larger than the frame, the contents are clipped to the size of the frame.</span></span> <span data-ttu-id="c39d1-148">Wenn der Inhalt kleiner als der Frames ist, enthält der Rest des Frames nicht definierte Daten.</span><span class="sxs-lookup"><span data-stu-id="c39d1-148">If the content is smaller than the frame, then the rest of the frame contains undefined data.</span></span> <span data-ttu-id="c39d1-149">Es wird empfohlen, dass Anwendungen eine Sub-Rect mit der **ContentSize**-Eigenschaft für den **Direct3D11CaptureFrame** kopieren, um zu verhindern, dass der Inhalt nicht definiert ist.</span><span class="sxs-lookup"><span data-stu-id="c39d1-149">It is recommended that applications copy out a sub-rect using the **ContentSize** property for that **Direct3D11CaptureFrame** to avoid showing undefined content.</span></span>

## <a name="react-to-capture-item-resizing-or-device-lost"></a><span data-ttu-id="c39d1-150">Auf das Ändern der Größe von Elementen oder verlorene Geräte reagieren</span><span class="sxs-lookup"><span data-stu-id="c39d1-150">React to capture item resizing or device lost</span></span>

<span data-ttu-id="c39d1-151">Während der Aufnahme können Anwendungen Aspekte der ihrer **Direct3D11CaptureFramePool** ändern.</span><span class="sxs-lookup"><span data-stu-id="c39d1-151">During the capture process, applications may wish to change aspects of their **Direct3D11CaptureFramePool**.</span></span> <span data-ttu-id="c39d1-152">Dies umfasst die Bereitstellung eines neuen Direct3D-Geräts, das Ändern der Größe der Framepuffer oder das Ändern der Anzahl der Puffer innerhalb des Pools.</span><span class="sxs-lookup"><span data-stu-id="c39d1-152">This includes providing a new Direct3D device, changing the size of the frame buffers, or even changing the number of buffers within the pool.</span></span> <span data-ttu-id="c39d1-153">In jedem dieser Szenarien ist die **Recreate**-Methode für das **Direct3D11CaptureFramePool**-Objekt das empfohlene Tool.</span><span class="sxs-lookup"><span data-stu-id="c39d1-153">In each of these scenarios, the **Recreate** method on the **Direct3D11CaptureFramePool** object is the recommended tool.</span></span>

<span data-ttu-id="c39d1-154">Wenn **Recreate** aufgerufen wird, werden alle vorhandenen Frames verworfen.</span><span class="sxs-lookup"><span data-stu-id="c39d1-154">When **Recreate** is called, all existing frames are discarded.</span></span> <span data-ttu-id="c39d1-155">Dadurch wird die Ausgabe von Frames verhindert, deren zugrunde liegende Direct3D-Oberfläche zu einem Gerät gehören, auf das die Anwendung nicht mehr zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="c39d1-155">This is to prevent handing out frames whose underlying Direct3D surfaces belong to a device that the application may no longer have access to.</span></span> <span data-ttu-id="c39d1-156">Aus diesem Grund sollten alle ausstehenden Frames vor dem Aufruf von **Recreate** verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="c39d1-156">For this reason, it may be wise to process all pending frames before calling **Recreate**.</span></span>

## <a name="putting-it-all-together"></a><span data-ttu-id="c39d1-157">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="c39d1-157">Putting it all together</span></span>

<span data-ttu-id="c39d1-158">Der folgende Codeausschnitt ist ein End-to-End-Beispiel für die Implementierung einer Bildschirmaufnahme in einer UWP-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="c39d1-158">The following code snippet is an end-to-end example of how to implement screen capture in a UWP application.</span></span> <span data-ttu-id="c39d1-159">In diesem Beispiel haben wir eine Schaltfläche in der Front-End-, die beim Klicken auf, ruft die **Button_ClickAsync** -Methode.</span><span class="sxs-lookup"><span data-stu-id="c39d1-159">In this sample, we have a button in the front-end which, when clicked, calls the **Button_ClickAsync** method.</span></span>

> [!NOTE]
> <span data-ttu-id="c39d1-160">Dieser Codeausschnitt wird [Win2D](http://microsoft.github.io/Win2D/html/Introduction.htm), eine Bibliothek für 2D-Grafikrendering verwendet.</span><span class="sxs-lookup"><span data-stu-id="c39d1-160">This snippet uses [Win2D](http://microsoft.github.io/Win2D/html/Introduction.htm), a library for 2D graphics rendering.</span></span> <span data-ttu-id="c39d1-161">Finden Sie in ihrer Dokumentation Informationen dazu, wie Sie es für Ihr Projekt einrichten.</span><span class="sxs-lookup"><span data-stu-id="c39d1-161">See their documentation for information about how to set it up for your project.</span></span>

```cs
using Microsoft.Graphics.Canvas;
using Microsoft.Graphics.Canvas.UI.Composition;
using System;
using System.Numerics;
using System.Threading.Tasks;
using Windows.Foundation;
using Windows.Graphics;
using Windows.Graphics.Capture;
using Windows.Graphics.DirectX;
using Windows.UI;
using Windows.UI.Composition;
using Windows.UI.Xaml;
using Windows.UI.Xaml.Controls;
using Windows.UI.Xaml.Hosting;

namespace WindowsGraphicsCapture
{
    /// <summary>
    /// An empty page that can be used on its own or navigated to within a Frame.
    /// </summary>
    public sealed partial class MainPage : Page
    {
        // Capture API objects.
        private SizeInt32 _lastSize;
        private GraphicsCaptureItem _item;
        private Direct3D11CaptureFramePool _framePool;
        private GraphicsCaptureSession _session;

        // Non-API related members.
        private CanvasDevice _canvasDevice;
        private CompositionGraphicsDevice _compositionGraphicsDevice;
        private Compositor _compositor;
        private CompositionDrawingSurface _surface;

        public MainPage()
        {
            this.InitializeComponent();
            Setup();
        }

        private void Setup()
        {
            _canvasDevice = new CanvasDevice();
            _compositionGraphicsDevice = CanvasComposition.CreateCompositionGraphicsDevice(Window.Current.Compositor, _canvasDevice);
            _compositor = Window.Current.Compositor;

            _surface = _compositionGraphicsDevice.CreateDrawingSurface(
                new Size(400, 400),
                DirectXPixelFormat.B8G8R8A8UIntNormalized,
                DirectXAlphaMode.Premultiplied);    // This is the only value that currently works with the composition APIs.

            var visual = _compositor.CreateSpriteVisual();
            visual.RelativeSizeAdjustment = Vector2.One;
            var brush = _compositor.CreateSurfaceBrush(_surface);
            brush.HorizontalAlignmentRatio = 0.5f;
            brush.VerticalAlignmentRatio = 0.5f;
            brush.Stretch = CompositionStretch.Uniform;
            visual.Brush = brush;
            ElementCompositionPreview.SetElementChildVisual(this, visual);
        }

        public async Task StartCaptureAsync()
        {
            // The GraphicsCapturePicker follows the same pattern the 
            // file pickers do. 
            var picker = new GraphicsCapturePicker();
            GraphicsCaptureItem item = await picker.PickSingleItemAsync();

            // The item may be null if the user dismissed the 
            // control without making a selection or hit Cancel. 
            if (item != null)
            {
                StartCaptureInternal(item);
            }
        }

        private void StartCaptureInternal(GraphicsCaptureItem item)
        {
            // Stop the previous capture if we had one.
            StopCapture();

            _item = item;
            _lastSize = _item.Size;

            _framePool = Direct3D11CaptureFramePool.Create(
               _canvasDevice, // D3D device 
               DirectXPixelFormat.B8G8R8A8UIntNormalized, // Pixel format 
               2, // Number of frames 
               _item.Size); // Size of the buffers 

            _framePool.FrameArrived += (s, a) =>
            {
                // The FrameArrived event is raised for every frame on the thread
                // that created the Direct3D11CaptureFramePool. This means we 
                // don't have to do a null-check here, as we know we're the only 
                // one dequeueing frames in our application.  

                // NOTE: Disposing the frame retires it and returns  
                // the buffer to the pool.

                using (var frame = _framePool.TryGetNextFrame())
                {
                    ProcessFrame(frame);
                }
            };

            _item.Closed += (s, a) =>
            {
                StopCapture();
            };

            _session = _framePool.CreateCaptureSession(_item);
            _session.StartCapture();
        }

        public void StopCapture()
        {
            _session?.Dispose();
            _framePool?.Dispose();
            _item = null;
            _session = null;
            _framePool = null;
        }

        private void ProcessFrame(Direct3D11CaptureFrame frame)
        {
            // Resize and device-lost leverage the same function on the
            // Direct3D11CaptureFramePool. Refactoring it this way avoids 
            // throwing in the catch block below (device creation could always 
            // fail) along with ensuring that resize completes successfully and 
            // isn’t vulnerable to device-lost.   
            bool needsReset = false;
            bool recreateDevice = false;

            if ((frame.ContentSize.Width != _lastSize.Width) ||
                (frame.ContentSize.Height != _lastSize.Height))
            {
                needsReset = true;
                _lastSize = frame.ContentSize;
            }

            try
            {
                // Take the D3D11 surface and draw it into a  
                // Composition surface.

                // Convert our D3D11 surface into a Win2D object.
                var canvasBitmap = CanvasBitmap.CreateFromDirect3D11Surface(
                    _canvasDevice,
                    frame.Surface);

                // Helper that handles the drawing for us.
                FillSurfaceWithBitmap(canvasBitmap);
            }

            // This is the device-lost convention for Win2D.
            catch (Exception e) when (_canvasDevice.IsDeviceLost(e.HResult))
            {
                // We lost our graphics device. Recreate it and reset 
                // our Direct3D11CaptureFramePool.  
                needsReset = true;
                recreateDevice = true;
            }

            if (needsReset)
            {
                ResetFramePool(frame.ContentSize, recreateDevice);
            }
        }

        private void FillSurfaceWithBitmap(CanvasBitmap canvasBitmap)
        {
            CanvasComposition.Resize(_surface, canvasBitmap.Size);

            using (var session = CanvasComposition.CreateDrawingSession(_surface))
            {
                session.Clear(Colors.Transparent);
                session.DrawImage(canvasBitmap);
            }
        }

        private void ResetFramePool(SizeInt32 size, bool recreateDevice)
        {
            do
            {
                try
                {
                    if (recreateDevice)
                    {
                        _canvasDevice = new CanvasDevice();
                    }

                    _framePool.Recreate(
                        _canvasDevice,
                        DirectXPixelFormat.B8G8R8A8UIntNormalized,
                        2,
                        size);
                }
                // This is the device-lost convention for Win2D.
                catch (Exception e) when (_canvasDevice.IsDeviceLost(e.HResult))
                {
                    _canvasDevice = null;
                    recreateDevice = true;
                }
            } while (_canvasDevice == null);
        }

        private async void Button_ClickAsync(object sender, RoutedEventArgs e)
        {
            await StartCaptureAsync();
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="c39d1-162">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="c39d1-162">See also</span></span>

* [<span data-ttu-id="c39d1-163">Windows.Graphics.Capture Namespace</span><span class="sxs-lookup"><span data-stu-id="c39d1-163">Windows.Graphics.Capture Namespace</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.capture)
