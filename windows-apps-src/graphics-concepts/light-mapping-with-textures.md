---
title: Lichtzuordnung mit Texturen
description: Eine Lichtzuordnung ist eine Textur oder Texturgruppe, die Informationen über Licht in der 3D-Szene enthält.
ms.assetid: 5C7518D2-AC92-4A97-B7AF-4469D213D7BD
keywords:
- Lichtzuordnung mit Texturen
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 9bbb723cc039d6ecca8a5ebcd30ef03559076934
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2018
ms.locfileid: "7160984"
---
# <a name="light-mapping-with-textures"></a><span data-ttu-id="247fa-104">Lichtzuordnung mit Texturen</span><span class="sxs-lookup"><span data-stu-id="247fa-104">Light mapping with textures</span></span>


<span data-ttu-id="247fa-105">Eine Lichtzuordnung ist eine Textur oder Texturgruppe, die Informationen über das Licht in einer 3D-Szene enthält.</span><span class="sxs-lookup"><span data-stu-id="247fa-105">A light map is a texture or group of textures that contains information about lighting in a 3D scene.</span></span> <span data-ttu-id="247fa-106">Lichtzuordnungen ordnen Licht- und Schattenbereiche Grundtypen zu.</span><span class="sxs-lookup"><span data-stu-id="247fa-106">Light maps map areas of light and shadow onto primitives.</span></span> <span data-ttu-id="247fa-107">Multipass und das Mischen mehrerer Texturen ermöglichen Ihrer Anwendung, Szenen mit einer realistischeren Darstellung zu rendern als mit Schattierungstechniken.</span><span class="sxs-lookup"><span data-stu-id="247fa-107">Multipass and multiple texture blending enable your application to render scenes with a more realistic appearance than shading techniques.</span></span>

<span data-ttu-id="247fa-108">Damit eine Anwendung eine 3D-Szene realistisch rendern kann, muss der Effekt von Lichtquellen in der Darstellung der Szene berücksichtigt werden.</span><span class="sxs-lookup"><span data-stu-id="247fa-108">For an application to realistically render a 3D scene, it must take into account the effect that light sources have on the appearance of the scene.</span></span> <span data-ttu-id="247fa-109">Obwohl Techniken wie Flat und Gouraud Shading in dieser Hinsicht wertvolle Tools darstellen, sind sie für Ihre Anforderungen möglicherweise unzureichend.</span><span class="sxs-lookup"><span data-stu-id="247fa-109">Although techniques such as flat and Gouraud shading are valuable tools in this respect, they can be insufficient for your needs.</span></span> <span data-ttu-id="247fa-110">Direct3D unterstützt auch Multipass und das Mischen mehrerer Texturen.</span><span class="sxs-lookup"><span data-stu-id="247fa-110">Direct3D supports multipass and multiple texture blending.</span></span> <span data-ttu-id="247fa-111">Mit diesen Funktionen kann Ihre Anwendung Szenen in einer realistischeren Darstellung rendern als nur mit Shading-Techniken gerenderte Szenen.</span><span class="sxs-lookup"><span data-stu-id="247fa-111">These capabilities enable your application to render scenes with a more realistic appearance than scenes rendered with shading techniques alone.</span></span> <span data-ttu-id="247fa-112">Durch die Anwendung einer oder mehrerer Lichtzuordnungen kann Ihre Anwendung Licht- und Schattenbereiche ihren Grundtypen zuordnen.</span><span class="sxs-lookup"><span data-stu-id="247fa-112">By applying one or more light maps, your application can map areas of light and shadow onto its primitives.</span></span>

<span data-ttu-id="247fa-113">Eine Lichtzuordnung ist eine Textur oder Texturgruppe, die Informationen über Licht in einer 3D-Szene enthält.</span><span class="sxs-lookup"><span data-stu-id="247fa-113">A light map is a texture or group of textures that contains information about lighting in a 3D scene.</span></span> <span data-ttu-id="247fa-114">Sie können Lichtinformationen in den Alpha-Werten der Lichtzuordnung, in den Farbwerten oder in beiden speichern.</span><span class="sxs-lookup"><span data-stu-id="247fa-114">You can store the lighting information in the alpha values of the light map, in the color values, or in both.</span></span>

<span data-ttu-id="247fa-115">Wenn Sie die Lichtzuordnung mithilfe eine mehrstufigen Texturverblendung implementieren, sollte Ihre Anwendung die Lichtzuordnung zu seinen Grundtypen beim ersten Durchlauf rendern.</span><span class="sxs-lookup"><span data-stu-id="247fa-115">If you implement light mapping using multipass texture blending, your application should render the light map onto its primitives on the first pass.</span></span> <span data-ttu-id="247fa-116">Im zweiten Durchlauf sollte sie die Basistextur rendern.</span><span class="sxs-lookup"><span data-stu-id="247fa-116">It should use a second pass to render the base texture.</span></span> <span data-ttu-id="247fa-117">Die Ausnahme bildet die Glanzlichtzuordnung.</span><span class="sxs-lookup"><span data-stu-id="247fa-117">The exception to this is specular light mapping.</span></span> <span data-ttu-id="247fa-118">Rendern Sie in diesem Fall zuerst die Basistextur und fügen Sie dann die Lichtzuordnung hinzu.</span><span class="sxs-lookup"><span data-stu-id="247fa-118">In that case, render the base texture first; then add the light map.</span></span>

