---
title: Zeichnen auf den Bildschirm
description: Schließlich wird der Code portiert, der den sich drehenden Würfel auf den Bildschirm zeichnet.
ms.assetid: cc681548-f694-f613-a19d-1525a184d4ab
ms.date: 02/08/2017
ms.topic: article
keywords: windows10, uwp, spiele, directx, grafiken
ms.localizationpriority: medium
ms.openlocfilehash: fc93111d48f71a6ca8acad8191a2afb535fad2f0
ms.sourcegitcommit: d2517e522cacc5240f7dffd5bc1eaa278e3f7768
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8328289"
---
# <a name="draw-to-the-screen"></a><span data-ttu-id="1523a-104">Zeichnen auf dem Bildschirm</span><span class="sxs-lookup"><span data-stu-id="1523a-104">Draw to the screen</span></span>




**<span data-ttu-id="1523a-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="1523a-105">Important APIs</span></span>**

-   [**<span data-ttu-id="1523a-106">ID3D11Texture2D</span><span class="sxs-lookup"><span data-stu-id="1523a-106">ID3D11Texture2D</span></span>**](https://msdn.microsoft.com/library/windows/desktop/ff476635)
-   [**<span data-ttu-id="1523a-107">ID3D11RenderTargetView</span><span class="sxs-lookup"><span data-stu-id="1523a-107">ID3D11RenderTargetView</span></span>**](https://msdn.microsoft.com/library/windows/desktop/ff476582)
-   [**<span data-ttu-id="1523a-108">IDXGISwapChain1</span><span class="sxs-lookup"><span data-stu-id="1523a-108">IDXGISwapChain1</span></span>**](https://msdn.microsoft.com/library/windows/desktop/hh404631)

<span data-ttu-id="1523a-109">Schließlich wird der Code portiert, der den sich drehenden Würfel auf den Bildschirm zeichnet.</span><span class="sxs-lookup"><span data-stu-id="1523a-109">Finally, we port the code that draws the spinning cube to the screen.</span></span>

<span data-ttu-id="1523a-110">In OpenGLES2.0 wird der Zeichnungskontext als EGLContext-Typ definiert. Er enthält die Fenster- und Oberflächenparameter sowie die erforderlichen Ressourcen zum Zeichnen in die Renderziele, mit denen das im Fenster angezeigte endgültige Bild erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="1523a-110">In OpenGL ES 2.0, your drawing context is defined as an EGLContext type, which contains the window and surface parameters as well the resources necessary for drawing to the render targets that will be used to compose the final image displayed to the window.</span></span> <span data-ttu-id="1523a-111">Mithilfe dieses Kontextes konfigurieren Sie die Grafikressourcen zur korrekten Anzeige der Ergebnisse Ihrer Shaderpipeline auf dem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="1523a-111">You use this context to configure the graphics resources to correctly display the results of your shader pipeline on the display.</span></span> <span data-ttu-id="1523a-112">Eine der primären Ressourcen ist der "Hintergrundpuffer" (auch als "Framepufferobjekt" bezeichnet), der die endgültigen, zusammengesetzten und für die Darstellung auf dem Bildschirm fertigen Renderziele enthält.</span><span class="sxs-lookup"><span data-stu-id="1523a-112">One of the primary resources is the "back buffer" (or "frame buffer object") that contains the final, composited render targets, ready for presentation to the display.</span></span>

<span data-ttu-id="1523a-113">Bei Direct3D ist der Prozess zum Konfigurieren der Grafikressourcen für das Zeichnen auf den Bildschirm didaktischer und erfordert mehr APIs.</span><span class="sxs-lookup"><span data-stu-id="1523a-113">With Direct3D, the process of configuring the graphics resources for drawing to the display is more didactic, and requires quite a few more APIs.</span></span> <span data-ttu-id="1523a-114">(Eine Microsoft Visual Studio Direct3D-Vorlage kann diesen Vorgang jedoch erheblich vereinfachen.) Um einen Kontext (als Direct3D-Gerätekontext bezeichnet) zu erhalten, müssen Sie zunächst ein [**ID3D11Device1**](https://msdn.microsoft.com/library/windows/desktop/hh404575)-Objekt erhalten und dieses zur Erstellung und Konfigurierung eines [**ID3D11DeviceContext1**](https://msdn.microsoft.com/library/windows/desktop/hh404598)-Objekts verwenden.</span><span class="sxs-lookup"><span data-stu-id="1523a-114">(A Microsoft Visual Studio Direct3D template can significantly simplify this process, though!) To obtain a context (called a Direct3D device context), you must first obtain an [**ID3D11Device1**](https://msdn.microsoft.com/library/windows/desktop/hh404575) object, and use it to create and configure an [**ID3D11DeviceContext1**](https://msdn.microsoft.com/library/windows/desktop/hh404598) object.</span></span> <span data-ttu-id="1523a-115">Diese beiden Objekte werden zusammen verwendet, um die spezifischen Ressourcen zu konfigurieren, die Sie zum Zeichnen auf den Bildschirm benötigen.</span><span class="sxs-lookup"><span data-stu-id="1523a-115">These two objects are used in conjunction to configure the specific resources you need for drawing to the display.</span></span>

<span data-ttu-id="1523a-116">Kurz gesagt: Die DXGI-APIs enthalten in erster Linie APIs zum Verwalten von Ressourcen, die direkt den Grafikadapter betreffen, und Direct3D enthält die APIs, mit denen Sie die GPU und Ihr in der CPU ausgeführtes Hauptprogramm verknüpfen können.</span><span class="sxs-lookup"><span data-stu-id="1523a-116">In short, the DXGI APIs contain primarily APIs for managing resources that directly pertain to the graphics adapter, and Direct3D contains the APIs that allow you to interface between the GPU and your main program running on the CPU.</span></span>

<span data-ttu-id="1523a-117">Zum Vergleich werden in diesem Beispiel die folgenden relevanten Typen aus den APIs verwendet:</span><span class="sxs-lookup"><span data-stu-id="1523a-117">For the purposes of comparison in this sample, here are the relevant types from each API:</span></span>

-   <span data-ttu-id="1523a-118">[**ID3D11Device1**](https://msdn.microsoft.com/library/windows/desktop/hh404575): Stellt eine virtuelle Darstellung des Grafikgeräts und seiner Ressourcen bereit.</span><span class="sxs-lookup"><span data-stu-id="1523a-118">[**ID3D11Device1**](https://msdn.microsoft.com/library/windows/desktop/hh404575): provides a virtual representation of the graphics device and its resources.</span></span>
-   <span data-ttu-id="1523a-119">[**ID3D11DeviceContext1**](https://msdn.microsoft.com/library/windows/desktop/hh404598): Stellt die Schnittstelle zum Konfigurieren von Puffern und Ausgeben von Renderbefehlen bereit.</span><span class="sxs-lookup"><span data-stu-id="1523a-119">[**ID3D11DeviceContext1**](https://msdn.microsoft.com/library/windows/desktop/hh404598): provides the interface to configure buffers and issue rendering commands.</span></span>
-   <span data-ttu-id="1523a-120">[**IDXGISwapChain1**](https://msdn.microsoft.com/library/windows/desktop/hh404631): Die Swapchain entspricht dem Hintergrundpuffer in OpenGL ES 2.0.</span><span class="sxs-lookup"><span data-stu-id="1523a-120">[**IDXGISwapChain1**](https://msdn.microsoft.com/library/windows/desktop/hh404631): the swap chain is analogous to the back buffer in OpenGL ES 2.0.</span></span> <span data-ttu-id="1523a-121">Sie ist der Bereich im Speicher des Grafikadapters, der die endgültigen gerenderten Bilder für die Anzeige enthält.</span><span class="sxs-lookup"><span data-stu-id="1523a-121">It is the region of memory on the graphics adapter that contains the final rendered image(s) for display.</span></span> <span data-ttu-id="1523a-122">Dieser Bereich wird als „Swapchain“ bezeichnet, da er mehrere beschreibbare Puffer enthält, die ausgetauscht werden können, um das aktuelle Renderbild auf dem Bildschirm darzustellen.</span><span class="sxs-lookup"><span data-stu-id="1523a-122">It is called the "swap chain" because it has several buffers that can be written to and "swapped" to present the latest render to the screen.</span></span>
-   <span data-ttu-id="1523a-123">[**ID3D11RenderTargetView**](https://msdn.microsoft.com/library/windows/desktop/ff476582): Enthält den 2D-Bitmappuffer, in den der Direct3D-Gerätekontext zeichnet und der von der Swapchain dargestellt wird.</span><span class="sxs-lookup"><span data-stu-id="1523a-123">[**ID3D11RenderTargetView**](https://msdn.microsoft.com/library/windows/desktop/ff476582): this contains the 2D bitmap buffer that the Direct3D device context draws into, and which is presented by the swap chain.</span></span> <span data-ttu-id="1523a-124">Wie bei OpenGLES2.0 können Sie mehrere Renderziele haben, von denen einige nicht an die Swapchain gebunden sind, die aber für Schattierungstechniken mit mehreren Durchgängen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1523a-124">As with OpenGL ES 2.0, you can have multiple render targets, some of which are not bound to the swap chain but are used for multi-pass shading techniques.</span></span>

<span data-ttu-id="1523a-125">In der Vorlage enthält das Rendererobjekt die folgenden Felder:</span><span class="sxs-lookup"><span data-stu-id="1523a-125">In the template, the renderer object contains the following fields:</span></span>

<span data-ttu-id="1523a-126">Direct3D11: Gerät- und Gerätekontextdeklarationen</span><span class="sxs-lookup"><span data-stu-id="1523a-126">Direct3D 11: Device and device context declarations</span></span>

``` syntax
Platform::Agile<Windows::UI::Core::CoreWindow>       m_window;

Microsoft::WRL::ComPtr<ID3D11Device1>                m_d3dDevice;
Microsoft::WRL::ComPtr<ID3D11DeviceContext1>          m_d3dContext;
Microsoft::WRL::ComPtr<IDXGISwapChain1>                      m_swapChainCoreWindow;
Microsoft::WRL::ComPtr<ID3D11RenderTargetView>          m_d3dRenderTargetViewWin;
```

<span data-ttu-id="1523a-127">Hier sehen Sie, wie der Hintergrundpuffer als Renderziel konfiguriert und für die Swapchain bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="1523a-127">Here's how the back buffer is configured as a render target and provided to the swap chain.</span></span>

``` syntax
ComPtr<ID3D11Texture2D> backBuffer;
m_swapChainCoreWindow->GetBuffer(0, IID_PPV_ARGS(backBuffer));
m_d3dDevice->CreateRenderTargetView(
  backBuffer.Get(),
  nullptr,
  &m_d3dRenderTargetViewWin);
```

<span data-ttu-id="1523a-128">Die Direct3D-Laufzeit erstellt implizit eine [**IDXGISurface1**](https://msdn.microsoft.com/library/windows/desktop/ff471343) für die [**ID3D11Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff476635). Diese stellt die Textur als „Hintergrundpuffer“ dar, der von der Swapchain zur Anzeige verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="1523a-128">The Direct3D runtime implicitly creates an [**IDXGISurface1**](https://msdn.microsoft.com/library/windows/desktop/ff471343) for the [**ID3D11Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff476635), which represents the texture as a "back buffer" that the swap chain can use for display.</span></span>

<span data-ttu-id="1523a-129">Für die Initialisierung und Konfiguration des Direct3D-Geräts und -Gerätekontexts sowie der Renderziele dienen die benutzerdefinierten Methoden **CreateDeviceResources** und **CreateWindowSizeDependentResources** in der Direct3D-Vorlage.</span><span class="sxs-lookup"><span data-stu-id="1523a-129">The initialization and configuration of the Direct3D device and device context, as well as the render targets, can be found in the custom **CreateDeviceResources** and **CreateWindowSizeDependentResources** methods in the Direct3D template.</span></span>

<span data-ttu-id="1523a-130">Weitere Informationen zum Direct3D-Gerätekontext und dessen Beziehung zu EGL und zum EGLContext-Typ finden Sie unter [Portieren von EGL-Code zu DXGI und Direct3D](moving-from-egl-to-dxgi.md).</span><span class="sxs-lookup"><span data-stu-id="1523a-130">For more info on Direct3D device context as it relates to EGL and the EGLContext type, read [Port EGL code to DXGI and Direct3D](moving-from-egl-to-dxgi.md).</span></span>

## <a name="instructions"></a><span data-ttu-id="1523a-131">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="1523a-131">Instructions</span></span>

### <a name="step-1-rendering-the-scene-and-displaying-it"></a><span data-ttu-id="1523a-132">Schritt1: Rendern und Anzeigen der Szene</span><span class="sxs-lookup"><span data-stu-id="1523a-132">Step 1: Rendering the scene and displaying it</span></span>

<span data-ttu-id="1523a-133">Nach dem Aktualisieren der Würfeldaten (in diesem Fall durch eine leichte Drehung des Würfels um die y-Achse) legt die Rendermethode den Viewport auf die Dimensionen des Zeichnungskontextes (EGLContext) fest.</span><span class="sxs-lookup"><span data-stu-id="1523a-133">After updating the cube data (in this case, by rotating it slightly around the y axis), the Render method sets the viewport to the dimensions of he drawing context (an EGLContext).</span></span> <span data-ttu-id="1523a-134">Dieser Kontext enthält den Farbpuffer, der unter Verwendung der konfigurierten Anzeige (EGLDisplay) auf der Fensteroberfläche (EGLSurface) angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="1523a-134">This context contains the color buffer that will be displayed to the window surface (an EGLSurface), using the configured display (EGLDisplay).</span></span> <span data-ttu-id="1523a-135">Dabei werden folgende Schritte ausgeführt: Die Scheitelpunktdaten-Attribute werden aktualisiert, der Indexpuffer wird erneut gebunden, der Würfel wird gezeichnet, und der von der Schattierungspipeline gezeichnete Farbpuffer wird ausgetauscht und auf der Anzeigeoberfläche dargestellt.</span><span class="sxs-lookup"><span data-stu-id="1523a-135">At this time, the example updates the vertex data attributes, re-binds the index buffer, draws the cube, and swaps in color buffer drawn by the shading pipeline to the display surface.</span></span>

<span data-ttu-id="1523a-136">OpenGLES2.0: Rendern eines Frames für die Anzeige</span><span class="sxs-lookup"><span data-stu-id="1523a-136">OpenGL ES 2.0: Rendering a frame for display</span></span>

``` syntax
void Render(GraphicsContext *drawContext)
{
  Renderer *renderer = drawContext->renderer;

  int loc;
   
  // Set the viewport
  glViewport ( 0, 0, drawContext->width, drawContext->height );
   
   
  // Clear the color buffer
  glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
  glEnable(GL_DEPTH_TEST);


  // Use the program object
  glUseProgram (renderer->programObject);

  // Load the a_position attribute with the vertex position portion of a vertex buffer element
  loc = glGetAttribLocation(renderer->programObject, "a_position");
  glVertexAttribPointer(loc, 3, GL_FLOAT, GL_FALSE, 
      sizeof(Vertex), 0);
  glEnableVertexAttribArray(loc);

  // Load the a_color attribute with the color position portion of a vertex buffer element
  loc = glGetAttribLocation(renderer->programObject, "a_color");
  glVertexAttribPointer(loc, 4, GL_FLOAT, GL_FALSE, 
      sizeof(Vertex), (GLvoid*) (sizeof(float) * 3));
  glEnableVertexAttribArray(loc);

  // Bind the index buffer
  glBindBuffer(GL_ELEMENT_ARRAY_BUFFER, renderer->indexBuffer);

  // Load the MVP matrix
  glUniformMatrix4fv(renderer->mvpLoc, 1, GL_FALSE, (GLfloat*) &renderer->mvpMatrix.m[0][0]);

  // Draw the cube
  glDrawElements(GL_TRIANGLES, renderer->numIndices, GL_UNSIGNED_INT, 0);

  eglSwapBuffers(drawContext->eglDisplay, drawContext->eglSurface);
}
```

<span data-ttu-id="1523a-137">Der Prozess in Direct3D11 ist sehr ähnlich.</span><span class="sxs-lookup"><span data-stu-id="1523a-137">In Direct3D 11, the process is very similar.</span></span> <span data-ttu-id="1523a-138">(Es wird vorausgesetzt, dass Sie die Viewport- und Renderzielkonfiguration der Direct3D-Vorlage verwenden.)</span><span class="sxs-lookup"><span data-stu-id="1523a-138">(We're assuming that you're using the viewport and render target configuration from the Direct3D template.</span></span>

-   <span data-ttu-id="1523a-139">Aktualisieren Sie die Konstantenpuffer (in diesem Fall die Modell-Anzeige-Projizierungsmatrix) mit Aufrufen für [**ID3D11DeviceContext1::UpdateSubresource**](https://msdn.microsoft.com/library/windows/desktop/hh446790).</span><span class="sxs-lookup"><span data-stu-id="1523a-139">Update the constant buffers (the model-view-projection matrix, in this case) with calls to [**ID3D11DeviceContext1::UpdateSubresource**](https://msdn.microsoft.com/library/windows/desktop/hh446790).</span></span>
-   <span data-ttu-id="1523a-140">Legen Sie den Scheitelpunktpuffer mit [**ID3D11DeviceContext1::IASetVertexBuffers**](https://msdn.microsoft.com/library/windows/desktop/ff476456) fest.</span><span class="sxs-lookup"><span data-stu-id="1523a-140">Set the vertex buffer with [**ID3D11DeviceContext1::IASetVertexBuffers**](https://msdn.microsoft.com/library/windows/desktop/ff476456).</span></span>
-   <span data-ttu-id="1523a-141">Legen Sie den Indexpuffer mit [**ID3D11DeviceContext1::IASetIndexBuffer**](https://msdn.microsoft.com/library/windows/desktop/ff476453) fest.</span><span class="sxs-lookup"><span data-stu-id="1523a-141">Set the index buffer with [**ID3D11DeviceContext1::IASetIndexBuffer**](https://msdn.microsoft.com/library/windows/desktop/ff476453).</span></span>
-   <span data-ttu-id="1523a-142">Legen Sie die spezifische Dreieckstopologie (eine Dreiecksliste) mit [**ID3D11DeviceContext1::IASetPrimitiveTopology**](https://msdn.microsoft.com/library/windows/desktop/ff476455) fest.</span><span class="sxs-lookup"><span data-stu-id="1523a-142">Set the specific triangle topology (a triangle list) with [**ID3D11DeviceContext1::IASetPrimitiveTopology**](https://msdn.microsoft.com/library/windows/desktop/ff476455).</span></span>
-   <span data-ttu-id="1523a-143">Legen Sie das Eingabelayout des Scheitelpunktpuffers mit [**ID3D11DeviceContext1::IASetInputLayout**](https://msdn.microsoft.com/library/windows/desktop/ff476454) fest.</span><span class="sxs-lookup"><span data-stu-id="1523a-143">Set the input layout of the vertex buffer with [**ID3D11DeviceContext1::IASetInputLayout**](https://msdn.microsoft.com/library/windows/desktop/ff476454).</span></span>
-   <span data-ttu-id="1523a-144">Binden Sie den Vertex-Shader mit [**ID3D11DeviceContext1::VSSetShader**](https://msdn.microsoft.com/library/windows/desktop/ff476493).</span><span class="sxs-lookup"><span data-stu-id="1523a-144">Bind the vertex shader with [**ID3D11DeviceContext1::VSSetShader**](https://msdn.microsoft.com/library/windows/desktop/ff476493).</span></span>
-   <span data-ttu-id="1523a-145">Binden Sie den Fragment-Shader mit [**ID3D11DeviceContext1::PSSetShader**](https://msdn.microsoft.com/library/windows/desktop/ff476472).</span><span class="sxs-lookup"><span data-stu-id="1523a-145">Bind the fragment shader with [**ID3D11DeviceContext1::PSSetShader**](https://msdn.microsoft.com/library/windows/desktop/ff476472).</span></span>
-   <span data-ttu-id="1523a-146">Senden Sie die indizierten Scheitelpunkte durch die Shader, und geben Sie die Farbergebnisse mit [**ID3D11DeviceContext1::DrawIndexed**](https://msdn.microsoft.com/library/windows/desktop/ff476409) an den Renderzielpuffer aus.</span><span class="sxs-lookup"><span data-stu-id="1523a-146">Send the indexed vertices through the shaders and output the color results to the render target buffer with [**ID3D11DeviceContext1::DrawIndexed**](https://msdn.microsoft.com/library/windows/desktop/ff476409).</span></span>
-   <span data-ttu-id="1523a-147">Zeigen Sie den Renderzielpuffer mit [**IDXGISwapChain1::Present1**](https://msdn.microsoft.com/library/windows/desktop/hh446797) an.</span><span class="sxs-lookup"><span data-stu-id="1523a-147">Display the render target buffer with [**IDXGISwapChain1::Present1**](https://msdn.microsoft.com/library/windows/desktop/hh446797).</span></span>

<span data-ttu-id="1523a-148">Direct3D11: Rendern eines Frames zur Anzeige</span><span class="sxs-lookup"><span data-stu-id="1523a-148">Direct3D 11: Rendering a frame for display</span></span>

``` syntax
void RenderObject::Render()
{
  // ...

  // Only update shader resources that have changed since the last frame.
  m_d3dContext->UpdateSubresource(
    m_constantBuffer.Get(),
    0,
    NULL,
    &m_constantBufferData,
    0,
    0);

  // Set up the IA stage corresponding to the current draw operation.
  UINT stride = sizeof(VertexPositionColor);
  UINT offset = 0;
  m_d3dContext->IASetVertexBuffers(
    0,
    1,
    m_vertexBuffer.GetAddressOf(),
    &stride,
    &offset);

  m_d3dContext->IASetIndexBuffer(
    m_indexBuffer.Get(),
    DXGI_FORMAT_R16_UINT,
    0);

  m_d3dContext->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
  m_d3dContext->IASetInputLayout(m_inputLayout.Get());

  // Set up the vertex shader corresponding to the current draw operation.
  m_d3dContext->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0);

  m_d3dContext->VSSetConstantBuffers(
    0,
    1,
    m_constantBuffer.GetAddressOf());

  // Set up the pixel shader corresponding to the current draw operation.
  m_d3dContext->PSSetShader(
    m_pixelShader.Get(),
    nullptr,
    0);

  m_d3dContext->DrawIndexed(
    m_indexCount,
    0,
    0);

    // ...

  m_swapChainCoreWindow->Present1(1, 0, &parameters);
}

```

<span data-ttu-id="1523a-149">Nachdem [**IDXGISwapChain1::Present1**](https://msdn.microsoft.com/library/windows/desktop/hh446797) aufgerufen wurde, wird der Frame an die konfigurierte Anzeige ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="1523a-149">Once [**IDXGISwapChain1::Present1**](https://msdn.microsoft.com/library/windows/desktop/hh446797) is called, your frame is output to the configured display.</span></span>

## <a name="previous-step"></a><span data-ttu-id="1523a-150">Vorheriger Schritt</span><span class="sxs-lookup"><span data-stu-id="1523a-150">Previous step</span></span>


[<span data-ttu-id="1523a-151">Portieren des GLSL-Codes</span><span class="sxs-lookup"><span data-stu-id="1523a-151">Port the GLSL</span></span>](port-the-glsl.md)

## <a name="remarks"></a><span data-ttu-id="1523a-152">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="1523a-152">Remarks</span></span>

<span data-ttu-id="1523a-153">In diesem Beispiel wurden viele der komplexen Schritte beim Konfigurieren von Geräteressourcen ausgelassen, insbesondere für UWP-DirectX-Apps (Universelle Windows-Plattform).</span><span class="sxs-lookup"><span data-stu-id="1523a-153">This example glosses over much of the complexity that goes into configuring device resources, especially for Universal Windows Platform (UWP) DirectX apps.</span></span> <span data-ttu-id="1523a-154">Wir empfehlen, den vollständigen Vorlagencode durchzugehen, vor allem die Teile, die die Einrichtung und Verwaltung der Fenster- und Geräteressourcen betreffen.</span><span class="sxs-lookup"><span data-stu-id="1523a-154">We suggest you review the full template code, especially the parts that perform the window and device resource setup and management.</span></span> <span data-ttu-id="1523a-155">UWP-Apps müssen sowohl Drehungsereignisse als auch Anhalte-/Fortsetzungsereignisse unterstützen. Die Vorlage zeigt die empfohlenen Methoden zum Behandeln des Verlusts einer Schnittstelle oder einer Änderung der Anzeigeparameter.</span><span class="sxs-lookup"><span data-stu-id="1523a-155">UWP apps have to support rotation events as well as suspend/resume events, and the template demonstrates best practices for handling the loss of an interface or a change in the display parameters.</span></span>

## <a name="related-topics"></a><span data-ttu-id="1523a-156">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="1523a-156">Related topics</span></span>


* [<span data-ttu-id="1523a-157">Portieren eines einfachen OpenGL ES 2.0-Renderers zu Direct3D 11</span><span class="sxs-lookup"><span data-stu-id="1523a-157">How to: port a simple OpenGL ES 2.0 renderer to Direct3D 11</span></span>](port-a-simple-opengl-es-2-0-renderer-to-directx-11-1.md)
* [<span data-ttu-id="1523a-158">Portieren der Shaderobjekte</span><span class="sxs-lookup"><span data-stu-id="1523a-158">Port the shader objects</span></span>](port-the-shader-config.md)
* [<span data-ttu-id="1523a-159">Portieren des GLSL-Codes</span><span class="sxs-lookup"><span data-stu-id="1523a-159">Port the GLSL</span></span>](port-the-glsl.md)
* [<span data-ttu-id="1523a-160">Zeichnen auf den Bildschirm</span><span class="sxs-lookup"><span data-stu-id="1523a-160">Draw to the screen</span></span>](draw-to-the-screen.md)

 

 




