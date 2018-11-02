---
title: Emissive-Lighting
description: Beim Emissive-Lighting handelt es sich um eine Beleuchtung, die von einem Objekt ausgeht (z. B. ein Glühen).
ms.assetid: 262EB9E2-DF96-401F-93D6-51A7BB60074B
keywords:
- Emissive-Lighting
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 9ce2082479261cd96fb1c5bafd5f2df06bf6f239
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5970217"
---
# <a name="emissive-lighting"></a><span data-ttu-id="38a9e-104">Emissive-Lighting</span><span class="sxs-lookup"><span data-stu-id="38a9e-104">Emissive lighting</span></span>


<span data-ttu-id="38a9e-105">*Ausstrahlende Beleuchtung* ist Licht, das ein Objekt ausstrahlt; beispielsweise ein Leuchten.</span><span class="sxs-lookup"><span data-stu-id="38a9e-105">*Emissive lighting* is light that is emitted by an object; for example, a glow.</span></span> <span data-ttu-id="38a9e-106">Durch das Ausstrahlen erscheint ein angezeigtes Objekt als selbstleuchtend.</span><span class="sxs-lookup"><span data-stu-id="38a9e-106">Emission makes a rendered object appear to be self-luminous.</span></span> <span data-ttu-id="38a9e-107">Die Emissionen wirken sich auf die Farbe eines Objektes aus. Sie können beispielsweise ein dunkles Material heller und teilweise in der emittierten Farbe erscheinen lassen.</span><span class="sxs-lookup"><span data-stu-id="38a9e-107">Emission affects an object's color and can, for example, make a dark material brighter and take on part of the emitted color.</span></span>

<span data-ttu-id="38a9e-108">Das Emissive-lighting wird durch einen einzigen Faktor beschrieben.</span><span class="sxs-lookup"><span data-stu-id="38a9e-108">Emissive lighting is described by a single term.</span></span>

<span data-ttu-id="38a9e-109">Emissive-Lighting = Cₑ</span><span class="sxs-lookup"><span data-stu-id="38a9e-109">Emissive Lighting = Cₑ</span></span>

<span data-ttu-id="38a9e-110">Dabei gilt Folgendes:</span><span class="sxs-lookup"><span data-stu-id="38a9e-110">where:</span></span>

| <span data-ttu-id="38a9e-111">Parameter</span><span class="sxs-lookup"><span data-stu-id="38a9e-111">Parameter</span></span> | <span data-ttu-id="38a9e-112">Standardwert</span><span class="sxs-lookup"><span data-stu-id="38a9e-112">Default value</span></span> | <span data-ttu-id="38a9e-113">Typ</span><span class="sxs-lookup"><span data-stu-id="38a9e-113">Type</span></span>                                                                 | <span data-ttu-id="38a9e-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="38a9e-114">Description</span></span>     |
|-----------|---------------|----------------------------------------------------------------------|-----------------|
| <span data-ttu-id="38a9e-115">Cₑ</span><span class="sxs-lookup"><span data-stu-id="38a9e-115">Cₑ</span></span>        | <span data-ttu-id="38a9e-116">(0,0,0,0)</span><span class="sxs-lookup"><span data-stu-id="38a9e-116">(0,0,0,0)</span></span>     | <span data-ttu-id="38a9e-117">Rot, Grün, Blau und Alphatransparenz (alle Gleitkommawerte)</span><span class="sxs-lookup"><span data-stu-id="38a9e-117">Red, green, blue, and alpha transparency (all floating-point values)</span></span> | <span data-ttu-id="38a9e-118">Emissionsfarbe.</span><span class="sxs-lookup"><span data-stu-id="38a9e-118">Emissive color.</span></span> |

 

<span data-ttu-id="38a9e-119">Der Wert für Cₑ ist entweder Farbe 1 oder Farbe 2.</span><span class="sxs-lookup"><span data-stu-id="38a9e-119">The value for Cₑ is either color 1 or color 2.</span></span> <span data-ttu-id="38a9e-120">Wenn die Vertex-Farbe nicht angegeben wird, wird das Emissive-Materialfarbe verwendet.</span><span class="sxs-lookup"><span data-stu-id="38a9e-120">If the vertex color is not provided, the material emissive color is used.</span></span>

