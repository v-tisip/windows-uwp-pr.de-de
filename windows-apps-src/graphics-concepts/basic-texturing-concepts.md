---
title: Grundlegende Texturkonzepte
description: Obwohl frühe computergenerierte 3D-Bilder generell hoch entwickelt waren, sahen diese künstlich glänzend aus.
ms.assetid: 3CA3905D-E837-48EB-A81F-319AA1C6537E
keywords:
- Grundlegende Texturkonzepte
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 2124c9e620694f62414c865e6d3247cd25ce70d0
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8217344"
---
# <a name="basic-texturing-concepts"></a><span data-ttu-id="ca608-104">Grundlegende Texturkonzepte</span><span class="sxs-lookup"><span data-stu-id="ca608-104">Basic texturing concepts</span></span>


<span data-ttu-id="ca608-105">Obwohl frühe computergenerierte 3D-Bilder generell hoch entwickelt waren, sahen diese künstlich glänzend aus.</span><span class="sxs-lookup"><span data-stu-id="ca608-105">Early computer-generated 3D images, although generally advanced for their time, tended to have a shiny plastic look.</span></span> <span data-ttu-id="ca608-106">Es fehlte ihnen Kennzeichen – wie etwa Abnutzungen, Risse, Fingerabdrücke und Flecken -, die 3D-Objekten eine realistische optische Komplexität verleihen.</span><span class="sxs-lookup"><span data-stu-id="ca608-106">They lacked the types of markings-such as scuffs, cracks, fingerprints, and smudges-that give 3D objects realistic visual complexity.</span></span> <span data-ttu-id="ca608-107">Texturen sind besonders für den verbesserten Realismus von computergenerierten 3D-Bilder beliebt.</span><span class="sxs-lookup"><span data-stu-id="ca608-107">Textures have become popular for enhancing the realism of computer-generated 3D images.</span></span>

<span data-ttu-id="ca608-108">Bei alltägliche Aufgaben bezieht sich das Wort „Textur” auf die Gleichmäßigkeit oder Rauheit eines Objekts.</span><span class="sxs-lookup"><span data-stu-id="ca608-108">In its everyday use, the word texture refers to an object's smoothness or roughness.</span></span> <span data-ttu-id="ca608-109">Im Computergrafiken ist eine Textur jedoch eine Bitmap aus Pixelfarben, die einem Objekt das Erscheinungsbild der Textur verleihen.</span><span class="sxs-lookup"><span data-stu-id="ca608-109">In computer graphics, however, a texture is a bitmap of pixel colors that give an object the appearance of texture.</span></span>

<span data-ttu-id="ca608-110">Da Direct3D-Texturen Bitmaps sind, kann jede Bitmap auf einen Direct3D-Grundtyp angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="ca608-110">Because Direct3D textures are bitmaps, any bitmap can be applied to a Direct3D primitive.</span></span> <span data-ttu-id="ca608-111">Beispielsweise können Apps Objekte erstellen und bearbeiten, die wie eine Holzmaserung aussehen.</span><span class="sxs-lookup"><span data-stu-id="ca608-111">For instance, applications can create and manipulate objects that appear to have a wood grain pattern in them.</span></span> <span data-ttu-id="ca608-112">Gras, Schmutz und Felsen können auf eine Gruppe von 3D-Grundtypen angewendet werden, die einen Hügel bilden.</span><span class="sxs-lookup"><span data-stu-id="ca608-112">Grass, dirt, and rocks can be applied to a set of 3D primitives that form a hill.</span></span> <span data-ttu-id="ca608-113">Das Ergebnis ist ein realistischer Berghang.</span><span class="sxs-lookup"><span data-stu-id="ca608-113">The result is a realistic-looking hillside.</span></span> <span data-ttu-id="ca608-114">Sie können Texturen ebenfalls für Effekte wie Straßenschilder, Gebirgsschichten einer Klippe verwenden oder damit die optische Erscheinung eines Marmorbodens erstellen.</span><span class="sxs-lookup"><span data-stu-id="ca608-114">You can also use texturing to create effects such as signs along a roadside, rock strata in a cliff, or the appearance of marble on a floor.</span></span>

<span data-ttu-id="ca608-115">Darüber hinaus unterstützt Direct3D komplexere Techniken wie Texturvermischung (transparent oder opak) und Licht.</span><span class="sxs-lookup"><span data-stu-id="ca608-115">In addition, Direct3D supports more advanced texturing techniques such as texture blending-with or without transparency-and light mapping.</span></span> <span data-ttu-id="ca608-116">Informationen hierzu finden Sie unter [Texturvermischung](texture-blending.md) und [Lichtzuordnung mit Texturen](light-mapping-with-textures.md).</span><span class="sxs-lookup"><span data-stu-id="ca608-116">See [Texture blending](texture-blending.md) and [Light mapping with textures](light-mapping-with-textures.md).</span></span>

<span data-ttu-id="ca608-117">Wenn die Anwendung ein Hardwareabstraktionsschichts- (HAL) oder Softwaregerät erstellt, können Sie 8-, 16-, 24-, 32-, 64- oder 128-Bit-Texturen verwenden.</span><span class="sxs-lookup"><span data-stu-id="ca608-117">If your application creates a hardware abstraction layer (HAL) device or a software device, it can use 8, 16, 24, 32, 64, or 128-bit textures.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="ca608-118"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="ca608-118"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="ca608-119">Texturen</span><span class="sxs-lookup"><span data-stu-id="ca608-119">Textures</span></span>](textures.md)

 

 




