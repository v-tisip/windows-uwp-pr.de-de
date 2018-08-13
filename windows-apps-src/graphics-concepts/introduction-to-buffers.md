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
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: 677eea4757220320bc364fef20bf5a5c8d4daaa2
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "1044339"
---
# <a name="introduction-to-buffers"></a><span data-ttu-id="1583c-104">Einführung zu Puffern</span><span class="sxs-lookup"><span data-stu-id="1583c-104">Introduction to buffers</span></span>


<span data-ttu-id="1583c-105">Eine Pufferressource ist eine Sammlung vollständig typisierter Daten, die zu Elementen gruppiert werden.</span><span class="sxs-lookup"><span data-stu-id="1583c-105">A buffer resource is a collection of fully typed data, grouped into elements.</span></span> <span data-ttu-id="1583c-106">Puffer speichern Daten, wie z.B. Texturkoordinaten in einem *Scheitelpunktpuffer*, Indizes in einem *Indexpuffer*, Shader-Konstantendaten in einem *Konstantenpuffer*, Positionsvektoren, normale Vektoren oder den Gerätezustand.</span><span class="sxs-lookup"><span data-stu-id="1583c-106">Buffers store data, such as texture coordinates in a *vertex buffer*, indexes in an *index buffer*, shader constants data in a *constant buffer*, position vectors, normal vectors, or device state.</span></span>

<span data-ttu-id="1583c-107">Ein Element Puffer 1 bis 4 Komponenten besteht.</span><span class="sxs-lookup"><span data-stu-id="1583c-107">A buffer element is made up of 1 to 4 components.</span></span> <span data-ttu-id="1583c-108">Pufferelemente können gepackte Datenwerten (wie R8G8B8A8-Oberflächenwerte), einzelne 8-Bit-Ganzahlen oder vier 32-Bit-Gleitkommawerte enthalten.</span><span class="sxs-lookup"><span data-stu-id="1583c-108">Buffer elements can include packed data values (like R8G8B8A8 surface values), single 8-bit integers, or four 32-bit floating point values.</span></span>

<span data-ttu-id="1583c-109">Puffer werden als unstrukturierte Ressource erstellt.</span><span class="sxs-lookup"><span data-stu-id="1583c-109">A buffer is created as an unstructured resource.</span></span> <span data-ttu-id="1583c-110">Da es unstrukturierten ist, ein Puffer kann keine Mipmap-Ebenen enthalten, es kann nicht beim Lesen gefiltert erhalten möchten, und sie nicht Multisampling sein.</span><span class="sxs-lookup"><span data-stu-id="1583c-110">Because it is unstructured, a buffer cannot contain any mipmap levels, it cannot get filtered when read, and it cannot be multisampled.</span></span>

## <a name="span-idbuffertypesspanspan-idbuffertypesspanspan-idbuffertypesspanbuffer-types"></a><span data-ttu-id="1583c-111"><span id="Buffer_Types"></span><span id="buffer_types"></span><span id="BUFFER_TYPES"></span>Puffercache-Typen</span><span class="sxs-lookup"><span data-stu-id="1583c-111"><span id="Buffer_Types"></span><span id="buffer_types"></span><span id="BUFFER_TYPES"></span>Buffer Types</span></span>


<span data-ttu-id="1583c-112">Es folgen die Puffer Ressourcentypen von Direct3D 11 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="1583c-112">The following are the buffer resource types supported by Direct3D 11.</span></span>

