---
title: Visual Studio-Tools für die Spieleprogrammierung
description: Sie erhalten eine Übersicht über spezielle DirectX-Tools, die unter Visual Studio verfügbar sind.
ms.assetid: 43137bfc-7876-70e0-515c-4722f68bd064
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP, Spiele, Visual Studio, Tools, DirectX
ms.localizationpriority: medium
ms.openlocfilehash: 5a3938f486d52942031944b1184a711ddbc579db
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "8209744"
---
# <a name="visual-studio-tools-for-game-programming"></a><span data-ttu-id="31ad9-104">Visual Studio-Tools für die Spieleprogrammierung</span><span class="sxs-lookup"><span data-stu-id="31ad9-104">Visual Studio tools for game programming</span></span>



**<span data-ttu-id="31ad9-105">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="31ad9-105">Summary</span></span>**

-   [<span data-ttu-id="31ad9-106">Erstellen eines DirectX-Spieleprojekts aus einer Vorlage</span><span class="sxs-lookup"><span data-stu-id="31ad9-106">Create a DirectX game project from a template</span></span>](user-interface.md)
-   <span data-ttu-id="31ad9-107">Visual Studio-Tools für die Programmierung von DirectX-Spielen</span><span class="sxs-lookup"><span data-stu-id="31ad9-107">Visual Studio tools for DirectX game programming</span></span>


<span data-ttu-id="31ad9-108">Wenn Sie Visual Studio Ultimate zum Entwickeln von DirectX-Apps verwenden, können Sie zusätzliche Tools zum Erstellen, Bearbeiten, Anzeigen in der Vorschau und Exportieren von Bild-, Modell- und Shaderressourcen nutzen.</span><span class="sxs-lookup"><span data-stu-id="31ad9-108">If you use Visual Studio Ultimate to develop DirectX apps, there are additional tools available for creating, editing, previewing, and exporting image, model, and shader resources.</span></span> <span data-ttu-id="31ad9-109">Außerdem sind Tools verfügbar, mit denen Sie Ressourcen zur Erstellungszeit konvertieren und DirectX-Grafikcode debuggen können.</span><span class="sxs-lookup"><span data-stu-id="31ad9-109">There are also tools that you can use to convert resources at build time and debug DirectX graphics code.</span></span>

<span data-ttu-id="31ad9-110">Dieses Thema enthält eine Übersicht über diese Grafiktools.</span><span class="sxs-lookup"><span data-stu-id="31ad9-110">This topic gives an overview of these graphics tools.</span></span>

## <a name="image-editor"></a><span data-ttu-id="31ad9-111">Grafik-Editor</span><span class="sxs-lookup"><span data-stu-id="31ad9-111">Image Editor</span></span>


<span data-ttu-id="31ad9-112">Nutzen Sie den Grafik-Editor zum Arbeiten mit den Arten von umfassenden Textur- und Bildformaten, die von DirectX verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="31ad9-112">Use the Image Editor to work with the kinds of rich texture and image formats that DirectX uses.</span></span> <span data-ttu-id="31ad9-113">Der Grafik-Editor unterstützt die folgenden Formate:</span><span class="sxs-lookup"><span data-stu-id="31ad9-113">The Image Editor supports the following formats.</span></span>

-   <span data-ttu-id="31ad9-114">PNG</span><span class="sxs-lookup"><span data-stu-id="31ad9-114">.png</span></span>
-   <span data-ttu-id="31ad9-115">JPG, JPEG, JPE, JFIF</span><span class="sxs-lookup"><span data-stu-id="31ad9-115">.jpg, .jpeg, .jpe, .jfif</span></span>
-   <span data-ttu-id="31ad9-116">DDS</span><span class="sxs-lookup"><span data-stu-id="31ad9-116">.dds</span></span>
-   <span data-ttu-id="31ad9-117">GIF</span><span class="sxs-lookup"><span data-stu-id="31ad9-117">.gif</span></span>
-   <span data-ttu-id="31ad9-118">BMP</span><span class="sxs-lookup"><span data-stu-id="31ad9-118">.bmp</span></span>
-   <span data-ttu-id="31ad9-119">DIB</span><span class="sxs-lookup"><span data-stu-id="31ad9-119">.dib</span></span>
-   <span data-ttu-id="31ad9-120">TIF, TIFF</span><span class="sxs-lookup"><span data-stu-id="31ad9-120">.tif, .tiff</span></span>
-   <span data-ttu-id="31ad9-121">TGA</span><span class="sxs-lookup"><span data-stu-id="31ad9-121">.tga</span></span>