## <a name="span-idexamplespanspan-idexamplespanspan-idexamplespanexample"></a><span data-ttu-id="38a9e-121"><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Beispiel</span><span class="sxs-lookup"><span data-stu-id="38a9e-121"><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Example</span></span>


<span data-ttu-id="38a9e-122">In diesem Beispiel wird das Objekt über die Ambiente-Beleuchtung der Szene und die Ambiente-Farbe des Materials eingefärbt.</span><span class="sxs-lookup"><span data-stu-id="38a9e-122">In this example, the object is colored using the scene ambient light and a material ambient color.</span></span>

<span data-ttu-id="38a9e-123">Entsprechend der Gleichung ist die resultierende Farbe der Objekt-Vertizes die Materialfarbe.</span><span class="sxs-lookup"><span data-stu-id="38a9e-123">According to the equation, the resulting color for the object vertices is the material color.</span></span>

<span data-ttu-id="38a9e-124">Die folgende Abbildungzeigt die Materialfarbe (Grün).</span><span class="sxs-lookup"><span data-stu-id="38a9e-124">The following illustration shows the material color, which is green.</span></span> <span data-ttu-id="38a9e-125">Die Emissive-Beleuchtung beleuchtet alle Objekt-Vertizes mit derselben Farbe.</span><span class="sxs-lookup"><span data-stu-id="38a9e-125">Emissive light lights all object vertices with the same color.</span></span> <span data-ttu-id="38a9e-126">Sie ist nicht von der Vertex-Normalen oder der Beleuchtungsrichtung abhängig.</span><span class="sxs-lookup"><span data-stu-id="38a9e-126">It is not dependent on the vertex normal or the light direction.</span></span> <span data-ttu-id="38a9e-127">Daher sieht die Kugel wie ein 2D-Kreis aus – denn es gibt keine Schattierung für die Oberfläche des Objekts.</span><span class="sxs-lookup"><span data-stu-id="38a9e-127">As a result, the sphere looks like a 2D circle because there is no difference in shading around the surface of the object.</span></span>

![Abbildungeiner grünen Kugel](images/lighte.jpg)

<span data-ttu-id="38a9e-129">Die folgende Abbildungzeigt, wie sich die Emissive-Beleuchtung mit den anderen drei Beleuchtungstypen mischt.</span><span class="sxs-lookup"><span data-stu-id="38a9e-129">The following illustration shows how the emissive light blends with the other three types of lights.</span></span> <span data-ttu-id="38a9e-130">Auf der rechten Seite der Kugel ist eine Mischung aus grüne Emissive- und roter Ambient-Beleuchtung sichtbar.</span><span class="sxs-lookup"><span data-stu-id="38a9e-130">On the right side of the sphere, there is a blend of the green emissive and the red ambient light.</span></span> <span data-ttu-id="38a9e-131">Auf der linken Seite der Kugel mischt sich die grüne Emissive-Beleuchtung mit einer Diffuse-Beleuchtung und erzeugt so einen roten Farbverlauf.</span><span class="sxs-lookup"><span data-stu-id="38a9e-131">On the left side of the sphere, the green emissive light blends with red ambient and diffuse light producing a red gradient.</span></span> <span data-ttu-id="38a9e-132">Das Glanzlicht in der Mitte ist Weiß. Es sorgt für einen gelben Ring, denn der Wert der Glanz-Beleuchtung fällt stark ab. Dies sorgt dafür, dass die Werte für die Ambiente-, Diffuse- und Emissions-Beleuchtung gemischt werden. So entsteht das Gelb.</span><span class="sxs-lookup"><span data-stu-id="38a9e-132">The specular highlight is white in the center and creates a yellow ring as the specular light value falls off sharply leaving the ambient, diffuse and emissive light values which blend together to make yellow.</span></span>

![Abbildungeiner grüne Kugel mit Emissive-Beleuchtung](images/lightadse.jpg)

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="38a9e-134"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="38a9e-134"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="38a9e-135">Beleuchtungsmathematik</span><span class="sxs-lookup"><span data-stu-id="38a9e-135">Mathematics of lighting</span></span>](mathematics-of-lighting.md)

 

 




