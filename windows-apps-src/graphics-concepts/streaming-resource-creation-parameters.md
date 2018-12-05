---
title: Parameter für das Erstellen von Streamingressourcen
description: Es gibt einige Einschränkungen für den Typ der Direct3D-Ressourcen, die Sie als Streamingressource erstellen können.
ms.assetid: 6FC5AD93-6F47-479E-947C-895C99B427BC
keywords:
- Parameter für das Erstellen von Streamingressourcen
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 1ddb150e570e25af7162a50309b9b0fc30cedf60
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8708079"
---
# <a name="streaming-resource-creation-parameters"></a><span data-ttu-id="11078-104">Parameter für das Erstellen von Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="11078-104">Streaming resource creation parameters</span></span>


<span data-ttu-id="11078-105">Es gibt einige Einschränkungen für den Typ der Direct3D-Ressourcen, die Sie als Streamingressource erstellen können.</span><span class="sxs-lookup"><span data-stu-id="11078-105">There are some constraints on the type of Direct3D resources that you can create as a streaming resource.</span></span>

<span data-ttu-id="11078-106"><span id="Supported-Resource-Type"></span><span id="supported-resource-type"></span><span id="SUPPORTED-RESOURCE-TYPE"></span>**Unterstützter Ressourcentyp**</span><span class="sxs-lookup"><span data-stu-id="11078-106"><span id="Supported-Resource-Type"></span><span id="supported-resource-type"></span><span id="SUPPORTED-RESOURCE-TYPE"></span>**Supported Resource Type**</span></span>  
<span data-ttu-id="11078-107">Texture2D\ [Array\] (einschließlich TextureCube\[Array\], der eine Variante von Texture2D\[Array\]) oder Buffer ist.</span><span class="sxs-lookup"><span data-stu-id="11078-107">Texture2D\[Array\] (including TextureCube\[Array\], which is a variant of Texture2D\[Array\]) or Buffer.</span></span>

<span data-ttu-id="11078-108">**Nicht unterstützt:** Texture1D\ [Array\].</span><span class="sxs-lookup"><span data-stu-id="11078-108">**NOT supported:** Texture1D\[Array\] .</span></span>

<span data-ttu-id="11078-109"><span id="Supported-Resource-Usage"></span><span id="supported-resource-usage"></span><span id="SUPPORTED-RESOURCE-USAGE"></span>**Unterstützte Ressourcenverwendung**</span><span class="sxs-lookup"><span data-stu-id="11078-109"><span id="Supported-Resource-Usage"></span><span id="supported-resource-usage"></span><span id="SUPPORTED-RESOURCE-USAGE"></span>**Supported Resource Usage**</span></span>  
<span data-ttu-id="11078-110">Standardverwendung.</span><span class="sxs-lookup"><span data-stu-id="11078-110">Default usage.</span></span>

<span data-ttu-id="11078-111">**Nicht unterstützt:** Dynamisch, staging oder unveränderlich.</span><span class="sxs-lookup"><span data-stu-id="11078-111">**NOT supported:** Dynamic, staging, or immutable.</span></span>

<span data-ttu-id="11078-112"><span id="Supported-Resource-Misc-Flags"></span><span id="supported-resource-misc-flags"></span><span id="SUPPORTED-RESOURCE-MISC-FLAGS"></span>**Sonstige unterstützte Ressourcen-Flags**</span><span class="sxs-lookup"><span data-stu-id="11078-112"><span id="Supported-Resource-Misc-Flags"></span><span id="supported-resource-misc-flags"></span><span id="SUPPORTED-RESOURCE-MISC-FLAGS"></span>**Supported Resource Misc Flags**</span></span>  
<span data-ttu-id="11078-113">Unterteilt; d.h. Streaming (gemäß Definition), Texturwürfel, indirekte Argumente zeichnen, Puffer lässt Rohdatenansichten zu, strukturierter Puffer, Ressourcenklammerung oder Mips generieren.</span><span class="sxs-lookup"><span data-stu-id="11078-113">Tiled; that is, streaming (by definition), texture cube, draw indirect arguments, buffer allow raw views, structured buffer, resource clamp, or generate mips.</span></span>

<span data-ttu-id="11078-114">**Nicht unterstützt:** freigegeben, freigegebenes schlüsselmutex, GDI-kompatibel, freigegebenes NT-Handle, eingeschränkter Inhalt, eingeschränkte freigegebene Ressource, ressourcentreiber, geschützt oder kachelpool.</span><span class="sxs-lookup"><span data-stu-id="11078-114">**NOT supported:** shared, shared keyed mutex, GDI compatible, shared NT handle, restricted content, restrict shared resource, restrict shared resource driver, guarded, or tile pool.</span></span>

<span data-ttu-id="11078-115"><span id="Supported-Bind-Flags"></span><span id="supported-bind-flags"></span><span id="SUPPORTED-BIND-FLAGS"></span>**Unterstützte Bindungsflags**</span><span class="sxs-lookup"><span data-stu-id="11078-115"><span id="Supported-Bind-Flags"></span><span id="supported-bind-flags"></span><span id="SUPPORTED-BIND-FLAGS"></span>**Supported Bind Flags**</span></span>  
<span data-ttu-id="11078-116">Als Shaderressource binden, Renderziel, Tiefenschablone oder unsortierter Zugriff.</span><span class="sxs-lookup"><span data-stu-id="11078-116">Bind as shader resource, render target, depth stencil, or unordered access.</span></span>