<span data-ttu-id="31ad9-122">Erstellen Sie [Buildanpassungsdateien](#build-customizations-for-3d-assets), um diese Formate zur Buildzeit in DDS-Dateien zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="31ad9-122">Create [build customization files](#build-customizations-for-3d-assets) to convert these to .dds files at build time.</span></span>

<span data-ttu-id="31ad9-123">Weitere Informationen finden Sie unter [Arbeiten mit Texturen und Bildern](https://msdn.microsoft.com/library/windows/apps/hh873119.aspx).</span><span class="sxs-lookup"><span data-stu-id="31ad9-123">For more information, see [Working with Textures and Images](https://msdn.microsoft.com/library/windows/apps/hh873119.aspx).</span></span>

> <span data-ttu-id="31ad9-124">**Hinweis:** der Grafik-Editor ist kein Ersatz für eine bildbearbeitungs app gedacht, aber für viele einfache Anzeige- und bearbeitungsfälle geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="31ad9-124">**Note**The Image Editor is not intended to be a replacement for a full feature image editing app, but is appropriate for many simple viewing and editing scenarios.</span></span>

 

## <a name="model-editor"></a><span data-ttu-id="31ad9-125">Modell-Editor</span><span class="sxs-lookup"><span data-stu-id="31ad9-125">Model Editor</span></span>


<span data-ttu-id="31ad9-126">Sie können den Modell-Editor verwenden, um grundlegende 3D-Modelle ganz neu zu erstellen oder um komplexere 3D-Modelle aus umfassenden 3D-Modelliertools anzuzeigen oder zu ändern.</span><span class="sxs-lookup"><span data-stu-id="31ad9-126">You can use the Model Editor to create basic 3D models from scratch, or to view and modify more-complex 3D models from full-featured 3D modeling tools.</span></span> <span data-ttu-id="31ad9-127">Der Modell-Editor unterstützt mehrere 3D-Modellformate, die bei der Entwicklung von DirectX-Apps verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="31ad9-127">The Model Editor supports several 3D model formats that are used in DirectX app development.</span></span> <span data-ttu-id="31ad9-128">Sie können [Buildanpassungsdateien](#build-customizations-for-3d-assets) erstellen, um diese Formate zur Buildzeit in CMO-Dateien zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="31ad9-128">You can create [build customization files](#build-customizations-for-3d-assets) to convert these to .cmo files at build time.</span></span>

-   <span data-ttu-id="31ad9-129">FBX</span><span class="sxs-lookup"><span data-stu-id="31ad9-129">.fbx</span></span>
-   <span data-ttu-id="31ad9-130">DAE</span><span class="sxs-lookup"><span data-stu-id="31ad9-130">.dae</span></span>
-   <span data-ttu-id="31ad9-131">OBJ</span><span class="sxs-lookup"><span data-stu-id="31ad9-131">.obj</span></span>

<span data-ttu-id="31ad9-132">Dies ist ein Screenshot eines Modells im Editor, auf das Beleuchtungsfunktionen angewendet wurden.</span><span class="sxs-lookup"><span data-stu-id="31ad9-132">Here's a screenshot of a model in the editor with lighting applied.</span></span>

![Teekanne](images/modeleditor.png)

<span data-ttu-id="31ad9-134">Weitere Informationen finden Sie unter [Arbeiten mit 3D-Modellen](https://msdn.microsoft.com/library/windows/apps/hh873114.aspx).</span><span class="sxs-lookup"><span data-stu-id="31ad9-134">For more information, see [Working with 3-D Models](https://msdn.microsoft.com/library/windows/apps/hh873114.aspx).</span></span>

> <span data-ttu-id="31ad9-135">**Hinweis:** der Modell-Editor ist kein Ersatz für eine modellbearbeitungs app gedacht, aber für viele einfache Anzeige- und bearbeitungsfälle geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="31ad9-135">**Note**The Model Editor is not intended to be a replacement for a full feature model editing app, but is appropriate for many simple viewing and editing scenarios.</span></span>

 

## <a name="shader-designer"></a><span data-ttu-id="31ad9-136">Shader-Designer</span><span class="sxs-lookup"><span data-stu-id="31ad9-136">Shader Designer</span></span>


<span data-ttu-id="31ad9-137">Verwenden Sie den Shader-Designer zum Erstellen benutzerdefinierter visueller Effekte für das Spiel oder die App, auch wenn Sie nicht mit der HLSL-Programmierung vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="31ad9-137">Use the Shader Designer to create custom visual effects for your game or app even if you don't know HLSL programming.</span></span>

<span data-ttu-id="31ad9-138">Sie erstellen einen Shader visuell als Diagramm.</span><span class="sxs-lookup"><span data-stu-id="31ad9-138">You create a shader visually as a graph.</span></span> <span data-ttu-id="31ad9-139">Jeder Knoten zeigt eine Vorschau der Ausgabe bis zum jeweiligen Vorgang an.</span><span class="sxs-lookup"><span data-stu-id="31ad9-139">Each node displays a preview of the output up to that operation.</span></span> <span data-ttu-id="31ad9-140">Im nächsten Beispiel wird Lambert-Beleuchtung mit einer Kugelvorschau angewendet.</span><span class="sxs-lookup"><span data-stu-id="31ad9-140">Here's an example that applies Lambert lighting with a sphere preview.</span></span>

![Visuelles Shaderdiagramm](images/shaderdesigner.png)

<span data-ttu-id="31ad9-142">Verwenden Sie den Shader-Editor, um Shader im DGSL-Format zu entwerfen, zu bearbeiten und zu speichern.</span><span class="sxs-lookup"><span data-stu-id="31ad9-142">Use the Shader Editor to design, edit, and save shaders in the .dgsl format.</span></span> <span data-ttu-id="31ad9-143">Außerdem können die folgenden Formate exportiert werden:</span><span class="sxs-lookup"><span data-stu-id="31ad9-143">It also exports the following formats.</span></span>

-   <span data-ttu-id="31ad9-144">HLSL (Quellcode)</span><span class="sxs-lookup"><span data-stu-id="31ad9-144">.hlsl (source code)</span></span>
-   <span data-ttu-id="31ad9-145">CSO (Bytecode)</span><span class="sxs-lookup"><span data-stu-id="31ad9-145">.cso (bytecode)</span></span>
-   <span data-ttu-id="31ad9-146">H (HLSL-Bytecode-Array)</span><span class="sxs-lookup"><span data-stu-id="31ad9-146">.h (HLSL bytecode array)</span></span>

<span data-ttu-id="31ad9-147">Erstellen Sie [Buildanpassungsdateien](#build-customizations-for-3d-assets), um diese Formate zur Buildzeit in CSO-Dateien zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="31ad9-147">Create [build customization files](#build-customizations-for-3d-assets) to convert any of these formats to .cso files at build time.</span></span>

<span data-ttu-id="31ad9-148">Unten ist ein Abschnitt eines HLSL-Codes angegeben, der vom Shader-Editor exportiert wurde.</span><span class="sxs-lookup"><span data-stu-id="31ad9-148">Here is a portion of HLSL code that is exported by the Shader Editor.</span></span> <span data-ttu-id="31ad9-149">Dies ist nur der Code für den Lambert-Beleuchtungsknoten.</span><span class="sxs-lookup"><span data-stu-id="31ad9-149">This is only the code for the Lambert lighting node.</span></span>

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

<span data-ttu-id="31ad9-150">Weitere Informationen finden Sie unter [Arbeiten mit Shadern](https://msdn.microsoft.com/library/windows/apps/hh873117.aspx).</span><span class="sxs-lookup"><span data-stu-id="31ad9-150">For more information, see [Working with Shaders](https://msdn.microsoft.com/library/windows/apps/hh873117.aspx).</span></span>

## <a name="build-customizations-for-3d-assets"></a><span data-ttu-id="31ad9-151">Buildanpassungen für 3D-Objekte</span><span class="sxs-lookup"><span data-stu-id="31ad9-151">Build customizations for 3D assets</span></span>


<span data-ttu-id="31ad9-152">Sie können dem Projekt Buildanpassungen hinzufügen, sodass Ressourcen von Visual Studio in nutzbare Formate konvertiert werden.</span><span class="sxs-lookup"><span data-stu-id="31ad9-152">You can add build customizations to your project so that Visual Studio converts resources to usable formats.</span></span> <span data-ttu-id="31ad9-153">Danach können Sie die Objekte in die App laden und verwenden, indem Sie DirectX-Ressourcen wie in jeder anderen DirectX-App auch erstellen und füllen.</span><span class="sxs-lookup"><span data-stu-id="31ad9-153">After that, you can load the assets into your app and use them by creating and filling DirectX resources just like you would in any other DirectX app.</span></span>

<span data-ttu-id="31ad9-154">Zum Hinzufügen von Buildanpassungen klicken Sie mit der rechten Maustaste auf das Projekt im **Projektmappen-Explorer** , und wählen Sie **Anpassungen erstellen**. Sie können die folgenden Arten von Buildanpassungen zu Ihrem Projekt hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="31ad9-154">To add a build customization, you right-click on the project in the **Solution Explorer** and select **Build Customizations...**. You can add the following types of build customizations to your project.</span></span>

-   <span data-ttu-id="31ad9-155">Von der Bildinhaltpipeline werden Bilddateien als Eingaben verwendet und DirectDraw Surface-Dateien (.dds) ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="31ad9-155">Image Content Pipeline takes image files as input and outputs DirectDraw Surface (.dds) files.</span></span>
-   <span data-ttu-id="31ad9-156">Von der Gitterinhaltpipeline werden Gitterdateien (z.B. FBX) als Eingabe verwendet und CMO-Gitterdateien ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="31ad9-156">Mesh Content Pipeline takes mesh files (such as .fbx) and outputs .cmo mesh files.</span></span>
-   <span data-ttu-id="31ad9-157">Von der Shaderinhaltpipeline werden visuelle Shaderdiagramme (.dgsl) aus dem Shader-Editor von Visual Studio verwendet und kompilierte Shaderausgabedateien (.cso) ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="31ad9-157">Shader Content Pipeline takes Visual Shader Graph (.dgsl) from the Visual Studio Shader Editor and outputs a Compiled Shader Output (.cso) file.</span></span>

<span data-ttu-id="31ad9-158">Weitere Informationen finden Sie unter [Verwenden von 3D-Objekten im Spiel oder in der App](https://msdn.microsoft.com/library/windows/apps/hh972446.aspx).</span><span class="sxs-lookup"><span data-stu-id="31ad9-158">For more information, see [Using 3-D Assets in Your Game or App](https://msdn.microsoft.com/library/windows/apps/hh972446.aspx).</span></span>

## <a name="debugging-directx-graphics"></a><span data-ttu-id="31ad9-159">Debuggen von DirectX-Grafiken</span><span class="sxs-lookup"><span data-stu-id="31ad9-159">Debugging DirectX graphics</span></span>


<span data-ttu-id="31ad9-160">Visual Studio enthält grafikspezifische Debugtools.</span><span class="sxs-lookup"><span data-stu-id="31ad9-160">Visual Studio provides graphics-specific debugging tools.</span></span> <span data-ttu-id="31ad9-161">Verwenden Sie diese Tools zum Debuggen der folgenden Komponenten:</span><span class="sxs-lookup"><span data-stu-id="31ad9-161">Use these tools to debug things like:</span></span>

-   <span data-ttu-id="31ad9-162">Grafikpipeline</span><span class="sxs-lookup"><span data-stu-id="31ad9-162">The graphics pipeline.</span></span>
-   <span data-ttu-id="31ad9-163">Ereignisaufrufliste</span><span class="sxs-lookup"><span data-stu-id="31ad9-163">The event call stack.</span></span>
-   <span data-ttu-id="31ad9-164">Objekttabelle</span><span class="sxs-lookup"><span data-stu-id="31ad9-164">The object table.</span></span>
-   <span data-ttu-id="31ad9-165">Gerätestatus</span><span class="sxs-lookup"><span data-stu-id="31ad9-165">The device state.</span></span>
-   <span data-ttu-id="31ad9-166">Shaderfehler</span><span class="sxs-lookup"><span data-stu-id="31ad9-166">Shader bugs.</span></span>
-   <span data-ttu-id="31ad9-167">Nicht initialisierte oder fehlerhafte Konstantenpuffer und Parameter</span><span class="sxs-lookup"><span data-stu-id="31ad9-167">Uninitialized or incorrect constant buffers and parameters.</span></span>
-   <span data-ttu-id="31ad9-168">DirectX-Versionskompatibilität</span><span class="sxs-lookup"><span data-stu-id="31ad9-168">DirectX version compatibility.</span></span>
-   <span data-ttu-id="31ad9-169">Begrenzte Direct2D-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="31ad9-169">Limited Direct2D support.</span></span>
-   <span data-ttu-id="31ad9-170">Betriebssystem- und SDK-Anforderungen</span><span class="sxs-lookup"><span data-stu-id="31ad9-170">Operating system and SDK requirements.</span></span>

<span data-ttu-id="31ad9-171">Weitere Informationen finden Sie unter [Debuggen von DirectX-Grafiken](https://msdn.microsoft.com/library/windows/apps/hh315751.aspx).</span><span class="sxs-lookup"><span data-stu-id="31ad9-171">For more information, see [Debugging DirectX Graphics](https://msdn.microsoft.com/library/windows/apps/hh315751.aspx).</span></span>


 

 

 




