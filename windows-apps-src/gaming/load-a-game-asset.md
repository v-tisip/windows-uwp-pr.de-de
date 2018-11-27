---
title: Laden von Ressourcen im DirectX-Spiel
description: In den meisten Spielen werden Ressourcen und Objekte (wie Shader, Texturen, vordefinierte Gitter oder andere Grafikdaten) an bestimmten Stellen aus dem lokalen Speicher oder über einen anderen Datenstrom geladen.
ms.assetid: e45186fa-57a3-dc70-2b59-408bff0c0b41
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, DirectX, Laden von Ressourcen
ms.localizationpriority: medium
ms.openlocfilehash: ca16dd6115bbbe84529928ca58ee0d3074498728
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7703134"
---
# <a name="load-resources-in-your-directx-game"></a><span data-ttu-id="71100-104">Laden von Ressourcen im DirectX-Spiel</span><span class="sxs-lookup"><span data-stu-id="71100-104">Load resources in your DirectX game</span></span>



<span data-ttu-id="71100-105">In den meisten Spielen werden Ressourcen und Objekte (wie Shader, Texturen, vordefinierte Gitter oder andere Grafikdaten) an bestimmten Stellen aus dem lokalen Speicher oder über einen anderen Datenstrom geladen.</span><span class="sxs-lookup"><span data-stu-id="71100-105">Most games, at some point, load resources and assets (such as shaders, textures, predefined meshes or other graphics data) from local storage or some other data stream.</span></span> <span data-ttu-id="71100-106">Dieser Abschnitt enthält eine allgemeine Übersicht über die Aspekte, die beim Laden dieser Dateien zur Verwendung in Ihrem DirectX-C/C++-UWP-Spiel (Universelle Windows-Plattform) zu berücksichtigen sind.</span><span class="sxs-lookup"><span data-stu-id="71100-106">Here, we walk you through a high-level view of what you must consider when loading these files to use in your DirectX C/C++ Universal Windows Platform (UWP) game.</span></span>

<span data-ttu-id="71100-107">Es kann beispielsweise sein, dass die Gitter für polygonale Objekte im Spiel mit einem anderen Tool erstellt und in einem bestimmten Format exportiert wurden.</span><span class="sxs-lookup"><span data-stu-id="71100-107">For example, the meshes for polygonal objects in your game might have been created with another tool, and exported to a specific format.</span></span> <span data-ttu-id="71100-108">Die kann auch besonders für Texturen der Fall sein: Während eine flache, unkomprimierte Bitmapgrafik in der Regel von den meisten Tools geschrieben und von den meisten Grafik-APIs verarbeitet werden kann, ist dieses Format zur Verwendung im Spiel möglicherweise sehr ineffizient.</span><span class="sxs-lookup"><span data-stu-id="71100-108">The same is true for textures, and more so: while a flat, uncompressed bitmap can be commonly written by most tools and understood by most graphics APIs, it can be extremely inefficient for use in your game.</span></span> <span data-ttu-id="71100-109">Sie werden durch die grundlegenden Schritte des Ladens von drei unterschiedlichen Arten von Grafikressourcen geführt, die in Verbindung mit Direct3D verwendet werden: Gitter (Modelle), Texturen (Bitmaps) und kompilierte Shaderobjekte.</span><span class="sxs-lookup"><span data-stu-id="71100-109">Here, we guide you through the basic steps for loading three different types of graphic resources for use with Direct3D: meshes (models), textures (bitmaps), and compiled shader objects.</span></span>

## <a name="what-you-need-to-know"></a><span data-ttu-id="71100-110">Wissenswertes</span><span class="sxs-lookup"><span data-stu-id="71100-110">What you need to know</span></span>


### <a name="technologies"></a><span data-ttu-id="71100-111">Technologien</span><span class="sxs-lookup"><span data-stu-id="71100-111">Technologies</span></span>

-   <span data-ttu-id="71100-112">Parallel Patterns Library (PPL)</span><span class="sxs-lookup"><span data-stu-id="71100-112">Parallel Patterns Library (ppltasks.h)</span></span>

### <a name="prerequisites"></a><span data-ttu-id="71100-113">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="71100-113">Prerequisites</span></span>

-   <span data-ttu-id="71100-114">Informationen zur grundlegenden Windows-Runtime</span><span class="sxs-lookup"><span data-stu-id="71100-114">Understand the basic Windows Runtime</span></span>
-   <span data-ttu-id="71100-115">Grundlegendes zu asynchronen Aufgaben</span><span class="sxs-lookup"><span data-stu-id="71100-115">Understand asynchronous tasks</span></span>
-   <span data-ttu-id="71100-116">Grundbegriffe der Programmierung von 3D-Grafiken</span><span class="sxs-lookup"><span data-stu-id="71100-116">Understand the basic concepts of 3-D graphics programming.</span></span>

<span data-ttu-id="71100-117">Dieses Beispiel enthält auch drei Codedateien zum Laden und Verwalten von Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="71100-117">This sample also includes three code files for resource loading and management.</span></span> <span data-ttu-id="71100-118">Sie werden in diesem Thema häufiger auf die in diesen Dateien definierten Codeobjekte treffen.</span><span class="sxs-lookup"><span data-stu-id="71100-118">You'll encounter the code objects defined in these files throughout this topic.</span></span>

-   <span data-ttu-id="71100-119">BasicLoader.h/.cpp </span><span class="sxs-lookup"><span data-stu-id="71100-119">BasicLoader.h/.cpp</span></span>
-   <span data-ttu-id="71100-120">BasicReaderWriter.h/.cpp</span><span class="sxs-lookup"><span data-stu-id="71100-120">BasicReaderWriter.h/.cpp</span></span>
-   <span data-ttu-id="71100-121">DDSTextureLoader.h/.cpp</span><span class="sxs-lookup"><span data-stu-id="71100-121">DDSTextureLoader.h/.cpp</span></span>

<span data-ttu-id="71100-122">Sie können über die folgenden Links auf den vollständigen Code für diese Beispiele zugreifen.</span><span class="sxs-lookup"><span data-stu-id="71100-122">The complete code for these samples can be found in the following links.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="71100-123">Thema</span><span class="sxs-lookup"><span data-stu-id="71100-123">Topic</span></span></th>
<th align="left"><span data-ttu-id="71100-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="71100-124">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="complete-code-for-basicloader.md"><span data-ttu-id="71100-125">Vollständiger Code für BasicLoader</span><span class="sxs-lookup"><span data-stu-id="71100-125">Complete code for BasicLoader</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="71100-126">Vollständiger Code für eine Klasse und Methoden, die gitterförmige Grafikobjekte konvertieren und in den Speicher laden.</span><span class="sxs-lookup"><span data-stu-id="71100-126">Complete code for a class and methods that convert and load graphics mesh objects into memory.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="complete-code-for-basicreaderwriter.md"><span data-ttu-id="71100-127">Vollständiger Code für BasicReaderWriter</span><span class="sxs-lookup"><span data-stu-id="71100-127">Complete code for BasicReaderWriter</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="71100-128">Vollständiger Code für eine Klasse und Methoden zum allgemeinen Lesen und Schreiben von Binärdatendateien.</span><span class="sxs-lookup"><span data-stu-id="71100-128">Complete code for a class and methods for reading and writing binary data files in general.</span></span> <span data-ttu-id="71100-129">Wird von der <a href="complete-code-for-basicloader.md">BasicLoader</a>-Klasse verwendet.</span><span class="sxs-lookup"><span data-stu-id="71100-129">Used by the <a href="complete-code-for-basicloader.md">BasicLoader</a> class.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="complete-code-for-ddstextureloader.md"><span data-ttu-id="71100-130">Vollständiger Code für DDSTextureLoader</span><span class="sxs-lookup"><span data-stu-id="71100-130">Complete code for DDSTextureLoader</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="71100-131">Vollständiger Code für eine Klasse und Methode, die eine DDS-Textur aus dem Speicher lädt.</span><span class="sxs-lookup"><span data-stu-id="71100-131">Complete code for a class and method that loads a DDS texture from memory.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="instructions"></a><span data-ttu-id="71100-132">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="71100-132">Instructions</span></span>

### <a name="asynchronous-loading"></a><span data-ttu-id="71100-133">Asynchrones Laden</span><span class="sxs-lookup"><span data-stu-id="71100-133">Asynchronous loading</span></span>

<span data-ttu-id="71100-134">Das asynchrone Laden wird mithilfe der **task**-Vorlage der Parallel Patterns Library (PPL) durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="71100-134">Asynchronous loading is handled using the **task** template from the Parallel Patterns Library (PPL).</span></span> <span data-ttu-id="71100-135">Eine **task** enthält einen Methodenaufruf gefolgt von einer Lambda-Funktion, mit der die Ergebnisse des asynchronen Aufrufs nach dessen Abschluss verarbeitet werden. Dabei wird normalerweise das folgende Format verwendet:</span><span class="sxs-lookup"><span data-stu-id="71100-135">A **task** contains a method call followed by a lambda that processes the results of the async call after it completes, and usually follows the format of:</span></span>

`task<generic return type>(async code to execute).then((parameters for lambda){ lambda code contents });`<span data-ttu-id="71100-136">.</span><span class="sxs-lookup"><span data-stu-id="71100-136">.</span></span>

