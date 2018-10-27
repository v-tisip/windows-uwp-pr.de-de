---
title: Texturansichten
description: Auf Texturressourcen wird in Direct3D mit einer Ansicht zugegriffen, bei der es sich um einen Mechanismus für die Hardware-Interpretation einer Ressource im Speicher handelt.
ms.assetid: 18DABFCE-8A36-4C4E-B08E-10428B05D701
keywords:
- Texturansichten
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 9506b86fc16861984e539c52bdd92eed544079a8
ms.sourcegitcommit: 086001cffaf436e6e4324761d59bcc5e598c15ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2018
ms.locfileid: "5692987"
---
# <a name="texture-views"></a><span data-ttu-id="6619c-104">Texturansichten</span><span class="sxs-lookup"><span data-stu-id="6619c-104">Texture views</span></span>


<span data-ttu-id="6619c-105">Auf Texturressourcen wird in Direct3D mit einer Ansicht zugegriffen, bei der es sich um einen Mechanismus für die Hardware-Interpretation einer Ressource im Speicher handelt.</span><span class="sxs-lookup"><span data-stu-id="6619c-105">In Direct3D, texture resources are accessed with a view, which is a mechanism for hardware interpretation of a resource in memory.</span></span> <span data-ttu-id="6619c-106">Eine Ansicht ermöglicht einer bestimmten Pipelinephase den Zugriff auf die erforderlichen [Unterressourcen](resource-types.md), in der von der Anwendung gewünschten Darstellung.</span><span class="sxs-lookup"><span data-stu-id="6619c-106">A view allows a particular pipeline stage to access only the [subresources](resource-types.md) it needs, in the representation desired by the application.</span></span>

<span data-ttu-id="6619c-107">Eine Ansicht unterstützt das Konzept einer typenlosen Ressource.</span><span class="sxs-lookup"><span data-stu-id="6619c-107">A view supports the notion of a typeless resource.</span></span> <span data-ttu-id="6619c-108">Eine typenlose Ressource ist eine Ressource mit einer bestimmten Größe, die aber nicht mit einem bestimmten Datentyp erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="6619c-108">A typeless resource is a resource created with a specific size but not a specific data type.</span></span> <span data-ttu-id="6619c-109">Die Daten werden dynamisch interpretiert, wenn sie an die Pipeline gebunden sind.</span><span class="sxs-lookup"><span data-stu-id="6619c-109">The data is interpreted dynamically when it is bound to the pipeline.</span></span>

<span data-ttu-id="6619c-110">Die folgende Abbildungzeigt ein Beispiel für die Bindung eines 2D-Textur-Arrays mit 6 Texturen als Shader-Ressource durch die Erstellung einer Shader-Ressourcenansicht dafür.</span><span class="sxs-lookup"><span data-stu-id="6619c-110">The following illustration shows an example of binding a 2D texture array with 6 textures as a shader resource by creating a shader resource view for it.</span></span> <span data-ttu-id="6619c-111">Die Ressource wird dann als Array von Texturen behandelt.</span><span class="sxs-lookup"><span data-stu-id="6619c-111">The resource is then addressed as an array of textures.</span></span> <span data-ttu-id="6619c-112">(Hinweis: Eine Unterressource kann nichtgleichzeitig als Eingabe und Ausgabe an die Pipeline gebunden werden.)</span><span class="sxs-lookup"><span data-stu-id="6619c-112">(Note: a subresource cannot be bound as both input and output to the pipeline simultaneously.)</span></span>

![Illustration eines Textur-Arrays mit sechs Texturen](images/d3d10-cube-texture-faces.png)

<span data-ttu-id="6619c-114">Bei Verwendung eines 2D-Textur-Arrays als Renderziel kann die Ressource als Array von 2D-Texturen (in diesem Beispiel 6) mit Mipmap-Ebenen (in diesem Beispiel 3) betrachtet werden.</span><span class="sxs-lookup"><span data-stu-id="6619c-114">When using a 2D texture array as a render target, the resource can be viewed as an array of 2D textures (6 in this example) with mipmap levels (3 in this example).</span></span>

<span data-ttu-id="6619c-115">Erstellen Sie ein Objekt für ein Renderziel durch Aufrufen von CreateRenderTargetView.</span><span class="sxs-lookup"><span data-stu-id="6619c-115">Create a view object for a render target by calling CreateRenderTargetView.</span></span> <span data-ttu-id="6619c-116">Rufen Sie dann OMSetRenderTargets auf, um die Renderzielansicht für die Pipeline festzulegen.</span><span class="sxs-lookup"><span data-stu-id="6619c-116">Then call OMSetRenderTargets to set the render target view to the pipeline.</span></span> <span data-ttu-id="6619c-117">Rendern Sie in die Renderziele durch Aufrufen von Draw und die Verwendung von RenderTargetArrayIndex zur Indizierung in der korrekten Textur des Arrays.</span><span class="sxs-lookup"><span data-stu-id="6619c-117">Render into the render targets by calling Draw and using the RenderTargetArrayIndex to index into the proper texture in the array.</span></span> <span data-ttu-id="6619c-118">Sie können eine Unterressource (eine Mipmap-Ebene, eine Array-Index-Kombination) zum Binden eines beliebigen Arrays von Unterressourcen verwenden.</span><span class="sxs-lookup"><span data-stu-id="6619c-118">You can use a subresource (a mipmap level, array index combination) to bind to any array of subresources.</span></span> <span data-ttu-id="6619c-119">Sie können also, wenn Sie wollen, die Bindung an die zweite Mipmap-Ebene durchführen und nur diese Mipmap-Ebene aktualisieren, wie in der folgenden Abbildung gezeigt.</span><span class="sxs-lookup"><span data-stu-id="6619c-119">So you could bind to the second mipmap level and only update this particular mipmap level if you wanted, as in the following illustration.</span></span>

![Illustration der Bindung nur an die zweite Mipmap-Ebene eines Textur-Arrays](images/d3d10-cube-texture-faces-subresource.png)

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="6619c-121"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="6619c-121"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="6619c-122">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="6619c-122">Resources</span></span>](resources.md)

 

 




