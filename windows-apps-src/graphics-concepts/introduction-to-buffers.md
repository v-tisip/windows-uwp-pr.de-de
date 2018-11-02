---
title: Einführung zu Puffern
description: Eine Pufferressource ist eine Sammlung vollständig typisierter Daten, die zu Elementen gruppiert werden.
ms.assetid: 494FDF57-0FBE-434C-B568-06F977B40263
keywords:
- Einführung zu Puffern
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 14e78aec9afa361b2627d62d92f0ee7d7ab0565b
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "5932162"
---
# <a name="introduction-to-buffers"></a><span data-ttu-id="6ebf3-104">Einführung zu Puffern</span><span class="sxs-lookup"><span data-stu-id="6ebf3-104">Introduction to buffers</span></span>


<span data-ttu-id="6ebf3-105">Eine Pufferressource ist eine Sammlung vollständig typisierter Daten, die zu Elementen gruppiert werden.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-105">A buffer resource is a collection of fully typed data, grouped into elements.</span></span> <span data-ttu-id="6ebf3-106">Puffer speichern Daten, wie z.B. Texturkoordinaten in einem *Scheitelpunktpuffer*, Indizes in einem *Indexpuffer*, Shader-Konstantendaten in einem *Konstantenpuffer*, Positionsvektoren, normale Vektoren oder den Gerätezustand.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-106">Buffers store data, such as texture coordinates in a *vertex buffer*, indexes in an *index buffer*, shader constants data in a *constant buffer*, position vectors, normal vectors, or device state.</span></span>

<span data-ttu-id="6ebf3-107">Ein Puffer-Element besteht aus 1 bis 4 Komponenten.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-107">A buffer element is made up of 1 to 4 components.</span></span> <span data-ttu-id="6ebf3-108">Pufferelemente können gepackte Datenwerten (wie R8G8B8A8-Oberflächenwerte), einzelne 8-Bit-Ganzahlen oder vier 32-Bit-Gleitkommawerte enthalten.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-108">Buffer elements can include packed data values (like R8G8B8A8 surface values), single 8-bit integers, or four 32-bit floating point values.</span></span>

<span data-ttu-id="6ebf3-109">Puffer werden als unstrukturierte Ressource erstellt.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-109">A buffer is created as an unstructured resource.</span></span> <span data-ttu-id="6ebf3-110">Da es unstrukturierte handelt, ein Puffer kann keine Mipmap-Ebenen enthalten, es kann nicht beim Lesen gefiltert abzurufen, und es kann nicht mit Multisampling sein.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-110">Because it is unstructured, a buffer cannot contain any mipmap levels, it cannot get filtered when read, and it cannot be multisampled.</span></span>

## <a name="span-idbuffertypesspanspan-idbuffertypesspanspan-idbuffertypesspanbuffer-types"></a><span data-ttu-id="6ebf3-111"><span id="Buffer_Types"></span><span id="buffer_types"></span><span id="BUFFER_TYPES"></span>Puffertypen</span><span class="sxs-lookup"><span data-stu-id="6ebf3-111"><span id="Buffer_Types"></span><span id="buffer_types"></span><span id="BUFFER_TYPES"></span>Buffer Types</span></span>


<span data-ttu-id="6ebf3-112">Im folgenden werden die Puffer-Ressourcentypen von Direct3D 11 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-112">The following are the buffer resource types supported by Direct3D 11.</span></span>