<span data-ttu-id="71100-137">Aufgaben können mithilfe der **.then()**-Syntax verkettet werden. Wenn ein Vorgang abgeschlossen ist, kann ein anderer asynchroner Vorgang ausgeführt werden, der von den Ergebnissen des vorherigen Vorgangs abhängt.</span><span class="sxs-lookup"><span data-stu-id="71100-137">Tasks can be chained together using the **.then()** syntax, so that when one operation completes, another async operation that depends on the results of the prior operation can be run.</span></span> <span data-ttu-id="71100-138">Auf diese Weise können Sie komplexe Objekte in separaten Threads für den Spieler nahezu unbemerkt laden, konvertieren und verwalten.</span><span class="sxs-lookup"><span data-stu-id="71100-138">In this way, you can load, convert, and manage complex assets on separate threads in a way that appears almost invisible to the player.</span></span>

<span data-ttu-id="71100-139">Weitere Informationen finden Sie unter [Asynchrone Programmierung in C++](https://msdn.microsoft.com/library/windows/apps/mt187334).</span><span class="sxs-lookup"><span data-stu-id="71100-139">For more details, read [Asynchronous programming in C++](https://msdn.microsoft.com/library/windows/apps/mt187334).</span></span>

<span data-ttu-id="71100-140">Als Nächstes werfen wir einen Blick auf die Grundstruktur zum Deklarieren und Erstellen einer Methode für das asynchrone Laden von Dateien: **ReadDataAsync**.</span><span class="sxs-lookup"><span data-stu-id="71100-140">Now, let's look at the basic structure for declaring and creating an async file loading method, **ReadDataAsync**.</span></span>

```cpp
#include <ppltasks.h>

// ...
concurrency::task<Platform::Array<byte>^> ReadDataAsync(
        _In_ Platform::String^ filename);

// ...

using concurrency;

task<Platform::Array<byte>^> BasicReaderWriter::ReadDataAsync(
    _In_ Platform::String^ filename
    )
{
    return task<StorageFile^>(m_location->GetFileAsync(filename)).then([=](StorageFile^ file)
    {
        return FileIO::ReadBufferAsync(file);
    }).then([=](IBuffer^ buffer)
    {
        auto fileData = ref new Platform::Array<byte>(buffer->Length);
        DataReader::FromBuffer(buffer)->ReadBytes(fileData);
        return fileData;
    });
}
```

<span data-ttu-id="71100-141">Wenn in Ihrem Code basierend auf diesem Code die oben definierte **ReadDataAsync**-Methode aufgerufen wird, wird eine Aufgabe zum Auslesen eines Puffers aus dem Dateisystem erstellt.</span><span class="sxs-lookup"><span data-stu-id="71100-141">In this code, when your code calls the **ReadDataAsync** method defined above, a task is created to read a buffer from the file system.</span></span> <span data-ttu-id="71100-142">Nach Abschluss dieses Vorgangs übernimmt eine verkettete Aufgabe den Puffer und führt für die Bytes dieses Puffers einen Datenstrom in ein Array durch, indem der statische [**DataReader**](https://msdn.microsoft.com/library/windows/apps/br208119)-Typ verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="71100-142">Once it completes, a chained task takes the buffer and streams the bytes from that buffer into an array using the static [**DataReader**](https://msdn.microsoft.com/library/windows/apps/br208119) type.</span></span>

```cpp
m_basicReaderWriter = ref new BasicReaderWriter();

// ...
return m_basicReaderWriter->ReadDataAsync(filename).then([=](const Platform::Array<byte>^ bytecode)
    {
      // Perform some operation with the data when the async load completes.          
    });
```

<span data-ttu-id="71100-143">Dies ist der Aufruf an **ReadDataAsync**.</span><span class="sxs-lookup"><span data-stu-id="71100-143">Here's the call you make to **ReadDataAsync**.</span></span> <span data-ttu-id="71100-144">Nach Abschluss des Vorgangs empfängt der Code ein Array mit Bytes, die aus der bereitgestellten Datei ausgelesen wurden.</span><span class="sxs-lookup"><span data-stu-id="71100-144">When it completes, your code receives an array of bytes read from the provided file.</span></span> <span data-ttu-id="71100-145">Da **ReadDataAsync** selbst als Aufgabe definiert ist, können Sie mithilfe einer Lambda-Funktion einen bestimmten Vorgang durchführen, wenn das Bytearray zurückgegeben wird. Dies kann beispielsweise die Übergabe dieser Bytedaten an eine geeignete DirectX-Funktion sein.</span><span class="sxs-lookup"><span data-stu-id="71100-145">Since **ReadDataAsync** itself is defined as a task, you can use a lambda to perform a specific operation when the byte array is returned, such as passing that byte data to a DirectX function that can use it.</span></span>

<span data-ttu-id="71100-146">Wenn Ihr Spiel nicht zu komplex aufgebaut ist, können Sie die Ressourcen mit einer Methode dieser Art laden, wenn Benutzer das Spiel starten.</span><span class="sxs-lookup"><span data-stu-id="71100-146">If your game is sufficiently simple, load your resources with a method like this when the user starts the game.</span></span> <span data-ttu-id="71100-147">Sie können diesen Schritt ausführen, bevor Sie an einem bestimmten Punkt der Aufrufabfolge Ihrer [**IFrameworkView::Run**](https://msdn.microsoft.com/library/windows/apps/hh700505)-Implementierung die Hauptspielschleife starten.</span><span class="sxs-lookup"><span data-stu-id="71100-147">You can do this before you start the main game loop from some point in the call sequence of your [**IFrameworkView::Run**](https://msdn.microsoft.com/library/windows/apps/hh700505) implementation.</span></span> <span data-ttu-id="71100-148">Sie rufen auch hier wieder die Methoden zum Laden der Ressourcen asynchron auf, damit das Spiel schneller gestartet werden kann und Spieler nicht auf den Abschluss des Ladevorgangs warten müssen, bevor die ersten Interaktionen möglich sind.</span><span class="sxs-lookup"><span data-stu-id="71100-148">Again, you call your resource loading methods asynchronously so the game can start quicker and so the player doesn't have to wait until the loading completes before engaging in early interactions.</span></span>

<span data-ttu-id="71100-149">Das eigentliche Spiel sollten jedoch erst richtig gestartet werden, nachdem das asynchrone Laden vollständig abgeschlossen ist!</span><span class="sxs-lookup"><span data-stu-id="71100-149">However, you don't want to start the game proper until all of the async loading has completed!</span></span> <span data-ttu-id="71100-150">Erstellen Sie eine Methode, mit der angezeigt wird, wann der Ladevorgang abgeschlossen ist, z.B. ein bestimmtes Feld. Verwenden Sie dann die Lambda-Funktionen für die Lademethoden, um den Abschluss des Vorgangs anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="71100-150">Create some method for signaling when loading is complete, such as a specific field, and use the lambdas on your loading method(s) to set that signal when finished.</span></span> <span data-ttu-id="71100-151">Überprüfen Sie die Variable, bevor Sie Komponenten starten, in denen die geladenen Ressourcen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="71100-151">Check the variable before starting any components that use those loaded resources.</span></span>

<span data-ttu-id="71100-152">In diesem Beispiel werden die in „BasicLoader.cpp“ definierten asynchronen Methoden verwendet, um Shader, ein Gitter und eine Textur zu laden, wenn das Spiel gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="71100-152">Here's an example using the async methods defined in BasicLoader.cpp to load shaders, a mesh, and a texture when the game starts up.</span></span> <span data-ttu-id="71100-153">Beachten Sie, dass für das Spielobjekt ein bestimmtes Feld **m\_loadingComplete** festgelegt wird, nachdem alle Lademethoden abgeschlossen sind.</span><span class="sxs-lookup"><span data-stu-id="71100-153">Notice that it sets a specific field on the game object, **m\_loadingComplete**, when all of the loading methods finish.</span></span>

```cpp
void ResourceLoading::CreateDeviceResources()
{
    // DirectXBase is a common sample class that implements a basic view provider. 
    
    DirectXBase::CreateDeviceResources(); 

    // ...

    // This flag will keep track of whether or not all application
    // resources have been loaded.  Until all resources are loaded,
    // only the sample overlay will be drawn on the screen.
    m_loadingComplete = false;

    // Create a BasicLoader, and use it to asynchronously load all
    // application resources.  When an output value becomes non-null,
    // this indicates that the asynchronous operation has completed.
    BasicLoader^ loader = ref new BasicLoader(m_d3dDevice.Get());

    auto loadVertexShaderTask = loader->LoadShaderAsync(
        "SimpleVertexShader.cso",
        nullptr,
        0,
        &m_vertexShader,
        &m_inputLayout
        );

    auto loadPixelShaderTask = loader->LoadShaderAsync(
        "SimplePixelShader.cso",
        &m_pixelShader
        );

    auto loadTextureTask = loader->LoadTextureAsync(
        "reftexture.dds",
        nullptr,
        &m_textureSRV
        );

    auto loadMeshTask = loader->LoadMeshAsync(
        "refmesh.vbo",
        &m_vertexBuffer,
        &m_indexBuffer,
        nullptr,
        &m_indexCount
        );

    // The && operator can be used to create a single task that represents
    // a group of multiple tasks. The new task's completed handler will only
    // be called once all associated tasks have completed. In this case, the
    // new task represents a task to load various assets from the package.
    (loadVertexShaderTask && loadPixelShaderTask && loadTextureTask && loadMeshTask).then([=]()
    {
        m_loadingComplete = true;
    });

    // Create constant buffers and other graphics device-specific resources here.
}
```

<span data-ttu-id="71100-154">Die Aufgaben werden mithilfe des Operators „&&“ aggregiert. So wird die Lambda-Funktion, mit der das Kennzeichen für „Laden abgeschlossen“ festgelegt wird, erst ausgelöst, wenn alle Aufgaben abgeschlossen sind.</span><span class="sxs-lookup"><span data-stu-id="71100-154">Note that the tasks have been aggregated using the && operator such that the lambda that sets the loading complete flag is triggered only when all of the tasks complete.</span></span> <span data-ttu-id="71100-155">Beachten Sie, dass Sie bei Verwendung mehrerer Kennzeichen auch Racebedingungen nutzen können.</span><span class="sxs-lookup"><span data-stu-id="71100-155">Note that if you have multiple flags, you have the possibility of race conditions.</span></span> <span data-ttu-id="71100-156">Wenn mit der Lambda-Funktion beispielsweise zwei Kennzeichen hintereinander für denselben Wert festgelegt werden, wird von einem anderen Thread möglicherweise nur das erste Kennzeichen erkannt, falls die Prüfung auf Kennzeichen vor dem Festlegen des zweiten Kennzeichens durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="71100-156">For example, if the lambda sets two flags sequentially to the same value, another thread may only see the first flag set if it examines them before the second flag is set.</span></span>

<span data-ttu-id="71100-157">Sie haben erfahren, wie Ressourcendateien asynchron geladen werden.</span><span class="sxs-lookup"><span data-stu-id="71100-157">You've seen how to load resource files asynchronously.</span></span> <span data-ttu-id="71100-158">Das synchrone Laden von Dateien ist wesentlich einfacher. Entsprechende Beispiele dafür finden Sie unter [Vollständiger Code für BasicReaderWriter](complete-code-for-basicreaderwriter.md) und [Vollständiger Code für BasicLoader](complete-code-for-basicloader.md).</span><span class="sxs-lookup"><span data-stu-id="71100-158">Synchronous file loads are much simpler, and you can find examples of them in [Complete code for BasicReaderWriter](complete-code-for-basicreaderwriter.md) and [Complete code for BasicLoader](complete-code-for-basicloader.md).</span></span>

<span data-ttu-id="71100-159">Für unterschiedliche Arten von Ressourcen und Objekten ist häufig eine zusätzliche Verarbeitung oder Konvertierung erforderlich, bevor Sie diese in Ihrer Grafikpipeline verwenden.</span><span class="sxs-lookup"><span data-stu-id="71100-159">Of course, different resource and asset types often require additional processing or conversion before they are ready to be used in your graphics pipeline.</span></span> <span data-ttu-id="71100-160">Wir sehen uns drei spezielle Typen von Ressourcen an: Gitter, Texturen und Shader.</span><span class="sxs-lookup"><span data-stu-id="71100-160">Let's take a look at three specific types of resources: meshes, textures, and shaders.</span></span>

### <a name="loading-meshes"></a><span data-ttu-id="71100-161">Laden von Gittern</span><span class="sxs-lookup"><span data-stu-id="71100-161">Loading meshes</span></span>

<span data-ttu-id="71100-162">Bei Gittern handelt es sich um Vertexdaten, die entweder mithilfe von Prozeduren im Code des Spiels generiert oder aus einer anderen App (wie 3DStudio MAX oder Alias WaveFront) oder einem anderen Tool in eine Datei exportiert werden.</span><span class="sxs-lookup"><span data-stu-id="71100-162">Meshes are vertex data, either generated procedurally by code within your game or exported to a file from another app (like 3DStudio MAX or Alias WaveFront) or tool.</span></span> <span data-ttu-id="71100-163">Diese Gitter stellen die Modelle Ihres Spiels dar, von einfachen Grundtypen wie Würfel und Kugeln bis zu Autos, Häusern und Figuren.</span><span class="sxs-lookup"><span data-stu-id="71100-163">These meshes represent the models in your game, from simple primitives like cubes and spheres to cars and houses and characters.</span></span> <span data-ttu-id="71100-164">Je nach Format sind darin auch Farb- und Animationsdaten enthalten.</span><span class="sxs-lookup"><span data-stu-id="71100-164">They often contain color and animation data, as well, depending on their format.</span></span> <span data-ttu-id="71100-165">Wir konzentrieren uns hier auf Gitter, die nur Vertexdaten enthalten.</span><span class="sxs-lookup"><span data-stu-id="71100-165">We'll focus on meshes that contain only vertex data.</span></span>

<span data-ttu-id="71100-166">Um ein Gitter richtig laden zu können, müssen Sie das Format der Daten in der Datei für das Gitter kennen.</span><span class="sxs-lookup"><span data-stu-id="71100-166">To load a mesh correctly, you must know the format of the data in the file for the mesh.</span></span> <span data-ttu-id="71100-167">Mit dem obigen einfachen **BasicReaderWriter**-Typ werden die Daten lediglich als Bytestream gelesen. Dabei ist dem Typ nicht bekannt, dass die Bytedaten ein Gitter darstellen, geschweige denn, dass es sich um ein bestimmtes Gitterformat handelt, das von einer anderen Anwendung exportiert wurde!</span><span class="sxs-lookup"><span data-stu-id="71100-167">Our simple **BasicReaderWriter** type above simply reads the data in as a byte stream; it doesn't know that the byte data represents a mesh, much less a specific mesh format as exported by another application!</span></span> <span data-ttu-id="71100-168">Sie müssen die Konvertierung durchführen, wenn Sie die Gitterdaten in den Arbeitsspeicher stellen.</span><span class="sxs-lookup"><span data-stu-id="71100-168">You must perform the conversion as you bring the mesh data into memory.</span></span>

<span data-ttu-id="71100-169">(Sie sollten stets versuchen, Objektdaten in einem Format zu verpacken, das möglichst genau mit der internen Darstellung übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="71100-169">(You should always try to package asset data in a format that's as close to the internal representation as possible.</span></span> <span data-ttu-id="71100-170">Dadurch wird der Ressourceneinsatz verringert und Zeit gespart.)</span><span class="sxs-lookup"><span data-stu-id="71100-170">Doing so will reduce resource utilization and save time.)</span></span>

<span data-ttu-id="71100-171">Als Nächstes werden die Bytedaten aus der Datei des Gitters abgerufen.</span><span class="sxs-lookup"><span data-stu-id="71100-171">Let's get the byte data from the mesh's file.</span></span> <span data-ttu-id="71100-172">Im Beispiel wird angenommen, dass die Datei in einem speziellen Format für Beispiele vorliegt und die Erweiterung ".vbo" aufweist.</span><span class="sxs-lookup"><span data-stu-id="71100-172">The format in the example assumes that the file is a sample-specific format suffixed with .vbo.</span></span> <span data-ttu-id="71100-173">(Wieder gilt, dass dieses Format nicht dem OpenGL-VBO-Format entspricht.) Jeder Vertex ist selbst dem **BasicVertex**-Typ zugeordnet. Dies ist eine Struktur, die im Code für das Konvertierungstool obj2vbo definiert ist.</span><span class="sxs-lookup"><span data-stu-id="71100-173">(Again, this format is not the same as OpenGL's VBO format.) Each vertex itself maps to the **BasicVertex** type, which is a struct defined in the code for the obj2vbo converter tool.</span></span> <span data-ttu-id="71100-174">Die Vertexdaten in der VBO-Datei haben das folgende Layout:</span><span class="sxs-lookup"><span data-stu-id="71100-174">The layout of the vertex data in the .vbo file looks like this:</span></span>

-   <span data-ttu-id="71100-175">Die ersten 32Bits (4Byte) des Datenstroms enthalten die Anzahl an Vertices (numVertices) im Gitter, dargestellt als uint32-Wert.</span><span class="sxs-lookup"><span data-stu-id="71100-175">The first 32 bits (4 bytes) of the data stream contain the number of vertices (numVertices) in the mesh, represented as a uint32 value.</span></span>
-   <span data-ttu-id="71100-176">Die nächsten 32 Bits (4 Byte) des Datenstroms enthalten die Anzahl an Indizes (numIndices) im Gitter, dargestellt als uint32-Wert.</span><span class="sxs-lookup"><span data-stu-id="71100-176">The next 32 bits (4 bytes) of the data stream contain the number of indices in the mesh (numIndices), represented as a uint32 value.</span></span>
-   <span data-ttu-id="71100-177">Die nachfolgenden Bits (numVertices \* sizeof(**BasicVertex**)) enthalten die Vertexdaten.</span><span class="sxs-lookup"><span data-stu-id="71100-177">After that, the subsequent (numVertices \* sizeof(**BasicVertex**)) bits contain the vertex data.</span></span>
-   <span data-ttu-id="71100-178">Die letzten Bits (numIndices \* 16) enthalten die Indexdaten, dargestellt als Abfolge von uint16-Werten.</span><span class="sxs-lookup"><span data-stu-id="71100-178">The last (numIndices \* 16) bits of data contain the index data, represented as a sequence of uint16 values.</span></span>

<span data-ttu-id="71100-179">Entscheidend ist: Sie sollten das Bitebenenlayout der geladenen Gitterdaten kennen.</span><span class="sxs-lookup"><span data-stu-id="71100-179">The point is this: know the bit-level layout of the mesh data you have loaded.</span></span> <span data-ttu-id="71100-180">Stellen Sie außerdem sicher, dass für Endian-Konsistenz gesorgt ist.</span><span class="sxs-lookup"><span data-stu-id="71100-180">Also, be sure you are consistent with endian-ness.</span></span> <span data-ttu-id="71100-181">Alle Windows8-Plattformen sind little Endian.</span><span class="sxs-lookup"><span data-stu-id="71100-181">All Windows8 platforms are little-endian.</span></span>

<span data-ttu-id="71100-182">Im Beispiel wird die „CreateMesh“-Methode aus der **LoadMeshAsync**-Methode aufgerufen, um diese Interpretation auf Bitebene durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="71100-182">In the example, you call a method, CreateMesh, from the **LoadMeshAsync** method to perform this bit-level interpretation.</span></span>

```cpp
task<void> BasicLoader::LoadMeshAsync(
    _In_ Platform::String^ filename,
    _Out_ ID3D11Buffer** vertexBuffer,
    _Out_ ID3D11Buffer** indexBuffer,
    _Out_opt_ uint32* vertexCount,
    _Out_opt_ uint32* indexCount
    )
{
    return m_basicReaderWriter->ReadDataAsync(filename).then([=](const Platform::Array<byte>^ meshData)
    {
        CreateMesh(
            meshData->Data,
            vertexBuffer,
            indexBuffer,
            vertexCount,
            indexCount,
            filename
            );
    });
}
```

<span data-ttu-id="71100-183">**CreateMesh** interpretiert die aus der Datei geladenen Bytedaten und erstellt einen Vertex- und einen Indexpuffer für das Gitter, indem die Vertex- bzw. Indexliste an [**ID3D11Device::CreateBuffer**](https://msdn.microsoft.com/library/windows/desktop/ff476501) übergeben werden und entweder D3D11\_BIND\_VERTEX\_BUFFER oder D3D11\_BIND\_INDEX\_BUFFER angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="71100-183">**CreateMesh** interprets the byte data loaded from the file, and creates a vertex buffer and an index buffer for the mesh by passing the vertex and index lists, respectively, to [**ID3D11Device::CreateBuffer**](https://msdn.microsoft.com/library/windows/desktop/ff476501) and specifying either D3D11\_BIND\_VERTEX\_BUFFER or D3D11\_BIND\_INDEX\_BUFFER.</span></span> <span data-ttu-id="71100-184">In **BasicLoader** wird der folgende Code verwendet:</span><span class="sxs-lookup"><span data-stu-id="71100-184">Here's the code used in **BasicLoader**:</span></span>

```cpp
void BasicLoader::CreateMesh(
    _In_ byte* meshData,
    _Out_ ID3D11Buffer** vertexBuffer,
    _Out_ ID3D11Buffer** indexBuffer,
    _Out_opt_ uint32* vertexCount,
    _Out_opt_ uint32* indexCount,
    _In_opt_ Platform::String^ debugName
    )
{
    // The first 4 bytes of the BasicMesh format define the number of vertices in the mesh.
    uint32 numVertices = *reinterpret_cast<uint32*>(meshData);

    // The following 4 bytes define the number of indices in the mesh.
    uint32 numIndices = *reinterpret_cast<uint32*>(meshData + sizeof(uint32));

    // The next segment of the BasicMesh format contains the vertices of the mesh.
    BasicVertex* vertices = reinterpret_cast<BasicVertex*>(meshData + sizeof(uint32) * 2);

    // The last segment of the BasicMesh format contains the indices of the mesh.
    uint16* indices = reinterpret_cast<uint16*>(meshData + sizeof(uint32) * 2 + sizeof(BasicVertex) * numVertices);

    // Create the vertex and index buffers with the mesh data.

    D3D11_SUBRESOURCE_DATA vertexBufferData = {0};
    vertexBufferData.pSysMem = vertices;
    vertexBufferData.SysMemPitch = 0;
    vertexBufferData.SysMemSlicePitch = 0;
    CD3D11_BUFFER_DESC vertexBufferDesc(numVertices * sizeof(BasicVertex), D3D11_BIND_VERTEX_BUFFER);

    m_d3dDevice->CreateBuffer(
            &vertexBufferDesc,
            &vertexBufferData,
            vertexBuffer
            );
    
    D3D11_SUBRESOURCE_DATA indexBufferData = {0};
    indexBufferData.pSysMem = indices;
    indexBufferData.SysMemPitch = 0;
    indexBufferData.SysMemSlicePitch = 0;
    CD3D11_BUFFER_DESC indexBufferDesc(numIndices * sizeof(uint16), D3D11_BIND_INDEX_BUFFER);
    
    m_d3dDevice->CreateBuffer(
            &indexBufferDesc,
            &indexBufferData,
            indexBuffer
            );
  
    if (vertexCount != nullptr)
    {
        *vertexCount = numVertices;
    }
    if (indexCount != nullptr)
    {
        *indexCount = numIndices;
    }
}
```

<span data-ttu-id="71100-185">Normalerweise erstellen Sie für jedes im Spiel eingesetzte Gitter ein Vertex/Index-Pufferpaar.</span><span class="sxs-lookup"><span data-stu-id="71100-185">You typically create a vertex/index buffer pair for every mesh you use in your game.</span></span> <span data-ttu-id="71100-186">Wo und wann Sie die Gitter laden, ist Ihre Entscheidung.</span><span class="sxs-lookup"><span data-stu-id="71100-186">Where and when you load the meshes is up to you.</span></span> <span data-ttu-id="71100-187">Falls Sie viele Gitter verwenden, kann es ratsam sein, nur an bestimmten Stellen im Spiel einige dieser Gitter vom Datenträger zu laden, z.B. während spezieller vordefinierter Ladezustände.</span><span class="sxs-lookup"><span data-stu-id="71100-187">If you have a lot of meshes, you may only want to load some from the disk at specific points in the game, such as during specific, pre-defined loading states.</span></span> <span data-ttu-id="71100-188">Für große Gitter, z.B. Geländedaten, können Sie die Vertices per Datenstrom aus einem Cache laden. Das ist jedoch eine komplexere Prozedur, die den Rahmen dieses Themas sprengt.</span><span class="sxs-lookup"><span data-stu-id="71100-188">For large meshes, like terrain data, you can stream the vertices from a cache, but that is a more complex procedure and not in the scope of this topic.</span></span>

<span data-ttu-id="71100-189">Wieder gilt: Es ist wichtig, dass Sie mit dem Format Ihrer Vertexdaten vertraut sind!</span><span class="sxs-lookup"><span data-stu-id="71100-189">Again, know your vertex data format!</span></span> <span data-ttu-id="71100-190">Es gibt sehr viele Möglichkeiten, Vertexdaten in den Tools darzustellen, die zum Erstellen von Modellen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="71100-190">There are many, many ways to represent vertex data across the tools used to create models.</span></span> <span data-ttu-id="71100-191">Außerdem haben Sie viele unterschiedliche Optionen, was die Darstellung des Eingabelayouts der Vertexdaten für Direct3D betrifft, z.B. Dreieckslisten und -ketten.</span><span class="sxs-lookup"><span data-stu-id="71100-191">There are also many different ways to represent the input layout of the vertex data to Direct3D, such as triangle lists and strips.</span></span> <span data-ttu-id="71100-192">Weitere Informationen zu Vertexdaten finden Sie unter [Einführung in Puffer in Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476898) und [Grundtypen](https://msdn.microsoft.com/library/windows/desktop/bb147291).</span><span class="sxs-lookup"><span data-stu-id="71100-192">For more information about vertex data, read [Introduction to Buffers in Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476898) and [Primitives](https://msdn.microsoft.com/library/windows/desktop/bb147291).</span></span>

<span data-ttu-id="71100-193">Als Nächstes sehen wir uns das Laden von Texturen an.</span><span class="sxs-lookup"><span data-stu-id="71100-193">Next, let's look at loading textures.</span></span>

### <a name="loading-textures"></a><span data-ttu-id="71100-194">Laden von Texturen</span><span class="sxs-lookup"><span data-stu-id="71100-194">Loading textures</span></span>

<span data-ttu-id="71100-195">Das am häufigsten in Spielen verwendete Objekt – und das Objekt mit den meisten Dateien auf dem Datenträger und im Arbeitsspeicher – sind Texturen.</span><span class="sxs-lookup"><span data-stu-id="71100-195">The most common asset in a game—and the one that comprises most of the files on disk and in memory—are textures.</span></span> <span data-ttu-id="71100-196">Wie Gitter auch, können Texturen in vielen unterschiedlichen Formaten vorliegen, und Sie können Texturen in ein Format konvertieren, das von Direct3D beim Laden verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="71100-196">Like meshes, textures can come in a variety of formats, and you convert them to a format that Direct3D can use when you load them.</span></span> <span data-ttu-id="71100-197">Außerdem gibt es viele verschiedene Arten von Texturen, die zum Erzeugen unterschiedlicher Effekte eingesetzt werden.</span><span class="sxs-lookup"><span data-stu-id="71100-197">Textures also come in a wide variety of types and are used to create different effects.</span></span> <span data-ttu-id="71100-198">MIP-Ebenen für Texturen können verwendet werden, um das Aussehen und die Leistung von entfernten Objekten zu verbessern. Verschmutzungs- und Beleuchtungsmaps werden verwendet, um Effekte und Details über einer Basistextur anzuordnen. Normale Maps werden zur Berechnung der Beleuchtung pro Pixel eingesetzt.</span><span class="sxs-lookup"><span data-stu-id="71100-198">MIP levels for textures can be used to improve the look and performance of distance objects; dirt and light maps are used to layer effects and detail atop a base texture; and normal maps are used in per-pixel lighting calculations.</span></span> <span data-ttu-id="71100-199">In modernen Spielen kann eine typische Szene über Tausende einzelner Texturen verfügen, die im Code alle effektiv verwaltet werden müssen!</span><span class="sxs-lookup"><span data-stu-id="71100-199">In a modern game, a typical scene can potentially have thousands of individual textures, and your code must effectively manage them all!</span></span>

<span data-ttu-id="71100-200">Wieder analog zu Gittern gibt es einige spezielle Formate, die mit dem Ziel einer effizienteren Arbeitsspeichernutzung eingesetzt werden.</span><span class="sxs-lookup"><span data-stu-id="71100-200">Also like meshes, there are a number of specific formats that are used to make memory usage for efficient.</span></span> <span data-ttu-id="71100-201">Da für Texturen häufig ein großer Anteil des GPU-Speichers (und Systemspeichers) verbraucht wird, werden diese Daten meist komprimiert.</span><span class="sxs-lookup"><span data-stu-id="71100-201">Since textures can easily consume a large portion of the GPU (and system) memory, they are often compressed in some fashion.</span></span> <span data-ttu-id="71100-202">Es besteht keine Notwendigkeit, für die Texturen Ihres Spiels die Komprimierung zu verwenden. Sie können beliebige Algorithmen für die Komprimierung bzw. Dekomprimierung nutzen, solange Sie für die Direct3D-Shader Daten in einem geeigneten Format bereitstellen (z.B. eine [**Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff476635)-Bitmap).</span><span class="sxs-lookup"><span data-stu-id="71100-202">You aren't required to use compression on your game's textures, and you can use any compression/decompression algorithm(s) you want as long as you provide the Direct3D shaders with data in a format it can understand (like a [**Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff476635) bitmap).</span></span>

<span data-ttu-id="71100-203">Direct3D bietet Unterstützung für die DXT-Texturkomprimierungsalgorithmen. Es kann jedoch sein, dass nicht alle DXT-Formate von der Grafikhardware des Spielers unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="71100-203">Direct3D provides support for the DXT texture compression algorithms, although every DXT format may not be supported in the player's graphics hardware.</span></span> <span data-ttu-id="71100-204">DDS-Dateien enthalten DXT-Texturen (sowie andere Texturkomprimierungsformate) und weisen die Erweiterung ".dds" auf.</span><span class="sxs-lookup"><span data-stu-id="71100-204">DDS files contain DXT textures (and other texture compression formats as well), and are suffixed with .dds.</span></span>

<span data-ttu-id="71100-205">Eine DDS-Datei ist eine Binärdatei mit den folgenden Informationen:</span><span class="sxs-lookup"><span data-stu-id="71100-205">A DDS file is a binary file that contains the following information:</span></span>

-   <span data-ttu-id="71100-206">DWORD ("Magic Number") mit dem vierstelligen Codewert "DDS" (0x20534444)</span><span class="sxs-lookup"><span data-stu-id="71100-206">A DWORD (magic number) containing the four character code value 'DDS ' (0x20534444).</span></span>

-   <span data-ttu-id="71100-207">Beschreibung der Daten in der Datei</span><span class="sxs-lookup"><span data-stu-id="71100-207">A description of the data in the file.</span></span>

    <span data-ttu-id="71100-208">Die Daten werden mit einer Headerbeschreibung per [**DDS\_HEADER**](https://msdn.microsoft.com/library/windows/desktop/bb943982) beschrieben. Das Pixelformat wird mit [**DDS\_PIXELFORMAT**](https://msdn.microsoft.com/library/windows/desktop/bb943984) definiert.</span><span class="sxs-lookup"><span data-stu-id="71100-208">The data is described with a header description using [**DDS\_HEADER**](https://msdn.microsoft.com/library/windows/desktop/bb943982); the pixel format is defined using [**DDS\_PIXELFORMAT**](https://msdn.microsoft.com/library/windows/desktop/bb943984).</span></span> <span data-ttu-id="71100-209">Beachten Sie, dass die Strukturen **DDS\_HEADER** und **DDS\_PIXELFORMAT** die veralteten DirectDraw7-Strukturen „DDSURFACEDESC2“, „DDSCAPS2“ und „DDPIXELFORMAT“ ersetzen.</span><span class="sxs-lookup"><span data-stu-id="71100-209">Note that the **DDS\_HEADER** and **DDS\_PIXELFORMAT** structures replace the deprecated DDSURFACEDESC2, DDSCAPS2 and DDPIXELFORMAT DirectDraw 7 structures.</span></span> <span data-ttu-id="71100-210">**DDS\_HEADER** ist die binäre Entsprechung von DDSURFACEDESC2 und DDSCAPS2.</span><span class="sxs-lookup"><span data-stu-id="71100-210">**DDS\_HEADER** is the binary equivalent of DDSURFACEDESC2 and DDSCAPS2.</span></span> <span data-ttu-id="71100-211">**DDS\_PIXELFORMAT** ist die binäre Entsprechung von DDPIXELFORMAT.</span><span class="sxs-lookup"><span data-stu-id="71100-211">**DDS\_PIXELFORMAT** is the binary equivalent of DDPIXELFORMAT.</span></span>

    ```cpp
    DWORD               dwMagic;
    DDS_HEADER          header;
    ```

    <span data-ttu-id="71100-212">Wenn der Wert von **dwFlags** in [**DDS\_PIXELFORMAT**](https://msdn.microsoft.com/library/windows/desktop/bb943984) auf DDPF\_FOURCC und **dwFourCC** auf „DX10“ festgelegt ist, ist eine zusätzliche [**DDS\_HEADER\_DXT10**](https://msdn.microsoft.com/library/windows/desktop/bb943983)-Struktur vorhanden. Darin werden Texturarrays oder DXGI-Formate aufgenommen, die nicht als RGB-Pixelformat ausgedrückt werden können, z.B. Gleitkommaformate, sRGB-Formate usw. Wenn die **DDS\_HEADER\_DXT10**-Struktur vorhanden ist, sieht die gesamte Datenbeschreibung wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="71100-212">If the value of **dwFlags** in [**DDS\_PIXELFORMAT**](https://msdn.microsoft.com/library/windows/desktop/bb943984) is set to DDPF\_FOURCC and **dwFourCC** is set to "DX10" an additional [**DDS\_HEADER\_DXT10**](https://msdn.microsoft.com/library/windows/desktop/bb943983) structure will be present to accommodate texture arrays or DXGI formats that cannot be expressed as an RGB pixel format such as floating point formats, sRGB formats etc. When the **DDS\_HEADER\_DXT10** structure is present, the entire data description will looks like this.</span></span>

    ```cpp
    DWORD               dwMagic;
    DDS_HEADER          header;
    DDS_HEADER_DXT10    header10;
    ```

-   <span data-ttu-id="71100-213">Ein Zeiger auf ein Bytearray, in dem die Hauptoberflächendaten enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="71100-213">A pointer to an array of bytes that contains the main surface data.</span></span>
    ```cpp
    BYTE bdata[]
    ```

-   <span data-ttu-id="71100-214">Ein Zeiger auf ein Bytearray, in dem die verbleibenden Oberflächen enthalten sind, z.B. Mipmap-Ebenen, Seiten einer Würfelmap, Tiefen in einer Volumentextur.</span><span class="sxs-lookup"><span data-stu-id="71100-214">A pointer to an array of bytes that contains the remaining surfaces such as; mipmap levels, faces in a cube map, depths in a volume texture.</span></span> <span data-ttu-id="71100-215">Weitere Informationen zum Layout der DDS-Datei finden Sie unter den folgenden Links: [texture](https://msdn.microsoft.com/library/windows/desktop/bb205578) [Cubemap](https://msdn.microsoft.com/library/windows/desktop/bb205577) oder [Volumentextur](https://msdn.microsoft.com/library/windows/desktop/bb205579).</span><span class="sxs-lookup"><span data-stu-id="71100-215">Follow these links for more information about the DDS file layout for a: [texture](https://msdn.microsoft.com/library/windows/desktop/bb205578), a [cube map](https://msdn.microsoft.com/library/windows/desktop/bb205577), or a [volume texture](https://msdn.microsoft.com/library/windows/desktop/bb205579).</span></span>

    ```cpp
    BYTE bdata2[]
    ```

<span data-ttu-id="71100-216">In vielen Tools erfolgt der Export im DDS-Format.</span><span class="sxs-lookup"><span data-stu-id="71100-216">Many tools export to the DDS format.</span></span> <span data-ttu-id="71100-217">Falls Sie nicht über ein Tool verfügen, mit dem Exporte der Textur in diesem Format möglich sind, können Sie ein Tool erstellen.</span><span class="sxs-lookup"><span data-stu-id="71100-217">If you don't have a tool to export your texture to this format, consider creating one.</span></span> <span data-ttu-id="71100-218">Weitere Informationen zum DDS-Format und zur Verwendung im Code finden Sie unter [Programmieranleitung für DDS](https://msdn.microsoft.com/library/windows/desktop/bb943991).</span><span class="sxs-lookup"><span data-stu-id="71100-218">For more detail on the DDS format and how to work with it in your code, read [Programming Guide for DDS](https://msdn.microsoft.com/library/windows/desktop/bb943991).</span></span> <span data-ttu-id="71100-219">In unserem Beispiel wird DDS verwendet.</span><span class="sxs-lookup"><span data-stu-id="71100-219">In our example, we'll use DDS.</span></span>

<span data-ttu-id="71100-220">Wie bei anderen Ressourcentypen auch, lesen Sie die Daten aus einer Datei als Bytestream aus.</span><span class="sxs-lookup"><span data-stu-id="71100-220">As with other resource types, you read the data from a file as a stream of bytes.</span></span> <span data-ttu-id="71100-221">Nachdem die Aufgabe für den Ladevorgang abgeschlossen ist, führt der Lambda-Aufruf Code aus (**CreateTexture**-Methode), um den Bytestream in ein für Direct3D geeignetes Format zu bringen.</span><span class="sxs-lookup"><span data-stu-id="71100-221">Once your loading task completes, the lambda call runs code (the **CreateTexture** method) to process the stream of bytes into a format that Direct3D can use.</span></span>

```cpp
task<void> BasicLoader::LoadTextureAsync(
    _In_ Platform::String^ filename,
    _Out_opt_ ID3D11Texture2D** texture,
    _Out_opt_ ID3D11ShaderResourceView** textureView
    )
{
    return m_basicReaderWriter->ReadDataAsync(filename).then([=](const Platform::Array<byte>^ textureData)
    {
        CreateTexture(
            GetExtension(filename) == "dds",
            textureData->Data,
            textureData->Length,
            texture,
            textureView,
            filename
            );
    });
}
```

<span data-ttu-id="71100-222">Im vorherigen Codeausschnitt wird mit der Lambda-Funktion geprüft, ob der Dateiname die Erweiterung "dds" aufweist.</span><span class="sxs-lookup"><span data-stu-id="71100-222">In the previous snippet, the lambda checks to see if the filename has an extension of "dds".</span></span> <span data-ttu-id="71100-223">Wenn ja, wird angenommen, dass es sich um eine DDS-Textur handelt.</span><span class="sxs-lookup"><span data-stu-id="71100-223">If it does, you assume that it is a DDS texture.</span></span> <span data-ttu-id="71100-224">Wenn nicht, verwenden Sie die Windows-Bilderstellungskomponenten-APIs (WIC), um das Format zu ermitteln und die Daten als Bitmap zu decodieren.</span><span class="sxs-lookup"><span data-stu-id="71100-224">If not, well, use the Windows Imaging Component (WIC) APIs to discover the format and decode the data as a bitmap.</span></span> <span data-ttu-id="71100-225">In beiden Fällen ist das Ergebnis eine [**Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff476635)-Bitmap (oder ein Fehler).</span><span class="sxs-lookup"><span data-stu-id="71100-225">Either way, the result is a [**Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff476635) bitmap (or an error).</span></span>

```cpp
void BasicLoader::CreateTexture(
    _In_ bool decodeAsDDS,
    _In_reads_bytes_(dataSize) byte* data,
    _In_ uint32 dataSize,
    _Out_opt_ ID3D11Texture2D** texture,
    _Out_opt_ ID3D11ShaderResourceView** textureView,
    _In_opt_ Platform::String^ debugName
    )
{
    ComPtr<ID3D11ShaderResourceView> shaderResourceView;
    ComPtr<ID3D11Texture2D> texture2D;

    if (decodeAsDDS)
    {
        ComPtr<ID3D11Resource> resource;

        if (textureView == nullptr)
        {
            CreateDDSTextureFromMemory(
                m_d3dDevice.Get(),
                data,
                dataSize,
                &resource,
                nullptr
                );
        }
        else
        {
            CreateDDSTextureFromMemory(
                m_d3dDevice.Get(),
                data,
                dataSize,
                &resource,
                &shaderResourceView
                );
        }

        resource.As(&texture2D);
    }
    else
    {
        if (m_wicFactory.Get() == nullptr)
        {
            // A WIC factory object is required in order to load texture
            // assets stored in non-DDS formats.  If BasicLoader was not
            // initialized with one, create one as needed.
            CoCreateInstance(
                    CLSID_WICImagingFactory,
                    nullptr,
                    CLSCTX_INPROC_SERVER,
                    IID_PPV_ARGS(&m_wicFactory));
        }

        ComPtr<IWICStream> stream;
        m_wicFactory->CreateStream(&stream);

        stream->InitializeFromMemory(
                data,
                dataSize);

        ComPtr<IWICBitmapDecoder> bitmapDecoder;
        m_wicFactory->CreateDecoderFromStream(
                stream.Get(),
                nullptr,
                WICDecodeMetadataCacheOnDemand,
                &bitmapDecoder);

        ComPtr<IWICBitmapFrameDecode> bitmapFrame;
        bitmapDecoder->GetFrame(0, &bitmapFrame);

        ComPtr<IWICFormatConverter> formatConverter;
        m_wicFactory->CreateFormatConverter(&formatConverter);

        formatConverter->Initialize(
                bitmapFrame.Get(),
                GUID_WICPixelFormat32bppPBGRA,
                WICBitmapDitherTypeNone,
                nullptr,
                0.0,
                WICBitmapPaletteTypeCustom);

        uint32 width;
        uint32 height;
        bitmapFrame->GetSize(&width, &height);

        std::unique_ptr<byte[]> bitmapPixels(new byte[width * height * 4]);
        formatConverter->CopyPixels(
                nullptr,
                width * 4,
                width * height * 4,
                bitmapPixels.get());

        D3D11_SUBRESOURCE_DATA initialData;
        ZeroMemory(&initialData, sizeof(initialData));
        initialData.pSysMem = bitmapPixels.get();
        initialData.SysMemPitch = width * 4;
        initialData.SysMemSlicePitch = 0;

        CD3D11_TEXTURE2D_DESC textureDesc(
            DXGI_FORMAT_B8G8R8A8_UNORM,
            width,
            height,
            1,
            1
            );

        m_d3dDevice->CreateTexture2D(
                &textureDesc,
                &initialData,
                &texture2D);

        if (textureView != nullptr)
        {
            CD3D11_SHADER_RESOURCE_VIEW_DESC shaderResourceViewDesc(
                texture2D.Get(),
                D3D11_SRV_DIMENSION_TEXTURE2D
                );

            m_d3dDevice->CreateShaderResourceView(
                    texture2D.Get(),
                    &shaderResourceViewDesc,
                    &shaderResourceView);
        }
    }


    if (texture != nullptr)
    {
        *texture = texture2D.Detach();
    }
    if (textureView != nullptr)
    {
        *textureView = shaderResourceView.Detach();
    }
}
```

<span data-ttu-id="71100-226">Nach Abschluss dieses Codes befindet sich ein [**Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff476635)-Objekt im Arbeitsspeicher, das aus einer Bilddatei geladen wurde.</span><span class="sxs-lookup"><span data-stu-id="71100-226">When this code completes, you have a [**Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff476635) in memory, loaded from an image file.</span></span> <span data-ttu-id="71100-227">Wie bei Gittern auch, enthalten Ihr Spiel und die einzelnen Szenen eine große Zahl dieser Objekte.</span><span class="sxs-lookup"><span data-stu-id="71100-227">As with meshes, you probably have a lot of them in your game and in any given scene.</span></span> <span data-ttu-id="71100-228">Es ist ratsam, pro Szene oder Level Caches für Texturen einzurichten, auf die regelmäßig zugegriffen wird, anstatt alle Texturen zu Beginn des Spiels oder eines Levels zu laden.</span><span class="sxs-lookup"><span data-stu-id="71100-228">Consider creating caches for regularly accessed textures per-scene or per-level, rather than loading them all when the game or level starts.</span></span>

<span data-ttu-id="71100-229">(Die **CreateDDSTextureFromMemory**-Methode, die im obigen Beispiel aufgerufen wird, ist in ganzer Länge unter [Vollständiger Code für DDSTextureLoader](complete-code-for-ddstextureloader.md) zu finden.)</span><span class="sxs-lookup"><span data-stu-id="71100-229">(The **CreateDDSTextureFromMemory** method called in the above sample can be explored in full in [Complete code for DDSTextureLoader](complete-code-for-ddstextureloader.md).)</span></span>

<span data-ttu-id="71100-230">Außerdem können einzelne Texturen oder Texturdesigns bestimmten Gitterpolygonen oder Oberflächen zugeordnet sein.</span><span class="sxs-lookup"><span data-stu-id="71100-230">Also, individual textures or texture "skins" may map to specific mesh polygons or surfaces.</span></span> <span data-ttu-id="71100-231">Diese Zuordnungsdaten werden normalerweise mit dem Tool exportiert, das von einem Spezialisten oder Designer zum Erstellen des Modells und der Texturen verwendet wurde.</span><span class="sxs-lookup"><span data-stu-id="71100-231">This mapping data is usually exported by the tool an artist or designer used to create the model and the textures.</span></span> <span data-ttu-id="71100-232">Stellen Sie sicher, dass Sie beim Laden der exportierten Daten auch diese Informationen erfassen. Sie benötigen diese Daten, um die richtigen Texturen den entsprechenden Oberflächen zuzuordnen, wenn Sie die Fragmentschattierung erstellen.</span><span class="sxs-lookup"><span data-stu-id="71100-232">Make sure that you capture this information as well when you load the exported data, as you will use it map the correct textures to the corresponding surfaces when you perform fragment shading.</span></span>

### <a name="loading-shaders"></a><span data-ttu-id="71100-233">Laden von Shadern</span><span class="sxs-lookup"><span data-stu-id="71100-233">Loading shaders</span></span>

<span data-ttu-id="71100-234">Bei Shadern handelt es sich um kompilierte High Level Shader Language (HLSL)-Dateien, die in den Arbeitsspeicher geladen und an bestimmten Stellen der Grafikpipeline aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="71100-234">Shaders are compiled High Level Shader Language (HLSL) files that are loaded into memory and invoked at specific stages of the graphics pipeline.</span></span> <span data-ttu-id="71100-235">Die am häufigsten verwendeten und wichtigsten Shader sind die Vertex- und Pixel-Shader, mit denen die einzelnen Vertices des Gitters bzw. die Pixel in den Viewports der Szenen verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="71100-235">The most common and essential shaders are the vertex and pixel shaders, which process the individual vertices of your mesh and the pixels in the scene's viewport(s), respectively.</span></span> <span data-ttu-id="71100-236">Der HLSL-Code wird ausgeführt, um die Geometrie zu transformieren, Beleuchtungseffekte und Texturen anzuwenden und die Nachbearbeitung der gerenderten Szene durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="71100-236">The HLSL code is executed to transform the geometry, apply lighting effects and textures, and perform post-processing on the rendered scene.</span></span>

<span data-ttu-id="71100-237">Ein Direct3D-Spiel kann über eine Reihe unterschiedlicher Shader verfügen, die jeweils zu einer separaten CSO-Datei (Compiled Shader Object, .cso) kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="71100-237">A Direct3D game can have a number of different shaders, each one compiled into a separate CSO (Compiled Shader Object, .cso) file.</span></span> <span data-ttu-id="71100-238">Normalerweise sind nicht so viele Dateien vorhanden, dass diese dynamisch geladen werden müssen. In den meisten Fällen können Sie die Dateien einfach zu Beginn des Spiels oder pro Level (z. B. einen Shader für Regeneffekte) laden.</span><span class="sxs-lookup"><span data-stu-id="71100-238">Normally, you don't have so many that you need to load them dynamically, and in most cases, you can simply load them when the game is starting, or on a per-level basis (such as a shader for rain effects).</span></span>

<span data-ttu-id="71100-239">Im Code der **BasicLoader**-Klasse werden einige Überladungen für unterschiedliche Shader bereitgestellt, einschließlich Vertex-, Geometry-, Pixel- und Hull-Shader.</span><span class="sxs-lookup"><span data-stu-id="71100-239">The code in the **BasicLoader** class provides a number of overloads for different shaders, including vertex, geometry, pixel, and hull shaders.</span></span> <span data-ttu-id="71100-240">Im folgenden Code ist ein Beispiel für Pixel-Shader enthalten.</span><span class="sxs-lookup"><span data-stu-id="71100-240">The code below covers pixel shaders as an example.</span></span> <span data-ttu-id="71100-241">(Den gesamten Code finden Sie unter [Vollständiger Code für BasicLoader](complete-code-for-basicloader.md).)</span><span class="sxs-lookup"><span data-stu-id="71100-241">(You can review the complete code in [Complete code for BasicLoader](complete-code-for-basicloader.md).)</span></span>

```cpp
concurrency::task<void> LoadShaderAsync(
    _In_ Platform::String^ filename,
    _Out_ ID3D11PixelShader** shader
    );

// ...

task<void> BasicLoader::LoadShaderAsync(
    _In_ Platform::String^ filename,
    _Out_ ID3D11PixelShader** shader
    )
{
    return m_basicReaderWriter->ReadDataAsync(filename).then([=](const Platform::Array<byte>^ bytecode)
    {
        
       m_d3dDevice->CreatePixelShader(
                bytecode->Data,
                bytecode->Length,
                nullptr,
                shader);
    });
}

```

<span data-ttu-id="71100-242">In diesem Beispiel verwenden Sie die **BasicReaderWriter**-Instanz (**m\_basicReaderWriter**), um die bereitgestellte kompilierte Shaderobjektdatei (.cso) als Bytestream einzulesen.</span><span class="sxs-lookup"><span data-stu-id="71100-242">In this example, you use the **BasicReaderWriter** instance (**m\_basicReaderWriter**) to read in the supplied compiled shader object (.cso) file as a byte stream.</span></span> <span data-ttu-id="71100-243">Nach Abschluss der Aufgabe ruft die Lambda-Funktion [**ID3D11Device::CreatePixelShader**](https://msdn.microsoft.com/library/windows/desktop/ff476513) mit den aus der Datei geladenen Bytedaten auf.</span><span class="sxs-lookup"><span data-stu-id="71100-243">Once that task completes, the lambda calls [**ID3D11Device::CreatePixelShader**](https://msdn.microsoft.com/library/windows/desktop/ff476513) with the byte data loaded from the file.</span></span> <span data-ttu-id="71100-244">In Ihrem Rückruf muss ein Kennzeichen dafür festgelegt werden, dass der Ladevorgang erfolgreich war, und der Code muss dieses Kennzeichen überprüfen, bevor der Shader ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="71100-244">Your callback must set some flag indicating that the load was successful, and your code must check this flag before running the shader.</span></span>

<span data-ttu-id="71100-245">Vertex-Shader sind etwas komplexer.</span><span class="sxs-lookup"><span data-stu-id="71100-245">Vertex shaders are bit more complex.</span></span> <span data-ttu-id="71100-246">Für einen Vertex-Shader laden Sie zusätzlich ein separates Eingabelayout, mit dem die Vertexdaten definiert werden.</span><span class="sxs-lookup"><span data-stu-id="71100-246">For a vertex shader, you also load a separate input layout that defines the vertex data.</span></span> <span data-ttu-id="71100-247">Mit dem folgenden Code kann ein Vertex-Shader zusammen mit einem benutzerdefinierten Vertexeingabelayout asynchron geladen werden.</span><span class="sxs-lookup"><span data-stu-id="71100-247">The following code can be used to asynchronously load a vertex shader along with a custom vertex input layout.</span></span> <span data-ttu-id="71100-248">Achten Sie darauf, dass die aus den Gittern geladenen Vertexinformationen von diesem Eingabelayout richtig dargestellt werden können!</span><span class="sxs-lookup"><span data-stu-id="71100-248">Be sure that the vertex information that you load from your meshes can be correctly represented by this input layout!</span></span>

<span data-ttu-id="71100-249">Wir erstellen das Eingabelayout, bevor der Vertex-Shader geladen wird.</span><span class="sxs-lookup"><span data-stu-id="71100-249">Let's create the input layout before you load the vertex shader.</span></span>

```cpp
void BasicLoader::CreateInputLayout(
    _In_reads_bytes_(bytecodeSize) byte* bytecode,
    _In_ uint32 bytecodeSize,
    _In_reads_opt_(layoutDescNumElements) D3D11_INPUT_ELEMENT_DESC* layoutDesc,
    _In_ uint32 layoutDescNumElements,
    _Out_ ID3D11InputLayout** layout
    )
{
    if (layoutDesc == nullptr)
    {
        // If no input layout is specified, use the BasicVertex layout.
        const D3D11_INPUT_ELEMENT_DESC basicVertexLayoutDesc[] =
        {
            { "POSITION", 0, DXGI_FORMAT_R32G32B32_FLOAT, 0, 0,  D3D11_INPUT_PER_VERTEX_DATA, 0 },
            { "NORMAL",   0, DXGI_FORMAT_R32G32B32_FLOAT, 0, 12, D3D11_INPUT_PER_VERTEX_DATA, 0 },
            { "TEXCOORD", 0, DXGI_FORMAT_R32G32_FLOAT,    0, 24, D3D11_INPUT_PER_VERTEX_DATA, 0 },
        };

        m_d3dDevice->CreateInputLayout(
                basicVertexLayoutDesc,
                ARRAYSIZE(basicVertexLayoutDesc),
                bytecode,
                bytecodeSize,
                layout);
    }
    else
    {
        m_d3dDevice->CreateInputLayout(
                layoutDesc,
                layoutDescNumElements,
                bytecode,
                bytecodeSize,
                layout);
    }
}
```

<span data-ttu-id="71100-250">In diesem speziellen Layout werden für jeden Vertex vom Vertex-Shader die folgenden Daten verarbeitet:</span><span class="sxs-lookup"><span data-stu-id="71100-250">In this particular layout, each vertex has the following data processed by the vertex shader:</span></span>

-   <span data-ttu-id="71100-251">Eine 3D-Koordinatenposition (x, y, z) im Koordinatenbereich des Modells, dargestellt in Form von drei 32-Bit-Gleitkommawerten.</span><span class="sxs-lookup"><span data-stu-id="71100-251">A 3D coordinate position (x, y, z) in the model's coordinate space, represented as a trio of 32-bit floating point values.</span></span>
-   <span data-ttu-id="71100-252">Ein normaler Vektor für den Vertex, ebenfalls dargestellt in Form von drei 32-Bit-Gleitkommawerten.</span><span class="sxs-lookup"><span data-stu-id="71100-252">A normal vector for the vertex, also represented as three 32-bit floating point values.</span></span>
-   <span data-ttu-id="71100-253">Ein transformierter 2D-Texturkoordinatenwert (u, v), dargestellt als 32-Bit-Gleitkommawertpaar.</span><span class="sxs-lookup"><span data-stu-id="71100-253">A transformed 2D texture coordinate value (u, v) , represented as a pair of 32-bit floating values.</span></span>

<span data-ttu-id="71100-254">Diese Eingabeelemente pro Vertex werden als [HLSL-Semantik](https://msdn.microsoft.com/library/windows/desktop/bb509647) bezeichnet. Es handelt sich dabei um eine Gruppe definierter Register, die zum Übergeben von Daten in das bzw. aus dem kompilierten Shaderobjekt verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="71100-254">These per-vertex input elements are called [HLSL semantics](https://msdn.microsoft.com/library/windows/desktop/bb509647), and they are a set of defined registers used to pass data to and from your compiled shader object.</span></span> <span data-ttu-id="71100-255">Die Pipeline führt den Vertex-Shader einmal für jeden Vertex des geladenen Gitters aus.</span><span class="sxs-lookup"><span data-stu-id="71100-255">Your pipeline runs the vertex shader once for every vertex in the mesh that you've loaded.</span></span> <span data-ttu-id="71100-256">Mit der Semantik wird die Eingabe in den Vertex-Shader (sowie auch die Ausgabe) während der Ausführung definiert, und diese Daten werden dann für die Berechnungen pro Vertex im HLSL-Code des Shaders bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="71100-256">The semantics define the input to (and output from) the vertex shader as it runs, and provide this data for your per-vertex computations in your shader's HLSL code.</span></span>

<span data-ttu-id="71100-257">Laden Sie als Nächstes das Vertex-Shaderobjekt.</span><span class="sxs-lookup"><span data-stu-id="71100-257">Now, load the vertex shader object.</span></span>

```cpp
concurrency::task<void> LoadShaderAsync(
        _In_ Platform::String^ filename,
        _In_reads_opt_(layoutDescNumElements) D3D11_INPUT_ELEMENT_DESC layoutDesc[],
        _In_ uint32 layoutDescNumElements,
        _Out_ ID3D11VertexShader** shader,
        _Out_opt_ ID3D11InputLayout** layout
        );

// ...

task<void> BasicLoader::LoadShaderAsync(
    _In_ Platform::String^ filename,
    _In_reads_opt_(layoutDescNumElements) D3D11_INPUT_ELEMENT_DESC layoutDesc[],
    _In_ uint32 layoutDescNumElements,
    _Out_ ID3D11VertexShader** shader,
    _Out_opt_ ID3D11InputLayout** layout
    )
{
    // This method assumes that the lifetime of input arguments may be shorter
    // than the duration of this task.  In order to ensure accurate results, a
    // copy of all arguments passed by pointer must be made.  The method then
    // ensures that the lifetime of the copied data exceeds that of the task.

    // Create copies of the layoutDesc array as well as the SemanticName strings,
    // both of which are pointers to data whose lifetimes may be shorter than that
    // of this method's task.
    shared_ptr<vector<D3D11_INPUT_ELEMENT_DESC>> layoutDescCopy;
    shared_ptr<vector<string>> layoutDescSemanticNamesCopy;
    if (layoutDesc != nullptr)
    {
        layoutDescCopy.reset(
            new vector<D3D11_INPUT_ELEMENT_DESC>(
                layoutDesc,
                layoutDesc + layoutDescNumElements
                )
            );

        layoutDescSemanticNamesCopy.reset(
            new vector<string>(layoutDescNumElements)
            );

        for (uint32 i = 0; i < layoutDescNumElements; i++)
        {
            layoutDescSemanticNamesCopy->at(i).assign(layoutDesc[i].SemanticName);
        }
    }

    return m_basicReaderWriter->ReadDataAsync(filename).then([=](const Platform::Array<byte>^ bytecode)
    {
       m_d3dDevice->CreateVertexShader(
                bytecode->Data,
                bytecode->Length,
                nullptr,
                shader);

        if (layout != nullptr)
        {
            if (layoutDesc != nullptr)
            {
                // Reassign the SemanticName elements of the layoutDesc array copy to point
                // to the corresponding copied strings. Performing the assignment inside the
                // lambda body ensures that the lambda will take a reference to the shared_ptr
                // that holds the data.  This will guarantee that the data is still valid when
                // CreateInputLayout is called.
                for (uint32 i = 0; i < layoutDescNumElements; i++)
                {
                    layoutDescCopy->at(i).SemanticName = layoutDescSemanticNamesCopy->at(i).c_str();
                }
            }

            CreateInputLayout(
                bytecode->Data,
                bytecode->Length,
                layoutDesc == nullptr ? nullptr : layoutDescCopy->data(),
                layoutDescNumElements,
                layout);   
        }
    });
}

```

<span data-ttu-id="71100-258">In diesem Code erstellen Sie den Vertex-Shader per Aufruf von [**ID3D11Device::CreateVertexShader**](https://msdn.microsoft.com/library/windows/desktop/ff476524), nachdem Sie die Bytedaten für die CSO-Datei des Vertex-Shaders eingelesen haben.</span><span class="sxs-lookup"><span data-stu-id="71100-258">In this code, once you've read in the byte data for the vertex shader's CSO file, you create the vertex shader by calling [**ID3D11Device::CreateVertexShader**](https://msdn.microsoft.com/library/windows/desktop/ff476524).</span></span> <span data-ttu-id="71100-259">Danach erstellen Sie das Eingabelayout für den Shader in derselben Lambda-Funktion.</span><span class="sxs-lookup"><span data-stu-id="71100-259">After that, you create your input layout for the shader in the same lambda.</span></span>

<span data-ttu-id="71100-260">Für andere Arten von Shadern, z.B. Geometry- und Hull-Shader, kann ebenfalls eine spezielle Konfiguration erforderlich sein.</span><span class="sxs-lookup"><span data-stu-id="71100-260">Other shader types, such as hull and geometry shaders, can also require specific configuration.</span></span> <span data-ttu-id="71100-261">Den vollständigen Code für verschiedene Methoden zum Laden von Shadern finden Sie unter [Vollständiger Code für BasicLoader](complete-code-for-basicloader.md) und [Beispiel für das Laden der Direct3D-Ressource]( http://go.microsoft.com/fwlink/p/?LinkID=265132).</span><span class="sxs-lookup"><span data-stu-id="71100-261">Complete code for a variety of shader loading methods is provided in [Complete code for BasicLoader](complete-code-for-basicloader.md) and in the [Direct3D resource loading sample]( http://go.microsoft.com/fwlink/p/?LinkID=265132).</span></span>

## <a name="remarks"></a><span data-ttu-id="71100-262">Hinweise</span><span class="sxs-lookup"><span data-stu-id="71100-262">Remarks</span></span>

<span data-ttu-id="71100-263">Sie sollten jetzt mit den Methoden zum asynchronen Laden häufig verwendeter Ressourcen und Objekte für Spiele, wie Gittern, Texturen und kompilierten Shadern, vertraut sein und diese Methoden erstellen und ändern können.</span><span class="sxs-lookup"><span data-stu-id="71100-263">At this point, you should understand and be able to create or modify methods for asynchronously loading common game resources and assets, such as meshes, textures, and compiled shaders.</span></span>

## <a name="related-topics"></a><span data-ttu-id="71100-264">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="71100-264">Related topics</span></span>

* [<span data-ttu-id="71100-265">Beispiel für das Laden von Direct3D-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="71100-265">Direct3D resource loading sample</span></span>]( http://go.microsoft.com/fwlink/p/?LinkID=265132)
* [<span data-ttu-id="71100-266">Vollständiger Code für „BasicLoader“</span><span class="sxs-lookup"><span data-stu-id="71100-266">Complete code for BasicLoader</span></span>](complete-code-for-basicloader.md)
* [<span data-ttu-id="71100-267">Vollständiger Code für BasicReaderWriter</span><span class="sxs-lookup"><span data-stu-id="71100-267">Complete code for BasicReaderWriter</span></span>](complete-code-for-basicreaderwriter.md)
* [<span data-ttu-id="71100-268">Vollständiger Code für DDSTextureLoader</span><span class="sxs-lookup"><span data-stu-id="71100-268">Complete code for DDSTextureLoader</span></span>](complete-code-for-ddstextureloader.md)

 

 




