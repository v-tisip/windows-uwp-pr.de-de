---
title: Indexpuffer
description: Indexpuffer sind Speicherpuffer mit Indexdaten, die Ganzzahl-Offsets in Vertexpuffer darstellen, und zum Rendern von Grundtypen verwendet werden.
ms.assetid: 14D3DEC5-CF74-488B-BE41-16BF5E3201BE
keywords: Indexpuffer
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: f79b6982ccb6a938f88a289a823dd5da855e57e2
ms.sourcegitcommit: c80b9e6589a1ee29c5032a0b942e6a024c224ea7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="index-buffers"></a><span data-ttu-id="f4619-104">Indexpuffer</span><span class="sxs-lookup"><span data-stu-id="f4619-104">Index buffers</span></span>


<span data-ttu-id="f4619-105">*Indexpuffer* sind Speicherpuffer mit Indexdaten, die Ganzzahl-Offsets in Vertexpuffer darstellen, und zum Rendern von Grundtypen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f4619-105">*Index buffers* are memory buffers that contain index data, which are integer offsets into vertex buffers, used to render primitives.</span></span>

<span data-ttu-id="f4619-106">Indexpuffer sind Speicherpuffer mit Indexdaten.</span><span class="sxs-lookup"><span data-stu-id="f4619-106">Index buffers are memory buffers that contain index data.</span></span> <span data-ttu-id="f4619-107">Indexdaten oder Indizes sind Ganzzahl-Offsets in Vertexpuffern, die zum Rendern von Grundtypen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f4619-107">Index data, or indices, are integer offsets into vertex buffers and are used to render primitives.</span></span>

<span data-ttu-id="f4619-108">Ein Vertexpuffer enthält Scheitelpunkte; deshalb können Sie einen Vertexpuffer mit oder ohne indizierten Grundtypen zeichnen.</span><span class="sxs-lookup"><span data-stu-id="f4619-108">A vertex buffer contains vertices; therefore, you can draw a vertex buffer either with or without indexed primitives.</span></span> <span data-ttu-id="f4619-109">Da ein Indexpuffer jedoch Indizes enthält, können Sie einen Indexpuffer nicht ohne entsprechenden Vertexpuffer verwenden.</span><span class="sxs-lookup"><span data-stu-id="f4619-109">However, because an index buffer contains indices, you cannot use an index buffer without a corresponding vertex buffer.</span></span>

## <a name="span-idindexbufferdescriptionspanspan-idindexbufferdescriptionspanspan-idindexbufferdescriptionspanindex-buffer-description"></a><span data-ttu-id="f4619-110"><span id="Index_Buffer_Description"></span><span id="index_buffer_description"></span><span id="INDEX_BUFFER_DESCRIPTION"></span>Beschreibung des Indexpuffers</span><span class="sxs-lookup"><span data-stu-id="f4619-110"><span id="Index_Buffer_Description"></span><span id="index_buffer_description"></span><span id="INDEX_BUFFER_DESCRIPTION"></span>Index Buffer Description</span></span>


<span data-ttu-id="f4619-111">Ein Indexpuffer wird anhand seiner Fähigkeiten beschrieben, wie z.B. wo im Speicher er vorhanden ist, ob Lese- und Schreibberechtigungen unterstützt werden, und nach Typ und Anzahl der enthaltenen Indizes.</span><span class="sxs-lookup"><span data-stu-id="f4619-111">An index buffer is described in terms of its capabilities, such as where it exists in memory, whether it supports reading and writing, and the type and number of indices it can contain.</span></span>

<span data-ttu-id="f4619-112">Die Beschreibungen von Indexpuffern geben Ihrer Anwendung Hinweise darauf, wie ein vorhandener Puffer erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="f4619-112">Index buffer descriptions tell your application how an existing buffer was created.</span></span> <span data-ttu-id="f4619-113">Sie stellen eine leere Beschreibungsstruktur für das System bereit, die mit den Fähigkeiten eines vorher erstellten Indexpuffers gefüllt wird.</span><span class="sxs-lookup"><span data-stu-id="f4619-113">You provide an empty description structure for the system to fill with the capabilities of a previously created index buffer.</span></span>

## <a name="span-idindexprocessingrequirementsspanspan-idindexprocessingrequirementsspanspan-idindexprocessingrequirementsspanindex-processing-requirements"></a><span data-ttu-id="f4619-114"><span id="Index_Processing_Requirements"></span><span id="index_processing_requirements"></span><span id="INDEX_PROCESSING_REQUIREMENTS"></span>Indexverarbeitungsanforderungen</span><span class="sxs-lookup"><span data-stu-id="f4619-114"><span id="Index_Processing_Requirements"></span><span id="index_processing_requirements"></span><span id="INDEX_PROCESSING_REQUIREMENTS"></span>Index Processing Requirements</span></span>


<span data-ttu-id="f4619-115">Die Leistung von Indexverarbeitungsvorgängen ist hauptsächlich davon abhängig, wo der Index im Speicher vorhanden ist, und welche Art von Renderinggerät verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f4619-115">The performance of index processing operations depends heavily on where the index buffer exists in memory and what type of rendering device is being used.</span></span> <span data-ttu-id="f4619-116">Anwendungen steuern die Speicherreservierung für Indexpuffer, wenn sie erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="f4619-116">Applications control the memory allocation for index buffers when they are created.</span></span>

<span data-ttu-id="f4619-117">Die Anwendung kann direkt Indizes in einen Indexpuffer schreiben, der im treiberoptimierten Arbeitsspeicher reserviert ist.</span><span class="sxs-lookup"><span data-stu-id="f4619-117">The application can directly write indices to a index buffer allocated in driver-optimal memory.</span></span> <span data-ttu-id="f4619-118">Mit dieser Technik wird später ein redundanter Kopiervorgang verhindert.</span><span class="sxs-lookup"><span data-stu-id="f4619-118">This technique prevents a redundant copy operation later.</span></span> <span data-ttu-id="f4619-119">Diese Technik funktioniert nicht optimal, wenn Ihre Anwendung Daten aus dem Indexpuffer zurückliest, da vom Host ausgeführte Lesevorgänge auf den treiberoptimierten Arbeitsspeicher sehr langsam sein können.</span><span class="sxs-lookup"><span data-stu-id="f4619-119">This technique does not work well if your application reads data back from an index buffer, because read operations done by the host from driver-optimal memory can be very slow.</span></span> <span data-ttu-id="f4619-120">Wenn Ihre Anwendung also während der Verarbeitung unregelmäßig Daten in oder aus dem Puffer lesen oder schreiben muss, ist ein Indexpuffer im Systemspeicher die bessere Wahl.</span><span class="sxs-lookup"><span data-stu-id="f4619-120">Therefore, if your application needs to read during processing or writes data to the buffer erratically, a system-memory index buffer is a better choice.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="f4619-121"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="f4619-121"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="f4619-122">Vertex- und Indexpuffer</span><span class="sxs-lookup"><span data-stu-id="f4619-122">Vertex and index buffers</span></span>](vertex-and-index-buffers.md)

 

 