-   [<span data-ttu-id="1583c-113">Vertexpuffer</span><span class="sxs-lookup"><span data-stu-id="1583c-113">Vertex Buffer</span></span>](#vertex-buffer)
-   [<span data-ttu-id="1583c-114">Indexpuffer</span><span class="sxs-lookup"><span data-stu-id="1583c-114">Index Buffer</span></span>](#index-buffer)
-   [<span data-ttu-id="1583c-115">Konstante Puffer</span><span class="sxs-lookup"><span data-stu-id="1583c-115">Constant Buffer</span></span>](#shader-constant-buffer)

### <a name="span-idvertexbufferspanspan-idvertexbufferspanspan-idvertexbufferspanspan-idvertex-bufferspanvertex-buffer"></a><span data-ttu-id="1583c-116"><span id="Vertex_Buffer"></span><span id="vertex_buffer"></span><span id="VERTEX_BUFFER"></span><span id="vertex-buffer"></span>Scheitelpunkt Puffer</span><span class="sxs-lookup"><span data-stu-id="1583c-116"><span id="Vertex_Buffer"></span><span id="vertex_buffer"></span><span id="VERTEX_BUFFER"></span><span id="vertex-buffer"></span>Vertex Buffer</span></span>

<span data-ttu-id="1583c-117">Ein Scheitelpunkt-Puffer enthält die Scheitelpunkt Daten verwendet, um die Geometrie definieren.</span><span class="sxs-lookup"><span data-stu-id="1583c-117">A vertex buffer contains the vertex data used to define your geometry.</span></span> <span data-ttu-id="1583c-118">Zu den Scheitelpunktdaten gehören Positionskoordinaten, Farbdaten, Texturkoordinatendaten, Normale-Daten usw.</span><span class="sxs-lookup"><span data-stu-id="1583c-118">Vertex data includes position coordinates, color data, texture coordinate data, normal data, and so on.</span></span>

<span data-ttu-id="1583c-119">Das einfachste Beispiel eines Scheitelpunkts Puffers ist ein, die nur Positionsdaten enthält.</span><span class="sxs-lookup"><span data-stu-id="1583c-119">The simplest example of a vertex buffer is one that only contains position data.</span></span> <span data-ttu-id="1583c-120">Die folgende Abbildungverdeutlicht dieses Beispiel.</span><span class="sxs-lookup"><span data-stu-id="1583c-120">It can be visualized like the following illustration.</span></span>

![Abbildung eines Vertexpuffers, der Positionsdaten enthält](images/d3d10-resources-single-element-vb2.png)

<span data-ttu-id="1583c-122">Häufiger enthält ein Vertexpuffer aber alle erforderlichen Daten, um 3D-Scheitelpunkte vollständig dazustellen.</span><span class="sxs-lookup"><span data-stu-id="1583c-122">More often, a vertex buffer contains all the data needed to fully specify 3D vertices.</span></span> <span data-ttu-id="1583c-123">Ein Beispiel dazu könnte ein Vertexpuffer sein, der eine Position pro Scheitelpunkt sowie Normale und Texturkoordinaten enthält.</span><span class="sxs-lookup"><span data-stu-id="1583c-123">An example of this could be a vertex buffer that contains per-vertex position, normal and texture coordinates.</span></span> <span data-ttu-id="1583c-124">Diese Daten sind in der Regel als Sätze der Elemente pro Scheitelpunkt organisiert, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="1583c-124">This data is usually organized as sets of per-vertex elements, as shown in the following illustration.</span></span>

![Abbildungeines Vertexpuffers, der Position, Normale und Texturdaten enthält](images/d3d10-vertex-buffer-element.png)

<span data-ttu-id="1583c-126">Dieser Puffer Scheitelpunkts enthält Vertices Daten. Scheitelpunkte werden drei Elemente (Position, Normal und Textur Koordinaten) gespeichert.</span><span class="sxs-lookup"><span data-stu-id="1583c-126">This vertex buffer contains per-vertex data; each vertex stores three elements (position, normal, and texture coordinates).</span></span> <span data-ttu-id="1583c-127">Position und Normale werden normalerweise mit drei 32-Bit-Gleitkommawerten und die Texturkoordinaten mit zwei 32-Bit-Gleitkommawerten angegeben.</span><span class="sxs-lookup"><span data-stu-id="1583c-127">The position and normal are each typically specified using three 32-bit floats and the texture coordinates using two 32-bit floats.</span></span>

<span data-ttu-id="1583c-128">Zugriff auf Daten aus einem Puffer Scheitelpunkts müssen Sie wissen, welche Scheitelpunkt zum Zugriff sowie die folgenden zusätzlichen Puffercache-Parameter:</span><span class="sxs-lookup"><span data-stu-id="1583c-128">To access data from a vertex buffer you need to know which vertex to access, plus the following additional buffer parameters:</span></span>

-   <span data-ttu-id="1583c-129">Offset - Die Anzahl von Bytes vom Anfang des Puffers bis zu den Daten für den ersten Scheitelpunkt.</span><span class="sxs-lookup"><span data-stu-id="1583c-129">Offset - the number of bytes from the start of the buffer to the data for the first vertex.</span></span>
-   <span data-ttu-id="1583c-130">BaseVertexLocation - Die Anzahl der Bytes vom Offset bis zum ersten Scheitelpunkt, den der entsprechende Zeichnen-Aufruf verwendet.</span><span class="sxs-lookup"><span data-stu-id="1583c-130">BaseVertexLocation - the number of bytes from the offset to the first vertex used by the appropriate draw call.</span></span>

<span data-ttu-id="1583c-131">Bevor Sie einen Scheitelpunkt Puffer erstellen, müssen Sie definieren des Layouts.</span><span class="sxs-lookup"><span data-stu-id="1583c-131">Before you create a vertex buffer, you need to define its layout.</span></span> <span data-ttu-id="1583c-132">Nachdem das Eingabe-Layout-Objekt erstellt wird, wird es in die [Phase Input Assembler (IA)](input-assembler-stage--ia-.md)binden.</span><span class="sxs-lookup"><span data-stu-id="1583c-132">After the input-layout object is created, you bind it to the [Input Assembler (IA) stage](input-assembler-stage--ia-.md).</span></span>

### <a name="span-idindexbufferspanspan-idindexbufferspanspan-idindexbufferspanspan-idindex-bufferspanindex-buffer"></a><span data-ttu-id="1583c-133"><span id="Index_Buffer"></span><span id="index_buffer"></span><span id="INDEX_BUFFER"></span><span id="index-buffer"></span>Indexpuffer</span><span class="sxs-lookup"><span data-stu-id="1583c-133"><span id="Index_Buffer"></span><span id="index_buffer"></span><span id="INDEX_BUFFER"></span><span id="index-buffer"></span>Index Buffer</span></span>

<span data-ttu-id="1583c-134">Index-Puffer enthalten ganze Zahl Offsets in Scheitelpunkts Puffer und dienen zum Rendern von Primitives effizienter.</span><span class="sxs-lookup"><span data-stu-id="1583c-134">Index buffers contain integer offsets into vertex buffers and are used to render primitives more efficiently.</span></span> <span data-ttu-id="1583c-135">Ein Indexpuffer enthält eine aufeinanderfolgende Reihe von 16-Bit- oder 32-Bit-Indizes; jeder Index wird verwendet, um einen Scheitelpunkt im Vertexpuffer zu kennzeichnen.</span><span class="sxs-lookup"><span data-stu-id="1583c-135">An index buffer contains a sequential set of 16-bit or 32-bit indices; each index is used to identify a vertex in a vertex buffer.</span></span> <span data-ttu-id="1583c-136">Die folgende Abbildung enthält eine Darstellung eines Indexpuffers.</span><span class="sxs-lookup"><span data-stu-id="1583c-136">An index buffer can be visualized like the following illustration.</span></span>

![Abbildung eines Indexpuffers](images/d3d10-index-buffer.png)

<span data-ttu-id="1583c-138">Die aufeinanderfolgenden Indizes in einem Indexpuffer werden mit den folgenden Parametern lokalisiert:</span><span class="sxs-lookup"><span data-stu-id="1583c-138">The sequential indices stored in an index buffer are located with the following parameters:</span></span>

-   <span data-ttu-id="1583c-139">Offset - die Anzahl von Bytes aus der Basisadresse des Indexpuffers.</span><span class="sxs-lookup"><span data-stu-id="1583c-139">Offset - the number of bytes from the base address of the index buffer.</span></span>
-   <span data-ttu-id="1583c-140">StartIndexLocation - gibt das erste Element der Index-Puffer aus der Basisadresse und der Offset an.</span><span class="sxs-lookup"><span data-stu-id="1583c-140">StartIndexLocation - specifies the first index buffer element from the base address and the offset.</span></span> <span data-ttu-id="1583c-141">Die Startposition stellt den ersten Index zu rendern.</span><span class="sxs-lookup"><span data-stu-id="1583c-141">The start location represents the first index to render.</span></span>
-   <span data-ttu-id="1583c-142">IndexCount – Die Anzahl der zu berechnenden und auszugebenden Indizes.</span><span class="sxs-lookup"><span data-stu-id="1583c-142">IndexCount - the number of indices to render.</span></span>

<span data-ttu-id="1583c-143">Anfang des Indexpuffer = Index Puffer Basisadresse Offset (Bytes) + StartIndexLocation \ \* ElementSize (Bytes).</span><span class="sxs-lookup"><span data-stu-id="1583c-143">Start of Index Buffer = Index Buffer Base Address + Offset (bytes) + StartIndexLocation \* ElementSize (bytes);</span></span>

<span data-ttu-id="1583c-144">In dieser Berechnung ist ElementSize die Größe der einzelnen Index-Puffer-Element, das zwei oder vier Bytes ist.</span><span class="sxs-lookup"><span data-stu-id="1583c-144">In this calculation, ElementSize is the size of each index buffer element, which is either two or four bytes.</span></span>

### <a name="span-idshaderconstantbufferspanspan-idshaderconstantbufferspanspan-idshaderconstantbufferspanspan-idshader-constant-bufferspanconstant-buffer"></a><span data-ttu-id="1583c-145"><span id="Shader_Constant_Buffer"></span><span id="shader_constant_buffer"></span><span id="SHADER_CONSTANT_BUFFER"></span><span id="shader-constant-buffer"></span>Konstante Puffer</span><span class="sxs-lookup"><span data-stu-id="1583c-145"><span id="Shader_Constant_Buffer"></span><span id="shader_constant_buffer"></span><span id="SHADER_CONSTANT_BUFFER"></span><span id="shader-constant-buffer"></span>Constant Buffer</span></span>

<span data-ttu-id="1583c-146">Ein konstanter Puffer können Sie effizient Shader-Konstanten Daten in der Pipeline bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="1583c-146">A constant buffer allows you to efficiently supply shader constants data to the pipeline.</span></span> <span data-ttu-id="1583c-147">Sie können einen Konstanten Puffer zum Speichern der Ergebnisse im Freigabefenster Stream-Ausgabe verwenden.</span><span class="sxs-lookup"><span data-stu-id="1583c-147">You can use a constant buffer to store the results of the stream-output stage.</span></span> <span data-ttu-id="1583c-148">Konzept, sucht ein konstanter Puffer wie bei einem einzelnen Element Scheitelpunkts Puffer, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="1583c-148">Conceptually, a constant buffer looks just like a single-element vertex buffer, as shown in the following illustration.</span></span>

![Abbildung eines Shader-Konstantenpuffers](images/d3d10-shader-resource-buffer.png)

<span data-ttu-id="1583c-150">Jedes Element speichert eine Konstante mit ein bis vier Komponenten, durch das Format der gespeicherten Daten bestimmt.</span><span class="sxs-lookup"><span data-stu-id="1583c-150">Each element stores a 1-to-4 component constant, determined by the format of the data stored.</span></span>

<span data-ttu-id="1583c-151">Ein konstanter Puffer kann nur ein einzelnes binden Flag verwenden, die mit einem anderen binden Flag kombiniert werden können.</span><span class="sxs-lookup"><span data-stu-id="1583c-151">A constant buffer can only use a single bind flag , which cannot be combined with any other bind flag.</span></span>

<span data-ttu-id="1583c-152">Um einen Puffer Shader-Konstante aus einer Shader lesen, verwenden Sie eine HLSL Last-Funktion.</span><span class="sxs-lookup"><span data-stu-id="1583c-152">To read a shader-constant buffer from a shader, use an HLSL load function.</span></span> <span data-ttu-id="1583c-153">Für jede Shader-Phase können bis zu 15 Shaderkonstantenpuffer vorhanden sein, die jeweils bis zu 4096 Konstanten umfassen können.</span><span class="sxs-lookup"><span data-stu-id="1583c-153">Each shader stage allows up to 15 shader-constant buffers; each buffer can hold up to 4096 constants.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="1583c-154"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="1583c-154"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="1583c-155">Vertex- und Indexpuffer</span><span class="sxs-lookup"><span data-stu-id="1583c-155">Vertex and index buffers</span></span>](vertex-and-index-buffers.md)

 

 




