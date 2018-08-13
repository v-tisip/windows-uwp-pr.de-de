---
title: Statusobjekte
description: Der Gerätestatus wird in Statusobjekten gruppiert, wodurch der Aufwand für Statusänderungen erheblich reduziert wird. Es gibt mehrere Statusobjekte und jedes dient der Initialisierung einer Statusgruppe für eine bestimmte Pipelinephase. Statusobjekte variieren je nach der Version von Direct3D.
ms.assetid: D998745C-2B75-4E59-9923-AD1A17A92E05
keywords:
- Statusobjekte
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: 763df332ab64fcc536f5358df8b22eecc08e7527
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "1044539"
---
# <a name="state-objects"></a><span data-ttu-id="8a180-106">Statusobjekte</span><span class="sxs-lookup"><span data-stu-id="8a180-106">State objects</span></span>


<span data-ttu-id="8a180-107">Der Gerätestatus wird in Statusobjekten gruppiert, wodurch der Aufwand für Statusänderungen erheblich reduziert wird.</span><span class="sxs-lookup"><span data-stu-id="8a180-107">Device state is grouped into state objects which greatly reduce the cost of state changes.</span></span> <span data-ttu-id="8a180-108">Es gibt mehrere Statusobjekte und jedes dient der Initialisierung einer Statusgruppe für eine bestimmte Pipelinephase.</span><span class="sxs-lookup"><span data-stu-id="8a180-108">There are several state objects, and each one is designed to initialize a set of state for a particular pipeline stage.</span></span> <span data-ttu-id="8a180-109">Statusobjekte variieren je nach der Version von Direct3D.</span><span class="sxs-lookup"><span data-stu-id="8a180-109">State objects vary by version of Direct3D.</span></span>

## <a name="span-idinputlayoutspanspan-idinputlayoutspanspan-idinputlayoutspaninput-layout-state"></a><span data-ttu-id="8a180-110"><span id="Input_Layout"></span><span id="input_layout"></span><span id="INPUT_LAYOUT"></span>Eingabelayoutstatus</span><span class="sxs-lookup"><span data-stu-id="8a180-110"><span id="Input_Layout"></span><span id="input_layout"></span><span id="INPUT_LAYOUT"></span>Input-Layout State</span></span>


<span data-ttu-id="8a180-111">Diese Statusgruppe bestimmt, wie die [Eingabeassemblerphase (IA)](input-assembler-stage--ia-.md) Daten aus den Eingabepuffern liest und sie für die Verwendung durch den Vertex-Shader zusammensetzt.</span><span class="sxs-lookup"><span data-stu-id="8a180-111">This group of state dictates how the [Input Assembler (IA) stage](input-assembler-stage--ia-.md) reads data out of the input buffers and assembles it for use by the vertex shader.</span></span> <span data-ttu-id="8a180-112">Dies umfasst Status wie die Anzahl der Elemente im Eingabepuffer und die Signatur der Eingabedaten.</span><span class="sxs-lookup"><span data-stu-id="8a180-112">This includes state such as the number of elements in the input buffer and the signature of the input data.</span></span> <span data-ttu-id="8a180-113">In der Eingabeassemblerphase (IA) werden Grundtypen aus dem Speicher in die Pipeline gestreamt.</span><span class="sxs-lookup"><span data-stu-id="8a180-113">The Input Assembler (IA) stage streams primitives from memory into the pipeline.</span></span>

## <a name="span-idrasterizerspanspan-idrasterizerspanspan-idrasterizerspanrasterizer-state"></a><span data-ttu-id="8a180-114"><span id="Rasterizer"></span><span id="rasterizer"></span><span id="RASTERIZER"></span>Rasterizerstatus</span><span class="sxs-lookup"><span data-stu-id="8a180-114"><span id="Rasterizer"></span><span id="rasterizer"></span><span id="RASTERIZER"></span>Rasterizer State</span></span>


