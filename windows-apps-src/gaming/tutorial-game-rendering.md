---
author: joannaleecy
title: Einrichtung
description: Hier erfahren Sie, wie Sie die Renderingpipeline zum Anzeigen von Grafiken zusammenstellen. Spiel-Rendering, Einrichten und Vorbereiten von Daten.
ms.assetid: 7720ac98-9662-4cf3-89c5-7ff81896364a
ms.author: joanlee
ms.date: 10/24/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Rendern
ms.localizationpriority: medium
ms.openlocfilehash: 134c9005a796f52fb61ba628c0a85c8dbd875442
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5938963"
---
# <a name="rendering-framework-ii-game-rendering"></a><span data-ttu-id="e3b74-105">Rendering-Framework II: Spiel-Rendering</span><span class="sxs-lookup"><span data-stu-id="e3b74-105">Rendering framework II: Game rendering</span></span>

<span data-ttu-id="e3b74-106">In [Rendering-Framework I](tutorial--assembling-the-rendering-pipeline.md) haben wir behandelt, wie wir Szeneninformationen erfassen und auf dem Bildschirm anzeigen.</span><span class="sxs-lookup"><span data-stu-id="e3b74-106">In [Rendering framework I](tutorial--assembling-the-rendering-pipeline.md), we've covered how we take the scene info and present it to the display screen.</span></span> <span data-ttu-id="e3b74-107">Jetzt gehen wir einen Schritt zurück und erläutern, wie Sie die Daten für das Rendering vorbereiten.</span><span class="sxs-lookup"><span data-stu-id="e3b74-107">Now, we'll take a step back and learn how to prepare the data for rendering.</span></span>

>[!Note]
><span data-ttu-id="e3b74-108">Wenn Sie den neuesten Code für dieses Beispiel noch nicht heruntergeladen haben, wechseln Sie zu [Direct3D-Spielbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Simple3DGameDX).</span><span class="sxs-lookup"><span data-stu-id="e3b74-108">If you haven't downloaded the latest game code for this sample, go to [Direct3D game sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Simple3DGameDX).</span></span> <span data-ttu-id="e3b74-109">Dieses Beispiel gehört zu einer großen Sammlung von UWP-Featurebeispielen.</span><span class="sxs-lookup"><span data-stu-id="e3b74-109">This sample is part of a large collection of UWP feature samples.</span></span> <span data-ttu-id="e3b74-110">Anweisungen zum Herunterladen des Beispiels finden Sie unter [Abrufen der UWP-Beispiele von GitHub](https://docs.microsoft.com/windows/uwp/get-started/get-uwp-app-samples).</span><span class="sxs-lookup"><span data-stu-id="e3b74-110">For instructions on how to download the sample, see [Get the UWP samples from GitHub](https://docs.microsoft.com/windows/uwp/get-started/get-uwp-app-samples).</span></span>

## <a name="objective"></a><span data-ttu-id="e3b74-111">Ziel</span><span class="sxs-lookup"><span data-stu-id="e3b74-111">Objective</span></span>

<span data-ttu-id="e3b74-112">Kurze Zusammenfassung des Ziels dieses Abschnitts:</span><span class="sxs-lookup"><span data-stu-id="e3b74-112">Quick recap on the objective.</span></span> <span data-ttu-id="e3b74-113">Es soll vermittelt werden, wie Sie ein einfaches Rendering-Framework einrichten, um die Grafikausgabe für ein UWP-DirectX-Spiel anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="e3b74-113">It is to understand how to set up a basic rendering framework to display the graphics output for a UWP DirectX game.</span></span> <span data-ttu-id="e3b74-114">Dazu sind drei Schritte erforderlich.</span><span class="sxs-lookup"><span data-stu-id="e3b74-114">We can loosely group them into these three steps.</span></span>

 1. <span data-ttu-id="e3b74-115">Einrichten einer Verbindung zur Grafikschnittstelle</span><span class="sxs-lookup"><span data-stu-id="e3b74-115">Establish a connection to our graphics interface</span></span>
 2. <span data-ttu-id="e3b74-116">Vorbereitung: Erstellen der Ressourcen, die zum Zeichnen der Grafiken benötigt werden</span><span class="sxs-lookup"><span data-stu-id="e3b74-116">Preparation: Create the resources we need to draw the graphics</span></span>
 3. <span data-ttu-id="e3b74-117">Anzeigen die Grafiken: Rendern des Frames</span><span class="sxs-lookup"><span data-stu-id="e3b74-117">Display the graphics: Render the frame</span></span>

<span data-ttu-id="e3b74-118">[Rendering-Framework I: Einführung in das Rendering](tutorial--assembling-the-rendering-pipeline.md) erläutert, wie Grafiken gerendert werden. Behandelt werden die Schritte 1 und 3.</span><span class="sxs-lookup"><span data-stu-id="e3b74-118">[Rendering framework I: Intro to rendering](tutorial--assembling-the-rendering-pipeline.md) explained how graphics are rendered, covering Steps 1 and 3.</span></span> 

<span data-ttu-id="e3b74-119">In diesem Artikel wird erläutert, wie Sie andere Teile dieses Frameworks einrichten und die erforderlichen Daten vorbereiten, bevor das Rendern (Schritt 2 des Prozesses) ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="e3b74-119">This article explains how to set up other pieces of this framework and prepare the required data before rendering can happen, which is Step 2 of the process.</span></span>

## <a name="design-the-renderer"></a><span data-ttu-id="e3b74-120">Entwerfen des Renderers</span><span class="sxs-lookup"><span data-stu-id="e3b74-120">Design the renderer</span></span>

<span data-ttu-id="e3b74-121">Der Renderer ist verantwortlich für das Erstellen und Verwalten alle D3D11- und D2D-Objekte, die verwendet, um die visuellen Spielelemente generieren.</span><span class="sxs-lookup"><span data-stu-id="e3b74-121">The renderer is responsible for creating and maintaining all the D3D11 and D2D objects used to generate the game visuals.</span></span> <span data-ttu-id="e3b74-122">Die Klasse __GameRenderer__ ist der Renderer für dieses Beispielspiel und wurde entwickelt, um Rendering-Anforderungen des Spiels zu erfüllen.</span><span class="sxs-lookup"><span data-stu-id="e3b74-122">The __GameRenderer__ class is the renderer for this sample game and is designed to meet the game's rendering needs.</span></span>

