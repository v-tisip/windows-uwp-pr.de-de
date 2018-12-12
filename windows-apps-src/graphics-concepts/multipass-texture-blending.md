---
title: Mehrstufige Texturvermischung
description: Direct3D-Apps können durch die Anwendung verschiedener Texturen auf eine Primitive im Laufe von mehreren Berechnungs- und Ausgabedurchläufen zahlreiche Spezialeffekte erzielen.
ms.assetid: FB4D6E3F-4EF5-4D20-BF7E-1008E790E30C
keywords:
- Mehrstufige Texturvermischung
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: d6b1e8958874ede50a18f2d2446c8f156361210e
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8932056"
---
# <a name="multipass-texture-blending"></a><span data-ttu-id="d39d1-104">Mehrstufige Texturvermischung</span><span class="sxs-lookup"><span data-stu-id="d39d1-104">Multipass texture blending</span></span>


<span data-ttu-id="d39d1-105">Direct3D-Anwendungen können durch die Anwendung verschiedener Texturen auf einen Grundtyp im Laufe von mehreren Berechnungs- und Ausgabedurchläufen zahlreiche Spezialeffekte erzielen.</span><span class="sxs-lookup"><span data-stu-id="d39d1-105">Direct3D applications can achieve numerous special effects by applying various textures to a primitive over the course of multiple rendering passes.</span></span> <span data-ttu-id="d39d1-106">Der allgemeine Begriff dafür ist *Mehrstufige Texturmischung*.</span><span class="sxs-lookup"><span data-stu-id="d39d1-106">The common term for this is *multipass texture blending*.</span></span> <span data-ttu-id="d39d1-107">Eine typische Anwendung der mehrstufigen Texturmischung ist die Nachbildung der Effekte komplexer Beleuchtungs- und Schattierungsmodelle durch die Anwendung mehrerer Farben aus mehreren unterschiedlichen Texturen.</span><span class="sxs-lookup"><span data-stu-id="d39d1-107">A typical use for multipass texture blending is to emulate the effects of complex lighting and shading models by applying multiple colors from several different textures.</span></span> <span data-ttu-id="d39d1-108">Eine solche Anwendung heißt *Lichtzuordnung*.</span><span class="sxs-lookup"><span data-stu-id="d39d1-108">One such application is called *light mapping*.</span></span> <span data-ttu-id="d39d1-109">Siehe [Lichtzuordnung mit Texturen](light-mapping-with-textures.md).</span><span class="sxs-lookup"><span data-stu-id="d39d1-109">See [Light mapping with textures](light-mapping-with-textures.md).</span></span>

<span data-ttu-id="d39d1-110">**Hinweis:**  einige Geräte können mehrere Texturen auf primitive in einem einzigen Durchgang anwenden.</span><span class="sxs-lookup"><span data-stu-id="d39d1-110">**Note** Some devices are capable of applying multiple textures to primitives in a single pass.</span></span> <span data-ttu-id="d39d1-111">Siehe [Texturvermischung](texture-blending.md).</span><span class="sxs-lookup"><span data-stu-id="d39d1-111">See [Texture blending](texture-blending.md).</span></span>

 

<span data-ttu-id="d39d1-112">Wenn die Hardware des Benutzers die Vermischung mehrerer Texturen nicht unterstützt, kann Ihre Anwendung die mehrstufige Texturvermischung verwenden, um die gleichen visuellen Effekte zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="d39d1-112">If the user's hardware does not support multiple texture blending, your application can use multipass texture blending to achieve the same visual effects.</span></span> <span data-ttu-id="d39d1-113">Die Anwendung kann jedoch nicht die Bildwechselfrequenzen erhalten, die bei Verwendung der Vermischung mehrerer Texturen möglich sind.</span><span class="sxs-lookup"><span data-stu-id="d39d1-113">However, the application cannot sustain the frame rates that are possible when using multiple texture blending.</span></span>

<span data-ttu-id="d39d1-114">Durchführen der mehrstufigen Texturvermischung in einer C/C++-Anwendung:</span><span class="sxs-lookup"><span data-stu-id="d39d1-114">To perform multipass texture blending in a C/C++ application:</span></span>

1.  <span data-ttu-id="d39d1-115">Setzen Sie eine Textur in Texturphase 0.</span><span class="sxs-lookup"><span data-stu-id="d39d1-115">Set a texture in texture stage 0.</span></span>
2.  <span data-ttu-id="d39d1-116">Wählen Sie die gewünschte Farb- und Alphavermischungsargumente und -abläufe.</span><span class="sxs-lookup"><span data-stu-id="d39d1-116">Select the desired color and alpha blending arguments and operations.</span></span> <span data-ttu-id="d39d1-117">Die Standardeinstellungen eignen sich hinlänglich für die mehrstufige Texturvermischung.</span><span class="sxs-lookup"><span data-stu-id="d39d1-117">The default settings are well-suited for multipass texture blending.</span></span>
3.  <span data-ttu-id="d39d1-118">Berechnen Sie die entsprechenden 3D-Objekte in der Szene und geben Sie diese aus.</span><span class="sxs-lookup"><span data-stu-id="d39d1-118">Render the appropriate objects in the scene.</span></span>
4.  <span data-ttu-id="d39d1-119">Setzen Sie die nächste Textur in Texturphase 0.</span><span class="sxs-lookup"><span data-stu-id="d39d1-119">Set the next texture in texture stage 0.</span></span>
5.  <span data-ttu-id="d39d1-120">Setzen Sie die Berechnungs- und Ausgabezustände, um die Ursprungs- und Zielvermischungsfaktoren nach Bedarf anzupassen.</span><span class="sxs-lookup"><span data-stu-id="d39d1-120">Set the render states to adjust the source and destination blending factors as needed.</span></span> <span data-ttu-id="d39d1-121">Das System vermischt die neuen Texturen mit den vorhandenen Pixeln in der Ziel-Ausgeben-Oberfläche gemäß dieser Parameter.</span><span class="sxs-lookup"><span data-stu-id="d39d1-121">The system blends the new textures with the existing pixels in the render-target surface according to these parameters.</span></span>
6.  <span data-ttu-id="d39d1-122">Wiederholen Sie die Schritte3, 4 und 5 mit so vielen Texturen wie gewünscht.</span><span class="sxs-lookup"><span data-stu-id="d39d1-122">Repeat Steps 3, 4, and 5 with as many textures as needed.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="d39d1-123"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="d39d1-123"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="d39d1-124">Texturvermischung</span><span class="sxs-lookup"><span data-stu-id="d39d1-124">Texture blending</span></span>](texture-blending.md)

 

 