<span data-ttu-id="247fa-119">Die mehrstufige Texturverblendung ermöglicht Ihrer Anwendung, die Lichtzuordnung und die Basistextur in einem Durchlauf zu rendern.</span><span class="sxs-lookup"><span data-stu-id="247fa-119">Multiple texture blending enables your application to render the light map and the base texture in one pass.</span></span> <span data-ttu-id="247fa-120">Wenn die Benutzerhardware für mehrstufige Texturverblendung geeignet ist, sollte Ihre Anwendung diesen Vorteil für die Lichtzuordnung nutzen.</span><span class="sxs-lookup"><span data-stu-id="247fa-120">If the user's hardware provides for multiple texture blending, your application should take advantage of it when performing light mapping.</span></span> <span data-ttu-id="247fa-121">Damit verbessern Sie die Leistung Ihrer Anwendung erheblich.</span><span class="sxs-lookup"><span data-stu-id="247fa-121">This significantly improves your application's performance.</span></span>

<span data-ttu-id="247fa-122">Durch die Verwendung von Lichtzuordnungen kann eine Direct3D-Anwendung beim Rendern von Grundtypen zahlreiche Lichteffekte erreichen.</span><span class="sxs-lookup"><span data-stu-id="247fa-122">Using light maps, a Direct3D application can achieve a variety of lighting effects when it renders primitives.</span></span> <span data-ttu-id="247fa-123">Sie kann nicht nur monochrome und farbige Lichter in einer Szene zuordnen, sondern auch Details hinzufügen, wie beispielsweise Glanzlicht oder diffuses Licht.</span><span class="sxs-lookup"><span data-stu-id="247fa-123">It can map not only monochrome and colored lights in a scene, but it can also add details such as specular highlights and diffuse lighting.</span></span>

<span data-ttu-id="247fa-124">Informationen zur Verwendung der Texturverblendung in Direct3D zum Ausführen einer Lichtzuordnung finden Sie in folgenden Themen.</span><span class="sxs-lookup"><span data-stu-id="247fa-124">Information on using Direct3D texture blending to perform light mapping is presented in the following topics.</span></span>

## <a name="span-idin-this-sectionspanin-this-section"></a><span data-ttu-id="247fa-125"><span id="in-this-section"></span>In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="247fa-125"><span id="in-this-section"></span>In this section</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="247fa-126">Thema</span><span class="sxs-lookup"><span data-stu-id="247fa-126">Topic</span></span></th>
<th align="left"><span data-ttu-id="247fa-127">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="247fa-127">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="monochrome-light-maps.md"><span data-ttu-id="247fa-128">Monochrome Lichtzuordnungen</span><span class="sxs-lookup"><span data-stu-id="247fa-128">Monochrome light maps</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="247fa-129">Durch die monochrome Lichtzuordnung sind ältere Adapter in der Lage, eine mehrstufige Texturverblendung auszuführen, wenn eine ältere 3D-Beschleunigerkarte die Texturverblendung unter Verwendung der Alpha-Werte des Zielpixels nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="247fa-129">Monochrome light mapping enables older adapters to perform multipass texture blending, when an older 3D accelerator board doesn't support texture blending using the alpha value of the destination pixel.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="color-light-maps.md"><span data-ttu-id="247fa-130">Farblichtzuordnung</span><span class="sxs-lookup"><span data-stu-id="247fa-130">Color light maps</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="247fa-131">Eine farbige Lichtzuordnung verwendet für die Beleuchtungsinformationen RGB-Daten in der Lichtzuordnung.</span><span class="sxs-lookup"><span data-stu-id="247fa-131">A colored light map uses the RGB data in the light map for its lighting information.</span></span> <span data-ttu-id="247fa-132">Eine Anwendung rendert 3D-Szenen in der Regel realistischer, wenn farbige Lichtzuordnungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="247fa-132">An application usually renders 3D scenes more realistically if it uses colored light maps.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="specular-light-maps.md"><span data-ttu-id="247fa-133">Glanzlichtzuordnungen</span><span class="sxs-lookup"><span data-stu-id="247fa-133">Specular light maps</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="247fa-134">Glänzende Objekte aus hochreflektieRendern Materialien erhalten durch das Beleuchten mit einer Lichtquelle Glanzlichter.</span><span class="sxs-lookup"><span data-stu-id="247fa-134">When illuminated by a light source, shiny objects that use highly reflective materials receive specular highlights.</span></span> <span data-ttu-id="247fa-135">Manchmal erhalten Sie genauere Glanzlichter, wenn Sie eine Glanzlichtzuordnung zu den Grundtypen anwenden, statt die vom Beleuchtungsmodul erzeugten Glanzlichter zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="247fa-135">Sometimes you can get more accurate highlights by applying specular light maps to primitives, rather than using the specular highlights produced by the lighting module.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="diffuse-light-maps.md"><span data-ttu-id="247fa-136">Diffuse Lichtzuordnungen</span><span class="sxs-lookup"><span data-stu-id="247fa-136">Diffuse light maps</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="247fa-137">Matte Oberflächen haben eine diffuse Lichtreflektion.</span><span class="sxs-lookup"><span data-stu-id="247fa-137">Matte surfaces have diffuse light reflection.</span></span> <span data-ttu-id="247fa-138">Die Helligkeit von diffusem Licht ist von der Entfernung zur Lichtquelle und dem Winkel zwischen der Oberflächennormale und dem Richtungsvektor der Lichtquelle abhängig.</span><span class="sxs-lookup"><span data-stu-id="247fa-138">The brightness of diffuse light depends on the distance from the light source and the angle between the surface normal and the light source direction vector.</span></span> <span data-ttu-id="247fa-139">Texturlichtzuordnungen können komplexe diffuse Beleuchtung simulieren.</span><span class="sxs-lookup"><span data-stu-id="247fa-139">Texture light maps can simulate complex diffuse lighting.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="247fa-140"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="247fa-140"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="247fa-141">Texturen</span><span class="sxs-lookup"><span data-stu-id="247fa-141">Textures</span></span>](textures.md)

 

 