<span data-ttu-id="e3b74-123">Hier einige Konzepte, die Sie verwenden können, um den Renderer für Ihr Spiel zu entwerfen:</span><span class="sxs-lookup"><span data-stu-id="e3b74-123">These are some concepts you can use to help design the renderer for your game:</span></span>
* <span data-ttu-id="e3b74-124">Da Direct3D11-APIs als [COM](https://msdn.microsoft.com/library/windows/desktop/ms694363.aspx)-APIs definiert sind, müssen Sie [ComPtr](https://docs.microsoft.com/cpp/windows/comptr-class)-Verweise auf die von diesen APIs definierten Objekte bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="e3b74-124">Because Direct3D 11 APIs are defined as [COM](https://msdn.microsoft.com/library/windows/desktop/ms694363.aspx) APIs, you must provide [ComPtr](https://docs.microsoft.com/cpp/windows/comptr-class) references to the objects defined by these APIs.</span></span> <span data-ttu-id="e3b74-125">Diese Objekte werden automatisch freigegeben, wenn ihr letzter Verweis den gültigen Bereich verlässt und die App beendet wird.</span><span class="sxs-lookup"><span data-stu-id="e3b74-125">These objects are automatically freed when their last reference goes out of scope when the app terminates.</span></span> <span data-ttu-id="e3b74-126">Weitere Informationen finden Sie unter [ComPtr](https://github.com/Microsoft/DirectXTK/wiki/ComPtr).</span><span class="sxs-lookup"><span data-stu-id="e3b74-126">For more information, see [ComPtr](https://github.com/Microsoft/DirectXTK/wiki/ComPtr).</span></span> <span data-ttu-id="e3b74-127">Beispiel für diese Objekte: Konstantenpuffer, Shaderobjekte – [Vertex-Shader](tutorial--assembling-the-rendering-pipeline.md#vertex-shaders-and-pixel-shaders), [Pixel-Shader](tutorial--assembling-the-rendering-pipeline.md#vertex-shaders-and-pixel-shaders) und Shaderressourcenobjekte.</span><span class="sxs-lookup"><span data-stu-id="e3b74-127">Example of these objects: constant buffers, shader objects - [vertex shader](tutorial--assembling-the-rendering-pipeline.md#vertex-shaders-and-pixel-shaders), [pixel shader](tutorial--assembling-the-rendering-pipeline.md#vertex-shaders-and-pixel-shaders), and shader resource objects.</span></span>
* <span data-ttu-id="e3b74-128">Konstantenpuffer sind in dieser Klasse definiert, um verschiedene Daten aufzunehmen, die zum Rendern benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="e3b74-128">Constant buffers are defined in this class to hold various data needed for rendering.</span></span>
    * <span data-ttu-id="e3b74-129">Durch die Verwendung mehrerer Konstantenpuffer für unterschiedliche Häufigkeiten kann die Menge an Daten reduziert werden, die pro Frame an die GPU gesendet werden müssen.</span><span class="sxs-lookup"><span data-stu-id="e3b74-129">Use multiple constant buffers with different frequencies to reduce the amount of data that must be sent to the GPU per frame.</span></span> <span data-ttu-id="e3b74-130">In diesem Beispiel werden die Konstanten basierend auf der Häufigkeit, mit der sie aktualisiert werden müssen, auf verschiedene Puffer verteilt.</span><span class="sxs-lookup"><span data-stu-id="e3b74-130">This sample separates constants into different buffers based on the frequency that they must be updated.</span></span> <span data-ttu-id="e3b74-131">Dies ist die empfohlene Methode für die Direct3D-Programmierung.</span><span class="sxs-lookup"><span data-stu-id="e3b74-131">This is a best practice for Direct3D programming.</span></span> 
    * <span data-ttu-id="e3b74-132">In diesem Beispielspiel sind 4 Konstantenpuffer definiert.</span><span class="sxs-lookup"><span data-stu-id="e3b74-132">In this game sample, 4 constant buffers are defined.</span></span>
        1. <span data-ttu-id="e3b74-133">__m\_constantBufferNeverChanges__ enthält die Beleuchtungsparameter.</span><span class="sxs-lookup"><span data-stu-id="e3b74-133">__m\_constantBufferNeverChanges__ contains the lighting parameters.</span></span> <span data-ttu-id="e3b74-134">Es wird einmal in der Methode __FinalizeCreateGameDeviceResources__ festgelegt und ändert sich nie wieder.</span><span class="sxs-lookup"><span data-stu-id="e3b74-134">It's set one time in the __FinalizeCreateGameDeviceResources__ method and never changes again.</span></span>
        2. <span data-ttu-id="e3b74-135">__m\_constantBufferChangeOnResize__ enthält die Projektionsmatrix.</span><span class="sxs-lookup"><span data-stu-id="e3b74-135">__m\_constantBufferChangeOnResize__ contains the projection matrix.</span></span> <span data-ttu-id="e3b74-136">Die Projektionsmatrix hängt von der Größe und dem Seitenverhältnis des Fensters ab.</span><span class="sxs-lookup"><span data-stu-id="e3b74-136">The projection matrix is dependent on the size and aspect ratio of the window.</span></span> <span data-ttu-id="e3b74-137">Sie wird in [__CreateWindowSizeDependentResources__](#createwindowsizedependentresources-method) festgelegt und aktualisiert, nachdem Ressourcen in die Methode [__FinalizeCreateGameDeviceResources__](#finalizecreategamedeviceresources-method) geladen wurden.</span><span class="sxs-lookup"><span data-stu-id="e3b74-137">It's set in [__CreateWindowSizeDependentResources__](#createwindowsizedependentresources-method) and then updated after resources are loaded in the [__FinalizeCreateGameDeviceResources__](#finalizecreategamedeviceresources-method) method.</span></span> <span data-ttu-id="e3b74-138">Beim Rendern in 3D wird sie auch zweimal pro Frame geändert.</span><span class="sxs-lookup"><span data-stu-id="e3b74-138">If rendering in 3D, it is also changed twice per frame.</span></span>
        3. <span data-ttu-id="e3b74-139">__m\_constantBufferChangesEveryFrame__ enthält die Ansichtsmatrix.</span><span class="sxs-lookup"><span data-stu-id="e3b74-139">__m\_constantBufferChangesEveryFrame__ contains the view matrix.</span></span> <span data-ttu-id="e3b74-140">Diese Matrix hängt von der Kameraposition und der Blickrichtung (der Projektionsnormalen) ab und ändert sich einmal pro Frame in __Render__-Methode.</span><span class="sxs-lookup"><span data-stu-id="e3b74-140">This matrix is dependent on the camera position and look direction (the normal to the projection) and changes one time per frame in the __Render__ method.</span></span> <span data-ttu-id="e3b74-141">Dies wurde in __Rendering-Framework I: Einführung in das Rendering__ in Verbindung mit der Methode [__GameRenderer::Render__](tutorial--assembling-the-rendering-pipeline.md#gamerendererrender-method) bereits erläutert.</span><span class="sxs-lookup"><span data-stu-id="e3b74-141">This was discussed earlier in __Rendering framework I: Intro to rendering__, under the [__GameRenderer::Render__ method](tutorial--assembling-the-rendering-pipeline.md#gamerendererrender-method).</span></span>
        4. <span data-ttu-id="e3b74-142">__m\_constantBufferChangesEveryPrim__ enthält die Modellmatrix und die Materialeigenschaften jedes Grundtyps.</span><span class="sxs-lookup"><span data-stu-id="e3b74-142">__m\_constantBufferChangesEveryPrim__ contains the model matrix and material properties of each primitive.</span></span> <span data-ttu-id="e3b74-143">Die Modellmatrix transformiert Scheitelpunkte aus lokalen Koordinaten in globale Koordinaten.</span><span class="sxs-lookup"><span data-stu-id="e3b74-143">The model matrix transforms vertices from local coordinates into world coordinates.</span></span> <span data-ttu-id="e3b74-144">Diese Konstanten gelten speziell für die einzelnen Grundtypen und werden für jeden Draw-Aufruf aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="e3b74-144">These constants are specific to each primitive and are updated for every draw call.</span></span> <span data-ttu-id="e3b74-145">Dies wurde in __Rendering-Framework I: Einführung in das Rendering__ unter [Rendern der Grundtypen](tutorial--assembling-the-rendering-pipeline.md#primitive-rendering) bereits erläutert.</span><span class="sxs-lookup"><span data-stu-id="e3b74-145">This was discussed earlier in __Rendering framework I: Intro to rendering__, under the [Primitive rendering](tutorial--assembling-the-rendering-pipeline.md#primitive-rendering).</span></span>
* <span data-ttu-id="e3b74-146">Shaderressourcenobjekte, die Texturen für die Grundtypen enthalten, werden in dieser Klasse ebenfalls definiert.</span><span class="sxs-lookup"><span data-stu-id="e3b74-146">Shader resource objects that hold textures for the primitives are also defined in this class.</span></span>
    * <span data-ttu-id="e3b74-147">Einige Texturen sind vordefiniert ([DDS](https://msdn.microsoft.com/library/windows/desktop/bb943991.aspx) ist ein Dateiformat, das zum Speichern von komprimierten und unkomprimierten Texturen verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="e3b74-147">Some textures are pre-defined ([DDS](https://msdn.microsoft.com/library/windows/desktop/bb943991.aspx) is a file format that can be used to store compressed and uncompressed textures.</span></span> <span data-ttu-id="e3b74-148">DDS-Texturen werden für die Wände und den Boden der Welt sowie für die Munitionskugeln verwendet.)</span><span class="sxs-lookup"><span data-stu-id="e3b74-148">DDS textures are used for the walls and floor of the world as well as the ammo spheres.)</span></span>
    * <span data-ttu-id="e3b74-149">Shaderressourcenobjekte in diesem Beispielspiel sind: __m\_sphereTexture__, __m\_cylinderTexture__, __m\_ceilingTexture__, __m\_floorTexture__, __m\_wallsTexture__.</span><span class="sxs-lookup"><span data-stu-id="e3b74-149">In this game sample, shader resource objects are: __m\_sphereTexture__, __m\_cylinderTexture__, __m\_ceilingTexture__, __m\_floorTexture__, __m\_wallsTexture__.</span></span>
* <span data-ttu-id="e3b74-150">Shaderobjekte werden in dieser Klasse zur Berechnung der Grundtypen und Texturen definiert.</span><span class="sxs-lookup"><span data-stu-id="e3b74-150">Shader objects are defined in this class to compute our primitives and textures.</span></span> 
    * <span data-ttu-id="e3b74-151">Die Shaderobjekte in diesem Beispielspiel sind __m\_vertexShader__, __m\_vertexShaderFlat__ und __m\_pixelShader__, __m\_pixelShaderFlat__.</span><span class="sxs-lookup"><span data-stu-id="e3b74-151">In this game sample, the shader objects are __m\_vertexShader__, __m\_vertexShaderFlat__, and __m\_pixelShader__, __m\_pixelShaderFlat__.</span></span>
    * <span data-ttu-id="e3b74-152">Der Vertexshader verarbeitet die Grundtypen und die grundlegende Beleuchtung. Der Pixelshader (auch als Fragmentshader bezeichnet) verarbeitet die Texturen und alle pixelgenauen Effekte.</span><span class="sxs-lookup"><span data-stu-id="e3b74-152">The vertex shader processes the primitives and the basic lighting, and the pixel shader (sometimes called a fragment shader) processes the textures and any per-pixel effects.</span></span>
    * <span data-ttu-id="e3b74-153">Es existieren zwei Versionen dieser Shader (regulär und flach) zum Rendern verschiedener Grundtypen.</span><span class="sxs-lookup"><span data-stu-id="e3b74-153">There are two versions of these shaders (regular and flat) for rendering different primitives.</span></span> <span data-ttu-id="e3b74-154">Die flachen Versionen sind wesentlich einfacher und bieten weder Glanzlichter noch Pixelbeleuchtungseffekte.</span><span class="sxs-lookup"><span data-stu-id="e3b74-154">The reason we have different versions is that the flat versions are much simpler and don't do specular highlights or any per pixel lighting effects.</span></span> <span data-ttu-id="e3b74-155">Sie werden für die Wände verwendet und beschleunigen das Rendern auf Geräten mit geringerer Leistung.</span><span class="sxs-lookup"><span data-stu-id="e3b74-155">These are used for the walls and make rendering faster on lower powered devices.</span></span>

## <a name="gamerendererh"></a><span data-ttu-id="e3b74-156">GameRenderer.h</span><span class="sxs-lookup"><span data-stu-id="e3b74-156">GameRenderer.h</span></span>

<span data-ttu-id="e3b74-157">Betrachten wir nun den Code im Renderer-Klassenobjekt des Spiel und vergleichen ihn mit __Sample3DSceneRenderer.h__ aus der DirectX 11 App-Vorlage.</span><span class="sxs-lookup"><span data-stu-id="e3b74-157">Now let's look at the code in the game sample's renderer class object and compare it with the __Sample3DSceneRenderer.h__ provided in the DirectX 11 App template.</span></span>

```cpp
// Class object handling the rendering of the game
ref class GameRenderer
{
internal:
    GameRenderer(const std::shared_ptr<DX::DeviceResources>& deviceResources);
    
    // Compared with Sample3DSceneRenderer.h in the DirectX 11 App template sample. 
    
    // These methods are present.
    void CreateDeviceDependentResources();
    void CreateWindowSizeDependentResources();
    void ReleaseDeviceDependentResources();
    void Render();

    // Added: Async related methods to prepare 3D game objects for rendering
    concurrency::task<void> CreateGameDeviceResourcesAsync(_In_ Simple3DGame^ game);
    void FinalizeCreateGameDeviceResources();
    concurrency::task<void> LoadLevelResourcesAsync();
    void FinalizeLoadLevelResources();
    // --- end of async related methods section

    // Added: Methods for rendering overlay
    Simple3DGameDX::IGameUIControl^ GameUIControl()  { return m_gameInfoOverlay; };

    DirectX::XMFLOAT2 GameInfoOverlayUpperLeft()
    {
        return DirectX::XMFLOAT2(m_gameInfoOverlayRect.left, m_gameInfoOverlayRect.top);
    };
    DirectX::XMFLOAT2 GameInfoOverlayLowerRight()
    {
        return DirectX::XMFLOAT2(m_gameInfoOverlayRect.right, m_gameInfoOverlayRect.bottom);
    };
    bool GameInfoOverlayVisible() { return m_gameInfoOverlay->Visible(); }
    // --- end of rendering overlay section

    //...
    protected private:
    // Cached pointer to device resources.
    std::shared_ptr<DX::DeviceResources>                m_deviceResources;

    // ...

    // Shader resource objects
    Microsoft::WRL::ComPtr<ID3D11ShaderResourceView>    m_sphereTexture;
    Microsoft::WRL::ComPtr<ID3D11ShaderResourceView>    m_cylinderTexture;
    Microsoft::WRL::ComPtr<ID3D11ShaderResourceView>    m_ceilingTexture;
    Microsoft::WRL::ComPtr<ID3D11ShaderResourceView>    m_floorTexture;
    Microsoft::WRL::ComPtr<ID3D11ShaderResourceView>    m_wallsTexture;

    // Constant Buffers
    Microsoft::WRL::ComPtr<ID3D11Buffer>                m_constantBufferNeverChanges;
    Microsoft::WRL::ComPtr<ID3D11Buffer>                m_constantBufferChangeOnResize;
    Microsoft::WRL::ComPtr<ID3D11Buffer>                m_constantBufferChangesEveryFrame;
    Microsoft::WRL::ComPtr<ID3D11Buffer>                m_constantBufferChangesEveryPrim;

    // Texture sampler
    Microsoft::WRL::ComPtr<ID3D11SamplerState>          m_samplerLinear;

    // Shader objects: Vertex shaders and pixel shaders
    Microsoft::WRL::ComPtr<ID3D11VertexShader>          m_vertexShader;
    Microsoft::WRL::ComPtr<ID3D11VertexShader>          m_vertexShaderFlat;
    Microsoft::WRL::ComPtr<ID3D11PixelShader>           m_pixelShader;
    Microsoft::WRL::ComPtr<ID3D11PixelShader>           m_pixelShaderFlat;
    Microsoft::WRL::ComPtr<ID3D11InputLayout>           m_vertexLayout;
};
```

## <a name="constructor"></a><span data-ttu-id="e3b74-158">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="e3b74-158">Constructor</span></span>

<span data-ttu-id="e3b74-159">Untersuchen wir nun den Code im __Renderer__-Konstruktor des Spiel und vergleichen ihn mit dem Konstruktor __Sample3DSceneRenderer.h__ aus der DirectX 11 App-Vorlage.</span><span class="sxs-lookup"><span data-stu-id="e3b74-159">Next, let's examine the game sample's __GameRenderer__ constructor and compare it with the __Sample3DSceneRenderer__ constructor provided in the DirectX 11 App template.</span></span>

```cpp
// Constructor method of the main rendering class object
GameRenderer::GameRenderer(const std::shared_ptr<DX::DeviceResources>& deviceResources) : //...
{
    // Compared with Sample3DSceneRenderer::Sample3DSceneRenderer in the DirectX 11 App template sample. 
    
    // Added: Create a new GameHud object to rendered text on the top left corner of the screen
    m_gameHud = ref new GameHud(
        deviceResources,
        "Windows platform samples",
        "DirectX first-person game sample"
        );
    //--- end of new GameHud object section
        
    // Added: Game info rendered as an overlay on the top right corner of the screen (eg. Hits, Shots, Time)    
    m_gameInfoOverlay = ref new GameInfoOverlay(deviceResources);
    //--- end of game info rendered as overlay section

    // These methods are present.
    CreateDeviceDependentResources();
    CreateWindowSizeDependentResources();
}
```

## <a name="create-and-load-directx-graphic-resources"></a><span data-ttu-id="e3b74-160">Erstellen und Laden von DirectX-Grafikressourcen</span><span class="sxs-lookup"><span data-stu-id="e3b74-160">Create and load DirectX graphic resources</span></span>

<span data-ttu-id="e3b74-161">Im Spielbeispiel (und in der Vorlage __DirectX 11-App (Universal Windows)__ von Visual Studio) wird das Erstellen und Laden von Spielressourcen mithilfe dieser beiden Methoden implementiert, die vom __GameRenderer__-Konstruktor aufgerufen werden. :</span><span class="sxs-lookup"><span data-stu-id="e3b74-161">In the game sample (and in Visual Studio's __DirectX 11 App (Universal Windows)__ template), creating and loading game resources is implemented using these two methods that are called from __GameRenderer__ constructor:</span></span>

* [__<span data-ttu-id="e3b74-162">CreateDeviceDependentResources</span><span class="sxs-lookup"><span data-stu-id="e3b74-162">CreateDeviceDependentResources</span></span>__](#createdevicedependentresources-method)
* [__<span data-ttu-id="e3b74-163">CreateWindowSizeDependentResources</span><span class="sxs-lookup"><span data-stu-id="e3b74-163">CreateWindowSizeDependentResources</span></span>__](#createwindowsizedependentresources-method)

## <a name="createdevicedependentresources-method"></a><span data-ttu-id="e3b74-164">CreateDeviceDependentResources-Methode</span><span class="sxs-lookup"><span data-stu-id="e3b74-164">CreateDeviceDependentResources method</span></span>

<span data-ttu-id="e3b74-165">In der DirectX 11-App-Vorlage wird diese Methode verwendet, um Vertex- und Pixel-Shader asynchron zu laden, den Shader und den Konstantenpuffer zu erstellen und ein Gittermodell mit Vertices zu erstellen, die Positions- und Farbinformationen enthalten.</span><span class="sxs-lookup"><span data-stu-id="e3b74-165">In the DirectX 11 App template, this method is used to load vertex and pixel shader asynchronously, create the shader and constant buffer, create a mesh with vertices that contain position and color info.</span></span> 

<span data-ttu-id="e3b74-166">Im Spielbeispiel werden diese Operationen der Szenenobjekte stattdessen auf die Methoden [__CreateGameDeviceResourcesAsync__](#creategamedeviceresourcesasync-method) und [__FinalizeCreateGameDeviceResources__](#finalizecreategamedeviceresources-method) aufgeteilt.</span><span class="sxs-lookup"><span data-stu-id="e3b74-166">In the sample game, these operations of the scene objects are instead split among the [__CreateGameDeviceResourcesAsync__](#creategamedeviceresourcesasync-method) and [__FinalizeCreateGameDeviceResources__](#finalizecreategamedeviceresources-method) methods.</span></span> 

<span data-ttu-id="e3b74-167">Was übernimmt diese Methode in diesem Spielbeispiel?</span><span class="sxs-lookup"><span data-stu-id="e3b74-167">For this game sample, what goes into this method?</span></span>

* <span data-ttu-id="e3b74-168">Instanziierte Variablen (__m\_gameResourcesLoaded__ = false und __m\_levelResourcesLoaded__ = false), die angeben, ob Ressourcen vor dem Rendern geladen wurden (da sie asynchron geladen werden).</span><span class="sxs-lookup"><span data-stu-id="e3b74-168">Instantiated variables (__m\_gameResourcesLoaded__ = false and __m\_levelResourcesLoaded__ = false) that indicate whether resources have been loaded before moving forward to render, since we're loading them asynchronously.</span></span> 
* <span data-ttu-id="e3b74-169">Da HUD- und Overlay-Rendering in separaten Klassenobjekten erfolgt, rufen Sie hier die Methoden __GameHud::CreateDeviceDependentResources__ und __GameInfoOverlay::CreateDeviceDependentResources__ auf.</span><span class="sxs-lookup"><span data-stu-id="e3b74-169">Since HUD and overlay rendering are in separate class objects, call __GameHud::CreateDeviceDependentResources__ and __GameInfoOverlay::CreateDeviceDependentResources__ methods here.</span></span>

<span data-ttu-id="e3b74-170">Hier der vollständige Code für __GameRenderer::CreateDeviceDependentResources__.</span><span class="sxs-lookup"><span data-stu-id="e3b74-170">Here's the code for __GameRenderer::CreateDeviceDependentResources__.</span></span>

```cpp
// This method is called in GameRenderer constructor when it's created in GameMain constructor.
void GameRenderer::CreateDeviceDependentResources()
{
    // instantiate variables that indicate if resources were loaded.
    m_gameResourcesLoaded = false;
    m_levelResourcesLoaded = false;

    // game HUD and overlay are design as separate class objects.
    m_gameHud->CreateDeviceDependentResources();
    m_gameInfoOverlay->CreateDeviceDependentResources();
}
```
<span data-ttu-id="e3b74-171">In der folgenden Tabelle sind die Methoden aufgeführt, die zum Erstellen und Laden von Ressourcen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e3b74-171">The table below lists the methods that are used to create and load resources.</span></span> <span data-ttu-id="e3b74-172">__CreateGameDeviceResourcesAsync__ und __FinalizeCreateGameDeviceResources__ wurden im Spielbeispiel hinzugefügt, sodass Ressourcen asynchron geladen werden.</span><span class="sxs-lookup"><span data-stu-id="e3b74-172">__CreateGameDeviceResourcesAsync__ and __FinalizeCreateGameDeviceResources__ are added in the sample game so that resources are loaded asynchronously.</span></span>

|<span data-ttu-id="e3b74-173">Ursprüngliche DirectX11-App-Vorlage</span><span class="sxs-lookup"><span data-stu-id="e3b74-173">Original DirectX 11 App template</span></span>           |<span data-ttu-id="e3b74-174">Spielbeispiel</span><span class="sxs-lookup"><span data-stu-id="e3b74-174">Sample game</span></span>                                                                |
|-------------------------------------------|---------------------------------------------------------------------------|
|<span data-ttu-id="e3b74-175">CreateDeviceDependentResources</span><span class="sxs-lookup"><span data-stu-id="e3b74-175">CreateDeviceDependentResources</span></span>             |<span data-ttu-id="e3b74-176">CreateDeviceDependentResources</span><span class="sxs-lookup"><span data-stu-id="e3b74-176">CreateDeviceDependentResources</span></span>                                             |
|                                           | <span data-ttu-id="e3b74-177">- CreateGameDeviceResourcesAsync (hinzugefügt)</span><span class="sxs-lookup"><span data-stu-id="e3b74-177">- CreateGameDeviceResourcesAsync (Added)</span></span>                                  |
|                                           | <span data-ttu-id="e3b74-178">- FinalizeCreateGameDeviceResources (hinzugefügt)</span><span class="sxs-lookup"><span data-stu-id="e3b74-178">- FinalizeCreateGameDeviceResources (Added)</span></span>                               |
|<span data-ttu-id="e3b74-179">CreateWindowSizeDependentResources</span><span class="sxs-lookup"><span data-stu-id="e3b74-179">CreateWindowSizeDependentResources</span></span>         |<span data-ttu-id="e3b74-180">CreateWindowSizeDependentResources</span><span class="sxs-lookup"><span data-stu-id="e3b74-180">CreateWindowSizeDependentResources</span></span>                                         |

<span data-ttu-id="e3b74-181">Bevor wir uns mit den anderen Methoden beschäftigen, die zum Erstellen und Laden von Ressourcen verwendet werden, erstellen wir zuerst den Renderer und sehen uns an, wie er in die Spielschleife passt.</span><span class="sxs-lookup"><span data-stu-id="e3b74-181">Before diving into the other methods that are used to create and load resources, let's first create the renderer and see how it fits into the game loop.</span></span>

## <a name="create-the-renderer"></a><span data-ttu-id="e3b74-182">Renderer erstellen</span><span class="sxs-lookup"><span data-stu-id="e3b74-182">Create the renderer</span></span>

<span data-ttu-id="e3b74-183">Der __GameRenderer__ wird im __GameMain__-Konstruktor erstellt.</span><span class="sxs-lookup"><span data-stu-id="e3b74-183">The __GameRenderer__ is created in the __GameMain__'s constructor.</span></span> <span data-ttu-id="e3b74-184">Es ruft auch die beiden anderen Methoden auf, [__CreateGameDeviceResourcesAsync__](#creategamedeviceresourcesasync-method) und [__FinalizeCreateGameDeviceResources__](#finalizecreategamedeviceresources-method), die zum Erstellen und Laden von Ressourcen hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="e3b74-184">It also calls the two other methods, [__CreateGameDeviceResourcesAsync__](#creategamedeviceresourcesasync-method) and [__FinalizeCreateGameDeviceResources__](#finalizecreategamedeviceresources-method) that are added to help create and load resources.</span></span>

```cpp

GameMain::GameMain(const std::shared_ptr<DX::DeviceResources>& deviceResources) : // ...
{
    m_deviceResources->RegisterDeviceNotify(this);

    // These methods are used in the DirectX 11 App template to create the class objects used for rendering. 
    // But are replaced in this game sample with GameRenderer as shown below.
    // m_sceneRenderer = std::unique_ptr<Sample3DSceneRenderer>(new Sample3DSceneRenderer(m_deviceResources));
    // m_fpsTextRenderer = std::unique_ptr<SampleFpsTextRenderer>(new SampleFpsTextRenderer(m_deviceResources));
    
    // Creation of GameRenderer
    m_renderer = ref new GameRenderer(m_deviceResources);
    
    //...

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
    
    //...
}
```

## <a name="creategamedeviceresourcesasync-method"></a><span data-ttu-id="e3b74-185">CreateGameDeviceResourcesAsync-Methode</span><span class="sxs-lookup"><span data-stu-id="e3b74-185">CreateGameDeviceResourcesAsync method</span></span>

<span data-ttu-id="e3b74-186">__CreateGameDeviceResourcesAsync__ wird von der Konstruktor-Methode __GameMain__ in der __create\_task__-Schleife aufgerufen, da Spielressourcen asynchron geladen werden.</span><span class="sxs-lookup"><span data-stu-id="e3b74-186">__CreateGameDeviceResourcesAsync__ is called from the __GameMain__ constructor method in the __create\_task__ loop since we're loading game resources asynchronously.</span></span>
        
<span data-ttu-id="e3b74-187">__CreateDeviceResourcesAsync__ ist eine Methode, die als gesonderte Reihe asynchroner Aufgaben ausgeführt wird, um die Spielressourcen zu laden.</span><span class="sxs-lookup"><span data-stu-id="e3b74-187">__CreateDeviceResourcesAsync__ is a method that runs as a separate set of async tasks to load the game resources.</span></span> <span data-ttu-id="e3b74-188">Da sie in einem gesonderten Thread ausgeführt werden soll, kann sie nur auf die Direct3D11-Gerätemethoden (definiert in __ID3D11Device__) und nicht auf die Gerätekontextmethoden (definiert in __ID3D11DeviceContext__) zugreifen, führt also keinerlei Rendering aus.</span><span class="sxs-lookup"><span data-stu-id="e3b74-188">Because it's expected to run on a separate thread, it only has access to the Direct3D 11 device methods (those defined on __ID3D11Device__) and not the device context methods (the methods defined on __ID3D11DeviceContext__), so it does not perform any rendering.</span></span>

<span data-ttu-id="e3b74-189">Die Methode __FinalizeCreateGameDeviceResources__ wird im Hauptthread ausgeführt und kann auf die Direct3D11-Gerätekontextmethoden zugreifen.</span><span class="sxs-lookup"><span data-stu-id="e3b74-189">__FinalizeCreateGameDeviceResources__ method runs on the main thread and does have access to the Direct3D 11 device context methods.</span></span>

<span data-ttu-id="e3b74-190">Prinzip:</span><span class="sxs-lookup"><span data-stu-id="e3b74-190">In principle:</span></span>
* <span data-ttu-id="e3b74-191">Verwenden Sie nur __ID3D11Device__-Methoden in __CreateGameDeviceResourcesAsync__, da diese auf jedem Thread ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="e3b74-191">Use only __ID3D11Device__ methods in __CreateGameDeviceResourcesAsync__ because they are free-threaded, which means that they are able to run on any thread.</span></span> <span data-ttu-id="e3b74-192">Es wird erwartet, dass sie nicht in dem Thread laufen, in dem __GameRenderer__ erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="e3b74-192">It is also expected that they do not run on the same thread as the one __GameRenderer__ was created on.</span></span> 
* <span data-ttu-id="e3b74-193">Verwenden Sie hier keine Methoden in __ID3D11DeviceContext__, da sie in einem einzelnen Thread und in demselben Thread wie __GameRenderer__ ausgeführt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="e3b74-193">Do not use methods in __ID3D11DeviceContext__ here because they need to run on a single thread and on the same thread as __GameRenderer__.</span></span>
* <span data-ttu-id="e3b74-194">Verwenden Sie diese Methode, um Konstantenpuffer zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="e3b74-194">Use this method to create constant buffers.</span></span>
* <span data-ttu-id="e3b74-195">Verwenden Sie diese Methode zum Laden von Texturen (z.B. die DDS-Dateien) und Shaderinformationen (z.B. die CSO-Dateien) in die [Shader](tutorial--assembling-the-rendering-pipeline.md#shaders).</span><span class="sxs-lookup"><span data-stu-id="e3b74-195">Use this method to load textures (like the .dds files) and shader info (like the .cso files) into the [shaders](tutorial--assembling-the-rendering-pipeline.md#shaders).</span></span>

<span data-ttu-id="e3b74-196">Verwendungszweck dieser Methode:</span><span class="sxs-lookup"><span data-stu-id="e3b74-196">This method is used to:</span></span>
* <span data-ttu-id="e3b74-197">Erstellen der 4 [Konstantenpuffer](tutorial--assembling-the-rendering-pipeline.md#buffer): __m\_constantBufferNeverChanges__, __m\_constantBufferChangeOnResize__, __m\_constantBufferChangesEveryFrame__, __m\_constantBufferChangesEveryPrim__</span><span class="sxs-lookup"><span data-stu-id="e3b74-197">Create the 4 [constant buffers](tutorial--assembling-the-rendering-pipeline.md#buffer): __m\_constantBufferNeverChanges__, __m\_constantBufferChangeOnResize__, __m\_constantBufferChangesEveryFrame__, __m\_constantBufferChangesEveryPrim__</span></span>
* <span data-ttu-id="e3b74-198">Erstellen eines [sampler-state](tutorial--assembling-the-rendering-pipeline.md#sampler-state)-Objekts, das Samplinginformationen für eine Textur kapselt</span><span class="sxs-lookup"><span data-stu-id="e3b74-198">Create a [sampler-state](tutorial--assembling-the-rendering-pipeline.md#sampler-state) object that encapsulates sampling information for a texture</span></span>
* <span data-ttu-id="e3b74-199">Erstellen einer Aufgabengruppe, die alle asynchronen Aufgaben enthält, die von der Methode erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="e3b74-199">Create a task group that contains all async tasks created by the method.</span></span> <span data-ttu-id="e3b74-200">Die Methode wartet auf den Abschluss dieser asynchronen Aufgaben und ruft dann __FinalizeCreateGameDeviceResources__ auf.</span><span class="sxs-lookup"><span data-stu-id="e3b74-200">It waits for the completion of all these async tasks, and then calls __FinalizeCreateGameDeviceResources__.</span></span>
* <span data-ttu-id="e3b74-201">Erstellen eines Lademoduls mithilfe von [Basic Loader](tutorial--assembling-the-rendering-pipeline.md#basicloader).</span><span class="sxs-lookup"><span data-stu-id="e3b74-201">Create a loader using [Basic Loader](tutorial--assembling-the-rendering-pipeline.md#basicloader).</span></span> <span data-ttu-id="e3b74-202">Fügen Sie die asynchronen Ladevorgänge des Lademoduls als Aufgaben in die zuvor erstellte Aufgabengruppe ein.</span><span class="sxs-lookup"><span data-stu-id="e3b74-202">Add the loader's async loading operations as tasks into the task group created earlier.</span></span>
* <span data-ttu-id="e3b74-203">Methoden wie __BasicLoader::LoadShaderAsync__ and  __BasicLoader::LoadTextureAsync__ dienen zum Laden von:</span><span class="sxs-lookup"><span data-stu-id="e3b74-203">Methods like __BasicLoader::LoadShaderAsync__ and  __BasicLoader::LoadTextureAsync__ are used to load:</span></span>
    * <span data-ttu-id="e3b74-204">kompilierten Shaderobjekten (VertextShader.cso, VertexShaderFlat.cso, PixelShader.cso, and PixelShaderFlat.cso).</span><span class="sxs-lookup"><span data-stu-id="e3b74-204">compiled shader objects (VertextShader.cso, VertexShaderFlat.cso, PixelShader.cso, and PixelShaderFlat.cso).</span></span> <span data-ttu-id="e3b74-205">Weitere Informationen finden Sie unter [Verschiedene Shader-Dateiformate](tutorial--assembling-the-rendering-pipeline.md#various-shader-file-formats).</span><span class="sxs-lookup"><span data-stu-id="e3b74-205">For more info, go to [Various shader file formats](tutorial--assembling-the-rendering-pipeline.md#various-shader-file-formats).</span></span>
    * <span data-ttu-id="e3b74-206">spielspezifischen Texturen (Assets\\seafloor.dds, metal_texture.dds, cellceiling.dds, cellfloor.dds, cellwall.dds).</span><span class="sxs-lookup"><span data-stu-id="e3b74-206">game specific textures (Assets\\seafloor.dds, metal_texture.dds, cellceiling.dds, cellfloor.dds, cellwall.dds).</span></span>

```cpp
task<void> GameRenderer::CreateGameDeviceResourcesAsync(_In_ Simple3DGame^ game)
{
    // Create the device dependent game resources.
    // Only the d3dDevice is used in this method.  It is expected
    // to not run on the same thread as the GameRenderer was created.
    // Create methods on the d3dDevice are free-threaded and are safe while any methods
    // in the d3dContext should only be used on a single thread and handled
    // in the FinalizeCreateGameDeviceResources method.
    m_game = game;

    auto d3dDevice = m_deviceResources->GetD3DDevice();

    // Define D3D11_BUFFER_DESC.
    // For API ref, go to: https://msdn.microsoft.com/library/windows/desktop/ff476092.aspx
    D3D11_BUFFER_DESC bd;
    ZeroMemory(&bd, sizeof(bd));
    
    bd.Usage = D3D11_USAGE_DEFAULT;
    // ...
    
    // Create the constant buffers: m_constantBufferNeverChanges, m_constantBufferChangeOnResize,
    // m_constantBufferChangesEveryFrame, m_constantBufferChangesEveryPrim
    // CreateBuffer is used to create one of these buffers: vertex buffer, index buffer, or 
    // shader-constant buffer. For CreateBuffer API ref info, go to: https://msdn.microsoft.com/library/windows/desktop/ff476501.aspx
    
    DX::ThrowIfFailed(
        d3dDevice->CreateBuffer(&bd, nullptr, &m_constantBufferNeverChanges) 
        );
    // ...
    
    // Define D3D11_SAMPLER_DESC. For API ref, go to: https://msdn.microsoft.com/library/windows/desktop/ff476207.aspx
    D3D11_SAMPLER_DESC sampDesc;

    // ZeroMemory fills a block of memory with zeros. 
    // For API ref, go to: https://msdn.microsoft.com/en-us/library/windows/desktop/aa366920(v=vs.85).aspx
    ZeroMemory(&sampDesc, sizeof(sampDesc));

    sampDesc.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;
    sampDesc.AddressU = D3D11_TEXTURE_ADDRESS_WRAP;
    sampDesc.AddressV = D3D11_TEXTURE_ADDRESS_WRAP;
    // ...
    
    // Create a sampler-state object that encapsulates sampling information for a texture.
    // The sampler-state interface holds a description for sampler state that you can bind to any 
    // shader stage of the pipeline for reference by texture sample operations.
    DX::ThrowIfFailed(
        d3dDevice->CreateSamplerState(&sampDesc, &m_samplerLinear)
        );

    // Start the async tasks to load the shaders and textures (resources).
    
    // Load compiled shader objects (VertextShader.cso, VertexShaderFlat.cso, PixelShader.cso, and PixelShaderFlat.cso).
    // The BasicLoader class is used to convert and load common graphics resources, such as meshes, textures, 
    // and various shader objects into the constant buffers. 
    // For more info, go to: https://docs.microsoft.com/windows/uwp/gaming/complete-code-for-basicloader
    BasicLoader^ loader = ref new BasicLoader(d3dDevice);

    std::vector<task<void>> tasks;

    uint32 numElements = ARRAYSIZE(PNTVertexLayout);

    // Load shaders asynchronously with the shader and pixel data using the BasicLoader::LoadShaderAsync method
    // Push these method calls into a list of tasks
    tasks.push_back(loader->LoadShaderAsync("VertexShader.cso", PNTVertexLayout, numElements, &m_vertexShader, &m_vertexLayout));
    tasks.push_back(loader->LoadShaderAsync("VertexShaderFlat.cso", nullptr, numElements, &m_vertexShaderFlat, nullptr));
    tasks.push_back(loader->LoadShaderAsync("PixelShader.cso", &m_pixelShader));
    tasks.push_back(loader->LoadShaderAsync("PixelShaderFlat.cso", &m_pixelShaderFlat));

    // Make sure the previous versions are set to NULL before any of the textures are loaded.
    m_sphereTexture = nullptr;
    // ...

    // Load Game specific textures (Assets\\seafloor.dds, metal_texture.dds, cellceiling.dds, cellfloor.dds, cellwall.dds).
    // Push these method calls also into a list of tasks
    tasks.push_back(loader->LoadTextureAsync("Assets\\seafloor.dds", nullptr, &m_sphereTexture));
    // ...
    
    tasks.push_back(create_task([]()
    {
        // Simulate loading additional resources by introducing a delay.
        wait(GameConstants::InitialLoadingDelay);
    }));

    // Returns when all the async tasks for loading the shader and texture assets have completed.
    return when_all(tasks.begin(), tasks.end());
}
```

## <a name="finalizecreategamedeviceresources-method"></a><span data-ttu-id="e3b74-207">FinalizeCreateGameDeviceResources-Methode</span><span class="sxs-lookup"><span data-stu-id="e3b74-207">FinalizeCreateGameDeviceResources method</span></span>

<span data-ttu-id="e3b74-208">Die Methode __FinalizeCreateGameDeviceResources__ wird aufgerufen, nachdem alle Aufgaben zum Laden von Ressourcen in der Methode __CreateGameDeviceResourcesAsync__ abgeschlossen sind.</span><span class="sxs-lookup"><span data-stu-id="e3b74-208">__FinalizeCreateGameDeviceResources__ method is called after all the load resources tasks that are in the __CreateGameDeviceResourcesAsync__ method completes.</span></span> 

* <span data-ttu-id="e3b74-209">Initialisieren Sie constantBufferNeverChanges mit den Beleuchtungspositionen und der Farbe.</span><span class="sxs-lookup"><span data-stu-id="e3b74-209">Initialize constantBufferNeverChanges with the light positions and color.</span></span> <span data-ttu-id="e3b74-210">Laden Sie die Anfangsdaten mit einem Gerätekontext-Methodenaufruf von __ID3D11DeviceContext :: UpdateSubresource__ in die Konstantenpuffer.</span><span class="sxs-lookup"><span data-stu-id="e3b74-210">Loads the initial data into the constant buffers with a device context method call to __ID3D11DeviceContext::UpdateSubresource__.</span></span>
* <span data-ttu-id="e3b74-211">Da asynchron geladene Ressourcen vollständig geladen wurden, ist es an der Zeit, sie mit den entsprechenden Spielobjekten zu verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="e3b74-211">Since asynchronously loaded resources have completed loading, it's time to associate them with the appropriate game objects.</span></span>
* <span data-ttu-id="e3b74-212">Erstellen Sie für jedes Spielobjekt das Gittermodell und das Material mit den Texturen, die geladen wurden.</span><span class="sxs-lookup"><span data-stu-id="e3b74-212">For each game object, create the mesh and the material using the textures that have been loaded.</span></span> <span data-ttu-id="e3b74-213">Dann ordnen Sie Gittermodell und Material den Spielobjekten zu.</span><span class="sxs-lookup"><span data-stu-id="e3b74-213">Then associate the mesh and material to the game object.</span></span>
* <span data-ttu-id="e3b74-214">Die Textur für die Zielspielobjekte (die aus konzentrischen farbigen Ringen besteht, oben mit einem numerischen Wert) wird nicht aus einer Texturdatei geladen.</span><span class="sxs-lookup"><span data-stu-id="e3b74-214">For the targets game object, the texture which is composed of concentric colored rings, with a numeric value on the top, is not loaded from a texture file.</span></span> <span data-ttu-id="e3b74-215">Sie wird stattdessen mithilfe des Codes in __TargetTexture.cpp__ generiert.</span><span class="sxs-lookup"><span data-stu-id="e3b74-215">Instead, it's procedurally generated using the code in __TargetTexture.cpp__.</span></span> <span data-ttu-id="e3b74-216">Die Klasse __TargetTexture__ erstellt die erforderlichen Ressourcen, um die Textur zur Initialisierungszeit in eine Off-Screen-Ressource zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="e3b74-216">The __TargetTexture__ class creates the necessary resources to draw the texture into an off screen resource at initialization time.</span></span> <span data-ttu-id="e3b74-217">Die resultierende Textur wird dann den entsprechenden Zielspielobjekten zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="e3b74-217">The resulting texture is then associated with the appropriate target game objects.</span></span>

<span data-ttu-id="e3b74-218">__FinalizeCreateGameDeviceResources__ und [__CreateWindowSizeDependentResources__](#createwindowsizedependentresource-method) teilen übereinstimmende Teile des Codes für folgende Aufgaben:</span><span class="sxs-lookup"><span data-stu-id="e3b74-218">__FinalizeCreateGameDeviceResources__ and [__CreateWindowSizeDependentResources__](#createwindowsizedependentresource-method) share similar portions of code for these:</span></span>
* <span data-ttu-id="e3b74-219">Verwenden Sie __SetProjParams__, um sicherzustellen, dass die Kamera mit der richtigen Projektionsmatrix arbeitet.</span><span class="sxs-lookup"><span data-stu-id="e3b74-219">Use __SetProjParams__ to ensure that the camera has the right projection matrix.</span></span> <span data-ttu-id="e3b74-220">Weitere Informationen finden Sie unter [Kamera und Koordinatenraum](tutorial--assembling-the-rendering-pipeline.md#camera-and-coordinate-space).</span><span class="sxs-lookup"><span data-stu-id="e3b74-220">For more info, go to [Camera and coordinate space](tutorial--assembling-the-rendering-pipeline.md#camera-and-coordinate-space).</span></span>
* <span data-ttu-id="e3b74-221">Behandeln Sie die Rotation des Bildschirms durch Rechtsmultiplikation der 3D-Rotationsmatrix mit der Projektionsmatrix der Kamera.</span><span class="sxs-lookup"><span data-stu-id="e3b74-221">Handle screen rotation by post multiplying the 3D rotation matrix to the camera's projection matrix.</span></span> <span data-ttu-id="e3b74-222">Aktualisieren Sie dann den __ConstantBufferChangeOnResize__-Konstantenpuffer mit der resultieRendern Projektionsmatrix.</span><span class="sxs-lookup"><span data-stu-id="e3b74-222">Then update the __ConstantBufferChangeOnResize__ constant buffer with the resulting projection matrix.</span></span>
* <span data-ttu-id="e3b74-223">Legen Sie die __boolesche__ globale Variable __m\_gameResourcesLoaded__ fest, um anzugeben, dass die Ressourcen nun in den Puffer geladen sind, bereit für den nächsten Schritt.</span><span class="sxs-lookup"><span data-stu-id="e3b74-223">Set the __m\_gameResourcesLoaded__ __Boolean__ global variable to indicate that the resources are now loaded in the buffers, ready for the next step.</span></span> <span data-ttu-id="e3b74-224">Wir haben diese Variable zu Beginn in der __GameRenderer__-Konstruktormethode über die __GameRenderer::CreateDeviceDependentResources__-Methode mit __FALSE__ initialisiert.</span><span class="sxs-lookup"><span data-stu-id="e3b74-224">Recall that we first initialized this variable as __FALSE__ in the __GameRenderer__'s constructor method, through the __GameRenderer::CreateDeviceDependentResources__ method.</span></span> 
* <span data-ttu-id="e3b74-225">Wenn __m\_gameResourcesLoaded__ den Wert __TRUE__ erhält, kann das Rendern der Szenenobjekte stattfinden.</span><span class="sxs-lookup"><span data-stu-id="e3b74-225">When this __m\_gameResourcesLoaded__ is __TRUE__, rendering of the scene objects can take place.</span></span> <span data-ttu-id="e3b74-226">Dies wurde erläutert im Artikel __Rendering-Framework I: Einführung in das Rendering__ in Verbindung mit der Methode [__GameRenderer::Render__](tutorial--assembling-the-rendering-pipeline.md#gamerendererrender-method) bereits erläutert.</span><span class="sxs-lookup"><span data-stu-id="e3b74-226">This was covered in the __Rendering framework I: Intro to rendering__ article, under [__GameRenderer::Render method__](tutorial--assembling-the-rendering-pipeline.md#gamerendererrender-method).</span></span>

```cpp
// When creating this sample game using the DirectX 11 App template, this method needs to be created.
// This new method is called from GameMain constructor in the .then loop.
// Make sure the 2D rendering is occurring on the same thread as the main rendering.
// Note: Helper class .h and .cpp files used in this method are located in the SharedContent/cpp/GameContent folder
void GameRenderer::FinalizeCreateGameDeviceResources()
{
    // All asynchronously loaded resources have completed loading.
    // Now associate all the resources with the appropriate game objects.
    // This method is expected to run in the same thread as the GameRenderer
    // was created. All work will happen behind the "Loading ..." screen after the
    // main loop has been entered.

    // Initialize constantBufferNeverChanges with the light positions and color.
    // These are handled here to ensure that the d3dContext is only
    // used in one thread.

    auto d3dDevice = m_deviceResources->GetD3DDevice();
    ConstantBufferNeverChanges constantBufferNeverChanges;
    constantBufferNeverChanges.lightPosition[0] = XMFLOAT4( 3.5f, 2.5f,  5.5f, 1.0f);
    // ...
    constantBufferNeverChanges.lightColor = XMFLOAT4(0.25f, 0.25f, 0.25f, 1.0f);

    // CPU copies data from memory (constantBufferNeverChanges) to a subresource 
    // created in non-mappable memory (m_constantBufferNeverChanges) which was created in the earlier 
    // CreateGameDeviceResourcesAsync method. For UpdateSubresource API ref info, 
    // go to: https://msdn.microsoft.com/library/windows/desktop/ff476486.aspx
    // To learn more about what a subresource is, go to:
    // https://msdn.microsoft.com/library/windows/desktop/ff476901.aspx

    m_deviceResources->GetD3DDeviceContext()->UpdateSubresource(
        m_constantBufferNeverChanges.Get(),
        0,
        nullptr,
        &constantBufferNeverChanges,
        0,
        0
        );

    // For the objects that function as targets, they have two unique generated textures.
    // One version is used to show that they have never been hit and the other is 
    // used to show that they have been hit.
    // TargetTexture is a helper class to procedurally generate textures for game
    // targets. The class creates the necessary resources to draw the texture into 
    // an off screen resource at initialization time.

    TargetTexture^ textureGenerator = ref new TargetTexture(
        d3dDevice,
        m_deviceResources->GetD2DFactory(),
        m_deviceResources->GetDWriteFactory(),
        m_deviceResources->GetD2DDeviceContext()
        );

    // CylinderMesh is a class derived from MeshObject and creates a ID3D11Buffer of
    // vertices and indices to represent a canonical cylinder (capped at
    // both ends) that is positioned at the origin with a radius of 1.0,
    // a height of 1.0 and with its axis in the +Z direction.
    // In the game sample, there are various types of mesh types:
    // CylinderMesh (vertical rods), SphereMesh (balls that the player shoots), 
    // FaceMesh (target objects), and WorldMesh (Floors and ceilings that define the enclosed area)

    MeshObject^ cylinderMesh = ref new CylinderMesh(d3dDevice, 26);
    // ...

    // The Material class maintains the properties that represent how an object will
    // look when it is rendered.  This includes the color of the object, the
    // texture used to render the object, and the vertex and pixel shader that
    // should be used for rendering.

    Material^ cylinderMaterial = ref new Material(
        XMFLOAT4(0.8f, 0.8f, 0.8f, .5f),
        XMFLOAT4(0.8f, 0.8f, 0.8f, .5f),
        XMFLOAT4(1.0f, 1.0f, 1.0f, 1.0f),
        15.0f,
        m_cylinderTexture.Get(),
        m_vertexShader.Get(),
        m_pixelShader.Get()
        );

    // ...
    auto objects = m_game->RenderObjects();

    // Attach the textures to the appropriate game objects.
    // We'll loop through all the objects that need to be rendered.
    for (auto object = objects.begin(); object != objects.end(); object++)
    {

        if ((*object)->TargetId() == GameConstants::WorldFloorId)
        {
            // Assign a normal material for the floor object.
            // This normal material uses the floor texture (cellfloor.dds) that was loaded asynchronously from
            // the Assets folder using BasicLoader::LoadTextureAsync method in the earlier 
            // CreateGameDeviceResourcesAsync loop

            (*object)->NormalMaterial(
                ref new Material(
                    XMFLOAT4(0.5f, 0.5f, 0.5f, 1.0f),
                    XMFLOAT4(0.8f, 0.8f, 0.8f, 1.0f),
                    XMFLOAT4(0.3f, 0.3f, 0.3f, 1.0f),
                    150.0f,
                    m_floorTexture.Get(),
                    m_vertexShaderFlat.Get(),
                    m_pixelShaderFlat.Get()
                    )
                );
            // Creates a mesh object called WorldFloorMesh and assign it to the floor object.
            (*object)->Mesh(ref new WorldFloorMesh(d3dDevice));
        }
        // ...
        else if (Cylinder^ cylinder = dynamic_cast<Cylinder^>(*object))
        {
            cylinder->Mesh(cylinderMesh);
            cylinder->NormalMaterial(cylinderMaterial);
        }
        else if (Face^ target = dynamic_cast<Face^>(*object))
        {
            const int bufferLength = 16;
            char16 str[bufferLength];
            int len = swprintf_s(str, bufferLength, L"%d", target->TargetId());
            Platform::String^ string = ref new Platform::String(str, len);

            ComPtr<ID3D11ShaderResourceView> texture;
            textureGenerator->CreateTextureResourceView(string, &texture);
            target->NormalMaterial(
                ref new Material(
                    XMFLOAT4(0.8f, 0.8f, 0.8f, 0.5f),
                    XMFLOAT4(0.8f, 0.8f, 0.8f, 0.5f),
                    XMFLOAT4(0.3f, 0.3f, 0.3f, 1.0f),
                    5.0f,
                    texture.Get(),
                    m_vertexShader.Get(),
                    m_pixelShader.Get()
                    )
                );

            textureGenerator->CreateHitTextureResourceView(string, &texture);
            target->HitMaterial(
                ref new Material(
                    XMFLOAT4(0.8f, 0.8f, 0.8f, 0.5f),
                    XMFLOAT4(0.8f, 0.8f, 0.8f, 0.5f),
                    XMFLOAT4(0.3f, 0.3f, 0.3f, 1.0f),
                    5.0f,
                    texture.Get(),
                    m_vertexShader.Get(),
                    m_pixelShader.Get()
                    )
                );

            target->Mesh(targetMesh);
        }
        // ...
    }


    // The SetProjParams method calculates the projection matrix based on input params and
    // ensures that the camera has been initialized with the right projection
    // matrix.  
    // The camera is not created at the time the first window resize event occurs.

    auto renderTargetSize = m_deviceResources->GetRenderTargetSize();
    m_game->GameCamera()->SetProjParams(
        XM_PI / 2,
        renderTargetSize.Width / renderTargetSize.Height,
        0.01f,
        100.0f
        );

    // Make sure that the correct projection matrix is set in the ConstantBufferChangeOnResize buffer.

    // Get the 3D rotation transform matrix. We are handling screen rotations directly to eliminate an unaligned 
    // fullscreen copy. So it is necessary to post multiply the 3D rotation matrix to the camera's projection matrix
    // to get the projection matrix that we need.

    auto orientation = m_deviceResources->GetOrientationTransform3D();

    ConstantBufferChangeOnResize changesOnResize;

    // The matrices are transposed due to the shader code expecting the matrices in the opposite
    // row/column order from the DirectX math library.

    // XMStoreFloat4x4 takes a matrix and writes the components out to sixteen single-precision floating-point values at the given address. 
    // The most significant component of the first row vector is written to the first four bytes of the address, 
    // followed by the second most significant component of the first row, and so on. The second row is then written out in a 
    // like manner to memory beginning at byte 16, followed by the third row to memory beginning at byte 32, and finally 
    // the fourth row to memory beginning at byte 48. For more API ref info, go to: 
    // https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.storing.xmstorefloat4x4.aspx

    XMStoreFloat4x4(
        &changesOnResize.projection,
        XMMatrixMultiply(
            XMMatrixTranspose(m_game->GameCamera()->Projection()),
            XMMatrixTranspose(XMLoadFloat4x4(&orientation))
            )
        );

    // UpdateSubresource method instructs CPU to copy data from memory (changesOnResize) to a subresource 
    // created in non-mappable memory (m_constantBufferChangeOnResize ) which was created in the earlier 
    // CreateGameDeviceResourcesAsync method.

    m_deviceResources->GetD3DDeviceContext()->UpdateSubresource(
        m_constantBufferChangeOnResize.Get(),
        0,
        nullptr,
        &changesOnResize,
        0,
        0
        );

    // Finally we set the m_gameResourcesLoaded as TRUE, so we can start rendering.
    m_gameResourcesLoaded = true;
}
```

## <a name="createwindowsizedependentresource-method"></a><span data-ttu-id="e3b74-227">CreateWindowSizeDependentResource-Methode</span><span class="sxs-lookup"><span data-stu-id="e3b74-227">CreateWindowSizeDependentResource method</span></span>

<span data-ttu-id="e3b74-228">CreateWindowSizeDependentResources-Methoden werden jedes Mal aufgerufen, wenn sich Fenstergröße, Ausrichtung, Stereorendering oder die Auflösung ändert.</span><span class="sxs-lookup"><span data-stu-id="e3b74-228">CreateWindowSizeDependentResources methods are called every time the window size, orientation, stereo-enabled rendering, or resolution changes.</span></span> <span data-ttu-id="e3b74-229">Im Spielbeispiel wird die Projektionsmatrix in __ConstantBufferChangeOnResize__aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="e3b74-229">In the sample game, it updates the projection matrix in __ConstantBufferChangeOnResize__.</span></span>

<span data-ttu-id="e3b74-230">Fenstergrößenressourcen werden auf folgende Weise aktualisiert:</span><span class="sxs-lookup"><span data-stu-id="e3b74-230">Window size resources are updated in this manner:</span></span> 
* <span data-ttu-id="e3b74-231">Das App-Framework erhält eines von mehreren möglichen Ereignissen, die auf eine Änderung des Fensterstatus hinweisen.</span><span class="sxs-lookup"><span data-stu-id="e3b74-231">The App framework gets one of several possible events indicating a change in the window state.</span></span> 
* <span data-ttu-id="e3b74-232">Die Hauptspielschleife wird dann über das Ereignis informiert und ruft __CreateWindowSizeDependentResources__ in der Instanz der Hauptklasse (__GameMain__) auf, die dann die __CreateWindowSizeDependentResources__-Implementierung in der Spielrendererklasse (__GameRenderer__) aufruft.</span><span class="sxs-lookup"><span data-stu-id="e3b74-232">Your main game loop is then informed about the event and calls __CreateWindowSizeDependentResources__ on the main class (__GameMain__) instance, which then calls the __CreateWindowSizeDependentResources__ implementation in the game renderer (__GameRenderer__) class.</span></span>
* <span data-ttu-id="e3b74-233">Die vorrangige Aufgabe dieser Methode ist die Sicherstellung, dass die visuellen Elemente aufgrund einer Änderung der Fenstereigenschaften nicht verwechselt oder ungültig werden.</span><span class="sxs-lookup"><span data-stu-id="e3b74-233">The primary job of this method is to make sure the visuals don't become confused or invalid because of a change in window properties.</span></span>

<span data-ttu-id="e3b74-234">Für dieses Spielbeispiel sind mehrere Methodenaufrufe mit der Methode [__FinalizeCreateGameDeviceResources__](#finalizecreategamedeviceresources-method) identisch.</span><span class="sxs-lookup"><span data-stu-id="e3b74-234">For this game sample, a number of method calls are the same as the [__FinalizeCreateGameDeviceResources__](#finalizecreategamedeviceresources-method) method.</span></span> <span data-ttu-id="e3b74-235">Eine Erläuterung des Codes finden Sie im vorherigen Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="e3b74-235">For code walkthrough, go to the previous section.</span></span>

<span data-ttu-id="e3b74-236">Die Anpassungen für die HUD- und Overlay-Fenstergröße des Spiels werden unter [Hinzufügen einer Benutzerschnittstelle](#tutorial--adding-a-user-interface) behandelt.</span><span class="sxs-lookup"><span data-stu-id="e3b74-236">The game HUD and overlay window size rendering adjustments is covered under [Add a user interface](#tutorial--adding-a-user-interface).</span></span>

```cpp
// Initializes view parameters when the window size changes.
void GameRenderer::CreateWindowSizeDependentResources()
{

    // Game HUD and overlay window size rendering adjustments are done here
    // but they'll be covered in the UI section instead.

    m_gameHud->CreateWindowSizeDependentResources();

    // ...

    auto d3dContext = m_deviceResources->GetD3DDeviceContext();
    // In Sample3DSceneRenderer::CreateWindowSizeDependentResources, we had:
    // Size outputSize = m_deviceResources->GetOutputSize();

    auto renderTargetSize = m_deviceResources->GetRenderTargetSize();

    // ...

    m_gameInfoOverlay->CreateWindowSizeDependentResources(m_gameInfoOverlaySize);

    if (m_game != nullptr)
    {
        // Similar operations as the last section of FinalizeCreateGameDeviceResources method
        m_game->GameCamera()->SetProjParams(
            XM_PI / 2, renderTargetSize.Width / renderTargetSize.Height,
            0.01f,
            100.0f
            );

        XMFLOAT4X4 orientation = m_deviceResources->GetOrientationTransform3D();

        ConstantBufferChangeOnResize changesOnResize;
        XMStoreFloat4x4(
            &changesOnResize.projection,
            XMMatrixMultiply(
                XMMatrixTranspose(m_game->GameCamera()->Projection()),
                XMMatrixTranspose(XMLoadFloat4x4(&orientation))
                )
            );

        d3dContext->UpdateSubresource(
            m_constantBufferChangeOnResize.Get(),
            0,
            nullptr,
            &changesOnResize,
            0,
            0
            );
    }
}
```

## <a name="next-steps"></a><span data-ttu-id="e3b74-237">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="e3b74-237">Next steps</span></span>

<span data-ttu-id="e3b74-238">Dies war der grundlegende Prozess zur Implementierung des Rendering-Frameworks für die Grafik eines Spiels.</span><span class="sxs-lookup"><span data-stu-id="e3b74-238">This is the basic process for implementing the graphics rendering framework of a game.</span></span> <span data-ttu-id="e3b74-239">Je größer Ihr Spiel ist, desto mehr Abstraktionen müssten Sie implementieren, um Hierarchien von Objekttypen und Animationsverhalten zu handhaben.</span><span class="sxs-lookup"><span data-stu-id="e3b74-239">The larger your game, the more abstractions you would have to put in place to handle hierarchies of object types and animation behaviors.</span></span> <span data-ttu-id="e3b74-240">Sie müssen komplexere Methoden zum Laden und Verwalten von Assets wie Gittermodelle und Texturen implementieren.</span><span class="sxs-lookup"><span data-stu-id="e3b74-240">You need to implement more complex methods for loading and managing assets such as meshes and textures.</span></span> <span data-ttu-id="e3b74-241">Als Nächstes wird das [Hinzufügen einer Benutzeroberfläche](tutorial--adding-a-user-interface.md) erläutert.</span><span class="sxs-lookup"><span data-stu-id="e3b74-241">Next, let's learn how to [add a user interface](tutorial--adding-a-user-interface.md).</span></span>