<span data-ttu-id="11078-117">**Nicht unterstützt:** Als Konstantenpuffer, Vertexpuffer (Binden eines geteilten Puffers als SRV/UAV/RTV wird unterstützt), Indexpuffer binden Puffer, Streamausgabe, Decoder oder video-Encoder.</span><span class="sxs-lookup"><span data-stu-id="11078-117">**NOT supported:** Bind as constant buffer, vertex buffer (binding a tiled Buffer as an SRV/UAV/RTV is supported), index buffer, stream output, decoder, or video encoder.</span></span>

<span data-ttu-id="11078-118"><span id="Supported-Formats"></span><span id="supported-formats"></span><span id="SUPPORTED-FORMATS"></span>**Unterstützte Formate**</span><span class="sxs-lookup"><span data-stu-id="11078-118"><span id="Supported-Formats"></span><span id="supported-formats"></span><span id="SUPPORTED-FORMATS"></span>**Supported Formats**</span></span>  
<span data-ttu-id="11078-119">Alle Formate, die für die gegebene Konfiguration verfügbar sind, unabhängig davon, ob sie eine geteilte Anordnung verwenden, mit einigen Ausnahmen.</span><span class="sxs-lookup"><span data-stu-id="11078-119">All formats that would be available for the given configuration regardless of it being tiled, with some exceptions.</span></span>

<span data-ttu-id="11078-120"><span id="Supported-Sample-Description--Multisample-count--quality-"></span><span id="supported-sample-description--multisample-count--quality-"></span><span id="SUPPORTED-SAMPLE-DESCRIPTION--MULTISAMPLE-COUNT--QUALITY-"></span>**Unterstützte Samplingbeschreibung (Multisampling-Anzahl, Qualität)**</span><span class="sxs-lookup"><span data-stu-id="11078-120"><span id="Supported-Sample-Description--Multisample-count--quality-"></span><span id="supported-sample-description--multisample-count--quality-"></span><span id="SUPPORTED-SAMPLE-DESCRIPTION--MULTISAMPLE-COUNT--QUALITY-"></span>**Supported Sample Description (Multisample count, quality)**</span></span>  
<span data-ttu-id="11078-121">Alles, was für die gegebene Konfiguration unterstützt wird, unabhängig davon, ob eine geteilte Anordnung verwendet wird, mit einigen Ausnahmen.</span><span class="sxs-lookup"><span data-stu-id="11078-121">Whatever would be supported for the given configuration regardless of it being tiled, with some exceptions.</span></span>

<span data-ttu-id="11078-122"><span id="Supported-Width-Height-MipLevels-ArraySize"></span><span id="supported-width-height-miplevels-arraysize"></span><span id="SUPPORTED-WIDTH-HEIGHT-MIPLEVELS-ARRAYSIZE"></span>**Unterstützte Width/Height/MipLevels/ArraySize**</span><span class="sxs-lookup"><span data-stu-id="11078-122"><span id="Supported-Width-Height-MipLevels-ArraySize"></span><span id="supported-width-height-miplevels-arraysize"></span><span id="SUPPORTED-WIDTH-HEIGHT-MIPLEVELS-ARRAYSIZE"></span>**Supported Width/Height/MipLevels/ArraySize**</span></span>  
<span data-ttu-id="11078-123">Im vollen Umfang von Direct3D unterstützt.</span><span class="sxs-lookup"><span data-stu-id="11078-123">Full extents supported by Direct3D.</span></span> <span data-ttu-id="11078-124">Streamingressourcen unterliegen nicht der Beschränkung auf die Gesamtspeichergröße wie Nicht-Streamingressourcen.</span><span class="sxs-lookup"><span data-stu-id="11078-124">Streaming resources don't have the restriction on total memory size imposed on non-streaming resources.</span></span> <span data-ttu-id="11078-125">Streamingressourcen werden nur durch die Grenzen des virtuellen Gesamtadressraums beschränkt.</span><span class="sxs-lookup"><span data-stu-id="11078-125">Streaming resources are only constrained by overall virtual address space limits.</span></span> <span data-ttu-id="11078-126">Siehe [Zuordnen des verfügbaren Speicherplatzes für Streamingressourcen](address-space-available-for-streaming-resources.md).</span><span class="sxs-lookup"><span data-stu-id="11078-126">See [Address space available for streaming resources](address-space-available-for-streaming-resources.md).</span></span>

<span data-ttu-id="11078-127">Der anfängliche Inhalt des Kachelpoolspeichers ist nicht definiert.</span><span class="sxs-lookup"><span data-stu-id="11078-127">The initial contents of tile pool memory are undefined.</span></span>

## <a name="span-idin-this-sectionspanin-this-section"></a><span data-ttu-id="11078-128"><span id="in-this-section"></span>Inhalt dieses Abschnitts</span><span class="sxs-lookup"><span data-stu-id="11078-128"><span id="in-this-section"></span>In this section</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="11078-129">Thema</span><span class="sxs-lookup"><span data-stu-id="11078-129">Topic</span></span></th>
<th align="left"><span data-ttu-id="11078-130">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="11078-130">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="address-space-available-for-streaming-resources.md"><span data-ttu-id="11078-131">Zuordnen des verfügbaren Speicherplatzes für Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="11078-131">Address space available for streaming resources</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="11078-132">In diesem Abschnitt wird der virtuelle Adressraum angegeben, der für Streamingressourcen verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="11078-132">This section specifies the virtual address space that is available for streaming resources.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="11078-133"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="11078-133"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="11078-134">Erstellen von Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="11078-134">Creating streaming resources</span></span>](creating-streaming-resources.md)

 

 




