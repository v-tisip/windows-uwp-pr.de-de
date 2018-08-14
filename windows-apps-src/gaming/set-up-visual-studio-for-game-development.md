---
author: mtoepke
title: Visual Studio-Tools für die Spieleprogrammierung
description: Sie erhalten eine Übersicht über spezielle DirectX-Tools, die unter Visual Studio verfügbar sind.
ms.assetid: 43137bfc-7876-70e0-515c-4722f68bd064
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Spiele, Visual Studio, Tools, DirectX
ms.openlocfilehash: 5f5c1ef45dd476565d302ef10f8d47ab2b819993
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: MT
ms.contentlocale: de-DE
ms.locfileid: "233672"
---
# <a name="visual-studio-tools-for-game-programming"></a><span data-ttu-id="21409-104">Visual Studio-Tools für die Spieleprogrammierung</span><span class="sxs-lookup"><span data-stu-id="21409-104">Visual Studio tools for game programming</span></span>


<span data-ttu-id="21409-105">\[ Aktualisiert für UWP-Apps unter Windows 10.</span><span class="sxs-lookup"><span data-stu-id="21409-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="21409-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="21409-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

**<span data-ttu-id="21409-107">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="21409-107">Summary</span></span>**

-   [<span data-ttu-id="21409-108">Erstellen eines DirectX-Spieleprojekts aus einer Vorlage</span><span class="sxs-lookup"><span data-stu-id="21409-108">Create a DirectX game project from a template</span></span>](user-interface.md)
-   <span data-ttu-id="21409-109">Visual Studio-Tools für die Programmierung von DirectX-Spielen</span><span class="sxs-lookup"><span data-stu-id="21409-109">Visual Studio tools for DirectX game programming</span></span>


<span data-ttu-id="21409-110">Wenn Sie Visual Studio Ultimate zum Entwickeln von DirectX-Apps verwenden, können Sie zusätzliche Tools zum Erstellen, Bearbeiten, Anzeigen in der Vorschau und Exportieren von Bild-, Modell- und Shaderressourcen nutzen.</span><span class="sxs-lookup"><span data-stu-id="21409-110">If you use Visual Studio Ultimate to develop DirectX apps, there are additional tools available for creating, editing, previewing, and exporting image, model, and shader resources.</span></span> <span data-ttu-id="21409-111">Außerdem sind Tools verfügbar, mit denen Sie Ressourcen zur Erstellungszeit konvertieren und DirectX-Grafikcode debuggen können.</span><span class="sxs-lookup"><span data-stu-id="21409-111">There are also tools that you can use to convert resources at build time and debug DirectX graphics code.</span></span>

<span data-ttu-id="21409-112">Dieses Thema enthält eine Übersicht über diese Grafiktools.</span><span class="sxs-lookup"><span data-stu-id="21409-112">This topic gives an overview of these graphics tools.</span></span>

## <a name="image-editor"></a><span data-ttu-id="21409-113">Grafik-Editor</span><span class="sxs-lookup"><span data-stu-id="21409-113">Image Editor</span></span>


<span data-ttu-id="21409-114">Nutzen Sie den Grafik-Editor zum Arbeiten mit den Arten von umfassenden Textur- und Bildformaten, die von DirectX verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="21409-114">Use the Image Editor to work with the kinds of rich texture and image formats that DirectX uses.</span></span> <span data-ttu-id="21409-115">Der Grafik-Editor unterstützt die folgenden Formate:</span><span class="sxs-lookup"><span data-stu-id="21409-115">The Image Editor supports the following formats.</span></span>

-   <span data-ttu-id="21409-116">PNG</span><span class="sxs-lookup"><span data-stu-id="21409-116">.png</span></span>
-   <span data-ttu-id="21409-117">JPG, JPEG, JPE, JFIF</span><span class="sxs-lookup"><span data-stu-id="21409-117">.jpg, .jpeg, .jpe, .jfif</span></span>
-   <span data-ttu-id="21409-118">DDS</span><span class="sxs-lookup"><span data-stu-id="21409-118">.dds</span></span>
-   <span data-ttu-id="21409-119">GIF</span><span class="sxs-lookup"><span data-stu-id="21409-119">.gif</span></span>
-   <span data-ttu-id="21409-120">BMP</span><span class="sxs-lookup"><span data-stu-id="21409-120">.bmp</span></span>
-   <span data-ttu-id="21409-121">DIB</span><span class="sxs-lookup"><span data-stu-id="21409-121">.dib</span></span>
-   <span data-ttu-id="21409-122">TIF, TIFF</span><span class="sxs-lookup"><span data-stu-id="21409-122">.tif, .tiff</span></span>
-   <span data-ttu-id="21409-123">TGA</span><span class="sxs-lookup"><span data-stu-id="21409-123">.tga</span></span>

<span data-ttu-id="21409-124">Erstellen Sie [Buildanpassungsdateien](#build-customizations-for-3d-assets), um diese Formate zur Buildzeit in DDS-Dateien zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="21409-124">Create [build customization files](#build-customizations-for-3d-assets) to convert these to .dds files at build time.</span></span>

<span data-ttu-id="21409-125">Weitere Informationen finden Sie unter [Arbeiten mit Texturen und Bildern](https://msdn.microsoft.com/library/windows/apps/hh873119.aspx).</span><span class="sxs-lookup"><span data-stu-id="21409-125">For more information, see [Working with Textures and Images](https://msdn.microsoft.com/library/windows/apps/hh873119.aspx).</span></span>

> <span data-ttu-id="21409-126">**Hinweis**: Der Grafik-Editor ist nicht als Ersatz für eine Bildbearbeitungs-App mit vollem Funktionsumfang gedacht, aber für viele einfache Anzeige- und Bearbeitungsfälle geeignet.</span><span class="sxs-lookup"><span data-stu-id="21409-126">**Note**  The Image Editor is not intended to be a replacement for a full feature image editing app, but is appropriate for many simple viewing and editing scenarios.</span></span>

 

## <a name="model-editor"></a><span data-ttu-id="21409-127">Modell-Editor</span><span class="sxs-lookup"><span data-stu-id="21409-127">Model Editor</span></span>


<span data-ttu-id="21409-128">Sie können den Modell-Editor verwenden, um grundlegende 3D-Modelle ganz neu zu erstellen oder um komplexere 3D-Modelle aus umfassenden 3D-Modelliertools anzuzeigen oder zu ändern.</span><span class="sxs-lookup"><span data-stu-id="21409-128">You can use the Model Editor to create basic 3D models from scratch, or to view and modify more-complex 3D models from full-featured 3D modeling tools.</span></span> <span data-ttu-id="21409-129">Der Modell-Editor unterstützt mehrere 3D-Modellformate, die bei der Entwicklung von DirectX-Apps verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="21409-129">The Model Editor supports several 3D model formats that are used in DirectX app development.</span></span> <span data-ttu-id="21409-130">Sie können [Buildanpassungsdateien](#build-customizations-for-3d-assets) erstellen, um diese Formate zur Buildzeit in CMO-Dateien zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="21409-130">You can create [build customization files](#build-customizations-for-3d-assets) to convert these to .cmo files at build time.</span></span>

-   <span data-ttu-id="21409-131">FBX</span><span class="sxs-lookup"><span data-stu-id="21409-131">.fbx</span></span>
-   <span data-ttu-id="21409-132">DAE</span><span class="sxs-lookup"><span data-stu-id="21409-132">.dae</span></span>
-   <span data-ttu-id="21409-133">OBJ</span><span class="sxs-lookup"><span data-stu-id="21409-133">.obj</span></span>

<span data-ttu-id="21409-134">Dies ist ein Screenshot eines Modells im Editor, auf das Beleuchtungsfunktionen angewendet wurden.</span><span class="sxs-lookup"><span data-stu-id="21409-134">Here's a screenshot of a model in the editor with lighting applied.</span></span>

![Teekanne](images/modeleditor.png)

<span data-ttu-id="21409-136">Weitere Informationen finden Sie unter [Arbeiten mit 3D-Modellen](https://msdn.microsoft.com/library/windows/apps/hh873114.aspx).</span><span class="sxs-lookup"><span data-stu-id="21409-136">For more information, see [Working with 3-D Models](https://msdn.microsoft.com/library/windows/apps/hh873114.aspx).</span></span>

> <span data-ttu-id="21409-137">**Hinweis**: Der Modell-Editor ist nicht als Ersatz für eine Modellbearbeitungs-App mit vollem Funktionsumfang gedacht, aber für viele einfache Anzeige- und Bearbeitungsfälle geeignet.</span><span class="sxs-lookup"><span data-stu-id="21409-137">**Note**  The Model Editor is not intended to be a replacement for a full feature model editing app, but is appropriate for many simple viewing and editing scenarios.</span></span>

 

## <a name="shader-designer"></a><span data-ttu-id="21409-138">Shader-Designer</span><span class="sxs-lookup"><span data-stu-id="21409-138">Shader Designer</span></span>


<span data-ttu-id="21409-139">Verwenden Sie den Shader-Designer zum Erstellen benutzerdefinierter visueller Effekte für das Spiel oder die App, auch wenn Sie nicht mit der HLSL-Programmierung vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="21409-139">Use the Shader Designer to create custom visual effects for your game or app even if you don't know HLSL programming.</span></span>

<span data-ttu-id="21409-140">Sie erstellen einen Shader visuell als Diagramm.</span><span class="sxs-lookup"><span data-stu-id="21409-140">You create a shader visually as a graph.</span></span> <span data-ttu-id="21409-141">Jeder Knoten zeigt eine Vorschau der Ausgabe bis zum jeweiligen Vorgang an.</span><span class="sxs-lookup"><span data-stu-id="21409-141">Each node displays a preview of the output up to that operation.</span></span> <span data-ttu-id="21409-142">Im nächsten Beispiel wird Lambert-Beleuchtung mit einer Kugelvorschau angewendet.</span><span class="sxs-lookup"><span data-stu-id="21409-142">Here's an example that applies Lambert lighting with a sphere preview.</span></span>

![Visuelles Shaderdiagramm](images/shaderdesigner.png)

<span data-ttu-id="21409-144">Verwenden Sie den Shader-Editor, um Shader im DGSL-Format zu entwerfen, zu bearbeiten und zu speichern.</span><span class="sxs-lookup"><span data-stu-id="21409-144">Use the Shader Editor to design, edit, and save shaders in the .dgsl format.</span></span> <span data-ttu-id="21409-145">Außerdem können die folgenden Formate exportiert werden:</span><span class="sxs-lookup"><span data-stu-id="21409-145">It also exports the following formats.</span></span>

-   <span data-ttu-id="21409-146">HLSL (Quellcode)</span><span class="sxs-lookup"><span data-stu-id="21409-146">.hlsl (source code)</span></span>
-   <span data-ttu-id="21409-147">CSO (Bytecode)</span><span class="sxs-lookup"><span data-stu-id="21409-147">.cso (bytecode)</span></span>
-   <span data-ttu-id="21409-148">H (HLSL-Bytecode-Array)</span><span class="sxs-lookup"><span data-stu-id="21409-148">.h (HLSL bytecode array)</span></span>

<span data-ttu-id="21409-149">Erstellen Sie [Buildanpassungsdateien](#build-customizations-for-3d-assets), um diese Formate zur Buildzeit in CSO-Dateien zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="21409-149">Create [build customization files](#build-customizations-for-3d-assets) to convert any of these formats to .cso files at build time.</span></span>

<span data-ttu-id="21409-150">Unten ist ein Abschnitt eines HLSL-Codes angegeben, der vom Shader-Editor exportiert wurde.</span><span class="sxs-lookup"><span data-stu-id="21409-150">Here is a portion of HLSL code that is exported by the Shader Editor.</span></span> <span data-ttu-id="21409-151">Dies ist nur der Code für den Lambert-Beleuchtungsknoten.</span><span class="sxs-lookup"><span data-stu-id="21409-151">This is only the code for the Lambert lighting node.</span></span>

```hlsl
//
// Lambert lighting function
//
float3 LambertLighting(
    float3 lightNormal,
    float3 surfaceNormal,
    float3 materialAmbient,
    float3 lightAmbient,
    float3 lightColor,
    float3 pixelColor
    )
{
    // Compute the amount of contribution per light.
    float diffuseAmount = saturate(dot(lightNormal, surfaceNormal));
    float3 diffuse = diffuseAmount * lightColor * pixelColor;

    // Combine ambient with diffuse.
    return saturate((materialAmbient * lightAmbient) + diffuse);
}
```

<span data-ttu-id="21409-152">Weitere Informationen finden Sie unter [Arbeiten mit Shadern](https://msdn.microsoft.com/library/windows/apps/hh873117.aspx).</span><span class="sxs-lookup"><span data-stu-id="21409-152">For more information, see [Working with Shaders](https://msdn.microsoft.com/library/windows/apps/hh873117.aspx).</span></span>

## <a name="build-customizations-for-3d-assets"></a><span data-ttu-id="21409-153">Buildanpassungen für 3D-Objekte</span><span class="sxs-lookup"><span data-stu-id="21409-153">Build customizations for 3D assets</span></span>


<span data-ttu-id="21409-154">Sie können dem Projekt Buildanpassungen hinzufügen, sodass Ressourcen von Visual Studio in nutzbare Formate konvertiert werden.</span><span class="sxs-lookup"><span data-stu-id="21409-154">You can add build customizations to your project so that Visual Studio converts resources to usable formats.</span></span> <span data-ttu-id="21409-155">Danach können Sie die Objekte in die App laden und verwenden, indem Sie DirectX-Ressourcen wie in jeder anderen DirectX-App auch erstellen und füllen.</span><span class="sxs-lookup"><span data-stu-id="21409-155">After that, you can load the assets into your app and use them by creating and filling DirectX resources just like you would in any other DirectX app.</span></span>

<span data-ttu-id="21409-156">Zum Hinzufügen von Buildanpassungen klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt und wählen die Option **Buildanpassungen...**.</span><span class="sxs-lookup"><span data-stu-id="21409-156">To add a build customization, you right-click on the project in the **Solution Explorer** and select **Build Customizations...**.</span></span> <span data-ttu-id="21409-157">Sie können dem Projekt die folgenden Arten von Buildanpassungen hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="21409-157">You can add the following types of build customizations to your project.</span></span>

-   <span data-ttu-id="21409-158">Von der Bildinhaltpipeline werden Bilddateien als Eingaben verwendet und DirectDraw Surface-Dateien (.dds) ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="21409-158">Image Content Pipeline takes image files as input and outputs DirectDraw Surface (.dds) files.</span></span>
-   <span data-ttu-id="21409-159">Von der Gitterinhaltpipeline werden Gitterdateien (z.B. FBX) als Eingabe verwendet und CMO-Gitterdateien ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="21409-159">Mesh Content Pipeline takes mesh files (such as .fbx) and outputs .cmo mesh files.</span></span>
-   <span data-ttu-id="21409-160">Von der Shaderinhaltpipeline werden visuelle Shaderdiagramme (.dgsl) aus dem Shader-Editor von Visual Studio verwendet und kompilierte Shaderausgabedateien (.cso) ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="21409-160">Shader Content Pipeline takes Visual Shader Graph (.dgsl) from the Visual Studio Shader Editor and outputs a Compiled Shader Output (.cso) file.</span></span>

<span data-ttu-id="21409-161">Weitere Informationen finden Sie unter [Verwenden von 3D-Objekten im Spiel oder in der App](https://msdn.microsoft.com/library/windows/apps/hh972446.aspx).</span><span class="sxs-lookup"><span data-stu-id="21409-161">For more information, see [Using 3-D Assets in Your Game or App](https://msdn.microsoft.com/library/windows/apps/hh972446.aspx).</span></span>

## <a name="debugging-directx-graphics"></a><span data-ttu-id="21409-162">Debuggen von DirectX-Grafiken</span><span class="sxs-lookup"><span data-stu-id="21409-162">Debugging DirectX graphics</span></span>


<span data-ttu-id="21409-163">Visual Studio enthält grafikspezifische Debugtools.</span><span class="sxs-lookup"><span data-stu-id="21409-163">Visual Studio provides graphics-specific debugging tools.</span></span> <span data-ttu-id="21409-164">Verwenden Sie diese Tools zum Debuggen der folgenden Komponenten:</span><span class="sxs-lookup"><span data-stu-id="21409-164">Use these tools to debug things like:</span></span>

-   <span data-ttu-id="21409-165">Grafikpipeline</span><span class="sxs-lookup"><span data-stu-id="21409-165">The graphics pipeline.</span></span>
-   <span data-ttu-id="21409-166">Ereignisaufrufliste</span><span class="sxs-lookup"><span data-stu-id="21409-166">The event call stack.</span></span>
-   <span data-ttu-id="21409-167">Objekttabelle</span><span class="sxs-lookup"><span data-stu-id="21409-167">The object table.</span></span>
-   <span data-ttu-id="21409-168">Gerätestatus</span><span class="sxs-lookup"><span data-stu-id="21409-168">The device state.</span></span>
-   <span data-ttu-id="21409-169">Shaderfehler</span><span class="sxs-lookup"><span data-stu-id="21409-169">Shader bugs.</span></span>
-   <span data-ttu-id="21409-170">Nicht initialisierte oder fehlerhafte Konstantenpuffer und Parameter</span><span class="sxs-lookup"><span data-stu-id="21409-170">Uninitialized or incorrect constant buffers and parameters.</span></span>
-   <span data-ttu-id="21409-171">DirectX-Versionskompatibilität</span><span class="sxs-lookup"><span data-stu-id="21409-171">DirectX version compatibility.</span></span>
-   <span data-ttu-id="21409-172">Begrenzte Direct2D-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="21409-172">Limited Direct2D support.</span></span>
-   <span data-ttu-id="21409-173">Betriebssystem- und SDK-Anforderungen</span><span class="sxs-lookup"><span data-stu-id="21409-173">Operating system and SDK requirements.</span></span>

<span data-ttu-id="21409-174">Weitere Informationen finden Sie unter [Debuggen von DirectX-Grafiken](https://msdn.microsoft.com/library/windows/apps/hh315751.aspx).</span><span class="sxs-lookup"><span data-stu-id="21409-174">For more information, see [Debugging DirectX Graphics](https://msdn.microsoft.com/library/windows/apps/hh315751.aspx).</span></span>

> <span data-ttu-id="21409-175">**Hinweis**: Dieser Artikel ist für Windows10-Entwickler gedacht, die Apps für die Universelle Windows-Plattform (UWP) schreiben.</span><span class="sxs-lookup"><span data-stu-id="21409-175">**Note**  This article is for Windows 10 developers writing Universal Windows Platform (UWP) apps.</span></span> <span data-ttu-id="21409-176">Wenn Sie für Windows8.x oder Windows Phone8.x entwickeln, finden Sie Informationen dazu in der [archivierten Dokumentation](http://go.microsoft.com/fwlink/p/?linkid=619132).</span><span class="sxs-lookup"><span data-stu-id="21409-176">If you’re developing for Windows 8.x or Windows Phone 8.x, see the [archived documentation](http://go.microsoft.com/fwlink/p/?linkid=619132).</span></span>

 

 

 