<span data-ttu-id="8a180-115">Diese Statusgruppe initialisiert die [Rasterizerphase (RS)](rasterizer-stage--rs-.md).</span><span class="sxs-lookup"><span data-stu-id="8a180-115">This group of state initializes the [Rasterizer (RS) stage](rasterizer-stage--rs-.md).</span></span> <span data-ttu-id="8a180-116">Dieses Objekt enthält Status wie Modi zum Füllen oder Aussortieren, Aktivieren eines Schneiderechtecks zum Zuschneiden und Festlegen von Parametern für das Multisampling.</span><span class="sxs-lookup"><span data-stu-id="8a180-116">This object includes state such as fill or cull modes, enabling a scissor rectangle for clipping, and setting multisample parameters.</span></span> <span data-ttu-id="8a180-117">In dieser Phase werden Grundtypen in Pixel gerastert, indem Vorgänge wie Zuschneiden durchgeführt und Viewports Grundtypen zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="8a180-117">This stage rasterizes primitives into pixels, performing operations like clipping and mapping primitives to the viewport.</span></span>

## <a name="span-iddepthstencilspanspan-iddepthstencilspanspan-iddepthstencilspandepth-stencil-state"></a><span data-ttu-id="8a180-118"><span id="DepthStencil"></span><span id="depthstencil"></span><span id="DEPTHSTENCIL"></span>Tiefenschablonenstatus</span><span class="sxs-lookup"><span data-stu-id="8a180-118"><span id="DepthStencil"></span><span id="depthstencil"></span><span id="DEPTHSTENCIL"></span>Depth-Stencil State</span></span>


<span data-ttu-id="8a180-119">Diese Statusgruppe initialisiert den Tiefenschablonenteil der [Ausgabezusammenführungsphase (OM)](output-merger-stage--om-.md).</span><span class="sxs-lookup"><span data-stu-id="8a180-119">This group of state initializes the depth-stencil portion of the [Output Merger (OM) stage](output-merger-stage--om-.md).</span></span> <span data-ttu-id="8a180-120">Genauer gesagt, initialisiert dieses Objekt Tiefen- und Schablonentests.</span><span class="sxs-lookup"><span data-stu-id="8a180-120">More specifically, this object initializes depth and stencil testing.</span></span>

## <a name="span-idblendspanspan-idblendspanspan-idblendspanblend-state"></a><span data-ttu-id="8a180-121"><span id="Blend"></span><span id="blend"></span><span id="BLEND"></span>Überblendungsstatus</span><span class="sxs-lookup"><span data-stu-id="8a180-121"><span id="Blend"></span><span id="blend"></span><span id="BLEND"></span>Blend State</span></span>


<span data-ttu-id="8a180-122">Diese Statusgruppe initialisiert den Überblendungsteil der [Ausgabezusammenführungsphase (OM)](output-merger-stage--om-.md).</span><span class="sxs-lookup"><span data-stu-id="8a180-122">This group of state initializes the blending portion of the [Output Merger (OM) stage](output-merger-stage--om-.md).</span></span>

## <a name="span-idsamplerspanspan-idsamplerspanspan-idsamplerspansampler-state"></a><span data-ttu-id="8a180-123"><span id="Sampler"></span><span id="sampler"></span><span id="SAMPLER"></span>Samplerstatus</span><span class="sxs-lookup"><span data-stu-id="8a180-123"><span id="Sampler"></span><span id="sampler"></span><span id="SAMPLER"></span>Sampler State</span></span>


<span data-ttu-id="8a180-124">Diese Statusgruppe initialisiert ein Samplerobjekt.</span><span class="sxs-lookup"><span data-stu-id="8a180-124">This group of state initializes a sampler object.</span></span> <span data-ttu-id="8a180-125">Ein Samplerobjekt wird von den Shaderphasen zum Filtern von Texturen im Speicher verwendet.</span><span class="sxs-lookup"><span data-stu-id="8a180-125">A sampler object is used by the shader stages to filter textures in memory.</span></span>

<span data-ttu-id="8a180-126">In Direct3D ist das Samplerobjekt nicht an eine bestimmte Textur gebunden, es beschreibt nur, wie die Filterung für angefügte Ressourcen erfolgt.</span><span class="sxs-lookup"><span data-stu-id="8a180-126">In Direct3D, the sampler object is not bound to a specific texture, it just describes how to do filtering given any attached resource.</span></span>