-   [<span data-ttu-id="6ebf3-113">Vertexpuffer</span><span class="sxs-lookup"><span data-stu-id="6ebf3-113">Vertex Buffer</span></span>](#vertex-buffer)
-   [<span data-ttu-id="6ebf3-114">Indexpuffer</span><span class="sxs-lookup"><span data-stu-id="6ebf3-114">Index Buffer</span></span>](#index-buffer)
-   [<span data-ttu-id="6ebf3-115">Konstantenpuffer</span><span class="sxs-lookup"><span data-stu-id="6ebf3-115">Constant Buffer</span></span>](#shader-constant-buffer)

### <a name="span-idvertexbufferspanspan-idvertexbufferspanspan-idvertexbufferspanspan-idvertex-bufferspanvertex-buffer"></a><span data-ttu-id="6ebf3-116"><span id="Vertex_Buffer"></span><span id="vertex_buffer"></span><span id="VERTEX_BUFFER"></span><span id="vertex-buffer"></span>Vertexpuffer</span><span class="sxs-lookup"><span data-stu-id="6ebf3-116"><span id="Vertex_Buffer"></span><span id="vertex_buffer"></span><span id="VERTEX_BUFFER"></span><span id="vertex-buffer"></span>Vertex Buffer</span></span>

<span data-ttu-id="6ebf3-117">Ein Vertexpuffer enthält Scheitelpunktdaten, die zur Definition Ihrer Geometrie verwendet.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-117">A vertex buffer contains the vertex data used to define your geometry.</span></span> <span data-ttu-id="6ebf3-118">Zu den Scheitelpunktdaten gehören Positionskoordinaten, Farbdaten, Texturkoordinatendaten, Normale-Daten usw.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-118">Vertex data includes position coordinates, color data, texture coordinate data, normal data, and so on.</span></span>

<span data-ttu-id="6ebf3-119">Das einfachste Beispiel für einen Vertexpuffer ist eine, die nur Positionsdaten enthält.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-119">The simplest example of a vertex buffer is one that only contains position data.</span></span> <span data-ttu-id="6ebf3-120">Die folgende Abbildungverdeutlicht dieses Beispiel.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-120">It can be visualized like the following illustration.</span></span>

![Abbildung eines Vertexpuffers, der Positionsdaten enthält](images/d3d10-resources-single-element-vb2.png)

<span data-ttu-id="6ebf3-122">Häufiger enthält ein Vertexpuffer aber alle erforderlichen Daten, um 3D-Scheitelpunkte vollständig dazustellen.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-122">More often, a vertex buffer contains all the data needed to fully specify 3D vertices.</span></span> <span data-ttu-id="6ebf3-123">Ein Beispiel dazu könnte ein Vertexpuffer sein, der eine Position pro Scheitelpunkt sowie Normale und Texturkoordinaten enthält.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-123">An example of this could be a vertex buffer that contains per-vertex position, normal and texture coordinates.</span></span> <span data-ttu-id="6ebf3-124">Diese Daten sind in der Regel als Sätze der Elemente pro Scheitelpunkt organisiert, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-124">This data is usually organized as sets of per-vertex elements, as shown in the following illustration.</span></span>

![Abbildungeines Vertexpuffers, der Position, Normale und Texturdaten enthält](images/d3d10-vertex-buffer-element.png)

<span data-ttu-id="6ebf3-126">Dieser Vertexpuffer enthält Daten pro Vertex. Jeder Scheitelpunkt speichert drei Elemente (Position, normale und Texturkoordinaten).</span><span class="sxs-lookup"><span data-stu-id="6ebf3-126">This vertex buffer contains per-vertex data; each vertex stores three elements (position, normal, and texture coordinates).</span></span> <span data-ttu-id="6ebf3-127">Position und Normale werden normalerweise mit drei 32-Bit-Gleitkommawerten und die Texturkoordinaten mit zwei 32-Bit-Gleitkommawerten angegeben.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-127">The position and normal are each typically specified using three 32-bit floats and the texture coordinates using two 32-bit floats.</span></span>

<span data-ttu-id="6ebf3-128">Um Daten aus einem Vertexpuffer zugreifen müssen Sie wissen, welche Scheitelpunkt zu Zugriff sowie die folgenden zusätzlichen Puffer-Parameter:</span><span class="sxs-lookup"><span data-stu-id="6ebf3-128">To access data from a vertex buffer you need to know which vertex to access, plus the following additional buffer parameters:</span></span>

-   <span data-ttu-id="6ebf3-129">Offset - Die Anzahl von Bytes vom Anfang des Puffers bis zu den Daten für den ersten Scheitelpunkt.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-129">Offset - the number of bytes from the start of the buffer to the data for the first vertex.</span></span>
-   <span data-ttu-id="6ebf3-130">BaseVertexLocation - Die Anzahl der Bytes vom Offset bis zum ersten Scheitelpunkt, den der entsprechende Zeichnen-Aufruf verwendet.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-130">BaseVertexLocation - the number of bytes from the offset to the first vertex used by the appropriate draw call.</span></span>

<span data-ttu-id="6ebf3-131">Bevor Sie einen Vertexpuffer erstellen, müssen Sie das Layout definieren.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-131">Before you create a vertex buffer, you need to define its layout.</span></span> <span data-ttu-id="6ebf3-132">Nachdem das eingabelayout Objekt erstellt wurde, wird es auf die [Eingabe-Assembler (IA)-Phase](input-assembler-stage--ia-.md)binden.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-132">After the input-layout object is created, you bind it to the [Input Assembler (IA) stage](input-assembler-stage--ia-.md).</span></span>

### <a name="span-idindexbufferspanspan-idindexbufferspanspan-idindexbufferspanspan-idindex-bufferspanindex-buffer"></a><span data-ttu-id="6ebf3-133"><span id="Index_Buffer"></span><span id="index_buffer"></span><span id="INDEX_BUFFER"></span><span id="index-buffer"></span>Indexpuffer</span><span class="sxs-lookup"><span data-stu-id="6ebf3-133"><span id="Index_Buffer"></span><span id="index_buffer"></span><span id="INDEX_BUFFER"></span><span id="index-buffer"></span>Index Buffer</span></span>

<span data-ttu-id="6ebf3-134">Indexpuffer enthalten Ganzzahl-Offsets in Vertexpuffern und werden zum effizienteren Rendern von Grundtypen verwendet.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-134">Index buffers contain integer offsets into vertex buffers and are used to render primitives more efficiently.</span></span> <span data-ttu-id="6ebf3-135">Ein Indexpuffer enthält eine aufeinanderfolgende Reihe von 16-Bit- oder 32-Bit-Indizes; jeder Index wird verwendet, um einen Scheitelpunkt im Vertexpuffer zu kennzeichnen.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-135">An index buffer contains a sequential set of 16-bit or 32-bit indices; each index is used to identify a vertex in a vertex buffer.</span></span> <span data-ttu-id="6ebf3-136">Die folgende Abbildung enthält eine Darstellung eines Indexpuffers.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-136">An index buffer can be visualized like the following illustration.</span></span>

![Abbildung eines Indexpuffers](images/d3d10-index-buffer.png)

<span data-ttu-id="6ebf3-138">Die aufeinanderfolgenden Indizes in einem Indexpuffer werden mit den folgenden Parametern lokalisiert:</span><span class="sxs-lookup"><span data-stu-id="6ebf3-138">The sequential indices stored in an index buffer are located with the following parameters:</span></span>

-   <span data-ttu-id="6ebf3-139">Offset - die Anzahl der Bytes aus der Basis-Adresse des Indexpuffers.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-139">Offset - the number of bytes from the base address of the index buffer.</span></span>
-   <span data-ttu-id="6ebf3-140">StartIndexLocation - gibt das erste Index Puffer Element aus der Basis Adresse und den Offset an.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-140">StartIndexLocation - specifies the first index buffer element from the base address and the offset.</span></span> <span data-ttu-id="6ebf3-141">Ausgangspfad stellt den ersten Index zu rendern.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-141">The start location represents the first index to render.</span></span>
-   <span data-ttu-id="6ebf3-142">IndexCount – Die Anzahl der zu berechnenden und auszugebenden Indizes.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-142">IndexCount - the number of indices to render.</span></span>

<span data-ttu-id="6ebf3-143">Beginn der Indexpuffer = Index Puffer Base Adresse + Offset (Bytes) + StartIndexLocation \ \* ElementSize (Bytes).</span><span class="sxs-lookup"><span data-stu-id="6ebf3-143">Start of Index Buffer = Index Buffer Base Address + Offset (bytes) + StartIndexLocation \* ElementSize (bytes);</span></span>

<span data-ttu-id="6ebf3-144">Bei der Berechnung ist ElementSize die Größe der einzelnen Elemente der Index-Puffer, der zwei oder vier Byte ist.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-144">In this calculation, ElementSize is the size of each index buffer element, which is either two or four bytes.</span></span>

### <a name="span-idshaderconstantbufferspanspan-idshaderconstantbufferspanspan-idshaderconstantbufferspanspan-idshader-constant-bufferspanconstant-buffer"></a><span data-ttu-id="6ebf3-145"><span id="Shader_Constant_Buffer"></span><span id="shader_constant_buffer"></span><span id="SHADER_CONSTANT_BUFFER"></span><span id="shader-constant-buffer"></span>Konstantenpuffer</span><span class="sxs-lookup"><span data-stu-id="6ebf3-145"><span id="Shader_Constant_Buffer"></span><span id="shader_constant_buffer"></span><span id="SHADER_CONSTANT_BUFFER"></span><span id="shader-constant-buffer"></span>Constant Buffer</span></span>

<span data-ttu-id="6ebf3-146">Ein Konstantenpuffer können Sie Shader-konstantendaten an die Pipeline effizient zu liefern.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-146">A constant buffer allows you to efficiently supply shader constants data to the pipeline.</span></span> <span data-ttu-id="6ebf3-147">Sie können einen Konstantenpuffer zum Speichern der Ergebnisse der Stream-Ausgabe-Stufe verwenden.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-147">You can use a constant buffer to store the results of the stream-output stage.</span></span> <span data-ttu-id="6ebf3-148">Vom Konzept her sieht ein Konstantenpuffer wie ein Vertexpuffer mit einem Element, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-148">Conceptually, a constant buffer looks just like a single-element vertex buffer, as shown in the following illustration.</span></span>

![Abbildung eines Shader-Konstantenpuffers](images/d3d10-shader-resource-buffer.png)

<span data-ttu-id="6ebf3-150">Jedes Element speichert eine Konstante mit ein bis vier Komponenten, durch das Format der gespeicherten Daten bestimmt.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-150">Each element stores a 1-to-4 component constant, determined by the format of the data stored.</span></span>

<span data-ttu-id="6ebf3-151">Ein konstanter Puffer kann nur ein bindungskennzeichen mit einzelnen verwenden, die mit allen anderen bindungskennzeichen kombiniert werden kann.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-151">A constant buffer can only use a single bind flag , which cannot be combined with any other bind flag.</span></span>

<span data-ttu-id="6ebf3-152">Um Shaderkonstanten Puffer von einem Shader zu lesen, verwenden Sie eine HLSL-Load-Funktion.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-152">To read a shader-constant buffer from a shader, use an HLSL load function.</span></span> <span data-ttu-id="6ebf3-153">Für jede Shader-Phase können bis zu 15 Shaderkonstantenpuffer vorhanden sein, die jeweils bis zu 4096 Konstanten umfassen können.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-153">Each shader stage allows up to 15 shader-constant buffers; each buffer can hold up to 4096 constants.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="6ebf3-154"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="6ebf3-154"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="6ebf3-155">Vertex- und Indexpuffer</span><span class="sxs-lookup"><span data-stu-id="6ebf3-155">Vertex and index buffers</span></span>](vertex-and-index-buffers.md)

 

 