## <a name="span-idperformanceconsiderationsspanspan-idperformanceconsiderationsspanspan-idperformanceconsiderationsspanperformance-considerations"></a><span data-ttu-id="8a180-127"><span id="Performance_Considerations"></span><span id="performance_considerations"></span><span id="PERFORMANCE_CONSIDERATIONS"></span>Überlegungen zur Leistung</span><span class="sxs-lookup"><span data-stu-id="8a180-127"><span id="Performance_Considerations"></span><span id="performance_considerations"></span><span id="PERFORMANCE_CONSIDERATIONS"></span>Performance Considerations</span></span>


<span data-ttu-id="8a180-128">Die Verwendung von Statusobjekten in der API führt zu einer Reihe von Leistungsvorteilen.</span><span class="sxs-lookup"><span data-stu-id="8a180-128">Designing the API to use state objects creates several performance advantages.</span></span> <span data-ttu-id="8a180-129">Dazu gehören: Überprüfen des Status bei der Objekterstellung, Aktivieren des Zwischenspeicherns von Statusobjekten in der Hardware und erhebliches Verringern der Statusmenge, die beim API-Aufruf für eine Statusfestlegung übergeben wird (durch Übergabe eines Handles an das Statusobjekt anstelle des Status).</span><span class="sxs-lookup"><span data-stu-id="8a180-129">These include validating state at object creation time, enabling caching of state objects in hardware, and greatly reducing the amount of state that is passed during a state-setting API call (by passing a handle to the state object instead of the state).</span></span>

<span data-ttu-id="8a180-130">Um diese Leistungsverbesserungen zu erzielen, sollten Sie Ihre Statusobjekte beim Start Ihrer Anwendung erstellen, und zwar vor der Renderschleife.</span><span class="sxs-lookup"><span data-stu-id="8a180-130">To achieve these performance improvements, you should create your state objects when your application starts up, well before your render loop.</span></span> <span data-ttu-id="8a180-131">Statusobjekte sind unveränderlich, d.h., nachdem sie erstellt wurden, können sie nicht mehr geändert werden.</span><span class="sxs-lookup"><span data-stu-id="8a180-131">State objects are immutable, that is, once they are created, you cannot change them.</span></span> <span data-ttu-id="8a180-132">Sie müssen sie stattdessen löschen und neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="8a180-132">Instead you must destroy and recreate them.</span></span>

<span data-ttu-id="8a180-133">Sie können mehrere Samplerobjekte mit verschiedenen Samplerstatuskombinationen erstellen.</span><span class="sxs-lookup"><span data-stu-id="8a180-133">You could create several sampler objects with various sampler-state combinations.</span></span> <span data-ttu-id="8a180-134">Das Ändern des Samplerstatus erfolgt dann durch Aufrufen der entsprechenden „Set”-API, die ein Handle für das Objekt (statt des Samplerstatus) übergibt.</span><span class="sxs-lookup"><span data-stu-id="8a180-134">Changing the sampler state is then accomplished by calling the appropriate "Set" API which passes a handle to the object (as opposed to the sampler state).</span></span> <span data-ttu-id="8a180-135">Der Aufwand für eine Statusänderung bei jedem Rendern von Frames wird dadurch deutlich reduziert, da die Anzahl der Aufrufe und die Menge an Daten erheblich verringert werden.</span><span class="sxs-lookup"><span data-stu-id="8a180-135">This significantly reduces the amount of overhead during each render frame for changing state since the number of calls and the amount of data are greatly reduced.</span></span>

<span data-ttu-id="8a180-136">Alternativ können Sie das Effektsystem verwenden, das automatisch die effiziente Erstellung und Zerstörung von Statusobjekten für Ihre Anwendung verwaltet.</span><span class="sxs-lookup"><span data-stu-id="8a180-136">Alternatively, you can choose to use the effect system which will automatically manage efficient creation and destruction of state objects for your application.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="8a180-137"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="8a180-137"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="8a180-138">Grafikpipeline</span><span class="sxs-lookup"><span data-stu-id="8a180-138">Graphics pipeline</span></span>](graphics-pipeline.md)

[<span data-ttu-id="8a180-139">Ansichten</span><span class="sxs-lookup"><span data-stu-id="8a180-139">Views</span></span>](views.md)

 

 




